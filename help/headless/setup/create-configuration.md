---
title: Een configuratie maken - installatie zonder kop
description: Een configuratie maken als eerste stap om in AEM as a Cloud Service met een headless-functie aan de slag te gaan.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Een configuratie maken - installatie zonder kop {#creating-configuration}

Als eerste stap om in AEM as a Cloud Service aan de slag te gaan met headless, moet u een configuratie tot stand brengen.

## Wat is een Configuratie? {#what-is-a-configuration}

Browser van de Configuratie verstrekt een generische configuratie API, inhoudsstructuur, resolutiemechanisme voor configuraties in AEM.

In de context van het beheer van inhoud zonder kop in AEM, denk aan een configuratie als werkplaats binnen AEM waar u uw Modellen van de Inhoud kunt tot stand brengen, die de structuur van uw toekomstige inhoud en de Fragmenten van de Inhoud bepalen. U kunt veelvoudige configuraties hebben om deze modellen te scheiden.

Als u met [ paginasjablonen in een volledig-stapel AEM implementatie vertrouwd bent, ](/help/sites-cloud/authoring/sites-console/templates.md) is het gebruik van configuraties voor het beheer van Content Models gelijkaardig.

## Hoe te om een Configuratie te creëren {#how-to-create-a-configuration}

Een beheerder zou slechts één keer een configuratie moeten tot stand brengen, of zeer seldomly wanneer een nieuwe werkruimte voor het organiseren van uw Modellen van de Inhoud wordt vereist. Voor deze gids aan de slag, moeten wij slechts één configuratie tot stand brengen.

1. Logboek in AEM as a Cloud Service en van het belangrijkste menu selecteert **Hulpmiddelen > Algemeen > Browser van de Configuratie**.
1. Verstrek a **Titel** en a **Naam** voor uw configuratie.
   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** wordt de knoopnaam in de bewaarplaats.
      * Het wordt automatisch geproduceerd gebaseerd op de titel en aangepast volgens [ AEM noemende overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md).
      * Deze kan zo nodig worden aangepast.
1. Controleer de volgende opties:
   * **Modellen van contentfragmenten**
   * **GraphQL Blijven Vragen**

   ![ creeer Configuratie ](../assets/create-configuration.png)

1. Selecteer **creëren**

U kunt indien nodig meerdere configuraties maken. Configuraties kunnen ook worden genest.

>[!NOTE]
>
>De opties van de configuratie naast **Modellen van het Fragment van de Inhoud** en **de Verlengde Vragen van GraphQL** kunnen afhankelijk van uw implementatievereisten noodzakelijk zijn.

## Volgende stappen {#next-steps}

Gebruikend deze configuratie, kunt u zich nu op het tweede deel van begonnen gids bewegen en [ creeer de Modellen van het Fragment van de Inhoud.](create-content-model.md)

>[!TIP]
>
>Voor volledige details over Browser van de Configuratie, [ zie de Browser van de Configuratie documentatie ](/help/implementing/developing/introduction/configurations.md).
