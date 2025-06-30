---
title: Metagegevensschema's definiëren de indeling van de pagina met eigenschappen van metagegevens
description: Het metagegevensschema definieert de indeling van de pagina met eigenschappen en de eigenschappen van metagegevens die voor elementen worden weergegeven. Leer hoe u een aangepast metagegevensschema kunt maken, het schema voor metagegevens kunt bewerken en hoe u het schema voor metagegevens op elementen kunt toepassen.
contentOwner: AG
feature: Metadata
role: User, Admin
exl-id: 9e94afeb-1c54-4653-bf52-b0910c0cb6c1
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '2497'
ht-degree: 5%

---

# Metagegevensschema&#39;s {#metadata-schemas}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/metadata-schemas.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Organisaties beschikken over een metagegevensmodel dat de detectie, het gebruik, de interoperabiliteit, enzovoort van middelen verbetert. Correcte toepassing van metagegevens is onaantastbaar om workflows met metagegevens en processen te behouden. Om aan organisatie-brede meta-gegevensstrategie en normen te houden, kunt u meta-gegevensschema&#39;s gebruiken die gebruikers DAM helpen zich te richten. Met [!DNL Adobe Experience Manager] kunt u gemakkelijk en flexibel metagegevensschema&#39;s maken, onderhouden en toepassen.

In [!DNL Adobe Experience Manager Assets] bevatten schema&#39;s specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] redacteur gebruiken om de bestaande schema&#39;s te wijzigen of douanemetagegevensschema&#39;s toe te voegen.

Ga als volgt te werk om de pagina met eigenschappen voor een element weer te geven en te bewerken:

1. Klik op de optie **[!UICONTROL View Properties]** van de snelle handelingen op het element element in de kaartweergave. Alternatief, selecteer een activa en klik dan **[!UICONTROL Properties]** ![ meningseigenschappen ](assets/do-not-localize/info-circle-icon.png) van de toolbar.

1. U kunt de verschillende bewerkbare eigenschappen van metagegevens bewerken onder de beschikbare tabbladen. U kunt het element [!UICONTROL Type] echter niet wijzigen op het tabblad [!UICONTROL Basic] met eigenschappen.

   ![ Basis lusje van activaEigenschappen, waar activa type niet kan worden veranderd ](assets/asset-properties-basic-tab.png)

   *Cijfer: Basis lusje op activa [!UICONTROL Properties].*

   Als u het MIME-type voor een element wilt wijzigen, gebruikt u een aangepast schema voor metagegevens of wijzigt u een bestaand formulier. Zie [ Forms van het Schema van Meta-gegevens ](#edit-metadata-schema-forms) voor meer informatie uitgeven. Als u het metagegevensschema van een MIME-type wijzigt, wordt de indeling van de eigenschappenpagina voor de elementen en alle subtypen gewijzigd. Als u bijvoorbeeld een JPEG-schema wijzigt onder `default/image` , wordt alleen de indeling van metagegevens (eigenschappen van elementen) gewijzigd voor elementen met het MIME-type `image/jpeg` . Als u echter het standaardschema bewerkt, worden de wijzigingen doorgevoerd in de indeling van de metagegevens voor alle typen elementen.

## Metagegevensschema-formulieren {#default-metadata-schema-forms}

Als u een lijst met formulieren of sjablonen wilt weergeven, navigeert u in de interface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** .

[!DNL Experience Manager] bevat de volgende sjablonen voor metagegevensschema-formulieren.

| Sjablonen | | Beschrijving |
|---|---|---|
| [!UICONTROL default] | | Het basisschema voor metagegevens voor elementen. |
| | De volgende onderliggende formulieren nemen de eigenschappen van het [!UICONTROL default] -formulier over: | |
| | <ul><li>[!UICONTROL dm_video]</li></ul> | Schemaformulier voor Dynamic Media-video&#39;s. |
| | <ul><li>[!UICONTROL image]</li></ul> | Schema voor afbeeldingen van het MIME-type, zoals `image/jpeg` en `image/png` . <br> Het [!UICONTROL image] -formulier heeft de volgende onderliggende formuliersjablonen: <ul><li> [!UICONTROL jpeg]: schema voor elementen met subtype [!UICONTROL jpeg] .</li> <li>[!UICONTROL tiff]: schema voor de elementen met subtype TIFF.</li></ul> |
| | <ul><li>[!UICONTROL application]</li></ul> | Schema-formulier voor elementen met het MIME-type, zoals `application/pdf` en `application/zip` . <br>[!UICONTROL pdf]: Schema voor elementen met subtype PDF. |
| | <ul><li>[!UICONTROL video]</li></ul> | Schema-formulier voor video-elementen van het type MIME, zoals `video/avi` en `video/mp4` . |
| [!UICONTROL collection] | | Schema voor verzamelingen. |
| [!UICONTROL contentfragment] | | Schemaformulier voor inhoudsfragmenten. |
| [!UICONTROL forms] | | Dit schema-formulier heeft betrekking op [!DNL Adobe Experience Manager Forms] . |
| [!UICONTROL ugc_contentfragment] | | Schemaformulier voor door de gebruiker gegenereerde inhoudsonderdelen en elementen die via sociale media in Experience Manager zijn geïntegreerd. |

>[!NOTE]
>
>Klik op de naam van het schema om de onderliggende formulieren van een schema weer te geven.

## Een metagegevensschema toevoegen {#add-a-metadata-schema-form}

Ga als volgt te werk om een metagegevensschemaformulier toe te voegen:

1. Als u een aangepaste sjabloon aan de lijst wilt toevoegen, klikt u op **[!UICONTROL Create]** op de werkbalk.

   >[!NOTE]
   >
   >Er wordt een vergrendelingssymbool weergegeven met de onbewerkte sjablonen. Als u een malplaatje aanpast, is het niet gesloten ![ slot gesloten ](assets/do-not-localize/lock_closed_icon.svg).

1. Geef in het dialoogvenster de titel van het schema op en klik op **[!UICONTROL Create]** om het maken van het formulier te voltooien.

## Formulieren met metagegevensschema bewerken {#edit-metadata-schema-forms}

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagplaats. U kunt tabs of formulieritems toevoegen aan het metagegevensschema. De tabbladen en formulieritems die van het bovenliggende element zijn afgeleid, bevinden zich in de vergrendelde status. U kunt deze niet wijzigen op het niveau van het kind.

1. Selecteer een formulier op de [!UICONTROL Metadata Schema Forms] -pagina en klik op **[!UICONTROL Edit]** in de werkbalk.

1. Pas het metagegevensformulier aan op de pagina **[!UICONTROL Metadata Schema Form Editor]** . Sleep de benodigde componenten van de tab **[!UICONTROL Build Form]** naar een van de tabbladen.

   ![ Redacteur van het Schema van Meta-gegevens om de pagina van ActivaEigenschappen aan te passen ](assets/metadata-schema-editor.png)

   *Cijfer: A [!UICONTROL Metadata Schema Form Editor] pagina met beschikbare lusjes.*

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]** .

