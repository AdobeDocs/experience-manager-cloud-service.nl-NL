---
title: API integreren in de Rule Editor voor Forms
description: Leer over de recentste verhogingen aan de Invoke Dienst in de Redacteur van de Regel, met inbegrip van hoe te om APIs voor Aangepast Forms te integreren die op de Componenten van de Kern wordt gebaseerd zonder een Model van de Gegevens van de Vorm te gebruiken.
feature: Adaptive Forms, Core Components, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
keywords: integreren API in regeleditor, serviceverbeteringen aanroepen
source-git-commit: 5d25204516cb46334c4d594c16852b033f3e6c90
workflow-type: tm+mt
source-wordcount: '1017'
ht-degree: 0%

---


# API integreren in regeleditor

<span> het integreren API in de Redacteur van de Regel is onder het Vroege Programma van de Goedkeuring. U kunt schrijven naar `aem-forms-ea@adobe.com` van uw officiële e-mailadres om deel te nemen aan het vroege adoptieprogramma en om toegang tot het vermogen te vragen.</span>

De Visual Rule Editor in Adaptive Forms ondersteunt directe API-integratie zonder een Form Data Model te maken. U kunt verbinding maken met een API-eindpunt door de API-URL (in JSON-indeling) in te voeren of de configuratie te importeren via een cURL-opdracht. Zodra geïntegreerd, kan de **Invoke Actie van de Dienst** worden gebruikt om API te roepen.

Formuliervelden kunnen rechtstreeks worden toegewezen aan de invoerparameters die zijn gedefinieerd in de API-configuratie. Op dezelfde manier kunnen de outputparameters aan vormgebieden worden in kaart gebracht gebruikend de **optie van de gebeurtenislading** voor de overeenkomstige API reactie.

Bovendien, laat de Visuele Redacteur van de Regel u **succes** en **mislukkingsmanagers** bepalen wanneer het aanhalen van de dienst. Succeshandlers bepalen de handelingen die moeten worden uitgevoerd na een geslaagde API-aanroep, terwijl foutafhandelaars definiëren hoe het formulier moet reageren wanneer een fout optreedt.

>[!NOTE]
>
> API-integratie in de Rule Editor is ook van toepassing op Edge Delivery Services Forms.

## Vergelijking: API-integratiemethoden

| Verhouding | API-integratie met FDM (Form Data Model) | Directe API Integratie (via *creeer API Integratie*) |
|--------------------------------|---------------------------------------------------------------------|-----------------------------------------------------------|
| **Doel** | Gecentraliseerde, herbruikbare API-integratie in meerdere formulieren | Snelle, formulierspecifieke API-integratie |
| **Plaats van de Opstelling** | Gemaakt en bewerkt in de formuliergegevensmodeleditor (AEM-console) | Direct gemaakt en bewerkt in de Editor voor adaptieve formulierregels |
| **Complexiteit** | Hogere installatie-inspanning (vereist toewijzing en configuratie) | Eenvoudig en licht |
| **best geschikt voor** | Gebruiksscenario&#39;s voor grote bedrijven of bedrijven met meerdere formulieren | Kleine formulieren, prototypen of eenmalige API-aanroepen |

## Configuratie API-integratie

In de onderstaande schermafbeelding wordt het configuratievenster voor API-integratie weergegeven:

![ API de Configuratie van de Integratie ](/help/forms/assets/api-integration-configuration.png)

### Opties voor sleutelconfiguratie

**API de Configuratie van de Integratie**

* **Invoer van cURL**: Vorm uw API integratie door een klaar-gemaakt bevel cURL in plaats van manueel het ingaan van details zoals API URL, de methode van HTTP, kopballen, en parameters te kleven.
* **Naam van de Vertoning**: De naam van de Douane voor de API dienst.
* **API URL**: Eindpunt van de API dienst.
* **Uitgezochte Methode van HTTP**: De HTTP- verzoekmethode die wordt gebruikt om API te roepen.
* **Type van Inhoud**: Bepaalt het verzoek en reactieformaat.
* **Vereiste Encryptie**: (Facultatief) verzekert gevoelige gegevens tijdens transmissie worden gecodeerd.
* **Uitvoeren bij Cliënt**: Wanneer toegelaten, wordt de API vraag gemaakt van de cliënt (browser) in plaats van de server.

