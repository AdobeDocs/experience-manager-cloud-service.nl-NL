---
title: Werken met inhoudsfragmenten (Assets - Inhoudsfragmenten)
description: Leer hoe u met Content Fragments in Adobe Experience Manager (AEM) as a Cloud Service inhoud kunt ontwerpen, maken, beheren en gebruiken, ideaal voor het ontwerpen van pagina's en het leveren zonder kop.
exl-id: db17eff1-4252-48d5-bb67-5e476e93ef7e
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2247'
ht-degree: 2%

---

# Werken met inhoudsfragmenten {#working-with-content-fragments}

Met Adobe Experience Manager (AEM) as a Cloud Service, laten de Fragmenten van de Inhoud u, pagina-onafhankelijke inhoud ontwerpen tot stand brengen, leiden en [&#x200B; publiceren &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md). Zo kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties/via meerdere kanalen, ideaal voor levering zonder kop. Zij kunnen ook samen met [&#x200B; multi-Plaats Beheer worden gebruikt om u toe te laten om uw inhoud &#x200B;](#reusing-content-fragments-with-msm) opnieuw te gebruiken.

Inhoudsfragmenten bevatten gestructureerde inhoud:

* Zij zijn gebaseerd op het Model van het Fragment van de a [&#x200B; Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md), dat vooraf een structuur voor het resulterende fragment bepaalt.
* De structuur kan liggen tussen:
   * Basis
      * Bijvoorbeeld een tekstveld met één regel tekst.
      * Deze kan worden gebruikt voor het voorbereiden van eenvoudige inhoud voor gebruik in paginaontwerp.
   * Complex
      * Een combinatie van een groot aantal velden met verschillende gegevenstypen, zoals tekst, getal, boolean, gegevens en tijd.
      * Deze kan worden gebruikt voor het voorbereiden van gestructureerde inhoud voor het ontwerpen van pagina&#39;s of voor levering aan uw toepassing.
   * Genest
      * Met de beschikbare gegevenstypen waarnaar wordt verwezen, kunt u de inhoud nesten.
      * Dit wordt doorgaans gebruikt voor levering aan uw toepassing.

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM-kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

>[!NOTE]
>
>De Fragmenten van de inhoud zijn een eigenschap van Plaatsen, maar worden opgeslagen als **Assets**.
>
>De Fragmenten van de inhoud en de Modellen van het Fragment van de Inhoud worden nu hoofdzakelijk beheerd met de **[console van de Fragmenten van de Inhoud](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**, hoewel de Fragmenten van de Inhoud nog van de **Assets** console kunnen worden beheerd, en de Modellen van het Fragment van de Inhoud van de **Hulpmiddelen** console. Deze sectie behandelt beheer van **Assets** en **de consoles van Hulpmiddelen**.
>
>Er zijn twee editors voor het ontwerpen van Content Fragments; hoewel de basisfunctionaliteit het zelfde is, zijn er sommige verschillen. Deze sectie behandelt de originele redacteur, hoofdzakelijk die van de **wordt betreden Assets** console. Zie de documentatie van Plaatsen, [&#x200B; de Fragmenten van de Inhoud - Authoring &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md), voor details van de nieuwe redacteur (hoofdzakelijk betreden van de **3&rbrace; console van de Fragmenten van de Inhoud &lbrace;).** Beide editors hebben een knevelschakelaar in de hoogste toolbar om snelle toegang tot de andere redacteur te verlenen.

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van uw inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md) - toelatend, creërend, en bepalend uw modellen
* [&#x200B; het Leiden de Fragmenten van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-managing.md) - creeer uw inhoudsfragmenten; dan geef, publiceer, en verwijzing uit
* [&#x200B; Variaties - het Authoring Inhoud van het Fragment &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) - auteur de fragmentinhoud en creeer variaties van de Meester
* [&#x200B; Markering &#x200B;](/help/assets/content-fragments/content-fragments-markdown.md) - het gebruiken van prijsdalingssyntaxis voor uw fragment
* [&#x200B; Gebruikend Bijbehorende Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-assoc-content.md) - toevoegend bijbehorende inhoud
* [&#x200B; Meta-gegevens - de Eigenschappen van het Fragment &#x200B;](/help/assets/content-fragments/content-fragments-metadata.md) - het bekijken van en het uitgeven van de fragmenteigenschappen
* Gebruik [&#x200B; de Fragmenten van de Inhoud, samen met GraphQL, zodat kunt u inhoud &#x200B;](/help/assets/content-fragments/content-fragments-graphql.md) voor gebruik in uw toepassingen leveren. Om met dit te helpen, kunt u voorproef [&#x200B; output JSON &#x200B;](/help/assets/content-fragments/content-fragments-json-preview.md).
* [Inhoudsfragmenten opnieuw gebruiken met MSM](#reusing-content-fragments-with-msm)

>[!NOTE]
>
>Deze pagina&#39;s kunnen worden gelezen met:
>
>* [&#x200B; het Authoring van de Pagina met de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* [Contentfragmenten aanpassen en uitbreiden](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [&#x200B; AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud &#x200B;](/help/headless/graphql-api/content-fragments.md)
>* Het [&#x200B; ModelOpenAPIs van het Fragment van de Inhoud en van het Fragment van de Inhoud &#x200B;](/help/headless/content-fragment-openapis.md)

Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* Fysiek kanaal, bijvoorbeeld desktop, mobiel.
* Leveringsvorm via een fysiek kanaal, bijvoorbeeld de pagina met productdetails, de pagina met productcategorieën voor desktops of de pagina Mobiel web en de pagina Mobiele apps voor mobiele apparaten.

(Waarschijnlijk) wilt u echter niet voor alle kanalen dezelfde inhoud gebruiken. U moet de inhoud optimaliseren op basis van het specifieke kanaal.

Met inhoudelementen kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan de tekst toe door elementen (gemengde-mediafragmenten) in te voegen.
* Maak geneste inhoud, zodat u de complexiteit van uw gegevens weerspiegelt.

Deze inhoudsfragmenten kunnen vervolgens worden samengevoegd om via verschillende kanalen ervaringen op te doen.

>[!NOTE]
>
>**de Fragmenten van de Inhoud** en **[Fragmenten van de Ervaring](/help/sites-cloud/authoring/fragments/content-fragments.md)** zijn verschillende eigenschappen binnen AEM:
>
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals tekst, cijfers en datums.
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Voor meer informatie, zie ook [&#x200B; Begrip van de Fragmenten van de Inhoud en de Fragmenten van de Ervaring in AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

## Inhoudsfragmenten en inhoudsservices {#content-fragments-and-content-services}

AEM Content Services is ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, maar niet alleen op webpagina&#39;s.

Ze leveren inhoud aan kanalen die geen traditionele AEM-webpagina&#39;s zijn, met behulp van gestandaardiseerde methoden die door elke client kunnen worden gebruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

De levering wordt uitgevoerd in JSON-indeling met behulp van de JSON Exporter.

Met AEM Content Fragments kunt u gestructureerde inhoud beschrijven en beheren. Gestructureerde inhoud wordt gedefinieerd in modellen die verschillende inhoudstypen kunnen bevatten, zoals tekst, numerieke gegevens, booleaanse gegevens, datum en tijd en meer.

Samen met de JSON-exportmogelijkheden van AEM-kerncomponenten kan deze gestructureerde inhoud vervolgens worden gebruikt om AEM-inhoud te leveren aan andere kanalen dan AEM-pagina&#39;s.

>[!NOTE]
>
>Zie [&#x200B; Zwaartepunt en AEM &#x200B;](/help/headless/introduction.md) voor een inleiding aan Zwaardeloze Ontwikkeling voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud. Zie [&#x200B; Vertaal Assets &#x200B;](/help/assets/translate-assets.md) voor verdere informatie.

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* Opgeslagen als **Assets**:

   * De fragmenten van de inhoud (en hun variaties) kunnen van de **Assets** console worden gecreeerd en worden gehandhaafd.
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Gebruikt in de [&#x200B; paginaredacteur door de component van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) (van verwijzingen voorzien component):

   * De **component van het Fragment van 0&rbrace; Inhoud &lbrace;is beschikbaar aan paginaauteurs.** Hiermee kunnen ze naar het vereiste inhoudsfragment in HTML- of JSON-indeling verwijzen en dit leveren.

* Toegankelijk gebruikend [&#x200B; AEM GraphQL API &#x200B;](/help/headless/graphql-api/content-fragments.md).

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Geen lay-out of ontwerp hebben (enige tekstopmaak is mogelijk in de modus RTF).
* Bevat één of meerdere [&#x200B; samenstellende delen &#x200B;](#constituent-parts-of-a-content-fragment).
* [&#x200B; bevat, of kan met, beelden &#x200B;](#fragments-with-visual-assets) worden verbonden.
* Wordt gebruikt [&#x200B; binnen-tussen inhoud &#x200B;](#in-between-content-when-page-authoring-with-content-fragments) wanneer van verwijzingen voorzien op een pagina.
* Ze zijn onafhankelijk van het leveringsmechanisme (pagina, kanaal).

### Fragmenten met Visual Assets {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Assets kan op verschillende manieren worden gebruikt met een inhoudsfragment. Elk van deze mogelijkheden heeft zijn eigen voordelen:

* **Activa van het Tussenvoegsel** in een fragment (gemengd-media fragmenten)

   * Zij zijn een deel van het fragment (zie [&#x200B; Vormende Delen van een Inhoudsfragment &#x200B;](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie [&#x200B; Invoegend Assets in uw Fragment &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de Redacteur van het Fragment voor meer informatie.

  >[!NOTE]
  >
  >Visuele elementen die in het inhoudsfragment zelf worden ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Verwante Inhoud**

   * Verbonden met een fragment; maar geen vast deel van het fragment (zie [&#x200B; Vormt Delen van een Inhoudsfragment &#x200B;](#constituent-parts-of-a-content-fragment)).
   * Heeft enige flexibiliteit voor positionering.
   * Eenvoudig beschikbaar voor gebruik (als tussenliggende inhoud) bij gebruik van het fragment op een pagina.

  Zie [&#x200B; Geassocieerde Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-assoc-content.md) voor meer informatie.

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Heeft enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.

  Zie {Browser van 0} Assets [&#x200B; voor meer informatie.](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser)

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Elementen van het Fragment**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Tekstblokken, vaak meerdere regels die zijn gescheiden als afzonderlijke entiteiten.

   * In de modi [Tekst met opmaak](/help/assets/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Assets die in een Fragment (Gemengd-Media Fragments) wordt opgenomen**

   * Assets (afbeeldingen) ingevoegd in het feitelijke fragment en gebruikt als de interne inhoud van een fragment.
   * Ingesloten in het alineasysteem van het fragment.
   * Kan worden geformatteerd wanneer het [&#x200B; fragment wordt gebruikt/op een pagina &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) van verwijzingen wordt voorzien.
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan slechts aan, worden toegevoegd geschrapt van, of binnen, een fragment gebruikend het [&#x200B; Rich formaat van de Tekst in de fragmentredacteur &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) worden bewogen.
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

     >[!CAUTION]
     >
     >Assets kan (per ongeluk) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

     >[!NOTE]
     >
     >Assets kan ook als extra (in-tussen) inhoud worden toegevoegd wanneer het gebruiken van een fragment op een pagina; het gebruiken van of [&#x200B; Geassocieerde Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-assoc-content.md) of activa van browser van Assets.

* **Verwante Inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Afbeeldingen, video&#39;s of andere fragmenten worden meestal weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De activa worden [&#x200B; geassocieerd aan fragmenten als inzamelingen &#x200B;](/help/assets/content-fragments/content-fragments-assoc-content.md); de bijbehorende inzamelingen staan de auteur toe om te beslissen welke activa te gebruiken wanneer zij de pagina ontwerpen.

      * Verzamelingen kunnen tijdens het ontwerpen van fragmenten als standaardinhoud worden gekoppeld.
      * [&#x200B; Assets (DAM) Inzamelingen &#x200B;](/help/assets/manage-collections.md) zijn de basis voor de bijbehorende inhoud van fragmenten.
   * Desgewenst kunt u het fragment zelf ook aan een verzameling toevoegen om het bijhouden van het fragment te vergemakkelijken.

* **Metagegevens van het Fragment**

   * Gebruik de [&#x200B; schema&#39;s van de meta-gegevens van Assets &#x200B;](/help/assets/metadata-schemas.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of hoger:

         * Door het fragment **Eigenschappen** van de console te bekijken/uit te geven
         * Door **Meta-gegevens** te uitgeven wanneer in de fragmentredacteur

  >[!CAUTION]
  >
  >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

* **Meester**

   * Een deel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Stramien kan niet worden verwijderd.

   * Het hoofd is toegankelijk in de fragmentredacteur onder **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**.
   * Stramien is geen variatie als zodanig, maar is de basis van alle variaties.

* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor een redactioneel doel; kan gerelateerd zijn aan een kanaal, maar is niet verplicht, kunnen ook voor lokale ad-hocwijzigingen worden gebruikt.
   * Wordt gecreeerd als exemplaren van **Hoofd**, maar kan dan zoals vereist worden uitgegeven. Er is inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * De variaties kunnen [&#x200B; &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) met Hoofd worden gesynchroniseerd als de Hoofdinhoud is bijgewerkt.
   * Kan [&#x200B; worden samengevat &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) om de tekst aan een vooraf bepaalde lengte snel te beknotten.
   * Beschikbaar onder het [&#x200B; lusje van Variaties &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) van de fragmentredacteur.

### Tussen inhoud wanneer pagina&#39;s worden gemaakt met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussenliggende inhoud:

* Beschikbaar voor gebruik in de Pagina-editor bij het werken met inhoudsfragmenten.
* [&#x200B; extra inhoud die binnen de stroom van een fragment &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-in-between-content) wordt toegevoegd nadat het wordt gebruikt of op een pagina van verwijzingen wordt voorzien.
* Beschikbaar voor gebruik in de [&#x200B; Redacteur van de Pagina wanneer het werken met de Fragmenten van de Inhoud &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md).
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Voor het maken van inhoudsfragmenten hebt u het volgende nodig:

* **Model van de Inhoud**

   * Zijn [&#x200B; toegelaten gebruikend Browser van de Configuratie &#x200B;](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * Wordt [&#x200B; gecreeerd gebruikend Hulpmiddelen &#x200B;](/help/assets/content-fragments/content-fragments-models.md).
   * Vereist om [&#x200B; tot een fragment &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments) te leiden.
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. Alle andere opties zijn optioneel.
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* **Component van het Fragment van de Inhoud**

   * Instrumentaal voor het leveren van het fragment in HTML-indeling, JSON-indeling of beide.
   * Vereist om [&#x200B; het fragment op een pagina &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) van verwijzingen te voorzien.
   * Verantwoordelijk voor de lay-out en levering van een fragment, dat wil zeggen, kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Wanneer u een fragment naar een pagina sleept in de ontwerpfase, wordt de vereiste component automatisch gekoppeld.

## Inhoudsfragmenten opnieuw gebruiken met MSM {#reusing-content-fragments-with-msm}

Wanneer betreden door de **Assets** console, kunt u MSM gebruiken en Levende Exemplaren voor uw fragmenten creëren.

Zie voor meer informatie:

* [Inhoudsfragmenten opnieuw gebruiken met MSM](/help/assets/content-fragments/content-fragments-msm.md)
* [&#x200B; hergebruik activa gebruikend MSM voor Assets &#x200B;](/help/assets/reuse-assets-using-msm.md).

Deze laten [&#x200B; overerving &#x200B;](/help/assets/content-fragments/content-fragments-variations.md#inheritance) voor zowel variaties als individuele gebieden van uw fragmenten toe.

>[!CAUTION]
>
>Als u MSM (dat tot exemplaren van Inhoudsfragmenten leidt) wilt gebruiken, dan zouden om het even welke **Unieke** beperkingen uit om het even welke Types moeten worden verwijderd van Gegevens die in de respectieve [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md) worden gebruikt.

## Voorbeeldengebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bedenk bij het ontwerpen van het fragment wat wordt gebruikt en waar het wordt gebruikt.

### WKND-voorbeeld {#wknd-sample}

De [&#x200B; steekproeven van de Plaats WKND &#x200B;](/help/implementing/developing/introduction/develop-wknd-tutorial.md) worden verstrekt om u over AEM as a Cloud Service te helpen leren.

Het WKND-project omvat:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