### Componenten op het tabblad [!UICONTROL Build Form] {#components-within-the-build-form-tab}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het schemaformulier gebruikt. Het tabblad **[!UICONTROL Settings]** bevat de kenmerken van elk item dat u selecteert op het tabblad **[!UICONTROL Build Form]** . De volgende tabel bevat een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]** :

| Componentnaam | Beschrijving |
| -------------------------------- | ----------------------------------------------------------------------------------- |
| [!UICONTROL Section Header] | Voeg een sectiekopje toe voor een lijst met gangbare componenten. |
| [!UICONTROL Single Line Text] | Voeg een eigenschap voor één regel tekst toe. De eigenschap wordt opgeslagen als een tekenreeks. |
| [!UICONTROL Multi Value Text] | Voeg een teksteigenschap voor meerdere waarden toe. Deze wordt opgeslagen als een tekenreeks-array. |
| [!UICONTROL Number] | Voeg een getalcomponent toe. |
| [!UICONTROL Date] | Voeg een datumcomponent toe. |
| [!UICONTROL Dropdown] | Voeg een vervolgkeuzelijst toe. |
| [!UICONTROL Standard Tags] | Voeg een tag toe. |
| [!UICONTROL Smart Tags] | U kunt zoekmogelijkheden uitbreiden door automatisch metagegevenstags toe te voegen. |
| [!UICONTROL Hidden Field] | Voeg een verborgen veld toe. Deze wordt als een POST-parameter verzonden wanneer het element wordt opgeslagen. |
| [!UICONTROL Asset Referenced By] | Voeg deze component toe om een lijst weer te geven met elementen waarnaar door het element wordt verwezen. |
| [!UICONTROL Asset Referencing] | Toevoegen om een lijst weer te geven met elementen die naar het element verwijzen. |
| [!UICONTROL Products References] | Toevoegen om de lijst weer te geven met producten die aan het element zijn gekoppeld. |
| [!UICONTROL Contextual Metadata] | Toevoegen om de weergave van andere tabbladen met metagegevens in de eigenschappenpagina met elementen te besturen. |

<!-- TBD: Ratings are not available in Experience Manager as a Cloud Service. Removed via cqdoc-18089 ticket. 
| [!UICONTROL Asset Rating]        | Add to display options for rating the asset.                                       |
-->

#### De metagegevenscomponent bewerken {#edit-the-metadata-component}

Als u de eigenschappen van een metagegevenscomponent in het formulier wilt bewerken, klikt u op de component om de volgende eigenschappen (of een subset ervan) op het tabblad **[!UICONTROL Settings]** geheel of gedeeltelijk te bewerken. Het wordt aanbevolen slechts één veld toe te wijzen aan een bepaalde eigenschap in het metagegevensschema. Anders wordt het laatst toegevoegde veld dat aan de eigenschap is toegewezen, door het systeem gekozen.

**Etiket van het Gebied**: De naam van het meta-gegevensbezit dat op de eigenschappen pagina voor de activa wordt getoond.

**Kaart aan Bezit**: Dit bezit specificeert de relatieve weg aan of naam van de activaknoop waar het in de bewaarplaats van CRX wordt bewaard. Het begint met `./` om aan te geven dat het pad zich onder het knooppunt van het element bevindt.

Hier volgen voorbeelden van geldige waarden voor een eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metadataknooppunt van de asset opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: slaat de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, wordt u aangeraden deze als Uitschakelen-bewerking te markeren. Anders treedt de fout &quot;Wijzigen van asset(s)&quot; op wanneer u de eigenschappen van de asset opslaat.

Om ervoor te zorgen dat de component correct in de vorm van het meta-gegevensschema wordt getoond, zou de bezitspad geen ruimten moeten omvatten.

* **Placeholder**: Gebruik dit bezit om relevante placeholder tekst betreffende het meta-gegevensbezit te specificeren.
* **Vereist**: Gebruik dit bezit om een meta-gegevensbezit als verplicht op de eigenschappen pagina te merken.
* **maak** onbruikbaar uit: Gebruik dit bezit om het even welke uitgeeft aan een bezit op de eigenschappen pagina niet toe te staan.
* **toon Leeg Gebied in Gelezen slechts**: Teken dit bezit om een meta-gegevensbezit op de eigenschappen pagina te tonen zelfs als het geen waarde heeft. Wanneer een eigenschap metadata geen waarde heeft, wordt deze standaard niet vermeld op de eigenschappenpagina.
* **toon geordende lijst**: Gebruik dit bezit om een geordende lijst van keuzen te tonen.
* **Keuzen**: Gebruik dit bezit om keuzen in een lijst te specificeren.
* **Beschrijving**: Gebruik dit bezit om een korte beschrijving voor de meta-gegevenscomponent toe te voegen.
* **Klasse**: De klasse van objecten het bezit wordt geassocieerd met.
* **Schrapping**: Klik [!UICONTROL Delete] om een component van de schemavorm te schrappen.

>[!NOTE]
>
>De component [!UICONTROL Hidden Field] bevat deze kenmerken niet. In plaats daarvan bevat de klasse eigenschappen, zoals Naam, Waarde, Veldlabel en Beschrijving. De waarden voor de component Verborgen veld worden als een POST-parameter verzonden wanneer het element wordt opgeslagen. Deze wordt niet opgeslagen als metagegevens voor het element.

Als u de optie **[!UICONTROL Required]** selecteert, kunt u zoeken naar assets waarvoor verplichte metadata ontbreken. Vouw in het deelvenster **[!UICONTROL Filters]** het predicaat **[!UICONTROL Metadata Validation]** uit en selecteer de optie **[!UICONTROL Invalid]**. In de zoekresultaten worden assets weergegeven waarvoor verplichte metadata ontbreken die u via het schemaformulier hebt geconfigureerd.

Als u de component Contextuele metagegevens toevoegt aan een tabblad van een schemaformulier, wordt de component weergegeven als een lijst op de eigenschappenpagina van elementen waarop het specifieke schema wordt toegepast. De lijst bevat alle andere tabbladen, behalve het tabblad waarop u de component Contextuele metagegevens hebt toegepast. Momenteel biedt deze functie basisfunctionaliteit voor het beheren van de weergave van metagegevens op basis van de context.

Als u een tabblad in de eigenschappenpagina wilt weergeven naast het tabblad waarop de component Contextuele metagegevens is toegepast, selecteert u het tabblad in de lijst. Het tabblad wordt toegevoegd aan de pagina met eigenschappen.

### Eigenschappen in JSON-bestand opgeven {#specify-properties-in-json-file}

