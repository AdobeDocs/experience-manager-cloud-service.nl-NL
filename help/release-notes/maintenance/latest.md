---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 23ebeb259e5955bd51431844fd67db9b363034ea
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 19823 {#19823}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 19823 samengevat, die op 4 maart 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 19687.

De activering van de 2025.3.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-19823}

* ASSETS-46491: OSGI-gebeurtenishandler voor statuswijziging van activaverwerking.
* ASSETS-45613: Verzend unpublish-gebeurtenissen wanneer elementen worden verwijderd of verplaatst.
* ASSETS-45131: Ondersteuning voor aangepaste tags in Content Hub.

### Opgeloste problemen {#fixed-issues-19823}

* ASSETS-20433: Problemen met het opnemen van dynamische media met PDF&#39;s die met een wachtwoord zijn beveiligd.
* ASSETS-24675: Afbeeldingsverwerkingsopties worden niet weergegeven voor afbeeldingsprofielen met alleen stalen.
* ASSETS-41257: Vergelijking van de versie van middelen zorgt voor een onjuiste hoogte-breedteverhouding. Elementversies worden in onjuiste volgorde in de tijdlijn weergegeven.
* ASSETS-44894: bladwijzers in de Assets-weergave kunnen mogelijk niet worden aangeklikt.
* ASSETS-45015: Breedte en hoogte van slim uitsnijden ingesteld op nul als greep van slim uitsnijdmiddel niet wordt gevonden.
* ASSETS-45192: Verlaag de pulsaanvraagfrequentie.
* ASSETS-45724: Controleer of het uploaden naar de DM opnieuw wordt geprobeerd als de uploadtaak niet is toegewezen.
* ASSETS-46425: Problemen met Adobe Stock-integratiezoekopdrachten.
* ASSETS-27400: de generator van de de voorproef van de omslag zou kunnen proberen origineel te openen.
* CQ-4358722: Andere landinstellingscodes verwerken in Java 11 en Java 17.
* SITES-29369: Pagina gepubliceerd/Niet-gepubliceerde gebeurtenissen geactiveerd bij activering/deactivering van bedrijfsmiddelen.
* SITES-24074: Verbeter toetsenbordtoegankelijkheid onder één shell.
* SITES-28058: Assets-maptitel wordt niet overgedragen naar live kopie.

### Bekende problemen {#known-issues-19823}

Geen.

### Verouderde functies en API&#39;s {#deprecated-19823}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-19823}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt zes geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-19823}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 76,0 | [ Oak API 1.76.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 27,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
