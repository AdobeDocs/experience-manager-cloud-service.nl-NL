---
title: Metagegevens bewerken of toevoegen
description: Leer over activa meta-gegevens in  [!DNL Experience Manager Assets]  en diverse manieren waardoor u activa meta-gegevens kunt uitgeven.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 464a97ce-da3e-47b5-9879-fafaf2f2378c
source-git-commit: 188f60887a1904fbe4c69f644f6751ca7c9f1cc3
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat bedrijven gecontroleerde en betrouwbare taalwoordenboeken voor metagegevens nodig hebben, staat [!DNL Experience Manager Assets] niet toe dat op aanvraag nieuwe eigenschappen voor metagegevens worden toegevoegd. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [ Creërend Nieuw Bezit van Meta-gegevens voor Assets ](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de gebruikersinterface van Assets en selecteer het pictogram **[!UICONTROL View Properties]** op de werkbalk.
   * Selecteer in de miniatuur van het element de handeling **[!UICONTROL View Properties]** quick.
   * Selecteer in de elementpagina de optie **[!UICONTROL View Properties]** op de werkbalk.

   Op de elementpagina worden de metagegevens van het element weergegeven. Deze metagegevens worden automatisch geëxtraheerd bij het uploaden (invoegen) naar Experience Manager Assets.

1. Breng desgewenst wijzigingen aan in de metagegevens op de verschillende tabbladen en selecteer **[!UICONTROL Save]** op de werkbalk als u de wijzigingen hebt voltooid. Selecteer **[!UICONTROL Close]** om terug te keren naar de Assets-webinterface.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om de eigenschap metadata toe te voegen.

Eventuele wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. Dit gebeurt via de terugschrijfworkflow voor Experience Manager-metagegevens. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title` ), worden overschreven en gemaakte eigenschappen (zoals aangepaste eigenschappen zoals `cq:tags` ) worden samen met het schema toegevoegd.

<!-- XMP write-back is supported and enabled for the platforms and file formats described in technical requirements. -->

## Metagegevensschema bewerken {#editing-metadata-schema}

Voor details op hoe te om meta-gegevensschema uit te geven, zie [ het Uitgeven van de vormen van het meta-gegevensschema ](metadata-schemas.md#edit-metadata-schema-forms).

## Een aangepaste naamruimte registreren in Experience Manager {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen in Experience Manager. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Ga naar de knooptype beleidspagina *https://&lt;host>:&lt;port>/crx/explorer/nodetypes/index.jsp*.
1. Selecteer **[!UICONTROL Namespaces]** boven aan de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, selecteert u **[!UICONTROL New]** onderaan.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en selecteer **[!UICONTROL Save]** .

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
