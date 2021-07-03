---
title: Bestanden in [!DNL Assets] inchecken en uitchecken
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
feature: Beheer van bedrijfsmiddelen
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: a2c2a1f4ef4a8f0cf1afbba001d24782a6a2a24e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Bestanden in [!DNL Experience Manager] DAM inchecken en uitchecken {#check-in-and-check-out-files-in-assets}

[!DNL Adobe Experience Manager Assets] Hiermee kunt u elementen uitchecken voor bewerking en ze weer inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij [!DNL Assets]. Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Selecteer in de gebruikersinterface [!DNL Assets] het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.

1. Klik **[!UICONTROL Checkout]** op de werkbalk. Met de optie **[!UICONTROL Checkout]** schakelt u over naar **[!UICONTROL Checkin]**.
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Het pictogram ![vergrendelingspictogram](assets/do-not-localize/checkout_lock.png) wordt weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![uitcheckpictogram in kaartweergave](assets/checkout-icon-card-view.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Als u de metagegevens voor het vergrendelde element wilt bewerken, klikt u op **[!UICONTROL View Properties]**.

1. Klik op **[!UICONTROL Edit]** om het element in de bewerkingsmodus te openen.

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op. U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer het bewerkte element in de interface [!DNL Assets] en klik op **[!UICONTROL Checkin]** op de werkbalk. Het gewijzigde element wordt ingecheckt bij [!DNL Assets] en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u als beheerder aan bij [!DNL Assets].
1. Selecteer in de gebruikersinterface [!DNL Assets] een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik **[!UICONTROL Release Lock]** op de werkbalk. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk een *map* te verwijderen die uitgecheckte elementbestanden bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

>[!MORELIKETHIS]
>
>* [Inchecken en uitchecken van  [!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en#how-app-works2)
>* [Videozelfstudie voor meer informatie over inchecken en uitchecken [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)

