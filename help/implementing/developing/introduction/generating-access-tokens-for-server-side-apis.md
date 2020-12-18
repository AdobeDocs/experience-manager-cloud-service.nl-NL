---
title: Toegangstokens genereren voor server-side API's
description: Leer hoe u communicatie tussen een externe server en AEM als Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
translation-type: tm+mt
source-git-commit: 251f5de85d63f6afd730fc450fe2b5a06bc90c38
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---


# Inleiding {#introduction}

>[!IMPORTANT]
>
>Deze functie is nog niet beschikbaar. Zie de [Release-aantekeningen](/help/release-notes/release-notes-cloud/release-notes-current.md) voor een actuele lijst met functies.

Sommige architecturen baseren zich op het maken van vraag aan AEM als Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om als Cloud Service te AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM als Cloud Service [Developer Console](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met de beheerdersrol kan een JWT-token voor toonder genereren. Dit token moet op de server worden geïnstalleerd en moet zorgvuldig worden behandeld als een geheime sleutel. De token van de JWT-toonder moet met IMS worden uitgewisseld voor een toegangstoken, die in het verzoek tot AEM als Cloud Service moet worden opgenomen.

De server-aan-server stroom impliceert de volgende stappen:

* Genereer het token voor de JWT-toonder vanaf de ontwikkelaarsconsole
* Installeer het token op een niet-AEM server die aanroepen naar AEM
* Uitwisseling JWT dragerteken voor een toegangstoken gebruikend Adobe APIs
* De AEM-API aanroepen

### Het produceren van de Token van de Drager JWT {#generating-the-jwt-bearer-token}

De gebruikers die de adminrol voor een organisatie hebben zullen het integratietabblad in de ontwikkelaarsconsole voor een bepaalde milieu, evenals twee knopen zien. Als u op de knop **Servicekredieten ophalen** klikt, worden de persoonlijke sleutel, het certificaat en de configuratie voor auteur- en publicatieniveaus van de omgeving gegenereerd, ongeacht de podselectie.

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

### Token installeren op een niet-AEM server {#install-the-token-on-a-non-aem-server}

De niet-AEM toepassing die vraag aan AEM maakt zou het de dragerteken van JWT moeten installeren, behandelend het als geheim.

### Uitwisseling het teken JWT voor een Token van de Toegang {#exchange-the-jwt-token-for-an-access-token}

Neem het JWT-token op in een aanroep van Adobe IMS-service om een toegangstoken op te halen. Dit is 24 uur geldig.

### De AEM-API {#calling-the-aem-api} aanroepen

Maak de aangewezen server-aan-server API vraag aan een AEM als Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"`.

<!-- ### Code Samples {#code-samples}

https://git.corp.adobe.com/boston/skyline-api-client-lib (internal note: URL will change to public git repo before we publish) contains client libraries written in node.js that will exchange the JSON outputted by the developer console for an access token. -->

## Developer Flow {#developer-flow}

Ontwikkelaars willen waarschijnlijk testen met een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen indient bij een AEM als ontwikkelomgeving. Nochtans, aangezien de ontwikkelaars niet noodzakelijk beheerdersroltoegang tot de AEM als Cloud Service hebben ontwikkelt milieu, kunnen wij niet veronderstellen zij de drager kunnen produceren JWT die in de regelmatige server-aan-server stroom wordt beschreven. Aldus, verstrekken wij een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan AEM als Cloud Service milieu&#39;s kan worden gebruikt die zij hebben toegang tot. Zie [documentatie van de Richtlijnen van de Ontwikkelaar](/help/implementing/developing/introduction/development-guidelines.md) voor informatie over de vereiste toestemmingen om de AEM als console van de Cloud Service ontwikkelaar te gebruiken.

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

## Intrekking van token aan JWT-gebruiker {#jwt-bearer-token-revocation}

Stuur een aanvraag naar de klantenondersteuning als de token voor de JWT-toonder moet worden ingetrokken.