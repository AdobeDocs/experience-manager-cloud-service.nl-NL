---
title: ID Connect-ondersteuning voor AEM as a Cloud Service openen op publicatieniveau
description: Meer informatie over het instellen van Open ID Connect (OIDC) voor AEM as a Cloud Service op publicatieniveau
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: 75c2dbc4f1d77de48764e5548637f95bee9264dd
workflow-type: tm+mt
source-wordcount: '1986'
ht-degree: 0%

---

# ID Connect-ondersteuning voor AEM as a Cloud Service openen op publicatieniveau {#open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier}

## Inleiding {#introduction}

Naarmate organisaties hun digitale ervaringen moderniseren, wordt een veilig en schaalbaar identiteitsbeheer een fundamentele vereiste. Adobe Experience Manager (AEM) Cloud Service biedt nu ondersteuning voor OpenID Connect (OIDC) op de publicatielaag, zodat naadloze en op standaarden gebaseerde integratie met toonaangevende identiteitsproviders (IdPs) mogelijk is, zoals Enterprise ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock en OIDC ondersteunde IDP&#39;s.

OIDC is een identiteitslaag bovenop het protocol OAuth 2.0 dat robuuste gebruikersauthentificatie terwijl het handhaven van eenvoud voor ontwikkelaars toelaat. Het wordt wijd goedgekeurd voor zaken-aan-consument (B2C), Intranet, en partnerportalscenario&#39;s, waar veilige gebruikerslogin en identiteitsfederaties worden vereist.

Tot nu toe waren AEM-klanten verantwoordelijk voor het implementeren van hun eigen aangepaste aanmeldingslogica op de publicatielaag, die de ontwikkelingstijd verlengde en langdurige onderhouds- en beveiligingsproblemen introduceerde. Met native ondersteuning voor OIDC verwijdert AEM Cloud Service deze last door een veilig, uitbreidbaar en door Adobe ondersteund verificatiemechanisme te bieden voor eindgebruikers die toegang willen tot publicatieomgevingen.

Of u nu een gepersonaliseerde consumentenwebsite of een geverifieerd intern portaal levert, OIDC on Publish vereenvoudigt identiteitsfederatie en vermindert risico door gecentraliseerd identiteitsbeheer. Het helpt organisaties ook om aan moderne naleving en veiligheidsnormen te voldoen zonder behendigheid te offeren.

## AEM voor OIDC-verificatie configureren {#configure-aem-oidc-authentication}

### Vereisten {#prerequisits}

We gaan ervan uit dat de volgende informatie beschikbaar of gedefinieerd is:

1. De paden van de inhoud die in de AEM-opslagplaats moet worden beveiligd
1. Een herkenningsteken voor IdP dat moet worden gevormd. Dit kan elke tekenreeks zijn

Informatie van de Configuratie IdP:

1. Clientid die in IdP wordt gevormd
1. Het geheim van de Cliënt dat in Idp wordt gevormd. Als PKCE op Idp werd gevormd, is het Geheim van de Cliënt niet beschikbaar. Sla de waarde voor onbewerkte tekst niet op in het configuratiebestand. Een CM-geheim gebruiken en ernaar verwijzen
1. Het werkingsgebied dat op Idp wordt gevormd. Minstens het bereik `openid` moet worden opgegeven
1. Of PKCE op IdP wordt toegelaten
1. `callbackUrl` wordt gedefinieerd met behulp van een van de geconfigureerde paden die zijn gedefinieerd in punt 1 en waarbij het achtervoegsel wordt toegevoegd: `/j_security_check`
1. De `baseUrl` voor toegang tot het standaard `.well-known` -bestand. Als de bekende URL bijvoorbeeld: `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration` de `baseUrl` is: `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`

### Overzicht van de configuratiebestanden {#overview-of-the-configuration-files}

Zoek onder een lijst met bestanden die moeten worden geconfigureerd:

1. **OIDC Verbinding**: dit zal door `OidcAuthenticationHandler` worden gebruikt om de gebruikers voor authentiek te verklaren, of door andere componenten om [&#x200B; toegang tot middelen toe te staan die door IdP worden beschermd gebruikend OAuth &#x200B;](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)
1. **OIDC de Handler van de Authentificatie**: Dit is de authentificatiemanager wordt gebruikt om gebruikers voor authentiek te verklaren die toegang tot de gevormde wegen
1. **UserInfoProcessor**: Deze component verwerkt de informatie die door IdP wordt ontvangen. Het kan door klanten worden uitgebreid om douanelogica uit te voeren
1. [**StandaardHandler van de Synchronisatie** &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html): Deze component leidt tot de gebruiker in de bewaarplaats
1. [**ExternalLoginModule** &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html): Deze component verklaart de gebruiker in de lokale eik bewaarplaats voor authentiek.

Het volgende diagram toont hoe de vermelde configuratieelementen verbonden zijn. Aangezien dit `ServiceFactory` -componenten zijn, kan `~uniqueid` elke willekeurige unieke tekenreeks zijn:

![&#x200B; OIDC configuratiediagram &#x200B;](/help/security/assets/oidc-diagram.png)

### De OIDC-verbinding configureren {#configure-the-oidc-connection}

Eerst, moeten wij de verbinding vormen OIDC. De veelvoudige verbindingen OIDC kunnen worden gevormd, en elk moet een verschillende naam hebben.

1. Maak een nieuw `.cfg.json` -bestand waarin de configuratie wordt opgeslagen. Bijvoorbeeld, kunt u gebruiken `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json` - het **azure** achtervoegsel moet een uniek herkenningsteken voor de verbinding zijn
1. Volg de configuratie-indeling in het onderstaande voorbeeld:

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/tenant-id/v2.0>",
    "clientId":"client-id-from-idp",
    "clientSecret":"xxxxxx"
   }
   ```

In sommige omgevingen is het mogelijk dat de identiteitsprovider (IdP) geen geldig `.well-known` eindpunt weergeeft.
Wanneer dit voorkomt, kunnen de vereiste eindpunten manueel worden bepaald door de volgende eigenschappen in het configuratiedossier te specificeren.
In deze configuratiemodus mag de eigenschap `baseUrl` niet worden ingesteld.

```
"authorizationEndpoint": "https://idp-url/oauth2/v1/authorize",
"tokenEndpoint": "https://idp-url/oauth2/v1/token",
"jwkSetURL":"https://idp-url/oauth2/v1/keys",
"issuer": "https://idp-url"
```

1. Configureer de eigenschappen als volgt:
   * **&quot;naam&quot;** kan door de gebruiker worden bepaald
   * `baseUrl` , `clientid` en `clientSecret` zijn configuratiewaarden die afkomstig zijn van de IdP.
   * Het bereik moet ten minste de waarde `openid` bevatten.

### OIDC-verificatiehandler configureren {#configure-oidc-authentication-handler}

Nu, vorm de OIDC authentificatiemanager. Er kunnen meerdere OIDC-verbindingen worden geconfigureerd. Elke naam moet een andere naam hebben. Als zij de zelfde [&#x200B; Externe Leverancier van de Identiteit van OAK &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html) delen, kunnen zij gebruikers delen.

1. Maak het configuratiebestand. Voor dit voorbeeld gebruiken we `org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json` . Het achtervoegsel `azure` moet een unieke id zijn. Zie een voorbeeld van het configuratiedossier hieronder:

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. Configureer vervolgens de eigenschappen als volgt:
   * `path`: het pad dat moet worden beveiligd
   * `callbackUri` : het pad dat moet worden beveiligd, waarbij het achtervoegsel `/j_security_check` wordt toegevoegd. Dat zelfde callbackUri ook in verre IdP als redirect url moet worden gevormd.
   * `defaultConnectionName`: configureren met dezelfde naam die is gedefinieerd voor de OIDC-verbinding in de vorige stap+
   * `pkceEnabled`: `true` Proefsleutel voor Codeuitwisseling (PKCE) op de stroom van de machtigingscode
   * `idp`: de naam van de [&#x200B; Externe Leverancier van de Identiteit van OAK &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html). Houd er rekening mee dat verschillende OAK IDP geen gebruikers of groepen kan delen

### SlingUserInfoProcessor configureren {#configure-slinguserinfoprocessor}

1. Maak het configuratiebestand. Voor dit voorbeeld gebruiken we `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessor~azure.cfg.json` . Het achtervoegsel `azure` moet een unieke id zijn. Zie een voorbeeld van het configuratiedossier hieronder:

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false,
      "idpNameInPrincipals": true
   }
   ```

1. Configureer vervolgens de eigenschappen als volgt:
   * `groupsInIdToken`: wordt ingesteld op true als de groepen worden verzonden in een ID-token. Als de waarde vals is, of niet gespecificeerd, worden de groepen gelezen van eindpunt UserInfo.
   * `groupsClaimName`: De naam van de claim bevat de groepen die in AEM moeten worden gesynchroniseerd.
   * `connection`: configureren met dezelfde naam die is gedefinieerd voor de OIDC-verbinding in de vorige stap
   * `storeAccessToken`: true als het toegangstoken moet worden opgeslagen in de repostory. Standaard is dit onwaar. Plaats het aan waar slechts als AEM tot middelen in naam van de gebruiker moet toegang hebben die in externe servers wordt opgeslagen die door zelfde IdP worden beschermd.
   * `storeRefreshToken`: true als het token Vernieuwen moet worden opgeslagen in de repostory. Standaard is dit onwaar. Plaats het aan waar slechts als AEM tot middelen in naam van de gebruiker moet toegang hebben die in externe servers wordt opgeslagen die door zelfde IdP worden beschermd en het teken van IdP moet verfrissen.
   * `idpNameInPrincipals`: wanneer ingesteld op true, wordt de naam van de IdP als achtervoegsel toegevoegd aan de principaal van de gebruiker en groep, gescheiden door een &#39;;&#39;. Als de IDP-naam bijvoorbeeld `azure-idp` is en de gebruikersnaam `john.doe` is, is de principal die in eiken is opgeslagen, `john.doe;azure-idp` . Dit is nuttig wanneer veelvoudige IdPs in eiken wordt gevormd om conflicten tussen gebruikers of groepen met de zelfde naam te vermijden die uit verschillende IdPs komen. Dit kan ook worden geplaatst om conflicten met gebruikers of groepen te vermijden die door andere authentificatiemanagers zoals Saml worden gecreeerd.
Merk op dat de Token van de Toegang en van het Vernieuwen worden opgeslagen gecodeerd met de hoofdsleutel van AEM.


### Synchronisatiehandler configureren {#configure-the-synchronization-handler}

Minstens één manager van de Synchronisatie moet me gevormd om de gebruikers te synchroniseren die in eikel voor authentiek worden verklaard. Voor meer details, zie [&#x200B; deze &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) pagina.

Maak een bestand met de naam `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json` . Het **azure** achtervoegsel moet een uniek herkenningsteken zijn. Voor meer informatie over hoe te om zijn eigenschappen te vormen, raadpleeg de [&#x200B; documentatie van de Synchronisatie van de Gebruiker van Oak en van de Groep &#x200B;](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html). Hieronder vindt u een voorbeeldconfiguratie:

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Tijdens de ontwikkeling, kunnen de vervaltijden tot een lagere waarde (bijvoorbeeld worden verminderd: 1s) om het testen van gebruiker en groepssynchronisatie in eiken te versnellen.
Onder enkele van de meest relevante kenmerken die in DefaultSyncHandler moeten worden geconfigureerd. Merk op dat het Dynamische Lidmaatschap van de Groep altijd in de Diensten van de Wolk zou moeten worden toegelaten.

| Eigenschapnaam | Notities | Voorgestelde waarde |
|---|---|---|
| `user.expirationTime` | Duur totdat een gesynchroniseerde gebruiker is verlopen. De gebruikers worden gesynchroniseerd slechts na de vervaltijd. | 1h |
| `user.membershipExpTime` | Duur totdat een gesynchroniseerd gebruikerslidmaatschap is verlopen. Gebruikerslidmaatschappen worden alleen gesynchroniseerd na de vervaltijd. | 1h |
| `user.dynamicMembership` | We raden u aan dynamisch groepslidmaatschap in te schakelen | true |
| `user.enforceDynamicMembership` | Wij adviseren het toelaten van de handhaving van dynamisch groepslidmaatschap | true |
| `group.dynamicGroups` | We raden aan dynamische groepen in te schakelen | true |
| user.propertyMapping | Bij de opgegeven implementatie van `UserInfoProcessor` worden slechts enkele eigenschappen gesynchroniseerd. Deze kan worden gewijzigd en aangepast. | <code>&quot;profile/givenName=profile/given_name&quot;,</code><br><code>&quot;profile/familyName=profile/family_name&quot;,</code><br><code> &quot;rep :fullname=profile/name&quot;,</code><br><code>&quot;profile/email=profile/email&quot;,</code><br><code>&quot;access_token=access_token&quot;,</code><br><code>&quot;refresh_token=refresh_token&quot;</code> |
| `user.membershipNestingDepth` | Retourneert de maximale diepte van het nesten van groepen wanneer lidmaatschapsrelaties worden gesynchroniseerd. Met de waarde 0 wordt het opzoeken van het groepslidmaatschap effectief uitgeschakeld. Met de waarde 1 voegt u alleen de directe groepen van een gebruiker toe. Deze waarde heeft geen effect wanneer u afzonderlijke groepen alleen synchroniseert wanneer u een abonnement voor een gebruikerslidmaatschap synchroniseert. | 1 |

### De externe aanmeldingsmodule configureren {#configure-the-external-login-module}

Tot slot moet u de Externe Module van de Aanmelding vormen.

1. Maak een bestand met de naam `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json` . Zie hieronder een voorbeeldconfiguratie:

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. Configureer de eigenschappen als volgt:

   * `sync.handlerName`: naam van de eerder gedefinieerde synchronisatiehandler
   * `idp.name`: OAK Identity Provider gedefinieerd in OIDC Authentication Handler

### Optioneel: een aangepaste UserInfoProcessor implementeren {#implement-a-custom-userinfoprocessor}

De gebruiker wordt voor authentiek verklaard door een Symbolisch van identiteitskaart, en de extra attributen worden gehaald in het `userInfo` eindpunt dat voor IdP wordt bepaald. Als de extra niet-standaardverrichtingen moeten worden uitgevoerd, is een douaneimplementatie van [&#x200B; UserInfoProcessor &#x200B;](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) de standaardimplementatie van het Verdelen.

### ACL voor externe groepen configureren {#configure-acl-for-external-groups}

Wanneer de gebruikers door OIDC voor authentiek worden verklaard, worden hun groepslidmaatschappen typisch gesynchroniseerd van de externe identiteitsleverancier.
Deze externe groepen worden dynamisch gemaakt in de AEM-opslagplaats, maar worden niet automatisch gekoppeld aan toegangsbeheeritems.
Om ervoor te zorgen dat de gebruikers de aangewezen toestemmingen hebben, moeten de toegangsbeheerlijsten (ACLs) uitdrukkelijk voor deze groepen worden bepaald.

Er zijn twee primaire benaderingen beschikbaar.

### Optie 1 — Lokale groepen

De externe groep kan als lid van een lokale groep worden toegevoegd die reeds vereiste ACLs heeft.
* De externe groep moet bestaan in de opslagplaats, die automatisch plaatsvindt wanneer een gebruiker die tot die groep behoort zich voor het eerst aanmeldt.
* Deze optie heeft over het algemeen de voorkeur wanneer Gesloten Gebruikersgroepen (CUGs) in gebruik zijn, aangezien de lokale groep op zowel auteur als publicatiemilieu&#39;s bestaat.

### Optie 2 — Directe ACLs op Externe Groepen via RepoInit

ACLs kan rechtstreeks op externe groepen worden toegepast gebruikend manuscripten RepoInit.
* Deze aanpak is efficiënter en heeft de voorkeur wanneer CUG&#39;s niet worden gebruikt.
* In het volgende voorbeeld ziet u een RepoInit-configuratie die leesmachtigingen toewijst aan een externe groep. Met de optie `ignoreMissingPrincipal` kunt u ACL maken, zelfs als de groep nog niet bestaat in de gegevensopslagruimte:

  ```
  {
    "scripts":[
      "set ACL for \"my-group;my-idp\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/magazine\r\nend"
    ]
  }    
  ```

>[!NOTE]
>De toestemmingen UI van AEM kan worden gebruikt om ACLs te inspecteren die aan groepshoofden wordt toegewezen

## Voorbeeld: OIDC-verificatie configureren met Azure Active Directory

### Vorm een nieuwe Toepassing in Azure Actieve Folder {#configure-a-new-application-in-azure-ad}

1. Creeer een nieuwe toepassing in Azure Actieve Folder door de [&#x200B; Azure Actieve documentatie van de Folder &#x200B;](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure) te volgen.  Hieronder ziet u hoe het scherm met het toepassingsoverzicht eruit moet zien:

   ![&#x200B; Overzicht van de Toepassing &#x200B;](/help/security/assets/odic-application-overview.png)

1. Als de Groepen of de toepassingsrollen worden vereist, volg de [&#x200B; documentatie &#x200B;](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers) om hen voor de toepassing toe te laten en hen in het Symbolische van identiteitskaart te verzenden. Onder een voorbeeld van gevormde groepen:

![&#x200B; OIDC de Symbolische identiteitskaart van de Claim &#x200B;](/help/security/assets/oidc-claim-id-token.png)

1. Volg de eerder gedocumenteerde stappen om de vereiste configuratiedossiers tot stand te brengen. Onder een voorbeeld specifiek voor Azure AD waarin:
   * De namen Verbinding, Verificatiehandler en DefaultSyncHandler worden gedefinieerd als: `azure`
   * De website-URL is: `www.mywebsite.com`
   * Het pad `/content/wknd/us/en/adventures` dat alleen toegankelijk is voor geverifieerde gebruikers in de groep, wordt beveiligd `adventures`
   * Tennant is: `tennat-id`,
   * Client id is: `client-id`
   * Geheim is: `secret`,
   * De groepen worden in het token Id verzonden in een claim die wordt aangeroepen: `groups`

### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email"
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

```
{
  "callbackUri":"https://www.mywebsite.com/content/wknd/us/en/adventures/j_security_check",
  "path":[
    "/content/wknd/us/en/adventures"
  ],
  "idp":"azure",
  "defaultConnectionName":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "group.pathPrefix": "oidc",
  "user.membershipNestingDepth": "1",
  "handler.name":"azure"
}
```

### org.apache.sling.jcr.repoinit.RepositoryInitializer~azure.cfg.json

```
{
  "scripts":[
    "set ACL for \"adventures;azure\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/adventures\r\nend"
  ]
}
```

### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

```
{
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false",
  "connection": "azure",
  "groupsClaimName": "groups"
}
```

### Aanvullende informatie over Azure AD groups {#additional-information-about-azure-ad-groups}

Om een groep aan voor de ondernemingstoepassing in Microsoft Azure Portal te vormen, moet u de toepassing zoeken: **Toepassingen van de Onderneming** en de groepen toevoegen: <!-- Alexandru: this bit cound be clearer-->

![&#x200B; OIDC Groep voegt toe &#x200B;](/help/security/assets/oidc-ad-additional-info.png)

Om de groepseis in het Token van identiteitskaart toe te laten, voeg de eis in de **Symbolische sectie van de Configuratie** van Microsoft Azure Portal toe: <!-- Alexandru: this bit cound be clearer as well-->

![&#x200B; OIDC de Symbolische identiteitskaart van de Claim &#x200B;](/help/security/assets/oidc-claim-id-token.png)

De configuratie van `SlingUserInfoProcessor` moet worden gewijzigd zoals in het onderstaande voorbeeld.

De bestandsnaam die moet worden gewijzigd, is `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json` . De inhoud moet als volgt worden geconfigureerd:

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```

## Hoe te van de Handler van de Authentificatie van Saml aan de Handler van de Authentificatie Oidc migreren

Wanneer AEM reeds met een Handler van de Authentificatie van SAML wordt gevormd, en de gebruikers in de bewaarplaats met [&#x200B; toegelaten gegevenssynchronisatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) aanwezig zijn, kunnen de conflicten tussen de originele gebruikers van SAML en de nieuwe gebruikers OIDC voorkomen.

1. Vorm [&#x200B; OidcAuthenticationHandler &#x200B;](#configure-oidc-authentication-handler) en laat `idpNameInPrincipals` in [&#x200B; SlingUserInfoProcessor &#x200B;](#configure-slinguserinfoprocessor) configuratie toe
1. Opstelling [&#x200B; ACL voor externe groepen &#x200B;](#configure-acl-for-external-groups).
1. Na login van gebruikers, kunnen de oude gebruikers die door de steekproef authentificatiemanager worden gecreeerd worden geschrapt.

>[!NOTE]
>Zodra de manager van de Authentificatie SAML wordt onbruikbaar gemaakt en de handler OIDC van de Authentificatie wordt toegelaten, als [&#x200B; gegevenssynchronisatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) niet wordt toegelaten, worden de bestaande zittingen ongeldig. Gebruikers moeten opnieuw verifiëren, wat resulteert in het maken van nieuwe OIDC-gebruikersknooppunten in de opslagplaats.

