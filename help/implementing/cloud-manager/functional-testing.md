---
title: Functionele tests
description: Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 305098c7ebcb6145129b146d60538b5177b4f26d
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 0%

---


# Inleiding {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Leer over de drie verschillende types van functionele tests die in het AEM as a Cloud Service plaatsingsproces worden gebouwd om kwaliteit en betrouwbaarheid van uw code te verzekeren."

Meer informatie over de kwaliteitskates in het dialoogvenster [as a Cloud Service implementatieproces AEM](/help/implementing/cloud-manager/deploy-code.md), de verschillende ingebouwde soorten functionele tests, hoe u kunt bijdragen en hoe u deze optimaal kunt gebruiken in de context van een algemene teststrategie.

## Overzicht

Het volgende diagram geeft een overzicht op hoog niveau van de beschikbare pijpleidingen in de context van een algemene teststrategie en de [as a Cloud Service implementatieproces AEM](/help/implementing/cloud-manager/deploy-code.md).

![AEM Cloud Service-implementatiekwaliteitspoorten](assets/functional-testing/quality-gates-compact.svg)

## Doel

Het doel van de AEM Cloud Service-distributiepijpleidingen is om robuuste en veilige implementaties in verschillende fasen van de ontwikkelings- en AEM levenscyclus van producten te vergemakkelijken. Deze pijpleidingen omvatten veelvoudige kwaliteitsspoorten op verschillende niveaus om de integriteit en de veiligheid van plaatsingen voor zowel uw AEM toepassingsveranderingen als AEM productupdates te verzekeren.

Adobe biedt verschillende ingebouwde kwaliteitspoorten, terwijl andere toepassingen uw interventie vereisen voor implementatie en configuratie. Deze kwaliteitspoorten zijn veelzijdig, waarbij sommige van deze poorten in verschillende fasen van de levenscyclus van toepassing zijn en zelfs geïntegreerd kunnen worden in uw eigen ontwikkelinstellingen en CI/CD-processen.

De ingebouwde kwaliteitspoorten valideren vooral de functionaliteit van het AEM product binnen de context van uw AEM. De aangepaste kwaliteitskates die u instelt, zijn daarentegen ontworpen om te controleren of de kritieke functies en gebruikersinteracties van uw toepassing naar behoren functioneren. Samen werken deze twee sets kwaliteitspoorten samen om robuuste en beveiligde geautomatiseerde implementaties voor zowel uw codewijzigingen als AEM productupdates te garanderen.

Het is belangrijk om op te merken dat deze kwaliteitspoorten niet bedoeld zijn als een uitgebreid testkader voor uw volledige teststrategie. Het AEM product wordt uitgebreid getest voordat het de AEM implementatieproces van de cloudservice binnengaat. Uw toepassing moet ook al van hoge kwaliteit zijn voordat deze de implementatiefase bereikt. Deze aanpak zorgt ervoor dat de kwaliteitsdoelen zich richten op hun primaire doel om het implementatieproces te waarborgen, in plaats van een volledig testregime te vervangen.

## Kwaliteitsgates

Het volgende diagram geeft een gedetailleerd overzicht van de beschikbare kwaliteitskates en het gebruik ervan in de algemene teststrategie en de [as a Cloud Service implementatieproces AEM](/help/implementing/cloud-manager/deploy-code.md).

![AEM Cloud Service-implementatiekwaliteitspoorten](assets/functional-testing/quality-gates-overview.svg)

### Door de klant geleverde kwaliteitsbonnen

