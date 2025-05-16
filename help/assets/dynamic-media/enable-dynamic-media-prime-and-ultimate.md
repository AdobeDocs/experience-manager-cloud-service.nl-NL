---
title: Laat  [!DNL Dynamic Media]  Prime en Ultimate toe
description: Leer hoe te om  [!DNL Dynamic Media]  Prime en het dienstenaanbod van Ultimate toe te laten.
feature: Asset Management
role: User, Admin
exl-id: 0ee161f5-bf44-41f1-928e-c07574fd43cc
source-git-commit: 603602dc70f9d7cdf78b91b39e3b7ff5090a6bc0
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# [!DNL Dynamic Media] Prime en Ultimate inschakelen {#enable-dynamic-media-prime-and-ultimate}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b> Dynamische Media Prime en Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b> AEM Assets Ultimate </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b> integratie van AEM Assets met Edge Delivery Services </b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i> Nieuwe </i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b> Uitbreidbaarheid UI </b></a>
        </td>
        <td>
            <a href="/help/assets/search-best-practices.md"><b> Beste praktijken van het Onderzoek </b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b> Beste praktijken van Meta-gegevens </b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b> Content Hub </b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b> Dynamische Media met mogelijkheden OpenAPI </b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b> de ontwikkelaarsdocumentatie van AEM Assets </b></a>
        </td>
    </tr>
</table>

[!DNL Adobe Experience Manager] Met as a Cloud Service hebt u toegang tot [!DNL Dynamic Media] Prime- en Ultimate-aanbiedingen om uw digitale workflows te stroomlijnen en inhoudsbeheer te optimaliseren. Zie [ Dynamische Media Prime en Ultimate ](/help/assets/dynamic-media/dm-prime-ultimate.md) om hun voordelen en de belangrijkste verschillen tussen hen te begrijpen.

Dit artikel biedt de end-to-end workflow om het [!DNL Dynamic Media] Prime- en Ultimate-aanbod in te schakelen.

## [!DNL Dynamic Media] Ultimate inschakelen {#enable-dynamic-media-ultimate}

[!DNL Dynamic Media] Ultimate inschakelen:

1. [ activeer  [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi)
1. [ vorm  [!DNL Dynamic Media]  oplossingen ](#configure-dynamic-media-solutions)
1. [Creeer en lijst  [!DNL Dynamic Media]  bedrijven](#create-and-list-dynamic-media-companies)
1. [ vorm douanedomein in leveringsrij ](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the [!DNL AEM] [!DNL Dynamic Media] API card](#onboarding-api-keys)
-->

Als u [!DNL Dynamic Media Prime] moet toelaten, zie snelle verbindingen die in [ worden verstrekt  [!DNL Dynamic Media Prime]](#enable-dynamic-media-prime) toelaten.

### [!DNL Dynamic Media with OpenAPI] activeren {#activate-dynamic-media-with-openapi}

[!DNL Dynamic Media] met OpenAPI-mogelijkheden biedt DAM de kern van een flexibel en efficiënt systeem voor de toeleveringsketen van inhoud om beheer en levering van middelen te garanderen.

De eerste stap in het proces om [!DNL Dynamic Media] Ultimate toe te laten is [[!DNL Dynamic Media]  met OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) voor uw milieu van Cloud Service te activeren.

#### Voorbereiden op aan de slag {#prerequisites}

Zorg ervoor dat u aan de volgende vereisten voldoet voordat u het activeringsproces start:

1. [ Toegang tot Cloud Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [ Uw programma omvat  [!DNL Dynamic Media]  oplossingen ](#configure-dynamic-media-solutions).
1. U hebt een [!DNL Dynamic Media] Prime- of Ultimate-licentie.

#### [!DNL Dynamic Media with OpenAPI] mogelijkheden inschakelen in uw Cloud Service-omgeving {#enable-dynamic-media-with-openapi-capabilites-in-your-CS-environment}

Voer de volgende stappen uit om [!DNL Dynamic Media with OpenAPI] in te schakelen voor uw cloudserviceomgeving:

1. [ navigeer aan Cloud Manager UI ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. [ creeer een milieu ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-environments), als u geen toegang tot bestaande hebt.

1. Selecteer **[!UICONTROL Click to activate]** in de **[!UICONTROL Dynamic Media]** rij van de **[!UICONTROL Environment Information]** sectie op de pagina met omgevingsdetails.

   ![ activeer dynamische media met mogelijkheden OpenAPI ](/help/assets/assets/activate-adv-capabiliites-of-dm-openAPI.png)

1. Klik op **[!UICONTROL Activate]** in het bevestigingsvenster om het activeringsproces van [!DNL Dynamic Media with OpenAPI] te starten. Nadat de activering is voltooid, geeft de Cloud Manager de volgende statusupdates weer:
   1. **[!UICONTROL Environment stage]**: **[!UICONTROL Running]**
   1. ![ DM geactiveerd ](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media]**:**[!UICONTROL OpenAPI capabilities are activated]**

      ![ activering succesvol ](/help/assets/assets/activation-successful.png){width="700" align="left"}

#### Opnieuw activeren {#retry-activation}

Als activering mislukt, geeft de Cloud Manager de volgende statusupdates weer:

* **[!UICONTROL Environment stage]**: **[!UICONTROL DM with OpenAPI Failed]**
* ![ DM geactiveerd ](/help/assets/assets/Images_icon.svg)**[!UICONTROL Dynamic Media]**:**[!UICONTROL OpenAPI capabilities failed to activate]**

  ![ herprobeer activering ](/help/assets/assets/retry-dm-openapi-failed-activation.png){width="700" align="left"}

Selecteer **[!UICONTROL Click to retry]** om activering opnieuw te starten.

U kunt ook de volgende stappen uitvoeren om het activeringsproces opnieuw te starten:

1. Navigeer naar de pagina met alle omgevingen.

1. Klik meer opties (![ meer opties ](/help/assets/assets/three-dots.svg)) aan het eind van uw milieurij.

1. Selecteer **[!UICONTROL Retry DM with OpenAPI Activation]** om activering opnieuw te starten.

   ![ herprobeer activering van de pagina van omgevingsdetails ](/help/assets/assets/restart-activation-process-from-list-environment-page.png)

### [!DNL Dynamic Media] oplossingen configureren {#configure-dynamic-media-solutions}

Vorm [!UICONTROL Dynamic Media] oplossingen om de basis en geavanceerde mogelijkheden van [ Dynamische Media met OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) op bestaande of nieuwe milieu&#39;s te gebruiken beschikbaar in Cloud Manager.

#### Voorbereiden op aan de slag {#prerequisites-to-configure-dynamic-media-solutions}

Zorg ervoor dat u de volgende functies hebt om [!UICONTROL Dynamic Media] -oplossingen te configureren:

1. [ Toegang tot Cloud Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. U hebt [!DNL Dynamic Media] Ultimate-licentie.

#### [!DNL Dynamic Media] -oplossingen configureren voor de levering van bedrijfsmiddelen {#configure-dynamic-media-solutions-for-asset-delivery}

Voer de volgende stappen uit:

1. [ creeer een nieuw programma ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/create-program) of navigeer aan een bestaand programma en klik **[!UICONTROL Edit]**. Op de pagina **[!UICONTROL Set up for production]** wordt het tabblad **[!UICONTROL Solutions & Add-ons]** weergegeven.

1. Selecteer **[!UICONTROL Assets]** , **[!UICONTROL Assets Prime]** , **[!UICONTROL Assets Ultimate]** of **[!UICONTROL Sites]** om de **[!UICONTROL Dynamic Media]** -oplossing aan uw programma toe te voegen.

1. Selecteer **[!UICONTROL Dynamic Media]** oplossing en klik op **[!UICONTROL Continue]** om **[!UICONTROL Dynamic Media]** oplossing aan uw programma toe te voegen. Met deze actie start u alle bestaande omgevingen in uw programma opnieuw op en voegt u de [!DNL Dynamic Media] -oplossing eraan toe. Bovendien wordt elke nieuwe omgeving die u onder uw programma maakt, automatisch [!DNL Dynamic Media] opgehaald.

   ![ opstelling voor productie ](/help/assets/assets/set-up-for-prod.png){width="500" align="left"}

Zie [ activeren  [!DNL Dynamic Media with OpenAPI]](#activate-dynamic-media-with-openapi) beginnen de mogelijkheden van [!DNL Dynamic Media] met mogelijkheden OpenAPI in uw milieu te gebruiken.

### [!DNL Dynamic Media] bedrijven maken en aanbieden {#create-and-list-dynamic-media-companies}

Creëer en maak een lijst van [!DNL Dynamic Media] bedrijven in uw AEM-cloudserviceomgeving om configuraties in uw AEM-omgeving te beheren.

#### Voorbereiden op aan de slag {#prerequisites-to-create-and-list-dynamic-media-companies}

Als u de bestaande bedrijven (accounts) wilt zien of een nieuw [!DNL Dynamic Media] -bedrijf (account) wilt toevoegen aan uw IMS-org, moet u beschikken over:

1. [ Toegang tot Cloud Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).

1. U hebt [!DNL Dynamic Media] Ultimate-licentie.

#### [!DNL Dynamic Media] Bedrijven in uw IMS-organisatie maken en weergeven {#create-and-list-dynamic-media-companies-in-your-ims-organisation}

Voer de volgende stappen uit om een nieuw [!DNL Dynamic Media] -bedrijf (account) te maken en weer te geven dat binnen uw [!DNL AEM] -omgeving kan worden geconfigureerd:

1. Navigeer aan de [ de vergunningspagina van Cloud Manager ](https://experience-stage.adobe.com/#/@ssahnichstage/cloud-manager/license).

1. Klik op **[!UICONTROL Add Company]** en het dialoogvenster **[!UICONTROL Create Dynamic Media Company]** wordt weergegeven.

1. Geef een unieke bedrijfsnaam van [!DNL Dynamic Media] op, selecteer een bedrijfsgebied en voeg een lijst met e-mailadressen van bedrijfsbeheerders toe, gescheiden door komma&#39;s.

   ![ creeer Dynamisch bedrijf van Media ](/help/assets/assets/create-dynamic-media-company.png){width="500" align="left"}

1. Klik op **[!UICONTROL Create]** om uw bedrijf te maken. Met deze actie voegt u een nieuwe rij toe aan de **[!UICONTROL [!DNL Dynamic Media] companies]** -sectie en geeft u **[!UICONTROL Setting up]** weer als de **[!UICONTROL STATUS]** -sectie van het bedrijf.

   ![ in werking gestelde Dynamische het bedrijfverwezenlijking van Media ](/help/assets/assets/dm-company-creation-initiated.png)

1. **Facultatief:** klik ![ infopictogram ](/help/assets/assets/info-icon-solid-black.svg) om de details van het bedrijf te zien. De **[!UICONTROL STATUS]** wordt bijgewerkt naar **[!UICONTROL Ready]** wanneer het bedrijf wordt gemaakt.

   ![ Dynamische het bedrijfinformatie van Media ](/help/assets/assets/dm-company-information.png)

1. Als Dynamische Beheerder van Media, controleer uw brievenbus voor welkome e-mail die een lijst van stappen omvat om [  [!DNL Dynamic Media]](/help/assets/dynamic-media/config-dm.md#architecture-diagram-of-dynamic-media) bedrijf in uw [!DNL AEM] milieu van Cloud Service te vormen om begonnen te worden.

   ![ welkome e-mail ](/help/assets/assets/welcome-email.png)

#### Bedrijf opnieuw maken {#retry-company-creation}

Als het aanmaken van [!DNL Dynamic Media] bedrijven mislukt, voert u de volgende stappen uit op basis van de status van de fout:

1. Als **[!UICONTROL Status]** in behandeling is, stelt u het probleem ter oplossing voor aan het klantenondersteuningsteam.


   ![ hangende status ](/help/assets/assets/company-creation-pending-status.png){width="350" align="center"}



1. Als **[!UICONTROL Status]** is mislukt, probeert u het opnieuw op basis van de oorzaak van de fout.

   ![ ontbroken status ](/help/assets/assets/company-creation-failure-status.png){width="380" align="center"}

### Optioneel: aangepaste domein in leveringslaag configureren {#configure-custom-domain-in-delivery-tier}

Als AEM as a Cloud Service wordt geleverd met een standaarddomein, kunt u dit naar wens aanpassen. Koppel een aangepast domein met Cloud Manager aan de leveringslaag.

#### Voorbereiden op aan de slag {#prerequisites-to-configure-custom-domain-in-delivery-tier}

Zorg ervoor dat u aan de volgende vereisten voldoet voordat u het configuratieproces start:

1. [ Toegang tot Cloud Manager ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [ reeds geactiveerd  [!DNL Dynamic Media with OpenAPI]  in uw milieu ](#activate-dynamic-media-with-openapi).
1. Ingeschakeld [!DNL Dynamic Media with OpenAPI] in gebruiksklare toestand.
1. EV- of OV-typecertificaat voor het domein dat moet worden gebruikt voor de leveringslaag. Zie [ Inleiding aan SSL certificaten ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) voor meer details.

#### Aangepast domein in leveringslaag configureren met Cloud Manager {#configure-custom-domain-in-delivery-tier-using-cloud-manager}

Voer de volgende stappen in Cloud Manager uit om een aangepast domein in de leveringsrij te vormen:

1. [ voeg een klant geleid SSL certificaat ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert) toe.

1. [ voeg een naam van het douanedomein ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings) toe.

1. Navigeer aan de pagina van milieudetails en [ voeg een configuratie CDN ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/domain-mappings/add-domain-mapping) toe. Selecteer tijdens het toevoegen van de configuratie **[!UICONTROL Delivery]** in het veld **[!UICONTROL Tier]** in het dialoogvenster **[!UICONTROL Configure CDN]** .

   ![ vorm CDN ](/help/assets/assets/select-delivery-tier-in-configure-cdn-form.png)

   Nadat u de configuraties hebt toegevoegd, wordt de lus **[!UICONTROL STATUS]** van **[!UICONTROL CDN Configurations]** bijgewerkt naar **[!UICONTROL Applied]** .

   ![ vorm CDN plaatsingsstatus ](/help/assets/assets/cdn-configuration-deployment-status.png)

1. Klik meer opties (![ meer opties ](/help/assets/assets/three-dots.svg)) en selecteer **[!UICONTROL Go live readiness]** om de **[!UICONTROL Go live readiness]** dialoogdoos te tonen.

   ![ ga levende bereidheid optie ](/help/assets/assets/go-live-readiness-option.png)

1. Voer de **[!UICONTROL Configure CNAME]** stappen uit om [ cdn.adobeaemcloud.com ](http://cdn.adobeaemcloud.com/) (het verslag van CNAME) in het DNS verslag van de DNS dienstverlener in kaart te brengen. Deze afbeelding zorgt ervoor dat de verzoeken die bij het douanedomein worden ontvangen aan Adobe CDN opnieuw worden gericht.

   ![ ga levende gereedheidsdialoogdoos ](/help/assets/assets/go-live-readiness-dialogbox.png){width="500" align="left"}

1. Klik op **[!UICONTROL Ok]** en **[!UICONTROL STATUS]** werkt het bestand bij met **[!UICONTROL Verified]** . Het aangepaste domein kan worden gebruikt in de URL van de levering.


   ![ vorm CDN ](/help/assets/assets/cdn-configurations-varified.png)



<!--
### Onboard API keys {#onboarding-api-keys}

Create an API key to access [!DNL Dynamic Media] with OpenAPIs and the delivery tier backed Asset Selector.

#### Prepare yourself for API keys onboarding process {#prerequisites-for-onboarding-api-keys} 

To start the API keys onboarding process, ensure you have:

1. [Access to Cloud Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/onboarding/journey/cloud-manager).
1. [Activated [!DNL Dynamic Media with OpenAPI] in your environment](#activate-dynamic-media-with-openapi).
1. [Access to the Adobe Developer Console](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis#create-adobe-developer-console-adc-project).

#### Onboard the API keys using [!DNL AEM Dynamic Media] API card {#onboarding-api-keys-using-aem-dynamic-media-api-card}

Use the [Adobe Developer Console](https://developer.adobe.com/developer-console/) to onboard the API keys to:

1. [Access Dynamic Media APIs](#access-dynamic-media-apis)
1. [Access Delivery tier backed Asset Selector](#access-delivery-tier-backed-asset-selector)

#### Create an API key to access [!DNL Dynamic Media] with OpenAPIs {#access-dynamic-media-apis}

Execute the following steps to create an API key to access [!DNL Dynamic Media] with OpenAPIs:

1. Navigate to the **[!UICONTROL Admin Console]**. The Admin Console displays the **[!UICONTROL author]**, **[!UICONTROL delivery]** and **[!UICONTROL publish]** instances.
![instances on admin console](/help/assets/assets/delivery-instance-admin-console.png)
1. Select the **[!UICONTROL delivery]** instance to display the product profile with **[!UICONTROL AEM Dynamic Media enable API Services]** enabled by default. The product profile looks like this: **[!UICONTROL AEM Assets DM OpenAPI Users - delivery  - Program [ID Number] - Environment [ID Number]]**. 

   ![product profile on admin console](/help/assets/assets/admin-console-product-profile.png)

   >[!NOTE]
   >
   >This delivery instance is common for [!DNL Content Hub] and [!DNL Dynamic Media] with OpenAPI capabilities.

1. Navigate to the [Adobe Developer console](https://developer.adobe.com/console) and [create a new project](https://developer.adobe.com/dep/guides/dev-console/create-project/). See [Invoke OpenAPI-based AEM APIs for server to server authentication](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) to learn about creating a new project.
1. Select **[!UICONTROL AEM Dynamic Media API]** to access to the [!DNL Dynamic Media with OpenAPI capabilities] and click **[!UICONTROL Next]**.
![adobe developer console](/help/assets/assets/adobe-developer-console.png)
1. Select **[!UICONTROL Server-to-Server Authentication]** and click **[!UICONTROL Next]**. See [Server to Server authentication](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/) to learn more about this authentication type.
![server-to-server-authentication](/help/assets/assets/server-to-server-authentication.png)
1. Select **[!UICONTROL OAuth Server-to-Server]**, specify a unique **[!UICONTROL Credential name]** and click **[!UICONTROL Next]**.
![oauth server to server credential](/help/assets/assets/oauth-server-server-and-credential-name.png)
1. Select your product profile (mentioned in step 2) to access the APIs using the environment's delivery endpoint and click **[!UICONTROL Save configured API]**.
![select product profile](/help/assets/assets/select-product-profile.png)
1. Select **[!UICONTROL AEM Dynamic Media API]**. Use the **[!UICONTROL OAuth Server-to-Server]** to fetch the **X-API-key** and access the token for the **authorization** header. 
![oauth server to server](/help/assets/assets/oauth-server-to-server-credentials.png)
Execute the below steps to use [Dynamic Media with OpenAPIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) using the **[!UICONTROL OAuth Server-to-Server]** credentials. 
    1. Copy the **[!UICONTROL API KEY (Client ID)]** and replace the `X-Api-Key` in the cURL.
    1. Click **[!UICONTROL Generate access token]** to generate an access token and replace `YOUR_JWT_HERE` with the token in the cURL.

The cURL looks like this:
```
headers: {
    'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    `},
```
See [Search Assets API](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/search-assets-api#search-assets-api-header) for more information.

### Access Delivery tier backed Asset Selector {#access-delivery-tier-backed-asset-selector}

TBD: Wiki in progress..
-->

## [!DNL Dynamic Media] Prime inschakelen {#enable-dynamic-media-prime}

[!DNL Dynamic Media] Prime inschakelen:

1. [ activeer Dynamische Media met OpenAPI ](#activate-dynamic-media-with-openapi)
1. [ Facultatief: Vorm douanedomein in leveringsrij ](#configure-custom-domain-in-delivery-tier)

<!--
1. [Onboard API keys using the AEM Dynamic Media API card](#onboarding-api-keys)
-->
