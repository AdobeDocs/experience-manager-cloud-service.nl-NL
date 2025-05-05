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

* **Werkschema van de Goedkeuring van het Project** - Dit werkschema laat u inhoud aan een gebruiker toewijzen, herzien, dan goedkeuren.
* **de Lancering van het Verzoek** - een werkschema de verzoeken om een lancering.
* **Verzoek het Landen Pagina** - Dit werkschema vraagt een het landen pagina.
* **Verzoek E-mail** - Werkschema voor het verzoeken van een e-mail.
* **DAM leidt tot en vertaalt exemplaar en DAM leidt het Exemplaar van de Taal** - creeert vertaalde binaire getallen, meta-gegevens, en markeringen voor activa en omslagen.

Afhankelijk van het projectsjabloon dat u selecteert, zijn bepaalde workflows beschikbaar:

|   | **Eenvoudig Project** | **Vertaal Project** |
|---|:-:|:-:|
| Projectgoedkeuringswerkstroom | x |  |
| Verzoek starten | x |  |
| Openingspagina aanvragen | x |  |
| E-mail aanvragen | x | |
| DAM Create Language Copy&ast; |  | x |
| DAM &amp;Create and Translate Language Copy;ast; |   | x |

>[!NOTE]
>
>&ast; Deze werkschema&#39;s zijn niet begonnen van de **tegel van het Werkschema** in Projecten. Zie [ Creërend de Kopieën van de Taal voor Assets ](/help/sites-cloud/administering/translation/managing-projects.md).

De stappen voor het starten en voltooien van workflows zijn hetzelfde, ongeacht de workflow die u kiest. Alleen de stappen worden gewijzigd.

U start een workflow rechtstreeks in Projecten (behalve voor DAM Create Language Copy of DAM Create and Translate Language Copy). De informatie over om het even welke opmerkelijke taken in een project is vermeld in de **Tile van Taken**. Meldingen voor taken die moeten worden voltooid, verschijnen naast het gebruikerspictogram.

Raadpleeg de volgende secties voor meer informatie over het werken met workflows in AEM:

* [Deelnemen aan workflows](/help/sites-cloud/authoring/workflows/participating.md)
* [Workflows toepassen op pagina&#39;s](/help/sites-cloud/authoring/workflows/applying.md)
* [Workflows configureren](/help/sites-cloud/administering/workflows-administering.md)

Deze sectie beschrijft de werkschema&#39;s beschikbaar voor Projecten.

## Workflow voor projectgoedkeuring {#project-approval-workflow}

In het werkschema van de Goedkeuring van het Project, wijst u inhoud aan een gebruiker toe, herziet, en keurt dan de inhoud goed.

1. In uw Eenvoudig project, selecteer het **`+`** teken in de **werkschema&#39;s** tegel en selecteer **Werkstroom van de Goedkeuring van het Project**.
1. Ga een titel in en selecteer aan wie om het van de lijst van het Team toe te wijzen. Voer, indien van toepassing, een beschrijving, een inhoudspad, een taakprioriteit en een vervaldatum in.

   ![ Goedkeuring van het Verzoek ](/help/sites-cloud/authoring/assets/projects-approval.png)

1. Klik **creëren**. De workflow wordt gestart. De taak verschijnt in de **tegel van 0&rbrace; Taken &lbrace;.**

## Verzoek indienen om workflow te starten {#request-launch-workflow}

Met deze workflow kunt u een verzoek indienen om de toepassing te starten.

1. Selecteer in uw Simple-project het **+**-teken in de tegel **Workflows** en selecteer **Workflow voor lancering aanvragen**.
1. Voer een titel in voor de opstart en geef het bronpad op. U kunt ook een beschrijving en live datum toevoegen, indien van toepassing. Selecteer Live-gegevens van bronpagina overnemen of subpagina&#39;s uitsluiten, afhankelijk van de manier waarop u de opstart wilt laten uitvoeren.

   ![ de lancering van het Verzoek ](/help/sites-cloud/authoring/assets/projects-request-launch.png)

1. Klik **creëren**. De workflow wordt gestart. Het werkschema verschijnt in de **lijst van Werkschema&#39;s** (klik ellipsen **..** op de **&#x200B;**&#x200B;tegel van Werkschema&#39;s om tot deze lijst toegang te hebben).

## Workflow voor taalkopieën maken (en vertalen) voor Assets {#create-and-translate-language-copy-workflow-for-assets}

**creeer het Exemplaar van de Taal** en **creeer en vertaalde 3&rbrace; werkschema&#39;s van het Exemplaar van de Taal &lbrace;zijn in detail behandeld in [ creërend taalexemplaren voor activa ](/help/assets/translate-assets.md).**
