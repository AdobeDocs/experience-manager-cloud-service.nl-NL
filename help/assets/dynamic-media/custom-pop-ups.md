---
title: Aangepaste pop-ups maken met Snelle weergave
description: '"Leer over hoe het gebrek Quickview in e-commerce ervaringen wordt gebruikt waarbij een pop-up venster met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren voor weergave in het pop-upvenster."'
feature: Interactive Images,Interactive Videos,Carousel Banners
role: Admin,User
exl-id: c2bc6ec8-d46e-4681-ac3e-3337b9e6ae5c
source-git-commit: 462ce45d24cf8bcad6963011d2d57d9d7da45550
workflow-type: tm+mt
source-wordcount: '1002'
ht-degree: 0%

---

# Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

The default Quickview is used in ecommerce experiences whereby a pop-up is displayed with product information to drive a purchase. U kunt echter aangepaste inhoud activeren om weer te geven in de pop-ups. Afhankelijk van de viewer die u gebruikt, kunnen klanten een hotspot, een miniatuurafbeelding of een afbeelding met hyperlinks selecteren om informatie of verwante inhoud weer te geven.

Quickview is supported by the following viewers in Dynamic Media:

* Interactive Images (selectable hotspots)
* Interactieve video (selecteerbare miniatuurafbeeldingen tijdens het afspelen van video)
* Carrouselbanners (selecteerbare hotspots of afbeeldingen met hyperlinks)

Hoewel de functionaliteit van elke viewer verschilt, is het proces voor het maken van een QuickView hetzelfde voor alle drie ondersteunde viewers.

**Aangepaste pop-ups maken met Snelle weergave:**

1. Maak een Snelle weergave voor een geüpload element.

   You typically create a Quickview the same time that you edit an asset for use with the viewer you are using.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer you are using</strong></td>
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
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank">Een interactieve afbeelding met uw website integreren</a>.<br /> </td>
    </tr>
    <tr>
    <td>Interactieve video<br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank">Integrating an interactive video with your website</a>.<br /> </td>
    </tr>
    <tr>
    <td>Carousel banner</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank">Adding a carousel banner to your website page</a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. De viewer die u gebruikt, moet weten hoe u de Snelle weergave kunt gebruiken.

   De viewer gebruikt een handler met de naam `QuickViewActive`.

   **Voorbeeld**
