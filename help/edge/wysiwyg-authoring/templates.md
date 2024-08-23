---
title: Paginasjablonen gebruiken met de universele editor
description: Leer hoe u paginasjablonen maakt en gebruikt met de Universal Editor.
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 773ce75975f4dcc2c5310422bcc377b487ebec25
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---


# Paginasjablonen gebruiken met de universele editor {#page-templates}

Leer hoe u paginasjablonen maakt en gebruikt met de Universal Editor.

>[!NOTE]
>
>Deze functie is beschikbaar in een komende release van AEM as a Cloud Service.

## Wat zijn paginasjablonen? {#what-are}

Op basis van de richtlijnen voor branding en marketing worden vaak bepaalde lay-outs voor uw inhoudspagina&#39;s voorgeschreven. Het is ook vaak een praktische realiteit dat veel van uw pagina&#39;s dezelfde structuur en indeling zullen hebben. Om de tijd van de auteurs van de inhoud te besparen, kunnen pagina&#39;s van malplaatjes worden gecreeerd.

Paginasjablonen fungeren als hoofdkopieën van uw paginalay-outs. Wanneer u een pagina maakt op basis van een sjabloon, wordt de inhoud van de sjabloon naar de nieuwe pagina gekopieerd. Op deze manier kunt u de lay-out en de initiële inhoud van de pagina voor de auteur van de inhoud vooraf definiëren en tijd besparen.

## Een paginasjabloon maken {#creating}

U kunt een paginasjabloon maken door een nieuwe pagina te maken of door een bestaande pagina als sjabloon te gebruiken. In beide gevallen, gebruikt u de **Console van 1} Plaatsen[**.](/help/sites-cloud/authoring/sites-console/introduction.md)

### Een nieuwe sjabloon maken {#create-new}

1. Gebruik de **console van Plaatsen** om aan de plaats te navigeren waar u wenst om de nieuwe pagina tot stand te brengen die als uw malplaatje zal dienen en [ creeer de pagina zoals u een andere.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Zodra de pagina wordt gecreeerd en u aan de console terugkeert, selecteer de pagina en dan het [**pictogram van Eigenschappen** ](/help/sites-cloud/authoring/sites-console/page-properties.md) in de toolbar tikken of klikken.

1. Op het **Geavanceerde** lusje van de eigenschappendialoog onder de **sectie van de Montages van het Malplaatje**, selecteer het knevel **Gebruik als Malplaatje**.

1. Op het **gebied van de Naam van het Malplaatje**, verstrek een beschrijvende naam.

   * Dit is de naam die het creëren van nieuwe inhoudspagina&#39;s zal tonen en u selecteert een malplaatje waarop om de nieuwe pagina te baseren.

1. Tik of klik **sparen &amp; sluit**.

Uw nieuwe pagina kan nu als sjabloon worden gebruikt bij het maken van nieuwe pagina&#39;s.

### Een bestaande pagina als sjabloon gebruiken {#existing-page}

1. Gebruik de **console van Plaatsen** aan [ navigeer aan de plaats van de pagina ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) u als malplaatje zou willen gebruiken.

1. Selecteer de pagina en tik of klik dan het **pictogram van Eigenschappen[** ](/help/sites-cloud/authoring/sites-console/page-properties.md) in de toolbar.

1. Op het **Geavanceerde** lusje van de eigenschappendialoog onder de **sectie van de Montages van het Malplaatje**, selecteer het knevel **Gebruik als Malplaatje**.

1. Op het **gebied van de Naam van het Malplaatje**, verstrek een beschrijvende naam.

   * Dit is de naam die het creëren van nieuwe inhoudspagina&#39;s zal tonen en u selecteert een malplaatje waarop om de nieuwe pagina te baseren.

1. Tik of klik **sparen &amp; sluit**.

De geselecteerde pagina kan nu als een sjabloon worden gebruikt bij het maken van nieuwe pagina&#39;s.

## Een pagina maken op basis van een sjabloon {#creating-from-template}

Het creëren van een pagina van een malplaatje voor gebruik met de Universele Redacteur is het zelfde werkschema zoals toen [ creërend de pagina zoals u een andere.](/help/sites-cloud/authoring/sites-console/creating-pages.md)

1. Gebruik de **console van Plaatsen** aan [ navigeer aan de plaats ](/help/sites-cloud/authoring/sites-console/introduction.md#selecting-resources) waar u wenst om de nieuwe pagina tot stand te brengen.

1. Tik of klik **creeer** -> **Pagina**.

1. Op het **Malplaatje** lusje van **creeer de tovenaar van de Pagina**, kunt u selecteren op welk malplaatje u wenst om uw nieuwe pagina te baseren. Tik of klik het gewenste malplaatje om het te selecteren en dan te tikken of **daarna** te klikken.

Voltooi de wizard op dezelfde manier als voor elke andere pagina en u hebt de nieuwe pagina gemaakt op basis van de geselecteerde sjabloon.

## Universele editor en de Pagina-editor {#page-vs-universal}

De malplaatjes van de pagina voor de Universele Redacteur lossen het zelfde probleem op zoals [ paginasjablonen voor de Redacteur van de AEM:](/help/sites-cloud/authoring/page-editor/templates.md) om inhoud te kunnen hergebruiken om pagina&#39;s snel tot stand te brengen die op een reeks vooraf bepaalde lay-outs worden gebaseerd. Ze lossen het probleem echter op zeer verschillende manieren op. Houd rekening met deze verschillen als u een gebruiker van de Pagina-editor bent.

* Pagina&#39;s die zijn gemaakt op basis van paginasjablonen voor de Universal Editor zijn onafhankelijke kopieën van de sjabloon.
* Als de sjabloon wordt gewijzigd, veranderen de resulterende pagina&#39;s dus niet.
* De auteur van de inhoud kan de inhoud van de resulterende pagina indien nodig wijzigen en bijwerken zonder beperkingen van de sjabloon.
