---
title: Voorwaarden verbergen gebruiken
description: De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 1%

---


# Voorwaarden {#using-hide-conditions} verbergen gebruiken

De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet. Een voorbeeld van dit zou zijn wanneer een malplaatjeauteur de Component [list ](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/list.html) in [malplaatjeredacteur](/help/sites-cloud/authoring/features/templates.md) vormt en besluit om de opties onbruikbaar te maken om de lijst te bouwen die op kindpagina&#39;s wordt gebaseerd. Als u deze optie in het ontwerpdialoogvenster uitschakelt, wordt een eigenschap zo ingesteld dat wanneer de component List wordt gerenderd, de voorwaarde hide wordt geëvalueerd en de optie om onderliggende pagina&#39;s weer te geven niet wordt weergegeven.

## Overzicht {#overview}

Dialogen kunnen zeer complex worden met talrijke opties voor de gebruiker, die slechts een fractie van de opties kan gebruiken die hun ter beschikking staan. Dit kan leiden tot een overweldigende ervaring voor de gebruikersinterface.

Door huidenvoorwaarden te gebruiken, hebben de beheerders, de ontwikkelaars, en de super gebruikers een manier om middelen te verbergen die op een reeks regels worden gebaseerd. Met deze functie kunnen ze bepalen welke bronnen moeten worden weergegeven wanneer een auteur inhoud bewerkt.

>[!NOTE]
>
>Het verbergen van een middel dat op een uitdrukking wordt gebaseerd vervangt ACL geen toestemmingen. De inhoud blijft bewerkbaar, maar wordt gewoon niet weergegeven.

## Implementatie- en gebruiksdetails {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` is verantwoordelijk het filtreren van de middelen die op het bestaan en de waarde van het  `granite:hide` bezit worden gebaseerd, dat op het te filteren gebied wordt gevestigd. De implementatie van `/libs/cq/gui/components/authoring/dialog/dialog.jsp` omvat een geval van `FilteringResourceWrapper.`

De implementatie maakt gebruik van de graniet [ELResolver API](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html) en voegt een `cqDesign` douanevariabele via ExpressionCustomizer toe.

Hier zijn een paar voorbeelden van huidenvoorwaarden op een ontwerpknoop die of onder `etc/design` of als Beleid van de Inhoud wordt gevestigd.

```
${cqDesign.myProperty}
${!cqDesign.myProperty}
${cqDesign.myProperty == 'someText'}
${cqDesign.myProperty != 'someText'}
${cqDesign.myProperty == true}
${cqDesign.myProperty == true}
${cqDesign.property1 == 'someText' && cqDesign.property2 || cqDesign.property3 != 1 || header.myHeader}
```

Houd rekening met het volgende wanneer u de expressie hide definieert:

* Om geldig te zijn, moet het bereik waarin de eigenschap wordt gevonden, worden uitgedrukt (bijvoorbeeld `cqDesign.myProperty`).
* Waarden zijn alleen-lezen.
* Functies (indien vereist) moeten worden beperkt tot een bepaalde set die door de dienst wordt geleverd.

## Voorbeeld {#example}

Voorbeelden van huidencondities zijn te vinden door AEM en met name de [kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html). Neem bijvoorbeeld de [lijstkerncomponent](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/list.html) zoals geïmplementeerd in de [WKND-zelfstudie.](/help/implementing/developing/introduction/develop-wknd-tutorial.md)

[Met behulp van de sjablooneditor](/help/sites-cloud/authoring/features/templates.md) kan de sjabloonauteur in het ontwerpdialoogvenster definiëren welke opties van de lijstcomponent beschikbaar zijn voor de auteur van de pagina. U kunt bijvoorbeeld instellen of de lijst een statische lijst moet zijn, een lijst met onderliggende pagina&#39;s, een lijst met gecodeerde pagina&#39;s, enzovoort. kan worden in- of uitgeschakeld.

Als een sjabloonauteur ervoor kiest de optie voor onderliggende pagina&#39;s uit te schakelen, wordt een ontwerpeigenschap ingesteld en wordt een voorwaarde voor verbergen aan de hand hiervan geëvalueerd. Hierdoor wordt de optie niet gerenderd voor de auteur van de pagina.

1. Standaard kan de auteur van de pagina de kerncomponent van de lijst gebruiken om een lijst op te bouwen met behulp van onderliggende pagina&#39;s door de optie **Onderliggende pagina&#39;s** te kiezen.

   ![Componentinstellingen weergeven](assets/hide-conditions-list-settings.png)

1. In de ontwerpdialoog van de component van de lijstkern, kan de malplaatjeauteur de optie **Kinderen onbruikbaar maken** kiezen om de optie te verhinderen om een lijst te produceren die op kindpagina&#39;s wordt gebaseerd aan de paginaauteur worden getoond.

   ![Dialoogvenster Componentontwerp weergeven](assets/hide-conditions-list-design.png)

1. Een beleidsknooppunt wordt gemaakt onder `/conf/wknd/settings/wcm/policies/wknd/components/list` met een eigenschap `disableChildren` ingesteld op `true`.

   ![Knooppuntstructuur van toestand Verbergen](assets/hide-conditions-node-structure.png)

1. De voorwaarde hide wordt gedefinieerd als de waarde van een eigenschap `granite:hide` op het knooppunt van de dialoogeigenschap `/libs/core/wcm/components/list/v2/list/cq:dialog/content/items/tabs/items/listSettings/items/columns/items/column/items/listFrom/items/children`

   ![Evaluatie van de toestand van de huid](assets/hide-conditions-evaluation.png)

1. De waarde van `disableChildren` wordt gehaald uit de ontwerpconfiguratie en de uitdrukking `${cdDesign.disableChildren}` evalueert aan `false`, betekenend zal de optie niet als deel van de component worden teruggegeven.

1. De optie **Onderliggende pagina&#39;s** wordt niet meer weergegeven voor de auteur van de pagina wanneer de component List wordt gebruikt.

   ![Component weergeven met onderliggende optie uitgeschakeld](assets/hide-conditions-child-disabled.png)
