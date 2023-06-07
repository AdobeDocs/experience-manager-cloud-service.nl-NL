---
title: OAuth2 Steun voor de Dienst van de Post
description: Oauth2-ondersteuning voor de Mail Service in Adobe Experience Manager as a Cloud Service
exl-id: 93e7db8b-a8bf-4cc7-b7f0-cda481916ae9
source-git-commit: 4997c506e1cd467255fe11cb596fb64d74a511af
workflow-type: tm+mt
source-wordcount: '691'
ht-degree: 0%

---

# OAuth2 Steun voor de Dienst van de Post {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service biedt OAuth2-ondersteuning voor zijn geïntegreerde e-mailservice, zodat organisaties zich aan de vereisten voor e-mail kunnen houden.

U kunt OAuth voor veelvoudige e-mailleveranciers vormen. Hieronder zijn geleidelijke instructies voor het vormen van de AEMDienst van de Post via OAuth2 met Microsoft Office 365 Vooruitzichten voor authentiek te verklaren. Andere verkopers kunnen op een gelijkaardige manier worden gevormd.

Voor meer informatie over de AEM as a Cloud Service Dienst van de Post, zie [E-mail verzenden](/help/implementing/developing/introduction/development-guidelines.md#sending-email).

## Microsoft Outlook {#microsoft-outlook}

1. Ga naar [https://portal.azure.com/](https://portal.azure.com/) en aanmelden.
1. Zoeken naar **Azure Active Directory** in de zoekbalk en klik op het resultaat. U kunt ook rechtstreeks bladeren naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Klikken op **Toepassingsregistratie** - **Nieuwe registratie**

   ![](assets/oauth-outlook1.png)

1. Vul de gegevens naar wens in en klik op **Registreren**
1. Ga naar de nieuwe app en selecteer **API-machtigingen**
1. Ga naar **Machtiging toevoegen** - **Grafiekmachtigingen** - **Gedelegeerde machtigingen**
1. Selecteer de onderstaande machtigingen voor uw app en klik op **Machtiging toevoegen**:
   * `https://graph.microsoft.com/SMTP.Send`
   * `https://graph.microsoft.com/Mail.Read`
   * `https://graph.microsoft.com/Mail.Send`
   * `https://graph.microsoft.com/User.Read`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Ga naar **Verificatie** - **Een platform toevoegen** - **Web** en in de **URL omleiden** de volgende URL&#39;s toevoegen: één met en één zonder een slash:
   * `http://localhost/`
   * `http://localhost`
1. Druk **Configureren** na het toevoegen van elke URL en het configureren van uw instellingen volgens uw vereisten
1. Ga vervolgens naar **Certificaten en geheimen**, klikt u op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let op dit geheim voor later gebruik
1. Druk **Overzicht** in het linkerdeelvenster en kopieer de waarden voor **Toepassings-id (client)** en **Directory (huurder)-id** voor later gebruik

Om opnieuw te verpakken, zult u aan de volgende informatie nodig hebben om OAuth2 voor de dienst van de Post op de AEM te vormen:

* Auth URL, die met huurderidentiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* De token-URL, die wordt samengesteld met de huurder-id. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Vernieuwen URL, die met huurder identiteitskaart zal worden geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Client-id
* Het clientgeheim

### Het genereren van het token Vernieuwen {#generating-the-refresh-token}

Daarna, moet u verfrissen teken produceren, dat een deel van de configuratie OSGi in een verdere stap zal zijn.

U kunt dit doen door deze stappen te volgen:

1. Open de volgende URL in de browser nadat u deze hebt vervangen `clientID` en `tenantID` met de specifieke waarden voor uw account: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?client_id=<clientId>&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access&state=12345`
1. Toestemming toestaan indien gevraagd
1. De URL wordt omgeleid naar een nieuwe locatie, in de volgende indeling: `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Kopieer de waarde van `<code>` in het bovenstaande voorbeeld
1. Gebruik het volgende cURL bevel om te krijgen refreshToken. U moet de huurderID, clientID en clientSecret vervangen door de waarden voor uw account en de waarde voor `<code>`:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
   --data-urlencode 'client_id=<clientID>' \
   --data-urlencode 'scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=authorization_code' \
   --data-urlencode 'client_secret=<clientSecret>' \
   --data-urlencode 'code=<code>'
   ```

1. Noteer refreshToken en accessToken.

### Tokens valideren {#validating-the-tokens}

Alvorens te werk te gaan om OAuth op de AEM kant te vormen, zorg ervoor om zowel accessToken als refreshToken met de hieronder procedure te bevestigen:

1. Genereer accessToken door te gebruiken vernieuwtToken in de vorige procedure wordt geproduceerd die. U kunt dit bereiken door de waarden voor `<client_id>`,`<client_secret>` en `<refreshToken>`:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
   --data-urlencode 'client_id=<client_id>' \
   --data-urlencode 'scope=https://graph.microsoft.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=refresh_token' \
   --data-urlencode 'client_secret=<client_secret>' \
   --data-urlencode 'refresh_token=<refreshToken>'
   ```

1. Verzend een post gebruikend accessToken, om te zien of werkt behoorlijk.

>[!NOTE]
>
> U kunt de Postman API-verzameling ophalen vanuit [deze locatie](https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow).
>
> Controleer de MSFT OAuth-documentatie [hier](https://learn.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth) voor meer informatie .

### Integratie met AEM as a Cloud Service {#integration-with-aem-as-a-cloud-service}

1. Een OSGI-eigenschappenbestand maken met de naam `com.day.cq.mailer.oauth.impl.OAuthConfigurationProviderImpl.cfg.json` krachtens `/apps/<my-project>/osgiconfig/config` met de volgende syntaxis:

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
       authCodeRedirectUrl: "http://localhost",
       refreshUrl: "<Refresh token Url>",
       refreshToken: "$[secret:SECRET_SMTP_OAUTH_REFRESH_TOKEN]"
   }
   ```

1. Vul de `authUrl`, `tokenUrl` en `refreshURL` door ze te construeren zoals beschreven in de vorige sectie.
1. Voeg de volgende Scopes aan de configuratie toe:
   * `https://graph.microsoft.com/SMTP.Send`
   * `https://graph.microsoft.com/Mail.Read`
   * `https://graph.microsoft.com/Mail.Send`
   * `https://graph.microsoft.com/User.Read`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Een OSGI-eigenschappenbestand maken `called com.day.cq.mailer.DefaultMailService.cfg.json`
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

1. Voor de vooruitzichten `smtp.host` configuratiewaarde is `smtp.office365.com`
1. Geef tijdens runtime de `refreshToken values` en `clientSecret` geheimen met de API voor variabelen van Cloud Manager zoals beschreven [hier](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api). De waarden voor de variabelen `SECRET_SMTP_OAUTH_REFRESH_TOKEN`  en `SECRET_SMTP_OAUTH_CLIENT_SECRET` moeten worden gedefinieerd.

### Problemen oplossen {#troubleshooting}

Als de mailservice niet goed werkt, moet u in de meeste gevallen de `refreshToken` zoals hierboven beschreven, de nieuwe waarde doorgeven via de Cloud Manager-API. Het duurt een paar minuten voordat de nieuwe waarde wordt geïmplementeerd.
