---
title: Hoe te om Gegevensbronnen te vormen?
description: Leer hoe te om RESTful Webdiensten, op SOAP-Gebaseerde Webdiensten, en de diensten van OData als gegevensbronnen voor een model van vormgegevens (FDM) te vormen.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 7b31a2ea016567979288c7a8e55ed5bf8dfc181d
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 0%

---


# Gegevensbronnen configureren {#configure-data-sources}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html) |
| AEM as a Cloud Service | Dit artikel |

![Gegevensintegratie](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Met gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden. De volgende typen worden buiten de box ondersteund:

* Relationele databases - MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®], postgreSQL, en [!DNL Oracle RDBMS]
* RESTful-webservices
* SOAP-webservices
* OData-diensten (versie 4.0)
* Microsoft® Dynamics
* SalesForce
* Microsoft® Azure Blob Storage

Gegevensintegratie ondersteunt OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, en API Key authentication types out-of-the-box, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl de RESTful, op SOAP-Gebaseerde, en de diensten OData binnen worden gevormd [!DNL Experience Manager] as a Cloud Service, JDBC voor relationele gegevensbanken en schakelaar voor [!DNL Experience Manager] gebruikersprofiel is geconfigureerd in [!DNL Experience Manager] webconsole.

## Relationele database configureren {#configure-relational-database}

### Vereisten

