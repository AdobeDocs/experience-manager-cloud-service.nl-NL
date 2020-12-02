---
title: Editor-beperkingen
description: De editor in de interface met aanraakbediening maakt gebruik van overlays voor interactie met inhoud die zich in een iframe bevindt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars.
translation-type: tm+mt
source-git-commit: fee73b5f5ba69422494efe554ac5aa62c046ad86
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---


# Editor-beperkingen {#editor-limitations}

De editor in de interface met aanraakbediening maakt gebruik van overlays voor interactie met inhoud die zich in een iframe bevindt. Deze interactie leidt tot sommige beperkingen in zowel gebruik van de redacteur als ook voor ontwikkelaars. Deze pagina geeft een overzicht van deze beperkingen en biedt waar mogelijk oplossingen of tijdelijke oplossingen.

## Functionele beperkingen {#functional-limitations}

Een auteur kan de volgende functionele beperkingen tegenkomen wanneer hij de editor gebruikt om pagina&#39;s te schrijven.

### Koppelingen niet actief {#links-not-active}

Wanneer [een pagina bewerken](/help/sites-cloud/authoring/fundamentals/editing-content.md), zijn koppelingen niet actief.

* [Schakel over naar  **** ](/help/sites-cloud/authoring/fundamentals/editing-content.md#preview-mode) Voorvertoning om te navigeren met de koppelingen in de inhoud.

### Structuurpagina&#39;s {#structure-pages}

De pagina&#39;s kunnen niet `structure` worden genoemd. Pagina&#39;s met de naam `structure` kunnen niet worden bewerkt in de pagina-editor.

## CSS-beperkingen {#css-limitations}

Een ontwikkelaar kan de volgende beperkingen ondervinden bij de interactie van de editor met CSS.

### Absoluut gepositioneerde elementen {#absolutely-positioned-elements}

Absoluut gepositioneerde elementen kunnen problemen veroorzaken in de positie van de overlay.

* Als dit gebeurt, zorg ervoor dat de afmetingen van absoluut gepositioneerd element correct zijn omdat de redacteur tot een bekleding met de nauwkeurige zelfde afmetingen zal leiden.

### vh-eenheden {#vh-units}

`vh` De eenheden worden niet ondersteund omdat de hoogte van het iframe automatisch moet worden aangepast door AEM.

### Vaste achtergrondafbeeldingen {#fixed-background-images}

Vaste achtergrondafbeeldingen worden mogelijk niet als vast weergegeven tijdens het schuiven omdat deze zijn ingesloten in een iframe.

* Als u **Pagina weergeven als gepubliceerd** selecteert in de acties op de kopbalk, wordt de pagina correct weergegeven.

### 100% hoogte {#height}

100% hoogte wordt niet ondersteund op het tekstelement van een pagina.

* U kunt de hoofdtekst van een volledig scherm opnieuw instellen door het hoofdelement als volgt uit te rekken:

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
