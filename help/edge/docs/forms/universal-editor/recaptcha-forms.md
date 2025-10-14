---
title: Google reCAPTCHA toevoegen aan Forms in Universal Editor
description: Handleiding voor de implementatie van de Google reCAPTCHA-beveiliging in Edge Delivery Services-formulieren om spam en automatische aanvallen te voorkomen
feature: Edge Delivery Services
keywords: reCAPTCHA in formulieren, met reCAPTCHA in de Universal Editor, voeg reCAPTCHA toe in formulieren, formulierbeveiliging, spambeveiliging
role: Developer, Admin
level: Intermediate
exl-id: 1f28bd13-133f-487e-8b01-334be7c08a3f
source-git-commit: fd3c53cf5a6d1c097a5ea114a831ff626ae7ad7e
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 0%

---


# Google reCAPTCHA toevoegen aan Forms in Universal Editor

Google reCAPTCHA helpt formulieren te beschermen door onderscheid te maken tussen menselijke gebruikers en geautomatiseerde bots. In deze handleiding wordt uitgelegd hoe u zowel de reCAPTCHA Enterprise- als de Standard-versie in de Universal Editor implementeert.

**Doelstellingen:**

- Selecteer de juiste reCAPTCHA-oplossing
- reCAPTCHA Enterprise of Standard configureren
- reCAPTCHA toevoegen aan uw formulieren
- De implementatie valideren en testen
- Prestaties bewaken en optimaliseren

## Vereisten

Zorg ervoor dat u het volgende hebt voordat u begint:

### Toegangsvereisten

- AEM as a Cloud Service authoring
- Universele Editor heeft toegang tot formulierbewerkingsmachtigingen

### Technische vereisten

- Active Google-account
- Voor Enterprise: Google Cloud Platform-project met facturering ingeschakeld
- Standaard: Google reCAPTCHA-account
- Verifieerde domeineigendom voor uw formulieren

### Kennisvereisten

- Basiskennis van AEM Forms en Universal Editor
- Kennis van cloudserviceconfiguraties
- Werken met concepten voor formulierbeveiliging

## Waarom gebruik je reCAPTCHA in je Forms?

