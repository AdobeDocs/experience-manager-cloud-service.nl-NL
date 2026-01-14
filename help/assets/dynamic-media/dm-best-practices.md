---
title: Best practices voor dynamische media
description: Leer meer over de beste praktijken in Dynamische Media wanneer het over het werken met beelden en video en beste praktijken voor Dynamische Kijkers van Media.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '4048'
ht-degree: 0%

---

# Best practices voor dynamische media{#about-dm-best-practices}

<!--**Organizations today must connect with their customers through an ever-growing array of channels and devices.** The customer experience spans physical stores, websites, mobile apps, social media, email, and e-commerce platforms. This diversity requires organizations to create many more versions of each piece of content. Personalization adds complexity by increasing the number of variations needed for each item. Despite budget constraints for content creation, there's still a need to produce more campaigns in the same timeframe, on a global scale. AEM Dynamic Media offers a comprehensive set of tools to meet these challenges, providing consistent, personalized, high-performance, and optimized brand experiences across all channels and devices. 

Key Features of AEM Dynamic Media:

* **Single File Approach:** Save on storage costs by storing just one master file. AEM Dynamic Media generates all size variations and visual effects on-demand, at the time of delivery, eliminating workflow complexity and last-minute creative changes.
* **Global Reach:** With Smart Imaging, images are automatically optimized during delivery, significantly reducing file size and page weight without sacrificing visual quality. This optimization is tailored for network bandwidth and device pixel ratio.
* **AI-Powered Efficiency:** Smart Crop uses AI to automate the cropping of images and videos, focusing on points of interest. This feature saves countless hours of manual editing and is designed for large-scale enterprise production.
* **Video Made Simple:** Upload a master video file and AEM Dynamic Media will adaptively stream it in multiple languages and with descriptive audio, ensuring a broad reach.
* **Customizable Experience Viewer:** Select, customize, and brand the experience viewers for images and videos with ease. These viewers can be seamlessly integrated into any digital experience.
* **Support for Emerging Formats:** AEM Dynamic Media is also your solution for delivering immersive 3D and panoramic experiences.

In the accompanying guide, you'll find a comprehensive list of best practices for maximizing the benefits of AEM Dynamic Media. As you embark on your Dynamic Media journey, make sure to consult these expert recommendations and resources.

Stage Business Problem Best Practice Recommendation: This section will outline specific business challenges and provide targeted best practices and recommendations to address them effectively. -->

{{see-also-dm}}

Organisaties worden geconfronteerd met een explosie van kanalen en apparaten om contact met gebruikers te maken. De reis van de klant omvat fysieke winkels, Web, mobiel, sociale media, e-mail, en handel. Om aan deze vraag te voldoen, biedt Dynamic Media op Adobe Experience Manager (AEM) een uitgebreide oplossing. Het optimaliseert levering van activa, behandelt verpersoonlijking, en verzekert verenigbare, prestaties, en merk-gerichte ervaringen over kanalen en apparaten.

Enkele belangrijkste elementen van Dynamische Media omvatten het volgende:

* **Enige dossierbenadering:** met Dynamische Media, slaat u één primair brondossier op, en alle groottevariaties en visuele gevolgen worden dynamisch gecreeerd en geoptimaliseerd op het tijdstip van levering. Deze benadering bespaart opslagkosten en elimineert werkstroomcomplexiteit.
* **werkelijk globaal:** Slimme Beeldvorming, die tijdens inhoudslevering wordt toegepast, vermindert beduidend beeldgrootte en paginagewicht zonder visuele kwaliteit te compromitteren. Deze is geoptimaliseerd voor netwerkbandbreedte en pixelverhoudingen van apparaten.
* **AI aangedreven:** Slim Uitsnijden, een AI-gedreven eigenschap, automatiseert beeld en videopunt-van-belang het bebouwen. Het elimineert handeninspanning en schalen efficiënt voor bedrijfsgebruik.
* **Gemakkelijke video:** upload primaire bronvideo&#39;s in Dynamische Media en stroom hen adaptief over veelvoudige talen met beschrijvende audio.
* **de bibliotheek van de kijker van de Ervaring:** pas en merk ervaringskijkers voor beelden en video&#39;s aan. Deze viewers integreren naadloos in uw digitale ervaringen.
* **Ontkomende formaatsteun:** De Dynamische Media laat de levering van 3D en panoramische ervaringen toe.

