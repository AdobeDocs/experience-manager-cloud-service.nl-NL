---
title: Dynamic Media-Cloud Service configureren
description: Leer hoe u Dynamic Media in Adobe Experience Manager configureert als Cloud Service.
topic: Beheerder
translation-type: tm+mt
source-git-commit: 0e951053a690d091d9b6462138042fd0c59fe5d3
workflow-type: tm+mt
source-wordcount: '3752'
ht-degree: 3%

---


# Informatie over het configureren van Dynamic Media-Cloud Service {#configuring-dynamic-media}

Als u Adobe Experience Manager voor verschillende omgevingen gebruikt, zoals ontwikkeling, staging en live productie, configureert u Dynamic Media-Cloud Services voor elk van deze omgevingen.

## Architectuurdiagram van Dynamic Media {#architecture-diagram-of-dynamic-media}

In het volgende architectuurdiagram wordt beschreven hoe Dynamic Media werkt.

Met de nieuwe architectuur is Experience Manager verantwoordelijk voor primaire bronactiva en syncs met Dynamic Media voor activa verwerking en het publiceren:

1. Wanneer het primaire bronelement als Cloud Service naar Adobe Experience Manager wordt geüpload, wordt het naar Dynamic Media gerepliceerd. Op dat moment verwerkt Dynamic Media alle processen voor het genereren van elementen, zoals videocodering en dynamische varianten van een afbeelding.
1. Nadat de vertoningen worden geproduceerd, kan de Experience Manager als Cloud Service tot de verre vertoningen van Dynamic Media veilig toegang hebben en voorproef (geen binaire getallen worden teruggestuurd naar de Experience Manager als instantie van de Cloud Service).
1. Nadat de inhoud klaar is om te publiceren en goed te keuren, brengt het de dienst van Dynamic Media teweeg om inhoud aan leveringsservers en geheim voorgeheugeninhoud bij CDN (het Netwerk van de Levering van de Inhoud) te duwen.

![chlimage_1-550](assets/chlimage_1-550.png)

>[!NOTE]
>
>Voor de volgende lijst met functies moet u de CDN uit de doos gebruiken die is gebundeld met Adobe Experience Manager - Dynamic Media. Een andere aangepaste CDN wordt niet ondersteund met deze functies.
>
>* [Smart Imaging](/help/assets/dynamic-media/imaging-faq.md)
>* [Cache-validatie](/help/assets/dynamic-media/invalidate-cdn-cache-dynamic-media.md)
>* [Hotlink-beveiliging](/help/assets/dynamic-media/hotlink-protection.md)
>* [HTTP/2-levering van inhoud](/help/assets/dynamic-media/http2faq.md)
>* URL omleiden op CDN-niveau
>* Akamai ChinaCDN (voor optimale levering in China)


<!-- OBSOLETE CONTENT

## (Optional) Migrating Dynamic Media presets and configurations from 6.3 to 6.5 Zero Downtime {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

If you are upgrading Experience Manager as a Cloud Service Dynamic Media from 6.3 to 6.4 or 6.5 (which now includes the ability for zero downtime deployments), you are required to run the following curl command to migrate all your presets and configurations from `/etc` to `/conf` in CRXDE Lite.

>[!NOTE]
>
>If you run your Experience Manager as a Cloud Service instance in compatibility mode--that is, you have the compatibility packaged installed--you do not need to run these commands.

For all upgrades, either with or without the compatibility package, you can copy the default, out-of-the-box viewer presets that originally came with Dynamic Media by running the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets/viewer.pushviewerpresets.json`

To migrate any custom viewer presets and configurations that you have created from `/etc` to `/conf`, run the following Linux curl command:

`curl -u admin:admin -X POST https://<server_address>:<server_port>/libs/settings/dam/dm/presets.migratedmcontent.json`

-->

## Dynamic Media-configuratie maken in Cloud Services {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. Tik in Experience Manager als Cloud Service op de Experience Manager als het logo van de Cloud Service om toegang te krijgen tot de algemene navigatieconsole.
1. Tik links van de console op het pictogram Extra en tik op **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Tik in het linkerdeelvenster van de Dynamic Media Configuration Browser page op **[!UICONTROL global]** (tik niet op of selecteer het mappictogram links van **[!UICONTROL global]**). Tik vervolgens op **[!UICONTROL Create]**.
1. Voer op de pagina **[!UICONTROL Create Dynamic Media Configuration]** een titel in, het e-mailadres van de Dynamic Media-account, het wachtwoord en selecteer vervolgens uw regio. Deze informatie wordt u door Adobe in de levering-e-mail verstrekt. Neem contact op met de klantenservice van Adobe als u dit e-mailbericht niet hebt ontvangen.
1. Klik op **[!UICONTROL Connect to Dynamic Media]**.
1. Voer in het dialoogvenster **[!UICONTROL Change Password]** in het veld **[!UICONTROL New Password]** een nieuw wachtwoord in dat uit 8-25 tekens bestaat. Het wachtwoord moet ten minste een van de volgende elementen bevatten:

   * Hoofdletter
   * Kleine letter
   * Getal
   * Speciaal teken: `# $ & . - _ : { }`

   Het veld **[!UICONTROL Current Password]** is opzettelijk voorgevuld en verborgen voor interactie.

   Indien nodig kunt u de spelling controleren van een wachtwoord dat u hebt getypt of getypt door op het oogpictogram voor het wachtwoord te tikken om het wachtwoord weer te geven. Tik nogmaals op het pictogram om het wachtwoord te verbergen.

