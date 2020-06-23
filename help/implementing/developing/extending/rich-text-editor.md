---
title: Vorm de Rich Text Editor aan auteursinhoud in [!DNL Adobe Experience Manager] als Cloud Service.
description: Vorm Rich Text Editor aan auteursinhoud in [!DNL Adobe Experience Manager] als Cloud Service.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 739dde6f9a6a7f4fe773e27e53f23a395f2881dc
workflow-type: tm+mt
source-wordcount: '1989'
ht-degree: 0%

---


# Configure the Rich Text Editor {#configure-the-rich-text-editor}

De Rich Text Editor (RTE) biedt auteurs een groot aantal functies voor het bewerken van tekstinhoud. Pictogrammen, selectiekaders, werkbalk en menu&#39;s zijn beschikbaar voor een WYSIWYG-ervaring bij het bewerken van tekst. De beheerders vormen RTE om, de eigenschappen toe te laten onbruikbaar te maken en uit te breiden beschikbaar in de auteurscomponenten. Zie hoe ontwerpers RTE [gebruiken voor het ontwerpen](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md) van webinhoud.

De concepten en de stappen van RTE die worden vereist om het te vormen zijn hieronder vermeld.

| Begrijp de concepten van RTE | Vereiste functies inschakelen | Afzonderlijke functies configureren |
|---|---|---|
| [Begrijp de interface](#understand-rte-ui) | [Configuratielocaties begrijpen en instellen](#understand-the-configuration-paths-and-locations) | [Plug-ins configureren](#enable-rte-functionalities-by-activating-plug-ins) |
| [Typen bewerkmodi](#editingmodes) | [Plug-ins activeren](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [Eigenschappen van functie instellen](#aboutplugins) |
| [Plug-ins](#aboutplugins) | [RTE-werkbalken configureren](#dialogfullscreen) | [De plakmodi configureren](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

## Begrijp de gebruikersinterface beschikbaar aan auteurs {#understand-rte-ui}

De interface RTE biedt een [ontvankelijk ontwerp](/help/sites-cloud/authoring/features/responsive-layout.md) voor auteursmilieu aan. De interface is ontworpen voor gebruik op touch- en desktopapparaten.

![Rich Text Editor, werkbalk](assets/rte-toolbar-full-screen-mode.png)

*Afbeelding: De werkbalk van de Rich Text Editor met alle beschikbare opties ingeschakeld.*

De werkbalk bevat de opties voor de WYSIWYG-ontwerpervaring. [!DNL Experience Manager] beheerders kunnen de opties vormen beschikbaar in de toolbar op de interface. Er is standaard een uitgebreide set bewerkingsopties beschikbaar in [!DNL Experience Manager]. Ontwikkelaars kunnen aanpassen [!DNL Experience Manager] om meer bewerkingsopties toe te voegen.

## Verschillende bewerkingsmodi {#editingmodes}

Auteurs kunnen tekstinhoud maken en bewerken in de verschillende modi van componenten. [!DNL Experience Manager] De toolbaropties voor het ontwerpen en het formatteren van inhoud en de gebruikerservaring van rte-toegelaten componenten op verschillende het uitgeven wijze variëren gebaseerd op configuraties RTE.

| Bewerkmodus | Bewerkingsgebied | Aanbevolen functies om te worden ingeschakeld |
|--- |--- |--- |
| Inline | Op locatie bewerken voor snelle, kleine bewerkingen; Opmaken zonder dialoogvenster te openen. | Minimale RTE-functies. |
| RTE volledig scherm | Behandelt de gehele pagina. | Alle vereiste eigenschappen van RTE. |
| Dialoog | Het dialoogvenster boven op de pagina-inhoud, maar beslaat niet de gehele pagina. | Schakel functies correct in. |
| Dialoogvenster op volledig scherm | Hetzelfde als de modus Volledig scherm; bevat gebieden van de dialoog naast RTE. | Alle vereiste eigenschappen van RTE. |

>[!NOTE]
>
>De functie voor bronbewerking is niet beschikbaar in de inline bewerkingsmodus. U kunt afbeeldingen niet slepen in de modus Volledig scherm. Alle andere functies werken in alle modi.

### Inline bewerken {#inline-editing}

Als u de inhoud binnen een pagina wilt bewerken, opent u de inhoud met een langzame dubbelklik. Er wordt een compacte werkbalk met basisopties weergegeven.

![Inline bewerken met de basisopties op de werkbalk](assets/inline-editing-mode-basic-options.png)

*Afbeelding: Inline bewerken met de basisopties op de werkbalk.*

### Volledig scherm bewerken {#full-screen-editing}

[!DNL Experience Manager] kunnen worden geopend in de weergave Volledig scherm, waarin de pagina-inhoud wordt verborgen en het beschikbare scherm wordt ingenomen. U kunt overwegen een gedetailleerde versie van de inlinebewerking op volledig scherm te bewerken, aangezien deze de meeste bewerkingsopties biedt. U kunt deze openen door op ![Pictogram te klikken om RTE op volledig scherm](assets/rte_fullscreen.png)te openen, vanuit de compacte werkbalk wanneer u de inline bewerkingsmodus gebruikt.

In de modus Volledig scherm van het dialoogvenster zijn, samen met een gedetailleerde RTE-werkbalk, ook de opties en componenten beschikbaar in een dialoogvenster. Het is alleen van toepassing voor een dialoog die naast andere componenten RTE bevat.

![De gedetailleerde RTE toolbar wanneer het uitgeven op volledig-schermwijze](assets/rte-toolbar-full-screen-mode.png)

*Afbeelding: De gedetailleerde RTE toolbar wanneer het uitgeven op volledig-schermwijze.*

### Dialoogbewerkingen {#dialog-editing}

Wanneer dubbelgeklikt wordt op een component, wordt een dialoogvenster geopend voor het bewerken van de inhoud. Het dialoogvenster wordt boven op de bestaande pagina geopend. In sommige specifieke scenario&#39;s, opent de dialoog als pop-up venster. Wanneer een tekstcomponent bijvoorbeeld deel uitmaakt van een kolom in een paginalay-out met meerdere kolommen en het gebied dat beschikbaar is voor het dialoogvenster kleiner is.

![Dialoogbewerkingsmodus](assets/dialog_editing_modetouchui.png)

*Afbeelding: De bewerkingsmodus van het dialoogvenster.*

## Informatie over RTE-plug-ins en de bijbehorende functies {#aboutplugins}

De functionaliteit wordt beschikbaar gesteld via een reeks plug-ins, elk met:

* Een `features` eigenschap, namelijk

   * Wordt gebruikt om de basisfunctionaliteit voor die plug-in te activeren of te deactiveren.
   * Gevormd gebruikend een gestandaardiseerde procedure.

* Indien van toepassing, meer eigenschappen en opties die gespecialiseerde configuratie vereisen.

De basiseigenschappen van RTE worden geactiveerd, of worden gedeactiveerd, door de waarde van het `features` bezit op een knoop specifiek voor de aangewezen stop-in.

In de volgende tabel worden de huidige plug-ins weergegeven:

* Plug-in-id&#39;s met een koppeling naar de API-documentatie. ID wordt gebruikt als de knooppuntnaam wanneer het [activeren van een stop-in](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin).
* Toegestane waarden voor de `features` eigenschap.
* Een beschrijving van de functionaliteit die door de plug-in wordt geboden.

| Plug-in-id | functies | Beschrijving |
|--- |--- |--- |
| bewerken | `cut`, `copy`, `paste-default`, `paste-plaintext`, `paste-wordhtml` | [Knip, kopieer en kopieer de drie plakmodi](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles). |
| [findreplace](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FindReplacePlugin) | `find`, `replace` | Zoeken en vervangen. |
| [format](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.FormatPlugin) | `bold`, `italic`, `underline` | [Basistekstopmaak](configure-rich-text-editor-plug-ins.md#textstyles). |
| [afbeelding](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ImagePlugin) | `image` | Basisondersteuning voor afbeeldingen (slepen vanuit de inhoud of de Inhoudszoeker). Afhankelijk van de browser heeft de ondersteuning verschillende gedragingen voor auteurs |
| [toetsen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.KeyPlugin) | - | Zie de [tabgrootte](configure-rich-text-editor-plug-ins.md#tabsize)om deze waarde te definiëren. |
| [justify](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.JustifyPlugin) | `justifyleft`, `justifycenter`, `justifyright` | Alinea-uitlijning. |
| [koppelingen](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.LinkPlugin) | `modifylink`, `unlink`, `anchor` | [Hyperlinks en ankers](configure-rich-text-editor-plug-ins.md#linkstyles). |
| [lijsten](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.ListPlugin) | `ordered`, `unordered`, `indent`, `outdent` | Deze insteekmodule bestuurt zowel de [inspringing als de lijsten](configure-rich-text-editor-plug-ins.md#indentmargin); inclusief geneste lijsten. |
| [misverstanden](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/widgets-api/index.html?class=CQ.form.rte.plugins.MiscToolsPlugin) | `specialchars`, `sourceedit` | Met diverse gereedschappen kunnen auteurs [speciale tekens](configure-rich-text-editor-plug-ins.md#spchar) invoeren of de HTML-bron bewerken. U kunt ook een [reeks speciale tekens](configure-rich-text-editor-plug-ins.md#definerangechar) toevoegen als u uw eigen lijst wilt definiëren. |
| Paraformat | `paraformat` | De standaardindelingen voor alinea&#39;s zijn Alinea, Kop 1, Kop 2 en Kop 3 (`<p>`, `<h1>`, `<h2>`en `<h3>`). U kunt meer alinea-indelingen [](configure-rich-text-editor-plug-ins.md#paraformats) toevoegen of de lijst uitbreiden. |
| spellingcontrole | `checktext` | [Spellingcontrole](configure-rich-text-editor-plug-ins.md#adddict)met behoud van taal. |
| stijlen | `styles` | Ondersteuning voor opmaak met behulp van een CSS-klasse. [Voeg nieuwe tekststijlen](configure-rich-text-editor-plug-ins.md#textstyles) toe als u uw eigen reeks stijlen voor gebruik met tekst wilt toevoegen (of uitbreiden). |
| subsuperscript | `subscript`, `superscript` | Extensies voor de basisindelingen, subscript en superscript toevoegen. |
| table | `table`, `removetable`, `insertrow`, `removerow`, `insertcolumn`, `removecolumn`, `cellprops`, `mergecells`, `splitcell`, `selectrow`, `selectcolumns` | Zie tabelstijlen [](configure-rich-text-editor-plug-ins.md#tablestyles) configureren om uw eigen stijlen voor gehele tabellen of afzonderlijke cellen toe te voegen. |
| ongedaan maken | `undo`, `redo` | Grootte historie van bewerkingen voor [ongedaan maken en opnieuw uitvoeren](configure-rich-text-editor-plug-ins.md#undohistory) . |

>[!NOTE]
>
>De plug-in Volledig scherm wordt niet ondersteund in de dialoogmodus. Gebruik de `dialogFullScreen` instelling om de werkbalk voor de modus Volledig scherm te configureren.

## Begrijp de configuratiewegen en plaatsen {#understand-the-configuration-paths-and-locations}

De [wijze van het uitgeven van RTE en de interface](#editingmodes) die u voor uw auteurs verstrekt bepalen de plaats voor de configuratiedetails wanneer u de stop-ins [van RTE](configure-rich-text-editor-plug-ins.md#activateplugin)activeert. De locaties zijn:

* Inline-modus: `cq:editConfig/cq:inplaceEditing`.
* Modus Volledig scherm: `cq:editConfig/cq:inplaceEditing`.
* Dialoogvenstermodus: `cq:dialog`.
* Dialoogmodus Volledig scherm: `cq:dialog`.

>[!NOTE]
>
>Geef het knooppunt onder niet de naam `cq:inplaceEditing` als `config`. Definieer bij `cq:inplaceEditing` knooppunt de volgende eigenschappen:
>
>* **Naam**: `configPath`
>* **Type**: `String`
>* **Waarde**: pad van het knooppunt met de feitelijke configuratie
>
>
Noem niet de de configuratieknoop van RTE zoals `config`. Anders, worden de configuraties RTE van kracht voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

Configureer de volgende eigenschappen die van toepassing zijn in de bewerkingsmodus van dialoogvenster:

* `useFixedInlineToolbar`: U kunt de werkbalk RTE vast maken in plaats van zwevend. Plaats dit bezit Van Boole dat op de knoop RTE met het verbinden wordt bepaald:resourceType= `cq/gui/components/authoring/dialog/richtext` aan `True`. Wanneer deze eigenschap is ingesteld op `True`, wordt het bewerken van RTF-gegevens gestart voor de `foundation-contentloaded` gebeurtenis. Om dit te verhinderen, plaats het bezit `customStart` aan `True` en teweegbrengt de `rte-start` gebeurtenis om RTE het uitgeven te beginnen. Wanneer dit bezit is `true`, begint RTE niet bij het klikken en dit is het standaardgedrag.

* `customStart`: Plaats dit bezit Van Boole dat op de knoop RTE aan wordt bepaald, om te controleren wanneer om RTE te beginnen door de gebeurtenis te teweegbrengen `True``rte-start`.

* `rte-start`: Trigger deze gebeurtenis op de `contenteditable-div` van RTE, wanneer beginnen RTE uit te geven. Het werkt alleen als `customStart` is ingesteld op `true`.

Wanneer RTE in de aanraking-toegelaten dialoog wordt gebruikt, plaats het bezit `useFixedInlineToolbar` om kwesties `true` te vermijden.

## RTE-functies inschakelen door plug-ins te activeren {#enable-rte-functionalities-by-activating-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt de eigenschap features configureren om de verschillende functies van elke insteekmodule in of uit te schakelen.

Voor gedetailleerde configuraties van de stop-ins van RTE, zie [hoe te om de stop-ins](configure-rich-text-editor-plug-ins.md)van RTE te activeren en te vormen.

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

De de tekstcomponent [van Componenten van de](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) Kern laat malplaatjeredacteurs om vele stop-ins te vormen RTE gebruikend het gebruikersinterface als inhoudsbeleid, eliminerend de behoefte aan technische configuratie. Het inhoudsbeleid kan werken met RTE UI-configuraties zoals in dit document wordt beschreven. Voor meer informatie, zie [creeer paginasjablonen](/help/sites-cloud/authoring/features/templates.md) en de de ontwikkelaarsdocumentatie [van de Componenten van de](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/developing.html)Kern.

>Ter referentie kunt u de standaardtekstcomponenten (geleverd als onderdeel van een standaardinstallatie) vinden op:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>
Als u uw eigen tekstcomponent wilt maken, kopieert u de bovenstaande component in plaats van deze componenten te bewerken.

## RTE-werkbalk configureren {#dialogfullscreen}

[!DNL Experience Manager] Hiermee kunt u de interface voor de Rich Text Editor op een andere manier configureren voor de verschillende bewerkingsmodi. De standaardinstellingen worden hieronder gegeven. U kunt deze standaardinstellingen op basis van uw vereisten overschrijven. U kunt alleen de werkbalkfuncties aanpassen die u aan de auteurs wilt geven. U hoeft niet alle werkbalkconfiguraties op te geven.

Gebruik de volgende voorbeeldconfiguratie om de werkbalk voor `dialogFullScreen`te configureren.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Er worden verschillende instellingen voor de gebruikersinterface gebruikt voor de inlinemodus en de modus Volledig scherm. Met de eigenschap toolbar geeft u de optie van de werkbalk op.

Als de optie zelf bijvoorbeeld een functie is (bijvoorbeeld `Bold`), wordt deze opgegeven als `PluginName#FeatureName` (bijvoorbeeld `links#modifylink`).

Als de optie een pop-up is (met enkele functies van een plug-in), wordt deze opgegeven als `#PluginName` (bijvoorbeeld `#format`).

U kunt scheidingstekens (`|`) tussen een groep opties opgeven met `-`.

Het pop-upknooppunt onder de modus Inline of Volledig scherm bevat een lijst met de pop-upovers die worden gebruikt. Elk onderliggend knooppunt onder het `popovers` knooppunt krijgt een naam na de insteekmodule (bijvoorbeeld de indeling). Deze heeft een eigenschap &#39;items&#39; die een lijst bevat met functies van de plug-in (bijvoorbeeld format#bold).

## RTE-gebruikersinterface-instellingen en inhoudsbeleid {#rtecontentpolicies}

De beheerders kunnen de opties controleren RTE gebruikend inhoudsbeleid, zeggen in plaats van de configuratie zoals hierboven beschreven. In het inhoudsbeleid worden de ontwerpeigenschappen van een component gedefinieerd wanneer deze worden gebruikt als onderdeel van een [bewerkbare sjabloon](/help/sites-cloud/authoring/features/templates.md). Als bijvoorbeeld een tekstcomponent die de RTE gebruikt wordt gebruikt met een bewerkbare sjabloon, kan het inhoudsbeleid definiëren dat de optie Vet beschikbaar is en zijn enkele opties voor alineaopmaak beschikbaar. Het inhoudsbeleid is herbruikbaar en kan op meerdere sjablonen worden toegepast.

De beschikbare opties in RTE stromen stroomafwaarts van de configuraties van het gebruikersinterface aan het inhoudsbeleid.

* De de configuratiemontages van de gebruikersinterface bepalen welke opties aan het inhoudsbeleid beschikbaar zijn.
* Als de gebruikersinterfaceconfiguratie van RTE verwijderde of geen punt toelaat, kan het inhoudsbeleid niet het vormen.
* Een auteur heeft toegang tot slechts dergelijke functionaliteit die door de gebruikersinterfaceconfiguraties en het inhoudsbeleid ter beschikking wordt gesteld.

Als voorbeeld kunt u de documentatie [van de Component van de](https://docs.adobe.com/help/en/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor)Kern van de Tekst zien.

## Toewijzing aanpassen tussen werkbalkpictogrammen en -opdrachten {#iconstoolbar}

U kunt de afbeelding aanpassen tussen de koraalpictogrammen die worden weergegeven op de RTE-werkbalk en de beschikbare opdrachten. U kunt geen andere pictogrammen gebruiken behalve Koraalpictogrammen.

1. Maak een knooppunt met de naam `icons` under `uiSettings/cui`.

1. Maak knooppunten voor afzonderlijke pictogrammen eronder.
1. Geef voor elk van de afzonderlijke pictogramknooppunten een koraalpictogram en een opdracht op om aan het pictogram toe te wijzen.

Hieronder ziet u een voorbeeldfragment waarmee u de opdracht toewijst `Bold` aan het pictogram Koraal met de naam `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true">
    <rtePlugins jcr:primaryType="nt:unstructured">
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/>
    </rtePlugins>
    <uiSettings jcr:primaryType="nt:unstructured">
        <cui jcr:primaryType="nt:unstructured">
            <inline jcr:primaryType="nt:unstructured"
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]">
            </inline>
            <icons jcr:primaryType="nt:unstructured">
                <bold jcr:primaryType="nt:unstructured"
                    command="format#bold"
                    icon="textItalic"/>
            </icons>
        </cui>
    </uiSettings>
</text>
```

## Bekende beperkingen {#known-limitations}

[!DNL Experience Manager] Het vermogen van RTE heeft de volgende beperkingen:

* RTE-mogelijkheden worden alleen ondersteund in [!DNL Experience Manager] componentdialoogvensters. RTE wordt niet gesteund op tovenaars of stichting-vormen.

* [!DNL Experience Manager] werkt niet op hybride apparaten. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* Geef het RTE-configuratieknooppunt geen naam `config`. Anders, treedt de configuratie RTE voor slechts de beheerders en niet voor de gebruikers in de groep van kracht `content-author`.

* RTE ondersteunt het insluiten van inhoud in een inline-frame of iframe niet.

## Tips en trucs {#best-practices-and-tips}

* Voor een zwevend dialoogvenster schakelt u alleen de plug-ins zonder pop-updialoogvenster in. Plug-ins zonder pop-up zijn kleiner en zijn het meest geschikt voor een zwevend dialoogvenster.
* Schakel de plug-ins met grotere pop-ups, zoals de `Paste` plug-in, alleen in de modus Volledig scherm of in de modus Volledig scherm in. Plug-ins met een grote pop-up hebben meer ruimte in het scherm nodig voor een goede ontwerpervaring.
* Gebruik de `rte.coralui3` bibliotheek als u aangepaste plug-ins voor CoralUI3 RTE gebruikt.

>[!MORELIKETHIS]
>
>* [RTE-plug-ins configureren](configure-rich-text-editor-plug-ins.md)
>* [Rich Text Editor gebruiken voor ontwerpen](/help/sites-cloud/authoring/fundamentals/rich-text-editor.md)
>* [RTE voor toegankelijke sites configureren](rte-accessible-content.md)
>* [Zelfstudie als voorbeeld voor het maken van een samengestelde component met meerdere velden](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)

