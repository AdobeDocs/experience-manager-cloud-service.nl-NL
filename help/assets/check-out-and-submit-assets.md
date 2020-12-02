---
title: Bestanden in [!DNL Assets] inchecken en uitchecken
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 8b1cc8af67c6d12d7e222e12ac4ff77e32ec7e0e
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 4%

---


# Bestanden in Elementen inchecken en uitchecken {#check-in-and-check-out-files-in-assets}

Met Adobe Experience Manager (AEM) Assets kunt u elementen uitchecken en deze opnieuw inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij AEM Assets. Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen {#checking-out-assets} uitchecken

1. Selecteer in de interface Elementen het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.

   ![chlimage_1-468](assets/chlimage_1-468.png)

1. Klik/tik op het pictogram **[!UICONTROL Checkout]** op de werkbalk.

   ![chlimage_1-469](assets/chlimage_1-469.png)

   Merk op dat het **[!UICONTROL Checkout]** pictogram aan het **[!UICONTROL Checkin]** pictogram met open slot van een knevel voorziet.

   ![chlimage_1-470](assets/chlimage_1-470.png)

   Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Er verschijnt een vergrendelingspictogram op de miniatuur van het element dat u hebt uitgecheckt.

   ![chlimage_1-471](assets/chlimage_1-471.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/chlimage_1-472.png)

   U kunt echter op het pictogram **[!UICONTROL View Properties]** klikken of erop tikken om de metagegevens voor het vergrendelde element te bewerken.

1. Klik of tik op het pictogram Bewerken om het element in de bewerkingsmodus te openen.

   ![chlimage_1-473](assets/chlimage_1-473.png)

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op.

   ![chlimage_1-474](assets/chlimage_1-474.png)

   U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer de bewerkte asset in de asset-interface en klik of tik op het pictogram **[!UICONTROL Checkin]** op de werkbalk.

   ![chlimage_1-475](assets/chlimage_1-475.png)

   Het gewijzigde element is ingecheckt in AEM Assets en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerde inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u als beheerder aan bij AEM Assets.
1. Selecteer in de interface Elementen een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik/tik op het pictogram **[!UICONTROL Release Lock]** op de werkbalk. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

   ![chlimage_1-477](assets/chlimage_1-477.png)