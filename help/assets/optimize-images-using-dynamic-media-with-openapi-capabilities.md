---
title: Afbeeldingen optimaliseren met Dynamic Media met OpenAPI-mogelijkheden
description: Leer hoe u afbeeldingen vlak voor de openbare levering kunt optimaliseren met de optimalisatiefuncties van Dynamic Media met OpenAPI-mogelijkheden
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
exl-id: 7822732b-e2b9-4b35-b92b-cb7b31d84489
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---

# Afbeeldingen optimaliseren met Dynamic Media met OpenAPI-mogelijkheden{#Optimize-images-using-Dynamic-Media-with-OpenAPI-Capabilities}

[!DNL Dynamic Media with OpenAPI capabilities] biedt optimalisatiefuncties voor afbeeldingen, zoals [!DNL Smart Crop] , [!DNL Image Presets] en [!DNL Smart Imaging] . Deze mogelijkheden bieden responsieve beelden van hoge kwaliteit die snel worden geladen op verschillende apparaten en netwerken.

## Slim uitsnijden{#smart-crop-using-dynamic-media-with-openapi-capabilities}

[&#x200B; het Slimme Gewas &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request) is een dynamisch het rangschikken vermogen van [!DNL Dynamic Media with OpenAPI capabilities]. [!DNL Smart Crop] is een geavanceerde beeldverwerkingstechniek die door AI aangedreven inhoud-bewuste het bebouwen gebruikt om beelden voor diverse het schermgrootte intelligent uit te snijden terwijl het bewaren van de visuele context in bebouwde versies. De AI analyseert het beeld om het brandpunt of het voorgenomen punt van belang te identificeren, en dan het beeld automatisch om het brandpunt in alle bebouwde versies te behouden. [!DNL Smart Crop] is een belangrijk element van responsief ontwerp en biedt een voordelige en tijdbesparende manier om afbeeldingen uit te snijden.

Zie het [&#x200B; Dynamische Profiles van het Beeld van Media &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles) artikel leren hoe te [&#x200B; Slimme vertoningen van het Gewas &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#creating-image-profiles) in [!DNL Admin View] tot stand brengen, [&#x200B; hen op omslagen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#applying-an-image-profile-to-folders) toepassen, of [&#x200B; geeft vertoningen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#editing-the-smart-crop-or-smart-swatch-of-a-single-image) reeds op een beeld of een omslag uit. Leer om a [!DNL Smart Crop] stap voor stap in deze [&#x200B; video &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use) tot stand te brengen.

De parameter [!DNL Smart Crop] verwacht dat benoemde-smartcrop-profielen bestaan en zijn toegepast op het element. Zie [&#x200B; Slimme profielen van het Gewas &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request) om meer over de [!DNL Smart Crop] parameter te leren en hoe de genoemde [!DNL Smart Crop] profielen worden toegepast.

>[!IMPORTANT]
>
> U kunt [!DNL Smart Crop] -uitvoeringen alleen maken in de beheerweergave.

## Voorinstellingen voor afbeeldingen{#image-presets-using-dynamic-media-with-openapi-capabilities}

Transformeer beelden op de vlucht gebruikend [&#x200B; Beeld vooraf instelt &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=preset&t=request) vermogen in [!DNL Dynamic Media with OpenAPI capabilities]. Een [!DNL image preset] is een vooraf gedefinieerde set regels voor het vergroten of verkleinen en opmaken van een uitvoerafbeelding.

[!DNL Dynamic Media with OpenAPI capabilities] gebruikt namen met voorinstellingen om een afbeelding direct te transformeren en de uitvoering direct te genereren. Wanneer u een afbeelding aanvraagt via een [!DNL Dynamic Media with OpenAPI] bezorgings-URL die een vooraf ingestelde parameter bevat, past [!DNL DM with OpenAPI] de transformaties van de voorinstelling toe, wordt de vertoning op aanvraag gemaakt en wordt deze aan de gebruiker geleverd.

U kunt één voorinstelling toepassen op meerdere afbeeldingen via de [!DNL Dynamic Media with OpenAPI] -bezorgings-URL&#39;s. Dit zorgt voor een consistente opmaak in de verschillende elementen zonder dat elk element handmatig hoeft te worden bewerkt.

Zie [&#x200B; het leiden Beeld stelt &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets) artikel vooraf in om [&#x200B; te leren hoe te tot beeld leidt vooraf instelt in Mening Admin &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-image-presets), en [&#x200B; hoe te om ontvankelijke beeld tot stand te brengen vooraf instelt &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-a-responsive-image-preset) dat automatisch activa aanpast om verschillende het schermgrootte te passen.

### Voordelen van het gebruik van voorinstellingen voor afbeeldingen{#benefits-of-image-presets}

[!DNL Image Presets] biedt verschillende voordelen voor het beheren en leveren van afbeeldingen in [!DNL Dynamic Media with OpenAPI] . Enkele van de belangrijkste voordelen zijn:

* Met voorinstellingen maakt u URL&#39;s voor de levering van afbeeldingen korter. Gebruik één voorinstelling in plaats van meerdere afbeeldingsmodifiers toe te voegen die de leverings-URL langer maken. Kortere URL&#39;s zijn eenvoudiger te beheren en zorgen voor consistente beeldlevering op verschillende websites, mobiele apps, e-mails en andere kanalen.
* Met voorinstellingen voor afbeeldingen kunt u in een bepaald tijdsbestek uitvoeringen maken op basis van een bronafbeeldingsbestand. Met deze mogelijkheid voor het genereren van uitvoeringen op aanvraag hoeft u niet meerdere statische uitvoeringen van hetzelfde bestand te maken en op te slaan, waardoor zowel de tijd als de opslag wordt bespaard.
* Pas één voorinstelling toe op een grote set elementen tegelijk, waarbij handmatige bewerkingen op elk element afzonderlijk worden vermeden, consistente opmaak wordt gegarandeerd en schaalbaarheid wordt ingeschakeld.
* Wanneer u de parameters van een voorinstelling bijwerkt, worden alle afbeeldingen met die voorinstelling automatisch opnieuw opgemaakt. Dit stroomlijnt het uitgeven door het formatteren updates te centraliseren, die de behoefte elimineren om individuele activa of Webcode opnieuw uit te geven.
* Verbetert efficiency en prestaties met dynamische vertoningen caching door CDN, resulterend in snellere lading en geoptimaliseerde prestaties over apparaten en netwerken.

### Afbeeldingsvoorinstellingen gebruiken{#use-image-presets-using-dynamic-media-with-openapi-capabilities}

Nadat u [!DNL Image Presets] hebt gemaakt, kunt u deze gebruiken voor de volgende workflows:

* [Voorinstellingen in URL voor levering van afbeeldingen gebruiken om de uitvoeringen direct te maken voordat deze aan de eindgebruiker worden geleverd](#use-presets-in-delivery-urls)
* [Voorinstellingen gebruiken tijdens het ontwerpen in AEM Sites](#use-presets-during-authoring-in-aem-sites)

#### Voorinstellingen gebruiken in URL voor levering van afbeelding{#use-presets-in-delivery-urls}

Met voorinstellingen kunt u uw URL&#39;s voor levering korter en gebruiksvriendelijker maken.  Elke naam van de voorinstelling fungeert als een unieke id in de leverings-URL. Verwijs in plaats van meerdere modifiers toe te voegen aan de leverings-URL van een element naar de naam van de voorinstelling om de uitvoering direct te genereren. [&#x200B; Leer om het Dynamische Beeld van Media toe te passen vooraf instelt aan uw beeld &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-presets).
In het volgende voorbeeld wordt een URL met een voorinstelling vergeleken met een URL zonder voorinstelling.

**URL zonder vooraf ingesteld (lange URL)**:

```
https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?width=400&height=300&fit=crop&qualit=85&sharpen=true
```

**URL met vooraf ingesteld (korte URL)**:

```
https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?preset=thumbnail
```

De vooraf ingestelde miniatuur bundelt dezelfde instellingen voor afbeeldingsmodifier.

#### Voorinstellingen gebruiken tijdens het ontwerpen in AEM Sites{#use-presets-during-authoring-in-aem-sites}

Auteurs kunnen [!DNL Image Presets] selecteren tijdens het bewerken van pagina&#39;s in de [!DNL AEM Sites] ontwerppagina wanneer [!DNL Dynamic Media] -ondersteuning is ingeschakeld.
Voer de volgende stappen uit om voorinstellingen voor afbeeldingen in uw ontwerppagina te gebruiken:

1. Navigeer naar de ontwerppagina voor sites.
1. Voer de stappen in [&#x200B; de verre activa van de Toegang in de sectie van de Redacteur van de Pagina van AEM &#x200B;](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor) uit om het [!DNL Asset Selector] paneel te gebruiken voor het selecteren van activa.
1. Blader in het deelvenster [!DNL asset selector] omlaag naar **[!UICONTROL Preset type]** , geef `Preset=Preset Name` op in het veld **[!UICONTROL Image Modifiers]** en klik op **[!UICONTROL Done]** .
   ![&#x200B; vooraf ingesteld &#x200B;](/help/assets/assets/preset-in-asset-selector-panel.png)

## Slimme afbeeldingen{#use-smart-imaging-using-dynamic-media-with-openapi-capabilities}

Wanneer u [!DNL Dynamic Media with OpenAPI capabilities] voor beeldlevering gebruikt, worden de beelden automatisch geoptimaliseerd door [&#x200B; Slimme beelden &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/). Geoptimaliseerde levering zorgt ervoor dat afbeeldingen sneller worden geladen, maximale visuele kwaliteit hebben en een minimale bestandsgrootte hebben. Hierdoor wordt de pagina het snelst geladen en blijft de visuele kwaliteit in alle apparaten en netwerken constant hoog, terwijl de minimale bandbreedte wordt verbruikt, waardoor uw website sneller en responsiever wordt.

[!DNL Smart Imaging] bevat de volgende mogelijkheden:

* [Omzetten in automatische indeling](#auto-format-conversion)
* [&#x200B; de bandbreedteoptimalisering van het Netwerk &#x200B;](#network-bandwidth-optimisation)

### Omzetten in automatische indeling{#auto-format-conversion}

[!DNL Dynamic Media with OpenAPI] [&#x200B; zet automatisch beelden in moderne, web-geoptimaliseerde formaten zoals AVIF of WEBP &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=auto-format&t=request) om. De omzetting hangt van de mogelijkheden van browser en [&#x200B; vergunning-recht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate), ongeacht het gevraagde formaat af.

De indelingen AVIF en WEBP bieden een betere compressie, waardoor afbeeldingen kleiner en sneller worden gemaakt voor levering en laden. AVIF wordt gebruikt als standaardformaat aangezien het alle browser mogelijkheden behandelt.

[!DNL Dynamic Media with OpenAPI] gebruikt de `auto-format` queryparameter om het gedrag van de browser te bepalen voor het omzetten van een afbeelding in verschillende indelingen voor geoptimaliseerde aflevering. De auto formaatomzetting omvat **autobevordering** en **autodemotion**. Wanneer het systeem voor levering een voor het web geoptimaliseerde indeling (AVIF of WEBP) via JPEG of PNG promoot, wordt deze automatisch promotie genoemd.

Standaard is de parameter `auto-format` query ingesteld op `true` . Wanneer `auto-format` (waar) wordt toegelaten, negeert het systeem het gevraagde formaat en selecteert automatisch een Web-geoptimaliseerd formaat (AVIF of WEBP) dat op beeldkenmerken, browser mogelijkheden, en [&#x200B; vergunning-recht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate) wordt gebaseerd.

Wanneer `auto-format` true is, levert het systeem de afbeeldingsindeling in de volgende volgorde:

* ***AVIF***: AVIF wordt geleverd als browser het steunt en de vergunning het toestaat. Dit wordt automatisch promoten genoemd.
* ***WEBP***: WEBP wordt geleverd als AVIF niet wordt gesteund of vergunning gegeven. Dit is ook automatische promotie.
* ***JPEG***: JPEG wordt geleverd slechts wanneer AVIF en WEBP niet gesteund zijn, en het beeld heeft geen alpha- kanaal (transparantie). Dit wordt automatische demotie genoemd.
* ***PNG***: PNG wordt geleverd wanneer browser geen moderne formaten steunt en het beeld alpha- kanaal (transparantie) heeft. Dit wordt ook wel automatische demotie genoemd.

Schakel `auto-format` uit door de queryparameter in te stellen op `false` en geef vervolgens de vereiste indeling op om de afbeelding in die indeling te laten leveren.

### Optimalisatie van netwerkbandbreedte{#network-bandwidth-optimisation}

Afbeeldingen worden automatisch geoptimaliseerd op basis van de netwerkvoorwaarden van de client, zodat de levering sneller verloopt en het laden soepel verloopt. De [&#x200B; Kwaliteit &#x200B;](#quality-parameter) en [&#x200B; maximum-kwaliteit &#x200B;](#max-quality-parameter) parameters past automatisch de kwaliteit aan door de niveaus van de beeldcompressie te controleren, met waarden die zich van 1 tot 100 uitstrekken.

Zie het volgende gedrag van de parameters `quality` en `max-quality` :

* Als zowel [!DNL quality] als [!DNL max-quality] zijn opgegeven, heeft [!DNL quality] voorrang.
* Als alleen [!DNL quality] wordt opgegeven, wordt de kwaliteit geleverd ongeacht de laadtijd op basis van de netwerksnelheid.
* Als alleen [!DNL max-quality] wordt opgegeven, wordt de afbeeldingskwaliteit automatisch aangepast op basis van de netwerkvoorwaarden, zodat de best mogelijke kwaliteit tot de opgegeven [!DNL max-quality] -waarde kan worden bereikt.
* Als geen van beide is opgegeven, past het systeem dynamische optimalisatie toe met de standaardwaarde `max-quality` `85` .

#### Kwaliteitsparameter{#quality-parameter}

De parameter quality geeft voorrang aan de afbeeldingskwaliteit boven de laadsnelheid. De kwaliteit van de uitvoerafbeelding wordt gecorrigeerd op de gevraagde waarde (tussen 1 en 100) en de netwerkomstandigheden worden genegeerd. Leer meer over de [&#x200B; parameter van de kwaliteitskwaliteit &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).

#### Max. kwaliteit, parameter{#max-quality-parameter}

De maximum-kwaliteit brengt beeldkwaliteit en ladingstijd in evenwicht die op de netwerksnelheid van de cliënt wordt gebaseerd. Het geeft voorrang aan snellere ladingstijden door beeldkwaliteit op langzamere netwerken te verminderen, terwijl nog het leveren van de hoogst mogelijke kwaliteit (1-100) voor de bepaalde netwerkvoorwaarden. Leer meer over de [&#x200B; maximum-kwaliteit parameter &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).
