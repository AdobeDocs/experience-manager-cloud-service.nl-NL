---
title: Bestanden in- en uitchecken in [!DNL Assets]
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: f7f60036088a2332644ce87f4a1be9bae3af1c5e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# Bestanden in- en uitchecken [!DNL Experience Manager] DAM {#check-in-and-check-out-files-in-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Experience Manager Assets] Hiermee kunt u elementen uitchecken voor bewerking en ze weer inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij [!DNL Assets]. Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Van de [!DNL Assets] -gebruikersinterface, selecteert u het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.

1. Klik op de werkbalk op **[!UICONTROL Checkout]**. De **[!UICONTROL Checkout]** optie schakelt over naar **[!UICONTROL Checkin]**.
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Het pictogram ![pictogram uitchecken vergrendeling](assets/do-not-localize/checkout_lock.png) wordt weergegeven op de miniatuur van het element dat u hebt uitgecheckt.

   ![uitcheckpictogram in kaartweergave](assets/checkout-icon-card-view.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![chlimage_1-472](assets/checkout-asset-toolbar-options.png)

   Klik op **[!UICONTROL View Properties]**.

1. Klikken **[!UICONTROL Edit]** om het element te openen in de bewerkingsmodus.

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op. U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Het bewerkte element selecteren in het menu [!DNL Assets] en klik op **[!UICONTROL Checkin]** op de werkbalk. Het gewijzigde element is ingecheckt bij [!DNL Assets] en is beschikbaar voor andere gebruikers om te bewerken.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Aanmelden bij [!DNL Assets] als beheerder.
1. Van de [!DNL Assets] een of meer elementen selecteren die door andere gebruikers zijn uitgecheckt.

   ![chlimage_1-476](assets/chlimage_1-476.png)

1. Klik op de werkbalk op **[!UICONTROL Release Lock]**. Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk een *map* die uitgecheckte elementbestanden bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Middelen publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Inchecken en uitchecken begrijpen [!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#how-app-works2)
>* [Videozelfstudie voor meer informatie over inchecken en uitchecken [!DNL Assets]](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html)
