---
title: Wizard Project maken
description: Leer over de tovenaar van de projectverwezenlijking om u te helpen snel opstelling uw project na het creëren van uw productieprogramma.
exl-id: 03736ca7-1345-4faf-a61a-f9213ab5c89a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Wizard Project maken {#project-creation-wizard}

Nadat u uw productieprogramma hebt gemaakt, biedt Cloud Manager een wizard om een minimale AEM te maken op basis van de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) om snel aan de slag te gaan.

Voer de volgende stappen uit om een AEM toepassingsproject te maken in Cloud Manager met de wizard.

1. Een productieprogramma maken door de stappen in het document uit te voeren [Productieprogramma&#39;s maken](creating-production-programs.md)

1. Zodra de opstelling van het programma volledig is, heb toegang tot **Overzicht** scherm van uw programma en zie **Tak en project maken** vraag-aan-actie kaart bij de bovenkant.

   ![Vraag-aan-actie zorg voor de tovenaar](assets/create-wizard1.png)

1. Klikken **Maken** om de wizard te starten en de **Titel** en **Nieuwe naam vertakking** in de **Een vertakking en project maken** venster.

   ![Een vertakking en project maken](assets/create-wizard2.png)

1. Klik optioneel op de scheidingslijn om de aanvullende parameters van uw project weer te geven. De standaardwaarden worden verstrekt door het AEM Project Archetype en over het algemeen te hoeven niet worden veranderd.

   ![Aanvullende projectparameters](assets/create-wizard5.png)

1. Klikken **Maken** het aanmaakproces van het project te starten.


A **Project wordt gemaakt.** de kaart vervangt nu de **Tak en project maken** call-to-action kaart als bovenkant van **Programmaoverzicht** scherm.

![Project wordt gemaakt](assets/create-wizard3.png)

Wanneer het programma is gemaakt, kunt u **Omgeving toevoegen** de kaart vervangt **Project wordt gemaakt.** kaart boven aan **Programmaoverzicht** scherm.

![Omgeving toevoegen](assets/create-wizard4.png)

U hebt nu een AEM project gebaseerd op het AEM archetype dat aan uw git bewaarplaats wordt toegevoegd als basis voor ontwikkeling voor uw eigen project. Daarna kunt u uw milieu&#39;s tot stand brengen waar u de projectcode kunt opstellen.

Zie [Uw omgevingen beheren](/help/implementing/cloud-manager/manage-environments.md) om te leren hoe u omgevingen kunt toevoegen of beheren.

>[!NOTE]
>
>De wizard is alleen beschikbaar voor productieprogramma&#39;s. Omdat [sandboxprogramma&#39;s](introduction-sandbox-programs.md#auto-creation) Als u een automatisch project wilt maken, is de wizard niet nodig.