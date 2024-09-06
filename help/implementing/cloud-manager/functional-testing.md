---
title: Functionele tests
description: Leer meer over de drie verschillende soorten functionele tests die in het AEM as a Cloud Service-implementatieproces zijn ingebouwd om de kwaliteit en betrouwbaarheid van uw code te garanderen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cfaa3be31195929b80310610120a779a20537c61
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 0%

---


# Inleiding {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Leer meer over de drie verschillende soorten functionele tests die in het AEM as a Cloud Service-implementatieproces zijn ingebouwd om de kwaliteit en betrouwbaarheid van uw code te garanderen."

Leer over de kwaliteitshates beschikbaar in het [ plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md), de verschillende soorten functionele ingebouwde tests, hoe u kunt bijdragen en hoe u het beste gebruik van hen in de context van een algemene het testen strategie kunt maken.

## Overzicht

Het volgende diagram verstrekt een overzicht op hoog niveau van de beschikbare pijpleidingen in de context van een algemene het testen strategie en het [ plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md).

![ de plaatsen van de plaatsingskwaliteit van AEM Cloud Service gates ](assets/functional-testing/quality-gates-compact.svg)

## Doel

Het doel van de AEM Cloud Service-distributiepijpleidingen is om robuuste en veilige implementaties in verschillende fasen van de ontwikkelings- en AEM levenscyclus van producten te vergemakkelijken. Deze pijpleidingen omvatten veelvoudige kwaliteitsspoorten op verschillende niveaus om de integriteit en de veiligheid van plaatsingen voor zowel uw AEM toepassingsveranderingen als AEM productupdates te verzekeren.

Adobe biedt verschillende ingebouwde kwaliteitspoorten, terwijl andere toepassingen uw interventie vereisen voor implementatie en configuratie. Deze kwaliteitspoorten zijn veelzijdig, waarbij sommige van deze poorten in verschillende fasen van de levenscyclus van toepassing zijn en zelfs geïntegreerd kunnen worden in uw eigen ontwikkelinstellingen en CI/CD-processen.

De ingebouwde kwaliteitspoorten valideren vooral de functionaliteit van het AEM product binnen de context van uw AEM. De aangepaste kwaliteitskates die u instelt, zijn daarentegen ontworpen om te controleren of de kritieke functies en gebruikersinteracties van uw toepassing naar behoren functioneren. Samen werken deze twee sets kwaliteitspoorten samen om robuuste en beveiligde geautomatiseerde implementaties voor zowel uw codewijzigingen als AEM productupdates te garanderen.

Het is belangrijk om op te merken dat deze kwaliteitspoorten niet bedoeld zijn als een uitgebreid testkader voor uw volledige teststrategie. Het AEM product wordt uitgebreid getest voordat het de AEM implementatieproces van de cloudservice binnengaat. Uw toepassing moet ook al van hoge kwaliteit zijn voordat deze de implementatiefase bereikt. Deze aanpak zorgt ervoor dat de kwaliteitsdoelen zich richten op hun primaire doel om het implementatieproces te waarborgen, in plaats van een volledig testregime te vervangen.

## Kwaliteitsgates

Het volgende diagram verstrekt een gedetailleerde mening van beschikbare kwaliteitskates en hun gebruik in de algemene het testen strategie en het [ de plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md).

![ de plaatsen van de plaatsingskwaliteit van AEM Cloud Service gates ](assets/functional-testing/quality-gates-overview.svg)

### Door de klant geleverde kwaliteitsbonnen

