---
title: Metagegevensschema's definiëren de indeling van de pagina met eigenschappen van metagegevens
description: Het metagegevensschema definieert de indeling van de pagina met eigenschappen en de eigenschappen van metagegevens die voor elementen worden weergegeven. Leer hoe u een aangepast metagegevensschema kunt maken, het schema voor metagegevens kunt bewerken en hoe u het schema voor metagegevens op elementen kunt toepassen.
contentOwner: AG
feature: Metagegevens
role: Business Practitioner,Administrator
exl-id: 9e94afeb-1c54-4653-bf52-b0910c0cb6c1
translation-type: tm+mt
source-git-commit: 855b8b1de11e5f986948d3144104d6b5226c2dd5
workflow-type: tm+mt
source-wordcount: '2424'
ht-degree: 6%

---

# Metagegevensschema&#39;s {#metadata-schemas}

Organisaties beschikken over een metagegevensmodel dat de detectie, het gebruik, de interoperabiliteit, enzovoort van middelen verbetert. Correcte toepassing van metagegevens is onaantastbaar om workflows met metagegevens en processen te behouden. Om aan organisatie-brede meta-gegevensstrategie en normen te houden, kunt u meta-gegevensschema&#39;s gebruiken die gebruikers DAM helpen zich te richten. [!DNL Adobe Experience Manager] biedt eenvoudige en flexibele methoden voor het maken, onderhouden en toepassen van metagegevensschema&#39;s.

In [!DNL Adobe Experience Manager Assets] bevatten schema&#39;s specifieke velden waarin specifieke informatie moet worden ingevuld. Het bevat ook lay-outinformatie om meta-gegevensgebieden op een gebruikersvriendelijke manier te tonen. Metagegevenseigenschappen zijn onder andere titel, beschrijving, MIME-typen, tags en meer. U kunt de [!UICONTROL Metadata Schema Forms] redacteur gebruiken om de bestaande schema&#39;s te wijzigen of douanemetagegevensschema&#39;s toe te voegen.

Ga als volgt te werk om de pagina met eigenschappen voor een element weer te geven en te bewerken:

1. Klik op de optie **[!UICONTROL View Properties]** van de snelle handelingen op het elementblok in de kaartweergave. U kunt ook een element selecteren en vervolgens op **[!UICONTROL Properties]** ![weergave-eigenschappen](assets/do-not-localize/info-circle-icon.png) op de werkbalk klikken.

