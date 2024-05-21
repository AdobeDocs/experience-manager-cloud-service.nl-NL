---
title: Inhoudsfragmenten ontwerpen
description: Begrijp hoe u inhoud voor uw inhoudsfragmenten ontwerpt en maak variaties van die inhoud afhankelijk van het doel. Dit biedt extra flexibiliteit voor zowel levering zonder kop als het ontwerpen van pagina's.
feature: Content Fragments
role: User, Developer, Architect
exl-id: a2f2b617-3bdf-4a22-ab64-95f2c65adc82
source-git-commit: fc97a51bb20bbf0d438d0f27a2246467a480eb71
workflow-type: tm+mt
source-wordcount: '2669'
ht-degree: 0%

---

# Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Het ontwerpen van inhoudsfragmenten is zowel gericht op de levering zonder kop als op het ontwerpen van pagina&#39;s.

Er zijn twee editors beschikbaar voor inhoudsfragmenten. De editor die in deze sectie wordt beschreven:

* is ontwikkeld voor inhoud zonder kop (hoewel het voor alle scenario&#39;s kan worden gebruikt)
* is beschikbaar via **Inhoudsfragmenten** console

Deze editor biedt:

* [Automatisch opslaan](#saving-autosaving)om te voorkomen dat bewerkingen per ongeluk verloren gaan.
* [In line uploaden van elementen als inhoudsverwijzingen](#reference-images), zonder ze eerst naar Asset DAM te moeten uploaden.
* [Variaties genereren](#generate-variations-ai) gebruiken om het maken van inhoud te versnellen op basis van aanwijzingen.
* [Voorvertoning](#preview-content-fragment) van de gerenderde ervaring die door het inhoudsfragment wordt geleverd.
* Vermogen [Publiceren](#publish-content-fragment) en [Publiceren ongedaan maken](#unpublish-content-fragment) uit de editor.
* Vermogen [gekoppelde taalkopieën bekijken en openen](#view-language-copies) in de editor.
* Vermogen [versiedetails weergeven](#view-version-history) in de editor. U kunt ook terugkeren naar een geselecteerde versie.
* Vermogen [bovenliggende verwijzingen weergeven en openen](#view-parent-references).
* Een hiërarchische weergave van het inhoudsfragment en de bijbehorende verwijzingen met de opdracht [Structuurelboom](#structure-tree).

>[!WARNING]
>
>De editor die in deze sectie wordt beschreven, is *alleen* beschikbaar in het *online* Adobe Experience Manager (AEM) as a Cloud Service.

## Inhoudsfragmenteditor {#content-fragment-editor}

Wanneer u de Inhoudsfragmenteditor voor het eerst opent, ziet u vier hoofdgebieden:

* bovenste werkbalk: voor belangrijke informatie en handelingen
   * een koppeling naar de Content Fragment Console (pictogram Start)
   * informatie over het model en de map
   * koppelingen naar [Voorvertoning (als het standaard URL-voorvertoningspatroon is geconfigureerd voor het model)](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-fragment-model-properties)
   * [Publiceren](#publish-content-fragment), en [Publiceren ongedaan maken](#unpublish-content-fragment) handelingen
   * een optie om alles weer te geven **Bovenliggende verwijzingen** (koppelingspictogram)
   * het fragment **[Status](/help/sites-cloud/administering/content-fragments/managing.md#statuses-content-fragments)** en laatst opgeslagen gegevens
   * een schakeloptie voor het overschakelen naar de oorspronkelijke (op elementen gebaseerde) editor

     >[!WARNING]
     >
     >De oorspronkelijke editor wordt op hetzelfde tabblad geopend. Het wordt afgeraden beide editors tegelijk te openen.

* linkerdeelvenster: toont de **[Variaties](#variations)** voor het inhoudsfragment en de bijbehorende **Velden**:
   * deze koppelingen kunnen worden gebruikt om [navigeren door de structuur van het inhoudsfragment](#navigate-structure)
* rechterdeelvenster: tabbladen voor presentaties [eigenschappen (metagegevens) en tags weergeven](#view-properties-tags), informatie over de [versiehistorie](#view-version-history)en informatie over [taalkopieën](#view-language-copies)
   * in de **Eigenschappen** kunt u de **Titel** en **Beschrijving** voor het fragment, of **Variatie**
* centraal deelvenster: geeft de daadwerkelijke velden en inhoud van de geselecteerde variatie weer
   * kunt u de inhoud bewerken
   * indien **Tijdelijke aanduiding voor tab** de velden worden gedefinieerd binnen het model dat ze hier worden weergegeven en kunnen worden gebruikt voor navigatie; ze worden horizontaal weergegeven of als een vervolgkeuzelijst.

  >[!NOTE]
  >
  >Afhankelijk van definities in het onderliggende model kunnen velden worden onderworpen aan bepaalde typen [Validatie](/help/assets/content-fragments/content-fragments-models.md#validation).

![Inhoudsfragmenteditor - Overzicht](assets/cf-authoring-overview.png)

## Navigeren door de structuur van het inhoudsfragment {#navigate-structure}

één inhoudsfragment;

* Bestaat uit twee niveaus:

   * **[Variaties](#variations)** van het inhoudsfragment
   * **Velden** - gedefinieerd door het inhoudsfragmentmodel en gebruikt door elke variatie

* Kan verschillende verwijzingen bevatten.

### Variaties en velden {#variations-and-fields}

In het linkerpaneel kunt u zien:

* de lijst van **[Variaties](#variations)** die voor dit fragment zijn gemaakt:
   * **Hoofd** De variatie die aanwezig is wanneer het inhoudsfragment voor het eerst wordt gemaakt, kunt u later andere varianten toevoegen
   * u kunt gebruiken produceert Variaties (#generate-Variaties) om een snel gebaseerde malplaatje te gebruiken dat de Adobe voor een specifiek gebruiksgeval heeft gecreeerd.
   * u kunt [een variatie maken](#create-variation)
* de **Velden** in het fragment en de variaties ervan:
   * het pictogram geeft de [Gegevenstype](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)
   * de tekst is de veldnaam
   * deze vormen samen een directe koppeling naar de inhoud van het veld in het centrale venster (voor de huidige variatie)

### Koppelingen volgen {#follow-links}

In verschillende delen van de editor ziet u het koppelingspictogram. Hiermee kunt u het weergegeven item openen, bijvoorbeeld een Content Fragment Model, een Parent Reference of een fragment waarnaar wordt verwezen:

![Inhoudsfragmenteditor - Koppelingspictogram](assets/cf-authoring-link-icon.png)

### Structuurelboom {#structure-tree}

Open de **Structuurelboom** van de redacteurstoolbar om de hiërarchische structuur van het Inhoudsfragment, en zijn verwijzingen te tonen. Gebruik de koppelingspictogrammen om naar de referenties te navigeren.

![Inhoudsfragmenteditor - Structuurelijn](assets/cf-authoring-structure-tree.png)

>[!NOTE]
>
>Zie [Structuur van inhoudsfragment analyseren - boomstructuur](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree) voor meer informatie .

## Opslaan en automatisch opslaan {#saving-autosaving}

<!-- CHECK: cannot be saved, no undo, redo -->

Bij elke update die u maakt, wordt het inhoudsfragment automatisch opgeslagen. De laatst opgeslagen tijd wordt weergegeven in de bovenste werkbalk.

## Variaties {#variations}

[Variaties](/help/sites-cloud/administering/content-fragments/overview.md#main-and-variations) zijn een belangrijk kenmerk van AEM inhoudsfragmenten. Hiermee kunt u kopieën van de **Hoofd** inhoud voor gebruik op specifieke kanalen, en scenario&#39;s, die tot hoofdloze levering van inhoud en pagina creatie nog flexibeler maken.

Vanuit de editor kunt u:

* [Variaties maken](#create-variation) van de **Hoofd** content

* [AI variaties genereren gebruiken](#generate-variations-ai) om Generative AI te gebruiken om een snel gebaseerde sjabloon te gebruiken die Adobe voor een specifiek gebruiksgeval heeft gemaakt.

* Selecteer de gewenste variatie voor het bewerken van de inhoud

* [Naam van variatie wijzigen](#rename-variation)

* [Een variatie verwijderen](#delete-variation)

### Een variatie maken {#create-variation}

Een variatie van het inhoudsfragment maken:

1. Selecteer in het linkerdeelvenster de optie **plusteken** (**Variatie maken**, dat recht heeft op **Variaties**.

   >[!NOTE]
   >
   >Nadat u de eerste variatie hebt gemaakt, worden bestaande variaties in hetzelfde deelvenster weergegeven.

   ![Inhoudsfragmenteditor - Uw eerste variatie maken](assets/cf-authoring-create-variation-01.png)

1. Voer een **Titel** voor uw variatie, en **Beschrijving** indien gewenst:

   ![Inhoudsfragmenteditor - Dialoogvenster Variatie maken](assets/cf-authoring-create-variation-02.png)

1. **Maken** de wijziging. De naam wordt weergegeven in de lijst.

### De naam van een variatie wijzigen {#rename-variation}

De naam van een **Variatie**:

1. Selecteer de gewenste variatie.

1. Open de **Eigenschappen** in het rechterdeelvenster.

1. De wijziging bijwerken **Titel**.

1. Druk op **Retourneren** of naar een ander veld gaan om de wijziging automatisch op te slaan. De titel wordt bijgewerkt in het gedeelte **Variaties** aan de linkerkant.

### Variaties maken met GenAI met Variaties genereren {#generate-variations-ai}

Gebruik Generatieve variaties om generatieve AI te gebruiken om het maken van inhoud te versnellen.

De generatieve variaties gebruiken in de Inhoudsfragmenteditor:

1. Open de Inhoudsfragmenteditor. In de kopbal zult u het ingangspunt vinden om Variaties te produceren:

   ![Variaties genereren in de Inhoudsfragmenteditor](assets/cfm-generate-variations1.png)

1. Variaties genereren wordt geopend op een nieuw tabblad. In de linkertrack ziet u de AEM Cloud-instantie en het inhoudsfragment waarvoor u inhoud maakt. Selecteer de vraag u wilt gebruiken of een nieuwe herinnering creëren.

   >[!NOTE]
   >
   >De beschikbare sjablonen voor herinneringen voor Adoben zijn nu beperkt, maar in toekomstige versies wordt meer toegevoegd.

   ![Exporteren om variaties in inhoudsfragment te genereren](assets/cfm-generate-variations2.png)

1. Genereer inhoud door de vragen in te vullen. Het inhoudsmodel van het fragment wordt automatisch gebruikt om inhoud te genereren met GenAI.

   >[!NOTE]
   >
   >Momenteel ondersteunen we alleen tekstvelden.

   ![Exporteren om variaties in inhoudsfragment te genereren](assets/cfm-generate-variations3.png)

1. Selecteer de variant die u wilt genereren en selecteer &quot;variatie exporteren&quot;. Bevestig de naam van de variatie van het inhoudsfragment en selecteer een van de volgende opties:

   * **Exporteren**: exporteer variatie naar Inhoudsfragment en blijf in de toepassing Variatie genereren.
   * **Exporteren en openen**: exporteer de variatie naar Inhoudsfragment en open een nieuw tabblad waarop het Inhoudsfragment wordt weergegeven met de nieuwe variatie van GenAI.

     ![Exporteren om variaties in inhoudsfragment te genereren](assets/cfm-generate-variations4.png)

1. Gegenereerde variaties worden weergegeven in de hoofdeditor voor contentfragmenten.

   ![Variaties in inhoudsfragment genereren weergeven](assets/cfm-generate-variations5.png)

Meer informatie over Variaties genereren [hier](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/generative-ai/generate-variations).

### Een wijziging verwijderen {#delete-variation}

Een variatie van het inhoudsfragment verwijderen:

    >[!OPMERKING]
    >
    >U kunt **Main** niet verwijderen.

1. Selecteer de variatie.

1. In de **Variatie** selecteert u het verwijderingspictogram (prullenbak):

   ![Inhoudsfragmenteditor - Variatiepictogram verwijderen](assets/cf-authoring-delete-variation.png)

1. Er wordt een dialoogvenster geopend. Selecteren **Verwijderen** om de actie te bevestigen.

## Tekstvelden met meerdere regels bewerken - Onbewerkte tekst of Markering {#edit-multi-line-text-fields-plaintext-markdown}

**[Tekst met meerdere regels](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** velden kunnen een van de volgende drie indelingen hebben:

* Onbewerkte tekst
* [Markering](/help/sites-cloud/administering/content-fragments/markdown.md)
* [RTF](#edit-multi-line-text-fields-rich-text)

Velden die zijn gedefinieerd als Onbewerkte tekst of Markeringen, hebben een eenvoudig tekstvak, zonder opmaakopties (op het scherm):

![Content Fragment Editor - Multi-line tekst - volledig scherm](assets/cf-authoring-multilinetext-plaintext-markdown.png)

## Tekstvelden met meerdere regels bewerken - RTF {#edit-multi-line-text-fields-rich-text}

Voor **[Tekst met meerdere regels](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** velden die zijn gedefinieerd als **RTF** Er zijn verschillende functies beschikbaar:

* Bewerk de inhoud:
   * Ongedaan maken/Opnieuw
   * Plakken/Plakken als tekst
   * Kopiëren
   * Alinea-indeling selecteren
   * Tabel maken/beheren
   * Tekst opmaken; vet, cursief, onderstrepen, kleur
   * Alinea-uitlijning instellen
   * Lijsten maken/beheren; genummerd met opsommingstekens
   * Tekst inspringen; verkleinen, vergroten
   * Huidige opmaak wissen
   * Koppelingen invoegen
   * Verwijzingen naar afbeeldingselementen selecteren en invoegen
   * Speciale tekens toevoegen
* [Editor op volledig scherm](#full-screen-editor-rich-text) - schakelen tussen volledig scherm en in-flow
* [Statistieken](#statistics-rich-text)
* [Vergelijken en synchroniseren](#compare-and-synchronize-rich-text)

Bijvoorbeeld:

![Content Fragment Editor - Multi-line text - full screen toggle](assets/cf-authoring-multilinetext-fullscreen-toggle.png)

>[!NOTE]
>
>Tekstvelden met meerdere regels worden ook aangegeven door de juiste [pictogram](#fields-datatypes-icons) in de **Velden** deelvenster.

### Volledige schermeditor - RTF-tekst {#full-screen-editor-rich-text}

De volledige-schermredacteur biedt de zelfde het uitgeven opties aan zoals wanneer in-stroom - maar biedt meer ruimte voor de tekst aan.

Bijvoorbeeld:

![Content Fragment Editor - Multi-line tekst - volledig scherm](assets/cf-authoring-multilinetext-fullscreen.png)

### Statistieken - RTF {#statistics-rich-text}

De handeling **Statistieken** Hiermee geeft u een gegevensbereik over de tekst weer in een veld met meerdere regels.

Bijvoorbeeld:

![Content Fragment Editor - Statistieken](assets/cf-authoring-multilinetext-statistics.png)

### Vergelijken en synchroniseren - RTF-tekst {#compare-and-synchronize-rich-text}

De handeling **Ververgelijken** is beschikbaar voor velden met meerdere regels als u een **Variatie** openen.

Hiermee opent u het veld Meerdere regels op volledig scherm en:

* geeft de inhoud voor beide weer **Hoofd** en de huidige **Variatie** tegelijkertijd, met vermelding van eventuele verschillen

* verschillen worden aangegeven door kleur:

   * groen geeft de toegevoegde inhoud aan (aan de variatie)
   * rood geeft aan dat inhoud is verwijderd (uit de variatie)
   * blauw geeft vervangen tekst aan

* verstrekt **Sync** handeling die de inhoud synchroniseert vanuit **Hoofd** op de huidige wijziging

   * indien **Hoofd** is bijgewerkt, worden deze wijzigingen overgedragen naar de wijziging
   * als de wijziging is bijgewerkt, worden deze wijzigingen overschreven door de inhoud van **Hoofd**

  >[!CAUTION]
  >
  >Synchronisatie is alleen beschikbaar voor het kopiëren van wijzigingen *van **Hoofd**de wijziging*.
  >
  >Wijzigingen overbrengen *van een wijziging naar **Hoofd*** is niet beschikbaar als optie.

Bijvoorbeeld, een scenario waar de variatie inhoud volledig was herschreven, zodat zal een synchronisatie die nieuwe inhoud met de inhoud van vervangen **Hoofd**:

![Content Fragment Editor - Vergelijken en synchroniseren](assets/cf-authoring-multilinetext-compare.png)

## Referenties beheren {#manage-references}

### Fragmentverwijzingen {#fragment-references}

[Fragmentverwijzingen](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments) kan worden gebruikt om:

* [een verwijzing naar een bestaand inhoudsfragment maken](#create-reference-existing-content-fragment)
* [een inhoudsfragment maken en ernaar verwijzen](#create-reference-content-fragment)

#### Een verwijzing naar een bestaand inhoudsfragment maken {#create-reference-existing-content-fragment}

Een verwijzing naar een bestaand inhoudsfragment maken:

1. Selecteer het veld.
1. Selecteren **Bestaande fragment toevoegen**.
1. Selecteer het gewenste fragment in de fragmentkiezer.

   >[!NOTE]
   >
   >U mag slechts één fragment tegelijk selecteren.

#### Een inhoudsfragment en verwijzing maken {#create-reference-content-fragment}

U kunt ook [selecteren **Nieuw fragment maken** om de **Maken** dialoogvenster](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment). Wanneer het fragment is gemaakt, wordt er naar dit fragment verwezen.

### Content References {#content-references}

[Content References](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) worden gebruikt om naar andere AEM inhoudstypen te verwijzen, zoals afbeeldingen, pagina&#39;s en Experience Fragments.

#### Referentieafbeeldingen {#reference-images}

In **Content Reference** velden die u kunt allebei:

* referentieelementen die al in de gegevensopslagruimte bestaan
* uploadt hen rechtstreeks aan het gebied; dit vermijdt de behoefte om **Activa** te uploaden console

  >[!NOTE]
  >
  >Een afbeelding rechtstreeks uploaden naar de **Content Reference** veld, it **moet**:
  >
  >* een **Hoofdpad** gedefinieerd (in de [Inhoudsfragmentmodel](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference)). Hiermee geeft u aan waar de afbeelding wordt opgeslagen.
  >* include **Afbeelding** in de lijst met toegestane inhoudstypen

U kunt een element toevoegen door:

* het nieuwe elementbestand rechtstreeks (bijvoorbeeld vanaf uw bestandssysteem) naar het **Content Reference** field
* gebruiken **Element toevoegen** actie, en selecteer dan of **Zoeken in middelen** of **Uploaden** om de juiste kiezer voor u te openen:

  ![Inhoudsfragmenteditor - Elementopties toevoegen](assets/cf-authoring-add-asset-options.png)

#### Referentiepagina&#39;s {#reference-pages}

Verwijzingen naar AEM pagina&#39;s, Experience Fragments of andere inhoudstypen toevoegen:

1. Selecteren **Inhoudspad toevoegen**.

1. Voeg het vereiste pad toe aan het invoerveld.

1. Bevestigen met **Toevoegen**.

### Bovenliggende verwijzingen weergeven {#view-parent-references}

Als u het koppelingspictogram op de bovenste werkbalk selecteert, wordt een lijst met alle bovenliggende verwijzingen geopend.

Bijvoorbeeld:

![Content Fragment Editor - Referenties tonen](assets/cf-authoring-show-references-link.png)

Er wordt een venster geopend met een overzicht van alle verwante referenties. Als u een verwijzing wilt openen, selecteert u de naam of titel of het koppelingspictogram.

Bijvoorbeeld:

![Content Fragment Editor - Referenties tonen](assets/cf-authoring-show-references.png)

## Eigenschappen en labels weergeven {#view-properties-tags}

Op het tabblad Eigenschappen van het rechterdeelvenster kunnen eigenschappen (metagegevens) en tags worden weergegeven. De eigenschappen kunnen zijn:

* voor de **Inhoudsfragment** - als **Hoofd** is momenteel geselecteerd
* voor een specifieke **Variatie**

![Inhoudsfragmenteditor - Eigenschappen](assets/cf-authoring-properties.png)

### Eigenschappen en tags bewerken {#edit-properties-tags}

Op het tabblad Eigenschappen (rechterdeelvenster) kunt u ook het volgende bewerken:

* **Titel**
* **Beschrijving**
* **Tags**: gebruiken van de drop-down lijst, of de selectiedialoog

  ![Content Fragment Editor - Tags beheren](assets/cf-authoring-edit-tags.png)

### Het model van het inhoudsfragment openen {#open-content-fragment-model}

Wanneer u **Hoofd** geselecteerd wordt de naam van het onderliggende inhoudsfragmentmodel weergegeven in de sectie Eigenschappen. Als u het koppelingspictogram selecteert, wordt het model op een apart tabblad geopend.

Bijvoorbeeld:

![Inhoudsfragmenteditor - Inhoudsfragmentmodel openen](assets/cf-authoring-open-model.png)

## Versiehistorie weergeven {#view-version-history}

In de **Versiehistorie** in het rechterdeelvenster worden de details van de huidige en vorige versies weergegeven:

>[!NOTE]
>
>Er wordt een nieuwe versie gemaakt wanneer het inhoudsfragment wordt gepubliceerd.

![Inhoudsfragmenteditor - Overzicht van versiegeschiedenis](assets/cf-authoring-version-history-overview.png)

### Versie vergelijken {#compare-version}

Voor een inhoudsfragment kunt u een vorige versie vergelijken met de huidige versie.

Een vorige versie vergelijken met de huidige versie:

1. Selecteer het pictogram met drie punten naast de versie.

1. Selecteren **Ververgelijken**.

![Content Fragment Editor - Versiegeschiedenis vergelijken](assets/cf-authoring-version-history-compare.png)

Hiermee opent u een weergave waarin de verschillen tussen de huidige versie van de inhoud en de geselecteerde vorige versie van het inhoudsfragment worden weergegeven. Van de **Variaties met wijzigingen** kunt u selecteren om de verschillen met de hoofdinhoud en/of inhoud van een variatie te zien.

Verschillen worden aangegeven met kleur:

* Groen: geeft inhoud aan die is toegevoegd (aan de huidige versie)
* Rood: geeft aan dat inhoud is verwijderd (uit de huidige versie)

![Content Fragment Editor - Versiegeschiedenis vergelijken versies](assets/cf-authoring-version-history-compare-versions.png)

### Versie herstellen {#revert-version}

U kunt terugkeren naar elke gewenste versie.

Een specifieke versie herstellen:

1. Selecteer het pictogram met drie punten naast de versie.

1. Selecteren **Vorige versie**.

![Inhoudsfragmenteditor - Versiehistorie herstellen](assets/cf-authoring-version-history-revert.png)

## De taalkopieën bekijken {#view-language-copies}

In de **Taaleigenschappen** tabdetails van eventuele bijbehorende taalkopieën worden weergegeven. Als u een koppelingspictogram selecteert, wordt de kopie op een apart tabblad geopend.

Bijvoorbeeld:

![Content Fragment Editor - Open Language Copy](assets/cf-authoring-open-language-copies.png)

>[!NOTE]
>
>Voor meer informatie over het vertalen van een inhoudsfragment en het maken van taalkopieën raadpleegt u de [AEM doorsnedenloze vertaalreis](/help/journey-headless/translation/overview.md).


## Voorvertoning van fragment weergeven {#preview-content-fragment}

De inhoudsfragmenteditor biedt auteurs de mogelijkheid om een voorvertoning van hun bewerkingen weer te geven in een externe frontendtoepassing.

Als u deze functie wilt gebruiken, moet u eerst:

* Werk met uw IT-team om de externe frontendtoepassing in te stellen die het inhoudsfragment rendert door de JSON-uitvoer te verbruiken.
* Wanneer de externe frontend-toepassing is ingesteld, wordt **URL-standaardvoorvertoningspatroon** moet worden gedefinieerd als [eigenschap van het juiste inhoudsfragmentmodel](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#properties).

Wanneer de URL is gedefinieerd, wordt **Voorvertoning** is actief. U kunt deze knop selecteren om de externe toepassing te starten (op een afzonderlijk tabblad) om het inhoudsfragment te renderen.

## Fragment publiceren {#publish-content-fragment}

U kunt **Publiceren** het fragment naar een van de volgende items:

* Voorbeeldexemplaar
* Instantie publiceren

U kunt het fragment publiceren vanuit de editor of de console. Zie [Een fragment publiceren en voorvertonen](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) voor volledige informatie.

## Publicatie van het fragment ongedaan maken {#unpublish-content-fragment}

U kunt **Publiceren ongedaan maken** het fragment van uw:

* Voorbeeldexemplaar
* Instantie publiceren

U kunt de publicatie van het fragment ongedaan maken vanuit de editor of de console. Zie [Publicatie van een fragment ongedaan maken](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) voor volledige informatie.

## Velden, gegevenstypen en pictogrammen {#fields-datatypes-icons}

De **Velden** worden alle velden in het inhoudsfragment weergegeven. Het pictogram geeft het **[Gegevenstype](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)**:

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><p><b>Tekst met één regel</b></p> </td>
   <td><p> <img src="assets/cf-authoring-single-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Tekst met meerdere regels</b></p> </td>
   <td><p> <img src="assets/cf-authoring-multi-line-text-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Getal</b></p> </td>
   <td><p> <img src="assets/cf-authoring-number-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Boolean</b></p> </td>
   <td><p> <img src="assets/cf-authoring-boolean-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Datum en tijd</b></p> </td>
   <td><p> <img src="assets/cf-authoring-date-time-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Opsomming</b></p> </td>
   <td><p> <img src="assets/cf-authoring-enumeration-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Tags</b></p> </td>
   <td><p> <img src="assets/cf-authoring-tags-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Content Reference</b></p> </td>
   <td><p> <img src="assets/cf-authoring-content-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Fragmentverwijzing</b></p> </td>
   <td><p> <img src="assets/cf-authoring-fragment-reference-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>JSON-object</b></p> </td>
   <td><p> <img src="assets/cf-authoring-json-icon.png"> </p></td>
  </tr>
  <tr>
   <td><p><b>Tijdelijke aanduiding voor tab</b></p><p>Hoewel niet vertegenwoordigd door een daadwerkelijk pictogram, wordt een <b>Tijdelijke aanduiding voor tab</b> wordt weergegeven in het linkerdeelvenster. <br>Het wordt ook weergegeven in het centrale deelvenster, horizontaal zoals weergegeven of in een vervolgkeuzelijst (als er te veel zijn om horizontaal te tonen).</p> </td>
   <td><p> <img src="assets/cf-authoring-tab-icon.png"> </p></td>
  </tr>
 </tbody>
</table>

## Goed om te weten {#good-to-know}

* U moet een inhoudsfragment bewerken [de juiste machtigingen](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions). Neem contact op met de systeembeheerder als er problemen optreden.

  Als u bijvoorbeeld geen `edit` de toestemmingen de redacteur zullen read-only zijn.

* Een inhoudsfragmentmodel kan vaak gegevensvelden definiëren met de naam **Titel** en **Beschrijving**. Als deze velden bestaan, zijn het door de gebruiker gedefinieerde velden en kunnen deze worden bijgewerkt in het dialoogvenster *centraal panel* wanneer u het fragment bewerkt.

  Het inhoudsfragment en de variaties ervan hebben ook metagegevensvelden (eigenschappen voor variatie) die worden genoemd **Titel** en **Beschrijving**. Deze velden maken integraal deel uit van elk inhoudsfragment en worden in eerste instantie gedefinieerd wanneer het fragment wordt gemaakt. Deze kunnen worden bijgewerkt in het dialoogvenster *rechterdeelvenster* wanneer u het fragment bewerkt.

* Zie de documentatie bij Middelen voor volledige informatie over de [oorspronkelijke editor voor inhoudsfragmenten](/help/assets/content-fragments/content-fragments-variations.md) - het is verkrijgbaar bij **Activa** en de **Inhoudsfragmenten** console.

* Uw projectteam kan de redacteur indien nodig aanpassen. Zie [De console en Editor voor inhoudsfragmenten aanpassen](/help/implementing/developing/extending/content-fragments-console-and-editor.md) voor nadere bijzonderheden.
