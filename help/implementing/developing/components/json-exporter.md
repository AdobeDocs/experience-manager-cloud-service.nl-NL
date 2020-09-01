---
title: JSON-exportfunctie voor services voor inhoud
description: AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, waarbij de aandacht niet op webpagina's wordt gevestigd. Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina's zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt.
translation-type: tm+mt
source-git-commit: 0799a817095558edd49b53ddc915c9474181fef7
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 4%

---


# JSON-exportfunctie voor services voor inhoud {#json-exporter-for-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM buiten de focus van webpagina&#39;s te veralgemenen.

Zij verstrekken de levering van inhoud aan kanalen die niet traditionele AEM Web-pagina&#39;s zijn, gebruikend gestandaardiseerde methodes die door om het even welke cliënt kunnen worden verbruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* Andere kanalen en aanraakpunten buiten AEM

Met inhoudsfragmenten die gestructureerde inhoud gebruiken, kunt u de inhoudsdiensten verlenen door JSON-exporter te gebruiken om de inhoud van een (y) AEM pagina in het formaat van het JSON-gegevensmodel te leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

## JSON-exportfunctie met kerncomponenten van inhoudsfragment {#json-exporter-with-content-fragment-core-components}

Met de AEM JSON-exportfunctie kunt u de inhoud van een (y) AEM pagina in de indeling van het JSON-gegevensmodel leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

Binnen AEM wordt de levering bereikt met behulp van de kiezer `model` en de `.json` extensie.

`.model.json`

1. Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. Zal inhoud leveren zoals:

   ![JSON-model van WKND-inhoud](assets/json-model-wknd.png)

U kunt de inhoud van een gestructureerd inhoudsfragment ook leveren door dit specifiek te activeren.

Dit wordt gedaan gebruikend de volledige weg aan het fragment (via `jcr:content`); bijvoorbeeld met een achtervoegsel zoals

`.../jcr:content/root/container/container/contentfragment.model.json`

De pagina kan één inhoudsfragment of meerdere componenten van verschillende typen bevatten. U kunt mechanismen zoals lijstcomponenten ook gebruiken om automatisch naar relevante inhoud te zoeken.

* Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
   ```

* Zal inhoud leveren zoals:

   ![JSON-model van WKND-inhoudsfragment](assets/json-model-wknd-content-fragment.png)

   >[!NOTE]
   >
   >U kunt uw eigen componenten [](enabling-json-exporter.md) aanpassen om tot deze gegevens toegang te hebben en te gebruiken.

   >[!NOTE]
   >
   >Hoewel het geen standaardimplementatie is, [worden](enabling-json-exporter.md#multiple-selectors) meerdere kiezers ondersteund, `model` maar dit moet wel de eerste zijn.

### Aanvullende informatie {#further-information}

Zie ook:

* HTTP-API voor assets
   * [HTTP-API voor assets](/help/assets/developer-reference-material-apis.md)
* Modellen voor verkopen:
   * [Sling Models - het associëren van een modelklasse met een middeltype sinds 130](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM met JSON:
   * [JSON-export inschakelen voor een component](enabling-json-exporter.md)

## Related Documentation {#related-documentation}

Zie voor meer informatie:

* [Inhoudsfragmenten in de gebruikershandleiding voor middelen](/help/assets/content-fragments/content-fragments.md)
* [Modellen van contentfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fundamentals/content-fragments.md)
* [Kerncomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/introduction.html) en de component [Inhoudsfragment](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/components/content-fragment-component.html)
