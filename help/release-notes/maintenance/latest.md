---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: f12e60cdfce24dd2f6c1400157180d16b1b98653
workflow-type: tm+mt
source-wordcount: '998'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17393 {#release-17393}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17393 samengevat, die op 13 augustus 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 17258.

De activering van de 2024.8.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17393}

* FORMS-15436 - Gracously behandelt uitzondering in de planner van de Status van Adobe Sign.
* FORMS-15362 - Voeg configuratie voor vorm-stichting in middelen toe om login toe te laten.
* FORMS-15261 - SPA wordt niet weergegeven in de Forms-editor.
* FORMS-15138 - Verwerking voor Dubbele gegevens achterwaartse verenigbaarheid toe te schrijven aan sling commons json verbetering.
* FORMS-15113 - De Veranderende Zeer belangrijke naam in sid from vistorId voor het volgen RUM.
* FORMS-15103 - Assets die in een formulier is bijgevoegd, wordt niet gepubliceerd bij levering aan de rand.
* FORMS-15082 - JSON-schema om toe te wijzen aan aangepaste formuliercomponenten.
* FORMS-15002 - Sjabloontype-registratie van v1-fragmenten.
* FORMS-14845 - Ondersteuning voor xdpRef in basisonderdelen van kerncomponenten via formulierbeheer.
* FORMS-14840 - Forms Prefill Service-fouten.
* FORMS-14836 - Verbeter vormen manager UI, aan lijst AF1 fragmentmalplaatjes.
* FORMS-14834 - Sjabloonondersteuning voor fragmenten in AF1.
* FORMS-14275 - Het met voeten treden van Dank u pagina en Dank u Bericht in Embed Container.
* FORMS-13623 - Functionaliteit voor het automatisch opslaan van tijd inschakelen voor V2.
* FORMS-8651 - Waarschuwingsvenster voor het wijzigen van de configuratie van het gegevensmodel op de pagina met formuliereigenschappen.
* SITES-23310 - Content Fragments REST API: Prevent Circular Dependency in Nested References for Content Fragments.
* SITES-23285 - de Fragmenten van de Inhoud REST API: creeer eindpunt om van alle beschikbare Talen een lijst te maken.
* SITES-22857 - Content Fragments REST API: Checkbox enumeration fields should not allow multiple property set to false.
* SITES-22813 - Content Fragments REST API: Definieer min/max eigenschappen voor opsommingsvelden.
* SITES-22031 - Content Fragments REST API: Get allowed content fragment models for a Fragment&#39;s folder.
* SITES-17640 - Content Fragments REST API: Content Fragment Publish operation validation.
* SITES-22677 - Content Fragments REST API: Win een vlakke lijst van afstammende verwijzingen terug
* SITES-22207 - Model gedupliceerd bij het maken van inhoudsfragmenten.
* SITES-23093 - Eventing: voeg tags toe aan ladingen voor gebeurtenissen van het Content Fragment Model.
* SITES-23092 - Eventing: voeg labels toe aan ladingen voor gebeurtenissen van het Fragment van de Inhoud.
* SITES-22447 - Voeg Ervaring toe de eigenschappen overervingssteun van het Fragment aan de Basis eigenschappen tabel.
* SITES-12209 - Verbeter de prestaties van de Redacteur van het Beleid door cq toe te voegen:beleid aan index.

### Opgeloste problemen {#fixed-issues-17393}

