---
title: Interactieve video's
description: Leer hoe u in Dynamic Media werkt met interactieve video's en schokkende video's.
translation-type: tm+mt
source-git-commit: dfd225bbef6d3244130aca2f18dbef4006f2ae65
workflow-type: tm+mt
source-wordcount: '6015'
ht-degree: 3%

---


# Interactieve video&#39;s{#interactive-videos}


U kunt eenvoudig interactieve video&#39;s maken. U kunt deze video&#39;s ook wel shoppable video&#39;s noemen en de conversie rechtstreeks vanuit de video sturen. De betrokkenheid van de klant bij de video vindt plaats in een deelvenster naast de videospeler, waar gerelateerde service-, informatie- of productminiaturen worden weergegeven op basis van wat in de video wordt getoond. Klanten kunnen op de miniatuur tikken en rechtstreeks aan de service worden gekoppeld, het item toevoegen aan een winkelwagentje voor directe aankoop of worden gekoppeld aan een webpagina voor meer informatie.

Wanneer de video eindigt, wordt een visueel overzicht van al dienstenaanbod getoond om een vraag aan actie te drijven. Klanten hebben nog een kans om op het gewenste item te tikken. Handelbare en specifieke ervaringen zoals deze verhogen de betrokkenheid van klanten en conversies.

Zie ook [Interactieve afbeeldingen](/help/assets/dynamic-media/interactive-images.md).

## Interactieve video in actie {#interactive-video-in-action}

