---
title: Aangepaste pop-ups maken met Snelle weergave
description: Leer over hoe het gebrek Quickview in e-commerce ervaringen wordt gebruikt waarbij een pop-up venster met productinformatie wordt getoond om een aankoop te drijven. U kunt aangepaste inhoud activeren om weer te geven in het pop-upvenster.
contentOwner: Rick Brough
feature: Interactive Images,Interactive Videos,Carousel Banners
role: Admin,User
exl-id: c2bc6ec8-d46e-4681-ac3e-3337b9e6ae5c
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# Aangepaste pop-ups maken met Snelle weergave {#using-quickviews-to-create-custom-pop-ups}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

De standaard Snelle mening wordt gebruikt in e-commerceervaringen waarbij pop-up met productinformatie wordt getoond om een aankoop te drijven. U kunt echter aangepaste inhoud activeren om weer te geven in de pop-ups. Afhankelijk van de viewer die u gebruikt, kunnen klanten een hotspot, een miniatuurafbeelding of een afbeelding met hyperlinks selecteren om informatie of verwante inhoud weer te geven.

QuickView wordt ondersteund door de volgende viewers in Dynamic Media:

* Interactieve afbeeldingen (selecteerbare hotspots)
* Interactieve video (selecteerbare miniatuurafbeeldingen tijdens het afspelen van video)
* Carrouselbanners (selecteerbare hotspots of afbeeldingen met hyperlinks)

Hoewel de functionaliteit van elke viewer verschilt, is het proces voor het maken van een QuickView hetzelfde voor alle drie ondersteunde viewers.

**om douanepop-ups tot stand te brengen gebruikend Snelle mening:**

1. Maak een Snelle weergave voor een geüpload element.

   Normaal gesproken maakt u een QuickView op hetzelfde moment dat u een element bewerkt voor gebruik met de viewer die u gebruikt.

   <table>
    <tbody>
    <tr>
    <td><strong>Viewer die u gebruikt</strong></td>
    <td><strong>Voer de volgende stappen uit om de Snelle weergave te maken</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeeldingen</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#adding-hotspots-to-an-image-banner" target="_blank"> Toevoegend hotspots aan een beeldbanner </a>.</td>
    </tr>
    <tr>
    <td>Interactieve video's</td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#adding-interactivity-to-your-video" target="_blank"> Toevoegend interactiviteit aan uw video </a>.</td>
    </tr>
    <tr>
    <td>Carousel Banners</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-hotspots-or-image-maps-to-an-image-banner" target="_blank"> Toevoegend Hotspots of Kaarten van het Beeld aan een Banner </a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. Vraag de insluitcode van de viewer aan om de viewer in uw website te integreren.

   <table>
    <tbody>
    <tr>
    <td><strong> Kijker u </strong><br /> gebruikt </td>
    <td><strong>Voer de volgende stappen uit om de viewer te integreren met uw website</strong></td>
    </tr>
    <tr>
    <td>Interactieve afbeelding</td>
    <td><a href="/help/assets/dynamic-media/interactive-images.md#integrating-an-interactive-image-with-your-website" target="_blank"> Integrerend een interactief beeld met uw website </a>.<br /> </td>
    </tr>
    <tr>
    <td>Interactieve video <br /> </td>
    <td><a href="/help/assets/dynamic-media/interactive-videos.md#integrating-an-interactive-video-with-your-website" target="_blank"> Integrerend een interactieve video met uw website </a>.<br /> </td>
    </tr>
    <tr>
    <td>Carousel banner</td>
    <td><a href="/help/assets/dynamic-media/carousel-banners.md#adding-a-carousel-banner-to-your-website-page" target="_blank"> Toevoegend een carrouselbanner aan uw website pagina </a>.<br /> </td>
    </tr>
    </tbody>
   </table>

1. De viewer die u gebruikt, moet weten hoe u de Snelle weergave kunt gebruiken.

   De viewer gebruikt een handler met de naam `QuickViewActive` .

   **Voorbeeld**
Stel dat u de volgende voorbeeldcode voor insluiten op uw webpagina gebruikte voor een interactieve afbeelding:

   ![ chlimage_1-291 ](assets/chlimage_1-291.png)

   De handler wordt met `setHandlers` in de viewer geladen:

   `*viewerInstance*.setHandlers({ *handler 1*, *handler 2*}, ...`

   **Gebruikend de steekproef inbedt codevoorbeeld van hierboven, hebt u de volgende code:**

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

   Ga als volgt te werk voor meer informatie over de methode `setHandlers()` :

   * De interactieve kijker van het Beeld - [ zenders ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-sethandlers.html)
   * De interactieve Videokijker - [ zethandlers ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-sethandlers.html)

1. Configureer nu de handler `quickViewActivate` .

   De `quickViewActivate` handler bestuurt de QuickView in de viewer. De manager bevat de veranderlijke lijst en functievraag voor gebruik met de Snelle mening. De ingebedde code verstrekt afbeelding voor de variabele SKU die in de Snelle mening wordt geplaatst. Er wordt ook een voorbeeldfunctie `loadQuickView` aangeroepen.

   **Veranderlijke afbeelding**
