---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 90e1ca38bd517215a631573987462a716bfed160
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 18459 {#18459}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 18459 samengevat, die op 5 november 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 18311.

De activering van de 2024.11.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-18459}

* CQ-4357471: Voeg ondersteuning toe voor i18n-woordenboeken omzetten in AEMaaCS.
* SITES-23591: Content Fragments: Content fragment upgrade for UID support.
* SITES-25440: Inhoudsfragmenten: CFM Search API om replicatiestatus weer te geven.
* SITES-24369: Content Fragments: OpenAPI documentatieverbeteringen.
* SITES-25478: Content Fragments: Add back-end support for external asset references.
* SITES-26119: Content Fragments: Add support of external asset references in reference type.
* SITES-21199: Edge Delivery met Universal Editor: voeg ondersteuning toe voor sjablonen die op basis van pagina&#39;s zijn gemaakt.
* SITES-20311: Edge Delivery met Universal Editor: voeg ondersteuning toe voor het importeren van CSV&#39;s in spreadsheets.
* SITES-24821: Edge Delivery met Universal Editor: zorg dat aem.page / aem.live de standaardinstelling is voor integratie met Edge Delivery.

### Opgeloste problemen {#fixed-issues-18459}

* CQ-4358730: CQPagePreviewGenerator mislukt als er meer dan 10 toetsen moeten worden vertaald.
* FORMS-14978: Pagina laden inschakelen voor een formulier op basis van kerncomponenten voor themaceredacteur.
* FORMS-16596: Toegankelijkheidsprobleem: uitgeschakelde knoppen niet herkend door Screen Reader.
* SITES-10575: MSM: Vervagings-bloomfilter Loader probeert meer dan 100.000 rijen te laden.
* SITES-20755: Inhoudsfragmenten: Verwijzing naar element met UUID vernieuwen geeft de miniatuur niet aan.
* SITES-26253: Inhoudsfragmenten: UUID-migratie: Wijzig het onderwerp van de schrijftaak om generiek te zijn.
* SITES-21338: Content Fragments: referencedBy eindpunt keert niet de correcte paginaverwijzing terug.
* SITES-24421: De Fragmenten van de inhoud: geef het eindpunt van CF uit werkt niet voor CF die via GET CF wordt teruggewonnen.
* SITES-25461: Inhoudsfragmenten: Filter op model in zoekopdracht naar CF&#39;s moet niet hoofdlettergevoelig zijn.
* SITES-25471: Content Fragments: Fix validation of global models in the ModelValidatorServlet.
* SITES-25795: Content Fragments: CF Model API ontbreekt wanneer er geen cq datum wordt geplaatst.
* SITES-25817: Inhoudsfragmenten: Verbeteren, starten: laatste promotie bijwerken voor CF-opstarters.
* SITES-26030: Inhoudsfragmenten: Endpoint /referencesTree retourneert geen benodigde header.
* SITES-26031: De Fragmenten van de inhoud: De status van de replicatie is niet teruggekeerd op CFM onderzoekseindpunt.
* SITES-26213: Content Fragments: Unpublish content fragments should only validate published references.
* SITES-26226: Inhoudsfragmenten: workflowprobleem starten wanneer geen van de opgegeven paden bruikbaar is.
* SITES-26238: Inhoudsfragmenten: De elementverwijzingen die door de API worden geretourneerd, hebben een andere volgorde dan de volgorde van JCR.
* SITES-25456: Gebeurtenissen: wanneer u een pagina verplaatst, wordt naast de gebeurtenis die door de pagina wordt verplaatst, een gebeurtenis gegenereerd die door de pagina wordt verwijderd.
* SITES-25658: Gebeurtenissen: De laag en sourceUrl worden niet gevuld in de gebeurtenissen van de paginacontrolestatus.
* SITES-6497: Launches: Create page in launch does not working.
* SITES-25938: Launches: Unexpected delete post Translation project.
* SITES-25393: Edge Delivery met Universal Editor: tekstknooppunten die verloren gaan bij het renderen van opgemaakte richtext met één alinea.
* SITES-24643: Edge Delivery with Universal Editor: OpenGraph- en twitter-metagegevenskenmerken werken niet in het metagegevensmodel van de pagina.
* SITES-25401: Experience Fragments: Trage XF referentie update


### Bekende problemen {#known-issues-18459}

Geen.

### Verouderde functies en API&#39;s {#deprecated-18459}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-18459}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 21 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-18459}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 70,0 | [ Oak API 1.70.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
