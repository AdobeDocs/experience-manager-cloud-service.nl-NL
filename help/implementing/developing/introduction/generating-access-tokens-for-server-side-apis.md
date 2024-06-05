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

Sommige architecturen baseren zich op het maken van vraag aan AEM as a Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om as a Cloud Service AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM as a Cloud Service [Ontwerpconsole](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## De server-naar-server stroom {#the-server-to-server-flow}

Gebruikers met een IMS org-beheerdersrol en die lid zijn van het AEM Gebruikers of AEM Beheerdersproductprofiel op AEM auteur, kunnen een set aanmeldingsgegevens genereren op basis van AEM as a Cloud Service. Elke referentie is een JSON-payload die een certificaat (de openbare sleutel), een persoonlijke sleutel en een technische account bevat die bestaat uit een `clientId` en `clientSecret`. Die geloofsbrieven kunnen later door een gebruiker met de AEM as a Cloud Service de beheerderrol van het Milieu worden teruggewonnen en zouden op een niet-AEM server moeten worden geïnstalleerd en zorgvuldig als geheime sleutel worden behandeld. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een getekende JWT-token te maken, dat wordt uitgewisseld met de Adobe Identity Management Services (IMS) voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te maken. Het certificaat in de geloofsbrieven verloopt na één jaar door gebrek, maar zij kunnen worden vernieuwd wanneer nodig, zoals beschreven [hier](#refresh-credentials).

De server-aan-server stroom impliceert de volgende stappen:

* De referenties ophalen op AEM as a Cloud Service via de ontwikkelaarsconsole
* Installeer de geloofsbrieven voor AEM as a Cloud Service op een niet AEM server die vraag aan AEM doet
* Een JWT-token genereren en deze token uitwisselen voor een toegangstoken met IMS API&#39;s van de Adobe
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### De AEM as a Cloud Service referenties ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving. Een gebruiker met de AEM as a Cloud Service de beheerderrol van het Milieu kan geloofsbrieven creëren, bekijken of beheren.

Klikken **Nieuwe technische account maken** Er wordt een set met referenties gemaakt die client-id, clientgeheim, persoonlijke sleutel, certificaat en configuratie voor auteur- en publicatieniveaus van de omgeving bevat, ongeacht de podselectie.

![Een nieuwe technische account maken](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Er wordt een nieuw browsertabblad geopend waarin de referenties worden weergegeven. U kunt deze weergave gebruiken om de referenties te downloaden door op het downloadpictogram naast de statustitel te drukken:

![Credentials downloaden](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nadat de geloofsbrieven worden gecreeerd, zullen zij onder verschijnen **Technische rekeningen** in de **Integraties** sectie:

![Credentials weergeven](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Gebruikers kunnen de referenties later weergeven met de actie Weergave. Bovendien kunnen gebruikers, zoals verderop in het artikel wordt beschreven, de referenties voor dezelfde technische account bewerken. Ze kunnen deze bewerking uitvoeren door een persoonlijke sleutel of certificaat te maken, voor gevallen waarin het certificaat moet worden vernieuwd of ingetrokken.

Gebruikers met de AEM rol Beheerder van het Milieu kunnen later geloofsbrieven voor extra technische rekeningen creëren. Deze mogelijkheid is handig wanneer verschillende API&#39;s verschillende toegangsvereisten hebben. Bijvoorbeeld lezen versus lezen-schrijven.

>[!NOTE]
>
>Klanten kunnen maximaal tien technische accounts maken, waaronder de accounts die al zijn verwijderd.

>[!IMPORTANT]
>
>Een IMS org beheerder (typisch de zelfde gebruiker die het milieu door middel van de Manager van de Wolk) leverde, die ook een lid van het Profiel van het Product van de Gebruikers of van AEM van de Beheerders op AEM Auteur is, moet eerst tot de Console van de Ontwikkelaar toegang hebben. Klik vervolgens op **Nieuwe technische account maken** voor de geloofsbrieven die moeten worden geproduceerd en later teruggewonnen door een gebruiker met admintoestemmingen aan het AEM as a Cloud Service milieu. Als de IMS org beheerder nog niet de technische rekening heeft gecreeerd, deelt een bericht hen mee dat zij de IMS org rol van de Beheerder nodig hebben.

### Installeer de AEM servicereferentials op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De toepassing die vraag aan AEM maakt zou tot de geloofsbrieven voor AEM as a Cloud Service moeten kunnen toegang hebben, behandelend het als geheim.

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

>[!NOTE]
>Als er veelvoudige geloofsbrieven zijn, zorg ervoor om het aangewezen jsdossier voor de API vraag aan AEM van verwijzingen te voorzien die later wordt aangehaald.

### De AEM-API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`. Als u bijvoorbeeld `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Ten eerste moet er een nieuw productprofiel worden gemaakt in de Adobe Admin Console.

1. Ga naar de Adobe Admin Console op [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/).
1. Druk op **Beheren** koppeling onder de **Producten en services** aan de linkerkant.
1. Selecteren **AEM as a Cloud Service**.
1. Druk op **Nieuw profiel** knop.

   ![Nieuw profiel](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Geef het profiel een naam en druk op **Opslaan**.

   ![Profiel opslaan](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Selecteer het profiel dat u hebt gemaakt in de profiellijst.
1. Selecteren **Gebruiker toevoegen**.

   ![Gebruiker toevoegen](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Voeg de technische account toe die u hebt gemaakt (in dit geval `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) en klik op **Opslaan**.

   ![Technisch account toevoegen](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Wacht 10 minuten op de veranderingen om van kracht te worden en een API vraag aan AEM met een toegangstoken te maken die van de nieuwe referentie wordt geproduceerd. Als cURL-opdracht wordt deze weergegeven als in dit voorbeeld:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nadat u de API-aanroep hebt gemaakt, wordt het productprofiel weergegeven als een gebruikersgroep in de AEM as a Cloud Service auteur-instantie, met de juiste technische account als lid van die groep.

Ga als volgt te werk om deze informatie te controleren:

1. Meld u aan bij de instantie van de auteur.
1. Ga naar **Gereedschappen** > **Beveiliging** en klik vervolgens op de knop **Groepen** kaart.
1. Zoek de naam van het profiel dat u in de lijst met groepen hebt gemaakt en klik erop:

   ![Groepsprofiel](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Schakel in het volgende venster over naar de **Leden** tabblad en controleer of de technische rekening daar correct wordt vermeld:

   ![Tabblad Leden](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


U kunt ook controleren of de technische account in de lijst van de gebruiker wordt weergegeven door de onderstaande stappen uit te voeren op de instantie van de auteur:

1. Ga naar **Gereedschappen** > **Beveiliging** > **Gebruikers**.
1. Controleer of uw technische account de gebruikerslijst is en selecteer deze.
1. Klik op de knop **Groepen** zodat u kunt controleren of de gebruiker deel uitmaakt van de groep die overeenkomt met uw productprofiel. Deze gebruiker is ook lid van een handvol andere groepen, waaronder Medewerkers:

   ![Groepslidmaatschap](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vóór medio 2023, voordat het mogelijk was meerdere referenties te maken, kregen klanten geen instructies om een productprofiel te maken in de Adobe Admin Console. Als zodanig was de technische rekening in AEM as a Cloud Service instantie niet geassocieerd met een andere groep dan &quot;Medewerkers&quot;. Ter wille van de consistentie wordt aanbevolen voor deze technische account een productprofiel in de Adobe Admin Console te maken zoals hierboven beschreven, en de bestaande technische account aan die groep toe te voegen.

<u>**De juiste machtigingen voor groepen instellen**</u>

Tot slot vorm de groep met de aangewezen toestemmingen noodzakelijk zodat kunt u uw APIs roepen of sluiten geschikt.

1. Meld u aan bij de juiste instantie van de auteur en ga naar **Instellingen** > **Beveiliging** > **Machtigingen**
1. Zoek de naam van de groep die overeenkomt met het productprofiel in het linkerdeelvenster (in dit geval alleen-lezen API&#39;s) en selecteer de naam:

   ![Zoeken naar groep](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klik op de knop Bewerken in het volgende venster:

   ![Machtigingen bewerken](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Wijzig de machtigingen op de juiste wijze en klik op **Opslaan**

   ![Bewerken van machtigingen bevestigen](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Meer informatie over het Adobe Identity Management System (IMS) en AEM gebruikers en groepen. Zie de [documentatie](/help/security/ims-support.md).

## Developer Flow {#developer-flow}

Ontwikkelaars willen waarschijnlijk testen met een ontwikkelingsexemplaar van hun niet-AEM toepassing (die op hun laptop wordt uitgevoerd of wordt gehost) die aanvragen doet voor een ontwikkelomgeving AEM as a Cloud Service ontwikkelomgeving. Omdat ontwikkelaars echter niet noodzakelijkerwijs beschikken over IMS-beheerdersmachtigingen, kan de Adobe niet aannemen dat zij de JWT-drager kunnen genereren die in de reguliere server-naar-server-flow wordt beschreven. Daarom verstrekt de Adobe een mechanisme voor een ontwikkelaar om een toegangstoken direct te produceren dat in verzoeken aan milieu&#39;s op AEM as a Cloud Service kan worden gebruikt waarop zij toegang hebben.

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

1. Ga naar de **Lokaal token** krachtens **Integraties**
1. Klikken **Token voor lokale ontwikkeling ophalen** in de Console van de Ontwikkelaar zodat kunt u een toegangstoken produceren.

### Vraag de AEM Toepassing met een Token van de Toegang {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`.

## Referenties vernieuwen {#refresh-credentials}

Standaard verlopen de referenties op AEM as a Cloud Service na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden.

Ga als volgt te werk om deze vernieuwingsextensie te bereiken:

* Gebruik de **Certificaat toevoegen** knop onder **Integraties** - **Technische rekeningen** in de ontwikkelaarsconsole, zoals hieronder getoond

  ![Referentievernieuwen](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nadat u op de knop hebt gedrukt, wordt een set referenties gegenereerd die een nieuw certificaat bevat. Installeer de nieuwe geloofsbrieven op uw off-AEM server en zorg ervoor dat de connectiviteit zoals verwacht is, zonder de oude geloofsbrieven te verwijderen.
* Zorg ervoor dat de nieuwe geloofsbrieven in plaats van de oude worden gebruikt wanneer het produceren van het toegangstoken.
* U kunt desgewenst het vorige certificaat intrekken (en vervolgens verwijderen), zodat het niet langer kan worden gebruikt voor verificatie met AEM as a Cloud Service.

## Intrekking van referenties {#credentials-revocation}

Als de persoonlijke sleutel in het gedrang komt, moet u referenties maken met een nieuw certificaat en een nieuwe persoonlijke sleutel. Nadat uw toepassing de nieuwe geloofsbrieven gebruikt zodat kunt u toegangstokens produceren, kunt u de oude certificaten intrekken en schrappen door het volgende te doen:

1. Voeg eerst de nieuwe toets toe. Met deze sleutel worden referenties gegenereerd met een nieuwe persoonlijke sleutel en een nieuw certificaat. De nieuwe persoonlijke sleutel wordt in de gebruikersinterface gemarkeerd als **huidig** en wordt daarom gebruikt voor alle nieuwe geloofsbrieven voor deze technische rekening die verder gaat. De referenties die aan de oudere persoonlijke sleutels zijn gekoppeld, zijn nog steeds geldig tot ze zijn ingetrokken. Selecteer de drie stippen (**...**) onder uw huidige technische account, selecteert u **Nieuwe persoonlijke sleutel toevoegen**:

   ![Nieuwe persoonlijke sleutel toevoegen](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Selecteren **Toevoegen** op het volgende tijdstip:

   ![Toevoegen van nieuwe persoonlijke sleutel bevestigen](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Er wordt een nieuw tabblad voor bladeren geopend met de nieuwe referenties en de gebruikersinterface wordt bijgewerkt zodat zowel de persoonlijke sleutel als de nieuwe wordt weergegeven met de code **huidig**:

   ![Persoonlijke sleutels in de gebruikersinterface](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installeer de nieuwe referenties op de niet-AEM server en zorg ervoor dat de connectiviteit naar behoren functioneert. Zie [Server naar server, sectie Stroom](#the-server-to-server-flow) voor meer informatie.
1. Het oude certificaat intrekken door de drie stippen te selecteren (**...**) rechts van het certificaat en selecteert u **Intrekken**:

   ![Certificaat intrekken](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Bevestig vervolgens de intrekking in de volgende vraag door op de knop **Intrekken** knop:

   ![Certificaatbevestiging intrekken](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Ten slotte verwijdert u het gecompromitteerde certificaat.
