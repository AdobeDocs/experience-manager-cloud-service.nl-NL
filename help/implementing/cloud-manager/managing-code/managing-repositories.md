---
title: Opslagplaatsen in Cloud Manager beheren
description: Leer hoe u uw git-opslagruimten in Cloud Manager maakt, weergeeft en verwijdert.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 0%

---


# Opslagplaatsen in Cloud Manager beheren {#managing-repos}

Leer hoe u uw git-opslagruimten in Cloud Manager maakt, weergeeft en verwijdert.

## Overzicht {#overview}

Opslagplaatsen worden gebruikt om de code van uw project op te slaan en te beheren met behulp van Git. Voor elk programma dat u in Cloud Manager maakt, is een opslagplaats met beheerde Adobe gemaakt.

U kunt desgewenst extra opslagruimten voor Adobe-beheer maken en ook uw eigen persoonlijke opslagruimten toevoegen. Alle bewaarplaatsen verbonden aan uw programma kunnen in het **venster van Bewaarplaatsen** worden bekeken.

In Cloud Manager gemaakte opslagplaatsen kunnen ook worden geselecteerd wanneer u pijpleidingen toevoegt of bewerkt. Zie [ CI-CD Pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) om meer te leren.

Er is één enkele primaire bewaarplaats of een tak voor om het even welke bepaalde pijpleiding. Met [ de steun van de it submodule, ](git-submodules.md) vele secundaire takken kunnen bij bouwstijltijd worden omvat.

## Venster Opslagplaatsen {#repositories-window}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het Programma**, selecteer het **lusje van Bewaarplaatsen** om aan de **pagina van Bewaarplaatsen** over te schakelen.

1. Het **venster van Bewaarplaatsen** toont alle bewaarplaatsen verbonden aan uw programma.

   ![ venster van Bewaarplaatsen ](assets/repositories.png)

Het **venster van Bewaarplaatsen** verstrekt details over de bewaarplaatsen:

* Het type gegevensopslagruimte
   * **Adobe** wijst op Adobe-geleide bewaarplaatsen
   * **GitHub** wijst op privé bewaarplaatsen GitHub die u beheert
* Toen het werd gemaakt
* Pijpleidingen die zijn gekoppeld aan de opslagplaats

U kunt de repository selecteren in het venster en op de elliptische knop klikken om actie te ondernemen in de geselecteerde repository.

* **[de Tak van de Controle / leidt Project](#check-branches)** (slechts beschikbaar voor Adobe bewaarplaatsen)
* **[Repository URL van het Exemplaar](#copy-url)**
* **[Mening &amp; Update](#view-update)**
* **[Schrapping](#delete)**

![ de acties van de Bewaarplaats ](assets/repository-actions.png)

## Opslagplaatsen toevoegen {#adding-repositories}

Tik of klik **voeg de knoop van de Bewaarplaats** in het **venster van Bewaarplaatsen** toe om **te beginnen voeg de** tovenaar van de Bewaarplaats {toe.

![ toevoegen de tovenaar van de bewaarplaats ](assets/add-repository-wizard.png)

Cloud Manager steunt beide bewaarplaatsen die door Adobe (**worden beheerd de Bewaarplaats van de Adobe**) evenals uw zelf-beheerde bewaarplaatsen (**Privé Bewaarplaats**). De vereiste velden zijn afhankelijk van het type opslagplaats dat u wilt toevoegen. Raadpleeg de volgende documenten voor meer informatie.

* [Opslagplaatsen voor Adoben toevoegen in Cloud Manager](adobe-repositories.md)
* [Persoonlijke opslagplaatsen toevoegen in Cloud Manager](private-repositories.md)

>[!NOTE]
>
>* Een gebruiker moet de rol **Manager van de Plaatsing** of **BedrijfsEigenaar** hebben om een bewaarplaats toe te voegen.
>* Er geldt een limiet van 300 gegevensbanken voor alle programma&#39;s in een bepaalde onderneming of IMS-organisatie.

## Repo-info openen {#repo-info}

Wanneer het bekijken van uw bewaarplaatsen in het **** venster van Bewaarplaatsen {, kunt u de details op bekijken hoe te tot Adobe-geleide bewaarplaatsen programmatically toegang te hebben door te tikken of de **knoop van Info van de Reparatie van de Toegang** in de toolbar te klikken.

![ informatie van de Bewaarplaats ](assets/repo-info.png)

Het **venster van Info van de Bewaarplaats** opent met de details. Voor meer informatie bij de toegang tot van bewaarplaats informatie, zie gelieve het document [ Toegang hebbend tot de Informatie van de Bewaarplaats.](accessing-repos.md)

## Branches controleren / Project maken {#check-branches}

De **Tak van de Controle / leidt de actie van het Project** voert twee functies afhankelijk van de staat van de bewaarplaats uit.

* Als de bewaarplaats nieuw-gecreeerd is, leidt de actie tot een steekproefproject dat op [ wordt gebaseerd het AEM projectarchetype.](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview)
* Als de gegevensopslagplaats reeds het steekproefproject heeft gecreeerd, controleert het de staat van de bewaarplaats en zijn takken en meldt terug als het steekproefproject reeds bestaat.

![ de bijwerkingsacties van de Controle ](assets/check-branches.png)

## Repository-URL kopiëren {#copy-url}

De **actie van Repository URL van het Exemplaar** kopieert URL van de bewaarplaats die in het **venster van Bewaarplaatsen** aan het klembord wordt geselecteerd om elders te worden gebruikt.

## Weergeven en bijwerken {#view-update}

De **Mening &amp; van de Update** actie opent de **dialoog van de Bewaarplaats van de Update**. Gebruikend het kunt u de **Naam** bekijken en **Voorproef URL van de Bewaarplaats** evenals de **Beschrijving** van de bewaarplaats bijwerken.

![ Mening en update bewaarplaats informatie ](assets/view-update.png)

## Verwijderen {#delete}

De **schrapping** actie verwijdert de bewaarplaats uit uw project. Een opslagplaats kan niet worden geschrapt als het met een pijpleiding wordt geassocieerd.

![ Schrapping ](assets/delete.png)

Als u een opslagplaats verwijdert, gebeurt het volgende:

* Maak de verwijderde opslagplaats onbruikbaar voor nieuwe opslagplaatsen die in de toekomst kunnen worden gecreeerd.
   * In dergelijke gevallen wordt het foutbericht `Repository name should be unique within organization.` weergegeven.
* Maak de verwijderde opslagplaats niet beschikbaar in Cloud Manager en niet beschikbaar voor koppelingen naar pijpleidingen.
