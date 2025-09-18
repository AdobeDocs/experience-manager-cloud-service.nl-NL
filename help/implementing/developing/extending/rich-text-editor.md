---
title: Vorm de Rijke Redacteur van de Tekst aan auteursinhoud in  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Vorm de Rich Redacteur van de Tekst aan auteursinhoud in  [!DNL Adobe Experience Manager]  as a Cloud Service.
contentOwner: AG
exl-id: 1f0ff800-5e95-429a-97f2-221db0668170
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 2c1b444d7b7dad94cc9ebda59783f9c6fde84a91
workflow-type: tm+mt
source-wordcount: '1892'
ht-degree: 0%

---


# De Rich Text Editor configureren {#configure-the-rich-text-editor}

De Rich Text Editor (RTE) biedt auteurs een groot aantal functies voor het bewerken van tekstinhoud. Pictogrammen, selectiekaders, werkbalk en menu&#39;s zijn beschikbaar voor een WYSIWYG-ervaring voor tekstbewerking. De beheerders vormen RTE om, de eigenschappen toe te laten onbruikbaar te maken en uit te breiden beschikbaar in de auteurscomponenten. Zie hoe de auteurs [ RTE voor creatie ](/help/sites-cloud/authoring/page-editor/rich-text-editor.md) webinhoud gebruiken.

De concepten en de stappen van RTE die worden vereist om het te vormen zijn hieronder vermeld.

