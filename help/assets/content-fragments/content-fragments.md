---
title: Werken met inhoudsfragmenten (elementen - inhoudsfragmenten)
description: Leer hoe u met Inhoudsfragmenten in Adobe Experience Manager (AEM) as a Cloud Service inhoud kunt ontwerpen, maken, curven en gebruiken, ideaal voor het ontwerpen van pagina's en het leveren zonder kop. Ook hoe zij samen met MSM kunnen worden gebruikt.
exl-id: db17eff1-4252-48d5-bb67-5e476e93ef7e
feature: Content Fragments
role: User
source-git-commit: 257930bc2633a0d31ad3bd28305b8159597befa5
workflow-type: tm+mt
source-wordcount: '2230'
ht-degree: 2%

---

# Werken met inhoudsfragmenten {#working-with-content-fragments}

Met Adobe Experience Manager (AEM) as a Cloud Service, laat de Fragmenten van de Inhoud u, ontwerp, leiden, en [pagina-onafhankelijke inhoud publiceren](/help/sites-cloud/authoring/fragments/content-fragments.md). Zo kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties/via meerdere kanalen, ideaal voor levering zonder kop. Zij kunnen ook samen met [Beheer van meerdere sites, zodat u uw inhoud opnieuw kunt gebruiken](#reusing-content-fragments-with-msm).

Inhoudsfragmenten bevatten gestructureerde inhoud:

* Zij zijn gebaseerd op een [Inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md), waarin een vooraf gedefinieerde structuur voor het resulterende fragment wordt gedefinieerd.
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

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

>[!NOTE]
>
>Inhoudsfragmenten zijn een functie Sites, maar worden opgeslagen als **Activa**.
>
>Ze worden nu voornamelijk beheerd met de **[Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console)** console, hoewel zij nog van kunnen leiden **Activa** console. Deze afdeling heeft betrekking op het beheer van de **Activa** console.
>
>Er zijn twee editors voor het ontwerpen van inhoudsfragmenten. In deze sectie wordt de oorspronkelijke editor beschreven, die voornamelijk wordt geopend vanuit de **Activa** console. Zie de documentatie van Plaatsen, [Inhoudsfragmenten - Authoring](/help/sites-cloud/administering/content-fragments/authoring.md), voor meer informatie over de nieuwe editor (die voornamelijk wordt benaderd vanuit de **Inhoudsfragmenten** console). Beide editors hebben een knevelschakelaar in de hoogste toolbar om snelle toegang tot de andere redacteur te verlenen.

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van uw inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md) - het inschakelen, maken en definiëren van uw modellen
* [Inhoudsfragmenten beheren](/help/assets/content-fragments/content-fragments-managing.md) - maak uw inhoudsfragmenten; bewerk, publiceer en verwijs vervolgens naar
* [Variaties - Fragmentinhoud ontwerpen](/help/assets/content-fragments/content-fragments-variations.md) - de fragmentinhoud ontwerpen en variaties van het stramien maken
* [Markering](/help/assets/content-fragments/content-fragments-markdown.md) - markeringssyntaxis gebruiken voor uw fragment
* [Gekoppelde inhoud gebruiken](/help/assets/content-fragments/content-fragments-assoc-content.md) - gekoppelde inhoud toevoegen
* [Metagegevens - Fragmenteigenschappen](/help/assets/content-fragments/content-fragments-metadata.md) - de fragmenteigenschappen weergeven en bewerken
* Gebruiken [Inhoudsfragmenten, in combinatie met GraphQL, zodat u inhoud kunt leveren](/help/assets/content-fragments/content-fragments-graphql.md) voor gebruik in uw toepassingen. Om dit te helpen, kunt u een voorvertoning weergeven [JSON-uitvoer](/help/assets/content-fragments/content-fragments-json-preview.md).
* [Inhoudsfragmenten opnieuw gebruiken met MSM](#reusing-content-fragments-with-msm)

>[!NOTE]
>
>Deze pagina&#39;s kunnen worden gelezen met:
>
>* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* [Contentfragmenten aanpassen en uitbreiden](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
>* De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md)

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
>**Inhoudsfragmenten** en **[Ervaar fragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)** Er zijn verschillende functies binnen AEM:
>* **Inhoudsfragmenten** redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals tekst, cijfers en datums.
>* **Ervaar fragmenten** volledig opgemaakt zijn, een fragment van een webpagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie ook voor meer informatie [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

## Inhoudsfragmenten en inhoudsservices {#content-fragments-and-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden gebruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

De levering wordt uitgevoerd in JSON-indeling met behulp van de JSON Exporter.

AEM Inhoudsfragmenten kunnen worden gebruikt om gestructureerde inhoud te beschrijven en te beheren. Gestructureerde inhoud wordt gedefinieerd in modellen die verschillende inhoudstypen kunnen bevatten, zoals tekst, numerieke gegevens, booleaanse gegevens, datum en tijd en meer.

Samen met de JSON-exportmogelijkheden van AEM kerncomponenten kan deze gestructureerde inhoud vervolgens worden gebruikt om AEM inhoud aan andere kanalen dan AEM pagina&#39;s te leveren.

>[!NOTE]
>
>Zie [Koploos en AEM](/help/headless/introduction.md) voor een inleiding op Headless Development voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud. Zie [Elementen vertalen](/help/assets/translate-assets.md) voor nadere informatie.

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* Opgeslagen als **Activa**:

   * Inhoudsfragmenten (en hun variaties) kunnen worden gemaakt en onderhouden op basis van de **Activa** console.
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Gebruikt in de [pagina-editor van de component Content Fragment](/help/sites-cloud/authoring/fragments/content-fragments.md) (verwijzende component):

   * De **Inhoudsfragment** is beschikbaar voor paginaauteurs. Hiermee kunnen ze naar het vereiste inhoudsfragment verwijzen en dit leveren in HTML- of JSON-indeling.

* Toegankelijk met de [GRAPHQL API AEM](/help/headless/graphql-api/content-fragments.md).

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Geen lay-out of ontwerp hebben (enige tekstopmaak is mogelijk in de modus RTF).
* Bevat een of meer [samenstellende delen](#constituent-parts-of-a-content-fragment).
* [Afbeeldingen bevatten of kunnen hiermee worden verbonden](#fragments-with-visual-assets).
* Wordt gebruikt [tussenliggende inhoud](#in-between-content-when-page-authoring-with-content-fragments) wanneer er op een pagina naar wordt verwezen.
* Ze zijn onafhankelijk van het leveringsmechanisme (pagina, kanaal).

### Fragmenten met visuele elementen {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Elementen kunnen op verschillende manieren met een inhoudsfragment worden gebruikt, elk met zijn eigen voordelen:

* **Element invoegen** in een fragment (fragmenten met gemengde media)

   * Ze maken deel uit van het fragment (zie [Delen van een inhoudsfragment maken](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie [Elementen invoegen in uw fragment](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de fragmenteditor voor meer informatie.

  >[!NOTE]
  >
  >Visuele elementen die in het inhoudsfragment zelf worden ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Gekoppelde inhoud**

   * Verbonden met een fragment; maar geen vast deel van het fragment (zie [Delen van een inhoudsfragment maken](#constituent-parts-of-a-content-fragment)).
   * Heeft enige flexibiliteit voor positionering.
   * Eenvoudig beschikbaar voor gebruik (als tussenliggende inhoud) bij gebruik van het fragment op een pagina.

  Zie [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) voor meer informatie .

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Heeft enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.

  Zie [Browser voor middelen](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser) voor meer informatie .

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Fragmentelementen**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Tekstblokken, vaak meerdere regels die zijn gescheiden als afzonderlijke entiteiten.

   * In de modi [Tekst met opmaak](/help/assets/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Elementen die in een fragment zijn ingevoegd (gemengde-mediafragmenten)**

   * Elementen (afbeeldingen) die in het feitelijke fragment zijn ingevoegd en worden gebruikt als de interne inhoud van een fragment.
   * Ingesloten in het alineasysteem van het fragment.
   * Kan worden opgemaakt wanneer de [fragment wordt gebruikt of er wordt naar verwezen op een pagina](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan alleen worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment met de opdracht [Opmaak RTF in de fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

     >[!CAUTION]
     >
     >Elementen kunnen (onbedoeld) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

     >[!NOTE]
     >
     >Elementen kunnen ook worden toegevoegd als aanvullende (tussen) inhoud wanneer een fragment op een pagina wordt gebruikt. Hierbij wordt een van de volgende [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) of elementen van de middelenbrowser.

* **Gekoppelde inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Afbeeldingen, video&#39;s of andere fragmenten worden meestal weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De activa zijn [gekoppeld aan fragmenten in de vorm van verzamelingen](/help/assets/content-fragments/content-fragments-assoc-content.md); de bijbehorende verzamelingen stellen de auteur in staat te beslissen welke elementen moeten worden gebruikt wanneer deze de pagina ontwerpen.

      * Verzamelingen kunnen tijdens het ontwerpen van fragmenten als standaardinhoud worden gekoppeld.
      * [Activa (DAM) Inzamelingen](/help/assets/manage-collections.md) vormen de basis voor de bijbehorende inhoud van fragmenten.
   * Desgewenst kunt u het fragment zelf ook aan een verzameling toevoegen om het bijhouden van het fragment te vergemakkelijken.

* **Fragmentmetagegevens**

   * Gebruik de [Metagegevensschema&#39;s voor elementen](/help/assets/metadata-schemas.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of hoger:

         * Door het fragment weer te geven/te bewerken **Eigenschappen** vanaf de console
         * Door de **Metagegevens** wanneer in de fragmenteditor

  >[!CAUTION]
  >
  >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

* **Master**

   * Een deel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Stramien kan niet worden verwijderd.

   * Stramien is toegankelijk in de fragmenteditor onder **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**.
   * Stramien is geen variatie als zodanig, maar is de basis van alle variaties.

* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor een redactioneel doel; kan gerelateerd zijn aan een kanaal, maar is niet verplicht, kunnen ook voor lokale ad-hocwijzigingen worden gebruikt.
   * Wordt gemaakt als kopieën van **Master**, maar kan vervolgens naar wens worden bewerkt. Er is inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * Variaties kunnen [gesynchroniseerd](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) met stramien als de stramieninhoud is bijgewerkt.
   * Kan [Samengevat](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) om de tekst snel af te kappen tot een vooraf gedefinieerde lengte.
   * Beschikbaar onder [Variaties](/help/assets/content-fragments/content-fragments-variations.md) tabblad van de fragmenteditor.

### Tussen inhoud wanneer pagina&#39;s worden gemaakt met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussenliggende inhoud:

* Beschikbaar voor gebruik in de Pagina-editor bij het werken met inhoudsfragmenten.
* [Aanvullende inhoud die wordt toegevoegd binnen de stroom van een fragment](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-in-between-content) nadat deze op een pagina wordt gebruikt of ernaar wordt verwezen.
* Beschikbaar voor gebruik in de [Pagina-editor wanneer u werkt met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md).
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Voor het maken van inhoudsfragmenten hebt u het volgende nodig:

* **Content Model**

   * zijn [toegelaten gebruikend Browser van de Configuratie](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * zijn [gemaakt met Gereedschappen](/help/assets/content-fragments/content-fragments-models.md).
   * Vereist voor [een fragment maken](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. Alle andere opties zijn optioneel.
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* **Component Inhoudsfragment**

   * Instrumentaal voor het leveren van het fragment in HTML-indeling, JSON-indeling of beide.
   * Vereist voor [verwijzen naar het fragment op een pagina](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Verantwoordelijk voor de lay-out en levering van een fragment, dat wil zeggen, kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Wanneer u een fragment naar een pagina sleept in de ontwerpfase, wordt de vereiste component automatisch gekoppeld.

## Inhoudsfragmenten opnieuw gebruiken met MSM {#reusing-content-fragments-with-msm}

Indien benaderd via de **Activa** kunt u MSM gebruiken en actieve kopieën maken voor uw fragmenten.

Zie voor meer informatie:

* [Inhoudsfragmenten opnieuw gebruiken met MSM](/help/assets/content-fragments/content-fragments-msm.md)
* [Elementen hergebruiken met MSM voor middelen](/help/assets/reuse-assets-using-msm.md).

Deze functie [overerving](/help/assets/content-fragments/content-fragments-variations.md#inheritance) voor zowel variaties als afzonderlijke velden van uw fragmenten.

>[!CAUTION]
>
>Als u MSM (dat tot exemplaren van Inhoudsfragmenten leidt) wilt gebruiken, dan om het even welk **Uniek** de beperkingen moeten worden verwijderd uit alle gegevenstypen die in de respectieve [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md).

## Voorbeeldengebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bedenk bij het ontwerpen van het fragment wat wordt gebruikt en waar het wordt gebruikt.

### WKND-voorbeeld {#wknd-sample}

De [WKND-site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) voorbeelden worden gegeven om u te helpen meer te leren over AEM as a Cloud Service.

Het WKND-project omvat:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:
  `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:
  `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
