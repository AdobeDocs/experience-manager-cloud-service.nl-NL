---
title: Taak voor bijwerken van inhoud
description: Leer wat de de inhoudsupdate van de Agent van de Merk is en wat het voor u kan doen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 36f4ba8207da67b8e68c9c9851311defc909b495
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# Taak voor bijwerken van inhoud {#content-update}

De baan van de inhoudsupdate van de [&#x200B; Agent van de Ervaring van het Merk &#x200B;](/help/ai-in-aem/agents/brand-experience/overview.md) automatiseert inhoudsproductie om dagelijkse taken voor Adobe Experience Manager (AEM) as a Cloud Service en Edge Delivery Services te versnellen.

## Overzicht {#overview}

De inhoudsupdate-taak werkt bestaande inhoud bij, inclusief inhoudsfragmenten, pagina&#39;s, formulieren en elementen. De taak kan handelingen uitvoeren zoals het bijwerken, verwijderen, vervangen of toevoegen van inhoudselementen om ervaringen nauwkeurig en actueel te houden. Invoer kan een natuurlijke taalbeschrijving zijn en bij Jira PDF&#39;s en screenshots kan ook invoer worden geleverd.

De functie voor het bijwerken van de inhoud verandert de gegevens die u opgeeft, in de natuurlijke taal of de visuele weergave, in de inhoud van de pagina-updates. U verstrekt URL van een pagina die moet bijwerken, samen met details van wat bijwerken vereist, en de agentenvaardigheid voltooit uw taak. Wanneer gebruikt met Adobe Experience Manager (AEM) as a Cloud Service, leidt de baan tot een nieuwe [&#x200B; lancering &#x200B;](/help/sites-cloud/authoring/launches/overview.md) zodat kunt u de updates herzien alvorens toe te passen. Wanneer gebruikt met het auteursrecht van het Document, leidt de baan tot een nieuwe [&#x200B; versie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#).

## Mogelijkheden {#capabilities}

U hebt toegang tot de vaardigheden voor het bijwerken van inhoud via:

* [De AI-assistent](#ai-assistant)
* [Jira](#jira)

## AI-assistent {#ai-assistant}

U kunt de taak in AEM openen via de AI-assistent.

Open de AI-assistent vanuit [`experience.adobe.com` &#x200B;](https://experience.adobe.com) en begin vervolgens met interactie door de vraag in de natuurlijke taal op te geven met behulp van het veld `Ask AI Assistant anything` :

![&#x200B; Baan van de Update van de Inhoud &#x200B;](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### De publicatie-URL configureren {#configuring-the-publish-url}

Voor het gebruik van een publicatie-URL (public Onder ogen zien) moet een eenmalige configuratie worden uitgevoerd:

* Vereisten:

   * Om de configuratie te kunnen maken, moet de gebruiker over System Admin of Product Admin-rechten beschikken.

* Configuratie:

   1. Roep de vaardigheid van de Update van de Inhoud aan door een inhoudsupdate voor URL te verzoeken.
   1. De medewerker zal u door de configuratie, door u een aantal vragen te stellen lopen.
   1. Nadat de publicatie-URL is voltooid, is deze geconfigureerd en kan deze worden gebruikt.

Bijvoorbeeld:

![&#x200B; de vaardigheid van de Update van de Inhoud - vorm publiceer URL &#x200B;](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### Vragen {#prompts}

Om inhoudsupdates in werking te stellen kunt u een brede waaier van natuurlijke taalherinneringen geven. U moet het openbare onder ogen ziende (publiceren) URL, of auteur milieu URL, van de pagina specificeren u wilt bijwerken. Sommige, maar niet alle, werkwoorden die worden ondersteund; vervangen, bijwerken, verwijderen, wijzigen, herzien, aanpassen, verwijderen.

>[!NOTE]
>
>Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan gebruikend [&#x200B; Jira &#x200B;](#jira), maar wordt niet gesteund met AI Medewerker.

### Voorbeeldvragen {#sample-prompts}

Voorbeelden hiervan zijn:

* op `<your-publish-URL>` update &quot;Uw perfecte koffie is vier vragen verderop!&quot; tot &quot;Uw koffie, jouw weg!&quot;
* op `<your-author-env-URL>` vervangt u de afbeelding van &quot;holdingcup.png&quot; in &quot;stairhead.png&quot;
* on `<your-publish-URL>` change &quot;Take our Coffee Quiz&quot; button to a boeiender version&quot;
* op `<your-author-env-URL>` de sectie &quot;Rewards unclaimis a Cadeautje gemist!&quot; te verwijderen

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

Als u de taak wilt gebruiken, voegt u een opmerking toe aan uw ticket. Vermeld in de opmerking de taak met het symbool `@` , samen met de instructies.

Bijvoorbeeld:

* `@aemagent@adobe.com process this ticket`

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

U kunt de Agenten van AEM door [&#x200B; Playground &#x200B;](https://www.aem.live/developer/aem-playground) onderzoeken, of met uw CSM of TAM verbinden om toegang via Agentic SKU te bespreken.

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Het dossier uploadt kan worden gebruikt wanneer het in wisselwerking staan met [&#x200B; Jira &#x200B;](#jira), maar wordt niet gesteund wanneer het in wisselwerking staan met de [&#x200B; AI Medewerker.](#ai-assistant)
