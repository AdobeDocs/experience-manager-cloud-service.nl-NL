---
title: Bestanden in- en uitchecken in [!DNL Assets]
description: Learn how to check out assets for editing and check them back in after the changes are complete.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: 034899c2a717fafdc50cc269d6db3feb77d907c5
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 1%

---

# Check-in and check-out files in [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets] lets you check out assets for editing and check them back in after you complete making the changes. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Other users cannot perform any of these operations on the asset until you check the asset back in to [!DNL Assets]. However, they can still change the metadata for the locked asset.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Van de [!DNL Assets] -gebruikersinterface, selecteert u het element dat u wilt uitchecken. You can also select multiple assets to check out.

1. Klik **[!UICONTROL Checkout]** op de werkbalk. The **[!UICONTROL Checkout]** option toggles to **[!UICONTROL Checkin]**.
To verify whether other users can edit the asset you checked out, log in as a different user. Het pictogram ![pictogram uitchecken vergrendeling](assets/do-not-localize/checkout_lock.png) wordt weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![uitcheckpictogram in kaartweergave](assets/checkout-icon-card-view.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Als u de metagegevens voor het vergrendelde element wilt bewerken, klikt u op **[!UICONTROL View Properties]**.

1. Klikken **[!UICONTROL Edit]** om het element te openen in de bewerkingsmodus.

1. Bewerk het element en sla de wijzigingen op. For example, crop the image and save. U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Het bewerkte element selecteren in het menu [!DNL Assets] en klik op **[!UICONTROL Checkin]** op de werkbalk. Het gewijzigde element is ingecheckt bij [!DNL Assets] en is beschikbaar voor andere gebruikers om te bewerken.

## Geforceerd inchecken {#forced-check-in}

Administrators can check in assets that are checked out by other users.

1. Aanmelden bij [!DNL Assets] als beheerder.
1. Van de [!DNL Assets] een of meer elementen selecteren die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik **[!UICONTROL Release Lock]** op de werkbalk. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk een *map* die uitgecheckte elementbestanden bevat. Before deleting a folder, ensure that no digital assets are checked-out by users.

>[!MORELIKETHIS]
>
>* [Inchecken en uitchecken begrijpen [!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [Video tutorial to understand check in and check out in [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)

