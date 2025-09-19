---
title: Forms Experience Builder implementeren en configureren
description: Leer hoe u met de Forms Experience Builder formulieren met progressieve openbaarmaking kunt maken en beheren voor alle gebruikerstypen
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: de524aeddd5f53cbd713ff0523222966752ebbc0
workflow-type: tm+mt
source-wordcount: '1404'
ht-degree: 0%

---


# Forms Experience Builder implementeren en configureren

>[!NOTE]
>
> De Forms Experience Builder is beschikbaar via een programma voor vroege toegang. Controleer voordat u begint of u toegang hebt aangevraagd en gekregen. Voor volledige instructies, zie [ onboarding ](product-overview.md#onboarding) informatie.

>[!IMPORTANT]
>
> **Documentatie onderworpen aan Verandering**: Deze documentatie wordt momenteel getest tegen het product en is onderworpen aan updates en revisies. De eigenschappen, de bevelen, en de voorbeelden kunnen veranderen aangezien de Bouwer van de Ervaring van Forms tijdens het Vroege programma van de Toegang blijft evolueren.

Deze uitgebreide handleiding helpt u om aan de slag te gaan met het maken en beheren van formulieren met behulp van conversationele AI-technologie. Of u nu een beginner bent die uw eerste formulier wil maken of een ervaren gebruiker die geavanceerde functies wil gebruiken, u vindt gedetailleerde informatie en praktische voorbeelden om uw reis door de mogelijkheden van Forms Experience Builder te begeleiden.

## Vereisten en instellen

### Toegangsvereisten

Voordat u Forms Experience Builder gaat gebruiken, moet u controleren of:

* **Toegang tot de Bouwer van de Ervaring van Forms** - Beschikbaar door het Vroege Programma van de Toegang
* **AEM Forms as a Cloud Service** - het milieu van de auteur van de productie met de AanpassingsComponenten van de Kern van Forms
* **Basis begrip** - vertrouwdheid met vormconcepten en bedrijfsvereisten

### Controleren of formulieren zijn ingeschakeld

Alvorens de Bouwer van de Ervaring van Forms te gebruiken, zorg ervoor [ AEM Forms voor uw milieu ](/help/forms/setup-forms-cloud-service.md) wordt toegelaten.

### Uw omgeving instellen

Uw installatieproces is afhankelijk van uw AEM Forms-implementatie. Kies het pad dat overeenkomt met uw project.

**voor Edge Delivery Services**

Als u Edge Delivery Services Forms gebruikt en vooral de Universal Editor. [ bereidt uw project voor Edge Delivery Services Forms ](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md) voor. Dit is een eenmalige installatie om de Forms Experience Builder te kunnen gebruiken.

**voor op componenten-Gebaseerde vormen van de Kern**

Als u Aangepaste Forms gebruikt die op de Componenten van de Kern in het auteursmilieu van AEM wordt gebaseerd, zorg [ de Aangepaste Componenten van de Kern van Forms ](/help/forms/enable-adaptive-forms-core-components.md) voor uw milieu wordt toegelaten.



## Snel starten

### De build voor formulierervaring openen

U hebt toegang tot de Forms Experience Builder vanaf drie primaire locaties, afhankelijk van uw workflow en formuliertype.


**1. De Adaptieve Redacteur van Forms (voor de Componenten van de Kern)**

U kunt de builder rechtstreeks starten terwijl u een specifiek formulier bewerkt.

1. Navigeer aan **AEM > Forms > Forms &amp; Documenten**.
1. [ creeer een nieuwe vorm gebruikend een malplaatje van de Componenten van de Kern ](/help/forms/creating-adaptive-form-core-components.md) of open bestaande.
1. Selecteer het **pictogram van de Bouwer van de Ervaring van Forms** in de toolbar van de redacteur om de gespreksinterface te openen.

   ![ AI Hulp pictogram* ](/help/edge/docs/forms/assets/adaptive-forms-editor.gif){width="75%"}

**1. Universele Redacteur (voor Edge Delivery Services Forms)**

Voor formulieren die via Edge Delivery Services worden geleverd, is de builder geïntegreerd in de Universal Editor.

1. Open uw Edge Delivery Services-formulier in de Universal Editor.
2. Selecteer het **pictogram van de Bouwer van de Ervaring van 0} Forms {in het juiste paneel om de gespreksinterface te lanceren.**

### Uw eerste formulier

| Voorbeeld van gesprek |   |
|--------------------------------------------------------------------------------------------------------------------------------------------|---|
| **probeer dit gesprek om een uitvoerige contactvorm tot stand te brengen (die op de demo van de Top wordt gebaseerd):**<br><br>**u:** &quot;creeer een contactvorm om persoonlijke informatie met inbegrip van volledige naam, e-mailadres, telefoonaantal, bedrijfsnaam, baantitel, en een berichtgebied voor onderzoeken&quot;AI te vangen:<br><br>**selecteer een malplaatje**    Een drop-down om een malplaatje <br> AI te selecteren:<br><br>**selecteer een thema**    Een drop-down om een thema <br> AI te selecteren:<br><br>**creeer Vorm** | ![ Uw Eerste Vorm ](/help/edge/docs/forms/assets/create-form.png) |
| <br>**AI:** Open Gemaakt Vorm | </br> Het formulier wordt gemaakt en geopend in de editor |


### Essentiële opdrachten

| Symbool | Doel | Voorbeeldengebruik |
|--------|---------|---------------|
| `/` | Snelle handelingen en sneltoetsen | `/create-form contact form`, `/help validation rules`, `/update-layout wizard` |
| `@` | Verwijzing naar bestaande formuliervelden | `@email`, `@firstName`, `Make @phoneNumber required` |
| Onbewerkte tekst | Natuurlijk gesprek | &quot;Voeg een vereist veld voor het telefoonnummer toe&quot;, &quot;Create validation for email&quot; |

**Specifieke Voorbeelden van het Bevel:**

* `/create-form customer survey` - Hiermee maakt u een nieuw formulier voor klantonderzoek
* `/add-field @email validation` - Hiermee voegt u validatie toe aan bestaand e-mailveld
* `/create-rule show @spouse if @maritalStatus equals married` - Maakt voorwaardelijke logica
* `/configure-submit to email support@company.com` - Hiermee wordt verzending via e-mail ingesteld
* `/help multi-step forms` - Haalt hulp op bij het maken van formulieren in meerdere stappen

### Tips voor succes

* **ben specifiek**: &quot;voeg een vereist e-mailgebied met bevestiging&quot;toe werkt beter dan &quot;voeg e-mail toe&quot;
* **Verwijzing bestaande gebieden**: Gebruik `@fieldName` wanneer het wijzigen van vormen
* **Vraag om hulp**: Type `/help` gevolgd door uw vraag
* **herhaalt**: Maak één verandering in een tijd voor beste resultaten


## Manieren om een formulier te maken

### Beginnen met aanwijzingen voor natuurlijke talen

Beschrijf uw formuliervereisten in natuurlijke taal en de Forms Experience Builder genereert de volledige formulierstructuur:

**Voorbeelden:**

* &quot;Een aanvraagformulier voor een lening maken met persoonlijke gegevens, financiële gegevens en het uploaden van documenten&quot;
* &quot;Maak een feedbackformulier voor klanten met beoordelingen, opmerkingen en productcategorieën&quot;
* &quot;Ik heb een meertrapsgewijs registratieformulier nodig voor een conferentie met betalingsverwerking&quot;


### Belangrijkste interacties

#### Formulierelementen toevoegen

**Basistoevoegingen:**

    👤 U: &quot;voeg een sectie voor persoonlijke informatie toe&quot;
    👤 U: &quot;omvat een dossierupload voor hervat&quot;
    👤 U: &quot;voeg een dropdown voor landselectie toe&quot;

**Gedetailleerde specificaties:**

    👤 U: &quot;Voeg een persoonlijk informatiepaneel met gebieden voor volledige naam, geboortedatum, telefoonaantal, en e-mailadres toe&quot;
    👤 U: &quot;omvat een veilige component van de dossierupload voor documenten, beperkt tot de dossiers van PDF onder 5MB&quot;
    👤 U: &quot;voeg een landdropdown met opties voor V.S., Canada, VK, en Duitsland toe&quot;

#### Dynamisch gedrag maken

**Eenvoudige logica:**

    👤 U: &quot;toon extra gebieden wanneer &quot;Andere&quot;wordt geselecteerd&quot;AI: &quot;Created a conditional rule that shows additional fields when &quot;Other&quot; is selected&quot;
    🤖 U: &quot;Make the email field required&quot;
    
    👤 AI: &quot;Updated the email field to be required with validation&quot;
    🤖 You: &quot;calculate the total automatically&quot;
    
    👤 AI: &quot;Added calculation logic to automatically compute totals&quot;
    🤖

**Complexe bedrijfsregels:**

    👤 U: &quot;toon de gebieden van de partnerinformatie slechts wanneer de huwelijksstatus aan &quot;Gehuwd&quot;wordt geplaatst:&quot;AI: &quot;creeerde een voorwaardelijke regel die de gebieden toont van de echtgeno(o)t op huwelijkse status wordt gebaseerd&quot;
    🤖 U: &quot;berekent de totale kosten door hoeveelheid en prijs te vermenigvuldigen, dan voeg 10% belasting&quot;dan toe AI: &quot;Toegevoegde berekeningslogica met hoeveelheid, prijs, en belastingberekening&quot;
    
    👤: Laat de verzendknoop toe slechts wanneer alle vereiste gebieden worden voltooid en de termijnen worden goedgekeurd&quot;
    🤖 AI: &quot;Gemaakt bevestigingslogica die voorlegging toelaat slechts wanneer alle voorwaarden worden voldaan aan&quot;
    
    👤
    🤖

#### Formulierindeling en -ontwerp

**de veranderingen van de Lay-out:**

    👤 U: &quot;maak dit een multi-step vorm&quot;
    🤖 AI: &quot;zette de vorm in een progressieve lay-out met navigatie&quot;om&quot;
    
    👤 U: &quot;organiseer gebieden in twee kolommen&quot;
    🤖 AI: &quot;werkte de lay-out aan vertoningsgebieden in een twee-kolomregeling&quot;bij 
    
    👤 U: &quot;Omzetten in een harmonielay-out&quot;
    🤖 AI: &quot;transformeerde de vorm om sectie in stijl te gebruiken 

**de verbeteringen van het Ontwerp:**

    👤 U: &quot;creeerde een tovenaar-stijl vorm met 3 stappen: persoonlijke info, voorkeur, en overzicht&quot;
    🤖 AI: &quot;creeerde een tovenaar vorm met drie verschillende stappen en navigatie&quot;
    
    👤 U: &quot;Rangschik de adresgebieden in een compacte twee-kolomlay-out&quot;
    🤖 AI: &quot;Georganiseerde adresgebieden in een compacte twee-kolomformaat&quot;
    
    👤 u: &quot;Werk de lay-out in aan 
    🤖 AI: &quot;Gewijzigd de lay-out om de verstrekte ontwerpverwijzing aan te passen&quot;

### Configuratie verzenden

De Forms Experience Builder kan verschillende verzendeindpunten configureren om uw formulieren te verbinden met externe systemen en services:

| Type handeling verzenden | Opdracht Instellen | Hoofdletters gebruiken |
|------------------|---------------|----------|
| **E-mail** | &quot;Formulier verzenden naar e-mail&quot; | Meldingen en bevestigingen voor het indienen van formulieren |
| **REST API** | &quot;Verzenden naar REST-eindpunt&quot; | Aangepaste toepassingen en systemen van derden |
| **Opslag van de Wolk** | &quot;Opslaan in Azure/SharePoint&quot; | Documentopslag en bestandsbeheer |
| **Workflow** | &quot;Verbinding maken met Power Automate&quot; | Automatisering en goedkeuring van bedrijfsprocessen |
| **Marketing** | &quot;Integreren met Marketo&quot; | Beheer van leads en automatisering van marketing |

**Geavanceerde voorlegt configuratievoorbeelden voor:**

    👤 U: &quot;Verzend vormverzendingen naar hr@company.com en creeer een geval in ons systeem van CRM&quot;
    🤖 AI: &quot;gevormde e-mail voorlegging en CRM voorlegt actie&quot;
    
    👤 U: &quot;voorlegt gegevens aan ons REST API eindpunt en teweegbrengt het nieuwe klantenwerkschema&quot;
    🤖 AI: &quot;De voorlegging van de Reparatie API van de Opstelling met werkschematriggers&quot;
    
    👤 U: &quot;E-reacties aan het verkoopteam en voegt de lood aan ons aan ons op aan ons marketing automatiseringsplatform toe&quot;
    🤖 AI: &quot;Gevormde multi-kanaals voorlegging met e-mail en marketing automatisering&quot;





## Geavanceerde formulierbewerkingen


### Complexe regel maken

Maak geavanceerde validatie- en bedrijfslogica die reageert op gebruikersinteracties en zorgt voor gegevensintegriteit:

    👤 U: &quot;toon de adressectie slechts als de gebruiker &quot;Schip aan verschillend adres&quot;selecteert \&quot;
    🤖 AI: &quot;creeerde een voorwaardelijke regel die het adrespaneel toont/verbergt dat op checkbox selectie wordt gebaseerd&quot;

### Formulier maken in meerdere stappen

    👤 U: &quot;creeer een progressieve vorm met 3 stappen: persoonlijke info, voorkeur, bevestiging&quot;
    🤖 AI: &quot;creeerde een progressieve vorm met navigatie tussen stappen en bevestiging in elk stadium&quot;

### Geavanceerde veldtypen

* Het uploaden van bestanden met validatie- en groottebeperkingen voor documentbeheer
* Datumkiezers met beperkingen en bedrijfsregels voor het plannen
* Vervolgkeuzelijsten met dynamische opties die worden gewijzigd op basis van gebruikersselecties
* Keuzerondjes met voorwaardelijke logica voor complexe beslissingsstructuren


### PDF naar formulierconversie

    👤 U: &quot;Convert this PDF into an interactive form&quot;
    🤖 AI: &quot;Analyzed the PDF and created a form with appropriate field types and validation&quot;





## Help en training voor producten

De Forms Experience Builder kan u ook leren over AEM Forms-functies:

### Stel vragen als:

* &quot;Hoe maak ik een formulier met meerdere stappen?&quot;
* &quot;Wat is het verschil tussen deelvensters en secties?&quot;
* &quot;Hoe kan ik e-mailmeldingen instellen?&quot;
* &quot;Wat zijn de beste praktijken voor mobiele vriendschappelijke vormen?&quot;
* &quot;Hoe kan ik thema&#39;s toepassen op mijn formulieren?&quot;

### Ga voor hulp naar:

* Concepten en terminologie van AEM Forms
* Stapsgewijze instructies voor complexe functies
* Aanbevolen werkwijzen en aanbevelingen
* Problemen met algemene problemen oplossen


Voor extra steun, verwijs naar de belangrijkste [ Snelle Bibliotheek van de Bouwer van de Ervaring van Forms ](/help/forms/experience-builder/forms-experience-builder-prompt-examples-library.md) of contacteer uw systeembeheerder voor technische bijstand.
