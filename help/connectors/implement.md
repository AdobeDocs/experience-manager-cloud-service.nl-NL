---
title: Een AEM-connector implementeren
description: Een AEM-connector implementeren
translation-type: tm+mt
source-git-commit: 69756d6831678151b0e8eb73db81113d49f17447
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 8%

---


Een AEM-connector implementeren
=============================

Hieronder vindt u nuttige verwijzingen voor het bouwen van [AEM-connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) en deze dienen te worden gelezen in combinatie met richtlijnen voor het [verzenden](submit.md) en [onderhouden](maintain.md) van connectors.

Merk op dat een vergunning van de Ontwikkelaar voor AEM door [het Programma van de Uitwisseling van de Adobe](https://partners.adobe.com/exchangeprogram/experiencecloud) kan worden verkregen.

Algemene integratiepatronen
---------------------------

AEM is een geavanceerde oplossing voor het beheer van webervaring en biedt vele potentiële integratiegebieden. Veelvoorkomende integratiepatronen zijn:

* Gegevens van een extern systeem naar AEM halen. U kunt bijvoorbeeld contactgegevens van een CRM exporteren om deze beschikbaar te maken voor een breder publiek dat een website met een AEM bezoekt.  Implementaties moeten gebruikmaken van de [Geplande taken](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs), die garandeert dat de taak wordt uitgevoerd, zelfs als de containers omlaag gaan. De code zou moeten worden ontworpen om te veronderstellen dat de baan potentieel meer dan eens kan worden teweeggebracht.
* Gegevens exporteren van AEM naar een extern systeem. Bijvoorbeeld instellingen voor abonnementen op nieuwsbrieven die op een door AEM aangedreven website worden ingediend bij een CRM.
* Elementen ophalen van AEM. Bijvoorbeeld een extern inhoudsbeheersysteem (CMS) dat verwijst naar een element dat is opgeslagen in AEM Assets. Een ander voorbeeld is een PIM-systeem dat een koppeling maakt naar een afbeelding in AEM Assets.
* Elementen opslaan in de AEM-infrastructuur. Bijvoorbeeld, een systeem van het Beheer van het Middel van de Marketing (MRM) dat een goedgekeurd activa in AEM Assets opslaat.
* Een aangepaste UI-component configureren en renderen. Stel bijvoorbeeld dat een auteur een video-component mag slepen en neerzetten en een specifieke video moet configureren om op de livesite af te spelen.
* Handelend op activa met een partnerdienst. Bijvoorbeeld het verzenden van middelen naar een videoplatform wanneer een pagina wordt gepubliceerd.
* Een site, pagina of element analyseren in de AEM-beheerconsole. Bijvoorbeeld: SEO-aanbevelingen doen voor een bestaande of niet-gepubliceerde pagina.
* Toegang op paginaniveau tot gebruikersgegevens die door een externe service worden onderhouden. Gebruik bijvoorbeeld demografische informatie om de site-ervaring aan te passen. Lees over ContextHub, een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens.
* Metagegevens van sitekopieën of middelen omzetten. Zie [AEM de Schakelaar van de Bootstrap van het Kader van de Vertaling ](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) voor steekproefcode gebruikend het AEM Vertaalkader, dat de aangewezen implementatie van vertaalschakelaars is.


Nuttige documentatie
--------------------

Experience Manager als Cloud Service [documentatie](../overview/introduction.md) verstrekt waardevolle inzichten in het ontwikkelen in AEM. Hieronder volgen enkele specifieke technische onderwerpen en verwijzingen die u nuttig kunt vinden wanneer het uitvoeren van een AEM schakelaar:

* Adobe Consulting Services (ACS) [AEM Samples](http://adobe-consulting-services.github.io/acs-aem-samples/) voor code met goede opmerkingen om AEM ontwikkelaars te helpen opleiden
* De verschillende documentatiekoppelingen in de sectie Gemeenschappelijke integratiepatronen van dit artikel

Communautaire middelen
--------------------

Naast de statische documentatie hierboven, bieden Adobe en de AEM gemeenschap middelen om een schakelaar aan markt te helpen brengen:

* Het [AEM Forum](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) van de Gemeenschap van de Adobe is een actieve plaats waar uw gelijken vragen stellen en antwoorden op vragen
* De extra technische middelen van Adobe zijn beschikbaar aan bepaalde partnerniveaus. Meer informatie over het [Adobe Exchange-programma](https://partners.adobe.com/exchangeprogram/experiencecloud).
* Als uw organisatie implementatiehulp nodig heeft, kunt u contact opnemen met het [Professionele services-team](http://www.adobe.com/nl/marketing-cloud/service-support/professional-consulting-training.html) van Adobe of [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) raadplegen voor een lijst van partners van Adobe over de hele wereld

Pakketstructuurregels
-----------------------

Om het rollen plaatsingen te steunen, hebben AEM als Cloud Service pakketten, waarvan schakelaars voorbeelden zijn, een strikte scheiding tussen &quot;onveranderlijke&quot;en &quot;veranderbare&quot;inhoud. Pakketten moeten zorgvuldig worden gescheiden tussen de volgende verpakkingseenheden:

* `/apps`
* `/content` and `/conf`

De schakelaars zouden aan deze verpakkingsrichtlijnen moeten houden, die in [dit artikel](/help/implementing/developing/introduction/aem-project-content-package-structure.md) worden beschreven. De bestaande schakelaars zouden moeten worden gerefactored om, eveneens in overeenstemming te zijn.

Bovendien zou slechts Adobe code in `/libs`, met klanten en partners moeten schrijven die in `/apps` schrijven.

Bestaande connectors moeten mogelijk ook worden vernieuwd om elke configuratie te verplaatsen die ooit `/etc` in andere mappen op het hoogste niveau is geplaatst, zoals `/conf`. Dit wordt beschreven in de [AEM documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html).

Het is raadzaam het grootste deel van de verbindingscode onder `/apps/connectors/<vendor>` te plaatsen om een schone opslagplaats te bevorderen voor klanten die verscheidene schakelaars hebben.

Configuraties van Cloud Services
-----------------------------

Één aspect van de schakelaarimplementatie is code die de configuratie van de schakelaar steunt. Met deze code wordt een kaart met de naam van de connector weergegeven onder Opties > Bewerkingen > Cloud Services. Wanneer geklikt, [configuratiesbrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) duikt op waar de klant de ouderomslag selecteert om de schakelaarconfiguratie te bevatten. De code van de schakelaar zou in een vorm met alle eigenschappen moeten resulteren die moeten worden gevormd, uiteindelijk het opslaan van de waarden in een configuratiemap onder `/conf`. Deze map kan later worden geselecteerd op het tabblad Sites-eigenschappen of Elementeigenschappen.


Contextbewuste configuraties
-----------------------------

[Contextbewuste ](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) configuratie verlaat aan laagconfiguratie over verschillende omslagen, met inbegrip van  `/libs`,  `/apps`en subfolders onder  `/conf`   `/conf`. Het steunt overerving zodat kan een klant globale configuratie vormen terwijl het aanbrengen van specifieke veranderingen voor elke microsite. Omdat het mogelijk is om deze eigenschap voor de Configuraties van Cloud Services te hefboomwerking, zou de schakelaarcode configuratie moeten van verwijzingen voorzien gebruikend context-Aware Configuratie API in plaats van het van verwijzingen voorzien van een specifiek configuratieknooppunt.

Als de gewijzigde configuraties in de Schakelaar worden gebruikt, architect de Schakelaar om het omvatten van/het samenvoegen van om het even welke toekomstige updates aan schakelaar-verstrekte standaardconfiguraties met om het even welke klantenconfiguraties te behandelen. Herinner dat het veranderen van aangepaste (zoals in veranderd door de klant) inhoud of configuratie zonder klantenwaarschuwing en toestemming (of tot onverwacht gedrag) met hun Schakelaar kan breken.

Aanbevolen werkwijzen voor codering
----------------------

Aangezien AEM als Cloud Service een inheemse oplossing van de Wolk is, zijn er sommige richtlijnen die de codestrategieën van een schakelaar kunnen beïnvloeden. Zie [AEM als Richtlijnen voor de Ontwikkeling van de Cloud Service](/help/implementing/developing/introduction/development-guidelines.md) voor meer informatie.

De AEM-aansluiting testen
-------------------------

Nieuwe schakelaars zouden moeten worden gecreeerd (of bestaande schakelaars gewijzigd) gebruikend lokale milieu ontwikkelingstechnieken. Het Team van de Partner zal partners ISV van een zandbakmilieu voorzien waar zij hun AEMSchakelaar aan een vanilletoepassing kunnen opstellen om ervoor te zorgen dat het werkt.