Voordat u relationele databases configureert met [!DNL Experience Manager] Webconsoleconfiguratie:
* [Geavanceerde netwerken inschakelen via de cloud Manager-API](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html), omdat poorten standaard zijn uitgeschakeld.
* [JDBC-stuurprogramma-afhankelijkheden toevoegen in Maven](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=en#mysql-driver-dependencies).


### Stappen om een relationele database te configureren

U kunt relationele databases configureren met [!DNL Experience Manager] Webconsole-configuratie. Ga als volgt te werk:

1. Ga naar [!DNL Experience Manager] webconsole op `https://server:host/system/console/configMgr`.
1. Zoeken **[!UICONTROL Day Commons JDBC Connections Pools]** configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.

   ![JDBC-connectorpool](/help/forms/assets/jdbc_connector.png)

1. In de configuratiedialoog, specificeer de details voor het gegevensbestand u, zoals wilt vormen:

   * Java™-klassenaam voor het JDBC-stuurprogramma
   * URI voor JDBC-verbinding
   * Gebruikersnaam en wachtwoord voor verbinding met het JDBC-stuurprogramma
   * Geef een SQL SELECT-query op in het dialoogvenster **[!UICONTROL Validation Query]** veld voor het valideren van verbindingen vanuit de pool. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:
      * SELECT 1 (MySQL en MS® SQL)
      * SELECTEER 1 uit twee items (Oracle)
   * Naam van de gegevensbron

   Voorbeeldtekenreeksen voor het configureren van een relationele database:

   ```text
      "datasource.name": "sqldatasourcename-mysql",
      "jdbc.driver.class": "com.mysql.jdbc.Driver",
      "jdbc.connection.uri": "jdbc:mysql://$[env:AEM_PROXY_HOST;default=proxy.tunnel]:30001/sqldatasourcename"
   ```

   >[!NOTE]
   >
   > Zie [SQL-verbindingen met JDBC DataSourcePool](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html) voor meer gedetailleerde informatie.

1. Selecteren **[!UICONTROL Save]** om de configuratie op te slaan.

Nu, kunt u het gevormde relationele gegevensbestand met uw Model van de Gegevens van het Vorm (FDM) gebruiken.

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and select to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties are available for use in form data model (FDM). Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model (FDM) can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Select **[!UICONTROL Save]** to save the configuration. -->

## Map configureren voor configuraties van cloudservices {#cloud-folder}

Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van cloudservices in [!DNL Experience Manager] worden geconsolideerd in de `/conf` map in [!DNL Experience Manager] opslagplaats. Standaard worden de `conf` map bevat de `global` map waar u configuraties voor cloudservices kunt maken. U moet deze optie echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om cloudserviceconfiguraties te maken en te organiseren.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   * Zie de [Configuratiebrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html) documentatie voor meer informatie.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. In de **[!UICONTROL Configuration Browser]**, selecteert u de `global` map en selecteer **[!UICONTROL Properties]**.

   1. In de **[!UICONTROL Configuration Properties]** dialoogvenster, inschakelen **[!UICONTROL Cloud Configurations]**.

   1. Selecteren **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. In de **[!UICONTROL Configuration Browser]**, selecteert u **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** , geeft u een titel voor de map op en schakelt u **[!UICONTROL Cloud Configurations]**.
1. Selecteren **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.

## RESTful-webservices configureren {#configure-restful-web-services}

RESTful-webservices kunnen worden beschreven met [Specificaties van de wagon](https://swagger.io/specification/v2/) in JSON- of YAML-indeling in een [!DNL Swagger] definitiebestand. RESTful-webservice configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u of [!DNL Swagger] file ([Versie 2.0](https://swagger.io/specification/v2/)) of [!DNL Swagger] file ([Tagvormige versie 3.0](https://swagger.io/specification/v3/)) op uw bestandssysteem of op de URL waar het bestand wordt gehost.

### RESTful-services configureren voor Open API Specification versie 2.0 {#configure-restful-services-open-api-2.0}

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL RESTful Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer een URL of een bestand in het menu [!UICONTROL Swagger Source] vervolgkeuzelijst en geeft dienovereenkomstig de [!DNL Swagger URL] aan de[!DNL  Swagger] definitiebestand uploaden of [!DNL Swagger] van uw lokale bestandssysteem.
   * Op basis van de[!DNL  Swagger] Broninvoer. De volgende velden zijn vooraf ingevuld met waarden:

      * Schema: de overdrachtprotocollen die door de REST API worden gebruikt. Het aantal schematypen dat in de drop-down lijst toont hangt van de regelingen af die in worden bepaald [!DNL Swagger] bron.
      * Host: de domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
        Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.

   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, API Key, of Custom Authentication — om toegang te krijgen tot de RESTful-service en dienovereenkomstig gegevens te verstrekken voor verificatie.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteren **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst te creëren.

### RESTful-services configureren voor Open API Specification versie 3.0 {#configure-restful-services-open-api-3.0}

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL RESTful Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer een URL of een bestand in het menu [!UICONTROL Swagger Source] vervolgkeuzelijst en geeft dienovereenkomstig de [!DNL Swagger 3.0 URL] aan de[!DNL  Swagger] definitiebestand uploaden of [!DNL Swagger] van uw lokale bestandssysteem.
   * Op basis van de[!DNL  Swagger] De broninvoer, de verbindingsinformatie met de doelserver wordt getoond.
   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, API Key, of Custom Authentication — om toegang te krijgen tot de RESTful-service en dienovereenkomstig gegevens te verstrekken voor verificatie.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteren **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst te creëren.

Sommige bewerkingen die niet worden ondersteund door RESTful-services Open API Specification versie 3.0 zijn:
* Callbacks
* één of meer
* Externe referentie
* Koppelingen
* Verschillende aanvraagorganen voor verschillende MIME-typen voor één enkele bewerking

Zie [OpenAPI 3.0-specificatie](https://swagger.io/specification/v3/) voor nadere informatie.

### De cliëntconfiguratie van HTTP van het het gegevensmodel van de vorm (FDM) om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] vormen een gegevensmodel wanneer het integreren met RESTful Webdiensten aangezien de gegevensbron HTTP cliëntconfiguraties voor prestatiesoptimalisering omvat.

Stel de volgende eigenschappen van de **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]** configuratie voor het opgeven van de reguliere expressie:

* Gebruik de `http.connection.max.per.route` eigenschap om het maximum aantal toegestane verbindingen tussen het formuliergegevensmodel (FDM) en de RESTful-webservices in te stellen. De standaardwaarde is 20 verbindingen.

* Gebruik de `http.connection.max` bezit om het maximumaantal toegestane verbindingen voor elke route te specificeren. De standaardwaarde is 40 verbindingen.

* Gebruik de `http.connection.keep.alive.duration` eigenschap om de duur op te geven waarvoor een blijvende HTTP-verbinding in leven wordt gehouden. De standaardwaarde is 15 seconden.

* Gebruik de `http.connection.timeout` eigenschap om de duur op te geven waarvoor de [!DNL Experience Manager Forms] server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

* Gebruik de `http.socket.timeout` eigenschap om de maximale periode voor inactiviteit tussen twee gegevenspakketten op te geven. De standaardwaarde is 30 seconden.

In het volgende JSON-bestand wordt een voorbeeld weergegeven:


```json
{   
   "http.connection.keep.alive.duration":"15",   
   "http.connection.max.per.route":"20",   
   "http.connection.timeout":"10",   
   "http.socket.timeout":"30",   
   "http.connection.idle.connection.timeout":"15",   
   "http.connection.max":"40" 
} 
```

1. Selecteren **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]**.

1. In de [!UICONTROL Form Data Model HTTP Client Configuration for REST data source] dialoogvenster:

   * Geef het maximale aantal toegestane verbindingen op tussen het formuliergegevensmodel (FDM) en de RESTful-webservices in het dialoogvenster **[!UICONTROL Connection limit in total]** veld. De standaardwaarde is 20 verbindingen.

   * Specificeer het maximumaantal toegestane verbindingen voor elke route in **[!UICONTROL Connection limit on per route basis]** veld. De standaardwaarde is twee verbindingen.

   * Geef de duur op, gedurende welke een blijvende HTTP-verbinding in leven blijft in het dialoogvenster **[!UICONTROL Keep alive]** veld. De standaardwaarde is 15 seconden.

   * Geef de duur op waarvoor de [!DNL Experience Manager Forms] server wacht tot een verbinding tot stand is gebracht, in de **[!UICONTROL Connection timeout]** veld. De standaardwaarde is 10 seconden.

   * Geef de maximale periode voor inactiviteit op tussen twee gegevenspakketten in het dialoogvenster **[!UICONTROL Socket timeout]** veld. De standaardwaarde is 30 seconden.

## SOAP-webservices configureren {#configure-soap-web-services}

SOAP-webservices worden beschreven met [Web Services Description Language (WSDL)-specificaties](https://www.w3.org/TR/wsdl). [!DNL Experience Manager Forms] ondersteunt het WSDL-model in RPC niet.

Om op SOAP-Gebaseerde Webdienst te vormen binnen [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u WSDL URL voor de Webdienst hebt, en doe het volgende:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL SOAP Web Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Geef het volgende op voor de SOAP-webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basisverificatie of Aangepaste verificatie — voor toegang tot de SOAP-service en dienovereenkomstig de gegevens voor verificatie opgeven.

     <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
     <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

     <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteren **[!UICONTROL Create]** om de cloudconfiguratie voor de SOAP-webservice te maken.

### Het gebruik van importinstructies in SOAP-webservices WSDL inschakelen {#enable-import-statements}

U kunt een reguliere expressie opgeven die fungeert als filter voor absolute URL&#39;s die zijn toegestaan als importinstructies in de WSDL van SOAP-webservices. Standaard is er geen waarde in dit veld. Dientengevolge, [!DNL Experience Manager] blokkeert alle importinstructies die beschikbaar zijn in WSDL. Als u `.*` als waarde in dit veld, [!DNL Experience Manager] staat alle instructies import toe.

Stel de `importAllowlistPattern` eigendom van de **[!UICONTROL Form Data Model SOAP Web Services Import Allowlist]** configuratie om de reguliere expressie op te geven. In het volgende JSON-bestand wordt een voorbeeld weergegeven:

```json
{
  "importAllowlistPattern": ".*"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Een OData-service configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u de dienstwortel URL voor de dienst hebt, en doe het volgende:

>[!NOTE]
>
> FDM-ondersteuning (Form Data Model) [OData versie 4](https://www.odata.org/documentation/).
>Voor een geleidelijke gids om te vormen [!DNL Microsoft®® Dynamics 365], online of ter plaatse, zie [[!DNL Microsoft® Dynamics] OData-configuratie](ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Selecteren **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL OData Service]** van de **[!UICONTROL Service Type]** vervolgkeuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en selecteert u **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het verificatietype: None, OAuth2.0([Autorisatiecode](https://oauth.net/2/grant-types/authorization-code/), [Client Credentials](https://oauth.net/2/grant-types/client-credentials/)), Basic Authentication, API Key, of Custom Authentication — om toegang te krijgen tot de OData-service en dienovereenkomstig de gegevens voor verificatie te verstrekken.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   >[!NOTE]
   >
   >Selecteer het OAuth 2.0 authentificatietype om met te verbinden [!DNL Microsoft®® Dynamics] diensten die het eindpunt OData als de dienstwortel gebruiken.

1. Selecteren **[!UICONTROL Create]** om de wolkenconfiguratie voor de dienst te creëren OData.

<!--
## Configure Microsoft® SharePoint List {#config-sharepoint-list}

<span class="preview"> This is a pre-release feature and accessible through our [pre-release channel](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

To save data in a tabular form use, Microsoft® SharePoint List. To configure a Microsoft SharePoint List in [!DNL Experience Manager] as a Cloud Service, do the following:

1. Go to **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.   
1. Select a **Configuration Container**. The configuration is stored in the selected Configuration Container. 
1. Click **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** from the drop-down list. The SharePoint configuration wizard appears.  
1. Specify the **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** and **[!UICONTROL OAuth URL]**. For information on how to retrieve Client ID, Client Secret, Tenant ID for OAuth URL, see [Microsoft&reg; Documentation](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
    * You can retrieve the `Client ID` and `Client Secret` of your app from the Microsoft&reg; Azure portal.
    * In the Microsoft&reg; Azure portal, add the Redirect URI as `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Replace `[author-instance]` with the URL of your Author instance.
    * Add the API permissions `offline_access` and `Sites.Manage.All` in the **Microsoft® Graph** tab to provide read/write permissions. Add `AllSites.Manage` permission in the **Sharepoint** tab to interact remotely with SharePoint data.
    * Use OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Replace `<tenant-id>` with the `tenant-id` of your app from the Microsoft&reg; Azure portal.

      >[!NOTE]
      >
      > The **client secret** field is mandatory or optional depends upon your Azure Active Directory application configuration. If your application is configured to use a client secret, it is mandatory to provide the client secret.

1. Click **[!UICONTROL Connect]**. On a successful connection, the `Connection Successful` message appears.
1. Select **[!UICONTROL SharePoint Site]** and **[!UICONTROL SharePoint List]** from the drop-down list.
1. Select **[!UICONTROL Create]** to create the cloud configuration for the Microsoft® SharePointList.

-->

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model (FDM), both the data source and [!DNL Experience Manager] Server running Form Data Model (FDM) authenticate each other's identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model (FDM) on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and select **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and select **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, select **[!UICONTROL Select Certificate File]**, upload the certificate, and select **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een FDM (Form Data Model) maken of als u al een FDM (Form Data Model) zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de gegevensbronnen die u hebt geconfigureerd. Zie [Formuliergegevensmodel maken](create-form-data-models.md) voor meer informatie.


<!--

>[!MORELIKETHIS]
>
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>*  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->