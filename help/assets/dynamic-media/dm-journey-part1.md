---
title: Dynamic Media Journey, Deel I
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
exl-id: f3472006-d5ae-4f70-af3e-44e73aee85cc
source-git-commit: 879af9e3168a1ab993eff930355c4bd200879c71
workflow-type: tm+mt
source-wordcount: '3612'
ht-degree: 0%

---

# Dynamic Media Journey: The Basics, Part I {#dm-journey-part1}

{{work-with-dynamic-media}}

Welkom bij de Dynamic Media Journey.

Deze reis gaat over de grondbeginselen van Dynamic Media, hoe het werkt, wat het voor u kan doen, en welke waarde het aan uw werk en uw klanten brengt.

**_Eerste vereisten_**

* Basiskennis van afbeeldingen en video-indelingen
* Basiskennis van HTML en CSS
* Basiskennis van ontwerpgereedschappen zoals Adobe Illustrator, Adobe Photoshop, Adobe XD
* Toegang tot Dynamic Media op Experience Manager is nuttig, maar niet vereist

**_wat u kunt verwachten te leren_**

_Deel I_

* Wat is Dynamic Media en hoe kan het u helpen?
* Kwesties gebruiken voor Dynamic Media
* Hoe een activum via het Dynamic Media-systeem stroomt

_Deel II_

* Anatomie van een Dynamic Media URL en hoe Dynamic Media inhoud levert
* Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen
* Afbeeldingssets, centrifuges en gemengde mediasets

**_Publiek_**
Het publiek dat het beste past bij de lezers van deze reis zijn de volgende personen die nieuw zijn voor Dynamic Media op Experience Manager:

* Beheerder
* Zakelijke analist
* Content Architect
* Inhoudsauteur
* Designer
* Developer
* Marketing
* Productmanager/eigenaar

>[!TIP]
>
>Voor de beste resultaten raadt Adobe u aan deze Dynamic Media-reis op een desktopcomputer te lezen en weer te geven.

## Wat is Dynamic Media en hoe kan het u helpen? {#dm-journey-a}

Met Dynamic Media kunt u op aanvraag rijke visuele producten en marketingmaterialen leveren. Het helpt u ook om interactieve het bekijken ervaringen, met inbegrip van gezoem, 360 graadspin, en video tot stand te brengen en te dienen. Uw elementen worden dynamisch geschaald voor gebruik op internet-, mobiele en sociale sites. Met behulp van een set primaire bronelementen - zoals afbeeldingen, video en 3D - genereert en levert Dynamic Media in real-time meerdere variaties van deze rijke inhoud via de algemene, schaalbare, voor prestaties geoptimaliseerde CDN (Content Delivery Network).

Dynamic Media past de workflows van de Adobe Experience Manager Assets-oplossing voor digitaal beheer van bedrijfsmiddelen toe om het beheerproces voor digitale campagnes te vereenvoudigen en te stroomlijnen.

### Eén bestand met eindeloze mogelijkheden

Één van de belangrijkste punten om over Dynamic Media te begrijpen is het concept _Één primair activadossier met eindeloze mogelijkheden_.

Om dit concept beter te begrijpen, denk over de manier u traditioneel met één enkel middel, zoals een beeld of een video werkt. Meestal maakt u één primair middel. Vervolgens maakt u handmatig versies van hetzelfde element voor elke ervaring, elk apparaat dat nodig is, elke webpagina en elke eigenschap waar het wordt gebruikt. Met tijd, kan dat enige middel tot 20, 30, of meer versies groeien, zonder versiegeschiedenis in bijlage aan hen. Stel je voor dat je dat doet voor elk beeld of elke video die je hebt. Het aantal versies van middelen zou snel overweldigend worden om te onderhouden en bij te werken, om nog maar te zwijgen van de stijging van opslagkosten.

