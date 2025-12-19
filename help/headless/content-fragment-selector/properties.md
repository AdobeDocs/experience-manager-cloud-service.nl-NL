---
title: Eigenschappen van Micro-Frontend-inhoudsfragmentkiezer voor Adobe Experience Manager as a Cloud Service
description: Eigenschappen om de Micro-Front Content Fragment Selector te configureren voor het zoeken, zoeken en ophalen van inhoudsfragmenten van uw toepassing.
role: Admin, User
exl-id: c81b5256-09fb-41ce-9581-f6d1ad316ca4
source-git-commit: 58995ae9c29d5a76b3f94de43f2bafecdaf7cf68
workflow-type: tm+mt
source-wordcount: '1073'
ht-degree: 0%

---

# Content Fragment Selector - Gerelateerde eigenschappen {#content-fragment-selector-related-properties}

Met de Micro-Frontend Content Fragment Selector kunt u in de opslagplaats door inhoudsfragmenten bladeren of deze doorzoeken en deze in uw toepassing gebruiken.

U kunt de volgende eigenschappen gebruiken om aan te passen hoe de Content Fragment Selector wordt weergegeven en hoe deze kan worden gebruikt:

## Eigenschappen van Content Fragment Selector {#content-fragment-selector-properties}

| Eigenschap | Type | Vereist | Standaard | Beschrijving |
|--- |--- |--- |--- |--- |
| `ref` | FragmentSelectorRef | | | Verwijzing naar de instantie `ContentFragmentSelector` , waarmee toegang wordt verleend tot beschikbare functionaliteit zoals `reload` . |
| `imsToken` | string | Nee | | IMS-token gebruikt voor verificatie. Indien niet opgegeven, wordt de IMS-aanmeldstroom gestart. |
| `repoId` | string | Nee | | Repository-id gebruikt voor de fragmentkiezer. Indien beschikbaar maakt de kiezer automatisch verbinding met de opgegeven opslagplaats en is het vervolgkeuzemenu van de opslagplaats verborgen. Indien niet opgegeven, kan de gebruiker een opslagplaats selecteren in de lijst met beschikbare opslagplaatsen waartoe hij toegang heeft. |
| `defaultRepoId` | string | Nee | | Opslagplaats-id die standaard wordt geselecteerd wanneer de gegevensopslagkiezer wordt weergegeven. Wordt alleen gebruikt als `repoId` niet is opgegeven. Als `repoId` is ingesteld, wordt de gegevensopslagkiezer verborgen en wordt deze waarde genegeerd. |
| `orgId` | string | Nee | | Organisatie-id gebruikt voor verificatie. Als deze optie niet wordt opgegeven, kan de gebruiker een opslagplaats selecteren van verschillende organisaties tot wie de gebruiker toegang heeft. Als de gebruiker geen toegang heeft tot een opslagplaats of organisatie, wordt de inhoud niet geladen. |
| `locale` | string | Nee | &quot;en-US&quot; | Landinstelling. |
| `env` | string | Nee | | Implementatieomgeving. Zie het type `Env` voor toegestane omgevingsnamen. |
| `filters` | FragmentFilter | Nee | `{ folder: "/content/dam" }` | Filters die moeten worden toegepast op de lijst met inhoudsfragmenten. Fragmenten onder `/content/dam` worden standaard weergegeven. |
| `isOpen` | boolean | Nee | `false` | Vlag om te controleren of de selecteur open of gesloten is. |
| `noWrap` | boolean | Nee | `false` | Hiermee wordt bepaald of de fragmentkiezer wordt weergegeven zonder een dialoogvenster voor terugloop. Wanneer ingesteld op `true` , wordt de fragmentkiezer rechtstreeks ingesloten in de bovenliggende container. Nuttig voor het integreren van de kiezer in aangepaste indelingen of workflows. |
| `onSelectionChange` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, huurderInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | Nee | | Callback-functie die wordt geactiveerd wanneer de selectie van inhoudsfragmenten verandert. Verstrekt de momenteel geselecteerde fragmenten, domeinnaam, huurdersinfo, bewaarplaats identiteitskaart, en leveringsbewaarplaatsen. |
| `onDismiss` | () => void | Nee | | Callback-functie die wordt geactiveerd wanneer de ontslagactie wordt uitgevoerd (bijvoorbeeld het sluiten van de kiezer). |
| `onSubmit` | ({ contentFragments: `ContentFragmentSelection`, domainName?: `string`, huurderInfo?: `string`, repoId?: `string`, deliveryRepos?: `DeliveryRepository[]` }) => void | Nee | | Callback functie teweeggebracht wanneer de gebruiker hun selectie bevestigt. Ontvangt de geselecteerde inhoudsfragmenten, de domeinnaam, huurdersinformatie, bewaarplaats-id, en leveringsbewaarplaatsen. |
| `theme` | &quot;licht&quot; of &quot;donker&quot; | Nee | | Thema voor de fragmentkiezer. Door gebrek, wordt het geplaatst aan het UnifiedShell omgevingsthema. |
| `selectionType` | &quot;single&quot; of &quot;multiple&quot; | Nee | `single` | U kunt selectietype gebruiken om de selectie voor de fragmentkiezer te beperken. |
| `dialogSize` | &quot;fullscreen&quot; of &quot;fullscreenTakOP&quot; | Nee | `fullscreen` | Optionele proxy om de grootte van het dialoogvenster te bepalen. |
| `runningInUnifiedShell` | boolean | Nee | | Of DestinationSelector onder UnifiedShell of standalone loopt. |
| `readonlyFilters` | ResourceReadonlyFiltersField [] | Nee | | Alleen-lezen filters die worden toegepast op de lijst met inhoudsfragmenten. Deze filters kunnen niet door de gebruiker worden verwijderd. |
| `selectedFragments` | ContentFragmentIdentifier [] | Nee | `[]` | Eerste selectie van inhoudsfragmenten die moet worden vooraf geselecteerd wanneer de kiezer wordt geopend. |
| `hipaaEnabled` | boolean | Nee | `false` | Geeft aan of HIPAA-compatibiliteit is ingeschakeld. |
| `inventoryView` | InventoryViewType | Nee | `table` | Standaardweergavetype inventarisatie dat in de kiezer moet worden gebruikt. |
| `inventoryViewToggleEnabled` | boolean | Nee | `false` | Hiermee wordt aangegeven of de voorraadweergave is ingeschakeld, zodat de gebruiker kan schakelen tussen tabel- en rasterweergave. |

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
