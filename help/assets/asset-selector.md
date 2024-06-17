---
title: Asset Selector voor [!DNL Adobe Experience Manager] als [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
contentOwner: KK
role: Admin, User
exl-id: 5f962162-ad6f-4888-8b39-bf5632f4f298
feature: Collaboration
source-git-commit: ab2cf8007546f538ce54ff3e0b92bb0ef399c758
workflow-type: tm+mt
source-wordcount: '3896'
ht-degree: 0%

---

# Micro-Frontend element selecteren {#Overview}

Micro-Frontend Asset Selector biedt een gebruikersinterface die eenvoudig kan worden geïntegreerd met de [!DNL Experience Manager Assets] zodat u door de in de opslagplaats beschikbare digitale middelen kunt bladeren of deze kunt zoeken en kunt gebruiken in de ontwerpervaring van uw toepassing.

De gebruikersinterface van Micro-Frontend wordt beschikbaar gesteld in uw toepassingservaring gebruikend het pakket van de Selecteur van Activa. Alle updates van het pakket worden automatisch geïmporteerd en de nieuwste versie van Asset Selector wordt automatisch in de toepassing geladen.

![Overzicht](assets/overview.png)

Asset Selector biedt vele voordelen, zoals:

* Eenvoudige integratie met een van de [Adobe](#asset-selector-ims) of [niet-Adobe](#asset-selector-non-ims) toepassingen die gebruikmaken van Vanilla JavaScript-bibliotheek.
* Eenvoudig te onderhouden als updates van het middelenkiezerpakket worden automatisch geïmplementeerd op de Asset Selector die beschikbaar is voor uw toepassing. Uw toepassing hoeft geen updates uit te voeren om de laatste wijzigingen te laden.
* Gemakkelijk aanpassen aangezien er eigenschappen beschikbaar zijn die de vertoning van de Selecteur van Activa binnen uw toepassing controleren.
* In de volledige tekst doorzoeken, uit-van-de-doos, en aangepaste filters om snel aan activa voor gebruik binnen de auteurservaring te navigeren.
* Mogelijkheid om binnen een IMS-organisatie te schakelen tussen opslagruimten voor het selecteren van bedrijfsmiddelen.
* De mogelijkheid om elementen te sorteren op naam, afmetingen en grootte en ze weer te geven in de weergave Lijst, Raster, Galerie of Waterval.

<!--Perform the following tasks to integrate and use Asset Selector with your [!DNL Experience Manager Assets] repository:

1. [Install Asset Selector](#installation)
2. [Integrate Asset Selector using Vanilla JS](#integration-using-vanilla-js)
3. [Use Asset Selector](#using-asset-selector)
-->

<!--
## Setting up Asset Selector {#asset-selector-setup}

![Asset Selector set up](assets/asset-selector-prereqs.png)
-->

## Vereisten{#prereqs}

U moet de volgende communicatiemethoden gebruiken:

* De toepassing wordt uitgevoerd op HTTPS.
* De URL van de toepassing bevindt zich in de lijst van gewenste personen van de IMS-client voor het doorsturen van URL&#39;s.
* De IMS-aanmeldstroom wordt geconfigureerd en weergegeven met een pop-up in de webbrowser. Daarom moeten pop-ups worden ingeschakeld of toegestaan in de doelbrowser.

Gebruik de bovenstaande voorwaarden als u een IMS-verificatieworkflow van de Asset Selector nodig hebt. Als u al bent geverifieerd met de IMS-workflow, kunt u in plaats daarvan de IMS-informatie toevoegen.

>[!IMPORTANT]
>
> Deze opslagplaats is bedoeld als aanvullende documentatie waarin de beschikbare API&#39;s en gebruiksvoorbeelden voor de integratie van Asset Selector worden beschreven. Voordat u de functie Asset Selector gaat installeren of gebruiken, moet u controleren of uw organisatie beschikt over de toegang tot Asset Selector als onderdeel van het as a Cloud Service Experience Manager Assets-profiel. Als u niet provisioned bent, kunt u deze componenten niet integreren of gebruiken. Om levering te verzoeken, zou uw programma admin een steunkaartje moeten opheffen duidelijk als P2 van Admin Console en de volgende informatie omvatten:
>
>* Domeinnamen waarbij de integrerende toepassing wordt gehost.
>* Na levering, zal uw organisatie worden voorzien van `imsClientId`, `imsScope`en `redirectUrl` die overeenkomen met de gevraagde omgevingen die essentieel zijn voor de configuratie van Asset Selector. Zonder deze geldige eigenschappen kunt u de installatiestappen niet uitvoeren.

## Installatie {#installation}

Asset Selector is beschikbaar via beide ESM CDN (bijvoorbeeld [esm.sh](https://esm.sh/)/[skypack](https://www.skypack.dev/)) en [UMD](https://github.com/umdjs/umd) versie.

In browsers die **UMD-versie** (aanbevolen):

```
<script src="https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/assets-selectors.js"></script>

<script>
  const { renderAssetSelector } = PureJSSelectors;
</script>
```

In browsers met `import maps` ondersteuning gebruiken **ESM CDN-versie**:

```
<script type="module">
  import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
</script>
```

In Deno/Webpack Module Federation met **ESM CDN-versie**:

```
import { AssetSelector } from 'https://experience.adobe.com/solutions/CQ-assets-selectors/static-assets/resources/@assets/selectors/index.js'
```

## Asset Selector integreren met Vanilla JS {#integration-using-vanilla-js}

U kunt alle [!DNL Adobe] of niet-Adobe [!DNL Experience Manager Assets] opslagplaats en selecteer elementen vanuit de toepassing. Zie [Integratie van Asset Selector met verschillende toepassingen](#asset-selector-integration-with-apps).

De integratie gebeurt door het pakket Asset Selector te importeren en verbinding te maken met de middelen die zijn as a Cloud Service met de Vanilla JavaScript-bibliotheek. Een `index.html` of een geschikt bestand in uw toepassing om:

* De verificatiedetails definiëren
* Toegang krijgen tot de as a Cloud Service gegevensopslagruimte
* De weergave-eigenschappen voor de middelenkiezer configureren

U kunt verificatie uitvoeren zonder enkele IMS-eigenschappen te definiëren, als:

* U integreert een [!DNL Adobe] toepassing op [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=en).
* Er is al een IMS-token gegenereerd voor verificatie.

## Asset Selector integreren met verschillende toepassingen {#asset-selector-integration-with-apps}

U kunt Asset Selector integreren met verschillende toepassingen, zoals:

* [Asset Selector integreren met een [!DNL Adobe] toepassing](#adobe-app-integration-vanilla)
* [Asset Selector integreren met een toepassing zonder Adobe](#adobe-non-app-integration)

>[!BEGINTABS]

<!--Integration with an Adobe application content starts here-->

>[!TAB Integratie met een Adobe-toepassing]

### Vereisten{#prereqs-adobe-app}

Gebruik de volgende voorwaarden als u Asset Selector integreert met een [!DNL Adobe] toepassing:

* [Communicatiemethoden](#prereqs)
* imsOrg
* imsToken
* apikey

### Asset Selector integreren met een [!DNL Adobe] toepassing {#adobe-app-integration-vanilla}

In het volgende voorbeeld wordt het gebruik van Asset Selector getoond wanneer een [!DNL Adobe] toepassing onder Verenigde Shell of wanneer u reeds hebt `imsToken` gegenereerd voor verificatie.

Neem het pakket Asset Selector in uw code op met het `script` tag, zoals weergegeven in _lijnen 6-15_ van het onderstaande voorbeeld. Wanneer het script is geladen, wordt het `PureJSSelectors` algemene variabele is beschikbaar voor gebruik. De middelenkiezer definiëren [eigenschappen](#asset-selector-properties) zoals getoond in _lijnen 16-23_. De `imsOrg` en `imsToken` beide eigenschappen zijn vereist voor verificatie in een Adobe toepassing. De `handleSelection` wordt gebruikt om de geselecteerde elementen af te handelen. Als u de Asset Selector wilt renderen, roept u de `renderAssetSelector` functie als vermeld in _lijn 17_. De functie Asset Selector wordt weergegeven in het dialoogvenster `<div>` containerelement, zoals getoond in _lijnen 21 en 22_.

Als u deze stappen uitvoert, kunt u Asset Selector gebruiken met uw [!DNL Adobe] toepassing.

```html {line-numbers="true"}
<!DOCTYPE html>
<html>
<head>
    <title>Asset Selector</title>
    <script src="https://experience.adobe.com/solutions/CQ-assets-selectors/assets/resources/assets-selectors.js"></script>
    <script>
        // get the container element in which we want to render the AssetSelector component
        const container = document.getElementById('asset-selector-container');
        // imsOrg and imsToken are required for authentication in Adobe application
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

<!--For detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

+++**ImsAuthProps**
De `ImsAuthProps` eigenschappen definiëren de verificatiegegevens en de stroom die de Asset Selector gebruikt om een `imsToken`. Door deze eigenschappen te plaatsen, kunt u controleren hoe de authentificatiestroom zich zou moeten gedragen en luisteraars voor diverse authentificatiegebeurtenissen registreren.

| Eigenschapnaam | Beschrijving |
|---|---|
| `imsClientId` | Een tekenreekswaarde die de IMS client-id vertegenwoordigt die voor verificatiedoeleinden wordt gebruikt. Deze waarde wordt verstrekt door Adobe en is specifiek voor uw Adobe AEM organisatie CS. |
| `imsScope` | Beschrijft het werkingsgebied dat in authentificatie wordt gebruikt. Het werkingsgebied bepaalt het niveau van toegang dat de toepassing aan uw organisatiemiddelen heeft. Meerdere bereiken kunnen worden gescheiden door komma&#39;s. |
| `redirectUrl` | Geeft de URL aan waar de gebruiker na verificatie opnieuw wordt omgeleid. Deze waarde wordt doorgaans ingesteld op de huidige URL van de toepassing. Indien een `redirectUrl` niet wordt geleverd, `ImsAuthService` gebruikt redirectUrl die wordt gebruikt om `imsClientId` |
| `modalMode` | Een Booleaanse waarde die aangeeft of de verificatiestroom al dan niet moet worden weergegeven in een modaal (pop-upmenu). Indien ingesteld op `true`, wordt de authentificatiestroom getoond in een pop-up. Indien ingesteld op `false`, wordt de verificatiestroom weergegeven in een volledige pagina die opnieuw wordt geladen. _Opmerking:_ voor een betere UX kunt u deze waarde dynamisch beheren als de gebruiker de browser pop-up heeft uitgeschakeld. |
| `onImsServiceInitialized` | Een callback-functie die wordt aangeroepen wanneer de Adobe IMS-verificatieservice wordt geïnitialiseerd. Deze functie heeft één parameter, `service`, dat een object is dat staat voor de Adobe IMS-service. Zie [`ImsAuthService`](#imsauthservice-ims-auth-service) voor meer informatie . |
| `onAccessTokenReceived` | Een callback-functie die wordt aangeroepen wanneer een `imsToken` wordt ontvangen van de Adobe IMS-verificatieservice. Deze functie heeft één parameter, `imsToken`, dat een tekenreeks is die het toegangstoken vertegenwoordigt. |
| `onAccessTokenExpired` | Een callback functie die wordt geroepen wanneer een toegangstoken is verlopen. Deze functie wordt typisch gebruikt om een nieuwe authentificatiestroom teweeg te brengen om een nieuw toegangstoken te verkrijgen. |
| `onErrorReceived` | Een callback functie die wordt geroepen wanneer een fout tijdens authentificatie voorkomt. Deze functie heeft twee parameters: het fouttype en het foutbericht. Het fouttype is een tekenreeks die het type fout vertegenwoordigt en het foutbericht is een tekenreeks die het foutbericht vertegenwoordigt. |

+++

+++**ImsAuthService**
`ImsAuthService` -klasse handelt de verificatiestroom voor de Asset Selector af. Het is de taak van `imsToken` van de Adobe IMS-verificatieservice. De `imsToken` wordt gebruikt om de gebruiker te verifiëren en toegang tot [!DNL Adobe Experience Manager] als [!DNL Cloud Service] Middelenopslagplaats. ImsAuthService gebruikt de `ImsAuthProps` eigenschappen om de authentificatiestroom te controleren en luisteraars voor diverse authentificatiegebeurtenissen te registreren. U kunt het handige gebruiken [`registerAssetsSelectorsAuthService`](#purejsselectorsregisterassetsselectorsauthservice) functie om de _ImsAuthService_ met de Asset Selector. De volgende functies zijn beschikbaar op de `ImsAuthService` klasse. Als u echter de opdracht _registerAssetsSelectorsAuthService_ als u deze functies niet rechtstreeks wilt aanroepen.

| Functienaam | Beschrijving |
|---|---|
| `isSignedInUser` | Bepaalt of de gebruiker momenteel binnen aan de dienst wordt ondertekend en een booleaanse waarde dienovereenkomstig terugkeert. |
| `getImsToken` | Hiermee wordt de verificatie opgehaald `imsToken` voor de momenteel aangemelde gebruiker, die kan worden gebruikt voor het verifiëren van aanvragen voor andere services, zoals het genereren van asset_rendition. |
| `signIn` | Hiermee wordt het aanmeldingsproces voor de gebruiker gestart. Deze functie gebruikt de `ImsAuthProps` om verificatie weer te geven in een pop-up of een volledige pagina die opnieuw wordt geladen |
| `signOut` | Signs the user out of the service, invalidating their authentication token and require them to sign in again to access protected resources. Als u deze functie aanroept, wordt de huidige pagina opnieuw geladen. |
| `refreshToken` | Verfrist het authentificatietoken voor de momenteel ondertekende gebruiker, verhinderend het en ononderbroken toegang tot beschermde middelen te verzekeren. Keert een nieuw authentificatietoken terug dat voor verdere verzoeken kan worden gebruikt. |

+++

+++**Validatie met opgegeven IMS-token**

```
<script>
    const apiToken="<valid IMS token>";
    function handleSelection(selection) {
    console.log("Selected asset: ", selection);
    };
    function renderAssetSelectorInline() {
    console.log("initializing Asset Selector");
    const props = {
    "repositoryId": "delivery-p64502-e544757.adobeaemcloud.com",
    "apiKey": "ngdm_test_client",
    "imsOrg": "<IMS org>",
    "imsToken": apiToken,
    handleSelection,
    hideTreeNav: true
    }
    const container = document.getElementById('asset-selector-container');
    PureJSSelectors.renderAssetSelector(container, props);
    }
    $(document).ready(function() {
    renderAssetSelectorInline();
    });
</script>
```

+++

+++**Callbacks van de dienst van IMS registreren**

```
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

+++

<!--Integration with non-Adobe application content starts here-->

>[!TAB Integratie met een toepassing zonder Adobe]

<!--### Integrate Asset Selector with a [!DNL non-Adobe] application {#adobe-non-app-integration}-->

### Vereisten {#prereqs-non-adobe-app}

Gebruik de volgende voorwaarden als u Asset Selector integreert met een toepassing zonder Adobe:

* [Communicatiemethoden](#prereqs)
* imsClientId
* imsScope
* redirectUrl
* imsOrg
* apikey

Asset Selector ondersteunt verificatie voor de [!DNL Experience Manager Assets] opslagplaats die gebruikmaakt van Identity Management System (IMS)-eigenschappen zoals `imsScope` of `imsClientID` wanneer u het met een niet-Adobe toepassing integreert.

+++**Asset Selector configureren voor een toepassing zonder Adobe**
Om de Selecteur van Activa voor een niet-Adobe toepassing te vormen, moet u eerst een steunkaartje voor levering registreren die door de integratiestappen wordt gevolgd.

**Een ondersteuningsticket registreren**
Stappen om een steunkaartje via de Admin Console te registreren:

1. Toevoegen **Asset Selector met AEM Assets** in de titel van het ticket.

1. Geef in de beschrijving de volgende gegevens op:

   * [!DNL Experience Manager Assets] als [!DNL Cloud Service] URL (programma-id en milieu-id).
   * Domeinnamen waarbij de niet-Adobe webtoepassing wordt gehost.
+++

+++**Integratiestappen**
Dit voorbeeld gebruiken `index.html` bestand voor verificatie bij integratie van Asset Selector met een toepassing zonder Adobe.

Gebruik het pakket Asset Selector om het `Script` Tag, zoals weergegeven in *lijn 9* tot *lijn 11* van het voorbeeld `index.html` bestand.

*Regel 14* tot *lijn 38* in het voorbeeld worden de eigenschappen van de IMS-stroom beschreven, zoals `imsClientId`, `imsScope`, en `redirectURL`. De functie vereist dat u ten minste een van de `imsClientId` en `imsScope` eigenschappen. Als u geen waarde definieert voor `redirectURL`, wordt de geregistreerde omleidings-URL voor de client-id gebruikt.

Aangezien u geen `imsToken` gegenereerd, gebruikt u de `registerAssetsSelectorsAuthService` en `renderAssetSelectorWithAuthFlow` functies, zoals getoond in lijn 40 tot lijn 50 van het voorbeeld `index.html` bestand. Gebruik de `registerAssetsSelectorsAuthService` functie voor `renderAssetSelectorWithAuthFlow` om de `imsToken` met de Asset Selector. [!DNL Adobe] raadt aan `registerAssetsSelectorsAuthService` wanneer u de component instantieert.

Bepaal de authentificatie en andere Activa as a Cloud Service op toegang betrekking hebbende eigenschappen in `const props` sectie, zoals getoond in *lijn 54* tot *lijn 60* van het voorbeeld `index.html` bestand.

De `PureJSSelectors` globale variabele, vermeld in *lijn 65*, wordt gebruikt om de Asset Selector in de webbrowser te renderen.

Asset Selector wordt weergegeven op de `<div>` containerelement, zoals vermeld in *lijn 74* tot *lijn 81*. In het voorbeeld wordt een dialoogvenster gebruikt om de Asset Selector weer te geven.

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

+++

+++**Kan geen toegang krijgen tot gegevensopslagruimte**

>[!TIP]
>
>Als u Asset Selector hebt geïntegreerd met de workflow Aanmelden maar nog steeds geen toegang hebt tot de gegevensopslagruimte, moet u ervoor zorgen dat browsercookies worden opgeschoond. Anders wordt het resultaat `invalid_credentials All session cookies are empty` fout in de console.

>[!ENDTABS]

## Eigenschappen van Asset Selector {#asset-selector-properties}

U kunt de eigenschappen van de Asset Selector gebruiken om de manier aan te passen waarop de Asset Selector wordt weergegeven. In de volgende tabel worden de eigenschappen weergegeven die u kunt gebruiken om de functie Asset Selector aan te passen en te gebruiken.

| Eigenschap | Type | Vereist | Standaard | Beschrijving |
|---|---|---|---|---|
| *spoor* | boolean | Nee | false | Indien gemarkeerd `true`, Asset Selector wordt weergegeven in een linkerspoorweergave. Als het is gemarkeerd `false`, wordt de Asset Selector weergegeven in de modale weergave. |
| *imsOrg* | string | Ja | | Adobe Identity Management System (IMS)-id die tijdens de provisioning is toegewezen [!DNL Adobe Experience Manager] als [!DNL Cloud Service] voor uw organisatie. De `imsOrg` is vereist om te controleren of de organisatie waartoe u toegang hebt, onder Adobe IMS valt of niet. |
| *imsToken* | string | Nee | | IMS-token voor toonder die wordt gebruikt voor verificatie. `imsToken` is vereist als u een [!DNL Adobe] toepassing voor de integratie. |
| *apiKey* | string | Nee | | API-sleutel die wordt gebruikt voor toegang tot de AEM Discovery-service. `apiKey` is vereist als u een [!DNL Adobe] toepassingsintegratie. |
| *rootPath* | string | Nee | /content/dam/ | Mappad waaruit de middelen worden weergegeven door de Asset Selector. `rootPath` kan ook in de vorm van inkapseling worden gebruikt. Als u bijvoorbeeld het volgende pad kiest, `/content/dam/marketing/subfolder/`Met Asset Selector kunt u niet door een bovenliggende map bladeren, maar alleen de onderliggende mappen weergeven. |
| *pad* | string | Nee | | Pad dat wordt gebruikt om naar een specifieke map met elementen te navigeren wanneer de Asset Selector wordt weergegeven. |
| *filterSchema* | array | Nee | | Model dat wordt gebruikt om filtereigenschappen te vormen. Dit is handig wanneer u bepaalde filteropties in de Asset Selector wilt beperken. |
| *filterFormProps* | Object | Nee | | Geef de filtereigenschappen op die u nodig hebt om de zoekopdracht te verfijnen. Bijvoorbeeld MIME-type JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nee |                 | Geselecteerde elementen opgeven wanneer de Asset Selector wordt weergegeven. Een array van objecten is vereist die een id-eigenschap van de elementen bevat. Bijvoorbeeld: `[{id: 'urn:234}, {id: 'urn:555'}]` Een element moet beschikbaar zijn in de huidige directory. Als u een andere map moet gebruiken, geeft u een waarde op voor de `path` ook eigenschap. |
| *acvConfig* | Object | Nee | | De bezit van de Mening van de Inzameling van activa dat voorwerp bevat dat douaneconfiguratie bevat om gebreken met voeten te treden. Deze eigenschap wordt ook gebruikt met `rail` eigenschap om de kijker van de middelen per spoor weer te geven. |
| *i18nSymbolen* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nee |                 | Als de OOTB-vertalingen onvoldoende zijn voor de behoeften van uw toepassing, kunt u een interface beschikbaar maken waarmee u uw eigen aangepaste gelokaliseerde waarden kunt doorgeven via de `i18nSymbols` prop. Als u een waarde door deze interface doorgeeft, overschrijft u de standaardvertalingen die worden geleverd en gebruikt u in plaats daarvan uw eigen vertaling. Als u de overschrijving wilt uitvoeren, moet u een geldige waarde opgeven [Berichtbeschrijving](https://formatjs.io/docs/react-intl/api/#message-descriptor) naar de toets van `i18nSymbols` die u wilt overschrijven. |
| *intl* | Object | Nee | | Asset Selector biedt standaard OTB-vertalingen. U kunt de vertaaltaal selecteren door een geldige landinstelling op te geven via het dialoogvenster `intl.locale` prop. Bijvoorbeeld: `intl={{ locale: "es-es" }}` </br></br> De landinstellingstekenreeksen die worden ondersteund volgen de [ISO 639 - Codes](https://www.iso.org/iso-639-language-codes.html) voor de vertegenwoordiging van namen van taalnormen. </br></br> Lijst met ondersteunde landinstellingen: Engels - &#39;en-us&#39; (standaard) Spaans - &#39;es-es&#39; Duits - &#39;de-de&#39; Frans - &#39;fr-fr&#39; Italiaans - &#39;it-it&#39; Japans - &#39;ja-jp&#39; Koreaans - &#39;ko-kr&#39; Portugees - &#39;pt-br&#39; Chinees (traditioneel) - &#39;zh-cn&#39; Chinees (Taiwan) - &#39;zh-tw&#39; |
| *repositoryId* | string | Nee | &#39;&#39; | Opslagplaats waar de inhoud wordt geladen door de Asset Selector. |
| *additionalAemSolutions* | `Array<string>` | Nee | [ ] | Hiermee kunt u een lijst met extra AEM opslagplaatsen toevoegen. Als deze eigenschap geen informatie bevat, worden alleen mediawisselaars of AEM Assets-opslagruimten in aanmerking genomen. |
| *hideTreeNav* | boolean | Nee |  | Hiermee geeft u op of de zijbalk met boomnavigatie met elementen moet worden weergegeven of verborgen. Het wordt alleen in modale zin gebruikt en daarom heeft dit onroerend goed geen effect in de spoorwegen. |
| *onDrop* | Functie | Nee | | Met de eigenschap kan een element worden neergezet. |
| *dropOptions* | `{allowList?: Object}` | Nee | | Vormt dalingsopties gebruikend &quot;lijst van gewenste personen&quot;. |
| *colorScheme* | string | Nee | | Thema configureren (`light` of `dark`) voor de Asset Selector. |
| *handleSelection* | Functie | Nee | | Wordt aangeroepen met een array van Asset-items wanneer activa worden geselecteerd en de `Select` op de modale knop wordt geklikt. Deze functie wordt alleen aangeroepen in de modale weergave. Voor de spoorstaafweergave gebruikt u de `handleAssetSelection` of `onDrop` functies. Voorbeeld: <pre>handleSelection=(assets: Asset[])=> {..}</pre> Zie [Geselecteerd elementtype](#selected-asset-type) voor meer informatie. |
| *handleAssetSelection* | Functie | Nee | | Wordt aangeroepen met een array van items wanneer de elementen worden geselecteerd of niet geselecteerd. Dit is handig wanneer u naar elementen wilt luisteren terwijl de gebruiker deze selecteert. Voorbeeld: <pre>handleSelection=(assets: Asset[])=> {..}</pre> Zie [Geselecteerd elementtype](#selected-asset-type) voor meer informatie. |
| *onClose* | Functie | Nee | | Wordt aangeroepen wanneer `Close` wordt in de modale weergave ingedrukt. Dit wordt alleen aangeroepen in `modal` in `rail` weergeven. |
| *onFilterSubmit* | Functie | Nee | | Wordt aangeroepen met filteritems wanneer de gebruiker andere filtercriteria wijzigt. |
| *selectionType* | string | Nee | enkel | Configuratie voor `single` of `multiple` selectie van elementen tegelijk. |
| *dragOptions.lijst van gewenste personen* | boolean | Nee | | De eigenschap wordt gebruikt om het slepen van elementen die niet kunnen worden geselecteerd toe te staan of te weigeren. |
| *aemTierType* | string | Nee | | Hiermee kunt u selecteren of u elementen uit de leveringslaag, de auteurslaag of beide wilt weergeven. <br><br> Syntaxis: `aemTierType:[0: "author" 1: "delivery"` <br><br> Als beide `["author","delivery"]` worden gebruikt, worden de opties voor zowel auteur als levering weergegeven door de repository switch. |
| *handleNavigateToAsset* | Functie | Nee | | Het is een callback functie om selectie van activa te behandelen. |
| *noWrap* | boolean | Nee | | De *noWrap* Deze eigenschap helpt de Asset Selector in het zijdeelvenster van het spoor weer te geven. Als dit bezit niet wordt vermeld, geeft het terug *Dialoogweergave* standaard. |
| *dialogSize* | overnemen op klein, middelgroot, groot, volledig scherm of volledig scherm | String | Optioneel | U kunt de lay-out bepalen door zijn grootte te specificeren gebruikend de bepaalde opties. |
| *colorScheme* | licht of donker | Nee | | Deze eigenschap wordt gebruikt om het thema van een toepassing Asset Selector in te stellen. U kunt kiezen tussen licht of donker thema. |
| *filterRepoList* | Functie | Nee |  | U kunt `filterRepoList` callback functie die de gegevensopslagplaats van de Experience Manager roept en een gefiltreerde lijst van bewaarplaatsen terugkeert. |

## Voorbeelden voor het gebruik van de eigenschappen van Asset Selector {#usage-examples}

U kunt de Asset Selector definiëren [eigenschappen](#asset-selector-properties) in de `index.html` bestand om de weergave van de Asset Selector in uw toepassing aan te passen.

### Voorbeeld 1: Kiezer voor bedrijfsmiddelen in spoorwegweergave

![spoorstaafvoorbeeld](assets/rail-view-example-vanilla.png)

Als de waarde van de AssetSelector `rail` is ingesteld op `false` of niet wordt vermeld in de eigenschappen, de vertoningen van de Selecteur van Activa in de Modale mening door gebrek. De `acvConfig` staat voor sommige diepgaande configuraties, zoals de Belemmering en de Daling toe. Bezoek [slepen en neerzetten in- of uitschakelen](#enable-disable-drag-and-drop) om inzicht te krijgen in het gebruik van `acvConfig` eigenschap.

<!--
### Example 2: Use selectedAssets property in addition to the path property

Use the `path` property to define the folder name that displays automatically when the Asset Selector is rendered. In addition, use the `selectedAssets` property to define the IDs for the assets that you need to select within the folder. Moreover, when you want to display assets that are pre-defined within the folder, you can use selectedAssets property.

   ![selected-assets-example](assets/selected-assets-example-vanilla.png)
-->

### Voorbeeld 2: popover-metagegevens

Gebruik verschillende eigenschappen om de metagegevens te definiëren van een element dat u wilt weergeven met een info-pictogram. De info popover verstrekt de inzameling van informatie over activa of de omslag met inbegrip van titel, afmetingen, datum van wijziging, plaats, en beschrijving van activa. In het onderstaande voorbeeld worden verschillende eigenschappen gebruikt om metagegevens van een element weer te geven, bijvoorbeeld `repo:path` eigenschap geeft de locatie van een element aan. <!--`repo` represents the repository from where the asset is showing, whereas, `path` represents the route from where the asset or folder is rendered.-->

![metadata-popover-example](assets/metadata-popover.png)

### Voorbeeld 3: Aangepaste filtereigenschap in de rasterweergave

Naast de beperkte zoekopdracht kunt u met de middelenkiezer verschillende kenmerken aanpassen om uw zoekopdracht te verfijnen van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] toepassing. Voeg de volgende code toe om aangepaste zoekfilters in uw toepassing toe te voegen. In het onderstaande voorbeeld wordt `Type Filter` zoek naar het type element tussen Afbeeldingen, Documenten of Video&#39;s of het filtertype dat u voor de zoekopdracht hebt toegevoegd.

![custom-filter-example-vanilla](assets/custom-filter-example-vanilla.png)

<!--

## Customization after integrating Asset Selector 

### Custom metadata

Assets display panel shows the out of the box metadata that can be displayed in the info of the asset. In addition to this, [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] application allows configuration of the asset selector by adding custom metadata that is shown in info panel of the asset.
-->

## Codefragmenten voor functionele setup{#code-snippets}

Definieer de vereisten in het dialoogvenster `index.html` bestand of een vergelijkbaar bestand in de implementatie van de toepassing om de verificatiegegevens te definiëren voor toegang tot het [!DNL Experience Manager Assets] opslagplaats. Als u klaar bent, kunt u naar wens codefragmenten toevoegen.

### Deelvenster Filter aanpassen {#customize-filter-panel}

U kunt het volgende codefragment toevoegen in `assetSelectorProps` -object om het filterdeelvenster aan te passen:

```
filterSchema: [
    {
    header: 'File Type',
    groupKey: 'TopGroup',
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    {
    label: 'Images',
    value: '<comma separated mimetypes, without space, that denote all images, for e.g., image/>',
    },
    {
    label: 'Videos',
    value: '<comma separated mimetypes, without space, that denote all videos for e.g., video/,model/vnd.mts,application/mxf>'
    }
    ]
    }
    ]
    },
    {
    fields: [
    {
    element: 'checkbox',
    name: 'type',
    options: [
    { label: 'JPG', value: 'image/jpeg' },
    { label: 'PNG', value: 'image/png' },
    { label: 'TIFF', value: 'image/tiff' },
    { label: 'GIF', value: 'image/gif' },
    { label: 'MP4', value: 'video/mp4' }
    ],
    columns: 3,
    },
    ],
    header: 'Mime Types',
    groupKey: 'MimeTypeGroup',
    }},
    {
    fields: [
    {
    element: 'checkbox',
    name: 'property=metadata.application.xcm:keywords.value',
    options: [
    { label: 'Fruits', value: 'fruits' },
    { label: 'Vegetables', value: 'vegetables'}
    ],
    columns: 3,
    },
    ],
    header: 'Food Category',
    groupKey: 'FoodCategoryGroup',
    }
],
```

### Informatie aanpassen in de modale weergave {#customize-info-in-modal-view}

U kunt de gedetailleerde weergave van een element aanpassen wanneer u op de knop ![info icon](assets/info-icon.svg) pictogram. Voer de onderstaande code uit:

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path'
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

### Slepen en neerzetten in- of uitschakelen {#enable-disable-drag-and-drop}

Voeg de volgende eigenschappen toe aan `assetSelectorProp` om slepen en neerzetten in te schakelen. Als u slepen en neerzetten wilt uitschakelen, vervangt u de opdracht `true` parameter with `false`.

```
rail: true,
acvConfig: {
dragOptions: {
allowList: {
'*': true,
},
},
selectionType: 'multiple'
}

// the drop handler to be implemented
function drop(e) {
e.preventDefault();
// following helps you get the selected assets – an array of objects.
const data = JSON.parse(e.dataTransfer.getData('collectionviewdata'));
}
```

### Selectie van activa {#selection-of-assets}

Het geselecteerde elementtype is een array met objecten die de elementgegevens bevatten wanneer u de `handleSelection`, `handleAssetSelection`, en `onDrop` functies.

Voer de volgende stappen uit om de selectie van één of meerdere activa te vormen:

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

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
        'https://ns.adobe.com/adobecloud/rel/rendition': Array<{
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

| Eigenschap | Type | Beschrijving |
|---|---|---|
| *repo:repositoryId* | string | Unieke id voor de gegevensopslagruimte waar het middel is opgeslagen. |
| *repo:id* | string | Unieke id voor het element. |
| *repo:assetClass* | string | De classificatie van het element (bijvoorbeeld afbeelding, video, document). |
| *repo:naam* | string | De naam van het element, inclusief de bestandsextensie. |
| *repo:grootte* | getal | De grootte van het element in bytes. |
| *repo:pad* | string | De locatie van het middel in de opslagplaats. |
| *repo:voorouders* | `Array<string>` | Een array van bovenliggende items voor het middel in de repository. |
| *repo:status* | string | Huidige status van het middel in de repository (bijvoorbeeld actief, verwijderd enzovoort). |
| *repo:createdBy* | string | De gebruiker of het systeem dat het element heeft gemaakt. |
| *repo:createDate* | string | De datum en tijd waarop het element is gemaakt. |
| *repo:modifiedBy* | string | De gebruiker of het systeem dat het element als laatste heeft gewijzigd. |
| *repo:modifyDate* | string | De datum en het tijdstip waarop het element voor het laatst is gewijzigd. |
| *dc:indeling* | string | De indeling van het element, zoals het bestandstype (bijvoorbeeld JPEG, PNG, enzovoort). |
| *tiff:imageWidth* | getal | De breedte van een element. |
| *tiff:imageLength* | getal | De hoogte van een element. |
| *computedMetadata* | `Record<string, any>` | Een object dat een emmertje vertegenwoordigt voor alle soorten metagegevens van het element (gegevensopslagruimte, toepassing of ingesloten metagegevens). |
| *_links* | `Record<string, any>` | Hypermediakoppelingen voor het bijbehorende element. Bevat koppelingen voor bronnen zoals metagegevens en uitvoeringen. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition>* | `Array<Object>` | Array met objecten die informatie bevatten over uitvoeringen van het element. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].href>* | string | De URI naar de vertoning. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].type>* | string | Het MIME-type van de vertoning. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].'repo:size>&#39;* | getal | De grootte van de vertoning in bytes. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].width>* | getal | De breedte van de vertoning. |
| *_links.<https://ns.adobe.com/adobecloud/rel/rendition[].height>* | getal | De hoogte van de vertoning. |

Voor een volledige lijst met eigenschappen en een gedetailleerd voorbeeld gaat u naar [Voorbeeld van code voor middelenkiezer](https://github.com/adobe/aem-assets-selectors-mfe-examples).

## Selectie van elementen afhandelen met behulp van objectschema {#handling-selection}

De `handleSelection` Deze eigenschap wordt gebruikt om een of meer selecties van Elementen in Elementenkiezer te verwerken. In het onderstaande voorbeeld wordt de gebruikssyntaxis van `handleSelection`.

![handgreep-selectie](assets/handling-selection.png)

## Selectie van elementen uitschakelen {#disable-selection}

Selectie uitschakelen wordt gebruikt om te verbergen of uit te schakelen dat de elementen of mappen kunnen worden geselecteerd. Het selectiekader van de kaart of het element dat u selecteert, wordt verborgen. Hierdoor wordt het selectievakje niet ingeschakeld. Als u deze functie wilt gebruiken, kunt u de positie opgeven van een element of map die u in een array wilt uitschakelen. Als u bijvoorbeeld de selectie van een map op de eerste positie wilt uitschakelen, kunt u de volgende code toevoegen:
`disableSelection: [0]:folder`

U kunt een lijst met MIME-typen (zoals afbeeldingen, mappen, bestanden of andere MIME-typen, bijvoorbeeld afbeeldingen/jpeg) opgeven die u wilt uitschakelen. De mime-typen die u declareert, worden toegewezen aan `data-card-type` en `data-card-mimetype` kenmerken van een element.

Daarnaast kunnen elementen met uitgeschakelde selectie versleepbaar zijn. Als u het slepen en neerzetten van een bepaald elementtype wilt uitschakelen, kunt u `dragOptions.allowList` eigenschap.

De syntaxis voor het uitschakelen van selectie is als volgt:

```
(args)=> {
    return(
        <ASDialogWrapper
            {...args}
            disableSelection={args.disableSelection}
            handleAssetSelection={action('handleAssetSelection')}
            handleSelection={action('handleSelection')}
            selectionType={args.selectionType}
        />
    );
}
```

>[!NOTE]
>
> In het geval van een element is het selectievakje Selecteren verborgen, terwijl in het geval van een map de map niet kan worden geselecteerd, maar de navigatie van de vermelde map nog steeds wordt weergegeven.

## Elementkiezer gebruiken {#using-asset-selector}

Zodra de Asset Selector is ingesteld en u bent geverifieerd dat u de Asset Selector kunt gebruiken met uw [!DNL Adobe Experience Manager] als [!DNL Cloud Service] kunt u elementen selecteren of verschillende andere bewerkingen uitvoeren om te zoeken naar uw elementen in de opslagplaats.

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

Met Asset Selector kunt u ook schakelen tussen opslagruimten voor middelenselectie. U kunt de opslagplaats van uw keus van drop-down selecteren beschikbaar in het linkerpaneel. De opslagruimteopties in de vervolgkeuzelijst zijn gebaseerd op de `repositoryId` in de `index.html` bestand. Het is gebaseerd op de omgeving van de geselecteerde IMS-org die wordt benaderd door de aangemelde gebruiker. Consumenten kunnen een voorkeur doorgeven `repositoryID` en in dat geval stopt de Asset Selector met het renderen van de repo-switch en geeft hij alleen activa van de gegeven repository weer.
<!--
It is based on the `imsOrg` that is provided in the application. If you want to see the list of repositories, then `repositoryId` is required to view those specific repositories in your application.
-->

### Middelenopslagplaats

Het is een verzameling mappen met elementen die u kunt gebruiken om bewerkingen uit te voeren.

### Buiten-de-box filters {#filters}

De Kiezer van activa verstrekt ook uit-van-de-doos filteropties om uw onderzoeksresultaten te verfijnen. De volgende filters zijn beschikbaar:

* `File type`: omvat map, bestand, afbeeldingen, documenten of video
* `MIME type`: omvat JPG, GIF, PPTX, PNG, MP4, DOCX, TIFF, PDF, XLSX
* `Image Size`: inclusief minimale/maximale breedte, minimale/maximale hoogte van afbeelding

  ![spoorstaafvoorbeeld](assets/filters-asset-selector.png)

### Aangepaste zoekopdracht

Met Asset Selector kunt u naast de zoekopdracht in volledige tekst ook elementen in bestanden zoeken met behulp van een aangepaste zoekopdracht. U kunt aangepaste zoekfilters gebruiken in zowel de modusweergave als de spoorweergave.

![aangepast zoeken](assets/custom-search1.png)

U kunt ook een standaardzoekfilter maken om de velden op te slaan waarnaar u vaak zoekt en deze later te gebruiken. Als u een aangepaste zoekopdracht naar uw elementen wilt maken, kunt u `filterSchema` eigenschap.

### Zoekbalk {#search-bar}

Met Asset Selector kunt u zoeken naar elementen in de geselecteerde opslagplaats in volledige tekst. Als u bijvoorbeeld het trefwoord typt `wave` in de zoekbalk, alle elementen met de opdracht `wave` trefwoord dat in een van de metagegevenseigenschappen wordt vermeld, wordt weergegeven.

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
*   **Configure** You can configure the files/folders that you want to show at the upfront. The assets that are chosen to view can be of any supported formats, for example, JPEG. It lets you control the display of various text or symbols as per your choice.
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
*   **Open in media library** Lets you open the asset in media library.
*   **Upload** Lets you upload an asset directly.
*   **Download** Downloads the asset in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
-->
<!--

### Status of an asset

Asset Selector lets you know the status of your uploaded assets. The status can be `Approved`, `Rejected`, or `Expired` of the asset. 
-->
<!--

### Localization

The integration of Asset Selector with [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] allows localized content appear in your application.
-->



<!--Best Practice-->
<!--
+++**Control default selection of the filter**
You can make the selection of filter default by implementing the following code snippet:

```
"defaultValue": [
    "image/*",
    "application/*"
],

{
    "label": "Documents",
    "value": "application/*"
}
```

+++
-->
