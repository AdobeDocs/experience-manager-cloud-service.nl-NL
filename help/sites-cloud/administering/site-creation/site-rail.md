---
title: Het Siterail gebruiken om uw Sitethema te beheren
description: Leer de krachtige functies van de Site-rail om u te helpen uw site eenvoudig aan te passen en te beheren.
feature: Administering
role: Admin
exl-id: 45785e5a-4fa2-4cf2-a300-f1865f6f5807
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Het Siterail gebruiken om uw Sitethema te beheren {#site-rail}

Leer de krachtige functies van de Site-rail om u te helpen uw site eenvoudig aan te passen en te beheren.

## Overzicht {#overview}

Met de Site-rail kunt u het thema en de sjabloonbronnen van uw site beheren. [Als andere rails](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) zoals de rails Inhoudsstructuur, Verwijzingen of Tijdlijn wordt de sitelijn weergegeven als het meest linkse deelvenster in de siteconsole, waarin informatie over het geselecteerde item wordt weergegeven. In tegenstelling tot andere spoorstaven geldt de Sitrails alleen voor de wortels van de Sitepagina.

De site-rail wordt gebruikt voor het beheer van thema- en sjabloongerelateerde informatie voor uw site, waaronder:

* [Themabronnen downloaden](#downloading-theme-sources)
* [Sjabloonbronnen downloaden, zoals draadframes](#downloading-template-resources)
* [Themaversies weergeven en wijzigen](#theme-vrsions)
* [Toelatend de front-end pijpleiding](#enabling-the-front-end-pipeline)

>[!TIP]
>
>Controleer de [Reis voor snel maken van site](/help/journey-sites/quick-site/overview.md) om uzelf vertrouwd te maken met het gereedschap Snel site maken en de front-end pijplijn om het thema van uw site eenvoudig aan te passen.

##  Themabronnen downloaden {#downloading-theme-sources}

Wanneer u een site maakt in AEM op basis van een [sitesjabloon,](site-templates.md) u kunt uw [site-thema](site-themes.md) het gebruik van de Sitelijn.

Terwijl de Site-rail in de siteconsole wordt weergegeven, selecteert u de hoofdmap van uw site om themagegevens over de site weer te geven.

![Themabronnen downloaden](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tik of klik op **Themabronnen downloaden** om een lokale kopie van het sitethema te downloaden als `.zip` bestand voor aanpassingsdoeleinden.

##  Sjabloonbronnen downloaden {#downloading-template-resources}

[Sitesjablonen](site-templates.md) kan informatie bevatten naast de structuur van uw site-inhoud en [site-thema.](site-themes.md) Sitesjablonen kunnen bijvoorbeeld draadframemodellen of andere sitegerelateerde bestanden bevatten.

Als uw site is gebaseerd op een sitesjabloon en de Site-rail in de siteconsole wordt weergegeven, selecteert u de hoofdmap van uw site om themagegevens over de site weer te geven, inclusief aanvullende sitebronnen.

![Themabronnen downloaden](/help/sites-cloud/administering/assets/download-theme-wireframe.png)

Tik of klik op de knop of knoppen onder de kop **Aanvullende sjabloonbronnen downloaden** om een lokale kopie van de beschikbare bestanden te downloaden.

## Themaversies weergeven en wijzigen {#them-versions}

Als uw site is gebaseerd op een sitesjabloon, is het mogelijk dat het thema al is aangepast door uw front-end ontwikkelaar. Met behulp van de Site-rail kunt u zien welke versie van het site-thema momenteel is geïmplementeerd en overschakelen op vorige versies.

Terwijl de Site-rail in de siteconsole wordt weergegeven, selecteert u de hoofdmap van uw site om themagegevens over de site weer te geven.

![De versies van de plaats in spoorstaaf](/help/sites-cloud/administering/assets/theme-versions.png)

De huidige versie van het thema wordt weergegeven met de knoeiboel voor vastleggen samen met de tijdstempel van de laatste update.

Tik of klik op **Versie selecteren** om vorige versies van het thema weer te geven.

![Themaversie selecteren](/help/sites-cloud/administering/assets/select-theme-versions.png)

Tik of klik op de versie die u wilt wijzigen en tik op **Toepassen** om de wijziging aan te brengen.

Als AEM ontdekt dat een nieuwere versie van het thema via de front-end pijpleiding is opgesteld maar niet op uw plaats is toegepast, zal een berichtpictogram tonen.

![Nieuwere versie van themaindicator](/help/sites-cloud/administering/assets/new-theme-version.png)

U kunt de **Versie selecteren** om bij te werken naar de nieuwe themaversie.

## Het toelaten van de Voor-Eind Pijpleiding {#enabling-front-end-pipeline}

Als uw plaats niet gebruikend een plaatsmalplaatje werd gecreeerd, is het niet mogelijk om de front-end pijpleiding te gebruiken om zijn thema aan te passen en op te stellen.

Nochtans kunt u de front-end pijpleiding voor uw plaats toelaten gebruikend de spoorstaaf van de Plaats.

Selecteer, terwijl Site-rail wordt weergegeven in de siteconsole, de hoofdmap van uw site om themagegevens over de site weer te geven en tik of klik op **Vooruiteinde pijplijn inschakelen**.

![Het toelaten van front-end pijpleiding](/help/sites-cloud/administering/assets/enable-fep.png)

Zie het document voor meer informatie [Het toelaten van de voorste-Eind Pijpleiding.](enable-front-end-pipeline.md)