Stel dat u de volgende voorbeeldcode voor insluiten op uw webpagina gebruikte voor een interactieve afbeelding:

   ![chlimage_1-291](assets/chlimage_1-291.png)

   The handler is loaded into the viewer using `setHandlers`:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Met behulp van het voorbeeld voor het insluiten van code hierboven hebt u de volgende code:**

   ```xml {.line-numbers}
   s7interactiveimageviewer.setHandlers({
       quickViewActivate": function(inData) {
           var sku=inData.sku;
           var genericVariable1=inData.genericVariable1;
           var genericVariable2=inData.genericVariable2;
          loadQuickView(sku,genericVariable1,genericVariable2);
       }
   })
   ```

   Meer informatie over `setHandlers()` methode op de volgende wijze:

   * Interactieve afbeeldingsviewer - [zeegrepen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * Interactieve videoviewer - [zeegrepen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. Configureer nu de `quickViewActivate` handler.

   De `quickViewActivate` De manager controleert de Snelle mening in de kijker. De manager bevat de veranderlijke lijst en functievraag voor gebruik met de Snelle mening. De ingebedde code verstrekt afbeelding voor de variabele SKU die in de Snelle mening wordt geplaatst. Er wordt ook een monster genomen `loadQuickView` functieaanroep.

   **Variable mapping**
Map variables for use in your web page to the SKU value and generic variables contained in the Quickview:

   `var *variable1*= inData.*quickviewVariable*`

   De verstrekte insluitcode heeft een steekproefafbeelding voor de variabele SKU:

   `var sku=inData.sku`

   Wijs ook andere variabelen van de Snelle mening toe, zoals in het volgende:

   ```xml {.line-numbers}
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **Functieaanroep**
De manager vereist ook een functievraag voor de Snelle mening om te werken. De functie wordt verondersteld om door uw gastheerpagina toegankelijk te zijn. De insluitcode bevat een voorbeeld van een functieaanroep:

   `loadQuickView(sku)`

   De aanroep van de voorbeeldfunctie gaat uit van de functie `loadQuickView()` bestaat en toegankelijk is.

   Meer informatie over `quickViewActivate` methode op de volgende wijze:

   * Interactieve afbeeldingsviewer - [Gebeurteniscallbacks](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * Interactieve videoviewer - [Gebeurteniscallbacks](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Interactieve gegevensondersteuning in de interactieve videoviewer - [Interactieve gegevensondersteuning](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Ga als volgt te werk:

   * Verwijder de commentaarmarkering van de sectie setHandlers van de insluitcode.
   * Wijs om het even welke extra variabelen in de Snelle mening toe.

      * Werk de `loadQuickView(sku,*var1*,*var2*)` Vraag als u meer variabelen toevoegt.
   * Eenvoudig maken `loadQuickView` () op pagina, buiten de viewer.

      Bijvoorbeeld, schrijft het volgende de waarde van SKU aan de browser console:

   ```xml {.line-numbers}
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Upload een HTML-pagina voor de test naar een webserver en open deze.

      De variabelen in de Snelle weergave worden toegewezen. De functieaanroep is ingesteld. En de browser console schrijft de veranderlijke waarde aan de browser console. Dit doet hij met behulp van de meegeleverde voorbeeldfunctie.



1. U kunt nu een functie gebruiken om een eenvoudige pop-up in de Snelle mening aan te halen. In het volgende voorbeeld wordt een `DIV` voor een popup.
1. Style the pop-up `DIV` in the following manner. Voeg desgewenst extra stijlen toe.

   ```xml {.line-numbers}
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Het pop-upvenster plaatsen `DIV` in de hoofdtekst van de pagina HTML.

   One of the elements is set with an ID that is updated with SKU value when the user invokes a Quickview. The example also includes a simple button to hide the pop-up again after it becomes visible.

   ```xml {.line-numbers}
   <div id="quickview_div" >
       <table>
           <tr><td><input id="btnClosePopup" type="button" value="Close"        onclick='document.getElementById("quickview_div").style.display="none"' /><br /></td></tr>
           <tr><td>SKU</td><td><input type="text" id="txtSku" name="txtSku"></td></tr>
       </table>
   </div>
   ```

1. Als u de SKU-waarde in het pop-upvenster wilt bijwerken, voegt u een functie toe. Maak het pop-upvenster zichtbaar door de eenvoudige functie te vervangen die in stap 5 is gemaakt:

   ```xml {.line-numbers}
   <script type="text/javascript">
       function loadQuickView(sku){
           document.getElementById("txtSku").setAttribute("value",sku); // write sku value
           document.getElementById("quickview_div").style.display="block"; // show popup
       }
   </script>
   ```

1. Upload een HTML-pagina voor de test naar uw webserver en open deze. De pop-up wordt weergegeven door de viewer `DIV` wanneer een gebruiker een Snelle mening aanhaalt.
1. **Het aangepaste pop-upvenster weergeven in de modus Volledig scherm**

   Sommige viewers, zoals de Interactieve Video-viewer, ondersteunen weergave op volledig scherm. However, using the pop-up as described in the previous steps causes it to display behind the viewer while in full screen mode.

   Als u het pop-upvenster in de modi Standaard en Volledig scherm wilt weergeven, koppelt u het pop-upvenster aan de viewercontainer. In dit geval gebruikt u een tweede handlermethode, `initComplete`.

   De `initComplete` handler wordt aangeroepen nadat de viewer is geïnitialiseerd.

   ```xml {.line-numbers}
   "initComplete":function() { code block }
   ```

   Meer informatie over `init()` methode op de volgende wijze:

   * Interactieve afbeeldingsviewer - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * Interactieve videoviewer - [init](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

1. Gebruik de volgende code om het pop-up-beschreven in de vorige stappen-aan de kijker vast te maken:

   ```xml {.line-numbers}
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

   ```xml {.line-numbers}
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

   **Voorbeeld**
In dit voorbeeld wordt de interactieve afbeeldingsviewer gebruikt.

   `s7interactiveimageviewer.init()`

   After you embed the viewer into your host page, be sure that the viewer instance is created. Also, ensure that the handlers are loaded before the viewer is invoked using `init()`.
