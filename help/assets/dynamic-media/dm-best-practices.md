---
title: Aanbevolen procedures voor Dynamic Media
description: Meer informatie over de beste praktijken in Dynamic Media wanneer het gaat om het werken met beelden en video.
contentOwner: Rick Brough
products: Experience Manager as a Cloud Service
topic-tags: introduction,administering
content-type: reference
feature: Adaptive Streaming, Best Practices, Smart Imaging, Image Profiles, Rulesets, Viewers, Smart Crop, SEO Optimization, Publishing, Video, Renditions, Asset Management
role: User, Admin
mini-toc-levels: 4
exl-id: 39e491bb-367d-4c72-b4ca-aab38d513ac5
source-git-commit: de1116ee39024d30e14838f8b36f9ab087a45f85
workflow-type: tm+mt
source-wordcount: '3571'
ht-degree: 0%

---

# Aanbevolen procedures voor Dynamic Media{#about-dm-best-practices}

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

Organisaties worden geconfronteerd met een explosie van kanalen en apparaten om contact met gebruikers te maken. De reis van de klant omvat fysieke winkels, Web, mobiel, sociale media, e-mail, en handel. Om aan deze vraag te voldoen, biedt Dynamic Media op Adobe Experience Manager (AEM) een uitgebreide oplossing. Het optimaliseert levering van activa, behandelt verpersoonlijking, en verzekert verenigbare, prestaties, en merk-gerichte ervaringen over kanalen en apparaten.

Enkele van de belangrijkste elementen van Dynamic Media zijn:

* **Eén bestandsaanpak:** In Dynamic Media slaat u één primair bronbestand op. Alle groottevariaties en visuele effecten worden op het moment van levering dynamisch gemaakt en geoptimaliseerd. Deze benadering bespaart opslagkosten en elimineert werkstroomcomplexiteit.
* **Echt globaal:** Met Smart Imaging, toegepast tijdens het leveren van inhoud, worden de afbeeldingsgrootte en het paginagewicht aanzienlijk verminderd zonder dat dit ten koste gaat van de visuele kwaliteit. Deze is geoptimaliseerd voor netwerkbandbreedte en pixelverhoudingen van apparaten.
* **Door AI aangedreven:** Slim uitsnijden, een door AI aangedreven functie, automatiseert het uitsnijden van foto&#39;s en videointeressepunten. Het elimineert handeninspanning en schalen efficiënt voor bedrijfsgebruik.
* **Eenvoudige video:** Upload primaire bronvideo&#39;s naar Dynamic Media en streep ze adaptief over meerdere talen met beschrijvende audio.
* **De viewerbibliotheek van de ervaring:** Pas de kijkers van de merkervaring voor beelden en video&#39;s aan. Deze viewers integreren naadloos in uw digitale ervaringen.
* **Ondersteuning voor nieuwe bestandsindelingen:** Dynamic Media maakt het mogelijk 3D-ervaringen en panoramische ervaringen op te doen.

Terwijl u de [Dynamic Media Journey](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-journey/dm-journey-part1)Door de geconsolideerde lijst met beste praktijken hieronder te herzien, kunt u de mogelijkheden optimaal benutten. Pas deze beste praktijken van Dynamic Media aan uw specifieke context en projectvereisten aan zodat kunt u uw ervaringen over kanalen en apparaten optimaliseren.

<!-- In Dynamic Media on AEM, there are sets of methods, techniques, and guidelines that can help you maximize the potential of your rich media content. These best practices can lead to optimal results and increase efficiency in your use of Dynamic Media. They represent the most efficient and effective courses of action in a particular situation. They also unlock high value for your audience and deliver high-quality, engaging content. -->

>[!IMPORTANT]
>
>De beste praktijken van Dynamic Media in dit artikel kunnen in tijd evolueren aangezien de nieuwe technologieën in Dynamic Media verschijnen. De informatie hieronder is actueel voor de nieuwste versie van Dynamic Media.


## Middelen in Dynamic Media plaatsen

**Bedrijfscase:** *Efficiënt beheer van grote volumes met middelen en zorg ervoor dat alleen relevante, goedgekeurde inhoud aan eindgebruikers wordt geleverd.*

Stroomlijn uw beheer van grote aantallen activa efficiënt. Zorg ervoor dat alleen de juiste, geoorloofde inhoud uw eindgebruikers bereikt met Dynamic Media&#39;s **Selectieve synchronisatie** en **Selectieve publicatie** functies.

