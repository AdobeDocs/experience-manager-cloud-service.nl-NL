---
title: Vorm de rijke stop-ins van de Redacteur van de Tekst in [!DNL Adobe Experience Manager].
description: Leer om de  [!DNL Adobe Experience Manager] Insteekmodules van de Redacteur van de RTF te vormen.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 6db201f00e8f304122ca8c037998b363ff102c1f
workflow-type: tm+mt
source-wordcount: '4279'
ht-degree: 0%

---


# Plug-insvan de Rich Text Editor configureren {#configure-the-rich-text-editor-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt het eigenschapbezit vormen om, één of meerdere eigenschappen van RTE toe te laten of onbruikbaar te maken. Dit artikel beschrijft hoe te om de stop-ins specifiek te vormen RTE.

Voor details over de andere configuraties RTE, zie [vormen Rich Text Editor](/help/implementing/developing/extending/rich-text-editor.md).

>[!NOTE]
>
>Als u met CRXDE Lite werkt, wordt aangeraden de wijzigingen regelmatig op te slaan met de optie [!UICONTROL Save All].

## Een insteekmodule activeren en de eigenschap featuresconfigureren {#activateplugin}

Voer de volgende stappen uit om een plug-in te activeren. Sommige stappen zijn alleen nodig wanneer u een insteekmodule voor het eerst configureert, omdat de bijbehorende knooppunten niet bestaan.

Standaard zijn `format`, `link`, `list`, `justify`, en `control` stop-ins en al hun eigenschappen toegelaten in RTE.

>[!NOTE]
>
>Het respectieve `rtePlugins` knooppunt wordt bedoeld als `<rtePlugins-node>` om dubbel werk in dit artikel te vermijden.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Creeer de ouderknoop van `<rtePlugins-node>` als het niet bestaat, alvorens om het even welke stop-ins te vormen RTE:

   * Afhankelijk van uw component zijn de bovenliggende knooppunten:

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * een alternatief configuratieknooppunt: `.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`
   * Zijn van type: **jcr:primaryType** `cq:Widget`
   * Beide hebben de volgende eigenschap:

      * **Naam** `name`
      * **Type** `String`
      * **Waarde** `./text`


1. Afhankelijk van de interface u voor vormt, creeer een knoop `<rtePlugins-node>`, als het niet bestaat:

   * **Naam** `rtePlugins`
   * **Type** `nt:unstructured`

1. Maak hieronder een knooppunt voor elke plug-in die u wilt activeren:

   * **Type** `nt:unstructured`
   * **Geef** de plug-in-id van de vereiste plug-in op.

Nadat u een insteekmodule hebt geactiveerd, volgt u deze richtlijnen om de eigenschap `features` te configureren.

|  | Alle functies inschakelen | Schakel een aantal specifieke functies in. | Alle functies uitschakelen. |
|---|---|---|---|
| Naam | functies | functies | functies |
| Type | Tekenreeks | `String` (meerdere tekenreeksen; Type instellen op  `String` en klikken  `Multi` in CRXDE Lite) | Tekenreeks |
| Waarde | `*` (een sterretje) | Instellen op een of meer functiewaarden. | - |

## Begrijp de findreplace plug-in {#findreplace}

Voor de `findreplace` plug-in is geen configuratie nodig. Het werkt uit de doos.

Wanneer u de vervangingsfunctie gebruikt, moet de te vervangen tekenreeks op hetzelfde moment worden ingevoerd als de zoektekenreeks. U kunt echter nog steeds op Zoeken klikken om de tekenreeks te zoeken voordat u deze vervangt. Als de vervangingstekenreeks wordt ingevoerd nadat op Zoeken is geklikt, wordt de zoekopdracht opnieuw ingesteld op het begin van de tekst.

Het dialoogvenster Zoeken en vervangen wordt transparant wanneer op Zoeken wordt geklikt en wordt dekkend wanneer op Vervangen wordt geklikt. Met dit gedrag kan de auteur de tekst controleren die moet worden vervangen. Als gebruikers op Alles vervangen klikken, wordt het dialoogvenster gesloten en wordt het aantal aangebrachte vervangingen weergegeven.

## De plakmodiconfigureren {#pastemodes}

Wanneer het gebruiken van RTE, kunnen de auteurs inhoud in één van de volgende drie wijzen kleven:

* **Browsermodus**: Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan.

* **Modus** Onbewerkte tekst: Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in de component [!DNL Experience Manager] worden ingevoegd.

* **MS Word-modus**: Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak.

### De beschikbare plakopties op de RTE-werkbalk configureren {#configure-paste-options-available-on-the-rte-toolbar}

U kunt sommige, alle, of geen van deze drie pictogrammen aan uw auteurs in de toolbar van RTE verstrekken:

* **[!UICONTROL Paste (Ctrl+V)]**: Kan vooraf worden geconfigureerd voor een van de drie bovenstaande plakmodi.

