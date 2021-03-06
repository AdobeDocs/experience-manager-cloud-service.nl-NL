---
title: Hoe te om Gegevensbronnen te vormen?
description: Met Experience Manager Forms Data Integration kunt u verschillende gegevensbronnen configureren en verbinden. Leer hoe u RESTful-webservices, SOAP-webservices en OData-services configureert als gegevensbronnen en deze kunt gebruiken om formuliergegevensmodellen te maken.
feature: Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: 983f1b815fd213863ddbcd83ac7e3f076c57d761
workflow-type: tm+mt
source-wordcount: '1574'
ht-degree: 0%

---

# Gegevensbronnen configureren {#configure-data-sources}

![Gegevensintegratie](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Met gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden. De volgende typen worden buiten de box ondersteund:

<!-- * Relational databases - MySQL, [!DNL Microsoft SQL Server], [!DNL IBM DB2], and [!DNL Oracle RDBMS] 
* [!DNL Experience Manager] user profile  -->
* RESTful-webservices
* SOAP-webservices
* OData-diensten (versie 4.0)
* Microsoft Dynamics
* SalesForce
* Microsoft Azure Blob Storage

De integratie van gegevens steunt OAuth2.0, Basisauthentificatie, en API Zeer belangrijke authentificatietypes out-of-the-box, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl de RESTful, op SOAP-Gebaseerde, en de diensten OData binnen worden gevormd [!DNL Experience Manager] as a Cloud Service <!--, JDBC for relational databases --> en aansluiting voor [!DNL Experience Manager] gebruikersprofiel is geconfigureerd in [!DNL Experience Manager] webconsole.

>[!NOTE]
>
>[!UICONTROL Experience Manager Forms] ondersteunt geen relationele database.

<!-- ## Configure relational database {#configure-relational-database}

You can configure relational databases using [!DNL Experience Manager] Web Console Configuration. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://server:host/system/console/configMgr`.
1. Look for **[!UICONTROL Apache Sling Connection Pooled DataSource]** configuration. Tap to open the configuration in edit mode.
1. In the configuration dialog, specify the details for the database you want to configure, such as:

    * Name of the data source
    * Data source service property that stores the data source name
    * Java class name for the JDBC driver
    * JDBC connection URI
    * Username and password to establish connection with the JDBC driver

   >[!NOTE]
   >
   >Ensure that you encrypt sensitive information like passwords before configuring the data source. To encrypt:
   >
   >    
   >    
   >    1. Go to https://'[server]:[port]'/system/console/crypto.
   >    1. In the **[!UICONTROL Plain Text]** field, specify the password or any string to encrypt and tap **[!UICONTROL Protect]**.
   >    
   >    
   >    
   >The encrypted text appears in the Protected Text field that you can specify in the configuration.

1. Enable **[!UICONTROL Test on Borrow]** or **[!UICONTROL Test on Return]** to specify that the objects are validated before being borrowed or returned from and to the pool, respectively.
1. Specify a SQL SELECT query in the **[!UICONTROL Validation Query]** field to validate connections from the pool. The query must return at least one row. Based on your database, specify one of the following:

    * SELECT 1 (MySQL and MS SQL) 
    * SELECT 1 from dual (Oracle)

1. Tap **[!UICONTROL Save]** to save the configuration. -->

<!-- ## Configure [!DNL Experience Manager] user profile {#configure-aem-user-profile}

You can configure [!DNL Experience Manager] user profile using User Profile Connector configuration in [!DNL Experience Manager] Web Console. Do the following:

1. Go to [!DNL Experience Manager] web console at `https://[server]:[port]/system/console/configMgr`.
1. Look for **[!UICONTROL AEM Forms Data Integrations - User Profile Connector Configuration]** and tap to open the configuration in edit mode.
1. In the User Profile Connector Configuration dialog, you can add, remove, or update user profile properties. The specified properties will be available for use in form data model. Use the following format to specify user profile properties:

   `name=[property_name_with_location_in_user_profile],type=[property_type]`

   Examples:

    * `name=profile/phoneNumber,type=string`
    * `name=profile/empLocation/*/city,type=string`

   >[!NOTE]
   >
   >The **&#42;** in the above example denotes all nodes under the `profile/empLocation/` node in [!DNL Experience Manager] user profile in CRXDE structure. It means that the Form Data Model can access the `city` property of type `string` present in any node under the `profile/empLocation/` node. However, the nodes that contain the specified property must follow a consistent structure.

1. Tap **[!UICONTROL Save]** to save the configuration. -->

## Map configureren voor configuraties van cloudservices {#cloud-folder}

Configuratie voor map met cloudservices is vereist voor het configureren van cloudservices voor RESTful-, SOAP- en OData-services.

Alle configuraties van cloudservices in [!DNL Experience Manager] worden geconsolideerd in de `/conf` map in [!DNL Experience Manager] opslagplaats. Standaard worden de `conf` map bevat de `global` map waar u configuraties voor cloudservices kunt maken. U moet deze optie echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om cloudserviceconfiguraties te maken en te organiseren.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]**.
   * Zie de [Configuratiebrowser](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html) documentatie voor meer informatie.
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. In de **[!UICONTROL Configuration Browser]**, selecteert u de `global` map en tik **[!UICONTROL Properties]**.

   1. In de **[!UICONTROL Configuration Properties]** dialoogvenster, inschakelen **[!UICONTROL Cloud Configurations]**.

   1. Tikken **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. In de **[!UICONTROL Configuration Browser]**, tikken **[!UICONTROL Create]**.