1. Typ in het veld **[!UICONTROL Repeat Password]** het nieuwe wachtwoord opnieuw en tik vervolgens op **[!UICONTROL Done.]**

   Het nieuwe wachtwoord wordt opgeslagen wanneer u op **[!UICONTROL Save]** in de rechterbovenhoek van de pagina **[!UICONTROL Create Dynamic Media Configuration]** tikt.

   Als u **[!UICONTROL Cancel]** in **[!UICONTROL Change Password]** dialoogdoos hebt getikt, moet u een nieuw wachtwoord nog ingaan wanneer u sparen de onlangs gecreeerde configuratie van Dynamic Media.

   Zie ook [Het wachtwoord wijzigen in Dynamic Media](#change-dm-password).

1. Wanneer de verbinding tot stand is gebracht, kunt u het volgende instellen:

   | Eigenschap | Beschrijving |
   |---|---|
   | Bedrijf | De naam van de Dynamic Media-account. Het is mogelijk dat u meerdere Dynamic Media-accounts hebt voor verschillende submerken, divisies of omgevingen waarin onderdelen worden opgedeeld/geproduceerd. |
   | Pad naar hoofdmap van bedrijf | Het pad naar de hoofdmap van uw bedrijf. |
   | Middelen publiceren | U kunt uit de volgende drie opties kiezen:<br>**[!UICONTROL Immediately]**: Wanneer elementen worden geüpload, neemt het systeem de elementen op en wordt direct de URL/Embed weergegeven. Er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>**[!UICONTROL Upon Activation]**: U moet het element eerst expliciet publiceren voordat er een koppeling URL/Embed is opgegeven.<br>**[!UICONTROL Selective Publish]**: Elementen worden automatisch gepubliceerd voor een beveiligde voorvertoning. Zij kunnen ook uitdrukkelijk aan Experience Manager als Cloud Service worden gepubliceerd zonder aan DMS7 voor levering in het openbare domein te publiceren. In de toekomst is deze optie bedoeld om elementen als Cloud Service naar Experience Manager te publiceren en elementen naar Dynamic Media te publiceren, die elkaar wederzijds uitsluiten. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies als Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. Of u kunt elementen alleen in de Experience Manager publiceren als een Cloud Service voor een voorvertoning. dezelfde activa worden niet in DMS7 gepubliceerd voor levering in het publieke domein. |
   | Beveiligde voorvertoningsserver | Hier kunt u het URL-pad naar de voorvertoningsserver voor veilige vertoningen opgeven. Met andere woorden, nadat uitvoeringen zijn gegenereerd, kan Experience Manager als Cloud Service veilig toegang krijgen tot de externe Dynamic Media-uitvoeringen en deze voorvertonen (er worden geen binaire bestanden teruggestuurd naar de Experience Manager als een instantie Cloud Service).<br>Tenzij u een speciale regeling hebt om de server van uw eigen bedrijf of een speciale server te gebruiken, adviseert Adobe dat u dit het plaatsen zoals gespecificeerd verlaat. |
   | Alle inhoud synchroniseren | Standaard geselecteerd. Schakel deze optie uit als u elementen selectief wilt opnemen in of uitsluiten van de synchronisatie met Dynamic Media. Als u deze optie uitschakelt, kunt u kiezen uit de volgende twee Dynamic Media-synchronisatiemodi:<br>**[!UICONTROL Dynamic Media sync mode]**<br>**[!UICONTROL Enable by default]**: De configuratie wordt standaard toegepast op alle mappen, tenzij u een map markeert die specifiek is bedoeld voor uitsluiting.<!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL Disabled by default]**: De configuratie wordt pas op een map toegepast als u een geselecteerde map expliciet markeert voor synchronisatie met Dynamic Media.<br>Als u een geselecteerde map wilt markeren voor synchronisatie met Dynamic Media, selecteert u een elementmap en tikt u vervolgens op de werkbalk op  **[!UICONTROL Properties]**. Kies op het tabblad **[!UICONTROL Details]** in de vervolgkeuzelijst **[!UICONTROL Dynamic Media sync mode]** een van de volgende drie opties. Tik **[!UICONTROL Save]** als u klaar bent. *Onthoud: Deze drie opties zijn niet beschikbaar als u **Alle inhoud eerder**synchroniseren hebt geselecteerd.* Zie ook  [Werken met Selectief publiceren op mapniveau in Dynamic Media.](/help/assets/dynamic-media/selective-publishing.md)<br>**[!UICONTROL Inherited]**: Geen expliciete synchronisatiewaarde in de map. In plaats daarvan neemt de map de synchronisatiewaarde over van een van de bovenliggende mappen of de standaardmodus in de cloudconfiguratie. De gedetailleerde status voor overgeërfde presentaties wordt weergegeven als knopinfo.<br>**[!UICONTROL Enable for subfolders]**: Neem alles op in deze substructuur voor synchronisatie met Dynamic Media. De mapspecifieke instellingen overschrijven de standaardmodus in de cloudconfiguratie.<br>**[!UICONTROL Disabled for subfolders]**: Sluit alles in deze substructuur uit van synchroniseren naar Dynamic Media. |

   >[!NOTE]
   >
   >Er is geen ondersteuning voor versiebeheer in Dynamische media. Uitgestelde activering wordt ook alleen toegepast als **[!UICONTROL Publish Assets]** in de pagina Dynamic Media-configuratie bewerken is ingesteld op **[!UICONTROL Upon Activation]**. En dan, slechts tot de eerste keer wordt het middel geactiveerd.
   >
   >
   >Nadat een middel wordt geactiveerd, worden om het even welke updates onmiddellijk gepubliceerd live aan S7 Levering.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. Tik op **[!UICONTROL Save]**. Het nieuwe Dynamic Media-wachtwoord en -configuratie worden opgeslagen. Als u **[!UICONTROL Cancel]** in plaats daarvan hebt getikt, wordt het wachtwoord niet bijgewerkt.
