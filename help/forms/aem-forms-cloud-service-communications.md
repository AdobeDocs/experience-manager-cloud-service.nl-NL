---
title: Hoe te om Forms as a Cloud Service te gebruiken om gegevens met malplaatjes samen te voegen XDP en PDF of output in PCL, ZPL, en de formaten van PostScript te produceren?
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
feature: Adaptive Forms,APIs & Integrations
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---


# Synchrone verwerking gebruiken {#sync-processing-introduction}

Met Forms as a Cloud Service - Communicatie-API&#39;s kunt u merkgeoriënteerde en gepersonaliseerde communicatie maken, samenstellen en leveren, zoals zakelijke correspondentie, documenten, instructies, aanvraagverwerkingsbrieven, aankondigingen van voordelen, aanvraagverwerkingsbrieven, maandelijkse facturen en welkomstkits. U kunt Communicatie APIs gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, DPL, IPL, en ZPL formaten te produceren.

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt. U kunt communicatie-API&#39;s gebruiken om een afdrukdocument te genereren voor elke record. <!-- You can also combine the records into a single document. --> Het resultaat is een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de desbetreffende velden.

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

* **Basisverificatie**: De basisauthentificatie is een eenvoudige authentificatieregeling die in het protocol van HTTP wordt gebouwd. De client verzendt HTTP-aanvragen met de machtigingsheader die het woord Basic bevat, gevolgd door een spatie en een base64-coded tekenreeks username:password. Als u bijvoorbeeld autoriseert als beheerder/beheerder, verzendt de client Basic [base64-coded string username]: [base64-coded string password].

* **Tokengebaseerde verificatie:** De op token-gebaseerde authentificatie gebruikt een toegangstoken (het teken van de authentificatie van de Drager) om verzoeken aan Experience Manager as a Cloud Service te maken. AEM Forms as a Cloud Service verstrekt APIs om het toegangstoken veilig terug te winnen. Om het teken terug te winnen en te gebruiken om een verzoek voor authentiek te verklaren:

   1. [As a Cloud Service referentie van Experience Manager ophalen uit de Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [Installeer de as a Cloud Service credentie van de Experience Manager op uw milieu](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (De Server van de Toepassing, de Server van het Web, of andere niet-AEM servers) die worden gevormd om verzoeken naar (maken vraag) de wolkendienst te verzenden.
   1. [Een JWT-token genereren en deze uitgewisseld met Adobe IMS API&#39;s voor een toegangstoken](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Voer de Experience Manager-API met het toegangstoken uit als een token voor Dragerverificatie.
   1. [Stel de juiste machtigingen in voor de gebruiker van de technische account in de Experience Manager-omgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

  >[!NOTE]
  >
  >Adobe raadt aan tokengebaseerde verificatie op een productieomgeving te gebruiken.

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

* Gebruikers met beheerdersrechten voor Experience Managers
* Sjablonen en andere elementen uploaden naar uw Experience Manager Forms Cloud Service-exemplaar

### (Alleen voor API&#39;s voor documentgeneratie) Sjablonen en andere elementen uploaden naar uw Experience Manager-instantie

Een organisatie heeft doorgaans meerdere sjablonen. Bijvoorbeeld, één malplaatje elk voor creditcardverklaringen, voordelenverklaringen, en claimtoepassingen. Upload al dergelijke XDP en PDF malplaatjes aan uw instantie van de Experience Manager. Een sjabloon uploaden:

1. Open een Experience Manager-instantie.
1. Ga naar Forms > Forms en Documenten
1. Klik op Maken > Map en maak een map. Open de map.
1. Klik op Maken > Bestand uploaden en upload de sjablonen.

### Een API aanroepen

De [API-naslagdocumentatie](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) verstrekt gedetailleerde informatie over alle parameters, authentificatiemethodes, en diverse diensten die door APIs worden verleend. De API-naslagdocumentatie biedt ook een API-definitiebestand in de indeling .yaml. U kunt het .yaml-bestand downloaden en uploaden naar [Postman](https://www.postman.com/) om de functionaliteit van de API&#39;s te controleren.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Alleen leden van een groep met formuliergebruikers hebben toegang tot communicatie-API&#39;s.

>[!MORELIKETHIS]
>
>* [Inleiding tot AEM Forms as a Cloud Service Communications](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service architectuur voor adaptieve Forms- en communicatie-API&#39;s](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Communicatieverwerking - synchrone API&#39;s](/help/forms/aem-forms-cloud-service-communications.md)
>* [Communicatieverwerking - Batch-API&#39;s](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)