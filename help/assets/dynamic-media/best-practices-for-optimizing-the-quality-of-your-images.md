---
title: Aanbevolen procedures voor het optimaliseren van de kwaliteit van uw afbeeldingen
description: Leer de beste praktijken die u helpen de kwaliteit van uw beeldactiva te optimaliseren gebruikend Dynamic Media.
contentOwner: Rick Brough
feature: Asset Management, Best Practices
role: User
exl-id: 2efc4a27-01d7-427f-9701-393497314402
source-git-commit: 6ad46350906c3b8a36a8e361714fa5fffdbf8e82
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 0%

---

# Aanbevolen procedures voor het optimaliseren van de kwaliteit van uw afbeeldingen {#best-practices-for-optimizing-the-quality-of-your-images}

{{work-with-dynamic-media}}

Het optimaliseren van de beeldkwaliteit kan een tijdrovend proces zijn omdat veel factoren bijdragen tot het renderen van acceptabele resultaten. Het resultaat is deels subjectief omdat individuen de beeldkwaliteit anders waarnemen. Gestructureerde experimenten zijn essentieel.

Adobe Experience Manager bevat meer dan 100 Dynamic Media-opdrachten voor het leveren van afbeeldingen voor het instellen en optimaliseren van afbeeldingen en het renderen van resultaten. De volgende richtlijnen kunnen u helpen het proces stroomlijnen en goede resultaten snel bereiken gebruikend sommige essentiële bevelen en beste praktijken.

