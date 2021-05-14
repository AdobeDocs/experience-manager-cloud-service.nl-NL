---
title: Interactieve afbeeldingen
description: Leer hoe u met interactieve afbeeldingen werkt in Dynamic Media.
feature: Interactieve afbeeldingen
role: Business Practitioner
exl-id: 89eef5e6-d508-4f33-b54e-24d4df49f8c3
source-git-commit: d3ee23917eba4a2e4ae1f2bd44f5476d2ff7dce1
workflow-type: tm+mt
source-wordcount: '4228'
ht-degree: 1%

---

# Interactieve afbeeldingen{#interactive-images}

U kunt statische afbeeldingen eenvoudig verrijken en aantrekkelijke ervaringen voor klanten creëren door &#39;onoverzichtelijke&#39; hotspots naar een afbeelding te slepen. Slepbare hotspots combineren aanvullende informatie over een product of service met een directe, verkooppuntfunctie &#39;Toevoegen aan winkelwagentje&#39; of &#39;Kopen&#39;. Klanten kunnen op deze hotspots tikken die rechtstreeks zijn gekoppeld aan het product of de service, deze toevoegen aan een winkelwagentje of zijn gekoppeld aan een webpagina. Directe ervaringen zoals deze verhogen de betrokkenheid van klanten en conversies op uw website.

Hier volgt een verschuifbare banner met een pop-upvenster in de Snelle weergave. Een gebruiker activeert de Snelle weergave door op de cirkel of de hotspot op het model te tikken.

![chlimage_1-152](assets/chlimage_1-368.png)

Zie [Interactieve afbeeldingen in actie](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion-QVzoom/index2-shoppable.html) op de bovenstaande webpagina.

## Bekijk hoe u interactieve afbeeldingsbanners {#watch-how-interactive-image-banners-are-created} maakt

