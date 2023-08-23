---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 10c495505b3997ec6360aa2764ead37725759cb2
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13206 {#release-13206}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13206 samengevat, die op 21 augustus 2023 openbaar werd gemaakt. Deze onderhoudrelease vervangt de releases 13173 en 13099 om een probleem op te lossen dat gevolgen heeft voor de functionaliteit van Inbox.

2023.8.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13206}

- SITES-13906: GraphQL - Upgrade to graphql-java 20.1.
- SITES-8972: GraphQL - Add option label in JSON for Enumeration data type.
- SITES-9689: GraphQL - Voeg een titel en beschrijving toe in JSON voor het gegevenstype Content Reference.
- SITES-13052: Content Fragments - Export Content Fragments to Adobe Target.

### Opgeloste problemen {#fixed-issues-13206}

- SITES-14937: MSM - de Vormen van de Output van de Overerving van de waarde van de Ouder worden van een knevel voorzien bij het klikken sparen &amp; dicht op levende exemplaren.
- SITES-14847: Content Fragments - Content Fragment Links are not highlight.
- SITES-11620: Inhoudsfragmenten - Het pad Verwijzingen is iets geknipt in de gebruikersinterface.
- SITES-14171: GraphQL - Cirkelverwijzingen worden in sommige gevallen niet afgebroken voor in cache opgeslagen gegevens.
- SITES-14577: Experience Fragments - Bulk publish werkt niet voor live kopieën.
- SITES-14341: Admin UI - Inconsistent gedrag van de knoop van &quot;Eigenschappen&quot;wanneer schrappingstoestemmingen worden verwijderd.
- SITES-11000: Interface voor beheerders - Referenties: inkomende koppelingen ontbreken op sommige pagina&#39;s.
- SITES-11559: Admin UI - Referenties: Inkomende koppelingen tonen onjuiste pagina&#39;s.
- SITES-14337: Admin UI - het openen van redacteurspagina veroorzaakt een fout in specifieke gevallen.
- SITES-13425: ContextHub - de Bar van het Menu toont niet wanneer het klikken van knoop ContextHub.
- CQ-4354266: Kan items in postvak niet openen.
- CQ-4354279: Kan activiteitenrapport niet zien onder tabblad Personalisatie.
- FORMS-9971: Wanneer een adaptief formulier wordt weergegeven in een andere landinstelling, wordt de zichtbaarheid van componenten onjuist geïnterpreteerd en toegepast.
- FORMS-9888: Wanneer een adaptief formulier is ingesteld om bij het verzenden van het formulier te worden omgeleid naar een externe URL (dank u page), wordt het formulier niet omgeleid naar de externe URL.
- FORMS-9845: Na het ontruimen van een dropdown gebruikend de regelredacteur, blijven de eerder verstrekte waarden, ondanks de veronderstelde klaring bestaan.
- FORMS-9263: Wanneer het label van een selectievakje speciale tekens bevat en een gebruiker op het selectievakje klikt, is het desbetreffende selectievakje niet ingeschakeld.
- FORMS-9254: Als een gebruiker door de tekst van de component van de Voorwaarden en bepalingen scrolt, wordt checkbox binnen de component automatisch toegelaten zelfs alvorens de gebruiker door de volledige tekst heeft geschoven.
- FORMS-9045: De scripttag lost geen externe fragmentverwijzingen op in de basis-XDP.
- FORMS-9026: Als u probeert een adaptief formulier te maken met een JSON-schema met opsommingstekens met lege tekenreeksen en validaties zonder fouten, resulteert het proces in een fout. Nadat u de pagina hebt vernieuwd, kan het formulier niet correct worden geladen. Er wordt een leeg formulier weergegeven, samen met een fout in het logbestand.
- FORMS-8964: In Android™ Chrome/Firefox kan de tekst niet worden bewerkt in de component Tekstvak als de maximale tekenlimiet is bereikt.
- FORMS-8668: Excessieve Java™-stackdumps in foutenlogboeken, ondanks functionele rendering, wat zorgt voor blokvorming van logbestanden.
- FORMS-8554: Aangepaste Forms met lui laden ingeschakeld werkt niet in de voorvertoningsmodus van de auteurinstantie.
- FORMS-8177: Wanneer de formulierservice actief is, is een uitzondering op &quot;com.adobe.aem.formsndocuments.publish.AssetReferenceProvider Kan de elementafhankelijkheden niet ophalen.&quot; voorkomt. De fout verdwijnt wanneer u de formulierservice uitschakelt.
- FORMS-3691: Sommige objecten ontbreken binnen het bereik IIFE (Direct Invoked Function Expression). Het belangrijkste doel van het gebruik van een IIFE is het creëren van een ruimte voor variabelen binnen de functie, om te voorkomen dat deze variabelen het mondiale bereik vervuilen.
- SITES-15463: Sitesjablonen - Sjablonen kunnen niet worden gepubliceerd.

### Bekende problemen {#known-issues-13206}

- SITES-15359: Inhoudsfragmenten - Het patroon van de variatienaam komt niet correct overeen met variaties die ```'_'``` in hun resourceramen.
- FORMS-10444: Adaptieve Forms-sjablonen - Sjablonen kunnen niet worden gepubliceerd (tijdelijke oplossing: distributieconsole gebruiken).
- CQ-4354191: Workflows - Aangepaste opstartcher kan vele malen worden geactiveerd vanwege replicatiemetagegevens die aanwezig zijn op nt:ungestructureerde knooppunten (workaround: updatedetectoren om eigenschappen van replicatiemetagegevens uit te sluiten om overlapping te voorkomen).
- SITES-15622: GraphQL - Issue with persisted query with number parameters.

### Ingesloten technologieën {#embedded-tech-13206}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,52-T20230629133256-25c01b8 | [API 1.52.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.52.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
