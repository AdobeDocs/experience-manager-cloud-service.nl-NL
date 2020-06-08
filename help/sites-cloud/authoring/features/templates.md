---
title: Paginasjablonen maken
description: De sjabloon definieert de structuur van de resulterende pagina en met de sjablooneditor. Het maken en onderhouden van sjablonen is niet langer een taak die alleen voor ontwikkelaars geldt
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '4554'
ht-degree: 11%

---


# Paginasjablonen maken {#creating-page-templates}

Wanneer u een pagina maakt, moet u een sjabloon selecteren die wordt gebruikt als basis voor het maken van de nieuwe pagina. De sjabloon definieert de structuur van de resulterende pagina, eventuele eerste inhoud en de componenten die kunnen worden gebruikt.

Met de **Sjablooneditor** is het creëren en onderhouden van sjablonen niet meer alleen een taak voor ontwikkelaars. Een hoofdgebruiker die ook **maker van sjablonen** wordt genoemd, kan ook worden betrokken. Ontwikkelaars zijn nog steeds nodig om de omgeving in te stellen, clientbibliotheken te maken en de te gebruiken componenten te maken, maar zodra deze basisbeginselen zijn ingesteld, kan de **maker van sjablonen** sjablonen maken en configureren zonder een ontwikkelingsproject.

Met de **Sjabloonconsole** kunnen sjabloonauteurs:

* Maak een nieuwe sjabloon of kopieer een bestaande sjabloon.
* De levenscyclus van de sjabloon beheren.

Met de **Sjablooneditor** kunnen sjabloonauteurs:

* Voeg componenten aan het malplaatje toe en plaats hen op een ontvankelijk net.
* Configureer de componenten vooraf.
* Bepaal welke componenten op pagina&#39;s kunnen worden uitgegeven die met het malplaatje worden gecreeerd.

In dit document wordt uitgelegd hoe een **sjabloonauteur** de sjabloonconsole en -editor kan gebruiken om bewerkbare sjablonen te maken en te beheren.

Voor gedetailleerde informatie over hoe de editable malplaatjes op een technisch niveau werken, te zien gelieve het document van de ontwikkelaar Pagina Malplaatjes - editable voor meer informatie. <!-- For detailed information about how editable templates work at a technical level, please see the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md) for more information.-->

>[!NOTE]
>
>De **sjablooneditor** biedt geen ondersteuning voor rechtstreekse targeting op het sjabloonniveau. Pagina&#39;s die zijn gemaakt op basis van een bewerkbare sjabloon, kunnen als doel worden ingesteld, maar de sjablonen zelf kunnen dat niet.

## Before You Start {#before-you-start}

>[!NOTE]
>
>Een beheerder moet een malplaatjeomslag in Browser **van** Configuraties vormen en juiste toestemmingen toepassen alvorens een malplaatjeauteur een malplaatje in die omslag kan tot stand brengen.

