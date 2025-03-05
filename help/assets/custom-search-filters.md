---
title: Aangepaste zoekfilters
description: Meer informatie over het aanpassen van het formulier met zoekfilters
role: User, Leader, Developer
exl-id: 383e8165-439e-447b-a19d-d5446238a13f
source-git-commit: 0484b8ac158f0590d5ada7536cf8b547c71ab686
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 2%

---

# Zoekfilters aanpassen {#customize-search-filters}

Met zoekfilters kunt u de zoekresultaten verfijnen op basis van verschillende parameters, zoals datum, bestandstype, tags en relevantie. Hierdoor wordt de zoekopdracht nauwkeuriger. Door filters toe te passen, kunt u snel de meest relevante resultaten efficiënt overslaan. Dit bespaart niet alleen tijd, maar verbetert ook de algemene zoekervaring door de resultaten af te stemmen op specifieke voorkeuren en behoeften.
Zie meer over [ onderzoek ](search-assets-view.md).

Aangepaste zoekfilters kunnen alleen worden toegewezen aan items in de index van doorzoekbare eigenschappen. Zorg ervoor dat alle aangepaste metagegevens zijn opgenomen voordat u uw aangepaste filterervaring configureert. Met [!DNL Assets view] kunt u zoekfilters aanpassen om het zoekproces te stroomlijnen. Voer de volgende stappen uit om de sjabloon van zoekfilters aan te passen:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL General Settings]**.
1. Ga naar de tab **[!UICONTROL Search]** . Klik op **[!UICONTROL Customize]** om het zoekformulier te configureren.

   ![ de montages van de douanefilter van het douaneonderzoek ](assets/custom-search-filter.png)

