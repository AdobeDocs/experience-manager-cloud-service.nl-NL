---
title: Ervaar fragmenten
description: Met Experience Fragments in Adobe Experience Manager as a Cloud Service kunt u uw ervaringen herbruikbaar en flexibel maken.
exl-id: 9dc33677-141f-47e5-a01e-6c7488686314
solution: Experience Manager Sites
feature: Authoring, Experience Fragments
role: User
source-git-commit: 7adfe0ca7fbab1f8a5bd488e524a48be62584966
workflow-type: tm+mt
source-wordcount: '2099'
ht-degree: 2%

---

# Ervaar fragmenten {#experience-fragments}

In Adobe Experience Manager as a Cloud Service:

* is een groep van een of meer componenten
* omvat zowel inhoud als lay-out
* kan worden verwezen binnen pagina&#39;s
* kan elke component bevatten

Een ervaringsfragment:

* Maakt deel uit van een ervaring (pagina).
* Kan op meerdere pagina&#39;s worden gebruikt (die zijn gebaseerd op bewerkbare sjablonen).
* Is gebaseerd op een malplaatje (editable slechts) om structuur en componenten te bepalen.
* Dit malplaatje wordt gebruikt om de *wortelpagina* van het Fragment van de Ervaring tot stand te brengen.
* Bestaat uit een of meer componenten, met layout, in een alineasysteem.
* Kan andere ervaringsfragmenten bevatten.
* Kan worden gecombineerd met andere componenten (waaronder andere Experience Fragments) om een volledige pagina (ervaring) te vormen.
* Een of meer variaties kunnen worden gemaakt op basis van de basispagina.
* Deze variaties kunnen inhoud en/of componenten delen.
* Kan worden opgedeeld in bouwstenen die kunnen worden gebruikt voor meerdere variaties van het fragment.

U kunt Experience Fragments gebruiken:

* Als een auteur onderdelen (een fragment van een ervaring) van een pagina opnieuw wil gebruiken.
Zonder Fragments van de Ervaring, zou de auteur dat fragment moeten kopiëren en kleven. Het maken en onderhouden van deze kopiëren/plakken-ervaringen kost veel tijd en is vaak het gevolg van gebruikersfouten.
De Fragmenten van de ervaring elimineren de behoefte aan exemplaar/deeg.
* Om de hoofdloze CMS-use-case te ondersteunen.
Auteurs willen AEM alleen gebruiken voor ontwerpen, maar niet voor levering aan de klant. Een systeem/aanraakpunt van derden zou deze ervaring gebruiken en vervolgens leveren aan de gebruiker.
* Met [ Multisite Beheer (MSM) ](/help/sites-cloud/administering/msm/overview.md); als Fragment van de Ervaring maakt deel uit van een pagina. Dit geldt zowel voor de afzonderlijke fragmenten als voor de mappen waarin deze zich bevinden.

