---
title: AEM-systeemoverzicht
description: AEM-systeemoverzicht
translation-type: tm+mt
source-git-commit: aa6bb878ea4c58ba1e2fbf82d53effaa1a72d668

---


# AEM-systeemoverzicht {#aem-system}

Op deze pagina vindt u het systeemoverzicht van Adobe Experience Manager (AEM).

## Achtergrond {#background}

Dit patroon wordt gebruikt om algemene informatie te identificeren die een overzicht van het AEM systeem verstrekt. De informatie kan punten omvatten zoals:

Gebruikte AEM versionAEM-producten (sites, middelen, formulieren, enzovoort) Aantal knooppunten (pagina&#39;s, elementen, enzovoort)

## Patroongegevens {#pattern-data}

De volgende objecten worden opgenomen in de JSON-weergave van het patroon:

* **item.message**: verwijst naar het bericht van het patroon.
* **item.context**: verwijst naar aanvullende informatie over de overzichtsinformatie:
   * *type*: Het type contextgegevens, &quot;aem.version&quot;, &quot;aem.product&quot; of &quot;node.count&quot;.
   * *gegevens*: Een JSON-object met de gegevens die overeenkomen met het type: &quot;version&quot; (tekenreeks), &quot;product&quot; (tekenreeks) of &quot;count&quot; (geheel getal).

### Mogelijke gevolgen en risico&#39;s {#possible-implications}

Niet van toepassing.

### Mogelijke oplossingen {#possible-solutions}

Niet van toepassing.
