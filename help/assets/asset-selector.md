---
title: Asset Selector voor [!DNL Adobe Experience Manager] als [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
contentOwner: Adobe
role: Admin,User
source-git-commit: 22d2a2235c8696fce76369d3ffe369bcbaa3f6f2
workflow-type: tm+mt
source-wordcount: '2343'
ht-degree: 0%

---


# Micro-Frontend element selecteren {#Overview}

Micro-Frontend Asset Selector biedt een gebruikersinterface die eenvoudig kan worden geïntegreerd met de [!DNL Experience Manager Assets as a Cloud Service] zodat u door de in de opslagplaats beschikbare digitale middelen kunt bladeren of deze kunt zoeken en kunt gebruiken in de ontwerpervaring van uw toepassing.

De gebruikersinterface van Micro-Frontend wordt beschikbaar gesteld in uw toepassingservaring gebruikend het pakket van de Selecteur van Activa. Alle updates van het pakket worden automatisch geïmporteerd en de nieuwste versie van Asset Selector wordt automatisch in de toepassing geladen.

![Overzicht](assets/overview.png)

De Kiezer van activa verstrekt vele voordelen, zoals:

* Eenvoudige integratie met alle Adobe- of niet-Adobe-toepassingen met Vanilla JavaScript-bibliotheek.
* Eenvoudig te onderhouden als updates van het middelenkiezerpakket worden automatisch geïmplementeerd op de Asset Selector die beschikbaar is voor uw toepassing. Uw toepassing hoeft geen updates uit te voeren om de laatste wijzigingen te laden.
* Gemakkelijk aanpassen aangezien er eigenschappen beschikbaar zijn die de vertoning van de Selecteur van Activa binnen uw toepassing controleren.

* In de volledige tekst doorzoeken, uit-van-de-doos, en aangepaste filters om snel aan activa voor gebruik binnen de auteurservaring te navigeren.

* Mogelijkheid om opslagruimten binnen een IMS-organisatie te verplaatsen voor het selecteren van bedrijfsmiddelen.

* De mogelijkheid om elementen te sorteren op naam, afmetingen en grootte en ze weer te geven in de weergave Lijst, Raster, Galerie of Waterval.

Voer de volgende taken uit om Asset Selector te integreren en te gebruiken in uw [!DNL Experience Manager Assets as a Cloud Service] opslagplaats:

* [Asset Selector integreren met Vanilla JS](#integration-with-vanilla-js)
* [Eigenschappen voor weergave van middelenkiezer definiëren](#asset-selector-properties)
* [Asset Selector gebruiken](#using-asset-selector)

## Asset Selector integreren met Vanilla JS {#integration-with-vanilla-js}

U kunt alle [!DNL Adobe] of niet-Adobe-toepassing met [!DNL Experience Manager Assets] als [!DNL Cloud Service] opslagplaats en selecteer elementen vanuit de toepassing.

De integratie gebeurt door het pakket Asset Selector te importeren en verbinding te maken met de middelen die zijn as a Cloud Service met de Vanilla JavaScript-bibliotheek. U moet een `index.html` of een geschikt bestand in uw toepassing naar -
* De verificatiedetails definiëren
* Toegang krijgen tot de as a Cloud Service gegevensopslagruimte
* De weergave-eigenschappen voor de middelenkiezer configureren

<!--
Asset Selector supports authentication to the [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository using Identity Management System (IMS) properties such as `imsScope` or `imsClientID`. Authentication using these IMS properties is referred to as SUSI (Sign Up Sign In) flow in this article.

You can perform authentication without defining some of the IMS properties, such as `imsScope` or `imsClientID`, if:

*   You are integrating an [!DNL Adobe] application on [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
*   You already have an IMS token generated for authentication.

Accessing [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository without defining `imsScope` or `imsClientID` IMS properties is referred to as a non-SUSI flow in this article.
-->

U kunt verificatie uitvoeren zonder enkele IMS-eigenschappen te definiëren, als:

* U integreert een [!DNL Adobe] toepassing op [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
* Er is al een IMS-token gegenereerd voor verificatie.

## Vereisten {#prerequisites}

<!--
If your application requires user based authentication, out-of-the-box Asset Selector also supports a flow for authentication to the [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository using Identity Management System (IMS.)

You can use properties such as `imsScope` or `imsClientID` to retrieve `imsToken` automatically. You can use SUSI (Sign Up Sign In) flow and IMS properties. Also, you can obtain your own imsToken and pass it to Asset Selector by integrating within [!DNL Adobe] application on Unified Shell or if you already have an imsToken obtained via other methods (for example, using technical account). Accessing [!DNL Experience Manager Assets] as a [!DNL Cloud Service] repository without defining IMS properties (For example, `imsScope` and `imsClientID`) is referred to as a non-SUSI flow.
-->

Definieer de vereisten in het dialoogvenster `index.html` bestand of een vergelijkbaar bestand in de implementatie van de toepassing om de verificatiegegevens te definiëren voor toegang tot het [!DNL Experience Manager Assets] als [!DNL Cloud Service] opslagplaats. Voorwaarden zijn:
* imsOrg
* imsToken
* apikey

<!--
The prerequisites vary if you are authenticating using a SUSI flow or a non-SUSI flow.

**Non-SUSI flow**

*   imsOrg
*   imsToken
*   apikey

For more information on these properties, refer to [Asset Selector Properties](#asset-selector-properties).

**SUSI flow**

*   imsClientId
*   imsScope
*   redirectUrl
*   imsOrg
*   apikey

For more information on these properties, refer to [Example for the SUSI flow](#susi-vanilla) and [Asset Selector Properties](#asset-selector-properties).
-->

## Installatie {#installation}

Middelen Kiezers zijn beschikbaar via beide ESM CDN (bijvoorbeeld [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) en [UMD](https://github.com/umdjs/umd) versie.

In browsers die **UMD-versie** (aanbevolen):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

In browsers met `import maps` ondersteuning gebruiken **ESM CDN-versie**:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
</script>
```

In Deno/Webpack Module Federation met **ESM CDN-versie**:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/@assets/selectors/index.js'
```

### Geselecteerd elementtype {#selected-asset-type}

Het geselecteerde elementtype is een array met objecten die de elementgegevens bevatten wanneer u de `handleSelection`, `handleAssetSelection`, en `onDrop` functies.

**Schema Syntax**

```
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'http://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
```

In de volgende tabel worden enkele belangrijke eigenschappen van het object Selected Asset beschreven.

| Eigenschap | Type | Toelichting |
|---|---|---|
| *repo:repositoryId* | string | Unieke id voor de gegevensopslagruimte waar het middel is opgeslagen. |
| *repo:id* | string | Unieke id voor het element. |
| *repo:assetClass* | string | De classificatie van het element (bijvoorbeeld afbeelding, video, document). |
| *repo:naam* | string | De naam van het element, inclusief de bestandsextensie. |
| *repo:grootte* | getal | De grootte van het element in bytes. |
| *repo:pad* | string | De locatie van het middel in de opslagplaats. |
| *repo:voorouders* | `Array<string>` | Een array van bovenliggende items voor het middel in de repository. |
| *repo:status* | string | Huidige status van het middel in de opslagplaats (bijvoorbeeld actief, verwijderd, enz.). |
| *repo:createdBy* | string | De gebruiker of het systeem dat het element heeft gemaakt. |
| *repo:createDate* | string | De datum en tijd waarop het element is gemaakt. |
| *repo:modifiedBy* | string | De gebruiker of het systeem dat het element als laatste heeft gewijzigd. |
| *repo:modifyDate* | string | De datum en het tijdstip waarop het element voor het laatst is gewijzigd. |
| *dc:indeling* | string | De indeling van het element, zoals het bestandstype (bijvoorbeeld JPEG, PNG, enz.). |
| *tiff:imageWidth* | getal | De breedte van een element. |
| *tiff:imageLength* | getal | De hoogte van een element. |
| *computedMetadata* | `Record<string, any>` | Een object dat een emmertje vertegenwoordigt voor alle soorten metagegevens van het element (gegevensopslagruimte, toepassing of ingesloten metagegevens). |
| *_links* | `Record<string, any>` | Hypermediakoppelingen voor het bijbehorende element. Bevat koppelingen voor bronnen zoals metagegevens en uitvoeringen. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition* | `Array<Object>` | Array met objecten die informatie bevatten over uitvoeringen van het element. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].href* | string | De URI naar de vertoning. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].type* | string | Het MIME-type van de vertoning. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].&quot;repo:size* | getal | De grootte van de vertoning in bytes. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].width* | getal | De breedte van de vertoning. |
| *_links.http://ns.adobe.com/adobecloud/rel/rendition[].height* | getal | De hoogte van de vertoning. |

Voor een volledige lijst met eigenschappen en een gedetailleerd voorbeeld gaat u naar [Voorbeeld van code voor middelenkiezer](https://github.com/adobe/aem-assets-selectors-mfe-examples).

<!--
### ImsAuthProps {#ims-auth-props}

The `ImsAuthProps` properties define the authentication information and flow that the Asset Selector uses to obtain an `imsToken`. By setting these properties, you can control how the authentication flow should behave and register listeners for various authentication events.

| Property Name | Description|
|---|---|
| `imsClientId`| A string value representing the IMS client ID used for authentication purposes. This value is provided by Adobe and is specific to your Adobe AEM CS organization.|
| `imsScope`| Describes the scopes used in authentication. The scopes determine the level of access that the application has to your organization resources. Multiple scopes can be separated by commas.|
| `redirectUrl` | Represents the URL where the user is redirected after authentication. This value is typically set to the current URL of the application. If a `redirectUrl` is not supplied, `ImsAuthService` will use the redirectUrl used to register the `imsClientId`|
| `modalMode`| A boolean indicating whether the authentication flow should be displayed in a modal (pop-up) or not. If set to `true`, the authentication flow is displayed in a pop-up. If set to `false`, the authentication flow is displayed in a full page reload. _Note:_ for better UX, you can dynamically control this value if the user has browser pop-up disabled. |
| `onImsServiceInitialized`| A callback function that is called when the Adobe IMS authentication service is initialized. This function takes one parameter, `service`, which is an object representing the Adobe IMS service. See [`ImsAuthService`](#imsauthservice-ims-auth-service) for more details.|
| `onAccessTokenReceived`| A callback function that is called when an `imsToken` is received from the Adobe IMS authentication service. This function takes one parameter, `imsToken`, which is a string representing the access token. |
| `onAccessTokenExpired`| A callback function that is called when an access token has expired. This function is typically used to trigger a new authentication flow to obtain a new access token. |
| `onErrorReceived`| A callback function that is called when an error occurs during authentication. This function takes two parameters: the error type and error message. The error type is a string representing the type of error and the error message is a string representing the error message. |

### ImsAuthService {#ims-auth-service}

`ImsAuthService` class handles the authentication flow for the Asset Selector. It is responsible for obtaining an `imsToken` from the Adobe IMS authentication service. The `imsToken` is used to authenticate the user and authorize access to the Adobe Experience Manager (AEM) CS Assets repository. ImsAuthService uses the `ImsAuthProps` properties to control the authentication flow and register listeners for various authentication events. You can use the convenient [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) function to register the _ImsAuthService_ instance with the Asset Selector. The following functions are available on the `ImsAuthService` class. However, if you're using the _registerAssetsSelectorsAuthService_ function, you do not need to call these functions directly.

| Function Name | Description |
|---|---|
| `isSignedInUser` | Determines whether the user is currently signed in to the service and returns a boolean value accordingly.|
| `getImsToken`    | Retrieves the authentication `imsToken` for the currently signed-in user, which can be used to authenticate requests to other services such as generating asset _rendition.|
| `signIn`| Initiates the sign-in process for the user. This function uses the `ImsAuthProps` to show authentication in either a pop-up or a full page reload |
| `signOut`| Signs the user out of the service, invalidating their authentication token and requiring them to sign in again to access protected resources. Invoking this function will reload the current page.|
| `refreshToken`| Refreshes the authentication token for the currently signed-in user, preventing it from expiring and ensuring uninterrupted access to protected resources. Returns a new authentication token that can be used for subsequent requests. |
-->

### Voorbeeld voor de niet-SUSI-stroom {#non-susi-vanilla}

In dit voorbeeld wordt getoond hoe u Asset Selector kunt gebruiken met een niet-SUSI-stroom wanneer u een [!DNL Adobe] toepassing onder Verenigde Shell of wanneer u reeds hebt `imsToken` gegenereerd voor verificatie.

Neem het pakket Asset Selector in uw code op met het `script` tag, zoals weergegeven in _lijnen 6 tot en met 15_ van het onderstaande voorbeeld. Wanneer het script is geladen, wordt het `PureJSSelectors` algemene variabele is beschikbaar voor gebruik. De middelenkiezer definiëren [eigenschappen](#asset-selector-properties) zoals getoond in _lijnen 16 tot en met 23_. De `imsOrg` en `imsToken` beide eigenschappen zijn vereist voor verificatie in niet-SUSI-stroom. De `handleSelection` wordt gebruikt om de geselecteerde elementen af te handelen. Als u de Asset Selector wilt renderen, roept u de `renderAssetSelector` functie als vermeld in _lijn 17_. De Asset Selector wordt weergegeven in het dialoogvenster `<div>` containerelement, zoals getoond in _lijnen 21 en 22_.

Als u deze stappen uitvoert, kunt u Asset Selector gebruiken met een niet-SUSI-stroom in uw [!DNL Adobe] toepassing.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in non-SUSI flow
        const assetSelectorProps = {
            imsOrg: 'example-ims@AdobeOrg',
            imsToken: "example-imsToken",
            apiKey: "example-apiKey-associated-with-imsOrg",
            handleSelection: (assets: SelectedAssetType[]) => {},
        };
        // Call the `renderAssetSelector` available in PureJSSelectors globals to render AssetSelector
        PureJSSelectors.renderAssetSelector(container, assetSelectorProps);
    </script>
</head>

<body>
    <div id="asset-selector-container" style="height: calc(100vh - 80px); width: calc(100vw - 60px); margin: -20px;">
    </div>
</body>

</html>
```

Ga voor meer informatie naar [Voorbeeld van code voor middelenkiezer](https://github.com/adobe/aem-assets-selectors-mfe-examples).

<!--
### Example for the SUSI flow {#susi-vanilla}

Use this example `index.html` file for authentication if you are integrating your application using SUSI flow.

Access the Asset Selector package using the `Script` Tag, as shown in *line 9* to *line 11* of the example `index.html` file.

*Line 14* to *line 38* of the example describes the IMS flow properties, such as `imsClientId`, `imsScope`, and `redirectURL`. The function requires that you define at least one of the `imsClientId` and `imsScope` properties. If you do not define a value for `redirectURL`, the registered redirect URL for the client ID is used.

As you do not have an `imsToken` generated, use the `registerAssetsSelectorsAuthService` and `renderAssetSelectorWithAuthFlow` functions, as shown in line 40 to line 50 of the example `index.html` file. Use the `registerAssetsSelectorsAuthService` function before `renderAssetSelectorWithAuthFlow` to register the `imsToken` with the Asset Selector. [!DNL Adobe] recommends to call `registerAssetsSelectorsAuthService` when you instantiate the component.

Define the authentication and other Assets as a Cloud Service access-related properties in the `const props` section, as shown in *line 54* to *line 60* of the example `index.html` file.

The `PureJSSelectors` global variable, mentioned in *line 65*, is used to render the Asset Selector in the web browser.

Asset Selector is rendered on the `<div>` container element, as mentioned in *line 74* to *line 81*. The example uses a dialog to display the Asset Selector.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>

<head>
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta charset="utf-8">
    <title>Asset Selectors</title>
    <link rel="stylesheet" href="index.css">
    <script id="asset-selector"
        src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/asset-selectors.js"></script>
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
-->

## Eigenschappen van Asset Selector gebruiken {#asset-selector-properties}

U kunt de eigenschappen van de Asset Selector gebruiken om de manier aan te passen waarop de Asset Selector wordt weergegeven. In de volgende tabel worden de eigenschappen weergegeven die u kunt gebruiken om de functie Asset Selector aan te passen en te gebruiken.

| Eigenschap | Type | Vereist | Standaard | Beschrijving |
|---|---|---|---|---|
| *spoor* | boolean | Nee | false | Indien gemarkeerd `true`, Asset Selector wordt weergegeven in een linkerspoorweergave. Als het is gemarkeerd `false`, wordt de Asset Selector weergegeven in de modale weergave. |
| *imsOrg* | string | Ja |  | Adobe Identity Management System-id (IMS) die tijdens de provisioning is toegewezen [!DNL Adobe Experience Manager] als [!DNL Cloud Service] voor uw organisatie. De `imsOrg` is vereist om te verifiëren of de organisatie waartoe u toegang hebt onder Adobe IMS valt of niet. |
| *imsToken* | string | Nee |  | IMS-token voor toonder die wordt gebruikt voor verificatie. `imsToken` is niet vereist als u de SUSI-flow gebruikt. Nochtans, wordt het vereist als u niet-SUSI stroom gebruikt. |
| *apiKey* | string | Nee |  | API-sleutel die wordt gebruikt voor toegang tot de AEM Discovery-service. `apiKey` is niet vereist als u de SUSI-flow gebruikt. Dit is echter vereist in niet-SUSI-stromen. |
| *rootPath* | string | Nee | /content/dam/ | Mappad waaruit de middelen worden weergegeven door de Asset Selector. `rootPath` kan ook in de vorm van inkapseling worden gebruikt. Voorbeeld: `/content/dam/marketing/subfolder/`Met Asset Selector kunt u niet door een bovenliggende map bladeren, maar alleen de onderliggende mappen weergeven. |
| *pad* | string | Nee |  | Pad dat wordt gebruikt om naar een specifieke map met elementen te navigeren wanneer de Asset Selector wordt weergegeven. |
| *filterSchema* | array | Nee |  | Model dat wordt gebruikt om filtereigenschappen te vormen. Dit is handig wanneer u bepaalde filteropties in de Asset Selector wilt beperken. |
| *filterFormProps* | Object | Nee |  | Geef de filtereigenschappen op die u nodig hebt om de zoekopdracht te verfijnen. Bijvoorbeeld MIME-type JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nee |  | Geselecteerde elementen opgeven wanneer de Asset Selector wordt weergegeven. Een array van objecten is vereist die een id-eigenschap van de elementen bevat. Bijvoorbeeld: `[{id: 'urn:234}, {id: 'urn:555'}]` Een element moet beschikbaar zijn in de huidige directory. Als u een andere map moet gebruiken, geeft u een waarde op voor de `path` ook eigenschap. |
| *acvConfig* | Object | Nee |  | De bezit van de Mening van de Inzameling van activa dat voorwerp bevat dat douaneconfiguratie bevat om gebreken met voeten te treden. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nee |  | Als de OOTB-vertalingen onvoldoende zijn voor de behoeften van uw toepassing, kunt u een interface beschikbaar maken waarmee u uw eigen aangepaste gelokaliseerde waarden kunt doorgeven via de `i18nSymbols` prop. Als u een waarde door deze interface doorgeeft, overschrijft u de standaardvertalingen die worden geleverd en gebruikt u in plaats daarvan uw eigen vertaling.  Als u de overschrijving wilt uitvoeren, moet u een geldige waarde opgeven [Berichtbeschrijving](https://formatjs.io/docs/react-intl/api/#message-descriptor) naar de toets van `i18nSymbols` die u wilt overschrijven. |
| *intl* | Object | Nee |  | Asset Selector biedt standaard OOTB-vertalingen. U kunt de vertaaltaal selecteren door een geldige tekenreeks voor de landinstelling op te geven via het dialoogvenster `intl.locale` prop. Bijvoorbeeld: `intl={{ locale: "es-es" }}` </br></br> De landinstellingstekenreeksen die worden ondersteund, volgen de [ISO 639 - Codes](https://www.iso.org/iso-639-language-codes.html) voor de vertegenwoordiging van namen van taalnormen. </br></br> Lijst met ondersteunde landinstellingen: Engels - &#39;en-us&#39; (standaard) Spaans - &#39;es-es&#39; Duits - &#39;de-de&#39; Frans - &#39;fr-fr&#39; Italiaans - &#39;it-it&#39; Japans - &#39;ja-jp&#39; Koreaans - &#39;ko-kr&#39; Portugees - &#39;pt-br&#39; Chinees (traditioneel) - &#39;zh-cn&#39; Chinees (Taiwan) - &#39;zh-tw&#39; |
| *repositoryId* | string | Nee | &#39;&#39; | Opslagplaats waar de inhoud wordt geladen door de Asset Selector. |
| *additionalAemSolutions* | `Array<string>` | Nee | [ ] | Hiermee kunt u een lijst met extra AEM opslagplaatsen toevoegen. Als deze eigenschap geen informatie bevat, worden alleen mediawisselaars of AEM Assets-opslagruimten in aanmerking genomen. |
| *hideTreeNav* | boolean | Nee |  | Hiermee geeft u op of de zijbalk met boomnavigatie met elementen moet worden weergegeven of verborgen. Het wordt alleen in modale zin gebruikt en daarom heeft dit onroerend goed geen effect in de spoorwegen. |
| *onDrop* | -functie | Nee |  | De eigenschap staat de neerzetfunctionaliteit van een element toe. |
| *dropOptions* | `{allowList?: Object}` | Nee |  | Vormt dalingsopties gebruikend &quot;lijst van gewenste personen&quot;. |
| *colorScheme* | string | Nee |  | Thema configureren (`light` of `dark`) voor de Asset Selector. |
| *handleSelection* | -functie | Nee |  | Wordt aangeroepen met een array van Asset-items wanneer activa worden geselecteerd en de `Select` op de modale knop wordt geklikt. Deze functie wordt alleen aangeroepen in de modale weergave. Voor de spoorstaafweergave gebruikt u de `handleAssetSelection` of `onDrop` functies. Voorbeeld: <pre>handleSelection=(assets: Element[])=> {..}</pre> Zie [Geselecteerd elementtype](#selected-asset-type) voor meer informatie. |
| *handleAssetSelection* | -functie | Nee |  | Wordt aangeroepen met een array van items wanneer de elementen worden geselecteerd of niet geselecteerd. Dit is handig wanneer u naar elementen wilt luisteren terwijl de gebruiker deze selecteert. Voorbeeld: <pre>handleSelection=(assets: Element[])=> {..}</pre> Zie [Geselecteerd elementtype](#selected-asset-type) voor meer informatie. |
| *onClose* | -functie | Nee |  | Wordt aangeroepen wanneer `Close` wordt in de modale weergave ingedrukt. Dit wordt alleen aangeroepen in `modal` in `rail` weergeven. |
| *onFilterSubmit* | -functie | Nee |  | Wordt aangeroepen met filteritems wanneer de gebruiker andere filtercriteria wijzigt. |
| *selectionType* | string | Nee | enkel | Configuratie voor `single` of `multiple` selectie van elementen tegelijk. |

## Voorbeelden voor het gebruik van de eigenschappen van Asset Selector {#usage-examples}

U kunt de Asset Selector definiëren [eigenschappen](#asset-selector-properties) in de `index.html` bestand om de weergave van de Asset Selector in uw toepassing aan te passen.

### Voorbeeld 1: Kiezer voor bedrijfsmiddelen in de spoorweergave

![spoorstaafvoorbeeld](assets/rail-view-example-vanilla.png)

Als de waarde van de AssetSelector `rail` is ingesteld op `false` of niet wordt vermeld in de eigenschappen, de vertoningen van de Selecteur van Activa in de Modale mening door gebrek.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### Voorbeeld 2: Metagegevens pop-up

Gebruik verschillende eigenschappen om de metagegevens te definiëren van een element dat u wilt weergeven met een info-pictogram. De info popover verstrekt de inzameling van informatie over activa of de omslag met inbegrip van titel, afmetingen, datum van wijziging, plaats, en beschrijving van activa. In het onderstaande voorbeeld worden verschillende eigenschappen gebruikt om metagegevens van een element weer te geven, bijvoorbeeld `repo:path` eigenschap geeft de locatie van een element aan. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)


### Voorbeeld 3: Aangepaste filtereigenschap in spoorweergave

Naast de beperkte zoekopdracht kunt u met de middelenkiezer verschillende kenmerken aanpassen om uw zoekopdracht te verfijnen van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] toepassing. U moet de volgende code toevoegen om aangepaste zoekfilters in uw toepassing toe te voegen. In het onderstaande voorbeeld wordt `Type Filter` zoek naar het type element tussen Afbeeldingen, Documenten of Video&#39;s of het filtertype dat u voor de zoekopdracht hebt toegevoegd.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

<!-- Property details to be added here. Referred the ticket https://jira.corp.adobe.com/browse/ASSETS-19023-->

<!--
## Asset Selector Object Schema {#object-schema}

Schema describes the object properties associated with an asset selected using Asset Selector. It uses the combination of data types and their values to validate the object describing the selected Asset using an Asset Selector.

**Schema Syntax**
````
interface SelectedAsset {
    'repo:id': string;
    'repo:name': string;
    'repo:path': string;
    'repo:size': number;
    'repo:createdBy': string;
    'repo:createDate': string;
    'repo:modifiedBy': string; 
    'repo:modifyDate': string; 
    'dc:format': string; 
    'tiff:imageWidth': number;
    'tiff:imageLength': number;
    'repo:state': string;
    computedMetadata: Record<string, any>;
    _links: {
        'http://ns.adobe.com/adobecloud/rel/rendition': Array<{
            href: string;
            type: string;
            'repo:size': number;
            width: number;
            height: number;
            [others: string]: any;
        }>;
    };
}
````

**Query Parameters**

| Parameter | Type | Description |
|---|---|---|
| repo:id | string | ID of an Asset |
| repo:name | string | The name of an Asset |
| repo:path | string | The path of an Asset |
| repo:size | number | Size of an Asset (in bytes) |
| repo:createdBy | string | ID of a user who created an Asset |
| repo: createdDate | string | The timestamp when an asset was created |
| repo:modifiedBy | string | ID of a user who modified the asset recently |
| repo:modifyDate | string | The timestamp when the asset was last modified |
| dc:format | string | MIME type of an Asset |
| tiff:imageWidth | number | The width of an image type of Asset |
| tiff:imageLength | number | The height of an image type of Asset |
| repo:state | string | The `Approved`, `Rejected`, or `Expired`state of an Asset |
| computedMetadata | string | It is an object that represents a bucket for all the Asset's metadata of all kinds (repository, application or embedded metadata) |
| _links | string | It represents the collection of links used in the Asset Selector. The links are represented in the form of an array. The parameters of an array include: `href`, `type`, `repo:size`, `width`, `height`, etc.  |

For the detailed example of Object Schema, click 
-->

## Selectie van elementen afhandelen met behulp van objectschema {#handling-selection}

De `handleSelection` Deze eigenschap wordt gebruikt om een of meer selecties van Elementen in Elementenkiezer te verwerken. In het onderstaande voorbeeld wordt de gebruikssyntaxis van `handleSelection`.

![handgreep-selectie](assets/handling-selection.png)

## Elementkiezer gebruiken {#using-asset-selector}

Zodra de Asset Selector is ingesteld en u bent geverifieerd dat u Asset Selector kunt gebruiken met uw [!DNL Adobe Experience Manager] als [!DNL Cloud Service] kunt u elementen selecteren of verschillende andere bewerkingen uitvoeren om te zoeken naar uw elementen in de opslagplaats.

![met middelenkiezer](assets/using-asset-selector.png)

* **A**: [Deelvenster verbergen/tonen](#hide-show-panel)
* **B**: [Repository-switch](#repository-switcher)
* **C**: [Activa](#repository)
* **D**: [Filters](#filters)
* **E**: [Zoekbalk](#search-bar)
* **F**: [Sorteren](#sorting)
* **G**: [Sorteren in oplopende of aflopende volgorde](#sorting)
* **H**: [Weergave](#types-of-view)

### Deelvenster verbergen/tonen {#hide-show-panel}

Als u mappen in de linkernavigatie wilt verbergen, klikt u op **[!UICONTROL Hide folders]** pictogram. Als u de wijzigingen ongedaan wilt maken, klikt u op de knop **[!UICONTROL Hide folders]** weer.

### Repository-switch {#repository-switcher}

Met Asset Selector kunt u ook schakelen tussen opslagruimten voor middelenselectie. U kunt de opslagplaats van uw keus van drop-down selecteren beschikbaar in het linkerpaneel. De opslagruimteopties in de vervolgkeuzelijst zijn gebaseerd op de `repositoryId` eigenschap gedefinieerd in het dialoogvenster `index.html` bestand. Het is gebaseerd op de milieu&#39;s van geselecteerde IMS org die door de het programma geopende gebruiker wordt betreden. Consumenten kunnen een voorkeursbehandeling doorgeven `repositoryID` en in dat geval stopt de Asset Selector met het renderen van de repo-switch en geeft hij alleen activa van de gegeven repository weer.
<!--
It is based on the `imsOrg` that is provided in the application. If you want to see the list of repositories, then `repositoryId` is required to view those specific repositories in your application.
-->

### Middelenopslagplaats

Het is een verzameling mappen met elementen die u kunt gebruiken om bewerkingen uit te voeren.

### Buiten-de-box filters {#filters}

De Kiezer van activa verstrekt ook uit-van-de-doos filteropties om uw onderzoeksresultaten te verfijnen. De volgende filters zijn beschikbaar:

* `File type`: omvat map, bestand, afbeeldingen, documenten of video
* `MIME type`: inclusief JPG, GIF, PPTX, PNG, MP4, DOCX, TIFF, PDF, XLSX
* `Image Size`: inclusief minimale/maximale breedte, minimale/maximale hoogte van afbeelding

![spoorstaafvoorbeeld](assets/filters-asset-selector.png)

### Aangepaste zoekopdracht

Met Asset Selector kunt u naast de zoekopdracht in volledige tekst ook elementen in bestanden zoeken met behulp van een aangepaste zoekopdracht. U kunt aangepaste zoekfilters gebruiken in zowel de modusweergave als de spoorweergave.

![aangepast zoeken](assets/custom-search.png)

U kunt ook een standaardzoekfilter maken om de velden op te slaan waarnaar u vaak zoekt en deze later te gebruiken. Als u een aangepaste zoekopdracht naar uw elementen wilt maken, kunt u `filterSchema` eigenschap.

### Zoekbalk {#search-bar}

Met Asset Selector kunt u de volledige tekst van de middelen in de geselecteerde opslagplaats doorzoeken. Als u bijvoorbeeld het trefwoord typt `wave` in de zoekbalk, alle elementen met de opdracht `wave` trefwoord dat in een van de metagegevenseigenschappen wordt vermeld, wordt weergegeven.

### Sorteren {#sorting}

U kunt elementen in de Asset Selector sorteren op naam, afmetingen of grootte van een element. U kunt de elementen ook in oplopende of aflopende volgorde sorteren.

### Weergavetypen {#types-of-view}

Met Asset Selector kunt u het element in vier verschillende weergaven weergeven:

* **![lijstweergave](assets/do-not-localize/list-view.png)[!UICONTROL List View]**: In de lijstweergave worden schuifbare bestanden en mappen in één kolom weergegeven.
* **![rasterweergave](assets/do-not-localize/grid-view.png)[!UICONTROL Grid View]**: In de rasterweergave worden schuifbare bestanden en mappen weergegeven in een raster met rijen en kolommen.
* **![galerieweergave](assets/do-not-localize/gallery-view.png)[!UICONTROL Gallery View]**: In de galerieweergave worden bestanden of mappen weergegeven in een horizontale lijst die in het midden is vergrendeld.
* **![watervalweergave](assets/do-not-localize/waterfall-view.png)[!UICONTROL Waterfall View]**: In de watervalweergave worden bestanden of mappen weergegeven in de vorm van een Bridge.

<!--
### Modes to view Asset Selector

Asset Selector supports two types of out of the box views:

**  Modal view or Inline view:** The modal view or inline view is the default view of Asset Selector that represents Assets folders in the front area. The modal view allows users to view assets in a full screen to ease the selection of multiple assets for import. Use `<AssetSelector rail={false}>` to enable modal view.

    ![modal-view](assets/modal-view.png)

**  Rail view:** The rail view represents Assets folders in a left panel. The drag and drop of assets can be performed in this view. Use `<AssetSelector rail={true}>` to enable rail view.

    ![rail-view](assets/rail-view.png)
-->
<!--

### Application Integration

Asset Selector is flexible and can be integrated within your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application. It is accessible and localized to add, search, and select assets in your application. With Asset Selector you can:
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It allows you to control the display of various text or symbols as per your choice.
*   **Perfect fit** Asset selector easily fits in your existing [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application and choose the way you want to view. The mode of view can be inline, rail, or modal view.
*   **Accessible** With Asset Selector, you can reach the desired asset in an easy manner.
*   **Localize** Assets can be availed for the various locales available as per Adobe's localization standards.
-->
<!--

### Support for multiple instances

The micro front-end design supports the display of multiple instances of Asset Selector on a single screen.

![multiple-instance](assets/multiple-instance.png)
-->

<!--

### Controlled selection with multi-select

You can make default multi-selection of assets by specifying the assets to the component using `selectedAssets` property. You should specify an array of asset IDs. For example, `[{id: 'urn:234}, {id: 'urn:555'}].`
-->
<!--

### Action buttons

When you customize your application with Asset Selector based on ReactJS, you are provided with the following action buttons to perform various actions:
*   **Open in media library** Allows you to open the asset in media library.
*   **Upload** Allows you to upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector allows you to know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->