---
title: Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM
description: Leer over de concepten en de mechanica van het modelleren van inhoud voor uw Headless CMS gebruikend de Modellen van Fragments van de Inhoud.
exl-id: fdfa79d3-fbed-4467-a898-c1b2678fc0cb
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 6306ad88b889197aff377dc0a72ea232cd76ff9c
workflow-type: tm+mt
source-wordcount: '636'
ht-degree: 0%

---

# Meer informatie over het maken van modellen voor inhoudsfragmenten in AEM {#architect-headless-content-fragment-models}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [ Reis van de Auteur van de Inhoud van AEM Headless ](overview.md) de [ Grondbeginselen van de Modellering van de Inhoud voor Zwaartepunt met AEM ](basics.md) behandelde de basisconcepten en de terminologie relevant voor creatie voor hoofd.

Dit artikel bouwt verder op deze principes zodat u begrijpt hoe u uw eigen modellen van het Fragment van de Inhoud voor uw project zonder titel van AEM creeert.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: de concepten en de mechanica van het modelleren van inhoud voor uw Hoofdloze CMS gebruikend de Modellen van de Fragmenten van de Inhoud.

<!-- which persona does this? -->
<!-- and who allows the configuration on the folders? -->

<!--
## Enabling Content Fragment Models {#enabling-content-fragment-models}

At the very start you need to enable Content Fragment Models for your site, this is done in the Configuration Browser; under Tools > General > Configuration Browser. You can either select to configure the global entry, or create a configuration. For example:

![Define configuration](/help/sites-cloud/administering/content-fragments/assets/cfm-conf-01.png)

>[!NOTE]
>
>See Additional Resources - Content Fragments in the Configuration Browser
-->

## Modellen voor inhoudsfragmenten maken {#creating-content-fragment-models}

Vervolgens kunt u de modellen van Content Fragments maken en de structuur definiëren.

1. Selecteer in de inhoudsfragmentconsole het deelvenster Modellen van inhoudsfragmenten.

1. Navigeer naar de map die geschikt is voor uw configuratie of subconfiguratie.

1. Het gebruik **leidt** tot om de **Nieuwe dialoog van het Fragmentmodel van de Inhoud** te openen.

   ![ Titel en beschrijving ](/help/sites-cloud/administering/content-fragments/assets/cf-managing-content-fragment-models-create.png)

1. De details invullen

1. Het gebruik **creeert** om het lege model te bewaren, of **creeert en opent**.

<!--
Then the Content Fragments Models can be created and the structure defined. This can be done under **Tools** > **General** > **Content Fragment Models**. 

![Content Fragment Models in Tools](assets/cfm-tools.png)

After selecting this you navigate to the location for your model and select **Create**. Here you can enter various key details.

The option **Enable model** is activated by default. This means that your model is available for use (in creating Content Fragments) as soon as you have saved it. You can deactivate this if you want - there are opportunities later to enable (or disable) an existing model.

![Create Content Fragment Model](/help/sites-cloud/administering/content-fragments/assets/cfm-models-02.png)

Confirm with **Create** and you can then **Open** your model to start defining the structure.
-->

## Modellen voor inhoudsfragmenten definiëren {#defining-content-fragment-models}

Wanneer u eerst een nieuw model opent u ziet - een grote lege ruimte aan de linkerzijde, en een lange lijst van **Types van Gegevens** bij het recht:

![ Leeg Model ](/help/sites-cloud/administering/content-fragments/assets/cfm-models-03.png)

Wat moet er gebeuren?

U kunt instanties van de **Types van Gegevens** op de linkerruimte slepen - u bepaalt reeds uw model!

![ die gebieden ](/help/sites-cloud/administering/content-fragments/assets/cfm-models-04.png) bepalen

Nadat u een gegevenstype toevoegt wordt u vereist om de **Eigenschappen** voor dat gebied te bepalen. Deze eigenschappen zijn afhankelijk van het type dat wordt gebruikt. Bijvoorbeeld:

