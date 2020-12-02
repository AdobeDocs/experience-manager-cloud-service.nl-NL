---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van elementen in AEM Assets en verschillende manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 8%

---


# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat bedrijven gecontroleerde en betrouwbare taalwoordenboeken voor metagegevens nodig hebben, staat AEM Assets het niet toe om ad-hocnieuwe eigenschappen voor metagegevens toe te voegen. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element {#editing-metadata-for-an-asset} bewerken

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de interface Elementen en klik op het pictogram **[!UICONTROL View Properties]** op de werkbalk.
   * Selecteer in de elementminiatuur de snelle handeling **[!UICONTROL View Properties]**.
   * Klik/tik **[!UICONTROL View Properties]** op de werkbalk vanaf de elementpagina.

   Op de elementpagina worden alle metagegevens van het element weergegeven. Deze metagegevens worden automatisch geëxtraheerd bij het uploaden (invoegen) naar AEM Assets.

1. Bewerk desgewenst de metadata op de verschillende tabbladen en klik of tik wanneer u klaar bent op **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan. Klik of tik op **[!UICONTROL Close]** om terug te keren naar de webinterface voor assets.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Eventuele wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP gegevens. Dit gebeurt via AEM workflow voor het terugschrijven van metagegevens. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title`) worden overschreven en nieuwe eigenschappen (zoals aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Metagegevensschema bewerken {#editing-metadata-schema}

Zie [Formulieren met metagegevens bewerken](metadata-schemas.md#edit-metadata-schema-forms) voor meer informatie over het bewerken van het schema voor metagegevens.

## Een aangepaste naamruimte registreren in AEM {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen binnen AEM. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Ga naar de knooptype beleidspagina *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Klik of tik **[!UICONTROL Namespaces]** bij de bovenkant van de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, klikt of tikt u op **[!UICONTROL New]** onderaan.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en klik of tik **[!UICONTROL Save]**.
