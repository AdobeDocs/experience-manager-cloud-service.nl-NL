---
title: Inhoudsfragmenten maken - Instellingen zonder kop
description: Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.
exl-id: a227ae2c-f710-4968-8a00-bfe48aa66145
source-git-commit: d35b60810a1624390d3d9c82c2a364140ea37536
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# Inhoudsfragmenten maken - Instellingen zonder kop {#creating-content-fragments}

Leer hoe u AEM inhoudsfragmenten kunt gebruiken voor het ontwerpen, maken, beheren en gebruiken van pagina-onafhankelijke inhoud voor levering zonder kop.

## Wat zijn inhoudsfragmenten? {#what-are-content-fragments}

[Nu hebt u een map met middelen gemaakt](create-assets-folder.md) waar u de inhoudsfragmenten kunt opslaan, kunt u nu de fragmenten maken!

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden die klaar is voor gebruik op meerdere locaties en via meerdere kanalen.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

## Een inhoudsfragment maken {#how-to-create-a-content-fragment}

Inhoudsauteurs maken een willekeurig aantal Inhoudsfragmenten om de inhoud te vertegenwoordigen die zij maken. Dit zal hun belangrijkste taak in AEM zijn. Met het oog op deze gids voor het op gang brengen van de werkzaamheden zullen we slechts één gids hoeven te maken.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Navigation -> Middelen**.
1. Tik of klik op de knop [eerder gemaakte map.](create-assets-folder.md)
1. Tik of klik op **Maken -> Inhoudsfragment**.
1. Het maken van een inhoudsfragment wordt in twee stappen weergegeven als een wizard. Selecteer eerst het model dat u wilt gebruiken om het inhoudsfragment te maken en tik of klik op **Volgende**.
   * Welke modellen beschikbaar zijn, is afhankelijk van de [**Cloud Configuration** u hebt gedefinieerd voor de map assets](create-assets-folder.md) waarin u het inhoudsfragment maakt.
   * Als u het bericht ontvangt `We could not find any models`, controleert u de configuratie van de map met elementen.

   ![Inhoudsfragmentmodel selecteren](../assets/content-fragment-model-select.png)
1. Een **Titel**, **Beschrijving**, en **Tags** tikken of klikken **Maken**.

   ![Inhoudsfragment maken](../assets/content-fragment-create.png)
1. Tik of klik op **Openen** in het bevestigingsvenster.

   ![Bevestiging van Content Fragment](../assets/content-fragment-confirmation.png)
1. Geef de details van het inhoudsfragment op in de Inhoudsfragmenteditor.

   ![Inhoudsfragmenteditor](../assets/content-fragment-edit.png)
1. Tik of klik op **Opslaan** of  **Opslaan en sluiten**.

Inhoudsfragmenten kunnen verwijzen naar andere inhoudsfragmenten, waarbij zo nodig een geneste inhoudsstructuur mogelijk is.

Inhoudsfragmenten kunnen ook verwijzen naar andere elementen in AEM. [Deze elementen moeten in AEM worden opgeslagen](/help/assets/manage-digital-assets.md) voordat u een verwijzing naar een inhoudsfragment maakt.

## Volgende stappen {#next-steps}

Nu u een inhoudsfragment hebt gemaakt, kunt u verdergaan naar het laatste gedeelte van de gids Aan de slag en [Maak API-aanvragen voor toegang tot en levering van inhoudsfragmenten.](create-api-request.md)

>[!TIP]
>
>Voor volledige details over het beheren van Inhoudsfragmenten raadpleegt u de [Documentatie over inhoudsfragmenten](/help/assets/content-fragments/content-fragments.md)
