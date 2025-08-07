---
title: Verzendacties voor AEM Forms configureren met Edge Delivery Services
description: Leer hoe u verzendacties in AEM Forms configureert met Edge Delivery Services. Kies tussen Forms-verzendservice en AEM-publicatieactie voor verzending om formuliergegevens veilig en efficiënt te verwerken.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '855'
ht-degree: 0%

---

# Verzendhandelingen voor AEM Forms configureren

Configureer de verwerking van formulierverzendingen om gegevens via AEM Forms met Edge Delivery Services naar spreadsheets, e-mail of backend-systemen te leiden.

## Handleiding voor snelle besluitvorming

Kies uw verzendmethode:

| Methode | Best voor | Complexiteit instellen | Gevallen gebruiken |
|--------|----------|------------------|-----------|
| **de Verzenddienst van Forms** | Eenvoudige gegevensvastlegging | Laag | Contactformulieren, enquêtes, basisgegevensverzameling |
| **AEM publiceert Verzending** | Complexe workflows | Hoog | Integratie van bedrijven, aangepaste verwerking, workflows |

## Vereisten

Voordat u verzendacties configureert, moet u ervoor zorgen dat:

- AEM Forms as a Cloud Service-exemplaar
- Edge Delivery Services-project geconfigureerd
- Formulier gemaakt met Document Authoring of Universal Editor
- Vereiste machtigingen voor doeldoelen (werkbladen, e-mailsystemen of AEM)

+++ Methode 1: Forms-verzendservice

De Forms-verzendservice is een door Adobe gehost eindpunt dat ideaal is voor eenvoudige scenario&#39;s voor gegevensvastlegging.

### Ondersteunde doelen

- **Spreadsheets**: Google Sheets, Microsoft Excel (OneDrive/SharePoint)
- **E-mail**: Verzend vormgegevens naar gespecificeerde e-mailadressen

### Configuratiestappen

1. **de Toegang van de Bestemming van de Opstelling**
   - Voor spreadsheets: geef machtiging voor bewerking toe aan `forms@adobe.com` op doelspreadsheet
   - Voor e-mail: Controleer of de e-mailadressen van ontvangers toegankelijk zijn

2. **vormVerzending** vormen
   - Open uw formulier in de ontwerpomgeving
   - Handeling Verzenden instellen op &quot;Forms-verzendservice&quot;
   - Doelspreadsheet-URL of e-mailadres opgeven
   - Het formulier opslaan en publiceren

3. **Verzending van de Test**
   - Testgegevens via het formulier verzenden
   - Controleren of gegevens worden weergegeven in doeldoel
   - Foutenlogboeken controleren als verzending mislukt

### Belangrijke opmerkingen

- Serviceaccount `forms@adobe.com` vereist bewerktoegang tot doelwerkbladen
- E-mailmeldingen worden direct na het verzenden van het formulier verzonden
- De bevestiging van gegevens komt op de dienstniveau voor

![ de Stroom van de Dienst van de Verzending van Forms ](/help/forms/assets/eds-fss.png)

+++

+++ Methode 2: AEM-publicatie verzenden

Verzend formuliergegevens rechtstreeks naar uw AEM as a Cloud Service-publicatie-instantie voor complexe verwerking.

### Wanneer moet AEM publiceren worden gebruikt?

- Aangepaste AEM-workflows vereist na verzending
- Integratie van het Model van de Gegevens van het formulier (FDM) met gegevensbestanden
- Integraties met services van derden (Marketo, Power Automate, Workfront Fusion)
- Azure Blob Storage- of SharePoint-documentbibliotheken
- Complexe servervalidatie of verwerkingslogica

### Beschikbare verzendhandelingen

- [Verzenden naar REST-eindpunt](/help/forms/configure-submit-action-restpoint.md)
- [E-mail verzenden via e-mailservices van AEM](/help/forms/configure-submit-action-send-email.md)
- [Verzenden met gebruik van formuliergegevensmodel](/help/forms/configure-data-sources.md)
- [AEM-workflow aanroepen](/help/forms/aem-forms-workflow-step-reference.md)
- [Verzenden naar SharePoint](/help/forms/configure-submit-action-sharepoint.md)
- [Verzenden naar OneDrive](/help/forms/configure-submit-action-onedrive.md)
- [Verzenden naar Azure Blob Storage](/help/forms/configure-submit-action-azure-blob-storage.md)
- [Verzenden naar Microsoft Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)
- [Verzenden naar Adobe Workfront Fusion](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
- [Verzenden naar Adobe Marketo Engage](/help/forms/submit-adaptive-form-to-marketo-engage.md)

![ AEM publiceert de Stroom van de Verzending ](/help/forms/assets/eds-aem-publish.png)

### Configuratievereisten

#### &#x200B;1. AEM Dispatcher-configuratie

Configureer Dispatcher op uw AEM-publicatieexemplaar:

- **Verzendpaden toestaan**: wijzig `filters.any` om POST-aanvragen toe te staan `/adobe/forms/af/submit/...`
- **Geen Omleiding**: Zorg ervoor de regels van Dispatcher niet de wegen van de vormvoorlegging omleiden

#### &#x200B;2. OSGi Referrer-filter

In AEM OSGi console (`/system/console/configMgr`):

1. Zoeken naar &quot;Apache Sling Referrer Filter&quot;
2. Voeg uw Edge Delivery-domein toe aan de lijst Hosts toestaan
3. Inclusief domeinen zoals `https://your-eds-domain.hlx.page`

#### &#x200B;3. CDN-omleidingsregels

Configureer uw Edge Delivery CDN om verzendingen te routeren:

- Verzoeken van `/adobe/forms/af/submit/...` naar uw AEM-publicatieexemplaar verzenden
- De implementatie varieert per CDN-provider (Fastly, Akamai, Cloudflare)

#### &#x200B;4. Formulierconfiguratie

1. Formulier maken in Universal Editor
2. Verzendactie configureren om AEM Forms-actie als doel in te stellen
3. Pad naar verzendeindpunt opgeven
4. Formulier publiceren naar Edge Delivery-site

+++

+++ Formulier insluiten (optioneel)

Formulieren die op één locatie zijn gemaakt, insluiten in verschillende webpagina&#39;s of sites.

### Gevallen gebruiken

- Standaardformulieren hergebruiken op meerdere bestemmingspagina&#39;s
- Gespecialiseerde formulieren opnemen in door document geschreven inhoud
- Eén formulier bijhouden in meerdere EDS-projecten

### CORS-configuratie

Het delen van bronnen voor kruisoorsprong configureren op de formulierbron:

1. **voeg de Kopballen van CORS** aan vormbronreacties toe:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`
   - `Access-Control-Allow-Headers: Content-Type`

2. **Configuratie van het Voorbeeld**:

       # Configuratie voor site waarop het formulier wordt gehost 
        kopballen:
        - path: /forms/**
        douane:
        toegang-controle-staat-oorsprong toe: https://host-domain.com
        toegang-controle-staat-methodes toe: GET, OPTIONS 
   
### Stappen insluiten

1. **creeer en publiceer Vorm**
   - Formulier bouwen met Document Authoring of Universal Editor
   - Verzendmethode configureren (FSS of AEM Publish)
   - Publiceren naar zelfstandige URL

2. **vorm CORS**
   - CORS-koppen instellen op formulierbronsite
   - Toestaan dat het hostpaginadomein het formulier ophaalt

3. **bed in de Pagina van de Gastheer** in
   - Insluitingsblok van formulier toevoegen aan hostpagina
   - Puntblok voor gepubliceerde formulier-URL
   - Hostpagina publiceren

![ Ingebedde Architectuur van de Vorm ](/help/forms/assets/eds-embedded-form.png)

+++

+++ Vaak voorkomende problemen

| Probleem | Oplossing |
|-------|----------|
| **de voorlegging van de Vorm ontbreekt** | Controleer consolefouten, verifieer eindpunt-URL, bevestig toestemmingen |
| **Ingesloten vorm verschijnt niet** | CORS-koppen configureren op formulierbron, URL van formulier verifiëren |
| **403/401 fouten met AEM** | Filter Verschuivingsverwijzing bijwerken, verificatie-instellingen controleren |
| **Gegevens die spreadsheet** niet bereiken | Controleren of `forms@adobe.com` bewerkingstoegang heeft, URL van werkblad controleren |
| **fouten CORS** | Correcte `Access-Control-Allow-Origin` kopteksten toevoegen aan formulierbron |

+++

## Configuratievoorbeelden

+++ Op document gebaseerd formulier met spreadsheet-verzending

1. Formulierstructuur maken in Google Docs/Sheets
2. Het eindpunt van de Forms-verzendservice configureren
3. Toegang tot doelwerkblad verlenen `forms@adobe.com`
4. Document publiceren naar Edge Delivery-site
5. Verzending van formulieren en gegevensstroom testen

+++

+++ Universal Editor-formulier met AEM-workflow

1. Formulier maken in Universal Editor
2. Handeling Verzenden configureren naar &quot;AEM-workflow aanroepen&quot;
3. Dispatcher- en referentiefilter instellen op AEM Publish
4. CDN die regels verplettert configureren
5. Formulier publiceren en werkstroom testen

+++

## Aanbevolen procedures

- **Dienst van de Verzending van Forms van het Gebruik** voor eenvoudige gegevens vangen scenario&#39;s
- **kies AEM publiceren** wanneer de complexe verwerking of de integratie worden vereist
- **Test grondig** in het opvoeren milieu alvorens productieleiding
- **Inzendingen van de Monitor** gebruikend de logboeken van AEM en consolefouten
- **voer juiste fout behandeling** voor ontbroken voorlegging uit
- **bevestigt gegevens** op zowel cliënt als serverniveaus
- **HTTPS van het Gebruik** voor alle vormvoorlegging en gegevenstransmissie

## Verwante onderwerpen

- [Authoring op basis van documenten met EDS Forms](/help/edge/docs/forms/tutorial.md)
- [Universele editor met EDS Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
- [AEM Forms-verzendservice](/help/forms/forms-submission-service.md)
- [Gegevensbronnen configureren](/help/forms/configure-data-sources.md)
- [AEM Forms Workflow Reference](/help/forms/aem-forms-workflow-step-reference.md)
