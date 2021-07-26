---
title: Schermvideo-uitvoeringen in rasters maken als Cloud Service
description: In deze pagina wordt beschreven hoe u als Cloud Service screens Video-uitvoeringen in rasters maakt.
source-git-commit: ec939ac6a91523a9ba64a555943eba8e6da071eb
workflow-type: tm+mt
source-wordcount: '326'
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


   >[!IMPORTANT]
   >Zorg ervoor dat u de coderingsnaam gebruikt die begint met &quot;screens-&quot;. Alleen deze video-uitvoeringen worden beschouwd als afspelen van de videobeleving in rasters als Cloud Service. Voer de bitsnelheid in die past bij uw video&#39;s (2500 kbps voor 720 px video en 5000 kbps voor 1080 px)

   >[!NOTE]
   >U kunt meerdere video-uitvoeringen toevoegen met verschillende breedte/hoogte/bitsnelheid, afhankelijk van uw wensen. Houd er echter rekening mee dat alle schermen- uitvoeringen worden gedownload door de rasterapparaten, ook al speelt het apparaat alleen video-uitvoering af.

1. Klik op Opslaan

1. Selecteer het verwerkingsprofiel en klik op &quot;Profiel toepassen op map(pen)&quot;

1. Selecteer de map(pen) waar de video&#39;s op schermen worden opgeslagen en klik op Toepassen

1. U kunt meerdere verwerkingsprofielen maken en deze toepassen op de corresponderende mappen, zodat de video&#39;s in die mappen de specifieke video-uitvoeringen ophalen

1. Wanneer u video&#39;s uploadt naar de map waar het verwerkingsprofiel is toegepast, worden video&#39;s verwerkt en geconfigureerde vertoningen gemaakt. Deze worden door de schermapparaten gebruikt om de video&#39;s af te spelen.