1. In de **[!UICONTROL Create Configuration]** een titel voor de map opgeven en inschakelen **[!UICONTROL Cloud Configurations]**.
1. Tikken **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor configuraties van de cloudservice.

## RESTful-webservices configureren {#configure-restful-web-services}

RESTful-webservice kan worden beschreven met [Specificaties van de wagon](https://swagger.io/specification/v2/) in JSON- of YAML-indeling in een [!DNL Swagger] definitiebestand. RESTful-webservice configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u of [!DNL Swagger] file ([Versie 2.0](https://swagger.io/specification/v2/)) op uw bestandssysteem of de URL waar het bestand wordt gehost.

Doe het volgende de diensten RESTful vormen:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Tikken **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL RESTful Service]** van de **[!UICONTROL Service Type]** keuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en tikt u op **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer URL of Bestand in het menu [!UICONTROL Swagger Source] vervolgkeuzelijst en geeft dienovereenkomstig de [!DNL Swagger URL] aan de[!DNL  Swagger] definitiebestand uploaden of [!DNL Swagger] van uw lokale bestandssysteem.
   * Op basis van de[!DNL  Swagger] De volgende velden worden vooraf gevuld met waarden bij de invoer van de bron:

      * Schema: De overdrachtprotocollen die door REST API worden gebruikt. Het aantal schematypen dat in de drop-down lijst toont hangt van de regelingen af die in worden bepaald [!DNL Swagger] bron.
      * Host: De domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: Het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
         Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.
   * Selecteer het authentificatietype ??? niets, OAuth2.0, Basisauthentificatie, API Sleutel, of de Authentificatie van de Douane ??? om tot de dienst toegang te hebben RESTful, en dienovereenkomstig details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tikken **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst tot stand te brengen.

### Het model van de gegevens van de vormHTTP cli??ntconfiguratie om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] formuliergegevensmodel bij integratie met RESTful-webservices als gegevensbron bevat HTTP-clientconfiguraties voor optimalisatie van prestaties.

Stel de volgende eigenschappen van de **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]** configuratie voor het opgeven van de reguliere expressie:

* Gebruik de `http.connection.max.per.route` eigenschap om het maximum aantal toegestane verbindingen tussen het formuliergegevensmodel en RESTful-webservices in te stellen. De standaardwaarde is 20 verbindingen.

