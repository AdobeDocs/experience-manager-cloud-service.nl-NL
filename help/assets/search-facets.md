---
title: Zoeken in facetten.
description: In dit artikel wordt beschreven hoe u zoekfacetten in de Experience Manager maakt, wijzigt en gebruikt.
feature: Metadata
role: Admin, User
exl-id: f994c1bf-3f9d-4cb2-88f4-72a9ad6fa999
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '2388'
ht-degree: 13%

---

# Zoeken in facetten {#search-facets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/search-facets.html) |
| AEM as a Cloud Service | Dit artikel |

Een bedrijfsbrede implementatie van Adobe Experience Manager Assets heeft de mogelijkheid om veel assets op te slaan. Soms kan het lastig en tijdrovend zijn om het juiste middel te vinden als u alleen de algemene zoekmogelijkheden van Experience Manager gebruikt.

Gebruik zoekfacetten in het deelvenster Filters om de zoekervaring gedetailleerder te maken en de zoekfunctionaliteit efficiënter en veelzijdiger te maken. De facetten van het onderzoek voegen veelvoudige afmetingen (predikaten) toe die u toelaten om complexere onderzoeken uit te voeren. Het deelvenster Filters bevat een aantal standaardfacetten. U kunt ook aangepaste zoekfacetten toevoegen.

Samengevat kunt u met zoekfacetten op verschillende manieren naar elementen zoeken in plaats van in één, vooraf bepaalde, taxonomische volgorde. U kunt gemakkelijk tot het gewenste niveau van detail voor een gerichter onderzoek boor.

Als u bijvoorbeeld een afbeelding zoekt, kunt u kiezen of u een bitmap- of een vectorafbeelding wilt. U kunt het zoekbereik verder verkleinen door het MIME-type voor de afbeelding op te geven. Op dezelfde manier kunt u bij het zoeken naar documenten de indeling opgeven, bijvoorbeeld PDF of MS Word.

## Een voorspelling toevoegen {#adding-a-predicate}

De zoekfacetten die in het deelvenster Filters worden weergegeven, worden in het onderliggende zoekformulier gedefinieerd aan de hand van voorspelden. Als u meer of verschillende facetten wilt weergeven, voegt u voorspelingen toe aan het standaardformulier of gebruikt u een aangepast formulier dat naar keuze facetten bevat.

Voor zoekopdrachten in volledige tekst voegt u de `Fulltext` voorspelling toe aan het formulier. Gebruik de voorspelling van de eigenschap om te zoeken naar elementen die overeenkomen met één eigenschap die u opgeeft. Gebruik de voorspelling Opties om te zoeken in elementen die overeenkomen met een of meer waarden voor een bepaalde eigenschap. Voeg de Datumbereik-voorspelling toe aan zoekelementen die binnen een opgegeven datumbereik zijn gemaakt.

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]** .
1. Van de pagina van Forms van het Onderzoek, uitgezocht **[!UICONTROL Assets Admin Search Rail]**, dan uitgezocht **** ![ aemassets_edit ](assets/aemassets_edit.png).

   ![ plaats en selecteer de Rail van het Onderzoek van Admin van Assets ](assets/assets_admin_searchrail.png)

1. Sleep op de pagina Zoeken in Forms bewerken een voorspelling van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster. Sleep bijvoorbeeld **[!UICONTROL Property Predicate]** .

   ![ Uitgezocht en beweeg predikaat om de onderzoeksfilters ](assets/drag_predicate.png) aan te passen

   *Cijfer: Selecteer en verplaats predikaat om de onderzoeksfilters aan te passen.*

1. Voer op het tabblad Instellingen een veldlabel, plaatsaanduidingstekst en beschrijving voor de voorspelling in. Geef een geldige naam op voor de eigenschap metadata die u aan de voorspelling wilt koppelen. Het koptekstlabel op het tabblad Instellingen geeft het type van de geselecteerde voorspelling aan.

   ![ Gebruik het lusje van Montages om de vereiste opties van te verstrekken predikaat ](assets/settings.png)

   *Cijfer: Gebruik het lusje van Montages om de vereiste opties van te verstrekken predikaat.*

1. Geef in het veld **[!UICONTROL Property Name]** een geldige naam op voor de metadata-eigenschap die u aan het predicaat wilt koppelen. Dit is de naam op basis waarvan de zoekopdracht wordt uitgevoerd. Voer bijvoorbeeld `jcr:content/metadata/dc:description` of `./jcr:content/metadata/dc:description` in. U kunt ook een bestaand knooppunt selecteren in het dialoogvenster Selecteren.

   ![ associeer een meta-gegevensbezit met predikaat op het gebied van de Naam van het Bezit ](assets/property_settings.png)

   *Cijfer: Koppel een meta-gegevensbezit met predikaat op het gebied van de Naam van het Bezit.*

