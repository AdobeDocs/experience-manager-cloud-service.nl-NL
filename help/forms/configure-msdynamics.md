---
title: Hoe te om Microsoft Dynamics 365 uit de doos gegevensmodellen van de vormgegevens voor Adaptive Forms te vormen?
description: Leer hoe u Microsoft Dynamics 365 kunt integreren met Adaptive Forms.
feature: Adaptive Forms, Form Data Model
role: User, Developer
source-git-commit: 25284474793742a1af28e3c81976a3061d9eaf3e
workflow-type: tm+mt
source-wordcount: '869'
ht-degree: 0%

---


# Microsoft® Dynamics 365 for AEM Forms configureren

Adobe Experience Manager Forms Data Integration biedt een cloudserviceconfiguratie voor de integratie van formulieren met de Microsoft Dynamics-server. Hiermee kunt u een FDM (Form Data Model) maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in de Microsoft Dynamics-service. Met het Form Data Model (FDM) kunt u Adaptive Forms maken die met de Microsoft Dynamics-server werkt om bedrijfsworkflows in te schakelen. Bijvoorbeeld:
* Vraag een Microsoft Dynamics-server naar gegevens en vul Adaptief Forms vooraf in.
* Gegevens naar Microsoft Dynamics schrijven bij het verzenden van een adaptief formulier.
* Schrijf gegevens in Microsoft Dynamics via aangepaste entiteiten die zijn gedefinieerd in FDM (Form Data Model).

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

<!-- 
[[!DNL Experience Manager Forms] Data Integration](data-integration.md) provides [!DNL Microsoft&reg; Dynamics 365] Cloud Services to integrate Adaptive Forms with out of the box Form Data Model (FDM). The Adaptive Forms can then interact with [!DNL Microsoft&reg; Dynamics 365] servers to enable business workflows. For example:

* Write data into [!DNL Microsoft&reg; Dynamics 365] on Adaptive Form submission.
* Write data in [!DNL Microsoft&reg; Dynamics 365] through custom entities defined in Form Data Model (FDM) and conversely.
* Query [!DNL Microsoft&reg; Dynamics 365]server for data and prepopulate Adaptive Forms.
* Read data from [!DNL Microsoft&reg; Dynamics 365] server.

