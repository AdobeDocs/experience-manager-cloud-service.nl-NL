---
title: Dynamische mediaafbeeldingsprofielen
description: Leer hoe u dynamische mediaafbeeldingsprofielen maakt die instellingen voor onscherp masker en slimme uitsnijdingen, slimme stalen of beide bevatten. Pas het profiel vervolgens toe op een map met afbeeldingselementen.
contentOwner: Rick Brough
feature: Asset Management,Image Profiles,Renditions,Best Practices
role: User
exl-id: 0856f8a1-e0a9-4994-b338-14016d2d67bd
source-git-commit: 36ab36ba7e14962eba3947865545b8a3f29f6bbc
workflow-type: tm+mt
source-wordcount: '3372'
ht-degree: 0%

---

# Dynamische mediaafbeeldingsprofielen {#image-profiles}

Wanneer u afbeeldingen uploadt, kunt u de afbeelding tijdens het uploaden automatisch uitsnijden door een afbeeldingsprofiel toe te passen op de map.

>[!IMPORTANT]
>
>Afbeeldingsprofielen zijn niet van toepassing op PDF-, geanimeerde GIF- of INDD-bestanden (Adobe InDesign).

## Onscherp masker, optie {#unsharp-mask}

Wanneer u een afbeeldingsprofiel maakt, kunt u met de optie **[!UICONTROL Unsharp mask]** een verscherpingsfiltereffect perfectioneren voor de uiteindelijke gedownsampelde afbeelding. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker in Adobe Photoshop.

>[!NOTE]
>
>Het onscherp masker wordt alleen toegepast op geschaalde uitvoeringen in de PTIFF-indeling (piramide tiff) die meer dan 50% zijn gedownsampled. Het onscherpe masker heeft geen invloed op de grootst mogelijke uitvoeringen binnen het pad. Terwijl kleinere uitvoeringen, zoals miniaturen, worden gewijzigd (en het onscherpe masker worden weergegeven).

In **[!UICONTROL Unsharp Mask]** hebt u de volgende filteropties:

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Hoeveelheid</td>
   <td>Hiermee bepaalt u de hoeveelheid contrast die wordt toegepast op de randpixels. De standaardwaarde is 1,75. Voor afbeeldingen met een hoge resolutie kunt u de resolutie verhogen tot maximaal 5. Beschouw Hoeveelheid als een maat voor de filterintensiteit. Het bereik is 0-5.</td>
  </tr>
  <tr>
   <td>Straal</td>
   <td>Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een waarde in tussen 1 en 2. Met een lage waarde worden alleen de randpixels verscherpt; met een hoge waarde wordt een bredere reeks pixels verscherpt. De juiste waarde is afhankelijk van de grootte van de afbeelding. De standaardwaarde is 0,2. Het bereik is 0-250.</td>
  </tr>
  <tr>
   <td>Drempel</td>
   <td><p>Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met deze optie bepaalt u hoe verschillende verscherpte pixels moeten verschillen van de omgeving om als randpixels te worden beschouwd. Alleen pixels die aan deze drempelwaarde voldoen, worden verscherpt. Experimenteer met waarden tussen 0 en 255 om ruis te voorkomen.</p> </td>
  </tr>
 </tbody>
</table>

