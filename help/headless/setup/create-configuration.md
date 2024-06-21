---
title: Een configuratie maken - installatie zonder kop
description: Creeer een configuratie als eerste stap aan het worden begonnen met hoofdloos in AEM as a Cloud Service.
exl-id: 48801599-f279-4e55-8033-9c418d2af5bb
feature: Headless, Content Fragments,GraphQL API
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# Een configuratie maken - installatie zonder kop {#creating-configuration}

Als eerste stap om met hoofdloze in AEM as a Cloud Service te worden begonnen, moet u een configuratie tot stand brengen.

## Wat is een Configuratie? {#what-is-a-configuration}

Browser van de Configuratie verstrekt een generische configuratie API, inhoudsstructuur, resolutiemechanisme voor configuraties in AEM.

In de context van het beheer van inhoud zonder kop in AEM, denk aan een configuratie als werkplaats binnen AEM waar u uw Modellen van de Inhoud kunt tot stand brengen, die de structuur van uw toekomstige inhoud en de Fragmenten van de Inhoud bepalen. U kunt veelvoudige configuraties hebben om deze modellen te scheiden.

Als u vertrouwd bent met [paginasjablonen in een volledige AEM-implementatie,](/help/sites-cloud/authoring/sites-console/templates.md) het gebruik van configuraties voor het beheer van inhoudsmodellen is vergelijkbaar.

## Hoe te om een Configuratie te creëren {#how-to-create-a-configuration}

Een beheerder zou slechts één keer een configuratie moeten tot stand brengen, of zeer seldomly wanneer een nieuwe werkruimte voor het organiseren van uw Modellen van de Inhoud wordt vereist. Voor deze gids aan de slag, moeten wij slechts één configuratie tot stand brengen.

1. Log in AEM as a Cloud Service en selecteer in het hoofdmenu **Gereedschappen > Algemeen > Configuratiebrowser**.
1. Geef een **Titel** en **Naam** voor uw configuratie.
   * De **Titel** moeten beschrijvend zijn.
   * De **Naam** wordt de knooppuntnaam in de gegevensopslagruimte.
      * Deze wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies](/help/implementing/developing/introduction/naming-conventions.md).
      * Deze kan zo nodig worden aangepast.
1. Controleer de volgende opties:
   * **Modellen van contentfragmenten**
   * **Aangehouden GraphQL-query&#39;s**

   ![Configuratie maken](../assets/create-configuration.png)

1. Selecteren **Maken**

U kunt indien nodig meerdere configuraties maken. Configuraties kunnen ook worden genest.

>[!NOTE]
>
>Configuratieopties naast **Modellen van inhoudsfragmenten** en **Aangehouden GraphQL-query&#39;s** kan nodig zijn, afhankelijk van uw implementatievereisten.

## Volgende stappen {#next-steps}

Met deze configuratie kunt u nu naar het tweede deel van de gids Aan de slag gaan en [Maak Content Fragment Models.](create-content-model.md)

>[!TIP]
>
>Voor volledige details over Browser van de Configuratie, [zie de Browser van de Configuratie documentatie](/help/implementing/developing/introduction/configurations.md).