1. U kunt de verschillende bewerkbare eigenschappen van metagegevens bewerken onder de beschikbare tabbladen. U kunt het element [!UICONTROL Type] echter niet wijzigen op het tabblad [!UICONTROL Basic] van de eigenschappenpagina.

   ![Het tabblad Standaard van de eigenschappen van elementen, waarin het elementtype niet kan worden gewijzigd](assets/asset-properties-basic-tab.png)

   *Afbeelding: Het tabblad Standaard voor elementen  [!UICONTROL Properties].*

   Als u het MIME-type voor een element wilt wijzigen, gebruikt u een aangepast schema voor metagegevens of wijzigt u een bestaand formulier. Zie [Metagegevensschema Forms](#edit-metadata-schema-forms) bewerken voor meer informatie. Als u het metagegevensschema van een MIME-type wijzigt, wordt de indeling van de eigenschappenpagina voor de elementen en alle subtypen gewijzigd. Als u bijvoorbeeld een JPEG-schema wijzigt onder `default/image`, wordt alleen de indeling van metagegevens (eigenschappen van elementen) gewijzigd voor elementen met het MIME-type `image/jpeg`. Als u echter het standaardschema bewerkt, worden de wijzigingen doorgevoerd in de indeling van de metagegevens voor alle typen elementen.

## Metagegevensschema-formulieren {#default-metadata-schema-forms}

Als u een lijst met formulieren of sjablonen wilt weergeven, navigeert u in de [!DNL Experience Manager]-interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**.

[!DNL Experience Manager] Hier vindt u de volgende sjablonen voor metagegevensschema-formulieren.

| Sjablonen |  | Beschrijving |
|---|---|---|
| [!UICONTROL default] |  | Het basisschema voor metagegevens voor elementen. |
|  | De volgende onderliggende formulieren nemen de eigenschappen over van het formulier [!UICONTROL default]: |  |
|  | <ul><li>[!UICONTROL dm_video]</li></ul> | Schema voor Dynamic Media-video&#39;s. |
|  | <ul><li>[!UICONTROL image]</li></ul> | Schema voor afbeeldingen van het MIME-type zoals `image/jpeg` en `image/png`. <br> Het  [!UICONTROL image] formulier heeft de volgende onderliggende formuliersjablonen: <ul><li> [!UICONTROL jpeg]: Schema voor activa met subtype  [!UICONTROL jpeg].</li> <li>[!UICONTROL tiff]: Schema voor de elementen met subtype TIFF.</li></ul> |
|  | <ul><li>[!UICONTROL application]</li></ul> | Schema-formulier voor elementen met het MIME-type zoals `application/pdf` en `application/zip`. <br>[!UICONTROL pdf]: Schemaformulier voor elementen met subtype PDF. |
|  | <ul><li>[!UICONTROL video]</li></ul> | Schemaformulier voor video-elementen met het MIME-type zoals `video/avi` en `video/mp4`. |
| [!UICONTROL collection] |  | Schemaformulier voor verzamelingen. |
| [!UICONTROL contentfragment] |  | Schemaformulier voor contentfragmenten. |
| [!UICONTROL forms] |  | Dit schema formulier heeft betrekking op [!DNL Adobe Experience Manager Forms]. |
| [!UICONTROL ugc_contentfragment] |  | Schemaformulier voor door de gebruiker gegenereerde inhoudsonderdelen en elementen die via sociale media in de Experience Manager zijn geïntegreerd. |

>[!NOTE]
>
>Klik op de naam van het schema om de onderliggende formulieren van een schema weer te geven.

## Een metagegevensschema toevoegen {#add-a-metadata-schema-form}

Ga als volgt te werk om een metagegevensschemaformulier toe te voegen:

1. Als u een aangepaste sjabloon aan de lijst wilt toevoegen, klikt u op **[!UICONTROL Create]** op de werkbalk.

   >[!NOTE]
   >
   >Er wordt een vergrendelingssymbool weergegeven met de onbewerkte sjablonen. Als u een malplaatje aanpast, is het niet gesloten ![slot gesloten](assets/do-not-localize/lock_closed_icon.svg).

1. Geef in het dialoogvenster de titel van het schema op en klik op **[!UICONTROL Create]** om het maken van het formulier te voltooien.

## Formulieren met metagegevensschema {#edit-metadata-schema-forms} bewerken

U kunt een nieuw toegevoegd of bestaand schema voor metagegevens bewerken. Het metagegevensschema bevat tabbladen en formulieritems binnen tabbladen. U kunt deze formulieritems toewijzen/configureren aan een veld binnen een metagegevensknooppunt in de CRX-opslagruimte. U kunt tabs of formulieritems toevoegen aan het metagegevensschemaformulier. De tabbladen en formulieritems die van het bovenliggende element zijn afgeleid, bevinden zich in de vergrendelde status. U kunt deze niet wijzigen op het niveau van het kind.

1. Selecteer op de pagina [!UICONTROL Metadata Schema Forms] een formulier en klik op **[!UICONTROL Edit]** in de werkbalk.

1. Pas op de pagina **[!UICONTROL Metadata Schema Form Editor]** het metagegevensformulier aan. Sleep de benodigde componenten van het tabblad **[!UICONTROL Build Form]** naar een van de tabbladen.

   ![Editor metagegevensschema om de pagina Eigenschappen van elementen aan te passen](assets/metadata-schema-editor.png)

   *Afbeelding: Een  [!UICONTROL Metadata Schema Form Editor] pagina met beschikbare tabbladen.*

1. Als u een component wilt configureren, selecteert u deze en wijzigt u de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**.

### Componenten op het tabblad [!UICONTROL Build Form] {#components-within-the-build-form-tab}

Het tabblad **[!UICONTROL Build Form]** bevat formulieritems die u in het schemaformulier gebruikt. Het tabblad **[!UICONTROL Settings]** bevat de kenmerken van elk item dat u selecteert op het tabblad **[!UICONTROL Build Form]**. De volgende tabel bevat een lijst met formulieritems die beschikbaar zijn op het tabblad **[!UICONTROL Build Form]**:

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
| [!UICONTROL Asset Rating] | Toevoegen aan weergaveopties voor het beoordelen van het element. |
| [!UICONTROL Contextual Metadata] | Toevoegen om de weergave van andere tabbladen met metagegevens in de eigenschappenpagina met elementen te besturen. |

#### De metagegevenscomponent {#edit-the-metadata-component} bewerken

Als u de eigenschappen van een metagegevenscomponent in het formulier wilt bewerken, klikt u op de component om de volgende eigenschappen (of een subset ervan) op het tabblad **[!UICONTROL Settings]** geheel of gedeeltelijk te bewerken.

**Veldlabel**: De naam van de eigenschap metadata die wordt weergegeven op de eigenschappenpagina voor het element.

**Toewijzen aan eigenschap**: This property specifies the relative path to or name of the asset node where it is saved in the CRX repository. Het begint met `./` om erop te wijzen dat de weg onder de knoop van het element is.

Hier volgen de geldige waarden voor deze eigenschap:

* `./jcr:content/metadata/dc:title`: Hiermee wordt de waarde in het metadataknooppunt van de asset opgeslagen als de eigenschap `dc:title`.

* `./jcr:created`: Hiermee slaat u de aanmaakdatum en -tijd van een element op. Het is een beschermde eigenschap. Als u deze eigenschappen configureert, raadt Adobe u aan deze als Uitschakelen bewerken te markeren. Anders treedt de fout &quot;Wijzigen van asset(s)&quot; op wanneer u de eigenschappen van de asset opslaat.

Om ervoor te zorgen dat de component correct in de vorm van het meta-gegevensschema wordt getoond, zou de bezitspad geen ruimten moeten omvatten.

* **Tijdelijke aanduiding**: Gebruik deze eigenschap om relevante plaatsaanduidingstekst met betrekking tot de eigenschap metadata op te geven.
* **Vereist**: Gebruik deze eigenschap om een eigenschap metadata als verplicht op de eigenschappenpagina te markeren.
* **Bewerken** uitschakelen: Met deze eigenschap kunt u bewerkingen van een eigenschap op de eigenschappenpagina niet toestaan.
* **Leeg veld alleen**-lezen tonen: Mark this property to display a metadata property on the properties page even if it has no value. Wanneer een eigenschap metadata geen waarde heeft, wordt deze standaard niet vermeld op de eigenschappenpagina.
* **Genummerde** lijst tonen: Gebruik deze eigenschap om een geordende lijst met keuzen weer te geven.
* **Keuzen**: Gebruik deze eigenschap om keuzen in een lijst op te geven.
* **Omschrijving** : Gebruik deze eigenschap om een korte beschrijving toe te voegen voor de metagegevenscomponent.
* **Klasse**: Objectklasse waaraan de eigenschap is gekoppeld.
* **Verwijderen**: Klik  [!UICONTROL Delete] om een component uit het schemaformulier te verwijderen.

>[!NOTE]
>
>De component [!UICONTROL Hidden Field] bevat deze kenmerken niet. In plaats daarvan bevat de klasse eigenschappen, zoals Naam, Waarde, Veldlabel en Beschrijving. De waarden voor de component Verborgen veld worden als een POST-parameter verzonden wanneer het element wordt opgeslagen. Deze wordt niet opgeslagen als metagegevens voor het element.

Als u de optie **[!UICONTROL Required]** selecteert, kunt u zoeken naar assets waarvoor verplichte metadata ontbreken. Vouw in het deelvenster **[!UICONTROL Filters]** het predicaat **[!UICONTROL Metadata Validation]** uit en selecteer de optie **[!UICONTROL Invalid]**. In de zoekresultaten worden assets weergegeven waarvoor verplichte metadata ontbreken die u via het schemaformulier hebt geconfigureerd.

Als u de component Contextuele metagegevens toevoegt aan een tabblad van een schemaformulier, wordt de component weergegeven als een lijst op de eigenschappenpagina van elementen waarop het specifieke schema wordt toegepast. De lijst bevat alle andere tabbladen, behalve het tabblad waarop u de component Contextuele metagegevens hebt toegepast. Momenteel biedt deze functie basisfunctionaliteit voor het beheren van de weergave van metagegevens op basis van de context.

Als u een tabblad in de eigenschappenpagina wilt weergeven naast het tabblad waarop de component Contextuele metagegevens is toegepast, selecteert u het tabblad in de lijst. Het tabblad wordt toegevoegd aan de pagina met eigenschappen.

### Eigenschappen opgeven in JSON-bestand {#specify-properties-in-json-file}

In plaats van eigenschappen voor de opties op het tabblad **[!UICONTROL Settings]** op te geven, kunt u de opties in een JSON-bestand definiëren door overeenkomstige sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL JSON Path]**.

