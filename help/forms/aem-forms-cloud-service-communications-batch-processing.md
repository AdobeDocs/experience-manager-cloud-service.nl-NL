---
title: PDF maken zonder problemen - Maak kennis met de kunst met batterijverwerking - Uw zelfhulp gids voor het genereren van miljoenen PDF-documenten!
description: Hoe te om merkgeoriënteerde en gepersonaliseerde mededelingen tot stand te brengen?
feature: Adaptive Forms, APIs & Integrations
role: Admin, Developer, User
exl-id: 542c8480-c1a7-492e-9265-11cb0288ce98
source-git-commit: 5e3175cc4d96c89df4154ae42c5042cf9c2ca739
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# AEM Forms as a Cloud Service Communications Batch-verwerking

Via communicatie kunt u merkgeoriënteerde en gepersonaliseerde communicatie maken, samenstellen en leveren, zoals zakelijke correspondentie, documenten, instructies, claimverwerkingsbrieven, voordeelberichten, maandelijkse facturen en welkomstkits. Met communicatie-API&#39;s kunt u een sjabloon (XFA of PDF) combineren met klantgegevens om documenten te genereren in de indelingen PDF, PS, PCL, DPL, IPL en ZPL.

De mededelingen verstrekken APIs voor het op bestelling en geplande documentgeneratie. U kunt synchrone API&#39;s voor asynchrone API&#39;s (Asynchrone API&#39;s) voor het genereren van geplande documenten gebruiken:

* Synchrone API&#39;s zijn geschikt voor gebruik op aanvraag, met lage latentie en het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op handelingen van gebruikers. Het genereren van een document bijvoorbeeld nadat een gebruiker een formulier heeft ingevuld.

* Batch-API&#39;s (Asynchrone API&#39;s) zijn geschikt voor geplande toepassingen waarbij meerdere documenten met hoge doorvoer worden gegenereerd. Met deze API&#39;s worden documenten batchgewijs gegenereerd. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

<!-- The following skills are required to create templates and use HTTP APIs: 

* Understanding of Adobe Forms Designer or Acrobat Forms to create templates

* Understanding of HTTP APIs and experience of using HTTP APIs

* Basic understanding of Adobe Experience Manager -->


## Batchbewerkingen {#batch-operations}

Een batchbewerking is een proces waarbij meerdere documenten van een vergelijkbaar type voor een set records met geplande intervallen worden gegenereerd. Een batchbewerking bestaat uit twee onderdelen: Configuratie (definitie) en uitvoering.

* **Configuratie (definitie)**: Een partijconfiguratie slaat informatie over diverse activa en eigenschappen op om voor geproduceerde documenten te plaatsen. Het bevat bijvoorbeeld details over de XDP- of PDF-sjabloon en de locatie van te gebruiken klantgegevens en het opgeven van verschillende eigenschappen voor uitvoerdocumenten.

* **Uitvoering**: Om een partijverrichting te beginnen, ga de naam van de partijconfiguratie tot batch-uitvoering API over.

### Componenten van een batchbewerking {#components-of-a-batch-operations}

**de configuratie van de Wolk van de Wolk van de Ervaring**: De configuratiehulp van de Wolk van de Ervaring helpt u een instantie van Experience Manager aan klant bezeten Microsoft Azure Opslag aan te sluiten. Hiermee kunt u de referenties opgeven waarmee Microsoft Azure-account bij een klant verbinding kan maken.

**de configuratie van de Opslag van de Gegevens van de Partij (USC)**: De hulp van de de gegevensconfiguratie van de partij u vormt een specifiek geval van opslag Blob voor Partij APIs. Hiermee kunt u de invoer- en uitvoerlocaties opgeven in de Microsoft Azure Blob-opslag die eigendom is van de klant.

**Partij APIs**: Laat u een partijconfiguraties tot stand brengen en de partijlooppas uitvoeren die op deze configuraties wordt gebaseerd om een PDF of een malplaatje XDP met gegevens samen te voegen en output in PDF, PS, PCL, DPL, IPL en formaten te produceren ZPL. De mededelingen verstrekken partij APIs voor configuratiebeheer en partijuitvoering.

![ gegeven-fusie-lijst ](assets/communications-batch-structure.png)

**Opslag**: Communicatie APIs gebruikt klant bezeten Microsoft Azure Cloud opslag om klantenverslagen te halen en geproduceerde documenten op te slaan. U configureert Microsoft Azure Storage in Experience Manager Cloud Service Configuration.

**App**: Uw douanetoepassing om de Partij APIs te gebruiken om documenten te produceren en te verbruiken.

## Meerdere documenten genereren met behulp van batchbewerkingen {#generate-multiple-documents-using-batch-operations}

U kunt batchbewerkingen gebruiken om meerdere documenten met een gepland interval te genereren.

