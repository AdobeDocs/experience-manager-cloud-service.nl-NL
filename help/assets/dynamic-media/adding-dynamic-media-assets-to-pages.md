---
title: Dynamic Media-elementen toevoegen aan pagina's
description: Dynamic Media-componenten als Cloud Service toevoegen aan een pagina in Adobe Experience Manager.
translation-type: tm+mt
source-git-commit: c3ada59105cad7c2fc3b36b032d045b91f86b495
workflow-type: tm+mt
source-wordcount: '2999'
ht-degree: 8%

---


# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de functionaliteit voor dynamische media wilt toevoegen aan assets die u op uw websites gebruikt, kunt u de component **Dynamische media**, **Interactieve media**, **Panoramische media** of **Video 360-media** rechtstreeks op de pagina toevoegen. U doet dit door naar de modus Lay-out te gaan en de componenten voor dynamische media in te schakelen. Vervolgens kunt u deze componenten aan de pagina toevoegen en assets aan de component toevoegen. De componenten voor dynamische media zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U voegt Dynamic Media-elementen rechtstreeks aan de pagina toe als u Experience Manager als uw WCM gebruikt. Als u een oplossing van derden gebruikt voor uw WCM, moet u uw assets [koppelen](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [insluiten](/help/assets/dynamic-media/embed-code.md). Voor een responsieve website van derden raadpleegt u het [leveren van geoptimaliseerde afbeeldingen op een responsieve site](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>U moet elementen publiceren voordat u ze in Experience Manager aan pagina&#39;s toevoegt. Zie [Dynamic Media-middelen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een Dynamic Media-component toevoegen aan een pagina {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een 3D-mediacomponent, Dynamic Media, Interactieve media, Panoramische media, SmartCrop-video of Video 360-mediacomponent aan een pagina is hetzelfde als het toevoegen van een component aan een pagina. De Dynamic Media-componenten worden in de volgende secties beschreven.

