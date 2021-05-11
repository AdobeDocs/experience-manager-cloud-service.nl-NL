---
title: Snelle weergaven gebruiken om aangepaste pop-ups te maken
description: '"Leer over hoe de standaard Snelle mening in ecommerce ervaringen wordt gebruikt waarbij een pop-up venster met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren om weer te geven in de pop-upversie van Windows®."'
feature: Interactieve afbeeldingen, interactieve video's, carrouselbanners
role: Administrator,Business Practitioner
exl-id: c2bc6ec8-d46e-4681-ac3e-3337b9e6ae5c
translation-type: tm+mt
source-git-commit: 78d85d31e03d8190c086a870f2fc2ff1cb00a320
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 0%

---

# Met Snelle weergaven aangepaste pop-upvensters® {#using-quickviews-to-create-custom-pop-ups} maken

De standaard Snelle mening wordt gebruikt in e-commerceervaringen waarbij pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt echter aangepaste inhoud activeren om weer te geven in de pop-ups. Afhankelijk van de viewer die u gebruikt, kunnen klanten op een hotspot, een miniatuurafbeelding of een afbeelding met hyperlinks tikken om informatie of verwante inhoud weer te geven.

Snelle weergaven worden ondersteund door de volgende viewers in Dynamic Media:

* Interactieve afbeeldingen (klikbare hotspots)
* Interactieve video (aanklikbare miniatuurafbeeldingen tijdens het afspelen van video)
* Carrouselbanners (aanklikbare hotspots of afbeeldingen met hyperlinks)

Hoewel de functionaliteit van elke viewer verschilt, is het proces voor het maken van een Snelle weergave hetzelfde voor alle drie ondersteunde viewers.

**Met Snelle weergaven kunt u een aangepaste pop-upversie van Windows® maken:**

1. Maak een Snelle weergave voor een geüpload element.

   Meestal maakt u een Snelle weergave op het moment dat u een element bewerkt voor gebruik met de viewer die u gebruikt.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer die u gebruikt</strong></td>
    <td><strong>Voer de volgende stappen uit om de Snelle weergave te maken</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeeldingen</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank">Hotspots toevoegen aan een afbeeldingsbanner</a>.</td>
    </tr>
    <tr>
    <td>Interactieve video's</td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#adding-interactivity-to-your-video" target="_blank">Interactiviteit toevoegen aan uw video</a>.</td>
    </tr>
    <tr>
    <td>Carousel-banners</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank">Hotspots of afbeeldingen met hyperlinks toevoegen aan een banner</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Vraag de insluitcode van de viewer aan om de viewer in uw website te integreren.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer die u gebruikt</strong><br /> </td>
    <td><strong>Voer de volgende stappen uit om de viewer te integreren met uw website</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeelding</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Een interactieve afbeelding met uw website</a> integreren.<br /> </td>
    </tr>
    <tr>
    <td>Interactieve video<br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Een interactieve video integreren met uw website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Carousel banner</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Een carrouselbanner toevoegen aan uw websitepagina</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. De viewer die u gebruikt, moet weten hoe de Snelle weergave moet worden gebruikt.

   De viewer gebruikt een handler met de naam `QuickViewActive`.

   ****
