---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Gebruik de functie Asset Selector om de metagegevens en vertoningen van elementen in uw toepassing te zoeken, te zoeken en op te halen.
role: Admin, User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '1277'
ht-degree: 0%

---


# Eigenschappen van Asset Selector {#asset-selector-properties}

U kunt de eigenschappen van de Asset Selector gebruiken om de manier aan te passen waarop de Asset Selector wordt weergegeven. In de volgende tabel worden de eigenschappen weergegeven die u kunt gebruiken om de functie Asset Selector aan te passen en te gebruiken.

| Eigenschap | Type | Vereist | Standaard | Beschrijving |
|---|---|---|---|---|
| *spoorstaaf* | Boolean | Nee | Onwaar | Indien gemarkeerd `true` , wordt Asset Selector weergegeven in een linkerspoorweergave. Als deze is gemarkeerd met `false` , wordt de Asset Selector weergegeven in de modale weergave. |
| *imsOrg* | String | Ja | | Adobe Identity Management System (IMS) ID die tijdens de provisioning [!DNL Adobe Experience Manager] is toegewezen als een [!DNL Cloud Service] voor uw organisatie. De `imsOrg` -toets is vereist om te verifiëren of de organisatie waartoe u toegang hebt, onder Adobe IMS valt of niet. |
| *imsToken* | String | Nee | | IMS-token voor toonder die wordt gebruikt voor verificatie. `imsToken` is vereist als u een [!DNL Adobe] -toepassing voor de integratie gebruikt. |
| *apiKey* | String | Nee | | API-sleutel die wordt gebruikt voor toegang tot de AEM Discovery-service. `apiKey` is vereist als u een [!DNL Adobe] -toepassingsintegratie gebruikt. |
| *filterSchema* | Array | Nee | | Model dat wordt gebruikt om filtereigenschappen te vormen. Dit is handig wanneer u bepaalde filteropties in de Asset Selector wilt beperken. |
| *filterFormProps* | Object | Nee | | Geef de filtereigenschappen op die u nodig hebt om de zoekopdracht te verfijnen. Voor! Voorbeeld: MIME-type JPG, PNG, GIF. |
| *selectedAssets* | Array `<Object>` | Nee |                 | Geef de geselecteerde Assets op wanneer de Asset Selector wordt weergegeven. Een array van objecten is vereist die een id-eigenschap van de elementen bevat. `[{id: 'urn:234}, {id: 'urn:555'}]` Een element moet bijvoorbeeld beschikbaar zijn in de huidige map. Als u een andere map moet gebruiken, geeft u ook een waarde op voor de eigenschap `path` . |
| *acvConfig* | Object | Nee | | De bezit van de Mening van de Inzameling van activa dat voorwerp bevat dat douaneconfiguratie bevat om gebreken met voeten te treden. Deze eigenschap wordt ook gebruikt met de eigenschap `rail` om de weergave per spoor van de viewer voor elementen in te schakelen. |
| *i18nSymbols* | `Object<{ id?: string, defaultMessage?: string, description?: string}>` | Nee |                 | Als de OOTB-vertalingen onvoldoende zijn voor de behoeften van uw toepassing, kunt u een interface beschikbaar maken waarmee u uw eigen gelokaliseerde waarden kunt doorgeven via de `i18nSymbols` -proxy. Als u een waarde door deze interface doorgeeft, overschrijft u de standaardvertalingen die worden geleverd en gebruikt u in plaats daarvan uw eigen vertaling. Om de opheffing uit te voeren, moet u een geldig ](https://formatjs.io/docs/react-intl/api/#message-descriptor) voorwerp van de Beschrijver van het Bericht [ tot de sleutel van `i18nSymbols` overgaan die u wilt met voeten treden. |
| *intl* | Object | Nee | | Asset Selector biedt standaard OTB-vertalingen. U kunt de vertaaltaal selecteren door een geldige tekenreeks voor de landinstelling op te geven via de eigenschap `intl.locale` . Bijvoorbeeld: `intl={{ locale: "es-es" }}` </br></br> de gesteunde scènekoorden volgen [ ISO 639 - Codes ](https://www.iso.org/iso-639-language-codes.html) voor de vertegenwoordiging van namen van taalnormen. </br></br> Lijst met ondersteunde landinstellingen: Engels - &#39;en-us&#39; (standaard) Spaans - &#39;es-es&#39; Duits - &#39;de-de&#39; Frans - &#39;fr-fr&#39; Italiaans - &#39;it-it&#39; Japans - &#39;ja-jp&#39; Koreaans - &#39;ko-kr&#39; Portugees - &#39;pt-br&#39; Chinees (traditioneel) - &#39;zh-cn&#39; Chinees (Taiwan) - &#39;zh-tw&#39; |
| *repositoryId* | String | Nee | &#39;&#39; | Opslagplaats waar de inhoud wordt geladen door de Asset Selector. |
| *additionalAemSolutions* | `Array<string>` | Nee | [ ] | Hiermee kunt u een lijst met extra AEM opslagplaatsen toevoegen. Als deze eigenschap geen informatie bevat, worden alleen mediawisselaars of AEM Assets-opslagruimten in aanmerking genomen. |
| *hideTreeNav* | Boolean | Nee |  | Hiermee geeft u op of de zijbalk met boomnavigatie met elementen moet worden weergegeven of verborgen. Het wordt alleen in modale zin gebruikt en daarom heeft dit onroerend goed geen effect in de spoorwegen. |
| *onDrop* | Functie | Nee | | Met de eigenschap kan een element worden neergezet. |
| *dropOptions* | `{allowList?: Object}` | Nee | | Vormt dalingsopties gebruikend &quot;lijst van gewenste personen&quot;. |
| *colorScheme* | String | Nee | | Configureer het thema (`light` of `dark` ) voor de Asset Selector. |
| *Thema* | String | Nee | Standaard | Pas thema toe op de toepassing Asset Selector tussen `default` en `express` . Deze ondersteunt ook `@react-spectrum/theme-express` . |
| *handleSelection* | Functie | Nee | | Wordt aangeroepen met een array van elementen wanneer elementen worden geselecteerd en op de knop `Select` op het modale object wordt geklikt. Deze functie wordt alleen aangeroepen in de modale weergave. Gebruik voor de rasterweergave de functies `handleAssetSelection` of `onDrop` . Voorbeeld: <pre>handleSelection=(assets: Asset[])=> {..}</pre> Zie [ Geselecteerd Type van Activa ](#selected-asset-type) voor details. |
| *handleAssetSelection* | Functie | Nee | | Wordt aangeroepen met een array van items wanneer de elementen worden geselecteerd of niet geselecteerd. Dit is handig wanneer u naar elementen wilt luisteren terwijl de gebruiker deze selecteert. Voorbeeld: <pre>handleSelection=(assets: Asset[])=> {..}</pre> Zie [ Geselecteerd Type van Activa ](#selected-asset-type) voor details. |
| *onClose* | Functie | Nee | | Wordt aangeroepen wanneer op de knop `Close` in de modale weergave wordt gedrukt. Dit wordt alleen aangeroepen in de `modal` -weergave en wordt in `rail` -weergave genegeerd. |
| *onFilterSubmit* | Functie | Nee | | Wordt aangeroepen met filteritems wanneer de gebruiker andere filtercriteria wijzigt. |
| *selectionType* | String | Nee | Enkel | Configuratie voor `single` of `multiple` selectie van elementen tegelijk. |
| *dragOptions.lijst van gewenste personen* | boolean | Nee | | De eigenschap wordt gebruikt om het slepen van elementen die niet kunnen worden geselecteerd toe te staan of te weigeren. |
| *nameTierType* | String | Nee |  | Hiermee kunt u selecteren of u elementen uit de leveringslaag, de auteurslaag of beide wilt weergeven. <br><br> Syntaxis: `aemTierType:[0]: "author" 1: "delivery"` <br><br> Als bijvoorbeeld beide `["author","delivery"]` worden gebruikt, worden opties voor zowel auteur als levering weergegeven door de repository switch. |
| *handleNavigateToAsset* | Functie | Nee | | Het is een callback functie om selectie van activa te behandelen. |
| *noWrap* | Boolean | Nee | | Het *noWrap* bezit helpt teruggevend de Selecteur van Activa in het paneel van de zijspoorstaaf. Als dit bezit niet wordt vermeld, geeft het de *mening van de Dialoog* door gebrek terug. |
| *dialogSize* | overnemen op klein, middelgroot, groot, volledig scherm of volledig scherm | String | Optioneel | U kunt de lay-out bepalen door zijn grootte te specificeren gebruikend de bepaalde opties. |
| *colorScheme* | Licht of donker | Nee | | Deze eigenschap wordt gebruikt om het thema van een toepassing Asset Selector in te stellen. U kunt kiezen tussen licht of donker thema. |
| *filterRepoList* | Functie | Nee |  | U kunt de callback-functie `filterRepoList` gebruiken die de gegevensopslagruimte van de Experience Manager aanroept en een gefilterde lijst met opslagruimten retourneert. |
| *endOptions* | Functie | | | U kunt tussen de volgende twee eigenschappen gebruiken: **getExpiryStatus** die status van een verlopen activa verstrekt. De functie retourneert `EXPIRED` , `EXPIRING_SOON` of `NOT_EXPIRED` op basis van de vervaldatum van een element dat u opgeeft. Zie [ verlopen activa ](#customize-expired-assets) aanpassen. Bovendien, kunt u **allowSelectionAndDrag** gebruiken waarin de waarde van de functie of `true` of `false` kan zijn. Wanneer de waarde is ingesteld op `false` , kan het verlopen element niet worden geselecteerd of gesleept op het canvas. |
| *showToast* | | Nee | | Hierdoor kan de Asset Selector een aangepast pop-upbericht weergeven voor het verlopen element. |
| *metadataSchema* | Array | Nee | | Voeg een array van velden toe die u opgeeft om metagegevens van de gebruiker te verzamelen. Met deze eigenschap kunt u ook verborgen metagegevens gebruiken die automatisch aan een element worden toegewezen, maar die niet zichtbaar zijn voor de gebruiker. |
| *onMetadataFormChange* | Callback-functie | Nee | | Deze bestaat uit `property` en `value` . `Property` evenaart *mapToProperty* van het gebied dat van *wordt overgegaan metadataSchema* de waarvan waarde wordt bijgewerkt. Terwijl, `value` evenaart de nieuwe waarde als input wordt verstrekt. |
| *targetUploadPath* | String |  | `"/content/dam"` | Het doeluploadpad voor de bestanden die standaard de hoofdmap van de gegevensopslagruimte vormen. |
| *hideUploadButton* | Boolean | | Onwaar | Hiermee zorgt u ervoor dat de interne knop voor uploaden verborgen moet zijn of niet. |
| *onUploadStart* | Functie | Nee |  | Het is een callback functie die wordt gebruikt om de upload bron onder Dropbox, OneDrive, of lokaal over te gaan. De syntaxis is `(uploadInfo: UploadInfo) => void` |
| *importSettings* | Functie | | | Hiermee wordt ondersteuning ingeschakeld voor het importeren van elementen van derden. `sourceTypes` gebruikt een array met de importbronnen die u wilt inschakelen. De ondersteunde bronnen zijn Onedrive en Dropbox. De syntaxis is `{ sourceTypes?: ImportSourceType[]; apiKey?: string; }` |
| *onUploadComplete* | Functie | Nee | | Dit is een callback-functie die wordt gebruikt om de status voor het uploaden van een bestand door te geven onder geslaagd, mislukt of gedupliceerd. De syntaxis is `(uploadStats: UploadStats) => void` |
| *onFilesChange* | Functie | Nee | | Het is een callback functie die wordt gebruikt om het gedrag van te tonen upload wanneer een dossier wordt veranderd. De nieuwe array met bestanden die moeten worden geüpload en het brontype van de upload worden doorgegeven. Source-type kan null zijn in het geval van een fout. De syntaxis is `(newFiles: File[], uploadType: UploadType) => void` |
| *uploadingPlaceholder* | String | | | Het is een plaatsaanduidingsafbeelding die het metagegevensformulier vervangt wanneer het uploaden van het element wordt gestart. De syntaxis is `{ href: string; alt: string; } ` |
| *uploadConfig* | Object | | | Het is een object dat een aangepaste configuratie voor het uploaden bevat. |
| *featureSet* | Array | String | | De eigenschap `featureSet:[ ]` wordt gebruikt om een bepaalde functionaliteit in of uit te schakelen in de toepassing Asset Selector. Als u de component of een functie wilt inschakelen, kunt u een tekenreekswaarde in de array doorgeven of de array leeg laten om die component uit te schakelen. Gebruik bijvoorbeeld de syntaxis `featureSet:[0:"upload"]` om de uploadfunctionaliteit in te schakelen in de Asset Selector. |

<!--
| *rootPath* | String | No | /content/dam/ | Folder path from which Asset Selector displays your assets. `rootPath` can also be used in the form of encapsulation. For example, given the following path, `/content/dam/marketing/subfolder/`, Asset Selector does not allow you to traverse through any parent folder, but only displays the children folders. |
| *path* | String | No | | Path that is used to navigate to a specific directory of assets when the Asset Selector is rendered. |
| *expirationDate* | Function | No | | This function is used to set the usability period of an asset. |
| *disableDefaultBehaviour* | Boolean | No | False | It is a function that is used to enable or disable the selection of an expired asset. You can customize the default behavior of an asset that is set to expire. See [customize expired assets](#customize-expired-assets). |
-->



