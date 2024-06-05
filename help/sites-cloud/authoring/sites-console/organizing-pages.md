---
title: Pagina's ordenen
description: Leer hoe u uw website kunt organiseren met AEM.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 2%

---


# Pagina&#39;s ordenen {#creating-and-organizing-pages}

Leer hoe u uw website kunt organiseren met AEM. Als u begrijpt hoe u uw pagina&#39;s moet ordenen, kunt u [nieuwe pagina&#39;s maken](/help/sites-cloud/authoring/sites-console/creating-pages.md) en [bestaande pagina&#39;s beheren.](/help/sites-cloud/authoring/sites-console/managing-pages.md)

{{edge-delivery-authoring}}

## Uw site organiseren {#organizing-your-site}

Als auteur moet u uw site binnen AEM ordenen. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* U kunt deze gemakkelijk vinden in de ontwerpomgeving
* Bezoekers naar uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt ook [mappen](#creating-a-new-folder) om uw inhoud beter in te delen.

De structuur van een website kan worden beschouwd als een structuur die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titels worden getoond wanneer de paginainhoud wordt bekeken.

In het volgende voorbeeld wordt getoond [WKND-zelfstudie](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) site, waar een artikel over skateparks (`la-skateparks`) is geopend:

`http://<host>:<port>/editor.html/content/wknd/en/sports/la-skateparks.html`

```xml
 /content
 /wknd
  /en
   /music
    /...
   /sports
    /la-skateparks
    /five-gyms-la
    /mountain-bike-routes
   /shopping
    /...
   /art
    /...
   /...
```

Deze structuur kan worden weergegeven vanuit de [**Sites** console,](/help/sites-cloud/authoring/sites-console/introduction.md) waar u door de pagina&#39;s van uw website kunt navigeren en acties op de pagina&#39;s kunt uitvoeren.

## Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:
   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.
* **[Naam](#name)**:
   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel. Zie de volgende sectie [Beperkingen en aanbevolen procedures voor paginanamen](#page-name-restrictions-and-best-practices) voor meer informatie.

### Beperkingen en aanbevolen procedures voor paginanamen {#page-name-restrictions-and-best-practices}

De **titel** en **naam** van de pagina kunnen afzonderlijk worden gemaakt, maar zijn aan elkaar gerelateerd:

* Bij het maken van een pagina worden alleen de **Titel** is vereist. Indien niet **Naam** wordt opgegeven bij het maken van de pagina. AEM genereert een naam uit de eerste 64 tekens van de titel (met inachtneming van de onderstaande validatie). Alleen de eerste 64 tekens worden gebruikt ter ondersteuning van de beste praktijken voor namen van korte pagina&#39;s.
* Als een paginanaam handmatig door de auteur wordt opgegeven, geldt de limiet van 64 tekens niet, maar kunnen andere technische beperkingen op de lengte van de paginanaam wel van toepassing zijn.

>[!TIP]
>
>Wanneer u een paginanaam definieert, is het verstandig de paginanaam zo kort maar expressief en zo gedenkwaardig mogelijk te houden, zodat de lezer deze goed begrijpt. Zie de [W3C-stijlhulplijn](https://www.w3.org/Provider/Style/TITLE.html) voor de `title` voor meer informatie.
>
>Houd er ook rekening mee dat sommige browsers (bijvoorbeeld oudere versies van IE) URL&#39;s tot een bepaalde lengte alleen kunnen accepteren, dus er is ook een technische reden om paginanamen kort te houden.

Wanneer u een pagina maakt, AEM [valideert de paginanaam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en het GCO.

De minimaal toegestane tekens zijn:

* `a` doorheen `z`
* `A` doorheen `Z`
* `0` doorheen `9`
* `_` (onderstrepingsteken)
* `-` (afbreekstreepje/minteken)

Alle tekens die zijn toegestaan, zijn beschikbaar in [naamconventies](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Paginanamen mogen maximaal 150 tekens bevatten.

### Titel {#title}

Als u alleen een pagina opgeeft **Titel** wanneer u een pagina maakt, wordt AEM de pagina afgeleid **Naam** van deze tekenreeks en [De naam valideren volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR.

A **Titel** veld met ongeldige tekens wordt geaccepteerd, maar voor de afgeleide naam worden de ongeldige tekens vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | `schoen.html` |
| SC%&amp;&#42;ç+ | `sc---c-.html` |

### Naam {#name}

Wanneer u een pagina opgeeft **Naam** bij het maken van een pagina, AEM [valideert de naam volgens de conventies](/help/implementing/developing/introduction/naming-conventions.md) opgelegd door AEM en JCR. U kunt geen ongeldige tekens verzenden in het dialoogvenster **Naam** veld. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd met een uitleg.

![Voorbeeld van het invoeren van een ongeldige paginanaam](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Gebruik geen code van twee letters, zoals gedefinieerd door ISO-639-1, als paginanaam, tenzij dit een hoofdtaalcode is.
>
>Zie [Inhoud voorbereiden voor vertaling](/help/sites-cloud/administering/translation/preparation.md) voor meer informatie .

## Sjablonen {#templates}

In AEM [template](/help/sites-cloud/authoring/sites-console/templates.md) is een gespecialiseerd type pagina dat wordt gebruikt als basis voor elke nieuwe pagina die wordt gemaakt.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. Sjablonen bestaan uit [componenten](#components).

AEM wordt geleverd met verschillende sjablonen die buiten de box zijn geplaatst. Welke sjablonen beschikbaar zijn, is afhankelijk van de afzonderlijke website. De belangrijkste velden zijn:

* **Titel** - De titel die op de resulterende webpagina wordt weergegeven
* **Naam** - Wordt gebruikt als naam voor de pagina
* **Sjabloon** - Een lijst met sjablonen die u kunt gebruiken bij het genereren van de nieuwe pagina

## Onderdelen {#components}

[Componenten](/help/implementing/developing/components/overview.md) Dit zijn de elementen die door AEM worden verstrekt zodat u specifieke types van inhoud kunt toevoegen. AEM wordt geleverd met een reeks componenten die buiten het vak worden weergegeven, [de kerncomponenten,](/help/implementing/developing/components/overview.md#core-components) die uitgebreide functionaliteit bieden. Enkele voorbeelden van de componenten zijn:

* Tekst
* Afbeelding
* Titel
* Carousel
* En nog veel meer

Als u eenmaal een pagina hebt gemaakt en geopend, kunt u [inhoud toevoegen met de componenten](/help/sites-cloud/authoring/page-editor/edit-content.md#inserting-a-component), die beschikbaar zijn op [componentbrowser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

>[!TIP]
>
>De [Componentenconsole](/help/sites-cloud/authoring/components-console.md) geef een overzicht van de componenten op uw instantie.