**Een Dynamic Media-component aan een pagina toevoegen**

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Tik in het linkervenster op het pictogram **[!UICONTROL Components]** en filter vervolgens voor Dynamic Media.

   Als er geen lijst met Dynamic Media-componenten beschikbaar is, moet u waarschijnlijk de Dynamic Media-componenten inschakelen die u wilt gebruiken. Zie [Dynamic Media-componenten inschakelen](#enabling-dynamic-media-components).

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Sleep een **[!UICONTROL Dynamic Media]** component en zet het neer op de gewenste plaats op de pagina.

1. Houd de muisaanwijzer rechtstreeks boven de component. Tik eenmaal om de werkbalk van de component weer te geven wanneer de component is omringd door een blauw vak. Tik op het pictogram **[!UICONTROL Configuration (wrench)]**.

   ![6_5_360video_wcmcomponentconfigure](assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [Stel de ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) opties van de component naar wens in.

   In het onderstaande voorbeeld ziet u het dialoogvenster Dynamic Media **[!UICONTROL Video 360 Media]** en de opties die beschikbaar zijn in de vervolgkeuzelijst Voorinstelling viewer.

   ![Video 360-mediacomponent](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Als u klaar bent, tikt u in de rechterbovenhoek van het dialoogvenster op het vinkje om de wijzigingen op te slaan.

### Dynamic Media-componenten {#enabling-dynamic-media-components} inschakelen

Als er geen Dynamic Media-componenten beschikbaar zijn om aan een pagina toe te voegen, betekent dit waarschijnlijk dat u eerst de componenten moet inschakelen die u wilt gebruiken.

1. Open in Experience Manager de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Tik links op de werkbalk naast de pagina op het pictogram Pagina-informatie en tik vervolgens op **[!UICONTROL Edit Template]** in de vervolgkeuzelijst.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Tik rechts van de werkbalk boven aan de pagina in de vervolgkeuzelijst op **[!UICONTROL Structure]**.

   ![Beleid](/help/assets/assets-dm/structure-mode.png)

1. Tik onder aan de pagina op **[!UICONTROL Layout Container]** om de werkbalk te openen en tik vervolgens op het pictogram Beleid.
1. Zorg ervoor dat op de **[!UICONTROL Layout Container]**-pagina onder de kop **[!UICONTROL Properties]** het tabblad **[!UICONTROL Allowed Components]** is geselecteerd.

   ![Toegestane componenten](/help/assets/assets-dm/allowed-components.png)

1. Schuif totdat u **[!UICONTROL Dynamic Media]** ziet.
1. Tik op het pictogram > links van **[!UICONTROL Dynamic Media]** om de lijst uit te vouwen en selecteer de Dynamic Media-componenten die u wilt inschakelen.

   ![Lijst met Dynamic Media-componenten](/help/assets/assets-dm/dm-components-select.png)

1. Tik rechtsboven op de pagina **[!UICONTROL Layout Container]** op het pictogram Gereed (vinkje).

1. Tik rechts van de werkbalk boven aan de pagina in de vervolgkeuzelijst op **[!UICONTROL Initial Content]** en [voeg vervolgens zoals gewoonlijk een Dynamic Media-component toe aan een pagina](#adding-a-dynamic-media-component-to-a-page).

## Dynamic Media-componenten lokaliseren {#localizing-dynamic-media-components}

U kunt Dynamic Media-componenten op twee manieren lokaliseren:

* Open **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]** op een webpagina in Sites. Selecteer de gewenste taal voor lokalisatie.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de siteselector. Tik op **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]**. Selecteer de gewenste taal voor lokalisatie.

   >[!NOTE]
   >
   >Niet alle talen in het menu **[!UICONTROL Language]** hebben tokens toegewezen.

## Beschikbare Dynamic Media-componenten {#dynamic-media-components}

Dynamic Media-componenten zijn beschikbaar wanneer u op het pictogram **[!UICONTROL Components]** tikt en vervolgens op **[!UICONTROL Dynamic Media]** filtert.

De volgende Dynamic Media-componenten zijn beschikbaar:

* **[!UICONTROL Dynamic Media]** - Wordt gebruikt voor assets zoals afbeeldingen, video, e-catalogi en spinsets.
* **[!UICONTROL Interactive Media]** - Gebruik deze optie voor interactieve elementen zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramic Media]** - Gebruik deze optie voor panoramische afbeeldingen of panoramische VR-afbeeldingselementen.
* **[!UICONTROL Video 360 Media]** - Gebruik voor 360 video- en 360 VR-video-elementen.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de sjablooneditor beschikbaar worden gemaakt voordat u ze kunt gebruiken. Nadat ze beschikbaar zijn gesteld in de sjablooneditor, kunt u de componenten aan uw pagina toevoegen, net als alle andere Experience Managers.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Component: Dynamic Media {#dynamic-media-component}

De Dynamic Media-component is slim. Afhankelijk van of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel: de grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de Dynamic Media-component die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Houd er rekening mee dat het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina niet wordt ondersteund.
>
>U kunt echter dezelfde viewer-voorinstelling gebruiken voor alle Dynamic Media-componenten die elementen van hetzelfde type gebruiken, binnen de pagina.

Wanneer u de Dynamic Media-component toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:

* De afbeelding heeft een piramide-TIFF-bestand. Afbeeldingen die zijn geïmporteerd voordat dynamische media is ingeschakeld, hebben geen TIFF-bestand met piramide.

#### Bij het werken met afbeeldingen {#when-working-with-images}

Met de Dynamic Media-component kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingensets, centrifuges en gemengde-mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding uit een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor afbeeldingen toepassen.

U kunt de volgende Dynamic Media-instellingen bewerken door te tikken op het pictogram **[!UICONTROL Edit]** in de component en vervolgens op **[!UICONTROL Dynamic Media Settings]**.

![dm-settings-image-preset](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Viewer preset]**—Selecteer een bestaande viewer-voorinstelling in het vervolgkeuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een afbeeldingsvoorinstelling gebruikt en vice versa.

   Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De weergegeven viewervoorinstellingen zijn ook slim: alleen relevante viewervoorinstellingen worden weergegeven.

* **[!UICONTROL Viewer modifiers]**—Viewer-modifiers hebben de vorm van name=value-paar met een &amp;-scheidingsteken en laten u viewers wijzigen, zoals uitgelegd in de Referentiehandleiding voor viewers. Een voorbeeld van een viewerwijzigingstoets is `posterimage=img.jpg&caption=text.vtt,1`. Hiermee wordt een andere afbeelding voor de videominiatuur ingesteld en wordt een ondertitelingsbestand aan de video gekoppeld.

* **[!UICONTROL Image preset]**—Selecteer een bestaande voorinstelling in het vervolgkeuzemenu. Als de afbeeldingsvoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een afbeeldingsvoorinstelling gebruikt en vice versa.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL Image Modifiers]**- U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze worden beschreven in Voorinstellingen afbeelding en de referentie van de opdracht Beeldbewerking.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL Breakpoints]**—Als u dit middel op een responsieve site gebruikt, moet u de onderbrekingspunten voor de afbeelding toevoegen. Afbeeldingsonderbrekingspunten moeten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te tikken.