Aangezien u de [&#x200B; Dynamische Reis van Media &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1) verkent, die de geconsolideerde lijst van beste praktijken hieronder herzien kan u helpen het grootste deel van zijn mogelijkheden maken. Pas deze best practices voor dynamische media aan aan uw specifieke context- en projectvereisten aan, zodat u uw ervaringen op verschillende kanalen en apparaten kunt optimaliseren.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>De best practices voor dynamische media in dit artikel kunnen in de loop der tijd evolueren naarmate nieuwe technologieën in dynamische media zich ontwikkelen. De informatie hieronder is actueel voor de recentste versie van Dynamische Media.


## Elementen opnemen in dynamische media

**Bedrijfs geval:** *beheert efficiënt grote volumes van activa en zorgt ervoor dat slechts relevante, goedgekeurde inhoud aan eind - gebruikers wordt geleverd.*

Stroomlijn uw beheer van grote aantallen activa efficiënt. Zorg ervoor dat slechts de aangewezen, geoorloofde inhoud uw eind - gebruikers door de Selectieve Synchronisatie van Dynamische Media **te gebruiken** en **Selectieve publiceer** eigenschappen bereikt.

* **Selectieve synchronisatie:**
Een pro-actieve eigenschap die u laat kiezen welke activa aan synchronisatie met Dynamische Media. U kunt bijvoorbeeld alleen die mappen synchroniseren die elementen bevatten waarvoor de definitieve goedkeuring is verleend. Deze workflow helpt u te controleren welke middelen worden voorbereid voor levering aan uw klanten.

* **Selectief publiceren:**
Nadat u uw elementen hebt gesynchroniseerd, kunt u met Selectief publiceren bepalen welke elementen zichtbaar zijn voor uw klanten. Dit betekent dat u kunt bepalen welke goedgekeurde middelen daadwerkelijk via uw kanalen worden geleverd, zodat uw klanten alleen de beste en meest relevante inhoud zien.

Deze twee beste praktijken helpen u betere controle, bestuur, en productiviteit over uw rijke-media inhoud bereiken.

Meer informatie? Ga naar [&#x200B; vormen Selectief publiceren op het omslagniveau in Dynamische Media &#x200B;](/help/assets/dynamic-media/selective-publishing.md).


## Dynamische mediaviewers

De best practices van Dynamic Media Viewer zijn essentiële richtlijnen die zijn ontworpen om de prestaties, functionaliteit en gebruikerservaring van Dynamic Media-elementen op AEM te optimaliseren. Deze praktijken zorgen ervoor dat de activa behoorlijk worden gesynchroniseerd, gepubliceerd, en gevormd om de volledige mogelijkheden van Dynamische Media te gebruiken.

Door deze beste praktijken te volgen, kunt u naadloze integratie, efficiënt middelenbeheer, en verbeterde kijkersinteractie bereiken. Het synchroniseren van elementen, het gebruik van slim uitsnijden en het volgen van de richtlijnen voor het opnemen van JavaScript-bestanden zijn allemaal belangrijke werkwijzen. Deze aanbevelingen helpen de integriteit en betrouwbaarheid van media levering over diverse platforms en apparaten handhaven.

* **Synchronize Kijker Assets:**
Zorg ervoor dat alle viewerelementen zijn gesynchroniseerd met Dynamic Media voordat u de speler gebruikt.

   * Open de pagina met voorbeeldbeheer op `/libs/dam/gui/content/s7dam/samplemanager/samplemanager` . Op deze pagina kunt u de elementen van een viewer opnieuw synchroniseren, inclusief pictogrammen voor een uitgeverfde viewer, CSS-bestanden en voorinstellingen.
   * Als u om het even welke viewerkwesties ontmoet, ga naar het [&#x200B; los Dynamische artikel van de Kijkers van Media &#x200B;](/help/assets/dynamic-media/troubleshoot-dm.md#viewers) problemen op.

* **publiceer Assets:**
Zorg ervoor dat de elementen zijn gepubliceerd voordat u deze weergeeft in de viewers voor levering.
* **Automatisch spelende Video&#39;s Gedemd:**
Voor automatisch afspelen in video&#39;s gebruikt u gedempte video-instellingen, omdat browsers het afspelen van video&#39;s met volume beperken.
* **het Slimme Uitsnijden:**
Gebruik de component Afbeelding v3 voor slim uitsnijden om de presentatie van afbeeldingselementen te verbeteren.
* **Insluiting van het Dossier van JavaScript:**
Neem alleen het JavaScript-bestand van de primaire viewer op uw pagina. Verwijs niet naar extra JavaScript-bestanden die de runtimelogica van de viewer kan downloaden. Maak met name geen directe koppeling naar de HTML5 SDK `Utils.js` -bibliotheek vanuit het `/s7viewers` -contextpad (ook wel SDK-include-bestanden genoemd). De logica van de viewer beheert de locatie van `Utils.js` of soortgelijke runtimeviewerbibliotheken, die tussen releases kunnen worden gewijzigd. Adobe houdt geen oudere versies van secundaire viewer-include-bestanden op de server bij, zodat het rechtstreeks verwijzen naar deze versies de viewerfunctionaliteit in toekomstige updates kan onderbreken.
* **Inbeddende Richtlijnen:**
Gebruik de documentatie voor het insluiten van richtlijnen die specifiek zijn voor elke kijker.
Meer informatie? Ga naar [&#x200B; Kijkers voor AEM Assets &#x200B;](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/viewers-aem-assets-dmc/c-html5-s7-aem-asset-viewers).
* **Zelfstudie en Voorbeelden van SDK:**
Herzie het [&#x200B; Zelfstudie van SDK van de Kijker &#x200B;](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/library/c-tutorial) en [&#x200B; HTML5 de toepassingsvoorbeelden van SDK &#x200B;](https://s7d9.scene7.com/s7sdk/2024.5/docs/jsdoc/index.html) voor een grondig inzicht in de component APIs van SDK.


## Elementen voorbereiden voor levering

### Uw elementen ordenen

**Bedrijfs geval:** *organiseert efficiënt activa om werkschema&#39;s te stroomlijnen.*

Voor efficiënte middelenorganisatie die workflows stroomlijnt, gebruikt u een of meer van de volgende aanbevolen procedures:

* **organiseer activa in omslagen:**
Bij het ordenen van elementen moeten deze worden ingedeeld in mappen, net als bij het ordenen van bestanden op een computer. Een correcte naamgeving, structurering van submappen en bestandsbeheer in deze mappen zijn van cruciaal belang voor een efficiënte verwerking van bedrijfsmiddelen. Het implementeren van systematische naamconventies en praktijken voor metagegevens maximaliseert het nut van de gegevensopslagruimte voor digitale middelen.
Meer informatie? Ga naar [&#x200B; organiseer activa in omslagen &#x200B;](/help/assets/organize-assets.md#organize-using-folders).
* **organiseer activa gebruikend markeringen:**
Tags toevoegen verbetert de zoekbaarheid, het maken van verzamelingen en de positie van zoekopdrachten. Adobe AI maakt gebruik van een zelfstudie-algoritme voor nauwkeurige codering, zodat elementen snel kunnen worden opgehaald. Adobe AI herkent en wijst ook relevante tags, waaronder aangepaste tags, toe aan assets, waardoor het beheer van bedrijfsmiddelen wordt vereenvoudigd met automatische, beschrijvende tags.
Meer informatie? Ga naar [&#x200B; organiseer activa gebruikend markeringen &#x200B;](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **organiseer activa als inzamelingen:**
Met Dynamic Media in combinatie met Experience Manager Assets kunt u op efficiënte wijze middelen verzamelen, bewerken en delen tussen gebruikers. U kunt diverse inzamelingstypes, met inbegrip van statische lijsten en dynamische, op onderzoek-gebaseerde compilaties vestigen. Deze inzamelingstypes kunnen over diverse plaatsen met klantgerichte toegang en het uitgeven rechten worden gedeeld.
Meer informatie? Ga naar [&#x200B; organiseer activa als inzamelingen &#x200B;](/help/assets/manage-collections.md).
* **organiseer activa gebruikend profielen:**
Een verwerkingsprofiel automatiseert de verwerking van middelen in aangewezen omslagen, die organisatie stroomlijnen. Door het standaardiseren van metagegevens, bestandsnamen en mapstructuren kunt u deze profielen consistent en nauwkeurig toepassen terwijl de verzameling van digitale elementen wordt uitgebreid.
Meer informatie? Ga naar [&#x200B; organiseer activa gebruikend profielen &#x200B;](/help/assets/organize-assets.md#organize-to-use-profiles).



### De kwaliteit van afbeeldingen optimaliseren

**Bedrijfs geval:** *verkrijg goede kwaliteitsbeelden van Dynamische Media.*

Om de beeldkwaliteit te verbeteren, moeten verschillende factoren zorgvuldig in overweging worden genomen. Het kan een tijdintensief proces zijn. Nochtans, zijn er sommige beproefde-en-ware praktijken die u kunnen helpen wenselijke resultaten bereiken. Tot de beste werkwijzen behoren onder andere het optimaliseren van de afbeelding, het verscherpen van afbeeldingen en de beste afbeeldingsindelingen die u kunt gebruiken.

Meer informatie? Ga naar [&#x200B; Beste praktijken voor het optimaliseren van de kwaliteit van uw beelden &#x200B;](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Omdat de perceptie van beeldkwaliteit van persoon tot persoon verschilt, is soms een systematische benadering van experimenten essentieel voor het bereiken van gewenste resultaten. Adobe Experience Manager ondersteunt dit proces met meer dan 100 opdrachten voor dynamische media voor het verbeteren van afbeeldingen.

Meer informatie? Controle [&#x200B; Dynamische Momentopname van Media &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 minuten, 17 seconden).

Als u de invloed van deze verschillende opdrachten op de afbeeldingskwaliteit wilt beoordelen, kunt u een afbeelding uploaden naar Dynamische media, de interface van het gereedschap gebruiken bij de opgegeven URL en de opdrachten toepassen die u wilt uitproberen.

Wil je het uitproberen? De [&#x200B; Dynamische Momentopname van Media van de lancering &#x200B;](https://snapshot.scene7.com/)

### Standaardiseren op stijlen die op afbeeldingen zijn toegepast

**Bedrijfs geval:** *normaliseert efficiënt de stijl en de transformatie die op mijn beeldactiva wordt toegepast.*

Gebruik regelmatig voorinstellingen voor afbeeldingen in dynamische media, zodat u de afbeeldingsformaten, indelingen en eigenschappen op consistente en dynamische wijze kunt aanpassen. Beschouw een voorinstelling voor afbeeldingen als een macro: het is een benoemde set opdrachten voor vergroten/verkleinen en opmaken. Als uw site bijvoorbeeld productafbeeldingen in verschillende formaten en formaten nodig heeft, met specifieke compressie voor desktops en mobiele apparaten, wordt dit proces efficiënt geautomatiseerd met behulp van Voorinstellingen voor afbeeldingen.

Wil je het uitproberen? Ga naar [&#x200B; Grondbeginselen van het creëren van beeld vooraf instelt om activa terug te geven &#x200B;](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### De focus en het beeld van afbeeldingen en video&#39;s aanpassen

**Bedrijfs geval:** *zorg ervoor dat het belangrijkste punt van belang van mijn beelden of video in nadruk over apparaten blijft.*

Smart Crop is een functie in Dynamic Media die gebruikmaakt van Adobe AI, Adobe AI en het leerframework voor machines om het bijsnijden van afbeeldingen en video&#39;s te automatiseren. Het detecteert en richt zich op intelligente wijze op het hoofdonderwerp of het belangrijkste aandachtspunt in een afbeelding of video. Deze intelligentie zorgt ervoor dat het brandpunt op verschillende schermgrootten op desktopcomputers en mobiele apparaten wordt gehandhaafd.

U kunt het beste een afbeeldingsprofiel maken met Slim uitsnijden. In het profiel kunt u verschillende schermgrootten definiëren en Adobe AI de rest laten doen, zodat uw afbeeldingen en video&#39;s altijd zijn geoptimaliseerd voor het apparaat van de viewer.

Meer informatie? Controle [&#x200B; Gebruikend Slimme Uitsnede met de Dynamische Media van AEM Assets &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minuten, 35 seconden) en [&#x200B; Gebruikend Dynamische Slimme Uitsnede van Media voor Video &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 minuten, 22 seconden).

### SEO-waarderingen verbeteren

**Bedrijfs geval:** *vorm Dynamische Media om betere classificaties te krijgen SEO.*

Gebruik regelmatig de volgende aanbevelingen om ervoor te zorgen dat uw afbeeldingen effectief bijdragen aan uw algemene SEO-strategie.

* **Betekenisvolle namen van beelddossier:**
Gebruik beschrijvende bestandsnamen die de afbeeldingsinhoud weerspiegelen. Bijvoorbeeld:

   * use `myCompany-Silver-Wrist-Watch`
   * *vermijd* `myCompany_Silver_Wrist_Watch` of `myCompanySilverWristWatch`

  Zodoende kunnen zoekprogramma&#39;s de context van de afbeelding begrijpen en de SEO verbeteren. Google geeft de voorkeur aan afbreekstreepjes boven onderstrepingstekens of spaties in een bestandsnaam. Vermijd ook het samenvoegen van woorden in een bestandsnaam.
* **Eigen domein:**
Implementeer een aangepast domein dat uw bedrijf of merknaam bevat om de herkenning en het vertrouwen van merken te versterken. Bijvoorbeeld:

   * use `http://images.mycompany.com/is/image/companyname/`
   * *vermijd* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`

* **SEO-vriendschappelijke omslagstructuur:**
Organiseer uw afbeeldingen in een mappenstructuur die uw bedrijfsnaam of merk bevat voor een betere indexering, zoals `http://images.mycompany.com/is/image/companyname/` .
* **Dynamische de regelreeksen van Media:**
Leer hoe u URL&#39;s voorwaardelijk kunt transformeren op basis van verschillende factoren, waardoor SEO en gebruikerservaring worden verbeterd.
Meer informatie? Ga naar [&#x200B; regelreeksen van het Gebruik om URLs &#x200B;](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md) om te zetten.
* **Slimme Beeldvorming en Slim Gewas:**
Gebruik de functies Slim beeld en Slim uitsnijden in dynamische media voor geoptimaliseerde en responsieve afbeeldingen. Hierdoor worden niet alleen de laadtijden van de pagina verbeterd, maar wordt ook een positieve bijdrage geleverd aan SEO-waarderingen.
Meer informatie? Ga naar [&#x200B; Slimme Beeldvorming &#x200B;](/help/assets/dynamic-media/imaging-faq.md), of bekijk [&#x200B; Gebruikend Slimme Uitsnede met de Dynamische Media van AEM Assets &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minuten, 35 seconden).

Houd er rekening mee dat deze aanbevolen procedures goed overeenkomen met de SEO-tips voor Google-afbeeldingen. Dergelijke praktijken benadrukken het belang om context en helderheid aan onderzoeksmotoren door juiste noemende overeenkomsten, gestructureerde gegevens, en geoptimaliseerde beeldlevering te verstrekken.

Meer informatie? Ga naar [&#x200B; URL structuur beste praktijken voor Google &#x200B;](https://developers.google.com/search/docs/crawling-indexing/url-structure) en [&#x200B; het beeldSEO beste praktijken van Google &#x200B;](https://developers.google.com/search/docs/appearance/google-images)

### Afbeeldingen dynamisch verbeteren en visuele effecten maken met behulp van opdrachten

**Bedrijfs geval:** *pas rijke visuele gevolgen op beelden toe.*

Dynamische media biedt een reeks opdrachten waarmee u afbeeldingen kunt verbeteren en visuele effecten dynamisch kunt maken, zonder dat u meerdere statische elementen nodig hebt. Hieronder volgt een korte uitleg van een aantal van deze processen en enkele voorbeelden die u kunnen helpen:

#### Effecten in de bronafbeelding

| Taak | Wat moet u doen? |
| --- | --- |
| **uploadt en publiceert uw originele beeld** | <ul><li> Begin door het originele beeld aan Dynamische Media te uploaden.</li><li> Zorg ervoor dat het via een URL is gepubliceerd en toegankelijk.</li><li> In dit voorbeeld wordt een voorraadafbeelding van een horloge met een witte achtergrond (laten we het &quot;Beeld X&quot; noemen) geüpload naar Dynamische media.<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer)</li></ul> |
| **creeer een masker** | <ul><li> Ontwikkelen een masker dat het onderwerp (het gebied waar u effecten wilt toepassen) en de achtergrond (het gebied dat u wilt wijzigen) definieert.<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)</li><li> Maskers zijn doorgaans grijswaardenafbeeldingen, waarbij wit het onderwerp vertegenwoordigt en zwart de achtergrond. U kunt maskers maken met gereedschappen zoals Adobe Photoshop.<br> wil meer leren? Ga naar [&#x200B; Creërend en het uitgeven van een snel masker in Photoshop &#x200B;](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).</li><li> Voor &quot;Beeld X,&quot;creeer een masker dat precies het onderwerp beschrijft u wilt verbeteren. Bijvoorbeeld een persoon, een object, enzovoort.</li></ul> |
| **pas Dynamische bevelen van Media URL voor gevolgen toe** | Nadat u een masker hebt, gebruikt u de URL-opdrachten om effecten toe te passen zoals een gloed buiten of wijzigt u de achtergrondkleur in &quot;Afbeelding X&quot;. Hier volgen twee voorbeelden:<ul><li> **Outer het effect van de gloed:**<br> om een buitenste gloedeffect langs de grens van het onderwerp toe te voegen, geef URL als dit uit:<br>[&#x200B; https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&effect=-1&pos=100,100&op_blur=75&op_grow=1&opac=25 &#x200B;](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&effect=-1&pos=100,100&op_blur=75&op_grow=1&opac=25) <br> In dit URL, `op_blur`, `op_grow`, en `opac` de parameters leiden tot het buitenste gloedeffect.</li><li> **Verandering van de Achtergrondkleur:**<br> om de achtergrondkleur te veranderen, gebruik URL met een verschillende waarde van de achtergrondkleur:<br>[&#x200B; https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&maskUse=invert&color=255,255,0 &#x200B;](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&maskUse=invert&maskUse=invert&color=255,255,0) <br> In dit voorbeeld, `color=255,255,0` plaatst de achtergrondkleur aan geel. Bewerk de achtergrond in een specifieke kleur voor visuele effecten.</li></ul> |

#### Een afbeeldingsrand toevoegen

Met Dynamische media kunt u afbeeldingen rechtstreeks via URL&#39;s bewerken. Dit is een krachtig hulpmiddel voor het maken van dynamische digitale ervaringen. Hieronder volgen enkele voorbeelden. Laten wij met het volgende originele beeld URL beginnen: [&#x200B; https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Taak | Wat moet u doen? |
| --- | --- |
| **Witte grens** | Om een witte grens toe te voegen, gebruik volgende URL:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10 &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10) <br> In dit URL, specificeert de `extend=10,10,10,10` parameter de grensgrootte van tien pixel op alle kanten. |
| **Vervagen langs de witte grens** | Om een vervagingseffect langs de witte grens toe te voegen, kunt u URL als volgt uitgeven:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&op_blur=60&color=0,0,0 &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&op_blur=60&color=0,0,0) <br> In dit URL, past de `effect=-1` parameter het vervagingseffect toe, en `op_blur=60` controleert de intensiteit van het onduidelijke beeld. |
| **het effect van de Slagschaduw langs de buitengrens** | Om een effect van de slagschaduw langs de buitengrens toe te voegen, gebruik dit URL:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&$shadow$&amp;color=0,0,0 &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&extend=10,10,10,10&effect=-1&$shadow$&color=0,0,0) <br> de `$shadow$` parameter leidt tot het schaduweffect, en `color=0,0,0` plaatst de schaduwkleur aan zwart. |

U kunt met deze URL&#39;s experimenteren om de gewenste visuele effecten te bereiken.

#### Afbeeldingsoverlays maken

Als u een logo of pictogram op een bestaande afbeelding wilt plaatsen, biedt Dynamic Media een eenvoudige manier om dit te bereiken met URL-opdrachten. Laten we de stappen afbreken.

| Stap | Wat moet u doen? |
| --- | --- |
| **uploadt en publiceert het basisbeeld** | Eerst uploadt en publiceert u de basisafbeelding waarop u het logo of pictogram wilt plaatsen. U kunt elke afbeelding als basis gebruiken.<br> bijvoorbeeld, hier is een basisbeeld:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **uploadt en publiceert het embleem of pictogrambeeld** | Vervolgens uploadt en publiceert u de afbeelding die u over de basisafbeelding wilt plaatsen. Deze afbeelding moet een transparant PNG-bestand zijn met het logo of pictogram dat u wilt bedekken.<br> hier is het transparante beeld PNG van een stervoorwerp met transparantiegevolgen die zullen worden bovenop gelegd:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/decorate-star &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **pas Dynamische Media URL** toe | Maak nu een URL voor dynamische media waarin de basisafbeelding en het logo of de pictogramafbeelding worden gecombineerd. U kunt URL-opdrachten gebruiken om dit effect te bereiken.<br> de structuur URL kijkt iets als dit:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&src=decorate-star&scale=1.25&posN=0.33,-.25&fmt=png &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&src=decorate-star&scale=1.25&posN=0.33,-.25&fmt=png) <br> waar de activa<ul><li> `hotspotRetailBaseImage` is de basisafbeelding.</li><li> `starxp` is de afbeelding van het logo/pictogram.</li><li> `layer=1` geeft aan dat het logo of pictogram in een laag over de basisafbeelding moet worden geplaatst.</li><li> `scale=1.25` past de grootte van het logo/pictogram aan.</li><li> `posN=0.33,-.25` bepaalt de positie van het logo/pictogram ten opzichte van de basisafbeelding.</li><li> `fmt=png` zorgt ervoor dat de uitvoer de PNG-indeling heeft.</li></ul> |

Meer informatie? Ga naar [&#x200B; src &#x200B;](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) voor meer details op het `src` bevel en andere Dynamische bevelen van Media URL.


#### Promotietekst overschrijven

Hieronder vindt u de stappen voor het bedekken van een promotietekstbericht op een afbeelding met HTML en CSS.

| Stap | Wat moet u doen? |
| --- | --- |
| **uploadt en publiceert het basisbeeld** | Eerst uploadt en publiceert u de basisafbeelding waarop u de tekst wilt plaatsen. U kunt elke gewenste afbeelding gebruiken. Bijvoorbeeld, hier is een beeld van de steekproefbasis:<br>[&#x200B; https://s7g2.scene7.com/is/image/genaibeta/leather-sofa &#x200B;](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa) <br> |
| **pas Dynamische de tekstexploitanten van Media toe** | Met Dynamische media kunt u tekstoperatoren toepassen om dynamische tekst rechtstreeks op de afbeelding te bedekken. De volgende voorbeeld-URL toont deze mogelijkheid:<br>[&#x200B; https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&posN=-0.3,-0.455&text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr 130&amp;bgcolor=FF3333&amp;wid=600&amp;hei=600 &#x200B;](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&posN=-0.3,-0.455&text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&size=370,70&textAttr=130&bgcolor=0 3333&wid=600&hei=600) |

#### Vergroten/verkleinen en uitsnijden voor verschillende toepassingen

##### Basisprincipes van afbeeldingsgrootte wijzigen

Bij het vergroten of verkleinen van afbeeldingen worden de afmetingen, resolutie en bestandsgrootte van een afbeelding gewijzigd. Hieronder volgen enkele belangrijke punten die u in overweging wilt nemen:

* **de samenstelling van het Pixel:**
Digitale afbeeldingen bestaan uit kleine stippen, pixels genoemd. Wanneer een afbeelding wordt gemaakt, heeft deze een specifiek aantal pixels. Bij het vergroten of verkleinen worden pixels toegevoegd of verwijderd om de afmetingen, resolutie en bestandsgrootte van de afbeelding te wijzigen.
* **Verhouding:**
Het handhaven van de hoogte-breedteverhouding (de verhouding tussen breedte en hoogte) is van cruciaal belang om vervorming te voorkomen. Of u nu een afbeelding groter (groter of kleiner (kleiner) maakt, het behoud van de hoogte-breedteverhouding zorgt voor visuele consistentie.
* **Overwegingen van de Kwaliteit:**
Het wijzigen van het formaat kan van invloed zijn op de afbeeldingskwaliteit. Vermijd drastisch opschalen, omdat dit tot pixelvorming kan leiden. In plaats daarvan kunt u de afbeelding op grotere grootte en met een hogere resolutie weergeven. Gebruik voor kleinere afbeeldingen de juiste gereedschappen om de resolutie te behouden.

##### Uitsnijden in plaats van vergroten/verkleinen

Uitsnijden en vergroten/verkleinen zijn technieken in dynamische media waarmee u afbeeldingen kunt transformeren op basis van verschillende gebruikssituaties, of het nu gaat om het maken van miniaturen, afbeeldingen in de productweergave of banners.

* **het Uitsnijden:**
Hierbij wordt een deel van een afbeelding verwijderd om de compositie en het kader te wijzigen. Het verandert de totale afmetingen niet, maar richt zich op een specifiek gebied.
* **het Resizing:**
Hiermee past u de afmetingen, resolutie en bestandsgrootte van de volledige afbeelding aan met behoud van de hoogte-breedteverhouding.

Laten we een gebruiksgeval onderzoeken dat de volgende afbeelding van de woonkamer omvat:

* **Origineel levende kamerbeeld:**
  [&#x200B; https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Duimnagel (200 px x 200 px):**
Een kleinere versie die geschikt is voor snel laden of weergeven.
  [&#x200B; https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&fit=crop)
* **Duimnagel met gewas (200 px x 200 px):**
Uitgesneden om de focus op het zacht gebied te richten.
  [&#x200B; https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&cropN=.24,.24,.6,.72&fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&hei=200&cropN=.24,.24,.6,.72&fit=crop)
* **beeld van de vertoningsvertoning van het Product (800 px x 600 px):**
Uitgesneden en vergroot of verkleind om de sofa te tonen.
  [&#x200B; https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&hei=600&cropN=.24,.24,.6,.72&fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&hei=600&cropN=.24,.24,.6,.72&fit=crop)
* **Banner (1720 px x 820 px):**
Voortgekomen uit de oorspronkelijke afbeelding, waarbij de ruimte wordt benadrukt.
  [&#x200B; https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&hei=820&cropN=0,.1,1,1&fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&hei=820&cropN=0,.1,1,1&fit=crop)

Voel u vrij om deze variaties voor uw specifieke behoeften te onderzoeken.
Wilt u meer weten over de opdrachten in een URL? Ga naar [&#x200B; verwijzing van het Bevel &#x200B;](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### GIF-afbeeldingen leveren

**Bedrijfs geval:** *GIFs van de Stroom gebruikend Dynamische Media*

U kunt GIF&#39;s uploaden en leveren via Dynamic Media. U rendert een geanimeerde GIF door `is/image` te vervangen door `is/content` in de URL. Als u bijvoorbeeld `abc.gif` hebt geüpload, gebruikt u het volgende:

* Dit URL-pad geeft een statische weergave van de GIF:

  ```
  https://your.domain.com/is/image/yourfolder/abc
  ```

* Met dit URL-pad wordt de animatieweergave van de GIF weergegeven:

  ```
  https://your.domain.com/is/content/yourfolder/abc
  ```

>[!NOTE]
>
>Wanneer u `is/content` gebruikt in het URL-pad, worden opdrachten voor afbeeldingstransformatie niet toegepast op het element.

### Een video voor mijn website publiceren

**Bedrijfs geval:** *publiceert snel een video voor een marketing plaats.*

* **selecteer een videoprofiel:**
Selecteer eerst in Dynamische media een geschikt videoprofiel. U kunt voor het *Aangepaste Video Coderen* profiel kiezen beschikbaar in AEM Assets onder VideoProfielen. Deze vooraf gedefinieerde coderingsinstellingen zorgen ervoor dat de video is geoptimaliseerd voor afspelen op verschillende apparaten en onder verschillende bandbreedteomstandigheden. U kunt ook uw eigen adaptief videoprofiel maken.
* **wijs het profiel toe:**
Wijs het gekozen videoprofiel toe aan de mappen waarin de video wordt geüpload. Met deze stap zorgt u ervoor dat de juiste coderingsinstellingen worden toegepast tijdens het uploaden.
* **upload de originele video:**
Upload het originele videobestand. Zorg ervoor dat het een video met hoge resolutie van goede kwaliteit is. Hoe beter de bronvideo, hoe beter het uiteindelijke resultaat.
* **Voorproef en publiceert:**
Bekijk een voorvertoning van de video, zodat u zeker weet dat alles er naar behoren uitziet. Ga door en publiceer de opmerking als u tevreden bent. Deze stap maakt de video toegankelijk voor uw publiek.
* **Verbinding of bedt in:**
Na publicatie hebt u twee opties.

   * **Verbinding direct:**
Gebruik de opgegeven URL om rechtstreeks te koppelen aan de video. Hyperlink het geschikt op uw marketingsite.
   * **bed de video in:**
Kopieer de ingesloten code en plak deze in de HTML van de webpagina waar u de video wilt weergeven. Hierdoor kan de video rechtstreeks op uw site worden afgespeeld.

Meer informatie? Ga naar [&#x200B; Video &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Video&#39;s configureren voor optimale kwaliteit en betrokkenheid

**Bedrijfs geval:** *de video&#39;s van de Opstelling voor de beste kwaliteit en de betrokkenheid.*

Om de beste kwaliteit en betrokkenheid voor uw video&#39;s te garanderen, kunt u overwegen een combinatie van de volgende strategieën voor best practices te implementeren:

* **gebruik ingebouwde HTML5 VideoKijker:**
Dynamische media HTML5 Video Viewer-voorinstellingen zijn robuuste videospelers. U kunt deze gebruiken om algemene problemen te voorkomen die samenhangen met het afspelen van HTML5-video en mobiele apparaten.
Deze voorinstellingen bieden oplossingen voor uitdagingen zoals het leveren van adaptieve bitsnelheden bij het streamen en het beperkte bereik van de desktopbrowser.
Meer informatie? Ga naar [&#x200B; Beste praktijken: Gebruikend HTML 5 videokijker &#x200B;](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Profiles van de Video van Media van het Gebruik Dynamische:**
Videoprofielen in Dynamic Media helpen u bij efficiënt videobeheer, consistente kwaliteit en adaptieve streaming.
Meer informatie? Ga naar [&#x200B; Dynamische VideoProfielen van Media &#x200B;](/help/assets/dynamic-media/video-profiles.md).

* **volg Beste praktijken voor Video Coderen:**
Hiermee past u videocoderingsprofielen toe die de oorspronkelijke videokwaliteit behouden zonder dat er tijdens het coderen buitensporig veel downscaling plaatsvindt.
Meer informatie? Ga naar [&#x200B; Beste praktijken voor het coderen van video&#39;s &#x200B;](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **keur het adaptieve stromen in plaats van progressief stromen goed:**
Bij adaptieve streaming wordt de videokwaliteit aangepast op basis van de snelheid en mogelijkheden van de internetverbinding van de kijker.
Er worden protocollen gebruikt, zoals HLS (Live HTTP-streaming) of DASH (`Dynamic Adaptive Streaming over HTTP`), voor een optimale afspeelkwaliteit.
In tegenstelling tot progressieve streaming, die lineaire, adaptieve streaming video levert, minimaliseert buffering en biedt een naadloze kijkervaring.

### Video&#39;s internationaliseren voor meertalig gebruik

**Bedrijfs geval:** *maak video&#39;s klaar voor meertalige consumptie.*

Het internationaliseren van video&#39;s voor meertalig gebruik is essentieel voor het bereiken van een wereldwijd publiek. Dynamische media biedt functies die u kunnen helpen dit doel te bereiken.

* **upload uw video&#39;s:**
   * Maak eerst een videocoderingsprofiel. U kunt het vooraf gedefinieerde profiel voor adaptieve videocodering gebruiken dat bij Dynamische media wordt geleverd, of uw eigen aangepaste profiel maken.
   * Koppel het videoverwerkingsprofiel aan een of meer mappen waarin u uw primaire bronvideo&#39;s uploadt.
   * Upload uw primaire bronvideo&#39;s naar deze mappen. Dynamische media codeert deze op basis van het toegewezen videoverwerkingsprofiel.
   * Dynamische media biedt voornamelijk ondersteuning voor korte video&#39;s (tot 30 minuten) met een minimale resolutie van meer dan 25 × 25. Videobestanden van maximaal 15 GB kunnen elk worden geüpload1.

* **beheer uw video&#39;s:**
   * Organiseer, doorblader, en onderzoek videoactiva binnen AEM.
   * Video-elementen voorvertonen en publiceren.
   * Bekijk de bronvideo en de bijbehorende gecodeerde vertoningen samen met de bijbehorende miniaturen.
   * Bewerk video-eigenschappen, zoals titel, beschrijving en tags2.

* **Localization:**
   * Maak audiotracks en ondertitels voor elke doelgeografie/taal.
   * Voeg deze audio- en ondertitelingstracks vanuit de AEM-interface toe aan uw video&#39;s.
   * Wanneer gebruikers de video&#39;s afspelen, kunnen ze hun voorkeurstaal voor audio en ondertitels selecteren.

* **het Publiceren:**
   * Als u AEM gebruikt als WCM-systeem (Web Content Management), kunt u rechtstreeks video&#39;s toevoegen aan uw webpagina&#39;s.
   * Als u een WCM-systeem van derden gebruikt, kunt u video&#39;s op uw webpagina&#39;s koppelen of insluiten met behulp van URL&#39;s of insluitcodes.

Meer informatie? Ga naar [&#x200B; Ongeveer veelvoudige titel en audiospoorsteun voor video&#39;s in Dynamische Media &#x200B;](/help/assets/dynamic-media/video.md#about-msma).


## Middelen leveren aan klanten

### Afbeeldingsgrootten optimaliseren en laadtijden van pagina&#39;s minimaliseren

**Bedrijfs geval:** *optimaliseer de grootte van beelden voor om het even welke browser of het scherm en verminder tijd van de paginalading.*

Dynamic Media Smart Imaging is een krachtig hulpmiddel dat de prestaties van de afbeeldingslevering verbetert door de indeling, grootte en kwaliteit van de afbeelding automatisch te optimaliseren op basis van de browsermogelijkheden van de client.

Adobe raadt u aan de mogelijkheden van Smart Imaging te gebruiken in plaats van de afbeeldingsindeling handmatig in te stellen op `webp` of `avif` . Dit is de reden waarom:

* **Browser verenigbaarheid:**
Slimme afbeeldingen zorgen ervoor dat de geleverde afbeeldingsindeling compatibel is met de browser van de gebruiker.
* **Optimale compressie:**
Het selecteert het beste formaat voor compressie die op specifieke browser, netwerkvoorwaarden, en het schermresolutie wordt gebaseerd.
* **Moderne formaten:**
Hoewel `avif` een nieuwere indeling is die betere compressie biedt, wordt deze nog niet overal in browsers ondersteund.
* **Beste praktijken:**
Om de beste indeling voor het web te garanderen, kunt u Slim beeld gebruiken om de indeling te selecteren in plaats van handmatig met de opdrachten `fmt=webp` of `fmt=avif` .

Door op Smart Imaging te vertrouwen, kunt u ervoor zorgen dat uw afbeeldingen zo efficiënt mogelijk worden geleverd, op maat van de bladeromgeving van elke gebruiker. Deze aanpak vereenvoudigt het proces en kan leiden tot betere prestaties op het gebied van het laden van afbeeldingen en de algehele gebruikerservaring.

Meer informatie? Ga naar [&#x200B; Slimme Beeldvorming &#x200B;](/help/assets/dynamic-media/imaging-faq.md).

### Na levering van activa aan klanten

**Bedrijfs geval:** *na het publiceren van nieuwe inhoud of het beschrijven van bestaande inhoud, hoe kan het worden gewaarborgd dat de veranderingen onmiddellijk op CDN verschijnen?*

De CDN (Content Delivery Network) plaatst dynamische media-elementen in cache, zodat deze snel aan klanten kunnen worden geleverd. Wanneer deze middelen worden bijgewerkt, is het belangrijk dat de wijzigingen onmiddellijk op de website van kracht worden. Door de CDN-cache leeg te maken of te wissen, kunnen elementen die door Dynamic Media worden geleverd, snel worden bijgewerkt. Deze benadering elimineert de behoefte om op het geheime voorgeheugen te wachten die op de waarde van TTL (Tijd aan Levend) wordt gebaseerd verlopen, die typisch aan tien uren wordt geplaatst. Afhankelijk van uw specifieke gebruiksgeval, kunt u de montages van CDN TTL (Tijd aan Levend) dienovereenkomstig bijwerken.

Meer informatie? Ga naar [&#x200B; ongeldig maakt het CDN geheime voorgeheugen als Dynamische Media &#x200B;](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md).

