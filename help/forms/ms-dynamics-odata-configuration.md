---
title: Hoe vorm ik  [!DNL Microsoft Dynamics]  OData voor AEM Forms?
description: Leer om het Model van de Gegevens van de Vorm (FDM) tot stand te brengen dat op de entiteiten, de attributen, en de diensten in  [!DNL Microsoft Dynamics]  worden bepaald dienst.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb7b41f0-fd4f-4ba6-9f45-792a66ba6368
hide: true
hidefromtoc: true
source-git-commit: 3a12fff170f521f6051f0c24a4eb28a12439eec1
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 1%

---

# [!DNL Microsoft Dynamics] OData-configuratie {#microsoft-dynamics-odata-configuration}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/ms-dynamics-odata-configuration.html) |
| AEM as a Cloud Service | Dit artikel |

![ gegeven-integratie ](assets/data-integeration.png)

[!DNL Microsoft Dynamics] is een software van het Beheer van de Verhouding van de Klant (CRM) en van de Planning van het Middel van de Onderneming (ERP) die ondernemingsoplossingen voor het creëren van en het beheren van klantenrekeningen, contacten, lood, kansen, en gevallen verstrekt. [[!DNL Experience Manager Forms]  de Integratie van Gegevens ](data-integration.md) verstrekt een configuratie van de wolkendienst OData om Forms met zowel online als op-gebouw [!DNL Microsoft Dynamics] server te integreren. Hiermee kunt u FDM (Form Data Model) maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in de [!DNL Microsoft Dynamics] -service. Met FDM (Form Data Model) kunt u Adaptive Forms maken dat met [!DNL Microsoft Dynamics] Server werkt om bedrijfsworkflows in te schakelen. Bijvoorbeeld:

* Query [!DNL Microsoft Dynamics] -server voor gegevens en het vooraf invullen van Adaptive Forms
* Gegevens naar [!DNL Microsoft Dynamics] schrijven bij het verzenden van een adaptief formulier
* Gegevens in [!DNL Microsoft Dynamics] schrijven via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel (FDM), en omgekeerd

<!--[!DNL Experience Manager Forms] add-on package also includes reference OData configuration that you can use to quickly integrate [!DNL Microsoft Dynamics] with [!DNL Experience Manager Forms].-->

<!--When the package is installed, the following entities and services are available on your [!DNL Experience Manager Forms] instance:

* MS Dynamics OData Cloud Service (OData Service)-->
<!--* Form Data Model with preconfigured [!DNL Microsoft Dynamics] entities and services.-->

<!-- Preconfigured [!DNL Microsoft Dynamics] entities and services in a Form Data Model are available on your [!DNL Experience Manager Forms] instance only if the run mode for the [!DNL Experience Manager] instance is set as `samplecontent` (default). -->  MS Dynamics OData Cloud Service (OData Service) is beschikbaar in alle uitvoermodi. Voor meer informatie bij het vormen looppas wijzen voor een [!DNL Experience Manager] instantie, zie [ Wijzen van de Looppas ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#runmodes).

AEM as a Cloud Service biedt verschillende mogelijkheden in het vak Acties verzenden voor het verwerken van verzonden formulieren. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).


## Vereisten {#prerequisites}

Voordat u begint met het instellen en configureren van [!DNL Microsoft Dynamics] , moet u controleren of:

<!--* Installed the [[!DNL Experience Manager Forms] add-on package](installing-configuring-aem-forms-osgi.md) -->
* Configureerde [!DNL Microsoft Dynamics] 365 online of installeerde een instantie van een van de volgende [!DNL Microsoft Dynamics] -versies:

   * [!DNL Microsoft Dynamics] 365 op locatie
   * [!DNL Microsoft Dynamics] 2016 op locatie

