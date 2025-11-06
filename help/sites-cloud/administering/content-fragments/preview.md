---
title: Voorvertoning van inhoudsfragmenten weergeven
description: Begrijp hoe u een voorvertoning van de inhoudsfragmenten kunt weergeven aan de hand van een reeks methoden.
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 1%

---

# Voorvertoning van inhoudsfragmenten weergeven {#previewing-content-fragments}

Inhoudsfragmenten kunnen zowel voor koploze levering als voor het schrijven van pagina&#39;s worden gebruikt. Aangezien de fragmenten uitsluitend inhoud zijn, zonder opmaak, kan het reviseren ervan een grotere uitdaging zijn. Er zijn dus meerdere methoden beschikbaar voor het voorvertonen van fragmenten, in verschillende scenario&#39;s.

Er zijn verscheidene methodes beschikbaar voor de Fragmenten van de Inhoud, die bij de console en de redacteur van de Fragmenten van de Console toegankelijk zijn. De console en de redacteur die in deze sectie worden beschreven zijn ontwikkeld voor hoofdloze inhoudslevering (hoewel zij voor alle scenario&#39;s kunnen worden gebruikt).

U kunt een voorvertoning van het fragment weergeven:

* gebruikend het [ patroon van URL van de Voorproef ](#preview-url-pattern)

* door te publiceren aan, en unpublishing van, de [ instantie van de Voorproef ](#preview-instance)

<!--
* with a HTML template, using **[Preview]()** from the Content Fragments console
-->

Natuurlijk, kunt u uw fragment in de [ redacteur van het Fragment van de Inhoud ook bekijken ](/help/sites-cloud/administering/content-fragments/authoring.md).

>[!IMPORTANT]
>
>De Fragmenten van de inhoud kunnen van twee consoles worden betreden: **de Fragmenten van de Inhoud** en **Assets**.
>
>Er zijn ook twee editors voor het ontwerpen van inhoudsfragmenten. Hoewel de basisfunctionaliteit hetzelfde is, zijn er enkele verschillen. Beide editors zijn toegankelijk vanuit beide consoles.
>
>Deze sectie behandelt de **console van de Fragmenten van de Inhoud** en de *nieuwe* redacteur van het Fragment van de Inhoud. Deze zijn ontwikkeld voor inhoud zonder kop (hoewel ze voor alle scenario&#39;s kunnen worden gebruikt)
>
>Zie voor meer informatie:
>
>* gebruik van de **Assets** console voor [ het beheren van de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md)
>* gebruik van de [*originele* redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-variations.md),
>* het gebruiken van [ Fragmenten van de Inhoud voor pagina-creatie ](/help/sites-cloud/authoring/fragments/content-fragments.md).

## Voorbeeld-URL-patroon {#preview-url-pattern}

De inhoudsfragmenteditor biedt auteurs de mogelijkheid om een voorvertoning van hun bewerkingen weer te geven in een externe frontendtoepassing.

Als u deze functie wilt gebruiken, moet u eerst:

* Werk met uw IT-team om de externe frontendtoepassing in te stellen die het inhoudsfragment rendert door de JSON-uitvoer te verbruiken.

* Wanneer de externe frontend toepassing opstelling is, moet het **StandaardPatroon van de Voorproef URL** als a [ bezit van het aangewezen Model van het Fragment van de Inhoud worden bepaald ](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#model-properties).

De voorbeeld-URL moet dit patroon volgen:

    `https://<preview_url>?param=${expression}`

Beschikbare expressies zijn:

* `${contentFragment.path}`
* `${contentFragment.model.path}`
* `${contentFragment.model.name}`
* `${contentFragment.variation}`
* `${contentFragment.id}`

Wanneer URL is bepaald, is de **[knoop van de Voorproef](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)** actief in de hoogste toolbar van de redacteur. U kunt deze knop selecteren om de externe toepassing te starten (op een afzonderlijk tabblad) om het inhoudsfragment te renderen.

## Voorvertoning van instantie {#preview-instance}

U kunt **publiceren**, en ****, uw fragment aan uw **[Dienst van de Voorproef](/help/headless/deployment/architecture.md)** (evenals aan uw Publish instantie) ongedaan maken.

U kunt het fragment publiceren vanuit de editor of de console.

Zie:

* [ het Publiceren en het Voorvertonen van een Fragment ](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) voor volledige details.

* [ Unpublishing een fragment ](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) voor volledige details.

<!--
## Preview based on a HTML Template {#preview-based-on-a-html-template}

The Content Fragment console provides a **Preview** option for every fragment.

The icon can be selected to open a dialog that represents the fragment based on a HTML template. You can use the default template, or develop and load your own.
-->