**Type van Authentificatie**

* **Opties**: Geen, Basis, Sleutel API, OAuth 2.0.

**Parameters van de Input**

* **uploadt JSON voor Input**: Upload een steekproefJSON dossier aan auto-bevolkte inputafbeeldingen.
   * **Naam**: De parameternaam van de input die door API wordt vereist.
   * **Type**: Het type van gegevens van de input (Koord, Aantal, Van Boole, enz.).
   * **in**: Plaats van de parameter (Vraag, Kopbal, of Lichaam).
   * **GebrekWaarde**: Voorgevulde waarde als niet verstrekt door de gebruiker.
   * **voeg** toe: Optie om extra inputparameters toe te voegen.

**Parameters van de Output**

* **uploadt JSON voor Output**: Upload een steekproefAPI reactie aan auto-geproduceerde afbeeldingen.
   * **Naam**: De naam van de parameter van de Output van de API reactie.
   * **Type**: Verwacht gegevenstype van de outputparameter (Koord, Aantal, enz.).
   * **binnen**: bepaalt waar de in kaart gebrachte waarde wordt verwacht.
   * **voeg/schrap** toe: Voeg nieuwe afbeeldingen toe of verwijder bestaande degenen.

## Hoofdlettergebruik: landvelden vullen in een Visumaanvraagformulier

**Scenario**: Een overheidsagentschap verstrekt een online Vorm van de Toepassing van Visa van de volgende gebieden:

1. Volledige naam (tekst)
2. Geboortedatum (Datum)
3. Land van staatsburgerschap (vervolgkeuzelijst)
4. Paspoortnummer (tekst)
5. Land van afgifte paspoort (vervolgkeuzelijst)
6. Land van bestemming (vervolgkeuzelijst)
7. Beoogde datum van aankomst (datum)

In plaats van het handhaven van een statische lijst van landen, haalt de vorm dynamisch landinformatie (continent, kapitaal, de codes van ISO Alpha, enz.) gebruikend **getcountry API**:

`https://secure.geonames.org/countryInfoJSON?username=aemforms`

Hierdoor wordt gewaarborgd dat aanvragers altijd een actuele en nauwkeurige lijst van landen zien terwijl zij het formulier invullen.

### Implementatie met API-integratie in de Rule Editor

U kunt API integreren zonder een Model van de Gegevens van de Vorm tot stand te brengen door **te klikken creeert API Integratie** knoop in de Redacteur van de Regel.

![ creeer API Integratie ](/help/forms/assets/create-api-integration.png)

Een API dienst genoemd **getcountry** wordt gevormd onder **API de Configuratie van de Integratie** in de Redacteur van de Regel:

![ API de Configuratie van het eindpunt van het rustpunt ](/help/forms/assets/api-restendpoint.png)

* **API Eindpunt URL** → `https://secure.geonames.org/countryInfoJSON?username=aemforms`
* **Methode van HTTP** → GET
* **Type van Inhoud** → JSON
* **Input** → `username` ging als vraagparameter (`aemforms`) over.
* **Output** → De gebieden van de Reactie zoals `continent`, `capital`, `countrynames`, `isoAlpha3`, en `languages` worden in kaart gebracht aan vormgebieden.

In de **Vorm van de Toepassing van het Visa**, zijn de drie drop-down gebieden, **Land van Burgerschap**, **Land van de Uitgave van het Paspoort**, en **Land van de Bestemming**, verbindend aan de **Invoke de actie van de Dienst**.

Wanneer de vorm laadt, **haalt de Dienst** de lijst van landen van API aan. De reactie wordt dan toegewezen om de drop-down opties automatisch te bevolken.

Bijvoorbeeld, wanneer de gebruiker **Land van Burgerschap** opent, wordt de lijst van landen dynamisch getoond van de API reactie.

![ aanhalen-dienst-api-integratie ](/help/forms/assets/invoke-service-api-integration.png)

![ API integratieoutput ](/help/forms/assets/api-integration-output.png)

