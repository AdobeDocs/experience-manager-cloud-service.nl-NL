---
title: Dynamic Media Cloud Service configureren
description: Informatie over het configureren van dynamische media in Adobe Experience Manager Cloud Service.
translation-type: tm+mt
source-git-commit: bc0852120580065a93923e7fe730485012afba6e
workflow-type: tm+mt
source-wordcount: '4796'
ht-degree: 8%

---


# Dynamic Media Cloud Service configureren {#configuring-dynamic-media-scene-mode}

Als u Adobe Experience Manager gebruikt die is ingesteld voor verschillende omgevingen, zoals een voor ontwikkeling, een voor ophaling en een voor live productie, moet u Dynamic Media Cloud Services configureren voor elk van deze omgevingen.

## Architectuurdiagram van dynamische media {#architecture-diagram-of-dynamic-media-scene-mode}

In het volgende architectuurdiagram wordt beschreven hoe Dynamic Media werkt.

Met de nieuwe architectuur is AEM verantwoordelijk voor hoofdelementen en synchronisaties met Dynamic Media voor het verwerken en publiceren van bedrijfsmiddelen:

1. Wanneer het hoofdelement naar AEM wordt geüpload, wordt het naar Dynamic Media gerepliceerd. Op dat moment worden met Dynamic Media alle processen voor het genereren van elementen, zoals videocodering en dynamische varianten van een afbeelding, verwerkt.
1. Nadat de vertoningen worden geproduceerd, kan AEM veilig tot de verre Dynamische vertoningen van Media toegang hebben en voorproef (geen binaire getallen worden teruggestuurd naar de instantie AEM).
1. Nadat de inhoud klaar is om te worden gepubliceerd en goedgekeurd, brengt het de Dynamische dienst van Media in werking om inhoud uit te duwen naar leveringsservers en geheim voorgeheugeninhoud bij CDN.

![chlimage_1-550](assets/chlimage_1-550.png)

