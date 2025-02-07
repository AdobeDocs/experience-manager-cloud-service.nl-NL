---
title: Hoe te om Gegevensbronnen te vormen?
description: Leer hoe te om RESTful Webdiensten, op SOAP-gebaseerde Webdiensten, en de diensten van OData als gegevensbronnen voor een model van vormgegevens (FDM) te vormen.
feature: Adaptive Forms, Form Data Model
role: User, Developer
level: Beginner
exl-id: cb77a840-d705-4406-a94d-c85a6efc8f5d
source-git-commit: c20b8909bb884f14bd7fe59f190de3cd375a7111
workflow-type: tm+mt
source-wordcount: '2144'
ht-degree: 0%

---


# Gegevensbronnen configureren {#configure-data-sources}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/form-data-model/configure-data-sources.html) |
| AEM as a Cloud Service | Dit artikel |

![ de integratie van Gegevens ](do-not-localize/data-integeration.png)

[!DNL Experience Manager Forms] Met gegevensintegratie kunt u verschillende gegevensbronnen configureren en verbinden. De volgende typen worden buiten de box ondersteund:

* Relationele databases - MySQL, [!DNL Microsoft® SQL Server], [!DNL IBM® DB2®] , postgreSQL en [!DNL Oracle RDBMS]
* RESTful-webservices
* SOAP webservices
* OData-diensten (versie 4.0)
* Microsoft® Dynamics
* Salesforce
* Microsoft® Azure Blob Storage

De integratie van gegevens steunt OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), Basisauthentificatie, en API Zeer belangrijke authentificatietypen uit-van-de-doos, en staat het uitvoeren van douaneauthentificatie voor de toegang tot van de Webdiensten toe. Terwijl RESTful, SOAP-gebaseerde, en OData de diensten in [!DNL Experience Manager] as a Cloud Service worden gevormd, worden JDBC voor relationele gegevensbestanden en schakelaar voor [!DNL Experience Manager] gebruikersprofiel gevormd in [!DNL Experience Manager] Webconsole.

## Relationele database configureren {#configure-relational-database}

### Vereisten

