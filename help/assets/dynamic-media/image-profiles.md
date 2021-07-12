---
title: Dynamic Media-afbeeldingsprofielen
description: Leer hoe u Dynamic Media-afbeeldingsprofielen maakt die instellingen voor onscherp masker en slim uitsnijden, slim staal of beide bevatten. Pas het profiel vervolgens toe op een map met afbeeldingselementen.
feature: Middelenbeheer, afbeeldingsprofielen, uitvoeringen
role: User
exl-id: 0856f8a1-e0a9-4994-b338-14016d2d67bd
source-git-commit: 24a4a43cef9a579f9f2992a41c582f4a6c775bf3
workflow-type: tm+mt
source-wordcount: '2631'
ht-degree: 6%

---

# Dynamic Media-afbeeldingsprofielen {#image-profiles}

Wanneer u afbeeldingen uploadt, kunt u de afbeelding tijdens het uploaden automatisch uitsnijden door een afbeeldingsprofiel toe te passen op de map.

>[!IMPORTANT]
>
>Afbeeldingsprofielen zijn niet van toepassing op PDF-, geanimeerde GIF- of INDD-bestanden (Adobe InDesign).

## Opties voor uitsnijden {#crop-options}

<!-- CQDOC-16069 for the paragraph directly below -->

De coördinaten voor Slim uitsnijden zijn afhankelijk van de hoogte-breedteverhouding. Als voor de instellingen voor slimme uitsnijdingen in een afbeeldingsprofiel de hoogte-breedteverhouding voor de toegevoegde afmetingen in het afbeeldingsprofiel hetzelfde is, wordt dezelfde hoogte-breedteverhouding naar Dynamic Media verzonden. Adobe raadt u aan hetzelfde snijgebied te gebruiken. Zo voorkomt u dat er invloed optreedt op verschillende afmetingen die in het afbeeldingsprofiel worden gebruikt.

Voor elke SmartCrop-generatie die u maakt, is extra verwerkingstijd nodig. Als u bijvoorbeeld meer dan vijf slimme-uitsnijdverhoudingen toevoegt, neemt het opnemen van elementen trager af. Het kan ook een verhoogde belasting op systemen veroorzaken. Omdat u Slim uitsnijden op mapniveau kunt toepassen, raadt Adobe u aan het te gebruiken in mappen *alleen* waar dat nodig is.

U hebt twee opties voor het uitsnijden van afbeeldingen waaruit u kunt kiezen. U kunt ook het maken van kleuren- en afbeeldingsstalen automatiseren.