* Gebruik de `http.connection.max` bezit om het maximumaantal toegestane verbindingen voor elke route te specificeren. De standaardwaarde is 40 verbindingen.

* Gebruik de `http.connection.keep.alive.duration` eigenschap om de duur op te geven waarvoor een blijvende HTTP-verbinding in leven wordt gehouden. De standaardwaarde is 15 seconden.

* Gebruik de `http.connection.timeout` eigenschap om de duur op te geven waarvoor [!DNL Experience Manager Forms] server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

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

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.


Voer de volgende stappen uit om de HTTP-client van het formuliergegevensmodel te configureren:

1. Aanmelden bij [!DNL Experience Manager Forms] Instantie van auteur als beheerder en ga naar [!DNL Experience Manager] bundels voor webconsoles. De standaard-URL is [https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr).

1. Tik op **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]**.

1. In de [!UICONTROL Form Data Model HTTP Client Configuration for REST data source] dialoogvenster:

   * Geef het maximale aantal toegestane verbindingen op tussen het gegevensmodel van het formulier en de RESTful-webservices in het dialoogvenster **[!UICONTROL Connection limit in total]** veld. De standaardwaarde is 20 verbindingen.

   * Specificeer het maximumaantal toegestane verbindingen voor elke route in **[!UICONTROL Connection limit on per route basis]** veld. De standaardwaarde is 2 verbindingen.

   * Geef de duur op, gedurende welke een blijvende HTTP-verbinding in leven blijft in het dialoogvenster **[!UICONTROL Keep alive]** veld. De standaardwaarde is 15 seconden.

   * Geef de duur op waarvoor de [!DNL Experience Manager Forms] server wacht tot een verbinding tot stand is gebracht, in het dialoogvenster **[!UICONTROL Connection timeout]** veld. De standaardwaarde is 10 seconden.

   * Geef de maximale periode voor inactiviteit op tussen twee gegevenspakketten in het dialoogvenster **[!UICONTROL Socket timeout]** veld. De standaardwaarde is 30 seconden.

## SOAP-webservices configureren {#configure-soap-web-services}

