---
title: Formulierontwerpvaardigheden
description: Leer meer over de vaardigheden van de Experience Production Agent bij het maken van formulieren en hoe u natuurlijke taal kunt gebruiken om nieuwe formulieren te maken.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: aa8369979c99535f0fd77e6a51af10cc17afd971
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---


# Vaardigheid voor maken van formulier {#form-creation-skill}

De vaardigheid van de vormverwezenlijking is een vermogen van de Agent van de Productie van de Ervaring die wordt ontworpen om vormen te ontwikkelen gebruikend natuurlijke taalherinneringen. Deze vaardigheid produceert automatisch aangewezen vormstructuur en gebiedstypes. De vaardigheid wordt gesurft door AI Medewerker.

Enkele belangrijke voordelen van het ontwerpen van formulieren zijn:

* **versnelde vormontwikkeling**: Creeer snel vormen gebruikend
eenvoudige natuurlijke taalbevelen, die de behoefte elimineren om traditionele productinterfaces te leren.
* **Consistente en op-brand ervaringen**: Creeer vormen die branding van uw organisatie, malplaatjes, en stijlrichtlijnen door goedgekeurde malplaatjes en stijlen te gebruiken volgen.
* **Lagere technische barrière**: Staat bedrijfsgebruikers toe om vormen gemakkelijk tot stand te brengen, zonder het vereisen van geavanceerde technische of diepe productdeskundigheid.

## Mogelijkheden {#capabilitiess}

* **creeer een nieuwe vorm met duidelijke tekstherinnering**: U kunt een vorm tot stand brengen door uw vereisten in gewone taal voor te leggen. De agent genereert automatisch de juiste formulierstructuur, veldtypen en ervaringen van het merk op basis van uw natuurlijke taalbeschrijving en opgegeven sjabloon. Deze mogelijkheid versnelt het maken van formulieren en zorgt ervoor dat de standaarden voor merk en naleving worden gehandhaafd.

* **de Invoer een document van PDF en zet het in vorm** om: U kunt bestaande documenten van PDF in vormen invoeren en omzetten. De agent analyseert geüploade inhoud om veldtypen te detecteren, lay-outs te behouden en formulieren te verbeteren met responsieve ontwerp- en validatielogica en er tegelijkertijd voor te zorgen dat de standaarden voor merk en compatibiliteit worden gehandhaafd.

  Wanneer u een van de bovenstaande mogelijkheden gebruikt, wordt u gevraagd het type formulier te kiezen dat u wilt maken, een sjabloon voor op kerncomponenten gebaseerde adaptieve formulieren of een sjabloon voor op Edge Delivery Services gebaseerde adaptieve formulieren op te geven en het voorkeurspad voor het opslaan van het formulier aan te geven. Als u een formulier maakt dat is gebaseerd op Edge Delivery Services, kunt u ook de GitHub-URL van de gegevensopslagruimte opgeven.


### Voorbeeldaanwijzingen {#sample-prompts}

* *creeer een vorm voor terugkoppel inzameling met naam, e-mail, en berichtgebieden*
* *creeer een klant terugkoppelt vorm met productclassificatie (1-5 sterren), commentaargebied, en facultatieve e-mail*
* *bouwt een contactvorm met naam, e-mail, onderwerpdrop, en berichtgebieden*
* *creeer een registratieformulier met persoonlijke informatie, rekeningsvoorkeur, en termen aanvaarding*
* *creeer een vorm van de creditcardtoepassing door het dossier van PDF beschikbaar in &quot;https://[ te importeren aem-auteur-url ]/path/to/pdf/file*
* *creeer een terugkoppel vorm gebruikend boilerplate bij &quot;<https://github.com/wkndforms/wesecure> &quot;*

## Uw formulier verfijnen {#refine-with-forms-experience-builder}

Nadat u de initiële formulierstructuur hebt gemaakt met AI Assistant, kunt u de Forms Experience Builder gebruiken om:

* **vormen van de Update**: Voeg of wijzig gebieden toe, pas gebiedstypes aan, en werk het stileren zoals nodig door de visuele redacteur bij.

* **Lay-out van de Update**: Herschik secties, groepen, of gebieden, pas het uit elkaar plaatsen aan, en wijzig de visuele hiërarchie om bruikbaarheid te verbeteren en uw vorm duidelijk en intuïtief voor uw publiek te verzekeren.

* **voegt bedrijfslogica** toe: Creeer voorwaardelijke logica, toon/verberg regels, gebiedsdelen, en bepaal bevestigingsregels.

* **vorm voorlegging**: Vorm waar de vormgegevens, met inbegrip van vestiging e-mailberichten, integratie met werkschema&#39;s, of verbindingen aan externe systemen worden voorgelegd.

Voor meer informatie, zie {de documentatie van de Bouwer van de Ervaring van 0} Forms [.](/help/forms/experience-builder/product-overview.md)


## Activering {#activation}

Als u de Experience Production Agent voor uw organisatie wilt inschakelen, moet de activering worden gestart via Adobe. Begin het proces door uit te reiken via:

* E-mail: `experience-production-agent@adobe.com`
* Of neem contact op met het aangewezen Adobe-accountteam.

Voor een efficiënte ervaring bij het instappen moet u de volgende gegevens opstellen en verstrekken:

Voor **AEM as a Cloud Service**, deel de volgende herkenningstekens:

* Organisatie-id
* `product_id`
* `profile_id`

Uw AEM-beheerder kan deze vinden door:

1. Navigeren naar <https://adminconsole.adobe.com/>
1. Selecterend **Adobe Experience Manager as a Cloud Service**
1. De juiste AEM-instantie in uw omgeving kiezen
1. Een profiel selecteren met lees-/schrijfmachtigingen voor relevante inhoud
1. De volledige URL van de browser van deze pagina kopiëren
1. De waarden `product_id` en `profile_id` extraheren van de URL\
   (Een URL zoals `https://adminconsole.adobe.com/products/profiles/users` bevat bijvoorbeeld deze parameters).

Voor **het Authoring van het Document van Edge Delivery**, leverde uw team van Adobe van:

* Domeinen voor uw Edge Delivery Services-omgeving
* Overeenkomende GitHub-gegevens:
   * Organisatie (organisatie)
   * Repository (Repo)
   * Branch

Het verstrekken van volledige en nauwkeurige informatie versnelt het activeringsproces en verzekert tijdige levering van de Agent van de Productie van de Ervaring.

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