Voordat u begint, is het belangrijk om te bedenken dat voor het maken van een nieuwe sjabloon samenwerking vereist is. Daarom wordt voor elke taak de [rol](#roles) vermeld. Dit heeft geen invloed op de manier waarop u een sjabloon gebruikt om een pagina te maken, maar het heeft wel invloed op de manier waarop een pagina betrekking heeft op de sjabloon.

### Rollen {#roles}

Om een nieuwe sjabloon te maken met behulp van de **sjabloonconsole** en de **sjablooneditor** is samenwerking tussen de volgende rollen vereist:

* **Beheerder**:
   * Hiermee maakt u een nieuwe map voor sjablonen waarvoor `admin` rechten vereist zijn.
   * Dergelijke taken kunnen vaak ook door een ontwikkelaar worden uitgevoerd
* **Developer**:
   * Concentraties op de technische/interne details
   * Heeft ervaring nodig met de ontwikkelomgeving.
   * Verstrekt de malplaatjeauteur van noodzakelijke informatie.
* **Sjabloonauteur**:
   * Dit is een specifieke auteur die lid is van de groep `template-authors`
      * Hiermee worden de vereiste rechten en machtigingen toegewezen.
   * Kan het gebruik van componenten en andere details op hoog niveau configureren die het volgende vereisen:
      * Enkele technische kennis
         * Gebruik bijvoorbeeld patronen bij het definiëren van paden.
      * Technische informatie van de ontwikkelaar.

Vanwege de aard van sommige taken, zoals het maken van een map, is een ontwikkelomgeving nodig. Hiervoor is kennis en ervaring vereist.

De in dit document beschreven taken worden weergegeven met de rol die verantwoordelijk is voor de uitvoering ervan.

## Creating and Managing Templates {#creating-and-managing-templates}

Bij het maken van een nieuwe bewerkbare sjabloon:

* Gebruik de **Sjabloonconsole** . Dit is beschikbaar in de **Algemene** sectie van de console van **Hulpmiddelen** .
   * Of rechtstreeks bij: `https://<host>:<port>/libs/wcm/core/content/sites/templates.html/conf`
* Kan zo nodig een map voor de sjablonen [](#creating-a-template-folder-admin) maken
* [Een nieuwe sjabloon](#creating-a-new-template-template-author)maken die aanvankelijk leeg is
* [Definieer indien nodig aanvullende eigenschappen](#defining-template-properties-template-author) voor de sjabloon
* [Bewerk de sjabloon](#editing-templates-template-authors) om het volgende te definiëren:
   * [Structuur](#editing-a-template-structure-template-author) - vooraf gedefinieerde inhoud die niet kan worden gewijzigd op pagina&#39;s die met de sjabloon zijn gemaakt.
   * [Eerste inhoud](#editing-a-template-initial-content-author) - vooraf gedefinieerde inhoud die kan worden gewijzigd op pagina&#39;s die met de sjabloon zijn gemaakt.
   * [Layout](#editing-a-template-layout-template-author) - Voor een reeks apparaten.
   * [Stijlen](/help/sites-cloud/authoring/features/style-system.md) - Definieer de stijlen die met de sjabloon en de componenten ervan moeten worden gebruikt.
* [De sjabloon](#enabling-a-template-template-author) inschakelen voor gebruik bij het maken van een pagina
* [De sjabloon](#allowing-a-template-author) voor de vereiste pagina of vertakking van uw website toestaan
* [De sjabloon](#publishing-a-template-template-author) publiceren om deze beschikbaar te maken in de publicatieomgeving

>[!NOTE]
>
>De **toegestane sjablonen** zijn vaak vooraf gedefinieerd wanneer uw website voor het eerst wordt ingesteld.

>[!CAUTION]
>
>Voer nooit informatie in die u wilt internationaliseren in een sjabloon. <!-- Never enter any information that needs to be [internationalized](/help/sites-developing/i18n.md) into a template.-->
>
>Voor sjabloonelementen zoals kop- en voetteksten die moeten worden gelokaliseerd, kunt u de [lokalisatiefuncties van de kerncomponenten benutten.](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)

### Sjabloonmap maken - Beheer {#creating-a-template-folder-admin}

Een malplaatjeomslag zou voor uw project moeten worden gecreeerd om uw project-specifieke malplaatjes te houden. Dit is een beheertaak die wordt beschreven in het document Paginasjablonen - Bewerkbaar. <!-- A template folder should be created for your project to hold your project-specific templates. This is an admin task and is described in the document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-folders).-->

### Een nieuwe sjabloon maken - Sjabloonauteur {#creating-a-new-template-template-author}

1. Open de **sjabloonconsole** (via **Gereedschappen ->** **Algemeen**) en ga vervolgens naar de vereiste map.

   >[!NOTE]
   >
   >In een standaard AEM-instantie bestaat de **algemene** map al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden.
   >
   >Het wordt aanbevolen een sjabloonmap te gebruiken die voor uw project is gemaakt. <!-- It is recommended best practice to use a [template folder created for your project](/help/sites-developing/page-templates-editable.md#template-folders).-->

1. Selecteer **Maken**, gevolgd door **Sjabloon** maken om de wizard te openen.

1. Kies een **Sjabloontype** en selecteer **Volgende**.

   >[!NOTE]
   >
   >Sjabloontypen zijn vooraf gedefinieerde sjabloonlay-outs en kunnen worden beschouwd als sjablonen voor een sjabloon. Deze worden vooraf bepaald door ontwikkelaars of de systeembeheerder. Meer informatie vindt u in het ontwikkelaarsdocument Paginasjablonen - Bewerkbaar. <!-- More information can be found in the developer document [Page Templates - Editable](/help/sites-developing/page-templates-editable.md#template-type).-->

1. Voer de **sjabloondetails** in:

   * **Sjabloonnaam**
   * **Beschrijving**

1. Selecteer **Maken**. Er wordt een bevestiging weergegeven. Selecteer **Openen** om de sjabloon te bewerken of **Gereed** om terug te keren naar de sjabloonconsole.

   >[!NOTE]
   >
   >Wanneer een nieuw malplaatje wordt gecreeerd is het duidelijk als **Ontwerp** in de console, wijst dit erop dat het nog niet beschikbaar aan gebruik door paginaauteurs is.

### Sjablooneigenschappen definiëren - Sjabloonauteur {#defining-template-properties-template-author}

Een sjabloon kan de volgende eigenschappen hebben:

* Afbeelding
   * Afbeelding die moet worden gebruikt als [miniatuur van de sjabloon](#template-thumbnail-image) voor selectie, zoals in de wizard Pagina maken.
      * Kan worden geüpload
      * Kan worden gegenereerd op basis van de sjablooninhoud
* Titel
   * Een titel die wordt gebruikt voor het identificeren van de sjabloon, zoals in de wizard **Pagina** maken.
* Beschrijving
   * Een optionele beschrijving voor meer informatie over de sjabloon en het gebruik ervan, bijvoorbeeld in de wizard **Pagina** maken.

De eigenschappen weergeven en/of bewerken:

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Selecteer **Eigenschappen weergeven** op de werkbalk of kies Snelle opties om het dialoogvenster te openen.
1. U kunt nu de sjablooneigenschappen weergeven of bewerken.

>[!NOTE]
>
>De status van een sjabloon (concept, ingeschakeld of uitgeschakeld) wordt aangegeven in de console.

#### Miniatuurafbeelding sjabloon {#template-thumbnail-image}

De sjabloonminiatuur definiëren:

1. Bewerk de sjablooneigenschappen.
1. Kies of u een miniatuur wilt uploaden of wilt dat deze wordt gegenereerd op basis van de sjablooninhoud.
   * Als u een miniatuur wilt uploaden, klikt u of tikt u op Afbeelding **uploaden**
   * Als u een miniatuur wilt genereren, klikt u of tikt u op Voorvertoning **genereren**
1. Voor beide methoden wordt een voorbeeld van de miniatuur weergegeven.
   * Als dit niet het geval is, klikt u of tikt u op **Wissen** om een andere afbeelding te uploaden of de miniatuur opnieuw te genereren.
1. Als u tevreden bent met de miniatuur, klikt u of tikt u op **Opslaan en sluiten**.

### Een sjabloon inschakelen en toestaan - Sjabloonauteur {#enabling-and-allowing-a-template-template-author}

Als u een sjabloon wilt kunnen gebruiken bij het maken van een pagina, moet u:

* [Schakel de sjabloon](#enabling-a-template-template-author) in om deze beschikbaar te maken voor gebruik bij het maken van pagina&#39;s.
* [Hiermee kan de sjabloon](#allowing-a-template-author) de vertakkingen van de inhoud aangeven waarin de sjabloon kan worden gebruikt.

#### Sjabloon inschakelen - Sjabloonauteur {#enabling-a-template-template-author}

U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken in de wizard **Pagina** maken.

>[!CAUTION]
>
>Zodra een malplaatje wordt toegelaten zal een waarschuwing worden getoond wanneer een malplaatjeauteur begint om het malplaatje verder bij te werken. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Selecteer **Inschakelen** of **Uitschakelen** op de werkbalk en nogmaals in het bevestigingsvenster.
1. U kunt de sjabloon nu gebruiken wanneer u een nieuwe pagina [](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page)maakt, maar u wilt de sjabloon [waarschijnlijk naar wens](#editing-templates-template-authors) bewerken.

>[!NOTE]
>
>De status van een sjabloon (concept, ingeschakeld of uitgeschakeld) wordt aangegeven in de console.

#### Een sjabloon toestaan - Auteur {#allowing-a-template-author}

Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

1. Open de [Pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) voor de hoofdpagina van de vertakking waar u de sjabloon wilt plaatsen.
1. Open het tabblad **Geavanceerd** .
1. Gebruik onder **Sjablooninstellingen** de optie **Veld toevoegen** om het pad of de paden naar de sjabloon of sjablonen op te geven.

   Het pad kan expliciet zijn of patronen gebruiken. Bijvoorbeeld:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   De volgorde van de paden is irrelevant, alle paden worden gescand en sjablonen worden opgehaald.

   >[!NOTE]
   >
   >Als de lijst **Toegestane sjablonen** leeg blijft, wordt de structuur opgetrokken totdat een waarde/lijst wordt gevonden.
   >
   >
   >Zie Sjabloonbeschikbaarheid - de principes voor toegestane sjablonen blijven ongewijzigd. <!--See [Template Availability](/help/sites-developing/templates.md#template-availability) - the principles for allowed templates remain the same.-->

1. Klik op **Opslaan** om de wijzigingen in de pagina-eigenschappen op te slaan.

>[!NOTE]
>
>Vaak zijn de toegestane sjablonen vooraf gedefinieerd voor uw gehele site wanneer deze wordt ingesteld.

### Een sjabloon publiceren - Sjabloonauteur {#publishing-a-template-template-author}

Aangezien het malplaatje van verwijzingen wordt voorzien wanneer een pagina wordt teruggegeven, moet het volledig gevormde malplaatje worden gepubliceerd zodat het op het publicatiemilieu beschikbaar is.

1. Selecteer de sjabloon in de **Sjabloonconsole**.
1. Select **Publish** from the toolbar to open the wizard.
1. Selecteer het **inhoudsbeleid** dat u samen wilt publiceren.
1. Selecteer **Publiceren** op de werkbalk om de handeling te voltooien.

## Sjablonen bewerken - Sjabloonauteurs {#editing-templates-template-authors}

Bij het maken of bewerken van een sjabloon zijn er verschillende aspecten die u kunt definiëren. Sjablonen bewerken is vergelijkbaar met het ontwerpen van pagina&#39;s.

Met de **moduskiezer** op de werkbalk kunt u het juiste aspect van de sjabloon selecteren en bewerken:

* [Structuur](#editing-a-template-structure-template-author)
* [Oorspronkelijke inhoud](#editing-a-template-initial-content-author)
* [Indeling](#editing-a-template-layout-template-author)

![Sjabloonbewerkingsmodus selecteren](/help/sites-cloud/authoring/assets/templates-mode.png)

Met de optie **Paginabeleid** in het menu **Pagina-informatie** kunt u wel het vereiste paginabeleid [](#page-policies)selecteren:

![Pagina-informatie sjablooneditor](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Als een auteur een sjabloon gaat bewerken die al is ingeschakeld, wordt een waarschuwing weergegeven. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

### Sjabloonkenmerken {#template-attributes}

De volgende kenmerken van een sjabloon kunnen worden bewerkt:

#### Structuur {#template-structure}

Componenten die aan de [structuur](#editing-a-template-structure-template-author) zijn toegevoegd, kunnen door de auteurs van de pagina niet worden verplaatst of verwijderd uit de resulterende pagina&#39;s. Als u wilt dat auteurs van pagina&#39;s componenten aan resulterende pagina&#39;s kunnen toevoegen en verwijderen, dan moet u een paragraafsysteem aan het malplaatje toevoegen.

Wanneer componenten zijn vergrendeld, kunt u inhoud toevoegen die niet kan worden bewerkt door auteurs van pagina&#39;s. U kunt componenten ontgrendelen, zodat u [initiële inhoud](#editing-a-template-initial-content-author)kunt definiëren.

>[!NOTE]
>
>In de structuurmodus kunnen componenten die het bovenliggende element van een niet-vergrendelde component zijn, niet worden verplaatst, geknipt of verwijderd.

#### Oorspronkelijke inhoud {#template-initial-content}

Wanneer een component ontgrendeld is, kunt u de [eerste inhoud](#editing-a-template-initial-content-author) definiëren die naar de resulterende pagina(&#39;s), gemaakt op basis van de sjabloon, wordt gekopieerd. Deze niet-vergrendelde componenten kunnen op de resulterende pagina(&#39;s) worden bewerkt.

>[!NOTE]
>
>In de modus **Oorspronkelijke inhoud** en op de resulterende pagina&#39;s kunnen alle ontgrendelde onderdelen met een toegankelijk bovenliggend element (d.w.z. onderdelen in een lay-outcontainer) worden verwijderd.

#### Indeling {#template-layout}

Met de [lay-out](#editing-a-template-layout-template-author) kunt u de sjabloonlay-out voor de vereiste apparaatindelingen vooraf bepalen. De modus **Lay-out** voor het ontwerpen van sjablonen heeft dezelfde functionaliteit als de modus [**Lay-out **voor het ontwerpen van pagina&#39;s](/help/sites-cloud/authoring/features/responsive-layout.md#defining-layouts-layout-mode).

#### Paginabeleid {#template-page-policies}

[Met paginabeleid](#page-policies) kunt u vooraf gedefinieerde paginabeleidsregels verbinden met de pagina. Met dit paginabeleid worden de verschillende ontwerpconfiguraties gedefinieerd.

#### Stijlen {#template-styles}

Met het [Stijlsysteem](/help/sites-cloud/authoring/features/style-system.md) kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.

Zie de documentatie [van het Systeem van de](/help/sites-cloud/authoring/features/style-system.md) Stijl voor meer informatie.

### Een sjabloon bewerken - Structuur - Sjabloonauteur {#editing-a-template-structure-template-author}

In de modus **Structuur** definieert u componenten en inhoud voor de sjabloon en definieert u het beleid voor de sjabloon en de componenten ervan.

* Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
* Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
* Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u [initiële inhoud](#editing-a-template-initial-content-author)kunt definiëren.
* Het ontwerpbeleid voor de componenten en pagina wordt gedefinieerd.

![Paginastructuur van de sjablooneditor](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Er zijn een aantal acties die u kunt uitvoeren in de modus **Structuur** van de sjablooneditor en een aantal functies om u te helpen:

#### Componenten toevoegen {#add-components}

Er zijn verschillende manieren om componenten aan de sjabloon toe te voegen:

* Vanuit de browser **Componenten** in het zijpaneel.
* Met de optie **Component invoegen** op de werkbalk kunt u componenten gebruiken die zich al in de sjabloon bevinden of het vak **Componenten hierheen slepen**.
* Sleep een element (vanuit de **middelenbrowser** in het zijpaneel) rechtstreeks naar de sjabloon om de juiste component ter plekke te genereren.

Na toevoeging wordt elke component gemarkeerd met:

* Een rand
* Een markering waarmee het componenttype wordt weergegeven
* Een markering die moet worden weergegeven wanneer de component is ontgrendeld

>[!NOTE]
>
>Wanneer u een standaardcomponent voor de **Titel** aan de sjabloon toevoegt, zal het de **standaardtekststructuur** bevatten.
>
>Als u dit wijzigt en uw eigen tekst toevoegt, wordt deze bijgewerkte tekst gebruikt wanneer een pagina wordt gemaakt op basis van de sjabloon.
>
>Als u de standaardtekst (structuur) verlaat, wordt de titel standaard ingesteld op de naam van de volgende pagina.

>[!NOTE]
>
>Hoewel niet identiek, heeft het toevoegen van componenten en activa aan een malplaatje vele gelijkenissen aan gelijkaardige acties wanneer het [paginaontwerp](/help/sites-cloud/authoring/fundamentals/editing-content.md).

#### Componenthandelingen {#component-actions}

Voer acties uit op de componenten nadat deze aan de sjabloon zijn toegevoegd. Elk afzonderlijk exemplaar heeft een toolbar die u toestaat om tot de beschikbare acties toegang te hebben, is de toolbar afhankelijk van het componenttype.

![Werkbalk van een sjablooncomponent](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Het kan ook afhankelijk zijn van acties zoals wanneer een beleid met de component is geassocieerd, dan wordt het pictogram van de ontwerpconfiguratie beschikbaar.

#### Bewerken en configureren {#edit-and-configure}

Met deze twee acties kunt u inhoud toevoegen aan uw componenten.

#### Rand om structuur aan te geven {#border-to-indicate-structure}

Als u in de **structuurmodus** werkt, wordt een oranje rand weergegeven die aangeeft welke component momenteel is geselecteerd. Een stippellijn geeft ook de bovenliggende component aan.

#### Beleid en eigenschappen (algemeen) {#policy-and-properties-general}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Maak een inhoudsbeleid of selecteer een bestaand beleid voor een component.

![Knop Inhoudsbeleid](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Zo kunt u de ontwerpdetails definiëren.

![Inhoudsbeleid](/help/sites-cloud/authoring/assets/template-content-policy.png)

Het configuratievenster is verdeeld in twee.

* In de linkerkant van de dialoog onder **Beleid**, hebt u de capaciteit om een bestaand beleid te selecteren of bestaande te selecteren.
* In de rechterkant van het dialoogvenster onder **Eigenschappen** kunt u de eigenschappen instellen die specifiek zijn voor het componenttype.

De beschikbare eigenschappen zijn afhankelijk van de geselecteerde component. Voor een tekstcomponent definiëren de eigenschappen bijvoorbeeld de kopieer- en plakopties, opmaakopties en alineastijl.

##### Beleid {#policy}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Onder **Beleid** kunt u een bestaand beleid selecteren om op de component via drop-down van toepassing te zijn.

![Beleid selecteren](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

U kunt een nieuw beleid toevoegen door de knop Toevoegen naast de vervolgkeuzelijst **Beleid** selecteren te selecteren. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** .

![Beleidsknop toevoegen](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

Het geselecteerde bestaande beleid in het **Uitgezochte beleidsdrop** kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast dropdown. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** . Standaard krijgt het gekopieerde beleid de naam **Kopie van X**, waarbij X de titel van het gekopieerde beleid is.

![De knop Beleid kopiëren](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Een beschrijving van het beleid is optioneel in het veld **Beleidsbeschrijving** .

In de **Andere malplaatjes die ook de geselecteerde beleidssectie** gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken dat in **Uitgezochte beleidsdrop** wordt geselecteerd.

![Gebruik van bestaand beleid](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Als meerdere componenten van hetzelfde type als initiële inhoud worden toegevoegd, geldt hetzelfde beleid voor alle componenten.

##### Eigenschappen {#properties}

In de kop **Eigenschappen** kunt u de instellingen van de component definiëren. De kop heeft twee tabbladen:

* Hoofd
* Functies

###### Hoofd {#main}

Op het tabblad **Main** worden de belangrijkste instellingen van de component gedefinieerd.

Voor een afbeeldingscomponent kunnen bijvoorbeeld de toegestane breedten worden gedefinieerd en kan het laden worden ingeschakeld.

Als een instelling meerdere configuraties toestaat, klikt of tikt u op de knop **Toevoegen** om nog een configuratie toe te voegen.

![Knop Toevoegen](/help/sites-cloud/authoring/assets/templates-add-button.png)

Als u een configuratie wilt verwijderen, klikt of tikt u op de knop **Verwijderen** rechts van de configuratie.

Als u een configuratie wilt verwijderen, klikt of tikt u op de knop **Verwijderen** .

![Knop Verwijderen](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Features {#features}

Op het tabblad **Functies** kunt u extra functies van de component in- of uitschakelen.

Voor een afbeeldingscomponent kunt u bijvoorbeeld de uitsnijdverhoudingen, de toegestane afbeeldingsoriëntaties en de vraag of uploads zijn toegestaan, definiëren.

![Tabblad Functies](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>In AEM worden uitsnijdverhoudingen gedefinieerd als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. Gebruikers die pagina&#39;s schrijven, zullen zich niet bewust zijn van enig verschil op voorwaarde dat u de **naam** duidelijk definieert aangezien dit is wat wordt weergegeven in de gebruikersinterface.

>[!NOTE]
>
>Het beleid van de inhoud voor componenten die de rijke tekstredacteur uitvoeren kan slechts voor opties worden bepaald die door RTE door zijn montages UI ter beschikking worden gesteld. <!--[Content policies for components implementing the rich text editor](/help/sites-administering/rich-text-editor.md#main-pars-header-206036638) can only be defined for options made available by the RTE through its UI settings.-->

#### Beleid en eigenschappen (container voor layout) {#policy-and-properties-layout-container}

Het beleid en de eigenschappen van een lay-outcontainer zijn gelijkaardig aan het algemene gebruik, maar met sommige verschillen.

>[!NOTE]
>
>Het vormen van een beleid is verplicht voor containercomponenten aangezien het u toelaat om componenten te bepalen die in de container beschikbaar zullen zijn.

Het configuratievenster wordt verdeeld in twee delen, enkel zoals in het algemene gebruik van het venster.

##### Beleid {#policy-layout}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Onder **Beleid** kunt u een bestaand beleid selecteren om op de component via drop-down van toepassing te zijn. Deze functie werkt net als bij het algemene gebruik van het venster.

##### Eigenschappen {#properties-layout}

In de kop **Eigenschappen** kunt u kiezen welke componenten beschikbaar zijn voor de lay-outcontainer en de instellingen definiëren. De kop heeft drie tabbladen:

* Toegestane componenten
* Standaardcomponenten
* Instellingen voor responsie

###### Toegestane componenten {#allowed-components}

Op het tabblad **Toegestane componenten** definieert u welke componenten beschikbaar zijn voor de lay-outcontainer.

* De componenten worden gegroepeerd op hun componentgroepen, die kunnen worden uitgevouwen en samengevouwen.
* U kunt een hele groep selecteren door de naam van de groep te controleren. U kunt de selectie van alle groepen ongedaan maken door de selectie uit te schakelen.
* Een min vertegenwoordigt minstens één maar niet alle punten in een groep worden geselecteerd.
* Er is een zoekopdracht beschikbaar om naar een component op naam te filteren.
* De tellingen die rechts van de naam van de componentengroep worden vermeld vertegenwoordigen het totale aantal geselecteerde componenten in die groepen ongeacht de filter.

![Tabblad Toegestane componenten](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Standaardcomponenten {#default-components}

Op het tabblad **Standaardcomponenten** definieert u welke componenten automatisch aan bepaalde mediatypen worden gekoppeld, zodat AEM weet met welke component deze worden gekoppeld wanneer een auteur een element van de elementenbrowser sleept. Merk op dat slechts de componenten met dalingsstreken voor dergelijke configuratie beschikbaar zijn.

Klik of tik **Toewijzing** toevoegen om een geheel nieuwe component en MIME typetoewijzing toe te voegen.

Selecteer een component in de lijst en klik of tik op **Type toevoegen** om een extra MIME-type toe te voegen aan een reeds toegewezen component. Klik op het pictogram **Verwijderen** om een MIME-type te verwijderen.

![Standaardcomponenten, tabblad](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Instellingen voor responsie {#responsive-settings}

Op het tabblad **Responsieve instellingen** kunt u het aantal kolommen in het resulterende raster van de layoutcontainer configureren.

#### Componenten ontgrendelen en vergrendelen {#unlock-and-lock-components}

U ontgrendelt/vergrendelt componenten om te bepalen of de inhoud beschikbaar is voor wijziging in de modus **Oorspronkelijke inhoud** .

Wanneer een component is ontgrendeld:

* Een open hangslotindicator wordt getoond in de grens.
* De componentwerkbalk wordt dienovereenkomstig aangepast.
* Alle inhoud die al is ingevoerd, wordt niet meer weergegeven in de **structuurmodus** .
   * Al ingevoerde inhoud wordt beschouwd als eerste inhoud en is alleen zichtbaar in de modus **Oorspronkelijke inhoud** .
* De bovenliggende elementen van de ontgrendelde component kunnen niet worden verplaatst, geknipt of verwijderd.

![Component-knop vergrendelen](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Dit omvat het ontgrendelen van containercomponenten zodat andere componenten kunnen worden toegevoegd, in de modus **Initiële content** of op de resulterende pagina&#39;s. Als u al componenten/content aan de container hebt toegevoegd voordat u de container ontgrendelt, worden deze niet meer weergegeven in de modus **Structuur**, maar in de modus **Initiële content**. In de **modus Structuur** wordt alleen de containercomponent zelf weergegeven met de lijst **Toegestane componenten**.

![Toegestane componenten](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Om ruimte te besparen, groeit de lay-outcontainer niet om de lijst van toegestane componenten aan te passen. In plaats daarvan wordt de container een schuifbare lijst.

De componenten die configureerbaar zijn, worden weergegeven met een pictogram **Beleid**, waarop kan worden getikt of geklikt om het beleid en de eigenschappen van die component te bewerken.

![Pictogram Configureerbare component](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Verhouding tot bestaande pagina&#39;s {#relationship-to-existing-pages}

Als de structuur na het maken van op de sjabloon gebaseerde pagina&#39;s wordt bijgewerkt, worden de wijzigingen in de sjabloon doorgevoerd in deze pagina&#39;s. Er wordt een waarschuwing weergegeven op de werkbalk om u hieraan te herinneren, samen met bevestigingsdialoogvensters.

![Banner die waarschuwt dat de sjabloon in gebruik is](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Een sjabloon bewerken - Eerste inhoud - Auteur {#editing-a-template-initial-content-author}

**De modus Eerste inhoud** wordt gebruikt voor gedefinieerde inhoud die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon. De eerste inhoud kan vervolgens door auteurs van pagina&#39;s worden bewerkt.

Hoewel alle content die in de modus **Structuur** is gemaakt, zichtbaar is in **Initiële content**, kunnen alleen de ontgrendelde componenten worden geselecteerd en bewerkt.

>[!NOTE]
>
>**De modus Oorspronkelijke inhoud** kan worden gebruikt als bewerkingsmodus voor pagina&#39;s die met die sjabloon zijn gemaakt. Het beleid wordt daarom niet gedefinieerd in de modus **Oorspronkelijke inhoud** , maar in de modus [**Structuur **](#editing-a-template-structure-template-author).

* Ontgrendelde componenten die beschikbaar zijn voor bewerking, worden gemarkeerd. Als deze optie is geselecteerd, hebben ze een blauwe rand:

   ![Modus Eerste inhoud](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png)

* Ontgrendelde componenten beschikken over een werkbalk waarmee u de inhoud kunt bewerken en configureren:

   ![Ontgrendelde component](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Als een containercomponent is ontgrendeld (in de modus **Structuur**), kunt u nieuwe componenten aan de container toevoegen (in de modus **Initiële content**). Componenten die in de modus **Initiële content** zijn toegevoegd, kunnen worden verplaatst naar of verwijderd uit de resulterende pagina&#39;s.

   U kunt een component toevoegen met behulp van het gebied **Componenten hierheen slepen** of de optie **Nieuwe component invoegen** op de werkbalk van de betreffende container.

   ![Component toevoegen](/help/sites-cloud/authoring/assets/templates-add-component.png)
   ![Component toevoegen](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png)

* Als de initiële inhoud van de sjabloon wordt bijgewerkt nadat pagina&#39;s zijn gemaakt op basis van de sjabloon, worden deze pagina&#39;s niet beïnvloed door wijzigingen in de oorspronkelijke inhoud van de sjabloon.

>[!NOTE]
>
>De eerste inhoud is bedoeld voor het voorbereiden van componenten en de paginalay-out die als uitgangspunt dienen voor het maken van de inhoud. Het is niet de bedoeling om de inhoud te zijn die ongewijzigd blijft. Daarom kan de initiële inhoud niet worden vertaald.
>
>Als u vertaalbare tekst in uw sjabloon wilt opnemen, bijvoorbeeld in kop- of voetteksten, kunt u de [lokalisatiefuncties van de kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/get-started/localization.html)gebruiken.

### Een sjabloon bewerken - Layout - Sjabloonauteur {#editing-a-template-layout-template-author}

U kunt de sjabloonlay-out voor een reeks apparaten definiëren. [De responsieve indeling](/help/sites-cloud/authoring/features/responsive-layout.md) voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

>[!NOTE]
>
>Wijzigingen in de lay-out worden weerspiegeld in de modus **Oorspronkelijke inhoud** , maar in de modus **Structuur** zijn geen wijzigingen zichtbaar.

![Sjabloonindeling bewerken](/help/sites-cloud/authoring/assets/templates-edit-layout.png)

### Een sjabloon bewerken - Paginabeleid - Sjabloonauteur/ontwikkelaar {#editing-a-template-page-policy-template-author-developer}

Het paginabeleid, inclusief de vereiste clientbibliotheken, blijft behouden onder de optie **Paginabeleid** van het menu **Pagina-informatie**.

Het dialoogvenster **Paginabeleid** openen:

1. Selecteer in de **Sjablooneditor** de optie **Pagina-informatie** op de werkbalk en vervolgens **Paginabeleid** om het dialoogvenster te openen.
1. Het dialoogvenster **Paginabeleid** wordt geopend en bestaat uit twee gedeelten:

   * De linkerhelft definieert het [paginabeleid](#page-policies)
   * De rechterhelft definieert de [pagina-eigenschappen](#page-properties)
   ![Paginaontwerp](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Paginabeleid {#page-policies}

U kunt een inhoudsbeleid toepassen op de sjabloon of de resulterende pagina&#39;s. Hiermee wordt het inhoudsbeleid voor het hoofdalineasysteem op de pagina gedefinieerd.

![Paginabeleid](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* U kunt een bestaand beleid voor de pagina selecteren in de vervolgkeuzelijst **Beleid** selecteren.

   ![Beleidskiezer](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

   U kunt een nieuw beleid toevoegen door de knop Toevoegen naast de vervolgkeuzelijst **Beleid** selecteren te selecteren. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** .

   ![Beleidsknop toevoegen](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

   Het geselecteerde bestaande beleid in het **Uitgezochte beleidsdrop** kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast dropdown. Vervolgens moet een nieuwe titel worden gegeven in het veld **Beleidstitel** . Standaard krijgt het gekopieerde beleid de naam **Kopie van X**, waarbij X de titel van het gekopieerde beleid is.

   ![De knop Beleid kopiëren](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Definieer een titel voor het beleid in het veld **Beleidstitel** . Een beleid is vereist om een titel te hebben zodat het gemakkelijk in het **Uitgezochte beleidsdrop** kan worden geselecteerd.

   ![Beleidstitel](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Een beschrijving van het beleid is optioneel in het veld **Beleidsbeschrijving** .
* In de **Andere malplaatjes die ook de geselecteerde beleidssectie** gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken dat in **Uitgezochte beleidsdrop** wordt geselecteerd.

   ![Beleidsgebruik](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Pagina-eigenschappen {#page-properties}

Met pagina-eigenschappen kunt u de vereiste clientbibliotheken definiëren in het dialoogvenster **Paginaontwerp** . Deze client-side bibliotheken bevatten stijlpagina&#39;s en javascript die met de sjabloon moeten worden geladen en pagina&#39;s die met die sjabloon zijn gemaakt.

![Pagina-eigenschappen](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Geef de clientbibliotheken op die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt. De naam van een bibliotheek invoeren in het tekstveld in de sectie **Clientzijbibliotheken** .

   ![Bibliotheken op de client](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Als er meerdere bibliotheken nodig zijn, klikt u op de knop Toevoegen om een extra tekstveld voor de naam van de bibliotheek toe te voegen.

   ![Knop Toevoegen](/help/sites-cloud/authoring/assets/templates-add-button.png)

   Voeg zoveel tekstvelden toe als nodig zijn voor uw clientbibliotheken.

* Definieer zo nodig de relatieve positie van de bibliotheken door de velden te slepen met de sleepgreep.

   ![Sleepgreep](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Terwijl de sjabloonauteur het paginabeleid voor de sjabloon kan opgeven, moet hij of zij details van de desbetreffende client-side bibliotheken ophalen van de ontwikkelaar.

### Een sjabloon bewerken - Initiële pagina-eigenschappen - Auteur {#editing-a-template-initial-page-properties-author}

Met de optie Eigenschappen **van** eerste pagina kunt u de eerste [pagina-eigenschappen](/help/sites-cloud/authoring/fundamentals/page-properties.md) definiëren die moeten worden gebruikt bij het maken van resulterende pagina&#39;s.

1. Selecteer in de sjablooneditor de optie **Pagina-informatie** op de werkbalk en kies vervolgens **Pagina-eigenschappen** bij openen om het dialoogvenster te openen.

1. In het dialoogvenster kunt u de eigenschappen definiëren die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt.

   ![Sjablonen, eigenschappen voor eerste pagina](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Bevestig uw definities met **Gedaan**.

## Best Practices {#best-practices}

Houd bij het maken van sjablonen rekening met:

1. Het effect van wijzigingen in de sjabloon wanneer pagina&#39;s zijn gemaakt op basis van die sjabloon.

   Hier volgt een lijst met de verschillende bewerkingen die mogelijk zijn op sjablonen, samen met de manier waarop deze van invloed zijn op de pagina&#39;s die er vanaf worden gemaakt:

   * Wijzigingen in de structuur:

      * Deze worden direct toegepast op de resulterende pagina&#39;s.
      * Bezoekers moeten de wijzigingen nog steeds kunnen zien door de gewijzigde sjabloon te publiceren.
   * Wijzigingen in inhoudsbeleid en ontwerpconfiguraties:

      * Deze zijn direct van toepassing op de resulterende pagina&#39;s.
      * De wijzigingen moeten worden gepubliceerd zodat bezoekers de wijzigingen kunnen zien.
   * Wijzigingen in de oorspronkelijke inhoud:

      * Deze zijn alleen van toepassing op pagina&#39;s die na de wijzigingen in de sjabloon worden gemaakt.
   * Wijzigingen in de layout zijn afhankelijk van of de gewijzigde component deel uitmaakt van:

      * Alleen structuur - onmiddellijk toegepast
      * Bevat initiële inhoud - alleen op pagina&#39;s die na de wijziging zijn gemaakt
   Wees extra voorzichtig als:

   * Componenten op ingeschakelde sjablonen vergrendelen of ontgrendelen.
   * Dit kan bijwerkingen hebben, aangezien bestaande pagina&#39;s het reeds kunnen gebruiken. Doorgaans:

      * Ontgrendelingscomponenten (die vergrendeld waren) ontbreken op bestaande pagina&#39;s.
      * Door componenten te vergrendelen (die bewerkbaar waren) wordt die inhoud niet op de pagina&#39;s weergegeven.
   >[!NOTE]
   >
   >AEM geeft expliciete waarschuwingen wanneer het veranderen van de slotstatus van componenten op malplaatjes die niet meer concepten zijn.

1. [Uw eigen mappen](#creating-a-template-folder-admin) maken voor uw sitespecifieke sjablonen.
1. [Publiceer uw malplaatjes](#publishing-a-template-template-author) van de console van **Malplaatjes** .
