---
title: Meer informatie over het gebruik van verwijzingen in inhoudsfragmenten
description: Leer over het gebruiken van verwijzingen in de Fragmenten van de Inhoud, voor inhoud, andere fragmenten en andere activa (media). Introduceer de noodzaak voor en de mechaniek van geneste fragmenten voor CMS-creatie zonder koppen.
exl-id: a65e8a5a-954b-4307-8027-ca8bac5f4261
solution: Experience Manager
feature: Headless
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 0%

---

# Meer informatie over het gebruik van verwijzingen in inhoudsfragmenten {#author-headless-references}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Schrijverreis zonder kopinhoud](overview.md) de [Inleiding](introduction.md) heeft betrekking op de basisbegrippen en de terminologie die relevant zijn voor het ontwerpen van koploze producten.

U hebt de grondbeginselen van de Authoring van CMS zonder hoofd geleerd, met een inleiding tot het ontwerpen met AEMaaCS en in het bijzonder, het ontwerpen van Inhoudsfragmenten.

Dit artikel bouwt op deze voort zodat begrijpt u hoe te om verwijzingen te gebruiken naar auteur uw eigen inhoud voor uw project zonder AEM.

## Doelstelling {#objective}

* **Publiek**: Geavanceerd
* **Doelstelling**: Introduceer het gebruik van verwijzingen voor CMS-ontwerpen zonder koptekst. Welke soorten verwijzingen beschikbaar zijn, en wat zijn hun doeleinden:

   * Content References
   * Verwijzingen naar element/media
   * Fragmentverwijzingen
   * Verbeterde verwijzingen vanuit een tekstblok

## Wat zijn referenties? {#what-are-references}

Verwijzingen zijn gewoon een mechanisme om uw bronnen aan te sluiten, of het nu andere inhoud, elementen (zoals afbeeldingen) of andere fragmenten betreft. Er zijn enkele verschillen, ook al zijn deze zeer vergelijkbaar.

Sommige verwijzingen hebben specifieke gegevenstypen (bijvoorbeeld Content References en Fragmentverwijzingen), terwijl andere eenvoudig worden toegevoegd als een verwijzing binnen een tekstblok (elementverwijzingen en geïmproviseerde verwijzingen).

![Inhoudsfragmenten - verwijzingen](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-overview.png)

## Content References {#content-references}

Content Reference do just that - they allow you to reference any other content. Hiermee wordt een browser geopend waarin u het inhoudsitem kunt selecteren.

## Verwijzingen naar element/media {#assets-media-references}

In een tekstblok kan naar elementen (bijvoorbeeld afbeeldingen of media) worden verwezen met de opdracht **Element invoegen** -optie. Hiermee opent u een browser waarin u het element kunt selecteren.

![Inhoudsfragmenten - Element invoegen](/help/journey-headless/author/assets/headless-journey-author-references-02.png)

## Fragmentverwijzingen {#fragment-references}

Ook hier geldt dat fragmentverwijzingen alleen maar kunnen verwijzen naar een ander fragment. Waarom dit belangrijk is, moet er wat meer uitleg komen.

U kunt bijvoorbeeld de volgende modellen van inhoudsfragmenten definiëren:

* Plaats
* Bedrijf
* Persoon
* Uitreiking

Het lijkt vrij eenvoudig, maar een bedrijf heeft zowel een CEO als werknemers...en dit zijn allemaal mensen, elk gedefinieerd als een persoon.

En een persoon kan een Prijs (of misschien twee) hebben.

* Mijn bedrijf - Bedrijf
   * CEO - Persoon
   * Werknemer(s) - Persoon
      * Persoonlijke onderscheiding(en) - Uitreiking

Dat is alleen maar voor starters. Afhankelijk van de complexiteit kan een prijs bedrijfsspecifiek zijn of kan een bedrijf zijn hoofdkantoor in een bepaalde stad hebben.

U kunt deze relaties vertegenwoordigen met fragmentverwijzingen, omdat deze worden begrepen door zowel u (de auteur) als de toepassingen zonder kop.

Als auteur bent u niet verantwoordelijk voor het definiëren van deze relaties (dat wordt gedaan door de Content Architect bij het maken van het Content Fragment Model), maar u moet weten hoe u de verwijzingen herkent en bewerkt.

<!--
![Content Modeling with Content Fragments](/help/journey-headless/developer/assets/headless-modeling-01.png "Content Modeling with Content Fragments")
-->

### Geneste fragmenten ontwerpen {#author-nested-fragment}

Verwijzingen naar fragmenten ontwerpen is vrij eenvoudig (hoewel het veld doorgaans niet wordt aangeduid als **Fragmentverwijzing**). U kunt de verwijzing rechtstreeks invoeren of (waarschijnlijker) het mappictogram selecteren om een browser te openen waarin u door het gewenste fragment kunt navigeren en het gewenste fragment kunt selecteren.

![Inhoudsfragmenten - verwijzingen](/help/journey-headless/author/assets/headless-journey-author-references-03.png)

De definitie van de besturingselementen van het inhoudsfragmentmodel:

* of u meerdere referenties kunt selecteren om toe te voegen
* de modeltypen van inhoudsfragmenten die u kunt selecteren; het model van het Fragment van de Inhoud bepaalt de fragmentmodellen die voor de verwijzing worden toegestaan, zodat AEM slechts fragmenten presenteert die op die modellen worden gebaseerd.

### Door geneste fragmenten navigeren {#navigate-nested-fragment}

Met de **Boomstructuur** van de Inhoudsfragmenteditor kunt u door de fragmenten navigeren waarnaar wordt verwezen door het fragment en vervolgens door alle verwijzingen die het fragment bevat. Als u een verwijzing selecteert, wordt dat fragment geopend voor bewerking.

![Structuuromvang van inhoudsfragment](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-structure-tree.png)

## Ad-hocverwijzingen {#adhoc-references}

De verbeterde verwijzingen kunnen als eenvoudige verbinding binnen een blok van tekst worden toegevoegd:

![Inhoudsfragmenten - Eenvoudige verwijzingen](/help/journey-headless/author/assets/headless-journey-author-references-04.png)

## Volgende functies {#whats-next}

Nu u over verwijzingen en structuur in Inhoudsfragmenten hebt geleerd, is de volgende stap: [Meer informatie over metagegevens en tags toevoegen](metadata-tagging.md). Zo leert en bespreekt u hoe u metagegevens en tags voor de inhoudsfragmenten kunt definiëren.

## Aanvullende bronnen {#additional-resources}

* [Werken met inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

   * [Inhoudsfragmenten beheren](/help/sites-cloud/administering/content-fragments/managing.md)

      * [De configuratie toepassen op de middelenmap](/help/sites-cloud/administering/content-fragments/setup.md#apply-the-configuration-to-your-folder)

      * [Een inhoudsfragment maken](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment)

   * [Inhoudsfragmenten ontwerpen](/help/sites-cloud/administering/content-fragments/authoring.md)

   * [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)

      * [Modellen van inhoudsfragmenten - gegevenstypen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)

      * [Modellen van inhoudsfragmenten - eigenschappen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties)

* Aan de slag - hulplijnen
   * [Een middelenmap maken - Instellingen zonder kop](/help/headless/setup/create-assets-folder.md)

* Reis van architect zonder hoofdinhoud AEM

* AEM doorsnedenloze vertaalreis