[!DNL Microsoft&reg; Dynamics 365] cloud services and Form Data Model (FDM) are available out of the box on the [!DNL AEM Forms] Server after you [set up a development project for Forms based on Experience Manager archetype](setup-local-development-environment.md#forms-cloud-service-local-development-environment).

>[!NOTE]
>
>Microsoft&reg; Dynamics 365 cloud services and Form Data Model (FDM) are available out of the box only if you set up an [!DNL Experience Manager Forms] as a [!DNL Cloud Service] project based on [AEM Archetype 30](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-30) or later.-->

## Vereisten

Controleer voordat u [!DNL Microsoft® Dynamics 365] integreert met AEM Forms as a Cloud Service of u de volgende stappen hebt uitgevoerd:


1. **opstelling de rekening in Microsoft Dynamics 365**

   Voer de in de video beschreven stappen uit om een Microsoft Dynamics 365-account in te stellen. In deze video wordt een proefaccount gemaakt voor demonstratiedoeleinden.

   >[!VIDEO](https://video.tv.adobe.com/v/3444389/)

1. **creeer een rekening in het Beheercentrum van het Platform van de Macht**
Creeer een rekening in het **Centrum van Admin van het Platform van de Macht** aan:
   * Gegevensinvoer toevoegen
   * Microsoft Dynamics 365-toepassingen inschakelen

   Voer de stappen in de video uit om een account te maken in het Power Platform Admin Center. In deze video is een proefaccount gemaakt voor demonstratiedoeleinden.
   >[!VIDEO](https://video.tv.adobe.com/v/3444388)

1. **Registreer een toepassing voor [!DNL Microsoft® Dynamics 365] in Azure Actieve Folder**

   Voer de stappen in de video uit om een toepassing voor [!DNL Microsoft® Dynamics 365] te registreren in Azure Active Directory.

   >[!VIDEO](https://video.tv.adobe.com/v/3444369/dynamics365integration-microsoftdynamics-apiaccess-azuread-appregistration)

   >[!NOTE]
   >
   > * Om de verbonden [!DNL Microsoft® Dynamics 365] toepassing tot stand te brengen, selecteer **Web** als platform en specificeer **Redirect URI** in het volgende formaat: `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/fdm.html`.
   > * Zorg ervoor dat u de client-id (ook wel de toepassings-id genoemd) en het clientgeheim opslaat voor toekomstig gebruik.

## Forms verbinden met Microsoft® Dynamics 365

Zodra u de hierboven vermelde voorwaarden hebt geconfigureerd, kunt u doorgaan met het integreren van Adaptive Forms met Microsoft® Dynamics 365. Voer de volgende stappen uit om gegevens naar Microsoft® Dynamics 365 te verzenden wanneer het formulier wordt verzonden:

[1. Configuratie van cloudservice voor Microsoft Dynamics configureren](#1-configure-cloud-service-configuration-for-microsoft-dynamics)

[2. Formuliergegevensmodel (FDM) maken](#2-create-form-data-model-fdm)

### 1. Configuratie van cloudservice voor Microsoft Dynamics configureren

>[!VIDEO](https://video.tv.adobe.com/v/3444370/cloudconfiguration-dataintegration-adobeexperiencemanager-aemforms-microsoftdynamics)

Voer de volgende stappen uit om de configuratie van de cloudservice van [!DNL Microsoft® Dynamics 365] te configureren:

1. Navigeer aan **[!UICONTROL Tools]** ![ hammer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]** op [!DNL AEM Forms] auteursinstantie,.

   ![ Uitgezochte de Gegevens van de Wolk Source ](/help/forms/assets/dynamics-data-source.png)
1. Selecteer een configurContainer. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]**.

   ![ creeer de Configuratie van de Wolk ](/help/forms/assets/dynamics-select-configuration.png)

   **creeer de configuratietovenaar van Source van Gegevens** verschijnt.

   ![ creeer de tovenaar van de Configuratie van Gegevens Source ](/help/forms/assets/dynamics-create-data-configuration.png)

1. Specificeer **[!UICONTROL Title]**, **[!UICONTROL Name]** en selecteer **[!UICONTROL Service Type]** als **OData Dienst**.
1. Klik op **[!UICONTROL Next]**. Het **lusje van de Authentificatie** verschijnt.

   ![ het Lusje van de Authentificatie ](/help/forms/assets/dynamics-authentication-tab.png)

1. Geef de waarde voor het veld **[!UICONTROL Service Root]** op.

   Ga naar uw instantie van de Dynamiek in het **Centrum van Admin van het Platform van de Macht** en navigeer aan [ Middelen van de Ontwikkelaar ](https://docs.microsoft.com/en-us/powerapps/developer/data-platform/view-download-developer-resources) om de waarde van de **Wortel van de Dienst** te bekijken. Het **Web API eindpunt** vertegenwoordigt de **wortel van de Dienst** waarde voor de instantie van de Dynamiek u met Aanpassings Forms wilt integreren. De **Wortel van de Dienst** URL is in het volgende formaat: `https://<tenant-name>.dynamics.com/api/data/v9.1/`

   ![ het gebied van de Wortel van de Dienst ](/help/forms/assets/dynamics-service-root.png)

1. Selecteer **[!UICONTROL Authentication Type]** als **OAuth2.0**.
1. Specificeer **identiteitskaart van de Cliënt** (die als identiteitskaart van de Toepassing wordt bedoeld) en **Geheime Cliënt** voor de verbonden toepassing.
U kunt **identiteitskaart van de Cliënt 1} terugwinnen en** Geheime Cliënt **van de Azure Actieve Toepassing van de Folder.**

   ![ identiteitskaart van de Cliënt en Geheime Cliënt ](/help/forms/assets/dynamics-azure-app-resgistration.png)

1. Geef het volgende op in de velden **[!UICONTROL OAuth URL]** , **[!UICONTROL Refresh Token URL]** en **[!UICONTROL Access Token URL]** .
U kunt **[!UICONTROL OAuth URL]** terugwinnen, **[!UICONTROL Refresh Token URL]**, en **[!UICONTROL Access Token URL]** van de **Eindpunten** sectie van uw Azure Actieve Toepassing van de Folder.

   ![ Azure App Endpoints ](/help/forms/assets/dynamics-azure-app-endpoints.png)

1. Geef `openid` op in het veld **[!UICONTROL Authorization Scope]** voor autorisatieproces op [!DNL Microsoft® Dynamics 365] .
1. Geef in het veld **[!UICONTROL Resource]** de URL van de dynamische instantie op om [!DNL Microsoft® Dynamics 365] te configureren met een FDM (Form Data Model).
U kunt het **Milieu URL** van het **Centrum van Admin van het Platform van de Macht** kopiëren of de instantie URL van de Dynamiek voortbrengen gebruikend de **Wortel van de Dienst** URL. De bron-URL heeft de volgende indeling: `https://<tenant-name>.dynamics.com`.

   ![ Gebied van het Middel van de Toepassing van de Macht ](/help/forms/assets/dynamics-resource-field.png)

1. Meld u aan met uw [!DNL Microsoft® Dynamics 365] -referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de [!DNL Microsoft® Dynamics 365] -service. Als de verbinding tot stand is gebracht, wordt u omgeleid naar de configuratiepagina van de cloudservice van [!DNL Microsoft® Dynamics 365] , die een succesbericht weergeeft.
1. Selecteer **[!UICONTROL Create]** om de configuratie op te slaan.

### 2. Formuliergegevensmodel (FDM) maken

>[!VIDEO](https://video.tv.adobe.com/v/3444367/aemforms-adobeexperiencemanager-formdatamodel--dataintegration-digitalforms)

U kunt het FDM (Form Data Model) maken met de gemaakte cloudconfiguratie van [!DNL Microsoft® Dynamics 365] . Voer de volgende stappen uit om een formuliergegevensmodel te maken:

1. Navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Data Integrations]** .
   ![ creeer het Model van de Gegevens van de Vorm ](/help/forms/assets/dynamics-create-fdm.png)

1. Klik op **[!UICONTROL Create]** en selecteer **[!UICONTROL Form data Model]** .
   ![ Uitgezochte Model van de Gegevens van de Vorm ](/help/forms/assets/dynamics-select-fdm.png)

   De **Create tovenaar van de Gegevens van de Vorm** verschijnt.
1. Klik op **[!UICONTROL Next]**.
1. Selecteer de gecreeerde wolkenconfiguratie van **Uitgezochte Gegevensbron** tabel.
   ![ Uitgezochte de Configuratie van de Wolk ](/help/forms/assets/dynamics-select-cloud-config.png)

1. Klik uitgeven ![ ](assets/edit.png) pictogram uitgeven {om het Model van de Gegevens van de Vorm (FDM) te bekijken en te vormen.

Daarna, kunt u [ het Model van de Gegevens van de Vorm (FDM) vormen ](/help/forms/work-with-form-data-model.md#configure-services) en het gebruiken in diverse Aanpassings het gebruiksgevallen van de Vorm, zoals:

* Aangepast formulier vooraf invullen door informatie op te vragen van [!DNL Microsoft Dynamics] -entiteiten en -services
* [!DNL Microsoft Dynamics] serverbewerkingen aanroepen die met behulp van adaptieve formulierregels zijn gedefinieerd in een formuliergegevensmodel (FDM)
* Verzonden formuliergegevens naar [!DNL Microsoft Dynamics] -entiteiten schrijven
* U kunt het formuliergegevensmodel zodanig configureren dat een adaptief formulier gegevens verzendt naar [!DNL Microsoft Dynamics] .

U kunt [ dan gebruiken voorleggen gebruikend het Model van de Gegevens van de Vorm (FDM) ](/help/forms/using-form-data-model.md) optie in een **Aangepaste Vorm** om gegevens van uw vorm naar gevormd over te brengen [!DNL Microsoft® Dynamics 365].


>[!MORELIKETHIS]
>
>* [ vorm gegevensbronnen voor AEM Forms ](/help/forms/configure-data-sources.md)
>* [ vorm Azure opslag voor AEM Forms ](/help/forms/configure-azure-storage.md)
>  [Forms Portal toevoegen aan een AEM Sites-pagina ](/help/forms/configure-forms-portal.md)