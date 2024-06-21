---
title: Aanpassing en doelgerichtheid van inhoud
description: Leer hoe u gepersonaliseerde, gerichte inhoud met AEM kunt creëren
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '1054'
ht-degree: 0%

---


# Aanpassing en doelgerichtheid van inhoud {#personalization-and-content-targeting}

De personalisering van de webinhoud die u aan klanten verstrekt, betekent het aanpassen van die ervaringen aan hun belangen en behoeften. Je kan dit doen op basis van de informatie die je over hen hebt, bijvoorbeeld: samenvattend winkelen, leeftijd, geslacht, geografie, enzovoort.

Met Adobe Experience Manager as a Cloud Service (AEM) kunt u een selectie van inhoud maken en vervolgens opgeven welk publiek (groepen eindgebruikers) elke afzonderlijke ervaring ziet. Dit betekent dat u zich richt op uw persoonlijke ervaringen op een bepaald publiek.

Wanneer uw lezer online is, controleert uw doelprogramma de informatie die beschikbaar is over de eindgebruiker en vergelijkt deze met de ervaringsdefinities. De motor *&quot;besluit&quot;* welke persoonlijke ervaring moet worden weergegeven.

AEM biedt een kader voor instrumenten voor:

* Het ontwerpen van gerichte inhoud, geschikt voor een waaier van publiek, afhankelijk van de beschikbare klanteninformatie.
* Het bepalen van de regels die worden gebruikt om de bekende gebruikersinformatie tegen een publieksdefinitie op te lossen.
* Het vormen van uw pagina&#39;s om gerichte gepersonaliseerde ervaringen voor te stellen; om de specifieke inhoud terug te geven toepasselijk op de huidige eindgebruiker.

In het volgende overzicht worden enkele termen beschreven die worden gebruikt voor personalisatie in AEM as a Cloud Service, gevolgd door een aanbevolen handelingsvolgorde.

## Ervaring {#experience}

Een ervaring is inhoud die u aan uw eindgebruikers wilt worden getoond.

## Persoonlijke ervaring {#personalized-experience}

Een gepersonaliseerde ervaring is een ervaring die aan een beperkt publiek wordt getoond. Het publiek wordt door u gedefinieerd en de inhoud wordt alleen weergegeven wanneer de informatie over de huidige eindgebruiker overeenkomt met die publieksdefinitie.

Wanneer u pagina&#39;s maakt, definieert u meerdere ervaringen, waarbij elke ervaring wordt omgezet in een of meer doelgroepen. Als geen publiek wordt opgelost, dan wordt de standaardervaring getoond.

### Voorstel {#offer}

Een aanbieding is een persoonlijke ervaring, die vaak voor een beperkte periode beschikbaar is.

Een pagina van een voorbeeldwebsite kan bijvoorbeeld aanbiedingen gebruiken als de laserafbeelding die boven aan de pagina wordt weergegeven. Een persoon boven de 30 en een persoon onder de 30 kunnen verschillende aanbiedingen zien als het ervaringsteken.

## Publiek {#audience}

Een publiek is een groep eindgebruikers die u wilt aanwijzen met gepersonaliseerde inhoud. Wanneer een bezoeker een webpagina opent, bepaalt de pagina-logica het publiek waartoe ze behoren op basis van bekende informatie. Gebaseerd op die beoordeling AEM toont de inhoud die u voor dat publiek hebt gecreeerd.

Het publiek is gebaseerd op marketingsegmenten. Ze worden gemaakt in AEM of Adobe Target. U kunt Adobe Target-soorten publiek rechtstreeks AEM maken met behulp van de console Soorten publiek.

### Segment {#segment}

Binnen AEM ContextHub, wordt een publiek bepaald als segment, dat op regels (voorwaarden) wordt gebaseerd. Deze worden vervolgens opgelost om de vereiste inhoud te renderen.

## Activiteit {#activity}

Een activiteit:

* definieert de toewijzing van een specifiek publiek (segment) met een specifieke ervaring
* wordt de periode gedefinieerd gedurende welke de streefwaarde wordt toegepast
* identificeert de [doelmotor](#targeting-engine) die uw pagina&#39;s gebruiken

De activiteit kan of een verpersoonlijkingsactiviteit, of A/B de activiteit van de Test (in het geval van het AEM en de verpersoonlijkingswerkschema van Adobe Target) zijn.

Een activiteit kan bijvoorbeeld ervaringen definiëren voor twee verschillende soorten publiek: mensen ouder dan 30 jaar en mensen jonger dan 30 jaar. Op een pagina van uw website kunnen dan verschillende producten voor elk publiek worden weergegeven.

Of, als ander voorbeeld, kan uw productcatalogus tellers omvatten die aandacht op seizoensgebonden producten richten. Een zomersportactiviteit zou het publiek kunnen bepalen dat de theers in de zomermaanden als doel hebben.

Gebruik de [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md) om de activiteiten voor uw [Merken](#brand). U kunt ook activiteiten maken terwijl u uw [doelinhoud](/help/sites-cloud/authoring/personalization/targeted-content.md) with [Doelmodus](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode).

### Merk {#brand}

Een merk heeft een selectie van marketingactiviteiten en -gebieden.

Wanneer u een merk gebruikend de console van Activiteiten creeert, verschijnt het ook in de console van Aanbiedingen.

### Gebied {#area}

Een gebied is een deelgebied van een merk.

## Doelmodus {#targeting-mode}

Wanneer creatie, is dit de het uitgeven wijze die wordt gebruikt om, de componenten voor verpersoonlijking te activeren en te vormen.

U kunt [Doelinhoud auteur](/help/sites-cloud/authoring/personalization/targeted-content.md) met behulp van de doelmodus van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor de ervaringen van uw marketing activiteiten tot stand te brengen.

## Ervaar fragment {#experience-fragments}

Een gegroepeerde set componenten die een ervaring opbouwen.

[Ervaar fragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) zijn gemaakt van inhoud en informatie (opmaak, enzovoort) om een ervaring te creëren; deze kunnen direct worden gebruikt bij het ontwerpen van pagina&#39;s. Ze kunnen worden beschouwd als een subset van een AEM pagina. Hiermee kunnen auteurs van inhoud inhoud inhoud hergebruiken via kanalen, waaronder sitepagina&#39;s en systemen van derden.

Voor een verpersoonlijkingsvoorbeeld, kunnen een Titel, Beeld, Beschrijving, en Vraag aan de Knoop van de Actie worden gecombineerd om een laserervaring te vormen. Het gebruiken van de Fragmenten van de Ervaring is een zeer belangrijk deel van het gebruiken van de verpersoonlijking van Adobe Target.

## Richtingsmotor {#targeting-engine}

De doelengine is het mechanisme dat de logica voor doelgerichte inhoud oplost. [Activiteiten](/help/sites-cloud/authoring/personalization/activities.md) zijn geconfigureerd voor het gebruik van een van de twee beschikbare motoren voor gerichte toepassingen: AEM en Adobe Target.

De gerichte Motor is het platform of het mechanisme dat bepaalt welk verpersoonlijkingssysteem aan gebruik.

AEM kan momenteel het volgende gebruiken:

* [AEM ContextHub](#aem-contexthub) (AEM)
* de [Adobe Target](#adobe-target) personalisatie-engine

>[!CAUTION]
>
>Een enkele AEM pagina kan niet beide engines tegelijkertijd gebruiken.
>
>U kunt beide engines gebruiken op afzonderlijke pagina&#39;s binnen dezelfde site.

### AEM ContextHub {#aem-contexthub}

AEM biedt de ingebouwde engine voor gericht werken [ContextHub](/help/implementing/developing/personalization/contexthub.md) die paginaverzoeken verwerkt en bepaalt welke inhoud moet worden weergegeven. Wanneer u de AEM doelengine gebruikt, kunt u alleen segmenten gebruiken die zijn gemaakt in AEM voor het definiëren van het publiek van uw ervaringen.

### Adobe Target {#adobe-target}

De [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) Bij het activeren van de engine wordt informatie die tijdens paginabezoeken is verzameld, in Adobe Target bijgehouden.

* Wanneer u deze doelengine gebruikt, gebruikt u de segmenten die u uit Adobe Target importeert om het publiek voor uw ervaringen te definiëren.
* Activiteiten die gebruikmaken van de Adobe Target-engine zijn [gesynchroniseerd met doel](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

U kunt deze engine gebruiken wanneer u [geïntegreerd met Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md).

## Uw persoonlijke inhoud instellen {#how-to-setup-personalized-content}

Er zijn verschillende stappen en definities vereist voor het leveren van uw gepersonaliseerde inhoud:

1. Stel de doelengine in door:

   1. Configureren [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md)
   1. Integreren met [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)

1. Configureer het publiek.

   1. Definieer, afhankelijk van uw doelengine, de [Doelgroep](https://experienceleague.adobe.com/docs/target/using/audiences/target.html) of [ContextHub-segment](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md), alsmede de regels.

1. Maak uw [Merk en activiteiten](/help/sites-cloud/authoring/personalization/activities.md).

1. Maak een selectie van ervaringen die u aan de verschillende doelgroepen wilt laten zien.

1. Deze ervaringen personaliseren, door [doelgerichtheid](/help/sites-cloud/authoring/personalization/targeted-content.md) zij worden gericht aan het specifieke publiek (segmenten).