Als u een interactieve, shoppable video in actie wilt zien, klikt u op [Livedemo&#39;s](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html), bladert u naar de kop **[!UICONTROL Shoppable Media]** op de pagina en klikt u op de shoppable video om het afspelen te starten.

* Terwijl producten tijdens het afspelen in de video worden gebruikt, wordt het identieke product rechts weergegeven als een miniatuurafbeelding.

* Tik op de miniatuur om de video te pauzeren en de Snelle weergave van het product te openen. Tik bijvoorbeeld op de miniatuurafbeelding van de KitchenAid in de video om een centrifugeerweergave van 360 graden van de mixer te bekijken of zoom in om details van de mixer te zien.

Zie ook [Interactieve video gebruiken met Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html?lang=en#dynamic-media)

<!-- 

There was a link here that showed the video frame of an interactive video and when the reader clicked the frame the video would play https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/AXIS/index.html. This now needs to call a new interactive video

-->

<!-- 

[A frame from an interactive, shoppable video](assets/chlimage_1-126.png) *A video frame capture from an interactive, shoppable video.*

-->

>[!NOTE]
>
>Als u een interactieve video maakt om een webpagina te starten wanneer een gebruiker op een miniatuurafbeelding tikt, blokkeren sommige apparaten het openen van de pop-upwebpagina. Wijzig in dergelijke gevallen de instelling van de pop-upblokkering op het apparaat. Tik bijvoorbeeld op een Apple iPhone 6 op **[!UICONTROL Settings > Safari > Block Pop-ups]** en schuif het besturingselement naar **[!UICONTROL Off]**. Wanneer u nu een interactieve video afspeelt en op een miniatuur klikt, wordt u gevraagd of u de pop-up wilt openen. Als u akkoord gaat, wordt de webpagina geopend.

### Bekijk hoe interactieve video&#39;s worden gemaakt {#watch-how-interactive-videos-are-created}

Bekijk een analyse van 7 minuten en 30 seconden over [hoe interactieve video&#39;s worden gemaakt](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveVideo) [](https://outv.omniture.com?v=s4NHQ2dzqd7hIqWjeG2sIdyNWsTWyupA).
(Hoewel de videoanalyse met Activa op bestelling wordt gemerkt, zijn de principes en de stappen nog van toepassing op Interactive Video in Adobe Experience Manager Assets.)

### Adobe Klantsucces Webinar {#adobe-customer-success-webinar}

Met de webinar [Interactieve video, het delen van koppelingen en het delen van YouTube in Experience Manager Assets](https://adobecustomersuccess.adobeconnect.com/p1yxzdo4aec/) leert u hoe u interactieve video en andere functies kunt gebruiken om conversiegedreven gebeurtenissen te koppelen aan uw video marketing inhoud.

## Snel starten: Interactieve video&#39;s {#quick-start-interactive-videos}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve video&#39;s in Dynamic Media.

Zoek naar **Voorbeeld** rubriek binnen enkele taken van het Snelle Begin. Het bevat een korte zelfstudie die is gebaseerd op deze [startdemo-webpagina die *nog niet* interactiviteit heeft toegevoegd aan deze ](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-0.html).

Met behulp van de **voorbeelden** kunt u de stappen illustreren voor het integreren van interactieve video&#39;s op uw eigen website.

Wanneer u de zelfstudie in de laatste voorbeeldsectie hebt voltooid, wordt [de laatste demo-webpagina met de volledig geïntegreerde interactieve video op deze manier weergegeven](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-3.html).



Interactieve videostappen:

1. **(Optioneel) Variabelen**  in de Snelle weergave identificeren - Begin door dynamische variabelen te identificeren die worden gebruikt door uw bestaande implementatie in de Snelle weergave. U gebruikt de variabelen om productminiaturen toe te wijzen aan hun overeenkomstige product Snelle mening wanneer u uw interactieve video creeert. Zie [(Optioneel) Variabelen in de Snelle weergave identificeren](#optional-identifying-quickview-variables).
   **Deze stap is alleen vereist als aan alle volgende voorwaarden wordt voldaan**: ・ U wilt interactiviteit aan uw video toevoegen door aan Snelle meningen in werking te stellen.
・ Uw implementatie van Experience Manager maakt *niet* gebruik van een eCommerce-integratieframework om productgegevens vanuit elke eCommerce-oplossing, zoals IBM WebSphere® Commerce, Elastic Path, hybris of Intershop, naar de Experience Manager te halen.

1. **(Optioneel) Een voorinstelling**  voor een interactieve videoviewer maken: pas de weergave en het gedrag aan van de verschillende componenten waaruit de speler bestaat, zoals de videoscrubber en de interactieve miniaturen.
Het is niet nodig een eigen voorinstelling voor een interactieve videoviewer te maken als u de voorinstellingen `Shoppable_Video_Light` of `Shoppable_Video_Dark` voor de externe interactieve videoviewer wilt gebruiken.
Zie [Een nieuwe voorinstelling voor de viewer maken](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) (optioneel) en [Speciale overwegingen voor het maken van een interactieve voorinstelling voor de viewer](/help/assets/dynamic-media/managing-viewer-presets.md#special-considerations-for-creating-an-interactive-viewer-preset).

1. **Een video en de bijbehorende afbeeldingselementen**  uploaden: hiermee kunt u een video en de bijbehorende afbeeldingen uploaden die u interactief wilt maken.
Zie [Een video en de bijbehorende miniatuurelementen uploaden](#uploading-a-video-and-its-associated-thumbnail-assets).

1. **Interactiviteit toevoegen aan uw video**  - Voeg een of meer tijdsegmenten toe aan de video. Koppel vervolgens afbeeldingsminiaturen aan die tijdsegmenten. Wijs elke afbeeldingsminiatuur toe aan een handeling zoals een hyperlink, een Snelle weergave of een Experience-fragment.
(De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.)
Voltooi de bewerking door de interactieve video-elementen te publiceren. Bij het publiceren wordt de insluitcode of URL gemaakt die u uiteindelijk kopieert en toepast op de bestemmingspagina van uw website. Zie [Interactiviteit toevoegen aan uw video](#adding-interactivity-to-your-video).
Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

1. **Een interactieve video toevoegen aan uw website of uw website in Experience Manager**  - Als u de Plaatsen van de Experience Manager, of Experience Manager eCommerce, of allebei gebruikt, kunt u de interactieve video aan een Web-pagina in Experience Manager direct toevoegen. Sleep de component Interactieve media naar de pagina. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)
Gebruik de insluitcode of URL om uw interactieve video te integreren met uw ervaringen op de website. Zie [Een interactieve video integreren met uw website](#integrating-an-interactive-video-with-your-website).
Als u WCM (Web Content Manager) van derden gebruikt, moet u de nieuwe interactieve video integreren met de bestaande implementatie van de Snelle weergave die op uw website wordt gebruikt. Zie [Een interactieve video integreren met een bestaande Snelle weergave](#integrating-an-interactive-video-with-an-existing-quickview).
   [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

## (Optioneel) Variabelen in de Snelle weergave {#optional-identifying-quickview-variables} identificeren

>[!NOTE]
Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
* U wilt interactiviteit aan uw video toevoegen door aan Snelle meningen te teweegbrengen.
* Uw implementatie van Experience Manager maakt *niet* gebruik van een eCommerce-integratieframework om productgegevens vanuit elke eCommerce-oplossing, zoals IBM WebSphere® Commerce, Elastic Path, hybris of Intershop, naar de Experience Manager te halen. <!-- See [eCommerce concepts in Experience Manager Assets](/help/sites-administering/concepts.md).-->

Als uw implementatie van Experience Manager eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande Snelle meningsimplementatie worden gebruikt zodat u productduimnagels aan hun overeenkomstige product kunt in kaart brengen Snelle mening tijdens het interactieve videoaanmaakproces.

Wanneer u tijdsegmenten aan een video toevoegt, wijst u SKU (Stock Keeping Unit) en om het even welke extra variabelen aan elke duimnagel toe u aan een segment toevoegt. Dergelijke variabelen worden later gebruikt om het juiste Snelle meningsproduct te tonen.

Het is belangrijk om correct te identificeren welke variabelen worden vereist om een product Snelle mening uniek teweeg te brengen.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor uw bestaande implementatie van Snelle weergave. Ze weten waarschijnlijk de minimale gegevensset die de Snelle weergave in het systeem identificeert. Het is echter mogelijk om gewoon het bestaande gedrag van de front-end code te analyseren.

Bij de meeste implementaties in de Snelle weergave wordt het volgende paradigma gebruikt:

* De gebruiker activeert een gebruikersinterface-element op de website. Als u bijvoorbeeld op een knop in de Snelle weergave klikt.
* De website verzendt een Ajax-aanvraag naar de achterkant om de gegevens of inhoud van de Snelle weergave te laden, indien nodig.
* De gegevens van de Snelle weergave worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

De aanpak bestaat er daarom uit verschillende delen van uw bestaande website te bezoeken waar Snelle weergave wordt geïmplementeerd. Vervolgens activeert u de Snelle weergave en legt u de URL van Ajax vast die door de webpagina is verzonden om de gegevens of inhoud van de Snelle weergave te laden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Als u alle uitgaande HTTP-aanvragen in Google Chrome wilt bekijken, drukt u op **F12** (Windows) of **Command+Options+I** (Mac) om het deelvenster Gereedschappen voor ontwikkelaars te openen en klikt u vervolgens op het tabblad **Netwerk**.

* In Firefox kunt u de Firebug-plug-in activeren door op **F12** (Windows) of **Command+Option+I** (Mac) te drukken en de tab **[!UICONTROL Net]** te gebruiken, of u kunt het ingebouwde controlemiddel en de tab Netwerk gebruiken.

* Activeer in Internet Explorer het foutopsporingsprogramma door op **F12** te drukken.

Wanneer netwerkcontrole is ingeschakeld in de browser, activeert u de Snelle weergave op de pagina.

Zoek nu de URL van de Snelle weergave Ajax in het netwerklogboek en kopieer de opgenomen URL voor toekomstige analyse. Wanneer u de Snelle weergave activeert, zijn er gewoonlijk veel verzoeken die naar de server worden verzonden. De URL van de Snelle weergave Ajax is doorgaans een van de eerste in de lijst. Het heeft of een complex gedeelte van het vraagkoord of weg, en zijn reactieMIME type of `text/html`, `text/xml`, of `text/javascript` is.

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat in de Snelle weergave-URL&#39;s onderdelen voorkomen die veel voorkomen in een bepaalde categorie websites, maar deze URL alleen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval is het enige variabele deel in de URL van de Snelle weergave de product-SKU. In dit geval is de product-SKU-waarde het enige gegevensstuk dat nodig is om miniaturen toe te voegen aan een tijdsegment in de interactieve video in Experience Manager.

In complexe gevallen heeft de URL van de Snelle weergave echter andere variërende elementen naast de SKU van het product, zoals categorie-id en kleurcode. In dergelijke gevallen wordt elk element van deze aard een aparte variabele in de definitie van miniatuurgegevens in de Experience Manager.

Bekijk de volgende voorbeelden van URL&#39;s in de Snelle weergave en de resulterende miniatuurvariabelen:

<table>
  <tbody>
  <tr>
    <td><p>Enige SKU, die in het vraagkoord wordt gevonden.</p> </td>
    <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige variabele deel in URL is de waarde van <code>productId=</code> de parameter van het vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben de duimnagels slechts gebieden SKU met waarden zoals <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong> nodig.</p> </td>
  </tr>
  <tr>
    <td><p>Eén SKU, gevonden in het URL-pad.</p> </td>
    <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van miniaturen van Experience Managers: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks.</p> </td>
    <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. De SKU wordt opgeslagen in de <code>prodId</code> parameter en categorie ID wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de miniatuurdefinities paren. Dat wil zeggen, een SKU-waarde en een extra variabele met de naam <code>categoryId</code>. De resulterende paren zijn:</p>
    <ul>
      <li>SKU is <code>305466</code> en <code>categoryId</code> is <code>1100004</code></li>
      <li>SKU is <code>310181</code> en <code>categoryId</code> is <code>1100004</code></li>
      <li>SKU is <code>308706</code> en <code>categoryId</code> is <code>1740148</code></li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Voorbeeld**

Wanneer de bovenstaande benadering wordt toegepast op de website van het Voorbeeld, hebt u een Web-pagina met verscheidene productduimnagels, elk met een &quot;ZIE MEER&quot;knoop:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-0.html)

Nadat u alle product Snelle meningen activeert beschikbaar op de pagina, krijgt u de volgende lijst van Snelle meningsverzoeken die aan het achterste eind worden gemaakt:

* datafeed/candles-233396346.json
* datafeed/candles-233978050.json
* datafeed/candles-234024346.json
* datafeed/candles-234024356.json
* datafeed/candles-234024359.json
* datafeed/cushions-233939848.json
* datafeed/cushions-234019477.json
* datafeed/cushions-234019483.json
* datafeed/furniture-231747479.json
* datafeed/furniture-232625621.json
* datafeed/furniture-232625626.json
* datafeed/furniture-233939810.json
* datafeed/furniture-233939825.json
* datafeed/furniture-233939828.json
* datafeed/furniture-233939853.json
* datafeed/furniture-233940334.json
* datafeed/glassware-000064007.json
* datafeed/glassware-230722193.json
* datafeed/glassware-233916550.json
* datafeed/glassware-233916597.json

Wanneer u de serveraanroepen bekijkt, is productspecifieke informatie alleen aanwezig in het aanvraagpad. U merkt ook dat het vraagkoord helemaal niet wordt gebruikt, en er zijn twee verschillende types van gegevensstukken in kwestie:

* Het eerste type is kaarsen, kussens, meubelen en glaswerk. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productcode, zoals 233916597. Je kan aannemen dat het &quot;product SKU&quot; is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van deze analyse concludeert u dat u de volgende twee variabelen kunt gebruiken voor de miniaturen: `categoryId` en `SKU`.

U kunt nu een video en de bijbehorende miniatuurelementen uploaden.

## (Optioneel) Een voorinstelling voor een interactieve videoviewer maken {#optional-creating-an-interactive-video-viewer-preset}

U kunt deze taak overslaan en verdergaan naar de volgende taak als u van plan bent om één van beide standaard, uit-van-de-doos Interactieve Video vooraf ingestelde types `Shoppable_Video_dark` of `Shoppable_Video_light` te gebruiken.

Wanneer in de ontwerpomgeving op een miniatuur wordt getikt, wordt een voorbeeld van het dialoogvenster Snelle weergave weergegeven.

![chlimage_1-21](assets/chlimage_1-127.png)

U kunt desgewenst uw eigen aangepaste voorinstelling voor een interactieve videoviewer maken. U kunt onder andere de opmaak bepalen van de videospeler, de interactieve miniaturen en de weergave van het miniatuurraster die aan het einde van de video wordt weergegeven.

Een voorinstelling voor een interactieve videoviewer geeft de video en alle tijdlijnsegmenten die u hebt toegevoegd correct weer. Er wordt ook een voorbeeld van de standaard Snelle weergave gebruikt wanneer u op een productminiatuur in de modus Voorbeeld klikt, zodat u de interactiviteit kunt testen voordat u de miniatuur publiceert.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt de status ervan automatisch ingesteld op **On** (Ingeschakeld) op de pagina Viewervoorinstellingen. Deze status betekent dat deze zichtbaar is in de component Dynamische media en wanneer u een voorvertoning van een video weergeeft. Zorg ervoor dat u de nieuwe viewervoorinstelling ook handmatig publiceert.

Zie [Een nieuwe voorinstelling voor de viewer maken](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) om uw eigen voorinstelling voor de interactieve videoviewer te maken.

## Een video en de bijbehorende miniatuurelementen uploaden {#uploading-a-video-and-its-associated-thumbnail-assets}

Als u de video en miniatuurelementen al hebt geüpload, gaat u verder naar [Interactiviteit toevoegen aan uw video](#adding-interactivity-to-your-video).

Als u de verkeerde video&#39;s of afbeeldingen hebt geüpload of als u geüploade video&#39;s of afbeeldingen wilt verwijderen die u niet meer nodig hebt, raadpleegt u [Elementen verwijderen](/help/assets/manage-digital-assets.md#delete-assets).

Een video en de bijbehorende miniatuurelementen uploaden:

1. Upload de video en de bijbehorende miniatuurbestanden naar de gewenste map of mappen.

   Zie [Elementen uploaden](/help/assets/manage-digital-assets.md).
Zie [Elementen uploaden met FTP-taakplanning](/help/assets/manage-digital-assets.md).

   Voeg nu interactiviteit toe aan uw video.

## Interactiviteit toevoegen aan uw video {#adding-interactivity-to-your-video}

U voegt tijdlijnsegmenten aan een video toe met de lokale visuele editor op de pagina Interactieve video maken.

Nadat u tijdlijnsegmenten hebt toegevoegd, voegt u miniatuurafbeeldingen toe binnen elk segment. Voor elke miniatuur die u toevoegt, past u er een actie op toe. U kunt bijvoorbeeld een Snelle weergave toepassen op de miniatuur, u kunt er een hyperlink aan toewijzen of u kunt een Experience Fragment toevoegen.

Zie [Fragmenten ervaren](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
Gereedschappen voor het delen van sociale media in interactieve video worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. In plaats daarvan kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

>[!NOTE]
De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Nadat u de interactieve video hebt opgeslagen, wordt de video direct geopend in Voorvertoning. Van daaruit kunt u een voorinstelling voor een interactieve videoviewer selecteren en de video afspelen om bij benadering te zien hoe deze er voor klanten uitziet.

**Interactiviteit toevoegen aan uw video**:

1. Navigeer in de weergave Elementen naar de video die u hebt geüpload en maak een interactieve video.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Select]** (vinkpictogram) op de afbeelding. Tik op **[!UICONTROL Edit]** op de werkbalk.

   * Tik op **[!UICONTROL More actions]** (drie punts pictogram) **[!UICONTROL > Edit]**.

   * Tik op de afbeelding om deze te openen op de pagina Detailweergave. Tik op **[!UICONTROL Edit]** op de werkbalk.

1. Voer op de pagina Interactieve video maken een van de volgende handelingen uit:

   * Tik op de knop **[!UICONTROL Play]** om de video af te spelen. Tik op **[!UICONTROL Add Segment]** op de werkbalk wanneer een bepaald product, een bepaalde service of een bepaald detail dat u wilt markeren, in beeld komt. Herhaal deze bewerking totdat u het einde van de video hebt bereikt.

      Voor elk tijdsegment dat u toevoegt, kunt u er een of meer miniatuurafbeeldingen aan toewijzen. Vervolgens kunt u deze miniaturen koppelen aan productpagina&#39;s in de Snelle weergave die klanten kunnen kopen of aan webpagina&#39;s voor meer informatie.

   * Tik op de knop **[!UICONTROL Play]** om de video af te spelen. Tik op **[!UICONTROL Pause]** wanneer een bepaald product, een bepaalde service of een bepaald detail dat u wilt markeren in beeld komt. Tik op **[!UICONTROL Add Segment]**.

      Ga door met het afspelen en pauzeren van de video op punten langs de tijdlijn waar u een segment wilt toevoegen totdat u het einde van de video hebt bereikt.

1. (Optioneel) Sleep de balk op de **[!UICONTROL Timeline Scale Slider]** naar links om in te zoomen of naar rechts om uit te zoomen. Met deze actie kunt u bepalen hoeveel details u ziet van de segmenten die u hebt toegevoegd.

   ![chlimage_1-22](assets/chlimage_1-128.png)

   Afhankelijk van de lengte van uw video, blijft de Duur van het Segment aan de volgende waarden in gebreke:

   <table>
      <tbody>
        <tr>
        <td><strong>Als de videolengte...</strong></td>
        <td><strong>De instelling voor Duur segment is standaard ingesteld op...</strong></td>
        </tr>
        <tr>
        <td>3 minuten of meer</td>
        <td>60 seconden</td>
        </tr>
        <tr>
        <td>2-3 minuten</td>
        <td>30 seconden</td>
        </tr>
        <tr>
        <td>1-2 minuten</td>
        <td>20 seconden<br /> </td>
        </tr>
        <tr>
        <td>30-60 seconden</td>
        <td>10 seconden</td>
        </tr>
        <tr>
        <td>30 seconden of minder</td>
        <td>5 seconden</td>
        </tr>
      </tbody>
    </table>

   De videotijdlijn gebruikt evenveel schermruimte als de ruimte die er beschikbaar voor is. Als u de grootte van de browser wijzigt, behouden de segmenten die u hebt toegevoegd de juiste breedte.

   Ter illustratie gebruiken de volgende drie schermafbeeldingen dezelfde video. U ziet dat de breedte van elk segment afhankelijk is van de instelling voor de tijdlijnschaal.

   ![chlimage_1-23](assets/chlimage_1-129.png)

   Schermafbeelding A

   Screenshot A hierboven toont u de standaardweergave van een 29-secondenproductvideo. De tijdlijnschaal wordt standaard ingesteld op 5 seconden.

   ![chlimage_1-130](assets/chlimage_1-130.png)

   Schermafbeelding B

   In bovenstaande afbeelding B werd de schuifregelaar Tijdlijnschaal van de standaardduur van 5 seconden naar 3 seconden gesleept. De afzonderlijke tijdstempels voor de schaal van de tijdlijn zijn nu allemaal ingesteld op intervallen van 3 seconden.

   ![chlimage_1-25](assets/chlimage_1-131.png)

   Screenshot C

   In bovenstaande screenshot C is de instelling voor Tijdlijnschaal verplaatst naar 8 seconden. U ziet hoe de segmenten met productminiaturen zijn verkleind. Op deze manier uitzoomen is handig als u een lange video hebt en u een overzicht wilt kunnen zien van meer segmenten die normaal gesproken in de breedte van de pagina passen.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * De begintijd en eindtijd van een segment aanpassen.

      Selecteer een segment en sleep vervolgens de voorloopblauwe of navolgende blauwe ovaal om respectievelijk de begin- of eindtijd aan te passen. Het weergegeven videoframe wordt op basis van uw aanpassingen naar de juiste tijd in de video verplaatst. De verplaatsing van het tijdlijnsegment wordt beperkt op basis van eventuele aangrenzende segmenten in de tijdlijn. De minimaal toegestane segmenttijd is één seconde.

      Gebruik de volgende sneltoetsen voor navigatie om uw videosegmenten snel te controleren en af te stemmen:

      * Tik op het blauwe ovaal vóór het begin van dat segment om de video direct naar het begin te zoeken.
      * Tik op het navolgende blauwe ovaal om de video direct naar het einde van dat segment te zoeken.
      * Tik op het hele segment om het afspelen van video terug te zetten naar het begin van dat segment.

   ![chlimage_1-26](assets/chlimage_1-132.png)

   Het einde van een tijdlijnsegment verplaatsen

   * Een segment verwijderen

      Selecteer het laatste segment dat zich op de tijdlijn bevindt en tik op **[!UICONTROL Delete Segment]** op de werkbalk. Als twee of meer segmenten zijn geselecteerd, is de functie Segment verwijderen uitgeschakeld.

      U kunt alleen het laatste segment verwijderen. Als u bijvoorbeeld alle segmenten op de tijdlijn wilt verwijderen, moet u altijd de laatste selecteren en vervolgens op **[!UICONTROL Delete Segment]** tikken.


1. Selecteer een tijdsegment waaraan u een of meer miniatuurafbeeldingen wilt koppelen.
1. Tik rechts van de video op het tabblad **[!UICONTROL Content]**.
1. Tik op **[!UICONTROL Select Assets]** onder het tabblad Inhoud en blader en selecteer alle afbeeldingselementen die u voor de video wilt gebruiken. De geselecteerde elementen worden toegevoegd aan het deelvenster Elementkiezer op het tabblad Inhoud.

1. Voer een van de volgende handelingen uit in de elementkiezer onder het tabblad Inhoud:

   <table>
      <tbody>
        <tr>
        <td>Een miniatuur koppelen aan het geselecteerde tijdlijnsegment</td>
        <td><p>Tik op de afbeelding in het deelvenster met middelenkiezers aan de rechterkant.</p> <p>U kunt zoveel miniaturen toevoegen als u wilt aan een tijdlijnsegment. Voor elke afbeelding die u selecteert, verschijnt een vinkje boven de afbeelding in de elementenkiezer.</p> </td>
        </tr>
        <tr>
        <td>Een miniatuur verwijderen uit het geselecteerde tijdlijnsegment</td>
        <td><p>Voer een van de volgende handelingen uit:</p>
          <ul>
          <li>Tik in het deelvenster met middelenkiezers op een afbeelding met een vinkje om de selectie ervan op te heffen. Het afbeeldingselement wordt verwijderd uit het tijdlijnsegment.<br /> </li>
          <li>Tik in het geselecteerde tijdlijnsegment op een afbeelding en tik vervolgens op de werkbalk op <strong>Product verwijderen</strong>.</li>
          </ul> </td>
        </tr>
      </tbody>
    </table>

   ![Elementkiezer](assets/chlimage_1-133.png)

   Tik op een afbeelding in het deelvenster met middelenkiezers om deze toe te voegen aan het geselecteerde tijdlijnsegment.

1. Selecteer één miniatuurafbeelding binnen een van de tijdlijnsegmenten en tik op het tabblad **[!UICONTROL Actions]**.
1. Voer een van de volgende handelingen uit:
   <table> 
    <tbody> 
      <tr> 
      <td>De geselecteerde miniatuurafbeelding aan een Snelle weergave koppelen</td> 
      <td><p>Tik onder Type handeling op <strong>Snelle weergave</strong>.</p> <p>Als u een klant van de Plaatsen van de Experience Manager en van de Handel bent:</p> 
       <ul> 
       <li>Het tekstveld SKU-waarde wordt vooraf ingevuld met de SKU (Stock Keeping Unit) van het geselecteerde product. SKU is een uniek herkenningsteken voor elk verschillend product of de dienst die u aanbiedt. Dit veld wordt automatisch ingevuld wanneer de afbeelding is gekoppeld aan een product in Experience Manager Commerce.</li> 
       <li>Als de vooraf ingevulde SKU onjuist is, tikt u op het pictogram Productkiezer (vergrootglas) of klikt u op dit pictogram om de pagina Selecteer product te openen. Tik op het product dat u wilt gebruiken en tik vervolgens op het vinkje in de rechterbovenhoek van de pagina. U gaat terug naar de Interactieve Video-editor.</li> 
       </ul> <p> Als u <em>not</em> een Plaats van de Experience Manager of een klant van de Handel bent</p> 
       <ul> 
       <li>Zie <a href="/help/assets/dynamic-media/carousel-banners.md#identifying-hotspot-and-image-map-variables">Hotspot-variabelen identificeren</a>. Deze variabelen moeten worden gedefinieerd.</li> 
       <li>Standaard gebruikt dit SKU-veld de bestandsnaam van het afbeeldingselement zonder de extensie. Als u een standaardnaamgevingsconventie volgt voor uw bestanden die op SKU zijn gebaseerd, hoeft dit veld gewoonlijk geen aanvullende bewerkingen uit te voeren. </li> 
       <li>Anders, geef de standaardwaarde uit en ga de correcte waarde SKU in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingegaan waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het Snelle meningsmalplaatje zodat het systeem weet om het in kaart gebrachte beeld met de Snelle mening van SKU te associëren.</li> 
       </ul> <p>(Optioneel) Tik op <strong>Algemene variabele toevoegen</strong> als er zich in de Snelle weergave andere variabelen bevinden die u moet gebruiken om een product nader te identificeren. Geef in het tekstveld een extra variabele op. <code>category=Womens</code> is bijvoorbeeld een toegevoegde variabele.</p> <p> </p> </td> 
      </tr> 
      <tr> 
      <td>De geselecteerde miniatuurafbeelding aan een hyperlink koppelen</td> 
      <td><p>Tik onder Type handeling op <strong>Hyperlink</strong> en voer een van de volgende handelingen uit:</p> 
       <ul> 
       <li>Als u een klant van de Plaatsen van de Experience Manager bent, tik het pictogram van de Selecteur van de Plaats (omslag) om aan een webpagina te navigeren. De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina's van de Plaatsen van de Experience Manager heeft.</li> 
       <li>Als u een zelfstandige Dynamic Media-klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.</li> 
       </ul> <p>Zorg ervoor dat u opgeeft of u de koppeling wilt openen op een nieuw browsertabblad of op het huidige tabblad.</p> </td> 
      </tr> 
      <tr> 
      <td>De geselecteerde miniatuurafbeelding aan een ervaringsfragment koppelen</td> 
      <td><p>Tik onder Type handeling op <strong>Fragment ervaren</strong> en voer de volgende handelingen uit:<p> 
       <ul> 
       <li>Als u een klant van de Plaatsen van de Experience Manager bent, tik het pictogram van het Onderzoek (vergrootglas) om de pagina van het Fragment van de Ervaring te openen. Tik of klik op het gewenste fragment van de Ervaring en tik op <strong>Als u wilt terugkeren naar het deelvenster Handelingen op de vorige pagina, selecteert u </strong>rechtsboven op de pagina.<br /> Zie Fragmenten  <a href="/help/sites-cloud/authoring/fundamentals/experience-fragments.md">ervaren</a>.</li> 
      </ul> 
       <ul> 
       <li>Geef de breedte en hoogte van het ervaringsfragment op zoals dit in de video wordt weergegeven.</li>
       </ul><strong>Opmerking</strong>: De gereedschappen voor het delen van sociale media in interactieve video worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. In plaats daarvan kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.</p></tr>&lt;&gt; 
      <tr> 
      <td>Een handeling bewerken die al is toegewezen aan een miniatuurafbeelding</td> 
      <td>Tik binnen een tijdlijnsegment op een miniatuurafbeelding met een kettingkoppeling rechts van het tekstlabel. De kettingkoppeling geeft aan dat er een handeling aan is toegewezen. Tik op het tabblad <strong>Handelingen</strong> om uw wijzigingen aan te brengen.</td> 
      </tr> 
      <tr> 
      <td>Het tekstlabel van een miniatuurafbeelding wijzigen</td> 
      <td><p>Standaard gebruikt het tekstlabel het metagegevensveld <code>Title</code> van de miniatuurafbeelding. Als <code>Title</code> niet aanwezig is, wordt in plaats daarvan de bestandsnaam van de miniatuurafbeelding gebruikt, maar zonder de extensie.</p> <p>Als u het tekstlabel van een miniatuurafbeelding wilt wijzigen, typt u de gewenste tekst onder het tabblad <strong>Handelingen </strong>direct onder het afbeeldingselement dat wordt weergegeven. Zie de onderstaande afbeelding.</p> <p>Het nieuwe tekstlabel wordt alleen gebruikt door de videospeler zelf en de miniatuurtekst die in het tijdlijnsegment wordt weergegeven. De labelwijziging heeft geen invloed op het metagegevensveld Titel van de miniatuurafbeelding en de bestandsnaam van de miniatuurafbeelding.</p> </td> 
      </tr> 
      <tr> 
      <td>Een aangebrachte wijziging herstellen</td> 
      <td>Tik in de rechterbovenhoek van de pagina op <strong>Ongedaan maken</strong> of <strong>Opnieuw</strong>.</td> 
      </tr> 
    </tbody> 
   </table>

   ![experienceExtension_interactivevideo&#39;s](assets/experiencefragment_interactivevideos.png)

   Er wordt een nieuw tekstlabel toegevoegd aan de miniatuurafbeelding.

1. Voer een van de volgende handelingen uit:

   * Herhaal stap 6-11 om meer miniatuurafbeeldingen toe te voegen aan tijdlijnsegmenten in uw video.
   * Ga verder met de optionele stap 13.

1. (Optioneel) Voer een van de volgende handelingen uit:

   * **[!UICONTROL Merge Segment]** - U kunt twee aangrenzende segmenten (met of zonder productminiaturen aan hen toegewezen) in één segment combineren.

      Tik in de tijdlijn op twee of meer aangrenzende segmenten die u wilt samenvoegen. Er zijn geen blauwe, ovale sleepgrepen op de twee geselecteerde segmenten in de onderstaande afbeelding.

      Tik **[!UICONTROL Merge Segment]** op de werkbalk.
   ![chlimage_1-134](assets/chlimage_1-134.png)

   Twee geselecteerde segmenten van vijf seconden samenvoegen tot één segment van tien seconden.

   * **[!UICONTROL Split Segment]** - U kunt één segment opsplitsen in twee segmenten met gelijke tijdnotatie. Als er al productminiaturen aan het segment zijn toegewezen, worden de miniaturen gecombineerd in het linkersegment.

      Tik op de tijdlijn op een segment dat u in tweeën wilt delen en tik op **[!UICONTROL Split Segment]** op de werkbalk.

      Als u twee of meer segmenten selecteert, wordt de functie **[!UICONTROL Split Segment]** uitgeschakeld.
   ![chlimage_1-135](assets/chlimage_1-135.png)

   Een geselecteerd segment van tien seconden opsplitsen in twee segmenten van vijf seconden elk.

1. In de rechterbovenhoek van de pagina **[!UICONTROL Create Interactive Video]** wordt de naam weergegeven van de momenteel geselecteerde viewer-voorinstelling die bij de video wordt gebruikt. Tik op de naam om een andere viewervoorinstelling te selecteren.

   Met de voorinstelling `Shoppable_Video_light` kunt u bijvoorbeeld de video afspelen met een wit weergavegebied naast de video. In het weergavegebied worden de aanklikbare miniatuurafbeeldingen tijdens het afspelen weergegeven. Met de voorinstelling `Shoppable_Video_dark` kunt u de video afspelen met een zwart weergavegebied naast de video.

   Als u uw eigen voorinstelling voor de interactieve videoviewer hebt gemaakt, wordt deze weergegeven in de lijst met voorinstellingen waaruit u kunt kiezen.

   Tik **[!UICONTROL Save]** als u klaar bent.

   >[!NOTE]
   Wanneer u uw interactieve video opslaat, wordt er automatisch een gekoppeld `.vtt`-bestand bij opgeslagen. Het `.vtt`-bestand wordt opgeslagen in de map `_VTT` in de hoofdmap van **[!UICONTROL Assets]**. Uw interactieve video kan alleen correct worden afgespeeld op uw website als het bestand en de map aanwezig zijn. Verplaats, bewerk of verwijder daarom de map `_VTT` of de content ervan niet.

1. Publiceer de interactieve video. Met Publiceren maakt u de insluitcode of URL die u uiteindelijk kopieert en plakt naar uw website.

   Als u interactiviteit hebt toegevoegd met Snelle weergaven, gebruikt u alleen de insluitcode. Als u interactiviteit hebt toegevoegd aan hypergekoppelde webpagina&#39;s, kunt u ook de gepubliceerde URL gebruiken. De op URL gebaseerde methode voor koppelen is echter niet mogelijk als uw interactieve inhoud koppelingen naar relatieve URL&#39;s bevat, met name koppelingen naar pagina&#39;s met Experience Managers Sites.

   Zie [Elementen publiceren](publishing-dynamicmedia-assets.md).

   >[!NOTE]
   Als u een schokkende video wilt publiceren met Snelle weergaven, moet u ook elk van de verwante afbeeldingselementen van de video afzonderlijk publiceren vanuit uw handelsgebied.

   Nadat u tijdlijnsegmenten hebt toegevoegd en de interactieve video hebt gepubliceerd, kunt u deze toevoegen aan de openingspagina van uw bestaande website. Zie [Een interactieve video integreren met uw website.](#integrating-an-interactive-video-with-your-website)

## Interactieve video-elementen publiceren {#publishing-interactive-video-assets}

Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van interactieve video-elementen.

## Een interactieve video integreren met uw website {#integrating-an-interactive-video-with-your-website}

Nadat u een video hebt geüpload, tijdlijnsegmenten hebt toegevoegd en de interactieve video hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

Als u een klant van de Plaatsen van de Experience Manager bent, kunt u de interactieve video toevoegen door de Interactieve component van Media aan uw pagina te slepen. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s.](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md)

Als u een zelfstandige klant van de Middelen van de Experience Manager bent, kunt u de interactieve video aan uw website manueel toevoegen zoals die in deze sectie wordt beschreven.

1. Kopieer de insluitcode of URL van de gepubliceerde interactieve video.
Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
Als u interactiviteit hebt toegevoegd met Snelle weergaven, gebruikt u alleen de insluitcode. Als u interactiviteit hebt toegevoegd aan hypergekoppelde webpagina&#39;s, kunt u ook de gepubliceerde URL gebruiken. De op URL gebaseerde methode voor koppelen is echter niet mogelijk als uw interactieve inhoud koppelingen naar relatieve URL&#39;s bevat, met name koppelingen naar pagina&#39;s met Experience Managers Sites.

1. Geef in de webpaginacode van het doel aan waar de statische video zich bevindt.
1. Verwijder de statische video en vervang de code door de insluitcode of URL die u uit de Elementen van de Experience Manager hebt gekopieerd.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch past in het gebied dat eerder werd ingenomen door de statische video.

>[!NOTE]
Als u nu alleen interactiviteit met hypergekoppelde webpagina&#39;s hebt toegevoegd, bent u klaar.
Als u echter interactiviteit hebt toegevoegd om een Snelle weergave te activeren, gelden de miniaturen naast de interactieve video alleen voor weergavedoeleinden. deze zijn nog niet geïntegreerd met uw bestaande Snelle weergaven. In dat geval moet u de interactieve video integreren met bestaande Snelle weergaven op uw website.

**Voorbeeld**

De demo-website als voorbeeld gebruiken:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-0.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-0.html)

De insluitcode voor video is standaard:

```xml
<style type="text/css">
 #s7video_div.s7videoviewer{
   width:100%;
   height:auto;
 }
</style>

<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/VideoViewer.js"></script>
<div id="s7video_div"></div>
<script type="text/javascript">
 var s7videoviewer = new s7viewers.VideoViewer({
  "containerId" : "s7video_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Video",
   "config2": "/etc/dam/presets/analytics",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "posterimage": "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 }).init();
</script>
```

Integratie is zo eenvoudig als het verwijderen van de video-insluitcode en het vervangen van deze code door de interactieve video-insluitcode uit de Experience Manager. U kunt het resultaat op de volgende URL zien. Hoewel er een interactieve video op de pagina wordt weergegeven, is deze nog niet geïntegreerd met de bestaande Snelle weergaven:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-1.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-1.html)

## Een interactieve video integreren met een bestaande Snelle weergave {#integrating-an-interactive-video-with-an-existing-quickview}

>[!NOTE]
Deze taak is slechts van toepassing als u een stand-alone klant van de Activa van de Experience Manager bent.

De laatste stap in dit proces is het integreren van uw interactieve video met een bestaande Quick view-implementatie die op uw website wordt gebruikt. Er is geen oplossing voor de integratie die in alle gevallen werkt. Elke implementatie van de Snelle weergave is uniek. Daarom is een specifieke aanpak nodig waarbij een front-end IT-persoon wordt bijgestaan.

De bestaande implementatie van de Snelle weergave vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Snelle mening URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een AJAX verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achtergrondlogica retourneert de corresponderende gegevens of inhoud van de Snelle weergave terug naar de front-end code.
1. De front-end code laadt de Snelle meningsgegevens of inhoud.
1. Naar keuze, zet de voorste-eindcode de geladen Snelle meningsgegevens in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze aanroepen vertegenwoordigen geen onafhankelijke openbare API-aanroepen die door de webpaginalogica kunnen worden aangeroepen vanuit een willekeurige stap. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer een gebruiker op een miniatuur in de interactieve video tikt en tegelijkertijd de stap 1 en 2 van de interactieve video vervangt, wordt deze gebruikersinteractie door de viewer afgehandeld. De viewer retourneert een gebeurtenis naar de webpagina die alle miniatuurgegevens bevat die eerder aan de Experience Manager zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgezonden door de interactieve video.
* Hiermee maakt u een URL van de Snelle weergave op basis van de miniatuurgegevens.
* Triggert het proces waarbij de Snelle weergave vanaf de achtergrond wordt geladen en op het scherm wordt weergegeven.

Bovendien ondersteunt de Interactieve Video-viewer de modus Volledig scherm. De eindgebruiker activeert Snelle weergaven door op een miniatuur te klikken zonder het volledige scherm te verlaten. Om deze functionaliteit te bereiken, wijzigt u de front-end code zodat het modale dialoogvenster Snelle weergave aan de container van de kijker is gekoppeld. Voeg geen BODY van het document of een ander Webpagina-element toe dat niet beschikbaar is wanneer de kijker op volledig-schermwijze is. De code die deze taak uitvoert, luistert naar een andere viewer-callback die wordt verzonden nadat de viewer op de pagina is geladen.

De insluitcode die door Experience Manager wordt geretourneerd, heeft al een gebruiksklare gebeurtenishandler. Er wordt opmerkingen toegevoegd zoals in het volgende gemarkeerde codefragment wordt getoond:

```xml
<style type="text/css">
 #s7interactivevideo_div.s7interactivevideoviewer{
   width:100%;
   height:auto;
 }
</style>
<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/InteractiveVideoViewer.js"></script>

<div id="s7interactivevideo_div"></div>
<script type="text/javascript">
 var s7interactivevideoviewer = new s7viewers.InteractiveVideoViewer({
  "containerId" : "s7interactivevideo_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Video_light",
   "config2": "/etc/dam/presets/analytics",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "interactivedata": "content/dam/_VTT/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4.svideo.vtt",
   "VideoPlayer.contenturl": "https://adobedemo62-h.assetsadobe.com/is/content",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 })
 /* // Example of interactive video event for quickview.
   s7interactivevideoviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku; //SKU for product ID
    //To pass other parameter from the hotspot, you need to add custom parameter during the hotspot setup as parameterName=value
    loadQuickView(sku); //Replace this call with your quickview plugin
    //Please refer to your quickviewer plugin for the quickview call
    },
"initComplete":function() {
    //--- Attach quickview popup to viewer container so popup will work in fullscreen mode ---
    var popup = document.getElementById('quickview_div'); // get custom quickview container
    popup.parentNode.removeChild(popup); // remove it from current DOM
    var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
    var inner_container = document.getElementById(sdkContainerId);
    inner_container.appendChild(popup); //Attach custom quickview container to viewer
    }
   });
 */
 s7interactivevideoviewer.init();
</script>
```

Het is dus alleen nodig de commentaarmarkering van het gemarkeerde codefragment hierboven ongedaan te maken en de dummy-handlers te vervangen door code die specifiek is voor de specifieke webpagina.

Er zijn twee standaardcallback managers aanwezig in de standaard insluitcode: `quickViewActivate` en `initComplete`. De handler `quickViewActivate` wordt geactiveerd wanneer op een miniatuur wordt geklikt in de viewer. Gebruik deze optie om de viewer te integreren met de activeringslogica van de Snelle weergave. De handler `initComplete` wordt slechts één keer geactiveerd wanneer de viewer op de pagina wordt geladen. Deze handler wordt gebruikt om de locatie van het dialoogvenster Snelle weergave in het DOM van de webpagina aan te passen.

Het proces om de Snelle mening URL te construeren is tegengesteld aan het proces om duimnagelvariabelen te identificeren die vroeger in dit onderwerp worden behandeld. Aan de hand van de eerder geïdentificeerde URL-voorbeelden van de Snelle weergave kunt u in elk geval zien hoe de URL van de Snelle weergave wordt samengesteld:

<table>
  <tbody>
  <tr>
    <td><p>Single SKU, gevonden in het vraagkoord</p> </td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
    <td>Enkele SKU, gevonden in het pad URL</td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks</p> </td>
    <td><code class="code">s7interactivevideoviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
  </tbody>
</table>

De laatste stap om de URL van de Snelle weergave te activeren en het deelvenster Snelle weergave te activeren, vereist hoogstwaarschijnlijk de hulp van een front-end IT-persoon van uw IT-afdeling. Ze hebben de kennis om te weten hoe u de implementatie van de Snelle weergave nauwkeurig vanuit de juiste stap kunt activeren en beschikken over een gebruiksklare URL voor de Snelle weergave.

U kunt zien hoe deze stappen worden toegepast op de demo-website om een interactieve video volledig te integreren met de code van de Snelle weergave. Eerder in dit onderwerp werd de structuur van de URL van de Snelle weergave als volgt geïdentificeerd:

```xml
/datafeed/$CategoryId$-$SKU$.json
```

Het is eenvoudig om deze URL binnen de `quickViewActivate` manager te reconstrueren gebruikend `categoryId` en `sku` gebieden beschikbaar in het `inData` voorwerp dat tot de manager door middel van de code van de kijker als in het volgende wordt overgegaan:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige functieaanroep `loadQuickView()`. Deze functie heeft slechts één argument, namelijk de URL van de gegevens in de Snelle weergave. De laatste stap om de interactieve video te integreren is dus het toevoegen van de volgende coderegel aan de `quickViewActivate` manager:

```xml
loadQuickView(quickViewUrl);
```

Tot slot moet het dialoogvenster Snelle weergave zijn gekoppeld aan het containerelement van de viewer. De standaard insluitcode bevat voorbeeldstappen om deze functionaliteit te bereiken. Als u een verwijzing naar het containerelement van de viewer wilt verkrijgen, kunt u de volgende coderegels gebruiken:

```xml
var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
var inner_container = document.getElementById(sdkContainerId);
```

Hierbij is `inner_container` een verwijzing naar een `DIV`-element dat door de viewer wordt beheerd. U wilt dat het dialoogvenster een onderliggend item is van dat `DIV`.

De stappen om het element van het modale dialoogvenster daadwerkelijk te vinden en aan de bovenstaande container te koppelen, zijn specifiek voor hoofdletters en kleine letters. Ook hier kunt u de hulp inroepen van uw front-end ontwikkelaar die bekend is met uw Quick view-implementatie die nodig is.

Voor de voorbeeldwebsite wordt het modale dialoogvenster van de Snelle weergave geïmplementeerd als een `DIV`, waarbij de snelweergave-modale id rechtstreeks aan het document is gekoppeld `BODY`. De code waarmee dat dialoogvenster naar de container van de viewer wordt verplaatst, is daarom even eenvoudig als de volgende code:

```xml
var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
var inner_container = document.getElementById(sdkContainerId);
inner_container.appendChild(document.getElementById("quickview-modal"));
```

De volledige broncode ziet er als volgt uit:

```xml
<style type="text/css">
 #s7interactivevideo_div.s7interactivevideoviewer{
   width:100%;
   height:auto;
 }
</style>
<script type="text/javascript" src="https://demos-pub.assetsadobe.com/etc/dam/viewers/s7viewers/html5/js/InteractiveVideoViewer.js"></script>

<div id="s7interactivevideo_div"></div>
<script type="text/javascript">
 var s7interactivevideoviewer = new s7viewers.InteractiveVideoViewer({
  "containerId" : "s7interactivevideo_div",
  "params" : {
   "serverurl" : "https://adobedemo62-h.assetsadobe.com/is/image",
   "contenturl" : "https://demos-pub.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Video_light",
   "videoserverurl": "https://gateway-na.assetsadobe.com/DMGateway/public/demoCo",
   "interactivedata": "content/dam/_VTT/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4.svideo.vtt",
   "VideoPlayer.contenturl": "https://adobedemo62-h.assetsadobe.com/is/content",
   "asset" : "/content/dam/marketing/shoppable-video/john-lewis/shoppable-video-john-lewis-2014.mp4" }
 })
 // Example of interactive video event for quickview.
   s7interactivevideoviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku; //SKU for product ID
     var categoryId=inData.categoryId; //categoryId
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   "initComplete":function() {
    //--- Attach quickview popup to viewer container so popup will work in fullscreen mode ---
    var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId(); // get viewer container component
    var inner_container = document.getElementById(sdkContainerId);
    inner_container.appendChild(document.getElementById("quickview-modal"));
    }
   });
 s7interactivevideoviewer.init();
</script>
```

De laatste demo-website met de volledig geïntegreerde interactieve video ziet er als volgt uit:

[https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-3.html](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-video/john-lewis/landing-3.html)

## Snelle weergaven gebruiken om aangepaste pop-upvensters te maken {#using-quickviews-to-create-custom-pop-ups}

Zie [Snelle weergaven gebruiken om aangepaste pop-upvensters te maken](/help/assets/dynamic-media/custom-pop-ups.md).
—>