1. Klik de **[!UICONTROL Preview]** ![ voorproef ](assets/preview.png) om een voorproef van het paneel van Filters te produceren aangezien het verschijnt nadat u predikaat toevoegt.
1. Bekijk de lay-out van de voorspelling in de modus Voorbeeld.

   ![ Voorproef de onderzoeksvorm alvorens de veranderingen voor te leggen ](assets/preview-1.png)

   Voorbeeld van het zoekformulier bekijken voordat de wijzigingen worden verzonden

1. Om de voorproef te sluiten, klik **[!UICONTROL Close]** ![ dicht ](assets/do-not-localize/close_icon.png) op de hoger-juiste hoek van de voorproef.
1. Selecteer **[!UICONTROL Done]** om de instellingen op te slaan.
1. Navigeer naar het deelvenster Zoeken in de gebruikersinterface van Assets. De voorspelling van de eigenschap wordt toegevoegd aan het deelvenster.
1. Voer in het tekstvak een beschrijving in voor het element dat u wilt doorzoeken. Voer bijvoorbeeld &quot;Adobe&quot; in. Wanneer u een zoekopdracht uitvoert, worden elementen met een beschrijving die overeenkomt met &quot;Adobe&quot;, weergegeven in de zoekresultaten.

## Een voorspelling van opties toevoegen {#adding-an-options-predicate}

Met de voorspelling Opties kunt u meerdere zoekopties toevoegen in het deelvenster Filters. U kunt een of meer van deze opties selecteren in het deelvenster Filters om te zoeken naar elementen. Als u bijvoorbeeld naar elementen wilt zoeken op basis van het bestandstype, configureert u opties, zoals Afbeeldingen, Multimedia, Documenten en Archieven, in het zoekformulier. Nadat u deze opties hebt geconfigureerd, wordt de zoekopdracht uitgevoerd op elementen van het type GIF, JPEG, PNG, enzovoort, wanneer u de optie Afbeeldingen in het deelvenster Filters selecteert.

Als u de opties wilt toewijzen aan de desbetreffende eigenschap, maakt u een knooppuntstructuur voor de opties en geeft u het pad van het bovenliggende knooppunt op in de eigenschap Eigenschapnaam van de voorspelling van opties. Het bovenliggende knooppunt moet van het type `sling` zijn: `OrderedFolder` . De opties moeten van het type `nt:unstructured` zijn. Voor de optieknooppunten moeten de eigenschappen `jcr:title` en `value` zijn geconfigureerd.

De eigenschap `jcr:title` is een gebruiksvriendelijke naam voor de optie die wordt weergegeven in het deelvenster Filters. Het veld `value` wordt gebruikt in de query om overeen te komen met de opgegeven eigenschap.

