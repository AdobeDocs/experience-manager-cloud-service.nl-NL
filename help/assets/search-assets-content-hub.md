---
title: Middelen zoeken in Content Hub
description: Leer hoe u middelen kunt zoeken in [!DNL Content Hub]
role: User
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---


# Assets zoeken in [!DNL Content Hub] {#search-assets}

![Bannerafbeelding voor delen](assets/search.png)

Als u een groot aantal middelen in uw opslagplaats hebt, is het tijdrovend om naar het juiste middel te zoeken. [!DNL The Content Hub] het onderzoek voorziet u van de capaciteit om de goedgekeurde activa te zoeken zodat u extra acties op hen kunt uitvoeren, zoals downloaden, delen, of inzamelingen tot stand brengen. U kunt verschillende mogelijkheden gebruiken om uw zoekresultaten te beperken, zoals het uitvoeren van op tekst gebaseerde zoekopdrachten, het gebruik van filters, het uitvoeren van tags of een specifieke zoekopdracht met slimme tags, het zoeken naar een bepaalde bestandsindeling, enzovoort.

## Vereisten {#prerequisites}

[Content Hub-gebruikers](deploy-content-hub.md#onboard-content-hub-users) kan handelingen uitvoeren die in dit artikel worden genoemd.

## Wat u kunt zoeken  {#what-you-can-search}

De [!DNL Content Hub] zoekopdracht levert resultaten op basis van:

* **Overeenkomende tekst:** De [!DNL Content Hub] met een zoekopdracht kunt u zoeken naar een element op basis van de naam of beschrijving. U kunt op trefwoorden gebaseerde zoekopdrachten uitvoeren waarbij het trefwoord wordt vergeleken met de tekst die beschikbaar is in de eigenschappen van een element.

* **Overeenkomende context:** [!DNL Content Hub] de lijst met zoekresultaten bevat geschatte resultaten van elementen die u krijgt op basis van de overeenkomende context. Als u bijvoorbeeld `cool` in de zoekbalk, de elementen die betrekking hebben op `winter`, `snow`, `cold surroundings`in de zoeklijst.

* **Informatie over element (titel, tags of slimme tags):** [!DNL Content Hub] gebruikt een slim zoekalgoritme om zoekresultaten nauwkeurig en zo relevant mogelijk te rangschikken. [Metagegevens](#asset-properties.md) de verzameling van alle gegevens die beschikbaar zijn voor een actief, maar het mag niet noodzakelijk in dat actief zijn. [Het helpt u om elementen verder te categoriseren en is nuttig aangezien de hoeveelheid digitale informatie groeit](/help/assets/configure-content-hub-ui-options.md##configure-metadata-search-content-hub).

* **Datum van laatste wijziging:** De elementen die onlangs zijn gewijzigd, staan boven aan de lijst met zoekresultaten. U kunt het datumbereik naar wens filteren.

* **Gebruik:** De algemeen gebruikte elementen staan boven aan de zoeklijst.

* **Zoekgeschiedenis:** Klik in het zoekvak zonder een teken te typen voor de zoekgeschiedenis. U kunt ook een bepaald trefwoord uit de geschiedenis verwijderen. De zoekgeschiedenis wordt opgeslagen in het cachegeheugen van een webbrowser, wat betekent dat als u de [!DNL Content Hub] Als u in een andere browser of in een ander cachegeheugen van de browser zoekt, kunt u de zoekgeschiedenis niet meer weergeven.

* **Zoeken terwijl u typt:** De [!DNL Content Hub] zoekopdrachten verbeteren de zoekervaring door tijdens het typen automatisch aangevulde suggesties op te geven.

## Basiszoekopdracht {#basic-search}

Basiszoekopdracht uitvoeren op [!DNL the Content Hub], navigeert u naar de zoekbalk en geeft u het trefwoord op dat u wilt zoeken. Navigeer naar de filters die beschikbaar zijn in het linkervenster en pas deze toe om de zoekresultaten te beperken.

Zoek bijvoorbeeld naar alle **[!UICONTROL JPEG]** afbeeldingen met trefwoord `architect` in de richtlijn, die in het laatste jaar is gewijzigd. Voer de volgende stappen uit om dit scenario uit te voeren:

1. Opgeven `architect` als het zoekwoord.

1. Navigeren naar het deelvenster Filters > **[!UICONTROL Format]** > selecteren **[!UICONTROL JPEG]**.

1. Navigeren naar **[!UICONTROL Modified]** > geef het datumbereik op.

   ![Basiszoekopdracht](assets/basic-search.png)

## De zoekresultaten verfijnen met filters {#narrow-down-search-results}

Gebruik het deelvenster Filters om te zoeken naar elementen op basis van metagegevens. U kunt zoekresultaten filteren op basis van verschillende zoekvoorspelling. U kunt alle geschikte voorspelling selecteren om uw zoekresultaten te minimaliseren of te verkleinen. Wanneer u meerdere opties in een filter selecteert, geeft Content Hub de elementen weer die overeenkomen met een van de opties die in een filter zijn geselecteerd. Wanneer u echter meerdere opties voor meerdere filters selecteert, geeft Content Hub alleen de elementen weer die overeenkomen met alle opties die voor de verschillende filters zijn geselecteerd om de zoekresultaten te beperken.

De standaardfilters bevatten bestandsindeling, goedgekeurd op, datum van goedkeuring, verlopen en niet verlopen elementen en vervaldatum. Beheerders kunnen ook de filters configureren die in de lijst met filters worden weergegeven. Zie voor meer informatie [Content Hub-gebruikersinterface configureren](configure-content-hub-ui-options.md#configure-filters-content-hub).

<!--

<table>
    <tbody>
     <tr>
      <th><strong>Search Predicate</strong></th>
      <th><strong>Description</strong></th>
      <th><strong>Properties</strong></th>
     </tr>
     <tr>
      <td> Campaigns </td>
      <td> Allows you to search using planned activity performed to take any particular action. For example, advertisement campaign run on Ferrari to know the understand the interests of people using number of clicks people perform.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Channels </td>
      <td> Helps you to understand the path from where the asset is coming from. For example, web, social media, books, catalog, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Region </td>
      <td> Helps you to understand the location where the asset is created. For example, Japan, EMEA, Worldwide, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Keywords </td>
      <td> Keyword helps you search using terms or the words that you enter based on the topic. For example, images, low-resolution, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Timeframe </td>
      <td> Helps you search assets using timeline. For example, search by year 2024, Q3 2023, etc.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td>File format</td>
      <td>Composition of an asset. The supported assets include image, document, video, printable media, and so on.</td>
      <td>
        <ul>
            <li>[!UICONTROL JPEG]</li> 
            <li>[!UICONTROL Quicktime]</li> 
            <li>[!UICONTROL PNG]</li> 
            <li>[!UICONTROL WebP]</li> 
            <li>[!UICONTROL MP4]</li> 
            <li>[!UICONTROL Plain]</li> 
            <li>[!UICONTROL PDF]</li>
            <li>[!UICONTROL SVG + XML]</li>
        </ul>
      </td>
     </tr>
     <tr>
      <td>Tags</td>
      <td>Tags help you categorize assets that can be browsed and searched more efficiently based on hierarchical taxonomies.</td>
      <td>
        <ul>
            <li>Field label</li>
            <li>Property name</li>
            <li>Path</li>
            <li>Description</li>
        </ul>
      </td>
     </tr>
     <!--<tr>
      <td>Subject</td>
      <td>Classification of assets based on their theme. For example, colorful, hiking, outdoors.</td>
      <td>NA</td>
     </tr>
          <tr>
      <td>Last modified</td>
      <td>Search assets based on their last modification. Specify the date range using the Start date and End date fields.</td>
      <td>
        <ul>
            <li>Range text (From)</li> 
            <li>Range text (To) </li>
        </ul>
      </td>
     </tr>    
     <!--<tr>
      <td>Asset ID</td>
      <td>Unique number that identifies the asset.</td>
      <td>NA</td>
     </tr>
     <tr>
      <td> Colors </td>
      <td> Helps you search assets using colors that are automatically identified in an asset using Adobe's Sensei AI capabilities.</td>
      <td>NA</td>
     </tr>  
    </tbody>
   </table>

-->

## Doe meer met zoeken {#do-more-with-search}

[!DNL The Content Hub] is niet beperkt tot zoeken, maar stelt u in staat aanvullende handelingen uit te voeren, zoals [downloaden](download-assets-content-hub.md), [delen](share-assets-content-hub.md), en [elementen toevoegen aan verzameling](collections-content-hub.md), rechtstreeks vanuit de interface voor zoeken of voorvertonen. Selecteer de elementen op de pagina met zoekresultaten om deze opties weer te geven.
