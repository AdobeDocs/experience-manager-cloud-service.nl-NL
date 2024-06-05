---
title: Projecten beheren
description: De projecten laten u uw project organiseren door middelen in één entiteit te groeperen die in de console van Projecten kan worden betreden en worden geleid
exl-id: be4616e7-18bc-4b2d-89f6-d04178ac7f3a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 9%

---

# Projecten beheren {#managing-projects}

Met projecten kunt u uw project ordenen door bronnen in één entiteit te groeperen.

In de **Projecten** console, hebt toegang tot en handelt u op uw projecten:

![De projectenconsole](/help/sites-cloud/authoring/assets/projects-console.png)

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

1. In **Projecten**, selecteert u **Maken** om de **Project maken** wizard:
1. Selecteer een sjabloon en klik op **Volgende**.

   ![Een project maken](/help/sites-cloud/authoring/assets/projects-create.png)

1. Definieer de **Titel** en **Beschrijving** en voeg een **Miniatuur** afbeelding, indien nodig. U kunt ook gebruikers toevoegen of verwijderen en tot welke groep zij behoren. Klik bovendien op **Geavanceerd** om een naam toe te voegen die in URL wordt gebruikt.

   ![Projectdetails toevoegen](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Selecteer **Maken**. De bevestiging vraagt of wilt u uw nieuw project openen of aan de console terugkeren.

### Middelen koppelen aan uw project {#associating-resources-with-your-project}

Aangezien de projecten u toelaten om middelen in één entiteit te groeperen, wilt u middelen aan uw project associëren. Deze bronnen worden **Tegels**. De typen bronnen die u kunt toevoegen, worden beschreven in [Projectblokken](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

Om middelen met uw project te associëren:

1. Open uw project vanuit de **Projecten** console.
1. Selecteren **Tegel toevoegen** en selecteer de tegel die u aan uw project wilt koppelen. U kunt meerdere typen tegels selecteren.

   ![Een tegel toevoegen aan een project](/help/sites-cloud/authoring/assets/projects-add-tile.png)

   >[!NOTE]
   >
   >De tegels van het project die met een project kunnen worden geassocieerd worden beschreven in detail [Projectelementen](/help/sites-cloud/authoring/projects/overview.md#project-tiles).

1. Selecteer **Maken**. Uw bron is gekoppeld aan uw project en vanaf nu hebt u toegang tot deze bron vanuit uw project.

### Een project- of bronnenkoppeling verwijderen {#deleting-a-project-or-resource-link}

De zelfde methode wordt gebruikt om een project van de console of een verbonden middel van uw project te schrappen:

1. Navigeer naar de juiste locatie:

   * Als u een project wilt verwijderen, gaat u naar het hoofdniveau van het dialoogvenster **Projecten** console.
   * Om een middelverbinding binnen een project te schrappen, open uw project in **Projecten** console.

1. Selectiemodus openen door te klikken **Selecteren** en het selecteren van uw project of middelverbinding.
1. Selecteren **Verwijderen**.

1. U moet de verwijdering bevestigen in een dialoogvenster. Indien bevestigd, wordt het project of de middelverbinding geschrapt. Selecteren **Deselecteren** om de selectiemodus af te sluiten.

>[!NOTE]
>
>Wanneer u het project creëert en gebruikers aan de verschillende rollen toevoegt, worden de groepen die aan het project gekoppeld zijn, automatisch gecreëerd om bijbehorende machtigingen te beheren. Bijvoorbeeld: een project met de naam Mijn project zou drie groepen hebben: **Mijn projecteigenaars**, **Mijn projecteditors**, **Mijn projectwaarnemers**. Als het project echter wordt verwijderd, worden deze groepen niet automatisch verwijderd. Een beheerder moet de groepen in **Gereedschappen** > **Beveiliging** > **Groepen**.

### Items toevoegen aan een tegel {#adding-items-to-a-tile}

In sommige tegels wilt u mogelijk meerdere items toevoegen. U kunt bijvoorbeeld meer dan één workflow tegelijk uitvoeren of meer dan één ervaring.

Items toevoegen aan een tegel:

1. In **Projecten**, navigeert u naar het project en selecteert u het keuzerondje omlaag op de tegel waaraan u een item wilt toevoegen.

   ![Item toevoegen aan een tegel](/help/sites-cloud/authoring/assets/project-workflows.png)

1. Voeg een item aan de tegel toe zoals u dat zou doen bij het maken van een tegel. Projectelementen worden beschreven [hier](/help/sites-cloud/authoring/projects/overview.md#project-tiles). In dit voorbeeld is een andere workflow toegevoegd.

### Een tegel openen {#opening-a-tile}

Mogelijk wilt u zien welke items zijn opgenomen in een huidige tegel, of wilt u items wijzigen of verwijderen in de tegel.

Een tegel openen zodat u items kunt weergeven of wijzigen:

1. In de console van Projecten, selecteer de ellipsen (...) pictogram bij de bodem van de kaart.

   ![Een tegel openen](/help/sites-cloud/authoring/assets/project-links.png)

1. AEM geeft de items in die tegel weer. U kunt de selectiemodus activeren om de items te wijzigen of te verwijderen.

   ![Tegel geopend](/help/sites-cloud/authoring/assets/projects-add-link.png)

## Projectstatistieken weergeven {#viewing-project-statistics}

U kunt projectstatistieken bekijken, in **Projecten** console.

### Een projecttijdlijn weergeven {#viewing-a-project-timeline}

De projecttijdlijn biedt informatie over wanneer de elementen in het project het laatst zijn gebruikt. Als u de projecttijdlijn wilt weergeven, selecteert u **Tijdlijn**, dan ga selectiewijze in en selecteer het project. Elementen worden weergegeven in het linkervenster. Selecteren **Tijdlijn** om terug te keren naar de **Projecten** console.

![Tijdlijn project](/help/sites-cloud/authoring/assets/projects-timeline.png)

### Actieve/Inactieve projecten weergeven {#viewing-active-inactive-projects}

Om tussen uw actieve en inactieve projecten, in te schakelen **Projecten** console, klik **Actieve projecten in-/uitschakelen**. Als er naast het pictogram een vinkje staat, worden de actieve projecten weergegeven.

![Knop Actieve projecten in-/uitschakelen](/help/sites-cloud/authoring/assets/projects-active.png)

Als het pictogram een x naast heeft, toont het de inactieve projecten.

![Knop Inactieve projecten in-/uitschakelen](/help/sites-cloud/authoring/assets/projects-inactive.png)

## Projecten inactief of actief maken {#making-projects-inactive-or-active}

U kunt een project willen inactief maken als u het hebt voltooid maar u wilt nog de informatie over het project houden.

Een project inactief (of actief) maken:

1. In de **Projecten** console, open uw project en dan vind **Projectinformatie** tegel.

   >[!NOTE]
   >
   Mogelijk moet u deze tegel toevoegen als deze nog niet in uw project staat. Zie [Tegels toevoegen](#adding-items-to-a-tile).

1. Selecteren **Bewerken**.
1. De kiezer wijzigen vanuit **Actief** tot **Inactief** (of omgekeerd).

   ![Een project activeren](/help/sites-cloud/authoring/assets/projects-add-team.png)

1. Selecteren **Gereed** om uw wijzigingen op te slaan.
