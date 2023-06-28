---
title: Middelen zoeken en ontdekken in [!DNL Assets view]
description: Middelen zoeken en ontdekken in [!DNL Assets view].
role: User
exl-id: be9597a3-056c-436c-a09e-15a03567c85a
source-git-commit: ed7ce8be17ad1445132b9aa38a0efa84ffa70fdf
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Middelen zoeken in [!DNL Assets view] {#search-assets}

>[!CONTEXTUALHELP]
>id="assets_search"
>title="Zoeken in middelen"
>abstract="Zoek naar activa door een sleutelwoord in de bar van het Onderzoek te specificeren of door activa te filtreren die op hun status, dossiertype, MIME type, grootte, verwezenlijking, wijziging, en vervaldata worden gebaseerd. Naast de standaardfilters kunt u ook aangepaste filters toepassen. U kunt de gefilterde resultaten opslaan als een opgeslagen zoekopdracht of als een slimme verzameling."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-assets-essentials/help/manage-collections.html?lang=en#manage-smart-collection" text="Slimme verzamelingen maken"

[!DNL Assets view] biedt effectief zoeken, dat werkt standaard. De zoekopdracht is uitgebreid omdat er in volledige tekst wordt gezocht. Met de krachtige zoekfunctionaliteit kunt u snel de juiste middelen vinden en de snelheid van de inhoud verbeteren. [!DNL Assets view] biedt zoekopdrachten in volledige tekst en zoekopdrachten via metagegevens, zoals slimme tags, titel, gemaakte datum en copyright.

Als u elementen wilt zoeken,

* Klik in het zoekvak boven aan de pagina. Standaard wordt gezocht in de map waarin u momenteel bladert. Voer een van de volgende handelingen uit:

  ![zoekvak](assets/search-box.png)

   * Zoeken met een trefwoord en desgewenst map wijzigen. Druk op Return.

   * Begin met werken met een onlangs weergegeven element door er direct naar te zoeken. Klik in het zoekvak en selecteer een element dat onlangs is weergegeven in de suggesties.

## De zoekresultaten filteren {#refine-search-results}

U kunt de zoekresultaten filteren op basis van de volgende parameters.

![Zoekfilters](assets/filters1.png)

*Afbeelding: Gezochte elementen filteren op basis van verschillende parameters.*

* Status van element: De zoekresultaten filteren met een `Approved`, `Rejected`, of `No Status` status van het element.

* Bestandstype: Filter de zoekresultaten op de ondersteunde bestandstypen, namelijk `Images`, `Documents`, en `Videos`.
* MIME-type: Filter voor een of meer ondersteunde bestandsindelingen. <!-- TBD:  [supported file formats](/help/assets/supported-file-formats-assets-view.md). -->
* Afbeeldingsgrootte: Geef een van de minimale en maximale afmetingen op voor het filteren van afbeeldingen. De grootte wordt opgegeven in pixelafmetingen en is niet de bestandsgrootte van de afbeeldingen.
* Gemaakt op: De aanmaakdatum van het element, zoals vermeld in de metagegevens. De standaard datumnotatie die wordt gebruikt is `yyyy-mm-dd`.
* Datum gewijzigd: De laatste gewijzigde datum van de elementen. De standaard datumnotatie die wordt gebruikt is `yyyy-mm-dd`.

* Vervaldatum: De zoekresultaten filteren op basis van een `Expired` status van het element. Daarnaast kunt u een datumbereik voor de vervaldatum voor elementen opgeven om de zoekresultaten verder te filteren.

* Aangepaste filters: [Aangepaste filters toevoegen](#custom-filters) aan de gebruikersinterface van de middelenweergave. Pas de aangepaste filters toe naast de standaardfilters om de zoekresultaten te verfijnen.

U kunt de gezochte middelen in stijgende of dalende orde van sorteren `Name`, `Relevancy`, `Size`, `Modified`, en `Created`.

## Aangepaste filters beheren {#custom-filters}

**Vereiste machtigingen:**  `Can Edit`, `Owner`of Beheerder.

In de weergave Elementen kunt u ook aangepaste filters toevoegen aan de gebruikersinterface. Vervolgens kunt u deze aangepaste filters toepassen naast de [standaardfilters](#refine-search-results) om de zoekresultaten te verfijnen.

De middelenweergave biedt de volgende aangepaste filters:

<table>
    <tbody>
     <tr>
      <th><strong>Aangepaste filternaam</strong></th>
      <th><strong>Beschrijving</strong></th>
     </tr>
     <tr>
      <td>Titel</td>
      <td>Filter elementen met de titel van het element. De titel die u opgeeft in de hoofdlettergevoelige zoekcriteria moet overeenkomen met de exacte titel van het element om in de resultaten te worden weergegeven.</td>
     </tr>
     <tr>
      <td>Naam</td>
      <td>Filter elementen met de naam van het elementbestand. De naam die u opgeeft in de hoofdlettergevoelige zoekcriteria moet overeenkomen met de exacte bestandsnaam van het element om in de resultaten te worden weergegeven.</td>
     </tr>
     <tr>
      <td>Elementgrootte</td>
      <td>Filter elementen door een formaatbereik in bytes te definiëren in de zoekcriteria voor een element dat in de resultaten moet worden weergegeven.</td>
     </tr>
     <tr>
      <td>Vooraf gedefinieerde labels</td>
      <td>Filter elementen met de slimme tag voor elementen. De naam van de slimme tag die u opgeeft in de hoofdlettergevoelige zoekcriteria, moet overeenkomen met de exacte naam van de slimme tag van het element om in de resultaten te worden weergegeven. U kunt niet meerdere slimme tags opgeven in zoekcriteria.</td>
     </tr>    
    </tbody>
   </table>

<!--
   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. For example, if you define <b>ma*</b> as the search criteria, Assets view displays assets with title, such as, market, marketing, man, manchester, and so on in the results.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria.

   You can use a wildcard operator (*) to enable Assets view to display assets in the results that partially match the search criteria. You can specify multiple smart tags separated by a comma in the search criteria.

   -->

### Aangepaste filters toevoegen {#add-custom-filters}

Aangepaste filters toevoegen:

1. Klik op **[!UICONTROL Filters]**.

1. In de **[!UICONTROL Custom Filters]** sectie, klikt u op **[!UICONTROL Edit]** of **[!UICONTROL Add Filters]**.

   ![Aangepaste filters toevoegen](assets/add-custom-filters.png)

1. Op de **[!UICONTROL Custom filters management]** selecteert u de filters die u aan de bestaande lijst met filters wilt toevoegen. Selecteren **[!UICONTROL Custom Filters]** om alle filters te selecteren.

1. Klikken **[!UICONTROL Confirm]** om de filters aan de gebruikersinterface toe te voegen.

### Aangepaste filters verwijderen {#remove-custom-filters}

Aangepaste filters verwijderen:

1. Klik op **[!UICONTROL Filters]**.

1. In de **[!UICONTROL Custom Filters]** sectie, klikt u op **[!UICONTROL Edit]**.

1. Op de **[!UICONTROL Custom filters management]** schakelt u de filters uit die u uit de bestaande lijst met filters wilt verwijderen.

1. Klikken **[!UICONTROL Confirm]** om de filters uit de gebruikersinterface te verwijderen.


## Opgeslagen zoekopdrachten {#saved-search}

Zoekfuncties zijn heel eenvoudig in [!DNL Assets view]. Vanuit het zoekvak kunt u niet alleen een trefwoord typen en op Enter drukken om de resultaten weer te geven, maar u kunt ook snel met één klik nogmaals zoeken naar de laatst doorzochte trefwoorden.

U kunt de zoekresultaten ook filteren op basis van specifieke criteria voor metagegevens en het type element. Voor veelgebruikte filters om de zoekervaring te verbeteren, [!DNL Assets view] Hiermee kunt u de zoekparameters opslaan. Vervolgens kunt u de opgeslagen zoekopdracht selecteren en het filter toepassen met één klik.

Als u een opgeslagen zoekopdracht wilt maken, zoekt u naar een element, past u een of meer filters toe en klikt u op **[!UICONTROL Save as]** > **[!UICONTROL Saved Search]** in de [!UICONTROL Filters] deelvenster. U kunt ook op **[!UICONTROL Save as]** en selecteert u **[!UICONTROL Smart Collection]** om de resultaten op te slaan als een slimme verzameling. Zie [Een slimme verzameling maken](manage-collections-assets-view.md#create-a-smart-collection) voor meer informatie .

![Slimme verzameling maken](assets/create-smart-collection.png)

<!-- TBD: Search behavior. Full-text search. Ranking and rank boosts. Hidden assets.
Report poor UX that users can only save a filtered search and not a simple search.
.
Are other supported files fully indexed and support full-text search? Eg. audio/videos files can at best have metadata indexed.
Anything about ranking of assets displayed in search results?

What about temporarily hiding an asset (suspending search on it) from the search results? If an asset is undergoing review collaboration, should it be used by others? Should it be hidden in search?

When userA is searching and userB add an asset that matches search results, will the asset display in search as soon as userA refreshes the page? Assuming indexing is near real-time. May not be so for bulk uploads.
-->

## Volgende stappen {#next-steps}

* [Een video bekijken om elementen te zoeken in de weergave Middelen](https://experienceleague.adobe.com/docs/experience-manager-learn/assets-essentials/basics/using.html)

* Feedback geven op het product met de [!UICONTROL Feedback] optie beschikbaar in de gebruikersinterface van de weergave Elementen

* Documentfeedback geven met [!UICONTROL Edit this page] ![de pagina bewerken](assets/do-not-localize/edit-page.png) of [!UICONTROL Log an issue] ![een GitHub-probleem maken](assets/do-not-localize/github-issue.png) beschikbaar op de rechterzijbalk

* Contact [Klantenservice](https://experienceleague.adobe.com/?support-solution=General#support)
