---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van elementen in [!DNL Experience Manager Assets] Dit is een aantal manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
feature: Metadata
role: User,Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat bedrijven gecontroleerde en betrouwbare metagegevenswoordenboeken nodig hebben, [!DNL Experience Manager Assets] staat het toevoegen van nieuwe eigenschappen van metagegevens niet toe op aanvraag. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de interface Elementen en selecteer het **[!UICONTROL View Properties]** op de werkbalk.
   * Selecteer in de miniatuur van het element de optie **[!UICONTROL View Properties]** snelle actie.
   * Selecteer op de elementpagina de optie **[!UICONTROL View Properties]** op de werkbalk.

   Op de elementpagina worden de metagegevens van het element weergegeven. Deze metagegevens worden automatisch geëxtraheerd bij het uploaden (invoegen) naar Experience Manager Assets.

1. Breng desgewenst wijzigingen aan in de metagegevens op de verschillende tabbladen en selecteer vervolgens, wanneer u klaar bent, **[!UICONTROL Save]** van de toolbar om uw veranderingen te bewaren. Selecteren **[!UICONTROL Close]** om terug te keren naar de middelenwebinterface.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om de eigenschap metadata toe te voegen.

Eventuele wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP gegevens. Dit gebeurt via de workflow voor het terugschrijven van metagegevens van Experience Managers. Wijzigingen in bestaande eigenschappen (zoals `dc:title`) worden overschreven en nieuwe eigenschappen gemaakt (inclusief aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Metagegevensschema bewerken {#editing-metadata-schema}

Voor meer informatie over het bewerken van het metagegevensschema raadpleegt u [Formulieren met metagegevensschema bewerken](metadata-schemas.md#edit-metadata-schema-forms).

## Een aangepaste naamruimte registreren in de Experience Manager {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten in de Experience Manager toevoegen. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Naar de beheerpagina voor knooppunttypen *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Selecteren **[!UICONTROL Namespaces]** boven aan de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, selecteert u **[!UICONTROL New]** onderaan.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en selecteer **[!UICONTROL Save]**.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
