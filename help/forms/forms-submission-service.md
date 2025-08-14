---
title: Forms-verzendservice voor Edge Delivery Services
description: Sla formulierverzendingen rechtstreeks op in spreadsheets met de door Adobe gehoste verzendservice van Forms. Leer opstelling, configuratie, en API gebruik voor de Bladen van Google, OneDrive, en de integratie van SharePoint.
keywords: Forms-verzendservice, Edge Delivery Services-formulieren, integratie van werkbladen, Google-werkbladen, OneDrive-formulieren, SharePoint-formulieren, gegevensverzameling
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner, Intermediate
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 07160248d5b5817d155a118475878ce04a687a32
workflow-type: tm+mt
source-wordcount: '1573'
ht-degree: 0%

---

# Forms-verzendservice voor Edge Delivery Services

De Forms-verzendservice is een door Adobe gehoste oplossing waarmee formulierverzendgegevens automatisch rechtstreeks in uw voorkeurspreadsheets worden opgeslagen: Google Sheets, Microsoft OneDrive of SharePoint. Dit elimineert de behoefte aan complexe backend infrastructuur terwijl het verstrekken van gegevens in real time en beheer.

## Overzicht

![ de voorleggingsdienst van Forms ](/help/forms/assets/form-submission-service.png)
*Figuur: Het werkschema van de Dienst van de Verzending van Forms - van vormvoorlegging aan spreadsheetopslag*

+++ Wie moet deze service gebruiken?

**Perfect voor:**

- **creators van de Inhoud** bouwend eenvoudige vormen van de gegevensinzameling
- **Kleine ondernemingen** die snelle vorm-aan-spreadsheetwerkschema&#39;s nodig hebben
- **de teams van de Marketing** verzamelen loodinformatie
- **de organisatoren van de Gebeurtenis** die registraties beheren

**overweeg alternatieven voor:**

- Complexe workflows die aangepaste logica vereisen
- Integratie van bedrijven met databases
- Forms heeft geavanceerde validatie of verwerking nodig

+++

+++ Vaak voorkomende gevallen

| Hoofdletters gebruiken | Voorbeeld | Voordelen voor werkblad |
|----------|---------|-------------------|
| **Contact Forms** | Website vragen → Google Sheets | Eenvoudige follow-up en CRM-import |
| **Registratie van de Gebeurtenis** | Conferentiehandtekeningen → Excel Online | Real-time bijhouden van deelnemers |
| **Loodgeneratie** | Nieuwsbrieven → SharePoint | Analyse van de marketingcampagne |
| **de Inzameling van de Terugkoppeling** | Antwoorden van de enquête → Google-bladen | Snelle gegevensvisualisatie |

+++

## Belangrijkste voordelen

De Forms-verzendservice biedt verschillende voordelen voor gestroomlijnde gegevensverzameling:

+++ Vereenvoudigde installatie

- **Geen backend infrastructuur** wordt vereist - de gastheren van Adobe het voorleggingseindpunt
- **Directe integratie** met populaire spreadsheetplatforms
- **Automatische gegevenstoewijzing** van vormgebieden aan spreadsheetkolommen

+++


+++ Real-Time gegevensbeheer

- **Onmiddellijke gegevens vangen** - de bijdragen verschijnen onmiddellijk in uw spreadsheet
- **Gestructureerde opslag** - georganiseerde kolommen voor gemakkelijke analyse
- **Levende samenwerking** - de veelvoudige teamleden kunnen tot gegevens toegang hebben en analyseren

+++

+++ Ingebouwde beveiliging en toegangsbeheer

- **Hefboomwerkingen bestaande toestemmingen** - gebruik de het delen van uw spreadsheetplatform controles
- **Adobe-Beheerde veiligheid** - veilig voorlegging eindpunt met onderneming-rang bescherming
- **Eigendom van Gegevens** - uw gegevensverblijven in uw gekozen spreadsheetplatform

+++

## Vereisten

Voordat u de Forms-verzendservice instelt, moet u controleren of:



+++ Technische vereisten

- **GitHub bewaarplaats** opstelling voor uw project van Edge Delivery Services met het recentste Aangepast geïnstalleerd Blok van Forms
- **goedkeuring van de Toegang** - bewaarplaats die aan de lijst van gewenste personen wordt toegevoegd

+++

+++ Platforminstelling werkblad


Kies een van de ondersteunde platforms:

- **Google Sheets** - de rekening van Google met de toestemmingen van de bladverwezenlijking
- **Microsoft OneDrive** - Microsoft 365 rekening met de Online toegang van Excel
- **SharePoint** - de toegang van SharePoint met lijst/bibliotheektoestemmingen

