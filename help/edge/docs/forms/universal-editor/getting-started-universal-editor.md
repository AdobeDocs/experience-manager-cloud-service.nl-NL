---
title: Aan de slag met Edge Delivery Services for AEM Forms met de Universal Editor
description: Leer hoe u krachtige formulieren maakt en publiceert met Edge Delivery Services en de WYSIWYG-authoring van Universal Editor.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '2116'
ht-degree: 0%

---


# Aan de slag met Edge Delivery Services for AEM Forms met de Universal Editor

| Ontwerpmethode | Hulplijn |
|---------------------------------|-----------------------------------------------------------------------|
| **Universele Redacteur (WYSIWYG)** | Dit artikel |
| **op document-gebaseerde Authoring** | [ op document-Gebaseerde leerprogramma ](/help/edge/docs/forms/tutorial.md) |

Edge Delivery Services for AEM Forms combineert krachtige webservices met WYSIWYG authoring in Universal Editor. In deze handleiding vindt u het maken, aanpassen en publiceren van formulieren die snel worden geladen.

## Wat u gaat bereiken

Aan het einde van deze zelfstudie gaat u als volgt te werk:

- Een GitHub-opslagplaats instellen met het Adaptive Forms Block
- Een AEM-site maken die is geïntegreerd met Edge Delivery Services
- Formulieren maken en publiceren met de Universal Editor
- Lokale ontwikkelomgeving configureren

## Kies uw pad

Selecteer de benadering die uw scenario aanpast:

![ kies Uw Gids van het Besluit van de Weg ](/help/edge/docs/forms/universal-editor/assets/choose-your-path.svg)
*Figuur: Visuele gids om u te helpen de juiste implementatieweg* kiezen