#### Een tabblad toevoegen aan of verwijderen uit het schemaformulier {#add-delete-a-tab-in-the-schema-form}

Met de schema-editor kunt u een tabblad toevoegen of verwijderen. De standaardschemavorm omvat **[!UICONTROL Basic]**, **[!UICONTROL Advanced]**, **[!UICONTROL IPTC]**, en **[!UICONTROL IPTC Extension]** lusjes.

![Standaardtabbladen in het metagegevensschema](assets/metadata-schema-form-tabs.png)

Klik `+` om een lusje op een schemavorm toe te voegen. Standaard heeft het nieuwe tabblad de naam `Unnamed-1`. U kunt de naam wijzigen op het tabblad **[!UICONTROL Settings]**. Klik `X` om een tabel te verwijderen.

![Een tabblad toevoegen of verwijderen met de Editor voor een metagegevensschema](assets/metadata-schema-form-new-tab.png)

## Formulieren met metagegevensschema {#deleting-metadata-schema-forms} verwijderen

Met AEM kunt u alleen aangepaste schema-formulieren verwijderen. U kunt hiermee de standaardschema-formulieren/sjablonen niet verwijderen. U kunt echter alle aangepaste wijzigingen in deze formulieren verwijderen.

Als u een formulier wilt verwijderen, selecteert u een formulier en klikt u op het pictogram voor verwijderen.

