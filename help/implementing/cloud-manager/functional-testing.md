---
title: Functionele tests
description: Leer meer over de drie verschillende soorten functionele tests die in het AEM as a Cloud Service-implementatieproces zijn ingebouwd om de kwaliteit en betrouwbaarheid van uw code te garanderen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 05531a5c1eca996bd3652d6ce6233b7a960d0bc9
workflow-type: tm+mt
source-wordcount: '1322'
ht-degree: 0%

---


# Inleiding {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Functionele tests"
>abstract="Leer meer over de drie verschillende soorten functionele tests die in het AEM as a Cloud Service-implementatieproces zijn ingebouwd om de kwaliteit en betrouwbaarheid van uw code te garanderen."

Ontdek de kwaliteitspoorten beschikbaar in het [ de plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md) en de diverse soorten ingebouwde functionele het testen. Leer hoe u hun gebruik kunt bijdragen en optimaliseren in het kader van een uitgebreide teststrategie.

## Informatie over functionele tests

Het volgende diagram verstrekt een overzicht op hoog niveau van de beschikbare pijpleidingen in de context van een algemene het testen strategie en het [ plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md).

![ de plaatsen van de plaatsingskwaliteit van AEM Cloud Service gates ](assets/functional-testing/quality-gates-compact.svg)

## Doel van functionele tests

Het doel van de AEM Cloud Service-distributiepijpleidingen is om robuuste en veilige implementaties in verschillende fasen van de ontwikkelings- en AEM levenscyclus van producten te vergemakkelijken. Deze pijpleidingen omvatten veelvoudige kwaliteitsspoorten op verschillende niveaus om de integriteit en de veiligheid van plaatsingen voor zowel uw AEM toepassingsveranderingen als AEM productupdates te verzekeren.

Adobe biedt verschillende ingebouwde kwaliteitspoorten, terwijl andere toepassingen uw interventie vereisen voor implementatie en configuratie. Deze kwaliteitspoorten zijn veelzijdig, worden tijdens verschillende levenscyclusfasen toegepast en worden rechtstreeks geïntegreerd in uw ontwikkelinstellingen en CI/CD-processen.

De ingebouwde kwaliteitspoorten valideren vooral de functionaliteit van het AEM product binnen de context van uw AEM. De aangepaste kwaliteitskates die u instelt, zijn daarentegen ontworpen om te controleren of de kritieke functies en gebruikersinteracties van uw toepassing naar behoren functioneren. Samen werken deze twee sets kwaliteitspoorten samen om robuuste en beveiligde geautomatiseerde implementaties voor zowel uw codewijzigingen als AEM productupdates te garanderen.

Het is belangrijk om op te merken dat deze kwaliteitspoorten niet bedoeld zijn als een uitgebreid testkader voor uw volledige teststrategie. Het AEM product wordt uitgebreid getest voordat het de AEM implementatieproces van de cloudservice binnengaat. Uw toepassing moet ook al van hoge kwaliteit zijn voordat deze de implementatiefase bereikt. Deze aanpak zorgt ervoor dat de kwaliteitsdoelen zich richten op hun primaire doel om het implementatieproces te waarborgen, in plaats van een volledig testregime te vervangen.

## Kwaliteitscijfers bij tests

Het volgende diagram verstrekt een gedetailleerde mening van beschikbare kwaliteitskates en hun gebruik in de algemene het testen strategie en het [ de plaatsingsproces van AEM as a Cloud Service ](/help/implementing/cloud-manager/deploy-code.md).

![ de plaatsen van de plaatsingskwaliteit van AEM Cloud Service gates ](assets/functional-testing/quality-gates-overview.svg)

### Door de klant geleverde kwaliteitsmodellen

