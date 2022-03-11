---
title: Hoe te vormen [!DNL Microsoft Dynamics] OData?
description: Leer hoe u een formuliergegevensmodel maakt op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in [!DNL Microsoft Dynamics] service. Met het formuliergegevensmodel kunt u een adaptieve Forms maken die interactief werkt met [!DNL Microsoft Dynamics] om bedrijfsworkflows in te schakelen.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb7b41f0-fd4f-4ba6-9f45-792a66ba6368
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---

# [!DNL Microsoft Dynamics] OData-configuratie {#microsoft-dynamics-odata-configuration}

![gegevensintegratie](assets/data-integeration.png)

[!DNL Microsoft Dynamics] is a Customer Relationship Management (CRM) and Enterprise Resource Planning (ERP) software that provides enterprise solutions for creating and managing customer accounts, contacts, leads, opportunities, and cases. [[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md) biedt een OData-cloudserviceconfiguratie voor de integratie van Forms met zowel online als op locatie [!DNL Microsoft Dynamics] server. Hiermee kunt u een formuliergegevensmodel maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in [!DNL Microsoft Dynamics] service. The Form Data Model can be used to create Adaptive Forms that interact with [!DNL Microsoft Dynamics] server to enable business workflows. Bijvoorbeeld:

* Query [!DNL Microsoft Dynamics] server voor gegevens en vooraf ingevulde Adaptive Forms
* Write data into [!DNL Microsoft Dynamics] on Adaptive Form submission
* Gegevens schrijven in [!DNL Microsoft Dynamics] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel en omgekeerd

<!--[!DNL Experience Manager Forms] add-on package also includes reference OData configuration that you can use to quickly integrate [!DNL Microsoft Dynamics] with [!DNL Experience Manager Forms].-->

<!--When the package is installed, the following entities and services are available on your [!DNL Experience Manager Forms] instance:

* MS Dynamics OData Cloud Service (OData Service)-->
<!--* Form Data Model with preconfigured [!DNL Microsoft Dynamics] entities and services.-->

<!-- Preconfigured [!DNL Microsoft Dynamics] entities and services in a Form Data Model are available on your [!DNL Experience Manager Forms] instance only if the run mode for the [!DNL Experience Manager] instance is set as `samplecontent` (default). -->  MS Dynamics OData Cloud Service (OData Service) is available with all run modes. For more information on configuring run modes for an [!DNL Experience Manager] instance, see [Run Modes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#runmodes).

## Vereisten {#prerequisites}

Voordat u begint met instellen en configureren [!DNL Microsoft Dynamics], zorg ervoor dat u:

<!--* Installed the [[!DNL Experience Manager Forms] add-on package](installing-configuring-aem-forms-osgi.md) -->
* Gevormd [!DNL Microsoft Dynamics] 365 online of geïnstalleerd een van de volgende exemplaren [!DNL Microsoft Dynamics] versies:

   * [!DNL Microsoft Dynamics] 365 ter plaatse
   * [!DNL Microsoft Dynamics] 2016 on-premises

* [Ingeschreven [!DNL Microsoft Dynamics] onlineservice met [!DNL Microsoft Azure] Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Take a note of the values for the client ID (also referred to as application ID) and client secret for the registered service. These values are used while [configuring cloud service for your [!DNL Microsoft Dynamics] service](#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerd [!DNL Microsoft Dynamics] toepassing {#set-reply-url-for-registered-microsoft-dynamics-application}

Do the following to set the Reply URL for registered [!DNL Microsoft Dynamics] application:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met online [!DNL Microsoft Dynamics] server.

1. Ga naar [!DNL Microsoft Azure] Active Directory-account en voeg de volgende URL voor de configuratie van de cloudservice toe in **[!UICONTROL Reply URLs]** instellingen voor uw geregistreerde toepassing:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure-directory](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Configureren [!DNL Microsoft Dynamics] voor IFD {#configure-microsoft-dynamics-for-ifd}

[!DNL Microsoft Dynamics] uses claims-based authentication to provide access to data on [!DNL Microsoft Dynamics] CRM server to external users. Om dit toe te laten, doe het volgende om te vormen [!DNL Microsoft Dynamics] voor Internet-Onder ogen ziet plaatsing (IFD) en vorm claimmontages.

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met [!DNL Microsoft Dynamics] server.

1. Configureren [!DNL Microsoft Dynamics] exemplaar ter plaatse voor IFD zoals beschreven in [IFD configureren voor [!DNL Microsoft Dynamics]](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Run the following commands using Windows PowerShell to configure claim settings on IFD-enabled [!DNL Microsoft Dynamics]:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   See [App registration for CRM on-premises (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) for details.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met [!DNL Microsoft Dynamics] server.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Where:

   * `Client-ID` is een cliëntidentiteitskaart u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de [!DNL Microsoft Dynamics] OData-cloudservice op [!DNL Experience Manager Forms]. De standaardcloudservice geïnstalleerd met de [!DNL Experience Manager Forms] wordt geïmplementeerd op de volgende URL:
      `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waar:

   * `resource` is de [!DNL Microsoft Dynamics] organisatie-URL.

1. [!DNL Microsoft Dynamics] uses HTTPS protocol. AD FS-eindpunten aanroepen vanuit [!DNL Forms] server, installeren [!DNL Microsoft Dynamics] sitecertificaat naar Java-certificaatarchief met het `keytool` de opdracht op de computer uitvoeren [!DNL Experience Manager Forms].

## Cloudservice configureren voor uw [!DNL Microsoft Dynamics] service {#configure-cloud-service-for-your-microsoft-dynamics-service}

An OData service is identified by its service root URL. Een OData-service configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u de dienstwortel URL voor de dienst hebt, en doe het volgende:

<!--The **MS Dynamics OData Cloud Service (OData Service)** configuration comes with default OData configuration. To configure it to connect with your [!DNL Microsoft Dynamics] service, do the following.-->

>[!NOTE]
>
>Voor geleidelijke gids om te vormen [!DNL Microsoft Dynamics 365], online of ter plaatse, zie [[!DNL Microsoft Dynamics] OData-configuratie](ms-dynamics-odata-configuration.md).

1. Go to **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   See [Configure folder for cloud service configurations](#cloud-folder) for information about creating and configuring a folder for cloud service configurations.

1. Tikken **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Specify a name and optionally a title for the configuration, select **[!UICONTROL OData Service]** from the **[!UICONTROL Service Type]** drop-down, optionally browse and select a thumbnail image for the configuration, and tap **[!UICONTROL Next]**.
In the **[!UICONTROL Authentication Settings]** tab:

   1. Voer de waarde in voor de **[!UICONTROL Service Root]** veld. Ga naar de instantie Dynamics en navigeer naar **[!UICONTROL Developer Resources]** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;tenant-name>/api/data/v9.1/

   1. Selecteren **[!UICONTROL OAuth 2.0]** als het verificatietype.

   1. De standaardwaarden in het dialoogvenster **[!UICONTROL Client Id]** (ook aangeduid als **Toepassings-id**), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL Refresh Token URL]**, **[!UICONTROL Access Token URL]**, en **[!UICONTROL Resource]** velden met waarden uit uw [!DNL Microsoft Dynamics] serviceconfiguratie. It is mandatory to specify the dynamics instance URL in the **[!UICONTROL Resource]** field to configure [!DNL Microsoft Dynamics] with a form data model. Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. For example, [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. Opgeven **[!UICONTROL openid]** in de **[!UICONTROL Authorization Scope]** veld voor het vergunningsproces op [!DNL Microsoft Dynamics].

      ![Verificatie-instellingen](assets/dynamics_authentication_settings_new.png)
Formuliergegevensmodel
1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar [!DNL Microsoft Dynamics] aanmeldingspagina.
1. Meld u aan met uw [!DNL Microsoft Dynamics] referenties en accepteren om de configuratie van de cloudservice in staat te stellen verbinding te maken met [!DNL Microsoft Dynamics] service. Het is een eenmalige taak om het Model van de Gegevens van de Vorm tussen de clouddienst en de dienst te vestigen.

   U bent het Model van de Gegevens van de Vorm de pagina van de de dienstconfiguratie van de wolk, die een bericht toont dat de configuratie OData met succes wordt bewaard.

The MS Dynamics OData Cloud Service (OData Service) cloud service is configured and connected with your Dynamics service. Form Data Model  Form Data Model

## Formuliergegevensmodel maken {#create-form-data-model}

<!--When you install the [!DNL Experience Manager Forms] package, a form data model, **[!DNL Microsoft Dynamics] FDM**, is deployed on your [!DNL Experience Manager] instance. By default, the Form Data Model uses [!DNL Microsoft Dynamics] service configured in the MS Dynamics OData Cloud Service (OData Service) as its data source.

On opening the Form Data Model for the first time, it connects to the configured [!DNL Microsoft Dynamics] service and fetches entities from your [!DNL Microsoft Dynamics] instance. The "contact" and "lead" entities from [!DNL Microsoft Dynamics] are already added in the form data model.

To review the form data model, go to **[!UICONTROL Form Data Model egrations]**. Select **[!DNL Microsoft Dynamics] FDM** and click **[!UICONTROL Edit]** to open the Form Data Model in edit mode. Alternatively, you can open the Form Data Model directly from the following URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`
 Form Data Model 
![default-fdm-1](assets/default-fdm-1.png)-->

After configuring MS Dynamics OData Cloud Ser Form Data Model ce) cloud service, you can use the service while creating form data models. Zie voor meer informatie [Formuliergegevensmodel maken](create-form-data-models.md).

Vervolgens kunt u een adaptief formulier maken op basis van het formuliergegevensmodel en dit gebruiken in verschillende gebruiksgevallen van het adaptieve formulier, zoals:

* Adaptief formulier vooraf invullen door informatie op te vragen van [!DNL Microsoft Dynamics] entiteiten en diensten
* Invoeden [!DNL Microsoft Dynamics] serverbewerkingen die zijn gedefinieerd in een formuliergegevensmodel met behulp van adaptieve formulierregels
* Write submitted form data to [!DNL Microsoft Dynamics] entities

<!--It is recommended to create a copy of the Form Data Model provided with the [!DNL Experience Manager Forms] package and configure data models and services to suit your requirements. It will ensure that any future updates to the package do not override your form data model.-->

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van het Formulier in bedrijfswerkschema&#39;s, zie [Gegevensintegratie](data-integration.md).
