---
title: Carousel Banners
description: Leer hoe u met Carousel Banners in Dynamic Media werkt.
contentOwner: Rick Brough
feature: Carousel Banners
role: User
exl-id: 34541302-6610-4f5e-af93-c95328dda910
source-git-commit: 89f23a590338561b4cfeb10b54a260a135ec2f08
workflow-type: tm+mt
source-wordcount: '4406'
ht-degree: 1%

---

# Carousel Banners{#carousel-banners}

Met carrouselbanners kunnen marketers de conversie stimuleren door eenvoudig interactieve, draaiende promotionele inhoud te maken en deze op elk scherm te leveren.

Het maken en wijzigen van inhoud in promotiebanners kan tijdrovend zijn, waardoor u minder snel nieuwe inhoud kunt publiceren of deze doelgerichter kunt maken. Met carrouselbanners kunt u snel roterende banners maken of wijzigen en interactiviteit toevoegen, zoals hotspots die zijn gekoppeld aan productdetails of verwante bronnen. U kunt ze op elk scherm aanbieden, zodat u nieuwe promotionele inhoud sneller op de markt kunt brengen.

Carousel Banners worden aangeduid door een banner met het woord **[!UICONTROL CAROUSELSET]** :

![ chlimage_1-438 ](assets/chlimage_1-438.png)

Op uw website kan een carrouselbanner er als volgt uitzien:

![ chlimage_1-439 ](assets/chlimage_1-439.png)

Hier kunt u door de afbeeldingen navigeren door de getallen te selecteren. Bovendien worden de dia&#39;s automatisch geroteerd op basis van een tijdsinterval dat u kunt aanpassen. Afbeeldingen in een carrouselbanner ondersteunen zowel hotspots als afbeeldingen met hyperlinks. Gebruikers kunnen een hyperlink selecteren of naar een hyperlink gaan of een Quickview-venster openen.

In dit voorbeeld heeft een gebruiker een afbeelding met hyperlinks geselecteerd en het Quickview-venster geopend voor handschoenen:

![ chlimage_1-440 ](assets/chlimage_1-440.png)

## Kijk hoe carrouselbanners zijn gemaakt {#watch-how-carousel-banners-are-created}

Bekijk een analyse op [ hoe de carrouselbanners ](https://s7d5.scene7.com/s7viewers/html5/VideoViewer.html?videoserverurl=https://s7d5.scene7.com/is/content/&amp;emailurl=https://s7d5.scene7.com/s7/emailFriend&amp;serverUrl=https://s7d5.scene7.com/is/image/&amp;config=Scene7SharedAssets/Universal_HTML5_Video_social&amp;contenturl=https://s7d5.scene7.com/skins/&amp;asset=S7tutorials/InteractiveCarouselBanner) (Duur: 10 minuten en 33 seconden) worden gecreeerd. U leert ook hoe u carrouselbanners kunt voorvertonen, bewerken en leveren.

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL dam-users]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen hebt creërend of uitgeeft, zie uw systeembeheerder die u aan de **d[!UICONTROL am-users]** groep kan toevoegen.

## Snel starten: Carousel-banners {#quick-start-carousel-banners}

Zo kunt u snel aan de slag:

