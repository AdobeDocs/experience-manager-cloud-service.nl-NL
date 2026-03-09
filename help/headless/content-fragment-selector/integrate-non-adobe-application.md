---
title: Inhoudsfragmentkiezer integreren met niet-Adobe- of externe toepassing
description: Integreer de kiezer voor inhoudsfragmenten met verschillende Adobe-, niet-Adobe- en externe toepassingen.
role: Admin, User, Developer
source-git-commit: 3af1a89489af96bf9c9908aea7fb20883956517b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Integratie met een niet-Adobe-toepassing {#integration-with-non-adobe-application}

Met de Content Fragment Selector kunt u verschillende toepassingen van andere leveranciers dan Adobe of derden integreren, zodat deze naadloos kunnen samenwerken.

## Vereisten {#prerequisites}

Gebruik de volgende voorwaarden als u Content Fragment Selector integreert met een niet-Adobe-toepassing:

* [Vereisten](/help/headless/content-fragment-selector/overview.md#prerequisites)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Wanneer u de toepassing integreert met een niet-Adobe-toepassing, biedt de Content Fragment Selector ondersteuning voor verificatie naar de Adobe Experience Manager (AEM) as a Cloud Service-opslagplaats met gebruik van Identity Management System (IMS)-eigenschappen zoals `imsScope` of `imsClientID` .

## Inhoudsfragmentkiezer configureren voor een niet-Adobe-toepassing {#configure-content-fragment-selector-for-a-non-adobe-application}

Om de selecteur van het Fragment van de Inhoud voor een niet-Adobe toepassing te vormen, moet u eerst een steunkaartje voor levering registreren alvorens met de integratiestappen te werk te gaan.

### Een ondersteuningsticket registreren {#logging-a-support-ticket}

Stappen om een steunkaartje via Admin Console te registreren:

1. Voeg **de Selecteur van het Fragment van de Inhoud met de Fragmenten van AEM** in de titel van het kaartje toe.

1. Geef in de beschrijving de volgende gegevens op:

   * Experience Manager as a Cloud Service URL (programma-id en milieu-id).
   * Domeinnamen waarbij de niet-Adobe webtoepassing wordt gehost.

## Integratiestappen {#integration-steps}

Gebruik het volgende voorbeeldbestand `index.html` voor verificatie bij het integreren van de Content Fragment Selector met een niet-Adobe toepassing:

* Open het pakket Content Fragment Selector met de tag `Script` .

* Definieer de IMS-floweigenschappen, zoals `imsClientId` , `imsScope` en `redirectURL` .

   * De functie vereist dat u ten minste een van de eigenschappen `imsClientId` en `imsScope` definieert.
   * Als u geen waarde definieert voor `redirectURL` , wordt de geregistreerde omleidings-URL voor de client-id gebruikt.

* Aangezien in het voorbeeld geen `imsToken` is gegenereerd, gebruikt u de functies `registerFragmentsSelectorsAuthService` en `renderFragmentSelectorWithAuthFlow` .

   * Gebruik de functie `registerFragmentsSelectorsAuthService` voor `renderFragmentSelectorWithAuthFlow` om de `imsToken` te registreren bij de Content Fragment Selector.
   * Adobe raadt aan `registerFragmentsSelectorsAuthService` aan te roepen wanneer u de component instantieert.

* Bepaal de authentificatie en andere Fragments as a Cloud Service toegang-verwante eigenschappen in de `const props` sectie.
* De algemene variabele `PureJSContentFragmentSelectors` wordt gebruikt om de kiezer voor inhoudsfragmenten te renderen in de webbrowser.
* De Content Fragment Selector wordt gerenderd op het `<div>` containerelement. In het voorbeeld wordt een dialoogvenster gebruikt om de kiezer voor inhoudsfragmenten weer te geven.

**Voorbeeld`ìndex.html`**

```html {line-numbers="true"}
<!doctype html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <link rel="icon" type="image/svg+xml" href="/vite.svg" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>testing-cf-mfe-integration-with-3rd-party-app</title>
        <script
            id="content-fragments-selector"
            src="https://experience.adobe.com/solutions/CQ-sites-content-fragment-selector/static-assets/resources/content-fragment-selector.js"
        ></script>
        <script>
            const imsProps = {
                imsClientId: '<IMS_CLIENT_ID>',
                imsScope:
                    'additional_info.projectedProductContext, AdobeID, openid, read_organizations',
                redirectUrl: window.location.href,
                onImsServiceInitialized: (service) => {
                    // invoked when the ims service is initialized and is ready
                    console.log('onImsServiceInitialized', service);
                },
                onAccessTokenReceived: (token) => {
                    console.log('onAccessTokenReceived', token);
                },
                onAccessTokenExpired: () => {
                    console.log('onAccessTokenError');
                    // re-trigger sign-in flow
                },
                onErrorReceived: (type, msg) => {
                    console.log('onErrorReceived', type, msg);
                },
            };

            function load() {
                const registeredTokenService =
                    PureJSContentFragmentSelectors.registerContentFragmentSelectorAuthService(
                        imsProps
                    );
                imsInstance = registeredTokenService;
            }

            // initialize the IMS flow before attempting to render the content fragment selector
            load();

            // function that will render the content fragment selector
            function renderContentFragmentSelectorWithAuthFlow() {
                const contentFragmentSelectorDialog = document.getElementById(
                    'content-fragment-selector-dialog'
                );

                const contentFragmentSelectorProps = {
                    inventoryViewToggleEnabled: true,
                    isOpen: true,
                    noWrap: false,
                    orgId: 'YOUR_ORG_ID@AdobeOrg',
                    // repoId: "author-p12345-e67890.adobeaemcloud.com", // if wanted to restrict to a specific repo
                    runningInUnifiedShell: false,
                    onDismiss: () => contentFragmentSelectorDialog.close(),
                    onSubmit: ({ contentFragments }) => {
                        const selectedContentFragment = contentFragments[0];
                        alert(selectedContentFragment.path);
                    },
                };
                // container element on which you want to render the ContentFragmentSelector component
                const container = document.getElementById('content-fragment-selector');

                /// Use the PureJSContentFragmentSelectors in globals to render the ContentFragmentSelector component
                PureJSContentFragmentSelectors.renderContentFragmentSelectorWithAuthFlow(
                    container,
                    contentFragmentSelectorProps,
                    () => contentFragmentSelectorDialog.showModal()
                );
            }
        </script>
    </head>
    <body>
        <div>
            <button onclick="renderContentFragmentSelectorWithAuthFlow()">
                Content Fragment Selector - Select Content Fragments with Ims Flow
            </button>
        </div>
        <dialog id="content-fragment-selector-dialog">
            <div
                id="content-fragment-selector"
                style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px"
            ></div>
        </dialog>
    </body>
</html>
```

## Kan geen toegang krijgen tot gegevensopslagruimte {#unable-to-access-delivery-repository}

Als u Content Fragment Selector hebt geïntegreerd met de workflow Aanmelden maar nog steeds geen toegang hebt tot de gegevensopslagruimte, moet u ervoor zorgen dat browsercookies zijn schoongemaakt.

Anders ziet u mogelijk de `invalid_credentials All session cookies are empty` -fout in de console.
