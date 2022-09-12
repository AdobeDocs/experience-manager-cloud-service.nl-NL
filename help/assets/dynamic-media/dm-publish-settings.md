---
title: Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren
description: Leer hoe u Publiceren instelt in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
exl-id: b0891095-e4a9-4dd5-8dfd-a576bc47d082
source-git-commit: 1730efd1fddd119f2b7950a0e7638ba5624fbb44
workflow-type: tm+mt
source-wordcount: '3213'
ht-degree: 0%

---

# Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren

<!-- hide: yes
hidefromtoc: yes -->

Het configureren van Dynamic Media Publish Setup is alleen beschikbaar als:

* U hebt een *bestaand* **[!UICONTROL Dynamic Media Configuration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager as a Cloud Service. Zie [Een Dynamic Media-configuratie maken in Cloud Services](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
* U bent een systeembeheerder van het systeem van de Experience Manager met beheerdervoorrechten.

Dynamic Media Publish Setup is bedoeld voor gebruik door ervaren ontwikkelaars en programmeurs van websites. Adobe Dynamic Media raadt gebruikers die deze publicatie-instellingen wijzigen aan bekend te zijn met Adobe Dynamic Media, HTTP-protocolstandaarden en -conventies en de basistechnologie voor beeldbewerking.

Op de pagina Dynamic Media Publish Setup (Publicatie-instellingen) worden standaardinstellingen vastgelegd die bepalen hoe elementen worden geleverd vanaf Adobe Dynamic Media-servers naar websites of toepassingen. Als er geen instelling is opgegeven, levert de Adobe Dynamic Media-server een element op basis van een standaardinstelling die is geconfigureerd op de Dynamic Media Publish Setup-pagina.

Zie ook [Optioneel - Dynamic Media-instellingen instellen en configureren](/help/assets/dynamic-media/config-dm.md#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings) voor meer optionele configuratietaken.

>[!NOTE]
>
>Dynamic Media Classic op Adobe Experience Manager as a Cloud Service upgraden naar Dynamic Media? De [Algemene instellingen](/help/assets/dynamic-media/dm-general-settings.md) De pagina&#39;s Pagina&#39;s Publiceren en Instellen in Dynamic Media worden vooraf gevuld met de waarden die van uw Dynamic Media Classic-account zijn overgenomen. De uitzonderingen zijn alle waarden die onder de **[!UICONTROL Default upload options]** op de pagina Algemene instellingen. Deze waarden zijn al in Experience Manager. Alle wijzigingen die u onder **[!UICONTROL Default upload options]**, door een van de vijf tabbladen, via de gebruikersinterface van de Experience Manager, worden weergegeven in Dynamic Media, niet in Dynamic Media Classic. Alle andere instellingen en waarden in het dialoogvenster [Algemene instellingen](/help/assets/dynamic-media/dm-general-settings.md) Dynamic Media Classic en Dynamic Media onderhouden de pagina&#39;s Publiceren instellen op de Experience Manager.

**Dynamic Media Publish Setup Image Server configureren:**

1. In de wijze van de Auteur van de Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben.
1. Selecteer in de linkertrack het pictogram Gereedschappen en ga naar **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]**.
1. In de pagina van de Server van het Beeld, plaats uw Server van het Beeld - publiceer context, en gebruik dan de vijf lusjes om gebrek te vormen publiceer montages.

   * [Afbeeldingsserver](#image-server)
      * [Beveiliging](#security-tab) tab
      * [Catalogusbeheer](#catalog-management-tab) tab
      * [Aanvraagkenmerken](#request-attributes-tab) tab
      * [Algemene miniatuurkenmerken](#common-thumbnail-attributes-tab) tab
      * [Kenmerken kleurbeheer](#color-management-attributes-tab) tab

   ![Dynamic Media Publish Setup-pagina](/help/assets/assets-dm/dm-publish-setup.png)
   *Dynamic Media Publish Setup-pagina, met de **[!UICONTROL Request Attributes]**geselecteerd.*<br><br>

1. Als u klaar bent, selecteert u in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save]**.

## Afbeeldingsserver {#image-server}

De pagina van de Server van het Beeld vestigt standaardmontages voor het leveren van beelden van beeldservers. Instellingen zijn beschikbaar in vijf categorieën

| Context publiceren | Beschrijving |
| --- | --- |
| Beeldserver | Hiermee geeft u de context voor publicatie-instellingen op. |
| Beeldserver testen | Hier geeft u de context voor het testen van publicatie-instellingen op.<br>Alleen voor nieuwe Dynamic Media-accounts is de standaardinstelling **[!UICONTROL Client address]** veld is ingesteld op `127.0.0.1` automatisch.<br>Zie [Elementen testen voordat ze openbaar worden gemaakt](#test-assets-before-making-public). |

### Het tabblad Beveiliging {#security-tab}

**[!UICONTROL Client address]** - Laat u één of meerdere IP adressen of IP adreswaaiers specificeren. Wanneer gespecificeerd, worden de verzoeken aan deze beeldcatalogus die van een cliënt bij een niet vermeld IP adres voortkomen verworpen. Deze regel geldt zowel voor de levering van afbeeldingen als voor gerenderde afbeeldingen.

![Het tabblad Beveiliging ](/help/assets/assets-dm/dm-ipallowlist.png)<br>*Het tabblad Beveiliging dat het veld IP &quot;allow&quot; weergeeft.*


### Tabblad Catalogusbeheer {#catalog-management-tab}

**[!UICONTROL Rule set definition file path]** - Hier geeft u het bestand op dat de definities van de regelset bevat voor de afbeeldingscatalogus.

Zie ook [RuleSetFile](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile.html) in de Dynamic Media Viewers Reference Guide.

>[!NOTE]
>
>Als uw Dynamic Media Classic-account al een **[!UICONTROL Rule set definition file path]** geselecteerd (zoals ingesteld onder **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]**, onder **[!UICONTROL Catalog Management]** -groep), haalt uw Dynamic Media-account op Experience Manager het bestand op van Dynamic Media Classic. Het bestand wordt vervolgens opgeslagen en beschikbaar gesteld in dit veld wanneer u het dialoogvenster **[!UICONTROL Dynamic Media Publish Setup]** pagina voor het eerst.

### Aanvraagkenmerken, tabblad {#request-attributes-tab}

Deze instellingen hebben betrekking op de standaardweergave van afbeeldingen.

| Instelling | Beschrijving |
| --- | --- |
| **[!UICONTROL Reply image size limit]** | Vereist.<br>Alleen voor nieuwe Dynamic Media-accounts wordt de standaardformaatlimiet automatisch ingesteld op Breedte: `3000` en Hoogte: `3000` voor beide **[!UICONTROL Image Serving]** en **[!UICONTROL Test Image Serving]**.<br>Geeft de maximale breedte en hoogte van de antwoordafbeelding aan die aan de client worden geretourneerd. De server retourneert een fout als een aanvraag een antwoordafbeelding veroorzaakt waarvan de breedte, of hoogte, of beide, groter is dan deze instelling.<br>Zie ook [MaxPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Request obfuscation mode]** | Schakel deze optie in als u base64-codering wilt toepassen op geldige aanvragen.<br>Zie ook [RequestObfuscation](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Request locking mode]** | Schakel deze optie in als u een eenvoudige hash-vergrendeling wilt opnemen in aanvragen.<br>Zie ook [RequestLock](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default Request Attributes]** |  |
| **[!UICONTROL Default image file suffix]** | Vereist.<br>Standaardbestandsextensie die wordt toegevoegd aan de waarden van het veld Pad en MaskPath voor de catalogus als het pad geen achtervoegsel voor het bestand bevat.<br>Zie ook [DefaultExt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default font face name]** | Hiermee geeft u op welk lettertype wordt gebruikt als er geen lettertype is opgegeven door een aanvraag voor een tekstlaag. Indien opgegeven, moet dit een geldige naam voor het lettertype zijn in de lettertypetoewijzing van deze afbeeldingscatalogus of in de lettertypetoewijzing van de standaardcatalogus.<br>Zie ook [DefaultFont](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default image]** | Biedt een standaardafbeelding die moet worden geretourneerd als reactie op een verzoek waarbij de gevraagde afbeelding niet wordt gevonden.<br>Zie ook [DefaultImage](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage.html) in de Dynamic Media Viewers Reference Guide.<br>**OPMERKING**: Als uw Dynamic Media Classic-account al een **[!UICONTROL Default image]** geselecteerd (zoals ingesteld onder **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]**, onder **[!UICONTROL Default Request Attributes]** -groep), haalt uw Dynamic Media-account op Experience Manager het bestand op van Dynamic Media Classic. Het bestand wordt vervolgens opgeslagen en beschikbaar gesteld in dit veld wanneer u het dialoogvenster **[!UICONTROL Dynamic Media Publish Setup]** pagina voor het eerst. |
| **[!UICONTROL Default image mode]** | Wanneer het schuifregelaarvak is ingeschakeld (schuifregelaar aan de rechterkant), wordt de schuifregelaar **[!UICONTROL Default image]** Hiermee vervangt u elke ontbrekende laag in de bronafbeelding door de standaardafbeelding en retourneert u de samenstelling zoals gewoonlijk. Wanneer het schuifregelaarvak is uitgeschakeld (schuifregelaar aan de linkerkant), wordt de volledige samengestelde afbeelding vervangen door de standaardafbeelding, zelfs als de ontbrekende afbeelding slechts een van de verschillende lagen is.<br>Zie ook [DefaultImageMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default view size]** | Vereist.<br>Alleen voor nieuwe Dynamic Media-accounts wordt de standaardweergavegrootte automatisch ingesteld op Breedte: `1280` en Hoogte: `1280` voor beide **[!UICONTROL Image Serving]** en **[!UICONTROL Test Image Serving]**.<br>De server beperkt antwoordafbeeldingen tot maximaal deze breedte en hoogte als in de aanvraag niet expliciet de weergavegrootte wordt opgegeven met `wid=`, `hei=`, of `scl=`.<br>Zie ook [DefaultPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail size]** | Vereist.<br>Wordt gebruikt in plaats van kenmerk **[!UICONTROL Default view size]** voor aanvragen van miniaturen (`req=tmb`). De server beperkt antwoordafbeeldingen tot maximaal deze breedte en hoogte als een miniatuuraanvraag (`req=tmb`) geeft de grootte niet expliciet aan met `wid=`, `hei=`, of `scl=`.<br>Zie ook [DefaultThumbPix](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default background color]** | Hiermee geeft u de RGB-waarde op die wordt gebruikt om een willekeurig gebied van een antwoordafbeelding dat geen werkelijke afbeeldingsgegevens bevat, in te vullen.<br>Zie ook [BkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL JPEG Encoding Attributes]** |  |
| **[!UICONTROL Quality]** | <br>Hiermee geeft u de standaardkenmerken op voor JPEG-antwoordafbeeldingen.<br>Alleen voor nieuwe Dynamic Media-accounts: **[!UICONTROL Quality]** standaardwaarde wordt automatisch ingesteld op `80` voor beide **[!UICONTROL Image Serving]** en **[!UICONTROL Test Image Serving]**.<br>Dit veld wordt gedefinieerd tussen 1 en 100.<br>Zie ook [JpegQuality](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Chromatically downsampling]** | Schakel chromatische downsampling van JPEG-coders in of uit. |
| **[!UICONTROL Default resampling mode]** | Hiermee geeft u de standaardkenmerken voor resampling en interpolatie op die u wilt gebruiken voor het schalen van afbeeldingsgegevens. Wanneer gebruiken `resMode` wordt niet opgegeven in een aanvraag.<br>Alleen voor nieuwe Dynamic Media-accounts wordt de standaardmodus voor het berekenen van nieuwe pixels automatisch ingesteld op `Sharp2` voor beide **[!UICONTROL Image Serving]** en **[!UICONTROL Test Image Serving]**.<br>Zie ook [ResMode](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode.html) in de Dynamic Media Viewers Reference Guide. |

### Algemene miniatuurkenmerken, tabblad {#common-thumbnail-attributes-tab}

Deze instellingen hebben betrekking op de standaardweergave en -uitlijning van miniatuurafbeeldingen.

| Instelling | Beschrijving |
| --- | --- |
| **[!UICONTROL Default background color for thumbnail]** | Hiermee geeft u de RGB-waarde op die wordt gebruikt om het gebied van een miniatuurafbeelding in de uitvoer te vullen dat geen werkelijke afbeeldingsgegevens bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** instellen op **[!UICONTROL Fit]** of **[!UICONTROL Texture]**.<br>Zie ook [ThumbBkgColor](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Horizontal alignment]** | Geeft de horizontale uitlijning aan van de miniatuurafbeelding in de rechthoek van de antwoordafbeelding die wordt opgegeven door `wid=` en `hei=` waarden.<br>Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** instellen op **[!UICONTROL Fit]**.<br>U kunt kiezen uit drie horizontale uitlijningen: **[!UICONTROL Center alignment]**, **[!UICONTROL Left alignment]**, en **[!UICONTROL Right alignment]**.<br>Zie ook [ThumbHorizAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Vertical alignment]** | Geeft de verticale uitlijning aan van de miniatuurafbeelding in de rechthoek van de antwoordafbeelding die wordt opgegeven door `wid=` en `hei=` waarden. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer **[!UICONTROL Default Thumbnail Type]** instellen op **[!UICONTROL Fit]**.<br>U kunt kiezen uit drie verticale uitlijningen: **[!UICONTROL Top alignment]**, **[!UICONTROL Center alignment]**, en **[!UICONTROL Bottom alignment]**.<br>Zie ook [ThumbVertAlign](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default cache time to live]** | Verstrekt een standaardvervalinterval in uren voor het geval dat een bepaalde catalogusverslag geen geldige waarde van de Vervaldatum van de catalogus bevat. Instellen op `-1` om te markeren als nooit verlopen. <br>Zie ook [Verlopen](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail type]** | Hiermee wordt een standaardinstelling voor het miniatuurtype opgegeven voor het geval dat een bepaalde catalogusrecord geen geldige waarde voor ThumbType-catalogus bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`).<br>U kunt uit drie miniatuurtypen kiezen: **[!UICONTROL Crop]**, **[!UICONTROL Fit]**, en **[!UICONTROL Texture]**.<br>Zie ook [ThumbType](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail resolution]** | Verstrekt een gebrek voor de duimnagelobjecten resolutie in het geval dat een bepaalde catalogusverslag geen geldige catalogus ThumbRes waarde bevat. Wordt alleen gebruikt voor miniatuuraanvragen (`req=tmb`) en wanneer de **[!UICONTROL Default thumbnail type]** instellen op **[!UICONTROL Texture]**.<br>Zie ook [ThumbRes](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres.html) in de Dynamic Media Viewers Reference Guide. |

### Kenmerken kleurbeheer, tabblad {#color-management-attributes-tab}

Deze instellingen bepalen welke ICC-kleurprofielen worden gebruikt voor afbeeldingen.

**Render-intentie kleurconversie**
Met een rendering intent voor kleurconversie kunt u de standaard rendering intent van de werkprofielen overschrijven om te bepalen hoe de bronkleuren worden aangepast. Wordt gebruikt als:

1. Een van de standaard-ICC-profielen is de doelkleurruimte van een kleuromzetting.
1. Dit profiel kenmerkt een uitvoerapparaat (printer of monitor).
1. En de opgegeven render-intentie is geldig voor dit profiel.

Bij verschillende rendering intents worden verschillende regels gebruikt om te bepalen hoe de bronkleuren worden aangepast.

Zie ook [IccRenderIntent](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent.html) in de Dynamic Media Viewers Reference Guide.

>[!NOTE]
>
>Over het algemeen kunt u het beste de standaard rendering intent gebruiken voor de geselecteerde kleurinstelling, die door Adobe is getest om te voldoen aan industriestandaarden. Als u bijvoorbeeld een kleurinstelling kiest voor Noord-Amerika of Europa, is de standaard rendering intent voor kleurconversie **[!UICONTROL Relative Colorimetric]**. Als u een kleurinstelling voor Japan kiest, is de standaard rendering intent voor kleurconversie **[!UICONTROL Perceptual]**.

| Instelling | Kenmerken |
| --- | --- |
| **[!UICONTROL CMYK default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor CMYK-gegevens. Indien **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer uitgeschakeld voor deze afbeeldingscatalogus als er CMYK-bronafbeeldingen bij betrokken zijn. Alle CMYK-werkruimten zijn apparaatafhankelijk, wat betekent dat ze zijn gebaseerd op werkelijke inkt- en papiercombinaties. De Adobe-benodigdheden van de CMYK-werkruimten zijn gebaseerd op standaarddrukcondities voor commerciële drukwerk.<br> Zie ook [IccProfileCMYK](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Gray-Scale default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor grijswaardengegevens. Indien **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer uitgeschakeld voor deze afbeeldingscatalogus wanneer er bronafbeeldingen met grijswaarden bij betrokken zijn.<br>Zie ook [IccProfileGray](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL RGB default color space]** | Hiermee geeft u de naam op van het ICC-kleurprofiel dat u wilt gebruiken als werkprofiel voor RGB-gegevens. Indien **[!UICONTROL None Specified]** wordt gekozen, wordt kleurbeheer uitgeschakeld voor deze afbeeldingscatalogus wanneer er afbeeldingen met RGB-bronnen bij betrokken zijn. In het algemeen is het beter om **[!UICONTROL Adobe RGB]** of **[!UICONTROL sRGB]** in plaats van het profiel voor een specifiek apparaat (zoals een monitorprofiel). **[!UICONTROL sRGB]** wordt aanbevolen voor het voorbereiden van afbeeldingen voor het web of mobiele apparaten, omdat hiermee de kleurruimte wordt gedefinieerd van de standaardmonitor die wordt gebruikt om afbeeldingen op het web weer te geven. **[!UICONTROL sRGB]** is ook geschikt wanneer u werkt met afbeeldingen van digitale camera&#39;s op consumentenniveau, omdat bij het merendeel van deze camera&#39;s s sRGB als de standaardkleurruimte worden gebruikt.<br>Zie ook [IccProfileRBG](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb.html) in de Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Color conversion rendering intent]** | **[!UICONTROL Perceptual]** - Beoogd wordt de visuele relatie tussen kleuren te behouden, zodat deze voor het menselijk oog natuurlijk worden ervaren, ook al kunnen de kleurwaarden zelf veranderen. Deze intent is geschikt voor fotografische afbeeldingen met veel kleuren die buiten de kleuromvang vallen. Deze instelling is de standaard rendering intent voor de Japanse afdrukindustrie. |
|  | **[!UICONTROL Relative Colorimetric]** - Vergelijkt het extreme hooglicht van de bronkleurruimte met dat van de doelkleurruimte en verschuift alle kleuren dienovereenkomstig. Kleuren buiten de kleuromvang worden verschoven naar de dichtstbijzijnde reproduceerbare kleur in de doelkleurruimte. Bij Relatief colorimetrisch blijven meer oorspronkelijke kleuren behouden dan bij Perceptueel. Deze instelling is de standaard rendering intent voor afdrukken in Noord-Amerika en Europa. |
|  | **[!UICONTROL Saturation]** - Probeert levendige kleuren in een afbeelding te produceren ten koste van de kleurnauwkeurigheid. Deze rendering intent is geschikt voor zakelijke afbeeldingen, zoals grafieken of diagrammen, waar heldere verzadigde kleuren belangrijker zijn dan de exacte relatie tussen kleuren. |
|  | **[!UICONTROL Absolute Colorimetric]** - Hiermee blijven kleuren die binnen de doelkleuromvang vallen ongewijzigd. Kleuren buiten de kleuromvang worden bijgesneden. Kleuren worden niet geschaald naar het witpunt van de bestemming. Deze intent is bedoeld om de kleurnauwkeurigheid te behouden ten koste van de relaties tussen kleuren en is geschikt voor proefdrukken om de uitvoer van een bepaald apparaat te simuleren. Deze intent is handig als u een voorvertoning wilt weergeven van de invloed van de papierkleur op de afgedrukte kleuren. |

## Elementen testen voordat ze openbaar worden gemaakt {#test-assets-before-making-public}

Veilig het Testen helpt u een veilig testmilieu bepalen en een robuuste zaken-aan-zaken oplossing bouwen, die op een configureerbare reeks IP adres en waaiers wordt gebaseerd. Met deze functionaliteit kunt u uw Adobe Dynamic Media-implementaties afstemmen op de architectuur van uw contentbeheer en bedrijfssysteem.

Met Beveiligd testen kunt u een voorvertoning van de testversie van de website weergeven met niet-gepubliceerde inhoud.

Maak indien gewenst een testomgeving in plaats van elementen openbaar te maken, en wel om de volgende redenen:

* Geef een voorvertoning weer van websites voordat u deze openbaar maakt (website die wordt gefaseerd).
* Serve activa die beperkte toegang, zoals eCatalogi vereisen die prijzen in een B2B Webtoepassing tonen.
* Gebruik middelen achter een firewall als onderdeel van het systeem voor productinformatiebeheer, de toepassing van de klantenservice, de trainingssite enzovoort.

>[!NOTE]
>
>Beveiligd testen heeft geen invloed op de toegang tot Adobe Dynamic Media Classic. De beveiliging van Adobe Dynamic Media Classic blijft consistent en vereist de gebruikelijke aanmeldingsgegevens voor toegang tot Adobe Dynamic Media Classic en verwante webservices.

### Hoe Veilig testen werkt {#how-test-assets-works}

De meeste bedrijven voeren hun Internet achter een firewall in werking. De toegang tot Internet is mogelijk door bepaalde routes en typisch door een beperkte waaier van openbare IP adressen.

Van uw collectief netwerk, kunt u uw openbaar IP adres uitvinden gebruikend websites zoals [https://www.whatismyip.com](https://www.whatismyip.com/) of vraag deze informatie aan bij uw IT-organisatie van uw bedrijf.

Met het Veilige Testen, vestigt Adobe Dynamic Media een specifieke Server van het Beeld voor het opvoeren van milieu&#39;s of interne toepassingen. Om het even welk verzoek aan deze server controleert het oorsprongIP adres. Als het inkomende verzoek niet binnen de goedgekeurde lijst van IP adressen is, is een mislukkingsreactie teruggekeerd. De beheerder van het Bedrijf van Adobe Dynamic Media vormt de goedgekeurde lijst van IP adressen voor het Veilige Testen van hun bedrijf milieu.

Omdat de plaats van het originele verzoek moet worden bevestigd, wordt het verkeer van de Veilige Testende dienst niet verpletterd door een netwerk van de inhoudsdistributie zoals het openbare verkeer van de Server van het Beeld van Dynamic Media. Verzoeken naar de service Beveiligd testen hebben een iets hogere latentie dan de openbare Dynamic Media Image Servers.

Niet-gepubliceerde middelen zijn direct beschikbaar bij de services voor het beveiligen van tests, zonder dat ze hoeven te worden gepubliceerd. Op deze manier kunt u een voorvertoning uitvoeren voordat elementen worden gepubliceerd naar hun openbare afbeeldingsserver.

>[!NOTE]
>
>De veilige Testende diensten gebruiken de Server van de Catalogus die met een interne publicatiecontext wordt gevormd. Daarom als uw bedrijf wordt gevormd om te publiceren om het Veilige Testen te beveiligen, om het even welke geupload activa in Adobe Dynamic Media onmiddellijk beschikbaar op de Veilige Testende diensten te worden. Deze functionaliteit is van toepassing, ongeacht of de elementen zijn gemarkeerd voor publiceren tijdens het uploaden.

De Secure Testing-services bieden momenteel ondersteuning voor de volgende typen middelen en functies:

* Afbeeldingen.
* Vignettes (aanvragen van Server renderen).
* Serveraanvragen renderen (ondersteund, maar moet expliciet door de klant worden aangevraagd).
* Sets, inclusief afbeeldingssets, eCatalog, rendersets en mediasets.
* Standaard Adobe Dynamic Media-viewers met rijke media.
* Adobe Dynamic Media OnDemand JSP-pagina&#39;s.
* Statische inhoud, zoals PDF-bestanden en progressief bediende video&#39;s.
* HTTP-videostreaming.
* Progressieve videostreaming.

De volgende elementtypen en -functies worden momenteel niet ondersteund:

* Zoeken in Adobe Dynamic Media Classic Info of eCatalog
* RTMP-videostreaming
* Web-to-print
* UGC-services (door de gebruiker gegenereerde inhoud)

>[!IMPORTANT]
>
>De ondersteuning voor nieuwe of bestaande UGC-vectorafbeeldingselementen in Adobe Dynamic Media is afgelopen op 30 september 2021.

### De service Beveiligde tests testen {#test-secure-testing-service}

Ga als volgt te werk om ervoor te zorgen dat de service Beveiligd testen naar behoren functioneert:

#### Uw account voorbereiden

1. Neem contact op met de klantenservice van Adobe en verzoek hen om Beveiligingstests op uw account in te schakelen.
1. Selecteer in Adobe Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]**.
1. Op de pagina van de Server van het Beeld, in **[!UICONTROL Publish Context]** vervolgkeuzelijst, selecteert u **[!UICONTROL Test Image Serving]**.
1. Selecteer **[!UICONTROL Security]** tab.
1. Voor de **[!UICONTROL Client address]** filter, selecteren **[!UICONTROL Add]**.
1. In de **[!UICONTROL IP Address]** veld, typt u een IP-adres.
1. In de **[!UICONTROL Mask]** veld, typt u een netmasker.

   >[!NOTE]
   >
   >Als u meer dan één IP adres en netto masker toevoegt, laat het effectief toe *alles* IP adressen om activavraag te maken, en zij allen verschijnen.

1. Voer een van de volgende handelingen uit:

   * Herhaal de vorige drie stappen om meer IP-adressen toe te voegen.
   * Ga door met de volgende stap.

1. In de hogere juiste hoek van de pagina van de Server van het Beeld, selecteer **[!UICONTROL Save]**.
1. Upload de gewenste afbeeldingen naar uw Adobe Dynamic Media-account.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Zorg ervoor dat sommige afbeeldingen zijn gemarkeerd voor publicatie en andere niet zijn gemarkeerd en verzend vervolgens de publicatietaak.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Bepaal de naam van uw Veilige het Testen dienst door te gaan **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media General Setting]**.
1. Op de **[!UICONTROL Server]** pagina, zoek de servernaam rechts van **[!UICONTROL Published Server Name]**.

Neem contact op met de Adobe als de servernaam ontbreekt of als de URL naar de server niet werkt.

#### Websitevariaties voorbereiden

U hebt twee variaties nodig van een website die de gepubliceerde en niet-gepubliceerde elementen koppelt:

* Openbare versie - Koppel elementen met behulp van uw traditionele URL-syntaxis van Adobe Dynamic Media.
* Versie Staging - Koppel elementen met dezelfde syntaxis, maar met de naam van de site voor Beveiligd testen.

#### De tests uitvoeren

Voer de volgende tests uit:

1. Controleer of elementen zichtbaar zijn vanuit uw bedrijfsnetwerk.

   Vanuit het bedrijfsnetwerk dat door het eerder gedefinieerde IP-adresbereik wordt geïdentificeerd, worden in de testversie van de website alle afbeeldingen weergegeven, ongeacht of deze zijn gemarkeerd voor publicatie of niet. Zo kunt u testen zonder dat u per ongeluk afbeeldingen ter beschikking stelt voordat u een voorvertoning van goedkeuring of het product start.

   Bevestig dat in de openbare versie van uw site de gepubliceerde middelen worden weergegeven zoals die eerder met Adobe Dynamic Media zijn gebruikt.

1. Van buiten uw bedrijfsnetwerk, verifieer dat nonpublished activa (d.w.z. unmarked voor publiceren) tegen derdetoegang worden beschermd.

   Open uw netwerk van buitenaf (zoals van uw huiscomputer, of over een verbinding 4G/5G), dan verifieer dat de openbare versie van de plaats alle gepubliceerde activa maar geen van de niet gepubliceerde inhoud toont.

   Bevestig dat de het opvoeren versie geen activa toont omdat u tot de Veilige Testende dienst van een niet goedgekeurd IP adres toegang hebt.