<table>
 <tbody>
  <tr>
   <td><strong>Optie</strong></td>
   <td><strong>Wanneer gebruiken</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Uitsnijden met pixels</td>
   <td>Bulk uitsnijdafbeeldingen alleen op basis van afmetingen.</td>
   <td><p>Als u deze optie wilt gebruiken, selecteert u <strong>Pixeluitsnede</strong> in de vervolgkeuzelijst Uitsnijdopties.</p> <p>Als u wilt uitsnijden vanaf de zijkanten van een afbeelding, voert u het aantal pixels in dat u wilt uitsnijden vanaf een zijde of elke zijde van de afbeelding. Hoeveel van de afbeelding wordt uitgesneden, is afhankelijk van de ppi-instelling (pixels per inch) in het afbeeldingsbestand.</p> <p>Een pixeluitsnijding voor een afbeeldingsprofiel wordt op de volgende manier weergegeven:<br /> </p>
    <ul>
     <li>Waarden zijn Boven, Onder, Links en Rechts.</li>
     <li>Linksboven wordt beschouwd als 0,0 en de pixeluitsnijding wordt daar berekend.</li>
     <li>Beginpunt voor uitsnijden: Links is X en Boven is Y</li>
     <li>Horizontale berekening: horizontale pixelgrootte van de oorspronkelijke afbeelding min links en vervolgens min rechts.</li>
     <li>Verticale berekening: verticale pixelhoogte min Boven en vervolgens min Onder.</li>
    </ul> <p>Stel dat u een afbeelding van 4000 x 3000 pixels hebt. U gebruikt waarden: Top=250, Bottom=500, Left=300, Right=700.</p> <p>Van gewas linksboven (300.250) die de vulruimte van (4000-300-700, 3000-250-500, of 3000.2250) gebruikt.</p> </td>
  </tr>
  <tr>
   <td>Slim uitsnijden</td>
   <td>Bulk uitsnijdafbeeldingen op basis van hun visuele brandpunt.</td>
   <td><p>Smart Crop maakt gebruik van de kracht van kunstmatige intelligentie in Adobe Sensei om het uitsnijden van afbeeldingen in bulk te automatiseren. Slim uitsnijden detecteert automatisch het brandpunt in een afbeelding en snijdt dit bij tot het gewenste aandachtspunt, ongeacht de schermgrootte.</p> <p>Als u Slim uitsnijden wilt gebruiken, selecteert u <strong>Slim uitsnijden</strong> in de vervolgkeuzelijst Uitsnijdopties en vervolgens rechts van Uitsnijden met responsieve afbeelding, schakelt u de functie in (uit).</p> <p>De standaardformaten voor breekpunten (Groot, Normaal, Klein) bestrijken het volledige bereik van formaten die de meeste afbeeldingen op mobiele apparaten en tablets, desktops en banners gebruiken. Desgewenst kunt u de standaardnamen van Groot, Normaal, en Klein uitgeven.</p> <p>Als u meer onderbrekingspunten wilt toevoegen, klikt u op <strong>Uitsnijden toevoegen</strong>; Als u een uitsnijding wilt verwijderen, klikt u op het pictogram met de prullenbak.</p> </td>
  </tr>
  <tr>
   <td>Kleur en afbeeldingsstaal</td>
   <td>Met Bulk wordt voor elke afbeelding een afbeeldingsstaal gegenereerd.</td>
   <td><p><strong>Opmerking</strong>: Slim staal wordt niet ondersteund in Dynamic Media Classic.</p> <p>Zoek en genereer automatisch stalen van hoge kwaliteit op basis van productafbeeldingen met kleuren of structuur.</p> <p>Als u Kleur en afbeeldingsstaal wilt gebruiken, selecteert u <strong>Slim uitsnijden</strong> in de vervolgkeuzelijst Uitsnijdopties. Schakel vervolgens de functie in (schakel deze in) rechts van Kleur en Afbeeldingsstaal. Geef een pixelwaarde op in de tekstvakken Breedte en Hoogte.</p> <p>Alle uitsnijdingen van afbeeldingen zijn beschikbaar via de Renditions-rail, maar stalen worden alleen gebruikt via de functie URL kopiëren. Gebruik uw eigen weergavecomponent om het staal op uw site te renderen. De uitzondering op deze regel zijn carrouselbanners. Dynamic Media biedt de weergavecomponent voor het staal dat wordt gebruikt in carrouselbanners.</p> <p><strong>Afbeeldingsstalen gebruiken</strong></p> <p>De URL voor afbeeldingsstalen is eenvoudig:</p> <p><code>/is/image/company/&lt;asset_name&gt;:Swatch</code></p> <p>Hierbij wordt <code>:Swatch</code> toegevoegd aan de aanvraag voor het element.</p> <p><strong>Kleurstalen gebruiken</strong></p> <p>Als u kleurstalen wilt gebruiken, dient u een <code>req=userdata</code>-verzoek in te dienen met het volgende:</p> <p><code>/is/image/&lt;company_name&gt;/&lt;swatch_asset_name&gt;:Swatch?req=userdata</code></p> <p>Hier volgt bijvoorbeeld een staalelement in Dynamic Media Classic:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch</code></p> <p>Hier ziet u de corresponderende URL <code>req=userdata</code> van het staalelement:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata</code></p> <p>De reactie <code>req=userdata</code> is als volgt:</p> <p><code class="code">SmartCropDef=Swatch
       SmartCropHeight=200.0
       SmartCropRect=0.421671,0.389815,0.0848564,0.0592593,200,200
       SmartCropType=Swatch
       SmartCropWidth=200.0
       SmartSwatchColor=0xA56DB2</code></p> <p>U kunt ook een <code>req=userdata</code>-reactie aanvragen in XML- of JSON-indeling, zoals in de volgende URL-voorbeelden:</p> <p><code>https://my.company.com:8080/is/image/DemoCo/Sleek:Swatch?req=userdata,xml</code></p><p><code>SmartSwatchColor</code></p><p></p></td></tr></tbody></table>

## Onscherp masker {#unsharp-mask}

