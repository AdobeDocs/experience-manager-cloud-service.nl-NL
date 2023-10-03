---
title: Installatie en configuratie van problemen oplossen
description: Installeren en configureren van AEM Forms as a Cloud Service omgeving oplossen.
contentOwner: khsingh
exl-id: 249ec8f2-4176-428a-bfcf-80b381ec7263
source-git-commit: defeee2fee42c6274c71438d6f9fde6e49a05081
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Configuratie {#installation-and-configuration}

U kunt een aantal van de volgende kwesties ontmoeten terwijl het vormen van een milieu van de Cloud Service:

## Forms-optie is niet beschikbaar

De **[!UICONTROL Forms]** deze optie is niet beschikbaar op de **[!UICONTROL Navigation]** pagina.

![Forms-optie is niet beschikbaar](assets/installation-configuration-forms-option-unavailable-troubleshooting.png)

Om het **[!UICONTROL Forms]** optie:

1. Aanmelden bij de [Cloud Manager](https://experience.adobe.com/)
1. Zoek uw programma en klik op de knop ![Forms-optie is niet beschikbaar](assets/Smock_Edit_18_N.svg) pictogram. Hiermee wordt de pagina Programma bewerken voor uw programma geopend.
1. Open de **[!UICONTROL Solutions & Add-ons]** tab.
1. Selecteer de **[!UICONTROL Forms]** en klik op **[!UICONTROL Save]**.

   ![Selecteer de optie Forms](assets/installation-configuration-select-forms-option.png)
1. [Maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html?lang=en#how-to-use) en [run](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html) zowel productiepijpleidingen als niet-productiepijpleidingen.

Nadat de pijpleiding wordt gebouwd en opgesteld, **[!UICONTROL Forms]** de optie **[!UICONTROL Navigation]** pagina.

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

Als u het probleem wilt oplossen, opent u Cloud Manager en selecteert u de optie **[!UICONTROL Update]** optie voor uw milieu, en stel de pijpleiding in werking.
