---
title: Toegangstokens genereren voor server-side API's (verouderd)
description: Leer hoe u communicatie tussen een externe server en AEM as a Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 22216d2c045b79b7da13f09ecbe1d56a91f604df
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 0%

---

# Toegangstokens genereren voor server-side API&#39;s (verouderd) {#generating-access-tokens-for-server-side-apis-legacy}

Sommige architecturen vertrouwen erop dat ze AEM as a Cloud Service bellen vanuit een toepassing die wordt gehost op een server buiten de AEM-infrastructuur. Bijvoorbeeld een mobiele toepassing die een server aanroept, die vervolgens API-aanvragen bij AEM as a Cloud Service indient.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. AEM as a Cloud Service [&#x200B; Developer Console &#x200B;](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tekenen nodig voor het authentificatieproces te produceren.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=nl-NL#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met een IMS org-beheerdersrol en die ook lid is van het productprofiel van AEM-gebruikers of AEM-beheerders op AEM-auteur, kan een AEM as a Cloud Service-referentie genereren. Die referentie kan later worden opgehaald door een gebruiker met de AEM as a Cloud Service Environment Administrator-rol en moet op de server worden geïnstalleerd en moet zorgvuldig worden behandeld als een geheime sleutel. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een ondertekende JWT-token te maken, die met IMS wordt uitgewisseld voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te doen. De geloofsbrieven verlopen na één jaar door gebrek, maar zij kunnen worden verfrist wanneer nodig, zie [&#x200B; Vernieuwen Geloofsbrieven &#x200B;](#refresh-credentials).

De server-aan-server stroom impliceert de volgende stappen:

* Referenties voor AEM as a Cloud Service ophalen vanuit de Developer Console
* Installeer de referenties voor AEM as a Cloud Service op een niet-AEM-server die AEM aanroept
* Een JWT-token genereren en deze token uitwisselen voor een toegangstoken met behulp van Adobe IMS API&#39;s
* De AEM API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### Credentials van AEM as a Cloud Service ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service-ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving en twee knoppen. Een gebruiker met de de beheerderrol van het Milieu van AEM as a Cloud Service kan **klikken produceert de knoop van de Credentials van de Dienst** om de de dienstgeloofsbrieven te produceren en te tonen. De JSON bevat alle informatie die vereist is voor de niet-AEM-server, inclusief client-id, clientgeheim, persoonlijke sleutel, certificaat en configuratie voor auteur- en publicatieniveaus van de omgeving, ongeacht de podselectie.

![&#x200B; JWT Generation &#x200B;](assets/JWTtoken3.png)

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

Na wordt geproduceerd, kunnen de geloofsbrieven later worden teruggewonnen door de **te drukken krijgt de knoop van de Credentials van de Dienst** in de zelfde plaats.

>[!IMPORTANT]
>
>Een IMS org beheerder - typisch de gebruiker die het milieu door Cloud Manager leverde - die ook lid van het Profiel van het Product van de Gebruikers of van AEM van de Beheerders van AEM op de Auteur van AEM zou moeten zijn, heeft toegang tot Developer Console. Dan moeten zij **klikken produceert de geloofsbrieven van de Dienst** knoop zodat worden de geloofsbrieven geproduceerd en later teruggewonnen door een gebruiker met admintoestemmingen aan het milieu van AEM as a Cloud Service. Als de IMS org beheerder deze taak niet heeft gedaan, deelt een bericht hen mee dat zij de rol van de Beheerder IMS org nodig hebben.

### De AEM Service Credentials installeren op een niet-AEM-server {#install-the-aem-service-credentials-on-a-non-aem-server}

De niet-AEM-toepassing die oproepen naar AEM doet, moet toegang hebben tot de geloofsbrieven van AEM as a Cloud Service en deze als geheim behandelen.

### Genereer een JWT-token en verander dit voor een Access Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Gebruik de geloofsbrieven om een teken van JWT in een vraag aan de dienst van Adobe tot stand te brengen IMS om een toegangstoken terug te winnen, dat 24 uur geldig is.

De AEM CS Service Credentials kunnen worden uitgewisseld voor een toegangstoken met behulp van voor dit doel ontworpen codevoorbeelden. De code van de steekproef is beschikbaar bij [&#x200B; Adobe openbare bewaarplaats GitHub &#x200B;](https://github.com/adobe/aemcs-api-client-lib), die codevoorbeelden bevat die u voor uw eigen projecten kunt kopiëren en aanpassen. Merk op dat deze bewaarplaats steekproefcode voor verwijzing bevat en niet als productie-klaar bibliotheekgebiedsdeel gehandhaafd wordt.

```
/*jshint node:true */
"use strict";

const fs = require('fs');
// Sample code adapted from Adobe's GitHub repository
const exchange = require("./your-local-aemcs-client"); // Copy and adapt the code from the GitHub repository

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

Het toegangstoken bepaalt wanneer het verloopt, die typisch 24 uren is. Er is steekproefcode in de git bewaarplaats om een toegangstoken te beheren en het te verfrissen alvorens het verloopt.

### De AEM API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een milieu van AEM as a Cloud Service, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"` . Als u bijvoorbeeld `curl` gebruikt:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen in voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Nadat de technische rekeningsgebruiker in AEM (komt voor na het eerste verzoek met het overeenkomstige toegangstoken) wordt gecreeerd, moet de technische rekeningsgebruiker behoorlijk **in** AEM worden toegelaten.

Standaard wordt in de AEM Auteur-service de gebruiker van de technische account toegevoegd aan de gebruikersgroep Medewerkers die lees- en toegangsrechten biedt voor AEM.

Deze gebruiker van een technische account in AEM kan verder worden voorzien van machtigingen met de gebruikelijke methoden.

## Developer Flow {#developer-flow}

Ontwikkelaars moeten testen met behulp van een ontwikkelingsexemplaar van hun niet-AEM-toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen indient bij een ontwikkelings-AEM as a Cloud Service-ontwikkelomgeving. Omdat ontwikkelaars echter niet noodzakelijkerwijs beschikken over IMS-beheerdersmachtigingen, kan Adobe niet aannemen dat ze de JWT-toonder kunnen genereren die wordt beschreven in de reguliere server-naar-server-flow. Aldus, verstrekt Adobe een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan een milieu van AEM as a Cloud Service kan worden gebruikt dat zij toegang hebben tot.

Zie de [&#x200B; documentatie van de Richtlijnen van de Ontwikkelaar &#x200B;](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) voor informatie over de vereiste toestemmingen om de de ontwikkelaarsconsole van AEM as a Cloud Service te gebruiken.

>[!NOTE]
>
>Het token voor lokale ontwikkelingstoegang is maximaal 24 uur geldig waarna het opnieuw moet worden gegenereerd met dezelfde methode.

Ontwikkelaars kunnen dit token gebruiken om aanroepen uit hun niet-AEM testtoepassing naar een AEM as a Cloud Service-omgeving uit te voeren. De ontwikkelaar gebruikt dit token doorgaans samen met de niet-AEM-toepassing op zijn eigen laptop. Bovendien is de AEM als Cloud doorgaans een omgeving die geen productie heeft.

De ontwikkelaarsstroom omvat de volgende stappen:

* Een toegangstoken genereren vanuit de Developer Console
* Roep de AEM-toepassing aan met het toegangstoken.

Ontwikkelaars kunnen ook API-aanroepen uitvoeren naar een AEM-project op hun lokale computer. In dat geval is een toegangstoken niet nodig.

### Het produceren van het Token van de Toegang {#generating-the-access-token}

Om een toegangstoken, in Developer Console te produceren, klik **krijgt Token van de Lokale Ontwikkeling**.

### Vraag dan de Toepassing van AEM met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een milieu van AEM as a Cloud Service, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"` .

## Referenties vernieuwen {#refresh-credentials}

Standaard verloopt de referentie op AEM as a Cloud Service na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden. Het gebruik **verfrist de Geloofsbrieven van de Dienst** van het **3&rbrace; lusje van Integraties &lbrace;in Developer Console, zoals hieronder getoond.**

![&#x200B; Referentie verfrist zich &#x200B;](assets/credential-refresh.png)

Nadat u op de knop hebt gedrukt, wordt een nieuwe set referenties gegenereerd. U kunt de geheime opslag bijwerken met de nieuwe gegevens en controleren of deze naar behoren werken.

>[!NOTE]
>
> Na het klikken van de **verfrist de knoop van de Referenties van de Dienst**, blijven de oude geloofsbrieven geregistreerd tot zij verlopen, maar slechts is de meest recente reeks beschikbaar om van Developer Console op om het even welk ogenblik worden gezien.

## Intrekking van servicereferenties {#service-credentials-revocation}

Als de aanmeldingsgegevens moeten worden ingetrokken, moet u een aanvraag indienen bij de klantenondersteuning. Ga hierbij als volgt te werk:

1. Schakel de gebruiker van de technische account voor de Adobe Admin Console uit in de gebruikersinterface:
   * Druk in Cloud Manager op de knop **...** naast uw omgeving. Met deze actie opent u de pagina met productprofielen
   * Nu, klik het **gebruikersprofiel van AEM**, om een lijst van de gebruikers te tonen
   * Klik **API Geloofsbrieven** tabel, dan vind de aangewezen technische rekeningsgebruiker en schrap het
2. Contact opnemen met de klantenondersteuning en vragen of de servicegegevens voor die specifieke omgeving worden verwijderd
3. Tot slot kunt u de geloofsbrieven opnieuw produceren, zoals die in deze documentatie wordt beschreven. Zorg er ook voor dat de nieuwe gebruiker van de technische account die wordt gemaakt, over de juiste machtigingen beschikt.
