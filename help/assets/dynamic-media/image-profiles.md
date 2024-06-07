---
title: Dynamic Media-afbeeldingsprofielen
description: Leer hoe u Dynamic Media-afbeeldingsprofielen maakt die instellingen voor onscherp masker en slim uitsnijden, slim staal of beide bevatten. Pas het profiel vervolgens toe op een map met afbeeldingselementen.
contentOwner: Rick Brough
feature: Asset Management,Image Profiles,Renditions,Best Practices
role: User
exl-id: 0856f8a1-e0a9-4994-b338-14016d2d67bd
source-git-commit: 35f31c95e92148ff5f3472f26ea9c40fa5a17947
workflow-type: tm+mt
source-wordcount: '3409'
ht-degree: 3%

---

# Dynamic Media-afbeeldingsprofielen {#image-profiles}

Wanneer u afbeeldingen uploadt, kunt u de afbeelding tijdens het uploaden automatisch uitsnijden door een afbeeldingsprofiel toe te passen op de map.

>[!IMPORTANT]
>
>Afbeeldingsprofielen zijn niet van toepassing op PDF-, geanimeerde GIFFEN- of INDD-bestanden (Adobe InDesign).

## Onscherp masker, optie {#unsharp-mask}

Als u een afbeeldingsprofiel maakt, kunt u de opdracht **[!UICONTROL Unsharp mask]** Hiermee kunt u een verscherpingsfiltereffect op de uiteindelijke gedownsampelde afbeelding perfectioneren. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker in Adobe Photoshop.

>[!NOTE]
>
>Onscherp masker wordt alleen toegepast op verkleinde uitvoeringen in de PTIFF-indeling (piramide tiff) die meer dan 50% zijn gedownsampled. Dat betekent dat de grootst mogelijke uitvoeringen binnen het pad niet worden beïnvloed door een onscherp masker. Terwijl kleinere uitvoeringen, zoals miniaturen, worden gewijzigd (en het onscherpe masker worden weergegeven).

In **[!UICONTROL Unsharp Mask]** hebt u de volgende filteropties:

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Hoeveelheid</td>
   <td>Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde is 1,75. Voor afbeeldingen met een hoge resolutie kunt u de resolutie verhogen tot maximaal 5. Beschouw Hoeveelheid als een maat voor de filterintensiteit. Bereik is 0-5.</td>
  </tr>
  <tr>
   <td>Straal</td>
   <td>Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een waarde in tussen 1 en 2. Met een lage waarde worden alleen de randpixels verscherpt; met een hoge waarde wordt een bredere reeks pixels verscherpt. De juiste waarde is afhankelijk van de grootte van de afbeelding. De standaardwaarde is 0,2. Bereik is 0-250.</td>
  </tr>
  <tr>
   <td>Drempel</td>
   <td><p>Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met waarden tussen 0 en 255 om ruis te voorkomen.</p> </td>
  </tr>
 </tbody>
</table>

Verscherpen wordt beschreven in [Afbeeldingen verscherpen](/help/assets/dynamic-media/assets/sharpening_images.pdf).

## Opties voor uitsnijden {#crop-options}

Wanneer u SmartCrop op afbeeldingen implementeert, raadt de Adobe de volgende aanbevolen procedures aan en past de volgende limiet toe:

| Element - Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| **Afbeelding** - Aantal slimme uitsnijdingen per afbeelding | 5 | 100 |

Zie ook [Dynamic Media-beperkingen](/help/assets/dynamic-media/limitations.md).

<!-- CQDOC-16069 for the paragraph directly below -->

De coördinaten voor slimme uitsnijdingen zijn afhankelijk van de hoogte-breedteverhouding. Als voor de instellingen Slim uitsnijden in een afbeeldingsprofiel de hoogte-breedteverhouding voor de toegevoegde afmetingen in het afbeeldingsprofiel gelijk is, wordt dezelfde hoogte-breedteverhouding naar Dynamic Media verzonden. Adobe raadt u aan hetzelfde snijgebied te gebruiken. Zo voorkomt u dat er invloed optreedt op verschillende afmetingen die in het afbeeldingsprofiel worden gebruikt.