Verscherpen wordt beschreven in [&#x200B; het Verscherpen Beelden &#x200B;](/help/assets/dynamic-media/assets/sharpening_images.pdf).

## Opties voor uitsnijden {#crop-options}

Als u SmartCrop op afbeeldingen implementeert, raadt Adobe de volgende aanbevolen procedures aan en past het de volgende limiet toe:

| Element - Type limiet | Beste praktijken | Oplegde limiet |
| --- | --- | --- |
| **Beeld** - Aantal Slimme Gewas per beeld | 5 | 100 |

Zie ook [&#x200B; Dynamische beperkingen van Media &#x200B;](/help/assets/dynamic-media/limitations.md).

<!-- CQDOC-16069 for the paragraph directly below -->

De coördinaten voor slimme uitsnijdingen zijn afhankelijk van de hoogte-breedteverhouding. Als voor de instellingen voor slimme uitsnijdingen in een afbeeldingsprofiel de hoogte-breedteverhouding voor de toegevoegde afmetingen in het afbeeldingsprofiel hetzelfde is, wordt dezelfde hoogte-breedteverhouding naar dynamische media verzonden. Adobe raadt u aan hetzelfde uitsnijdgebied te gebruiken. Zo voorkomt u dat er invloed optreedt op verschillende afmetingen die in het afbeeldingsprofiel worden gebruikt.

Voor elke slimme uitsnijdgeneratie die u maakt, is extra verwerkingstijd nodig. Als u bijvoorbeeld meer dan vijf hoogte-breedteverhoudingen voor slimme uitsnijden toevoegt, kan dit leiden tot een trage inname van elementen. Het kan ook een verhoogde belasting van systemen veroorzaken. Aangezien slim uitsnijden kan worden toegepast op mapniveau, raadt Adobe aan het alleen te gebruiken voor mappen waar dat nodig is.

**Richtlijnen voor het bepalen van Slimme Uitsnede in een Profiel van het Beeld**
Adobe raadt de volgende richtlijnen en tips aan om het gebruik van Smart Crop onder controle te houden en de verwerkingstijd en opslag van gewassen te optimaliseren:

* Op afbeeldingselementen waarop een slimme uitsnijding wordt toegepast, moet minimaal 50 x 50 pixels of groter zijn.
* In het ideale geval hebt u 10-15 slimme gewassen per afbeelding om de beeldverhoudingen en de verwerkingstijd te optimaliseren.
* Noem slimme gewassen die op gewassenafmetingen worden gebaseerd, niet op eindgebruik. Dit helpt u te optimaliseren voor duplicaten waarbij één dimensie op meerdere pagina&#39;s wordt gebruikt.
* Maak paginagewijs/middelengewijs afbeeldingsprofielen voor specifieke mappen en submappen in plaats van een algemeen profiel voor slimme uitsnijdingen dat wordt toegepast op alle mappen of alle elementen.
* Een afbeeldingsprofiel dat u toepast op submappen, overschrijft een afbeeldingsprofiel dat is toegepast op de map.
* Een afbeeldingsprofiel dat dubbele slimme-uitsnijdafmetingen bevat, is niet toegestaan.
* Dubbele benoemde afbeeldingsprofielen waarvoor opties voor slim uitsnijden zijn ingesteld, zijn niet toegestaan.

U hebt twee opties voor het uitsnijden van afbeeldingen waaruit u kunt kiezen: pixeluitsnijding en slim uitsnijden. U kunt er ook voor kiezen om het maken van kleur- en afbeeldingsstalen te automatiseren of de snijinhoud in de verschillende doelresoluties te behouden.

>[!IMPORTANT]
>
>Adobe raadt u aan de gegenereerde gewassen en stalen te controleren om na te gaan of deze geschikt en relevant zijn voor uw merk en waarden.

| Optie | Wanneer gebruiken | Beschrijving |
| --- | --- | --- |
| **[!UICONTROL Pixel Crop]** | Bulk uitsnijdafbeeldingen alleen op basis van afmetingen. | Selecteer in de vervolgkeuzelijst **[!UICONTROL Cropping Options]** de optie **[!UICONTROL Pixel Crop]**.<br> om van de kanten van een beeld uit te snijden, gaat u het aantal pixel in om van om het even welke kant of elke kant van het beeld uit te snijden. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand.<br> het pixeluitsnijding van het Profiel van het Beeld geeft op de volgende manier terug:<br>・ De waarden zijn Boven, Onder, Links, en Rechts.<br>・ Linksboven wordt beschouwd als `0,0` en de pixeluitsnede wordt daar berekend.<br>・ Beginpunt voor uitsnijden: Links is X en Boven is Y <br>・ Horizontale berekening: horizontale pixelgrootte van oorspronkelijke afbeelding min Links en vervolgens minus Rechts.<br>・ Verticale berekening: verticale pixelhoogte minus Boven en vervolgens minus Onder.<br> bijvoorbeeld, veronderstel u een 4000x 3000 pixelbeeld hebt. U gebruikt waarden: Top=250, Bottom=500, Left=300, Right=700.<br> van upper-left (300.250) gewas die de vullingsruimte van (4000-300-700, 300-250-500, of 3000.2250) gebruiken. |
| **[!UICONTROL Smart Crop]** | Bulk uitsnijdafbeeldingen op basis van hun visuele brandpunt. | Slim uitsnijden gebruikt de kracht van kunstmatige intelligentie in Adobe Sensei om het uitsnijden van afbeeldingen snel in bulk te automatiseren. Slim uitsnijden detecteert automatisch het brandpunt in een afbeelding en snijdt dit bij tot het gewenste aandachtspunt, ongeacht de schermgrootte.<br> Van **[!UICONTROL Cropping Options]** drop-down lijst, uitgezochte **[!UICONTROL Smart Crop]**, dan rechts van **[!UICONTROL Responsive Image Crop]**, laat (zet) de eigenschap toe.<br> de standaardbreekpuntgrootte (**[!UICONTROL Large]**, **[!UICONTROL Medium]**, **[!UICONTROL Small]**) behandelt de volledige waaier van grootte die de meeste beelden op mobiele en tabletapparaten, Desktops, en banners gebruiken. Desgewenst kunt u de standaardnamen van Groot, Medium en Klein bewerken.<br> om meer breekpunten toe te voegen, selecteer **[!UICONTROL Add Crop]**; om een uitsnijding te schrappen, selecteer het pictogram van het Ongedaan maken kan. |
| **[!UICONTROL Color and Image Swatch]** | Met Bulk wordt voor elke afbeelding een afbeeldingsstaal gegenereerd. | **Nota**: Het slimme Staal wordt niet gesteund in Dynamic Media Classic.<br> bepaal de plaats en produceert automatisch van uitstekende kwaliteit stalen van productbeelden die kleur of textuur tonen.<br> van de **[!UICONTROL Cropping Options]** drop-down lijst, uitgezochte **[!UICONTROL Smart Crop]**. Schakel vervolgens rechts van **[!UICONTROL Color and Image Swatch]** de functie in (schakel deze in). Geef een pixelwaarde op in de tekstvakken **[!UICONTROL Width]** en **[!UICONTROL Height]** .<br> terwijl alle beeldgewassen van het spoor van Vertoningen beschikbaar zijn, worden de monsters slechts gebruikt als **[!UICONTROL Copy URL]** eigenschap. Gebruik uw eigen weergavecomponent om het staal op uw site te renderen. De uitzondering op deze regel zijn carrouselbanners. Dynamic Media biedt de weergavecomponent voor het staal dat wordt gebruikt in carrouselbanners.<br><br>**Gebruikend beeldstalen**<br> URL voor beeldmonsters is ongecompliceerd:<br>`/is/image/company/&lt;asset_name&gt;:Swatch`<br> waar `:Swatch` aan het activaverzoek wordt toegevoegd.<br><br>**Gebruikend kleurenstalen**<br> om kleurenstalen te gebruiken, maakt u a `req=userdata` verzoek met het volgende:<br>`/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata`<br><br> Bijvoorbeeld, is het volgende een staalactiva in Dynamic Media Classic:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch`<br> en hier is het overeenkomstige de dienovereenkomstige van de staalactiva `req=userdata` URL:<br>`https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata`<br> De `req=userdata` reactie is als volgt:<br>`SmartCropDef=Swatch`<br>`SmartCropHeight=200.0`<br>`SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200`<br>`SmartCropType=Swatch`<br>`SmartCropWidth=200.0`<br>`SmartSwatchColor=0xA56DB2`<br> u kunt een `req=userdata` reactie in of XML of formaat JSON, zoals in verzoeken respectieve URL voorbeelden:<br>・ `https://my.company.com</code>:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,json`<br>・ `https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml`<br><br>**Nota**: U moet uw eigen component tot stand brengen WCM om een kleurenmonster te verzoeken en de `SmartSwatchColor` attributen te ontleden, die door een hexadecimale waarde met 24 bits van RGB worden vertegenwoordigd.<br> zie ook [`userdata` &#x200B;](https://experienceleague.adobe.com/nl/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/req/r-userdata) in de Gids van de Verwijzing van Kijkers. |
| **[!UICONTROL Preserve crop content across target resolutions]** | Uitsnijdinhoud in dezelfde verhouding behouden | Gebruik deze optie wanneer u een profiel voor slimme uitsnijdingen maakt.<br> om nieuwe gewasseninhoud - terwijl het handhaven van het brandpunt - voor een bepaalde aspectverhouding over verschillende resoluties te produceren, uncheck deze optie <br> als u besluit om dit vakje los te maken, zorg ervoor dat de originele beeldresolutie groter is dat de resoluties die u voor uw slim gewassenprofiel bepaalt.<br><br> als voorbeeld, veronderstel u de aspectverhoudingen bij 600 x 600 (Groot), 400 x 400 (Medium), en 300 x 300 (Klein) hebt geplaatst.<br> wanneer **[!UICONTROL Preserve crop content across target resolutions]** de optie wordt gecontroleerd **, ziet u het zelfde gewas over alle drie resoluties, gelijkend op de volgende steekproefoutput van beelden (voor illustratieve slechts doeleinden):<br>![&#x200B; Uitgezochte Optie &#x200B;](/help/assets/dynamic-media/assets/preserve-checked.png)<br><br> wanneer **[!UICONTROL Preserve crop content across target resolutions]** optie *ongecontroleerd* is, is de gewasseninhoud nieuw voor alle drie resoluties, gelijkend op de volgende steekproefoutput van beelden (voor illustratieve slechts doeleinden):<br>![&#x200B; Niet gecontroleerde Optie 1&rbrace;:](/help/assets/dynamic-media/assets/preserve-unchecked.png) Geen Gecontroleerde Optie 1&rbrace; 0&rbrace; |

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
| GIF | `.gif` | image/gif | sRGB | 15 GB | Ja; het eerste frame van de geanimeerde GIF wordt gebruikt voor de vertoning. U kunt het eerste frame niet configureren of wijzigen. |
| JPEG | `.jpg` en `.jpeg` | image/jpeg | sRGB | 15 GB | Ja |
| PNG | `.png` | image/png | sRGB | 15 GB | Ja |
| PSD | `.psd` | image/vnd.adobe.photoshop | sRGB <br> CMYK | 2 GB | Ja |
| SVG | | | | | Nee |
| TIFF | `.tif` en `.tiff` | image/tiff | sRGB <br> CMYK | 4 GB | Ja |
| WebP/Geanimeerde WebP | | | | | Nee |

## Dynamische mediaafbeeldingsprofielen maken {#creating-image-profiles}

Om geavanceerde verwerkingsparameters voor andere activa te bepalen types, zie [&#x200B; Vormend de Verwerking van Activa &#x200B;](config-dm.md#configuring-asset-processing).

Zie [&#x200B; Ongeveer Dynamische Profielen van het Beeld van Media en Videoprofielen &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md).

Zie ook [&#x200B; Beste praktijken voor het Organiseren van uw Digitale Assets voor het gebruiken van Profielen van de Verwerking &#x200B;](/help/assets/organize-assets.md).

**om Dynamische Profielen van het Beeld van Media tot stand te brengen:**

1. Selecteer het Adobe Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]** .
1. Selecteer **[!UICONTROL Create]** als u een afbeeldingsprofiel wilt toevoegen.
1. Voer een profielnaam en waarden in voor onscherp masker, uitsnijden of staal of voor beide.

   >[!TIP]
   >
   >Gebruik een profielnaam die specifiek is voor het beoogde doel. Stel dat u een profiel wilt maken dat alleen stalen genereert. Slim uitsnijden is uitgeschakeld en Kleur en afbeeldingsstaal is ingeschakeld. In dergelijke gevallen kunt u de profielnaam &quot;Slim staal&quot; gebruiken.

   Zie ook [Opties voor slim bijsnijden en slimme stalen](#crop-options) en [Onscherp masker](#unsharp-mask).

   ![&#x200B; gewas &#x200B;](assets/crop.png)

1. Selecteer **[!UICONTROL Save]**. Het gemaakte profiel wordt weergegeven in de lijst met beschikbare profielen.

## Dynamische afbeeldingsprofielen van media bewerken of verwijderen {#editing-or-deleting-image-profiles}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]** .
1. Selecteer het afbeeldingsprofiel dat u wilt bewerken of verwijderen. Selecteer **[!UICONTROL Edit Image Processing Profile]** als u het bestand wilt bewerken. Selecteer **[!UICONTROL Delete Image Processing Profile]** als u het wilt verwijderen.

   ![&#x200B; chlimage_1-254 &#x200B;](assets/chlimage_1-254.png)

1. Sla de wijzigingen op als u het bestand bewerkt. Bevestig bij verwijderen dat u het profiel wilt verwijderen.

## Een dynamisch afbeeldingsprofiel voor media toepassen op mappen {#applying-an-image-profile-to-folders}

Wanneer u een afbeeldingsprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Als zodanig kunt u slechts één afbeeldingsprofiel aan een map toewijzen. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander afbeeldingsprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen met een toegewezen profiel geven de naam van het profiel op de kaart weer.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

U kunt afbeeldingsprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand afbeeldingsprofiel heeft dat u later hebt gewijzigd. Zie [&#x200B; activa in een omslag opnieuw verwerken nadat u zijn verwerkingsprofiel &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) hebt uitgegeven.

### Dynamische mediaafbeeldingsprofielen toepassen op specifieke mappen {#applying-image-profiles-to-specific-folders}

U kunt vanuit het menu **[!UICONTROL Tools]** of vanuit **[!UICONTROL Properties]** een afbeeldingsprofiel toepassen op een map.

Mappen met een toegewezen profiel geven de naam van het profiel direct onder de mapnaam weer.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [&#x200B; activa in een omslag opnieuw verwerken nadat u zijn verwerkingsprofiel &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) hebt uitgegeven.

#### Dynamische mediaafbeeldingsprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]** .
1. Selecteer het afbeeldingsprofiel dat u wilt toepassen op een of meerdere mappen.

   ![&#x200B; chlimage_1-255 &#x200B;](assets/chlimage_1-255.png)

1. Selecteer **[!UICONTROL Apply Processing Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en selecteer **[!UICONTROL Apply]** . Mappen met een toegewezen profiel geven de naam van het profiel direct onder de mapnaam weer.

#### Dynamische mediaafbeeldingsprofielen toepassen op mappen vanuit eigenschappen {#applying-image-profiles-to-folders-from-properties}

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** .
1. Navigeer aan a *omslag* (niet een activa) waarop u een Profiel van het Beeld wilt toepassen.
1. Voer afhankelijk van de weergave waarin u zich bevindt een van de volgende handelingen uit:
   * Houd de aanwijzer in de kaartweergave boven op de map en selecteer het vinkje om het te selecteren.
   * Schakel in de kolomweergave of de lijstweergave het selectievakje links van de mapnaam in.
1. Selecteer **[!UICONTROL Properties]** op de werkbalk.
1. Selecteer de tab **[!UICONTROL Dynamic Media Processing]** .
1. Selecteer onder **[!UICONTROL Image Profile]** in de vervolgkeuzelijst **[!UICONTROL Profile Name]** het profiel dat u wilt toepassen.
1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek van de pagina. Mappen met een toegewezen profiel geven de naam van het profiel direct onder de mapnaam weer.

   ![&#x200B; chlimage_1-256 &#x200B;](assets/chlimage_1-256.png)

### Een dynamisch afbeeldingsprofiel voor media algemeen toepassen {#applying-an-image-profile-globally}

Naast het toepassen van een profiel op een omslag, kunt u ook globaal toepassen. Voor inhoud die in een map naar Experience Manager Assets wordt geüpload, wordt het geselecteerde profiel toegepast.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [&#x200B; activa in een omslag opnieuw verwerken nadat u zijn verwerkingsprofiel &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) hebt uitgegeven.

**om een Dynamisch Profiel van het Beeld van Media globaal toe te passen:**

1. Voer een van de volgende handelingen uit:

   * Navigeer naar `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en selecteer **[!UICONTROL Save]** .

     ![&#x200B; chlimage_1-257 &#x200B;](assets/chlimage_1-257.png)

   * Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content` .

     Voeg de eigenschap `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` toe en selecteer **[!UICONTROL Save All]** .

     ![&#x200B; configure_image_profiles &#x200B;](assets/configure_image_profiles.png)

## Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

>[!IMPORTANT]
>
>Adobe raadt u aan eventuele gegenereerde slimme gewassen en slimme stalen te controleren om te controleren of deze geschikt en relevant zijn voor uw merk en waarden.

Als u het brandpunt van een afbeelding wilt verfijnen, kunt u de uitlijning handmatig aanpassen of het formaat van het venster voor slimme uitsnijden aanpassen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

>[!IMPORTANT]
>
>Wanneer u het venster voor slim uitsnijden van een element handmatig aanpast, worden de wijzigingen opgeslagen. Deze bewerkingen blijven intact, zelfs als u het element later opnieuw verwerkt. Als u de breedte, hoogte of beide in het gedeelte **[!UICONTROL Responsive Image Crop]** van het afbeeldingsprofiel bewerkt, wordt het element opnieuw verwerkt.
>Zie [&#x200B; Dynamische activa van Media in een omslag &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerken.

Herhaal de slimme uitsnijding om de extra uitsnijdingen indien nodig opnieuw te genereren.

Zie ook [&#x200B; uitgeven het slimme gewas of het slimme monster van veelvoudige beelden &#x200B;](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**om het slimme gewas of slim monster van één enkel beeld uit te geven:**

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** en vervolgens naar de map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.
1. Selecteer de map om de inhoud ervan te openen.
1. Selecteer de afbeelding waarvan u de slimme uitsnijding of het slimme staal wilt aanpassen.
1. Selecteer **[!UICONTROL Smart Crop]** in de werkbalk.

   >[!TIP]
   >
   >Gebruik de sneltoets `s` om de slimme gewassen of slimme stalen te bewerken.

1. Voer een van de volgende handelingen uit:

   * Sleep de schuifregelaar naar links of rechts boven in de rechterbovenhoek van de pagina om respectievelijk de weergave van de afbeelding te vergroten of te verkleinen.
   * Sleep in de afbeelding een hoekgreep om de grootte van het zichtbare gebied van het uitsnijden of staal aan te passen.
   * Sleep het vak of het staal in de afbeelding naar een nieuwe locatie. U kunt alleen afbeeldingsstalen bewerken; kleurstalen zijn statisch.
   * Selecteer **[!UICONTROL Revert]** in de rechterbovenhoek van de afbeelding om alle bewerkingen ongedaan te maken en het oorspronkelijke uitsnijden of staal te herstellen.
   * Gebruik de pijltoetsen op het toetsenbord om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina en selecteer **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

>[!IMPORTANT]
>
>Adobe raadt u aan eventuele gegenereerde slimme gewassen en slimme stalen te controleren om te controleren of deze geschikt en relevant zijn voor uw merk en waarden.

Nadat u een afbeeldingsprofiel (met slimme uitsnijding) hebt toegepast op een map, is op alle afbeeldingen in die map een uitsnijding toegepast. Indien nodig kunt u de uitlijning handmatig aanpassen of het venster voor slimme uitsnijden op meerdere afbeeldingen vergroten of verkleinen om de brandpunten verder te perfectioneren.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

>[!IMPORTANT]
>
>Wanneer u het venster voor slimme uitsnijdingen van meerdere elementen handmatig aanpast, worden de wijzigingen opgeslagen. Deze bewerkingen blijven intact, zelfs als u de elementen later opnieuw verwerkt. Als u de breedte, hoogte of beide in het gedeelte **[!UICONTROL Responsive Image Crop]** van het afbeeldingsprofiel bewerkt, worden deze elementen opnieuw verwerkt.
>Zie [&#x200B; Dynamische activa van Media in een omslag &#x200B;](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets) opnieuw verwerken.

Herhaal de slimme uitsnijding om de extra uitsnijdingen indien nodig opnieuw te genereren.

**om het slimme gewas of slim monster van veelvoudige beelden uit te geven:**

1. Selecteer het Experience Manager-logo en navigeer naar **[!UICONTROL Assets]** en vervolgens naar een map waarop een profiel voor slimme uitsnijdingen of slimme stalen is toegepast.
1. Selecteer in de map het pictogram **[!UICONTROL More Actions]** (...) en selecteer vervolgens **[!UICONTROL Smart Crop]** .

1. Voer op de pagina **[!UICONTROL Edit Smart Crops]** een van de volgende handelingen uit:

   * Pas de weergavegrootte van afbeeldingen op de pagina aan.

     Sleep de schuifregelaar naar links of rechts naast de vervolgkeuzelijst voor de naam van het onderbrekingspunt om het formaat van de weergave van de weer te geven afbeelding te wijzigen.

     ![&#x200B; edit_smart_crop-sliderbar &#x200B;](assets/edit_smart_crops-sliderbar.png)

   * Filter de lijst met weer te geven afbeeldingen op basis van namen van onderbrekingspunten. In het onderstaande voorbeeld worden de afbeeldingen gefilterd met de naam van het onderbrekingspunt &quot;Medium&quot;.

     Selecteer in de vervolgkeuzelijst in de rechterbovenhoek van de pagina een naam voor het onderbrekingspunt om te filteren op welke afbeeldingen u ziet. (Zie de bovenstaande afbeelding.)

     ![&#x200B; geef_smart_crop-dropdownlist uit &#x200B;](assets/edit_smart_crops-dropdownlist.png)

   * Pas het formaat van het vak voor slimme uitsnijden aan. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak. Pas de grootte van het zichtbare gebied van de uitsnijding aan.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak naar de afbeelding. Pas de grootte van het zichtbare gebied van de uitsnijding aan. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en vervolgens de hoekgreep van het uitsnijdvak slepen. Pas de grootte van het zichtbare gebied van het staal aan.

     ![&#x200B; het Vergroten van het slimme gewas van een beeld &#x200B;](assets/edit_smart_crops-resize.png).

   * Het vak voor slimme uitsnijding verplaatsen. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u het uitsnijdvak naar een nieuwe locatie.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u het vak voor slim uitsnijden naar een nieuwe locatie. U kunt ook het slimme staal onder de afbeelding selecteren (kleurstalen zijn statisch) en het uitsnijdvak van het slimme staal naar een nieuwe locatie slepen.

     ![&#x200B; geef_smart_crop-move &#x200B;](assets/edit_smart_crops-move.png) uit

   * Maak alle bewerkingen ongedaan en herstel het oorspronkelijke slimme uitsnijdstaal of het oorspronkelijke slimme staal (alleen van toepassing op de huidige bewerkingssessie).

     Selecteer **[!UICONTROL Revert]** boven de afbeelding.

     ![&#x200B; edit_smart_crop-revert &#x200B;](assets/edit_smart_crops-revert.png)

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina en selecteer **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Een afbeeldingsprofiel uit mappen verwijderen {#removing-an-image-profile-from-folders}

Wanneer u een afbeeldingsprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een afbeeldingsprofiel uit een map verwijderen vanuit het menu **[!UICONTROL Tools]** of vanuit **[!UICONTROL Properties]** als u in de map bent.

### Dynamische mediaafbeeldingsprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Selecteer het Experience Manager-logo en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]** .
1. Selecteer het afbeeldingsprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Selecteer **[!UICONTROL Remove Processing Profile from Folders]** en selecteer de map of meerdere mappen waaruit u het profiel wilt verwijderen en selecteer **[!UICONTROL Remove]** .

   U kunt bevestigen dat het afbeeldingsprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Dynamische mediaafbeeldingsprofielen uit mappen verwijderen met eigenschappen {#removing-image-profiles-from-folders-via-properties}

1. Selecteer het Experience Manager-logo en navigeer **[!UICONTROL Assets]** naar de map waarvan u een afbeeldingsprofiel wilt verwijderen.
1. Selecteer in de map het vinkje om het te selecteren en selecteer vervolgens **[!UICONTROL Properties]** .
1. Selecteer de tab **[!UICONTROL Image Profiles]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Profile Name]** eerst **[!UICONTROL None]** en vervolgens **[!UICONTROL Save & Close]** .

   Mappen met een toegewezen profiel geven de naam van het profiel direct onder de mapnaam weer.
