---
title: Afhandeling van grote opslagplaatsen voor inhoud (verouderd)
description: In deze sectie wordt de verwerking van grote opslagplaatsen voor inhoud beschreven
hide: true
hidefromtoc: true
source-git-commit: 1fb4d0f2a3b3f9a27f5ab1228ec2d419149e0764
workflow-type: tm+mt
source-wordcount: '1638'
ht-degree: 0%

---

# Afhandeling van grote opslagplaatsen voor inhoud (verouderd) {#handling-large-content-repositories}

## Overzicht {#overview}

Het kopiëren van een groot aantal lobs met het hulpmiddel van de Overdracht van de Inhoud (CTT) kan veelvoudige dagen vergen.
Als u de extractie- en innamefasen van de activiteit voor inhoudsoverdracht aanzienlijk wilt versnellen en de inhoud naar AEM as a Cloud Service wilt verplaatsen, kan CTT een hefboomwerking hebben [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) als een optionele stap vóór het kopiëren. Deze pre-exemplaarstap kan worden gebruikt wanneer de bron AEM instantie wordt gevormd om een Amazon S3, de opslag van de Gegevens van de Opslag van Azure Blob, of de Opslag van de Gegevens van het Dossier te gebruiken. Zodra deze voorstap is geconfigureerd, kopieert AzCopy in de extractiefase lobs van Amazon S3, Azure Blob Storage of File data store naar de migratieset blob store. In de innamefase kopieert AzCopy klodders van de blob store van de migratieset naar de bestemming AEM as a Cloud Service blob store.

>[!NOTE]
> Deze functionaliteit is geïntroduceerd in de CTT 1.5.4-versie.

## Belangrijke overwegingen voordat u begint {#important-considerations}

Volg de onderstaande sectie om de belangrijke overwegingen te begrijpen voordat u begint:

* De AEM van de bron moet 6.3 - 6.5 zijn.

* De gegevensopslag van de bron AEM wordt gevormd om Amazon S3 of Azure Blob Storage te gebruiken. Raadpleeg voor meer informatie [Opslaan van knooppunten en gegevensopslag configureren in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en).

* Elke migratieset kopieert de gehele gegevensopslagruimte, zodat slechts één migratieset moet worden gebruikt.

* U hebt toegang nodig om te installeren [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) op de instantie (of VM) die de bron AEM instantie uitvoert.

* De Inzameling van het huisvuil van de Opslag van gegevens is in de voorafgaande 7 dagen in werking gesteld op de bron. Raadpleeg voor meer informatie [Opruiming voor dataopslag](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection).


### Extra overwegingen als de bron AEM instantie wordt gevormd om een opslag van de Gegevens van de Opslag van de Opslag van Amazon S3 of van Azure te gebruiken {#additional-considerations-amazons3-azure}

