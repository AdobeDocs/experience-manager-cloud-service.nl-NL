---
title: Ervaar fragmenten
description: Met Adobe Experience Manager kunt u uw ervaringen herbruikbaar en flexibel maken.
translation-type: tm+mt
source-git-commit: b7a2e86de27dbfcdecaf3a2bc1984678b7b69375

---


# Ervaar fragmenten {#experience-fragments}

In Adobe Experience Manager als Cloud Service, een Experience Fragment:
* is een groep van een of meer componenten
* omvat zowel inhoud als lay-out
* kan worden verwezen binnen pagina&#39;s
* kan elke component bevatten

Een ervaringsfragment:

* Maakt deel uit van een ervaring (pagina).
* Kan op meerdere pagina&#39;s worden gebruikt.
* Is gebaseerd op een malplaatje (editable slechts) om structuur en componenten te bepalen.
* Bestaat uit een of meer componenten, met layout, in een alineasysteem.
* Kan andere ervaringsfragmenten bevatten.
* Kan worden gecombineerd met andere componenten (waaronder andere Experience Fragments) om een volledige pagina (ervaring) te vormen.
* Kan verschillende variaties hebben, die inhoud en/of componenten kunnen delen.
* Kan worden opgedeeld in bouwstenen die kunnen worden gebruikt voor meerdere variaties van het fragment.

U kunt Experience Fragments gebruiken:

* Als een auteur onderdelen (een fragment van een ervaring) van een pagina opnieuw wil gebruiken.
Zonder Fragments van de Ervaring, zou de auteur dat fragment moeten kopiëren en kleven. Het maken en onderhouden van deze kopiëren/plakken-ervaringen kost veel tijd en is vaak het gevolg van gebruikersfouten.
De Fragmenten van de ervaring elimineren de behoefte aan exemplaar/deeg.
* Om het hoofdloze gebruik-geval CMS te steunen.
Auteurs willen AEM alleen gebruiken voor ontwerpen, maar niet voor levering aan de klant. Een systeem/aanraakpunt van derden zou deze ervaring gebruiken en vervolgens leveren aan de eindgebruiker.

>[!NOTE]
>
>Schrijf toegang voor ervaringsfragmenten vereist dat de gebruikersaccount in de groep wordt geregistreerd:
>
>* `experience-fragments-editors`
>
>
Neem contact op met de systeembeheerder als er problemen optreden.

## Wanneer moet u ervaringsfragmenten gebruiken? {#when-should-you-use-experience-fragments}

Er moeten ervaringsfragmenten worden gebruikt:

* Wanneer u ervaringen wilt hergebruiken.
   * Ervaringen die opnieuw worden gebruikt met dezelfde of vergelijkbare inhoud.
* Wanneer u AEM gebruikt als platform voor het leveren van inhoud voor derden.
   * Elke oplossing die AEM als platform voor de levering van inhoud wil gebruiken.
   * Inhoud insluiten in aanraakpunten van derden.
* Als u ervaring hebt met verschillende variaties of uitvoeringen.
   * Kanaal- of contextspecifieke variaties.
   * ervaring die zinvol is om te groeperen; bijvoorbeeld een campagne met verschillende ervaringen op verschillende kanalen.
