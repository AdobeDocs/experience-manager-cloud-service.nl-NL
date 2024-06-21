---
title: Inhoudsfragmenten - Setup
description: Leer hoe u Content Fragment en GraphQL inschakelt voor gebruik met AEM functies voor levering zonder kop en het ontwerpen van pagina's.
feature: Content Fragments
role: Developer, Architect
exl-id: 3974d698-1e7d-4a5f-a6d5-cbf8d96b4095
solution: Experience Manager Sites
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# Inhoudsfragmenten - Setup {#content-fragments-setup}

Met Content Fragments in Adobe Experience Manager (AEM) as a Cloud Service kunt u inhoud voorbereiden voor gebruik op meerdere locaties en via meerdere kanalen. Dit is ideaal voor levering zonder kop en voor het ontwerpen van pagina&#39;s.

U moet de functie Inhoudsfragment inschakelen om de instantie in te schakelen voor de functionaliteit:

* **Modellen van inhoudsfragmenten** - verplicht

  >[!CAUTION]
  >
  >Als u niet inschakelt **Modellen van inhoudsfragmenten**:
  >
  >* de **Maken** is niet beschikbaar voor het maken van modellen.
  >* u kunt niet [Selecteer de configuratie van Plaatsen om het verwante eindpunt tot stand te brengen](/help/headless/graphql-api/graphql-endpoint.md).

* **Aangehouden GraphQL-query&#39;s** - facultatief

Het instellen van de instantie is voltooid:

* door [het toelaten van functionaliteit in Browser van de Configuratie](#enable-content-fragment-functionality-configuration-browser)
* dan [het toepassen van de configuratie op uw individuele omslagen van Activa](#apply-the-configuration-to-your-folder)

## Functionaliteit van inhoudsfragment inschakelen in de configuratiebrowser {#enable-content-fragment-functionality-configuration-browser}

Als u de functionaliteit Content Fragment, van Modellen van inhoudsfragmenten en blijvende query&#39;s van GraphQL wilt gebruiken, **moet** ze eerst via de **Configuratiebrowser**:

>[!NOTE]
>
>Zie voor meer informatie [Configuratiebrowser](/help/implementing/developing/introduction/configurations.md#using-configuration-browser).

>[!NOTE]
>
>[Subconfiguraties](/help/implementing/developing/introduction/configurations.md#configuration-resolution) (een configuratie die in een andere configuratie is genest), wordt volledig ondersteund voor gebruik met Content Fragments, Content Fragment Models en GraphQL query&#39;s.
>
>Ik wil alleen opmerken dat:
>
>* Na het creëren van modellen in een subconfiguration, is het NIET mogelijk om het model aan een andere subconfiguration te bewegen of te kopiëren.
>
>* Een eindpunt van GraphQL zal (nog) op een ouder (wortel) configuratie worden gebaseerd.
>
>* Blijvende query&#39;s worden (nog) als relevant voor de bovenliggende (basis)configuratie opgeslagen.

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Gebruiken **Maken** om het dialoogvenster te openen, waarin u:

   1. Geef een **Titel**.
   1. Bij het maken **Naam** wordt de knooppuntnaam in de gegevensopslagruimte.
U kunt een naam invoeren. Als u het veld leeg laat, wordt het automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies](/help/implementing/developing/introduction/naming-conventions.md); u kunt het resultaat indien nodig aanpassen.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **Aangehouden GraphQL-query&#39;s**

      ![Configuratie definiëren](assets/cf-setup-create-conf.png)

1. Selecteren **Maken** om de definitie op te slaan.

## De configuratie toepassen op uw map {#apply-the-configuration-to-your-folder}

Wanneer de configuratie **globaal** is ingeschakeld voor de functionaliteit van Content Fragment, wordt deze toegepast op elke map Middelen die toegankelijk is via **Activa** console.

Als u andere configuraties (dus zonder globale configuraties) wilt gebruiken in een vergelijkbare map Elementen, moet u de verbinding definiëren. Doe dit door het juiste **Configuratie** in de **Cloud Servicen** tabblad van het **Eigenschappen van map** van de desbetreffende map.

![Configuratie toepassen](assets/cf-setup-apply-conf.png)
