---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe te om de functionaliteit van het Fragment van de Inhoud en van GraphQL in Browser van de Configuratie toe te laten om AEM koploze leveringseigenschappen te gebruiken.
feature: Content Fragments
role: User
hide: true
index: false
hidefromtoc: true
exl-id: 55d442ae-ae06-4dfa-8e4e-b415385ccea5
source-git-commit: 5ce5746026c5683e79cdc1c9dc96804756321cdb
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 3%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

<!--
hide: yes
index: no
hidefromtoc: yes
-->

Leer hoe te om specifieke functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Voordat u Inhoudsfragmenten kunt gebruiken, moet u de opdracht **Configuratiebrowser** inschakelen:

* **Modellen van inhoudsfragmenten** - verplicht
* **Aangehouden GraphQL-query&#39;s** - facultatief

>[!CAUTION]
>
>Als u niet inschakelt **Modellen van inhoudsfragmenten**:
>
>* de **Maken** is niet beschikbaar voor het maken van modellen.
>* u kunt [Selecteer de configuratie van Plaatsen om het verwante eindpunt tot stand te brengen](/help/headless/graphql-api/graphql-endpoint.md).

U moet het volgende doen om de functionaliteit van inhoudsfragmenten in te schakelen:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiesbrowser
* De configuratie toepassen op de map Middelen

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Bepaalde [Functionaliteit van inhoudsfragment](#creating-a-content-fragment-model), u **moet** eerst de **Configuratiebrowser**:

>[!NOTE]
>
>Zie voor meer informatie [Configuratiebrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Subconfiguraties](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (een configuratie die in een andere configuratie is genest), wordt volledig ondersteund voor gebruik met Content Fragments, Content Fragment Models en GraphQL query&#39;s.
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

1. Gebruiken **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel**.
   1. De **Naam** wordt de knooppuntnaam in de gegevensopslagruimte.
      * Deze wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies](/help/implementing/developing/introduction/naming-conventions.md).
      * U kunt deze desgewenst aanpassen.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **Aangehouden GraphQL-query&#39;s**

      ![Configuratie definiëren](assets/cfm-conf-01.png)

1. Selecteren **Maken** om de definitie op te slaan.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op uw map {#apply-the-configuration-to-your-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor de functionaliteit van inhoudsfragmenten, is het van toepassing op elke elementenmap die toegankelijk is via de **Activa** console.

Als u andere configuraties (behalve algemene configuraties) wilt gebruiken in een vergelijkbare map Elementen, moet u de verbinding definiëren. Deze verbinding wordt tot stand gebracht door de juiste **Configuratie** in de **Cloud Servicen** tabblad van het **Eigenschappen van map** van de desbetreffende map.

![Configuratie toepassen](assets/cfm-conf-02.png)