Voordat u relationele databases configureert met gebruik van de [!DNL Experience Manager] webconsoleconfiguratie, moet u:
* [ laat geavanceerd voorzien van een netwerk door wolkenmanager API ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/advanced-networking.html) toe, aangezien de havens door gebrek worden onbruikbaar gemaakt.
* [ voeg JDBC bestuurdersgebiedsdelen in Geweven ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html?lang=en#mysql-driver-dependencies) toe.


### Stappen om een relationele database te configureren

U kunt relationele databases configureren met [!DNL Experience Manager] Web Console Configuration. Ga als volgt te werk:

1. Ga naar [!DNL Experience Manager] webconsole op `https://server:host/system/console/configMgr` .
1. Zoek **[!UICONTROL Day Commons JDBC Connections Pools]** -configuratie. Selecteer deze optie om de configuratie te openen in de bewerkingsmodus.

   ![ JDBC Connector Pool ](/help/forms/assets/jdbc_connector.png)

1. In de configuratiedialoog, specificeer de details voor het gegevensbestand u, zoals wilt vormen:

   * Java™-klassenaam voor het JDBC-stuurprogramma
   * URI voor JDBC-verbinding
   * Gebruikersnaam en wachtwoord voor verbinding met het JDBC-stuurprogramma
   * Geef een SQL SELECT-query op in het veld **[!UICONTROL Validation Query]** om verbindingen vanuit de pool te valideren. De query moet ten minste één rij retourneren. Geef op basis van uw database een van de volgende opties op:
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
   > Zie [ SQL verbindingen gebruikend JDBC DataSourcePool ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/networking/examples/sql-datasourcepool.html) voor meer gedetailleerde informatie.

1. Selecteer **[!UICONTROL Save]** om de configuratie op te slaan.

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

Alle configuraties van de cloudservice in [!DNL Experience Manager] worden geconsolideerd in de `/conf` -map in de [!DNL Experience Manager] -opslagplaats. Standaard bevat de map `conf` de map `global` waarin u cloudserviceconfiguraties kunt maken. U moet deze optie echter handmatig inschakelen voor cloudconfiguraties. U kunt ook extra mappen maken in `conf` om configuraties voor cloudservices te maken en in te delen.

De map configureren voor configuraties van cloudservices:

1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   * Zie Browser van de Configuratie ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/introduction/configurations.html) documentatie 0} {voor meer informatie.[
1. Ga als volgt te werk om de algemene map voor cloudconfiguraties in te schakelen of sla deze stap over om een andere map voor cloudserviceconfiguraties te maken en te configureren.

   1. Selecteer in **[!UICONTROL Configuration Browser]** de map `global` en selecteer **[!UICONTROL Properties]** .

   1. Schakel **[!UICONTROL Cloud Configurations]** in het dialoogvenster **[!UICONTROL Configuration Properties]** in.

   1. Selecteer **[!UICONTROL Save & Close]** om de configuratie op te slaan en het dialoogvenster af te sluiten.

1. Selecteer **[!UICONTROL Create]** in de **[!UICONTROL Configuration Browser]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een titel op voor de map en schakel **[!UICONTROL Cloud Configurations]** in.
1. Selecteer **[!UICONTROL Create]** om de map te maken die is ingeschakeld voor cloudserviceconfiguraties.

## RESTful-webservices configureren {#configure-restful-web-services}

De RESTful Webdiensten kunnen worden beschreven gebruikend [ de specificaties van de Wagger ](https://swagger.io/specification/v2/) in formaat JSON of YAML in a [!DNL Swagger] definitiedossier of een Eindpunt van de Dienst.

>[!NOTE]
> Om RESTful Webdienst in [!DNL Experience Manager] as a Cloud Service te vormen, zorg ervoor dat u of het [!DNL Swagger] dossier ([ Versie 2.0 van de Tagger ](https://swagger.io/specification/v2/)) of [!DNL Swagger] dossier ([ Versie van de Wagger 3.0 ](https://swagger.io/specification/v3/)) op uw dossiersysteem of URL hebt waar het dossier wordt ontvangen.

### RESTful-services configureren voor Open API Specification versie 2.0 {#configure-restful-services-open-api-2.0}

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer een URL of een Dossier van [!UICONTROL Swagger Source] drop-down, en specificeer dienovereenkomstig [!DNL Swagger URL] aan het [!DNL  Swagger] definitiedossier of upload het [!DNL Swagger] dossier van uw lokaal dossiersysteem.
   * Gebaseerd op de [!DNL  Swagger] input van Source., zijn de volgende gebieden pre-bevolkt met waarden:

      * Schema: de overdrachtprotocollen die door de REST API worden gebruikt. Het aantal schematypen dat in de drop-down lijst wordt getoond hangt van de regelingen af die in de [!DNL Swagger] bron worden bepaald.
      * Host: de domeinnaam of het IP-adres van de host die de REST API aanbiedt. Het is een verplicht veld.
      * Basispad: het URL-voorvoegsel voor alle API-paden. Het is een optioneel veld.\
        Bewerk indien nodig de vooraf ingevulde waarden voor deze velden.

   * Selecteer het authentificatietype — niets, OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), BasisAuthentificatie, API Sleutel, of de Authentificatie van de Douane — om tot de RESTful dienst toegang te hebben, en dienovereenkomstig details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** selecteert als verificatietype, geeft u de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Location]** en geef de naam van de header of de queryparameter dienovereenkomstig op in het veld **[!UICONTROL Parameter Name]** .

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteer **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst tot stand te brengen.

### RESTful-services configureren voor Open API Specification versie 3.0 {#configure-restful-services-open-api-3.0}

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Specificeer de volgende details voor de RESTful dienst:

   * Selecteer een URL of een Dossier van [!UICONTROL Swagger Source] drop-down, en specificeer dienovereenkomstig [!DNL Swagger 3.0 URL] aan het [!DNL  Swagger] definitiedossier of upload het [!DNL Swagger] dossier van uw lokaal dossiersysteem.
   * Gebaseerd op de [!DNL  Swagger] input van Source, wordt de verbindingsinformatie met de doelserver getoond.
   * Selecteer het authentificatietype — niets, OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), BasisAuthentificatie, API Sleutel, of de Authentificatie van de Douane — om tot de RESTful dienst toegang te hebben, en dienovereenkomstig details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** selecteert als verificatietype, geeft u de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Location]** en geef de naam van de header of de queryparameter dienovereenkomstig op in het veld **[!UICONTROL Parameter Name]** .

   <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteer **[!UICONTROL Create]** om de wolkenconfiguratie voor de RESTful dienst tot stand te brengen.

Sommige bewerkingen die niet worden ondersteund door RESTful-services Open API Specification versie 3.0 zijn:
* Callbacks
* één of meer
* Externe referentie
* Koppelingen
* Verschillende aanvraagorganen voor verschillende MIME-typen voor één enkele bewerking

Zie [ 3.0 Specificatie OpenAPI ](https://swagger.io/specification/v3/) voor gedetailleerde informatie.

### Vorm de diensten RESTful gebruikend de Eindpunt van de Dienst {#configure-restful-services-service-endpoint}

<span class="preview"> De service-eindpuntfunctionaliteit valt onder het programma Vroege adopter en is alleen van toepassing op kerncomponenten. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen.

1. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL RESTful Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .

1. Selecteer op de volgende pagina **[!UICONTROL Service Endpoint]** in de **[!UICONTROL RESTful Service dropdown]** .

   ![ Eindpunt van de Dienst ](/help/forms/assets/select-service-endpoint.png)

1. Geef **[!UICONTROL Service Endpoint URL]** op.

   >[!NOTE]
   > Standaard is Type methode POST.
1. Selecteer een van de inhoudstypen die u wilt kiezen in de vervolgkeuzelijst. Inhoudstypen zijn uit meerdere delen bestaande formuliergegevens, JSON- en URL-codering (Key-Value-paar).
1. Nu selecteert u om het even welk van het Type van Authentificatie zoals OAuth 2.0, Basisauthentificatie, Sleutel API, de Authentificatie van de Douane, van de drop-down lijst.
   ![ de authentificatietype van het Eindpunt van de Dienst ](/help/forms/assets/service-endpoint-authtype.png)
1. Klik op Maken.

### De cliëntconfiguratie van HTTP van het het gegevensmodel van de vorm (FDM) om prestaties te optimaliseren {#fdm-http-client-configuration}

[!DNL Experience Manager Forms] vormen een gegevensmodel wanneer het integreren met RESTful Webdiensten aangezien de gegevensbron de cliëntconfiguraties van HTTP voor prestatiesoptimalisering omvat.

Stel de volgende eigenschappen van de **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]** -configuratie in om de reguliere expressie op te geven:

* Gebruik de eigenschap `http.connection.max.per.route` om het maximum aantal toegestane verbindingen tussen het formuliergegevensmodel (FDM) en RESTful-webservices in te stellen. De standaardwaarde is 20 verbindingen.

* Gebruik de eigenschap `http.connection.max` om het maximum aantal toegestane verbindingen voor elke route op te geven. De standaardwaarde is 40 verbindingen.

* Gebruik de eigenschap `http.connection.keep.alive.duration` om de duur op te geven waarvoor een blijvende HTTP-verbinding in leven blijft. De standaardwaarde is 15 seconden.

* Gebruik de eigenschap `http.connection.timeout` om de duur op te geven waarvoor de [!DNL Experience Manager Forms] -server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

* Gebruik de eigenschap `http.socket.timeout` om de maximale tijdsperiode voor inactiviteit tussen twee gegevenspakketten op te geven. De standaardwaarde is 30 seconden.

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

1. Selecteer **[!UICONTROL Form Data Model HTTP Client Configuration for REST data source]** .

1. In het dialoogvenster [!UICONTROL Form Data Model HTTP Client Configuration for REST data source] :

   * Geef het maximale aantal toegestane verbindingen op tussen het formuliergegevensmodel (FDM) en de RESTful-webservices in het veld **[!UICONTROL Connection limit in total]** . De standaardwaarde is 20 verbindingen.

   * Geef het maximale aantal toegestane verbindingen voor elke route op in het veld **[!UICONTROL Connection limit on per route basis]** . De standaardwaarde is twee verbindingen.

   * Geef in het veld **[!UICONTROL Keep alive]** de duur op waarvoor een permanente HTTP-verbinding in leven blijft. De standaardwaarde is 15 seconden.

   * Geef in het veld **[!UICONTROL Connection timeout]** de tijdsduur op waarvoor de [!DNL Experience Manager Forms] -server wacht tot een verbinding tot stand is gebracht. De standaardwaarde is 10 seconden.

   * Geef in het veld **[!UICONTROL Socket timeout]** de maximale periode voor inactiviteit op tussen twee gegevenspakketten. De standaardwaarde is 30 seconden.

## Webservices configureren SOAP {#configure-soap-web-services}

Op SOAP gebaseerde Webdiensten worden beschreven gebruikend {de specificaties van de Beschrijving van de Diensten van het Web van 0} van de Taal (WSDL) ](https://www.w3.org/TR/wsdl). [ [!DNL Experience Manager Forms] biedt geen ondersteuning voor het WSDL-model in RPC-stijl.

Als u in [!DNL Experience Manager] as a Cloud Service op SOAP gebaseerde webservice wilt configureren, controleert u of u de WSDL-URL voor de webservice hebt en voert u de volgende handelingen uit:

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](configure-data-sources.md#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL SOAP Web Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Geef het volgende op voor de SOAP webservice:

   * WSDL-URL voor de webservice.
   * Service Endpoint. Specificeer een waarde op dit gebied om het de diensteindpunt met voeten te treden dat in WSDL wordt vermeld.
   * Selecteer het authentificatietype — niets, OAuth2.0 ([ Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), BasisAuthentificatie, of de Authentificatie van de Douane — om tot de SOAP dienst toegang te hebben, en dienovereenkomstig de details voor authentificatie te verstrekken.

     <!--If you select **[!UICONTROL X509 Token]** as the Authentication type, configure the X509 certificate. For more information, see [Set up certificates](install-configure-document-services.md#set-up-certificates-for-reader-extension-and-encryption-service).-->
     <!--Specify the KeyStore alias for the X509 certificate in the **[!UICONTROL Key Alias]** field. Specify the time, in seconds, until the authentication request remains valid, in the **[!UICONTROL Time To Live]** field. Optionally, select to sign the message body or timestamp header or both.-->

     <!--If you select **[!UICONTROL Mutual Authentication]** as the authentication type, see [Certificate-based mutual authentication for RESTful and SOAP web services](#mutual-authentication).-->

1. Selecteer **[!UICONTROL Create]** om de cloudconfiguratie voor de SOAP webservice te maken.

### Het gebruik van importinstructies in SOAP webservices WSDL inschakelen {#enable-import-statements}

U kunt een reguliere expressie opgeven die fungeert als filter voor absolute URL&#39;s die zijn toegestaan als importinstructies in SOAP WSDL voor webservices. Standaard is er geen waarde in dit veld. Hierdoor blokkeert [!DNL Experience Manager] alle importinstructies die beschikbaar zijn in WSDL. Als u `.*` opgeeft als waarde in dit veld, staat [!DNL Experience Manager] alle instructies import toe.

Stel de eigenschap `importAllowlistPattern` van de **[!UICONTROL Form Data Model SOAP Web Services Import Allowlist]** -configuratie in om de reguliere expressie op te geven. In het volgende JSON-bestand wordt een voorbeeld weergegeven:

```json
{
  "importAllowlistPattern": ".*"
}
```

Om waarden van een configuratie te plaatsen, [ produceer OSGi Configuraties gebruikend de AEM SDK ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [ stel de configuratie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) aan uw instantie van de Cloud Service op.

## OData-services configureren {#config-odata}

De dienst OData wordt geïdentificeerd door zijn de dienstwortel URL. Als u een OData-service in [!DNL Experience Manager] as a Cloud Service wilt configureren, moet u ervoor zorgen dat u over de servicebasis-URL voor de service beschikt en moet u het volgende doen:

>[!NOTE]
>
> Het gegevensmodel van de vorm (FDM) steunt [ OData versie 4 ](https://www.odata.org/documentation/).
>Voor een geleidelijke gids om [!DNL Microsoft®® Dynamics 365], online of op-gebouw te vormen, zie [[!DNL Microsoft® Dynamics]  Configuratie OData ](ms-dynamics-odata-configuration.md).

1. Ga naar **[!UICONTROL Tools > Cloud Services > Data Sources]** . Selecteer deze optie om de map te selecteren waarin u een cloudconfiguratie wilt maken.

   Zie [ omslag voor de configuraties van de wolkendienst ](#cloud-folder) voor informatie over het creëren van en het vormen van een omslag voor de configuraties van de wolkendienst vormen.

1. Selecteer **[!UICONTROL Create]** om **[!UICONTROL Create Data Source Configuration wizard]** te openen. Geef een naam en eventueel een titel voor de configuratie op, selecteer **[!UICONTROL OData Service]** in de vervolgkeuzelijst **[!UICONTROL Service Type]** , blader optioneel naar een miniatuurafbeelding en selecteer een miniatuurafbeelding voor de configuratie en selecteer **[!UICONTROL Next]** .
1. Specificeer de volgende details voor de dienst OData:

   * Service Root URL voor de OData-service die moet worden geconfigureerd.
   * Selecteer het authentificatietype — niets, OAuth2.0 ([ de Code van de Vergunning ](https://oauth.net/2/grant-types/authorization-code/), [ de Verantwoordelijkheden van de Cliënt ](https://oauth.net/2/grant-types/client-credentials/)), BasisAuthentificatie, Sleutel API, of de Authentificatie van de Douane — om tot de dienst toegang te hebben OData, en dienovereenkomstig de details voor authentificatie te verstrekken.

   Als u **[!UICONTROL API Key]** selecteert als verificatietype, geeft u de waarde voor de API-sleutel op. De API-sleutel kan als aanvraagheader of als queryparameter worden verzonden. Selecteer een van deze opties in de vervolgkeuzelijst **[!UICONTROL Location]** en geef de naam van de header of de queryparameter dienovereenkomstig op in het veld **[!UICONTROL Parameter Name]** .

   >[!NOTE]
   >
   >Selecteer het OAuth 2.0 authentificatietype om met [!DNL Microsoft®® Dynamics] diensten te verbinden gebruikend het eindpunt OData als de dienstwortel.

1. Selecteer **[!UICONTROL Create]** om de wolkenconfiguratie voor de dienst te creëren OData.

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

U hebt de gegevensbronnen geconfigureerd. Vervolgens kunt u een FDM (Form Data Model) maken of als u al een FDM (Form Data Model) zonder gegevensbron hebt gemaakt, kunt u dit koppelen aan de gegevensbronnen die u hebt geconfigureerd. Zie [ het model van vormgegevens ](create-form-data-models.md) voor details creëren.

<!--

>[!MORELIKETHIS]
>
>* [Configure Azure storage for AEM Forms](/help/forms/configure-azure-storage.md)
>* [Integrate Microsoft Dynamics 365 and Salesforce with Adaptive Forms](/help/forms/configure-msdynamics-salesforce.md)
>*  [Add Forms Portal to an AEM Sites page](/help/forms/configure-forms-portal.md)

-->