---
title: Video-uitvoeringen maken in as a Cloud Service schermen
description: Op deze pagina wordt beschreven hoe u video-uitvoeringen kunt maken in as a Cloud Service schermen.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '360'
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
   >Zie [Scherminhoudprovider gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html#screens-content-provider) voor meer informatie .

1. Klik op de sectie Gereedschappen in de linkernavigatiebalk en klik op **Activa** en klik vervolgens op **Profielen verwerken**.

   ![Klik op Profielen verwerken](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klikken **Maken** om een verwerkingsprofiel te maken.

   ![Klik op Maken](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Voer de **Naam**, zoals **ScreensProcessingProfile**.

   ![Dialoogvenster Profiel verwerken waarin het veld Naam is gemarkeerd.](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigeren naar **Video** zodat u een videocodering kunt toevoegen en vervolgens op **Nieuwe toevoegen**.

   ![Dialoogvenster Profiel verwerken met de knop Nieuwe toevoegen gemarkeerd.](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Voer de **Coderingsnaam** zoals **schermvullend** en de **Bitsnelheid** als **2500**.

   ![Het dialoogvenster Profiel verwerken met de knop Opslaan gemarkeerd.](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Gebruik de coderingsnaam die begint met &quot;screens-&quot;. Alleen deze video-uitvoeringen worden beschouwd als het afspelen van de video-ervaring in as a Cloud Service schermen. Voer de bitsnelheid in die voor uw video&#39;s wordt gebruikt (2500 kbps voor video van 720 pixels en 5000 kbps voor video van 1080 px).

   >[!NOTE]
   >U kunt meerdere video-uitvoeringen met verschillende breedte/hoogte/bitsnelheid toevoegen om uw video&#39;s te kunnen bewerken. Alle schermen, vertoningen worden gedownload door de apparaten van de Schermen, alhoewel het apparaat slechts videovertoning speelt.

1. Klikken **Opslaan**.

1. Selecteer het verwerkingsprofiel en klik op **Profiel toepassen op mappen**.

   ![Profiel toepassen op map](/help/screens-cloud/assets/configure/screens-video-5.png)

1. Selecteer de mappen waarin schermvideo&#39;s worden opgeslagen en klik op **Toepassen**.

   ![Klik op Toepassen](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* U kunt meerdere verwerkingsprofielen maken en deze toepassen op de corresponderende mappen, zodat de video&#39;s in die mappen de specifieke video-uitvoeringen krijgen.
   >* Wanneer u video&#39;s uploadt naar de map waarin een verwerkingsprofiel is toegepast, worden video&#39;s verwerkt. De gevormde vertoningen worden gecreeerd, die door de apparaten van het Scherm worden gebruikt om de video&#39;s te spelen.