Dynamic Media, echter, is fundamenteel verschillend van andere systemen omdat u het gebruikt om uw media __ van enige, primaire activa, en van vraag te leveren URL. De Dynamic Media URL-paden die u aanvraagt, bevatten instructies die de publicatieserver van de Adobe vertellen hoe het element moet worden weergegeven wanneer het op het scherm van de klant wordt weergegeven. Als u bijvoorbeeld hetzelfde primaire element gebruikt, kunt u het onmiddellijk in onbeperkte uitvoeringen laten leveren, waarbij de grootte, indeling, resolutie, gewicht, kleur, uitsnijden en effecten zoals een zoomweergave worden gewijzigd.

Deze unieke leveringsmethode zorgt ervoor dat de verenigbare kwaliteitservaringen naar om het even welk scherm, ongeacht grootte of bandbreedte worden verzonden. Volledige video&#39;s zijn ook geoptimaliseerd voor alle schermtypen en worden adaptief gestreamd om een consistente gebruikerservaring van hoge kwaliteit te garanderen.

<!-- As part of building and publishing assets with Dynamic Media, you visually configure the effects that you want to apply to assets. In so doing, you are literally building the URL that correctly tells the publish server how to deliver your primary asset to the screen.  -->

![ Adobe Dynamic Media levert het zelfde primaire beeld aan verschillende media in verschillende grootte en formaten ](/help/assets/dynamic-media/assets/dm-oneasset-multioutput.png)
_Adobe Dynamic Media verzekert verenigbaar, de kwaliteitservaringen worden geleverd aan om het even welk scherm, ongeacht grootte of bandbreedte._

Terwijl u doorleest, gaat u meer leren over waarom dit concept van &quot;één primair elementenbestand, eindeloze mogelijkheden&quot; belangrijk is.

### Het netwerk voor de levering van inhoud

Wanneer u klaar bent om live te gaan met een afbeeldingselement of een video-element, wordt dit ondersteund door de ruggengraat van Dynamic Media, die bestaat uit een krachtig, bovenste leveringsnetwerk. Het netwerk dient elke dag honderden klanten over de hele wereld. De middelen worden verdeeld op het Netwerk van de Levering van de Inhoud - of CDN - dat door Akamai wordt ontvangen. CDN is een systeem van computerdiensten die samen samenwerken om inhoud, vooral grote rijke media inhoud, aan eind te leveren.

In het CDN-systeem wordt webinhoud opgeslagen in webcaches via internet. Vervolgens wordt het bestand vanuit de webcache aan de eindgebruikers geleverd, zodat het sneller kan worden geleverd. Dus de eerste keer dat iemand een webpagina downloadt, worden de elementen die ze zien geleverd aan een CDN-cache. Ze worden opgeslagen op de server, zodat dezelfde inhoud sneller wordt geleverd wanneer iemand in hetzelfde gebied de webpagina weer opent. De inhoud wordt sneller geleverd, omdat deze zich dichter bij de gebruiker bevindt. Een CDN maakt voor snellere Web-pagina vertoningen, en toch vermindert het bandbreedteeisen op de centrale server omdat de inhoud van een geheim voorgeheugennetwerk, niet van een centrale server in elke instantie wordt geleverd. Deze geoptimaliseerde stroom betekent een betere gebruikerservaring, die tot verhoogde verkoop leidt.

<!-- USE AN IMAGE HERE? ![Content delivery network](/help/assets/assets-dm/cdn.png) -->

Historisch, levert CDN 3.5 petabytes van verkeer aan klanten elke maand. Het systeem kan 52 miljard activa in één enkele dag leveren. Dat aantal vergelijkt aan 864.000 beelden en video&#39;s met succes geleverd aan klanten, _elke seconde_.

### Slimme afbeeldingen

