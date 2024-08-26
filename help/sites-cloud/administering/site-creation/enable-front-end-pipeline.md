---
title: Het toelaten van de Voorste Pijpleiding
description: Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema's te gebruiken om uw plaats sneller aan te passen.
feature: Administering
role: Admin
exl-id: 55d54d72-f87b-47c9-955f-67ec5244dd6e
solution: Experience Manager Sites
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---

# Het toelaten van de Voorste Pijpleiding {#enable-front-end-pipeline}

Leer hoe u de front-end pijpleiding voor bestaande plaatsen kunt toelaten om plaatsthema&#39;s te gebruiken om uw plaats sneller aan te passen.

## Overzicht {#overview}

De front-end pijpleiding is een mechanisme dat enkel de front-end code van uw websites kan snel opstellen die op [ wordt gebaseerd plaatsenthema&#39;s ](site-themes.md) en [ plaatssjablonen.](site-templates.md)

Deze pijpleiding behandelt slechts front-end code, die het plaatsingsproces sneller dan volledig-stapel plaatsingen maakt. Met deze functie kunnen ontwikkelaars aan de voorzijde uw site eenvoudig aanpassen zonder dat ze kennis van AEM nodig hebben.

De plaatsen die op plaatsmalplaatjes worden gebaseerd kunnen de front-end pijpleiding door gebrek gebruiken. Dit document beschrijft hoe u uw bestaande plaatsen kunt aanpassen om uit de front-end pijpleiding voordeel te halen.

>[!TIP]
>
>Als u niet vertrouwd met de front-end pijpleiding bent en hoe te om plaatsen op te stellen snel gebruikend het en plaatssjablonen, zie ](/help/journey-sites/quick-site/overview.md) de Reis van de Aanmaak van de Snelle Plaats [ voor een inleiding.

AEM kunt uw site configureren om thema&#39;s te laden die zijn geïmplementeerd met de Front End Pipeline, zelfs als uw site niet is gemaakt met sitesjablonen en -thema&#39;s, door deze in lagen boven op bestaande clientbibliotheken te plaatsen.

## Technische details {#technical-details}

Wanneer u de front-end pijplijn voor een plaats activeert, AEM brengt de volgende veranderingen in uw plaatsstructuur aan.

* Alle pagina&#39;s van de site bevatten één extra CSS- en JS-bestand, dat kan worden gewijzigd door updates te implementeren via een speciale Cloud Manager front-end pipe.
* De toegevoegde CSS- en JS-bestanden zijn aanvankelijk leeg. U kunt echter een map met &quot;themabronnen&quot; downloaden om de mappenstructuur in te stellen die nodig is om CSS- en JS-code-updates via de pijplijn te implementeren.
* Alleen ontwikkelaars kunnen de wijziging ongedaan maken door de knooppunten `SiteConfig` en `HtmlPageItemsConfig` die met deze bewerking onder `/conf/<site-name>/sling:configs` worden gemaakt, te verwijderen.

>[!NOTE]
>
>Met deze actie worden de bestaande clientbibliotheken van de site niet automatisch omgezet voor gebruik van de eindpijplijn voor lettertypen. Het verplaatsen van deze bronnen van de omslag van de cliëntbibliotheek naar de front-end pijpleidingsomslag is een taak die handwerk door een front-end ontwikkelaar vereist.

## Vereisten {#requirements}

AEM kan uw bestaande plaats automatisch aanpassen om de front-end pijpleiding te gebruiken. Om dit werkschema te kunnen doen, moet uw plaats [ v2 of nieuwer van de Component van de Pagina van de Componenten van de Kern gebruiken.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/page)

## Het toelaten van Voorste Pijl-Eind {#enabling}

{{add-cm-allowlist-frontend-pipeline}}

Het toelaten van uw plaats wordt gedaan van de console van Plaatsen gebruikend het [ spoor van de Plaats.](site-rail.md)

1. Logboek in AEM en navigeer aan uw plaats via **Globale Navigatie** > **Plaatsen**.
1. Selecteer uw site in de console. Selecteer de hoofdmap van de site en geen onderliggende pagina&#39;s.
1. Met uw geselecteerde plaats, open de [ spoorselecteur ](/help/sites-cloud/authoring/basic-handling.md#rail-selector) bij de linkerzijde en kies **Plaats**.
1. In het **spoor van de Plaats**, klik de knoop **laat Voorste Pijpleiding van het Eind** toe.

   ![ laat front-end pijpleiding ](/help/sites-cloud/administering/assets/enable-front-end-pipeline.png) toe

1. AEM vraagt u de aangebrachte wijzigingen te bevestigen met een overzicht. Bevestig en uw site is aangepast.

Nu, is uw plaats klaar om de front-end pijpleiding te gebruiken. Meer over de front-end pijpleiding en het beheren van uw plaatsthema leren zie:

* [Het Siterail gebruiken om uw Sitethema te beheren](site-rail.md)
* [ Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) - Deze documentatierit geeft u en overzicht van begin tot eind van het proces om snel een plaats op te stellen gebruikend de front-end pijpleiding en het Snelle hulpmiddel van de Aanmaak van de Plaats.
* [ CI/CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) - Dit document beschrijft de front-end pijpleiding in de context van de volledig-stapel en Webrijpijpleidingen.
