---
title: Ervaring controleren testen
description: Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen.
exl-id: 8d31bc9c-d38d-4d5b-b2ae-b758e02b7073
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---


# Ervaring controleren testen {#experience-audit-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_expaudittesting"
>title="Ervaring controleren testen"
>abstract="Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen."

Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen.

## Overzicht {#overview}

De Controle van de ervaring is een eigenschap beschikbaar in de pijpleidingen van de Productie van de Plaatsen van Cloud Manager die het plaatsingsproces bevestigt en helpt ervoor zorgen dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Breng geen regressies aan.

De controle van de ervaring in Cloud Manager zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing werd geïntroduceerd.

Experience Audit wordt aangedreven door Google Lighthouse, een opensource tool uit Google.

>[!INFO]
>
>Met ingang van 31 augustus 2023 zal Experience Audit een overgang maken naar toonaangevende resultaten die specifiek zijn voor het mobiele platform. Metrische gegevens over mobiele prestaties zijn doorgaans lager dan die van desktopcomputers. Daarom moet u een verschuiving in de gerapporteerde prestaties na deze wijziging verwachten.

## Beschikbaarheid {#availability}

Er is een Experience Audit beschikbaar voor Cloud Manager:

* Sites-productiepijpleidingen, standaard.
* Voorkant ontwikkelingspijpleidingen, optioneel.

Zie de [ sectie van de Configuratie ](#configuration) voor meer informatie over hoe te om de controle voor de facultatieve milieu&#39;s te vormen.

## Configuratie {#configuration}

De Experience Audit is standaard beschikbaar voor productiepijpleidingen. Het kan facultatief worden toegelaten voor front-end ontwikkelingspijpleidingen. In alle gevallen, moet u bepalen welke inhoudswegen tijdens pijpleidingsuitvoering worden geëvalueerd.

U vormt welke pagina&#39;s inbegrepen in de Controle van de Ervaring wanneer u opstelling uw pijpleiding zijn.

1. Afhankelijk van het type van pijpleiding u wenst te vormen, volg de richtingen aan:

   * Voeg een nieuwe [ productiepijpleiding toe, ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) als u wenst om de wegen te bepalen die door de controle moeten worden geëvalueerd.
   * Voeg een nieuwe [ niet-productiepijplijn toe, ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) als u wenst om de controle op een front-end of ontwikkelings volledig-stapelpijpleiding toe te laten.
   * Of u kunt [ een bestaande pijpleiding uitgeven, ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) en de bestaande opties bijwerken.

1. Als u toevoegt of een niet-productiepijplijn uitgeeft waarvoor u de Controle van de Ervaring wilt gebruiken, moet u **checkbox van de Controle van de Ervaring {op het** Source Code **tabel selecteren.**

   ![ toelatend de Controle van de Ervaring ](assets/experience-audit-enable.jpg)

   * Dit is alleen nodig voor niet-productiepijpleidingen.
   * Het **lusje van de Controle van de Ervaring** verschijnt wanneer checkbox wordt geselecteerd.

1. Voor zowel productie als niet productiepijpleidingen, bepaalt u de wegen die in de Controle van de Ervaring op de **Controle van de Ervaring** tabel moeten worden omvat.

   * Pagina-paden moeten beginnen met `/` en zijn relatief ten opzichte van uw site.
   * Als uw site bijvoorbeeld `wknd.site` is en u `https://wknd.site/us/en/about-us.html` wilt opnemen in de Experience Audit, voert u het pad in `/us/en/about-us.html` .

   ![ die een weg voor de Controle van de Ervaring bepalen ](assets/experience-audit-add-page.png)

1. Tik of klik **toevoegen de Pagina** en de weg wordt auto-voltooid met het adres van uw milieu en toegevoegd aan de lijst van wegen.

   ![ het Opslaan weg aan de lijst ](assets/experience-audit-page-added.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klik **sparen** om uw pijpleiding te bewaren.

## Werken met de resultaten van Experience Audit {#understanding-experience-audit-results}

De Controle van de ervaring verstrekt geaggregeerde en gedetailleerde op paginaniveau testresultaten via de [ pagina van de de uitvoeringspijplijn van de productiepijplijn ](/help/implementing/cloud-manager/deploy-code.md).

* Met statistische gegevens worden de gemiddelde scores op de pagina&#39;s gemeten die zijn gecontroleerd op prestaties, toegankelijkheid, aanbevolen procedures, SEO (Search Engine Optimization).
* Afzonderlijke scores op paginaniveau zijn ook beschikbaar via de neerwaartse boor.
* Nadere gegevens over de scores zijn beschikbaar om de resultaten van de afzonderlijke tests te bekijken, samen met aanwijzingen voor het verhelpen van eventuele problemen die zijn vastgesteld.
* Een geschiedenis van de testresultaten wordt voortgeduurd binnen Cloud Manager om te bepalen als de veranderingen die in de pijpleiding worden geïntroduceerd om het even welke regressies van de vorige looppas omvatten.

### Samengevoegde scores {#aggregate-scores}

De score voor het geaggregeerde niveau is gebaseerd op de gemiddelde score van de pagina&#39;s die in de run zijn opgenomen. De verandering op het gezamenlijke niveau vertegenwoordigt de gemiddelde score van de pagina&#39;s in de huidige looppas in vergelijking met het gemiddelde van de scores van de vorige looppas, zelfs als de inzameling van pagina&#39;s die om worden gevormd om zijn omvat tussen looppas is veranderd.

Er is een score voor het geaggregeerde niveau voor elk type test, zoals prestaties, toegankelijkheid, SEO en aanbevolen procedures.

De metrische wijziging kan een van de volgende waarden hebben.

* **Positieve waarde** - de pagina&#39;s zijn op de geselecteerde test sinds de laatste looppas van de productiepijpleiding verbeterd.

* **Negatieve waarde** - de pagina&#39;s zijn op de geselecteerde test sinds de laatste looppas van de productiepijpleiding opnieuw gedrukt.

* **Geen Verandering** - de pagina&#39;s hebben het zelfde sinds de laatste looppas van de productiepijplijn gescoord.

* **n.v.t.** - Er was geen vorige beschikbare score om te vergelijken.

![ de resultaten van de Controle van de Ervaring ](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, is meer gedetailleerde paginaniveau-scoring beschikbaar. U kunt zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige testlooppas werden gescoord.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd en kunt u aangeven wat de problemen zijn als er mogelijkheden voor verbetering zijn gevonden.

![ pagina-vlakke scores ](/help/implementing/cloud-manager/assets/exp-audit-2.png)
