---
title: Taak voor maken van formulier
description: Leer meer over de functie voor het maken van formulieren door de Brand Experience Agent en hoe u natuurlijke taal kunt gebruiken om geheel nieuwe formulieren te maken.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 24ad5f36-405b-4ea2-9819-de6aea856a7a
source-git-commit: 36f4ba8207da67b8e68c9c9851311defc909b495
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Taak voor maken van formulier {#form-creation-job}

De baan van de vormverwezenlijking is een vermogen van de [&#x200B; Agent van de Ervaring van het Merk &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) die wordt ontworpen om vormen te ontwikkelen gebruikend natuurlijke taalherinneringen. Deze taak genereert automatisch de juiste formulierstructuur en veldtypen. De taak wordt weergegeven via AI Assistant.

Enkele belangrijke voordelen van het maken van formulieren zijn onder andere:

* **versnelde vormontwikkeling**: Creeer snel vormen gebruikend eenvoudige natuurlijke taalbevelen, die de behoefte elimineren om traditionele productinterfaces te leren.
* **Consistente en op-brand ervaringen**: Creeer vormen die branding van uw organisatie, malplaatjes, en stijlrichtlijnen door goedgekeurde malplaatjes en stijlen te gebruiken volgen.
* **Lagere technische barrière**: Sta bedrijfsgebruikers toe om vormen gemakkelijk tot stand te brengen, zonder het vereisen van geavanceerde technische of diepe productdeskundigheid.

## Mogelijkheden {#capabilities}

* **creeer een nieuwe vorm met duidelijke tekstherinnering**: U kunt een vorm tot stand brengen door uw vereisten in gewone taal voor te leggen. De vaardigheid produceert automatisch aangewezen vormstructuur, gebiedstypes, en merkervaringen op basis van uw natuurlijke taalbeschrijving en gespecificeerd malplaatje. Deze mogelijkheid versnelt het maken van formulieren en zorgt ervoor dat de standaarden voor merk en naleving worden gehandhaafd.

* **de Invoer een document van PDF en zet het in vorm** om: U kunt bestaande documenten van PDF in vormen invoeren en omzetten. De vaardigheid analyseert geüploade inhoud om veldtypes te ontdekken, lay-outs te bewaren, en vormen met ontvankelijke ontwerp en bevestigingslogica te verbeteren terwijl het verzekeren van merk en nalevingsnormen wordt gehandhaafd.

Als u een van deze mogelijkheden gebruikt, wordt u gevraagd het type formulier te kiezen dat u wilt maken. Geef een adaptieve formuliersjabloon voor Core Components (Basiscomponenten) of een adaptieve formuliersjabloon voor Edge Delivery Services op en geef aan welk pad u het formulier wilt opslaan. Als u een formulier maakt dat is gebaseerd op Edge Delivery Services, kunt u ook de GitHub-URL van de gegevensopslagruimte opgeven.


### Voorbeeldvragen {#sample-prompts}

* *creeer een vorm voor terugkoppel inzameling met naam, e-mail, en berichtgebieden*
* *creeer een klant terugkoppelt vorm met productclassificatie (1-5 sterren), commentaargebied, en facultatieve e-mail*
* *bouwt een contactvorm met naam, e-mail, onderwerpdrop, en berichtgebieden*
* *creeer een registratieformulier met persoonlijke informatie, rekeningsvoorkeur, en termen aanvaarding*
* *creeer een vorm van de creditcardtoepassing door het dossier van PDF in te voeren beschikbaar bij`https://[aem-author-url]/path/to/pdf/file`*
* *creeer een terugkoppel vorm gebruikend boilerplate bij`https://github.com/wkndforms/wesecure`*

## Uw formulier verfijnen {#refine-with-forms-experience-builder}

Nadat u de initiële formulierstructuur hebt gemaakt met de AI Assistant, kunt u de Forms Experience Builder gebruiken om:

* **vormen van de Update**: Voeg of wijzig gebieden toe, pas gebiedstypes aan, en werk het stileren zoals nodig door de visuele redacteur bij.

* **Lay-out van de Update**: Herschik secties, groepen, of gebieden, pas het uit elkaar plaatsen aan, en wijzig de visuele hiërarchie om bruikbaarheid te verbeteren en uw vorm duidelijk en intuïtief voor uw publiek te verzekeren.

* **voegt bedrijfslogica** toe: Creeer voorwaardelijke logica, toon/verberg regels, gebiedsdelen, en bepaal bevestigingsregels.

* **vorm voorlegging**: Vorm waar de vormgegevens, met inbegrip van vestiging e-mailberichten, integratie met werkschema&#39;s, of verbindingen aan externe systemen worden voorgelegd.

Voor meer informatie, zie {de documentatie van de Bouwer van de Ervaring van 0} Forms.[&#128279;](/help/forms/experience-builder/product-overview.md)

## Activering {#activation}

U kunt de Agenten van AEM door [&#x200B; Playground &#x200B;](https://www.aem.live/developer/aem-playground) onderzoeken, of met uw CSM of TAM verbinden om toegang via Agentic SKU te bespreken.

<!-- 
#### Import and convert {#import-and-convert}

Transform existing documents into interactive digital forms. The agent analyzes uploaded content to detect field types, preserve layouts, and enhance forms with responsive design and validation logic. Supported formats include Acroforms, XFA PDFs, flat PDFs, images (JPG, PNG), and hand-drawn form photographs.

>[!VIDEO](https://video.tv.adobe.com/v/3474042)

**Prompt examples:**

* *Convert the attached PDF file to an adaptive form*
* *Transform this scanned form image into an interactive digital form*
* *Import the employee onboarding PDF and create an editable form*
* *Convert this paper form photograph into a digital form with validation*
-->

<!-- 
### Embed an existing form to a sites page {#embed-existing-form}

The form creation skill enables seamless integration of existing forms into any sites page through natural language commands. Rather than manually locating, copying, and embedding form components, users can simply specify which form to add and where to place it. The agent handles the technical implementation, ensuring proper rendering and functionality.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Embed the contact form to the homepage*
* *Add the existing customer feedback form to the support page*
* *Insert the newsletter signup form into the footer section*
* *Place the registration form on /content/site/signup*
* *Add form "contact-us-2024" to the current page*
-->

<!-- 
### Build and add a form to an existing sites page {#build-and-add-form}

The form creation skill combines form creation and site integration in a single conversational workflow. Users can describe the form they need and specify where to add it, and the agent creates the form and embeds it into the specified page automatically. This eliminates the traditional multi-step process of creating a form separately and then manually adding it to a page.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Create a newsletter signup form with email field and add it to the footer*
* *Build a quick contact form with name, email, and message, then add it to /content/about-us*
* *Add a feedback form with rating stars and comment field to this page*
* *Create a simple survey form with 5 questions and embed it on the customer portal homepage*
* *Build an event registration form with name, email, and date selection, then add it to /content/events/conference-2025*
-->
