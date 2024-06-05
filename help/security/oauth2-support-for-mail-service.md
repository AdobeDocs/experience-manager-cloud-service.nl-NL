---
title: OAuth2 Steun voor de Dienst van de Post
description: OAuth2 Support for the Mail Service in Adobe Experience Manager as a Cloud.Service.
exl-id: 93e7db8b-a8bf-4cc7-b7f0-cda481916ae9
feature: Security
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---


# OAuth2 Steun voor de Dienst van de Post {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service biedt OAuth2-ondersteuning voor de geïntegreerde e-mailservice om organisaties in staat te stellen zich aan de vereisten voor e-mail te houden.

U kunt OAuth voor veelvoudige e-mailleveranciers vormen. Hieronder vindt u stapsgewijze instructies voor het configureren van de AEM Mail Service voor verificatie via OAuth2 met Microsoft® Office 365 Outlook. Andere verkopers kunnen op een gelijkaardige manier worden gevormd.

Voor meer informatie over de AEM as a Cloud Service Dienst van de Post, zie [E-mail verzenden](/help/implementing/developing/introduction/development-guidelines.md#sending-email).

## Microsoft® Outlook {#microsoft-outlook}

1. Ga naar [https://portal.azure.com/](https://portal.azure.com/) en aanmelden.
1. Zoeken naar **Azure Active Directory** in de zoekbalk en klik op het resultaat. U kunt ook rechtstreeks bladeren naar [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)
1. Klikken **Toepassingsregistratie** > **Nieuwe registratie**.

   ![Toepassingsregistratieproces starten](assets/oauth-outlook1.png)

1. Vul de gegevens naar wens in en klik op **Registreren**.
1. Ga naar de gemaakte app en selecteer **API-machtigingen**.
1. Klikken **Machtiging toevoegen** > **Grafiekmachtigingen** > **Gedelegeerde machtigingen**.
1. Selecteer de onderstaande machtigingen voor uw app en klik op **Machtiging toevoegen**:

   >[!NOTE]
   >
   >De configuratie van toestemmingen kan in tijd evolueren. Werken met Microsoft® als deze niet werken zoals u had verwacht.

   * `https://outlook.office.com/SMTP.Send`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Ga naar **Verificatie** > **Een platform toevoegen** > **Web** en in de **URL omleiden** de volgende URL&#39;s toevoegen: één met en één zonder een slash:
   * `http://localhost/`
   * `http://localhost`
1. Druk **Configureren** na het toevoegen van elke URL en het configureren van uw instellingen volgens uw vereisten.
1. Ga vervolgens naar **Certificaten en geheimen**, klikt u op **Nieuw clientgeheim** en volg de stappen op het scherm om een geheim te maken. Let erop dat u dit geheim opneemt voor later gebruik.
1. Druk **Overzicht** in het linkerdeelvenster en kopieer de waarden voor **Toepassings-id (client)** en **Directory (huurder)-id** voor later gebruik.

Om opnieuw te verpakken, gebruik volgende informatie om OAuth2 voor de dienst van de Post op de AEM kant te vormen:

* Auth URL, die met huurderidentiteitskaart wordt geconstrueerd. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* De token-URL, die wordt samengesteld met de huurder-id. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* De vernieuwings-URL, die wordt samengesteld met de huurder-id. Het heeft de volgende vorm: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Client-id
* Het clientgeheim

### Het genereren van het token Vernieuwen {#generating-the-refresh-token}

Daarna, vernieuw symbolisch, dat een deel van de configuratie OSGi in een verdere stap door het volgende te doen is:

1. Open de volgende URL in de browser nadat u deze hebt vervangen `clientID` en `tenantID` met de specifieke waarden voor uw account:

   ```
   https://login.microsoftonline.com/%3ctenantID%3e/oauth2/v2.0/authorize?client_id=%3cclientId%3e&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https://outlook.office.com/SMTP.Send%20email%20openid%20profile%20offline_access&state=12345`
   ```

1. Toestaan dat toestemming wordt gevraagd als u hierom wordt gevraagd.
1. De URL wordt omgeleid naar een nieuwe locatie, in de volgende indeling:

   ```
   http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
   ```

1. De waarde kopiëren van `<code>` in het bovenstaande voorbeeld.
1. Gebruik het volgende cURL bevel om te krijgen refreshToken. Vervang de huurderID, clientID, en clientSecret met de waarden voor uw rekening, en de waarde voor `<code>`:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
   --data-urlencode 'client_id=<clientID>' \
   --data-urlencode 'scope=https://outlook.office.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=authorization_code' \
   --data-urlencode 'client_secret=<clientSecret>' \
   --data-urlencode 'code=<code>'
   ```

1. Noteer refreshToken en accessToken.

### Tokens valideren {#validating-the-tokens}

Alvorens te werk te gaan om OAuth op de AEM kant te vormen, zorg ervoor om zowel accessToken als refreshToken met de hieronder procedure te bevestigen:

1. Genereer accessToken door refreshToken te gebruiken die in de vorige procedure wordt geproduceerd door de volgende krulling te gebruiken, die de waarden voor vervangt `<client_id>`,`<client_secret>`, en `<refreshToken>`:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
   --data-urlencode 'client_id=<client_id>' \
   --data-urlencode 'scope=https://outlook.office.com/SMTP.Send https://graph.microsoft.com/Mail.Read https://graph.microsoft.com/Mail.Send https://graph.microsoft.com/User.Read email openid profile offline_access' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=refresh_token' \
   --data-urlencode 'client_secret=<client_secret>' \
   --data-urlencode 'refresh_token=<refreshToken>'
   ```

1. Verzend een post gebruikend accessToken, zodat kunt u zien of werkt het behoorlijk.

>[!NOTE]
>
> U kunt de Postman API-verzameling ophalen vanuit [deze locatie](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-auth-code-flow).
>
> Zie de MSFT OAuth-documentatie [hier](https://learn.microsoft.com/en-us/exchange/client-developer/legacy-protocols/how-to-authenticate-an-imap-pop-smtp-application-by-using-oauth) voor meer informatie .

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

1. Vul de `authUrl`, `tokenUrl`, en `refreshURL` door ze te construeren zoals beschreven in de vorige sectie.
1. Voeg de volgende Scopes aan de configuratie toe:

   >[!NOTE]
   >
   >Scopes kunnen zich in de loop der tijd ontwikkelen. Werken met Microsoft® als deze niet werken zoals u had verwacht.

   * `https://outlook.office.com/SMTP.Send`
   * `openid`
   * `offline_access`
   * `email`
   * `profile`
1. Een OSGI-eigenschappenbestand maken `called com.day.cq.mailer.DefaultMailService.cfg.json`
krachtens `/apps/<my-project>/osgiconfig/config` met de onderstaande syntaxis. De `smtp.host` en `smtp.port` de waarden wijzen op geavanceerde voorzien van een netwerkconfiguratie, zoals die in [Zelfstudie over e-mailservice](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/networking/examples/email-service).

   ```
   {
    "smtp.host": "$[env:AEM_PROXY_HOST;default=proxy.tunnel]",
    "smtp.user": "<user account that logged into get the oauth tokens>",
    "smtp.password": "value not used",
    "smtp.port": 30465,
    "from.address": "<from address used for sending>",
    "smtp.ssl": false,
    "smtp.starttls": true,
    "smtp.requiretls": true,
    "debug.email": false,
    "oauth.flow": true
   }
   ```

1. Voor de vooruitzichten `smtp.host` configuratiewaarde is `smtp.office365.com`
1. Geef tijdens runtime de `refreshToken values` en `clientSecret` geheimen met de API voor variabelen van Cloud Manager zoals beschreven [hier](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api) of door [Cloud Manager om variabelen toe te voegen.](/help/implementing/cloud-manager/environment-variables.md) De waarden voor de variabelen `SECRET_SMTP_OAUTH_REFRESH_TOKEN`  en `SECRET_SMTP_OAUTH_CLIENT_SECRET` moeten worden gedefinieerd.

### Problemen oplossen {#troubleshooting}

Als de mailservice niet correct werkt, moet u de `refreshToken` zoals hierboven beschreven, de nieuwe waarde doorgeven via de Cloud Manager-API. Het duurt een paar minuten voordat de nieuwe waarde is geïmplementeerd.
