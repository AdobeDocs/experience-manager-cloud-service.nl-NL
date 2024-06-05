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

De front-end pijpleiding is een mechanisme dat enkel de front-end code van uw websites kan snel opstellen die op worden gebaseerd [sitethema&#39;s](site-themes.md) en [sitesjablonen.](site-templates.md)

In plaats van de full-stack te implementeren, wordt alleen front-end code afgehandeld door deze pijplijn, waardoor het proces sneller verloopt. Bovendien kunnen front-end ontwikkelaars uw site eenvoudig en snel aanpassen zonder kennis van AEM.

De plaatsen die op plaatsmalplaatjes worden gebaseerd kunnen de front-end pijpleiding door gebrek gebruiken. Dit document beschrijft hoe u uw bestaande plaatsen kunt aanpassen om uit de front-end pijpleiding voordeel te halen.

>[!TIP]
>
>Als u niet vertrouwd met de front-end pijpleiding bent en hoe te om plaatsen snel op te stellen gebruikend het en plaatssjablonen, zie [Reis voor snel maken van sites](/help/journey-sites/quick-site/overview.md) voor een inleiding.

Als u uw bestaande site niet hebt gemaakt op basis van sitesjablonen en -thema&#39;s, kunt AEM uw site zodanig configureren dat de thema&#39;s worden geladen die worden geïmplementeerd met de Front End Pipeline boven op de bestaande clientbibliotheken.

## Technische details {#technical-details}

Wanneer u de front-end pijplijn voor een plaats activeert, AEM brengt de volgende veranderingen in uw plaatsstructuur aan.

* Alle pagina&#39;s van de site bevatten één extra CSS- en JS-bestand, dat kan worden gewijzigd door updates te implementeren via een speciale front-end pipe van Cloud Manager.
* De toegevoegde CSS- en JS-bestanden zijn aanvankelijk leeg, maar u kunt een map met &quot;themabronnen&quot; downloaden om de mapstructuur te starten waarmee u CSS- en JS-code-updates via die pijplijn kunt implementeren.
* Deze wijziging kan alleen ongedaan worden gemaakt door een ontwikkelaar door de opdracht `SiteConfig` en `HtmlPageItemsConfig` knooppunten die met deze bewerking onder worden gemaakt `/conf/<site-name>/sling:configs`.

>[!NOTE]
>
>Deze actie zal niet automatisch de bestaande cliëntbibliotheken van de plaats omzetten om de doopvont-eind pijpleiding te gebruiken. Het verplaatsen van deze bronnen van de omslag van de cliëntbibliotheek naar de front-end pijpleidingsomslag is een taak die handwerk door een front-end ontwikkelaar vereist.

## Vereisten {#requirements}

AEM kan uw bestaande plaats automatisch aanpassen om de front-end pijpleiding te gebruiken. Uw site moet [v2 of hoger van de paginacomponent van de kerncomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## Het toelaten van Voorste Pijl-Eind {#enabling}

Het toelaten van uw plaats doet van de console van Plaatsen gebruikend [Sitemlek.](site-rail.md)

1. Meld u aan bij AEM en navigeer naar uw site via **Algemene navigatie** > **Sites**.
1. Selecteer uw site in de console. Selecteer de hoofdmap van de site en geen onderliggende pagina&#39;s.
1. Selecteer uw site en open het dialoogvenster [spoorwegkiezer](/help/sites-cloud/authoring/basic-handling.md#rail-selector) links en kiest u **Site**.
1. In de **Site** rails, klik op de knop **Vooruiteinde pijplijn inschakelen**.

   ![Pijpleiding aan de voorzijde inschakelen](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vraagt u om te bevestigen met een overzicht van de aangebrachte wijzigingen. Bevestig en uw site is aangepast.

Nu is uw plaats klaar om de front-end pijpleiding te gebruiken. Meer over de front-end pijpleiding en het beheren van uw plaatsthema leren zie:

* [Het Siterail gebruiken om uw Sitethema te beheren](site-rail.md)
* [Reis voor snel maken van site](/help/journey-sites/quick-site/overview.md) - Deze documentatietraject biedt u een overzicht van het proces waarbij u snel een site implementeert met behulp van de front-end pijplijn en het hulpprogramma Snel site maken.
* [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - In dit document wordt de front-end pijplijn beschreven in de context van de full-stack en web-tier pijpleidingen.