| **Weg A: Nieuw Project** | **Weg B: Bestaand Project** |
|----------------------------------------|-------------------------------------------|
| Begin met een vooraf geconfigureerde sjabloon | Formulieren toevoegen aan uw huidige AEM-project |
| **Best voor:** Nieuwe implementaties | **Best voor:** Bestaande AEM Sites |
| **wat u krijgt:** Vooraf gevormd Blok van Forms | **wat u krijgt:** Forms die aan bestaande plaats wordt toegevoegd |
| **Stappen:** Malplaatje → Opstelling → Forms | **Stappen:** integratie → Configuratie → Forms |
| [ Begin met Weg A ](#path-a-create-new-project-with-forms) | [ Begin met Weg B ](#path-b-add-forms-to-existing-project) |

## Vereisten

Voordat u begint, moet u het volgende doen:

### Vereiste toegang

- **GitHub rekening** met toestemming om bewaarplaatsen tot stand te brengen
- **AEM as a Cloud Service** auteurstoegang

### Technische vereisten

- **de grondbeginselen van de Git**: kloon, begaat, duw verrichtingen
- **de technologieën van het Web**: HTML, CSS, de grondbeginselen van JavaScript
- **Node.js** (versie 16+ geadviseerd) voor lokale ontwikkeling
- **npm** of **garen** pakketmanager

### Aanbevolen kennis

- Basisbegrip van AEM Sites-concepten
- Kennis van de beginselen van het formulierontwerp
- Ervaring met WYSIWYG-editors

>[!TIP]
>
> Nieuw bij AEM? Begin met [ AEM Sites die Begonnen Gids ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html) wordt.

## Pad A: Nieuw project maken met Forms

**Best voor:** Nieuwe implementaties of bewijs-van-concepten

De AEM Forms Boilerplate biedt een vooraf geconfigureerde sjabloon met een geïntegreerd adaptief Forms Block.

### Overzicht van stappen

1. Opstelling een bewaarplaats van GitHub van het malplaatje
2. AEM Code Sync installeren
3. AEM-projectverbinding configureren
4. Een AEM-site maken en publiceren
5. Formulieren toevoegen met de Universal Editor

Laten we elke stap doorlopen:

+++Stap 1: Create GitHub Repository from Template

1. **heb toegang tot het malplaatje van AEM Forms Boilerplate**
   - Ga naar [ https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms)

   ![ AEM Forms Boilerplate Malplaatje ](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   *Cijfer: AEM Forms Boilerplate bewaarplaats met vooraf gevormd Adaptief Blok van Forms*

2. **creeer uw bewaarplaats**
   - Klik **Gebruik dit malplaatje** > **creeer een nieuwe bewaarplaats**

   ![ creeer Bewaarplaats van Malplaatje ](/help/edge/docs/forms/assets/use-eds-form-template.png)
   *Cijfer: Gebruikend het malplaatje om een nieuwe bewaarplaats* tot stand te brengen

3. **vorm bewaarplaats montages**
   - **Eigenaar**: Selecteer uw rekening GitHub of organisatie
   - **Naam van de Bewaarplaats**: Kies een beschrijvende naam (b.v., `my-forms-project`)
   - **Zichtbaarheid**: Selecteer **Openbaar** (geadviseerd voor Edge Delivery Services)
   - Klik **creeer Bewaarplaats**

   ![ Configuratie van de Bewaarplaats ](/help/edge/docs/forms/assets/name-eds-repo.png)
   *Cijfer: Het vormen van uw nieuwe bewaarplaats met openbaar zicht*

**Bevestiging:** bevestig u een nieuwe bewaarplaats GitHub hebt die op het malplaatje van AEM Forms wordt gebaseerd Boilerplate.

+++

+++Stap 2: AEM Code Sync installeren

Met AEM Code Sync worden wijzigingen in de inhoud automatisch gesynchroniseerd tussen uw AEM-ontwerpomgeving en uw GitHub-opslagplaats.

1. **installeer de App GitHub**
   - Ga naar [ https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new)

2. **vorm toegangstoestemmingen**
   - Selecteer **slechts uitgezochte bewaarplaatsen**
   - Kies uw nieuwe opslagplaats
   - Klik **sparen**

   ![ de Installatie van de Synchronisatie van de Code van AEM ](/help/edge/docs/forms/assets/aem-code-sync-up.png)
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

   ![ Creërend fstab.yaml- dossier ](/help/edge/docs/forms/assets/open-fstab.png)
   *Cijfer: Creërend het fstab.yaml configuratiedossier*

3. **voeg uw de verbindingsdetails van AEM toe**

   Kopieer en plak de volgende configuratie, waarbij u de plaatsaanduidingen vervangt:

   ```yaml
   mountpoints:
     /: https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main
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

   ![ het Uitgeven fstab.yaml- dossier ](/help/edge/docs/forms/assets/edit-fstab-file.png)
   *Cijfer: Het vormen van het bergpunt voor de integratie van AEM*

4. **zet de configuratie** vast
   - Voeg een commit message toe: &quot;Add AEM integration configuration&quot;
   - Klik **nieuw dossier** vastleggen

   ![ het Vastleggen van fstab veranderingen ](/help/edge/docs/forms/assets/commit-fstab-changes.png)
   *Cijfer: Het vastmaken van de configuratie fstab.yaml*

**Bevestig Bevestiging:** bevestig uw verbinding van de bewaarplaats GitHub aan AEM.

>[!NOTE]
>
>Hebt u problemen opgebouwd? Zie [ het oplossen van problemen GitHub bouwt kwesties ](#troubleshooting-github-build-issues).

+++

+++Stap 4: Creeer een Plaats van AEM die met uw bewaarplaats GitHub wordt verbonden.

1. **heb toegang tot de console van AEM Sites**
   - Aanmelden bij uw AEM as a Cloud Service-ontwerpinstantie
   - Ga aan **Plaatsen**

   ![ AEM Sites Console ](/help/edge/assets/select-sites.png)
   *Cijfer: Toegang tot de console van AEM Sites*

2. **de plaatsverwezenlijking van het Begin**
   - Klik **creëren** > **Plaats van malplaatje**

   ![ creeer de Optie van de Plaats ](/help/edge/docs/forms/assets/create-sites.png)
   *Cijfer: Creërend een nieuwe plaats van malplaatje*

3. **selecteer het malplaatje van Edge Delivery Services**
   - Kies het **malplaatje van de Plaats van Edge Delivery Services**
   - Klik **daarna**

   ![ de Selectie van het Malplaatje van de Plaats ](/help/edge/docs/forms/assets/select-site-template.png)
   *Cijfer: Het selecteren van het de plaatsmalplaatje van Edge Delivery Services*

   >[!NOTE]
   >
   >**niet beschikbaar Malplaatje?** Als de Edge Delivery Services-sjabloon niet wordt weergegeven:
   >
   >1. Klik **Invoer** om het malplaatje te uploaden
   >2. De malplaatjes van de download van [ versies GitHub ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases)

4. **vorm uw plaats**

   Voer de volgende gegevens in:

   | Veld | Waarde | Voorbeeld |
   |-----------------|-----------------------------|-----------------------------------------|
   | **Titel van de Plaats** | Beschrijvende naam voor site | &quot;Mijn Forms-project&quot; |
   | **Naam van de Plaats** | URL-vriendelijke naam | &quot;my-forms-project&quot; |
   | **GitHub URL** | URL van opslagplaats | `https://github.com/mycompany/my-forms-project` |

   ![ Configuratie van de Plaats ](/help/edge/docs/forms/assets/create-aem-site.png)
   *Cijfer: Het vormen van uw nieuwe plaats van AEM met integratie GitHub*

5. **Volledige plaatsverwezenlijking**
   - Uw instellingen controleren
   - Klik **creëren**

   ![ Bevestig de Creatie van de Plaats ](/help/edge/docs/forms/assets/click-ok-aem-site.png)
   *Cijfer: Bevestigend plaatsverwezenlijking*

   **Succes!** Uw AEM-site wordt nu gemaakt en verbonden met GitHub.

6. **Open in Universele Redacteur**
   - Zoek in de Sites-console uw nieuwe site
   - Selecteer de pagina `index`
   - Klik **uitgeven**

   ![ geef Plaats in Universele Redacteur ](/help/edge/docs/forms/assets/edit-site.png) uit
   *Cijfer: Het openen van uw plaats voor het uitgeven*

   De Universal Editor wordt op een nieuw tabblad geopend en biedt mogelijkheden voor het schrijven van WYSIWYG.

   ![ Universele Interface van de Redacteur ](/help/edge/docs/forms/assets/site-in-universal-editor.png)
   *Figuur: Uw plaats die in Universele Redacteur voor WYSIWYG wordt geopend die* uitgeeft

**Bevestiging:** bevestig uw plaats van AEM klaar voor vorm creatie is.

+++

+++Stap 5: Uw site publiceren

Door te publiceren maakt u uw site beschikbaar op Edge Delivery Services voor wereldwijde toegang.

1. **Snel publiceren van de console van Plaatsen**
   - Terug naar de AEM Sites-console
   - Selecteer uw sitepagina&#39;s (of selecteer alles met Ctrl+A)
   - Klik **Snel publiceren**

   ![ het Publiceren AEM Plaats ](/help/edge/docs/forms/assets/publish-sites.png)
   *Figuur: Het selecteren van pagina&#39;s voor snel publiceert*

2. **Bevestig het publiceren**
   - In de bevestigingsdialoog, klik **publiceren**

   ![ Snelle Publish Dialoog ](/help/edge/docs/forms/assets/quick-publish.png)
   *Cijfer: Bevestigend publiceer actie*

   **Alternatief:** u kunt direct van Universele Redacteur ook publiceren gebruikend publiceren knoop.

   ![ publiceer van Universele Redacteur ](/help/edge/docs/forms/assets/qui.png)
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

**daarna:** [ creeer uw eerste vorm ](#create-your-first-form)

+++

## Pad B: Forms toevoegen aan bestaand project

**Best voor:** Bestaande AEM Sites met Edge Delivery Services

Als u al een AEM-project hebt met Edge Delivery Services, kunt u formuliermogelijkheden toevoegen door het Adaptive Forms Block te integreren.

### Vereisten voor pad B

- Het bestaande project van AEM dat met [ wordt gebouwd AEM Boilerplate XWalk ](https://github.com/adobe-rnd/aem-boilerplate-xwalk)
- Plaatselijke ontwikkelomgeving ingesteld
- Toegang tot uw gegevensopslagruimte krijgen

**Gebruikend AEM Forms Boilerplate?** als uw project met [ AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms) werd gecreeerd, zijn de vormen reeds geïntegreerd. Skip aan [ creeer Uw Eerste Vorm ](#create-your-first-form).

Laten we elke stap doorlopen:

### Overzicht van stappen

1. Aangepaste Forms-blokbestanden kopiëren
2. Projectconfiguratie bijwerken
3. ESLint-regels configureren
4. Wijzigingen maken en toewijzen

+++Stap 1: Forms-blokbestanden kopiëren

1. **navigeer aan uw lokaal project**

   ```bash
   cd /path/to/your/aem-project
   ```

2. **Download vereiste dossiers van AEM Forms Boilerplate**

   Kopieer deze dossiers van de [ bewaarplaats van AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms):

   | Source | Doel | Doel |
   |------------------------------------------------------------------------|----------------------------|----------------------------|
   | [`blocks/form/`](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) | `blocks/form/` | Functionaliteit van kernformulieren |
   | [`scripts/form-editor-support.js`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) | `scripts/form-editor-support.js` | Integratie van Universal Editor |
   | [`scripts/form-editor-support.css`](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) | `scripts/form-editor-support.css` | Editor-opmaak |

3. **de redacteurssteun van de Update**
   - Vervang uw `/scripts/editor-support.js` dossier met [ redacteur-support.js van AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js)

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

+++Stap 4: Bouwen en implementeren

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

**daarna:** [ creeer Uw Eerste Vorm ](#create-your-first-form)

## Uw eerste formulier maken

**is op van toepassing:** zowel Weg A als de gebruikers van Weg B

Nu uw project is ingesteld met formuliermogelijkheden, maken we uw eerste formulier met de WYSIWYG-interface van Universal Editor.

### Overzicht van het proces voor het maken van formulieren

1. **voeg Aangepast Blok van de Vorm** aan uw pagina toe
2. **voeg vormcomponenten** (tekstinput, knopen, enz.) toe
3. **vorm componenteneigenschappen**
4. **Voorproef en test** uw vorm
5. **publiceer** de bijgewerkte pagina

Laten we elke stap doorlopen:

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

   ![ toevoegend Aangepast Blok van de Vorm ](/help/edge/docs/forms/assets/add-adaptive-form-block.png)
   *Cijfer: Het toevoegen van een Aangepast blok van de Vorm aan uw pagina*

**Bevestiging:** bevestig u een lege vormcontainer hebt.

+++

+++Stap 2: Formuliercomponenten toevoegen

1. **ga aan uw vormblok**
   - Zoek in de inhoudsstructuur de sectie Adaptief formulier die u zojuist hebt toegevoegd

   ![ Aangepast toegevoegd Blok van de Vorm ](/help/edge/docs/forms/assets/adative-form-block.png)
   *Cijfer: Het adaptieve blok van de Vorm in de inhoudsboom*

2. **voeg vormcomponenten** toe

   U kunt componenten op twee manieren toevoegen:

   **Methode A: Klik om toe te voegen**
   - Klik **toevoegen** (+) pictogram in uw vormsectie
   - Selecteer componenten van de **Adaptieve lijst van Componenten van de Vorm**

   **Methode B: Sleep en Daling**
   - Componenten rechtstreeks van het deelvenster Componenten naar het formulier slepen

   ![ toevoegend de Componenten van de Vorm ](/help/edge/docs/forms/assets/add-component.png)
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

   ![ het Comité van Eigenschappen van de Component ](/help/edge/docs/forms/assets/component-properties.png)
   *Cijfer: Het vormen componenteneigenschappen*

4. **Voorproef uw vorm**

   Uw formulier ziet er ongeveer als volgt uit:

   ![ Voltooide Voorproef van de Vorm ](/help/edge/docs/forms/assets/added-form-aem-sites.png)
   *Cijfer: De vorm van het voorbeeld die met Universele Redacteur* wordt gecreeerd

**Bevestiging:** bevestig uw vorm klaar voor het publiceren is.

>[!IMPORTANT]
>
> Vergeet niet uw pagina te publiceren nadat u wijzigingen hebt aangebracht om updates in de browser te zien.

+++

+++Stap 3: Uw formulier publiceren

1. **publiceer van Universele Redacteur**
   - Klik **publiceren** knoop in Universele Redacteur

   ![ het Publiceren Vorm ](/help/edge/docs/forms/assets/publish-form.png)
   *Cijfer: Het publiceren van uw vorm van Universele Redacteur*

2. **Bevestig het publiceren**
   - In de bevestigingsdialoog, klik **publiceren**

   ![ publiceer bevestiging ](/help/edge/docs/forms/assets/publish-form1.png)
   *Cijfer: Bevestigend publiceer actie*

   U ziet een succesbericht waarin de publicatie wordt bevestigd.

   ![ publiceer Succes ](/help/edge/docs/forms/assets/publish-form2.png)
   *Cijfer: Succesvolle publicatiebevestiging*

3. **Mening uw levende vorm**

   Uw formulier is nu live op:

   ```
   https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/
   ```

   **Voorbeeld URL:**

   ```
   https://main--my-forms-project--mycompany.aem.page/content/my-forms-project/
   ```

   ![ Levende Pagina van de Vorm ](/help/edge/docs/forms/assets/publish-index-page.png)
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
> **leer meer:** [ creeer standalone vormen in Universele Redacteur ](/help/edge/docs/forms/universal-editor/create-forms.md)

## Lokale ontwikkelomgeving instellen

**Best voor:** Ontwikkelaars die vorm het stileren en gedrag willen aanpassen

Met een lokale ontwikkelomgeving kunt u wijzigingen aanbrengen en deze direct bekijken zonder de publicatiecyclus te doorlopen.

++ AEM CLI en lokale ontwikkeling instellen

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

+++GitHub bouwt Kwesties

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

+++Universal Editor-problemen

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

