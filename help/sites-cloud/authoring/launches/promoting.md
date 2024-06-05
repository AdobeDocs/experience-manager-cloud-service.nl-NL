---
title: Starten promoten
description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen.
exl-id: 5f5ed17c-43db-4ef6-ab79-c491326fa01c
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---

# Starten promoten {#promoting-launches}

U moet opstartiepagina&#39;s promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina&#39;s vervangen door de inhoud van de gepromoveerde pagina. De volgende opties zijn beschikbaar bij het promoten van een startpagina:

* Of alleen de huidige pagina of de volledige lancering wordt bevorderd.
* Of de onderliggende pagina&#39;s van de huidige pagina worden bevorderd.
* Of de volledige lancering of slechts pagina&#39;s wordt bevorderd die zijn veranderd.
* Of de introductie moet worden verwijderd nadat deze is bevorderd.

>[!NOTE]
>
>Nadat u de startpagina&#39;s naar het doel hebt opgewaardeerd (**Productie**), kunt u de **Productie** pagina&#39;s als een entiteit (om het proces sneller te maken). Voeg de pagina&#39;s toe aan een workflowpakket en gebruik dit als de payload voor een workflow die een pakket met pagina&#39;s activeert. U moet het workflowpakket maken voordat u de introductie kunt promoten. Zie [Promotiepagina&#39;s verwerken met AEM workflow](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>Een enkele lancering kan niet tegelijkertijd worden bevorderd. Dit betekent dat twee promotieacties tegelijk op dezelfde start kunnen leiden tot een fout - `Launch could not be promoted` (samen met conflictfouten in het logbestand).

>[!CAUTION]
>
>Bij het promoten van introducties voor *gewijzigd* pagina&#39;s, wordt rekening gehouden met wijzigingen in zowel de bron- als startvertakkingen.

## Startpagina&#39;s promoten {#promoting-launch-pages}

