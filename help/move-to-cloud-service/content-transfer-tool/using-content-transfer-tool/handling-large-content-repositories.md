---
title: Afhandeling van grote opslagplaatsen voor inhoud
description: In deze sectie wordt de verwerking van grote opslagplaatsen voor inhoud beschreven
exl-id: 2eca7fa6-fb34-4b08-b3ec-4e9211e94275
source-git-commit: 65847fc03770fe973c3bfee4a515748f7e487ab6
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 1%

---

# Afhandeling van grote opslagplaatsen voor inhoud {#handling-large-content-repositories}

## Overzicht {#overview}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_precopy"
>title="Afhandeling van grote opslagplaatsen voor inhoud"
>abstract="Als u de extractie- en innamefasen van de activiteit voor inhoudsoverdracht aanzienlijk wilt versnellen en de inhoud naar AEM as a Cloud Service wilt verplaatsen, kan CTT AzCopy gebruiken als een optionele stap voor het kopiëren. Zodra deze voorstap is geconfigureerd, kopieert AzCopy in de extractiefase lobs van Amazon S3 of Azure Blob Storage naar de blob-opslag van de migratieset. In de innamefase kopieert AzCopy klodders van de blob store van de migratieset naar de bestemming AEM as a Cloud Service blob store."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en#setting-up-pre-copy-step" text="Aan de slag met AzCopy als een stap Vooraf kopiëren"

Het kopiëren van een groot aantal lobs met het hulpmiddel van de Overdracht van de Inhoud (CTT) kan veelvoudige dagen vergen.
Als u de extractie- en innamefasen van de activiteit voor inhoudsoverdracht aanzienlijk wilt versnellen en de inhoud naar AEM as a Cloud Service wilt verplaatsen, kan CTT [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) gebruiken als een optionele stap voor het kopiëren. Deze pre-exemplaarstap kan worden gebruikt wanneer de bron AEM instantie wordt gevormd om een gegevensopslag van de Opslag van de Opslag van Amazon S3 of van Azure te gebruiken Blob.  Zodra deze voorstap is geconfigureerd, kopieert AzCopy in de extractiefase lobs van Amazon S3 of Azure Blob Storage naar de blob-opslag van de migratieset. In de innamefase kopieert AzCopy klodders van de blob store van de migratieset naar de bestemming AEM as a Cloud Service blob store.

>[!NOTE]
> Deze functionaliteit is geïntroduceerd in de CTT 1.5.4-versie.

## Belangrijke overwegingen voordat u begint {#important-considerations}

Volg de onderstaande sectie om de belangrijke overwegingen te begrijpen voordat u begint:

* AEM versie moet 6.3 - 6.5 zijn
* De gegevensopslag van de bron AEM wordt gevormd om Amazon S3 of Azure Blob Storage te gebruiken. Voor meer details, verwijs [Het vormen knoopopslag en gegevensopslag in AEM 6](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en).
* De volledige gegevensopslag wordt tijdens de extractie gekopieerd. Aangezien er kosten zijn verbonden aan het overdragen van gegevens van zowel Amazon S3 als Azure Blob Storage, zijn de overdrachtskosten relatief ten opzichte van de totale hoeveelheid gegevens in de opslagcontainer (al dan niet vermeld in AEM). Raadpleeg [Amazon S3](https://aws.amazon.com/s3/pricing/) en [Azure Blob Storage](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) voor meer informatie.
* Elke migratieset kopieert de gehele gegevensopslagruimte, zodat slechts één migratieset moet worden gebruikt.
* U hebt toegang nodig om [AzCopy](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) te installeren op de instantie (of VM) waarop de bron AEM instantie wordt uitgevoerd.
* U hebt een toegangstoets en een geheim sleutelpaar nodig voor het Amazon S3-bronemmertje of een SAS URI voor de bron Azure Blob Storage-container (alleen-lezen is prima).
* De Inzameling van het huisvuil van de Opslag van gegevens is in de voorafgaande 7 dagen in werking gesteld op de bron. Voor meer details, verwijs naar [de huisvuilinzameling van de opslagplaats ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html?lang=en#data-store-garbage-collection).
* De meeste gegevens over de broninstantie worden in de migratie opgenomen.

## AzCopy instellen als een stap vóór kopiëren {#setting-up-pre-copy-step}

Volg deze sectie om te leren hoe u AzCopy kunt instellen als een pre-kopiestap met het gereedschap Inhoud overbrengen om de inhoud te migreren naar AEM as a Cloud Service:

### 0. Totale grootte van alle inhoud in de gegevensopslag bepalen {#determine-total-size}

#### Azure Blob Storage Data Store {#azure-blob-storage}

Van de pagina van containereigenschappen in het Azure portaal, gebruik **berekent grootte** knoop om de grootte van al inhoud in de container te bepalen. Bijvoorbeeld:

![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/Azure-blob-storage-data-store.png)

#### Amazon S3 Data Store {#amazon-data}

U kunt het tabblad Metriek van de container gebruiken om de grootte van alle inhoud in de container te bepalen. Bijvoorbeeld:


![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets/amazon-s3-data-store.png)

### 1. AzCopy installeren {#install-azcopy}

[](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) AzCopyis is een opdrachtregelprogramma van Microsoft dat beschikbaar moet zijn in de broninstantie om deze functie in te schakelen.

Kortom, u zult zeer waarschijnlijk Linux x86-64 binair van [AzCopy docs page](https://docs.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) willen downloaden en untar het aan een plaats zoals /usr/bin. Noteer waar u het binaire bestand hebt geplaatst, aangezien u het volledige pad naar het binaire bestand in een latere stap nodig hebt.

### 2. Een CTT-release (Content Transfer Tool) installeren met ondersteuning voor AzCopy {#install-ctt-azcopy-support}

Ondersteuning voor AzCopy is opgenomen in de CTT 1.5.4-release. U kunt de recentste versie van CTT van [de portal van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) downloaden.

### 3. Een bestand azcopy.config configureren {#configure-azcopy-config-file}

Voor de bron AEM instantie, in `crx-quickstart/cloud-migration`, creeer een nieuw dossier genoemd azcopy.config.

De inhoud van dit configuratiebestand is anders, afhankelijk van het feit of uw bron AEM instantie een Azure- of Amazon S3-gegevensopslag gebruikt.

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

### 4. Uitpakken met AzCopy {#extracting-azcopy}

Als het bovenstaande configuratiebestand is geïnstalleerd, wordt de voorkopieerfase van AzCopy uitgevoerd als onderdeel van elke volgende extractie. Als u wilt voorkomen dat het bestand wordt uitgevoerd, kunt u de naam van het bestand wijzigen of het bestand verwijderen.

1. Begin een extractie van CTT UI. Raadpleeg [Aan de slag met Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) en [Extractieproces](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/extracting-content.html?lang=en) voor meer informatie.

1. Bevestig dat de volgende regel in het extractielogboek wordt afgedrukt:

```
c.a.g.s.m.commons.ContentExtractor - *************** Beginning AzCopy Pre-Copy phase ***************
```

Gefeliciteerd! Deze logbestandvermelding betekent dat uw configuratie als geldig is beschouwd en dat AzCopy momenteel alle lobs van de broncontainer naar de migratiecontainer kopieert.

De logbestandvermeldingen van AzCopy worden weergegeven in het extractielogbestand en worden voorafgegaan door c.a.g.s.m.c.azcopy.AzCopyBlobPreCopy - [AzCopy pre-copy]

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

### 5. Inschakelen met AzCopy {#ingesting-azcopy}

Met de release van Content Transfer Tool 1.5.4 hebben we AzCopy-ondersteuning toegevoegd aan de opname van auteurs.

>[!NOTE]
>Aanbevolen wordt om opname door de auteur eerst alleen uit te voeren. Hierdoor wordt de opname voor publiceren sneller wanneer deze later wordt uitgevoerd.

Als u AzCopy tijdens inname wilt gebruiken, dient u over een AEM as a Cloud Service versie te beschikken die ten minste versie 2021.6.5561 is.

Begin met de auteursinvoer van CTT UI. Raadpleeg [Ingestieproces](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/ingesting-content.html?lang=en) voor meer informatie.
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

## Volgende functies {#whats-next}

Als u hebt geleerd dat u grote opslagplaatsen voor inhoud moet verwerken om de extractie- en insluitingsfasen van de activiteit voor de overdracht van inhoud aanzienlijk te versnellen en inhoud naar AEM as a Cloud Service te verplaatsen, bent u nu klaar om het extractieproces in het gereedschap voor de overdracht van inhoud te leren. Zie [Inhoud extraheren uit bron in gereedschap Inhoud overbrengen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/extracting-content.md) om te leren hoe u de migratieset kunt extraheren uit het gereedschap Inhoud overbrengen.