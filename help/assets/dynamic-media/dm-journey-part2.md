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
source-git-commit: 35f31c95e92148ff5f3472f26ea9c40fa5a17947
workflow-type: tm+mt
source-wordcount: '2647'
ht-degree: 0%

---

# Dynamic Media Journey: The Basics, Part II  {#dm-journey-part2}

Welkom bij Dynamic Media Journey: The Basics, Part II, waar u het volgende kunt verwachten:

* Anatomie van een Dynamic Media URL en hoe Dynamic Media inhoud levert
* Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen
* Afbeeldingssets, centrifuges en gemengde mediasets

Zie ook [Dynamic Media Journey; The Basics, Part I](/help/assets/dynamic-media/dm-journey-part1.md).

>[!TIP]
>
>Voor de beste resultaten raadt Adobe u aan deze Dynamic Media-reis op een desktopcomputer te lezen en weer te geven.

## Anatomie van een Dynamic Media URL en hoe Dynamic Media inhoud levert {#dm-journey-d}

Nadat uw Dynamic Media-elementen zijn geüpload en gepubliceerd, kunt u de gegenereerde URL van een element kopiëren en deze in uw browser plakken om te zien hoe het element er voor een klant uitziet. De volgende gekopieerde URL voor een gecontroleerde afbeelding is gesplitst naar kleur, zodat u deze eenvoudiger kunt lezen en begrijpen.

![Anatomie van een Dynamic Media-URL](/help/assets/dynamic-media/assets/dm-colored-url.png)
_Anatomie van een Dynamic Media-URL._

Het eerste deel van de rode URL verwijst naar het serverdomein zelf. In dit geval wordt Dynamic Media uitgevoerd op een algemeen serverdomein, dat `https://s7d1.scene7.com/is/image/`. Het is gemakkelijk om naar een reeks beelden te kunnen kijken en te begrijpen of zij door Dynamic Media enkel door het serverdomein worden gediend. De URL zal redelijk consistent zijn. Er zijn echter sommige Dynamic Media-klanten die zijn overgeschakeld naar een specifiek serverdomein waar dit mogelijk is `name-of-your-company.scene7.com`. Een specifiek serverdomein is vereist voor Smart Imaging.

De accountnaam is het gedeelte in paars. In dit geval wordt de account aangeroepen `jpearldemo`.

De ID of naam van het element `AdobeStock_28563982` is groen. Merk op dat het element _nee_ bestandsextensie zoals `.png` of `.jpg`. Wanneer elementen in Dynamic Media worden opgenomen, wordt de bestandsextensie verwijderd en wordt een ander type bestand gemaakt: een piramid-TIFF-bestand. Met de piramic-TIFF kan Dynamic Media snel uitvoeringen maken.

Tot slot zijn er enkele parameters voor beeldverwerking. `?wid=1000&fmt=jpeg&qlt=85`geel aan het uiteinde.

Het volledige URL-pad is live. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?wid=1000&amp;fmt=jpeg&amp;qlt=85){target="_blank"}.

Zorg dat uw browservenster nog steeds open is voor de Dynamic Media URL en de gecontroleerde afbeelding. Laten we nader kijken hoe u uitvoeringen van de afbeelding kunt maken door alleen de URL te wijzigen.

### De gecontroleerde afbeelding renderen via de URL

Eerst verwijdert u alleen handmatig de regels voor afbeeldingsverwerking in het URL-pad. Laat de servernaam, accountnaam en de element-id of afbeeldingsnaam ongewijzigd. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982){target="_blank"}.

Voeg nu een afbeeldingsverwerkingsparameter toe aan het einde van de URL. Typ rechts van de naam van de afbeelding in het veld URL het volgende. `?wid=500`en vervolgens op **[!UICONTROL Enter]**. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=500){target="_blank"}.

U ziet dat er een nieuwe uitvoering van het horloge wordt gegenereerd. Een belangrijke stap voorwaarts om te begrijpen dat u met deze eenvoudige oefening van het wijzigen van de afbeeldingsbreedte de afbeelding volledig dynamisch genereert.

Wijzig nu de breedte van `500` pixels naar `1000` pixels en druk vervolgens op **[!UICONTROL Enter]**. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000){target="_blank}.
Het moment waarop u drukt **[!UICONTROL Enter]**, gaat browser terug naar de Server van het Beeld van Dynamic Media. Het produceert een gloednieuwe vertoning van het horloge, die op de nieuwe breedtewaarde wordt gebaseerd u enkel inging, dan levert het nieuwe beeld terug aan browser, en caches het.

Dynamic Media beschikt over een groot aantal parameters voor beeldverwerking waarmee u uw afbeeldingselementen op webpagina&#39;s kunt perfectioneren. U kunt [zie hier een lijst](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html?lang=en).

Voeg nu een rotatieparameter toe aan de gecontroleerde afbeelding. En het einde van het URL-pad, onmiddellijk na `wid=1000`, type `&rotate=90`en drukt u vervolgens op **[!UICONTROL Enter]**. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=90){target="_blank"}.

