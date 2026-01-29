---
title: Overzicht van zoekagent
description: Leer hoe u de Discovery Agent kunt gebruiken om relevante AEM-inhoud op aanvraag te leveren via natuurlijke, conversationele herinneringen voor een gestroomlijnde, klikvrije ontdekkingservaring.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: d0c683d20f8932683d3d0aa11a67be92d35b725c
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 0%

---


# Detectieagent {#discovery-agent}

De Discovery Agent levert AEM-inhoud op aanvraag via natuurlijke, conversationele aanwijzingen voor een gestroomlijnde, klikvrije detectiervaring. In Assets, Content Fragments en Adaptive Forms wordt op intelligente wijze gezocht naar relevante materialen, zoals afbeeldingen, video&#39;s, PDF-documenten, artikelen en formuliersjablonen. Met de natuurlijke taal kunt u naar inhoud zoeken zonder complexe query&#39;s te maken of filters toe te passen in de AEM Assets-interface. Gebaseerd op uw herinnering, keert de agent gekromde resultaten samen met activa meta-gegevens en levering URLs terug, klaar om in andere toepassingen worden ingebed.

Enkele belangrijke voordelen van Discovery Agent zijn:

* **Verenigde Ontdekking van de Inhoud**: Heb toegang tot alle soorten inhoud van AEM, zoals beelden, video&#39;s, de documenten van PDF, artikelen, en vormen van één enkele conversationele interface.

* **Snellere Planning van de Campagne**: Verzamel snel visuals en vormen voor marketing campagnes over E-mail, Web, en de kanalen van de Sociale.

* **Verbeterde Productiviteit**: Verminder tijd het doorbladeren bewaarplaatsen of het filtreren meta-gegevens door geautomatiseerd, op bedoeling-gebaseerd onderzoek.

* **Consistent Inhoudsgebruik**: Zorgt voor hergebruik van goedgekeurde activa en fragmenten, die merkconsistentie over kanalen handhaven.

