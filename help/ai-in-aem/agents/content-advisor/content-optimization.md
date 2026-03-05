---
title: Content Optimization Agent
description: Leer hoe u de agent voor het optimaliseren van inhoud kunt gebruiken om te transformeren hoe gebruikers elementen verfijnen en aanpassen door instructies in de natuurlijke taal toe te passen om voor kanalen geschikte variaties te maken.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 896fc25b-7f60-47b8-9264-2ef6b85d954c
source-git-commit: a9f1ed92e3ca05be6f4db578a814330004100b3e
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Content Optimization Agent {#content-optimization-agent}

Als deel van [ de Agent van de Adviseur van de Inhoud van AEM ](/help/ai-in-aem/agents/content-advisor/overview.md) de agent van de inhoudoptimalisering transformeert hoe de gebruikers en activa aanpassen door natuurlijke taalinstructies toe te passen om kanaal-klaar variaties tot stand te brengen. Of het produceren van nieuwe vertoningen, het aanpassen van visuele eigenschappen, het veranderen van achtergronden, of het voorbereiden van activa voor specifieke digitale kanalen, de agent interpreteert gebruikersintent en voert complexe het uitgeven taken automatisch uit. Het werkt naadloos met [ de agent van de inhoudsontdekking, ](/help/ai-in-aem/agents/content-advisor/discovery.md) die de activa neemt en geoptimaliseerde variaties gebruikend kern [ Dynamische Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) produceert die merk, kanaal, en campagnevereisten zonder handontwerpinspanning ontmoeten.

Enkele belangrijke voordelen van de agent voor het optimaliseren van inhoud zijn:

* **de krachtige activatransformatie van 0}: Zet eenvoudige, conversationele herinneringen in nauwkeurige beeldverrichtingen, zoals het resizing, het scherpen, het weerspiegelen, of het opnieuw kleuren om, die de behoefte aan gespecialiseerde het uitgeven hulpmiddelen elimineren.**

* **kanaal-geoptimaliseerde output**: produceert snel vertoningen die voor specifieke platforms zoals de Artikelen van het Installagram, Webbanners, of andere marketing touchpoints worden gemaakt, die activa voor onmiddellijk gebruik klaar verzekeren.

* **de verhoging van Creative bij schaal**: Past visuele aanpassingen en verhogingen, zoals achtergrondveranderingen of grafische overlays toe, om hoog-volume creatieve werkschema&#39;s te steunen zonder teams neer te vertragen.

* **[Naadloze samenwerking met de agent van de inhoudsontdekking](/help/ai-in-aem/agents/content-advisor/discovery.md)**: Bouwt op de activa voort die door de agent van de inhoudsontdekking worden geïdentificeerd, toelatend activa van begin tot eind terugwinning en optimalisering door natuurlijk gesprek.

