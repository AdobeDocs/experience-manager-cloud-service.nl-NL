---
title: Implementeren van een AEM-aansluiting
description: Meer informatie over connectoren, wat ze kunnen doen en hoe u deze waardevolle tools implementeert in Experience Manager.
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
feature: Operations
role: Admin
source-git-commit: 0e328d013f3c5b9b965010e4e410b6fda2de042e
workflow-type: tm+mt
source-wordcount: '935'
ht-degree: 7%

---


Implementeren van een AEM-aansluiting
=============================

Hieronder vindt u nuttige verwijzingen voor het bouwen van [AEM-connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) en deze dienen te worden gelezen in combinatie met richtlijnen voor het [verzenden](submit.md) en [onderhouden](maintain.md) van connectors.

Een ontwikkelaarslicentie voor AEM kan worden verkregen via de [Adobe Exchange](https://partners.adobe.com/exchangeprogram/experiencecloud).

Algemene integratiepatronen
---------------------------

AEM is een geavanceerde oplossing voor het beheer van webervaring en biedt vele potentiële integratiegebieden. Veelvoorkomende integratiepatronen zijn:

* Gegevens van een extern systeem naar AEM halen. U kunt bijvoorbeeld contactgegevens van een CRM exporteren om deze beschikbaar te maken voor een breder publiek dat een website met een AEM bezoekt.  Implementaties moeten gebruikmaken van de [Geplande taken](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs), die garandeert dat de taak ook wordt uitgevoerd als de containers omlaag gaan. De code zou moeten worden ontworpen om te veronderstellen dat de baan potentieel meer dan eens kan worden teweeggebracht.
* Gegevens exporteren van AEM naar een extern systeem. Bijvoorbeeld instellingen voor abonnementen op nieuwsbrieven die op een door AEM aangedreven website worden ingediend bij een CRM.
* Elementen ophalen van AEM. Bijvoorbeeld een extern inhoudsbeheersysteem (CMS) dat verwijst naar een element dat is opgeslagen in AEM Assets. Een ander voorbeeld is een PIM-systeem dat een koppeling maakt naar een afbeelding in AEM Assets.
* Elementen opslaan in de AEM. Bijvoorbeeld, een systeem van het Beheer van het Middel van de Marketing (MRM) dat een goedgekeurd activa in AEM Assets opslaat.
* Een aangepaste UI-component configureren en renderen. Stel bijvoorbeeld dat een auteur een video-component mag slepen en neerzetten en een specifieke video moet configureren om op de livesite af te spelen.
* Handelend op activa met een partnerdienst. Bijvoorbeeld het verzenden van middelen naar een videoplatform wanneer een pagina wordt gepubliceerd.
* Een site, pagina of element analyseren in de AEM-beheerconsole. Bijvoorbeeld: SEO-aanbevelingen doen voor een bestaande of niet-gepubliceerde pagina.
* Toegang op paginaniveau tot gebruikersgegevens die door een externe service worden onderhouden. Gebruik bijvoorbeeld demografische informatie om de site-ervaring aan te passen. Lees over ContextHub, een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens.
* Metagegevens van sitekopieën of middelen omzetten. Zie de [AEM Bootstrap-aansluiting voor vertaalframework](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) voor voorbeeldcode die het AEM Vertaalkader gebruikt, dat de aangewezen implementatie van vertaalschakelaars is.


Nuttige documentatie
--------------------

Experience Manager as a Cloud Service [documentatie](../overview/introduction.md) biedt waardevolle inzichten in de ontwikkeling in AEM. Hieronder volgen enkele specifieke technische onderwerpen en verwijzingen die u nuttig kunt vinden wanneer het uitvoeren van een AEM schakelaar:

* Adobe Consulting Services (ACS) [AEM](https://adobe-consulting-services.github.io/acs-aem-samples/) voor code met goede opmerkingen om AEM ontwikkelaars te helpen opleiden
* De verschillende documentatiekoppelingen in de sectie Gemeenschappelijke integratiepatronen van dit artikel

Communautaire middelen
--------------------

Naast de bovenstaande statische documentatie bieden de Adobe en de AEM gemeenschap middelen om een aansluiting op de markt te brengen:

* De Adobe Gemeenschap [AEM](https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) is een actieve site waarop uw collega&#39;s vragen stellen en antwoorden op vragen
* De extra technische middelen van de Adobe zijn beschikbaar aan bepaalde partnerniveaus. Meer informatie over de [Adobe Exchange](https://partners.adobe.com/exchangeprogram/experiencecloud).
* Als uw organisatie implementatiehulp nodig heeft, kunt u contact opnemen met het [Professionele services-team](https://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) van Adobe of [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) raadplegen voor een lijst van partners van Adobe over de hele wereld

Pakketstructuurregels
-----------------------

Om het rollen plaatsingen te steunen, hebben AEM as a Cloud Service pakketten, waarvan schakelaars voorbeelden zijn, een strikte scheiding tussen &quot;onveranderlijke&quot;en &quot;veranderbare&quot;inhoud. Pakketten moeten zorgvuldig worden gescheiden tussen de volgende verpakkingseenheden:

* `/apps`
* `/content` en `/conf`

De aansluitingen moeten zich houden aan deze verpakkingsrichtlijnen, die worden beschreven in [dit artikel](/help/implementing/developing/introduction/aem-project-content-package-structure.md). De bestaande schakelaars zouden moeten worden gerefactored om, eveneens in overeenstemming te zijn.

Daarnaast moet alleen Adobe code schrijven naar `/libs`, met klanten en partners die in schrijven `/apps`.

De bestaande schakelaars kunnen ook refactoring moeten zijn om het even welke configuratie te bewegen die eens zou kunnen zijn geplaatst `/etc` in andere mappen op het hoogste niveau, zoals `/conf`. Deze herstructurering werd uitgevoerd als onderdeel van AEM 6.5 en wordt beschreven in de [AEM 6.5-documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html).

Aanbevolen wordt de meeste verbindingscode onder te plaatsen `/apps/connectors/<vendor>` het bevorderen van een schone opslagplaats voor klanten die verschillende connectoren hebben.

Configuraties van Cloud Servicen
-----------------------------

Één aspect van de schakelaarimplementatie is code die de configuratie van de schakelaar steunt. Met deze code wordt een kaart met de naam van de connector weergegeven onder Opties > Bewerkingen > Cloud Servicen. Als erop wordt geklikt, wordt een [configuratievenster](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) verschijnt op de plaats waar de klant de ouderomslag selecteert om de schakelaarconfiguratie te bevatten. De code van de schakelaar zou in een vorm met alle eigenschappen moeten resulteren die moeten worden gevormd, uiteindelijk het opslaan van de waarden in een configuratiemap onder `/conf`. Deze map kan later worden geselecteerd op het tabblad Sites-eigenschappen of Elementeigenschappen.


Contextbewuste configuraties
-----------------------------

[Contextbewuste configuraties](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) staat toe aan laagconfiguratie over verschillende omslagen, met inbegrip van `/libs`, `/apps`, `/conf` en submappen onder `/conf`. Het steunt overerving zodat kan een klant globale configuratie vormen terwijl het aanbrengen van specifieke veranderingen voor elke microsite. Omdat het mogelijk is om deze eigenschap voor de Configuraties van Cloud Servicen te gebruiken, zou de schakelaarcode configuratie moeten van verwijzingen voorzien gebruikend context-Aware Configuratie API in plaats van het van verwijzingen voorzien van een specifieke configuratieknoop.

Als de gewijzigde configuraties in de Schakelaar worden gebruikt, architect de Schakelaar om het omvatten van/het samenvoegen van om het even welke toekomstige updates aan schakelaar-verstrekte standaardconfiguraties met om het even welke klantenconfiguraties te behandelen. Herinner dat het veranderen van aangepaste (zoals in veranderd door de klant) inhoud of configuratie zonder klantenwaarschuwing en toestemming (of tot onverwacht gedrag) met hun Schakelaar kan breken.

Aanbevolen werkwijzen voor codering
----------------------

Aangezien AEM as a Cloud Service een Cloud-inheemse oplossing is, zijn er sommige richtlijnen die de codestrategieën van een schakelaar kunnen beïnvloeden. Zie [as a Cloud Service ontwikkelingsrichtsnoeren AEM](/help/implementing/developing/introduction/development-guidelines.md) voor meer informatie .

De AEM-aansluiting testen
-------------------------

Nieuwe schakelaars zouden moeten worden gecreeerd (of bestaande schakelaars gewijzigd) gebruikend lokale milieu ontwikkelingstechnieken. Het Team van de Partner zal partners ISV van een zandbakmilieu voorzien waar zij hun AEMSchakelaar aan een vanilletoepassing kunnen opstellen om ervoor te zorgen dat het werkt.