| ![&#x200B; Veiligheid &#x200B;](/help/edge/docs/forms/universal-editor/assets/security.svg) | ![&#x200B; Bot Bescherming &#x200B;](/help/edge/docs/forms/universal-editor/assets/bot-protection.svg) | ![&#x200B; Ervaring van 0&rbrace; Gebruiker](/help/edge/docs/forms/universal-editor/assets/user-experience.svg) |
|:-------------:|:-------------:|:-------------:|
| **Verbeterde Veiligheid** | **Bot &amp; Preventie Spam** | **Naadloze Ervaring van de Gebruiker** |
| Formulieren beschermen tegen frauduleuze activiteiten en aanvallen | Voorkomen dat automatische bots formulieren verzenden | Onzichtbare reCAPTCHA verstoort legitieme gebruikers niet |

**Zeer belangrijk Concept:** reCAPTCHA gebruikt machine het leren om gebruikersgedrag te analyseren en wijst een score (0.0 tot 1.0) toe die op de waarschijnlijkheid van menselijke interactie wijst. Hogere scores duiden op menselijke gebruikers; lagere scores duiden op bots.

**Voorbeeld:** de vorm van de belastingberekening die gevoelige gegevens behandelt vereist bescherming tegen geautomatiseerde aanvallen. reCAPTCHA controleert of de inzendingen afkomstig zijn van echte gebruikers, niet van bots.

## Kies uw reCAPTCHA-oplossing

Edge Delivery Services Forms ondersteunt twee Google reCAPTCHA-opties. Gebruik de volgende criteria om de juiste oplossing te selecteren:

### Handleiding voor snelle besluitvorming

**Onderneming van het Gebruik reCAPTCHA als u hebt:**

- Formulieren voor hoog verkeer (>10.000 verzoeken/maand)
- Strikte conformiteitseisen (GDPR, SOX, HIPAA)
- Noodzaak van geavanceerde analyses en rapportage
- Begroting voor premiumfuncties
- Complexe multidomein-implementaties

**Norm van het Gebruik reCAPTCHA als u hebt:**

- Laag tot matig verkeer (&lt;10.000 verzoeken/maand)
- Basisbeveiligingsbehoeften
- Beperkt budget (gratis niveau)
- Eenvoudige installatie van één domein
- Zijn nieuw voor reCAPTCHA

### Gedetailleerde vergelijking

| **Eigenschap** | **reCAPTCHA Onderneming** | **reCAPTCHA Standaard** |
|-------------|--------------------------|------------------------|
| **Kosten** | Betaald (op gebruik gebaseerde prijsstelling) | Gratis |
| **Limiet van het Verzoek** | Onbeperkt | 1M verzoeken/maand |
| **Geavanceerde Analytics** | Gedetailleerde rapportage | Alleen basisstatussen |
| **de Regels van de Douane** | Accountspecifieke regels | Alleen algemene regels |
| **Ondersteuning voor meerdere domeinen** | Geavanceerd beheer | Basisondersteuning |
| **SLA** | 99,9% uptime garantie | Beste inspanning |
| **Steun** | Enterprise-ondersteuning | Communautaire steun |
| **Naleving** | Bedrijfsniveau | Standaardcompatibiliteit |

**verstrekken Beide oplossingen:**

- Score-gebaseerde detectie (schaal 0,0 tot 1,0)
- Onzichtbare bewerking (geen gebruikersinteractie vereist)
- Apparaatleerboontetectie
- Risicobeoordeling in realtime

## reCAPTCHA Enterprise instellen


+++ Stap 1: Google Cloud-omgeving voorbereiden

**Vereisten:**

1. Google Cloud Project met facturering ingeschakeld
2. Project-id (van GCP-dashboard)
3. Domeinverificatie voor uw formulieren
4. Beheerders krijgen toegang tot GCP en AEM

**Opstelling:**

1. Een Google Cloud-project maken of selecteren
   - Ga naar [&#x200B; Google Cloud Console &#x200B;](https://console.cloud.google.com/)
   - Een nieuw project maken of een bestaand project selecteren
   - Noteer uw project-id

2. reCAPTCHA Enterprise API inschakelen
   - Ga naar API&#39;s en services > Bibliotheek
   - Zoeken naar &quot;reCAPTCHA Enterprise API&quot;
   - Klikken en inschakelen

3. API-referenties maken
   - Ga naar API&#39;s en services > Referenties
   - Klik op Referenties maken > API-sleutel
   - De API-sleutel kopiëren en opslaan

4. Sitetoets maken
   - Ga naar Beveiliging > reCAPTCHA Enterprise
   - Klik op Toets maken
   - Op muziek gebaseerd sleuteltype kiezen
   - Uw domein(en) toevoegen
   - Drempelscore instellen (aanbevolen: 0,5)

**Controlepunt van de Bevestiging:** zorg u hebt:

- Project-id
- API-sleutel
- Site-sleutel
- Geverifieerd domein in Google Cloud

+++

+++ Stap 2: AEM Cloud Configuration Container configureren

![&#x200B; de geleidelijke opstelling van de wolkenconfiguratie &#x200B;](/help/edge/docs/forms/universal-editor/assets/recaptcha-general-configuration.png)
*Cijfer: Het toelaten van wolkenconfiguraties voor uw vormcontainer*

**Opstelling:**

1. Toegangsconfiguratiebrowser
   - Aanmelden bij de instantie van AEM-auteur
   - Ga naar Gereedschappen > Algemeen > Configuratiebrowser

2. Cloudconfiguraties inschakelen
   - De configuratiecontainer van uw formulier zoeken
   - Eigenschappen selecteren
   - Cloudconfiguraties controleren
   - Klik op Opslaan en sluiten

3. Configuratie controleren
   - De optie &quot;Cloud Configurations&quot; bevestigen wordt weergegeven in de containereigenschappen

**Controlepunt van de Bevestiging:**

- Cloud Configurations ingeschakeld voor uw container
- Container wordt weergegeven in de configuratiebrowser
- Eigenschappen tonen &quot;Cloud Configurations&quot; zoals ingeschakeld

+++

+++ Stap 3: Configureer de reCAPTCHA Enterprise Service in AEM

![&#x200B; reCAPTCHA het configuratiescherm van de Onderneming &#x200B;](/help/edge/docs/forms/universal-editor/assets/recaptcha-enterprise.png)
*Cijfer: reCAPTCHA de configuratieinterface van de Onderneming in AEM*

**Configuratie:**

1. Toegang tot configuratie reCAPTCHA
   - Ga naar Extra > Cloud Services > reCAPTCHA
   - De configuratiecontainer van het formulier selecteren
   - Klik op Maken

2. Enterprise-instellingen configureren
   - Titel: beschrijvende naam (bijvoorbeeld &quot;Production reCAPTCHA&quot;)
   - Naam: Systeemnaam (automatisch gegenereerd of aangepast)
   - Versie: selecteer ReCAPTCHA Enterprise
   - Project-id: voer uw Google Cloud-project-id in
   - Sitecode: voer de sitesleutel in vanuit Google Cloud
   - API-sleutel: voer uw Google Cloud API-sleutel in
   - Type sleutel: Score-gebaseerde sitetoets selecteren

3. Beveiligingsdrempel instellen
   - Drempelscore: instellen tussen 0,0 en 1,0
   - Aanbevolen waarden:
      - 0.7-0.9: Hoge veiligheid (kan sommige wettige gebruikers blokkeren)
      - 0.5-0.7: Evenwichtige zekerheid (aanbevolen)
      - 0.1-0.5: Minder beveiliging (meer gebruikers zijn toegestaan)

4. Opslaan en publiceren
   - Klik op Maken om de configuratie op te slaan
   - Klik op Publiceren om deze beschikbaar te maken

**Controlepunt van de Bevestiging:**

- Configuratie is opgeslagen
- Alle vereiste velden voltooid
- Gepubliceerde en zichtbare configuratie
- Geen foutberichten

+++

## RECAPTCHA-standaard instellen

+++Stap 1: haal API-sleutels voor reCAPTCHA aan (zie details)

>[!IMPORTANT]
>
> Edge Delivery Services Forms biedt alleen ondersteuning voor reCAPTCHA v2 (Score-based). Gebruik de versie van het selectievakje niet.

**Zeer belangrijke Generatie:**

1. Google reCAPTCHA-console openen

   - Ga naar [&#x200B; Google reCAPTCHA Admin Console &#x200B;](https://www.google.com/recaptcha/admin)
   - Aanmelden met uw Google-account

2. Nieuwe site maken

   - Klik op + om een nieuwe site toe te voegen
   - Label: voer een beschrijvende naam in
   - reCAPTCHA Type: Selecteer reCAPTCHA v2 > &quot;Ik ben geen robot&quot; Onzichtbaar
   - Domeinen: Voeg uw formulierdomein(s) toe
   - Algemene voorwaarden accepteren en klikken op Verzenden

3. Verzamel uw toetsen

   - Site-sleutel: de sitetoets kopiëren (openbare sleutel)
   - Geheime sleutel: Kopieer de geheime sleutel (persoonlijke sleutel)

**Controlepunt van de Bevestiging:**

- Site gemaakt in de reCAPTCHA-console

- Site-sleutel verkregen

- Geheim sleutel verkregen

- Toegevoegde en geverifieerde domeinen

+++

+++Stap 2: AEM Cloud Configuration Container configureren (zie details)

Volg hetzelfde proces als in de Enterprise-instelling:

1. Cloud Configurations inschakelen in de configuratievenster

2. Containerconfiguratie controleren

3. Bevestig instellingen worden opgeslagen

+++

+++Stap 3: Configureer de standaardservice reCAPTCHA in AEM (zie details)

![&#x200B; reCAPTCHA Standaard configuratiescherm &#x200B;](/help/edge/docs/forms/universal-editor/assets/recaptcha.png)
*Cijfer: reCAPTCHA Standaard configuratieinterface in AEM*

**Configuratie:**

1. Toegang tot configuratie reCAPTCHA

   - Ga naar Extra > Cloud Services > reCAPTCHA
   - De configuratiecontainer van het formulier selecteren
   - Klik op Maken

2. Standaardinstellingen configureren

   - Titel: beschrijvende naam (bijvoorbeeld &quot;Standard reCAPTCHA&quot;)
   - Naam: Systeemnaam (automatisch gegenereerd of aangepast)
   - Versie: selecteer ReCAPTCHA v2
   - Sitecode: voer de Google reCAPTCHA-sitetoets in
   - Geheime sleutel: voer je geheime sleutel voor Google reCAPTCHA in

3. Opslaan en publiceren

   - Klik op Maken om de configuratie op te slaan
   - Klik op Publiceren om deze beschikbaar te maken

**Controlepunt van de Bevestiging:**

- Configuratie gemaakt zonder fouten

- Beide toetsen zijn correct ingevoerd

- Configuratie is gepubliceerd

- Configuratie wordt weergegeven in de lijst

+++

## reCAPTCHA toevoegen aan uw formulier

Nadat u de service reCAPTCHA hebt geconfigureerd, voegt u als volgt beveiliging toe aan uw formulier:

![&#x200B; Toevoegend de reCAPTCHA component aan een vorm &#x200B;](/help/edge/docs/forms/universal-editor/assets/add-recaptcha-component.png)
*Figuur: Het toevoegen van de Onzichtbare component Captcha aan uw vorm*

+++&#x200B;1. Formulier openen in Universal Editor
Ga naar uw formulier in AEM Sites en klik op Bewerken om het te openen in de Universal Editor. Wacht tot de editor is geladen.

- Ga naar uw formulier in AEM Sites
- Klik op Bewerken om te openen in de universele editor
- Wacht tot de editor is geladen
+++

+++&#x200B;2. Zoek de formulierstructuur
Zoek in de inhoudsstructuur (linkerdeelvenster) de sectie Adaptief formulier en vouw de formulierstructuur uit om de invoegpunten te zien.

- Zoek in de inhoudsstructuur (linkerdeelvenster) de sectie Adaptief formulier
- De formulierstructuur uitvouwen om invoegpunten te zien
+++

+++3. Add reCAPTCHA Component
Voeg de component Captcha (onzichtbaar) toe aan uw formulier.

- Klik op het pictogram Toevoegen (+) in uw formuliersectie
- Selecteer Captcha (Onzichtbaar) in de lijst met componenten
- U kunt ook de component slepen en neerzetten vanuit het deelvenster Componenten
+++

+++&#x200B;4. Component configureren (optioneel)
Selecteer de nieuw toegevoegde component captcha en verifieer het uw configuratie reCAPTCHA gebruikt.

- De nieuw toegevoegde component captcha selecteren
- Controleer in het deelvenster Eigenschappen of de reCAPTCHA-configuratie wordt gebruikt
- Geen extra configuratie nodig voor basisopstelling
+++

+++&#x200B;5. Publiceer uw wijzigingen
Publiceer uw wijzigingen en controleer of er geen fouten zijn.

- Klik op Publiceren in universele editor
- Wacht op bevestiging
- Controleren of er geen fouten verschijnen
+++

### Implementatie controleren

Het beveiligde formulier is nu beschikbaar op:

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/
<form-name>
```

**Voorbeeld URL:**

```
https://main--my-forms--company.aem.live/content/forms/af/
contact-us-form
```
