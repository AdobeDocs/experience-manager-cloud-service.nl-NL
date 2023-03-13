---
title: Werken met contentfragmenten
description: Leer hoe u met Content Fragments in Adobe Experience Manager (AEM) as a Cloud Service inhoud kunt ontwerpen, maken, curven en gebruiken die onafhankelijk is van pagina's. Dit is ideaal voor het ontwerpen van pagina's en het leveren zonder kop.
feature: Content Fragments
role: User
exl-id: d12b1dda-85ce-4665-b8b1-915b74231bb8
source-git-commit: 9c3153efe4aacd1666663cd5eb718f75329202af
workflow-type: tm+mt
source-wordcount: '2066'
ht-degree: 3%

---

# Werken met contentfragmenten {#working-with-content-fragments}

Met Adobe Experience Manager (AEM) as a Cloud Service, staan de Fragments van de Inhoud u toe om te ontwerpen, tot stand te brengen, te leiden en [pagina-onafhankelijke inhoud publiceren](/help/sites-cloud/authoring/fundamentals/content-fragments.md) Zo kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties/via meerdere kanalen, ideaal voor het ontwerpen van pagina&#39;s en voor levering zonder kop.

Inhoudsfragmenten bevatten gestructureerde inhoud:

* Zij zijn gebaseerd op een [Inhoudsfragmentmodel](/help/sites-cloud/administering/content-fragments/content-fragments-models.md), waarin een vooraf gedefinieerde structuur voor het resulterende fragment wordt gedefinieerd.
* De structuur kan liggen tussen:
   * Basis
      * Bijvoorbeeld een tekstveld met één regel tekst.
      * Kan worden gebruikt voor het voorbereiden van eenvoudige inhoud voor gebruik in paginaontwerp.
   * Complex
      * Een combinatie van een groot aantal velden met verschillende gegevenstypen, zoals tekst, getal, boolean, gegevens en tijd.
      * Kan worden gebruikt voor het voorbereiden van meer gestructureerde inhoud voor het ontwerpen van pagina&#39;s of voor levering aan uw toepassing.
   * Genest
      * Met de beschikbare gegevenstypen waarnaar wordt verwezen, kunt u de inhoud nesten.
      * De neiging om voor levering aan uw toepassing te worden gebruikt.

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van uw inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md)
* [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments-models.md) - het inschakelen, maken en definiëren van uw modellen
* [De console Inhoudsfragmenten gebruiken](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) - om toegang te krijgen tot uw fragmenten, deze te maken, te bewerken, te publiceren en ernaar te verwijzen
* [Inhoudsfragmenten beheren](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md) - maak uw inhoudsfragmenten; vervolgens bewerken, publiceren en verwijzen
* [Variaties - Fragmentinhoud ontwerpen](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) - de fragmentinhoud ontwerpen en variaties van de Master inhoud maken
* [Markering](/help/sites-cloud/administering/content-fragments/content-fragments-markdown.md) - markeringssyntaxis gebruiken voor uw fragment
* [Gekoppelde inhoud gebruiken](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) - gekoppelde inhoud toevoegen
* [Metagegevens - Fragmenteigenschappen](/help/sites-cloud/administering/content-fragments/content-fragments-metadata.md) - de fragmenteigenschappen weergeven en bewerken
* Gebruik uw inhoudsfragmenten:

   * [voor paginaontwerp](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
   * [samen met GraphQL, voor headless levering aan uw toepassingen](/help/sites-cloud/administering/content-fragments/content-fragments-graphql.md).
Om dit te helpen, kunt u een voorvertoning weergeven van de [Boomstructuur](/help/sites-cloud/administering/content-fragments/content-fragments-structure-tree.md) en [JSON-uitvoer](/help/sites-cloud/administering/content-fragments/content-fragments-json-preview.md).

>[!NOTE]
>
>Deze pagina&#39;s kunnen worden gelezen in combinatie met:
>
>* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* [Contentfragmenten aanpassen en uitbreiden](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)


Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* fysiek kanaal; bijvoorbeeld desktop, mobiel.
* Vorm van levering in een fysiek kanaal; bijvoorbeeld de pagina &#39;&#39;productdetails&#39;&#39;, &#39;&#39;productcategoriepagina&#39;&#39; voor desktop&#39; of &#39;&#39;mobiel web&#39;&#39; en &#39;&#39;mobiele app&#39; voor mobiele apparaten.

U (waarschijnlijk) wilt echter niet exact dezelfde inhoud gebruiken voor alle kanalen. U moet de inhoud optimaliseren op basis van het specifieke kanaal.

Met inhoudelementen kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan de tekst toe door elementen (gemengde-mediafragmenten) in te voegen.
* Maak geneste inhoud om de complexiteit van uw gegevens te weerspiegelen.

Deze inhoudsfragmenten kunnen vervolgens worden samengevoegd om via verschillende kanalen ervaringen op te doen.

>[!NOTE]
>
>**Inhoudsfragmenten** en **[Ervaar fragmenten](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** zijn verschillende functies in AEM:
>* **Inhoudsfragmenten** redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals teksten, cijfers en datums.
>* **Ervaar fragmenten** volledig zijn ingedeeld; een fragment van een webpagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie ook voor meer informatie [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

## Inhoudsfragmenten en inhoudsservices {#content-fragments-and-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina&#39;s wordt gevestigd.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

De levering wordt uitgevoerd in JSON-indeling met behulp van de JSON Exporter.

AEM Inhoudsfragmenten kunnen worden gebruikt om gestructureerde inhoud te beschrijven en te beheren. Gestructureerde inhoud wordt gedefinieerd in modellen die verschillende inhoudstypen kunnen bevatten; waaronder tekst, numerieke gegevens, booleaanse gegevens, datum en tijd en meer.

Samen met de JSON-exportmogelijkheden van AEM kerncomponenten kan deze gestructureerde inhoud vervolgens worden gebruikt om AEM inhoud aan andere kanalen dan AEM pagina&#39;s te leveren.

>[!NOTE]
>
>Zie [Koploos en AEM](/help/headless/introduction.md) voor een inleiding op Headless Development voor AEM Sites as a Cloud Service.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud. Zie [Vertaalmiddelen](/help/assets/translate-assets.md) voor nadere informatie.

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* A **Sites** gebruiken.

* Opgeslagen als **Activa**:

   * Inhoudsfragmenten (en hun variaties) kunnen worden gemaakt en onderhouden op basis van de **Inhoudsfragmenten** en de **Activa** console.
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Gebruikt in de [pagina-editor via de component Inhoudsfragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (verwijzende component):

   * De **Inhoudsfragment** is beschikbaar voor auteurs van pagina&#39;s. Hiermee kunnen ze naar het vereiste inhoudsfragment verwijzen en dit leveren in HTML- of JSON-indeling.

* Toegankelijk met de [GraphQL API AEM](/help/headless/graphql-api/content-fragments.md).

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Zijn zonder lay-out of ontwerp (wat tekst het formatteren is mogelijk op Rich Text wijze).
* Bevat een of meer, [samenstellende delen](#constituent-parts-of-a-content-fragment).
* Kan [afbeeldingen bevatten of ermee verbonden zijn](#fragments-with-visual-assets).
* Kan gebruiken [tussenliggende inhoud](#in-between-content-when-page-authoring-with-content-fragments) wanneer verwezen op een pagina.

* zijn onafhankelijk van het leveringsmechanisme (d.w.z. pagina, kanaal).

### Fragmenten met visuele elementen {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Elementen kunnen op verschillende manieren met een inhoudsfragment worden gebruikt. elk met zijn eigen voordeel:

* **Element invoegen** in een fragment (gemengde-mediafragmenten)

   * Vormen een integrerend deel van het fragment (zie [Delen van een inhoudsfragment maken](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie [Elementen invoegen in uw fragment](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de fragmenteditor voor meer informatie.

   >[!NOTE]
   >
   >Visuele elementen die in het inhoudsfragment zelf zijn ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Gekoppelde inhoud**

   * zijn verbonden met een fragment; maar geen vast deel van het fragment (zie [Delen van een inhoudsfragment maken](#constituent-parts-of-a-content-fragment)).
   * Biedt enige flexibiliteit voor positionering.
   * U kunt het fragment gemakkelijk gebruiken (als tussenliggende inhoud) op een pagina.
   * Zie [Gekoppelde inhoud](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) voor meer informatie .

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Biedt enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.
   * Zie [Browser voor middelen](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) voor meer informatie .

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Fragmentelementen**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Tekstblokken, vaak meerdere regels, die zijn gescheiden als afzonderlijke entiteiten.

   * In de modi [Tekst met opmaak](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Elementen die in een fragment zijn ingevoegd (gemengde-mediafragmenten)**

   * Elementen (afbeeldingen) die in het feitelijke fragment zijn ingevoegd en worden gebruikt als de interne inhoud van een fragment.
   * zijn ingesloten in het alineasysteem van het fragment.
   * Kan worden opgemaakt wanneer de [fragment wordt gebruikt of er wordt naar verwezen op een pagina](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan alleen worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment met [Opmaak RTF in de fragmenteditor](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

      >[!CAUTION]
      >
      >Elementen kunnen (onbedoeld) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

      >[!NOTE]
      >
      >Elementen kunnen ook worden toegevoegd als [extra inhoud (tussen)](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) bij het gebruik van een fragment op een pagina; het gebruiken van of Bijbehorende Inhoud of activa van browser van Activa.

* **Gekoppelde inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Meestal worden afbeeldingen, video&#39;s of andere fragmenten weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De activa zijn [gekoppeld aan fragmenten via verzamelingen](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md); Met gekoppelde verzamelingen kan de auteur beslissen welke elementen worden gebruikt wanneer deze de pagina ontwerpt.

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

   * Een integraal onderdeel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Master kan niet worden verwijderd.
   * Master is toegankelijk in de fragmenteditor onder **[Variaties](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md)**.
   * Master is geen variatie als zodanig, maar is de basis van alle variaties.


* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor redactionele doeleinden; kan verband houden met het kanaal, maar is niet verplicht, en kan ook voor ad-hoclokale aanpassingen worden gebruikt.
   * Wordt gemaakt als kopieën van **Master**, maar kan vervolgens naar behoefte worden bewerkt; er is gewoonlijk inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * Variaties kunnen [gesynchroniseerd](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#synchronizing-with-master) master als de Master inhoud is bijgewerkt.
   * Kan [Samengevat](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#summarizing-text) om de tekst snel af te kappen tot een vooraf gedefinieerde lengte.
   * Beschikbaar onder [Variaties](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md) tabblad van de fragmenteditor.

### Tussen inhoud wanneer pagina&#39;s worden gemaakt met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussen inhoud:

* Is beschikbaar voor gebruik in de Redacteur van de Pagina wanneer het werken met Inhoudsfragmenten.
* Is [extra inhoud die is toegevoegd binnen de stroom van een fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content) als er op een pagina naar is verwezen of er gebruik van is gemaakt.
* Is beschikbaar voor gebruik in [Pagina-editor wanneer u werkt met inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Voor het maken van inhoudfragmenten hebt u het volgende nodig:

* **Inhoudsmodel**

   * zijn [toegelaten gebruikend Browser van de Configuratie](/help/sites-cloud/administering/content-fragments/content-fragments-configuration-browser.md).
   * zijn [gemaakt met Gereedschappen](/help/sites-cloud/administering/content-fragments/content-fragments-models.md).
   * Vereist voor [een fragment maken](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#creating-content-fragments).
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. alles is optioneel .
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* **Component Inhoudsfragment**

   * Instrumentaal voor het leveren van het fragment in HTML- en/of JSON-indeling.
   * Vereist voor [verwijzen naar het fragment op een pagina](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Verantwoordelijk voor de lay-out en levering van een fragment; d.w.z. kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Als u een fragment naar een pagina sleept tijdens het ontwerpen, wordt de vereiste component automatisch gekoppeld.

## Voorbeeldgebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bij het ontwerpen van het fragment moet u rekening houden met de plaats waar het fragment wordt gebruikt.

### WKND-voorbeeld {#wknd-sample}

De [WKND-site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) voorbeelden worden gegeven om u te helpen meer te leren over AEM as a Cloud Service.

Het WKND-project omvat:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:
   `http://<hostname>:<port>/libs/dam/cfm/models/console/content/models.html/conf/wknd`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:
   `http://<hostname>:<port>/assets.html/content/dam/wknd/en`
