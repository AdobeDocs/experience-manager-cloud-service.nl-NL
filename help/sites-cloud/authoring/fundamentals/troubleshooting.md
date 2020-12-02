---
title: Problemen met AEM bij ontwerpen oplossen
description: Sommige problemen die u bij het gebruik van AEM tegenkomt
translation-type: tm+mt
source-git-commit: 16725342c1a14231025bbc1bafb4c97f0d7cfce8
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 13%

---


# Problemen met AEM oplossen bij ontwerpen {#troubleshooting-aem-when-authoring}

De volgende sectie behandelt sommige kwesties die u wanneer het gebruiken van AEM zou kunnen ontmoeten, samen met suggesties op hoe te om hen problemen op te lossen.

## Oude paginaversie nog steeds op gepubliceerde site {#old-page-version-still-on-published-site}

* **Probleem**:
   * U hebt wijzigingen aangebracht in een pagina en de pagina gepubliceerd naar de publicatiesite, maar de *oude*-versie van de pagina wordt nog steeds weergegeven op de publicatiesite.
* **Reden**:
   * Dit kan verscheidene oorzaken hebben, meestal het geheime voorgeheugen (of uw lokale browser of de Verzender), hoewel het soms een kwestie met de replicatierij kan zijn.
* **Oplossingen**:
   * Hier zijn verschillende mogelijkheden:
   * Controleer of de pagina correct is gerepliceerd. Controleer de paginastatus en, indien nodig, de status van de replicatiewachtrij.
   * Wis de cache in uw lokale browser en open de pagina opnieuw.
   * Voeg `?` aan het eind van pagina URL toe. Bijvoorbeeld:
      * `http://<host>:<port>/sites.html/content?`
      * Hiermee wordt de pagina rechtstreeks bij AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de cache van de Dispatcher moet wissen.
   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Componenthandelingen niet zichtbaar op werkbalk {#component-actions-not-visible-on-toolbar}

* **Probleem**:
   * Het volledige bereik van toepasselijke componentacties is niet zichtbaar wanneer u een inhoudspagina bewerkt in de auteursomgeving.
* **Reden**:
   * In zeldzame gevallen kan een eerdere actie gevolgen hebben voor de werkbalk.
* **Oplossing**:
   * Vernieuw de pagina.
