---
title: AEM Assets configureren als een [!DNL Cloud Service] met Brand Portal
description: AEM Assets configureren met Brand Portal.
contentOwner: Vishabh Gupta
translation-type: tm+mt
source-git-commit: bafb952cd984885e0f309b8a78a96ae48320b7df
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 20%

---


# AEM Assets configureren als een [!DNL Cloud Service] met Brand Portal {#configure-aem-assets-with-brand-portal}

Als u Adobe Experience Manager Assets Brand Portal configureert, kunt u goedgekeurde merkmiddelen van Adobe Experience Manager Assets publiceren als een [!DNL Cloud Service]-exemplaar naar Brand Portal en deze verspreiden onder de gebruikers van het Brand Portal.

**Configuratieworkflow**

AEM Assets als [!DNL Cloud Service] wordt gevormd met het Portaal van het Merk via de Console van de Ontwikkelaar van de Adobe, die een Adobe Identity Management Services (IMS) rekeningsteken voor vergunning van de Poorthuurder van het Merk aanschaft. Voor dit programma zijn configuraties vereist in zowel AEM Assets als Adobe Developer Console.

1. In AEM Assets maakt u een IMS-account en genereert u een openbare sleutel (certificaat).
1. In de Console van de Ontwikkelaar van Adobe, creeer een project voor uw Poorthuurder van het Merk (organisatie).
1. Onder het project, vorm API gebruikend de openbare sleutel om een verbinding van de de dienstrekening tot stand te brengen.
1. Krijg de geloofsbrieven van de de dienstrekening en JSON Web Token (JWT) nuttige ladingsinformatie.
1. In AEM Assets configureert u de IMS-account met de gegevens van de serviceaccount en de JWT-payload.
1. In AEM Assets configureert u de Brand Portal-cloudservice met behulp van het IMS-account en het Brand Portal-eindpunt (organisatie-URL).
1. Test uw configuratie door middel van het publiceren van middelen van AEM Assets naar Brand Portal.

>[!NOTE]
>
>Een AEM Assets als een [!DNL Cloud Service] instantie moet slechts met één merkportaalhuurder worden gevormd.

## Vereisten {#prerequisites}

U hebt het volgende nodig om AEM Assets te configureren met Brand Portal:

* Een in werking gestelde AEM Assets als [!DNL Cloud Service] instantie
* Een URL voor Poortgebruiker voor merken
* Een gebruiker met systeembeheerdersbevoegdheden op de IMS-organisatie van de Brand Portal-tenant

## Configuratie maken {#create-new-configuration}

Voer de volgende stappen in de opgegeven reeks uit om AEM Assets met Brand Portal te configureren.