U gebruikt **[!UICONTROL Unsharp mask]** om een verscherpingsfiltereffect op de definitieve gedownsampelde afbeelding nauwkeurig af te stemmen. U kunt de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd. Voor dit effect worden dezelfde opties gebruikt als voor het filter Onscherp masker van Adobe Photoshop.

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
   <td>Radius</td>
   <td>Hiermee bepaalt u het aantal pixels rondom de randpixels dat invloed heeft op de verscherping. Voer voor afbeeldingen met een hoge resolutie een waarde in tussen 1 en 2. Bij een lage waarde worden alleen de randpixels verscherpt. met een hoge waarde wordt een grotere reeks pixels verscherpt . De juiste waarde is afhankelijk van de grootte van de afbeelding. De standaardwaarde is 0,2. Bereik is 0-250.</td>
  </tr>
  <tr>
   <td>Drempel</td>
   <td><p>Hiermee bepaalt u het contrastbereik dat moet worden genegeerd wanneer het filter Onscherp masker wordt toegepast. Met andere woorden, met deze optie bepaalt u hoe verschillend de verscherpte pixels moeten zijn van het omringende gebied voordat ze als randpixels worden beschouwd en worden verscherpt. Experimenteer met waarden tussen 0 en 255 om ruis te voorkomen.</p> </td>
  </tr>
 </tbody>
</table>

Verscherpen wordt beschreven in [Afbeeldingen verscherpen](/help/assets/dynamic-media/assets/sharpening_images.pdf).

## Dynamic Media-afbeeldingsprofielen maken {#creating-image-profiles}

