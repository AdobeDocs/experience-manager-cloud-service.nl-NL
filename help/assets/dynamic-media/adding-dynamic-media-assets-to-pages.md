---
title: Dynamische media-elementen toevoegen aan pagina's
description: Dynamische mediacomponenten toevoegen aan een pagina in AEM
translation-type: tm+mt
source-git-commit: 454f4c9585b575ae0d904292ddd659148393db0b

---


# Adding Dynamic Media Assets to Pages{#adding-dynamic-media-assets-to-pages}

Als u de functionaliteit Dynamische media wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de component **Dynamische media**, **Interactieve media**, **Panoramische media** of **Video 360 Media** rechtstreeks op de pagina toevoegen. U doet dit door de modus Lay-out in te voeren en de componenten Dynamische media in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en elementen aan de component toevoegen. De dynamische componenten van Media zijn slim - zij weten of u een beeld of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U voegt dynamische media-elementen rechtstreeks aan de pagina toe als u AEM als uw WCM gebruikt. Als u een derde voor uw WCM gebruikt, of [verbinding](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [bedt](/help/assets/dynamic-media/embed-code.md) uw activa in. Voor een responsieve website van derden raadpleegt u het [leveren van geoptimaliseerde afbeeldingen op een responsieve site](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>U moet elementen publiceren voordat u deze aan pagina&#39;s in AEM toevoegt. See [Publishing Dynamic Media Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een component Dynamische media aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een mediacomponent Dynamische media, Interactieve media, Panoramische media of Video 360 aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De dynamische componenten van Media worden beschreven in de volgende secties.

**Een component Dynamische media aan een pagina toevoegen**

1. Open in AEM de pagina waaraan u de component Dynamische media wilt toevoegen.
1. Tik in het linkerdeelvenster op het pictogram **[!UICONTROL Componenten]** en filter vervolgens op Dynamische media.

   Als er geen dynamische mediacomponenten beschikbaar zijn, moet u de dynamische mediacomponenten inschakelen of inschakelen. Zie Sjablonen [bewerken - Sjabloonauteurs](/help/sites-cloud/authoring/features/templates.md) voor meer informatie.

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Sleep een component **[!UICONTROL Dynamische media]** en zet deze op de gewenste locatie op de pagina neer.

   In het onderstaande voorbeeld wordt de component **[!UICONTROL Video 360 Media]** gebruikt.

   ![6_5_360video_wcmcomponentdrag](assets/6_5_360video_wcmcomponentdrag.png)

1. Houd de muisaanwijzer rechtstreeks boven de component. Tik eenmaal om de werkbalk van de component weer te geven wanneer de component is omringd door een blauw vak. Tik op het pictogram **[!UICONTROL Configuratie (moersleutel)]** .

   ![6_5_360video_wcmcomponentconfigure](assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [Stel de componentopties](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) naar wens in.

   In het onderstaande voorbeeld ziet u het dialoogvenster Dynamische media **[!UICONTROL Video 360 Media]** component en de opties die beschikbaar zijn in de vervolgkeuzelijst Voorinstelling viewer.

   ![Video 360-mediacomponent](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Als u klaar bent, tikt u in de rechterbovenhoek van het dialoogvenster op het vinkje om de wijzigingen op te slaan.

## Dynamische mediacomponenten lokaliseren {#localizing-dynamic-media-components}

U kunt dynamische mediacomponenten op twee manieren lokaliseren:

* Open **[!UICONTROL Eigenschappen]** op een webpagina in Sites en selecteer het tabblad **[!UICONTROL Geavanceerd]** . Selecteer de gewenste taal voor lokalisatie.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de sitekiezer. Tik op **[!UICONTROL Eigenschappen]** en selecteer het tabblad **[!UICONTROL Geavanceerd]** . Selecteer de gewenste taal voor lokalisatie.

   >[!NOTE]
   >
   >Niet alle talen die in het menu **[!UICONTROL Taal]** beschikbaar zijn, hebben tokens toegewezen.

## Beschikbare dynamische mediacomponenten {#dynamic-media-components}

De dynamische componenten van Media zijn beschikbaar wanneer u het pictogram van **[!UICONTROL Componenten]** tikt, dan filter op **[!UICONTROL Dynamische Media]**.

De dynamische componenten van Media die beschikbaar zijn omvatten het volgende:

* **[!UICONTROL Dynamische media]** - wordt gebruikt voor elementen zoals afbeeldingen, video, eCatalogs en centrifuges.
* **[!UICONTROL Interactieve media]** - Gebruik voor alle interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramische media]** - Gebruik voor panoramische afbeeldingen of panoramische VR-afbeeldingselementen.
* **[!UICONTROL Video 360 Media]** - Gebruik voor 360 video en 360 VR video activa.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten via de sjablooneditor beschikbaar worden gemaakt voordat ze kunnen worden gebruikt. Nadat ze in de sjablooneditor beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als alle andere AEM-componenten.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Component: Dynamische media {#dynamic-media-component}

De component Dynamische media is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer hierop. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Dynamic Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>
Houd er rekening mee dat het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina niet wordt ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Dynamic Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

Wanneer u de component Dynamische media toevoegt en **[!UICONTROL Dynamische media-instellingen]** leeg zijn of een element niet correct kunt toevoegen, controleert u het volgende:

* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat dynamische media is ingeschakeld, hebben geen TIFF-bestand met piramide.

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de component Dynamische media kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

U kunt de volgende instellingen voor dynamische media bewerken door te tikken op het pictogram **[!UICONTROL Bewerken]** in de component en vervolgens op Instellingen **[!UICONTROL voor]** dynamische media.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent Dynamische media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component op het **[!UICONTROL Geavanceerde]** lusje met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]**.

* **[!UICONTROL Voorinstelling]** viewer: selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

   Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De weergegeven viewervoorinstellingen zijn ook slim. Alleen relevante viewervoorinstellingen worden weergegeven.

* **[!UICONTROL Viewermodifiers]**—Viewer modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals beschreven in de Viewer Reference Guide. Een voorbeeld van een viewermodifier is `posterimage=img.jpg&caption=text.vtt,1` die een andere afbeelding instelt voor de videominiatuur en een ondertitelingsbestand aan de video koppelt.

* **[!UICONTROL Voorinstelling]** afbeelding - Selecteer een bestaande voorinstelling voor de afbeelding in het keuzemenu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en andersom.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Afbeeldingswijzigingstoetsen]**- U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te leveren. Deze worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Onderbrekingspunten]**- Als u dit element gebruikt op een responsieve site, moet u de onderbrekingspunten van de afbeelding toevoegen. Afbeeldingsonderbrekingspunten moeten door komma&#39;s (,) worden gescheiden. Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te tikken.

* **[!UICONTROL Titel]**- Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt-tekst]**- Voeg een titel toe aan de afbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Openen in]**—U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breedte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Hoogte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.


