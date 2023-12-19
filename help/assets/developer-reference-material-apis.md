---
title: Ontwikkelaarsreferenties voor [!DNL Assets]
description: "[!DNL Assets] Met API's en inhoud voor ontwikkelaarsverwijzing kunt u elementen beheren, zoals binaire bestanden, metagegevens, uitvoeringen, opmerkingen en [!DNL Content Fragments]."
contentOwner: AG
feature: APIs,Assets HTTP API
role: Developer,Architect,Admin
exl-id: c75ff177-b74e-436b-9e29-86e257be87fb
source-git-commit: 5acbd7a56f18ee4c3d8b8f04ab17ad44fe6f0647
workflow-type: tm+mt
source-wordcount: '1926'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager Assets] Gebruiksgevallen, API&#39;s en referentiemateriaal voor ontwikkelaars {#assets-cloud-service-apis}

Het artikel bevat aanbevelingen, referentiematerialen en bronnen voor ontwikkelaars van [!DNL Assets] als [!DNL Cloud Service]. Het omvat nieuwe module voor het uploaden van middelen, API-referentie en informatie over de ondersteuning die wordt geboden in workflows na verwerking.

## [!DNL Experience Manager Assets] API&#39;s en bewerkingen {#use-cases-and-apis}

[!DNL Assets] als [!DNL Cloud Service] bevat verschillende API&#39;s die programmatisch kunnen communiceren met digitale elementen. Elke API ondersteunt specifieke gebruiksgevallen, zoals vermeld in de onderstaande tabel. De [!DNL Assets] gebruikersinterface, [!DNL Experience Manager] bureaubladtoepassing en [!DNL Adobe Asset Link] alle of sommige bewerkingen ondersteunen.

>[!CAUTION]
>
>Sommige API&#39;s blijven bestaan, maar worden niet actief ondersteund (aangeduid met een ×). Gebruik deze API&#39;s zoveel mogelijk niet.

| Ondersteuningsniveau | Beschrijving |
| ------------- | --------------------------- |
| ✓ | Ondersteund |
| × | Niet ondersteund. Niet gebruiken. |
| - | Niet beschikbaar |

