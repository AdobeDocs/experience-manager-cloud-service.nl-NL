---
title: Een AEM-connector implementeren
description: Een AEM-connector implementeren
translation-type: tm+mt
source-git-commit: bffc335fdafe6bf12a66bcd2f7aacf029fce567e
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 8%

---


Een AEM-connector implementeren
=============================

Hieronder vindt u nuttige verwijzingen voor het bouwen van [AEM-connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) en deze dienen te worden gelezen in combinatie met richtlijnen voor het [verzenden](submit.md) en [onderhouden](maintain.md) van connectors.

Een ontwikkelaarslicentie voor AEM kan worden verkregen via het [Adobe Exchange-programma](https://partners.adobe.com/exchangeprogram/experiencecloud).

Algemene integratiepatronen
---------------------------

AEM is een geavanceerde oplossing voor het beheer van webervaring en biedt vele potentiële integratiegebieden. Veelvoorkomende integratiepatronen zijn:

* Gegevens van een extern systeem naar AEM halen. U exporteert bijvoorbeeld contactgegevens van een CRM om deze beschikbaar te maken voor een groter publiek dat een AEM-website bezoekt.  De implementaties zouden de [Geplande Banen](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs)van Sling moeten gebruiken, die waarborgt dat de baan wordt uitgevoerd zelfs als de containers dalen. De code zou moeten worden ontworpen om te veronderstellen dat de baan potentieel meer dan eens kan worden teweeggebracht.
* Gegevens van AEM exporteren naar een extern systeem. Bijvoorbeeld instellingen voor abonnementen op nieuwsbrieven die op een AEM-website worden ingediend bij een CRM.
* Elementen ophalen van AEM. Bijvoorbeeld een extern inhoudsbeheersysteem (CMS) dat verwijst naar een element dat is opgeslagen in AEM Assets. Een ander voorbeeld is een PIM-systeem dat een koppeling maakt naar een afbeelding in AEM Assets.
* Elementen opslaan in de AEM-infrastructuur. Bijvoorbeeld, een systeem van het Beheer van het Middel van de Marketing van het Middel (MRM) dat een goedgekeurd activa in AEM Assets opslaat.
* Een aangepaste UI-component configureren en renderen. Stel bijvoorbeeld dat een auteur een video-component mag slepen en neerzetten en een specifieke video moet configureren om op de livesite af te spelen.
* Handelend op activa met een partnerdienst. Bijvoorbeeld het verzenden van middelen naar een videoplatform wanneer een pagina wordt gepubliceerd.
* Een site, pagina of element analyseren in de AEM-beheerconsole. Bijvoorbeeld: SEO-aanbevelingen doen voor een bestaande of niet-gepubliceerde pagina.
* Toegang op paginaniveau tot gebruikersgegevens die door een externe service worden onderhouden. Gebruik bijvoorbeeld demografische informatie om de site-ervaring aan te passen. Lees over ContextHub, een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens.
* Metagegevens van sitekopieën of middelen omzetten. Zie de [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) voor voorbeeldcode met behulp van het AEM Translation Framework, de voorkeursimplementatie van vertaalconnectors.


Nuttige documentatie
--------------------

Experience Manager als [documentatie](../overview/introduction.md) voor Cloud Servicen biedt waardevolle inzichten in de ontwikkeling van AEM. Hieronder volgen enkele specifieke technische onderwerpen en verwijzingen die u nuttig kunt vinden wanneer het uitvoeren van een schakelaar AEM:

* AEM-voorbeelden ( [AEM) van Adobe Consulting Services (ACS) voor code](http://adobe-consulting-services.github.io/acs-aem-samples/) met veel opmerkingen voor AEM-ontwikkelaars
* De verschillende documentatiekoppelingen in de sectie Gemeenschappelijke integratiepatronen van dit artikel

Communautaire middelen
--------------------

Naast de bovenstaande statische documentatie bieden Adobe en de AEM-community resources om een aansluiting op de markt te brengen:

* Het [AEM Forum](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) van de Gemeenschap van Adobe is een actieve plaats waar uw gelijken vragen stellen en antwoorden op vragen
* Voor bepaalde partnerniveaus zijn aanvullende technische bronnen van Adobe beschikbaar. Meer informatie over het [Adobe Exchange-programma](https://partners.adobe.com/exchangeprogram/experiencecloud).
* Als uw organisatie implementatiehulp nodig heeft, kunt u contact opnemen met het [Professionele services-team](http://www.adobe.com/nl/marketing-cloud/service-support/professional-consulting-training.html) van Adobe of [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) raadplegen voor een lijst van partners van Adobe over de hele wereld

Pakketstructuurregels
-----------------------

Om het rollen plaatsingen te steunen, heeft AEM als Cloud Service pakketten, waarvan schakelaars voorbeelden zijn, een strikte scheiding tussen &quot;onveranderlijk&quot;en &quot;veranderbare&quot;inhoud. Pakketten moeten zorgvuldig worden gescheiden tussen de volgende verpakkingseenheden:

* `/apps`
* `/content` and `/conf`

De schakelaars zouden aan deze verpakkingsrichtlijnen moeten houden, die in [dit artikel](/help/implementing/developing/introduction/aem-project-content-package-structure.md)worden beschreven. De bestaande schakelaars zouden moeten worden gerefactored om, eveneens in overeenstemming te zijn.

Daarnaast moet alleen Adobe code schrijven naar `/libs`, met klanten en partners waarin ze schrijven `/apps`.

De bestaande schakelaars kunnen ook refactored moeten zijn om het even welke configuratie te bewegen die eens `/etc` in andere hoogste niveauomslagen zoals `/conf`zou kunnen zijn geplaatst. Dit wordt beschreven in de [AEM documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

Het is raadzaam de meeste connectorcode onder te plaatsen `/apps/connectors/<vendor>` om een schone opslagplaats te promoten voor klanten die meerdere connectors hebben.

Configuraties van Cloud Servicen
-----------------------------

Één aspect van de schakelaarimplementatie is code die de configuratie van de schakelaar steunt. Met deze code wordt een kaart met de naam van de connector weergegeven onder Opties > Bewerkingen > Cloud Servicen. Wanneer geklikt, popt browser van de configuratie omhoog waar de klant de ouderomslag selecteert om de schakelaarconfiguratie te bevatten. De code van de schakelaar zou in een vorm met alle eigenschappen moeten resulteren die moeten worden gevormd, uiteindelijk het opslaan van de waarden in een configuratiemap onder `/conf`. Deze map kan later worden geselecteerd op het tabblad Sites-eigenschappen of Elementeigenschappen.


Contextbewuste configuraties
-----------------------------

[Contextbewuste configuraties](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) staan toe om configuratie over verschillende omslagen, met inbegrip van `/libs`, `/apps`, `/conf` en subfolders onder `/conf`. Het steunt overerving zodat kan een klant globale configuratie vormen terwijl het aanbrengen van specifieke veranderingen voor elke microsite. Omdat het mogelijk is om deze eigenschap voor de Configuraties van Cloud Servicen te hefboomwerking, zou de schakelaarcode configuratie moeten van verwijzingen voorzien gebruikend context-Aware Configuratie API in plaats van het van verwijzingen voorzien van een specifiek configuratieknooppunt.

Als de gewijzigde configuraties in de Schakelaar worden gebruikt, architect de Schakelaar om het omvatten van/het samenvoegen van om het even welke toekomstige updates aan schakelaar-verstrekte standaardconfiguraties met om het even welke klantenconfiguraties te behandelen. Herinner dat het veranderen van aangepaste (zoals in veranderd door de klant) inhoud of configuratie zonder klantenwaarschuwing en toestemming (of tot onverwacht gedrag) met hun Schakelaar kan breken.

Aanbevolen werkwijzen voor codering
----------------------

Aangezien AEM als Cloud Service een inheemse oplossing van de Wolk is, zijn er sommige richtlijnen die de codestrategieën van een schakelaar kunnen beïnvloeden. Zie [AEM als de Richtlijnen](/help/implementing/developing/introduction/development-guidelines.md) van de Ontwikkeling van de Cloud Service voor meer informatie.

De AEM-connector testen
-------------------------

Nieuwe schakelaars zouden moeten worden gecreeerd (of bestaande schakelaars gewijzigd) gebruikend lokale milieu ontwikkelingstechnieken. Het Team van de Partner zal partners ISV van een zandbakmilieu voorzien waar zij hun Schakelaar AEM aan een vanilletoepassing kunnen opstellen om ervoor te zorgen dat het werkt.