Voor elke slimme uitsnijdgeneratie die u maakt, is extra verwerkingstijd nodig. Als u bijvoorbeeld meer dan vijf hoogte-breedteverhoudingen voor slimme uitsnijden toevoegt, kan dit leiden tot een trage inname van elementen. Het kan ook een verhoogde belasting van systemen veroorzaken. Omdat u Slim uitsnijden op mapniveau kunt toepassen, wordt het aanbevolen dat u het uitsnijden in mappen gebruikt *alleen* waar dat nodig is.

**Richtlijnen voor het definiëren van SmartCrop in een afbeeldingsprofiel**
Om het gebruik van SmartCrop onder controle te houden en de verwerkingstijd en opslag van gewassen te optimaliseren, beveelt de Adobe de volgende richtlijnen en tips aan:

* Op afbeeldingselementen waarop een slimme uitsnijding wordt toegepast, moet minimaal 50 x 50 pixels of groter zijn.
* In het ideale geval hebt u 10-15 slimme gewassen per afbeelding om de beeldverhoudingen en de verwerkingstijd te optimaliseren.
* Noem slimme gewassen die op gewassenafmetingen worden gebaseerd, niet op eindgebruik. Dit helpt u te optimaliseren voor duplicaten waarbij één dimensie op meerdere pagina&#39;s wordt gebruikt.
* Maak paginagewijs/middelengewijs afbeeldingsprofielen voor specifieke mappen en submappen in plaats van een algemeen profiel voor slimme uitsnijdingen dat wordt toegepast op alle mappen of alle elementen.
* Een afbeeldingsprofiel dat u op submappen toepast, overschrijft een afbeeldingsprofiel dat op de map is toegepast.
* Een afbeeldingsprofiel dat dubbele slimme-uitsnijdafmetingen bevat, is niet toegestaan.
* Dubbele benoemde afbeeldingsprofielen waarvoor opties voor slim uitsnijden zijn ingesteld, zijn niet toegestaan.

U hebt twee opties voor het uitsnijden van afbeeldingen waaruit u kunt kiezen: Uitsnijden van pixels en Slim uitsnijden. U kunt er ook voor kiezen om het maken van kleur- en afbeeldingsstalen te automatiseren of de snijinhoud in de verschillende doelresoluties te behouden.

>[!IMPORTANT]
>
>De Adobe raadt u aan de gegenereerde gewassen en stalen te herzien om ervoor te zorgen dat deze geschikt en relevant zijn voor uw merk en waarden.

