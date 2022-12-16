---
title: AEM Forms as a Cloud Service - Communicatie
description: Automatisch gegevens samenvoegen met XDP- en PDF-sjablonen of uitvoer genereren in PCL-, ZPL- en PostScript-indelingen
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1177'
ht-degree: 1%

---


# Synchrone verwerking gebruiken {#sync-processing-introduction}

Forms as a Cloud Service - Communicatie APIs staat u toe om, merkgeoriënteerde en gepersonaliseerde mededelingen tot stand te brengen samen te stellen en te leveren zoals bedrijfscorrespondentie, documenten, verklaringen, claimverwerkingsbrieven, voordeelberichten, claimverwerkingsbrieven, maandelijkse rekeningen, en welkomstkits. U kunt Communicatie APIs gebruiken om een malplaatje (XFA of PDF) met klantengegevens te combineren om documenten in PDF, PS, PCL, DPL, IPL, en ZPL formaten te produceren.

Overweeg een scenario waar u één of meerdere malplaatjes en veelvoudige verslagen van de gegevens van XML voor elke malplaatje hebt. U kunt communicatie-API&#39;s gebruiken om een afdrukdocument te genereren voor elke record. <!-- You can also combine the records into a single document. --> Het resultaat is een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de desbetreffende velden.

Forms as a Cloud Service - Communications biedt API&#39;s (asynchrone API&#39;s) op aanvraag en in batch voor het genereren van geplande documenten:

* Synchrone API&#39;s zijn geschikt voor gebruik op aanvraag, met lage latentie en het genereren van documenten met één record. Deze API&#39;s zijn geschikter voor gebruiksgevallen die zijn gebaseerd op gebruikersacties. Het genereren van een document bijvoorbeeld nadat een gebruiker een formulier heeft ingevuld.

* Batch-API&#39;s (Asynchrone API&#39;s) zijn geschikt voor geplande toepassingen waarbij meerdere documenten met hoge doorvoer worden gegenereerd. Deze API&#39;s genereren documenten batchgewijs. Zo worden telefoonrekeningen, creditcardafschriften en uitkeringsafschriften elke maand gegenereerd.

## Synchrone bewerkingen gebruiken {#batch-operations}

Een synchrone bewerking is een proces waarbij documenten lineair worden gegenereerd. Deze API&#39;s worden geclassificeerd als API&#39;s voor één gebruiker en API&#39;s voor meerdere gebruikers:

### API&#39;s voor één gebruiker

* API&#39;s voor het genereren van documenten
* Documentmanipulatie-API&#39;s

### API&#39;s voor meerdere workers

* Hulpprogramma-API&#39;s voor documenten

### Verifieer enig-huurder API

API-bewerkingen van één gebruiker ondersteunen twee verificatietypen:

* **Basisverificatie**: De basisauthentificatie is een eenvoudige authentificatieregeling die in het protocol van HTTP wordt gebouwd. De client verzendt HTTP-aanvragen met de machtigingsheader die het woord Basic bevat, gevolgd door een spatie en een base64-coded tekenreeks username:password. Als u bijvoorbeeld autoriseert als beheerder/beheerder, verzendt de client Basic [base64-coded string username]: [base64-gecodeerd tekenreekswachtwoord].

