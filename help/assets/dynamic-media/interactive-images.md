---
title: Interactieve afbeeldingen
description: Leer hoe u met interactieve afbeeldingen werkt in Dynamic Media.
contentOwner: Rick Brough
feature: Interactive Images
role: User
exl-id: 89eef5e6-d508-4f33-b54e-24d4df49f8c3
source-git-commit: bae9a5178c025b3bafa8ac2da75a1203206c16e1
workflow-type: tm+mt
source-wordcount: '4039'
ht-degree: 0%

---

# Interactieve afbeeldingen{#interactive-images}

U kunt statische afbeeldingen eenvoudig verrijken en aantrekkelijke ervaringen voor klanten creëren door &#39;onoverzichtelijke&#39; hotspots naar een afbeelding te slepen. Slepbare hotspots combineren aanvullende informatie over een product of service met een directe, verkooppuntfunctie &#39;Toevoegen aan winkelwagentje&#39; of &#39;Kopen&#39;. Klanten kunnen deze hotspots selecteren die rechtstreeks aan het product of de service zijn gekoppeld, deze aan een winkelwagentje toevoegen of aan een webpagina zijn gekoppeld. Directe ervaringen zoals deze verhogen de betrokkenheid van klanten en conversies op uw website.

Hier volgt een blaasbare banner met een pop-upvenster van QuickView. Een gebruiker activeert de Snelle weergave door op de cirkel of de hotspot op het model te tikken.

![ chlimage_1-152 ](assets/chlimage_1-368.png)

Zie [ interactieve beelden in actie ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html) op de Web-pagina hierboven wordt afgebeeld.

## Controleren hoe interactieve afbeeldingsbanners worden gemaakt {#watch-how-interactive-image-banners-are-created}

Bekijk een analyse op [ hoe de interactieve beeldbanners ](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minuten en 33 seconden) worden gecreeerd. U leert ook hoe u interactieve afbeeldingsbanners kunt voorvertonen, bewerken en leveren.

## Snel starten: Interactieve afbeeldingen {#quick-start-interactive-images}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve afbeeldingen in Adobe Experience Manager Assets.

Zoek de **rubriek van het Voorbeeld** binnen sommige van de Snelle taken van het Begin. Het bevat een korte zelfstudie die op a [ Web-pagina voorbeeld gebaseerd is dat nog geen Interactieve Beelden heeft die aan het ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html) worden toegevoegd.



De zelfstudie helpt u de stappen te illustreren voor het integreren van interactieve afbeeldingen op uw eigen website.

Stappen voor interactieve afbeeldingen:

1. **(Optioneel) Identificeer hotspot-variabelen** . Als u Adobe Experience Manager Assets en Dynamic Media standalone gebruikt, identificeer dynamische variabelen die in uw bestaande implementatie van de QuickView worden gebruikt. Zo weet u zeker dat u hotspotgegevens kunt invoeren wanneer u de interactieve afbeelding maakt. Zie [ (Optioneel) Hotspot-variabelen identificeren ](#optional-identifying-hotspot-variables) .
Nochtans, als u Experience Manager Sites, of Experience Manager eCommerce, of allebei gebruikt, dan is deze stap niet noodzakelijk.

1. **(Optioneel) Maak een voorinstelling voor een interactieve afbeeldingsviewer.** Pas de grafische afbeelding aan die wordt gebruikt om hotspots te vertegenwoordigen. U hoeft geen eigen voorinstelling voor de interactieve afbeeldingsviewer te maken als u in plaats daarvan de voorinstelling voor de externe interactieve afbeeldingsviewer met de naam `Shoppable_Banner` wilt gebruiken.
Zie [ (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken ](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset) .

1. **upload een beeldbanner**. Upload afbeeldingsbanners die u interactief wilt maken.
Zie [ Uploading een beeldbanner ](#uploading-an-image-banner).

1. **voeg hotspots aan een beeldbanner** toe. Voeg een of meer hotspots toe aan een afbeeldingsbanner. Koppel elke koppeling aan een handeling zoals een hyperlink, Snelle weergave of een ervaringsfragment. Nadat u hotspots hebt toegevoegd, kunt u deze taak voltooien door de interactieve afbeelding te publiceren.
Zie [ Toevoegend hotspots aan een beeldbanner ](#adding-hotspots-to-an-image-banner).
Zie [ het Voorproeven van interactieve beelden ](#optional-previewing-interactive-images) - Facultatief. U kunt desgewenst een representatie van de verscherpte banner bekijken en de interactiviteit ervan testen.
Zie [ het Publiceren Assets ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor details op hoe te om interactieve beeldactiva te publiceren.

1. **voeg een interactief beeld aan uw website of aan uw website in Experience Manager** toe. Als u Sites of eCommerce gebruikt, of beide, kunt u interactieve beelden direct aan een Web-pagina in Experience Manager toevoegen. Sleep de component Interactieve media naar de pagina. Zie [ Toevoegend Dynamic Media Assets aan Pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Als u Experience ManagerAssets en Dynamic Media op zichzelf gebruikt, kopieert u de insluitcode naar uw website. Dan, integreer het met uw bestaande Snelle mening. Zie [ Integrerend een interactief beeld met uw website ](#integrating-an-interactive-image-with-your-website).
Als u WCM (Web Content Manager) van derden gebruikt, integreert u de nieuwe interactieve video met de bestaande Snelle weergave die op uw website wordt gebruikt. Zie [ Integrerend een interactief beeld met een bestaande QuickView ](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optioneel) Hotspotvariabelen identificeren {#optional-identifying-hotspot-variables}

>[!NOTE]
>
>Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
>
>* U wilt interactiviteit aan uw beeld toevoegen door aan Snelle meningen te teweegbrengen.
>* Uw implementatie van Experience Manager gebruikt ** geen eCommerce integratiekader om productgegevens in Experience Manager van om het even welke oplossing van de eCommerce te trekken. Tot deze oplossingen behoren IBM® WebSphere® Commerce, Elastic Path, SAP Hybris of Intershop.
>
>Als uw implementatie van Experience Manager eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande implementatie van QuickView worden gebruikt zodat u hotspot gegevens kunt ingaan om het interactieve beeld tot stand te brengen.

Wanneer u hotspots toevoegt aan een bannerafbeelding in Experience Manager Assets, wijst u een SKU (Stock Keeping Unit) toe. SKU is een uniek herkenningsteken voor elk verschillend product of de dienst die u aanbiedt. Voeg desgewenst extra optionele variabelen toe aan elke hotspot. Dergelijke hotspotvariabelen worden later gebruikt om hotspots te laten overeenkomen met Quickview-inhoud.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot gegevens te associëren. Elke hotspot die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie bevatten om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem.

Er zijn verschillende manieren om een set variabelen te identificeren die voor hotspot-gegevens moet worden gebruikt.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van QuickView. Dergelijke mensen zullen waarschijnlijk weten wat de minimumreeks gegevens wordt vereist om Snelle mening in het systeem te identificeren. Het is echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Selecteer bijvoorbeeld een knop Snelle weergave.
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd. Vervolgens activeert u de Quickview en de Ajax-URL die via webpagina is verzonden, om de gegevens of inhoud van de Snelle weergave te laden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 om het paneel van Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te selecteren.
Druk in een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en selecteer vervolgens het tabblad Netwerk.

* In Firefox kunt u de Firebug-plug-in activeren door op F12 te drukken en het tabblad Net te gebruiken. Of u kunt het ingebouwde gereedschap Inspecteur en het bijbehorende tabblad Netwerk gebruiken.
Druk in een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en selecteer vervolgens het tabblad Inspecteur.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van Quickview Ajax in het netwerklogboek en kopieer de geregistreerde URL voor toekomstige analyse. Gewoonlijk wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft een complex gedeelte of pad voor een querytekenreeks en het MIME-type voor reactie is `text/html` , `text/xml` of `text/javascript` .

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen kunnen bevatten die algemeen gelden voor een bepaalde categorie websites. Ze veranderen echter alleen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU ook verschillende elementen. Variabele elementen kunnen bijvoorbeeld categorie-id, kleurcode en code voor grootte zijn. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot-gegevens in de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

Bekijk de volgende voorbeelden van URL&#39;s van QuickView en de resulterende hotspot-variabelen:

<table>
  <tbody>
  <tr>
    <td><p>Enige SKU, die in het vraagkoord wordt gevonden.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
      <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige veranderlijke deel in URL is de waarde van de productId= parameter van het vraagkoord, en het is duidelijk een waarde SKU. De hotspots hebben daarom alleen SKU-velden nodig die zijn gevuld met waarden als <strong><code>866558</code></strong> , <strong><code>1196184</code></strong> , <strong><code>1081492</code></strong> en <strong><code>1898294</code></strong> .</p> </td>
  </tr>
  <tr>
    <td><p>Eén SKU, gevonden in het URL-pad.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong> .</p> </td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks.</p> </td>
    <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorieidentiteitskaart <code></code> wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de hotspot-definities paren. Dit is een SKU-waarde en een extra variabele met de naam <code>categoryId</code> . De resulterende paren zijn als volgt:</p>
    <ul>
      <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code> .</p> </li>
      <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong> .</p> </li>
      <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong> .</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Voorbeeld**

U kunt de zelfde benadering toepassen die in de drie bovenstaande voorbeelden op de [ demo Web-pagina ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html) wordt gebruikt.

De demo-webpagina heeft verschillende productminiaturen, elk met een Quickview-knop met het label &quot;Meer weergeven&quot;. Selecteer elke knop terwijl het foutopsporingsprogramma van uw webbrowser nog is geactiveerd en noteer de opgenomen URL&#39;s van de Snelle weergave. Nadat u alle vier de product Snelle meningen activeert beschikbaar op de pagina, hebt u de volgende lijst van de verzoeken van de Snelle mening die aan het achterste eind worden gemaakt:

* `/datafeed/Male-Windbreaker.json`
* `/datafeed/Male-SimpleHenley.json`
* `/datafeed/Male-CamoPullover.json`
* `/datafeed/Female-QuiltedDownJacket.json`

Wanneer u de serveraanroepen bekijkt, ziet u dat productspecifieke informatie alleen aanwezig is in het aanvraagpad. U merkt ook op dat het vraagkoord helemaal niet wordt gebruikt en er zijn twee verschillende types van betrokken gegevensstukken:

* Het eerste type is Mannelijk of Vrouwelijk. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productnaam, zoals CamoPullover, die waarschijnlijk SKU is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van een dergelijke analyse gebruikt u `categoryId` en `SKU` voor hotspots.

U kunt nu een afbeeldingsbanner uploaden en er hotspots aan toevoegen met de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

## (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken {#optional-creating-an-interactive-image-viewer-preset}

U kunt de standaardvoorinstelling voor een interactieve afbeeldingsviewer buiten de box met de naam `Shoppable_Banner` gebruiken die bij Experience Manager Assets wordt geleverd. U kunt ook uw eigen aangepaste viewer-voorinstelling maken voor gebruik met interactieve afbeeldingen.

Wanneer u een aangepaste voorinstelling voor een interactieve afbeeldingsviewer maakt, kunt u de weergave van hotspots in de afbeeldingsbanner bepalen. Als onderdeel van het maken van de viewervoorinstelling kunt u een hotspot-afbeelding uit een galerie met vooraf gedefinieerde afbeeldingen gebruiken.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt deze automatisch geactiveerd (ingeschakeld) op de pagina met de lijst met voorinstellingen voor viewers in Experience Manager Assets. Deze functionaliteit houdt in dat het zichtbaar is in de Interactieve component van Media en wanneer u activa bekijkt. Nochtans, om *te leveren* een interactieve banner met deze vooraf ingestelde kijker, *publiceert* ook uw vooraf ingestelde kijker. Deze regel geldt voor aangepaste of uit-van-box viewer-voorinstellingen.

**om een Interactieve de kijker van het Beeld tot stand te brengen vooraf ingesteld:**

1. Ga in de linkertrack naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Viewer Presets]** .
1. Selecteer **[!UICONTROL Create]** in de rechterbovenhoek van de pagina.
1. Typ in het dialoogvenster Nieuwe voorinstelling voor viewer een naam om de voorinstelling voor de interactieve bannerviewer te beschrijven.

   Deze titel wordt weergegeven op de pagina met de lijst met voorinstellingen voor viewers nadat u de titel hebt opgeslagen.

1. Selecteer in het vervolgkeuzemenu Uitgebreid mediatype de optie **[!UICONTROL Interactive Image]**.
1. Selecteer **[!UICONTROL Create]** .
1. Selecteer de tab **[!UICONTROL Appearance]** op de pagina Voorinstelling viewer bewerken.
1. Voer een van de volgende handelingen uit:

   * Als u uw eigen hotspot-afbeelding wilt uploaden die u voor afbeeldingen wilt gebruiken, selecteert u het pictogram Asset Picker. Navigeer op de pagina Inhoud selecteren naar de gewenste hotspot-afbeelding en selecteer deze. Selecteer het pictogram Vinkje in de rechterbovenhoek.
   * Als u een vooraf gedefinieerde hotspot-afbeelding wilt selecteren, selecteert u het pictogram Hotspot-galerie. Selecteer in het palet van de hotspot de hotspot die u wilt gebruiken.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

   Zorg ervoor dat u de nieuwe viewervoorinstelling publiceert.

   Zie [ de Kijker van Publish stelt ](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets) vooraf in.

   U kunt nu een afbeeldingsbanner uploaden.

## Een afbeeldingsbanner uploaden {#uploading-an-image-banner}

Als u reeds de beelden hebt geüpload die u wilt gebruiken, aan de volgende stap vooruitgaan, [ toevoegend hotspots aan een beeldbanner ](#adding-hotspots-to-an-image-banner).

**om een beeldbanner te uploaden:**

1. Upload afbeeldingsbanners die u interactief wilt maken.

   Zie [ Uploading activa ](/help/assets/manage-digital-assets.md#uploading-assets).

   U kunt nu hotspots toevoegen aan de afbeeldingsbanner. Zie de volgende taak hieronder.

## Hotspots toevoegen aan een afbeeldingsbanner {#adding-hotspots-to-an-image-banner}

U kunt hotspots toevoegen aan een afbeeldingsbanner met de editor op de pagina Hotspot-beheer.

Wanneer u hotspots toevoegt, kunt u deze definiëren als een pop-upweergave in QuickView, als een hyperlink of als een Experience-fragment.

Zie [ Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Gebruik of maak in plaats daarvan viewervoorinstellingen die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw interactieve afbeelding, kunt u Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit ziet voor klanten.

Zie [ (Optioneel) Een voorvertoning weergeven van interactieve afbeeldingen ](#optional-previewing-interactive-images) .

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een interactieve afbeelding of een carrouselbanner, worden de hotspotgegevens opgeslagen op dezelfde metagegevenslocatie. Deze locatie is relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
>
>Houd er echter rekening mee dat Carousel Banners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten. Interactieve afbeeldingen bieden dat niet. Houd hier rekening mee als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt in plaats daarvan interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.
>
>Zie ook [ Banners van de Carrousel ](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
>
>Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

**om hotspots aan een beeldbanner toe te voegen:**

1. Navigeer in de Assets-weergave naar de afbeeldingsbanner die u interactief wilt maken.
1. Voer een van de volgende handelingen uit:

   * Houd de muisaanwijzer boven de afbeelding en selecteer vervolgens **[!UICONTROL Select]** (vinkje). Selecteer **[!UICONTROL Edit]** op de werkbalk.

   * Houd de muisaanwijzer boven de afbeelding en selecteer vervolgens **[!UICONTROL More actions]** (pictogram met drie punten) **[!UICONTROL > Edit]** .

   * Selecteer de afbeelding om deze te openen op de pagina Detailweergave. Selecteer **[!UICONTROL Edit]** in de werkbalk.

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Add Hotspot]** (vingergeselecteerd pictogram) om de pagina Hotspot-beheer te openen.
1. Selecteer **[!UICONTROL Hotspot]** in de linkerbovenhoek van de pagina.

   1. Selecteer **[!UICONTROL Hotspot]** in de linkerbovenhoek van de pagina Hotspot Management.
   1. Selecteer in de afbeelding een locatie waar u de hotspot wilt weergeven. Sleep indien nodig de hotspot om de locatie aan te passen. Of gebruik de pijltoetsen op het toetsenbord om de positie van een geselecteerde hotspot te bepalen.
   1. Voeg desgewenst meer hotspots toe door de stappen a en b te herhalen.
   1. (Optioneel) Als u een hotspot wilt verwijderen, selecteert u deze in de afbeelding en selecteert u vervolgens **[!UICONTROL Delete]** (prullenbakpictogram) onder de kop **[!UICONTROL Hotspots]** .

1. Typ in het tekstveld Naam de naam van de hotspot. Deze naam wordt ook weergegeven in de vervolgkeuzelijst Geselecteerde hotspot.
1. Voer een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Quickview]** .

      * Als u een Experience Manager Sites- of eCommerce-klant bent, selecteert u het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Selecteer het product u wilt gebruiken, dan selecteren **** Uitgezocht in de hoger-juiste hoek van de pagina. U wordt teruggestuurd naar de pagina Hotspot-beheer.
      * Als u *niet* een klant van Experience Manager Sites of eCommerce bent

         * Zie [ identificerend hotspot variabelen ](#optional-identifying-hotspot-variables); u moet deze variabelen bepalen.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU van het product. De ingevoerde waarde van SKU bevolkt automatisch het veranderlijke gedeelte van het malplaatje van de Snelle mening. Het zorgt ervoor dat het systeem weet om geplakte hotspot met een bepaalde Snelle mening van SKU te associëren.
         * (Optioneel) Als er andere variabelen in de Snelle weergave zijn die worden gebruikt om een product verder te identificeren, selecteert u **[!UICONTROL Add Generic Variable]** . Geef in het tekstveld een extra variabele op. `category=Mens` is bijvoorbeeld een toegevoegde variabele.

   * Selecteer **[!UICONTROL Hyperlink]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het pictogram Site-kiezer (map). Navigeer naar een URL. De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Experience Fragment]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Selecteer het ervaringsfragment dat u wilt gebruiken. Selecteer vervolgens **[!UICONTROL Select]** rechtsboven op de pagina. U wordt teruggestuurd naar de pagina Hotspot-beheer.
Zie [ Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals u het wilt weergeven op de banner.

        >[!NOTE]
        >
        >De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Gebruik of maak in plaats daarvan viewervoorinstellingen die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

1. Selecteer **[!UICONTROL Save]** om uw werk op te slaan en terug te keren naar de pagina Bladeren.
1. Publish the interactive image. Publiceren zorgt voor de banner via de cloud en genereert ook insluitcode waarmee u kunt integreren met een website van derden.

   Zie [ de activa van Publish ](/help/assets/manage-digital-assets.md#publish-assets).

   Nadat u hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

   Zie [ een interactief beeld met uw website ](#integrating-an-interactive-image-with-your-website) integreren.

   >[!NOTE]
   >
   >Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

### (Optioneel) Interactieve afbeeldingen voorvertonen {#optional-previewing-interactive-images}

Met Voorvertoning kunt u zien hoe uw interactieve afbeelding er uitziet voor klanten. Met Voorvertoning kunt u ook de hotspots van de afbeelding testen om te controleren of deze zich naar behoren gedragen.

Als u tevreden bent met de interactieve afbeelding, kunt u deze publiceren.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) inbedden.
Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

**aan voorproef interactieve beelden:**

1. Navigeer in de Assets-weergave naar een bestaande interactieve afbeelding die u hebt gemaakt en selecteer deze om deze te openen in Voorvertoning.
1. Selecteer **[!UICONTROL Viewers]** in de vervolgkeuzelijst Inhoud in de linkerbovenhoek van de pagina Voorvertoning.
1. Selecteer **[!UICONTROL Shoppable_Banner]** in de lijst Viewers of de naam van de voorinstelling voor de interactieve afbeeldingsviewer die u hebt gemaakt.
1. Selecteer hotspots in de afbeelding om de bijbehorende acties van hotspots te testen.

## Interactieve Publish-afbeeldingselementen {#publishing-interactive-image-assets}

Zie [ Publish Assets ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor details op hoe te om interactieve beeldactiva te publiceren.

## Een interactieve afbeelding met uw website integreren {#integrating-an-interactive-image-with-your-website}

Nadat u een bannerafbeelding hebt geüpload, hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze toevoegen aan uw websitepagina.

Als u een Experience Manager Sites-klant bent, kunt u de interactieve afbeelding toevoegen door de component Interactieve media naar de pagina te slepen. Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

Als u een zelfstandige Experience Manager Assets-klant bent, kunt u de interactieve afbeelding handmatig aan uw website toevoegen, zoals in deze sectie wordt beschreven.

1. Kopieer de insluitcode van de gepubliceerde interactieve afbeelding.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) inbedden.

1. Voeg de gekopieerde insluitcode toe op de gewenste locatie op de webpagina.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch in het toegewezen gebied past.

**Voorbeeld**

Gebruikend de [ demowebsite als voorbeeld ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-0.html), merk op dat het beeld van de drie individuen een statische `IMG` markering is:

```xml {.line-numbers}
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Integratie is net zo eenvoudig als het verwijderen van de tag `IMG` en het vervangen door de gekopieerde insluitcode uit Experience Manager Assets. U kunt zien dat het resultaat [ het shoppable interactieve beeld op de pagina met drie cirkelhotspots ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-1.html) toont.

>[!NOTE]
>
>Zoals dit punt, zijn de hotspots op het shoppable interactieve beeld van de demo website slechts voor vertoningsdoeleinden. Ze zijn nog niet geïntegreerd met de bestaande Snelle weergaven.

Als u een &#39;uitsnijding&#39; wilt toepassen op een verwisselbare interactieve afbeelding voor een responsieve omgeving, neemt u het configuratiekenmerk Interactive Image `ZoomView.iscommand` op in het pad. In dit geval wordt de component `ZoomView` aangeroepen en is `iscommand` de opdracht &quot;uitsnijden&quot; voor het bedienen van afbeeldingen die u toepast.

Zie [ ZoomView.iscommand ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) configuratieattributen.

Zie [ gewas ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) beeld het dienen bevel.

U bent nu klaar om de interactieve afbeelding te integreren met een bestaande QuickView op uw website.

## Een interactieve afbeelding integreren met een bestaande QuickView {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
>
>Deze taak is alleen van toepassing als u een zelfstandige Experience Manager Assets-klant bent.

De laatste stap in dit proces is het integreren van de interactieve afbeelding met een bestaande Quickview-implementatie op uw website. Er is geen oplossing voor de integratie die in alle gevallen werkt. Elke implementatie van Quickview is uniek en een specifieke benadering is nodig. Daarom is het nuttig om de hulp van een front-end IT-persoon in te roepen.

De bestaande implementatie van QuickView vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Quickview URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achterste logica keert de overeenkomstige gegevens of inhoud van de Snelle mening terug naar de front-end code.
1. De front-end code laadt de gegevens of de inhoud van de Snelle mening.
1. Naar keuze, zet de front-end code de geladen gegevens van de Snelle mening in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm voor de gebruiker weer.

Deze vraag vertegenwoordigt niet noodzakelijk onafhankelijke openbare API vraag die door de Web-pagina logica van een willekeurige stap wordt geroepen. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer de verschuifbare interactieve afbeelding stap 1 en gedeeltelijk stap 2 vervangt, tikt een gebruiker op een hotspot in de verschuifbare afbeelding. Deze gebruikersinteractie wordt door de viewer afgehandeld. De viewer retourneert een gebeurtenis naar de webpagina die alle hotspotgegevens bevat die eerder aan Experience Manager Assets zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgegeven door de mogelijk onjuiste interactieve afbeelding.
* Hiermee maakt u een Quickview-URL op basis van de hotspot-gegevens.
* Triggert het proces om de Snelle mening van het achtereind te laden en het terug te geven op het scherm voor vertoning.

De insluitcode die door Experience Manager Assets wordt geretourneerd, heeft een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd, zoals in het volgende gemarkeerde codefragment wordt getoond:

```xml {.line-numbers}
        var s7interactiveimageviewer = new s7viewers.InteractiveImage({
            "containerId" : "s7interactiveimage_div",
            "params" : {
                "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
                "contenturl" : "https://aodmarketingna.assetsadobe.com/",
                "config" : "/etc/dam/presets/viewer/Shoppable_Media",
                "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
        })
        /* // Example of interactive image event for Quickview.
             s7interactiveimageviewer.setHandlers({
                "quickViewActivate": function(inData) {
                    var sku=inData.sku; //SKU for product ID
                    //To pass other parameter from the hotspot, add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //See your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot-variabelen die eerder zijn behandeld.

Zie [ hotspot variabelen ](#optional-identifying-hotspot-variables) identificeren.

Met behulp van de vorige URL-voorbeelden van Quickview kunt u in de volgende voorbeelden zien hoe de URL van de QuickView in elk geval wordt samengesteld:

<table>
 <tbody>
  <tr>
   <td><p>Enige SKU, die in het vraagkoord wordt gevonden</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/json?productId=" + inData.sku + "&amp;amp;source=100";
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>Enkele SKU, gevonden in het pad URL</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/product/" + inData.sku;
      },
      });</code></td>
  </tr>
  <tr>
   <td><p>SKU en categorie-id in de queryreeks</p> </td>
   <td><code class="code">s7interactiveimageviewer.setHandlers({
      "quickViewActivate": function(inData) {
      var quickViewUrl = "https://server/quickView/product/?category=" + inData.categoryId + "&amp;amp;prodId=" + inData.sku;
      },
      });</code></td>
  </tr>
 </tbody>
</table>

De laatste stap om de Quickview URL teweeg te brengen en het paneel van de Snelle mening te activeren vereist de hulp van een front-end persoon van IT van uw werk. Zij hebben de kennis om het best te weten hoe te om de implementatie van de Snelle mening van de juiste stap nauwkeurig teweeg te brengen, die een klaar-aan-gebruiksKickview URL hebben.

U kunt zien hoe deze stappen worden toegepast op de demo-website om een onoverzichtelijke interactieve afbeelding volledig te integreren met de Quickview-code. Eerder werd de structuur van de URL van de Snelle weergave als volgt geïdentificeerd:

```xml {.line-numbers}
/datafeed/$categoryId$-$SKU$.json
```

Als u deze URL wilt reconstrueren binnen de `quickViewActivate` -handler, kunt u de velden `categoryId` en `SKU` gebruiken. Deze velden zijn beschikbaar in het `inData` -object dat door de code van de viewer wordt doorgegeven aan de handler:

```xml {.line-numbers}
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige functieaanroep `loadQuickView()` . Deze functie heeft slechts één argument, namelijk de gegevens-URL van de Snelle weergave. De laatste stap voor het integreren van de verschuifbare interactieve afbeelding is dan ook het toevoegen van de volgende coderegel aan de `quickViewActivate` -handler:

```xml {.line-numbers}
loadQuickView(quickViewUrl);
```

Hier volgt de volledige broncode:

```xml {.line-numbers}
 var s7interactiveimageviewer = new s7viewers.InteractiveImage({
  "containerId" : "s7interactiveimage_div",
  "params" : {
   "serverurl" : "https://aodmarketingna.assetsadobe.com/is/image",
   "contenturl" : "https://aodmarketingna.assetsadobe.com/",
   "config" : "/etc/dam/presets/viewer/Shoppable_Media",
   "asset" : "/content/dam/mac/aodmarketingna/shoppable-banner/shoppable-banner.jpg" }
 })
   s7interactiveimageviewer.setHandlers({
   "quickViewActivate": function(inData) {
     var sku=inData.sku;
     var categoryId=inData.categoryId;
    var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
    loadQuickView(quickViewUrl);
    },
   });
 s7interactiveimageviewer.init();
```

De [ definitieve demowebsite met het volledig geïntegreerde interactieve beeld ](https://experienceleague.adobe.com/tools/dynamic-media-demo/shoppable-banner/we-fashion/landing-3.html).

## Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

Zie [ douane pop-up Windows® gebruikend QuickView ](/help/assets/dynamic-media/custom-pop-ups.md) creëren.
