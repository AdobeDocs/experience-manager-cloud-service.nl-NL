---
title: Meer informatie over inhoud zonder kop en hoe u kunt lokaliseren in AEM
description: Ontdek headless-concepten, hoe ze in kaart worden gebracht aan AEM en de theorie van AEM lokalisatie.
source-git-commit: 22ca7c01bfddb407c119de7d9a4d105941772664
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 0%

---

# Meer informatie over inhoud zonder kop en hoe u kunt lokaliseren in AEM {#learn-about}

Ontdek headless-concepten, hoe ze in kaart worden gebracht aan AEM en de theorie van AEM lokalisatie.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de inhoud zonder kop, hoe AEM koploze inhoud ondersteunt en hoe dergelijke inhoud kan worden gelokaliseerd. Na het lezen moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en lokalisatie.

## Volledige levering van inhoud {#full-stack}

Sinds de opkomst van gebruiksvriendelijke, grootschalige contentbeheersystemen (CMS&#39;s) hebben organisaties deze als centrale locatie gebruikt voor het beheer van berichten, branding en communicatie. Het gebruik van het CMS als centraal punt voor het beheer van ervaringen heeft de efficiëntie verbeterd doordat taken in verschillende systemen niet hoeven te worden gedupliceerd.

![De klassieke full-stack CMS](/help/journey-headless/developer/assets/full-stack.png)

In een volledig-stapel CMS, is alle functionaliteit voor het manipuleren van inhoud in CMS. De functies van het systeem bestaan uit verschillende onderdelen van de CMS-stapel. De full-stack oplossing heeft veel voordelen.

* Er is één systeem om te onderhouden.
* Inhoud wordt centraal beheerd.
* Alle diensten van het systeem zijn geïntegreerd.
* Inhoud schrijven is naadloos.

Als dus een nieuw kanaal moet worden toegevoegd of ondersteuning voor nieuwe soorten ervaringen is vereist, kunnen een (of meer) nieuwe componenten in de stapel worden ingevoegd en is er slechts één plaats om wijzigingen aan te brengen.

![Een nieuw kanaal toevoegen aan de stapel](/help/journey-headless/developer/assets/adding-channel.png)

De complexiteit van de afhankelijkheden in de stapel wordt snel zichtbaar naarmate andere items in de stapel moeten worden aangepast aan de wijzigingen.

## De kop in de kop {#the-head}

Het hoofd van een systeem is doorgaans de uitvoerrenderer van dat systeem, meestal in de vorm van een grafische interface of andere grafische uitvoer.

Als we het hebben over een CMS zonder kop, beheert het CMS de inhoud en blijft het leveren aan consumenten. Door de **content** echter alleen op gestandaardiseerde wijze te leveren, laat een CMS zonder kop de uiteindelijke uitvoerrendering weg en laat de **presentatie** van de inhoud over aan de verbruikende service.

![CMS zonder hoofd](/help/journey-headless/developer/assets/headless-cms.png)

De verbruikende services, of het nu gaat om AIR, een webshop, mobiele ervaring, progressieve webapps (PWA), enz., nemen inhoud van het CMS zonder kop in en bieden hun eigen rendering. Ze zorgen ervoor dat ze hun eigen hoofd geven aan je inhoud.

Het weglaten van het hoofd vereenvoudigt CMS door ingewikkeldheid te verwijderen. Hierdoor wordt ook de verantwoordelijkheid voor het renderen van de inhoud verplaatst naar de diensten die de inhoud echt nodig hebben en die vaak beter geschikt zijn voor dergelijke rendering.

## Inhoud zonder hoofd lokaliseren in AEM {#localizing-in-aem}

Naast robuuste tools voor het maken, beheren en leveren van traditionele webpagina&#39;s op een volledig stapelbare manier, biedt AEM ook de mogelijkheid om op zichzelf staande selecties van inhoud te maken en deze zonder problemen te bedienen.

Dankzij de kracht van AEM kan de inhoud zonder kop, volledig of in beide modellen tegelijk worden geleverd. Voor de lokalisatiespecialist kan dezelfde set lokalisatieprogramma&#39;s worden toegepast op beide typen inhoud, zodat u een uniforme aanpak hebt voor het vertalen van uw inhoud.

## Volgende functies {#what-is-next}

Hartelijk dank voor de start van uw AEM meesleploze lokalisatietraject! Nu u dit document leest, moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Wees vertrouwd met de manier waarop AEM ondersteuning biedt voor headless en lokalisatie.

Voortbouwen op deze kennis en doorgaan met uw AEM ongekende lokalisatietraject door het document [Aan de slag te gaan met AEM hoofdloze lokalisatie](getting-started.md). Hierin hebt u een overzicht van hoe AEM inhoud zonder kop beheert en de lokalisatieprogramma&#39;s van het document kent.

## Aanvullende bronnen {#additional-resources}

Hoewel u kunt doorgaan naar het volgende gedeelte van de reis zonder kop door het document [Aan de slag met AEM hoofdloze lokalisatie te bekijken,](getting-started.md) zijn de volgende aanvullende, optionele bronnen die een diepere duw doen in sommige concepten die in dit document worden genoemd, maar die niet nodig zijn om verder te gaan op de tocht zonder kop.

* [MSM en vertaling](/help/sites-cloud/administering/msm-and-translation.md) : de details van AEM beheer voor meerdere sites en hoe het werkt met de vertaalhulpmiddelen
