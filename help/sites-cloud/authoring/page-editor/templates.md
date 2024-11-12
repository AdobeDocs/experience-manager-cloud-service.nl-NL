---
title: Sjablonen om pagina's te maken die kunnen worden bewerkt met de Pagina-editor
description: U kunt de Redacteur van het Malplaatje gebruiken om malplaatjes tot stand te brengen die uw inhoudsauteurs kunnen gebruiken om pagina's tot stand te brengen die met de Redacteur van de Pagina editable zijn.
exl-id: 4c9dbf26-5852-45ab-b521-9f051c153b2e
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 41abdfcf142a3f39854978c5acf0e5d28872b3c4
workflow-type: tm+mt
source-wordcount: '4415'
ht-degree: 5%

---


# Sjablonen om pagina&#39;s te maken die kunnen worden bewerkt met de Pagina-editor {#creating-page-templates}

U kunt de Redacteur van het Malplaatje gebruiken om malplaatjes tot stand te brengen die uw inhoudsauteurs kunnen gebruiken om pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina editable zijn.

## Overzicht {#overview}

Wanneer een auteur een pagina maakt, moet hij of zij een sjabloon selecteren dat als basis voor de nieuwe pagina wordt gebruikt. De sjabloon definieert de structuur van de resulterende pagina, eventuele eerste inhoud en de componenten die kunnen worden gebruikt bij het bewerken van de pagina in de Pagina-editor.