* Aangezien er kosten zijn verbonden aan het overdragen van gegevens van zowel Amazon S3 als Azure Blob Storage, zijn de overdrachtskosten relatief ten opzichte van de totale hoeveelheid gegevens in de opslagcontainer (al dan niet vermeld in AEM). Zie [Amazon S3](https://aws.amazon.com/s3/pricing/) en [Azure Blob Storage](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) voor meer informatie .

* U hebt een toegangstoets en een geheim sleutelpaar nodig voor het Amazon S3-bronemmertje of een SAS URI voor de bron Azure Blob Storage-container (alleen-lezen is prima).

### Extra overwegingen als de bron AEM instantie wordt gevormd om de Opslag van de Gegevens van het Dossier te gebruiken {#additional-considerations-aem-instance-filedatastore}

* Het lokale systeem moet vrije ruimte hebben strikt groter dan 1/256 grootte van de brondatastore. Als de datastore bijvoorbeeld 3 TB groot is, moet er meer vrije ruimte dan 11,72 GB beschikbaar zijn in het dialoogvenster `crx-quickstart/cloud-migration` -map op de bron zodat AzCopy kan werken. Het bronsysteem moet minstens 1 GB vrije ruimte hebben. Vrije ruimte kan worden verkregen door `df -h` op Linux-instanties en opdracht dir in Windows-instanties.

* Telkens wanneer de extractie wordt uitgevoerd met AzCopy ingeschakeld, wordt de volledige datastore van het bestand afgevlakt en naar de container voor cloudmigratie gekopieerd. Als uw migratieset beduidend kleiner is dan de grootte van uw datastore, dan is de extractie AzCopy niet de optimale benadering.

* Als AzCopy eenmaal is gebruikt om over de datastore te kopiëren, schakelt u deze uit voor delta- of top-up extracties.

## AzCopy instellen als een stap vóór kopiëren {#setting-up-pre-copy-step}

Volg deze sectie om te leren hoe u AzCopy kunt instellen als een pre-kopiestap met het gereedschap Inhoud overbrengen om de inhoud te migreren naar AEM as a Cloud Service:

### 0. Totale grootte van alle inhoud in de gegevensopslag bepalen {#determine-total-size}

Het is om twee redenen belangrijk om de totale grootte van de gegevensopslag te bepalen:

* Als de bron AEM wordt gevormd om de gegevensopslag van het Dossier te gebruiken, moet het lokale systeem vrije ruimte hebben strikt groter dan 1/256 grootte van de opslag van brongegevens.

* Door de totale grootte van de gegevensopslag te weten, kunt u de extractie- en innametijden beter inschatten. Gebruik de [Berekening van gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-implementation-phase.html?lang=en#content-transfer) in [Cloud Acceleration Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/introduction-cam/overview-cam.html?lang=en) om een schatting te krijgen van de extractie- en innametijden.

#### Azure Blob Storage Data Store {#azure-blob-storage}

Van de pagina van containereigenschappen in het Azure portaal, gebruik **Grootte berekenen** om de grootte van alle inhoud in de container te bepalen. Bijvoorbeeld:

![afbeelding](/help/journey-migration/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 Data Store {#amazon-data}

U kunt het tabblad Metriek van de container gebruiken om de grootte van alle inhoud in de container te bepalen. Bijvoorbeeld:


![afbeelding](/help/journey-migration/content-transfer-tool/assets/amazon-s3-data-store.png)

#### Bestandsgegevensopslag {#file-data-store-determine-size}

* Voor MAC, de systemen van UNIX, stel het du bevel op de datastore folder in werking om zijn grootte te krijgen:
   `du -sh [path to datastore on the instance]`. Als uw datastore zich bijvoorbeeld op `/mnt/author/crx-quickstart/repository/datastore`Met de volgende opdracht krijgt u de grootte ervan: `du -sh /mnt/author/crx-quickstart/repository/datastore`.

* Voor Vensters, gebruik het dir bevel op de datastore folder om zijn grootte te krijgen:
   `dir /a/s [location of datastore]`.

### 1. AzCopy installeren {#install-azcopy}

[AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) is een opdrachtregelprogramma van Microsoft dat beschikbaar moet zijn in de broninstantie om deze functie in te schakelen.

Kortom, u zult waarschijnlijk Linux x86-64 binair van het binaire getal van willen downloaden [AzCopy-documentpagina](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) en verwijder het naar een locatie zoals /usr/bin.

>[!IMPORTANT]
>Noteer waar u het binaire bestand hebt geplaatst, aangezien u het volledige pad naar het binaire bestand in een latere stap nodig hebt.

### 2. Een CTT-release (Content Transfer Tool) installeren met ondersteuning voor AzCopy {#install-ctt-azcopy-support}

AzCopy-ondersteuning voor Amazon S3 en Azure Blob Storage is inbegrepen bij de CTT 1.5.4-release.
Ondersteuning voor File Data Store is opgenomen in de CTT 1.7.2-release. U kunt de meest recente versie van CTT downloaden van de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portaal.


### 3. Een bestand azcopy.config configureren {#configure-azcopy-config-file}

Op de bron AEM instantie, in `crx-quickstart/cloud-migration`, maakt u een nieuw bestand met de naam `azcopy.config`.

>[!NOTE]
>De inhoud van dit configuratiebestand is anders, afhankelijk van het feit of uw bron AEM instantie een Azure- of Amazon S3-gegevensopslag of File-gegevensopslag gebruikt.

#### Azure Blob Storage Data Store {#azure-blob-storage-data}

Het bestand azcopy.config moet de volgende eigenschappen bevatten (gebruik de juiste azCopyPath en azureSas voor uw instantie).

>[!NOTE]
>
> Als u liever geen schrijftoegang wilt verlenen tot de blob opslagcontainer, kunt u een nieuwe SAS URI genereren die alleen lees- en lijstmachtigingen heeft.

```
azCopyPath=/usr/bin/azcopy
azureSas=https://example-resource.blob.core.windows.net/example-container?sig=--REDACTED--
```

#### Amazon S3 Data Store {#amazon-sdata-store}

Het bestand azcopy.config moet de volgende eigenschappen bevatten (gebruik de juiste waarden voor de instantie).

>[!NOTE]
>
> Als uw instantie Rollen IAM gebruikt om AEM toe te laten om tot S3 toegang te hebben, zult u een beleid en een gebruiker met de acties moeten tot stand brengen ListBucket en GetObject die voor het S3 emmertje worden toegelaten. Gebruik de toegangstoets en de geheime sleutel van deze gebruiker nadat u deze hebt ingesteld.

```
azCopyPath=/usr/bin/azcopy
s3Bucket=aem-63
s3Region=us-west-2
s3AccessKey=--REDACTED--
s3SecretKey=--REDACTED--
```

#### Bestandsgegevensopslag {#file-data-store-azcopy-config}

Uw `azcopy.config` Het bestand moet de eigenschap azcopyPath bevatten en een optionele eigenschap repository.home die naar de locatie van de datastore van het bestand wijst. Gebruik de juiste waarden voor de instantie.
Bestandsgegevensopslag

```
azCopyPath=/usr/bin/azcopy
repository.home=/mnt/crx/author/crx-quickstart/repository/datastore
```

De eigenschap azcopyPath moet het volledige pad bevatten van de locatie waar het opdrachtregelgereedschap azCopy op de AEM-instantie is geïnstalleerd. Als de eigenschap azCopyPath ontbreekt, wordt de voorbeeldstap niet uitgevoerd.

Indien `repository.home` het bezit mist van azcopy.config, toen de standaarddatastore plaats `/mnt/crx/author/crx-quickstart/repository/datastore` wordt gebruikt voor het uitvoeren van precisie.

### 4. Uitpakken met AzCopy {#extracting-azcopy}

Als het bovenstaande configuratiebestand is geïnstalleerd, wordt de voorkopieerfase van AzCopy uitgevoerd als onderdeel van elke volgende extractie. Als u wilt voorkomen dat het bestand wordt uitgevoerd, kunt u de naam van het bestand wijzigen of het bestand verwijderen.

>[!NOTE]
>Als AzCopy niet correct wordt gevormd zou u dit bericht in de logboeken zien:
>`INFO c.a.g.s.m.c.a.AzCopyCloudBlobPreCopy - Blob pre-copy is not supported`.

1. Begin een extractie van CTT UI. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) en de [Extractieproces](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en) voor meer informatie .

1. Bevestig dat de volgende regel in het extractielogboek wordt afgedrukt:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Gefeliciteerd! Deze logbestandvermelding betekent dat uw configuratie als geldig is beschouwd en dat AzCopy momenteel alle lobs van de broncontainer naar de migratiecontainer kopieert.

De logitems van AzCopy worden weergegeven in het extractielogbestand en worden voorafgegaan door c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy vooraf kopiëren]

>[!CAUTION]
>
> De eerste paar minuten van een extractie bekijken de extractielogboeken nauwkeurig op tekenen van een probleem. Als voorbeeld, is hier wat zou worden geregistreerd als de bron Azure container niet kon worden gevonden:

```
[AzCopy pre-copy] failed to perform copy command due to error: cannot start job due to error: cannot list files due to reason -> github.com/Azure/azure-storage-blob-go/azblob.newStorageError, github.com/Azure/azure-storage-blob-go@v0.10.1-0.20210407023846-16cf969ec1c3/azblob/zc_storage_error.go:42
[AzCopy pre-copy] ===== RESPONSE ERROR (ServiceCode=ContainerNotFound) =====
[AzCopy pre-copy] Description=The specified container does not exist.
[AzCopy pre-copy] RequestId:5fb674b9-201e-001b-2a5b-527400000000
[AzCopy pre-copy] Time:2021-05-26T18:18:07.5931967Z, Details: 
[AzCopy pre-copy] Code: ContainerNotFound
```

Als er een probleem optreedt met AzCopy, mislukt de extractie direct en bevatten de extractielogboeken details over de fout.

Alle blobs die vóór de fout zijn gekopieerd, worden automatisch door AzCopy overgeslagen bij volgende bewerkingen, en hoeven niet opnieuw te worden gekopieerd.

#### Voor de opslag van bestandsgegevens {#file-data-store-extract}

Wanneer AzCopy voor source file dataStore loopt, zou u berichten als deze in de logboeken moeten zien erop wijzen die dat de omslagen worden verwerkt:
`c.a.g.s.m.c.a.AzCopyFileSourceBlobPreCopy - [AzCopy pre-copy] Processing folder (1/24) crx-quickstart/repository/datastore/5d`

### 5. Inschakelen met AzCopy {#ingesting-azcopy}

Met de release van Content Transfer Tool 1.5.4 hebben we AzCopy-ondersteuning toegevoegd aan de opname van auteurs.

>[!NOTE]
>Aanbevolen wordt om opname door de auteur eerst alleen uit te voeren. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

Als u AzCopy tijdens inname wilt gebruiken, dient u over een AEM as a Cloud Service versie te beschikken die ten minste versie 2021.6.5561 is.

Begin met de auteursinvoer van CTT UI. Zie de [Inktproces](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en) voor meer informatie .
De logboekingangen van AzCopy zullen in het innamelogboek verschijnen. Ze zullen er als volgt uitzien:

```
*************** Beginning AzCopy pre-copy phase ***************
INFO: Scanning...
INFO: Failed to create one or more destination container(s). Your transfers may still succeed if the container already exists.
INFO: Any empty folders will not be processed, because source and/or destination doesn't have full folder support
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

## AzCopy uitschakelen {#disable-azcopy}

Als u AzCopy wilt uitschakelen, wijzigt u de naam van de `azcopy.config` bestand.

De azcopy-extractie kan bijvoorbeeld worden uitgeschakeld met: `mv /mnt/crx/author/crx-quickstart/cloud-migration/azcopy.config /mnt/crx/author/crx-quickstart/cloud-migration/noazcopy.config`.

## Volgende functies {#whats-next}

Als u hebt geleerd dat u grote opslagplaatsen voor inhoud moet verwerken om de extractie- en insluitingsfasen van de activiteit voor de overdracht van inhoud aanzienlijk te versnellen en inhoud naar AEM as a Cloud Service te verplaatsen, bent u nu klaar om het extractieproces in het gereedschap voor de overdracht van inhoud te leren. Zie [Inhoud uit bron extraheren in gereedschap voor inhoudsoverdracht](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) om te leren hoe u de migratieset kunt extraheren met het gereedschap Inhoud overbrengen.
