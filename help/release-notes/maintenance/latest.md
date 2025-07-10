---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ff500e08e31e53f5452eed6cfe06539cabe2ecdd
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 21484 {#21484}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 21484 samengevat, die op 8 juli 2025 openbaar werd gemaakt. De vorige onderhoudsrelease was release 21331.

De activering van de 2025.7.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-21484}

Geen.

### Opgeloste problemen {#fixed-issues-21484}

Geen.

#### AEM Guides {#guides-21484}

* GUIDEN-29781: Wanneer een commentaar van XML binnen een element in de mening van Source wordt toegevoegd, worden de belangrijke en het slepen ruimten rond de commentaar verloren op omschakelingsmeningen.
* GUIDEN-29078: Wanneer het openen van een onderwerp in de mening van de Auteur na browser verfrist, worden eerder toegepaste markeringen in het paneel van de Eigenschappen van het Dossier niet behouden, en het toevoegen van nieuwe markeringen beschrijft de bestaande, vooral wanneer een groot aantal markeringen voor selectie beschikbaar zijn.
* GUIDES-28214: Pogingen om overzichtstaken tot stand te brengen door het werkschema van AEM ontbreken constant omdat de overzichtsknoop niet wordt gecreeerd.
* GUIDEN-28104: Het publiceren van een kaart DITA met `chunk=to-content` attributen leidt tot dubbele knopen JCR in de nieuwe output van AEM Sites, die tot overtollige inhoudsstructuur in AEM Sites leiden.
* GUIDES-29065, GUIDES-28793: De kwesties van prestaties zoals langere ladingstijden en intermitterende onderbrekingen worden waargenomen wanneer het werken met grote inzamelingen.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-21484}

Geen.

### Verouderde functies en API&#39;s {#deprecated-21484}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-21484}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 5 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-21484}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 80,0 | [ Oak API 1.80.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
