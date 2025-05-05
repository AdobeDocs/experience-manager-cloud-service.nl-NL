---
title: Video-uitvoeringen maken in Screens as a Cloud Service
description: Op deze pagina wordt beschreven hoe u video-uitvoeringen kunt maken in Screens as a Cloud Service.
exl-id: a9c46036-cd29-47fa-81d9-c865cf22c98a
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---

# Video-uitvoeringen maken in Screens as a Cloud Service {#creating-screens-video-renditions}

## Inleiding {#introduction}

In deze sectie wordt beschreven hoe u video-uitvoeringen kunt maken die in Screens-spelers worden gebruikt.

>[!IMPORTANT]
>De stappen die in deze sectie worden gemarkeerd, moeten worden geconfigureerd als u video&#39;s wilt gebruiken in Screens-kanalen.

## Stappen voor het maken van video-uitvoeringen in Screens as a Cloud Service {#steps-creating-screens-video-renditions}

Ga als volgt te werk om video-uitvoeringen te maken in Screens as a Cloud Service van Screens Content Provider:

1. Navigeer naar uw kanaal in de Screens Content Provider.

   >[!NOTE]
   >Zie [ Gebruikend de Leverancier van de Inhoud van Screens ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/configure-screens-cloud/using-screens-content-provider.html?lang=nl-NL#screens-content-provider) voor meer details.

1. Klik de sectie van Hulpmiddelen van de linkernavigatiebar en klik **Assets** en klik dan **Profielen van de Verwerking**.

   ![ klik het Verwerken Profielen ](/help/screens-cloud/assets/configure/screens-cp-3.png)

1. Klik **creëren** om een verwerkingsprofiel tot stand te brengen.

   ![ klik creëren ](/help/screens-cloud/assets/configure/screens-video-2.png)

1. Ga de **Naam**, zoals **ScreensProcessingProfile** in.

   ![ de dialoogdoos die van het Profiel van de Verwerking het benadrukte gebied van de Naam tonen.](/help/screens-cloud/assets/configure/screens-video-3.png)

1. Navigeer aan **Video** lusje zodat kunt u een video coderen toevoegen, en dan **klikken voegt Nieuw** toe.

   ![ de dialoogdoos die van het Profiel van de Verwerking Nieuwe benadrukte knoop toont.](/help/screens-cloud/assets/configure/screens-video-4a.png)

1. Ga de **Coderende Naam** zoals in, **schermen-volledig** en **Bitsnelheid** als **2500**.

   ![ de dialoogdoos die van het Profiel van de Verwerking sparen benadrukte knoop toont.](/help/screens-cloud/assets/configure/screens-video-4.png)

   >[!IMPORTANT]
   >Gebruik de coderingsnaam die begint met &quot;screens-&quot;. Alleen deze video-uitvoeringen worden beschouwd als het afspelen van de video-ervaring in Screens as a Cloud Service. Voer de bitsnelheid in die voor uw video&#39;s wordt gebruikt (2500 kbps voor video van 720 pixels en 5000 kbps voor video van 1080 px).

   >[!NOTE]
   >U kunt meerdere video-uitvoeringen met verschillende breedte/hoogte/bitsnelheid toevoegen om uw video&#39;s te kunnen bewerken. Alle schermen, vertoningen worden gedownload door de apparaten van Screens, alhoewel het apparaat slechts videovertoning speelt.

1. Klik **sparen**.

1. Selecteer het profiel van de Verwerking en klik **passen Profiel op Omslagen** toe.

   ![ pas Profiel op Omslag ](/help/screens-cloud/assets/configure/screens-video-5.png) toe

1. Selecteer de omslagen waar de video&#39;s van Screens worden gehouden en de klik **past** toe.

   ![ klik toepassen ](/help/screens-cloud/assets/configure/screens-video-6.png)

   >[!NOTE]
   >
   >* U kunt meerdere verwerkingsprofielen maken en deze toepassen op de corresponderende mappen, zodat de video&#39;s in die mappen de specifieke video-uitvoeringen krijgen.
   >* Wanneer u video&#39;s uploadt naar de map waarin een verwerkingsprofiel is toegepast, worden video&#39;s verwerkt. Er worden geconfigureerde uitvoeringen gemaakt die door de Screens-apparaten worden gebruikt om de video&#39;s af te spelen.
