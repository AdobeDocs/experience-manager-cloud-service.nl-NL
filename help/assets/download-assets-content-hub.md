---
title: Middelen downloaden van Content Hub
description: Leer hoe u middelen kunt downloaden van de Content Hub-portal
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: 28424cb184d0378669498c78e571961227f6539a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Middelen downloaden van de Content Hub {#download-assets}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![ de activa van de Download ](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Content Hub-gids is nu beschikbaar in de PDF-indeling. Download de volledige handleiding en gebruik Adobe Acrobat AI Assistant om je vragen te beantwoorden.
>
>[!BADGE  de PDF van de Gids van Content Hub ]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Met de Content Hub kunt u uw middelen downloaden en delen. In de Content Hub-gebruikersinterface worden alleen goedgekeurde elementen weergegeven. Deze elementen kunnen afbeeldingen, video&#39;s of andere digitale inhoud bevatten. De Content Hub verbetert de toegankelijkheid en het aanpassingsvermogen voor een effectieve verdeling van activa.

Met Content Hub kunt u een of meer elementen en de beschikbare uitvoeringen downloaden.

## Een middel en de bijbehorende uitvoeringen downloaden {#download-asset-renditions}

Voer de volgende stappen uit om een element en de bijbehorende uitvoeringen te downloaden:

1. Klik op het element om de eigenschappen ervan weer te geven.

1. Klik ![ download ](/help/assets/assets/download-icon.svg) om het downloadproces te beginnen. In het deelvenster Download worden alle beschikbare elementuitvoeringen weergegeven (Origineel + andere uitvoeringen).

   >[!NOTE]
   >
   De vertoningen van vertoningen slechts als hun zicht gebruikend het [ Gebruikersinterface van de Configuratie ](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) wordt toegelaten.

1. Selecteer de vertoning(en) en klik op **[!UICONTROL Download]** .

   ![ Download enige activa vertoningen ](/help/assets/assets/download-single-asset-renditions.png)


Als u een middel met licentie downloadt, selecteert u **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** en klikt u op **[!UICONTROL Download]** . U kunt ook op **[!UICONTROL terms & conditions]** klikken om de elementlicentie weer te geven. De voorvertoning van de licentie wordt alleen weergegeven als het element is goedgekeurd in de as a Cloud Service ontwerpomgeving van Assets. Voor meer informatie, zie [ Gelicentieerde activa op Content Hub ](/help/assets/manage-licensed-assets-on-content-hub.md) beheren.

## Meerdere elementen en de bijbehorende uitvoeringen downloaden {#download-multiple-assets-renditions}

Voer de volgende stappen uit om meerdere elementen en de bijbehorende uitvoeringen te downloaden:

1. Selecteer de activa en klik ![ download ](/help/assets/assets/download-icon.svg) **[!UICONTROL Download]**. In het scherm [!UICONTROL Download assets] worden alle geselecteerde elementen weergegeven.
1. Klik op **[!UICONTROL Download]** om een keuze te maken uit de verschillende downloadopties om te beginnen met downloaden:

   * **Downloaden[!UICONTROL Originals]**: selecteer deze optie om de geselecteerde elementen in het oorspronkelijke formulier te downloaden.
   * **Downloaden[!UICONTROL Renditions only]**: selecteer deze optie om alle beschikbare vertoningen van de activa behalve de originele activa te downloaden.
   * **Downloaden[!UICONTROL Originals & All renditions]**: selecteer deze optie om zowel het origineel als de vertoningen van de geselecteerde elementen te downloaden.

     ![ Download veelvoudige vertoningen ](/help/assets/assets/download-multiple-renditions.png)

     >[!NOTE]
     >
     De vertoningen van vertoningen slechts als hun zicht gebruikend het [ Gebruikersinterface van de Configuratie ](/help/assets/configure-content-hub-ui-options.md#renditions-content-hub) wordt toegelaten.

   Als een van de geselecteerde elementen een onder licentie geplaatst element is, klikt u op de licentie van het element in het linkerdeelvenster om de voorvertoning weer te geven. Hierin kunt u **[!UICONTROL I have read and accepted the terms & conditions mentioned above]** selecteren en vervolgens op **[!UICONTROL Download]** klikken. De voorvertoning van de licentie wordt alleen weergegeven als het element is goedgekeurd in de as a Cloud Service ontwerpomgeving van Assets. Voor meer informatie, zie [ Gelicentieerde activa op Content Hub ](/help/assets/manage-licensed-assets-on-content-hub.md) beheren.

   ![ download-veelvoudige-vergunning ](/help/assets/assets/download-multiple-license.png)

<!--1. On the Content Hub homepage, select the asset and click **Download**. The **Download assets** dialog box displays a license or list of licenses associated with the selected assets in the left pane. 
1. Click a license in the left pane to see its PDF in the middle pane and the associated assets with it in the right pane. The license PDF preview is displayed only if the license is approved in your Assets as a Cloud Service environment. [Approve the license PDFs](/help/assets/approve-assets-content-hub.md) of the selected assets to see their previews.
1. Optional: Click ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the dialog box.
1. Select **I have read and accept all the terms and conditions mentioned above.** 
1. Click **Download** to download the selected assets.-->

<!---This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the preview of the associated assets to the license in the right. Reviewed licenses are highlighted in light blue.


The dialog box that displays depends on whether the download list includes expired assets or only non-expired assets. <br/>
**Download expired assets dialog box:** This dialog box displays the expired assets' preview along with their expiry date in the left pane. The expired assets' count out of total selected displays in the right pane. Click **Proceed with all assets** to download expired assets with other assets (if present). The Download assets dialog box displays. See the [Download assets dialog box](#Download-asset-dialog-box) to proceed further.
    
    >[!NOTE]
    >
    >[Enable the download option for expired assets](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub) to download them. Only expired assets that have enabled downloading are available for download.

   <a id="Download-asset-dialog-box"></a> **Download assets dialog box:** This dialog box displays the list of licenses associated with the selected assets in the left pane. Select a license to preview its terms and conditions (in pdf format) in the middle pane and the associated assets' preview and their count in the right pane. Reviewed licenses are highlighted in light blue.

    >[!NOTE]
    >
    > The **Download Asset dialog box** previews licensing terms and conditions only for approved licenses. [Approve the assets' licenses](/help/assets/approve-assets-content-hub.md) before downloading them to preview their licensing terms in the **Download Asset dialog box**.

1. Click  ![remove-icon](/help/assets/assets/remove-icon.svg) to remove a license from the download dialog box. 

1. Accept the terms and conditions and then click **Download** to download assets associated with the available licenses in the left pane.-->
<!--![download-multiple-license](/help/assets/assets/download-multiple-license.png)-->

<!---
### Download non-licensed Assets {#download-non-licensed-assets}

 To download non-licensed assets, select the assets and click ![download](/help/assets/assets/download-icon.svg) from the top rail.-->







