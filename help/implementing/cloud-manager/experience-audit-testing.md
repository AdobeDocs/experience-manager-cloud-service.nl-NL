---
title: Ervaring controleren testen
description: Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---


# Ervaring controleren testen {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Ervaring controleren testen"
>abstract="Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen."

Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen.

## Overzicht {#overview}

De Audit van de ervaring is een eigenschap beschikbaar in de pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk die het plaatsingsproces bevestigt en helpt ervoor zorgen dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Breng geen regressies aan.

De controle van de ervaring in de Manager van de Wolk zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing werd geïntroduceerd.

Experience Audit wordt aangedreven door Google Lighthouse, een opensource tool van Google, en wordt ingeschakeld in alle productiepijpleidingen van Cloud Manager.

>[!INFO]
>
>Met ingang van 31 augustus 2023 zal Experience Audit een overgang maken naar toonaangevende resultaten die specifiek zijn voor het mobiele platform. Merk op dat mobiele prestatiesmetriek typisch lager dan die van Desktop registreren, zodat zou u een verschuiving in de gemelde prestaties na deze verandering moeten voorzien.

>[!TIP]
>
>U vormt welke pagina&#39;s inbegrepen in de Controle van de Ervaring wanneer u [de pijplijn instellen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code).

## Werken met de resultaten van Experience Audit {#understanding-experience-audit-results}

De Audit van de ervaring verstrekt geaggregeerde en gedetailleerde testresultaten op paginaniveau via [uitvoeringspagina van productiepijplijn](/help/implementing/cloud-manager/deploy-code.md).

* Met statistische gegevens worden de gemiddelde scores op de pagina&#39;s gemeten die zijn gecontroleerd op prestaties, toegankelijkheid, aanbevolen procedures, SEO (Search Engine Optimization).
* Afzonderlijke scores op paginaniveau zijn ook beschikbaar via de neerwaartse boor.
* Nadere gegevens over de scores zijn beschikbaar om de resultaten van de afzonderlijke tests te bekijken, samen met aanwijzingen voor het verhelpen van eventuele problemen die zijn vastgesteld.
* Een geschiedenis van de testresultaten wordt voortgeduurd binnen de Manager van de Wolk om te bepalen als de veranderingen die in de pijpleiding worden geïntroduceerd om het even welke regressies van de vorige looppas omvatten.

### Samengevoegde scores {#aggregate-scores}

De score voor het geaggregeerde niveau is gebaseerd op de gemiddelde score van de pagina&#39;s die in de run zijn opgenomen. De verandering op het gezamenlijke niveau vertegenwoordigt de gemiddelde score van de pagina&#39;s in de huidige looppas in vergelijking met het gemiddelde van de scores van de vorige looppas, zelfs als de inzameling van pagina&#39;s die om worden gevormd om zijn omvat tussen looppas is veranderd.

Er is een score voor het geaggregeerde niveau voor elk type test, zoals prestaties, toegankelijkheid, SEO en aanbevolen procedures.

De metrische wijziging kan een van de volgende waarden hebben.

* **Positieve waarde** - De pagina(&#39;s) is (zijn) verbeterd ten opzichte van de geselecteerde test sinds de laatste productiepijpleiding.

* **Negatieve waarde** - de pagina(&#39;s) sinds de laatste productiepijpleiding op de geselecteerde test is (zijn) teruggelopen.

* **Geen wijziging** - De pagina(&#39;s) hebben dezelfde score gekregen sinds de laatste productiepijpleiding.

* **NVT** - Er was geen vorige score beschikbaar om te vergelijken.

![Resultaten van controle door ervaring](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, is meer gedetailleerde paginaniveau-scoring beschikbaar. U kunt zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige testlooppas werden gescoord.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd en kunt u aangeven wat de problemen zijn als er mogelijkheden voor verbetering zijn gevonden.

![Scores op paginaniveau](/help/implementing/cloud-manager/assets/exp-audit-2.png)
