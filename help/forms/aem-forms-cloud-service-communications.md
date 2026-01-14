---
title: Hoe kan Forms as a Cloud Service gebruiken om gegevens samen te voegen met XDP- en PDF-sjablonen of om uitvoer te genereren in PCL-, ZPL- en PostScript-indelingen?
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
feature: Adaptive Forms,APIs & Integrations
role: Admin, Developer, User
source-git-commit: 43b648eb3984867fda35ee04de10b78dd836b481
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# Synchrone verwerking gebruiken {#sync-processing-introduction}

Forms as a Cloud Service - Met communicatie-API&#39;s kunt u merkgeoriënteerde en gepersonaliseerde communicatie maken, samenstellen en leveren, zoals zakelijke correspondentie, documenten, instructies, aanvraagverwerkingsbrieven, aankondigingen van voordelen, claimverwerkingsbrieven, maandelijkse facturen en welkomstkits. Met communicatie-API&#39;s kunt u een sjabloon (XFA of PDF) combineren met klantgegevens om documenten te genereren in de indelingen PDF, PS, PCL, DPL, IPL en ZPL.

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt. U kunt communicatie-API&#39;s gebruiken om een afdrukdocument te genereren voor elke record. <!-- You can also combine the records into a single document. --> Het resultaat is een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de bijbehorende velden.

Forms as a Cloud Service - Communications biedt op aanvraag API&#39;s (asynchrone API&#39;s) voor het genereren van geplande documenten:

* Synchrone API&#39;s zijn geschikt voor gebruik op aanvraag, met lage latentie en het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op handelingen van gebruikers. Het genereren van een document bijvoorbeeld nadat een gebruiker een formulier heeft ingevuld.

* Batch-API&#39;s (Asynchrone API&#39;s) zijn geschikt voor geplande toepassingen waarbij meerdere documenten met hoge doorvoer worden gegenereerd. Met deze API&#39;s worden documenten batchgewijs gegenereerd. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Synchrone bewerkingen gebruiken {#batch-operations}

Een synchrone bewerking is een proces waarbij documenten lineair worden gegenereerd. Deze API&#39;s worden geclassificeerd als API&#39;s voor één gebruiker en API&#39;s voor meerdere gebruikers:

### API&#39;s voor één gebruiker

* API&#39;s voor het genereren van documenten
* Documentmanipulatie-API&#39;s

<!-- 
### Multi-tenant APIs

* Document utility APIs -->


### Verifieer enig-huurder API

API-bewerkingen van één gebruiker ondersteunen twee verificatietypen:

* **Basisauthentificatie**: De basisauthentificatie is een eenvoudige authentificatieregeling die in het protocol van HTTP wordt gebouwd. De cliënt verzendt HTTP- verzoeken met de kopbal van de Vergunning die het woord Basis bevat dat door een ruimte en een base64-gecodeerde koordgebruikersbenaming :password wordt gevolgd. Bijvoorbeeld, om als admin/admin toe te staan verzendt de cliënt Basis [ base64-gecodeerde koordgebruikersbenaming ]: [ base64-gecodeerde koordwachtwoord ].

