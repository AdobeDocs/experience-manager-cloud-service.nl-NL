---
title: Aanpassing en doelgerichtheid van inhoud
description: Leer hoe AEM persoonlijke inhoud kan maken
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# Aanpassing en doelgerichtheid van inhoud {#personalization}

## Aanpassing en doelgerichtheid van inhoud {#personalization-and-content-targeting}

AEM biedt een kader van instrumenten voor het ontwerpen van gerichte inhoud en het presenteren van persoonlijke ervaringen.

## Doelmodus {#targeting-mode}

[Doelinhoud auteur](/help/sites-cloud/authoring/personalization/targeted-content.md) het gebruiken van de Wijze van het Doel van AEM. De gerichte wijze en de component van het Doel verstrekken hulpmiddelen om inhoud voor de ervaringen van uw marketing activiteiten tot stand te brengen.

## Activiteiten {#activities}

Met de activiteiten worden uw marketingactiviteiten gedefinieerd en georganiseerd. De activiteiten omvatten het publiek dat u richt, en de periode waarin het richten wordt toegepast.

Uw productcatalogus kan bijvoorbeeld theers bevatten die de aandacht richten op seizoensgebonden producten. De activiteit van de Sport van de Zomer bepaalt de marketing segmenten die de telers tijdens zomermaanden richten.

De activiteiten bepalen ook de [doelmotor](#targeting-engine) die uw pagina&#39;s gebruiken.

Gebruik de [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md) om de activiteiten voor uw merken te maken en te beheren. U kunt ook activiteiten maken terwijl u [doelinhoud auteur](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Ervaringen {#experiences}

Voor elke activiteit, bepaalt u één of meerdere ervaringen die het publiek identificeren dat u richt. AEM stelt u in staat de inhoud te beheren die elke ervaring omvat.

De soorten publiek zijn gebaseerd op marketing segmenten die of in AEM of Adobe Target worden gecreeerd. Wanneer een bezoeker een webpagina opent, bepaalt de paginalogica het publiek waartoe zij behoren en geeft deze de inhoud weer die u voor dat publiek hebt gemaakt.

Een activiteit definieert bijvoorbeeld ervaringen voor twee verschillende soorten publiek: vrouwen ouder dan 30 jaar en vrouwen jonger dan 30 jaar. Op de vrouwenpagina van een website kunnen verschillende producten voor elke ervaring worden weergegeven.

U definieert ervaringen voor een activiteit. U kunt de [Activiteitenconsole](/help/sites-cloud/authoring/personalization/activities.md#adding-editing-an-activity-using-the-activities-console) of [Doelmodus](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode) om ervaringen aan een activiteit toe te voegen.

## Aanbiedingen {#offers}

Een aanbieding is inhoud die op een plaats op een pagina voor een ervaring verschijnt. Gebruik verschillende aanbiedingen voor verschillende ervaringen om de doeltreffendheid van de inhoud voor uw publiek te maximaliseren.

Op de pagina voor vrouwen van een voorbeeldwebsite kunt u bijvoorbeeld aanbiedingen gebruiken als de laserafbeelding die boven aan de pagina wordt weergegeven. Een ander aanbod wordt gebruikt als taser voor vrouwen ouder dan 30 jaar en voor vrouwen jonger dan 30 jaar.

Gebruik de [Aanbiedingsconsole](/help/sites-cloud/authoring/personalization/offers.md) om aanbiedingen te maken die u in meerdere ervaringen kunt gebruiken. Aanbiedingen voor eenmalig gebruik maken of aanbiedingen uit een aanbiedingenbibliotheek toevoegen wanneer [ontwerpen, doelinhoud](/help/sites-cloud/authoring/personalization/targeted-content.md).

## Richtingsmotor {#targeting-engine}

De doelengine is het mechanisme dat de logica voor doelgerichte inhoud aandrijft. [Activiteiten](/help/sites-cloud/authoring/personalization/activities.md) zijn geconfigureerd voor het gebruik van een van de volgende twee motoren: AEM en Adobe Target.

### AEM {#aem}

AEM verstrekt ingebouwde het richten motor die paginaverzoeken verwerkt en de inhoud aan vertoning bepaalt. Wanneer u de AEM doelengine gebruikt, kunt u alleen segmenten gebruiken die zijn gemaakt in AEM voor het definiëren van het publiek van uw ervaringen.

### Adobe Target {#adobe-target}

De Adobe Target-engine voor doelwitten zorgt ervoor dat informatie die tijdens paginabezoeken is verzameld, wordt bijgehouden in Adobe Target.

* Wanneer u deze doelengine gebruikt, gebruikt u de segmenten die u uit Adobe Target importeert om het publiek voor uw ervaringen te definiëren.
* Activiteiten die gebruikmaken van de Adobe Target-engine zijn [gesynchroniseerd met doel](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

U kunt deze engine gebruiken wanneer u deze hebt geïntegreerd met Adobe Target. <!--You can use this engine when you have [integrated with Adobe Target](/help/sites-administering/opt-in.md).-->