+++

+++ Machtigingen en toegang

- **geeft toestemmingen** voor het doelspreadsheet uit
- **delend mogelijkheden** om toegang tot `forms@adobe.com` te verlenen
- **toestemmingen van de generatie van de verbinding 0&rbrace; &lbrace;voor uw gekozen platform**

+++

>[!TIP]
>
>**Nieuw aan Edge Delivery Services?** Begin met het [ Begonnen Leerprogramma ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) aan opstelling uw projectstichting.

## Configuratiemethoden

De Forms-verzendservice biedt twee configuratiemethoden. Kies de methode die het beste bij uw workflow past:


+++ Uw configuratiemethode kiezen

| Methode | Best voor | Vereiste tijd | Technisch niveau |
|--------|----------|---------------|-----------------|
| **[Handmatige Opstelling](#manual-configuration)** | Inhoudsmakers, eenmalige installatie | 10-15 minuten | Beginnen |
| **[API Configuratie](#api-configuration)** | Ontwikkelaars, geautomatiseerde workflows | 5-10 minuten | Intermediair |

+++

+++ Projectinstelling

Voordat u een van beide methoden configureert, moet u ervoor zorgen dat uw AEM-projectstichting gereed is:

1. **creeer of werk uw project van AEM** met het recentste Adaptieve Blok van Forms bij ([ Begonnen het Leerprogramma ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial))

2. **Update`fstab.yaml`** in uw projectwortel:

   ```yaml
   # Replace with the path to your shared folder
   mountpoints:
     /: https://drive.google.com/drive/folders/your-shared-folder-id
   ```


3. **deel uw projectomslag** met `forms@adobe.com` (geef vereiste toestemmingen uit)

+++

+++

## Handmatige configuratie

![ Werkschema voor de dienst van de vormenvoorlegging ](/help/forms/assets/forms-submission-service-workflow.png)
*Cijfer: Volledig werkschema voor de handmatige opstelling van de Dienst van de Verzending van Forms*

Voer de volgende stapsgewijze instructies uit om het formulier in te stellen met verzending van werkbladen:



+++ Stap 1: Uw formulierdefinitie maken

Maak uw formulierstructuur met Google Sheets of Microsoft Excel.

**Stappen van de Making van de Vorm:**

1. **open uw spreadsheetplatform** (Google Bladen of Microsoft Excel)
2. **creeer een nieuw spreadsheet** voor uw vormproject
3. **Naam uw blad** (moet of `helix-default` of `shared-aem` zijn)
4. **bepaalt uw vormstructuur** gebruikend de [ gids van de vormverwezenlijking ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)

![ de Definitie van de Vorm ](/help/forms/assets/form-submission-definition.png)
*Voorbeeld: De definitie van de vorm met gebiedstypes, etiketten, en bevestigingsregels*

>[!IMPORTANT]
>
>**het Noemen van het Blad Vereisten**
>
>Het definitieblad van het formulier moet een naam hebben:
>
>- `helix-default` (aanbevolen voor enkele formulieren)
>- `shared-aem` (voor meervoudige projecten)
>
>Andere bladnamen worden niet door het systeem herkend.

**Controlepunt van de Bevestiging:**

- De formulierstructuur is voltooid met alle vereiste velden
- Werkblad krijgt de juiste naam (`helix-default` of `shared-aem`)
- Veldtypen en validatieregels zijn op de juiste wijze geconfigureerd

+++

+++ Stap 2: Maak het werkblad voor gegevensverzameling

Stel een speciaal blad in voor het ontvangen van formulierverzendgegevens.

**Opstelling van het Blad van Gegevens:**

1. **voeg een nieuw blad** aan uw bestaand spreadsheet toe
2. **noem het blad precies`incoming`** (case-sensitive)
3. **de kolomkopballen van de opstelling** die uw vormgebieden aanpassen
4. **sparen spreadsheet** om ervoor te zorgen de veranderingen worden bewaard

![ Binnenkomend blad ](/help/forms/assets/form-submission-incoming-sheet.png)
*Voorbeeld: Binnenkomend blad met kolomkopballen die vormgebieden aanpassen*

>[!WARNING]
>
>**Kritieke Vereiste**
>
>De naam van het blad moet exact `incoming` (kleine letters) zijn. Zonder dit blad:
>
>- Formulieraanvragen worden afgewezen
>- Er worden geen gegevens opgeslagen
>- Gebruikers zien verzendfouten

**Controlepunt van de Bevestiging:**

- `incoming` -werkblad bestaat in het werkblad
- Kolomkoppen komen overeen met uw formulierveldnamen
- Werkblad is op de juiste wijze opgeslagen en toegankelijk

>[!TIP]
>
>**ProUiteinde:** kopieer de nauwkeurige gebiedsnamen van uw vormdefinitie om perfecte aanpassing tussen vormgebieden en spreadsheetkolommen te verzekeren.

+++

+++ Stap 3: Deel spreadsheet met de Dienst van Adobe

Bied de Adobe Forms-verzendservice toegang tot uw spreadsheet.

**het Delen Proces:**

1. **klik de knoop van het Aandeel** in de hoogste juiste hoek van uw spreadsheet
2. **voeg de de dienstrekening van Adobe toe:**
   - E-mail: `forms@adobe.com`
   - Het niveau van de toestemming: **Redacteur** (die voor gegevens wordt vereist schrijven)
3. **verzend de het delen uitnodiging**
4. **exemplaar de spreadsheetverbinding** voor de volgende stap

   ![ Aankomend blad van het Aandeel ](/help/forms/assets/form-submission-share-incoming.png)
   *geleidelijke het delen proces voor het verlenen van de diensttoegang van Adobe*

**Platform-Specifieke Instructies:**

**Google Bladen:**

- `forms@adobe.com` toevoegen als editor
- Zorg ervoor dat &quot;Iedereen met de koppeling kan weergeven&quot; is ingeschakeld
- Kopieer de deelbare koppeling

**Microsoft Excel (OneDrive/SharePoint):**

- `forms@adobe.com` toevoegen met bewerkingsmachtigingen
- Koppeling delen instellen op &quot;Iedereen met de koppeling kan bewerken&quot;
- De URL voor delen kopiëren

  ![ verbinding van het Exemplaar van inkomend blad ](/help/forms/assets/form-submission-copy-link.png)
  *Voorbeeld: Het kopiëren van de shareable verbinding voor vormconfiguratie*

**Controlepunt van de Bevestiging:**

- `forms@adobe.com` heeft Editor toegang tot uw spreadsheet
- De werkbladkoppeling is gekopieerd en klaar voor gebruik
- Met machtigingen voor delen is externe toegang mogelijk

+++

+++ Stap 4: Formulier verbinden met werkblad

Koppel uw formulierdefinitie aan het verzendwerkblad.

**vorm-spreadsheet Verbinding:**

1. **open uw spreadsheet van de vormdefinitie** (met `helix-default` of `shared-aem` blad)
2. **plaats van de Submit veldrij** in uw vormdefinitie
3. **plak de gekopieerde spreadsheetverbinding** in de **kolom van de Actie** voor het Submit gebied
4. **sparen de veranderingen** aan uw vormdefinitie

   ![ Verbinding een spreadsheet ](/help/forms/assets/form-submission-sheet-linking.png)

*Voorbeeld: Verbindend voorlegt actie aan uw spreadsheet van de gegevensinzameling*

**het Publiceren van Uw Vorm:**

1. **Open AEM Sidekick** in uw browser
2. **Voorproef uw vorm** om de configuratie te testen
3. **publiceer de vorm** om het levend te maken

**Definitieve Bevestiging:**

- Werkbladkoppeling wordt correct toegevoegd aan de handeling Veld verzenden
- Formulierdefinitie wordt opgeslagen en gepubliceerd
- Alle velden worden correct weergegeven in het voorbeeld
- Verzendknop is correct geconfigureerd

>[!SUCCESS]
>
>**Opstelling voltooit!** Uw formulier is nu verbonden met de Forms-verzendservice. Test het door voorbeeldgegevens te verzenden en het `incoming` -blad te controleren.

**de Materialen van de Verwijzing:**

- [ Volledige voorbeeldspreadsheet ](/help/forms/assets/spreadsheet.xlsx) met juiste configuratie
- [ documentatie van AEM Sidekick ](https://www.aem.live/docs/sidekick) voor het publiceren van begeleiding

+++

## API-configuratie

Met de API-methode kunnen ontwikkelaars via programmacode gegevens verzenden naar de Forms-verzendservice, ideaal voor geautomatiseerde workflows en aangepaste integraties.


+++ Wanneer gebruikt u de API

**Perfect voor:**

- Geautomatiseerde systemen voor gegevensverzameling
- Aangepaste formulierimplementaties
- Integratie met bestaande toepassingen
- Werkstromen voor bulkgegevensverzending

+++

+++ API-vereisten

Controleer voordat u de API gebruikt of:

- **voltooide de opstelling van het Spreadsheet** (met inbegrip van `incoming` blad)
- **de diensttoegang van Adobe** verleend aan `forms@adobe.com`
- **identiteitskaart van de Vorm** van uw gepubliceerde vorm
- **informatie van de Bewaarplaats** (organisatie en plaatsnaam)

>[!IMPORTANT]
>
>**Vereiste Stappen van de Opstelling**
>
>De API vereist de zelfde spreadsheetopstelling zoals handconfiguratie:
>
>- `incoming` sheet moet bestaan
>- `forms@adobe.com` moet Editor toegang hebben
>- Blad moet via AEM Sidekick worden gepubliceerd

+++

+++ API-eindpunt en verificatie

**Basis URL:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`

**Vereiste Kopballen:**

- `Content-Type: application/json`
- `x-adobe-routing: tier=live,bucket=main--[repository]--[organization]`

**API Documentatie:** [ Volledige API Verwijzing ](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)

+++

+++ Postman gebruiken

Postman biedt een gebruikersvriendelijke interface voor het testen van API-verzendingen.

**Instructies van de Opstelling:**

1. **creeer een nieuw POST verzoek** in Postman
2. **vorm het eindpunt:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`
3. **vervangt placeholders:**
   - `{id}` → Uw huidige formulier-id
   - `[repository]` → De naam van uw GitHub-opslagplaats
   - `[organization]` → Uw GitHub-organisatie/gebruikersnaam

**Configuratie van het verzoek:**

     &quot;json 

https://forms.adobe.com/adobe/forms/af/submit/your-form-id

Kopteksten:
Inhoudstype: application/json
x-adobe-routing: tier=live, bucket=main-your-repo-your-org

Lichaam (JSON):
&lbrace;
&quot;data&quot;: &lbrace;
&quot;startDate&quot;: &quot;2025-01-10&quot;,
&quot;endDate&quot;: &quot;2025-01-25&quot;,
&quot;bestemming&quot;: &quot;Australië&quot;,
&quot;class&quot;: &quot;First Class&quot;,
&quot;budget&quot;: &quot;2000&quot;,
&quot;bedrag&quot;: &quot;1000000&quot;,
&quot;name&quot;: &quot;Mary&quot;,
&quot;leeftijd&quot;: &quot;35&quot;,
&quot;subscribe&quot;: null,
&quot;email&quot;: &quot;mary@gmail.com&quot;
&rbrace;
&rbrace;
&quot;

**Verwachte Reactie:**

- **Code van de Status:** `201 Created`
- **Gegevens verschijnt** in uw `incoming` spreadsheet onmiddellijk

![ postmanscherm ](/help/forms/assets/postman-api.png)
*Voorbeeld: Succesvolle API voorlegging gebruikend de interface van Postman*

+++

+++ Opdrachtregel gebruiken (curl)

Voor ontwikkelaars die terminal/bevelherinnering verkiezen, gebruik krulling om gegevens programmatically voor te leggen.

**Opstelling van de Lijn van het Bevel:**

Vervang de volgende plaatsaanduidingen in de onderstaande opdrachten:

- `{id}` → Uw huidige formulier-id
- `[repository]` → De naam van uw GitHub-opslagplaats
- `[organization]` → Uw GitHub-organisatie/gebruikersnaam

>[!BEGINTABS]

>[!TAB  macOS/Linux ]

```bash
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" \
    --header "Content-Type: application/json" \
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" \
    --data '{
        "data": {
            "startDate": "2025-01-10",
            "endDate": "2025-01-25",
            "destination": "Australia",
            "class": "First Class",
            "budget": "2000",
            "amount": "1000000",
            "name": "Joe",
            "age": "35",
            "subscribe": null,
      "email": "joe@example.com"
                }
            }'
        ```

>[!TAB Windows Command Prompt]

```cmd
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" ^
    --header "Content-Type: application/json" ^
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" ^
  --data "{\"data\": {\"startDate\": \"2025-01-10\", \"endDate\": \"2025-01-25\", \"destination\": \"Australia\", \"class\": \"First Class\", \"budget\": \"2000\", \"amount\": \"1000000\", \"name\": \"Joe\", \"age\": \"35\", \"subscribe\": null, \"email\": \"joe@example.com\"}}"
```

>[!TAB  Vensters PowerShell ]

```powershell
$body = @{
  data = @{
    startDate = "2025-01-10"
    endDate = "2025-01-25"
    destination = "Australia"
    class = "First Class"
    budget = "2000"
    amount = "1000000"
    name = "Joe"
    age = "35"
    subscribe = $null
    email = "joe@example.com"
  }
} | ConvertTo-Json -Depth 3

Invoke-RestMethod -Uri "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" `
  -Method POST `
  -Headers @{"Content-Type"="application/json"; "x-adobe-routing"="tier=live,bucket=main--your-repo--your-org"} `
  -Body $body
    ```

>[!ENDTABS]

+++

+++ API Response & Verification

**Successful Response:**

```http
HTTP/1.1 201 Created
Connection: keep-alive
Content-Length: 0
X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
Date: Fri, 10 Jan 2025 13:06:10 GMT
Access-Control-Allow-Origin: *
```

**Verificatie van Gegevens:**

Controleer na een geslaagde verzending of de gegevens in uw spreadsheet worden weergegeven:

![ bijgewerkt blad ](/help/forms/assets/updated-sheet.png)
*Voorbeeld: Gegevens met succes geschreven aan het inkomende blad via API*

**Bevestiging van de Reactie:**

- **Status van HTTP:** `201 Created` wijst op succesvolle voorlegging
- **x-verzoek-identiteitskaart:** Unieke herkenningsteken voor het volgen van de voorlegging
- **Gegevens verschijnt** in uw `incoming` blad binnen seconden
- **Alle vormgebieden** worden behoorlijk in kaart gebracht aan spreadsheetkolommen

+++

## Problemen oplossen



+++ Algemene problemen en oplossingen

**Probleem: 403 Verboden Fout**

```
Causes: Missing or incorrect access permissions
Solutions:
- Verify forms@adobe.com has Editor access to your spreadsheet
- Check that your repository is added to the allowlist
- Confirm the x-adobe-routing header format
```

**Probleem: 404 niet Gevonden Fout**

```
Causes: Incorrect Form ID or endpoint URL
Solutions:  
- Verify your Form ID is correct
- Check the API endpoint URL format
- Ensure your form is published and live
```


**Probleem: Gegevens verschijnen niet in Spreadsheet**

```
Causes: Missing 'incoming' sheet or permission issues
Solutions:
- Confirm 'incoming' sheet exists (case-sensitive)
- Verify column headers match form field names exactly
- Check forms@adobe.com has edit permissions
- Ensure spreadsheet is shared properly
```


**Probleem: De ongeldige Fout van het Formaat JSON**

```
Causes: Malformed request body
Solutions:
- Validate JSON syntax using online JSON validators
- Ensure proper escaping of special characters
- Check quote marks and brackets are balanced
```


+++

+++ Help opvragen

**Kanalen van de Steun:**

- **Early Access Issues:** Email [ aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)
- **API Documentatie:** [ Verwijzing van de Ontwikkelaar ](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)
- **Communautaire Steun:** [ Gemeenschap van de Liga van de Ervaring van Adobe ](https://experienceleaguecommunities.adobe.com/)

+++

## Volgende stappen

Nu u de gevormde Dienst van de Verzending van Forms hebt, onderzoek deze verwante onderwerpen:


+++ Verbeter je Forms

- **[creeer Geavanceerde Forms ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)** - voeg bevestiging, voorwaardelijke logica, en douane het stileren toe
- **[Gids van de Componenten van de Vorm ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/forms-components)** - onderzoek beschikbare types van vormgebied

+++

+++ Alternatieve verzendmethoden

- **[AEM publiceert Verzending](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)** - voor complexe werkschema&#39;s en ondernemingsintegratie
- **[de Douane legt Acties](/help/forms/configure-submit-actions-core-components.md)** voor - Geavanceerde voorlegging behandeling

+++

+++ Gegevensbeheer

- **[Analytics van de Vorm](/help/forms/view-understand-aem-forms-analytics-reports.md)** - de prestaties en het gebruik van de vorm van het spoor
- **[Integratie van Gegevens](/help/forms/configure-data-sources.md)** - verbind vormen met gegevensbestanden en de systemen van CRM

+++

## Samenvatting

De Forms-verzendservice biedt een krachtige, niet-codeoplossing voor het rechtstreeks verzamelen van formuliergegevens in spreadsheets. Belangrijkste voordelen zijn:

- **Snelle opstelling** - Geen vereiste backendinfrastructuur
- **gegevens in real time** - Onmiddellijke voorlegging vangen
- **Flexibele platforms** - de Bladen van Google, OneDrive, of SharePoint
- **API toegang** - Programmatic voorleggingsmogelijkheden
- **veiligheid van de Onderneming** - Adobe-Beheerde eindpunten met toegangscontroles

**Klaar om te beginnen?** volg de [ handconfiguratie ](#manual-configuration) gids voor een visuele opstelling, of sprong aan [ API configuratie ](#api-configuration) voor programmatic integratie.
