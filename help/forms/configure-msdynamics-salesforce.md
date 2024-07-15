---
title: Hoe te om de Dynamica 365 van Microsoft en Salesforce uit de doos gegevensmodellen van de vormgegevens voor Adaptive Forms te vormen?
description: Leer hoe u Microsoft Dynamics 365 en Salesforce integreert met Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 2a43b2db-2dfb-4c79-88be-ea770b44dac1
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 1%

---

# Microsoft® Dynamics 365 of Salesforce voor AEM Forms configureren {#configure-azure-storage}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Dit artikel |

[[!DNL Experience Manager Forms]  de Integratie van Gegevens ](data-integration.md) verleent [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] wolkendiensten om adaptieve vormen met uit het Model van de Gegevens van de Vorm van de doos (FDM) te integreren. De Adaptive Forms kan vervolgens communiceren met [!DNL Microsoft® Dynamics 365] - en [!DNL Salesforce] -servers om bedrijfsworkflows mogelijk te maken. Bijvoorbeeld:

* Schrijf gegevens naar [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] bij het verzenden van een adaptief formulier.
* Schrijf gegevens in [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM) en omgekeerd.
* Vraag [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] -server om gegevens en vul Adaptief Forms vooraf in.
* Gegevens lezen van [!DNL Microsoft® Dynamics 365] - en [!DNL Salesforce] -server.

[!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] de wolkendiensten en het Model van de Gegevens van de Vorm (FDM) zijn beschikbaar uit de doos op de [!DNL AEM Forms] Server nadat u [ opstelling een ontwikkelingsproject voor Forms die op archetype van de Experience Manager ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) wordt gebaseerd.

>[!NOTE]
>
>Microsoft® Dynamics 365 en [!DNL Salesforce] de wolkendiensten en het Model van de Gegevens van de Vorm (FDM) zijn beschikbaar uit de doos slechts als u opstelling [!DNL Experience Manager Forms] als [!DNL Cloud Service] project dat op [ wordt gebaseerd Archetype 30 ](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) of later AEM.

## [!DNL Salesforce] cloudservice configureren {#configure-salesforce-cloud-service}

Voordat u de [!DNL Salesforce] -cloudservices configureert, moet u de volgende taken uitvoeren:

* [ creeer een verbonden OAuth-Toegelaten  [!DNL Salesforce]  toepassing ](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). Wanneer u de verbonden [!DNL Salesforce] toepassing creeert, specificeer callback URL in het volgende formaat:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Waar server en poort verwijzen naar de hostnaam en het poortnummer van de [!DNL AEM Forms] -server.

* Geef tijdens het maken van de verbonden [!DNL Salesforce] -toepassing `full` en `offline_access` op als waarden voor het OAuth-bereik.

* Noteer de waarden voor de client-id (Consumentencode genoemd) en het clientgeheim (Consumentengeheim genoemd) voor de verbonden toepassing.

Voer de volgende stappen uit om de cloudservice van [!DNL Salesforce] te configureren:

1. Voor [!DNL AEM Forms] auteursinstantie, navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**. De lijst van beschikbare omslagomslagen omvat een omslag met de titel die voor `DappTitle` wordt gespecificeerd terwijl [ het AEM archetype project ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) produceert.
1. Selecteer de mapnaam, selecteer **[!UICONTROL Salesforce Cloud Config]** en selecteer **[!UICONTROL Properties]** .
1. Op het tabblad **[!UICONTROL Authentication Settings]** :
   1. Geef de [!DNL Salesforce] domein-URL op in het veld **[!UICONTROL Host]** . Bijvoorbeeld, [ domein-naam ] .my.salesforce.com.
   1. Geef de client-id (Consumer Key) en het clientgeheim (Consumentengeheim) voor de verbonden toepassing op.
   1. Specificeer **volledige offline_access** (`full` en `offine_access` waarden die door een ruimte worden gescheiden) op het **[!UICONTROL Authorization Scope]** gebied.
   1. Selecteer **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de aanmeldingspagina van [!DNL Microsoft® Dynamics] .
   1. Meld u aan met uw [!DNL Salesforce] -referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de [!DNL Salesforce] -service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de configuratiepagina van de cloudservice van [!DNL Salesforce] , die een succesbericht weergeeft.
1. Selecteer **[!UICONTROL Save & Close]** om de configuratie-instellingen te voltooien.

### Toegang vanuit het vak [!DNL Salesforce] Formuliergegevensmodel (FDM)

Een [!DNL Salesforce] Model van de Gegevens van de Vorm (FDM) is beschikbaar uit de doos op de [!DNL AEM Forms] Server nadat u [ opstelling een ontwikkelingsproject voor Forms die op archetype van de Experience Manager ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) wordt gebaseerd.

Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** om het FDM (Form Data Model) te openen. De lijst van beschikbare omslagen omvat een omslag met de titel die voor `DappTitle` wordt gespecificeerd terwijl [ het AEM archetype project ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) produceert. Selecteer de omslagnaam, selecteer **[!UICONTROL Salesforce Data Model]**, en selecteer uitgeven ![ ](assets/edit.png) pictogram uitgeven om het model van vormgegevens (FDM) te bekijken.