Zie [Elementverwerking configureren](config-dm.md#configuring-asset-processing) om geavanceerde verwerkingsparameters voor andere elementtypen te definiëren.

Zie [Informatie over Dynamic Media-afbeeldingsprofielen en videoprofielen](/help/assets/dynamic-media/about-image-video-profiles.md).

Zie ook [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/dynamic-media/best-practices-for-file-management.md).

**Dynamic Media-afbeeldingsprofielen maken:**

1. Tik op het Adobe Experience Manager-logo en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Tik op **[!UICONTROL Create]** om een afbeeldingsprofiel toe te voegen.
1. Voer een profielnaam en waarden in voor onscherp masker, uitsnijden of staal of voor beide.

   Tip: Gebruik een profielnaam die specifiek is voor het beoogde doel. Stel dat u een profiel wilt maken dat alleen stalen genereert. Slim uitsnijden is uitgeschakeld en Kleur en afbeeldingsstaal is ingeschakeld. In dergelijke gevallen kunt u de profielnaam &quot;Slimme stalen&quot; gebruiken.

   Zie ook [Opties voor slim bijsnijden en slimme stalen](#crop-options) en [Onscherp masker](#unsharp-mask).

   ![uitsnijden](assets/crop.png)

1. Tik op **[!UICONTROL Save]**. Het nieuwe profiel wordt weergegeven in de lijst met beschikbare profielen.

## Dynamic Media-afbeeldingsprofielen bewerken of verwijderen {#editing-or-deleting-image-profiles}

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt bewerken of verwijderen. Selecteer **[!UICONTROL Edit Image Processing Profile]** om deze te bewerken. Selecteer **[!UICONTROL Delete Image Processing Profile]** om het te verwijderen.

   ![chlimage_1-254](assets/chlimage_1-254.png)

1. Sla de wijzigingen op als u het bestand bewerkt. Bevestig bij verwijderen dat u het profiel wilt verwijderen.

## Dynamic Media-afbeeldingsprofiel toepassen op mappen {#applying-an-image-profile-to-folders}

Wanneer u een afbeeldingsprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Als zodanig kunt u slechts één afbeeldingsprofiel aan een map toewijzen. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander afbeeldingsprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat op de kaart wordt weergegeven.

<!-- When you add smart crop to an existing Image Profile, you need to re-trigger the [DAM Update Asset workflow](assets-workflow.md) if you want to generate crops for existing assets in your asset repository. -->

U kunt afbeeldingsprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand afbeeldingsprofiel heeft dat u later hebt gewijzigd. Zie [Elementen opnieuw verwerken in een map nadat u het verwerkingsprofiel ervan hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

### Dynamic Media-afbeeldingsprofielen toepassen op specifieke mappen {#applying-image-profiles-to-specific-folders}

U kunt een Profiel van het Beeld op een omslag van binnen het **[!UICONTROL Tools]** menu toepassen of als u in de omslag, van **[!UICONTROL Properties]** bent.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen opnieuw verwerken in een map nadat u het verwerkingsprofiel ervan hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

#### Dynamic Media-afbeeldingsprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-image-profiles-to-folders-from-profiles-user-interface}

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u wilt toepassen op een of meerdere mappen.

   ![chlimage_1-255](assets/chlimage_1-255.png)

1. Tik op **[!UICONTROL Apply Processing Profile to Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen en tik/klik op **[!UICONTROL Apply]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Dynamic Media-afbeeldingsprofielen vanuit eigenschappen toepassen op mappen {#applying-image-profiles-to-folders-from-properties}

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Assets]** en vervolgens naar de map waarop u een afbeeldingsprofiel wilt toepassen.
1. Tik in de map op het vinkje om het te selecteren en tik op **[!UICONTROL Properties]**.
1. Tik op het tabblad **[!UICONTROL Image Profiles]**. Selecteer het profiel in de vervolgkeuzelijst **[!UICONTROL Profile Name]** en tik vervolgens op **[!UICONTROL Save & Close]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

   ![chlimage_1-256](assets/chlimage_1-256.png)

### Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen {#applying-an-image-profile-globally}

Naast het toepassen van een profiel op een omslag, kunt u ook globaal toepassen. Voor inhoud die in Experience Manager Assets in een willekeurige map wordt geüpload, wordt het geselecteerde profiel toegepast.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [Elementen opnieuw verwerken in een map nadat u het verwerkingsprofiel ervan hebt bewerkt](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).

**Een Dynamic Media-afbeeldingsprofiel wereldwijd toepassen:**

1. Voer een van de volgende handelingen uit:

   * Navigeer naar `https://&lt;AEM server&gt;/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en tik **[!UICONTROL Save]**.

      ![chlimage_1-257](assets/chlimage_1-257.png)

   * Navigeer naar CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`.

      Voeg de eigenschap `imageProfile:/conf/global/settings/dam/adminui-extension/imageprofile/<name of image profile>` toe en tik **[!UICONTROL Save All]**.

      ![configure_image_profiles](assets/configure_image_profiles.png)

## Het slimme uitsnijdstaal of het slimme staal van één afbeelding bewerken {#editing-the-smart-crop-or-smart-swatch-of-a-single-image}

U kunt het venster voor slimme uitsnijden van een afbeelding handmatig opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

Zie ook [Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken](#editing-the-smart-crop-or-smart-swatch-of-multiple-images).

**Het slimme uitsnijd of slimme staal van één afbeelding bewerken:**

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Assets]** en vervolgens naar de map waarop een profiel voor slimme uitsnijdingen of slimme staalafbeeldingen is toegepast.
1. Tik op de map om de inhoud van de map te openen.
1. Tik op de afbeelding waarvan u het slimme uitsnijdstaal of het slimme staal wilt aanpassen.
1. Tik op **[!UICONTROL Smart Crop]** op de werkbalk.

1. Voer een van de volgende handelingen uit:

   * Sleep de schuifregelaar naar links of rechts boven in de rechterbovenhoek van de pagina om respectievelijk de weergave van de afbeelding te vergroten of te verkleinen.
   * Sleep in de afbeelding een hoekgreep om de grootte van het zichtbare gebied van het uitsnijden of staal aan te passen.
   * Sleep het vak of het staal in de afbeelding naar een nieuwe locatie. U kunt alleen afbeeldingsstalen bewerken; kleurstalen zijn statisch.
   * Tik boven de afbeelding op **[!UICONTROL Revert]** om al uw bewerkingen ongedaan te maken en het oorspronkelijke uitsnijd of staal te herstellen.
   * Gebruik de pijltoetsen op het toetsenbord om de framegrootte bij te snijden, of om de positie van de afbeelding te wijzigen, of beide.

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]** en tik vervolgens op **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken {#editing-the-smart-crop-or-smart-swatch-of-multiple-images}

Nadat u een afbeeldingsprofiel met slimme uitsnijding hebt toegepast op een map, is op alle afbeeldingen in die map een uitsnijding toegepast. Desgewenst kunt u het venster voor slimme uitsnijden in meerdere afbeeldingen *handmatig opnieuw uitlijnen of het formaat ervan wijzigen om het brandpunt verder te verfijnen.*

Nadat u een slim uitsnijden hebt bewerkt en opgeslagen, wordt de wijziging doorgegeven overal waar u het uitsnijden voor de specifieke afbeeldingen gebruikt.

U kunt slimme uitsnijdingen opnieuw uitvoeren als u de extra uitsnijdingen opnieuw wilt genereren.

**Het slimme uitsnijdstaal of het slimme staal van meerdere afbeeldingen bewerken:**

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Assets]** en vervolgens naar een map waarop een profiel voor slimme uitsnijdingen of slimme staalafbeeldingen is toegepast.
1. Tik in de map op het pictogram **[!UICONTROL More Actions]** (...) en tik vervolgens op **[!UICONTROL Smart Crop]**.

1. Voer op de pagina **[!UICONTROL Edit Smart Crops]** een van de volgende handelingen uit:

   * Pas de weergavegrootte van afbeeldingen op de pagina aan.

      Sleep de schuifregelaar naar links of rechts naast de vervolgkeuzelijst voor de naam van het onderbrekingspunt om het formaat van de weergave van de weer te geven afbeelding te wijzigen.

      ![edit_smart_crop-sliderbar](assets/edit_smart_crops-sliderbar.png)

   * Filter de lijst met weer te geven afbeeldingen op basis van namen van onderbrekingspunten. In het onderstaande voorbeeld worden de afbeeldingen gefilterd op de naam van het onderbrekingspunt &quot;Normaal&quot;.

      Selecteer in de vervolgkeuzelijst in de rechterbovenhoek van de pagina een naam voor het onderbrekingspunt om te filteren op welke afbeeldingen u ziet. (Zie de bovenstaande afbeelding.)

      ![edit_smart_crop-dropdownlist](assets/edit_smart_crops-dropdownlist.png)

   * Pas het formaat van het vak voor slimme uitsnijden aan. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak. Pas de grootte van het zichtbare gebied van de uitsnijding aan.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u de hoekgreep van het uitsnijdvak naar de afbeelding. Pas de grootte van het zichtbare gebied van de uitsnijding aan. Of tik op het slimme staal onder de afbeelding (kleurstalen zijn statisch) en sleep vervolgens de hoekgreep van het uitsnijdvak. Pas de grootte van het zichtbare gebied van het staal aan.

      ![Het formaat van het slimme uitsnijden van een afbeelding](assets/edit_smart_crops-resize.png) wijzigen.

   * Het vak voor slimme uitsnijding verplaatsen. Voer een van de volgende handelingen uit:

      * Als de afbeelding alleen een slim uitsnijden of een slim staal bevat, sleept u het uitsnijdvak naar een nieuwe locatie.
      * Als de afbeelding zowel een slim uitsnijden als een slim staal bevat, sleept u het vak voor slim uitsnijden naar een nieuwe locatie. Of tik of klik op het slimme staal onder de afbeelding (kleurstalen zijn statisch) en sleep het uitsnijdvak van het slimme staal naar een nieuwe locatie.

      ![edit_smart_crop-move](assets/edit_smart_crops-move.png)

   * Maak alle bewerkingen ongedaan en herstel het oorspronkelijke slimme uitsnijdstaal of het oorspronkelijke slimme staal (alleen van toepassing op de huidige bewerkingssessie).

      Tik **[!UICONTROL Revert]** boven de afbeelding.

      ![edit_smart_crop-revert](assets/edit_smart_crops-revert.png)



1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save]** en tik vervolgens op **[!UICONTROL Close]** om terug te keren naar de map met elementen.

## Een afbeeldingsprofiel verwijderen uit mappen {#removing-an-image-profile-from-folders}

Wanneer u een afbeeldingsprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Elke verwerking van bestanden die in de mappen is opgetreden, blijft echter intact.

U kunt een Profiel van het Beeld uit een omslag uit **[!UICONTROL Tools]** menu verwijderen of als u in de omslag, uit **[!UICONTROL Properties]** bent.

### Dynamic Media-afbeeldingsprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-image-profiles-from-folders-via-profiles-user-interface}

1. Tik op het logo van de Experience Manager en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Image Profiles]**.
1. Selecteer het afbeeldingsprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Tik op **[!UICONTROL Remove Processing Profile from Folders]** en selecteer de map of meerdere mappen die u wilt gebruiken om het profiel te verwijderen en tik op **[!UICONTROL Remove]**.

   U kunt bevestigen dat het afbeeldingsprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Dynamic Media-afbeeldingsprofielen uit mappen verwijderen door eigenschappen {#removing-image-profiles-from-folders-via-properties}

1. Tik op het logo van de Experience Manager en navigeer **[!UICONTROL Assets]** naar de map waaruit u een afbeeldingsprofiel wilt verwijderen.
1. Tik in de map op het vinkje om het te selecteren en tik vervolgens op **[!UICONTROL Properties]**.
1. Selecteer het tabblad **[!UICONTROL Image Profiles]**.
1. Selecteer **[!UICONTROL None]** in de vervolgkeuzelijst **[!UICONTROL Profile Name]** en tik **[!UICONTROL Save & Close]**.

   Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.