* **op token-gebaseerde authentificatie:** Op token-gebaseerde authentificatie gebruikt een toegangstoken (het teken van de authentificatie van de Drager) om verzoeken aan Experience Manager as a Cloud Service te doen. AEM Forms as a Cloud Service biedt API&#39;s om het toegangstoken veilig op te halen. Om het teken terug te winnen en te gebruiken om een verzoek voor authentiek te verklaren:

   1. [ wint de credentie van Experience Manager as a Cloud Service van Developer Console ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html) terug.
   1. [ installeer de credentie van Experience Manager as a Cloud Service op uw milieu ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (De Server van de Toepassing, de Server van het Web, of andere servers niet-AEM) die worden gevormd om verzoeken naar (maken vraag) de wolkendienst te verzenden.
   1. [ produceer een teken JWT en ruilde het met Adobe IMS APIs voor een toegangstoken ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Voer de Experience Manager API met het toegangstoken als token voor Dragerverificatie uit.
   1. [ plaats aangewezen toestemmingen voor de technische rekeningsgebruiker in het milieu van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

  >[!NOTE]
  >
  >Adobe raadt aan tokenverificatie te gebruiken in een productieomgeving.

  >[!IMPORTANT]
  >
  > Voor meer informatie, zie [ OAuth server-aan-server authentificatie ](/help/forms/oauth-api-authetication.md) en [ server-aan-server authentificatie JWT ](/help/forms/jwt-api-authentication.md).
<!-- 

### Authenticate a multi-tenant API

#### Authentication Headers

Every inbound HTTP API call to the multi-tenant API must contain these three headers:


* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

The values which should be sent in the `x-api-key` and `x-gw-ims-org-id` headers are provided in the Credentials details screen in the [Adobe Developer Console](https://developer.adobe.com/console). The value of the `x-api-key` header is the Client ID and the value for the `x-gw-ims-org-id` header is the Organization ID.

#### Configure Adobe Developer console to generate an access token

To set up authentication APIs, create a project in Adobe Developer Console and add Communication APIs to the project on Adobe Developer Console. The integration generates API Key, Client Secret, Payload (JWT):

1. Contact you Adobe Developer Console administrator. Ask the administrator to add as a developer.
1. Log in to `https://developer.adobe.com/console/`. Use your developer account that your administrator has provisioned to log in to Adobe Developer Console.
1. Select your organization from the top-right corner. If you do not know your organization, contact your administrator.
1. Select **[!UICONTROL Create new project]**. A screen to get started with your new project appears. Select **[!UICONTROL Add API]**. A screen with list of all the APIs enabled for your account appears.
1. Select **[!UICONTROL AEM Forms - Communications]** and select **[!UICONTROL Next]**. A screen to configure the API appears.
1. Select **[!UICONTROL OPTION 1 Generate a key pair]** and select **[!UICONTROL Generate keypair]**. It creates and downloads the configuration file. The downloaded configuration file contains all your app settings, along with the only copy of your private key. Adobe does not record your private key, make sure to securely store the downloaded file. Select **[!UICONTROL Next]**.
1. Select **[!UICONTROL Integrations - Cloud Service]** and select **[!UICONTROL Save configured API]**. Select **[!UICONTROL Service Account (JWT)]** to view the API Key, Client Secret, and other information required to access the APIs. You set to use the token to access the APIs.

#### Programmatically generate and use an access token

To programmatically generate an access token, generate a JSON Web Token (JWT) and exchange it with the Adobe Identity Management Service (IMS) for an access token.

Use the following keys, referred to as claims, to construct JWT JSON object:


* `exp`- the requested expiration of the access token, expressed as several seconds since January 1, 1970 GMT. For most use cases, this is a relatively small value. For example, 5 minutes, for five minutes from now, this value should be 1670923791.
* `iss` - the Organization ID from the Adobe Developer Console project, in the format org_ident@AdobeOrg.
* `sub` - the Technical Account ID from the Adobe Developer Console integration, in the format: id@techacct.adobe.com.
* `aud` - the Client ID from the Adobe Developer Console integration prepended with `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - set to the literal value `true`

This JSON object must be then base64 encoded and signed using the private key for the project. Finally, the encoded value is sent in the body of a POST request to `https://ims-na1.adobelogin.com/ims/exchange/jwt` along with the Client ID and Client Secret for the project.

##### Example

```JSON

    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache

```

#### Language Support for JWT

While it is possible to do the entire JWT generation and exchange process in custom code, it is more common to use a higher-level library to do so. A number of such libraries are listed on the [Adobe I/O JWT Documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

-->

### (Alleen voor API&#39;s voor documentgeneratie) Elementen en machtigingen configureren

Voor het gebruik van synchrone API&#39;s is het volgende vereist:

* Gebruikers met Experience Manager-beheerdersrechten
* Sjablonen en andere elementen uploaden naar uw Experience Manager Forms Cloud Service-exemplaar

### (Alleen voor API&#39;s voor documentgeneratie) Sjablonen en andere middelen uploaden naar uw Experience Manager-instantie

Een organisatie heeft doorgaans meerdere sjablonen. Bijvoorbeeld, één malplaatje elk voor creditcardverklaringen, voordelenverklaringen, en claimtoepassingen. Upload dergelijke XDP- en PDF-sjablonen naar uw Experience Manager-exemplaar. Een sjabloon uploaden:

1. Open je Experience Manager-exemplaar.
1. Ga naar Forms > Forms en Documenten
1. Klik op Maken > Map en maak een map. Open de map.
1. Klik op Maken > Bestand uploaden en upload de sjablonen.

### Een API aanroepen

De [ API verwijzingsdocumentatie ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie biedt ook een API-definitiebestand in de indeling .yaml. U kunt het .yaml dossier downloaden en het uploaden aan [ Postman ](https://www.postman.com/) om functionaliteit van APIs te controleren.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
> Leer de gedetailleerde stappen om Communicatie APIs van AEM Forms aan te halen, zie [ de Communicatie APIs van AEM Forms aanhalen gebruikend het Server-aan-Server 1} artikel van de Authentificatie van OAuth.](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)

>[!MORELIKETHIS]
>
>* [ Inleiding aan de Mededelingen van AEM Forms as a Cloud Service ](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [ de Architectuur van as a Cloud Service van AEM Forms voor Adaptieve Forms en Communicatie APIs ](/help/forms/aem-forms-cloud-service-architecture.md)
>* [ Communicatie Verwerking - Synchrone APIs ](/help/forms/aem-forms-cloud-service-communications.md)
>* [ Communicatie Verwerking - Partij APIs ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [ Communicatie API van Forms - Leerprogramma ](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)