Voorbeeld: u gebruikte de volgende voorbeeldcode voor insluiten op uw webpagina voor een interactieve afbeelding:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   De handler wordt in de viewer geladen met `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Met behulp van het voorbeeld voor het insluiten van code hierboven hebt u de volgende code:**

   ```xml
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Meer informatie over de methode `setHandlers()` vindt u in het volgende voorbeeld:

   * Interactieve afbeeldingsviewer - [verzegelingen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * Interactieve videoviewer - [sethandlers](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. Configureer nu de handler `quickViewActivate`.

   De `quickViewActivate` manager controleert de Snelle meningen in de kijker. De handler bevat de lijst met variabelen en functieaanroepen voor gebruik met de Snelle weergave. De insluitcode biedt toewijzingen voor de SKU-variabele die is ingesteld in de Snelle weergave. Het maakt ook een steekproef `loadQuickView` functievraag.

   **Variabele variabelen**
mappingMap voor gebruik in uw Web-pagina aan de waarde SKU en generische variabelen in de Snelle mening:

   `var *variable1*= inData.*quickviewVariable*`

   De verstrekte insluitcode heeft een steekproefafbeelding voor de variabele SKU:

   `var sku=inData.sku`

   Wijs ook andere variabelen in de Snelle weergave toe, zoals in het volgende voorbeeld:

   ```
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Functie**
callDe manager vereist ook een functievraag voor de Snelle mening om te werken. De functie wordt verondersteld om door uw gastheerpagina toegankelijk te zijn. De insluitcode bevat een voorbeeld van een functieaanroep:

   `loadQuickView(sku)`

   De aanroep van de voorbeeldfunctie gaat ervan uit dat de functie `loadQuickView()` bestaat en toegankelijk is.

   Meer informatie over de methode `quickViewActivate` vindt u in het volgende voorbeeld:

   * Interactieve beeldviewer - [Gebeurteniscallbacks](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * Interactieve videoviewer - [Gebeurteniscallbacks](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Interactieve gegevensondersteuning in de interactieve videoviewer - [Interactieve gegevensondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Ga als volgt te werk:

   * Verwijder de commentaarmarkering van de sectie setHandlers van de insluitcode.
   * Wijs eventuele extra variabelen in de Snelle weergave toe.

      * Werk `loadQuickView(sku,*var1*,*var2*)` vraag bij als u meer variabelen toevoegt.
   * Maak een eenvoudige functie `loadQuickView` () op pagina, buiten de viewer.

      Bijvoorbeeld, schrijft het volgende de waarde van SKU aan de browser console:

   ```xml
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Upload een HTML-testpagina naar een webserver en open deze.

      De variabelen in de Snelle weergave worden toegewezen. De functieaanroep is ingesteld. En de browser console schrijft de veranderlijke waarde aan de browser console. Dit doet hij met behulp van de meegeleverde voorbeeldfunctie.



1. U kunt nu een functie gebruiken om een eenvoudige pop-up in de Snelle mening aan te halen. In het volgende voorbeeld wordt een `DIV` voor een pop-up gebruikt.
1. Maak het pop-upvenster op de volgende manier `DIV` op. Voeg desgewenst extra stijlen toe.

   ```xml
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Plaats de pop-up `DIV` in het lichaam van uw HTML- pagina.

   Één van de elementen wordt geplaatst met een identiteitskaart die met waarde SKU wordt bijgewerkt wanneer de gebruiker een Snelle mening aanhaalt. Het voorbeeld bevat ook een eenvoudige knop waarmee u de pop-up weer kunt verbergen nadat deze zichtbaar is geworden.

   ```xml
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Als u de SKU-waarde in het pop-upvenster wilt bijwerken, voegt u een functie toe. Maak het pop-upvenster zichtbaar door de eenvoudige functie te vervangen die in stap 5 is gemaakt:

   ```xml
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Upload een HTML-testpagina naar uw webserver en open deze. De viewer geeft het pop-upvenster `DIV` weer wanneer een gebruiker een Snelle weergave aanroept.
1. **Het aangepaste pop-upvenster weergeven in de modus Volledig scherm**

   Sommige viewers, zoals de Interactieve Video-viewer, ondersteunen weergave op volledig scherm. Als u de pop-up echter gebruikt zoals in de vorige stappen wordt beschreven, wordt deze achter de viewer weergegeven in de modus Volledig scherm.

   Als u het pop-upvenster in de modi Standaard en Volledig scherm wilt weergeven, koppelt u het pop-upvenster aan de viewercontainer. In dit geval, gebruik een tweede managermethode, `initComplete`.

   De handler `initComplete` wordt aangeroepen nadat de viewer is geïnitialiseerd.

   ```xml
   "initComplete":function() { code block }
   ```

   Meer informatie over de methode `init()` vindt u in het volgende voorbeeld:

   * Interactieve afbeeldingsviewer - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * Interactieve videoviewer - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. Gebruik de volgende code om het pop-up-beschreven in de vorige stappen-aan de kijker vast te maken:

   ```xml
   "initComplete":function() {
       var popup = document.getElementById('quickview_div');
       popup.parentNode.removeChild(popup);
       var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
       var inner_container = document.getElementById(sdkContainerId);
       inner_container.appendChild(popup);
   }
   ```

   In de bovenstaande code hebt u het volgende gedaan:

   * Uw aangepaste pop-upvenster geïdentificeerd.
   * Verwijderd uit DOM.
   * De viewercontainer geïdentificeerd.
   * De pop-up is gekoppeld aan de viewercontainer.

1. De gehele setHandlers-code is vergelijkbaar met de volgende code (de interactieve videoviewer is gebruikt):

   ```xml
   s7interactivevideoviewer.setHandlers({
       "quickViewActivate": function(inData) {
           var sku=inData.sku;
           loadQuickView(sku);
   
       },
       "initComplete":function() {
           var popup = document.getElementById('quickview_div'); // get custom quick view container
           popup.parentNode.removeChild(popup); // remove it from current DOM
           var sdkContainerId = s7interactivevideoviewer.getComponent("container").getInnerContainerId();
           var inner_container = document.getElementById(sdkContainerId);
           inner_container.appendChild(popup);
       }
   });
   ```

1. Nadat de handlers worden geladen, initialiseert u de kijker:

   `*viewerInstance.*init()`

   ****
VoorbeeldIn dit voorbeeld wordt de interactieve afbeeldingsviewer gebruikt.

   `s7interactiveimageviewer.init()`

   Nadat u de viewer hebt ingesloten in uw hostpagina, moet u controleren of de viewer-instantie is gemaakt. Zorg er ook voor dat de handlers worden geladen voordat de viewer wordt aangeroepen met `init()`.
