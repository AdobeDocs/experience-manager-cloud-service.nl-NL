---
title: Inhoudsfragmentkiezer integreren met een Adobe-toepassing
description: Integreer de kiezer voor inhoudsfragmenten met verschillende Adobe-toepassingen.
role: Admin, User, Developer
source-git-commit: a16d9e9fa6483a89283c595372abcc437d1d962e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Inhoudsfragmentkiezer integreren met Adobe-toepassing {#integrate-content-fragment-selector-with-adobe-application}

Met de Content Fragment Selector kunt u verschillende Adobe-toepassingen integreren, zodat deze naadloos kunnen samenwerken.

## Vereisten {#prerequisites}

Gebruik de volgende voorwaarden als u de Content Fragment Selector integreert met een Adobe-toepassing:

* [Vereisten](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsOrg
* imsToken
* apikey

## Inhoudsfragmentkiezer integreren met een Adobe-toepassing {#integrate-content-fragment-selector-with-an-adobe-application}

In het volgende voorbeeld wordt het gebruik van de Content Fragment Selector getoond wanneer u een Adobe-toepassing onder Unified Shell uitvoert of wanneer u al een `imsToken` voor verificatie hebt gegenereerd.

Neem het pakket Content Fragment Selector in uw code op met de tag `script` , zoals in het onderstaande voorbeeld wordt getoond.

* Wanneer het script is geladen, is de algemene variabele `PureJSContentFragmentSelectors` beschikbaar voor gebruik.
* Bepaal de Eigenschappen van de Selecteur van het Fragment van de Inhoud [ ](/help/headless/content-fragment-selector/properties.md):

   * de eigenschappen `imsOrg` en `imsToken` zijn beide vereist voor verificatie in een Adobe-toepassing
   * de eigenschap `handleSelection` wordt gebruikt om de geselecteerde fragmenten af te handelen.

* Roep de functie `renderFragmentSelector` aan om de Content Fragment Selector te renderen.
* De Content Fragment Selector wordt weergegeven in het `<div>` containerelement.

Als u dergelijke stappen uitvoert, kunt u de Content Fragment Selector gebruiken met uw Adobe-toepassing.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Fragment Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-fragmentss-selectors/static-fragments/resources/fragments-selectors.js"></script>
    <script>
        // get the container element in which we want to render the FragmentSelector component
        const container = document.getElementById('fragment-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
        const fragmentSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (fragmentss: SelectedFragmentType[]) => {},
        };
        // Call the `renderFragmentSelector` available in PureJSContentFragmentSelectors globals to render FragmenttSelector
        PureJSContentFragmentSelectors.renderFragmentSelector(container, fragmentSelectorProps);
    </script>
</head>

<body>
    <div id="fragment-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

### ImsAuthProps {#imsauthprops}

Met de eigenschappen `ImsAuthProps` worden de verificatiegegevens en de stroom gedefinieerd die de kiezer voor het inhoudsfragment gebruikt om een `imsToken` -element te verkrijgen. Door deze eigenschappen te plaatsen, kunt u controleren hoe de authentificatiestroom zich gedraagt en luisteraars voor diverse authentificatiegebeurtenissen registreert.

Voor bezitsdetails zie [ Eigenschappen ImsAuthProps ](/help/headless/content-fragment-selector/properties.md#imsauthprops-properties)

### ImsAuthService {#imsauthservice}

`ImsAuthService` -klasse handelt de verificatiestroom voor de fragmentkiezer af. Het is verantwoordelijk voor het verkrijgen van een `imsToken` van de Adobe IMS-verificatieservice. `imsToken` wordt gebruikt om de gebruiker te verifiëren en toegang tot de AEM as a Cloud Service-opslagplaats te verlenen. `ImsAuthService` gebruikt de `ImsAuthProps` -eigenschappen om de verificatiestroom te beheren en listeners voor verschillende verificatiegebeurtenissen te registreren. U kunt de functie `registerFragmentsSelectorsAuthService` gebruiken om de instantie `ImsAuthService` te registreren bij de fragmentkiezer. De volgende functies zijn beschikbaar voor de `ImsAuthService` -klasse. Als u echter de functie `registerFragmentsSelectorsAuthService` gebruikt, hoeft u deze functies niet rechtstreeks aan te roepen.

Voor bezitsdetails zie [ Eigenschappen ImsAuthService ](/help/headless/content-fragment-selector/properties.md#imsauthservice-properties)

### Validatie met opgegeven IMS-token {#validation-with-provided-ims-token}

```javascript
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected fragment: ", selection);
    };
    function renderFragmentSelectorInline() {
    console.log("initializing Fragment Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('fragment-selector-container');
    PureJSContentFragmentSelectors.renderFragmentSelector(container, props);
    }
    $(document).ready(function() {
    renderFragmentSelectorInline();
    });
</script>
```

### Callbacks van de dienst van IMS registreren {#register-callbacks-to-ims-service}

```java
// object `imsProps` to be defined as below 
let imsProps = {
    imsClientId: <IMS Client Id>,
        imsScope: "openid",
        redirectUrl: window.location.href,
        modalMode: true,
        adobeImsOptions: {
            modalSettings: {
            allowOrigin: window.location.origin,
},
        useLocalStorage: true,
},
onImsServiceInitialized: (service) => {
            console.log("onImsServiceInitialized", service);
},
onAccessTokenReceived: (token) => {
            console.log("onAccessTokenReceived", token);
},
onAccessTokenExpired: () => {
            console.log("onAccessTokenError");
// re-trigger sign-in flow
},
onErrorReceived: (type, msg) => {
            console.log("onErrorReceived", type, msg);
},
}
```
