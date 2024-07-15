---
title: Het toelaten van de Voorste Pijpleiding
description: Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema's te gebruiken om uw plaats sneller aan te passen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 0%

---

# Het toelaten van de Voorste Pijpleiding {#enable-front-end-pipeline}

Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema&#39;s te gebruiken om uw plaats sneller aan te passen.

## Overzicht {#overview}

De front-end pijpleiding is een mechanisme dat enkel de front-end code van uw websites kan snel opstellen die op [ wordt gebaseerd plaatsenthema&#39;s ](site-themes.md) en [ plaatssjablonen.](site-templates.md)

In plaats van de full-stack te implementeren, wordt alleen front-end code afgehandeld door deze pijplijn, waardoor het proces sneller verloopt. Bovendien kunnen front-end ontwikkelaars uw site eenvoudig en snel aanpassen zonder kennis van AEM.

De plaatsen die op plaatsmalplaatjes worden gebaseerd kunnen de front-end pijpleiding door gebrek gebruiken. Dit document beschrijft hoe u uw bestaande plaatsen kunt aanpassen om uit de front-end pijpleiding voordeel te halen.

>[!TIP]
>
>Als u niet vertrouwd met de front-end pijpleiding bent en hoe te om plaatsen snel op te stellen gebruikend het en plaatssjablonen, zie {de reis van de Verwezenlijking van 0} Snelle Plaats ](/help/journey-sites/quick-site/overview.md) voor een inleiding.[

Als u uw bestaande site niet hebt gemaakt op basis van sitesjablonen en -thema&#39;s, kunt AEM uw site zodanig configureren dat de thema&#39;s worden geladen die worden geïmplementeerd met de Front End Pipeline boven op de bestaande clientbibliotheken.

## Technische details {#technical-details}

Wanneer u de front-end pijplijn voor een plaats activeert, AEM brengt de volgende veranderingen in uw plaatsstructuur aan.

* Alle pagina&#39;s van de site bevatten één extra CSS- en JS-bestand, dat kan worden gewijzigd door updates te implementeren via een speciale Cloud Manager front-end pipe.
* De toegevoegde CSS- en JS-bestanden zijn aanvankelijk leeg, maar u kunt een map met &quot;themabronnen&quot; downloaden om de mapstructuur te starten waarmee u CSS- en JS-code-updates via die pijplijn kunt implementeren.
* Deze wijziging kan alleen ongedaan worden gemaakt door een ontwikkelaar, door de knooppunten `SiteConfig` en `HtmlPageItemsConfig` te verwijderen die met deze bewerking onder `/conf/<site-name>/sling:configs` worden gemaakt.

>[!NOTE]
>
>Deze actie zal niet automatisch de bestaande cliëntbibliotheken van de plaats omzetten om de doopvont-eind pijpleiding te gebruiken. Het verplaatsen van deze bronnen van de omslag van de cliëntbibliotheek naar de front-end pijpleidingsomslag is een taak die handwerk door een front-end ontwikkelaar vereist.

## Vereisten {#requirements}

AEM kan uw bestaande plaats automatisch aanpassen om de front-end pijpleiding te gebruiken. Om dit te kunnen doen, moet uw plaats [ v2 of nieuwer van de Component van de Pagina van de Componenten van de Kern gebruiken.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## Het toelaten van Voorste Pijl-Eind {#enabling}

Het toelaten van uw plaats wordt gedaan van de console van Plaatsen gebruikend het [ spoor van de Plaats.](site-rail.md)

1. Logboek in AEM en navigeer aan uw plaats via **Globale Navigatie** > **Plaatsen**.
1. Selecteer uw site in de console. Selecteer de hoofdmap van de site en geen onderliggende pagina&#39;s.
1. Met uw geselecteerde plaats, open de [ spoorselecteur ](/help/sites-cloud/authoring/basic-handling.md#rail-selector) bij de linkerzijde en kies **Plaats**.
1. In het **spoor van de Plaats**, klik de knoop **laat Voorste Pijpleiding van het Eind** toe.

   ![ laat front-end pijpleiding ](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png) toe

1. AEM vraagt u om te bevestigen met een overzicht van de aangebrachte wijzigingen. Bevestig en uw site is aangepast.

Nu is uw plaats klaar om de front-end pijpleiding te gebruiken. Meer over de front-end pijpleiding en het beheren van uw plaatsthema leren zie:

* [Het Siterail gebruiken om uw Sitethema te beheren](site-rail.md)
* [ Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) - Deze documentatierit geeft u en overzicht van begin tot eind van het proces om snel een plaats op te stellen gebruikend de front-end pijpleiding en het Snelle hulpmiddel van de Aanmaak van de Plaats.
* [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Dit document beschrijft de front-end pijpleiding in de context van de volledig-stapel en Webrijpijpleidingen.
