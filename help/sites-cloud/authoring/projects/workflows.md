---
title: Werken met projectworkflows
description: Een verscheidenheid van projectwerkschema's is beschikbaar uit de doos.
exl-id: a5c9a6df-7def-43f3-b41b-524a4f4211e9
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---

# Werken met projectworkflows {#working-with-project-workflows}

De projectworkflows die beschikbaar zijn uit het vak zijn onder andere:

* **Workflow voor projectgoedkeuring** - Met deze workflow kunt u inhoud toewijzen aan een gebruiker, controleren en vervolgens goedkeuren.
* **Verzoek starten** - Een workflow waarvoor de toepassing wordt gestart.
* **Openingspagina aanvragen** - Voor deze workflow is een bestemmingspagina vereist.
* **E-mail aanvragen** - Workflow voor het aanvragen van een e-mail.
* **DAM maken en vertalen kopie en DAM maken taalkopie** - Hiermee maakt u vertaalde binaire bestanden, metagegevens en tags voor elementen en mappen.

Afhankelijk van het projectsjabloon dat u selecteert, zijn bepaalde workflows beschikbaar:

|   | **Eenvoudig project** | **Omzettingsproject** |
|---|:-:|:-:|
| Projectgoedkeuringswerkstroom | x |  |
| Verzoek starten | x |  |
| Openingspagina aanvragen | x |  |
| E-mail aanvragen | x | |
| DAM Create Language Copy&amp;ast; |  | x |
| DAM &amp;Create and Translate Language Copy |   | x |

>[!NOTE]
>
>&amp;Laatste; deze workflows worden niet gestart vanuit de **Workflow** tegel in projecten. Zie [Taalkopieën voor middelen maken](/help/sites-cloud/administering/translation/managing-projects.md).

De stappen voor het starten en voltooien van workflows zijn hetzelfde, ongeacht de workflow die u kiest. Alleen de stappen worden gewijzigd.

U start een workflow rechtstreeks in Projecten (behalve voor DAM Create Language Copy of DAM Create and Translate Language Copy). Informatie over openstaande taken in een project wordt vermeld in de **Taken** tegel. Meldingen voor taken die moeten worden voltooid, verschijnen naast het gebruikerspictogram.

Raadpleeg de volgende secties voor meer informatie over het werken met workflows in AEM:

* [Deelnemen aan workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Workflows toepassen op pagina&#39;s](/help/sites-cloud/authoring/workflows/applying.md)
* [Workflows configureren](/help/sites-cloud/administering/workflows-administering.md)

Deze sectie beschrijft de werkschema&#39;s beschikbaar voor Projecten.

## Workflow voor projectgoedkeuring {#project-approval-workflow}

In het werkschema van de Goedkeuring van het Project, wijst u inhoud aan een gebruiker toe, herziet, en keurt dan de inhoud goed.

1. In uw Eenvoudig project, selecteer **`+`** aanmelden **Workflows** tegel en selecteer **Workflow voor projectgoedkeuring**.
1. Ga een titel in en selecteer aan wie om het van de lijst van het Team toe te wijzen. Voer, indien van toepassing, een beschrijving, een inhoudspad, een taakprioriteit en een vervaldatum in.

   ![Goedkeuring aanvragen](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Klikken **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de **Taken** tegel.

## Verzoek indienen om workflow te starten {#request-launch-workflow}

Met deze workflow kunt u een verzoek indienen om de toepassing te starten.

1. Selecteer in uw Simple-project het **+**-teken in de tegel **Workflows** en selecteer **Workflow voor lancering aanvragen**.
1. Voer een titel in voor de opstart en geef het bronpad op. U kunt ook een beschrijving en live datum toevoegen, indien van toepassing. Selecteer Live-gegevens van bronpagina overnemen of subpagina&#39;s uitsluiten, afhankelijk van de manier waarop u de opstart wilt laten uitvoeren.

   ![Verzoek starten](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Klikken **Maken**. De workflow wordt gestart. De workflow wordt weergegeven in het dialoogvenster **Workflows** lijst (klik op ovalen) **...** op de **Workflows** tegel voor toegang tot deze lijst).

## Workflow voor taalkopieën maken (en vertalen) voor middelen {#create-and-translate-language-copy-workflow-for-assets}

De **Taalkopie maken** en de **Taalkopie maken en vertalen** workflows worden uitvoerig behandeld [maken, taalkopieën voor elementen](/help/assets/translate-assets.md).