SOAP-webservices worden beschreven met [Web Services Description Language (WSDL)-specificaties](https://www.w3.org/TR/wsdl). [!DNL Experience Manager Forms] biedt geen ondersteuning voor WSDL-model van RPC-stijl.

Om op SOAP-Gebaseerde Webdienst te vormen binnen [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u WSDL URL voor de Webdienst hebt, en doe het volgende:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](configure-data-sources.md#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Tikken **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL SOAP Web Service]** van de **[!UICONTROL Service Type]** keuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en tikt u op **[!UICONTROL Next]**.
1. Geef het volgende op voor de SOAP-webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het authentificatietype ??? niets, OAuth2.0, Basisauthentificatie, of de Authentificatie van de Douane ??? om tot de dienst van de ZEEP toegang te hebben, en dienovereenkomstig de details voor authentificatie te verstrekken.

      <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
      <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

      <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Tikken **[!UICONTROL Create]** om de cloudconfiguratie voor de SOAP-webservice te maken.

### Het gebruik van importinstructies in SOAP-webservices WSDL inschakelen {#enable-import-statements}

U kunt een reguliere expressie opgeven die fungeert als filter voor absolute URL&#39;s die zijn toegestaan als importinstructies in de WSDL van SOAP-webservices. Standaard is er geen waarde in dit veld. Dientengevolge [!DNL Experience Manager] blokkeert alle importinstructies die beschikbaar zijn in WSDL. Als u `.*` als waarde in dit veld, [!DNL Experience Manager] staat alle instructies import toe.

Stel de `importAllowlistPattern` eigendom van de **[!UICONTROL Form Data Model SOAP Web Services Import Allowlist]** configuratie om de reguliere expressie op te geven. In het volgende JSON-bestand wordt een voorbeeld weergegeven:

```json
{
  "importAllowlistPattern": ".*"
}
```

Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

## OData-services configureren {#config-odata}

De dienst OData wordt ge??dentificeerd door zijn de dienstwortel URL. Een OData-service configureren in [!DNL Experience Manager] as a Cloud Service, zorg ervoor dat u de dienstwortel URL voor de dienst hebt, en doe het volgende:

>[!NOTE]
>
> Formuliergegevensmodel ondersteunt [OData versie 4](https://www.odata.org/documentation/).
>Voor geleidelijke gids om te vormen [!DNL Microsoft Dynamics 365], online of ter plaatse, zie [[!DNL Microsoft Dynamics] OData-configuratie](ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]**. Tik om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [Map configureren voor configuraties van cloudservices](#cloud-folder) voor informatie over het maken en configureren van een map voor cloudserviceconfiguraties.

1. Tikken **[!UICONTROL Create]** om de **[!UICONTROL Create Data Source Configuration wizard]**. Geef een naam en eventueel een titel voor de configuratie op. Selecteer **[!UICONTROL OData Service]** van de **[!UICONTROL Service Type]** keuzelijst, bladert u optioneel naar een miniatuurafbeelding voor de configuratie en tikt u op **[!UICONTROL Next]**.
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het authentificatietype ??? niets, OAuth2.0, Basisauthentificatie, API Sleutel, of de Authentificatie van de Douane ??? om tot de dienst toegang te hebben OData, en dienovereenkomstig de details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** Geef als verificatietype de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in het menu **[!UICONTROL Location]** vervolgkeuzelijst en geef de naam van de header of de parameter query op in de **[!UICONTROL Parameter Name]** veld dienovereenkomstig.

   >[!NOTE]
   >
   >U moet OAuth 2.0 authentificatietype selecteren om met te verbinden [!DNL Microsoft Dynamics] diensten die eindpunt OData als de dienstwortel gebruiken.

1. Tikken **[!UICONTROL Create]** om de wolkenconfiguratie voor de dienst te cre??ren OData.

<!--## Certificate-based mutual authentication for RESTful and SOAP web services {#mutual-authentication}

When you enable mutual authentication for form data model, both the data source and [!DNL Experience Manager] Server running Form Data Model authenticate each other???s identity before sharing any data. You can use mutual authentication for REST and SOAP-based connections (data sources). To configure mutual authentication for a Form Data Model on your [!DNL Experience Manager Forms] environment:

1. Upload the private key (certificate) to [!DNL Experience Manager Forms] server. To upload the private key:
   1. Log in to your [!DNL Experience Manager Forms] server as an administrator.
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**. Select the `fd-cloudservice` user and tap **[!UICONTROL Properties]**.
   1. Open the **[!UICONTROL Keystore]** tab, expand the **[!UICONTROL Add Private Key from KeyStore file]** option, upload the KeyStore File, specify the aliases, passwords, and tap **[!UICONTROL Submit]**. The Certificate is uploaded.  The private key alias is mentioned in the certificate and set while creating the certificate.
1. Upload trust certificate to Global Trust Store. To upload the certificate:
   1. Navigate to **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]**.
   1. Expand the **[!UICONTROL Add Certificate from CER file]** option, tap **[!UICONTROL Select Certificate File]**, upload the certificate, and tap **[!UICONTROL Submit]**.
1. Configure [SOAP](#configure-soap-web-services) or [RESTful](#configure-restful-web-services) web services as the data source and select **[!UICONTROL Mutual authentication]** as the authentication type. If you configure multiple self-signed certificates for `fd-cloudservice` user, specify the Key Alias name for the certificate.-->

## Volgende stappen {#next-steps}

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een formuliergegevensmodel maken of als u al een formuliergegevensmodel zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de gegevensbronnen die u zojuist hebt geconfigureerd. Zie [Formuliergegevensmodel maken](create-form-data-models.md) voor meer informatie.