* **Selectieve synchronisatie:**
Een proactieve functie waarmee u kunt kiezen welke elementen u wilt synchroniseren met Dynamic Media. U kunt bijvoorbeeld alleen die mappen synchroniseren die elementen bevatten waarvoor de definitieve goedkeuring is verleend. Deze workflow helpt u te controleren welke middelen worden voorbereid voor levering aan uw klanten.

* **Selectieve publicatie:**
Nadat u uw elementen hebt gesynchroniseerd, kunt u met Selectief publiceren bepalen welke elementen zichtbaar zijn voor uw klanten. Dit betekent dat u kunt bepalen welke goedgekeurde middelen daadwerkelijk via uw kanalen worden geleverd, zodat uw klanten alleen de beste en meest relevante inhoud zien.

Deze twee beste praktijken helpen u betere controle, bestuur, en productiviteit over uw rijke-media inhoud bereiken.

Meer informatie? Ga naar [Selectieve publicatie op mapniveau in Dynamic Media configureren](/help/assets/dynamic-media/selective-publishing.md).


## Elementen voorbereiden voor levering

### Uw elementen ordenen

**Bedrijfscase:** *Elementen efficiënt ordenen om workflows te stroomlijnen.*

Voor efficiënte middelenorganisatie die workflows stroomlijnt, gebruikt u een of meer van de volgende aanbevolen procedures:

