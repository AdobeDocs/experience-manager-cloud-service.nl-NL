---
title: Inhoudsfragmenten - Setup
description: Leer hoe u Content Fragment en GraphQL inschakelt voor gebruik met AEM-functies voor levering zonder kop en het ontwerpen van pagina's.
feature: Content Fragments
role: Developer
exl-id: 3974d698-1e7d-4a5f-a6d5-cbf8d96b4095
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Inhoudsfragmenten - Setup {#content-fragments-setup}

Met inhoudsfragmenten in Adobe Experience Manager (AEM) as a Cloud Service kunt u inhoud voorbereiden voor gebruik op meerdere locaties en via meerdere kanalen. Dit is ideaal voor levering zonder kop en voor het ontwerpen van pagina&#39;s.

U moet de functie Inhoudsfragment inschakelen om de instantie in te schakelen voor de functionaliteit:

* **Modellen van het Fragment van de Inhoud** - verplicht

  >[!CAUTION]
  >
  >Als u niet **Modellen van het Fragment van de Inhoud** toelaat:
  >
  >* **creeer** optie zal niet beschikbaar voor het creëren van modellen zijn.
  >* u zult niet de configuratie van Plaatsen kunnen [ selecteren om het verwante eind-punt ](/help/headless/graphql-api/graphql-endpoint.md) tot stand te brengen.

* **GraphQL Blijven Vragen** - facultatief

Het instellen van de instantie is voltooid:

* door [ toelatend functionaliteit in Browser van de Configuratie ](#enable-content-fragment-functionality-configuration-browser)
* dan [ het toepassen van de configuratie op uw individuele omslagen van Assets ](#apply-the-configuration-to-your-folder)

## Functionaliteit van inhoudsfragment inschakelen in de configuratiebrowser {#enable-content-fragment-functionality-configuration-browser}

Om de functionaliteit van het Fragment van de Inhoud, van de Modellen van het Fragment van de Inhoud en GraphQL Gepersiste Vragen te gebruiken, moet u **eerst hen toelaten via** Browser van de Configuratie **:**

>[!NOTE]
>
>Voor meer details, zie [ Browser van de Configuratie ](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[ Subconfiguration ](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (een configuratie die binnen een andere configuratie wordt genest) wordt volledig gesteund voor gebruik met de Fragmenten van de Inhoud, Modellen van het Fragment van de Inhoud en de vragen van GraphQL.
>
>Ik wil alleen opmerken dat:
>
>* Na het creëren van modellen in een subconfiguration, is het NIET mogelijk om het model aan een andere subconfiguration te bewegen of te kopiëren.
>
>* Een eindpunt van GraphQL zal (nog) op een ouder (wortel) configuratie worden gebaseerd.
>
>* Blijvende query&#39;s worden (nog) als relevant voor de bovenliggende (basis)configuratie opgeslagen.

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Het gebruik **creeert** om de dialoog te openen, waar u:

   1. Specificeer a **Titel**.
   1. Op verwezenlijking, wordt de **Naam** de knoopnaam in de bewaarplaats.
U kunt een naam invoeren. Als u het gebied leeg verlaat wordt het automatisch geproduceerd gebaseerd op de titel, dan aangepast volgens [ AEM noemende overeenkomsten ](/help/implementing/developing/introduction/naming-conventions.md); u kunt het resultaat indien nodig aanpassen.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **GraphQL Blijven Vragen**

      ![ bepaalt configuratie ](assets/cf-setup-create-conf.png)

1. Selecteer **creeer** om de definitie te bewaren.

## De configuratie toepassen op uw map {#apply-the-configuration-to-your-folder}

Wanneer de configuratie **globale** voor de functionaliteit van het Fragment van de Inhoud wordt toegelaten, is het dan op om het even welke omslag van Assets van toepassing - toegankelijk door de **Assets** console.

Als u andere configuraties (dus niet globaal) wilt gebruiken met een vergelijkbare Assets-map, moet u de verbinding definiëren. Doe dit door de aangewezen **Configuratie** in het **lusje van de Diensten van de Wolk** van de **Eigenschappen van de Omslag** van de aangewezen omslag te selecteren.

![ pas configuratie ](assets/cf-setup-apply-conf.png) toe
