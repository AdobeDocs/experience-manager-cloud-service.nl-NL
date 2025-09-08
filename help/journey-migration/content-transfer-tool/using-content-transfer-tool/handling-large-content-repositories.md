---
title: Afhandeling van grote opslagplaatsen voor inhoud
description: In deze sectie wordt de verwerking van grote opslagplaatsen voor inhoud beschreven
exl-id: 21bada73-07f3-4743-aae6-2e37565ebe08
feature: Migration
role: Admin
source-git-commit: b729c07c78519cd9b6536a0dd142aa8ed01d2a22
workflow-type: tm+mt
source-wordcount: '1842'
ht-degree: 0%

---

# Afhandeling van grote opslagplaatsen voor inhoud {#handling-large-content-repositories}

## Overzicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Afhandeling van grote opslagplaatsen voor inhoud"
>abstract="Als u de extractie- en insluitingsfasen van de activiteit voor inhoudsoverdracht aanzienlijk wilt versnellen om inhoud naar AEM as a Cloud Service te verplaatsen, kunt u met het gereedschap Inhoud overbrengen (CTT) AzCopy gebruiken als een optionele stap vóór het kopiëren. Zodra deze voorstap is geconfigureerd, kopieert AzCopy in de extractiefase lobs van Amazon S3 of Azure Blob Storage naar de blob-opslag van de migratieset. In de innamefase kopieert AzCopy klodders van de blob store van de migratieset naar de AEM as a Cloud Service blob store van de bestemming."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html#setting-up-pre-copy-step" text="Aan de slag met AzCopy als een stap Vooraf kopiëren"

Het kopiëren van vele blobs met het hulpmiddel van de Overdracht van de Inhoud (CTT) kan veelvoudige dagen vergen.
Om de extractie en inname fasen van de activiteit van de inhoudsoverdracht te versnellen om inhoud naar AEM as a Cloud Service te bewegen, kan CTT [ AzCopy ](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) als facultatieve pre-exemplaarstap gebruiken. Deze pre-exemplaarstap kan worden gebruikt wanneer de bronAEM instantie wordt gevormd om een Amazon S3, Azure Blob de gegevensopslag van de Opslag, of de Opslag van de Gegevens van het Dossier te gebruiken. De voorkopieerstap is het meest effectief voor de eerste volledige extractie en inname. Het gebruik van een voorkopie voor volgende top-ups wordt echter afgeraden (als de grootte van de top-up minder is dan 200 GB), omdat dit veel tijd kan kosten voor het gehele proces. Zodra deze voorstap is geconfigureerd, kopieert AzCopy in de extractiefase lobs van Amazon S3, Azure Blob Storage of File data store naar de migratieset blob store. In de innamefase kopieert AzCopy klodders van de blob store van de migratieset naar de AEM as a Cloud Service blob store van de bestemming.

## Belangrijke overwegingen voordat u begint {#important-considerations}

Volg de onderstaande sectie om de belangrijke overwegingen te begrijpen voordat u begint:

* Vanaf versie 2.0.16 van CTT wordt de precoy-instelling automatisch uitgevoerd wanneer de bundel is geïnstalleerd. Als de ingestelde migratie groter is dan 200 GB, wordt in het extractieproces automatisch de functie voor precopy gebruikt. Het bestand azcopy.config wordt gemaakt in de map crx-quickstart/cloud-migration/. U te hoeven niet manueel de precoyopstelling te doen als u CTT versie 2.0.16 of later gebruikt.

* Source AEM moet 6.3 - 6.5 zijn.

* Source AEM Data Store is geconfigureerd voor gebruik van Amazon S3 of Azure Blob Storage. Voor meer details, zie [ het Vormen knoopopslag en gegevensopslag in AEM 6 ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html).

* Elke migratieset kopieert de volledige gegevensopslag, zodat slechts één migratieset zou moeten worden gebruikt.

* U hebt toegang nodig om [ AzCopy ](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) op de instantie (of VM) te installeren die de bronAEM instantie in werking stellen.