* **Elementen ordenen in mappen:**
Bij het ordenen van elementen moeten deze worden ingedeeld in mappen, net als bij het ordenen van bestanden op een computer. Een correcte naamgeving, structurering van submappen en bestandsbeheer in deze mappen zijn van cruciaal belang voor een efficiënte verwerking van bedrijfsmiddelen. Het implementeren van systematische naamconventies en praktijken voor metagegevens maximaliseert het nut van de gegevensopslagruimte voor digitale middelen.
Meer informatie? Ga naar [Elementen in mappen ordenen](/help/assets/organize-assets.md#organize-using-folders).
* **Elementen ordenen met tags:**
Tags toevoegen verbetert de zoekbaarheid, het maken van verzamelingen en de positie van zoekopdrachten. Adobe Sensei AI maakt gebruik van een zelfstudie-algoritme voor nauwkeurige codering, zodat elementen snel kunnen worden opgehaald. Adobe Sensei herkent en wijst ook relevante tags, waaronder aangepaste tags, toe aan bedrijfsmiddelen, waardoor het beheer van bedrijfsmiddelen wordt vereenvoudigd met automatische, beschrijvende tags.
Meer informatie? Ga naar [Elementen ordenen met tags](/help/assets/organize-assets.md#use-tags-to-organize-assets).
* **Elementen indelen als verzamelingen:**
Met Dynamic Media en Experience Manager Assets kunt u op efficiënte wijze middelen verzamelen, bewerken en delen tussen gebruikers. U kunt diverse inzamelingstypes, met inbegrip van statische lijsten en dynamische, op onderzoek-gebaseerde compilaties vestigen. Deze inzamelingstypes kunnen over diverse plaatsen met klantgerichte toegang en het uitgeven rechten worden gedeeld.
Meer informatie? Ga naar [Elementen ordenen als verzamelingen](/help/assets/manage-collections.md).
* **Elementen ordenen met behulp van profielen:**
Een verwerkingsprofiel automatiseert de verwerking van middelen in aangewezen omslagen, die organisatie stroomlijnen. Door het standaardiseren van metagegevens, bestandsnamen en mapstructuren kunt u deze profielen consistent en nauwkeurig toepassen terwijl de verzameling van digitale elementen wordt uitgebreid.
Meer informatie? Ga naar [Elementen ordenen met behulp van profielen](/help/assets/organize-assets.md#organize-to-use-profiles).



### De kwaliteit van afbeeldingen optimaliseren

**Bedrijfscase:** *Haal afbeeldingen van goede kwaliteit op uit Dynamic Media.*

Om de beeldkwaliteit te verbeteren, moeten verschillende factoren zorgvuldig in overweging worden genomen. Het kan een tijdintensief proces zijn. Nochtans, zijn er sommige beproefde-en-ware praktijken die u kunnen helpen wenselijke resultaten bereiken. Tot de beste werkwijzen behoren onder andere het optimaliseren van de afbeelding, het verscherpen van afbeeldingen en de beste afbeeldingsindelingen die u kunt gebruiken.

Meer informatie? Ga naar [Aanbevolen procedures voor het optimaliseren van de kwaliteit van uw afbeeldingen](/help/assets/dynamic-media/best-practices-for-optimizing-the-quality-of-your-images.md).

Omdat de perceptie van beeldkwaliteit van persoon tot persoon verschilt, is soms een systematische benadering van experimenten essentieel voor het bereiken van gewenste resultaten. Adobe Experience Manager ondersteunt dit proces met meer dan 100 Dynamic Media-opdrachten voor het verbeteren van afbeeldingen.

Meer informatie? Controle [Dynamic Media-momentopname](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot) (3 minuten, 17 seconden).

Als u de invloed van deze verschillende opdrachten op de afbeeldingskwaliteit wilt beoordelen, kunt u een afbeelding uploaden naar Dynamic Media, de interface van het gereedschap op de opgegeven URL gebruiken en de opdrachten toepassen die u wilt uitproberen.

Wil je het uitproberen? Starten [Dynamic Media-momentopname](https://snapshot.scene7.com/)

### Standaardiseren op stijlen die op afbeeldingen zijn toegepast

**Bedrijfscase:** *De stijl en transformatie die op mijn afbeeldingselementen zijn toegepast, op efficiënte wijze standaardiseren.*

In Dynamic Media kunt u regelmatig voorinstellingen voor afbeeldingen gebruiken, zodat u de afbeeldingsformaten, indelingen en eigenschappen op consistente en dynamische wijze kunt aanpassen. Beschouw een voorinstelling voor afbeeldingen als een macro: het is een benoemde set opdrachten voor vergroten/verkleinen en opmaken. Als uw site bijvoorbeeld productafbeeldingen in verschillende formaten en formaten nodig heeft, met specifieke compressie voor desktops en mobiele apparaten, wordt dit proces efficiënt geautomatiseerd met behulp van Voorinstellingen voor afbeeldingen.

Wil je het uitproberen? Ga naar [Basisprincipes van het maken van voorinstellingen voor afbeeldingen om elementen te renderen](/help/assets/dynamic-media/dm-journey-part2.md#dm-journey-e)

### De focus en het beeld van afbeeldingen en video&#39;s aanpassen

**Bedrijfscase:** *Zorg ervoor dat het belangrijkste aandachtspunt van mijn afbeeldingen of video&#39;s op alle apparaten blijft staan.*

Smart Crop is een functie in Dynamic Media die gebruikmaakt van Adobe Sensei, het AI-framework van Adobe en het framework voor machinaal leren, om het bijsnijden van afbeeldingen en video&#39;s te automatiseren. Het detecteert en richt zich op intelligente wijze op het hoofdonderwerp of het belangrijkste aandachtspunt in een afbeelding of video. Deze intelligentie zorgt ervoor dat het brandpunt op verschillende schermgrootten op desktopcomputers en mobiele apparaten wordt gehandhaafd.

U kunt het beste een afbeeldingsprofiel maken met Slim uitsnijden. In het profiel kunt u verschillende schermgrootten definiëren en Adobe Sensei de rest laten doen, zodat uw afbeeldingen en video&#39;s altijd zijn geoptimaliseerd voor het apparaat van de viewer.

Meer informatie? Controle [Slim uitsnijden gebruiken met AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minuten, 35 seconden) en [Dynamic Media Smart Crop for Video gebruiken](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/video/dynamic-media-smart-crop-video) (6 minuten, 22 seconden).

### SEO-waarderingen verbeteren

**Bedrijfscase:** *Configureer Dynamic Media voor betere SEO-waarderingen.*

Gebruik regelmatig de volgende aanbevelingen om ervoor te zorgen dat uw afbeeldingen effectief bijdragen aan uw algemene SEO-strategie.

* **Betekenisvolle namen van afbeeldingsbestanden:**
Gebruik beschrijvende bestandsnamen die de afbeeldingsinhoud weerspiegelen. Bijvoorbeeld:
   * gebruiken `myCompany-Silver-Wrist-Watch`
   * *vermijden* `myCompany_Silver_Wrist_Watch` of `myCompanySilverWristWatch`

  Zodoende kunnen zoekprogramma&#39;s de context van de afbeelding begrijpen en de SEO verbeteren. Google geeft de voorkeur aan afbreekstreepjes boven onderstrepingstekens of spaties in een bestandsnaam. Vermijd ook het samenvoegen van woorden in een bestandsnaam.
* **Aangepast domein:**
Implementeer een aangepast domein dat uw bedrijf of merknaam bevat om de herkenning en het vertrouwen van merken te versterken. Bijvoorbeeld:
   * gebruiken `http://images.mycompany.com/is/image/companyname/`
   * *vermijden* `https://s7d1.scene7.com/is/image/folder/AdobeStock_28563982`
* **SEO-vriendelijke mapstructuur:**
Uw afbeeldingen ordenen in een mappenstructuur die uw bedrijfsnaam of merk bevat voor een betere indexering, zoals `http://images.mycompany.com/is/image/companyname/`.
* **Dynamic Media-regelsets:**
Leer hoe u URL&#39;s voorwaardelijk kunt transformeren op basis van verschillende factoren, waardoor SEO en gebruikerservaring worden verbeterd.
Meer informatie? Ga naar [Regelsets gebruiken om URL&#39;s te transformeren](/help/assets/dynamic-media/using-rulesets-to-transform-urls.md).
* **Slim beeld en Slim uitsnijden:**
Gebruik de functies Slim beeld en Slim uitsnijden in Dynamic Media om geoptimaliseerde en responsieve afbeeldingen te leveren. Hierdoor worden niet alleen de laadtijden van de pagina verbeterd, maar wordt ook een positieve bijdrage geleverd aan SEO-waarderingen.
Meer informatie? Ga naar [Slimme afbeeldingen](/help/assets/dynamic-media/imaging-faq.md), of wacht [Slim uitsnijden gebruiken met AEM Assets Dynamic Media](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) (6 minuten, 35 seconden).

Houd er rekening mee dat deze aanbevolen procedures goed overeenkomen met de SEO-tips voor Google-afbeeldingen. Dergelijke praktijken benadrukken het belang om context en helderheid aan onderzoeksmotoren door juiste noemende overeenkomsten, gestructureerde gegevens, en geoptimaliseerde beeldlevering te verstrekken.

Meer informatie? Ga naar [Aanbevolen werkwijzen voor URL-structuur voor Google](https://developers.google.com/search/docs/crawling-indexing/url-structure) en [Aanbevolen werkwijzen voor SEO-afbeeldingen in Google](https://developers.google.com/search/docs/appearance/google-images)


### Afbeeldingen dynamisch verbeteren en visuele effecten maken met behulp van opdrachten

**Bedrijfscase:** *Pas rijke visuele effecten toe op afbeeldingen.*

Dynamic Media beschikt over een aantal opdrachten waarmee u afbeeldingen kunt verbeteren en visuele effecten dynamisch kunt maken, zonder dat u meerdere statische elementen nodig hebt. Hieronder volgt een korte uitleg van een aantal van deze processen en enkele voorbeelden die u kunnen helpen:

#### Effecten in de bronafbeelding

| Taak | Wat moet u doen? |
| --- | --- |
| **De originele afbeelding uploaden en publiceren** | ・ Begin door de originele afbeelding naar Dynamic Media te uploaden.<br>・ Zorg ervoor dat het via een URL wordt gepubliceerd en toegankelijk is.<br>・ In dit voorbeeld wordt een voorraadafbeelding van een horloge met een witte achtergrond (laten we het &quot;Afbeelding X&quot; noemen) geüpload naar Dynamic Media.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer) |
| **Een masker maken** | ・ Ontwikkelen een masker dat het onderwerp (het gebied waar u effecten wilt toepassen) en de achtergrond (het gebied dat u wilt wijzigen) definieert.<br>[https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps](https://s7g2.scene7.com/is/image/genaibeta/watch-silver-offer-maskps)<br>・ Maskers zijn doorgaans grijswaardenafbeeldingen, waarbij wit staat voor het onderwerp en zwart voor de achtergrond. U kunt maskers maken met gereedschappen zoals Adobe Photoshop.<br>Meer informatie? Ga naar [Een snelmasker maken en bewerken in Photoshop](https://helpx.adobe.com/in/photoshop/using/create-temporary-quick-mask.html).<br>・ Voor &quot;Beeld X,&quot;creeer een masker dat precies het onderwerp beschrijft u wilt verbeteren. Bijvoorbeeld een persoon, een object, enzovoort. |
| **Dynamic Media URL-opdrachten toepassen op effecten** | Nadat u het masker hebt, gebruikt u URL-opdrachten om effecten als slagschaduwen toe te passen of wijzigt u de achtergrondkleur in &quot;Afbeelding X&quot;. Hier volgen twee voorbeelden:<br><br> ・ **Slagschaduweffect:**<br> Als u een slagschaduweffect langs de grens van het onderwerp wilt toevoegen, bewerkt u de URL als volgt:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;effect=-1&amp;pos=100,100&amp;op_blur=75&amp;op_grow=1&amp;opac=25)<br>In deze URL, `$shadow$` de parameter het schaduweffect creëert, en `color=0,0,0` Hiermee stelt u de schaduwkleur in op zwart.<br>・ **Wijziging van achtergrondkleur:**<br> Als u de achtergrondkleur wilt wijzigen, gebruikt u de URL met een andere achtergrondkleurwaarde:<br>[https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0](https://s7g10.scene7.com/is/image/genaibeta/watch-silver-offer?mask=watch-silver-offer-maskps&amp;maskUse=invert&amp;maskUse=invert&amp;color=255,255,0)<br> In dit voorbeeld: `color=255,255,0` stelt de achtergrondkleur in op geel. Bewerk de achtergrond in een specifieke kleur voor visuele effecten. |

#### Een afbeeldingsrand toevoegen

Met Dynamic Media kunt u afbeeldingen rechtstreeks via URL&#39;s manipuleren. Dit is een krachtig hulpmiddel voor het maken van dynamische digitale ervaringen. Hieronder volgen enkele voorbeelden. Laten we beginnen met de volgende URL van de oorspronkelijke afbeelding: [https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel).

| Taak | Wat moet u doen? |
| --- | --- |
| **Witte rand** | Gebruik de volgende URL om een witte rand toe te voegen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10)<br>In deze URL, `extend=10,10,10,10` parameter geeft de randgrootte van tien pixels aan alle zijden aan. |
| **Vervagen langs de witte rand** | Als u een vervagingseffect langs de witte rand wilt toevoegen, kunt u de URL als volgt bewerken:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;op_blur=60&amp;color=0,0,0)<br>In deze URL, `effect=-1` parameter het vervagingseffect toepast, en `op_blur=60` bepaalt de intensiteit van de vervaging. |
| **Slagschaduweffect langs de buitenste rand** | Gebruik de volgende URL om een slagschaduweffect langs de buitenste rand toe te voegen:<br>[https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0](https://s7g2.scene7.com/is/image/genaibeta/ocean-facing-hotel?size=400,400&amp;extend=10,10,10,10&amp;effect=-1&amp;$shadow$&amp;color=0,0,0)<br>De `$shadow$` de parameter het schaduweffect creëert, en `color=0,0,0` Hiermee stelt u de schaduwkleur in op zwart. |

U kunt met deze URL&#39;s experimenteren om de gewenste visuele effecten te bereiken.

#### Afbeeldingsoverlays maken

Als u een logo of pictogram op een bestaande afbeelding wilt plaatsen, biedt Dynamic Media een eenvoudige manier om dit te bereiken met URL-opdrachten. Laten we de stappen afbreken.

| Stap | Wat moet u doen? |
| --- | --- |
| **De basisafbeelding uploaden en publiceren** | Eerst uploadt en publiceert u de basisafbeelding waarop u het logo of pictogram wilt plaatsen. U kunt elke afbeelding als basis gebruiken.<br>Hier ziet u bijvoorbeeld een basisafbeelding:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa). |
| **Het logo of de pictogramafbeelding uploaden en publiceren** | Vervolgens uploadt en publiceert u de afbeelding die u over de basisafbeelding wilt plaatsen. Deze afbeelding moet een transparant PNG-bestand zijn met het logo of pictogram dat u wilt bedekken.<br>Hier ziet u de transparante PNG-afbeelding van een sterobject met transparantie-effecten die wordt overschreven:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorate-star](https://s7g2.scene7.com/is/image/genaibeta/decorate-star) |
| **De Dynamic Media-URL toepassen** | Maak nu een Dynamic Media-URL waarin de basisafbeelding en het logo of de pictogramafbeelding worden gecombineerd. U kunt URL-opdrachten gebruiken om dit effect te bereiken.<br>De URL-structuur ziet er ongeveer als volgt uit:<br>[https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa?layer=1&amp;src=decorate-star&amp;scale=1.25&amp;posN=0.33,-.25&amp;fmt=png)<br>waar<br>・ `hotspotRetailBaseImage` is de basisafbeelding.<br>・ `starxp` Dit is het logo/pictogram.<br>・ `layer=1` Hiermee geeft u op dat het logo of pictogram in een laag over de basisafbeelding moet worden geplaatst.<br>・ `scale=1.25` past de grootte van het logo/pictogram aan.<br>・ `posN=0.33,-.25` Hiermee bepaalt u de positie van het logo/pictogram ten opzichte van de basisafbeelding.<br>・ `fmt=png` zorgt ervoor dat de uitvoer de PNG-indeling heeft. |

Meer informatie? Ga naar [src](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-src) voor meer informatie over de `src` en andere URL-opdrachten van Dynamic Media.


#### Promotietekst overschrijven

Hieronder vindt u de stappen voor het bedekken van promotietekstberichten op afbeeldingen met HTML en CSS.

| Stap | Wat moet u doen? |
| --- | --- |
| **De basisafbeelding uploaden en publiceren** | Eerst uploadt en publiceert u de basisafbeelding waarop u de tekst wilt plaatsen. U kunt elke gewenste afbeelding gebruiken. Hier ziet u bijvoorbeeld een voorbeeld van een basisafbeelding:<br>[https://s7g2.scene7.com/is/image/genaibeta/leather-sofa](https://s7g2.scene7.com/is/image/genaibeta/leather-sofa)<br> |
| **Dynamic Media-tekstoperatoren toepassen** | Met Dynamic Media kunt u tekstoperatoren toepassen om dynamische tekst rechtstreeks op de afbeelding te bedekken. De volgende voorbeeld-URL toont deze mogelijkheid aan:<br>[https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=0 3333&amp;wid=600&amp;hei=600](https://s7g10.scene7.com/is/image/genaibeta/leather-sofa?layer=1&amp;posN=-0.3,-0.455&amp;text=%7b\rtf1\ansi%7b\fonttbl%7b\f0+Arial;%7d%7d%7b\colortbl+\red255\green255\blue255;%7d\copyfit1000\vertalc\qc%7b\cf0\fs42+New+Collection%7d%7d&amp;size=370,70&amp;textAttr=130&amp;bgcolor=0 3333&amp;wid=600&amp;hei=600) |

#### Vergroten/verkleinen en uitsnijden voor verschillende toepassingen

##### Basisprincipes van afbeeldingsgrootte wijzigen

Bij het vergroten of verkleinen van afbeeldingen worden de afmetingen, resolutie en bestandsgrootte van een afbeelding gewijzigd. Hieronder volgen enkele belangrijke punten die u in overweging wilt nemen:

* **Pixelsamenstelling:**
Digitale afbeeldingen bestaan uit kleine stippen, pixels genoemd. Wanneer een afbeelding wordt gemaakt, heeft deze een specifiek aantal pixels. Bij het vergroten of verkleinen worden pixels toegevoegd of verwijderd om de afmetingen, resolutie en bestandsgrootte van de afbeelding te wijzigen.
* **Verhouding:**
Het handhaven van de hoogte-breedteverhouding (de verhouding tussen breedte en hoogte) is van cruciaal belang om vervorming te voorkomen. Of u nu een afbeelding groter (groter of kleiner (kleiner) maakt, het behoud van de hoogte-breedteverhouding zorgt voor visuele consistentie.
* **Kwaliteitsoverwegingen:**
Het wijzigen van het formaat kan van invloed zijn op de afbeeldingskwaliteit. Vermijd drastisch opschalen, omdat dit tot pixelvorming kan leiden. In plaats daarvan kunt u de afbeelding op grotere grootte en met een hogere resolutie weergeven. Gebruik voor kleinere afbeeldingen de juiste gereedschappen om de resolutie te behouden.

##### Uitsnijden in plaats van vergroten/verkleinen

Uitsnijden en vergroten/verkleinen zijn technieken in Dynamic Media waarmee u afbeeldingen kunt transformeren op basis van verschillende gebruikssituaties, of het nu gaat om het maken van miniaturen, afbeeldingen in de productweergave of banners.

* **Uitsnijden:**
Hierbij wordt een deel van een afbeelding verwijderd om de compositie en het kader te wijzigen. Het verandert de totale afmetingen niet, maar richt zich op een specifiek gebied.
* **Grootte wijzigen:**
Hiermee past u de afmetingen, resolutie en bestandsgrootte van de volledige afbeelding aan met behoud van de hoogte-breedteverhouding.

Laten we een gebruiksgeval onderzoeken dat de volgende afbeelding van de woonkamer omvat:

* **Originele afbeelding van de woonruimte:**
  [https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa](https://s7g2.scene7.com/is/image/genaibeta/decorative-room-sofa)
* **Miniatuur (200 x 200 px):**
Een kleinere versie die geschikt is voor snel laden of weergeven.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;fit=crop)
* **Miniatuur met uitsnijden (200 px x, 200 px):**
Uitgesneden om de focus op het zacht gebied te richten.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=200&amp;hei=200&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Afbeelding voor productweergave (800 px x 600 px):**
Uitgesneden en vergroot of verkleind om de sofa te tonen.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=800&amp;hei=600&amp;cropN=.24,.24,.6,.72&amp;fit=crop)
* **Banner (1720 px x 820 px):**
Voortgekomen uit de oorspronkelijke afbeelding, waarbij de ruimte wordt benadrukt.
  [https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop](https://s7g10.scene7.com/is/image/genaibeta/decorative-room-sofa?wid=1720&amp;hei=820&amp;cropN=0,.1,1,1&amp;fit=crop)

Voel u vrij om deze variaties voor uw specifieke behoeften te onderzoeken.
Wilt u meer weten over de opdrachten in een URL? Ga naar [Opdrachtverwijzing](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference).

### Een video voor mijn website publiceren

**Bedrijfscase:** *Publiceer snel een video voor een marketingsite.*

* **Selecteer een videoprofiel:**
Selecteer eerst in Dynamic Media een geschikt videoprofiel. U kunt kiezen voor de *Adaptieve videocodering* beschikbaar in AEM Assets onder Videoprofielen. Deze vooraf gedefinieerde coderingsinstellingen zorgen ervoor dat de video is geoptimaliseerd voor afspelen op verschillende apparaten en onder verschillende bandbreedteomstandigheden. U kunt ook uw eigen adaptief videoprofiel maken.
* **Wijs het profiel toe:**
Wijs het gekozen videoprofiel toe aan de mappen waarin de video wordt geüpload. Met deze stap zorgt u ervoor dat de juiste coderingsinstellingen worden toegepast tijdens het uploaden.
* **De originele video uploaden:**
Upload het originele videobestand. Zorg ervoor dat het een video met hoge resolutie van goede kwaliteit is. Hoe beter de bronvideo, hoe beter het uiteindelijke resultaat.
* **Voorvertonen en publiceren:**
Bekijk een voorvertoning van de video, zodat u zeker weet dat alles er naar behoren uitziet. Ga door en publiceer de opmerking als u tevreden bent. Deze stap maakt de video toegankelijk voor uw publiek.
* **Koppeling of insluiten:**
Na publicatie hebt u twee opties.
   * **Direct koppelen:**
Gebruik de opgegeven URL om rechtstreeks te koppelen aan de video. Hyperlink het geschikt op uw marketingsite.
   * **De video insluiten:**
Kopieer de ingevoerde insluitcode en plak deze in de HTML van de webpagina waar u de video wilt weergeven. Hierdoor kan de video rechtstreeks op uw site worden afgespeeld.

Meer informatie? Ga naar [Video](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/video).

### Video&#39;s configureren voor optimale kwaliteit en betrokkenheid

**Bedrijfscase:** *Stel video&#39;s in voor de beste kwaliteit en betrokkenheid.*

Om de beste kwaliteit en betrokkenheid voor uw video&#39;s te garanderen, kunt u overwegen een combinatie van de volgende strategieën voor best practices te implementeren:

* **Gebruik de ingebouwde HTML5 Video Viewer:**
De Dynamic Media HTML5 Video Viewer-voorinstellingen zijn robuuste videospelers. U kunt deze gebruiken om algemene problemen te voorkomen die samenhangen met het afspelen van HTML5-video en mobiele apparaten.
Deze voorinstellingen bieden oplossingen voor uitdagingen zoals het leveren van adaptieve bitsnelheden bij het streamen en het beperkte bereik van de desktopbrowser.
Meer informatie? Ga naar [Tips en trucs: De HTML 5-videoviewer gebruiken](/help/assets/dynamic-media/video.md#best-practice-using-the-html-video-viewer).

* **Dynamic Media-videoprofielen gebruiken:**
Videoprofielen in Dynamic Media helpen u bij efficiënt videobeheer, consistente kwaliteit en adaptieve streaming.
Meer informatie? Ga naar [Dynamic Media-videoprofielen](/help/assets/dynamic-media/video-profiles.md).

* **Volg de aanbevolen procedures voor videocodering:**
Hiermee past u videocoderingsprofielen toe die de oorspronkelijke videokwaliteit behouden zonder dat er tijdens het coderen buitensporig veel downscaling plaatsvindt.
Meer informatie? Ga naar [Aanbevolen werkwijzen voor het coderen van video&#39;s](/help/assets/dynamic-media/video.md#best-practices-for-encoding-videos).

* **Adaptieve streaming toepassen in plaats van progressieve streaming:**
Bij adaptieve streaming wordt de videokwaliteit aangepast op basis van de snelheid en mogelijkheden van de internetverbinding van de kijker.
Er worden protocollen gebruikt zoals HLS (Live HTTP-streaming) of DASH (`Dynamic Adaptive Streaming over HTTP`) om een optimale afspeelkwaliteit te garanderen.
In tegenstelling tot progressieve streaming, die lineaire, adaptieve streaming video levert, minimaliseert buffering en biedt een naadloze kijkervaring.

* **Schakel DASH in voor uw account (Digital Adaptive Streaming via HTTP):**
DASH levert dynamisch video-inhoud via adaptieve streaming.
Om DASH toe te laten, creeer een steunkaartje voor uw milieu.
Meer informatie? Ga naar [DASH inschakelen op uw Dynamic Media-account](/help/assets/dynamic-media/video.md#enable-dash).

### Video&#39;s internationaliseren voor meertalig gebruik

**Bedrijfscase:** *Maak video&#39;s klaar voor meertalig gebruik.*

Het internationaliseren van video&#39;s voor meertalig gebruik is essentieel voor het bereiken van een wereldwijd publiek. Dynamic Media biedt functies die u kunnen helpen dit doel te bereiken.

* **Uw video&#39;s uploaden:**
   * Maak eerst een videocoderingsprofiel. U kunt het vooraf gedefinieerde profiel voor adaptieve videocodering dat bij Dynamic Media wordt geleverd, gebruiken of uw eigen aangepaste profiel maken.
   * Koppel het videoverwerkingsprofiel aan een of meer mappen waarin u uw primaire bronvideo&#39;s uploadt.
   * Upload uw primaire bronvideo&#39;s naar deze mappen. Dynamic Media codeert deze op basis van het toegewezen videoverwerkingsprofiel.
   * Dynamic Media biedt voornamelijk ondersteuning voor korte video&#39;s (tot 30 minuten) met een minimale resolutie van meer dan 25 × 25. Videobestanden van maximaal 15 GB kunnen elk worden geüpload1.

* **Uw video&#39;s beheren:**
   * Organiseer, doorblader, en onderzoek videoactiva binnen AEM.
   * Video-elementen voorvertonen en publiceren.
   * Bekijk de bronvideo en de bijbehorende gecodeerde vertoningen samen met de bijbehorende miniaturen.
   * Video-eigenschappen bewerken, zoals titel, beschrijving en tags2.

* **Lokalisatie:**
   * Maak audiotracks en ondertitels voor elke doelgeografie/taal.
   * Voeg deze audio en ondertitelsporen aan uw video&#39;s van de AEM interface toe.
   * Wanneer gebruikers de video&#39;s afspelen, kunnen ze hun voorkeurstaal voor audio en ondertitels selecteren.

* **Publiceren:**
   * Als u AEM gebruikt als WCM-systeem (Web Content Management), kunt u rechtstreeks video&#39;s toevoegen aan uw webpagina&#39;s.
   * Als u een WCM-systeem van derden gebruikt, kunt u video&#39;s op uw webpagina&#39;s koppelen of insluiten met behulp van URL&#39;s of insluitcodes.

Meer informatie? Ga naar [Ondersteuning voor meerdere bijschriften en audiotracks voor video&#39;s in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) of wacht [Meerdere bijschriften en audiotracks toevoegen aan een video](https://delivery-p106302-e1008131.adobeaemcloud.com/adobe/assets/urn:aaid:aem:daf9a222-9f7f-4333-b167-98cb4c63a1f8/play) (1 minuten, 41 seconden).


## Middelen leveren aan klanten

### Afbeeldingsgrootten optimaliseren en laadtijden van pagina&#39;s minimaliseren

**Bedrijfscase:** *Optimaliseer de grootte van afbeeldingen voor elke browser of scherm en verkort de laadtijd van de pagina.*

Dynamic Media Smart Imaging is een krachtig hulpmiddel dat de prestaties van de afbeeldingslevering verbetert door de indeling, grootte en kwaliteit van de afbeelding automatisch te optimaliseren op basis van de browsermogelijkheden van de client.

Adobe raadt u aan de mogelijkheden van Smart Imaging te gebruiken in plaats van de afbeeldingsindeling handmatig in te stellen op `webp` of `avif`. Dit is de reden waarom:

* **Browsercompatibiliteit:**
Slimme afbeeldingen zorgen ervoor dat de geleverde afbeeldingsindeling compatibel is met de browser van de gebruiker.
* **Optimale compressie:**
Het selecteert het beste formaat voor compressie die op specifieke browser, netwerkvoorwaarden, en het schermresolutie wordt gebaseerd.
* **Moderne indelingen:**
while `avif` Het is een nieuwere indeling die betere compressie biedt. Deze indeling wordt nog niet overal in browsers ondersteund.
* **Tips en trucs:**
Om de beste voor het web geoptimaliseerde indeling te garanderen, kunt u Smart Imaging gebruiken om de indeling te selecteren in plaats van handmatig de opdrachten te gebruiken `fmt=webp` of `fmt=avif`.

Door op Smart Imaging te vertrouwen, kunt u ervoor zorgen dat uw afbeeldingen zo efficiënt mogelijk worden geleverd, op maat van de bladeromgeving van elke gebruiker. Deze aanpak vereenvoudigt het proces en kan leiden tot betere prestaties op het gebied van het laden van afbeeldingen en de algehele gebruikerservaring.

Meer informatie? Ga naar [Slimme afbeeldingen](/help/assets/dynamic-media/imaging-faq.md).