Dynamic Media is al heel goed in het optimaliseren van elementen en het ervoor zorgen dat elk element via de CDN snel wordt geladen op mobiele en desktopsystemen. Hiervoor worden in Dynamic Media afbeeldingsvoorinstellingen gebruikt om de kwaliteit van de afbeelding te definiëren. Ze definiëren ook het type afbeelding dat u verzendt, de scherpte en andere delen voor verschillende delen van uw ervaringen of pagina&#39;s.

Maar om waarde aan Dynamic Media verder toe te voegen voorbij beeld stelt vooraf in, is er _Slimme Beeldvorming_.

Smart Imaging biedt nog betere prestaties bij het leveren van afbeeldingselementen door de indeling en bestandsgrootte van een afbeelding automatisch te optimaliseren op basis van de browsermogelijkheden van de klant. Het werkt met uw bestaande voorinstellingen voor afbeeldingen (voorinstellingen voor afbeeldingen worden besproken in deel II van deze reis) en gebruikt intelligentie bij levering.

Deze intelligentie vermindert verder de grootte van het beelddossier die op browser en de snelheid van de netwerkverbinding wordt gebaseerd. Omdat imageelementen het grootste deel van de laadtijd van een pagina uitmaken, kan de prestatieverbetering een grondige invloed hebben op belangrijke bedrijfsindicatoren, zoals:

* Hogere conversie
* Tijd doorgebracht op de locatie
* Lagere stuitsnelheid van site

Over het algemeen kunt u met intelligente beeldverwerking een prestatieverbetering van 22 tot 47% verwachten, afhankelijk van uw bestaande voorinstellingen voor afbeeldingen en specifieke kenmerken van de eindgebruiker. De beeldkwaliteit blijft behouden alsof deze nooit wordt beïnvloed.

![ Slimme Beeldvorming ](/help/assets/dynamic-media/assets/dm-smart-imaging.png)
_het Slimme Beeld optimaliseert automatisch het formaat en de dossiergrootte van een beeld die op browser van een klant vermogen en netwerksnelheid wordt gebaseerd._

Slimme beeldverwerking is niet standaard ingeschakeld, omdat hiervoor een gecoördineerde inspanning van u en de Adobe van Dynamic Media nodig is. Voor het inschakelen van Smart Imaging moet de CDN-cache volledig worden gewist. Deze cache wordt vervolgens opnieuw gevuld met tijd. Als u in het gebruiken van Slimme Beeldvorming geinteresseerd bent, kunt u met Adobe werken om het te hebben aangezet door een technisch steunkaartje voor te leggen. Technische ondersteuning geeft u vervolgens een URL-parameter waarmee u vooraf slimme beeldverwerking kunt uitproberen. U kunt de presentatie uitproberen op elk van uw webpagina&#39;s of afbeeldingen, zodat u de prestaties en besparingen kunt zien. U kunt SmartImage vervolgens inschakelen voor uw volledige site.

### Adaptieve videosets

Wanneer er een video op een pagina, of een hoofdpagina is, neigen uw klanten om met die inhoud langer in dienst te nemen en langer op de pagina te blijven, wat typisch een goed ding is. Dit gedrag wordt getoond door analyses die de Adobe heeft uitgevoerd. Video kan echter complex zijn. Om te beginnen hebt u vaak een groot primair bestand. Het is ingewikkeld om te bepalen hoe te en video te leveren, allen om ervoor te zorgen dat de ervaring regelmatig loopt ongeacht het apparaat het wordt bekeken, en ongeacht bandbreedte.

Om deze kwestie op te lossen, geeft Dynamic Media u de capaciteit om _Aangepaste VideoReeksen_ tot stand te brengen.

Met een adaptieve videoset worden versies van dezelfde video gegroepeerd die met verschillende bitsnelheden en indelingen zijn gecodeerd.

U begint met uw originele, primaire video, die u in het systeem uploadt. Dynamic Media wijzigt automatisch grootte, of _transcodeert_, die video in veelvoudige video&#39;s. Op het moment van levering bepaalt het op intelligente wijze welk videoscherm, welke kwaliteit en welke indeling moet worden gebruikt en levert het aan de telefoon, tablet of desktopcomputer.

