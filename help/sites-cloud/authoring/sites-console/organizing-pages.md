---
title: Pagina's ordenen
description: Leer hoe u uw website kunt organiseren met AEM.
exl-id: c57096ca-34fe-4b19-98e0-8f3cd43cf24e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 9a700e9eb3116252f42bb08db9dadc0e8a6adbf7
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 2%

---


# Pagina&#39;s ordenen {#creating-and-organizing-pages}

Leer hoe u uw website kunt organiseren met AEM. Zodra u begrijpt hoe u uw pagina&#39;s moet organiseren, kunt u [&#x200B; nieuwe pagina&#39;s &#x200B;](/help/sites-cloud/authoring/sites-console/creating-pages.md) creëren en [&#x200B; het bestaan pagina&#39;s &#x200B;](/help/sites-cloud/authoring/sites-console/managing-pages.md) beheren.

## Uw site organiseren {#organizing-your-site}

Als auteur moet u uw site ordenen in AEM. Dit betekent dat u inhoudspagina&#39;s maakt en een naam geeft, zodat:

* U kunt deze gemakkelijk vinden in de ontwerpomgeving
* Bezoekers naar uw site kunnen deze gemakkelijk in de publicatieomgeving bekijken

U kunt [&#x200B; omslagen &#x200B;](#creating-a-new-folder) ook gebruiken helpen uw inhoud organiseren.

De structuur van een website kan worden beschouwd als een structuur die uw inhoudspagina&#39;s bevat. De namen van deze inhoudspagina&#39;s worden gebruikt om URLs te vormen, terwijl de titels worden getoond wanneer de paginainhoud wordt bekeken.

Het volgende toont een voorbeeld van de [&#x200B; plaats van het Leerprogramma WKND &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=nl-NL), waar een artikel over skateparks (`la-skateparks`) wordt betreden:

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

Deze structuur kan van de **console van de Plaatsen[** worden bekeken &#x200B;](/help/sites-cloud/authoring/sites-console/introduction.md), waar u door de pagina&#39;s van uw website kunt navigeren en acties op de pagina&#39;s uitvoeren.

## Naamgevingsconventies voor pagina {#page-naming-conventions}

Bij het maken van een pagina zijn er twee sleutelvelden:

* **[Titel](#title)**:
   * Dit wordt aan de gebruiker getoond in de console en bij het uitgeven bij de bovenkant van de paginainhoud getoond.
   * Dit veld is verplicht.
* **[Naam](#name)**:
   * Hiermee wordt de URI gegenereerd.
   * Gebruikersinvoer voor dit veld is optioneel. Indien niet opgegeven, wordt de naam afgeleid van de titel. Zie de volgende sectie [&#x200B; Beperkingen van de Naam van de Pagina en Beste praktijken &#x200B;](#page-name-restrictions-and-best-practices) voor details.

### Beperkingen en aanbevolen procedures voor paginanamen {#page-name-restrictions-and-best-practices}

De **titel** en **naam** van de pagina kunnen afzonderlijk worden gemaakt, maar zijn aan elkaar gerelateerd:

* Wanneer het creëren van een pagina, slechts wordt het **gebied van de Titel** vereist. Als geen **Naam** bij paginaverwezenlijking wordt verstrekt, zal AEM een naam van de eerste 64 karakters van de titel (het observeren van de hieronder vermelde bevestiging) produceren. Alleen de eerste 64 tekens worden gebruikt ter ondersteuning van de beste praktijken voor namen van korte pagina&#39;s.
* Als een paginanaam handmatig door de auteur wordt opgegeven, geldt de limiet van 64 tekens niet, maar kunnen andere technische beperkingen op de lengte van de paginanaam wel van toepassing zijn.

>[!TIP]
>
>Wanneer u een paginanaam definieert, is het verstandig de paginanaam zo kort maar expressief en zo gedenkwaardig mogelijk te houden, zodat de lezer deze goed begrijpt. Zie de [&#x200B; W3C stijlgids &#x200B;](https://www.w3.org/Provider/Style/TITLE.html) voor het `title` element voor meer informatie.
>
>Houd er ook rekening mee dat sommige browsers (bijvoorbeeld oudere versies van IE) URL&#39;s tot een bepaalde lengte alleen kunnen accepteren, dus er is ook een technische reden om paginanamen kort te houden.

Wanneer het creëren van een pagina, bevestigt AEM [&#x200B; de paginanaam volgens de overeenkomsten &#x200B;](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.

De minimaal toegestane tekens zijn:

* `a` tot en met `z`
* `A` tot en met `Z`
* `0` tot en met `9`
* `_` (underscore)
* `-` (afbreekstreepje/minteken)

De volledige details van alle toegestane karakters kunnen in [&#x200B; worden gevonden de noemende overeenkomsten &#x200B;](/help/implementing/developing/introduction/naming-conventions.md).

>[!NOTE]
>
>Paginanamen mogen maximaal 150 tekens bevatten.

### Titel {#title}

Als u slechts een pagina **Titel** wanneer het creëren van een pagina verstrekt, leidt AEM de pagina **Naam** van dit koord af en [&#x200B; bevestigt de naam volgens de overeenkomsten &#x200B;](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd.

Het gebied van de Titel van A **&#x200B;**&#x200B;dat ongeldige karakters bevat wordt goedgekeurd, maar de afgeleide naam heeft de ongeldige karakters vervangen. Bijvoorbeeld:

| Titel | Afgeleide naam |
|---|---|
| Schön | `schoen.html` |
| SC% &amp;&#42; ç+ | `sc---c-.html` |

### Naam {#name}

Wanneer u een pagina **Naam** wanneer het creëren van een pagina levert, bevestigt AEM [&#x200B; de naam volgens de overeenkomsten &#x200B;](/help/implementing/developing/introduction/naming-conventions.md) die door AEM en JCR worden opgelegd. U kunt geen ongeldige karakters op het **gebied van de Naam** voorleggen. Wanneer AEM ongeldige tekens detecteert, wordt het veld gemarkeerd met een verklarende melding.

![&#x200B; Voorbeeld van het ingaan van een ongeldige paginanaam &#x200B;](/help/sites-cloud/authoring/assets/organizing-invalid-name.png)

>[!TIP]
>
>Gebruik geen code van twee letters, zoals gedefinieerd door ISO-639-1, als paginanaam, tenzij dit een hoofdtaalcode is.
>
>Zie [&#x200B; Voorbereidend Inhoud voor Vertaling &#x200B;](/help/sites-cloud/administering/translation/preparation.md) voor meer informatie.

## Sjablonen {#templates}

In AEM, is a [&#x200B; malplaatje &#x200B;](/help/sites-cloud/authoring/page-editor/templates.md) een gespecialiseerd type van pagina die als basis voor om het even welke nieuwe pagina wordt gebruikt die wordt gecreeerd.

De sjabloon definieert de structuur van een pagina, inclusief een miniatuurafbeelding en andere eigenschappen. U hebt bijvoorbeeld aparte sjablonen voor productpagina&#39;s, sitemaps en contactgegevens. De malplaatjes worden samengesteld uit [&#x200B; componenten &#x200B;](#components).

AEM wordt geleverd met verschillende sjablonen die u kunt vinden. Welke sjablonen beschikbaar zijn, is afhankelijk van de afzonderlijke website. De belangrijkste velden zijn:

* **Titel** - de titel die op het resulterende Web-pagina wordt getoond
* **Naam** - Gebruikt wanneer het noemen van de pagina
* **Malplaatje** - een lijst van malplaatjes beschikbaar voor gebruik wanneer het produceren van de nieuwe pagina

## Onderdelen {#components}

[&#x200B; Componenten &#x200B;](/help/implementing/developing/components/overview.md) zijn de elementen die door AEM worden verstrekt zodat u specifieke soorten inhoud kunt toevoegen. AEM komt met een waaier van uit-van-de-doos componenten, genoemd [&#x200B; de Componenten van de Kern &#x200B;](/help/implementing/developing/components/overview.md#core-components), die uitvoerige functionaliteit verstrekken. Enkele voorbeelden van de componenten zijn:

* Tekst
* Afbeelding
* Titel
* Carrousel
* En nog veel meer

Zodra u hebt gecreeerd en een pagina geopend kunt u [&#x200B; inhoud toevoegen gebruikend de componenten &#x200B;](/help/sites-cloud/authoring/page-editor/edit-content.md#inserting-a-component), die van [&#x200B; componentenbrowser &#x200B;](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser) beschikbaar zijn.

>[!TIP]
>
>De [&#x200B; Console van Componenten &#x200B;](/help/sites-cloud/authoring/components-console.md) geeft een overzicht van de componenten op uw instantie.
