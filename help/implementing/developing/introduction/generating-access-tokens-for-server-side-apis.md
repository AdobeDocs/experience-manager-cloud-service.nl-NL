---
title: Toegangstokens genereren voor server-side API's
description: Leer hoe u communicatie tussen een externe server en AEM as a Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2089'
ht-degree: 0%

---

# Toegangstokens genereren voor server-side API&#39;s {#generating-access-tokens-for-server-side-apis}

Sommige architecturen vertrouwen op het maken van vraag aan AEM as a Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld een mobiele toepassing die een server aanroept, die vervolgens API-aanvragen bij AEM as a Cloud Service indient.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. AEM as a Cloud Service [ Developer Console ](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tekenen nodig voor het authentificatieproces te produceren.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## De server-naar-server stroom {#the-server-to-server-flow}

Gebruikers met een IMS org-beheerdersrol en die lid zijn van het AEM Gebruikers of AEM Beheerdersproductprofiel op AEM auteur, kunnen een set referenties genereren vanuit AEM as a Cloud Service. Elke referentie is een JSON-payload die een certificaat (de openbare sleutel), een persoonlijke sleutel en een technische account bevat die bestaat uit een `clientId` en `clientSecret` . Die geloofsbrieven kunnen later door een gebruiker met de de beheerderrol van het Milieu van AEM as a Cloud Service worden teruggewonnen en zouden op een niet-AEM server moeten worden geïnstalleerd en zorgvuldig als geheime sleutel worden behandeld. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een getekende JWT-token te maken, dat wordt uitgewisseld met de Adobe Identity Management Services (IMS) voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te doen. Het certificaat in de geloofsbrieven verloopt na één jaar door gebrek, maar zij kunnen worden verfrist wanneer nodig, zoals die [ hier ](#refresh-credentials) wordt beschreven.

De server-aan-server stroom impliceert de volgende stappen:

* Referenties ophalen op AEM as a Cloud Service vanuit de Developer Console
* Installeer de referenties voor AEM as a Cloud Service op een niet-AEM server die aanroepen naar AEM
* Een JWT-token genereren en deze token uitwisselen voor een toegangstoken met IMS API&#39;s van de Adobe
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### Credentials van AEM as a Cloud Service ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service-ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving. Een gebruiker met de AEM as a Cloud Service Environment Administrator-rol kan referenties maken, weergeven of beheren.

Het klikken **leidt tot nieuwe technische rekening**, wordt een reeks geloofsbrieven gecreeerd die cliënt identiteitskaart, cliëntgeheim, privé sleutel, certificaat, en configuratie voor auteur omvat en lagen van het milieu, ongeacht de podselectie publiceert.

![ Creërend een nieuwe Technische Rekening ](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Er wordt een nieuw browsertabblad geopend waarin de referenties worden weergegeven. U kunt deze weergave gebruiken om de referenties te downloaden door op het downloadpictogram naast de statustitel te drukken:

![ Referenties van de Download ](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nadat de geloofsbrieven worden gecreeerd, zullen zij onder het **Technische lusje van Rekeningen** in de **sectie van de Integraties** verschijnen:

![ Credentials van de Mening ](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Gebruikers kunnen de referenties later weergeven met de actie Weergave. Bovendien kunnen gebruikers, zoals verderop in het artikel wordt beschreven, de referenties voor dezelfde technische account bewerken. Ze kunnen deze bewerking uitvoeren door een persoonlijke sleutel of certificaat te maken, voor gevallen waarin het certificaat moet worden vernieuwd of ingetrokken.

Gebruikers met de AEM as a Cloud Service Environment Administrator-rol kunnen later referenties voor extra technische accounts maken. Deze mogelijkheid is handig wanneer verschillende API&#39;s verschillende toegangsvereisten hebben. Bijvoorbeeld lezen versus lezen-schrijven.

>[!NOTE]
>
>Klanten kunnen maximaal tien technische accounts maken, waaronder de accounts die al zijn verwijderd.

>[!IMPORTANT]
>
>Een IMS org beheerder (typisch de zelfde gebruiker die het milieu door middel van de Cloud Manager) leverde, die ook een lid van het Profiel van het Product van de Gebruikers of van AEM van de Beheerders op AEM Auteur is, moet eerst tot Developer Console toegang hebben. Dan, klik **creëren nieuwe technische rekening** voor de geloofsbrieven die moeten worden geproduceerd en later teruggewonnen door een gebruiker met admintoestemmingen aan het milieu van AEM as a Cloud Service. Als de IMS org beheerder nog niet de technische rekening heeft gecreeerd, deelt een bericht hen mee dat zij de IMS org rol van de Beheerder nodig hebben.

### Installeer de AEM servicereferentials op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De toepassing die vraag aan AEM maakt zou tot de geloofsbrieven voor AEM as a Cloud Service moeten kunnen toegang hebben, behandelend het als geheim.

### Genereer een JWT-token en verander dit voor een Access Token {#generate-a-jwt-token-and-exchange-it-for-an-access-token}

Gebruik de geloofsbrieven om een teken van JWT in een vraag aan de dienst van IMS van de Adobe tot stand te brengen om een toegangstoken terug te winnen, dat 24 uren geldig is.

De AEM CS Service Credentials kunnen worden uitgewisseld voor een toegangstoken met behulp van clientbibliotheken die voor dit doel zijn ontworpen. De cliëntbibliotheken zijn beschikbaar bij [ openbare bewaarplaats GitHub van de Adobe ](https://github.com/adobe/aemcs-api-client-lib), die gedetailleerdere begeleiding en recentste informatie bevat.

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

>[!NOTE]
>Als er veelvoudige geloofsbrieven zijn, zorg ervoor om het aangewezen jsdossier voor de API vraag aan AEM van verwijzingen te voorzien die later wordt aangehaald.

### De AEM-API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een milieu van AEM as a Cloud Service, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"` . Als u bijvoorbeeld `curl` gebruikt:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Ten eerste moet er een nieuw productprofiel worden gemaakt in de Adobe Admin Console.

1. Ga naar Adobe Admin Console in [ https://adminconsole.adobe.com/ ](https://adminconsole.adobe.com/).
1. Pers **leiden** verbinding onder de **Producten en de kolom van de Diensten** op de linkerzijde.
1. Selecteer **AEM as a Cloud Service**.
1. Druk de **Nieuwe knoop van het Profiel**.

   ![ Nieuw Profiel ](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Noem het profiel en druk **sparen**.

   ![ sparen Profiel ](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Selecteer het profiel dat u hebt gemaakt in de profiellijst.
1. Selecteer **toevoegen Gebruiker**.

   ![ voeg Gebruiker ](/help/implementing/developing/introduction/assets/s2s-addusers.png) toe

1. Voeg de technische rekening toe die u (in dit geval `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) creeerde, en klik **sparen**.

   ![ voeg de Rekening van de Tech ](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png) toe

1. Wacht 10 minuten op de veranderingen om van kracht te worden en een API vraag aan AEM met een toegangstoken te maken die van de nieuwe referentie wordt geproduceerd. Als cURL-opdracht wordt deze weergegeven als in dit voorbeeld:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nadat u de API-aanroep hebt gemaakt, wordt het productprofiel weergegeven als een gebruikersgroep in de AEM as a Cloud Service-auteur-instantie, met de juiste technische account als lid van die groep.

Ga als volgt te werk om deze informatie te controleren:

1. Meld u aan bij de instantie van de auteur.
1. Ga naar **Hulpmiddelen** > **Veiligheid**, dan klik de **Groepen** kaart.
1. Zoek de naam van het profiel dat u in de lijst met groepen hebt gemaakt en klik erop:

   ![ Profiel van de Groep ](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. In het volgende venster, schakelaar over aan het **lusje van Leden** en controleer als de technische rekening daar correct vermeld is:

   ![ Leden tabel ](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


U kunt ook controleren of de technische account in de lijst van de gebruiker wordt weergegeven door de onderstaande stappen uit te voeren op de instantie van de auteur:

1. Ga naar **Hulpmiddelen** > **Veiligheid** > **Gebruikers**.
1. Controleer of uw technische account de gebruikerslijst is en selecteer deze.
1. Klik het **lusje van Groepen** zodat kunt u verifiëren dat de gebruiker een deel van de groep is die aan uw productprofiel beantwoordt. Deze gebruiker is ook lid van een handvol andere groepen, waaronder Medewerkers:

   ![ Lidmaatschap van de Groep ](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vóór medio 2023, voordat het mogelijk was meerdere referenties te maken, kregen klanten geen instructies om een productprofiel te maken in de Adobe Admin Console. Als zodanig was de technische rekening niet geassocieerd met een andere groep dan &quot;Medewerkers&quot; in de AEM as a Cloud Service-instantie. Ter wille van de consistentie wordt aanbevolen voor deze technische account een productprofiel in de Adobe Admin Console te maken zoals hierboven beschreven, en de bestaande technische account aan die groep toe te voegen.

<u>**plaats de aangewezen Toestemmingen van de Groep**</u>

Tot slot vorm de groep met de aangewezen toestemmingen noodzakelijk zodat kunt u uw APIs roepen of sluiten geschikt.

1. Logon aan de aangewezen auteursinstantie, en navigeer aan **Montages** > **Veiligheid** > **Toestemmingen**
1. Zoek de naam van de groep die overeenkomt met het productprofiel in het linkerdeelvenster (in dit geval alleen-lezen API&#39;s) en selecteer de naam:

   ![ Onderzoek naar Groep ](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klik op de knop Bewerken in het volgende venster:

   ![ geeft toestemmingen uit ](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Wijzig de toestemmingen geschikt en klik **sparen**

   ![ bevestigt het uitgeven van toestemmingen ](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Meer informatie over het Adobe Identity Management System (IMS) en AEM gebruikers en groepen. Zie de [ documentatie ](/help/security/ims-support.md).

## Developer Flow {#developer-flow}

Ontwikkelaars willen waarschijnlijk testen met een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen doet voor een ontwikkelings-AEM as a Cloud Service-ontwikkelomgeving. Omdat ontwikkelaars echter niet noodzakelijkerwijs beschikken over IMS-beheerdersmachtigingen, kan de Adobe niet aannemen dat zij de JWT-drager kunnen genereren die in de reguliere server-naar-server-flow wordt beschreven. Daarom verstrekt de Adobe een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren die in verzoeken aan milieu&#39;s op AEM as a Cloud Service kan worden gebruikt waar zij toegang tot hebben.

Zie de [ documentatie van de Richtlijnen van de Ontwikkelaar ](/help/implementing/developing/introduction/development-guidelines.md#crxde-lite-and-developer-console) voor informatie over de vereiste toestemmingen om de de ontwikkelaarsconsole van AEM as a Cloud Service te gebruiken.

>[!NOTE]
>
>Het token voor lokale ontwikkelingstoegang is maximaal 24 uur geldig waarna het opnieuw moet worden gegenereerd met dezelfde methode.

Ontwikkelaars kunnen dit token gebruiken om aanroepen uit te voeren vanuit hun niet-AEM testtoepassing naar een AEM as a Cloud Service-omgeving. De ontwikkelaar gebruikt dit token doorgaans met de niet-AEM toepassing op zijn eigen laptop. Bovendien is de AEM als Cloud doorgaans een omgeving die geen productie heeft.

De ontwikkelaarsstroom omvat de volgende stappen:

* Een toegangstoken genereren vanuit de Developer Console
* Roep de AEM toepassing met het toegangstoken aan.

Ontwikkelaars kunnen ook API-aanroepen uitvoeren naar een AEM project dat op hun lokale computer wordt uitgevoerd. In dat geval is een toegangstoken niet nodig.

### Het produceren van het Token van de Toegang {#generating-the-access-token}

1. Ga naar het **Lokale teken** onder **Integraties**
1. Klik **krijgen Token van de Lokale Ontwikkeling** in Developer Console zodat kunt u een toegangstoken produceren.

### Vraag de AEM Toepassing met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een milieu van AEM as a Cloud Service, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Authorization&quot; de waarde `"Bearer <access_token>"` .

## Referenties vernieuwen {#refresh-credentials}

Standaard verlopen de gegevens op AEM as a Cloud Service na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden.

Ga als volgt te werk om deze vernieuwingsextensie te bereiken:

* Gebruik **certificaat** knoop onder **Integraties** toevoegen - **Technische Rekeningen** in Developer Console, zoals hieronder getoond

  ![ Referentie verfrist zich ](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nadat u op de knop hebt gedrukt, wordt een set referenties gegenereerd die een nieuw certificaat bevat. Installeer de nieuwe geloofsbrieven op uw off-AEM server en zorg ervoor dat de connectiviteit zoals verwacht is, zonder de oude geloofsbrieven te verwijderen.
* Zorg ervoor dat de nieuwe geloofsbrieven in plaats van de oude worden gebruikt wanneer het produceren van het toegangstoken.
* U kunt desgewenst het vorige certificaat intrekken (en vervolgens verwijderen), zodat het niet langer kan worden gebruikt voor verificatie met AEM as a Cloud Service.

## Intrekking van referenties {#credentials-revocation}

Als de persoonlijke sleutel in het gedrang komt, moet u referenties maken met een nieuw certificaat en een nieuwe persoonlijke sleutel. Nadat uw toepassing de nieuwe geloofsbrieven gebruikt zodat kunt u toegangstokens produceren, kunt u de oude certificaten intrekken en schrappen door het volgende te doen:

1. Voeg eerst de nieuwe toets toe. Met deze sleutel worden referenties gegenereerd met een nieuwe persoonlijke sleutel en een nieuw certificaat. De nieuwe privé sleutel wordt duidelijk in het gebruikersinterface als **huidig** en wordt daarom gebruikt voor alle nieuwe geloofsbrieven voor deze technische rekening die door:gaan. De referenties die aan de oudere persoonlijke sleutels zijn gekoppeld, zijn nog steeds geldig tot ze zijn ingetrokken. Om deze herroeping te bereiken, selecteer de drie punten (**...**) onder uw huidige technische rekening, dan uitgezocht **voeg nieuwe privé sleutel** toe:

   ![ voeg nieuwe privé sleutel ](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png) toe

1. Selecteer **toevoegen** bij de herinnering die volgt:

   ![ Bevestig het toevoegen van nieuwe privé sleutel ](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Een nieuw doorbladert lusje met de nieuwe geloofsbrieven opent en het gebruikersinterface wordt bijgewerkt om zowel privé sleutels met nieuwe te tonen duidelijk als **huidig**:

   ![ Persoonlijke sleutels in UI ](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installeer de nieuwe referenties op de niet-AEM server en zorg ervoor dat de connectiviteit naar behoren functioneert. Zie [ Server aan de sectie van de Stroom van de Server ](#the-server-to-server-flow) voor details.
1. Intrekken het oude certificaat door de drie punten (**te selecteren...**) rechts van het certificaat, en het selecteren **Intrekken**:

   ![ Intrekken certificaat ](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Dan, bevestig de herroeping in de volgende herinnering door de **Revoke** knoop te drukken:

   ![ intrekken certificaatbevestiging ](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Ten slotte verwijdert u het gecompromitteerde certificaat.