>[!IMPORTANT]
>
>Door AI gegenereerde reacties kunnen onjuist of misleidend zijn. Controleer de voorgestelde oplossingen en reacties met twee controles.
>
>Zie ook [ Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

>[!VIDEO](https://video.tv.adobe.com/v/3480078)

## Vereisten {#prerequisites-content-optimization-agent}

Variaties of optimalisaties genereren voor afbeeldingselementen. U moet:

* Een geldige licentie voor dynamische media

* Dynamic Media met OpenAPI ingeschakeld in een AEM as a Cloud Service-omgeving.

* De activa in [ erkende staat ](/help/assets/manage-organize-assets-view.md#manage-asset-status) in uw milieu van AEM as a Cloud Service.

## Vaardigheden {#skills-content-optimization-agent}

De agent voor het optimaliseren van inhoud biedt de volgende vaardigheden:

* **Begrijp intent door natuurlijke taal**

  De agent voor het optimaliseren van inhoud interpreteert de gebruikersintentie op basis van vragen in de natuurlijke taal, waarbij rekening wordt gehouden met kanaal-, campagne- en publiekcontext om de meest relevante optimaliseringsacties te bepalen.

* **produceert dynamische inhoudvarianten**

  De agent voor het optimaliseren van de inhoud maakt geoptimaliseerde varianten als dynamische URL&#39;s die op maat zijn gemaakt voor verschillende kanalen en opmaaktypen.

* **optimaliseert beeldinhoud**

  De agent voor het optimaliseren van inhoud past verbeteringen toe, zoals het omzetten van indelingen, het aanpassen van de resolutie, bijsnijden en verscherpen om de afbeeldingskwaliteit te verbeteren.

* **multi-variant activa optimalisering**

  De agent voor het optimaliseren van inhoud kan meerdere geoptimaliseerde afbeeldingsvariaties genereren op basis van de elementen die door de content discovery agent worden geretourneerd. Hierbij wordt één natuurlijke-taalprompt weergegeven, zodat gebruikers snel en efficiënt uitvoeringen kunnen maken die geschikt zijn voor kanalen.

## Personas {#personas-content-optimization-agent}

Kanaalmarketers, de belangrijkste persona voor de agent voor het optimaliseren van inhoud, kunnen de juiste broninhoud met hoge resolutie selecteren en geoptimaliseerde indelingen aanvragen die zijn afgestemd op hun kanalen en publiekssegmenten.

De regionale marketers en de uitzendkrachten kunnen de agent van de inhoudoptimalisering ook gebruiken om kanaalklaar beeldvariaties snel te produceren die snellere, consistentere inhoudsproductie steunen.

## Toegang verkrijgen {#access-content-optimization-agent}

U kunt de agent voor het optimaliseren van inhoud in AEM openen via de AI Assistant. Meld u aan bij [`experience.adobe.com` ](https://experience.adobe.com) en u kunt beginnen met interactie met AI Assistant door de vraag in de natuurlijke taal op te geven met behulp van het veld `Ask AI Assistant anything` :

![ de agent van de inhoudoptimalisering van de Toegang ](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

## Gebruiksscenario&#39;s en Voorbeeldvragen {#use-cases-prompts}

Gebruik de agent van de inhoudoptimalisering door naar de juiste activa door de [ agent van de inhoudsontdekking te zoeken.](/help/ai-in-aem/agents/content-advisor/discovery.md) Wanneer de relevante afbeeldingen zijn weergegeven, kunnen gebruikers rechtstreeks uit de zoekresultaten geoptimaliseerde of kanaalspecifieke varianten voor een of meerdere elementen genereren. Deze workflow garandeert input van hoge kwaliteit en consistent betere optimalisatieresultaten. [ zie de volledige lijst van beschikbare optimalisaties ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) voor meer informatie.

* **de verwezenlijking van de vertoning van de hoge resolutie**

  De agent kan nieuwe uitvoeringen van een element op een opgegeven resolutie- en kwaliteitsniveau genereren, waardoor het eenvoudig is om kanaalklare variaties voor te bereiden zonder handmatig te bewerken.


  Voorbeeldprompt:

  Maak een `2000px` -uitvoering als `JPEG` met `80%` -kwaliteit.

  Onderzoek naar het juiste middel gebruikend de [ agent van de inhoudsontdekking ](/help/ai-in-aem/agents/content-advisor/discovery.md) en gebruik dan de volgende herinneringen in het geval van veelvoudige onderzoeksresultaten:

  Voor het derde zoekresultaat maakt u een `2000px` vertoning `JPEG` met `80%` kwaliteit.

  OF

  Voor `Asset ID` genereert u een uitvoering van 2000 px als `JPEG` met `80%` kwaliteit

* **verbetering van het Beeld**

  De agent kan visuele verbeteringen toepassen—zoals verscherpen—om ervoor te zorgen dat de elementen er scherp en goed gedefinieerd uitzien voordat deze over campagnes worden gebruikt.

  Voorbeeldprompt:

  Verscherp de afbeelding.


* **de aanpassingen van de Achtergrondkleur**

  De agent kan achtergrondkleuren in transparante elementen bijwerken of vervangen, waarbij hij ondersteuning biedt voor merkspecifieke kleurschema&#39;s of door campagne gestuurde visuele thema&#39;s.

  Voorbeeldprompt:

  Wijzig de achtergrondkleur van de `PNG` in `#ff8932` .

* **de transformaties van de Richtlijn**

  De agent kan visuele elementen spiegelen of spiegelen om deze uit te lijnen op de behoeften van de layout of op creatieve wijze, zonder dat externe bewerkingsgereedschappen nodig zijn.

  Voorbeeldprompt:

  De afbeelding horizontaal spiegelen.

* **kanaal-geoptimaliseerde vertoningen**

  De agent kan vertoningen produceren die aan platform-specifieke vereisten-zoals de Artikelen van het Installagram worden aangepast-verzekert de activa formaat, de verhouding, en kwaliteitsrichtlijnen automatisch ontmoeten.

  Voorbeeldvraag:

  Maak een vertoning voor een `Instagram` -artikel.

* **Gemarkeerde overlays en samengestelde generatie**

  De agent kan promotionele afbeeldingen, bedekkingen of badges op bestaande middelen toepassen met nauwkeurige plaatsing, waardoor het snel maken van composities voor campagnes wordt ondersteund.

  Voorbeeldvraag:

  Bedek de afbeelding met `30%` korting op afbeeldingen boven de promotiebanner en plaats deze `100px` vanuit het middelpunt.

  >[!NOTE]
  >
  >Overlayposities zijn mogelijk niet correct.


## Optimalisatieresultaten {#content-optimization-agent-results}

Wanneer u een optimalisatieverzoek opgeeft, retourneert de agent voor het optimaliseren van de inhoud het verbeterde element, samen met handige toegangsopties op basis van het type element:

* **Beelden**: De reactie omvat een duimnagelvoorproef en opties om Dynamische Media URL te openen of het geoptimaliseerde beeld te downloaden.

* **de documenten van PDF**: De reactie omvat een duimnagelvoorproef en opties om Dynamische Media URL te openen of het geoptimaliseerde dossier te downloaden.

* **Video&#39;s**: De reactie verstrekt opties om Dynamische Media URL te openen of de geoptimaliseerde video te downloaden.

![ de resultaten van de Optimalisering van de Inhoud ](/help/ai-in-aem/agents/content-advisor/assets/download-content-optimization.png)

Deze resultaten maken het gemakkelijk om de geoptimaliseerde output te herzien en onmiddellijk het over stroomafwaartse kanalen of werkschema&#39;s te gebruiken.


## Beperkingen {#limitations-content-optimization}

* Het instellen van de achtergrondkleur wordt niet ondersteund.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-agent}

The following are some prompting best practices:

* Be explicit about the enhancement you want the content optimization agent to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
