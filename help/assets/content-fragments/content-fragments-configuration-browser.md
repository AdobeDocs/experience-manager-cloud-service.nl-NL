---
title: Inhoudsfragmenten - Configuratiebrowser (Assets - Inhoudsfragmenten)
description: Leer hoe te om de functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten.
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
feature: Content Fragments
role: User, Admin, Developer
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM het gebruiken van krachtige koploze leveringseigenschappen te gebruiken.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Alvorens Inhoudsfragmenten te gebruiken, moet u **Browser van de Configuratie** gebruiken om toe te laten:

* **Modellen van het Fragment van de Inhoud** - verplicht
* **GraphQL Blijven Vragen** - facultatief

>[!CAUTION]
>
>Als u niet **Modellen van het Fragment van de Inhoud** toelaat:
>
>* **creeer** optie is niet beschikbaar voor het creëren van modellen.
>* u kunt niet [ de configuratie van Plaatsen selecteren om het verwante eindpunt ](/help/headless/graphql-api/graphql-endpoint.md) tot stand te brengen.

U moet het volgende doen om de functionaliteit van inhoudsfragmenten in te schakelen:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiebrowser
* De configuratie toepassen op uw Assets-map

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Om bepaalde [ functionaliteit van het Fragment van de Inhoud ](#creating-a-content-fragment-model) te gebruiken, moet u **** eerst hen als **Browser van de Configuratie** toelaten:

>[!NOTE]
>
>Zie [ Browser van de Configuratie ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[ Subconfiguration ](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (een configuratie die binnen een andere configuratie wordt genest) wordt volledig gesteund voor gebruik met de Fragmenten van de Inhoud, Modellen van het Fragment van de Inhoud en de vragen van GraphQL.
>
>Ik wil alleen opmerken dat:
>
>
>* Na het creëren van modellen in een subconfiguration, is het NIET mogelijk om het model aan een andere subconfiguration te bewegen of te kopiëren.
>
>* Een eindpunt van GraphQL is (nog) gebaseerd op een ouder (wortel) configuratie.
>
>* Blijvende query&#39;s worden (nog) opgeslagen als relevant voor de bovenliggende (basis)configuratie.


1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Het gebruik **creeert** om de dialoog te openen, waar u:

   1. Specificeer a **Titel**.
   1. De **Naam** wordt de knoopnaam in de bewaarplaats.
      * Het wordt automatisch geproduceerd gebaseerd op de titel en aangepast volgens [ AEM noemende overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md).
      * U kunt deze desgewenst aanpassen.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **GraphQL Blijven Vragen**

      ![ bepaalt configuratie ](assets/cfm-conf-01.png)

1. Selecteer **creeer** om de definitie te bewaren.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op uw Assets-map {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globale** voor de functionaliteit van het inhoudsfragment wordt toegelaten, dan op om het even welke omslag van Assets van toepassing is.

Als u andere configuraties (behalve algemene configuraties) wilt gebruiken in een vergelijkbare Assets-map, moet u de verbinding definiëren. Deze verbinding wordt gedaan door de aangewezen **Configuratie** in het **Cloud Servicen** lusje van de **Eigenschappen van de Omslag** van de aangewezen omslag te selecteren.

![ pas configuratie ](assets/cfm-conf-02.png) toe