Op een mobiel iOS-apparaat wordt bijvoorbeeld een bandbreedte zoals 4G, 5G of Wi-Fi gedetecteerd. Vervolgens wordt automatisch de naar rechts gecodeerde video geselecteerd bij de verschillende bitsnelheden van de video in de adaptieve videoset. De video wordt gestreamd naar mobiele apparaten, tablets of desktopcomputers.

Bovendien wordt de videokwaliteit dynamisch geschakeld automatisch als de netwerkvoorwaarden veranderen. En als een klant in de modus Volledig scherm op een desktopcomputer komt, reageert de Adaptive Video Set met een betere resolutie, waardoor de kijkervaring van de klant wordt verbeterd.

Het gebruik van Adaptieve videosets zorgt voor een vloeiende, hoogwaardige weergave voor klanten die Dynamic Media-video op meerdere schermen en apparaten afspelen. Het neemt de complexiteit van video echt weg.

## Kwesties gebruiken voor Dynamic Media {#dm-journey-b}

Hieronder vindt u een aantal veelvoorkomende gebruiksproblemen en oplossingen waarmee Dynamic Media u kan helpen bij het aansturen van een positieve betrokkenheid van klanten, loyaliteit, conversie en een verhoogd rendement op investeringen.

### Hoofdlettergebruik: benadering primaire bestanden

Een van de belangrijkste gebruiksgevallen voor Dynamic Media is ook een van de meest voor de hand liggende. Dat wil zeggen, het gewicht van pagina&#39;s en ervaringen verminderen en de grootte van de inhoud verminderen, of het nu gaat om een afbeelding of een video die wordt geleverd.

Hieronder ziet u een typische ervaring of webpagina. Ongeveer 90% van een pagina bestaat uit rijke media, zoals beelden en video&#39;s, die algemeen veel zwaardere dossiers zijn.

![ de paginagewicht van de Inhoud ](/help/assets/dynamic-media/assets/dm-content-page-weight.png)
_de paginagewicht van de Inhoud van een typische Web-pagina._

De resterende 10% is HTML, CSS-code en specifieke tags. U wilt de 90%-dikte van die pagina optimaliseren en Dynamic Media helpt daarbij. Eerder, las u over het concept _één primair activadossier met eindeloze mogelijkheden_. Deze aanpak is belangrijk voor het verminderen van het totale paginagewicht. De mogelijkheid om één primair middel te gebruiken op een pagina met productdetails, een miniatuurpagina, uw winkelwagentje en uw zoekraster, is een goede tijdbesparende functie. En het zorgt ook voor consistentie tussen ervaringen.

![ Primaire dossierbenadering ](/help/assets/dynamic-media/assets/dm-onefile.png)
_de horloge is één primair activadossier, maar met veelvoudige vertoningen van het - niet exemplaren - gecreeerd op de vlucht._

Laten we nader kijken naar de problemen die Dynamic Media oplost met het ene bestand en een aantal van de oplossingen voor die aanpak.

| **Uitgave** | **oplossing van Dynamic Media** |
|---|---|
| Maak elk element en sla dit op. | Gebruik één afbeeldingsbestand, waarbij de vereiste uitvoeringen alleen automatisch worden gemaakt op het moment van levering. |
| Hoge opslagkosten. | Hiermee voorkomt u dat meerdere kopieën van een element moeten worden gemaakt en opgeslagen. |
| Moeilijkheden om de voogdijketen te handhaven. | Garandeert de levering van apparaat-geoptimaliseerde en verenigbare ervaringen. |
| Geen versiehistorie. | |
| Inconsistente merkervaringen op verschillende apparaten. | |
| Onnodige kosten voor het maken van dubbele elementen. | |

