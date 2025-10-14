---
title: Naamgevingsconventies
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Naamgevingsconventies{#naming-conventions}

Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. Er worden echter AEM andere conventies voor de naam van paginaknooppunten opgelegd.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de AEM implementatie van de [&#x200B; nut JCR &#x200B;](#jcr-utilities).
* PageManager: de [&#x200B; Manager van de Pagina &#x200B;](#page-manager) verstrekt methodes voor de verrichtingen van het paginaniveau.
* Binnen de AEM-gebruikersinterface {#ui-behavior}

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[&#x200B; JcrUtil &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) is de AEM implementatie van de nut JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`
   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.
* `createValidName`
   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[&#x200B; PageManager &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) verstrekt methodes voor de verrichtingen van het paginaniveau, die op [&#x200B; worden gebaseerd JCRUtil &#x200B;](#jcr-utilities).

### Werking AEM UI {#ui-behavior}

De gebruikersinterface van de AEM bij het beheren van inhoud:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:
   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt
