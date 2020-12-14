---
title: Creërend een Hoofdloze Gids van het Begin van de Configuratie
description: Als eerste stap om met hoofdloze in AEM als Cloud Service begonnen te worden, moet u een configuratie tot stand brengen.
translation-type: tm+mt
source-git-commit: 259d54a225f8dee5929f62b784e28f3fc2bb794a
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Creërend een Hoofdloze Gids van het Begin van de Configuratie {#creating-configuration}

Als eerste stap om met hoofdloze in AEM als Cloud Service begonnen te worden, moet u een configuratie tot stand brengen.

## Wat is een Configuratie? {#what-is-a-configuration}

Browser van de Configuratie verstrekt een generische configuratie API, inhoudsstructuur, resolutiemechanisme voor configuraties in AEM.

In de context van het beheer van inhoud zonder kop in AEM, denk aan een configuratie als werkplaats binnen AEM waar u uw Modellen van de Inhoud kunt tot stand brengen, die de structuur van uw toekomstige inhoud en de Fragmenten van de Inhoud bepalen. U kunt veelvoudige configuraties hebben om deze modellen te scheiden.

Als u met [paginasjablonen in een full-stack AEM implementatie vertrouwd bent,](/help/sites-cloud/authoring/features/templates.md) is het gebruik van configuraties voor het beheer van Content Models vergelijkbaar.

## Hoe te om een Configuratie {#how-to-create-a-configuration} te creëren

Een beheerder zou slechts één keer een configuratie moeten tot stand brengen, of zeer seldomly wanneer een nieuwe werkruimte voor het organiseren van uw Modellen van de Inhoud wordt vereist. Voor deze gids aan de slag, moeten wij slechts één configuratie tot stand brengen.

1. Meld u aan bij AEM als Cloud Service en selecteer **Gereedschappen -> Algemeen -> Configuratiebrowser** in het hoofdmenu.
1. Geef een **Titel** en een **Naam** op voor uw configuratie.
   * De **Titel** zou beschrijvend moeten zijn.
   * De **Naam** wordt de knooppuntnaam in de repository.
      * Deze wordt automatisch gegenereerd op basis van de titel en aangepast volgens de naamconventies [AEM.](/help/implementing/developing/introduction/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.
1. Controleer de volgende opties:
   * **Modellen van contentfragmenten**
   * **GrafiekQL blijvende vragen**

   ![Configuratie maken](../assets/create-configuration.png)

1. Tik of klik op **Maken**

Indien nodig kunt u meerdere configuraties maken. Configuraties kunnen ook worden genest.

>[!NOTE]
>
>De opties van de configuratie naast **de Modellen van het Fragment van de Inhoud** en **GrahQL Persistent Vragen** kunnen afhankelijk van uw implementatievereisten noodzakelijk zijn.

## Volgende stappen {#next-steps}

Met deze configuratie kunt u nu naar het tweede deel van de gids Aan de slag gaan en [Modellen van inhoudsfragmenten maken.](create-content-model.md)

>[!TIP]
>
>Voor volledige details over Browser van de Configuratie, [zie de Browser van de Configuratie documentatie.](/help/implementing/developing/introduction/configurations.md)
