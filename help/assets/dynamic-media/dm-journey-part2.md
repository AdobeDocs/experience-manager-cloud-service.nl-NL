---
title: Reis naar Dynamic Media, Deel II
description: De Dynamic Media Journey bespreekt de basisbeginselen van Dynamic Media, hoe het werkt, wat het voor u kan doen, en welke waarde het aan uw werk en uw klanten brengt.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Image Profiles,Best Practices
role: User, Admin
mini-toc-levels: 4
hide: false
hidefromtoc: false
exl-id: cdca41ad-a2cd-4f68-aaa4-5eec33c30f0b
source-git-commit: 879af9e3168a1ab993eff930355c4bd200879c71
workflow-type: tm+mt
source-wordcount: '2591'
ht-degree: 0%

---

# Dynamic Media Journey: The Basics, Part II  {#dm-journey-part2}

{{work-with-dynamic-media}}

Welkom bij Dynamic Media Journey: The Basics, Part II, waar u het volgende kunt verwachten:

* Anatomie van een Dynamic Media URL en hoe Dynamic Media inhoud levert
* Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen
* Afbeeldingssets, centrifuges en gemengde mediasets

Zie ook [ Reis van Dynamic Media; De Grondbeginselen, Deel I ](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>Voor de beste resultaten raadt Adobe u aan deze Dynamic Media-reis op een desktopcomputer te lezen en weer te geven.

## Anatomie van een Dynamic Media URL en hoe Dynamic Media inhoud levert {#dm-journey-d}

Nadat uw Dynamic Media-elementen zijn geüpload en gepubliceerd, kunt u de gegenereerde URL van een element kopiëren en deze in uw browser plakken om te zien hoe het element er voor een klant uitziet. De volgende gekopieerde URL voor een gecontroleerde afbeelding is gesplitst naar kleur, zodat u deze eenvoudiger kunt lezen en begrijpen.

![ Anatomie van een Dynamic Media URL ](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Anatomie van een Dynamic Media URL._

Het eerste deel van de rode URL verwijst naar het serverdomein zelf. In dit geval wordt Dynamic Media uitgevoerd op een algemeen serverdomein, namelijk `https://s7d1.scene7.com/is/image/` . Het is gemakkelijk om naar een reeks beelden te kunnen kijken en te begrijpen of zij door Dynamic Media enkel door het serverdomein worden gediend. De URL zal redelijk consistent zijn. Er zijn echter sommige Dynamic Media-klanten die zijn overgeschakeld naar een specifiek serverdomein waar dit mogelijk `name-of-your-company.scene7.com` is. Een specifiek serverdomein is vereist voor Smart Imaging.

De accountnaam is het gedeelte in paars. In dit geval wordt het account `jpearldemo` genoemd.

De element-id of naam, `AdobeStock_28563982` , is groen. Bericht dat de activa _geen_ dossieruitbreiding zoals `.png` of `.jpg` heeft. Wanneer elementen in Dynamic Media worden opgenomen, wordt de bestandsextensie verwijderd en wordt een ander type bestand gemaakt: een piramid-TIFF-bestand. Met de piramic-TIFF kan Dynamic Media snel uitvoeringen maken.

En tenslotte, zijn er sommige beeldverwerkingsparameters, `?wid=1000&fmt=jpeg&qlt=85`, die in geel op het eind worden getoond.

Het volledige URL-pad is live. [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85) {target="_blank"}.

Zorg dat uw browservenster nog steeds open is voor de Dynamic Media URL en de gecontroleerde afbeelding. Laten we nader kijken hoe u uitvoeringen van de afbeelding kunt maken door alleen de URL te wijzigen.

### De gecontroleerde afbeelding renderen via de URL

Eerst verwijdert u alleen handmatig de regels voor afbeeldingsverwerking in het URL-pad. Laat de servernaam, accountnaam en de element-id of afbeeldingsnaam ongewijzigd. [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982) {target="_blank"}.

Voeg nu een afbeeldingsverwerkingsparameter toe aan het einde van de URL. Typ `?wid=500` in het veld URL rechts van de naam van de afbeelding en druk op **[!UICONTROL Enter]** . [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500) {target="_blank"}.

U ziet dat er een nieuwe uitvoering van het horloge wordt gegenereerd. Een belangrijke stap voorwaarts om te begrijpen dat u met deze eenvoudige oefening van het wijzigen van de afbeeldingsbreedte de afbeelding volledig dynamisch genereert.

Wijzig nu de breedtewaarde van `500` pixels in `1000` pixels en druk op **[!UICONTROL Enter]** . [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000) {target="_blank}.
Wanneer u op **[!UICONTROL Enter]** drukt, gaat de browser terug naar de Dynamic Media Image Server. Het produceert een gloednieuwe vertoning van het horloge, die op de nieuwe breedtewaarde wordt gebaseerd u enkel inging, dan levert het nieuwe beeld terug aan browser, en caches het.

Dynamic Media beschikt over een groot aantal parameters voor beeldverwerking waarmee u uw afbeeldingselementen op webpagina&#39;s kunt perfectioneren. U kunt [ een lijst van hen hier ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en) zien.

Voeg nu een rotatieparameter toe aan de gecontroleerde afbeelding. En het einde van het URL-pad, direct na `wid=1000` , typt u `&rotate=90` en drukt vervolgens op **[!UICONTROL Enter]** . [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90) {target="_blank"}.

Het horloge wordt nog steeds enigszins schuingetrokken naar links. Wijzig de rotatiewaarde van `90` in `92` en druk op **[!UICONTROL Enter]** . [ probeer het ](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9) {target="_blank"}.

Wanneer u nogmaals op **[!UICONTROL Enter]** drukt, wordt bijna onmiddellijk een nieuwe uitvoering van het horloge gegenereerd. U kunt het soort prestaties zien die u krijgt, die verklaart waarom Dynamic Media meer dan 800.000 beeldverzoeken, _per seconde_, op een bezet weekend, of belangrijke vakantie kan leveren.

Hoewel het mogelijk is de parameters voor afbeeldingsverwerking in een URL per afbeelding te wijzigen, is dit geen efficiënte methode, vooral niet als u tienduizenden afbeeldingen op uw website hebt staan. Een veel betere aanpak is het gebruik van voorinstellingen voor afbeeldingen.

## Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen {#dm-journey-e}

Er zijn meerdere manieren en plaatsen waarop u een afbeelding wilt maken of waarop een afbeelding beschikbaar is. Een Creative gaat gewoonlijk naar Adobe Photoshop en slaat elk van deze verschillende vertoningen op als statische afbeeldingen.

![ Statische beelden ](/help/assets/dynamic-media/assets/dm-static-images.png)
_Goed: statische beelden, manueel creeerde elk._

Stel je nu voor dat de Creative Director naar de beelden kijkt en zegt:

_&quot;Ik wilde echt dit schot zodat de grote hand naar vier richt, en de kleine hand richt bij 1 om de horlogewijzerplaat gemakkelijker te maken te zien.&quot;_

De creatieve zou alle nieuwe statische beelden opnieuw moeten opnemen.

Als u echter verschillende voorinstellingen voor afbeeldingen hebt in Dynamic Media, kunt u deze afbeeldingen op elk gewenst moment gebruiken. Met de voorinstellingen voor afbeeldingen worden standaarden afgedwongen.

![ Primaire dossierbenadering ](/help/assets/dynamic-media/assets/dm-onefile.png)
_Best: één dossier met veelvoudige die vertoningen op de vlucht worden gecreeerd gebruikend beeld vooraf instelt, zoals `Search_Grid` en `Thumbnail`._

| **waarom gebruik beeld vooraf instelt?** | |
|---|---|
| Normen | Met voorinstellingen voor afbeeldingen wordt een standaardbehandeling voor afbeeldingsverwerking toegepast op elke afbeelding waarmee de voorinstelling wordt gemaakt. |
| Wijzigingsbeheer | Als u de afbeeldingsverwerking moet wijzigen, bewerkt u gewoon de parameter van de bestaande voorinstelling. De bijgewerkte definitie wordt automatisch doorgegeven aan alle aanvragen. |

Elke plaats die u een bepaald type beeld nodig hebt, bijvoorbeeld,

* een pagina met productdetails,
* zoekraster,
* miniatuur,
* boodschappenkaart, of
* hoofdafbeelding

U wilt dat de afbeelding met dezelfde parameters wordt geleverd, waar deze ook worden gebruikt.

Laten we even bekijken hoe een voorinstelling voor afbeeldingen in Dynamic Media is gemaakt.

![ Creërend een beeld dat met het Basislusje ](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png) vooraf in wordt gesteld
_Creërend een beeld dat met het Basis lusje vooraf in wordt gesteld._

In het voorbeeld hierboven, kunt u zien dat een nieuw beeld vooraf ingesteld met de naam _Medium_ werd gecreeerd. Dynamic Media gebruikt een voorbeeld, een out-of-box afbeelding - de rugzak - om u te helpen kenmerken van de voorinstelling van de afbeelding zien terwijl u deze maakt.

_Medium_ vooraf ingesteld beeld heeft een breedte van 500 pixel en een hoogte van 800 pixel. In Deel I van deze Reis leest u hoe u elementen in verschillende indelingen kunt leveren. In het keuzemenu **[!UICONTROL Format]** kunt u ervoor kiezen elementen te leveren als JPEG, PNG, TIFF of diverse andere indelingen. U hebt hier flexibiliteit.

Als u het tabblad **[!UICONTROL Advanced]** selecteert, kunt u opties instellen voor de kleurruimte van het element. Afhankelijk van de indeling die u hebt geselecteerd op het tabblad **[!UICONTROL Basic]** - in het bovenstaande voorbeeld is JPEG geselecteerd - kunt u elementen leveren in RGB, Grijswaarden of CMYK. In het keuzemenu **[!UICONTROL Color Profile]** kunt u opgeven hoe u een CMYK-afbeeldingselement wilt leveren dat u wilt afdrukken. Er zijn ook extra parameters die u kunt toepassen voor het verscherpen van afbeeldingen. In dit geval is **[!UICONTROL Unsharp Mask]** toegepast.

![ Creërend een beeld vooraf ingesteld door opties van het Geavanceerde lusje te selecteren ](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_Creërend een beeld vooraf ingesteld door opties van het Geavanceerde lusje te selecteren._

U herinnert zich in [ Anatomie van Dynamic Media URL ](#dm-journey-d) vroeger, dat u over Dynamic Media URL leest en hoe dat wordt gebouwd. In het tekstvak **[!UICONTROL Image Modifier]** kunt u eventueel extra gewenste parameters voor de afbeeldingsverwerking invoeren. De parameters worden opgenomen in de naam van de voorinstelling van de URL wanneer uw afbeeldingen worden geleverd, met behulp van de voorinstelling. In de bovenstaande schermafbeelding is de parameter `bgc=451B15` toegevoegd. Er is dus een donkerbruine achtergrondkleur toegevoegd.

U kunt een voorinstelling voor afbeeldingen zien als een recept voor uw afbeeldingen. Het zal om het even welke beelden leveren die de vooraf ingestelde, constant, elke keer gebruiken; het zal het zelfde zijn. De parameter `&op_brightness=+10` is ook toegevoegd om de helderheid iets te verhogen.

Als u klaar bent, slaat u de voorinstelling op en is deze nu beschikbaar voor alle afbeeldingen die u hebt. In dit geval, wilt u _Medium_ vooraf ingesteld beeld op een beeld van een kom van vloeibare chocolade toepassen.

![ Toepassend het beeld vooraf ingesteld *Medium* om een vertoning van een beeld ](/help/assets/dynamic-media/assets/dm-medium-image-preset.png) te produceren
_Toepassend het beeld vooraf ingestelde Medium om een vertoning van een beeld te produceren._

U kopieert de URL en plakt deze in uw browser om de weergave van de afbeelding te controleren. [ probeer het ](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$) {target="_blank"}.

In uw browser, merk de naam van het beeld vooraf ingesteld _Medium_ in de volledige weg URL op.

U kunt zien wat voor helderheid in de afbeelding wordt weergegeven. Deze kwaliteit is deels te wijten aan de manier waarop de kom chocolade is neergeschoten. Bovendien is het gedeeltelijk omdat u met Dynamic Media grotere afbeeldingen kunt opslaan dan die welke via digitale kanalen worden geleverd.

Als alles er goed uitziet voor uw kom chocolade, plakt u de URL in uw webpagina&#39;s waar u de afbeelding op uw website wilt weergeven.

Als u nogmaals kijkt naar de onderstaande afbeelding, ziet u dat er een `Cart` voorinstelling voor de afbeelding, een `Grid` voorinstelling, een `Large` voorinstelling, een `PDP-page` voorinstelling (Productdetailpagina) en verschillende andere voorinstellingen zijn.

![ Statische en dynamische beeldvoorinstellingen ](/help/assets/dynamic-media/assets/dm-image-presets.png)
_Statische en Dynamische beeldvoorinstellingen. De gecontroleerde afbeelding is gerenderd met de voorinstelling voor de `PDP-page` -afbeelding._

Maar wat als u een beeld op uw website moet veranderen? Stel dat u bijvoorbeeld tests hebt uitgevoerd en hebt vastgesteld dat de afbeelding van 120 x 120 (de voorinstelling voor de afbeelding `Cart` ) niet op de gewenste wijze wordt ontvangen. U moet de afbeelding groter maken door de breedte te verhogen tot 175 pixels en de hoogte te verhogen tot 175 pixels. Traditioneel zou je naar Adobe Photoshop moeten gaan om al die kartonafbeeldingen opnieuw te maken. Maar in Dynamic Media bewerkt u gewoon de voorinstelling van de afbeelding door de waarden voor Breedte en Hoogte bij te werken naar 175 en de voorinstelling op te slaan, zoals in het onderstaande voorbeeld wordt getoond.

![ Bewerkend een vooraf ingesteld beeld ](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_het uitgeven van de Breedte en de Hoogte van `Cart` vooraf ingesteld beeld._

Nadat u uw vooraf ingesteld beeld verandert, en het geheime voorgeheugen verwijdert, worden alle beelden bijgewerkt, en alle URLs die met die vooraf ingesteld worden gebruikt, _niet_ veranderen overal. Dat betekent dat er geen verbroken koppelingen en geen omleidingen van webpagina&#39;s nodig zijn.

## Afbeeldingssets, centrifuges en gemengde-mediasets {#dm-journey-f}

Een van de populairste toepassingen van Dynamic Media is de mogelijkheid voor u om afbeeldingssets, centrifuges en gemengde-mediasets te maken.

Afbeeldingssets bestaan doorgaans uit een reeks afbeeldingselementen die als één entiteit worden gepresenteerd. Deze sets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met afbeeldingssets kunt u andere weergaven van iets weergeven en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken. [ Mening een beeld plaatste genoemd &quot;Lopend&quot;die de kijker van de Flyout ](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running) gebruikt.

Hier in Dynamic Media kun je verschillende beelden zien van loopschoenen. Het is een serie van de productlijn die verkoop en marketing klanten als één enkele presentatie willen bekijken; een reeks van het Beeld.

![ Creërend een beeldreeks ](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_het begin van het creëren van een Reeks van het Beeld._

Als u de afbeeldingsset wilt maken, kiest u **[!UICONTROL Image Set]** in het keuzemenu **[!UICONTROL Create]** . In het menu ziet u ook opties voor het maken van een **[!UICONTROL Mixed Media Set]** , een **[!UICONTROL Spin Set]** en een **[!UICONTROL Carousel Set]** . U maakt deze sets op ongeveer dezelfde manier als een afbeeldingsset.

Een gemengde mediaset kan afbeeldingen, stalensets, centrifuges, video&#39;s en adaptieve videosets bevatten. [ probeer het ](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Een reeks van de Draai simuleert de echte handeling van het draaien van een voorwerp om het te onderzoeken. Met centrifuges kunt u de belangrijkste visuele details vanuit elke hoek bekijken. [ probeer het ](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400) {target="_blank"}.

Het maken van een afbeeldingsset is eenvoudig. U voegt gewoon de afbeeldingselementen toe die u in de set wilt opnemen.

![ Creërend een beeldreeks ](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_De Vastgestelde Redacteur van het Beeld laat u beeldactiva toevoegen en hun verschijning in de reeks opnieuw rangschikken._

U moet de set een naam geven. Kies de naam zorgvuldig omdat u deze later niet kunt bewerken. In het bovenstaande voorbeeld wordt de set `Running` genoemd. Als u klaar bent, slaat u de set op.

Hier is de `Running` -afbeelding ingesteld in Experience Manager Assets.

![ het Lopende beeld dat in Experience Manager Assets, de Mening van de Kaart wordt geplaatst ](/help/assets/dynamic-media/assets/dm-image-set.png)
_het `Running` Beeld dat in Experience Manager Assets, de Mening van de Kaart wordt geplaatst._

Of u een reeks van het Beeld, een Gemengde reeks van Media, een reeks van de Draai, of een andere interactieve media hebt gecreeerd, nadat u de reeks creeert, wilt u zien hoe het verschijnt en voor een klant gedraagt. Dynamic Media heeft vele ingebouwde kijkers die u dat laten doen.

U begint met het selecteren van de samengestelde afbeeldingsset om deze te openen in een voorvertoning, zoals in het volgende voorbeeld wordt getoond.

![ Het Lopende beeld dat in voorproef met de geselecteerde optie van Kijkers wordt geplaatst ](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_het `Running` Beeld dat in voorproef met geselecteerde optie van Kijkers wordt geplaatst._

In het voorbeeld kunt u de actieve schoenstalen selecteren en in- en uitzoomen op de schoenen. Als u een viewer op de set wilt toepassen, selecteert u **[!UICONTROL Viewers]** in het keuzemenu.

![ Het Lopende beeld dat met de kijker wordt geplaatst die van de Flyout op het ](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png) wordt toegepast
_het `Running` Beeld plaatste met de Reclamer die op het wordt toegepast._

In dit geval is de viewer van `Flyout` geselecteerd. Op dit punt kunt u een voorvertoning van de afbeeldingsset weergeven in de viewer. Maar het is beter om het in uw browser te zien, enkel hoe een klant het ziet. U selecteert **[!UICONTROL URL]** linksonder en kopieert de URL en plakt deze in uw browser. [ probeer het ](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout) {target="_blank"}.

Met de enkele URL kunt u de afbeeldingsset en de viewer gebruiken waar u deze nodig hebt op uw website. In het vorige voorbeeld hebt u wellicht gemerkt dat **[!UICONTROL Embed]** rechts van de URL-knop staat. Door **[!UICONTROL Embed]** te selecteren, kunt u de code voor deze beeldreeks/kijker kopiëren, en het toevoegen aan een Web-pagina of een component van Experience Manager Sites.

De Flyout-viewer is een standaardviewer zonder vak waarvan u de eigenschappen kunt bewerken. U kunt ook, net als bij het maken van een voorinstelling voor afbeeldingen, uw eigen aangepaste viewer maken.

Vermeend dat uw verkoop- en marketingteam de Flyout-viewer niet bevalt. Ze houden van de zoomfunctie, maar ze willen dat klanten het zoomeffect direct boven de schoenen zien. In dat geval past u gewoon de InlineZoom-viewer toe op de afbeeldingsset en kopieert en plakt u de URL in uw browser om te zien hoe deze zich gedraagt. [ probeer het ](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom) {target="_blank"}.

Wanneer u de muisaanwijzer over de schoen beweegt, zoomt u in op die afbeelding en ziet u meer details wanneer u de aanwijzer verplaatst. En de reden daarvoor is gewoon de grootte van de afbeelding die aanvankelijk in Dynamic Media werd geüpload.

Als je denkt dat je als consument leeft, of als je je dagelijkse rol vervult, en als je naar verschillende websites gaat, zie je dit soort dingen. Denk na over hoe dat gebeurt en hoe je de kracht van Dynamic Media kunt gebruiken in je eigen werk en op de website van je bedrijf.

U leest alleen over afbeeldingssets en viewers. Laten we naar een paar andere kijkers kijken en ze uitproberen op één manier. Als u de viewer opnieuw wilt instellen, klikt u op de knop **[!UICONTROL Refresh]** in de linkerbenedenhoek.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* `ZoomVertical_dark` -viewer toegepast op een afbeeldingselement. [ probeer het ](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark) {target="_blank"}.
* `Zoom_light` -viewer toegepast op een afbeelding. [ probeer het ](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light) {target="_blank"}.

## Optioneel - Meer informatie

Als u meer wilt weten over wat u zojuist leest, gebruikt u de onderstaande materialen om concepten in detail te verkennen. Anders is de Dynamic Media-reis voltooid!

{{see-also-dm}}

<!--
_Dynamic Media Help topics_

* [How to create image presets](/help/assets/dynamic-media/image-presets.md)
* A list of [image processing parameters](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) that you can use in the Image Modifier field when you create an image preset
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to create Image sets](/help/assets/dynamic-media/image-sets.md)
* [How to create Spin sets](/help/assets/dynamic-media/spin-sets.md)
* [How to create Mixed Media sets](/help/assets/dynamic-media/mixed-media-sets.md) -->

_zelfstudies van Dynamic Media_

* [ Gebruik Dynamic Media met Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [ de inhoudsbibliotheek van Adobe Experience Manager ](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (onderzoek op _Dynamic Media_)

_de kijkers van Dynamic Media_

* [ Levende Demo&#39;s ](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) van elke kijker

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->