* [ registreerde de toepassing voor  [!DNL Microsoft Dynamics]  online dienst met  [!DNL Microsoft Azure]  Actieve Folder ](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl [ het vormen de wolkendienst voor uw  [!DNL Microsoft Dynamics]  dienst ](#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerde [!DNL Microsoft Dynamics] -toepassing {#set-reply-url-for-registered-microsoft-dynamics-application}

Ga als volgt te werk om de antwoordURL voor geregistreerde [!DNL Microsoft Dynamics] -toepassing in te stellen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens het integreren van [!DNL Experience Manager Forms] met de online [!DNL Microsoft Dynamics] -server.

1. Ga naar [!DNL Microsoft Azure] Active Directory-account en voeg de volgende URL voor de configuratie van de cloudservice toe in **[!UICONTROL Reply URLs]** -instellingen voor uw geregistreerde toepassing:

   `https://[server]:[port]/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![ Azure folder ](assets/azure_directory_new.png)

1. Sla de configuratie op.

## [!DNL Microsoft Dynamics] configureren voor IFD {#configure-microsoft-dynamics-for-ifd}

[!DNL Microsoft Dynamics] gebruikt op claims gebaseerde verificatie om externe gebruikers toegang te bieden tot gegevens op de [!DNL Microsoft Dynamics] CRM-server. Om dit in te schakelen, doet u het volgende om [!DNL Microsoft Dynamics] voor Internet-Onder ogen ziende plaatsing (IFD) te vormen en claimmontages te vormen.

>[!NOTE]
>
> Gebruik deze procedure alleen tijdens de integratie van [!DNL Experience Manager Forms] met de server op locatie [!DNL Microsoft Dynamics] .

1. Vorm [!DNL Microsoft Dynamics] op-gebouwinstantie voor IFD zoals die in [ wordt beschreven vorm IFD voor  [!DNL Microsoft Dynamics] ](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten te vormen [!DNL Microsoft Dynamics]:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [ registratie van de app voor CRM op-gebouw (IFD) ](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor details.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van [!DNL Experience Manager Forms] met de server op locatie [!DNL Microsoft Dynamics] .

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId “<Client-ID>” -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waarbij:

   * `Client-ID` is een cliëntID u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de [!DNL Microsoft Dynamics] OData-cloudservice op [!DNL Experience Manager Forms] . De standaardcloudservice die met de [!DNL Experience Manager Forms] wordt geïnstalleerd, wordt geïmplementeerd op de volgende URL:
     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier “<Client-ID>” -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waarbij:

   * `resource` is de [!DNL Microsoft Dynamics] organisatie-URL.

1. [!DNL Microsoft Dynamics] gebruikt het HTTPS-protocol. Als u AD FS-eindpunten wilt aanroepen vanaf de [!DNL Forms] -server, installeert u [!DNL Microsoft Dynamics] -sitecertificaat naar het Java-certificaatarchief met de opdracht `keytool` op de computer waarop [!DNL Experience Manager Forms] wordt uitgevoerd.

## Cloudservice configureren voor uw [!DNL Microsoft Dynamics] -service {#configure-cloud-service-for-your-microsoft-dynamics-service}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service wilt configureren in [!DNL Experience Manager] as a Cloud Service, moet u ervoor zorgen dat u de servicebasis-URL voor de service hebt en moet u het volgende doen:

<!--The **MS Dynamics OData Cloud Service (OData Service)** configuration comes with default OData configuration. To configure it to connect with your [!DNL Microsoft Dynamics] service, do the following.-->

>[!NOTE]
>
>Voor geleidelijke gids om [!DNL Microsoft Dynamics 365], online of op-gebouw te vormen, zie [[!DNL Microsoft Dynamics]  Configuratie OData ](ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL OData Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
Op het tabblad **[!UICONTROL Authentication Settings]** :

   1. Voer de waarde voor het veld **[!UICONTROL Service Root]** in. Ga naar de instantie van de Dynamiek en navigeer aan **[!UICONTROL Developer Resources]** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;huurder-name>/api/data/v9.1/

   1. Selecteer **[!UICONTROL OAuth 2.0]** als verificatietype.

   1. Vervang de standaardwaarden in **[!UICONTROL Client Id]** (die ook als **identiteitskaart van de Toepassing** worden bedoeld), **[!UICONTROL Client Secret]**, **[!UICONTROL OAuth URL]**, **[!UICONTROL Refresh Token URL]**, **[!UICONTROL Access Token URL]**, en **[!UICONTROL Resource]** gebieden met waarden van uw [!DNL Microsoft Dynamics] de dienstconfiguratie. Het is verplicht de URL van de instantie dynamics op te geven in het veld **[!UICONTROL Resource]** om [!DNL Microsoft Dynamics] te configureren met een formuliergegevensmodel (FDM). Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld, [ https://org.crm.dynamics.com ](https://org.crm.dynamics.com/).

   1. Geef **[!UICONTROL openid]** op in het veld **[!UICONTROL Authorization Scope]** voor autorisatieproces op [!DNL Microsoft Dynamics] .

      ![ Montages van de Authentificatie ](assets/dynamics_authentication_settings_new.png)
Formuliergegevensmodel (FDM)
1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de aanmeldingspagina van [!DNL Microsoft Dynamics] .
1. Meld u aan met uw [!DNL Microsoft Dynamics] -referenties en accepteer dit om de configuratie van de cloudservice in staat te stellen verbinding te maken met de [!DNL Microsoft Dynamics] -service. Het is een eenmalige taak om het Model van de Gegevens van de Vorm (FDM) de clouddienst en de dienst te vestigen.

   U bent het Model van de Gegevens van de Vorm de pagina van de de dienstconfiguratie van de wolk, die een bericht toont dat de configuratie OData met succes wordt bewaard.

De MS Dynamics OData Cloud Service (OData Service)-cloudservice is geconfigureerd en verbonden met uw Dynamics-service. Formuliergegevensmodel (FDM)

## Formuliergegevensmodel (FDM) maken {#create-form-data-model}

<!--When you install the [!DNL Experience Manager Forms] package, a form data model, **[!DNL Microsoft Dynamics] FDM**, is deployed on your [!DNL Experience Manager] instance. By default, the Form Data Model uses [!DNL Microsoft Dynamics] service configured in the MS Dynamics OData Cloud Service (OData Service) as its data source.

On opening the Form Data Model for the first time, it connects to the configured [!DNL Microsoft Dynamics] service and fetches entities from your [!DNL Microsoft Dynamics] instance. The "contact" and "lead" entities from [!DNL Microsoft Dynamics] are already added in the form data model.

To review the form data model, go to **[!UICONTROL Form Data Model egrations]**. Select **[!DNL Microsoft Dynamics] FDM** and click **[!UICONTROL Edit]** to open the Form Data Model in edit mode. Alternatively, you can open the Form Data Model directly from the following URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`
 Form Data Model 
![default-fdm-1](assets/default-fdm-1.png)-->

Nadat u de MS Dynamics OData-cloudservice hebt geconfigureerd, kunt u de service gebruiken tijdens het maken van een FDM-model (Form Data Model). Voor meer informatie, zie [ het model van vormgegevens (FDM) ](create-form-data-models.md) creëren.

Vervolgens kunt u een adaptief formulier-gebaseerd formuliergegevensmodel (FDM) maken en dit gebruiken in verschillende gebruiksgevallen van adaptieve formulieren, zoals:

* Aangepast formulier vooraf invullen door informatie op te vragen van [!DNL Microsoft Dynamics] -entiteiten en -services
* [!DNL Microsoft Dynamics] serverbewerkingen aanroepen die met behulp van adaptieve formulierregels zijn gedefinieerd in een formuliergegevensmodel (FDM)
* Verzonden formuliergegevens naar [!DNL Microsoft Dynamics] -entiteiten schrijven

<!--It is recommended to create a copy of the Form Data Model provided with the [!DNL Experience Manager Forms] package and configure data models and services to suit your requirements. It will ensure that any future updates to the package do not override your form data model.-->

U kunt [ vormen het Model van Gegevens van de Vorm verzendt Actie ](/help/forms/using-form-data-model.md) voor een AanpassingsVorm om gegevens naar Microsoft Dynamics OData te verzenden.

Voor meer informatie over het creëren van en het gebruiken van het Model van de Gegevens van de Vorm (FDM) in bedrijfswerkschema&#39;s, zie {de Integratie van 0} Gegevens ](data-integration.md).[

## Verwante artikelen

{{af-submit-action}}