| Begrijp de concepten van RTE | Vereiste functies inschakelen | Afzonderlijke functies configureren |
|---|---|---|
| [ begrijp de interface ](#understand-rte-ui) | [ Begrijp en plaats config plaatsen plaatsen ](#understand-the-configuration-paths-and-locations) | [ vorm stop-ins ](#enable-rte-functionalities-by-activating-plug-ins) |
| [ Types van het uitgeven wijzen ](#editingmodes) | [ activeer stop-ins ](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin) | [ plaats eigenschapeigenschappen ](#aboutplugins) |
| [ Ongeveer stop-ins ](#aboutplugins) | [ vorm RTE toolbars ](#dialogfullscreen) | [ vorm de deegwijzen ](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles) |

>[!NOTE]
>
>De RTE die in dit document wordt beschreven, beschrijft de RTE die beschikbaar is in de Pagina-editor. Als u de moderne Universele Redacteur gebruikt, te zien gelieve het document [ Vormend RTE voor de Universele Redacteur ](/help/implementing/universal-editor/configure-rte.md) voor details.

## Begrijp de gebruikersinterface beschikbaar aan auteurs {#understand-rte-ui}

De interface RTE biedt a [ ontvankelijk ontwerp ](/help/sites-cloud/authoring/page-editor/responsive-layout.md) voor auteursmilieu aan. De interface is ontworpen voor gebruik op touch- en desktopapparaten.

![ Rich Text Editor toolbar ](assets/rte-toolbar-full-screen-mode.png)

*Cijfer: De rijke toolbar van de Redacteur van de Tekst met alle beschikbare toegelaten opties.*

De werkbalk bevat opties voor de WYSIWYG-ontwerpervaring. [!DNL Experience Manager] beheerders kunnen de opties vormen beschikbaar in de toolbar op de interface. In [!DNL Experience Manager] is standaard een uitgebreide set bewerkingsopties beschikbaar. Ontwikkelaars kunnen [!DNL Experience Manager] aanpassen om meer bewerkingsopties toe te voegen.

## Verschillende bewerkingsmodi {#editingmodes}

Auteurs kunnen tekstinhoud in [!DNL Experience Manager] maken en bewerken met de verschillende modi van componenten. De toolbaropties voor het ontwerpen en het formatteren van inhoud en de gebruikerservaring van rte-toegelaten componenten op verschillende het uitgeven wijze variëren gebaseerd op configuraties RTE.

| Bewerkmodus | Bewerkingsgebied | Aanbevolen functies om te worden ingeschakeld |
|--- |--- |--- |
| Inline | Lokaal bewerken voor snelle, kleine bewerkingen; opmaken zonder een dialoogvenster te openen. | Minimale RTE-functies. |
| RTE volledig scherm | Behandelt de gehele pagina. | Alle vereiste eigenschappen van RTE. |
| Dialoog | Het dialoogvenster boven op de pagina-inhoud, maar beslaat niet de gehele pagina. | Schakel functies correct in. |
| Dialoogvenster op volledig scherm | Hetzelfde als de modus Volledig scherm; bevat velden van het dialoogvenster naast RTE. | Alle vereiste eigenschappen van RTE. |

>[!NOTE]
>
>De functie voor bronbewerking is niet beschikbaar in de inline bewerkingsmodus. U kunt afbeeldingen niet naar het volledige scherm slepen. Alle andere functies werken in alle modi.

### Inline bewerken {#inline-editing}

Als u de inhoud binnen een pagina wilt bewerken, opent u de inhoud met een langzame dubbelklik. Er wordt een compacte werkbalk met basisopties weergegeven.

![ Inline het uitgeven met basisopties in de toolbar ](assets/inline-editing-mode-basic-options.png)

*Cijfer: Het gealigneerde uitgeven met basisopties in de toolbar.*

### Volledig scherm bewerken {#full-screen-editing}

[!DNL Experience Manager] -componenten kunnen worden geopend in de weergave Volledig scherm, waarin de pagina-inhoud wordt verborgen en het beschikbare scherm wordt ingenomen. U kunt overwegen een gedetailleerde versie van de inlinebewerking op volledig scherm te bewerken, aangezien deze de meeste bewerkingsopties biedt. Het kan worden geopend door ![ Pictogram te klikken om RTE in volledig-scherm ](assets/rte_fullscreen.png), van de compacte toolbar te openen wanneer het gebruiken van de gealigneerde het uitgeven wijze.

In de modus Volledig scherm van het dialoogvenster zijn, samen met een gedetailleerde RTE-werkbalk, ook de opties en componenten beschikbaar in een dialoogvenster. Het is alleen van toepassing voor een dialoog die naast andere componenten RTE bevat.

![ de gedetailleerde toolbar van RTE wanneer het uitgeven op volledig-schermwijze ](assets/rte-toolbar-full-screen-mode.png)

*Cijfer: De gedetailleerde toolbar van RTE wanneer het uitgeven op volledig-schermwijze.*

### Dialoogvenster bewerken {#dialog-editing}

Wanneer dubbelgeklikt wordt op een component, wordt een dialoogvenster geopend voor het bewerken van de inhoud. Het dialoogvenster wordt boven op de bestaande pagina geopend. In sommige specifieke scenario&#39;s, opent de dialoog als pop-up venster. Wanneer een tekstcomponent bijvoorbeeld deel uitmaakt van een kolom in een paginalay-out met meerdere kolommen en het gebied dat beschikbaar is voor het dialoogvenster kleiner is.

![ Dialoog het uitgeven wijze ](assets/dialog_editing_modetouchui.png)

*Cijfer: Dialoog het uitgeven wijze.*

## Informatie over RTE-plug-ins en de bijbehorende functies {#aboutplugins}

De functionaliteit wordt beschikbaar gesteld via een reeks plug-ins, elk met:

* Een eigenschap `features` , namelijk

   * Wordt gebruikt om de basisfunctionaliteit voor die plug-in te activeren of te deactiveren.
   * Gevormd gebruikend een gestandaardiseerde procedure.

* Indien van toepassing, meer eigenschappen en opties die gespecialiseerde configuratie vereisen.

De basisfuncties van de RTE worden geactiveerd of gedeactiveerd door de waarde van de eigenschap `features` op een knooppunt dat specifiek is voor de juiste insteekmodule.

In de volgende tabel worden de huidige plug-ins weergegeven:

* Plug-in-id&#39;s met een koppeling naar de API-documentatie. Identiteitskaart wordt gebruikt als knoopnaam wanneer [ het activeren van een elektrisch toestel ](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#activateplugin).
* Toegestane waarden voor de eigenschap `features` .
* Een beschrijving van de functionaliteit die door de plug-in wordt geboden.

| Plug-in-id | functies | Beschrijving |
|--- |--- |--- |
| bewerken | `cut`, `copy`, `paste-default`, `paste-plaintext`, `paste-wordhtml` | [ Besnoeiing, exemplaar en, de drie deegwijzen ](/help/implementing/developing/extending/configure-rich-text-editor-plug-ins.md#textstyles). |
| findreplace | `find`, `replace` | Zoeken en vervangen. |
| format | `bold`, `italic`, `underline` | [ Basis tekst het formatteren ](configure-rich-text-editor-plug-ins.md#textstyles). |
| image | `image` | Basisondersteuning voor afbeeldingen (slepen vanuit de inhoud of de Finder). Afhankelijk van de browser heeft de ondersteuning verschillende gedragingen voor auteurs |
| toetsen | - | Om deze waarde te bepalen, zie [ lusjegrootte ](configure-rich-text-editor-plug-ins.md#tabsize). |
| uitvullen | `justifyleft`, `justifycenter`, `justifyright` | Alinea-uitlijning. |
| koppelingen | `modifylink`, `unlink`, `anchor` | [ Hyperlinks en ankers ](configure-rich-text-editor-plug-ins.md#linkstyles). |
| lijsten | `ordered`, `unordered`, `indent`, `outdent` | Deze stop-binnen controleert zowel [ inspringing als lijsten ](configure-rich-text-editor-plug-ins.md#indentmargin); met inbegrip van genestelde lijsten. |
| misverstanden | `specialchars`, `sourceedit` | Diverse hulpmiddelen laten auteurs [ speciale karakters ](configure-rich-text-editor-plug-ins.md#spchar) ingaan of de bron van HTML uitgeven. Ook, kunt u a [ waaier van speciale karakters ](configure-rich-text-editor-plug-ins.md#definerangechar) toevoegen als u uw eigen lijst wilt bepalen. |
| Paraformat | `paraformat` | De standaardindelingen voor alinea&#39;s zijn Alinea, Kop 1, Kop 2 en Kop 3 (`<p>`, `<h1>`, `<h2>` en `<h3>`). U kunt [ meer paragraafformaten ](configure-rich-text-editor-plug-ins.md#paraformats) toevoegen of de lijst uitbreiden. |
| spelling | `checktext` | [ Taal bewuste spellingcontrole ](configure-rich-text-editor-plug-ins.md#adddict). |
| stijlen | `styles` | Ondersteuning voor opmaak met behulp van een CSS-klasse. [ voeg nieuwe tekststijlen ](configure-rich-text-editor-plug-ins.md#textstyles) toe als u (of breid) uw eigen waaier van stijlen voor gebruik met tekst wilt toevoegen. |
| subsuperscript | `subscript`, `superscript` | Extensies voor de basisindelingen, subscript en superscript toevoegen. |
| table | `table`, `removetable`, `insertrow`, `removerow`, `insertcolumn`, `removecolumn`, `cellprops`, `mergecells`, `splitcell`, `selectrow`, `selectcolumns` | Zie [ vormen lijststijlen ](configure-rich-text-editor-plug-ins.md#tablestyles) om uw eigen stijlen voor volledige lijsten of individuele cellen toe te voegen. |
| ongedaan maken | `undo`, `redo` | De grootte van de geschiedenis van [ maakt en doet ](configure-rich-text-editor-plug-ins.md#undohistory) verrichtingen ongedaan. |

>[!NOTE]
>
>De plug-in Volledig scherm wordt niet ondersteund in de dialoogmodus. Gebruik de instelling `dialogFullScreen` om de werkbalk voor de modus Volledig scherm te configureren.

## Begrijp de configuratiewegen en plaatsen {#understand-the-configuration-paths-and-locations}

De [ wijze van RTE het uitgeven en de interface ](#editingmodes) die u voor uw auteurs verstrekt beslist de plaats voor de configuratiedetails wanneer u [ de stop-ins van RTE ](configure-rich-text-editor-plug-ins.md#activateplugin) activeert. De locaties zijn:

* Inline-modus: `cq:editConfig/cq:inplaceEditing`.
* Modus Volledig scherm: `cq:editConfig/cq:inplaceEditing` .
* Dialoogvenstermodus: `cq:dialog`.
* Dialoogmodus Volledig scherm: `cq:dialog` .

>[!NOTE]
>
>Geef het knooppunt geen naam onder `cq:inplaceEditing` als `config` . Definieer bij knooppunt `cq:inplaceEditing` de volgende eigenschappen:
>
>* **Naam**: `configPath`
>* **Type**: `String`
>* **Waarde**: weg van de knoop die de daadwerkelijke configuratie bevatten
>
>Geef het RTE-configuratieknooppunt geen naam als `config` . Anders, zijn de configuraties RTE van kracht voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

Configureer de volgende eigenschappen die van toepassing zijn in de bewerkingsmodus van dialoogvenster:

* `useFixedInlineToolbar`: u kunt de werkbalk RTE laten vastzetten in plaats van zweven. Stel deze Booleaanse eigenschap in die op het RTE-knooppunt wordt gedefinieerd met sling :resourceType= `cq/gui/components/authoring/dialog/richtext` to `True` . Wanneer deze eigenschap is ingesteld op `True` , wordt de RTF-bewerking gestart voor de gebeurtenis `foundation-contentloaded` . Om dit te voorkomen, stelt u de eigenschap `customStart` in op `True` en activeert u de gebeurtenis `rte-start` om RTE-bewerking te starten. Wanneer deze eigenschap `true` is, begint RTE niet bij het klikken en dit is het standaardgedrag.

* `customStart`: stel deze Booleaanse eigenschap die op het RTE-knooppunt is gedefinieerd in op `True` om te bepalen wanneer RTE moet worden gestart door de gebeurtenis te activeren `rte-start` .

* `rte-start`: Trigger deze gebeurtenis op `contenteditable-div` van RTE, wanneer beginnen RTE uit te geven. Deze werkt alleen als `customStart` is ingesteld op `true` .

Wanneer u RTE gebruikt in het dialoogvenster met aanraakbediening, stelt u de eigenschap `useFixedInlineToolbar` in op `true` om problemen te voorkomen.

## RTE-functies inschakelen door plug-ins te activeren {#enable-rte-functionalities-by-activating-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt de eigenschap features configureren om de verschillende functies van elke insteekmodule in of uit te schakelen.

Voor gedetailleerde configuraties van de stop-ins van RTE, zie [ hoe te om de stop-ins van RTE te activeren en te vormen ](configure-rich-text-editor-plug-ins.md).

<!-- TBD ENGREVIEW: To confirm if the sample works in CS or not?
**Sample**: Download [this sample configuration](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) that illustrates how to configure RTE. In this package all the features are enabled. -->

De [ de tekstcomponent van Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=nl-NL#the-text-component-and-the-rich-text-editor) laat malplaatjeredacteurs om vele stop-ins te vormen RTE gebruikend het gebruikersinterface als inhoudsbeleid, die de behoefte aan technische configuratie elimineren. Het inhoudsbeleid kan werken met RTE UI-configuraties, zoals in dit document wordt beschreven. Voor meer informatie, zie [ paginasjablonen ](/help/sites-cloud/authoring/page-editor/templates.md) en de [ de ontwikkelaarsdocumentatie van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html?lang=nl-NL) creëren.

>Ter referentie kunt u de standaardtekstcomponenten (geleverd als onderdeel van een standaardinstallatie) vinden op:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>Als u uw eigen tekstcomponent wilt maken, kopieert u de bovenstaande component in plaats van deze componenten te bewerken.

## RTE-werkbalk configureren {#dialogfullscreen}

Met [!DNL Experience Manager] kunt u de interface voor de Rich Text Editor op verschillende manieren configureren voor de verschillende bewerkingsmodi. De standaardinstellingen worden hieronder gegeven. U kunt deze standaardinstellingen op basis van uw vereisten overschrijven. U kunt alleen de werkbalkfuncties aanpassen die u aan de auteurs wilt geven. U hoeft niet alle werkbalkconfiguraties op te geven.

Gebruik de volgende voorbeeldconfiguratie om de werkbalk voor `dialogFullScreen` te configureren.

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

Als de optie zelf bijvoorbeeld een functie is (bijvoorbeeld `Bold` ), wordt deze opgegeven als `PluginName#FeatureName` (bijvoorbeeld `links#modifylink` ).

Als de optie een pop-up is (met enkele functies van een plug-in), wordt deze opgegeven als `#PluginName` (bijvoorbeeld `#format` ).

Scheidingstekens (`|`) tussen een groep opties kunnen worden opgegeven met `-` .

Het pop-upknooppunt onder de modus Inline of Volledig scherm bevat een lijst met de pop-upovers die worden gebruikt. Elk onderliggend knooppunt onder het knooppunt `popovers` krijgt een naam na de insteekmodule (bijvoorbeeld de indeling). Deze heeft een eigenschap &#39;items&#39; die een lijst bevat met functies van de plug-in (bijvoorbeeld format#bold).

## RTE-gebruikersinterface-instellingen en inhoudsbeleid {#rtecontentpolicies}

De beheerders kunnen de opties controleren RTE gebruikend inhoudsbeleid, zeggen in plaats van de configuratie zoals hierboven beschreven. Het beleid van de inhoud bepaalt de ontwerpeigenschappen van een component wanneer gebruikt als deel van een [ editable malplaatje ](/help/sites-cloud/authoring/page-editor/templates.md). Als bijvoorbeeld een tekstcomponent die de RTE gebruikt wordt gebruikt met een bewerkbare sjabloon, kan het inhoudsbeleid definiëren dat de optie Vet beschikbaar is en zijn enkele opties voor alineaopmaak beschikbaar. Het inhoudsbeleid is herbruikbaar en kan op meerdere sjablonen worden toegepast.

De beschikbare opties in RTE stromen stroomafwaarts van de configuraties van het gebruikersinterface aan het inhoudsbeleid.

* De de configuratiemontages van de gebruikersinterface bepalen welke opties aan het inhoudsbeleid beschikbaar zijn.
* Als de gebruikersinterfaceconfiguratie van RTE verwijderde of geen punt toelaat, kan het inhoudsbeleid niet het vormen.
* Een auteur heeft toegang tot slechts dergelijke functionaliteit die door de gebruikersinterfaceconfiguraties en het inhoudsbeleid ter beschikking wordt gesteld.

Als voorbeeld, kunt u de [ documentatie van de Component van de Kern van de Tekst ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html?lang=nl-NL#the-text-component-and-the-rich-text-editor) zien.

## Toewijzing aanpassen tussen werkbalkpictogrammen en -opdrachten {#iconstoolbar}

U kunt de afbeelding aanpassen tussen de koraalpictogrammen die worden weergegeven op de RTE-werkbalk en de beschikbare opdrachten. U kunt geen andere pictogrammen gebruiken behalve Koraalpictogrammen.

1. Maak een knooppunt met de naam `icons` onder `uiSettings/cui` .

1. Maak knooppunten voor afzonderlijke pictogrammen eronder.
1. Geef voor elk van de afzonderlijke pictogramknooppunten een koraalpictogram en een opdracht op om aan het pictogram toe te wijzen.

Hieronder ziet u een voorbeeldfragment waarmee u de opdracht `Bold` toewijst aan het pictogram Koraal met de naam `textItalic` .

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

[!DNL Experience Manager] De mogelijkheid van RTE heeft de volgende beperkingen:

* RTE-mogelijkheden worden alleen ondersteund in dialoogvensters van [!DNL Experience Manager] -componenten. RTE wordt niet gesteund op tovenaars of stichting-vormen.

* [!DNL Experience Manager] werkt niet op hybride apparaten. <!-- TBD: Check. This is not mentioned in Known Issue /help/release-notes/known-issues.md-->

* Geef het RTE-configuratieknooppunt geen naam `config` . Anders, treedt de configuratie RTE voor slechts de beheerders en niet voor de gebruikers in de groep `content-author` van kracht.

* RTE ondersteunt het insluiten van inhoud in een inline-frame of iframe niet.

## Tips en trucs {#best-practices-and-tips}

* Voor een zwevend dialoogvenster schakelt u alleen de plug-ins in zonder een pop-updialoogvenster. Plug-ins zonder pop-up zijn kleiner en zijn het meest geschikt voor een zwevend dialoogvenster.
* Schakel de plug-ins met grotere pop-ups, zoals de plug-in `Paste` , alleen in de modus Volledig scherm of in de modus Volledig scherm in. Plug-ins met een grote pop-up hebben meer ruimte in het scherm nodig voor een goede ontwerpervaring.
* Gebruik de `rte.coralui3` -bibliotheek als u aangepaste plug-ins voor CoralUI3 RTE gebruikt.

>[!MORELIKETHIS]
>
>* [ vorm stop-ins RTE ](configure-rich-text-editor-plug-ins.md)
>* [ Redacteur van de Tekst van het Gebruik Rich voor creatie ](/help/sites-cloud/authoring/page-editor/rich-text-editor.md)
>* [ vorm RTE voor toegankelijke plaatsen ](rte-accessible-content.md)
