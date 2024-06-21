---
title: Een overzicht van het werken met inhoudsfragmenten
description: Leer hoe u met Content Fragments in AEM as a Cloud Service inhoud kunt maken en gebruiken; ideaal voor levering zonder kop en voor het schrijven van pagina's.
feature: Content Fragments
role: User, Developer, Architect
exl-id: ce9cb811-57d2-4a57-a360-f56e07df1b1a
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '1803'
ht-degree: 1%

---

# Een overzicht van het werken met inhoudsfragmenten {#overview-working-with-content-fragments}

Met Adobe Experience Manager (AEM) as a Cloud Service, staan de Fragments van de Inhoud u toe om te ontwerpen, tot stand te brengen, te leiden, en [pagina-onafhankelijke inhoud publiceren](/help/sites-cloud/authoring/fragments/content-fragments.md). Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen, ideaal voor levering zonder kop en voor het ontwerpen van pagina&#39;s.

>[!IMPORTANT]
>
>Inhoudsfragmenten kunnen worden benaderd vanuit twee consoles: **Inhoudsfragmenten** en **Activa**.
>
>Er zijn ook twee editors beschikbaar voor Content Fragments. (Beide editors zijn toegankelijk vanuit beide consoles.)
>
>In dit gedeelte worden de **Inhoudsfragmenten** en de *new* Inhoudsfragmenteditor. Deze zijn ontwikkeld voor inhoud zonder kop (hoewel ze voor alle scenario&#39;s kunnen worden gebruikt)
>
>Zie voor meer informatie:
>
>* gebruik van de **Activa** console voor [beheren van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-managing.md)
>* gebruik van de [*origineel* Inhoudsfragmenteditor](/help/assets/content-fragments/content-fragments-variations.md),
>* gebruiken [Inhoudsfragmenten voor paginaontwerp](/help/sites-cloud/authoring/fragments/content-fragments.md).


Inhoudsfragmenten bevatten gestructureerde inhoud:

* Elk fragment is gebaseerd op een [Inhoudsfragmentmodel](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Het inhoudsfragmentmodel definieert de structuur van het resulterende fragment.
* Elk fragment bestaat uit:
   * **[Hoofd](#main-and-variations)** - een integraal onderdeel van het fragment dat de kerninhoud bevat; bestaat altijd en kan niet worden verwijderd
   * **[Variaties](#main-and-variations)** - een of meer permutaties van de inhoud, gemaakt door de auteur
* De structuur kan liggen tussen:
   * Basis
      * Bijvoorbeeld een tekstveld met één regel tekst.
      * Kan worden gebruikt voor het voorbereiden van eenvoudige inhoud voor gebruik in paginaontwerp.
      * Kan ook worden gebruikt voor koploze levering aan uw toepassing.
   * Complex
      * Een combinatie van een groot aantal velden met verschillende gegevenstypen, zoals tekst, getal, boolean en datum en tijd.
      * Kan worden gebruikt voor het voorbereiden van meer gestructureerde inhoud voor het ontwerpen van pagina&#39;s of voor levering zonder kop aan uw toepassing.
   * Genest
      * Met de beschikbare gegevenstypen waarnaar wordt verwezen, kunt u de inhoud nesten.
      * De neiging om voor hoofdloze levering aan uw toepassing te worden gebruikt.

Inhoudsfragmenten kunnen ook in JSON-indeling worden geleverd, waarbij gebruik wordt gemaakt van de JSON-exportmogelijkheden (Sling Model) van AEM kerncomponenten. Deze leveringsvorm:

* biedt u de mogelijkheid om de component te gebruiken om te beheren welke elementen van een fragment moeten worden geleverd
* staat bulklevering toe; door veelvoudige toe te voegen [Core-componenten van inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) op de pagina die wordt gebruikt voor API-levering

Het aantal communicatiekanalen neemt jaarlijks toe. Doorgaans verwijzen kanalen naar het leveringsmechanisme, als:

* Fysiek kanaal, bijvoorbeeld desktop, mobiel.
* Leveringsvorm via een fysiek kanaal, bijvoorbeeld de pagina met productdetails, de pagina met productcategorieën voor desktops of de pagina Mobiel web en de pagina Mobiele apps voor mobiele apparaten.

(Waarschijnlijk) wilt u de opdracht *exact* dezelfde inhoud voor alle kanalen - u moet de inhoud optimaliseren volgens het specifieke kanaal.

Met inhoudelementen kunt u:

* Overweeg hoe u doelpubliek efficiënt langs verschillende kanalen kunt bereiken.
* Kanaalneutrale redactionele inhoud maken en beheren.
* Stel inhoudsgroepen samen voor een reeks kanalen.
* Ontwerpinhoudvariaties voor specifieke kanalen.
* Voeg afbeeldingen aan uw tekst toe door elementen in te voegen.
* Maak geneste inhoud om de complexiteit van uw gegevens te weerspiegelen.

Deze inhoudsfragmenten kunnen vervolgens worden samengesteld om ervaringen via verschillende kanalen te bieden.

>[!NOTE]
>
>**Inhoudsfragmenten** en **[Ervaar fragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)** Er zijn verschillende functies binnen AEM:
>* **Inhoudsfragmenten** redactionele inhoud, met definitie en structuur, maar zonder extra visueel ontwerp en/of lay-out. Ze kunnen worden gebruikt om onder andere toegang te krijgen tot gestructureerde gegevens, zoals tekst, cijfers en datums.
>* **Ervaar fragmenten** volledig opgemaakt zijn, een fragment van een webpagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.
>
>Zie voor meer informatie [Inhoudsfragmenten en ervaringsfragmenten in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html#content-fragments).

Deze pagina&#39;s en de volgende pagina&#39;s bevatten de taken voor het maken, configureren, onderhouden en gebruiken van de inhoudsfragmenten:

* [Functionaliteit van inhoudsfragment inschakelen voor uw instantie](/help/sites-cloud/administering/content-fragments/setup.md)
* [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) - het inschakelen, maken en definiëren van uw modellen
* [Inhoudsfragmenten maken](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment) (met de console voor inhoudsfragmenten)

Nadat de fragmenten zijn gemaakt, kunt u:

* [De console Inhoudsfragmenten gebruiken](/help/sites-cloud/administering/content-fragments/managing.md) - toegang te krijgen tot, te publiceren (om een voorvertoning of productie weer te geven) en naar uw fragmenten te verwijzen
* [De editor Inhoudsfragmenten gebruiken](/help/sites-cloud/administering/content-fragments/authoring.md) - om uw fragmenten te bewerken, te publiceren (voor voorvertoning of productie) en ernaar te verwijzen
* [Analyseren](/help/sites-cloud/administering/content-fragments/analysis.md)  de structuur van het inhoudsfragment met de editor
* [Toegang tot uw fragmenten met GraphQL, zodat u uw toepassingen zonder kop kunt bedienen](/help/sites-cloud/administering/content-fragments/content-delivery-with-graphql.md).
* [Of gebruik uw fragmenten voor paginaontwerp](/help/sites-cloud/authoring/fragments/content-fragments.md)

>[!NOTE]
>
>Deze pagina&#39;s kunnen samen met:
>
>* [Contentfragmenten aanpassen en uitbreiden](/help/implementing/developing/extending/content-fragments-customizing.md)
>* [Contentfragmenten die componenten voor rendering configureren](/help/implementing/developing/extending/content-fragments-configuring-components-rendering.md)
>* [Ondersteuning voor contentfragmenten in HTTP-API van AEM Assets](/help/assets/content-fragments/assets-api-content-fragments.md)
>* [GraphQL API AEM voor gebruik met inhoudsfragmenten](/help/headless/graphql-api/content-fragments.md)
>* [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md).
>* De [Inhoudsfragment en Inhoudsfragmentmodel OpenAPI&#39;s](/help/headless/content-fragment-openapis.md) zijn ook beschikbaar.


## Hoofd en Variaties {#main-and-variations}

Variaties zijn een belangrijk kenmerk van AEM inhoudsfragmenten. Hiermee kunt u kopieën van de **Hoofd** inhoud voor gebruik op specifieke kanalen, en scenario&#39;s, die tot hoofdloze levering van inhoud en pagina creatie nog flexibeler maken.

* **Hoofd**

   * **Hoofd** is geen variatie als zodanig, maar is de basis van alle variaties.
   * Een integraal onderdeel van het fragment

      * Elk inhoudsfragment heeft één instantie van **Hoofd**.
      * **Hoofd** kan niet worden verwijderd.

   * **Hoofd** is toegankelijk in de fragmenteditor onder **[Variaties](/help/sites-cloud/administering/content-fragments/authoring.md#variations)**.

  >[!NOTE]
  >
  >In de editor beschikbaar via de **Activa** console, **Hoofd** wordt gelabeld als **Master**.

* **Variaties**

   * Uitvoeringen van fragmenttekst die specifiek zijn voor redactionele doeleinden; kan gerelateerd zijn aan het kanaal maar is niet verplicht, maar kan ook voor lokale ad-hocwijzigingen worden gebruikt.
   * Wordt gemaakt als kopieën van **Hoofd**, maar kan vervolgens naar wens worden bewerkt; er is vaak sprake van overlappende inhoud tussen de variaties zelf.
   * Kan tijdens het ontwerpen van fragmenten worden gedefinieerd; vanuit het linkerdeelvenster.
   * Opgeslagen in het fragment, om spreiding van inhoudskopieën te voorkomen.
   * Variaties kunnen [vergeleken en gesynchroniseerd](/help/sites-cloud/administering/content-fragments/authoring.md#compare-and-synchronize-rich-text) with **Hoofd**.
  <!--
  * Can be [Summarized](/help/sites-cloud/administering/content-fragments/authoring.md#summarizing-text) to quickly truncate the text to a predefined length.
  -->

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

* A **Sites** gebruiken.

* Opgeslagen als **Activa**:

   * Inhoudsfragmenten (en hun variaties) kunnen worden gemaakt en onderhouden op basis van de [Content Fragments-console](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console).
   * Gemaakt en bewerkt in het dialoogvenster [Inhoudsfragmenteditor](/help/sites-cloud/administering/content-fragments/authoring.md).

* Toegankelijk voor de levering van inhoud met de [GRAPHQL API AEM](/help/headless/graphql-api/content-fragments.md).

* Beschikbaar in het dialoogvenster [pagina-editor met behulp van de component Inhoudsfragment](/help/sites-cloud/authoring/fragments/content-fragments.md) (verwijzende component):

   * De [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html) is beschikbaar voor auteurs van pagina&#39;s. Hiermee kunnen ze naar het vereiste inhoudsfragment in HTML- of JSON-indeling verwijzen en dit leveren.

Inhoudsfragmenten zijn een inhoudsstructuur die:

* Deze variabelen zijn niet opgemaakt of ontworpen (tekstopmaak is mogelijk voor tekstvelden).
* Deze zijn onafhankelijk van het leveringsmechanisme (zoals de pagina of het kanaal).
* Bevat een of meer, [samenstellende delen](#constituent-parts-of-a-content-fragment).
* Kan [afbeeldingen bevatten of ermee verbonden zijn](#fragments-with-visual-assets).

### Fragmenten met visuele elementen {#fragments-with-visual-assets}

Om auteurs meer controle over hun inhoud te geven, kunnen afbeeldingen worden toegevoegd aan en/of geïntegreerd met een inhoudsfragment.

Elementen kunnen op verschillende manieren met een inhoudsfragment worden gebruikt, elk met zijn eigen voordelen:

* als **Content Reference**
* binnen een **Tekst met meerdere regels** field

### Delen van een inhoudsfragment maken {#constituent-parts-of-a-content-fragment}

De elementen van het inhoudsfragment bestaan uit de volgende onderdelen (direct of indirect):

* **Fragmentelementen**

   * Elementen correleren met de gegevensvelden die inhoud bevatten.
   * U gebruikt een [Inhoudsfragmentmodel](/help/sites-cloud/administering/content-fragments/content-fragment-models.md) om het inhoudsfragment te maken. De elementen (velden) die in het model zijn opgegeven, definiëren de structuur van het fragment. Deze elementen (velden) kunnen van verschillende gegevenstypen zijn.

* **Fragmentalinea&#39;s**

   * Tekstblokken, vaak meerdere regels, die zijn gescheiden als afzonderlijke entiteiten.

   * Inhoudsbeheer tijdens het ontwerpen van pagina&#39;s inschakelen.

* **Fragmentmetagegevens**

   * Gebruik de [Metagegevensschema&#39;s voor elementen](/help/assets/metadata-schemas.md).
   * Tags kunnen worden gemaakt wanneer u:

      * Het fragment maken en ontwerpen
      * of later, wanneer u [de eigenschappen weergeven of bewerken](/help/sites-cloud/administering/content-fragments/authoring.md#view-properties-tags) wanneer in de fragmenteditor

  >[!CAUTION]
  >
  >Metagegevensverwerkingsprofielen zijn niet van toepassing op inhoudsfragmenten.

  >[!CAUTION]
  >
  >Een inhoudsfragmentmodel kan vaak gegevensvelden definiëren met de naam **Titel** en **Beschrijving**. Als deze twee gebieden bestaan, zijn zij user-defined gebieden en kunnen op het inhoudsgebied van de redacteur worden bijgewerkt.
  >
  >Het inhoudsfragment en de variaties ervan hebben ook metagegevensvelden (eigenschapvelden), genaamd **Titel** en **Beschrijving**. Deze twee metagegevensvelden maken integraal deel uit van een inhoudsfragment en variatie. Deze velden worden in eerste instantie gedefinieerd wanneer het fragment wordt gemaakt. Deze eigenschappen kunnen worden bijgewerkt in het gebied met eigenschappen/metagegevens van de editor.

* **[Hoofd](#main-and-variations)**
* **[Variaties](#main-and-variations)**

### Vereist door fragmenten {#required-by-fragments}

Voor het maken van Content Fragments hebt u nodig:

* **Content Model**

   * zijn [toegelaten gebruikend Browser van de Configuratie](/help/sites-cloud/administering/content-fragments/setup.md).
   * zijn [gemaakt met Gereedschappen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md).
   * Vereist voor [een fragment maken](/help/sites-cloud/administering/content-fragments/managing.md#creating-content-fragments).
   * Definieert de structuur van een fragment (titel, inhoudselementen, tagdefinities).
   * Definities van inhoudsfragmentmodel vereisen een titel en één gegevenselement. Alle overige elementen zijn optioneel.
   * Het model kan de standaardinhoud definiëren, indien van toepassing.
   * Auteurs kunnen de gedefinieerde structuur niet wijzigen tijdens het ontwerpen van fragmentinhoud, maar ze kunnen de modeleditor wel openen vanuit de fragmenteditor.
   * Wijzigingen die worden aangebracht in een model nadat afhankelijke inhoudsfragmenten zijn gemaakt, kunnen van invloed zijn op die inhoudsfragmenten.

Als u de Content Fragments wilt gebruiken voor de levering van inhoud zonder kop, hebt u ook het volgende nodig:

* a [GraphQL-query](/help/headless/graphql-api/content-fragments.md) de vereiste inhoud aanvragen
* deze inhoud kan vervolgens worden gebruikt voor de ontwikkeling van uw eigen SPA voor AEM; bekijk de volgende documenten voor meer informatie:

   * [SPA WKND-zelfstudie](/help/implementing/developing/hybrid/wknd-tutorial.md)
   * [Aan de slag met Reageren](/help/implementing/developing/hybrid/getting-started-react.md)
   * [Aan de slag met Angular](/help/implementing/developing/hybrid/getting-started-angular.md)

Als u de Content Fragments wilt gebruiken voor het ontwerpen van pagina&#39;s, hebt u ook het volgende nodig:

* A **Component Inhoudsfragment**

   * Instrumentaal voor het leveren van het fragment in HTML- en/of JSON-indeling.
   * Vereist voor [verwijzen naar het fragment op een pagina](/help/sites-cloud/authoring/fragments/content-fragments.md).
   * Verantwoordelijk voor de lay-out en levering van een fragment, bijvoorbeeld kanalen.
   * Fragmenten hebben een of meer specifieke componenten nodig om de lay-out te definiëren en om enkele of alle elementen/variaties en bijbehorende inhoud te leveren.
   * Wanneer u een fragment naar een pagina sleept in de ontwerpfase, wordt de vereiste component automatisch gekoppeld.
   * Zie de [Component Content Fragment Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html).

## Voorbeeldengebruik {#example-usage}

Een fragment met de elementen en variaties kan worden gebruikt om coherente inhoud voor meerdere kanalen te maken. Bij het ontwerpen van het fragment moet u rekening houden met wat er wordt gebruikt en waar.

### WKND-voorbeeld {#wknd-sample}

De [Gedeelde WKND-site en WKND](/help/implementing/developing/introduction/develop-wknd-tutorial.md) voorbeelden worden gegeven om u te helpen meer te leren over AEM as a Cloud Service.

<!-- CHECK: which links can/should be used these days? -->

Het WKND-project omvat:

* Modellen voor inhoudsfragmenten zijn beschikbaar onder:

   * `.../libs/dam/cfm/models/console/content/models.html/conf/wknd`

   * `.../ui#/aem/libs/dam/cfm/models/console/content/models.html/conf/wknd-shared`

* Inhoudsfragmenten (en andere inhoud) beschikbaar onder:

   * `.../assets.html/content/dam/wknd/en`
