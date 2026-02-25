---
title: Taak voor bijwerken van inhoud
description: Leer wat de de inhoudsupdate van de Agent van de Merk is en wat het voor u kan doen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 0%

---


# Taak voor bijwerken van inhoud {#content-update}

De baan van de inhoudsupdate van de [&#x200B; Agent van de Ervaring van het Merk &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) automatiseert inhoudsproductie om dagelijkse taken voor Adobe Experience Manager (AEM) as a Cloud Service en Edge Delivery Services te versnellen.

## Overzicht {#overview}

De inhoudsupdate-taak werkt bestaande inhoud bij, inclusief inhoudsfragmenten, pagina&#39;s, formulieren en elementen. De taak kan handelingen uitvoeren zoals het bijwerken, verwijderen, vervangen of toevoegen van inhoudselementen om ervaringen nauwkeurig en actueel te houden. Invoer kan een natuurlijke taalbeschrijving zijn en bij Jira PDF&#39;s en screenshots kan ook invoer worden geleverd.

De functie voor het bijwerken van de inhoud verandert de gegevens die u opgeeft, in de natuurlijke taal of de visuele weergave, in de inhoud van de pagina-updates. U verstrekt URL van een pagina die moet bijwerken, samen met details van wat bijwerken vereist, en de agentenvaardigheid voltooit uw taak.

## Mogelijkheden {#capabilities}

U hebt toegang tot de vaardigheden voor het bijwerken van inhoud via:

* [De AI-assistent](#ai-assistant)
* [Jira](#jira)

## AI-assistent {#ai-assistant}

U kunt de taak in AEM openen via de AI-assistent.

Open de AI-assistent vanuit [`experience.adobe.com` &#x200B;](https://experience.adobe.com) en begin vervolgens met interactie door de vraag in de natuurlijke taal op te geven met behulp van het veld `Ask AI Assistant anything` :

![&#x200B; Baan van de Update van de Inhoud &#x200B;](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### Voorbeeldvragen {#sample-prompts}

Om inhoudsupdates in werking te stellen kunt u een brede waaier van natuurlijke taalherinneringen geven. U moet ook de openbare URL opgeven van de pagina die u wilt bijwerken. Bijvoorbeeld:

* Wijzig de volgende pagina `https://www.your-url.com/sale` De hoofdhoofdhoofdhoofdhoofdhoofdhoofdkop bijwerken naar &quot;Zwarte Vrijdag - Schaal - tot 70% korting&quot;, wijzig de afteltimer om &quot;Eindigt binnen 48 uur&quot; te tonen, verwijder &quot;Aanmelden voor updates&quot;, wijzig alle knoppen &quot;Nu winkelen&quot; in &quot;De deal regelen&quot;

* `https://www.your-url.com/laptops/your-laptop-model` Update banner copy to &quot;Save 300 USD Today Only&quot;, Update pricing from 1.299 USD to 99 USD, Remove finance option banner

* `https://www.your-url.com/your-sneaker` Werk de voorraadstatus bij van &quot;Low Stock&quot; naar &quot;Back in Stock - Limited Quantities&quot;. Wijzig de formaatkiezer om de beschikbare formaten in groen te markeren. Verwijder de badge &quot;Binnenkort&quot;

* `https://www.your-url.com/your-sneaker` Werk de productafbeeldingen bij om nieuwe kleuren weer te geven

>[!NOTE]
>
>Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan gebruikend [&#x200B; Jira &#x200B;](#jira), maar wordt niet gesteund met AI Medewerker.

## Jira {#jira}

Met de update-taak voor inhoud in Jira kunt u een ticket maken met instructies waarmee uw bewerkingen worden geautomatiseerd.

### Een ticket maken {#create-a-ticket}

Maak een Jira-ticket (van elk type). Er zijn twee essentiële details nodig op het **gebied van de Beschrijving** van uw kaartje:

1. De openbare URL van de pagina die u moet bewerken.

1. De benodigde wijzigingen.

   De baan steunt de volgende waaier van formaten om uw veranderingen te beschrijven:

   * Natuurlijke taal in de beschrijving van het ticket
      * bijvoorbeeld &quot;De kopregel wijzigen van X in Y&quot;
   * PDF met annotatie gekoppeld
      * Maak bijvoorbeeld een PDF van uw pagina en voeg annotaties toe waarin staat wat u wilt wijzigen
   * Opmerkingen in bijgevoegde PDF
      * Maak bijvoorbeeld een PDF van uw pagina en voeg opmerkingen toe waarin u opgeeft wat u wilt wijzigen
   * Bijgevoegde schermafbeelding gekoppeld
      * Neem bijvoorbeeld een schermafbeelding van een deel van de pagina en voeg annotaties toe waarin staat wat u wilt wijzigen
   * Microsoft Word-bestand bijgevoegd, met wijzigingen in de natuurlijke taal

### De taak aanroepen vanaf uw ticket {#invoke-the-job-from-your-ticket}

Als u de taak wilt gebruiken, voegt u een opmerking toe aan uw ticket. In de opmerking wordt de taak vermeld met het symbool `@` en de opdracht die moet worden uitgevoerd, bijvoorbeeld:

* `@aemagent@adobe.com process`

Op dit moment begrijpt de taak de opdrachten:

* `process` - de aanvraag verwerken
* `cancel` - een verwerkingsverzoek annuleren
* `retry` - een aanvraag opnieuw verwerken
* `feedback` - feedback toepassen op een vorige generatie
* `reprocess` - de oorspronkelijke aanvraag opnieuw verwerken

### Hoe de baan interactie heeft {#how-the-agent-interacts}

Nadat u een opdracht aan de taak hebt gegeven, reageert deze met opmerkingen in de jira. In de opmerkingen worden de voortgang van de taak en de ondernomen acties beschreven.

Als de opdracht `process` updates activeert, volgen de reacties mogelijk de volgende volgorde:

* De eerste opmerking bevestigt dat de taak is gestart.

* Zodra de taak is voltooid, reageert de taak met een andere opmerking die details bevat van de ondernomen acties.
   * De inhoud die door de taak wordt bijgewerkt, is niet-destructief. Dit betekent dat ze naar een voorvertoningsinstantie worden gemaakt.
   * De opmerking bevat koppelingen naar de updates, zodat u deze kunt reviseren en publiceren of de Jira kunt toewijzen aan de verantwoordelijke persoon.

* De volgende afbeelding toont een voorbeeld-Jira die het `process` bevel voor de baan van de inhoudsupdate in werking stelt:

  ![&#x200B; Jira van het Voorbeeld gebruikend de baan van de inhoudsupdate van de Agent van de Productie van de Ervaring &#x200B;](assets/content-update-jira-example.png)

## Activering {#activation}

Neem contact op met Adobe als u de communicatietaak wilt activeren en toegang wilt krijgen tot de communicatietaak. Om aan de slag te gaan kunt u:

* Contact `experience-production-agent@adobe.com`
* Of ga naar uw accountteam

Om het proces te versnellen helpt het om de volgende informatie te verstrekken:

* Voor AEM as a Cloud Service moet u het volgende opgeven:
   * Organisatie-id
   * `product_id`
   * `profile_id`

   * U vindt deze waarden als volgt:
      1. Uw beheerder moet [`https://adminconsole.adobe.com` bezoeken &#x200B;](https://adminconsole.adobe.com)
      1. Selecteer **Adobe Experience Manager as a Cloud Service**
      1. Selecteer de juiste AEM-instantie
      1. Selecteer het profiel dat lees- en schrijfbewerkingen toestaat voor de desbetreffende inhoud
      1. De URL van de browser ophalen
      1. Extraheer `product_id` en `profile_id` uit de URL.
Bijvoorbeeld: `https://adminconsole.adobe.com/products/profiles/users`

* Authoring in Edge Delivery-documenten
   * Geef uw Adobe-team de volgende informatie:
      * Relevante domeinen
      * Relevante Github-informatie:
         * Org
         * Repo
         * Branch

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan met [&#x200B; Jira &#x200B;](#jira), maar wordt niet gesteund wanneer het in wisselwerking staan met de [&#x200B; AI Medewerker.](#ai-assistant)
