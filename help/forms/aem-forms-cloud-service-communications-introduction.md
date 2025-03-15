---
title: AEM Forms as a Cloud Service Communication-API's
description: Documenten genereren, bewerken en beveiligen met AEM Forms Communication-API's in de cloud
Keywords: document generation, PDF manipulation, document security, batch processing, document conversion, PDF/A compliance
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: a9eed5b6219163e721d81c9d77a31604666a2ac5
workflow-type: tm+mt
source-wordcount: '1423'
ht-degree: 0%

---


# AEM Forms as a Cloud Service Communication-API&#39;s {#communications-apis-overview}

> **Beschikbaarheid van de Versie**
>
> * **AEM 6.5**: [ Overzicht van de Diensten van het Document van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html)
> * **AEM as a Cloud Service**: Dit artikel

## Inleiding

Via communicatie-API&#39;s in AEM Forms as a Cloud Service kunt u door uw merk goedgekeurde, gepersonaliseerde en gestandaardiseerde documenten maken voor uw zakelijke behoeften. Met deze krachtige API&#39;s kunt u documenten programmatisch genereren, manipuleren en beveiligen, op aanvraag of in batchprocessen op grote volumes.


### Belangrijkste voordelen

* **Gestroomlijnde documentgeneratie** - creeer gepersonaliseerde documenten door malplaatjes met klantengegevens samen te voegen
* **Krachtige documentmanipulatie** - combineer, herschik, en bevestig de documenten van PDF programmatically
* **Flexibele plaatsingsopties** - Gebruik op bestelling APIs voor lage latentiebehoeften of batch-APIs voor high-productietaken
* **Verbeterde veiligheid** - pas digitale handtekeningen, certificatie, en encryptie toe om gevoelige documenten te beschermen
* **Cloud-inheemse architectuur** - hefboomwerking scalable, veilige wolkeninfrastructuur zonder onderhoudsoverheadkosten

## Belangrijkste mogelijkheden

Communicatie-API&#39;s bieden een uitgebreide set mogelijkheden voor documentverwerking die zijn ingedeeld in de volgende functionele gebieden:


| Document genereren | Documentmanipulatie | Document uitnemen | Documentconversie | Document Assurance |
|---------------------|----------------------|---------------------|---------------------|-------------------|
| Genereer gepersonaliseerde documenten door sjablonen samen te voegen met gegevens in verschillende indelingen, waaronder PDF en afdrukindelingen. | U kunt PDF-documenten programmatisch combineren, herschikken en valideren om nieuwe documentpakketten te maken. | Eigenschappen, metagegevens en inhoud uit PDF-documenten extraheren voor verdere verwerking. | Documenten converteren naar andere indelingen, waaronder PDF/A-compatibiliteitsvalidatie voor archiveringsbehoeften. | Digitale handtekeningen, certificering en versleuteling toepassen om documenten te beveiligen en te beveiligen. |

## Document genereren

In API&#39;s voor het genereren van communicatiedocumenten worden sjablonen (XFA of PDF) gecombineerd met klantgegevens (XML) om gepersonaliseerde documenten te maken in PDF en verschillende afdrukindelingen (PS, PCL, DPL, IPL, ZPL).

### Werken met het genereren van documenten

De typische werkstroom omvat:

1. Creërend een malplaatje gebruikend [ Designer ](use-forms-designer.md)
2. XML-gegevens voorbereiden om de sjabloon te vullen
3. Communicatie APIs gebruiken om het malplaatje met gegevens samen te voegen
4. Uitvoerdocumenten in de gewenste indeling genereren

![ Communicatie Werkschema van de documentgeneratie ](assets/communicaions-workflow.png)

### PDF-documenten maken

Met de API&#39;s voor het genereren van documenten kunt u niet-interactieve PDF-documenten maken door XML-gegevens samen te voegen met formuliersjablonen:

![ creeer PDF documenten ](assets/outPutPDF_popup.png)

U kunt de gegenereerde PDF&#39;s via downloads aan gebruikers leveren, ze opslaan in een opslagplaats of ze optioneel uploaden naar Azure Blob Storage.

