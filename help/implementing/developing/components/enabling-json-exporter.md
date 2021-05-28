---
title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
source-git-commit: ac64ca485391d843c0ebefcf86e80b4015b72b2f
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 1%

---

# JSON-export inschakelen voor een component {#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De JSON-export is gebaseerd op [Sling Models](https://sling.apache.org/documentation/bundles/models.html) en op het [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130)-framework (dat zelf afhankelijk is van [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Daarom zult u deze twee stappen moeten volgen om de uitvoer van JSON op om het even welke component toe te laten.

* [Definieer een Sling-model voor de component](#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een Sling-model voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Zie het artikel [Sling Model Exporters ontwikkelen in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html) voor een voorbeeld van het gebruik van Sling Modellen.

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Dit zorgt ervoor dat uw component zelfstandig kan worden geëxporteerd met de kiezer `.model` en de extensie `.json`.

Daarnaast wordt hiermee aangegeven dat de klasse Sling Model kan worden aangepast in de interface `ComponentExporter`.

>[!NOTE]
>
>Jackson-annotaties worden gewoonlijk niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De `ExporterConstants` en `ComponentExporter` klassen komen uit de `com.adobe.cq.export.json` bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruiksgeval is, is het mogelijk om veelvoudige selecteurs naast `model` selecteur te vormen.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In een dergelijk geval moet de `model`-kiezer echter de eerste kiezer zijn en moet de extensie `.json` zijn.

## Annoteer de Sling Model Interface {#annotate-the-sling-model-interface}

Om door het kader van de Exporteur van JSON in aanmerking te worden genomen, zou de Model interface `ComponentExporter` interface (of `ContainerExporter`, in het geval van een containercomponent) moeten uitvoeren.

De overeenkomstige interface van het Verzamelmodel (`MyComponent`) zou dan worden geannoteerd gebruikend [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getter. Dit kan worden voorkomen of met `@JsonIgnore` of `@JsonProperty` worden met voeten getreden om het bezit anders te noemen JSON.

## Voorbeeld {#example}

[De ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) Componenten van de Kern steunen de uitvoer JSON en kunnen als verwijzing worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

## Verwante documentatie {#related-documentation}

Zie voor meer informatie:

* [Inhoudsfragmenten in de gebruikershandleiding voor middelen](/help/assets/content-fragments/content-fragments.md)
* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [De ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) Componenten van de kern en de component van het Fragment van de  [Inhoud](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)
