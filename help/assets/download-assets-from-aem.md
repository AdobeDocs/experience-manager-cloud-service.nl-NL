---
title: Elementen downloaden
description: Elementen downloaden van [!DNL Adobe Experience Manager Assets] en schakelt u de downloadfunctionaliteit in of uit.
contentOwner: VG
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: b4d661bcafb874749b5da436bf2fd16ebeba773e
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---

# Elementen downloaden van [!DNL Adobe Experience Manager] {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar middelen rechtstreeks verzenden vanuit [!DNL Adobe Experience Manager Assets]. Gedownloade elementen worden gebundeld in een ZIP-bestand. <!-- The compressed ZIP file has a maximum file size of 1 GB for the export job. A maximum of 500 total assets per export job are allowed. -->

<!--
>[!NOTE]
>
>Recipients of emails must be members of the `dam-users` group to access the ZIP download link in the email message. To be able to download the assets, the members must have permissions to launch workflows that trigger downloading of assets.
-->

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

U kunt Experience Manager-elementen downloaden met de volgende methoden:

<!-- * [Link Share](#link-share-download) -->

* [Gebruikersinterface Experience Manager](#download-assets)
* [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* [Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal.html)
* [Desktop-app](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets)

## Elementen downloaden met [!DNL Experience Manager] interface {#download-assets}

De asynchrone downloaddienst verstrekt een kader voor naadloze download van grote activa. De downloadarchieven die groter zijn dan 100 GB worden gesplitst in meerdere ZIP-archieven met een maximale grootte van 100 GB elk. Deze kunnen afzonderlijk worden gedownload. Kleinere bestanden worden in real-time gedownload vanuit de gebruikersinterface. [!DNL Experience Manager] één elementdownload niet archiveert op de plaats waar het oorspronkelijke bestand is gedownload. Deze functionaliteit maakt snellere downloads mogelijk.

Standaard, [!DNL Experience Manager] activeert een melding nadat de downloadworkflow is voltooid. Het downloadbericht wordt weergegeven in het dialoogvenster  [[!DNL Experience Manager] Inbox](/help/sites-cloud/authoring/getting-started/inbox.md).

![Inbox-melding](assets/inbox-notification-for-large-downloads.png)

<!--
The large files are downloaded asynchronously and [!DNL Experience Manager] notifies of the completion via notifications in the Inbox. See [understand [!DNL Experience Manager] Inbox](/help/sites-cloud/authoring/getting-started/inbox.md).

![Download notification](assets/download-notification.png)

*Figure: Download notification via [!DNL Experience Manager] Inbox.*

Asynchronous downloads are triggered in either of the following case:

* If there are more than 10 assets or more than 100 MB to be downloaded.
* If the download takes more than 30 seconds to prepare.
-->


<!-- Go live is on 27th Jan 2022
### Enable email notifications for large downloads {#enable-emails-for-large-downloads}

>[!NOTE]
>
>This functionality is available in the Experience Manager prerelease channel.

Asynchronous downloads are triggered in any of the following cases:

* If there are more than ten assets 
* If the download size is more than 100 MB
* If the download takes more than 30 seconds to prepare

While the asynchronous download runs at the backend, the user can continue to explore and work further in Experience Manager. An out-of-the-box mechanism is required to notify the user upon completion of the download process. To achieve this objective, the administrators can configure email service by setting up an SMTP server. See [configure Mail Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email).

Once the email service is configured, the administrators and users can enable email notifications from the Experience Manager interface. 

To enable email notifications:

1. Log in to [!DNL Experience Manager Assets].
1. Click the user icon from the upper-right corner and then click **[!UICONTROL My Preferences]**. The User Preferences window opens.
1. Select the **[!UICONTROL Asset Download email notifications]** check box and click **[!UICONTROL Accept]**.

   ![enable-email-notifications-for-large-downloads](/help/assets/assets/enable-email-for-large-downloads.png)

-->

Voer de volgende stappen uit om elementen te downloaden:

1. In [!DNL Experience Manager] gebruikersinterface, klik **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar de elementen die u wilt downloaden. Selecteer de map of selecteer een of meer middelen in de map. Klik op de werkbalk op **[!UICONTROL Download]**.

   ![Beschikbare opties voor het downloaden van elementen van [!DNL Experience Manager Assets]](/help/assets/assets/asset-download1.png)

1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | Downloadoptie | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om elk element dat u downloadt, inclusief elementen, op te nemen in onderliggende mappen die onder de bovenliggende map van het element zijn genest in één map op uw lokale computer. Wanneer deze optie *niet* Selecteer standaard de maphiërarchie die wordt genegeerd en alle elementen worden naar één map op uw lokale computer gedownload. |
   | **[!UICONTROL Email]** | Selecteer deze optie om een e-mailbericht (met een koppeling naar uw download) naar een andere gebruiker te verzenden. De ontvangende gebruiker moet lid van zijn `dam-users` groep. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm zonder vertoningen wilt downloaden.<br>De optie Subassets is beschikbaar als het oorspronkelijke element subassets heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u hebt geselecteerd. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme-uitsnijduitvoeringen van het geselecteerde element vanuit [!DNL Experience Manager]. Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een van de opties [Voorinstelling afbeelding](/help/assets/dynamic-media/image-presets.md) lijst. <br>Bovendien kunt u de grootte en maateenheid, de indeling, de kleurruimte, de resolutie en eventuele optionele afbeeldingsaanpassingen selecteren, zoals het omkeren van de afbeelding. De optie is alleen beschikbaar als u [!DNL Dynamic Media] ingeschakeld. |

1. Klik in het dialoogvenster op **[!UICONTROL Download]**.

   Als e-mailmelding is ingeschakeld voor grote downloads, wordt een e-mail met een download-URL van de gearchiveerde ZIP-map in uw Postvak IN weergegeven. Klik op de downloadkoppeling in de e-mail om de ZIP-map te downloaden.

   ![e-mailmeldingen voor grote downloads](/help/assets/assets/email-for-large-notification.png)

   U kunt de melding ook in uw [!DNL Experience Manager] Postvak IN.

   ![inbox-notifications-voor-grote downloads](/help/assets/assets/inbox-notification-for-large-downloads.png)

## Elementen downloaden die via koppelingen delen worden gedeeld {#link-share-download}

<!--
>[!NOTE]
>
>This functionality is available in the Experience Manager prerelease channel.
-->

Het delen van elementen via een koppeling is een handige manier om deze beschikbaar te maken voor belangstellenden zonder dat zij zich hoeven aan te melden bij [!DNL Assets]. Zie [Functionaliteit voor delen koppelen](/help/assets/share-assets.md#sharelink).

Wanneer gebruikers elementen downloaden van gedeelde koppelingen [!DNL Assets] gebruikt een asynchrone service die snellere en ononderbroken downloads biedt. De te downloaden middelen worden op de achtergrond in een Postvak IN in een ZIP-archief met beheerbare bestandsgrootte in een wachtrij geplaatst. Voor zeer grote downloads wordt het downloaden afgekapt in bestanden van 100 GB.

De [!UICONTROL Download Inbox] geeft de verwerkingsstatus van elk archief weer. Zodra de verwerking is voltooid, kunt u de archieven downloaden van inbox.

![Postvak IN downloaden](assets/link-sharing-download-inbox.png)

## Enable asset download servlet {#enable-asset-download-servlet}

De standaardserver [!DNL Experience Manager] Hiermee kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven om ZIP-bestanden met elementen te maken. De downloadvoorbereiding kan prestatiesimplicaties hebben of kan zelfs de server en het netwerk overbelasten. Om dergelijke potentiële DoS-achtige risico&#39;s te verlichten die door deze eigenschap worden veroorzaakt, `AssetDownloadServlet` De component OSGi is uitgeschakeld voor publicatie-instanties. Als u de downloadfunctie niet nodig hebt op auteur-instanties, schakelt u het servlet-programma uit bij de auteur.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de vereisten voor het dagelijks downloaden. Een hoge waarde kan van invloed zijn op de prestaties.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatieruntime, dat wil zeggen: `config.publish`:

   `/apps/<your-app-name>/config.publish`

1. Maak in de configuratiemap een nieuw bestand van het type `nt:file` benoemd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vullen `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met het volgende. Hiermee stelt u een maximale grootte (in bytes) in voor het downloaden als waarde van `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```java
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

Als u de downloadfunctionaliteit niet nodig hebt, dan onbruikbaar servlet om het even welke DoS-gelijkaardige risico&#39;s te verhinderen. De `Asset Download Servlet` kan worden uitgeschakeld op een [!DNL Experience Manager] auteur en publiceer instanties door de configuratie van de verzender bij te werken om het even welke verzoeken van de activadownload te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Als u aanvragen voor het downloaden van middelen wilt blokkeren via een dispatcherconfiguratie, bewerkt u de `dispatcher.any` en voeg een nieuwe regel toe aan de [filtersectie](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#configuring).

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

## Tips en beperkingen {#tips-limitations}

* Als u een lege map downloadt, [!DNL Experience Manager] geeft een succesbericht weer over het maken van een ZIP-archief, maar het archief wordt niet gemaakt.

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen downloaden](drm.md)
>* [Elementen downloaden met de bureaubladtoepassing Experience Manager op Win- of Mac-computers](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html)
>* [Elementen downloaden met de Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-apps](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)

