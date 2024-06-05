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

De Audit van de ervaring is een eigenschap beschikbaar in de pijpleidingen van de Productie van de Plaatsen van de Manager van de Wolk die het plaatsingsproces bevestigt en helpt ervoor zorgen dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Breng geen regressies aan.

De controle van de ervaring in de Manager van de Wolk zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing werd geïntroduceerd.

Experience Audit wordt aangedreven door Google Lighthouse, een opensource tool uit Google.

>[!INFO]
>
>Met ingang van 31 augustus 2023 zal Experience Audit een overgang maken naar toonaangevende resultaten die specifiek zijn voor het mobiele platform. Metrische gegevens over mobiele prestaties zijn doorgaans lager dan die van desktopcomputers. Daarom moet u een verschuiving in de gerapporteerde prestaties na deze wijziging verwachten.

## Beschikbaarheid {#availability}

Experience Audit is beschikbaar voor Cloud Manager:

* Sites-productiepijpleidingen, standaard.
* Voorkant ontwikkelingspijpleidingen, optioneel.

Zie de [Configuratiesectie](#configuration) voor meer informatie over hoe te om de controle voor de facultatieve milieu&#39;s te vormen.

## Configuratie {#configuration}

De Experience Audit is standaard beschikbaar voor productiepijpleidingen. Het kan facultatief worden toegelaten voor front-end ontwikkelingspijpleidingen. In alle gevallen, moet u bepalen welke inhoudswegen tijdens pijpleidingsuitvoering worden geëvalueerd.

U vormt welke pagina&#39;s inbegrepen in de Controle van de Ervaring wanneer u opstelling uw pijpleiding zijn.

1. Afhankelijk van het type van pijpleiding u wenst te vormen, volg de richtingen aan:

   * Een nieuwe toevoegen [productiepijpleiding,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) als u de wegen wilt bepalen die door de controle moeten worden geëvalueerd.
   * Een nieuwe toevoegen [niet-productiepijpleiding,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) als u wenst om de controle op een front-end of ontwikkelings volledig-stapelpijpleiding toe te laten.
   * Of u kunt [een bestaande pijpleiding bewerken;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) en werkt de bestaande opties bij.

1. Als u toevoegt of een niet productiepijplijn uitgeeft waarvoor u de Controle van de Ervaring wilt gebruiken, moet u selecteren **Experience Audit** Selectievakje op de **Broncode** tab.

   ![Ervaring controleren inschakelen](assets/experience-audit-enable.jpg)

   * Dit is alleen nodig voor niet-productiepijpleidingen.
   * De **Experience Audit** wordt weergegeven wanneer het selectievakje is ingeschakeld.

1. Voor zowel productie als niet productie pijpleidingen, bepaalt u de wegen die in de Controle van de Ervaring op moeten worden omvat **Experience Audit** tab.

   * Pagina-paden moeten beginnen met `/` en zijn relatief ten opzichte van uw site.
   * Als uw site bijvoorbeeld `wknd.site` en zou graag `https://wknd.site/us/en/about-us.html` Voer in de Experience Audit het pad in `/us/en/about-us.html`.

   ![Een pad definiëren voor de Experience Audit](assets/experience-audit-add-page.png)

1. Tik of klik op **Pagina toevoegen** en het pad wordt automatisch ingevuld met het adres van de omgeving en toegevoegd aan de padlijst.

   ![Pad naar tabel opslaan](assets/experience-audit-page-added.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klikken **Opslaan** om uw pijpleiding te redden.

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

* **Positieve waarde** - De pagina&#39;s zijn verbeterd ten opzichte van de geselecteerde test sinds de laatste productiepijpleiding.

* **Negatieve waarde** - de pagina&#39;s zijn teruggelopen op de geselecteerde test sinds de laatste productiepijpleiding.

* **Geen wijziging** - De pagina&#39;s hebben hetzelfde gescand sinds de laatste productiepijpleiding.

* **NVT** - Er was geen vorige score beschikbaar om te vergelijken.

![Resultaten van controle door ervaring](/help/implementing/cloud-manager/assets/exp-audit-1.png)

### Scores op paginaniveau {#page-level-scores}

Door in een van de tests te boren, is meer gedetailleerde paginaniveau-scoring beschikbaar. U kunt zien hoe de individuele pagina&#39;s voor de specifieke test samen met de verandering van de vorige testlooppas werden gescoord.

Als u op de details van een afzonderlijke pagina klikt, krijgt u informatie over de elementen van de pagina die zijn geëvalueerd en kunt u aangeven wat de problemen zijn als er mogelijkheden voor verbetering zijn gevonden.

![Scores op paginaniveau](/help/implementing/cloud-manager/assets/exp-audit-2.png)