| Optie | Wanneer gebruiken | Beschrijving |
| --- | --- | --- |
| **[!UICONTROL Pixel Crop]** | Bulk uitsnijdafbeeldingen alleen op basis van afmetingen. | Selecteer in de vervolgkeuzelijst **[!UICONTROL Cropping Options]** de optie **[!UICONTROL Pixel Crop]**.<br>Als u wilt uitsnijden vanaf de zijkanten van een afbeelding, voert u het aantal pixels in dat u wilt uitsnijden vanaf een zijde of elke zijde van de afbeelding. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand.<br>Een pixeluitsnijding voor een afbeeldingsprofiel wordt op de volgende manier gerenderd:<br>・ Waarden zijn Boven, Onder, Links en Rechts.<br>・ Linksboven wordt overwogen `0,0` en de pixeluitsnijding wordt daar berekend.<br>・ Beginpunt voor uitsnijden: Links is X en Boven is Y<br>・ Horizontale berekening: horizontale pixelgrootte van oorspronkelijke afbeelding min links en vervolgens min rechts.<br>・ Verticale berekening: verticale pixelhoogte min bovenkant, en dan minus Onder.<br>Stel dat u een afbeelding van 4000 x 3000 pixels hebt. U gebruikt waarden: Top=250, Bottom=500, Left=300, Right=700.<br>Van gewas linksboven (300.250) die de vulruimte van (4000-300-700, 3000-250-500, of 3000.2250) gebruikt. |
| **[!UICONTROL Smart Crop]** | Bulk uitsnijdafbeeldingen op basis van hun visuele brandpunt. | Smart Crop maakt gebruik van de kracht van kunstmatige intelligentie in Adobe Sensei om het uitsnijden van afbeeldingen in bulk te automatiseren. Slim uitsnijden detecteert automatisch het brandpunt in een afbeelding en snijdt dit bij tot het gewenste aandachtspunt, ongeacht de schermgrootte.<br>Van de **[!UICONTROL Cropping Options]** vervolgkeuzelijst, selecteert u **[!UICONTROL Smart Crop]** en vervolgens rechts van **[!UICONTROL Responsive Image Crop]** schakelt u de functie in (schakelt u deze in).<br>De standaardpuntgrootten (**[!UICONTROL Large]**, **[!UICONTROL Medium]**, **[!UICONTROL Small]**) bestrijkt het volledige scala aan formaten dat de meeste afbeeldingen op mobiele apparaten, tablets, desktops en banners gebruiken. Desgewenst kunt u de standaardnamen van Groot, Normaal, en Klein uitgeven.<br>Selecteer **[!UICONTROL Add Crop]**; als u een uitsnijding wilt verwijderen, selecteert u het pictogram met de prullenbak. |
| **[!UICONTROL Color and Image Swatch]** | Met Bulk wordt voor elke afbeelding een afbeeldingsstaal gegenereerd. | **Opmerking**: Slim staal wordt niet ondersteund in Dynamic Media Classic.<br>Zoek en genereer automatisch stalen van hoge kwaliteit op basis van productafbeeldingen met kleuren of structuur.<br>Van de **[!UICONTROL Cropping Options]** vervolgkeuzelijst, selecteert u **[!UICONTROL Smart Crop]**. Vervolgens rechts van **[!UICONTROL Color and Image Swatch]** schakelt u de functie in (schakelt u deze in). Geef een pixelwaarde op in het dialoogvenster **[!UICONTROL Width]** en **[!UICONTROL Height]** tekstvakken.<br>Hoewel alle beeldgewassen van Renditions spoor beschikbaar zijn, worden de monsters slechts gebruikt door **[!UICONTROL Copy URL]** gebruiken. Gebruik uw eigen weergavecomponent om het staal op uw site te renderen. De uitzondering op deze regel zijn carrouselbanners. Dynamic Media biedt de weergavecomponent voor het staal dat wordt gebruikt in carrouselbanners.<br><br>**Afbeeldingsstalen gebruiken**<br> De URL voor afbeeldingsstalen is eenvoudig:<br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br>Wanneer `:Swatch` wordt toegevoegd aan de aanvraag voor het element.<br><br>**Kleurstalen gebruiken**<br> Als u kleurstalen wilt gebruiken, maakt u een `req=userdata` verzoek met het volgende:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br>Hier volgt bijvoorbeeld een staalelement in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br>Hier ziet u de overeenkomstige stalen `req=userdata` URL:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br>De `req=userdata` de reactie is als volgt :<br>`SmartCropDef=Swatch`<br>`SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br>U kunt ook een `req=userdata` reactie in XML- of JSON-indeling, zoals in de volgende URL-voorbeelden:<br>・`https://my.company.com</code>:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>・`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Opmerking**: U moet uw eigen WCM-component maken om een kleurstaal aan te vragen en de `SmartSwatchColor` kenmerk, weergegeven door een hexadecimale waarde van 24-bits RGB.<br>Zie ook [`userdata`](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata.html) in de Referentiehandleiding voor viewers. |
| **[!UICONTROL Preserve crop content across target resolutions]** | Uitsnijdinhoud in dezelfde verhouding behouden | Gebruik deze optie wanneer u een profiel voor slimme uitsnijdingen maakt.<br>Schakel deze optie uit als u nieuwe uitsnijdinhoud wilt genereren voor een bepaalde hoogte-breedteverhouding in verschillende resoluties, terwijl het brandpunt behouden blijft <br>Als u dit selectievakje uitschakelt, controleert u of de oorspronkelijke afbeeldingsresolutie hoger is dan de resoluties die u voor het profiel Slim uitsnijden definieert.<br><br>Stel dat u de hoogte-breedteverhoudingen hebt ingesteld op 600 x 600 (groot), 400 x 400 (gemiddeld) en 300 x 300 (klein).<br>Wanneer **[!UICONTROL Preserve crop content across target resolutions]** optie is *ingeschakeld* In alle drie de resoluties ziet u dezelfde uitsnijding, vergelijkbaar met de volgende voorbeelduitvoer van afbeeldingen (alleen ter illustratie):<br>![Option ingeschakeld](/help/assets/dynamic-media/assets/preserve-checked.png)<br><br>Wanneer **[!UICONTROL Preserve crop content across target resolutions]** optie is *ongecontroleerd* De uitsnijdinhoud is nieuw voor alle drie de resoluties, net als de volgende voorbeelduitvoer van afbeeldingen (alleen ter illustratie):<br>![Option uitgeschakeld](/help/assets/dynamic-media/assets/preserve-unchecked.png) |