| Hoofdletters gebruiken | [aem-upload](https://github.com/adobe/aem-upload) | [Experience Manager / Verkopen / JCR](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html) Java API&#39;s | [Asset compute](https://experienceleague.adobe.com/docs/asset-compute/using/extend/understand-extensibility.html) | [[!DNL Assets] HTTP-API](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/mac-api-assets.html#create-an-asset) | Sling [GET](https://sling.apache.org/documentation/bundles/rendering-content-default-get-servlets.html) / [POST](https://sling.apache.org/documentation/bundles/manipulating-content-the-slingpostservlet-servlets-post.html) servlets | [GraphQL](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) |
| ----------------|:---:|:---:|:---:|:---:|:---:|:---:|
| **Origineel binair** |  |  |  |  |  |  |
| Origineel maken | ✓ | × | - | × | × | - |
| Origineel lezen | - | × | ✓ | ✓ | ✓ | - |
| Origineel bijwerken | ✓ | × | ✓ | × | × | - |
| Origineel verwijderen | - | ✓ | - | ✓ | ✓ | - |
| Origineel kopiëren | - | ✓ | - | ✓ | ✓ | - |
| Origineel verplaatsen | - | ✓ | - | ✓ | ✓ | - |
| **Metagegevens** |  |  |  |  |  |  |
| Metagegevens maken | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens lezen | - | ✓ | - | ✓ | ✓ | - |
| Metagegevens bijwerken | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens verwijderen | - | ✓ | ✓ | ✓ | ✓ | - |
| Metagegevens kopiëren | - | ✓ | - | ✓ | ✓ | - |
| Metagegevens verplaatsen | - | ✓ | - | ✓ | ✓ | - |
| **Inhoudsfragmenten (CF)** |  |  |  |  |  |  |
| CF maken | - | ✓ | - | ✓ | - | - |
| CF lezen | - | ✓ | - | ✓ | - | ✓ |
| CF bijwerken | - | ✓ | - | ✓ | - | - |
| CF verwijderen | - | ✓ | - | ✓ | - | - |
| CF kopiëren | - | ✓ | - | ✓ | - | - |
| CF verplaatsen | - | ✓ | - | ✓ | - | - |
| **Versies** |  |  |  |  |  |  |
| Versie maken | ✓ | ✓ | - | - | - | - |
| Leesversie | - | ✓ | - | - | - | - |
| Versie verwijderen | - | ✓ | - | - | - | - |
| **Mappen** |  |  |  |  |  |  |
| Map maken | ✓ | ✓ | - | ✓ | - | - |
| Map lezen | - | ✓ | - | ✓ | - | - |
| Map verwijderen | ✓ | ✓ | - | ✓ | - | - |
| Map kopiëren | ✓ | ✓ | - | ✓ | - | - |
| Map verplaatsen | ✓ | ✓ | - | ✓ | - | - |

## Elementen uploaden {#asset-upload}

In [!DNL Experience Manager] als [!DNL Cloud Service]kunt u de elementen rechtstreeks uploaden naar de cloudopslag met HTTP API. De stappen voor het uploaden van een binair bestand staan hieronder. Voer deze stappen uit in een externe toepassing en niet in de [!DNL Experience Manager] JVM.

1. [Een HTTP-aanvraag verzenden](#initiate-upload). Het geeft informatie [!DNL Experience Manage]r plaatsing van uw intent om een nieuw binair getal te uploaden.
1. [PUT de inhoud van binair getal](#upload-binary) naar een of meer URI&#39;s die in het inleidingsverzoek worden verstrekt.
1. [Een HTTP-aanvraag verzenden](#complete-upload) om de server mee te delen dat de inhoud van binair getal met succes werd geüpload.

![Overzicht van het directe binaire upload protocol](assets/add-assets-technical.png)

>[!IMPORTANT]
>
Voer de bovenstaande stappen uit in een externe toepassing en niet in de [!DNL Experience Manager] JVM.

Deze aanpak biedt een schaalbare en krachtigere verwerking van geüploade bedrijfsmiddelen. De verschillen ten opzichte van [!DNL Experience Manager] 6,5 zijn:

* Binaire getallen worden niet doorlopen [!DNL Experience Manager], die het uploadproces nu eenvoudig coördineert met de binaire cloudopslag die voor de plaatsing wordt gevormd.
* Binaire cloudopslag werkt met een Content Delivery Network (CDN) of Edge-netwerk. Een CDN selecteert een uploadeindpunt dat dichter voor een cliënt is. Wanneer de gegevens een kortere afstand aan een nabijgelegen eindpunt reizen, verbeteren de uploadprestaties en de gebruikerservaring, vooral voor geografisch verdeelde teams.

>[!NOTE]
>
Zie de cliëntcode om deze benadering in open-source uit te voeren [aem-upload bibliotheek](https://github.com/adobe/aem-upload).
>
[!IMPORTANT]
>
In bepaalde omstandigheden kunnen wijzigingen zich niet volledig verspreiden tussen verzoeken om Experience Manager vanwege uiteindelijk consistente aard van de opslag in Cloud Service. Dit leidt tot 404 reacties om uploadvraag in werking te stellen of te voltooien toe te schrijven aan de vereiste omslagverwezenlijking die niet wordt verspreid. Clients moeten 404 reacties verwachten en deze afhandelen door een nieuwe strategie uit te voeren.

### Uploaden starten {#initiate-upload}

Verzend een HTTP-POST-aanvraag naar de gewenste map. In deze map worden middelen gemaakt of bijgewerkt. Inclusief de kiezer `.initiateUpload.json` om erop te wijzen dat het verzoek het uploaden van een binair dossier moet in werking stellen. Het pad naar de map waar het element moet worden gemaakt, is bijvoorbeeld `/assets/folder`. Het verzoek van de POST is `POST https://[aem_server]:[port]/content/dam/assets/folder.initiateUpload.json`.

Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens met de volgende velden:

* `(string) fileName`: Vereist. De naam van het element zoals het wordt weergegeven [!DNL Experience Manager].
* `(number) fileSize`: Vereist. De bestandsgrootte in bytes van het element dat wordt geüpload.

Eén aanvraag kan worden gebruikt om uploads voor meerdere binaire bestanden te starten, zolang elk binair getal de vereiste velden bevat. Als dit lukt, reageert de aanvraag op een `201` statuscode en een body die JSON-gegevens in de volgende indeling bevat:

```json
{
    "completeURI": "(string)",
    "folderPath": "(string)",
    "files": [
        {
            "fileName": "(string)",
            "mimeType": "(string)",
            "uploadToken": "(string)",
            "uploadURIs": [
                "(string)"
            ],
            "minPartSize": (number),
            "maxPartSize": (number)
        }
    ]
}
```

* `completeURI` (tekenreeks): Roep deze URI aan wanneer het binaire bestand klaar is met uploaden. De URI kan een absolute of relatieve URI zijn en clients moeten beide kunnen afhandelen. De waarde kan dus `"https://[aem_server]:[port]/content/dam.completeUpload.json"` of `"/content/dam.completeUpload.json"` Zie [uploaden voltooien](#complete-upload).
* `folderPath` (tekenreeks): Volledig pad naar de map waarin het binaire bestand is geüpload.
* `(files)` (array): Een lijst met elementen waarvan de lengte en volgorde overeenkomen met de lengte en volgorde van de lijst met binaire informatie die in de initiërende aanvraag wordt verstrekt.
* `fileName` (tekenreeks): De naam van het corresponderende binaire getal, zoals opgegeven in het initiërende verzoek. Deze waarde moet in het volledige verzoek worden opgenomen.
* `mimeType` (tekenreeks): Het mime-type van het corresponderende binaire getal, zoals opgegeven in het initiërende verzoek. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadToken` (tekenreeks): een token voor het uploaden van het overeenkomstige binaire bestand. Deze waarde moet in het volledige verzoek worden opgenomen.
* `uploadURIs` (array): Een lijst met tekenreeksen waarvan de waarden volledige URI&#39;s zijn waarnaar de binaire inhoud moet worden geüpload (zie [Binair bestand uploaden](#upload-binary)).
* `minPartSize` (getal): de minimale lengte, in bytes, van gegevens die aan een van de `uploadURIs`, als er meer dan één URI is.
* `maxPartSize` (getal): De maximale lengte, in bytes, van gegevens die aan een van de `uploadURIs`, als er meer dan één URI is.

### Binair bestand uploaden {#upload-binary}

De uitvoer van het starten van een upload bevat een of meer URI-waarden voor uploaden. Als er meerdere URI&#39;s zijn opgegeven, kan de client de binaire code splitsen in onderdelen en PUT-aanvragen van elk onderdeel naar de opgegeven URI&#39;s voor uploaden in volgorde indienen. Houd u aan de volgende richtlijnen wanneer u ervoor kiest om het binaire getal in delen te splitsen:

* Elk deel, met uitzondering van het laatste, moet groter zijn dan of gelijk zijn aan `minPartSize`.
* Elk onderdeel moet een grootte hebben van minder dan of gelijk aan `maxPartSize`.
* Als de grootte van uw binair getal overschrijdt `maxPartSize`, splitst de binaire waarde in delen om deze te uploaden.
* U hoeft niet alle URI&#39;s te gebruiken.

Als de grootte van uw binair getal kleiner dan of gelijk aan is `maxPartSize`, kunt u in plaats daarvan het gehele binaire bestand uploaden naar één URI voor uploaden. Als er meer dan één URI voor uploaden is opgegeven, gebruikt u de eerste URI en negeert u de rest. U hoeft niet alle URI&#39;s te gebruiken.

Met behulp van CDN-randknooppunten kunt u het opvragen van binaire bestanden versnellen.

De eenvoudigste manier om dit te bereiken is om de waarde van `maxPartSize` als de grootte van uw onderdeel. Het API-contract garandeert dat er voldoende URI&#39;s zijn voor het uploaden van het binaire bestand als u deze waarde als deelgrootte gebruikt. Hiervoor splitst u het binaire bestand in delen van grootte `maxPartSize`, met één URI voor elk onderdeel op volgorde. Het laatste deel kan elke grootte kleiner dan of gelijk aan `maxPartSize`. Stel bijvoorbeeld dat de totale grootte van het binaire getal 20.000 bytes is. `minPartSize` is 5.000 bytes, `maxPartSize` is 8.000 bytes, en het aantal upload URIs is 5. Voer de volgende stappen uit:

* Upload de eerste 8.000 bytes van het binaire getal met behulp van de eerste upload URI.
* Upload de tweede 8.000 bytes van het binaire getal met behulp van de tweede upload URI.
* Upload de laatste 4.000 bytes van het binaire getal met behulp van de derde upload URI. Aangezien dit het laatste deel is, hoeft het niet groter te zijn dan `minPartSize`.
* U hoeft de laatste twee URI&#39;s voor uploaden niet te gebruiken. U kunt ze negeren.

Een algemene fout is om de onderdeelgrootte te berekenen op basis van het aantal URI&#39;s voor uploaden dat door de API wordt verschaft. Het API-contract garandeert niet dat deze aanpak werkt en kan leiden tot deelgrootten die buiten het bereik liggen tussen `minPartSize` en `maxPartSize`. Dit kan resulteren in binaire upload mislukkingen.

Opnieuw, de gemakkelijkste en veiligste manier is eenvoudig delen van grootte gelijk aan `maxPartSize`.

Als het uploaden is gelukt, reageert de server op elke aanvraag met een `201` statuscode.

>[!NOTE]
>
Voor meer informatie over het uploadalgoritme, zie [officiële functiedocumentatie](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload) en [API-documentatie](https://jackrabbit.apache.org/oak/docs/apidocs/org/apache/jackrabbit/api/binary/BinaryUpload.html) in het Apache Jackrabbit Oak-project.

### Uploaden voltooien {#complete-upload}

Nadat alle delen van een binair dossier worden geupload, leg een verzoek van de POST van HTTP aan volledige URI voor die door de initiatiegegevens wordt verstrekt. Het inhoudstype van de aanvraaginstantie moet `application/x-www-form-urlencoded` formuliergegevens, die de volgende velden bevatten.

| Velden | Type | Vereist of niet | Beschrijving |
|---|---|---|---|
| `fileName` | String | Vereist | De naam van het element, zoals deze werd verstrekt in de inleidingsgegevens. |
| `mimeType` | String | Vereist | Het HTTP-inhoudstype van het binaire getal, zoals is opgegeven door de initiatiegegevens. |
| `uploadToken` | String | Vereist | Upload token voor het binaire bestand, zoals werd opgegeven in de initiatiegegevens. |
| `createVersion` | Boolean | Optioneel | Indien `True` en er een element met de opgegeven naam bestaat, dan [!DNL Experience Manager] maakt een nieuwe versie van het element. |
| `versionLabel` | String | Optioneel | Als er een nieuwe versie wordt gemaakt, wordt het label gekoppeld aan de nieuwe versie van een element. |
| `versionComment` | String | Optioneel | Als er een nieuwe versie wordt gemaakt, worden de opmerkingen gekoppeld aan de versie. |
| `replace` | Boolean | Optioneel | Indien `True` en er een element met de opgegeven naam bestaat, [!DNL Experience Manager] Hiermee verwijdert u het element en maakt u het opnieuw. |
| `uploadDuration` | Getal | Optioneel | De totale hoeveelheid tijd, in milliseconden, voor het dossier om volledig te uploaden. Indien opgegeven, wordt de uploadduur opgenomen in de logbestanden van het systeem voor de analyse van de overdrachtssnelheid. |
| `fileSize` | Getal | Optioneel | De grootte van het bestand, in bytes. Indien opgegeven, wordt de bestandsgrootte opgenomen in de logbestanden van het systeem voor de analyse van de overdrachtssnelheid. |

>[!NOTE]
>
Als het element bestaat en beide `createVersion` noch `replace` wordt opgegeven, dan [!DNL Experience Manager] werkt de huidige versie van het element met het nieuwe binaire getal bij.

Net als bij het initiëringsproces kunnen de volledige aanvraaggegevens informatie voor meer dan één bestand bevatten.

Het uploaden van een binair getal gebeurt pas wanneer de volledige URL voor het bestand wordt aangeroepen. Een element wordt verwerkt nadat het uploadproces is voltooid. De verwerking wordt niet gestart, zelfs niet als het binaire bestand van het element volledig is geüpload maar het uploadproces niet is voltooid. Als het uploaden is gelukt, reageert de server met een `200` statuscode.

### Voorbeeld van Shell-script om elementen te uploaden naar AEM as a Cloud Service {#upload-assets-shell-script}

Het uploadproces in meerdere stappen voor directe binaire toegang binnen AEM as a Cloud Service is geïllustreerd in het volgende voorbeeld shell-script `aem-upload.sh`:

```bash
#!/bin/bash

# Check if pv is installed
if ! command -v pv &> /dev/null; then
    echo "Error: 'pv' command not found. Please install it before running the script."
    exit 1
fi

# Check if jq is installed
if ! command -v jq &> /dev/null; then
    echo "Error: 'jq' command not found. Please install it before running the script."
    exit 1
fi

# Set DEBUG to true to enable debug statements
DEBUG=true

# Function for printing debug statements
function debug() {
    if [ "${DEBUG}" = true ]; then
        echo "[DEBUG] $1"
    fi
}

# Function to check if a file exists
function file_exists() {
    [ -e "$1" ]
}

# Function to check if a path is a directory
function is_directory() {
    [ -d "$1" ]
}

# Check if the required number of parameters are provided
if [ "$#" -ne 4 ]; then
    echo "Usage: $0 <aem-url> <asset-folder> <file-to-upload> <bearer-token>"
    exit 1
fi

AEM_URL="$1"
ASSET_FOLDER="$2"
FILE_TO_UPLOAD="$3"
BEARER_TOKEN="$4"

# Extracting file name or folder name from the file path
NAME=$(basename "${FILE_TO_UPLOAD}")

# Step 1: Check if "file-to-upload" is a folder
if is_directory "${FILE_TO_UPLOAD}"; then
    echo "Uploading files from the folder recursively..."
    
    # Recursively upload files in the folder
    find "${FILE_TO_UPLOAD}" -type f | while read -r FILE_PATH; do
        FILE_NAME=$(basename "${FILE_PATH}")
        debug "Uploading file: ${FILE_PATH}"
        
        # You can choose to initiate upload for each file here
        # For simplicity, let's assume you use the same ASSET_FOLDER for all files
        ./aem-upload.sh "${AEM_URL}" "${ASSET_FOLDER}" "${FILE_PATH}" "${BEARER_TOKEN}"
    done
else
    # "file-to-upload" is a single file
    FILE_NAME="${NAME}"

    # Step 2: Calculate File Size
    FILE_SIZE=$(stat -c %s "${FILE_TO_UPLOAD}")

    # Step 3: Initiate Upload
    INITIATE_UPLOAD_ENDPOINT="${AEM_URL}/content/dam/${ASSET_FOLDER}.initiateUpload.json"

    debug "Initiating upload..."
    debug "Initiate Upload Endpoint: ${INITIATE_UPLOAD_ENDPOINT}"
    debug "File Name: ${FILE_NAME}"
    debug "File Size: ${FILE_SIZE}"

    INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
        -d "fileName=${FILE_NAME}" \
        -d "fileSize=${FILE_SIZE}" \
        ${INITIATE_UPLOAD_ENDPOINT})

    # Continue with the rest of the script...
fi


# Check if the response body contains the specified HTML content for a 404 error
if echo "${INITIATE_UPLOAD_RESPONSE}" | grep -q "<title>404 Specified folder not found</title>"; then
    echo "Folder not found. Creating the folder..."

    # Attempt to create the folder
    CREATE_FOLDER_ENDPOINT="${AEM_URL}/api/assets/${ASSET_FOLDER}"

    debug "Creating folder..."
    debug "Create Folder Endpoint: ${CREATE_FOLDER_ENDPOINT}"

    CREATE_FOLDER_RESPONSE=$(curl -X POST \
        -H "Content-Type: application/json" \
        -H "Authorization: Bearer ${BEARER_TOKEN}" \
        -d '{"class":"'${ASSET_FOLDER}'","properties":{"title":"'${ASSET_FOLDER}'"}}' \
        ${CREATE_FOLDER_ENDPOINT})

    # Check the response code and inform the user accordingly
    STATUS_CODE_CREATE_FOLDER=$(echo "${CREATE_FOLDER_RESPONSE}" | jq -r '.properties."status.code"')
    case ${STATUS_CODE_CREATE_FOLDER} in
        201)
            echo "Folder created successfully. Initiating upload again..."

            # Retry Initiate Upload after creating the folder
            INITIATE_UPLOAD_RESPONSE=$(curl -X POST \
                -H "Authorization: Bearer ${BEARER_TOKEN}" \
                -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
                -d "fileName=${FILE_NAME}" \
                -d "fileSize=${FILE_SIZE}" \
                ${INITIATE_UPLOAD_ENDPOINT})
            ;;
        409)
            echo "Error: Folder already exists."
            ;;
        412)
            echo "Error: Precondition failed. Root collection cannot be found or accessed."
            exit 1
            ;;
        500)
            echo "Error: Internal Server Error. Something went wrong."
            exit 1
            ;;
        *)
            echo "Error: Unexpected response code ${STATUS_CODE_CREATE_FOLDER}"
            exit 1
            ;;
    esac
fi

# Extracting values from the response
FOLDER_PATH=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.folderPath')
UPLOAD_URIS=($(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadURIs[]'))
UPLOAD_TOKEN=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].uploadToken')
MIME_TYPE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].mimeType')
MIN_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].minPartSize')
MAX_PART_SIZE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.files[0].maxPartSize')
COMPLETE_URI=$(echo "${INITIATE_UPLOAD_RESPONSE}" | jq -r '.completeURI')

# Extracting "Affinity-cookie" from the response headers
AFFINITY_COOKIE=$(echo "${INITIATE_UPLOAD_RESPONSE}" | grep -i 'Affinity-cookie' | awk '{print $2}')

debug "Folder Path: ${FOLDER_PATH}"
debug "Upload Token: ${UPLOAD_TOKEN}"
debug "MIME Type: ${MIME_TYPE}"
debug "Min Part Size: ${MIN_PART_SIZE}"
debug "Max Part Size: ${MAX_PART_SIZE}"
debug "Complete URI: ${COMPLETE_URI}"
debug "Affinity Cookie: ${AFFINITY_COOKIE}"
if $DEBUG; then
    i=1
    for UPLOAD_URI in "${UPLOAD_URIS[@]}"; do
        debug "Upload URI $i: "$UPLOAD_URI
        i=$((i+1))
    done
