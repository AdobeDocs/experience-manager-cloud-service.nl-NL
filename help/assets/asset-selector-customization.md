---
title: Toepassing Asset Selector aanpassen
description: Gebruik functies om de kiezer van het element in uw toepassing aan te passen.
role: Admin, User
exl-id: 0fd0a9f7-8c7a-4c21-9578-7c49409df609
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 0%

---

# Aanpassingen voor Asset Selector {#asset-selector-customization}

Met Asset Selector kunt u verschillende componenten aanpassen op basis van voorkeuren, vereisten of functionele behoeften. U kunt de volgende componenten aanpassen [&#x200B; Micro-Frontend de Selector van Activa &#x200B;](#overview-asset-selector.md):

* [Deelvenster Filter aanpassen](#customize-filter-panel)
* [Informatie aanpassen in de modale weergave](#customize-info-in-modal-view)
* [Slepen en neerzetten in- of uitschakelen](#enable-disable-drag-and-drop)
* [Selectie van Assets](#selection-of-assets)
* [Verlopen elementen aanpassen](#customize-expired-assets)
* [Contextafhankelijke aanroepfilter](#contextual-invocation-filter)
* [dragOptions, eigenschap](#drag-options-property)

U moet de eerste vereisten in het {**dossier 0} index.html of een gelijkaardig dossier binnen uw toepassingsimplementatie bepalen om de authentificatiedetails te bepalen om tot de** bewaarplaats toegang te hebben. [!DNL Experience Manager Assets] Als u klaar bent, kunt u naar wens codefragmenten toevoegen.

## Deelvenster Filter aanpassen {#customize-filter-panel}

U kunt het volgende codefragment toevoegen in het object `assetSelectorProps` om het filterdeelvenster aan te passen:

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
    },
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

## Informatie aanpassen in de modale weergave {#customize-info-in-modal-view}

U kunt de detailmening van activa aanpassen wanneer u het ![&#x200B; infopictogram &#x200B;](assets/info-icon.svg) pictogram klikt. Voer de onderstaande code uit:

```
// Create an object infoPopoverMap and set the property `infoPopoverMap` with it in assetSelectorProps
const infoPopoverMap = (map) => {
// for example, to skip `path` from the info popover view
let defaultPopoverData = PureJSSelectors.getDefaultInfoPopoverData(map);
return defaultPopoverData.filter((i) => i.label !== 'Path')
};
assetSelectorProps.infoPopoverMap = infoPopoverMap;
```

## Slepen en neerzetten in- of uitschakelen {#enable-disable-drag-and-drop}

Voeg de volgende eigenschappen toe aan `assetSelectorProp` om slepen en neerzetten in te schakelen. Als u slepen en neerzetten wilt uitschakelen, vervangt u de parameter `true` door `false` .

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

## Selectie van Assets {#selection-of-assets}

Het geselecteerde elementtype is een array met objecten die de elementinformatie bevat wanneer de functies `handleSelection` , `handleAssetSelection` en `onDrop` worden gebruikt.

Voer de volgende stappen uit om de selectie van één of meerdere activa te vormen:

```
acvConfig: {
selectionType: 'multiple' // 'single' for single selection
}
// the `handleSelection` callback, always gets you the array of selected assets
```

**Syntaxis van het Schema**

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
| *repo:name* | string | De naam van het element, inclusief de bestandsextensie. |
| *repo:size* | getal | De grootte van het element in bytes. |
| *repo:path* | string | De locatie van het middel in de opslagplaats. |
| *repo:ancestors* | `Array<string>` | Een array van bovenliggende items voor het middel in de repository. |
| *repo:state* | string | Huidige status van het middel in de repository (bijvoorbeeld actief, verwijderd enzovoort). |
| *repo:createdBy* | string | De gebruiker of het systeem dat het element heeft gemaakt. |
| *repo:createDate* | string | De datum en tijd waarop het element is gemaakt. |
| *repo:modifiedBy* | string | De gebruiker of het systeem dat het element als laatste heeft gewijzigd. |
| *repo:modifyDate* | string | De datum en het tijdstip waarop het element voor het laatst is gewijzigd. |
| *dc:format* | string | De indeling van het element, zoals het bestandstype (bijvoorbeeld JPEG, PNG, enzovoort). |
| *tiff:imageWidth* | getal | De breedte van een element. |
| *tiff:imageLength* | getal | De hoogte van een element. |
| *computedMetadata* | `Record<string, any>` | Een object dat een emmertje vertegenwoordigt voor alle soorten metagegevens van het element (gegevensopslagruimte, toepassing of ingesloten metagegevens). |
| *_links* | `Record<string, any>` | Hypermediakoppelingen voor het bijbehorende element. Bevat koppelingen voor bronnen zoals metagegevens en uitvoeringen. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition>`* | `Array<Object>` | Array met objecten die informatie bevatten over uitvoeringen van het element. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].href>`* | string | De URI naar de vertoning. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].type>`* | string | Het MIME-type van de vertoning. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].repo:size>`* | getal | De grootte van de vertoning in bytes. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].width>`* | getal | De breedte van de vertoning. |
| *`_links.<https://ns.adobe.com/adobecloud/rel/rendition[].height>`* | getal | De hoogte van de vertoning. |

### Selectie van Assets afhandelen met behulp van objectschema {#handling-selection}

De eigenschap `handleSelection` wordt gebruikt om één of meerdere selecties van Assets in Assets Selector af te handelen. In het onderstaande voorbeeld wordt de gebruikssyntaxis van `handleSelection` weergegeven.

![&#x200B; handvat-selectie &#x200B;](assets/handling-selection.png)

### Selectie van Assets uitschakelen {#disable-selection}

Selectie uitschakelen wordt gebruikt om te verbergen of uit te schakelen dat de elementen of mappen kunnen worden geselecteerd. Het selectiekader van de kaart of het element dat u selecteert, wordt verborgen. Hierdoor wordt het selectievakje niet ingeschakeld. Als u deze functie wilt gebruiken, kunt u de positie opgeven van een element of map die u in een array wilt uitschakelen. Als u bijvoorbeeld de selectie van een map op de eerste positie wilt uitschakelen, kunt u de volgende code toevoegen:
`disableSelection: [0]:folder`

U kunt een lijst met MIME-typen (zoals afbeeldingen, mappen, bestanden of andere MIME-typen, bijvoorbeeld afbeeldingen/jpeg) opgeven die u wilt uitschakelen. De mime-typen die u declareert, worden toegewezen aan `data-card-type` - en `data-card-mimetype` -kenmerken van een element.

Bovendien kan Assets met uitgeschakelde selectie worden versleept. Als u het slepen en neerzetten van een bepaald elementtype wilt uitschakelen, kunt u de eigenschap `dragOptions.allowList` gebruiken.

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

<!--For a complete list of properties and detailed example, visit [Asset Selector Code Example](https://github.com/adobe/aem-assets-selectors-mfe-examples).-->

## Verlopen elementen aanpassen {#customize-expired-assets}

Met Asset Selector kunt u het gebruik van een verlopen element beheren. U kunt het verlopen activa met een **aanpassen die spoedig** badge vervalt die u kan helpen van tevoren over de activa weten die binnen 30 dagen van de huidige datum zullen verlopen. Bovendien kan dit worden aangepast aan de vereisten. U kunt ook de selectie van een verlopen element op het canvas toestaan of andersom. De aanpassing van een verlopen element kan op verschillende manieren worden gedaan gebruikend sommige codefragmenten:

<!--{
    getExpiryStatus: function, // to control Expired/Expiring soon badges of the asset
    allowSelectionAndDrag: boolean, // set true to allow the selection of expired assets on canvas, set false, otherwise.
}-->

```
expiryOptions: {
    getExpiryStatus: getExpiryStatus;
}
```

### Selectie van een verlopen element {#selection-of-expired-asset}

U kunt het gebruik van een verlopen element aanpassen om het selecteerbaar of niet-selecteerbaar te maken. U kunt aanpassen of u het slepen en neerzetten van een verlopen element op het canvas Asset Selector wilt toestaan of niet. Hiervoor gebruikt u de volgende parameters om een element op het canvas niet-selecteerbaar te maken:

```
expiryOptions:{
    allowSelectionAndDrop: false;
}
```

<!--
Additionally, To do this, navigate to **[!UICONTROL Disable default expiry behavior]** under the [!UICONTROL Controls] tab and set the boolean value to `true` or `false` as per the requirement. If `true` is selected, you can see the select box over the expired asset, otherwise it remains unselected. You can hover to the info icon of an asset to know the details of an expired asset. 

![Disable default expiry behavior](assets/disable-default-expiry-behavior.png)-->

### De duur van een verlopen element instellen {#set-duration-of-expired-asset}

Het volgende codefragment helpt u **het Verlopen Soon** badge voor de activa plaatsen die binnen volgende vijf dagen verlopen: <!--The `expirationDate` property is used to set the expiration duration of an asset. Refer to the code snippet below:-->

```
/**
  const getExpiryStatus = async (asset) => {
  if (!asset.expirationDate) {
    return null;
  }
  const currentDate = new Date();
  const millisecondsInDay = 1000 * 60 * 60 * 24;
  const fiveDaysFromNow = new Date(value: currentDate.getTime() + 5 * millisecondsInDay);
  const expirationDate = new Date(asset.expirationDate);
  if (expirationDate.getTime() < currentDate.getTime()) {
    return 'EXPIRED';
  } else if (expirationDate.getTime() < fiveDaysFromNow.getTime()) {
    return 'EXPIRING_SOON';
  } else {
    return 'NOT_EXPIRED';
  }
};
```

<!--In the above code snippet, the `getExpiryStatus` function is used to show the **Expiring soon** badge that have expiration date stored in `customExpirationDate`. Additionally, it sets the expiration date of an asset to five days from the current date. The `millisecondsInDay` helps you set expiry of an asset by specifying the time range in milliseconds. You can replace milliseconds with hours directly or customize function as per the requirement. Whereas, the `getTime()` function returns the number of milliseconds for the mentioned date. See [properties](#asset-selector-properties) to know about `expirationDate` property.-->

Raadpleeg het volgende voorbeeld om te begrijpen hoe de eigenschap werkt om de huidige datum en tijd op te halen:

```
const currentData = new Date();
currentData.getTime(),
```

keert `1718779013959` terug die volgens datumformaat 2024-06-19T06 :36: 53.959Z is.

### Het pop-upbericht van een verlopen element aanpassen {#customize-toast-message}

De eigenschap `showToast` wordt gebruikt om het pop-upbericht aan te passen dat u op een verlopen element wilt weergeven.

Syntaxis:

```
{
    type: 'ERROR', 'NEUTRAL', 'INFO', 'SUCCESS',
    message: '<message to be shown>',
    timeout: optional,
}
```

De standaardtime-out is 500 milliseconden. U kunt deze desgewenst wijzigen. Als u de waarde `timeout: 0` doorgeeft, blijft de toast geopend totdat u op de kruisknop klikt.

Hieronder ziet u een voorbeeld voor het weergeven van een pop-upbericht als u een map niet wilt selecteren en een bijbehorend bericht wilt weergeven:

```
const showToast = {
    type: 'ERROR',
    message: 'Folder cannot be selected',
    timeout: 5000,
}
```

Gebruik het volgende codefragment om pop-upbericht voor het gebruik van een verlopen element weer te geven:

```
(args) => {
    const [selectedAssets, setSelectedAssets] = useState([]);
    const [showToast, setShowToast] = React.useState(false);
    const handleAssetSelection = (assets) => {
        let directorySelectedFlag = false;
        const temp = assets.filter((asset) => {
            if (asset['repo:assetClass'] === 'directory') {
                directorySelectedFlag = true;
                setShowToast(true);
            }
            return !(asset['repo:assetClass'] === 'directory');
        });
        if (!directorySelectedFlag) {
            setShowToast(false);
        }
        setSelectedAssets(temp);
    };
    return (
        <ASDialogWrapper
            {...args}
            showToast={showToast ? args.showToast : null}
            selectedAssets={selectedAssets}
            handleAssetSelection={handleAssetSelection}
        />
    );
}
```

## Contextafhankelijke aanroepfilter{#contextual-invocation-filter}

Met Asset Selector kunt u een tagkiezerfilter toevoegen. De tag wordt ondersteund door een taggroep waarin alle relevante tags worden gecombineerd met een bepaalde taggroep. Bovendien kunt u extra tags selecteren die overeenkomen met het element dat u zoekt. Bovendien kunt u de standaardtaggroepen onder het contextafhankelijke aanroepingsfilter die meestal door u worden gebruikt, ook instellen zodat ze onderweg toegankelijk zijn voor u.

>[!NOTE]
>
> * U moet een codefragment voor contextafhankelijke aanroepcode toevoegen om een tagfilter in de zoekopdracht in te schakelen.
> * Het is verplicht de eigenschap name te gebruiken die overeenkomt met het type taggroep `(property=xcm:keywords.id=)` .

Syntaxis:

```
const filterSchema=useMemo(() => {
    return: [
        {
            element: 'taggroup',
            name: 'property=xcm:keywords.id='
        },
    ];
}, []);
```

Als u labelgroepen wilt toevoegen aan het deelvenster Filters, is het verplicht ten minste één taggroep als standaardgroep toe te voegen. Bovendien kunt u met het codefragment eronder de standaardtags toevoegen die vooraf zijn geselecteerd in de taggroep.

```
export const WithAssetTags = (props) = {
const [selectedTags, setSelectedTags] = useState (
new Set(['orientation', 'color', 'facebook', 'experience-fragments:', 'dam', 'monochrome'])
const handleSelectTags = (selected) => {
setSelectedTags (new Set (selected)) ;
};
const filterSchema = useMemo ((); => {
    return {
        schema: [
            ｛
                fields: [
                    {
                    element: 'checkbox', 
                    name: 'property=xcm:keywords=', 
                    defaultValue: Array. from(selectedTags), 
                    options: assetTags, 
                    orientation: 'vertical',
                    },
                ],
    header: 'Asset Tags', 
    groupkey: 'AssetTagsGroup',
        ],
    },
｝；
}, [selectedTags]);
```

![&#x200B; filter van de markeringsgroep &#x200B;](assets/tag-group.gif)

## Uploaden in Asset Selector {#upload-in-asset-selector}

U kunt bestanden of mappen vanuit uw lokale bestandssysteem uploaden naar Asset Selector. Als u bestanden wilt uploaden met het lokale bestandssysteem, moet u doorgaans een upload-functie gebruiken die wordt geleverd door een Asset Selector-microfront-end toepassing. De `upload` verschillende codefragmenten die vereist zijn om het uploaden in een elementenkiezer aan te roepen, zijn:

* [Eenvoudig formuliercodefragment uploaden](#basic-upload)
* [Configuratie uploaden](#upload-config)
* [Uploaden met metagegevens](#upload-with-metadata)
* [Aangepaste upload](#customized-upload)
* [Uploaden met bronnen van derden](#upload-using-third-party-source)

### Basisupload formulier {#basic-upload}

```
import { AllInOneUpload } from '@assets/upload';
import { TextField, ContextualHelp } from '@adobe/react-spectrum';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

export const UploadExample = () => {
    return (
        <>
            <TextField
                marginStart="size-200"
                width="size-6000"
                isDisabled={true}
                label="Target Upload Path"
                value={targetUploadPath}
                contextualHelp={
                    <ContextualHelp>
                        <Content>Use Storybook Controls panel to change the default upload location</Content>
                    </ContextualHelp>
                }
            />
            <AllInOneUpload
                repositoryId={repoId}
                apiToken={apiToken}
                targetUploadPath={targetUploadPath}
            />
        <>
    )
}
```

### Configuratie uploaden {#upload-config}

```
uploadConfig: {
        onUploadStart: action('onUploadStart'),
        onUploadComplete: action('onUploadComplete'),
        metadataSchema: [
            {
                mapToProperty: 'dam:assetStatus',
                value: 'approved',
                element: 'hidden',
            },
        ],
        ... more properties
     }, 
```

*Meer eigenschappen zijn `metadataSchema` , `onMetadataFormChange` , `targetUploadPath` , `hideUploadButton` , `onUploadStart` , `importSettings` `onUploadComplete` , `onFilesChange` ,`uploadingPlaceholder`* . Zie [&#x200B; de eigenschappen van de Selecteur van Activa &#x200B;](#asset-selector-properties.md) voor meer informatie.

### Uploaden met metagegevens {#upload-with-metadata}

```
import { AllInOneUpload } from '@assets/upload';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

/**
 * see https://git.corp.adobe.com/CQ/assets-upload/blob/main/packages/@assets/upload/stories/data/SampleMetadataSchemas.ts
 * for full schema shape used in rendered example below
 */
const metadataSchema = [
    {
        mapToProperty: 'gmo:lineofBusiness',
        label: 'Line of Business',
        placeholder: 'Select one',
        required: true,
        element: 'dropdown',
        dropdownOptions: [
            {
                id: 'corporate',
                name: 'Corporate',
            },
            {
                id: 'digital-media-dme',
                name: 'Digital Media (DMe)',
            },
            {
                id: 'digital-experience-dx',
                name: 'Digital Experience (DX)',
            },
            {
                id: 'business-solutions',
                name: 'Business Solutions',
            },
        ],
    },
    // ... see link above for full schema
    {
        mapToProperty: 'dam:assetStatus',
        value: 'approved',
        // hidden metadata element, this metadata will be applied to the asset without rendering UI for user input
        element: 'hidden',
    },
];

const handleMetadataFormChange = (event: MetadataChangeEvent) => {
    const { property, value } = event;

    console.log({ property, value });
}

const UploadExampleWithMetadataForm = () => {
    return (
        <AllInOneUpload
            repositoryId={repoId}
            apiToken={apiToken}
            targetUploadPath={targetUploadPath}
            metadataSchema={sampleMetadataSchema}
            onMetadataFormChange={handleMetadataFormChange}
        />
    )
}
```

### Aangepaste upload {#customized-upload}

```
const MultipleAllInOneUploadExample = () => {
    const mfeRef = React.useRef<{ iframeRef: { current: HTMLIFrameElement } }>(null);

    return (
        <>
            <Button
                onPress={() => UploadCoordinator.initiateUpload(mfeRef.current?.iframeRef?.current)}
            >
                External Initiate Upload
            </Button>
            <AllInOneUpload
                {...otherProps}
                ref={mfeRef}
            />
        <>
    );
}
```

### Uploaden met bronnen van derden {#upload-using-third-party-source}

```
import { useState, useRef } from 'react';
import { AllInOneUpload, UploadCoordinator } from '@assets/upload';
import { Button, Flex, Divider } from '@adobe/react-spectrum';
import { sampleMetadataSchema } from './SampleMetadataSchemas';

const repoId = 'author-p52554-e145207-cmstg.adobeaemcloud.com'
const apiToken = 'eyJhbG....';
const targetUploadPath = '/content/dam/hydrated-assets/cq/as/cq-assets-upload-storybook-testing';

const defaultFiles = [
    new File(['file-content'], 'Controlled File 1'),
    new File(['file-content-with-more'], 'Controlled File 2')
];

const ControlledUploadExample = () => {
    const [controlledFiles, setControlledFiles] = useState<File[]>(defaultFiles)
    const inputRef = React.useRef<HTMLInputElement>(null);

    const handleFileInputChange = useCallback((e: ChangeEvent<HTMLInputElement>) => {
        if (e.target.files) {
            setMyFiles([...e.target.files]);
        }
    }, []);

    return (
        <Flex height="100%" alignItems="center" direction="column">
            <Flex direction="row" alignItems="center" justifyContent="center">
                <Button
                    variant="accent"
                    onPress={() => UploadCoordinator.initiateUpload()}
                    isDisabled={files.length < 1}
                >
                    External Initiate Upload
                </Button>
                <Button
                    variant="secondary"
                    onPress={() => {
                        inputRef.current?.click();
                    }}
                >
                    External Browse files
                </Button>
            </Flex>
            <Divider size="M" marginTop="size-200" />
            <AllInOneUpload
                repositoryId={repoId}
                apiToken={apiToken}
                targetUploadPath={targetUploadPath}
                files={controlledFiles}
                onFilesChange={setControlledFiles}
                hideUploadButton={true}
                metadataSchema={sampleMetadataSchema}
            />
            <input
                ref={inputRef}
                type="file"
                style={{ display: 'none' }}
                onChange={handleFileInputChange}
                multiple={true}
            />
        </Flex>
    )
}
```

### dragOptions, eigenschap {#drag-options-property}

```
dragOptions: {
            allowList: {
                '*': true,          // allow all types to be dragged
                'folder': false,    // except those explicitly set to disallow
                'image/jpeg': false // or those with specific mimeTypes
            },
         }
```

>[!MORELIKETHIS]
>
>* [&#x200B; Eigenschappen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-properties.md)
>* [&#x200B; integreer de Selector van Activa met diverse toepassingen &#x200B;](/help/assets/integrate-asset-selector.md)
>* [&#x200B; Eigenschappen van de Selecteur van Activa &#x200B;](/help/assets/asset-selector-properties.md)
>* [&#x200B; integreer de Selector van Activa met Dynamische Media met mogelijkheden OpenAPI &#x200B;](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
