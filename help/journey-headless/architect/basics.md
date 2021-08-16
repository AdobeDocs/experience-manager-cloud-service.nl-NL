---
title: Basisbeginselen van Content Modeling
description: Leer de basis van het modelleren van inhoud voor uw Zwaarloze CMS gebruikend de Fragments van de Inhoud.
index: false
hide: true
hidefromtoc: true
source-git-commit: 41ad9e8ee77ae4494d28026b5ad9da45c06eaeaf
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 1%

---


# Leer de basisbeginselen van de Content Modeling voor headless met AEM {#content-modeling-headless-basics}

## Het artikel tot nu toe {#story-so-far}

Aan het begin van de [AEM Headless Content Architect Journey](overview.md) heeft de [Inleiding](introduction.md) de basisconcepten en -terminologie behandeld die relevant zijn voor het modelleren van inhoud voor zonder kop.

Dit artikel bouwt hierop voort, zodat u begrijpt hoe u uw inhoud voor uw project zonder AEM kunt modelleren.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doel**: Introduceer de concepten Inhoud modelleren voor Hoofdloze CMS.

## Inhoud modelleren met modellen van inhoudsfragmenten {#architect-content-fragment-models}

De modellering van de inhoud (Gegevens) is een reeks gevestigde technieken, vaak gebruikt wanneer ontwikkelde relatiedatabases, zodat wat de Modellering van de Inhoud voor AEM Zwaartepunt betekent?

### Waarom? {#why}

Om ervoor te zorgen dat uw toepassing de vereiste inhoud van AEM consistent en efficiënt kan aanvragen en ontvangen, moet deze inhoud gestructureerd zijn.

Dit betekent dat uw toepassing van tevoren de vorm van de reactie en daarom hoe te om het weet te verwerken. Dit is veel gemakkelijker dan het ontvangen van vrije-vorminhoud, die moet worden geparseerd om te bepalen wat het bevat en daarom, hoe het kan worden gebruikt.

### Inleiding aan hoe? {#how}

AEM gebruikt Content Fragments om de structuren te bieden die nodig zijn voor de levering van inhoud zonder kop aan uw toepassingen.

De structuur van het inhoudsmodel is:

* door de definitie van het inhoudsfragmentmodel wordt gerealiseerd,
* gebruikt als basis voor de Inhoudsfragmenten die worden gebruikt voor het genereren van inhoud.

>[!NOTE]
>
>De modellen van het Fragment van de Inhoud worden ook gebruikt als basis van de AEM Schema GraphQL, die voor het terugwinnen van uw inhoud - meer over dat in de Reis van de Ontwikkelaar wordt gebruikt.

Verzoeken om uw inhoud worden gemaakt met de AEM GraphQL API, een aangepaste implementatie van de standaard GraphQL API. AEM GraphQL API staat toepassingen toe om (complexe) vragen op uw Fragments van de Inhoud uit te voeren, met elke vraag die volgens een specifiek modeltype is.

De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## De structuur maken met modellen van inhoudsfragmenten {#create-structure-content-fragment-models}

Modellen van inhoudsfragmenten bieden verschillende mechanismen waarmee u de structuur van de inhoud kunt definiëren.

Een inhoudsfragmentmodel beschrijft een entiteit.

>[!NOTE]
>De functionaliteit van het Fragment van de inhoud moet in Browser van de Configuratie worden toegelaten zodat u nieuwe modellen kunt tot stand brengen.

>[!TIP]
>
>Het model moet een naam krijgen, zodat de auteur van de inhoud weet welk model moet worden geselecteerd bij het maken van een inhoudsfragment.

Binnen een model:

1. **Met** gegevenstypen kunt u de afzonderlijke kenmerken definiëren.
Definieer bijvoorbeeld het veld met de naam van een docent als **Text** en de bijbehorende servicejaren als **Number**.
1. Met de gegevenstypen **Content Reference** en **Fragmentverwijzing** kunt u relaties maken met andere inhoud binnen AEM.
1. Met het gegevenstype **Fragmentverwijzing** kunt u meerdere structuurniveaus realiseren door de Content Fragments (op basis van het modeltype) te nesten. Dit is van essentieel belang voor het modelleren van inhoud.

Bijvoorbeeld:

![Inhoud modelleren met Content ](assets/headless-modeling-01.png "FragmentsContent Modeling met Content Fragments")

## Gegevenstypen {#data-types}