fi


# Calculate the number of parts needed
NUM_PARTS=$(( (FILE_SIZE + MAX_PART_SIZE - 1) / MAX_PART_SIZE ))
debug "Number of Parts: $NUM_PARTS"

# Calculate the part size for the last chunk
LAST_PART_SIZE=$(( FILE_SIZE % MAX_PART_SIZE ))
if [ "${LAST_PART_SIZE}" -eq 0 ]; then
    LAST_PART_SIZE=${MAX_PART_SIZE}
fi

# Step 4: Upload binary to the blob store in parts
PART_NUMBER=1
for i in $(seq 1 $NUM_PARTS); do
    PART_SIZE=${MAX_PART_SIZE}
    if [ ${PART_NUMBER} -eq ${NUM_PARTS} ]; then
        PART_SIZE=${LAST_PART_SIZE}
        debug "Last part size: ${PART_SIZE}"
    fi

    PART_FILE="/tmp/${FILE_NAME}_part${PART_NUMBER}"

    # Creating part file 
    SKIP=$((PART_NUMBER - 1))
    SKIP=$((MAX_PART_SIZE * SKIP))
    dd if="${FILE_TO_UPLOAD}" of="${PART_FILE}"  bs="${PART_SIZE}" skip="${SKIP}" count="${PART_SIZE}" iflag=skip_bytes,count_bytes  > /dev/null 2>&1
    debug "Creating part file: ${PART_FILE} with size ${PART_SIZE}, skipping first ${SKIP} bytes."

    
    UPLOAD_URI=${UPLOAD_URIS[$PART_NUMBER-1]}

    debug "Uploading part ${PART_NUMBER}..."
    debug "Part Size: $PART_SIZE"
    debug "Part File: ${PART_FILE}"
    debug "Part File Size: $(stat -c %s "${PART_FILE}")"
    debug "Upload URI: ${UPLOAD_URI}"

    # Upload the part in the background
    if command -v pv &> /dev/null; then
        pv "${PART_FILE}" | curl --progress-bar -X PUT --data-binary "@-" "${UPLOAD_URI}" &
    else
        curl -# -X PUT --data-binary "@${PART_FILE}" "${UPLOAD_URI}" &
    fi

    PART_NUMBER=$((PART_NUMBER + 1))