<span class="preview"> het Uploaden van geproduceerde PDFs aan Azure BlobOpslag is beschikbaar door het [ Vroege Programma van de Aannemer ](/help/forms/early-access-ea-features.md). Neem contact op met aem-forms-ea@adobe.com via uw officiële e-mail om deel te nemen.</span>

### Documenten met afdrukindeling maken

Documenten genereren in afdrukformaten, zoals:
* PostScript (PS)
* Printer Command Language (PCL)
* Zebra Printing Language (ZPL)

Deze indelingen zijn ideaal voor hoogwaardige afdrukbewerkingen en speciale afdrukbehoeften.

### Batchverwerking voor meerdere documenten

Verwerk grote hoeveelheden documenten efficiënt met batch-API&#39;s:

![ Werkstroom van de Verwerking van de Partij ](assets/ou_OutputBatchMany_popup.png)

Met batchverwerking kunt u:

* Afzonderlijke documenten genereren voor elke record in een XML-gegevensbron
* Documenten asynchroon verwerken voor betere prestaties
* Verschillende omzettingsparameters voor het batchproces configureren

## Documentmanipulatie

Met API&#39;s voor documentmanipulatie kunt u PDF-documenten programmatisch combineren, herschikken en transformeren.

### Document samenstellen

Combineer meerdere PDF- of XDP-documenten tot één samenhangend document:

![ samenstellend een eenvoudig document van PDF van veelvoudige documenten van PDF ](assets/as_document_assembly.png)

Mogelijkheden voor documentverzameling zijn:
* Eenvoudige PDF-documenten maken van meerdere bronnen
* PDF-portfolio&#39;s maken
* Gecodeerde documenten samenstellen
* Bates-nummering toevoegen voor juridische documenten
* Interactieve formulieren samenvoegen en afvlakken

### Documentdemontage

Verdeel grote PDF-documenten in kleinere, beter te beheren onderdelen:

![ het Verdelen van een brondocument dat op referenties in veelvoudige documenten wordt gebaseerd ](assets/as_intro_pdfsfrombookmarks.png)

Met documentdemontage kunt u:
* Specifieke pagina&#39;s uit brondocumenten extraheren
* Documenten verdelen op basis van bladwijzers
* Logische documentsets maken van grotere compilaties

>[!NOTE]
>
> AEM Forms bevat veel ingebouwde lettertypen die naadloos kunnen worden geïntegreerd met PDF-bestanden. Voor een volledige lijst van gesteunde doopvonten, [ klik hier ](/help/forms/supported-out-of-the-box-fonts.md).

## Document uitnemen

<span class="preview"> de Extractie van het Document is beschikbaar door het [ Vroege Programma van de Aannemer ](/help/forms/early-access-ea-features.md). Neem contact op met aem-forms-ea@adobe.com via uw officiële e-mail om deel te nemen.</span>

Met API&#39;s voor het uitpakken van documenten kunt u gegevens ophalen uit PDF-documenten, zoals:

* Documenteigenschappen (is het een invulbaar formulier, bevat het bijlagen, enz.)
* Gebruiksrechten en machtigingen
* Metagegevens met gebruik van Adobe Extensible Metadata Platform (XMP)

Deze functie is vooral handig voor documentbeheersystemen, archiveringsoplossingen en workflowautomatisering.

## Documentconversie

### Conversie en validatie van PDF/A

Converteer standaard PDF-documenten naar PDF/A-indeling voor langetermijnarchiveringsdoeleinden:

* Ondersteuning voor PDF/A-1a, 1b, 2a, 2b, 3a en 3b compatibiliteitsnormen
* Validatie van PDF/A-compatibiliteit
* Behoud van documentintegriteit met ingesloten lettertypen en niet-gecomprimeerde inhoud

### PDF naar XDP-conversie

<span class="preview"> PDF aan XDP conversie is beschikbaar door het [ Vroege Programma van de Aannemer ](/help/forms/early-access-ea-features.md). Neem contact op met aem-forms-ea@adobe.com via uw officiële e-mail om deel te nemen.</span>

Converteer PDF-documenten met XFA-streams naar XDP-indeling voor sjabloonbewerking en hergebruik.

## Document Assurance {#doc-assurance}