* De Inzameling van het huisvuil van de Opslag van gegevens is in de voorafgaande zeven dagen op de bron in werking gesteld. Voor meer details, zie {de inzameling van het huisvuil van de 0} opslag van Gegevens [.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#data-store-garbage-collection)

### Aanvullende overwegingen als de AEM-broninstantie is geconfigureerd voor het gebruik van een Amazon S3- of Azure Blob Storage Data Store {#additional-considerations-amazons3-azure}

* Er zijn kosten verbonden aan de overdracht van gegevens uit Amazon S3 en Azure Blob Storage. De overdrachtskosten zijn relatief ten opzichte van de totale hoeveelheid gegevens in uw bestaande opslagcontainer (al dan niet vermeld in AEM). Zie [ Amazon S3 ](https://aws.amazon.com/s3/pricing/) en [ Azure BlobOpslag ](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) voor meer details.

* U hebt een toegangstoets en een geheim sleutelpaar nodig voor de bestaande bron Amazon S3 bucket, of een SAS URI voor de bestaande bron Azure Blob Storage container (alleen-lezen toegang is prima).

### Aanvullende overwegingen als de AEM-broninstantie is geconfigureerd voor het gebruik van File Data Store {#additional-considerations-aem-instance-filedatastore}

* Het lokale systeem moet vrije ruimte hebben strikt groter dan 1/256 grootte van de brondatastore. Als de datastore bijvoorbeeld 3 terabytes groot is, moet er vrije ruimte van meer dan 11,72 GB aanwezig zijn in de map `crx-quickstart/cloud-migration` op de bron, anders werkt AzCopy niet. Het bronsysteem moet minstens 1 GB vrije ruimte hebben. Vrije ruimte kan worden verkregen door `df -h` bevel op instanties Linux®, en dir bevel in de instanties van Vensters te gebruiken.

* Telkens wanneer de extractie wordt uitgevoerd met AzCopy ingeschakeld, wordt de volledige bestandsdatastore afgevlakt en naar de container voor cloudmigratie gekopieerd. Als uw migratieset kleiner is dan de grootte van uw datastore, is de extractie van AzCopy niet de optimale benadering.

* Als AzCopy eenmaal is gebruikt om over de bestaande datastore te kopiëren, schakelt u deze uit voor delta- of top-up extracties.

## AzCopy instellen als een stap vóór kopiëren {#setting-up-pre-copy-step}

>[!NOTE]
>Vanaf versie 2.0.16 van CTT wordt de precoy-instelling automatisch uitgevoerd wanneer de bundel is geïnstalleerd. Als de ingestelde migratie groter is dan 200 GB, wordt in het extractieproces automatisch de functie voor precopy gebruikt. Het bestand azcopy.config wordt gemaakt in de map crx-quickstart/cloud-migration/. Als u de configuratie van het bestand handmatig wilt bijwerken, bekijkt u de onderstaande secties.

Volg deze sectie zodat u kunt leren hoe u opstelling om AzCopy als pre-exemplaarstap met het Hulpmiddel van de Overdracht van de Inhoud te gebruiken om de inhoud aan AEM as a Cloud Service te migreren:

### &#x200B;0. Bepaal de totale grootte van alle inhoud in de gegevensopslag {#determine-total-size}

Het is om twee redenen belangrijk om de totale grootte van de gegevensopslag te bepalen:

* Als de bron-AEM is geconfigureerd om de gegevensopslag van het bestand te gebruiken, moet het lokale systeem over voldoende vrije ruimte beschikken die strikt groter is dan de grootte 1/256 van de gegevensopslagruimte van de bron.

#### Azure Blob Storage Data Store {#azure-blob-storage}

Van de bestaande containereigenschappen pagina in het Azure portaal, gebruik **berekent grootte** knoop om de grootte van al inhoud in de container te bepalen. Bijvoorbeeld:

![afbeelding](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 Data Store {#amazon-data}

U kunt het tabblad Metriek van de container gebruiken om de grootte van alle inhoud in de container te bepalen. Bijvoorbeeld:


![afbeelding](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### Bestandsgegevensopslag {#file-data-store-determine-size}

* Voor Mac, UNIX® systemen, stel het du bevel op de datastore folder in werking om zijn grootte te krijgen:
  `du -sh [path to datastore on the instance]`. Als uw datastore bijvoorbeeld op `/mnt/author/crx-quickstart/repository/datastore` staat, krijgt u met de volgende opdracht de grootte: `du -sh /mnt/author/crx-quickstart/repository/datastore` .

* Voor Vensters, gebruik het dir bevel op de datastore folder om zijn grootte te krijgen:
  `dir /a/s [location of datastore]`.

### &#x200B;1. Installeer AzCopy {#install-azcopy}

[ AzCopy ](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) is een bevel-lijn hulpmiddel dat door Microsoft® wordt verstrekt dat op de broninstantie beschikbaar moet zijn om deze eigenschap toe te laten.

Kortom, wilt u het binaire getal Linux® x86-64 van de [ AzCopy docs pagina ](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) downloaden en het untar aan een plaats zoals /usr/bin.

>[!IMPORTANT]
>Noteer waar u het binaire bestand hebt geplaatst, omdat u het volledige pad naar het binaire bestand in een latere stap nodig hebt.

### &#x200B;2. Installeer de CTT-release (Content Transfer Tool) met ondersteuning voor AzCopy {#install-ctt-azcopy-support}

>[!IMPORTANT]
>De laatst vrijgegeven versie van CTT moet worden gebruikt.

AzCopy-ondersteuning voor Amazon S3, Azure Blob Storage en File Data Store is inbegrepen in de nieuwste CTT-release.
U kunt de recentste versie van CTT van het [ portaal van de Distributie van de Software downloaden ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).
Er zij op gewezen dat alleen versies 2.0.0 en hoger worden ondersteund en dat het raadzaam is de meest recente versie te gebruiken.

### &#x200B;3. Configureer een bestand azcopy.config {#configure-azcopy-config-file}

Maak in `crx-quickstart/cloud-migration` in de AEM-broninstantie een bestand met de naam `azcopy.config` .

>[!NOTE]
>De inhoud van dit configuratiebestand is anders, afhankelijk van het feit of uw AEM-broninstantie een Azure- of Amazon S3-gegevensopslag of File-gegevensopslag gebruikt.

#### Azure Blob Storage Data Store {#azure-blob-storage-data}

Het bestand azcopy.config moet de volgende eigenschappen bevatten (gebruik de juiste azCopyPath en azureSas voor uw instantie).

>[!NOTE]
>
> Als u geen schrijftoegang wilt verlenen tot de bestaande blob opslagcontainer, kunt u een nieuwe SAS URI produceren die slechts Gelezen en van de Lijst toestemmingen heeft.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3 Data Store {#amazon-sdata-store}

Het bestand azcopy.config moet de volgende eigenschappen bevatten (gebruik de juiste waarden voor de instantie).

>[!NOTE]
>
> Als uw instantie de Rollen van IAM gebruikt om AEM toe te laten om tot S3 toegang te hebben, moet u een beleid en een gebruiker met de acties tot stand brengen ListBucket en GetObject die voor het S3 emmertje worden toegelaten. Gebruik de toegangstoets en de geheime sleutel van deze gebruiker nadat u deze hebt ingesteld.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

#### Bestandsgegevensopslag {#file-data-store-azcopy-config}

Het `azcopy.config` -bestand moet de eigenschap azCopyPath en een optionele eigenschap repository.home bevatten die naar de locatie van de datastore van het bestand wijst. Gebruik de juiste waarden voor de instantie.
Bestandsgegevensopslag

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

De eigenschap azCopyPath moet het volledige pad bevatten van de locatie waar het opdrachtregelprogramma azCopy op de AEM-broninstantie is geïnstalleerd. Als de eigenschap azCopyPath ontbreekt, wordt de voorbeeldstap niet uitgevoerd.

Als de eigenschap `repository.home` ontbreekt in azcopy.config, wordt de standaarddatastore-locatie `/mnt/crx/author/crx-quickstart/repository/datastore` gebruikt om de precisie uit te voeren.

### &#x200B;4. Uitpakken met AzCopy {#extracting-azcopy}

Als het bovenstaande configuratiebestand is geïnstalleerd, wordt de voorkopieerfase van AzCopy uitgevoerd als onderdeel van elke volgende extractie. Als u wilt voorkomen dat het bestand wordt uitgevoerd, kunt u de naam van het bestand wijzigen of het bestand verwijderen.

>[!NOTE]
>Als AzCopy niet correct wordt gevormd, zou u het volgende bericht in de logboeken zien:
>>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Begin een extractie van CTT UI. Zie [ Begonnen het Worden met het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/getting-started-content-transfer-tool.md) en het [ Proces van de Uitwinning ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) voor meer details.

1. Bevestig dat de volgende regel wordt afgedrukt in het extractielogboek:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Gefeliciteerd! Deze logbestandvermelding betekent dat uw configuratie als geldig is beschouwd en dat AzCopy alle lobs van de broncontainer naar de migratiecontainer kopieert.

De logboekingangen van AzCopy verschijnen in het extractielogboek, en met c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy vooraf bepaald - [ AzCopy ]

>[!CAUTION]
>
> De eerste paar minuten van een extractie bekijken de extractielogboeken nauwkeurig op tekenen van een probleem. Als voorbeeld, is hier wat zou worden geregistreerd als de bron Azure container niet kon worden gevonden:

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason > github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

Als er een probleem is met AzCopy, mislukt de extractie direct en bevatten de extractielogboeken details over de fout.

Alle blobs die vóór de fout zijn gekopieerd, worden automatisch door AzCopy overgeslagen bij volgende uitvoering en hoeven niet opnieuw te worden gekopieerd.

>[!TIP]
>Een opname kan nu automatisch worden gepland om onmiddellijk te beginnen nadat een extractie is gelukt. Zie [ Ingesterend Inhoud in Doel ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor meer informatie.

>[!TIP]
>Als de blob-overdracht met AzCopy enige tijd vorderde maar vervolgens voor slechts enkele lobs is mislukt, voert u de extractie opnieuw uit met de opties PreCopy en Overschrijven container voor Staging uitgeschakeld. Hiermee migreert u alleen de resterende kloven die niet eerder zijn overgedragen.

#### Voor de opslag van bestandsgegevens {#file-data-store-extract}

Wanneer AzCopy voor source file dataStore loopt, zou u berichten als deze in de logboeken moeten zien erop wijzen die dat de omslagen worden verwerkt:
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### &#x200B;5. Bijwerken met AzCopy {#ingesting-azcopy}

Zie [ Ingesterend Inhoud in Doel ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) voor algemene informatie over het opnemen van inhoud in het doel van Cloud Acceleration Manager (CAM), met inbegrip van instructie op hoe te om AzCopy (pre-copy), of niet, in de &quot;Nieuwe Dialoog van de Ingestie&quot;te gebruiken.

Als u AzCopy tijdens het gebruik wilt gebruiken, moet u beschikken over een AEM as a Cloud Service-versie die ten minste versie 2021.6.5561 is.

Zie de lijst Ingestietaken in de Cloud Acceleration Manager en de logboeken van de opname zodat u de voortgang kunt zien. De logbestandvermeldingen met betrekking tot de
geslaagde AzCopy-taken worden als volgt weergegeven (waarbij rekening wordt gehouden met enkele verschillen). Als u de logboeken zo nu en dan controleert, kan dit problemen veroorzaken
vroeg, en hulp u een snelle oplossing voor om het even welke problemen vinden.

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination does not have full folder support
INFO: azcopy: A newer version 10.11.0 is available to download
 
Job 419d98da-fc05-2a45-70cc-797fee632031 has started
Log file is located at: /root/.azcopy/419d98da-fc05-2a45-70cc-797fee632031.log
 
0.0 %, 0 Done, 0 Failed, 886 Pending, 0 Skipped, 886 Total,
 
Job 419d98da-fc05-2a45-70cc-797fee632031 summary
Elapsed Time (Minutes): 0.0334
Number of File Transfers: 886
Number of Folder Property Transfers: 0
Total Number of Transfers: 886
Number of Transfers Completed: 17
Number of Transfers Failed: 0
Number of Transfers Skipped: 869
TotalBytesTransferred: 248350
Final Job Status: CompletedWithSkipped
 
*************** Completed AzCopy pre-copy phase ***************
```

## Volgende functies {#whats-next}

U hebt nu geleerd hoe u grote opslagplaatsen voor inhoud kunt verwerken om de extractie- en insluitingsfasen van de activiteit voor de overdracht van inhoud te versnellen en inhoud naar AEM as a Cloud Service te verplaatsen. U kunt nu het extractieproces leren met het gereedschap Inhoud overbrengen. Zie [ het Uithalen Inhoud van Source in het Hulpmiddel van de Overdracht van de Inhoud ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) zodat kunt u leren hoe te om uw migratie uit het Hulpmiddel van de Overdracht van de Inhoud wordt geplaatst te halen.