Na het vormen van de [[!DNL Salesforce]  dienst van Config van de Wolk ](#configure-salesforce-cloud-service), kunt u adaptieve vormen met uit de doos [!DNL Salesforce] Model van Gegevens integreren.

## [!DNL Microsoft® Dynamics 365] cloudservice configureren {#configure-dynamics-cloud-service}

Voordat u de cloudservice van [!DNL Microsoft® Dynamics 365] configureert, moet u de volgende taken uitvoeren:

* [ Register een toepassing voor  [!DNL Microsoft® Dynamics 365]  met Azure Actieve Folder ](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). Wanneer u de verbonden [!DNL Microsoft® Dynamics 365] toepassing creeert, specificeer Reageren URLs in het volgende formaat:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Waar server en poort verwijzen naar de hostnaam en het poortnummer van de [!DNL AEM Forms] -server.

* Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de verbonden toepassing.

Voer de volgende stappen uit om de cloudservice van [!DNL Microsoft® Dynamics 365] te configureren:

1. Voor [!DNL AEM Forms] auteursinstantie, navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**. De lijst van beschikbare omslagomslagen omvat een omslag met de titel die voor `DappTitle` wordt gespecificeerd terwijl [ het AEM archetype project ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) produceert.
1. Selecteer de mapnaam, selecteer **[!UICONTROL Microsoft® Dynamics 365 Cloud Config]** en selecteer **[!UICONTROL Properties]** .
1. Op het tabblad **[!UICONTROL Authentication Settings]** :
   1. Voer de waarde voor het veld **[!UICONTROL Service Root]** in. Ga naar de instantie van de Dynamiek en navigeer aan [ Middelen van de Ontwikkelaar ](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources) om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld: `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. Geef de client-id (toepassings-id) en het clientgeheim voor de verbonden toepassing op.
   1. Vervang `{tenant}` door een huurder-id in de velden **[!UICONTROL OAuth URL]** , **[!UICONTROL Refresh Token URL]** en **[!UICONTROL Access Token URL]** .
   1. Geef in het veld **[!UICONTROL Resource]** de URL van de dynamische instantie op om [!UICONTROL Microsoft® Dynamics] te configureren met een FDM (Form Data Model). Gebruik de URL van de hoofdmap van de service om de instantie-URL Dynamics af te leiden. Bijvoorbeeld `https://<tenant-name>.dynamics.com` .

   1. Geef `openid` op in het veld **[!UICONTROL Authorization Scope]** voor autorisatieproces op [!DNL Microsoft® Dynamics 365] .
   1. Meld u aan met uw [!DNL Microsoft® Dynamics 365] -referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de [!DNL Microsoft® Dynamics 365] -service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de configuratiepagina van de cloudservice van [!DNL Microsoft® Dynamics 365] , die een succesbericht weergeeft.
1. Selecteer **[!UICONTROL Save & Close]** om de configuratie-instellingen te voltooien.

### Toegang vanuit het vak [!DNL Microsoft® Dynamics 365] Formuliergegevensmodel (FDM)

Een [!DNL Microsoft® Dynamics 365] Model van de Gegevens van de Vorm (FDM) is beschikbaar uit de doos op de [!DNL AEM Forms] Server nadat u [ opstelling een ontwikkelingsproject voor Forms die op archetype van de Experience Manager ](setup-local-development-environment.md##forms-cloud-service-local-development-environment) wordt gebaseerd.

Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** om het FDM (Form Data Model) te openen. De lijst van beschikbare omslagen omvat een omslag met de titel die voor `DappTitle` wordt gespecificeerd terwijl [ het AEM archetype project ](setup-local-development-environment.md#forms-cloud-service-local-development-environment) produceert. Selecteer de omslagnaam, selecteer **[!UICONTROL Microsoft® Dynamics 365 Data Model]**, en selecteer uitgeven ![ ](assets/edit.png) pictogram uitgeven om het model van vormgegevens (FDM) te bekijken.

Na het vormen van de [[!DNL Microsoft® Dynamics 365]  dienst van Config van de Wolk ](#configure-dynamics-cloud-service), kunt u adaptieve vormen met uit de doos [!DNL Microsoft® Dynamics 365] Model van Gegevens integreren.

>[!MORELIKETHIS]
>
>* [ vorm gegevensbronnen voor AEM Forms ](/help/forms/configure-data-sources.md)
>* [ vorm Azure opslag voor AEM Forms ](/help/forms/configure-azure-storage.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina ](/help/forms/configure-forms-portal.md)