Het horloge wordt nog steeds enigszins schuingetrokken naar links. De rotatiewaarde wijzigen van `90` tot `92`en drukt u vervolgens op **[!UICONTROL Enter]**. [Probeer het](https://s7d1.scene7.com/is/image/jpearldemo/AdobeStock%5F28563982?wid=1000&amp;rotate=9){target="_blank"}.

Nogmaals, het moment waarop u drukt **[!UICONTROL Enter]** Er wordt bijna onmiddellijk een nieuwe uitvoering van het horloge gegenereerd. U kunt zien wat voor prestaties u krijgt, wat verklaart waarom Dynamic Media meer dan 800.000 afbeeldingsverzoeken kan indienen, _per seconde_, op een druk weekend of een grote vakantie.

Hoewel het mogelijk is de parameters voor afbeeldingsverwerking in een URL per afbeelding te wijzigen, is dit geen efficiënte methode, vooral niet als u tienduizenden afbeeldingen op uw website hebt staan. Een veel betere aanpak is het gebruik van voorinstellingen voor afbeeldingen.

## Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen {#dm-journey-e}

Er zijn meerdere manieren en plaatsen waarop u een afbeelding wilt maken of waarop een afbeelding beschikbaar is. Een Creative gaat gewoonlijk naar Adobe Photoshop en slaat elk van deze verschillende vertoningen op als statische afbeeldingen.

![Statische afbeeldingen](/help/assets/dynamic-media/assets/dm-static-images.png)
_Goed: statische afbeeldingen, elk handmatig gemaakt._

Stel je nu voor dat de Creative Director naar de beelden kijkt en zegt:

_&quot;Ik wilde deze opname echt, zodat de grote hand naar de vier wijst, en de kleine hand naar de 1 wijst om de horlogewijzerplaat makkelijker te zien te maken.&quot;_

De creatieve zou alle nieuwe statische beelden opnieuw moeten opnemen.

Als u echter verschillende voorinstellingen voor afbeeldingen hebt in Dynamic Media, kunt u deze afbeeldingen op elk gewenst moment gebruiken. Met de voorinstellingen voor afbeeldingen worden standaarden afgedwongen.

![Primaire bestandenbenadering](/help/assets/dynamic-media/assets/dm-onefile.png)
_Best: één bestand met meerdere uitvoeringen die direct worden gemaakt met behulp van voorinstellingen voor afbeeldingen, zoals `Search_Grid` en `Thumbnail`._

| **Waarom voorinstellingen voor afbeeldingen gebruiken?** | |
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

![Een voorinstelling voor afbeeldingen maken die begint met het tabblad Standaard](/help/assets/dynamic-media/assets/dm-image-preset-basictab.png)
_Een voorinstelling voor afbeeldingen maken die begint met het tabblad Standaard._

In het bovenstaande voorbeeld ziet u dat er een nieuwe voorinstelling voor de afbeelding met de naam is gemaakt _Normaal_. Dynamic Media gebruikt een voorbeeld, een out-of-box afbeelding - de rugzak - om u te helpen kenmerken van de voorinstelling van de afbeelding zien terwijl u deze maakt.

De _Normaal_ de vooraf ingestelde afbeelding heeft een breedte van 500 pixels en een hoogte van 800 pixels. In Deel I van deze Reis leest u hoe u elementen in verschillende indelingen kunt leveren. Van de **[!UICONTROL Format]** keuzemenu, kunt u ervoor kiezen elementen te leveren als JPEG, PNG, TIFF of diverse andere indelingen. U hebt hier flexibiliteit.

De **[!UICONTROL Advanced]** bevat opties voor de kleurruimte van het element. Afhankelijk van de indeling die u hebt geselecteerd in het dialoogvenster **[!UICONTROL Basic]** -tab - in het bovenstaande voorbeeld is JPEG geselecteerd - kunt u elementen leveren in RGB, Grijswaarden of CMYK. Van de **[!UICONTROL Color Profile]** vervolgkeuzemenu, kunt u opgeven hoe u een CMYK-afbeeldingselement wilt leveren dat u wilt afdrukken. Er zijn ook extra parameters die u kunt toepassen voor het verscherpen van afbeeldingen. In dit geval: **[!UICONTROL Unsharp Mask]** is toegepast.

![Een afbeeldingsvoorinstelling maken door opties te selecteren op het tabblad Geavanceerd](/help/assets/dynamic-media/assets/dm-image-preset-advancedtab.png)
_Een voorinstelling voor afbeeldingen maken door opties te selecteren op het tabblad Geavanceerd._

U herinnert zich in [Anatomie van een Dynamic Media-URL](#dm-journey-d) eerder, dat u over Dynamic Media URL leest en hoe dat wordt gebouwd. De **[!UICONTROL Image Modifier]** In dit tekstvak kunt u eventueel extra gewenste parameters voor de afbeeldingsverwerking invoeren. De parameters worden opgenomen in de naam van de voorinstelling van de URL wanneer uw afbeeldingen worden geleverd, met behulp van de voorinstelling. In de bovenstaande schermafbeelding, de parameter `bgc=451B15` is toegevoegd. Er is dus een donkerbruine achtergrondkleur toegevoegd.

U kunt een voorinstelling voor afbeeldingen zien als een recept voor uw afbeeldingen. Het zal om het even welke beelden leveren die de vooraf ingestelde, constant, elke keer gebruiken; het zal het zelfde zijn. De parameter `&op_brightness=+10` is ook toegevoegd om de helderheid iets te verhogen.

Als u klaar bent, slaat u de voorinstelling op en is deze nu beschikbaar voor alle afbeeldingen die u hebt. In dit geval wilt u de opdracht _Normaal_ een voorinstelling voor een afbeelding van een kom met vloeibare chocolade.

![De voorinstelling voor afbeeldingen toepassen *Normaal* om een uitvoering van een afbeelding te genereren](/help/assets/dynamic-media/assets/dm-medium-image-preset.png)
_Door de voorinstelling Medium van de afbeelding toe te passen, genereert u een uitvoering van een afbeelding._

U kopieert de URL en plakt deze in uw browser om de weergave van de afbeelding te controleren. [Probeer het](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_74043302?$Medium$){target="_blank"}.

Let op de naam van de voorinstelling voor de afbeelding in uw browser _Normaal_ in het volledige URL-pad.

U kunt zien wat voor helderheid in de afbeelding wordt weergegeven. Deze kwaliteit is deels te wijten aan de manier waarop de kom chocolade is neergeschoten. Bovendien is het gedeeltelijk omdat u met Dynamic Media grotere afbeeldingen kunt opslaan dan die welke via digitale kanalen worden geleverd.

Als alles er goed uitziet voor uw kom chocolade, plakt u de URL in uw webpagina&#39;s waar u de afbeelding op uw website wilt weergeven.

Als u nogmaals kijkt naar de onderstaande afbeelding, ziet u dat er een `Cart` voorinstelling afbeelding, een `Grid` voorinstelling, `Large` voorinstelling, `PDP-page` (Productdetailpagina) en diverse andere voorinstellingen.

![Statische en dynamische voorinstellingen voor afbeeldingen](/help/assets/dynamic-media/assets/dm-image-presets.png)
_Statische en dynamische voorinstellingen voor afbeeldingen. De gecontroleerde afbeelding is gerenderd met de `PDP-page` voorinstelling afbeelding._

Maar wat als u een beeld op uw website moet veranderen? Stel dat u een aantal tests hebt uitgevoerd en dat de afbeelding van 120 x 120 (de `Cart` (voorinstelling afbeelding) niet ontvangen zoals u dacht. U moet de afbeelding groter maken door de breedte te verhogen tot 175 pixels en de hoogte te verhogen tot 175 pixels. Traditioneel zou je naar Adobe Photoshop moeten gaan om al die kartonafbeeldingen opnieuw te maken. Maar in Dynamic Media bewerkt u gewoon de voorinstelling van de afbeelding door de waarden voor Breedte en Hoogte bij te werken naar 175 en de voorinstelling op te slaan, zoals in het onderstaande voorbeeld wordt getoond.

![Een voorinstelling voor afbeeldingen bewerken](/help/assets/dynamic-media/assets/dm-edit-image-preset.png)
_De breedte en hoogte van het dialoogvenster `Cart` voorinstelling afbeelding._

Nadat u de voorinstelling van de afbeelding hebt gewijzigd en de cache hebt verwijderd, worden alle afbeeldingen bijgewerkt en worden alle URL&#39;s die met die voorinstelling worden gebruikt, ook _niet_ overal wijzigen. Dat betekent dat er geen verbroken koppelingen en geen omleidingen van webpagina&#39;s nodig zijn.

## Afbeeldingssets, centrifuges en gemengde-mediasets {#dm-journey-f}

Een van de populairste toepassingen van Dynamic Media is de mogelijkheid voor u om afbeeldingssets, centrifuges en gemengde-mediasets te maken.

Afbeeldingssets bestaan doorgaans uit een reeks afbeeldingselementen die als één entiteit worden gepresenteerd. Deze sets bieden gebruikers een geïntegreerde weergave, waarbij gebruikers verschillende weergaven van een item kunnen zien door op een miniatuurafbeelding te klikken. Met afbeeldingssets kunt u andere weergaven van iets weergeven en de viewer beschikt over zoomgereedschappen waarmee u afbeeldingen op de juiste wijze kunt bekijken. [Een afbeeldingsset met de naam &quot;Running&quot; weergeven die de Flyout-viewer gebruikt](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running).

Hier in Dynamic Media kun je verschillende beelden zien van loopschoenen. Het is een serie van de productlijn die verkoop en marketing klanten als één enkele presentatie willen bekijken; een reeks van het Beeld.

![Een afbeeldingsset maken](/help/assets/dynamic-media/assets/dm-create-image-set.png)
_Het begin van het maken van een Afbeeldingsset._

Als u de afbeeldingsset wilt maken, kiest u **[!UICONTROL Image Set]** van de **[!UICONTROL Create]** keuzelijst. In het menu ziet u dat er ook opties zijn om een **[!UICONTROL Mixed Media Set]**, **[!UICONTROL Spin Set]** en **[!UICONTROL Carousel Set]**. U maakt deze sets op ongeveer dezelfde manier als een afbeeldingsset.

Een gemengde mediaset kan afbeeldingen, stalensets, centrifuges, video&#39;s en adaptieve videosets bevatten. [Probeer het](https://s7d9.scene7.com/s7viewers/html5/MixedMediaViewer.html?asset=Scene7SharedAssets/Mixed_Media_Set_Sample). Een reeks van de Draai simuleert de echte handeling van het draaien van een voorwerp om het te onderzoeken. Met centrifuges kunt u de belangrijkste visuele details vanuit elke hoek bekijken. [Probeer het](https://s7d9.scene7.com/s7viewers/html5/SpinViewer.html?asset=Scene7SharedAssets/SpinSet_Sample&amp;stagesize=500,400){target="_blank"}.

Het maken van een afbeeldingsset is eenvoudig. U voegt gewoon de afbeeldingselementen toe die u in de set wilt opnemen.

![Een afbeeldingsset maken](/help/assets/dynamic-media/assets/dm-create-image-set-add-assets.png)
_Met de Editor voor het instellen van afbeeldingen kunt u afbeeldingselementen toevoegen en de weergave ervan in de set opnieuw ordenen._

U moet de set een naam geven. Kies de naam zorgvuldig omdat u deze later niet kunt bewerken. In het bovenstaande voorbeeld wordt de set aangeroepen `Running`. Als u klaar bent, slaat u de set op.

En hier is het `Running` Afbeelding ingesteld in Experience Manager Assets.

![De actieve afbeelding is ingesteld in Experience Manager Assets, Kaartweergave](/help/assets/dynamic-media/assets/dm-image-set.png)
_De `Running` Afbeelding ingesteld in Experience Manager Assets, Kaartweergave._

Of u een reeks van het Beeld, een Gemengde reeks van Media, een reeks van de Draai, of een andere interactieve media hebt gecreeerd, nadat u de reeks creeert, wilt u zien hoe het verschijnt en voor een klant gedraagt. Dynamic Media heeft vele ingebouwde kijkers die u dat laten doen.

U begint met het selecteren van de samengestelde afbeeldingsset om deze te openen in een voorvertoning, zoals in het volgende voorbeeld wordt getoond.

![De actieve afbeelding die in de voorvertoning is ingesteld en de optie Viewers is geselecteerd](/help/assets/dynamic-media/assets/dm-image-set-viewer.png)
_De `Running` Afbeelding ingesteld in voorvertoning terwijl de optie Viewers is geselecteerd._

In het voorbeeld kunt u de actieve schoenstalen selecteren en in- en uitzoomen op de schoenen. Als u een viewer wilt toepassen op de set, selecteert u **[!UICONTROL Viewers]** in het keuzemenu.

![De uitvoerafbeelding die is ingesteld met de Flyout-viewer erop is toegepast](/help/assets/dynamic-media/assets/dm-image-set-flyout-viewer.png)
_De `Running` Afbeelding die is ingesteld terwijl de Flyout-viewer erop is toegepast._

In dit geval worden de `Flyout` viewer is geselecteerd. Op dit punt kunt u een voorvertoning van de afbeeldingsset weergeven in de viewer. Maar het is beter om het in uw browser te zien, enkel hoe een klant het ziet. U selecteert **[!UICONTROL URL]** linksonder, kopieert u de URL en plakt u deze in uw browser. [Probeer het](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/Flyout){target="_blank"}.

Met de enkele URL kunt u de afbeeldingsset en de viewer gebruiken waar u deze nodig hebt op uw website. In het vorige voorbeeld hebt u wellicht opgemerkt dat: **[!UICONTROL Embed]** rechts van de URL-knop. Door **[!UICONTROL Embed]** kunt u de code voor deze afbeeldingsset/viewer kopiëren en toevoegen aan een webpagina of een Experience Manager Sites-component.

De Flyout-viewer is een standaardviewer zonder vak waarvan u de eigenschappen kunt bewerken. U kunt ook, net als bij het maken van een voorinstelling voor afbeeldingen, uw eigen aangepaste viewer maken.

Vermeend dat uw verkoop- en marketingteam de Flyout-viewer niet bevalt. Ze houden van de zoomfunctie, maar ze willen dat klanten het zoomeffect direct boven de schoenen zien. In dat geval past u gewoon de InlineZoom-viewer toe op de afbeeldingsset en kopieert en plakt u de URL in uw browser om te zien hoe deze zich gedraagt. [Probeer het](https://s7d1.scene7.com/s7viewers/html5/FlyoutViewer.html?asset=jpearldemo/Running&amp;config=jpearldemo/InlineZoom){target="_blank"}.

Wanneer u de muisaanwijzer over de schoen beweegt, zoomt u in op die afbeelding en ziet u meer details wanneer u de aanwijzer verplaatst. En de reden daarvoor is gewoon de grootte van de afbeelding die aanvankelijk in Dynamic Media werd geüpload.

Als je denkt dat je als consument leeft, of als je je dagelijkse rol vervult, en als je naar verschillende websites gaat, zie je dit soort dingen. Denk na over hoe dat gebeurt en hoe je de kracht van Dynamic Media kunt gebruiken in je eigen werk en op de website van je bedrijf.

U leest alleen over afbeeldingssets en viewers. Laten we naar een paar andere kijkers kijken en ze uitproberen op één manier. Als u de viewer opnieuw wilt instellen, klikt u op de knop **[!UICONTROL Refresh]** linksonder.

<!-- LEAVE THIS HIDDEN PATH IN THE DOCUMENTATION FOR DEMO PURPOSES [Flyout viewer with image set](http://www.partycity.com/girls-little-old-lady-costume-P750948.html) -->

* `ZoomVertical_dark` viewer toegepast op een afbeeldingselement. [Probeer het](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_96311480&amp;config=jpearldemo/ZoomVertical_dark){target="_blank"}.
* `Zoom_light` viewer die op een afbeelding is toegepast. [Probeer het](https://s7d1.scene7.com/s7viewers/html5/BasicZoomViewer.html?asset=jpearldemo/AdobeStock_38827423&amp;config=jpearldemo/Zoom_light){target="_blank"}.

## Optioneel - Meer informatie

Als u meer wilt weten over wat u zojuist leest, gebruikt u de onderstaande materialen om concepten in detail te verkennen. Anders is de Dynamic Media-reis voltooid!

_Dynamic Media Help-onderwerpen_

* [Voorinstellingen voor afbeeldingen maken](/help/assets/dynamic-media/image-presets.md)
* Een lijst van [parameters voor afbeeldingsverwerking](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference.html) die u kunt gebruiken in het veld Afbeeldingsmodifier wanneer u een voorinstelling voor een afbeelding maakt
* [Elementen voorvertonen](/help/assets/dynamic-media/previewing-assets.md)
* [Een voorvertoning weergeven van 3D-elementen](/help/assets/dynamic-media/previewing-3d-assets.md)
* [Afbeeldingssets maken](/help/assets/dynamic-media/image-sets.md)
* [Spin-sets maken](/help/assets/dynamic-media/spin-sets.md)
* [Gemengde mediasets maken](/help/assets/dynamic-media/mixed-media-sets.md)

_Dynamic Media-zelfstudies_

* [Dynamic Media gebruiken met Experience Manager Assets](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [Adobe Experience Manager-inhoudsbibliotheek](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (zoek op _Dynamic Media_)

_Dynamic Media-viewers_

* [Live demo&#39;s](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) van elke viewer

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->