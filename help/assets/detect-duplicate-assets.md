---
title: Digitale middelen beheren
description: Leer hoe u dubbele elementen kunt detecteren
contentOwner: KK
mini-toc-levels: 3
feature: Asset Management,Publishing,Collaboration,Asset Processing
role: User,Architect,Admin
exl-id: 40f63933-4f4e-4318-8d42-4b5c9b01f7cd
source-git-commit: 237b4a8e01af74dbaac0ba1715b5fa95c931be7c
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 2%

---

# Gedupliceerde elementen detecteren {#detect-duplicate-assets}

Als een DAM-gebruiker een of meer middelen uploadt die al in de gegevensopslagruimte aanwezig zijn, [!DNL Experience Manager] detecteert de duplicatie en brengt de gebruiker op de hoogte. Dubbele detectie is standaard uitgeschakeld, omdat deze invloed kan hebben op de prestaties, afhankelijk van de grootte van de opslagplaats en het aantal geüploade middelen.

De functie inschakelen:

1. Ga naar **[!UICONTROL Tools > Assets > Assets Configurations]**.

1. Klik op **[!UICONTROL Asset Duplication Detector]**.

1. Op de [!UICONTROL Asset Duplication Detector page], klikt u op **[!UICONTROL Enabled]**.

   `dam:sha1` De waarde voor het veld Metagegevens detecteren zorgt ervoor dat dubbele elementen worden gedetecteerd, zelfs als de bestandsnamen verschillend zijn.

1. Klik op **[!UICONTROL Save]**.

   ![Detector van duplicatie van middelen](assets/asset-duplication-detector.png)

>[!NOTE]
>
>Als u Duplicatiedetector hebt geconfigureerd met `/apps/example/config.author/com.adobe.cq.assetcompute.impl.assetprocessor.AssetDuplicationDetector.cfg.json` configuratiedossier (configuratie OSGi), kunt u het blijven gebruiken, nochtans, adviseert de Adobe het gebruiken van de nieuwe methode.


Zodra toegelaten, verzendt de Experience Manager berichten van dubbele activa naar Experience Manager Inbox. Het is een geaggregeerd resultaat voor meerdere duplicaten. Op basis van de resultaten kunnen gebruikers ervoor kiezen de elementen te verwijderen.

![Melding in postvak voor dubbele elementen](assets/duplicate-detect-inbox-notification.png)

>[!NOTE]
>
>Wanneer u elementen uploadt naar de opslagplaats, detecteert Experience Manager duplicatie en wordt u op de hoogte gebracht van de eerste 100 dubbele elementen.