Document Assurance bevat API&#39;s voor handtekening en versleuteling waarmee u uw documenten gedurende de volledige levenscyclus kunt beveiligen.

### Handtekening-API&#39;s

PDF-documenten beveiligen met digitale handtekeningen en certificering:

* Zichtbare of onzichtbare handtekeningvelden toevoegen
* Handtekeningvelden digitaal ondertekenen
* Documenten certificeren voor integriteit
* Handtekeningen uit documenten verwijderen
* Handtekeningvelden verwijderen uit documenten

<span class="preview"> de verwijdering van de Handtekening en de schrapping van het handtekeningsgebied zijn beschikbaar door het [ Vroege Programma van de Aannemer ](/help/forms/early-access-ea-features.md). Neem contact op met aem-forms-ea@adobe.com via uw officiële e-mail om deel te nemen.</span>

### Coderings-API&#39;s

Documentinhoud beveiligen met versleuteling:

* PDF-documenten versleutelen met wachtwoorden
* Op een wachtwoord gebaseerde codering verwijderen
* Beveiligingstypen bepalen die worden toegepast op documenten
* Beveiligingsgegevens ophalen uit beveiligde documenten

### Documenthulpprogramma {#doc-utility}

Documenthulpprogramma&#39;s bieden aanvullende functionaliteit voor het werken met PDF-documenten:

#### Gebruiksrechten-API&#39;s (Reader-extensie)

<span class="preview"> de Rechten van het Gebruik (de Uitbreiding van Reader) is beschikbaar door het [ Vroege Programma van de Aannemer ](/help/forms/early-access-ea-features.md). Neem contact op met aem-forms-ea@adobe.com via uw officiële e-mail om deel te nemen.</span>

Breid de functionaliteit van Adobe Reader uit door gebruiksrechten toe te voegen aan PDF-documenten en schakelt functies zoals:

* Formulier invullen en opslaan
* Opmerkingen en annotaties toevoegen
* Digitaal ondertekenen
* Bestandsbijlagen
* Formuliergegevens importeren/exporteren
* Toegang tot webservices en databases

Beschikbare gebruiksrechten zijn onder meer:

* **Interactie van de Vorm**: De Vulling van de vorm, de Invoer/de Uitvoer van de Gegevens van de Vorm, Dynamische Gebieden/Pagina&#39;s van de Vorm
* **Annotaties**: Commentaren (online en off-line), Digitale Handtekeningen
* **de Behandeling van het Document**: Ingesloten Dossiers, voorleggen standalone, streepjescodes decoderen
* **Online Diensten**: Online Forms, toegang tot Webdiensten

## Typen communicatie-API&#39;s {#types}

Communicatie biedt twee typen API&#39;s die geschikt zijn voor verschillende gebruiksgevallen:

### Synchrone API&#39;s