Op dezelfde manier gebruiken het **Land van de Uitgave van het Paspoort** en **Land van de Bestemming** de zelfde API vraag, die verenigbare en bijgewerkte gegevens over alle drie gebieden verzekert.

## Opnieuw proberen voor API-fouten implementeren

Wanneer een API-aanvraag mislukt, is het vaak handig om de aanvraag opnieuw uit te voeren voordat een fout aan de gebruiker wordt gemeld. U kunt een opiniepeiling uitvoeren en mechanisme opnieuw proberen door douanecode in het {**dossier te schrijven 0} function.js.**

In het volgende voorbeeld ziet u hoe u API-fouten kunt verwerken met maximaal twee pogingen om opnieuw te proberen en exponentiële back-ups tussen pogingen:

```javascript
/**
 * Handles request retries with up to 2 retry attempts
 * @param {function} requestFn - The request function to execute
 * @return {Promise} A promise that resolves with the response or rejects after all retries
 */
function retryHandler(requestFn) {
    const MAX_RETRIES = 2;
    
    /**
     * Attempts the request with retry metadata
     * @param {number} retryCount - Current retry attempt count
     * @return {Promise} The request promise
     */
    function attemptRequest(retryCount = 0) {
        // Include retry metadata if this is a retry
        const requestOptions = retryCount > 0 ? {
            headers: {
                'X-Retry': 'true',
                'X-Retry-Count': retryCount.toString(),
                'X-Retry-Time': new Date().toISOString()
            },
            body: {
                retry: true,
                retryCount: retryCount,
                timestamp: Date.now()
            }
        } : undefined;

        return requestFn(requestOptions)
            .then(function(response) {
                if (response && response.status >= 400) {
                    console.warn('Request failed with status ' + response.status);
                    throw new Error('Request failed with status ' + response.status);
                }
                return response;
            })
            .catch(function(error) {
                console.warn('Request attempt ' + (retryCount + 1) + ' failed:', error.message);
                
                // Retry if max attempts not reached
                if (retryCount < MAX_RETRIES) {
                    console.log('Retrying request, attempt ' + (retryCount + 2) + ' of ' + (MAX_RETRIES + 1));
                    
                    // Exponential backoff delay: 1s, 2s, 4s...
                    const delay = Math.pow(2, retryCount) * 1000;
                    
                    return new Promise(function(resolve) {
                        setTimeout(resolve, delay);
                    }).then(function() {
                        return attemptRequest(retryCount + 1);
                    });
                } else {
                    // All retries exhausted
                    console.error('All retry attempts failed. Final error:', error.message);
                    throw new Error('Request failed after ' + (MAX_RETRIES + 1) + ' attempts: ' + error.message);
                }
            });
    }
    
    // Start the first attempt
    return attemptRequest(0);
}
```

In de bovengenoemde code, beheert de **functie 0} retryHandler API verzoeken met automatische herpogingen in het geval van mislukking.** Er wordt een aanvraagfunctie (requestFn) gebruikt en de aanvraag wordt maximaal twee keer uitgevoerd, waarbij metagegevens worden toegevoegd voor elke nieuwe poging.

>[!NOTE]
>
> Voor gedetailleerde stappen op hoe te om douanefuncties toe te voegen, verwijs naar de [ Inleiding aan de Functies van de Douane voor Adaptieve Forms die op de 1} artikel van de Componenten van de Kern wordt gebaseerd.](/help/forms/create-and-use-custom-functions.md)

## Veelgestelde vragen

* **moet ik een Model van de Gegevens van de Vorm creëren om API in Aangepast Forms te integreren?**\
  Nee. Met de Visuele Redacteur van de Regel, kunt u APIs direct integreren gebruikend **creeer API de optie van de Integratie** zonder een Model van de Gegevens van de Vorm te creëren. Deze aanpak is het meest geschikt voor eenvoudige of formulierspecifieke gebruiksgevallen.

* **kan ik API vraag beveiligen die van de Redacteur van de Regel wordt gemaakt?**\
  Ja. De API Configuratie van de Integratie verstrekt authentificatieopties zoals **Basis, API Sleutel, en OAuth 2.0**. U kunt **Vereiste Encryptie** ook toelaten om ervoor te zorgen dat de gevoelige gegevens veilig worden overgebracht.