>[!NOTE]
>
>Nadat u aangepaste wijzigingen in een standaardformulier hebt verwijderd, verschijnt het vergrendelingspictogram opnieuw vóór de aangepaste wijzigingen in het schema voor metagegevens om aan te geven dat de standaardstatus van het formulier is hersteld.

>[!NOTE]
>
>* Nadat u aangepaste wijzigingen in een standaardformulier hebt verwijderd, wordt de vergrendeling ![lock closed](assets/do-not-localize/lock_closed_icon.svg) opnieuw weergegeven vóór het formulier. Hiermee wordt aangegeven dat de standaardstatus van het formulier wordt hersteld.
>* U kunt de standaardformulieren voor het metagegevensschema niet verwijderen in [!DNL Assets].


## Schemaformulieren voor MIME-typen {#schema-forms-for-mime-types}

[!DNL Experience Manager] bevat standaardformulieren voor diverse MIME-typen uit het vak. U kunt echter aangepaste formulieren toevoegen voor elementen van verschillende MIME-typen.

### Nieuwe formulieren toevoegen voor MIME-typen {#adding-new-forms-for-mime-types}

Maak een formulier onder het juiste formuliertype. Als u bijvoorbeeld een sjabloon wilt toevoegen voor het subtype `image/png`, maakt u het formulier onder de &quot;afbeeldingsformulieren&quot;. De titel voor het schemaformulier is de naam van het subtype. In dit geval is de titel `png`.