|                               | Eenheidstests | Aangepaste <br/> functionele tests | Aangepaste <br/> UI-tests | Klant <br/> Validaties | Handmatig <br/> testen |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **de Pijpleiding van de Productie** | Ja <br/> het Blokkeren <br/> | Ja <br/> het Blokkeren <br/> 60m Onderbreking | Ja <br/> het Blokkeren <br/> Onderbreking 30m | Nee | Nee |
| **niet-Productie Pijpleiding** | Ja <br/> het Blokkeren <br/> | Opt-binnen <br/> het Blokkeren <br/> 60m Onderbreking | Opt-binnen <br/> het Blokkeren <br/> 30m Onderbreking | Nee | Nee |
| **interne Bevestiging van de Adobe** | Ja <br/> het Blokkeren <br/> | Ja <br/> het Blokkeren <br/> 60m Onderbreking | Ja <br/> het Blokkeren <br/> Onderbreking 30m | Nee | Nee |
| **Klant CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokale Ontwikkelaar van de Klant** | Ja | Ja | Ja | Ja | Ja |

### Eenheidstest

U wordt aangemoedigd om de eenheidstests voor uw AEM toepassing te verstrekken, die de basis van elke teststrategie vormen. Ze zijn bedoeld om snel en vaak te draaien en snel feedback te geven. Ze zijn nauw geïntegreerd in de workflows voor ontwikkelaars, uw eigen CI/CD en de implementatiepijplijnen voor de AEM cloudservice.

