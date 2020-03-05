---
title: Dynamische Media Cloud Service configureren
description: Informatie over hoe te om Dynamische Media in de Dienst van de Wolk van de Manager van de Ervaring van Adobe te vormen.
translation-type: tm+mt
source-git-commit: ad621c24e58fba6bcc873e36544505cc50385509

---


# Dynamic Media configureren {#configuring-dynamic-media-scene-mode}

Als u de opstelling van de Manager van de Ervaring van Adobe voor verschillende milieu&#39;s, zoals voor ontwikkeling, voor het opvoeren, en voor levende productie gebruikt, moet u de Dynamische Diensten van de Wolk van Media voor elk van die milieu&#39;s vormen.

## Architectuurdiagram van Dynamische Media {#architecture-diagram-of-dynamic-media-scene-mode}

Het volgende architectuurdiagram beschrijft hoe de Dynamische Media werkt.

Met de nieuwe architectuur, is AEM verantwoordelijk voor hoofdactiva en synchroon met Dynamische Media voor activa verwerking en het publiceren:

1. Wanneer de hoofdactiva aan AEM worden geupload, wordt het herhaald aan Dynamische Media. Op dat punt, behandelt de Dynamische Media alle activa verwerking en renditiegeneratie, zoals video het coderen en dynamische varianten van een beeld.
1. Nadat de rendities worden geproduceerd, kan AEM veilig tot de verre Dynamische rendities van Media toegang hebben en voorproef (geen binaire getallen worden teruggestuurd naar de instantie AEM).
1. Nadat de inhoud klaar is om worden gepubliceerd en worden goedgekeurd, brengt het de Dynamische dienst van Media in werking om inhoud aan leveringsservers en geheim voorgeheugeninhoud bij CDN uit te duwen.

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

## Dynamische Media Cloud Service configureren {#configuring-dynamic-media-cloud-services}

**Alvorens u de Dynamische Dienst** van de Wolk van Media vormt: Nadat u uw levering-e-mail met de Dynamische geloofsbrieven van Media ontvangt, moet u [login](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) aan Dynamische Klassieke Media om uw wachtwoord te veranderen. Het wachtwoord dat in de leveringse-mail wordt verstrekt is systeem-geproduceerd en bedoeld om een tijdelijk wachtwoord slechts te zijn. Het is belangrijk dat u het wachtwoord bijwerkt zodat de Dynamische Dienst van de Wolk van Media opstelling met de correcte geloofsbrieven is.

Om dynamische media wolkendiensten te vormen:

1. Tik in AEM op het AEM-logo om toegang te krijgen tot de wereldwijde navigatieconsole.
1. Aan de linkerkant van de console, onder de rubriek van **[!UICONTROL Hulpmiddelen]** , kraken de Diensten van de **[!UICONTROL Wolk > de Dynamische Configuratie]** van Media.
1. Voor de Dynamische Browser van de Configuratie van Media pagina, in de linkerruit, tik **[!UICONTROL globaal]** (tik niet of selecteer het omslagpictogram links van **[!UICONTROL globaal]**), dan **[!UICONTROL creeer]** de kraan.
1. Op de Create Dynamische pagina van de Configuratie van Media, ga een titel, het Dynamische e-mailadres van de rekening van Media, wachtwoord in, dan selecteer uw gebied. Deze worden verstrekt aan u door Adobe in de levering e-mail. Neem contact op met Customer Support als je dit niet hebt ontvangen.
1. Klik **[!UICONTROL verbinden met Dynamische Media]**.

   >[!NOTE]
   >
   >Nadat u uw levering-e-mail met Dynamische geloofsbrieven van Media ontvangt, te [registreren in](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Dynamische Klassieke Media om uw wachtwoord te veranderen. Het wachtwoord dat in de leveringse-mail wordt verstrekt is systeem-geproduceerd en bedoeld om een tijdelijk wachtwoord slechts te zijn. Het is belangrijk dat u het wachtwoord bijwerkt zodat de Dynamische de wolkendienst van Media opstelling met de correcte geloofsbrieven is.

1. Wanneer de verbinding succesvol is, kunt u het volgende plaatsen:

   * **[!UICONTROL Bedrijf]** - de naam van de Dynamische rekening van Media. Het is mogelijk u veelvoudige Dynamische rekeningen van Media voor verschillende sub-brands, afdelingen, of verschillende het opvoeren/productiemilieu&#39;s kunt hebben.

   * **[!UICONTROL Pad voor hoofdmap van bedrijf]**

   * **[!UICONTROL Publiceer Activa]** - de optie **[!UICONTROL onmiddellijk]** betekent dat wanneer de activa worden geupload, het systeem de activa opneemt en URL/Embed onmiddellijk verstrekt. Er is geen gebruikersinterventie noodzakelijk om activa te publiceren. De optie **[!UICONTROL op Activering]** (gebrek) betekent dat u de activa moet uitdrukkelijk publiceren eerst alvorens een verbinding URL/Embed wordt verstrekt.

   * **[!UICONTROL De veilige Server]** van de Voorproef - laat u de weg URL aan uw veilige server van de renditievoorproef specificeren. Namelijk nadat de rendities worden geproduceerd, kan AEM veilig tot de verre Dynamische rendities van Media toegang hebben en voorproef (geen binaire getallen worden teruggestuurd naar de instantie AEM).
Tenzij u een speciale regeling hebt om de server van uw eigen bedrijf of een speciale server te gebruiken, adviseert Adobe Systems dat u dit het plaatsen zoals gespecificeerd verlaat.

   * **[!UICONTROL Synchroniseer alle inhoud]** - Standaard geselecteerd. Schrap deze optie als u activa van de synchronisatie aan Dynamische Media selectief wilt omvatten of uitsluiten. Het schrappen van deze optie laat u van de volgende twee Dynamische de synchronisatiewijzen van Media kiezen:

   * **[!UICONTROL Dynamische Media-synchronisatiemodus]**
      * **[!UICONTROL Toegelaten door gebrek]** - de configuratie wordt toegepast op alle omslagen door gebrek tenzij u een omslag specifiek voor het uitsluiten merkt. <!-- you can then deselect the folders that you do not want the configuration applied to.-->
      * **[!UICONTROL Gehandicapten door gebrek]** - de configuratie wordt niet toegepast op om het even welke omslag tot u uitdrukkelijk een geselecteerde omslag voor synchronisatie aan Dynamische Media merkt.
Om een geselecteerde omslag voor synchronisatie aan Dynamische Media te merken, open de pagina van Eigenschappen van uw activaomslag. Tik op het tabblad **[!UICONTROL Details]** en kies vervolgens in de vervolgkeuzelijst **[!UICONTROL Dynamische mediasynchronisatiemodus]** uit de volgende drie opties en sla vervolgens de optie **[!UICONTROL Opslaan]** op.
         * **[!UICONTROL Geërft]** - Geen expliciete synchronisatiewaarde op de omslag; in plaats daarvan, erft de omslag de synchronisatiewaarde van één van zijn voorvaderomslagen of de standaardwijze in de wolkenconfiguratie. De gedetailleerde status voor geërfte shows als hulpmiddeluiteinde.
         * **[!UICONTROL Inschakelen voor submappen]** - Alles opnemen in deze substructuur voor synchronisatie naar dynamische media. De omslag-specifieke montages treden de standaardwijze in de wolkenconfiguratie met voeten.
         * **[!UICONTROL Uitgeschakeld voor submappen]** - sluit alles in deze substructuur uit van het synchroniseren naar Dynamische media.
   >[!NOTE]
   >
   >Er is geen steun voor het versioning in Dynamische Media. Ook, is de vertraagde activering van toepassing slechts als de **[!UICONTROL Publish Activa]** in de Edit Dynamische pagina van de Configuratie van Media aan **[!UICONTROL op Activering]** wordt geplaatst, en dan slechts tot de eerste keer de activa wordt geactiveerd.
   >
   >
   >Nadat een activum wordt geactiveerd, worden om het even welke updates onmiddellijk gepubliceerd levend aan S7 Levering.

   ![dynamicmediaconfiguration2updated](assets/dynamicmediaconfiguration2updated.png)

1. Tik op **[!UICONTROL Opslaan]**.
1. Om voorproef de Dynamische inhoud van Media te beveiligen alvorens het wordt gepubliceerd, zult u &quot;whitelist&quot;de AEM auteursinstantie moeten om met Dynamische Media te verbinden:

   * Opening van een sessie aan uw Dynamische Klassieke rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html). Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Als u niet over deze informatie beschikt, neemt u contact op met Technische ondersteuning.
   * Voor de navigatiebar dichtbij het hoogste recht van de pagina, klik **[!UICONTROL Opstelling > de Opstelling van de Toepassing > publiceren Opstelling > de Server]** van het Beeld.

   * Voor de Server van het Beeld publiceer pagina, in de Publish drop-down lijst van de Context, het uitgezochte Bediende **[!UICONTROL van het Beeld van de]** Test.
   * Voor de Filter van het Adres van de Cliënt, **[!UICONTROL voegt de Tik toe]**.
   * Selecteer de controledoos om (aanzet) het adres toe te laten, en dan het IP adres van de instantie van de Auteur AEM (niet Verzender IP) in te gaan.
   * Click **[!UICONTROL Save]**.

U wordt nu gebeëindigd met de basisconfiguratie; u bent klaar om Dynamische Media te gebruiken.

