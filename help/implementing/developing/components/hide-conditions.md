---
title: Voorwaarden verbergen gebruiken
description: De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet.
exl-id: 2a96f246-fb0f-4298-899e-ebbf9fc1c96f
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Voorwaarden verbergen gebruiken {#using-hide-conditions}

De voorwaarden van de huid kunnen worden gebruikt om te bepalen als een componentenmiddel wordt teruggegeven of niet. Een voorbeeld van dit zou zijn wanneer een malplaatjeauteur de de lijstcomponent van de Component van de Kern [ ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/list.html) in de [ malplaatjedacteur ](/help/sites-cloud/authoring/page-editor/templates.md) vormt en besluit om de opties onbruikbaar te maken om de lijst te bouwen die op kindpagina&#39;s wordt gebaseerd. Als u deze optie in het ontwerpdialoogvenster uitschakelt, wordt een eigenschap zo ingesteld dat wanneer de component List wordt gerenderd, de voorwaarde hide wordt geëvalueerd en de optie om onderliggende pagina&#39;s weer te geven niet wordt weergegeven.

## Overzicht {#overview}

Dialogen kunnen zeer complex worden met talrijke opties voor de gebruiker, die slechts een fractie van de opties kan gebruiken die hun ter beschikking staan. Dit kan leiden tot een overweldigende ervaring voor de gebruikersinterface.

Door huidenvoorwaarden te gebruiken, hebben de beheerders, de ontwikkelaars, en de super gebruikers een manier om middelen te verbergen die op een reeks regels worden gebaseerd. Met deze functie kunnen ze bepalen welke bronnen moeten worden weergegeven wanneer een auteur inhoud bewerkt.

>[!NOTE]
>
>Het verbergen van een middel dat op een uitdrukking wordt gebaseerd vervangt ACL geen toestemmingen. De inhoud blijft bewerkbaar, maar wordt gewoon niet weergegeven.

## Implementatie- en gebruiksgegevens {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` is verantwoordelijk voor het filteren van de bronnen op basis van het bestaan en de waarde van de eigenschap `granite:hide` , die zich in het te filteren veld bevindt. De implementatie van `/libs/cq/gui/components/authoring/dialog/dialog.jsp` bevat een instantie van `FilteringResourceWrapper.`

De implementatie maakt gebruik van graniet [ ELResolver API ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html) en voegt een `cqDesign` douanevariabele via ExpressionCustomizer toe.

Hier volgen enkele voorbeelden van verbergingsvoorwaarden voor een ontwerpknooppunt onder `etc/design` of als een inhoudsbeleid.

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

* Om geldig te zijn, moet het bereik waarin de eigenschap wordt gevonden, worden uitgedrukt (bijvoorbeeld `cqDesign.myProperty` ).
* Waarden zijn alleen-lezen.
* De functies (indien nodig) moeten beperkt blijven tot een bepaalde reeks die door de dienst wordt geleverd.

## Voorbeeld {#example}

De voorbeelden van huidenvoorwaarden kunnen door AEM en de [ kerncomponenten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) in het bijzonder worden gevonden. Bijvoorbeeld, overweeg de [ component van de lijstkern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/list.html) zoals die in het [ WKND leerprogramma ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) wordt uitgevoerd.

[ Gebruikend de malplaatjeredacteur ](/help/sites-cloud/authoring/page-editor/templates.md), kan de malplaatjeauteur in de ontwerpdialoog bepalen welke opties van de lijstcomponent die aan de paginaauteur beschikbaar zijn. U kunt bijvoorbeeld instellen of de lijst een statische lijst moet zijn, een lijst met onderliggende pagina&#39;s, een lijst met gecodeerde pagina&#39;s enzovoort in- of uitschakelen.

Als een sjabloonauteur ervoor kiest de optie voor onderliggende pagina&#39;s uit te schakelen, wordt een ontwerpeigenschap ingesteld en wordt een voorwaarde voor verbergen aan de hand hiervan geëvalueerd. Hierdoor wordt de optie niet gerenderd voor de auteur van de pagina.

1. Door gebrek, kan de paginaauteur de component van de lijstkern gebruiken om een lijst te bouwen gebruikend kindpagina&#39;s door de optie **Pagina&#39;s van het Kind te kiezen**.

   ![ de montages van de Component van de Lijst ](assets/hide-conditions-list-settings.png)

1. In de ontwerpdialoog van de component van de lijstkern, kan de malplaatjeauteur de optie **kiezen maakt Kinderen** onbruikbaar om de optie te verhinderen om een lijst te produceren die op kindpagina&#39;s wordt gebaseerd aan de paginaauteur worden getoond.

   ![ het ontwerpdialoog van de Component van de Lijst ](assets/hide-conditions-list-design.png)

1. Een beleidsknooppunt wordt gemaakt onder `/conf/wknd/settings/wcm/policies/wknd/components/list` met een eigenschap `disableChildren` ingesteld op `true` .

   ![ structuur van de Knoop van verbergingsvoorwaarde ](assets/hide-conditions-node-structure.png)

1. De voorwaarde hide wordt gedefinieerd als de waarde van een eigenschap `granite:hide` in het knooppunt met dialoogeigenschappen `/libs/core/wcm/components/list/v2/list/cq:dialog/content/items/tabs/items/listSettings/items/columns/items/column/items/listFrom/items/children`

   ![ Evaluatie van huidenvoorwaarde ](assets/hide-conditions-evaluation.png)

1. De waarde van `disableChildren` wordt uit de ontwerpconfiguratie gehaald en de expressie `${cqDesign.disableChildren}` evalueert naar `false` , wat betekent dat de optie niet wordt gerenderd als onderdeel van de component.

1. De optie **Pagina&#39;s van het Kind** wordt niet meer teruggegeven voor de paginaauteur wanneer het gebruiken van de lijstcomponent.

   ![ Component van de Lijst met gehandicapte kindoptie ](assets/hide-conditions-child-disabled.png)