### Ondersteunde bestandsindelingen voor afbeeldingen met slimme uitsnijden en kleurstalen

De maximale resolutie voor ondersteunde invoerbestanden is 16 kB.

>[!NOTE]
>
>De resolutie van 16 kB is een weergaveresolutie met ongeveer 16.000 pixels horizontaal. De meest gebruikte resolutie van 16 kB is 15360 x 8640, die het pixelaantal van 8kHD in elke afmeting verdubbelt, voor een totaal van vier keer zo veel pixel. Deze resolutie heeft 132,7 megapixels, 16 keer zoveel pixels als een resolutie van 4.000 pixels en 64 keer zoveel pixels als de resolutie van 1.080p.

| Afbeeldingsindeling | Niet-hoofdlettergevoelige bestandsextensie | MIME-type | Ondersteunde invoerkleurruimte | Maximale ondersteunde grootte invoerbestand | Ondersteunde afbeeldingsindeling? |
| --- | --- | --- | --- | --- | --- |
| BMP | `.bmp` | image/bmp | sRGB | 4 GB | Ja |
| CMYK | | | | | Ja |
| EPS | | | | | Nee |
| GIF | `.gif` | image/gif | sRGB | 15 GB | Ja; het eerste frame van het geanimeerde GIF wordt gebruikt voor de vertoning. U kunt het eerste frame niet configureren of wijzigen. |
| JPEG | `.jpg` en `.jpeg` | image/jpeg | sRGB | 15 GB | Ja |
| PNG | `.png` | image/png | sRGB | 15 GB | Ja |
| PSD | `.psd` | image/vnd.adobe.photoshop | sRGB<br>CMYK | 2 GB | Ja |
| SVG | | | | | Nee |
| TIFF | `.tif` en `.tiff` | image/tiff | sRGB<br>CMYK | 4 GB | Ja |
| WebP/Geanimeerde WebP | | | | | Nee |

## Dynamic Media-afbeeldingsprofielen maken {#creating-image-profiles}

