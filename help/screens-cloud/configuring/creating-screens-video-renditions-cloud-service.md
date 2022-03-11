---
title: Video-uitvoeringen maken in as a Cloud Service schermen
description: Op deze pagina wordt beschreven hoe u video-uitvoeringen kunt maken in as a Cloud Service schermen.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# Video-uitvoeringen maken in as a Cloud Service schermen {#creating-screens-video-renditions}

## Inleiding {#introduction}

In deze sectie wordt beschreven hoe u video-uitvoeringen kunt maken die in schermspelers worden gebruikt.

>[!IMPORTANT]
>De stappen die in deze sectie worden gemarkeerd, moeten worden geconfigureerd als u video&#39;s wilt gebruiken in schermkanalen.

## Stappen voor het maken van video-uitvoeringen in as a Cloud Service schermen {#steps-creating-screens-video-renditions}

Voer de onderstaande stappen uit om video-uitvoeringen te maken in rasters die zijn as a Cloud Service van de Inhoudsprovider voor schermen:

1. Navigeer naar uw kanaal in de Inhoudsprovider voor schermen.

   >[!NOTE]
   >Zie [Scherminhoudprovider gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=en#screens-content-provider) voor meer informatie .

1. Klik op de sectie Gereedschappen in de linkernavigatiebalk en klik op **Activa** en klik vervolgens op **Profielen verwerken**.

   ![](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klikken op **Maken** om een nieuw verwerkingsprofiel te maken.

   ![](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Voer de **Naam**, zoals **ScreensProcessingProfile**.

   ![](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigeren naar **Video** om een videocodering toe te voegen en klik op **Nieuwe toevoegen**.

   ![](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Voer de **Coderingsnaam** zoals **schermvullend** en de **Bitsnelheid** als **2500**.

   ![](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Zorg ervoor dat u de coderingsnaam gebruikt die begint met &quot;screens-&quot;. Alleen deze video-uitvoeringen worden beschouwd als zijnde een afspeelvideo in as a Cloud Service schermen. Voer de bitsnelheid in die voor uw video&#39;s geschikt is (2500 kbps voor 720 px video en 5000 kbps voor 1080 px).

   >[!NOTE]
   >U kunt meerdere video-uitvoeringen met verschillende breedte/hoogte/bitsnelheid toevoegen om uw video&#39;s te kunnen bewerken. Houd er rekening mee dat alle schermen- uitvoeringen worden gedownload door de apparaten Screens, ook al speelt het apparaat alleen video-uitvoering af.

1. Klikken op **Opslaan**.

1. Selecteer het verwerkingsprofiel en klik op **Profiel toepassen op map(pen)**.

   ![](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Selecteer de map(pen) waar de video&#39;s op het scherm worden opgeslagen en klik op **Toepassen**.

   ![](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >* U kunt meerdere verwerkingsprofielen maken en deze toepassen op de corresponderende mappen, zodat de video&#39;s in die mappen de specifieke video-uitvoeringen krijgen.
   >* Wanneer u video&#39;s uploadt naar de map waar het verwerkingsprofiel is toegepast, worden video&#39;s verwerkt en geconfigureerde vertoningen gemaakt, die verder worden gebruikt door de schermapparaten om de video&#39;s af te spelen.

