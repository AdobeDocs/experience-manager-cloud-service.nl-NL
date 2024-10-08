---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Integreer de selecteur van Activa met diverse Adobe, niet-Adobe, en derdetoepassingen.
role: Admin, User
exl-id: 55848de0-aff2-42a0-b959-c771235d9425
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# Integratie met een toepassing zonder Adobe {#integrate-asset-selector-non-adobe-app}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Met Asset Selector kunt u toepassingen van andere leveranciers of leveranciers integreren, zodat deze naadloos kunnen samenwerken.

## Vereisten {#prereqs-non-adobe-app}

Gebruik de volgende voorwaarden als u Asset Selector integreert met een toepassing zonder Adobe:

* [Communicatiemethoden](/help/assets/overview-asset-selector.md#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Asset Selector ondersteunt verificatie naar de [!DNL Experience Manager Assets] repository met behulp van Identity Management System (IMS)-eigenschappen zoals `imsScope` of `imsClientID` wanneer u deze integreert met een niet-Adobe toepassing.

## Asset Selector configureren voor een toepassing zonder Adobe {#configure-non-adobe-app}

Om de Selecteur van Activa voor een niet-Adobe toepassing te vormen, moet u eerst een steunkaartje voor levering registreren die door de integratiestappen wordt gevolgd.

### Een ondersteuningsticket registreren {#log-a-support-ticket}

Stappen om een steunkaartje via de Admin Console te registreren:

1. Voeg **de Selecteur van Activa met AEM Assets** in de titel van het kaartje toe.

1. Geef in de beschrijving de volgende gegevens op:

   * [!DNL Experience Manager Assets] als een [!DNL Cloud Service] URL (programma-id en milieu-id).
   * Domeinnamen waarbij de niet-Adobe webtoepassing wordt gehost.

## Integratiestappen {#non-adobe-app-integration-steps}

Gebruik dit voorbeeldbestand `index.html` voor verificatie terwijl Asset Selector wordt geïntegreerd met een toepassing zonder Adobe.

Heb toegang tot het pakket van de Selecteur van Activa gebruikend de `Script` Markering, zoals aangetoond in *lijn 9* aan *lijn 11* van het voorbeeld `index.html` dossier.

*Lijn 14* aan *lijn 38* van het voorbeeld beschrijft de IMS stroomeigenschappen, zoals `imsClientId`, `imsScope`, en `redirectURL`. De functie vereist dat u ten minste een van de eigenschappen `imsClientId` en `imsScope` definieert. Als u geen waarde definieert voor `redirectURL` , wordt de geregistreerde omleidings-URL voor de client-id gebruikt.

Aangezien u geen `imsToken` hebt geproduceerd, gebruik de `registerAssetsSelectorsAuthService` en `renderAssetSelectorWithAuthFlow` functies, zoals aangetoond in lijn 40 tot lijn 50 van het voorbeeld `index.html` dossier. Gebruik de functie `registerAssetsSelectorsAuthService` voor `renderAssetSelectorWithAuthFlow` om de `imsToken` bij de functie Asset Selector te registreren. [!DNL Adobe] raadt aan `registerAssetsSelectorsAuthService` aan te roepen wanneer u de component instantieert.

Bepaal de authentificatie en andere as a Cloud Service toegang-verwante eigenschappen van Assets in de `const props` sectie, zoals aangetoond in *lijn 54* aan *lijn 60* van het voorbeeld `index.html` dossier.

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
>* [ integreer de Selector van Activa met diverse toepassingen ](/help/assets/integrate-asset-selector.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ integreer de Selector van Activa met Dynamic Media met mogelijkheden OpenAPI ](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
>* [ de aanpassingen van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