AEM bevat de volgende gegevenstypen waarmee u uw inhoud kunt modelleren:

* Tekst met één regel
* Tekst met meerdere regels
* Getal
* Boolean
* Datum en tijd
* Opsomming
* Tags
* Content Reference
* Fragmentverwijzing
* JSON-object

>[!NOTE]
>
>Meer details zijn beschikbaar onder Modellen van het Fragment van de Inhoud - de Types van Gegevens.

## Verwijzingen en geneste inhoud {#references-nested-content}

Twee gegevenstypen bevatten verwijzingen naar inhoud buiten een specifiek fragment:

* **Content**
ReferenceThis verstrekt een eenvoudige verwijzing naar andere inhoud van om het even welk type.
U kunt bijvoorbeeld naar een afbeelding op een bepaalde locatie verwijzen.

* **Fragment**
ReferenceThis biedt verwijzingen naar andere inhoudsfragmenten.
Dit type verwijzing wordt gebruikt om geneste inhoud te creëren, introducerend de verhoudingen nodig om uw inhoud te modelleren.
Het gegevenstype kan worden geconfigureerd om fragmentauteurs toe te staan:
   * Bewerk het fragment waarnaar wordt verwezen rechtstreeks.
   * Een nieuw inhoudsfragment maken op basis van het juiste model

>[!NOTE]
>
>U kunt ook ad-hocverwijzingen maken met koppelingen in tekstblokken.

## Structuurniveaus (geneste fragmenten) {#levels-of-structure-nested-fragments}

Voor inhoud die het **gegevenstype van de Verwijzing van het Fragment** modelleert staat u toe om veelvoudige niveaus van structuur en verhoudingen tot stand te brengen.

Met deze verwijzing kunt u *verbinden* diverse Modellen van het Fragment van de Inhoud om interrelaties te vertegenwoordigen. Hierdoor kan de toepassing zonder kop de verbindingen volgen en zo nodig toegang krijgen tot de inhoud.

>[!NOTE]
>
>Dit moet met voorzichtigheid worden gebruikt en de beste praktijken kunnen als *nest zo veel als nodig, maar zo weinig mogelijk* worden gedefinieerd.

Fragmentverwijzingen doen alleen dat - ze stellen u in staat naar een ander fragment te verwijzen.

U kunt bijvoorbeeld de volgende modellen van inhoudsfragmenten definiëren:

* Plaats
* Bedrijf
* Person
* Awards

Het lijkt vrij eenvoudig, maar een bedrijf heeft natuurlijk zowel een CEO als werknemers....en dit zijn allemaal mensen, elk gedefinieerd als een persoon.

En een persoon kan een Prijs (of misschien twee) hebben.

* Mijn bedrijf - Bedrijf
   * CEO - Persoon
   * Werknemer(s) - Persoon
      * Persoonlijke onderscheiding(en) - Uitreiking

Dat is alleen maar voor starters. Afhankelijk van de complexiteit kan een prijs bedrijfsspecifiek zijn of kan een bedrijf zijn hoofdkantoor in een bepaalde stad hebben.

U kunt deze interrelaties vertegenwoordigen met fragmentverwijzingen, zoals u (de architect), de auteur van de inhoud en de toepassingen zonder kop ze begrijpt.

## Volgende functies {#whats-next}

Nu u de grondbeginselen hebt geleerd, is de volgende stap [Leren over het Creëren van Modellen van het Fragment van de Inhoud in AEM](model-structure.md). Dit zal de diverse beschikbare verwijzingen introduceren en bespreken, en hoe te om niveaus van structuur met de Verwijzingen van het Fragment tot stand te brengen - een zeer belangrijk deel van modellering voor headless.

## Aanvullende bronnen {#additional-resources}

* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)

   * [Content Fragment Models - Data Types](/help/assets/content-fragments/content-fragments-models.md#data-types)

* [Authoring van concepten](/help/sites-cloud/authoring/getting-started/concepts.md)

* [Basisverwerking](/help/sites-cloud/authoring/getting-started/basic-handling.md)  - deze pagina is hoofdzakelijk gebaseerd op de  **** Sitesconsole, maar vele/de meeste eigenschappen zijn ook relevant voor het ontwerpen van  **Inhoud** Fragmentseert onder de  **** console van Activa.

* [Werken met contentfragmenten](/help/assets/content-fragments/content-fragments.md)