>[!NOTE]
>
>**[de Fragmenten van de Inhoud](/help/sites-cloud/authoring/fragments/content-fragments.md)** en **Fragmenten van de Ervaring** zijn verschillende eigenschappen binnen AEM:
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, cijfers en datums.
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Voor meer informatie, zie [ Begrip van de Fragmenten van de Inhoud en de Fragmenten van de Ervaring in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=nl-NL#content-fragments).

>[!NOTE]
>
>Schrijf toegang voor ervaringsfragmenten vereist dat de gebruikersaccount in de groep wordt geregistreerd:
>
>* `experience-fragments-editors`
>
>Neem contact op met de systeembeheerder als er problemen optreden.

## Wanneer moet u ervaringsfragmenten gebruiken? {#when-should-you-use-experience-fragments}

Er moeten ervaringsfragmenten worden gebruikt:

* Wanneer u ervaringen wilt hergebruiken.
   * Ervaringen die opnieuw worden gebruikt met dezelfde of vergelijkbare inhoud.
* Wanneer u AEM gebruikt als platform voor het leveren van inhoud voor derden.
   * Om het even welke oplossing die AEM als platform van de inhoudslevering wil gebruiken.
   * Inhoud insluiten in aanraakpunten van derden.
* Als u ervaring hebt met verschillende variaties of uitvoeringen.
   * Kanaal- of contextspecifieke variaties.
   * Ervaringen die zinvol zijn om te groeperen, bijvoorbeeld een campagne met verschillende ervaringen over verschillende kanalen.
* Wanneer u Omnichannel Commerce gebruikt.
   * Aanraakpunten transactioneel maken.

## Fragmenten voor uw ervaring ordenen {#organizing-your-experience-fragments}

Het wordt aanbevolen:
* mappen gebruiken om uw fragmenten van de ervaring te ordenen,

* [ vormt de toegestane malplaatjes op deze omslagen ](#configure-allowed-templates-folder).

Door mappen te maken kunt u:

* een zinvolle structuur voor uw ervaringsfragmenten maken, bijvoorbeeld volgens de classificatie

  >[!NOTE]
  >
  >U hoeft de structuur van uw ervaringsfragmenten niet uit te lijnen met de paginastructuur van uw site.

* [de toegestane sjablonen toewijzen op mapniveau](#configure-allowed-templates-folder)

  >[!NOTE]
  >
  >U kunt de [ malplaatjeredacteur ](/help/sites-cloud/authoring/page-editor/templates.md) gebruiken om uw eigen malplaatje tot stand te brengen.

Het WKND-project structureert een aantal Experience Fragments volgens `Contributors` . De gebruikte structuur illustreert ook hoe andere functies, zoals beheer voor meerdere sites (inclusief taalkopieën), kunnen worden gebruikt.

Zie:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![ Omslagen voor de Fragmenten van de Ervaring ](/help/sites-cloud/authoring/assets/xf-folders.png)

## Het creëren van en het Vormen van een Omslag voor uw Fragmenten van de Ervaring {#creating-and-configuring-a-folder-for-your-experience-fragments}

Om een omslag voor uw Fragments van de Ervaring tot stand te brengen en te vormen wordt het geadviseerd:

1. [ creeer een omslag ](/help/sites-cloud/authoring/sites-console/managing-pages.md#creating-a-new-folder).

1. [ vormt de toegestane malplaatjes van het Fragment van de Ervaring voor die omslag ](#configure-allowed-templates-folder).

>[!NOTE]
>
>Het is ook mogelijk om de [ Toegestane Malplaatjes voor uw instantie ](#configure-allowed-templates-instance) te vormen, maar deze methode wordt **niet** geadviseerd aangezien de waarden op verbetering kunnen worden beschreven.

### Configureer de toegestane sjablonen voor uw map {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dit is de geadviseerde methode om **Toegestane Malplaatjes** te specificeren, aangezien de waarden niet op verbetering zullen worden beschreven.

1. Navigeer aan de vereiste **omslag van de Fragmenten van de Ervaring**.

1. Selecteer de omslag, en dan **Eigenschappen**.

1. Specificeer de regelmatige uitdrukking voor het terugwinnen van de vereiste malplaatjes op het **Toegelaten gebied van Malplaatjes**.

   Bijvoorbeeld:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Zie:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![ Eigenschappen van het Fragment van de Ervaring - Toegestane Malplaatjes ](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Zie [ Malplaatjes voor de Fragmenten van de Ervaring ](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor verdere details.

1. Selecteer **sparen en Sluiten**.

### Vorm de Toegestane Malplaatjes voor uw Instantie {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Het wordt niet geadviseerd om **Toegestane Malplaatjes** door deze methode te veranderen, aangezien de gespecificeerde malplaatjes op verbetering kunnen worden beschreven.
>
>Gebruik dit dialoogvenster alleen ter informatie.

1. Navigeer aan de vereiste **console van de Fragmenten van de Ervaring**.

1. Selecteer **de opties van de Configuratie**:

   ![ knoop van de Configuratie ](/help/sites-cloud/authoring/assets/xf-18.png)

1. Specificeer de vereiste malplaatjes in **vormen de Fragmenten van de Ervaring** dialoog:

   ![ vorm de Fragmenten van de Ervaring ](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Zie [ Malplaatjes voor de Fragmenten van de Ervaring ](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor verdere details.

1. Selecteer **sparen**.

## Een ervaringsfragment maken {#creating-an-experience-fragment}

Een ervaringsfragment maken:

1. Selecteer **Fragmenten van de Ervaring** van de Globale Navigatie.

   ![ Fragmenten van de Ervaring in het paneel van de Navigatie ](/help/sites-cloud/authoring/assets/xf-01.png)

1. Navigeer aan de vereiste omslag en selecteer **creeer**:

   ![ Creërend een omslag voor de Fragmenten van de Ervaring ](/help/sites-cloud/authoring/assets/xf-02.png)

1. Selecteer **Fragment van de Ervaring** om **te openen creeer de tovenaar van het Fragment van de Ervaring**.

   Selecteer de vereiste **sjabloon** en kies vervolgens **Volgende**:

   ![ Selecterend een malplaatje van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/xf-03.png)


1. Voer de **Eigenschappen** voor uw **Experience-fragment** in.

   A **Titel** is verplicht. Als de **Naam** leeg wordt verlaten wordt het afgeleid uit de **Titel**.

   ![ de eigenschappen van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/xf-04.png)

   >[!NOTE]
   >
   >Labels uit de sjabloon Fragmentervaring worden niet samengevoegd met codes op de basispagina van dit ervaringsfragment.
   >
   >Deze zijn volledig gescheiden.

1. Klik **creëren**.

   Er wordt een bericht weergegeven. Selecteren:

   * **Gedaan** om aan de console terug te keren
   * **Open** om de fragmentredacteur te openen

## Uw ervaringsfragment bewerken {#editing-your-experience-fragment}

De Experience Fragment Editor biedt u vergelijkbare mogelijkheden als de normale pagina-editor.

>[!NOTE]
>
>Zie [ het Uitgeven van de Inhoud van de Pagina ](/help/sites-cloud/authoring/page-editor/edit-content.md) voor meer informatie over hoe te om de paginaredacteur te gebruiken.

De volgende voorbeeldprocedure laat zien hoe u een gummetje voor een product kunt maken:

1. De belemmering en laat vallen de vereiste component van [ Browser van Componenten ](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

1. Afhankelijk van de component:
   * Voeg naar wens inhoud en/of elementen toe.
   * Configureer de eigenschappen naar wens.

1. Voeg desgewenst meer componenten toe.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![ Fragment van de Ervaring op pagina ](/help/sites-cloud/authoring/assets/xf-05.png)

## Een ervaringsfragmentvariatie maken {#creating-an-experience-fragment-variation}

U kunt variaties van uw Fragment van de Ervaring tot stand brengen, afhankelijk van uw behoeften:

1. Open uw fragment voor [ het uitgeven ](#editing-your-experience-fragment).
1. Open het **lusje van Variaties**.

   ![ Creërend een variatie van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/xf-06.png)

1. **creeer** laat u tot stand brengen:

   * **Variatie**
   * **Verandering als levende-exemplaar**.

     >[!NOTE]
     >
     >Als u een initiële variatie maakt als Live kopie, wordt de titel overgenomen door de Source van Live kopie als de hoofdvariatie te gebruiken.

1. Definieer de vereiste eigenschappen:

   * **Malplaatje**
   * **Titel**
   * **Naam** - als verlaten leeg het uit de Titel wordt afgeleid
   * **Beschrijving**
   * **de markeringen van de Variatie**

   Bijvoorbeeld:

   ![ eigenschappen van de Variatie ](/help/sites-cloud/authoring/assets/xf-07.png)


1. Bevestig met **Gedaan**, wordt de nieuwe variatie getoond in het paneel.

## Uw ervaringsfragment gebruiken {#using-your-experience-fragment}

U kunt het fragment van de Ervaring nu gebruiken wanneer het ontwerpen van uw pagina&#39;s:

1. Open een pagina om te bewerken.

   >[!NOTE]
   >
   >De pagina moet zijn gebaseerd op een bewerkbare sjabloon.

1. Maak een instantie van de component Experience Fragment in het paginalineasysteem:

1. Voeg het daadwerkelijke Fragment van de Ervaring aan de componenteninstantie toe; of:

   * Sleep het vereiste fragment uit de Assets-browser en zet het neer op de component.
   * Selecteer **vormen** van de componententoolbar en specificeer het te gebruiken fragment, bevestig met **Gedaan**.

   >[!NOTE]
   >
   >Bewerken werkt op de werkbalk van de component als een sneltoets waarmee het fragment in de fragmenteditor wordt geopend.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![ Fragment van de Ervaring in de Redacteur van de Pagina ](/help/sites-cloud/authoring/assets/xf-08.png)

## Bouwstenen {#building-blocks}

U kunt een of meer componenten selecteren om een bouwsteen voor recycling binnen uw fragment te maken:

### Een bouwblok maken {#creating-a-building-block}

Een bouwblok maken:

1. In de redacteur van het Fragment van de Ervaring, selecteer de componenten u wilt hergebruiken:

   ![ Uitgezochte component voor het Blok van de Bouw ](/help/sites-cloud/authoring/assets/xf-09.png)

1. Van de componententoolbar, uitgezochte **Bekeerling aan bouwsteen**:

   ![ knoop van het Blok van de Bouw ](/help/sites-cloud/authoring/assets/xf-10.png)

1. Voer de naam van de **bouwsteen** in en bevestig dit met **Converteren**:

   ![ het Blok van de Bouw van de Naam ](/help/sites-cloud/authoring/assets/xf-11.png)

1. Het **Blok van de Bouw** wordt getoond in het linkerlusje (**Lokale**), en kan voor verdere actie worden geselecteerd:

   ![ Blok van de Bouw in spoorstaaf ](/help/sites-cloud/authoring/assets/xf-12.png)

#### Een bouwblok beheren {#managing-a-building-block}

Uw bouwsteen is zichtbaar in de **Blokken van de Bouw** tabel. Voor elk blok zijn de volgende acties beschikbaar:

* **ga naar meester**: open de variatie van de wortelpagina in een nieuw lusje
* **anders noemen**
* **Schrapping**

![ het Leiden de Blokken van de Bouw ](/help/sites-cloud/authoring/assets/xf-13.png)

#### Een bouwsteen gebruiken {#using-a-building-block}

U kunt de bouwsteen naar het alineasysteem van om het even welk fragment slepen, zoals met om het even welke component.

Als u een Experience Fragment bewerkt, worden de beschikbare bouwstenen weergegeven op het tabblad links. U kunt filteren op basis van:

* **Lokale** - de Blokken van de bouw van het huidige Fragment van de Ervaring
* **allen** - de Blokken van de bouw van alle fragmenten

![ het Selecteren van Bouwstenen ](/help/sites-cloud/authoring/assets/xf-14.png)

## Personalization op uw Experience Fragment {#personalization-experience-fragment}

Met Personalization op uw ervaringsfragment kunt u als een markeerteken één keer een doelpubliek voor het ervaringsfragment definiëren en het fragment vervolgens op elke pagina opnieuw gebruiken. Dit:

* hoeft u niet telkens wanneer het fragment wordt gebruikt, de vereiste variaties voor elk publiek op te geven
* handhaaft stijl over de aanbiedingen

U kunt een Experience Fragment maken met meerdere componenten die binnen dit ene fragment zijn gegroepeerd. U kunt ook variaties van het fragment maken voor elk specifiek publiekssegment en deze fragmenten van de Ervaring vervolgens opnieuw gebruiken voor alle vereiste kanalen.

Personalization wordt bereikt door de **Personalization** eigenschappen op of het Fragment of de variatie van de Ervaring, of de omslag te bepalen die de fragmenten bevat; dit betekent dat de overerving verpersoonlijkingseigenschappen kan met voeten treden.

Het vormen van deze eigenschappen laat ook de **het richten** wijze in de redacteur van het Fragment van de Ervaring toe.

### Personalization definiëren voor uw ervaringsfragment {#defining-personalization-experience-fragment}

Het fragment aanpassen:

1. Navigeer aan de vereiste plaats in de **console van de Fragmenten van de Ervaring**.

1. Selecteer of een omslag of uw fragment, dan **Eigenschappen** van de toolbar.

   >[!NOTE]
   >
   >Personalization-eigenschappen die in een map zijn gedefinieerd, worden door alle onderliggende mappen onderaan in de substructuur overgeërfd, en ervaren fragmenten (en variaties) binnen die substructuur. Ze kunnen worden overschreven door de overerving te verbreken.

1. Open het **Personalization** lusje om uw montages te bepalen en te bewaren. Bijvoorbeeld in een map:

   ![ Fragment van de Ervaring - de Eigenschappen van de Personalisatie ](/help/sites-cloud/authoring/assets/xf-personalization-properties.png)

   >[!CAUTION]
   >
   >Wanneer een fragment in een pagina van Plaatsen wordt ingebed, en **Personalization** is gevormd, dan slechts wordt de verpersoonlijkingsversie van de pagina gebruikt bij pagina die tijd teruggeeft.
   >
   >Als u wilt dat de doelbewerkingen op de componenten in een fragment worden uitgevoerd, moet aan de volgende voorwaarden worden voldaan:
   >
   >Het **ContextHub Weg** in het **Personalization** lusje wordt geselecteerd moet of zijn:
   >
   >* hetzelfde pad als het pad dat is geconfigureerd voor de pagina waar het fragment wordt gerenderd
   >
   >  Of:
   >
   >* een weg die een ondergroep van de opslag bevat die in ContextHub wordt bepaald die voor de pagina wordt gevormd
   >
   >Het **Weg van Segmenten** in het **Personalization** lusje wordt geselecteerd moet of zijn:
   >
   >* hetzelfde pad als het pad dat is geconfigureerd voor de pagina waar het fragment wordt gerenderd
   >
   >  of
   >
   >* een pad dat een subset bevat van de segmenten die voor de pagina zijn geconfigureerd

### Doelstelling definiëren voor uw ervaringsfragment {#defining-targeting-experience-fragment}

Nadat de verpersoonlijkingseigenschappen worden gevormd, is de het richten wijze beschikbaar wanneer het fragment voor het uitgeven wordt geopend.

![ de Redacteur van het Fragment van de Ervaring - het richten wijze ](/help/sites-cloud/authoring/assets/xf-targeting-mode.png)

Deze modus werkt op dezelfde manier als bij paginabewerking. Zie [ het richten wijze voor de Redacteur van de Pagina ](/help/sites-cloud/authoring/personalization/targeted-content.md) voor meer details.

## Details van uw ervaringsfragment {#details-of-your-experience-fragment}

Details van het fragment kunt u zien:

1. Navigeer naar de locatie van uw ervaringsfragmenten (navigeer niet verder naar beneden naar de variaties in het fragment).
De details worden getoond in alle meningen van de **console van Fragmenten van de 1&rbrace; Ervaring, met de** Mening van de Lijst **met inbegrip van details van een [ uitvoer naar Doel ](/help/sites-cloud/integrating/integrating-adobe-target.md):**

   ![ de details van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/xf-15.png)

1. Wanneer u **Eigenschappen** van het Fragment van de Ervaring opent:

   ![ knoop van Eigenschappen ](/help/sites-cloud/authoring/assets/xf-16.png)

   De eigenschappen zijn beschikbaar op verschillende tabbladen:

   >[!CAUTION]
   >
   >Deze lusjes worden getoond wanneer u **Eigenschappen** van de console van de Fragmenten van de Ervaring opent.
   >
   >Als u **Eigenschappen opent** tijdens het bewerken van een Experience-fragment, worden de juiste [Pagina-eigenschappen](/help/sites-cloud/authoring/sites-console/page-properties.md) weergegeven.

   ![ de eigenschappen van het Fragment van de Ervaring ](/help/sites-cloud/authoring/assets/xf-17.png)

   * **Basis**
      * **Titel** - verplicht
      * **Beschrijving**
      * **Markeringen**
      * **Totaal aantal varianten** - slechts informatie
      * **Aantal Webvarianten** - slechts informatie
      * **Aantal niet-Web varianten** - slechts informatie
      * **Aantal pagina&#39;s die dit fragment** gebruiken - slechts informatie
   * **Cloud Servicen**
      * **Configuratie van de Wolk**
      * **Configuraties van de Cloud Service**
      * **Facebook pagina ID**
      * **de raad van Pinterest**
   * **Verwijzingen**
      * Een lijst met verwijzingen
   * **Personalization**
      * **ContextHub Weg**
      * **Weg van Segmenten**
      * **Merk**

## De normale HTML-vertoning {#the-plain-html-rendition}

Met de kiezer `.plain.` in de URL hebt u vanuit de browser toegang tot de uitvoering van normale HTML.

>[!NOTE]
>
>Hoewel dit direct beschikbaar van browser is, [ het primaire doel is andere toepassingen (bijvoorbeeld, derdeWeb apps, douane mobiele implementaties) toe te staan om tot de inhoud van het Fragment van de Ervaring direct toegang te hebben, gebruikend slechts URL ](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Fragmenten voor publicatie-ervaring {#publishing-experience-fragments}

Het publiceren van uw Fragment van de Ervaring is fundamenteel het zelfde als [ het publiceren van een pagina ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) (hoewel van de console of de redacteur van de Fragmenten van de Ervaring).

Alternatief kunt u [ ook publiceren aan Voorproef ](/help/sites-cloud/authoring/sites-console/previewing-content.md) (opnieuw van de console of de redacteur van de Fragmenten van de Ervaring).

## Exporteren van ervaringsfragmenten {#exporting-experience-fragments}

Standaard worden Experience Fragments geleverd in de HTML-indeling. Dit kan zowel door AEM als derdekanalen worden gebruikt.

Voor export naar Adobe Target kan JSON ook worden gebruikt. Zie:

* [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exporteren van ervaringsfragmenten naar Adobe Target](/help/sites-cloud/integrating/experience-fragments-target.md)
