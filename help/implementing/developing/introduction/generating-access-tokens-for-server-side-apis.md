---
title: Toegangstokens genereren voor server-side API's
description: Leer hoe u communicatie tussen een externe server en AEM als Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
translation-type: tm+mt
source-git-commit: a8cb0c1bf2cdc741173e83ad00b6453931a8df18
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Inleiding {#introduction}

>[!IMPORTANT]
>
>Deze functie is nog niet beschikbaar. Zie de [Release-aantekeningen](/help/release-notes/release-notes-cloud/release-notes-current.md) voor een actuele lijst met functies.

Sommige architecturen baseren zich op het maken van vraag aan AEM als Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om als Cloud Service te AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM als Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met de admin rol kan een AEM als Cloud Service credential produceren, die op de server zou moeten worden geïnstalleerd en zorgvuldig als geheime sleutel zouden moeten worden behandeld. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM als Cloud Service-API. De gegevens worden gebruikt om een ondertekende JWT-token te maken, die met IMS wordt uitgewisseld voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM als Cloud Service te doen.

De server-aan-server stroom impliceert de volgende stappen:

* De AEM ophalen als Cloud Service van de ontwikkelaarsconsole
* Installeer de AEM als geloofsbrieven van de Cloud Service op een niet AEM server die vraag aan AEM maken
* Een JWT-token genereren en dat token uitwisselen voor een toegangstoken met behulp van Adobe API&#39;s
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie

### De AEM ophalen als referentie Cloud Service {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers die de beheerrol voor een IMS-organisatie hebben, zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving en twee knoppen. Als u op de knop **Servicedesentials ophalen** klikt, worden de servicereferenties gegenereerd. Deze worden gebruikt voor alle informatie die vereist is voor de niet-AEM server, inclusief client-id, clientgeheim, persoonlijke sleutel, certificaat en configuratie voor auteur- en publicatieniveaus van de omgeving, ongeacht de podselectie.

![JWT Generation](assets/JWTtoken3.png)

De uitvoer is vergelijkbaar met:

```
{
  "ok": true,
  "integration": {
    "imsEndpoint": "ims-na1.adobelogin.com",
    "metascopes": "ent_aem_cloud_sdk,ent_cloudmgr_sdk",
    "technicalAccount": {
      "clientId": "cm-p123-e1234",
      "clientSecret": "4AREDACTED17"
    },
    "email": "abcd@techacct.adobe.com",
    "id": "ABCDAE10A495E8C@techacct.adobe.com",
    "org": "1234@AdobeOrg",
    "privateKey": "-----BEGIN RSA PRIVATE KEY-----\r\REDACTED\r\n==\r\n-----END RSA PRIVATE KEY-----\r\n",
    "publicKey": "-----BEGIN CERTIFICATE-----\r\nREDACTED\r\n-----END CERTIFICATE-----\r\n"
  },
  "statusCode": 200
}
```

### Installeer de AEM servicedesentials op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De niet-AEM toepassing die vraag aan AEM maakt zou tot de AEM als geloofsbrieven van de Cloud Service moeten kunnen toegang hebben, behandelend het als geheim.

### Genereer een JWT-token en verruilen dit voor een toegangstoken{#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Gebruik de geloofsbrieven om een teken JWT in een vraag aan de dienst van Adobe IMS tot stand te brengen om een toegangstoken terug te winnen, dat 24 uur geldig is.

De AEM-CS Service Credentials kunnen worden uitgewisseld voor een toegangstoken met behulp van clientbibliotheken die voor dit doel zijn ontworpen. De cliëntbibliotheken zijn beschikbaar [openbaar GitHub bewaarplaats ](https://github.com/adobe/aemcs-api-client-lib), die gedetailleerdere begeleiding en recentste informatie bevat.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
const exchange = require("@adobe/aemcs-api-client-lib");

const jsonfile = "aemcs-service-credentials.json";

var config = JSON.parse(fs.readFileSync(jsonfile, 'utf8'));
exchange(config).then(accessToken => {
    // output the access token in json form including when it will expire.
    console.log(JSON.stringify(accessToken,null,2));
}).catch(e => {
    console.log("Failed to exchange for access token ",e);
});
```

De zelfde uitwisseling kan in om het even welke taal worden uitgevoerd die een ondertekend Token JWT met het correcte formaat kan produceren en IMS Symbolische Uitwisseling APIs roepen.

Het toegangstoken zal bepalen wanneer het verloopt, wat typisch 12h is. Er is steekproefcode in de git bewaarplaats om een toegangstoken te beheren en het te verfrissen alvorens het verloopt.

### De AEM-API {#calling-the-aem-api} aanroepen

Maak de aangewezen server-aan-server API vraag aan een AEM als Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"`. Als u bijvoorbeeld `curl` gebruikt:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

## Developer Flow {#developer-flow}

Ontwikkelaars willen waarschijnlijk testen met een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen indient bij een AEM als ontwikkelomgeving. Nochtans, aangezien de ontwikkelaars niet noodzakelijk beheerdersroltoegang tot de AEM als Cloud Service hebben ontwikkelt milieu, kunnen wij niet veronderstellen zij de drager kunnen produceren JWT die in de regelmatige server-aan-server stroom wordt beschreven. Aldus, verstrekken wij een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan AEM als Cloud Service milieu&#39;s kan worden gebruikt die zij hebben toegang tot.

Zie [documentatie van de Richtlijnen van de Ontwikkelaar](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) voor informatie over de vereiste toestemmingen om de AEM als console van de Cloud Service ontwikkelaar te gebruiken.

>[!NOTE]
>
>Het token is 24 uur geldig waarna het opnieuw moet worden gegenereerd met dezelfde methode.

De ontwikkelaars kunnen dit teken gebruiken om vraag van hun niet-AEM testtoepassing aan een AEM als milieu van de Cloud Service te maken. De ontwikkelaar gebruikt dit token doorgaans samen met de niet-AEM toepassing op zijn eigen laptop. Bovendien is de AEM als Cloud doorgaans een omgeving die geen productie heeft.

De ontwikkelaarsstroom omvat de volgende stappen:

* Een toegangstoken genereren vanuit de ontwikkelaarsconsole
* Roep de AEM toepassing met het toegangstoken aan.

Ontwikkelaars kunnen ook API-aanroepen uitvoeren naar een AEM project dat op hun lokale computer wordt uitgevoerd. In dat geval is een toegangstoken niet nodig.

### Het produceren van het Token van de Toegang {#generating-the-access-token}

Klik **Get Local Development Token** knoop in de Console van de Ontwikkelaar om een toegangstoken te produceren.

### Vraag dan AEM Toepassing met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een AEM als Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"`.

## Intrekking servicekredieten {#service-credentials-revocation}

Stuur een aanvraag naar de klantenondersteuning als de token voor de JWT-toonder moet worden ingetrokken.