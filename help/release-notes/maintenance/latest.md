---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 9278ec9bb5bccd7b40cd65a120f296faba454b9c
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 18311 {#18311}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 18311 samengevat, die op 22 oktober 2024 openbaar werd gemaakt. De vorige onderhoudrelease was release 18175.

De activering van de 2024.10.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-18311}

* ASSETS-41820: Indexering verbeteringen voor de verwerking van waakhond.
* ASSETS-43720: Functionele verbeteringen in de verwerking van waakhond.
* ASSETS-42554: Prestatieverbeteringen voor grote mappen.
* SKYOPS-77603: Beheer van omleidingen door zakelijke gebruikers.

### Opgeloste problemen {#fixed-issues-18311}

* ASSETS-37534: Wijzigingen in zoekopdracht om eigenschap die wordt gebruikt voor goedkeuringsdoel, niet beschikbaar te maken.
* ASSETS-38322: Verwijder de publicatiecriteria provider config Remove publiceer gebeurteniseigenschap.
* ASSETS-40482: Toegankelijkheidsprobleem in spel/pauze en dempen/dempen in Scene7-videospeler.
* ASSETS-40593: De foutpagina treedt op nadat u op de knop &quot;Eigenschappen&quot; hebt geklikt in Assets > Bestanden.
* ASSETS-40598: Synchroniseer slimme gewassen wanneer niet-gesynchroniseerd element wordt verplaatst naar een map waarvoor synchronisatie is ingeschakeld.
* ASSETS-40743: Problemen met het activeren van het dialoogvenster Element vervangen wanneer bepaalde tekens voorkomen in de bestandsnaam.
* ASSETS-40825: Assets Search Facets verdwijnt na bewerking van zoekformulier.
* ASSETS-41007: Verwijdering op AEM laat soms verweesde Assets bij levering.
* ASSETS-41172: Dynamic Media sjablonen met speciale tekens niet toegestaan in naam.
* ASSETS-41896 : Assets genoemd in cq:discted property on the folder should NOT be published to Brand Portal.
* ASSETS-42067: Dynamic Media Templates - Download geeft een fout.
* ASSETS-42070: Dynamic Media-sjablonen - gebruikers zonder beheerdersrechten moeten toegang hebben tot Sjabloon voor maken/bewerken.
* ASSETS-42344: Connected Assets Sync verbroken - Opnieuw verbinden en advies voor klant.
* ASSETS-42620: Probleem met de voorvertoningsoptie van elementversies - laat een leeg voorbeeld zien wanneer we het element openen.
* ASSETS-42701: Probleem met levering en uitsnijden van geoptimaliseerde webafbeeldingen.
* ASSETS-42966: Async barricade kan bij vergissing worden vrijgegeven als meerdere taken hetzelfde pad hebben.
* ASSETS-43072: Dynamic Media Templates - Sjabloonverwijzingen, zoekonderbrekingen op een ongeldige referentie.
* ASSETS-43212: Problemen met internationalisatie in de editor voor het metagegevensschema.
* ASSETS-43202: oplossingen voor het selecteren van annotaties die u wilt afdrukken vanuit de tijdlijn.
* ASSETS-43502: AEM naam bestaande voorinstelling CS-afbeelding niet weergegeven op pagina Bewerken.
* ASSETS-43538: Bij het synchroniseren van een taak met kopieerelementen wordt een onjuiste eigenschap gebruikt voor het bronpad.
* ASSETS-43798: controleer eerst op bestemmingspad voordat u elementen kopieert.
* ASSETS-43945: Verhoog de wachttijd voor opnieuw proberen tot 20 minuten voor de taakwachtrij voor async-elementen.
* ASSETS-44025: De functie voor het verwijderen van elementen kan niet worden gesynchroniseerd wanneer afzonderlijke elementen zijn geselecteerd.
* SITES-26128 : Class cast-uitzondering in CreateLiveCopyStep.
* SCRNS-4551: [ SG Pools ] het kanaal van Screens die videocomponent bevatten toont &quot;Algemene Fout van de Pagina&quot;op browser voorproef en speler

### Bekende problemen {#known-issues-18311}

* FORMS-15818: Component descriptor-item `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` niet gevonden instructies in serverlogboeken. Dit zijn ongevaarlijke loginstructies.

### Verouderde functies en API&#39;s {#deprecated-18311}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-18311}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 3 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-18311}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 70,0 | [ Oak API 1.70.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
