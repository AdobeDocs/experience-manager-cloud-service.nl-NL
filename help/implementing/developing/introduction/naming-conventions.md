---
title: Naamgevingsconventies
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Naamgevingsconventies{#naming-conventions}

Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. AEM stelt echter andere conventies voor de naam van paginaknooppunten op.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de implementatie van AEM van de [&#x200B; nut JCR &#x200B;](#jcr-utilities).
* PageManager: de [&#x200B; Manager van de Pagina &#x200B;](#page-manager) verstrekt methodes voor de verrichtingen van het paginaniveau.
* In de gebruikersinterface van AEM {#ui-behavior}

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[&#x200B; JcrUtil &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/jcr/JcrUtil.html) is de implementatie van AEM van de nut JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`
   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.
* `createValidName`
   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[&#x200B; PageManager &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/api/PageManager.html) verstrekt methodes voor de verrichtingen van het paginaniveau, die op [&#x200B; worden gebaseerd JCRUtil &#x200B;](#jcr-utilities).

### Werking gebruikersinterface van AEM {#ui-behavior}

De gebruikersinterface van AEM bij het beheren van inhoud:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:
   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt
