---
title: Facetten doorzoeken.
description: In dit artikel wordt beschreven hoe u zoekfacetten in AEM kunt maken, wijzigen en gebruiken.
translation-type: tm+mt
source-git-commit: bd02261e62de28860c6c95794cd69e6529240b6d
workflow-type: tm+mt
source-wordcount: '2263'
ht-degree: 18%

---


# Facetten doorzoeken {#search-facets}

Een bedrijfsbrede implementatie van Adobe Experience Manager (AEM) Assets heeft de capaciteit om vele activa op te slaan. Soms kan het lastig en tijdrovend zijn om het juiste middel te vinden als u alleen de algemene zoekmogelijkheden van AEM gebruikt.

Gebruik zoekfacetten in het deelvenster Filters om de zoekervaring gedetailleerder te maken en de zoekfunctionaliteit efficiënter en veelzijdiger te maken. De facetten van het onderzoek voegen veelvoudige afmetingen (predikaten) toe die u toelaten om complexere onderzoeken uit te voeren. Het deelvenster Filters bevat een aantal standaardfacetten. U kunt ook aangepaste zoekfacetten toevoegen.

Samengevat kunt u met zoekfacetten op verschillende manieren naar elementen zoeken in plaats van in één, vooraf bepaalde, taxonomische volgorde. U kunt gemakkelijk tot het gewenste niveau van detail voor een gerichter onderzoek boor.

Als u bijvoorbeeld een afbeelding zoekt, kunt u kiezen of u een bitmap- of een vectorafbeelding wilt. U kunt het zoekbereik verder verkleinen door het MIME-type voor de afbeelding op te geven. Op dezelfde manier kunt u bij het zoeken naar documenten de indeling opgeven, bijvoorbeeld PDF of MS Word.

## Een voorspelling {#adding-a-predicate} toevoegen

De zoekfacetten die in het deelvenster Filters worden weergegeven, worden in het onderliggende zoekformulier gedefinieerd aan de hand van voorspelden. Als u meer of verschillende facetten wilt weergeven, voegt u voorspelingen toe aan het standaardformulier of gebruikt u een aangepast formulier dat naar keuze facetten bevat.

Voor full-text onderzoeken, voeg `Fulltext` voorspellen aan de vorm toe. Gebruik de voorspelling van de eigenschap om te zoeken naar elementen die overeenkomen met één eigenschap die u opgeeft. Gebruik de voorspelling Opties om te zoeken in elementen die overeenkomen met een of meer waarden voor een bepaalde eigenschap. Voeg de Datumbereik-voorspelling toe aan zoekelementen die binnen een opgegeven datumbereik zijn gemaakt.

1. Klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de pagina Zoeken in Forms en tik vervolgens op **Bewerken** ![aemassets_edit](assets/aemassets_edit.png).

   ![Zoek en selecteer de middelen die Admin Search Rail](assets/assets_admin_searchrail.png)

1. Sleep op de pagina Zoeken in Forms bewerken een voorspelling van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster. Sleep bijvoorbeeld **[!UICONTROL Property Predicate]**.

   ![Een voorspelling selecteren en verplaatsen om de zoekfilters aan te passen](assets/drag_predicate.png)

   *Afbeelding: Selecteer en verplaats een voorspelling om de zoekfilters aan te passen.*

1. Voer op het tabblad Instellingen een veldlabel, plaatsaanduidingstekst en beschrijving voor de voorspelling in. Geef een geldige naam op voor de eigenschap metadata die u aan de voorspelling wilt koppelen. Het koptekstlabel op het tabblad Instellingen geeft het type van de geselecteerde voorspelling aan.

   ![Gebruik het tabblad Instellingen om de vereiste opties voor een voorspelling op te geven](assets/settings.png)

   *Afbeelding: Gebruik het lusje van Montages om de vereiste opties van een predikaat te verstrekken.*

1. Geef in het veld **[!UICONTROL Property Name]** een geldige naam op voor de metadata-eigenschap die u aan het predicaat wilt koppelen. Dit is de naam op basis waarvan de zoekopdracht wordt uitgevoerd. Voer bijvoorbeeld `jcr:content/metadata/dc:description` of `./jcr:content/metadata/dc:description` in. U kunt ook een bestaand knooppunt selecteren in het dialoogvenster Selecteren.

   ![Een metagegevenseigenschap koppelen aan een voorspelling in het veld Eigenschapnaam](assets/property_settings.png)

   *Afbeelding: Koppel een eigenschap metadata aan een voorspelling in het veld Eigenschapnaam.*

