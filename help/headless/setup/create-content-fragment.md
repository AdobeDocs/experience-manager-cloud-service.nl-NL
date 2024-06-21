---
title: Inhoudsfragmenten maken - Instellingen zonder kop
description: Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Inhoudsfragmenten maken - Instellingen zonder kop {#creating-content-fragments}

Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.

## Wat zijn inhoudsfragmenten? {#what-are-content-fragments}

[Nu hebt u een map met middelen gemaakt](create-assets-folder.md) waar u de inhoudsfragmenten kunt opslaan, kunt u nu de fragmenten maken!

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

## Een inhoudsfragment maken {#how-to-create-a-content-fragment}

Inhoudsauteurs maken een willekeurig aantal Inhoudsfragmenten om de inhoud weer te geven die zij maken. Dat is hun belangrijkste taak in AEM. Met het oog op deze gids voor het op gang brengen van de werkzaamheden zullen we slechts één gids hoeven te maken.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Navigatie** > **Inhoudsfragmenten**.

1. Selecteer de [eerder gemaakte map.](create-assets-folder.md)
1. Selecteren **Maken**.
1. Het maken van een inhoudsfragment wordt weergegeven als een dialoogvenster.
Selecteer de locatie en het model waarmee u het inhoudsfragment wilt maken.

   * Welke modellen beschikbaar zijn, is afhankelijk van [**Cloud Configuration** u hebt gedefinieerd voor de map assets](create-assets-folder.md) waarin u het inhoudsfragment maakt.
   * Als uw model niet beschikbaar is, controleert u de configuratie van de map Assets.

   Voeg de titel, de naam en, indien nodig, de beschrijving toe.

   ![Dialoogvenster Nieuw inhoudsfragment maken](/help/sites-cloud/administering/content-fragments/assets/cfc-console-create.png)

1. Selecteren **Maken** of  **Maken en openen**.

Inhoudsfragmenten kunnen verwijzen naar andere inhoudsfragmenten, waarbij zo nodig een geneste inhoudsstructuur mogelijk is.

Inhoudsfragmenten kunnen ook verwijzen naar andere elementen in AEM. [Deze elementen moeten in AEM worden opgeslagen](/help/assets/manage-digital-assets.md) voordat u een verwijzing naar een inhoudsfragment maakt.

## Volgende stappen {#next-steps}

Nu u een inhoudsfragment hebt gemaakt, kunt u verdergaan naar het laatste gedeelte van de gids Aan de slag en [Maak API-aanvragen voor toegang tot en levering van inhoudsfragmenten.](create-api-request.md)

>[!TIP]
>
>Voor volledige details over het beheren van Inhoudsfragmenten raadpleegt u de [Documentatie over inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
