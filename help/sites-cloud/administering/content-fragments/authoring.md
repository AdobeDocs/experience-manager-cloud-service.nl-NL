---
title: Inhoudsfragmenten ontwerpen
description: Begrijp hoe u inhoud voor uw inhoudsfragmenten ontwerpt en maak variaties van die inhoud afhankelijk van het doel. Inhoudsfragmenten bieden extra flexibiliteit voor zowel de levering zonder kop als het schrijven van pagina's.
feature: Content Fragments
role: User, Developer, Architect
exl-id: a2f2b617-3bdf-4a22-ab64-95f2c65adc82
solution: Experience Manager Sites
source-git-commit: 1fade922ac38340aaaee71794f96db738d492ed6
workflow-type: tm+mt
source-wordcount: '2778'
ht-degree: 0%

---

# Inhoudsfragmenten ontwerpen {#authoring-content-fragments}

Het ontwerpen van inhoudsfragmenten is zowel gericht op de levering zonder kop als op het ontwerpen van pagina&#39;s.

Er zijn twee editors beschikbaar voor inhoudsfragmenten. De editor die in deze sectie wordt beschreven:

* is ontwikkeld voor inhoud zonder kop (hoewel het voor alle scenario&#39;s kan worden gebruikt)
* is beschikbaar bij de **console van de Fragmenten van de Inhoud**

Deze editor biedt:

* [&#x200B; auto-sparen &#x200B;](#saving-autosaving), om toevallig verlies van uitgeeft te verhinderen.
* [&#x200B; In-line het uploaden van activa als inhoudsverwijzingen &#x200B;](#reference-images), zonder het moeten hen aan Activa DAM eerst uploaden.
* [&#x200B; produceer Variaties &#x200B;](#generate-variations-ai) om Generatieve AI te gebruiken om inhoudsverwezenlijking te versnellen die op herinneringen wordt gebaseerd.
* [&#x200B; Voorproef &#x200B;](#preview-content-fragment) van de teruggegeven ervaring die door het Fragment van de Inhoud wordt geleverd.
* Capaciteit om [&#x200B; te publiceren &#x200B;](#publish-content-fragment) en [&#x200B; &#x200B;](#unpublish-content-fragment) van de redacteur ongedaan te maken.
* Capaciteit aan [&#x200B; mening, en open, bijbehorende taalexemplaren &#x200B;](#view-language-copies) in de redacteur.
* Mogelijkheid aan [&#x200B; details van de meningsversie &#x200B;](#view-version-history) in de redacteur. U kunt ook terugkeren naar een geselecteerde versie.
* Capaciteit aan [&#x200B; mening, en open, ouderverwijzingen &#x200B;](#view-parent-references).
* Een hiërarchische mening van het Fragment van de Inhoud, en zijn verwijzingen, gebruikend de [&#x200B; boom van de Structuur &#x200B;](#structure-tree).

>[!WARNING]
>
>De redacteur die in deze sectie wordt beschreven is *slechts* beschikbaar in [&#x200B; Verenigde Shell &#x200B;](/help/overview/aem-cloud-service-on-unified-shell.md); zo *online* Adobe Experience Manager (AEM) as a Cloud Service, niet een lokale instantie.

## Inhoudsfragmenteditor {#content-fragment-editor}

Wanneer u de Inhoudsfragmenteditor voor het eerst opent, ziet u vier hoofdgebieden:

* bovenste werkbalk: voor belangrijke informatie en handelingen
   * een koppeling naar de Content Fragment Console (pictogram Start)
   * informatie over het model en de map
   * verbindingen aan [&#x200B; Voorproef &#x200B;](#preview-content-fragment); als het StandaardPatroon van de Voorproef URL voor het model wordt gevormd
   * [&#x200B; publiceer &#x200B;](#publish-content-fragment), en [&#x200B; unpublish &#x200B;](#unpublish-content-fragment) acties
   * een optie om alle **Verwijzingen van de Ouder** (verbindingspictogram) te tonen
   * het fragment **[Status](/help/sites-cloud/administering/content-fragments/managing.md#statuses-content-fragments)**, en laatst bewaarde informatie
   * een schakeloptie voor het overschakelen naar de oorspronkelijke (op Assets gebaseerde) editor

     >[!WARNING]
     >
     >De oorspronkelijke editor wordt op hetzelfde tabblad geopend. Het wordt afgeraden beide editors tegelijk te openen.

* linkerpaneel: toont de **[Variaties](#variations)** voor het Fragment van de Inhoud, en zijn **Gebieden**:
   * deze verbindingen kunnen worden gebruikt om [&#x200B; de structuur van het Fragment van de Inhoud te navigeren &#x200B;](#navigate-structure)
* juist paneel: stelt lusjes [&#x200B; voor die de eigenschappen (meta-gegevens) en markeringen &#x200B;](#view-properties-tags) tonen, informatie over de [&#x200B; versiegeschiedenis &#x200B;](#view-version-history), en informatie met betrekking tot om het even welke [&#x200B; taalexemplaren &#x200B;](#view-language-copies)
   * in het **lusje van Eigenschappen** kunt u de **Titel** en **Beschrijving** voor het fragment bijwerken, of **Variatie**
   * In het **lusje van Commentaren** kunt u toevoegen, en lezen, commentaren helpen u met andere auteurs samenwerken
* centraal deelvenster: geeft de daadwerkelijke velden en inhoud van de geselecteerde variatie weer
   * kunt u de inhoud bewerken
      * wanneer gevormd (als veelvoud) in het model, staan diverse gegevenstypes u toe **&#x200B;**&#x200B;instanties van het relevante gebied toevoegen
   * als **de gebieden van Tijdelijke aanduiding van het Lusje** worden bepaald binnen het model zij hier en worden getoond:
      * kan worden gebruikt voor navigatie
      * wordt horizontaal weergegeven of als een vervolgkeuzelijst

  >[!NOTE]
  >
  >Afhankelijk van definities in het onderliggende model, kunnen de gebieden aan bepaalde types van [&#x200B; Bevestiging &#x200B;](/help/assets/content-fragments/content-fragments-models.md#validation) onderworpen zijn.

![&#x200B; de Redacteur van het Fragment van de Inhoud - Overzicht &#x200B;](assets/cf-authoring-overview.png)

## Navigeren door de structuur van het inhoudsfragment {#navigate-structure}

één inhoudsfragment;

* Bestaat uit twee niveaus:

   * **[Variaties](#variations)** van het Fragment van de Inhoud
   * **Gebieden** - die door het Model van het Fragment van de Inhoud worden bepaald, en door elke variatie worden gebruikt

* Kan verschillende verwijzingen bevatten.

### Variaties en velden {#variations-and-fields}

In het linkerpaneel kunt u zien:

* de lijst van **[Variaties](#variations)** die voor dit fragment zijn gecreeerd:
   * **Hoofd** is de Variatie die aanwezig is wanneer het Fragment van de Inhoud eerst wordt gecreeerd, kunt u anderen later toevoegen
   * u kunt gebruiken produceert Variaties (#generate-Variaties) om een op herinnering gebaseerde malplaatje te gebruiken dat Adobe voor een specifiek gebruiksgeval heeft gecreeerd.
   * u kunt ook [&#x200B; tot een Variatie &#x200B;](#create-variation) leiden
* de **Gebieden** binnen het fragment, en zijn variaties:
   * het pictogram wijst op het [&#x200B; Type van Gegevens &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)
   * de tekst is de veldnaam
   * deze vormen samen een directe koppeling naar de inhoud van het veld in het centrale venster (voor de huidige variatie)

### Koppelingen volgen {#follow-links}

In verschillende delen van de editor ziet u het koppelingspictogram. Dit pictogram kan worden gebruikt om het weergegeven item te openen, bijvoorbeeld een Content Fragment Model, een Parent Reference of een fragment waarnaar wordt verwezen:

![&#x200B; de Redacteur van het Fragment van de Inhoud - Pictogram van de Verbinding &#x200B;](assets/cf-authoring-link-icon.png)

### Structuurelboom {#structure-tree}

Open het **lusje van de boom van de Structuur** van de redacteurstoolbar om de hiërarchische structuur van het Fragment van de Inhoud, en zijn verwijzingen te tonen. Gebruik de koppelingspictogrammen om naar de referenties te navigeren.

![&#x200B; de Redacteur van het Fragment van de Inhoud - de boom van de Structuur &#x200B;](assets/cf-authoring-structure-tree.png)

>[!NOTE]
>
>Zie [&#x200B; Analyserend de Structuur van het Fragment van de Inhoud - de boom van de Structuur &#x200B;](/help/sites-cloud/administering/content-fragments/analysis.md#structure-tree) voor meer details.

## Opslaan en automatisch opslaan {#saving-autosaving}

<!-- CHECK: cannot be saved, no undo, redo -->

Bij elke update die u maakt, wordt het inhoudsfragment automatisch opgeslagen. De laatst opgeslagen tijd wordt weergegeven in de bovenste werkbalk.

## Variaties {#variations}

[&#x200B; de Variaties &#x200B;](/help/sites-cloud/administering/content-fragments/overview.md#main-and-variations) zijn een significante eigenschap van de Fragmenten van de Inhoud van AEM. Zij staan u toe om exemplaren van de **Belangrijkste** inhoud voor gebruik op specifieke kanalen, en scenario&#39;s tot stand te brengen en uit te geven, makend koploze inhoudslevering en pagina het schrijven nog flexibeler.

Vanuit de editor kunt u:

* [&#x200B; creeer variaties &#x200B;](#create-variation) van de **Belangrijkste** inhoud

* [&#x200B; het Gebruik produceert Variaties AI &#x200B;](#generate-variations-ai) om Generatieve AI te gebruiken om een snel gebaseerd malplaatje te gebruiken dat Adobe voor een specifiek gebruiksgeval heeft gecreeerd.

* Selecteer de gewenste variatie voor het bewerken van de inhoud

* [Naam van variatie wijzigen](#rename-variation)

* [Een variatie verwijderen](#delete-variation)

### Een variatie maken {#create-variation}

Een variatie van het inhoudsfragment maken:

1. In het linkerpaneel, selecteer het **plusteken** (**creeer variatie**) die rechts van **Variaties** is.

   >[!NOTE]
   >
   >Nadat u de eerste variatie hebt gemaakt, worden bestaande variaties in hetzelfde deelvenster weergegeven.

   ![&#x200B; de Redacteur van het Fragment van de Inhoud - creeer uw eerste Variatie &#x200B;](assets/cf-authoring-create-variation-01.png)

1. In de dialoog, ga a **Titel** voor uw variatie in, en a **Beschrijving** als gewild:

   ![&#x200B; de Redacteur van het Fragment van de Inhoud - creeer de dialoog van de Variatie &#x200B;](assets/cf-authoring-create-variation-02.png)

1. **creeer** de variatie. De naam wordt weergegeven in de lijst.

### De naam van een variatie wijzigen {#rename-variation}

Om a **Verandering** anders te noemen:

1. Selecteer de gewenste variatie.

1. Open het **lusje van Eigenschappen** in het juiste paneel.

1. Werk de variatie **Titel** bij.

1. Of druk **Terugkeer** of beweging aan een ander gebied om de verandering auto-sparen. De titel wordt bijgewerkt in het **paneel van Variaties** op de linkerzijde.

### Variaties maken met GenAI met Variaties genereren {#generate-variations-ai}

Gebruik Generatieve variaties om generatieve AI te gebruiken om het maken van inhoud te versnellen.

Open de Inhoudsfragmenteditor om het ingangspunt te zoeken voor het genereren van variaties.

Zie [&#x200B; Variaties produceren - in AEM Editors &#x200B;](/help/generative-ai/generate-variations-integrated-editor.md) geïntegreerd om meer te leren.

### Een wijziging verwijderen {#delete-variation}

Een variatie van het inhoudsfragment verwijderen:

>[!NOTE]
>
>U kunt niet **Hoofd** schrappen.

1. Selecteer de variatie.

1. In het **paneel van de Variatie**, selecteer het schrappingspictogram (het Afval kan):

   ![&#x200B; de Redacteur van het Fragment van de Inhoud - het pictogram van de Variatie van de Schrapping &#x200B;](assets/cf-authoring-delete-variation.png)

1. Er wordt een dialoogvenster geopend. Selecteer **Schrapping** om de actie te bevestigen.

## Tekstvelden met meerdere regels bewerken - Onbewerkte tekst of Markering {#edit-multi-line-text-fields-plaintext-markdown}

**[de gebieden van de 0&rbrace; Meerdere lijntekst &lbrace;kunnen één van drie formaten hebben:](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)**

* Onbewerkte tekst
* [Markering](/help/sites-cloud/administering/content-fragments/markdown.md)
* [RTF](#edit-multi-line-text-fields-rich-text)

Velden die zijn gedefinieerd als Onbewerkte tekst of Markeringen, hebben een eenvoudig tekstvak, zonder opmaakopties (op het scherm):

![&#x200B; de Redacteur van het Fragment van de Inhoud - Meerdere lijntekst - volledig scherm &#x200B;](assets/cf-authoring-multilinetext-plaintext-markdown.png)

## Tekstvelden met meerdere regels bewerken - RTF {#edit-multi-line-text-fields-rich-text}

Voor **[Meerdere lijntekst](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)** gebieden die als **Rijke Tekst** worden bepaald, zijn diverse eigenschappen beschikbaar:

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
* [&#x200B; volledig-het schermredacteur &#x200B;](#full-screen-editor-rich-text) - knevel tussen volledig-scherm en in-stroom
* [Statistieken](#statistics-rich-text)
* [Vergelijken en synchroniseren](#compare-and-synchronize-rich-text)

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - Meerdere lijntekst - het volledig schermknevel &#x200B;](assets/cf-authoring-multilinetext-fullscreen-toggle.png)

>[!NOTE]
>
>De veelvoudige gebieden van de lijntekst worden ook vermeld door het aangewezen [&#x200B; pictogram &#x200B;](#fields-datatypes-icons) in het **paneel van Gebieden**.

### Volledige schermeditor - RTF-tekst {#full-screen-editor-rich-text}

De volledige-schermredacteur biedt de zelfde het uitgeven opties aan zoals wanneer in-stroom - maar biedt meer ruimte voor de tekst aan.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - Meerdere lijntekst - volledig scherm &#x200B;](assets/cf-authoring-multilinetext-fullscreen.png)

### Statistieken - RTF {#statistics-rich-text}

De actie **Statistieken** toont een waaier van informatie over de tekst op een Meerdere lijngebied.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - Statistieken &#x200B;](assets/cf-authoring-multilinetext-statistics.png)

### Vergelijken en synchroniseren - RTF-tekst {#compare-and-synchronize-rich-text}

De actie **vergelijkt** is beschikbaar voor Meerdere lijngebieden wanneer u open de Verandering van de a **&#x200B;**&#x200B;hebt.

Hiermee opent u het veld Meerdere regels op volledig scherm en:

* toont de inhoud voor zowel **Hoofd** als de huidige **Verandering** parallel, met om het even welke benadrukte verschillen

* verschillen worden aangegeven door kleur:

   * groen geeft de toegevoegde inhoud aan (aan de variatie)
   * rood geeft aan dat inhoud is verwijderd (uit de variatie)
   * blauw geeft vervangen tekst aan

* verstrekt de **Synchronisatie** actie, die de inhoud van **Hoofd** aan de huidige variatie synchroniseert

   * als **Hoofd** is bijgewerkt, dan zullen deze veranderingen worden overgebracht naar de variatie
   * als de variatie is bijgewerkt, dan zullen deze veranderingen door de inhoud van **Hoofd** worden overschreven

  >[!CAUTION]
  >
  >De synchronisatie is slechts beschikbaar om veranderingen *van **Hoofd**&#x200B;aan de variatie* te kopiëren.
  >
  >Het overbrengen van veranderingen *van een variatie aan **Hoofd*** is niet beschikbaar als optie.

Bijvoorbeeld, een scenario waar de variatieinhoud volledig was herschreven, zodat zal een synchronisatie die nieuwe inhoud met de inhoud van **Hoofd** vervangen:

![&#x200B; de Redacteur van het Fragment van de Inhoud - vergelijk en synchroniseer &#x200B;](assets/cf-authoring-multilinetext-compare.png)

## Referenties beheren {#manage-references}

### Fragmentverwijzingen {#fragment-references}

[&#x200B; de Verwijzingen van het Fragment &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#fragment-reference-nested-fragments) kunnen worden gebruikt om:

* [een verwijzing naar een bestaand inhoudsfragment maken](#create-reference-existing-content-fragment)
* [een inhoudsfragment maken en ernaar verwijzen](#create-reference-content-fragment)

#### Een verwijzing naar een bestaand inhoudsfragment maken {#create-reference-existing-content-fragment}

Een verwijzing naar een bestaand inhoudsfragment maken:

1. Selecteer het veld.
1. Selecteer **toevoegen bestaand fragment**.
1. Selecteer het gewenste fragment in de fragmentkiezer.

   >[!NOTE]
   >
   >U mag slechts één fragment tegelijk selecteren.

#### Een inhoudsfragment en verwijzing maken {#create-reference-content-fragment}

Alternatief kunt u [&#x200B; selecteren **nieuw fragment** creëren om **te openen creeer** dialoog &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#creating-a-content-fragment). Wanneer het fragment is gemaakt, wordt er naar dit fragment verwezen.

### Content References {#content-references}

[&#x200B; Verwijzingen van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference) worden gebruikt om andere inhoudstypes van AEM, zoals beelden, pagina&#39;s, en de Fragmenten van de Ervaring van verwijzingen te voorzien.

#### Referentieafbeeldingen {#reference-images}

In **de gebieden van de Verwijzing van de Inhoud** kunt u:

* verwijzingselementen die al in uw lokale opslagplaats bestaan
* referentiemiddelen die zich in een externe opslagplaats bevinden
* uploadt activa rechtstreeks aan het gebied; dit vermijdt de behoefte om de **Assets** console te gebruiken om te uploaden

  >[!NOTE]
  >
  >Om een beeld aan het **gebied van de Verwijzing van de Inhoud direct te uploaden**, moet het **&#x200B;**:
  >
  >* hebben a **Weg van de Weg van de Weg van de Wortel** bepaald (in het [&#x200B; Model van het Fragment van de Inhoud &#x200B;](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#content-reference)). Hiermee geeft u aan waar de afbeelding wordt opgeslagen.
  >* omvat **Beeld** in de lijst van toegelaten inhoudstypes

##### Referentie lokale Assets {#reference-local-assets}

Als u naar een lokaal element wilt verwijzen, kunt u:

* belemmering en laat vallen het nieuwe activadossier direct (bijvoorbeeld, van uw dossiersysteem) in het **gebied van de Verwijzing van de Inhoud**
* gebruik **activa** actie toevoegen, dan uitgezocht of **doorbladeren Assets** of **uploadt** om de aangewezen selecteur voor u te openen om te gebruiken:

  ![&#x200B; de Redacteur van het Fragment van de Inhoud - voeg activaopties &#x200B;](assets/cf-authoring-add-asset-options.png) toe

##### Referentie externe Assets {#reference-remote-assets}

Verwijzen naar externe elementen:

1. Specificeer de verre **Bewaarplaats** wanneer het doorbladeren voor activa:

   ![&#x200B; de Redacteur van het Fragment van de Inhoud - Uitgezochte Activa van ver &#x200B;](assets/cf-authoring-remote-asset-01.png)

2. Na de selectie kunt u de locatie zien in de elementgegevens:

   ![&#x200B; de Redacteur van het Fragment van de Inhoud - Activa van verre bewaarplaats &#x200B;](assets/cf-authoring-remote-asset-02.png)

###### Externe Assets - Beperkingen {#remote-assets-limitations}

Er zijn enkele beperkingen wanneer wordt verwezen naar externe middelen:

* Slechts [&#x200B; goedgekeurde &#x200B;](/help/assets/approve-assets.md) activa zijn beschikbaar voor verwijzing van een verre bewaarplaats van Activa.

* Als een element waarnaar wordt verwezen, wordt verwijderd uit de externe opslagplaats, resulteert dit in een verbroken Content Reference.

* Alle opslagplaatsen voor leveringsmiddelen waartoe de gebruiker toegang heeft, zijn beschikbaar voor selectie. De beschikbare lijst kan niet worden beperkt.

* Zowel de AEM-instantie als de externe gegevensopslagruimte moeten dezelfde versie hebben.

* Er worden geen metagegevens van middelen weergegeven via de API voor beheer of de API voor levering. U moet de API voor metagegevens van middelen gebruiken om de metagegevens van de elementen op te halen:

   * de individuele activa meta-gegevens: [&#x200B; https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetMetadata](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetMetadata)

   * krijg bulkmeta-gegevensinformatie gebruikend (experimenteel) onderzoek API: [&#x200B; https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/search &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/search)

>[!NOTE]
>
>Zie ook [&#x200B; AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud - Dynamische Media voor OpenAPI activa steun (Verre Assets) &#x200B;](/help/headless/graphql-api/content-fragments.md#dynamic-media-for-openapi-asset-support)

#### Referentiepagina&#39;s {#reference-pages}

Verwijzingen naar AEM-pagina&#39;s, Experience Fragments of andere soorten inhoud toevoegen:

1. Selecteer **toevoegen inhoudsweg**.

1. Voeg het vereiste pad toe aan het invoerveld.

1. Bevestig met **toevoegt**.

>[!NOTE]
>
>Dit mag niet worden gebruikt voor verwijzingen naar:
>
>* De Fragmenten van de inhoud - gebruik de Verwijzing van het a [&#x200B; Fragment &#x200B;](#fragment-references)
>* Beelden - gebruik [&#x200B; Beelden van de Verwijzing &#x200B;](#reference-images)

### Bovenliggende verwijzingen weergeven {#view-parent-references}

Als u het koppelingspictogram op de bovenste werkbalk selecteert, wordt een lijst met alle bovenliggende verwijzingen geopend.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - toon Verwijzingen &#x200B;](assets/cf-authoring-show-references-link.png)

Er wordt een venster geopend met een overzicht van alle verwante referenties. Als u een verwijzing wilt openen, selecteert u de naam of titel of het koppelingspictogram.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - toon Verwijzingen &#x200B;](assets/cf-authoring-show-references.png)

## Eigenschappen en labels weergeven {#view-properties-tags}

Op het tabblad Eigenschappen van het rechterdeelvenster kunnen eigenschappen (metagegevens) en tags worden weergegeven. De eigenschappen kunnen zijn:

* voor het **Fragment van de Inhoud** - als **Hoofd** momenteel wordt geselecteerd
* voor een specifieke **Variatie**

![&#x200B; de Redacteur van het Fragment van de Inhoud - Eigenschappen &#x200B;](assets/cf-authoring-properties.png)

### Eigenschappen en tags bewerken {#edit-properties-tags}

Op het tabblad Eigenschappen (rechterdeelvenster) kunt u ook het volgende bewerken:

* **Titel**
* **Beschrijving**
* **Markeringen**: het gebruiken van de drop-down lijst, of de selectiedialoog

  ![&#x200B; de Redacteur van het Fragment van de Inhoud - leidt Markeringen &#x200B;](assets/cf-authoring-edit-tags.png)

### Het model van het inhoudsfragment openen {#open-content-fragment-model}

Wanneer u **Hoofd** hebt geselecteerd, wordt de naam van het onderliggende Model van het Fragment van de Inhoud getoond in de eigenschappen sectie. Als u het koppelingspictogram selecteert, wordt het model op een apart tabblad geopend.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - open Model van het Fragment van de Inhoud &#x200B;](assets/cf-authoring-open-model.png)

## Versiehistorie weergeven {#view-version-history}

In het **de geschiedenislusje van de Versie** van het juiste paneel, worden de details van huidige, en vorige, versies getoond:

>[!NOTE]
>
>Er wordt een nieuwe versie gemaakt wanneer het inhoudsfragment wordt gepubliceerd.

![&#x200B; de Redacteur van het Fragment van de Inhoud - het Overzicht van de Geschiedenis van de Versie &#x200B;](assets/cf-authoring-version-history-overview.png)

### Versie vergelijken {#compare-version}

Voor een inhoudsfragment kunt u een vorige versie vergelijken met de huidige versie.

Een vorige versie vergelijken met de huidige versie:

1. Selecteer het pictogram met drie punten naast de versie.

1. Selecteer **vergelijken**.

![&#x200B; de Redacteur van het Fragment van de Inhoud - de Geschiedenis van de Versie vergelijkt &#x200B;](assets/cf-authoring-version-history-compare.png)

Hiermee opent u een weergave waarin de verschillen tussen de huidige versie van de inhoud en de geselecteerde vorige versie van het inhoudsfragment worden weergegeven. Van de **Variaties met veranderingen** drop-down, kunt u selecteren om verschillen van de Belangrijkste inhoud en/of inhoud van een Variatie te zien.

Verschillen worden aangegeven met kleur:

* Groen: geeft inhoud aan die is toegevoegd (aan de huidige versie)
* Rood: geeft aan dat inhoud is verwijderd (uit de huidige versie)

![&#x200B; de Redacteur van het Fragment van de Inhoud - de Geschiedenis van de Versie vergelijkt Versies &#x200B;](assets/cf-authoring-version-history-compare-versions.png)

### Versie herstellen {#revert-version}

U kunt terugkeren naar elke gewenste versie.

Een specifieke versie herstellen:

1. Selecteer het pictogram met drie punten naast de versie.

1. Selecteer **terugkeren**.

![&#x200B; de Redacteur van het Fragment van de Inhoud - de Geschiedenis van de Versie terugkeert &#x200B;](assets/cf-authoring-version-history-revert.png)

## De taalkopieën bekijken {#view-language-copies}

In de **eigenschappen van de Taal** lusjedetails van om het even welke verwante taalexemplaren worden getoond. Als u een koppelingspictogram selecteert, wordt de kopie op een apart tabblad geopend.

Bijvoorbeeld:

![&#x200B; de Redacteur van het Fragment van de Inhoud - open Exemplaar van de Taal &#x200B;](assets/cf-authoring-open-language-copies.png)

>[!NOTE]
>
>Voor meer details over het vertalen van een Fragment van de Inhoud, en het creëren van taalexemplaren, zie de [&#x200B; Hoofdloze Vertaalreis van AEM &#x200B;](/help/journey-headless/translation/overview.md).

## Opmerkingen over het fragment {#commenting-on-your-fragment}

Om u toe te laten om in-product en in-context samen te werken, verstrekt het **lusje van Commentaren** in het juiste paneel de volgende mogelijkheden:

* Een nieuwe opmerking toevoegen
* Specifieke gebruikers in een opmerking labelen
   * Ze ontvangen een melding met een koppeling om het fragment rechtstreeks te openen
* Als een bestaande opmerking
* Een opmerking beantwoorden
* Uw opmerkingen opmaken; basisopmaak is beschikbaar
* Een tekstzoekopdracht uitvoeren met bestaande opmerkingen
* Een bestaande opmerking bewerken
* Opmerkingen verwijderen

![&#x200B; de Redacteur van het Fragment van de Inhoud - Commentaren tabel &#x200B;](assets/cf-authoring-comments.png)

>[!NOTE]
>
>Deze commentaren zijn niet zichtbaar als [&#x200B; Annotaties in de originele redacteur &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#annotating-a-content-fragment), noch in de [&#x200B; Chronologie van de console van Assets &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

## Voorvertoning van fragment weergeven {#preview-content-fragment}

De inhoudsfragmenteditor biedt auteurs de mogelijkheid om een voorvertoning van hun bewerkingen weer te geven in een externe frontendtoepassing. Dit vereist dat het **[StandaardPatroon van de Voorproef URL](/help/sites-cloud/administering/content-fragments/preview.md#preview-url-pattern)** wordt bepaald, om de **knoop van de Voorproef** in de hoogste toolbar van de redacteur te activeren. U kunt deze knop selecteren om de externe toepassing te starten (op een afzonderlijk tabblad) om het inhoudsfragment te renderen.

## Fragment publiceren {#publish-content-fragment}

U kunt **publiceren** uw fragment aan of uw:

* Voorbeeldexemplaar
* Instantie publiceren

U kunt het fragment publiceren vanuit de editor of de console. Zie [&#x200B; het Publiceren en het Voorvertonen van een Fragment &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) voor volledige details.

## Publicatie van het fragment ongedaan maken {#unpublish-content-fragment}

U kunt **ook unpublish** uw fragment van of uw:

* Voorbeeldexemplaar
* Instantie publiceren

U kunt de publicatie van het fragment ongedaan maken vanuit de editor of de console. Zie [&#x200B; Unpublishing een fragment &#x200B;](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) voor volledige details.

## Velden, gegevenstypen en pictogrammen {#fields-datatypes-icons}

Het **paneel van Gebieden** maakt een lijst van alle gebieden binnen het Fragment van de Inhoud. Het pictogram wijst op het **[Type van Gegevens](/help/sites-cloud/administering/content-fragments/content-fragment-models.md#data-types)**:

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
   <td><p><b>Tijdelijke aanduiding voor tab</b></p><p>Hoewel niet vertegenwoordigd door een werkelijk pictogram, wordt Placeholder van het a <b> Lusje </b> vertegenwoordigd in het linkerpaneel. <br> het wordt ook vertegenwoordigd in het centrale paneel, of horizontaal zoals getoond, of in een drop-down lijst (wanneer er teveel zijn om horizontaal te tonen).</p> </td>
   <td><p> <img src="assets/cf-authoring-tab-icon.png"> </p></td>
  </tr>
 </tbody>
</table>

## Goed om te weten {#good-to-know}

* Om een Fragment van de Inhoud uit te geven hebt u [&#x200B; de aangewezen toestemmingen &#x200B;](/help/implementing/developing/extending/content-fragments-customizing.md#asset-permissions) nodig. Neem contact op met de systeembeheerder als er problemen optreden.

  Als u bijvoorbeeld geen `edit` -machtigingen hebt, is de editor alleen-lezen.

* Een model van het Fragment van de Inhoud kan gegevensgebieden vaak bepalen genoemd **Titel** en **Beschrijving**. Als deze gebieden bestaan, zijn zij user-defined gebieden en kunnen in het *centrale paneel* worden bijgewerkt wanneer het uitgeven van het fragment.

  Het tevreden Fragment, en zijn variaties, hebben ook meta-gegevensgebieden (de eigenschappen van de Variatie) geroepen **Titel** en **Beschrijving**. Deze velden maken integraal deel uit van elk inhoudsfragment en worden in eerste instantie gedefinieerd wanneer het fragment wordt gemaakt. Zij kunnen in het *juiste paneel* worden bijgewerkt wanneer het uitgeven van het fragment.

* Zie de documentatie van Assets voor volledige informatie over de [&#x200B; originele redacteur van het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) - het is beschikbaar van zowel de **Assets** console als de **console van de Fragmenten van de Inhoud**.

* Uw projectteam kan de redacteur indien nodig aanpassen. Zie [&#x200B; het Aanpassen van de Console en de Redacteur van het Fragment van de Inhoud &#x200B;](/help/implementing/developing/extending/content-fragments-console-and-editor.md) voor verdere details.
