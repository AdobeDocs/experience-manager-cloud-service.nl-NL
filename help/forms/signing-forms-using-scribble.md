---
title: Hoe kan ik e-handtekeningen toepassen op een formulier met krabbelhandtekeningen?
description: Leer elektronische handtekeningen op een formulier toepassen met krabbelhandtekeningen.
uuid: ffeba886-9b24-4ed1-95c0-e19356ff2f23
products: SG_EXPERIENCEMANAGER/FORMS
topic-tags: author
feature: Adaptive Forms, Foundation Components
exl-id: dc89ecb1-2d9e-4d1d-b85b-af90c550e7d8
role: User, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1318'
ht-degree: 0%

---

# Een formulier elektronisch ondertekenen met scripthandtekeningen{#apply-electronic-signatures-to-a-form-using-deprecated-scribble-signatures}

>[!NOTE]
>
> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/signing-forms-using-scribble.html) |
| AEM as a Cloud Service | Dit artikel |


U kunt de **component van de Ondertekening van 0} Krabbelen gebruiken {om (Krabbelen) handtekening op een Aangepaste Vorm te trekken.**<!-- The Signature step component displays a PDF version of the Adaptive Form. You require a Document of Record option enabled or form template based Adaptive Forms to use the Signature step component. -->

![ Scripttekendialoog ](assets/scribble-signature.png)

## Verschillende opties beschikbaar in het venster Handtekening

* **A:** klik het **pictogram van de Borstel van de Verf** om uw handtekening op canvas te trekken.
* **B:** klik het **Duidelijke** pictogram om de handtekening op canvas te ontruimen.
* **C:** klik het **Geolocation** pictogram om geolocation samen met de handtekening toe te voegen.
* **D:** klik het **pictogram van het Toetsenbord** om uw naam op canvas te typen.

Zodra u het Gedaan ![ a_forms_save ](assets/aem_forms_save.png) pictogram in het Krabbelhandtekeningsvenster selecteert, kunt u niet de handtekening uitgeven. Als u de handtekening wilt bewerken, moet u de huidige handtekening negeren en opnieuw ondertekenen met de bovenstaande optie Penseel/toetsenbord.

U kunt **selecteren vormt** ![ pictogram ](assets/configure.png) om de aspectverhouding van het Krabbelcanvas van de Handtekening te plaatsen.

* Als de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen kleiner is dan 1, worden de gegevens over de geolocatie toegevoegd onder aan het canvas voor Krabbelhandtekeningen.
* Wanneer de hoogte-breedteverhouding van het canvas voor Krabbelhandtekeningen groter is dan 1, wordt de informatie over de geolocatie toegevoegd aan de rechterkant van het canvas voor Krabbelhandtekeningen.


![ krabbelhandtekening-bodem ](assets/scribble-signature-aspectratio.PNG)



>[!NOTE]
>
>Handtekeningen worden altijd opgeslagen in de PNG-indeling.

## Een adaptief formulier configureren voor het gebruik van een scripthandtekening {#configure-an-adaptive-form-to-use-scribble-signature}

1. Open een adaptief formulier in de bewerkingsmodus.
1. De belemmering-en-daling de **component van de Handtekening van 0} Krabbelen {van componentenbrowser aan de Aangepaste Vorm.**
1. Selecteer **vormen** ![ ](assets/configure.png) pictogram. De eigenschappenbrowser wordt geopend en de eigenschappen van de component Krabbelen handtekening worden weergegeven. [ vormt eigenschappen van Krabbelhandtekening ](#properties-of-scribble-signature-component) zoals die in de volgende sectie wordt besproken.

   ![ Krabbelen Handtekening ](/help/forms/assets/scribblesig.png)

1. Selecteer het Gedaan ![ name_forms_save ](assets/aem_forms_save.png) pictogram om de veranderingen te bewaren. De handtekening is geconfigureerd.

## Eigenschappen van de component Krabbelhandtekening configureren

Met het dialoogvenster Configureren kunt u de component Scripthandtekening eenvoudig aanpassen voor bezoekers.

### Tabblad Standaard

![ Basis lusje ](/help/forms/assets/scribblesig-basic.png)

* **Naam** - u kunt een vormcomponent gemakkelijk met zijn unieke naam zowel in de vorm als in de regelredacteur identificeren, maar de naam moet geen ruimten of speciale karakters bevatten.

* **Titel** - met zijn Titel, kunt u een component in een vorm gemakkelijk identificeren en door gebrek, verschijnt de titel bovenop de component. Als u geen titel toevoegt, wordt de naam van de component weergegeven in plaats van de titeltekst.

* **staat RTF voor Titel** toe - Deze eigenschappen laat gebruikers toe om gewone teksttitels te formatteren, die eigenschappen zoals vette, cursieve, onderstreepte tekst, diverse doopvonten, doopvontgrootte, kleuren, en extra optie opnemen om visuele presentatie en aanpassing te verbeteren. Deze functie biedt meer flexibiliteit en creatieve controle bij het opvallen van titels in documenten, websites of toepassingen.\
  Op het selecteren van checkbox voor **staat RTF-tekst voor Titel** toe, wordt het formatteren opties zichtbaar om de titel van de component te stileren. Om tot alle beschikbare het formatteren opties toegang te hebben, kunt u op het ![ pictogram Volledig scherm ](/help/forms/assets/fullscreen-icon.png) tabel klikken.

  ![ de rijke tekststeun van 0}](/help/forms/assets/richtext-support-title.png)

* **Verberg Titel** - selecteer de optie om de Titel van de component te verbergen.
* **Vereist Gebied** - selecteer de optie om het gebied verplicht te maken.
* **Vereiste Bericht van het Gebied** - het **Vereiste Bericht van het Gebied** is een klantgericht bericht dat aan gebruikers wordt getoond wanneer zij proberen om een vorm voor te leggen zonder een verplicht gebied in te vullen.
* **Model van Gegevens Bind Verwijzing** - A bindt verwijzing is een verwijzing naar een gegevenselement dat in een externe gegevensbron wordt opgeslagen en in een vorm wordt gebruikt. Met de bind-verwijzing kunt u gegevens dynamisch binden aan formuliervelden, zodat in het formulier de meest actuele gegevens uit de gegevensbron kunnen worden weergegeven. Een bind-verwijzing kan bijvoorbeeld worden gebruikt om de naam en het adres van een klant in een formulier weer te geven op basis van de id van de klant die in het formulier is ingevoerd. De bind verwijzing kan ook worden gebruikt om de gegevensbron met gegevens bij te werken ingegaan in de vorm. Op deze manier kunt u in AEM Forms formulieren maken die interageren met externe gegevensbronnen, zodat u een naadloze gebruikerservaring hebt voor het verzamelen en beheren van gegevens.
* **Verberg Voorwerp** - selecteer de optie om de component van de vorm te verbergen. De component blijft toegankelijk voor andere doeleinden, zoals het gebruiken voor berekeningen in de Redacteur van de Regel. Dit is handig wanneer u informatie wilt opslaan die niet hoeft te worden bekeken of rechtstreeks door de gebruiker hoeft te worden gewijzigd.
* **maak Voorwerp** onbruikbaar - selecteer de optie om de component onbruikbaar te maken. De uitgeschakelde component is niet actief of bewerkbaar voor de eindgebruiker. De gebruiker kan de waarde van het veld zien, maar kan deze niet wijzigen. De component blijft toegankelijk voor andere doeleinden, zoals het gebruiken voor berekeningen in de Redacteur van de Regel.
* **Verhouding** - de aspectverhouding in een Krabbelende component van de Handtekening bepaalt het proportionele verband tussen zijn breedte en hoogte.
* **Lay-out van het Gebied** - de **optie van de Lay-out van het Gebied** bepaalt hoe de vormelementen, met inbegrip van de etiketten (titels) en foutenmeldingen, met betrekking tot de component worden geplaatst. De **Titel en de Fout als Boven van Widget** plaatsen de titel van het gebied (etiket) en foutenmeldingen boven de component. **erf van de AanpassingsConfiguratie van de Vorm** gebruikt de montages van de standaardgebiedlay-out die in de Aangepaste configuratie van de Vorm worden gespecificeerd.
* **CSS Klasse** - de **CSS klasse** staat u toe om douanestijlen op een component toe te passen door één of meerdere CSS klassen toe te wijzen die in uw stijlpagina worden bepaald. Het maakt consistente opmaak en aanpassing van de layout mogelijk in uw adaptieve formulier.

### Help-inhoud

![ Inhoud tabel van de Hulp ](/help/forms/assets/scribblesig-help.png)

* **Korte beschrijving** - een korte beschrijving is een korte tekstverklaring die extra informatie of verduidelijking over het doel van een specifiek vormgebied verstrekt. Het helpt de gebruiker begrijpen welk type gegevens in het gebied moeten worden ingegaan en kan richtlijnen of voorbeelden verstrekken helpen ervoor zorgen dat de ingevoerde informatie geldig is en aan de gewenste criteria voldoet. Korte beschrijvingen blijven standaard verborgen. Laat **toe tonen altijd korte beschrijving** optie om het onder de component te tonen.

* **toont altijd korte beschrijving** - laat de optie toe om de Korte beschrijving onder de component te tonen.

* **Lange Beschrijving** - het verwijst naar extra informatie of begeleiding die aan de gebruiker wordt verstrekt om hen bij het correct invullen van een vormgebied bij te staan. Deze wordt weergegeven wanneer de gebruiker op het Help-pictogram (i) naast de component klikt. De klasse biedt gedetailleerdere informatie dan de label- of plaatsaanduidingstekst van een formulierveld en is ontworpen om de gebruiker te helpen de vereisten of beperkingen van het veld te begrijpen. Het kan ook suggesties of voorbeelden bevatten om het invullen van het formulier eenvoudiger en nauwkeuriger te maken.

### Tabblad Toegankelijkheid {#accessibility}

![ Toegankelijkheid tabel ](/help/forms/assets/scribblesig-acc.png)

Op het **lusje van de Toegankelijkheid**, worden de waarden geplaatst voor [ toegankelijkheid ARIA ](https://www.w3.org/WAI/standards-guidelines/aria/) etiketten voor de component. Er zijn verschillende opties beschikbaar voor het gebruik van de tekst voor schermlezers:

* **de Voorrang van Reader van 0} het Scherm** - de Voorrang van Reader van het Scherm verwijst naar extra tekst die specifiek bedoeld is om door ondersteunende technologieën, zoals het schermlezers te worden gelezen, die door visueel gehandicapte individuen wordt gebruikt. Deze tekst bevat een audiobeschrijving van het doel van het formulierveld en kan informatie bevatten over de titel, beschrijving, naam en relevante berichten (aangepaste tekst) van het veld. Met de schermlezertekst kunt u ervoor zorgen dat het formulier toegankelijk is voor alle gebruikers, inclusief gebruikers met een visuele handicap, en krijgt deze een volledig inzicht in het formulierveld en de vereisten ervan.

   * **Tekst van de Douane**: Selecteer deze optie om de douanetekst voor de toegankelijkheidslabels van ARIA te gebruiken. Als u deze optie selecteert, wordt het dialoogvenster Aangepaste tekst weergegeven. U kunt relevante informatie toevoegen in het dialoogvenster Aangepaste tekst.
   * **Korte Beschrijving**: Selecteer deze optie om de beschrijving voor de toegankelijkheidslabels van ARIA te gebruiken.
   * **Titel**: Selecteer deze optie om de titel voor de toegankelijkheidslabels van ARIA te gebruiken.
   * **Naam**: Selecteer deze optie om de naam voor de toegankelijkheidslabels van ARIA te gebruiken.
   * **niets**: Selecteer deze optie als u niet voor de toegankelijkheidslabels van ARIA wilt toevoegen.

<!--

 * **Element Name**: Specify name of the component.

    * **Title:** Specify unique title of the component.
    * **Template message:** Specify the message to be displayed while the signature PDF is being loaded. Adobe Sign services take some time to prepare and load signature PDF.
    * **Signing Service:** Select the **Scribble Signature** option.

    * **CSS Class**: Specify CSS class of the client library, if any. Adobe recommends using [themes](themes.md) and [in-line styles](inline-style-adaptive-forms.md) instead of CSS Class.
## Sign an Adaptive Form using Scribble Signature {#sign-an-adaptive-form-using-scribble-signature}

1. After you fill an Adaptive Form and reach the Signature Step page, the signature screen is displayed.

   ![Signature screen for EchoSign page](assets/esignscribblesign.jpg)

1. Click **[!UICONTROL Sign]**. The scribble sign dialog appears. Sign the form and click the Done ![aem_forms_save](assets/aem_forms_save.png) icon to save the signature.

   ![Scribble sign dialog](assets/scribblewidget.png)

1. Click complete to finish the signing process.

   ![Complete the signing process](assets/scribblecomplete.jpg)

The signatures are added to the form and the form control moves to the next panel. -->

## Zie ook {#see-also}

{{see-also}}