1. Klik **[!UICONTROL Preview]** ![voorproef](assets/preview.png) om een voorproef van het paneel van Filters te produceren aangezien het verschijnt nadat u het predikaat toevoegt.
1. Bekijk de lay-out van de voorspelling in de modus Voorbeeld.

   ![Voorbeeld van het zoekformulier bekijken voordat de wijzigingen worden verzonden](assets/preview-1.png)

   Voorbeeld van het zoekformulier bekijken voordat de wijzigingen worden verzonden

1. Als u de voorvertoning wilt sluiten, klikt u op **[!UICONTROL Close]** ![close](assets/do-not-localize/close_icon.png) in de rechterbovenhoek van de voorvertoning.
1. Tik op **[!UICONTROL Done]** om de instellingen op te slaan.
1. Navigeer naar het deelvenster Zoeken in de gebruikersinterface Elementen. De voorspelling van de eigenschap wordt toegevoegd aan het deelvenster.
1. Voer in het tekstvak een beschrijving in voor het element dat u wilt doorzoeken. Voer bijvoorbeeld &quot;Adobe&quot; in. Wanneer u een zoekopdracht uitvoert, worden elementen met een beschrijving die overeenkomt met &quot;Adobe&quot;, weergegeven in de zoekresultaten.

## Een voorspelling van opties toevoegen {#adding-an-options-predicate}

Met de voorspelling Opties kunt u meerdere zoekopties toevoegen in het deelvenster Filters. U kunt een of meer van deze opties selecteren in het deelvenster Filters om te zoeken naar elementen. Als u bijvoorbeeld naar elementen wilt zoeken op basis van het bestandstype, configureert u opties, zoals Afbeeldingen, Multimedia, Documenten en Archieven, in het zoekformulier. Nadat u deze opties hebt geconfigureerd, wordt de zoekopdracht uitgevoerd op elementen van het type GIF, JPEG, PNG, enzovoort, wanneer u de optie Afbeeldingen selecteert in het deelvenster Filters.

Als u de opties wilt toewijzen aan de desbetreffende eigenschap, maakt u een knooppuntstructuur voor de opties en geeft u het pad van het bovenliggende knooppunt op in de eigenschap Eigenschapnaam van de voorspelling van opties. Het bovenliggende knooppunt moet van het type `sling` zijn: `OrderedFolder`. De opties moeten van het type `nt:unstructured` zijn. De optieknooppunten moeten de eigenschappen `jcr:title` en `value` hebben gevormd.

De eigenschap `jcr:title` is een gebruiksvriendelijke naam voor de optie die wordt weergegeven in het deelvenster Filters. Het veld `value` wordt gebruikt in de query om overeen te komen met de opgegeven eigenschap.

Wanneer u een optie selecteert, wordt het onderzoek uitgevoerd gebaseerd op het `value` bezit van de optieknoop en zijn kindknopen, als om het even welk. De volledige boom onder de optieknoop wordt getransformeerd en het `value` bezit van elke kindknoop wordt gecombineerd gebruikend OF verrichting om de onderzoeksvraag te vormen.

Als u bijvoorbeeld &quot;Afbeeldingen&quot; selecteert voor bestandstypen, wordt de zoekquery voor de assets samengesteld door de eigenschap `value` te combineren met een OR-bewerking. De zoekquery voor afbeeldingen wordt bijvoorbeeld samengesteld door de resultaten te combineren die overeenkomen met *afbeelding/jpeg*, *afbeelding/gif*, *afbeelding/png*, *afbeelding/pjpeg* en *afbeelding/tiff* voor de eigenschap `jcr:content/metadata/dc:format` met behulp van een OR-bewerking.

Het bezit van de waarde van een dossiertype, zoals die in CRXDE wordt gezien wordt gebruikt voor onderzoeksvragen om te werken

In plaats van handmatig een knooppuntstructuur voor de opties in de CRX-opslagplaats te maken, kunt u de opties in een JSON-bestand definiëren door overeenkomstige sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL Property Name]**. U kunt bijvoorbeeld de sleutel-waardeparen `image/bmp`, `image/gif`, `image/jpeg` en `image/png` definiëren en hun waarden opgeven zoals getoond in het volgende JSON-voorbeeldbestand. In het veld **[!UICONTROL Property Name]** kunt u het CRX-pad voor dit bestand opgeven.