>[!IMPORTANT]
>
>Door AI gegenereerde reacties kunnen onjuist of misleidend zijn. Controleer de voorgestelde oplossingen en reacties met twee controles.
>
>Zie ook [&#x200B; Generatieve AI de Richtlijnen van de Gebruiker van Adobe Experience Cloud &#x200B;](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Vaardigheden {#skills-discovery-agent}

De zoekagent biedt de volgende vaardigheden:

* **Ontdekking van de natuurlijke taalinhoud**\
  Met de zoekagent kunnen gebruikers relevante elementen, inhoudsfragmenten en adaptieve formulieren vinden in Adobe Experience Manager (AEM) met eenvoudige aanwijzingen voor natuurlijke talen. Er zijn geen complexe zoekopdrachten vereist.

* **Op markering-gebaseerde activa ontdekking**

  De zoekagent gebruikt zoekopdrachten in de natuurlijke taal om te zoeken naar middelen die zijn gekoppeld aan specifieke tags in de AEM-opslagplaats, zodat gebruikers snel toegang krijgen tot inhoud die is georganiseerd of niet is georganiseerd volgens de taxonomie van de organisatie.

* **op omslag-gebaseerde inhoudsontdekking:**\
  De zoekagent kan middelen identificeren door aanwijzingen in de natuurlijke taal te interpreteren die verwijzen naar mapnamen in AEM. Gebruikers kunnen de map gewoon in hun vraag vermelden, zonder handmatig door de opslagplaats te navigeren, waardoor het aantal klikken dat nodig is om de juiste inhoud te zoeken aanzienlijk wordt verminderd.

## Personas {#personas-discovery-agent}

### Campagnemanagers {#campaign-managers}

Met Discovery Agent kunnen campagnebeheerders vertrouwde, krachtige inhoud voor ideatie snel identificeren en opnieuw gebruiken.

### Kanaalmarkeertekens {#channel-marketers}

Met Discovery Agent kunnen Channel Marketers op efficiënte wijze relevante middelen vinden om consistente, meerkanaalse ervaringen te creëren.

### DAM Libraries {#dam-librarians}

De DAM-bibliotheken kunnen activa markeren die de door de organisatie vastgestelde metagegevensnormen missen, een consistent bestuur ondersteunen en ervoor zorgen dat de middelen volledig en gebruiksklaar blijven.

### Agentschappen en partners {#agencies-partners}

Agentschappen en partners kunnen eenvoudig door een merk goedgekeurde middelen vinden in Content Hub en deze hergebruiken om creatief werk te versnellen en tegelijk op de merkstandaarden te blijven aansluiten.

## Hoe toegang te krijgen tot Discovery Agent? {#access-discovery-agent}

Via de AI-assistent hebt u toegang tot de agents in AEM. Meld u aan bij experience.adobe.com en u kunt interactie aangaan met AI Assistant door de vraag in de natuurlijke taal op te geven met behulp van het zoekvak:

![&#x200B; de Agent van de Ontdekking van de Toegang &#x200B;](/help/ai-in-aem/agents/discovery/assets/access-discovery-agent.png)

Voor informatie over het MCP eindpunt om tot de Agent van de Ontdekking toegang te hebben, contacteer de Steun van Adobe.

## Gebruikskwesties en voorbeeldaanwijzingen {#use-cases-prompts}

### Assets {#discovery-agent-use-cases-assets}

**Op markering-gebaseerde activa ontdekking**

De zoekagent gebruikt zoekopdrachten in de natuurlijke taal om te zoeken naar middelen die zijn gekoppeld aan specifieke tags in de AEM-opslagplaats, zodat gebruikers snel toegang krijgen tot inhoud die is geordend volgens de taxonomie van hun organisatie.

Voorbeeldprompt:

Afbeeldingen met label `office` weergeven in map `WKND` .

**op omslag-gebaseerde inhoudsontdekking:**\
De zoekagent kan middelen identificeren door aanwijzingen in de natuurlijke taal te interpreteren die verwijzen naar mapnamen in AEM. Gebruikers kunnen de map gewoon in hun vraag vermelden, zonder handmatig door de opslagplaats te navigeren, waardoor het aantal klikken dat nodig is om de juiste inhoud te zoeken aanzienlijk wordt verminderd.

Voorbeeld vraagt:

* Zijn er svgs in de map `WKND` ?
* Elementen weergeven die na `Nov 1 2025` in de map `WKND` zijn gewijzigd.
* Lijst `lifestyle` afbeeldingen in map `WKND` .

**op formaat-Gebaseerde activaontdekking**

De zoekagent kan middelen identificeren die voldoen aan specifieke kwaliteitseisen, zoals bestandsindeling, zodat gebruikers snel productbeelden kunnen vinden die klaar zijn voor levering van hoge kwaliteit en die via kanalen kunnen worden hergebruikt.

Voorbeeldprompt:

PNG-afbeeldingen verpakken van product zoeken.

**Orientation-based inhoudsontdekking**

De zoekagent kan elementen filteren door visuele kenmerken, zoals de aanwezigheid van personen en de richting van een afbeelding, te herkennen. Hierdoor kunnen gebruikers inhoud snel verkleinen tot de meest relevante beelden zonder handmatig meerdere filters toe te passen in AEM.

Voorbeeldprompt:

Elementen weergeven met persoon in de stand Liggend.

### Inhoudsfragmenten {#discovery-agent-use-cases-content-fragments}

Met de zoekagent kunnen gebruikers snel de juiste Content Fragments vinden door verwijzingen naar de natuurlijke taal te interpreteren voor campagnemenamen, productmerken, publicatiestatus en recente creatieactiviteiten. Hierdoor kunnen teams fragmenten die klaar zijn voor campagnes, oppervlakkig weergeven en gloedspecifieke inhoud weergeven zonder handmatig door mappen te bladeren of meerdere filters toe te passen in AEM.

Voorbeeld vraagt:

* Toon inhoudsfragmenten voor het creëren van WKND aanbiedingscampagne.

* Toon het inhoudfragment voor de drank van americano.

* Toon me alle gepubliceerde inhoudsfragmenten voor dranken WKND.

* Alle inhoudsfragmenten weergeven die in de afgelopen 2 weken zijn gemaakt.

### Forms {#discovery-agent-use-cases-forms}

Met de zoekagent kunt u snel adaptieve formulieren vinden met de aanwijzingen voor natuurlijke talen. Er wordt gezocht in formulierinhoud en metagegevens om overeenkomsten te zoeken op basis van trefwoorden in uw vragen. Dit betekent dat u relevante formulieren kunt detecteren, zelfs als de zoektermen niet in de titel of beschrijving van het formulier staan.

Voorbeeld vraagt:

* Toon mij alle aanvraagformulieren voor leningen.
* Formulieren zoeken die u wilt aanvragen voor een taak.
* Contactformulieren zoeken.
* Ik zoek werknemers aan boord formulieren.
* Formulieren voor creditcardtoepassingen weergeven.

Opmerking: formulierdetectie ondersteunt momenteel alleen Edge Delivery Services-formulieren en zoekopdrachten op basis van tags zijn momenteel niet beschikbaar voor formulieren.

## Zoekresultaten {#discovery-agent-search-results}

### Assets {#discovery-agent-search-results-assets}

De agent van de Ontdekking keert de hoogste resultaten voor elke vraag terug, die door relevantie wordt gesorteerd om ervoor te zorgen dat de nauwkeurige gelijken eerst verschijnen. De agent combineert meta-gegeven-gedreven vragen met semantische onderzoek om een geconcentreerde reeks waarschijnlijke gelijken samen te stellen, dan gebruikt een LLM om hen te rangschikken die op gebruikersintent worden gebaseerd. Deze overvloeimethode levert nauwkeurige, contextbewuste resultaten zonder dat deze volledig afhankelijk zijn van een directe trefwoordovereenkomst.

Elk resultaat omvat activa naam samen met zeer belangrijke activa meta-gegevens zoals de activaweg, de schepper, aanmaakdatum, titel, beschrijving, formaat, laatste bepaling, laatste gewijzigde datum, dossiergrootte, dimensies, [&#x200B; Dynamische Media URL &#x200B;](/help/assets/dynamic-media/dynamic-media.md), en bijbehorende markeringen. Als een activa in goedgekeurde staat is, omvatten de resultaten ook [&#x200B; Dynamische Media met OpenAPI URL &#x200B;](/help/assets/dynamic-media-open-apis-overview.md).

U kunt op het middelenpad klikken om naadloos naar de middelenlocatie in AEM te navigeren.

![&#x200B; activa van het Onderzoek gebruikend de Agent van de Ontdekking &#x200B;](/help/ai-in-aem/agents/discovery/assets/search-results-discovery-agent.png)

U kunt deze elementdetails gebruiken om snel te evalueren of een element aan de vereisten voldoet zonder naar elk element te navigeren om deze details weer te geven.

>[!NOTE]
>
>Het [&#x200B; Dynamische media URL &#x200B;](/help/assets/dynamic-media/dynamic-media.md) gebiedsvertoningen in de onderzoeksresultaten slechts als de activa wordt gepubliceerd en u een geldige Dynamische vergunning van Media hebt. Op dezelfde manier [&#x200B; Dynamische Media met OpenAPI URL &#x200B;](/help/assets/dynamic-media-open-apis-overview.md) gebiedsvertoningen slechts als u een geldige Dynamische vergunning van Media hebt en Dynamische Media met OpenAPI wordt toegelaten voor uw instantie van AEM as a Cloud Service.

### Inhoudsfragmenten {#discovery-agent-search-results-content-fragments}

De zoekagent biedt zoekmogelijkheden met volledige tekst voor inhoudsfragmenten, waarbij de hoogste resultaten worden geretourneerd die het best overeenkomen met de opgegeven prompt. Elk resultaat bevat de naam van het inhoudsfragment en belangrijke metagegevensvelden, zoals het pad naar het inhoudsfragment, de maker, de aanmaakdatum, variaties, de laatste modifier en de laatst gewijzigde datumvelden.

![&#x200B; Fragmenten van de Inhoud van het Onderzoek gebruikend de Agent van de Ontdekking &#x200B;](/help/ai-in-aem/agents/discovery/assets/search-content-fragments-discovery-agent.png)

U kunt op het pad Inhoudsfragment klikken om naadloos naar de locatie Inhoudsfragment in AEM te navigeren.

## Aankondiging van aanbevolen procedures {#prompting-best-practices-discovery-agent}

Geef beknopte details op in de herinneringen voor de natuurlijke taal, zodat de agent nauwkeurige en relevante resultaten kan retourneren. Hoe duidelijker u beschrijft wat u zoekt, hoe beter de agent de uitvoer kan verfijnen en verfijnen. U kunt bijvoorbeeld:

* Metagegevens van elementen definiëren, zoals tags, mapnamen, aanmaakdatums, publicatiestatus, namen van auteurs in uw vragen om elementen te filteren.

* Gebruik uw organisatie-specifieke meta-gegevens, zoals categorieën (lopende schoenen, elektronica), seizoenen (herfst, lente), gebeurtenissen (zwarte Vrijdag, productlancering), en kanalen (Web, E-mail, Druk) om inhoud verder te filtreren.

## Beperkingen {#limitations-discovery-agent}

De Agent van de ontdekking steunt afmetingsgebaseerde herinneringen slechts voor beeld en formaat SVG types. Bijvoorbeeld `Find images wider than 1080px` .