In plaats van eigenschappen voor de opties op het tabblad **[!UICONTROL Settings]** op te geven, kunt u de opties in een JSON-bestand definiëren door overeenkomstige sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL JSON Path]**.

#### Een tabblad toevoegen aan of verwijderen uit het schemaformulier {#add-delete-a-tab-in-the-schema-form}

Met de schema-editor kunt u een tabblad toevoegen of verwijderen. Het standaardschema bevat de tabbladen **[!UICONTROL Basic]** , **[!UICONTROL Advanced]** , **[!UICONTROL IPTC]** en **[!UICONTROL IPTC Extension]** .

![ Standaardlusjes in de vorm van het Schema van Meta-gegevens ](assets/metadata-schema-form-tabs.png)

Klik op `+` om een tabblad toe te voegen aan een schemaformulier. Standaard heeft het nieuwe tabblad de naam `Unnamed-1` . U kunt de naam wijzigen via het tabblad **[!UICONTROL Settings]** . Klik op `X` om een tab te verwijderen.

![ voeg of schrap een lusje toe gebruikend de Redacteur van het Schema van Meta-gegevens ](assets/metadata-schema-form-new-tab.png)

## Formulieren met metagegevens verwijderen {#deleting-metadata-schema-forms}

Met Experience Manager kunt u alleen aangepaste schema-formulieren verwijderen. U kunt hiermee de standaardschema-formulieren/sjablonen niet verwijderen. U kunt echter alle aangepaste wijzigingen in deze formulieren verwijderen.

Als u een formulier wilt verwijderen, selecteert u een formulier en klikt u op het pictogram voor verwijderen.

>[!NOTE]
>
>Nadat u aangepaste wijzigingen in een standaardformulier hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór de aangepaste wijzigingen in het schema voor metagegevens om aan te geven dat de standaardstatus van het formulier is hersteld.

>[!NOTE]
>
>* Nadat u douaneveranderingen in een standaardvorm schrapt, sluit het slot ![ gesloten ](assets/do-not-localize/lock_closed_icon.svg) opnieuw verschijnt vóór de vorm. Hiermee wordt aangegeven dat de standaardstatus van het formulier wordt hersteld.
>* U kunt de standaardformulieren voor het metagegevensschema niet verwijderen in [!DNL Assets] .

## Schema-formulieren voor MIME-typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] bevat standaardformulieren voor verschillende MIME-typen uit het vak. U kunt echter aangepaste formulieren toevoegen voor elementen van verschillende MIME-typen.

### Nieuwe formulieren toevoegen voor MIME-typen {#adding-new-forms-for-mime-types}

Maak een formulier onder het juiste formuliertype. Als u bijvoorbeeld een sjabloon voor het subtype `image/png` wilt toevoegen, maakt u het formulier onder de &quot;afbeeldingsformulieren&quot;. De titel voor het schemaformulier is de naam van het subtype. In dit geval is de titel `png` .

#### Een bestaande schemasjabloon gebruiken voor verschillende MIME-typen {#use-an-existing-schema-template-for-various-mime-types}

U kunt een bestaande sjabloon voor een ander MIME-type gebruiken. Gebruik bijvoorbeeld het formulier `image/jpeg` voor elementen van het MIME-type `image/png` .

In dit geval maakt u een knooppunt op `/etc/dam/metadataeditor/mimetypemappings` in de CRX-opslagplaats. Geef een naam voor het knooppunt op en definieer de volgende eigenschappen:

| Naam | Beschrijving | Type | Waarde |
|------|-------------|------|-------|
| `exposedmimetype` | Naam van het bestaande formulier dat moet worden toegewezen | `String` | `image/jpeg` |
| `mimetypes` | Lijst met MIME-typen die het formulier gebruiken dat is gedefinieerd in het kenmerk `exposedmimetype` | `String` | `image/png` |

[!DNL Assets] wijst de volgende MIME-typen en schema-formulieren toe:

| Schema | MIME-typen |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/Related; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/Related; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/Related; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Toegang tot metagegevensschema&#39;s verlenen {#grant-access-to-metadata-schemas}

De functie Metagegevensschema is alleen beschikbaar voor beheerders. Beheerders kunnen echter toegang verlenen aan niet-beheerders door bepaalde machtigingen te wijzigen. Geef niet-beheerders de machtigingen voor de map `/conf` op voor het maken, wijzigen en verwijderen van machtigingen.

## Mapspecifieke metagegevens toepassen {#applying-folder-specific-metadata}

Met [!DNL Assets] kunt u een variant van een metagegevensschema definiëren en dit toepassen op een specifieke map.