1. Tik in het dialoogvenster **[!UICONTROL Configuring Dynamic Media]** op **[!UICONTROL OK]** om de configuratie te starten.

   >[!IMPORTANT]
   >
   >Wanneer de nieuwe configuratie van Dynamic Media zijn opstelling beëindigt, ontvangt u een statusbericht binnen Experience Manager als Inbox van de Cloud Service.
   >
   >Dit Inbox bericht deelt u als de configuratie of succesvol of niet was.
   > Zie [Problemen met een nieuwe Dynamic Media-configuratie oplossen](#troubleshoot-dm-config) en [Uw Postvak In](/help/sites-cloud/authoring/getting-started/inbox.md) voor meer informatie.

1. Om Dynamic Media-inhoud veilig voor te vertonen voordat deze wordt gepubliceerd, gebruikt Experience Manager als Cloud Service standaard tokenverificatie. Nochtans, kunt u &quot;lijst van gewenste personen&quot;meer IPs ook om gebruikers toegang tot veilig voorproefinhoud te verlenen. Ga als volgt te werk om deze handeling in te stellen: <!-- To securely preview Dynamic Media content before it gets published, you must "allowlist" the Experience Manager as a Cloud Service author instance to connect to Dynamic Media. To set up this action, do the following: -->

   * Open [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meld u vervolgens aan bij uw account. Adobe heeft uw aanmeldingsgegevens en aanmeldingsgegevens op het moment van de levering verstrekt. Als u deze informatie niet hebt, neemt u contact op met de klantenservice van Adobe.
   * Tik op de navigatiebalk in de rechterbovenhoek van de pagina op **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
   * Selecteer **[!UICONTROL Test Image Serving]** in de vervolgkeuzelijst op de pagina Publiceren afbeeldingsserver.**[!UICONTROL Publish Context]**
   * Tik **[!UICONTROL Add]** voor het clientadresfilter.
   * Om (draai) het adres toe te laten, selecteer de controledoos, dan ga het IP adres van de instantie van de Auteur van de Experience Manager (niet Verzender IP) in.
   * Klik op **[!UICONTROL Save]**.

U wordt nu gebeëindigd met de basisconfiguratie; U kunt Dynamic Media gebruiken.

Als u uw configuratie verder wilt aanpassen, kunt u naar keuze om het even welke taken voltooien onder [Het Vormen Geavanceerde Montages in Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

### Problemen met een nieuwe Dynamic Media-configuratie {#troubleshoot-dm-config} oplossen

Wanneer een nieuwe configuratie van Dynamic Media zijn opstelling beëindigt, ontvangt u een statusbericht binnen Experience Manager als Inbox van de Cloud Service. Deze melding geeft aan of de configuratie is gelukt of niet, zoals in de volgende afbeeldingen in het Postvak In wordt getoond.

![Experience Manager Postvak IN gelukt](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![Fout in Experience Manager Inbox](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

Zie ook [Uw Postvak IN](/help/sites-cloud/authoring/getting-started/inbox.md).

**Een nieuwe Dynamic Media-configuratie oplossen**

1. Tik in de rechterbovenhoek van de Experience Manager als Cloud Service op het belpictogram en tik op **[!UICONTROL View All]**.
1. Tik op de pagina Inbox op het succesbericht om een overzicht te lezen van de status en logboeken van de configuratie.

   Als de configuratie ontbrak, tik het mislukkingsbericht gelijkend op het volgende screenshot.

   ![Dynamic Media instellen mislukt](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. Controleer op de pagina **[!UICONTROL DMSETUP]** de configuratiedetails die de fout beschrijven. Let met name op foutberichten of foutcodes. Neem contact op met de klantenservice van Adobe voor deze informatie.

   ![Dynamic Media-instellingspagina](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Het wachtwoord wijzigen in Dynamic Media {#change-dm-password}

Het verlopen van wachtwoorden in Dynamic Media is ingesteld op 100 jaar vanaf de huidige systeemdatum.

Het wachtwoord moet ten minste een van de volgende elementen bevatten:

* Hoofdletter
* Kleine letter
* Getal
* Speciaal teken: `# $ & . - _ : { }`

Indien nodig kunt u de spelling controleren van een wachtwoord dat u hebt getypt of getypt door op het oogpictogram voor het wachtwoord te tikken om het wachtwoord weer te geven. Tik nogmaals op het pictogram om het wachtwoord te verbergen.

Het gewijzigde wachtwoord wordt opgeslagen wanneer u **[!UICONTROL Save]** in de rechterbovenhoek van de pagina **[!UICONTROL Edit Dynamic Media Configuration]** tikt.

1. Tik in Experience Manager als Cloud Service op de Experience Manager als het logo van de Cloud Service om toegang te krijgen tot de algemene navigatieconsole.
1. Tik links van de console op het pictogram Extra en tik op **[!UICONTROL Cloud Services > Dynamic Media Configuration.]**
1. Tik op **[!UICONTROL global]** op de pagina Dynamic Media Configuration Browser in het linkerdeelvenster. Tik niet op het mappictogram of selecteer dit links van **[!UICONTROL global]**. Tik vervolgens op **[!UICONTROL Edit.]**
1. Tik op de pagina **[!UICONTROL Edit Dynamic Media Configuration]**, direct onder het veld **[!UICONTROL Password]**, op **[!UICONTROL Change Password.]**
1. Voer in het dialoogvenster **[!UICONTROL Change Password]** de volgende handelingen uit:

   * Voer in het veld **[!UICONTROL New Password]** een nieuw wachtwoord in.

      Het veld **[!UICONTROL Current Password]** is opzettelijk voorgevuld en verborgen voor interactie.

   * Typ in het veld **[!UICONTROL Repeat Password]** het nieuwe wachtwoord opnieuw en tik vervolgens op **[!UICONTROL Done.]**

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Edit Dynamic Media Configuration]** op **[!UICONTROL Save]** en tik vervolgens op **[!UICONTROL OK.]**

## (Optioneel) Geavanceerde instellingen configureren in Dynamic Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Als u de configuratie en installatie van Dynamic Media verder wilt aanpassen of de prestaties ervan wilt optimaliseren, kunt u een of meer van de volgende *optionele*-taken uitvoeren:

* [Dynamic Media-instellingen instellen en configureren](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Optioneel) De prestaties van Dynamic Media afstemmen](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Optioneel) Dynamic Media-instellingen {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings} instellen en configureren

Met de Dynamic Media Classic-gebruikersinterface kunt u uw Dynamic Media-instellingen wijzigen.

Voor sommige van de bovenstaande taken is het vereist dat u de [Klassieke Dynamic Media-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) opent en zich vervolgens aanmeldt bij uw account.

De taken van de opstelling en van de configuratie omvatten het volgende:

* [Publicatie-instelling voor afbeeldingsserver](#publishing-setup-for-image-server)
* [Algemene instellingen van toepassing configureren](#configuring-application-general-settings)
* [Kleurbeheer configureren](#configuring-color-management)
* [MIME-typen bewerken voor ondersteunde indelingen](#editing-mime-types-for-supported-formats)
* [MIME-typen toevoegen voor niet-ondersteunde indelingen](#adding-mime-types-for-unsupported-formats)

<!-- * [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### Publicatie-instelling voor afbeeldingsserver {#publishing-setup-for-image-server}

De instellingen voor Publicatie-instellingen bepalen hoe elementen standaard worden geleverd door Dynamic Media. Als er geen instelling is opgegeven, levert Dynamic Media een element op basis van de standaardinstellingen die zijn gedefinieerd in Publicatie-instelling. Als u bijvoorbeeld een aanvraag indient om een afbeelding te leveren die geen resolutiekenmerk bevat, levert dit een afbeelding op met de standaardinstelling Objectresolutie.

Publicatie-instelling configureren: Klik in Dynamic Media Classic op **[!UICONTROL Setup > Application Setup > Publish Setup > Image Server]**.

Het scherm van de Server van het Beeld vestigt standaardmontages voor het leveren van beelden. Zie het scherm UI voor beschrijving van elke het plaatsen.

**[!UICONTROL Request Attributes]** - Met deze instellingen worden limieten ingesteld voor afbeeldingen die van de server kunnen worden geleverd.
**[!UICONTROL Default Request Attributes]** - Deze instellingen hebben betrekking op de standaardweergave van afbeeldingen.
**[!UICONTROL Common Thumbnail Attributes]** - Deze instellingen hebben betrekking op de standaardweergave van miniatuurafbeeldingen.
**[!UICONTROL Defaults for Catalog Fields]**- Deze instellingen hebben betrekking op de resolutie en het standaardtype miniatuur van afbeeldingen.
**[!UICONTROL Color Management Attributes]** - Deze instellingen bepalen welke ICC-kleurprofielen worden gebruikt.
**[!UICONTROL Compatibility Attributes]** - Met deze instelling kunnen alinea&#39;s met regelafstand en navolgende in tekstlagen op dezelfde manier worden behandeld als in versie 3.6, voor achterwaartse compatibiliteit.
**[!UICONTROL Localization Support]** - Met deze instellingen kunt u meerdere kenmerken voor de landinstelling beheren. U kunt hiermee ook een landinstellingenkaarttekenreeks opgeven, zodat u kunt definiëren welke talen u wilt ondersteunen voor de verschillende knopinfo in Viewers. Zie [Overwegingen bij het instellen van lokalisatie van middelen](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#considerations-when-setting-up-localization-of-assets) voor meer informatie over het instellen van **[!UICONTROL Localization Support]**.

#### Algemene instellingen van toepassing configureren {#configuring-application-general-settings}

Als u de pagina Algemene instellingen toepassing wilt openen, klikt u op **[!UICONTROL Setup > Application Setup > General Settings.]** in de klassieke algemene navigatiebalk van Dynamic Media

**[!UICONTROL Servers]** - Dynamic Media levert automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account. Wijzig geen van de servernamen, tenzij expliciet de instructie wordt gegeven dit te doen door Experience Manager als ondersteuning voor Cloud Servicen.
**[!UICONTROL Overwrite Images]** - Dynamic Media staat niet toe dat twee bestanden dezelfde naam hebben. De URL-id van elk item (de bestandsnaam minus de extensie) moet uniek zijn. Met deze opties geeft u op hoe vervangende elementen worden geüpload: of zij het origineel vervangen of dupliceren. Dubbele elementen krijgen de naam &quot;-1&quot;. (De naam van bijvoorbeeld stoel.tif wordt gewijzigd in stoel-1.tif). Deze opties zijn van invloed op elementen die zijn geüpload naar een andere map dan het origineel of op elementen met een andere bestandsextensie dan het origineel.
**[!UICONTROL Overwrite in current folder, same base image name/extension]** - Deze optie is de strengste regel voor vervanging. Hiervoor moet u de vervangende afbeelding uploaden naar dezelfde map als het origineel en dezelfde bestandsextensie hebben als het origineel. Als niet aan deze vereisten wordt voldaan, wordt een dubbel gecreeerd. Om consistentie met Experience Manager als Cloud Service te handhaven, altijd kiezen **[!UICONTROL Overwrite in current folder, same base image name/extension]**.
**[!UICONTROL Overwrite in any folder, same base asset name/extension]** - Vereist dat de vervangende afbeelding dezelfde bestandsextensie heeft als de oorspronkelijke afbeelding. bijvoorbeeld stoel.jpg moet stoel.jpg vervangen, niet stoel.tif. U kunt de vervangende afbeelding echter naar een andere map uploaden dan het origineel. De bijgewerkte afbeelding staat in de nieuwe map; het bestand kan niet meer op de oorspronkelijke locatie worden gevonden.
**[!UICONTROL Overwrite in any folder, same base asset name regardless of extension]** - Deze optie is de meest inclusieve vervangingsregel. U kunt een vervangende afbeelding uploaden naar een andere map dan het origineel, een bestand met een andere bestandsextensie uploaden en het oorspronkelijke bestand vervangen. Als het oorspronkelijke bestand zich in een andere map bevindt, bevindt de vervangende afbeelding zich in de nieuwe map waarnaar het is geüpload.
**[!UICONTROL Default Color Profiles]** - Zie Kleurbeheer  [configureren ](#configuring-color-management) voor meer informatie. Standaard geeft het systeem 15 uitvoeringen weer wanneer u **[!UICONTROL Renditions]** en 15 viewervoorinstellingen selecteert wanneer u **[!UICONTROL Viewers]** in de gedetailleerde weergave van de asset selecteert. U kunt deze limiet verhogen. Zie [Het weergegeven aantal afbeeldingsvoorinstellingen vergroten of verkleinen](/help/assets/dynamic-media/managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) of [Het weergegeven aantal viewervoorinstellingen vergroten of verkleinen](/help/assets/dynamic-media/managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Kleurbeheer configureren {#configuring-color-management}

Met Dynamic Media-kleurbeheer kunt u correcte elementen kleuren. Met kleurcorrectie behouden ingesloten elementen hun kleurruimte (RGB, CMYK, Grijs) en ingesloten kleurprofiel. Wanneer u een dynamische uitvoering aanvraagt, wordt de afbeeldingskleur met CMYK-, RGB- of grijsuitvoer gecorrigeerd naar de doelkleurruimte. Zie [Voorinstellingen voor afbeeldingen configureren](/help/assets/dynamic-media/managing-image-presets.md).

De standaardkleureigenschappen configureren voor het inschakelen van kleurcorrectie bij het aanvragen van afbeeldingen:

1. Open de [Dynamic Media Klassieke bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started) en meld u vervolgens aan bij uw account met de aanmeldingsgegevens die tijdens de provisioning zijn opgegeven.
1. Ga naar **[!UICONTROL Setup > Application Setup]**.
1. Vouw het gebied **[!UICONTROL Publish Setup]** uit en selecteer **[!UICONTROL Image Server]**. Stel **[!UICONTROL Publish Context]** in op **[!UICONTROL Image Serving]** wanneer u standaardinstellingen voor publicatie-exemplaren instelt.
1. Blader naar de eigenschap die u moet wijzigen, bijvoorbeeld een eigenschap in het gebied **[!UICONTROL Color Management Attributes]**.
U kunt de volgende eigenschappen voor kleurcorrectie instellen:

   | Eigenschap | Beschrijving |
   |---|---|
   | CMYK-standaardkleurruimte | Naam van het standaard CMYK-kleurprofiel. |
   | Standaardkleurruimte grijswaarden | Naam van het standaardkleurprofiel Grijs. |
   | Standaardkleurruimte RGB | Naam van het standaard RGB-kleurprofiel. |
   | Render-intentie kleurconversie | Geeft de render-intentie aan. Acceptabele waarden zijn: **[!UICONTROL perceptual]**, **[!UICONTROL relative colometric]**, **[!UICONTROL saturation]**, **[!UICONTROL absolute colometric.]** Adobe raadt **[!UICONTROL relative]** als standaardwaarde aan. |

1. Tik op **[!UICONTROL Save]**.

U kunt bijvoorbeeld **[!UICONTROL RGB Default Color Space]** instellen op *sRGB* en **[!UICONTROL CMYK Default Color Space]** op *WebCoated*.

Dit doet het volgende:

* Hiermee schakelt u kleurcorrectie in voor RGB- en CMYK-afbeeldingen.
* RGB-afbeeldingen zonder kleurprofiel worden verondersteld in de kleurruimte *sRGB* te staan.
* CMYK-afbeeldingen zonder kleurprofiel worden geacht zich in de kleurruimte *WebCoated* te bevinden.
* Dynamische uitvoeringen die RGB-uitvoer retourneren, retourneren deze in de kleurruimte *sRGB*.
* Dynamische uitvoeringen die CMYK-uitvoer retourneren, retourneren deze in de kleurruimte *WebCoated*.

#### MIME-typen bewerken voor ondersteunde indelingen {#editing-mime-types-for-supported-formats}

U kunt bepalen welke elementtypen door Dynamic Media worden verwerkt en geavanceerde parameters voor elementverwerking aanpassen. U kunt bijvoorbeeld parameters voor elementverwerking opgeven om het volgende te doen:

* Een Adobe PDF converteren naar een eCatalog-element.
* Converteer een Adobe Photoshop-document (.PSD) naar een bannersjabloonelement voor personalisatie.
* Rasteren een Adobe Illustrator-bestand (.AI) of een Adobe Photoshop Encapsulated PostScript® (.EPS).
* [U kunt videoprofielen ](/help/assets/dynamic-media/video-profiles.md) en  [beeldbewerkingsprofielen ](/help/assets/dynamic-media/image-profiles.md) gebruiken om respectievelijk de verwerking van video&#39;s en afbeeldingen te definiëren.

Zie [Elementen uploaden](/help/assets/add-assets.md).

**De MIME-typen bewerken voor ondersteunde indelingen**

1. In Experience Manager als Cloud Service, klik de Experience Manager als embleem van de Cloud Service om tot de globale navigatieconsole toegang te hebben, dan klik **[!UICONTROL General > CRXDE Lite]**.
1. Navigeer in de linkerspoorstaaf naar het volgende:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![MIME-typen](assets/mimetypes.png)

1. Selecteer een MIME-type onder de map mimeTypes.
1. Aan de rechterkant van de pagina CRXDE Lite, in het onderste gedeelte:

   * Dubbelklik op het veld **[!UICONTROL enabled]**. Standaard zijn alle MIME-elementtypen ingeschakeld (ingesteld op **[!UICONTROL true]**), wat betekent dat de elementen worden gesynchroniseerd met Dynamic Media voor verwerking. Als u dit MIME-type van element wilt uitsluiten van verwerking, wijzigt u deze instelling in **[!UICONTROL false]**.

   * Dubbelklik op **[!UICONTROL jobParam]** om het bijbehorende tekstveld te openen. Zie [Ondersteunde MIME-typen](/help/assets/file-format-support.md) voor een lijst met toegestane waarden voor de verwerkingsparameters die u voor een bepaald MIME-type kunt gebruiken.

1. Voer een van de volgende handelingen uit:
   * Herhaal stap 3-4 om meer MIME-typen te bewerken.
   * Klik in de menubalk van de pagina CRXDE Lite op **[!UICONTROL Save All.]**

1. Tik in de linkerbovenhoek van de pagina op **[!UICONTROL CRXDE Lite]** om terug te keren naar de Experience Manager als een Cloud Service.

#### MIME-typen toevoegen voor niet-ondersteunde indelingen {#adding-mime-types-for-unsupported-formats}

U kunt aangepaste MIME-typen toevoegen voor niet-ondersteunde indelingen in Experience Manager Assets. Verplaats het MIME-type vóór `image_` om ervoor te zorgen dat nieuwe knooppunten die u toevoegt in CRXDE Lite, niet worden verwijderd door Experience Manager. Zorg er ook voor dat de ingeschakelde waarde is ingesteld op **[!UICONTROL false]**.

**MIME-typen toevoegen voor niet-ondersteunde indelingen**

1. Tik **[!UICONTROL Tools > Operations > Web Console.]** vanuit Experience Manager als Cloud Service

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Er wordt een nieuw browsertabblad geopend voor de pagina **[!UICONTROL Adobe Experience Manager Web Console Configuration]**.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Schuif op de pagina omlaag naar de naam *Adobe CQ Scene7 Asset MIME type Service*, zoals u in de volgende schermafbeelding ziet. Tik rechts van de naam op **[!UICONTROL Edit the configuration values]** (potloodpictogram).

   ![2019-08-02_16-44-56](assets/2019-08-02_16-44-56.png)

1. Klik op de pagina **Adobe CQ Scene7 Asset MIME type Service** op een plusteken pictogram &lt;+>. De locatie in de tabel waar u op het plusteken klikt om het nieuwe MIME-type toe te voegen, is triviaal.

   ![2019-08-02_16-27-27](assets/2019-08-02_16-27-27.png)

1. Typ `DWG=image/vnd.dwg` in het lege tekstveld dat u zojuist hebt toegevoegd.

   Het voorbeeld `DWG=image/vnd.dwg` is alleen ter illustratie. Het MIME-type dat u hier toevoegt, kan elke andere niet-ondersteunde indeling hebben.

   ![2019-08-02_16-36-36](assets/2019-08-02_16-36-36.png)

1. Tik in de rechterbenedenhoek van de pagina op **[!UICONTROL Save]**.

   Op dit punt kunt u het browsertabblad sluiten waarop de pagina Configuratie Adobe Experience Manager-webconsole is geopend.

1. Keer terug naar het browser lusje dat uw open Experience Manager als console van de Cloud Service heeft.
1. Tik **[!UICONTROL Tools > General > CRXDE Lite]** vanuit Experience Manager als Cloud Service.

   ![2019-08-02_16-55-41](assets/2019-08-02_16-55-41.png)

1. Navigeer in de linkerspoorstaaf naar het volgende:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Sleep het MIME-type `image_vnd.dwg` en zet het direct boven `image_` in de structuur neer, zoals in de volgende schermafbeelding wordt getoond.

   ![crxdelite_cqdoc-14627](assets/crxdelite_cqdoc-14627.png)

1. Terwijl het MIME-type `image_vnd.dwg` nog steeds is geselecteerd, dubbelklikt u op het tabblad **[!UICONTROL Properties]** in de rij **[!UICONTROL enabled]** onder de kolomkop **[!UICONTROL Value]** op de waarde. De vervolgkeuzelijst **[!UICONTROL Value]** wordt geopend.
1. Typ `false` in het veld (of selecteer **[!UICONTROL false]** in de vervolgkeuzelijst).

   ![2019-08-02_16-60-30](assets/2019-08-02_16-60-30.png)

1. Klik in de linkerbovenhoek van de pagina CRXDE Lite op **[!UICONTROL Save All]**.



### (Optioneel) De prestaties van Dynamic Media {#optional-tuning-the-performance-of-dynamic-media-scene-mode} afstemmen

Om Dynamic Media <!--(with `dynamicmedia_scene7` run mode)--> vlot te laten werken, raadt Adobe de volgende tips voor synchronisatieprestaties/schaalbaarheid aan:

* De vooraf gedefinieerde taakparameters bijwerken voor het verwerken van verschillende bestandsindelingen.
* Het bijwerken van de vooraf gedefinieerde Granite-workflow (video-elementen) vormt een wachtrij voor arbeidersthreads.
* Het bijwerken van de vooraf gedefinieerde tijdelijke Granite-workflow (afbeeldingen en niet-video-elementen) vormt een wachtrij voor arbeidersthreads.
* De maximale uploadverbindingen naar de Dynamic Media Classic-server bijwerken.

#### De vooraf gedefinieerde taakparameters bijwerken voor de verwerking van verschillende bestandsindelingen

U kunt taakparameters instellen voor snellere verwerking wanneer u bestanden uploadt. Als u bijvoorbeeld PSD-bestanden uploadt, maar deze niet als sjablonen wilt verwerken, kunt u de uitname van lagen instellen op false (uitgeschakeld). In dat geval ziet de aangepaste taakparameter er als volgt uit: `process=None&createTemplate=false`.

Gebruik de volgende parameters als u sjabloonontwerp wilt inschakelen: `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- THIS PARAGRAPH WAS REPLACED WITH THE TWO PARAGRAPHS DIRECTLY ABOVE BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe raadt u aan de volgende taakparameters voor PDF-, PostScript®- en PSD-bestanden te gebruiken:

| Bestandstype | Aanbevolen taakparameters |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

Zie [MIME-typen bewerken voor ondersteunde indelingen](#editing-mime-types-for-supported-formats) om deze parameters bij te werken.

Zie ook [MIME-typen toevoegen voor niet-ondersteunde indelingen](#adding-mime-types-for-unsupported-formats).

#### De Granite Transient Workflow Queue {#updating-the-granite-transient-workflow-queue} bijwerken

De Granite Transit Workflow-wachtrij wordt gebruikt voor de **[!UICONTROL DAM Update Asset]**-workflow. In Dynamic Media wordt het gebruikt voor het opnemen en verwerken van afbeeldingen.

**De Granite Transient Workflow-wachtrij bijwerken**

1. Navigeer naar [https://&lt;server>/system/console/configMgr](https://localhost:4502/system/console/configMgr) en zoek naar **Wachtrij: Granite Transient Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. Wijzig in het veld **[!UICONTROL Maximum Parallel Jobs]** het getal in de gewenste waarde.

   U kunt **[!UICONTROL Maximum Parallel Jobs]** verhogen om voldoende ondersteuning te bieden voor het zwaar uploaden van bestanden naar Dynamic Media. De exacte waarde is afhankelijk van de hardwarecapaciteit. In bepaalde scenario&#39;s, zoals een eerste migratie of een eenmalige bulkupload, kunt u een grote waarde gebruiken. Houd er echter rekening mee dat het gebruik van een grote waarde (bijvoorbeeld twee keer het aantal cores) negatieve gevolgen kan hebben voor andere gelijktijdige activiteiten. Als dusdanig, test en pas de waarde aan die op uw bepaald gebruiksgeval wordt gebaseerd.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Tik op **[!UICONTROL Save]**.

#### De Granite Workflow-wachtrij bijwerken {#updating-the-granite-workflow-queue}

De Granite Workflow-wachtrij wordt gebruikt voor niet-tijdelijke workflows. In Dynamic Media werd video verwerkt met de **[!UICONTROL Dynamic Media Encode Video]**-workflow.

De Granite Workflow-wachtrij bijwerken:

1. Navigeer naar `https://<server>/system/console/configMgr` en zoek naar **Wachtrij: Gerichte werkstroom Wachtrij**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. Wijzig in het veld **[!UICONTROL Maximum Parallel Jobs]** het getal in de gewenste waarde.

   Standaard is het maximale aantal parallelle taken afhankelijk van het aantal beschikbare CPU-cores. Op een 4-core server worden bijvoorbeeld twee threads voor workers toegewezen. (Een waarde tussen 0.0 en 1.0 is op verhouding-gebaseerd, of om het even welke aantallen groter dan één wijst het aantal arbeidersdraden toe.)

   In de meeste gevallen is de standaardinstelling 0,5 voldoende.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Tik op **[!UICONTROL Save]**.

#### De Scene7-uploadverbinding {#updating-the-scene-upload-connection} bijwerken

Met de instelling Scene7 Upload Connection synchroniseert u Experience Manager-elementen met Dynamic Media Classic-servers.

De Scene7-uploadverbinding bijwerken:

1. Ga naar `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. Wijzig desgewenst het getal in het veld **[!UICONTROL Number of connections]** of in het veld **[!UICONTROL Active job timeout]**.

   Met de instelling **[!UICONTROL Number of connections]** bepaalt u het maximum aantal HTTP-verbindingen dat is toegestaan voor Experience Manager naar Dynamic Media-upload. Doorgaans is de vooraf gedefinieerde waarde van tien verbindingen voldoende.

   Met de instelling **[!UICONTROL Active job timeout]** bepaalt u de wachttijd voordat geüploade Dynamic Media-elementen worden gepubliceerd op de leveringsserver. Deze waarde is standaard 2100 seconden of 35 minuten.

   In de meeste gevallen is de instelling 2100 voldoende.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Tik op **[!UICONTROL Save.]**

<!-- NOTE - OBSOLETE that customisations to replication agents to transform content are no longer used; the following content is obsolete now 

### (Optional) Filtering assets for replication {#optional-filtering-assets-for-replication}

In non-Dynamic Media deployments, you replicate *all* assets (both images and video) from your Experience Manager as a Cloud Service author environment to the Experience Manager as a Cloud Service publish node. This workflow is necessary because the Experience Manager as a Cloud Service publish servers also deliver the assets.

However, in Dynamic Media deployments, because assets are delivered by way of the cloud service, there is no need to replicate those same assets to Experience Manager as a Cloud Service publish nodes. Such a "hybrid publishing" workflow avoids extra storage costs and longer processing times to replicate assets. Other content, such as Site pages, continue to be served from the Experience Manager as a Cloud Service publish nodes.

The filters provide a way for you to *exclude* assets from being replicated to the Experience Manager as a Cloud Service publish node.

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

1. In Experience Manager as a Cloud Service, tap the Experience Manager as a Cloud Service logo to access the global navigation console and tap the **[!UICONTROL Tools > General > CRXDE Lite]**.
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

