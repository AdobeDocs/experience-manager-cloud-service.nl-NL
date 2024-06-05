---
title: Bulk bewerken van pagina-eigenschappen configureren
description: Leer hoe u bulkbewerking kunt configureren, zodat u de eigenschappen van meerdere pagina's tegelijk kunt bewerken.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Bulk bewerken van pagina-eigenschappen configureren {#configuring-bulk-editing-of-page-properties}

[Pagina-eigenschappen in bulk bewerken](/help/sites-cloud/authoring/sites-console/page-properties.md#from-the-sites-console-multiple-pages) Hiermee kunt u de eigenschappen van meerdere pagina&#39;s tegelijk bewerken.

## Overwegingen {#considerations}

Pagina-eigenschappen zijn standaard niet ingeschakeld voor bulkbewerking. Ze moeten expliciet zijn ingeschakeld. Wanneer u de pagina-eigenschappen definieert die beschikbaar moeten zijn voor bulkbewerking, moet u rekening houden met bepaalde implicaties, zoals:

* Bepaalde velden zijn gewoonlijk uniek. U moet beslissen of het zinvol is dergelijke velden in te schakelen voor bulkbewerking, wanneer er één waarde wordt toegepast.
   * Paginatitels zijn bijvoorbeeld bijna altijd uniek.
* Bepaalde velden kunnen meerdere waarden hebben die een betekenisvolle weergave vereisen bij het renderen.
   * Bijvoorbeeld een vervolgkeuzelijst met status **Gereed voor publicatie**. Dit kan verschillende waarden hebben voordat bulkbewerkingen worden uitgevoerd, zoals **klaar**, **tijdens de herziening**, **in uitvoering**, enzovoort.

Vanwege de mogelijkheid van meerdere waarden wordt aangeraden alleen de volgende veldtypen in te schakelen voor bulkbewerking.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Veld inschakelen {#enabling-a-field}

Deze stappen gebruiken de `/apps/core/wcm/components/page/v1/page` van de [WKND-voorbeeldinhoud](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als voorbeeld om bulkbewerking op een veld in een ontwikkelomgeving mogelijk te maken.

1. Met CRXDE opent u de pagina-component.
1. Ga naar het gewenste veld in het dialoogvenster `cq:dialog` definitie.
1. Definieer de volgende eigenschap op het veldknooppunt:

   * **Naam**: `allowBulkEdit`
   * **Type**: `Boolean`
   * **Waarde**: `true`

1. Selecteren **Alles opslaan** om uw updates voort te zetten.

## Beperkingen {#limitations}

Bulkbewerking van pagina-eigenschappen is:

* Niet beschikbaar voor pagina&#39;s in een live kopie.
* Alleen beschikbaar voor pagina&#39;s met hetzelfde brontype.
