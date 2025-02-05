---
title: Inhoudsfragmenten maken - Instellingen zonder kop
description: Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Inhoudsfragmenten maken - Instellingen zonder kop {#creating-content-fragments}

Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.

## Wat zijn inhoudsfragmenten? {#what-are-content-fragments}

[ nu dat u een activa omslag ](create-assets-folder.md) hebt gecreeerd waar u uw Fragmenten van de Inhoud kunt opslaan, kunt u de fragmenten nu tot stand brengen!

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

## Een inhoudsfragment maken {#how-to-create-a-content-fragment}

Inhoudsauteurs maken een willekeurig aantal Inhoudsfragmenten om de inhoud weer te geven die zij maken. Dat is hun belangrijkste taak in AEM. Met het oog op deze gids voor het op gang brengen van de werkzaamheden zullen we slechts één gids hoeven te maken.

1. Logboek in AEM as a Cloud Service en van het belangrijkste menu selecteert **Navigatie** > **de Fragmenten van de Inhoud**.

1. Selecteer de [ omslag u eerder ](create-assets-folder.md) creeerde.
1. Selecteer **creeer**.
1. Het maken van een inhoudsfragment wordt weergegeven als een dialoogvenster.
Selecteer de locatie en het model waarmee u het inhoudsfragment wilt maken.

   * De beschikbare modellen hangen van de [**Configuratie van de Wolk** af u voor de activa omslag ](create-assets-folder.md) bepaalde waarin u het Fragment van de Inhoud creeert.
   * Als uw model niet beschikbaar is, controleert u de configuratie van de map Assets.

   Voeg de titel, de naam en, indien nodig, de beschrijving toe.

   ![ creeer de Nieuwe dialoog van het Fragment van de Inhoud ](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. Selecteer **creeer** of **creeer en open**.

Inhoudsfragmenten kunnen verwijzen naar andere inhoudsfragmenten, waarbij zo nodig een geneste inhoudsstructuur mogelijk is.

Inhoudsfragmenten kunnen ook verwijzen naar andere elementen in AEM. [ Deze activa moeten in AEM ](/help/assets/manage-digital-assets.md) worden opgeslagen alvorens een het van verwijzingen voorzien Fragment van de Inhoud te creëren.

## Volgende stappen {#next-steps}

Nu u een Fragment van de Inhoud hebt gecreeerd, kunt u zich op het definitieve deel van het begonnen worden gids bewegen en [ creeer API verzoeken om tot inhoudsfragmenten toegang te hebben en te leveren ](create-api-request.md).

>[!TIP]
>
>Voor volledige details over het beheren van de Fragmenten van de Inhoud, zie de [ documentatie van de Fragmenten van de Inhoud ](/help/sites-cloud/administering/content-fragments/overview.md).
