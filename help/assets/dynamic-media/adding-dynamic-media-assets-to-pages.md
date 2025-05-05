---
title: Dynamische media Assets toevoegen aan pagina's
description: Leer hoe u dynamische mediacomponenten aan een pagina in Adobe Experience Manager as a Cloud Service kunt toevoegen.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 2f2fd6cb-8b53-4167-a7e3-453f27549109
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '2999'
ht-degree: 5%

---

# Dynamische media Assets toevoegen aan pagina&#39;s{#adding-dynamic-media-assets-to-pages}

Om de Dynamische functionaliteit van Media aan activa toe te voegen die u op uw websites gebruikt, kunt u de **Dynamische Media** toevoegen, **Interactieve Media**, **Panoramische Media**, of **Video 360 Media** component direct op de pagina. U opent de modus Lay-out en schakelt de componenten Dynamische media in. Vervolgens voegt u deze componenten aan de pagina toe en voegt u elementen aan de component toe. De componenten voor dynamische media zijn slim: ze weten of u een afbeelding of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U voegt dynamische media-elementen rechtstreeks aan de pagina toe als u [!DNL Adobe Experience Manager] als uw WCM gebruikt. Als u een oplossing van derden gebruikt voor uw WCM, moet u uw assets [koppelen](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [insluiten](/help/assets/dynamic-media/embed-code.md). Voor een ontvankelijke derdewebsite, zie [ leverend geoptimaliseerde beelden aan een ontvankelijke plaats ](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>Zorg ervoor dat u elementen publiceert voordat u deze aan de pagina&#39;s in [!DNL Experience Manager] toevoegt. Zie [ het Publiceren van Dynamische Media Assets ](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Een component Dynamische media aan een pagina toevoegen {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van 3D-media, dynamische media, interactieve media, panoramische media, SmartCrop-video of Video 360-mediacomponent aan een pagina is hetzelfde als het toevoegen van een component aan een pagina.

**om een Dynamische component van Media aan een pagina toe te voegen:**

1. Open in [!DNL Experience Manager] de pagina waaraan u de component Dynamische media wilt toevoegen.
1. Selecteer in het linkerdeelvenster het pictogram **[!UICONTROL Components]** en filter vervolgens voor Dynamische media.

   Als er geen lijst met dynamische mediacomponenten beschikbaar is, moet u waarschijnlijk de dynamische mediacomponenten inschakelen die u wilt gebruiken. Zie [ Dynamische componenten van Media ](#enabling-dynamic-media-components) toelaten.

   ![ 6_5_360video_wcmcomponent ](assets/6_5_360video_wcmcomponent.png)

1. Sleep een component **[!UICONTROL Dynamic Media]** en zet deze neer op de gewenste locatie op de pagina.

1. Plaats de aanwijzer rechtstreeks op de component. Wanneer de component door een blauw vakje wordt omringd, selecteer eens om de toolbar van de component te tonen. Selecteer het pictogram **[!UICONTROL Configuration (wrench)]** .

   ![ 6_5_360video_wcmcomponentconfigure ](assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamic Media-component die u op de pagina hebt neergezet, wordt een configuratiedialoogvenster geopend. [ plaats de opties van de component ](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) zonodig.

   In het onderstaande voorbeeld ziet u het dialoogvenster Dynamische media **[!UICONTROL Video 360 Media]** en de opties die beschikbaar zijn in de vervolgkeuzelijst Voorinstelling viewer.

   ![ Video 360 de component van Media ](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De Dynamic Media Video 360 Media-component.

1. Wanneer u klaar bent, selecteert u in de rechterbovenhoek van het dialoogvenster het vinkje om de wijzigingen op te slaan.

### Dynamische mediacomponenten inschakelen {#enabling-dynamic-media-components}

Als er geen dynamische mediacomponenten beschikbaar zijn om aan een pagina toe te voegen, betekent dit waarschijnlijk dat u de componenten moet inschakelen die u wilt gebruiken.

1. Open in [!DNL Experience Manager] de pagina waaraan u de component Dynamische media wilt toevoegen.
1. Selecteer links van de werkbalk naast de pagina het pictogram Pagina-informatie en selecteer vervolgens **[!UICONTROL Edit Template]** in de vervolgkeuzelijst.

   ![ geef-malplaatje uit ](/help/assets/assets-dm/edit-template.png)

1. Selecteer in de vervolgkeuzelijst rechts van de werkbalk boven aan de pagina de optie **[!UICONTROL Structure]** .

   ![ Beleid ](/help/assets/assets-dm/structure-mode.png)

1. Selecteer onder aan de pagina de optie **[!UICONTROL Layout Container]** om de werkbalk van de pagina te openen en selecteer vervolgens het pictogram Beleid.
1. Controleer of op de pagina **[!UICONTROL Layout Container]** onder de kop **[!UICONTROL Properties]** het tabblad **[!UICONTROL Allowed Components]** is geselecteerd.

   ![ Toegestane componenten ](/help/assets/assets-dm/allowed-components.png)

1. Schuif totdat u **[!UICONTROL Dynamic Media]** ziet.
1. Selecteer het pictogram > links van **[!UICONTROL Dynamic Media]** en selecteer vervolgens de dynamische mediacomponenten die u wilt inschakelen.

   ![ Dynamische de componentenlijst van Media ](/help/assets/assets-dm/dm-components-select.png)

1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Layout Container]** het pictogram Gereed (vinkje).

1. Selecteer in de vervolgkeuzelijst rechts van de werkbalk boven aan de pagina de optie **[!UICONTROL Initial Content]** .
1. [ voegt een Dynamische component van Media aan een pagina ](#adding-a-dynamic-media-component-to-a-page) toe zoals gebruikelijk.

## Dynamische mediacomponenten lokaliseren {#localizing-dynamic-media-components}

U kunt dynamische mediacomponenten op twee manieren lokaliseren:

* Open **[!UICONTROL Properties]** en selecteer het tabblad **[!UICONTROL Advanced]** op een webpagina in Sites. Selecteer de gewenste taal voor lokalisatie.

  ![ chlimage_1-172 ](assets/chlimage_1-538.png)

* Selecteer de gewenste pagina of paginagroep in de sitekiezer. Selecteer **[!UICONTROL Properties]** en selecteer de tab **[!UICONTROL Advanced]** . Selecteer de gewenste taal voor lokalisatie.

  >[!NOTE]
  >
  >Niet alle talen die beschikbaar zijn in het menu **[!UICONTROL Language]** , hebben tokens toegewezen.

## Beschikbare dynamische mediacomponenten {#dynamic-media-components}

Dynamische mediacomponenten zijn beschikbaar wanneer u het pictogram **[!UICONTROL Components]** selecteert en vervolgens filtert op **[!UICONTROL Dynamic Media]** .

De dynamische componenten van Media die beschikbaar zijn omvatten het volgende:

* **[!UICONTROL Dynamic Media]** - Wordt gebruikt voor assets zoals afbeeldingen, video, e-catalogi en spinsets.
* **[!UICONTROL Interactive Media]** - Wordt gebruikt voor interactieve elementen, zoals interactieve video, interactieve afbeeldingen of carrouselsets.
* **[!UICONTROL Panoramic Media]** - Wordt gebruikt voor panoramische afbeeldingen of voor VR-afbeeldingselementen voor panoramische afbeeldingen.
* **[!UICONTROL Video 360 Media]** - Gebruik voor 360 video- en 360 VR-video-elementen.

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten beschikbaar worden gemaakt in de sjablooneditor voordat u ze kunt gebruiken. Nadat de componenten in de sjablooneditor beschikbaar zijn gemaakt, kunt u de componenten aan de pagina toevoegen, net als alle andere componenten van [!DNL Experience Manager] .

![ 6_5_dynamicmediawcmcomponents ](assets/6_5_dynamicmediawcmcomponents.png)

### Component: dynamische media {#dynamic-media-component}

De component Dynamische media is slim. U hebt verschillende opties, of u nu een afbeelding of video toevoegt. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer hierop. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component Dynamic Media die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke Dynamic Media-component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Dynamic Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

Wanneer u de component Dynamische media toevoegt en **[!UICONTROL Dynamic Media Settings]** leeg is of wanneer u een element niet correct kunt toevoegen, controleert u het volgende:

* De afbeelding heeft een piramideTIFF-bestand. Afbeeldingen die worden geïmporteerd voordat u Dynamische media inschakelt, hebben geen TIFF-bestand met piramide.

#### Wanneer u met afbeeldingen werkt {#when-working-with-images}

Met de component Dynamische media kunt u dynamische afbeeldingen toevoegen, zoals afbeeldingssets, centrifuges en gemengde mediasets. U kunt inzoomen, uitzoomen en, indien van toepassing, een afbeelding binnen een centrifugeset draaien of een afbeelding van een ander type set selecteren.

U kunt de viewervoorinstelling, afbeeldingsvoorinstelling of afbeeldingsindeling ook rechtstreeks in de component configureren. Als u een afbeelding responsief wilt maken, kunt u de onderbrekingspunten instellen of een responsieve voorinstelling voor de afbeelding toepassen.

U kunt de volgende instellingen voor dynamische media bewerken door het pictogram **[!UICONTROL Edit]** in de component te selecteren en vervolgens **[!UICONTROL Dynamic Media Settings]** .

![ Dynamische het beeld van Media vooraf ingestelde montages ](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Dit is de enige optie die beschikbaar is als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt. De weergegeven viewervoorinstellingen zijn ook slimme voorinstellingen voor relevante viewers.

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van name=value pair met een &amp;-scheidingsteken en laten u viewers wijzigen zoals wordt beschreven in de Viewer Reference Guide. Een voorbeeld van een viewermodifier is `posterimage=img.jpg&caption=text.vtt,1` , die een andere afbeelding instelt voor de videominiatuur en een ondertitelingsbestand aan de video koppelt.

* **[!UICONTROL Image preset]** - Selecteer een bestaande voorinstelling voor een afbeelding in de vervolgkeuzelijst. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie [ Beeld beheren vooraf instelt ](/help/assets/dynamic-media/managing-image-presets.md). U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door meer opdrachten voor afbeeldingen in te voeren. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Breakpoints]** - Als u dit middel op een ontvankelijke plaats gebruikt, moet u de beeldbreekpunten toevoegen. Afbeeldingsonderbrekingspunten moeten worden gescheiden door komma&#39;s (,). Deze optie werkt wanneer er geen hoogte of breedte is gedefinieerd in een voorinstelling voor afbeeldingen.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Optimize for higher resolution devices]** - Selecteer (standaard) het selectievakje om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven als het volgende true is:
   * Onder Type voorinstelling wordt **[!UICONTROL Image Preset]** geselecteerd en wordt **[!UICONTROL RESS_IP]** geselecteerd in de vervolgkeuzelijst **[!UICONTROL Image Preset]** .

  ![ het plaatsen van de de pixelverhouding van het apparaat voor vooraf ingesteld beeld ](/help/assets/dynamic-media/assets/dpr-ress-ip.png)

  Zie ook [ Ongeveer de optimalisering van de apparatenpixelverhouding ](/help/assets/dynamic-media/imaging-faq.md#dpr).

  Alle [!DNL Experience Manager] Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de afbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de afbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met video {#when-working-with-video}

Met de component Dynamische media kunt u dynamische video toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

![ chlimage_1-173 ](assets/chlimage_1-540.png)

U kunt de volgende instellingen voor dynamische media bewerken door **[!UICONTROL Edit]** te selecteren in de component.

>[!NOTE]
>
>Standaard is de videocomponent Dynamic Media adaptief. Als u een vaste grootte wilt maken, stelt u deze in de component in met de tabbladen **[!UICONTROL Width]** en **[!UICONTROL Height]** **[!UICONTROL Advanced]** .

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande voorinstelling voor een videoviewer in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Viewer modifiers]** - Viewer-modifiers hebben de vorm van `name=value` pair met een `&` -scheidingsteken. Hiermee kunt u viewers wijzigen zoals wordt beschreven in de Adobe Viewers Reference Guide. Een voorbeeld van een viewer-modifier is `posterimage=img.jpg&caption=text.vtt,1`

  Met vieweropties kunt u bijvoorbeeld het volgende doen:

   * Koppel een bijschriftdossier met een video: [ titel ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html?lang=nl-NL)
   * Koppel een navigatiedossier met een video: [ navigatie ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html?lang=nl-NL)

     U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

#### Wanneer u werkt met Slim uitsnijden {#when-working-with-smart-crop}

Met de component Dynamische media kunt u SmartCrop-afbeeldingselementen toevoegen aan uw webpagina&#39;s. Wanneer u de component bewerkt, kunt u een vooraf gedefinieerde videoviewer gebruiken om de video op de pagina af te spelen.

Zie [ Slim Uitsnijden van het Gebruik met de Dynamische Media van Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use.html?lang=nl-NL)

Zie ook [ Profielen van het Beeld ](/help/assets/dynamic-media/image-profiles.md).

![ Dynamische slimme het gewassenmontages van Media ](assets/dm-settings-smart-crop.png)

U kunt de volgende instelling voor dynamische media bewerken door **[!UICONTROL Edit]** te selecteren in de component.

>[!NOTE]
>
>Standaard is de afbeeldingscomponent voor dynamische media adaptief. Als u een vaste grootte wilt instellen, stelt u dit in de component op het tabblad **[!UICONTROL Advanced]** met **[!UICONTROL Width]** en **[!UICONTROL Height]** in.

* **[!UICONTROL Image Modifiers]** - U kunt afbeeldingseffecten toepassen door meer opdrachten voor afbeeldingen in te voeren. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de verwijzing Opdracht Beeldserver.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

  U kunt de volgende geavanceerde instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Enable Aspect Ratio match]** - Selecteer deze optie als u wilt dat Dynamic Media een slimme uitsnijdvertoning kiest met een hoogte-breedteverhouding die het best overeenkomt met de hoogte-breedteverhouding van de oorspronkelijke afbeelding.

* **[!UICONTROL Optimize for higher resolution devices]** - Selecteer (standaard) het selectievakje om DPR (Device Pixel Ratio)-optimalisatie toe te staan.

  De optie **[!UICONTROL Optimize for higher resolution devices]** wordt alleen weergegeven als het volgende true is:

   * Onder Type voorinstelling is de optie **[!UICONTROL Smart Crop]** geselecteerd.

  ![ het plaatsen van de de pixelverhouding van het apparaat voor slimme gewas ](/help/assets/dynamic-media/assets/dpr-smartcrop.png)

  Zie ook [ Ongeveer de optimalisering van de apparatenpixelverhouding ](/help/assets/dynamic-media/imaging-faq.md#dpr).

  Alle [!DNL Experience Manager] Dynamic Media Smart Imaging DPR-waarden worden genegeerd.

* **[!UICONTROL Title]** - Wijzig de titel van de slimme-uitsnijdafbeelding.

* **[!UICONTROL Alt Text]** - Voeg een titel toe aan de slimme-uitsnijdafbeelding voor gebruikers die afbeeldingen hebben uitgeschakeld.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL URL, Open in]** - U kunt een element zo instellen dat een koppeling wordt geopend. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

  Deze optie is niet beschikbaar als u afbeeldingssets, centrifuges of gemengde mediasets bekijkt.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

### Component: interactieve media {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen zoals hotspots of beeldkaarten hebben. Gebruik de component **[!UICONTROL Interactive Media]** als u een interactieve afbeelding, interactieve video of carrouselbanner hebt.

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

![ chlimage_1-174 ](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL General]** -instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Viewer preset]** - Selecteer een bestaande viewervoorinstelling in de vervolgkeuzelijst. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Voorinstellingen voor viewers moeten worden gepubliceerd voordat ze kunnen worden gebruikt. Zie Viewer-voorinstellingen beheren.

* **[!UICONTROL Title]** - Wijzig de titel van de video.

* **[!UICONTROL Width]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

* **[!UICONTROL Height]** - Voer een waarde in pixels in als u wilt dat de afbeelding een vaste grootte heeft. Als u deze waarde leeg laat, wordt het element adaptief.

  U kunt de volgende **[!UICONTROL Add To Cart]** -instellingen bewerken door **[!UICONTROL Edit]** te selecteren in de component.

* **[!UICONTROL Show Product Asset]** - Deze waarde is standaard geselecteerd. In het productelement ziet u een afbeelding van het product, zoals gedefinieerd in de Commerce-module. Schakel het vinkje uit om het productelement niet weer te geven.

* **[!UICONTROL Show Product Price]** - Deze waarde is standaard geselecteerd. De prijs van het product is de prijs van het object zoals gedefinieerd in de module Commerce. Schakel het vinkje uit om de productprijs niet weer te geven.

* **[!UICONTROL Show Product Form]** - Deze waarde is standaard niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Schakel het vinkje uit om de productvarianten niet weer te geven.

### Component: panoramische media {#panoramic-media-component}

Panoramische media-component is bedoeld voor die elementen die bolvormige panoramische afbeeldingen zijn. Dergelijke afbeeldingen bieden een kijkervaring van 360° voor een ruimte, eigenschap, locatie of landschap. Een afbeelding kan alleen als bolvormig panorama worden beschouwd als de afbeelding een van de volgende opties of beide heeft:

* Een hoogte-breedteverhouding van 2:1.
* Gelabeld met de trefwoorden `equirectangular` of (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [ Gebruikend Markeringen ](/help/sites-cloud/authoring/sites-console/tags.md).

Zowel de criteria voor hoogte-breedteverhouding als voor trefwoorden zijn van toepassing op panoramische assets voor de pagina met assetdetails en de **[!UICONTROL Panoramic Media]** WCM-component.

>[!NOTE]
>
>Als uw webpagina het volgende heeft:
>
>* Meerdere instanties van de component **[!UICONTROL Panoramic Media]** die op dezelfde pagina worden gebruikt.
>* Elke instantie gebruikt hetzelfde elementtype.
>
>Het toewijzen van een andere viewervoorinstelling aan elke **[!UICONTROL Panoramic Media]** -component op die pagina wordt niet ondersteund.
>
>U kunt echter dezelfde viewervoorinstelling gebruiken voor alle Panoramische Media-componenten die elementen van hetzelfde type gebruiken, op de pagina.

![ Vooraf ingestelde Panoramische media kijker ](assets/panoramic-media-viewer-preset.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component te selecteren.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in de vervolgkeuzelijst met voorinstellingen voor viewer.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publiceer viewervoorinstellingen voordat u deze gebruikt. Zie [ Kijker beheren stelt ](/help/assets/dynamic-media/managing-viewer-presets.md) vooraf in.

### Component: Video 360-media {#video-media-component}

Met de component **[!UICONTROL Video 360 Media]** kunt u rechthoekige video op uw webpagina renderen. Dit zorgt voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap of medische procedure.

Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; bij het afspelen op mobiele apparaten worden doorgaans de ingebouwde gyroscopische besturingselementen gebruikt.

De viewer bevat native ondersteuning voor de levering van 360 video-elementen. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

![ 6_5_360video_wcmcomponent-1 ](assets/6_5_360video_wcmcomponent-1.png)

U kunt de volgende instelling bewerken door **[!UICONTROL Configure]** in de component te selecteren.

* **[!UICONTROL Viewer Preset]** - Selecteer een bestaande viewer in de vervolgkeuzelijst met voorinstellingen voor viewer. Gebruik Video360VR voor eindgebruikers die een virtuele realiteitsbril gebruiken. Bevat basisbesturingselementen voor het afspelen van video en functies voor sociale media. Gebruik Video360_social, die basisbesturingselementen voor het afspelen van video bevat. Video renderen wordt uitgevoerd in de stereomodus. Handmatige zichtpuntcontrole is uitgeschakeld, maar gyroscopische controle is ingeschakeld. Er zijn geen functies voor sociale media.

Als de viewervoorinstelling die u zoekt niet zichtbaar is, controleert u of deze is gepubliceerd. Publiceer viewervoorinstellingen voordat u deze gebruikt. Zie [ Kijker beheren stelt ](/help/assets/dynamic-media/managing-viewer-presets.md) vooraf in.

### HTTP/2 gebruiken om dynamische media-elementen te leveren {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van dynamische media-elementen kan nu plaatsvinden via HTTP/2, wat betere responstijd en laadtijden biedt.

Zie [ HTTP2 Levering van Inhoud ](/help/assets/dynamic-media/http2faq.md) voor volledige details bij het worden begonnen HTTP/2 met uw Dynamische rekening van Media te gebruiken.

>[!MORELIKETHIS]
>
>* [ Gebruik de Videospeler in Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-player-feature-video-use.html?lang=nl-NL)
>* [ Interactieve Video van het Gebruik met de Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-interactive-video-feature-video-use.html?lang=nl-NL)
>* [ Begrijp de Kijker van Activa met de Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/viewers/dynamic-media-viewer-feature-video-understand.html?lang=nl-NL)
>* [ de Videominiatuur van de Douane van het Gebruik met de Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-video-thumbnails-feature-video-use.html?lang=nl-NL)
>* [ Begrijp het Beheer van de Kleur met de Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-color-management-technical-video-setup.html?lang=nl-NL#dynamic-media)
>* [ Beeld van het Gebruik het Verscherpen met de Dynamische Media van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use.html?lang=nl-NL)
