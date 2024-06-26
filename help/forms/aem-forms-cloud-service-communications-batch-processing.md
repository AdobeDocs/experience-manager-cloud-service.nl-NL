---
title: Gemakkelijk maken van PDF, moeiteloos maken - Maak kennis met de kunst met batterijverwerking - Uw zelfhulplijn voor het genereren van miljoenen PDF-documenten!
description: Hoe te om merkgeoriënteerde en gepersonaliseerde mededelingen tot stand te brengen?
feature: Adaptive Forms, APIs & Integrations
role: Admin, Developer, User
exl-id: 542c8480-c1a7-492e-9265-11cb0288ce98
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# AEM Forms as a Cloud Service Communicatie Batch-verwerking

Via communicatie kunt u merkgeoriënteerde en gepersonaliseerde communicatie maken, samenstellen en leveren, zoals zakelijke correspondentie, documenten, instructies, claimverwerkingsbrieven, voordeelberichten, maandelijkse facturen en welkomstkits. U kunt Communicatie APIs gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, DPL, IPL, en ZPL formaten te produceren.

De mededelingen verstrekken APIs voor het op bestelling en geplande documentgeneratie. U kunt synchrone API&#39;s voor asynchrone API&#39;s (Asynchrone API&#39;s) voor het genereren van geplande documenten gebruiken:

* Synchrone API&#39;s zijn geschikt voor gebruik op aanvraag, met lage latentie en het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op handelingen van gebruikers. Het genereren van een document bijvoorbeeld nadat een gebruiker een formulier heeft ingevuld.

* Batch-API&#39;s (Asynchrone API&#39;s) zijn geschikt voor geplande toepassingen waarbij meerdere documenten met hoge doorvoer worden gegenereerd. Met deze API&#39;s worden documenten batchgewijs gegenereerd. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

<!-- The following skills are required to create templates and use HTTP APIs: 

* Understanding of Adobe Forms Designer or Acrobat Forms to create templates

* Understanding of HTTP APIs and experience of using HTTP APIs

* Basic understanding of Adobe Experience Manager -->


## Batchbewerkingen {#batch-operations}

Een batchbewerking is een proces waarbij meerdere documenten van een vergelijkbaar type voor een set records met geplande intervallen worden gegenereerd. Een batchbewerking bestaat uit twee onderdelen: Configuratie (definitie) en uitvoering.

* **Configuratie (definitie)**: Een batchconfiguratie slaat informatie op over diverse elementen en eigenschappen die moeten worden ingesteld voor gegenereerde documenten. Bijvoorbeeld, verstrekt het details over het malplaatje XDP of PDF en de plaats van klantengegevens aan gebruik samen met het specificeren van diverse eigenschappen voor outputdocumenten.

* **Uitvoering**: Als u een batchbewerking wilt starten, geeft u de naam van de batchconfiguratie door aan de API voor batchuitvoering.

### Componenten van een batchbewerking {#components-of-a-batch-operations}

**Cloud-configuratie**: Dankzij de configuratie Experience Manger Cloud kunt u een Experience Manager-exemplaar aansluiten op Microsoft Azure Storage in eigendom van klanten. Hiermee kunt u de referenties opgeven waarmee Microsoft Azure-account bij een klant verbinding kan maken.

**Configuratie gegevensopslag in batch (USC)**: Met de configuratie van batchgegevens kunt u een specifiek exemplaar van Blob-opslag configureren voor batch-API&#39;s. Hiermee kunt u de invoer- en uitvoerlocaties opgeven in de Microsoft Azure Blob-opslag die eigendom is van de klant.

**Batch-API&#39;s**: Hiermee kunt u batchconfiguraties maken en de batchbewerkingen op basis van deze configuraties uitvoeren om een PDF- of XDP-sjabloon samen te voegen met gegevens en uitvoer te genereren in de indelingen PDF, PS, PCL, DPL, IPL en ZPL. De mededelingen verstrekken partij APIs voor configuratiebeheer en partijuitvoering.

