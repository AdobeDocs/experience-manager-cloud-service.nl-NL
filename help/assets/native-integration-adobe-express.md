---
title: Gebruik Content Advisor voor toegang tot AEM Assets in Adobe Express
description: Gebruik Content Advisor om AEM Assets rechtstreeks te ontdekken en te openen binnen de native Adobe Express-integratie.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 54e66597d60621743cb39ef0b8edb21b6eea6c8d
workflow-type: tm+mt
source-wordcount: '2483'
ht-degree: 0%

---

# Gebruik Content Advisor voor toegang tot AEM Assets in Adobe Express {#native-integration-adobe-express-using-content-advisor}

Adobe Experience Manager (AEM) Assets integreert native met Adobe Express, waardoor u middelen van AEM Assets rechtstreeks binnen de Express-interface kunt detecteren, benaderen en gebruiken met Content Advisor.

Content Advisor transformeert hoe u middelen ontdekt en gebruikt in Adobe Express door de creatieve workflow rechtstreeks te voorzien van intelligente, contextbewuste detectie van middelen. In plaats van te zoeken naar elementen door trefwoorden te typen, heeft Content Advisor relevante oppervlakken, goedgekeurde middelen op basis van uw canvasinhoud, campagnemateriaal en intent, zodat u sneller de juiste middelen kunt vinden.

Met slimme suggesties, toegang tot dynamische media-uitvoeringen en volledige zichtbaarheid in metagegevens van elementen kunt u met Content Advisor op efficiënte wijze elementen van AEM Assets zoeken, evalueren en gebruiken zonder Adobe Express te verlaten. Dit zorgt voor snellere content creation, beter hergebruik van bedrijfsmiddelen en een consistent gebruik van goedgekeurde, merkconforme middelen.

