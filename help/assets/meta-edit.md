---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van elementen in [!DNL Experience Manager Assets] Dit is een aantal manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: 4be76f19c27aeab84de388106a440434a99a738c
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 8%

---

# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat bedrijven gecontroleerde en betrouwbare metagegevenswoordenboeken nodig hebben, [!DNL Experience Manager Assets] is het niet mogelijk om ad-hoc nieuwe eigenschappen van metagegevens toe te voegen. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de interface Elementen en klik op het element **[!UICONTROL View Properties]** op de werkbalk.
   * Selecteer in de miniatuur van het element de optie **[!UICONTROL View Properties]** snelle actie.
   * Klik/tik op de elementpagina **[!UICONTROL View Properties]** op de werkbalk.

   Op de elementpagina worden alle metagegevens van het element weergegeven. Deze metagegevens worden automatisch geëxtraheerd bij het uploaden (invoegen) naar Experience Manager Assets.

1. Bewerk desgewenst de metadata op de verschillende tabbladen en klik of tik wanneer u klaar bent op **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan. Klik of tik op **[!UICONTROL Close]** om terug te keren naar de webinterface voor assets.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Eventuele wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP gegevens. Dit gebeurt via de workflow voor het terugschrijven van metagegevens van Experience Managers. Wijzigingen in bestaande eigenschappen (zoals `dc:title`) worden overschreven en nieuwe eigenschappen gemaakt (inclusief aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Metagegevensschema bewerken {#editing-metadata-schema}

Voor meer informatie over het bewerken van het metagegevensschema raadpleegt u [Formulieren met metagegevensschema bewerken](metadata-schemas.md#edit-metadata-schema-forms).

## Een aangepaste naamruimte registreren in de Experience Manager {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten in de Experience Manager toevoegen. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Naar de beheerpagina voor knooppunttypen *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Klikken of tikken **[!UICONTROL Namespaces]** boven aan de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, klikt u of tikt u op **[!UICONTROL New]** onderaan.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en klik of tik **[!UICONTROL Save]**.
