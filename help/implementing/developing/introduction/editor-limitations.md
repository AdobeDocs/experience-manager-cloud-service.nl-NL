---
title: Beperkingen in paginaeditor
description: De Pagina-editor maakt gebruik van overlays om te werken met inhoud die is opgesloten in een iframe. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars.
exl-id: 6a4f0e43-1076-4da9-95dc-9c5bf83e30d0
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---


# Beperkingen in paginaeditor {#editor-limitations}

[&#x200B; de Redacteur van de Pagina &#x200B;](/help/sites-cloud/authoring/page-editor/introduction.md) maakt gebruik van bekledingen om met inhoud in te wisselen die in een iframe wordt beperkt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars. Deze pagina geeft een overzicht van deze beperkingen en biedt waar mogelijk oplossingen of tijdelijke oplossingen.

## Functionele beperkingen {#functional-limitations}

Een auteur kan de volgende functionele beperkingen tegenkomen wanneer hij de editor gebruikt om pagina&#39;s te schrijven.

### Koppelingen niet actief {#links-not-active}

Wanneer [&#x200B; het uitgeven van een pagina &#x200B;](/help/sites-cloud/authoring/page-editor/edit-content.md), zijn de verbindingen niet actief.

* [&#x200B; Schakelaar aan **Voorproef** wijze &#x200B;](/help/sites-cloud/authoring/page-editor/introduction.md#preview-mode) om het gebruiken van de verbindingen in uw inhoud te navigeren.

### Structuurpagina&#39;s {#structure-pages}

Pagina&#39;s kunnen geen naam `structure` krijgen. Pagina&#39;s met de naam `structure` kunnen niet worden bewerkt in de pagina-editor.

## CSS-beperkingen {#css-limitations}

Een ontwikkelaar kan de volgende beperkingen ondervinden bij de interactie van de editor met CSS.

### Absoluut gepositioneerde elementen {#absolutely-positioned-elements}

Absoluut gepositioneerde elementen kunnen problemen veroorzaken in de positie van de overlay.

* Als dit gebeurt, zorg ervoor dat de afmetingen van absoluut gepositioneerd element correct zijn omdat de redacteur tot een bekleding met de nauwkeurige zelfde afmetingen zal leiden.

### vh Eenheden {#vh-units}

`vh` -eenheden worden niet ondersteund, omdat de hoogte van het iframe automatisch moet worden aangepast door AEM.

### Vaste achtergrondafbeeldingen {#fixed-background-images}

Vaste achtergrondafbeeldingen worden mogelijk niet als vast weergegeven tijdens het schuiven omdat deze zijn ingesloten in een iframe.

* Het selecteren van **Pagina van de Mening zoals Gepubliceerd** in de acties van de kopbalbar toont behoorlijk de pagina.

### 100% hoogte {#height}

100% hoogte wordt niet ondersteund op het tekstelement van een pagina.

* U kunt doorwerken om een hoofdtekst voor een volledig scherm te implementeren door het tekstelement als volgt uit te rekken:

```xml
body {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
}
```

### Marge samenvouwen {#margin-collapsing}

Problemen met samenvouwen van marges kunnen worden gezien als het eerste onderliggende element van het body-element een marge heeft.

* De oplossing is een duidelijke oplossing op het niveau van het lichaamselement als volgt toe te voegen:

```xml
body:before, body:after{
    content: ' ';
    display: table;
}
```
