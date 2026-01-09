---
title: Hoe stelt u Forms Communications Synchronous API's in?
description: Ontwikkelomgeving instellen voor interactieve communicatie-synchrone API's voor Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: e2f57a32fcc098a2331ad74540a3d48832c2b3c3
workflow-type: tm+mt
source-wordcount: '2380'
ht-degree: 0%

---


# OAuth Server-to-Server Toegang voor Communicatie Synchrone APIs van AEM Forms configureren

Deze handleiding bevat instructies voor het configureren en aanroepen van AEM Forms Communications Synchronous API&#39;s die via de Adobe Developer Console worden benaderd via OAuth Server-to-Server-verificatie.

## Vereisten

Als u een omgeving wilt instellen voor het uitvoeren en testen van AEM Forms Communications API&#39;s, moet u het volgende doen:

### Toegang en machtigingen

Zorg ervoor u de vereiste toegangsrechten en toestemmingen hebt alvorens u begint de Mededelingen APIs te vormen.

**Gebruiker en roltoestemmingen**

- Ontwikkelaarsrol toegewezen in Adobe Admin Console
- Toestemming om projecten te maken in de Adobe Developer Console

>[!NOTE]
>
> Meer leren over het toewijzen van rollen en het verlenen van toegang tot gebruikers, verwijs naar het artikel [ gebruikers en rollen ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/users-and-roles) toevoegen.

**Toegang van de Bewaarplaats van de it**

- Toegang tot Cloud Manager Git Repository
- Referenties ophalen voor klonen en wijzigingen doorvoeren

>[!NOTE]
>
> Meer leren op hoe te om Adobe Cloud Manager en Adobe Cloud Manager te integreren, zie {de Documentatie van de Integratie van 0} it [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html)

### Toegangstoken genereren met Adobe Developer Console (ADC)

- Genereer toegangstoken via de Adobe Developer Console met behulp van OAuth Server-to-Server verificatie.
- Client-id ophalen van de Adobe Developer Console

>[!NOTE]
>
> Voor meer informatie over Server-aan-Server authentificatie OAuth die Adobe Developer Console gebruikt, [ klik hier ](/help/forms/oauth-api-authetication.md).

### Ontwikkelingsinstrumenten

- **Node.js** voor het runnen van steekproeftoepassingen
- Laatste versie van **Git**
- Toegang tot **terminal/de lijn van het Bevel**
- **redacteur van de Tekst of winde** voor het uitgeven van configuratiedossiers (de Code van VS, IntelliJ, enz.)
- **Postman** of gelijkaardig hulpmiddel voor API het testen

>[!NOTE]
>
> Dit is een eenmalig proces per omgevingsproces dat moet worden voltooid voordat AEM Forms Communications API&#39;s kunnen worden ingesteld.

## AEM Forms Communications Synchronous API&#39;s configureren

AEM Forms Communication-API&#39;s zijn toegankelijk via de Adobe Developer Console met behulp van OAuth server-to-server verificatie.

Voer de stappen uit om uit te leggen hoe u de synchrone API&#39;s voor communicatie van Forms configureert om PDF te genereren met behulp van de sjabloon en het XDP-bestand:

### Stap 1: Toegang tot AEM Cloud Service Environment en AEM Forms Endpoint

Open de omgevingsgegevens van de AEM Cloud Service om de URL&#39;s en id&#39;s te verkrijgen die nodig zijn voor de API-configuratie.

#### 1.1 Aanmelden bij Adobe Cloud Manager

1. Ga aan [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com)
2. Meld u aan bij uw Adobe ID

#### 1.2 Navigeer naar het programmaoverzicht

Selecteer uw programma in de lijst. U wordt opnieuw gericht aan de **pagina van het Overzicht van het Programma**

![ Pagina van het Overzicht van het Programma ](/help/forms/assets/program-overview.png)

#### 1.3 Toegang tot en weergave van AEM Cloud Service Environment

U kunt de details van de AEM Cloud Service Environment weergeven of openen met een van de volgende twee opties:

>[!BEGINTABS]

>[!TAB  Optie 1: Van de Pagina van het Overzicht ]