![&#x200B; de bannerbeeld van de Adviseur van de Inhoud &#x200B;](assets/content-advisor-banner-image.png)

U kunt ook elementen op het Express-canvas plaatsen en nieuwe of bewerkte inhoud terugzetten naar AEM Assets, zodat u verzekerd bent van gecentraliseerd beheer van bedrijfsmiddelen en beheer. Native integratie met Adobe Express biedt de volgende belangrijke voordelen:

* Snellere content creation dankzij de context-bewuste assetdetectie en aanbevelingen.

* Groter hergebruik van inhoud door bestaande elementen te bewerken en nieuwe elementen op te slaan naar AEM Assets.

* Snellere toegang tot goedgekeurde, voor kanalen geoptimaliseerde dynamische media-uitvoeringen.

* Minder tijd en moeite om nieuwe middelen of nieuwe versies te maken met behoud van de consistentie van merken.

## Vereisten {#prerequisites}

Toegang tot Adobe Express en ten minste één omgeving in AEM Assets. De omgeving kan elk van de Assets as a Cloud Service-opslagplaatsen zijn.

## AEM Assets gebruiken in Adobe Express-editor {#use-aem-assets-in-express}

Voer de volgende stappen uit om AEM Assets in Adobe Express Editor te gaan gebruiken:

1. Open de Adobe Express-webtoepassing.

2. Open een nieuw leeg canvas door een nieuwe sjabloon of een project te laden of door een element te maken.

3. Klik op **[!UICONTROL Assets]** in het navigatievenster aan de linkerkant. De vertoningen van Adobe Express [&#x200B; Adviseur van de Inhoud &#x200B;](#intelligent-asset-discovery-content-advisor), die van de bewaarplaatsen een lijst maakt die u gerechtigd bent tot toegang samen met de lijst van activa en omslagen beschikbaar op wortel-niveau.

4. Blader of onderzoek naar activa in uw bewaarplaats gebruikend [&#x200B; Adviseur van de Inhoud &#x200B;](#intelligent-asset-discovery-content-advisor), dan sleep en laat vallen hen op het canvas. U kunt ook op de elementen klikken om deze op het canvas te plaatsen. U kunt ![&#x200B; filter &#x200B;](assets/do-not-localize/filter.svg) activa door diverse criteria, zoals goedkeuringsstatus, dossiertype, MIME type, en afmetingen ook filtreren.

   >[!NOTE]
   >
   >Filteren op dimensie is niet van toepassing op video&#39;s.

   ![&#x200B; omvat activa van Assets toe:voegen-op &#x200B;](assets/native-express-content-advisor-home.png)

## Intelligente assetdetectie met Content Advisor {#intelligent-asset-discovery-content-advisor}

Met de Content Advisor kunt u relevante elementen detecteren aan de hand van intelligente, contextbewuste aanbevelingen die zijn gebaseerd op uw inhoud of campagnecorrectie van het canvas. Hiermee kunt u ook dynamische media-uitvoeringen selecteren die geschikt zijn voor gebruik.


De Adviseur van de inhoud toont de lijst van dossiers, omslagen, en inzamelingen in de meningen van de Lijst en van het Net. Hiermee kunt u elementen in de indelingen PNG, JPEG, PSD, MP4, SVG en PDF toevoegen aan het Express-canvas. U kunt de scrollable dossiers van PDF of een andere formaattypes ook voorproef door het ![&#x200B; pictogram van Info &#x200B;](assets/info-icon.svg) te klikken beschikbaar op de activakaart.

Klik het ![&#x200B; pictogram van Info &#x200B;](assets/info-icon.svg) pictogram om activa meta-gegevens ook te bekijken beschikbaar in het **[!UICONTROL Basic]** lusje of mening Dynamische vertoningen van Media beschikbaar in de [&#x200B; Dynamische Media &#x200B;](#dynamic-media-renditions-content-advisor) tabel. Sleep de voorgestelde inhoud naar het canvas. U kunt ook op het element klikken om deze automatisch op het canvas te plaatsen.

![&#x200B; meta-gegevens van Activa in Adobe Express &#x200B;](assets/express-native-integration-metadata.png)


>[!IMPORTANT]
> 
>Zorg ervoor dat u een **auteur** bewaarplaats van de **3&rbrace; drop-down lijst van de Bewaarplaats &lbrace;selecteert.** A **levering** bewaarplaats toont de eigenschappen van de Adviseur van de Inhoud niet.
>
> Bovendien heeft de **levering** bewaarplaats geen activa die in omslagen en inzamelingen worden georganiseerd. Alle elementen worden weergegeven op het hoofdniveau in een platte structuur.

Content Advisor biedt de volgende belangrijke functies:

* [AI Zoeken naar slimmere detectie van bedrijfsmiddelen](#content-advisor-ai-search)

* [Slimme suggesties op basis van context en intentie](#smart-suggestions-content-advisor)

* [Campagneringsbriefjes om relevante middelen te ontdekken](#campaign-briefs-content-advisor)

* [Dynamische media-elementuitvoeringen beschikbaar voor gebruik](#dynamic-media-renditions-content-advisor)

* [Metagegevens van toegangsmiddelen consistent met de Assets-weergave](#asset-metadata-content-advisor)

* [Toegangsfilters zijn consistent met de Assets-weergave](#filters-content-advisor)

* [Recente en opgeslagen zoekopdrachten openen en opnieuw gebruiken](#saved-searches-content-advisor)

* [Zoeken naar elementen in en tussen verzamelingen](#search-collections-content-advisor)

### AI Zoeken naar slimmere detectie van bedrijfsmiddelen {#content-advisor-ai-search}

De Adviseur van de inhoud gebruikt een geavanceerd onderzoeksvermogen dat de betekenis en de intentie achter de vraag van een gebruiker eerder dan het baseren op nauwkeurige sleutelwoordgelijken begrijpt. Het gebruikt Kunstmatige Intelligentie (AI) en machine het leren om nauwkeurigere en context-bewuste resultaten te leveren.

In tegenstelling tot de traditionele op trefwoorden gebaseerde zoekopdracht, waarbij naar exacte termen wordt gezocht, worden in AI-zoekopdrachten de relaties tussen woorden, concepten en gebruikersintentie geïnterpreteerd. Dit zorgt ervoor dat de gebruikers vinden wat zij-zelfs als hun vraag verschillend wordt gephrased, typos bevat, of in een andere taal is.

![&#x200B; AI Onderzoek naar activa in Adobe Express &#x200B;](assets/express-native-integration-ai-search.png)

Sommige hiervan zijn de belangrijkste voordelen:

* Meertalige ondersteuning: zoek in meerdere talen zonder exacte vertalingen. Gebruikers kunnen relevante inhoud vinden, ongeacht hun querytaal.

* Verwerkt spelfouten: interpreteert typefouten en spelfouten en zorgt ervoor dat de resultaten nauwkeurig zijn, zelfs met imperfecte invoer.

* Begrijpt synoniemen: levert resultaten voor verwante termen en woordgroepen, zodat gebruikers niet het juiste trefwoord hoeven te raden.

* Context-bewust zoeken: herkent de intentie achter een query, niet alleen de exacte woorden.

>[!IMPORTANT]
> 
>* De minimaal vereiste AEM-releaseversie voor toegang tot AI-zoekopdrachten in Content Advisor is `21994` .


### Slimme suggesties op basis van context en intentie {#smart-suggestions-content-advisor}

In Content Advisor worden slimme suggesties weergegeven op basis van de context en intentie van de inhoud in het Express canvas. Hierdoor kunt u snel middelen vinden en gebruiken die op uw inhoudsbehoeften zijn afgestemd zonder tijdrovende handmatige zoekopdracht.

![&#x200B; Voorgestelde inhoud van de Adviseur van de Inhoud in Adobe Express &#x200B;](assets/express-native-integration-suggested-content.png)

>[!IMPORTANT]
> 
>* In Content Advisor worden slimme suggesties weergegeven op basis van de context en intentie van de inhoud die beschikbaar is in de tekstlagen of de titel in het Express canvas. De resultaten worden niet weergegeven op basis van de afbeeldingen die op het canvas beschikbaar zijn.
>* U moet een GenAI Rider ondertekenen om deze functie te kunnen gebruiken in Content Advisor. Neem contact op met uw Adobe-vertegenwoordiger om GenAI-stuurprogramma te ondertekenen.
>* De minimaal vereiste AEM-releaseversie voor toegang tot deze functie is `21994` .
>* Slimme suggesties worden niet automatisch bijgewerkt wanneer u het canvas bijwerkt. Klik verfrissen pictogram op **het Voorgestelde paneel van de Inhoud** om de bijgewerkte lijst van suggesties te bekijken,

### Campagneringsbriefjes om relevante middelen te ontdekken {#campaign-briefs-content-advisor}

Met Content Advisor kunt u een kort campagneretablet uploaden om relevante elementen te detecteren zonder handmatig zoektrefwoorden in te voeren. Content Advisor analyseert de informatie in de campagneresamenvatting om inzicht te krijgen in de intentie van de campagne en raadt relevante middelen aan die beschikbaar zijn in AEM Assets.

![&#x200B; omvat activa van Assets toe:voegen-op &#x200B;](assets/upload-brief-native-express.png)

>[!IMPORTANT]
>
>* Content Advisor analyseert de informatie die beschikbaar is als tekst in de campagneremap om relevante elementen aan te bevelen. De beschikbare informatie wordt niet geanalyseerd als afbeeldingen in de campagneremap.
>* De ondersteunde bestandstypen die u kunt uploaden als een campagnecorrectie zijn onder andere PDF-, DOCX- en TXT-documenten.
>* U moet een GenAI Rider ondertekenen om deze functie te kunnen gebruiken in Content Advisor. Neem contact op met uw Adobe-vertegenwoordiger om GenAI-stuurprogramma te ondertekenen.
>* De minimaal vereiste AEM-releaseversie voor toegang tot deze functie is `21994` .

### Dynamische media-elementuitvoeringen beschikbaar voor gebruik {#dynamic-media-renditions-content-advisor}

De dynamische vertoningen van Media verstrekken klaar-aan-gebruik, kanaal-geoptimaliseerde versies van activa, met inbegrip van [&#x200B; beeld vooraf instelt &#x200B;](/help/assets/dynamic-media/managing-image-presets.md), [&#x200B; Slimme Uitsnijdingen &#x200B;](/help/assets/dynamic-media/image-profiles.md), formaattypes, en kleurenprofielen. Deze uitvoeringen helpen u ervoor te zorgen dat het geselecteerde element voldoet aan de vereisten voor kanalen en ontwerpen zonder dat handmatig bewerken of het dupliceren van middelen vereist is.

U kunt de opties Dynamische media ook toepassen om aanpassingen in real-time voor te vertonen voordat u de vertoning op het Express-canvas plaatst, zodat u sneller de meest geschikte vertoning kunt selecteren en tegelijkertijd de consistentie en kwaliteit van de elementen behoudt.

Klik het ![&#x200B; pictogram van Info &#x200B;](assets/info-icon.svg) pictogram op de activakaart en selecteer het **[!UICONTROL Dynamic Media]** lusje om de beschikbare vertoningen voor een activa te bekijken. U kunt selecteren om [&#x200B; Dynamische Media Scene7 &#x200B;](/help/assets/dynamic-media/dynamic-media.md) vertoningen of [&#x200B; Dynamische Media met OpenAPI &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) vertoningen te bekijken. Wanneer u **[!UICONTROL OpenAPI]** selecteert voor een element, worden de beschikbare uitvoeringen alleen weergegeven als het element is goedgekeurd en beschikbaar is voor Dynamic Media met OpenAPI.

U moet een geldige AEM Dynamic Media-licentie hebben om het tabblad Dynamische media weer te geven.

![&#x200B; de Dynamische vertoningen van Media van de Mening Dynamische &#x200B;](assets/native-express-dynamic-media.png)

Klik het ![&#x200B; pictogram van de voorproef &#x200B;](assets/do-not-localize/preview-icon.svg) pictogram aan voorproef de vertoning of klik de vertoningsnaam om hen automatisch op het canvas te plaatsen. U kunt ook een voorvertoning van de vertoning weergeven en deze vervolgens slepen en neerzetten om de afbeelding op het canvas te plaatsen.

![&#x200B; de Dynamische vertoningen van Media van de Voorproef &#x200B;](assets/native-express-dynamic-media-preview.png)

Klik op **[!UICONTROL Add Modifiers]**, geef een modifier op in het tekstvak en druk op Enter om de transformatie in real-time toe te passen op de uitvoeringen. Op dezelfde manier kunt u meerdere modifiers toevoegen aan een uitvoering en een voorvertoning van die transformaties weergeven. Sleep het element van de voorvertoning naar het canvas. De vertoning na het toepassen van deze modifiers wordt niet opgeslagen. Zie de lijst van gesteunde bepalingen voor [&#x200B; Dynamische Media Scene7 &#x200B;](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference) en [&#x200B; Dynamische Media met OpenAPI &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat).

>[!IMPORTANT]
> 
>Met Dynamic Media kunt u de 80 MB-limiet voor het uploaden van bestanden in Adobe Express (web) overwinnen door geoptimaliseerde uitvoeringen van grote middelen te bieden. Dynamische media-uitvoeringen reduceren de bestandsgrootte aanzienlijk, terwijl de visuele kwaliteit behouden blijft. Een TIFF-element van 300 MB kan bijvoorbeeld worden geleverd als een 2,5 MB-uitvoering zonder dat de kwaliteit in het gedrang komt, waardoor een efficiënt gebruik van middelen met hoge resolutie in Adobe Express mogelijk is.

### Metagegevens van toegangsmiddelen consistent met de Assets-weergave {#asset-metadata-content-advisor}

Content Advisor biedt toegang tot de eigenschappen van middelen die in AEM Assets zijn gedefinieerd, inclusief metagegevens die beschikbaar zijn in de Assets-weergave. Content Advisor gebruikt dezelfde configuratie van metagegevens als in Assets View, waarbij de lijst met tabbladen voor metagegevens en de inhoud wordt herhaald in de pagina met informatie over elementen in de Assets-weergave. Op deze manier kunt u belangrijke gegevens over elementen, zoals titel, beschrijving, indeling, grootte en andere metagegevens, controleren voordat u een element selecteert. Toegang tot de eigenschappen van elementen zorgt ervoor dat u het juiste en goedgekeurde middel voor uw inhoud kiest.

![&#x200B; de meningsmeta-gegevens van Assets in de Adviseur van de Inhoud &#x200B;](assets/native-express-asset-metadata.png)

Klik het ![&#x200B; pictogram van Info &#x200B;](assets/info-icon.svg) pictogram op de activakaart en selecteer het **[!UICONTROL Basic]** lusje om activa meta-gegevens te bekijken. U kunt ook andere tabbladen met metagegevens over elementen, zoals Product, Campagne en Tags, weergeven, in overeenstemming met de metagegevens over elementen die in de Assets-weergave worden weergegeven.

In Content Advisor worden eigenschappen (metagegevens) voor bestanden in een alleen-lezen weergave weergegeven. De eigenschappen worden niet weergegeven voor verzamelingen en mappen.

### Toegangsfilters zijn consistent met de Assets-weergave {#filters-content-advisor}

Content Advisor biedt in Express dezelfde filtermogelijkheden als in de Assets-weergave, zodat u elementen kunt verfijnen met behulp van vooraf gedefinieerde filters. Dezelfde filtermogelijkheden als beschikbaar in de Assets-weergave zijn ook van toepassing op de filters die specifiek zijn voor inhoudssoorten, zoals bestanden, mappen en verzamelingen. Dit zorgt voor een consistente ervaring met het detecteren van bedrijfsmiddelen en helpt u op efficiënte wijze relevante bedrijfsmiddelen te vinden in Adobe Express.

Als er geen filters zijn ingesteld in de Assets-weergave via een filterschema, worden in Content Advisor filters weergegeven die niet in de box staan, zoals Bestandstype, Bestandsindeling, Status van element, Bestandsgrootte, Afbeeldingsbreedte, Afbeeldingshoogte, Gewijzigde datum en Gemaakt op.

### Recente en opgeslagen zoekopdrachten openen en opnieuw gebruiken {#saved-searches-content-advisor}

Opgeslagen zoekopdrachten die in de Assets-weergave zijn gemaakt, zijn ook beschikbaar, zodat u vooraf gedefinieerde zoekcriteria opnieuw kunt gebruiken. Opgeslagen zoekopdrachten werken consistent tussen de Assets-weergave en Content Advisor in verschillende browsers. Op deze manier kunt u op efficiënte wijze middelen zoeken aan de hand van consistente zoekpatronen in AEM Assets en Adobe Express.

U slaat de veelgebruikte zoekopdracht op met Content Advisor:

1. Geef een zoekterm op (optioneel), klik op het pictogram Filters en selecteer de opties op basis van uw vereisten om een zoekquery te maken.

1. Klik op **[!UICONTROL Apply]** om de resultaten weer te geven.

1. Klik het filterpictogram > **beheert bewaarde onderzoeken** > **creeer nieuw Bewaarde Onderzoek**.

1. Specificeer de naam van het onderzoek en klik ![&#x200B; pictogram van Info &#x200B;](assets/do-not-localize/checkmark-icon.svg) om het te bewaren. De zoekopdracht wordt weergegeven in de lijst met items.

   ![&#x200B; Opgeslagen Adviseur van de Inhoud van Zoekopdrachten &#x200B;](assets/native-express-saved-searches.png)

Als u een van de opgeslagen zoekopdrachten wilt toepassen, klikt u op het pictogram met filters, selecteert u het zoekitem in de vervolgkeuzelijst **[!UICONTROL Saved Searches]** en klikt u op **[!UICONTROL Apply]** .

Met Content Advisor kunt u uw recente zoekopdrachten opslaan en veelgebruikte zoekopdrachten opslaan, zodat u ze later snel kunt openen. De lijst met recente zoekopdrachten is niet consistent tussen de Assets-weergave en Content Advisor. Dezelfde gebruiker kan verschillende recente zoekopdrachten uitvoeren in de Assets-weergave en in Content Advisor. Als u de modus Incognito gebruikt om toegang te krijgen tot Content Advisor, is de lijst met recente zoekopdrachten niet beschikbaar. Bovendien worden recente zoekopdrachten niet door verschillende browsers voor dezelfde gebruiker gedeeld en zijn deze specifiek voor de AEM-omgeving.



De functie Standaard opgeslagen zoekopdracht, die beschikbaar is in de Assets-weergave, is nog niet beschikbaar in Content Advisor.

### Zoeken naar elementen in en tussen verzamelingen {#search-collections-content-advisor}

Met Content Advisor kunt u zoeken naar elementen of verzamelingen in alle verzamelingen of uw zoekopdracht beperken tot een bepaalde verzameling. Hierdoor kunt u snel elementen van gekromde verzamelingen zoeken en gebruiken, terwijl de gewenste organisatiecontext behouden blijft.

## Afbeelding vervangen met AEM-upload {#replace-image-using-aem-upload}

Bovendien kunt u de toegevoegde afbeeldingen vervangen met **[!UICONTROL AEM Upload]** . Voer daartoe de volgende stappen uit:

1. Blader naar elementen of zoek ze en sleep ze naar het canvas.

1. Selecteer de afbeelding die u wilt vervangen. Klik op **[!UICONTROL Replace]** en selecteer **[!UICONTROL AEM Assets]** onder verschillende andere opties.

   ![&#x200B; AEM vervangt &#x200B;](assets/aem-replace.png)

1. [&#x200B; Adviseur van de Inhoud &#x200B;](#intelligent-asset-discovery-content-advisor) opent in de linkernavigatieruit. In Adobe Express wordt de lijst met opslagplaatsen weergegeven die u kunt openen, samen met de lijst met elementen en mappen die beschikbaar zijn op hoofdniveau. Selecteer een element om een voorvertoning van de vervanging op het canvas weer te geven en klik vervolgens op **[!UICONTROL Replace]** om te bevestigen.

   >[!NOTE]
   >
   > SVG-bestandstypen worden niet ondersteund.

## Adobe Express-projecten opslaan in AEM Assets {#save-express-projects-in-assets}

Nadat u de gewenste wijzigingen hebt aangebracht in het Express-canvas, kunt u het opslaan in AEM Assets.

1. Klik op **[!UICONTROL Share]** om het dialoogvenster **[!UICONTROL Share]** te openen.

   ![&#x200B; sparen activa in AEM &#x200B;](assets/adobe-express-share.png)

2. Selecteer **AEM Assets**. Adobe Express geeft het dialoogvenster voor uploaden weer.

3. Selecteer of **Huidige Pagina** of **Alle Pagina&#39;s**. Geef een naam en indeling op voor de elementen die u wilt exporteren. U kunt de inhoud van het canvas exporteren in de indelingen PNG, JPEG, PDF, MP4, MP4+PNG of MP4+JPEG. De opmaak wordt automatisch aangepast op basis van de elementen op de canvaspagina(&#39;s).
Het selecteren van **Huidige Pagina** slaat de activa op uw huidige pagina aan uw bestemmingsomslag op. Als u **Alle Pagina&#39;s** selecteert en het uitvoerformaat niet PDF is, worden alle canvaspagina&#39;s bewaard als afzonderlijke dossiers in een nieuwe omslag binnen uw bestemmingsomslag. Als de exportindeling PDF is, worden alle canvaspagina&#39;s als één PDF-bestand opgeslagen in de doelmap.

4. Klik het omslagpictogram onder **Omslag van de Bestemming** om een plaats te selecteren en de activa te bewaren.

   ![&#x200B; sparen activa in AEM &#x200B;](/help/assets/assets/page-selection-and-destination-folder.png)

5. Facultatief: U kunt campagnemetagegevens voor uw toevoegen gebruikend het **project of campagnenaam** gebied. U kunt een bestaande naam gebruiken of een nieuwe naam maken. U kunt meerdere project- of campagnenamen definiëren voor het uploaden. Als u de naam wilt registreren, typt u gewoon de naam en klikt u op Enter.
Het wordt aanbevolen dat Adobe waarden opgeeft in de rest van de velden en een verbeterde zoekervaring maakt voor uw geüploade elementen.

6. Definieer ook waarden voor de velden **[!UICONTROL Keywords]** en **[!UICONTROL Channels]** .

7. Klik op **[!UICONTROL Upload]** om de elementen te uploaden naar AEM Assets.

   <table> 
    <tbody>
     <tr>
      <th><strong>Ondersteunde indelingen</strong></th>
      <th><strong>Grootte</strong></th>
     </tr>
    </tr>
    <tr>
        <td>[!UICONTROL JPEG]</td>
        <td> 65 MP (bijvoorbeeld 8.000 x 8.000 of 16.000 x 4.000) </td>
    </tr>
    <tr>
        <td>[!UICONTROL PNG]</td>
        <td> 65 MP (bijvoorbeeld 8.000 x 8.000 of 16.000 x 4.000) </td>
    </tr>
    <tr>
        <td>[!UICONTROL SVG]</td>
        <td> Maximaal 250 kB</td>
    </tr>
    <tr>
        <td>[!UICONTROL MP4]</td>
        <td> 3840 x 3840 pixels, maximaal 200 MB</td>
    </tr>
    <tr>
      <td colspan="2"> <i> De grootte van het element moet minder zijn dan 80 MB voor bureaubladapparaten en 40 MB voor mobiele apparaten. </i></td>
   </tr>
    </tbody>
   </table>

## Beperkingen {#limitations}

1. Voor het importeren en exporteren is MP4 het ondersteunde videobestandstype.

2. Voor **MP4 videoinvoer**, worden de video&#39;s met transparante achtergronden (alpha- kanaal) niet gesteund.
   <!--
   1. The maximum file size supported is 200 MB. If this limit exceeds, an alert message displays.
   2. The maximum supported resolution is 3840 X 3840 pixels.
   3. Videos with transparent backgrounds (alpha channel) are not supported.
   -->

3. Voor **MP4 videouitvoer**, is de maximumgesteunde dossiergrootte 200 MB. Als deze limiet wordt overschreden, wordt in een waarschuwing aanbevolen de video te verkleinen tot 200 MB of minder, of deze handmatig te uploaden naar de AEM Assets-doelmap nadat deze is gedownload.

<!--
## Content Advisor Properties {#content-advisor-props}

You can configure following properties for the content advisor:

* `featureSet` : This property enables the Content Advisor MFE.

    ```
    featureSet: [
        ...defaultFeatures, /* to include all default features */
        'advisor', /* enables Content Advisor features */
        'content-fragments', /* enables Content Fragments */
    ],
    ```

* `rail:true/false` : If marked true, Content Advisor is rendered in a left rail view. If it is marked false, the Content Advisor is rendered in modal view.

## Browse assets using Content Advisor {#browse-assets-content-advisor}

<!--In the Modal View of Content Advisor, you can access both [Assets](#using-assets-tab) and [Content Fragments](#using-content-fragments) within a unified interface.

### Assets tab{#assets-tab}

The **[!UICONTROL Assets]** tab allows you to browse or filter available assets, preview them before selection, and choose appropriate **[!UICONTROL Dynamic Media]** [renditions](renditions.md) or [smart crops](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles) as needed. Assets, folders, and collections are presented together in a single, streamlined experience. The interface also provides contextual recommendations based on the integrated application context, helping you quickly identify relevant content.

Within assets tab, you can access content by browsing [Files and folders](#content-advisor-files-and-folders) or viewing [Collections](#content-advisor-collections).

### Files and Folders tab{#content-advisor-files-and-folders}

Browsing content using Files and Folders allows you navigate your assets in a familiar hierarchical structure, making it easy to locate assets within the repository. To browse assets within files and folders, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Files & Folders]**. A hierarchical structure is then displayed, allowing you to easily locate and select the desired assets.

![Browse assets using files and folder](assets/browse-assets-content-advisor.png)

### Collections tab{#content-advisor-collections}

Browsing content using Collections allows you to access curated groups of assets within Collections. To browse assets within Collections, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Collections]**. The interface then displays curated groups of assets, enabling you to browse the content you need.

![Browse assets using Collections](assets/browse-assets-collections.png)

<!--
### Content Fragments tab{#content-fragments}

The [Content Fragments](/help/assets/content-fragments/content-fragments.md) tab displays structured assets, allowing you to browse, search, and filter fragments efficiently within the same interface. To browse assets using Content Fragments, navigate to the **[!UICONTROL Content Fragments]** tab to access and explore the fragments available in the repository.

![Browse assets using Content Fragments](assets/browse-assets-content-fragment.png)
-->


