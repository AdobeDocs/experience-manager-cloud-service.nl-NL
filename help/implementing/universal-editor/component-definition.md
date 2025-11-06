---
title: Componentdefinitie
description: Begrijp het JSON-contract tussen de componentdefinitie en de Universal Editor in detail.
feature: Developing
role: Admin, Developer
exl-id: e1bb1a54-50c0-412a-a8fd-8167c6f47d2b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 0%

---

# Componentdefinitie {#component-definition}

Begrijp het JSON-contract tussen de componentdefinitie en de Universal Editor in detail.

## Overzicht {#overview}

In het bestand `component-definition.json` worden de componenten gedefinieerd die beschikbaar zijn voor de auteurs van de inhoud voor het project. In dit document wordt in detail uitgelegd wat het doel van dit bestand is en hoe de Universal Editor dit gebruikt om pagina-ontwerpcomponenten aan uw auteurs voor te stellen.

>[!TIP]
>
>Voor een overzicht van de inhoud modellerend proces, te zien gelieve het document [&#x200B; Modellering van de Inhoud voor de Authoring van WYSIWYG met de Projecten van Edge Delivery Services.](https://www.aem.live/developer/component-model-definitions)

>[!TIP]
>
>U hoeft geen geheel nieuw `component-definition.json` -bestand te maken. Het project boilerplate dat u aan [&#x200B; laarzentrekker uw project &#x200B;](https://www.aem.live/developer/ue-tutorial) gebruikt bevat a [&#x200B; volledig-functionerend `component-definition.json` dossier &#x200B;](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) dat u aan uw behoeften kunt aanpassen.

## Voorbeeldcomponentdefinitie {#example}

Hieronder volgt een volledig, maar eenvoudig `component-definition.json` als voorbeeld.

```json
{
  "groups":[
    {
      "title":"General Components",
      "id":"general",
      "components":[
        {
          "title":"Text",
          "id":"text",
          "model": "text",
          "filter": "texts",
          "plugins":{
            "aem":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            },
            "aem65":{
              "page":{
                "resourceType":"wknd/components/text",
                "template":{
                  "text":"Default Text",
                  "name":"Text"
                }
              }
            }
          }
        }
      ]
    }
  ]
}
```

## `groups` {#groups}

`groups` bepaalt de groepen componenten die de auteur in de Universele Redacteur ziet wanneer het klikken **&#x200B;**&#x200B;pictogram in het eigenschappenpaneel van de redacteur [&#x200B; toevoegt een nieuwe component aan een pagina &#x200B;](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components). Groepen helpen bij het ordenen van de componenten. De gemeenschappelijke groepen zouden **Algemene Componenten** en **Geavanceerde Componenten** kunnen zijn.

* `title` definieert de tekstuele beschrijving van de groep die wordt weergegeven in de gebruikersinterface van de editor.
* `id` geeft de groep op unieke wijze aan.

## `components` {#components}

`components` definieert welke componenten tot een groep behoren.

* `title` definieert de tekstuele beschrijving van de component die in de UI wordt weergegeven.
* `id` geeft de component op unieke wijze aan.
   * Het [&#x200B; componentenmodel &#x200B;](/help/implementing/universal-editor/field-types.md#model-structure) van het zelfde `id` bepaalt de gebieden van de component.
   * Omdat het uniek is kan het, bijvoorbeeld, in a [&#x200B; filterdefinitie &#x200B;](/help/implementing/universal-editor/filtering.md) worden gebruikt om te bepalen welke componenten aan een container kunnen worden toegevoegd.
* `model` bepaalt welk [&#x200B; model &#x200B;](/help/implementing/universal-editor/field-types.md#model-structure) met de component wordt gebruikt.
   * Het model wordt daardoor gehandhaafd centraal in de componentendefinitie en te hoeven niet [&#x200B; worden gespecificeerd de instrumentatie.](/help/implementing/universal-editor/field-types.md#instrumentation)
   * Op deze manier kunt u componenten over containers verplaatsen.
* `filter` bepaalt welke [&#x200B; filter &#x200B;](/help/implementing/universal-editor/filtering.md) met de component zou moeten worden gebruikt.

## `plugins` {#plugins}

`plugins` definieert welke plug-in verantwoordelijk is voor het voortduren van de component. Veelgebruikte plug-ins zijn:

* `aem` voor [&#x200B; AEM as a Cloud Service.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service)
* `aem65` voor [&#x200B; AEM 6.5. &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65) en [&#x200B; AEM 6.5 LTS &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts)
* `xwalk` voor [&#x200B; Authoring met AEM Sites voor Edge Delivery Services.](https://www.aem.live/developer/ue-tutorial)

## `page` of `cf` {#page-cf}

Nadat `plugin` is gedefinieerd, moet u aangeven of het een pagina-gerelateerd of fragmentgerelateerd bestand is.

* `page` geeft aan dat de component inhoud op de huidige pagina is.
* `cf` wijst erop dat de component met inhoud binnen a [&#x200B; het Fragment van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments.md) verwant is.

### `page` {#page}

Als de component inhoud op de pagina is, kunt u de volgende informatie verstrekken.

* `resourceType` bepaalt het [&#x200B; Verschuiven &#x200B;](/help/implementing/developing/introduction/sling-cheatsheet.md) `resourceType` wordt gebruikt voor het teruggeven van de component die.
* `template` definieert optionele sleutel/waarden die automatisch naar de nieuwe component moeten worden geschreven en definieert welk filter en/of model op de component moet worden toegepast.
   * Nuttig voor verklarende, steekproef, of placeholder tekst.

#### `template` {#template}

Door optionele sleutel/waardeparen op te geven, kan `template` deze automatisch naar de nieuwe component schrijven. Daarnaast kunnen ook de volgende optionele waarden worden opgegeven.

### `cf` {#cf}

Als de component verwant is aan inhoud binnen een inhoudsfragment, kunt u de volgende informatie verstrekken.

* `name` definieert een optionele naam die is opgeslagen in de JCR voor de nieuwe component.
   * Alleen informatief en wordt gewoonlijk niet in de gebruikersinterface weergegeven als de `title` is.
* `cfModel` bepaalt het [&#x200B; 2&rbrace; model van het Fragment van de Inhoud &lbrace;voor de onlangs-gecreeerde component.](/help/assets/content-fragments/content-fragments-models.md)
* `cfFolder` definieert in welke map het inhoudsfragment moet worden gemaakt.
* `title` definieert de titel van het nieuwe inhoudsfragment.
* `description` definieert een beschrijving van het nieuwe inhoudsfragment.
* `template` definieert optionele sleutel(waarden) die automatisch naar het nieuwe inhoudsfragment moeten worden geschreven.
   * Nuttig voor verklarende, steekproef, of placeholder tekst.

### `cf` Kan worden geïmporteerd {#cf-implied}

Als de pagina [&#x200B; &#x200B;](/help/implementing/universal-editor/getting-started.md#instrument-page) van instrumenten wordt voorzien om aan een verwijzingsgebied te richten, zal `cf` worden verondersteld.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

In een dergelijk geval wordt `cf` aangenomen, omdat `data-aue-prop` naar een verwijzingsveld verwijst. Zonder de instructie `data-aue-prop` gaat de Universal Editor ervan uit dat `page` wordt gebruikt, omdat de componenten in dat geval niet via een referentieveld zijn gekoppeld.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

Componenten zijn eenvoudigweg subknooppunten onder de bron.