#### Een bestaande schemasjabloon gebruiken voor verschillende MIME-typen {#use-an-existing-schema-template-for-various-mime-types}

U kunt een bestaande sjabloon voor een ander MIME-type gebruiken. Gebruik bijvoorbeeld het formulier `image/jpeg` voor elementen van het MIME-type `image/png`.

In dit geval maakt u een knooppunt op `/etc/dam/metadataeditor/mimetypemappings` in de CRX-opslagplaats. Geef een naam voor het knooppunt op en definieer de volgende eigenschappen:

| Naam | Beschrijving | Type | Waarde |
|------|-------------|------|-------|
| `exposedmimetype` | Naam van het bestaande formulier dat moet worden toegewezen | `String` | `image/jpeg` |
| `mimetypes` | Lijst met MIME-typen die het formulier gebruiken dat is gedefinieerd in het kenmerk `exposedmimetype` | `String` | `image/png` |

[!DNL Assets] Hiermee worden de volgende MIME-typen en schema-formulieren toegewezen:

| Schema-formulier | MIME-typen |
|---|---|
| image/jpeg | image/pjpeg |
| image/tiff | image/x-tiff |
| application/pdf | application/postscript |
| application/x-ImageSet | Multipart/aanverwante; type=application/x-ImageSet |
| application/x-SpinSet | Multipart/aanverwante; type=application/x-SpinSet |
| application/x-MixedMediaSet | Multipart/aanverwante; type=application/x-MixedMediaSet |
| video/quicktime | video/x-quicktime |
| video/mpeg4 | video/mp4 |
| video/avi | video/avi, video/msvideo, video/x-msvideo |
| video/wmv | video/x-ms-wmv |
| video/flv | video/x-flv |

## Toegang verlenen tot metagegevensschema&#39;s {#grant-access-to-metadata-schemas}

De functie Metagegevensschema is alleen beschikbaar voor beheerders. Beheerders kunnen echter toegang verlenen aan niet-beheerders door bepaalde machtigingen te wijzigen. Verstrek de niet beheerdergebruikers tot toestemmingen op `/conf` leiden, wijzigen en schrappen.

## Mapspecifieke metagegevens toepassen {#applying-folder-specific-metadata}

[!DNL Assets] Hiermee kunt u een variant van een metagegevensschema definiëren en dit toepassen op een specifieke map.

U kunt bijvoorbeeld een variant van het standaardmetagegevensschema definiëren en deze toepassen op een map. Wanneer u het gewijzigde schema toepast, wordt het oorspronkelijke standaardmetagegevensschema genegeerd dat op elementen in de map is toegepast.

Alleen elementen die zijn geüpload naar de map waarop dit schema is toegepast, komen overeen met de gewijzigde metagegevens die zijn gedefinieerd in het schema voor alternatieve metagegevens. [!DNL Assets] in andere mappen waarin het oorspronkelijke schema wordt toegepast, blijven de metagegevens die in het oorspronkelijke schema zijn gedefinieerd, behouden.

Metagegevensovererving door elementen is gebaseerd op het schema dat wordt toegepast op de map op het hoogste niveau in de hiërarchie. Hetzelfde schema wordt toegepast op of overgeërfd door de submappen. Als een ander schema op submapniveau wordt toegepast, stopt de overerving.

1. Navigeer in [!DNL Experience Manager] interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Schakel het selectievakje in vóór een formulier, bijvoorbeeld het standaardmetagegevensformulier, en klik op **[!UICONTROL Copy]** en sla het op als een aangepast formulier. Geef een aangepaste naam voor het formulier op, bijvoorbeeld `my_default`. U kunt ook een aangepast formulier maken.