>[!VIDEO](https://video.tv.adobe.com/v/338349)

U kunt de video bekijken of de onderstaande instructies uitvoeren om te leren hoe u documenten kunt genereren met behulp van batchbewerkingen. De API verwijzingsdocumentatie die in video wordt gebruikt is beschikbaar in het formaat .yaml. U kunt het [ Band APIs ](assets/batch-api.yaml) dossier downloaden en het uploaden aan Postman om functionaliteit van APIs te controleren en langs de video te volgen.

### Voorwaarden {#pre-requisites}

Voor het gebruik van de batch-API is het volgende vereist:

* [ Microsoft Azure-opslagaccount ](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-create)
* PDF- of XDP-sjablonen
* [Gegevens die met sjablonen moeten worden samengevoegd](#form-data)
* Gebruikers met Experience Manager-beheerdersrechten

### Uw omgeving instellen {#setup-your-environment}

Voordat u een batchbewerking gebruikt:

* Klantgegevens (XML-bestanden) uploaden naar Microsoft Azure Blob Storage
* Een Cloud-configuratie maken
* Batchgegevensopslagconfiguratie maken
* Sjablonen en andere elementen uploaden naar uw Experience Manager Forms Cloud Service-exemplaar

### Klantgegevens (XML-bestanden) uploaden naar Azure Storage

Op uw Microsoft Azure Opslag, creeer [ containers ](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs) en [ upload klantengegevens (XML) ](https://docs.microsoft.com/en-us/azure/vs-azure-tools-storage-explorer-blobs#managing-blobs-in-a-blob-container) aan de [ omslagen ](https://docs.microsoft.com/en-us/azure/storage/blobs/storage-quickstart-blobs-portal) binnen de containers.

>[!NOTE]
>
>U kunt de Microsoft Azure-opslag zo configureren dat de invoermap automatisch wordt gewist of dat de inhoud van de uitvoermap op geplande intervallen naar een andere locatie wordt verplaatst. Zorg er echter voor dat de mappen niet worden gereinigd wanneer een batchbewerking die verwijst naar de mappen nog wordt uitgevoerd.

### Een Cloud-configuratie maken {#create-a-cloud-configuration}

Met de Cloud-configuratie wordt uw Experience Manager-instantie verbonden met Microsoft Azure Storage. Een cloudconfiguratie maken:

1. Ga naar Extra > Cloud Services > Azure Storage
1. Open een map als host voor de configuratie en klik op Maken. U gebruikt de algemene map of maakt een map.
1. Geef een naam op voor de configuratie en referenties waarmee u verbinding wilt maken met de service. U kunt [ deze geloofsbrieven van uw portaal van de Opslag van Microsoft Azure ](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal#view-account-access-keys) terugwinnen.
1. Klik op Maken.

Uw Experience Manager-exemplaar is nu gereed om verbinding te maken met Microsoft Azure Storage en deze te gebruiken voor het opslaan en lezen van inhoud, indien nodig.

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

Uw Experience Manager-exemplaar is nu verbonden met Microsoft Azure Storage en geconfigureerd voor het ophalen en verzenden van gegevens naar specifieke locaties op Microsoft Azure Storage.

### Sjablonen en andere elementen uploaden naar uw Experience Manager-instantie {#upload-templates-and-other-assets-to-your-AEM-instance}

Een organisatie heeft doorgaans meerdere sjablonen. Bijvoorbeeld, één malplaatje elk voor creditcardverklaringen, voordelenverklaringen, en claimtoepassingen. Upload dergelijke XDP- en PDF-sjablonen naar uw Experience Manager-exemplaar. Een sjabloon uploaden:

1. Open je Experience Manager-exemplaar.
1. Ga naar Forms > Forms en Documenten
1. Klik op Maken > Map en maak een map. Open de map.
1. Klik op Maken > Bestand uploaden en upload de sjablonen.

## batch-API gebruiken om documenten te genereren {#use-batch-API-to-generate-documents}

Als u een batch-API wilt gebruiken, maakt u een batchconfiguratie en voert u op basis van die configuratie een uitvoering uit. De API-documentatie biedt informatie over API&#39;s voor het maken en uitvoeren van een batch, overeenkomende parameters en mogelijke fouten. U kunt het [ API definitiedossier ](assets/batch-api.yaml) downloaden en het uploaden aan [ Postman ](https://go.postman.co/home) of gelijkaardige software om APIs te testen om een partijverrichting tot stand te brengen en in werking te stellen.

### Een batch maken {#create-a-batch}

Als u een batch wilt maken, gebruikt u de `POST /config` API. Neem de volgende verplichte eigenschappen op in de hoofdtekst van de HTTP-aanvraag:

* **configName**: Specificeer Unieke naam van de partij. Bijvoorbeeld: `wknd-job`
* **dataSourceConfigUri**: specificeer plaats van de configuratie van de Opslag van de Gegevens van de Partij. Het kan relatieve of absolute weg van de configuratie zijn. Bijvoorbeeld: `/conf/global/settings/forms/usc/batch/wknd-batch`
* **outputTypes**: Specificeer outputformaten: PDF en DRUK. Als u het uitvoertype PRINT gebruikt, geeft u in de eigenschap `printedOutputOptionsList` ten minste één afdrukoptie op. De afdrukopties worden bepaald door hun rendertype, zodat er momenteel geen meerdere afdrukopties met hetzelfde rendertype zijn toegestaan. De ondersteunde indelingen zijn PS, PCL, DPL, IPL en ZPL.

* **malplaatje**: Specificeer absolute of relatieve weg van het malplaatje. Bijvoorbeeld: `crx:///content/dam/formsanddocuments/wknd/statements.xdp`

Als u een relatief pad opgeeft, moet u ook een basisinhoud opgeven. Zie API-documentatie voor meer informatie over de hoofdmap van de inhoud.

<!-- For example, you include the following JSON in the body of HTTP APIs to create a batch named wknd-job: -->

U kunt `GET /config /[configName]` gebruiken om details van de partijconfiguratie te zien.

### Een batch uitvoeren {#run-a-batch}

Als u een batch wilt uitvoeren (uitvoeren), gebruikt u de `POST /config /[configName]/execution` . Als u bijvoorbeeld een batch met de naam wknd-demo wilt uitvoeren, gebruikt u /config/wknd-demo/executing. De server retourneert HTTP-antwoordcode 202 bij het accepteren van de aanvraag. De API retourneert geen lading behalve een unieke code (uitvoering-herkenningsteken) in kopbal van de reactie van HTTP voor de partijbaan die op de server loopt. U kunt de uitvoering-herkenningsteken gebruiken om de status van de partij terug te winnen.

>[!NOTE]
>
>Breng tijdens het uitvoeren van de batch geen wijzigingen aan in de corresponderende bron- en doelmappen, de configuratie van de gegevensbron en de Microsoft Azure Cloud-configuratie.

### De status van een partij controleren {#status-of-a-batch}

Gebruik `GET /config /[configName]/execution/[execution-identifier]` om de status van een batch op te halen. De uitvoering-herkenningsteken is inbegrepen in de kopbal van de reactie van HTTP voor het verzoek van de partijuitvoering.

Het antwoord op het statusverzoek bevat de statussectie. Het verstrekt details over status van de partijbaan, aantal verslagen reeds in pijplijn (reeds gelezen en die worden verwerkt), en status van elk outputType/renderType (aantal lopend, opgevolgd, en ontbroken punten). De status omvat ook de begin- en eindtijd van een batchtaak, samen met informatie over eventuele fouten. De eindtijd is -1 tot de partijlooppas eigenlijk voltooit.

>[!NOTE]
>
>* Wanneer u meerdere PRINT-indelingen aanvraagt, bevat de status meerdere items. Bijvoorbeeld PRINT/ZPL, PRINT/IPL.
>* Een batchtaak leest niet alle records tegelijk, maar de taak blijft het aantal records lezen en verhogen. De status retourneert dus -1 totdat alle records zijn gelezen.

### Gegenereerde documenten weergeven {#view-generated-documents}

Nadat de taak is voltooid, worden de gegenereerde documenten opgeslagen in de map `success` op de doellocatie die is opgegeven in de configuratie Batch Data Store. Als er fouten optreden, maakt de service een map `failure` . Het verstrekt informatie over het type en de reden van fouten.

Laten we het met behulp van een voorbeeld begrijpen: neem aan dat er een invoergegevensbestand `record1.xml` en twee uitvoertypen zijn: `PDF` en `PCL` . Vervolgens bevat de doellocatie twee submappen `pdf` en `pcl` , één voor elk uitvoertype. Laten we aannemen dat het genereren van PDF is gelukt. De submap `pdf` bevat vervolgens de submap `success` die op zijn beurt het daadwerkelijk gegenereerde PDF-document bevat `record1.pdf` . Hiermee wordt aangenomen dat PCL-generatie is mislukt. De submap `pcl` bevat vervolgens een `failure` submap die op zijn beurt een foutbestand bevat `record1.error.txt` dat details van de fout bevat. Bovendien bevat de doellocatie een tijdelijke map met de naam `__tmp__` , waarin bepaalde bestanden staan die tijdens de uitvoering van de batch zijn vereist. Deze map kan worden verwijderd als er geen actieve batchbewerkingen zijn die verwijzen naar de doelmap.

>[!NOTE]
>
>Het verwerken van een batch kan enige tijd in beslag nemen, afhankelijk van het aantal invoerrecords en de complexiteit van de sjabloon. Wacht een paar minuten voordat u doelmappen controleert op uitvoerbestanden.

## API-naslagdocumentatie

De API verwijzingsdocumentatie verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie is beschikbaar in de indeling .yaml. U kunt het [ Band APIs ](assets/batch-api.yaml) dossier downloaden en het uploaden aan Postman om functionaliteit van APIs te controleren.

>[!MORELIKETHIS]
>
>* [ Inleiding aan de Mededelingen van AEM Forms as a Cloud Service ](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [ de Architectuur van as a Cloud Service van AEM Forms voor Adaptieve Forms en Communicatie APIs ](/help/forms/aem-forms-cloud-service-architecture.md)
>* [ Communicatie Verwerking - Synchrone APIs ](/help/forms/aem-forms-cloud-service-communications.md)
>* [ Communicatie Verwerking - Partij APIs ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [ Communicatie Verwerking - Op bestelling APIs ](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)
