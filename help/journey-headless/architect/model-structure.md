---
title: Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM
description: Leer over de concepten en de mechanica van het modelleren van inhoud voor uw Zwaarloze CMS gebruikend de Modellen van de Fragments van de Inhoud.
index: true
hide: false
hidefromtoc: false
exl-id: fdfa79d3-fbed-4467-a898-c1b2678fc0cb
source-git-commit: 117d79b277118f39dfc442957989095bab5670b9
workflow-type: tm+mt
source-wordcount: '690'
ht-degree: 2%

---

# Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM {#architect-headless-content-fragment-models}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Headless Content Author Reis](overview.md) behandelde [Grondbeginselen van inhoudsmodellen voor headless met AEM](basics.md) de basisconcepten en de terminologie relevant voor het ontwerpen voor headless.

Dit artikel bouwt op deze voort zodat begrijpt u hoe te om uw eigen Modellen van het Fragment van de Inhoud voor uw project zonder AEM te creëren.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doel**: de concepten en de mechanica van het modelleren van inhoud voor uw Zwaarloze CMS gebruikend de Modellen van de Fragments van de Inhoud.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools -> General -> Configuration Browser. You can either select to configure the global entry, or create a new configuration. For example:

![Define configuration](/help/assets/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Modellen voor inhoudsfragmenten maken {#creating-content-fragment-models}

Vervolgens kunt u de modellen van Content Fragments maken en de structuur definiëren. U doet dit onder Gereedschappen -> Middelen -> Modellen voor inhoudsfragmenten.

![Modellen van inhoudsfragmenten in gereedschappen](assets/cfm-tools.png)

Nadat u deze optie hebt geselecteerd, navigeert u naar de locatie voor uw model en selecteert u **Maken**. Hier kunt u verschillende belangrijke details invoeren.

De optie **Model inschakelen** wordt standaard geactiveerd. Dit betekent dat uw model beschikbaar is voor gebruik (bij het maken van inhoudsfragmenten) zodra u het hebt opgeslagen. U kunt dit desgewenst deactiveren. Er zijn later mogelijkheden om een bestaand model in te schakelen (of uit te schakelen).

![Inhoudsfragmentmodel maken](/help/assets/content-fragments/assets/cfm-models-02.png)

Bevestig met **Create** en u kunt dan **Open** uw model beginnen de structuur te bepalen.

## Modellen voor inhoudsfragmenten definiëren {#defining-content-fragment-models}

Wanneer u eerst een nieuw model opent zult u zien - een grote lege ruimte aan de linkerzijde, en een lange lijst van **Types van Gegevens** bij het recht:

![Leeg model](/help/assets/content-fragments/assets/cfm-models-03.png)

Wat moet er gebeuren?

U kunt instanties van **Gegevenstypen** naar de linkerruimte slepen - u definieert reeds uw model!

![Velden definiëren](/help/assets/content-fragments/assets/cfm-models-04.png)

Nadat u een gegevenstype hebt toegevoegd, moet u **Eigenschappen** voor dat veld definiëren. Deze hangen van het type af dat wordt gebruikt. Bijvoorbeeld:

![Gegevenseigenschappen](/help/assets/content-fragments/assets/cfm-models-05.png)

U kunt zoveel velden toevoegen als u nodig hebt. Bijvoorbeeld:

![Inhoudsfragmentmodel](/help/assets/content-fragments/assets/cfm-models-07.png)

### Uw makers van inhoud {#your-content-authors}

De auteurs van de inhoud zien de gegevenstypen en eigenschappen die u hebt gebruikt om uw modellen te maken, niet. Dit betekent dat u mogelijk hulp en informatie moet bieden over de manier waarop specifieke velden worden ingevuld. Voor basisinformatie kunt u het Etiket van het Gebied en StandaardWaarde gebruiken, maar de complexere gevallen zouden de projectspecifieke documentatie kunnen moeten worden overwogen.

>[!NOTE]
>
>Zie Aanvullende bronnen - Modellen van inhoudsfragmenten.

## Modellen voor inhoudsfragmenten beheren {#managing-content-fragment-models}

<!-- needs more details -->

Het beheren van uw modellen van het Fragment van de Inhoud impliceert:

* Het toelaten (of het onbruikbaar maken) hen - dit maakt hen voor auteurs beschikbaar wanneer het creëren van de Fragmenten van de Inhoud.
* Verwijderen - verwijdering is altijd nodig, maar u moet er rekening mee houden dat u een model verwijdert dat al wordt gebruikt voor inhoudsfragmenten, met name fragmenten die al zijn gepubliceerd.

## Publiceren {#publishing}

<!-- needs more details -->

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

>[!NOTE]
>
>Als een auteur een inhoudsfragment probeert te publiceren waarvoor het model nog niet is gepubliceerd, zal een selectielijst dit vermelden en het model zal met het fragment worden gepubliceerd.

Zodra een model wordt gepubliceerd is het *locked* in een LEZEN-ONLY wijze op auteur. Dit is bedoeld om veranderingen te verhinderen die in fouten aan bestaande schema&#39;s en vragen GraphQL, vooral op het publicatiemilieu zouden resulteren. Dit wordt in de console aangegeven met **Locked**.

Wanneer het model **Locked** (in LEZEN-slechts wijze) is, kunt u de inhoud en de structuur van modellen zien maar u kunt hen niet direct uitgeven; hoewel u **Locked** modellen van of de console, of modelredacteur kunt beheren.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap het creëren van uw eigen Modellen van het Fragment van de Inhoud te beginnen.

## Aanvullende bronnen {#additional-resources}

* [Authoring van concepten](/help/sites-cloud/authoring/getting-started/concepts.md)

* [Basisverwerking](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - deze pagina is hoofdzakelijk gebaseerd op de  **** Sitesconsole, maar vele/de meeste eigenschappen zijn ook relevant voor het navigeren aan, en het nemen van actie op, de  **Modellen van het Fragment van de** Inhoud onder de console  **** van Activa.

* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)

   * [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)

      * [Het model van het inhoudsfragment definiëren](/help/assets/content-fragments/content-fragments-models.md#defining-your-content-fragment-model)

      * [Een inhoudsfragmentmodel in- of uitschakelen](/help/assets/content-fragments/content-fragments-models.md#enabling-disabling-a-content-fragment-model)

      * [Modellen voor inhoudsfragmenten toestaan in de middelenmap](/help/assets/content-fragments/content-fragments-models.md#allowing-content-fragment-models-assets-folder)

      * [Een inhoudsfragmentmodel verwijderen](/help/assets/content-fragments/content-fragments-models.md#deleting-a-content-fragment-model)

      * [Een inhoudsfragmentmodel publiceren](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model)

      * [Publicatie van een inhoudsfragmentmodel ongedaan maken](/help/assets/content-fragments/content-fragments-models.md#unpublishing-a-content-fragment-model)

      * [Vergrendelde (gepubliceerde) modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md#locked-published-content-fragment-models)

* Aan de slag - hulplijnen

   * [Modellen voor inhoudsfragmenten maken, headless Quick Start Guide](/help/implementing/developing/headless/getting-started/create-content-model.md)
