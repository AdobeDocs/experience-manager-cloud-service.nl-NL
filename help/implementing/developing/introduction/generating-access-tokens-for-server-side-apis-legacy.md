---
title: Toegangstokens genereren voor server-side API's (verouderd)
description: Leer hoe u communicatie tussen een externe server en AEM as a Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
hidefromtoc: true
exl-id: 6561870c-cbfe-40ef-9efc-ea75c88c4ed7
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 0%

---

# Toegangstokens genereren voor server-side API&#39;s (verouderd) {#generating-access-tokens-for-server-side-apis-legacy}

Sommige architecturen baseren zich op het maken van vraag aan AEM as a Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om as a Cloud Service AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM as a Cloud Service [Ontwerpconsole](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

<!-- ERROR: Not Found (HTTP error 404)
>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met een IMS org beheerderrol, en die ook een lid van het Profiel van het Product van de AEMGebruikers of AEM van Beheerders op AEM Auteur is, kan een AEM as a Cloud Service referentie produceren. Die referentie kan later door een gebruiker met de AEM as a Cloud Service de beheerderrol van het Milieu worden teruggewonnen en op de server worden geïnstalleerd en de behoeften moeten zorgvuldig als geheime sleutel worden behandeld. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een ondertekende JWT-token te maken, die met IMS wordt uitgewisseld voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te maken. De geloofsbrieven verlopen na één jaar door gebrek, maar zij kunnen worden verfrist wanneer nodig, zoals beschreven [hier](#refresh-credentials).

De server-aan-server stroom impliceert de volgende stappen:

* De referenties voor AEM as a Cloud Service ophalen via de ontwikkelaarsconsole
* Installeer de geloofsbrieven voor AEM as a Cloud Service op een niet AEM server die vraag aan AEM doet
* Een JWT-token genereren en deze token uitwisselen voor een toegangstoken met IMS API&#39;s van de Adobe
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### De AEM as a Cloud Service referenties ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving en twee knoppen. Een gebruiker met de AEM as a Cloud Service beheerderrol van het Milieu kan klikken **Servicekredieten genereren** knoop om de de dienstgeloofsbrieven json te produceren en te tonen. De JSON bevat alle informatie die voor de niet-AEM server is vereist, inclusief client-id, clientgeheim, persoonlijke sleutel, certificaat en configuratie voor auteur- en publicatieniveaus van de omgeving, ongeacht de podselectie.

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

Nadat het wordt geproduceerd, kunnen de geloofsbrieven later worden teruggewonnen door te drukken **Servicekredieten ophalen** op dezelfde locatie.

>[!IMPORTANT]
>
>Een beheerder IMS org - typisch de gebruiker die het milieu door middel van de Manager van de Wolk leverde - die ook lid van het Profiel van het Product van de Gebruikers of van AEM van de Beheerders op AEM Auteur zou moeten zijn, heeft toegang tot de Console van de Ontwikkelaar. Vervolgens moeten ze op de knop **Servicekredieten genereren** zodat worden de geloofsbrieven geproduceerd en later teruggewonnen door een gebruiker met admintoestemmingen aan het AEM as a Cloud Service milieu. Als de IMS org beheerder deze taak niet heeft gedaan, deelt een bericht hen mee dat zij de rol van de Beheerder IMS org nodig hebben.

### Installeer de AEM servicereferentials op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De niet-AEM toepassing die vraag aan AEM maakt zou tot de geloofsbrieven van AEM as a Cloud Service moeten kunnen toegang hebben, behandelend het als geheim.

### Genereer een JWT-token en verander dit voor een Access Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Gebruik de geloofsbrieven om een teken van JWT in een vraag aan de dienst van IMS van de Adobe tot stand te brengen om een toegangstoken terug te winnen, dat 24 uren geldig is.

De AEM CS Service Credentials kunnen worden uitgewisseld voor een toegangstoken met behulp van clientbibliotheken die voor dit doel zijn ontworpen. De clientbibliotheken zijn beschikbaar via [De openbare GitHub-opslagplaats van Adobe](https://github.com/adobe/aemcs-api-client-lib), die gedetailleerdere richtsnoeren en de meest recente informatie bevat.

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

Het toegangstoken bepaalt wanneer het verloopt, die typisch 24 uren is. Er is steekproefcode in de git bewaarplaats om een toegangstoken te beheren en het te verfrissen alvorens het verloopt.

### De AEM-API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`. Als u bijvoorbeeld `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Nadat de gebruiker van de technische rekening in AEM (komt voor na het eerste verzoek met het overeenkomstige toegangstoken) wordt gecreeerd, moet de gebruiker van de technische rekening behoorlijk worden toegelaten **in** AEM.

Standaard wordt in de AEM-auteurservice de gebruiker van de technische account toegevoegd aan de gebruikersgroep Medewerkers die AEM voor leestoegang biedt.

Deze gebruiker van de technische rekening in AEM kan verder worden voorzien van toestemmingen gebruikend de gebruikelijke methodes.

## Developer Flow {#developer-flow}

Ontwikkelaars moeten testen met behulp van een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen doet voor een ontwikkelomgeving AEM as a Cloud Service ontwikkelomgeving. Omdat ontwikkelaars echter niet noodzakelijkerwijs beschikken over IMS-beheerdersmachtigingen, kan de Adobe niet aannemen dat zij de JWT-drager kunnen genereren die in de reguliere server-naar-server-flow wordt beschreven. Aldus, verstrekt de Adobe een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan een AEM as a Cloud Service milieu kan worden gebruikt dat zij toegang hebben tot.

Zie de [Documentatie ontwikkelaarsrichtlijnen](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) voor informatie over de vereiste toestemmingen om de AEM as a Cloud Service ontwikkelaarsconsole te gebruiken.

>[!NOTE]
>
>Het token voor lokale ontwikkelingstoegang is maximaal 24 uur geldig waarna het opnieuw moet worden gegenereerd met dezelfde methode.

Ontwikkelaars kunnen dit token gebruiken om aanroepen uit te voeren vanuit hun niet-AEM testtoepassing naar een AEM as a Cloud Service omgeving. De ontwikkelaar gebruikt dit token doorgaans met de niet-AEM toepassing op zijn eigen laptop. Bovendien is de AEM als Cloud doorgaans een omgeving die geen productie heeft.

De ontwikkelaarsstroom omvat de volgende stappen:

* Een toegangstoken genereren vanuit de ontwikkelaarsconsole
* Roep de AEM toepassing met het toegangstoken aan.

Ontwikkelaars kunnen ook API-aanroepen uitvoeren naar een AEM project dat op hun lokale computer wordt uitgevoerd. In dat geval is een toegangstoken niet nodig.

### Het produceren van het Token van de Toegang {#generating-the-access-token}

Als u een toegangstoken wilt genereren, klikt u in de Developer Console op **Token voor lokale ontwikkeling ophalen**.

### Vraag dan AEM Toepassing met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`.

## Referenties vernieuwen {#refresh-credentials}

Standaard verloopt de referentie op AEM as a Cloud Service na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden. Gebruiken **Referenties service vernieuwen** van de **Integraties** in de Developer Console, zoals hieronder wordt weergegeven.

![Referentievernieuwen](assets/credential-refresh.png)

Nadat u op de knop hebt gedrukt, wordt een nieuwe set referenties gegenereerd. U kunt de geheime opslag bijwerken met de nieuwe gegevens en controleren of deze naar behoren werken.

>[!NOTE]
>
> Nadat u op de knop **Referenties service vernieuwen** blijven de oude gegevens geregistreerd tot ze verlopen, maar alleen de meest recente set is op elk gewenst moment beschikbaar om te worden bekeken in de Developer Console.

## Intrekking van servicereferenties {#service-credentials-revocation}

Als de aanmeldingsgegevens moeten worden ingetrokken, moet u een aanvraag indienen bij de klantenondersteuning. Ga hierbij als volgt te werk:

1. Schakel de gebruiker van de technische account voor de Adobe Admin Console uit in de gebruikersinterface:
   * Druk op de knop **...** naast uw omgeving. Met deze actie opent u de pagina met productprofielen
   * Klik nu op de knop **AEM** profiel, om een lijst met gebruikers weer te geven
   * Klik op de knop **API-referenties** , zoekt u de juiste gebruiker van de technische account en verwijdert u deze
2. Contact opnemen met de klantenondersteuning en vragen of de servicegegevens voor die specifieke omgeving worden verwijderd
3. Tot slot kunt u de geloofsbrieven opnieuw produceren, zoals die in deze documentatie wordt beschreven. Zorg er ook voor dat de nieuwe gebruiker van de technische account die wordt gemaakt, over de juiste machtigingen beschikt.