Wijs variabelen voor gebruik in uw Web-pagina aan de waarde SKU en generische variabelen in de Snelle mening toe:

   `var *variable1*= inData.*quickviewVariable*`

   De verstrekte insluitcode heeft een steekproefafbeelding voor de variabele SKU:

   `var sku=inData.sku`

   Wijs ook andere variabelen van de Snelle mening toe, zoals in het volgende:

   ```xml {.line-numbers}
   var <i>variable2</i>= inData.<i>quickviewVariable2</i>
    var <i>variable3</i>= inData.<i>quickviewVariable3</i>
   ```

   **de vraag van de Functie**
De manager vereist ook een functievraag voor de Snelle mening om te werken. De functie wordt verondersteld om door uw gastheerpagina toegankelijk te zijn. De insluitcode bevat een voorbeeld van een functieaanroep:

   `loadQuickView(sku)`

   De aanroep van de voorbeeldfunctie gaat ervan uit dat de functie `loadQuickView()` bestaat en toegankelijk is.

   Ga als volgt te werk voor meer informatie over de methode `quickViewActivate` :

   * De interactieve kijker van het Beeld - [ callbacks van de Gebeurtenis ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/c-html5-aem-interactive-image-event-callbacks.html)
   * De interactieve Videokijker - [ callbacks van de Gebeurtenis ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-event-callbacks.html)
   * Interactieve gegevenssteun in Interactieve Videokijker - [ Interactieve gegevenssteun ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/c-html5-aem-int-video-int-data-support.html)

1. Ga als volgt te werk:

   * Verwijder de commentaarmarkering van de sectie setHandlers van de insluitcode.
   * Wijs om het even welke extra variabelen in de Snelle mening toe.

      * Werk de `loadQuickView(sku,*var1*,*var2*)` vraag bij als u meer variabelen toevoegt.

   * Maak een eenvoudige `loadQuickView` () functie op pagina, buiten de viewer.

     Bijvoorbeeld, schrijft het volgende de waarde van SKU aan de browser console:

   ```xml {.line-numbers}
   function loadQuickView(sku){
       console.log ("quickview sku value is " + sku);
   }
   ```

   * Upload een HTML-testpagina naar een webserver en open deze.

     De variabelen in de Snelle weergave worden toegewezen. De functieaanroep is ingesteld. En de browser console schrijft de veranderlijke waarde aan de browser console. Dit doet hij met behulp van de meegeleverde voorbeeldfunctie.

1. U kunt nu een functie gebruiken om een eenvoudige pop-up in de Snelle mening aan te halen. In het volgende voorbeeld wordt een `DIV` voor een pop-up gebruikt.
1. Maak het pop-upmenu `DIV` op de volgende manier op. Voeg desgewenst extra stijlen toe.

   ```xml {.line-numbers}
   <style type="text/css">
       #quickview_div{
           position: absolute;
           z-index: 99999999;
           display: none;
       }
   </style>
   ```

1. Plaats de pop-up `DIV` in de tekst van uw HTML-pagina.

   Één van de elementen wordt geplaatst met een identiteitskaart die met waarde SKU wordt bijgewerkt wanneer de gebruiker een Snelle mening aanhaalt. Het voorbeeld bevat ook een eenvoudige knop waarmee u de pop-up weer kunt verbergen nadat deze zichtbaar is geworden.

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
           document.getElementById("quickview_div").style.display="block"; // show pop-up
       }
   </script>
   ```

1. Upload een HTML-testpagina naar uw webserver en open deze. De viewer geeft het pop-upvenster `DIV` weer wanneer een gebruiker een Snelle weergave aanroept.
1. **hoe te om het douane pop-up venster op volledige het schermwijze** te tonen

   Sommige viewers, zoals de Interactieve Video-viewer, ondersteunen weergave in de modus Volledig scherm. Als u de pop-up echter gebruikt zoals in de vorige stappen wordt beschreven, wordt deze achter de viewer weergegeven in de modus Volledig scherm.

   Als u het pop-upvenster in de modi Standaard en Volledig scherm wilt weergeven, koppelt u het pop-upvenster aan de viewercontainer. In dit geval gebruikt u de tweede handlermethode, `initComplete` .

   De `initComplete` -handler wordt aangeroepen nadat de viewer is geïnitialiseerd.

   ```xml {.line-numbers}
   "initComplete":function() { code block }
   ```

   Ga als volgt te werk voor meer informatie over de methode `init()` :

   * De interactieve kijker van het Beeld - [ init ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-images/jsapi-interactive-image/r-html5-aem-int-image-viewer-javascriptapiref-init.html)
   * De interactieve Videoviewer - [ init ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/library/viewers-for-aem-assets-only/interactive-video/jsapi-interactive-video/r-html5-aem-int-video-javascriptapiref-init.html)

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

   Nadat u de viewer hebt ingesloten in uw hostpagina, moet u controleren of de viewer-instantie is gemaakt. Zorg er ook voor dat de handlers worden geladen voordat de viewer wordt aangeroepen met `init()` .