Wanneer u aan één dossier denkt, creeert u activa voor elke soort ervaring. U hebt misschien één beginafbeelding, en dan moet u 20, 30 of 40 variaties van die afbeelding maken, die u uiteindelijk moet opslaan en betalen voor die opslag.

Dan moet u ervoor zorgen dat het juiste beeld wordt gebruikt en dat uw vermogen om consistentie over uw merken te hebben kan beïnvloeden. En als u een afbeelding niet kunt vinden, moet u teruggaan en deze elementen dupliceren.

Met Dynamic Media kunt u variaties van afbeeldingen maken, direct, vanaf de eerste afbeelding. Met dit programma kunt u creatief zijn met dat primaire materiaal en hoeft u niet met uw grafisch ontwerper of fotostudio om aanvullende inhoud te maken heen en weer te gaan. En dat is geld en tijd bespaard.

Bij de aanpak van één bestand gebruikt u één primair bestand. Maak vervolgens die versies of uitvoeringen die op uw sites vereist zijn, en eigenschappen en ervaringen, alleen op het moment dat ze door een klant worden geleverd of gezien. Deze efficiëntie kan de hoeveelheid opslagruimte die nodig is voor uw middelen aanzienlijk verminderen en de complexiteit van uw workflow in het algemeen verminderen. En met Dynamic Media&#39;s leveringssysteem garandeert het dat elk beeld en elke video geoptimaliseerd is, snel wordt geladen en er op alle schermen en apparaten geweldig uitziet.

### Hoofdlettergebruik: Video

Een ander gebruiksgeval waarvoor Dynamic Media oplost is video. Video is complex. Het is moeilijk te beheren. Videobestanden zijn lastig op te slaan en te verplaatsen vanwege hun inherente bestandsgrootte.

| **Uitgave** | **oplossing van Dynamic Media** |
|---|---|
| Moeilijk om video te beheren en te leveren die voor diverse apparaten wordt geoptimaliseerd. | Gebruik één video waarvan de grootte automatisch voor alle apparaten wordt aangepast. |
| Video&#39;s worden standaard of worden op lage kwaliteit afgespeeld vanwege de beschikbare bandbreedte van de gebruiker. | Lever video via een HTML-speler die de beschikbare bandbreedte automatisch detecteert en de kwaliteit aanpast om een hoge kwaliteit en een vloeiende weergave te garanderen. |
| Onuitvoerbaar en tijdrovend om alle versies van een video handmatig te maken, alleen voor een goede weergave en weergave op verschillende apparaten. | Elimineer de uren van vervelende transcoderingswerk met een vereenvoudigde werkstroom. |
| | Maak tijd vrij voor werk van hogere waarde. |

Klanten komen naar Dynamic Media met de volgende problemen die ze hopen op te lossen:

&quot;_Mijn zaken heeft de video, en de afdeling besteedde een groot bedrag aan het creëren van het, maar verscheept van het plaatsen van het op pagina&#39;s, of het leveren van het. De reden was dat de kwaliteit van de video niet gegarandeerd kon worden door het testen, of zelfs niet als het echt zou spelen. En uiteindelijk, beïnvloedt dat het merk van de zaken en potentieel zijn rol aan omzetting._&quot;

Dynamic Media&#39;s oplossing is dat één primair videobestand wordt gebruikt en dat Dynamic Media alle formaten laat doormaken via zijn transcoderingsproces. Dan, koppel dat met de intelligente videospeler van Dynamic Media. Deze workflow garandeert dat de video die u gebruikt op de hoofdbestemmingspagina of op een categorie- of productdetailpagina, overal consistent zal zijn en van hoge kwaliteit zal worden geleverd.

Hier zijn verscheidene meer te overwegen gebruiksgevallen.

### Gebruik van hoofdletters en kleine letters: Eén bron van waarheid

