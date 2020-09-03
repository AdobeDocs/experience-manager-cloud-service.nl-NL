---
title: Experience Audit Testing - Cloud Services
description: Experience Audit Testing - Cloud Services
translation-type: tm+mt
source-git-commit: d03ef0afe91760e35ef4e8fb3e3f2c833cbf945c
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 0%

---


# Experience Audit Testing {#experience-audit-testing}

Experience Audit is een functie die beschikbaar is in Cloud Manager Sites Production Pipelines, een opensource tool van Google. Deze functie is ingeschakeld in alle productiepijpleidingen van Cloud Manager.

Het valideert het plaatsingsproces en de hulp zorgt ervoor dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Neem geen regressies op in deze afmetingen.

Experience Audit in Cloud Manager zorgt ervoor dat de digitale ervaring van eindgebruikers op de site op de hoogste standaarden kan worden gehandhaafd. De resultaten zijn informatief en stellen de gebruiker in staat de scores en de wijziging tussen de huidige en vorige scores te bekijken. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing zal worden geïntroduceerd.

## Werken met de resultaten van Experience Audit {#understanding-experience-audit-results}

De Audit van de ervaring verstrekt geaggregeerde en gedetailleerde op paginaniveau testresultaten via de de uitvoeringspagina van de Pijpleiding van de Productie.

* De cijfers op het niveau van het samengevoegde niveau meten de gemiddelde score over de pagina&#39;s die werden gecontroleerd.
* Afzonderlijke scores op paginaniveau zijn ook beschikbaar via de neerwaartse boor.
* Er zijn details van de scores beschikbaar om te zien wat de resultaten zijn van de afzonderlijke tests, samen met aanwijzingen voor het verhelpen van problemen die tijdens de inhoudscontrole zijn vastgesteld.
* Een geschiedenis van de testresultaten wordt voortgeduurd binnen de Manager van de Wolk zodat kunnen de klanten zien of de veranderingen die in de pijpleidingslooppas worden geïntroduceerd om het even welke regressies van de vorige looppas omvatten.

### Samengevoegde scores {#aggregate-scores}

Voor elk type test (prestaties, toegankelijkheid, SEO, aanbevolen methoden en PWA) is een score voor het geaggregeerde niveau beschikbaar.

De score voor het geaggregeerde niveau is gebaseerd op de gemiddelde score van de pagina&#39;s die in de run zijn opgenomen. De verandering op het gezamenlijke niveau vertegenwoordigt de gemiddelde score van de pagina&#39;s in de huidige looppas in vergelijking met het gemiddelde van de scores van de vorige looppas, zelfs als de inzameling van pagina&#39;s die om worden gevormd om zijn omvat tussen looppas is veranderd.

De waarde van de metrische waarde van de Verandering kan één van het volgende zijn:

* **Positieve waarde** : de pagina(&#39;s) zijn verbeterd op de geselecteerde test sinds de laatste productiepijpleiding

* **Negatieve waarde** : de pagina(&#39;s) zijn tijdens de geselecteerde test opnieuw geperst sinds de laatste productiepijpleiding

* **Geen wijziging** - de pagina(&#39;s) hebben dezelfde score behaald sinds de laatste productiepijpleiding

* **N.v.t** . - er was geen vorige score beschikbaar om te vergelijken

   ![](/help/implementing/developing/introduction/assets/content-audit-test1.png)

### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, kunt u een gedetailleerdere score op paginaniveau zien. De gebruiker zal kunnen zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige tijd de test in werking werden gesteld.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd, en kunt u aangeven welke problemen u kunt oplossen als er mogelijkheden voor verbetering zijn gevonden. De details van de tests en de bijbehorende richtsnoeren worden verstrekt door Google Lighthouse.

![](/help/implementing/developing/introduction/assets/page-level-scores.png)

