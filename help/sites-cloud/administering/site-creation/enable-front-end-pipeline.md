---
title: Voorste pijplijn inschakelen
description: Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema's te gebruiken om uw plaats sneller aan te passen.
feature: Administering
role: Admin
source-git-commit: dc7e89c601bb02c78f65ca58eff34c15092b5561
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---


# Voorste pijplijn inschakelen {#enable-front-end-pipeline}

Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema&#39;s te gebruiken om uw plaats sneller aan te passen.

## Overzicht {#overview}

De front-end pijpleiding is een mechanisme dat enkel de front-end code van uw websites kan snel opstellen die op worden gebaseerd [sitethema&#39;s](site-themes.md) en [sitesjablonen.](site-templates.md)

In plaats van de full-stack te implementeren, wordt alleen front-end code afgehandeld door deze pijplijn waardoor het proces sneller verloopt en ontwikkelaars aan de voorkant ook in staat zijn uw site eenvoudig en snel aan te passen zonder kennis van AEM.

De plaatsen die op plaatsmalplaatjes worden gebaseerd kunnen hefboomwerking de front-end pijpleiding door gebrek. Dit document beschrijft hoe u uw bestaande plaatsen kunt aanpassen om uit de front-end pijpleiding voordeel te halen.

>[!TIP]
>
>Als u niet vertrouwd met de front-end pijpleiding bent en hoe te om plaatsen snel op te stellen gebruikend het en plaatssjablonen, te herzien gelieve [Reis voor snel maken van sites](/help/journey-sites/quick-site/overview.md) voor een inleiding.

Als u uw bestaande site niet hebt gemaakt op basis van sitesjablonen en -thema&#39;s, kunt AEM uw site zodanig configureren dat de thema&#39;s worden geladen die worden geïmplementeerd met de Front End Pipeline boven op de bestaande clientbibliotheken.

## Vereisten {#requirements}

AEM kan uw bestaande plaats automatisch aanpassen om de front-end pijpleiding te gebruiken. Om dit te kunnen doen, moet uw site [v2 of hoger van de paginacomponent van de kerncomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/page.html)

## Het toelaten van Voorste Pijl-Eind {#enabling}

Het inschakelen van uw site wordt uitgevoerd via de Sites-console.

1. Meld u aan bij AEM en navigeer naar uw site via **Algemene navigatie** > **Sites**.
1. Selecteer uw site in de console. U moet de hoofdmap van de site selecteren en geen onderliggende pagina&#39;s.
1. Selecteer uw site en open het dialoogvenster [spoorwegkiezer](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) links en kiest u **Site**.
1. In de **Site** spoor, klik de knoop **Vooruiteinde pijplijn inschakelen**.

   ![Pijpleiding aan de voorzijde inschakelen](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png)

1. AEM vraagt u om te bevestigen met een overzicht van de aangebrachte wijzigingen. Bevestig en uw site is aangepast.

Nu is uw plaats klaar om de front-end pijpleiding te gebruiken. Meer over de front-end pijpleiding leren zie:

* [Reis voor snel maken van site](/help/journey-sites/quick-site/overview.md) - Deze documentatietraject biedt u een overzicht van het proces van het snel implementeren van een site met behulp van de front-end pijplijn en het hulpprogramma Snel site maken.
* [CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - In dit document wordt de front-end pijplijn beschreven in de context van de full-stack en web-tier pijpleidingen.