|                               | Eenheidstests | Aangepast<br/> Functionele tests | Aangepast<br/> UI-tests | Klant<br/> Validaties | Handmatig<br/> Testen |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Productiepijpleiding** | Ja<br/>Blokkeren<br/> | Ja<br/>Blokkeren<br/>60m Time-out | Ja<br/>Blokkeren<br/>Tijdslimiet van 30 m | Nee | Nee |
| **Niet-productiepijpleiding** | Ja<br/>Blokkeren<br/> | Inschakelen<br/>Blokkeren<br/>60m Time-out | Inschakelen<br/>Blokkeren<br/>Tijdslimiet van 30 m | Nee | Nee |
| **Interne validatie Adobe** | Ja<br/>Blokkeren<br/> | Ja<br/>Blokkeren<br/>60m Time-out | Ja<br/>Blokkeren<br/>Tijdslimiet van 30 m | Nee | Nee |
| **Klant-CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokale ontwikkelaar van klant** | Ja | Ja | Ja | Ja | Ja |

### Eenheidstest

U wordt aangemoedigd om de eenheidstests voor uw AEM toepassing te verstrekken, die de basis van elke teststrategie vormen. Ze zijn bedoeld om snel en vaak te draaien en snel feedback te geven. Ze zijn nauw geïntegreerd in de workflows voor ontwikkelaars, uw eigen CI/CD en de implementatiepijplijnen voor de AEM cloudservice.

