---
title: Content Discovery Agent
description: Leer hoe u de content discovery agent kunt gebruiken om relevante AEM content op aanvraag te leveren via natuurlijke, conversationele herinneringen voor een gestroomlijnde, klikvrije ontdekkingservaring.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 676300cd-b799-4c53-a58e-043e58a2cbc5
source-git-commit: a9f1ed92e3ca05be6f4db578a814330004100b3e
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 0%

---


# Content Discovery Agent {#discovery-agent}

Als deel van de Agent van de Adviseur van de Inhoud van AEM [, &#x200B;](/help/ai-in-aem/agents/content-advisor/overview.md) de agent van de inhoudsontdekking levert de inhoud van AEM op bestelling door natuurlijke, conversationele herinneringen voor een gestroomlijnde, klik-vrije ontdekkingservaring. In Assets, Content Fragments en Adaptive Forms wordt op intelligente wijze gezocht naar relevante materialen, zoals afbeeldingen, video&#39;s, PDF-documenten, artikelen en formuliersjablonen. Met de natuurlijke taal kunt u naar inhoud zoeken zonder complexe query&#39;s te maken of filters toe te passen in de AEM Assets-interface. Gebaseerd op uw herinnering, keert de agent gekromde resultaten samen met activa meta-gegevens en levering URLs terug, klaar om in andere toepassingen worden ingebed.

Enkele belangrijke voordelen van de Content Discovery Agent zijn:

* **Verenigde Ontdekking van de Inhoud**: Heb toegang tot alle soorten inhoud van AEM, zoals beelden, video&#39;s, de documenten van PDF, artikelen, en vormen van één enkele conversationele interface.

* **Snellere Planning van de Campagne**: Verzamel snel visuals en vormen voor marketing campagnes over E-mail, Web, en de kanalen van de Sociale.

* **Verbeterde Productiviteit**: Verminder tijd het doorbladeren bewaarplaatsen of het filtreren meta-gegevens door geautomatiseerd, op bedoeling-gebaseerd onderzoek.

* **Consistent Inhoudsgebruik**: Zorgt voor hergebruik van goedgekeurde activa en fragmenten, die merkconsistentie over kanalen handhaven.

>[!VIDEO](https://video.tv.adobe.com/v/3479983)

>[!IMPORTANT]
>
>Door AI gegenereerde reacties kunnen onjuist of misleidend zijn. Controleer de voorgestelde oplossingen en reacties met twee controles.
>
>Zie ook [&#x200B; Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

## Vaardigheden {#skills-discovery-agent}

De agent voor het detecteren van inhoud biedt de volgende vaardigheden:

* **Ontdekking van de natuurlijke taalinhoud**\
  Met de zoekfunctie voor inhoud kunnen gebruikers relevante elementen, inhoudsfragmenten en adaptieve formulieren vinden in Adobe Experience Manager (AEM) met eenvoudige aanwijzingen voor natuurlijke talen. Er zijn geen complexe zoekopdrachten vereist.

* **Op markering-gebaseerde activa ontdekking**

  De agent voor het detecteren van inhoud maakt gebruik van natuurlijke-taalaanwijzingen om te zoeken naar middelen die zijn gekoppeld aan specifieke tags in de AEM-opslagplaats, zodat gebruikers snel toegang krijgen tot inhoud die is geordend of niet is geordend volgens de taxonomie van de organisatie.

* **op omslag-gebaseerde inhoudsontdekking:**\
  De agent voor het detecteren van inhoud kan elementen herkennen door aanwijzingen in de natuurlijke taal te interpreteren die verwijzen naar mapnamen in AEM. Gebruikers kunnen de map gewoon in hun vraag vermelden, zonder handmatig door de opslagplaats te navigeren, waardoor het aantal klikken dat nodig is om de juiste inhoud te zoeken aanzienlijk wordt verminderd.

## Personas {#personas-content-discovery}

### Campagnemanagers {#campaign-managers}

Met de Content Discovery Agent kunnen campagnemanagers vertrouwde, krachtige inhoud voor ideatie snel identificeren en opnieuw gebruiken.

### Kanaalmarkeertekens {#channel-marketers}

Met de Content Discovery Agent kunnen channelmarketers op efficiënte wijze relevante middelen vinden om consistente multi-kanaalervaringen te creëren.

### DAM Libraries {#dam-librarians}

DAM-bibliotheken kunnen elementen markeren die de door de organisatie ingestelde metagegevensstandaarden missen, zodat consistent bestuur wordt ondersteund en wordt gewaarborgd dat de middelen volledig en gebruiksklaar blijven.

### Agentschappen en partners {#agencies-partners}

Agentschappen en partners kunnen in Content Hub eenvoudig door een merk goedgekeurde middelen vinden en deze hergebruiken om creatief werk te versnellen en tegelijkertijd aan de merkstandaarden te blijven voldoen.

## Toegang verkrijgen {#access}

U kunt de agent voor het detecteren van inhoud openen in AEM via de AI Assistant. Logon aan [`experience.adobe.com` &#x200B;](https://experience.adobe.com) en u kunt beginnen met interactie met AI Medewerker door uw herinnering in natuurlijke taal te specificeren gebruikend het onderzoeksvakje:

![&#x200B; de ontdekkingsagent van de inhoud van de Toegang &lbrace;](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

Voor informatie over het MCP eindpunt om tot de agent van de inhoudsontdekking toegang te hebben, contacteer de Steun van Adobe.

## Gebruiksscenario&#39;s en Voorbeeldvragen {#use-cases-prompts}

### Assets {#discovery-agent-use-cases-assets}

**Op markering-gebaseerde activa ontdekking**

De agent voor het detecteren van inhoud maakt gebruik van natuurlijke-taalaanwijzingen om te zoeken naar middelen die zijn gekoppeld aan specifieke tags in de AEM-opslagplaats, zodat gebruikers snel toegang krijgen tot inhoud die is geordend volgens de taxonomie van hun organisatie.

Voorbeeldprompt:

Afbeeldingen met label `office` weergeven in map `WKND` .

**op omslag-gebaseerde inhoudsontdekking:**\
De agent voor het detecteren van inhoud kan elementen herkennen door aanwijzingen in de natuurlijke taal te interpreteren die verwijzen naar mapnamen in AEM. Gebruikers kunnen de map gewoon in hun vraag vermelden, zonder handmatig door de opslagplaats te navigeren, waardoor het aantal klikken dat nodig is om de juiste inhoud te zoeken aanzienlijk wordt verminderd.

Voorbeeld vraagt:

* Zijn er svgs in de map `WKND` ?
* Elementen weergeven die na `Nov 1 2025` in de map `WKND` zijn gewijzigd.
* Lijst `lifestyle` afbeeldingen in map `WKND` .

**op formaat-Gebaseerde activaontdekking**

Met de agent voor het detecteren van inhoud kunt u elementen identificeren die voldoen aan specifieke kwaliteitseisen, zoals bestandsindeling, zodat gebruikers snel productvisuele informatie kunnen vinden die klaar is voor levering van hoge kwaliteit en die via kanalen opnieuw kan worden gebruikt.

Voorbeeldprompt:

PNG-afbeeldingen verpakken van product zoeken.

**Orientation-based inhoudsontdekking**

De agent voor het detecteren van inhoud kan elementen filteren door visuele kenmerken te herkennen, zoals de aanwezigheid van personen en de richting van een afbeelding. Hierdoor kunnen gebruikers inhoud snel verkleinen tot de meest relevante beelden zonder handmatig meerdere filters toe te passen in AEM.

Voorbeeldprompt:

Elementen weergeven met persoon in de stand Liggend.

### Inhoudsfragmenten {#discovery-agent-use-cases-content-fragments}

Met de Content Discovery Agent kunnen gebruikers snel de juiste Content Fragments vinden door verwijzingen naar natuurlijke talen te interpreteren voor campagnemenamen, productmerken, publicatiestatus en recente creatieactiviteiten. Hierdoor kunnen teams fragmenten die klaar zijn voor campagnes, oppervlakkig weergeven en gloedspecifieke inhoud weergeven zonder handmatig door mappen te bladeren of meerdere filters toe te passen in AEM.

Voorbeeld vraagt:

* Toon inhoudsfragmenten voor het creëren van WKND aanbiedingscampagne.

* Toon het inhoudfragment voor de drank van americano.

* Toon me alle gepubliceerde inhoudsfragmenten voor dranken WKND.

* Alle inhoudsfragmenten weergeven die in de afgelopen 2 weken zijn gemaakt.

### Forms {#discovery-agent-use-cases-forms}

Met de zoekfunctie voor inhoud kunt u snel adaptieve formulieren vinden met de aanwijzingen voor natuurlijke talen. Er wordt gezocht in formulierinhoud en metagegevens om overeenkomsten te zoeken op basis van trefwoorden in uw vragen. Dit betekent dat u relevante formulieren kunt detecteren, zelfs als de zoektermen niet in de titel of beschrijving van het formulier staan.

Voorbeeld vraagt:

* Toon mij alle aanvraagformulieren voor leningen.
* Formulieren zoeken die u wilt aanvragen voor een agent.
* Contactformulieren zoeken.
* Ik zoek werknemers aan boord formulieren.
* Formulieren voor creditcardtoepassingen weergeven.

Opmerking: formulierdetectie ondersteunt momenteel alleen Edge Delivery Services-formulieren en zoekopdrachten op basis van tags zijn momenteel niet beschikbaar voor formulieren.

## Zoekresultaten {#discovery-agent-search-results}

### Assets {#discovery-agent-search-results-assets}

De agent van de inhoudsontdekking keert de hoogste resultaten voor elke vraag terug, die door relevantie wordt gesorteerd ervoor te zorgen dat de nauwkeurige gelijken eerst verschijnen. De agent combineert meta-gegeven-gedreven vragen met semantische onderzoek om een geconcentreerde reeks waarschijnlijke gelijken samen te stellen, dan gebruikt een LLM om hen te rangschikken die op gebruikersintent worden gebaseerd. Deze overvloeimethode levert nauwkeurige, contextbewuste resultaten zonder dat deze volledig afhankelijk zijn van een directe trefwoordovereenkomst.

Elk resultaat omvat activa naam samen met zeer belangrijke activa meta-gegevens zoals de activaweg, de schepper, aanmaakdatum, titel, beschrijving, formaat, laatste bepaling, laatste gewijzigde datum, dossiergrootte, dimensies, [&#x200B; Dynamische Media URL &#x200B;](/help/assets/dynamic-media/dynamic-media.md), en bijbehorende markeringen. Als een activa in goedgekeurde staat is, omvatten de resultaten ook [&#x200B; Dynamische Media met OpenAPI URL &#x200B;](/help/assets/dynamic-media-open-apis-overview.md).

U kunt op het middelenpad klikken om naadloos naar de middelenlocatie in AEM te navigeren.

![&#x200B; de activa van het Onderzoek gebruikend de agent van de inhoudsontdekking &#x200B;](/help/ai-in-aem/agents/content-advisor/assets/search-results-discovery-agent.png)

U kunt deze elementdetails gebruiken om snel te evalueren of een element aan de vereisten voldoet zonder naar elk element te navigeren om deze details weer te geven.

>[!NOTE]
>
>Het [&#x200B; Dynamische media URL &#x200B;](/help/assets/dynamic-media/dynamic-media.md) gebiedsvertoningen in de onderzoeksresultaten slechts als de activa wordt gepubliceerd en u een geldige Dynamische vergunning van Media hebt. Op dezelfde manier [&#x200B; Dynamische Media met OpenAPI URL &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) gebiedsvertoningen slechts als u een geldige Dynamische vergunning van Media hebt en Dynamische Media met OpenAPI wordt toegelaten voor uw instantie van AEM as a Cloud Service.

### Inhoudsfragmenten {#discovery-agent-search-results-content-fragments}

De agent voor het detecteren van inhoud biedt zoekmogelijkheden in volledige tekst voor inhoudsfragmenten, waarbij de hoogste resultaten worden geretourneerd die het best overeenkomen met de opgegeven vraag. Elk resultaat bevat de naam van het inhoudsfragment en belangrijke metagegevensvelden, zoals het pad naar het inhoudsfragment, de maker, de aanmaakdatum, variaties, de laatste modifier en de laatst gewijzigde datumvelden.

![&#x200B; de Fragmenten van de Inhoud van het Onderzoek gebruikend de agent van de inhoudsontdekking &#x200B;](/help/ai-in-aem/agents/content-advisor/assets/search-content-fragments-discovery-agent.png)

U kunt op het pad Inhoudsfragment klikken om naadloos naar de locatie Inhoudsfragment in AEM te navigeren.

## Aankondiging van beste praktijken {#prompting-best-practices-discovery-agent}

Geef beknopte details op in de herinneringen voor de natuurlijke taal, zodat de agent nauwkeurige en relevante resultaten kan retourneren. Hoe duidelijker u beschrijft wat u zoekt, hoe beter de agent de uitvoer kan verfijnen en verfijnen. U kunt bijvoorbeeld:

* Metagegevens van elementen definiëren, zoals tags, mapnamen, aanmaakdatums, publicatiestatus, namen van auteurs in uw vragen om elementen te filteren.

* Gebruik uw organisatie-specifieke meta-gegevens, zoals categorieën (lopende schoenen, elektronica), seizoenen (herfst, lente), gebeurtenissen (zwarte Vrijdag, productlancering), en kanalen (Web, E-mail, Druk) om inhoud verder te filtreren.

## Beperkingen {#limitations-discovery-agent}

De agent voor het detecteren van inhoud ondersteunt alleen op dimensies gebaseerde aanwijzingen voor afbeeldings- en SVG-formaattypen. Bijvoorbeeld `Find images wider than 1080px` .