>[!NOTE]
>
>Dit omvat de handmatige actie van het bevorderen van lanceringspagina&#39;s wanneer er slechts één lanceringsniveau is. Zie:
>
>* [Een geneste start bevorderen](#promoting-a-nested-launch) wanneer de structuur meer dan één keer wordt gestart.
>* [Starten - de volgorde van gebeurtenissen](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) voor meer informatie over automatische promotie en publicatie.
>

U kunt lanceringen van één van beide bevorderen **Sites** of de **Starten** console:

1. Openen:
   * De **Sites** console bij navigeren naar bronpagina&#39;s:
      1. Open de [referentie-rail](/help/sites-cloud/authoring/sites-console/console-side-panel.md#references) en selecteert u de gewenste bronpagina met [selectiemodus](/help/sites-cloud/authoring/basic-handling.md) (of selecteer en open de referentie-rail, de volgorde is niet belangrijk). Alle verwijzingen worden weergegeven.
      1. Selecteren **Starten** (bijvoorbeeld Launches (1)) om een lijst weer te geven met de specifieke startacties.
      1. Selecteer de specifieke lancering om de beschikbare acties te tonen.
      1. Selecteren **Starten bevorderen** om de wizard te openen.
   * De **Sites** console bij navigeren door opstartiepagina&#39;s:
      1. Selecteer de vereiste startpagina met [selectiemodus](/help/sites-cloud/authoring/basic-handling.md).
      1. De **Bevorderen** is beschikbaar in de werkbalk.
   * De **Starten** console:
      1. Selecteer de startknop (selecteer de miniatuur).
      1. Selecteren **Bevorderen**.
1. In de eerste stap kunt u het volgende opgeven:
   * **Doel**
      * **Starten na promotie verwijderen**
   * **Toepassingsgebied**
      * **Volledige introductie bevorderen**
      * **Gewijzigde pagina&#39;s promoten**
      * **Goedgekeurde pagina&#39;s promoten** - afhankelijk van de workflow voor goedkeuring van de lancering
      * **Huidige pagina promoten**
      * **Huidige pagina en subpagina&#39;s promoten**

     Als u bijvoorbeeld alleen gewijzigde pagina&#39;s wilt promoten:

     ![Promotie starten](/help/sites-cloud/authoring/assets/launches-promote.png)

     >[!NOTE]
     >
     >Dit geldt voor één keer starten, als u geneste lanceringen hebt, zie [Een geneste start bevorderen](#promoting-a-nested-launch).
1. Selecteren **Volgende** om verder te gaan.
1. U kunt de pagina&#39;s bekijken die u wilt promoten. Deze zijn afhankelijk van het gekozen paginabereik:

   ![Aanbieding bekijken](/help/sites-cloud/authoring/assets/launches-promote-review.png)

1. Selecteren **Bevorderen**.

## Starten van pagina&#39;s tijdens bewerken bevorderen {#promoting-launch-pages-when-editing}

Wanneer u een startpagina bewerkt, wordt **Starten bevorderen** actie is ook beschikbaar via **Pagina-informatie**. Hierdoor wordt de wizard geopend die de benodigde informatie verzamelt.

![Starten bevorderen via site-info](/help/sites-cloud/authoring/assets/launches-promote-page-info.png)

>[!NOTE]
>
>Dit is beschikbaar voor enkelvoudig en [geneste lanceringen](#promoting-a-nested-launch).

## Een geneste start bevorderen {#promoting-a-nested-launch}

Nadat u een geneste start hebt gemaakt, kunt u deze herstellen naar een van de bronnen, inclusief de hoofdbron (productie).

![Een geneste start](/help/sites-cloud/authoring/assets/launches-promoting-nested.png)

1. Net als bij het maken van een geneste startpagina navigeert u naar de gewenste opstart en selecteert u deze in het dialoogvenster **Starten** of de **Verwijzingen** spoorwegen.
1. Selecteren **Starten bevorderen** om de wizard te openen.
1. Voer de vereiste gegevens in:
   * **Doel**
      * **Promotiedoel** - U kunt een van de bronnen promoten.
      * **Starten na promotie verwijderen** - Na de promotie worden de geselecteerde start en alle daarin geneste lanceringen verwijderd.
   * **Toepassingsgebied** - Hier kunt u kiezen of u de volledige opstart wilt promoten of alleen pagina&#39;s die daadwerkelijk zijn bewerkt. In het laatste geval kunt u opgeven of u subpagina&#39;s wilt opnemen of uitsluiten. De standaardconfiguratie is dat alleen paginawijzigingen voor de huidige pagina worden bevorderd:
      * **Volledige introductie bevorderen**
      * **Gewijzigde pagina&#39;s promoten**
      * **Goedgekeurde pagina&#39;s promoten** - afhankelijk van de workflow voor goedkeuring van de lancering
      * **Huidige pagina promoten**
      * **Huidige pagina en subpagina&#39;s promoten**

   ![Starten van instellingen bevorderen](/help/sites-cloud/authoring/assets/launches-promote-settings.png)

1. Selecteren **Volgende**.
1. De details van de aanbieding bekijken voordat je de selectie maakt **Bevorderen**:

   ![Promotie-instellingen bekijken](/help/sites-cloud/authoring/assets/launches-promote-review-2.png)

   >[!NOTE]
   >
   >De weergegeven pagina&#39;s zijn afhankelijk van de **Toepassingsgebied** gedefinieerde en mogelijk de pagina&#39;s die daadwerkelijk zijn bewerkt.

1. Je wijzigingen worden gepropageerd en weerspiegeld in de **Starten** console:

   ![In-startconsole](/help/sites-cloud/authoring/assets/launches-console.png)

## Promotiepagina&#39;s verwerken met AEM workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Als u een workflow automatisch wilt starten wanneer pagina&#39;s worden geconverteerd, configureert u een workflow voor het pakketknooppunt. <!--To start a workflow automatically when pages are promoted, [configure a workflow launcher](/help/sites-administering/workflows-starting.md#workflows-launchers) for the package node.-->

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s voor Starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![Aanbiedingsworkflow](/help/sites-cloud/authoring/assets/launches-create-workflow.png)
