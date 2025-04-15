---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c5152543550b5f81bf0b79741f288b0c16648584
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 20476 {#20476}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 20476 samengevat, die op 15 april 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd gepubliceerd in 2013.

De activering van de 2025.4.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-20476}

* CNTBF-411: Voeg de mogelijkheid toe om de salesbaan te verwijderen voor het geval deze door JCR wordt geannuleerd.
* CQ-4359813: AEM Translation Kit: 20 maart.
* CQ-4359811: Granite Translation Kit: 20 maart.
* GRANITE-57863: Werk FileVault bij naar versie 3.8.4.
* GRANITE-56154: Vorm exponentiële herpogingen in eiken-segment-azure.
* GRANITE-55999: Verbeter prestaties van UserPropertiesService.
* GRANITE-55781: vermijd overtollige herconfiguratie van gebruikerslidmaatschap.
* GRANITE-53956: Upgrade Azure SDK V8 t/m V12 for eak-segment-azure.
* GRANITE-50654: Op het belangrijkste toestemmingenlusje, verwijder &quot;iedereen&quot;lading door gebrek op het vooreind.
* SKYOPS-103444: Update aan Sling ResourceResolver 1.12.6.
* SKYOPS-101147: Update caconfig impl.
* SKYOPS-97124: Voeg waarschuwingen voor de analysator toe voor verouderde versies van de SPIFly-bundel.
* SKYOPS-95826: Update runtime Java-versies naar 11.0.26 en 21.0.6.
* SKYOPS-53671: Gebruik door de klant geïnstalleerde artefacten van eigenschapmodellen op (RDE) AEM opnieuw begint.

### Opgeloste problemen {#fixed-issues-20476}

* ASSETS-49027: [ Regression ] AemRequestEventFilter breekt POST- verzoeken aan de OSGI Webconsole.
* ASSETS-44956: Kan geen dynamische mediarenditie selecteren. Scripttags moeten in de bovenste component worden geladen.
* CNTBF-410: CheckJob getId null pointer in ContentCopy Bundle.
* CNTBF-341: ContentCopy-exportindex buiten bereik.
* CQ-4355411: Knopinfo blijft beschikbaar in het dialoogvenster Gebruikersvoorkeuren.
* GRANITE-57265: De waarden van de neerwaartse selectie worden niet geselecteerd.
* GRANITE-57067 - Ontbrekend effectief beleid op UI.
* SITES-30727: slepen en neerzetten kan mislukken voor subcomponenten in de AEM-editor.
* SKYOPS-90607: Het verdelen van Banen wordt uitgevoerd in inactieve plaatsing/veranderbare inhoud.
* SKYOPS-95722: `MaxPermSize` -grootte verwijderen uit snelstartmarkeringen in AEM-SDK.
* SKYOPS-103569: bepaalde afbeeldingen kunnen niet worden geladen met Java 21: `javax.imageio.IIOException: Cannot create Sun JPEGImageReader backend` .

### Bekende problemen {#known-issues-20476}

Geen.

### Verouderde functies en API&#39;s {#deprecated-20476}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-20476}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 5 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-20476}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 78,0 | [ Oak API 1.78.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2.28.0. | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