Wanneer u een optie selecteert, wordt de zoekopdracht uitgevoerd op basis van de eigenschap `value` van het optieknooppunt en eventuele onderliggende knooppunten. De volledige structuur onder het optieknooppunt wordt doorlopen en de `value` eigenschap van elk onderliggend knooppunt wordt gecombineerd met een OR-bewerking om de zoekquery te vormen.

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

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools > General > Search Forms]** .
1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de pagina **[!UICONTROL Search Forms]** en selecteer vervolgens het pictogram Bewerken.
1. Sleep op de pagina **[!UICONTROL Edit Search Form]** **[!UICONTROL Options Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. Voer op het tabblad **[!UICONTROL Settings]** een label en een naam voor de eigenschap in. Als u bijvoorbeeld elementen wilt zoeken op basis van hun indeling, geeft u een gebruikersvriendelijke naam voor het label op, bijvoorbeeld **[!UICONTROL File Type]** . Geef de eigenschap op die is gebaseerd op de zoekopdracht in het eigenschapveld, bijvoorbeeld `jcr:content/metadata/dc:format.`
1. Voer een van de volgende handelingen uit:

   * Geef in het veld **[!UICONTROL Property Name]** het pad van het JSON-bestand op, waarin u de knooppunten voor de opties definieert en corresponderende sleutelwaardeparen opgeeft.
   * Selecteer ![ Assets voegt pictogram ](assets/do-not-localize/aem_assets_add_icon.png) naast het gebied van Opties toe om de vertoningstekst en de waarde voor de opties te specificeren u in het paneel van Filters wilt leveren. Om een andere optie toe te voegen, voegt de uitgezochte ![ Assets pictogram ](assets/do-not-localize/aem_assets_add_icon.png) toe en herhaalt de stap.

1. Zorg ervoor dat **[!UICONTROL Single Select]** is uitgeschakeld, zodat de gebruiker meerdere opties voor bestandstypen tegelijk kan selecteren (bijvoorbeeld Afbeeldingen, Documenten, Multimedia en Archieven). Als u **[!UICONTROL Single Select]** selecteert, kan de gebruiker slechts één optie tegelijk selecteren voor bestandstypen.

   ![ de beschikbare gebieden in de Opties voorspellen ](assets/options_predicate.png)

   De beschikbare velden in de voorspelling Opties

1. Op het **gebied van de Beschrijving**, ga een facultatieve beschrijving in en klik dan **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Zoeken. Het voorspellen van Opties wordt toegevoegd aan het **paneel van het Onderzoek**. De opties voor **[!UICONTROL File Type]** worden weergegeven als selectievakjes.

## Een voorspelling van een eigenschap met meerdere waarden toevoegen {#adding-a-multi-value-property-predicate}

Met de voorspelling `Multi Value Property` kunt u elementen zoeken naar meerdere waarden. Neem bijvoorbeeld een scenario waarin u afbeeldingen van meerdere producten in [!DNL Assets] hebt en de metagegevens voor elke afbeelding een SKU-nummer bevatten dat aan het product is gekoppeld. Met deze voorspelling kunt u op basis van meerdere SKU-nummers zoeken naar productafbeeldingen.

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]** .
1. Voor de pagina van Forms van het Onderzoek, uitgezocht **[!UICONTROL Assets Admin Search Rail]**, geeft uitgezocht **** ![ aemassets_edit ](assets/aemassets_edit.png) uit.
1. Sleep op de pagina Zoekformulier bewerken een **[!UICONTROL Multi Value Property Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. Voer op het tabblad **[!UICONTROL Settings]** een label en plaatsaanduidingstekst in voor de voorspelling. Geef de naam van de eigenschap op op basis waarvan de zoekopdracht in het eigenschapveld moet worden uitgevoerd, bijvoorbeeld `jcr:content/metadata/dc:value` . U kunt ook een knooppunt selecteren in het dialoogvenster Selecteren.
1. Zorg ervoor dat **[!UICONTROL Delimiter Support]** is geselecteerd. Geef in het veld **[!UICONTROL Input Delimiters]** scheidingstekens op om afzonderlijke waarden van elkaar te scheiden. Standaard wordt een komma opgegeven als scheidingsteken. U kunt een ander scheidingsteken opgeven.
1. Op het **gebied van de Beschrijving**, ga een facultatieve beschrijving in en selecteer dan **[!UICONTROL Done]**.
1. Ga naar het deelvenster Filters in de gebruikersinterface Assets. Het predicaat **[!UICONTROL Multi Value Property]** wordt toegevoegd aan het deelvenster.
1. Geef meerdere waarden op in het veld Meerdere waarden, gescheiden door de scheidingstekens, en voer de zoekopdracht uit. Met de functie voor voorspellen wordt een exacte tekstovereenkomst opgehaald voor de waarden die u opgeeft.

## Een voorspelling van tags toevoegen {#adding-a-tags-predicate}

Met de voorspelling `Tags` kunt u op tags gebaseerde zoekopdrachten naar elementen uitvoeren. Standaard zoekt [!DNL Assets] naar elementen op basis van de tags die u opgeeft. Met andere woorden, de zoekquery voert een OR-bewerking uit met de opgegeven tags. U kunt echter de optie Alle tags afstemmen gebruiken om te zoeken naar elementen die alle tags bevatten die u opgeeft.

1. Klik op het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]** .
1. Van de pagina van Forms van het Onderzoek, selecteer **[!UICONTROL Assets Admin Search Rail]** en selecteer dan **uitgeven** ![ aemassets_edit ](assets/aemassets_edit.png).
1. Op de pagina Zoekformulier bewerken sleept u **[!UICONTROL Tags Predicate]** van het tabblad Voorspelling selecteren naar het hoofdvenster.
1. Voer op het tabblad Instellingen een plaatsaanduidingstekst in voor de voorspelling. Geef de naam van de eigenschap op op basis waarvan de zoekopdracht in het eigenschapveld moet worden uitgevoerd, bijvoorbeeld `jcr:content/metadata/cq:tags` . U kunt ook een knooppunt in CRXDE selecteren in het dialoogvenster Selecteren.
1. Configureer de padeigenschap Root-tags van deze voorspelling om verschillende tags in de lijst Tags te vullen.
1. Selecteer **[!UICONTROL Show match all tags option]** om te zoeken naar assets die alle tags bevatten die u opgeeft.

   ![ Typische montages van Markeringen voorspellen ](assets/tags_predicate.png)

