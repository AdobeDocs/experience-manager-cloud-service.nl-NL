---
title: Dynamische media-elementen toevoegen aan pagina's
description: Hoe te om de Dynamische componenten van Media aan een pagina in AEM toe te voegen
translation-type: tm+mt
source-git-commit: 8464d5fa5dd1b8a8a2d5ce47321e1062b536408b

---


# Adding Dynamic Media Assets to Pages{#adding-dynamic-media-assets-to-pages}

Om de Dynamische functionaliteit van Media aan activa toe te voegen u op uw websites gebruikt, kunt u de **Dynamische Media**, de **Interactieve Media**, de Media **van** Panoramiek, of de component van Media **van** Video 360 direct op de pagina toevoegen. U doet dit door de wijze van de Lay-out in te gaan en de Dynamische componenten van Media toe te laten. Dan kunt u deze componenten aan de pagina toevoegen en activa toevoegen aan de component. De dynamische componenten van Media zijn slim - zij weten of u een beeld of een video toevoegt en de beschikbare configuratieopties veranderen dienovereenkomstig.

U voegt de Dynamische activa van Media rechtstreeks aan de pagina toe als u AEM als uw WCM gebruikt. Als u een derde voor uw WCM gebruikt, of [verbind](/help/assets/dynamic-media/linking-urls-to-yourwebapplication.md) of [bedt](/help/assets/dynamic-media/embed-code.md) uw activa in. Voor een ontvankelijke derdewebsite, zie het [leveren van geoptimaliseerde beelden aan een ontvankelijke plaats](/help/assets/dynamic-media/responsive-site.md).

>[!NOTE]
>
>U moet activa publiceren alvorens hen aan pagina&#39;s in AEM toe te voegen. See [Publishing Dynamic Media Assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md).

## Het toevoegen van een Dynamische component van Media aan een pagina {#adding-a-dynamic-media-component-to-a-page}

Het toevoegen van een Dynamische Media, Interactieve Media, Media Panorama, of Video 360 de component van Media aan een pagina is het zelfde als toevoegend een component aan om het even welke pagina. De dynamische componenten van Media worden beschreven in de volgende secties.

**Het toevoegen van een Dynamische component van Media aan een pagina**

1. In AEM, open de pagina waar u de Dynamische component van Media wilt toevoegen.
1. In de linkerruit, tik het pictogram van **[!UICONTROL Componenten]** , dan filter voor Dynamische Media.

   Als geen Dynamische componenten van Media beschikbaar zijn, moet u de Dynamische componenten van Media toelaten-of aanzetten. Zie [het Uitgeven Malplaatjes - de Auteurs](/help/sites-cloud/authoring/features/templates.md) van het Malplaatje voor meer informatie.

   ![6_5_360video_wcmcomponent](assets/6_5_360video_wcmcomponent.png)

1. Sleep een **[!UICONTROL Dynamische component van Media]** en laat vallen het in de gewenste plaats op de pagina.

   In het voorbeeld hieronder, wordt de **[!UICONTROL Video 360 component van Media]** gebruikt.

   ![6_5_360video_wcmcomponentdrag](assets/6_5_360video_wcmcomponentdrag.png)

1. Houd de muisaanwijzer rechtstreeks op de component. Wanneer de component door een blauwe doos wordt omringd, tik eens om de toolbar van de component te tonen. Tik op het pictogram **[!UICONTROL Configuratie (moersleutel)]** .

   ![6_5_360video_wcmcomponentconfigure](assets/6_5_360video_wcmcomponentconfigure.png)

1. Afhankelijk van de Dynamische component van Media u op de pagina liet vallen, opent een doos van de configuratiedialoog. [Plaats zonodig de opties](/help/assets/dynamic-media/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) van de component.

   Het voorbeeld toont hieronder de Dynamische de **[!UICONTROL Video 360 de componentendialoogdoos van Media]** en de opties beschikbaar bij de Kijker Vooraf ingestelde drop-down lijst.

   ![Video 360 Mediacomponent](assets/6_5_360video_wcmcomponentviewerpreset.png)

   De dynamische Media Video 360 component van Media.

1. Wanneer u, dichtbij de hoger-juiste hoek van de dialoogdoos wordt gebeëindigd, tik het controleteken om uw veranderingen te bewaren.

## Dynamische mediacomponenten lokaliseren {#localizing-dynamic-media-components}

U kunt de Dynamische componenten van Media op één van twee manieren lokaliseren:

* Binnen een Web-pagina in Plaatsen, open **[!UICONTROL Eigenschappen]** en selecteer de **[!UICONTROL Geavanceerde]** tabel. Selecteer de gewenste taal voor lokalisatie.

   ![chlimage_1-172](assets/chlimage_1-538.png)

* Van de plaatsselecteur, selecteer de gewenste pagina of de paginagroep. Tik op **[!UICONTROL Eigenschappen]** en selecteer het tabblad **[!UICONTROL Geavanceerd]** . Selecteer de gewenste taal voor lokalisatie.

   >[!NOTE]
   >
   >Houd er rekening mee dat niet alle talen die beschikbaar zijn in het menu **[!UICONTROL Taal]** , tokens hebben toegewezen.

## Beschikbare dynamische media componenten {#dynamic-media-components}

De dynamische componenten van Media zijn beschikbaar wanneer u het pictogram van **[!UICONTROL Componenten]** , dan filter op **[!UICONTROL Dynamische Media]** tikt.

De dynamische componenten van Media die beschikbaar zijn omvatten het volgende:

* **[!UICONTROL Dynamische media]** - Gebruik voor dergelijke activa zoals beelden, video, eCatalogs, en spin reeksen.
* **[!UICONTROL Interactieve media]** - Gebruik voor om het even welke interactieve activa zoals interactieve video, interactieve beelden, of carrouselreeksen.
* **[!UICONTROL Panoramische media]** - Gebruik voor panoramisch beeld of panoramische VR beeldactiva.
* **[!UICONTROL Video 360 Media]** - Gebruik voor 360 video en 360 VR videoactiva.

>[!NOTE]
>
>Deze componenten zijn niet beschikbaar door gebrek en moeten als malplaatjeredacteur beschikbaar worden gesteld alvorens te gebruiken. Nadat zij in de malplaatjedacteur ter beschikking worden gesteld, kunt u de componenten aan uw pagina toevoegen aangezien u een andere component AEM.

![6_5_dynamicmediawecomponenten](assets/6_5_dynamicmediawcmcomponents.png)

### Onderdeel: Dynamische media {#dynamic-media-component}

De dynamische component van Media is slim. Afhankelijk van of u een beeld of een video toevoegt, hebt u diverse opties. De component steunt beeld vooraf instelt, op beeld-gebaseerde kijkers zoals beeldreeksen, spin reeksen, gemengde media reeksen, en video. Bovendien is de kijker ontvankelijk-de grootte van het scherm verandert automatisch gebaseerd op het schermgrootte. Alle kijkers zijn de kijkers van HTML5.

>[!NOTE]
>
>Als uw Web-pagina het volgende heeft:
>
>* Veelvoudige instanties van de Dynamische component die van Media op de zelfde pagina worden gebruikt.
>* Elke instantie gebruikt het zelfde activatype.
>
>
Me ervan bewust ben dat het toewijzen van een verschillende vooraf ingestelde kijker aan elke Dynamische component van Media op die pagina niet wordt gesteund.
>
>U kunt, echter, de zelfde vooraf ingestelde kijker voor alle Dynamische componenten van Media gebruiken die activa van het zelfde type, binnen de pagina gebruiken.

Wanneer u de Dynamische component van Media toevoegt, en de **[!UICONTROL Dynamische Montages]** van Media leeg is of u kunt geen activa behoorlijk toevoegen, controleer het volgende:

* Het beeld heeft een piramide tiff dossier. De beelden die vóór dynamische media worden ingevoerd worden toegelaten hebben geen piramid tiff dossier dat.

#### Wanneer u werkt met afbeeldingen {#when-working-with-images}

De dynamische component van Media laat u dynamische beelden, met inbegrip van beeldreeksen, spin reeksen, en gemengde media reeksen toevoegen. U kunt binnen zoemen, zoemen uit, en indien toepasselijk een beeld binnen een spin draaien - reeks of een beeld van een ander type van reeks selecteren.