Ze worden geïmplementeerd met JUnit en uitgevoerd met Maven. Zie de [ kernmodule van het Archetype van het Project van de AEM ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/developing/archetype/using#unit-tests) voor een test van de voorbeeldeenheid voor AEM en begonnen worden.

### Codekwaliteit

Deze kwaliteitspoort is geconfigureerd buiten de box en voert statische codeanalyse uit op uw AEM toepassingscode.

Zie [ het Testen van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md) en [ de kwaliteitsregels van de Code van de Douane ](/help/implementing/cloud-manager/custom-code-quality-rules.md) voor meer informatie.

### Producttests

De functionele tests van het product zijn stabiele de integratietests van HTTP (ITs) voor kern AEM functionaliteit, met inbegrip van creatie en replicatietaken. De Adobe verstrekt en handhaaft hen uit-van-de-doos. Ze zijn bedoeld om te voorkomen dat wijzigingen in aangepaste toepassingscode worden geïmplementeerd als deze de kernfunctionaliteit van het AEM verbreekt.

Zij gebruiken JUnit voor implementatie, lopen met Maven, en baseren zich op officiële [ AEM het Testen Clients ](https://github.com/adobe/aem-testing-clients). De testsuite voor het product wordt onderhouden zoals
een [ open-bronproject ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke), volgt best-practices en kan als een goed uitgangspunt voor de implementatie van uw tests worden beschouwd.

### Aangepaste functionele tests

Gelijkaardig aan de producttests, zijn de functionele tests van de klant de integratietests van HTTP (ITs) die met JUnit worden uitgevoerd, lopen gebruikend Maven, en bovenop de officiële [ AEM het Testen Clients ](https://github.com/adobe/aem-testing-clients) worden gebouwd.

>[!NOTE]
>
>Aangepaste functionele tests worden uitgevoerd in zowel productie- als niet-productie (opt-in) pijpleidingen die worden gebruikt voor AEM implementatie van toepassingswijzigingen en AEM productenpushupdates. Ze spelen een cruciale rol bij het waarborgen van de juiste werking van uw toepassing en het verbeteren van de veiligheid van de release. De functionele tests van de klant worden ook uitgevoerd in interne pre-releasevalideringspijpleidingen voor elke klant, wat helpt om vroege feedback te geven.

Om efficiënte pijpleidingslooppas te handhaven, adviseert de Adobe zich op zeer belangrijke eigenschappen en primaire gebruikersinteractiestromen te concentreren, die voor een functionele testruntime van rond 15 minuten of minder richten. Volledige functionele testreeksen die deze tijd overschrijden, moeten worden uitgevoerd als onderdeel van de algemene klantenvalidatiepijpleidingen tijdens het ontwikkelingsproces.

Zie [ open-sourced producttests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) of de [ it.tests module van het Archetype van de AEM Projecten ](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests) voor voorbeelden.

Zie [ Functionele Tests van Java ](/help/implementing/cloud-manager/java-functional-testing.md) voor meer informatie.

### Aangepaste UI-tests

Om risicobeheersing voor uw klant-specifieke ontwikkeling te maximaliseren, moedigt de Adobe u aan om kritieke tests UI in AEM as a Cloud Service te vangen. Houd ze beperkt, maar richt zich op het maximaliseren van hun impact op de klantervaring.

De tests worden verpakt in een Docker-afbeelding - ontworpen om zo vluchtig mogelijk te zijn (met ondersteuning voor Cypress, Playwright, Selenium, Java en JavaScript). Ze hebben dezelfde kenmerken en doeleinden als de aangepaste functionele tests.

>[!NOTE]
>
>Aangepaste UI-tests worden uitgevoerd in zowel productie- als niet-productie (opt-in) pijpleidingen die worden gebruikt voor AEM implementatie van toepassingswijzigingen en AEM productenpushupdates. Ze zijn essentieel om ervoor te zorgen dat uw toepassing correct werkt en om de veiligheid van het vrijkomen te verbeteren. De tests van de klantengebruikersinterface worden ook uitgevoerd in interne pre-releasebevestigingspijpleidingen voor elke klant, die hulp vroege terugkoppelt verstrekt.
>
>De containers niet-Selenium zouden tests moeten uitvoeren gebruikend een volmacht van HTTP die op de milieuvariabelen in de [ wordt gebaseerd UI die Sectie ](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) testen.

Om de uitvoering van pijpleidingen efficiënt te houden, adviseert de Adobe zich op zeer belangrijke eigenschappen en belangrijkste gebruikersinteractiestromen te concentreren. Volledige UI-testreeksen die deze kwaliteitspoort overschrijden, moeten worden uitgevoerd als onderdeel van de algemene klantenvalidatiepijplijnen. Neem ze op in het ontwikkelingsproces van de klant.

Zie [ open-sourced voorbeeldtests ](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) of de [ ui.tests module van het Archetype van de Projecten van de AEM ](/help/implementing/cloud-manager/ui-testing.md) voor voorbeelden.

Zie [ het Testen van UI van de Douane ](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) voor meer informatie.

### Ervaring audit

De gate van de ervaringscontrole van de kwaliteit voert [ Lighthouse van Google ](https://developer.chrome.com/docs/lighthouse/overview/) controles tegen de webpagina van de klant uit.

Deze kwaliteitspoort wordt geleverd door AEM kant-en-klaar, maar blokkeert de uitrol van pijpleidingen niet. Door gebrek, wordt een controle tegen de wortelpagina (`/`) van de publiceer instantie uitgevoerd. U kunt bijdragen door maximaal 25 douanewegen te vormen die voor controles worden overwogen.

Zie [ het Testen van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md) voor meer informatie.

### Klantenvalidaties

De kwaliteitsgate voor klantvalidaties is een plaatsaanduiding voor de eigen teststrategie en -inspanning van de klant, die worden uitgevoerd voordat de wijzigingen in de toepassing van de klant de implementatiepijplijnen van de AEM cloud bereiken.

Hier kunt u de gewenste gereedschappen en frameworks kiezen. In tegenstelling tot de tests van de klantenfunctie en van de douane UI, zijn er geen op AEM as a Cloud Service betrekking hebbende grenzen. Als dusdanig, adviseert de Adobe dat u lang-lopende functionele en UI het testen hier uitvoert.

Terwijl u om het even welk hulpmiddel en kader kunt kiezen, stelt de Adobe voor om op HTTP-Gebaseerde integratie en tests UI op de hulpmiddelen en het kader te richten die in de de testkwaliteitsgrafiek van de douane functionele en UI worden gebruikt. Bovendien, adviseert de Adobe het opnemen van [ Snelle Milieu&#39;s van de Ontwikkeling (RDE) ](/help/implementing/developing/introduction/rapid-development-environments.md) in uw lokale het testen strategie om AEM wolkenmilieu&#39;s dicht te weerspiegelen.

### Handmatig testen

De poort voor het handmatig testen van de kwaliteit is een plaatsaanduiding voor klanten die handmatig testen uitvoeren. Omdat AEM wolkenpijpleidingen geen handtest steunen, moet het in uw lokale teststrategie worden omvat.

Voor handmatige tests kan het nuttig zijn om te integreren met een extra AEM Cloud Service-ontwikkelomgeving.