1. Voer in het veld **[!UICONTROL Description]** een optionele beschrijving in en selecteer vervolgens **[!UICONTROL Done]** .
1. Navigeer naar het deelvenster Zoeken. De voorspelling **[!UICONTROL Tags]** wordt toegevoegd aan het deelvenster Zoeken.
1. Geef tags op op basis waarvan u de elementen wilt zoeken of een selectie wilt maken in de lijst met suggesties.
1. Selecteer **[!UICONTROL Match all]** om te zoeken naar overeenkomsten die alle tags bevatten die u opgeeft.

U kunt de codestructuur in oplopende of aflopende volgorde sorteren op basis van de datum **[!UICONTROL Name]** (alfabetische volgorde), **[!UICONTROL Created]** date of **[!UICONTROL Modified]** . In de volgende afbeelding wordt de codestructuur alfabetisch gesorteerd op basis van de **[!UICONTROL Name]** .

![ toe:voegen-markeringen ](assets/add-tags-to-asset.png)


## Andere voorspellingen toevoegen {#adding-other-predicates}

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
   <td>Zoekvoorspelling om volledige tekstzoekopdrachten uit te voeren op een volledig elementknooppunt. Deze wordt toegewezen met de operator <code>jcr</code>:<code>contains</code> . U kunt een relatief pad opgeven als u een volledige tekstzoekopdracht wilt uitvoeren op een bepaald gedeelte van het knooppunt met elementen.</td>
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
   <td><p>Publish-status</p> </td>
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
   <td><p>Datum</p> </td>
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
   <td><p>Zoeken voorspelt hoe u elementen kunt zoeken op basis van hun grootte. Het is een op meer details gebaseerde voorspelling waarbij u de schuifopties van een configureerbaar knooppunt selecteert. De standaardopties zijn gedefinieerd op /libs/dam/options/predicates/filesize in de CRX-opslagplaats. De bestandsgrootte wordt opgegeven in bytes.</p> </td>
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
   <td>Publish-status</td>
   <td>Zoeken voorspellen om te zoeken naar elementen op basis van hun publicatiestatus </td>
   <td>
    <ul>
     <li>Label</li>
     <li>Eigenschapnaam</li>
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

## Standaardzoekfacetten verwijderen {#removing-default-search-facets}

Adobe raadt u aan voorzichtig te zijn met het verwijderen van standaardzoekfacetten om prestatieproblemen te voorkomen. Het verwijderen van standaardzoekfacetten kan ook van invloed zijn op het standaardgedrag van functies.

Verwijder de volgende verborgen velden niet omdat dit tot een probleem met de queryprestaties voor OmniSearch en slimme verzamelingen leidt:

* group.2_group.type=dam:Asset

* group.1_group.type=nt:map

* group.p.or=true

## Standaardzoekfacetten herstellen {#restoring-default-search-facets}

Standaard verschijnt het pictogram Vergrendelen voor **[!UICONTROL Assets Admin Search Rail]** op de pagina van **[!UICONTROL Search Forms]** . Het vergrendelingspictogram verdwijnt als u zoekfacetten aan het formulier toevoegt die aangeven dat het standaardformulier is gewijzigd.

Het vergrendelingspictogram tegen een optie op de pagina Zoeken in Forms geeft aan dat de standaardinstellingen intact zijn en niet worden aangepast.

Voer de volgende stappen uit om de standaardzoekfacet te herstellen:

1. Selecteer **[!UICONTROL Assets Admin Search Rail]** op de pagina van **[!UICONTROL Search Forms]** .
1. Selecteer **[!UICONTROL Delete]** ![ schrappingspictogram ](assets/do-not-localize/deleteoutline.png) in de toolbar.
1. Selecteer **[!UICONTROL Delete]** in het bevestigingsvenster om de aangepaste wijzigingen te verwijderen.

   Nadat u de aangepaste wijzigingen in zoekfacetten hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór **[!UICONTROL Assets Admin Search Rail]** op de pagina **[!UICONTROL Search Forms]**.

## Gebruikersmachtigingen {#user-permissions}

Als er geen beheerdersrol aan u is toegewezen, volgt hier een lijst met machtigingen die u nodig hebt voor het uitvoeren van bewerkingen, verwijderen en voorvertoningen van handelingen met zoekfacetten.

| Handeling | Machtiging |
|---|---|
| Bewerken | lees- en schrijfmachtigingen voor het knooppunt `/apps` in CRX. |
| Verwijderen | Rechten voor het lezen, schrijven en verwijderen van het knooppunt `/apps` in CRX. |
| Voorvertoning | Rechten voor het lezen, schrijven en verwijderen van het knooppunt `/var/dam/content` in CRX. Lees- en schrijfmachtigingen voor `/apps` node. |

**zie ook**

* [ beste praktijken van het Onderzoek ](search-best-practices.md)
* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [ Onderzoek digitale activa ](search-assets.md).
