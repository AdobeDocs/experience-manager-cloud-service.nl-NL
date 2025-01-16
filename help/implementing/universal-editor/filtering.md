---
title: Componenten filteren
description: Leer hoe u de toegestane componenten per container in de Universele Redacteur kunt beperken gebruikend componentenfilters.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 48c1a109c060db4ce19bf645723357008d51c572
workflow-type: tm+mt
source-wordcount: '151'
ht-degree: 0%

---


# Componenten filteren {#filtering-components}

Leer hoe u de toegestane componenten per container in de Universele Redacteur kunt beperken gebruikend componentenfilters.

## Filters {#filters}

Wanneer u de Universal Editor gebruikt, kunt u de toegestane componenten per containercomponent beperken. Hiervoor moet u een extra scripttag invoeren, die naar de filterdefinitie verwijst.

```html
<script type="application/vnd.adobe.aue.filter+json" src="/static/filter-definition.json"></script>
```

Een filterdefinitie zou als het volgende kunnen kijken, die een container zou beperken om slechts het toevoegen van tekst en beelden toe te staan.

```json
[
  {
    "id": "container-filter",
     "components": ["text", "image"]
   }
]
```

Vervolgens kunt u naar de filterdefinitie van de containercomponent verwijzen door de eigenschap `data-aue-filter` toe te voegen en de id door te geven van het filter dat u eerder hebt gedefinieerd.

```html
data-aue-filter="container-filter"
```

Als u het kenmerk `components` in een filterdefinitie instelt op `null` , worden alle componenten toegestaan, net als wanneer er geen filter is.

```json
[
  {
    "id": "another-container-filter",
     "components": null
   }
]
```

>[!TIP]
>
>Leer over andere aanpassing en uitbreidingsopties beschikbaar aan de Universele Redacteur in het document [ die en de Universele Redacteur aanpassen uitbreiden.](/help/implementing/universal-editor/customizing.md)
