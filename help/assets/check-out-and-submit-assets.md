---
title: Bestanden in- en uitchecken in  [!DNL Assets]
description: Leer hoe u middelen kunt uitchecken voor bewerking en ze weer kunt inchecken nadat de wijzigingen zijn voltooid.
contentOwner: AG
feature: Asset Management
role: User
exl-id: adb94a31-d949-4f4a-89bc-44f1b4f67e14
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 1%

---

# Bestanden in [!DNL Experience Manager] DAM inchecken en uitchecken {#check-in-and-check-out-files-in-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

Met [!DNL Adobe Experience Manager Assets] kunt u elementen uitchecken en deze opnieuw inchecken nadat u alle wijzigingen hebt aangebracht. Nadat u een element hebt uitgecheckt, kunt u het element alleen bewerken, annoteren, publiceren, verplaatsen of verwijderen. Als u een element uitcheckt, vergrendelt u het element. Andere gebruikers kunnen geen van deze bewerkingen op het element uitvoeren totdat u het element weer incheckt bij [!DNL Assets] . Ze kunnen echter wel de metagegevens van het vergrendelde element wijzigen.

Om activa te kunnen uitchecken/inchecken, hebt u schrijftoegang op hen nodig.

Met deze functie voorkomt u dat andere gebruikers de wijzigingen overschrijven die door een auteur zijn aangebracht en waarbij meerdere gebruikers samenwerken aan het bewerken van workflows in verschillende teams.

## Elementen uitchecken {#checking-out-assets}

1. Selecteer in de gebruikersinterface van [!DNL Assets] het element dat u wilt uitchecken. U kunt ook meerdere elementen selecteren om uit te checken.

1. Klik in de werkbalk op **[!UICONTROL Checkout]** . Met de optie **[!UICONTROL Checkout]** schakelt u over naar **[!UICONTROL Checkin]** .
Meld u aan als een andere gebruiker om te controleren of andere gebruikers het uitgecheckte element kunnen bewerken. Het pictogram van het pictogramslot ![&#x200B; checkout &#x200B;](assets/do-not-localize/checkout_lock.png) toont op de duimnagel van de activa die u controleerde.

   ![&#x200B; checkout pictogram in kaartmening &#x200B;](assets/checkout-icon-card-view.png)

   Selecteer het element. Op de werkbalk worden geen opties weergegeven waarmee u elementen kunt bewerken, notities kunt aanbrengen, kunt publiceren of verwijderen.

   ![&#x200B; chlimage_1-472 &#x200B;](assets/checkout-asset-toolbar-options.png)

   Klik op **[!UICONTROL View Properties]** als u de metagegevens voor het vergrendelde element wilt bewerken.

1. Klik op **[!UICONTROL Edit]** om het element te openen in de bewerkingsmodus.

1. Bewerk het element en sla de wijzigingen op. Snijd bijvoorbeeld de afbeelding bij en sla deze op. U kunt er ook voor kiezen om het element te annoteren of te publiceren.

1. Selecteer het bewerkte element in de interface van [!DNL Assets] en klik op **[!UICONTROL Checkin]** op de werkbalk. Het gewijzigde element is ingecheckt in [!DNL Assets] en is beschikbaar voor andere gebruikers voor bewerking.

## Geforceerd inchecken {#forced-check-in}

Beheerders kunnen elementen inchecken die door andere gebruikers zijn uitgecheckt.

1. Meld u aan bij [!DNL Assets] als beheerder.
1. Selecteer in de gebruikersinterface van [!DNL Assets] een of meer elementen die door andere gebruikers zijn uitgecheckt.

   ![&#x200B; chlimage_1-476 &#x200B;](assets/chlimage_1-476.png)

1. Klik in de werkbalk op **[!UICONTROL Release Lock]** . Het element is ingecheckt en kan worden bewerkt aan andere gebruikers.

## Aanbevolen werkwijzen en beperkingen {#tips-limitations}

* Het is mogelijk om a *omslag* te schrappen die uitgecheckte activadossiers bevat. Voordat u een map verwijdert, moet u controleren of er geen digitale elementen zijn uitgecheckt door gebruikers.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [&#x200B; Begrijp controle binnen en controle in  [!DNL Experience Manager]  Desktop app &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=nl-NL#how-app-works2)
>* [&#x200B; Videozelfstudie om controle binnen te begrijpen en uit te checken  [!DNL Assets] &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/collaboration/check-in-and-check-out.html?lang=nl-NL)
