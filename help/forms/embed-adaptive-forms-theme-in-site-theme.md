---
title: Een Adaptief Forms-thema insluiten in een AEM Sites-thema
description: Leer hoe u een Adaptief Forms-thema (bijvoorbeeld Canvas) integreert in een AEM Sites-thema, zodat sitepagina's en ingesloten Adaptief Forms één uniform thema en één geïntegreerde implementatie delen.
keywords: thema voor adaptieve formulieren, sitethema, AEM Sites-thema, integratie van formulierthema's, front-end pijplijn, insluiten van thema's
feature: Adaptive Forms, Core Components
role: Developer
badgeSaas: label="AEM Forms" type="Positive" tooltip="van toepassing op AEM Forms)."
exl-id: 0607e11c-84d2-42cb-be9f-acd7c328a342
source-git-commit: 89b0f2a8ca9d2f60365a5c3962b0b4e826f79b3e
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Een Adaptief Forms-thema insluiten in een AEM Sites-thema

U kunt een Adaptief thema van Forms (zoals het [&#x200B; thema van het Canvas van AEM Forms &#x200B;](https://github.com/adobe/aem-forms-theme-canvas)) in uw thema van AEM Sites inbedden. Die manier, drijft één enkel thema zowel uw plaatspagina&#39;s als om het even welke Aangepaste Forms ingebed op die pagina&#39;s, met één bouwstijl en één plaatsing via de [&#x200B; Voorste-EindPijpleiding van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=nl-NL).

Dit artikel is bedoeld voor ontwikkelaars die het standaard (of aangepaste) AEM Sites-thema onderhouden of aanpassen en die adaptieve formulieropmaak willen opnemen zonder een aparte Forms-themaimplementatie te beheren.

## Vereisten {#prerequisites}

Voordat u begint, moet u controleren of:

* **AEM as a Cloud Service** met [&#x200B; Voorste-Eind Pijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=nl-NL) die voor uw plaatsthema wordt gevormd.
* **het themabronnen van de Plaats** - bijvoorbeeld, het [&#x200B; standaardthema van het plaatsmalplaatje &#x200B;](https://github.com/adobe/aem-site-template-standard) (het antwoord dat `theme/` met `src/theme.scss`, `src/components/`, etc. bevat).
* **de themabronnen van Forms** - het [&#x200B; thema van het Canvas van AEM Forms &#x200B;](https://github.com/adobe/aem-forms-theme-canvas) (of een ander compatibel Adaptief thema van Forms) gekloond of plaatselijk gedownload.
* **Node.js en npm** - om het plaatsthema (zie themaREADME voor gesteunde versies) te bouwen.
* **Gemaakt** - als u het volledige pakket van het plaatsmalplaatje (facultatief voor thema-slechts werk) bouwt.

## Stap 1: De map met adaptieve formuliercomponenten maken {#step-1-create-folder}

Maak in de site-themaopslagplaats de map waarin het Forms-thema zich bevindt:

```text
theme/src/components/adaptiveform/
```

Alle Forms-themaelementen bevinden zich onder deze map zodat ze gescheiden blijven van bestaande sitecomponenten.

## Stap 2: Forms-themacomponenten en -afbeeldingen kopiëren {#step-2-copy-components-and-images}

Gebruikend uw **thema van Forms** (bijvoorbeeld, `aem-forms-theme-canvas`) en uw **plaats thema** wegen:

1. **de componentenomslagen van het Exemplaar**\
   Kopieer vanuit het Forms-thema de volledige inhoud van `src/components/` naar het sitethema als:

   ```text
   theme/src/components/adaptiveform/
   ```

   Dus je krijgt paden als:

   ```text
   theme/src/components/adaptiveform/button/
   theme/src/components/adaptiveform/checkbox/
   theme/src/components/adaptiveform/container/
   … (one folder per component)
   ```

   ![&#x200B; voeg adaptieve vormcomponenten &#x200B;](/help/forms/assets/theme-add-adaptiveform-component.png) toe

2. **beelden van het Exemplaar**\
   Kopieer de Forms-themaafbeeldingen naar het sitethema:

   ```text
   Forms theme:  src/resources/images/*
   Site theme:   theme/src/components/adaptiveform/resources/images/
   ```

   Maak `theme/src/components/adaptiveform/resources/images/` als dit niet het geval is en kopieer vervolgens alle afbeeldingselementen (bijvoorbeeld `question.svg` , `Chevron-Left.svg` , `busy-state.gif` , enzovoort).

   ![&#x200B; voeg beelden &#x200B;](/help/forms/assets/theme-add-images.png) toe

## Stap 3: Variabelen en combinaties kopiëren {#step-3-copy-variables-and-mixins}

In het Forms-thema worden gedeelde variabelen en combinaties gebruikt onder `src/site/` . Kopieer slechts deze twee dossiers in de **wortel** van `adaptiveform/` (niet binnen a `site` subfolder):

| Source (thema Forms) | Doel (sitethema) |
|---------------------------|---------------------------------------------------|
| `src/site/_variables.scss` | `theme/src/components/adaptiveform/_variables.scss` |
| `src/site/_mixin.scss` | `theme/src/components/adaptiveform/_mixin.scss` |

Kopieer **&#x200B;**&#x200B;niet de rest van de omslag van het thema van Forms `src/site/`; slechts worden deze twee dossiers vereist voor de ingebedde vormstijlen.

![&#x200B; voegt variabelen en mengen &#x200B;](/help/forms/assets/theme-add-mixin-variable.png) toe

## Stap 4: Afbeeldingspaden corrigeren in SCSS {#step-4-fix-image-paths}

In het Forms-thema verwijzen SCSS-deelbestanden vaak naar afbeeldingen met paden zoals `./resources/` of `url(resources/` . Na het kopiëren naar het sitethema, moeten deze paden naar `theme/src/components/adaptiveform/resources/images/` verwijzen.

Het **standaardthema van het plaatssjabloon** gebruikt Pakket, dat `url()` wegen van `theme/src/` oplost. Gebruik dus het pad `theme/src/components/adaptiveform/resources/images/` (relatief ten opzichte van **`components/adaptiveform/resources/images/`** ) wanneer de afbeeldingen zich in `theme/src/` bevinden.

**vind en vervang** in elk `.scss` onder `theme/src/components/adaptiveform/`:

| Zoeken | Vervangen door |
|------|------------------|
| `./resources/` | `components/adaptiveform/resources/` |
| `url(resources/` | `url(components/adaptiveform/resources/` |
| `url('resources/` | `url('components/adaptiveform/resources/` |
| `url(../resources/` | `url(components/adaptiveform/resources/` |

**Voorbeeld** - vóór (het thema van Forms):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(./resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

**na** (plaatsthema, beelden in `adaptiveform/resources/images/`):

```scss
.cmp-adaptiveform-button__questionmark {
  background: url(components/adaptiveform/resources/images/question.svg) center center / cover no-repeat, #969696;
}
```

![&#x200B; de beelden URL van de Verandering &#x200B;](/help/forms/assets/theme-change-url.png)

Herhaal dit voor elk SCSS-bestand onder `adaptiveform/` dat verwijst naar afbeeldingen (knop, accordeon, wizard, container, krabbel en andere). Het wordt aanbevolen om in uw IDE via `theme/src/components/adaptiveform/` een zoek-/vervangactie voor het hele project uit te voeren.

## Stap 5: Maak het adaptieve form entry-point SCSS {#step-5-create-adaptiveform-scss}

Maak **`theme/src/components/adaptiveform/_adaptiveform.scss`** in het sitethema. Dit bestand moet:

1. Importeer de gedeelde variabelen en mixins.
2. Importeer het SCSS-hoofdbestand van elke adaptieve formuliercomponent.

Gebruik het volgende als het volledige ingangspunt (komt overeen met de standaardintegratie met alle op Core Components-gebaseerde formuliercomponenten):

```scss
//== Adaptive Form components (forms theme integration)
// Variables and mixins for adaptive form components
@import 'variables';
@import 'mixin';

//== Core adaptive form components
@import './button/_button.scss';
@import './checkboxgroup/_checkboxgroup.scss';
@import './container/_container.scss';
@import './datepicker/_datepicker.scss';
@import './dropdown/_dropdown.scss';
@import './fileinput/_fileinput.scss';
@import './footer/_footer.scss';
@import './image/_image.scss';
@import './numberinput/_numberinput.scss';
@import './panelcontainer/_panelcontainer.scss';
@import './radiobutton/_radiobutton.scss';
@import './text/_text.scss';
@import './textinput/_textinput.scss';
@import './accordion/_accordion.scss';
@import './tabsontop/_tabsontop.scss';
@import './pageheader/_pageheader.scss';
@import './wizard/_wizard.scss';
@import './title/_title.scss';
@import './telephoneinput/_telephoneinput.scss';
@import './emailinput/_emailinput.scss';
@import './recaptcha/_recaptcha.scss';
@import './verticaltabs/_verticaltabs.scss';
@import './checkbox/_checkbox.scss';
@import './termsandconditions/_termsandconditions.scss';
@import './switch/_switch.scss';
@import './hcaptcha/_hcaptcha.scss';
@import './turnstile/_turnstile.scss';
@import './review/_review.scss';
@import './scribble/_scribble.scss';
@import './datetime/_datetime.scss';
```

![&#x200B; adaptieve vorm scss &#x200B;](/help/forms/assets/theme-adaptive-form-scss.png)

Als uw Forms-thema bepaalde componenten weglaat (bijvoorbeeld geen krabbels of captcha), verwijdert of maakt u opmerkingen over de overeenkomende `@import` -regels om bouwfouten te voorkomen. De lijst hierboven past de [&#x200B; het themastructuur van het Canvas &#x200B;](https://github.com/adobe/aem-forms-theme-canvas) aan.

## Stap 6: Importeer het adaptieve formulierthema in het site-thema {#step-6-import-in-theme-scss}

In **`theme/src/theme.scss`**, voeg één enkele invoer bij het **eind** van het dossier (na andere componenteninvoer) toe:

```scss
//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

**Voorbeeld** - eind van `theme.scss`:

```scss
// ... existing site component imports ...
@import './components/embed/_embed.scss';
@import './components/pdfviewer/_pdfviewer.scss';
@import './components/socialmediasharing/_social_media_sharing.scss';

//== Adaptive Form components (forms theme)
@import './components/adaptiveform/_adaptiveform.scss';
```

![&#x200B; voeg adaptieve vormCSS &#x200B;](/help/forms/assets/theme-add-adaptive-form-scss-theme.png) toe

Dit is de enige vereiste wijziging in de bestaande sitethemastructuur. Alle formulierspecifieke code blijft onder `src/components/adaptiveform/` staan.

## Stap 7: Bouwen en implementeren {#step-7-build-and-deploy}

1. Bouw het thema van de plaats van de themawortel:

   ```bash
   cd theme
   npm install
   npm run build
   ```

   ![&#x200B; looppas bouwt &#x200B;](/help/forms/assets/theme-mpm-run-build.png)

2. Stel via uw bestaande [&#x200B; voor-EindPijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=nl-NL) op. Na de implementatie wordt hetzelfde thema-CSS toegepast op zowel sitepagina&#39;s als ingesloten Adaptive Forms.

## Problemen oplossen {#troubleshooting}

| Probleem | Te controleren wat |
|-------|-------------------------------|
| Build mislukt: &quot;bestand niet gevonden&quot; voor een afbeelding | Zorg ervoor dat alle formulierafbeeldingen zich in `theme/src/components/adaptiveform/resources/images/` bevinden. In elke `.scss` onder `adaptiveform/` gebruikt u `url(components/adaptiveform/resources/images/...)` , zodat het pad verdwijnt uit `theme/src/` (vereist voor de standaardversie van het sitemenu voor het samenstellen van pakketten met sitethema&#39;s). Gebruik `../resources/` of `resources/` alleen niet tenzij de bundelaar paden per bestand oplost. Gebruik vervolgens het pad dat overeenkomt met de afbeeldingsmap. |
| Build mislukt: &quot;file not found&quot; voor `_variables.scss` of `_mixin.scss` | Kopieer beide bestanden van het Forms-thema `src/site/` naar `theme/src/components/adaptiveform/` (de adaptiveform-hoofdmap), niet in een `site` -submap. |
| Build mislukt: &quot;bestand niet gevonden&quot; voor een component (bijvoorbeeld `_scribble.scss`) | Het Forms-thema bevat die component mogelijk niet. Verwijder in `theme/src/components/adaptiveform/_adaptiveform.scss` de regel `@import` voor die component of verwijder de regel. |
| Formulier wordt weergegeven, maar er zijn geen stijlen | Bevestig dat de pagina gebruikmaakt van de clientbibliotheek met het ingebouwde thema-CSS en dat `theme.scss` de `@import './components/adaptiveform/_adaptiveform.scss';` -regel bevat en het thema opnieuw is samengesteld en geïmplementeerd. |
| Stijlconflict tussen site- en formuliercomponenten | Klassen van formuliercomponenten krijgen een naam (bijvoorbeeld `cmp-adaptiveform-button`). Als u klassen ziet, controleert u of de CSS van de aangepaste site die klassen overschrijft en past u specificiteit of orde aan. |

## Zie ook {#see-also}

* [Thema&#39;s gebruiken om adaptieve Forms op basis van kerncomponenten te maken](/help/forms/using-themes-in-core-components.md)
* [&#x200B; ontwikkelt zich met Voorste-Eind Pijpleidingen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines.html?lang=nl-NL)