| **Uitgave** | **oplossing van Dynamic Media** |
|---|---|
| Digitale middelen verspreid over de organisatie, verdeeld in verschillende teams of bedrijfseenheden. | Alle digitale middelen opslaan en beheren op een centrale locatie. |
| Teamleden downloaden lokale versies en maken deze. | De leden van het team gebruiken één enkel primair dossier om _tot stand te brengen en_ alle noodzakelijke versies over diverse het schermgrootte en apparaten te leveren. |
| Elementen voor eenmalig gebruik die zijn gemaakt voor elke ervaring en elk apparaat. | Elimineert bedrijfsmiddelen voor eenmalig gebruik en bespaart tijd en geld bij het maken ervan. |

### Hoofdlettergebruik: slim uitsnijden met AI-voeding voor rich media

| **Uitgave** | **oplossing van Dynamic Media** |
|---|---|
| Het tijdrovende en arbeidsintensieve tekenen, meten en knippen van afbeeldingen of video&#39;s om het brandpunt te benadrukken en op de juiste wijze weer te geven op alle schermgrootten en apparaten. | Gebruikt SmartCrop in Dynamic Media, een Adobe Sensei AI-mogelijkheid, om automatisch het brandpunt in een afbeelding of video te detecteren en uit te snijden om het brandpunt te behouden. |
| Tijd verloren die beter kan worden besteed aan het creëren van ervaringen met een hoog effect. | Hiermee legt u het bedoelde interessepunt vast, ongeacht de schermgrootte. |
| Elementen voor eenmalig gebruik die zijn gemaakt voor elke ervaring en elk apparaat. | Elimineert vervelende handmatige taken en biedt beelden en video van hoge kwaliteit die snel worden geladen en die er op elk apparaat of scherm goed uitzien. |

### Hoofdlettergebruik: interactieve media ontwerpen

| **Uitgave** | **oplossing van Dynamic Media** |
|---|---|
| Plat en statische klantenervaringen die geen aansporing, geen loyaliteit, of aandrijvingsomzetting aangaan. | Met deze optie kunnen niet-technische gebruikers eenvoudig en naadloos interactieve elementen toevoegen, zoals hotspots, carrousels en centrifuges, voor meer dynamische en boeiende ervaringen. |
| Beperkt rendement op investeringen van digitale middelen en een lappendeken van ervaringen van klanten. | Stuurt conversie en rendement op investeringen uit veelzijdige media-ervaringen. |

## Hoe een activum via het Dynamic Media-systeem stroomt {#dm-journey-c}

Hieronder ziet u een standaardworkflow voor Dynamic Media.

![ het werkschema van Dynamic Media ](/help/assets/dynamic-media/assets/dm-workflow.png)
_hoe een activa door het systeem van Dynamic Media stromen._

U begint met de creatiefase met het belangrijkste doel om uw primaire activa aan het eind te hebben. Deze primaire elementen kunnen afkomstig zijn van fotofragmenten, van videobereizers of van audiobestanden die u hebt gemaakt. U kunt de toepassingen van de Creative Suite van de Adobe zoals Adobe InDesign, Adobe Photoshop, Adobe Illustrator gebruiken om u te helpen de inhoud uitwerken.

Wanneer het ontwerponderdeel klaar is, plaatst u het element in de ontwerpoplossing door het element te uploaden naar Dynamic Media. In Dynamic Media zorgt u ervoor dat u de juiste voorinstellingen en viewers voor afbeeldingen op uw verschillende webpagina&#39;s op uw site hebt geplaatst.

En uiteindelijk optimaliseert u al die inhoud en publiceert u deze naar Dynamic Media-servers, zodat deze beschikbaar is voor web, drukwerk, e-mail, desktops en mobiele apparaten.

### Elementen uploaden naar Dynamic Media

Wanneer u klaar bent met het maken van een primair middel, uploadt u het naar Dynamic Media. Het type bestand dat u uploadt en de indeling en grootte van het bestand zijn belangrijke kenmerken voor Dynamic Media. Het is op het moment van het uploaden dat u ervoor wilt zorgen dat de maximale waarde wordt gehaald uit de ondersteuning van één bestand.

