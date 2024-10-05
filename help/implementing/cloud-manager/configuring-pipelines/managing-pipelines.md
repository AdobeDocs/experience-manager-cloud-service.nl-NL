---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 0%

---


# Pijpleidingen beheren {#managing-pipelines}

Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.

## Pipetkaart {#pipeline-card}

De **Pijpleidingen** kaart op de **pagina van het Overzicht van het Programma** in Cloud Manager geeft u een overzicht van al uw pijpleidingen en hun huidige status.

![ de kaart van Pijpleidingen in Cloud Manager ](/help/implementing/cloud-manager/assets/configure-pipeline/pipelines-card.png)

Door de ellipsieknoop naast elke pijpleiding te klikken kunt u de volgende acties voeren.

* [De pijplijn uitvoeren](#running-pipelines)
* [De pijplijn bewerken](#editing-pipelines)
* [De pijplijn verwijderen](#deleting-pipelines)
* [Details weergeven](#view-details)

Onder aan de lijst met pijpleidingen staan algemene opties.

* **voeg** toe - aan [ voeg een nieuwe productiepijpleiding ](configuring-production-pipelines.md) toe of [ voeg nieuwe niet-productiepijpleiding ](configuring-non-production-pipelines.md) toe
* **toon allen** - neemt de gebruiker aan het scherm van Pijpleidingen om alle pijpleidingen in een meer gedetailleerde lijst te bekijken.
* **Info van de Reactie van de Toegang** - Toont de informatie noodzakelijk om tot de git van Cloud Manager toegang te hebben bewaarplaats
* **leer Meer** - navigeert aan CI/CD de middelen van de pijpleidingsdocumentatie.

## Venster Pijpleidingen {#pipelines}

Het **venster van Pijpleidingen** toont een volledige lijst van alle pijpleidingen voor het geselecteerde programma. Dit is nuttig aangezien het uitvoerigere informatie dan voorstelt wat in de [ Kaart van de Pijpleiding ](#pipeline-card) beschikbaar is.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het 0} Programma, selecteer het** Pijpleidingen **lusje om aan het** venster van de Pijpleidingen **over te schakelen.**

1. Hier kunt u een lijst van alle pijpleidingen voor het programma zien en pijpleidingsuitvoering beginnen en tegenhouden zoals u in de **Kaart van Pijpleidingen**.

Als een pijpleiding uitvoert, die het informatiepictogram in de **kolom van de Status** klikken openbaart details over de uitvoering.

![ de uitvoeringsdetails van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-status.png)

Het klikken **details van de Mening** neemt u aan de [ details van de pijpleidingsuitvoering ](#view-details).

U kunt de elliptische knoop van de pijpleiding ook klikken om extra acties aangewezen aan de pijpleidingsstaat te nemen zoals [ het uitgeven ](#editing-pipelines) het of [ het annuleren van uitvoering ](#cancel).

![ Acties van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-actions.png)

## Activiteitenvenster {#activity}

Het **venster van de Activiteit** toont een volledige lijst van alle pijpleidingen uitvoeringen voor het geselecteerde programma evenals andere belangrijke programmagebeurtenissen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, selecteer het **lusje van de Activiteit** om aan het **venster van de Activiteit** over te schakelen.

1. Hier ziet u een lijst van alle pijpleiding uitvoeringen voor het programma met inbegrip van huidige en historische executies.

Als een pijpleiding uitvoert, zal het klikken van het informatiepictogram in de **kolom van de Status** details over de uitvoering openbaren.

![ de uitvoeringsdetails van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-activity.png)

Tapping of het klikken van de rij die de pijpleidingsuitvoering vertegenwoordigt neemt u aan de [ details van de pijpleidingsuitvoering ](#view-details).

U kunt de ellipsis knoop ook klikken om verdere actie op de pijpleidingsuitvoering, zoals mening zijn details of download het logboek, dat u aan de [ pagina van de pijpleidingsdetails ](#view-details) neemt.

![ de uitvoeringshandelingen van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-execution-actions.png)

## Lopende pijpleidingen {#running-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u uitgezocht **Looppas** van het menu in werking stelt.

1. De pijpleidingslooppas begint en door de **Status** kolom wordt vermeld.

U kunt de details van de looppas zien door de ellipsknoop opnieuw te klikken en **[details van de Mening](#view-details)** te selecteren.

Afhankelijk van het type van pijpleiding, kunt u de looppas kunnen annuleren door de ellipsknoop opnieuw te klikken en **te selecteren annuleert**.

## Een pijplijn bewerken {#editing-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u **uitgeven en dan selecteren** van het menu uitgeven.

1. De **geeft de pijpleiding van de Productie uit** of **geeft niet-Productie pijplijn** dialoogvakvertoningen uit, toestaand u om de zelfde details uit te geven die u toen het creëren van de pijpleiding inging.

   * Zie de volgende pagina&#39;s voor details over de gebieden en configuratieopties beschikbaar voor pijpleidingen.
      * [Productiepijpleidingen configureren](configuring-production-pipelines.md)
      * [Niet-productiepijpleidingen configureren](configuring-non-production-pipelines.md)

1. Klik **Update** zodra u het uitgeven van de pijpleiding wordt gedaan.

>[!NOTE]
>
>U kunt een lopende pijpleiding niet uitgeven.

>[!NOTE]
>
>De de rij en config van het Web pijpleidingen worden niet gesteund met privé bewaarplaatsen. Zie [ een Privé Bewaarplaats in Cloud Manager ](/help/implementing/cloud-manager/managing-code/private-repositories.md) voor details en de volledige lijst van beperkingen toevoegen.

## Verwijderen van pijpleidingen {#deleting-pipelines}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u uitgezocht **Schrapping** van het menu in werking stelt.

>[!NOTE]
>
>U kunt geen lopende pijpleiding schrappen.

## Details van pipet weergeven {#view-details}

U kunt de details van een pijpleiding bekijken om de status en de logboeken van zijn laatste looppas te zien.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **Pipelines** kaart van de **pagina van het Overzicht van het Programma** en klik de ellipsknoop naast de pijpleiding u uitgezocht **details van de Mening** van het menu in werking stelt.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![ details van de Pijpleiding ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Van hier kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie het document [ Opstellend Uw Code ](/help/implementing/cloud-manager/deploy-code.md) voor meer informatie over codeplaatsing en tests in werking stellen.

Alle stappen in een pijpleidingsuitvoering worden getoond met degenen die nog niet uit grijs begonnen. De voltooide stappen tonen hun duur.

Zodra een pijpleidingsstap volledig is, wordt een samenvatting voorgesteld.

![ Overzicht van de Stap ](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-step.png)

Selecteer de **verbinding van de Details van de Mening** om de **sectie van de Duur** te openbaren. Dit omvat de gemiddelde duur van de pijpleiding op basis van de historische trend voor dat programma.

![ Duur ](/help/implementing/cloud-manager/assets/configure-pipeline/duration.png)

Als uw pijpleiding a **Code Scanning** stap bevatte, die kwesties opriep, kunt u de **knoop van de Details van de Download** tikken of klikken om een lijst van [ tests van de codekwaliteit ](/help/implementing/cloud-manager/code-quality-testing.md) te bekijken die niet overgegaan.

![ de kwaliteitskwesties van de Code ](assets/managing-pipelines-code-quality-issues.png)

De kolom van de Plaats van het Dossier van het A **Project** is beschikbaar in het Csv- dossier om op de plaats van de beledigende code te wijzen. Deze kolom is de project-relatieve weg, terwijl de **kolom van de Plaats van het 0} Dossier {wordt geproduceerd.**

![ van het de aftasten van de code van het Project details ](assets/managing-pipelines-code-quality-details.png)

>[!NOTE]
>
>U kunt details van een pijpleiding slechts bekijken die loopt of minstens eens in werking is gesteld.

## Pijpleidingen annuleren {#cancel}

Als een pijpleiding in de bevestiging of bouwt beeldfase is kunt u veilig de pijpleidingslooppas annuleren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de pagina van het programmaoverzicht, klik de elliptische knoop van de pijpleiding u op de **kaart van de Pijpleidingen** wilt annuleren.

   ![ het Kantelen van een pijpleiding ](/help/implementing/cloud-manager/assets/cancel-pipeline.png)

1. Selecteer **annuleren**.

Alternatief kunt u een pijpleiding van de pagina van pijpleidingsdetails annuleren.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **lusje van de Pijpleidingen** van de **pagina van het Overzicht van het Programma** en selecteer de pijpleiding u wilt annuleren.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

   ![ annuleert de details van de Pijpleiding ](/help/implementing/cloud-manager/assets/cancel-pipeline-details.png)

1. Selecteer **annuleren**.