* **Tokengebaseerde verificatie:** De op token-gebaseerde authentificatie gebruikt een toegangstoken (het teken van de authentificatie van de Drager) om verzoeken aan Experience Manager as a Cloud Service te maken. AEM Forms as a Cloud Service verstrekt APIs om het toegangstoken veilig terug te winnen. Om het teken terug te winnen en te gebruiken om een verzoek voor authentiek te verklaren:

   1. [as a Cloud Service referentie van Experience Manager ophalen uit de ontwikkelaarsconsole](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [Installeer de as a Cloud Service credentie van de Experience Manager op uw milieu](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (De Server van de Toepassing, de Server van het Web, of andere niet-AEM servers) die worden gevormd om verzoeken naar (maken vraag) de wolkendienst te verzenden.
   1. [Een JWT-token genereren en deze uitgewisseld met Adobe IMS API&#39;s voor een toegangstoken](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Voer de Experience Manager-API met het toegangstoken uit als een token voor Dragerverificatie.
   1. [Stel de juiste machtigingen in voor de gebruiker van de technische account in de Experience Manager-omgeving](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe raadt aan tokenverificatie op een productieomgeving te gebruiken.

### Verifieer multi-huurder API

#### Verificatiekoppen

Elke binnenkomende HTTP API-aanroep naar de Cloud Manager API moet de volgende drie headers bevatten:

* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

De waarden die moeten worden verzonden in de `x-api-key` en `x-gw-ims-org-id` De kopballen worden verstrekt in het de detailscherm van Geloofsbrieven in [Adobe Developer Console](https://developer.adobe.com/console). De waarde van de `x-api-key` header is de client-id en de waarde voor de `x-gw-ims-org-id` header is de organisatie-id.

#### Adobe Developer-console configureren om een toegangstoken te genereren

Als u verificatie-API&#39;s wilt instellen, maakt u een project in Adobe Developer Console en voegt u communicatie-API&#39;s toe aan het project in Adobe Developer Console. De integratie genereert API Key, Client Secret, Payload (JWT):

1. Neem contact op met de beheerder van de Adobe Developer-console. Vraag de beheerder om toe te voegen als ontwikkelaar.
1. Aanmelden bij `https://developer.adobe.com/console/`. Gebruik uw ontwikkelaarsaccount die uw beheerder heeft ingericht voor aanmelding bij Adobe Developer Console.
1. Selecteer uw organisatie in de rechterbovenhoek. Neem contact op met de beheerder als u uw organisatie niet kent.
1. Tik op **[!UICONTROL Create new project]**. Er verschijnt een scherm om aan de slag te gaan met uw nieuwe project. Tik op **[!UICONTROL Add API]**. Er verschijnt een scherm met een lijst van alle API&#39;s die voor uw account zijn ingeschakeld.
1. Selecteren **[!UICONTROL AEM Forms - Communications]** en tikken **[!UICONTROL Next]**. Er verschijnt een scherm om de API te configureren.
1. Selecteren **[!UICONTROL OPTION 1 Generate a key pair]** en tikken **[!UICONTROL Generate keypair]**. Het maakt en downloadt het configuratiebestand. Het gedownloade configuratiebestand bevat al uw toepassingsinstellingen en het enige exemplaar van uw persoonlijke sleutel. Adobe neemt uw persoonlijke sleutel niet op. Sla het gedownloade bestand op. Tik op **[!UICONTROL Next]**.
1. Selecteren **[!UICONTROL Integrations - Cloud Service]** en tikken **[!UICONTROL Save configured API]**. Tikken **[!UICONTROL Service Account (JWT)]** om de API-sleutel, clientgeheim en andere informatie weer te geven die vereist is voor toegang tot de API&#39;s. U stelt het token in om toegang te krijgen tot de API&#39;s.

#### Programmaticaal produceer en gebruik een toegangstoken

Om een toegangstoken programmatically te produceren, een Token van het Web JSON (JWT) te produceren en het met de Dienst van Adobe Identity Management (IMS) voor een toegangstoken te ruilen.

Gebruik de volgende toetsen, ook wel claims genoemd, om een JWT JSON-object te maken:

* `exp`- de gevraagde vervaldatum van de toegangstoken, uitgedrukt als een aantal seconden sinds 1 januari 1970 GMT. In de meeste gevallen is dit een relatief kleine waarde. Bijvoorbeeld, 5 minuten, over vijf minuten, zou deze waarde 1670923791 moeten zijn.
* `iss` - de organisatie-id van het Adobe Developer Console-project, in de notatie org_ident@AdobeOrg.
* `sub` - de technische-accountid van de integratie met de Adobe Developer Console, in de volgende notatie: id@techacct.adobe.com.
* `aud` - De client-id uit de Adobe Developer Console-integratie die is voorafgegaan door `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - ingesteld op de letterlijke waarde `true`

Dit JSON-object moet vervolgens base64 gecodeerd en ondertekend zijn met de persoonlijke sleutel voor het project. Tot slot wordt de gecodeerde waarde verzonden in het lichaam van een verzoek van de POST aan `https://ims-na1.adobelogin.com/ims/exchange/jwt` samen met Client ID en Client Secret voor het project.

##### Voorbeeld

```JSON
    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache
```

#### Taalondersteuning voor JWT

Hoewel het mogelijk is om het volledige JWT-genereren en -uitwisselingsproces in aangepaste code uit te voeren, is het gemeenschappelijker om hiervoor een bibliotheek op een hoger niveau te gebruiken. Een aantal van deze bibliotheken wordt vermeld op de [Adobe I/O JWT-documentatie](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

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