U kunt de vooraf ingestelde kijker, vooraf ingesteld beeld, of beeldformaat direct in de component ook vormen. Om een beeld ontvankelijk te maken kunt u of de breekpunten plaatsen of een ontvankelijk vooraf ingesteld beeld toepassen.

U kunt de volgende Dynamische Montages van Media uitgeven door het pictogram van **[!UICONTROL Edit]** in de component en toen de **[!UICONTROL Dynamische Montages]** van Media te tikken.

![dm-instellingen - vooraf ingesteld beeld](assets/dm-settings-image-preset.png)

>[!NOTE]
>
>Door gebrek, is de Dynamische het beeldcomponent van Media adaptief. Als u het een vaste grootte wilt maken, plaats het in de component in het **[!UICONTROL Geavanceerde]** lusje met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]**.

* **[!UICONTROL De vooraf ingestelde]**-uitgezochte kijker een bestaande vooraf ingestelde kijker van het drop-down menu. Als de vooraf ingestelde kijker u zoekt niet zichtbaar is, kunt u het zichtbaar moeten maken. Zie Kijker beheren stelt vooraf in. U kunt geen vooraf ingestelde kijker selecteren als u een vooraf ingesteld beeld en vice versa gebruikt.

   Dit is de enige beschikbare optie als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt. De kijker stelt getoond vooraf in is ook slim - slechts de relevante kijker stelt verschijnt vooraf in.

* **[!UICONTROL De de bepalingen]**-Kijker van de kijker bepalingen nemen de vorm van name=value paar met een &amp; afbakening en laten u kijkers veranderen zoals die in de Gids van de Verwijzing van Kijkers worden geschetst. Een voorbeeld van een kijkersbepaling is `posterimage=img.jpg&caption=text.vtt,1` die een verschillend beeld voor de videoduimnagel plaatst en een gesloten titel/ondertiteldossier met de video associeert.

* **[!UICONTROL Afbeelding vooraf ingesteld]**-Selecteer een bestaand vooraf ingesteld beeld in het vervolgkeuzemenu. Als het vooraf ingestelde beeld u zoekt niet zichtbaar is, kunt u het zichtbaar moeten maken. Zie Afbeelding beheren vooraf instelt. U kunt geen vooraf ingestelde kijker selecteren als u een vooraf ingesteld beeld en vice versa gebruikt.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL De bepalingen]**-u van het beeld kunnen beeldgevolgen toepassen door extra beeldbevelen te leveren. Deze worden beschreven in Beeld vooraf instelt en de verwijzing van het Bevel van de Server van het Beeld.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL Breekpunten]**-als u deze activa op een ontvankelijke plaats gebruikt, moet u de beeldbreekpunten toevoegen. De breekpunten van het beeld moeten door komma&#39;s (,) worden gescheiden. Deze optie werkt wanneer er geen hoogte of breedte die in een vooraf ingesteld beeld wordt bepaald is.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door te tikken **[!UICONTROL geef]** in de component uit.

* **[!UICONTROL Titel]**-verander de titel van het beeld.

* **[!UICONTROL Alt tekst]**-voeg een titel aan het beeld voor die gebruikers toe die grafiek hebben uitgezet.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL URL, open in]**-u kunt activa plaatsen om een verbinding te openen. Plaats URL en in Open binnen wijzen erop of u het in het zelfde venster of een nieuw venster wilt openen.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL Breedte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

* **[!UICONTROL Hoogte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.


#### Wanneer u met Video werkt {#when-working-with-video}

Gebruik de Dynamische component van Media om dynamische video aan uw Web-pagina&#39;s toe te voegen. Wanneer u de component uitgeeft kunt u verkiezen om een vooraf bepaalde videokijker te gebruiken die voor het spelen van de video op de pagina wordt vooraf ingesteld.

![chlimage_1-173](assets/chlimage_1-540.png)

U kunt de volgende Dynamische Montages van Media uitgeven door te klikken **[!UICONTROL uitgeeft]** in de component.

>[!NOTE]
>
>Standaard wordt de videocomponent Dynamic Media aangepast. Als u het een vaste grootte wilt maken, plaats het in de component met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]** in het **[!UICONTROL Geavanceerde]** lusje.

