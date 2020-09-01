---
title: Naamgevingsconventies
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Naamgevingsconventies{#naming-conventions}

Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository. Er worden echter AEM andere conventies voor de naam van paginaknooppunten opgelegd.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de AEM uitvoering van de [GCO-voorzieningen](#jcr-utilities).
* PageManager: biedt [Paginabeheer](#page-manager) methoden voor bewerkingen op paginaniveau.
* Binnen de AEM UI {#ui-behavior}

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[JcrUtil](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) is de AEM implementatie van de hulpprogramma&#39;s van het JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`
   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.
* `createValidName`
   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[PageManager](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/api/PageManager.html) biedt methoden voor bewerkingen op paginaniveau op basis van [JCRUtil](#jcr-utilities).

### Werking AEM UI {#ui-behavior}

De gebruikersinterface van de AEM bij het beheren van inhoud:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:
   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt
