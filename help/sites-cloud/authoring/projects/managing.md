---
title: Projecten beheren
description: De projecten laten u uw project organiseren door middelen in één entiteit te groeperen die in de console van Projecten kan worden betreden en worden geleid
exl-id: be4616e7-18bc-4b2d-89f6-d04178ac7f3a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '876'
ht-degree: 9%

---

# Projecten beheren {#managing-projects}

Met projecten kunt u uw project ordenen door bronnen in één entiteit te groeperen.

In de **console van Projecten**, hebt u toegang en handelt op uw projecten:

![ de console van Projecten ](/help/sites-cloud/authoring/assets/projects-console.png)

In Projecten, kunt u een project tot stand brengen, middelen met uw project associëren, en ook een project of verbindingen van het Middel schrappen. U kunt een tegel openen om de inhoud ervan weer te geven en items aan een tegel toe te voegen. In dit onderwerp worden deze procedures beschreven.

## Een project maken {#creating-a-project}

Uit de doos, verstrekt AEM deze malplaatjes om van te kiezen wanneer u een project creeert:

* Eenvoudig project
* Mediaproject
* Omzettingsproject

<!-- Hiding product photoshoot via cqdoc-18072 as it is not available in Skyline.
* Product Photo Shoot Project 
-->

De procedure om een project tot stand te brengen is voor alle projecten hetzelfde. Het verschil tussen de soorten projecten omvat beschikbare [gebruikersrollen](/help/sites-cloud/authoring/projects/overview.md) en [workflows](/help/sites-cloud/authoring/projects/workflows.md).  Een project maken:

1. In **Projecten**, uitgezochte **creeert** om **te openen creeer de** tovenaar van het Project:
1. Selecteer een malplaatje en klik **daarna**.

   ![ Creërend een project ](/help/sites-cloud/authoring/assets/projects-create.png)

