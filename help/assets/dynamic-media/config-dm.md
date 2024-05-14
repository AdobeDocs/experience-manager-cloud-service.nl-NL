---
title: Dynamic Media-Cloud Service configureren
description: Leer hoe u Dynamic Media in Adobe Experience Manager as a Cloud Service configureert.
contentOwner: Rick Brough
feature: Configuration,Dynamic Media
role: Admin,User
exl-id: 8e07bc85-ef26-4df4-8e64-3c69eae91e11
source-git-commit: 26afff3a39a2a80c1f730287b99f3fb33bff0673
workflow-type: tm+mt
source-wordcount: '3575'
ht-degree: 1%

---

# Informatie over het configureren van Dynamic Media Cloud Service {#configuring-dynamic-media}

Als u Adobe Experience Manager voor verschillende omgevingen gebruikt, zoals ontwikkeling, staging en live productie, configureert u Dynamic Media-Cloud Servicen voor elk van deze omgevingen.

Zie ook [Een alias-account voor een Dynamic Media-bedrijf configureren](/help/assets/dynamic-media/dm-alias-account.md)

## Architectuurdiagram van Dynamic Media {#architecture-diagram-of-dynamic-media}

In het volgende architectuurdiagram wordt beschreven hoe Dynamic Media werkt.

Met de nieuwe architectuur is Experience Manager verantwoordelijk voor primaire bronactiva en syncs met Dynamic Media voor activa verwerking en het publiceren:

1. Wanneer het primaire bronelement naar Adobe Experience Manager as a Cloud Service wordt geüpload, wordt het naar Dynamic Media gerepliceerd. Op dat moment verwerkt Dynamic Media alle processen voor het genereren van elementen, zoals videocodering en dynamische varianten van een afbeelding.
1. Nadat de vertoningen worden geproduceerd, kan de as a Cloud Service Experience Manager veilig tot de verre vertoningen van Dynamic Media toegang hebben en voorproef (geen binaire getallen worden teruggestuurd naar de as a Cloud Service instantie van de Experience Manager).
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

## Een Dynamic Media-configuratie maken in Cloud Servicen {#configuring-dynamic-media-cloud-services}

<!-- **Before you creating a Dynamic Media Configuration in Cloud Services**: After you receive your provisioning email with Dynamic Media credentials, you must open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account to change your password. The password provided in the provisioning email is system-generated and intended to be a temporary password only. It is important that you update the password so that Dynamic Media Cloud Service is set up with the correct credentials. -->

1. In as a Cloud Service Experience Manager, selecteer het as a Cloud Service embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben.
1. Selecteer links van de console het pictogram Gereedschappen en ga naar **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Selecteer in het linkerdeelvenster van de Dynamic Media Configuration Browser-pagina de optie **[!UICONTROL global]** (selecteer het mappictogram niet links van **[!UICONTROL global]**). Selecteer vervolgens **[!UICONTROL Create]**.
1. Op de **[!UICONTROL Create Dynamic Media Configuration]** Voer de titel, het e-mailadres van de Dynamic Media-account en het wachtwoord van de bedrijfsbeheerder van de Dynamic Media-account in en selecteer vervolgens uw regio. Deze informatie wordt u per Adobe verstrekt in de levering e-mail. Neem contact op met de klantenondersteuning van de Adobe als u dit e-mailbericht niet hebt ontvangen.
1. Selecteren **[!UICONTROL Connect to Dynamic Media]**.
1. In de **[!UICONTROL Change Password]** in het dialoogvenster **[!UICONTROL New Password]** voert u een nieuw wachtwoord in dat uit 8-25 tekens bestaat. Het wachtwoord moet ten minste een van de volgende elementen bevatten:

   * Hoofdletter
   * Kleine letter
   * Getal
   * Speciaal teken: `# $ & . - _ : { }`

   De **[!UICONTROL Current Password]** wordt opzettelijk voorgevuld en verborgen voor interactie.

   Indien nodig kunt u de spelling controleren van een wachtwoord dat u hebt getypt of dat u opnieuw hebt getypt door het oogpictogram voor het wachtwoord te selecteren om het wachtwoord weer te geven. Selecteer opnieuw het pictogram om het wachtwoord te verbergen.

