---
title: Adaptieve Forms met Edge Delivery Services publiceren
description: Leer hoe u Adaptive Forms kunt publiceren, configureren en benaderen met Edge Delivery Services voor productiegebruik.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
keywords: [formulieren publiceren, Edge Delivery Services, formulierconfiguratie, CORS, referentiefilter]
exl-id: ba1c608d-36e9-4ca1-b87b-0d1094d978db
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: 746
ht-degree: 0%

---

# Adaptieve Forms met Edge Delivery Services publiceren

Als u een adaptief formulier publiceert, kunt u het op Edge Delivery Services beschikbaar stellen voor eindgebruikers en verzenden. Dit proces omvat drie hoofdfasen: het publiceren van het formulier, het configureren van beveiligingsinstellingen en het openen van het actieve formulier.

**wat u zult verwezenlijken:**

- Uw formulier publiceren naar Edge Delivery Services
- Beveiligingsinstellingen configureren voor het verzenden van formulieren
- Uw gepubliceerde formulier openen en verifiëren
- Stel het juiste URL-routering en CORS-beleid in

## Vereisten

- Adaptief formulier gemaakt met Edge Delivery Services-sjabloon
- Beproefd formulier en gebruiksklaar voor productie
- Machtigingen voor AEM Forms-auteurs
- Cloud Manager-toegang (voor productieconfiguratie)
- Ontwikkelaarstoegang tot formulierblokcode (voor installatie van verzending)

## Overzicht van publicatieproces

Voor het publiceren van formulieren naar Edge Delivery Services geldt een driefasenaanpak:

- **Fase 1: De Publicatie van de vorm** - publiceer uw vorm aan CDN en verifieer publicatiestatus
- **Fase 2: De Configuratie van de veiligheid** - het beleid van CORS van de opstelling en verwijzerfilters voor veilige voorlegging
- **Fase 3: Toegang en Bevestiging** - de vormfunctionaliteit van de Test en bevestigt het volledige werkschema

Elke fase bouwt op vorige voort om veilige, functionele plaatsing te verzekeren.

### Fase 1: Uw formulier publiceren

+++ Stap 1: Publiceren starten

1. **heb toegang tot uw vorm**: Open uw AanpassingsVorm in de Universele Redacteur
2. **Begin het publiceren**: Klik **publiceren** pictogram in de toolbar

   ![ klik publiceren ](/help/forms/assets/publish-icon-eds-form.png)

+++


+++ Stap 2: Controleren en bevestigen

1. **Overzicht het publiceren activa**: Het systeem toont alle activa die, met inbegrip van uw vorm worden gepubliceerd

   ![ op Klik publiceren ](/help/forms/assets/on-click-publish.png)

2. **Bevestig het publiceren**: Klik **publiceren** te werk te gaan
3. **verifieer succes**: Zoek het bevestigingsbericht

   ![ publiceer Succes ](/help/forms/assets/publish-success.png)

+++


+++ Stap 3: Publicatiestatus verifiëren

**de status van de Controle**: Klik **publiceren** opnieuw pictogram om huidige status te bekijken

![ publiceer Status ](/help/forms/assets/publish-status.png)

**Controlepunt van de Bevestiging:**

- Het formulier toont de status &quot;Gepubliceerd&quot; in de editor
- Geen foutberichten tijdens publicatieproces
- Het formulier wordt weergegeven in de lijst met gepubliceerde elementen

+++


+++ Gepubliceerde Forms beheren

**om een vorm ongedaan te maken:**

1. Uw formulier openen in de editor
2. Klik op het menu met drie punten (⋯) in de rechterbovenhoek
3. Selecteer **Unpublish**

![ unpublish vorm ](/help/forms/assets/unpublish--form.png)

+++


### Fase 2: Beveiligingsinstellingen configureren

+++ Waarom de Configuratie van de Veiligheid wordt vereist

Om beveiligde formulierverzendingen in te schakelen, moet u beveiligingsinstellingen configureren die:

- Edge Delivery Services toestaan gegevens naar AEM te verzenden
- Ongeoorloofde toegang tot uw AEM-exemplaar voorkomen
- CORS inschakelen (Cross-Origin Resource Sharing) voor formulierverzendingen
- Aanvragen filteren om alleen legitieme Edge Delivery-domeinen toe te staan

>[!IMPORTANT]
>
>**Vereist voor Productie**: Deze configuraties zijn verplicht voor vormvoorlegging om in productiemilieu&#39;s te werken.

+++



+++ Stap 1: URL voor formulierverzending configureren

**Doel**: Directe vormbijdragen aan uw instantie van AEM

**Plaats van het Dossier**: `blocks/form/constant.js` in uw project van Edge Delivery Services

**Voorbeelden van de Configuratie:**

```javascript
// Production Environment
export const submitBaseUrl = 'https://publish-p120-e12.adobeaemcloud.com';

// Local Development Environment  
export const submitBaseUrl = 'http://localhost:4503';

// Staging Environment
export const submitBaseUrl = 'https://publish-staging-p120-e12.adobeaemcloud.com';
```

