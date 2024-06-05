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

In het paneel Site kunt u het thema en de sjabloonbronnen van uw site beheren. [Net als andere deelvensters](/help/sites-cloud/authoring/sites-console/console-side-panel.md) zoals de deelvensters Inhoudsstructuur, Verwijzingen of Tijdlijn wordt het deelvenster Site weergegeven als het meest linkse deelvenster in de siteconsole, waarin informatie over het geselecteerde item wordt weergegeven. In tegenstelling tot andere deelvensters is het deelvenster Site alleen van toepassing op de hoofdmap van de site.

Het paneel Site wordt gebruikt voor het beheer van thema&#39;s en sjabloongerelateerde informatie voor uw site, waaronder:

* [Themabronnen downloaden](#downloading-theme-sources)
* [Sjabloonbronnen downloaden, zoals draadframes](#downloading-template-resources)
* [Themaversies weergeven en wijzigen](#theme-vrsions)
* [Toelaten van de front-end pijpleiding](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Controleer de [Reis voor snel maken van site](/help/journey-sites/quick-site/overview.md) om uzelf vertrouwd te maken met het gereedschap Snel site maken en de front-end pijplijn om het thema van uw site eenvoudig aan te passen.

## Themabronnen downloaden {#downloading-theme-sources}

Wanneer u een site maakt in AEM op basis van een [sitesjabloon,](site-templates.md) u kunt uw [site-thema](site-themes.md) via het deelvenster Site.

Selecteer, terwijl het deelvenster Site wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven.

![Themabronnen downloaden](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Selecteren **Themabronnen downloaden** om een lokale kopie van het sitethema te downloaden als `.zip` bestand voor aanpassingsdoeleinden.

## Sjabloonbronnen downloaden {#downloading-template-resources}

[Sitesjablonen](site-templates.md) kan informatie bevatten naast de structuur van uw site-inhoud en [site-thema.](site-themes.md) Sitesjablonen kunnen bijvoorbeeld draadframemodellen of andere sitegerelateerde bestanden bevatten.

Als uw site is gebaseerd op een sitesjabloon en het Sitepaneel in de siteconsole wordt weergegeven, selecteert u de hoofdmap van uw site om themagegevens over de site weer te geven, inclusief extra sitemiddelen.

![Themabronnen downloaden](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Selecteer de knop of knoppen onder de kop **Aanvullende sjabloonbronnen downloaden** om een lokale kopie van de beschikbare bestanden te downloaden.

## Themaversies weergeven en wijzigen {#them-versions}

Als uw site is gebaseerd op een sitesjabloon, is het mogelijk dat het thema al is aangepast door uw front-end ontwikkelaar. Met behulp van het deelvenster Site kunt u bekijken welke versie van het sitethema momenteel is geïmplementeerd en overschakelen op vorige versies.

Selecteer, terwijl het deelvenster Site wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven.

![Siteversies in het deelvenster](/help/sites-cloud/administering/assets/theme-versions.png)

De huidige versie van het thema wordt weergegeven met de knoeiboel voor vastleggen samen met de tijdstempel van de laatste update.

Selecteren **Versie selecteren** om vorige versies van het thema weer te geven.

![Themaversie selecteren](/help/sites-cloud/administering/assets/select-theme-versions.png)

Selecteer de versie die u wilt wijzigen en selecteer **Toepassen** om de wijziging aan te brengen.

Als AEM ontdekt dat een nieuwere versie van het thema via de front-end pijpleiding is opgesteld maar niet op uw plaats is toegepast, zal een berichtpictogram tonen.

![Nieuwere versie van themaindicator](/help/sites-cloud/administering/assets/new-theme-version.png)

U kunt de **Versie selecteren** om bij te werken naar de nieuwe themaversie.

## Het toelaten van de Voorste Pijpleiding {#enabling-front-end-pipeline}

Als uw plaats niet gebruikend een plaatsmalplaatje werd gecreeerd, is het niet mogelijk om de front-end pijpleiding te gebruiken om zijn thema aan te passen en op te stellen.

U kunt echter de front-end pijplijn voor uw site inschakelen via het deelvenster Site.

Selecteer, terwijl het deelvenster Site wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven en selecteer vervolgens **Vooruiteinde pijplijn inschakelen**.

![Het toelaten van front-end pijpleiding](/help/sites-cloud/administering/assets/enable-fep.png)

Zie het document voor meer informatie [Het toelaten van de voorste-Eind Pijpleiding.](enable-front-end-pipeline.md)
