---
title: Werken met contentfragmenten
description: Leer hoe u met Content Fragments in Adobe Experience Manager (AEM) als Cloud Service pagina-onafhankelijke inhoud kunt ontwerpen, maken, beheren en gebruiken.
translation-type: tm+mt
source-git-commit: da8fcf1288482d406657876b5d4c00b413461b21
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 3%

---


# Werken met contentfragmenten{#working-with-content-fragments}

>[!CAUTION]
>
>De AEM GraphQL API voor de Levering van Inhoudsfragmenten is op verzoek beschikbaar.
>
>Neem contact op met [Adobe Support](https://experienceleague.adobe.com/?lang=en&amp;support-solution=General#support) om de API voor uw AEM in te schakelen als een programma voor Cloud Servicen.

Met Adobe Experience Manager (AEM) als Cloud Service kunt u met Inhoudsfragmenten pagina-onafhankelijke inhoud ontwerpen, maken, beheren en [publiceren. ](/help/sites-cloud/authoring/fundamentals/content-fragments.md) Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties/via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud:

* Ze zijn gebaseerd op een [Inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md), dat een structuur vooraf definieert voor het resulterende fragment.
* De structuur kan liggen tussen:
   * Basis
      * Bijvoorbeeld een tekstveld met één regel tekst.
      * Kan worden gebruikt voor het voorbereiden van eenvoudige inhoud voor gebruik in paginaontwerp.
   * Complex
      * Een combinatie van een groot aantal velden met verschillende gegevenstypen, zoals tekst, getal, boolean, gegevens en tijd.
      * Kan worden gebruikt voor het voorbereiden van meer gestructureerde inhoud voor het ontwerpen van pagina&#39;s of voor levering aan uw toepassing.

<!--
  * Nested
    * The reference data types available allow you to nest your content.
    * Tends to be used for delivery to your application.
-->

Inhoudsfragmenten kunnen ook worden geleverd in JSON-indeling, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe, door veelvoudige inhoudfragment kerncomponenten op de pagina toe te voegen die voor levering API wordt gebruikt

Deze en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van uw inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/assets/content-fragments/content-fragments-configuration-browser.md)
* [Modellen](/help/assets/content-fragments/content-fragments-models.md)  voor inhoudsfragmenten - uw modellen inschakelen, maken en definiëren
* [Inhoudsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)  beheren: maak inhoudsfragmenten. vervolgens bewerken, publiceren en verwijzen
* [Variaties - Inhoud](/help/assets/content-fragments/content-fragments-variations.md)  fragment ontwerpen - De fragmentinhoud ontwerpen en variaties van de Master inhoud maken
* [Markering](/help/assets/content-fragments/content-fragments-markdown.md) : markeringssyntaxis gebruiken voor het fragment
* [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md)  gebruiken - gekoppelde inhoud toevoegen
* [Metagegevens - Fragmenteigenschappen](/help/assets/content-fragments/content-fragments-metadata.md)  - de fragmenteigenschappen weergeven en bewerken
* Gebruik [Inhoudsfragmenten, samen met GraphQL, om inhoud](/help/assets/content-fragments/content-fragments-graphql.md) voor gebruik in uw toepassingen te leveren. Om dit te helpen, kunt u voorproef [JSON output](/help/assets/content-fragments/content-fragments-json-preview.md).

