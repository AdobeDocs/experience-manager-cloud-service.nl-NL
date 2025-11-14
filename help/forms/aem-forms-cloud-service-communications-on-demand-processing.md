---
title: Hoe stellen Interactieve Communicatie Synchrone APIs?
description: Ontwikkelomgeving instellen voor interactieve communicatie-synchrone API's voor Adobe Experience Manager Forms as a Cloud Service
role: Admin, Developer, User
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
index: false
source-git-commit: cb69041ff59ba1ff586e8c1c71090cc2eb9ad453
workflow-type: tm+mt
source-wordcount: '2573'
ht-degree: 0%

---


# AEM Forms as a Cloud Service Communications Synchronous APIs Processing

Deze handleiding bevat uitgebreide instructies voor het instellen en gebruiken van AEM Forms Communications Synchronous API&#39;s.

Leer hoe u uw AEM as a Cloud Service-omgeving configureert, API-toegang inschakelt en communicatie-API&#39;s oproept met de OAuth Server-to-Server-verificatie.

## Vereisten

Als u een omgeving wilt instellen voor het uitvoeren en testen van AEM Forms Communications API&#39;s, moet u het volgende doen:

### Toegang en machtigingen

Zorg ervoor u de vereiste toegangsrechten en toestemmingen hebt alvorens u begint de Mededelingen APIs te vormen.

**Gebruiker en roltoestemmingen**

