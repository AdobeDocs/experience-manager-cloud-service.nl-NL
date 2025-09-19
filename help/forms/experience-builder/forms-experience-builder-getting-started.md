---
title: Aan de slag met Forms Experience Builder
description: Leer de basisbeginselen van het maken van uw eerste AI-formulier met Forms Experience Builder. Stapsgewijze zelfstudie met voorbeelden en aanbevolen procedures.
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1133'
ht-degree: 0%

---


# Aan de slag met Forms Experience Builder {#getting-started-forms-experience-builder}

Forms Experience Builder maakt het maken van formulieren revolutionair door gebruik te maken van AI om beschrijvingen van natuurlijke talen om te zetten in volledig functionele digitale formulieren. Deze handleiding helpt u bij het maken van uw eerste formulier en bij het begrijpen van de basisconcepten die Forms Experience Builder krachtig maken.

## Wat is Forms Experience Builder? {#what-is-forms-experience-builder}

Forms Experience Builder is een door AI aangedreven programma voor het maken van formulieren waarmee u geavanceerde digitale formulieren kunt maken met behulp van een conversatietaal. In plaats van traditionele interfaces voor slepen en neerzetten of complexe codering beschrijft u gewoon wat u wilt en maakt de AI het formulier voor u.

**Zeer belangrijke mogelijkheden:**

* **de verwezenlijking van de Natuurlijke taalvorm** - beschrijf uw vormvereisten in duidelijk Engels

* **Intelligente invoer en omzetting** - zet bestaande documenten in interactieve vormen om

* **Slimme gebiedsgeneratie** - AI-Gerichte gebieden met pre-bevolkte opties

* **Bedrijfs logische automatisering** - creeer voorwaardelijke regels en bevestiging door gesprek

* **de integratie van het Systeem** - verbind vormen met uw bestaande bedrijfswerkschema&#39;s

## Vereisten {#prerequisites-getting-started}

Voordat u begint, moet u controleren of:

* **Toegang tot de Bouwer van de Ervaring van Forms** - Beschikbaar door het Vroege Programma van de Toegang
* **AEM Forms as a Cloud Service** - het milieu van de auteur van de productie met de AanpassingsComponenten van de Kern van Forms
* **Basis begrip** - vertrouwdheid met vormconcepten en bedrijfsvereisten

Voor gedetailleerde technische opstellingsvereisten en omgevingsconfiguratie, zie [ opstellen en de Bouwer van de Ervaring van Forms vormen ](deploy-forms-experience-builder.md).

## Manieren om formulieren te maken {#two-ways-to-create-forms}

Nadat u de Tovenaar van Forms gebruikt om het malplaatje van de Componenten van de a [ Kern ](/help/forms/creating-adaptive-form-core-components.md) of [ Edge Delivery Services ](/help/edge/docs/forms/universal-editor/create-forms.md) malplaatje, thema, en andere opties te selecteren, biedt de Bouwer van de Ervaring van Forms twee primaire benaderingen voor vormverwezenlijking aan:

### &#x200B;1. Geheel nieuw maken {#create-from-scratch}

Formulieren samenstellen met behulp van beschrijvingen van uw eigen taal.

**Wanneer te gebruiken:**

* Nieuwe formulieren maken op basis van vereisten

* Formulieren maken voor nieuwe bedrijfsprocessen

* Wanneer u duidelijke specificaties hebt maar geen bestaande documenten

**Voorbeeld:**

     creeer een klant terugkoppelt vorm met:
     - de Rating van het Product (1-5 sterren) 
     - het gebied van de Commentaar voor gedetailleerde terugkoppelt 
     - de e-mail van de Klant (facultatief) 
     - voorlegt aan e-mailbericht 

