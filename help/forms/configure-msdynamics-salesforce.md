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
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/oauth2-client-credentials-flow-for-server-to-server-integration.html) |
| AEM as a Cloud Service | Dit artikel |

[[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md) verstrekt [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] cloudservices om adaptieve formulieren te integreren met FDM (Form Data Model) buiten het vak. De Adaptive Forms kan dan communiceren met [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] servers om bedrijfswerkstromen toe te laten. Bijvoorbeeld:

* Gegevens schrijven naar [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] op Aangepast formulier verzenden.
* Gegevens schrijven in [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM) en omgekeerd.
* Query [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] voor gegevens en vult Adaptive Forms vooraf in.
* Gegevens lezen van [!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] server.

[!DNL Microsoft® Dynamics 365] en [!DNL Salesforce] cloudservices en het formuliergegevensmodel (FDM) zijn beschikbaar in het vak op het tabblad [!DNL AEM Forms] Server na u [een ontwikkelingsproject voor Forms opzetten op basis van het archetype van de Experience Manager](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft® Dynamics 365 en [!DNL Salesforce] de wolkendiensten en het Model van de Gegevens van het Vorm (FDM) zijn beschikbaar uit de doos slechts als u opstelling [!DNL Experience Manager Forms] als [!DNL Cloud Service] project gebaseerd op [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) of hoger.

## Configureren [!DNL Salesforce] cloudservice {#configure-salesforce-cloud-service}

Voordat u de [!DNL Salesforce] cloudservices, zorg ervoor dat u de volgende taken uitvoert:

* [Maak een aangesloten OAuth-ingeschakeld [!DNL Salesforce] toepassing](https://help.salesforce.com/s/articleView?id=sf.connected_app_create_api_integration.htm&amp;type=5). Wanneer u de verbinding maakt [!DNL Salesforce] de callback-URL in de volgende notatie opgeven:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Waar server en poort verwijzen naar de hostnaam en het poortnummer voor de [!DNL AEM Forms] Server.

* Tijdens het maken van de verbinding [!DNL Salesforce] toepassing, specificeer `full` en `offline_access` als de waarden voor het OAuth-bereik.

* Noteer de waarden voor de client-id (Consumentencode genoemd) en het clientgeheim (Consumentengeheim genoemd) voor de verbonden toepassing.

Voer de volgende stappen uit om het [!DNL Salesforce] cloudservice:

1. Aan [!DNL AEM Forms] auteurinstantie, navigeren aan **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**. De lijst met beschikbare mappen bevat een map met de titel die is opgegeven voor `DappTitle`  while [het produceren van het project van AEM archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).
1. Selecteer de mapnaam, selecteer **[!UICONTROL Salesforce Cloud Config]** en selecteert u **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Authentication Settings]** tab:
   1. Geef de [!DNL Salesforce] Domein URL in de **[!UICONTROL Host]** veld. Bijvoorbeeld: [Domeinnaam].my.salesforce.com.
   1. Geef de client-id (Consumer Key) en het clientgeheim (Consumentengeheim) voor de verbonden toepassing op.
   1. Opgeven **full offline_access** (`full` en `offine_access` waarden, gescheiden door een spatie) in het dialoogvenster **[!UICONTROL Authorization Scope]** veld.
   1. Selecteer **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar [!DNL Microsoft® Dynamics] aanmeldingspagina
   1. Meld u aan met uw [!DNL Salesforce] referenties en accepteren om de configuratie van de cloudservice in staat te stellen verbinding te maken met [!DNL Salesforce] service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de [!DNL Salesforce] de configuratiepagina van de wolkendienst, die een succesbericht toont.
1. Selecteren **[!UICONTROL Save & Close]** om de configuratie te voltooien opstelling.

### Toegang buiten de doos [!DNL Salesforce] Formuliergegevensmodel (FDM)

A [!DNL Salesforce] FDM (Form Data Model) is beschikbaar in het vak op het tabblad [!DNL AEM Forms] Server na u [een ontwikkelingsproject voor Forms opzetten op basis van het archetype van de Experience Manager](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

Als u toegang wilt krijgen tot het formuliergegevensmodel (FDM), navigeert u naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**. De lijst met beschikbare mappen bevat een map met de titel die is opgegeven voor `DappTitle`  while [het produceren van het project van AEM archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment). Selecteer de mapnaam, selecteer de optie **[!UICONTROL Salesforce Data Model]** en selecteert u Bewerken ![Bewerken](assets/edit.png) pictogram voor weergave van het formuliergegevensmodel (FDM).

Nadat u de [[!DNL Salesforce] Cloud Config-service](#configure-salesforce-cloud-service), kunt u adaptieve formulieren integreren met behulp van de doos [!DNL Salesforce] Gegevensmodel.

## Configureren [!DNL Microsoft® Dynamics 365] cloudservice {#configure-dynamics-cloud-service}

Voordat u de [!DNL Microsoft® Dynamics 365] cloudservice, zorg ervoor dat u de volgende taken uitvoert:

* [Een aanvraag registreren voor [!DNL Microsoft® Dynamics 365] met Azure Active Directory](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/walkthrough-register-app-azure-active-directory). Wanneer u de verbinding maakt [!DNL Microsoft® Dynamics 365] -toepassing, geeft u de antwoordURL&#39;s op in de volgende indeling:

  ```
  https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html
  ```

  Waar server en poort verwijzen naar de hostnaam en het poortnummer voor de [!DNL AEM Forms] Server.

* Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de verbonden toepassing.

Voer de volgende stappen uit om het [!DNL Microsoft® Dynamics 365] cloudservice:

1. Aan [!DNL AEM Forms] auteurinstantie, navigeren aan **[!UICONTROL Tools]** ![hamer](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]**. De lijst met beschikbare mappen bevat een map met de titel die is opgegeven voor `DappTitle`  while [het produceren van het project van AEM archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).
1. Selecteer de mapnaam, selecteer **[!UICONTROL Microsoft® Dynamics 365 Cloud Config]** en selecteert u **[!UICONTROL Properties]**.
1. In de **[!UICONTROL Authentication Settings]** tab:
   1. Voer de waarde in voor de **[!UICONTROL Service Root]** veld. Ga naar de instantie Dynamics en navigeer naar [Bronnen voor ontwikkelaars](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources) om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld: `https://<tenant-name>.dynamics.com/api/data/v9.1/`
   1. Geef de client-id (toepassings-id) en het clientgeheim voor de verbonden toepassing op.
   1. Vervangen `{tenant}` met een huurder-id in het **[!UICONTROL OAuth URL]**, **[!UICONTROL Refresh Token URL]**, en **[!UICONTROL Access Token URL]** velden.
   1. Geef de URL van de dynamische instantie op in het dialoogvenster **[!UICONTROL Resource]** te configureren veld [!UICONTROL Microsoft® Dynamics] met een formuliergegevensmodel (FDM). Gebruik de URL van de hoofdmap van de service om de instantie-URL Dynamics af te leiden. Bijvoorbeeld: `https://<tenant-name>.dynamics.com`.

   1. Opgeven `openid` in de **[!UICONTROL Authorization Scope]** veld voor het vergunningsproces op [!DNL Microsoft® Dynamics 365].
   1. Meld u aan met uw [!DNL Microsoft® Dynamics 365] referenties en accepteren om de configuratie van de cloudservice in staat te stellen verbinding te maken met [!DNL Microsoft® Dynamics 365] service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de [!DNL Microsoft® Dynamics 365] de configuratiepagina van de wolkendienst, die een succesbericht toont.
1. Selecteren **[!UICONTROL Save & Close]** om de configuratie te voltooien opstelling.

### Toegang buiten de doos [!DNL Microsoft® Dynamics 365] Formuliergegevensmodel (FDM)

A [!DNL Microsoft® Dynamics 365] FDM (Form Data Model) is beschikbaar in het vak op het tabblad [!DNL AEM Forms] Server na u [een ontwikkelingsproject voor Forms opzetten op basis van het archetype van de Experience Manager](setup-local-development-environment.md##forms-cloud-service-local-development-environment).

Als u toegang wilt krijgen tot het formuliergegevensmodel (FDM), navigeert u naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]**. De lijst met beschikbare mappen bevat een map met de titel die is opgegeven voor `DappTitle`  while [het produceren van het project van AEM archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment). Selecteer de mapnaam, selecteer de optie **[!UICONTROL Microsoft® Dynamics 365 Data Model]** en selecteert u Bewerken ![Bewerken](assets/edit.png) pictogram voor weergave van het formuliergegevensmodel (FDM).

Nadat u de [[!DNL Microsoft® Dynamics 365] Cloud Config-service](#configure-dynamics-cloud-service), kunt u adaptieve formulieren integreren met behulp van de doos [!DNL Microsoft® Dynamics 365] Gegevensmodel.

>[!MORELIKETHIS]
>
>* [Gegevensbronnen configureren voor AEM Forms](/help/forms/configure-data-sources.md)
>* [Azure-opslag voor AEM Forms configureren](/help/forms/configure-azure-storage.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina](/help/forms/configure-forms-portal.md)
