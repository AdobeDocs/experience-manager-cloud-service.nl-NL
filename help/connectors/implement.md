---
title: Implementeren van een AEM-aansluiting
description: Meer informatie over connectoren, wat ze kunnen doen en hoe u deze waardevolle tools implementeert in Experience Manager.
exl-id: 70024424-8c52-493e-bbc9-03d238b8a5f5
feature: Operations
role: Admin
source-git-commit: a9cec66cf518a19a5a6152d431a052369b5b503a
workflow-type: tm+mt
source-wordcount: '922'
ht-degree: 4%

---


Implementeren van een AEM-aansluiting
=============================

Geleverd hieronder zijn nuttige verwijzingen voor de bouw AEM Schakelaars en zouden met begeleiding moeten worden gelezen bij [ het voorleggen ](submit.md) en [ het handhaven van ](maintain.md) schakelaars.

Een vergunning van de Ontwikkelaar voor AEM kan door het [ Programma van de Adobe Exchange ](https://partners.adobe.com/technologyprogram/experiencecloud.html) worden verkregen.

Algemene integratiepatronen
---------------------------

AEM is een geavanceerde oplossing voor het beheer van webervaring en biedt vele potentiële integratiegebieden. Veelvoorkomende integratiepatronen zijn:

* Gegevens van een extern systeem naar AEM halen. U kunt bijvoorbeeld contactgegevens van een CRM exporteren om deze beschikbaar te maken voor een breder publiek dat een website met een AEM bezoekt.  De uitvoeringen zouden het Verschuiven [ Geplande Banen ](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs) moeten gebruiken, die garandeert dat de baan wordt uitgevoerd zelfs als de containers dalen. De code zou moeten worden ontworpen om te veronderstellen dat de baan potentieel meer dan eens kan worden teweeggebracht.
* Gegevens exporteren van AEM naar een extern systeem. Abonnementsinstellingen voor nieuwsbrieven worden bijvoorbeeld via een op AEM gebaseerde website naar een CRM verzonden.
* Elementen ophalen van AEM. Bijvoorbeeld een extern inhoudsbeheersysteem (CMS) dat verwijst naar een element dat is opgeslagen in AEM Assets. Een ander voorbeeld is een PIM-systeem dat een koppeling maakt naar een afbeelding in AEM Assets.
* Elementen opslaan in de AEM. Bijvoorbeeld, een systeem van het Beheer van het Middel van de Marketing (MRM) dat een goedgekeurd activa in AEM Assets opslaat.
* Een aangepaste UI-component configureren en renderen. Stel bijvoorbeeld dat een auteur een video-component mag slepen en neerzetten en een specifieke video moet configureren om op de livesite af te spelen.
* Handelend op activa met een partnerdienst. Bijvoorbeeld het verzenden van middelen naar een videoplatform wanneer een pagina wordt gepubliceerd.
* Een site, pagina of element in de Admin Console AEM analyseren. Bijvoorbeeld: SEO-aanbevelingen doen voor een bestaande of niet-gepubliceerde pagina.
* Toegang op paginaniveau tot gebruikersgegevens die door een externe service worden onderhouden. Gebruik bijvoorbeeld demografische informatie om de site-ervaring aan te passen. Lees over ContextHub, een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens.
* Metagegevens van sitekopieën of middelen omzetten. Zie [ AEM de Schakelaar van de Bootstrap van het Kader van de Vertaling ](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) voor steekproefcode gebruikend het Kader van de Vertaling van de AEM, die de aangewezen implementatie van vertaalschakelaars is.


Nuttige documentatie
--------------------

De as a Cloud Service Experience Manager [ documentatie ](../overview/introduction.md) verstrekt waardevolle inzichten in het ontwikkelen in AEM. Hieronder volgen enkele specifieke technische onderwerpen en verwijzingen die u nuttig kunt vinden wanneer het uitvoeren van een AEM schakelaar:

* De Diensten van Adobe Consulting (ACS) [ AEM Steekproeven ](https://adobe-consulting-services.github.io/acs-aem-samples/) voor goed-becommentarieerde code helpen AEM ontwikkelaars onderwijzen
* De verschillende documentatiekoppelingen in de sectie Gemeenschappelijke integratiepatronen van dit artikel

Communautaire middelen
--------------------

Naast de bovenstaande statische documentatie bieden de Adobe en de AEM gemeenschap middelen om een aansluiting op de markt te brengen:

* Het forum van de Gemeenschap van de Adobe [ AEM ](https://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) is een actieve plaats waar uw edelen vragen stellen en antwoorden aan vragen
* De extra technische middelen van de Adobe zijn beschikbaar aan bepaalde partnerniveaus. Leer meer over het [ Programma van de Adobe Exchange ](https://partners.adobe.com/technologyprogram/experiencecloud.html).
* Als uw organisatie implementatiehulp nodig heeft, kunt u contact opnemen met het [Professionele services-team](https://solutionpartners.adobe.com/s/directory) van Adobe of [Solution Partner Finder](https://solutionpartners.adobe.com/s/directory/) raadplegen voor een lijst van partners van Adobe over de hele wereld

Pakketstructuurregels
-----------------------

Om het rollen plaatsingen, AEM as a Cloud Service pakketten-zulke als schakelaars-handhaven een strikte scheiding tussen &quot;onveranderlijk&quot;en &quot;veranderbare&quot;inhoud te vergemakkelijken. De verpakkingen moeten duidelijk zijn ingedeeld en omvatten:

* `/apps`
* `/content` en `/conf`

De schakelaars zouden aan deze verpakkingsrichtlijnen moeten houden, die onder [ worden beschreven AEM de Structuur van het Project ](/help/implementing/developing/introduction/aem-project-content-package-structure.md). De bestaande schakelaars zouden moeten worden gerefactored om, eveneens in overeenstemming te zijn.

Daarnaast moet alleen Adobe code schrijven naar `/libs` , met klanten en partners die schrijven naar `/apps` .

Het kan ook zijn dat bestaande connectors opnieuw moeten worden bekeken om een configuratie te verplaatsen die ooit `/etc` in andere mappen op het hoogste niveau is geplaatst, zoals `/conf` . Deze herstructurering werd gedaan als deel van AEM 6.5 en wordt beschreven in [ AEM 6.5 documentatie ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/restructuring/repository-restructuring).

Adobe raadt u aan de meeste connectorcode onder `/apps/connectors/<vendor>` te plaatsen om een schone opslagplaats te behouden, vooral voor klanten die meerdere connectors gebruiken.

Configuraties van Cloud Servicen
-----------------------------

Één aspect van de schakelaarimplementatie is de code die de configuratie van de schakelaar steunt. Met deze code wordt een kaart met de naam van de connector weergegeven onder Opties > Bewerkingen > Cloud Servicen. Wanneer geklikt, pop a [ configuratiebrowser ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser) op waar de klant de ouderomslag selecteert om de schakelaarconfiguratie te bevatten. De code van de schakelaar zou in een vorm met alle eigenschappen moeten resulteren die moeten worden gevormd, die uiteindelijk de waarden in een configuratiemap onder `/conf` opslaan. Deze map kan later worden geselecteerd op het tabblad Sites-eigenschappen of Assets-eigenschappen.


Contextbewuste configuraties
-----------------------------

[ context-Aware Configuraties ](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) laat u configuratie over verschillende omslagen, met inbegrip van `/libs`, `/apps`, `/conf` en subfolders onder `/conf` in lagen. Het steunt overerving zodat kan een klant globale configuratie vormen terwijl het aanbrengen van specifieke veranderingen voor elke microsite. Omdat het mogelijk is om deze eigenschap voor de Configuraties van Cloud Servicen te gebruiken, zou de schakelaarcode configuratie moeten van verwijzingen voorzien gebruikend context-Aware Configuratie API in plaats van het van verwijzingen voorzien van een specifieke configuratieknoop.

Als de gewijzigde configuraties in de Schakelaar worden gebruikt, architect de Schakelaar om het omvatten van/het samenvoegen van om het even welke toekomstige updates aan schakelaar-verstrekte standaardconfiguraties met om het even welke klantenconfiguraties te behandelen. Houd in mening dat het wijzigen van klant-aangepaste inhoud of configuraties zonder voorafgaande kennisgeving en toestemming onverwacht gedrag in hun Schakelaar kan verstoren of veroorzaken.

Aanbevolen werkwijzen voor codering
----------------------

Omdat AEM as a Cloud Service een oplossing in de cloud is, zijn er enkele richtlijnen die de codestrategieën van een connector kunnen beïnvloeden. Zie [ de Richtlijnen van de Ontwikkeling van AEM as a Cloud Service ](/help/implementing/developing/introduction/development-guidelines.md) voor meer details.

De AEM-aansluiting testen
-------------------------

Nieuwe schakelaars zouden moeten worden gecreeerd (of bestaande schakelaars gewijzigd) gebruikend lokale milieu ontwikkelingstechnieken. Het Team van de Partner voorziet partners ISV van een zandbakmilieu waar zij hun AEMSchakelaar aan een vanilletoepassing kunnen opstellen om ervoor te zorgen dat het werkt.
