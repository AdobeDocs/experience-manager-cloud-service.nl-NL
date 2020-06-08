---
title: Aanpassing en doelgerichtheid van inhoud
description: Leer hoe AEM persoonlijke inhoud kan maken
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Aanpassing en doelgerichtheid van inhoud {#personalization}

## Aanpassing en doelgerichtheid van inhoud {#personalization-and-content-targeting}

AEM biedt een raamwerk van instrumenten voor het ontwerpen van gerichte inhoud en het presenteren van persoonlijke ervaringen.

## Doelmodus {#targeting-mode}

[Auteur doelt inhoud](/help/sites-cloud/authoring/personalization/targeted-content.md) met de doelmodus van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor de ervaringen van uw marketing activiteiten tot stand te brengen.

## Activiteiten {#activities}

Met de activiteiten worden uw marketingactiviteiten gedefinieerd en georganiseerd. De activiteiten omvatten het publiek dat u richt, en de periode waarin het richten wordt toegepast.

Uw productcatalogus kan bijvoorbeeld theers bevatten die de aandacht richten op seizoensgebonden producten. De activiteit van de Sport van de Zomer bepaalt de marketing segmenten die de telers tijdens zomermaanden richten.

Met de activiteiten wordt ook aangegeven welke [doelengine](#targeting-engine) uw pagina&#39;s gebruiken.

Gebruik de [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md) om de activiteiten voor uw merken tot stand te brengen en te beheren. U kunt ook activiteiten maken terwijl u [doelinhoud](/help/sites-cloud/authoring/personalization/targeted-content.md)ontwerpt.

## Ervaringen {#experiences}

Voor elke activiteit, bepaalt u één of meerdere ervaringen die het publiek identificeren dat u richt. Met AEM kunt u de inhoud van elke ervaring beheren.

Soorten publiek zijn gebaseerd op marketingsegmenten die in AEM of Adobe Target zijn gemaakt. Wanneer een bezoeker een webpagina opent, bepaalt de paginalogica het publiek waartoe zij behoren en geeft deze de inhoud weer die u voor dat publiek hebt gemaakt.

Een activiteit definieert bijvoorbeeld ervaringen voor twee verschillende soorten publiek: vrouwen ouder dan 30 jaar en vrouwen jonger dan 30 jaar. Op de vrouwenpagina van een website kunnen verschillende producten voor elke ervaring worden weergegeven.

U definieert ervaringen voor een activiteit. U kunt de console [van](/help/sites-cloud/authoring/personalization/activities.md#adding-editing-an-activity-using-the-activities-console) Activiteiten of het [richten wijze](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode) gebruiken om ervaringen aan een activiteit toe te voegen.

## Aanbiedingen {#offers}

Een aanbieding is inhoud die op een plaats op een pagina voor een ervaring verschijnt. Gebruik verschillende aanbiedingen voor verschillende ervaringen om de doeltreffendheid van de inhoud voor uw publiek te maximaliseren.

Op de pagina voor vrouwen van een voorbeeldwebsite kunt u bijvoorbeeld aanbiedingen gebruiken als de laserafbeelding die boven aan de pagina wordt weergegeven. Een ander aanbod wordt gebruikt als taser voor vrouwen ouder dan 30 jaar en voor vrouwen jonger dan 30 jaar.

Gebruik de console [](/help/sites-cloud/authoring/personalization/offers.md) Aanbiedingen om aanbiedingen te creëren die u in veelvoudige ervaringen kunt gebruiken. Aanbiedingen voor eenmalig gebruik maken of aanbiedingen uit een aanbiedingsbibliotheek toevoegen wanneer u [doelinhoud](/help/sites-cloud/authoring/personalization/targeted-content.md)ontwerpt.

## Richtingsmotor {#targeting-engine}

De doelengine is het mechanisme dat de logica voor doelgerichte inhoud aandrijft. [De activiteiten](/help/sites-cloud/authoring/personalization/activities.md) worden gevormd om één van twee te gebruiken richtend motoren die beschikbaar zijn: AEM en Adobe Target.

### AEM {#aem}

AEM biedt een ingebouwde engine die paginaverzoeken verwerkt en bepaalt welke inhoud moet worden weergegeven. Wanneer u de AEM-doelengine gebruikt, kunt u alleen segmenten gebruiken die in AEM zijn gemaakt om het publiek van uw ervaringen te bepalen.

### Adobe-doel {#adobe-target}

De Adobe Target-engine zorgt ervoor dat informatie die tijdens paginabezoeken is verzameld, wordt bijgehouden in Adobe Target.

* Wanneer u deze doelengine gebruikt, gebruikt u de segmenten die u vanuit Adobe Target importeert om het publiek voor uw ervaringen te definiëren.
* Activiteiten die gebruikmaken van de Adobe Target-engine worden [gesynchroniseerd met Target](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

U kunt deze engine gebruiken wanneer u deze hebt geïntegreerd met Adobe Target. <!--You can use this engine when you have [integrated with Adobe Target](/help/sites-administering/opt-in.md).-->
