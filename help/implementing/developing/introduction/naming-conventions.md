---
title: Naamgevingsconventies
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Naamgevingsconventies{#naming-conventions}

Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. Er worden echter AEM andere conventies voor de naam van paginaknooppunten opgelegd.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de AEM implementatie van de [JCR-hulpprogramma&#39;s](#jcr-utilities).
* PageManager: de [Paginabeheer](#page-manager) biedt methoden voor bewerkingen op paginaniveau.
* Binnen AEM UI {#ui-behavior}

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) JcrUtilis is de AEM implementatie van de hulpprogramma&#39;s van het JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`
   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.
* `createValidName`
   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) PageManager biedt methoden voor bewerkingen op paginaniveau op basis van  [JCRUtil](#jcr-utilities).

### Werking AEM UI {#ui-behavior}

De gebruikersinterface van de AEM bij het beheren van inhoud:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:
   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt
