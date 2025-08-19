---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e92cfb15a6dfe5a8a474996f52c8a0c689f5e6
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 21994 {#21994}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 21994 samengevat, die op 19 augustus 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 21772.

De activering van de 2025.8.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Nieuwe functies  {#new-features-21994}

Geen.

### Verbeteringen {#enhancements-21994}

* GRANITE-53488: Verbeter deleteconf.json eindpuntfout behandeling.
* GRANITE-59968: Allow om REPLICATION_FORCE_READY_MILLIES te vormen.
* GRANITE-60183: Apache commons-fileupload 1.6.0.
* GRANITE-60306: Apache commons-lang tot 3.18.0.
* GRANITE-60637: Apache commons-codec naar 1.19.0.
* GRANITE-60645: Apache commons-ui 2.20.0.
* GRANITE-60663: Apache commons-text 1.14.0.
* GRANITE-60714: Mongo Java Driver 5.2.
* GRANITE-60778: FileVault 4.0.0.
* GRANITE-60823: Jackrabbit 2.2.2.
* GRANITE-60967: Creeer metriek voor het volgen van clientlib compilatietijd.
* SKYOPS-105469: Steun voor acsredirectMgr in autofix api toevoegen.
* SKYOPS-113929: Voeg metriek toe voor replicatieluchtcontrole.
* SKYOPS-84821: motor voor verkoop 2.16.6.
* SKYOPS-114322: Bump up closure compiler language in level to `ECMASCRIPT_2018`.

### Opgeloste problemen {#fixed-issues-21994}

* GRANITE-60167: De indexupdate van Async in Skyline steunt geen Csv- gegevens.
* GRANITE-60532: Wijziging van waardeschakelingen wordt niet opgenomen.
* SITES-34277: Oplossing voor een blokkeringsfout in vertaalworkflows voor pagina&#39;s.
* SKYOPS-105471: Steun dambaseredirect moeilijke situatie voor ook autofix.
* SKYOPS-109532: het toevoegen van eigenschap verwijderde verbinding als commentaar achter knevel.

#### AEM Guides {#guides-21994}

* GUIDES-26688: CSS- en paginalay-outbestanden in native PDF-sjablonen vertonen een inconsequent gedrag bij het vergrendelen van bestanden, waardoor bewerkingen mogelijk zijn, zelfs wanneer de bestanden zijn vergrendeld.
* GUIDEN-30900: Het kopiëren van een map met een groot aantal elementen uit de gebruikersinterface van Assets leidt tot een API-time-out. De verrichting blijft in het achterste eind lopen en voltooit na wat tijd, maar geen succes of mislukkingsbericht, of bericht wordt getoond in UI.
* GUIDEN-29090: In de Eigen output van PDF, verschijnt de Lijst van Index (LOI) in een niet alfabetische orde en de genestelde indextermijnen worden niet behoorlijk gegroepeerd, die de index moeilijk maken te navigeren.
* HULPLIJNEN-11227: Het kopiëren van een kaart DITA van Assets UI kopieert ook zijn in bijlage Basislijn aan de nieuwe kaart.
* GUIDEN-31506: De homepage gaat leeg wanneer één van de dossiers die in Recente dossiers widget worden vermeld op een malplaatje wordt gebaseerd de waarvan bronmalplaatje geen duimnagel omvat.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-21994}

* Apache HTTPD versie 2.4.65 introduceert wijzigingen die van invloed kunnen zijn op bepaalde configuraties vanwege nieuwe beperkingen die als onderdeel van beveiligingsoplossingen zijn geïmplementeerd. Deze oplossingen verhelpen kwetsbaarheden door ervoor te zorgen dat instructies zoals `RequestHeader set` , `edit` en `edit_r` die worden gebruikt om de header van het inhoudstype te wijzigen, nu correct worden beperkt tot aanvraagheaders. Door deze wijziging worden ongewenste wijzigingen in de reactiekoppen voorkomen, met name voor statische inhoud.

### Verouderde functies en API&#39;s {#deprecated-21994}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-21994}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt twee geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-21994}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 84,0 | [ Oak API 1.84.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [ Apache Httpd 2.4.65 ](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [ Ondersteunde versies Node.js ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
