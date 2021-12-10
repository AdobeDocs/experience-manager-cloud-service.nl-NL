---
title: Inleiding tot Adaptive Forms
seo-title: Introduction to authoring Adaptive Forms
description: AEM Forms biedt gebruiksvriendelijke maar toch krachtige interface voor het ontwerpen van Adaptive Forms. Deze sjabloon biedt een groot aantal componenten en gereedschappen waarmee u formulieren kunt maken.
seo-description: AEM Forms provide easy-to-use yet powerful interface for authoring Adaptive Forms. It provides a host of components and tools that you can use to build forms.
uuid: 3b150507-41b9-47c2-a94c-f85b903b2274
content-type: reference
topic-tags: author, introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: ba70921e-db7e-43f6-902c-1065d3b13aef
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '2302'
ht-degree: 0%

---


# Adaptieve Forms-editor {#introduction-to-authoring-adaptive-forms}

## Overzicht {#overview}

Met Adaptieve Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. [!DNL AEM Forms] biedt een intuïtieve gebruikersinterface en kant-en-klare componenten voor het maken en werken met Adaptive Forms. U kunt desgewenst een adaptief formulier maken op basis van een formuliermodel of -schema of zonder formuliermodel. Het is belangrijk om zorgvuldig het formuliermodel te kiezen dat niet alleen aan uw vereisten voldoet, maar ook uw bestaande infrastructurele investeringen en middelen uitbreidt. U kunt uit de volgende opties kiezen om een adaptief formulier te maken:

<!-- * **Using a form data model**
  [Data integration](data-integration.md) lets you integrate entities and services from disparate data sources in to a Form Data Model that you can use to create Adaptive Forms. Choose Form Data Model if the Adaptive Form you are creating involves fetching and write data from and to multiple data source. -->

* **Een XDP-formuliersjabloon gebruiken**
Het is een ideaal formuliermodel als u investeert in XFA-gebaseerde of XDP-formulieren. Het biedt een directe manier om uw XFA-formulieren om te zetten in Adaptive Forms. Bestaande XFA-regels blijven behouden in de gekoppelde Adaptive Forms. De resulterende Adaptieve Forms ondersteunt XFA-constructies, zoals validaties, gebeurtenissen, eigenschappen en patronen.

* **Een XML-schemadefinitie (XSD) of een JSON-schema gebruiken**
De schema&#39;s van XML en JSON vertegenwoordigen de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt het schema koppelen aan een adaptief formulier en de elementen ervan gebruiken om dynamische inhoud toe te voegen aan het adaptieve formulier. De elementen van het schema zijn beschikbaar voor gebruik op het tabblad Gegevensmodelobjecten van de browser Inhoud wanneer u Adaptief Forms maakt.

* **Geen of geen formuliermodel gebruiken**
Adaptieve Forms die met deze optie is gemaakt, gebruikt geen formuliermodel. De XML-gegevens die op basis van dergelijke formulieren worden gegenereerd, hebben een vlakke structuur met velden en bijbehorende waarden.

<!--  For more information about creating an Adaptive Form, see [Creating an Adaptive Form](creating-adaptive-form.md). -->

## Aangepaste interface voor formulierontwerp {#adaptive-form-authoring-ui}

De interface voor het optimaliseren van aanrakingen voor het ontwerpen van Adaptive Forms is intuïtief en biedt:

* Functionaliteit voor slepen en neerzetten
* Standaardformuliercomponenten
* Geïntegreerde opslagplaats voor middelen

Wanneer u een nieuw adaptief formulier maakt of een bestaand adaptief formulier bewerkt, gebruikt u de volgende UI-elementen:

* [Zijbalk](#sidebar)
* [Pagina, werkbalk](#page-toolbar)
* [Component, werkbalk](#component-toolbar)
* [Pagina Adaptief formulier](#af-page)

<!-- ![Adaptive Form authoring UI](assets/formeditor.png)

**A.** Sidebar **B.** Page toolbar **C.** Adaptive Form page -->

### Zijbalk {#sidebar}

Met de zijbalk kunt u

* Zoek, bekijk en gebruik middelen in uw AEM DAM-opslagplaats (Digital Asset Management).
* Zie formulierinhoud zoals deelvensters, componenten, velden en indeling.
* Voeg componenten toe aan uw formulier.
* Eigenschappen van componenten bewerken.

![Zijbalk](assets/sidebar-comps.png)

**A.** Inhoudsbrowser **B.** Eigenschappenbrowser **C.** Bandenbrowser **D.** Browser voor componenten

<!--Click to enlarge

](assets/sidebar-comps-1.png) -->

De zijbalk bestaat uit de volgende browsers:

* **Inhoudsbrowser**
In de inhoudbrowser kunt u zien:

   * **Formulierobjecten**
Hiermee geeft u de objecthiërarchie van het formulier weer. Auteurs kunnen naar specifieke formuliercomponenten navigeren door op dat element te tikken in de formulierobjectstructuur. Auteur kan objecten zoeken en opnieuw rangschikken vanuit deze structuur.

   * **Gegevensmodelobjecten**
Hiermee kunt u de hiërarchie van het formuliermodel bekijken.
Hiermee kunt u formuliermodelelementen naar het adaptieve formulier slepen en neerzetten. De toegevoegde elementen worden automatisch geconverteerd naar formuliercomponenten met behoud van hun oorspronkelijke eigenschappen. U kunt gegevensmodelobjecten zien wanneer uw formulier gebruikmaakt van een XML-schema, JSON-schema of XDP-sjabloon.

* **Eigenschappenbrowser**

   Hiermee kunt u de eigenschappen van een component bewerken. De eigenschappen veranderen afhankelijk van een component. Eigenschappen van de container van het Adaptief formulier weergeven:

   Selecteer een component en tik vervolgens op ![op veldniveau](assets/Smock_SelectContainer_18_N.svg) > **[!UICONTROL Adaptive Form Container]** en tikt u vervolgens op ![eigenschappen](assets/Smock_Wrench_18_N.svg).

* **Bandenbrowser**

   Hiermee kunt u verschillende typen inhoud segmenteren, zoals afbeeldingen, documenten, pagina&#39;s, films, enzovoort.

* **Browser voor componenten**

   Bevat componenten die u kunt gebruiken om een adaptief formulier te maken. U kunt componenten van naar het Aangepaste formulier slepen om formulierelementen toe te voegen en toegevoegde elementen te configureren volgens de vereisten. In de volgende tabel worden de componenten beschreven die in de componentbrowser worden weergegeven.

<table>
 <tbody>
  <tr>
   <th><strong>Component</strong></th>
   <th><strong>Functionaliteit</strong></th>
  </tr>
  <tr>
   <td>Adobe Sign Block</td>
   <td>Voegt een blok tekst met plaatsaanduidingen toe voor velden die moeten worden ingevuld tijdens het ondertekenen met Adobe Sign.</td>
  </tr>
  <tr>
   <td>Knop</td>
   <td>Voegt een knoop toe, die u kunt vormen om acties uit te voeren, zoals sparen, terugstellen, volgende gaan, vorige gaan, etc.</td>
  </tr>
  <tr>
   <td>Captcha</td>
   <td>Voegt CAPTCHA-validatie toe met de Google reCAPTCHA-service.</td>
  </tr>
  <tr>
   <td>Diagram</td>
   <td>Hiermee voegt u een grafiek toe die u kunt gebruiken in Adaptief Forms en documenten voor een visuele weergave van tweedimensionale gegevens in herhaalbare deelvensters en tabelrijen.</td>
  </tr>
  <tr>
   <td>Selectievakje</td>
   <td>Hiermee wordt een selectievakje toegevoegd.</td>
  </tr>
  <tr>
   <td>Datuminvoerveld</td>
   <td>Gebruik de component Datuminvoerveld in het formulier, zodat klanten dag, maand en jaar afzonderlijk in drie vakken kunnen invullen. U kunt de vormgeving van de component aanpassen en de datumnotatie wijzigen. U kunt uw klanten bijvoorbeeld datums laten invoeren in de notatie MM/DD/JJJJ of DD/MM/JJJJ.</td>
  </tr>
  <tr>
   <td>Datumkiezer</td>
   <td>Hiermee voegt u een kalender-veld toe waarin een datum wordt gekozen.</td>
  </tr>
  <tr>
   <td>Documentfragment</td>
   <td>Hiermee kunt u herbruikbare componenten van een correspondentie toevoegen.</td>
  </tr>
  <tr>
   <td>Fragmentgroep document</td>
   <td>Hiermee kunt u een groep gerelateerde documentfragmenten toevoegen die u in een lettertypesjabloon als één eenheid kunt gebruiken.</td>
  </tr>
  <tr>
   <td>Vervolgkeuzelijst</td>
   <td>Hiermee voegt u een vervolgkeuzelijst toe: één of meerdere selecties</td>
  </tr>
  <tr>
   <td>E-mail</td>
   <td><p>Hiermee voegt u een veld toe waarin u het e-mailadres kunt vastleggen. De component Email valideert standaard e-mailadressen met de volgende reguliere expressie.</p> <p><code>^[a-zA-Z0-9.!#$%&amp;’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:.[a-zA-Z0-9-]+)*$</code></p> </td>
  </tr>
  <tr>
   <td>Bestandsbijlage</td>
   <td><p>Hiermee voegt u een knop toe waarmee gebruikers door ondersteunende documenten kunnen bladeren en deze aan een formulier kunnen toevoegen.</p> <p><strong>Opmerking: </strong>De component Bestandsbijlage ondersteunt een vooraf gedefinieerde set bestandsindelingen in Adaptive Forms ingeschakeld voor Adobe Sign. Zie voor meer informatie <a href="https://helpx.adobe.com/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text">Ondersteunde bestandsindelingen</a>.</p> </td>
  </tr>
  <tr>
   <td>Lijst met bestandsbijlagen</td>
   <td>Hiermee voegt u een veld toe met alle bijlagen die zijn geüpload met de component Bestandsbijlage.</td>
  </tr>
  <tr>
   <td>Voettekst<br /> </td>
   <td>Hiermee voegt u de koptekst van de pagina toe, die doorgaans het logo van een bedrijf, de titel van het formulier en het overzicht bevat.<br /> </td>
  </tr>
  <tr>
   <td>Koptekst</td>
   <td>Hiermee voegt u de voettekst van de pagina toe die meestal copyrightinformatie en koppelingen naar andere pagina's bevat. </td>
  </tr>
  <tr>
   <td>Afbeelding</td>
   <td>Hiermee kunt u een afbeelding invoegen.</td>
  </tr>
  <tr>
   <td>Afbeeldingskeuze</td>
   <td>Hiermee kunnen uw klanten een afbeelding selecteren die informatie verschaft. U kunt de informatie gebruiken om de gepersonaliseerde diensten aan uw klanten te verlenen.</td>
  </tr>
  <tr>
   <td>Volgende knop</td>
   <td>Hiermee voegt u een knop toe waarmee u naar het volgende venster in een formulier kunt navigeren.</td>
  </tr>
  <tr>
   <td>Numeriek vak</td>
   <td>Hiermee wordt een veld toegevoegd voor het vastleggen van numerieke waarden</td>
  </tr>
  <tr>
   <td>Numerieke stap</td>
   <td>Gebruik Numerieke Stepper in uw formulier om uw klanten een numerieke waarde te laten invoeren die ze op basis van een vooraf gedefinieerde stap kunnen verhogen of verlagen.</td>
  </tr>
  <tr>
   <td>Deelvenster</td>
   <td><p>Hiermee voegt u een deelvenster of subdeelvenster toe.</p> <p>U kunt ook een deelvenstercomponent toevoegen vanaf de werkbalk van het bovenliggende deelvenster met de opdracht <span class="uicontrol">Deelvenster Onderliggend element toevoegen</code> knop. Op dezelfde manier kunt u een paneelspecifieke toolbar toevoegen gebruikend <span class="uicontrol">Werkbalk Deelvenster toevoegen</code> knop. U kunt de positie van de paneelwerkbalk configureren met behulp van het dialoogvenster Deelvenster bewerken.</code></code></p> </td>
  </tr>
  <tr>
   <td>Wachtwoordvak</td>
   <td>Hiermee voegt u een veld toe waarin u een wachtwoord kunt vastleggen.</td>
  </tr>
  <tr>
   <td>Vorige knop</td>
   <td>Hiermee voegt u een knop toe die gebruikers nodig hebben om terug te gaan naar de vorige pagina of het vorige deelvenster.</td>
  </tr>
  <tr>
   <td>Keuzerondje</td>
   <td>Hiermee voegt u keuzerondjes toe.</td>
  </tr>
  <tr>
   <td>Knop Opnieuw instellen</td>
   <td>Hiermee voegt u een knop toe waarmee u formuliervelden opnieuw kunt instellen.</td>
  </tr>
  <tr>
   <td>Knop Opslaan</td>
   <td>Hiermee voegt u een knop toe om formuliergegevens op te slaan.</td>
  </tr>
  <tr>
   <td>Krabbelhandtekening</td>
   <td>Hiermee voegt u een veld voor het vastleggen van scripthandtekeningen toe.</td>
  </tr>
  <tr>
   <td>Scheidingsteken</td>
   <td>Hiermee schakelt u visuele segregatie van deelvensters in het formulier in.</td>
  </tr>
  <tr>
   <td>Handtekeningstap</td>
   <td>Hiermee geeft u de informatie weer die in het formulier en de handtekeningvelden is opgegeven, zodat de gebruiker het formulier kan verifiëren en ondertekenen.</td>
  </tr>
  <tr>
   <td>Tekst</td>
   <td>Hiermee kunt u statische tekst opgeven.</td>
  </tr>
  <tr>
   <td>Verzendknop</td>
   <td>Hiermee voegt u een verzendknop toe om het formulier naar de geconfigureerde handeling Verzenden te verzenden.</td>
  </tr>
  <tr>
   <td>Samenvattingsstap</td>
   <td>Hiermee verzendt u het formulier en de samenvattingstekst die de auteurs opgeven nadat het formulier is verzonden. </td>
  </tr>
  <tr>
   <td>Overschakelen</td>
   <td>Voegt een schakelaar toe die een knevel uitvoert of laat/onbruikbaar maakt actie toe. U kunt niet meer dan twee opties in de component van de Schakelaar toevoegen. Aangezien een schakelaar slechts twee waarden kan hebben: Aan of Uit, verplicht is niet van toepassing. Er wordt minstens één waarde opgeslagen, ongeacht de gebruikersinvoer. <br /> </td>
  </tr>
  <tr>
   <td>Tabel</td>
   <td>Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. </td>
  </tr>
  <tr>
   <td>Telefoon</td>
   <td><p>Hiermee voegt u een veld toe waarin u het telefoonnummer kunt vastleggen. De component van de Telefoon staat auteurs toe om één van de volgende types van telefoonaantal te vormen. Elk type is gekoppeld aan een standaardreguliere expressie voor validatie.</p>
    <ul>
     <li>Type International wordt gevalideerd door <code>^[+][0-9]{0,14}$</code>.</li>
     <li>Type USPhoneNumber wordt gevalideerd door <code>{'+1 ('999') '999-9999}</code>.</li>
     <li>Type UKPhoneNumber wordt gevalideerd door <code>text{'+'99 999 999 9999}</code>.</li>
     <li>Aangepast type biedt geen standaard validatiepatroon. Het neemt de waarde van het laatste geselecteerde type van telefoonaantal. U kunt ook uw eigen aangepaste validatiepatroon opgeven.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Voorwaarden en bepalingen<br /> </td>
   <td>Hiermee voegt u een veld toe waarin auteurs de voorwaarden kunnen opgeven die gebruikers kunnen bekijken voordat ze het formulier invullen.</td>
  </tr>
  <tr>
   <td>Tekstvak </td>
   <td><p>Voegt een tekstvak toe waarin een gebruiker de vereiste informatie kan opgeven. </p> <p>Standaard accepteert de component Tekstvak alleen onbewerkte tekst. U kunt een component van de Doos van de Tekst toelaten om RTF goed te keuren. Een tekstcomponent met RTF-functionaliteit biedt opties voor het toevoegen van kopteksten, het wijzigen van tekenstijlen (vet, cursief, onderstrepen van tekens), het maken van geordende en ongeordende lijsten, het wijzigen van de tekstachtergrond en tekstkleur en het toevoegen van hyperlinks. Als u RTF-tekst wilt inschakelen voor een tekstvak, schakelt u de optie<strong> RTF-tekst toestaan</strong> in de componenteigenschappen.</p> </td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>Hiermee geeft u een titel op voor het adaptieve formulier.</td>
  </tr>
  <tr>
   <td>Stap verifiëren</td>
   <td><p>Hiermee voegt u een tijdelijke aanduiding toe waarmee het ingevulde formulier wordt weergegeven ter verificatie door de gebruiker.</p> <p><strong>Opmerking</strong>: Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook afgeraden de component Verify te gebruiken in een adaptief formulierfragment.</p> </td>
  </tr>
 </tbody>
</table>

### Pagina, werkbalk {#page-toolbar}

De pagina-werkbalk boven in het scherm bevat opties waarmee u een voorbeeld van het formulier kunt bekijken, de eigenschappen van het formulier kunt wijzigen en de indeling van het formulier kunt bewerken. U kunt een voorbeeld van het formulier bekijken wanneer u het maakt en wijzigingen aanbrengen. In de paginabooltoolbar, ziet u:

* **Zijpaneel in-/uitschakelen** ![schakelen tussen zijpaneel](assets/Smock_RailLeft_18_N.svg): Hiermee kunt u Zijbalk tonen of verbergen.

* **Pagina-informatie** ![thema-opties](assets/Smock_Properties_18_N.svg): Hiermee kunt u pagina-eigenschappen weergeven, een formulier publiceren/publiceren, een formulierwerkstroom starten en het formulier openen in een klassieke gebruikersinterface.

* **Emulator** ![liniaal](assets/Smock_Devices_18_N.svg): Hiermee kunt u het uiterlijk van een formulier emuleren voor verschillende weergavegrootten, zoals tablets en telefoons.

* **Bewerken**: Hiermee kunt u andere modi selecteren, zoals: **[!UICONTROL Edit]**, **[!UICONTROL Style]**, **[!UICONTROL Developer]**, en **[!UICONTROL Design]**.

   * **Bewerken**: Hiermee kunt u de eigenschappen van het formulier en de componenten ervan bewerken. U kunt bijvoorbeeld een component toevoegen, een afbeelding neerzetten en verplichte velden opgeven.
   * **Stijl**: Hiermee kunt u de vormgeving van componenten van het formulier opmaken. In de stijlmodus kunt u bijvoorbeeld een deelvenster selecteren en de achtergrondkleur ervan opgeven.

   * **Ontwikkelaar**: Hiermee kan een ontwikkelaar:

      * Ontdek waaruit de formulieren bestaan.
      * Foutopsporing waar en wanneer gebeurt, wat weer helpt om problemen op te lossen.

      * **Ontwerp**. Hiermee kunt u aangepaste componenten, of componenten buiten het vak die niet in het zijpaneel staan, in- of uitschakelen.

* **Voorvertoning**: Hiermee kunt u een voorbeeld bekijken van de weergave van het formulier wanneer u het publiceert.

### Component, werkbalk {#component-toolbar}

![Component-werkbalk in de aanraakinterface](assets/component-toolbar.png)

Wanneer u een component selecteert, ziet u een werkbalk waarin u de component kunt bewerken. U krijgt opties om, eigenschappen van de componenten te snijden te kleven, te bewegen en te specificeren. U kunt kiezen uit de volgende opties:

A.**Configureren**: Wanneer u tikt **[!UICONTROL Configure]**, zijn componenteigenschappen zichtbaar in de zijbalk. Als u deze eigenschappen configureert, kunt u de ervaring voor het vastleggen van gegevens aanpassen. U kunt de elementnaam van de component wijzigen en de labeltekst opgeven in het veld Titel van de component. Met elementnaam kunt u waarden vastleggen die gebruikers invoeren met de component. In de componenteigenschappen geeft u het gedrag van de component op en beheert u de gebruikersinvoer. Configureer eigenschappen in de zijbalk om gebruikersgegevens vast te leggen en te gebruiken voor verdere verwerking. Met de eigenschappen voor de container Adaptief formulier kunt u clientbibliotheken, indelingen, thema&#39;s, Document of Record-instellingen, opslaginstellingen, verzendinstellingen en metagegevensinstellingen opgeven.

B.**Kopiëren**: Met de optie Kopiëren kunt u een component kopiëren en op andere plaatsen in het formulier plakken. Wanneer u een component plakt, krijgt de geplakte component een nieuwe elementnaam maar behoudt deze de eigenschappen van de gekopieerde component.

C.**Knippen**: Met de optie Knippen kunt u een component in het adaptieve formulier van de ene naar de andere plaats verplaatsen.

D. **Verwijderen**: Hiermee kunt u de component uit het formulier verwijderen.

E. **Invoegen**: Hiermee kunt u een component invoegen boven de geselecteerde component.

F. **Plakken**: Hiermee kunt u de component die u hebt geknipt of gekopieerd, plakken met de hierboven beschreven opties.

G. **Regels bewerken**: Hiermee opent u de regeleditor. Voor meer informatie, <!-- see [Rule Editor](rule-editor.md). -->

H. **Groep**: Hiermee kunt u meerdere componenten selecteren als u meerdere componenten tegelijk wilt knippen, kopiëren of plakken.

I. **Bovenliggend**: Hiermee kunt u het bovenliggende element van een component selecteren. Een tekstveld bevindt zich bijvoorbeeld binnen een subsectie, die zich in een sectie bevindt. De sectie bevindt zich in het hoofddeelvenster van de hulplijn en de container van het adaptieve formulier is de bovenliggende laag van een hoofddeelvenster van de hulplijn. Voor een component, kunt u alle opties zien met hiërarchie gesorteerd onderaan-op.

Als u bijvoorbeeld tikt **[!UICONTROL Parent]** voor een tekstvak ziet u :

* Onderafdeling
* Sectie
* guideRootPanel
* Container voor adaptieve vorm

J. **Overige**: Biedt meer opties voor het werken met de geselecteerde component.

* SOM-expressie weergeven
* Een deelvenster opslaan als fragment (alleen voor deelvensters)
* Onderliggend deelvenster toevoegen (alleen voor deelvensters)
* Deelvensterwerkbalk toevoegen (alleen voor deelvensters)
* Vervangen (niet voor deelvensters)

### Pagina Adaptief formulier {#af-page}

De pagina Adaptief formulier is het daadwerkelijke formulier. Het is als elke andere WCM pagina die als WCM wordt gemodelleerd `cq:Page` component. In de volgende afbeelding ziet u de inhoudsstructuur van een typisch adaptief formulier.

![Inhoudsstructuur van een Adaptief formulier-WCM-pagina](assets/afstructure.png)

De inhoudsstructuur bevat doorgaans de volgende primaire componenten:

* **guideContainer**: De basis van een adaptief formulier, dat is gemarkeerd als **[!UICONTROL Start of Adaptive Form]** in de interface voor adaptief formulier. In deze component kunt u het volgende opgeven:

   * *Mobiele lay-out van het adaptieve formulier*: Hiermee definieert u de weergave van het formulier op mobiele apparaten.
   * *Pagina Bedankt*: Hiermee definieert u de pagina waarop de gebruiker na het verzenden van het formulier wordt omgeleid.
   * *Handeling verzenden*: Hiermee bepaalt u hoe het formulier op de server wordt verwerkt wanneer de gebruiker het formulier verzendt.
   * *Stijlen*: Hiermee geeft u het pad op naar het CSS-bestand dat wordt gebruikt om de weergave van het formulier aan te passen.

* **rootPanel:** Het hoofdvenster van een adaptief formulier. Het kan subdeelvensters onder de puntenknoop bevatten. Aan elk deelvenster, inclusief het hoofddeelvenster, kan een lay-out zijn gekoppeld. De indeling van het deelvenster bepaalt hoe het formulier wordt opgemaakt. In de schermindeling Accordeon worden de items ervan bijvoorbeeld ingedeeld als Accordion-stappen.

* **werkbalk:** Een container voor adaptieve formulieren heeft een bijbehorende algemene werkbalk, die algemeen is voor het formulier. Deze werkbalk kan worden toegevoegd met de opdracht **[!UICONTROL Add Toolbar]** in de bewerkbalk. Hiermee kunnen auteurs handelingen toevoegen, zoals Verzenden, Opslaan, Herstellen, enzovoort.

* **activa:** Dit knooppunt bevat aanvullende informatie die wordt gebruikt voor het ontwerpen van formulieren. Bijvoorbeeld details van het formuliermodel, lokalisatiedetails, enzovoort.