De onderstaande afbeelding is bijvoorbeeld 4560 x 3020 pixels. En hoewel u misschien nooit een afbeelding van die grootte gebruikt, kunt u deze nog uploaden. Hoe groter de afbeelding, hoe beter de kwaliteit die Dynamic Media kan leveren, zelfs tot een miniatuuruitvoering. Herinner me: u kunt _gemakkelijk verminderen_ de resolutie van een bestaand beeld. Maar als u probeert __ de resolutie van een beeld te verhogen, zal het resultaat waarschijnlijk onbevredigend zijn.

![ Geadviseerde formaten om in Dynamic Media ](/help/assets/dynamic-media/assets/dm-upload-formats.png) te uploaden
_Overwegingen voor activa uploadt._

Adobe raadt u aan elementen zonder verlies te uploaden. Over het algemeen kunt u het beste JPEG voorkomen, omdat u de afbeeldingskwaliteit na verloop van tijd begint te verliezen wanneer u JPEG levert of JPEG blijft opslaan. U wilt beginnen met afbeeldingen met de hoogste resolutie in een indeling zonder verlies waarmee u kunt leven. Deze indeling is doorgaans een TIFF- of PNG-bestand.

Wanneer u nadenkt over een digitaal kanaal of een webweergave, denkt u doorgaans aan RGB (rood, groen, blauw).

De meesten zouden nooit nadenken over het leveren van iets in CMYK of waarom u misschien zelfs in CMYK wilt leveren. De reden hiervoor is dat de kleurruimte het meest wordt gebruikt voor het afleveren van afgedrukte items. Maar Dynamic Media kan in beide kleurruimten zorgen.

Er zijn veel klanten die nog steeds drukken, zoals pakhuis-groothandelsclubs. Er zijn supermarkten die vaak vliegers wekelijks afdrukken. Dergelijke klanten vereisen dat hun beelden in beide kleurenruimten zijn. Dit vereist meestal twee verschillende afbeeldingen: een in RGB en een in CMYK. U kunt CMYK-elementen echter rechtstreeks uploaden naar Dynamic Media en Dynamic Media RGB-elementen laten leveren via een voorinstelling voor afbeeldingen of via een kleurprofiel. Er is geen behoefte om veelvoudige versies van een dossier tot stand te brengen, waarbij het concept _één primair activadossier met eindeloze mogelijkheden_ wordt gehandhaafd.

<!-- **The Value of Renditioning??? or Demo portion** -->

### Publish en voorvertoningselementen

Nadat u activa in Dynamic Media uploadt, is het een goede praktijk om __ hen te publiceren door de activa te selecteren, en dan **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]** in Dynamic Media te klikken. U moet elementen publiceren als u ze in een ervaring wilt gebruiken. Nadat elementen zijn gepubliceerd, kunt u ze gebruiken om op een webpagina op te nemen met een door Dynamic Media gegenereerde URL die u kopieert, of door code op de pagina in te sluiten.

Naast het handmatig publiceren van middelen kunt u Dynamic Media zodanig configureren dat u direct elementen publiceert - zonder tussenkomst van de gebruiker - op het moment van uploaden.

Na het uploaden zijn er verschillende manieren om een voorvertoning van de uitvoeringen van een element weer te geven in Dynamic Media. Voorvertoning van uitvoeringen kan u helpen een idee te krijgen van wat een klant ziet. Een gemeenschappelijke voorproefmethode moet een activa selecteren en dan zijn Vertoningen bekijken door een _vooraf ingesteld beeld_ zoals gezien in het volgende te selecteren.

