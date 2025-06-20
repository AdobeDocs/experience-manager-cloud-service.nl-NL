---
title: Bulk bewerken van pagina-eigenschappen configureren
description: Leer hoe u bulkbewerking kunt configureren, zodat u de eigenschappen van meerdere pagina's tegelijk kunt bewerken.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Bulk bewerken van pagina-eigenschappen configureren {#configuring-bulk-editing-of-page-properties}

[ Bulk het uitgeven van paginaeigenschappen ](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#from-the-sites-console-multiple-pages) laat u de eigenschappen van veelvoudige pagina&#39;s in één keer uitgeven.

## Overwegingen {#considerations}

Pagina-eigenschappen zijn standaard niet ingeschakeld voor bulkbewerking. Ze moeten expliciet zijn ingeschakeld. Wanneer u de pagina-eigenschappen definieert die beschikbaar moeten zijn voor bulkbewerking, moet u rekening houden met bepaalde implicaties, zoals:

* Bepaalde velden zijn gewoonlijk uniek. U moet beslissen of het zinvol is dergelijke velden in te schakelen voor bulkbewerking, wanneer er één waarde wordt toegepast.
   * Paginatitels zijn bijvoorbeeld bijna altijd uniek.
* Bepaalde velden kunnen meerdere waarden hebben die een betekenisvolle weergave vereisen bij het renderen.
   * Bijvoorbeeld, een status drop-down geëtiketteerd **Klaar voor Publicatie**. Dit zou verscheidene waarden vóór bulk-uitgeeft zoals **klaar**, **in overzicht**, **in uitvoering**, etc. kunnen hebben.

Vanwege de mogelijkheid van meerdere waarden wordt aangeraden alleen de volgende veldtypen in te schakelen voor bulkbewerking.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Veld inschakelen {#enabling-a-field}

Deze stappen gebruiken `/apps/core/wcm/components/page/v1/page` van de [ WKND steekproefinhoud ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als voorbeeld om bulkhet uitgeven op een gebied in een ontwikkelomgeving toe te laten.

1. Met CRXDE opent u de pagina-component.
1. Navigeer naar het vereiste veld binnen de definitie van `cq:dialog` .
1. Definieer de volgende eigenschap op het veldknooppunt:

   * **Naam**: `allowBulkEdit`
   * **Type**: `Boolean`
   * **Waarde**: `true`

1. Selecteer **sparen allen** om uw updates voort te zetten.

## Beperkingen {#limitations}

Bulkbewerking van pagina-eigenschappen is:

* Niet beschikbaar voor pagina&#39;s in een live kopie.
* Alleen beschikbaar voor pagina&#39;s met hetzelfde brontype.
