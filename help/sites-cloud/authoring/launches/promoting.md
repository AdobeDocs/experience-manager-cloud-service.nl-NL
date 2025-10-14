---
title: Starten promoten
description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen.
exl-id: 5f5ed17c-43db-4ef6-ab79-c491326fa01c
solution: Experience Manager Sites
feature: Authoring, Launches
role: User
source-git-commit: b5ded40d1cb8b8fab28583467b68c4586eecf1a0
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
>Nadat u de lanceringspagina&#39;s aan het doel (**Productie**) bevordert, kunt u de **Productie** pagina&#39;s als entiteit (om het proces sneller te maken) activeren. Voeg de pagina&#39;s toe aan een workflowpakket en gebruik dit als de payload voor een workflow die een pakket met pagina&#39;s activeert. U moet het workflowpakket maken voordat u de introductie kunt promoten. Zie [&#x200B; het Verwerken bevorderde Pagina&#39;s gebruikend AEM Werkschema &#x200B;](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>Een enkele lancering kan niet tegelijkertijd worden bevorderd. Dit betekent dat twee promotieacties bij dezelfde introductie tegelijkertijd kunnen resulteren in een fout - `Launch could not be promoted` (samen met conflictfouten in het logbestand).

>[!CAUTION]
>
>Wanneer het bevorderen van lanceringen voor *gewijzigde* pagina&#39;s, worden de wijzigingen in zowel de bron als lanceringstakken overwogen.

## Startpagina&#39;s promoten {#promoting-launch-pages}

