---
title: Elementen, mappen en verzamelingen delen als een koppeling
description: In dit artikel wordt beschreven hoe u elementen, mappen en verzamelingen als hyperlink deelt binnen Experience Manager Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: ce22a7ba95942881b90a4f3f22d89bcd35b5e559
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---


# Elementen delen en distribueren die worden beheerd in Experience Manager {#share-assets-from-aem}

Met AEM (Adobe Experience Manager) kunt u elementen, mappen en verzamelingen delen met leden van uw organisatie en externe entiteiten, waaronder partners en leveranciers. Gebruik de volgende methoden om elementen van Experience Manager Assets te delen als een [!DNL Cloud Service]:

* Delen als een koppeling.
* Download elementen en deel ze afzonderlijk.
* Delen via AEM bureaubladtoepassing.
* Delen via Adobe Asset Link.
* (Binnenkomende functionaliteit) Delen met behulp van Brand Portal.

## Elementen delen als een koppeling {#sharelink}

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op `/var/dam/share`-locatie kunnen de koppelingen weergeven die met hen worden gedeeld. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij AEM Assets.

>[!NOTE]
>
>* U hebt ACL toestemming op de omslag of de activa nodig uitgeven die u als verbinding wilt delen.
>* Voordat u een koppeling met gebruikers deelt, moet u ervoor zorgen dat Day CQ Mail Service is geconfigureerd. Anders treedt een fout op.


1. Selecteer in de gebruikersinterface Elementen het element dat u wilt delen als een koppeling.
1. Klik/tik op **[!UICONTROL Share Link]** op de werkbalk. In het veld **[!UICONTROL Share Link]** wordt automatisch een elementkoppeling gemaakt. Kopieer deze koppeling en deel deze met de gebruikers. De standaardvervaltijd voor de verbinding is één dag.

   >[!NOTE]
   >
   >Als een gedeeld element naar een andere locatie wordt verplaatst, werkt de koppeling niet meer. Maak de koppeling opnieuw en deel deze opnieuw met de gebruikers.

<!--
## Share assets as a link {#sharelink}

To generate the URL for assets you want to share with users, use the Link Sharing dialog. Users with administrator privileges or with read permissions at `/var/dam/share` location are able to view the links shared with them. Sharing assets through a link is a convenient way of making resources available to external parties without them having to first log in to AEM Assets.

>[!NOTE]
>
>* You need Edit ACL permission on the folder or the asset that you want to share as a link.
>* Before you share a link with users, ensure that Day CQ Mail Service is configured. Otherwise, an error occurs.

1. In the Assets user interface, select the asset to share as a link.
1. From the toolbar, click/tap the **[!UICONTROL Share Link]**.

   An asset link is auto-created in the **[!UICONTROL Share Link]** field. Copy this link and share it with the users. The default expiration time for the link is one day.

   Alternatively, proceed to perform steps 3-7 of this procedure to add email recipients, configure the expiration time for the link, and send it from the dialog.

   >[!NOTE]
   >
   >If a shared asset is moved to a different location, its link stops working. Re-create the link and re-share with the users.

1. From the web console, open the **[!UICONTROL Day CQ Link Externalizer]** configuration and modify the following properties in the **[!UICONTROL Domains]** field with the values mentioned against each:

    * local
    * author
    * publish

   For the local and author properties, provide the URL for the local and author instance respectively. Both local and author properties have the same value if you run a single AEM author instance. For publish, provide the URL for the publish instance.

