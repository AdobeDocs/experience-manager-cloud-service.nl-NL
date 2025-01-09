---
title: Componentdefinitie
description: Begrijp het JSON-contract tussen de componentdefinitie en de Universal Editor in detail.
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 7f54d2ee61d2b92e7a0f02c66ce8ee5cdbedd73c
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Componentdefinitie {#component-definition}

Begrijp het JSON-contract tussen de componentdefinitie en de Universal Editor in detail.

## Overzicht {#overview}

In het bestand `component-definition.json` worden de componenten gedefinieerd die beschikbaar zijn voor de auteurs van de inhoud voor het project. In dit document wordt in detail uitgelegd wat het doel van dit bestand is en hoe de Universal Editor dit gebruikt om pagina-ontwerpcomponenten aan uw auteurs voor te stellen.

>[!TIP]
>
>Voor een overzicht van de inhoud modellerend proces, te zien gelieve het document [ Modellering van de Inhoud voor de Authoring van WYSIWYG met de Projecten van Edge Delivery Services.](/help/edge/wysiwyg-authoring/content-modeling.md)

>[!TIP]
>
>U hoeft geen geheel nieuw `component-definition.json` -bestand te maken. Het project boilerplate dat u aan [ laarzentrekker uw project ](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) gebruikt bevat a [ volledig-functionerend `component-definition.json` dossier ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/blob/main/component-definition.json) dat u aan uw behoeften kunt aanpassen.

## Voorbeeldcomponentdefinitie {#example}

Hieronder volgt een volledig, maar eenvoudig `component-definition.json` als voorbeeld.

```json
{
  "groups": [
    {
      "title": "General Components",
      "id": "general",
      "components": [
        {
          "title": "Text",
          "id": "text",
          "plugins": {
            "aem": {
              "page": {
                "resourceType": "wknd/components/text",
                "template": {
                  "text": "Default Text"
                }
              }
            },
            "aem65": {
              "page": {
                "resourceType": "wknd/components/text",
                "template": {
                  "text": "Default Text"
                }
              }
            }
          }
        },
      }
   ]
}
```

## `groups` {#groups}

`groups` bepaalt de groepen componenten die de auteur in de Universele Redacteur ziet wanneer het klikken **** pictogram in het eigenschappenpaneel van de redacteur [ toevoegt een nieuwe component aan een pagina.](/help/sites-cloud/authoring/universal-editor/authoring.md#adding-components) Met groepen kunt u de componenten ordenen. De gemeenschappelijke groepen zouden **Algemene Componenten** en **Geavanceerde Componenten** kunnen zijn.

* `title` definieert de tekstuele beschrijving van de groep die wordt weergegeven in de gebruikersinterface van de editor.
* `id` geeft de groep op unieke wijze aan.

## `components` {#components}

`components` definieert welke componenten tot een groep behoren.

* `title` definieert de tekstuele beschrijving van de component die in de UI wordt weergegeven.
* `id` geeft de component op unieke wijze aan.
   * Het [ componentenmodel ](/help/implementing/universal-editor/field-types.md#model-structure) van het zelfde `id` bepaalt de gebieden van de component.
   * Omdat het uniek is kan het, bijvoorbeeld, in a [ filterdefinitie ](/help/implementing/universal-editor/customizing.md#filtering-components) worden gebruikt om te bepalen welke componenten aan een container kunnen worden toegevoegd.

## `plugins` {#plugins}

`plugins` definieert welke plug-in verantwoordelijk is voor het voortduren van de component. Veelgebruikte plug-ins zijn:

* `aem` voor AEM as a Cloud Service.
* `aem5` voor AEM 6.5.
* `xwalk` voor AEM as a Cloud Service WYSIWYG authoring.

## `page` of `cf` {#page-cf}

Nadat `plugin` is gedefinieerd, moet u aangeven of het een pagina-gerelateerd of fragmentgerelateerd bestand is.

* `page` geeft aan dat de component inhoud op de huidige pagina is.
* `cf` wijst erop dat de component met inhoud binnen a [ het Fragment van de Inhoud verwant is.](/help/assets/content-fragments/content-fragments.md)

### `page` {#page}

Als de component inhoud op de pagina is, kunt u de volgende informatie verstrekken.

* `name` definieert een optionele naam die is opgeslagen in de JCR voor de nieuwe component.
   * Alleen informatief en wordt gewoonlijk niet in de gebruikersinterface weergegeven als de `title` is.
* `resourceType` bepaalt het [ Verschuiven ](/help/implementing/developing/introduction/sling-cheatsheet.md) `resourceType` wordt gebruikt voor het teruggeven van de component die.
* `template` definieert optionele sleutel(waarden) die automatisch naar de nieuwe component moeten worden geschreven.
   * Nuttig voor verklarende, steekproef, of placeholder tekst.

### `cf` {#cf}

Als de component verwant is aan inhoud binnen een inhoudsfragment, kunt u de volgende informatie verstrekken.

* `name` definieert een optionele naam die is opgeslagen in de JCR voor de nieuwe component.
   * Alleen informatief en wordt gewoonlijk niet in de gebruikersinterface weergegeven als de `title` is.
* `cfModel` bepaalt het [ 2} model van het Fragment van de Inhoud {voor de onlangs-gecreeerde component.](/help/assets/content-fragments/content-fragments-models.md)
* `cfFolder` definieert in welke map het inhoudsfragment moet worden gemaakt.
* `title` definieert de titel van het nieuwe inhoudsfragment.
* `description` definieert een beschrijving van het nieuwe inhoudsfragment.
* `template` definieert optionele sleutel(waarden) die automatisch naar het nieuwe inhoudsfragment moeten worden geschreven.
   * Nuttig voor verklarende, steekproef, of placeholder tekst.

### `cf` Kan worden geïmporteerd {#cf-implied}

Als de pagina [ ](/help/implementing/universal-editor/getting-started.md#instrument-page) van instrumenten wordt voorzien om aan een verwijzingsgebied te richten, zal `cf` worden verondersteld.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container" data-aue-prop="field"></div>
```

In een dergelijk geval wordt `cf` aangenomen, omdat `data-aue-prop` naar een verwijzingsveld verwijst. Zonder de instructie `data-aue-prop` gaat de Universal Editor ervan uit dat `page` wordt gebruikt, omdat de componenten in dat geval niet via een referentieveld zijn gekoppeld.

```html
<div data-aue-resource="urn:aem:/content" data-aue-type="container"></div>
```

Componenten zijn eenvoudigweg subknooppunten onder de bron.
