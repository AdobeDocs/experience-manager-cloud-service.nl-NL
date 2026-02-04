---
title: Een gekoppelde gebruikersinterface aanroepen bij instantie Publiceren
description: Leer hoe te om de Associate UI van AEM Forms op Publish instanties te integreren en aan te halen om klant-onder ogen ziet beroeps toe te laten om gepersonaliseerde Interactieve Mededelingen in real time te produceren.
products: SG_EXPERIENCEMANAGER/Cloud Service/FORMS
feature: Interactive Communication
role: User, Developer, Admin
hide: true
hidefromtoc: true
source-git-commit: 2f3badafddfdfe1dd21eb74be7189102aa0474bc
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---


# Genereer Persoonlijke Mededelingen met Associate UI

<span> De interactieve communicatiemogelijkheid is beschikbaar in het kader van het programma voor vroegtijdige adoptie. Verzend een e-mail van uw werkadres naar `aem-forms-ea@adobe.com` om toegang aan te vragen.</span>

Associate UI kan direct op Publish instanties worden aangehaald, toelatend klant-onder ogen ziet beroeps zoals gebiedvenates en de dienstagenten om gepersonaliseerde mededelingen in real time tijdens klanteninteractie te produceren.

De onderstaande lijst toont de diverse scenario&#39;s in real-world waar de Vennoot UI kan worden gebruikt om gepersonaliseerde berichten naar klanten te verzenden:

| Industrie | Hoofdletters gebruiken |
|----------|----------|
| **Financiële Diensten** | Redenen in real-time aanmaningen voor het bevestigen van leningen, accountinstructies en samenvattingen van risicoprofielen genereren tijdens vergaderingen van klanten |
| **Verzekering** | Onmiddellijk een bewijs van verzekering overleggen en een overzicht van de regeling van aanvragen bij de loketten van de dienst overleggen |
| **Gezondheidszorg** | Samenvattingen van patiëntenbehandelingsplannen maken met berekende afnamegrootten en -schema&#39;s |
| **Regering** | Verzamel controleverslagen van de politie, ontvangstbewijzen van de burgerdienst, en samenvattingen van de gevallenupdate ter plaatse |

## Vereisten

Voordat u de gekoppelde interface integreert met uw toepassing, moet u controleren of:

- Interactieve communicatie gemaakt en gepubliceerd
- Browser met popup-ondersteuning ingeschakeld
- De geassocieerde [&#x200B; gebruikers moeten deel van de vorm-geassocieerde groep &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/forms/administrator-help/setup-organize-users/creating-configuring-roles#assign-a-role-to-users-and-groups) uitmaken
- De authentificatie vormde - [&#x200B; SAML 2.0 &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/authentication/saml-2-0)

>[!NOTE]
>
> Voor Geassocieerde UI, worden de extra configuraties van SAML vereist voorbij de standaardopstelling die in [&#x200B; wordt verklaard SAML 2.0 authentificatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/authentication/saml-2-0) artikel. Zie de [&#x200B; Extra configuraties van SAML voor Associate UI &#x200B;](#additional-saml-configurations-for-associate-ui) sectie voor details.

### Aanvullende SAML-configuraties voor Associatieve UI

Wanneer het vormen van SAML 2.0 authentificatie voor Associate UI, moet u de volgende specifieke montages in uw OSGi configuratiedossiers toepassen.

#### SAML-verificatiehandler

Maak het bestand `com.adobe.granite.auth.saml.SamlAuthenticationHandler~saml.cfg.json` in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
  {
    "path": ["/libs/fd/associate"],
    "serviceProviderEntityId": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com",
    "assertionConsumerServiceURL": "https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/saml_login",
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

Werk het bestand `org.apache.sling.engine.impl.auth.SlingAuthenticator~saml.cfg.json` bij in `ui.config/src/main/content/jcr_root/apps/<project-name>/osgiconfig/config.publish` :

```json
{
  "sling.auth.requirements": ["+/libs/fd/associate/ui.html"],
  "sling.auth.anonymous": false
}
```

#### Dispatcher-filter

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

Om Associate UI van uw toepassing aan te halen, vorm de Publish instantie URL, bereidt de gegevenslading voor, en gebruik de integratiefunctie om Associate UI in een nieuw browser venster te lanceren.

### Stap 1: Vorm de Publish Instantie URL

De Associate UI wordt betreden via een specifiek eindpunt op uw de Publish instantie van AEM Forms Cloud Service:

```javascript
const AEM_URL = 'https://publish-p{program-id}-e{env-id}.adobeaemcloud.com/libs/fd/associate/ui.html';
```

Vervang `{program-id}` en `{env-id}` door de werkelijke omgevingswaarden.

### Stap 2: De gegevenslading voorbereiden

U kunt de gegevenslading structureren met de volgende indeling:

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
| `prefill` | Optioneel | Bevat de dienstconfiguratie voor gegevens prefilling. |
| `prefill.serviceName` | Optioneel | Naam van de service Formuliergegevensmodel die moet worden aangeroepen voor het vooraf invullen van gegevens |
| `prefill.serviceParams` | Optioneel | Sleutelwaardeparen die tot de vooraf ingevulde dienst worden overgegaan |
| `options` | Optioneel | Aanvullende eigenschappen die worden ondersteund voor PDF-rendering - locale, includeAttachments, embedFonts, makeAccessible |

### Stap 3: Implementeer de integratiefunctie

Maak een JavaScript-functie om de koppelingsinterface te starten en de berichtcommunicatie af te handelen:

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

### Stap 4: De functie aanroepen

Roep de functie aan met de juiste parameters:

```javascript
// Basic invocation with IC ID only
launchAssociateUI('12345', '', {}, {});

// With prefill service
launchAssociateUI('12345', 'FdmTestData', 
  { customerId: '101'}, {});

// With all parameters
launchAssociateUI('12345', 'FdmTestData', 
  { policyNumber: 'POL-123' }, 
  { locale: 'en', acrobatVersion: 'Acrobat_11' });
```

## Uw integratie testen met een voorbeeld-HTML-pagina

Hier volgt een eenvoudig HTML-voorbeeld om te zien hoe de Associate UI op de voorgrond wordt weergegeven en om uw integratie te testen. Op deze voorbeeldpagina kunt u de IC-id invoeren, vooraf ingevulde serviceparameters configureren, PDF-opties instellen en de interface voor koppelen op uw publicatie-instantie starten.

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

### Hoe het monster werkt

1. **identiteitskaart van IC Gebied**: Ga het Interactieve (vereiste) Communicatie herkenningsteken in
2. **vooraf ingevulde Dienst**: specificeer de de dienstnaam van het Model van Gegevens van de Vorm voor het vooraf invullen van gegevens
3. **Parameters van de Dienst**: Ga JSON voorwerp met parameters in om tot de prefill dienst over te gaan
4. **Opties**: Ga configuratieopties voor PDF, bijvoorbeeld, scène, includeAttachments, embedFonts, makeAccessible in
5. **Knoop van de Lancering**: Opent Associate UI in een nieuw venster en verzendt de initialisatiegegevens

## Voorbeelden van gegevensdoorvoer

### Minimale nuttige last (alleen IC)

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

### Met vooraf ingevulde gegevens

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

### Met optieconfiguratie

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
      locale: "en_US",
      includeAttachments: "true",
      webOptimized: "false",
      embedFonts: "false",
      makeAccessible: "false"
  }
}
```

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