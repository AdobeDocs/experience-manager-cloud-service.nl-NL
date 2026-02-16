---
title: Associate UI voor interactieve communicatie bij uitvoering integreren
description: Leer hoe te om AEM Forms te integreren associate UI met uw toepassing om klant-onder ogen ziet beroeps toe te laten om gepersonaliseerde Interactieve Mededelingen in real time op Publish instanties te produceren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
exl-id: f946ccea-86d0-4086-8208-9583b8206244
source-git-commit: 749ad181c7e9e59a0601e0eddd85b0bd0e761f08
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Associatieve UI integreren in uw toepassing

<span> De interactieve communicatiemogelijkheid is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.</span>

Dit artikel verklaart hoe te om Associate UI met uw toepassing te integreren, toelatend klant-onder ogen ziet beroeps zoals gebiedsassociaties en de dienstagenten om gepersonaliseerde Interactieve Mededelingen in real time op te produceren publiceert instanties.

## Vereisten

Voordat u de gekoppelde interface integreert met uw toepassing, moet u controleren of:

- Interactieve communicatie gemaakt en gepubliceerd
- Browser met popup-ondersteuning ingeschakeld
- De geassocieerde [&#x200B; gebruikers moeten deel van de vorm-geassocieerde groep &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups) uitmaken
- De authentificatie vormde gebruikend om het even welk [&#x200B; authentificatiemechanisme dat door AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/authentication) wordt gesteund (bijvoorbeeld, SAML 2.0, OAuth, of de managers van de douaneauthentificatie)

>[!NOTE]
>
>- Dit artikel toont authentificatieconfiguratie gebruikend SAML 2.0 met [&#x200B; Microsoft Entra identiteitskaart (Azure AD) als Identiteitskaart &#x200B;](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings) aan.
>- Voor Geassocieerde UI, worden de extra configuraties van SAML vereist voorbij de standaardopstelling die in [&#x200B; wordt verklaard SAML 2.0 authentificatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) artikel. Zie de [&#x200B; Extra configuraties van SAML voor Associate UI &#x200B;](#additional-saml-configurations-for-associate-ui) sectie voor details.

### Aanvullende SAML-configuraties voor Associatieve UI

Wanneer het vormen van SAML 2.0 authentificatie voor Associate UI, moet u de volgende specifieke montages in uw OSGi configuratiedossiers toepassen.

#### SAML-verificatiehandler

De manager van de Authentificatie van SAML is een OSGi fabrieksconfiguratie die veelvoudige configuraties SAML voor verschillende middelbomen toestaat. Dit maakt de implementatie van AEM op meerdere locaties mogelijk en stelt u in staat gekoppelde UI-bronnen toe te voegen aan uw bestaande SAML-installatie.

Maak het bestand `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login"
    "idpUrl": "https://login.microsoftonline.com/{azure-tenant-id}/saml2",
    "idpCertAlias": "{your-certificate-alias}",
    "idpIdentifier": "https://sts.windows.net/{azure-tenant-id}/",
    "userIDAttribute": "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name",
    "createUser": true,
    "userIntermediatePath": "saml",
    "synchronizeAttributes": [
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname=profile/givenName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname=profile/familyName",
      "http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress=profile/email"
      ],
      "addGroupMemberships": true,
      "defaultGroups": ["forms-associates"],
      "defaultRedirectUrl": "/libs/fd/associate/ui.html",
      "idpHttpRedirect": false,
      "service.ranking": 5002
  }
```

| Eigenschap | Beschrijving |
|----------|-------------|
| `path` | Moet worden ingesteld op `/libs/fd/associate` voor gekoppelde UI |
| `defaultGroups` | Instellen op `forms-associates` om gebruikers automatisch toe te wijzen aan de vereiste groep |
| `defaultRedirectUrl` | Verstuurt geverifieerde gebruikers om naar de gekoppelde gebruikersinterface |
| `idpHttpRedirect` | Moet `false` zijn voor SP-gestarte flow |
| `idpCertAlias` | Moet overeenkomen met de alias van het certificaat in Trust Store (hoofdlettergevoelig) |

#### Sling Authenticator

De Sling Authenticator dwingt authentificatie voor de toegang tot van de Medewerkende middelen UI op Publish af.

Werk het bestand `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` bij in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Dispatcher-filter

Voeg de volgende regels toe om ervoor te zorgen dat Interactieve Mededelingen APIs en Associate UI correct op de Publish instantie functioneren.

Voeg de volgende regels toe aan uw `dispatcher/src/conf.dispatcher.d/filters/filters.any` -bestand als dit nog niet het geval is:

```json
  # Allow Interactive Communications APIs and Associate UI
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/adobe/communications" }
  /XXXX { /type "allow" /method '(GET|POST|OPTIONS)' /url "/adobe/communications/*" }
  /XXXX { /type "allow" /method "GET" /url "/content/dam/fd:fonts/*" }
  /XXXX { /type "allow" /method '(GET|OPTIONS)' /url "/libs/fd/associate/*" }
```

>[!NOTE]
>
> Vervang `XXXX` door de juiste numerieke volgorde die in het bestaande `filters.any` -bestand wordt gebruikt.

## Associate UI aanroepen bij publicatie-instantie

Deze sectie begeleidt u door het lanceren van Associate UI van uw eigen toepassing. Voer de volgende stappen uit om snel aan de slag te gaan—te beginnen met een gebruiksklare HTML-voorbeeldpagina en deze vervolgens voor uw omgeving te configureren.

### Stap 1: Beginnen met de HTML-voorbeeldpagina

Gebruik de volgende voorbeeldpagina van HTML om snel te testen en te begrijpen hoe de integratie met de Associate UI werkt. Kopieer deze code naar een HTML-bestand en open deze in uw browser.

>[!NOTE]
>
> Voor dit voorbeeld HTML zijn een IC-id en een vooraf ingevulde service vereist. U kunt het testen gebruikend uw identiteitskaart van IC en de steekproef Prefill dienst &quot;FdmTestData&quot;.&quot;

Het HTML-voorbeeld biedt een eenvoudige formulierinterface waarin u uw interactieve communicatiedetails kunt invoeren en de gebruikersinterface voor koppelen met één klik kunt starten.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Associate UI Integration</title>
  <style>
    body {
      font-family: sans-serif;
      max-width: 600px;
      margin: 50px auto;
      padding: 20px;
    }
    .form-group {
      margin: 20px 0;
    }
    label {
      display: block;
      margin-bottom: 5px;
      font-weight: bold;
    }
    input, textarea {
      width: 100%;
      padding: 8px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
    }
    textarea {
      height: 80px;
      font-family: monospace;
    }
    button {
      padding: 10px 20px;
      margin: 5px;
      cursor: pointer;
      border-radius: 4px;
    }
    .btn-primary {
      background: #007bff;
      color: white;
      border: none;
    }
    .btn-primary:hover {
      background: #0056b3;
    }
    .error {
      color: red;
      font-size: 12px;
      display: none;
    }
  </style>
</head>
<body>
  <h1>Launch Associate UI</h1>

  <form id="form">
    <div class="form-group">
      <label>IC ID *</label>
      <input type="text" id="icId" placeholder="Enter Interactive Communication ID" required>
    </div>

    <div class="form-group">
      <label>Prefill Service</label>
      <input type="text" id="serviceName" placeholder="e.g., CustomerDataService">
    </div>

    <div class="form-group">
      <label>Service Parameters (JSON)</label>
      <textarea id="serviceParams" placeholder='{"customerId": "12345"}'>{}</textarea>
      <span id="paramsError" class="error">Invalid JSON format</span>
    </div>

    <div class="form-group">
      <label>Options (JSON)</label>
      <textarea id="options" placeholder='{"mode": "edit", "locale": "en_US"}'>{}</textarea>
      <span id="optionsError" class="error">Invalid JSON format</span>
    </div>

    <button type="button" onclick="reset()">Reset</button>
    <button type="button" class="btn-primary" onclick="launch()">Launch Associate UI</button>
  </form>

  <script>
    // Replace with your AEM Publish instance URL
    const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';

    function validateJSON(str, errorId) {
      const err = document.getElementById(errorId);
      try {
        const obj = JSON.parse(str || '{}');
        err.style.display = 'none';
        return obj;
      } catch (e) {
        err.style.display = 'block';
        return null;
      }
    }

    function launch() {
      const icId = document.getElementById('icId').value.trim();
      if (!icId) {
        alert('IC ID is required');
        return;
      }

      const params = validateJSON(document.getElementById('serviceParams').value, 'paramsError');
      const opts = validateJSON(document.getElementById('options').value, 'optionsError');

      if (!params || !opts) {
        alert('Please fix JSON errors before launching');
        return;
      }

      const data = {
        id: icId,
        prefill: {
          serviceName: document.getElementById('serviceName').value.trim(),
          serviceParams: params
        },
        options: opts
      };

      const win = window.open(AEM_URL, '_blank');
      if (!win) {
        alert('Pop-up blocked. Please enable pop-ups for this site.');
        return;
      }

      const handler = (e) => {
        if (e.data && e.data.type === 'READY' && e.data.source === 'APP') {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      };

      window.addEventListener('message', handler);

      // Fallback timeout in case READY message is missed
      setTimeout(() => {
        if (win && !win.closed) {
          win.postMessage({ type: 'INIT', source: 'PORTAL', data }, '*');
          window.removeEventListener('message', handler);
        }
      }, 1000);
    }

    function reset() {
      document.getElementById('form').reset();
      document.getElementById('serviceParams').value = '{}';
      document.getElementById('options').value = '{}';
      document.getElementById('paramsError').style.display = 'none';
      document.getElementById('optionsError').style.display = 'none';
    }
  </script>
</body>
</html>
```

### Stap 2: Vorm Uw Publish Instantie URL

Voordat u de gebruikersinterface voor koppelen kunt starten, moet u het voorbeeld naar de publicatie-instantie van AEM Forms Cloud Service sturen.

Zoek in het bovenstaande HTML-voorbeeld de volgende regel in de sectie `<script>` :

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Vervang de plaatsaanduidingswaarden door de werkelijke omgevingsdetails:
- `{program-id}`: uw programma-id voor AEM Cloud-service
- `{env-id}`: uw milieu-id

Als uw programma-id bijvoorbeeld `12345` is en de omgeving-id `67890` , wordt de URL:

```javascript
const AEM_URL = 'https://publish-p12345`-e67890.adobeaemcloud.com/libs/fd/associate/ui.html';
```

>[!NOTE]
>
> Om veiligheidsredenen, worden de parameters zoals Interactieve Communicatie identiteitskaart, de prefill dienst, en de dienstparameters niet overgegaan door URL. In plaats daarvan worden deze parameters veilig doorgegeven met de JavaScript `postMessage` -API.

### Stap 3: Inzicht in de JavaScript-integratiefunctie

Het voorbeeld HTML gebruikt de volgende JavaScript-functie om de Associate UI te starten. Deze functie valideert de IC-id, construeert de gegevenslading, opent de Associate UI in een nieuw browservenster en verzendt de gegevens met behulp van de `postMessage` -API van de browser.

```javascript
function launchAssociateUI(icId, prefillService, prefillParams, options) {
  if (!icId) {
    console.error('IC ID required');
    return;
  }

  const data = {
    id: icId,
    prefill: {
      serviceName: prefillService || '',
      serviceParams: prefillParams || {}
    },
    options: options || {}
  };

  const AEM_URL = 'https://your-aem.adobeaemcloud.com/libs/fd/associate/ui.html';
  const win = window.open(AEM_URL, '_blank');

  if (!win) {
    alert('Please enable pop-ups for this site');
    return;
  }

  const readyHandler = (event) => {
    if (event.data && event.data.type === 'READY' && event.data.source === 'APP') {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  };

  window.addEventListener('message', readyHandler);

  // Fallback timeout in case READY message is missed
  setTimeout(() => {
    if (win && !win.closed) {
      win.postMessage({ type: 'INIT', source: 'PORTAL', data: data }, '*');
      window.removeEventListener('message', readyHandler);
    }
  }, 1000);
}
```

De functie accepteert vier parameters: de (vereiste) IC-id, de Prefill-servicenaam, Prefill-serviceparameters en aanvullende opties. Deze parameters zijn gestructureerd in de gegevenslading zoals hieronder beschreven.

### Stap 4: Begrijp de gegevensladingsstructuur

**formaat van de Payload:**

```javascript
const data = {
  id: "your-ic-id",              // Required: Interactive Communication ID
  prefill: {                      // Optional: Data to prefill the IC
    serviceName: "YourService",
    serviceParams: { key: "value" }
  },
  options: {}                     // Optional: Additional configuration options
};
```

**Componenten van de Payload:**

| Component | Vereist | Beschrijving |
|-----------|----------|-------------|
| `id` | Ja | De id van de te laden interactieve communicatie (IC) |
| `prefill` | Optioneel | Bevat de dienstconfiguratie voor gegevens prefilling |
| `prefill.serviceName` | Optioneel | Naam van de service Formuliergegevensmodel die moet worden aangeroepen voor het vooraf invullen van gegevens |
| `prefill.serviceParams` | Optioneel | Sleutelwaardeparen die tot de vooraf ingevulde dienst worden overgegaan |
| `options` | Optioneel | Extra eigenschappen die worden ondersteund voor PDF-rendering: locale, includeAttachments, embedFonts, makeAccessible |

#### Voorbeelden van gegevensdoorvoer

**Minimale Payload (identiteitskaart van IC slechts)**

Gebruik deze optie wanneer geen vooraf ingevulde gegevens vereist zijn:

```json
{
  "id": "12345",
  "prefill": { 
    "serviceName": "", 
    "serviceParams": {} 
  },
  "options": {}
}
```

**met vooraf ingevulde Gegevens**

Gebruik dit om IC met klantengegevens dynamisch te bevolken:

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": {}
}
```

**met PDF die Opties teruggeven**

Gebruik deze optie om extra renderopties op te geven:

```json
{
  "id": "12345",
  "prefill": {
    "serviceName": "IC_FDM",
    "serviceParams": {
      "customerId": "101",
      "accountNumber": "ACC-98765"
    }
  },
  "options": { 
      "locale": "en_US",
      "includeAttachments": "true",
      "webOptimized": "false",
      "embedFonts": "false",
      "makeAccessible": "false"
  }
}
```

### Stap 5: Ga identiteitskaart van IC in en lanceer Associate UI

Nu kunt u de gebruikersinterface voor koppelen starten met de voorbeeldpagina van HTML:

1. **ga identiteitskaart van IC** in: Op het **identiteitskaart van IC** gebied, ga het herkenningsteken van uw gepubliceerde Interactieve Mededeling in. Dit is het enige vereiste veld.

1. **vormt de Vooraf ingevulde Dienst**: Als u IC met dynamische gegevens wilt vooraf invullen, ga de modeldienstnaam van de Gegevens van de Vorm in de **Prefill 3&rbrace; gebied van de Dienst &lbrace;in.** Gebruik bijvoorbeeld `FdmTestData` voor voorbeeldgegevens.

   ![&#x200B; Steekproef HTML UI &#x200B;](/help/forms/assets/samplehtmlui.png)

1. **klik Lanceer Geassocieerde UI**: Klik de **Lanceer Associate knoop UI**. Er wordt een nieuw browservenster geopend met de Associate UI, die vooraf is geladen met uw interactieve communicatie.

Voer de gegevens in en de bijbehorende interface wordt weergegeven zoals hieronder wordt getoond:

![&#x200B; Associate UI &#x200B;](/help/forms/assets/associateui.png)

>[!NOTE]
>
> Als het venster niet wordt geopend, controleert u of uw browser pop-ups voor deze site toestaat.


<!--**Add Service Parameters**: In the **Service Parameters (JSON)** field, enter a JSON object with the parameters your prefill service requires. For example:

   ```json
   {"customerId": "101", "accountNumber": "ACC-98765"}
   ```

  **Set PDF Options** (optional): In the **Options (JSON)** field, configure rendering options such as locale, attachments, or accessibility settings.-->

## Problemen oplossen

### Pop-up geblokkeerd

**Probleem**: Het Associate venster UI opent niet.

**Oplossing**:
- Pop-ups voor uw domein inschakelen in browserinstellingen
- Zorg ervoor dat `window.open()` wordt aangeroepen door een gebruikersactie (bijv. klikken op een knop)
- Testen met verschillende browsers om blokkeringsgedrag te identificeren

### Gegevens niet geladen

**Probleem**: De Interactieve Mededeling opent maar de gegevens bevolken niet.

**Oplossing**:
- Controleren of de IC-id correct is en of de IC is gepubliceerd
- Browserconsole voor JavaScript-fouten controleren
- Zorg ervoor dat de `postMessage` -structuur exact overeenkomt met de specificatie
- Controleren of de service Formuliergegevensmodel correct is geconfigureerd

### Verificatiefout

**Probleem**: De gebruiker ontvangt een authentificatiefout wanneer Associate UI opent.

**Oplossing**:
- SAML 2.0-verificatie configureren op de instantie Publiceren
- Verifieer de gebruiker deel van de **vorm-geassocieerde** groep uitmaakt
- Instellingen voor sessietime-out controleren

### CORS-fouten

**Probleem**: Het Middel van de dwars-Oorsprong die fouten in console delen.

**Oplossing**:
- Voor ontwikkeling: gebruik `'*'` als oorsprong van doel in `postMessage`
- Voor productie: geef de exacte oorspronkelijke URL van uw toepassing op
- Zorg ervoor dat de CORS-instellingen voor de publicatie-instantie uw toepassingsdomein toestaan

<!--## Best Practices

When implementing the Associate UI integration, follow these best practices:

1. **Validation**: Always validate the IC ID and JSON payload before sending
2. **Error Handling**: Implement proper error handling for `window.open()` failures
3. **User Experience**: Display a loading indicator while the Associate UI initializes
4. **Memory Management**: Remove event listeners after initialization to prevent memory leaks
5. **Testing**: Test the integration with popup blockers enabled to ensure graceful handling
6. **User Permissions**: Verify users have appropriate access to the forms-associates group-->

## Zie ook

- [UI koppelen in de Interactive Communication Editor](/help/forms/interactive-communication/associate-ui-in-interactive-communication-editor.md)
- [Interactieve communicatie over de cloud](/help/forms/early-access-ea-features.md#interactive-communications-on-cloud)
- [Functies voor vroege toegang](/help/forms/early-access-ea-features.md)