**Best voor**: Op bestelling, lage latentie, enige documentgeneratie
**Gevallen van het Gebruik**: Gebruiker-teweeggebrachte documentgeneratie, interactieve toepassingen
**Documentatie**: [ Synchrone API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

### Batch-API&#39;s (asynchroon)

**Best voor**: Gepland, hoog-productie, veelvoudige documentgeneratie
**Gebruik gevallen**: Maandelijkse verklaringen, rekeningen, berichten, geplande rapporten
**Documentatie**: [ Partij API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

## Aan de slag met communicatie-API&#39;s

### Onboarding Process

Communicatie is beschikbaar als zelfstandige module of invoegtoepassing voor Forms as a Cloud Service-gebruikers:

1. Neem contact op met Adobe Sales of uw Adobe-vertegenwoordiger om toegang te vragen
2. Adobe maakt toegang voor uw organisatie mogelijk en kent beheerdersrechten toe
3. Uw beheerder kan dan toegang verlenen aan ontwikkelaars in uw organisatie

### Communicatie in uw omgeving inschakelen

Ga als volgt te werk om Communicatie voor uw Forms as a Cloud Service-omgeving in te schakelen:

1. Aanmelden bij Cloud Manager en AEM Forms as a Cloud Service Instance openen
2. Open de optie Programma bewerken en ga naar het tabblad Oplossingen en invoegtoepassingen
3. Selecteer de optie **[!UICONTROL Forms - Communications]**

   ![ Mededelingen ](assets/communications.png)

   Als u **[!UICONTROL Forms - Digital Enrollment]** al hebt ingeschakeld, selecteert u in plaats daarvan de optie **[!UICONTROL Forms - Communications Add-On]** .

   ![ Addon ](assets/add-on.png)

4. Klikken **[!UICONTROL Update]**
5. De build-pijplijn uitvoeren - Communicatie-API&#39;s worden ingeschakeld na voltooiing

>[!NOTE]
>
> Om documentmanipulatie APIs toe te laten, voeg de volgende regel aan uw [ configuratie van Dispatcher ](setup-local-development-environment.md#forms-specific-rules-to-dispatcher) toe:
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## API-naslagdocumentatie {#api-reference}

Communicatie-API&#39;s zijn ingedeeld in verschillende functionele categorieën, elk met gedetailleerde referentiedocumentatie. Deze API-verwijzingen bieden uitgebreide informatie over eindpunten, parameters, verzoek-/antwoordindelingen en verificatievereisten.

### API&#39;s voor het genereren van documenten

| API | Beschrijving | Verwijzing koppeling |
|-----|-------------|----------------|
| Document genereren - synchroon | Documenten op aanvraag genereren met een lage latentie voor interactieve scenario&#39;s | [ API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/) |
| Document genereren - Batch | Hoge volumes documenten asynchroon verwerken voor geplande bewerkingen | [ API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/) |

### Documentmanipulatie-API&#39;s

| API | Beschrijving | Verwijzing koppeling |
|-----|-------------|----------------|
| Documentmanipulatie - synchroon | PDF-documenten combineren, splitsen en transformeren met gebruik van DDX-instructies | [ API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/) |

### Document Assurance API&#39;s

| API | Beschrijving | Verwijzing koppeling |
|-----|-------------|----------------|
| DocAssurance - Synchronous | Digitale handtekeningen, certificering, codering en lezerextensies toepassen | [ API Verwijzing ](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/docassurance/) |

### Algemene API-parameters

Elke API-categorie heeft specifieke parameters, maar enkele algemene parameters zijn:

#### Parameters voor het genereren van documenten

| Parameter | Type | Vereist | Beschrijving |
|-----------|------|----------|-------------|
| `template` | String | Ja | Pad naar het XDP- of PDF-sjabloonbestand |
| `data` | String | Nee | XML-gegevens die moeten worden samengevoegd met de sjabloon |
| `outputOptions` | Object | Nee | Configuratieopties voor het uitvoerdocument |

#### Parameters voor documentmanipulatie

| Parameter | Type | Vereist | Beschrijving |
|-----------|------|----------|-------------|
| `ddx` | String | Ja | DDX-instructies voor documentmontage of demontage |
| `inputDocuments` | Object | Ja | Kaart van te verwerken invoerdocumenten |
| `outputOptions` | Object | Nee | Configuratieopties voor het uitvoerdocument |

#### Assurance-parameters document

| Parameter | Type | Vereist | Beschrijving |
|-----------|------|----------|-------------|
| `inputPDF` | String | Ja | PDF-document invoeren dat moet worden beveiligd of ondertekend |
| `certificateAlias` | String | Voorwaardelijk | Alias van het certificaat voor ondertekeningsbewerkingen |
| `credentialPassword` | String | Voorwaardelijk | Wachtwoord voor referentie gebruikt bij ondertekening |

Voor volledige parameterdetails, authentificatievereisten, en voorbeeldverzoeken/reacties, verwijs naar de specifieke API verwijzingsdocumentatie verbonden in de lijsten hierboven.

## Aanvullende bronnen {#see-also}

* [Communicatieverwerking - synchrone API&#39;s](/help/forms/aem-forms-cloud-service-communications.md)
* [Communicatieverwerking - Batch-API&#39;s](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [AEM Forms as a Cloud Service-architectuur](/help/forms/aem-forms-cloud-service-architecture.md)
* [ API de Documentatie van de Verwijzing ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)
* [Functies van programma voor vroege adoptie](/help/forms/early-access-ea-features.md)