#### Wanneer u werkt met video {#when-working-with-video}

Met de component Dynamische media kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-173](assets/chlimage_1-540.png)

U kunt de volgende instellingen voor dynamische media bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

>[!NOTE]
>
>Standaard is de videocomponent Dynamic Media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]** op het **[!UICONTROL Geavanceerde]** lusje.

* **[!UICONTROL Viewer preset**—Selecteer een bestaande voorinstelling voor een videoviewer in het vervolgkeuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Viewer modifiers**—Viewer modifiers have the form of name=value pair with a &amp; delimiter and let you change viewers as described in the Adobe Viewers Reference Guide. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1`

   Met viewermodifiers kunt u bijvoorbeeld het volgende doen:

   * Een bijschriftbestand koppelen aan een video: [bijschrift](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Een navigatiebestand koppelen aan een video: [navigatie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)
   U kunt de volgende geavanceerde instellingen bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

* **[!UICONTROL Titel**—Wijzig de titel van de video.

* **[!UICONTROL Breedte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Hoogte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met Slim uitsnijden {#when-working-with-smart-crop}

Met de component Dynamische media kunt u SmartCrop-afbeeldingselementen toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

Zie Slim uitsnijden [gebruiken met dynamische media van AEM-elementen](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/smart-crop-feature-video-use.html)

Zie ook [Afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

U kunt de volgende instelling voor dynamische media bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent Dynamische media adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component op het **[!UICONTROL Geavanceerde]** lusje met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]**.

* **[!UICONTROL Afbeeldingswijzigingstoetsen]**- U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te leveren. Deze worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

   U kunt de volgende geavanceerde instellingen bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

* **[!UICONTROL Hoogte-breedteverhouding]** inschakelen - Komt overeen met de hoogte-breedteverhouding van de oorspronkelijke afbeelding wanneer u een slimme uitsnijdvertoning selecteert.

* **[!UICONTROL Titel]**- Wijzig de titel van de afbeelding Slim uitsnijden.

* **[!UICONTROL Alt-tekst]**- Voeg een titel toe aan de slimme-bijsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Openen in]**—U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

   Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breedte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Hoogte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

### Component: Interactieve media {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de component **[!UICONTROL Interactieve media]** .

De component Interactieve media is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer hierop. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Interactive Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>
Houd er rekening mee dat het toewijzen van een andere viewervoorinstelling aan elke interactieve mediacomponent op die pagina niet wordt ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle interactieve mediacomponenten die op de pagina elementen van hetzelfde type gebruiken.

![chlimage_1-174](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL algemene]** instellingen bewerken door te tikken op **[!UICONTROL Bewerken]** in de component.

* **[!UICONTROL Voorinstelling]** viewer: selecteer een bestaande viewervoorinstelling in het keuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Titel]**- Wijzig de titel van de video.

* **[!UICONTROL Breedte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Hoogte]**- Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

   U kunt de volgende instellingen voor **[!UICONTROL Toevoegen aan winkelwagentje]** bewerken door in de component op **[!UICONTROL Bewerken]** te klikken.

* **[!UICONTROL Productelement]** tonen - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

* **[!UICONTROL Productprijs]** tonen - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

* **[!UICONTROL Productformulier]** tonen - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.

### Component: Panoramische media {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panoramische afbeeldingen zijn. Dergelijke afbeeldingen bieden een kijkervaring van 360° voor een ruimte, eigenschap, locatie of landschap. Een afbeelding kan alleen als bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Gelabeld met de trefwoorden `equirectangular` (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [Tags](/help/sites-cloud/authoring/features/tags.md)gebruiken.

Zowel zijn de aspectverhouding als de sleutelwoordcriteria op panoramische activa voor de pagina van elementdetails en de **[!UICONTROL Panoramische Media]** WCM component van toepassing.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere versies van het **[!UICONTROL Panoramische Media]** -onderdeel dat op dezelfde pagina wordt gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>
Houd er rekening mee dat het niet wordt ondersteund om een andere viewervoorinstelling toe te wijzen aan elk **[!UICONTROL Panoramisch Media]** -onderdeel op die pagina.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Panoramische Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

![panoramisch-media-viewer-voorinstelling](assets/panoramic-media-viewer-preset.png)

U kunt het volgende plaatsen uitgeven door te tikken **[!UICONTROL vormt]** in de component.

* **[!UICONTROL Voorinstelling]** viewer - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. U moet viewervoorinstellingen publiceren voordat u deze kunt gebruiken. Zie Voorinstellingen [van viewers](/help/assets/dynamic-media/managing-viewer-presets.md)beheren.

### Component: Video 360-media {#video-media-component}

Met de Media **[!UICONTROL -component]** Video 360 kunt u equirechthoekige video op uw webpagina weergeven voor een indrukwekkende kijkervaring in een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; afspelen op mobiele apparaten maakt doorgaans gebruik van de ingebouwde gyroscopische besturingselementen.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

U kunt het volgende plaatsen uitgeven door te tikken **[!UICONTROL vormt]** in de component.

* **[!UICONTROL Voorinstelling]** viewer - Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer. Gebruik Video360VR voor eindgebruikers die een virtuele realiteitsbril gebruiken. Bevat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik Video360_social, die basisbesturingselementen voor het afspelen van video bevat. Video renderen wordt uitgevoerd in de stereomodus. Handmatige zichtpuntcontrole is uitgeschakeld, maar gyroscopische controle is ingeschakeld. Er zijn geen functies voor sociale media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. U moet viewervoorinstellingen publiceren voordat u deze kunt gebruiken. Zie Voorinstellingen [van viewers](/help/assets/dynamic-media/managing-viewer-presets.md)beheren.

### HTTP/2 gebruiken om dynamische media-elementen te leveren {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van dynamische media-elementen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van Inhoud](/help/assets/dynamic-media/http2faq.md) voor volledige details over begonnen worden het gebruiken van HTTP/2 met uw Dynamische rekening van Media.

>[!MORELIKETHIS]
>
>* [De videospeler gebruiken in dynamische AEM-media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Interactieve video gebruiken met AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [Understanding the Asset Viewer with AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Aangepaste videominiatuur gebruiken met dynamische AEM-media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Werken met kleurbeheer met dynamische AEM-media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Afbeelding verscherpen gebruiken met dynamische AEM-media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

