---
title: Experience Audit Testing - Cloud Services
description: Experience Audit Testing - Cloud Services
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
translation-type: tm+mt
source-git-commit: f6c700f82bc5a1a3edf05911a29a6e4d32dd3f72
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Ervaring controleren {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Experience Audit Testing"
>abstract="Experience Audit is een functie die beschikbaar is in de Sites Production-pijpleidingen van Cloud Manager, aangedreven door Google Lighthouse, een opensource tool van Google. Deze functie is ingeschakeld in alle productiepijpleidingen van Cloud Manager."

Experience Audit is een functie die beschikbaar is in de Sites Production-pijpleidingen van Cloud Manager, aangedreven door Google Lighthouse, een opensource tool van Google. Deze functie is ingeschakeld in alle productiepijpleidingen van Cloud Manager.

Het valideert het plaatsingsproces en de hulp zorgt ervoor dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Neem geen regressies op in deze afmetingen.

Experience Audit in Cloud Manager zorgt ervoor dat de digitale ervaring van eindgebruikers op de site op de hoogste standaarden kan worden gehandhaafd. De resultaten zijn informatief en stellen de gebruiker in staat de scores en de wijziging tussen de huidige en vorige scores te bekijken. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing zal worden geïntroduceerd.

## De resultaten van de Experience Audit {#understanding-experience-audit-results}

De Audit van de ervaring verstrekt geaggregeerde en gedetailleerde op paginaniveau testresultaten via de de uitvoeringspagina van de Pijpleiding van de Productie.

* De gegevens op het niveau van het samengevoegde niveau meten de gemiddelde score over de pagina&#39;s die voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek) werden gecontroleerd.
   >[!NOTE]
   >De progressieve score van de Web App (PWA) is niet inbegrepen in de summiere score en zal slechts in het pagina-vlakke scherm van rapportdetails worden getoond.
* Afzonderlijke scores op paginaniveau zijn ook beschikbaar via de neerwaartse boor.
* Nadere bijzonderheden over de scores zijn beschikbaar om te zien wat de resultaten zijn van de afzonderlijke tests, samen met aanwijzingen voor het verhelpen van eventuele problemen die tijdens de ervaringsaudit zijn vastgesteld.
* Een geschiedenis van de testresultaten wordt voortgeduurd binnen de Manager van de Wolk zodat kunnen de klanten zien of de veranderingen die in de pijpleidingslooppas worden geïntroduceerd om het even welke regressies van de vorige looppas omvatten.

### Samengevoegde scores {#aggregate-scores}

Er is een score voor het geaggregeerde niveau voor elk type test, zoals prestaties, toegankelijkheid, SEO en aanbevolen procedures.
>[!NOTE]
>De progressieve score van de Web App (PWA) is niet inbegrepen in de summiere score en zal slechts in het pagina-vlakke scherm van rapportdetails worden getoond.

De score voor het geaggregeerde niveau is gebaseerd op de gemiddelde score van de pagina&#39;s die in de run zijn opgenomen. De verandering op het gezamenlijke niveau vertegenwoordigt de gemiddelde score van de pagina&#39;s in de huidige looppas in vergelijking met het gemiddelde van de scores van de vorige looppas, zelfs als de inzameling van pagina&#39;s die om worden gevormd om zijn omvat tussen looppas is veranderd.

De waarde van de metrische waarde van de Verandering kan één van het volgende zijn:

* **Positieve waarde** : de pagina(&#39;s) zijn verbeterd op de geselecteerde test sinds de laatste productiepijpleiding

* **Negatieve waarde** : de pagina(&#39;s) zijn tijdens de geselecteerde test opnieuw geperst sinds de laatste productiepijpleiding

* **Geen wijziging**  - de pagina(&#39;s) hebben hetzelfde gescand sinds de laatste productiepijpleiding

* **N.v.t** . - er was geen vorige score beschikbaar om te vergelijken

   ![](/help/implementing/cloud-manager/assets/exp-audit-1.png)


### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, kunt u een gedetailleerdere score op paginaniveau zien. De gebruiker zal kunnen zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige tijd de test in werking werden gesteld.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd, en kunt u aangeven welke problemen u kunt oplossen als er mogelijkheden voor verbetering zijn gevonden. De details van de tests en de bijbehorende richtsnoeren worden verstrekt door Google Lighthouse.

![](/help/implementing/cloud-manager/assets/exp-audit-2.png)