U kunt bijvoorbeeld een variant van het standaardmetagegevensschema definiëren en deze toepassen op een map. Wanneer u het gewijzigde schema toepast, wordt het oorspronkelijke standaardmetagegevensschema genegeerd dat op elementen in de map is toegepast.

Alleen elementen die zijn geüpload naar de map waarop dit schema is toegepast, komen overeen met de gewijzigde metagegevens die zijn gedefinieerd in het schema voor alternatieve metagegevens. [!DNL Assets] in andere mappen waar het oorspronkelijke schema wordt toegepast, blijven de metagegevens die zijn gedefinieerd in het oorspronkelijke schema in acht nemen.

Metagegevensovererving door elementen is gebaseerd op het schema dat wordt toegepast op de map op het hoogste niveau in de hiërarchie. Hetzelfde schema wordt toegepast op of overgeërfd door de submappen. Als een ander schema op submapniveau wordt toegepast, stopt de overerving.

1. Navigeer in de interface van [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** . De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Schakel het selectievakje in vóór een formulier, bijvoorbeeld het standaardmetagegevensformulier, en klik op **[!UICONTROL Copy]** en sla het op als een aangepast formulier. Geef een aangepaste naam voor het formulier op, bijvoorbeeld `my_default` . U kunt ook een aangepast formulier maken.

1. Selecteer op de pagina **[!UICONTROL Metadata Schema Forms]** het `my_default` -formulier en klik vervolgens op **[!UICONTROL Edit]** .
1. Voeg op de pagina **[!UICONTROL Metadata Schema Editor]** een tekstveld toe aan het schema. Voeg bijvoorbeeld een veld met het label **[!UICONTROL Category]** toe.
1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** .
1. Selecteer **[!UICONTROL Apply to Folders]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.
1. Selecteer de map waarop u het gewijzigde schema wilt toepassen en selecteer vervolgens **[!UICONTROL Apply]** .
1. Als op de map het andere metagegevensschema is toegepast, verschijnt er een waarschuwing dat u het bestaande metagegevensschema wilt overschrijven. Klik **overschrijven**.
1. Klik **O.K.** om het succesbericht te sluiten.
1. Navigeer naar de map waarop u het gewijzigde metagegevensschema hebt toegepast.

## Verplichte metagegevens definiëren {#defining-mandatory-metadata}

U kunt verplichte velden definiëren op mapniveau. Deze worden afgedwongen voor elementen die naar de map worden geüpload. Als u elementen uploadt met ontbrekende metagegevens voor de verplichte velden die u eerder hebt gedefinieerd, wordt een visuele indicatie voor ontbrekende metagegevens weergegeven in de weergave Kaart.

>[!NOTE]
>
>Een metagegevensveld kan op basis van de waarde van een ander veld als verplicht worden gedefinieerd. In de weergave Kaarten geeft Experience Manager geen waarschuwingsbericht weer over ontbrekende metagegevens voor dergelijke verplichte metagegevensvelden.

1. Klik op het Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]** . De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Sla het standaardmetagegevensformulier op als een aangepast formulier. Sla het bestand bijvoorbeeld op als `my_default` .
1. Bewerk het aangepaste formulier. Voeg een verplicht veld toe. Voeg bijvoorbeeld een veld **[!UICONTROL Category]** toe en maak het veld verplicht.
1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]** . Selecteer het formulier en selecteer vervolgens **[!UICONTROL Apply to Folders]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.
1. Navigeer naar de map en upload elementen met ontbrekende metagegevens voor het verplichte veld dat u aan het aangepaste formulier hebt toegevoegd. Er wordt een bericht voor de ontbrekende metagegevens van het verplichte veld weergegeven in de kaartweergave van het element.
1. (Optioneel) Toegang `https://[server]:[port]/system/console/components/` . Configureer en schakel `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` in die standaard is uitgeschakeld. Stel een frequentie in waarmee Experience Manager controleert of metagegevens over de elementen geldig zijn.

   Deze configuratie voegt een eigenschap `hasValidMetadata` toe aan `jcr:content` elementen. Met deze eigenschap kan Experience Manager resultaten in een zoekopdracht filteren.

   >[!NOTE]
   >
   >Als een element wordt toegevoegd na de geplande controle, wordt het element pas bij de volgende geplande controle gemarkeerd met `hasValidMetadata` . De elementen worden niet weergegeven in tussenliggende zoekresultaten.

   >[!CAUTION]
   >
   >De controles van de meta-gegevensbevestiging zijn middelintensief en kunnen de prestaties van uw systeem beïnvloeden. Plan de controles dienovereenkomstig. Als de server het laden niet aankan, probeert u deze taak uit te schakelen

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)