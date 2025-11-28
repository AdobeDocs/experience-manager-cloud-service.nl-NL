---
title: Vaardigheid voor bijwerken van inhoud
description: Leer wat de inhoud van de Agent van de Productie van de Ervaring bijwerkt vaardigheid is en wat het voor u kan doen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 437da39f61d7af2fe01a1617d3299fd60ee38ad5
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 0%

---


# Vaardigheid voor bijwerken van inhoud {#content-update}

De content update-vaardigheid van de Experience Production Agent automatiseert de content productie om dagelijkse taken voor Adobe Experience Manager (AEM) as a Cloud Service en Edge Delivery Services te versnellen.

De inhoud werkt bestaande inhoud bij, inclusief inhoudsfragmenten, pagina&#39;s, formulieren en elementen. De agent kan acties uitvoeren zoals het bijwerken, verwijderen, vervangen of toevoegen van inhoudselementen om ervaringen nauwkeurig en actueel te houden. Invoer kan een natuurlijke taalbeschrijving zijn en bij Jira PDF&#39;s en screenshots kan ook invoer worden geleverd.

## Overzicht {#overview}

De inhoud werkt de vaardigheden bij die u, of door natuurlijke taal of visuals, in inhoudsupdates op uw pagina verstrekt. U verstrekt URL van een pagina die moet bijwerken, samen met details van wat bijwerken vereist, en de agentenvaardigheid voltooit uw taak.

## Mogelijkheden {#capabilities}

U hebt toegang tot de vaardigheden voor het bijwerken van inhoud via:

* [AI-assistent](#ai-assistant)

* [Jira](#jira)

## AI-assistent {#ai-assistant}

Via de AI-assistent hebt u toegang tot de agents in AEM.

Open de AI Assistant vanaf experience.adobe.com en begin met interactie door uw vraag in natuurlijke taal op te geven met behulp van het veld `Ask AI Assistant anything` :

![ de Agent van de Ontdekking van de Toegang ](/help/ai-in-aem/agents/production/assets/content-update-ai-assistant-example.png)

### Voorbeeldvragen {#sample-prompts}

Om inhoudsupdates in werking te stellen kunt u een brede waaier van natuurlijke taalherinneringen geven. U moet ook de openbare URL opgeven van de pagina die u wilt bijwerken. Bijvoorbeeld:

* Wijzig de volgende pagina https://www.your-url.com/sale De hoofdhoofdhoofdhoofdkop bijwerken naar &quot;Black Vrijdag Mega Sale Sale - Tot 70% korting&quot;, wijzig de afteltimer om &quot;Eindigt binnen 48 uur&quot; te tonen, Verwijdert &quot;Aanmelden voor updates&quot;, wijzig alle knoppen &quot;Nu winkelen&quot; in &quot;De deal regelen&quot;

* https://www.your-url.com/laptops/your-laptop-model De bannerkopie van de update naar "Bespaar vandaag slechts 300 USD", werk de prijzen van 1.299 USD aan 999 USD bij, verwijder de banner van de financieringsoptie

* https://www.your-url.com/your-sneaker Werk de voorraadstatus bij van "Low Stock" in "Back in Stock - Limited Quantities", wijzig de formaatkiezer om de beschikbare formaten in groen te markeren. Verwijder het logo "Komende binnenkort"

* https://www.your-url.com/your-sneaker Werk de productafbeeldingen bij om nieuwe kleuren weer te geven

>[!NOTE]
>
>Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan gebruikend [ Jira ](#jira), maar wordt niet gesteund met AI Medewerker.

## Jira {#jira}

Met de vaardigheid van de inhoudsupdate in Jira kunt u een ticket maken met instructies waarmee uw bewerkingen worden geautomatiseerd.

### Een ticket maken {#create-a-ticket}

Maak een Jira-ticket (van elk type).

Er zijn twee essentiële details nodig op het **gebied van de Beschrijving** van uw kaartje:

1. De openbare URL van de pagina die u moet bewerken.

1. De benodigde wijzigingen.

   Momenteel steunt de vaardigheid de volgende waaier van formaten om uw veranderingen te beschrijven:

   * Natuurlijke taal in de beschrijving van het ticket
      * bijvoorbeeld &quot;De kopregel wijzigen van X in Y&quot;
   * PDF met annotatie gekoppeld
      * Maak bijvoorbeeld een PDF van uw pagina en voeg annotaties toe waarin staat wat u wilt wijzigen
   * Opmerkingen in bijgevoegde PDF
      * Maak bijvoorbeeld een PDF van uw pagina en voeg opmerkingen toe waarin u opgeeft wat u wilt wijzigen
   * Bijgevoegde schermafbeelding gekoppeld
      * Neem bijvoorbeeld een schermafbeelding van een deel van de pagina en voeg annotaties toe waarin staat wat u wilt wijzigen
   * Microsoft Word-bestand bijgevoegd, met wijzigingen in de natuurlijke taal

### Roep de agent aan vanaf uw ticket {#invoke-the-agent-from-your-ticket}

Om de agent te gebruiken, voeg een commentaar aan uw kaartje toe. In de opmerking vermeldt u de agent met het symbool `@` en de opdracht die het moet uitvoeren, bijvoorbeeld:

* `@aemagent@adobe.com process`

Momenteel, begrijpt de agent de bevelen:

* `process` - de aanvraag verwerken
* `cancel` - een verwerkingsverzoek annuleren
* `retry` - een aanvraag opnieuw verwerken
* `feedback` - feedback toepassen op een vorige generatie
* `reprocess` - de oorspronkelijke aanvraag opnieuw verwerken

### Hoe de agent in wisselwerking staat {#how-the-agent-interacts}

Nadat u een bevel aan de agent uitgeeft, antwoordt het met commentaren in Jira. De opmerkingen geven de voortgang van de agent in detail aan en de acties die zijn uitgevoerd.

Als de opdracht `process` updates activeert, volgen de reacties mogelijk de volgende volgorde:

* De eerste opmerking bevestigt dat de agent is gestart.

* Zodra de taak wordt voltooid. de agent reageert met een andere opmerking die details bevat van de ondernomen acties.
   * De inhoudsupdates die door de agent worden gemaakt zijn niet-destructief - dit betekent dat zij aan een voorproefinstantie worden gemaakt.
   * De opmerking bevat koppelingen naar de updates, zodat u deze kunt reviseren en publiceren of de Jira kunt toewijzen aan de verantwoordelijke persoon.

* Het volgende beeld toont een voorbeeldJira die het `process` bevel voor de vaardigheid van de inhoudsupdate teweegbrengt:

  ![ Jira van het Voorbeeld gebruikend de vaardigheid van de inhoudsupdate van de Agent van de Productie van de Ervaring ](assets/content-update-jira-example.png)

## Activering {#activation}

Als u de Experience Production Agent wilt activeren en gebruiken, moet u contact opnemen met Adobe. U kunt contact opnemen met:

* `experience-production-agent@adobe.com`
* of neem contact op met uw accountteam

Om het proces te versnellen helpt het om de volgende informatie te verstrekken:

* Voor AEM as a Cloud Service
   * U moet uw volgende gegevens opgeven:
      * Organisatie-id
      * `product_id`
      * `profile_id`

   * Deze waarden kunt u vinden in de volgende stappen:
      * Uw beheerder moet naar <https://adminconsole.adobe.com/> gaan
      * Selecteer **Adobe Experience Manager as a Cloud Service**
      * Selecteer de juiste AEM-instantie
      * Selecteer het profiel dat lees- en schrijfbewerkingen toestaat voor de desbetreffende inhoud
      * De URL van de browser ophalen
      * Extraheer `product_id` en `profile_id` uit de URL.
Bijvoorbeeld: <https://adminconsole.adobe.com/products/profiles/users>

* Authoring in Edge Delivery-documenten
   * Geef uw Adobe-team de volgende informatie:
      * Relevante domeinen
      * Relevante Github-informatie:
         * Org
         * Repo
         * Branch

## Beperkingen {#limitations}

De beperkingen voor de Content Updater zijn momenteel:

* Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan met [ Jira ](#jira), maar wordt niet gesteund wanneer het in wisselwerking staan met de [ Medewerker AI ](#ai-assistant).
