---
title: Schermvideo-uitvoeringen in rasters maken als Cloud Service
description: In deze pagina wordt beschreven hoe u als Cloud Service screens Video-uitvoeringen in rasters maakt.
source-git-commit: 0badd4209b35b4c8cdfa765a08b5d9db749f52b5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Schermvideo-uitvoeringen in rasters maken als Cloud Service {#creating-screens-video-renditions}

## Inleiding {#introduction}

In deze handleiding wordt beschreven hoe u video-uitvoeringen kunt maken die in schermspelers worden gebruikt.

>[!IMPORTANT]
>De stappen die in deze sectie worden gemarkeerd, moeten worden geconfigureerd als u video&#39;s wilt gebruiken in schermkanalen.

## Stappen voor het maken van schermvideo-uitvoeringen in schermen als Cloud Service {#steps-creating-screens-video-renditions}

1. Navigeer naar uw kanaal in de Inhoudsprovider voor schermen.

   >[!NOTE]
   >Raadpleeg [Scherminhoudsprovider gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider) voor meer informatie.

1. Klik op de sectie Gereedschappen in de linkernavigatiebalk en klik op **Middelen**. Klik vervolgens op **Profielen verwerken**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klik op **Maken** om een nieuw verwerkingsprofiel te maken.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Voer de **Naam** in, zoals **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigeer naar het tabblad **Video** om een videocodering toe te voegen en klik op **Nieuwe toevoegen**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Voer de **Coderingsnaam** zoals , **screens-fullhd** en **Bitsnelheid** in als **2500**.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Zorg ervoor dat u de coderingsnaam gebruikt die begint met &quot;screens-&quot;. Alleen deze video-uitvoeringen worden beschouwd als een Cloud Service voor het afspelen van de video-ervaring in rasters. Voer de bitsnelheid in die voor uw video&#39;s geschikt is (2500 kbps voor 720 px video en 5000 kbps voor 1080 px).

   >[!NOTE]
   >U kunt meerdere video-uitvoeringen met verschillende breedte/hoogte/bitsnelheid toevoegen om uw video&#39;s te kunnen bewerken. Houd er rekening mee dat alle schermen- uitvoeringen worden gedownload door de apparaten Screens, ook al speelt het apparaat alleen video-uitvoering af.

1. Klik op **Opslaan**.

1. Selecteer het verwerkingsprofiel en klik op **Profiel toepassen op map(pen)**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Selecteer de map(pen) waarin de video&#39;s op schermen worden opgeslagen en klik op **Toepassen**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* U kunt meerdere verwerkingsprofielen maken en deze toepassen op de corresponderende mappen, zodat de video&#39;s in die mappen de specifieke video-uitvoeringen krijgen.
   >* Wanneer u video&#39;s uploadt naar de map waar het verwerkingsprofiel is toegepast, worden video&#39;s verwerkt en geconfigureerde vertoningen gemaakt, die verder worden gebruikt door de schermapparaten om de video&#39;s af te spelen.