* CQ-4358028 - Kan geen project maken als de miniatuur wordt geüpload.
* CQ-4357891 - Sequence Issue of Exported XLIFF.
* CQ-4357059 - Het voltooien van de Vertaaltaak duurt uren, wat leidt tot een time-out van 503 in AEMaaCS.
* FORMS-15320 - E-mailverzending werkt niet in een basisformulier voor componenten.
* FORMS-15272 - AEM Forms - Checkbox-groep verzendt slechts 1 waarde.
* FORMS-15269 - Facing product related issues after Maintenance release 16461.
* FORMS-15174 - JsonSchemaParser isValid issue.
* FORMS-15095 - TextBox met meerdere regels kan worden uitgerekt tot voorbij het bevatten van deelvensters in AEM Forms.
* FORMS-15057 - FDM SharePoint-lijst die bijlage fout voor voorlegging > 999 werpt.
* FORMS-15011 - de Redacteur van de Kern veroorzaakt consolefout terwijl het openen van een Vorm in redacteur.
* FORMS-14809 - SDK-map wordt niet automatisch gemaakt in de gedeelde tijdelijke map.
* FORMS-14327 - Forms Service API&#39;s: extraheren gegevens:- geeft 500 responscode wanneer een niet-interactieve pdf wordt ingevoerd.
* FORMS-7475 - Sorteren werkt niet op de pagina Adaptief formulier maken.
* FORMS-3309 - Als bij het verzenden van een formulier meerdere opties zijn geselecteerd, wordt in een gegenereerde DoR slechts één optie weergegeven.
* SITES-23646 - het modeleindpunt van GraphQL ontbreekt voor modellen die met OpenAPI worden gecreeerd als de gebieden uniek bevatten.
* SITES-23637 - Content Fragments REST API: OpenAPI gebruikt niet het juiste waardetype voor opsommingen.
* SITES-23573 - Content Fragments REST API: Live-relaties worden niet gerespecteerd bij uuid-fragmenten voor GET-inhoud.
* SITES-23535 - Content Fragments REST API: Content Fragment Model enumeration multi-fields have empty values.
* SITES-23534 - Content Fragments REST API: Content Fragment Validation ClassCastException.
* SITES-23524 - Pas het modeleindpunt van GraphQL BFF aan om multi-field opsommingsgebieden te steunen.
* SITES-23467 - Content Fragments REST API: De Modellen van het onderzoek ontbreken wegens curseurkwestie.
* SITES-23327 - ArrayIndexOutOfBoundsException in AuditLogTimelineEventProvider tijdens de beschrijving van de tijdlijngebeurtenisverwerking.
* SITES-23277 - Content Fragments REST API: Content Fragment Field live relationship check should only be made for live copies.
* SITES-23232 - De bevestiging van de Douane werkt niet in nieuwe redacteur CF UI.
* SITES-23090 - Content Fragments REST API: Cannot update title of a locked Content Fragment.
* SITES-22981 - Het bevorderen van een geneste lancering die niet diep is publiceert niet.
* SITES-22870 - PathAttributesHandler.processSrcAttr ArrayIndexOutOfBoundsException.
* SITES-22814 - Content Fragments REST API: Checkbox Enumeration fragment fields values should be ordered by the keys defined in the model.
* SITES-22716 - Issue with OTB components live usage List.
* SITES-22457 - Het bevorderen van een lancering die niet diep is werkt broninhoud niet bij.
* SITES-22449 - Kan wijzigingen in inhoudsfragmenten niet opslaan na AEM P20-upgrade.
* SITES-22279 - Content Fragments REST API: Content Fragment mist het unieke kenmerk voor opsommingstypen.
* SITES-22203 - Content Fragments REST API: Align Management APIs to response the same situatie.
* SITES-21973 - Content Fragments REST API: Model mist het unieke attribuut voor opsommingstypen.
* SITES-20364 - 302 leidt het Werken niet met selecteur in URL om.
* SITES-21198 - VersionPreviewServlet: Overbodig verwijderen wordt gelijktijdig uitgevoerd op alle clusterknooppunten die samenvoegconflicten en blokken veroorzaken
* GRANITE-53094 - JS Use objects based on Repository cannot be located when using relative paths.

### Bekende problemen {#known-issues-17393}

Geen.

### Kennisgeving wijzigen {#change-notice-17393}

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [ de documentatie ](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer details.

### Verouderde functies en API&#39;s {#deprecated-17393}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Ingesloten technologieën {#embedded-tech-17393}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 66,0 | [ Oak API 1.66.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.66.0/index.html) |
| AEM SLING-API | 2.27.2. | [ Apache Sling API 2.27.2 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2,25,4 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
