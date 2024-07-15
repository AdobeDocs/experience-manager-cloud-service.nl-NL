---
title: Het Sitepaneel gebruiken om uw sitethema te beheren
description: Leer de krachtige eigenschappen van het paneel van de Plaats om u te helpen uw plaatsthema gemakkelijk aanpassen en beheren.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
solution: Experience Manager Sites
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---


# Uw sitethema beheren met het deelvenster Site {#site-panel}

Leer de krachtige eigenschappen van het paneel van de Plaats om u te helpen uw plaatsthema gemakkelijk aanpassen en beheren.

## Overzicht {#overview}

In het paneel Site kunt u het thema en de sjabloonbronnen van uw site beheren. [ als andere panelen ](/help/sites-cloud/authoring/sites-console/console-side-panel.md) zoals de Inhoudsboom, Verwijzingen, of panelen van de Chronologie, wordt het paneel van de Plaats getoond als uiterst linkse paneel in de plaatsenconsole, tonend informatie over het geselecteerde punt. In tegenstelling tot andere deelvensters is het deelvenster Site alleen van toepassing op de hoofdmap van de site.

Het paneel Site wordt gebruikt voor het beheer van thema&#39;s en sjabloongerelateerde informatie voor uw site, waaronder:

* [Themabronnen downloaden](#downloading-theme-sources)
* [Sjabloonbronnen downloaden, zoals draadframes](#downloading-template-resources)
* [Themaversies weergeven en wijzigen](#theme-vrsions)
* [Toelaten van de front-end pijpleiding](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Herzie de [ Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) om zich met het Snelle hulpmiddel van de Aanmaak van de Plaats en de front-end pijpleiding vertrouwd te maken om uw plaatsthema gemakkelijk aan te passen.

## Themabronnen downloaden {#downloading-theme-sources}

Wanneer u een plaats in AEM creeert die op het malplaatje van de a [ plaats wordt gebaseerd, ](site-templates.md) kunt u uw [ plaatsthema ](site-themes.md) downloaden gebruikend het paneel van de Plaats.

Selecteer, terwijl het deelvenster Site wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven.

![ Download themabronnen ](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Selecteer **Bronnen van het Thema van de Download** om een lokaal exemplaar van het plaatsthema als `.zip` dossier voor aanpassingsdoeleinden te downloaden.

## Sjabloonbronnen downloaden {#downloading-template-resources}

{de malplaatjes van de Plaats ](site-templates.md) kunnen informatie naast uw structuur van de plaatsinhoud en [ plaatsthema bevatten.[](site-themes.md) Sitesjablonen kunnen bijvoorbeeld draadframe-ontwerpen of andere sitegerelateerde bestanden bevatten.

Als uw site is gebaseerd op een sitesjabloon en het Sitepaneel in de siteconsole wordt weergegeven, selecteert u de hoofdmap van uw site om themagegevens over de site weer te geven, inclusief extra sitemiddelen.

![ Download themabronnen ](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Selecteer de knoop of de knopen onder de rubriek **Download extra malplaatjemiddelen** om een lokaal exemplaar van de beschikbare dossiers te downloaden.

## Themaversies weergeven en wijzigen {#them-versions}

Als uw site is gebaseerd op een sitesjabloon, is het mogelijk dat het thema al is aangepast door uw front-end ontwikkelaar. Met behulp van het deelvenster Site kunt u bekijken welke versie van het sitethema momenteel is geïmplementeerd en overschakelen op vorige versies.

Selecteer, terwijl het deelvenster Site wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven.

![ versies van de Plaats in het paneel ](/help/sites-cloud/administering/assets/theme-versions.png)

De huidige versie van het thema wordt weergegeven met de knoeiboel voor vastleggen samen met de tijdstempel van de laatste update.

Selecteer **Uitgezochte Versie** om vorige versies van het thema te bekijken.

![ Uitgezochte themaversie ](/help/sites-cloud/administering/assets/select-theme-versions.png)

Selecteer de versie u wilt veranderen en dan selecteren **** toepassen om de verandering aan te brengen.

Als AEM ontdekt dat een nieuwere versie van het thema via de front-end pijpleiding is opgesteld maar niet op uw plaats is toegepast, zal een berichtpictogram tonen.

![ Nieuwere versie van themaindicator ](/help/sites-cloud/administering/assets/new-theme-version.png)

U kunt de **Uitgezochte knoop van de Versie** gebruiken om aan de nieuwe themaversie bij te werken.

## Het toelaten van de Voorste Pijpleiding {#enabling-front-end-pipeline}

Als uw plaats niet gebruikend een plaatsmalplaatje werd gecreeerd, is het niet mogelijk om de front-end pijpleiding te gebruiken om zijn thema aan te passen en op te stellen.

U kunt echter de front-end pijplijn voor uw site inschakelen via het deelvenster Site.

Met het paneel dat van de Plaats in de plaatsenconsole toont, selecteer de wortel van uw plaats om themainformatie over de plaats te openbaren en dan **te selecteren laat Voorste Pijpleiding van het Eind** toe.

![ toelatend front-end pijpleiding ](/help/sites-cloud/administering/assets/enable-fep.png)

Voor meer informatie, zie het document [ Toelatend de Voorste-Eind Pijpleiding.](enable-front-end-pipeline.md)
