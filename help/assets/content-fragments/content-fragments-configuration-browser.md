---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.
feature: Content Fragments
role: User
exl-id: 9fc911de-1d33-4811-8f58-ea21ce94bedb
source-git-commit: 78448aafa1b397f9131c12ab2afd74b05ae53e66
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 15%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe te om bepaalde functionaliteit van het Fragment van de Inhoud in Browser van de Configuratie toe te laten om AEM krachtige koploze leveringseigenschappen te gebruiken.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Voordat u Inhoudsfragmenten kunt gebruiken, moet u de opdracht **Configuratiebrowser** inschakelen:

* **Modellen van inhoudsfragmenten** - verplicht
* **GrafiekQL blijvende vragen** - facultatief

>[!CAUTION]
>
>Als u deze optie niet inschakelt **Modellen van inhoudsfragmenten**:
>
>* de **Maken** Deze optie is niet beschikbaar voor het maken van nieuwe modellen.
>* u kunt niet [Selecteer de configuratie van Plaatsen om het verwante eindpunt tot stand te brengen](/help/headless/graphql-api/graphql-endpoint.md).


Voor het inschakelen van de functionaliteit voor inhoudsfragmenten moet u:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiesbrowser
* De configuratie toepassen op de map Middelen

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Naar [bepaalde functionaliteit van inhoudsfragmenten gebruiken](#creating-a-content-fragment-model) u **moet** ze eerst via de **Configuratiebrowser**:

>[!NOTE]
>
>Zie ook voor meer informatie [Configuratiebrowser:](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Subconfiguraties](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (een configuratie die in een andere configuratie is genest), wordt volledig ondersteund voor gebruik met Content Fragments, Content Fragment Models en GraphQL-query&#39;s.
>
>Ik wil alleen opmerken dat:
>
>
>* Na het creëren van modellen in een subconfiguratie, is het NIET mogelijk om het model naar een andere subconfiguratie te bewegen of te kopiëren.
>
>* Een eindpunt GraphQL zal (nog) op een ouder (wortel) configuratie worden gebaseerd.
>
>* Blijvende query&#39;s worden (nog) als relevant voor de bovenliggende (basis)configuratie opgeslagen.



1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Gebruiken **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel**.
   1. Selecteer
      * **Modellen van contentfragmenten**
      * **GrafiekQL blijvende vragen**

      ![Configuratie definiëren](assets/cfm-conf-01.png)


1. Selecteren **Maken** om de definitie op te slaan.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op de middelenmap {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor de functionaliteit van inhoudsfragmenten en wordt vervolgens toegepast op elke map Middelen.

Als u andere configuraties (dat wil zeggen exclusief globaal) wilt gebruiken met een vergelijkbare map met assets, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

![Configuratie toepassen](assets/cfm-conf-02.png)