* **[!UICONTROL Title]**—Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt Text]**—Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL URL, Open in]**—U kunt een middel instellen om een koppeling te openen. Stel de URL in en kies Openen in om aan te geven of u deze wilt openen in hetzelfde venster of in een nieuw venster.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL Width]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

* **[!UICONTROL Height]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.


#### Bij het werken met video {#when-working-with-video}

Gebruik de Dynamic Media-component om dynamische video toe te voegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u ervoor kiezen een vooraf gedefinieerde videoviewer te gebruiken voor het afspelen van de video op de pagina.

![chlimage_1-173](assets/chlimage_1-540.png)

U kunt de volgende Dynamic Media-instellingen bewerken door in de component op **[!UICONTROL Edit]** te klikken.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met **[!UICONTROL Width]** en **[!UICONTROL Height]** in **[!UICONTROL Advanced]** tabel.

* **[!UICONTROL Viewer preset]**—Selecteer een bestaande voorinstelling voor een videoviewer in het vervolgkeuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Viewer modifiers]**—Viewer-modifiers hebben de vorm van name=value-paar met een &amp;-scheidingsteken en laten u viewers wijzigen zoals is beschreven in de Referentiehandleiding voor Adobe-viewers. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1`

   Met vieweropties kunt u bijvoorbeeld het volgende doen:

   * Een bijschriftbestand aan een video koppelen: [caption](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Koppel een navigatiebestand aan een video: [navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Title]**—Wijzig de titel van de video.

* **[!UICONTROL Width]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

* **[!UICONTROL Height]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

#### Bij werken met Slim uitsnijden {#when-working-with-smart-crop}

Gebruik de Dynamic Media-component om SmartCrop-afbeeldingselementen aan uw webpagina&#39;s toe te voegen. Wanneer u de component bewerkt, kunt u ervoor kiezen een vooraf gedefinieerde videoviewer te gebruiken voor het afspelen van de video op de pagina.

Zie [Slim uitsnijden gebruiken met Experience Manager Assets Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/smart-crop-feature-video-use.html)

Zie ook [Afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md).

![dm-settings-smart-crop](assets/dm-settings-smart-crop.png)

U kunt de volgende Dynamic Media-instelling bewerken door in de component op **[!UICONTROL Edit]** te klikken.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Image Modifiers]**- U kunt afbeeldingseffecten toepassen door extra opdrachten voor afbeeldingen te geven. Deze worden beschreven in Voorinstellingen afbeelding en de referentie van de opdracht Beeldbewerking.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Enable Aspect Ration match]**—Selecteer deze optie als u wilt dat Dynamic Media een slimme uitsnijdvertoning kiest met een hoogte-breedteverhouding die het best overeenkomt met de hoogte-breedteverhouding van de oorspronkelijke afbeelding.

* **[!UICONTROL Title]**—Wijzig de titel van de slimme-uitsnijdafbeelding.

* **[!UICONTROL Alt Text]**—Voeg een titel toe aan de slimme-uitsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL URL, Open in]**—U kunt een middel instellen om een koppeling te openen. Stel de URL in en kies Openen in om aan te geven of u deze wilt openen in hetzelfde venster of in een nieuw venster.

   Deze optie is niet beschikbaar als u afbeeldingensets, spin-sets of gemengde-mediasets bekijkt.

* **[!UICONTROL Width]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

* **[!UICONTROL Height]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

### Component: Interactieve media {#interactive-media-component}

De component Interactieve media is bedoeld voor elementen die interactiviteit hebben op dergelijke hotspots of afbeeldingen met hyperlinks. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de **[!UICONTROL Interactive Media]** component.

De component Interactieve media is slim. Afhankelijk van of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel: de grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Interactieve media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Houd er rekening mee dat het toewijzen van een andere viewervoorinstelling aan elke interactieve mediacomponent op die pagina niet wordt ondersteund.
>
>U kunt echter op de pagina dezelfde viewer-voorinstelling gebruiken voor alle interactieve mediacomponenten die elementen van hetzelfde type gebruiken.

![chlimage_1-174](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL General]**-instellingen bewerken door op **[!UICONTROL Edit]** in de component te tikken.

* **[!UICONTROL Viewer preset]**—Selecteer een bestaande viewer-voorinstelling in het vervolgkeuzemenu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze mogelijk zichtbaar maken. Voorinstellingen van viewer moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Title]**—Wijzig de titel van de video.

* **[!UICONTROL Width]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

* **[!UICONTROL Height]**—Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als je deze waarde leeg laat, wordt het asset adaptief.

   U kunt de volgende **[!UICONTROL Add To Cart]** montages uitgeven door **[!UICONTROL Edit]** in de component te klikken.

* **[!UICONTROL Show Product Asset]**—Deze waarde is standaard geselecteerd. Het productmiddel toont een beeld van het product zoals die in de module van de Handel wordt bepaald. Schakel het vinkje uit om het productelement niet weer te geven.

* **[!UICONTROL Show Product Price]**—Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het product zoals deze is gedefinieerd in de module Handel. Schakel het vinkje uit om de prijs van het product niet weer te geven.

* **[!UICONTROL Show Product Form]**—Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten, zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.

### Component: Panoramische media {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panorama-afbeeldingen zijn. Zulke afbeeldingen bieden een 360°-kijkervaring van een kamer, eigenschap, locatie of landschap. Een afbeelding kan alleen worden beschouwd als een bolvormig panorama als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Getagd met de trefwoorden `equirectangular` of (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de **[!UICONTROL Panoramic Media]** WCM-component.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de **[!UICONTROL Panoramic Media]**-component die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.

>
>
Houd er rekening mee dat het toewijzen van een andere viewervoorinstelling aan elke component **[!UICONTROL Panoramic Media]** op die pagina niet wordt ondersteund.
>
>U kunt echter op de pagina dezelfde viewer-voorinstelling gebruiken voor alle Panorama-mediacomponenten die elementen van hetzelfde type gebruiken.

![panorama-media-viewer-preset](assets/panoramic-media-viewer-preset.png)

U kunt de volgende instelling bewerken door te tikken op **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]**—Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. U moet viewervoorinstellingen publiceren voordat u ze kunt gebruiken. Zie [Viewer-voorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

### Component: Video 360-media {#video-media-component}

Gebruik de component **[!UICONTROL Video 360 Media]** om rechthoekige video op uw webpagina te renderen voor een meeslepende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; afspelen op mobiele apparaten gebruikt doorgaans hun ingebouwde gyroscopische besturingselementen.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360-video met standaardvideo-extensies, zoals .mp4, .mkv en .mov. De meest voorkomende codec is H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

U kunt de volgende instelling bewerken door te tikken op **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]**—Selecteer een bestaande viewer in het vervolgkeuzemenu met voorinstellingen voor viewer. Gebruik Video360VR voor eindgebruikers die een virtuele-reality-bril gebruiken. Bevat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik Video360_social, inclusief standaardbesturingselementen voor het afspelen van video. Video wordt gerenderd in de stereomodus. Handmatig gezichtspunt is uitgeschakeld, maar gyroscopische besturing is ingeschakeld. Er zijn geen functies voor social media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. U moet viewervoorinstellingen publiceren voordat u ze kunt gebruiken. Zie [Viewer-voorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

### HTTP/2 gebruiken om Dynamic Media-elementen {#using-http-to-delivery-dynamic-media-assets} te leveren

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de communicatie tussen browsers en servers verbetert. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-assets kan nu plaatsvinden via HTTP/2, wat betere respons- en laadtijden biedt.

Zie [HTTP2 Levering van Content](/help/assets/dynamic-media/http2faq.md) voor volledige informatie over hoe u aan de slag gaat met HTTP/2 met uw Dynamic Media-account.

>[!MORELIKETHIS]
>
>* [Video Player gebruiken in Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Interactieve video gebruiken met Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [De Asset Viewer begrijpen met Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Aangepaste videominiaturen gebruiken met Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Werken met kleurbeheer met Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Afbeelding verscherpen gebruiken met Experience Manager Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

