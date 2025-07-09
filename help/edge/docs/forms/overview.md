---
title: Overzicht Edge Delivery Services for AEM Forms
description: Leer hoe u Edge Delivery Services kunt gebruiken om krachtige formulieren te maken en te leveren met AEM Forms, waardoor u snel kunt ontwikkelen en gegevens gestroomlijnd kunt verzamelen.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: 1ddf97f56e5a9b7c95959da47a748f5a6d128e43
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---


# Edge Delivery Services voor AEM Forms


Edge Delivery Services for AEM Forms is een set services die een snelle ontwikkelomgeving mogelijk maakt waarin auteurs snel nieuwe formulieren kunnen bijwerken, publiceren en lanceren. Deze services bieden buitengewone en zeer belangrijke vormen van ervaring die de betrokkenheid en conversies stimuleren. Deze formulieren zijn gemakkelijk te ontwerpen en te ontwikkelen.

* **Snellere Ervaringen:** Forms wordt geleverd van een globaal Netwerk van de Levering van de Inhoud (CDN), ervoor zorgend zij snel voor gebruikers laden.
* **Snelle Ontwikkeling:** Een gestroomlijnd ontwikkelingsproces staat voor snellere updates toe. De veranderingen kunnen worden gepubliceerd zonder het wachten op lange pijpleidingsbouwwerken.
* **Flexibele Authoring:** Kies uit diverse gereedschappen om formulieren te maken, inclusief op documenten gebaseerde authoring (Microsoft Word, Google Docs/Sheets) of een visuele WYSIWYG-editor (Universal Editor).

## Hoe werkt het

Met Edge Delivery Services kunnen de structuur en inhoud van uw formulier zich bevinden in bronnen zoals AEM as a Cloud Service, Microsoft SharePoint of Google Drive. Deze inhoud wordt gepubliceerd naar een algemene CDN. Wanneer een gebruiker uw site bezoekt, wordt het formulier rechtstreeks vanaf de dichtstbijzijnde CDN-Edge-server aangeboden voor optimale prestaties.

![ Vereenvoudigd architectuurdiagram dat inhoudsbronnen, een CDN, en de gebruiker toont.](/help/forms/assets/eds-simplified-architecture.png)
**Vereenvoudigde Architectuur van Edge Delivery Services met Forms**

De gegevens die door gebruikers worden ingediend, kunnen naar verschillende bestemmingen worden verzonden, van een eenvoudig spreadsheet tot een krachtige AEM-backend voor verdere verwerking.

## Een ontwerpmethode kiezen

U kunt op verschillende manieren formulieren maken voor uw Edge Delivery Services-sites. De beste methode is afhankelijk van de vaardigheden van uw team, de complexiteit van het formulier en uw projectvereisten.

![ de boom van het Besluit helpen een vorm auteursmethode kiezen.](/help/forms/assets/eds-authoring-selection.png)
**de Boom van het Beslissingsbesluit van de Authoring van de Vorm**

### Authoring op basis van documenten

Deze methode staat u toe om vormen te creëren gebruikend Microsoft Word of Google Docs/Sheets [. ](/help/edge/docs/forms/create-forms.md) U definieert formuliervelden, labels en typen in een document met een specifieke tabelindeling. Edge Delivery Services converteert dit document naar een interactief HTML-formulier.

**Eigenschappen:**

* Auteur in vertrouwde gereedschappen: Word, Google Docs of Google Sheets.
* Definieer velden zoals tekstinvoer, e-mail, vervolgkeuzelijsten, selectievakjes en keuzerondjes.
* Stel basisvalidatieregels in, zoals vereiste velden.
* Integreer Google reCAPTCHA voor spambescherming.
* Ondersteuning voor het uploaden van bestanden.
* Gegevens rechtstreeks verzenden naar een spreadsheet of e-mailadres.
* Breid met douanecode via GitHub voor geavanceerde componenten en het stileren uit.

**Best voor:**

* Teams die vooral documenteditors gebruiken voor het maken van inhoud.
* Snel eenvoudige tot matig complexe formulieren maken.
* Eenvoudige gegevensverzameling naar een spreadsheet of e-mail.

De toestemmingen van op document-gebaseerde vormen worden typisch behandeld door de [ Dienst van de Verzending van AEM Forms ](/help/forms/forms-submission-service.md), die gegevens aan een gevormd spreadsheet of e-mailadres leidt.

### Universal Editor Authoring

De [ Universele Redacteur verstrekt een moderne, interface van WYSIWYG ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) voor de bouw van vormen met een belemmering-en-dalingservaring.

**Eigenschappen:**

* Het visuele, belemmering-en-dalingsvormgebouw met een bibliotheek van pre-gebouwde componenten.
* Configureer realtime validatie en complexe bedrijfslogica (geef/verberg bijvoorbeeld velden op basis van gebruikersselecties).
* Live voorvertoning voor verschillende apparaten.
* Diepe integratie met AEM as a Cloud Service-functies zoals Content Fragments, AEM Workflows en gebruikersmachtigingen.
* Met AI ondersteunde formulieren maken en bewerken via de &quot;Experience Builder&quot;.

**Best voor:**

* Complexe formulieren maken met voorwaardelijke logica, deelvensters met meerdere stappen of personalisatie.
* Teams (bijvoorbeeld marketers, zakelijke gebruikers) die de voorkeur geven aan visuele hulpmiddelen.
* Projecten die een sterke integratie met de AEM-backend vereisen voor gegevensverwerking en workflows.