```json
{
    "options" :
 [
          {"value" : "image/bmp","text" : "BMP"},
          {"value" : "image/gif","text" : "GIF"},
          {"value" : "image/jpeg","text" : "JPEG"},
          {"value" : "image/png","text" : "PNG"}
 ]
}
```

Als u een bestaand knooppunt wilt gebruiken, geeft u dit op in het dialoogvenster Selecteren.

>[!NOTE]
>
>De voorspelling van Opties is een aangepaste omslag die bezitsvoorspelling omvat om het beschreven gedrag aan te tonen. Momenteel, is er geen REST eindpunt beschikbaar om de functionaliteit te steunen native.

1. Tik op het AEM en ga naar **[!UICONTROL Tools > General > Search Forms]**.
1. Selecteer op de pagina **[!UICONTROL Search Forms]** de optie **[!UICONTROL Assets Admin Search Rail]** en tik vervolgens op het pictogram Bewerken.
1. Sleep op de pagina **[!UICONTROL Edit Search Form]** **[!UICONTROL Options Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. Voer op het tabblad **[!UICONTROL Settings]** een label en een naam voor de eigenschap in. Als u bijvoorbeeld assets wilt zoeken op basis van hun indeling, geeft u een gebruikersvriendelijke naam voor het label op, bijvoorbeeld **[!UICONTROL File Type]**. Geef de eigenschap op op basis waarvan de zoekopdracht in het eigenschapsveld moet worden uitgevoerd, bijvoorbeeld `jcr:content/metadata/dc:format.`
1. Voer een van de volgende handelingen uit:

   * Geef in het veld **[!UICONTROL Property Name]** het pad van het JSON-bestand op, waarin u de knooppunten voor de opties definieert en corresponderende sleutel-waardeparen opgeeft.
   * Tik ![Middelen voeg pictogram](assets/do-not-localize/aem_assets_add_icon.png) naast het veld Opties om de weergavetekst en -waarde op te geven voor de opties die u wilt opgeven in het deelvenster Filters. Tik op ![Middelen toevoegen pictogram](assets/do-not-localize/aem_assets_add_icon.png) en herhaal de stap om nog een optie toe te voegen.

1. Zorg ervoor dat **[!UICONTROL Single Select]** is uitgeschakeld, zodat de gebruiker meerdere opties voor bestandstypen tegelijk kan selecteren (bijvoorbeeld Afbeeldingen, Documenten, Multimedia en Archieven). Als u **[!UICONTROL Single Select]** selecteert, kan de gebruiker slechts één optie tegelijk selecteren voor bestandstypen.

   ![De beschikbare velden in de voorspelling Opties](assets/options_predicate.png)

   De beschikbare velden in de voorspelling Opties

1. Voer in het veld **Beschrijving** een optionele beschrijving in en klik op **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Zoeken. De voorspelling Opties wordt toegevoegd aan het **deelvenster Zoeken**. De opties voor **[!UICONTROL File Type]** worden getoond als checkboxes.

## Een voorspelling van een eigenschap met meerdere waarden toevoegen {#adding-a-multi-value-property-predicate}

Met de voorspelling `Multi Value Property` kunt u elementen zoeken naar meerdere waarden. Neem bijvoorbeeld een scenario waarin u afbeeldingen van meerdere producten in AEM Assets hebt en de metagegevens voor elke afbeelding een SKU-nummer bevatten dat aan het product is gekoppeld. Met deze voorspelling kunt u op basis van meerdere SKU-nummers zoeken naar productafbeeldingen.

1. Klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de pagina Zoeken in Forms en tik **Edit** ![aemassets_edit](assets/aemassets_edit.png).
1. Sleep op de pagina Zoekformulier bewerken een **[!UICONTROL Multi Value Property Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. Voer op het tabblad **[!UICONTROL Settings]** een label en plaatsaanduidingstekst in voor de voorspelling. Geef de naam van de eigenschap op op basis waarvan de zoekopdracht moet worden uitgevoerd in het eigenschapveld, bijvoorbeeld `jcr:content/metadata/dc:value`. U kunt ook een knooppunt selecteren in het dialoogvenster Selecteren.
1. Zorg ervoor dat **[!UICONTROL Delimiter Support]** is geselecteerd. Geef in het veld **[!UICONTROL Input Delimiters]** scheidingstekens op om afzonderlijke waarden van elkaar te scheiden. Standaard wordt een komma opgegeven als scheidingsteken. U kunt een ander scheidingsteken opgeven.
1. Voer in het veld **Beschrijving** een optionele beschrijving in en tik op **[!UICONTROL Done]**.
1. Ga naar het deelvenster Filters in de gebruikersinterface Assets. Het predicaat **[!UICONTROL Multi Value Property]** wordt toegevoegd aan het deelvenster.
1. Geef meerdere waarden op in het veld Meerdere waarden, gescheiden door de scheidingstekens, en voer de zoekopdracht uit. Met de functie voor voorspellen wordt een exacte tekstovereenkomst opgehaald voor de waarden die u opgeeft.

## Voorspelfunctie {#adding-a-tags-predicate} voor tags toevoegen

Met de voorspelling `Tags` kunt u op tags gebaseerde zoekopdrachten naar elementen uitvoeren. Standaard zoekt AEM Assets naar elementen op basis van de tags die u opgeeft. Met andere woorden, de zoekquery voert een OR-bewerking uit met de opgegeven tags. U kunt echter de optie Alle tags afstemmen gebruiken om te zoeken naar elementen die alle tags bevatten die u opgeeft.

1. Klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de pagina Zoeken in Forms en tik op **Bewerken** ![aemassets_edit](assets/aemassets_edit.png).
1. Op de pagina Zoekformulier bewerken sleept u **[!UICONTROL Tags Predicate]** van het tabblad Predicate selecteren naar het hoofdvenster.
1. Voer op het tabblad Instellingen een plaatsaanduidingstekst in voor de voorspelling. Geef de naam van de eigenschap op op basis waarvan de zoekopdracht moet worden uitgevoerd in het eigenschapveld, bijvoorbeeld `jcr:content/metadata/cq:tags`. U kunt ook een knooppunt in CRXDE selecteren in het dialoogvenster Selecteren.
1. Configureer de padeigenschap Root-tags van deze voorspelling om verschillende tags in de lijst Tags te vullen.
1. Selecteer **[!UICONTROL Show match all tags option]** om te zoeken naar assets die alle tags bevatten die u opgeeft.

   ![Typische instellingen van labels voorspellen](assets/tags_predicate.png)

1. Voer in het veld **[!UICONTROL Description]** een optionele beschrijving in en klik/tik **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Zoeken. De voorspelling **[!UICONTROL Tags]** wordt toegevoegd aan het deelvenster Zoeken.
1. Geef tags op op basis waarvan u de elementen wilt zoeken of een selectie wilt maken in de lijst met suggesties.
1. Selecteer **[!UICONTROL Match all]** om te zoeken naar overeenkomsten die alle markeringen omvatten die u specificeert.

## Andere voorspelling {#adding-other-predicates} toevoegen

Net als bij de manier waarop u een voorspelling van eigenschappen of een voorspelling van opties toevoegt, kunt u de volgende aanvullende voorspelling toevoegen aan het deelvenster Zoeken:

<table>
 <tbody>
  <tr>
   <td><p><strong>Naam voorspelling</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
   <td><p><strong>Eigenschappen</strong></p> </td>
  </tr>
  <tr>
   <td><p>Fulltext</p> </td>
   <td>Zoekvoorspelling om volledige tekstzoekopdrachten uit te voeren op een volledig elementknooppunt. Deze wordt toegewezen met de operator <code>jcr</code>:<code>contains</code>. U kunt een relatief pad opgeven als u een volledige tekstzoekopdracht wilt uitvoeren op een bepaald gedeelte van het knooppunt met elementen.</td>
   <td>
    <ul>
     <li>Label</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padbrowser</td>
   <td>Zoekvoorspelling voor het zoeken naar elementen in mappen en submappen op een vooraf geconfigureerd hoofdpad</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Basispad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Pad</p> </td>
   <td><p>Gebruik deze optie om resultaten op de locatie te filteren. U kunt verschillende paden opgeven als opties.</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Pad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Status publiceren</p> </td>
   <td><p>Zoeken voorspellen om middelen te zoeken op basis van hun publicatiestatus</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Relatieve datum</p> </td>
   <td><p>Zoeken voorspelt dat er wordt gezocht naar elementen op basis van de relatieve datum waarop deze zijn gemaakt. U kunt bijvoorbeeld opties configureren, zoals 2 maanden geleden, 3 weken geleden enzovoort. </p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Relatieve datum</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Bereik</p> </td>
   <td><p>Zoeken voorspelt dat er wordt gezocht in elementen die binnen een opgegeven bereik vallen. In het paneel van het Onderzoek, kunt u minimum en maximumwaarden voor de waaier specificeren.</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Datumbereik</p> </td>
   <td><p>Zoeken voorspelt hoe u elementen die binnen een opgegeven bereik zijn gemaakt, kunt zoeken naar een datumeigenschap. In het deelvenster Zoeken kunt u begin- en einddatums opgeven met behulp van datumkiezers.</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam</li>
     <li>Tekst bereik (van)</li>
     <li>Tekst bereik (naar)</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Date</p> </td>
   <td><p>Zoeken voorspelt hoe elementen op basis van een schuifregelaar worden doorzocht op basis van een eigenschap date.</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Bestandsgrootte</p> </td>
   <td><p>Zoeken voorspelt hoe u elementen kunt zoeken op basis van hun grootte. Het is een op meer details gebaseerde voorspelling waarbij u de schuifopties van een configureerbaar knooppunt selecteert. De standaardopties worden gedefinieerd op /libs/dam/options/predicates/filesize in de CRX-opslagplaats. De bestandsgrootte wordt opgegeven in bytes.</p> </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Pad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Element laatst gewijzigd</td>
   <td>Zoekvoorspelling voor zoeken in onlangs gewijzigde elementen </td>
   <td>
    <ul>
     <li>Eigenschapnaam</li>
     <li>Waarde van eigenschap</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Status publiceren</td>
   <td>Zoeken voorspellen om te zoeken naar elementen op basis van hun publicatiestatus </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Classificatie</td>
   <td>Zoeken voorspelt dat er wordt gezocht naar elementen op basis van hun gemiddelde waardering </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vervalstatus</td>
   <td>Zoeken voorspelt dat naar elementen wordt gezocht op basis van hun vervalstatus </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Verborgen</td>
   <td>Zoekvoorspelling die een verborgen veldeigenschap definieert voor het zoeken naar elementen</td>
   <td>
    <ul>
     <li>Eigenschapnaam</li>
     <li>Waarde van eigenschap</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Standaardzoekfacetten herstellen {#restoring-default-search-facets}

Standaard wordt een vergrendelingspictogram weergegeven vóór **[!UICONTROL Assets Admin Search Rail]** op de pagina **[!UICONTROL Search Forms]**. Het vergrendelingspictogram verdwijnt als u zoekfacetten aan het formulier toevoegt die aangeven dat het standaardformulier is gewijzigd.

Het vergrendelingspictogram tegen een optie op de pagina Zoeken in Forms geeft aan dat de standaardinstellingen intact zijn en niet zijn aangepast.

Voer de volgende stappen uit om de standaardzoekfacet te herstellen:

1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de **[!UICONTROL Search Forms]** pagina.
1. Tik **[!UICONTROL Delete]** ![verwijderingspictogram](assets/do-not-localize/deleteoutline.png) in de werkbalk.
1. Tik in het bevestigingsvenster op **[!UICONTROL Delete]** om de aangepaste wijzigingen te verwijderen.

   Nadat u de aangepaste wijzigingen in zoekfacetten hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór **[!UICONTROL Assets Admin Search Rail]** op de pagina **[!UICONTROL Search Forms]**.

## Gebruikersmachtigingen {#user-permissions}

Als er geen beheerdersrol aan u is toegewezen, volgt hier een lijst met machtigingen die u nodig hebt voor het uitvoeren van bewerkingen, verwijderen en voorvertoningen van handelingen met zoekfacetten.

| Actie | Machtiging |
|---|---|
| Bewerken | Lees en schrijf toestemmingen op de `/apps` knoop in CRX. |
| Verwijderen | Lees, schrijf, en schrap toestemmingen op de `/apps` knoop in CRX. |
| Voorvertoning | Lees, schrijf, en schrap toestemmingen op de `/var/dam/content` knoop in CRX. Ook, lees en schrijf toestemmingen op `/apps` knoop. |

>[!MORELIKETHIS]
>
>* [Digitale middelen](search-assets.md) zoeken.

