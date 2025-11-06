---
title: JSON-exportfunctie voor services voor inhoud
description: AEM Content Services is ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, maar niet alleen op webpagina's. Ze leveren inhoud aan kanalen die geen traditionele AEM-webpagina's zijn, met behulp van gestandaardiseerde methoden die door elke client kunnen worden gebruikt.
exl-id: d3ddffb7-cef9-4c86-aa31-175f13f9b4a5
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# JSON-exportfunctie voor services voor inhoud {#json-exporter-for-content-services}

AEM Content Services zijn ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, maar niet alleen via webpagina&#39;s.

Ze leveren inhoud aan kanalen die geen traditionele AEM-webpagina&#39;s zijn, met behulp van gestandaardiseerde methoden die door elke client kunnen worden gebruikt. Deze kanalen kunnen zijn:

* Toepassingen voor één pagina
* Systeemeigen mobiele toepassingen
* Andere kanalen en aanraakpunten buiten AEM

Met inhoudsfragmenten die gestructureerde inhoud gebruiken, kunt u inhoudsdiensten verlenen door de JSON-exporter te gebruiken om de inhoud van een (y) AEM-pagina in JSON-gegevensmodelindeling te leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

## JSON-exportfunctie met kerncomponenten van inhoudsfragment {#json-exporter-with-content-fragment-core-components}

Met de AEM JSON-exportfunctie kunt u de inhoud van een (y) AEM-pagina in JSON-indeling voor gegevensmodellen leveren. Dit kan dan door uw eigen toepassingen worden verbruikt.

In AEM wordt de levering bereikt met de extensie selector `model` en `.json` .

`.model.json`

1. Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks.model.json
   ```

1. Hiermee wordt inhoud geleverd, zoals:

   ![ JSON model van inhoud WKND ](assets/json-model-wknd.png)

U kunt de inhoud van een gestructureerd inhoudsfragment ook leveren door dit specifiek te activeren.

Dit gebeurt met het volledige pad naar het fragment (via de `jcr:content` ), bijvoorbeeld met een achtervoegsel zoals.

`.../jcr:content/root/container/container/contentfragment.model.json`

De pagina kan één inhoudsfragment of meerdere componenten van verschillende typen bevatten. U kunt mechanismen zoals lijstcomponenten ook gebruiken om automatisch naar relevante inhoud te zoeken.

* Bijvoorbeeld een URL zoals:

  ```shell
  http://localhost:4502/content/wknd/language-masters/en/magazine/guide-la-skateparks/jcr:content/root/container/container/contentfragment.model.json
  ```

* Hiermee wordt inhoud geleverd, zoals:

  ![ JSON model van WKND inhoudsfragment ](assets/json-model-wknd-content-fragment.png)

  >[!NOTE]
  >
  >U kunt [ uw eigen componenten ](enabling-json-exporter.md) aanpassen om tot dit gegeven toegang te hebben en te gebruiken.

  >[!NOTE]
  >
  >Hoewel niet een standaardimplementatie, [ worden de veelvoudige selecteurs gesteund ](enabling-json-exporter.md#multiple-selectors), maar `model` moet de eerste zijn.

### Aanvullende informatie {#further-information}

* ASSETS HTTP API
   * [ASSETS HTTP API](/help/assets/developer-reference-material-apis.md)
* Modellen voor verkopen:
   * [ het Verdelen Modellen - het associëren van een modelklasse met een middeltype sinds 130 ](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)
* AEM met JSON:
   * [JSON-export inschakelen voor een component](enabling-json-exporter.md)

## Verwante documentatie {#related-documentation}

* [Inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)
* [Modellen van inhoudsfragmenten](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-cloud/authoring/fragments/content-fragments.md)
* [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en de [ component van het Fragment van de Inhoud ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html)