* Wanneer u Omnichannel Commerce gebruikt.
   * Deel commerciële inhoud op schaal op [sociale media](/help/implementing/developing/extending/experience-fragments.md#social-variations) .
   * Aanraakpunten transactioneel maken.

## Fragmenten voor uw ervaring ordenen {#organizing-your-experience-fragments}

Het wordt aanbevolen:
* mappen gebruiken om uw fragmenten van de ervaring te ordenen,

* [configureer de toegestane sjablonen voor deze mappen](#configure-allowed-templates-folder).

Door mappen te maken kunt u:

* een zinvolle structuur voor uw ervaringsfragmenten maken; bijvoorbeeld volgens classificatie

   >[!NOTE]
   >
   >U hoeft de structuur van uw ervaringsfragmenten niet uit te lijnen met de paginastructuur van uw site.

* [de toegestane sjablonen toewijzen op mapniveau](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >U kunt de [sjablooneditor](/help/sites-cloud/authoring/features/templates.md) gebruiken om uw eigen sjabloon te maken.

Het WKND-project bouwt een aantal ervaringsfragmenten op basis van `Contributors`. De gebruikte structuur illustreert ook hoe andere functies, zoals beheer voor meerdere sites (inclusief taalkopieën), kunnen worden gebruikt.

Zie:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Mappen voor ervaringsfragmenten](/help/sites-cloud/authoring/assets/xf-folders.png)

## Het creëren van en het Vormen van een Omslag voor uw Fragmenten van de Ervaring {#creating-and-configuring-a-folder-for-your-experience-fragments}

Om een omslag voor uw Fragments van de Ervaring tot stand te brengen en te vormen wordt het geadviseerd:

1. [Maak een map](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-folder).

1. [Configureer de toegestane sjablonen voor ervaringsfragmenten voor die map](#configure-allowed-templates-folder).

>[!NOTE]
>
>Het is ook mogelijk om de [Toegestane Malplaatjes voor uw instantie](#configure-allowed-templates-instance)te vormen, maar deze methode wordt **niet** geadviseerd aangezien de waarden op verbetering kunnen worden beschreven.

### Configureer de toegestane sjablonen voor uw map {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dit is de geadviseerde methode om de **Toegestane Malplaatjes** te specificeren, aangezien de waarden niet op verbetering zullen worden beschreven.

1. Navigeer naar de map met vereiste **ervaringsfragmenten** .

1. Selecteer de map en vervolgens **Eigenschappen**.

1. Geef de reguliere expressie op voor het ophalen van de vereiste sjablonen in het veld **Toegestane sjablonen** .

   Bijvoorbeeld:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Zie:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Ervaar fragmenteigenschappen - Toegestane sjablonen](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Zie [Sjablonen voor ervaringsfragmenten](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor meer informatie.

1. Selecteer **Opslaan en Sluiten**.

### Vorm de Toegestane Malplaatjes voor uw Instantie {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Het wordt afgeraden de **toegestane sjablonen** met deze methode te wijzigen, omdat de opgegeven sjablonen tijdens de upgrade kunnen worden overschreven.
>
>Gebruik dit dialoogvenster alleen ter informatie.

1. Navigeer naar de vereiste **console van Fragments** van de Ervaring.

1. Selecteer **configuratieopties**:

   ![Knop Configuratie](/help/sites-cloud/authoring/assets/xf-18.png)

1. Geef de vereiste sjablonen op in het dialoogvenster Fragmenten **voor ervaring** configureren:

   ![Fragmenten voor ervaring configureren](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Zie [Sjablonen voor ervaringsfragmenten](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor meer informatie.

1. Selecteer **Opslaan**.


## Een ervaringsfragment maken {#creating-an-experience-fragment}

Een ervaringsfragment maken:

1. Selecteer Fragmenten **van de** Ervaring van de Globale Navigatie.

   ![Ervaar fragmenten in het navigatievenster](/help/sites-cloud/authoring/assets/xf-01.png)

1. Navigeer naar de gewenste map en selecteer **Maken**:

   ![Een map maken voor Experience Fragments](/help/sites-cloud/authoring/assets/xf-02.png)

1. Selecteer Fragment **van de** Ervaring om de **Create tovenaar van het Fragment** van de Ervaring te openen.

   Selecteer de vereiste **sjabloon** en **kies Volgende**:

   ![Een ervaringsfragmentsjabloon selecteren](/help/sites-cloud/authoring/assets/xf-03.png)


1. Voer de **eigenschappen** in voor het **ervaringsfragment**.

   Een **titel** is verplicht. Als de **naam** leeg blijft, wordt deze afgeleid van de **titel**.

   ![Ervaar fragmenteigenschappen](/help/sites-cloud/authoring/assets/xf-04.png)

1. Klik op **Maken**.

   Er wordt een bericht weergegeven. Selecteer:

   * **Gereed** om terug te keren naar de console
   * **Openen** om de fragmenteditor te openen

## Uw ervaringsfragment bewerken {#editing-your-experience-fragment}

De Experience Fragment Editor biedt u vergelijkbare mogelijkheden als de normale pagina-editor.

>[!NOTE]
>
>Zie Pagina-inhoud [](/help/sites-cloud/authoring/fundamentals/editing-content.md) bewerken voor meer informatie over het gebruik van de pagina-editor.

De volgende voorbeeldprocedure laat zien hoe u een gummetje voor een product kunt maken:

1. Sleep de vereiste component vanuit de [Componentbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

1. Afhankelijk van de component:
   * Voeg naar wens inhoud en/of elementen toe.
   * Configureer de eigenschappen naar wens.

1. Voeg desgewenst meer componenten toe.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Ervaar fragment op pagina](/help/sites-cloud/authoring/assets/xf-05.png)

## Een ervaringsfragmentvariatie maken {#creating-an-experience-fragment-variation}

U kunt variaties van uw Fragment van de Ervaring tot stand brengen, afhankelijk van uw behoeften:

1. Open het fragment om het te [bewerken](#editing-your-experience-fragment).
1. Open het tabblad **Variaties** .

   ![Een Experience Fragment-wijziging maken](/help/sites-cloud/authoring/assets/xf-06.png)

1. **Met Maken** kunt u:

   * **Variatie**
   * **Variatie als live-kopie**.

1. Definieer de vereiste eigenschappen:

   * **Sjabloonmodel**
   * **Titel**
   * **Naam** - indien leeg gelaten, wordt deze afgeleid van de titel
   * **Beschrijving**
   * **Variatietags**
   Bijvoorbeeld:

   ![Variatie-eigenschappen](/help/sites-cloud/authoring/assets/xf-07.png)

1. Bevestig met **Gereed**, de nieuwe variatie zal in het paneel worden getoond.

## Uw ervaringsfragment gebruiken {#using-your-experience-fragment}

U kunt het fragment van de Ervaring nu gebruiken wanneer het ontwerpen van uw pagina&#39;s:

1. Open een pagina om te bewerken.

1. Maak een instantie van de component Experience Fragment in het paginalineasysteem:

1. Voeg het daadwerkelijke fragment van de Ervaring aan de componenteninstantie toe; ofwel:

   * Sleep het vereiste fragment uit de middelenbrowser en zet het neer op de component.
   * Selecteer **Vorm** van de componententoolbar en specificeer het te gebruiken fragment, bevestig met **Gedaan**.
   >[!NOTE]
   >
   >Bewerken werkt op de werkbalk van de component als een sneltoets waarmee het fragment in de fragmenteditor wordt geopend.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Ervaar het fragment in de Pagina-editor](/help/sites-cloud/authoring/assets/xf-08.png)

## Building Blocks {#building-blocks}

U kunt een of meer componenten selecteren om een bouwsteen voor recycling binnen uw fragment te maken:

### Een bouwblok maken {#creating-a-building-block}

Een nieuw bouwblok maken:

1. In de redacteur van het Fragment van de Ervaring, selecteer de componenten u wilt hergebruiken:

   ![Component selecteren voor bouwblok](/help/sites-cloud/authoring/assets/xf-09.png)

1. Selecteer op de werkbalk Componenten de optie **Omzetten in bouwsteen**:

   ![Knop Gebouwd blok](/help/sites-cloud/authoring/assets/xf-10.png)

1. Voer de naam van het **bouwblok** in en bevestig dit met **Omzetten**:

   ![Naambouwblok](/help/sites-cloud/authoring/assets/xf-11.png)

1. Het **bouwblok** wordt weergegeven op het linkertabblad (**Lokaal**) en kan worden geselecteerd voor verdere actie:

   ![Bouwblok in de spoorstaaf](/help/sites-cloud/authoring/assets/xf-12.png)

#### Een bouwblok beheren {#managing-a-building-block}

Uw bouwsteen is zichtbaar in de Blokken van de **Bouwstijl** tabel. Voor elk blok zijn de volgende acties beschikbaar:

* **Ga naar stramien**: de hoofdvariant openen op een nieuw tabblad
* **Naam wijzigen**
* **Verwijderen**

![Gebouwenblokken beheren](/help/sites-cloud/authoring/assets/xf-13.png)

#### Een bouwsteen gebruiken {#using-a-building-block}

U kunt de bouwsteen naar het alineasysteem van om het even welk fragment slepen, zoals met om het even welke component.

Als u een Experience Fragment bewerkt, worden de beschikbare bouwstenen weergegeven op het tabblad Left-hanf. U kunt filteren op basis van:

* **Lokaal** - Blokken maken op basis van het huidige ervaringsfragment
* **Alles** - Blokken maken van alle fragmenten

![Bouwblokken selecteren](/help/sites-cloud/authoring/assets/xf-14.png)

## Details van uw ervaringsfragment {#details-of-your-experience-fragment}

Details van het fragment kunt u zien:

1. Navigeer naar de locatie van uw ervaringsfragmenten (navigeer niet verder naar beneden naar de variaties in het fragment).
De details worden getoond in alle meningen van de console van de Fragmenten **van de** Ervaring, met de Mening **van de** Lijst met details van het uitvoeren naar Doel: <!--Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an [export to Target](/help/sites-administering/experience-fragments-target.md):-->

   ![Ervaar fragmentdetails](/help/sites-cloud/authoring/assets/xf-15.png)

1. Wanneer u de **eigenschappen** van het ervaringsfragment opent:

   ![Eigenschappen, knop](/help/sites-cloud/authoring/assets/xf-16.png)

   De eigenschappen zijn beschikbaar op verschillende tabbladen:

   >[!CAUTION]
   >
   >Deze lusjes worden getoond wanneer u **Eigenschappen** van de console van de Fragmenten van de Ervaring opent.
   >
   >Als u Eigenschappen **** opent tijdens het bewerken van een Ervingsfragment, worden de juiste [Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) weergegeven.

   ![Ervaar fragmenteigenschappen](/help/sites-cloud/authoring/assets/xf-17.png)

   * **Basis**
      * **Titel** - verplicht
      * **Beschrijving**
      * **Tags**
      * **Totaal aantal varianten** - alleen informatie
      * **Aantal webvarianten** - alleen informatie
      * **Aantal niet-webvarianten** - alleen informatie
      * **Aantal pagina&#39;s dat dit fragment** gebruikt - alleen informatie
   * **Cloud Services**
      * **Cloud Configuration**
      * **Cloud Service Configurations**
      * **Facebook-pagina-id**
      * **Pinterest board**
   * **Verwijzingen**
      * Een lijst met verwijzingen
   * **Status van sociale media**
      * Details van variaties in sociale media

## De normale HTML-uitvoering {#the-plain-html-rendition}

Met de `.plain.` kiezer in de URL hebt u vanuit de browser toegang tot de onbewerkte HTML-uitvoering.

>[!NOTE]
>
>Hoewel dit direct beschikbaar is vanuit de browser, is [het primaire doel dat andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang krijgen tot de inhoud van het Experience Fragment door alleen de URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition)te gebruiken.

## Exporteren van ervaringsfragmenten {#exporting-experience-fragments}

Experience Fragments worden standaard geleverd in de HTML-indeling. Dit kan zowel door AEM als derdekanalen worden gebruikt.

Voor exporteren naar Adobe Target kan JSON ook worden gebruikt. Zie Doelintegratie met de Fragmenten van de Ervaring voor volledige informatie. <!--For export to Adobe Target, JSON can also be used. See [Target Integration with Experience Fragments](/help/sites-administering/experience-fragments-target.md) for full information.-->
