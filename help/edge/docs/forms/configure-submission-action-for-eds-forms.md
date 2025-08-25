---
title: Verzendacties voor AEM Forms configureren met Edge Delivery Services
description: Leer hoe u verzendacties in AEM Forms configureert met Edge Delivery Services. Kies tussen Forms-verzendservice en AEM-publicatieactie voor verzending om formuliergegevens veilig en efficiënt te verwerken.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 2d16a9bd1f498dd0f824e867fd3b5676fb311bb3
workflow-type: tm+mt
source-wordcount: '810'
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

#### &#x200B;1. AEM Instance URL bijwerken in Edge Delivery

Werk de instantie-URL van AEM Cloud Service bij in het `constant.js` -bestand in het `form` blok onder `submitBaseUrl` . U kunt URL vormen die op uw milieu wordt gebaseerd:

**voor de instantie van Cloud Service**

```js
export const submitBaseUrl = '<aem-publish-instance-URL>';
```

**voor lokale ontwikkeling**

```js
export const submitBaseUrl = 'http://localhost:<port-number>';
```

#### &#x200B;2. OSGi Referrer-filter

Configureer het filter Referrer om uw specifieke Edge Delivery-sitedomeinen toe te staan:

1. Maak of werk het OSGi-configuratiebestand bij: `org.apache.sling.security.impl.ReferrerFilter.cfg.json`

2. Voeg de volgende configuratie toe met uw specifieke sitedomeinen:

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "main--abc--adobe.aem.live",
       "main--abc1--adobe.aem.live"
     ],
     "allow.hosts.regexp": [
       "https://.*\\.aem\\.live:443",
       "https://.*\\.aem\\.page:443",
       "https://.*\\.hlx\\.page:443",
       "https://.*\\.hlx\\.live:443"
     ],
     "filter.methods": [
       "POST",
       "PUT",
       "DELETE",
       "COPY",
       "MOVE"
     ],
     "exclude.agents.regexp": [
       ""
     ]
   }
   ```

3. De configuratie implementeren via Cloud Manager

Voor gedetailleerde configuratie van de Filter OSGi Referrer, verwijs naar de [ Gids van de Filter van de Verwijzer 0&rbrace;.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

#### &#x200B;3. Problemen met CORS (Cross Origin Resource Sharing)

Configureer CORS-instellingen in AEM om aanvragen van uw specifieke Edge Delivery-sitedomeinen toe te staan:

**Localhost van de Ontwikkelaar**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true
```

**de Plaatsen van Edge Delivery - voeg individueel elk plaatsdomein toe**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc--adobe\.aem\.live$)#" CORSTrusted=true
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://main--abc1--adobe\.aem\.live$)#" CORSTrusted=true
```

**de domeinen van Franklin van de Oudheid (als nog in gebruik)**

```apache
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

>[!NOTE]
>
>Vervang `main--abc--adobe.aem.live` en `main--abc1--adobe.aem.live` door de werkelijke sitedomeinen. Voor elke site die vanuit dezelfde opslagplaats wordt gehost, is een apart CORS-configuratieitem vereist.

Voor gedetailleerde configuratie CORS, verwijs naar de [ Gids van de Configuratie van CORS ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors).


Om CORS voor uw lokale ontwikkelomgeving toe te laten, verwijs naar [ het Delen van het Middel van de Cross-Origin (CORS) ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) artikel begrijpen.

<!--
#### 4. CDN Redirect Rules

Configure your Edge Delivery CDN to route submissions:

- Route requests from `/adobe/forms/af/submit/...` to your AEM Publish instance
- Implementation varies by CDN provider (Fastly, Akamai, Cloudflare)-->

#### &#x200B;4. Formulierconfiguratie

1. Formulier maken in Universal Editor
2. Verzendactie configureren om AEM Forms-actie als doel in te stellen
3. Pad naar verzendeindpunt opgeven
4. Formulier publiceren naar Edge Delivery-site

+++
<!--
+++ Form Embedding

Embed forms created in one location into different web pages or sites.

### Use Cases

- Reuse standard forms across multiple landing pages
- Include specialized forms in Document-Authored content
- Maintain single form across multiple EDS projects

### CORS Configuration

Configure Cross-Origin Resource Sharing on the form source:

1. **Add CORS Headers** to form source responses:
   - `Access-Control-Allow-Origin: https://your-host-domain.com`
   - `Access-Control-Allow-Methods: GET, OPTIONS`  
   - `Access-Control-Allow-Headers: Content-Type`

2. **Example Configuration**:

        # Configuration for site hosting the form
        headers:
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS

### Embedding Steps

1. **Create and Publish Form**
   - Build form using Document Authoring or Universal Editor
   - Configure submission method (FSS or AEM Publish)
   - Publish to standalone URL

2. **Configure CORS**
   - Set up CORS headers on form source site
   - Allow host page domain to fetch form

3. **Embed in Host Page**
   - Add form embedding block to host page
   - Point block to published form URL
   - Publish host page

![Embedded Form Architecture](/help/forms/assets/eds-embedded-form.png)

+++-->

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
