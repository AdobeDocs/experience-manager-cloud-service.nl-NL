---
title: Hoe kan ik configureren [!DNL Microsoft Dynamics] OData voor AEM Forms?
description: Leer om het Model van de Gegevens van de Vorm (FDM) tot stand te brengen dat op de entiteiten, de attributen, en de diensten wordt gebaseerd die in [!DNL Microsoft Dynamics] service.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb7b41f0-fd4f-4ba6-9f45-792a66ba6368
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 1%

---

# [!DNL Microsoft Dynamics] OData-configuratie {#microsoft-dynamics-odata-configuration}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/ms-dynamics-odata-configuration.html) |
| AEM as a Cloud Service | Dit artikel |

![gegevensintegratie](assets/data-integeration.png)

[!DNL Microsoft Dynamics] is een software van het Beheer van de Verhouding van de Klant (CRM) en van de Planning van het Middel van de Onderneming (ERP) die ondernemingsoplossingen voor het creëren van en het beheren van klantenrekeningen, contacten, lood, kansen, en gevallen verstrekt. [[!DNL Experience Manager Forms] Gegevensintegratie](data-integration.md) biedt een OData-cloudserviceconfiguratie voor de integratie van Forms met zowel online als op locatie [!DNL Microsoft Dynamics] server. Hiermee kunt u een FDM (Form Data Model) maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in [!DNL Microsoft Dynamics] service. Met FDM (Form Data Model) kunt u Adaptive Forms maken die interactief werkt met [!DNL Microsoft Dynamics] server om bedrijfswerkstromen toe te laten. Bijvoorbeeld:

* Query [!DNL Microsoft Dynamics] server voor gegevens en vooraf ingevulde Adaptive Forms
* Gegevens schrijven naar [!DNL Microsoft Dynamics] over het indienen van adaptieve formulieren
* Gegevens schrijven in [!DNL Microsoft Dynamics] via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM) en omgekeerd

<!--[!DNL Experience Manager Forms] add-on package also includes reference OData configuration that you can use to quickly integrate [!DNL Microsoft Dynamics] with [!DNL Experience Manager Forms].-->

<!--When the package is installed, the following entities and services are available on your [!DNL Experience Manager Forms] instance:

* MS Dynamics OData Cloud Service (OData Service)-->
<!--* Form Data Model with preconfigured [!DNL Microsoft Dynamics] entities and services.-->

