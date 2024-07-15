---
title: Vorm AEM Assets als a [!DNL Cloud Service]  met Brand Portal
description: Leer hoe u AEM Assets kunt configureren met Brand Portal. Met de configuratie kunt u goedgekeurde merkmiddelen van een AEM naar Brand Portal publiceren en deze aan de Brand Portal-gebruikers distribueren.
contentOwner: AK
feature: Brand Portal, Asset Distribution, Configuration
role: Admin
exl-id: 078e522f-bcd8-4734-95db-ddc8772de785
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '1717'
ht-degree: 7%

---

# Experience Manager Assets configureren met Brand Portal {#configure-aem-assets-with-brand-portal}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/brandportal/configure-aem-assets-with-brand-portal.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Als u Adobe Experience Manager Assets Brand Portal configureert, kunt u goedgekeurde merkmiddelen van Adobe Experience Manager Assets publiceren als een [!DNL Cloud Service] -exemplaar naar Brand Portal en deze verspreiden onder de Brand Portal-gebruikers.

## Brand Portal activeren met Cloud Manager {#activate-brand-portal}

De Cloud Manager-gebruiker activeert Brand Portal voor een Experience Manager Assets als een [!DNL Cloud Service] -instantie. De activeringsworkflow maakt de vereiste configuraties (machtigingstoken, IMS-configuratie en Brand Portal-cloudservice) op de achtergrond en geeft de status van de Brand Portal-huurder in Cloud Manager weer. Als u Brand Portal activeert, kunnen Experience Manager Assets-gebruikers elementen publiceren naar Brand Portal en deze verspreiden onder Brand Portal-gebruikers.

**Eerste vereisten**

U hebt het volgende nodig om Brand Portal op uw Experience Manager Assets te activeren als een [!DNL Cloud Service] -instantie:

* Een Experience Manager Assets die wordt uitgevoerd als een [!DNL Cloud Service] -instantie.
* Een gebruiker die toegang heeft tot Cloud Manager, toegewezen aan profielen van het Cloud Manager-product. Zie [ toegang hebbend tot Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html#accessing-cloud-manager) voor meer informatie.

>[!NOTE]
>
>Een geconfigureerde productieomgeving is vereist voor een Experience Manager Assets als een [!DNL Cloud Service] -instantie om verbinding te maken met een Brand Portal-huurder.

**Stappen om Brand Portal** te activeren

U kunt Brand Portal activeren terwijl u de productieomgevingen voor uw Experience Manager Assets maakt als een [!DNL Cloud Service] -instantie of afzonderlijk. Laten we ervan uitgaan dat de omgeving al tot stand is gekomen en dat u nu Brand Portal moet activeren.

1. Meld u aan bij Adobe Cloud Manager en navigeer naar **[!UICONTROL Environments]** .

   Op de pagina **[!UICONTROL Environments]** wordt de lijst met alle bestaande omgevingen weergegeven.

1. Selecteer de omgevingen (een voor een) in de lijst om de omgevingsdetails weer te geven.

   Brand Portal heeft recht op een van de beschikbare omgevingen en wordt weergegeven onder **[!UICONTROL Environment Information]** .

   Wanneer u de omgeving hebt gevonden die aan Brand Portal is gekoppeld, klikt u op de knop **[!UICONTROL Activate Brand Portal]** om de activeringsworkflow te starten.

   ![ activeer Brand Portal ](assets/create-environment4.png)

1. Het duurt slechts een paar minuten om de Brand Portal-gebruiker te activeren, aangezien de activeringsworkflow de vereiste configuraties op de achtergrond maakt. Zodra de Brand Portal-huurder is geactiveerd, verandert de status in Geactiveerd.

   ![ Status van de Mening ](assets/create-environment5.png)


>[!NOTE]
>
>Brand Portal moet op dezelfde IMS org als de Experience Manager Assets worden geactiveerd als een [!DNL Cloud Service] -instantie.
>
>Als u een bestaande de wolkenconfiguratie van Brand Portal ([ hebt manueel gevormd gebruikend Adobe Developer Console ](#manual-configuration)) voor een (org1-bestaand) IMS en uw Experience Manager Assets als a [!DNL Cloud Service] instantie wordt gevormd voor een andere IMS org (org2-nieuw), die Brand Portal van Cloud Manager activeert stelt Brand Portal IMS org aan `org2-new` terug. Hoewel de handmatig geconfigureerde cloudconfiguratie op `org1-existing` zichtbaar is in de Experience Manager Assets-auteurinstantie, maar niet meer wordt gebruikt na het activeren van Brand Portal vanuit de Cloud Manager.
>
>Als de bestaande Brand Portal-cloudconfiguratie en Experience Manager Assets als een [!DNL Cloud Service] -instantie dezelfde IMS org (org1) gebruiken, hoeft u Brand Portal alleen vanuit de Cloud Manager te activeren.
>
>Wijzig geen automatisch gegenereerde instellingen.

**zie ook**:

* [ voegt gebruikers en rollen in as a Cloud Service Experience Manager Assets toe ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html)

* [ beheert milieu&#39;s in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html#adding-environments)


**Login aan uw huurder van Brand Portal**:

Nadat u de Brand Portal-huurder in Cloud Manager hebt geactiveerd, kunt u zich vanuit de Admin Console aanmelden bij Brand Portal of rechtstreeks de URL van de huurder gebruiken.

De standaard-URL van de Brand Portal-gebruiker is: `https://<tenant-id>.brand-portal.adobe.com/` .

Daar is de Tenant-id de IMS org.


Voer de volgende stappen uit als u niet zeker bent van de Brand Portal-URL:

1. Login aan [ Admin Console ](https://adminconsole.adobe.com/) en navigeer aan **[!UICONTROL Products]**.
1. Selecteer **[!UICONTROL Adobe Experience Manager Brand Portal – Brand Portal]** in het linkerdeelvenster.
1. Klik op **[!UICONTROL Go to Brand Portal]** om Brand Portal rechtstreeks in de browser te openen.

   U kunt ook de URL van de Brand Portal-huurder kopiëren van de koppeling **[!UICONTROL Go to Brand Portal]** en deze plakken in uw browser om de Brand Portal-interface te openen.

   ![ Toegang Brand Portal ](assets/access-bp-on-cloud.png)


**Verbinding van de Test**

Voer de volgende stappen uit om de verbinding tussen uw Experience Manager Assets als een [!DNL Cloud Service] -instantie en Brand Portal-huurder te valideren:

1. Aanmelden bij Experience Manager Assets.

1. Van het **paneel van Hulpmiddelen**, navigeer aan **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![ navigeer aan de distributieoptie ](assets/test-bpconfig1.png)

   Een Brand Portal Distribution Agent (**[!UICONTROL bpdistributionagent0]**) wordt gecreeerd onder **[!UICONTROL Publish to Brand Portal]**.

   ![ creeer verdelingsagent ](assets/test-bpconfig2.png)

1. Klik op **[!UICONTROL Publish to Brand Portal]** om de distributieagent te openen.

   U kunt de distributielijnen onder het **[!UICONTROL Status]** lusje zien.

   Een distributieagent bevat twee wachtrijen:
   * **verwerkingswachtrij**: voor de distributie van assets naar Brand Portal.

   * **foutenwachtrij**: voor de assets waarvoor de distributie is mislukt.

   >[!NOTE]
   >
   >Het wordt aanbevolen om de fouten te controleren en de **foutenwachtrij** regelmatig te wissen.

   ![ rij van de Verwerking voor de distributie van activa ](assets/test-bpconfig3.png)

1. Klik op het pictogram **[!UICONTROL Test Connection]** om de verbinding tussen Experience Manager Assets als een [!DNL Cloud Service] en Brand Portal te controleren.

   ![ verifieer verbinding tussen AEM en Brand Portal ](assets/test-bpconfig4.png)

   Een bericht lijkt dat uw *testpakket met succes wordt geleverd*.

   >[!NOTE]
   >
   >Schakel de distributieagent niet uit, want dit kan de distributie van de assets (die actief zijn in de wachtrij) doen mislukken.

Als u de verbinding tussen uw Experience Manager Assets als een [!DNL Cloud Service] -instantie en Brand Portal-huurder wilt controleren, publiceert u een element van Experience Manager Assets naar Brand Portal. Als de verbinding is gelukt, is het gepubliceerde element zichtbaar in de Brand Portal-interface.


U kunt nu het volgende doen:

* [Publish-middelen van Experience Manager Assets naar Brand Portal](publish-to-brand-portal.md)
* [Publish-mappen van Experience Manager Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish-collecties van Experience Manager Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [ de activa van Publish van Brand Portal aan Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) - De Middelen van Activa in Brand Portal
* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

Zie {de documentatie van 0} Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor meer informatie.[

**Logboeken van de Distributie**

U kunt de logboeken van de distributieagent voor de activa het publiceren werkschema controleren.

Laten we nu een middel van Experience Manager Assets naar Brand Portal publiceren en de logboeken bekijken.

1. Volg de stappen (van 1 tot 4) zoals aangetoond in de **sectie van de Verbinding van de Test** en navigeer aan de pagina van de distributieagent.
1. Klik op **[!UICONTROL Logs]** om de logbestanden met de verwerking en fouten weer te geven.

   ![ Logboeken van de Verwerking en van de fout ](assets/test-bpconfig5.png)

De distributieagent heeft de volgende logboeken geproduceerd:

* INFO: Het is een systeem-geproduceerd logboek dat op succesvolle configuratie van de verdelingsagent teweegbrengt.
* DSTRQ1 (aanvraag 1): geactiveerd tijdens testverbinding.

Bij het publiceren van de asset worden de volgende aanvraag- en antwoordlogboeken gegenereerd:

**Aanvraag van distributieagent**:

* DSTRQ2 (aanvraag 2): de aanvraag voor het publiceren van de asset wordt geactiveerd.
* DSTRQ3 (verzoek 3): Het systeem activeert een andere aanvraag om de Experience Manager Assets-map (waarin het element bestaat) te publiceren en repliceert de map in Brand Portal.

**Antwoord van distributieagent**:

* queue-bpdistributionagent0 (DSTRQ2): de asset wordt gepubliceerd naar Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): het systeem dupliceert de Experience Manager Assets-map (die het element bevat) in Brand Portal.

In het bovenstaande voorbeeld worden een aanvullende aanvraag en een aanvullend antwoord geactiveerd. Het systeem kan de bovenliggende map (Pad toevoegen) niet vinden in Brand Portal omdat het element voor de eerste keer is gepubliceerd. Daarom heeft het een extra aanvraag gestart om een bovenliggende map met dezelfde naam te maken in Brand Portal waar het element wordt gepubliceerd.

>[!NOTE]
>
>Er wordt een extra aanvraag gegenereerd als de bovenliggende map niet bestaat in Brand Portal of is gewijzigd in Experience Manager Assets.

Naast de automatiseringsworkflow om Brand Portal op Experience Manager Assets als een [!DNL Cloud Service] te activeren, bestaat er een andere methode om Experience Manager Assets handmatig als een [!DNL Cloud Service] met Brand Portal te configureren met Adobe Developer Console. Dit wordt niet meer aanbevolen.

>[!NOTE]
>
>Neem contact op met de Klantenondersteuning als u problemen ondervindt tijdens het activeren van uw Brand Portal-medewerker.

## Handmatige configuratie met Adobe Developer Console {#manual-configuration}

>[!NOTE]
>
> U kunt vanaf juni 2024 geen nieuwe JWT-referenties maken. Voortaan worden alleen OAuth-referenties gemaakt.
> Zie meer [ creërend een configuratie OAuth ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration:~:text=For%20example%3A-,Creating%20an%20OAuth%20configuration,-To%20create%20a).

In de volgende sectie wordt beschreven hoe u Experience Manager Assets handmatig kunt configureren als een [!DNL Cloud Service] met Brand Portal met Adobe Developer Console.

Eerder, werd Experience Manager Assets als [!DNL Cloud Service] manueel gevormd met Brand Portal via Adobe Developer Console, die een de rekeningsteken van Identity Management van de Adobe (IMS) voor vergunning van de huurder van Brand Portal koopt. Er zijn configuraties voor nodig, zowel in Experience Manager Assets als in Adobe Developer Console.

<!--1. In Experience Manager Assets, create an IMS account and generate a public key (certificate).-->
<!--1. Under the project, configure an API using the public key to create a service account connection.
1. Get the service account credentials and JSON Web Token (JWT) payload information.
1. In Experience Manager Assets, configure the IMS account using the service account credentials and JWT payload.-->
1. Maak in Adobe Developer Console een project voor uw Brand Portal-huurder (organisatie).
1. In Experience Manager Assets configureert u de Brand Portal-cloudservice met behulp van het IMS-account en het Brand Portal-eindpunt (organisatie-URL).
1. Test uw configuratie door middelen van Experience Manager Assets aan Brand Portal te publiceren.

>[!NOTE]
>
>Een Experience Manager Assets als een [!DNL Cloud Service] -instantie mag slechts met één Brand Portal-huurder worden geconfigureerd.

**Eerste vereisten**

U hebt het volgende nodig om Experience Manager Assets met Brand Portal te configureren:

* Een Experience Manager Assets uitvoeren als een [!DNL Cloud Service] -instantie
* URL Brand Portal-gebruiker
* Een gebruiker met systeembeheerdersrechten voor de IMS-organisatie van de Brand Portal-huurder

## Configuratie maken {#create-new-configuration}

Voer de volgende stappen in de opgegeven reeks uit om Experience Manager Assets met Brand Portal te configureren.

1. [De OAuth-referenties configureren in de Adobe Developer Console](#config-oauth)
1. [Een nieuwe Adobe IMS-integratie maken met OAuth](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-cloud-service)
   <!--1. [Obtain public certificate](#public-certificate)-->
<!--1. [Create service account (JWT) connection](#createnewintegration) 
1. [Configure IMS account](#create-ims-account-configuration)-->

<!--
### Create IMS configuration {#create-ims-configuration}

The IMS configuration authenticates your Experience Manager Assets as a [!DNL Cloud Service] instance with the Brand Portal tenant. 

IMS configuration includes two steps:

* [Obtain public certificate](#public-certificate) 
* [Configure IMS account](#create-ims-account-configuration)
-->
<!--

### Obtain public certificate {#public-certificate}

The public key (certificate) authenticates your profile on Adobe Developer Console.

1. Login to Experience Manager Assets.
1. From the **Tools** panel, navigate to **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. In Adobe IMS Configurations page, click **[!UICONTROL Create]**. It will redirect to the **[!UICONTROL Adobe IMS Technical Account Configuration]** page. By default, the **Certificate** tab opens.
1. Select **[!UICONTROL Adobe Brand Portal]** in the **[!UICONTROL Cloud Solution]** drop-down list.  
1. Select the **[!UICONTROL Create new certificate]** check box and specify an **alias** for the public key. The alias serves as name of the public key. 
1. Click **[!UICONTROL Create certificate]**. Then, click **[!UICONTROL OK]** to generate the public key.

   ![Create Certificate](assets/ims-config2.png)

1. Click the **[!UICONTROL Download Public Key]** icon and save the public key (CRT) file on your machine.

   The public key is used later to configure API for your Brand Portal tenant and generate service account credentials in Adobe Developer Console.  

   ![Download Certificate](assets/ims-config3.png)

1. Click **[!UICONTROL Next]**.

    In the **Account** tab, Adobe IMS account is created which requires the service account credentials that are generated in Adobe Developer Console. Keep this page open for now.

    Open a new tab and [create a service account (JWT) connection in Adobe Developer Console](#createnewintegration) to get the credentials and JWT payload for configuring the IMS account. 
-->
<!--

### Create service account (JWT) connection {#createnewintegration}

In Adobe Developer Console, projects and APIs are configured at Brand Portal tenant (organization) level. Configuring an API creates a service account (JWT) connection. There are two methods to configure API, by generating a key pair (private and public keys) or by uploading a public key. To configure Experience Manager Assets with Brand Portal, you must generate a public key (certificate) in Experience Manager Assets and create credentials in Adobe Developer Console by uploading the public key. These credentials are required to configure the IMS account in Experience Manager Assets. Once the IMS account is configured, you can configure the Brand Portal cloud service in Experience Manager Assets.

Perform the following steps to generate the service account credentials and JWT payload:

1. Login to Adobe Developer Console with system administrator privileges on the IMS organization (Brand Portal tenant). The default URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Ensure that you have selected the correct IMS organization (Brand Portal tenant) from the drop-down (organization) list located at the upper-right corner.

1. Click **[!UICONTROL Create new project]**. A blank project with a system-generated name is created for your organization. 

   Click **[!UICONTROL Edit project]** to update the **[!UICONTROL Project Title]** and **[!UICONTROL Description]**, and click **[!UICONTROL Save]**.
   
1. In the **[!UICONTROL Project overview]** tab, click **[!UICONTROL Add API]**.

1. In the **[!UICONTROL Add an API window]**, select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Next]**. 

   Ensure that you have access to the Experience Manager Brand Portal service.

1. In the **[!UICONTROL Configure API]** window, click **[!UICONTROL Upload your public key]**. Then, click **[!UICONTROL Select a File]** and upload the public key (.crt file) that you have downloaded in the [obtain public certificate](#public-certificate) section. 

   Click **[!UICONTROL Next]**.

   ![Upload Public Key](assets/service-account3.png)

1. Verify the public key and click **[!UICONTROL Next]**.

1. Select **[!UICONTROL Assets Brand Portal]** as the default product profile and click **[!UICONTROL Save configured API]**. 

   ![Select Product Profile](assets/service-account4.png)

1. Once the API is configured, you are redirected to the API overview page. From the left navigation under **[!UICONTROL Credentials]**, click the **[!UICONTROL Service Account (JWT)]** option.

   >[!NOTE] 
   >
   >* You can view the credentials and perform actions such as generate JWT tokens, copy credential details, retrieve client secret, and so on.
   >* Currently, only the Adobe's Developer Console Service Account (JWT) credential type is supported. Do not use the `OAuth Server-to-Server` credential type until it is supported in mid-April. Read more at [JWT Credentials Deprecation in Adobe Developer Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/security/jwt-credentials-deprecation-in-adobe-developer-console.html).

1. From the **[!UICONTROL Client Credentials]** tab, copy the **[!UICONTROL client ID]**. 

   Click **[!UICONTROL Retrieve Client Secret]** and copy the **[!UICONTROL client secret]**.

   ![Service Account Credentials](assets/service-account5.png)

1. Navigate to the **[!UICONTROL Generate JWT]** tab and copy the **[!UICONTROL JWT Payload]** information. 

You can now use the client ID (API key), client secret, and JWT payload to [configure the IMS account](#create-ims-account-configuration) in Experience Manager Assets.
-->
<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create an integration page. 
   
   Select your organization from the drop-down list.

   In **[!UICONTROL Experience Cloud]**, Select **[!UICONTROL AEM Brand Portal]** and click **[!UICONTROL Continue]**. 

   If the Brand Portal option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Create Integration](assets/create-new-integration2.png)

1. Specify a name and description for the integration. Click **[!UICONTROL Select a File from your computer]** and upload the `AEM-Adobe-IMS.crt` file downloaded in the [obtain public certificates](#public-certificate) section.

1. Select the profile of your organization. 

   Or, select the default profile **[!UICONTROL Assets Brand Portal]** and click **[!UICONTROL Create Integration]**. The integration is created.

1. Click **[!UICONTROL Continue to integration details]** to view the integration information. 

   Copy the **[!UICONTROL API Key]** 
   
   Click **[!UICONTROL Retrieve Client Secret]** and copy the Client Secret key.

   ![API Key, Client Secret, and payload information of an integration](assets/create-new-integration3.png)

1. Navigate to **[!UICONTROL JWT]** tab, and copy the **[!UICONTROL JWT payload]**.

   The API Key, Client Secret key, and JWT payload information is used to create IMS account configuration.

-->

### De OAuth-referenties configureren in de Adobe Developer Console {#config-oauth}

[ vorm de geloofsbrieven OAuth in Adobe Developer Console ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#credentials-in-the-developer-console) en selecteer Brand Portal API.

### Nieuwe Adobe IMS-integratie maken met OAuth {#create-ims-account-configuration}

[ creeer een nieuwe Integratie van Adobe IMS gebruikend OAuth ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service#creating-oauth-configuration) en selecteer Brand Portal van de drop down onder de Oplossing van de Wolk.

<!--
Ensure that you have performed the following steps:

* [Obtain public certificate](#public-certificate)
* [Create service account (JWT) connection](#createnewintegration)
-->

<!--1. Open the IMS Configuration and navigate to the **[!UICONTROL Account]** tab. Keep the page open while [obtaining the public certificate](#public-certificate).

1. Specify a **[!UICONTROL Title]** for the IMS account.

   In the **[!UICONTROL Authorization Server]** field, specify the URL: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)  
-->
<!--
1. Complete the configuration based on details from the [Developer Console](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation/). Click **[!UICONTROL Create]**.
-->
<!--Specify client ID in the **[!UICONTROL API key]** field, **[!UICONTROL Client Secret]**, and **[!UICONTROL Payload]** (JWT payload) that you have copied while [creating the service account (JWT) connection](#createnewintegration).

   The IMS account is configured. 

   ![IMS Account configuration](assets/create-new-integration6.png)

 <!--  
1. Select the IMS account configuration and click **[!UICONTROL Check Health]**.

   Click **[!UICONTROL Check]** in the dialog box. On successful configuration, a message appears that the *Token is retrieved successfully*.

   ![Adobe IMS Configurations Check Health.](assets/create-new-integration5.png)
-->
<!--
>[!CAUTION]
>
>You must have only one IMS configuration.
>
>Ensure that the IMS configuration passes the health check. If the configuration does not pass the health check, it is invalid. You must delete it and create another valid configuration.
-->

### Cloudservice configureren {#configure-cloud-service}

Voer de volgende stappen uit om de Brand Portal-cloudservice te configureren:

1. Aanmelden bij Experience Manager Assets.

1. Van het **paneel van Hulpmiddelen**, navigeer aan **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op **[!UICONTROL Create]** op de pagina Brand Portal Configurations.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de configuratie IMS die u terwijl [ vormend de rekening IMS ](#create-ims-account-configuration) creeerde.

   Geef in het veld **[!UICONTROL Service URL]** de URL van de Brand Portal-huurder (organisatie) op.

   ![ de dialoogdoos van de Configuratie van Brand Portal.](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save & Close]**. De cloudconfiguratie wordt gemaakt.

   Uw Experience Manager Assets als een [!DNL Cloud Service] -instantie is nu geconfigureerd met de Brand Portal-huurder.

U kunt de configuratie nu testen door de distributieagent te controleren en elementen naar Brand Portal te publiceren.

**Lijst van gewenste personen Eind IPs in SPS als veilige voorproef toegelaten**
Als het gebruiken van Dynamic Media-Scene7 met [ veilige voorproef ](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=en) voor een bedrijf werd toegelaten, dan wordt het geadviseerd dat de bedrijfbeheerder van Scene7 [ lijst van gewenste personen openbaar uitgang IPs ](#https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=en#testing-the-secure-testing-service) voor respectieve gebieden gebruikend SPS (het Uitgeven van Scene7 Systeem) flits UI.
De IP&#39;s van de uitgang zijn als volgt:

| **Gebied** | **IP van de Eis** |
|--- |--- |
| NA | 130.248.160.68, 20.94.203.130 |
| EMEA | 51.132.146.75, 130.248.244.202, 130.248.244.203, 130.248.244.204, 130.2 48.244.210, 130.248.244.211, 13.248.244.212 |
| APAC | 63 140 44 54 |

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Login to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![test-bpconfig1](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![test-bpconfig2](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![test-bpconfig3](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click the **[!UICONTROL Test Connection]** icon.

   ![test-bpconfig4](assets/test-bpconfig4.png)

   A message appears that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Avoid disabling the distribution agent, as it can cause the distribution of the assets (running-in-queue) to fail.

You can now:

* [Publish assets from AEM Assets to Brand Portal](publish-to-brand-portal.md)
* [Publish folders from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish collections from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html) - Asset Sourcing in Brand Portal
* [Publish presets, schemas, and facets to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publish tags to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

See [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) for more information.

## Distribution logs {#distribution-logs}

You can monitor the distribution agent logs for the asset publishing workflow. 

For example, we have published an asset from AEM Assets to Brand Portal to validate the configuration. 

1. Follow the steps (from 1 to 4) as shown in the [Test Configuration](#test-configuration) section and navigate to the distribution agent page.
1. Click **[!UICONTROL Logs]** to view the processing and error logs.

   ![ctest-bpconfig4](assets/ctest-bpconfig4.png)

The distribution agent has generated the following logs:

* INFO: This is a system-generated log that triggers on successful configuration of the distribution agent. 
* DSTRQ1 (Request 1): Triggers on test connection.

On publishing the asset, the following request and response logs are generated:

**Distribution agent request**:

* DSTRQ2 (Request 2): The asset publishing request is triggered.
* DSTRQ3 (Request 3): The system triggers another request to publish the AEM Assets folder (in which the asset exists) and replicates the folder in Brand Portal.

**Distribution agent response**:

* queue-bpdistributionagent0 (DSTRQ2): The asset is published to Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): The system replicates the AEM Assets folder (containing the asset) in Brand Portal.

In the above example, an additional request and response is triggered. The system could not find the parent folder (Add Path) in Brand Portal because the asset was published for the first time, therefore, it triggered an additional request to create a parent folder with the same name in Brand Portal where the asset is published.  

>[!NOTE]
>
>Additional request is generated in case the parent folder does not exist in Brand Portal or has been modified in AEM Assets. 
-->

<!--

## Additional information {#additional-information}

Go to `/system/console/slingmetrics` for statistics related to the distributed content:

1. **Counter metrics**
   * sling: `mac_sync_request_failure`
   * sling: `mac_sync_request_received`
   * sling: `mac_sync_request_success`

1. **Time metrics**
   * sling: `mac_sync_distribution_duration`
   * sling: `mac_sync_enqueue_package_duration`
   * sling: `mac_sync_setup_request_duration`

-->

<!--
   Comment Type: draft

   <li> </li>
   -->

<!--
   Comment Type: draft

   <li>Step text</li>
-->

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Publish Assets naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