Zie voor meer informatie over het definiëren van geavanceerde verwerkingsparameters voor andere elementtypen [Elementverwerking configureren](config-dm.md#configuring-asset-processing).

Zie [Informatie over Dynamic Media-afbeeldingsprofielen en videoprofielen](/help/assets/dynamic-media/about-image-video-profiles.md).

Zie ook [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/organize-assets.md).

**Dynamic Media-afbeeldingsprofielen maken:**

1. Selecteer het Adobe Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer **[!UICONTROL Create]**.
1. Voer een profielnaam en waarden in voor onscherp masker, uitsnijden of staal of voor beide.

   Tip: gebruik een profielnaam die specifiek is voor het beoogde doel. Stel dat u een profiel wilt maken dat alleen stalen genereert. Slim uitsnijden is uitgeschakeld en Kleur en afbeeldingsstaal is ingeschakeld. In dergelijke gevallen kunt u de profielnaam &quot;Slimme stalen&quot; gebruiken.

   Zie ook [Opties voor slim bijsnijden en slimme stalen](#crop-options) en [Onscherp masker](#unsharp-mask).

   ![uitsnijden](assets/crop.png)

1. Selecteer **[!UICONTROL Save]**. Het gemaakte profiel wordt weergegeven in de lijst met beschikbare profielen.

## Dynamic Media-afbeeldingsprofielen bewerken of verwijderen {#editing-or-deleting-image-profiles}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt bewerken of verwijderen. Selecteer **[!UICONTROL Edit Image Processing Profile]**. Selecteer **[!UICONTROL Delete Image Processing Profile]**.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Sla de wijzigingen op als u het bestand bewerkt. Bevestig bij verwijderen dat u het profiel wilt verwijderen.

## Dynamic Media-afbeeldingsprofiel toepassen op mappen {#applying-an-image-profile-to-folders}

Wanneer u een afbeeldingsprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Als zodanig kunt u slechts één afbeeldingsprofiel aan een map toewijzen. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander afbeeldingsprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat op de kaart wordt weergegeven.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

U kunt afbeeldingsprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand afbeeldingsprofiel heeft dat u later hebt gewijzigd. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

### Dynamic Media-afbeeldingsprofielen toepassen op specifieke mappen {#applying-image-profiles-to-specific-folders}

U kunt een afbeeldingsprofiel toepassen op een map vanuit de **[!UICONTROL Tools]** of als u zich in de map bevindt, vanuit **[!UICONTROL Properties]**.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

#### Dynamic Media-afbeeldingsprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt toepassen op een of meerdere mappen.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Selecteren **[!UICONTROL Apply Processing Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en selecteer **[!UICONTROL Apply]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Dynamic Media-afbeeldingsprofielen toepassen op mappen vanuit eigenschappen {#applying-image-profiles-to-folders-from-properties}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]**.
1. Navigeren naar een *map* (geen element) waarop u een afbeeldingsprofiel wilt toepassen.
1. Voer afhankelijk van de weergave waarin u zich bevindt een van de volgende handelingen uit:
   * Houd de aanwijzer in de kaartweergave boven op de map en selecteer het vinkje om het te selecteren.
   * Schakel in de kolomweergave of de lijstweergave het selectievakje links van de mapnaam in.
1. Selecteer op de werkbalk de optie **[!UICONTROL Properties]**.
1. Selecteer de **[!UICONTROL Dynamic Media Processing]** tab.
1. Onder **[!UICONTROL Image Profile]** van de **[!UICONTROL Profile Name]** selecteert u het profiel dat u wilt toepassen.
1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save & Close]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen {#applying-an-image-profile-globally}

Naast het toepassen van een profiel op een omslag, kunt u ook globaal toepassen. Voor inhoud die in een map naar Experience Manager Assets wordt geüpload, wordt het geselecteerde profiel toegepast.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen in een map opnieuw verwerken nadat u het verwerkingsprofiel hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

**Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen:**

1. Voer een van de volgende handelingen uit:

   * Navigeren naar `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en selecteer **[!UICONTROL Save]**.

     ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`.

     De eigenschap toevoegen `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` en selecteert u **[!UICONTROL Save All]**.

     ![configure_image_profiles](assets/configure_image_profiles.png)

## Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!IMPORTANT]
>
>Adobe raadt u aan om gegenereerde slimme gewassen en slimme stalen te controleren om te controleren of deze geschikt en relevant zijn voor uw merk en waarden.

U kunt het venster voor slimme uitsnijden van een afbeelding handmatig opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

>[!IMPORTANT]
>
>Wanneer u het venster voor slim uitsnijden van een element handmatig opnieuw uitlijnt of het formaat ervan wijzigt, blijft die bewerking behouden, zelfs als u later besluit het element opnieuw te verwerken. Als u echter de breedte, de hoogte of beide in het dialoogvenster **[!UICONTROL Responsive Image Crop]** in het afbeeldingsprofiel, wordt dat element opnieuw verwerkt.
>Zie [Dynamic Media-elementen in een map opnieuw verwerken](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

Zie ook [Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Het slimme uitsnijd of slimme staal van één afbeelding bewerken:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]** en vervolgens naar de map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.
1. Selecteer de map om de inhoud ervan te openen.
1. Selecteer de afbeelding waarvan u de slimme uitsnijding of het slimme staal wilt aanpassen.
1. Selecteer in de werkbalk de optie **[!UICONTROL Smart Crop]**.

1. Voer een van de volgende handelingen uit:

   * Sleep de schuifregelaar naar links of rechts boven in de rechterbovenhoek van de pagina om respectievelijk de weergave van de afbeelding te vergroten of te verkleinen.
   * Sleep in de afbeelding een hoekgreep om de grootte van het zichtbare gebied van het uitsnijden of staal aan te passen.
   * Sleep het vak of het staal in de afbeelding naar een nieuwe locatie. U kunt alleen afbeeldingsstalen bewerken; kleurstalen zijn statisch.
   * Selecteer boven de afbeelding de optie  **[!UICONTROL Revert]** om al uw bewerkingen ongedaan te maken en het oorspronkelijke uitsnijden of staal te herstellen.
   * Gebruik de pijltoetsen op het toetsenbord om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

>[!IMPORTANT]
>
>Adobe raadt u aan om gegenereerde slimme gewassen en slimme stalen te controleren om te controleren of deze geschikt en relevant zijn voor uw merk en waarden.

Nadat u een afbeeldingsprofiel met slimme uitsnijding hebt toegepast op een map, is op alle afbeeldingen in die map een uitsnijding toegepast. Indien gewenst kunt u *handmatig* U kunt het venster voor slimme uitsnijden in meerdere afbeeldingen opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

>[!IMPORTANT]
>
>Wanneer u het venster voor slimme uitsnijdingen van meerdere elementen handmatig opnieuw uitlijnt of het formaat ervan wijzigt, blijven deze bewerkingen behouden, zelfs als u later besluit deze elementen opnieuw te verwerken. Als u echter de breedte, de hoogte of beide in het dialoogvenster **[!UICONTROL Responsive Image Crop]** in het afbeeldingsprofiel, worden deze elementen opnieuw verwerkt.
>Zie [Dynamic Media-elementen in een map opnieuw verwerken](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

**Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken:**

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Assets]** en vervolgens naar een map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.
1. Selecteer in de map de **[!UICONTROL More Actions]** (...), selecteert u vervolgens **[!UICONTROL Smart Crop]**.

1. Op de **[!UICONTROL Edit Smart Crops]** pagina, voer een van de volgende handelingen uit:

   * Pas de weergavegrootte van afbeeldingen op de pagina aan.

     Sleep de schuifregelaar naar links of rechts naast de vervolgkeuzelijst voor de naam van het onderbrekingspunt om het formaat van de weergave van de weer te geven afbeelding te wijzigen.

     ![edit_smart_crop-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filter de lijst met weer te geven afbeeldingen op basis van namen van onderbrekingspunten. In het onderstaande voorbeeld worden de afbeeldingen gefilterd op de naam van het onderbrekingspunt &quot;Normaal&quot;.

     Selecteer in de vervolgkeuzelijst in de rechterbovenhoek van de pagina een naam voor het onderbrekingspunt om te filteren op welke afbeeldingen u ziet. (Zie de bovenstaande afbeelding.)

     ![edit_smart_crop-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Pas het formaat van het vak voor slimme uitsnijden aan. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak. Pas de grootte van het zichtbare gebied van de uitsnijding aan.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak naar de afbeelding. Pas de grootte van het zichtbare gebied van de uitsnijding aan. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en vervolgens de hoekgreep van het uitsnijdvak slepen. Pas de grootte van het zichtbare gebied van het staal aan.

     ![Het formaat van het slimme uitsnijden van een afbeelding wijzigen](assets/edit_smart_crops-resize.png).

   * Het vak voor slimme uitsnijding verplaatsen. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u het uitsnijdvak naar een nieuwe locatie.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u het vak voor slim uitsnijden naar een nieuwe locatie. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en het uitsnijdvak van het slimme staal naar een nieuwe locatie slepen.

     ![edit_smart_crop-move](assets/edit_smart_crops-move.png)

   * Maak alle bewerkingen ongedaan en herstel het oorspronkelijke slimme uitsnijdstaal of het oorspronkelijke slimme staal (alleen van toepassing op de huidige bewerkingssessie).

     Selecteren **[!UICONTROL Revert]** boven de afbeelding.

     ![edit_smart_crop-revert](assets/edit_smart_crops-revert.png)

1. Selecteer rechtsboven in de pagina de optie **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Een afbeeldingsprofiel uit mappen verwijderen {#removing-an-image-profile-from-folders}

Wanneer u een afbeeldingsprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een afbeeldingsprofiel uit een map verwijderen vanuit de map **[!UICONTROL Tools]** of als u zich in de map bevindt, vanuit **[!UICONTROL Properties]**.

### Dynamic Media-afbeeldingsprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Selecteer het logo van de Experience Manager en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Selecteren **[!UICONTROL Remove Processing Profile from Folders]** en selecteer de map of meerdere mappen waaruit u het profiel wilt verwijderen en selecteer **[!UICONTROL Remove]**.

   U kunt bevestigen dat het afbeeldingsprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Eigenschappen Dynamic Media-afbeeldingsprofielen uit mappen verwijderen {#removing-image-profiles-from-folders-via-properties}

1. Selecteer het logo van de Experience Manager en navigeer **[!UICONTROL Assets]** en vervolgens naar de map waaruit u een afbeeldingsprofiel wilt verwijderen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]**.
1. Selecteer de **[!UICONTROL Image Profiles]** tab.
1. Van de **[!UICONTROL Profile Name]** vervolgkeuzelijst, selecteert u **[!UICONTROL None]** selecteert u vervolgens **[!UICONTROL Save & Close]**.

   Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
