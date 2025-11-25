---
title: Variaties - Inhoud van fragment ontwerpen (Assets - Inhoudsfragmenten)
description: Begrijp hoe de variaties van het Fragment van de Inhoud u toestaan om inhoud voor het fragment te ontwerpen, dan variaties van die inhoud tot stand te brengen volgens doel, daarom verhogend de flexibiliteit.
exl-id: af05aae6-d535-4007-ba81-7f41213ff152
feature: Content Fragments
role: User
solution: Experience Manager Sites
source-git-commit: 8a8f63758cf216b502d5ee894ff5af7285777889
workflow-type: tm+mt
source-wordcount: '2571'
ht-degree: 4%

---

# Variaties - Fragmentinhoud ontwerpen{#variations-authoring-fragment-content}

[&#x200B; de Variaties &#x200B;](/help/assets/content-fragments/content-fragments.md#constituent-parts-of-a-content-fragment) zijn een significante eigenschap van de Fragmenten van de Inhoud in Adobe Experience Manager (AEM) as a Cloud Service. Dit is omdat zij u exemplaren van de **Hoofd** inhoud voor gebruik op specifieke kanalen en scenario&#39;s laten tot stand brengen en uitgeven. Dit maakt met name de levering van inhoud zonder kop nog flexibeler.

>[!NOTE]
>
>De Fragmenten van de inhoud zijn een eigenschap van Plaatsen, maar worden opgeslagen als **Assets**.
>
>Er zijn twee redacteurs voor het ontwerpen van de Fragmenten van de Inhoud - de nieuwe redacteur en de originele redacteur. De nieuwe redacteur is het gebrek. Hoewel de basisfunctionaliteit hetzelfde is, zijn er enkele verschillen.
>
>In deze sectie wordt de oorspronkelijke editor beschreven. Dit wordt [&#x200B; geopend via de nieuwe redacteur &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#opening-the-fragment-editor).
>
>Zie de documentatie van Plaatsen, [&#x200B; de Fragmenten van de Inhoud - Authoring &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md), voor volledige details van de nieuwe redacteur.

Van het **lusje van Variaties** kunt u het volgende doen:

* [&#x200B; ga de inhoud &#x200B;](#authoring-your-content) voor uw fragment in,
* [&#x200B; creeer en beheer variaties &#x200B;](#managing-variations) van de **Hoofd** inhoud,

Voer een reeks andere acties uit afhankelijk van het gegevenstype dat wordt bewerkt, bijvoorbeeld:

* [&#x200B; Tussenvoegsel visuele activa in uw fragment &#x200B;](#inserting-assets-into-your-fragment) (beelden)

* Selecteer tussen [&#x200B; Rijke Tekst &#x200B;](#rich-text), [&#x200B; Onbewerkte Tekst &#x200B;](#plain-text), en [&#x200B; Markdown &#x200B;](#markdown) voor het uitgeven

* [Inhoud uploaden](#uploading-content)

* [&#x200B; de belangrijkste statistieken van de Mening &#x200B;](#viewing-key-statistics) (over multi-lijntekst)

* [Tekst samenvatten](#summarizing-text)

* [Variaties synchroniseren met stramieninhoud](#synchronizing-with-master)

>[!CAUTION]
>
>Nadat een fragment is gepubliceerd en/of waarnaar wordt verwezen, geeft AEM een waarschuwing weer wanneer een auteur het fragment opent voor opnieuw bewerken. Hiermee wordt u gewaarschuwd dat wijzigingen in het fragment ook van invloed zijn op de pagina&#39;s waarnaar wordt verwezen.

## Inhoud ontwerpen {#authoring-your-content}

Wanneer u uw inhoudsfragment voor het uitgeven in de originele redacteur opent, is het **lusje van Variaties** open door gebrek. Hier kunt u de inhoud ontwerpen, voor stramien of variaties die u hebt. Het gestructureerde fragment bevat velden van diverse gegevenstypen die in het inhoudsmodel zijn gedefinieerd.

Bijvoorbeeld:

![&#x200B; volledige het schermredacteur &#x200B;](assets/cfm-variations-02.png)

U kunt:

* Maak direct aan uw inhoud in het **lusje van Variaties** uitgeeft; elk gegevenstype verstrekt verschillende het uitgeven opties, bijvoorbeeld:

   * wanneer gevormd (als veelvoud) in het model, staan diverse gegevenstypes u toe **&#x200B;**&#x200B;instanties van het relevante gebied toevoegen

   * voor **multi-line tekst** gebieden, kunt u [&#x200B; het volledig-schermredacteur &#x200B;](#full-screen-editor) ook openen:

      * selecteren het [&#x200B; Formaat &#x200B;](#formats)
      * zie meer het uitgeven opties (voor [&#x200B; Rich Text &#x200B;](#rich-text) formaat)
      * toegang tot een waaier van [&#x200B; acties &#x200B;](#actions)

   * Voor **gebieden van de Verwijzing van het 0&rbrace; Fragment &lbrace;, kan de** Edit optie van het Fragment van de Inhoud [, afhankelijk van de modeldefinitie beschikbaar zijn.](#fragment-references-edit-content-fragment)

* Wijs **Markeringen** aan de huidige variatie toe; de markeringen kunnen worden toegevoegd, worden bijgewerkt en, worden verwijderd.

   * [&#x200B; de Markeringen &#x200B;](/help/sites-cloud/authoring/sites-console/tags.md) zijn krachtig wanneer het organiseren van uw fragmenten aangezien zij voor inhoudsclassificatie en taxonomie kunnen worden gebruikt. Tags kunnen worden gebruikt voor het zoeken naar inhoud (door tags) en het toepassen van bulkbewerkingen.

      * Zoekt naar een tag en retourneert het fragment, waarbij de tagvariatie is gemarkeerd.
      * Variatietags kunnen ook worden gebruikt om variaties te groeperen voor een specifiek CDN-profiel (Content Delivery Network) (voor CDN-caching) in plaats van de variatienaam te gebruiken.

     U kunt bijvoorbeeld relevante fragmenten labelen als &#39;kerstlancering&#39; om alleen deze fragmenten als een subset te kunnen doorbladeren, of om ze te kopiëren voor gebruik met een andere toekomstige start in een nieuwe map.

  >[!NOTE]
  >
  >**de Markeringen** kunnen ook worden toegevoegd (aan de **Hoofd** variatie) als deel van [&#x200B; Meta-gegevens &#x200B;](/help/assets/content-fragments/content-fragments-metadata.md)

* [&#x200B; creeer en beheer variaties &#x200B;](#managing-variations) van de **Hoofd** inhoud.

>[!NOTE]
>
>Afhankelijk van definities in het onderliggende model, kunnen de gebieden aan bepaalde types van [&#x200B; Bevestiging &#x200B;](/help/assets/content-fragments/content-fragments-models.md#validation) onderworpen zijn.

### Volledige schermeditor {#full-screen-editor}

Wanneer u een tekstveld met meerdere regels bewerkt, kunt u de volledige schermeditor openen. Selecteer de gewenste tekst en selecteer vervolgens het volgende actiepictogram:

![&#x200B; volledig het pictogram van de het schermredacteur &#x200B;](assets/cfm-variations-03.png)

Hiermee opent u de teksteditor voor het volledige scherm:

![&#x200B; volledige het schermredacteur &#x200B;](assets/cfm-variations-fullscreentexteditor.png)

De teksteditor voor volledig scherm biedt de volgende mogelijkheden:

* Toegang tot diverse [&#x200B; acties &#x200B;](#actions)
* Afhankelijk van het [&#x200B; formaat &#x200B;](#formats), extra het formatteren opties ([&#x200B; Rijke Tekst &#x200B;](#rich-text))

### Handelingen {#actions}

De volgende acties zijn ook beschikbaar (voor alle [&#x200B; formaten &#x200B;](#formats)) wanneer de volledig-schermredacteur (namelijk multi-line tekst) open is:

* Selecteer het [&#x200B; formaat &#x200B;](#formats) ([&#x200B; Rijke Tekst &#x200B;](#rich-text), [&#x200B; Onbewerkte Tekst &#x200B;](#plain-text), [&#x200B; Markdown &#x200B;](#markdown))

* [Inhoud uploaden](#uploading-content)

* [Tekststatistieken tonen](#viewing-key-statistics)

* [&#x200B; synchroniseer met Hoofd &#x200B;](#synchronizing-with-master) (wanneer het uitgeven van een variatie)

* [Tekst samenvatten](#summarizing-text)

### Indelingen {#formats}

De opties voor het bewerken van tekst met meerdere regels zijn afhankelijk van de geselecteerde indeling:

* [RTF](#rich-text)
* [Onbewerkte tekst](#plain-text)
* [Markering](#markdown)

De indeling kan worden geselecteerd in de schermvullende editor.

### RTF {#rich-text}

Met RTF-bewerking kunt u opmaken:

* Vet
* Cursief
* Onderstrepen
* Uitlijning: links, midden, rechts
* Lijst met opsommingstekens
* Genummerde lijst
* Inspringing: verhogen, verlagen
* Hyperlinks maken/verbreken
* Tekst/tekst uit Word plakken
* Een tabel invoegen
* Alineastijl: Alinea, kop 1/2/3
* [Element invoegen](#inserting-assets-into-your-fragment)
* Open de volledige-schermredacteur, waar de volgende het formatteren opties beschikbaar zijn:
   * Zoeken
   * Zoeken/vervangen
   * Spellingcontrole
   * [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [&#x200B; het Fragment van de Inhoud van het Tussenvoegsel &#x200B;](#inserting-content-fragment-into-your-fragment); beschikbaar wanneer uw **multi-line tekst** gebied met **wordt gevormd staat de Verwijzing van het Fragment** toe.

De [&#x200B; acties &#x200B;](#actions) zijn ook toegankelijk van de het volledig-schermredacteur.

### Onbewerkte tekst {#plain-text}

Met platte tekst kunt u snel inhoud invoeren zonder opmaak- of markeringsgegevens. U kunt de het volledig-schermredacteur voor verdere [&#x200B; acties &#x200B;](#actions) ook openen.

>[!CAUTION]
>
>Als u **Onbewerkte Tekst** selecteert, zou u om het even welke het formatteren, of prijsdaling, of activa kunnen verliezen die u in één van beide **Rijke Tekst** of **Markting** opnam.

### Markering {#markdown}

>[!NOTE]
>
>Voor volledige informatie, zie de [&#x200B; documentatie van de Vermindering &#x200B;](/help/assets/content-fragments/content-fragments-markdown.md).

Hiermee kunt u de tekst opmaken met behulp van een markering. U kunt het volgende definiëren:

* Koppen
* Alinea&#39;s en regeleinden
* Koppelingen
* Afbeeldingen
* Aanhalingstekens blokkeren
* Lijsten
* Nadruk
* Codeblokken
* backslash-eces

U kunt de het volledig-schermredacteur voor verdere [&#x200B; acties &#x200B;](#actions) ook openen.

>[!CAUTION]
>
>Als u tussen **Tekst met opmaak** en **Markdown** schakelt, kunt u onverwachte effecten met Blokcitaten en Codeblokken ervaren, aangezien deze twee opmaakindelingen verschillen in hoe zij worden behandeld.

### Fragmentverwijzingen {#fragment-references}

Als het Content Fragment-model fragmentverwijzingen bevat, hebben de auteurs van het fragment mogelijk aanvullende opties:

* [Inhoudsfragment bewerken](#fragment-references-edit-content-fragment)
* [Nieuw inhoudsfragment](#fragment-references-new-content-fragment)

![&#x200B; Verwijzingen van het Fragment &#x200B;](assets/cfm-variations-12.png)

#### Inhoudsfragment bewerken {#fragment-references-edit-content-fragment}

De optie **geeft het Fragment van de Inhoud uit** opent dat fragment in een nieuw redacteurslusje (binnen zelfde browser tabel).

Het selecteren van het originele lusje opnieuw (bijvoorbeeld, **Kleine Pony Inc.**) sluit dit secundaire lusje (in dit geval, **Adam Smith**).

![&#x200B; Verwijzingen van het Fragment &#x200B;](assets/cfm-variations-editreference.png)

#### Nieuw inhoudsfragment {#fragment-references-new-content-fragment}

De optie **Nieuwe Fragment van de Inhoud** laat u een fragment tot stand brengen. Hiervoor wordt een variant van de wizard voor het maken van inhoudsfragmenten geopend in de editor.

**om een inhoudsfragment tot stand te brengen:**

1. Navigeer naar en selecteer de gewenste map.
1. Het selecteren van **daarna**.
1. Het specificeren van eigenschappen; bijvoorbeeld, **Titel**.
1. Selecterend **creeer**.
1. Tot slot:
   1. **Gedaan**:
      * retourneert (naar het oorspronkelijke fragment)
      * verwijst naar het nieuwe fragment
   1. **Open**:
      * verwijst naar het nieuwe fragment
      * Hiermee opent u het nieuwe fragment om het te bewerken in een nieuw browsertabblad

### Belangrijkste statistieken weergeven {#viewing-key-statistics}

Wanneer de volledig-schermredacteur open is, toont de actie **Statistieken van de Tekst** een waaier van informatie over de tekst.

Bijvoorbeeld:

![&#x200B; statistieken &#x200B;](assets/cfm-variations-04.png)

### Inhoud uploaden {#uploading-content}

U kunt het maken van inhoudsfragmenten vereenvoudigen door tekst te uploaden die is voorbereid in een externe editor en deze rechtstreeks toe te voegen aan het fragment.

### Tekst samenvatten {#summarizing-text}

Samenvattende tekst is ontworpen om gebruikers te helpen de lengte van hun tekst te beperken tot een vooraf gedefinieerd aantal woorden, terwijl de hoofdpunten en de algemene betekenis behouden blijven.

>[!NOTE]
>
>Op een meer technisch niveau, houdt het systeem de zinnen die het als het verstrekken van de *beste verhouding van informatiedichtheid en uniciteit* volgens specifieke algoritmen berekent.

>[!CAUTION]
>
>Het inhoudsfragment moet een geldige taalmap (ISO-code) hebben als voorouder. Hiermee wordt bepaald welk taalmodel moet worden gebruikt.
>
>Bijvoorbeeld `en/` zoals in het volgende pad:
>
>  `/content/dam/my-brand/en/path-down/my-content-fragment`

>[!CAUTION]
>
>Engels is beschikbaar buiten de box.
>
>Andere talen zijn beschikbaar als Pakketten van het Model van de Taal van Software Distributie:
>
>* [&#x200B; Frans (fr) &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-fr)
>* [&#x200B; Duits (de) &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-de)
>* [&#x200B; Italiaans (het) &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-it)
>* [&#x200B; Spaans (es) &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq630/product/smartcontent-model-es)
>

1. Selecteer **Meester** of de vereiste variatie.
1. Open de editor voor het volledige scherm.

1. Selecteer **vatten tekst** van de toolbar samen.

   ![&#x200B; samenvatting &#x200B;](assets/cfm-variations-05.png)

1. Specificeer het doelaantal woorden en selecteer **Begin**:
1. De oorspronkelijke tekst wordt naast de voorgestelde samenvatting weergegeven:

   * Alle zinnen die moeten worden verwijderd, worden rood gemarkeerd met doorhaling.
   * Klik op een gemarkeerde zin, zodat u deze in de samengevatte inhoud kunt houden.
   * Klik op een niet-gemarkeerde zin, zodat deze kan worden verwijderd.

1. Selecteer **vat** samen om de veranderingen te bevestigen.

1. De oorspronkelijke tekst wordt naast de voorgestelde samenvatting weergegeven:

   * Alle zinnen die moeten worden verwijderd, worden rood gemarkeerd met doorhaling.
   * Klik op een gemarkeerde zin, zodat u deze in de samengevatte inhoud kunt houden.
   * Klik op een niet-gemarkeerde zin, zodat deze kan worden verwijderd.
   * De samenvattingsstatistieken worden getoond: **Ware** en **Doel** -
   * U kunt **Voorproef** de veranderingen.

   ![&#x200B; samenvattingsvergelijking &#x200B;](assets/cfm-variations-06.png)

### Een inhoudsfragment annoteren {#annotating-a-content-fragment}

Een fragment annoteren:

1. Selecteer **Meester** of de vereiste variatie.

1. Open de editor voor het volledige scherm.

1. Het **annoteert** pictogram is beschikbaar in de hoogste toolbar. U kunt desgewenst tekst selecteren.

   ![&#x200B; annoteren &#x200B;](assets/cfm-variations-07.png)

1. Er wordt een dialoogvenster geopend. Hier kunt u uw annotatie invoeren.

   ![&#x200B; annoteren &#x200B;](assets/cfm-variations-07a.png)

1. Selecteer **toepassen** op de dialoog.

   ![&#x200B; annoteren &#x200B;](assets/cfm-variations-annotations-apply-icon.png)

   Als de annotatie is toegepast op de geselecteerde tekst, blijft die tekst gemarkeerd.

   ![&#x200B; annoteren &#x200B;](assets/cfm-variations-07b.png)

1. Sluit de volledige-schermredacteur, de annotaties worden nog benadrukt. Als deze optie is geselecteerd, wordt een dialoogvenster geopend waarin u de annotatie verder kunt bewerken.

1. Selecteer **sparen**.

1. Sluit de volledige-schermredacteur, de annotaties worden nog benadrukt. Als deze optie is geselecteerd, wordt een dialoogvenster geopend waarin u de annotatie verder kunt bewerken.

   ![&#x200B; annoteren &#x200B;](assets/cfm-variations-07c.png)

>[!NOTE]
>
>De eigenschap van Annotaties toont geen commentaren ingegaan in de nieuwe [&#x200B; redacteur van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md#commenting-on-your-fragment).

### Annotaties weergeven, bewerken, verwijderen {#viewing-editing-deleting-annotations}

Annotaties:

* Deze worden aangegeven door de markering in de tekst, zowel in de modus Volledig scherm als in de normale modus van de editor. Alle details van een annotatie kunnen vervolgens worden weergegeven, bewerkt en/of verwijderd door op de gemarkeerde tekst te klikken, waarna het dialoogvenster opnieuw wordt geopend.

  >[!NOTE]
  >
  >Er is een keuzekiezer beschikbaar als er meerdere annotaties zijn toegepast op één stuk tekst.

* Wanneer u de volledige tekst verwijdert waarop de annotatie is toegepast, wordt de annotatie ook verwijderd.

* Het kan worden vermeld, en worden geschrapt, door het **lusje van Annotaties** in de fragmentredacteur te selecteren.

  ![annotaties](assets/cfm-variations-08.png)

* Het kan, in de [&#x200B; Chronologie &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) voor het geselecteerde fragment worden bekeken en worden geschrapt.

### Assets invoegen in uw fragment {#inserting-assets-into-your-fragment}

Om het proces te verlichten om inhoudsfragmenten te ontwerpen, kunt u [&#x200B; Assets &#x200B;](/help/assets/manage-digital-assets.md) (beelden) direct aan het fragment toevoegen.

Zij worden toegevoegd aan de paragraafopeenvolging van het fragment zonder enige het formatteren; het formatteren kan worden gedaan wanneer het [&#x200B; fragment wordt gebruikt/op een pagina &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) van verwijzingen wordt voorzien.

>[!CAUTION]
>
>Deze elementen kunnen niet worden verplaatst of verwijderd op een pagina waarnaar wordt verwezen. Dit moet gebeuren in de fragmenteditor.
>
>Nochtans, moet het formatteren van de activa (bijvoorbeeld, grootte) in de [&#x200B; paginaredacteur &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) worden gedaan. De representatie van het element in de fragmenteditor is uitsluitend bedoeld voor het ontwerpen van de inhoudsstroom.

>[!NOTE]
>
>Er zijn diverse methodes om [&#x200B; beelden &#x200B;](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

1. Plaats de cursor op de positie waar u de afbeelding wilt toevoegen.
1. Gebruik het pictogram **Asset invoegen** om het zoekdialoogvenster te openen.

   ![&#x200B; pictogram van het tussenvoegselmiddel &#x200B;](assets/cfm-variations-09.png)

1. In het dialoogvenster kunt u naar het vereiste element navigeren in DAM of het element zoeken in DAM.

   Selecteer het gewenste element door op de miniatuur te klikken.

1. Gebruik **Selecteren** om de asset op de huidige locatie toe te voegen aan het alineasysteem van het contentfragment.

   >[!CAUTION]
   >
   >Nadat u een element hebt toegevoegd, als u de indeling wijzigt in:
   >
   >* **Onbewerkte Tekst**: de activa worden verloren van het fragment.
   >* **Markering**: het element is niet zichtbaar, maar is nog daar wanneer u aan **Rijke Tekst** terugkeert.

### Een inhoudsfragment invoegen in uw fragment {#inserting-content-fragment-into-your-fragment}

U kunt het maken van inhoudsfragmenten vereenvoudigen door ook een ander inhoudsfragment aan het fragment toe te voegen.

Ze worden als een referentie toegevoegd op de huidige locatie in het fragment.

>[!NOTE]
>
>Deze optie is beschikbaar wanneer uw **multi-line tekst** met **wordt gevormd toestaat de Verwijzing van het Fragment**.

>[!CAUTION]
>
>Deze elementen kunnen niet worden verplaatst of verwijderd op een pagina waarnaar wordt verwezen. Dit moet gebeuren in de fragmenteditor.
>
>Nochtans, moet het formatteren van de activa (bijvoorbeeld, grootte) in de [&#x200B; paginaredacteur &#x200B;](/help/sites-cloud/authoring/fragments/content-fragments.md) worden gedaan. De representatie van het element in de fragmenteditor is uitsluitend bedoeld voor het ontwerpen van de inhoudsstroom.

>[!NOTE]
>
>Er zijn diverse methodes om [&#x200B; beelden &#x200B;](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

1. Plaats de cursor op de positie waar u het fragment wilt toevoegen.
1. Gebruik het **pictogram van het Fragment van de Inhoud van het Tussenvoegsel** om de onderzoeksdialoog te openen.

   ![&#x200B; pictogram van het Fragment van de Tussenvoegsel Inhoud &#x200B;](assets/cfm-variations-13.png)

1. In het dialoogvenster kunt u naar het gewenste fragment in de Assets-map navigeren of naar het fragment zoeken.

   Selecteer het gewenste fragment door op de miniatuur te klikken.

1. Gebruik **Uitgezochte** om een verwijzing naar het geselecteerde Fragment van de Inhoud aan uw huidig inhoudsfragment (bij de huidige plaats) toe te voegen.

   >[!CAUTION]
   >
   >Nadat u een verwijzing naar een ander fragment hebt toegevoegd, wijzigt u de indeling in:
   >
   >* **Onbewerkte Tekst**: de verwijzing wordt verloren van het fragment.
   >* **Markering**: de verwijzing blijft.

## Overerving {#inheritance}

Overerving is het mechanisme waarbij inhoud automatisch van het ene naar het andere fragment kan worden verplaatst. De overerfde gebieden, en de variaties, kunnen het product van [&#x200B; Beheer van meerdere plaatsen &#x200B;](/help/assets/content-fragments/content-fragments-msm.md) zijn.

U kunt de overerving annuleren (en vervolgens opnieuw inschakelen). Afhankelijk van de context, kan dit voor een variatie, of een individueel gebied, beschikbaar zijn als het fragment deel van een levende kopie uitmaakt.

![&#x200B; een Fragment van de Inhoud die overervingsverhouding toont &#x200B;](/help/assets/content-fragments/assets/cfm-variations-inheritance.png)

Bijvoorbeeld:

* Overerving annuleren

  ![&#x200B; annuleert Overerving knoop &#x200B;](/help/assets/content-fragments/assets/editing-cancel-inheritance.png)

* Overerving opnieuw inschakelen (als overerving al is geannuleerd)

  ![&#x200B; re-Enable de knoop van de Overerving &#x200B;](/help/assets/content-fragments/assets/editing-reenable-inheritance.png)

<!--
* Rollout action is also available in Live Copy source

  ![Rollout button](/help/assets/content-fragments/assets/editing-rollout.png)
-->

## Variaties beheren {#managing-variations}

### Een variatie maken {#creating-a-variation}

De variaties laten u de **Hoofd** inhoud nemen en het variëren volgens doel (indien nodig).

**om een variatie tot stand te brengen:**

>[!NOTE]
>
>Variaties voegen verwerkingstijd toe aan een inhoudsfragment, aan de auteursomgeving en ook bij levering. Aanbevolen wordt het aantal variaties tot een beheerbaar minimum te beperken.
>
>De beste manier is om tien variaties per inhoudsfragment niet te overschrijden.

1. Open het fragment en controleer of het zijpaneel zichtbaar is.
1. Selecteer **Variaties** van de pictogrambar in het zijpaneel.
1. Selecteer **creeer Variatie**.
1. Een dialoogdoos opent zodat kunt u de **Titel** en **Beschrijving** voor de nieuwe variatie specificeren.
1. Selecteer **toevoegen**; het fragment **Hoofd** wordt gekopieerd aan de nieuwe variatie, die nu open voor [&#x200B; het uitgeven &#x200B;](#editing-a-variation) is.

   >[!NOTE]
   >
   >Wanneer het creëren van een variatie is het altijd de **Meester** die wordt gekopieerd, niet de variatie die open is.

   >[!NOTE]
   >
   >Wanneer u een variatie creeert, worden alle **Markeringen** momenteel toegewezen aan de **Hoofd** variatie gekopieerd aan uw nieuwe variatie.

### Een variatie bewerken {#editing-a-variation}

U kunt de variatie-inhoud wijzigen na:

* [&#x200B; Creërend uw variatie &#x200B;](#creating-a-variation).
* Een bestaand fragment openen en vervolgens de gewenste variant in het zijpaneel selecteren.

![&#x200B; het uitgeven van een variatie &#x200B;](assets/cfm-variations-10.png)

### De naam van een variatie wijzigen {#renaming-a-variation}

1. Open uw fragment en selecteer **Variaties** van het zijpaneel.
1. Selecteer de gewenste variatie.
1. Selecteer **anders noemen** van **&#x200B;**&#x200B;drop-down Acties.

1. Voer in het dialoogvenster dat verschijnt de nieuwe **titel** en/of **beschrijving** in.

1. Bevestig **anders noemen** actie.

>[!NOTE]
>
>Dit beïnvloedt slechts de variatie **Titel**.

### Een variatie verwijderen {#deleting-a-variation}

1. Open uw fragment en selecteer **Variaties** van het zijpaneel.
1. Selecteer de gewenste variatie.
1. Selecteer **Schrapping** van de **drop-down Acties**.

1. Bevestig de **schrapping** actie in de dialoog.

>[!NOTE]
>
>U kunt niet **Hoofd** schrappen.

### Synchroniseren met stramien {#synchronizing-with-master}

**Hoofd** is een deel van een inhoudsfragment en, door definitie, dat het het hoofdexemplaar van de inhoud houdt. Terwijl de variaties de individuele bijgewerkte en op maat gemaakte versies van die inhoud houden. Wanneer de Master wordt bijgewerkt, is het mogelijk dat deze wijzigingen ook relevant zijn voor de wijzigingen en daarom aan hen moeten worden doorgegeven.

Wanneer u een variatie bewerkt, hebt u toegang tot de handeling voor het synchroniseren van het huidige element van de variatie met stramien. Hiermee kunt u automatisch wijzigingen kopiëren die u hebt aangebracht in Stramien naar de gewenste variatie.

>[!CAUTION]
>
>De synchronisatie is alleen beschikbaar om wijzigingen *van **Master**&#x200B;naar de variatie* te kopiëren.
>
>Alleen het huidige element van de variatie wordt gesynchroniseerd.
>
>De synchronisatie werkt slechts op de **multi-lijn tekst** gegeven-type.
>
>Het overbrengen van wijzigingen *van een variatie naar **master*** is niet beschikbaar als optie.

1. Open het inhoudsfragment in de fragmenteditor. Zorg ervoor dat het **Hoofd** is uitgegeven.

1. Selecteer een specifieke variant en kies vervolgens de gewenste synchronisatiehandeling uit:

   * de **drop-down selecteur van de Acties** **synchroniseer huidig element met meester**

     ![&#x200B; synchroniserend met meester &#x200B;](assets/cfm-variations-11a.png)

   * de toolbar van de het volledig-schermredacteur - **Synchronisatie met meester**

     ![&#x200B; synchroniserend met meester &#x200B;](assets/cfm-variations-11b.png)

1. Stramien en variaties worden naast elkaar weergegeven:

   * groen geeft aan dat inhoud is toegevoegd (aan de variatie)
   * rood geeft aan dat inhoud is verwijderd (uit de variatie)
   * blauw geeft vervangen tekst aan

   ![&#x200B; synchroniserend met meester &#x200B;](assets/cfm-variations-11c.png)

1. Selecteer **Synchroniseer**, wordt de variatie bijgewerkt en getoond.