1. Bepaal de **Titel** en **Beschrijving** en voeg het beeld van de a **Duimnagel** indien nodig toe. U kunt ook gebruikers toevoegen of verwijderen en tot welke groep zij behoren. Bovendien klik **Geavanceerd** om een naam toe te voegen die in URL wordt gebruikt.

   ![ Toevoegend projectdetail ](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Selecteer **Maken**. De bevestiging vraagt of wilt u uw nieuw project openen of aan de console terugkeren.

### Middelen koppelen aan uw project {#associating-resources-with-your-project}

Aangezien de projecten u toelaten om middelen in één entiteit te groeperen, wilt u middelen aan uw project associëren. Deze middelen worden genoemd **Tegels**. De soorten middelen u kunt toevoegen worden beschreven in [ Tegels van het Project ](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

Om middelen met uw project te associëren:

1. Open uw project van de **Projecten** console.
1. Selecteer **Tegel** toevoegen en de tegel selecteren die u aan uw project wilt verbinden. U kunt meerdere typen tegels selecteren.

   ![ Toevoegend een tegel aan een project ](/help/sites-cloud/authoring/assets/projects-add-tile.png)

   >[!NOTE]
   >
   >De tegels van het project die met een project kunnen worden geassocieerd worden beschreven in [ tegels van het Project ](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

1. Selecteer **Maken**. Uw bron is gekoppeld aan uw project en vanaf nu hebt u toegang tot deze bron vanuit uw project.

### Een project- of bronnenkoppeling verwijderen {#deleting-a-project-or-resource-link}

De zelfde methode wordt gebruikt om een project van de console of een verbonden middel van uw project te schrappen:

1. Navigeer naar de juiste locatie:

   * Om een project te schrappen gaat naar het hoogste niveau van de **console van Projecten**.
   * Om een middelverbinding binnen een project te schrappen, open uw project in de **console van Projecten**.

1. Ga selectiewijze door **Uitgezocht** te klikken en uw project of middelverbinding te selecteren.
1. Selecteer **Schrapping**.

1. U moet de verwijdering bevestigen in een dialoogvenster. Indien bevestigd, wordt het project of de middelverbinding geschrapt. Selecteer **Deselecteer** om selectiewijze weg te gaan.

>[!NOTE]
>
>Wanneer u het project creëert en gebruikers aan de verschillende rollen toevoegt, worden de groepen die aan het project gekoppeld zijn, automatisch gecreëerd om bijbehorende machtigingen te beheren. Bijvoorbeeld: een project met de naam Mijn project zou drie groepen hebben: **Mijn projecteigenaars**, **Mijn projecteditors**, **Mijn projectwaarnemers**. Als het project echter wordt verwijderd, worden deze groepen niet automatisch verwijderd. Een beheerder moet de groepen in **Hulpmiddelen** manueel schrappen > **Veiligheid** > **Groepen**.

### Items toevoegen aan een tegel {#adding-items-to-a-tile}

In sommige tegels wilt u mogelijk meerdere items toevoegen. U kunt bijvoorbeeld meer dan één workflow tegelijk uitvoeren of meer dan één ervaring.

Items toevoegen aan een tegel:

1. In **Projecten**, navigeer aan het project en selecteer onderaan chevron op de tegel u een punt aan wilt toevoegen.

   ![ voeg punt aan een tegel ](/help/sites-cloud/authoring/assets/project-workflows.png) toe

1. Voeg een item aan de tegel toe zoals u dat zou doen bij het maken van een tegel. Zie [ tegels van het Project ](/help/sites-cloud/authoring/projects/overview.md#project-tiles) voor meer details. In dit voorbeeld is een andere workflow toegevoegd.

### Een tegel openen {#opening-a-tile}

Mogelijk wilt u zien welke items zijn opgenomen in een huidige tegel, of wilt u items wijzigen of verwijderen in de tegel.

Een tegel openen zodat u items kunt weergeven of wijzigen:

1. In de console van Projecten, selecteer de ellipsen (...) pictogram bij de bodem van de kaart.

   ![ die een tegel ](/help/sites-cloud/authoring/assets/project-links.png) openen

1. AEM geeft de items in die tegel weer. U kunt de selectiemodus activeren om de items te wijzigen of te verwijderen.

   ![ Geopende Tegel ](/help/sites-cloud/authoring/assets/projects-add-link.png)

## Projectstatistieken weergeven {#viewing-project-statistics}

U kunt projectstatistieken, in de **Projecten** console bekijken.

### Een projecttijdlijn weergeven {#viewing-a-project-timeline}

De projecttijdlijn biedt informatie over wanneer de elementen in het project het laatst zijn gebruikt. Om de projectchronologie te bekijken, selecteer **Chronologie**, dan ga selectiewijze in en selecteer het project. Assets wordt weergegeven in het linkerdeelvenster. Selecteer **Chronologie** om aan de **Projecten** console terug te keren.

![ de chronologie van het Project ](/help/sites-cloud/authoring/assets/projects-timeline.png)

### Actieve/Inactieve projecten weergeven {#viewing-active-inactive-projects}

Om tussen uw actieve en inactieve projecten, in de **console van Projecten** van een knevel te voorzien, klik **de Actieve Projecten** van de knevel. Als er naast het pictogram een vinkje staat, worden de actieve projecten weergegeven.

![ Wissel Actieve knoop van Projecten ](/help/sites-cloud/authoring/assets/projects-active.png)

Als het pictogram een x naast heeft, toont het de inactieve projecten.

![ knevel Inactieve knoop van Projecten ](/help/sites-cloud/authoring/assets/projects-inactive.png)

## Projecten inactief of actief maken {#making-projects-inactive-or-active}

U kunt een project willen inactief maken als u het hebt voltooid maar u wilt nog de informatie over het project houden.

Een project inactief (of actief) maken:

1. In de **console van Projecten**, open uw project en vind dan de **informatie van het Project** tegel.

   >[!NOTE]
   >
   Mogelijk moet u deze tegel toevoegen als deze nog niet in uw project staat. Zie [ Toevoegend Tegels ](#adding-items-to-a-tile).

1. Selecteer **uitgeven**.
1. Verander de selecteur van **Actieve** in **Inactieve** (of omgekeerd).

   ![ het Activeren van een project ](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Selecteer **Gedaan** om uw veranderingen te bewaren.