>[!VIDEO](https://video.tv.adobe.com/v/3473104)



### &#x200B;2. Importeren en converteren {#import-and-convert}

Bestaande documenten transformeren in interactieve digitale formulieren.

Voordat u deze optie gebruikt, uploadt u uw PDF-bestand of een afbeelding van het formulier. De PDF kan een AcroForm- of een XFA-gebaseerd PDF-formulier zijn. Voor [ andere types van PDF forms ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/forms/document-services/pdf-forms-and-documents), gebruik [ Voorbereiden de optie van de Vorm ](https://helpx.adobe.com/in/acrobat/using/creating-distributing-pdf-forms.html) in Adobe Acrobat om hen in een AcroForm om te zetten

**Wanneer te gebruiken:**

* Bestaande PDF forms converteren

* Modernisering van papieren processen

* Als u bestaande formulierontwerpen hebt die u wilt verbeteren

**Voorbeeld:**

     /create-form converteren het bijgevoegde PDF-bestand naar een adaptief formulier 

>[!VIDEO](https://video.tv.adobe.com/v/3474042)


## Uw eerste formulier: stapsgewijze zelfstudie {#first-form-tutorial}

Laten we een eenvoudig contactformulier maken om de basisworkflow te begrijpen.

### Stap 1: Begin met een eenvoudige beschrijving {#step-1-simple-description}

Beginnen met een basisformulierbeschrijving:

     creeer een basiscontactvorm met naam, e-mail, en berichtgebieden 

Hiermee maakt u een formulier met drie essentiële velden.

![ Vorm met drie essentieel gebied - gecreeerd gebruikend natuurlijke taalherinnering ](/help/forms/assets/forms-experience-builder-contact-us-form.png)

### Stap 2: Voeg validatie en vereisten toe {#step-2-add-validation}

Het formulier verbeteren met validatieregels:

     maak @name en @email verplichte gebieden met aangewezen bevestiging 

Het symbool `@` verwijst naar specifieke velden voor doelwijzigingen.

![ Toegevoegde bevestiging in de bouwer van de vormervaring gebruikend natuurlijke taalherinnering ](/help/forms/assets/forms-experience-builder-contact-us-form-add-validation.png)


### Stap 3: De gebruikerservaring verbeteren {#step-3-improve-ux}

Voeg nuttige plaatsaanduidingstekst en begeleiding toe:

     voegt placeholder tekst toe: @name &quot;Uw volledige naam&quot;, @email &quot;your.email@company.com&quot;, @message &quot;vertelt ons hoe wij kunnen helpen&quot;

![ Toegevoegde bevestiging die natuurlijke taalherinneringen in de bouwer van de vormervaring gebruikt ](/help/forms/assets/forms-experience-builder-contact-us-form-add-placeholder.png)

### Stap 4: Geavanceerde functies toevoegen {#step-4-advanced-features}

Inclusief extra functionaliteit:

     voegt twee dropdowns 
    
     toe - vraagType met opties: &quot;Algemene Vraag&quot;, &quot;Verzoek van de Steun&quot;, &quot;Onderzoek van de Verkoop&quot;, &quot;Partnerschap&quot;
    
     - urgentLevel met opties (Laag, Medium, Hoog) 


![ toegevoegde een dropdown componenten gebruikend natuurlijke taalherinneringen in de bouwer van de vormervaring ](/help/forms/assets/forms-experience-builder-contact-us-form-add-dropdown.png)


### Stap 5: Voorwaardelijke logica implementeren {#step-5-conditional-logic}

Creëer slim, context-bewust gedrag door regels zoals toe te voegen:

     verberg @priorityLevel dropdown op vormlading 
     toon @priorityLevel dropdown (Laag, Medium, Hoog) slechts wanneer @vraagType &quot;Verzoek van de Steun&quot;evenaart 

Dit zijn twee afzonderlijke regels: de ene regel verbergt de vervolgkeuzelijst met het urgentieniveau wanneer het formulier wordt geladen en de andere regel toont deze alleen wanneer het enquêtetype &quot;Ondersteuningsverzoek&quot; is. U moet elke regel met een afzonderlijke herinnering-slechts één regel tot stand brengen kan tegelijkertijd worden gecreeerd.

## De AI-gespreksbenadering begrijpen {#ai-conversation-approach}

De Bouwer van de Ervaring van Forms gebruikt een conversatie waar u kunt:

### Referentievelden met @-symbolen {#reference-fields}

Gebruik `@fieldName` om te verwijzen naar specifieke velden:

     maak @email een vereist gebied 
     bevestiging aan @phoneNumber voor het formaat van de V.S. 
     Verandering @submitButton tekst aan &quot;verzendt Bericht&quot;

>[!VIDEO](https://video.tv.adobe.com/v/3474043)


### Opdrachten voor natuurlijke talen gebruiken {#natural-language-commands}

Beschrijf wat u in duidelijk Engels wilt:

     - voeg een sectie voor bedrijfsinformatie 
     toe - creeer een dropdown voor afdelingsselectie 
     - omvat een dossier uploadt voor hervat 
     - opstelling e-mailberichten wanneer de vorm wordt voorgelegd 

### Stapsgewijs opbouwen {#build-incrementally}

Begin eenvoudig en voeg geleidelijk complexiteit toe:

1. **Basisstructuur** - creeer eerst de essentiële gebieden
2. **voeg bevestiging** toe - voer vereiste gebieden en formaatbevestiging uit
3. **verbeter UX** - voeg placeholders, hulptekst, en het stileren toe
4. **voert logica** uit - voeg voorwaardelijke regels en bedrijfslogica toe
5. **vorm voorlegging** - de verwerking en berichten van de opstelling vorm


## Veelvoorkomende formulierpatronen {#common-form-patterns}

### Contactformulieren en feedbackformulieren {#contact-feedback-forms}

**Basis contactvorm:**

     creeer een contactvorm met:
     - Naam (vereist) 
     - E-mail (vereist, bevestigd) 
     - Onderwerp dropdown (Algemeen, Steun, Verkoop, Partnerschap) 
     - Bericht (vereist, multi-lijn) 
     - voorlegt knoop 

**Klantenfeedback vorm:**

     creeer een klant terugkoppelt vorm met:
     - de Rating van het Product (1-5 sterren) 
     - het gebied van de Commentaar voor gedetailleerde terugkoppelt 
     - de e-mail van de Klant (facultatief) 
     - voorlegt aan e-mailbericht 

### Registratie- en instapformulieren {#registration-onboarding-forms}

**de registratie van de Gebruiker:**

     creeer een vorm van de gebruikersregistratie met:
     - Persoonlijke informatie (naam, e-mail, telefoon) 
     - de voorkeur van de Rekening (bulletin, berichten) 
     - de Termijnen en voorwaardenaanvaarding 
     - de verwezenlijking van het Wachtwoord met sterktebevestiging 

**Werknemer op het instappen:**

     creeer een werknemer op het instappen vorm met:
     - Persoonlijke details en contactinformatie 
     - de informatie van de Werkgelegenheid en begindatum 
     - het Document uploadt (hervat, identiteitskaart, belastingvormen) 
     - de selectie en voorkeur van Voordelen 

### Beoordeling- en beoordelingsformulieren {#survey-assessment-forms}

**het Tevredenheidsonderzoek van de Klant:**

     creeer een onderzoek van de klantentevredenheid met:
     - Algemene classificatie (1-10 schaal) 
     - de ratings van de Categorie (product, de dienst, steun) 
     - Open-eind koppelt secties 
     - Demografische informatie (facultatief) 

**beoordeling van Vaardigheden:**

     creeer een vorm van de vaardigheidsbeoordeling met:
     - de categorieën van de Vaardigheid met bekwaamheidsniveaus 
     - de duur van de Ervaring voor elke vaardigheid 
     - Certificatie en opleidingsinformatie 
     - Zelfbeoordeling en doelstellingen 

## Testen en valideren {#testing-validation}

### Uw formulieren altijd testen {#always-test-forms}

Voordat u een formulier implementeert:

1. **Test alle gebieden** - verzeker bevestigingswerk correct

2. **verifieer voorwaardelijke logica** - controleer dat de regels behoorlijk teweegbrengen

3. **voorlegging van de Test** - bevestig gegevens correct worden verwerkt

4. **bevestigt op verschillende apparaten** - verzeker mobiele verenigbaarheid

5. **Overzicht met stakeholders** - krijg terugkoppelen van eind - gebruikers

### Algemene validatiepatronen {#validation-patterns}

**E-mailbevestiging:**

     voeg e-mailformaatbevestiging aan @email gebied 
 toe
**de aantalbevestiging van de Telefoon:**

     voeg de formaatbevestiging van het Amerikaanse telefoonaantal aan @phoneNumber 
 toe
**bevestiging van de Leeftijd:**

     voeg leeftijdsbevestiging toe: moet 18 of ouder voor @dateOfBirth 
 zijn
**het uploadt van het Dossier bevestiging:**

     voeg dossiertype bevestiging toe: slechts PDF, DOC, DOCX toegestaan voor @resume 
     toevoegt de grens van de dossiergrootte: maximum 5MB voor @resume 

## Volgende stappen {#next-steps}

Nu u de grondbeginselen begrijpt, verkent u deze geavanceerde onderwerpen:

* **[LLM-Verbeterde slimme gebieden](forms-experience-builder-llm-smart-fields.md)** - creeer gebieden met pre-bevolkte opties gebruikend AI kennis
* **[AI-Gerichte vormverwezenlijking](forms-experience-builder-prompt-examples-library.md)** - Geavanceerde snelle patronen en voorbeelden
* **[Intelligente invoer en omzetting](intelligent-import-conversion.md)** - zet bestaande documenten in vormen om
* **[de voorlegging en integratie van de Vorm](form-submission-integration.md)** - verbind vormen met uw bedrijfssystemen


## Verwante artikelen

* [Overzicht van Forms Experience Builder](product-overview.md)
* [Met LLM verbeterde slimme velden](forms-experience-builder-llm-smart-fields.md)
* [Formulier maken met AI](forms-experience-builder-prompt-examples-library.md)
* [Intelligente import en conversie](intelligent-import-conversion.md)
* [Formulierverzending en integratie](form-submission-integration.md)
* [Veelgestelde vragen](forms-experience-builder-frequently-asked-questions.md)
