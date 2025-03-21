---
title: Hotlink-beveiliging activeren in Dynamic Media
description: Leer hoe u hotlinkbeveiliging activeert in Dynamic Media.
contentOwner: Rick Brough
feature: Asset Management
role: User
exl-id: 0198b3a3-173e-46ca-a845-3f58f8eab769
source-git-commit: c82f84fe99d8a196adebe504fef78ed8f0b747a9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# Hotlink-beveiliging activeren in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuw </i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b> laat Dynamische Media Prime en Ultimate </b></a> toe
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

Hot linking wordt gebruikt wanneer een externe website HTML-code gebruikt om een afbeelding van uw website weer te geven. Ze gebruiken uw bandbreedte telkens wanneer de afbeelding wordt opgevraagd, omdat de browser van de bezoeker deze rechtstreeks vanaf uw server opent. De hotlink *bescherming* is een methode om andere websites te verhinderen direct met beelden, CSS, of JavaScript op uw Web-pagina&#39;s te verbinden. Dit soort schild helpt onnodig bandbreedtegebruik onder uw Dynamic Media-account te verminderen.

[ de Klantenondersteuning van Adobe ](https://experienceleague.adobe.com/?support-solution=Experience+Manager#home) kan een verwijzerfilter op het niveau vormen CDN. Zo zorgt u ervoor dat de inhoud van dynamische media alleen wordt verzonden naar websites in uw lijst met toegestane websites voor het domein.

>[!NOTE]
>
>Deze functie vereist dat u de uit-van-de-doos CDN gebruikt die met de Dynamische Media van Adobe Experience Manager wordt gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie. Om hot link-beveiliging te activeren, moet een beheerder een ondersteuningsticket maken om de configuratiewijziging in uw Dynamic Media-account aan te vragen. Er zijn geen extra kosten voor het activeren van hotlink-beveiliging.
