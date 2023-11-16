---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op **Programmaoverzicht** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![Pipelinekaart in Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

Door de ellipsieknoop naast elke pijpleiding te klikken kunt u de volgende acties voeren.

* [De pijplijn uitvoeren](#running-pipelines)
* [De pijplijn bewerken](#editing-pipelines)
* [De pijplijn verwijderen](#deleting-pipelines)
* [Details weergeven](#view-details)

Onder aan de lijst met pijpleidingen staan algemene opties.

* **Toevoegen** - Aan [toevoegen van een nieuwe productiepijplijn](configuring-production-pipelines.md) of [nieuwe niet-productiepijpleiding toevoegen](configuring-non-production-pipelines.md)
* **Alles tonen** - Neemt de gebruiker aan het scherm van Pijpleidingen om alle pijpleidingen in een meer gedetailleerde lijst te bekijken.
* **Repo-info openen** - Geeft de informatie weer die nodig is om toegang te krijgen tot de gegevensopslagruimte van Cloud Manager
* **Meer informatie** - Navigeert aan CI/CD pijpleidingsdocumentatiemiddelen.

## Venster Pijpleidingen {#pipelines}

De **Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Dit is handig omdat het uitgebreidere informatie biedt dan de informatie in de [Pipetkaart.](#pipeline-card)

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Van de **Programmaoverzicht** pagina, tik of klik op de knop **Pijpleidingen** tab naar **Pijpleidingen** venster.

1. Hier kunt u een lijst van alle pijpleidingen voor het programma zien evenals begin en stop pijpleidingsuitvoering zoals u in **Pijppijplijnkaart**.

Als een pijpleiding uitvoert, beweegt over zijn **Status** de kolom zal details over de uitvoering openbaren.

![Uitvoeringdetails pijpleiding](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

Tikken of klikken **Details weergeven** neemt u mee naar de [details over de uitvoering van de pijpleiding.](#view-details)

## Activiteitenvenster {#activity}

De **Activiteiten** toont een volledige lijst van alle pijpleiding uitvoeringen voor het geselecteerde programma.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Van de **Programmaoverzicht** pagina, tik of klik op de knop **Activiteit** tab naar **Activiteit** venster.

1. Hier ziet u een lijst van alle pijpleiding uitvoeringen voor het programma met inbegrip van huidige en historische executies.

Als een pijpleiding uitvoert, beweegt over zijn **Status** de kolom zal details over de uitvoering openbaren.

![Uitvoeringdetails pijpleiding](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Tikken of klikken **Details weergeven** neemt u mee naar de [details over de uitvoering van de pijpleiding.](#view-details)

## Lopende pijpleidingen {#running-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik de ellipsknoop naast de pijpleiding u in werking stelt uitgezocht **Uitvoeren** in het menu.

1. De pijpleidingslooppas begint en door **Status** kolom.

U kunt de details van de run zien door nogmaals op de knop voor ovaal te klikken en vervolgens **[Bekijk details.](#view-details)**

Afhankelijk van het type pijplijn, kunt u de looppas kunnen annuleren door de ellipsknoop opnieuw te klikken en te selecteren **Annuleren**.

## Bewerkingspijplijnen {#editing-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik de ellipsknoop naast de pijpleiding u wilt uitgeven en dan selecteren **Bewerken** in het menu.

1. De **Productiepijpleiding bewerken** of **Niet-productiepijplijn bewerken** wordt weergegeven, zodat u dezelfde details kunt bewerken als u hebt ingevoerd bij het maken van de pijplijn.

   * Zie de volgende pagina&#39;s voor details op alle gebieden en configuratieopties beschikbaar voor pijpleidingen.
      * [Productiepijpleidingen configureren](configuring-production-pipelines.md)
      * [Niet-productiepijpleidingen configureren](configuring-non-production-pipelines.md)

1. Klikken **Bijwerken** zodra u klaar bent met het bewerken van de pijplijn.

>[!NOTE]
>
>U kunt een lopende pijpleiding niet uitgeven.

## Verwijderen van pijpleidingen {#deleting-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik de ellipsknoop naast de pijpleiding u in werking stelt uitgezocht **Verwijderen** in het menu.

>[!NOTE]
>
>U kunt geen lopende pijpleiding schrappen.

## Details van pipet weergeven {#view-details}

U kunt de details van een pijpleiding bekijken om de status en de logboeken van zijn laatste looppas te zien.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik de ellipsknoop naast de pijpleiding u in werking stelt uitgezocht **Details weergeven** in het menu.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![Details pijpleiding](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Van hier kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie het document [Uw code implementeren](/help/implementing/cloud-manager/deploy-code.md) voor meer informatie over codeplaatsing en tests in werking stellen.

Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

Zodra een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

![Overzicht stap](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

Tik of klik op de knop **Details weergeven** koppeling om de **Duur** sectie. Dit omvat de gemiddelde duur van de pijpleiding op basis van de historische trend voor dat programma.

![Duur](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

>[!NOTE]
>
>U kunt details van een pijpleiding slechts bekijken die loopt of minstens eens in werking is gesteld.

## Pijpleidingen annuleren {#cancel}

Als een pijpleiding in de bevestiging of bouwt beeldfase is kunt u veilig de pijpleidingslooppas annuleren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Van de pagina van het programmaoverzicht, klik de elliptische knoop van de pijpleiding u op wilt annuleren **Pijpleidingen** kaart.

   ![Een pijpleiding annuleren](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Tik of klik op **Annuleren**.

Alternatief kunt u een pijpleiding van de pagina van pijpleidingsdetails annuleren.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** van de **Programmaoverzicht** pagina en tik of klik op de pijplijn die u wilt annuleren.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

   ![Details van pijplijn annuleren](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Tik of klik op **Annuleren**.
