---
title: Aan de slag met Edge Delivery Services for AEM Forms met de Universal Editor
description: Leer hoe u krachtige formulieren maakt en publiceert met Edge Delivery Services en de WYSIWYG-authoring van Universal Editor.
feature: Edge Delivery Services
role: Admin, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2608'
ht-degree: 0%

---


# Aan de slag met Edge Delivery Services for AEM Forms met de Universal Editor

| Ontwerpmethode | Hulplijn |
|---------------------------------|-----------------------------------------------------------------------|
| **Universele Redacteur (WYSIWYG)** | Dit artikel |
| **op document-gebaseerde Authoring** | [&#x200B; op document-Gebaseerde leerprogramma &#x200B;](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services for AEM Forms combineert krachtige webservices met WYSIWYG authoring in Universal Editor. In deze handleiding vindt u het maken, aanpassen en publiceren van formulieren die snel worden geladen.

## Wat u gaat bereiken

Aan het einde van deze zelfstudie gaat u als volgt te werk:

- Een GitHub-opslagplaats instellen met het Adaptive Forms Block
- Een AEM-site maken die is geïntegreerd met Edge Delivery Services
- Formulieren maken en publiceren met de Universal Editor
- Lokale ontwikkelomgeving configureren

## Kies uw pad

Selecteer de benadering die uw scenario aanpast:

![&#x200B; kies Uw Gids van het Besluit van de Weg &#x200B;](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*Figuur: Visuele gids om u te helpen de juiste implementatieweg* kiezen

| **Weg A: Nieuw Project** | **Weg B: Bestaand Project** |
|----------------------------------------|-------------------------------------------|
| Begin met een vooraf geconfigureerde sjabloon | Formulieren toevoegen aan uw huidige AEM-project |
| **Best voor:** Nieuwe implementaties | **Best voor:** Bestaande AEM Sites |
| **wat u krijgt:** Vooraf gevormd Blok van Forms | **wat u krijgt:** Forms die aan bestaande plaats wordt toegevoegd |
| **Stappen:** Malplaatje → Opstelling → Forms | **Stappen:** integratie → Configuratie → Forms |
| [&#x200B; Begin met Weg A &#x200B;](#path-a-create-new-project-with-forms) | [&#x200B; Begin met Weg B &#x200B;](#path-b-add-forms-to-existing-project) |

## Vereisten

Voor een vloeiende en geslaagde ervaring met Edge Delivery Services for AEM Forms met de Universal Editor, moet u de volgende voorwaarden controleren en bevestigen voordat u verdergaat:

### Toegangsvereisten

- **Rekening GitHub**: U moet een rekening GitHub met toestemmingen hebben om nieuwe bewaarplaatsen tot stand te brengen. Dit is essentieel voor het beheren van uw projectbroncode en het samenwerken met uw team.
- **Toegang van de Authoring van AEM as a Cloud Service**: Zorg ervoor u auteur-vlakke toegang tot uw milieu van AEM as a Cloud Service hebt. Deze toegang is vereist voor het maken, bewerken en publiceren van formulieren.

### Technische vereisten

- **Familiariteit met Git**: U zou comfortabel moeten zijn uitvoerend basishandelingen van het Git zoals het klonen bewaarplaatsen, het begaan van veranderingen, en het duwen van updates. Deze vaardigheden zijn fundamenteel voor broncontrole en projectsamenwerking.
- **Begrip van de Technologieën van het Web**: Een werkende kennis van HTML, CSS, en JavaScript wordt geadviseerd. Deze technologieën vormen de basis van formulieraanpassingen en probleemoplossing.
- **Node.js (versie 16 of hoger)**: Node.js wordt vereist voor lokale ontwikkeling en het runnen bouwt hulpmiddelen. Zorg ervoor dat versie 16 of hoger op uw systeem is geïnstalleerd.
- **de Manager van het Pakket (npm of garen)**: U zult of npm (de Manager van het Pakket van de Knoop) of garen nodig hebben om projectgebiedsdelen en manuscripten te beheren.

### Aanbevolen achtergrond

- **de Concepten van AEM Sites**: Een basisbegrip van AEM Sites, met inbegrip van plaatsstructuur en inhoud creatie, zal u helpen en vormen effectief integreren navigeren.
- **Beginselen van het Ontwerp van de Vorm**: De vertrouwdheid met beste praktijken in vorm ontwerp-zoals bruikbaarheid, toegankelijkheid, en gegevensbevestiging-zal u toelaten om efficiënte en gebruikersvriendelijke vormen tot stand te brengen.
- **Ervaring met WYSIWYG Editors**: De vroegere ervaring die redacteurs gebruikt van What You See Is What You Get (WYSIWYG) zal u hefboomwerking de visuele auteursmogelijkheden van de Universele Redacteur efficiënter helpen.

>[!TIP]
>
> Nieuw bij AEM? Begin met [&#x200B; AEM Sites die Begonnen Gids &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html) wordt.

## Pad A: Een nieuw project maken met Forms

**geadviseerd voor:** Nieuwe projecten, piloten, of bewijs-van-concept initiatieven

Gebruik de AEM Forms Boilerplate om uw projectopstelling te versnellen. Deze bouwsteen biedt een gebruiksklare sjabloon die het Adaptive Forms Block naadloos integreert, waarmee u snel formulieren kunt maken en implementeren binnen uw AEM-site.

### Overzicht

Als u uw nieuwe project met geïntegreerde formulieren wilt starten, gaat u als volgt te werk:

1. Maak een GitHub-opslagplaats met de AEM Forms Boilerplate-sjabloon.
2. Stel AEM Code Sync in om de synchronisatie van inhoud tussen AEM en uw repository te automatiseren.
3. Vorm de verbinding tussen uw project GitHub en uw milieu van AEM.
4. Een nieuwe AEM-site maken en publiceren.
5. Formulieren toevoegen en beheren met de Universal Editor.

De volgende secties zullen u door elke stap in detail begeleiden, die een vlotte en efficiënte ervaring verzekeren van de projectopstelling.

+++Stap 1: Create GitHub Repository from Template

1. **heb toegang tot het malplaatje van AEM Forms Boilerplate**
   - Ga naar [&#x200B; https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)

   ![&#x200B; AEM Forms Boilerplate Malplaatje &#x200B;](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *Cijfer: AEM Forms Boilerplate bewaarplaats met vooraf gevormd Adaptief Blok van Forms*

2. **creeer uw bewaarplaats**
   - Klik **Gebruik dit malplaatje** > **creeer een nieuwe bewaarplaats**

   ![&#x200B; creeer Bewaarplaats van Malplaatje &#x200B;](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *Cijfer: Gebruikend het malplaatje om een nieuwe bewaarplaats* tot stand te brengen

3. **vorm bewaarplaats montages**
   - **Eigenaar**: Selecteer uw rekening GitHub of organisatie
   - **Naam van de Bewaarplaats**: Kies een beschrijvende naam (b.v., `my-forms-project`)
   - **Zichtbaarheid**: Selecteer **Openbaar** (geadviseerd voor Edge Delivery Services)
   - Klik **creeer Bewaarplaats**

   ![&#x200B; Configuratie van de Bewaarplaats &#x200B;](/help/edge/docs/forms/assets/name-eds-repo.png)
   *Cijfer: Het vormen van uw nieuwe bewaarplaats met openbaar zicht*

**Bevestiging:** bevestig u een nieuwe bewaarplaats GitHub hebt die op het malplaatje van AEM Forms wordt gebaseerd Boilerplate.

+++

+++Stap 2: AEM Code Sync installeren

Met AEM Code Sync worden wijzigingen in de inhoud automatisch gesynchroniseerd tussen uw AEM-ontwerpomgeving en uw GitHub-opslagplaats.

1. **installeer de App GitHub**
   - Ga naar [&#x200B; https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)

2. **vorm toegangstoestemmingen**
   - Selecteer **slechts uitgezochte bewaarplaatsen**
   - Kies uw nieuwe opslagplaats
   - Klik **sparen**

   ![&#x200B; de Installatie van de Synchronisatie van de Code van AEM &#x200B;](/help/edge/docs/forms/assets/aem-code-sync-up.png)
   *Cijfer: Het installeren van de Synchronisatie van de Code van AEM met bewaarplaats-specifieke toestemmingen*

**Controlepunt:** de Synchronisatie van de Code van AEM is nu geïnstalleerd en heeft toegang tot uw bewaarplaats.

+++

+++Stap 3: AEM-integratie configureren

Het bestand `fstab.yaml` verbindt de GitHub-opslagplaats met de AEM-ontwerpomgeving voor inhoudssynchronisatie.

1. **navigeer aan uw bewaarplaats**
   - Ga naar uw nieuwe GitHub-opslagplaats
   - De AEM Forms Boilerplate-bestanden worden weergegeven

2. **creeer het fstab.yaml- dossier**
   - Klik **voeg dossier** toe > **creeer nieuw dossier** in de wortelfolder
   - Geef het bestand een naam `fstab.yaml`

   ![&#x200B; Creërend fstab.yaml- dossier &#x200B;](/help/edge/docs/forms/assets/open-fstab.png)
   *Cijfer: Creërend het fstab.yaml configuratiedossier*

3. **voeg uw de verbindingsdetails van AEM toe**

   Kopieer en plak de volgende configuratie, waarbij u de plaatsaanduidingen vervangt:

   ```yaml
   mountpoints:
     /: 
     url: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
     type: "markup" 
     suffix: ".html" 
   ```

   **vervang:**
   - `<aem-author>`: De URL van uw AEM as a Cloud Service-auteur (bijvoorbeeld `author-p12345-e67890.adobeaemcloud.com` )
   - `<owner>`: Uw GitHub-gebruikersnaam of -organisatie
   - `<repository>`: De naam van uw gegevensopslagruimte

   **Voorbeeld:**

   ```yaml
   mountpoints:
     /: https://author-p12345-e67890.adobeaemcloud.com/bin/franklin.delivery/mycompany/my-forms-project/main
   ```

   ![&#x200B; het Uitgeven fstab.yaml- dossier &#x200B;](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *Cijfer: Het vormen van het bergpunt voor de integratie van AEM*

4. **zet de configuratie** vast
   - Voeg een commit message toe: &quot;Add AEM integration configuration&quot;
   - Klik **nieuw dossier** vastleggen

   ![&#x200B; het Vastleggen van fstab veranderingen &#x200B;](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *Cijfer: Het vastmaken van de configuratie fstab.yaml*

**Bevestig Bevestiging:** bevestig uw verbinding van de bewaarplaats GitHub aan AEM.

>[!NOTE]
>
> Hebt u problemen opgebouwd? Zie [&#x200B; het oplossen van problemen GitHub bouwt kwesties &#x200B;](#troubleshooting-github-build-issues).

+++

+++Stap 4: Creeer een Plaats van AEM die met uw bewaarplaats GitHub wordt verbonden.

1. **heb toegang tot de console van AEM Sites**
   - Aanmelden bij uw AEM as a Cloud Service-ontwerpinstantie
   - Ga aan **Plaatsen**

   ![&#x200B; AEM Sites Console &#x200B;](/help/edge/assets/select-sites.png)
   *Cijfer: Toegang tot de console van AEM Sites*

2. **de plaatsverwezenlijking van het Begin**
   - Klik **creëren** > **Plaats van malplaatje**

   ![&#x200B; creeer de Optie van de Plaats &#x200B;](/help/edge/docs/forms/assets/create-sites.png)
   *Cijfer: Creërend een nieuwe plaats van malplaatje*

3. **selecteer het malplaatje van Edge Delivery Services**
   - Kies het **malplaatje van de Plaats van Edge Delivery Services**
   - Klik **daarna**

   ![&#x200B; de Selectie van het Malplaatje van de Plaats &#x200B;](/help/edge/docs/forms/assets/select-site-template.png)
   *Cijfer: Het selecteren van het de plaatsmalplaatje van Edge Delivery Services*

   >[!NOTE]
   >
   >**niet beschikbaar Malplaatje?** Als de Edge Delivery Services-sjabloon niet wordt weergegeven:
   >
   >1. Klik **Invoer** om het malplaatje te uploaden
   >2. De malplaatjes van de download van [&#x200B; versies GitHub &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)

4. **vorm uw plaats**

   Voer de volgende gegevens in:

   | Veld | Waarde | Voorbeeld |
   |-----------------|-----------------------------|-----------------------------------------|
   | **Titel van de Plaats** | Beschrijvende naam voor site | &quot;Mijn Forms-project&quot; |
   | **Naam van de Plaats** | URL-vriendelijke naam | &quot;my-forms-project&quot; |
   | **GitHub URL** | URL van opslagplaats | `https://github.com/mycompany/my-forms-project` |

   ![&#x200B; Configuratie van de Plaats &#x200B;](/help/edge/docs/forms/assets/create-aem-site.png)
   *Cijfer: Het vormen van uw nieuwe plaats van AEM met integratie GitHub*

5. **Volledige plaatsverwezenlijking**
   - Uw instellingen controleren
   - Klik **creëren**

   ![&#x200B; Bevestig de Creatie van de Plaats &#x200B;](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *Cijfer: Bevestigend plaatsverwezenlijking*

   **Succes!** Uw AEM-site wordt nu gemaakt en verbonden met GitHub.

6. **Open in Universele Redacteur**
   - Zoek in de Sites-console uw nieuwe site
   - Selecteer de pagina `index`
   - Klik **uitgeven**

   ![&#x200B; geef Plaats in Universele Redacteur &#x200B;](/help/edge/docs/forms/assets/edit-site.png) uit
   *Cijfer: Het openen van uw plaats voor het uitgeven*

   De Universal Editor wordt op een nieuw tabblad geopend en biedt mogelijkheden voor het schrijven van WYSIWYG.

   ![&#x200B; Universele Interface van de Redacteur &#x200B;](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *Figuur: Uw plaats die in Universele Redacteur voor WYSIWYG wordt geopend die* uitgeeft

**Bevestiging:** bevestig uw plaats van AEM klaar voor vorm creatie is.

+++

+++Stap 5: Uw site publiceren

Door te publiceren maakt u uw site beschikbaar op Edge Delivery Services voor wereldwijde toegang.

1. **Snel publiceren van de console van Plaatsen**
   - Terug naar de AEM Sites-console
   - Selecteer uw sitepagina&#39;s (of selecteer alles met Ctrl+A)
   - Klik **Snel publiceren**

   ![&#x200B; het Publiceren AEM Plaats &#x200B;](/help/edge/docs/forms/assets/publish-sites.png)
   *Figuur: Het selecteren van pagina&#39;s voor snel publiceert*

2. **Bevestig het publiceren**
   - In de bevestigingsdialoog, klik **publiceren**

   ![&#x200B; Snelle Publish Dialoog &#x200B;](/help/edge/docs/forms/assets/quick-publish.png)
   *Cijfer: Bevestigend publiceer actie*

   **Alternatief:** u kunt direct van Universele Redacteur ook publiceren gebruikend publiceren knoop.

   ![&#x200B; publiceer van Universele Redacteur &#x200B;](/help/edge/docs/forms/assets/qui.png)
   *Cijfer: Het publiceren direct van Universele Redacteur*

3. **toegang tot uw levende plaats**

   Uw site is nu live op:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Verklaarde Structuur URL:**
   - `<branch>`: GitHub-vertakking (gewoonlijk `main`)
   - `<repo>`: De naam van uw gegevensopslagruimte
   - `<owner>`: Uw GitHub-gebruikersnaam of -organisatie
   - `<site-name>`: De naam van uw AEM-site

   **Voorbeeld:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

**Bevestiging:** bevestig uw plaats op Edge Delivery Services levend is.

>[!TIP]
>
> **Patronen URL:**
>
> - **Homepage:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
> - **Andere pagina&#39;s:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<page-name>`

**daarna:** [&#x200B; creeer uw eerste vorm &#x200B;](#create-your-first-form)

+++

## Pad B: Forms toevoegen aan bestaand project

**Best voor:** Bestaande AEM Sites met Edge Delivery Services

Als u al een AEM-project hebt met Edge Delivery Services, kunt u formuliermogelijkheden toevoegen door het Adaptive Forms Block te integreren.

### Vereisten voor pad B

Als u formulieren wilt integreren in uw bestaande AEM-project, moet u aan de volgende voorwaarden voldoen:

- U hebt een bestaand project van AEM dat gebruikend [&#x200B; AEM Boilerplate XWalk &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-xwalk) werd gecreeerd.
- U hebt opstelling van het a [&#x200B; lokale ontwikkelmilieu &#x200B;](#set-up-local-development-environment)
- U hebt toegang tot uw projectopslagplaats, waardoor u wijzigingen kunt klonen, wijzigen en doorvoeren.

>[!NOTE]
>
> Als uw project oorspronkelijk opstelling gebruikend [&#x200B; AEM Forms Boilerplate &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-forms) was, is de vormfunctionaliteit reeds inbegrepen. In dit geval, kunt u zich naar [&#x200B; bewegen leidt tot Uw Eerste sectie van de Vorm &#x200B;](#create-your-first-form).

De volgende handleiding biedt een gestructureerde aanpak voor het toevoegen van formuliermogelijkheden aan uw bestaande project. Elke stap is ontworpen voor een naadloze integratie en optimale functionaliteit in de Universal Editor-omgeving.

### Overzicht

U voert de volgende stappen op hoog niveau uit:

1. Kopieer de Adaptive Forms Block-bestanden naar uw project.
2. Werk de configuratie van uw project bij om vormcomponenten te erkennen en te steunen.
3. Pas de regels ESLint aan om de nieuwe dossiers en coderingspatronen aan te passen.
4. Stel uw project samen en leg de wijzigingen vast aan uw opslagplaats.

+++Stap 1: Forms-blokbestanden kopiëren

1. **navigeer aan uw lokaal project**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **Download vereiste dossiers van AEM Forms Boilerplate**

   Kopieer deze dossiers van de [&#x200B; bewaarplaats van AEM Forms Boilerplate &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-forms):

   | Source | Doel | Doel |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | Functionaliteit van kernformulieren |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | Integratie van Universal Editor |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | Editor-opmaak |

3. **de redacteurssteun van de Update**
   - Vervang uw `/scripts/editor-support.js` dossier met [&#x200B; redacteur-support.js van AEM Forms Boilerplate &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)

**Bevestig Bevestiging:** bevestig de dossiers van het vormblok in uw project zijn.

+++

+++Stap 2: Component Configuration bijwerken

1. **het sectiemodel van de Update**

   Open `/models/_section.json` en voeg formuliercomponenten aan de filters toe:

   ```json
   {
        "filters": [
        {
      "id": "section",
      "components": [
           "text",
           "image",
           "button",
        "form",
        "embed-adaptive-form"
      ]
       }
     ]
   }
   ```

   **wat dit doet:** laat vormcomponenten in de Universele de componentenplukker van de Redacteur toe.

**Bevestig Bevestiging:** bevestig vormcomponenten verschijnen in Universele Redacteur.

+++

+++Stap 3: ESLint configureren (optioneel)

**waarom deze stap:** verhindert het verbinden fouten van vorm-specifieke dossiers en vormt juiste bevestigingsregels.

1. **Update.eslintignore**

   Voeg deze regels toe aan `/.eslintignore` :

   ```bash
   # Form block rule engine files
   blocks/form/rules/formula/*
   blocks/form/rules/model/*
   blocks/form/rules/functions.js
   scripts/editor-support.js
   scripts/editor-support-rte.js
   ```

2. **Update.eslintrc.js**

   Voeg de volgende regels toe aan het `rules` -object in `/.eslintrc.js` :

   ```javascript
   {
     "rules": {
       // Existing rules...
   
       // Form component cell limits
    'xwalk/max-cells': ['error', {
         '*': 4, // default limit
      form: 15,
      wizard: 12,
      'form-button': 7,
      'checkbox-group': 20,
      checkbox: 19,
      'date-input': 21,
      'drop-down': 19,
      email: 22,
      'file-input': 20,
      'form-fragment': 15,
      'form-image': 7,
      'multiline-input': 23,
      'number-input': 22,
      panel: 17,
      'radio-group': 20,
      'form-reset-button': 7,
      'form-submit-button': 7,
      'telephone-input': 20,
      'text-input': 23,
      accordion: 14,
      modal: 11,
      rating: 18,
      password: 20,
         tnc: 12
       }],
   
       // Disable this rule for forms
       'xwalk/no-orphan-collapsible-fields': 'off'
     }
   }
   ```

**Bevestiging:** bevestig werken ESLint met vormcomponenten.

+++

+++Stap 4: Opbouwen en implementeren

1. **installeer gebiedsdelen en bouwt**

   ```bash
   # Install any new dependencies
   npm install
   
   # Build component definitions
   npm run build:json
   ```

   **wat dit doet:**
   - Updates `component-definition.json` uitvoeren met formuliercomponenten
   - Genereert `component-models.json` met formuliermodellen
   - Creeert `component-filters.json` met het filtreren regels

2. **verifieer geproduceerde dossiers**

   Controleer of deze bestanden in de hoofdmap van het project formuliergerelateerde objecten bevatten:
   - `component-definition.json`
   - `component-models.json`
   - `component-filters.json`

3. **verbind en duw veranderingen**

   ```bash
   git add .
   git commit -m "Add Adaptive Forms Block integration"
   git push origin main
   ```

**Bevestiging:** bevestig uw project vormmogelijkheden omvat.

+++

**daarna:** [&#x200B; creeer Uw Eerste Vorm &#x200B;](#create-your-first-form)

## Uw eerste formulier maken

**die deze sectie zou moeten volgen:**\
Deze sectie is relevant voor gebruikers die of Weg A (nieuw project) of Weg B (bestaand project) volgen.

Met uw project dat nu is uitgerust voor het maken van formulieren, kunt u uw eerste formulier maken met de intuïtieve WYSIWYG-ontwerpomgeving van de Universal Editor. De volgende stappen bieden een gestructureerde aanpak voor het ontwerpen, configureren en publiceren van een formulier binnen uw AEM-site.

### Overzicht

Het proces voor het maken van een formulier in de Universal Editor bestaat uit verschillende belangrijke fasen:

1. **Tussenvoegsel het Adaptieve Blok van de Vorm**\
   Voeg eerst het Adaptief formulierblok toe aan de door u gekozen pagina.

2. **voeg de Componenten van de Vorm toe**\
   Vul het formulier door componenten in te voegen, zoals tekstvelden, knoppen en andere invoerelementen.

3. **vorm de Eigenschappen van de Component**\
   Pas de instellingen en eigenschappen van elke component aan aan de vereisten van het formulier aan.

4. **Voorproef en test Uw Vorm**\
   Gebruik de voorbeeldfunctionaliteit om de weergave en het gedrag van het formulier te valideren voordat u het publiceert.

5. **publiceer de Bijgewerkte Pagina**\
   Publiceer de pagina nadat deze is bevonden om het formulier beschikbaar te maken voor eindgebruikers.

In de volgende secties vindt u een gedetailleerde handleiding voor elk van deze stappen, zodat u over een vloeiende en effectieve manier beschikt om formulieren te maken.

+++Stap 1: Adaptief formulierblok toevoegen

1. **open uw pagina in Universele Redacteur**
   - Navigeer aan de **Sites** console in AEM
   - Selecteer de pagina waaraan u een formulier wilt toevoegen (bijvoorbeeld `index`)
   - Klik **uitgeven**

   De pagina wordt geopend in de Universal Editor voor bewerking in WYSIWYG.

2. **voeg de Adaptieve component van de Vorm** toe
   - Open het **paneel van de Boom van de Inhoud** (linkerzijbalk)
   - Ga naar een sectie waar u het formulier wilt toevoegen
   - Klik **toevoegen** (+) pictogram
   - Selecteer **Aangepaste Vorm** van de componentenlijst

   ![&#x200B; toevoegend Aangepast Blok van de Vorm &#x200B;](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *Cijfer: Het toevoegen van een Aangepast blok van de Vorm aan uw pagina*

**Bevestiging:** bevestig u een lege vormcontainer hebt.

+++

+++Stap 2: Formuliercomponenten toevoegen

1. **ga aan uw vormblok**
   - Zoek in de inhoudsstructuur de sectie Adaptief formulier die u zojuist hebt toegevoegd

   ![&#x200B; Aangepast toegevoegd Blok van de Vorm &#x200B;](/help/edge/docs/forms/assets/adative-form-block.png)
   *Cijfer: Het adaptieve blok van de Vorm in de inhoudsboom*

2. **voeg vormcomponenten** toe

   U kunt componenten op twee manieren toevoegen:

   **Methode A: Klik om toe te voegen**
   - Klik **toevoegen** (+) pictogram in uw vormsectie
   - Selecteer componenten van de **Adaptieve lijst van Componenten van de Vorm**

   **Methode B: Sleep en Daling**
   - Componenten rechtstreeks van het deelvenster Componenten naar het formulier slepen

   ![&#x200B; toevoegend de Componenten van de Vorm &#x200B;](/help/edge/docs/forms/assets/add-component.png)
   *Cijfer: Het toevoegen van componenten aan uw vorm*

   **geadviseerde startercomponenten:**
   - Tekstinvoer (voor naam, e-mail)
   - Tekstgebied (voor berichten)
   - Verzendknop

3. **vorm componenteneigenschappen**
   - Een formuliercomponent selecteren
   - Gebruik het **paneel van Eigenschappen** (juiste sidebar) om te vormen:
      - Labels en plaatsaanduidingen
      - Validatieregels
      - Vereiste veldinstellingen

   ![&#x200B; het Comité van Eigenschappen van de Component &#x200B;](/help/edge/docs/forms/assets/component-properties.png)
   *Cijfer: Het vormen componenteneigenschappen*

4. **Voorproef uw vorm**

   Uw formulier ziet er ongeveer als volgt uit:

   ![&#x200B; Voltooide Voorproef van de Vorm &#x200B;](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *Cijfer: De vorm van het voorbeeld die met Universele Redacteur* wordt gecreeerd

**Bevestiging:** bevestig uw vorm klaar voor het publiceren is.

>[!IMPORTANT]
>
> Vergeet niet uw pagina te publiceren nadat u wijzigingen hebt aangebracht om updates in de browser te zien.

+++

+++Stap 3: Uw formulier publiceren

1. **publiceer van Universele Redacteur**
   - Klik **publiceren** knoop in Universele Redacteur

   ![&#x200B; het Publiceren Vorm &#x200B;](/help/edge/docs/forms/assets/publish-form.png)
   *Cijfer: Het publiceren van uw vorm van Universele Redacteur*

2. **Bevestig het publiceren**
   - In de bevestigingsdialoog, klik **publiceren**

   ![&#x200B; publiceer bevestiging &#x200B;](/help/edge/docs/forms/assets/publish-form1.png)
   *Cijfer: Bevestigend publiceer actie*

   U ziet een succesbericht waarin de publicatie wordt bevestigd.

   ![&#x200B; publiceer Succes &#x200B;](/help/edge/docs/forms/assets/publish-form2.png)
   *Cijfer: Succesvolle publicatiebevestiging*

3. **Mening uw levende vorm**

   Uw formulier is nu live op:

   ```
   https://<branch>--<repo>--<owner>.aem.live/content/<site-name>/
   ```

   **Voorbeeld URL:**

   ```
   https://main--my-forms-project--mycompany.aem.live/content/my-forms-project/
   ```

   ![&#x200B; Levende Pagina van de Vorm &#x200B;](/help/edge/docs/forms/assets/publish-index-page.png)
   *Cijfer: Uw gepubliceerde vormpagina op Edge Delivery Services*

**Gefeliciteerd!** Uw formulier is nu live en klaar om opmerkingen te verzamelen.

+++

### Volgende stappen

Nu u een werkformulier hebt, kunt u:

- **pas het stileren** door CSS en de dossiers van JavaScript uit te geven aan
- **voeg geavanceerde vormeigenschappen** als bevestigingsregels en voorwaardelijke logica toe
- **opstelling lokale ontwikkeling** voor snellere herhaling
- **creeer standalone vormen** voor specifieke gebruiksgevallen

>[!TIP]
>
> **leer meer:** [&#x200B; creeer standalone vormen in Universele Redacteur &#x200B;](/help/edge/docs/forms/universal-editor/create-forms.md)

## Lokale ontwikkelomgeving instellen

**Best voor:** Ontwikkelaars die vorm het stileren en gedrag willen aanpassen

Met een lokale ontwikkelomgeving kunt u wijzigingen aanbrengen en deze direct bekijken zonder de publicatiecyclus te doorlopen.

+++AEM CLI en lokale ontwikkeling instellen

1. **installeer AEM CLI**

   De AEM CLI vereenvoudigt lokale ontwikkelingstaken:

   ```bash
       npm install -g @adobe/aem-cli
   ```

2. **Kloon uw bewaarplaats**

   ```bash
   git clone https://github.com/<owner>/<repo>
   cd <repo>
   ```

   Vervang `<owner>` en `<repo>` door de werkelijke GitHub-gegevens.

3. **Begin de lokale ontwikkelingsserver**

   ```bash
   aem up
   ```

   Hiermee start u een lokale server met hot-reload-mogelijkheden.

4. **maak aanpassingen**

   - Bestanden in de map `blocks/form/` bewerken voor formulieropmaak en -gedrag
   - Wijzigen `form.css` voor opmaak
   - `form.js` bijwerken voor gedrag

   **zie onmiddellijk veranderingen** in uw browser bij `http://localhost:3000`

5. **stel uw veranderingen** op

   ```bash
   git add .
   git commit -m "Custom form styling"
   git push origin main
   ```

   Uw wijzigingen zijn beschikbaar op:
   - **Voorproef:** `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`
   - **Productie:** `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`

+++


## Problemen oplossen

### Veelvoorkomende problemen en oplossingen

+++GitHub Build Issues

**Probleem:** bouwt mislukkingen of het verbinden fouten

**Oplossing 1: De Fouten van de handvat het Linting**

Als er verbindingsfouten optreden:

1. `package.json` openen in de hoofdmap van het project
2. Zoek het script `lint` :

   ```json
   "scripts": {
     "lint": "npm run lint:js && npm run lint:css"
   }
   ```

3. Koppeling tijdelijk uitschakelen:

   ```json
   "scripts": {
     "lint": "echo 'skipping linting for now'"
   }
   ```

4. De wijzigingen vastleggen en duwen

**Oplossing 2: De Fouten van de Weg van de module**

Als u &quot;Kan pad naar module &#39;/scripts/lib-franklin.js&#39; niet omzetten:

1. Navigeren naar `blocks/form/form.js`
2. De instructie import bijwerken:

   ```javascript
   // Change this:
   import { ... } from '/scripts/lib-franklin.js';
   
   // To this:
   import { ... } from '/scripts/aem.js';
   ```

+++

+++Problemen met formulierfunctionaliteit

**Probleem:** de inzendingen van de vorm werken niet

**Oplossingen:**

- Controleer of u een verzendknopcomponent hebt
- URL-configuratie van formulieractie controleren
- Formuliervalidatieregels controleren
- Testen in voorvertoningsmodus eerst

**Probleem:** het stileren kwesties

**Oplossingen:**

- CSS-bestandspaden controleren in `blocks/form/`
- Browser-cache wissen
- CSS-syntaxis verifiëren
- Testen in de lokale ontwikkelomgeving

+++

+++Problemen met de Universal Editor

**Probleem:** de componenten van de Vorm verschijnen niet in Universele Redacteur

**Oplossingen:**

- Controleren of AEM Code Sync is geïnstalleerd en uitgevoerd
- Controleer of `fstab.yaml` de juiste URL van de AEM-auteur heeft
- Zorg ervoor dat uw AEM-instantie vroege toegang heeft ingeschakeld
- `component-definition.json` bevestigen bevat formuliercomponenten

**Probleem:** Veranderingen niet zichtbaar na het publiceren

**Oplossingen:**

- Wacht op CDN-cache vernieuwen
- Browser cache controleren (modus Incognito/Private proberen)
- Controleren of de juiste URL-indeling wordt gebruikt

+++



