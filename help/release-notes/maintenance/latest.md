---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: a091dd6b1b69d77f9eeb50065e8946af0133f4f9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 19149 {#19149}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 19149 samengevat, die op 21 januari 2025 openbaar werd gemaakt. De vorige onderhoudrelease was release 18751.

De activering van de 2025.1.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-19149}

* ASSETS-45286: granulaire voortgang tonen voor downloadarchivering van async-taak.
* ASSETS-46296: Ondersteuning voor Dynamic Media-sjablonen in Asset Selector.
* ASSETS-44796: Fire Assets Events for DAM async assets jobs.

### Opgeloste problemen {#fixed-issues-19149}

* GRANITE-55074: zorg ervoor dat de antwoordkopballen van CORS op foutenreacties worden geplaatst.
* ASSETS-43755: Verbeteringen op het gebied van schaalbaarheid van bulkactiva hebben betrekking op.
* ASSETS-45399: Omleiden naar Assets Console na het maken van een live kopie van het element.
* ASSETS-45462: Problemen met het in cache plaatsen van browsers met miniaturen van aangepaste mappen.
* ASSETS-46398: Download- en herverwerkingsacties verbergen voor DM-sjablonen.
* ASSETS-44484: Problemen met opnieuw opslaan van Connected Assets-configuratie.
* ASSETS-44122: Bij het kopiëren naar de huidige map wordt de naam van de doelmap niet gewijzigd wanneer de taak Kopiëren naar de huidige map wordt gesynchroniseerd.
* ASSETS-44463: De knop CSV downloaden is niet zichtbaar bij het exporteren van metagegevens.
* ASSETS-45134: Verplaats een taak met de titel van de bestemming en overschrijf alle maptitels.
* ASSETS-45137: Conflicten met bulkuploads via Assets View.
* ASSETS-45758: Asset Relations krijgt een oneindige drukke/ladende animatie na het toevoegen van een relatie.
* ASSETS-44148: De gebeurtenis NODE_MOVED in AEM kan schadelijke NPE in logboeken veroorzaken.
* ASSETS-28607: JS-fout bij het instellen van aangepaste videominiatuur.
* GRANITE-55781: Verbeter groepssynchronisatie tussen Adobe Developer Console en AEM. Meer details in [ Veranderingen in de Synchronisatie van de Gebruikersgroep en van het Profiel van het Product ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).
* GRANITE-55754: zorg ervoor dat SDK-opstartscripts Java 21 ondersteunen.
* GRANITE-54248: Kan niet door alle items in de map met grote elementen bladeren.
* SCRNS-4597: De meningsverbeteringen van de de lijstmening van het resultaat van het onderzoek.


### Bekende problemen {#known-issues-19149}

Geen.

### Verouderde functies en API&#39;s {#deprecated-19149}

Bij het gebruik van de Adobe Admin Console voor machtigingsbeheer MOGEN de volgende groepen NIET worden gebruikt, aangezien zij niet meer worden gesynchroniseerd met AEM:
* AEM groepen die eindigen met _GROUP_NAME_SUFFIX.
* Productprofielen uit andere omgevingen, programma&#39;s of producten.

Voor meer details, gelieve te controleren [ Veranderingen in de Synchronisatie van de Groep van de Gebruiker en van het Profiel van het Product ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).


Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-19149}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 4 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-19149}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 72,0 | [ Oak API 1.72.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