<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading AEM Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your AEM instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Dynamic Media Cloud Service configureren {#configuring-dynamic-media-cloud-services}

**Voordat u Dynamic Media Cloud Service** configureert: Nadat u uw provisioning-e-mail met Dynamic Media-referenties hebt ontvangen, moet u zich [aanmelden](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) bij Dynamic Media Classic om uw wachtwoord te wijzigen. Het wachtwoord dat in de e-mailprovisioning wordt ingevoerd, wordt door het systeem gegenereerd en is alleen bedoeld als tijdelijk wachtwoord. Het is belangrijk dat u het wachtwoord bijwerkt zodat Dynamic Media Cloud Service wordt ingesteld met de juiste referenties.

Dynamische mediawolkenservices configureren:

1. Tik in AEM op het AEM-logo om toegang te krijgen tot de algemene navigatieconsole.
1. Tik links van de console onder de kop **[!UICONTROL Tools]** op **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Tik op de pagina Configuratiebrowser voor dynamische media in het linkerdeelvenster op **[!UICONTROL global]** (tik niet op het mappictogram links van **[!UICONTROL global]** of selecteer dit niet) en tik vervolgens op **[!UICONTROL Create]**.
1. Voer op de pagina Dynamische mediaconfiguratie maken een titel in, het e-mailadres van de Dynamic Media-account, het wachtwoord en selecteer vervolgens het gebied. Deze worden door Adobe aan u verstrekt in de levering e-mail. Neem contact op met de ondersteuningsafdeling als u dit niet hebt ontvangen.
1. Klik op **[!UICONTROL Connect to Dynamic Media]**.

   >[!NOTE]
   >
   >Nadat u een e-mailbericht met dynamische media-referenties hebt ontvangen, [meldt u zich aan bij](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Dynamic Media Classic om uw wachtwoord te wijzigen. Het wachtwoord dat in de e-mailprovisioning wordt ingevoerd, wordt door het systeem gegenereerd en is alleen bedoeld als tijdelijk wachtwoord. Het is belangrijk dat u het wachtwoord bijwerkt zodat de Dynamic Media Cloud Service wordt ingesteld met de juiste referenties.

1. Wanneer de verbinding tot stand is gebracht, kunt u het volgende instellen:

   * **[!UICONTROL Company]** - de naam van de Dynamic Media-account. Het is mogelijk dat u meerdere Dynamic Media-accounts hebt voor verschillende submerken, divisies of verschillende testomgevingen/productieomgevingen.

   * **[!UICONTROL Company Root Folder Path]**

   * **[!UICONTROL Publishing Assets]** - U kunt uit de volgende drie opties kiezen:
      * **[!UICONTROL Immediately]** betekent dat wanneer elementen worden geüpload, het systeem de elementen opgeeft en de URL/Embed onmiddellijk levert. Er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.
      * **[!UICONTROL Upon Activation]** betekent dat u het element eerst expliciet moet publiceren voordat een URL/koppeling Insluiten wordt opgegeven.
      * **[!UICONTROL Selective Publish]** betekent dat elementen automatisch worden gepubliceerd voor beveiligde voorvertoning en expliciet kunnen worden gepubliceerd naar AEM zonder dat ze naar DMS7 worden gepubliceerd voor levering in het publieke domein. In de toekomst verbetert Adobe deze optie om elementen naar AEM te publiceren en elementen naar Dynamic Media te publiceren, die elkaar wederzijds uitsluiten. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies als Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook elementen uitsluitend in AEM publiceren om een voorbeeld te bekijken. dezelfde activa worden niet in DMS7 gepubliceerd voor levering in het publieke domein.
   * **[!UICONTROL Secure Preview Server]** - Hiermee kunt u het URL-pad naar de voorvertoningsserver voor veilige vertoningen opgeven. Dat wil zeggen dat AEM na het genereren van uitvoeringen veilig toegang heeft tot de externe dynamische media-uitvoeringen en deze voorvertoning kan bekijken (er worden geen binaire bestanden teruggestuurd naar de AEM-instantie).
Tenzij u een speciale regeling hebt om de server van uw eigen bedrijf of een speciale server te gebruiken, adviseert Adobe Systems dat u dit het plaatsen zoals gespecificeerd verlaat.

   * **[!UICONTROL Sync all content]** - Standaard geselecteerd. Schakel deze optie uit als u elementen selectief wilt opnemen in of uitsluiten van de synchronisatie met dynamische media. Als u deze optie uitschakelt, kunt u kiezen uit de volgende twee dynamische media-synchronisatiemodi:

   * **[!UICONTROL Dynamic Media sync mode]**
      * **[!UICONTROL Enabled by default]** - De configuratie wordt standaard toegepast op alle mappen, tenzij u een map markeert die specifiek is bedoeld voor uitsluiting. <!-- you can then deselect the folders that you do not want the configuration applied to.-->
      * **[!UICONTROL Disabled by default]** - De configuratie wordt pas op een map toegepast als u een geselecteerde map expliciet markeert voor synchronisatie met Dynamic Media.
Als u een geselecteerde map wilt markeren voor synchronisatie met Dynamische media, opent u de pagina Eigenschappen van uw assetmap. Tik op de **[!UICONTROL Details]** tab en kies vervolgens in de **[!UICONTROL Dynamic Media sync mode]** vervolgkeuzelijst een van de volgende drie opties en sla vervolgens op Tik op **[!UICONTROL Save]**.
         * **[!UICONTROL Inherited]** - Geen expliciete synchronisatiewaarde in de map; in plaats daarvan overerft de map de synchronisatiewaarde van een van de bovenliggende mappen of de standaardmodus in de cloudconfiguratie. De gedetailleerde status voor overgeërfde toont als knopinfo.
         * **[!UICONTROL Enable for sub-folders]** - Neem alles op in deze substructuur voor synchronisatie met dynamische media. De mapspecifieke instellingen overschrijven de standaardmodus in de cloudconfiguratie.
         * **[!UICONTROL Disabled for sub-folders]** - Sluit alles in deze substructuur uit van synchroniseren naar dynamische media.
   >[!NOTE]
   >
   >Er is geen ondersteuning voor versiebeheer in Dynamische media. Ook is de vertraagde activering slechts van toepassing als **[!UICONTROL Publish Assets]** op de pagina Configuratie van dynamische media bewerken is ingesteld op **[!UICONTROL Upon Activation]**, en dit alleen tot de eerste keer dat de asset wordt geactiveerd.
   >
   >
   >Nadat een middel wordt geactiveerd, worden om het even welke updates onmiddellijk gepubliceerd live aan S7 Levering.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Tik op **[!UICONTROL Save]**.
1. Als u de dynamische media-inhoud veilig wilt voorvertonen voordat deze wordt gepubliceerd, moet u de AEM-auteurinstantie &#39;whitelist&#39; om verbinding te maken met Dynamic Media:

   * Meld u aan bij uw Dynamic Media Classic-account: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.
   * Klik op de navigatiebalk rechts boven aan de pagina **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**.

   * Selecteer op de pagina Publiceren afbeeldingsserver in de vervolgkeuzelijst Publicatie-context de optie **[!UICONTROL Test Image Serving]**.
   * Tik voor het filter Clientadres op **[!UICONTROL Add]**.
   * Schakel het selectievakje in om het adres in te schakelen (inschakelen) en voer vervolgens het IP-adres in van de instantie AEM-auteur (niet Dispatcher IP).
   * Klik op **[!UICONTROL Save]**.

U wordt nu gebeëindigd met de basisconfiguratie; u kunt Dynamische media gebruiken.

Als u uw configuratie verder wilt aanpassen, kunt u naar keuze om het even welke taken voltooien onder het [Vormen Geavanceerde Montages in Dynamische Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (Optioneel) Geavanceerde instellingen configureren in dynamische media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Als u de configuratie en de opstelling van Dynamische Media verder wilt aanpassen, of zijn prestaties optimaliseren, kunt u één of meerdere van de volgende *facultatieve* taken voltooien:

* [Instellingen voor dynamische media instellen en configureren](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Optioneel) De prestaties van dynamische media afstemmen](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Optioneel) Instellingen voor dynamische media instellen en configureren {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Gebruik het Dynamische Klassieke (Scene7) gebruikersinterface van Media om veranderingen in uw Dynamische montages van Media aan te brengen.

Sommige taken hierboven vereisen dat u zich hier in Dynamische Klassieke Media (Scene7) registreert: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

De taken van de opstelling en van de configuratie omvatten het volgende:

* [Publicatie-instelling voor afbeeldingsserver](#publishing-setup-for-image-server)
* [Algemene instellingen van toepassing configureren](#configuring-application-general-settings)
* [Kleurbeheer configureren](#configuring-color-management)
* [Elementverwerking configureren](#configuring-asset-processing)
* [Aangepaste MIME-typen toevoegen voor niet-ondersteunde indelingen](#adding-custom-mime-types-for-unsupported-formats)
* [Voorinstellingen voor batchsets maken om automatisch afbeeldingssets en centrifuges te genereren](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Publicatie-instelling voor afbeeldingsserver {#publishing-setup-for-image-server}

De instellingen voor Publicatie-instellingen bepalen hoe elementen standaard worden geleverd via Dynamische media. Als er geen instelling is opgegeven, levert Dynamic Media een element op basis van de standaardinstellingen die zijn gedefinieerd in Publicatie-instelling. Als u bijvoorbeeld een aanvraag indient om een afbeelding te leveren die geen resolutiekenmerk bevat, levert dit een afbeelding op met de standaardinstelling Objectresolutie.

Publicatie-instelling configureren: Klik in Dynamic Media Classic **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**.

Het scherm van de Server van het Beeld vestigt standaardmontages voor het leveren van beelden. Zie het scherm UI voor beschrijving van elke het plaatsen.

* **[!UICONTROL Request Attributes]** - Met deze instellingen worden limieten ingesteld voor afbeeldingen die van de server kunnen worden geleverd.
* **[!UICONTROL Default Request Attributes]** - Deze instellingen hebben betrekking op de standaardweergave van afbeeldingen.
* **[!UICONTROL Common Thumbnail Attributes]** - Deze instellingen hebben betrekking op de standaardweergave van miniatuurafbeeldingen.
* **[!UICONTROL Defaults for Catalog Fields]**- Deze instellingen hebben betrekking op de resolutie en het standaardtype miniatuur van afbeeldingen.
* **[!UICONTROL Color Management Attributes]** - Deze instellingen bepalen welke ICC-kleurprofielen worden gebruikt.
* **[!UICONTROL Compatibility Attributes]** - Met deze instelling kunnen alinea&#39;s met regelafstand en navolgende in tekstlagen op dezelfde manier worden behandeld als in versie 3.6, voor achterwaartse compatibiliteit.
* **[!UICONTROL Localization Support]** - Met deze instellingen kunt u meerdere kenmerken voor de landinstelling beheren. U kunt hiermee ook een landinstellingenkaarttekenreeks opgeven, zodat u kunt definiëren welke talen u wilt ondersteunen voor de verschillende knopinfo in Viewers. Zie **Overwegingen bij het instellen van lokalisatie van middelen** voor meer informatie over het instellen van lokalisatieservice [](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Algemene instellingen van toepassing configureren {#configuring-application-general-settings}

Klik op Dynamische media Classic Global Navigation Bar om de pagina Algemene instellingen toepassing te openen **[!UICONTROL Setup > Application Setup > General Settings]**.

* **[!UICONTROL Servers]** - Dynamische media biedt via provisioning van accounts automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account. Wijzig geen van de servernamen, tenzij dit expliciet wordt opgedragen door AEM-ondersteuning.

* **[!UICONTROL Overwrite Images]** - Dynamische media staat niet toe dat twee bestanden dezelfde naam hebben. De URL-id van elk item (de bestandsnaam minus de extensie) moet uniek zijn. Met deze opties geeft u op hoe vervangende elementen worden geüpload: of zij het origineel vervangen of dupliceren. Dubbele elementen krijgen de naam &quot;-1&quot;. (De naam van bijvoorbeeld stoel.tif wordt gewijzigd in stoel-1.tif). Deze opties zijn van invloed op elementen die naar een andere map zijn geüpload dan het origineel of op elementen met een andere bestandsnaamextensie dan het origineel (zoals JPG, TIF of PNG).

* **[!UICONTROL Overwrite in current folder, same base image name/extension]** - Deze optie is de strengste regel voor vervanging. Hiervoor moet u de vervangende afbeelding uploaden naar dezelfde map als het origineel en moet de vervangende afbeelding dezelfde bestandsnaamextensie hebben als het origineel. Als niet aan deze vereisten wordt voldaan, wordt een dubbel gecreeerd.

   >[!NOTE]
   >
   >Kies altijd de volgende instelling om consistentie met AEM te behouden: **Overschrijven in huidige map, dezelfde naam/extensie voor basisafbeelding**

* **[!UICONTROL Overwrite in any folder, same base asset name/extension]** - Vereist dat de vervangende afbeelding dezelfde bestandsnaamextensie heeft als de oorspronkelijke afbeelding (bijvoorbeeld eigenschap.jpg moet de naam stoel.jpg vervangen, niet stoel.tif). U kunt de vervangende afbeelding echter naar een andere map uploaden dan het origineel. De bijgewerkte afbeelding staat in de nieuwe map; kan het bestand niet meer vinden op de oorspronkelijke locatie
* **[!UICONTROL Overwrite in any folder, same base asset name regardless of extension]** - Deze optie is de meest inclusieve vervangingsregel. U kunt een vervangende afbeelding uploaden naar een andere map dan het origineel, een bestand met een andere bestandsnaamextensie uploaden en het oorspronkelijke bestand vervangen. Als het oorspronkelijke bestand zich in een andere map bevindt, bevindt de vervangende afbeelding zich in de nieuwe map waarnaar het is geüpload.

* **[!UICONTROL Default Color Profiles]** - Zie Kleurbeheer [configureren](#configuring-color-management) voor meer informatie.

>[!NOTE]
>
>Standaard geeft het systeem 15 uitvoeringen weer wanneer u **[!UICONTROL Renditions]** en 15 viewervoorinstellingen selecteert wanneer u **[!UICONTROL Viewers]** in de gedetailleerde weergave van de asset selecteert. U kunt deze limiet verhogen. Zie [Het weergegeven aantal afbeeldingsvoorinstellingen vergroten of verkleinen](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) of [Het weergegeven aantal viewervoorinstellingen vergroten of verkleinen](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).


#### Kleurbeheer configureren {#configuring-color-management}

Met dynamisch kleurbeheer voor media kunt u correcte elementen kleuren. Met kleurcorrectie behouden ingesloten elementen hun kleurruimte (RGB, CMYK, Grijs) en ingesloten kleurprofiel. Wanneer u een dynamische uitvoering aanvraagt, wordt de afbeeldingskleur met CMYK-, RGB- of grijsuitvoer gecorrigeerd naar de doelkleurruimte. Zie Voorinstellingen [voor afbeeldingen](/help/assets/dynamic-media/managing-image-presets.md)configureren.

De standaardeigenschappen voor kleuren configureren om kleurcorrectie in te schakelen bij het aanvragen van afbeeldingen:

1. [Meld u aan bij Dynamic Media Classic](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) met aanmeldingsgegevens die tijdens de provisioning worden geleverd. Ga naar **[!UICONTROL Setup > Application Setup]**.
1. Vouw het gebied **[!UICONTROL Publish Setup]** uit en selecteer **[!UICONTROL Image Server]**. Stel **[!UICONTROL Publish Context]** in op **[!UICONTROL Image Serving]** wanneer u standaardinstellingen voor publicatie-exemplaren instelt.
1. Blader naar de eigenschap die u wilt wijzigen, bijvoorbeeld een eigenschap in het **[!UICONTROL Color Management Attributes]** gebied.

   U kunt de volgende eigenschappen voor kleurcorrectie instellen:

   * **[!UICONTROL CMYK Default Color Space]** - Naam van het standaard CMYK-kleurprofiel
   * **[!UICONTROL Gray-Scale Default Color Space]** - Naam van het standaardgrijskleurprofiel
   * **[!UICONTROL RGB Default Color Space]** - Naam van het standaard RGB-kleurprofiel
   * **[!UICONTROL Color Conversion Rendering Intent]** - Geeft de render-intentie op. Acceptabele waarden zijn: **[!UICONTROL perceptual]**, **[!UICONTROL relative colometric]**, **[!UICONTROL saturation]**, **[!UICONTROL absolute colometric]**. Adobe raadt **[!UICONTROL relative]]**aan als de standaardinstelling.

1. Tik op **[!UICONTROL Save]**.

U kunt bijvoorbeeld **[!UICONTROL RGB Default Color Space]** instellen op *sRGB* en **[!UICONTROL CMYK Default Color Space]** op *WebCoated*.

Dit doet het volgende:

* Hiermee schakelt u kleurcorrectie in voor RGB- en CMYK-afbeeldingen.
* RGB-afbeeldingen die geen kleurprofiel hebben, worden verondersteld zich in de *sRGB* -kleurruimte te bevinden.
* CMYK-afbeeldingen die geen kleurprofiel hebben, worden aangenomen in *WebCoated* -kleurruimte.
* Dynamische uitvoeringen die RGB-uitvoer retourneren, retourneren deze in de *sRGB *kleurruimte.
* Dynamische uitvoeringen die CMYK-uitvoer retourneren, retourneren deze in de *WebCoated* -kleurruimte.

#### Elementverwerking configureren {#configuring-asset-processing}

U kunt bepalen welke elementtypen door Dynamic Media moeten worden verwerkt en de geavanceerde parameters voor elementverwerking aanpassen. U kunt bijvoorbeeld parameters voor elementverwerking opgeven om het volgende te doen:

* Een Adobe PDF converteren naar een eCatalog-element.
* Zet een Adobe Photoshop-document (.PSD) om in een bannersjabloon voor personalisatie.
* Hiermee wordt een Adobe Illustrator-bestand (.AI) of een Adobe Photoshop Encapsulated PostScript-bestand (.EPS) gerasterd.
* Opmerking: U kunt videoprofielen en afbeeldingsprofielen gebruiken om respectievelijk de verwerking van video&#39;s en afbeeldingen te definiëren.

Zie Elementen [uploaden](/help/assets/add-assets.md).

**Elementverwerking configureren**

1. In AEM, click the AEM logo to access the global navigation console, then click **[!UICONTROL General > CRXDE Lite]**.
1. Navigeer in de linkerspoorstaaf naar het volgende:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypen](assets/mimetypes.png)

1. Selecteer een mime-type onder de map mimeTypes.
1. Aan de rechterkant van de pagina CRXDE Lite, in het lagere gedeelte:

   * Dubbelklik op het **[!UICONTROL enabled]** veld. Standaard zijn alle elementtypen ingeschakeld (ingesteld op **[!UICONTROL true]**), wat betekent dat de elementen worden gesynchroniseerd met Dynamic Media voor verwerking. Als u wilt uitsluiten dat dit elementtype mime wordt verwerkt, wijzigt u deze instelling in **[!UICONTROL false]**.

   * Dubbelklik **[!UICONTROL jobParam]** om het bijbehorende tekstveld te openen. Zie [Ondersteunde MIME-typen](/help/assets/file-format-support.md) voor een lijst met toegestane waarden voor de verwerkingsparameters die u voor een bepaald MIME-type kunt gebruiken.

1. Voer een van de volgende handelingen uit:

   * Herhaal stap 3-4 om extra mime-typen te bewerken.
   * Klik op de menubalk van de pagina CRXDE Lite **[!UICONTROL Save All]**.

1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL CRXDE Lite]** om terug te keren naar AEM.

#### Aangepaste MIME-typen toevoegen voor niet-ondersteunde indelingen {#adding-custom-mime-types-for-unsupported-formats}

U kunt aangepaste MIME-typen voor niet-ondersteunde indelingen toevoegen in AEM Assets. Om ervoor te zorgen dat een nieuw knooppunt dat u in CRXDE Lite toevoegt, niet door AEM wordt verwijderd, moet u ervoor zorgen dat u het MIME-type verplaatst vóór `image_` en de ingeschakelde waarde ervan is ingesteld op **[!UICONTROL false]**.

**Aangepaste MIME-typen toevoegen voor niet-ondersteunde indelingen**

1. Tik op AEM **[!UICONTROL Tools > Operations > Web Console]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Er wordt een nieuw browsertabblad geopend voor de **[!UICONTROL Adobe Experience Manager Web Console Configuration]** pagina.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Schuif op de pagina omlaag naar de naam *Adobe CQ Scene7 Asset MIME type Service*, zoals u in de volgende schermafbeelding ziet. Tik rechts van de naam op **[!UICONTROL Edit the configuration values]** (potloodpictogram).

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Op de **pagina van de Dienst** van het TypeDienst van Elementen MIME van Adobe CQ Scene7, klik om het even welk plusteken pictogram &lt;+>. De locatie in de tabel waar u op het plusteken klikt om het nieuwe mime-type toe te voegen, is triviaal.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. Typ `DWG=image/vnd.dwg` in het lege tekstveld dat u zojuist hebt toegevoegd.

   Het voorbeeld `DWG=image/vnd.dwg` is alleen ter illustratie. Het MIME-type dat u hier toevoegt, kan elke andere niet-ondersteunde indeling hebben.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. In the lower-right corner of the page, tap **[!UICONTROL Save]**.

   U kunt nu het browsertabblad sluiten waarop de pagina Configuratie webconsole van Adobe Experience Manager wordt geopend.

1. Keer terug naar het browser lusje dat uw open console AEM heeft.
1. Tik op AEM **[!UICONTROL Tools > General > CRXDE Lite]**.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. Navigeer in de linkerspoorstaaf naar het volgende:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Sleep het mime-type `image_vnd.dwg` en zet het vlak boven `image_` in de structuur neer, zoals in de volgende schermafbeelding wordt getoond.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. Terwijl het mimetype `image_vnd.dwg` nog steeds is geselecteerd, dubbelklikt u op het tabblad **[!UICONTROL Properties]** in de rij **[!UICONTROL enabled]** onder de kolomkop **[!UICONTROL Value]** op de waarde om de vervolgkeuzelijst **[!UICONTROL Value]** te openen.
1. Typ `false` in het veld (of selecteer een optie in de **[!UICONTROL false]** vervolgkeuzelijst).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. Near the upper-left corner of the CRXDE Lite page, click **[!UICONTROL Save All]**.

#### Voorinstellingen voor batchsets maken om automatisch afbeeldingssets en centrifuges te genereren {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Met voorinstellingen voor batchsets kunt u het maken van afbeeldingssets of centrifuges automatiseren terwijl elementen naar dynamische media worden geüpload.

Bepaal eerst de naamgevingsconventie voor hoe elementen in een set moeten worden gegroepeerd. Vervolgens kunt u een voorinstelling voor een batch-set maken. Dit is een unieke, op zichzelf staande set instructies die definiëren hoe de set moet worden samengesteld met afbeeldingen die overeenkomen met de gedefinieerde naamgevingsconventies in het vooraf ingestelde recept.

Wanneer u bestanden uploadt, maakt Dynamic Media automatisch een set met alle bestanden die overeenkomen met de gedefinieerde naamgevingsconventie in de actieve voorinstellingen.

**Standaardnaamgeving configureren**

Een standaardnaamgevingsconventie maken die wordt gebruikt in een willekeurig recept voor een voorinstelling voor batchverwerking. De standaardnaamgevingsconventie die is geselecteerd in de definitie van de voorinstelling voor batch-sets, is mogelijk alles wat uw bedrijf nodig heeft om sets te genereren in batch. Er wordt een voorinstelling voor een batchset gemaakt waarin de standaardnaamgevingsconventie wordt gebruikt die u definieert. U kunt zo veel voorinstellingen Batch-set maken met alternatieve, aangepaste naamconventies die nodig zijn voor een bepaalde set inhoud als er een uitzondering is op de standaardnaamgeving die door het bedrijf is gedefinieerd.

Hoewel het instellen van een standaardnaamgevingsconventie niet is vereist voor het gebruik van de functie voor voorinstellingen voor batchsets, wordt u aangeraden de standaardnaamgevingsconventie te gebruiken om zoveel elementen van de naamgevingsconventie te definiëren als u wilt groeperen in een set, zodat u het maken van batchsets kunt stroomlijnen.

U kunt ook formuliervelden gebruiken **[!UICONTROL View Code]** zonder dat deze beschikbaar zijn. In deze weergave maakt u uw definities van de naamgevingsconventie volledig met behulp van reguliere expressies.

Er zijn twee elementen beschikbaar voor definitie, Identieke en Basisnaam. Met deze velden kunt u alle elementen van een naamgevingsconventie definiëren en het gedeelte van de conventie identificeren dat wordt gebruikt voor de naamgeving van de set waarin deze elementen zich bevinden. De individuele naamgevingsconventie van een onderneming kan voor elk van deze elementen gebruik maken van een of meer definitielijnen. U kunt zo vele lijnen voor uw unieke definitie gebruiken en hen groeperen in verschillende elementen, zoals voor HoofdBeeld, het element van de Kleur, het element van de Afwisselende Mening, en het element van het Monster.

**Standaardnaamgeving configureren**

1. Logon aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Tik op de navigatiebalk boven aan de pagina **[!UICONTROL Setup > Application Setup > Batch Set Presets > Default Naming]**.
1. Selecteer **[!UICONTROL View Form]** of **[!UICONTROL View Code]** om op te geven hoe u informatie over elke asset wilt weergeven en invoeren.

   U kunt het **[!UICONTROL View Code]** selectievakje inschakelen om de waarde van de reguliere expressie naast de formulierselecties weer te geven. U kunt deze waarden invoeren of wijzigen om de elementen van de naamgevingsconventie te definiëren, als de formulierweergave u beperkt om welke reden dan ook. Als uw waarden niet kunnen worden geparseerd in de formulierweergave, worden de formuliervelden inactief.

   >[!NOTE]
   >
   >Door-geactiveerde formuliervelden wordt niet gevalideerd dat de reguliere expressies juist zijn. U ziet de resultaten van de reguliere expressie die u bouwt voor elk element na de resultaatregel. De volledige reguliere expressie wordt onder aan de pagina weergegeven.

1. Vouw indien nodig elk element uit en voer de naamgevingsconventies in die u wilt gebruiken.
1. Voer zo nodig een van de volgende handelingen uit:

   * Tik **[!UICONTROL Add]** om nog een naamgevingsconventie voor een element toe te voegen.
   * Tik **[!UICONTROL Remove]** om een naamgevingsconventie voor een element te verwijderen.

1. Voer een van de volgende handelingen uit:

   * Tik op een naam **[!UICONTROL Save As]** en typ een naam voor de voorinstelling.
   * Tik **[!UICONTROL Save]** als u een bestaande voorinstelling bewerkt.

**Een voorinstelling voor een batchset maken**

Dynamische media gebruikt vooraf ingestelde batch-sets om elementen te ordenen in sets afbeeldingen (alternatieve afbeeldingen, kleuropties, 360 centrifuges) die kunnen worden weergegeven in viewers. De voorinstellingen voor batchsets worden automatisch naast de processen voor het uploaden van elementen in Dynamic Media uitgevoerd.

U kunt uw voorinstellingen voor batchsets maken, bewerken en beheren. Er zijn twee vormen van vooraf ingestelde batch-definities: een voor een standaardnaamgevingsconventie die u hebt ingesteld en een conventie voor aangepaste naamgevingsconventies die u direct maakt.

U kunt de methode voor formuliervelden gebruiken om een voorinstelling voor een batchset te definiëren of de methode voor code, waarmee u reguliere expressies kunt gebruiken. Net als bij Standaardnaam kunt u de optie Code weergeven kiezen terwijl u de definitie in de formulierweergave definieert en reguliere expressies gebruiken om uw definities samen te stellen. U kunt ook de optie voor het uitsluitend gebruiken van de ene weergave of de andere uitschakelen.

**Een voorinstelling voor een batch-set maken**

1. Logon aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Tik op de navigatiebalk boven aan de pagina **[!UICONTROL Setup > Application Setup > Batch Set Presets > Batch Set Preset]**.

   Let op: **[!UICONTROL View Form]** zoals ingesteld in de rechterbovenhoek van de pagina Details, is de standaardweergave.

1. Tik in het deelvenster Lijst met voorinstellingen op **[!UICONTROL Add]** om de definitievelden te activeren in het deelvenster Details aan de rechterkant van het scherm.
1. Typ in het veld Naam voorinstelling in het deelvenster Details een naam voor de voorinstelling.
1. Selecteer een type voorinstelling in het keuzemenu Type batch.
1. Voer een van de volgende handelingen uit:

   * Als u een standaardnaamgevingsconventie gebruikt die u eerder hebt ingesteld onder **[!UICONTROL Application Setup > Batch Set Presets > Default Naming]**, vouwt u deze uit **[!UICONTROL Asset Naming Conventions]** en tikt u vervolgens in de vervolgkeuzelijst Bestandsnaamgeving op **[!UICONTROL Default]**.

   * To define a new naming convention as you set up the preset, expand **[!UICONTROL Asset Naming Conventions]**, and then in the File Naming drop-down list, click **[!UICONTROL Custom]**.

1. Definieer bij Volgorde de volgorde waarin afbeeldingen worden weergegeven nadat de set is gegroepeerd in Dynamische media.

   Uw elementen worden standaard alfanumeriek geordend. U kunt echter een door komma&#39;s gescheiden lijst met reguliere expressies gebruiken om de volgorde te definiëren.

1. Geef bij Naamgeving instellen en Creatieconcept het achtervoegsel of het voorvoegsel op van de basisnaam die u in de Naamgevingsconventie voor middelen hebt gedefinieerd. Definieer ook waar de set wordt gemaakt in de mappenstructuur Dynamische media.

   Als u grote aantallen sets definieert, kunt u deze beter apart houden van de mappen die de elementen zelf bevatten. U kunt bijvoorbeeld een map met afbeeldingssets maken en hier gegenereerde sets plaatsen.

1. Tik in het venster Details op **[!UICONTROL Save]**.
1. Tik **[!UICONTROL Active]** naast de naam van de nieuwe voorinstelling.

   Als u de voorinstelling activeert, weet u zeker dat de voorinstelling van de batch-set wordt toegepast wanneer u elementen uploadt naar Dynamic Media.

**Een voorinstelling voor een batch-set maken voor het automatisch genereren van een 2D-centrifugeset**

U kunt het Type van Reeks van de Partij gebruiken **[!UICONTROL Multi-Axis Spin Set]** om een recept tot stand te brengen dat de generatie van 2D Reeksen van de Rotatie automatiseert. Bij het groeperen van afbeeldingen worden de reguliere expressies Rij en Kolom gebruikt, zodat de afbeeldingselementen op de juiste wijze worden uitgelijnd op de corresponderende locatie in de multidimensionale array. Er is geen minimum- of maximumaantal rijen of kolommen dat u in een centrifugeerset moet hebben.

Stel dat u bijvoorbeeld een spin-set met meerdere assen wilt maken met de naam `spin-2dspin`. U hebt een set afbeeldingen met een set centrifuges die drie rijen bevatten, met 12 afbeeldingen per rij. De afbeeldingen krijgen de volgende naam:

```
spin-01-01
 spin-01-02
 …
 spin-01-12
 spin-02-01
 …
 spin-03-12
```

Met deze informatie kan het recept voor Type batch-set als volgt worden gemaakt:

![chlimage_1-560](assets/chlimage_1-560.png)

De groepering voor het gedeelte met de naam van de gedeelde asset van de spinset wordt toegevoegd aan het veld **Overeenkomst** (zoals gemarkeerd). Het variabele gedeelte van de naam van de asset met de rij en kolom wordt toegevoegd aan respectievelijk de velden **Rij** en **Kolom**.

Wanneer de spinset wordt geüpload en gepubliceerd, activeert u de naam van het recept voor de 2D-spinset die wordt vermeld onder **Voorinstellingen voor batchsets** in het dialoogvenster **Taakopties uploaden**.

**Een voorinstelling voor een batch-set maken voor het automatisch genereren van een 2D-reeks met draaien**

1. Logon aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Klik op de navigatiebalk boven aan de pagina op **[!UICONTROL Setup > Application Setup > Batch Set Presets > Batch Set Preset**.

   Let op: **[!UICONTROL View Form]** zoals ingesteld in de rechterbovenhoek van de pagina Details, is de standaardweergave.

1. Klik in het deelvenster Lijst met voorinstellingen op **[!UICONTROL Add]** om de definitievelden te activeren in het deelvenster Details aan de rechterkant van het scherm.
1. Typ in het veld Naam voorinstelling in het deelvenster Details een naam voor de voorinstelling.
1. Selecteer in het vervolgkeuzemenu Batchsettype de optie **[!UICONTROL Asset Set]**.
1. Selecteer in de vervolgkeuzelijst Subtype **[!UICONTROL Multi-Axis Spin Set]**.
1. Vouw uit **[!UICONTROL Asset Naming Conventions]** en klik vervolgens in de vervolgkeuzelijst Bestandsnaamgeving op **[!UICONTROL Custom]**.
1. Gebruik de kenmerken **[!UICONTROL Match]** en (optioneel) **[!UICONTROL Base Name]** om een reguliere expressie te definiëren voor de naamgeving van afbeeldingsassets waaruit de groepering bestaat.

   De reguliere expressie Letterlijke overeenkomst ziet er bijvoorbeeld als volgt uit:

   `(w+)-w+-w+`

1. Breid uit **[!UICONTROL Row Column Position]**, en bepaal dan het naamformaat voor de positie van het beeldelement binnen 2D de Reeks serie van de Rotatie.

   Gebruik het haakje om de rij- of kolompositie in de bestandsnaam in te sluiten.

   Voor uw reguliere rijexpressie ziet deze er bijvoorbeeld als volgt uit:

   `\w+-R([0-9]+)-\w+`

   or

   `\w+-(\d+)-\w+`

   Voor uw kolom regelmatige uitdrukking, zou het als het volgende kunnen kijken:

   `\w+-\w+-C([0-9]+)`

   or

   `\w+-\w+-C(\d+)`

   Dit zijn slechts voorbeelden. U kunt uw reguliere expressie maken op een manier die aan uw wensen voldoet.

   >[!NOTE]
   >
   >Als de combinatie van reguliere rij- en kolomexpressies de positie van het element binnen de multidimensionale spinsetarray niet kan bepalen, wordt dat element niet toegevoegd aan de set en wordt een fout geregistreerd.

1. Geef bij Naamgeving instellen en Creatieconcept het achtervoegsel of het voorvoegsel op van de basisnaam die u in de Naamgevingsconventie voor middelen hebt gedefinieerd.

   Definieer ook waar de centrifugeset wordt gemaakt in de structuur van de map Dynamic Media Classic.

   Als u grote aantallen sets definieert, kunt u deze beter apart houden van de mappen die de elementen zelf bevatten. Maak bijvoorbeeld een map met centrifuges waarin de gegenereerde sets hier worden geplaatst.

1. Klik in het venster Details op **[!UICONTROL Save]**.
1. Klik naast de naam van de nieuwe voorinstelling. **[!UICONTROL Active]**

   Als u de voorinstelling activeert, weet u zeker dat de voorinstelling van de batch-set wordt toegepast wanneer u elementen uploadt naar Dynamic Media.

### (Optioneel) De prestaties van dynamische media afstemmen {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Adobe raadt de volgende tips voor synchronisatieprestaties/schaalbaarheid aan om dynamische media vloeiend <!--(with `dynamicmedia_scene7` run mode)--> te houden:

* De vooraf gedefinieerde taakparameters bijwerken voor het verwerken van verschillende bestandsindelingen.
* Het bijwerken van de vooraf gedefinieerde Granite-workflow (video-elementen) vormt een wachtrij voor arbeidersthreads.
* Bij het bijwerken van de vooraf gedefinieerde Granite transient-workflow (afbeeldingen en niet-video-elementen) kunt u de workflowthreads voor workers in de wachtrij gebruiken.
* De maximale uploadverbindingen naar de Dynamic Media Classic-server bijwerken.

#### De vooraf gedefinieerde taakparameters bijwerken voor de verwerking van verschillende bestandsindelingen

U kunt taakparameters instellen voor snellere verwerking wanneer u bestanden uploadt. Als u bijvoorbeeld PSD-bestanden uploadt, maar deze niet als sjablonen wilt verwerken, kunt u de uitname van lagen instellen op false (uitgeschakeld). In dat geval wordt de aangepaste taakparameter weergegeven zoals `process=None&createTemplate=false`.

Adobe raadt u aan de volgende taakparameters voor PDF-, Postscript- en PSD-bestanden te gebruiken:

| Bestandstype | Aanbevolen taakparameters |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=Layername&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

Als u een van deze parameters wilt bijwerken, volgt u de stappen in Op MIME gebaseerde elementen [inschakelen/Dynamische media Klassieke ondersteuning](#enabling-mime-type-based-assets-scene-upload-job-parameter-support)voor taakparameters uploaden.

#### De Granite Transient Workflow-wachtrij bijwerken {#updating-the-granite-transient-workflow-queue}

De Granite Transit Workflow-wachtrij wordt gebruikt voor de **[!UICONTROL DAM Update Asset]** workflow. In Dynamische media, wordt het gebruikt voor beeldopname en verwerking.

**De Granite Transient Workflow-wachtrij bijwerken**

1. Ga naar [https://&lt;server>/system/console/configMgr](https://localhost:4502/system/console/configMgr) en zoek naar **Wachtrij: Granite Transient Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. Wijzig in het **[!UICONTROL Maximum Parallel Jobs]** veld het getal in de gewenste waarde.

   Standaard is het maximale aantal parallelle taken afhankelijk van het aantal beschikbare CPU-cores. Op een 4-core server worden bijvoorbeeld twee threads toegewezen. (Een waarde tussen 0,0 en 1,0 is gebaseerd op verhouding, of om het even welke aantallen groter dan 1 zullen het aantal arbeidersdraden toewijzen.)

   Adobe raadt aan dat 32 **[!UICONTROL Maximum Parallel Jobs]** wordt geconfigureerd voor voldoende ondersteuning voor het uploaden van bestanden naar Dynamic Media Classic (Scene7).

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Tik op **[!UICONTROL Save]**.

#### De Granite Workflow-wachtrij bijwerken {#updating-the-granite-workflow-queue}

De Granite Workflow-wachtrij wordt gebruikt voor niet-tijdelijke workflows. In Dynamische Media, gebruikte het om video met het **[!UICONTROL Dynamic Media Encode Video]** werkschema te verwerken.

**De Granite Workflow-wachtrij bijwerken**

1. Navigeer naar `https://<server>/system/console/configMgr` en zoek naar **Wachtrij: Granite Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. Wijzig in het **[!UICONTROL Maximum Parallel Jobs]** veld het getal in de gewenste waarde.

   Standaard is het maximale aantal parallelle taken afhankelijk van het aantal beschikbare CPU-cores. Op een 4-core server worden bijvoorbeeld twee threads toegewezen. (Een waarde tussen 0,0 en 1,0 is gebaseerd op verhouding, of om het even welke aantallen groter dan 1 zullen het aantal arbeidersdraden toewijzen.)

   In de meeste gevallen is de standaardinstelling 0,5 voldoende.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Tik op **[!UICONTROL Save]**.

#### Het bijwerken van Scene7 uploadt verbinding {#updating-the-scene-upload-connection}

Scene7 uploadt verbinding die plaatst synchroniseert activa AEM aan Dynamische Media Klassieke servers.

**Om de Scene7 uploadverbinding bij te werken**

1. Ga naar `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Wijzig het nummer in het **[!UICONTROL Number of connections]** veld en/of het **[!UICONTROL Active job timeout]** veld naar wens.

   Met de **[!UICONTROL Number of connections]** instelling bepaalt u het maximum aantal HTTP-verbindingen dat AEM mag uploaden naar Dynamic Media. doorgaans is de vooraf gedefinieerde waarde van 10 verbindingen voldoende.

   De **[!UICONTROL Active job timeout]** instelling bepaalt de wachttijd voor geüploade dynamische media-elementen die moeten worden gepubliceerd in de leveringsserver. Deze waarde is standaard 2100 seconden of 35 minuten.

   In de meeste gevallen is de instelling 2100 voldoende.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Tik op **[!UICONTROL Save]**.

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your AEM author environment to the AEM publish node. This workflow is necessary because the AEM publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to AEM publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the AEM publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the AEM publish node.

#### Using default asset filters for replication {#using-default-asset-filters-for-replication}

If you are using Dynamic Media for imaging and/or video, then you can use the default filters that we provide as-is. The following filters are active by default:

<table>
 <tbody>
  <tr>
   <td> </td>
   <td><strong>Filter</strong></td>
   <td><strong>Mimetype</strong></td>
   <td><strong>Renditions</strong></td>
  </tr>
  <tr>
   <td>Dynamic Media Image Delivery</td>
   <td><p>filter-images</p> <p>filter-sets</p> <p> </p> </td>
   <td><p>Starts with <strong>image/</strong></p> <p>Contains <strong>application/</strong> and ends with <strong>set</strong>.</p> </td>
   <td>The out-of-the-box "filter-images" (applies to single images assets, including interactive images) and "filter-sets" (applies to Spin Sets, Image Sets, Mixed Media Sets, and Carousel Sets) will:
    <ul>
     <li>Exclude from replication the original image and static image renditions.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Dynamic Media Video Delivery</td>
   <td>filter-video</td>
   <td>Starts with <strong>video/</strong></td>
   <td>The out-of-the-box "filter-video" will:
    <ul>
     <li>Exclude from replication the original video and static thumbnail renditions.<br /> <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Filters apply to mime types and cannot be path specific.

#### Customizing asset filters for replication {#customizing-asset-filters-for-replication}

1. In AEM, tap the AEM logo to access the global navigation console and tap the **[!UICONTROL Tools > General > CRXDE Lite]**.
1. In the left folder tree, navigate to `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` to review the filters.

   ![chlimage_1-17](assets/chlimage_1-2.png)

1. To define the Mime Type for the filter, you can locate the Mime Type as follows:

   In the left rail, expand `content > dam > <locate_your_asset> > jcr:content > metadata`, and then in the table, locate `dc:format`.

   The following graphic is an example of an asset's path to `dc:format`.

   ![chlimage_1-18](assets/chlimage_1-3.png)

   Notice that the `dc:format` for the asset `Fiji Red.jpg` is `image/jpeg`.

   To have this filter apply to all images, regardless of their format, set the value to `image/*` where `*` is a regular expression that is applied to all images of any format.

   To have the filter apply only to images of the type JPEG, enter a value of `image/jpeg`.

1. Define what renditions you want to include or exclude from replication.

   Characters that you can use to filter for replication include the following:

<table>
 <tbody>
  <tr>
   <td><strong>Character to use</strong></td>
   <td><strong>How it filters assets for replication</strong></td>
  </tr>
  <tr>
   <td>*</td>
   <td>Wildcard character<br /> </td>
  </tr>
  <tr>
   <td>+</td>
   <td>Includes assets for replication.</td>
  </tr>
  <tr>
   <td>-</td>
   <td>Excludes assets from replication.</td>
  </tr>
 </tbody>
</table>

   Navigate to `content/dam/<locate your asset>/jcr:content/renditions`.

   The following graphic is an example of an asset's renditions.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   If you only wanted to replicate the original, then you would enter `+original`.

   -->