1. [Openbaar certificaat verkrijgen](#public-certificate)
1. [Verbinding voor serviceaccount (JWT) maken](#createnewintegration)
1. [IMS-account configureren](#create-ims-account-configuration)
1. [Cloudservice configureren](#configure-the-cloud-service)
1. [Configuratie testen](#test-configuration)

### IMS-configuratie maken {#create-ims-configuration}

De configuratie IMS verklaart uw AEM Assets als instantie [!DNL Cloud Service] met de Poorthuurder van het Merk voor authentiek.

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

   De openbare sleutel zal later worden gebruikt om API voor uw Poorthuurder van het Merk te vormen en de geloofsbrieven van de de dienstrekening in de Console van de Ontwikkelaar van Adobe te produceren.

   ![Download Certificate](assets/ims-config3.png)

1. Klik op **[!UICONTROL Next]**.

   Op het tabblad **Account** wordt een Adobe IMS-account gemaakt waarvoor de referenties van de serviceaccount zijn vereist die in de Adobe Developer Console zijn gegenereerd. Laat deze pagina voorlopig open.

   Open een nieuw lusje en [creeer een verbinding van de de dienstrekening (JWT) in de Console van de Ontwikkelaar van Adobe ](#createnewintegration) om de geloofsbrieven en JWT lading voor het vormen van de rekening te krijgen IMS.

### Verbinding {#createnewintegration} maken voor serviceaccount (JWT)

In de Console van de Ontwikkelaar van Adobe, worden de projecten en APIs gevormd op het niveau van de huurder van het Portaal van het Merk (organisatie). Als u een API configureert, wordt een JWT-verbinding (Service Account) gemaakt. Er zijn twee methodes om API te vormen, door een zeer belangrijk paar (privé en openbare sleutels) te produceren of door een openbare sleutel te uploaden. Als u AEM Assets wilt configureren met Brand Portal, moet u een openbare sleutel (certificaat) genereren in AEM Assets en referenties maken in de Adobe Developer Console door de openbare sleutel te uploaden. Deze gegevens zijn vereist om de IMS-account in AEM Assets te configureren. Zodra de IMS-account is geconfigureerd, kunt u de Brand Portal-cloudservice in AEM Assets configureren.

Voer de volgende stappen uit om de geloofsbrieven van de de dienstrekening en lading van JWT te produceren:

1. Meld u aan bij de Adobe Developer Console met systeembeheerdersrechten voor de IMS-organisatie (Poortmedewerker). De standaard-URL is [https://www.adobe.com/go/devs_console_ui](https://www.adobe.com/go/devs_console_ui).


   >[!NOTE]
   >
   >Zorg ervoor dat u de juiste IMS-organisatie (Brand Portal-huurder) hebt geselecteerd in de vervolgkeuzelijst (organisatie) in de rechterbovenhoek.

1. Klik op **[!UICONTROL Create new project]**. Er wordt een leeg project met een door het systeem gegenereerde naam gemaakt voor uw organisatie.

   Klik **[!UICONTROL Edit project]** om **[!UICONTROL Project Title]** en **[!UICONTROL Description]** bij te werken, en **[!UICONTROL Save]** te klikken.

1. Klik op het tabblad **[!UICONTROL Project overview]** op **[!UICONTROL Add API]**.

1. Selecteer **[!UICONTROL Add an API window]** in **[!UICONTROL AEM Brand Portal]** en klik **[!UICONTROL Next]**.

   Zorg ervoor dat u toegang hebt tot de service AEM Brand Portal.

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

Voer de volgende stappen uit om de merkportalcloudservice te configureren:

1. Meld u aan bij AEM Assets.

1. Navigeer in het deelvenster **Gereedschappen** naar **[!UICONTROL Cloud Services]** > **[!UICONTROL AEM Brand Portal]**.

1. Klik op **[!UICONTROL Create]** op de pagina Poortconfiguraties voor merken.

1. Geef een **[!UICONTROL Title]** op voor de configuratie.

   Selecteer de IMS-configuratie die u hebt gemaakt tijdens het configureren van de IMS-account](#create-ims-account-configuration).[

   Geef in het veld **[!UICONTROL Service URL]** de URL van uw medewerker (organisatie) van het Brand Portal op.

   ![](assets/create-cloud-service.png)

1. Klik op **[!UICONTROL Save & Close]**. De cloudconfiguratie wordt gemaakt.

   Uw AEM Assets als [!DNL Cloud Service] instantie wordt nu gevormd met de Poorthuurder van het Merk.

### Configuratie testen {#test-configuration}

Voer de volgende stappen uit om de configuratie te valideren:

1. Meld u aan bij AEM Assets.

1. Navigeer in het deelvenster **Gereedschappen** naar **[!UICONTROL Deployment]** > **[!UICONTROL Distribution]**.

   ![](assets/test-bpconfig1.png)

   Een merkportal-distributieagent (**[!UICONTROL bpdistributionagent0]**) wordt gemaakt onder **[!UICONTROL Publish to Brand Portal]**.

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

1. Als u de verbinding tussen AEM Assets als [!DNL Cloud Service] en Brand Portal wilt controleren, klikt u op het pictogram **[!UICONTROL Test Connection]**.

   ![](assets/test-bpconfig4.png)

   Er verschijnt een bericht dat uw *testpakket is geleverd*.

   >[!NOTE]
   >
   >Schakel de distributieagent niet uit, want dit kan de distributie van de assets (die actief zijn in de wachtrij) doen mislukken.

U kunt nu het volgende doen:

* [Assets publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md)
* [Mappen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-folders-to-brand-portal)
* [Verzamelingen publiceren van AEM Assets naar Brand Portal](publish-to-brand-portal.md#publish-collections-to-brand-portal)
* [Middelen publiceren van Brand Portal naar AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/asset-sourcing-in-brand-portal/brand-portal-asset-sourcing.html?lang=en)  - Asset Sourcing in Brand Portal
* [Voorinstellingen, schema&#39;s en facetten publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/publish-schema-search-facets-presets.html)
* [Tags publiceren naar Brand Portal](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/publish/brand-portal-publish-tags.html)

Zie [Handelsversie](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/home.html) voor meer informatie.

## Distributielogboeken {#distribution-logs}

U kunt de logboeken van de distributieagent voor de activa het publiceren werkschema controleren.

We hebben bijvoorbeeld een middel van AEM Assets naar Brand Portal gepubliceerd om de configuratie te valideren.

1. Volg de stappen (van 1 tot 4) zoals aangetoond in [de sectie van de Configuratie van de Test](#test-configuration) en navigeer aan de pagina van de distributieagent.
1. Klik **[!UICONTROL Logs]** om de verwerking en foutenlogboeken te bekijken.

   ![](assets/test-bpconfig5.png)

De distributieagent heeft de volgende logboeken geproduceerd:

* INFO: Dit is een systeem-geproduceerd logboek dat op succesvolle configuratie van de verdelingsagent teweegbrengt.
* DSTRQ1 (aanvraag 1): geactiveerd tijdens testverbinding.

Bij het publiceren van de asset worden de volgende aanvraag- en antwoordlogboeken gegenereerd:

**Aanvraag van distributieagent**:

* DSTRQ2 (aanvraag 2): de aanvraag voor het publiceren van de asset wordt geactiveerd.
* DSTRK3 (verzoek 3): Het systeem activeert een andere aanvraag om de AEM Assets-map (waarin het element bestaat) te publiceren en repliceert de map in Brand Portal.

**Antwoord van distributieagent**:

* queue-bpdistributionagent0 (DSTRQ2): de asset wordt gepubliceerd naar Brand Portal.
* queue-bpdistributionagent0 (DSTRQ3): Het systeem dupliceert de AEM Assets-map (die het element bevat) in Brand Portal.

In het bovenstaande voorbeeld worden een aanvullende aanvraag en een aanvullend antwoord geactiveerd. Het systeem kan de bovenliggende map (Pad toevoegen) niet vinden in Brand Portal omdat het element voor het eerst is gepubliceerd. Daarom heeft het een extra verzoek geactiveerd om een bovenliggende map met dezelfde naam te maken in Brand Portal waar het element is gepubliceerd.

>[!NOTE]
>
>Er wordt een extra aanvraag gegenereerd als de bovenliggende map niet bestaat in Brand Portal of is gewijzigd in AEM Assets.

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
