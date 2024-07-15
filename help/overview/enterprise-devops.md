---
title: Enterprise DevOps
description: Leer over de processen, de methodes, en de mededeling die worden vereist om plaatsing te verlichten en samenwerking te vereenvoudigen.
exl-id: c8da1fd7-fe3e-4c7b-8fe7-1f7faf02769c
source-git-commit: 1a4c5e618adaef99d82a00e1118d1a0f8536fc14
workflow-type: tm+mt
source-wordcount: '1009'
ht-degree: 46%

---

# Enterprise DevOps{#enterprise-devops}

DevOps omvat de processen, de methodes, en de mededeling die worden vereist om:

* Eenvoudige implementatie van uw software in verschillende omgevingen.
* Vereenvoudig de samenwerking tussen de ontwikkelings-, test- en implementatieteams.

DevOps heeft als doel om de onderstaande problemen te voorkomen:

* Handmatige fouten.
* Vergeten elementen; bijvoorbeeld bestanden, configuratiegegevens.
* Discrepanties; bijvoorbeeld tussen de lokale omgeving van een ontwikkelaar en andere omgevingen.

## Omgevingen {#environments}

Adobe Experience Manager (AEM) as a Cloud Service bestaat gewoonlijk uit meerdere omgevingen die op verschillende niveaus voor verschillende doeleinden worden gebruikt:

