---
title: Toegangstokens genereren voor server-side API's
description: Leer hoe u communicatie tussen een externe server en AEM as a Cloud Service vergemakkelijkt door een beveiligd JWT Token te genereren
exl-id: 20deaf8f-328e-4cbf-ac68-0a6dd4ebf0c9
source-git-commit: dd869397feca593f93ee8ed5030828e01cc45c4d
workflow-type: tm+mt
source-wordcount: '2132'
ht-degree: 0%

---

# Toegangstokens genereren voor server-side API&#39;s {#generating-access-tokens-for-server-side-apis}

Sommige architecturen baseren zich op het maken van vraag aan AEM as a Cloud Service van een toepassing die op een server buiten AEM infrastructuur wordt ontvangen. Bijvoorbeeld, een mobiele toepassing die een server roept, die dan API verzoeken om as a Cloud Service AEM.

De server-aan-server stroom wordt hieronder beschreven, samen met een vereenvoudigde stroom voor ontwikkeling. De AEM as a Cloud Service [Ontwerpconsole](development-guidelines.md#crxde-lite-and-developer-console) wordt gebruikt om tokens te produceren nodig voor het authentificatieproces.

<!-- Alexandru: hiding this until the tutorials reflect the new UI

>[!NOTE]
>
>In addition to this documentation, you can also consult the tutorials on [Token-based authentication for AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/overview.html?lang=en#authentication) and [Getting a Login Token for Integrations](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-getting-login-token-integrations.html). -->

## De server-naar-server stroom {#the-server-to-server-flow}

Een gebruiker met een IMS org beheerderrol, en die ook een lid van het Profiel van het Product van de Gebruikers of van AEM op Auteur AEM is, kan een reeks AEM as a Cloud Service geloofsbrieven produceren, elk waarvan een nuttige lading JSON is die een certificaat (de openbare sleutel), een privé sleutel, en een technische rekening omvat die uit een `clientId` en `clientSecret`. Die geloofsbrieven kunnen later door een gebruiker met de AEM as a Cloud Service de beheerderrol van het Milieu worden teruggewonnen en zouden op een niet-AEM server moeten worden geïnstalleerd en zorgvuldig behandeld als geheime sleutel. Dit JSON-indelingsbestand bevat alle gegevens die vereist zijn voor integratie met een AEM as a Cloud Service API. De gegevens worden gebruikt om een getekende JWT-token te maken, dat wordt uitgewisseld met de Adobe Identity Management Services (IMS) voor een IMS-toegangstoken. Dit toegangstoken kan dan als het authentificatietoken van de Drager worden gebruikt om verzoeken aan AEM as a Cloud Service te maken. Het certificaat in de geloofsbrieven verlopen na één jaar door gebrek, maar zij kunnen worden vernieuwd wanneer nodig, zoals beschreven [hier](#refresh-credentials).

De server-aan-server stroom impliceert de volgende stappen:

* De AEM as a Cloud Service gegevens ophalen uit de ontwikkelaarsconsole
* Installeer de AEM as a Cloud Service geloofsbrieven op een niet AEM server die vraag aan AEM maken
* Een JWT-token genereren en dat token uitwisselen voor een toegangstoken met behulp van Adobe API&#39;s
* De AEM-API aanroepen met het toegangstoken als een token voor Dradenverificatie
* Stel de juiste machtigingen in voor de gebruiker van de technische account in de AEM-omgeving

### De AEM as a Cloud Service referenties ophalen {#fetch-the-aem-as-a-cloud-service-credentials}

Gebruikers met toegang tot de AEM as a Cloud Service ontwikkelaarsconsole zien het tabblad Integraties in de Developer Console voor een bepaalde omgeving. Een gebruiker met de AEM as a Cloud Service rol van de Beheerder van het Milieu kan geloofsbrieven creëren, bekijken of beheren.

Klik op de knop **Nieuwe technische account maken** er wordt een nieuwe set referenties gemaakt met de id van de client, het clientgeheim, de persoonlijke sleutel, het certificaat en de configuratie voor auteur- en publicatieniveaus van de omgeving, ongeacht de podselectie.

![Een nieuwe technische account maken](/help/implementing/developing/introduction/assets/s2s-createtechaccount.png)

Er wordt een nieuw browsertabblad geopend met de referenties. U kunt deze weergave gebruiken om de referenties te downloaden door op het downloadpictogram naast de statustitel te drukken:

![Credentials downloaden](/help/implementing/developing/introduction/assets/s2s-credentialdownload.png)

Nadat de geloofsbrieven worden gecreeerd, zullen zij onder verschijnen **Technische rekeningen** in de **Integraties** sectie:

![Credentials weergeven](/help/implementing/developing/introduction/assets/s2s-viewcredentials.png)

Gebruikers kunnen de referenties later weergeven met de actie Weergave. Bovendien kunnen gebruikers, zoals verderop in het artikel wordt beschreven, de referenties voor dezelfde technische account wijzigen door een nieuwe persoonlijke sleutel of een nieuw certificaat te maken, voor gevallen waarin het certificaat moet worden vernieuwd of ingetrokken.

Gebruikers met de AEM as a Cloud Service rol Beheerder van het Milieu kunnen later nieuwe geloofsbrieven voor extra technische rekeningen tot stand brengen. Dit is handig wanneer verschillende API&#39;s verschillende toegangsvereisten hebben. Bijvoorbeeld lezen versus lezen-schrijven.

>[!NOTE]
>
>Klanten kunnen maximaal 10 technische accounts maken, waaronder accounts die al zijn verwijderd.

>[!IMPORTANT]
>
>Een IMS org-beheerder (doorgaans dezelfde gebruiker die de omgeving heeft ingericht via Cloud Manager), die ook lid moet zijn van het productprofiel AEM gebruikers of AEM beheerders van AEM-auteur, moet eerst toegang krijgen tot de Developer Console en op de knop **Nieuwe technische account maken** om de geloofsbrieven te produceren en later terug te winnen door een gebruiker met admin toestemmingen aan het AEM as a Cloud Service milieu. Als de IMS org beheerder dit niet heeft gedaan, zal een bericht hen informeren dat zij de rol van de Beheerder IMS org nodig hebben.

### Installeer de AEM servicereferenties op een niet-AEM server {#install-the-aem-service-credentials-on-a-non-aem-server}

De toepassing die vraag aan AEM maakt zou tot de AEM as a Cloud Service geloofsbrieven moeten kunnen toegang hebben, behandelend het als geheim.

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

>[!NOTE]
>Als er veelvoudige geloofsbrieven zijn, zorg ervoor om het aangewezen jsdossier voor de API vraag aan AEM van verwijzingen te voorzien die later zal worden aangehaald.

### De AEM-API aanroepen {#calling-the-aem-api}

Maak de aangewezen server-aan-server API vraag aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`. Als u bijvoorbeeld `curl`:

```curlc
curl -H "Authorization: Bearer <your_ims_access_token>" https://author-p123123-e23423423.adobeaemcloud.com/content/dam.json
```

### Stel de juiste machtigingen voor de gebruiker van de technische account in AEM {#set-the-appropriate-permissions-for-the-technical-account-user-in-aem}

Ten eerste moet er een nieuw productprofiel worden gemaakt in de Adobe Admin Console. U kunt dit bereiken door deze stappen te volgen:

1. Ga naar de Adobe Admin Console op [https://adminconsole.adobe.com/](https://adminconsole.adobe.com/)
1. Druk op **Beheren** koppeling onder de **Producten en services** links.
1. Selecteren **AEM as a Cloud Service**
1. Druk op **Nieuw profiel** knop

   ![Nieuw profiel](/help/implementing/developing/introduction/assets/s2s-newproductprofile.png)

1. Geef het profiel een naam en druk op **Opslaan**

   ![Profiel opslaan](/help/implementing/developing/introduction/assets/s2s-saveprofile.png)

1. Selecteer het profiel dat u zojuist hebt gemaakt in de profiellijst
1. Druk op **Gebruiker toevoegen** knop

   ![Gebruiker toevoegen](/help/implementing/developing/introduction/assets/s2s-addusers.png)

1. Voeg de technische account toe die u zojuist hebt gemaakt (in dit geval `84b2c3a2-d60a-40dc-84cb-e16b786c1673@techacct.adobe.com`) en drukken op **Opslaan**

   ![Technisch account toevoegen](/help/implementing/developing/introduction/assets/s2s-addtechaccount.png)

1. Wacht 10 minuten op de veranderingen om van kracht te worden en een API vraag aan AEM met een toegangstoken te maken die van de nieuwe referentie wordt geproduceerd. Als cURL-opdracht wordt deze weergegeven als in dit voorbeeld:

   `curl -H "Authorization: Bearer <access_token>" https://author-pXXXXX-eXXXXX.adobeaemcloud.net/content/dam.json `


Nadat u de API-aanroep hebt gemaakt, wordt het productprofiel weergegeven als een gebruikersgroep in de AEM as a Cloud Service auteur-instantie, met de juiste technische account als lid van die groep.

Om dit te controleren, moet u:

1. Aanmelden bij de instantie van de auteur
1. Ga naar **Gereedschappen** - **Beveiliging** en klik op de knop **Groepen** kaart
1. Zoek de naam van het profiel dat u in de lijst met groepen hebt gemaakt en klik erop:

   ![Groepsprofiel](/help/implementing/developing/introduction/assets/s2s-groupprofile.png)

1. Schakel in het volgende venster over naar de **Leden** tabblad en controleer of de technische rekening daar correct wordt vermeld:

   ![Tabblad Leden](/help/implementing/developing/introduction/assets/s2s-techaccountmembers.png)


U kunt ook controleren of de technische account wordt weergegeven in de lijst met gebruikers door de onderstaande stappen uit te voeren op de instantie van de auteur:

1. Ga naar **Gereedschappen** - **Beveiliging** - **Gebruikers**
1. Controleer of uw technische account de gebruikerslijst is en klik erop
1. Klik op de knop **Groepen** om te controleren of de gebruiker deel uitmaakt van de groep die overeenkomt met uw productprofiel. Deze gebruiker is ook lid van een handvol andere groepen, waaronder Medewerkers:

   ![Groepslidmaatschap](/help/implementing/developing/introduction/assets/s2s-groupmembership.png)

>[!NOTE]
>
>Vóór medio 2023, alvorens het mogelijk was om veelvoudige geloofsbrieven tot stand te brengen, werden de klanten niet geleid om een productprofiel in de console van Admin van de Adobe tot stand te brengen en zo werd de technische rekening niet geassocieerd met een groep buiten &quot;Medewerkers&quot;in de AEM as a Cloud Service instantie. Ter wille van de consistentie wordt aanbevolen voor deze technische account een nieuw productprofiel in de Adobe Admin Console te maken zoals hierboven beschreven, en de bestaande technische account aan die groep toe te voegen.

<u>**Stel de juiste machtigingen voor groepen in**</u>

Tot slot vorm de groep met de aangewezen toestemmingen nodig aan om uw APIs aan te halen of te sluiten geschikt. U kunt dit doen door:

1. Aanmelden bij de juiste instantie van de auteur en naar **Instellingen** - **Beveiliging** - **Machtigingen**
1. Zoek de naam van de groep die overeenkomt met het productprofiel in het linkerdeelvenster (in dit geval alleen-lezen API&#39;s) en klik erop:

   ![Zoeken naar groep](/help/implementing/developing/introduction/assets/s2s-searchforgroup.png)

1. Klik op de knop Bewerken in het volgende venster:

   ![Machtigingen bewerken](/help/implementing/developing/introduction/assets/s2s-editpermissions.png) 

1. Wijzig de machtigingen op de juiste wijze en klik op **Opslaan**

   ![Bewerken van machtigingen bevestigen](/help/implementing/developing/introduction/assets/s2s-confirmeditpermissions.png)

>[!INFO]
>
>Meer informatie over het Adobe Identity Management System (IMS) en AEM gebruikers en groepen vindt u in het [documentatie](/help/security/ims-support.md).

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

1. Ga naar de **Lokaal token** krachtens **Integraties**
1. Klik op de knop **Token voor lokale ontwikkeling ophalen** in de Ontwikkelaarsconsole om een toegangstoken te produceren.

### Roep de AEM Toepassing met een Token van de Toegang aan {#call-the-aem-application-with-an-access-token}

Maak de aangewezen server-aan-server API vraag van de niet-AEM toepassing aan een AEM as a Cloud Service milieu, met inbegrip van het toegangstoken in de kopbal. Gebruik dus voor de header &quot;Autorisatie&quot; de waarde `"Bearer <access_token>"`.

## Referenties vernieuwen {#refresh-credentials}

Standaard verlopen de AEM as a Cloud Service gegevens na een jaar. Om de dienstcontinuïteit te verzekeren, hebben de ontwikkelaars de optie om de geloofsbrieven te verfrissen, die hun beschikbaarheid voor een extra jaar uitbreiden.

Om dit te bereiken, kunt u:

* Gebruik de **Certificaat toevoegen** knop onder **Integraties** - **Technische rekeningen** in de ontwikkelaarsconsole, zoals hieronder getoond

   ![Referentie vernieuwen](/help/implementing/developing/introduction/assets/s2s-credentialrefresh.png)

* Nadat u op de knop hebt gedrukt, wordt een set referenties gegenereerd die een nieuw certificaat bevat. Installeer de nieuwe geloofsbrieven op uw off-AEM server en zorg ervoor dat de connectiviteit zoals verwacht is, zonder de oude geloofsbrieven te verwijderen 
* Zorg ervoor de nieuwe geloofsbrieven in plaats van de oude worden gebruikt wanneer het produceren van het toegangstoken
* U kunt desgewenst het vorige certificaat intrekken (en vervolgens verwijderen), zodat het niet langer kan worden gebruikt voor verificatie met AEM as a Cloud Service.

## Intrekking van referenties {#credentials-revocation}

Als de persoonlijke sleutel in het gedrang komt, moet u referenties maken met een nieuw certificaat en een nieuwe persoonlijke sleutel. Nadat uw toepassing de nieuwe geloofsbrieven gebruikt om toegangstokens te produceren, kunt u de oude certificaten intrekken en schrappen.

U kunt dit doen door deze stappen te volgen:

1. Voeg eerst de nieuwe toets toe. Hiermee worden referenties gegenereerd met een nieuwe persoonlijke sleutel en een nieuw certificaat. De nieuwe persoonlijke sleutel wordt in de gebruikersinterface gemarkeerd als **huidig** en zal dus worden gebruikt voor alle nieuwe geloofsbrieven voor deze technische rekening. De referenties die aan de oudere persoonlijke sleutels zijn gekoppeld, zijn nog steeds geldig tot ze zijn ingetrokken. Om dit te bereiken drukt u op de drie puntjes (**...**) onder uw huidige technische account en druk op **Nieuwe persoonlijke sleutel toevoegen**:

   ![Nieuwe persoonlijke sleutel toevoegen](/help/implementing/developing/introduction/assets/s2s-addnewprivatekey.png)

1. Druk **Toevoegen** op het volgende tijdstip:

   ![Toevoegen van nieuwe persoonlijke sleutel bevestigen](/help/implementing/developing/introduction/assets/s2s-addprivatekeyconfirm.png)

   Er wordt een nieuw tabblad voor bladeren geopend met de nieuwe onderliggende items en de gebruikersinterface wordt bijgewerkt met de privétoetsen, waarbij de nieuwe wordt gemarkeerd als **huidig**:

   ![Persoonlijke sleutels in de gebruikersinterface](/help/implementing/developing/introduction/assets/s2s-twokeys.png)

1. Installeer de nieuwe referenties op de niet-AEM server en zorg ervoor dat de connectiviteit naar behoren functioneert. Zie de [Server naar server, sectie Stroom](#the-server-to-server-flow) voor meer informatie over hoe u dit kunt doen
1. Intrekken van het oude certificaat. U kunt dit doen door de drie puntjes te selecteren (**...**) rechts van het certificaat en door te drukken op **Intrekken**:

   ![Certificaat intrekken](/help/implementing/developing/introduction/assets/s2s-revokecert.png)

   Bevestig vervolgens de intrekking in de volgende vraag door op de knop **Intrekken** knop:

   ![Certificaatbevestiging intrekken](/help/implementing/developing/introduction/assets/s2s-revokecertificateconfirmation.png)

1. Ten slotte verwijdert u het gecompromitteerde certificaat.