1. Op de **pagina van het Overzicht van het Programma**
2. Klik **&quot;Milieu&#39;s&quot;** in het linkerzijmenu.  U ziet een lijst met alle omgevingen
3. Klik op de naam van de specifieke omgeving om details weer te geven

   ![ Mening Alle Milieu&#39;s ](/help/forms/assets/all-env.png)

>[!TAB  Optie 2: Van de Sectie van Milieu&#39;s ]

1. Op de **pagina van het Overzicht van het Programma**
2. Bepaal de plaats van de **sectie van Milieu&#39;s**
3. Klik **&quot;tonen allen&quot;** om alle milieu&#39;s te bekijken
4. Klik het **weglatingsmenu (...)** naast het milieu
5. Selecteer **&quot;Details van de Mening&quot;**

   ![ Optie1-Milieu Details ](/help/forms/assets/option2-env-details.png)

>[!ENDTABS]

#### &#x200B;4. Zoek je AEM Forms-eindpunt

Van de **pagina van de Milieu** details, neem nota van uw instantie van AEM URL.

![ Optie1-Milieu Details ](/help/forms/assets/option1-env.png)

>[!NOTE]
>
> Om te zien hoe te om tot het Milieu van de Dienst van de Wolk van de Toegang AEM en Eindpunt van AEM Forms toegang te hebben, zie [ het Leiden Documentatie van Milieu&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html).

### Stap 2: gegevensopslagruimte voor klonen

Kloont de Cloud Manager Git Repository om uw API-configuratiebestanden te beheren.

#### 2.1 Zoek de sectie Opslagplaats

1. Op de **pagina van het Overzicht van het 0} Programma, klik de** Bewaarplaatsen **tabel**
2. Zoek de naam van de opslagplaats en klik op het weglatingenmenu (...)
3. De URL van de gegevensopslagruimte kopiëren

   ![ Reactie URL van het Exemplaar ](/help/forms/assets/copy-repo-url.png)

>[!NOTE]
>
> De URL-indeling is doorgaans `https://git.cloudmanager.adobe.com/<org>/<program>/`

#### 2.2 Klonen met Git-opdracht

1. De opdrachtprompt of terminal openen
2. Voer de opdracht `git clone` uit om de Git-opslagplaats te klonen.

   ```bash
   git clone [repository-url]
   ```

>[!NOTE]
>
> Als u de Git-opslagplaats wilt klonen, gebruikt u de gegevens die door Adobe Cloud Manager zijn opgegeven.

Als u bijvoorbeeld uw Git Repository wilt klonen, voert u de volgende opdracht uit:

```bash
https://git.cloudmanager.adobe.com/formsinternal01/AEMFormsInternal-ReleaseSanity-pXXX-ukYYYY/
```

![ Klonend de Bewaarplaats van de it ](/help/forms/assets/repo-clone.png)

Meer leren op hoe te om Adobe Cloud Manager en Adobe Cloud Manager te integreren, zie {de Documentatie van de Integratie van 0} it [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html)

### Stap 3: Adobe Developer Console Project Setup

#### 3.1 Toegang tot Adobe Developer Console

1. Ga aan [ Adobe Developer Console ](https://developer.adobe.com/console)
2. Meld u aan bij uw Adobe ID
3. Nieuw project maken of naar een bestaand project navigeren

>[!BEGINTABS]

>[!TAB  om een nieuw project ] te creëren

1. Van de **Snelle sectie van het Begin**, klik **creeer nieuw project**
2. Een nieuw project wordt gecreeerd met een standaardnaam

   ![ creeer ADC Project ](/help/forms/assets/adc-home.png)

3. Klik **uitgeven project** in de hoogste juiste hoek

   ![ geef Project ](/help/forms/assets/adc-edit-project.png) uit

4. Geef een betekenisvolle naam op (bijvoorbeeld &quot;formsproject&quot;)
5. Klik **sparen**

   ![ geef de Naam van het Project uit ](/help/forms/assets/adc-edit-projectname.png)

>[!TAB  om aan uw bestaand project ] te navigeren

1. Klik **Alle Projecten** van Adobe Developer Console

   ![ Projecten van het Onderzoek ](/help/forms/assets/search-adc-project.png)

2. Zoek uw project en klik om het te openen.

   ![ plaats Projecten ](/help/forms/assets/locate-adc-project.png)

>[!ENDTABS]

#### 3.2 Communicatie-API&#39;s van Forms toevoegen

1. Klik **toevoegen API**

   ![ voeg api ](/help/forms/assets/adc-add-api.png) toe

2. In _voeg API_ dialoog toe, filter door **Experience Cloud**
3. Selecteer **&quot;Communicatie APIs van Forms&quot;**

   ![ voeg Communicatie API van Forms toe ](/help/forms/assets/adc-add-forms-api.png)

4. Klik **daarna**
5. Selecteer **Server-aan-Server** authentificatiemethode

   ![ Uitgezochte methode van de Authentificatie ](/help/forms/assets/adc-add-authentication-method.png)
6. Klik **daarna**

#### 3.3 Productprofiel toevoegen

1. Selecteer het **Profiel van het Product** dat uw instantie URL van AEM (`https://Service Type -Environment Type-Program XXX-Environment XXX.adobeaemcloud.com`) aanpast.

2. Klik **sparen gevormde API**. De API en het Profiel van het Product worden toegevoegd aan uw project

   ![ Uitgezochte Configuratie van het Project ](/help/forms/assets/adc-add-product-profile.png)

3. Bekijk de **Credentials details** sectie

   ![ Credentials van de Mening ](/help/forms/assets/adc-view-credential.png)

**Opname API geloofsbrieven**

```text
    API Credentials:
    ================
    Client ID: <your_client_id>
    Client Secret: <your_client_secret>
    Technical Account ID: <tech_account_id>
    Organization ID: <org_id>
    Scopes: AdobeID,openid,read_organizations
```

#### 3.4 Genereer de toegang

>[!BEGINTABS]

>[!TAB  voor het Testen ]

Handmatig toegangstokens genereren in Adobe Developer Console:

1. Klik **&quot;produceer toegangstoken&quot;** knoop in de API van uw project sectie
2. Het gegenereerde toegangstoken kopiëren

   ![ produceer het Token van de Toegang ](/help/forms/assets/adc-access-token.png)

>[!NOTE]
>
> Het teken van de toegang is geldig slechts voor **24 uren**

>[!TAB  voor Productie ]

Genereer programmatically tokens gebruikend [ IMS van Adobe ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/security/setting-up-ims-integrations-for-aem-as-a-cloud-service) API:

**Vereiste Referenties:**

- Client-id
- Clientgeheim
- Bereiken (doorgaans: `openid, AdobeID, read_organizations, additional_info.projectedProductContext, read_pc.dma_aem_cloud, aem.document`)

**Symbolische Eindpunt:**

```
    https://ims-na1.adobelogin.com/ims/token/v3
```

**Verzoek van de Steekproef (krulling):**

```bash
    curl -X POST 'https://ims-na1.adobelogin.com/ims/token/v3' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'grant_type=client_credentials' \
    -d 'client_id=<YOUR_CLIENT_ID>' \
    -d 'client_secret=<YOUR_CLIENT_SECRET>' \
    -d 'scope=AdobeID,openid,read_organizations'
```

**Reactie:**

```json
        {
        "access_token": "eyJhbGciOiJSUz...",
        "token_type": "bearer",
        "expires_in": 86399
        }
```

>[!ENDTABS]

U kunt het gegenereerde toegangstoken nu gebruiken om API-aanroepen te maken voor ontwikkelings-, stage- of productieomgevingen.

>[!NOTE]
>
> Meer over server-aan-server authentificatie OAuth via Adobe Developer Console leren, verwijs naar het [ artikel van de Authentificatie van 0} OAuth Server-aan-Server.](/help/forms/oauth-api-authetication.md)

### Stap 4: Client-id registreren bij AEM-omgeving

Om identiteitskaart van de Cliënt van uw ADC Project toe te laten om met de instantie van AEM te communiceren, moet u het registreren gebruikend een YAML configuratiedossier en het opstellen via een Pijpleiding Config.

#### 4.1 Configuratiedirectory zoeken of maken

1. Ga naar de gekloonde AEM Project-opslagplaats en zoek de map `config`
2. Als het niet bestaat, creeer het op het niveau van de projectwortel:

   ```bash
   mkdir config
   ```

3. Maak een nieuw bestand met de naam `api.yaml` in de map `config` :

   ```bash
   touch config/api.yaml
   ```

4. Voeg de volgende code toe aan het `api.yaml` -bestand:

   ```yaml
   kind: "API"
   version: "1"
   metadata:
   envTypes: ["dev"]  # or ["prod", "stage"] for production environments
   data:
   allowedClientIDs:
       author:
       - "<your_client_id>"
       publish:
       - "<your_client_id>"
       preview:
       - "<your_client_id>"
   ```

In het volgende voorbeeld worden de configuratieparameters uitgelegd:

- **soort**: Altijd plaats aan `"API"` (identificeert dit als API configuratie)
- **versie**: API versie, typisch `"1"` of `"1.0"`
- **envTypes**: Serie van milieutypes waar dit config van toepassing is
   - `["dev"]` - Alleen ontwikkelomgevingen
   - `["stage"]` - Alleen testomgevingen
   - `["prod"]` - Alleen productieomgevingen
- **allowedClientIDs**: De cliënt IDs wordt toegestaan om tot uw instantie van AEM toegang te hebben
   - **auteur**: De identiteitskaart van de cliënt voor auteursrij
   - **publiceert**: De identiteitskaart van de cliënt voor publiceer rij
   - **voorproef**: De identiteitskaart van de cliënt voor voorproefrij

![ Toevoegend het dossier Config ](/help/forms/assets/create-api-yaml-file.png)

#### 4.2 Wijzigingen vastleggen en duwen

1. Navigeer naar de hoofdmap van uw gekloonde opslagplaats en voer de onderstaande opdrachten uit:


   ```bash
       git add config/api.yaml
       git commit -m "Whitelist client id for api invocation"
       git push origin <your-branch>
   ```

   ![ de Veranderingen van de Git van de Duw ](/help/forms/assets/push-yaml-changes-in-git.png)


### Stap 5: Opstelling Config Pipeline

#### 5.1 Zoek de Pipelinekaart

1. Bepaal de plaats van **Pijpleidingen** kaart op de pagina van het Overzicht van het Programma
2. Klik **&quot;toevoegen&quot;** knoop

   ![ voeg Pipleine ](/help/forms/assets/add-pipeline.png) toe

#### 5.2 Selecteer het type Pijpleiding

- **voor de milieu&#39;s van de Ontwikkeling**: Selecteer **&quot;voeg niet-productiepijpleiding toe&quot;**. Niet-productiepijpleidingen zijn bestemd voor ontwennings- en werkruimten

- **voor de milieu&#39;s van de Productie**: Selecteer **&quot;Voeg de Pijpleiding van de Productie toe&quot;**. Voor productiepijpleidingen zijn aanvullende goedkeuringen vereist

>[!NOTE]
>
> In dit geval, creeer een niet-Productiepijpleiding aangezien een ontwikkelomgeving beschikbaar is.

**1. Vorm Pijpleiding - het Lusje van de Configuratie**

In het **lusje van de Configuratie**:

a. **Type van Pijpleiding**

- Selecteer **&quot;Pipeline van de Plaatsing&quot;**

b. **Naam van de Pijpleiding**

- Geef een beschrijvende naam op. Geef de pijpleiding bijvoorbeeld de naam `api-config-pipieline`

c. **Trigger van de Plaatsing**

- **Hand**: Implementeer slechts wanneer manueel teweeggebracht (geadviseerd voor aanvankelijke opstelling)
- **op de Veranderingen van het Git**: Auto-stel op wanneer de veranderingen aan de tak worden geduwd

d. **Belangrijk Metrisch Gedrag van Mislukt**

- **vraag telkens als**: Vraag om actie op mislukkingen (gebrek)
- **Onmiddellijk Fail**: Automatisch ontbreken pijpleiding op metrische mislukkingen
- **ga onmiddellijk** verder: ondanks mislukkingen

e. Klik **&quot;ga&quot;** verder om aan het **Source Code** lusje te werk te gaan

![ Config Pijpleiding ](/help/forms/assets/add-config-pipeline.png)

**2. Pijpleiding configureren - tabblad Source-code**

In het **lusje van de Code van 0} Source:**