>[!NOTE]
>
>Dit omvat de handmatige actie van het bevorderen van lanceringspagina&#39;s wanneer er slechts één lanceringsniveau is. Zie:
>
>* [&#x200B; Bevorderend een Genestelde Lancering &#x200B;](#promoting-a-nested-launch) wanneer er meer dan één lancering in de structuur is.
>* [&#x200B; Lanceringen - de Orde van Gebeurtenissen &#x200B;](/help/sites-cloud/authoring/launches/overview.md#launches-the-order-of-events) voor verdere details over automatische bevordering en publicatie.
>

U kunt lanceringen van of de **console van Plaatsen** of de **console van Lanceringen** bevorderen:

1. Openen:
   * De **console van Plaatsen** wanneer het navigeren van bronpagina&#39;s:
      1. Open het [&#x200B; verwijzingenspoor &#x200B;](/help/sites-cloud/authoring/sites-console/console-side-panel.md#references) en selecteer de vereiste bronpagina gebruikend [&#x200B; selectiemodus &#x200B;](/help/sites-cloud/authoring/basic-handling.md) (of selecteer en open de verwijzingsspoorwegen, is de orde niet belangrijk). Alle verwijzingen worden weergegeven.
      1. Selecteer **Lanceringen** (bijvoorbeeld, Lanceringen (1)) om een lijst van de specifieke lanceringen te tonen.
      1. Selecteer de specifieke lancering om de beschikbare acties te tonen.
      1. Selecteer **Bevorderen lancering** om de tovenaar te openen.
   * De **console van Plaatsen** wanneer het navigeren van lanceringspagina&#39;s:
      1. Selecteer de vereiste lanceringspagina gebruikend [&#x200B; selectiemodus &#x200B;](/help/sites-cloud/authoring/basic-handling.md).
      1. **bevordert** actie is beschikbaar in de toolbar.
   * De **console van Lanceringen**:
      1. Selecteer de startknop (selecteer de miniatuur).
      1. Selecteer **bevorderen**.
1. In de eerste stap kunt u het volgende opgeven:
   * **Doel**
      * **schrapping lancering na bevordering**
   * **Reikwijdte**
      * **bevorderen volledige lancering**
      * **bevordert gewijzigde pagina&#39;s**
      * **bevordert goedgekeurde pagina&#39;s** - afhankelijk van het werkschema van de lanceringsgoedkeuring
      * **bevordert huidige pagina**
      * **bevordert huidige pagina en subpagina&#39;s**

     Als u bijvoorbeeld alleen gewijzigde pagina&#39;s wilt promoten:

     ![&#x200B; Bevordering van de Lancering &#x200B;](/help/sites-cloud/authoring/assets/launches-promote.png)

     >[!NOTE]
     >
     >Dit behandelt één enkele lancering, als u genestelde lanceringen zie [&#x200B; Bevorderend een Genestelde Lancering &#x200B;](#promoting-a-nested-launch).

1. Selecteer **daarna** te werk te gaan.

1. U kunt de pagina&#39;s bekijken die u wilt promoten. Deze zijn afhankelijk van het gekozen paginabereik:

   ![&#x200B; bevordering van het Overzicht &#x200B;](/help/sites-cloud/authoring/assets/launches-promote-review.png)

1. Selecteer **bevorderen**.

## Starten van pagina&#39;s tijdens bewerken bevorderen {#promoting-launch-pages-when-editing}

Wanneer u een lanceringspagina uitgeeft, **bevordert de 1&rbrace; actie van de Lancering &lbrace;ook beschikbaar bij** Informatie van de Pagina **.** Hierdoor wordt de wizard geopend die de benodigde informatie verzamelt.

![&#x200B; Bevorder lancering van plaatsinfo &#x200B;](/help/sites-cloud/authoring/assets/launches-promote-page-info.png)

>[!NOTE]
>
>Dit is beschikbaar voor enige en [&#x200B; genestelde lanceringen &#x200B;](#promoting-a-nested-launch).

## Een geneste start bevorderen {#promoting-a-nested-launch}

Nadat u een geneste start hebt gemaakt, kunt u deze herstellen naar een van de bronnen, inclusief de hoofdbron (productie).

![&#x200B; Een genestelde lancering &#x200B;](/help/sites-cloud/authoring/assets/launches-promoting-nested.png)

1. Zoals met het Creëren van een Genestelde Lancering, navigeer aan en selecteer de vereiste lancering in of de **console van Lanceringen** of de **spoorstaaf van Verwijzingen**.
1. Selecteer **Bevorderen lancering** om de tovenaar te openen.
1. Voer de vereiste gegevens in:
   * **Doel**
      * **doel van de Bevordering** - u kunt aan om het even welke bronnen bevorderen.
      * **schrapping lancering na bevordering** - na bevordering, worden de geselecteerde lancering, en om het even welke lanceringen die binnen het worden genesteld, geschrapt.
   * **Reikwijdte** - hier kunt u selecteren of om de volledige lancering, of slechts pagina&#39;s te bevorderen die eigenlijk zijn uitgegeven. In het laatste geval kunt u opgeven of u subpagina&#39;s wilt opnemen of uitsluiten. De standaardconfiguratie is dat alleen paginawijzigingen voor de huidige pagina worden bevorderd:
      * **bevorderen volledige lancering**
      * **bevordert gewijzigde pagina&#39;s**
      * **bevordert goedgekeurde pagina&#39;s** - afhankelijk van het werkschema van de lanceringsgoedkeuring
      * **bevordert huidige pagina**
      * **bevordert huidige pagina en subpagina&#39;s**

   ![&#x200B; bevordert lanceringsmontages &#x200B;](/help/sites-cloud/authoring/assets/launches-promote-settings.png)

1. Selecteer **daarna**.
1. Herzie de promotiedetails alvorens **te selecteren bevorderen**:

   ![&#x200B; de bevorderingsmontages van het Overzicht &#x200B;](/help/sites-cloud/authoring/assets/launches-promote-review-2.png)

   >[!NOTE]
   >
   >De vermelde pagina&#39;s zullen van het **Gedefinieerde Werkingsgebied** en misschien de pagina&#39;s afhangen die eigenlijk zijn uitgegeven.

1. Uw veranderingen worden bevorderd en in de **console van Lanceringen** weerspiegeld:

   ![&#x200B; In lanceert console &#x200B;](/help/sites-cloud/authoring/assets/launches-console.png)

## Promotiepagina&#39;s verwerken met AEM workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Als u een workflow automatisch wilt starten wanneer pagina&#39;s worden geconverteerd, configureert u een workflow voor het pakketknooppunt. <!--To start a workflow automatically when pages are promoted, [configure a workflow launcher](/help/sites-administering/workflows-starting.md#workflows-launchers) for the package node.-->

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s voor Starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![&#x200B; werkschema van de Bevordering &#x200B;](/help/sites-cloud/authoring/assets/launches-create-workflow.png)