<!-- Preconfigured [!DNL Microsoft Dynamics] entities and services in a Form Data Model are available on your [!DNL Experience Manager Forms] instance only if the run mode for the [!DNL Experience Manager] instance is set as `samplecontent` (default). -->  MS Dynamics OData Cloud Service (OData Service) is beschikbaar in alle uitvoermodi. Voor meer informatie over het vormen van looppaswijzen voor een [!DNL Experience Manager] -instantie, zie [Modi uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#runmodes).

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak om acties in te dienen voor de verwerking van formulierverzendingen. Meer informatie over deze opties vindt u in het gedeelte [Handeling Adaptief verzenden van formulier](/help/forms/configure-submit-actions-core-components.md)  artikel.


## Vereisten {#prerequisites}

Voordat u begint met het instellen en configureren [!DNL Microsoft Dynamics], zorg ervoor dat u:

<!--* Installed the [[!DNL Experience Manager Forms] add-on package](installing-configuring-aem-forms-osgi.md) -->
* geconfigureerd [!DNL Microsoft Dynamics] 365 online of geïnstalleerd een van de volgende exemplaren: [!DNL Microsoft Dynamics] versies:

   * [!DNL Microsoft Dynamics] 365 ter plaatse
   * [!DNL Microsoft Dynamics] 2016 ter plaatse

* [Ingeschreven verzoek om [!DNL Microsoft Dynamics] onlineservice met [!DNL Microsoft Azure] Active Directory](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl [configureren van cloudservice voor uw [!DNL Microsoft Dynamics] service](#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerd [!DNL Microsoft Dynamics] toepassing {#set-reply-url-for-registered-microsoft-dynamics-application}

Voer de volgende handelingen uit om de antwoordURL in te stellen voor geregistreerde [!DNL Microsoft Dynamics] toepassing:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met online [!DNL Microsoft Dynamics] server.

1. Ga naar [!DNL Microsoft Azure] Active Directory-account en voeg de volgende URL voor de configuratie van de cloudservice toe in **[!UICONTROL Reply URLs]** instellingen voor uw geregistreerde toepassing:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![Azure-directory](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Configureren [!DNL Microsoft Dynamics] voor IFD {#configure-microsoft-dynamics-for-ifd}

[!DNL Microsoft Dynamics] gebruikt op beweringen-gebaseerde authentificatie om toegang tot gegevens te verlenen over [!DNL Microsoft Dynamics] CRM-server voor externe gebruikers. Om dit toe te laten, doe het volgende om te vormen [!DNL Microsoft Dynamics] voor Internet-Onder ogen ziet plaatsing (IFD) en vorm claimmontages.

>[!NOTE]
>
> Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met [!DNL Microsoft Dynamics] server.

1. Configureren [!DNL Microsoft Dynamics] exemplaar ter plaatse voor IFD zoals beschreven in [IFD configureren voor [!DNL Microsoft Dynamics]](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten te vormen [!DNL Microsoft Dynamics]:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [Toepassingsregistratie voor CRM op locatie (IFD)](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor meer informatie.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren [!DNL Experience Manager Forms] met [!DNL Microsoft Dynamics] server.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waarbij:

   * `Client-ID` is een cliëntidentiteitskaart u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de [!DNL Microsoft Dynamics] OData-cloudservice op [!DNL Experience Manager Forms]. De standaardcloudservice geïnstalleerd met de [!DNL Experience Manager Forms] wordt geïmplementeerd op de volgende URL:
     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waarbij:

   * `resource` is de [!DNL Microsoft Dynamics] organisatie-URL.

1. [!DNL Microsoft Dynamics] gebruikt het HTTPS-protocol. AD FS-eindpunten aanroepen vanuit [!DNL Forms] server, installeren [!DNL Microsoft Dynamics] sitecertificaat naar Java-certificaatarchief met het `keytool` de opdracht op de computer uitvoeren [!DNL Experience Manager Forms].

## Cloudservice configureren voor uw [!DNL Microsoft Dynamics] service {#configure-cloud-service-for-your-microsoft-dynamics-service}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Een OData-service configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u de dienstwortel URL voor de dienst hebt, en doe het volgende:

<!--The **MS Dynamics OData Cloud Service (OData Service)** configuration comes with default OData configuration. To configure it to connect with your [!DNL Microsoft Dynamics] service, do the following.-->

>[!NOTE]
>
>Voor geleidelijke gids om te vormen [!DNL Microsoft Dynamics 365], online of ter plaatse, zie [[!DNL Microsoft Dynamics] OData-configuratie](ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL OData Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
In de **[!UICONTROL Authentication Settings]** tab:

   1. Voer de waarde in voor de **[!UICONTROL Service Root]** veld. Ga naar de instantie Dynamics en navigeer naar **[!UICONTROL Developer Resources]** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;tenant-name>/api/data/v9.1/

   1. Selecteren **[!UICONTROL OAuth 2.0]** als het verificatietype.

   1. De standaardwaarden vervangen in het dialoogvenster **[!UICONTROL Client Id]** (ook aangeduid als **Toepassings-id**), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL Refresh Token URL]**, **[!UICONTROL Access Token URL]**, en **[!UICONTROL Resource]** velden met waarden uit uw [!DNL Microsoft Dynamics] serviceconfiguratie. Het is verplicht de URL van de dynamische instantie op te geven in het dialoogvenster **[!UICONTROL Resource]** te configureren veld [!DNL Microsoft Dynamics] met een formuliergegevensmodel (FDM). Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld: [https://org.crm.dynamics.com](https://org.crm.dynamics.com/).

   1. Opgeven **[!UICONTROL openid]** in de **[!UICONTROL Authorization Scope]** veld voor het vergunningsproces op [!DNL Microsoft Dynamics].

      ![Verificatie-instellingen](assets/dynamics_authentication_settings_new.png)
Formuliergegevensmodel (FDM)
1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar [!DNL Microsoft Dynamics] aanmeldingspagina
1. Meld u aan met uw [!DNL Microsoft Dynamics] referenties en accepteren om de configuratie van de cloudservice in staat te stellen verbinding te maken met [!DNL Microsoft Dynamics] service. Het is een eenmalige taak om het Model van de Gegevens van de Vorm (FDM) de clouddienst en de dienst te vestigen.

   U bent het Model van de Gegevens van de Vorm de pagina van de de dienstconfiguratie van de wolk, die een bericht toont dat de configuratie OData met succes wordt bewaard.

De de wolkendienst van de Cloud Service van de Dynamica van MS (OData Service) wordt gevormd en met uw dienst van de Dynamica verbonden. Formuliergegevensmodel (FDM)

## Formuliergegevensmodel (FDM) maken {#create-form-data-model}

<!--When you install the [!DNL Experience Manager Forms] package, a form data model, **[!DNL Microsoft Dynamics] FDM**, is deployed on your [!DNL Experience Manager] instance. By default, the Form Data Model uses [!DNL Microsoft Dynamics] service configured in the MS Dynamics OData Cloud Service (OData Service) as its data source.

On opening the Form Data Model for the first time, it connects to the configured [!DNL Microsoft Dynamics] service and fetches entities from your [!DNL Microsoft Dynamics] instance. The "contact" and "lead" entities from [!DNL Microsoft Dynamics] are already added in the form data model.

To review the form data model, go to **[!UICONTROL Form Data Model egrations]**. Select **[!DNL Microsoft Dynamics] FDM** and click **[!UICONTROL Edit]** to open the Form Data Model in edit mode. Alternatively, you can open the Form Data Model directly from the following URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`
 Form Data Model 
![default-fdm-1](assets/default-fdm-1.png)-->

Nadat u de MS Dynamics OData-cloudservice hebt geconfigureerd, kunt u de service gebruiken tijdens het maken van een FDM-model (Form Data Model). Zie voor meer informatie [Formuliergegevensmodel maken (FDM)](create-form-data-models.md).

Vervolgens kunt u een adaptief formulier-gebaseerd formuliergegevensmodel (FDM) maken en dit gebruiken in verschillende gebruiksgevallen van adaptieve formulieren, zoals:

* Adaptief formulier vooraf invullen door informatie op te vragen van [!DNL Microsoft Dynamics] entiteiten en diensten
* Invoeden [!DNL Microsoft Dynamics] serverbewerkingen die zijn gedefinieerd in een formuliergegevensmodel (FDM) met behulp van adaptieve formulierregels
* Verzonden formuliergegevens schrijven naar [!DNL Microsoft Dynamics] entiteiten

<!--It is recommended to create a copy of the Form Data Model provided with the [!DNL Experience Manager Forms] package and configure data models and services to suit your requirements. It will ensure that any future updates to the package do not override your form data model.-->

U kunt [De handeling Verzenden van formuliergegevensmodel configureren](/help/forms/using-form-data-model.md) voor een adaptief formulier om gegevens naar Microsoft Dynamics OData te verzenden.

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van de Vorm (FDM) in bedrijfswerkschema&#39;s, zie [Gegevensintegratie](data-integration.md).

## Verwante artikelen

{{af-submit-action}}