**Controlepunt van de Bevestiging:**

- `constant.js` bestand bijgewerkt met juiste AEM-publicatie-URL
- URL komt overeen met uw omgeving (productie, opbouw of lokaal)
- Geen slash in de URL

+++



+++ Stap 2: CORS-instellingen configureren

**Doel**: Toestaan de verzoeken van de vormvoorlegging van de domeinen van Edge Delivery Services

**Implementatie**: voeg configuratie CORS aan uw de verzender of configuratie van AEM Apache toe

```apache
# Local Development Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(http://localhost(:\d+)?$)#" CORSTrusted=true

# Edge Delivery Services - Preview/Stage Environment  
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.page$)#" CORSTrusted=true

# Edge Delivery Services - Production Environment
SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*\.hlx\.live$)#" CORSTrusted=true
```

**Controlepunt van de Bevestiging:**

- CORS-regels toegepast op de configuratie van de verzender
- Alle vereiste domeinen (localhost, hlx.page, hlx.live) worden opgenomen
- Configuratie geïmplementeerd in doelomgeving

**Documentatie van de Verwijzing:**

- [ de Gids van de Configuratie van CORS ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/getting-started-with-aem-headless/deployments/configurations/cors)
- [ Documentatie van de Filter van de Verwijzer ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/headless/deployment/referrer-filter)

+++



+++ Stap 3: Filter Referrer configureren

**Doel**: Beperk schrijven verrichtingen tot erkende domeinen van Edge Delivery Services

**Methode van de Implementatie**: Vorm via Cloud Manager in AEM as a Cloud Service

**Dossier van de Configuratie**: Voeg aan de configuratie van OSGi van uw project toe

```json
{
  "allow.empty": false,
  "allow.hosts": [],
  "allow.hosts.regexp": [
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

**Uitsplitsing van de Configuratie:**

- **`allow.empty`**: verwerpt aanvragen zonder verwijzingskoppen
- **`allow.hosts.regexp`**: geeft aanvragen van Edge Delivery Services-domeinen toestemming
- **`filter.methods`**: past filtering toe op deze HTTP-methoden
- **`exclude.agents.regexp`**: Gebruikersagenten uitgesloten van filteren

**Controlepunt van de Bevestiging:**

- Configuratie van het verwijzingsfilter geïmplementeerd via Cloud Manager
- Configuratie actief op AEM-publicatie-instantie
- Het verzenden van formulieren testen vanuit Edge Delivery Services-domein
- Niet-geautoriseerde domeinen kunnen geen formulieren verzenden

**Documentatie van de Verwijzing:**

- [ vorm de Filter van de Referateur via Cloud Manager ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing)

+++


### Fase 3: Toegang tot uw gepubliceerde formulier



+++ URL-structuur voor Edge Delivery Services

**StandaardFormaat URL:**

```
https://<branch>--<repo>--<owner>.aem.live/content/forms/af/<form_name>
```

**Componenten URL:**

- **`<branch>`**: naam van vertakking instellen (doorgaans `main` )
- **`<repo>`**: Naam opslagplaats
- **`<owner>`**: GitHub-organisatie of gebruikersnaam
- **`<form_name>`**: De naam van het formulier (kleine letters, afgebroken)

**milieu-Specifieke URLs:**

```
# Production Environment (.aem.live)
https://main--universaleditor--wkndforms.aem.live/content/forms/af/wknd-form

# Preview Environment (.aem.page) 
https://main--universaleditor--wkndforms.aem.page/content/forms/af/wknd-form
```

+++



+++ Eindvalidatiestappen

**verifieer de Toegankelijkheid van de Vorm:**

1. **vorm het laden van de Test**: Bezoek uw vorm URL en bevestig het behoorlijk laadt
2. **de vormvoorlegging van de Test**: Vul uit en verzend de vorm om gegevensverwerking te verifiëren
3. **Controle ontvankelijk ontwerp**: De vorm van de test op verschillende apparaten en schermgrootte
4. **bevestigt veiligheid**: Zorg CORS en verwijzersfilter correct werken

**Verwachte Resultaten:**

- Formulier wordt geladen zonder fouten
- Alle formuliervelden worden correct weergegeven
- Formulierverzendprocessen succesvol
- Gegevens worden weergegeven in de geconfigureerde bestemming (werkblad, e-mail, enz.)
- Geen consolefouten met betrekking tot CORS of veiligheidsbeleid

+++


## Volgende stappen


- [Formulierverzendacties configureren](/help/edge/docs/forms/universal-editor/submit-action.md)
- [Stijl en thema voor uw formulieren](/help/edge/docs/forms/universal-editor/style-theme-forms.md)
- [Responsieve formulierindelingen maken](/help/edge/docs/forms/universal-editor/responsive-layout.md)
- [reCAPTCHA-beveiliging toevoegen](/help/edge/docs/forms/universal-editor/recaptcha-forms.md)



