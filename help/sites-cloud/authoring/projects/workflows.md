---
title: Werken met projectworkflows
description: Een verscheidenheid van projectwerkschema's is beschikbaar uit de doos.
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 12%

---


# Werken met projectworkflows {#working-with-project-workflows}

De projectworkflows die beschikbaar zijn uit het vak zijn onder andere:

* **Workflow** voor projectgoedkeuring - Met deze workflow kunt u inhoud toewijzen aan een gebruiker, deze controleren en vervolgens goedkeuren.
* **Starten** aanvragen - Een workflow waarvoor u een opstart wilt aanvragen.
* **Openingspagina** aanvragen - Deze workflow vraagt om een bestemmingspagina.
* **E-mail** aanvragen - Workflow voor het aanvragen van een e-mail.
* **DAM maakt en vertaalt kopie en DAM maakt taalkopie** - maakt vertaalde binaire bestanden, metagegevens en tags voor elementen en mappen.

Afhankelijk van het projectsjabloon dat u selecteert, zijn bepaalde workflows beschikbaar:

|  | **Eenvoudig project** | **Mediaproject** | **Omzettingsproject** |
|---|:-:|:-:|:-:|
| Verzoek om kopie |  | x |  |
| Fotofoto van product |  | x |  |
| Projectgoedkeuring | x |  |  |
| Verzoek starten | x |  |  |
| Openingspagina aanvragen | x |  |  |
| E-mail aanvragen | x |  |  |
| DAM Create Language Copy&amp;ast; |  |  | x |
| DAM &amp;Create and Translate Language Copy;ast; |  |  | x |

>[!NOTE]
>
>&amp;ast; Deze werkschema&#39;s zijn niet begonnen van de tegel van het **Werkschema** in Projecten. Zie Taalkopieën maken voor elementen.
<!--
>&ast; These workflows are not started from the **Workflow** tile in Projects. See [Creating Language Copies for Assets.](/help/sites-administering/tc-manage.md)
-->

De stappen voor het starten en voltooien van workflows zijn hetzelfde, ongeacht de workflow die u kiest. Alleen de stappen worden gewijzigd.

U start een workflow rechtstreeks in Projecten (behalve voor DAM Create Language Copy of DAM Create and Translate Language Copy). De informatie over om het even welke opmerkelijke taken in een project wordt vermeld in de **tegel van Taken** . Meldingen voor taken die moeten worden voltooid, verschijnen naast het gebruikerspictogram.

Raadpleeg de volgende secties voor meer informatie over het werken met workflows in AEM:

* [Deelnemen aan workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Workflows toepassen op pagina&#39;s](/help/sites-cloud/authoring/workflows/applying.md)
* Workflows configureren <!--* [Configuring workflows](/help/sites-administering/workflows.md)-->

Deze sectie beschrijft de werkschema&#39;s beschikbaar voor Projecten.

## Workflow voor kopiëren aanvragen {#request-copy-workflow}

Met deze workflow kunt u een gebruiker om een manuscript vragen en het vervolgens goedkeuren. De workflow voor het kopiëren van aanvragen starten:

1. Selecteer in uw Media-project het **+**-teken in de tegel **Workflows** en selecteer **Workflow voor kopiëren aanvragen**.
1. Voer een eigenschapstitel in en een korte samenvatting van wat u vraagt. Voer, indien van toepassing, een doelwoordtelling, taakprioriteit en een vervaldatum in.

   ![Kopieerwerkstroom aanvragen](/help/sites-cloud/authoring/assets/projects-request-copy.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

   ![Verzoek om kopie toegevoegd](/help/sites-cloud/authoring/assets/projects-request-copy-add.png)

## Workflow voor projectgoedkeuring {#project-approval-workflow}

In het werkschema van de Goedkeuring van het Project, wijst u inhoud aan een gebruiker toe, herziet, en keurt dan de inhoud goed.

1. In your Simple project, select the **`+`** sign in the **Workflows** tile and select **Project Approval Workflow**.
1. Ga een titel in en selecteer aan wie om het van de lijst van het Team toe te wijzen. Voer, indien van toepassing, een beschrijving, een inhoudspad, een taakprioriteit en een vervaldatum in.

   ![Goedkeuring aanvragen](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

   ![Goedkeuring aanvragen](/help/sites-cloud/authoring/assets/projects-approval-add.png)

## Verzoek indienen om workflow te starten {#request-launch-workflow}

Met deze workflow kunt u een verzoek indienen om de toepassing te starten.

1. Selecteer in uw Simple-project het **+**-teken in de tegel **Workflows** en selecteer **Workflow voor lancering aanvragen**.
1. Voer een titel in voor de opstart en geef het bronpad voor de opstart op. U kunt ook een beschrijving en live datum toevoegen, indien van toepassing. Selecteer Live-gegevens van bronpagina overnemen of subpagina&#39;s uitsluiten, afhankelijk van de manier waarop u de opstart wilt laten uitvoeren.

   ![Verzoek starten](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Klik op **Maken**. De workflow wordt gestart. De workflow wordt weergegeven in de lijst **Workflows** (klik op Ovaal **..** op de **werkstroomtegel** voor toegang tot deze lijst).

## Workflow voor taalkopieën maken (en vertalen) voor middelen {#create-and-translate-language-copy-workflow-for-assets}

De workflows **Taalkopie maken** en **Taalkopie maken en vertalen** worden uitgebreid besproken bij het maken van taalkopieën voor assets.
