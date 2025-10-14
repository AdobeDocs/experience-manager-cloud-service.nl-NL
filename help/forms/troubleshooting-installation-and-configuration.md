---
title: Hoe te om installatie en configuratiekwesties voor het as a Cloud Service milieu van AEM Forms problemen op te lossen?
description: Installatie en configuratie van AEM Forms as a Cloud Service-omgeving oplossen.
contentOwner: khsingh
feature: Adaptive Forms
role: User
exl-id: 249ec8f2-4176-428a-bfcf-80b381ec7263
source-git-commit: 0b693cb51a96011235fa87a5899426c6b0c2509a
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Configuratie {#installation-and-configuration}

U kunt een aantal van de volgende kwesties ontmoeten terwijl het vormen van een milieu van de Cloud Service:

## Forms-optie is niet beschikbaar

De optie **[!UICONTROL Forms]** is niet beschikbaar op de pagina van **[!UICONTROL Navigation]** .

![&#x200B; de optie van Forms is niet beschikbaar &#x200B;](assets/installation-configuration-forms-option-unavailable-troubleshooting.png)

De optie **[!UICONTROL Forms]** inschakelen:

1. Login aan [&#x200B; Cloud Manager &#x200B;](https://experience.adobe.com/)
1. Bepaal de plaats van uw programma en klik de ![&#x200B; optie van Forms is niet beschikbaar &#x200B;](assets/Smock_Edit_18_N.svg) pictogram. Hiermee wordt de pagina Programma bewerken voor uw programma geopend.
1. Open de tab **[!UICONTROL Solutions & Add-ons]** .
1. Selecteer de optie **[!UICONTROL Forms]** en klik op **[!UICONTROL Save]** .

   ![&#x200B; selecteer de optie van Forms &#x200B;](assets/installation-configuration-select-forms-option.png)
1. [&#x200B; creeer &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=nl-NL#how-to-use) en [&#x200B; stel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=nl-NL) zowel productie als niet-productie pijpleidingen in werking.

Nadat de pijpleiding wordt gebouwd en opgesteld, de **[!UICONTROL Forms]** optie op de **[!UICONTROL Navigation]** pagina.

<!--  
## Environment creation fails {#environment-creation-fails}

Users are unable to create an [!DNL AEM Forms] as a Cloud Service environment. The environment creation fails after running for some time.

A missing profile can lead to environment creation failure. Check that the profile exists in Admin Console. If the profile does not exist, perform the following steps to create the profile:

1. Log in to [Admin Console](https://adminconsole.adobe.com/). Use Adobe ID of administrator provisioned to use Automated Forms Conversion Service to login. Do not any other ID or Federated ID to login.
1. Click the **[!UICONTROL Automated Forms Conversion Service]** option.
1. Click **[!UICONTROL New Profile]** in the Products tab.
1. Specify Name, Display Name, and Description for the profile. Click **[!UICONTROL Done]**. A profile is created.

If the profile exists and issues still persist, contact Adobe Support. -->

## De pijpleiding bouwt ontbreekt {#build-pipeline-fails}

De gebruikers kunnen niet bouwstijlpijpleiding in werking stellen. De pijpleiding ontbreekt na het runnen voor wat tijd.

Als u het probleem wilt oplossen, opent u Cloud Manager, selecteert u de optie **[!UICONTROL Update]** voor uw omgeving en voert u de pijplijn uit.


## Bundels bevinden zich niet in de actieve status {#bundles-inactive-state}

Voer de volgende stappen uit om het probleem op te lossen:

1. Start AEM en wacht tot het programma volledig is gestart tot alle bundels zijn opgestart.
1. Stop AEM (Ctrl + C).
1. Plaats het Forms `.far` -bestand in de installatiemap.
1. Start de AEM server opnieuw.