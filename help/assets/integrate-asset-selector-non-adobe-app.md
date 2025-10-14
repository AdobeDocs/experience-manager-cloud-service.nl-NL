---
title: Asset Selector integreren met toepassing van andere leveranciers dan Adobe
description: Integreer de kiezer voor middelen met verschillende Adobe-, niet-Adobe- en externe toepassingen.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: 39b6bbc10507f0391583d9cdc054a1611b64326a
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# Integratie met een niet-Adobe-toepassing {#integrate-asset-selector-non-adobe-app}

Met Asset Selector kunt u toepassingen van andere leveranciers dan Adobe of derden integreren, zodat deze naadloos kunnen samenwerken.

## Vereisten {#prereqs-non-adobe-app}

Gebruik de volgende voorwaarden als u Asset Selector integreert met een niet-Adobe-toepassing:

* [Communicatiemethoden](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Asset Selector ondersteunt verificatie naar de [!DNL Experience Manager Assets] repository met behulp van Identity Management System (IMS)-eigenschappen zoals `imsScope` of `imsClientID` wanneer u deze integreert met een niet-Adobe-toepassing.

## Asset Selector configureren voor een niet-Adobe-toepassing {#configure-non-adobe-app}

Als u Asset Selector wilt configureren voor een niet-Adobe-toepassing, moet u eerst een ondersteuningsticket voor provisioning registreren, gevolgd door de integratiestappen.

### Een ondersteuningsticket registreren {#log-a-support-ticket}

Stappen om een steunkaartje via Admin Console te registreren:

1. Voeg **de Selecteur van Activa met AEM Assets** in de titel van het kaartje toe.

1. Geef in de beschrijving de volgende gegevens op:

   * [!DNL Experience Manager Assets] als een [!DNL Cloud Service] URL (programma-id en milieu-id).
   * Domeinnamen waarbij de niet-Adobe webtoepassing wordt gehost.

## Integratiestappen {#non-adobe-app-integration-steps}

Gebruik dit voorbeeldbestand `index.html` voor verificatie terwijl Asset Selector wordt geïntegreerd met een niet-Adobe-toepassing.

Heb toegang tot het pakket van de Selecteur van Activa gebruikend de `Script` Markering, zoals aangetoond in *lijn 9* aan *lijn 11* van het voorbeeld `index.html` dossier.

*Lijn 14* aan *lijn 38* van het voorbeeld beschrijft de IMS stroomeigenschappen, zoals `imsClientId`, `imsScope`, en `redirectURL`. De functie vereist dat u ten minste een van de eigenschappen `imsClientId` en `imsScope` definieert. Als u geen waarde definieert voor `redirectURL` , wordt de geregistreerde omleidings-URL voor de client-id gebruikt.

Aangezien u geen `imsToken` hebt geproduceerd, gebruik de `registerAssetsSelectorsAuthService` en `renderAssetSelectorWithAuthFlow` functies, zoals aangetoond in lijn 40 tot lijn 50 van het voorbeeld `index.html` dossier. Gebruik de functie `registerAssetsSelectorsAuthService` voor `renderAssetSelectorWithAuthFlow` om de `imsToken` bij de functie Asset Selector te registreren. [!DNL Adobe] raadt aan `registerAssetsSelectorsAuthService` aan te roepen wanneer u de component instantieert.

Bepaal de authentificatie en andere Assets as a Cloud Service op toegang betrekking hebbende eigenschappen in de `const props` sectie, zoals aangetoond in *lijn 54* aan *lijn 60* van het voorbeeld `index.html` dossier.

De `PureJSSelectors` globale variabele, die in *wordt vermeld lijn 65*, wordt gebruikt om de Selecteur van Activa in Webbrowser terug te geven.

De Selecteur van activa wordt teruggegeven op het `<div>` containerelement, zoals vermeld in *lijn 74* aan *lijn 81*. In het voorbeeld wordt een dialoogvenster gebruikt om de Asset Selector weer te geven.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta charset="utf-8">
    <title>Asset Selectors</title>
    <link rel="stylesheet" href="index.css">
    <script id="asset-selector"
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>
    <script>

        const imsProps = {
            imsClientId: "<obtained from IMS team>",
            imsScope: "openid, <other scopes>",
            redirectUrl: window.location.href,
            modalMode: true, // false to open in a full page reload flow
            onImsServiceInitialized: (service) => {
                // invoked when the ims service is initialized and is ready
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

        function load() {
            const registeredTokenService = PureJSSelectors.registerAssetsSelectorsAuthService(imsProps);
            imsInstance = registeredTokenService;
        };

        // initialize the IMS flow before attempting to render the asset selector
        load();
        

        //function that will render the asset selector
        function renderAssetSelectorWithAuthFlowFlow() {
            const otherProps = {
            // any other props supported by asset selector
            }
            const assetSelectorProps = {
                "imsOrg": "imsorg",
                ...otherProps
            }
             // container element on which you want to render the AssetSelector/DestinationSelector component
            const container = document.getElementById('asset-selector');

            /// Use the PureJSSelectors in globals to render the AssetSelector/DestinationSelector component
            PureJSSelectors.renderAssetSelectorWithAuthFlow(container, assetSelectorProps, () => {
                const assetSelectorDialog = document.getElementById('asset-selector-dialog');
                assetSelectorDialog.showModal();
            });
        }
    </script>

</head>
<body class="asset-selectors">
    <div>
        <button onclick="renderAssetSelectorWithAuthFlowFlow()">Asset Selector - Select Assets with Ims Flow</button>
    </div>
        <dialog id="asset-selector-dialog">
            <div id="asset-selector" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
            </div>
        </dialog>
    </div>
</body>

</html>
```

## Kan geen toegang krijgen tot gegevensopslagruimte {#unable-to-access-delivery-repository}

>[!TIP]
>
>Als u Asset Selector hebt geïntegreerd met de workflow Aanmelden maar nog steeds geen toegang hebt tot de gegevensopslagruimte, moet u ervoor zorgen dat browsercookies worden opgeschoond. Anders krijgt u de fout `invalid_credentials All session cookies are empty` in de console.

>[!MORELIKETHIS]
>
>* [&#x200B; integreer de Selector van Activa met diverse toepassingen &#x200B;](/help/assets/integrate-asset-selector.md)
>* [&#x200B; Eigenschappen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-properties.md)
>* [&#x200B; integreer de Selector van Activa met Dynamische Media met mogelijkheden OpenAPI &#x200B;](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [&#x200B; de aanpassingen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-customization.md)
