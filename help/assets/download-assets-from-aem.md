---
title: Elementen downloaden
description: Elementen downloaden van [!DNL Adobe Experience Manager Assets] en schakelt u de downloadfunctionaliteit in of uit.
contentOwner: Vishabh Gupta
feature: Asset Management
role: User
exl-id: f68b03ba-4ca1-4092-b257-16727fb12e13
source-git-commit: ddc79a163e328d560912550900242cc089df3958
workflow-type: tm+mt
source-wordcount: '1191'
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


### E-mailmeldingen inschakelen voor grote downloads {#enable-emails-for-large-downloads}

>[!NOTE]
>
>Deze functie is beschikbaar in het prereleasekanaal. Zie [Prerelease Channel-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#enable-prerelease) voor informatie om de functie in te schakelen voor uw omgeving.

Asynchrone downloads worden in een van de volgende gevallen geactiveerd:

* Indien er meer dan tien activa zijn
* Als de downloadgrootte groter is dan 100 MB
* Als het downloaden meer dan 30 seconden duurt om voor te bereiden

Terwijl de asynchrone download achteraan loopt, kan de gebruiker blijven onderzoeken en verder in Experience Manager werken. Een out-of-box mechanisme is vereist om de gebruiker op de hoogte te brengen wanneer het downloadproces is voltooid. Om dit doel te bereiken, kunnen de beheerders e-maildienst vormen door opstelling een server SMTP. Zie [Mail Service configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html#sending-email).

Nadat de e-mailservice is geconfigureerd, kunnen beheerders en gebruikers e-mailmeldingen inschakelen via de interface Experience Manager.

E-mailmeldingen inschakelen:

1. Aanmelden bij [!DNL Experience Manager Assets].
1. Klik op het gebruikerspictogram in de rechterbovenhoek en klik vervolgens op **[!UICONTROL My Preferences]**. Het venster Gebruikersvoorkeuren wordt geopend.
1. Selecteer **[!UICONTROL Asset Download email notifications]** selectievakje en klik op **[!UICONTROL Accept]**.

   ![inschakelen-e-mailmeldingen voor grote downloads](/help/assets/assets/enable-email-for-large-downloads.png)


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