1. Het [!UICONTROL Configure Filters] -formulier wordt weergegeven. Zorg ervoor dat u in de bewerkingsmodus werkt, zodat u wijzigingen in de sjabloon kunt aanbrengen. U kunt overschakelen op [!UICONTROL Preview mode] om een voorbeeld van een bestaand zoekformulier te bekijken.
1. De filterelementen van de daling van de [ douanefilters ](#available-custom-filters) op het canvas. U kunt de component slepen en neerzetten om deze indien nodig opnieuw te rangschikken.

   >[!VIDEO](https://video.tv.adobe.com/v/3443080)

1. Klik op **[!UICONTROL Preview mode]** om de wijzigingen te bekijken.
1. Klik op **[!UICONTROL Confirm]** om op te slaan.

## Beschikbare aangepaste filters {#available-custom-filters}

De weergave van Assets biedt de volgende aangepaste filters die opnieuw kunnen worden geconfigureerd volgens de vereisten:

* [Elementen filteren](#filter-elements)
* [Vooraf geconfigureerde filters](#preconfigured-filters)

### Elementen filteren {#filter-elements}

U kunt een verzameling filterelementen op het canvas met aangepaste zoekfilters gebruiken. Deze elementen kunnen opnieuw worden geconfigureerd op basis van de bruikbaarheid van kenmerken van zoekeigenschappen. Nochtans, kunt u de [ filtereigenschappen ](#filter-properties) zoals per uw vereisten aanpassen. De volgende filterelementen zijn beschikbaar in [!DNL Assets view] :

<table>
    <tr>
        <th>Elementen filteren</th>
        <th>Beschrijving</th>
        <th>Eigenschappen</th>
    </tr>
    <tr>
        <td>Tekst</td>
        <td>Een tekstveld is een invoergebied waarin u informatie met betrekking tot het filter kunt typen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Waarden
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Opties</td>
        <td>De opties verwijzen naar de beschikbare alternatieven om een aangewezen punt van een lijst te selecteren.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Waarden
                <li>Opties
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Boolean</td>
        <td>Een Booleaanse waarde vertegenwoordigt één werkelijke waarde. U kunt de optie gebruiken wanneer u een van de opties specifiek wilt kiezen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Getal</td>
        <td>Gebruik dit filterelement om een numerieke waarde te vertegenwoordigen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Stepper
                <li>Stepperwaarde
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Vervolgkeuzelijst</td>
        <td>U kunt kiezen uit de verschillende opties die in een lijst met opties worden weergegeven.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Opties
                <li>Waarden
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Datum</td>
        <td>Wordt gebruikt om de datum op te geven.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Padbrowser</td>
        <td>Wordt gebruikt om door bestanden of mappen in de Experience Manager-opslagplaats te navigeren.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Padverkenner
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Tags</td>
        <td>Hiermee selecteert u tags uit de beschikbare opties. Tags bieden specifiekere informatie over de elementen en verbeteren de ontdekkingsmogelijkheden ervan. De markeringen die reeds op de geselecteerde activa worden toegepast tonen in het <b> paneel van Eigenschappen </b>. Als u tags opslaat op een aangepaste eigenschap voor metagegevens en het hoofdpad gebruikt om deze te beperken tot een hiërarchie, kunt u dezelfde configuratie gebruiken in uw zoekfilters. Als u de relevante tags niet kunt vinden, maakt u deze en wijst u ze toe aan de geselecteerde elementen. Zie <a href = "tagging-management-assets-view.md"> Tags beheren in de Assets-weergave </a> voor meer informatie over het maken en toewijzen van tags aan elementen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Tagkiezer
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Gebruiker</td>
        <td>Wordt gebruikt om het type gebruiker op te geven onder beheerders, gewone gebruikers en consumenten.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Beschrijving
            </ul>
        </td>
    </tr>
</table>

### Vooraf geconfigureerde filters {#preconfigured-filters}

De vooraf geconfigureerde filters zijn vooraf ingestelde instellingen waarmee u ze rechtstreeks op het canvas kunt gebruiken. Nochtans, kunt u de [ filtereigenschappen ](#filter-properties) zoals per uw vereisten aanpassen. De volgende filters zijn vooraf geconfigureerd in [!DNL Assets view] :

<table>
    <tr>
        <th>Vooraf geconfigureerde filters</th>
        <th>Beschrijving</th>
        <th>Eigenschappen</th>
    </tr>
    <tr>
        <td>Bestandstype</td>
        <td>Filter de zoekresultaten op de ondersteunde bestandstypen: "Afbeeldingen", "Documenten" en "Video's".</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Opties
                <li>Waarden
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Bestandsindeling</td>
        <td>De Assets-weergave ondersteunt elke binaire bestandsindeling met basisservices, zoals opslag, uploaden, kopiëren, verplaatsen, verwijderen en toevoegen van metagegevens.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Afbeeldingsgrootte</td>
        <td>Geef een van de minimale en maximale afmetingen op voor het filteren van afbeeldingen. De grootte wordt opgegeven in pixelafmetingen en is niet de bestandsgrootte van de afbeeldingen.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Stepper
                <li>Stepperwaarde
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Breedte afbeelding</td>
        <td>Verticale afmetingen van een afbeelding.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Stepper
                <li>Stepperwaarde
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Hoogte afbeelding</td>
        <td>Horizontale afmetingen van een afbeelding.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Stepper
                <li>Stepperwaarde
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Aanmaakdatum</td>
        <td>Datumbereik waarin elementen zijn gemaakt.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Datum gewijzigd</td>
        <td>Datumbereik waarin elementen zijn gewijzigd.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Status van activa</td>
        <td>Met de Assets-weergave kunt u de status instellen voor de middelen die in de repository beschikbaar zijn. Stel een elementstatus in om het downstreamgebruik van digitale elementen beter te beheren en te beheren. Kies onder <b> Goedgekeurd, Verworpen, of Geen Status </b>.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Slimme tags</td>
        <td>Filter elementen met behulp van slimme tags die zijn toegevoegd aan de Experience Manager-opslagplaats.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Delimeter-ondersteuning
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Dynamische mediastatus</td>
        <td>Kies de status van een element tussen gepubliceerd of niet gepubliceerd.</td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Opties
                <li>Waarden
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Vervaldatum</td>
        <td>Filter elementen die een datumbereik opgeven waarna de elementen niet langer geldig of nodig zijn. </td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Type selectie
                <li>Beschrijving
            </ul>
        </td>
    </tr>
    <tr>
        <td>Labels (Taxonomy)</td>
        <td>Het is een systeem om digitale activa te organiseren en te classificeren die markeringen gebruiken, hoofdzakelijk creërend een hiërarchische structuur van sleutelwoorden die gebruikers toestaat om relevante inhoud gemakkelijk te zoeken en te vinden door specifieke markeringen op elk middel toe te passen, </td>
        <td>
            <ul>
                <li>Label
                <li>Metagegevens
                <li>Tagkiezer
                <li>Beschrijving
            </ul>
        </td>
    </tr>
</table>

#### Filtereigenschappen {#filter-properties}

Elk filterelement is gekoppeld aan een set eigenschappen. De volgende eigenschappen worden gebruikt in het filter en vooraf geconfigureerde elementen:

<table>
    <tr>
        <th>Eigenschappen</th>
        <th>Waarden</th>
        <th>Beschrijving</th>
    </tr>
    <tr>
        <td>Label</td>
        <td>Tekst</td>
        <td>Het is een id van het filter dat u gebruikt.</td>
    </tr>
    <tr>
        <td>Metagegevens</td>
        <td>Vervolgkeuzelijst</td>
        <td>De eigenschap metadata wordt gebruikt om goedgekeurde metagegevens uit de Adobe Experience Manager Assets-opslagplaats toe te wijzen. U kunt de metagegevenswaarde kiezen in het keuzemenu dat moet worden toegewezen aan het filterelement. </td>
    </tr>
    <tr>
        <td>Type selectie</td> 
        <td>Enkel, Veelvoudig, Exact, of Waaier </td>
        <td>
            <ul>
                <li><b> Enige selectie </b> staat het kiezen van één punt bij me toe, dat voor verschillende keuzen ideaal is.
                <li><b> Veelvoudige selectie </b> staat het kiezen van verscheidene punten toe gelijktijdig, die nuttig is om veelvoudige opties te selecteren. 
                <li><b> Exacte selectie </b> staat het kiezen van een nauwkeurig enkel punt van diverse opties toe.
                <li><b> selectie van de Waaier </b> staat het kiezen van een ononderbroken reeks waarden binnen een bepaalde waaier toe, nuttig om een waaier van data of numerieke waarden te selecteren.
            </ul>
        </td>   
    </tr>
    <tr>
        <td>Opties</td>
        <td>Handmatig, JSON-pad of CSV-upload</td>
        <td>
            <ul>
                <li>Kies <b> Handboek </b> als u opties manueel wilt toevoegen. 
                <li>Kies <b> Weg JSON </b> om opties van het JSON dossier toe te voegen. 
                <li>Kies <b> CSV uploadt </b> om een Csv- dossier in te voeren dat waarden bevat die in de opties moeten worden toegevoegd.
            </ul>
        </td>
    </tr>
    <tr>
       <td>Waarden</td>
        <td>Toevoegen of bewerken</td>
        <td>
        <ul>
        <li>Klik <b> toevoegen </b> om een nieuwe waarde toe te voegen. 
        <li>Klik op <span> ✎ </span> om het label te bewerken. 
        <li>Klik <span>? </span> om de optiewaarde te schrappen. 
        <li>Klik <b> uitgeven </b> om de uit te geven opties te wijzigen. 
        <li>U kunt de volgorde van opties ook wijzigen door ze ingedrukt te houden.
        </td>
    </tr>
    <tr>
        <td>Delimeter-ondersteuning</td>
        <td>In- of uitschakelen</td>
        <td>Een scheidingsteken is een symbool dat wordt gebruikt om afzonderlijke elementen in tekst te scheiden. Bijvoorbeeld komma's, spaties of puntkomma's.</td>
    </tr>
    <tr>
        <td>Stepper</td>
        <td>Waarde</td>
        <td>Schakel de knop Stapsgewijs in op het nummerveld om de waarde bij elke klik te verhogen of te verlagen. </td>
    </tr>
    <tr>
        <td>Stepperwaarde </td>
        <td>Getal</td>
        <td>De waarde voor verhogen/verlagen wordt aangegeven wanneer de stapsgewijze knop wordt gebruikt. De optie wordt weergegeven wanneer de stapfunctie is ingeschakeld.</td>
    </tr>
    <tr>
        <td>Beschrijving</td>
        <td>Tekst</td>
        <td>Voeg een gedetailleerde uitleg toe voor aanvullende informatie over het filterelement.</td>
    </tr>
</table>


## Een filterelement verwijderen {#delete-a-filter-element}

Ga als volgt te werk om een zoekfilter te verwijderen:

1. Ga naar **[!UICONTROL Settings]** > **[!UICONTROL General Settings]**.
1. Ga naar de tab **[!UICONTROL Search]** . Klik op **[!UICONTROL Customize]** om het zoekformulier te configureren.
1. Het [!UICONTROL Configure Filters] -formulier wordt weergegeven. Zorg ervoor dat u in de bewerkingsmodus werkt, zodat u wijzigingen in de sjabloon kunt aanbrengen.
1. Selecteer het filterelement dat u wilt verwijderen. Selecteer bijvoorbeeld **[!UICONTROL Image height]** .
1. Klik op **[!UICONTROL Delete Category]** om het filterelement te verwijderen. Het element **[!UICONTROL Image height]** wordt verwijderd van het canvas.
1. Klik op **[!UICONTROL Confirm]** om het formulier op te slaan.

## Aangepaste zoekfilters gebruiken{#using-custom-search-filters}

Nadat u de zoekfilters hebt geconfigureerd, kunt u deze gebruiken om te zoeken naar elementen in de opslagplaats.

![ Gebruikend de filters van het douaneonderzoek ](assets/using-custom-search-filters.png)

>[!MORELIKETHIS]
>
>* [Assets doorzoeken](search-assets-view.md)
