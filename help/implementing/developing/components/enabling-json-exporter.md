---
title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
exl-id: e9be5c0c-618e-4b56-a365-fcdd185ae808
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# JSON-export inschakelen voor een component {#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De JSON-export is gebaseerd op [Verkoopmodellen](https://sling.apache.org/documentation/bundles/models.html)en de [Verkoopmodel exporteren](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) kader (dat zelf op [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

Dit betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Voer daarom de volgende twee stappen uit om JSON-export voor een willekeurige component mogelijk te maken.

* [Definieer een verkoopmodel voor de component](#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een verkoopmodel voor de component {#define-a-sling-model-for-the-component}

Eerst moet een Sling Model voor de component worden bepaald.

>[!NOTE]
>
>Zie het artikel voor een voorbeeld van het gebruik van Sling Models [Exporteurs van verkoopmodellen ontwikkelen in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter.html).

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Zo weet u zeker dat uw component zelfstandig kan worden geëxporteerd met de opdracht `.model` en de `.json` extensie.

Daarnaast wordt hiermee aangegeven dat de klasse Sling Model kan worden aangepast aan de `ComponentExporter` interface.

>[!NOTE]
>
>Jackson-annotaties worden gewoonlijk niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Hiermee zorgt u ervoor dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De `ExporterConstants` en `ComponentExporter` klassen komen uit `com.adobe.cq.export.json` bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om veelvoudige selecteurs naast te vormen `model` kiezer.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In dat geval echter `model` moet de eerste kiezer zijn en de extensie moet `.json`.

## De interface van het verkoopmodel notities aanbrengen {#annotate-the-sling-model-interface}

Om door het JSON Exporter-kader in aanmerking te worden genomen, moet de modelinterface de `ComponentExporter` interface (of `ContainerExporter`, in het geval van een containercomponent).

De overeenkomstige interface van het Model van de Verkoop (`MyComponent`) wordt vervolgens met behulp van [Jackson-annotaties](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes zouden moeten in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden hun JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getter. Dit kan worden voorkomen of overschreven door `@JsonIgnore` of `@JsonProperty` om de naam van de JSON-eigenschap te wijzigen.

## Voorbeeld {#example}

[De kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) ondersteunt JSON-export en kan als referentie worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

## Verwante documentatie {#related-documentation}

* [Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
* [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)
* [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en de [Component Inhoudsfragment](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)
