---
title: Eigenschappen van Micro-Frontend-inhoudsfragmentkiezer voor Adobe Experience Manager as a Cloud Service
description: Eigenschappen om de Micro-Front Content Fragment Selector te configureren voor het zoeken, zoeken en ophalen van inhoudsfragmenten van uw toepassing.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: a3d8961b6006903c42d983c82debb63ce8abe9ad
workflow-type: tm+mt
source-wordcount: '894'
ht-degree: 0%

---

# Content Fragment Selector - Gerelateerde eigenschappen {#content-fragment-selector-related-properties}

Met de Micro-Frontend Content Fragment Selector kunt u in de opslagplaats door inhoudsfragmenten bladeren of deze doorzoeken en deze in uw toepassing gebruiken.

U kunt de volgende eigenschappen gebruiken om aan te passen hoe de Content Fragment Selector wordt weergegeven en hoe deze kan worden gebruikt:

## Eigenschappen van Content Fragment Selector {#content-fragment-selector-properties}

| Eigenschap | Type | Vereist | Standaard | Beschrijving |
|--- |--- |--- |--- |--- |
| `imsToken` | string | Nee | | IMS-token gebruikt voor verificatie. |
| `repoId` | string | Nee | | ID opslagplaats gebruikt voor verificatie. |
| `orgId` | string | Ja | | Organisatie-id gebruikt voor verificatie. |
| `locale` | string | Nee | | Lokale gegevens. |
| `env` | Omgeving | Nee | | Implementatieomgeving van Content Fragment Selector. |
| `filters` | FragmentFilter | Nee | | Filters die moeten worden toegepast voor de lijst met inhoudsfragmenten. Fragmenten onder `/content/dam` worden standaard weergegeven. Standaardwaarde: `{ folder: "/content/dam" }` |
| `isOpen` | boolean | Ja | `false` | Markering om het openen of sluiten van de kiezer te activeren. |
| `onDismiss` | () => void | Ja | | Functie die moet worden geroepen wanneer **Ontkenning** wordt geselecteerd. |
| `onSubmit` | ({ contentFragments: `{id: string, path: string}[]` , domainNames: `string[]` }) => void | Ja | | Functie die moet worden geroepen wanneer **Uitgezocht** na het selecteren van één of meerdere Fragments van de Inhoud wordt gebruikt. <br><br> de functie zal ontvangen:<br><ul><li> de geselecteerde inhoudsfragmenten met `id` - en `path` -velden</li><li>en domeinnamen die gerelateerd zijn aan de programma-id van de repository en de omgeving-id, die de status `ready` en `tier` Publish hebben</li></ul><br> als er geen domeinnamen zijn zal het de Publish instantie als reserve domein gebruiken. |
| `theme` | &quot;licht&quot; of &quot;donker&quot; | Nee | | Thema van de kiezer voor inhoudsfragmenten. Het standaardthema wordt geplaatst aan het thema van het milieu UnifiedShell. |
| `selectionType` | &quot;single&quot; of &quot;multiple&quot; | Nee | `single` | Selectietype dat kan worden gebruikt om de selectie voor de FragmentSelector te beperken. |
| `dialogSize` | &quot;fullscreen&quot; of &quot;fullscreenTakOP&quot; | Nee | `fullscreen` | Optionele eigenschap om de grootte van het dialoogvenster te bepalen. |
| `waitForImsToken` | boolean | Nee | `false` | Geeft aan of de Content Fragment Selector wordt gerenderd in de context van SUSI flow en moet wachten tot `imsToken` gereed is. |
| `imsAuthInfo` | ImsAuthInfo | Nee | | Object met de IMS-verificatiegegevens van de aangemelde gebruiker. |
| `runningInUnifiedShell` | boolean | Nee | | Wijst erop of de Selector van het Fragment van de Inhoud onder UnifiedShell of standalone loopt. |
| `readonlyFilters` | ResourceReadFiltersField | Nee | | Alleen-lezen filters die kunnen worden toegepast op de lijst met inhoud en die niet kunnen worden verwijderd. |

## Eigenschappen van ImsAuthProps {#imsauthprops-properties}

Met de eigenschappen `ImsAuthProps` worden de verificatiegegevens en de stroom gedefinieerd die de kiezer voor het inhoudsfragment gebruikt om een `imsToken` -element te verkrijgen. Door deze eigenschappen te plaatsen, kunt u controleren hoe de authentificatiestroom zich zou moeten gedragen en luisteraars voor diverse authentificatiegebeurtenissen registreren.

