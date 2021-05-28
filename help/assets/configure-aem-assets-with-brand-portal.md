---
title: AEM Assets configureren als een [!DNL Cloud Service] met Brand Portal
description: AEM Assets configureren met Brand Portal.
contentOwner: Vishabh Gupta
feature: Brand Portal,Asset Distribution,Configuration
role: Administrator
exl-id: 078e522f-bcd8-4734-95db-ddc8772de785
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '2268'
ht-degree: 12%

---

# AEM Assets configureren als een [!DNL Cloud Service] met Brand Portal {#configure-aem-assets-with-brand-portal}

Als u Adobe Experience Manager Assets Brand Portal configureert, kunt u goedgekeurde merkmiddelen van Adobe Experience Manager Assets publiceren als een [!DNL Cloud Service]-exemplaar naar Brand Portal en deze verspreiden onder de Brand Portal-gebruikers.

## Brand Portal activeren met Cloud Manager {#activate-brand-portal}

De gebruiker van de Manager van de Wolk activeert Brand Portal voor een AEM Assets als [!DNL Cloud Service] instantie. De activeringsworkflow maakt de vereiste configuraties (machtigingstoken, IMS-configuratie en Brand Portal-cloudservice) op de achtergrond en geeft de status van de Brand Portal-huurder in Cloud Manager weer. Als u Brand Portal activeert, kunnen AEM Assets-gebruikers elementen publiceren naar Brand Portal en deze verspreiden onder Brand Portal-gebruikers.

**Vereisten**

U hebt het volgende nodig om Brand Portal op uw AEM Assets te activeren als een [!DNL Cloud Service]-instantie:

