---
title: Opslagplaatsen in Cloud Manager beheren
description: Leer hoe u Git-opslagruimten in Cloud Manager toevoegt, weergeeft en verwijdert.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---


# repositories beheren in Cloud Manager {#managing-repos}

Leer hoe u uw git-opslagruimten in Cloud Manager kunt weergeven, toevoegen en verwijderen.

## Over opslagruimten in Cloud Manager {#overview}

Opslagplaatsen in Cloud Manager worden gebruikt om de projectcode op te slaan en te beheren met Git. Voor elk *programma* u toevoegt, wordt een Adobe-Beheerde bewaarplaats automatisch gecreeerd.

Daarnaast kunt u meer door Adobe beheerde opslagruimten maken of uw eigen persoonlijke opslagruimten toevoegen. Alle bewaarplaatsen verbonden aan uw programma kunnen op de **pagina van Bewaarplaatsen** worden bekeken.

In Cloud Manager gemaakte opslagplaatsen kunnen ook worden geselecteerd bij het toevoegen of bewerken van pijpleidingen. Voor meer informatie bij het vormen van pijpleidingen, zie [&#x200B; CI-CD Pijpleidingen &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Elke pijpleiding is verbonden met een primaire bewaarplaats of tak. Nochtans, met [&#x200B; submodule van de Git steun &#x200B;](git-submodules.md), kunnen de veelvoudige secundaire takken tijdens het bouwstijlproces worden omvat.

## De pagina Opslagplaatsen weergeven {#repositories-window}

Op de **pagina van Bewaarplaatsen**, kunt u details over de geselecteerde bewaarplaats bekijken. Deze informatie omvat het type opslagplaats dat in gebruik is. Als de bewaarplaats als **Adobe** duidelijk is, wijst het erop dat het een Adobe-Beheerde bewaarplaats is. Als het als **GitHub** wordt geëtiketteerd, verwijst het naar een privé bewaarplaats GitHub die u beheert. Daarnaast bevat de pagina gegevens zoals wanneer de opslagplaats is gemaakt en de bijbehorende pijpleidingen.

Om actie op een geselecteerde bewaarplaats te ondernemen, kunt u op de bewaarplaats klikken en ![&#x200B; Meer pictogram &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) gebruiken om een drop-down menu te openen. Voor Adobe-Beheerde bewaarplaatsen, kunt u **[Tanden controleren / Project creëren](#check-branches)**.

![&#x200B; de acties van de Bewaarplaats &#x200B;](assets/repository-actions.png)
*drop-down menu op de pagina van Bewaarplaatsen.*

Andere beschikbare acties op het drop-down menu omvatten **[Repository URL van het Exemplaar](#copy-url)**, **[Mening &amp; Update](#view-update)**, en **[Schrapping](#delete)** de bewaarplaats.

**om de pagina van Bewaarplaatsen te bekijken:**

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Van de **pagina van het Overzicht van het 0&rbrace; Programma, op het zijmenu, klik** pictogram van de Omslag ![&#x200B; &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) Bewaarplaatsen **.**

1. De **pagina van Bewaarplaatsen** toont alle bewaarplaatsen verbonden aan uw geselecteerd programma.

   ![&#x200B; pagina van Bewaarplaatsen &#x200B;](assets/repositories.png)
   *de pagina van Bewaarplaatsen in Cloud Manager.*

## Een opslagplaats toevoegen {#adding-repositories}

Een gebruiker moet de rol **Manager van de Plaatsing** of **BedrijfsEigenaar** hebben om een bewaarplaats toe te voegen.

Op de **pagina van Bewaarplaatsen**, dichtbij de hoger-juiste hoek, klik **Add Bewaarplaats**

![&#x200B; toevoegen de dialoogdoos van de bewaarplaats &#x200B;](assets/repository-add.png)
*voeg de dialoogdoos van de Bewaarplaats toe.*

Cloud Manager steunt twee types van bewaarplaatsen: Adobe-Beheerde bewaarplaatsen (**Adobe Bewaarplaats**) en zelfbeheerde bewaarplaatsen (**Privé Bewaarplaats**). De vereiste velden voor installatie zijn afhankelijk van het type opslagplaats dat u wilt toevoegen. Raadpleeg de volgende secties voor meer informatie:

* [Adobe-opslagplaatsen toevoegen in Cloud Manager](adobe-repositories.md)
* [Persoonlijke opslagruimten toevoegen in Cloud Manager](private-repositories.md)

Er geldt een limiet van 300 gegevensbanken voor alle programma&#39;s in een bepaalde onderneming of IMS-organisatie.

## Gegevens uit de gegevensopslagplaats {#repo-info}

Wanneer het bekijken van uw bewaarplaatsen in het **&#x200B;**&#x200B;venster van Bewaarplaatsen &lbrace;, kunt u de details op bekijken hoe te tot de Adobe-Beheerde bewaarplaatsen programmatically toegang te hebben door de **knoop van Info van de Reparatie van de Toegang** op de toolbar te klikken.

![&#x200B; informatie van de Bewaarplaats &#x200B;](assets/repository-access-repo-info2.png)

Het **venster van Info van de Bewaarplaats** opent met de details. Voor meer informatie bij de toegang tot van bewaarplaats informatie, zie [&#x200B; Toegang tot de Informatie van de Bewaarplaats &#x200B;](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

## Branches controleren / Project maken {#check-branches}

In **AEM Cloud Manager**, de **Tak van de Controle / creeer de actie van het Project** dient twee doeleinden, afhankelijk van de huidige staat van de bewaarplaats.

* Als de bewaarplaats nieuw wordt gecreeerd, produceert deze actie een steekproefproject gebruikend [&#x200B; het het projectarchetype van AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview).
* Als het voorbeeldproject reeds in de bewaarplaats wordt gecreeerd, controleert de actie de status van de bewaarplaats en zijn takken, die terugkoppelen op of het steekproefproject reeds bestaat.

  ![&#x200B; de bijwerkingsacties van de Controle &#x200B;](assets/check-branches.png)

## Repository-URL kopiëren {#copy-url}

De **actie van Repository URL van het Exemplaar van de Bewaarplaats** kopieert URL van de bewaarplaats die in de **wordt geselecteerd Repositories** pagina aan het klembord dat elders moet worden gebruikt.

## Een opslagplaats weergeven en bijwerken {#view-update}

De **Mening &amp; van de Update** actie opent de **Repository van de Update** dialoogdoos, waar u de 4&rbrace; Naam van de bewaarplaats **en** Voorproef van Repository URL van de Bewaarplaats **kunt bekijken.** Bovendien, laat het u de **Beschrijving** van de bewaarplaats bijwerken.

![&#x200B; Mening en update bewaarplaats informatie &#x200B;](assets/repository-view-update.png)

## Een opslagplaats verwijderen {#delete}

De **schrapping** actie verwijdert de bewaarplaats uit uw project. Een opslagplaats kan niet worden geschrapt als het met een pijpleiding wordt geassocieerd.

![&#x200B; Schrapping &#x200B;](assets/repository-delete.png)

Als u een opslagplaats verwijdert, wordt de naam onbruikbaar voor nieuwe opslagplaatsen die in de toekomst worden gemaakt. Als u probeert een gegevensopslagruimte toe te voegen met dezelfde naam als een verwijderde gegevensopslagruimte, wordt het volgende foutbericht weergegeven:

`Repository name should be unique within organization.`

Bovendien is de verwijderde opslagplaats niet meer beschikbaar in Cloud Manager en kan deze niet worden gekoppeld aan pijpleidingen.

