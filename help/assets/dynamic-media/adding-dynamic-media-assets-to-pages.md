---
title: Dynamic Media-elementen toevoegen aan pagina's
description: Leer hoe u Dynamic Media-componenten aan een pagina in Adobe Experience Manager as a Cloud Service kunt toevoegen.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 2f2fd6cb-8b53-4167-a7e3-453f27549109
source-git-commit: 74254387de1761f25127180787453e681181d97a
workflow-type: tm+mt
source-wordcount: '3000'
ht-degree: 5%

---

# Dynamic Media-elementen toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Als u de Dynamic Media-functionaliteit wilt toevoegen aan elementen die u op uw websites gebruikt, kunt u de opdracht **Dynamic Media**, **Interactieve media**, **Panoramische media**, of **Video 360-media** rechtstreeks op de pagina. U opent de modus Lay-out en schakelt de Dynamic Media-componenten in. Vervolgens voegt u deze componenten aan de pagina toe en voegt u elementen aan de component toe. De componenten voor dynamische media zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

Als u Dynamic Media-elementen gebruikt, voegt u deze rechtstreeks toe aan de pagina [!DNL Adobe Experience Manager] als uw WCM. Als u een oplossing van derden gebruikt voor uw WCM, moet u uw assets [koppelen](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [insluiten](/help/assets/dynamic-media/embed-code.md). Voor een responsieve website van derden raadpleegt u [geoptimaliseerde afbeeldingen leveren aan een responsieve site](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Zorg ervoor dat u elementen publiceert voordat u deze aan pagina&#39;s toevoegt in [!DNL Experience Manager]. Zie [Dynamic Media-middelen publiceren](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een Dynamic Media-component aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een 3D-mediacomponent, Dynamic Media, Interactieve media, Panoramische media, SmartCrop-video of Video 360-mediacomponent aan een pagina is hetzelfde als het toevoegen van een component aan een pagina.

**Een Dynamic Media-component aan een pagina toevoegen:**

1. In [!DNL Experience Manager], opent u de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Selecteer in het linkerdeelvenster de optie **[!UICONTROL Components]** en filter vervolgens voor Dynamic Media.

   Als er geen lijst met Dynamic Media-componenten beschikbaar is, moet u waarschijnlijk de Dynamic Media-componenten inschakelen die u wilt gebruiken. Zie [Dynamic Media-componenten inschakelen](#enabling-dynamic-media-components).

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Sleep een **[!UICONTROL Dynamic Media]** en zet deze neer op de gewenste locatie op de pagina.

1. Plaats de aanwijzer rechtstreeks op de component. Wanneer de component door een blauw vakje wordt omringd, selecteer eens om de toolbar van de component te tonen. Selecteer de **[!UICONTROL Configuration (wrench)]** pictogram.

   ![6_5_360video_wcmcomponentconfigure](assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [Opties van component instellen](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) indien nodig.

   In het onderstaande voorbeeld ziet u de Dynamic Media **[!UICONTROL Video 360 Media]** en de opties beschikbaar in de vervolgkeuzelijst Voorinstelling viewer.

   ![Video 360-mediacomponent](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Wanneer u klaar bent, selecteert u in de rechterbovenhoek van het dialoogvenster het vinkje om de wijzigingen op te slaan.

### Dynamic Media-componenten inschakelen {#enabling-dynamic-media-components}

Als er geen Dynamic Media-componenten beschikbaar zijn om aan een pagina toe te voegen, betekent dit waarschijnlijk dat u de componenten moet inschakelen die u wilt gebruiken.

1. In [!DNL Experience Manager], opent u de pagina waaraan u de Dynamic Media-component wilt toevoegen.
1. Selecteer links van de werkbalk boven aan de pagina het pictogram Pagina-informatie en selecteer vervolgens **[!UICONTROL Edit Template]** in de vervolgkeuzelijst.

   ![edit-template](/help/assets/assets-dm/edit-template.png)

1. Selecteer in de vervolgkeuzelijst rechts van de werkbalk boven aan de pagina de optie **[!UICONTROL Structure]**.

   ![Beleid](/help/assets/assets-dm/structure-mode.png)

1. Selecteer onder aan de pagina de optie **[!UICONTROL Layout Container]** om zijn toolbar te openen, dan selecteer het pictogram van het Beleid.
1. Op de **[!UICONTROL Layout Container]** pagina, onder de **[!UICONTROL Properties]** , zorgt u ervoor dat **[!UICONTROL Allowed Components]** is geselecteerd.

   ![Toegestane componenten](/help/assets/assets-dm/allowed-components.png)

1. Schuiven totdat u ziet **[!UICONTROL Dynamic Media]**.
1. Selecteer het pictogram > links van **[!UICONTROL Dynamic Media]** Selecteer vervolgens de Dynamic Media-componenten die u wilt inschakelen.

   ![Lijst met Dynamic Media-componenten](/help/assets/assets-dm/dm-components-select.png)

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Layout Container]** selecteert u het pictogram Gereed (vinkje).

1. Selecteer in de vervolgkeuzelijst rechts van de werkbalk boven aan de pagina de optie **[!UICONTROL Initial Content]**.
1. [Een Dynamic Media-component aan een pagina toevoegen](#adding-a-dynamic-media-component-to-a-page) zoals gebruikelijk.

## Dynamic Media-componenten lokaliseren {#localizing-dynamic-media-components}

U kunt Dynamic Media-componenten op twee manieren lokaliseren:

* Open **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]** op een webpagina in Sites. Selecteer de gewenste taal voor lokalisatie.

  ![chlimage_1-172](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de sitekiezer. Selecteren **[!UICONTROL Properties]** en selecteert u de **[!UICONTROL Advanced]** tab. Selecteer de gewenste taal voor lokalisatie.

  >[!NOTE]
  >
  >Niet alle talen die beschikbaar zijn in de **[!UICONTROL Language]** aan het menu zijn tokens toegewezen.

## Beschikbare Dynamic Media-componenten {#dynamic-media-components}

Dynamic Media-componenten zijn beschikbaar wanneer u **[!UICONTROL Components]** pictogram, vervolgens filteren op **[!UICONTROL Dynamic Media]**.

De volgende Dynamic Media-componenten zijn beschikbaar:

* **[!UICONTROL Dynamic Media]** - Wordt gebruikt voor assets zoals afbeeldingen, video, e-catalogi en spinsets.
* **[!UICONTROL Interactive Media]** - Wordt gebruikt voor interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramic Media]** - Gebruik voor panoramische afbeeldingen of panoramische VR-afbeeldingen.
* **[!UICONTROL Video 360 Media]** - Wordt gebruikt voor 360 video- en 360 VR-video-elementen.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten beschikbaar worden gemaakt in de sjablooneditor voordat u ze kunt gebruiken. Nadat ze in de sjablooneditor beschikbaar zijn gemaakt, kunt u de componenten op dezelfde manier aan de pagina toevoegen als andere componenten [!DNL Experience Manager] component.

![6_5_dynamicmediawcmcomponents](assets/6_5_dynamicmediawcmcomponents.png)

### Component: Dynamic Media {#dynamic-media-component}

De Dynamic Media-component is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer hierop. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de Dynamic Media-component die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Dynamic Media-componenten die op de pagina elementen van hetzelfde type gebruiken.

Wanneer u de Dynamic Media-component toevoegt, en **[!UICONTROL Dynamic Media Settings]** is leeg of u kunt een element niet correct toevoegen, controleer het volgende:

* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die worden geïmporteerd voordat u Dynamic Media inschakelt, beschikken niet over een TIFF-bestand met piramide.

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de Dynamic Media-component kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

U kunt de volgende Dynamic Media Settings bewerken door **[!UICONTROL Edit]** in de component en vervolgens **[!UICONTROL Dynamic Media Settings]**.

![Dynamic Media-instellingen voor voorinstellingen voor afbeeldingen](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Dit is de enige optie die beschikbaar is als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn ook slimme voorinstellingen voor relevante viewers.

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals beschreven in de Viewer Reference Guide. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1` Hiermee stelt u een andere afbeelding in voor de videominiatuur en koppelt u een ondertitelingsbestand/ondertitelingsbestand aan de video.

* **[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor de afbeelding in de vervolgkeuzelijst. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [Voorinstellingen afbeelding beheren](/help/assets/dynamic-media/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door meer afbeeldingsopdrachten te geven. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breakpoints]** - Als u dit middel op een ontvankelijke plaats gebruikt, moet u de beeldbreekpunten toevoegen. Afbeeldingsonderbrekingspunten moeten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** in de component.

* **[!UICONTROL Optimize for higher resolution devices]** - Schakel het selectievakje (standaard) in om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De **[!UICONTROL Optimize for higher resolution devices]** Deze optie wordt alleen weergegeven als de volgende waarde true is:
   * Onder Type voorinstelling, **[!UICONTROL Image Preset]** is geselecteerd, en **[!UICONTROL RESS_IP]** is geselecteerd uit het **[!UICONTROL Image Preset]** vervolgkeuzelijst.

  ![instelling voor pixelverhouding van apparaat voor voorinstelling afbeelding](/help/assets/dynamic-media/assets/dpr-ress-ip.png)

  Zie ook [Optimalisatie van apparaatpixelverhoudingen](/help/assets/dynamic-media/imaging-faq.md#dpr).

  Alle [!DNL Experience Manager] Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel aan de afbeelding toe voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Met de Dynamic Media-component kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![chlimage_1-173](assets/chlimage_1-540.png)

U kunt de volgende Dynamic Media-instellingen bewerken door **[!UICONTROL Edit]** in de component.

>[!NOTE]
>
>De Dynamic Media-videocomponent is standaard adaptief. Als u van het een vaste grootte wilt maken, plaats het in de component met **[!UICONTROL Width]** en **[!UICONTROL Height]** in de **[!UICONTROL Advanced]** tab.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Viewer modifiers]** - Viewer-wijzigingstoetsen hebben de vorm van `name=value` paar met een `&` scheidingsteken. Hiermee kunt u viewers wijzigen zoals wordt beschreven in de naslaggids voor Adobe viewers. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1`

  Met vieweropties kunt u bijvoorbeeld het volgende doen:

   * Een bijschriftbestand koppelen aan een video: [bijschrift](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Een navigatiebestand koppelen aan een video: [navigatie](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)

     U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** in de component.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met Slim uitsnijden {#when-working-with-smart-crop}

Met de Dynamic Media-component kunt u SmartCrop-afbeeldingselementen toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

Zie [Slim uitsnijden gebruiken met Experience Manager Assets Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html)

Zie ook [Afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md).

![Instellingen voor slimme uitsnijdingen in Dynamic Media](assets/dm-settings-smart-crop.png)

U kunt de volgende Dynamic Media-instelling bewerken door **[!UICONTROL Edit]** in de component.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door meer afbeeldingsopdrachten te geven. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** in de component.

* **[!UICONTROL Enable Aspect Ratio match]** - Selecteer deze optie als u wilt dat Dynamic Media een slimme uitsnijdvertoning kiest met een hoogte-breedteverhouding die het beste overeenkomt met de hoogte-breedteverhouding van de oorspronkelijke afbeelding.

* **[!UICONTROL Optimize for higher resolution devices]** - Schakel het selectievakje (standaard) in om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De **[!UICONTROL Optimize for higher resolution devices]** Deze optie wordt alleen weergegeven als de volgende waarde true is:

   * Onder Type voorinstelling, **[!UICONTROL Smart Crop]** is geselecteerd.

  ![instelling voor pixelverhouding van apparaat voor slim uitsnijden](/help/assets/dynamic-media/assets/dpr-smartcrop.png)

  Zie ook [Optimalisatie van apparaatpixelverhoudingen](/help/assets/dynamic-media/imaging-faq.md#dpr).

  Alle [!DNL Experience Manager] Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de slimme-uitsnijdafbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de slimme-uitsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

### Component: interactieve media {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Als u een interactieve afbeelding, interactieve video of carrouselbanner hebt, gebruikt u de **[!UICONTROL Interactive Media]** component.

De component Interactieve media is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. Bovendien reageert de viewer snel. De grootte van het scherm wordt automatisch aangepast op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Interactive Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke interactieve mediacomponent op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle interactieve mediacomponenten die op de pagina elementen van hetzelfde type gebruiken.

![chlimage_1-174](assets/chlimage_1-541.png)

U kunt het volgende bewerken **[!UICONTROL General]** instellingen door **[!UICONTROL Edit]** in de component.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

  U kunt het volgende bewerken **[!UICONTROL Add To Cart]** instellingen door **[!UICONTROL Edit]** in de component.

* **[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. Het productelement toont een afbeelding van het product zoals gedefinieerd in de module Handel. Schakel het vinkje uit om het productelement niet weer te geven.

* **[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

* **[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.

### Component: panoramische media {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panoramische afbeeldingen zijn. Dergelijke afbeeldingen bieden een kijkervaring van 360° voor een ruimte, eigenschap, locatie of landschap. Een afbeelding kan alleen als bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Gecodeerd met de trefwoorden `equirectangular` of (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [Tags gebruiken](/help/sites-cloud/authoring/sites-console/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de **[!UICONTROL Panoramic Media]** WCM-component.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de **[!UICONTROL Panoramic Media]** die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Verschillende viewervoorinstellingen toewijzen aan elke **[!UICONTROL Panoramic Media]** wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Panoramische Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

![Voorinstelling panoramische mediasviewer](assets/panoramic-media-viewer-preset.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in de vervolgkeuzelijst met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publiceer viewervoorinstellingen voordat u deze gebruikt. Zie [Viewer-voorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

### Component: Video 360-media {#video-media-component}

Gebruik de **[!UICONTROL Video 360 Media]** voor het weergeven van rechthoekige video op uw webpagina. Dit zorgt voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen gebruikt.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in de vervolgkeuzelijst met voorinstellingen voor viewer. Gebruik Video360VR voor eindgebruikers die een virtuele realiteitsbril gebruiken. Bevat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik Video360_social, die basisbesturingselementen voor het afspelen van video bevat. Video renderen wordt uitgevoerd in de stereomodus. Handmatige zichtpuntcontrole is uitgeschakeld, maar gyroscopische controle is ingeschakeld. Er zijn geen functies voor sociale media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publiceer viewervoorinstellingen voordat u deze gebruikt. Zie [Viewer-voorinstellingen beheren](/help/assets/dynamic-media/managing-viewer-presets.md).

### HTTP/2 gebruiken om Dynamic Media-elementen te leveren {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-middelen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [HTTP2 Levering van inhoud](/help/assets/dynamic-media/http2faq.md) voor volledige informatie over hoe u aan de slag gaat met HTTP/2 met uw Dynamic Media-account.

>[!MORELIKETHIS]
>
>* [De videospeler in Experience Manager Dynamic Media gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-player-feature-video-use.html)
>* [Interactieve video gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-interactive-video-feature-video-use.html)
>* [De Asset Viewer begrijpen met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/viewers/dynamic-media-viewer-feature-video-understand.html)
>* [Aangepaste videominiatuur gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Kleurbeheer begrijpen met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-color-management-technical-video-setup.html#dynamic-media)
>* [Afbeelding verscherpen gebruiken met Experience Manager Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use.html)