* **[!UICONTROL vooraf ingesteld**-Selecteer een bestaande videokijker die van het drop-down menu vooraf in wordt gesteld. Als de vooraf ingestelde kijker u zoekt niet zichtbaar is, kunt u het zichtbaar moeten maken. Zie Kijker beheren stelt vooraf in.

* **[!UICONTROL de bepalingen**-Kijker van de Kijker bepalingen nemen de vorm van name=value paar met a &amp; afbakening en laten u kijkers veranderen zoals die in de Gids van de Verwijzing van de Kijkers van Adobe worden geschetst. Een voorbeeld van een kijkersbepaling is `posterimage=img.jpg&caption=text.vtt,1`

   Met kijkersbepalingen, kunt u bijvoorbeeld, het volgende doen:

   * Associeer een titeldossier met een video: [bijschrift](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-caption.html)
   * Associeer een navigatiedossier met een video: [navigatie](https://docs.adobe.com/content/help/en/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/video/command-reference-url-video/r-html5-video-viewer-url-navigation.html)
   U kunt de volgende Geavanceerde Montages uitgeven door te klikken **[!UICONTROL uitgeeft]** in de component.

* **[!UICONTROL titel**-verander de titel van de video.

* **[!UICONTROL Breedte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

* **[!UICONTROL Hoogte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

#### Wanneer het werken met Slimme Gewas {#when-working-with-smart-crop}

Gebruik de Dynamische component van Media om de Slimme het beeldactiva van het Gewas aan uw Web-pagina&#39;s toe te voegen. Wanneer u de component uitgeeft kunt u verkiezen om een vooraf bepaalde videokijker te gebruiken die voor het spelen van de video op de pagina wordt vooraf ingesteld.

Zie Slimme [uitsnijden met dynamische media van AEM-elementen gebruiken](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/smart-crop-feature-video-use.html)

Zie ook [Afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md).

![dm-settings-smart-gewas](assets/dm-settings-smart-crop.png)

U kunt de volgende Dynamische Plaatsing van Media uitgeven door te klikken **[!UICONTROL uitgeeft]** in de component.

>[!NOTE]
>
>Door gebrek, is de Dynamische het beeldcomponent van Media adaptief. Als u het een vaste grootte wilt maken, plaats het in de component in het **[!UICONTROL Geavanceerde]** lusje met de **[!UICONTROL Breedte]** en de **[!UICONTROL Hoogte]**.

* **[!UICONTROL De bepalingen]**-u van het beeld kunnen beeldgevolgen toepassen door extra beeldbevelen te leveren. Deze worden beschreven in Beeld vooraf instelt en de verwijzing van het Bevel van de Server van het Beeld.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

   U kunt de volgende Geavanceerde Montages uitgeven door te klikken **[!UICONTROL uitgeeft]** in de component.

* **[!UICONTROL Laat de gelijke]**-uitgezochte optie van de Ratie van het Aspect toe deze optie om Dynamische Media te laten een slimme gewassenvertolking met een aspectverhouding plukken die het beste de aspectverhouding van het originele beeld aanpast.

* **[!UICONTROL Titel]**-verander de titel van het Slimme beeld van het Gewas.

* **[!UICONTROL Alt tekst]**-voeg een titel aan het slimme gewassenbeeld voor die gebruikers toe die grafiek hebben uitgezet.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL URL, open in]**-u kunt activa plaatsen om een verbinding te openen. Plaats URL en in Open binnen wijzen erop of u het in het zelfde venster of een nieuw venster wilt openen.

   Deze optie is niet beschikbaar als u beeldreeksen, spin reeksen, of gemengde media reeksen bekijkt.

* **[!UICONTROL Breedte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

* **[!UICONTROL Hoogte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

### Onderdeel: Interactieve media {#interactive-media-component}

De interactieve component van Media is voor die activa die interactiviteit op hen hebben dergelijke hotspots of beeldkaarten. Als u een interactief beeld, interactieve video, of carrouselbanner hebt, gebruik de **[!UICONTROL Interactieve component van Media]** .

De interactieve component van Media is slim. Afhankelijk van of u een beeld of een video toevoegt, hebt u diverse opties. Bovendien is de kijker ontvankelijk-de grootte van het scherm verandert automatisch gebaseerd op het schermgrootte. Alle kijkers zijn de kijkers van HTML5.

>[!NOTE]
>
>Als uw Web-pagina het volgende heeft:
>
>* Veelvoudige instanties van de Interactieve component die van Media op de zelfde pagina wordt gebruikt.
>* Elke instantie gebruikt het zelfde activatype.
>
>
Me ervan bewust ben dat het toewijzen van een verschillende kijker die aan elke Interactieve component van Media op die pagina wordt vooraf in wordt gesteld niet wordt gesteund.
>
>U kunt, echter, de zelfde vooraf ingestelde kijker voor alle Interactieve componenten van Media gebruiken die activa van het zelfde type, binnen de pagina gebruiken.

![chlimage_1-174](assets/chlimage_1-541.png)

U kunt de volgende **[!UICONTROL Algemene]** montages uitgeven door te typen **[!UICONTROL geef]** in de component uit.

* **[!UICONTROL De vooraf ingestelde]**-uitgezochte kijker een bestaande vooraf ingestelde kijker van het drop-down menu. Als de vooraf ingestelde kijker u zoekt niet zichtbaar is, kunt u het zichtbaar moeten maken. De kijker stelt moet worden gepubliceerd alvorens zij kunnen worden gebruikt vooraf in. Zie Kijker beheren stelt vooraf in.

* **[!UICONTROL Titel]**-verander de titel van de video.

* **[!UICONTROL Breedte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

* **[!UICONTROL Hoogte]**-ga waarde in pixel in als u het beeld een vaste grootte wilt zijn. Als u deze waarde leeg laat, wordt de waarde aangepast.

   U kunt het volgende uitgeven **[!UICONTROL toevoegt aan de montages van de Kar]** door te klikken **[!UICONTROL geef]** in de component uit.

* **[!UICONTROL Productelement]** weergeven—Standaard is deze waarde geselecteerd. De productactiva tonen een beeld van het product zoals die in de module van de Handel wordt bepaald. Ontruim het vinkje om niet de productactiva te tonen.

* **[!UICONTROL Toon de prijs]**-door gebrek van het Product, wordt deze waarde geselecteerd. De productprijs geeft de prijs van het object weer zoals gedefinieerd in de module Handel. Schakel het vinkje uit om de productprijs niet weer te geven.

* **[!UICONTROL Toon vorm]**-door gebrek van het Product, wordt deze waarde niet geselecteerd. Het productformulier bevat alle productvarianten zoals grootte en kleur. Ontruim het vinkje om de productvarianten niet te tonen.

### Onderdeel: Panoramische media {#panoramic-media-component}

De component van de Media van Panoramiek is voor die activa die sferische panoramische beelden zijn. Dergelijke beelden verstrekken een 360° het bekijken ervaring van een ruimte, een bezit, een plaats, of een landschap. Een beeld om als bolvormig panorama te kwalificeren, moet het of één OF allebei van het volgende hebben:

* Een hoogte-breedteverhouding van 2:1.
* Tagged met de sleutelwoorden `equirectangular` (`spherical` + `panorama`) of (`spherical` + `panoramic`). Zie [Labels](/help/sites-cloud/authoring/features/tags.md)gebruiken.

Zowel zijn de aspectverhouding als sleutelwoordcriteria op panoramische activa voor de pagina van activadetails en de **[!UICONTROL component van Media]** van Panorama WCM van toepassing.

>[!NOTE]
>
>Als uw Web-pagina het volgende heeft:
>
>* Veelvoudige instanties van de **[!UICONTROL component van Media]** Panorama die op de zelfde pagina worden gebruikt.
>* Elke instantie gebruikt het zelfde activatype.
>
>
Me ervan bewust ben dat het toewijzen van een verschillende kijker die aan elke component van Media **** Panorama op die pagina wordt vooraf in wordt gesteld niet wordt gesteund.
>
>U kunt, echter, de zelfde vooraf ingestelde kijker voor alle componenten gebruiken van Media Panorama die activa van het zelfde type, binnen de pagina gebruiken.

![panoramisch-media-vooraf ingesteld-kijker](assets/panoramic-media-viewer-preset.png)

U kunt het volgende plaatsen uitgeven door te tikken **[!UICONTROL vormt]** in de component.

* **[!UICONTROL De kijker stelt]**-selecteert een bestaande kijker van het vooraf ingestelde drop-down menu van de Kijker vooraf in.

Als de vooraf ingestelde kijker u zoekt niet zichtbaar is, controleer om ervoor te zorgen dat het wordt gepubliceerd. U moet kijker publiceren stelt vooraf in alvorens u hen kunt gebruiken. Zie [het Leiden Kijker vooraf instelt](/help/assets/dynamic-media/managing-viewer-presets.md).

### Onderdeel: Video 360-media {#video-media-component}

Gebruik de **[!UICONTROL Video 360 component van Media]** om onrechthoekige video op uw Web-pagina voor een overweldigende het bekijken ervaring van een ruimte, een bezit, een plaats, een landschap, of een medische procedure terug te geven.

Tijdens het afspelen op een vlakke display heeft de gebruiker de controle over de kijkhoek; playback op mobiele apparaten hefboomwerking gewoonlijk hun ingebouwde gyroscopische controles.

De kijker omvat inheemse steun voor de levering van 360 videoactiva. Door gebrek, is geen extra configuratie noodzakelijk voor het bekijken of playback. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De gemeenschappelijkste codec is H.264.

![6_5_360video_wcmcomponent-1](assets/6_5_360video_wcmcomponent-1.png)

U kunt het volgende plaatsen uitgeven door te tikken **[!UICONTROL vormt]** in de component.

* **[!UICONTROL De kijker stelt]**-selecteert een bestaande kijker van het vooraf ingestelde drop-down menu van de Kijker vooraf in. Gebruik Video360VR voor eindgebruikers die een bril voor virtuele realiteit gebruiken. Inclusief elementaire functies voor het afspelen van video&#39;s en functies voor sociale media. Gebruik Video360_social die basiscontroles van de videoplayback omvat. Het video teruggeven wordt gedaan op stereomodus. De handbediening van het gezichtspunt is uit maar de gyroscopische controle is aan. Er zijn geen sociale mediafuncties.

Als de vooraf ingestelde kijker u zoekt niet zichtbaar is, controleer om ervoor te zorgen dat het wordt gepubliceerd. U moet kijker publiceren stelt vooraf in alvorens u hen kunt gebruiken. Zie [het Leiden Kijker vooraf instelt](/help/assets/dynamic-media/managing-viewer-presets.md).

### Het gebruiken van HTTP/2 aan levering de Dynamische activa van Media {#using-http-to-delivery-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte Webprotocol dat de manier verbetert browsers en de servers communiceren. Het verstrekt snellere overdracht van informatie en vermindert de hoeveelheid verwerkingsmacht die nodig is. De levering van de Dynamische activa van Media kan nu over HTTP/2 zijn die betere reactie en ladingstijden verstrekt.

Zie [HTTP2 Levering van Inhoud](/help/assets/dynamic-media/http2faq.md) voor volledige details bij het worden begonnen HTTP/2 met uw Dynamische rekening van Media te gebruiken.

>[!MORELIKETHIS]
>
>* [Het gebruiken van de VideoSpeler in Dynamische Media AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-player-feature-video-use.html)
>* [Interactieve video gebruiken met AEM Dynamic Media](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-interactive-video-feature-video-use.html)
>* [Het begrip van de Kijker van Activa met Dynamische Media AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-viewer-feature-video-understand.html)
>* [Het gebruiken van de Duimnagel van de Video van de Douane met Dynamische Media AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-video-thumbnails-feature-video-use.html)
>* [Het begrip van Kleurbeheer met Dynamische Media AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-color-management-technical-video-setup.html)
>* [Het gebruiken van Beeld die met Dynamische Media AEM scherpt](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/dynamic-media/dynamic-media-image-sharpening-feature-video-use.html)