![ Previewing een vertoning van een activa die op het Grote beeld wordt gebaseerd vooraf ingesteld ](/help/assets/dynamic-media/assets/dm-image-preset-with-url.png)
_previewing een vertoning van een activa die op geselecteerde &quot;Grote&quot;beeldvooraf ingesteld wordt gebaseerd. Er is op de URL-knop geklikt. Het resulterende URL-pad bevat de naam voor de voorinstelling &quot;Groot&quot; en kan worden gebruikt in een webpagina._

Bovenstaande URL is live! [ probeer het ](http://s7d1.scene7.com/is/image/jpearldemo/AdobeStock_28563982?$Large$) {target="_blank"}.

Een andere methode aan voorproef een activa is de beeldactiva te selecteren en dan a _vooraf ingestelde Kijkers_ te selecteren zoals die in het volgende wordt gezien.

![ Previewing activa die op de Verticale die kijker van het Licht van het Gezoem wordt gebaseerd ](/help/assets/dynamic-media/assets/dm-viewer-preset.png)
_previewing activa die op geselecteerde &quot;ZoomVertical_light&quot;kijker wordt gebaseerd vooraf ingesteld. De muisaanwijzer (`+`) is over het horloge verplaatst om in te zoomen. Merk op URL en bed knopen in._

De bovenstaande vertoning is live! [ probeer het ](https://s7d1.scene7.com/s7viewers/html5/ZoomVerticalViewer.html?asset=jpearldemo/AdobeStock_28563982&amp;config=jpearldemo/ZoomVertical_light) {target="_blank"}.

## Optioneel - Meer informatie

Deel I van deze reis ging over de grondbeginselen van verschillende Dynamic Media-onderwerpen. Als u meer wilt weten over wat u leest, gebruikt u de onderstaande materialen om concepten in detail te verkennen. Anders kunt u doorgaan met deel II van uw reis. Zie [ wat volgende in deze Reis van Dynamic Media ](#whats-next) is.

{{see-also-dm}}
<!--
_Dynamic Media Help topics_

* [Work with Dynamic Media in Experience Manager](/help/assets/dynamic-media/dynamic-media.md)
* [About Smart Imaging](/help/assets/dynamic-media/imaging-faq.md)
* [How to create Adaptive Video Sets](/help/assets/dynamic-media/video.md)
* [Best practices for optimizing the quality of your images](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md)
* [How to upload assets](/help/assets/add-assets.md#upload-assets)
* [How to preview assets](/help/assets/dynamic-media/previewing-assets.md)
* [How to preview 3D assets](/help/assets/dynamic-media/previewing-3d-assets.md)
* [How to deliver Dynamic Media Assets](/help/assets/dynamic-media/delivering-dynamic-media-assets.md)
* [How to publish assets](/help/assets/dynamic-media/publishing-dynamicmedia-assets.md)
* [Work with Selective Publish in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md) -->

_zelfstudies van Dynamic Media_

* [ Gebruik Dynamic Media met Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html)
* [ de inhoudsbibliotheek van Adobe Experience Manager ](https://experienceleague.adobe.com/?lang=en#recommended/solutions/experience-manager) (onderzoek op _Dynamic Media_)

_de kijkers van Dynamic Media_

* [ Levende Demo&#39;s ](https://landing.adobe.com/en/na/dynamic-media/ctir-2755/live-demos.html) van elke kijker

## Hoe verder in deze Dynamic Media-reis {#whats-next}

In deel II van deze reis, onderzoekt u nauwgezet Dynamic Media URLs om beter te begrijpen wat aan de hand is wanneer een activa wordt geleverd. U leert ook meer over de grondbeginselen van het maken van voorinstellingen voor afbeeldingen om elementen te renderen, en leert over Afbeeldingssets, Spin-sets en Gemengde-mediasets en hoe deze worden gemaakt.

Neem me aan [ Reis van Dynamic Media: De Grondbeginselen, Deel II ](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-d).

<!-- Live as of April 28 2022. LEAVE IN HERE https://landing.adobe.com/en/na/dynamic-media/ctir-2755/index.html -->