>[!NOTE]
>
>[ de Malplaatjes zijn ook beschikbaar voor het creëren van pagina&#39;s die met de Universele Redacteur editable zijn.](/help/sites-cloud/authoring/universal-editor/templates.md)

Met de **Redacteur van het Malplaatje**, creërend en het handhaven van malplaatjes is geen ontwikkelaar-enige taak. Een type van macht-gebruiker, die a **malplaatjeauteur** wordt genoemd, kan malplaatjes tot stand brengen. De ontwikkelaars worden vereist om het milieu te plaatsen, cliëntbibliotheken te creëren, en de te gebruiken componenten tot stand te brengen, maar zodra deze grondbeginselen op zijn plaats zijn heeft de **malplaatjeauteur** de flexibiliteit om malplaatjes tot stand te brengen en te vormen zonder een ontwikkelaar te impliceren.

De **Redacteur van het Malplaatje** staat malplaatjeauteurs toe om:

* Voeg componenten aan het malplaatje toe en plaats hen op een ontvankelijk net.
* Configureer de componenten vooraf.
* Bepaal welke componenten op pagina&#39;s kunnen worden uitgegeven die met het malplaatje worden gecreeerd.

Dit document verklaart hoe de auteur van het a **malplaatje** de **Redacteur van het Malplaatje** kan gebruiken om editable malplaatjes tot stand te brengen en te beheren.

Voor gedetailleerde informatie over hoe editable malplaatjes op een technisch niveau werken, zie het ontwikkelaarsdocument [ Bewerkbare Malplaatjes ](/help/implementing/developing/components/templates.md) voor meer informatie.

>[!NOTE]
>
>De **sjablooneditor** biedt geen ondersteuning voor rechtstreekse targeting op het sjabloonniveau. Pagina&#39;s die zijn gemaakt op basis van een bewerkbare sjabloon kunnen worden geactiveerd, maar de sjablonen zelf kunnen dat niet.

## Voordat u begint {#before-you-start}

Voordat u begint, is het belangrijk om te bedenken dat voor het maken van een sjabloon samenwerking vereist is. Om deze reden wordt de [ Rol ](#roles) vermeld voor elke taak. Dit heeft geen invloed op de manier waarop u een sjabloon gebruikt om een pagina te maken, maar het heeft wel invloed op de manier waarop een pagina betrekking heeft op de sjabloon.

>[!NOTE]
>
>Een beheerder moet een malplaatjeomslag in **Browser van Configuraties** vormen en juiste toestemmingen toepassen alvorens een malplaatjeauteur een malplaatje in die omslag kan tot stand brengen.

### Rollen {#roles}

Voor het maken van een nieuwe sjabloon is samenwerking tussen de volgende rollen vereist:

* **Admin**:
   * Voor het maken van een nieuwe map met sjablonen zijn `admin` -rechten vereist.
   * Dergelijke taken kunnen vaak ook door een ontwikkelaar worden uitgevoerd
* **Ontwikkelaar**:
   * Concentraties op de technische/interne details
   * Heeft ervaring nodig met de ontwikkelomgeving.
   * Verstrekt de malplaatjeauteur van noodzakelijke informatie.
* **Auteur van het Malplaatje**:
   * Dit is een specifieke auteur die lid is van de groep `template-authors`
      * Hiermee worden de vereiste rechten en machtigingen toegewezen.
   * Kan het gebruik van componenten en andere details op hoog niveau configureren die het volgende vereisen:
      * Enkele technische kennis
         * Gebruik bijvoorbeeld patronen bij het definiëren van paden.
      * Technische informatie van de ontwikkelaar.

Vanwege de aard van sommige taken, zoals het maken van een map, is een ontwikkelomgeving nodig. Hiervoor is kennis en ervaring vereist.

De in dit document beschreven taken worden weergegeven met de rol die verantwoordelijk is voor de uitvoering ervan.

## Sjablonen maken en beheren {#creating-and-managing-templates}

Bij het maken van een bewerkbare sjabloon:

* [ creeer een nieuw malplaatje ](#creating-a-new-template-template-author), dat aanvankelijk leeg zal zijn
* [ bepaal extra eigenschappen ](#defining-template-properties-template-author) voor het malplaatje indien nodig
* [ geef het malplaatje ](#editing-templates-template-authors) uit om te bepalen:
   * [ Structuur ](#editing-a-template-structure-template-author) - vooraf bepaalde inhoud die niet op pagina&#39;s kan worden veranderd die met het malplaatje worden gecreeerd.
   * [ Aanvankelijke Inhoud ](#editing-a-template-initial-content-author) - vooraf bepaalde inhoud die op pagina&#39;s kan worden veranderd die met het malplaatje worden gecreeerd.
   * [ Lay-out ](#editing-a-template-layout-template-author) - voor een waaier van apparaten.
   * [ Stijlen ](/help/sites-cloud/authoring/page-editor/style-system.md) - bepaal de stijlen die met het malplaatje en zijn componenten moeten worden gebruikt.
* [ laat het malplaatje ](#enabling-a-template-template-author) voor gebruik toe wanneer het creëren van een pagina
* [ sta het malplaatje ](#allowing-a-template-author) voor de vereiste pagina of tak van uw website toe
* [ Publish het malplaatje ](#publishing-a-template-template-author) om het op te stellen publiceert milieu

>[!NOTE]
>
>**Toegestane Malplaatjes** zijn vaak vooraf bepaald wanneer uw website aanvankelijk opstelling is.

>[!TIP]
>
>Ga nooit om het even welke informatie in die [ ](/help/implementing/developing/extending/i18n/dev.md) in een malplaatje moet worden geinternationaliseerd.
>
>Voor malplaatjeelementen zoals kopballen en footers die moeten worden gelokaliseerd, gebruik de [ localisatieeigenschappen van de kerncomponenten.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html)

### Sjabloonmap maken - Beheer {#creating-a-template-folder-admin}

Een malplaatjeomslag zou voor uw project moeten worden gecreeerd om uw project-specifieke malplaatjes te houden. Dit is een admin taak en in het document [ Malplaatjes van de Pagina ](/help/implementing/developing/components/templates.md#template-folders) beschreven.

### Een nieuwe sjabloon maken - Sjabloonauteur {#creating-a-new-template-template-author}

1. Open de **[Console van Malplaatjes](/help/sites-cloud/administering/templates-console.md)** dan navigeer aan de vereiste omslag.

   >[!NOTE]
   >
   >In een standaard AEM instantie bestaat de **globale** omslag reeds in de malplaatjeconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden.
   >
   >Het wordt geadviseerd beste praktijken om a [ malplaatjeomslag te gebruiken die voor uw project ](/help/implementing/developing/components/templates.md#template-folders) wordt gecreeerd.

1. Selecteer **creëren**, die door **wordt gevolgd leidt Malplaatje** om de tovenaar te openen.

1. Kies het Type van a **Malplaatje**, dan selecteer **daarna**.

   >[!NOTE]
   >
   >Sjabloontypen zijn vooraf gedefinieerde sjabloonlay-outs en kunnen worden beschouwd als sjablonen voor een sjabloon. Deze worden vooraf bepaald door ontwikkelaars of de systeembeheerder. Meer informatie kan in het ontwikkelaardocument [ Malplaatjes van de Pagina ](/help/implementing/developing/components/templates.md#template-type) worden gevonden.—>

1. Voltooi de **Details van het Malplaatje**:

   * **Naam van het Malplaatje**
   * **Beschrijving**

1. Selecteer **Maken**. Een bevestiging wordt getoond, selecteert **Open** beginnen het malplaatje uit te geven of **Gedaan** om aan de malplaatjeconsole terug te keren.

   >[!NOTE]
   >
   >Wanneer een nieuw malplaatje wordt gecreeerd is het duidelijk als **Ontwerp** in de console, wijst dit erop dat het nog niet beschikbaar aan gebruik door paginaauteurs is.

>[!TIP]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe raadt niet aan meer dan 1000 sjablonen te hebben vanwege mogelijke gevolgen voor de prestaties.

### Sjablooneigenschappen definiëren - Sjabloonauteur {#defining-template-properties-template-author}

Een sjabloon kan de volgende eigenschappen hebben:

* Afbeelding
   * Beeld dat als a [ duimnagel van het malplaatje ](#template-thumbnail-image) moet worden gebruikt om selectie zoals in de Create tovenaar van de Pagina te helpen.
      * Kan uploaden
      * Kan worden gegenereerd op basis van de sjablooninhoud
* Titel
   * Een titel die voor het identificeren van het malplaatje zoals in **wordt gebruikt leidt tot de tovenaar van de Pagina**.
* Beschrijving
   * Een facultatieve beschrijving om meer informatie over het malplaatje en zijn gebruik te verstrekken, dat bijvoorbeeld, in **kan worden gezien leidt tot de tovenaar van de Pagina**.

Na het creëren van het malplaatje, gebruik de **[Console van Malplaatjes](/help/sites-cloud/administering/templates-console.md)** om de malplaatjeeigenschappen te bekijken of uit te geven.

#### Miniatuurafbeelding sjabloon {#template-thumbnail-image}

De sjabloonminiatuur definiëren:

1. Bewerk de sjablooneigenschappen.
1. Kies of u een miniatuur wilt uploaden of wilt dat deze wordt gegenereerd op basis van de sjablooninhoud.
   * Als u een duimnagel wilt uploaden, uitgezochte **Upload Beeld**
   * Als u een duimnagel wilt produceren, **produceer Voorproef**
1. Voor beide methoden wordt een voorbeeld van de miniatuur weergegeven.
   * Als het niet bevredigend is, uitgezochte **Duidelijk** om een ander beeld te uploaden of de duimnagel opnieuw te produceren.
1. Wanneer u met de duimnagel wordt tevreden, uitgezocht **sparen &amp; sluit**.

### Een sjabloon inschakelen en toestaan - Sjabloonauteur {#enabling-and-allowing-a-template-template-author}

Als u een sjabloon wilt kunnen gebruiken bij het maken van een pagina, moet u:

* [ laat het malplaatje ](#enabling-a-template-template-author) toe om het voor gebruik beschikbaar te maken wanneer het creëren van pagina&#39;s.
* [ sta het malplaatje ](#allowing-a-template-author) toe om de inhoudtakken te specificeren waar het malplaatje kan worden gebruikt.

#### Sjabloon inschakelen - Sjabloonauteur {#enabling-a-template-template-author}

Een malplaatje kan worden toegelaten of worden onbruikbaar gemaakt om het beschikbaar of niet beschikbaar te maken in **creëren de tovenaar van de Pagina**.

Gebruik de **[Console van Malplaatjes](/help/sites-cloud/administering/templates-console.md)** om een malplaatje toe te laten of onbruikbaar te maken.

>[!CAUTION]
>
>Nadat een sjabloon is ingeschakeld, wordt een waarschuwing weergegeven wanneer een sjabloonauteur de sjabloon verder gaat bijwerken. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

#### Een sjabloon toestaan - Auteur {#allowing-a-template-author}

Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

1. Open de [ Eigenschappen van de Pagina ](/help/sites-cloud/authoring/sites-console/page-properties.md) voor de wortelpagina van de tak waar u het malplaatje beschikbaar wilt zijn.
1. Open het **Geavanceerde** lusje.
1. Gebruik onder **Sjablooninstellingen** de optie **Veld toevoegen** om het pad of de paden naar de sjabloon of sjablonen op te geven.

   Het pad kan expliciet zijn of patronen gebruiken. Bijvoorbeeld:

   `/conf/<your-folder>/settings/wcm/templates/.*`

   De volgorde van de paden is irrelevant. Alle paden worden gescand en sjablonen worden opgehaald.

   >[!NOTE]
   >
   >Als de **Toegestane lijst van Malplaatjes** leeg wordt verlaten, dan wordt de boom gevergd tot een waarde/lijst wordt gevonden.
   >
   >Zie [ Beschikbaarheid van het Malplaatje ](/help/implementing/developing/components/templates.md#template-availability) - de principes voor toegestane malplaatjes blijven het zelfde.

1. Klik **sparen** om de veranderingen in de paginaeigenschappen te bewaren.

>[!NOTE]
>
>Vaak zijn de toegestane sjablonen vooraf gedefinieerd voor uw gehele site wanneer deze wordt ingesteld.

### Een sjabloon publiceren - Sjabloonauteur {#publishing-a-template-template-author}

Aangezien het malplaatje van verwijzingen wordt voorzien wanneer een pagina wordt teruggegeven, moet het volledig gevormde malplaatje worden gepubliceerd zodat het op het publicatiemilieu beschikbaar is.

Publish malplaatjes die de **[Console van Malplaatjes gebruiken.](/help/sites-cloud/administering/templates-console.md)**

## Sjablonen bewerken - Sjabloonauteurs {#editing-templates-template-authors}

Bij het maken of bewerken van een sjabloon zijn er verschillende aspecten die u kunt definiëren. Sjablonen bewerken is vergelijkbaar met het ontwerpen van pagina&#39;s.

De **selecteur van de Wijze** in de toolbar laat u het aangewezen aspect van het malplaatje selecteren en uitgeven:

* [Structuur](#editing-a-template-structure-template-author)
* [Oorspronkelijke inhoud](#editing-a-template-initial-content-author)
* [Layout](#editing-a-template-layout-template-author)

![ de redacteurswijze van het Malplaatje selecteur ](/help/sites-cloud/authoring/assets/templates-mode.png)

Terwijl de **optie van het Beleid van de Pagina** op het **menu van de Informatie van de Pagina** u [ het vereiste paginabeleid ](#page-policies) laat selecteren:

![ de Informatie van de Pagina van de Redacteur van het Malplaatje ](/help/sites-cloud/authoring/assets/templates-page-information.png)

>[!CAUTION]
>
>Als een auteur een sjabloon gaat bewerken die al is ingeschakeld, wordt een waarschuwing weergegeven. Dit moet de gebruiker informeren dat naar de sjabloon kan worden verwezen, zodat wijzigingen van invloed kunnen zijn op de pagina&#39;s die naar de sjabloon verwijzen.

### Sjabloonkenmerken {#template-attributes}

De volgende kenmerken van een sjabloon kunnen worden bewerkt:

#### Structuur {#template-structure}

De componenten die aan de [ structuur ](#editing-a-template-structure-template-author) worden toegevoegd kunnen niet worden bewogen/van resulterende pagina&#39;s door de paginaauteurs worden verwijderd. Als u wilt dat auteurs van pagina&#39;s componenten aan resulterende pagina&#39;s kunnen toevoegen en verwijderen, dan moet u een paragraafsysteem aan het malplaatje toevoegen.

Wanneer componenten zijn vergrendeld, kunt u inhoud toevoegen die niet kan worden bewerkt door auteurs van pagina&#39;s. U kunt componenten ontgrendelen om u toe te staan om [ Aanvankelijke Inhoud ](#editing-a-template-initial-content-author) te bepalen.

>[!NOTE]
>
>In de structuurmodus kunnen componenten die het bovenliggende element van een niet-vergrendelde component zijn, niet worden verplaatst, geknipt of verwijderd.

#### Oorspronkelijke inhoud {#template-initial-content}

Wanneer een component is ontgrendeld kunt u de [ aanvankelijke inhoud ](#editing-a-template-initial-content-author) bepalen die aan de resulterende pagina(s) wordt gekopieerd, die van het malplaatje wordt gecreeerd. Deze niet-vergrendelde componenten kunnen op de resulterende pagina(&#39;s) worden bewerkt.

>[!NOTE]
>
>Op **Aanvankelijke wijze van de Inhoud** en op de resulterende pagina&#39;s, kunnen om het even welke ontgrendelde componenten die een toegankelijke ouder (namelijk componenten binnen een lay-outcontainer) hebben worden geschrapt.

#### Layout {#template-layout}

Met de [lay-out](#editing-a-template-layout-template-author) kunt u de sjabloonlay-out voor de vereiste apparaatindelingen vooraf bepalen. De modus **Lay-out** voor het ontwerpen van sjablonen heeft dezelfde functionaliteit als de modus [**Lay-out** voor het ontwerpen van pagina&#39;s](/help/sites-cloud/authoring/page-editor/responsive-layout.md#defining-layouts-layout-mode).

#### Paginabeleid {#template-page-policies}

[ het beleid van de Pagina ](#page-policies) kan vooraf bepaald paginabeleid met de pagina verbinden. Met dit paginabeleid worden de verschillende ontwerpconfiguraties gedefinieerd.

#### Stijlen {#template-styles}

Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.

Gelieve te zien de [ documentatie van het Systeem van de Stijl ](/help/sites-cloud/authoring/page-editor/style-system.md) voor meer informatie.

### Een sjabloon bewerken - Structuur - Sjabloonauteur {#editing-a-template-structure-template-author}

Op **wijze van de Structuur** bepaalt u componenten en inhoud voor uw malplaatje en bepaalt beleid voor het malplaatje en zijn componenten.

* Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.
* Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
* De componenten kunnen opnieuw worden ontgrendeld en worden gesloten om u toe te staan om [ aanvankelijke inhoud ](#editing-a-template-initial-content-author) te bepalen.
* Het ontwerpbeleid voor de componenten en pagina wordt gedefinieerd.

![ de paginastructuur van de Redacteur van het Malplaatje ](/help/sites-cloud/authoring/assets/templates-page-structure.png)

Er zijn verscheidene acties u op de **wijze van de Structuur** van de malplaatjeredacteur en verscheidene eigenschappen kunt nemen om u bij te staan:

#### Componenten toevoegen {#add-components}

Er zijn verschillende manieren om componenten aan de sjabloon toe te voegen:

* Van **Componenten** browser in het zijpaneel.
* Met de optie **Component invoegen** op de werkbalk kunt u componenten gebruiken die zich al in de sjabloon bevinden of het vak **Componenten hierheen slepen**.
* Door activa (van **Assets** browser in het zijpaneel) direct op het malplaatje te slepen om de aangewezen component in plaats te produceren.

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
>Hoewel niet identiek, heeft het toevoegen van componenten en activa aan een malplaatje vele gelijkenissen aan gelijkaardige acties wanneer [ pagina creatie.](/help/sites-cloud/authoring/page-editor/edit-content.md)

#### Componenthandelingen {#component-actions}

Voer acties uit op de componenten nadat deze aan de sjabloon zijn toegevoegd. Elk afzonderlijk exemplaar heeft een toolbar die u tot de beschikbare acties toegang heeft, is de toolbar afhankelijk van het componenttype.

![ toolbar van de Actie van een malplaatjecomponent ](/help/sites-cloud/authoring/assets/templates-component-actions.png)

Het kan ook afhankelijk zijn van acties zoals wanneer een beleid met de component is geassocieerd, dan wordt het pictogram van de ontwerpconfiguratie beschikbaar.

#### Bewerken en configureren {#edit-and-configure}

Met deze twee acties kunt u inhoud toevoegen aan uw componenten.

#### Rand om structuur aan te geven {#border-to-indicate-structure}

Wanneer het werken op **de wijze van de Structuur** een oranje grens wijst op de component momenteel geselecteerd. Een stippellijn geeft ook de bovenliggende component aan.

#### Beleid en eigenschappen (algemeen) {#policy-and-properties-general}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Maak een inhoudsbeleid of selecteer een bestaand beleid voor een component.

![ knoop van het Beleid van de Inhoud ](/help/sites-cloud/authoring/assets/templates-content-policy-button.png)

Hiermee kunt u de ontwerpdetails definiëren.

![ Beleid van de Inhoud ](/help/sites-cloud/authoring/assets/template-content-policy.png)

Het configuratievenster is verdeeld in twee.

* In de linkerkant van de dialoog onder **Beleid**, kunt u een bestaand beleid selecteren of bestaande selecteren.
* In de rechterkant van de dialoog onder **Eigenschappen**, kunt u de eigenschappen plaatsen specifiek voor het componententype.

De beschikbare eigenschappen zijn afhankelijk van de geselecteerde component. Voor een tekstcomponent definiëren de eigenschappen bijvoorbeeld de kopieer- en plakopties, opmaakopties en alineastijl.

##### Beleid {#policy}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Onder **Beleid** kunt u een bestaand beleid selecteren om op de component als drop-down van toepassing te zijn.

![ Uitgezochte beleid ](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

Een nieuw beleid kan worden toegevoegd door toe te voegen knoop naast **Uitgezochte beleid** drop-down te selecteren. Geef een nieuwe titel op het **gebied van de Titel van het Beleid**.

![ voeg de knoop van het Beleid toe ](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

Het geselecteerde bestaande beleid in **Uitgezochte beleid** drop-down lijst kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast de drop-down lijst. Geef een nieuwe titel op het **gebied van de Titel van het Beleid**. Door gebrek wordt het gekopieerde beleid genoemd **Exemplaar van X**, waar X de titel van het gekopieerde beleid is.

![ knoop van het Beleid van het Exemplaar ](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

Een beschrijving van het beleid is facultatief op het **gebied van de Beschrijving van het Beleid**.

In de **Andere malplaatjes die ook de geselecteerde beleids** sectie gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken in de **Uitgezochte beleid** drop-down lijst wordt geselecteerd.

![ Gebruik van bestaand beleid ](/help/sites-cloud/authoring/assets/templates-policy-use.png)

>[!NOTE]
>
>Als meerdere componenten van hetzelfde type als initiële inhoud worden toegevoegd, geldt hetzelfde beleid voor alle componenten.

##### Eigenschappen {#properties}

Onder de **rubriek van Eigenschappen** kunt u de montages van de component bepalen. De kop heeft twee tabbladen:

* Hoofd
* Functies

###### Hoofd {#main}

Op het **Belangrijkste** lusje, worden de belangrijkste montages van de component bepaald.

Voor een afbeeldingscomponent kunnen bijvoorbeeld de toegestane breedten worden gedefinieerd en kan het laden worden ingeschakeld.

Als het plaatsen voor veelvoudige configuraties toestaat, selecteer **voeg** knoop toe om een andere configuratie toe te voegen.

![ voeg knoop ](/help/sites-cloud/authoring/assets/templates-add-button.png) toe

Om een configuratie te verwijderen, selecteer de **schrapping** knoop die aan het recht van de configuratie wordt gevestigd.

Om een configuratie te verwijderen, selecteer **Schrapping** knoop.

![ knoop van de Schrapping ](/help/sites-cloud/authoring/assets/templates-delete-button.png)

###### Functies {#features}

Het **lusje van Eigenschappen** laat u extra eigenschappen van de component toelaten of onbruikbaar maken.

Voor een afbeeldingscomponent kunt u bijvoorbeeld de uitsnijdverhoudingen, de toegestane afbeeldingsoriëntaties en de vraag of uploads zijn toegestaan, definiëren.

![ Eigenschappen tabel ](/help/sites-cloud/authoring/assets/templates-features-tab.png)

>[!CAUTION]
>
>In AEM gewassenverhoudingen worden bepaald als **hoogte/breedte**. Dit verschilt van de conventionele definitie van breedte/hoogte en wordt gedaan om oude compatibiliteitsredenen. De pagina auteursende gebruikers zullen zich niet van enig verschil bewust zijn die u de **Naam** duidelijk bepaalt aangezien dit is wat in UI wordt getoond.

>[!NOTE]
>
>[ het beleid van de Inhoud voor componenten die de rijke tekstredacteur ](/help/implementing/developing/extending/rich-text-editor.md) uitvoeren kan slechts voor opties worden bepaald die door RTE door zijn montages worden ter beschikking gesteld UI.

#### Beleid en eigenschappen (container voor layout) {#policy-and-properties-layout-container}

Het beleid en de eigenschappen van een lay-outcontainer zijn gelijkaardig aan het algemene gebruik, maar met sommige verschillen.

>[!NOTE]
>
>Het vormen van een beleid is verplicht voor containercomponenten aangezien het u toelaat om componenten te bepalen die in de container beschikbaar zijn.

Het configuratievenster wordt verdeeld in twee delen, enkel zoals in het algemene gebruik van het venster.

##### Beleid {#policy-layout}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

Onder **Beleid** kunt u een bestaand beleid selecteren om op de component via drop-down van toepassing te zijn. Deze functie werkt net als bij het algemene gebruik van het venster.

##### Eigenschappen {#properties-layout}

Onder de **rubriek van Eigenschappen** kunt u kiezen welke componenten voor de lay-outcontainer beschikbaar zijn en hun montages bepalen. De kop heeft drie tabbladen:

* Toegestane componenten
* Standaardcomponenten
* Instellingen voor responsie

###### Toegestane componenten {#allowed-components}

Op het **Toegestane lusje van Componenten**, bepaalt u welke componenten voor de lay-outcontainer beschikbaar zijn.

* De componenten worden gegroepeerd op hun componentgroepen, die kunnen worden uitgevouwen en samengevouwen.
* U kunt een hele groep selecteren door de naam van de groep te controleren. U kunt de selectie van alle groepen ongedaan maken door de selectie uit te schakelen.
* Een min vertegenwoordigt minstens één maar niet alle punten in een groep worden geselecteerd.
* Er is een zoekopdracht beschikbaar om naar een component op naam te filteren.
* De tellingen die rechts van de naam van de componentengroep worden vermeld vertegenwoordigen het totale aantal geselecteerde componenten in die groepen ongeacht de filter.

![ Toegestane Componenten tabel ](/help/sites-cloud/authoring/assets/templates-allowed-components-tab.png)

###### Standaardcomponenten {#default-components}

Op het **StandaardComponenten** lusje, bepaalt u welke componenten automatisch met bepaalde media types worden geassocieerd zodat wanneer een auteur activa van activabrowser sleept, AEM weet met welke component om het te associëren. Alleen componenten met dropzones zijn beschikbaar voor een dergelijke configuratie.

Selecteer **Toewijzing** toevoegen om een volledig nieuwe component en MIME typetoewijzing toe te voegen.

Selecteer een component in de lijst en selecteer **type** toevoegen om een extra type MIME aan een reeds in kaart gebrachte component toe te voegen. Klik op het pictogram **Verwijderen** om een MIME-type te verwijderen.

![ StandaardComponenten tabel ](/help/sites-cloud/authoring/assets/templates-default-components-tab.png)

###### Instellingen voor responsie {#responsive-settings}

Op het **Responsieve lusje van Montages** kunt u het aantal kolommen in het resulterende net van de lay-outcontainer vormen.

#### Componenten ontgrendelen en vergrendelen {#unlock-and-lock-components}

U ontgrendelt/sluit componenten om te bepalen of de inhoud voor verandering op **Aanvankelijke wijze van de Inhoud** beschikbaar is.

Wanneer een component is ontgrendeld:

* Een open hangslotindicator wordt getoond in de grens.
* De componentwerkbalk wordt dienovereenkomstig aangepast.
* Om het even welke reeds ingegane inhoud zal niet meer op **wijze van de Structuur** worden getoond.
   * Al ingegaan inhoud wordt beschouwd als aanvankelijke inhoud en is slechts zichtbaar op **Aanvankelijke wijze van de Inhoud**.
* De bovenliggende elementen van de ontgrendelde component kunnen niet worden verplaatst, geknipt of verwijderd.

![ de componentenknoop van het Slot ](/help/sites-cloud/authoring/assets/templates-unlock-component.png)

Dit omvat het ontgrendelen van containercomponenten zodat andere componenten kunnen worden toegevoegd, in de modus **Initiële content** of op de resulterende pagina&#39;s. Als u reeds componenten/inhoud aan de container vóór het ontgrendelen van het hebt toegevoegd, dan worden deze niet meer getoond wanneer op **de wijze van de Structuur**, maar zij worden getoond op **Aanvankelijke Inhoud** wijze. In **Wijze van de Structuur**, slechts wordt de containercomponent zelf getoond met zijn lijst van **Toegestane Componenten**.

![ Toegestane Componenten ](/help/sites-cloud/authoring/assets/templates-allowed-components.png)

Om ruimte te besparen, groeit de lay-outcontainer niet om de lijst van toegestane componenten aan te passen. In plaats daarvan wordt de container een schuifbare lijst.

De componenten die configureerbaar zijn, worden weergegeven met een pictogram **Beleid**, waarop kan worden getikt of geklikt om het beleid en de eigenschappen van die component te bewerken.

![ Configureerbaar pictogram van de Component ](/help/sites-cloud/authoring/assets/templates-configurable-component.png)

#### Verhouding tot bestaande pagina&#39;s {#relationship-to-existing-pages}

Als de structuur na het maken van op de sjabloon gebaseerde pagina&#39;s wordt bijgewerkt, worden de wijzigingen in de sjabloon doorgevoerd in deze pagina&#39;s. Er wordt een waarschuwing weergegeven op de werkbalk om u hieraan te herinneren, samen met bevestigingsdialoogvensters.

![ waarschuwing van de Banner dat het malplaatje in gebruik is ](/help/sites-cloud/authoring/assets/templates-in-use-banner.png)

### Een sjabloon bewerken - Eerste inhoud - Auteur {#editing-a-template-initial-content-author}

**de wijze van de 1} Eerste Inhoud van 0} wordt gebruikt aan bepaalde inhoud die zal verschijnen wanneer een pagina eerst gebaseerd op het malplaatje wordt gecreeerd.** De eerste inhoud kan vervolgens door auteurs van pagina&#39;s worden bewerkt.

Hoewel alle content die in de modus **Structuur** is gemaakt, zichtbaar is in **Initiële content**, kunnen alleen de ontgrendelde componenten worden geselecteerd en bewerkt.

>[!NOTE]
>
>**de wijze van de 1} Eerste Inhoud** kan van uitgeeft wijze voor pagina&#39;s worden gedacht die met dat malplaatje worden gecreeerd. Daarom wordt het beleid niet bepaald op **Aanvankelijke wijze van de Inhoud** maar eerder op [**3} wijze van de Structuur ](#editing-a-template-structure-template-author).**

* Ontgrendelde componenten die beschikbaar zijn voor bewerking, worden gemarkeerd. Als deze optie is geselecteerd, hebben ze een blauwe rand:

  ](/help/sites-cloud/authoring/assets/templates-initial-content-mode.png) de Eerste wijze van de Inhoud 0}![

* Ontgrendelde componenten beschikken over een werkbalk waarmee u de inhoud kunt bewerken en configureren:

  ![ Ontgrendelde component ](/help/sites-cloud/authoring/assets/templates-unlocked-components.png)

* Als een containercomponent is ontgrendeld (in de modus **Structuur**), kunt u nieuwe componenten aan de container toevoegen (in de modus **Initiële content**). Componenten die in de modus **Initiële content** zijn toegevoegd, kunnen worden verplaatst naar of verwijderd uit de resulterende pagina&#39;s.

  U kunt een component toevoegen met behulp van het gebied **Componenten hierheen slepen** of de optie **Nieuwe component invoegen** op de werkbalk van de betreffende container.

  ![ voeg component ](/help/sites-cloud/authoring/assets/templates-add-component.png) toe
  ![ voeg component ](/help/sites-cloud/authoring/assets/templates-add-component-dialog.png) toe

* Als de initiële inhoud van de sjabloon wordt bijgewerkt nadat pagina&#39;s zijn gemaakt op basis van de sjabloon, worden deze pagina&#39;s niet beïnvloed door wijzigingen in de oorspronkelijke inhoud van de sjabloon.

>[!NOTE]
>
>De eerste inhoud is bedoeld voor het voorbereiden van componenten en de paginalay-out die als uitgangspunt dienen voor het maken van de inhoud. Het is niet de bedoeling om de inhoud te zijn die ongewijzigd blijft. Daarom kan de initiële inhoud niet worden vertaald.
>
>Als u vertaalbare tekst in uw malplaatje zoals in kopballen of footers moet omvatten, kunt u de [ localisatieeigenschappen van de kerncomponenten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) gebruiken.

### Een sjabloon bewerken - Layout - Sjabloonauteur {#editing-a-template-layout-template-author}

U kunt de sjabloonlay-out voor een reeks apparaten definiëren. [ Responsieve lay-out ](/help/sites-cloud/authoring/page-editor/responsive-layout.md) voor malplaatjes werkt aangezien het voor pagina creatie doet.

>[!NOTE]
>
>De veranderingen in de lay-out worden weerspiegeld in **Aanvankelijke wijze van de Inhoud**, maar geen verandering wordt gezien op **wijze van de Structuur**.

![ geef malplaatjelay-out ](/help/sites-cloud/authoring/assets/templates-edit-layout.png) uit

### Een sjabloon bewerken - Paginabeleid - Sjabloonauteur/ontwikkelaar {#editing-a-template-page-policy-template-author-developer}

Het paginabeleid, inclusief de vereiste clientbibliotheken, blijft behouden onder de optie **Paginabeleid** van het menu **Pagina-informatie**.

Om tot de **dialoog van het Beleid van de Pagina** toegang te hebben:

1. Van de **Redacteur van het Malplaatje**, selecteer **Informatie van de Pagina** van de toolbar, toen **Beleid van de Pagina** om de dialoog te openen.
1. Het **dialoogvenster van het Beleid van de 1} Pagina opent en is verdeeld in twee secties:**

   * De linkerhelft bepaalt het [ paginabeleid ](#page-policies)
   * De rechterhelft bepaalt de [ paginaeigenschappen ](#page-properties)

   ![ het ontwerp van de Pagina ](/help/sites-cloud/authoring/assets/templates-page-design.png)

#### Paginabeleid {#page-policies}

U kunt een inhoudsbeleid toepassen op de sjabloon of de resulterende pagina&#39;s. Hiermee wordt het inhoudsbeleid voor het hoofdalineasysteem op de pagina gedefinieerd.

![ Beleid van de Pagina ](/help/sites-cloud/authoring/assets/templates-page-policy.png)

* U kunt een bestaand beleid voor de pagina van **selecteren beleid** drop-down.

  ![ selecteur van het Beleid ](/help/sites-cloud/authoring/assets/templates-policy-selector.png)

  Een nieuw beleid kan worden toegevoegd door toe te voegen knoop naast **te selecteren beleid** drop-down lijst. Geef een nieuwe titel op het **gebied van de Titel van het Beleid**.

  ![ voeg de knoop van het Beleid toe ](/help/sites-cloud/authoring/assets/templates-add-policy-button.png)

  Het geselecteerde bestaande beleid in **Uitgezochte beleid** drop-down lijst kan als nieuw beleid worden gekopieerd gebruikend de exemplaarknoop naast de drop-down lijst. Geef een nieuwe titel op het **gebied van de Titel van het Beleid**. Door gebrek wordt het gekopieerde beleid genoemd **Exemplaar van X**, waar X de titel van het gekopieerde beleid is.

  ![ knoop van het Beleid van het Exemplaar ](/help/sites-cloud/authoring/assets/templates-copy-policy-button.png)

* Bepaal een titel voor het beleid op het **gebied van de Titel van het Beleid**. Een beleid wordt vereist om een titel te hebben zodat het gemakkelijk in **Uitgezochte beleid** drop-down lijst kan worden geselecteerd.

  ![ Titel van het Beleid ](/help/sites-cloud/authoring/assets/templates-policy-title.png)

* Een beschrijving van het beleid is facultatief op het **gebied van de Beschrijving van het Beleid**.
* In de **Andere malplaatjes die ook de geselecteerde beleids** sectie gebruiken, kunt u gemakkelijk zien welke andere malplaatjes het beleid gebruiken in de **Uitgezochte beleid** drop-down lijst wordt geselecteerd.

  ![ het gebruik van het Beleid ](/help/sites-cloud/authoring/assets/templates-policy-use.png)

#### Pagina-eigenschappen {#page-properties}

Gebruikend paginaeigenschappen, kunt u de vereiste cliënt-zijbibliotheken bepalen door de **dialoog van het Ontwerp van de Pagina te gebruiken**. Deze client-side bibliotheken bevatten stijlpagina&#39;s en javascript die met de sjabloon moeten worden geladen en pagina&#39;s die met die sjabloon zijn gemaakt.

![Pagina-eigenschappen](/help/sites-cloud/authoring/assets/templates-page-properties.png)

* Geef de clientbibliotheken op die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt. Het ingaan van de naam van een bibliotheek op het tekstgebied in de **sectie van de Bibliotheken van de Kant van de Cliënt**.

  ![ cliënt-zijbibliotheken ](/help/sites-cloud/authoring/assets/templates-client-side-libraries.png)

* Als er meerdere bibliotheken nodig zijn, klikt u op de knop Toevoegen om een extra tekstveld voor de naam van de bibliotheek toe te voegen.

  ![ voeg knoop ](/help/sites-cloud/authoring/assets/templates-add-button.png) toe

  Voeg zoveel tekstvelden toe als nodig zijn voor uw clientbibliotheken.

* Definieer zo nodig de relatieve positie van de bibliotheken door de velden te slepen met de sleepgreep.

  ![ handvat van de belemmering ](/help/sites-cloud/authoring/assets/templates-drag-handle.png)

>[!NOTE]
>
>Hoewel de sjabloonauteur het paginabeleid voor de sjabloon kan opgeven, moet hij of zij details van de desbetreffende client-side bibliotheken van de ontwikkelaar ophalen.

### Een sjabloon bewerken - Initiële pagina-eigenschappen - Auteur {#editing-a-template-initial-page-properties-author}

Gebruikend de **Aanvankelijke optie van de Eigenschappen van de Pagina**, kunt u de aanvankelijke [ pagina eigenschappen ](/help/sites-cloud/authoring/sites-console/page-properties.md) bepalen die moeten worden gebruikt wanneer het creëren van resulterende pagina&#39;s.

1. Van de malplaatjedacteur, uitgezochte **Informatie van de Pagina** van de toolbar, toen **Aanvankelijke Eigenschappen van de Pagina** om de dialoog te openen.

1. In het dialoogvenster kunt u de eigenschappen definiëren die u wilt toepassen op pagina&#39;s die met deze sjabloon zijn gemaakt.

   ![ Sjablonen aanvankelijke pagina-eigenschappen ](/help/sites-cloud/authoring/assets/templates-initial-properties.png)

1. Bevestig uw definities met **Gereed**.

## Aanbevolen procedures {#best-practices}

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

      * Ontgrendelingscomponenten (die zijn vergrendeld) ontbreken op bestaande pagina&#39;s.
      * Door componenten te vergrendelen (die bewerkbaar waren) wordt die inhoud niet op de pagina&#39;s weergegeven.

   >[!NOTE]
   >
   >AEM geeft expliciete waarschuwingen wanneer het veranderen van de slotstatus van componenten op malplaatjes die niet meer concepten zijn.

1. [ Creërend uw eigen omslagen ](#creating-a-template-folder-admin) voor uw plaats-specifieke malplaatjes.
1. [ Publish uw malplaatjes ](#publishing-a-template-template-author) van de **[console van Malplaatjes.]** (/help/sites-cloud/administering/templates-console.md)
