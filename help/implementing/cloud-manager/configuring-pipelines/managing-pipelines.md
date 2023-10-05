---
title: Pijpleidingen beheren
description: Leer hoe u uw bestaande pijpleidingen kunt beheren, inclusief bewerken, uitvoeren en verwijderen.
index: true
exl-id: 4aff5a84-134a-43fa-8de8-8d564f4edd16
source-git-commit: b8d692e354851a31b4f66b24135c863b5ca723b4
workflow-type: tm+mt
source-wordcount: '667'
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

## Lopende pijpleidingen {#running-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op de ellipsieknoop naast de pijpleiding u in werking stelt selecteren **Uitvoeren** in het menu.

1. De pijpleidingslooppas begint en door **Status** kolom.

U kunt de details van de run zien door nogmaals op de knop voor ovaal te klikken en vervolgens **[Bekijk details.](#view-details)**

Afhankelijk van het type pijplijn, kunt u de looppas kunnen annuleren door de ellipsknoop opnieuw te klikken en te selecteren **Annuleren**.

## Bewerkingspijplijnen {#editing-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op de ellipsieknoop naast de pijpleiding u wilt uitgeven en dan selecteren **Bewerken** in het menu.

1. De **Productiepijpleiding bewerken** of **Niet-productiepijplijn bewerken** wordt weergegeven, zodat u dezelfde details kunt bewerken als u hebt ingevoerd bij het maken van de pijplijn.

   * Zie de volgende pagina&#39;s voor details op alle gebieden en configuratieopties beschikbaar voor pijpleidingen.
      * [Productiepijpleidingen configureren](configuring-production-pipelines.md)
      * [Niet-productiepijpleidingen configureren](configuring-non-production-pipelines.md)

1. Klikken op **Bijwerken** zodra u klaar bent met het bewerken van de pijplijn.

>[!NOTE]
>
>U kunt een lopende pijpleiding niet uitgeven.

## Verwijderen van pijpleidingen {#deleting-pipelines}

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op de ellipsieknoop naast de pijpleiding u in werking stelt selecteren **Verwijderen** in het menu.

>[!NOTE]
>
>U kunt geen lopende pijpleiding schrappen.

## Details van pipet weergeven {#view-details}

U kunt de details van een pijpleiding bekijken om de status en de logboeken van zijn laatste looppas te zien.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Pijpleidingen** kaart van **Programmaoverzicht** pagina en klik op de ellipsieknoop naast de pijpleiding u in werking stelt selecteren **Details weergeven** in het menu.

1. U wordt genomen aan de detailspagina van de lopende pijpleiding.

![Details pijpleiding](/help/implementing/cloud-manager/assets/configure-pipeline/pipeline-running-details.png)

Van hier kunt u het statuut van de diverse stappen van de pijpleiding zien en bouwstijllogboeken voor kenmerkende doeleinden terugwinnen. Zie het document [Uw code implementeren](/help/implementing/cloud-manager/deploy-code.md) voor meer informatie over codeplaatsing en tests in werking stellen.

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