Bekijk een analyse op [hoe de interactieve beeldbanners worden gecreeerd](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (10 minuten en 33 seconden). U leert ook hoe u interactieve afbeeldingsbanners kunt voorvertonen, bewerken en leveren.

## Snel starten: Interactieve afbeeldingen {#quick-start-interactive-images}

De volgende stapsgewijze beschrijving van de workflow is ontworpen om u te helpen snel aan de slag te gaan met interactieve afbeeldingen in Adobe Experience Manager Assets.

Zoek naar **Voorbeeld** rubriek binnen enkele taken van het Snelle Begin. Het bevat een korte zelfstudie die is gebaseerd op een [webpaginavoorbeeld waaraan nog geen interactieve afbeeldingen zijn toegevoegd](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html).



De zelfstudie helpt u de stappen te illustreren voor het integreren van interactieve afbeeldingen op uw eigen website.

Stappen voor interactieve afbeeldingen:

1. **(Optioneel) Hotspotvariabelen** identificeren. Als u Adobe Experience Manager Assets en Dynamic Media standalone gebruikt, identificeert u dynamische variabelen die worden gebruikt in uw bestaande Quick view-implementatie. Zo weet u zeker dat u hotspotgegevens kunt invoeren wanneer u de interactieve afbeelding maakt. Zie [(Optioneel) Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables).
Nochtans, als u de Plaatsen van de Experience Manager, of Experience Manager eCommerce, of allebei gebruikt, dan is deze stap niet noodzakelijk.

1. **(Optioneel) Een voorinstelling** voor een interactieve afbeeldingsviewer maken. Pas de grafische afbeelding aan die wordt gebruikt om hotspots te vertegenwoordigen. Het is niet nodig een eigen voorinstelling voor de interactieve afbeeldingsviewer te maken als u de voorinstelling `Shoppable_Banner` in plaats daarvan wilt gebruiken die buiten de box is ingesteld met de naam Interactive Image Viewer.
Zie [(Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken](/help/assets/dynamic-media/managing-viewer-presets.md#creating-a-new-viewer-preset).

1. **Een afbeeldingsbanner** uploaden. Upload afbeeldingsbanners die u interactief wilt maken.
Zie [Een afbeeldingsbanner uploaden](#uploading-an-image-banner).

1. **Hotspots toevoegen aan een afbeeldingsbanner**. Voeg een of meer hotspots toe aan een afbeeldingsbanner. Koppel elke koppeling aan een handeling, zoals een hyperlink, een Snelle weergave of een ervaringsfragment. Nadat u hotspots hebt toegevoegd, kunt u deze taak voltooien door de interactieve afbeelding te publiceren.
Zie [Hotspots toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).
Zie [Interactieve afbeeldingen voorvertonen](#optional-previewing-interactive-images) - Optioneel. U kunt desgewenst een representatie van de verscherpte banner bekijken en de interactiviteit ervan testen.
Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van interactieve afbeeldingselementen.

1. **Een interactieve afbeelding in Experience Manager** toevoegen aan uw website of website. Als u Sites of eCommerce gebruikt, of beide, kunt u interactieve beelden direct aan een Web-pagina in Experience Manager toevoegen. Sleep de component Interactieve media naar de pagina. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).
Als u Experience ManagerAssets en Dynamic Media op zichzelf gebruikt, kopieert u de insluitcode naar uw website. Vervolgens integreert u deze met uw bestaande Snelle weergave. Zie [Een interactieve afbeelding integreren met uw website](#integrating-an-interactive-image-with-your-website).
Als u WCM (Web Content Manager) van derden gebruikt, integreert u de nieuwe interactieve video met de bestaande Snelle weergave die op uw website wordt gebruikt. Zie [Een interactieve afbeelding integreren met een bestaande Snelle weergave](#integrating-an-interactive-image-with-an-existing-quickview).

## (Optioneel) Hotspotvariabelen {#optional-identifying-hotspot-variables} identificeren

>[!NOTE]
>
>Deze taak is alleen vereist als aan de volgende voorwaarden wordt voldaan:
>
>* U wilt interactiviteit aan uw beeld toevoegen door aan Snelle meningen te teweegbrengen.
>* Uw implementatie van Experience Manager maakt *niet* gebruik van een eCommerce-integratieframework om productgegevens vanuit elke eCommerce-oplossing in de Experience Manager te krijgen. Dergelijke oplossingen zijn onder andere IBM® WebSphere® Commerce, Elastic Path, SAP Hybris of Intershop.

>
>
Als uw implementatie van Experience Manager eCommerce gebruikt, kunt u deze taak overslaan en aan de volgende taak te werk gaan.

Begin door dynamische variabelen te identificeren die door uw bestaande Quick view implementatie worden gebruikt zodat u hotspot gegevens kunt ingaan om het interactieve beeld tot stand te brengen.

Wanneer u hotspots toevoegt aan een bannerafbeelding in Experience Manager Assets, wijst u een SKU (Stock Keeping Unit) toe. SKU is een uniek herkenningsteken voor elk verschillend product of de dienst die u aanbiedt. Voeg desgewenst extra optionele variabelen toe aan elke hotspot. Dergelijke hotspotvariabelen worden later gebruikt om hotspots aan te passen aan de inhoud van de Snelle weergave.

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot gegevens te associëren. Elke hotspot die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie bevatten om het product ondubbelzinnig te identificeren in het bestaande back-endsysteem.

Er zijn verschillende manieren om een set variabelen te identificeren die voor hotspot-gegevens moet worden gebruikt.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van de Snelle weergave. Dergelijke mensen zullen waarschijnlijk weten wat de minimumreeks gegevens is die wordt vereist om Snelle mening in het systeem te identificeren. Het is echter ook mogelijk om eenvoudig het bestaande gedrag van de front-end code te analyseren.

Bij de meeste implementaties in de Snelle weergave wordt het volgende paradigma gebruikt:

* De gebruiker activeert een gebruikersinterface-element op de website. Als u bijvoorbeeld op een knop in de Snelle weergave klikt.
* De website verzendt een Ajax-aanvraag naar de achterkant om de gegevens of inhoud van de Snelle weergave te laden, indien nodig.
* De gegevens van de Snelle weergave worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie Snelle weergave is geïmplementeerd. Vervolgens activeert u de Snelle weergave en haalt u de URL van Ajax op die door de webpagina is verzonden om de gegevens of inhoud van de Snelle weergave te laden.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Om alle uitgaande HTTP- verzoeken in Google Chrome te zien, druk F12 om het paneel van Hulpmiddelen van de Ontwikkelaar te openen, en dan het lusje van het Netwerk te klikken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Netwerk.

* In Firefox kunt u de Firebug-plug-in activeren door op F12 te drukken en het tabblad Net te gebruiken. Of u kunt het ingebouwde gereedschap Inspecteur en het bijbehorende tabblad Netwerk gebruiken.
Druk op een Mac op Command+Option+I om het deelvenster Gereedschappen voor ontwikkelaars te openen en klik vervolgens op het tabblad Inspecteur.

Wanneer netwerkcontrole is ingeschakeld in de browser, activeert u de Snelle weergave op de pagina.

Zoek nu de URL van de Snelle weergave Ajax in het netwerklogboek en kopieer de opgenomen URL voor toekomstige analyse. Wanneer u de Snelle weergave activeert, zijn er gewoonlijk veel verzoeken die naar de server worden verzonden. De URL van de Snelle weergave Ajax is doorgaans een van de eerste in de lijst. Het heeft of een complex gedeelte van het vraagkoord of weg, en zijn reactieMIME type of `text/html`, `text/xml`, of `text/javascript` is.

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat URL&#39;s in de Snelle weergave onderdelen kunnen bevatten die veel worden gebruikt voor een bepaalde categorie websites. Ze veranderen echter alleen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval is het enige variabele deel in de URL van de Snelle weergave de product-SKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU ook verschillende elementen. Variabele elementen kunnen bijvoorbeeld categorie-id, kleurcode en code voor grootte zijn. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot-gegevens in de functie voor onoverzichtbare interactieve afbeeldingen in Experience Manager Assets.

Bekijk de volgende voorbeelden van URL&#39;s in de Snelle weergave en de resulterende hotspot-variabelen:

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
    </ul> <p>Het enige veranderlijke deel in URL is de waarde van de productId= parameter van het vraagkoord, en het is duidelijk een waarde SKU. Daarom hebben de hotspots alleen SKU-velden nodig die zijn gevuld met waarden zoals <strong><code>866558</code></strong>, <strong><code>1196184</code></strong>, <strong><code>1081492</code></strong>, <strong><code>1898294</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>Eén SKU, gevonden in het URL-pad.</p> </td>
    <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/product/6422350843</code></p> </li>
      <li><p><code>https://server/product/1607745002</code></p> </li>
      <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots: <strong><code>6422350843</code></strong>, <strong><code>1607745002</code></strong>, <strong><code>0086724882</code></strong>.</p> </td>
  </tr>
  <tr>
    <td><p>SKU en categorie-id in de queryreeks.</p> </td>
    <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
      <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. De SKU wordt opgeslagen in de <code>prodId</code> parameter en de categorie ID<code></code> wordt opgeslagen in de <code>category=</code> parameter.</p> <p>Daarom zijn de hotspot-definities paren. Dat wil zeggen, een SKU-waarde en een extra variabele met de naam <code>categoryId</code>. De resulterende paren zijn:</p>
    <ul>
      <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code>.</p> </li>
      <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong>.</p> </li>
      <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong>.</p> </li>
    </ul> <p> </p> </td>
  </tr>
  </tbody>
</table>

**Voorbeeld**

U kunt de zelfde benadering toepassen die in de drie voorbeelden hierboven op [demo Web page](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html) wordt gebruikt.

De demo-webpagina heeft verschillende productminiaturen, elk met een knop voor de Snelle weergave met het label Meer weergeven. Zorg dat het foutopsporingsprogramma van uw webbrowser is geactiveerd en klik op elke knop en noteer de opgenomen URL&#39;s van de Snelle weergave. Nadat u alle vier de product Snelle meningen activeert beschikbaar op de pagina, hebt u de volgende lijst van Snelle meningsverzoeken die aan het achterste eind worden gemaakt:

* `/datafeed/Men-Windbreaker.json`
* `/datafeed/Men-SimpleHenley.json`
* `/datafeed/Men-CamoPullover.json`
* `/datafeed/Women-QuiltedDownJacket.json`

Wanneer u de serveraanroepen bekijkt, ziet u dat productspecifieke informatie alleen aanwezig is in het aanvraagpad. U merkt ook op dat het vraagkoord helemaal niet wordt gebruikt en er zijn twee verschillende types van betrokken gegevensstukken:

* Het eerste type is Men of Vrouwen. Je kunt deze &#39;productcategorie&#39; noemen.
* Het tweede type is productnaam, zoals CamoPullover, die waarschijnlijk SKU is.

Op basis van deze informatie heeft de volledige URL van de Snelle weergave het volgende patroon:

`/datafeed/$categoryId$-$SKU$.json`

Op basis van een dergelijke analyse gebruikt u `categoryId` en `SKU` voor hotspots.

U kunt nu een afbeeldingsbanner uploaden en er hotspots aan toevoegen met de functie voor onoverzichtelijke interactieve afbeeldingen in Experience Manager Assets.

## (Optioneel) Een voorinstelling voor een interactieve afbeeldingsviewer maken {#optional-creating-an-interactive-image-viewer-preset}

U kunt ervoor kiezen om de standaardvoorinstelling `Shoppable_Banner` voor de Interactieve afbeeldingsviewer buiten de box te gebruiken die wordt geleverd bij Experience Manager Assets. U kunt ook uw eigen aangepaste viewer-voorinstelling maken voor gebruik met interactieve afbeeldingen.

Wanneer u een aangepaste voorinstelling voor een interactieve afbeeldingsviewer maakt, kunt u de weergave van hotspots in de afbeeldingsbanner bepalen. Als onderdeel van het maken van de viewervoorinstelling kunt u een hotspot-afbeelding uit een galerie met vooraf gedefinieerde afbeeldingen gebruiken.

Nadat u de viewervoorinstelling hebt opgeslagen, wordt deze automatisch geactiveerd (ingeschakeld) op de pagina met de lijst met voorinstellingen voor viewer in Experience Manager Assets. Deze functionaliteit houdt in dat het zichtbaar is in de Interactieve component van Media en wanneer u activa bekijkt. Als u echter *een interactieve banner met deze viewervoorinstelling wilt leveren,* ook de viewervoorinstelling publiceren *.* Deze regel geldt voor aangepaste of uit-van-box viewer-voorinstellingen.

**Een voorinstelling voor een interactieve afbeeldingsviewer maken**

1. Tik **[!UICONTROL Tools > Assets > Viewer Presets]** in de linkerrail.
1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Create]**.
1. Typ in het dialoogvenster Nieuwe voorinstelling voor viewer een naam om de voorinstelling voor de interactieve bannerviewer te beschrijven.

   Deze titel wordt weergegeven op de pagina met de lijst met voorinstellingen voor viewers nadat u de titel hebt opgeslagen.

1. Selecteer in het vervolgkeuzemenu Uitgebreid mediatype de optie **[!UICONTROL Interactive Image]**.
1. Tik op **[!UICONTROL Create]**.
1. Tik op het tabblad **[!UICONTROL Appearance]** op de pagina Voorinstelling viewer bewerken.
1. Voer een van de volgende handelingen uit:

   * Tik op het pictogram Asset Picker om uw eigen hotspot-afbeelding te uploaden die u voor afbeeldingen wilt gebruiken. Navigeer op de pagina Inhoud selecteren naar de gewenste hotspot-afbeelding en selecteer deze. Tik op het pictogram Vinkje in de rechterbovenhoek.
   * Tik op het pictogram Hotspot-galerie om een vooraf gedefinieerde hotspot-afbeelding te selecteren. Tik in het palet van de hotspot op de hotspot die u wilt gebruiken.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]**.

   Zorg ervoor dat u de nieuwe viewervoorinstelling publiceert.

   Zie [Voorinstellingen van viewer publiceren](/help/assets/dynamic-media/managing-viewer-presets.md#publishing-viewer-presets).

   U kunt nu een afbeeldingsbanner uploaden.

## Een afbeeldingsbanner {#uploading-an-image-banner} uploaden

Als u de afbeeldingen die u wilt gebruiken al hebt geüpload, gaat u naar de volgende stap [Hotspots toevoegen aan een afbeeldingsbanner](#adding-hotspots-to-an-image-banner).

**Een afbeeldingsbanner uploaden**

1. Upload afbeeldingsbanners die u interactief wilt maken.

   Zie [Elementen uploaden](/help/assets/manage-digital-assets.md#uploading-assets).

   U kunt nu hotspots toevoegen aan de afbeeldingsbanner. zie de volgende taak hieronder.

## Hotspots toevoegen aan een afbeeldingsbanner {#adding-hotspots-to-an-image-banner}

U kunt hotspots toevoegen aan een afbeeldingsbanner met de editor op de pagina Hotspot-beheer.

Wanneer u hotspots toevoegt, kunt u deze definiëren als een pop-upweergave in de Snelle weergave, als een hyperlink of als een Experience-fragment.

Zie [Fragmenten ervaren](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Gebruik of maak in plaats daarvan viewervoorinstellingen die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw interactieve afbeelding, kunt u Voorvertoning gebruiken om een voorstelling te zien van hoe uw interactieve afbeelding eruit ziet voor klanten.

Zie [(Optioneel) Interactieve afbeeldingen voorvertonen](#optional-previewing-interactive-images).

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeelding in een interactieve afbeelding of een carrouselbanner, worden de hotspotgegevens opgeslagen op dezelfde metagegevenslocatie. Deze locatie is relatief ten opzichte van de locatie van de afbeelding, ongeacht of het een interactieve afbeelding of een carrouselbanner betreft. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
Houd er echter rekening mee dat Carousel Banners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten. een interactieve afbeelding niet. Houd hier rekening mee als u een interactieve afbeelding of Carousel Banner wilt maken die dezelfde afbeelding gebruikt. U kunt in plaats daarvan interactieve afbeeldingen en carrouselbanners maken met afzonderlijke kopieën van dezelfde afbeelding.
Zie ook [Carrouselbanners](/help/assets/dynamic-media/carousel-banners.md).

>[!NOTE]
Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

**Hotspots toevoegen aan een afbeeldingsbanner**

1. Navigeer in de weergave Elementen naar de afbeeldingsbanner die u interactief wilt maken.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Select]** (vinkpictogram) op de afbeelding. Tik op **[!UICONTROL Edit]** op de werkbalk.

   * Tik op **[!UICONTROL More actions]** (drie punts pictogram) **[!UICONTROL > Edit]**.

   * Tik op de afbeelding om deze te openen op de pagina Detailweergave. Tik op **[!UICONTROL Edit]** op de werkbalk.

1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Add Hotspot]** (vingertikpictogram) om de pagina Hotspotbeheer te openen.
1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL Hotspot]**.

   1. Tik in de linkerbovenhoek van de pagina Hotspot Management op **[!UICONTROL Hotspot]**.
   1. Tik in de afbeelding op een locatie waar u de hotspot wilt weergeven. Sleep indien nodig de hotspot om de locatie ervan aan te passen. Of gebruik de pijltoetsen op het toetsenbord om de positie van een geselecteerde hotspot te bepalen.
   1. Voeg desgewenst meer hotspots toe door de stappen a en b te herhalen.
   1. (Optioneel) Als u een hotspot wilt verwijderen, selecteert u deze in de afbeelding en tikt u op **[!UICONTROL Delete]** (prullenbakpictogram) onder de kop **[!UICONTROL Hotspots]**.

1. Typ in het tekstveld Naam de naam van de hotspot. Deze naam wordt ook weergegeven in de vervolgkeuzelijst Geselecteerde hotspot.
1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Quick view]**.

      * Tik of klik op het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen als u een Experience Manager- of eCommerce-klant bent. Tik op het product dat u wilt gebruiken en tik vervolgens op **Select** in de rechterbovenhoek van de pagina. U wordt teruggestuurd naar de pagina Hotspot-beheer.
      * Als u *not* een klant van de Experience Manager of van de eCommerce bent

         * Zie [Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables); U moet deze variabelen definiëren.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU van het product. De ingevoerde waarde SKU vult automatisch het variabele gedeelte van het malplaatje van de Snelle mening. Het zorgt ervoor dat het systeem weet om geëtst hotspot met de Snelle mening van SKU te associëren.
         * (Optioneel) Tik op **[!UICONTROL Add Generic Variable]** als er andere variabelen in de Snelle weergave zijn die worden gebruikt om een product verder te identificeren. Geef in het tekstveld een extra variabele op. `category=Mens` is bijvoorbeeld een toegevoegde variabele.
   * Tik op **[!UICONTROL Hyperlink]**.

      * Tik op het pictogram Siteselector (map) als u een klant bent van de Experience Manager Sites. Navigeer naar een URL. De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
      * Als u een zelfstandige klant bent, geeft u in het tekstveld HREF het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [Werken met kiezers](/help/assets/dynamic-media/working-with-selectors.md) voor meer informatie.

   * Tik op **[!UICONTROL Experience Fragment]**.

      * Als u een klant van de Plaatsen van de Experience Manager bent, tik of klik het pictogram van het Onderzoek (vergrootglas) om de pagina van het Fragment van de Ervaring te openen. Tik op het ervaringsfragment dat u wilt gebruiken. Tik vervolgens op **[!UICONTROL Select]** in de rechterbovenhoek van de pagina. U wordt teruggestuurd naar de pagina Hotspot-beheer.
Zie [Fragmenten ervaren](/help/sites-cloud/authoring/fundamentals/experience-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals u het wilt weergeven op de banner.

         >[!NOTE]
         De gereedschappen voor het delen van sociale media in interactieve afbeeldingen worden niet ondersteund wanneer u de viewer insluit in een ervaringsfragment. Gebruik of maak in plaats daarvan viewervoorinstellingen die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.



1. Tik **[!UICONTROL Save]** om uw werk op te slaan en terug te keren naar de pagina Bladeren.
1. Publiceer de interactieve afbeelding. Publiceren zorgt voor de banner via de cloud en genereert ook insluitcode waarmee u kunt integreren met een website van derden.

   Zie [Elementen publiceren](/help/assets/manage-digital-assets.md#publish-assets).

   Nadat u hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze nu toevoegen aan uw bestaande website.

   Zie [Een interactieve afbeelding integreren met uw website](#integrating-an-interactive-image-with-your-website).

   >[!NOTE]
   Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

### (Optioneel) Interactieve afbeeldingen voorvertonen {#optional-previewing-interactive-images}

Met Voorvertoning kunt u zien hoe uw interactieve afbeelding er uitziet voor klanten. Met Voorvertoning kunt u ook de hotspots van de afbeelding testen om te controleren of deze zich naar behoren gedragen.

Als u tevreden bent met de interactieve afbeelding, kunt u deze publiceren.
Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).
Zie [URL&#39;s koppelen aan uw webtoepassing](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met de pagina&#39;s van de Plaatsen van de Experience Manager heeft.
Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

**Interactieve afbeeldingen voorvertonen**

1. Navigeer in de weergave Middelen naar een bestaande, door u gemaakte interactieve afbeelding en tik erop om deze te openen in Voorvertoning.
1. Tik in de vervolgkeuzelijst Inhoud in de linkerbovenhoek van de voorvertoningspagina op **[!UICONTROL Viewers]**.
1. Tik in de lijst Viewers op **[!UICONTROL Shoppable_Banner]** of de naam van de voorinstelling voor de interactieve afbeeldingsviewer die u hebt gemaakt.
1. Tik op hotspots in de afbeelding om de bijbehorende acties van hotspots te testen.

## Interactieve afbeeldingselementen publiceren {#publishing-interactive-image-assets}

Zie [Elementen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor meer informatie over het publiceren van interactieve afbeeldingselementen.

## Een interactieve afbeelding integreren met uw website {#integrating-an-interactive-image-with-your-website}

Nadat u een bannerafbeelding hebt geüpload, hotspots hebt toegevoegd en de interactieve afbeelding hebt gepubliceerd, kunt u deze toevoegen aan uw websitepagina.

Als u een klant van de Plaatsen van de Experience Manager bent, kunt u het interactieve beeld toevoegen door de Interactieve component van Media op uw pagina te slepen. Zie [Dynamic Media-elementen toevoegen aan pagina&#39;s](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md).

Als u een zelfstandige klant van de Middelen van de Experience Manager bent, kunt u het interactieve beeld aan uw website manueel toevoegen zoals die in deze sectie wordt beschreven.

1. Kopieer de insluitcode van de gepubliceerde interactieve afbeelding.
Zie [Video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/dynamic-media/embed-code.md).

1. Voeg de gekopieerde insluitcode toe op de gewenste locatie op de webpagina.
De gekopieerde insluitcode wordt ingesteld voor een responsieve omgeving, zodat deze automatisch in het toegewezen gebied past.

**Voorbeeld**

Als u de [demo-website als voorbeeld](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-0.html) gebruikt, ziet u dat het beeld van de drie personen een statische `IMG`-tag is:

```xml
<img class="img-responsive" width="100%" title="Hero Image 2" alt="Hero Image 2" src="images/shoppable-banner.jpg">
```

Integratie is zo eenvoudig als het verwijderen van de tag `IMG` en het vervangen door de gekopieerde insluitcode uit Experience Manager Assets. U kunt zien dat het resultaat [de schokbare interactieve afbeelding op de pagina weergeeft met drie cirkelvormige hotspots](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-1.html).

>[!NOTE]
Zoals dit punt, zijn de hotspots op het shoppable interactieve beeld van de demo website slechts voor vertoningsdoeleinden. Ze zijn nog niet geïntegreerd met de bestaande Snelle weergaven.

Als u een &#39;uitsnijding&#39; wilt toepassen op een verwisselbare interactieve afbeelding voor een responsieve omgeving, neemt u het configuratiekenmerk Interactive Image `ZoomView.iscommand` op in het pad. In dit geval wordt de `ZoomView`-component aangeroepen en `iscommand` is de opdracht voor het leveren van de &quot;uitsnijdafbeelding&quot; die u toepast.

Zie [ZoomView.iscommand](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/command-reference-configuration-attributes-interactive-images/r-html5-aem-interactive-image-config-attrib-zoomview-iscommand.html) configuratiekenmerk.

Zie [opdracht Uitsnijden](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-crop.html) afbeelding weergeven.

U kunt de interactieve afbeelding nu integreren met een bestaande Snelle weergave op uw website.

## Een interactieve afbeelding integreren met een bestaande Snelle weergave {#integrating-an-interactive-image-with-an-existing-quickview}

>[!NOTE]
Deze taak is slechts van toepassing als u een stand-alone klant van de Activa van de Experience Manager bent.

De laatste stap in dit proces is het integreren van de interactieve afbeelding met een bestaande Quick view-implementatie op uw website. Er is geen oplossing voor de integratie die in alle gevallen werkt. Elke Quick view-implementatie is uniek en er is een specifieke aanpak nodig. Daarom is het nuttig om de hulp van een front-end IT-persoon in te roepen.

De bestaande implementatie van de Snelle weergave vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Snelle mening URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achtergrondlogica retourneert de corresponderende gegevens of inhoud van de Snelle weergave terug naar de front-end code.
1. De front-end code laadt de Snelle meningsgegevens of inhoud.
1. Naar keuze, zet de voorste-eindcode de geladen Snelle meningsgegevens in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm weer voor de eindgebruiker.

Deze vraag vertegenwoordigt niet noodzakelijk onafhankelijke openbare API vraag die door de Web-pagina logica van een willekeurige stap wordt geroepen. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer de verschuifbare interactieve afbeelding stap 1 en gedeeltelijk stap 2 vervangt, tikt een gebruiker op een hotspot in de verschuifbare afbeelding. Deze gebruikersinteractie wordt door de viewer afgehandeld. De viewer retourneert een gebeurtenis naar de webpagina die alle hotspotgegevens bevat die eerder aan Experience Manager Assets zijn toegevoegd.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die wordt uitgegeven door de mogelijk onjuiste interactieve afbeelding.
* Hiermee maakt u een URL van de Snelle weergave op basis van de hotspot-gegevens.
* Triggert het proces waarbij de Snelle weergave vanaf de achtergrond wordt geladen en op het scherm wordt weergegeven.

De insluitcode die door Experience Manager Assets wordt geretourneerd, heeft een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd, zoals in het volgende gemarkeerde codefragment wordt getoond:

```xml
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
                    //To pass other parameter from the hotspot, you will need to add custom parameter during the hotspot setup as parameterName=value
                    loadQuickView(sku); //Replace this call with your Quickview plugin
                    //Please refer to your Quickviewer plugin for the Quickview call
                 },
             });
        */
        s7interactiveimageviewer.init();
```

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot-variabelen die eerder zijn behandeld.

Zie [Hotspot-variabelen identificeren](#optional-identifying-hotspot-variables).

Aan de hand van de vorige URL-voorbeelden van de Snelle weergave kunt u in de volgende voorbeelden zien hoe de URL van de Snelle weergave in elk geval wordt samengesteld:

<table>
 <tbody>
  <tr>
   <td><p>Single SKU, gevonden in het vraagkoord</p> </td>
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

De laatste stap om de URL van de Snelle weergave te activeren en het deelvenster Snelle weergave te activeren, vereist de hulp van een front-end IT-persoon van uw werk. Ze hebben de kennis om te weten hoe u de implementatie van de Snelle weergave nauwkeurig vanuit de juiste stap kunt activeren en beschikken over een gebruiksklare URL voor de Snelle weergave.

U kunt zien hoe deze stappen worden toegepast op de demo-website om een onduidelijk interactieve afbeelding volledig te integreren met de code van de Snelle weergave. Eerder werd de structuur van de URL van de Snelle weergave als volgt geïdentificeerd:

```xml
/datafeed/$categoryId$-$SKU$.json
```

Als u deze URL wilt reconstrueren binnen de handler `quickViewActivate`, kunt u de velden `categoryId` en `SKU` gebruiken. Deze velden zijn beschikbaar in het `inData`-object dat door de code van de viewer aan de handler wordt doorgegeven:

```xml
var sku=inData.sku;
var categoryId=inData.categoryId;
var quickViewUrl = "datafeed/" + categoryId + "-" + sku + ".json";
```

De demowebsite activeert het dialoogvenster Snelle weergave met een eenvoudige functieaanroep `loadQuickView()`. Deze functie heeft slechts één argument, namelijk de URL van de gegevens in de Snelle weergave. Als dusdanig, is de laatste stap om het shoppable interactieve beeld te integreren de volgende lijn van code aan `quickViewActivate` manager toe te voegen:

```xml
loadQuickView(quickViewUrl);
```

Hier volgt de volledige broncode:

```xml
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

De [definitieve demowebsite met de volledig geïntegreerde interactieve afbeelding](https://marketing.adobe.com/resources/help/en_US/dm/shoppable-banner/we-fashion/landing-3.html).

## Snelle weergaven gebruiken om aangepaste pop-ups {#using-quickviews-to-create-custom-pop-ups} te maken

Zie [Snelle weergaven gebruiken om aangepaste pop-upvensters® te maken](/help/assets/dynamic-media/custom-pop-ups.md).
