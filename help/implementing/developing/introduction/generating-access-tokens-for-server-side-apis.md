---
title: Toegangstokens genereren voor server-side API's
description: Leer hoe u communicatie tussen een externe server en AEM as a Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: c4f4ce968c17db1f1185ce7be9cad833eaf0b91b
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---

# Inleiding {#introduction}

Sommige architecturen baseren zich op het maken van vraag aan AEM as a Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om as a Cloud Service AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM as a Cloud Service [Ontwerpconsole](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

>[!NOTE]
>
>Naast deze documentatie kunt u ook de zelfstudie raadplegen over [Token-gebaseerde authentificatie voor AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication).

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met een IMS org beheerderrol, en die ook een lid van het Profiel van het Product van de AEM Gebruikers of AEM van Beheerders op AEM Auteur is, kan een AEM as a Cloud Service referentie produceren. Die referentie kan later door een gebruiker met de AEM as a Cloud Service de beheerderrol van het Milieu worden teruggewonnen en zou op de server moeten worden geïnstalleerd en de behoeften moeten zorgvuldig als geheime sleutel worden behandeld. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een ondertekende JWT-token te maken, die met IMS wordt uitgewisseld voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te maken. De geloofsbrieven verlopen na één jaar door gebrek, maar zij kunnen worden verfrist wanneer nodig, zoals beschreven [hier](#refresh-credentials).

De server-aan-server stroom impliceert de volgende stappen:

* De AEM as a Cloud Service gegevens ophalen uit de ontwikkelaarsconsole
* Installeer de AEM as a Cloud Service geloofsbrieven op een niet AEM server die vraag aan AEM maken
* Een JWT-token genereren en dat token uitwisselen voor een toegangstoken met behulp van Adobe API&#39;s
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### De AEM as a Cloud Service referenties ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving en twee knoppen. Een gebruiker met de AEM as a Cloud Service rol van de Beheerder van het Milieu kan klikken **Servicekredieten genereren** om de verbinding van de de dienstgeloofsbrieven te produceren en te tonen, die alle informatie zal bevatten die voor de niet AEM server, met inbegrip van cliënt identiteitskaart, cliëntgeheim, privé sleutel, certificaat, en configuratie voor auteur en publicatieniveaus van het milieu, ongeacht de podselectie wordt vereist.

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

Nadat het wordt geproduceerd, kunnen de geloofsbrieven op een recentere datum worden teruggewonnen door op **Servicekredieten ophalen** op dezelfde locatie.

>[!IMPORTANT]
>
>Een IMS org-beheerder (doorgaans dezelfde gebruiker die de omgeving heeft ingericht via Cloud Manager), die ook lid moet zijn van het productprofiel AEM gebruikers of AEM beheerders van AEM-auteur, moet eerst toegang krijgen tot de Developer Console en op de knop **Servicekredieten genereren** om de geloofsbrieven te produceren en later terug te winnen door een gebruiker met admin toestemmingen aan het AEM as a Cloud Service milieu. Als de IMS org beheerder dit niet heeft gedaan, zal een bericht hen informeren dat zij de rol van de Beheerder IMS org nodig hebben.

### Installeer de AEM servicereferenties op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De niet-AEM toepassing die vraag aan AEM maakt zou tot de AEM as a Cloud Service geloofsbrieven moeten kunnen toegang hebben, behandelend het als geheim.

### Genereer een JWT-token en verander dit voor een Access Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Gebruik de geloofsbrieven om een teken JWT in een vraag aan de dienst van Adobe IMS tot stand te brengen om een toegangstoken terug te winnen, dat 24 uur geldig is.

De AEM CS Service Credentials kunnen worden uitgewisseld voor een toegangstoken met behulp van clientbibliotheken die voor dit doel zijn ontworpen. De clientbibliotheken zijn beschikbaar via [Adobe](https://github.com/adobe/aemcs-api-client-lib), die gedetailleerdere richtsnoeren en de meest recente informatie bevat.

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

Het toegangstoken zal bepalen wanneer het verloopt, wat typisch 24 uren is. Er is steekproefcode in de git bewaarplaats om een toegangstoken te beheren en het te verfrissen alvorens het verloopt.

### De AEM-API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`. Als u bijvoorbeeld `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Zodra de gebruiker van de technische rekening in AEM wordt gecreeerd (dit komt na het eerste verzoek met het overeenkomstige toegangstoken voor), moet de gebruiker van de technische rekening behoorlijk worden toegelaten **in** AEM.

Merk op dat de gebruiker van de technische rekening op de dienst van de Auteur AEM door gebrek, aan de gebruikersgroep van Medewerkers wordt toegevoegd die lees toegang AEM.

Deze gebruiker van de technische rekening in AEM kan verder worden voorzien van toestemmingen gebruikend de gebruikelijke methodes.

## Developer Flow {#developer-flow}

Ontwikkelaars willen waarschijnlijk testen met een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen doet voor een ontwikkelomgeving AEM as a Cloud Service ontwikkelomgeving. Nochtans, aangezien de ontwikkelaars niet noodzakelijk IMS beheerdersroltoestemmingen hebben, kunnen wij niet veronderstellen zij de drager JWT die in de regelmatige server-aan-server stroom wordt beschreven kunnen produceren. Aldus, verstrekken wij een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan AEM as a Cloud Service milieu&#39;s kan worden gebruikt waar zij toegang tot hebben.

Zie de [Documentatie ontwikkelaarsrichtlijnen](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) voor informatie over de vereiste toestemmingen om de AEM as a Cloud Service ontwikkelaarsconsole te gebruiken.

>[!NOTE]
>
>Het token voor lokale ontwikkelingstoegang is maximaal 24 uur geldig waarna het opnieuw moet worden gegenereerd met dezelfde methode.

Ontwikkelaars kunnen dit token gebruiken om aanroepen uit te voeren vanuit hun niet-AEM testtoepassing naar een AEM as a Cloud Service omgeving. De ontwikkelaar gebruikt dit token doorgaans samen met de niet-AEM toepassing op zijn eigen laptop. Bovendien is de AEM als Cloud doorgaans een omgeving die geen productie heeft.

De ontwikkelaarsstroom omvat de volgende stappen:

* Een toegangstoken genereren vanuit de ontwikkelaarsconsole
* Roep de AEM toepassing met het toegangstoken aan.

Ontwikkelaars kunnen ook API-aanroepen uitvoeren naar een AEM project dat op hun lokale computer wordt uitgevoerd. In dat geval is een toegangstoken niet nodig.

### Het produceren van het Token van de Toegang {#generating-the-access-token}

Klik op de knop **Token voor lokale ontwikkeling ophalen** in de Ontwikkelaarsconsole om een toegangstoken te produceren.

### Vraag dan AEM Toepassing met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`.

## Referenties vernieuwen {#refresh-credentials}

Standaard verlopen de AEM as a Cloud Service gegevens na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden.

Om dit te bereiken, kunt u gebruiken **Referenties service vernieuwen** van de knop **Integraties** in de Developer Console, zoals hieronder wordt weergegeven.

![Referentie vernieuwen](assets/credential-refresh.png)

Nadat u op de knop hebt gedrukt, wordt een nieuwe set referenties gegenereerd. U kunt de geheime opslag bijwerken met de nieuwe gegevens en controleren of deze naar behoren werken.

>[!NOTE]
>
> Nadat u op de knop **Referenties service vernieuwen** blijven de oude gegevens geregistreerd tot ze verlopen, maar alleen de meest recente set is op elk gewenst moment beschikbaar om te worden bekeken in de Developer Console.

## Intrekking van servicereferenties {#service-credentials-revocation}

Als de geloofsbrieven moeten worden ingetrokken, moet u een verzoek aan klantensteun indienen gebruikend deze stappen:

1. Schakel de technische accountgebruiker voor de Adobe Admin Console uit in de gebruikersinterface:
   * Druk in Cloud Manager op **...** naast uw omgeving. Hiermee wordt de pagina met productprofielen geopend
   * Klik nu op de knop **AEM** profiel, om een lijst met gebruikers weer te geven
   * Klik op de knop **API-referenties** , zoekt u de juiste gebruiker van de technische account en verwijdert u deze
2. Contact opnemen met de klantenondersteuning en vragen of de servicegegevens voor die specifieke omgeving worden verwijderd
3. Tot slot kunt u de geloofsbrieven opnieuw produceren, zoals die in deze documentatie wordt beschreven. Zorg er ook voor dat de nieuwe gebruiker van de technische account die wordt gemaakt, over de juiste machtigingen beschikt.