a. **Type van Plaatsing**

- Selecteer **&quot;gerichte plaatsing&quot;**

b. **Opties van de Plaatsing**

- Selecteer **&quot;Config&quot;** (stel configuratiedossiers slechts op). Het vertelt Cloud Manager dit een config plaatsing is.

c. **Uitgezochte In aanmerking komende Milieu van de Plaatsing**

- Kies het milieu waar u config wilt opstellen. In dit geval is dit een `dev` -omgeving.

d. **bepaal de Details van de Code van Source**

- **Bewaarplaats**: Selecteer de bewaarplaats die uw `api.yaml` dossier bevat. Selecteer bijvoorbeeld de `AEMFormsInternal-ReleaseSanity-pXXXXX-ukYYYYY` repository.
- **Tak van de Git**: Selecteer uw tak. In dit geval wordt de code bijvoorbeeld geïmplementeerd in de `main` -vertakking.
- **Plaats van de Code**: ga de weg aan `config` folder in. Terwijl `api.yaml` zich in de `config` -map bij de hoofdmap bevindt, voert u `/config` in

e. Klik **&quot;sparen&quot;** om de pijpleiding tot stand te brengen

![ Config Pijpleiding ](/help/forms/assets/confirm-pipeline-1.png)

### Stap 6: Configuratie implementeren

Nu de pijplijn wordt gecreeerd, stel uw `api.yaml` configuratie op:

#### 6.1 Van het Overzicht van Pijpleidingen

1. Voor de pagina van het Overzicht van het Programma, bepaal de plaats van de **Pijpleidingen** kaart
2. Navigeer aan uw onlangs gecreeerd config pijpleiding in de lijst. Bijvoorbeeld, zoek de pijpleidingsnaam u creeerde (b.v., &quot;api-config-pijpleiding&quot;). U kunt pijpleidingsdetails met inbegrip van status en laatste looppas zien.

#### 6.2 De implementatie starten*

1. Klik **&quot;bouwen&quot;** knoop (of speel pictogram ▶) naast uw pijpleiding
2. Bevestig de plaatsing indien ertoe aangezet en de pijpleidingsuitvoering begint

![ stel de pijpleiding ](/help/forms/assets/run-config-pipeline.png) in werking

#### 6.3 Controleren of de implementatie is gelukt

- Wacht op de pijpleiding om te voltooien.
   - Als dit lukt, verandert de status in &quot;Succes&quot; (groen vinkje ✓ ).
   - Als dit mislukt, verandert de status in &#39;&#39;Mislukt&#39;&#39; (rood kruis ✗ ). Klik **Logboeken van de Download** om de foutendetails te bekijken.

     ![ Succes van de Pijpleiding ](/help/forms/assets/pipeline-suceess.png)

U kunt nu de Forms Communications API&#39;s testen. Voor testdoeleinden kunt u de API&#39;s aanroepen met de Postman, curl of een andere REST-client.

### Stap 7: API-specificaties en tests

Nu uw omgeving is geconfigureerd, kunt u de communicatie-API&#39;s van AEM Forms starten met het testen van de communicatie-API&#39;s van Swagger UI of via programmacode door de toepassing NodeJS te ontwikkelen.

>[!BEGINTABS]

>[!TAB  A. Gebruikersinterface voor API-tests gebruiken ]

De wagger UI verstrekt een interactieve interface voor het testen APIs zonder code te schrijven.Gebruik **probeert het** eigenschap om [ te roepen en te testen produceert de Communicatie API van PDF ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm) Forms.

1. Navigeer aan [ Communicatie API Verwijzing van Forms ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) en open de [ Communicatie API van Forms ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document) documentatie in uw browser.
2. Breid de **sectie van de Generatie van het 0} Document uit en selecteer** produceert een invulbare vorm van PDF van een malplaatje XDP of van PDF, naar keuze met gegevens die [ samenvoegen.](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm)
3. In de juiste ruit, klik **probeert het**.

   ![ Testen van de Wagger voor API ](/help/forms/assets/api-doc-generation.png)
4. Voer de volgende waarden in:

   | **Sectie** | **Parameter** | **Waarde** |
   |--------------|---------------|------------|
   | emmer | AEM-exemplaar | AEM-instantienaam zonder de Adobe-domeinnaam (`.adobeaemcloud.com`). Gebruik bijvoorbeeld `pXXXXX-eYYYYY` als emmertje. |
   | Beveiliging | Dragertoken | Gebruik het [ toegangstoken van de Server-aan-Server referentie van het Project van Adobe Developer Console ](/help/forms/oauth-api-authetication.md#how-to-generate-an-access-token-using-oauth-server-to-server-authentication) |
   | Lichaam | template | Upload een XDP om het PDF-formulier te genereren. Bijvoorbeeld, kunt u [ dit XDP ](/help/forms/assets/ClosingForm.xdp) gebruiken om een PDF te produceren. |
   | Lichaam | data | Een optioneel XML-bestand met de gegevens die met de sjabloon moeten worden samengevoegd om een voorgevuld PDF-formulier te genereren. Bijvoorbeeld, kunt u [ dit XML ](/help/forms/assets/ClosingForm.xml) gebruiken om een PDF te produceren. |
   | Parameters | X-Adobe-Accept-Experimental | 1 |

5. Klik **verzenden** om API aan te halen

   ![ verzend API ](/help/forms/assets/api-send.png)

6. Controleer de reactie in het **lusje van de Reactie**:
   - Als de antwoordcode `200` is, betekent dit dat de PDF is gemaakt.
   - Als de antwoordcode `400` is, betekent dit dat de aanvraagparameters ongeldig of onjuist zijn geformuleerd.
   - Als de antwoordcode `500` is, betekent dit dat er een interne serverfout is.
   - Als de antwoordcode `403` is, betekent dit dat er een machtigingsfout is.

   In dit geval is de antwoordcode `200` , hetgeen betekent dat de PDF is gegenereerd:

   ![ Reactie van het Overzicht ](/help/forms/assets/api-success.png)

   Nu, kunt u [ gecreeerde PDF ](/help/forms/assets/create-pdf.pdf) downloaden gebruikend de **3} knoop van de Download {en het bekijken in de kijker van PDF:**

   ![ Mening PDF ](/help/forms/assets/create-pdf.png)

   >[!NOTE]
   >
   > Voor testende doeleinden, kunt u [ Postman ](https://www.postman.com/), [ krullen ](https://curl.se/), of een andere cliënt van de WEERSTING ook gebruiken om AEM APIs aan te halen.

>[!TAB  B. Programmatiatically door Toepassing NodeJS te ontwikkelen ]

Ontwikkel een toepassing Node.js om een invulbare vorm van PDF van een **XDP** malplaatje en een **dossier van XML** te produceren dat het **Document Services API** gebruikt

**Eerste vereisten**

- Knooppunt.js geïnstalleerd op uw systeem
- Active AEM as a Cloud Service-exemplaar
- Dragertoken voor API-verificatie van Adobe Developer Console
- Voorbeeld-XDP-bestand: [ ClosingForm.xdp ](/help/forms/assets/ClosingForm.xdp)
- Het Dossier van XML van de steekproef: [ ClosingForm.xml ](/help/forms/assets/ClosingForm.xml)

Als u de toepassing Node.js wilt ontwikkelen, volgt u de stapsgewijze ontwikkeling:

**Stap 1: Creeer een Nieuw Project Node.js**

Open de cmd/terminal en voer de volgende bevelen uit:

```bash
# Create a new directory
mkdir demo-nodejs-generate-pdf
cd demo-nodejs-generate-pdf

##### Initialize Node.js project
npm init -y
```

![ creeer nieuw knoop js project ](/help/forms/assets/api-1.png)

**Stap 2: Installeer Vereiste Afhankelijkheden**

Installeer de **knoop-haal**, **dotenv**, en **vorm-gegevens** bibliotheken om HTTP- verzoeken te maken, milieu variabelen te lezen, en vormgegevens respectievelijk te behandelen.

```bash
npm install node-fetch
npm install dotenv
npm install form-data
```

![ installeer npm gebiedsdelen ](/help/forms/assets/api-2.png)

**Stap 3: Update package.json**

1. Open cmd/terminal en stel het bevel in werking:

   ```bash
   code .
   ```

   ![ open project in redacteur ](/help/forms/assets/api-3.png)

   Het opent het project in de coderedacteur.

2. Werk het `package.json` -bestand bij om het `type` to `module` -bestand toe te voegen.

   ```bash
   {
   "name": "demo-nodejs-generate-pdf",
   "version": "1.0.0",
   "type": "module",
   "main": "index.js",
   }
   ```

   ![ update pakketdossier ](/help/forms/assets/api-4.png)

**Stap 4: Creeer een .env- Dossier**

1. .env dossier op het wortelniveau van een project tot stand brengen
2. Voeg de volgende configuratie toe en vervang placeholders met de daadwerkelijke waarden van OAuth van het Project van ADC Server-aan-Server referentie.

   ```bash
   CLIENT_ID=<ADC Project OAuth Server-to-Server credential ClientID>
   CLIENT_SECRET=<ADC Project OAuth Server-to-Server credential Client Secret>
   SCOPES=<ADC Project OAuth Server-to-Server credential Scopes>
   ```

   ![ creeer env- dossier ](/help/forms/assets/api-5.png)

   >[!NOTE]
   >
   > U kunt de `CLIENT_ID` , `CLIENT_SECRET` en `SCOPES` van het Adobe Developer Console-project kopiëren.

**Stap 5: Creeer src/index.js**

1. `index.js` -bestand maken op het hoofdniveau van het project
2. Voeg de volgende code toe en vervang de plaatsaanduidingen door de werkelijke waarden:

```javascript
// Import the dotenv configuration to load environment variables from the .env file
import "dotenv/config";

// Import fetch for making HTTP requests
import fetch from "node-fetch";
import fs from "fs";
import FormData from "form-data";

// REPLACE THE FOLLOWING VALUE WITH YOUR OWN
const bucket = <bucket-value>; // Your AEM Cloud Service Bucket name
const xdpFilePath = <xdp-file>;
const xmlFilePath = <xml-file>;

// Load environment variables
const clientId = process.env.CLIENT_ID;
const clientSecret = process.env.CLIENT_SECRET;
const scopes = process.env.SCOPES;

// Adobe IMS endpoint for obtaining an access token
const adobeIMSV3TokenEndpointURL = "https://ims-na1.adobelogin.com/ims/token/v3";

// Function to get an access token
const getAccessToken = async () => {
    console.log("Getting access token from IMS...");

    const options = {
        method: "POST",
        headers: {
            "Content-Type": "application/x-www-form-urlencoded",
        },
        body: `grant_type=client_credentials&client_id=${clientId}&client_secret=${clientSecret}&scope=${scopes}`,
    };

    const response = await fetch(adobeIMSV3TokenEndpointURL, options);
    const responseJSON = await response.json();

    console.log("Access token received.");
    return responseJSON.access_token;
};

// Function to generate PDF form from XDP and XML
const generatePDF = async () => {
    const accessToken = await getAccessToken();

    console.log("Generating PDF form from XDP and XML...");

    // Read XDP and XML files
    const xdpFile = fs.readFileSync(xdpFilePath);
    const xmlFile = fs.readFileSync(xmlFilePath);

    const url = `https://${bucket}.adobeaemcloud.com/adobe/document/generate/pdfform`;

    const formData = new FormData();
    formData.append("template", xdpFile, {
        filename: "form.xdp",
        contentType: "application/vnd.adobe.xdp+xml"
    });
    formData.append("data", xmlFile, {
        filename: "data.xml",
        contentType: "application/xml"
    });

    const response = await fetch(url, {
        method: "POST",
        headers: {
            Authorization: `Bearer ${accessToken}`,
            "X-Api-Key": clientId,
            "X-Adobe-Accept-Experimental": "1",
            ...formData.getHeaders()
        },
        body: formData,
    });

    if (response.ok) {
        const arrayBuffer = await response.arrayBuffer();
        fs.writeFileSync("generatedForm.pdf", Buffer.from(arrayBuffer));
        console.log("✅ PDF form generated successfully (saved as generatedForm.pdf)");
    } else {
        console.error("❌ Failed to generate PDF. Status:", response.status);
        console.error(await response.text());
    }
};

// Run the PDF generation function
generatePDF();
```

![ creeer index.js ](/help/forms/assets/api-6.png)

**Stap 6: Looppas de Toepassing**

```bash
node src/index.js
```

![ looppas toepassing ](/help/forms/assets/api-7.png)

De PDF wordt gemaakt in de map `demo-nodejs-generate-pdf` . Navigeer naar de map om het gegenereerde bestand met de naam `generatedForm.pdf` te zoeken.

![ mening creeerde pdf ](/help/forms/assets/api-8.png)

![ Mening PDF ](/help/forms/assets/create-pdf.png)

>[!ENDTABS]

U kunt [ geproduceerde PDF ](/help/forms/assets/create-pdf.png) openen om het te bekijken.

## Problemen oplossen

### Vaak voorkomende problemen en mogelijke oorzaken

#### Versie 1: 403 Verboden fout

**Symptomen:**

- API-aanvragen worden geretourneerd `403 Forbidden`
- Het bericht van de fout: *Onbevoegde Toegang*

**Mogelijke Oorzaak:**

- Client-id niet geregistreerd in de configuratie `api.yaml` van de AEM-instantie

#### Versie 2: 401 niet-geautoriseerde fout

**Symptomen:**

- API-aanvragen worden geretourneerd `401 Unauthorized`
- Het bericht van de fout: *Ongeldig of verlopen teken*

**Mogelijke Oorzaken:**

- Toegangstoken is verlopen (alleen geldig gedurende 24 uur)
- Onjuiste of onjuiste client-id en clientgeheim

#### Versie 3: fout 404 niet gevonden

**Symptomen:**

- API-aanvragen worden geretourneerd `404 Not Found`
- Het bericht van de fout: *Middel vond niet* of *API eindpunt niet*

**Mogelijke Oorzaak:**

- Onjuiste emmerparameter (komt niet overeen met AEM-instantie-id)

#### Probleem 4: implementatiefouten van pijplijn

**Symptomen:**

- Uitvoering van configuratiepipet mislukt
- In implementatielogboeken worden fouten met betrekking tot `api.yaml` weergegeven

**Mogelijke Oorzaken:**

- Ongeldige YAML-syntaxis (problemen met de inspringing, quoting of arrayindeling)
- `api.yaml` in onjuiste map geplaatst
- Onjuiste of onjuiste client-id in de configuratie
- Ongeldig clientgeheim

#### Probleem 5: communicatie-API&#39;s van Forms worden niet uitgevoerd

**Symptomen:**

- API-aanvragen retourneren fouten die aangeven dat er niet-ondersteunde of niet-beschikbare functies zijn.
- PDF genereren met XDP en XML werkt niet.
- De plaatsing van de pijpleiding voltooit met succes, maar runtime API vraag ontbreekt.

**Mogelijke Oorzaak:**

In de AEM-omgeving wordt een versie uitgevoerd die is uitgebracht voordat Forms Communication-API&#39;s zijn geïntroduceerd of ondersteund.
Om het milieu van AEM bij te werken verwijs naar de [ instantie van AEM van de Update ](#update-aem-instance) sectie.

## AEM-instantie bijwerken

U kunt als volgt het AEM-exemplaar bijwerken om Omgevingsdetails te zoeken:

1. Selecteer het `ellipsis` (...) pictogram naast de milieunaam en klik **Update**
2. Klik **voorleggen** knoop en stel de voorgestelde FullstackPipeline in werking.

   ![ Milieu van de Update ](/help/forms/assets/update-env.png)

## Verwante artikelen

- Leren hoe te opstellingsmilieu voor Partij (Asynchrone APIs), zie [ AEM Forms as a Cloud Service Communicatie Batch-verwerking ](/help/forms/aem-forms-cloud-service-communications-batch-processing.md).