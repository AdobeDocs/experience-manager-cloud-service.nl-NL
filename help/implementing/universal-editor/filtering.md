---
title: Componenten filteren
description: Leer hoe u de toegestane componenten per container in de Universele Redacteur kunt beperken gebruikend componentenfilters.
feature: Developing
role: Admin, Developer
exl-id: eeae8d7c-c563-4d9b-8c54-1098a4e98c18
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '153'
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
>Meer informatie over andere opties voor aanpassing en extensie die beschikbaar zijn in de Universal Editor vindt u in de documenten:
>
>* [&#x200B; het Aanpassen van de Universele Redacteur &#x200B;](/help/implementing/universal-editor/customizing.md)
>* [&#x200B; Uitbreidend de Universele Redacteur &#x200B;](/help/implementing/universal-editor/extending.md)