| Eigenschapnaam | Beschrijving |
|--- |--- |
| `imsClientId` | Een tekenreekswaarde die de IMS client-id vertegenwoordigt die voor verificatiedoeleinden wordt gebruikt. Deze waarde wordt geleverd door Adobe en is specifiek voor uw Adobe AEM CS-organisatie. |
| `imsScope` | Beschrijft het werkingsgebied dat in authentificatie wordt gebruikt. Het werkingsgebied bepaalt het niveau van toegang dat de toepassing aan uw organisatiemiddelen heeft. Meerdere bereiken kunnen worden gescheiden door komma&#39;s. |
| `redirectUrl` | Geeft de URL aan waar de gebruiker na verificatie opnieuw wordt omgeleid. Deze waarde wordt doorgaans ingesteld op de huidige URL van de toepassing. Als een `redirectUrl` niet wordt opgegeven, gebruikt `ImsAuthService` de redirectUrl die wordt gebruikt om de `imsClientId` te registreren |
| `modalMode` | Een Booleaanse waarde die aangeeft of de verificatiestroom al dan niet moet worden weergegeven in een modaal (pop-upmenu). Indien ingesteld op `true` , wordt de verificatiestroom weergegeven in een pop-up. Indien ingesteld op `false` , wordt de verificatiestroom weergegeven in een volledige pagina die opnieuw wordt geladen.<br>**Nota:** voor betere UX, kunt u deze waarde dynamisch controleren als de gebruiker browser pop-up gehandicapten heeft. |
| `onImsServiceInitialized` | Een callback-functie die wordt aangeroepen wanneer de Adobe IMS-verificatieservice wordt geïnitialiseerd. Deze functie heeft één parameter, `service` , die een object is dat de Adobe IMS-service vertegenwoordigt. Zie [`ImsAuthService`](#imsauthservice-ims-auth-service) voor meer informatie. |
| `onAccessTokenReceived` | Een callback-functie die wordt aangeroepen wanneer een `imsToken` wordt ontvangen van de Adobe IMS-verificatieservice. Deze functie heeft één parameter, `imsToken`, die een tekenreeks is die het toegangstoken vertegenwoordigt. |
| `onAccessTokenExpired` | Een callback functie die wordt geroepen wanneer een toegangstoken is verlopen. Deze functie wordt typisch gebruikt om een nieuwe authentificatiestroom teweeg te brengen om een nieuw toegangstoken te verkrijgen. |
| `onErrorReceived` | Een callback functie die wordt geroepen wanneer een fout tijdens authentificatie voorkomt. Deze functie heeft twee parameters: het fouttype en het foutbericht. Het fouttype is een tekenreeks die het type fout vertegenwoordigt en het foutbericht is een tekenreeks die het foutbericht vertegenwoordigt. |

## Eigenschappen van ImsAuthService {#imsauthservice-properties}

De `ImsAuthService` -klasse handelt de verificatiestroom voor de Content Fragment Selector af. Het is verantwoordelijk voor het verkrijgen van een `imsToken` van de Adobe IMS-verificatieservice. `imsToken` wordt gebruikt om de gebruiker te verifiëren en toegang tot de Adobe Experience Manager (AEM) CS-opslagplaats te verlenen. ImsAuthService gebruikt de `ImsAuthProps` eigenschappen om de authentificatiestroom te controleren en luisteraars voor diverse authentificatiegebeurtenissen te registreren. U kunt de handige `registerContentFragmentSelectorAuthService` functie gebruiken om de `ImsAuthService` -instantie te registreren bij de Content Fragment Selector. De volgende functies zijn beschikbaar voor de `ImsAuthService` -klasse. Als u echter de functie `registerContentFragmentSelectorAuthService` gebruikt, hoeft u deze functies niet rechtstreeks aan te roepen.

| Functienaam | Beschrijving |
|--- |--- |
| `isSignedInUser` | Bepaalt of de gebruiker momenteel binnen aan de dienst wordt ondertekend en een booleaanse waarde dienovereenkomstig terugkeert. |
| `getImsToken` | Wint de authentificatie `imsToken` voor de momenteel ondertekende gebruiker terug, die kan worden gebruikt om verzoeken aan andere diensten zoals het produceren van activa _vertoning voor authentiek te verklaren._ |
| `signIn` | Hiermee wordt het aanmeldingsproces voor de gebruiker gestart. Deze functie gebruikt `ImsAuthProps` om verificatie weer te geven in een pop-up of een volledige pagina die opnieuw wordt geladen. |
| `signOut` | Signs the user out of the service, invalidating their authentication token and require them to sign in again to access protected resources. Als u deze functie aanroept, wordt de huidige pagina opnieuw geladen. |
| `refreshToken` | Verfrist het authentificatietoken voor de momenteel ondertekende gebruiker, verhinderend het en ononderbroken toegang tot beschermde middelen te verzekeren. Keert een nieuw authentificatietoken terug dat voor verdere verzoeken kan worden gebruikt. |
