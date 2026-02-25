---
title: Taak voor optimalisatie van inhoud
description: Leer hoe u de functie voor het optimaliseren van inhoud kunt gebruiken om te transformeren hoe gebruikers elementen verfijnen en aanpassen door instructies in de natuurlijke taal toe te passen om voor kanalen geschikte variaties te maken.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 896fc25b-7f60-47b8-9264-2ef6b85d954c
source-git-commit: a31cd8ea0ae02a51efb748097c195d68dc8b554d
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# Taak voor optimalisatie van inhoud {#content-optimization-job}

Als deel van [&#x200B; de Agent van de Adviseur van de Inhoud van AEM &#x200B;](/help/ai-in-aem/agents/content-advisor/overview.md) zet de baan van de inhoudoptimalisering om hoe de gebruikers verfijnen en activa aanpassen door natuurlijke taalinstructies toe te passen om kanaal-klaar variaties tot stand te brengen. Of u nu nieuwe uitvoeringen genereert, visuele eigenschappen aanpast, achtergronden wijzigt of elementen voorbereidt voor specifieke digitale kanalen, de taak interpreteert de intentie van de gebruiker en voert automatisch complexe bewerkingstaken uit. Het werkt naadloos met [&#x200B; de baan van de inhoudsontdekking, &#x200B;](/help/ai-in-aem/agents/content-advisor/discovery.md) die de activa neemt het vindt en geoptimaliseerde variaties produceert gebruikend kern [&#x200B; Dynamische Media met mogelijkheden OpenAPI &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) die merk, kanaal, en campagnevereisten zonder handontwerpinspanning ontmoeten.

Enkele belangrijke voordelen van de functie voor het optimaliseren van inhoud zijn:

* **de krachtige activatransformatie van 0&rbrace;: Zet eenvoudige, conversationele herinneringen in nauwkeurige beeldverrichtingen, zoals het resizing, het scherpen, het weerspiegelen, of het opnieuw kleuren om, die de behoefte aan gespecialiseerde het uitgeven hulpmiddelen elimineren.**

* **kanaal-geoptimaliseerde output**: produceert snel vertoningen die voor specifieke platforms zoals de Artikelen van het Installagram, Webbanners, of andere marketing touchpoints worden gemaakt, die activa voor onmiddellijk gebruik klaar verzekeren.

* **de verhoging van Creative bij schaal**: Past visuele aanpassingen en verhogingen, zoals achtergrondveranderingen of grafische overlays toe, om hoog-volume creatieve werkschema&#39;s te steunen zonder teams neer te vertragen.

* **[Naadloze samenwerking met de baan van de inhoudsontdekking](/help/ai-in-aem/agents/content-advisor/discovery.md)**: Bouw op de activa die door de baan van de inhoudsontdekking worden geïdentificeerd, toelatend activa van begin tot eind herwinning en optimalisering door natuurlijk gesprek.

>[!IMPORTANT]
>
>Door AI gegenereerde reacties kunnen onjuist of misleidend zijn. Controleer de voorgestelde oplossingen en reacties met twee controles.
>
>Zie ook [&#x200B; Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

>[!VIDEO](https://video.tv.adobe.com/v/3480078)

## Vereisten {#prerequisites-content-optimization-job}

Variaties of optimalisaties genereren voor afbeeldingselementen. U moet:

* Een geldige licentie voor dynamische media

* Dynamic Media met OpenAPI ingeschakeld in een AEM as a Cloud Service-omgeving.

* De activa in [&#x200B; erkende staat &#x200B;](/help/assets/manage-organize-assets-view.md#manage-asset-status) in uw milieu van AEM as a Cloud Service.

## Vaardigheden {#skills-content-optimization-job}

De functie voor het optimaliseren van inhoud biedt de volgende vaardigheden:

* **Begrijp intent door natuurlijke taal**

  De functie voor het optimaliseren van inhoud interpreteert de gebruikersinzet op basis van vragen in de natuurlijke taal, waarbij rekening wordt gehouden met kanaal-, campagne- en publiekcontext om de meest relevante optimaliseringsacties te bepalen.

* **produceert dynamische inhoudvarianten**

  De functie voor het optimaliseren van inhoud maakt geoptimaliseerde varianten als dynamische URL&#39;s die op maat zijn gemaakt voor verschillende kanalen en opmaaktypen.

* **optimaliseert beeldinhoud**

  De functie voor het optimaliseren van inhoud past verbeteringen toe, zoals het omzetten van indelingen, het aanpassen van de resolutie, bijsnijden en verscherpen om de afbeeldingskwaliteit te verbeteren.

* **multi-variant activa optimalisering**

  De functie voor het optimaliseren van inhoud kan meerdere geoptimaliseerde afbeeldingsvariaties genereren op basis van de elementen die door de functie voor het detecteren van inhoud worden geretourneerd. Hierbij wordt één natuurlijke-taalprompt weergegeven, zodat gebruikers snel en efficiënt uitvoeringen kunnen maken die geschikt zijn voor kanalen.

## Personas {#personas-content-optimization-job}

Kanaalmarketers, de belangrijkste persoon voor de optimalisatietaak voor inhoud, kunnen de juiste broninhoud met hoge resolutie selecteren en geoptimaliseerde indelingen aanvragen die zijn afgestemd op hun kanalen en publiekssegmenten.

Regionale marketeers en uitzendkrachten kunnen ook de functie voor het optimaliseren van inhoud gebruiken om snel afbeeldingsvariaties te genereren die geschikt zijn voor kanalen en die een snellere en consistentere productie van inhoud ondersteunen.

## Toegang verkrijgen {#access-content-optimization-job}

U hebt toegang tot de functie voor het optimaliseren van inhoud in AEM via de AI Assistant. Meld u aan bij [`experience.adobe.com` &#x200B;](https://experience.adobe.com) en u kunt beginnen met interactie met AI Assistant door de vraag in de natuurlijke taal op te geven met behulp van het veld `Ask AI Assistant anything` :

![&#x200B; de baan van de inhoudoptimalisering van de Toegang &#x200B;](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

## Gebruiksscenario&#39;s en Voorbeeldvragen {#use-cases-prompts}

Gebruik de baan van de inhoudoptimalisering door naar de juiste activa door de [&#x200B; baan van de inhoudsontdekking te zoeken.](/help/ai-in-aem/agents/content-advisor/discovery.md) Wanneer de relevante afbeeldingen zijn weergegeven, kunnen gebruikers rechtstreeks uit de zoekresultaten geoptimaliseerde of kanaalspecifieke varianten voor een of meerdere elementen genereren. Deze workflow garandeert input van hoge kwaliteit en consistent betere optimalisatieresultaten. [&#x200B; zie de volledige lijst van beschikbare optimalisaties &#x200B;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) voor meer informatie.

* **de verwezenlijking van de vertoning van de hoge resolutie**

  De taak kan nieuwe uitvoeringen van een element op een opgegeven resolutie- en kwaliteitsniveau genereren, waardoor het eenvoudig is om kanaalklare variaties voor te bereiden zonder handmatig te bewerken.


  Voorbeeldprompt:

  Maak een `2000px` -uitvoering als `JPEG` met `80%` -kwaliteit.

  Onderzoek naar het juiste middel gebruikend de [&#x200B; baan van de inhoudsontdekking &#x200B;](/help/ai-in-aem/agents/content-advisor/discovery.md) en gebruik dan de volgende herinneringen in het geval van veelvoudige onderzoeksresultaten:

  Voor het derde zoekresultaat maakt u een `2000px` vertoning `JPEG` met `80%` kwaliteit.

  OF

  Voor `Asset ID` genereert u een uitvoering van 2000 px als `JPEG` met `80%` kwaliteit

* **verbetering van het Beeld**

  De baan kan visuele verbeteringen-zoals het scherpen-toepassen om activa te verzekeren helder en duidelijk gedefiniëerd alvorens over campagnes wordt gebruikt.

  Voorbeeldprompt:

  Verscherp de afbeelding.


* **de aanpassingen van de Achtergrondkleur**

  De taak kan achtergrondkleuren in transparante elementen bijwerken of vervangen, en daarbij merkspecifieke kleurenschema&#39;s of campagnegestuurde visuele thema&#39;s ondersteunen.

  Voorbeeldprompt:

  Wijzig de achtergrondkleur van de `PNG` in `#ff8932` .

* **de transformaties van de Richtlijn**

  De taak kan worden gespiegeld of gespiegeld zodat de weergave is afgestemd op de behoeften van de indeling of op de creatieve richting, zonder dat externe bewerkingsgereedschappen nodig zijn.

  Voorbeeldprompt:

  De afbeelding horizontaal spiegelen.

* **kanaal-geoptimaliseerde vertoningen**

  De baan kan vertoningen veroorzaken die aan platform-specifieke vereisten-zoals de Artikelen van het Installagram worden aangepast-ervoor zorgen de activa formaat, verhouding, en kwaliteitsrichtlijnen automatisch ontmoeten.

  Voorbeeldvraag:

  Maak een vertoning voor een `Instagram` -artikel.

* **Gemarkeerde overlays en samengestelde generatie**

  De baan kan promotionele grafiek, overlays, of badges op bestaande activa met nauwkeurige plaatsing toepassen, die snelle verwezenlijking van campagne-klaar samenstellingen steunt.

  Voorbeeldvraag:

  Bedek de afbeelding met `30%` korting op afbeeldingen boven de promotiebanner en plaats deze `100px` vanuit het middelpunt.

  >[!NOTE]
  >
  >Overlayposities zijn mogelijk niet correct.


## Optimalisatieresultaten {#content-optimization-job-results}

Wanneer u een optimalisatieverzoek opgeeft, retourneert de optimalisatietaak voor inhoud het verbeterde element samen met handige toegangsopties op basis van het type element:

* **Beelden**: De reactie omvat een duimnagelvoorproef en opties om Dynamische Media URL te openen of het geoptimaliseerde beeld te downloaden.

* **de documenten van PDF**: De reactie omvat een duimnagelvoorproef en opties om Dynamische Media URL te openen of het geoptimaliseerde dossier te downloaden.

* **Video&#39;s**: De reactie verstrekt opties om Dynamische Media URL te openen of de geoptimaliseerde video te downloaden.

![&#x200B; de resultaten van de Optimalisering van de Inhoud &#x200B;](/help/ai-in-aem/agents/content-advisor/assets/download-content-optimization.png)

Deze resultaten maken het gemakkelijk om de geoptimaliseerde output te herzien en onmiddellijk het over stroomafwaartse kanalen of werkschema&#39;s te gebruiken.


## Beperkingen {#limitations-content-optimization}

* Het instellen van de achtergrondkleur wordt niet ondersteund.

<!--


## Prompting best Practices {#prompting-best-practices-content-optimization-job}

The following are some prompting best practices:

* Be explicit about the enhancement you want the content optimization job to apply. Clearly state the transformation or adjustment you expect. Precise instructions help the agent produce accurate and predictable results. For example, Instead of `Make it good quality`, specify `Create a JPEG image with 90% quality`.

* Provide detailed parameters whenever possible. The more context you give, such as dimensions, format, quality, placement, or color values, the more tailored the output is.

-->