* Een in werking gestelde AEM Assets als [!DNL Cloud Service] instantie.
* Een gebruiker die toegang heeft tot Cloud Manager en die is toegewezen aan profielen van het product van Cloud Manager. Zie [Cloud Manager openen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#accessing-cloud-manager) voor meer informatie.

>[!NOTE]
>
>Een AEM Assets als een [!DNL Cloud Service] instantie is gerechtigd om met slechts één huurder van Brand Portal te verbinden. U kunt meerdere omgevingen (ontwikkeling, productie en werkgebied) voor uw AEM Assets hebben als een [!DNL Cloud Service]-instantie, waarbij Brand Portal op één omgeving wordt geactiveerd.

**Stappen om Brand Portal te activeren**

U kunt Brand Portal activeren terwijl u de omgevingen voor uw AEM Assets maakt als een [!DNL Cloud Service]-exemplaar of afzonderlijk. Laten we ervan uitgaan dat de omgevingen al zijn gemaakt en dat u nu Brand Portal moet activeren.

1. Meld u aan bij Adobe Cloud Manager en navigeer naar **[!UICONTROL Environments]**.

   Op de pagina **[!UICONTROL Environments]** wordt de lijst met alle bestaande omgevingen weergegeven.

1. Selecteer de omgevingen (een voor een) in de lijst om de omgevingsdetails weer te geven.

   Brand Portal heeft recht op een van de beschikbare omgevingen en wordt weergegeven onder **[!UICONTROL Environment Information]**.

   Wanneer u de omgeving hebt gevonden die aan Brand Portal is gekoppeld, klikt u op de knop **[!UICONTROL Activate Brand Portal]** om de activeringsworkflow te starten.

   ![Brand Portal activeren](assets/create-environment4.png)

1. Het duurt slechts een paar minuten om de Brand Portal-gebruiker te activeren, aangezien de activeringsworkflow de vereiste configuraties op de achtergrond maakt. Zodra de Brand Portal-huurder is geactiveerd, verandert de status in Geactiveerd.

   ![Status weergeven](assets/create-environment5.png)


>[!NOTE]
>
>Brand Portal moet op dezelfde IMS org als de AEM Assets worden geactiveerd als een [!DNL Cloud Service]-instantie.
>
>Als u een bestaande Brand Portal wolkenconfiguratie ([manueel gevormd gebruikend de Console van de Ontwikkelaar van de Adobe](#manual-configuration)) voor IMS (org1-bestaand) hebt en uw AEM Assets aangezien een [!DNL Cloud Service] instantie voor een andere IMS org (org2-nieuw) wordt gevormd, stelt het activeren van Brand Portal van de Manager van de Wolk Brand Portal IMS org aan `org2-new` terug. Hoewel de handmatig geconfigureerde cloudconfiguratie op `org1-existing` zichtbaar is in de AEM Assets-ontwerpinstantie, maar niet meer wordt gebruikt na het activeren van Brand Portal vanuit Cloud Manager.
>
>Als de bestaande Brand Portal-cloudconfiguratie en AEM Assets als een [!DNL Cloud Service]-instantie dezelfde IMS org (org1) gebruiken, hoeft u Brand Portal alleen te activeren via Cloud Manager.

**Zie ook**:
* [Gebruikers en rollen toevoegen in AEM Assets als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/add-users-roles.html?lang=en#role-definitions)

* [Omgevingen beheren in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=en#adding-environments)


**Meld u aan bij uw Brand Portal-medewerker**:

Nadat u de Brand Portal-huurder hebt geactiveerd in Cloud Manager, kunt u zich vanuit Admin Console aanmelden bij Brand Portal of rechtstreeks de URL van de huurder gebruiken.

De standaard-URL van de Brand Portal-gebruiker is: `https://<tenant-id>.brand-portal.adobe.com/`.

Daar is de Tenant-id de IMS org.

Voer de volgende stappen uit als u niet zeker bent van de Brand Portal-URL:

1. Meld u aan bij [Admin Console](http://adminconsole.adobe.com/) en navigeer naar **[!UICONTROL Products]**.
1. Selecteer **[!UICONTROL Adobe Experience Manager Brand Portal – Brand Portal]** in het linkerspoor.
1. Klik op **[!UICONTROL Go to Brand Portal]** om Brand Portal rechtstreeks in de browser te openen.

   Of kopieer de URL van de Brand Portal-huurder van de koppeling **[!UICONTROL Go to Brand Portal]** en plak deze in uw browser om de Brand Portal-interface te openen.

   ![Toegang tot Brand Portal](assets/access-bp-on-cloud.png)


**Verbinding testen**

Voer de volgende stappen uit om de verbinding tussen uw AEM Assets als [!DNL Cloud Service] instantie en Brand Portal huurder te bevestigen:

1. Meld u aan bij AEM Assets.

1. Navigeer in het deelvenster **Gereedschappen** naar **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

   Een Brand Portal Distribution Agent (**[!UICONTROL bpdistributionagent0]**) wordt gecreeerd onder **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)


1. Klik **[!UICONTROL Publish to Brand Portal]** om de verdelingsagent te openen.

   U kunt de distributielijnen onder **[!UICONTROL Status]** tabel zien.

   Een distributieagent bevat twee wachtrijen:
   * **verwerkingswachtrij**: voor de distributie van assets naar Brand Portal.

   * **foutenwachtrij**: voor de assets waarvoor de distributie is mislukt.
   >[!NOTE]
   >
   >Het wordt aanbevolen om de fouten te controleren en de **foutenwachtrij** regelmatig te wissen.

   ![](assets/test-bpconfig3.png)

1. Als u de verbinding tussen AEM Assets als een [!DNL Cloud Service] en Brand Portal wilt controleren, klikt u op het pictogram **[!UICONTROL Test Connection]**.

   ![](assets/test-bpconfig4.png)

   Er verschijnt een bericht dat uw *testpakket is geleverd*.

   >[!NOTE]
   >
   >Schakel de distributieagent niet uit, want dit kan de distributie van de assets (die actief zijn in de wachtrij) doen mislukken.

Als u de verbinding tussen uw AEM Assets als een [!DNL Cloud Service]-exemplaar en Brand Portal-huurder wilt controleren, publiceert u een element van AEM Assets naar Brand Portal. Als de verbinding is gelukt, is het gepubliceerde element zichtbaar in de Brand Portal-interface.


U kunt nu het volgende doen:

* [Assets publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Elementen publiceren van Brand Portal naar AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=en)  - Asset Sourcing in Brand Portal
* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

Zie [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor meer informatie.

**Distributielogboeken**

U kunt de logboeken van de distributieagent voor de activa het publiceren werkschema controleren.

Laten we nu een middel van AEM Assets naar Brand Portal publiceren en de logboeken bekijken.

1. Voer de stappen uit (van 1 tot en met 4) zoals aangegeven in de sectie **Verbinding testen** en navigeer naar de pagina voor de distributieagent.
1. Klik **[!UICONTROL Logs]** om de verwerking en foutenlogboeken te bekijken.

   ![](assets/test-bpconfig5.png)

De distributieagent heeft de volgende logboeken geproduceerd:

* INFO: Het is een systeem-geproduceerd logboek dat op succesvolle configuratie van de verdelingsagent teweegbrengt.
* DSTRQ1 (aanvraag 1): geactiveerd tijdens testverbinding.

Bij het publiceren van de asset worden de volgende aanvraag- en antwoordlogboeken gegenereerd:

**Aanvraag van distributieagent**:

* DSTRQ2 (aanvraag 2): de aanvraag voor het publiceren van de asset wordt geactiveerd.
* DSTRK3 (verzoek 3): Het systeem activeert een andere aanvraag om de AEM Assets-map (waarin het element bestaat) te publiceren en repliceert de map in Brand Portal.

**Antwoord van distributieagent**:

* queue-bpdistributionagent0 (DSTRQ2): de asset wordt gepubliceerd naar Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): Het systeem dupliceert de AEM Assets-map (die het element bevat) in Brand Portal.

In het bovenstaande voorbeeld worden een aanvullende aanvraag en een aanvullend antwoord geactiveerd. Het systeem kan de bovenliggende map (Pad toevoegen) niet vinden in Brand Portal omdat het element voor de eerste keer is gepubliceerd. Daarom heeft het een extra aanvraag gestart om een bovenliggende map met dezelfde naam te maken in Brand Portal waar het element wordt gepubliceerd.

>[!NOTE]
>
>Er wordt een extra aanvraag gegenereerd als de bovenliggende map niet bestaat in Brand Portal of is gewijzigd in AEM Assets.

Samen met de automatiseringswerkstroom om Brand Portal op AEM Assets als [!DNL Cloud Service] te activeren, bestaat er een andere methode om AEM Assets als [!DNL Cloud Service] met Brand Portal manueel te vormen gebruikend de Console van de Ontwikkelaar van de Adobe die niet meer wordt geadviseerd.

>[!NOTE]
>
>Neem contact op met de Adobe-ondersteuning als u problemen ondervindt tijdens het activeren van uw Brand Portal-medewerker.

## Handmatige configuratie met Adobe Developer Console {#manual-configuration}

In de volgende sectie wordt beschreven hoe u AEM Assets handmatig kunt configureren als een [!DNL Cloud Service] met Brand Portal met behulp van Adobe Developer Console.

Eerder, werd AEM Assets als [!DNL Cloud Service] manueel gevormd met Brand Portal via de Console van de Ontwikkelaar van de Adobe, die een Adobe Identity Management Services (IMS) accountteken voor toestemming van de huurder van Brand Portal koopt. Voor dit programma zijn configuraties vereist in zowel AEM Assets als Adobe Developer Console.

1. In AEM Assets maakt u een IMS-account en genereert u een openbare sleutel (certificaat).
1. In de Console van de Ontwikkelaar van Adobe, creeer een project voor uw huurder van Brand Portal (organisatie).
1. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening tot stand te brengen.
1. Krijg de geloofsbrieven van de de dienstrekening en JSON Web Token (JWT) nuttige ladingsinformatie.
1. In AEM Assets configureert u de IMS-account met de gegevens van de serviceaccount en de JWT-payload.
1. In AEM Assets configureert u de Brand Portal-cloudservice met behulp van het IMS-account en het Brand Portal-eindpunt (organisatie-URL).
1. Test uw configuratie door middelen van AEM Assets aan Brand Portal te publiceren.

>[!NOTE]
>
>Een AEM Assets als een [!DNL Cloud Service] instantie moet slechts met één Brand Portal huurder worden gevormd.

**Vereisten**

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een in werking gestelde AEM Assets als [!DNL Cloud Service] instantie
* URL Brand Portal-gebruiker
* Een gebruiker met systeembeheerdersbevoegdheden op de IMS-organisatie van de Brand Portal-tenant

## Configuratie maken {#create-new-configuration}

Voer de volgende stappen in de opgegeven reeks uit om AEM Assets met Brand Portal te configureren.

1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)
1. [IMS-account configureren](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)

### IMS-configuratie maken {#create-ims-configuration}

De configuratie IMS verifieert uw AEM Assets als instantie [!DNL Cloud Service] met de huurder van Brand Portal.

De IMS-configuratie omvat twee stappen:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [IMS-account configureren](#create-ims-account-configuration)

### Openbaar certificaat verkrijgen {#public-certificate}

Met de openbare sleutel (certificaat) wordt uw profiel geverifieerd in de Adobe Developer Console.

1. Meld u aan bij AEM Assets.
1. Navigeer in het deelvenster **Gereedschappen** naar **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.
1. Klik op **[!UICONTROL Create]** op de pagina Adobe IMS-configuraties. Het zal aan de **[!UICONTROL Adobe IMS Technical Account Configuration]** pagina opnieuw richten. Standaard wordt het tabblad **Certificaat** geopend.
1. Selecteer **[!UICONTROL Adobe Brand Portal]** in **[!UICONTROL Cloud Solution]** dropdown lijst.
1. Selecteer het selectievakje **[!UICONTROL Create new certificate]** en geef een **alias** op voor de openbare sleutel. De alias fungeert als naam voor de openbare sleutel.
1. Klik op **[!UICONTROL Create certificate]**. Klik vervolgens op **[!UICONTROL OK]** om de openbare sleutel te genereren.

   ![Create Certificate](assets/ims-config2.png)

1. Klik op het pictogram **[!UICONTROL Download Public Key]** en sla het bestand met de openbare sleutel (CRT) op uw computer op.

   De openbare sleutel wordt later gebruikt om API voor uw Brand Portal huurder te vormen en de geloofsbrieven van de de dienstrekening in de Console van de Ontwikkelaar van Adobe te produceren.

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   Op het tabblad **Account** wordt een Adobe IMS-account gemaakt waarvoor de referenties van de serviceaccount zijn vereist die in de Adobe Developer Console zijn gegenereerd. Laat deze pagina voorlopig open.

   Open een nieuw lusje en [creeer een verbinding van de de dienstrekening (JWT) in de Console van de Ontwikkelaar van Adobe ](#createnewintegration) om de geloofsbrieven en JWT lading voor het vormen van de rekening te krijgen IMS.

### Verbinding voor serviceaccount (JWT) maken {#createnewintegration}

In de Console van de Ontwikkelaar van Adobe, worden de projecten en APIs gevormd op het niveau van de huurder van Brand Portal (organisatie). Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. Als u AEM Assets wilt configureren met Brand Portal, moet u een openbare sleutel (certificaat) genereren in AEM Assets en referenties maken in de Adobe Developer Console door de openbare sleutel te uploaden. Deze gegevens zijn vereist om de IMS-account in AEM Assets te configureren. Zodra de IMS-account is geconfigureerd, kunt u de Brand Portal-cloudservice in AEM Assets configureren.

Voer de volgende stappen uit om de geloofsbrieven van de de dienstrekening en lading van JWT te produceren:

1. Meld u aan bij de Adobe Developer Console met systeembeheerdersrechten voor de IMS-organisatie (Brand Portal-huurder). De standaard-URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Zorg ervoor dat u de juiste IMS-organisatie (Brand Portal-huurder) hebt geselecteerd in de vervolgkeuzelijst (organisatie) in de rechterbovenhoek.

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klik **[!UICONTROL Edit project]** om **[!UICONTROL Project Title]** en **[!UICONTROL Description]** bij te werken, en **[!UICONTROL Save]** te klikken.

1. Klik op het tabblad **[!UICONTROL Project overview]** op **[!UICONTROL Add API]**.

1. Selecteer **[!UICONTROL Add an API window]** in **[!UICONTROL AEM Brand Portal]** en klik **[!UICONTROL Next]**.

   Zorg ervoor dat u toegang hebt tot de AEM Brand Portal-service.

1. Klik in het venster **[!UICONTROL Configure API]** op **[!UICONTROL Upload your public key]**. Klik vervolgens op **[!UICONTROL Select a File]** en upload de openbare sleutel (.crt-bestand) die u hebt gedownload in de sectie [public certificate](#public-certificate).

   Klik op **[!UICONTROL Next]**.

   ![Openbare sleutel uploaden](assets/service-account3.png)

1. Verifieer de openbare sleutel en klik **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Assets Brand Portal]** als het standaardproductprofiel en klik **[!UICONTROL Save configured API]**.

   <!-- 
   In Brand Portal, a default profile is created for each organization. The Product Profiles are created in admin console for assigning users to groups (based on the roles and permissions). For configuration with Brand Portal, the OAuth token is created at organization level. Therefore, you must configure the default Product Profile for your organization. 
   -->

   ![Productprofiel selecteren](assets/service-account4.png)

1. Nadat de API is geconfigureerd, wordt u omgeleid naar de API-overzichtspagina. Klik in de linkernavigatie onder **[!UICONTROL Credentials]** op de optie **[!UICONTROL Service Account (JWT)]**.

   >[!NOTE]
   >
   >U kunt de geloofsbrieven bekijken en acties uitvoeren zoals produceren JWT tokens, exemplaar credentiedetails, terugwinnen cliëntgeheim, etc.

1. Kopieer op het tabblad **[!UICONTROL Client Credentials]** de **[!UICONTROL client ID]**.

   Klik **[!UICONTROL Retrieve Client Secret]** en kopieer **[!UICONTROL client secret]**.

   ![Servicerekeningen](assets/service-account5.png)

1. Navigeer naar het tabblad **[!UICONTROL Generate JWT]** en kopieer de informatie **[!UICONTROL JWT Payload]**.

U kunt nu de client-id (API-sleutel), het clientgeheim en de JWT-payload gebruiken om de IMS-account](#create-ims-account-configuration) in AEM Assets te configureren.[

<!--
1. Click **[!UICONTROL Create Integration]**.

1. Select **[!UICONTROL Access an API]**, and click **[!UICONTROL Continue]**.

   ![Create New Integration](assets/create-new-integration1.png)

1. Create a new integration page opens. 
   
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

   The API Key, Client Secret key, and JWT payload information will be used to create IMS account configuration.

-->

### IMS-account {#create-ims-account-configuration} configureren

Controleer of u de volgende stappen hebt uitgevoerd:

* [Openbaar certificaat verkrijgen](#public-certificate)
* [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)

Voer de volgende stappen uit om de IMS-account te configureren.

1. Open de Configuratie IMS en navigeer aan **[!UICONTROL Account]** tabel. U hield de pagina open terwijl [het openbare certificaat verkrijgen](#public-certificate).

1. Geef een **[!UICONTROL Title]** op voor het IMS-account.

   Geef in het veld **[!UICONTROL Authorization Server]** de URL op: [https://ims-na1.adobelogin.com/](https://ims-na1.adobelogin.com/)

   Geef de client-id op in het veld **[!UICONTROL API key]**, **[!UICONTROL Client Secret]** en **[!UICONTROL Payload]** (JWT-payload) die u hebt gekopieerd tijdens het maken van de JWT-verbinding (Service Account)](#createnewintegration).[

   Klik op **[!UICONTROL Create]**.

   De IMS-account is geconfigureerd.

   ![IMS Account configuration](assets/create-new-integration6.png)


1. Selecteer de IMS-accountconfiguratie en klik op **[!UICONTROL Check Health]**.

   Klik **[!UICONTROL Check]** in de dialoogdoos. Bij succesvolle configuratie, lijkt een bericht dat *Token met succes* wordt teruggewonnen.

   ![](assets/create-new-integration5.png)

>[!CAUTION]
>
>U kunt slechts één IMS-configuratie hebben.
>
>Zorg ervoor dat de IMS-configuratie slaagt voor de statuscontrole. Als de configuratie niet slaagt voor de statuscontrole, is deze ongeldig. U moet deze dan verwijderen en een nieuwe, geldige configuratie maken.

### Cloudservice configureren {#configure-the-cloud-service}

Voer de volgende stappen uit om de Brand Portal-cloudservice te configureren:

1. Meld u aan bij AEM Assets.

1. Navigeer in het deelvenster **Gereedschappen** naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op **[!UICONTROL Create]** op de pagina Brand Portal Configurations.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de IMS-configuratie die u hebt gemaakt tijdens het configureren van de IMS-account](#create-ims-account-configuration).[

   Geef in het veld **[!UICONTROL Service URL]** de URL van de Brand Portal-huurder (organisatie) op.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save & Close]**. De cloudconfiguratie wordt gemaakt.

   Uw AEM Assets als [!DNL Cloud Service] instantie wordt nu gevormd met de huurder van Brand Portal.

U kunt de configuratie nu testen door de distributieagent te controleren en elementen naar Brand Portal te publiceren.

<!--
### Test configuration {#test-configuration}

Perform the following steps to validate the configuration:

1. Log in to AEM Assets.

1. From the **Tools** panel, navigate to **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

    ![](assets/test-bpconfig1.png)

   A Brand Portal distribution agent (**[!UICONTROL bpdistributionagent0]**) is created under **[!UICONTROL Publish to Brand Portal]**.

   ![](assets/test-bpconfig2.png)


1. Click **[!UICONTROL Publish to Brand Portal]** to open the distribution agent. 

   You can see the distribution queues under the **[!UICONTROL Status]** tab. 
   
   A distribution agent contains two queues: 
   * **processing-queue**: for the distribution of assets to Brand Portal. 

   * **error-queue**: for the assets where distribution has failed. 
   
   >[!NOTE]
   >
   >It is recommended to review the failures and  clear the **error-queue** periodically.  

   ![](assets/test-bpconfig3.png)

1. To verify the connection between AEM Assets as a [!DNL Cloud Service] and Brand Portal, click on the **[!UICONTROL Test Connection]** icon.

   ![](assets/test-bpconfig4.png)

   A message appears that your *test package is successfully delivered*.

   >[!NOTE]
   >
   >Avoid disabling the distribution agent, as it can cause the distribution of the assets (running-in-queue) to fail.

You can now:

* [Publish assets from AEM Assets to Brand Portal](publish-to-brand-portal.md)
* [Publish folders from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Publish collections from AEM Assets to Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Publish assets from Brand Portal to AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=en) - Asset Sourcing in Brand Portal
* [Publish presets, schemas, and facets to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Publish tags to Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

See [Brand Portal documentation](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) for more information.

## Distribution logs {#distribution-logs}

You can monitor the distribution agent logs for the asset publishing workflow. 

For example, we have published an asset from AEM Assets to Brand Portal to validate the configuration. 

1. Follow the steps (from 1 to 4) as shown in the [Test Configuration](#test-configuration) section and navigate to the distribution agent page.
1. Click **[!UICONTROL Logs]** to view the processing and error logs.

   ![](assets/test-bpconfig5.png)

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