1. In the email address box of the **[!UICONTROL Link Sharing]** dialog, type the email ID of the user you want to share the link with. You can also share the link with multiple users.

   If the user is a member of your organization, select the user's email ID from the suggested email IDs that appear in the list below the typing area. For an external user, type the complete email ID and then select it from the list.

   To enable emails to be sent out to users, configure the SMTP server details in [Day CQ Mail Service](/help/assets/configure-asset-sharing.md#configmailservice).

   >[!NOTE]
   >
   >If you enter an email ID of a user that is not a member of your organization, the words "External User" are prefixed with the email ID of the user.

1. In the **[!UICONTROL Subject]** box, enter a subject for the asset you want to share.
1. In the **[!UICONTROL Message]** box, enter an optional message.
1. In the **[!UICONTROL Expiration]** field, specify an expiration date and time for the link using the date picker. By default, the expiration date is set for a week from the date you share the link.
1. To let users download the original image along with the renditions, select **[!UICONTROL Allow download of original file]**.

   >[!NOTE]
   >
   >By default, users can only download the renditions of the asset that you share as a link.

1. Click **[!UICONTROL Share]**. A message confirms that the link is shared with the users through an email.
1. To view the shared asset, click/tap the link in the email that is sent to the user. The shared asset is displayed in the **[!UICONTROL Adobe Marketing Cloud]** page.

   To toggle to the list view, click/tap the layout icon in the toolbar.

1. To generate a preview of the asset, click/tap the shared asset. To close the preview and return to the **[!UICONTROL Marketing Cloud]** page, click/tap **[!UICONTROL Back]** in the toolbar. If you have shared a folder, click/tap **[!UICONTROL Parent Folder]** to return to the parent folder.

   >[!NOTE]
   >
   >AEM supports generating the preview of assets of these MIME types: JPG, PNG, GIF, BMP, INDD, PDF, and PPT. You can only download the assets of the other MIME types.

1. To download the shared asset, click/tap **[!UICONTROL Select]** from the toolbar, click/tap the asset, and then click/tap **[!UICONTROL Download]** from the toolbar.
1. To view the assets you shared as links, go to the Assets user interface and click/tap the GlobalNav icon. Choose **[!UICONTROL Navigation]** from the list to display the Navigation pane.
1. From the Navigation pane, choose **[!UICONTROL Shared Links]** to display a list of shared assets.
1. To un-share an asset, select it and tap/click **[!UICONTROL Unshare]** from the toolbar.

A message confirms that you unshared the asset. In addition, the entry for the asset is removed from the list.
-->

## Elementen downloaden en delen {#download-and-share-assets}

Gebruikers kunnen de vereiste elementen downloaden en deze buiten [!DNL Experience Manager] delen. Voor meer informatie, zie [hoe te om activa te zoeken](/help/assets/search-assets.md), [hoe te om activa te downloaden](/help/assets/download-assets-from-aem.md), en [hoe te om inzamelingen te downloaden](manage-collections.md#download-a-collection)

## Elementen delen met creatieve professionals {#share-with-creatives}

Marketers en zakelijke gebruikers kunnen hun goedgekeurde bedrijfsmiddelen eenvoudig delen met hun creatieve professionals.

* **Desktop-app** AEM: De app werkt op Windows en Mac. Zie [Overzicht van de bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html). Zie [Elementen doorbladeren, zoeken en voorvertonen](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#browse-search-preview-assets) voor informatie over hoe geautoriseerde desktopgebruikers gemakkelijk toegang kunnen krijgen tot de gedeelde elementen. De desktopgebruikers kunnen elementen maken en deze delen met hun collega&#39;s die AEM gebruikers zijn, bijvoorbeeld door nieuwe afbeeldingen te uploaden. Zie [Elementen uploaden met de bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#upload-and-add-new-assets-to-aem).

* **Adobe-elementkoppeling**: De creatieve professionals kunnen rechtstreeks vanuit Adobe InDesign, Adobe Illustrator en Adobe Photoshop zoeken en middelen gebruiken.

## Assets delen configureren {#configure-sharing}

De verschillende opties om de activa te delen vereisen specifieke configuratie en hebben specifieke eerste vereisten.

### Delen van koppelingen voor elementen configureren {#asset-link-sharing}

<!-- TBD: Web Console is not there so how to configure Day CQ email service? Or is it not required now? -->

Gebruik het dialoogvenster Koppelen om de URL te genereren voor elementen die u met gebruikers wilt delen. Gebruikers met beheerdersrechten of met leesmachtigingen op `/var/dam/share`-locatie kunnen de koppelingen weergeven die met hen worden gedeeld. Het delen van elementen via een koppeling is een handige manier om bronnen beschikbaar te maken voor externe partijen zonder dat deze zich eerst hoeven aan te melden bij AEM Assets.

>[!NOTE]
>
>Als u verbindingen van uw instantie van de Auteur AEM aan externe entiteiten wilt delen, zorg ervoor dat u slechts volgende URLs voor `GET` verzoeken blootstelt. Blokkeer andere URL&#39;s om ervoor te zorgen dat uw AEM-auteur-instantie veilig is.
>* `[aem_server]:[port]/linkshare.html`
>* `[aem_server]:[port]/linksharepreview.html`
>* `[aem_server]:[port]/linkexpired.html`


<!--
## Configure Day CQ mail service {#configmailservice}

Before you can share assets as links, configure the email service.

1. Click or tap the AEM logo, and then navigate to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the list of services, locate **[!UICONTROL Day CQ Mail Service]**.
1. Click the **[!UICONTROL Edit]** icon beside the service, and configure the following parameters for **Day CQ Mail Service]** with the details mentioned against their names:

    * SMTP server host name: email server host name
    * SMTP server port: email server port
    * SMTP user: email server user name
    * SMTP password: email server password

1. Click/tap **[!UICONTROL Save]**.
-->

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.
### Configure maximum data size {#maxdatasize}

When you download assets from the link shared using the Link Sharing feature, AEM compresses the asset hierarchy from the repository and then returns the asset in a ZIP file. However, in the absence of limits to the amount of data that can be compressed in a ZIP file, huge amounts of data is subjected to compression, which causes out of memory errors in JVM. To secure the system from a potential denial of service attack due to this situation, you can configure the maximum size of the downloaded files. If uncompressed size of the asset exceeds the configured value, asset download requests are rejected. The default value is 100 MB.

1. Click/Tap the AEM logo and then go to **[!UICONTROL Tools]** &gt; **[!UICONTROL Operations]** &gt; **[!UICONTROL Web Console]**.
1. From the web console, locate the **[!UICONTROL Day CQ DAM Adhoc Asset Share Proxy Servlet]** configuration.
1. Open the configuration in edit mode, and modify the value of the **[!UICONTROL Max Content Size (uncompressed)]** parameter.
1. Save the changes.
-->

<!--
Add content or link about how to configure sharing via BP, DA, AAL, etc.
-->

### Desktophandelingen inschakelen voor gebruik met bureaubladtoepassing {#desktop-actions}

Vanuit de gebruikersinterface Middelen in een browser kunt u de middelenlocaties of uitchecken verkennen en het middel openen voor bewerking in uw desktoptoepassing. Deze opties worden Desktopacties genoemd en om het toe te laten, zie [Desktopacties in AEM Webinterface](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#desktopactions-v2) toelaten.

![Desktophandelingen als sneltoets gebruiken bij het werken met de bureaubladtoepassing](assets/enable_desktop_actions.png)

### Configuraties voor het gebruik van Adobe Asset Link {#configure-asset-link}

Adobe Asset Link stroomlijnt de samenwerking tussen ontwerpers en marketers bij het maken van inhoud. Adobe Experience Manager-middelen (AEM) worden verbonden met Creative Cloud-bureaubladapps Adobe InDesign, Adobe Photoshop en Adobe Illustrator. Met het deelvenster Adobe Asset Link hebben creatieve toepassingen toegang tot inhoud die in AEM Assets is opgeslagen en kunnen ze deze inhoud wijzigen zonder dat ze de meest bekende creatieve apps hoeven te verlaten.

Zie [hoe te om AEM aan gebruik met de Verbinding van Activa van Adobe te vormen ](https://helpx.adobe.com/enterprise/using/configure-aem-assets-for-asset-link.html).

## Aanbevolen procedures en problemen oplossen {#bestpractices}

* Elementmappen of -verzamelingen die in hun naam een witruimte bevatten, worden mogelijk niet gedeeld.
* Als gebruikers de gedeelde elementen niet kunnen downloaden, moet u bij de AEM controleren wat de [downloadlimieten](#maxdatasize) zijn.

<!--
* If you cannot send email with links to shared assets or if the other users cannot receive your email, check with your AEM administrator if the [email service](/help/assets/configure-asset-sharing.md#configmailservice) is configured or not. 
* If you cannot share assets using link sharing functionality, ensure that you have the appropriate permissions. See [share assets](#sharelink).
-->

<!-- TBD: Add content or link about how to share using Brand Portal when it is available on [!DNL Cloud Service].
-->