Als u uw configuratie verder wilt aanpassen, kunt u om het even welke taken naar keuze voltooien onder het [Vormen van Geavanceerde Montages in Dynamische Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (Facultatief) het Vormen Geavanceerde Montages in Dynamische Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Als u de configuratie en de opstelling van Dynamische Media wilt verder aanpassen, of zijn prestaties optimaliseren, kunt u één of meerdere van de volgende *facultatieve* taken voltooien:

* [Opstelling en configuratie van Dynamische montages van Media](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Facultatief) Stemmend de prestaties van Dynamische Media](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Facultatief) Opstelling en configuratie van de Dynamische montages van Media {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Gebruik het Dynamische Klassieke (Scene7) gebruikersinterface van Media om veranderingen in uw Dynamische montages van Media aan te brengen.

Sommige taken hierboven vereisen dat u in Dynamische Klassieke Media (Scene7) hier registreert: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

De taken van de opstelling en van de configuratie omvatten het volgende:

* [Publishing-installatie voor afbeeldingsserver](#publishing-setup-for-image-server)
* [Algemene instellingen voor toepassingen configureren](#configuring-application-general-settings)
* [Kleurbeheer configureren](#configuring-color-management)
* [Het vormen activaverwerking](#configuring-asset-processing)
* [Het toevoegen van douaneMIME types voor niet gestaafde formaten](#adding-custom-mime-types-for-unsupported-formats)
* [Het creëren van partijreeks stelt aan auto-geproduceerde de Reeksen van het Beeld vooraf in en de Reeksen van de Rotatie](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Publishing-installatie voor afbeeldingsserver {#publishing-setup-for-image-server}

De Publish montages van de Opstelling bepalen hoe de activa door gebrek van Dynamische Media worden geleverd. Als geen het plaatsen wordt gespecificeerd, levert de Dynamische Media activa volgens de standaardmontages die in Publish Opstelling worden bepaald. Bijvoorbeeld, een verzoek om een beeld te leveren dat geen resolutieattribuut omvat brengt een beeld met het Standaard plaatsen van de Resolutie van Objecten op.

Om te vormen publiceer Opstelling: in Dynamische Klassieke Media, klik **[!UICONTROL Opstelling > de Opstelling van de Toepassing > publiceren Opstelling > de Server]** van het Beeld.

Het scherm van de Server van het Beeld vestigt standaardmontages voor het leveren van beelden. Zie het scherm UI voor beschrijving van elke het plaatsen.

* **[!UICONTROL Attributen]** aanvragen - Deze instellingen stellen limieten op aan afbeeldingen die vanaf de server kunnen worden geleverd.
* **[!UICONTROL Standaard de Attributen]** van het Verzoek - Deze montages hebben betrekking op de standaardverschijning van beelden.
* **[!UICONTROL De gemeenschappelijke Attributen]** van de Duimnagel - Deze montages hebben betrekking op de standaardverschijning van duimnagelbeelden.
* **[!UICONTROL Gebreken voor de Gebieden]** van de Catalogus - Deze montages hebben betrekking op de resolutie en standaardduimnageltype van beelden.
* **[!UICONTROL De Attributen]** van het Beheer van de kleur - Deze montages bepalen welke ICC kleurenprofielen worden gebruikt.
* **[!UICONTROL De Attributen]** van de verenigbaarheid - dit het plaatsen laat het leiden en het slepen paragrafen in tekstlagen toe om worden behandeld aangezien zij in versie 3.6 voor achterwaartse verenigbaarheid waren.
* **[!UICONTROL Localisatieondersteuning]** - Met deze instellingen kunt u meerdere locale kenmerken beheren. Het laat u ook een koord van de scènekaart specificeren zodat kunt u bepalen welke talen u voor de diverse tooltips in Kijkers wilt steunen. Zie **Overwegingen bij het instellen van lokalisatie van bedrijfsmiddelen** voor meer informatie over het instellen van [lokalisatieservice]](https://help.adobe.com/en_US/scene7/using/WS997f1dc4cb0179f034e07dc31412799d19a-8000.html).

#### Algemene instellingen voor toepassingen configureren {#configuring-application-general-settings}

Om de pagina van de Montages van de Toepassing te openen Algemene, in de Dynamische Klassieke Globale bar van de Navigatie van Media, klik **[!UICONTROL Opstelling > de Opstelling van de Toepassing > Algemene Montages]**.

* **[!UICONTROL Servers]** - Op rekeningprovisioning, verstrekt de Dynamische Media automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om koorden URL voor uw website en toepassingen te construeren. Deze vraag URL is specifiek voor uw rekening. Verander geen van de servernamen tenzij uitdrukkelijk de instructie wordt gegeven dit te doen door AEM-ondersteuning.

* **[!UICONTROL Afbeeldingen]** overschrijven - Met dynamische media kunnen twee bestanden niet dezelfde naam hebben. De URL-ID van elk item (bestandsnaam min de extensie) moet uniek zijn. Deze opties specificeren hoe de vervangingsactiva worden geupload: of zij het origineel vervangen of duplicaat worden. De dubbele activa worden anders genoemd met &quot;-1&quot;(bijvoorbeeld, wordt stoel.tif anders genoemd stoel-1.tif). Deze opties beïnvloeden activa die aan een verschillende omslag worden geupload dan origineel of activa met een verschillende filename uitbreiding van origineel (zoals JPG, TIF, of PNG).

* **[!UICONTROL Beschrijf in huidige omslag, de zelfde naam van het basisbeeld/de uitbreiding]** - Deze optie is de strengste regel voor vervanging. Het vereist dat u het vervangingsbeeld aan de zelfde omslag zoals origineel uploadt, en dat het vervangingsbeeld de zelfde filename uitbreiding zoals origineel heeft. Als aan deze vereisten niet wordt voldaan, wordt een duplicaat gecreeerd.

   >[!NOTE]
   >
   >Om consistentie met AEM te handhaven, kies altijd dit het plaatsen: In de huidige map **overschrijven, dezelfde naam/extensie van basisimage**

* **[!UICONTROL Overschrijven in om het even welke omslag, de zelfde naam van basisactiva/uitbreiding]** - vereist dat het vervangingsbeeld de zelfde filename uitbreiding heeft zoals het originele beeld (bijvoorbeeld, moet seat.jpg stoel.jpg, niet stoel.tif vervangen). Nochtans, kunt u het vervangingsbeeld aan een verschillende omslag uploaden dan origineel. Het bijgewerkte beeld verblijft in de nieuwe omslag; het dossier kan niet meer in zijn originele plaats worden gevonden
* **[!UICONTROL Beschrijf in om het even welke omslag, de zelfde naam van basisactiva ongeacht uitbreiding]** - Deze optie is de meest inclusieve vervangingsregel. U kunt een vervangingsbeeld aan een verschillende omslag dan origineel uploaden, een dossier met een verschillende filename uitbreiding uploaden, en het oorspronkelijke dossier vervangen. Als het oorspronkelijke dossier in een verschillende omslag is, verblijft het vervangingsbeeld in de nieuwe omslag waaraan het werd geupload.

* **[!UICONTROL Standaard kleurenprofielen]** - zie het [Vormen van het Beheer](#configuring-color-management) van de Kleur voor extra informatie.

>[!NOTE]
>
>Door gebrek, toont het systeem 15 rendities wanneer u **[!UICONTROL Renditions]** selecteert en 15 kijker vooraf instelt wanneer u **[!UICONTROL Kijkers]** in de het detailmening van de activa selecteert. Je kunt deze limiet verhogen. Zie het [Verhogen of het verminderen van het aantal beeld vooraf instelt dat de vertoning](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) of het [Verhogen van of het verminderen van het aantal kijker vooraf instelt die vertoning](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).


#### Kleurbeheer configureren {#configuring-color-management}

Het dynamische beheer van de media kleur laat u correcte activa kleuren. Met kleurcorrectie behouden ingesloten elementen hun kleurruimte (RGB, CMYK, Grijs) en ingesloten kleurprofiel. Wanneer u om een dynamische vertolking verzoekt, wordt de beeldkleur verbeterd in de ruimte van de doelkleur gebruikend CMYK, RGB, of de output van Gray. Zie [het Vormen beeld vooraf instelt](/help/assets/dynamic-media/managing-image-presets.md).

Om de standaardeigenschappen van de kleur te vormen om kleurencorrectie toe te laten wanneer het verzoeken van beelden:

1. [Logboek in Dynamische Klassieke](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html) Media gebruikend geloofsbrieven die tijdens levering worden verstrekt. Navigeer aan **[!UICONTROL Opstelling > de Opstelling]** van de Toepassing.
1. Breid het **[!UICONTROL Publish gebied van de Opstelling]** uit en selecteer de Server **[!UICONTROL van het]** Beeld. De reeks **[!UICONTROL publiceert Context]** aan **[!UICONTROL Beeld Servend]** wanneer het plaatsen van gebreken voor publiceert instanties.
1. De rol aan het bezit u moet veranderen, bijvoorbeeld een bezit in het gebied van de Attributen **[!UICONTROL van het Beheer van de]** Kleur.

   U kunt de volgende eigenschappen van de kleurencorrectie plaatsen:

   * **[!UICONTROL CMYK StandaardKleurruimte]** - Naam van het standaard CMYK kleurenprofiel
   * **[!UICONTROL Standaard grijsschaalkleurruimte]** - Naam van standaard grijs kleurenprofiel
   * **[!UICONTROL RGB Standaardkleurenruimte]** - Naam van het standaard RGB kleurenprofiel
   * **[!UICONTROL De Omzetting die van de kleur Intent]** teruggeeft - specificeert teruggeven bedoeling. Aanvaardbare waarden zijn: **[!UICONTROL perceptueel]**, **[!UICONTROL relatieve colometrisch]**, **[!UICONTROL verzadiging]**, **[!UICONTROL absolute colometrisch]**. Adobe adviseert **[!UICONTROL relatief]]**als gebrek.

1. Tik op **[!UICONTROL Opslaan]**.

Bijvoorbeeld, kon u de **[!UICONTROL RGB Ruimte]** Standaard van de Kleur aan *sRGB* plaatsen, en de Ruimte **[!UICONTROL van de StandaardKleur]** CMYK aan *WebCoated*.

Dit zou het volgende doen:

* Laat kleurencorrectie voor RGB en beelden toe CMYK.
* RGB beelden die geen kleurenprofiel hebben zullen worden verondersteld om in de *sRGB kleurenruimte* te zijn.
* De beelden CMYK die geen kleurenprofiel hebben zullen worden verondersteld om in *WebCoated* kleurenruimte te zijn.
* De dynamische vertolkingen die RGB output terugkeren, zullen het in *sRGB *kleurenruimte terugkeren.
* De dynamische vertolkingen die output CMYK terugkeren, zullen het in de *WebCoated* kleurenruimte terugkeren.

#### Het vormen activaverwerking {#configuring-asset-processing}

U kunt bepalen welke activatypes door Dynamische Media zouden moeten worden verwerkt en geavanceerde parameters van de activaverwerking aanpassen. Bijvoorbeeld, kunt u parameters van de activaverwerking specificeren om het volgende te doen:

* Zet Adobe PDF in een eCatalog activa om.
* Zet een Document van Adobe Photoshop (.PSD) in een activa van het bannermalplaatje voor verpersoonlijking om.
* Rasterize een dossier van de Illustrator van Adobe (.AI) of een dossier van Postscript van Adobe Photoshop Inkapselde (.EPS).
* Opmerking: De videoprofielen en de Profielen van de Beeldvorming kunnen worden gebruikt om de verwerking van video&#39;s en beelden te bepalen, respectievelijk.

Zie [Activa](/help/assets/add-assets.md)uploaden.

**Om activaverwerking te vormen**

1. In AEM, klik het embleem AEM om tot de globale navigatieconsole toegang te hebben, dan klik **[!UICONTROL Algemeen > CRXDE Lite]**.
1. In de linkerspoorstaaf, navigeer aan het volgende:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Onder de omslag mimeTypes, selecteer een mimenttype.
1. Op de rechterkant van de pagina van CRXDE Lite, in het lagere gedeelte:

   * dubbelklik op het **[!UICONTROL ingeschakelde]** veld. Door gebrek worden alle types van activakalm toegelaten (die aan **[!UICONTROL waar]** worden geplaatst), zo betekent de activa aan Dynamische Media voor verwerking zullen worden gesynchroniseerd. Als u wenst om dit type van activummime uit te sluiten van wordt verwerkt, verander dit het plaatsen in **[!UICONTROL vals]**.

   * dubbelklik op **[!UICONTROL jobParam]** om het bijbehorende tekstveld te openen. Zie de [Gesteunde Types](/help/assets/file-format-support.md) van Mime voor een lijst van toegestane waarden van de verwerkingsparameter u voor een bepaald mimenttype kunt gebruiken.

1. Voer een van de volgende handelingen uit:

   * Herhaal stappen 3-4 om extra mimmetypes uit te geven.
   * Voor de menubar van de pagina van CRXDE Lite, klik **[!UICONTROL sparen allen]**.

1. In de upper-left hoek van de pagina, kraan **[!UICONTROL CRXDE Lite]** om aan AEM terug te keren.

#### Het toevoegen van douaneMIME types voor niet gestaafde formaten {#adding-custom-mime-types-for-unsupported-formats}

U kunt douaneMIME types voor niet gestaafde formaten in activa toevoegen AEM. Om ervoor te zorgen dat om het even welke nieuwe knoop u in CRXDE Lite toevoegt niet door AEM wordt geschrapt, moet u ervoor zorgen dat u het MIME type vóór beweegt `image_` en zijn toegelaten waarde aan **[!UICONTROL vals]** wordt geplaatst.

**Om douane MIME types voor niet gestaafde formaten toe te voegen**

1. Van AEM, tik **[!UICONTROL Hulpmiddelen > Verrichtingen > de Console]** van het Web.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Een nieuw browser lusje opent voor de pagina van de Configuratie van de Console van het Web van de Manager van de Ervaring van **[!UICONTROL Adobe van de Console]** .

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Voor de pagina, scrol neer aan de naam *Adobe CQ Scene7 het typeDienst* van de Activa MIME zoals gezien het volgende scherm ontsproten. Aan het recht van de naam, tik **[!UICONTROL uitgeven de configuratiewaarden]** (potloodpictogram).

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Voor de pagina van de **Activa MIME van het type** van de Dienst van Adobe CQ Scene7 de pagina, klik om het even welk plusteken pictogram &lt;+>. De plaats in de lijst waar u het plusteken klikt om het nieuwe mimenttype toe te voegen is triviaal.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. Typ `DWG=image/vnd.dwg` in het lege tekstveld dat u zojuist hebt toegevoegd.

   Merk op dat het voorbeeld slechts ter illustratie `DWG=image/vnd.dwg` is. Het MIME type dat u hier toevoegt kan een ander niet gestaafd formaat zijn.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. Tik in de rechterbenedenhoek van de pagina op **[!UICONTROL Opslaan]**.

   Op dit punt, kunt u het browser lusje sluiten dat de open pagina van de Configuratie van de Console van het Web van de Manager van de Ervaring van Adobe van de Console van het Web heeft.

1. Ga terug naar het browsertabblad met uw open AEM-console.
1. Van AEM, tik **[!UICONTROL Hulpmiddelen > Algemeen > CRXDE Lite]**.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. In de linkerspoorstaaf, navigeer aan het volgende:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Sleep het mimenttype `image_vnd.dwg` en laat vallen het direct boven `image_` in de boom zoals die in het volgende het schermschot wordt gezien.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. Met het mimenttype `image_vnd.dwg` nog selecteerde, van het lusje van **[!UICONTROL Eigenschappen]** , in de **[!UICONTROL toegelaten]** rij, onder de de kolomkopbal van de **[!UICONTROL Waarde]** , klik de waarde tweemaal om de drop-down lijst van de **[!UICONTROL Waarde]** te openen.
1. Typ `false` in het veld (of selecteer **[!UICONTROL false]** in de vervolgkeuzelijst).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. Bij de upper-left hoek van de pagina van CRXDE Lite, klik **[!UICONTROL sparen allen]**.

#### Het creëren van partijreeks stelt aan auto-geproduceerde de Reeksen van het Beeld vooraf in en de Reeksen van de Rotatie {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

De partijreeks van het gebruik stelt vooraf in om de verwezenlijking van beeldreeksen of spin reeksen te automatiseren terwijl de activa aan Dynamische Media worden geupload.

Eerst, bepaal de noemende overeenkomst voor hoe de activa in een reeks zouden moeten worden gegroepeerd. U kunt een vooraf ingestelde partijreeks dan tot stand brengen die een uniek genoemde, met alle accomodatie reeks instructies is die bepaalt hoe te om de reeks te construeren gebruikend beelden die de bepaalde noemende overeenkomsten in het vooraf ingestelde recept aanpassen.

Wanneer u dossiers uploadt, leidt de Dynamische Media automatisch tot een reeks met alle dossiers die de bepaalde noemende overeenkomst in actief aanpassen vooraf instelt.

**Standaardnaamgeving configureren**

Creeer een standaard noemende overeenkomst die in om het even welk partij vastgestelde recept wordt gebruikt. De standaard noemende overeenkomst die in de vooraf ingestelde partijreeks definitie wordt geselecteerd kan al uw bedrijf zijn moet partij-produceren reeksen. Een vooraf ingestelde partijreeks wordt gecreeerd om de standaard noemende overeenkomst te gebruiken die u bepaalt. U kunt zo vele Reeks van de Partij tot stand brengen vooraf instelt met afwisselende, douane noemende overeenkomsten nodig voor een bepaalde reeks inhoud in gevallen waar er een uitzondering op het bedrijf-bepaalde gebrek noemend is.

Terwijl de vestiging een standaard noemende overeenkomst niet wordt vereist om partij te gebruiken vooraf ingestelde functionaliteit te gebruiken, adviseert de beste praktijken dat u de standaard noemende overeenkomst gebruikt om zo vele elementen van uw noemende overeenkomst te bepalen die u gegroepeerd in een reeks wilt zodat kunt u de verwezenlijking van de partijreeks stroomlijnen.

Als alternatief, merk op dat u de Code **[!UICONTROL van de]** Mening zonder beschikbare vormgebieden kunt gebruiken. In deze mening creeert u uw noemende definities van de conventie volledig gebruikend regelmatige uitdrukkingen.

Twee elementen zijn beschikbaar voor definitie, Gelijke en Naam van de Basis. Deze gebieden laten u alle elementen van een noemende overeenkomst bepalen en het deel identificeren dat wordt gebruikt om de reeks te noemen waarin zij bevat zijn. De individuele noemingsovereenkomst van een onderneming kan van één of meerdere lijnen van definitie voor elk van deze elementen gebruik maken. U kunt zo vele lijnen voor uw unieke definitie gebruiken en hen groeperen in verschillende elementen, zoals voor het Belangrijkste Beeld, het element van de Kleur, het Afwisselende element van de Mening, en het element van het Monster groeperen.

**Standaard het noemen vormen**

1. Opening van een sessie aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Als u niet over deze informatie beschikt, neemt u contact op met Technische ondersteuning.

1. Voor de navigatiebar dichtbij de bovenkant van de pagina, stelt de **[!UICONTROL Opstelling van de Tik > de Opstelling van de Toepassing > de Reeks van de Partij > Standaard het Noemen]** vooraf in.
1. Selecteer de Vorm **[!UICONTROL van de]** Mening of de Code **[!UICONTROL van de]** Mening om te specificeren hoe u informatie over elk element bekijken en wilt ingaan.

   U kunt de de controledoos van de Code **[!UICONTROL van de]** Mening selecteren om de regelmatige bouw van de uitdrukkingswaarde naast uw vormselecties te bekijken. U kunt deze waarden ingaan of veranderen helpen de elementen van de noemende overeenkomst bepalen, als de vormmening u om het even welke reden beperkt. Als uw waarden niet in de vormmening kunnen worden ontleed, worden de vormgebieden inactief.

   >[!NOTE]
   >
   >De-geactiveerde vormgebieden voeren geen bevestiging uit dat uw regelmatige uitdrukkingen correct zijn. U ziet resultaten van de regelmatige uitdrukking u voor elk element na de lijn van het Resultaat bouwt. De volledige regelmatige uitdrukking is zichtbaar bij de bodem van de pagina.

1. Breid zonodig elk element uit en ga de noemende overeenkomsten in u wilt gebruiken.
1. Doe zonodig om het even welke volgend:

   * Het lusje **[!UICONTROL voegt]** toe om een andere noemende overeenkomst voor een element toe te voegen.
   * Tik **[!UICONTROL verwijderen]** om een naamgevingsconventie voor een element te verwijderen.

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Opslaan als]** en typ een naam voor de voorinstelling.
   * Tik op **[!UICONTROL Opslaan]** als u een bestaande voorinstelling bewerkt.

**Een vooraf ingestelde batchset maken**

De dynamische Media gebruiken partijreeks vooraf instelt om activa in reeksen beelden (afwisselende beelden, kleurenopties, 360 spin) te organiseren voor vertoning in kijkers. De partijreeks stelt automatisch looppas naast activa vooraf in stelt uploadt processen in Dynamische Media.

U kunt, uw partijreeks creëren uitgeven en beheren vooraf instelt. Er zijn twee vormen van partij vooraf ingestelde definities: voor een standaard noemende overeenkomst die u opstelling, en voor douane noemende overeenkomsten zou kunnen hebben die u bij de vlucht creeert.

U kunt of de methode van het vormgebied gebruiken om een vooraf ingestelde partijreeks of de codemethode te bepalen, die u regelmatige uitdrukkingen laat gebruiken. Zoals in Standaard het Noemen, kunt u de Code van de Mening tezelfdertijd kiezen u in de Mening van de Vorm bepaalt en regelmatige uitdrukkingen gebruikt om uw definities te bouwen. Afwisselend, kunt u of mening uncheck om één of andere uitsluitend te gebruiken.

**Om een Vooraf ingestelde Reeks van de Partij te creëren**

1. Opening van een sessie aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Als u niet over deze informatie beschikt, neemt u contact op met Technische ondersteuning.

1. Voor de navigatiebar dichtbij de bovenkant van de pagina, stelt de **[!UICONTROL Opstelling van de Tik > de Opstelling van de Toepassing > de Reeks van de Partij vooraf in > Vooraf ingestelde]** Reeks van de Partij.

   Merk op dat de Vorm **[!UICONTROL van de]** Mening, zoals die in de hoger-juiste hoek van de pagina van Details wordt geplaatst, de standaardmening is.

1. In het Vooraf ingestelde paneel van de Lijst, **[!UICONTROL voeg]** toe om de definitiegebieden in het paneel van Details aan de rechterkant van het scherm te activeren.
1. In het paneel van Details, op het Vooraf ingestelde gebied van de Naam, typ een naam voor vooraf ingesteld.
1. Selecteer een vooraf ingesteld type in het vervolgkeuzemenu Type batchset.
1. Voer een van de volgende handelingen uit:

   * Als u een standaard noemende overeenkomst gebruikt die u eerder opstelling onder de Opstelling van de **[!UICONTROL Toepassing > de Reeks van de Partij > Standaard het Noemen]** vooraf instelt, breid de het Noemen van **[!UICONTROL Activa Conventies]**, en toen in de Noemen van het Dossier drop-down lijst, **[!UICONTROL Gebrek]** van de kraan uit.

   * Om een nieuwe noemende overeenkomst te bepalen aangezien u opstelling vooraf instelt, breid de het Noemen van **[!UICONTROL Activa Overeenkomsten]**, en toen in de Dossier die drop-down lijst noemt, uit **[!UICONTROL Douane]**.

1. Voor de orde van de Opeenvolging, bepaal de orde waarin de beelden worden getoond nadat de reeks samen in Dynamische Media wordt gegroepeerd.

   Door gebrek, worden uw activa alfabetisch bevolen. Nochtans, kunt u een komma-gescheiden lijst van regelmatige uitdrukkingen gebruiken om de orde te bepalen.

1. Voor Vastgestelde het Noemen en Verdrag van de Verwezenlijking, specificeer het achtervoegsel of de prefix aan de basisnaam u in de het Noemen van Activa Overeenkomst bepaalde. Ook, bepaal waar de reeks binnen de Dynamische de omslagstructuur van Media zal worden gecreeerd.

   Als u grote aantallen reeksen bepaalt, kunt u verkiezen om deze gescheiden van de omslagen te houden die de activa zelf bevatten. Bijvoorbeeld, kunt u een omslag van de Reeksen van het Beeld tot stand brengen en hier geproduceerde reeksen plaatsen.

1. Tik in het veld Details op **[!UICONTROL Opslaan]**.
1. Tik **[!UICONTROL Actief]** naast de nieuwe vooraf ingestelde naam.

   Het activeren van vooraf ingesteld zorgt ervoor dat wanneer u activa aan Dynamische Media uploadt, de vooraf ingestelde partijreeks wordt toegepast om de reeks te produceren.

**Het creëren van een Reeks van de Partij Vooraf ingesteld voor de auto-generatie van een 2D Reeks van de Rotatie**

U kunt de Reeks van het Type van Partij **[!UICONTROL Multi-AsRotatie gebruiken Reeks]** om een recept tot stand te brengen dat de generatie van 2D Reeksen van de Rotatie automatiseert. De groepering van beelden gebruikt Rij en de regelmatige uitdrukkingen van de Kolom zodat de beeldactiva behoorlijk in de overeenkomstige plaats in de multi-dimensionele serie worden gericht. Er is geen minimum of maximumaantal rijen of kolommen dat u in een multi-as spin reeks moet hebben.

Als voorbeeld, veronderstel u een multi-as spin genoemde reeks wilt tot stand brengen `spin-2dspin`. U hebt een reeks van spin vastgestelde beelden die drie rijen, met 12 beelden per rij bevatten. De beelden worden genoemd als volgt:

```
spin-01-01
 spin-01-02
 …
 spin-01-12
 spin-02-01
 …
 spin-03-12
```

Met deze informatie, zou uw recept van het Type van Batch kunnen als volgt worden gecreeerd:

![chlimage_1-560](assets/chlimage_1-560.png)

De groepering voor het gedeelde activanaamdeel van spinset wordt toegevoegd aan het gebied van de **Gelijke** (zoals benadrukt). Het veranderlijke deel van de activanaam die de rij en de kolom bevat wordt toegevoegd aan de gebieden van de **Rij** en van de **Kolom** , respectievelijk.

Wanneer de Reeks van de Rotatie wordt geupload en gepubliceerd, zou u de naam van het 2D Vastgestelde recept van de Rotatie activeren dat onder de Reeks van de **Partij vermeld is vooraf instelt** in de de dialoogdoos van de Opties **van de** Upload van de Baan.

**Om een Reeks van de Partij tot stand te brengen die voor de auto-generatie van een 2D Reeks van de Rotatie vooraf in wordt gesteld**

1. Opening van een sessie aan uw Dynamische Klassieke (Scene7) rekening van Media: [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Uw geloofsbrieven en opening van een sessie werden verstrekt door Adobe op het tijdstip van levering. Als u niet over deze informatie beschikt, neemt u contact op met Technische ondersteuning.

1. Voor de navigatiebar dichtbij de bovenkant van de pagina, klik **[!UICONTROL de Opstelling > de Opstelling van de Toepassing > de Reeks van de Partij vooraf instelt > de Reeks van de Partij Vooraf ingesteld**.

   Merk op dat de Vorm **[!UICONTROL van de]** Mening, zoals die in de hoger-juiste hoek van de pagina van Details wordt geplaatst, de standaardmening is.

1. In het Vooraf ingestelde paneel van de Lijst, voegt de klik **[!UICONTROL toe]** om de definitiegebieden in het paneel van Details op de rechterkant van het scherm te activeren.
1. In het paneel van Details, op het Vooraf ingestelde gebied van de Naam, typ een naam voor vooraf ingesteld.
1. Selecteer in het vervolgkeuzemenu Type Batch-set de optie **[!UICONTROL Asset Set]**.
1. Selecteer in de vervolgkeuzelijst Subtype de optie **[!UICONTROL Multi-Axis Spin Set]**.
1. Breid de het Noemen van **[!UICONTROL Activa Conventies]** uit, en dan in de het Noemen van het Dossier drop-down lijst, klik **[!UICONTROL Douane]**.
1. Gebruik de attributen van de Naam **[!UICONTROL van de]** Gelijke en, naar keuze, van de Naam **[!UICONTROL van de]** Basis om een regelmatige uitdrukking voor het noemen van beeldactiva te bepalen die omhoog het groeperen maken.

   Bijvoorbeeld, zou uw letterlijke regelmatige uitdrukking van de Gelijke als het volgende kunnen kijken:

   `(w+)-w+-w+`

1. Breid de Positie **[!UICONTROL van de Kolom van de]** Rij uit, en bepaal dan het naamformaat voor de positie van beeldactiva binnen de 2D Vastgestelde serie van de Rotatie.

   Gebruik de haakje om de rij of kolompositie in het dossier te omarmen - noem.

   Bijvoorbeeld, voor uw rijregelmatige uitdrukking, zou het als het volgende kunnen kijken:

   `\w+-R([0-9]+)-\w+`

   or

   `\w+-(\d+)-\w+`

   Voor uw kolom regelmatige uitdrukking, zou het als het volgende kunnen kijken:

   `\w+-\w+-C([0-9]+)`

   or

   `\w+-\w+-C(\d+)`

   Vergeet niet dat dit slechts voorbeelden zijn. U kunt uw regelmatige uitdrukking tot stand brengen nochtans wilt u uw behoeften aanpassen.

   >[!NOTE]
   >
   >Als de combinatie van rij en kolom regelmatige uitdrukkingen niet de positie van de activa binnen de multi-dimensionale spinsetserie kan bepalen, dan wordt dat activa niet toegevoegd aan de reeks en een fout wordt geregistreerd.

1. Voor Vastgestelde het Noemen en Verdrag van de Verwezenlijking, specificeer het achtervoegsel of de prefix aan de basisnaam u in de het Noemen van Activa Overeenkomst bepaalde.

   Ook, bepaal waar de centrifugereeks binnen de Dynamische Klassieke de omslagstructuur van Media zal worden gecreeerd.

   Als u grote aantallen reeksen bepaalt, kunt u verkiezen om deze gescheiden van de omslagen te houden die de activa zelf bevatten. Bijvoorbeeld, creeer een omslag van de Reeksen van de Rotatie om geproduceerde reeksen hier te plaatsen.

1. Klik in het veld Details op **[!UICONTROL Opslaan]**.
1. Klik **[!UICONTROL Actief]** naast de nieuwe vooraf ingestelde naam.

   Het activeren van vooraf ingesteld zorgt ervoor dat wanneer u activa aan Dynamische Media uploadt, de vooraf ingestelde partijreeks wordt toegepast om de reeks te produceren.

### (Facultatief) Stemmend de prestaties van Dynamische Media {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Om Dynamische Media <!--(with `dynamicmedia_scene7` run mode)--> regelmatig lopend te houden, adviseert Adobe de volgende synchronisatieprestaties/scalability het verfijnen uiteinden:

* Werk de vooraf bepaalde de werkdragers van de de rijwerker van het Granite- werkschema (videoactiva) bij draden.
* Werk de vooraf bepaalde Granite tijdelijke werkschema (beelden en niet-videoactiva) bij van de rijwerkerdraden van de rij voorbijgaande werkkracht draden.
* Werk het maximum bij uploadt verbindingen aan de Dynamische Klassieke server van Media.

#### De Granite Transient Workflow Queue bijwerken {#updating-the-granite-transient-workflow-queue}

De Granite Transit Workflow-wachtrij wordt gebruikt voor de **[!UICONTROL DAM Update Asset]** -workflow. In Dynamische Media, wordt het gebruikt voor beeldopname en verwerking.

**Om de Granite Transient Workflow Queue bij te werken**

1. Navigeer aan [https://&lt;server>/systeem/console/configMgr](https://localhost:4502/system/console/configMgr) en onderzoek naar **Rij: Granite Transient Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat PID OSGi dynamisch wordt geproduceerd.

1. Op het gebied van de **[!UICONTROL Maximum Parallelle Banen]** , verander het aantal in de gewenste waarde.

   Door gebrek, hangt het maximumaantal parallelle banen van het aantal beschikbare cores van cpu af. Bijvoorbeeld, op een 4 kernserver, wijst het 2 arbeidersdraden toe. (De waarde van A tussen 0.0 en 1.0 is gebaseerde verhouding, of om het even welke aantallen groter dan 1 zullen het aantal arbeidersdraden toewijzen.)

   Adobe adviseert dat 32 de **[!UICONTROL Maximum Parallelle Banen]** worden gevormd om zwaar te steunen uploadt van dossiers aan Dynamische Klassieke Media (Scene7) voldoende.

   ![chlimage_1](assets/chlimage_1.jpeg)

1. Tik op **[!UICONTROL Opslaan]**.

#### De Granite Workflow-wachtrij bijwerken {#updating-the-granite-workflow-queue}

De Granite Werkstroom-wachtrij wordt gebruikt voor niet-tijdelijke werkstromen. In Dynamische Media, gebruikte het om video met de **[!UICONTROL Dynamische Media te verwerken codeerde Video]** werkschema.

**Om de Granite Workflow Queue bij te werken**

1. Navigeer aan `https://<server>/system/console/configMgr` en onderzoek naar **Rij: Graniet Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat PID OSGi dynamisch wordt geproduceerd.

1. Op het gebied van de **[!UICONTROL Maximum Parallelle Banen]** , verander het aantal in de gewenste waarde.

   Door gebrek, hangt het maximumaantal parallelle banen van het aantal beschikbare cores van cpu af. Bijvoorbeeld, op een 4 kernserver, wijst het 2 arbeidersdraden toe. (De waarde van A tussen 0.0 en 1.0 is gebaseerde verhouding, of om het even welke aantallen groter dan 1 zullen het aantal arbeidersdraden toewijzen.)

   Voor de meeste gebruiksgevallen, is 0.5 standaard het plaatsen voldoende.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Tik op **[!UICONTROL Opslaan]**.

#### Het bijwerken van Scene7 uploadt verbinding {#updating-the-scene-upload-connection}

Scene7 uploadt het plaatsen van de Verbinding synchroniseert activa AEM aan Dynamische Klassieke servers van Media.

**Om Scene7 bij te werken upload verbinding**

1. Blader naar `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Op het gebied **[!UICONTROL van het Aantal verbindingen]** en/of het gebied van de **[!UICONTROL Actieve baanonderbreking]** , verander het aantal zoals gewenst.

   Het **[!UICONTROL Aantal verbindingen]** die controleert het maximumaantal verbindingen plaatsen van HTTP toegestaan voor AEM aan Dynamische Media uploadt; typisch, is de vooraf bepaalde waarde van 10 verbindingen voldoende.

   De **[!UICONTROL Actieve baanonderbreking]** die bepaalt de wachttijd voor de geuploade Dynamische activa van Media die in leveringsserver moeten worden gepubliceerd plaatst. Deze waarde is 2100 seconden of 35 minuten door gebrek.

   Voor de meeste gebruiksgevallen is de instelling van 2100 voldoende.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Tik op **[!UICONTROL Opslaan]**.

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

