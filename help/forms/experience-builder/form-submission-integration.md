---
title: Formulierverzending en integratie
description: Leer hoe u formulieren configureert en Forms Experience Builder-formulieren integreert met externe systemen, API's en bedrijfsworkflows.
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Developer
exl-id: c772556b-dab6-4fa8-b728-1fe52c6596a4
source-git-commit: 1d378e6c8ac714779e77314d3457a14d40cd222f
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# Formulierverzending en integratie

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar via een programma voor vroege toegang. Controleer voordat u begint of u toegang hebt aangevraagd en gekregen.

Forms Experience Builder biedt krachtige integratiemogelijkheden om uw formulieren te verbinden met externe systemen, API&#39;s en bedrijfsworkflows. In deze handleiding wordt beschreven hoe u formulierverzendingen kunt configureren en verschillende integratiescenario&#39;s kunt instellen.

## Opties voor verzendconfiguratie

### E-mailverzendingen

Formulieren configureren om verzendingen via e-mail te verzenden:

**Basis e-mailopstelling:**

- E-mailadressen van ontvangers instellen
- E-mailsjablonen configureren
- CC- en BCC-ontvangers toevoegen
- E-mailmeldingen instellen

**Geavanceerde e-maileigenschappen:**

- Dynamische selectie van ontvanger
- E-mailsjablonen met formuliergegevens
- Afhandeling van bijlagen
- E-mailleveringsbevestiging

### REST API-integratie

Formulieren verbinden met externe API&#39;s en services:

**API eindpuntconfiguratie:**

- REST API-URL&#39;s instellen
- Verificatiemethoden configureren
- Aanvraagkoppen en -parameters instellen
- Responsgegevens verwerken

**afbeelding van Gegevens:**

- Formuliervelden toewijzen aan API-parameters
- Transformatie gegevensindelingen
- Geneste JSON-structuren verwerken
- Foutreacties beheren

### Integratie van cloudopslag

Formulierverzendingen opslaan in cloudopslagservices:

**Gesteunde platforms:**

- Microsoft Azure Blob-opslag
- Amazon S3
- Google Cloud Storage
- SharePoint Online

**de opties van de Configuratie:**

- Opslagreferenties instellen
- Mappenstructuren configureren
- Naamconventies voor bestanden instellen
- Toegangsmachtigingen beheren

### Workflowintegratie

Formulieren verbinden met workflows voor bedrijfsprocessen:

**de Macht van Microsoft automatiseren:**

- Workflows activeren bij het verzenden van formulieren
- Formuliergegevens doorgeven aan workflowstappen
- Workflowreacties verwerken
- Goedkeuringsprocessen beheren

**Werkschema van Adobe:**

- Integreren met AEM Workflow
- Goedkeuringsketens instellen
- Meldingsstappen configureren
- Documentverwerking beheren

## Formulierverzendingen instellen

### Stap 1: De configuratie van de de voorlegging van de toegang

1. Open uw formulier in Forms Experience Builder
2. Navigeren naar de verzendinstellingen
3. Selecteer Formulierverzending configureren
4. Kies uw integratietype

### Stap 2: E-mailverzendingen configureren

**Basis e-mailopstelling:**

     vorm e-mailvoorlegging aan hr@company.com met:
     - Onderwerp: &quot;Nieuwe Toepassing van de Werknemer&quot;
     - omvat vormgegevens in e-maillichaam 
     - verzend bevestiging aan aanvrager 

**Geavanceerde e-mailconfiguratie:**

     opstelling dynamische e-mail die verplettert:
     - als de afdeling &quot;IT&quot;evenaart, verzend naar it-hr@company.com 
     - als de afdeling &quot;Verkoop&quot;evenaart, verzend naar sales-hr@company.com 
     - Gebrek aan hr@company.com 

### Stap 3: API-integratie instellen

**REST API configuratie:**

     legt vormgegevens aan REST eindpunt voor:
     - URL: https://api.company.com/forms/submit 
     - Methode: POST 
     - Authentificatie: Het teken van de drager 
     - Content-Type: application/json 

**de kaartvoorbeeld van Gegevens:**

     de vormgebieden van de Kaart aan API:
     - firstName -> user.first_name 
     - lastName -> user.last_name 
     - email -> user.email_address 
     - afdeling -> user.department_id 

### Stap 4: cloudopslag configureren

**Azure Blob Opslagopstelling:**

     de vormvoorlegging van de opslag in Azure:
     - Container: vorm-voorlegging 
     - Omslag: /{year}/{month}/{day}/
     - het formaat van het Dossier: JSON met gehechtheid 
     - het niveau van de Toegang: Privé 

## Voorbeelden van integratie

### Feedbackformulier voor klanten

**de configuratie van de Verzending:**

- E-mailmelding aan ondersteuningsteam
- Gegevens opslaan in CRM-systeem via API
- Automatisch een ondersteuningsticket maken
- Bevestigingsbericht verzenden naar klant

**Implementatie:**
Feedbackformulier voor klant verzenden naar:
1. E-mail <support@company.com> met formuliergegevens
2. POST naar CRM-API om klantrecord te maken
3. Workflow voor het maken van tickets voor triggerondersteuning
4. Stuur een e-mail naar de klant

