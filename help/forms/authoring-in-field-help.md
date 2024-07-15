---
title: Hoe kunt u Help-tekst toevoegen voor AEM Adaptive Forms-velden?
description: Met AEM Forms kunt u in de context Help toevoegen aan velden en deelvensters voor adaptieve formulieren als tekst of rich media, waaronder video's.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
source-git-commit: 0f8aed76af4d2640094a76f2805f73a0a619e33f
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Contextassistentie voor het ontwerpen van formuliervelden{#authoring-in-context-help-for-form-fields}

## Inleiding {#introduction}

In bepaalde situaties weten eindgebruikers die een formulier invullen niet zeker hoe ze details in een bepaald formulierveld moeten invullen. Om dergelijke problemen aan te pakken, biedt Adaptive Forms ondersteuning voor het toevoegen van tekst of uitgebreide contexthulp aan een formulierveld. Hiermee verbetert u de ervaring bij het invullen van formulieren en voorkomt u dubbelzinnigheid voor eindgebruikers.

In dit artikel wordt besproken hoe formulierauteurs in-context Help kunnen toevoegen tijdens het ontwerpen van Adaptive Forms.

## In-context-Help toevoegen {#add-in-context-help}

U kunt in-context hulp specificeren gebruikend de volgende opties in de sectie van de Inhoud van de Hulp van het eigenschappen lusje in sidebar.

* [Korte beschrijving](authoring-in-field-help.md#p-short-description-p)
* [Lange beschrijving](authoring-in-field-help.md#p-long-description-p)

![ In-context hulp voor vormgebieden ](assets/descriptions.png)

>[!NOTE]
>
>Lange beschrijving heeft voorrang op de korte beschrijving. Als u beide hebt opgegeven, wordt alleen de beschrijving Lang weergegeven.

### Korte beschrijving {#short-description}

In het veld Korte beschrijving kunt u snelle en korte aanwijzingen geven over het invullen van een formulierveld. De tekst die in het veld Korte beschrijving is opgegeven, wordt als knopinfo weergegeven wanneer u de muis boven het veld houdt.

![ Korte beschrijving voor het toevoegen van in-context hulp voor vormgebieden ](assets/tooltip.png)

>[!NOTE]
>
>Selecteer **altijd tonen korte beschrijving** om de hulptekst onder het gebied permanent te tonen.

![ Permanente korte in-context hulp onder het gebied ](assets/short1.png)

### Lange beschrijving {#long-description}

U kunt het lange beschrijvingsgebied gebruiken om lange teksten te specificeren of rijke media inhoud, met inbegrip van video&#39;s in te bedden, als in-context hulp. In de volgende afbeelding ziet u bijvoorbeeld hoe u een video kunt insluiten als in-context-Help.

![ Toevoegend rijke media als in-context hulp voor vormgebieden ](assets/long-descriptions.png)

Als u een lange beschrijving toevoegt, wordt een **weergegeven?** naast het veld. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de lange beschrijving.

![ Voorbeeld van rijke media in-context hulp ](assets/photoshop.png)

### Help op deelvensterniveau {#panel-level-help}

Naast de contextHelp voor formuliervelden kunt u op deelvensterniveau Help opgeven op het tabblad Help-inhoud van het dialoogvenster Bewerken van het deelvenster.

![ Toevoegend in-context hulp voor een vormpaneel ](assets/panel-level-help.png)

Wanneer u Help voor het deelvenster toevoegt, wordt een **weergegeven?** naast de beschrijving van het deelvenster. Als u op het pictogram klikt, wordt de inhoud weergegeven die is toegevoegd in de sectie Help-inhoud van het dialoogvenster voor het bewerken van deelvensters.

![ Voorbeeld van in-context hulp op het niveau van het vormpaneel ](assets/photoshop-1.png)

>[!MORELIKETHIS]
>
>* [ voeg placeholder tekst aan vormgebieden toe ](/help/forms/placeholder-text-in-aem-forms.md)
>* [ voeg Voetnoot aan een adaptieve vorm voor rijke teksten ](/help/forms/footnotes-richtextsupport.md) toe