done

# Wait for all background processes to finish
wait

# Step 5: Complete the upload in AEM
COMPLETE_UPLOAD_ENDPOINT="${AEM_URL}${COMPLETE_URI}"

debug "Completing the upload..."
debug "Complete Upload Endpoint: ${COMPLETE_UPLOAD_ENDPOINT}"

RESPONSE=$(curl -X POST \
    -H "Authorization: Bearer ${BEARER_TOKEN}" \
    -H "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" \
    -H "Affinity-cookie: ${AFFINITY_COOKIE}" \
    --data-urlencode "uploadToken=${UPLOAD_TOKEN}" \
    --data-urlencode "fileName=${FILE_NAME}" \
    --data-urlencode "mimeType=${MIME_TYPE}" \
    "${COMPLETE_UPLOAD_ENDPOINT}")
    
debug $RESPONSE

echo "File upload completed successfully."
```

### Uploadbibliotheek met open bron {#open-source-upload-library}

Voor meer informatie over de uploadalgoritmen of om uw eigen uploadscripts en -gereedschappen te maken, biedt Adobe opensource-bibliotheken en -gereedschappen:

* [Opensource-em-upload-bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).

>[!NOTE]
>
Zowel de aem-upload bibliotheek als het bevel-lijn hulpmiddel gebruiken allebei [node-httptransfer-bibliotheek](https://github.com/adobe/node-httptransfer/)

### Verouderde API&#39;s voor middelenupload {#deprecated-asset-upload-api}

<!-- #ENGCHECK review / update the list of deprecated APIs below. -->

De nieuwe uploadmethode wordt alleen ondersteund voor [!DNL Adobe Experience Manager] als [!DNL Cloud Service]. De API&#39;s van [!DNL Adobe Experience Manager] 6.5 zijn afgekeurd. De methoden voor het uploaden of bijwerken van elementen of uitvoeringen (elke binaire upload) zijn afgekeurd in de volgende API&#39;s:

* [EXPERIENCE MANAGER ASSETS HTTP API](mac-api-assets.md)
* `AssetManager` Java API, zoals `AssetManager.createAsset(..)`, `AssetManager.createAssetForBinary(..)`, `AssetManager.getAssetForBinary(..)`, `AssetManager.removeAssetForBinary(..)`, `AssetManager.createOrUpdateAsset(..)`, `AssetManager.createOrReplaceAsset(..)`

>[!MORELIKETHIS]
>
* [Opensource-em-upload-bibliotheek](https://github.com/adobe/aem-upload).
* [Opensource opdrachtregelprogramma](https://github.com/adobe/aio-cli-plugin-aem).
* [Apache Jackrabbit Oak-documentatie voor direct uploaden](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html#Upload).

## Workflows voor de verwerking en naverwerking van bedrijfsmiddelen {#post-processing-workflows}

In [!DNL Experience Manager]is de verwerking van de activa gebaseerd op **[!UICONTROL Processing Profiles]** configuratie die gebruikt [microservices voor bedrijfsmiddelen](asset-microservices-configure-and-use.md#get-started-using-asset-microservices). Voor verwerking zijn geen ontwikkelaarsextensies vereist.

Voor workflowconfiguratie na verwerking gebruikt u de standaardworkflows met extensies met aangepaste stappen.

## Ondersteuning van workflowstappen in de naverwerkingsworkflow {#post-processing-workflows-steps}

Als u een upgrade uitvoert van een vorige versie van [!DNL Experience Manager], kunt u met behulp van asset-microservices elementen verwerken. De &#39;cloud-native asset microservices&#39; zijn eenvoudiger te configureren en gebruiken. Enkele workflowstappen die in het dialoogvenster [!UICONTROL DAM Update Asset] in de vorige versie wordt niet ondersteund. Zie voor meer informatie over ondersteunde klassen de klasse [Java API-referentie of JavaDocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

De volgende technische workflowmodellen worden vervangen door asset microservices of de ondersteuning is niet beschikbaar:

* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.StartTrainingProcess`
* `com.day.cq.dam.similaritysearch.internal.workflow.smarttags.TransferTrainingDataProcess`
* `com.day.cq.dam.switchengine.process.SwitchEngineHandlingProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`