![data-merge-table](assets/communications-batch-structure.png)

**Opslag**: Communicatie-API&#39;s maken gebruik van Microsoft Azure Cloud-opslag die eigendom is van klanten, om klantgegevens op te halen en gegenereerde documenten op te slaan. U configureert Microsoft Azure Storage in Experience Manager Cloud Service Configuration.

**App**: De aangepaste toepassing waarmee u de batch-API&#39;s kunt gebruiken voor het genereren en gebruiken van documenten.

## Meerdere documenten genereren met behulp van batchbewerkingen {#generate-multiple-documents-using-batch-operations}

U kunt batchbewerkingen gebruiken om meerdere documenten met een gepland interval te genereren.

>[!VIDEO](https://video.tv.adobe.com/v/338349)

U kunt de video bekijken of de onderstaande instructies uitvoeren om te leren hoe u documenten kunt genereren met behulp van batchbewerkingen. De API verwijzingsdocumentatie die in video wordt gebruikt is beschikbaar in het formaat .yaml. U kunt de [Batch-API&#39;s](assets/batch-api.yaml) bestand maken en uploaden naar Postman om de functionaliteit van API&#39;s te controleren en de video te volgen.

### Voorwaarden {#pre-requisites}

Voor het gebruik van de batch-API is het volgende vereist:

* [Microsoft Azure Storage-account](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create)
* PDF- of XDP-sjablonen
* [Gegevens die met sjablonen moeten worden samengevoegd](#form-data)
* Gebruikers met beheerdersrechten voor Experience Managers

### Uw omgeving instellen {#setup-your-environment}

Voordat u een batchbewerking gebruikt:

* Klantgegevens (XML-bestanden) uploaden naar Microsoft Azure Blob Storage
* Een Cloud-configuratie maken
* Batchgegevensopslagconfiguratie maken
* Sjablonen en andere elementen uploaden naar uw Experience Manager Forms Cloud Service-exemplaar

### Klantgegevens (XML-bestanden) uploaden naar Azure Storage {#upload-customer-data-to-Azure-Storage}

Maak op uw Microsoft Azure Storage [containers](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs) en [klantgegevens uploaden (XML)](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs#managing-blobs-in-a-blob-container) aan de [mappen](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) in de containers.
>[!NOTE]
>
>U kunt de Microsoft Azure-opslag zo configureren dat de invoermap automatisch wordt gewist of dat de inhoud van de uitvoermap op geplande intervallen naar een andere locatie wordt verplaatst. Zorg er echter voor dat de mappen niet worden gereinigd wanneer een batchbewerking die verwijst naar de mappen nog wordt uitgevoerd.

### Een Cloud-configuratie maken {#create-a-cloud-configuration}

Met de cloudconfiguratie wordt uw Experience Manager-instantie verbonden met Microsoft Azure Storage. Een cloudconfiguratie maken:

1. Ga naar Extra > Cloud Servicen > Azure Storage
1. Open een map als host voor de configuratie en klik op Maken. U gebruikt de algemene map of maakt een map.
1. Geef een naam op voor de configuratie en referenties waarmee u verbinding wilt maken met de service. U kunt [deze gegevens ophalen van uw Microsoft Azure Storage portal](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal#view-account-access-keys).
1. Klik op Maken.

Uw Experience Manager-instantie is nu klaar om verbinding te maken met Microsoft Azure Storage en deze te gebruiken om indien nodig inhoud op te slaan en te lezen.

### Batchgegevensopslagconfiguratie maken {#create-batch-data-store-configuration}

Met de configuratie van batchgegevens kunt u containers en mappen configureren voor invoer en uitvoer. U bewaart uw klantenverslagen in de Omslag van Source en de geproduceerde documenten worden geplaatst in de Omslag van de Bestemming.

De configuratie maken:

1. Ga naar Extra > Forms > Unified Storage Connector.
1. Open een map als host voor de configuratie en klik op Maken. U gebruikt de algemene map of maakt een map.
1. Geef de titel en naam van de configuratie op. Selecteer in Opslag Microsoft Azure Storage.
1. Blader in Opslagconfiguratiepad naar en selecteer de Cloud Configuration die referenties van de Azure-opslagaccount in eigendom van de klant bevat.
1. Geef in de Source-map de naam op van de Azure Storage-container en de map met records.
1. Geef in de doelmap het pad op van de Azure Storage-container en -map waarin de gegenereerde documenten worden opgeslagen.
1. Klik op Maken.

Uw Experience Manager-instantie is nu verbonden met Microsoft Azure Storage en geconfigureerd voor het ophalen en verzenden van gegevens naar specifieke locaties op Microsoft Azure Storage.

### Sjablonen en andere elementen uploaden naar uw Experience Manager-instantie {#upload-templates-and-other-assets-to-your-AEM-instance}

Een organisatie heeft doorgaans meerdere sjablonen. Bijvoorbeeld, één malplaatje elk voor creditcardverklaringen, voordelenverklaringen, en claimtoepassingen. Upload al dergelijke XDP en PDF malplaatjes aan uw instantie van de Experience Manager. Een sjabloon uploaden:

1. Open een Experience Manager-instantie.
1. Ga naar Forms > Forms en Documenten
1. Klik op Maken > Map en maak een map. Open de map.
1. Klik op Maken > Bestand uploaden en upload de sjablonen.

## batch-API gebruiken om documenten te genereren {#use-batch-API-to-generate-documents}

Als u een batch-API wilt gebruiken, maakt u een batchconfiguratie en voert u op basis van die configuratie een uitvoering uit. De API-documentatie biedt informatie over API&#39;s voor het maken en uitvoeren van een batch, overeenkomende parameters en mogelijke fouten. U kunt de [API-definitiebestand](assets/batch-api.yaml) bestand en uploaden naar [Postman](https://go.postman.co/home) of soortgelijke software om de API&#39;s te testen om een batchbewerking te maken en uit te voeren.

### Een batch maken {#create-a-batch}

Als u een batch wilt maken, gebruikt u de opdracht `POST /config` API. Neem de volgende verplichte eigenschappen op in de hoofdtekst van de HTTP-aanvraag:

* **configName**: Geef de unieke naam van de batch op. Bijvoorbeeld: `wknd-job`
* **dataSourceConfigUri**: Geef de locatie van de configuratie Batch Data Store op. Het kan relatieve of absolute weg van de configuratie zijn. Bijvoorbeeld: `/conf/global/settings/forms/usc/batch/wknd-batch`
* **outputTypes**: Geef uitvoerindelingen op: PDF en PRINT. Als u het uitvoertype PRINT gebruikt, kunt u `printedOutputOptionsList` -eigenschap, geeft u ten minste één afdrukoptie op. De afdrukopties worden bepaald door hun rendertype, zodat er momenteel geen meerdere afdrukopties met hetzelfde rendertype zijn toegestaan. De ondersteunde indelingen zijn PS, PCL, DPL, IPL en ZPL.

* **template**: Geef het absolute of relatieve pad van de sjabloon op. Bijvoorbeeld: `crx:///content/dam/formsanddocuments/wknd/statements.xdp`

Als u een relatief pad opgeeft, moet u ook een basisinhoud opgeven. Zie API-documentatie voor meer informatie over de hoofdmap van de inhoud.

<!-- For example, you include the following JSON in the body of HTTP APIs to create a batch named wknd-job: -->

U kunt `GET /config /[configName]` om details van de partijconfiguratie te zien.

### Een batch uitvoeren {#run-a-batch}

Als u een batch wilt uitvoeren (uitvoeren), gebruikt u de opdracht `POST /config /[configName]/execution`. Als u bijvoorbeeld een batch met de naam wknd-demo wilt uitvoeren, gebruikt u /config/wknd-demo/executing. De server retourneert HTTP-antwoordcode 202 bij het accepteren van de aanvraag. De API retourneert geen lading behalve een unieke code (uitvoering-herkenningsteken) in kopbal van de reactie van HTTP voor de partijbaan die op de server loopt. U kunt de uitvoering-herkenningsteken gebruiken om de status van de partij terug te winnen.

>[!NOTE]
>
>Breng tijdens het uitvoeren van de batch geen wijzigingen aan in de corresponderende bron- en doelmappen, de configuratie van de gegevensbron en de Microsoft Azure Cloud-configuratie.

### De status van een partij controleren {#status-of-a-batch}

Als u de status van een batch wilt ophalen, gebruikt u de opdracht `GET /config /[configName]/execution/[execution-identifier]`. De uitvoering-herkenningsteken is inbegrepen in de kopbal van de reactie van HTTP voor het verzoek van de partijuitvoering.

Het antwoord op het statusverzoek bevat de statussectie. Het verstrekt details over status van de partijbaan, aantal verslagen reeds in pijplijn (reeds gelezen en die worden verwerkt), en status van elk outputType/renderType (aantal lopend, opgevolgd, en ontbroken punten). De status omvat ook de begin- en eindtijd van een batchtaak, samen met informatie over eventuele fouten. De eindtijd is -1 tot de partijlooppas eigenlijk voltooit.

>[!NOTE]
>
>* Wanneer u meerdere PRINT-indelingen aanvraagt, bevat de status meerdere items. Bijvoorbeeld PRINT/ZPL, PRINT/IPL.
>* Een batchtaak leest niet alle records tegelijk, maar de taak blijft het aantal records lezen en verhogen. De status retourneert dus -1 totdat alle records zijn gelezen.

### Gegenereerde documenten weergeven {#view-generated-documents}

Nadat de taak is voltooid, worden de gegenereerde documenten opgeslagen in de `success` map op de doellocatie die is opgegeven in de configuratie Batch Data Store. Als er om het even welke fouten zijn, leidt de dienst tot `failure` map. Het verstrekt informatie over het type en de reden van fouten.

Laten we het met behulp van een voorbeeld begrijpen: aannemen dat er een invoergegevensbestand is `record1.xml` en twee uitvoertypen: `PDF` en `PCL`. De doellocatie bevat vervolgens twee submappen `pdf` en `pcl`, één voor elk uitvoertype. Laten we aannemen dat de generatie van PDF is gelukt, dan de `pdf` submap bevat de `success` submap die op zijn beurt het daadwerkelijk gegenereerde PDF-document bevat `record1.pdf`. Laten we aannemen dat PCL-generatie is mislukt. `pcl` submap bevat een `failure` submap die op zijn beurt een foutbestand bevat `record1.error.txt` bevat details over de fout. De doellocatie bevat ook een tijdelijke map met de naam `__tmp__` die bepaalde bestanden bevat die vereist zijn tijdens de uitvoering van de batch. Deze map kan worden verwijderd als er geen actieve batchbewerkingen zijn die verwijzen naar de doelmap.

>[!NOTE]
>
>Het verwerken van een batch kan enige tijd in beslag nemen, afhankelijk van het aantal invoerrecords en de complexiteit van de sjabloon. Wacht een paar minuten voordat u doelmappen controleert op uitvoerbestanden.

## API-naslagdocumentatie

De API verwijzingsdocumentatie verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie is beschikbaar in de indeling .yaml. U kunt de [Batch-API&#39;s](assets/batch-api.yaml) bestand maken en uploaden naar Postman om de functionaliteit van API&#39;s te controleren.

>[!MORELIKETHIS]
>
>* [Inleiding tot AEM Forms as a Cloud Service Communications](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service architectuur voor adaptieve Forms- en communicatie-API&#39;s](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Communicatieverwerking - synchrone API&#39;s](/help/forms/aem-forms-cloud-service-communications.md)
>* [Communicatieverwerking - Batch-API&#39;s](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)