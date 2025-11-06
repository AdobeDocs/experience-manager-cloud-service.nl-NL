---
title: Hoe te om Salesforce uit de doos modellen van vormgegevens voor Adaptive Forms te vormen?
description: Leer hoe u Salesforce kunt integreren met Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
exl-id: 184db05b-7237-4dce-8059-03c39b93d7d7
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Salesforce voor AEM Forms configureren {#configure-azure-storage}

[[!DNL Experience Manager Forms]  de Integratie van Gegevens &#x200B;](data-integration.md) verstrekt [!DNL Salesforce] de Diensten van de Wolk om Aanpassings Forms met het Model van de Gegevens van de Vorm van OTB (FDM) te integreren. De Adaptive Forms kan vervolgens communiceren met [!DNL Salesforce] -servers om bedrijfsworkflows in te schakelen. Bijvoorbeeld:

* Schrijf gegevens naar [!DNL Salesforce] bij het verzenden van een adaptief formulier.
* Schrijf gegevens in [!DNL Salesforce] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM) en omgekeerd.
* Vraag [!DNL Salesforce] -server om gegevens en vul Adaptief Forms vooraf in.
* Gegevens van de [!DNL Salesforce] -server lezen.

[!DNL Salesforce] de wolkendiensten en het Model van de Gegevens van de Vorm (FDM) zijn beschikbaar uit de doos op de [!DNL AEM Forms] Server nadat u [&#x200B; opstelling een ontwikkelingsproject voor Forms die op Experience Manager archetype &#x200B;](setup-local-development-environment.md#forms-cloud-service-local-development-environment) wordt gebaseerd.

>[!NOTE]
>
>[!DNL Salesforce] de wolkendiensten en het Model van de Gegevens van de Vorm (FDM) zijn beschikbaar uit de doos slechts als u opstelling een [!DNL Experience Manager Forms] als [!DNL Cloud Service] project dat op [&#x200B; wordt gebaseerd Archetype 30 van AEM &#x200B;](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) of later.

## [!DNL Salesforce] cloudservice configureren {#configure-salesforce-cloud-service}

Voordat u de [!DNL Salesforce] -cloudservices configureert, moet u de volgende taken uitvoeren:

* [&#x200B; creeer een verbonden OAuth-Toegelaten  [!DNL Salesforce]  toepassing &#x200B;](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&type=5). Wanneer u de verbonden [!DNL Salesforce] toepassing creeert, specificeer callback URL in het volgende formaat:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Waar server en poort verwijzen naar de hostnaam en het poortnummer van de [!DNL AEM Forms] -server.

* Geef tijdens het maken van de verbonden [!DNL Salesforce] -toepassing `full` en `offline_access` op als waarden voor het OAuth-bereik.

* Noteer de waarden voor de client-id (Consumentencode genoemd) en het clientgeheim (Consumentengeheim genoemd) voor de verbonden toepassing.

Voer de volgende stappen uit om de cloudservice van [!DNL Salesforce] te configureren:

1. Voor [!DNL AEM Forms] auteursinstantie, navigeer aan **[!UICONTROL Tools]** ![&#x200B; hamer &#x200B;](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**.
2. Selecteer de mapnaam, selecteer **[!UICONTROL Salesforce Cloud Config]** en selecteer **[!UICONTROL Properties]** .
3. Op het tabblad **[!UICONTROL Authentication Settings]** :
   1. Geef de [!DNL Salesforce] domein-URL op in het veld **[!UICONTROL Host]** . Bijvoorbeeld, [ domein-naam ] .my.salesforce.com.
   2. Geef de client-id (Consumer Key) en het clientgeheim (Consumentengeheim) voor de verbonden toepassing op.
   3. Specificeer **volledige offline_access** (`full` en `offine_access` waarden die door een ruimte worden gescheiden) op het **[!UICONTROL Authorization Scope]** gebied.
   4. Selecteer **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de aanmeldingspagina van [!DNL Salesforce] .
   5. Meld u aan met uw [!DNL Salesforce] -referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de [!DNL Salesforce] -service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de configuratiepagina van de cloudservice van [!DNL Salesforce] , die een succesbericht weergeeft.
4. Selecteer **[!UICONTROL Save & Close]** om de configuratie-instellingen te voltooien.

### Toegang vanuit het vak [!DNL Salesforce] Formuliergegevensmodel (FDM)

Een [!DNL Salesforce] Model van de Gegevens van de Vorm (FDM) is beschikbaar uit de doos op de [!DNL AEM Forms] Server nadat u [&#x200B; opstelling een ontwikkelingsproject voor Forms die op Experience Manager archetype &#x200B;](setup-local-development-environment.md#forms-cloud-service-local-development-environment) wordt gebaseerd.

U kunt als volgt het formuliergegevensmodel (FDM) openen:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** .
1. Selecteer de omslagnaam, selecteer **[!UICONTROL Salesforce Data Model]**, en selecteer uitgeven ![&#x200B; &#x200B;](assets/edit.png) pictogram uitgeven om het model van vormgegevens (FDM) te bekijken.

Na het vormen van de [[!DNL Salesforce]  dienst van Config van de Wolk &#x200B;](#configure-salesforce-cloud-service), kunt u adaptieve vormen met uit de doos [!DNL Salesforce] Model van Gegevens integreren.

>[!MORELIKETHIS]
>
>* [&#x200B; vorm gegevensbronnen voor AEM Forms &#x200B;](/help/forms/configure-data-sources.md)
>* [&#x200B; vorm Azure opslag voor AEM Forms &#x200B;](/help/forms/configure-azure-storage.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina &#x200B;](/help/forms/configure-forms-portal.md)