1. Selecteer op de pagina **[!UICONTROL Metadata Schema Forms]** het formulier `my_default` en klik vervolgens op **[!UICONTROL Edit]**.
1. Voeg op de pagina **[!UICONTROL Metadata Schema Editor]** een tekstveld toe aan het schema. Voeg bijvoorbeeld een veld met het label **[!UICONTROL Category]** toe.
1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]**.
1. Klik/tik **[!UICONTROL Apply to Folder(s)]** van de toolbar om de douanemetagegevens op een omslag toe te passen.
1. Selecteer de map waarop u het gewijzigde schema wilt toepassen en klik op **[!UICONTROL Apply]**.
1. Als op de map het andere metagegevensschema is toegepast, verschijnt er een waarschuwing dat u op het punt staat het bestaande metagegevensschema te overschrijven. Klik **Overschrijven**.
1. Klik **OK** om het succesbericht te sluiten.
1. Navigeer naar de map waarop u het gewijzigde metagegevensschema hebt toegepast.

## Verplichte metagegevens definiëren {#defining-mandatory-metadata}

U kunt verplichte velden definiëren op mapniveau. Deze worden afgedwongen voor elementen die naar de map worden geüpload. Als u elementen uploadt met ontbrekende metagegevens voor de verplichte velden die u eerder hebt gedefinieerd, wordt een visuele indicatie voor ontbrekende metagegevens weergegeven in de weergave Kaart.

>[!NOTE]
>
>Een metagegevensveld kan op basis van de waarde van een ander veld als verplicht worden gedefinieerd. In de weergave Kaarten geeft AEM het waarschuwingsbericht over ontbrekende metagegevens voor dergelijke verplichte metagegevensvelden niet weer.

1. Klik op het AEM-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Schemas]**. De pagina **[!UICONTROL Metadata Schema Forms]** wordt weergegeven.
1. Sla het standaardmetagegevensformulier op als een aangepast formulier. Sla het bestand bijvoorbeeld op als `my_default`.
1. Bewerk het aangepaste formulier. Voeg een verplicht veld toe. Voeg bijvoorbeeld een veld **[!UICONTROL Category]** toe en maak het veld verplicht.
1. Klik op **[!UICONTROL Save]**. Het gewijzigde formulier wordt weergegeven op de pagina **[!UICONTROL Metadata Schema Forms]**. Selecteer het formulier en klik of tik op **[!UICONTROL Apply to Folder(s)]** op de werkbalk om de aangepaste metagegevens toe te passen op een map.
1. Navigeer naar de map en upload elementen met ontbrekende metagegevens voor het verplichte veld dat u aan het aangepaste formulier hebt toegevoegd. Er wordt een bericht voor de ontbrekende metagegevens van het verplichte veld weergegeven in de kaartweergave van het element.
1. (Optioneel) Toegang `https://[server]:[port]/system/console/components/`. Configureer en schakel `com.day.cq.dam.core.impl.MissingMetadataNotificationJob` component in die standaard is uitgeschakeld. Stel een frequentie in waarmee AEM controleert of metagegevens over de elementen geldig zijn.

   Bij deze configuratie wordt een eigenschap `hasValidMetadata` aan `jcr:content` elementen toegevoegd. Met deze eigenschap kunnen AEM resultaten in een zoekopdracht filteren.

   >[!NOTE]
   >
   >Als een element wordt toegevoegd na de geplande controle, wordt het element niet gemarkeerd met `hasValidMetadata` tot de volgende geplande controle. De elementen worden niet weergegeven in tussenliggende zoekresultaten.

   >[!CAUTION]
   >
   >De controles van de meta-gegevensbevestiging zijn middelintensief en kunnen de prestaties van uw systeem beïnvloeden. Plan de controles dienovereenkomstig. Als de server het laden niet aankan, probeert u deze taak uit te schakelen