Ze worden geïmplementeerd met JUnit en uitgevoerd met Maven. Zie [kernmodule van het AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/core.html#unit-tests) voor een voorbeeldeenheidstest voor AEM en aan de slag gaan.

### Codekwaliteit

Deze kwaliteitspoort is geconfigureerd buiten de box en voert statische codeanalyse uit op uw AEM toepassingscode.

Zie [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md) en [Aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor meer informatie .

### Producttests

De functionele tests van het product zijn een reeks stabiele HTTP integratietests (ITs) van kernfunctionaliteit in AEM zoals creatie en replicatietaken. De Adobe verstrekt en handhaaft hen uit-van-de-doos. Ze zijn bedoeld om te voorkomen dat wijzigingen in aangepaste toepassingscode worden geïmplementeerd als deze de kernfunctionaliteit van het AEM verbreekt.

Ze worden geïmplementeerd met Junit, worden uitgevoerd met Maven en gebruiken de officiële [Clients AEM testen](https://github.com/adobe/aem-testing-clients). De producttestsuite wordt als een [open-source-project](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke), volgt de beste praktijken en kan als een goed uitgangspunt voor de implementatie van uw tests worden beschouwd.

### Aangepaste functionele tests

Zoals de producttests, zijn de functionele tests van de klant de integratietests van HTTP (ITs) en worden zo goed uitgevoerd gebruikend Junit, uitgevoerd gebruikend Maven en gebouwd bovenop de officiële [Clients AEM testen](https://github.com/adobe/aem-testing-clients).

>[!NOTE]
>
>Aangepaste functionele tests worden uitgevoerd in de productie- en niet-productiepijpleidingen (opt-in) die worden gebruikt door wijzigingen in de implementatie van AEM toepassing en AEM productpushupdates en die daarom een belangrijke bijdrage leveren aan het goed functioneren van uw toepassing en het verhogen van de veiligheid van de release. De functionele tests van de klant worden ook uitgevoerd in interne pre-releasevalideringspijpleidingen voor elke klant, wat helpt om vroege feedback te geven.

Om pijplijnlooppas efficiënt te houden, adviseren wij zich op zeer belangrijke eigenschappen en belangrijkste gebruikersinteractiestromen te concentreren. Een runtime van ~15 minuten of minder voor functionele tests wordt aanbevolen. Volledige functionele testreeksen die niet in deze kwaliteitspoort passen, worden aanbevolen als onderdeel van algemene klantvalideringsleidingen tijdens de ontwikkelingscyclus van de klant.

Zie [open-sourced producttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) of de [it.tests module van de Archetype van de Projecten van de AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/ittests.html) voor voorbeelden.

Zie [Functionele Java-tests](/help/implementing/cloud-manager/java-functional-testing.md) voor meer informatie .

### Aangepaste UI-tests

Om risicobeheersing voor uw klant-specifieke ontwikkeling te maximaliseren, moedigt de Adobe u sterk aan om kritieke tests UI in AEMCS te vangen. Het is de bedoeling dat ze in aantal beperkt blijven, maar met de grootste invloed op uw klantervaring.

De tests worden verpakt in een Docker-afbeelding - ontworpen om zo vluchtig mogelijk te zijn (met ondersteuning voor Cypress, Selenium, Java en Javascript). Ze hebben dezelfde kenmerken en doeleinden als de aangepaste functionele tests.

>[!NOTE]
>
>Aangepaste UI-tests worden uitgevoerd in de productie- en niet-productie (opt-in) pijpleidingen die worden gebruikt door de implementatie van de AEM toepassing en AEM productpush-updates, en vormen daarom een belangrijke bijdrage aan het goed functioneren van uw toepassing en het verhogen van de veiligheid van de release. De tests van de klantengebruikersinterface worden ook uitgevoerd in interne pre-releasebevestigingspijpleidingen voor elke klant, die hulp vroege terugkoppelt verstrekt.
>
>Niet-seleniumcontainers moeten tests uitvoeren met een HTTP-proxy op basis van de omgevingsvariabelen in de [Sectie voor testen gebruikersinterface.](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing)

Om pijpleiding efficiënte uitvoeringen te houden, adviseren wij zich op zeer belangrijke eigenschappen en belangrijkste gebruikersinteractiestromen te concentreren. Volledige UI-testsuites die niet in deze kwaliteitspoort passen, worden aanbevolen als onderdeel van algemene klantvalidatiepijpleidingen tijdens de ontwikkelingsstroom van de klant.

Zie [open-sourced voorbeeldtests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) of de [ui.tests module van de Archetype van de Projecten van de AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uitests.html) voor voorbeelden.

Zie [Aangepaste UI-tests](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) voor meer informatie .

### Experience Audit

Het kwaliteitsgate van de ervaringscontrole wordt uitgevoerd [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/) op de website van de klant.

Deze kwaliteitspoort wordt geleverd door AEM kant-en-klaar, maar blokkeert de uitrol van pijpleidingen niet. Standaard wordt een controle uitgevoerd op de hoofdpagina (`/`) van het publicatieexemplaar wordt uitgevoerd. U kunt bijdragen door maximaal 25 douanewegen te vormen die voor controles worden overwogen.

Zie [Ervaring controleren testen](/help/implementing/cloud-manager/experience-audit-testing.md) voor meer informatie .

### Klantenvalidaties

De kwaliteitsgate voor klantvalidaties is een plaatsaanduiding voor de eigen teststrategie en -inspanning van de klant, die worden uitgevoerd voordat de wijzigingen in de toepassing van de klant de implementatiepijplijnen van de AEM cloud bereiken.

Hier kunt u de gewenste gereedschappen en frameworks kiezen. In tegenstelling tot de tests van de klantenfunctie en van de douaneUI, zijn er geen AEM as a Cloud Service verwante grenzen, en wij adviseren daarom om de functie en UI het testen hier uit te voeren.

Terwijl u om het even welk hulpmiddel en kader vrij kunt kiezen, adviseren wij u op HTTP-Gebaseerde integratietests en tests UI met de hulpmiddelen en het kader beschikbaar in de de kwaliteitsproeven van de douane functionele tests en van de douanetest UI. We raden u aan om integratie [Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) in uw lokale teststrategie om zo dicht mogelijk bij AEM cloudomgevingen te testen.

### Handmatig testen

De poort voor het handmatig testen van de kwaliteit is een plaatsaanduiding voor klanten die handmatig testen uitvoeren. AEM wolkenpijpleidingen ondersteunen handmatige tests niet en dit moet daarom gebeuren als onderdeel van uw eigen lokale teststrategie.

Voor handmatige tests kan het nuttig zijn om te integreren met een extra AEM Cloud Service-ontwikkelomgeving.