* [Ontwikkeling](#development)
* [Kwaliteitsborging](#quality-assurance)
* [Staging](#staging)
* [Productie](#production-author-and-publish)

>[!NOTE]
>
>De productieomgeving moet minstens één auteur en één publicatieomgeving hebben.
>
>Het wordt aanbevolen dat alle andere omgevingen ook bestaan uit een auteur- en publicatieomgeving, zodat de productieomgeving wordt weerspiegeld en vroege tests mogelijk zijn.

### Ontwikkeling {#development}

De ontwikkelaars zijn verantwoordelijk voor het ontwikkelen en aanpassen van het voorgestelde project (website, mobiele toepassingen, DAM-implementatie, enzovoort), met alle vereiste functionaliteit. Ontwikkelaars:

* ontwikkelen alle benodigde elementen en maken deze op maat, bijvoorbeeld sjablonen, componenten, workflows, applicaties
* realiseren het ontwerp
* ontwikkelen de noodzakelijke diensten en de manuscripten zodat kunt u de vereiste functionaliteit uitvoeren

De configuratie van het [ ontwikkelings ](/help/implementing/developing/introduction/development-guidelines.md) milieu kan van diverse factoren afhangen, hoewel het typisch uit is samengesteld:

* Een geïntegreerd ontwikkelingssysteem met versiecontrole om een geïntegreerde codebasis te verstrekken. Deze geïntegreerde codebasis wordt gebruikt om code van de individuele ontwikkelomgevingen samen te voegen en te consolideren die door elke ontwikkelaar worden gebruikt.
* Een persoonlijke omgeving voor elke ontwikkelaar; gewoonlijk op hun lokale machine. Met de juiste intervallen wordt de code gesynchroniseerd met het versiebeheersysteem

Afhankelijk van de schaal van uw systeem kan de ontwikkelomgeving beschikken over zowel auteur- als publicatie-instanties.

### Kwaliteitsborging {#quality-assurance}

Deze omgeving wordt door het team voor kwaliteitsborging gebruikt om uw nieuwe systeem volledig te testen, zowel ten aanzien van het ontwerp als de functionaliteit. De omgeving moet beschikken over auteur- en publicatieomgevingen met geschikte content. Ook moet het alle noodzakelijke services bieden om een volledige reeks tests mogelijk te maken.

### Staging {#staging}

De testomgeving moet een spiegel zijn van de productieomgeving - configuratie, code en inhoud:

* In deze omgeving worden scripts getest waarmee de daadwerkelijke implementatie wordt uitgevoerd.
* Het kan voor definitieve tests (ontwerp, functionaliteit, en interfaces) worden gebruikt alvorens aan de productiemilieu&#39;s op te stellen.
* Hoewel de stagingomgeving nooit identiek kan zijn aan de productieomgeving, moet deze zo dicht mogelijk bij de uiteindelijk gewenste niveaus voor prestaties en belasting liggen.

### Productie - Auteur en Publish {#production-author-and-publish}

Het productiemilieu bestaat uit de milieu&#39;s die [ auteur en ](/help/sites-cloud/authoring/author-publish.md) uw implementatie publiceren.

Een productieomgeving bestaat uit ten minste één auteurinstantie en één publicatie-instantie:

* Een [auteurinstantie](#author) voor de invoer van content.
* Een [publicatie-instantie](#publish) voor content die aan uw bezoekers/gebruikers ter beschikking wordt gesteld.

Afhankelijk van de schaal van het project, bestaat het vaak uit verscheidene auteurs, of uitgevers, of allebei. Op een lager niveau kan de repository ook naar meerdere instanties worden geclusterd.

#### Auteur {#author}

Gewoonlijk bevinden de instanties van de auteur zich achter de interne firewall. Deze interne firewall is de omgeving waarin u en uw collega&#39;s ontwerptaken uitvoeren, zoals:

* het volledige systeem beheren
* uw content invoeren
* de lay-out en het ontwerp van uw content configureren
* uw content activeren voor de publicatieomgeving

Content die is geactiveerd, wordt in een pakket geplaatst en naar de replicatiewachtrij van de auteuromgeving verzonden. Het replicatieproces verplaatst de content dan naar de publicatieomgeving.

Als u gegevens die in een publicatieomgeving zijn gegenereerd, wilt terugkeren naar de auteursomgeving, pollt een replicatielistener in de auteuromgeving de publicatieomgeving en haalt deze inhoud op uit de omgekeerde replicatieoutbox van de publicatieomgeving.

#### Publish {#publish}

Meestal bevindt een publicatie-omgeving zich in de DMZ (Demilitarisated Zone). In deze omgeving hebben bezoekers toegang tot uw inhoud (bijvoorbeeld via een website of in de vorm van een mobiele toepassing) en communiceren ze hiermee via het openbare programma of via uw intranet. Een publicatieomgeving:

* bevat content die is gerepliceerd vanuit de auteuromgeving
* stelt die content ter beschikking van de bezoekers
* slaat gebruikersgegevens op die door uw bezoekers worden gegenereerd, zoals opmerkingen of andere formulierverzendingen
* kan worden geconfigureerd zodat dergelijke gebruikersgegevens via een postvak UIT voor omgekeerde replicatie kan worden teruggestuurd naar de auteuromgeving

De publicatieomgeving genereert uw inhoud dynamisch in real-time en de inhoud kan voor elke gebruiker afzonderlijk worden aangepast.

## Codeverplaatsing {#code-movement}

Code altijd van beneden naar boven doorgeven:

* de code wordt aanvankelijk ontwikkeld op de lokale omgeving en vervolgens geïntegreerd in de ontwikkelomgevingen
* gevolgd door grondig testen op de QA-omgevingen
* vervolgens opnieuw getest op testomgevingen
* en pas hierna kan de code worden geïmplementeerd in de productieomgevingen

Doorgaans wordt de code (bijvoorbeeld aangepaste functionaliteit van webtoepassingen en ontwerpsjablonen) overgedragen door pakketten te exporteren en te importeren tussen de verschillende opslagruimten voor inhoud. Waar zinvol kan deze replicatie als automatisch proces worden geconfigureerd.

Projecten op AEM as a Cloud Service activeren vaak de implementatie van code:

* Automatisch: voor overdracht naar de ontwikkelings- en kwaliteitscontroleomgevingen.
* Handmatig: implementaties in de staging- en productieomgeving worden op een meer beheerste manier uitgevoerd, vaak handmatig; automatisering is echter mogelijk, indien nodig.

![Codeverplaatsing](assets/code-movement.png)

## Inhoud verplaatsen {#content-movement}

Content die is bedoeld voor productie, moet **altijd** worden geschreven op de productieauteurinstantie.

Inhoud mag geen code volgen die van lagere naar hogere omgevingen overgaat. Dat wil zeggen dat auteurs inhoud maken op lokale computers of lagere omgevingen en deze vervolgens naar de productieomgeving verplaatsen geen goede praktijk is. De reden is dat het fouten en inconsistenties kan introduceren.

Productiecontent moet van de productieomgeving naar de stagingomgeving worden verplaatst. Zo biedt de stagingomgeving een efficiënte en nauwkeurige testomgeving.

>[!NOTE]
>
>Deze methode houdt niet in dat de staging-inhoud voortdurend moet worden gesynchroniseerd met de productie. Regelmatige updates zijn voldoende, maar vooral voordat een nieuwe codering wordt getest. Inhoud in de QA- en ontwikkelomgevingen hoeft niet zo vaak te worden bijgewerkt. Het moet alleen een goede weergave zijn van de productie-inhoud.

Inhoud kan worden overgedragen:

* Tussen de verschillende omgevingen: door pakketten te exporteren en te importeren.
* Tussen verschillende instanties - door de inhoud rechtstreeks te repliceren (AEM as a Cloud Service-replicatie) (via een HTTP- of HTTPS-verbinding).

![Content verplaatsen](assets/content-movement.png)