|                               | Eenheidstests | Aangepaste <br/> functionele tests | Aangepaste <br/> UI-tests | Klant <br/> Validaties | Handmatig <br/> testen |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **de Pijpleiding van de Productie** | Ja <br/> het Blokkeren <br/> | Ja <br/> het Blokkeren <br/> 60m Onderbreking | Ja <br/> het Blokkeren <br/> Onderbreking 30m | Nee | Nee |
| **niet-Productie Pijpleiding** | Ja <br/> het Blokkeren <br/> | Opt-binnen <br/> het Blokkeren <br/> 60m Onderbreking | Opt-binnen <br/> het Blokkeren <br/> 30m Onderbreking | Nee | Nee |
| **interne Bevestiging van de Adobe** | Ja <br/> het Blokkeren <br/> | Ja <br/> het Blokkeren <br/> 60m Onderbreking | Ja <br/> het Blokkeren <br/> Onderbreking 30m | Nee | Nee |
| **Klant CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokale Ontwikkelaar van de Klant** | Ja | Ja | Ja | Ja | Ja |

### Eenheidstest

U wordt aangemoedigd om de eenheidstests voor uw AEM toepassing te verstrekken, die de basis van elke teststrategie vormen. Ze zijn bedoeld om snel en vaak te draaien en snel feedback te geven. Ze zijn nauw geïntegreerd in de workflows voor ontwikkelaars, uw eigen CI/CD en de implementatiepijplijnen voor de AEM cloudservice.

