---
title: Sjablonen voor het maken van pagina's die kunnen worden bewerkt met de universele editor
description: Leer hoe u sjablonen maakt die u kunt gebruiken om pagina's te maken die u kunt bewerken met de universele editor, zodat u tijd bespaart en zorgt voor consistente branding.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: f0d60086-e92e-4492-ad50-bef84fed2a82
source-git-commit: bcf0940d3365ecde6788772d28d32f22f367816d
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Sjablonen voor het maken van pagina&#39;s die kunnen worden bewerkt met de universele editor {#page-templates}

Leer hoe u sjablonen maakt die u kunt gebruiken om pagina&#39;s te maken die u kunt bewerken met de universele editor, zodat u tijd bespaart en zorgt voor consistente branding.

>[!NOTE]
>
>[ de Malplaatjes zijn ook beschikbaar voor het creëren van pagina&#39;s die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md) editable zijn.

## Wat zijn paginasjablonen? {#what-are}

Op basis van de richtlijnen voor branding en marketing worden vaak bepaalde lay-outs voor uw inhoudspagina&#39;s voorgeschreven. Het is ook vaak een praktische realiteit dat veel van uw pagina&#39;s dezelfde structuur en indeling zullen hebben. Om de tijd van de auteurs van de inhoud te besparen, kunnen pagina&#39;s van malplaatjes worden gecreeerd.

Paginasjablonen fungeren als hoofdkopieën van uw paginalay-outs. Wanneer u een pagina maakt op basis van een sjabloon, wordt de eerste inhoud van de sjabloon naar de nieuwe pagina gekopieerd. Op deze manier kunt u de basislay-out en inhoud van de pagina voor de auteur van de inhoud vooraf definiëren en tijd besparen.

## Paginasjablonen inschakelen {#enabling-templates}

Als u sjablonen wilt gebruiken om pagina&#39;s te maken die u kunt bewerken met de universele editor, moet u de optie inschakelen.

Schakel eerst bewerkbare sjablonen in voor de configuratie van uw site.

1. Gebruik de **console van Plaatsen** en [ selecteer de wortel van uw plaats ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Zodra de plaatswortel wordt geselecteerd, tik of klik het [**pictogram van Eigenschappen** ](/help/sites-cloud/authoring/sites-console/page-properties.md) in de toolbar.
1. Op het **Geavanceerde** lusje van de eigenschappendialoog neemt nota van de waarde op het **gebied van de Configuratie van de Wolk**.
1. Van de belangrijkste navigatie, kies **Hulpmiddelen** -> **Algemeen** -> **Browser van de Configuratie**.
1. In **[Browser van de Configuratie](/help/implementing/developing/introduction/configurations.md)**, selecteer de configuratie u in de vorige stap opnam en tikt of **Eigenschappen** in de toolbar klikt.
1. In het **venster van de Eigenschappen van de Configuratie**, controleer de optie **Bewerkbare Malplaatjes**.
1. Tik of klik **sparen &amp; sluit**.

Nadat de configuratie is ingeschakeld, moet u sjablonen voor uw site toestaan.

1. Gebruik de **console van Plaatsen** en [ selecteer de wortel van uw plaats ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources).
1. Zodra de plaatswortel wordt geselecteerd, tik of klik het [**pictogram van Eigenschappen** ](/help/sites-cloud/authoring/sites-console/page-properties.md) in de toolbar.
1. Op het **Geavanceerde** lusje van de eigenschappendialoog onder de **sectie van de Montages van het Malplaatje**, tik of klik **toevoegen** knoop.
1. In het nieuwe, lege gebied dat onder **Toegelaten Malplaatjes** verschijnt, voeg de weg `/conf/<site>/settings/wcm/templates/.*` toe.
1. Tik of klik **sparen &amp; sluit**.

U kunt nu sjablonen gebruiken om pagina&#39;s voor uw site te maken. Deze taak mag slechts eenmaal worden uitgevoerd op elke site/configuratie waar u sjablonen wilt gebruiken wanneer u pagina&#39;s maakt die u kunt bewerken met de universele editor.

## Een nieuwe sjabloon maken {#create-new}

U kunt of [ een nieuwe pagina ](/help/sites-cloud/authoring/sites-console/creating-pages.md) tot stand brengen om als malplaatje te dienen of een bestaande pagina als basis van een malplaatje te gebruiken.

1. Gebruik de **console van Plaatsen** aan [ navigeer aan de nieuwe of bestaande pagina ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) die u wenst om als malplaatje te gebruiken en het te ontsteken of te klikken om het te selecteren.

1. Zodra de pagina wordt geselecteerd, tik of klik het [**pictogram van Eigenschappen** ](/help/sites-cloud/authoring/sites-console/page-properties.md) in de toolbar.

1. Op het **Geavanceerde** lusje van de eigenschappendialoog onder de **sectie van de Montages van het Malplaatje**, selecteer de knevel **Pagina van het Gebruik als Malplaatje**.

1. Tik of klik **sparen &amp; sluit**.

Uw nieuwe pagina kan nu als sjabloon worden gebruikt bij het maken van nieuwe pagina&#39;s.

## Een pagina maken op basis van een sjabloon {#creating-from-template}

Het creëren van een pagina van een malplaatje dat met de Universele Redacteur editable is is het zelfde werkschema zoals [ creërend een andere pagina ](/help/sites-cloud/authoring/sites-console/creating-pages.md).

1. Gebruik de **console van Plaatsen** aan [ navigeer aan de plaats ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) waar u wenst om de nieuwe pagina tot stand te brengen.

1. Tik of klik **creeer** -> **Pagina**.

1. Op het **Malplaatje** lusje van **creeer de tovenaar van de Pagina**, kunt u selecteren op welk malplaatje u wenst om uw nieuwe pagina te baseren. Tik of klik het gewenste malplaatje om het te selecteren en dan te tikken of **daarna** te klikken.

Voltooi de wizard op dezelfde manier als voor elke andere pagina en u hebt de nieuwe pagina gemaakt op basis van de geselecteerde sjabloon.

## Pagina&#39;s en sjablonen {#pages-vs-templates}

Met paginasjablonen definieert u alleen de eerste inhoud van pagina&#39;s. Pagina&#39;s kunnen dan volledig worden bewerkt met de universele editor.

* Pagina&#39;s die zijn gemaakt op basis van paginasjablonen zijn onafhankelijke kopieën van de sjabloon.
* Als de sjabloon verandert, veranderen de bestaande pagina&#39;s die op die sjabloon zijn gebaseerd niet.
* De auteur van de inhoud kan de inhoud van de resulterende pagina indien nodig wijzigen en bijwerken zonder beperkingen van de sjabloon.

## Bewerkbare sjablonen {#editable-templates}

De pagina&#39;s die met de [ Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/introduction.md) worden gecreeerd kunnen ook op malplaatjes worden gebaseerd. De malplaatjes die worden gebruikt om pagina&#39;s voor de Universele Redacteur en de Redacteur van de Pagina tot stand te brengen zowel hefboomwerking AEM [ editable malplaatjes ](/help/implementing/developing/components/templates.md).

In sjablonen die worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met de Pagina-editor, worden alle functies van bewerkbare sjablonen gebruikt. Sjablonen die worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met de universele editor, gebruiken alleen de oorspronkelijke inhoudsfunctie.