<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Smart Imaging inschakelen in Dynamic Media {#bp-enable-smart-imaging}

**Slimme beeldvorming:**

* Als u Smart Imaging inschakelt in Dynamic Media, kunt u de afbeeldingsindeling, grootte en kwaliteit automatisch optimaliseren op basis van de mogelijkheden van de clientbrowser.
Meer informatie? Ga naar [ Slimme Beeldvorming ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/imaging-faq).
* Hierdoor worden de prestaties van de afbeeldingslevering verbeterd doordat deze parameters dynamisch worden aangepast.
* U kunt Slimme Beeldvorming evalueren gebruikend het zelfevaluatiehulpmiddel [ Momentopname ](https://snapshot.scene7.com/).

**formaten van het Beeld:**

* Vermijd het gebruik van expliciete `fmt=webp` - of `fmt=avif` -opdrachten in een URL, tenzij dit specifiek is vereist voor een use-case.
* Slimme afbeeldingen selecteren automatisch de beste indeling, waardoor de bandbreedte optimaal wordt.

**Standaardgedrag:**

* Als er geen indelingsopdracht is opgegeven in de URL en Smart Imaging niet is ingeschakeld, wordt Dynamic Media-afbeeldingen standaard geleverd in de JPEG-indeling.

Door geïnformeerde keuzes te maken over afbeeldingsindelingen en Smart Imaging in te schakelen, kunt u de prestaties en gebruikerservaring aanzienlijk beïnvloeden.


<!-- ADDED THE FOLLOWING TOPIC AS PER CQDOC-21594 -->

## Aanbevolen procedures voor het selecteren van de bronafbeelding {#bp-select-source-image}

Essentiële overwegingen bij het werken met bronafbeeldingen:

* **het beeldformaat van Source:**
   * Als u lossless indelingen gebruikt, zoals PNG, TIFF of PSD, blijft de afbeeldingskwaliteit hoog zonder compressiefacten.
   * Met deze indelingen blijven alle oorspronkelijke gegevens behouden, waardoor ze ideaal zijn voor bewerking en verdere verwerking.
* **de beeldgrootte van Source:**
   * Vanaf een afbeelding met een hoge resolutie biedt deze meer details en flexibiliteit.
   * Wanneer afbeeldingen in verschillende formaten moeten worden weergegeven (bijvoorbeeld op verschillende apparaten of schermresoluties), kunt u beter schalen als u een grotere bronafbeelding hebt.
   * Voor afbeeldingen die zoomen ondersteunen (zoals productfoto&#39;s), kunt u de afmetingen ongeveer 2000 pixels of meer meten aan de langste zijde.
   * Logo&#39;s of banners die niet hoeven in te zoomen, kunnen worden geüpload in de grootst mogelijke grootte die nodig is voor het beoogde gebruik.

Door deze zorgvuldige keuzes op bronniveau te maken, kunt u aanzienlijk bijdragen aan de algemene kwaliteit van uw visuele inhoud.

<!-- REMOVED TOPIC AS PER CQDOC-21594
## Best practices for image format (`&fmt=`) {#best-practices-for-image-format-fmt}

* JPG or PNG are the best choices to deliver images in good quality and with manageable size and weight.
* If no format command is supplied in the URL, Dynamic Media Image Delivery defaults to JPG for delivery.
* JPG compresses at a ratio of 10:1 and usually produces smaller image file sizes. PNG compresses at a ratio of about 2:1, except when images contain a white background. Typically though, PNG file sizes are larger than JPG files.
* JPG uses lossy compression, meaning that picture elements (pixels) are dropped during compression. PNG on the other hand uses lossless compression.
* JPG often compresses photographic images with better fidelity than synthetic images with sharp edges and contrast.
* If your images contain transparency, use PNG because JPG does not support transparency.

As a best practice for image format, start with the most common setting `&fmt=JPG`. -->

## Aanbevolen werkwijzen voor afbeeldingsgrootte {#best-practices-for-image-size}

Het dynamisch verkleinen van de afbeeldingsgrootte is een van de meest voorkomende taken. Hierbij moet u de grootte opgeven en eventueel opgeven in welke downsamplingmodus de afbeelding moet worden gedownsampled.

* Voor afbeeldingsgrootten kunt u het beste en het eenvoudigst `&wid=<value>` en `&hei=<value>,` of alleen `&hei=<value>` gebruiken. Met deze parameters wordt de afbeeldingsbreedte automatisch ingesteld op basis van de hoogte-breedteverhouding.
* `&resMode=<value>` controleert het algoritme dat voor downsampling wordt gebruikt. Begin met `&resMode=sharp2` . Deze waarde biedt de beste afbeeldingskwaliteit. Terwijl het gebruiken van het downsampling `value =bilin` sneller is, resulteert het vaak in het aliasing van artefacten.

U kunt het beste `&wid=<value>&hei=<value>&resMode=sharp2` of `&hei=<value>&resMode=sharp2` gebruiken om de afbeeldingsgrootte aan te passen

## Aanbevolen procedures voor verscherpen van afbeeldingen {#best-practices-for-image-sharpening}

Het verscherpen van afbeeldingen is het meest complexe aspect van het beheren van afbeeldingen op uw website en er worden veel fouten gemaakt. Neem de tijd om meer te leren over hoe verscherpen en onscherp maskeren in de Experience Manager werken door naar de volgende nuttige bronnen te verwijzen:

* Het Witboek van beste praktijken [ de Kwaliteit van het Beeld van Adobe Dynamic Media Classic en het Verscherpen Beste praktijken ](/help/assets/dynamic-media/assets/sharpening_images.pdf) is eveneens op Experience Manager van toepassing.

* Controle [ het Beeld van het Gebruik dat met Experience Manager verscherpt - Dynamic Media ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media).

Met Experience Manager kunt u afbeeldingen verscherpen bij inname, bij levering of beide. Meestal is het echter het beste om afbeeldingen te verscherpen met slechts één methode of een andere methode, maar niet met beide. Wanneer u afbeeldingen verscherpt bij levering, op een URL, krijgt u doorgaans de beste resultaten.

Er zijn twee methoden voor het verscherpen van afbeeldingen die u kunt gebruiken:

* Eenvoudig verscherpen ( `&op_sharpen` ) - Net als bij het verscherpingsfilter in Photoshop wordt bij eenvoudige verscherping de standaardverscherping toegepast op de uiteindelijke weergave van de afbeelding na dynamisch vergroten of verkleinen. Deze methode kan echter niet door de gebruiker worden geconfigureerd. De beste manier is om het gebruik van `&op_sharpen` te vermijden, tenzij dit vereist is.
* Onscherp maskeren ( `&op_USM` ) - Onscherp maskeren is een industriestandaard filter voor verscherpen. U kunt afbeeldingen het beste verscherpen met onscherp maskeren volgens de onderstaande richtlijnen. Met Onscherp maskeren kunt u de volgende drie parameters instellen:

   * `&op_sharpen=` bedrag,straal,drempel

      * **[!UICONTROL amount]** (0-5, sterkte van het effect.)
      * **[!UICONTROL radius]** (0-250, breedte van de &#39;verscherpingslijnen&#39; die rond het verscherpte object zijn getekend, zoals gemeten in pixels.)

     Onthoud dat de parameterstraal en de hoeveelheid tegen elkaar werken. Vermindering van de straal kan worden gecompenseerd door het bedrag te verhogen. Met Straal kunt u nauwkeuriger omgaan, aangezien een lagere waarde alleen de randpixels verscherpt, terwijl met een hogere waarde een bredere reeks pixels wordt verscherpt.

      * **[!UICONTROL threshold]** (0-255, gevoeligheid van effect.)

     Deze parameter bepaalt hoe verschillend de verscherpte pixel van het omringende gebied moeten zijn alvorens zij als randpixel worden beschouwd en de filter scherpt hen. Met de parameter **[!UICONTROL threshold]** voorkomt u te veel verscherpende gebieden met vergelijkbare kleuren, zoals huidskleuren. Als u bijvoorbeeld een drempelwaarde van 12 instelt, worden kleine variaties in de helderheid van de huidskleur genegeerd om &#39;ruis&#39; te voorkomen, terwijl randcontrast wordt toegevoegd aan gebieden met hoog contrast, zoals waar de wimpers de huid raken.

     Zie de volgende bronnen voor meer informatie over de manier waarop u deze drie parameters instelt, inclusief aanbevolen procedures voor gebruik met het filter:

      * Het Witboek van beste praktijken [ de Kwaliteit van het Beeld van Adobe Dynamic Media Classic en het Verscherpen Beste praktijken ](/help/assets/dynamic-media/assets/sharpening_images.pdf) is eveneens op Experience Manager van toepassing.

      * Controle [ het Beeld van het Gebruik dat met Experience Manager verscherpt - Dynamic Media ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-image-sharpening-feature-video-use#dynamic-media).

      * Met Experience Manager kunt u ook een vierde parameter instellen: monochroom (0,1). Deze parameter bepaalt of onscherp maskeren wordt toegepast op elke kleurcomponent afzonderlijk met de waarde 0 of op de helderheid/intensiteit van de afbeelding met de waarde 1.

Als beste praktijken, begin met de onscherpe parameter van de maskerstraal. De volgende instellingen voor Straal kunt u gebruiken:

* **[!UICONTROL Website]**: 0,2-0,3 pixels
* **[!UICONTROL Photographic printing (250-300 ppi)]**: 0,3-0,5 pixels
* **[!UICONTROL Offset printing (266-300 ppi)]**: 0,7-1,0 pixels
* **[!UICONTROL Canvas printing (150 ppi)]**: 1,5-2,0 pixels

Verhoog de waarde geleidelijk van 1,75 naar 4. Als de verscherping nog steeds niet de gewenste manier is, vergroot u de straal met een decimaalteken en voer de hoeveelheid nogmaals uit van 1,75 naar 4. Herhaal deze bewerking zo nodig.

Laat de monochrome parameter-instelling op 0 staan.

### Aanbevolen werkwijzen voor JPEF-compressie (`&qlt=`) {#best-practices-for-jpef-compression-qlt}

* Deze parameter bepaalt JPG coderingskwaliteit. Een hogere waarde betekent een afbeelding van hogere kwaliteit, maar een groot bestand. Een lagere waarde betekent een afbeelding van lagere kwaliteit, maar een kleiner bestand. Het bereik voor deze parameter is 0-100.
* Stel de parameterwaarde niet in op 100 om te optimaliseren voor kwaliteit. Het verschil tussen een instelling van 90 of 95 en 100 is bijna onwaarneembaar. En toch wordt met 100 het afbeeldingsbestand onnodig groter. Stel de `qlt= value` daarom in op 90 of 95 om de kwaliteit te optimaliseren, maar te voorkomen dat afbeeldingsbestanden te groot worden.
* Als u wilt optimaliseren voor een kleine bestandsgrootte van de afbeelding, maar de afbeeldingskwaliteit op een acceptabel niveau wilt houden, stelt u de waarde `qlt= value` in op 80. Waarden lager dan 70 tot 75 resulteren in een aanzienlijke verslechtering van de beeldkwaliteit.
* Als beste manier om in het midden te blijven stelt u de `qlt= value` in op 85 om in het midden te blijven.
* De chromamarkering gebruiken in `qlt=`

   * De parameter `qlt=` heeft een tweede instelling waarmee u het downsamplen van RGB-kleuren kunt inschakelen met de waarde `,1` of uitschakelen met de waarde `,0` .
   * Om het eenvoudig te houden, begin met RGB het chromaticiteitdownsampling uitgezet (`,0`). Deze instelling resulteert doorgaans in een betere beeldkwaliteit, vooral bij synthetische afbeeldingen met veel scherpe randen en contrast.

U kunt het beste `&qlt=85,0` gebruiken als JPG compressie.

## Aanbevolen werkwijzen voor JPEG vergroten/verkleinen (`&jpegSize=`) {#best-practices-for-jpeg-sizing-jpegsize}

De parameter `jpegSize` is handig als u wilt garanderen dat een afbeelding een bepaalde grootte niet overschrijdt voor levering aan apparaten met een beperkt geheugen.

* Deze parameter wordt geplaatst in kilobytes (`jpegSize=&lt;size_in_kilobytes&gt;`). Hiermee wordt de maximaal toegestane grootte voor het leveren van de afbeelding gedefinieerd.
* `&jpegSize=` communiceert met de JPG compressieparameter `&qlt=` . Als de JPG reactie met de opgegeven JPG compressieparameter (`&qlt=`) de jpegSize-waarde niet overschrijdt, wordt de afbeelding geretourneerd met `&qlt=` zoals gedefinieerd. Anders wordt `&qlt=` geleidelijk verkleind totdat de afbeelding past in de maximaal toegestane grootte. Of, totdat het systeem bepaalt dat het niet past en een fout retourneert.

U kunt het beste `&jpegSize=` instellen en de parameter `&qlt=` toevoegen als u JPG afbeeldingen afgeeft aan apparaten met beperkt geheugen.

## Overzicht van best practices {#best-practices-summary}

U kunt het beste een hoge afbeeldingskwaliteit en een kleine bestandsgrootte bereiken door de volgende combinatie van parameters te gebruiken:

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Deze combinatie van instellingen levert in de meeste gevallen uitstekende resultaten op.

Als de afbeelding verder moet worden geoptimaliseerd, kunt u de parameters voor verscherpen (onscherp maskeren) geleidelijk perfectioneren door te beginnen met een straal die is ingesteld op 0,2 of 0,3. Vervolgens verhoogt u geleidelijk het bedrag van 1,75 tot maximaal 4 (400% in Photoshop). Controleer of het gewenste resultaat is bereikt.

Als de verscherpingsresultaten nog steeds niet bevredigend zijn, vergroot u de straal in decimale stappen. Voor elke decimale toename start u de hoeveelheid opnieuw op bij 1,75 en verhoogt u deze geleidelijk tot 4. Herhaal dit proces totdat u het gewenste resultaat hebt bereikt. Terwijl de waarden hierboven een benadering zijn die creatieve studio&#39;s hebben bevestigd, herinner me dat u met andere waarden kunt beginnen en andere strategieën kunt volgen. Of de resultaten voor u bevredigend zijn of niet is een subjectieve kwestie, daarom is gestructureerde experimenten van essentieel belang.

Tijdens het experimenteren zijn de volgende algemene suggesties nuttig om uw workflow te optimaliseren:

* Probeer de verschillende parameters in real-time uit en test ze rechtstreeks op een URL.
* U kunt het beste de opdrachten Dynamic Media Image Serving groeperen in een voorinstelling voor afbeeldingen. Een voorinstelling voor een afbeelding bestaat in feite uit URL-opdrachtmacro&#39;s met aangepaste namen voor voorinstellingen, zoals `$thumb_low$` en `&product_high$` . De naam van de aangepaste voorinstelling in een URL-pad roept deze voorinstellingen aan. Met deze functionaliteit kunt u opdrachten en kwaliteitsinstellingen voor verschillende gebruikspatronen van afbeeldingen op uw website beheren en de totale lengte van URL&#39;s verkorten.
* Experience Manager biedt ook geavanceerdere manieren om de afbeeldingskwaliteit af te stemmen, zoals het toepassen van verscherpende afbeeldingen bij opname. Om het teruggeven resultaten te stemmen en te optimaliseren, ](https://business.adobe.com/customers/consulting-services/main.html) kan de raadplegende diensten van de Adobe u met aangepast inzicht en beste praktijken helpen.[
