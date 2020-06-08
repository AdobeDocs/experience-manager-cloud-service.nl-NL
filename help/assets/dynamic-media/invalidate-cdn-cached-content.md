---
title: Uw CDN-gecachete content ongeldig maken
description: Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
translation-type: tm+mt
source-git-commit: 6224d193adfb87bd9b080f48937e0af1f03386d6
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 28%

---


# Uw CDN-gecachete content ongeldig maken {#invalidating-your-cdn-cached-content}

Dynamische media-elementen worden door de CDN in cache geplaatst voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u deze wijzigingen mogelijk direct van kracht laten worden. Door de CDN-inhoud (Content Delivery Network) in de cache te ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

Zie ook [Cacheoverzicht in Dynamische Klassieke Media (Scene7)](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html).

**Om uw CDN caching inhoud ongeldig te maken:**

1. Logon aan uw Dynamische Klassieke (Scene7) rekening van Media:

   [https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html](https://www.adobe.com/marketing-cloud/experience-manager/scene7-login.html)

   Adobe heeft uw gegevens en aanmeldingsgegevens opgegeven op het moment van de provisioning. Neem contact op met Technische ondersteuning als u deze informatie niet hebt.

1. Klik op **[!UICONTROL Setup > Application Setup > General Settings]**.
1. Ga naar het **[!UICONTROL CDN Invalidation Template]** tekstvak op de pagina Algemene instellingen toepassing onder de kop Servers.

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel bijvoorbeeld dat u een URL voor een afbeelding (inclusief voorinstellingen of wijzigingstoetsen) opgeeft die verwijst `<ID>`in plaats van een specifieke afbeelding-id, zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen bevat `<ID>`, vult Dynamic Media in `https://<server>/is/image` waar `<server>` de naam van de publicatieserver is die is gedefinieerd in Algemene instellingen en &lt;ID> de middelen zijn die zijn geselecteerd om ongeldig te worden gemaakt.

1. Klik in de rechterbenedenhoek van de pagina op **[!UICONTROL Close]**.
1. In Dynamische Media Klassieke (Scene7) UI, selecteer één of meerdere activa, dan klik **[!UICONTROL File > Invalidate CDN]**. Er wordt een lijst weergegeven met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en de elementen die u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeelding met afbeeldingselementen hebt geselecteerd met de naam `Backpack_B`. Wanneer u klikt, resulteert dit in **[!UICONTROL File > Invalidate CDN]** de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Klik in de keuzelijst URL **[!UICONTROL Continue]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. u hoeft CDN niet vooraf in te stellen om sjabloon ongeldig te maken.

   Nadat u klikt **[!UICONTROL Continue]**, wordt een indicator getoond die u een schatting van geeft hoe lang het zal duren om het geheime voorgeheugen te ontruimen.

   Als u meerdere assets hebt geselecteerd en vervolgens op **[!UICONTROL File > Invalidate CDN]** hebt geklikt, wordt naar elke asset verwezen in de opgeslagen **[!UICONTROL Template URL]**. Daarom kunt u een **[!UICONTROL CDN Invalidate Template]** definiëren waarin naar elke voorinstelling voor URL-afbeeldingen wordt verwezen waarnaar op uw website wordt verwezen (zoals productdetails, zoekresultaten, enz.). Wanneer u vervolgens een of meer afbeeldingen selecteert om ongeldig te worden gemaakt door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u assets selecteert en vervolgens op **[!UICONTROL File > Invalidate CDN]** klikt, gebruikt Dynamische media een ongeldige CDN-sjabloon om automatisch URL&#39;s te maken om ongeldig te maken vanaf het CDN (Content Delivery Network). Als het tekstvak **[!UICONTROL CDN Invalidate Template]** leeg is, wordt er een lege URL-lijst weergegeven. Caching bij CDN is niet gebaseerd op assets; het is gebaseerd op URL. Daarom moet u de volledige URL&#39;s die op uw website staan, kennen. Nadat u deze URL&#39;s hebt bepaald, kunt u ze eerder in de stappen toevoegen aan het tekstvak **[!UICONTROL Invalidate CDN Template]**. Vervolgens kunt u deze assets selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >U kunt ook volledige URL&#39;s aan de **[!UICONTROL Invalidate CDN]** lijst toevoegen. Als u deze aanpak volgt, is het niet nodig elementen te selecteren in Dynamic Media Classic voordat u naar de **[!UICONTROL File > Invalidate CDN]** optie gaat.

