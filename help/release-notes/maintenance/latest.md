---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 0dab7428d8ae5ec4c11a88ff310fad649a365868
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 1%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13665 {#release-13665}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13665 samengevat, die op 27 september 2023 openbaar werd gemaakt. Deze onderhoudrelease vervangt release 13420.

2023.10.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13665}

* Verschillende verbeteringen in de API&#39;s voor inhoudsfragmenten.
* ASSETS-26713: Assets-dashboard: het nieuwe Experience UI-dashboard is nu bereikbaar via Touch UI.
* SITES-11206: Content Fragments: Search API for Content Fragments.
* SITES-11262: Inhoudsfragmenten: knop om over te schakelen naar de nieuwe Inhoudsfragmenteditor.
* SITES-15447: Core Components: Release van versie 2.23.4.

### Opgeloste problemen {#fixed-issues-13665}

* Verschillende vertalingen.
* CQ-4354428: Workflows: kan een taak in Postvak IN niet voltooien.
* SITES-9733: Content Fragments: Asset References in content fragment reference panel shows 0(zero) references.
* SITES-14561: Inhoudsfragmenten: Vaste en verbeterde HTML naar Markup-conversie.
* SITES-14882: Inhoudsfragmenten: als we het inhoudsfragment bewerken en het tabblad sluiten zonder op de knop Opslaan of Sluiten te klikken, worden de waarden opgeslagen.
* SITES-15167: Inhoudsfragmenten: het repareren van een variatie met een ongeldige lading retourneert niet 400, maar 500.
* SITES-15514: Content Fragments: Malformed Markdown output voor lijst binnen RTE.
* SITES-15661: Inhoudsfragmenten: gebruik geen unieke restrictie en wijzig de volgorde van items in verwijzingsvelden in de API Fragments.
* SITES-15730: Schermen: functionaliteit voor kanaalvoorvertoning werkt niet op het dashboard.
* SITES-15995: Inhoudsfragmenten: MIME-typen van zowel model- als fragmentlange tekstvelden worden gecodeerd.
* SITES-16074: Inhoudsfragmenten: Tagvelden die geen tekenreeks zijn[] kan niet van JCR worden opgehaald.
* SITES-16084: Inhoudsfragmenten: CFHomeCardModelImpl ontbreekt de doelnavigator.
* SITES-14773: De Fragmenten van de ervaring: De Verwijzing van de verbinding wordt niet bijgewerkt binnen ervaringsfragment.
* SITES-14899: De Fragmenten van de Ervaring: Veelvoudige aanbiedingen die voor XF variaties in Doel worden gecreeerd.
* SITES-8590: GraphQL: De coderingskwesties met variabelen in persisted query.
* SITES-9224: GraphQL: de uitzondering Writer is al gesloten in GraphQLServlet.
* SITES-14800: GraphQL: Exception in persisted GraphQL query&#39;s with variables.
* SITES-15586: GraphQL: Issue with persisted query filtering with null values.
* SITES-15622: GraphQL: Probleem met aanhoudende query&#39;s met getallen en bool parameters.
* SITES-15654: GraphQL: Issue with union &amp; properties with same name.
* SITES-15267: Opstarten: Bij de promotie worden geen opstartiepagina&#39;s opgehaald die zijn gewijzigd voordat de startconfiguratie werd gewijzigd.
* SITES-15406: Start: kan geen startpagina toevoegen.
* SITES-15427: Launches: Inconsistent gedrag van het bereik &quot;Huidige pagina en subpagina&#39;s bevorderen&quot;.
* SITES-15429: Launches: pagina&#39;s ontwerpen verwijderd tijdens het promoten van startpagina&#39;s.
* SITES-15462: Launches: Automatische promotieprocedure publiceert pagina&#39;s die buiten het promotiebereik vallen.
* SITES-15815: Launches: Verwijderde pagina uit Launch zorgt ervoor dat Starten niet correct wordt bevorderd.
* SITES-15223: Pagina-editor: kan componenten niet vergroten of verkleinen in emulator voor tabletgrootte.
* SITES-15463: Paginasjablonen: sjablonen kunnen niet worden gepubliceerd.

### Bekende problemen {#known-issues-13665}

Geen

### Ingesloten technologieën {#embedded-tech-13665}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM | 1,54-T20230817132355-3800a65 | [API 1.54.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