<!-- Commenting the previous list documented at the time of GA. Replacing it with the updated list via cqdoc-18231.

* `com.day.cq.dam.core.process.DeleteImagePreviewProcess`
* `com.day.cq.dam.s7dam.common.process.DMEncodeVideoWorkflowCompletedProcess`
* `com.day.cq.dam.core.process.GateKeeperProcess`
* `com.day.cq.dam.core.process.AssetOffloadingProcess`
* `com.day.cq.dam.core.process.MetadataProcessorProcess`
* `com.adobe.cq.dam.dm.process.workflow.DMImageProcess`
* `com.day.cq.dam.s7dam.common.process.S7VideoThumbnailProcess`
* `com.day.cq.dam.scene7.impl.process.Scene7UploadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoProxyServiceProcess`
* `com.day.cq.dam.s7dam.common.process.VideoThumbnailDownloadProcess`
* `com.day.cq.dam.s7dam.common.process.VideoUserUploadedThumbnailProcess`
* `com.day.cq.dam.core.process.CreatePdfPreviewProcess`
* `com.day.cq.dam.core.process.CreateWebEnabledImageProcess`
* `com.day.cq.dam.video.FFMpegThumbnailProcess`
* `com.day.cq.dam.core.process.ThumbnailProcess`
* `com.day.cq.dam.cameraraw.process.CameraRawHandlingProcess`
* `com.day.cq.dam.core.process.CommandLineProcess`
* `com.day.cq.dam.pdfrasterizer.process.PdfRasterizerHandlingProcess`
* `com.day.cq.dam.core.process.AddPropertyWorkflowProcess`
* `com.day.cq.dam.core.process.CreateSubAssetsProcess`
* `com.day.cq.dam.core.process.DownloadAssetProcess`
* `com.day.cq.dam.word.process.ExtractImagesProcess`
* `com.day.cq.dam.word.process.ExtractPlainProcess`
* `com.day.cq.dam.video.FFMpegTranscodeProcess`
* `com.day.cq.dam.ids.impl.process.IDSJobProcess`
* `com.day.cq.dam.indd.process.INDDMediaExtractProcess`
* `com.day.cq.dam.indd.process.INDDPageExtractProcess`
* `com.day.cq.dam.core.impl.lightbox.LightboxUpdateAssetProcess`
* `com.day.cq.dam.pim.impl.sourcing.upload.process.ProductAssetsUploadProcess`
* `com.day.cq.dam.core.process.ScheduledPublishBPProcess`
* `com.day.cq.dam.core.process.ScheduledUnPublishBPProcess`
* `com.day.cq.dam.core.process.SendDownloadAssetEmailProcess`
-->

<!-- PPTX source: slide in add-assets.md - overview of direct binary upload section of
https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [Elementen HTTP-API](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)

>[!MORELIKETHIS]
>
* [[!DNL Experience Cloud] als [!DNL Cloud Service] SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).