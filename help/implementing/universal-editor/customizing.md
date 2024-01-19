---
title: De gebruikersinterface aanpassen
description: Leer over de verschillende uitbreidingspunten die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 7ef3efa6e074778b7b3e3a8159056200b2663b30
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# De gebruikersinterface aanpassen {#customizing-ui}

Leer over de verschillende uitbreidingspunten die u toestaan om UI van de Universele Redacteur aan te passen om de behoeften van uw inhoudsauteurs te steunen.

## Publiceren uitschakelen {#disable-publish}

Voor bepaalde ontwerpworkflows moet de inhoud worden gecontroleerd voordat deze wordt gepubliceerd. In dergelijke situaties mag de optie om te publiceren niet beschikbaar zijn voor auteurs.

De **Publiceren** Deze knop kan daarom volledig in een app worden onderdrukt door de volgende metagegevens toe te voegen.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```
