---
title: Zoeken in Forms configureren
description: Zoeken in Forms voor Adobe Experience Manager as a Cloud Service configureren.
exl-id: b06649c4-cc91-44e3-8699-00e90140b90d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2036'
ht-degree: 1%

---

# Zoeken in Forms configureren {#configuring-search-forms}

Adobe Experience Manager as a Cloud Service is uitgerust met een krachtig [Zoeken](/help/sites-cloud/authoring/search.md) mechanisme.

In combinatie hiermee is er ook een set vooraf gedefinieerde opties waarmee u de inhoud kunt filteren. Deze bevatten vooraf gedefinieerde facetten, zoals **Wijzigingsdatum**, **Status publiceren**, of **Status van bioscoop** om u te helpen snel tot de middelen doordringen u nodig hebt.

![zoeken en filteren](assets/csf-usage.png)

Samen helpen u om uw inhoud snel en gemakkelijk te vinden van:

* [Zoeken en filteren](/help/sites-cloud/authoring/search.md#search-and-filter)
* [Spoorwegkiezer](/help/sites-cloud/authoring/basic-handling.md#rail-selector)
* de [Browser voor middelen](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser) (bij het bewerken van pagina&#39;s)

>[!NOTE]
>
>U kunt de onderliggende [Inhoud zoeken en indexeren](/help/operations/indexing.md) service.

Gebruiken **Zoeken in Forms** kunt u deze deelvensters aanpassen en uitbreiden, afhankelijk van uw specifieke behoeften.

De **Zoeken in Forms** een selectie buiten de box van [voorspellen](#predicates-and-their-settings) die u kunt combineren en definiëren. De [dialoogvensters voor het configureren van deze formulieren](#configuring-your-search-forms) kan worden geraadpleegd via:

* **Gereedschappen**
   * **Algemeen**
      * **Zoeken in Forms**

## Standaard Forms {#default-forms}

Wanneer u voor het eerst toegang krijgt tot **Zoeken in Forms** op de console ziet u dat alle configuraties een hangslotsymbool hebben. Dit wijst erop dat de overeenkomstige configuratie de standaardconfiguratie (uit-van-de-doos) is - en kan niet worden geschrapt. Zodra u hebt aangepast, en bewaard, zal een configuratie het slot verdwijnen. Het verschijnt weer als u [verwijder uw aangepaste configuratie](#deleting-a-configuration-to-reinstate-the-default), in welk geval de standaardwaarde (en de hangslotindicator) opnieuw worden ingevoerd.

![overzicht van zoekformulieren configureren](assets/csf-overview.png)

De standaardconfiguraties (alfabetisch weergegeven) zijn:

* **Middelen Admin Search Rail**
* **Pagina-editor (zoeken naar documenten)**
* **Pagina-editor (zoek fragmenten met ervaring)**
* **Pagina-editor (zoeken naar afbeeldingen)**
* **Pagina-editor (Manuscript-zoekopdracht)**
* **Pagina-editor (zoeken naar pagina)**
* **Pagina-editor (zoeken in alinea&#39;s)**
* **Pagina-editor (productzoekopdracht)**
* **Pagina-editor (zoeken in Scene7)**
* **Pagina-editor (videozoekopdracht)**
* **Zoekspoor voor projectbeheerder**
* **Zoekspoor voor projectvertaling**
* **Sites Admin Search Rail**
* **Zoekspoor voor fragmenten Admin**
* **Zoeken op rails voor voorraadbeheerders**
* **Modellen van inhoudsfragmenten doorzoeken**
* **Zoekspoor voor projectbeheerder**
* **Zoekspoor voor projectvertaling**

>[!NOTE]
>
>Zie voor meer informatie over aan middelen gerelateerde zoekformulieren [Middelen - zoekfactoren](/help/assets/search-facets.md).


## Voorspellen en de bijbehorende instellingen {#predicates-and-their-settings}

### Voorspellen {#predicates}

De volgende predikaten zijn beschikbaar, afhankelijk van de configuratie:

<table>
 <tbody>
  <tr>
   <th>Voorspelend</th>
   <th>Doel</th>
   <th>Instellingen</th>
  </tr>
  <tr>
   <td>Analyse</td>
   <td>Mogelijkheden zoeken/filteren in de Sites-browser bij het weergeven van gegevens met analysemogelijkheden. De zoekfilters van Analytics laden tot aan de in kaart gebrachte aangepaste analytische kolommen.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Goedkeuringsstatus</td>
   <td>Zoeken op basis van goedkeuringsstatus.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Auteur</td>
   <td>Zoeken volgens auteur.</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Uitgecheckt door</td>
   <td>Zoeken naar elementen die zijn uitgecheckt door een specifieke gebruiker.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Afhandelingsstatus</td>
   <td>Zoeken naar elementen met een specifieke status voor uitchecken.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Onderdelen</td>
   <td>Hiermee kan een auteur zoeken/filteren op pagina's die een specifieke component bevatten. Bijvoorbeeld een afbeeldingsgalerie.<br /> </td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Diepte van eigenschap</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datumbereik</td>
   <td>Zoek naar middelen die binnen een gespecificeerde waaier voor een datumbezit worden gecreeerd. In het deelvenster Zoeken kunt u begin- en einddatums opgeven.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Bereik tekst (Van)*</li>
     <li>Bereik tekst (naar)*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vervalstatus</td>
   <td>Zoek bronnen op basis van de vervalstatus.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bestandsgrootte</td>
   <td>Bronnen filteren op basis van hun grootte.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bestandstype</td>
   <td>Elementen zoeken op basis van het bestands-/mime-type.</td>
   <td>
    <ul>
     <li>Veldlabel</li> 
     <li>Eigenschapnaam*</li>
     <li>Mimetype-pad</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Fulltext</td>
   <td>Zoeken voorspelt zoekopdrachten in volledige tekst. Het is toegewezen met de operator "jcr:contains".</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Groep</td>
   <td>Zoeken naar voorspellingen voor groep (alleen gebruikt binnen het voorvoegsel Inzichten).</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Verborgen filter</td>
   <td>Een filter op eigenschap en waarde, niet zichtbaar voor de gebruiker.</td>
   <td>
    <ul>
     <li>Eigenschapnaam*</li>
     <li>Waarde van eigenschap*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Inzichten</td>
   <td>Zoek volgens een selectie van parameters van Inzichten.</td>
   <td>Dit is een complexe predikaat die uit veelvoudige predikaten wordt samengesteld:
    <ul>
     <li>Groep</li>
     <li>Bereik</li>
     <li>Opties</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Lid van herkomst</td>
   <td>Zoeken naar elementen die lid zijn van een verzameling</td>
   <td>
    <ul>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Eigenschap voor meerdere waarden</td>
   <td>Zoeken op meerdere waarden van een opgegeven eigenschap.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Delimiter-ondersteuning</li>
     <li>Invoerscheidingstekens</li>
     <li>Hoofdlettergebruik negeren</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Opties</td>
   <td><p>De opties zijn inhoudsknooppunten die door de gebruiker zijn gemaakt.</p> <p>Zie <a href="#addinganoptionspredicate">Vooraf ingestelde opties toevoegen</a> voor meer informatie .</p> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Enkel selecteren</li>
     <li>Opties toevoegen</li>
     <li>Handmatig</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Opties, eigenschap</td>
   <td>Zoeken op een of meer eigenschappen van de optie.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Pad naar knooppunt Opties</li>
     <li>Diepte van eigenschap</li>
     <li>Enkel selecteren</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Paginastatus</td>
   <td>Pagina's filteren op basis van hun status.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Naam van eigenschap publiceren*</li>
     <li>Eigenschapnaam vergrendelde pagina's*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pad</td>
   <td>Filter op basis van een specifiek pad. U kunt meerdere paden opgeven als opties.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Zoekpaden toevoegen</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Padbrowser</td>
   <td>Geef een padbrowser op om naar een vooraf gedefinieerd hoofdpad te zoeken.</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Basispad</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Pad verborgen</td>
   <td>Een filter op pad dat niet zichtbaar is voor de gebruiker.</td>
   <td>
    <ul>
     <li>Naam eigenschap ("path")</li>
     <li>Waarde van het onroerend goed (`/content/dam')</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Eigenschap</td>
   <td>Zoeken op een opgegeven eigenschap.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam</li>
     <li>Gedeeltelijk zoeken</li>
     <li>Hoofdlettergebruik negeren</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Status publiceren</td>
   <td>Bronnen filteren op basis van hun publicatiestatus.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bereik</td>
   <td>Zoekbronnen binnen een opgegeven bereik. In het paneel van het Onderzoek, kunt u minimum en maximumwaarden voor de waaier specificeren.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Classificatie</td>
   <td>Zoek naar middelen volgens hun gemiddelde classificatie.<br /> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Relatieve datum</td>
   <td>Bronnen filteren op basis van de relatieve datum waarop ze zijn gemaakt. 1 week geleden, 1 maand geleden.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Relatieve datum</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Schuifbereik</td>
   <td>Een gemeenschappelijk onderzoek voorspelt zich uitbreidend de waaiervoorspelling met het schuifvermogen. De waarde van de gezochte eigenschap moet tussen de schuifregelaargrenzen liggen.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Pad naar knooppunt Opties</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Status</td>
   <td>Zoeken op basis van de status voor goedkeuring en afhandeling.</td>
   <td>Dit is een complexe predikaat die uit veelvoudige predikaten wordt samengesteld:
    <ul>
     <li>Goedkeuringsstatus</li>
     <li>Afhandelingsstatus</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Tags</td>
   <td>Zoeken op basis van tags.</td>
   <td>
    <ul>
     <li>Veldgelavel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Alle labels weergeven, optie</li>
     <li>Pad van basiscodes</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Sjablonen</td>
   <td>Zoeken volgens de geselecteerde sjabloon.</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> 
   </td>
  </tr>
  <tr>
   <td>Vertaalstatus</td>
   <td>Zoeken volgens de vertaalstatus.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
    </ul> 
   </td>
  </tr>
 </tbody>
</table>

<!--
  <tr>
   <td>Date ???</td>
   <td>Slider-based search of assets based on a date property.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Description</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Asset Last Modified ?????</td>
   <td>Date the asset was last modified.<br /> </td>
   <td>A customized predicate, based on the Date Predicate.</td>
  </tr>
  <tr>
   <td>Range Options ???</td>
   <td>A specific search predicate for Assets and the same as common Slider Predicate. Is still available due to backward compatibilty issues.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Option Path</li>
     <li>Description</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tag </td>
   <td>Search assets based on tags. You can configure the Path property to populate various tags in the Tags list.</td>
   <td>
    <ul>
     <li>Field Label</li>
     <li>Property Name*</li>
     <li>Option Path</li>
     <li>Description</li>
    </ul> </td>
  </tr>
-->

>[!NOTE]
>
>De algemene zoekvoorspelling wordt gedefinieerd in:
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>Deze informatie is alleen ter referentie. U kunt deze niet wijzigen `/libs`.

<!--
>* Search predicates related only to siteadmin (classic UI) are located under:
> `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * These are deprecated and only available for backward compatibility.
>
-->

### Instellingen voor voorspelling {#predicate-settings}

Afhankelijk van de voorspelling zijn er verschillende instellingen beschikbaar voor de configuratie, waaronder:

* **Veldlabel**

  Het label dat wordt weergegeven als de inklapbare koptekst of als veldlabel van de voorspelling.

* **Beschrijving**

  Beschrijvende details voor de gebruiker.

* **Plaatsaanduiding**

  Lege tekst of de plaatsaanduiding van de voorspelling voor het geval er geen filtertekst wordt ingevoerd.

* **Eigenschapnaam**

  De eigenschap waarop moet worden gezocht. Er wordt een relatief pad en de jokertekens gebruikt `*/*/*` Geef de diepte van de eigenschap op ten opzichte van de `jcr:content` knooppunt (elke asterisk vertegenwoordigt één knooppuntniveau).

  Als u slechts op een eerste niveaukindknoop van het middel wilt zoeken dat heeft `x` eigenschap op de `jcr:content` knooppuntgebruik `*/jcr:content/x`

* **Diepte van eigenschap**

  De maximumdiepte om naar dat bezit binnen de middelen te zoeken. Een zoekopdracht naar die eigenschap kan dus worden uitgevoerd op een resource en recursieve onderliggende elementen totdat het niveau van de onderliggende objecten gelijk is aan de opgegeven diepte.

* **Waarde van eigenschap**

  De eigenschapswaarde als een absolute tekenreeks of als expressietaal, bijvoorbeeld `cq:Page` of

  `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **Bereik tekst**

  Het label van het bereikveld in het dialoogvenster **Datumbereik** voorspellen.

* **Optiepad**

  De gebruiker kan het pad selecteren met behulp van de Padbrowser op het tabblad Voorspelfunctie. Na het selecteren van **+** wordt gebruikt om de selectie toe te voegen aan de lijst met geldige opties (en **-** pictogram om indien nodig te verwijderen).

  De opties zijn inhoudsknooppunten die door de gebruiker zijn gemaakt en die de volgende structuur hebben:

  `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **Pad naar knooppunt Opties**
In feite hetzelfde als het **Pad naar opties** Alleen dit gebeurt in het gemeenschappelijke voorspelde veld, het andere is specifiek voor elementen.

* **Enkel selecteren**
Als deze optie is ingeschakeld, worden de opties weergegeven als selectievakjes die slechts één selectie toestaan. Als u per ongeluk een selectievakje hebt ingeschakeld, kan dit worden uitgeschakeld.

* **Naam/namen van eigenschappen van live-kopie publiceren en kopiëren**
De etiketten voor publiceren en levende exemplaarcontroledozen voor het specifieke predikaat van Plaatsen.

* De &amp;laatste; op de veldlabels in de **Instellingen** tab betekent dat de velden verplicht zijn en dat er een foutbericht wordt weergegeven als het veld leeg blijft.

## Uw zoekopdracht configureren, Forms {#configuring-your-search-forms}

### Een aangepaste configuratie maken/openen {#creating-opening-a-customized-configuration}

1. Navigeren naar **Gereedschappen**, **Algemeen**, **Zoeken in Forms**.

1. Selecteer de configuratie die u wilt aanpassen.
1. Gebruik de **Bewerken** om de configuratie voor bijwerken te openen.
1. Als u een nieuwe aanpassing wilt maken, zult u waarschijnlijk [nieuwe basisvelden toevoegen en de instellingen definiëren](#add-edit-a-predicate-field-and-define-field-settings) zoals vereist. Als een bestaande aanpassing u een bestaand gebied en [de instellingen bijwerken](#add-edit-a-predicate-field-and-define-field-settings).
1. Selecteren **Gereed** om de configuratie op te slaan. De volgende keer dat de configuratie wordt gebruikt, zijn uw wijzigingen zichtbaar.

   >[!NOTE]
   >
   >De aangepaste configuraties worden (indien van toepassing) opgeslagen onder:
   >
   >* `/apps/cq/gui/content/facets/<option>`
   >* `/apps/commerce/gui/content/facets/<option>`

### Een voorspelbaar veld toevoegen/bewerken en veldinstellingen definiëren {#add-edit-a-predicate-field-and-define-field-settings}

U kunt velden toevoegen of bewerken en de instellingen van velden definiëren/bijwerken:

1. [Open de aangepaste configuratie](#creating-opening-a-customized-configuration) voor bijwerken.
1. Als u een nieuw gebied wilt toevoegen, open **Predicate selecteren** en sleep de vereiste voorspelling naar de gewenste locatie. Bijvoorbeeld de **Datumbereik**:

   ![voorspelling toevoegen](assets/csf-add-predicate.png)

1. Afhankelijk van of:

   * U voegt een nieuw veld toe:

     Na het toevoegen van predikaat, **Instellingen** wordt geopend en worden de eigenschappen weergegeven die kunnen worden gedefinieerd.

   * U wilt een bestaande voorspelling bijwerken:

     Selecteer het voorloopveld (rechts) en open vervolgens het **Instellingen** tab.

   De instellingen voor de **Datumbereik**:

   ![voorspellen wijzigen](assets/csf-modify-predicate.png)

1. Breng de gewenste wijzigingen aan en bevestig deze met **Gereed**. De volgende keer dat de configuratie wordt gebruikt, zijn uw wijzigingen zichtbaar.

### Een voorvertoning weergeven van de zoekconfiguratie {#previewing-the-search-configuration}

1. Selecteer het pictogram Voorvertoning:

   ![voorvertoningspictogram](assets/csf-preview-icon.png)

1. Hiermee geeft u de zoekformulieren weer zoals deze worden weergegeven (volledig uitgevouwen) in de kolom Zoeken van de desbetreffende console.

   ![voorbeeldformulier](assets/csf-preview-form.png)

1. **Sluiten** de voorvertoning om de configuratie te retourneren en te voltooien.

### Een voorspelbaar veld verwijderen {#deleting-a-predicate-field}

1. [Open de aangepaste configuratie](#creating-opening-a-customized-configuration) voor bijwerken.
1. Selecteer het voorloopveld (rechts) en open het dialoogvenster **Instellingen** en selecteert u vervolgens de **Verwijderen** pictogram (linksonder).

   ![verwijderpictogram](assets/csf-delete-icon.png)

1. In een dialoogvenster wordt bevestiging van de verwijderactie gevraagd.

1. Bevestig dit en eventuele andere wijzigingen met **Gereed**.

### Een configuratie verwijderen (om de standaardinstelling te herstellen) {#deleting-a-configuration-to-reinstate-the-default}

Zodra u een configuratie hebt aangepast zal dit de gebreken met voeten treden. U kunt de standaardconfiguratie herstellen door uw aangepaste configuratie te schrappen.

>[!NOTE]
>
>U kunt de standaardconfiguraties niet verwijderen.

Het schrappen van een aangepaste configuratie wordt gedaan van de console:

1. Selecteer de vereiste configuratie (bijvoorbeeld **Pagina-editor (zoeken in alinea&#39;s)**) en vervolgens de **Verwijderen** pictogram in de werkbalk:

   ![default herstellen](assets/csf-restore-default.png)

1. De aangepaste configuratie wordt verwijderd en de standaardinstelling wordt hersteld (dit wordt aangegeven door het opnieuw verschijnen van het hangslotsymbool in de console).

### Voorwaarden voor opties toevoegen {#adding-options-predicates}

De voorspelling van de optie (Opties, het Bezit van Opties) staat u toe om een punt te vormen dat moet worden gezocht naar. Deze worden meestal gebruikt om rechtstreeks onder de pagina naar iets te zoeken, bijvoorbeeld een eigenschap op het paginaknooppunt.

In het volgende voorbeeld (om te zoeken op basis van de sjabloon die wordt gebruikt om een pagina te maken) worden de desbetreffende stappen geïllustreerd:

1. Maak het knooppunt waarin de eigenschap wordt gedefinieerd waarop moet worden gezocht.

   U hebt een basisknooppunt met definities van de afzonderlijke opties nodig om beschikbaar te zijn voor de gebruiker.

   De knooppunten voor de afzonderlijke opties hebben de volgende eigenschappen nodig:

   * `jcr:title` - het veldetiket dat in de zoekrail moet worden aangebracht
   * `value` - de waarde van de eigenschap waarop moet worden gezocht

   ![Predicate definitie](assets/csf-options-predicate-01.png)

   >[!NOTE]
   >
   >U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
   >
   >Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >1. Het vereiste item opnieuw maken, zoals dit bestaat in `/libs`, onder `/apps`. In dit geval:
   >1. `/libs/cq/gui/content/common/options/predicates`
   >1. Breng wijzigingen aan in `/apps.`

1. Open de **Zoeken in Forms** console en selecteer de configuratie u wilt bijwerken. Bijvoorbeeld: **Sites Admin Search Rail**. Selecteer vervolgens **Bewerken**.

1. Afhankelijk van de configuratie voegt u een **Opties** of **Opties, eigenschap** naar de configuratie.
1. Werk de velden bij, met name:

   * **Eigenschapnaam**

     Specifiek het knoopbezit dat op de doelknopen moet worden gezocht. Bijvoorbeeld:

     `jcr:content/cq:template`

   * **Pad naar knooppunt Option**

     Selecteer het pad naar de locatie waar uw opties staan. Bijvoorbeeld:

     `/apps/cq/gui/content/common/options/predicates/templatetype`

   ![Voorspelden van optie](assets/csf-options-predicate-02.png)

1. Selecteren **Gereed** om uw configuratie op te slaan.
1. Navigeer aan de aangewezen console (in dit voorbeeld, **Sites**) en opent u de **Zoeken - Filters** spoorwegen. De nieuwe zoekformulieren en de verschillende opties zijn zichtbaar. Selecteer de gewenste optie om de zoekresultaten weer te geven.

   ![gebruikte opties](assets/csf-options-usage.png)


## Gebruikersmachtigingen {#user-permissions}

In de volgende tabel worden de machtigingen weergegeven die vereist zijn voor het uitvoeren van bewerkingen, verwijderen en voorvertoningen van handelingen op zoekformulieren.

<table>
 <thead>
  <tr>
   <td><strong>Handeling</strong></td>
   <td><strong>Machtigingen</strong></td>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td>Bewerken </td>
   <td>Lezen, schrijven toestemmingen op <code>/apps </code>knooppunt.</td>
  </tr>
  <tr>
   <td>Verwijderen</td>
   <td>De machtigingen Lezen, Schrijven en Verwijderen voor de <code>/apps</code> node</td>
  </tr>
  <tr>
   <td>Voorvertoning</td>
   <td>De machtigingen Lezen, Schrijven en Verwijderen voor de <code>/var/dam/content</code> knooppunt.<br /> Lezen, schrijven toestemmingen op <code>/apps</code> knooppunt.</td>
  </tr>
 </tbody>
</table>