1. [ identificeer hotspot en beeld kaartvariabelen ](#identifying-hotspot-and-image-map-variables) (slechts voor klanten die Adobe Experience Manager Assets + Dynamic Media gebruiken)

   Begin door dynamische variabelen te identificeren die door de bestaande Snelle meningsimplementatie worden gebruikt. Zo kunt u tijdens het maken van carrouselbanners in Experience Manager Assets naar behoren hotspots en afbeeldingskaartgegevens invoeren.

<!-- LEAVE; COMMERCE BEING ADDED AGAIN IN THE FUTURE

   >[!NOTE]
   >
   >If you are an Experience Manager Sites or Ecommerce customer, you can use the built-in feature to navigate to product pages and lookup the existing skus in the product catalog. You do not need to manually enter hotspot or image map variables.
   >
   >
   >If you are an Experience ManagerAssets and Dynamic Media customer, you will manually enter data for hotspots and image maps, and then integrate the published URL or Embed code with your third-party content management system.

-->

1. Optioneel: [Maak zo nodig een viewervoorinstelling voor een carrouselset](/help/assets/dynamic-media/managing-viewer-presets.md).

   Als beheerder kunt u het gedrag en de weergave van de carrousel aanpassen door uw eigen voorinstelling voor de Carousel-viewer te maken. Het belangrijkste voordeel is dat u deze aangepaste viewer-voorinstelling kunt hergebruiken voor meerdere carrousels. Gebruikers kunnen het gedrag en de weergave van de carrousel echter desgewenst rechtstreeks aanpassen tijdens het ontwerpen van de carrousel. Deze benadering heeft de voorkeur wanneer u een specifiek ontwerp voor een bepaalde carrousel wilt.

1. [ upload een beeldbanner ](#uploading-image-banners).

   Upload afbeeldingsbanners die u interactief wilt maken.

1. [ creeer een Reeks Carousel ](#creating-carousel-sets).

   In de Reeksen van Carrousels, navigeren de gebruikers door bannerbeelden en selecteren hotspots of beeldkaarten om tot relevante inhoud toegang te hebben.

   Als u een Carousel-set wilt maken in Assets, selecteert u **[!UICONTROL Create]** en vervolgens **[!UICONTROL Carousel Sets]** . Voeg elementen aan dia&#39;s toe en selecteer **[!UICONTROL Save]**. U kunt de weergave en het gedrag van de carrousel ook rechtstreeks in de editor bewerken.

1. [ voeg hotspots of beeldkaarten aan een beeldbanner ](#adding-hotspots-or-image-maps-to-an-image-banner) toe.

   Voeg een of meer hotspots of afbeeldingen met hyperlinks toe aan een afbeeldingsbanner. Koppel vervolgens elk element aan een handeling zoals een koppeling, een Snelle weergave of een ervaringsfragment. Nadat u hotspots of afbeeldingen met hyperlinks hebt toegevoegd, kunt u deze taak voltooien door de carrouselset te publiceren. Met Publiceren maakt u de insluitcode die u kunt gebruiken om de bestemmingspagina van uw website te kopiëren en toe te passen.

   Zie [ (Optioneel) Voorvertoning carrouselbanners weergeven ](#optional-previewing-carousel-banners) - Optioneel. U kunt desgewenst een voorstelling van de carrouselset weergeven en de interactiviteit ervan testen.

1. [ de Banners van de Carrousel van Publish ](#publishing-carousel-banners).

   U publiceert een Carousel-set op dezelfde manier als elk ander element. Navigeer in Assets naar de Carousel-set, selecteer deze en selecteer **[!UICONTROL Publish]** . Als u een Carousel-set publiceert, worden de URL en de insluittekenreeks geactiveerd.

1. Voer een van de volgende handelingen uit:

   * [ voeg een carrouselbanner aan uw website toe ](#adding-a-carousel-banner-to-your-website-page) u kunt carrouselbanner URL toevoegen of code inbedden u op de website pagina hebt gekopieerd.

      * [ integreer de carrouselbanner met een bestaande Snelle mening ](#integrating-the-carousel-banner-with-an-existing-quickview). Als u een systeem voor webcontentbeheer van derden gebruikt, moet u de nieuwe carrouselbanner integreren met de bestaande Quick view-implementatie op uw website.

   * [ voeg een carrouselbanner aan uw website in Experience Manager ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toe. Als u een Experience Manager Sites-klant bent, kunt u de carrousel die rechtstreeks op de pagina is ingesteld, toevoegen met de component Interactive Media.

Als u de Reeksen van Carrousel moet uitgeven, zie [ Carrouselreeksen ](#editing-carousel-sets) uitgeven. Bovendien kunt u [ Carousel - vastgestelde eigenschappen ](/help/assets/manage-digital-assets.md#editing-properties) bekijken en uitgeven.

## Hotspot- en afbeeldingskaartvariabelen identificeren {#identifying-hotspot-and-image-map-variables}

Begin door dynamische variabelen te identificeren die door de bestaande Snelle meningsimplementatie worden gebruikt. Met deze methode kunt u tijdens het maken van carrousel-sets in Experience Manager Assets de hotspots of afbeeldingskaartgegevens correct invoeren.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt aan een bannerafbeelding, wijst u een SKU (Stock Keeping Unit) toe. U kunt ook optionele extra variabelen toewijzen aan elke hotspot of afbeelding met hyperlinks. Dergelijke variabelen worden later gebruikt om hotspots of afbeeldingen met hyperlinks aan te passen aan de inhoud van de Snelle weergave.

<!-- LEAVE; COMMERCE BEING ADDED LATER

>[!NOTE]
>
>If you are an Experience Manager Sites and/or Experience Manager Ecommerce customer, skip this step. You do not need to manually identify hotspot or image map variables; you can use the integration with Ecommerce for product integration. See information on [setting up eCommerce](/help/sites-cloud/administering/generic.md). In addition, you can use the Interactive component and add it to your web page.
>
>If you are an Experience Manager Assets or Media customer, you publish the URL or Embed code and then integrate with your third-party content management system and identify hotspots and image maps manually.

-->

Het is belangrijk om het aantal en het type variabelen correct te identificeren om met hotspot of beeldkaartgegevens te associëren. Op elke hotspot of afbeeldingskaart die aan een bannerafbeelding wordt toegevoegd, moet voldoende informatie staan om het product ondubbelzinnig te identificeren in het bestaande back-end systeem. Zorg er tegelijkertijd voor dat elke hotspot of afbeelding met hyperlinks niet meer gegevens bevat dan nodig is. De reden hiervoor is dat het gegevensinvoerproces hierdoor te complex en voortdurend hotspot- of imagekaartbeheer wordt.

Er zijn verschillende manieren om een set variabelen te identificeren die moet worden gebruikt voor hotspot- of afbeeldingskaartgegevens.

Soms is het voldoende om IT-specialisten te raadplegen die verantwoordelijk zijn voor de bestaande implementatie van QuickView. Zij zullen waarschijnlijk weten wat de minimumreeks gegevens is om Snelle mening in het systeem te identificeren. Het is echter mogelijk om gewoon het bestaande gedrag van de front-end code te analyseren.

De meeste implementaties van de Snelle mening gebruiken het volgende paradigma:

* De gebruiker activeert een gebruikersinterface-element op de website. Selecteer bijvoorbeeld een knop **[!UICONTROL Quickview]** .
* De website verzendt een Ajax-aanvraag naar de achterkant om de Quickview-gegevens of -inhoud te laden, indien nodig.
* De Quickview-gegevens worden omgezet in de inhoud ter voorbereiding op de weergave op de webpagina.
* Tot slot geeft de front-end code dergelijke inhoud visueel op het scherm terug.

Vervolgens kunt u verschillende delen van de bestaande website bezoeken waar de functie QuickView is geïmplementeerd. Vervolgens activeert u de Quickview en de Ajax-URL die door de webpagina is verzonden voor het laden van de gegevens of inhoud van de Snelle weergave.

Normaal is er geen behoefte aan u om het even welke gespecialiseerde het zuiveren hulpmiddelen te gebruiken. Moderne webbrowsers beschikken over webinspecteurs die hun werk naar behoren doen. Hieronder volgen enkele voorbeelden van webbrowsers met webcontroles:

* Als u alle uitgaande HTTP-aanvragen in Google Chrome wilt bekijken, drukt u op F12 (Windows®) of Command-Option-I (Mac) om het deelvenster Developer te openen. Selecteer het tabblad Netwerk.
* In Firefox kunt u de Firebug-plug-in activeren door op F12 (Windows®) of Command-Option-I (Mac) te drukken. Gebruik zijn lusje van het Netwerk, of gebruik het ingebouwde hulpmiddel van de Inspecteur en zijn Netwerk tabel.

Wanneer netwerkcontrole in browser wordt aangezet, teweeg de Snelle mening op de pagina.

Zoek nu de URL van de Snelle weergave Ajax in het netwerklogboek en kopieer de opgenomen URL voor toekomstige analyse. Gewoonlijk wanneer u de Quickview teweegbrengt zijn er talrijke verzoeken die naar de server worden verzonden. De URL van Quickview Ajax is doorgaans een van de eerste in de lijst. Het heeft een complex gedeelte of pad voor een querytekenreeks en het MIME-type voor reactie is `text/html` , `text/xml` of `text/javascript` .

Tijdens dit proces is het belangrijk om verschillende delen van uw website te bezoeken, met verschillende productcategorieën en typen. De reden hiervoor is dat in de Snelle weergave-URL&#39;s onderdelen voorkomen die veel voorkomen in een bepaalde categorie websites, maar deze URL alleen wijzigen als u een ander gedeelte van de website bezoekt.

In het eenvoudigste geval, is het enige veranderlijke deel in Quickview URL productSKU. In dit geval is de SKU-waarde het enige gegevensstuk dat u nodig hebt om hotspots of afbeeldingen met hyperlinks toe te voegen aan de bannerafbeelding.

In complexe gevallen heeft de URL van de Snelle weergave echter naast de SKU ook verschillende elementen. Enkele van deze elementen zijn onder andere categorie-id, kleurcode, code voor de grootte, enzovoort. In dergelijke gevallen is elk element een afzonderlijke variabele in de definitie van hotspot- of afbeeldingskaart in de bannerfunctie carrousel.

Bekijk de volgende voorbeelden van URL&#39;s in QuickView en de resulterende hotspot- of afbeeldingskaartvariabelen:

<table>
 <tbody>
  <tr>
   <td>Enige SKU, die in het vraagkoord wordt gevonden.</td>
   <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/json?productId=866558&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1196184&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1081492&amp;source=100</code></p> </li>
     <li><p><code>https://server/json?productId=1898294&amp;source=100</code></p> </li>
    </ul> <p>Het enige variabele deel in de URL is de waarde van de parameter van de <code>productId=</code> querytekenreeks en het is duidelijk een SKU-waarde. Voor hotspots of afbeeldingen met hyperlinks zijn daarom alleen SKU-velden nodig die zijn gevuld met waarden zoals <code>866558,</code> <code>1196184,</code> <code>1081492,</code> <code>1898294.</code></p> </td>
  </tr>
  <tr>
   <td>Eén SKU, gevonden in het URL-pad.</td>
   <td><p>De opgenomen URL's van de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/product/6422350843</code></p> </li>
     <li><p><code>https://server/product/1607745002</code></p> </li>
     <li><p><code>https://server/product/0086724882</code></p> </li>
    </ul> <p>Het variabele gedeelte bevindt zich in het laatste gedeelte van het pad en wordt de SKU-waarde van de hotspots/afbeeldingen met hyperlinks:<strong><code>6422350843</code>, <code>1607745002,</code> </strong><code>0086724882.</code></p> </td>
  </tr>
  <tr>
   <td>SKU en categorie-id in de queryreeks.</td>
   <td><p>De opgenomen URL's in de Snelle weergave bevatten het volgende:</p>
    <ul>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=305466</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1100004&amp;prodId=310181</code></p> </li>
     <li><p><code>https://server/quickView/product/?category=1740148&amp;prodId=308706</code></p> </li>
    </ul> <p>In dit geval bevat de URL twee verschillende onderdelen. SKU wordt opgeslagen in de <code>prodId</code> parameter en categorie identiteitskaart wordt opgeslagen in de <code>category=</code> parameter.</p> <p>De definities van hotspot/afbeelding met hyperlinks zijn dus paren. Dit is een SKU-waarde en een extra variabele met de naam <code>categoryId</code> . De resulterende paren zijn als volgt:</p>
    <ul>
     <li><p>SKU is <strong><code>305466</code></strong> en <code>categoryId</code> is <code>1100004</code> .</p> </li>
     <li><p>SKU is <strong><code>310181</code></strong> en <code>categoryId</code> is <strong><code>1100004</code></strong> .</p> </li>
     <li><p>SKU is <strong><code>308706</code></strong> en <code>categoryId</code> is <strong><code>1740148</code></strong> .</p> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

## Afbeeldingsbanners uploaden {#uploading-image-banners}

Als u reeds de beelden hebt geupload die u wilt gebruiken, aan de volgende stap vooruitgaan, [ creeer de Reeksen van Carousel ](#creating-carousel-sets). De afbeeldingen die in de carrousel worden gebruikt, moeten worden geüpload nadat Dynamic Media is ingeschakeld.

Om beeldbanners te uploaden, zie [ activa ](/help/assets/manage-digital-assets.md) uploaden.

## Carrouselsets maken {#creating-carousel-sets}

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL dam-users]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de groep **[!UICONTROL dam-users]** kan toevoegen.

**om de Reeksen van Carousel tot stand te brengen:**

1. Navigeer in Assets naar de map waarin u de Carousel-set wilt maken en ga naar **[!UICONTROL Create > Carousel Set]** .
1. Selecteer op de pagina Carousel Banner Editor de optie **[!UICONTROL Tap to open Asset Selector]** om de afbeelding voor de eerste dia te selecteren.

   Voer een van de volgende handelingen uit op de pagina Carousel Banner Editor:

   * Selecteer **[!UICONTROL Add Slide]** pictogram in de linkerbovenhoek van de pagina.

   * Selecteer **[!UICONTROL Tap to open Asset Selector]** in het midden van de pagina.

   Selecteer deze optie om de elementen te selecteren die u in de Carousel-set wilt opnemen. Geselecteerde elementen hebben een vinkje. Wanneer u klaar bent, selecteert u **[!UICONTROL Select]** in de rechterbovenhoek van de pagina.

   Met de Asset Selector kunt u naar elementen zoeken door een trefwoord in te voeren en **[!UICONTROL Return]** te selecteren. U kunt ook filters toepassen om de zoekresultaten te verfijnen. U kunt filteren op pad, verzameling, bestandstype en tag. Selecteer het filter en selecteer vervolgens het pictogram **[!UICONTROL Filter]** op de werkbalk. Wijzig de weergave door het pictogram Weergave te selecteren en **[!UICONTROL Column View]** , **[!UICONTROL Card View]** of **[!UICONTROL List View]** te selecteren.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md) voor meer informatie.

1. Ga door met het toevoegen van dia&#39;s totdat u alle afbeeldingen hebt toegevoegd die u wilt roteren in de Carousel-set.
1. (Optioneel) Voer een van de volgende handelingen uit:

   * Sleep indien nodig dia&#39;s om de volgorde van de afbeeldingen in de lijst te wijzigen.
   * Als u een afbeelding wilt verwijderen, selecteert u de afbeelding en selecteert u vervolgens **[!UICONTROL Delete Slide]** op de werkbalk.

   * Als u een voorinstelling wilt toepassen, selecteert u in de rechterbovenhoek van de pagina de vervolgkeuzelijst met voorinstellingen en selecteert u vervolgens een voorinstelling die u tegelijk op de set wilt toepassen.

   Selecteer de dia om een dia te verwijderen. Selecteer op de werkbalk **[!UICONTROL Delete Slide]** . Als u een dia wilt verplaatsen, selecteert u het pictogram voor herschikking en gaat u naar de gewenste locatie.

1. Nadat u de afbeeldingen in dia&#39;s hebt toegevoegd, kunt u een hotspot, afbeelding met hyperlinks of beide toevoegen aan uw afbeelding. Zie [ hotspots of beeldkaarten aan een Banner van het Beeld ](#adding-hotspots-or-image-maps-to-an-image-banner) toevoegen.
1. U kunt het visuele ontwerp en het gedrag van carrouselsets wijzigen. Selecteer de tabbladen **[!UICONTROL Behavior]** en **[!UICONTROL Appearance]** als u de weergave van de carrouselbanner of het gedrag van specifieke componenten wilt aanpassen. Zie [ de Kijker beheren stelt ](/help/assets/dynamic-media/viewer-presets.md) voor meer informatie vooraf in over hoe te om de kijkersredacteur te gebruiken.

   >[!NOTE]
   >
   >Voor carrouselbanners kunt u het volgende aanpassen:
   >
   >* Duur waarin een afbeelding wordt weergegeven. Standaard wordt elke afbeelding 9 seconden weergegeven.
   >* Animatie. Elke dia-overgang is standaard vervagen. U kunt dat wijzigen in een dia-overgang.
   >* Stijl van de knoppen. Gebruikers kunnen door de banners roteren door elke punt of elk aantal te selecteren. U kunt wijzigen waar de knoppen van de ingestelde indicator worden weergegeven (en of ze numeriek of gestippeld zijn) en hoe groot ze zijn.
   >* Wijzig de markeerstijl van een afbeeldingskaart of het pictogram dat voor hotspots wordt gebruikt.
   >* Voordat u een viewervoorinstelling bewerkt, kiest u de stijl waarop u de voorinstelling wilt baseren. Als u geen stijl kiest en de voorinstelling van de viewer gaat bewerken, gaan alle wijzigingen verloren als u een andere voorinstelling kiest.

   U kunt ook een voorvertoning van de vormgeving van de carrouselbanner weergeven. Zie [ (Optioneel) Voorvertoning carrouselbanners weergeven ](#optional-previewing-carousel-banners) .

1. Selecteer **[!UICONTROL Save]** wanneer u klaar bent.

## Hotspots of afbeeldingen met hyperlinks toevoegen aan een afbeeldingsbanner {#adding-hotspots-or-image-maps-to-an-image-banner}

Met de Carousel-set-editor kunt u hotspots of afbeeldingen met hyperlinks toevoegen aan een banner.

Wanneer u hotspots of afbeeldingen met hyperlinks toevoegt, kunt u deze definiëren als een pop-upweergave in de Snelle weergave, als een hyperlink of als een Experience-fragment.

Zie [ Fragment van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md).

>[!NOTE]
>
>De gereedschappen voor het delen van sociale media in de Carousel Banner worden niet ondersteund wanneer u de viewer insluit in een Experience Fragment.
>
>Om dit probleem te verhelpen, kunt u voorinstellingen voor viewers gebruiken of maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

Terwijl u hotspots of afbeeldingen met hyperlinks toevoegt aan een afbeelding, vergeet dan niet uw werk op te slaan. Opties voor Ongedaan maken en Opnieuw worden in de rechterbovenhoek van de pagina ondersteund tijdens de huidige sessie voor maken en bewerken.

Wanneer u klaar bent met het maken van uw carrouselbanner, kunt u Voorvertoning optioneel gebruiken om een voorstelling te zien van hoe uw carrouselbanner aan klanten wordt weergegeven.

Zie [ (Optioneel) Voorvertoning carrouselbanners weergeven ](#optional-previewing-carousel-banners) .

>[!NOTE]
>
>Wanneer u hotspots toevoegt aan een afbeeldingsbanner, worden de gegevens van de hotspot opgeslagen op dezelfde metagegevenslocatie, relatief ten opzichte van de locatie van de afbeelding. Dit geldt ongeacht of het een interactieve afbeelding of een carrouselbanner is. Deze functionaliteit betekent dat u in elke viewer eenvoudig dezelfde afbeelding opnieuw kunt gebruiken, samen met de gedefinieerde hotspotgegevens.
>
>Houd er echter rekening mee dat Carousel Banners afbeeldingen met hyperlinks ondersteunen op afbeeldingen die ook hotspots kunnen bevatten. Interactieve afbeeldingen bieden dat niet. Onthoud deze tip als u een interactieve afbeelding of carrouselbanner wilt maken die dezelfde afbeelding gebruikt. Overweeg om interactieve afbeeldingen en carrouselbanners te maken met aparte kopieën van dezelfde afbeelding.

>[!NOTE]
>
>Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

<!-- See also [Adding Image Maps](/help/assets/image-maps.md). -->

**om hotspots of beeldkaarten aan een Banner van het Beeld toe te voegen:**

1. Navigeer vanuit Assets naar de carrouselset die u interactief wilt maken.
1. Selecteer de carrouselset en selecteer **[!UICONTROL Edit]** . De Carousel Viewer Editor wordt geopend.
1. Selecteer de dia die u interactief wilt maken.
1. Selecteer **[!UICONTROL Hotspot]** of **[!UICONTROL Image Map]** in de linkerbovenhoek van de pagina.
1. Voer een van de volgende handelingen uit:

   * Voor hotspots: selecteer in de afbeelding de locatie waar u de hotspot wilt weergeven.
   * Voor afbeeldingen met hyperlinks: sleep in de afbeelding van linksboven naar rechtsonder om het gebied met de afbeelding met hyperlinks te maken. U kunt de grootte van de afbeelding met hyperlinks aanpassen door de hoeken te slepen.

   Sleep indien nodig de hotspot of de afbeelding met hyperlinks naar een nieuwe locatie. U kunt ook de pijltoetsen op het toetsenbord gebruiken om de positie van een geselecteerde hotspot te bepalen. Voeg desgewenst meer hotspots of afbeeldingen met hyperlinks toe.

   Als u een hotspot of afbeelding met hyperlinks wilt verwijderen, selecteert u de tab **[!UICONTROL Actions]** . Selecteer onder de kop **[!UICONTROL Maps & Hotspots]** in de vervolgkeuzelijst **[!UICONTROL Selected Type]** de naam van de hotspot of de afbeelding met hyperlinks die u wilt verwijderen. Selecteer het pictogram **[!UICONTROL Trash]** naast het menu en selecteer vervolgens **[!UICONTROL Delete]** .

1. Typ in het tekstveld Naam de naam van de hotspot of de afbeelding met hyperlinks. Deze naam wordt ook weergegeven in de vervolgkeuzelijst **[!UICONTROL Maps & Hotspot]** . Als u een naam opgeeft, kunt u de hotspot of de afbeelding met hyperlinks gemakkelijk herkennen als u deze later wilt wijzigen.
1. Voer op het tabblad **[!UICONTROL Actions]** een van de volgende handelingen uit:

   * Selecteer **[!UICONTROL Quickview]** .

      * Als u een Experience Manager Sites <!-- and Ecommerce--> -klant bent, selecteert u het pictogram Productkiezer (vergrootglas) om de pagina Selecteer product te openen. Als u wilt terugkeren naar de Carousel Banner Editor, selecteert u het product dat u wilt gebruiken en selecteert u vervolgens het vinkje in de rechterbovenhoek van de pagina.
      * Als u geen Experience Manager Sites <!-- or Ecommerce -->-klant bent:

         * Definieer variabelen. Zie [ hotspot variabelen ](#identifying-hotspot-and-image-map-variables) identificeren.
         * Voer vervolgens handmatig de SKU-waarde in. Typ in het tekstveld SKU-waarde de SKU (Stock Keeping Unit) van het product. Dit is een unieke id voor elk afzonderlijk product of elke service die u aanbiedt. De ingevoerde waarde SKU vult automatisch het variabele gedeelte van het malplaatje van de Snelle mening. Het systeem weet nu om geselecteerde hotspot met een bepaalde Snelle mening van SKU te associëren.
         * (Optioneel) Als de Snelle weergave andere variabelen bevat die u moet gebruiken om een product verder te identificeren, selecteert u **[!UICONTROL Add Generic Variable]** . Geef in het tekstveld een extra variabele op. category=Mens is bijvoorbeeld een toegevoegde variabele.

         * Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Hyperlink]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het pictogram Sitekiezer (map) om naar een URL te navigeren.

        >[!NOTE]
        >
        >De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.

      * Als u een zelfstandige klant bent, geeft u in het href-tekstveld het volledige URL-pad naar een gekoppelde webpagina op.

   Zorg ervoor dat u opgeeft of u de koppeling wilt openen in een nieuw browsertabblad (aanbevolen standaard) of op hetzelfde tabblad.

   Zie [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md) voor meer informatie.

   * Selecteer **[!UICONTROL Experience Fragment]** .

      * Als u een Experience Manager Sites-klant bent, selecteert u het zoekpictogram (vergrootglas) om de pagina Experience Fragment te openen. Als u wilt terugkeren naar de pagina Hotspot-beheer, selecteert u het gewenste ervaringsfragment en selecteert u vervolgens in de rechterbovenhoek van de pagina **[!UICONTROL Select]** .
Zie [ Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/content-fragments.md).

      * Geef de breedte en hoogte van het ervaringsfragment op zoals dit op de banner wordt weergegeven.

        >[!NOTE]
        >
        >De gereedschappen voor het delen van sociale media in de Carousel Banner worden niet ondersteund wanneer u de viewer insluit in een Experience Fragment.
        >
        >U kunt dit omzeilen door voorinstellingen voor viewers te gebruiken of te maken die geen gereedschappen voor het delen van sociale media hebben. Met dergelijke voorinstellingen voor viewers kunt u de voorinstelling met succes insluiten in Experience Fragments.

   ![ experience_fragment-carouselbanner ](assets/experience_fragment-carouselbanner.png)

   U kunt ook een voorvertoning van de vormgeving van de carrouselbanner weergeven. Zie [ (Optioneel) Voorvertoning carrouselbanners weergeven ](#optional-previewing-carousel-banners) .

1. Selecteer **[!UICONTROL Save]** .
1. Publish de carrouselset. Bij het publiceren wordt de insluitcode of URL gemaakt die u op uw websitepagina kunt gebruiken. Als u een Experience Manager Sites-klant bent, voegt u de carrousel rechtstreeks toe aan uw webpagina.

   Zie [ de activa van Publish ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

   Zie [ een carrousel toevoegen die aan uw website landende pagina ](#adding-a-carousel-banner-to-your-website-page) wordt geplaatst

## Carrouselsets bewerken {#editing-carousel-sets}

>[!NOTE]
>
>Gebruikers zonder beheerdersrechten moeten worden toegevoegd aan de **[!UICONTROL dam-users]** -groep om carrouselbanners te kunnen maken of bewerken. Als u problemen ondervindt bij het maken of bewerken, raadpleegt u de systeembeheerder die u aan de groep **[!UICONTROL dam-users]** kan toevoegen.

U kunt verschillende bewerkingstaken uitvoeren op Carousel Sets, zoals:

* Voeg dia&#39;s toe aan een Carousel-set. Zie ook [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).
* Wijzig de volgorde van de dia&#39;s in de carrouselset.
* Elementen in de Carousel-set verwijderen.
* Een viewervoorinstelling toepassen.
* Verwijder de carrouselset.
* Voeg hotspots en afbeeldingen met hyperlinks toe of bewerk deze. Zie ook [ Werk met Kiezers ](/help/assets/dynamic-media/working-with-selectors.md).

**om de Reeksen van Carousel uit te geven:**

1. Voer een van de volgende handelingen uit:

   * Houd de cursor boven een Carousel-set-element en selecteer vervolgens **[!UICONTROL Edit]** (potloodpictogram).
   * Houd de cursor boven een Carousel-set-element, selecteer **[!UICONTROL Select]** (vinkje) en selecteer vervolgens op de werkbalk **[!UICONTROL Edit]** .

   * Selecteer een Carousel-set-element en selecteer vervolgens in de linkerbovenhoek van de pagina **[!UICONTROL Edit]** (potloodpictogram).

1. Voer een van de volgende handelingen uit om de Carousel-set te bewerken:

   * Selecteer het pictogram **[!UICONTROL Add Slide]** als u een dia wilt toevoegen. Navigeer naar het element dat u aan die dia wilt toevoegen en selecteer vervolgens het vinkje.
   * Als u de volgorde van dia&#39;s wilt wijzigen, sleept u een dia naar een nieuwe locatie (selecteer het pictogram voor opnieuw ordenen om items te verplaatsen).
   * Om hotspot of beeldkaart toe te voegen, selecteer hotspot of beeld kaartpictogrammen en zie [ hotspots en beeldkaarten aan een Banner van het Beeld ](#adding-hotspots-or-image-maps-to-an-image-banner) toevoegen.
   * Als u de weergave of het gedrag van de carrouselset wilt bewerken, selecteert u de tab **[!UICONTROL Appearance]** of de tab **[!UICONTROL Behavior]** en stelt u de gewenste opties in.
   * Als u hotspots of afbeeldingen met hyperlinks wilt bewerken, selecteert u op de gewenste dia een hotspot of afbeelding met hyperlinks. Breng de wijzigingen aan onder het tabblad **[!UICONTROL Actions]** .
   * Als u een dia wilt verwijderen, selecteert u deze en selecteert u **[!UICONTROL Delete Slide]** in de werkbalk.
   * Als u een voorinstelling wilt toepassen, selecteert u in de rechterbovenhoek van de pagina de vervolgkeuzelijst **[!UICONTROL Preset]** en selecteert u vervolgens een voorinstelling voor de viewer.
   * Als u een volledige Carousel-set wilt verwijderen, navigeert u naar de Carousel-set, selecteert u deze en selecteert u vervolgens **[!UICONTROL Delete]** .

   >[!NOTE]
   >
   >Als u interactieve afbeeldingen met hotspots bewerkt en de afbeelding bijsnijdt, worden de hotspots verwijderd.

## (Optioneel) Voorvertoning carrouselbanners bekijken {#optional-previewing-carousel-banners}

Met Voorvertoning kunt u zien hoe de carrouselbanner er uitziet voor klanten. Met Voorvertoning kunt u ook de hotspots en afbeeldingen van de carrouselbanner testen om te controleren of deze zich naar behoren gedragen.

Wanneer u tevreden bent met de carrouselbanner, kunt u deze publiceren.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) inbedden.
Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Dynamic Media Assets aan pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

U kunt een voorvertoning van carrouselbanners weergeven in de Carousel Editor (voorkeursmethode) of in de lijst **[!UICONTROL Viewers]** .

**aan naar keuze voorproef Carousel Banners:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande carrouselbanner die u hebt gemaakt en selecteer deze om deze te openen.
1. Selecteer **[!UICONTROL Edit]** .
1. Selecteer in de lijst met voorinstellingen voor viewers rechts op de werkbalk een viewer om een voorvertoning van de carrouselbanner weer te geven.

   ![ experience_fragment-carouselbanner-viewerdropdown ](assets/experience_fragment-carouselbanner-viewerdropdown.png)

1. Selecteer **[!UICONTROL Preview]** .
1. Als u de bijbehorende acties wilt testen, selecteert u de hotspots of afbeeldingen met hyperlinks in de afbeelding.

**aan voorproef carrouselbanners van de lijst van Kijkers:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande carrouselbanner die u hebt gemaakt en selecteer deze om deze te openen.
1. Selecteer het pictogram Inhoud in de linkerbovenhoek van de voorvertoningspagina.
1. Selecteer in de lijst **[!UICONTROL Viewers]** in het deelvenster links van de pagina de naam van de voorinstelling voor de carrouselbannerviewer die u wilt gebruiken.
1. Als u de bijbehorende acties wilt testen, selecteert u de hotspots of afbeeldingen met hyperlinks in de afbeelding.

## Publish Carousel Banners {#publishing-carousel-banners}

Als u de carrousel wilt gebruiken, moet u deze publiceren. Als u een Carousel-set publiceert, worden de URL en de insluitcode geactiveerd. Het publiceert ook de carrousel naar de Dynamic Media-cloud, die is geïntegreerd met een CDN voor schaalbare en krachtige levering.

>[!NOTE]
>
>Als u een bestaande interactieve afbeelding met hotspots voor uw carrouselbanner gebruikt, moet u de interactieve afbeelding afzonderlijk publiceren nadat u de carrouselbanner hebt gepubliceerd.
>
>Als u een reeds gepubliceerde interactieve afbeelding wijzigt die u in een carrouselbanner gebruikt, publiceert u ook de interactieve afbeelding zodat deze wijzigingen worden weerspiegeld in de carrouselbanner.

Zie [ Publish Dynamic Media Assets ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md) voor informatie over hoe te om carrouselbanners te publiceren.

## Een Carousel-banner toevoegen aan uw websitepagina {#adding-a-carousel-banner-to-your-website-page}

Nadat u bannerafbeeldingen hebt geüpload om een carrousel, toegevoegde hotspots of afbeeldingen met hyperlinks of beide te maken, naar de banner. De carrouselset is gepubliceerd. U kunt deze nu toevoegen aan uw bestaande websitepagina.

>[!NOTE]
>
>Als u een Experience Manager Sites-klant bent, kunt u de carrouselbanner rechtstreeks aan de pagina toevoegen door de component Interactieve media naar de pagina te slepen. Zie [ Dynamic Media Assets aan Pagina&#39;s ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md) toevoegen.

Als u echter een zelfstandige Experience Manager Assets-klant bent, kunt u de carrouselbanner handmatig toevoegen aan de bestemmingspagina van uw website.

1. Kopieer de insluitcode van de gepubliceerde carrouselset.
Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/dynamic-media/embed-code.md) inbedden.

1. Voeg de insluitcode die u van Experience Manager Assets hebt gekopieerd, toe aan uw webpagina.
De gekopieerde insluitcode reageert zodat deze automatisch in het insluitingsgebied van de pagina past.

## De Carousel Banner integreren met een bestaande QuickView {#integrating-the-carousel-banner-with-an-existing-quickview}

Opmerking: deze stap is alleen van toepassing als u een zelfstandige Experience Manager Assets-klant bent.

De laatste stap in dit proces is het integreren van de carrouselbanner met een bestaande implementatie van QuickView op uw website. Elke implementatie van de Snelle weergave is uniek en er is een specifieke aanpak nodig waarbij meestal een front-end IT-persoon wordt betrokken.

De bestaande implementatie van QuickView vertegenwoordigt normaal gesproken een reeks onderling samenhangende acties die op de webpagina in de volgende volgorde plaatsvinden:

1. Een gebruiker activeert een element in de gebruikersinterface van uw website.
1. De front-end code verkrijgt een Snelle mening URL die op het gebruikersinterface element wordt gebaseerd dat in stap 1 werd teweeggebracht.
1. De front-end code verzendt een Ajax- verzoek gebruikend URL die in stap 2 wordt verkregen.
1. De achterste logica retourneert de corresponderende gegevens of inhoud van de Snelle weergave terug naar de front-end code.
1. De front-end code laadt de Snelle meningsgegevens of inhoud.
1. Naar keuze, zet de voorste-eindcode de geladen Snelle meningsgegevens in een vertegenwoordiging van HTML om.
1. De front-end code geeft een modaal dialoogvenster of deelvenster weer en geeft de HTML-inhoud op het scherm voor de gebruiker weer.

Deze aanroepen vertegenwoordigen geen onafhankelijke openbare API-aanroepen die door de webpaginalogica kunnen worden aangeroepen vanuit een willekeurige stap. In plaats daarvan, is het een geketende vraag waar elke volgende stap in de laatste fase (callback) van de vorige stap verborgen is.

Wanneer een gebruiker een hotspot of afbeelding met hyperlinks selecteert, wordt deze interactie door de viewer afgehandeld terwijl de carrouselbanner stap 1 en gedeeltelijk stap 2 vervangt. De viewer retourneert een gebeurtenis naar de webpagina die alle eerder toegevoegde hotspot- of afbeeldingskaartgegevens bevat.

In een dergelijke gebeurtenishandler doet de front-end code het volgende:

* Luistert naar een gebeurtenis die door de carrouselbanner wordt uitgegeven.
* Hiermee maakt u een URL van de Snelle weergave op basis van de gegevens van de hotspot of afbeelding met hyperlinks.
* Triggert het proces waarbij de Snelle weergave vanaf de achterkant wordt geladen en op het scherm wordt weergegeven voor weergave.

De insluitcode die door Experience Manager Assets wordt geretourneerd, bevat al een gebruiksklare gebeurtenishandler die als commentaar wordt gemarkeerd.

Het is dus alleen nodig de commentaarmarkering van de code ongedaan te maken en de dummy-handlertekst te vervangen door de code die specifiek is voor de specifieke webpagina.

Het proces voor het samenstellen van de URL van de Snelle weergave is tegengesteld aan het proces voor het identificeren van hotspot- en afbeeldingskaartvariabelen die eerder zijn behandeld.

Zie [ hotspot en beeld kaartvariabelen identificeren ](#identifying-hotspot-and-image-map-variables).

De laatste stap om de URL van de Snelle weergave te activeren en het deelvenster Snelle weergave te activeren, vereist hoogstwaarschijnlijk de hulp van een front-end IT-persoon van uw IT-afdeling. Ze hebben de kennis om te weten hoe u de implementatie van de Snelle weergave nauwkeurig vanuit de juiste stap kunt activeren en beschikken over een gebruiksklare URL voor de Snelle weergave.

## Aangepaste pop-upvensters® maken met Quickview {#using-quickviews-to-create-custom-pop-ups}

Zie [ douane pop-up Windows® gebruikend QuickView ](/help/assets/dynamic-media/custom-pop-ups.md) creëren.