>[!NOTE]
>
>Deze pagina&#39;s kunnen worden gelezen in combinatie met:
>
>* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
>* [Contentfragmenten aanpassen en uitbreiden](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [AEM GraphQL API voor gebruik met Content Fragments](/help/assets/content-fragments/graphql-api-content-fragments.md)


Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* fysiek kanaal; bijvoorbeeld desktop, mobiel.
* Vorm van levering in een fysiek kanaal; Bijvoorbeeld de pagina met productdetails, de pagina met productcategorieën voor desktops of mobiele websites, de pagina met mobiele apps voor mobiele apparaten.

U (waarschijnlijk) wilt echter niet exact dezelfde inhoud gebruiken voor alle kanalen. U moet de inhoud optimaliseren op basis van het specifieke kanaal.

Met inhoudelementen kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan uw tekst toe door elementen (gemengde-mediafragmenten) in te voegen.

<!--
* Create nested content to reflect the complexity of your data.
-->

Deze inhoudsfragmenten kunnen vervolgens worden samengevoegd om via verschillende kanalen ervaringen op te doen.

>[!NOTE]
>
>**Content** Fragmentations en  **[Experience](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** Fragmentes zijn verschillende functies in AEM:
>* **Inhoudsfragmenten** zijn redactionele inhoud die kan worden gebruikt voor toegang tot gestructureerde gegevens, waaronder teksten, getallen en datums. Het zijn pure inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out.
>* **De inhoud van de** ervaringen met fragmentatie is volledig afgebakend. een fragment van een webpagina.

>
>
De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie ook [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=en#content-fragments) voor meer informatie.

## Content Fragments and Content Services {#content-fragments-and-content-services}

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
>Zie [Headless and AEM](/help/implementing/developing/headless/introduction.md) voor een inleiding tot Headless Development voor AEM Sites als Cloud Service.

>[!NOTE]
>
>AEM ondersteunt ook het vertalen van fragmentinhoud.

<!--
>[!NOTE]
>
>AEM also supports the translation of fragment content. See [Creating Translation Projects for Content Fragments](/help/assets/creating-translation-projects-for-content-fragments.md) for further information.
-->

## Inhoudstype {#content-type}

Inhoudsfragmenten zijn:

* Opgeslagen als **Middelen**:

   * Inhoudsfragmenten (en hun variaties) kunnen worden gemaakt en onderhouden met de console **Middelen**.
   * Gemaakt en bewerkt in de Inhoudsfragmenteditor.

* Wordt gebruikt in de [pagina-editor met behulp van de component Content Fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md) (verwijzende component):

   * De component **Inhoudsfragment** is beschikbaar voor auteurs van pagina&#39;s. Hiermee kunnen ze naar het vereiste inhoudsfragment verwijzen en dit leveren in HTML- of JSON-indeling.

* Toegankelijk met de [AEM GraphQL API](/help/assets/content-fragments/graphql-api-content-fragments.md).

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Zijn zonder lay-out of ontwerp (wat tekst het formatteren is mogelijk op Rich Text wijze).
* Bevat een of meer [samenstellende delen](#constituent-parts-of-a-content-fragment).
* Kan [afbeeldingen bevatten of daarmee zijn verbonden](#fragments-with-visual-assets).
* Kan [tussen inhoud](#in-between-content-when-page-authoring-with-content-fragments) gebruiken wanneer verwezen op een pagina.

* zijn onafhankelijk van het leveringsmechanisme (d.w.z. pagina, kanaal).

### Fragmenten met visuele elementen {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Elementen kunnen op verschillende manieren met een inhoudsfragment worden gebruikt. elk met zijn eigen voordeel:

* **Element invoegen** in een fragment (gemengde-mediafragmenten)

   * Vormen een integraal deel van het fragment (zie [Delen van een inhoudsfragment](#constituent-parts-of-a-content-fragment)).
   * De positie van het element definiëren.
   * Zie [Elementen invoegen in uw fragment](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment) in de fragmenteditor voor meer informatie.

   >[!NOTE]
   >
   >Visuele elementen die in het inhoudsfragment zelf zijn ingevoegd, worden aan de voorafgaande alinea gekoppeld. Wanneer het fragment aan een pagina wordt toegevoegd, worden deze elementen ten opzichte van die alinea verplaatst wanneer tussenliggende inhoud wordt toegevoegd.

* **Gekoppelde inhoud**

   * zijn verbonden met een fragment; maar geen vast deel van het fragment (zie [Delen van een inhoudsfragment](#constituent-parts-of-a-content-fragment)).
   * Biedt enige flexibiliteit voor positionering.
   * U kunt het fragment gemakkelijk gebruiken (als tussenliggende inhoud) op een pagina.
   * Zie [Gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) voor meer informatie.

* Assets die beschikbaar zijn in de **assetbrowser** van de pagina-editor

   * Volledige flexibiliteit toestaan voor de selectie van een element.
   * Biedt enige flexibiliteit voor positionering.
   * Bevat niet het concept dat voor een specifiek fragment wordt goedgekeurd.
   * Zie [Assets Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser) voor meer informatie.

### Onderdelen van een inhoudsfragment {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Fragmentelementen**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een inhoudsmodel om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Tekstblokken, vaak meerdere regels, die zijn gescheiden als afzonderlijke entiteiten.

   * In de modi [Tekst met opmaak](/help/assets/content-fragments/content-fragments-variations.md#rich-text) en [Markdown](/help/assets/content-fragments/content-fragments-variations.md#markdown) kan een alinea worden opgemaakt als een koptekst. In dat geval horen die alinea en de volgende alinea bij elkaar als één eenheid.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Elementen die in een fragment zijn ingevoegd (gemengde-mediafragmenten)**

   * Elementen (afbeeldingen) die in het feitelijke fragment zijn ingevoegd en worden gebruikt als de interne inhoud van een fragment.
   * zijn ingesloten in het alineasysteem van het fragment.
   * Kan worden opgemaakt wanneer het [fragment wordt gebruikt/op een pagina](/help/sites-cloud/authoring/fundamentals/content-fragments.md) van verwijzingen wordt voorzien.
   * Kan alleen met de fragmenteditor worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment. Deze handelingen kunnen niet worden uitgevoerd in de paginaeditor.
   * Kan alleen worden toegevoegd aan, verwijderd uit of verplaatst binnen een fragment met [RTF-indeling in de fragmenteditor](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
   * Kan alleen worden toegevoegd aan tekstelementen met meerdere regels (elk fragmenttype).
   * Aan de voorgaande tekst (alinea) worden toegevoegd.

      >[!CAUTION]
      >
      >Elementen kunnen (onbedoeld) uit een fragment worden verwijderd door over te schakelen op de indeling Onbewerkte tekst.

      >[!NOTE]
      >
      >Elementen kunnen ook worden toegevoegd als [extra (tussenliggende) inhoud](/help/sites-cloud/authoring/fundamentals/content-fragments.md#using-associated-content) bij het gebruik van een fragment op een pagina. het gebruiken van of Bijbehorende Inhoud of activa van browser van Middelen.

* **Gekoppelde inhoud**

   * Dit is inhoud die zich buiten een fragment bevindt, maar die van redactionele betekenis is. Meestal worden afbeeldingen, video&#39;s of andere fragmenten weergegeven.
   * De afzonderlijke elementen in de verzameling zijn beschikbaar voor gebruik met het fragment in de pagina-editor wanneer het aan een pagina wordt toegevoegd. Dit betekent dat ze optioneel zijn, afhankelijk van de vereisten van het specifieke kanaal.
   * De elementen zijn [gekoppeld aan fragmenten via verzamelingen](/help/assets/content-fragments/content-fragments-assoc-content.md); Met gekoppelde verzamelingen kan de auteur beslissen welke elementen worden gebruikt wanneer deze de pagina ontwerpt.

      * Verzamelingen kunnen tijdens het ontwerpen van fragmenten als standaardinhoud worden gekoppeld.
      * [Elementen (DAM) ](/help/assets/manage-collections.md) Verzamelingen vormen de basis voor de bijbehorende inhoud van fragmenten.
   * Desgewenst kunt u het fragment zelf ook aan een verzameling toevoegen om het bijhouden van het fragment te vergemakkelijken.

* **Fragmentmetagegevens**

   * Gebruik de [schema&#39;s voor metagegevens van elementen](/help/assets/metadata-schemas.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of hoger:

         * Door het fragment **Eigenschappen** vanuit de console weer te geven/te bewerken
         * Door de **Metagegevens** te bewerken in de fragmenteditor

   >[!CAUTION]
   >
   >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

* **Master**

   * Een integraal onderdeel van het fragment

      * Elk inhoudsfragment heeft één instantie van Master.
      * Master kan niet worden verwijderd.
   * Master is toegankelijk in de fragmentredacteur onder **[Variaties](/help/assets/content-fragments/content-fragments-variations.md)**.
   * Master is geen variatie als zodanig, maar is de basis van alle variaties.


* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor redactionele doeleinden; kan verband houden met het kanaal, maar is niet verplicht, en kan ook voor ad-hoclokale aanpassingen worden gebruikt.
   * worden gemaakt als kopieën van **Master**, maar kunnen vervolgens naar wens worden bewerkt; er is gewoonlijk inhoudsoverlap tussen de variaties zelf.
   * Kan worden gedefinieerd tijdens het ontwerpen van fragmenten.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * Variaties kunnen [gesynchroniseerd](/help/assets/content-fragments/content-fragments-variations.md#synchronizing-with-master) met Master zijn als de Master inhoud is bijgewerkt.
   * Kan [Samengevat](/help/assets/content-fragments/content-fragments-variations.md#summarizing-text) zijn om de tekst snel af te kappen tot een vooraf gedefinieerde lengte.
   * Beschikbaar op het tabblad [Variaties](/help/assets/content-fragments/content-fragments-variations.md) van de fragmenteditor.

### Tussenliggende inhoud bij pagina&#39;s ontwerpen met inhoudsfragmenten {#in-between-content-when-page-authoring-with-content-fragments}

Tussen inhoud:

* Is beschikbaar voor gebruik in de Redacteur van de Pagina wanneer het werken met Inhoudsfragmenten.
* Is [extra inhoud toegevoegd binnen de stroom van een fragment](/help/sites-cloud/authoring/fundamentals/content-fragments.md#adding-in-between-content) zodra het is gebruikt/van verwijzingen voorzien op een pagina.
* Is beschikbaar voor gebruik in [de Redacteur van de Pagina wanneer het werken met Inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
* Tussen-inhoud kan aan elk fragment worden toegevoegd, waarbij slechts één element zichtbaar is.
* De bijbehorende inhoud kan worden gebruikt, evenals activa en/of componenten van aangewezen browser.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

### Vereist door fragmenten {#required-by-fragments}

Voor het maken van inhoudfragmenten hebt u het volgende nodig:

* **Inhoudsmodel**

   * Zijn [toegelaten gebruikend Browser van de Configuratie](/help/assets/content-fragments/content-fragments-configuration-browser.md).
   * [gemaakt met Tools](/help/assets/content-fragments/content-fragments-models.md).
   * Vereist om [een fragment](/help/assets/content-fragments/content-fragments-managing.md#creating-content-fragments) te maken.
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsmodellen vereisen een titel en één gegevenselement. alles is optioneel .
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* **Component Inhoudsfragment**

   * Instrumentaal voor het leveren van het fragment in HTML- en/of JSON-indeling.
   * Vereist om [naar het fragment op een pagina te verwijzen](/help/sites-cloud/authoring/fundamentals/content-fragments.md).
   * Verantwoordelijk voor de lay-out en levering van een fragment; d.w.z. kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Als u een fragment naar een pagina sleept tijdens het ontwerpen, wordt de vereiste component automatisch gekoppeld.

## Voorbeeld van gebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bij het ontwerpen van het fragment moet u rekening houden met de plaats waar het fragment wordt gebruikt.

### WKND-monster {#wknd-sample}

De [WKND Site](/help/implementing/developing/introduction/develop-wknd-tutorial.md) steekproeven worden verstrekt om u te helpen over AEM als Cloud Service leren. Het omvat voorbeeldfragmenten, deze kunnen worden gezien bij:

`hhttp://<host>:<port>/assets.html/content/dam/wknd/en/adventures`