Ze worden geïmplementeerd met JUnit en uitgevoerd met Maven. Zie [ kernmodule van het AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/core.html#unit-tests) voor een test van de voorbeeldeenheid voor AEM en begonnen worden.

### Codekwaliteit

Deze kwaliteitspoort is geconfigureerd buiten de box en voert statische codeanalyse uit op uw AEM toepassingscode.

Zie [ het Testen van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md) en [ de kwaliteitsregels van de Code van de Douane ](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor meer informatie.

### Producttests

De functionele tests van het product zijn een reeks stabiele HTTP integratietests (ITs) van kernfunctionaliteit in AEM zoals creatie en replicatietaken. De Adobe verstrekt en handhaaft hen uit-van-de-doos. Ze zijn bedoeld om te voorkomen dat wijzigingen in aangepaste toepassingscode worden geïmplementeerd als deze de kernfunctionaliteit van het AEM verbreekt.

Zij worden uitgevoerd gebruikend Junit, in werking gesteld gebruikend Maven en gebruiken officiële [ AEM het Testen Clients ](https://github.com/adobe/aem-testing-clients). De testsuite voor het product wordt onderhouden zoals
een [ open-bronproject ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke), volgt best-practices en kan als een goed uitgangspunt voor de implementatie van uw tests worden beschouwd.

### Aangepaste functionele tests

Als de producttests, zijn de klanten functionele tests integratietests van HTTP (ITs) en worden zo goed uitgevoerd gebruikend Junit, uitgevoerd gebruikend Maven en gebouwd bovenop de officiële [ AEM het Testen Clients ](https://github.com/adobe/aem-testing-clients).

>[!NOTE]
>
>Aangepaste functionele tests worden uitgevoerd in de productie- en niet-productiepijpleidingen (opt-in) die worden gebruikt door wijzigingen in de implementatie van AEM toepassing en AEM productpushupdates en die daarom een belangrijke bijdrage leveren aan het goed functioneren van uw toepassing en het verhogen van de veiligheid van de release. De functionele tests van de klant worden ook uitgevoerd in interne pre-releasevalideringspijpleidingen voor elke klant, wat helpt om vroege feedback te geven.

Om pijplijnlooppas efficiënt te houden, adviseren wij zich op zeer belangrijke eigenschappen en belangrijkste gebruikersinteractiestromen te concentreren. Een runtime van ~15 minuten of minder voor functionele tests wordt aanbevolen. Volledige functionele testreeksen die niet in deze kwaliteitspoort passen, worden aanbevolen als onderdeel van algemene klantvalideringsleidingen tijdens de ontwikkelingscyclus van de klant.

Zie [ open-sourced producttests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) of de [ it.tests module van het Archetype van de AEM Projecten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/ittests.html) voor voorbeelden.

Zie [ Functionele Tests van Java ](/help/implementing/cloud-manager/java-functional-testing.md) voor meer informatie.

### Aangepaste UI-tests

Om risicobeheersing voor uw klant-specifieke ontwikkeling te maximaliseren, moedigt de Adobe u sterk aan om kritieke tests UI in AEMCS te vangen. Het is de bedoeling dat ze in aantal beperkt blijven, maar met de grootste invloed op uw klantervaring.

De tests worden verpakt in een Docker-afbeelding - ontworpen om zo vluchtig mogelijk te zijn (met ondersteuning voor Cypress, Selenium, Java en Javascript). Ze hebben dezelfde kenmerken en doeleinden als de aangepaste functionele tests.

>[!NOTE]
>
>Aangepaste UI-tests worden uitgevoerd in de productie- en niet-productie (opt-in) pijpleidingen die worden gebruikt door de implementatie van de AEM toepassing en AEM productpush-updates, en vormen daarom een belangrijke bijdrage aan het goed functioneren van uw toepassing en het verhogen van de veiligheid van de release. De tests van de klantengebruikersinterface worden ook uitgevoerd in interne pre-releasebevestigingspijpleidingen voor elke klant, die hulp vroege terugkoppelt verstrekt.
>
>De containers niet-Selenium zouden tests moeten uitvoeren gebruikend een volmacht van HTTP die op de milieuvariabelen in de [ wordt gebaseerd UI die Sectie ](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) testen.

Om pijpleiding efficiënte uitvoeringen te houden, adviseren wij zich op zeer belangrijke eigenschappen en belangrijkste gebruikersinteractiestromen te concentreren. Volledige UI-testsuites die niet in deze kwaliteitspoort passen, worden aanbevolen als onderdeel van algemene klantvalidatiepijpleidingen tijdens de ontwikkelingsstroom van de klant.

Zie [ open-sourced voorbeeldtests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) of de [ ui.tests module van het Archetype van de Projecten van de AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uitests.html) voor voorbeelden.

Zie [ het Testen van UI van de Douane ](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) voor meer informatie.

### Experience Audit

De gate van de ervaringscontrole van de kwaliteit voert [ Lighthouse van Google ](https://developer.chrome.com/docs/lighthouse/overview/) controles tegen de webpagina van de klant uit.

Deze kwaliteitspoort wordt geleverd door AEM kant-en-klaar, maar blokkeert de uitrol van pijpleidingen niet. Door gebrek, wordt een controle tegen de wortelpagina (`/`) van de publiceer instantie uitgevoerd. U kunt bijdragen door maximaal 25 douanewegen te vormen die voor controles worden overwogen.

Zie [ het Testen van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md) voor meer informatie.

### Klantenvalidaties

De kwaliteitsgate voor klantvalidaties is een plaatsaanduiding voor de eigen teststrategie en -inspanning van de klant, die worden uitgevoerd voordat de wijzigingen in de toepassing van de klant de implementatiepijplijnen van de AEM cloud bereiken.

Hier kunt u de gewenste gereedschappen en frameworks kiezen. In tegenstelling tot de tests van de klantenfunctie en van de douane UI, zijn er geen aan AEM as a Cloud Service verwante grenzen, en wij adviseren daarom om de functie en UI het testen hier uit te voeren.

Terwijl u om het even welk hulpmiddel en kader vrij kunt kiezen, adviseren wij u op HTTP-Gebaseerde integratietests en tests UI met de hulpmiddelen en het kader beschikbaar in de de kwaliteitsproeven van de douane functionele tests en van de douanetest UI. Wij adviseren het integreren [ Snelle Milieu&#39;s van de Ontwikkeling (RDE) ](/help/implementing/developing/introduction/rapid-development-environments.md) in uw lokale testende strategie om zo dicht mogelijk aan AEM wolkenmilieu&#39;s te testen.

### Handmatig testen

De poort voor het handmatig testen van de kwaliteit is een plaatsaanduiding voor klanten die handmatig testen uitvoeren. AEM wolkenpijpleidingen ondersteunen handmatige tests niet en dit moet daarom gebeuren als onderdeel van uw eigen lokale teststrategie.

Voor handmatige tests kan het nuttig zijn om te integreren met een extra AEM Cloud Service-ontwikkelomgeving.