### Werknemer aan boord van formulier

**de configuratie van de Verzending:**

- E-mailHR team met nieuwe huurinformatie
- Documenten opslaan in SharePoint
- Workflow voor inboden activeren
- Gebruikersaccounts maken in verschillende systemen

**Implementatie:**
Procesmedewerker aan boord:
1. E-mail <hr@company.com> met werknemersgegevens
2. Documenten uploaden naar de map SharePoint employee
3. Start de instapworkflow in Power Automate
4. Maak accounts in HR-systeem, e-mail en andere tools

### Generatieformulier voor lood

**de configuratie van de Verzending:**

- Belangrijkste gegevens opslaan in marketingautomatiseringsplatform
- Melding verzenden naar verkoopteam
- Leiding toevoegen aan CRM-systeem
- Opvolgingse-mailreeks activeren

**Implementatie:**
Productie van lood in processen:
1. POST-gegevens voor leads naar Marketo API
2. Create lead record in Salesforce
3. E-mailverkoopteam met gegevens over leads
4. Geautomatiseerde reeks e-mailprogramma&#39;s starten

## Geavanceerde integratiescenario&#39;s

### Formulierverwerking in meerdere stappen

**Complexe werkschemaintegratie:**

- Formuliergegevens valideren op externe systemen
- Betalingen verwerken via betaalgateways
- Documenten en contracten genereren
- Meldingen verzenden naar meerdere belanghebbenden

### Real-time gegevensvalidatie

**op API-Gebaseerde bevestiging:**

- E-mailadressen op bedrijfsdirectory valideren
- Beschikbaarheid van producten controleren in inventarisatiesysteem
- Klantgegevens verifiëren in CRM
- Betaalgegevens valideren

### Voorwaardelijke voorlegging verpletterend

**Dynamisch verpletterend gebaseerd op vormgegevens:**

- De route aan verschillende die afdelingen op onderzoekstype worden gebaseerd
- Verzenden naar verschillende systemen op basis van klantniveau
- Proces verschilt op basis van voltooiingsstatus van formulier
- Afhandeling van verschillende bedrijfsregels per regio

## Beveiliging en naleving

### Gegevensbescherming

**Encryptie en veiligheid:**

- Gevoelige gegevens tijdens de doorvoer versleutelen
- Beveilig API-referenties en tokens
- Voer juiste toegangscontroles uit
- Beleid voor gegevensopslag volgen

### Nalevingseisen

**GDPR en privacy:**

- Goedkeuringsbeheer implementeren
- Voorzie de mogelijkheden van de gegevensexport
- Verzoeken om gegevensverwijdering inschakelen
- Controlerrails onderhouden

**de normen van de Industrie:**

- HIPAA-naleving voor gezondheidszorgformulieren
- PCI DSS voor betalingsverwerking
- SOX-compatibiliteit voor financiële formulieren
- Industriespecifieke regelgeving

## Testen en valideren

### Verzendproef

**scenario&#39;s van de Test:**

- Levering en opmaak van e-mail controleren
- API-connectiviteit en gegevenstoewijzing testen
- Uploads voor cloudopslag valideren
- Functie workflowtrigger controleren

**de behandeling van de Fout:**

- De scenario&#39;s van de netwerkmislukking van de test
- Foutbericht valideren
- Controleren op mechanismen voor opnieuw proberen
- Opties voor fallback controleren

### Optimalisatie van prestaties

**de strategieën van de optimalisering:**

- asynchrone verwerking implementeren
- Batchbewerkingen voor bulkgegevens gebruiken
- API-aanroepfrequentie optimaliseren
- Veelgebruikte gegevens in cache opslaan

## Problemen met integratie oplossen

### Algemene problemen

**E-mail leveringskwesties:**

- SMTP-serverconfiguratie controleren
- E-mailadressen van ontvangers verifiëren
- Instellingen van spamfilter controleren
- Opmaak van e-mailsjablonen testen

**API integratieproblemen:**

- API-eindpunt-URL&#39;s verifiëren
- Verificatiegegevens controleren
- Aanvraagindeling en koppen valideren
- API-responsverwerking controleren

**de integratiekwesties van de Opslag:**

- Opslaggegevens bevestigen
- Mapmachtigingen controleren
- Limieten voor het uploaden van bestanden controleren
- Netwerkconnectiviteit testen

### Hulp krijgen

Voor integratieproblemen:

- Controle [ Veelgestelde vragen van de Bouwer van de Ervaring van Forms ](forms-experience-builder-frequently-asked-questions.md)
- Herzie [ Begonnen gids ](forms-experience-builder-getting-started.md)
- Neem contact op met de systeembeheerder voor technische ondersteuning
- Raadpleeg de API-documentatie voor externe services

<!-- 
## Related articles

- [Forms Experience Builder Overview](product-overview.md)
- [Getting started with Forms Experience Builder](forms-experience-builder-getting-started.md)
- [Deploy and configure Forms Experience Builder](deploy-forms-experience-builder.md)
- [Intelligent import and conversion](intelligent-import-conversion.md)
- [Frequently asked questions](forms-experience-builder-frequently-asked-questions.md)

-->