- Adobe ID die in [&#x200B; https://account.adobe.com/ &#x200B;](https://account.adobe.com/) wordt gecreeerd
- Adobe ID die is gekoppeld aan de e-mail van uw organisatie
- Adobe Managed Services-productcontext toegewezen
- Ontwikkelaarsrol toegewezen in Adobe Admin Console
- Toestemming om projecten te maken in de Adobe Developer Console

>[!NOTE]
>
> Meer leren over het toewijzen van rollen en het verlenen van toegang tot gebruikers, verwijs naar het artikel [&#x200B; gebruikers en rollen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-manager/content/requirements/users-and-roles) toevoegen.

**Toegang van Cloud Manager**

- Login geloofsbrieven voor [&#x200B; Cloud Manager &#x200B;](https://my.cloudmanager.adobe.com)
- Toegang tot het weergeven en beheren van de omgevingen van uw programma
- Toestemming om CI/CD-pijpleidingen te creëren en te leiden
- Toegang tot omgevingsdetails en configuratie

**Toegang van de Bewaarplaats van de it**

- Toegang tot Cloud Manager Git Repository
- Referenties ophalen voor klonen en wijzigingen doorvoeren

### Ontwikkelingsinstrumenten

- **Node.js** voor het runnen van steekproeftoepassingen
- Laatste versie van **Git**
- Toegang tot **terminal/de lijn van het Bevel**
- **redacteur van de Tekst of winde** voor het uitgeven van configuratiedossiers (de Code van VS, IntelliJ, enz.)
- **Postman** of gelijkaardig hulpmiddel voor API het testen

>[!NOTE]
>
> Dit is een eenmalig proces per omgevingsproces dat moet worden voltooid voordat AEM Forms Communications API&#39;s kunnen worden ingesteld.

Laten we nu elke stap in detail begrijpen.

### Stap 1: AEM-exemplaar bijwerken

Het AEM-exemplaar bijwerken:

1. **Logboek in Adobe Cloud Manager**
   1. Ga aan [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com)
   2. Meld u aan bij uw Adobe ID

2. **ga aan het Overzicht van het Programma**
   1. Selecteer uw programma in de lijst. U wordt omgeleid naar de pagina Program Overview

3. **plaats de Details van het Milieu**
   1. Selecteer het `ellipsis` (...) pictogram naast de milieunaam en klik **Update**
   2. Klik **voorleggen** knoop en stel de voorgestelde FullstackPipeline in werking.

      ![&#x200B; Milieu van de Update &#x200B;](/help/forms/assets/update-env.png)

### Stap 2: gegevensopslagruimte voor klonen

Kloont de Cloud Manager Git Repository om uw API-configuratiebestanden te beheren.

1. **plaats van de Sectie van de Bewaarplaats**
   1. Op de **pagina van het Overzicht van het 0&rbrace; Programma, klik de** Bewaarplaatsen **tabel**
   2. Zoek de naam van de opslagplaats en klik op het weglatingenmenu (...)
   3. De URL van de gegevensopslagruimte kopiëren

      >[!NOTE]
      >
      > De URL-indeling is doorgaans `https://git.cloudmanager.adobe.com/<org>/<program>/`

2. **Kloon die het Bevel van het Git gebruiken**

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
      https://git.cloudmanager.adobe.com/formsinternal01/AEMFormsInternal-ReleaseSanity-p43162-uk59167/
      ```

      ![&#x200B; Klonend de Bewaarplaats van de it &#x200B;](/help/forms/assets/repo-clone.png)


**de Opties van de Integratie van de Bewaarplaats van de it**

Adobe Cloud Manager biedt ondersteuning voor beide opslagplaatsingsopties:

- **direct gebruik van het Bewaarplaats van de Bewaarplaats van het Git van Cloud Manager**
   - Native Cloud Manager Git-opslagplaats gebruiken
   - Ingebouwde integratie met pijpleidingen

- **Integratie met Customer-Beheerde Bewaarplaats van de it**
   - Sluit uw eigen Git-opslagplaats aan (GitHub, GitLab, Bitbucket, enz.)
   - Synchronisatie met Adobe Cloud Manager configureren

Meer leren op hoe te om Adobe Cloud Manager en Adobe Cloud Manager te integreren, zie {de Documentatie van de Integratie van 0} it [.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/managing-code/git-integration.html)

### Stap 3: Toegang tot AEM Cloud Service Environment en AEM Forms Endpoint

Open de omgevingsgegevens van de AEM Cloud Service om de URL&#39;s en id&#39;s te verkrijgen die nodig zijn voor de API-configuratie.

1. **Logboek in Adobe Cloud Manager**
   1. Ga aan [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com)
   2. Meld u aan bij uw Adobe ID

2. **ga aan het Overzicht van het Programma**
Selecteer uw programma in de lijst. U wordt omgeleid naar de pagina Program Overview

3. **Toegang en de Omgeving van de Dienst van de Wolk AEM**

   U kunt de details van de AEM Cloud Service Environment weergeven of openen met een van de volgende twee opties:

   - **Optie 1: Van de Pagina van het Overzicht**

      1. Op de **pagina van het Overzicht van het Programma**
      2. Klik **&quot;Milieu&#39;s&quot;** in het linkerzijmenu.  U ziet een lijst met alle omgevingen

         ![&#x200B; Mening Alle Milieu&#39;s &#x200B;](/help/forms/assets/all-env.png)

      3. Klik op de naam van de specifieke omgeving om details weer te geven

         ![&#x200B; Optie1-Milieu Details &#x200B;](/help/forms/assets/option1-env.png)

   - **Optie 2: Van de Sectie van Milieu&#39;s**

      1. Op de pagina Programmaoverzicht
      2. Bepaal de plaats van de **sectie van Milieu&#39;s**
      3. Klik **&quot;tonen allen&quot;** om alle milieu&#39;s te bekijken
      4. Klik het **weglatingsmenu (...)** naast het milieu
         ![&#x200B; Optie1-Milieu Details &#x200B;](/help/forms/assets/option2-env-details.png)
      5. Selecteer **&quot;Details van de Mening&quot;**

         ![&#x200B; Optie1-Milieu Details &#x200B;](/help/forms/assets/option1-env.png)

4. **vind Uw Eindpunt van AEM Forms**

   Van de **detailspagina van het Milieu** Milieu, neem nota van de volgende details:

   **URL van de Dienst van de Auteur**

   - URL: `https://author-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Emmertje: auteur-pXXXXX-YYYY
Voorbeeld: `https://author-p43162-e177398.adobeaemcloud.com`

   **publiceer de Dienst URL**

   - URL: `https://publish-pXXXXX-eYYYYY.adobeaemcloud.com`
   - Emmertje: publish-pXXXXX-YYYY
Voorbeeld: `https://publish-p43162-e177398.adobeaemcloud.com`

>[!NOTE]
>
> Om te zien hoe te om tot het Milieu van de Dienst van de Wolk van de Toegang AEM en Eindpunt van AEM Forms toegang te hebben, zie [&#x200B; het Leiden Documentatie van Milieu&#39;s &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=nl-NL).

### Stap 4: API Access Configuration

Voer de volgende stappen uit om AEM Forms Communications API&#39;s te configureren:

#### 4.1 Adobe Developer Console Project Setup

1. **Toegang Adobe Developer Console**
   1. Ga aan [&#x200B; Adobe Developer Console &#x200B;](https://developer.adobe.com/console)
   2. Meld u aan bij uw Adobe ID

2. **creeer Nieuw Project**
   1. Van de **Snelle sectie van het Begin**, klik **creeer nieuw project**
   2. Een nieuw project wordt gecreeerd met een standaardnaam

      ![&#x200B; creeer ADC Project &#x200B;](/help/forms/assets/adc-home.png)

   3. Klik **uitgeven project** in de hoogste juiste hoek

      ![&#x200B; geef Project &#x200B;](/help/forms/assets/adc-edit-project.png) uit

   4. Geef een betekenisvolle naam op (bijvoorbeeld &quot;formsproject&quot;)
   5. Klik **sparen**

      ![&#x200B; geef de Naam van het Project uit &#x200B;](/help/forms/assets/adc-edit-projectname.png)

#### 4.2 Communicatie-API&#39;s van Forms toevoegen

Afhankelijk van uw vereisten kunt u verschillende AEM Forms Communications API&#39;s toevoegen.

**A. Voor Document Services API&#39;s**

1. Klik **toevoegen API**

   ![&#x200B; voeg api &#x200B;](/help/forms/assets/adc-add-api.png) toe

2. Selecteer **Communicatie APIs van Forms**
   1. In _voeg API_ dialoog toe, filter door **Experience Cloud**
   2. Selecteer **&quot;Communicatie APIs van Forms&quot;**

   ![&#x200B; voeg Communicatie API van Forms toe &#x200B;](/help/forms/assets/adc-add-forms-api.png)


3. Selecteer **Server-aan-Server** authentificatiemethode

   ![&#x200B; Uitgezochte methode van de Authentificatie &#x200B;](/help/forms/assets/adc-add-authentication-method.png)

**B. Voor Forms Runtime API&#39;s**

1. **klik toevoegen API**
   - In uw project, klik **toevoegen API** knoop

   ![&#x200B; voeg api &#x200B;](/help/forms/assets/adc-add-api.png) toe

2. **Uitgezochte AEM Forms Levering en Runtime API**
   - In _voeg API_ dialoog toe, filter door **Experience Cloud**
   - Selecteer **&quot;AEM Forms Delivery and Runtime API&quot;**
   - Klik **daarna**

   ![&#x200B; voeg runtime API &#x200B;](/help/forms/assets/add-runtime-api.png) toe


3. **Methode van de Authentificatie**
   - Selecteer **Server-aan-Server** authentificatiemethode.


   ![&#x200B; Uitgezochte methode van de Authentificatie &#x200B;](/help/forms/assets/add-authentication-for-runtime-apis.png)

#### 4.3 Productprofiel toevoegen

Ga als volgt te werk om het productprofiel toe te voegen:

1. Selecteer het aangewezen **Profiel van het Product** dat op vereist toegangsniveau wordt gebaseerd:

   | Toegangstype | Productprofiel |
   |------------------|----------------------|
   | Alleen-lezen toegang | `AEM Users - author - Program XXX - Environment XXX` |
   | Toegang lezen/schrijven | `AEM Assets Collaborator Users - author - Program XXX - Environment XXX` |
   | Volledige administratieve toegang | `AEM Administrators - author - Program XXX - Environment XXX` |

2. Selecteer het **Profiel van het Product** dat uw Dienst URL van de Auteur (`https://author-pXXXXX-eYYYYY.adobeaemcloud.com`) aanpast. Selecteer bijvoorbeeld `https://author-pXXXXX-eYYYYY.adobeaemcloud.com` .

3. Klik **sparen gevormde API**. De API en het Profiel van het Product worden toegevoegd aan uw project

   ![&#x200B; Uitgezochte Configuratie van het Project &#x200B;](/help/forms/assets/adc-add-product-profile.png)

#### 4.4 Referenties genereren en opslaan

1. **toegang tot Uw geloofsbrieven**

   1. Ga naar uw project in Adobe Developer Console
   2. Klik op **Server-aan-Server** referentie
   3. Bekijk de **Credentials details** sectie

   ![&#x200B; Credentials van de Mening &#x200B;](/help/forms/assets/adc-view-credential.png)

2. **Opname API geloofsbrieven**

   ```text
   API Credentials:
   ================
   Client ID: <your_client_id>
   Client Secret: <your_client_secret>
   Technical Account ID: <tech_account_id>
   Organization ID: <org_id>
   Scopes: AdobeID,openid,read_organizations
   ```

#### 4.5 de Generatie van het Toegangstoken

**A. Voor testen**

Handmatig toegangstokens genereren in Adobe Developer Console:

1. **ga aan uw Project**
   1. Open uw project in Adobe Developer Console
   2. Klik **Server-aan-Server**

2. **produceer het Token van de Toegang**
   1. Klik **&quot;produceer toegangstoken&quot;** knoop in de API van uw project sectie
   2. Het gegenereerde toegangstoken kopiëren

   ![&#x200B; produceer het Token van de Toegang &#x200B;](/help/forms/assets/adc-access-token.png)

   >[!NOTE]
   >
   > Het teken van de toegang is geldig voor **24 uren**

**B. Voor productie**

Tkens programmatisch genereren met de opdracht cURL:

**Vereiste Referenties:**

- Client-id
- Clientgeheim
- Bereiken (doorgaans: `AdobeID,openid,read_organizations`)

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

#### 4.6 Client-id registreren bij AEM-omgeving

Om identiteitskaart van de Cliënt van uw ADC Project toe te laten om met de instantie van AEM te communiceren, moet u het registreren gebruikend een YAML configuratiedossier en het opstellen via een Pijpleiding Config.

1. **plaats of creeer Folder Config**

   1. Navigeer naar de gekloonde AEM Project-opslagplaats en ga naar de map `config` .
   2. Als het niet bestaat, creeer het op het niveau van de projectwortel:

   ```bash
   mkdir config
   ```

2. Maak een nieuw bestand met de naam `api.yaml` in de map `config` :

   ```bash
   touch config/api.yaml
   ```

3. Voeg de volgende code toe aan het `api.yaml` -bestand:

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

   Voeg bijvoorbeeld `allowedClientIDs` as `6bc4589785e246eda29a545d3ca55980` en envTypes als `dev` toe:

   ![&#x200B; Toevoegend het dossier Config &#x200B;](/help/forms/assets/create-api-yaml-file.png)

4. **zet en duw Veranderingen** vast

   1. Navigeer naar de hoofdmap van uw gekloonde opslagplaats en voer de onderstaande opdrachten uit:


   ```bash
       git add config/api.yaml
       git commit -m "Whitelist client id for api invocation"
       git push origin <your-branch>
   ```

   ![&#x200B; de Veranderingen van de Git van de Duw &#x200B;](/help/forms/assets/push-yaml-changes-in-git.png)


5. **Opstelling Config Pipeline**

   1. **Logboek in Cloud Manager**
      1. Ga aan [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com)
      2. Meld u aan bij uw Adobe ID

   2. **ga aan Uw Programma**
Selecteer uw programma in de lijst en u wordt omgeleid op de pagina van het Overzicht van het Programma

   3. **plaats van de Kaart van Pijpleidingen**
      1. Bepaal de plaats van **Pijpleidingen** kaart op de pagina van het Overzicht van het Programma
      1. Klik **&quot;toevoegen&quot;** knoop

   4. **Uitgezochte Type van Pijpleiding**

      - **voor de milieu&#39;s van de Ontwikkeling**: Selecteer **&quot;voeg niet-productiepijpleiding toe&quot;**. Niet-productiepijpleidingen zijn bestemd voor ontwennings- en werkruimten

      - **voor de milieu&#39;s van de Productie**: Selecteer **&quot;Voeg de Pijpleiding van de Productie toe&quot;**. Voor productiepijpleidingen zijn aanvullende goedkeuringen vereist

        >[!NOTE]
        >
        > In dit geval, creeer een niet-Productiepijpleiding aangezien een ontwikkelomgeving beschikbaar is.

   5. **vorm Pijpleiding - het Lusje van de Configuratie**

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

      ![&#x200B; Config Pijpleiding &#x200B;](/help/forms/assets/add-config-pipeline.png)

   6. **vorm Pijpleiding - het Lusje van de Code van Source**

      In het **lusje van de Code van 0&rbrace; Source:**

      a. **Type van Plaatsing**
      - Selecteer **&quot;gerichte plaatsing&quot;**

      b. **Opties van de Plaatsing**
      - Selecteer **&quot;Config&quot;** (stel configuratiedossiers slechts op). Het vertelt Cloud Manager dit een config plaatsing is.

      c. **Uitgezochte In aanmerking komende Milieu van de Plaatsing**
      - Kies het milieu waar u config wilt opstellen. In dit geval is dit een `dev` -omgeving.

      d. **bepaal de Details van de Code van Source**

      - **Bewaarplaats**: Selecteer de bewaarplaats die uw `api.yaml` dossier bevat. Selecteer bijvoorbeeld de `AEMFormsInternal-ReleaseSanity-p43162-uk59167` repository.
      - **Tak van de Git**: Selecteer uw tak. In dit geval wordt de code bijvoorbeeld geïmplementeerd in de `main` -vertakking.
      - **Plaats van de Code**: ga de weg aan `config` folder in. Terwijl `api.yaml` zich in de `config` -map bij de hoofdmap bevindt, voert u `/config` in

      e. Klik **&quot;sparen&quot;** om de pijpleiding tot stand te brengen

      ![&#x200B; Config Pijpleiding &#x200B;](/help/forms/assets/confirm-pipeline-1.png)

6. **stelt Configuratie** op

   Nu de pijplijn wordt gecreeerd, stel uw `api.yaml` configuratie op:

   1. **van het Overzicht van Pijpleidingen**
      1. Voor de pagina van het Overzicht van het Programma, bepaal de plaats van de **Pijpleidingen** kaart
      2. Navigeer aan uw onlangs gecreeerd config pijpleiding in de lijst. Bijvoorbeeld, zoek de pijpleidingsnaam u creeerde (b.v., &quot;api-config-pijpleiding&quot;). U kunt pijpleidingsdetails met inbegrip van status en laatste looppas zien.

   2. **Begin de Plaatsing**
      1. Klik **&quot;bouwen&quot;** knoop (of speel pictogram ▶) naast uw pijpleiding
      2. Bevestig de plaatsing indien ertoe aangezet en de pijpleidingsuitvoering begint

      ![&#x200B; stel de pijpleiding &#x200B;](/help/forms/assets/run-config-pipeline.png) in werking

   3. **verifieer Succesvolle Plaatsing**
      - Wacht op de pijpleiding om te voltooien.
         - Als dit lukt, verandert de status in &quot;Succes&quot; (groen vinkje ✓ ).
         - Als dit mislukt, verandert de status in &#39;&#39;Mislukt&#39;&#39; (rood kruis ✗ ). Klik **Logboeken van de Download** om de foutendetails te bekijken.

           ![&#x200B; Succes van de Pijpleiding &#x200B;](/help/forms/assets/pipeline-suceess.png)

      U kunt nu de Forms Communications API&#39;s testen. Voor testdoeleinden kunt u de API&#39;s aanroepen met de Postman, curl of een andere REST-client.

### Stap 5: API-specificaties en tests

Nu uw milieu wordt gevormd, kunt u beginnen de Communicatie van AEM Forms APIs te testen of gebruikend [&#x200B; Vwagen UI &#x200B;](#a-using-swagger-ui-for-api-testing) of programmatically door toepassing te ontwikkelen NodeJS.

In dit voorbeeld kunnen we een PDF genereren met behulp van de Document Services API&#39;s met de sjabloon en het XDP-bestand.

#### A. Het gebruiken van Swagger UI voor API het Testen

De wagger UI verstrekt een interactieve interface voor het testen APIs zonder code te schrijven.Gebruik **probeert het** eigenschap om [&#x200B; te roepen en te testen produceert de Dienst API van het Document van PDF &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm).

1. Navigeren naar API-documentatie
   - Forms API: [&#x200B; Forms API Verwijzing &#x200B;](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
   - Document Services: [&#x200B; de Verwijzing van de Diensten API van het Document &#x200B;](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)
Open de [&#x200B; Document Services APIs &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document) documentatie in uw browser.
2. Breid de **sectie van de Generatie van het 0&rbrace; Document uit en selecteer** produceert een invulbare vorm van PDF van een malplaatje XDP of van PDF, naar keuze met gegevens die [&#x200B; samenvoegen.](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/#operation/renderPDFForm)
3. In de juiste ruit, klik **probeert het**.

   ![&#x200B; Testen van de Wagger voor API &#x200B;](/help/forms/assets/api-doc-generation.png)
4. Voer de volgende waarden in:

   | **Sectie** | **Parameter** | **Waarde** |
   |--------------|---------------|------------|
   | emmer | AEM-exemplaar | AEM-instantienaam zonder de Adobe-domeinnaam (`.adobeaemcloud.com`). Gebruik bijvoorbeeld `p43162-e177398` als emmertje. |
   | Beveiliging | Dragertoken | Gebruik het toegangstoken van de Server-aan-Server referentie van het Project van Adobe Developer Console |
   | Lichaam | template | Upload een XDP om het PDF-formulier te genereren. Bijvoorbeeld, kunt u [&#x200B; dit XDP &#x200B;](/help/forms/assets/ClosingForm.xdp) gebruiken om een PDF te produceren. |
   | Lichaam | data | Een optioneel XML-bestand met de gegevens die met de sjabloon moeten worden samengevoegd om een voorgevuld PDF-formulier te genereren. Bijvoorbeeld, kunt u [&#x200B; dit XML &#x200B;](/help/forms/assets/ClosingForm.xml) gebruiken om een PDF te produceren. |
   | Parameters | X-Adobe-Accept-Experimental | 1 |

5. Klik **verzenden** om API aan te halen

   ![&#x200B; verzend API &#x200B;](/help/forms/assets/api-send.png)

6. Controleer de reactie in het **lusje van de Reactie**:
   - Als de antwoordcode `200` is, betekent dit dat de PDF is gemaakt.
   - Als de antwoordcode `400` is, betekent dit dat de aanvraagparameters ongeldig of onjuist zijn geformuleerd.
   - Als de antwoordcode `500` is, betekent dit dat er een interne serverfout is.

   In dit geval is de antwoordcode `200` , hetgeen betekent dat de PDF is gegenereerd:

   ![&#x200B; Reactie van het Overzicht &#x200B;](/help/forms/assets/api-success.png)

   Nu, kunt u [&#x200B; gecreeerde PDF &#x200B;](/help/forms/assets/create-pdf.pdf) downloaden gebruikend de **3&rbrace; knoop van de Download &lbrace;en het bekijken in de kijker van PDF:**

   ![&#x200B; Mening PDF &#x200B;](/help/forms/assets/create-pdf.png)

>[!NOTE]
>
> Voor testende doeleinden, kunt u [&#x200B; Postman &#x200B;](https://www.postman.com/), [&#x200B; krullen &#x200B;](https://curl.se/), of een andere cliënt van de WEERSTING ook gebruiken om AEM APIs aan te halen.

#### B. Programmaticaal door de Toepassing van NodeJS te ontwikkelen

Ontwikkel een toepassing Node.js om een invulbare vorm van PDF van een **XDP** malplaatje en een **dossier van XML** te produceren dat het **Document Services API** gebruikt

##### Vereisten

- Knooppunt.js geïnstalleerd op uw systeem
- Active AEM as a Cloud Service-exemplaar
- Dragertoken voor API-verificatie van Adobe Developer Console
- Voorbeeld-XDP-bestand: [&#x200B; ClosingForm.xdp &#x200B;](/help/forms/assets/ClosingForm.xdp)
- Het Dossier van XML van de steekproef: [&#x200B; ClosingForm.xml &#x200B;](/help/forms/assets/ClosingForm.xml)

Als u de toepassing Node.js wilt ontwikkelen, volgt u de stapsgewijze ontwikkeling:

##### Stap 1: Creeer een Nieuw project Node.js

Open de cmd/terminal en voer de volgende bevelen uit:

```bash
# Create a new directory
mkdir demo-nodejs-generate-pdf
cd demo-nodejs-generate-pdf

##### Initialize Node.js project
npm init -y
```

![&#x200B; creeer nieuw knoop js project &#x200B;](/help/forms/assets/api-1.png)

##### Stap 2: Vereiste afhankelijkheden installeren

Installeer de **knoop-haal**, **dotenv**, en **vorm-gegevens** bibliotheken om HTTP- verzoeken te maken, milieu variabelen te lezen, en vormgegevens respectievelijk te behandelen.

```bash
npm install node-fetch
npm install dotenv
npm install form-data
```

![&#x200B; installeer npm gebiedsdelen &#x200B;](/help/forms/assets/api-2.png)

##### Stap 3: Update package.json

1. Open cmd/terminal en stel het bevel in werking:

   ```bash
   code .
   ```

   ![&#x200B; open project in redacteur &#x200B;](/help/forms/assets/api-3.png)

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

   ![&#x200B; update pakketdossier &#x200B;](/help/forms/assets/api-4.png)

##### Stap 4: Een .env-bestand maken

1. .env dossier op het wortelniveau van een project tot stand brengen
2. Voeg de volgende configuratie toe en vervang placeholders met de daadwerkelijke waarden van OAuth van het Project van ADC Server-aan-Server referentie.

   ```bash
   CLIENT_ID=<ADC Project OAuth Server-to-Server credential ClientID>
   CLIENT_SECRET=<ADC Project OAuth Server-to-Server credential Client Secret>
   SCOPES=<ADC Project OAuth Server-to-Server credential Scopes>
   ```

   ![&#x200B; creeer env- dossier &#x200B;](/help/forms/assets/api-5.png)

   >[!NOTE]
   >
   > U kunt de `CLIENT_ID` , `CLIENT_SECRET` en `SCOPES` van het Adobe Developer Console-project kopiëren.

##### Stap 5: src/index.js maken

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

![&#x200B; creeer index.js &#x200B;](/help/forms/assets/api-6.png)

##### Stap 6: Voer de toepassing uit

```bash
node src/index.js
```

![&#x200B; looppas toepassing &#x200B;](/help/forms/assets/api-7.png)

De PDF wordt gemaakt in de map `demo-nodejs-generate-pdf` . Navigeer naar de map om het gegenereerde bestand met de naam `generatedForm.pdf` te zoeken.

![&#x200B; mening creeerde pdf &#x200B;](/help/forms/assets/api-8.png)

U kunt [&#x200B; geproduceerde PDF &#x200B;](/help/forms/assets/create-pdf.png) openen om het te bekijken.

## Problemen oplossen

### Vaak voorkomende problemen en mogelijke oorzaken

#### Versie 1: 403 Verboden fout

**Symptomen:**

- API-aanvragen worden geretourneerd `403 Forbidden`
- Het bericht van de fout: *Ontkende Toegang* of *Onvoldoende toestemmingen*
- Komt zelfs met een geldig toegangstoken voor

**Mogelijke Oorzaken:**

- Onvoldoende rechten in het productprofiel dat is gekoppeld aan de referentie OAuth Server-to-Server
- De gebruikersgroep van de dienst in de Auteur van AEM mist noodzakelijke toestemmingen op vereiste inhoudspaden

#### Versie 2: 401 niet-geautoriseerde fout

**Symptomen:**

- API-aanvragen worden geretourneerd `401 Unauthorized`
- Het bericht van de fout: *Ongeldig of verlopen teken*

**Mogelijke Oorzaken:**

- Toegangstoken is verlopen (alleen geldig gedurende 24 uur)
- Onjuiste of onjuiste client-id en clientgeheim
- Ontbrekende of onjuist gevormde verificatieheaders in de API-aanvraag

#### Versie 3: fout 404 niet gevonden

**Symptomen:**

- API-aanvragen worden geretourneerd `404 Not Found`
- Het bericht van de fout: *Middel vond niet* of *API eindpunt niet*

**Mogelijke Oorzaken:**

- Client-id niet geregistreerd in de configuratie `api.yaml` van de AEM-instantie
- Onjuiste emmerparameter (komt niet overeen met AEM-instantie-id)
- Ongeldige of niet-bestaande bron-id (formulier of middel)

#### Probleem 4: Optie voor verificatie van server naar server niet beschikbaar

**Symptomen:**

- OAuth Server-to-Server-optie ontbreekt of is uitgeschakeld in Adobe Developer Console

**Mogelijke Oorzaak:**

- Gebruiker die de integratie creeert wordt niet toegevoegd als a **Ontwikkelaar** in het bijbehorende Profiel van het Product

#### Probleem 5: implementatiefouten van pijplijn

**Symptomen:**

- Uitvoering van configuratiepipet mislukt
- In implementatielogboeken worden fouten met betrekking tot `api.yaml` weergegeven

**Mogelijke Oorzaken:**

- Ongeldige YAML-syntaxis (problemen met de inspringing, quoting of arrayindeling)
- `api.yaml` in onjuiste map geplaatst
- Onjuiste of onjuiste client-id in de configuratie


## Verwante artikelen

Leren hoe te opstellingsmilieu voor Partij (Asynchrone APIs), zie [&#x200B; AEM Forms as a Cloud Service Communicatie Batch-verwerking &#x200B;](/help/forms/aem-forms-cloud-service-communications-batch-processing.md).
