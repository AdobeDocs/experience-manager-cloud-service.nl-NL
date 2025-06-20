---
title: De Sjabloonconsole
description: Leer hoe de sjabloonconsole fungeert als de centrale locatie voor het weergeven en beheren van uw paginasjablonen.
solution: Experience Manager Sites
feature: Administering
role: User
exl-id: d11d7176-dd35-4855-9dcd-dd40ff096510
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---

# De Sjabloonconsole {#templates-console}

Leer hoe de sjabloonconsole fungeert als de centrale locatie voor het weergeven en beheren van uw paginasjablonen.

## Overzicht {#overview}

Wanneer u een pagina maakt, moet u een sjabloon selecteren. De paginasjabloon wordt gebruikt als basis voor de nieuwe pagina. [ AEM die editable malplaatjes ](/help/implementing/developing/components/templates.md)  kan de structuur van de resulterende pagina, om het even welke aanvankelijke inhoud, en de componenten bepalen die (ontwerpeigenschappen) kunnen worden gebruikt.

De auteurs van de inhoud worden voorgesteld met een selectie van beschikbare malplaatjes wanneer zij [ nieuwe pagina&#39;s in de plaatsenconsole ](/help/sites-cloud/authoring/sites-console/creating-pages.md) creëren. Sjablonen kunnen worden gebruikt om pagina&#39;s te maken die kunnen worden bewerkt met:

* [ de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md) of
* [De Universal Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Met de sjabloonconsole kan een beheerder alle paginasjablonen op een centrale locatie weergeven en beheren.

## De Sjabloonconsole openen {#accessing}

1. Aanmelden bij AEM as a Cloud Service.
1. Open de globale navigatie en selecteer het **paneel van Hulpmiddelen** en dan **Algemeen** -> **Malplaatjes**.

## Afdrukstand {#orientation}

De malplaatjeconsole wordt georganiseerd in omslagen met één omslag per [ configuratie ](/help/implementing/developing/introduction/configurations.md) waar de editable malplaatjes voor de configuratie zijn geactiveerd.

![ de Console van Malplaatjes ](assets/templates-console/templates-console.png)

[ de standaardmening ](/help/sites-cloud/authoring/quick-start.md) van de console is de kaartmening. Tik of klik op een map om de inhoud ervan te verkennen.

![ Inhoud van malplaatjeomslag in malplaatjeconsole ](assets/templates-console/templates-console-templates.png)

Selecteer een sjabloon om de beschikbare opties op de werkbalk weer te geven.

![ de consoletoolbar van Malplaatjes ](assets/templates-console/templates-console-toolbar.png)

* [Bewerken](#edit-edit)
* [Eigenschappen](#properties)
* [Uitschakelen/inschakelen](#enable-disable)
* [Publiceren](#publish)
* [Kopiëren](#copy)
* [Verwijderen](#delete)

## Bewerken {#edit}

Als u een sjabloon bewerkt, wordt de editor geopend die is gebruikt om de sjabloon te maken. Ofwel:

* [De sjablooneditor](/help/sites-cloud/authoring/page-editor/templates.md)
* [De Universal Editor](/help/sites-cloud/authoring/universal-editor/templates.md)

Met de gewenste editor kunt u de benodigde wijzigingen in de sjabloon aanbrengen. Het bewerken van een sjabloon die in gebruik is, kan van invloed zijn op de auteurs.

* Voor sjablonen die zijn gemaakt met de Sjablooneditor, kunnen wijzigingen van invloed zijn op live pagina&#39;s die zijn gebaseerd op de geselecteerde sjabloon.
* Voor sjablonen die zijn gemaakt met de Universal Editor, hebben de aangebrachte wijzigingen alleen invloed op nieuwe pagina&#39;s die uw auteurs maken op basis van de geselecteerde sjabloon.

Als een auteur aan een malplaatje begint dat met de malplaatjeredacteur wordt gecreeerd die reeds is toegelaten, wordt een waarschuwing getoond.

>[!TIP]
>
>Nadat u een sjabloon in de console hebt geselecteerd, gebruikt u de sneltoets `e` om de geselecteerde sjabloon te bewerken.

## Eigenschappen {#properties}

U kunt de [ eigenschappen van het malplaatje ](/help/sites-cloud/authoring/page-editor/templates.md) veel op de zelfde manier uitgeven dat u pagina eigenschappen kunt [ uitgeven.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md) Sjablooneigenschappen zijn onder andere:

* Sjabloontitel
* Beschrijving
* Afbeelding

>[!TIP]
>
>Nadat u een sjabloon in de console hebt geselecteerd, gebruikt u de sneltoets `p` om de eigenschappen van de geselecteerde sjabloon te openen.

## In- en uitschakelen {#enable-disable}

Een sjabloon kan een van de volgende drie statussen hebben:

* **Ontwerp** - het malplaatje wordt nog gecreeerd en is niet beschikbaar voor het creëren van nieuwe pagina&#39;s.
* **Toegelaten** - het malplaatje is volledig en beschikbaar voor het creëren van nieuwe pagina&#39;s.
* **Gehandicapten** - het malplaatje is volledig maar niet beschikbaar voor het creëren van nieuwe pagina&#39;s.

Wanneer een malplaatje wordt gecreeerd, is het door gebrek of in a **Ontwerp** staat (voor malplaatjes die met de [ Redacteur van het Malplaatje ](/help/sites-cloud/authoring/page-editor/templates.md) worden gecreeerd) of **Toegelaten** staat (voor malplaatjes die met de [ Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/templates.md) worden gecreeerd).

Een sjabloon moet zijn ingeschakeld voordat het door inhoudsauteurs kan worden gebruikt om pagina&#39;s te maken. Als een sjabloon niet meer nodig is, kan deze worden uitgeschakeld zodat deze niet meer wordt weergegeven in de wizard Pagina maken.

* Selecteer het malplaatje en klik **onbruikbaar maken** om het malplaatje onbruikbaar te maken.
* Selecteer het malplaatje en klik **toelaten** om het malplaatje toe te laten.

## Publiceren {#publish}

Een sjabloon die met de sjablooneditor is gemaakt, kan alleen worden gebruikt nadat het is gepubliceerd. Selecteer het malplaatje en klik **publiceren** om te publiceren.

Sjablonen die zijn gemaakt met de universele editor hoeven niet te worden gepubliceerd om te worden gebruikt.

## Kopiëren {#copy}

Als u een aantal pagina&#39;s hebt die in structuur gelijkaardig zijn, kunt u de **knoop van het Exemplaar** gebruiken om een werkingsgebied van een malplaatje tot stand te brengen en dan het exemplaar te variëren dat op uw behoeften wordt gebaseerd. Dit is ook handig als u een sjabloon op een andere site wilt gebruiken.

1. Selecteer het malplaatje en dan het Tik of klik **Exemplaar** om een exemplaar tot stand te brengen.
1. Navigeer naar de plaats waar u de kopie wilt maken.
1. Tik of klik **Deeg** in de toolbar.

Na het plakken kunt u:

* [ geef het malplaatje ](#edit) uit om het zonodig aan te passen.
* [ gebruik het eigenschappenvenster ](#properties) om de malplaatjetitel bij te werken.
* [ laat het malplaatje ](#enable-disable) toe zodat kan het worden gebruikt om pagina tot stand te brengen.
* [ publiceer het malplaatje ](#publish) indien vereist.

>[!TIP]
>
>Nadat u een sjabloon in de console hebt geselecteerd, gebruikt u de sneltoets `Command+c` of `ctrl+c` om de geselecteerde sjabloon te kopiëren.

## Verwijderen {#delete}

Als een sjabloon niet meer nodig is, kan deze worden verwijderd, mits er op geen enkele pagina naar wordt verwezen.

Selecteer het malplaatje en dan de Tik of klik **Schrapping** om het te schrappen.

>[!TIP]
>
>Nadat u een sjabloon in de console hebt geselecteerd, gebruikt u de sneltoets `Backspace` om de geselecteerde sjabloon te verwijderen.

## Sjablonen maken {#create}

Gebruik **creeer** knoop in de console om een nieuw malplaatje in uw huidige plaats tot stand te brengen. Voor details bij het creëren van een malplaatje, te zien gelieve het document [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Redacteur van de Pagina ](/help/sites-cloud/authoring/page-editor/templates.md) editable zijn.

**creeer** knoop wordt slechts gebruikt om malplaatjes tot stand te brengen die met de Redacteur van de Pagina editable zijn. Gelieve te zien het document [ Malplaatjes om Pagina&#39;s tot stand te brengen die met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/templates.md) editable zijn om over het creëren van malplaatjes te leren die op pagina&#39;s worden gebaseerd die met de Universele Redacteur worden gemaakt.