Forms die met de Universele Redacteur wordt gebouwd kan de [ Verzenddienst van Forms gebruiken ](/help/forms/forms-submission-service.md) of worden gevormd om [ acties te gebruiken voorlegt die OOTB voor geavanceerde gegevensbehandeling ](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md), zoals het verzenden van gegevens naar een Werkschema van AEM, een eindpunt van REST, of aan een gegevensbestand worden verstrekt.

### Forms insluiten in pagina&#39;s voor het schrijven van documenten

[ Document Authoring (DA) ](https://www.aem.live/developer/da-tutorial) is een op Adobe gehoste service voor het beheer van website-inhoud voor Edge Delivery Services. Hoewel DA zelf geen formulieropbouwprogramma is, kunt u het gebruiken om webpagina&#39;s te ontwerpen en vervolgens formulieren in te sluiten die met andere methoden zijn gemaakt.

**hoe het werkt:**

1. **creeer de Vorm:** bouw uw vorm gebruikend of op document-Gebaseerde Authoring of de Universele Redacteur.
2. **publiceer de Vorm:** zorg de vorm wordt gepubliceerd en bij zijn eigen URL toegankelijk.
3. **bed in DA in:** op uw Document Authoring pagina, voeg een blok toe dat verwijzingen URL van de vorm om het in te bedden.

Deze aanpak geldt voor teams die Document Authoring gebruiken als primair contentbeheersysteem voor Edge Delivery Services-sites.

## Vergelijking ontwerpmethode

| Criteria | Authoring op basis van documenten | Universele editor (WYSIWYG) | Forms in Document Authoring (DA) |
|----------------------------------|---------------------------------------|-----------------------------------------|-------------------------------------------|
| **Primair Authoring Hulpmiddel** | Word/Google Docs/Sheets | Browser (AEM Universal Editor) | N/A (Forms is *ingebed*) |
| **Niveau van de Vaardigheid van het Team** | Kennis hebben van documenteditors | Compatibel met visuele webgereedschappen | Gebruikt DA voor pagina-inhoud |
| **Typische Complexiteit van de Vorm** | Eenvoudig tot matig | Modern tot complex, op bedrijfsniveau | Afhankelijk van het ingesloten formulier |
| **de Opties van de Verzending** | Forms-verzendservice (naar blad/e-mail) | Forms-verzendservice, AEM-publicatie (workflow, formuliergegevensmodel, integratie van derden) | Ingesloten formulier als volgt instellen |
| **AEM Backend Integratie** | Minimaal | Hoog (met publicatie in AEM) | Indirect, via ingesloten Universal Editor-formulier |
| **Best voor...** | Snelle gegevensvastlegging bij het maken van eenvoudige formulieren door inhoudteams. | Marketers en zakelijke gebruikers die behoefte hebben aan visuele controle, complexe formulieren of diepgaande AEM-integratie. | Sites waar de primaire inhoud wordt beheerd in DA. |

<!-- 
## Detailed Feature Comparison

| **Capability**                        | **Universal Editor (WYSIWYG)** | **Document-based Authoring** | **Document Authoring (DA)** |
|-----------------------------------------|-------------------------------|-----------------------------|-----------------------------|
| **Unified Composition with Sites**    | ✅                            |                              | ✅ (with embedded forms)     |
| **Embedding Form Support**            | ✅                            | ✅                          | ✅ (embed from Universal Editor or Docs)   |
| **Rules (Dynamic Behavior)**          | Advanced rules editor with custom functions | Limited: Show/hide, compute value, custom functions | Depends on embedded form     |
| **Attachment Support**                | ✅                            | ℹ️ (Early Access)           | Depends on embedded form     |
| **CAPTCHA Support**                   | reCAPTCHA Enterprise          | reCAPTCHA Enterprise       | Depends on embedded form     |
| **Submission Features**               | REST, Email, FDM, Workflow, SharePoint, OneDrive, Azure Blob, Power Automate, Workfront Fusion (EA) | Only Spreadsheet            | Follows embedded form's setup |
| **Data Schema**                       | FDM, Custom                   | Custom                      | Based on embedded form       |
| **Pre-fill**                          | 💡 (via Wizard)               | ✅                          | Depends on embedded form     |
| **Fragments**                         | ✅                            | ✅                          | Depends on embedded form     |
| **Visual Rule Editor**                | ✅                            |                              |                              |
| **Localization**                      | 💡 (via Sites)                | ℹ️ (Excel/Sheets manual)    | Depends on embedded form     |
| **Template Support**                  | Only Initial Content          |                              |                              |
| **Theme**                             | ℹ️ (at project level)         | ℹ️ (at project level)        | ℹ️ (based on hosting site)    |
| **Custom Component**                  | ✅                            | ✅                          | ✅ (if embedded component supports it) |
| **Experimentation**                   | ✅                            | ✅                          | Depends on embed context     |
| **Submit Action**                     | ✅                            | Only Spreadsheet            | Based on embedded form       |
-->



## Volgende stappen

* [Een formulier maken met op documenten gebaseerde ontwerpen](/help/edge/docs/forms/tutorial.md)
* [Meer informatie over de Universal Editor voor Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Formulierverzendacties configureren](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
* [ leer over Document Authoring (DA) ](https://www.aem.live/developer/da-tutorial)