* **[!UICONTROL Paste as Text]**: Geeft functionaliteit voor de modus Onbewerkte tekst.

* **[!UICONTROL Paste from Word]**: Biedt functionaliteit in de modus MS Word.

Om RTE te vormen om de vereiste pictogrammen te tonen, volg deze stappen.

1. Navigeer naar de component, bijvoorbeeld `/apps/<myProject>/components/text`.
1. Navigeer naar het knooppunt `rtePlugins/edit`. Zie [Een insteekmodule activeren](#activateplugin) als het knooppunt niet bestaat.
1. Maak de eigenschap `features` op het knooppunt `edit` en voeg een of meer functies toe. Sla alle wijzigingen op.

### Het gedrag van het pictogram Plakken (Ctrl+V) en de sneltoetsconfigureren {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut}

U kunt het gedrag van het pictogram **[!UICONTROL Paste (Ctrl+V)]** vooraf configureren door de volgende stappen uit te voeren. Deze configuratie definieert ook het gedrag van sneltoetsen Ctrl+V die auteurs gebruiken om inhoud te plakken.

De configuratie staat voor de volgende drie soorten gebruiksgevallen toe:

* Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan. Gevormd gebruikend `browser` hieronder.

* Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in de component [!DNL Experience Manager] worden ingevoegd. Gevormd gebruikend `plaintext` hieronder.

* Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak. Gevormd gebruikend `wordhtml` hieronder.

1. Navigeer in uw component naar `<rtePlugins-node>/edit`-knooppunt. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. In de `edit` knoop creeer een bezit gebruikend de volgende details:

   * **Naam** `defaultPasteMode`
   * **Type** `String`
   * **** Waarden zijn een van de vereiste plakmodi  `browser`,  `plaintext`of  `wordhtml` modi.

### Configureer de toegestane indelingen bij het plakken van inhoud {#pasteformats}

De plakken-als-Microsoft-Word (`paste-wordhtml`) wijze kan verder worden gevormd zodat u uitdrukkelijk een paar stijlen kunt toestaan wanneer het kleven in [!DNL Experience Manager] van een ander programma, zoals [!DNL Microsoft Word].

Als u bijvoorbeeld alleen vette indelingen en lijsten wilt toestaan bij het plakken in [!DNL Experience Manager], kunt u de andere indelingen filteren. Dit wordt configureerbare het kleven het filtreren genoemd, die voor allebei kan worden gedaan:

* [Tekst](#pastemodes)
* [Koppelingen](#linkstyles)

Voor koppelingen kunt u ook de protocollen definiëren die automatisch worden geaccepteerd.

Om te vormen welke formaten worden toegestaan wanneer het kleven van tekst in [!DNL Experience Manager] van een ander programma:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/edit`. Maak de knooppunten als het knooppunt niet bestaat. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak een knooppunt onder het knooppunt `edit` voor de HTML-plakregels:

   * **Naam** `htmlPasteRules`
   * **Type** `nt:unstructured`

1. Maak een knooppunt onder `htmlPasteRules` voor de details van de toegestane basisindelingen:

   * **Naam** `allowBasics`
   * **Type** `nt:unstructured`

1. Als u de afzonderlijke geaccepteerde indelingen wilt beheren, maakt u een of meer van de volgende eigenschappen op het knooppunt `allowBasics`:

   * **Naam** `bold`
   * **Naam** `italic`
   * **Naam** `underline`
   * **Naam** `anchor`  (voor zowel koppelingen als benoemde ankers)
   * **Naam** `image`

   Alle eigenschappen zijn van **Type** `Boolean`, zodat kunt u in de juiste **Waarde** het vinkje selecteren of verwijderen om de functionaliteit in of uit te schakelen.

   >[!NOTE]
   >
   >Indien niet expliciet gedefinieerd, wordt de standaardwaarde true gebruikt en wordt de opmaak geaccepteerd.

1. Andere indelingen kunnen ook worden gedefinieerd met behulp van een reeks andere eigenschappen of knooppunten, die ook worden toegepast op het knooppunt `htmlPasteRules`:

| Eigenschap | Type | Beschrijving |
|--- |--- |--- |
| `allowBlockTags` | `String` | Hiermee definieert u de lijst met blokcodes die zijn toegestaan. Enkele mogelijke blokcodes zijn koppen (h1, h2, h3), alinea&#39;s (p), lijsten (ol, ul), tabellen (tabel). |
| `fallbackBlockTag` | `String` | Definieert de bloktag die wordt gebruikt voor alle blokken met een bloktag die niet in `allowBlockTags` zijn opgenomen. Meestal volstaat `p`. |
| `table` | `nt:unstructured` | Hiermee definieert u het gedrag bij het plakken van tabellen. Dit knooppunt moet de eigenschap allow (type Boolean) hebben om te bepalen of het plakken van tabellen is toegestaan. Als allow op false is ingesteld, moet u de eigenschap ignoreMode (type String) opgeven om te bepalen hoe geplakte tabelinhoud wordt verwerkt. Geldige waarden voor ignoreMode zijn `remove` om tabelinhoud te verwijderen en `paragraph` om tabelcellen om te zetten in alinea&#39;s. |
| `list` | `nt:unstructured` | Hiermee definieert u het gedrag bij het plakken van lijsten. U moet de eigenschap `allow` (type Boolean) hebben om te definiëren of het plakken van lijsten is toegestaan. Als `allow` aan `false` wordt geplaatst, specificeer het bezit `ignoreMode` (type `String`) om te bepalen hoe te om het even welke gekleefde lijsteinhoud te behandelen. De geldige waarden voor ignoreMode zijn `remove` die lijstinhoud verwijdert en `paragraph` die lijstpunten in paragrafen omzet. |

Hieronder ziet u een voorbeeld van een geldige `htmlPasteRules`-structuur:

```xml
"htmlPasteRules": {
    "allowBasics": {
        "italic": true,
        "link": true
    },
    "allowBlockTags": [
        "p", "h1", "h2", "h3"
    ],
    "list": {
        "allow": false,
        "ignoreMode": "paragraph"
    },
    "table": {
        "allow": true,
        "ignoreMode": "paragraph"
    }
}
```

1. Sla alle wijzigingen op.

## Tekststijlen configureren {#textstyles}

Auteurs kunnen stijlen toepassen om de weergave van een deel van de tekst te wijzigen. De stijlen zijn gebaseerd op CSS-klassen die u vooraf definieert in uw CSS-stijlpagina. Stileerde inhoud wordt ingesloten in `span`-tags met behulp van het `class`-kenmerk om naar de CSS-klasse te verwijzen. Bijvoorbeeld:

`<span class=monospaced>Monospaced Text Here</span>`

Wanneer de plug-in Stijlen voor de eerste keer is ingeschakeld, zijn er geen standaardstijlen beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs stijlen te voorzien:

* Schakel de vervolgkeuzelijst Stijl in.
* Geef een of meer locaties van de stijlpagina&#39;s op.
* Geef de afzonderlijke stijlen op die u kunt selecteren in de pop-uplijst Stijlen.

Voor latere herconfiguraties, bijvoorbeeld om meer stijlen toe te voegen, volg slechts de instructies om naar een nieuw stijlblad te verwijzen en de extra stijlen te specificeren.

>[!NOTE]
>
>Stijlen kunnen ook worden gedefinieerd voor [tabellen of tabelcellen](configure-rich-text-editor-plug-ins.md#tablestyles). Deze configuraties vereisen afzonderlijke procedures.

### De vervolgkeuzelijst Stijlinschakelen {#styleselectorlist}

Hiervoor schakelt u de insteekmodule Stijlen in.

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/styles`. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `styles`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`  (sterretje)

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Zodra de plug-in Stijlen is ingeschakeld, wordt de vervolgkeuzelijst Stijl weergegeven in het dialoogvenster Bewerken. De lijst is echter leeg omdat er geen stijlen zijn geconfigureerd.

### De locatie van het stijlblad opgeven {#locationofstylesheet}

Geef vervolgens de locatie(s) op van de stijlpagina(&#39;s) waarnaar u wilt verwijzen:

1. Navigeer naar het hoofdknooppunt van de tekstcomponent, bijvoorbeeld `/apps/<myProject>/components/text`.
1. Voeg de eigenschap `externalStyleSheets` toe aan het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `externalStyleSheets`
   * **Type** `String[]`  (meerdere tekenreeksen; klik op  **** Meerdere CRXDE)
   * **Waarde(s)** Het pad en de bestandsnaam van elk stijlblad dat u wilt opnemen. Gebruik repository paden.

   >[!NOTE]
   >
   >U kunt op elk later moment verwijzingen naar extra stijlbladen toevoegen.

1. Sla alle wijzigingen op.

Wanneer u RTE gebruikt in een dialoogvenster (klassieke gebruikersinterface), kunt u stijlpagina&#39;s opgeven die zijn geoptimaliseerd voor RTF-bewerking. Vanwege technische beperkingen gaat de CSS-context verloren in de editor, zodat u deze context kunt emuleren om de WYSIWYG-ervaring te verbeteren.

De rijke Redacteur van de Tekst gebruikt een containerDOM element met een identiteitskaart van `CQrte` die verschillende stijlen om verstrekt te bekijken en uit te geven:

```css
#CQ td {
// defines the style for viewing
 }
```

```css
#CQrte td {
 // defines the style for editing
 }
```

### Geef de beschikbare stijlen op in de pop-uplijst {#stylesindropdown}

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/styles`, zoals gecreeerd in [Toelatend de stijldrop-down selecteur](#styleselectorlist).
1. Onder de knoop `styles`, creeer een knoop (ook genoemd `styles`) om de lijst te houden die beschikbaar wordt gemaakt:

   * **Naam** `styles`
   * **Type** `cq:WidgetCollection`

1. Creeer een knoop onder de `styles` knoop om een individuele stijl te vertegenwoordigen:

   * **Naam**, u kunt de naam specificeren, maar het zou voor de stijl geschikt moeten zijn
   * **Type** `nt:unstructured`

1. Voeg de eigenschap `cssName` toe aan dit knooppunt om naar de CSS-klasse te verwijzen:

   * **Naam** `cssName`
   * **Type** `String`
   * **** ValueThe name of the CSS class (without a previous &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)

1. Voeg de eigenschap `text` toe aan hetzelfde knooppunt. Hiermee wordt de tekst gedefinieerd die wordt weergegeven in het selectievak:

   * **Naam** `text`
   * **Type** `String`
   * **** ValueDescription of the style; wordt weergegeven in het keuzemenu Stijl.

1. Sla de wijzigingen op.

   Herhaal bovenstaande stappen voor elke vereiste stijl.

### RTE configureren voor optimale woordeinden in het Japans {#jpwordwrap}

Auteurs die [!DNL Experience Manager] gebruiken om inhoud in de Japanse taal te schrijven, kunnen een stijl toepassen op tekens om regeleinde te voorkomen wanneer een regeleinde niet vereist is. Op deze manier kunnen auteurs de zinnen op de gewenste positie laten afbreken. De stijl voor deze functionaliteit is gebaseerd op CSS-klasse die vooraf is gedefinieerd in de CSS-stijlpagina.

Ga als volgt te werk om de stijl te maken die auteurs op Japanse tekst kunnen toepassen:

1. Maak een knooppunt onder het knooppunt Stijlen. Zie [een stijl opgeven](#stylesindropdown).
   * Naam: `jpn-word-wrap`
   * Type: `nt:unstructure`

1. Voeg de eigenschap `cssName` toe aan het knooppunt om naar de CSS-klasse te verwijzen. Deze klassenaam is een gereserveerde naam voor de functie voor tekstomloop in Japans.
   * Naam: `cssName`
   * Type: `String`
   * Waarde: `jpn-word-wrap` (zonder voorafgaande `.`)

1. Voeg de bezitstekst aan de zelfde knoop toe. De waarde is de naam van de stijl die de auteurs zien wanneer ze de stijl selecteren.
   * Naam: `text`
*Type: 
`String`
   * Waarde: `Japanese word-wrap`

1. Maak een stijlpagina en geef het pad op. Zie [locatie van stijlpagina](#locationofstylesheet) specificeren. Voeg de volgende inhoud aan de stijlpagina toe. Wijzig de achtergrondkleur naar wens.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![Stijlblad om Japanse tekstomloopfunctie beschikbaar te maken voor auteurs](assets/rte_jpwordwrap_stylesheet.jpg)

## De alineaopmaakconfigureren {#paraformats}

Om het even welke tekst authored in RTE wordt geplaatst binnen een blokmarkering, het gebrek is `<p>`. Als u de insteekmodule `paraformat` inschakelt, geeft u via een vervolgkeuzelijst aanvullende blokcodes op die aan alinea&#39;s kunnen worden toegewezen. Alineaopmaak bepaalt het alineatype door de juiste bloktag toe te wijzen. De auteur kan deze selecteren en toewijzen met de kiezer Indeling. De voorbeeldbloklabels omvatten onder andere de standaardalinea &lt;p> en koppen &lt;h1>, &lt;h2> enzovoort.

>[!CAUTION]
>
>Deze plug-in is niet geschikt voor inhoud met een complexe structuur, zoals lijsten of tabellen.

>[!NOTE]
>
>Als een bloktag, bijvoorbeeld een tag `<hr>`, niet aan een alinea kan worden toegewezen, is dit geen geldig gebruiksgeval voor een plug-in `paraformat`.

Wanneer de insteekmodule Alineopmaak voor het eerst is ingeschakeld, zijn er geen standaardalineaopmaak beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs alinea-indelingen te bieden:

* Schakel de pop-upselectielijst [!UICONTROL Format] in.
* Geef in het pop-upmenu de blokcodes op die u als alinea-indeling kunt selecteren.

Voor latere herconfiguraties, zeg om meer formaten toe te voegen, volg slechts het relevante deel van de instructies.

### De keuzelijst Indelinginschakelen {#formatselectorlist}

Voer de volgende stappen uit om de `paraformat`-plug-in in te schakelen:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/paraformat`. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `paraformat`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`  (sterretje)

>[!NOTE]
>
>Als de plug-in niet verder is geconfigureerd, zijn de standaardindelingen die zijn ingeschakeld Alinea ( `<p>`), Kop 1 ( `<h1>`), Kop 2 ( `<h2>`), Kop 3 ( `<h3>`).

>[!CAUTION]
>
>Wanneer het vormen van de paragraafformaten van RTE, verwijder niet de paragraafmarkering &lt;p> als het formatteren optie. Als de tag `<p>` wordt verwijderd, kan de auteur van de inhoud de optie [!UICONTROL Paragraph formats] niet selecteren, zelfs niet als er extra indelingen zijn geconfigureerd.

### Geef de beschikbare alineaopmaak op {#paraformatsindropdown}

Alinea-indelingen kunnen worden geselecteerd door:

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/paraformat`, zoals gecreeerd in [Het toelaten van de formaatdrop-down selecteur](#styleselectorlist).
1. Onder de `paraformat` knoop creeer een knoop, om de lijst van formaten te houden:

   * **Naam** `formats`
   * **Type** `cq:WidgetCollection`

1. Creeer een knoop onder de `formats` knoop, dit houdt details voor een individueel formaat:

   * **U kunt de naam** opgeven, maar deze moet wel geschikt zijn voor de indeling (bijvoorbeeld mijnalinea, mijnkop1).
   * **Type** `nt:unstructured`

1. Aan dit knooppunt voegt u de eigenschap toe om de gebruikte bloktag te definiëren:

   * **Naam** `tag`
   * **Type** `String`
   * **** ValueThe block tag for the format; bijvoorbeeld: p, h1, h2, enz.

      U hoeft de punthaakjes voor scheidingstekens niet in te voeren.

1. Aan de zelfde knoop voeg een ander bezit toe, voor beschrijvende tekst om in de drop-down lijst te verschijnen:

   * **Naam** `description`
   * **Type** `String`
   * **** ValueThe descriptive text for this format; bijvoorbeeld Alinea, Kop 1, Kop 2 enzovoort. Deze tekst wordt weergegeven in de selectielijst Indeling.

1. Sla de wijzigingen op.

   Herhaal de stappen voor elke vereiste indeling.

>[!CAUTION]
>
>Als u aangepaste indelingen definieert, worden de standaardindelingen (`<p>`, `<h1>`, `<h2>` en `<h3>`) verwijderd. Maak de `<p>`-indeling opnieuw omdat dit de standaardindeling is.

## Speciale tekensconfigureren {#spchar}

Wanneer in een standaard [!DNL Experience Manager]-installatie de `misctools`-plug-in is ingeschakeld voor speciale tekens (`specialchars`), is er direct een standaardselectie beschikbaar voor gebruik. bijvoorbeeld de symbolen copyright en trademark.

U kunt RTE vormen om uw selectie van karakters beschikbaar te maken; of door verschillende karakters, of een volledige opeenvolging te bepalen.

>[!CAUTION]
>
>Als u speciale tekens toevoegt, wordt de standaardselectie genegeerd. Definieer deze tekens desgewenst opnieuw in de selectie.

### Eén teken definiëren {#definesinglechar}

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/misctools`. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `misctools`:

   * **Naam** `features`
   * **Type** `String[]`
   * **Waarde** `specialchars`

          (of `String / *` als u alle functies voor deze plug-in toepast)

1. Onder `misctools` creeer een knoop om de speciale karakterconfiguraties te houden:

   * **Naam** `specialCharsConfig`
   * **Type** `nt:unstructured`

1. Maak onder `specialCharsConfig` een ander knooppunt voor de lijst met tekens:

   * **Naam** `chars`
   * **Type** `nt:unstructured`

1. Voeg onder `chars` een knooppunt toe voor een afzonderlijke tekendefinitie:

   * **** U kunt de naam opgeven, maar deze moet het teken weerspiegelen; bijvoorbeeld de helft.
   * **Type** `nt:unstructured`

1. Aan deze knoop voeg het volgende bezit toe:

   * **Naam** `entity`
   * **Type** `String`
   * **De** waarde van de HTML-weergave van het vereiste teken; bijvoorbeeld  `&189;` voor de fractie de helft.

1. Sla de wijzigingen op.

In CRXDE, zodra het bezit wordt bewaard, wordt het vertegenwoordigde karakter getoond. Zie onder het voorbeeld van de helft. Herhaal bovenstaande stappen om meer speciale tekens beschikbaar te maken voor auteurs.

![In CRXDE, voeg één enkel karakter toe dat op RTE ](assets/chlimage_1-106.png "toolbarIn CRXDE ter beschikking moet worden gesteld, voeg één enkel karakter toe dat op de toolbar van RTE ter beschikking moet worden gesteld")

### Een tekenbereik definiëren {#definerangechar}

1. Gebruik stap 1 tot en met 3 van [Eén teken definiëren](#definesinglechar).
1. Voeg onder `chars` een knooppunt toe voor de definitie van het tekenbereik:

   * **** U kunt de naam opgeven, maar deze moet wel het tekenbereik weerspiegelen. bijvoorbeeld potloden .
   * **Type** `nt:unstructured`

1. Voeg onder dit knooppunt (benoemd op basis van uw speciale tekenbereik) de volgende twee eigenschappen toe:

   * **Naam** `rangeStart`

      **Type** `Long`
      **De** waarde van de  [](https://unicode.org/) Unicode-representatie (decimaal) van het eerste teken in het bereik

   * **Naam** `rangeEnd`

      **Type** `Long`
      **De** waarde van de  [](https://unicode.org/) Unicode-representatie (decimaal) van het laatste teken in het bereik

1. Sla de wijzigingen op.

   Als u bijvoorbeeld een bereik definieert tussen 998 en 10000, kunt u de volgende tekens gebruiken.

   ![Definieer in CRXDE een tekenbereik dat beschikbaar moet worden gemaakt in RTE](assets/chlimage_1-107.png)

   *Afbeelding: Definieer in CRXDE een tekenbereik dat beschikbaar moet worden gemaakt in RTE*

   ![Speciale tekens die beschikbaar zijn in RTE worden weergegeven aan auteurs in een pop-](assets/rtepencil.png "upvensterSpeciale tekens die beschikbaar zijn in RTE worden weergegeven aan auteurs in een pop-upvenster")

## Tabelstijlen configureren {#tablestyles}

Stijlen worden doorgaans toegepast op tekst, maar een aparte set stijlen kan ook worden toegepast op een tabel of op een paar tabelcellen. Dergelijke stijlen zijn beschikbaar voor auteurs in het selectievak Stijl in het dialoogvenster Eigenschappen van cel of Tabeleigenschappen. De stijlen zijn beschikbaar wanneer het uitgeven van een lijst binnen een component van de Tekst (of een derivaat) en niet in de standaardcomponent van de Lijst.

>[!NOTE]
>
>U kunt stijlen alleen definiëren voor tabellen en cellen voor klassieke gebruikersinterface.

>[!NOTE]
>
>Het kopiëren en het kleven van lijsten in of van de component van RTE is browser-afhankelijk. De functie wordt niet in het vak ondersteund voor alle browsers. Afhankelijk van de tabelstructuur en de browser krijgt u mogelijk verschillende resultaten. Wanneer u bijvoorbeeld een tabel kopieert en plakt in een RTE-component in Mozilla Firefox in Classic UI en Touch UI, blijft de indeling van de tabel niet behouden.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/table`. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `table`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`

   >[!NOTE]
   >
   >Als u niet alle lijsteigenschappen wilt toelaten kunt u `features` bezit tot stand brengen als:
   >* **Type** `String[]`

   * **Waarde** één of beide van het volgende, naargelang van de behoefte:
      * `table` het bewerken van tabeleigenschappen toestaan; inclusief de stijlen.
      * `cellprops` om het bewerken van celeigenschappen mogelijk te maken, inclusief de stijlen.


1. Definieer de locatie van CSS-stijlpagina&#39;s om deze te verwijzen. Zie [De locatie van het stijlblad opgeven](#locationofstylesheet) omdat dit hetzelfde is als wanneer [stijlen voor tekst worden gedefinieerd](#textstyles). De locatie kan worden gedefinieerd als u andere stijlen hebt gedefinieerd.
1. Onder de `table` knoop creeer de volgende knopen zoals vereist:

   * Stijlen definiëren voor de gehele tabel (beschikbaar onder **[!UICONTROL Table properties]**):

      * **Naam** `tableStyles`
      * **Type** `cq:WidgetCollection`
   * Stijlen definiëren voor de afzonderlijke cellen (beschikbaar onder **[!UICONTROL Cell properties]**),

      * **Naam** `cellStyles`
      * **Type** `cq:WidgetCollection`


1. Maak een knooppunt (onder het knooppunt `tableStyles` of `cellStyles`, al naar gelang van toepassing) om een afzonderlijke stijl te vertegenwoordigen,

   * **U** kunt de naam opgeven, maar deze moet de stijl weerspiegelen.
   * **Type** `nt:unstructured`

1. Maak op dit knooppunt de eigenschappen:

   * De CSS-stijl waarnaar wordt verwezen, definiëren

      * **Naam** `cssName`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande  `.`, bijvoorbeeld,  `cssClass` in plaats van  `.cssClass`)
   * Als u een beschrijvende tekst wilt definiëren die in de pop-upkiezer moet worden weergegeven,

      * **Naam** `text`
      * **Type** `String`
      * **De** waarde van de tekst die in de selectielijst moet worden weergegeven


1. Sla alle wijzigingen op.

Herhaal bovenstaande stappen voor elke vereiste stijl.

### Verborgen koppen in tabellen configureren voor toegankelijkheid {#hiddenheader}

Soms kunt u gegevenslijsten zonder visuele tekst in een kolomkopbal tot stand brengen veronderstellend dat het doel van de kopbal door de visuele verhouding van de kolom met andere kolommen wordt geïmpliceerd. In dit geval moet verborgen binnentekst in de cel in de kopcel worden weergegeven, zodat schermlezers en andere ondersteunende hulpmiddelen het doel van de kolom kunnen begrijpen.

Om toegankelijkheid in dergelijke scenario&#39;s te verbeteren, steunt RTE verborgen kopbalcellen. Bovendien worden er configuratie-instellingen gegeven voor verborgen koppen in tabellen. Met deze instellingen kunt u CSS-stijlen toepassen op verborgen koppen in de bewerkings- en voorvertoningsmodus. Om auteurs te helpen verborgen kopballen in Edit wijze identificeren, omvat de volgende parameters in uw code:

* `hiddenHeaderEditingCSS`: Hiermee geeft u de naam op van de CSS-klasse die wordt toegepast op de cel met verborgen koptekst wanneer RTE wordt bewerkt.
* `hiddenHeaderEditingStyle`: Hiermee geeft u een stijltekenreeks op die wordt toegepast op de cel met verborgen koptekst wanneer RTE wordt bewerkt.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

Om auteurs te helpen CSS op verborgen kopballen op de voorproefwijze toepassen, kunt u de volgende parameters in uw code omvatten:

* `hiddenHeaderClassName`: Hiermee geeft u de naam op van de CSS-klasse die wordt toegepast op de verborgen kopcel in de voorvertoningsmodus.
* `hiddenHeaderStyle`: Hiermee geeft u een stijltekenreeks op die wordt toegepast op de cel met de verborgen koptekst in de voorvertoningsmodus.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

## Woordenboeken toevoegen voor de spellingcontrole {#adddict}

Wanneer de insteekmodule voor spellingcontrole is geactiveerd, gebruikt de RTE woordenboeken voor elke geschikte taal. Deze worden vervolgens geselecteerd volgens de taal van de website door ofwel de taaleigenschap van de substructuur te nemen of de taal uit de URL te halen; bijvoorbeeld. de `/en/` tak wordt gecontroleerd als Engels, de `/de/` tak als Duits.

>[!NOTE]
>
>Het bericht &#39;&#39;Spellingcontrole mislukt.&#39;&#39; wordt gezien als een controle voor een taal wordt geprobeerd die niet geïnstalleerd is.

Een standaardinstallatie van de Experience Manager bevat de woordenboeken voor:

* Amerikaans Engels (nl_nl)
* Brits Engels (en_gb)

>[!NOTE]
>
>De standaardwoordenboeken bevinden zich op `/libs/cq/spellchecker/dictionaries`, samen met de juiste leesmij-bestanden. Wijzig de bestanden niet.

Voer de volgende stappen uit als u meer woordenboeken wilt toevoegen.

1. Navigeer naar de pagina [https://extensions.openoffice.org/](https://extensions.openoffice.org/).
1. Selecteer de gewenste taal en download het ZIP-bestand met de spellingdefinities. Extraheer de inhoud van het archief op uw bestandssysteem.

   >[!CAUTION]
   >
   >Alleen woordenboeken in de `MySpell`-indeling voor OpenOffice.org v2.0.1 of eerder worden ondersteund. Aangezien de woordenboeken nu archiefbestanden zijn, wordt u aangeraden het archief na het downloaden te verifiëren.

1. Zoek de .aff- en .dic-bestanden. Bestandsnaam in kleine letters behouden. Bijvoorbeeld `de_de.aff` en `de_de.dic`.
1. Laad de .aff- en .dic-bestanden in de opslagplaats op `/apps/cq/spellchecker/dictionaries`.

>[!NOTE]
>
>De spellingcontrole van RTE is beschikbaar op bestelling. Deze wordt niet automatisch uitgevoerd wanneer u tekst gaat typen.
>Als u de spellingcontrole wilt uitvoeren, tikt u op of klikt u op de knop Spellingcontrole op de werkbalk. RTE controleert de spelling van woorden en benadrukt verkeerd-gespelde woorden.
>Als u een wijziging opneemt die door de spellingcontrole wordt voorgesteld, worden de tekststatus en onjuist gespelde woorden niet meer gemarkeerd. Als u de spellingcontrole wilt uitvoeren, tikt u nogmaals op de knop Spellingcontrole of klikt u nogmaals op de knop Spellingcontrole.

## De historiegrootte configureren voor het ongedaan maken en opnieuw uitvoeren van handelingen {#undohistory}

Met RTE kunnen auteurs enkele laatste bewerkingen ongedaan maken of opnieuw uitvoeren. Standaard worden 50 bewerkingen opgeslagen in de geschiedenis. U kunt deze waarde naar wens configureren.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/undo`. Maak deze knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap op het knooppunt `undo`:

   * **Naam** `maxUndoSteps`
   * **Type** `Long`
   * **De** waarde van het aantal stappen ongedaan maken die u in de geschiedenis wilt opslaan. De standaardwaarde is 50. Gebruik `0` om ongedaan te maken/opnieuw.

1. Sla de wijzigingen op.

## De tabgrootteconfigureren {#tabsize}

Wanneer het tabteken wordt ingedrukt binnen tekst, wordt een vooraf gedefinieerd aantal spaties ingevoegd. Dit zijn standaard drie vaste spaties en één spatie.

De tabgrootte definiëren:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/keys`. Maak de knooppunten als de knooppunten niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap op het knooppunt `keys`:

   * **Naam** `tabSize`
   * **Type** `String`
   * **De** waarde van het aantal spatietekens dat voor de tabulator moet worden gebruikt.

1. Sla de wijzigingen op.

## Inspringingsmargeinstellen {#indentmargin}

Wanneer inspringing is ingeschakeld (standaard), kunt u de grootte van de inspringing definiëren:

>[!NOTE]
>
>Deze inspringingsgrootte wordt alleen toegepast op alinea&#39;s (blokken tekst). het heeft geen invloed op de inspringing van feitelijke lijsten.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/lists`. Maak deze knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak op het knooppunt `lists` de parameter `identSize`:

   * **Naam**:  `identSize`
   * **Type**:  `Long`
   * **Waarde**: aantal pixels dat is vereist voor de inspringingsmarge.

## De hoogte van bewerkbare ruimteconfigureren {#editablespace}

U kunt de hoogte van de bewerkbare ruimte definiëren die in het dialoogvenster van de component wordt weergegeven. De configuratie is slechts van toepassing wanneer het gebruiken van RTE in een dialoog. De hoogte van het dialoogvenster wordt niet gewijzigd door de configuratie.

1. Maak in het knooppunt `../items/text` in de dialoogdefinitie voor de component een eigenschap:

   * **Naam** `height`
   * **Type** `Long`
   * **De** waarde van de hoogte van het bewerkingscanvas in pixels.

1. Sla de wijzigingen op.

## Stijlen en protocollen voor koppelingen configureren {#linkstyles}

Wanneer u koppelingen toevoegt in [!DNL Experience Manager], kunt u de CSS-stijlen definiëren die moeten worden gebruikt en de protocollen die automatisch moeten worden geaccepteerd. Om te vormen hoe de verbindingen in [!DNL Experience Manager] van een ander programma worden toegevoegd, bepaal de regels van HTML.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Maak een knooppunt op hetzelfde niveau als `<rtePlugins-node>`, dat wil zeggen: maak het knooppunt onder het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `htmlRules`
   * **Type** `nt:unstructured`

   >[!NOTE]
   >
   >Het knooppunt `../items/text` heeft de eigenschap:
   >* **Naam** `xtype`
   >* **Type** `String`
   >* **Waarde** `richtext`

   De locatie van het knooppunt `../items/text` kan variëren, afhankelijk van de structuur van het dialoogvenster. Twee voorbeelden zijn `/apps/myProject>/components/text/dialog/items/text` en `/apps/<myProject>/components/text/dialog/items/panel/items/text`.

1. Maak onder `htmlRules` een knooppunt.

   * **Naam** `links`
   * **Type** `nt:unstructured`

1. Definieer onder het knooppunt `links` de eigenschappen naar wens:

   * CSS-stijl voor interne koppelingen:

      * **Naam** `cssInternal`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)
   * CSS-stijl voor externe koppelingen

      * **Naam** `cssExternal`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)
   * Array van geldige **[!UICONTROL protocols]**, inclusief `https://`, `https://`, `file://`, `mailto:` en andere,

      * **Naam** `protocols`
      * **Type** `String[]`
      * **Waarde**(s) een of meer protocollen
   * **defaultProtocol**  (eigenschap van het type  **String**): Protocol dat moet worden gebruikt als de gebruiker niet uitdrukkelijk één specificeerde.

      * **Naam** `defaultProtocol`
      * **Type** `String`
      * **Waarde**(s) een of meer standaardprotocollen
   * Definitie van hoe te om het doelattribuut van een verbinding te behandelen. Een knooppunt maken:

      * **Naam** `targetConfig`
      * **Type** `nt:unstructured`

      Op het knooppunt `targetConfig`: de vereiste eigenschappen definiëren:

      * Geef de doelmodus op:

         * **Naam** `mode`
         * **Type** `String`)
         * **Waarde**(s) :

            * `auto`: betekent dat een automatisch doel wordt gekozen

               (opgegeven door de eigenschap `targetExternal` voor externe koppelingen of `targetInternal` voor interne koppelingen).

            * `manual`: niet van toepassing in dit verband
            * `blank`: niet van toepassing in dit verband
      * Het doel voor interne koppelingen:

         * **Naam** `targetInternal`
         * **Type** `String`
         * **Waarde** van het doel voor interne koppelingen (alleen gebruiken als de modus is  `auto`)
      * Het doel voor externe koppelingen:

         * **Naam** `targetExternal`
         * **Type** `String`
         * **De** waarde van het doel voor externe koppelingen (wordt alleen gebruikt wanneer de modus is  `auto`).








1. Sla alle wijzigingen op.
