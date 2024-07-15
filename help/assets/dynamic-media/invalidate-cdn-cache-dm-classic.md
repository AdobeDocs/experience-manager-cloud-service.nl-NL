---
title: De CDN-cache (Content Delivery Network) ongeldig maken via Dynamic Media Classic
description: Leer hoe u inhoud in de cache van uw CDN (Content Delivery Network) ongeldig maakt, zodat u snel elementen kunt bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.
contentOwner: Rick Brough
feature: Asset Management,Dynamic Media Classic
role: Admin,User
exl-id: 7e488699-5633-437f-9e2e-58c98aa13145
source-git-commit: b37ff72dbcf85e5558eb3421b5168dc48e063b47
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 13%

---

# De CDN-cache ongeldig maken via Dynamic Media Classic {#invalidating-your-cdn-cached-content}

Dynamic Media-elementen worden door de CDN (Content Delivery Network) in cache geplaatst voor snelle levering. Wanneer u echter updates aan een element aanbrengt, wilt u dat deze wijzigingen onmiddellijk van kracht worden. Als u de CDN-inhoud in de cache ongeldig maakt, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten tot de cache verloopt.

>[!NOTE]
>
>Voor deze functie is het vereist dat u de CDN uit de doos gebruikt die bij Adobe Experience Manager Dynamic Media is gebundeld. Een andere aangepaste CDN wordt niet ondersteund met deze functie.

>[!IMPORTANT]
>
>Deze stappen zijn alleen van toepassing op Dynamic Media in Adobe Experience Manager 6.5, Service Pack 5 of eerder. <!-- If you are using Dynamic Media in AEM as a Cloud Service, [use the new steps found here](/help/assets/invalidate-cdn-cache-dynamic-media.md). -->

<!-- REMOVED MARCH 28, 2022 BECAUSE OF 404; NO REDIRECT WAS PUT IN PLACE BY SUPPORT See also [Cache overview in Dynamic Media Classic](https://helpx.adobe.com/experience-manager/scene7/kb/base/caching-questions/scene7-caching-overview.html). -->

**om uw CDN geheime voorgeheugen als Dynamic Media Classic ongeldig te maken:**

1. Open de [ Desktoptoepassing van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), dan login aan uw rekening.

   Uw aanmeldingsgegevens en aanmeldingsgegevens zijn door de Adobe opgegeven op het moment van levering. Neem contact op met de Klantenondersteuning als u deze informatie niet hebt.

1. Ga naar **[!UICONTROL Setup]** > **[!UICONTROL Application Setup]** > **[!UICONTROL General Settings]** .
1. Zoek op de pagina Algemene instellingen van toepassing onder de kop Servers het tekstvak **[!UICONTROL CDN Invalidation Template]** .

1. Geef de sjabloon op die wordt gebruikt voor het ongeldig maken van de CDN-cache (Content Delivery Network).

   Stel dat u bijvoorbeeld een afbeeldings-URL (inclusief voorinstellingen of wijzigingstoetsen) opgeeft die verwijst naar `<ID>` in plaats van een specifieke afbeelding-id, zoals in het volgende voorbeeld:

   `https://server.com/is/image/Company/<ID>?$product$`

   Als de sjabloon alleen `<ID>` bevat, vult Dynamic Media `https://<server>/is/image` in waarbij `<server>` de Publish Server Name is die is gedefinieerd in General Settings en &lt;ID> de middelen is die zijn geselecteerd om ongeldig te worden gemaakt.

1. Selecteer **[!UICONTROL Close]** rechtsonder op de pagina.
1. Selecteer in de gebruikersinterface van Dynamic Media Classic (Scene7) een of meer elementen en ga vervolgens naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** . Er wordt een lijst weergegeven met een of meer URL&#39;s die zijn gegenereerd op basis van de sjabloon die u hebt gemaakt en de elementen die u hebt geselecteerd. De URL van de server wordt gebruikt onder &quot;Gepubliceerde servernaam&quot; onder Algemene instellingen van toepassing.

   Stel dat u, terwijl de CDN-validatiesjabloon in de vorige stap is ingesteld, één afbeelding met afbeeldingselementen hebt geselecteerd met de naam `Backpack_B` . Wanneer u naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** gaat, resulteert dit in de volgende gegenereerde URL in de gebruikersinterface voor CDN-validatie:

   `https://server.com/is/image/Company/Backpack_B?$product$`

1. Selecteer in de keuzelijst URL de optie **[!UICONTROL Continue]** om de cache voor elke specifieke URL te wissen. U kunt een URL bewerken of u kunt een URL toevoegen door deze in het vak URL-lijst te typen of te plakken. U hoeft CDN niet vooraf in te stellen om de sjabloon ongeldig te maken.

   Nadat u **[!UICONTROL Continue]** hebt geselecteerd, wordt een indicator weergegeven die u een schatting geeft van hoe lang het duurt om de cache te wissen.

   Als u meerdere elementen hebt geselecteerd en vervolgens naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** gaat, wordt naar elk element verwezen in het opgeslagen **[!UICONTROL Template URL]** . Daarom kunt u een **[!UICONTROL CDN Invalidate Template]** definiëren die verwijst naar elke voorinstelling voor URL-afbeeldingen waarnaar op uw website wordt verwezen, zoals productdetails en zoekresultaten. Wanneer u vervolgens een of meer afbeeldingen selecteert om ongeldig te worden gemaakt door het cachegeheugen, vullen de URL&#39;s automatisch de interface in.

   >[!NOTE]
   >
   >Wanneer u elementen selecteert en vervolgens naar **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** gaat, gebruikt Dynamic Media een CDN-sjabloon voor ongeldig maken om automatisch URL&#39;s te maken die ongeldig worden gemaakt vanaf de CDN. Als het tekstvak **[!UICONTROL CDN Invalidate Template]** leeg is, wordt er een lege URL-lijst weergegeven. Caching bij CDN is niet gebaseerd op assets; het is gebaseerd op URL. Daarom moet u de volledige URL&#39;s die op uw website staan, kennen. Nadat u deze URL&#39;s hebt bepaald, kunt u ze eerder in de stappen toevoegen aan het tekstvak **[!UICONTROL Invalidate CDN Template]**. Vervolgens kunt u deze assets selecteren en de URL&#39;s in één stap ongeldig maken.
   >
   >U kunt ook volledige URL&#39;s toevoegen aan de lijst **[!UICONTROL Invalidate CDN]** . Als u deze aanpak volgt, is het niet nodig elementen te selecteren in Dynamic Media Classic voordat u naar de optie **[!UICONTROL File]** > **[!UICONTROL Invalidate CDN]** gaat.
