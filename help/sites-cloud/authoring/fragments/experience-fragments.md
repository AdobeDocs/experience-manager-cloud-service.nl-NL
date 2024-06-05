---
title: Ervaar fragmenten
description: Met Experience Fragments in Adobe Experience Manager as a Cloud Service kunt u uw ervaringen herbruikbaar en flexibel maken.
exl-id: 9dc33677-141f-47e5-a01e-6c7488686314
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
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
* Deze sjabloon wordt gebruikt om de *hoofdpagina* van het ervaringsfragment.
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
* Om het hoofdloze gebruik-geval CMS te steunen.
Auteurs willen AEM alleen gebruiken voor ontwerpen, maar niet voor levering aan de klant. Een systeem/aanraakpunt van derden zou deze ervaring gebruiken en vervolgens leveren aan de gebruiker.
* Met [Beheer van meerdere sites (MSM)](/help/sites-cloud/administering/msm/overview.md); een ervaringsfragment maakt deel uit van een pagina. Dit geldt zowel voor de afzonderlijke fragmenten als voor de mappen waarin deze zich bevinden.

>[!NOTE]
>
>**[Inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)** en **Ervaar fragmenten** Er zijn verschillende functies binnen AEM:
>* **Inhoudsfragmenten** redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, cijfers en datums.
>* **Ervaar fragmenten** volledig opgemaakt zijn, een fragment van een webpagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie voor meer informatie [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

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

* [vormen de toegestane malplaatjes op deze omslagen](#configure-allowed-templates-folder).

Door mappen te maken kunt u:

* een zinvolle structuur voor uw ervaringsfragmenten maken, bijvoorbeeld volgens de classificatie

  >[!NOTE]
  >
  >U hoeft de structuur van uw ervaringsfragmenten niet uit te lijnen met de paginastructuur van uw site.

* [de toegestane sjablonen toewijzen op mapniveau](#configure-allowed-templates-folder)

  >[!NOTE]
  >
  >U kunt de [sjablooneditor](/help/sites-cloud/authoring/sites-console/templates.md) om uw eigen sjabloon te maken.

Het WKND-project structureert bepaalde ervaringsfragmenten volgens `Contributors`. De gebruikte structuur illustreert ook hoe andere functies, zoals beheer voor meerdere sites (inclusief taalkopieën), kunnen worden gebruikt.

Zie:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Mappen voor ervaringsfragmenten](/help/sites-cloud/authoring/assets/xf-folders.png)

## Het creëren van en het Vormen van een Omslag voor uw Fragmenten van de Ervaring {#creating-and-configuring-a-folder-for-your-experience-fragments}

Om een omslag voor uw Fragments van de Ervaring tot stand te brengen en te vormen wordt het geadviseerd:

1. [Een map maken](/help/sites-cloud/authoring/sites-console/managing-pages.md#creating-a-new-folder).

1. [Configureer de toegestane sjablonen voor ervaringsfragmenten voor die map](#configure-allowed-templates-folder).

>[!NOTE]
>
>Het is ook mogelijk om [Toegestane sjablonen voor uw instantie](#configure-allowed-templates-instance), maar deze methode **niet** aanbevolen omdat de waarden tijdens de upgrade kunnen worden overschreven.

### Configureer de toegestane sjablonen voor uw map {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dit is de aanbevolen methode voor het opgeven van de **Toegestane sjablonen**, omdat de waarden niet worden overschreven bij een upgrade.

1. Navigeer naar de vereiste **Ervaar fragmenten** map.

1. Selecteer de map en **Eigenschappen**.

1. Geef de reguliere expressie op voor het ophalen van de vereiste sjablonen in het dialoogvenster **Toegestane sjablonen** veld.

   Bijvoorbeeld:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Zie:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Ervaar fragmenteigenschappen - Toegestane sjablonen](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Zie [Sjablonen voor ervaringsfragmenten](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor nadere bijzonderheden.

1. Selecteren **Opslaan en sluiten**.

### Vorm de Toegestane Malplaatjes voor uw Instantie {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Het wordt afgeraden de **Toegestane sjablonen** door deze methode, aangezien de gespecificeerde malplaatjes bij verbetering kunnen worden beschreven.
>
>Gebruik dit dialoogvenster alleen ter informatie.

1. Navigeer naar de vereiste **Ervaar fragmenten** console.

1. Selecteren **Configuratieopties**:

   ![Knop Configuratie](/help/sites-cloud/authoring/assets/xf-18.png)

1. Geef de vereiste sjablonen op in het dialoogvenster **Fragmenten voor ervaring configureren** dialoogvenster:

   ![Fragmenten voor ervaring configureren](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Zie [Sjablonen voor ervaringsfragmenten](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments) voor nadere bijzonderheden.

1. Selecteren **Opslaan**.

## Een ervaringsfragment maken {#creating-an-experience-fragment}

Een ervaringsfragment maken:

1. Selecteren **Ervaar fragmenten** in de globale navigatie.

   ![Ervaar fragmenten in het navigatievenster](/help/sites-cloud/authoring/assets/xf-01.png)

1. Ga naar de gewenste map en selecteer **Maken**:

   ![Een map maken voor Experience Fragments](/help/sites-cloud/authoring/assets/xf-02.png)

1. Selecteren **Ervaar fragment** om de **Experience Fragment maken** wizard.

   Selecteer de vereiste **sjabloon** en kies vervolgens **Volgende**:

   ![Een ervaringsfragmentsjabloon selecteren](/help/sites-cloud/authoring/assets/xf-03.png)


1. Voer de **Eigenschappen** voor uw **Experience-fragment** in.

   A **Titel** is verplicht. Als de **Naam** wordt niet ingevuld en wordt afgeleid van de **Titel**.

   ![Ervaar fragmenteigenschappen](/help/sites-cloud/authoring/assets/xf-04.png)

   >[!NOTE]
   >
   >Labels uit de sjabloon Fragmentervaring worden niet samengevoegd met codes op de basispagina van dit ervaringsfragment.
   >
   >Deze zijn volledig gescheiden.

1. Klikken **Maken**.

   Er wordt een bericht weergegeven. Selecteren:

   * **Gereed** om naar de console terug te keren
   * **Openen** om de fragmenteditor te openen

## Uw ervaringsfragment bewerken {#editing-your-experience-fragment}

De Experience Fragment Editor biedt u vergelijkbare mogelijkheden als de normale pagina-editor.

>[!NOTE]
>
>Zie [Pagina-inhoud bewerken](/help/sites-cloud/authoring/page-editor/edit-content.md) voor meer informatie over het gebruik van de pagina-editor.

De volgende voorbeeldprocedure laat zien hoe u een gummetje voor een product kunt maken:

1. Sleep de vereiste component vanuit de [Browser voor componenten](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

1. Afhankelijk van de component:
   * Voeg naar wens inhoud en/of elementen toe.
   * Configureer de eigenschappen naar wens.

1. Voeg desgewenst meer componenten toe.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Ervaar fragment op pagina](/help/sites-cloud/authoring/assets/xf-05.png)

## Een ervaringsfragmentvariatie maken {#creating-an-experience-fragment-variation}

U kunt variaties van uw Fragment van de Ervaring tot stand brengen, afhankelijk van uw behoeften:

1. Open het fragment voor [bewerken](#editing-your-experience-fragment).
1. Open de **Variaties** tab.

   ![Een Experience Fragment-wijziging maken](/help/sites-cloud/authoring/assets/xf-06.png)

1. **Maken** kunt u maken:

   * **Variatie**
   * **Variatie als live-kopie**.

     >[!NOTE]
     >
     >Als u een initiële variatie maakt als Live kopie, wordt de titel overgenomen door de bron van Live kopie als de hoofdvariatie te gebruiken.

1. Definieer de vereiste eigenschappen:

   * **Sjabloon**
   * **Titel**
   * **Naam** - indien niet ingevuld, wordt het afgeleid van de titel
   * **Beschrijving**
   * **Variatietags**

   Bijvoorbeeld:

   ![Variatie-eigenschappen](/help/sites-cloud/authoring/assets/xf-07.png)


1. Bevestigen met **Gereed**, wordt de nieuwe variatie weergegeven in het deelvenster.

## Uw ervaringsfragment gebruiken {#using-your-experience-fragment}

U kunt het fragment van de Ervaring nu gebruiken wanneer het ontwerpen van uw pagina&#39;s:

1. Open een pagina om te bewerken.

   >[!NOTE]
   >
   >De pagina moet zijn gebaseerd op een bewerkbare sjabloon.

1. Maak een instantie van de component Experience Fragment in het paginalineasysteem:

1. Voeg het daadwerkelijke Fragment van de Ervaring aan de componenteninstantie toe; of:

   * Sleep het vereiste fragment uit de middelenbrowser en zet het neer op de component.
   * Selecteren **Configureren** op de componentwerkbalk en geef het te gebruiken fragment op, bevestigen met **Gereed**.

   >[!NOTE]
   >
   >Bewerken werkt op de werkbalk van de component als een sneltoets waarmee het fragment in de fragmenteditor wordt geopend.

Bijvoorbeeld: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Ervaar het fragment in de Pagina-editor](/help/sites-cloud/authoring/assets/xf-08.png)

## Bouwstenen {#building-blocks}

U kunt een of meer componenten selecteren om een bouwsteen voor recycling binnen uw fragment te maken:

### Een bouwblok maken {#creating-a-building-block}

Een bouwblok maken:

1. In de redacteur van het Fragment van de Ervaring, selecteer de componenten u wilt hergebruiken:

   ![Component selecteren voor bouwblok](/help/sites-cloud/authoring/assets/xf-09.png)

1. Selecteer op de werkbalk Componenten de optie **Omzetten in bouwsteen**:

   ![Knop Gebouwd blok](/help/sites-cloud/authoring/assets/xf-10.png)

1. Voer de naam van de **bouwsteen** in en bevestig dit met **Converteren**:

   ![Naambouwblok](/help/sites-cloud/authoring/assets/xf-11.png)

1. De **Bouwsteen** wordt weergegeven op het linkertabblad (**Lokaal**) en kan voor verdere actie worden geselecteerd:

   ![Bouwblok in de spoorstaaf](/help/sites-cloud/authoring/assets/xf-12.png)

#### Een bouwblok beheren {#managing-a-building-block}

Uw bouwsteen is zichtbaar in **Bouwstenen** tab. Voor elk blok zijn de volgende acties beschikbaar:

* **Ga naar stramien**: open de variatie van de wortelpagina in een nieuw lusje
* **Naam wijzigen**
* **Verwijderen**

![Gebouwenblokken beheren](/help/sites-cloud/authoring/assets/xf-13.png)

#### Een bouwsteen gebruiken {#using-a-building-block}

U kunt de bouwsteen naar het alineasysteem van om het even welk fragment slepen, zoals met om het even welke component.

Als u een Experience Fragment bewerkt, worden de beschikbare bouwstenen weergegeven op het tabblad links. U kunt filteren op basis van:

* **Lokaal** - Blokken maken op basis van het huidige ervaringsfragment
* **Alles** - Blokken maken van alle fragmenten

![Bouwblokken selecteren](/help/sites-cloud/authoring/assets/xf-14.png)

## Personalisatie op uw ervaringsfragment {#personalization-experience-fragment}

Als u het fragment personaliseert op uw ervaringsfragment, kunt u als een markeerteken één keer een doelpubliek voor het ervaringsfragment definiëren en het fragment vervolgens op een willekeurige pagina opnieuw gebruiken. Dit:

* hoeft u niet telkens wanneer het fragment wordt gebruikt, de vereiste variaties voor elk publiek op te geven
* handhaaft stijl over de aanbiedingen

U kunt een Experience Fragment maken met meerdere componenten die binnen dit ene fragment zijn gegroepeerd. U kunt ook variaties van het fragment maken voor elk specifiek publiekssegment en deze fragmenten van de Ervaring vervolgens opnieuw gebruiken voor alle vereiste kanalen.

Personalisatie wordt bereikt door het definiëren van de **Personalisatie** eigenschappen op het fragment of de variatie van de Ervaring, of de omslag die de fragmenten bevat; dit betekent dat de overerving verpersoonlijkingseigenschappen kan met voeten treden.

Als u deze eigenschappen configureert, wordt de optie **Targeting** in de Experience Fragment-editor.

### Specialisatie definiëren voor uw ervaringsfragment {#defining-personalization-experience-fragment}

Het fragment aanpassen:

1. Ga naar de gewenste locatie in het dialoogvenster **Ervaar fragmenten** console.

1. Selecteer een map of fragment, en **Eigenschappen** op de werkbalk.

   >[!NOTE]
   >
   >De eigenschappen van de verpersoonlijking die op een omslag worden bepaald worden geërft door alle kindomslagen neer door de subboom, en de Fragmenten van de Ervaring (en variaties) binnen die subboom. Ze kunnen worden overschreven door de overerving te verbreken.

1. Open de **Personalisatie** om uw instellingen te definiëren en op te slaan. Bijvoorbeeld in een map:

   ![Experience Fragment - Persoonlijke eigenschappen](/help/sites-cloud/authoring/assets/xf-personalization-properties.png)

   >[!CAUTION]
   >
   >Wanneer een fragment is ingesloten op een sitepagina, en **Personalisatie** is gevormd, dan slechts wordt de verpersoonlijkingsversie van de pagina gebruikt bij pagina die tijd teruggeeft.
   >
   >Als u wilt dat de doelbewerkingen op de componenten in een fragment worden uitgevoerd, moet aan de volgende voorwaarden worden voldaan:
   >
   >De **ContextHub-pad** geselecteerd in het dialoogvenster **Personalisatie** tab:
   >
   >* hetzelfde pad als het pad dat is geconfigureerd voor de pagina waar het fragment wordt gerenderd
   >
   >  Of:
   >
   >* een weg die een ondergroep van de opslag bevat die in ContextHub wordt bepaald die voor de pagina wordt gevormd
   >
   >De **Segmentpad** geselecteerd in het dialoogvenster **Personalisatie** tab:
   >
   >* hetzelfde pad als het pad dat is geconfigureerd voor de pagina waar het fragment wordt gerenderd
   >
   >  of
   >
   >* een pad dat een subset bevat van de segmenten die voor de pagina zijn geconfigureerd

### Doelstelling definiëren voor uw ervaringsfragment {#defining-targeting-experience-fragment}

Nadat de verpersoonlijkingseigenschappen worden gevormd, is de het richten wijze beschikbaar wanneer het fragment voor het uitgeven wordt geopend.

![Experience Fragment Editor - Targeingmodus](/help/sites-cloud/authoring/assets/xf-targeting-mode.png)

Deze modus werkt op dezelfde manier als bij paginabewerking. Zie [Doelmodus voor de Pagina-editor](/help/sites-cloud/authoring/personalization/targeted-content.md) voor meer informatie .

## Details van uw ervaringsfragment {#details-of-your-experience-fragment}

Details van het fragment kunt u zien:

1. Navigeer naar de locatie van uw ervaringsfragmenten (navigeer niet verder naar beneden naar de variaties in het fragment).
De details worden getoond in alle meningen van **Ervaar fragmenten** console, met de **Lijstweergave** , met inbegrip van nadere gegevens over een [exporteren naar doel](/help/sites-cloud/integrating/integrating-adobe-target.md):

   ![Ervaar fragmentdetails](/help/sites-cloud/authoring/assets/xf-15.png)

1. Wanneer u het dialoogvenster **Eigenschappen** van het ervaringsfragment:

   ![Eigenschappen, knop](/help/sites-cloud/authoring/assets/xf-16.png)

   De eigenschappen zijn beschikbaar op verschillende tabbladen:

   >[!CAUTION]
   >
   >Deze tabbladen worden weergegeven wanneer u **Eigenschappen** van de console van de Fragmenten van de Ervaring.
   >
   >Als u **Eigenschappen opent** tijdens het bewerken van een Experience-fragment, worden de juiste [Pagina-eigenschappen](/help/sites-cloud/authoring/sites-console/page-properties.md) weergegeven.

   ![Ervaar fragmenteigenschappen](/help/sites-cloud/authoring/assets/xf-17.png)

   * **Basis**
      * **Titel** - verplicht
      * **Beschrijving**
      * **Tags**
      * **Totaal aantal varianten** - alleen informatie
      * **Aantal webvarianten** - alleen informatie
      * **Aantal niet-webvarianten** - alleen informatie
      * **Aantal pagina&#39;s dat dit fragment gebruikt** - alleen informatie
   * **Cloud Servicen**
      * **Cloud Configuration**
      * **Configuraties van Cloud Servicen**
      * **Facebook-pagina-id**
      * **Pinterest board**
   * **Verwijzingen**
      * Een lijst met verwijzingen
   * **Personalisatie**
      * **ContextHub-pad**
      * **Segmentpad**
      * **Merk**

## De normale HTML-vertoning {#the-plain-html-rendition}

Met de `.plain.` in de URL hebt, kunt u vanuit de browser toegang krijgen tot de uitvoering van normale HTML.

>[!NOTE]
>
>Hoewel dit direct beschikbaar is in de browser, [het primaire doel is om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment, met alleen de URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Fragmenten voor publicatie-ervaring {#publishing-experience-fragments}

Het publiceren van het fragment van uw ervaring is in feite hetzelfde als [publiceren, een pagina](/help/sites-cloud/authoring/sites-console/publishing-pages.md) (vanuit de console of editor van de Experience Fragments).

U kunt ook [publiceren naar voorvertoning](/help/sites-cloud/authoring/sites-console/previewing-content.md) (opnieuw van de console of de redacteur van Fragmenten van de Ervaring).

## Exporteren van ervaringsfragmenten {#exporting-experience-fragments}

Standaard worden Experience Fragments geleverd in de HTML-indeling. Dit kan zowel door AEM als derdekanalen worden gebruikt.

Voor export naar Adobe Target kan JSON ook worden gebruikt. Zie:

* [Integreren met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exporteren van ervaringsfragmenten naar Adobe Target](/help/sites-cloud/integrating/experience-fragments-target.md)