1. In de **[!UICONTROL Repeat Password]** veld, typ het nieuwe wachtwoord opnieuw en selecteer vervolgens **[!UICONTROL Done]**.

   Het nieuwe wachtwoord wordt opgeslagen wanneer u **[!UICONTROL Save]** in de rechterbovenhoek van het **[!UICONTROL Create Dynamic Media Configuration]** pagina.

   Als u **[!UICONTROL Cancel]** in de **[!UICONTROL Change Password]** moet u nog steeds een nieuw wachtwoord invoeren wanneer u de gemaakte Dynamic Media-configuratie opslaat.

   Zie ook [Het wachtwoord wijzigen in Dynamic Media](#change-dm-password).

1. Wanneer de verbinding tot stand is gebracht, kunt u het volgende instellen:

   | Eigenschap | Beschrijving |
   |---|---|
   | Bedrijf | De naam van de Dynamic Media-account.<br>**Belangrijk**: Slechts één configuratie van Dynamic Media in Cloud Servicen wordt gesteund op een geval van Experience Manager; voeg niet meer dan één configuratie toe. Meerdere Dynamic Media-configuraties op een Experience Manager-instantie zijn _niet_ ondersteund of aanbevolen door Adobe.<!-- CQDOC-19579 and CQDOC-19612 --><br>Zie ook [Een alias-account voor een Dynamic Media-bedrijf configureren](/help/assets/dynamic-media/dm-alias-account.md). |
   | Pad naar hoofdmap van bedrijf | Het pad naar de hoofdmap van uw bedrijf. |
   | Middelen publiceren | U kunt uit de volgende drie opties kiezen:<br>**[!UICONTROL Immediately]**- Wanneer elementen worden geüpload, neemt het systeem de elementen op en wordt de URL/Embed onmiddellijk weergegeven. Er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>**[!UICONTROL On Activation]** - U moet het element eerst expliciet publiceren voordat er een URL-/insluitkoppeling wordt opgegeven.<br>**[!UICONTROL Selective Publish]**- Elementen worden automatisch gepubliceerd voor een beveiligde voorvertoning. Zij kunnen ook uitdrukkelijk aan as a Cloud Service Experience Manager worden gepubliceerd zonder aan DMS7 voor levering in het openbare domein te publiceren. In de toekomst is deze optie bedoeld om elementen te publiceren voor de Experience Manager van as a Cloud Service elementen en om elementen te publiceren naar Dynamic Media, die elkaar wederzijds uitsluiten. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies als Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. Of u kunt elementen alleen publiceren in Experience Managers die as a Cloud Service zijn voor voorvertoning; deze middelen worden niet gepubliceerd in DMS7 voor levering in het publieke domein. |
   | Secure Preview Server | Hier kunt u het URL-pad naar de voorvertoningsserver voor veilige vertoningen opgeven. Dat wil zeggen, nadat uitvoeringen zijn gegenereerd, kunnen as a Cloud Service Experience Managers veilig de externe Dynamic Media-uitvoeringen openen en bekijken (er worden geen binaire bestanden teruggestuurd naar de as a Cloud Service instantie van de Experience Manager).<br>Tenzij u een speciale regeling hebt om de server van uw eigen bedrijf of een speciale server te gebruiken, adviseert de Adobe dat u dit het plaatsen zoals gespecificeerd verlaat. |
   | Alle inhoud synchroniseren | Standaard geselecteerd. Schakel deze optie uit als u elementen selectief wilt opnemen in of uitsluiten van de synchronisatie met Dynamic Media. Als u deze optie uitschakelt, kunt u kiezen uit de volgende twee Dynamic Media-synchronisatiemodi:<br>**[!UICONTROL Dynamic Media sync mode]**<br>**[!UICONTROL Enable by default]**- De configuratie wordt standaard toegepast op alle mappen, tenzij u een map markeert die specifiek is bedoeld voor uitsluiting.<!-- you can then deselect the folders that you do not want the configuration applied to.--><br>**[!UICONTROL Disabled by default]** - De configuratie wordt pas op een map toegepast als u een geselecteerde map expliciet markeert voor synchronisatie met Dynamic Media.<br>Als u een geselecteerde map wilt markeren voor synchronisatie met Dynamic Media, selecteert u een elementmap en selecteert u vervolgens op de werkbalk **[!UICONTROL Properties]**. Op de **[!UICONTROL Details]** tabblad, in de **[!UICONTROL Dynamic Media sync mode]** kiest u een van de volgende drie opties. Als u klaar bent, selecteert u **[!UICONTROL Save]**. _Vergeet niet dat deze drie opties niet beschikbaar zijn als u deze optie hebt geselecteerd **Alle inhoud synchroniseren**eerder._ Zie ook [Werken met Selectief publiceren op mapniveau in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).<br>**[!UICONTROL Inherited]**- Geen expliciete synchronisatiewaarde in de map. In plaats daarvan neemt de map de synchronisatiewaarde over van een van de bovenliggende mappen of de standaardmodus in de cloudconfiguratie. De gedetailleerde status voor overgeërfde toont dit als knopinfo.<br>**[!UICONTROL Enable for subfolders]** - Neem alles op in deze substructuur voor synchronisatie met Dynamic Media. De mapspecifieke instellingen overschrijven de standaardmodus in de cloudconfiguratie.<br>**[!UICONTROL Disabled for subfolders]**- Sluit alles in deze substructuur uit van synchroniseren naar Dynamic Media. |

   >[!NOTE]
   >
   >Er is geen ondersteuning voor versiebeheer in Dynamische media. Uitgestelde activering is alleen van toepassing als **[!UICONTROL Publish Assets]** in de pagina Dynamic Media-configuratie bewerken is ingesteld op **[!UICONTROL Upon Activation]**. En dan, slechts tot de eerste keer wordt het middel geactiveerd.
   >
   >
   >Nadat een middel wordt geactiveerd, worden om het even welke updates onmiddellijk gepubliceerd live aan S7 Levering.

   ![dynamicmediaconfiguration2updated](/help/assets/assets-dm/dynamicmediaconfigurationupdated.png)

1. Selecteer **[!UICONTROL Save]**. Het nieuwe Dynamic Media-wachtwoord en de nieuwe configuratie worden opgeslagen. Als u **[!UICONTROL Cancel]** in plaats daarvan, komt geen wachtwoordupdate voor.
1. In de **[!UICONTROL Configuring Dynamic Media]** dialoogvenster selecteert u **[!UICONTROL OK]** om met de configuratie te beginnen.

   >[!IMPORTANT]
   >
   >Wanneer de nieuwe configuratie van Dynamic Media zijn opstelling beëindigt, ontvangt u een statusbericht binnen as a Cloud Service Inbox van de Experience Manager.
   >
   >Dit Inbox bericht deelt u als de configuratie of succesvol of niet was.
   > Zie [Een nieuwe Dynamic Media-configuratie oplossen](#troubleshoot-dm-config) en [Uw Postvak IN](/help/sites-cloud/authoring/inbox.md) voor meer informatie .

1. Om Dynamic Media-inhoud veilig voor te vertonen voordat deze wordt gepubliceerd, gebruikt de as a Cloud Service Experience Manager een op token gebaseerde validatie en wordt daarom standaard de Dynamic Media-inhoud voorvertoond door de auteur van de Experience Manager. U kunt echter *lijst van gewenste personen* meer IPs om gebruikers toegang te verlenen tot veilig voorproef inhoud. Als u deze handeling wilt instellen in as a Cloud Service Experience Manager, raadpleegt u [Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren - tabblad Beveiliging](/help/assets/dynamic-media/dm-publish-settings.md#security-tab). <!-- To securely preview Dynamic Media content before it gets published, you must "allowlist" the Experience Manager as a Cloud Service author instance to connect to Dynamic Media. To set up this action, do the following: -->

<!--
    * Open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. Your credentials and sign-in details were provided by Adobe at the time of provisioning. If you do not have this information, contact Adobe Customer Support.
    * On the navigation bar near the upper right corner of the page, go to **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL Publish Setup]** > **[!UICONTROL Image Server]**.
    * On the Image Server Publish page, in the **[!UICONTROL Publish Context]** drop-down list, select **[!UICONTROL Test Image Serving]**.
    * For the Client Address Filter, select **[!UICONTROL Add]**.
    * To enable (turn on) the address, select the check box, then enter the IP address of the Experience Manager Author instance (not Dispatcher IP).
    * Select **[!UICONTROL Save]**. -->

U bent nu klaar met de basisconfiguratie. U kunt Dynamic Media gebruiken.

Als u uw configuratie verder wilt aanpassen, zoals toelatend ACL (de Lijst van het Toegangsbeheer) toestemmingen, kunt u naar keuze om het even welke taken voltooien onder [Geavanceerde instellingen configureren in Dynamic Media](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

### Een nieuwe Dynamic Media-configuratie oplossen {#troubleshoot-dm-config}

Wanneer een nieuwe configuratie van Dynamic Media zijn opstelling beëindigt, ontvangt u een statusbericht binnen Experience Manager as a Cloud Service Inbox. Deze melding geeft aan of de configuratie is gelukt of niet, zoals in de volgende afbeeldingen in het Postvak In wordt getoond.

![Experience Manager Postvak IN gelukt](/help/assets/dynamic-media/assets/dmconfig-inbox-success.png)

![Fout in Experience Manager Inbox](/help/assets/dynamic-media/assets/dmconfig-inbox-failure.png)

Zie ook [Uw Postvak IN](/help/sites-cloud/authoring/inbox.md).

**Een nieuwe Dynamic Media-configuratie oplossen:**

1. Vlak de hogere juiste hoek van de as a Cloud Service pagina van de Experience Manager, selecteer het belpictogram, dan selecteer **[!UICONTROL View All]**.
1. Voor de Inbox pagina, selecteer het succesbericht om een overzicht van de status en de logboeken van de configuratie te lezen.

   Als de configuratie ontbrak, selecteer het mislukkingsbericht gelijkend op het volgende screenshot.

   ![Dynamic Media instellen mislukt](/help/assets/dynamic-media/assets/dmconfig-fail-notification.png)

1. Op de **[!UICONTROL DMSETUP]** pagina, de configuratiedetails bekijken die de mislukking beschrijven. Let met name op foutberichten of foutcodes. Neem contact op met de Klantenondersteuning van de Adobe voor deze informatie.

   ![Dynamic Media-instellingspagina](/help/assets/dynamic-media/assets/dmconfig-fail-page.png)

### Het wachtwoord wijzigen in Dynamic Media {#change-dm-password}

Het verlopen van wachtwoorden in Dynamic Media is ingesteld op 100 jaar vanaf de huidige systeemdatum.

Het wachtwoord moet ten minste een van de volgende elementen bevatten:

* Hoofdletter
* Kleine letter
* Getal
* Speciaal teken: `# $ & . - _ : { }`

Indien nodig kunt u de spelling controleren van een wachtwoord dat u hebt getypt of dat u opnieuw hebt getypt door het oogpictogram voor het wachtwoord te selecteren om het wachtwoord weer te geven. Selecteer opnieuw het pictogram om het wachtwoord te verbergen.

Het gewijzigde wachtwoord wordt opgeslagen wanneer u **[!UICONTROL Save]** in de rechterbovenhoek van het **[!UICONTROL Edit Dynamic Media Configuration]** pagina.

1. In as a Cloud Service Experience Manager, selecteer het as a Cloud Service embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben.
1. Selecteer links van de console het pictogram Gereedschappen en ga naar **[!UICONTROL Cloud Services > Dynamic Media Configuration]**.
1. Selecteer in het linkerdeelvenster van de Dynamic Media Configuration Browser-pagina de optie **[!UICONTROL global]**. Selecteer het mappictogram links van **[!UICONTROL global]**. Selecteer vervolgens **[!UICONTROL Edit]**.
1. Op de **[!UICONTROL Edit Dynamic Media Configuration]** pagina, direct onder de **[!UICONTROL Password]** veld, selecteren **[!UICONTROL Change Password]**.
1. In de **[!UICONTROL Change Password]** voert u de volgende handelingen uit:

   * In de **[!UICONTROL New Password]** voert u een nieuw wachtwoord in.

     De **[!UICONTROL Current Password]** wordt opzettelijk voorgevuld en verborgen voor interactie.

   * In de **[!UICONTROL Repeat Password]** veld, typ het nieuwe wachtwoord opnieuw en selecteer vervolgens **[!UICONTROL Done]**.

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Edit Dynamic Media Configuration]** pagina, selecteert u **[!UICONTROL Save]** selecteert u vervolgens **[!UICONTROL OK]**.

## (Optioneel) Geavanceerde instellingen configureren in Dynamic Media{#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Als u de configuratie en configuratie van Dynamic Media verder wilt aanpassen of de prestaties ervan wilt optimaliseren, kunt u een of meer van de volgende handelingen uitvoeren _optioneel_ taken:

* [(Optioneel) ACL-machtigingen inschakelen in Dynamic Media](#optional-enable-acl)
* [(Optioneel) Dynamic Media-instellingen instellen en configureren](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings)
* [(Optioneel) Pas de prestaties van Dynamic Media aan](#optional-tuning-the-performance-of-dynamic-media-scene-mode)

<!--

* [(Optional) Filtering assets for replication](#optional-filtering-assets-for-replication)

-->

### (Optioneel) De toegangsbeheerlijst inschakelen in Dynamic Media {#optional-enable-acl}

Als je Dynamic Media uitvoert op AEM, gaat het momenteel door `/is/image` verzoeken om het Beeld van de Voorproef te beveiligen die zonder ACL (de Lijst van het Toegangsbeheer) toestemmingen op PlatformServerServlet te controleren. U kunt echter _enable_ ACL toestemmingen. De bevoegde autoriteit `/is/image` verzoeken. Als een gebruiker niet gemachtigd is om toegang te krijgen tot het middel, wordt de fout &quot;403 - Verboden&quot; weergegeven.

**Om ACL toestemmingen in Dynamic Media toe te laten:**

1. Navigeer vanuit Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Er wordt een nieuw browsertabblad geopend voor de **[!UICONTROL Adobe Experience Manager Web Console Configuration]** pagina.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Ga naar de naam op de pagina _Adobe CQ Scene7 PlatformServer_.

1. Rechts van de naam selecteert u het potloodpictogram (**[!UICONTROL Edit the configuration values]**).

1. Op de **com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.name** Selecteer het selectievakje voor de volgende twee instellingen:

   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.cache.enable.name` - Als deze instelling is ingeschakeld, worden de resultaten van de toestemming voor het opslaan gedurende twee minuten in cache geplaatst (standaard).
   * `com.adobe.cq.dam.s7imaging.impl.ps.PlatformServerServlet.validate.userAccess.name` - Als deze instelling is ingeschakeld, wordt de toegang van een gebruiker gevalideerd terwijl deze via Dynamic Media Image Server een voorvertoning van de elementen weergeeft.

   ![Instellingen van toegangsbeheerlijst inschakelen in de modus Dynamic Media - Scene7](/help/assets/dynamic-media/assets/acl.png)

1. Selecteer in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Save]**.

### (Optioneel) Dynamic Media-instellingen instellen en configureren {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings}

Met de Dynamic Media Classic-gebruikersinterface kunt u uw Dynamic Media-instellingen wijzigen.

<!-- Some of the tasks above require that you open the [Dynamic Media Classic desktop application](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), then sign in to your account. -->

De taken van de opstelling en van de configuratie omvatten het volgende:

* [Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren](#publishing-setup-for-image-server)
* [Algemene instellingen van Dynamic Media configureren](#configuring-application-general-settings)
* [Kleurbeheer configureren](#configuring-color-management)
* [MIME-typen bewerken voor ondersteunde indelingen](#editing-mime-types-for-supported-formats)
* [MIME-typen toevoegen voor niet-ondersteunde indelingen](#adding-mime-types-for-unsupported-formats)
<!-- OBSOLETE BUT LEAVE FOR POSSIBLE FUTURE* [Creating batch set presets to auto-generate Image Sets and Spin Sets](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets) -->

#### Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren {#publishing-setup-for-image-server}

Op de pagina Dynamic Media Publish Setup (Publicatie-instellingen) worden standaardinstellingen vastgelegd die bepalen hoe elementen worden geleverd vanaf Adobe Dynamic Media-servers naar websites of toepassingen.

Zie [Dynamic Media-publicatie-instellingen voor afbeeldingsserver configureren](/help/assets/dynamic-media/dm-publish-settings.md).

#### Algemene instellingen van Dynamic Media configureren {#configuring-application-general-settings}

De Dynamic Media configureren **[!UICONTROL Publish Server Name]** URL en de **[!UICONTROL Origin Server Name]** URL. U kunt ook **[!UICONTROL Upload to Application]** instellingen en **[!UICONTROL Default Upload Options]** allemaal op basis van uw specifieke gebruiksgeval.

Zie [Algemene instellingen van Dynamic Media configureren](/help/assets/dynamic-media/dm-general-settings.md).

#### Kleurbeheer configureren {#configuring-color-management}

Met Dynamic Media-kleurbeheer kunt u correcte elementen kleuren. Met kleurcorrectie behouden ingesloten elementen hun kleurruimte (RGB, CMYK, Grijs) en ingesloten kleurprofiel. Wanneer u een dynamische uitvoering aanvraagt, wordt de afbeeldingskleur met CMYK-, RGB- of grijsuitvoer gecorrigeerd naar de doelkleurruimte.

Zie [Voorinstellingen afbeelding configureren](/help/assets/dynamic-media/managing-image-presets.md).

De standaardkleureigenschappen configureren voor het inschakelen van kleurcorrectie bij het aanvragen van afbeeldingen:

1. Open de [Dynamic Media Classic-bureaubladtoepassing](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started)Meld u vervolgens aan bij uw account met de aanmeldingsgegevens die tijdens de provisioning zijn opgegeven.
1. Ga naar **[!UICONTROL Setup > Application Setup]**.
1. Vouw het gebied **[!UICONTROL Publish Setup]** uit en selecteer **[!UICONTROL Image Server]**. Stel **[!UICONTROL Publish Context]** in op **[!UICONTROL Image Serving]** wanneer u standaardinstellingen voor publicatie-exemplaren instelt.
1. Blader naar de eigenschap die u moet wijzigen, bijvoorbeeld een eigenschap in het dialoogvenster **[!UICONTROL Color Management Attributes]** gebied.
U kunt de volgende eigenschappen voor kleurcorrectie instellen:

   | Eigenschap | Beschrijving |
   |---|---|
   | CMYK-standaardkleurruimte | Naam van het standaard CMYK-kleurprofiel. |
   | Standaardkleurruimte grijswaarden | Naam van het standaardkleurprofiel Grijs. |
   | RGB, standaardkleurruimte | Naam van het standaardkleurprofiel RGB. |
   | Render-intentie kleurconversie | Geeft de render-intentie aan. Acceptabele waarden zijn: **[!UICONTROL perceptual]**, **[!UICONTROL relative colometric]**, **[!UICONTROL saturation]**, **[!UICONTROL absolute colometric]**. Adobe beveelt aan **[!UICONTROL relative]** als de standaardinstelling. |

1. Selecteren **[!UICONTROL Save]**.

U kunt bijvoorbeeld **[!UICONTROL RGB Default Color Space]** instellen op *sRGB* en **[!UICONTROL CMYK Default Color Space]** op *WebCoated*.

Dit doet het volgende:

* Hiermee schakelt u kleurcorrectie in voor RGB- en CMYK-afbeeldingen.
* RGB-afbeeldingen die geen kleurprofiel hebben, worden verondersteld in de *sRGB* kleurruimte.
* CMYK-afbeeldingen zonder kleurprofiel worden geacht zich in *WebCoated* kleurruimte.
* Dynamische uitvoeringen die RGB-uitvoer retourneren, retourneren deze in het dialoogvenster *sRGB* kleurruimte.
* Dynamische uitvoeringen die CMYK-uitvoer retourneren, retourneren deze in het dialoogvenster *WebCoated* kleurruimte.

#### MIME-typen bewerken voor ondersteunde indelingen {#editing-mime-types-for-supported-formats}

U kunt bepalen welke elementtypen door Dynamic Media worden verwerkt en geavanceerde parameters voor elementverwerking aanpassen. U kunt bijvoorbeeld parameters voor elementverwerking opgeven om het volgende te doen:

* Een Adobe PDF converteren naar een eCatalog-element.
* Converteer een Adobe Photoshop-document (.PSD) naar een bannersjabloonelement voor personalisatie.
* Rasteren een Adobe Illustrator-bestand (.AI) of een Adobe Photoshop Encapsulated-PostScript® (.EPS).
* [Videoprofielen](/help/assets/dynamic-media/video-profiles.md) en [Afbeeldingsprofielen](/help/assets/dynamic-media/image-profiles.md) kan worden gebruikt om respectievelijk de verwerking van video&#39;s en afbeeldingen te definiëren.

Zie [Elementen uploaden](/help/assets/add-assets.md).

**MIME-typen bewerken voor ondersteunde indelingen:**

1. Meld u aan bij de as a Cloud Service Experience Manager als productbeheerder.
1. In as a Cloud Service Experience Manager, selecteer het as a Cloud Service embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben, dan ga **[!UICONTROL General > CRXDE Lite]**.

   Als u geen toegang hebt tot CRXDE Lite, raadpleegt u [CRXDE Lite gebruiken](/help/implementing/developing/tools/crxde.md).

1. Navigeer in de linkerspoorstaaf naar het volgende:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![MIME-typen](assets/mimetypes.png)

1. Selecteer een MIME-type onder de map mimeTypes.
1. Aan de rechterkant van de pagina CRXDE Lite, in het onderste gedeelte:

   * Selecteer de **[!UICONTROL enabled]** veld. Standaard zijn alle MIME-elementtypen ingeschakeld (ingesteld op **[!UICONTROL true]**), wat betekent dat de activa voor verwerking naar Dynamic Media worden gesynchroniseerd. Als u dit MIME-type van element wilt uitsluiten van verwerking, wijzigt u deze instelling in **[!UICONTROL false]**.

   * Dubbelselecteren **[!UICONTROL jobParam]** om het bijbehorende tekstveld te openen. Zie [Ondersteunde MIME-typen](/help/assets/file-format-support.md) voor een lijst met toegestane waarden voor de verwerkingsparameters die u kunt gebruiken voor een bepaald MIME-type.

1. Voer een van de volgende handelingen uit:
   * Herhaal stap 3-4 om meer MIME-typen te bewerken.
   * Selecteer in de menubalk van de pagina CRXDE Lite de optie **[!UICONTROL Save All]**.

1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL CRXDE Lite]** om terug te keren naar as a Cloud Service Experience Manager.

#### MIME-typen toevoegen voor niet-ondersteunde indelingen {#adding-mime-types-for-unsupported-formats}

U kunt aangepaste MIME-typen toevoegen voor niet-ondersteunde indelingen in Experience Manager Assets. Om ervoor te zorgen dat nieuwe knooppunten die u in CRXDE Lite toevoegt, niet door Experience Manager worden verwijderd, verplaatst u het MIME-type eerder `image_`. Controleer ook of de ingeschakelde waarde is ingesteld op **[!UICONTROL false]**.

**MIME-typen toevoegen voor niet-ondersteunde indelingen:**

1. Meld u aan bij de as a Cloud Service Experience Manager als productbeheerder.
1. Van as a Cloud Service Experience Manager, ga naar **[!UICONTROL Tools > Operations > Web Console]**.

   ![2019-08-02_16-13-14](assets/2019-08-02_16-13-14.png)

1. Er wordt een nieuw browsertabblad geopend voor de **[!UICONTROL Adobe Experience Manager Web Console Configuration]** pagina.

   ![2019-08-02_16-17-29](assets/2019-08-02_16-17-29.png)

1. Schuif op de pagina omlaag naar de naam *Adobe CQ Scene7 Asset MIME type Service*, zoals u in de volgende schermafbeelding ziet. Selecteer rechts van de naam de optie **[!UICONTROL Edit the configuration values]** (potloodpictogram).

   ![De configuratiewaarden bewerken](assets/2019-08-02_16-44-56.png)

1. Op de **Adobe CQ Scene7 Asset MIME Type Service** pagina, selecteert u een plusteken &lt;+>. De locatie in de tabel waar u het plusteken selecteert om het nieuwe MIME-type toe te voegen, is triviaal.

   ![Adobe CQ Scene7 Asset Mime Type Service](assets/2019-08-02_16-27-27.png)

1. Type `DWG=image/vnd.dwg` in het lege tekstveld dat u zojuist hebt toegevoegd.

   De `DWG=image/vnd.dwg` MIME-type is alleen bedoeld voor voorbeelddoeleinden. Het MIME-type dat u hier toevoegt, kan elke andere niet-ondersteunde indeling hebben.

   ![DWG-mime-type toevoegen](assets/2019-08-02_16-36-36.png)

1. Selecteer in de rechterbenedenhoek van de pagina de optie **[!UICONTROL Save]**.

   Op dit punt kunt u het browsertabblad sluiten waarop de pagina Configuratie Adobe Experience Manager-webconsole is geopend.

1. Keer terug naar het browser lusje dat uw open Experience Manager as a Cloud Service console heeft.
1. Van as a Cloud Service Experience Manager, ga naar **[!UICONTROL Tools > General > CRXDE Lite]**.

   Als u geen toegang hebt tot CRXDE Lite, raadpleegt u [CRXDE Lite gebruiken](/help/implementing/developing/tools/crxde.md).

   ![Gereedschappen > Algemeen > CRXDE Lite](assets/2019-08-02_16-55-41.png)

1. Navigeer in de linkerspoorstaaf naar het volgende:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Het MIME-type slepen `image_vnd.dwg` en direct boven plaatsen `image_` in de boom zoals die in het volgende schermschot wordt gezien.

   ![Een DWG-bestand bewerken in CRXDE Lite](assets/crxdelite_cqdoc-14627.png)

1. Met het MIME-type `image_vnd.dwg` nog steeds geselecteerd, uit de **[!UICONTROL Properties]** tabblad, in de **[!UICONTROL enabled]** rij, onder de **[!UICONTROL Value]** kolomkop, dubbelselecteer de waarde. De **[!UICONTROL Value]** vervolgkeuzelijst wordt geopend.
1. Type `false` in het veld (of selecteer **[!UICONTROL false]** in de vervolgkeuzelijst).

   ![Mimenttypen bewerken in CRXDE Lite](assets/2019-08-02_16-60-30.png)

1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **[!UICONTROL Save All]**.

### (Optioneel) Pas de prestaties van Dynamic Media aan {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Dynamic Media behouden <!--(with `dynamicmedia_scene7` run mode)--> De Adobe raadt de volgende tips voor synchronisatieprestaties/schaalbaarheid aan om deze vloeiend te maken:

* [De vooraf gedefinieerde taakparameters bijwerken voor de verwerking van verschillende bestandsindelingen](#update-job-para).
* [Werk de vooraf bepaalde de arbeidersthreads van de Rij van de Werkstroom van de Granite (videoactiva) bij](#update-granite-workflow-queue-worker-threads-video)
* [Werk de vooraf gedefinieerde Granite Transient Workflow Queue (images en niet-video-elementen)-threads bij](#update-granite-transient-workflow-queue-worker-threads-images).
* [De maximale uploadverbindingen naar de Dynamic Media Classic (Scene7)-server bijwerken](#update-max-s7-upload-connections).

#### De vooraf gedefinieerde taakparameters bijwerken voor de verwerking van verschillende bestandsindelingen {#update-job-para}

U kunt taakparameters aanpassen zodat bestanden sneller worden verwerkt. Als u bijvoorbeeld PSD-bestanden uploadt, maar deze niet als sjablonen wilt verwerken, kunt u de uitname van lagen instellen op false (uitgeschakeld). In dat geval ziet de aangepaste taakparameter er als volgt uit: `process=None&createTemplate=false`.

Gebruik de volgende parameters als u sjabloonontwerp wilt inschakelen: `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- THIS PARAGRAPH WAS REPLACED WITH THE TWO PARAGRAPHS DIRECTLY ABOVE BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

Adobe raadt u aan de volgende taakparameters voor PDF-, PostScript®- en PSD-bestanden te gebruiken:

| Bestandstype | Aanbevolen taakparameters |
| ---| ---|
| PDF | `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

Zie voor het bijwerken van deze parameters [MIME-typen bewerken voor ondersteunde indelingen](#editing-mime-types-for-supported-formats).

Zie ook [MIME-typen toevoegen voor niet-ondersteunde indelingen](#adding-mime-types-for-unsupported-formats).

#### Werk de vooraf bepaalde de arbeidersthreads van de Rij van de Werkstroom van de Granite (videoactiva) bij {#update-granite-workflow-queue-worker-threads-video}

De Granite Workflow-wachtrij wordt gebruikt voor niet-tijdelijke workflows. In Dynamic Media werd video verwerkt met de **[!UICONTROL Dynamic Media Encode Video]** workflow.

>[!NOTE]
>
>U moet als productbeheerder zijn aangemeld bij de as a Cloud Service Experience Manager om deze taak te voltooien.

Als u geen toegang tot OSGi hebt, zie [OSGi-configuratie](/help/implementing/developing/components/overview.md#osgi-configuration).

**Om de vooraf bepaalde de arbeidersthreads bij te werken van de Rij van het Werkschema van de Granite (videoactiva):**

1. Navigeren naar `https://<server>/system/console/configMgr` en zoek naar **Wachtrij: Granite Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. In de **[!UICONTROL Maximum Parallel Jobs]** , wijzigt u het getal in de gewenste waarde.

   Standaard is het maximale aantal parallelle taken afhankelijk van het aantal beschikbare CPU-cores. Op een 4-core server worden bijvoorbeeld twee threads voor workers toegewezen. (Een waarde tussen 0.0 en 1.0 is op verhouding-gebaseerd, of om het even welke aantallen groter dan één wijst het aantal arbeidersdraden toe.)

   In de meeste gevallen is de standaardinstelling 0,5 voldoende.

   ![Configuratie van een wachtrij voor taakverwerking](assets/chlimage_1-1.jpeg)

1. Selecteren **[!UICONTROL Save]**.

#### Werk de vooraf bepaalde de arbeidersthreads bij van de Rij van de Rij van de Rij van de Granite Transiet {#update-granite-transient-workflow-queue-worker-threads-images}

De Granite Transit Workflow-wachtrij wordt gebruikt voor de **[!UICONTROL DAM Update Asset]** workflow. In Dynamic Media wordt het gebruikt voor het opnemen en verwerken van afbeeldings- en niet-video-elementen.

>[!NOTE]
>
>U moet als productbeheerder zijn aangemeld bij de as a Cloud Service Experience Manager om deze taak te voltooien.

**Om de vooraf bepaalde de werkrijarbeidersthreads bij te werken van de rij van de Grensovergang van de Granite Transient van het Werkschema:**

1. Ga naar de **Configuratie Adobe Experience Manager-webconsole** om `http://<host>:<port>/system/console/configMgr`
1. Zoeken naar **Wachtrij: Granite Transient Workflow Queue**.

   >[!NOTE]
   >
   >Een tekstonderzoek is noodzakelijk in plaats van een directe URL omdat OSGi PID dynamisch wordt geproduceerd.

1. In de **[!UICONTROL Maximum Parallel Jobs]** , wijzigt u het getal in de gewenste waarde.

   U kunt **[!UICONTROL Maximum Parallel Jobs]** om voldoende ondersteuning te bieden voor het uploaden van bestanden naar Dynamic Media. De exacte waarde is afhankelijk van de hardwarecapaciteit. In bepaalde scenario&#39;s, zoals een eerste migratie of een eenmalige bulkupload, kunt u een grote waarde gebruiken. Houd er echter rekening mee dat het gebruik van een grote waarde (bijvoorbeeld twee keer het aantal cores) negatieve gevolgen kan hebben voor andere gelijktijdige activiteiten. Als dusdanig, test en pas de waarde aan die op uw bepaald gebruiksgeval wordt gebaseerd.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Selecteren **[!UICONTROL Save]**.

#### De maximale uploadverbindingen naar de Dynamic Media Classic (Scene7)-server bijwerken {#update-max-s7-upload-connections}

Met de instelling Dynamic Media Classic (Scene7) Upload Connection synchroniseert u Experience Managers met Dynamic Media Classic-servers.

>[!NOTE]
>
>U moet als productbeheerder zijn aangemeld bij de as a Cloud Service Experience Manager om deze taak te voltooien.

**Zo werkt u de maximale uploadverbindingen naar de Dynamic Media Classic (Scene7)-server bij:**

1. Navigeren naar `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. In de **[!UICONTROL Number of connections]** of de **[!UICONTROL Active job timeout]** of beide, wijzig het nummer naar wens.

   De **[!UICONTROL Number of connections]** Met deze instelling bepaalt u het maximum aantal HTTP-verbindingen dat Experience Manager naar Dynamic Media-upload is toegestaan. Doorgaans is de vooraf gedefinieerde waarde van tien verbindingen voldoende.

   De **[!UICONTROL Active job timeout]** Met deze instelling bepaalt u de wachttijd voordat geüploade Dynamic Media-elementen worden gepubliceerd op de leveringsserver. Deze waarde is standaard 2100 seconden of 35 minuten.

   In de meeste gevallen is de instelling 2100 voldoende.

   ![Adobe Scene7 Upload Service](assets/chlimage_1-2.jpeg)

1. Selecteren **[!UICONTROL Save]**.

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

1. In Experience Manager as a Cloud Service, select the Experience Manager as a Cloud Service logo to access the global navigation console and select the **[!UICONTROL Tools > General > CRXDE Lite]**.
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
