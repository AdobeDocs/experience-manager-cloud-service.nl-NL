---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 1a1eeb3b9aec839677baadf9bea67993a22f9519
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 22943 {#22943}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 22943 samengevat, die op 14 oktober 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 22758.

De activering van de 2025.10.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-22943}

* ASSETS-57809: Index definition update voor damAssetLucene-13.
* ASSETS-36521: Verbeterde DM-werkstroom voor uploaden om consistente naverwerking te garanderen.
* ASSETS-56400: nieuwe OOTB Zoom PNG-uitvoering toegevoegd voor elementen met transparantie.
* ASSETS-55326: Ingeschakelde configuratieweergave van AI-metagegevens via HTTP-gebeurtenissen.
* ASSETS-56905: Ondersteuning voor verbinding met InDesign via proxy.
* ASSETS-48286: voeg CAI-eigenschappen toe aan Algolië voor GenStudio.
* ASSETS-48653: Pas het onzichtbare watermerk toe tijdens de voorbewerkingsfase.
* ASSETS-55874: Migrating image preset from scene7 to DMWithOpenapi.
* SITES-30452: De verbeteringen van inhoud API voor ASO op het /content/definition eindpunt.

### Opgeloste problemen {#fixed-issues-22943}

* ASSETS-56301: Correctie van het exporteren van selectieve metagegevens om PredictedTags in CSV op te nemen.
* ASSETS-55543: Refactored async verwerkingslogica in een herbruikbare bundel.
* ASSETS-54789: Vaste NPE in ACLPermissionsValidator wanneer DM ACL wordt toegelaten.
* ASSETS-55888: Oplossing voor malwareuitvoering in het deelvenster UI-uitvoeringen.
* GRANITE-62236: Probleem met lokalisatie van trefwoorden opgelost in opgeslagen zoekopdrachten naar slimme verzamelingen.
* GRANITE-61875: Probleem opgelost met de hotfix voor &quot;evaluatie van ongeldige expressie&quot;, waardoor het opslaan van contentfragmenten en het downloaden van middelen wordt voorkomen.
* SITES-24074: Fixed hidden mobile navigation receiving focus during keyboard tab navigation.
* SITES-33611: Correctie van het probleem met Live Copy-overzicht voor markten met grote volumes.

#### AEM Guides {#guides-22943}

* GUIDEN-31421: Wanneer de veelvoudige kaarten DITA of de onderwerpen open zijn en één van de onderwerpen wordt gesloten, **>>** knoop die toont alle open lusjes wordt overlapt met de resterende open lusjes op de bar van het Lusje.
* GUIDES-33229: Bij het genereren van PDF&#39;s worden de filterregels in een DITAVAL-bestand genegeerd als een eigenschapsnaam een punt bevat.
* GUIDEN-33720: Wanneer het zoemen in het scherm van Vertaling UI, de Send voor Vertaling knoop beweegt zich onder de ellips en wordt toegelaten zelfs zonder enige activa die worden geselecteerd.
* GUIDES-33590: Wanneer een revisor een revisietaak voltooit of een revisietaak van de aanvrager bijwerkt zonder opmerkingen in te voeren, wordt in het bericht dat wordt verzonden de meest recente vorige opmerking weergegeven.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Verouderde functies en API&#39;s {#deprecated-22943}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-22943}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 14 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Kennisgeving wijzigen

* Deze versie bevat de volgende nieuwe versies van de productindex:
* **damAssetLucene-13**

### Ingesloten technologieën {#embedded-tech-22943}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 86,0 | [ Oak 1.86.0 API ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.86/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [ Apache Httpd 2.4.65 ](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.2. | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [ Ondersteunde versies Node.js ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
