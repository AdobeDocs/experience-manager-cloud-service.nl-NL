---
title: OAuth2 Steun voor de Dienst van de Post
description: Oauth2 Steun voor de Dienst van de Post in Adobe Experience Manager als Cloud Service
source-git-commit: b46062697b25aa8d3f215a8a4249f5203bec268e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# OAuth2-ondersteuning voor de e-mailservice {#oauth2-support-for-the-mail-service}

AEM als Cloud Service biedt OAuth2 steun voor zijn geïntegreerde Dienst van de Post aan, om organisaties toe te staan om e-mailvereisten te beveiligen.

U kunt OAuth voor veelvoudige e-mailleveranciers vormen. Hieronder zijn geleidelijke instructies voor het vormen van de AEMDienst van de Post via OAuth2 met Microsoft Office 365 Vooruitzichten voor authentiek te verklaren. Andere verkopers kunnen op een gelijkaardige manier worden gevormd.

Voor meer informatie over de AEM als Dienst van de Post van de Cloud Service, zie [Verzendend E-mail](/help/implementing/developing/introduction/development-guidelines.md#sending-email).

## Microsoft Outlook {#microsoft-outlook}

1. Ga naar [https://portal.azure.com/](https://portal.azure.com/) en meld u aan.
1. Zoek naar **Azure Actieve Folder** in de onderzoeksbar en klik op het resultaat. U kunt ook rechtstreeks naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) bladeren
1. Klik op **Toepassingsregistratie** - **Nieuwe registratie**

   ![](assets/oauth-outlook1.png)

1. Vul de informatie in volgens uw vereisten en klik op **Register**
1. Ga naar de nieuwe app en selecteer **API-machtigingen**
1. Ga naar **Machtiging toevoegen** - **Machtiging grafiek** - **Gedelegeerde machtigingen**
1. Selecteer de onderstaande machtigingen voor uw app en klik op **Machtiging toevoegen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Ga naar **Verificatie** - **Voeg een platform** toe - **Web**, en in **Redirect Urls** sectie, voeg hieronder URLs - met en toe zonder een voorwaartse schuine streep:
   * `http://localhost/`
   * `http://localhost`
1. Druk **Configure** na het toevoegen van elke URL en vorm uw montages volgens uw vereisten
1. Ga vervolgens naar **Certificaten en geheimen**, klik op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let op dit geheim voor later gebruik
1. Druk **Overzicht** in de linkerhand ruit en kopieer de waarden voor **toepassings (cliënt) identiteitskaart** en **Folder (huurder) ID** voor later gebruik

Om opnieuw te verpakken, zult u aan de volgende informatie nodig hebben om OAuth2 voor de dienst van de Post op de AEM te vormen:

* Auth URL, die met huurderidentiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* De token-URL, die wordt samengesteld met de huurder-id. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Vernieuwen URL, die met huurder identiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Client-id
* Het clientgeheim

### Het genereren van het vernieuwingstoken {#generating-the-refresh-token}

Daarna, moet u verfrissen teken produceren, dat een deel van de configuratie OSGi in een verdere stap zal zijn.

U kunt dit doen door deze stappen te volgen:

1. Open de volgende URL in de browser nadat u `clientID` en `tenantID` hebt vervangen door de waarden die specifiek zijn voor uw account: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?client_id=<clientId>&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20EWS.AccessAsUser.All%20https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office365.com%2FMail.Read%20https%3A%2F%2Foutlook.office365.com%2FMail.Send%20openid%20offline_access&state=12345`
1. Toestemming toestaan indien gevraagd
1. De URL wordt omgeleid naar een nieuwe locatie, in de volgende indeling: `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Kopieer de waarde van `<code>` in het bovenstaande voorbeeld
1. Gebruik het volgende cURL bevel om te krijgen refreshToken. U moet de huurderID, clientID en clientSecret vervangen door de waarden voor uw account en de waarde voor `<code>`:

   `curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
--data-urlencode 'client_id=<clientID>' \
--data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
--data-urlencode 'redirect_uri=http://localhost' \
--data-urlencode 'grant_type=authorization_code' \
--data-urlencode 'client_secret=<clientSecret>' \
--data-urlencode 'code=<code>'`

1. Noteer refreshToken en accessToken.

### Tokens {#validating-the-tokens} valideren

Alvorens te werk te gaan om OAuth op de AEM kant te vormen, zorg ervoor om zowel accessToken als refreshToken met de hieronder procedure te bevestigen:

1. Genereer accessToken door te gebruiken vernieuwtToken in de vorige procedure wordt geproduceerd die. U kunt dit bereiken door de volgende krulling te gebruiken, waarbij de waarden voor `<client_id>`,`<client_secret>` en `<refreshToken>` worden vervangen:

   `curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
--data-urlencode 'client_id=<client_id>' \
--data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
--data-urlencode 'redirect_uri=http://localhost' \
--data-urlencode 'grant_type=refresh_token' \
--data-urlencode 'client_secret=<client_secret>' \
--data-urlencode 'refresh_token=<refreshToken>'`

1. Verzend een post gebruikend accessToken, om te zien of werkt behoorlijk.

>[!NOTE]
>
> U kunt de Postman API-verzameling ophalen van [deze locatie](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow).

### Integratie met AEM als Cloud Service {#integration-with-aem-as-a-cloud-service}

1. Maak een OSGI-eigenschappenbestand met de naam `com.day.cq.mailer.oauth.impl.OAuthConfigurationProviderImpl.cfg.json` onder `/apps/<my-project>/osgiconfig/config` met de volgende syntaxis:

   ```
   {
       authUrl: "<Authorization Url>",
       tokenUrl: "<Token Url>",
       clientId: "<clientID>",
       clientSecret: "$[secret:SECRET_SMTP_OAUTH_CLIENT_SECRET]",
       scopes: [
          "scope1",
          "scope2"
       ],
       refreshUrl: "<Refresh token Url>",
       refreshToken: "$[secret:SECRET_SMTP_OAUTH_REFRESH_TOKEN]"
   }
   ```

1. Vul `authUrl`, `tokenUrl` en `refreshURL` door hen te construeren zoals die in de vorige sectie worden beschreven.
1. Voeg de volgende Scopes aan de configuratie toe:
   * `openid`
   * `offline_access`
   * `https://outlook.office365.com/Mail.Send`
   * `https://outlook.office365.com/Mail.Read`
   * `https://outlook.office365.com/SMTP.Send`
1. Een OSGI-eigenschappenbestand maken `called com.day.cq.mailer.impl.DefaultMailService.cfg.json`
krachtens 
`/apps/<my-project>/osgiconfig/config`  met de volgende syntaxis:

   ```
   {
    "smtp.host": "<smtp hostname>"
    "smtp.user": "<user account that logged into get the oauth tokens>",
    "smtp.password": "value not used",
    "smtp.port": 587,
    "from.address": "<from address used for sending>"
    "smtp.ssl": false,
    "smtp.starttls": true,
    "smtp.requiretls": true,
    "debug.email": false,
    "oauth.flow": true
   }
   ```

1. Voor vooruitzichten is de `smtp.host` configuratiewaarde `smtp.office365.com`
1. Geef tijdens runtime de `refreshToken values`- en `clientSecret`-geheimen door met de API voor variabelen van Cloud Manager, zoals [hier](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api) wordt beschreven. De waarden voor de variabelen `SECRET_SMTP_OAUTH_REFRESH_TOKEN` en `SECRET_SMTP_OAUTH_CLIENT_SECRET` moeten worden gedefinieerd.

### Problemen oplossen {#troubleshooting}

Als de mailservice niet goed werkt, moet u in de meeste gevallen `refreshToken` opnieuw genereren zoals hierboven is beschreven en de nieuwe waarde doorgeven via de API van Cloud Manager. Het duurt een paar minuten voordat de nieuwe waarde wordt geïmplementeerd.