![ Eigenschappen van Gegevens ](/help/sites-cloud/administering/content-fragments/assets/cfm-models-05.png)

U kunt zoveel velden toevoegen als u nodig hebt. Bijvoorbeeld:

![ Model van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/assets/cfm-models-07.png)

### Uw makers van inhoud {#your-content-authors}

De auteurs van de inhoud zien de gegevenstypen en eigenschappen die u hebt gebruikt om uw modellen te maken, niet. Dit betekent dat u mogelijk hulp en informatie moet bieden over de manier waarop specifieke velden worden ingevuld. Voor basisinformatie kunt u het Etiket van het Gebied en StandaardWaarde gebruiken, maar de complexere gevallen zouden de projectspecifieke documentatie kunnen moeten worden overwogen.

>[!NOTE]
>
>Zie Aanvullende bronnen - Modellen van inhoudsfragmenten.

## Modellen voor inhoudsfragmenten beheren {#managing-content-fragment-models}

<!-- needs more details -->

Het beheren van uw modellen van het Fragment van de Inhoud impliceert:

* Het toelaten (of het onbruikbaar maken) hen - dit maakt hen voor auteurs beschikbaar wanneer het creëren van de Fragmenten van de Inhoud.
* Verwijderen - verwijdering is altijd nodig, maar u moet wel weten dat u een model verwijdert dat al wordt gebruikt voor inhoudsfragmenten, met name fragmenten die al zijn gepubliceerd.

## Publiceren {#publishing}

<!-- needs more details -->

Inhoudsfragmentmodellen moeten worden gepubliceerd wanneer/voordat afhankelijke inhoudsfragmenten worden gepubliceerd.

>[!NOTE]
>
>Als een auteur een inhoudsfragment probeert te publiceren waarvoor het model nog niet is gepubliceerd, geeft een selectielijst dit aan en het model wordt gepubliceerd met het fragment.

Zodra een model wordt gepubliceerd is het *gesloten* in een LEZEN-ONLY wijze op auteur. Dit is bedoeld om wijzigingen te voorkomen die zouden leiden tot fouten in bestaande GraphQL-schema&#39;s en query&#39;s, met name in de publicatieomgeving. Het wordt vermeld in de console door **Vergrendelde**.

Wanneer het model **** (op LEZEN-ONLY wijze) wordt gesloten, kunt u de inhoud en de structuur van modellen zien maar u kunt hen niet direct uitgeven; hoewel u **Vergrendelde** modellen van of de console, of de modelredacteur kunt beheren.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap het creëren van uw eigen Modellen van het Fragment van de Inhoud te beginnen.

## Aanvullende bronnen {#additional-resources}

* [Concepten ontwerpen](/help/sites-cloud/authoring/author-publish.md)

* [ Basis Behandelend ](/help/sites-cloud/authoring/basic-handling.md) - deze pagina is hoofdzakelijk gebaseerd op de **console van Plaatsen**, maar vele/meeste eigenschappen zijn ook relevant voor het navigeren aan, en het nemen van actie op, **Modellen van het Fragment van de Inhoud** onder de **Algemene** console.

* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)

      * [Het model van het inhoudsfragment definiëren](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)

      * [Een inhoudsfragmentmodel in- of uitschakelen](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#enabling-disabling-a-content-fragment-model)

      * [Modellen voor inhoudsfragmenten toestaan in uw Assets-map](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#allowing-content-fragment-models-assets-folder)

      * [Een inhoudsfragmentmodel verwijderen](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#deleting-a-content-fragment-model)

      * [Een inhoudsfragmentmodel publiceren](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#publishing-a-content-fragment-model)

      * [Publicatie van een inhoudsfragmentmodel ongedaan maken](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#unpublishing-a-content-fragment-model)

      * [Vergrendelde modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#locked-content-fragment-models)

* Aan de slag - hulplijnen

   * [Modellen voor inhoudsfragmenten maken zonder kop instellen](/help/headless/setup/create-content-model.md)
