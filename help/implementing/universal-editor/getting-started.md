---
title: Aan de slag met de Universal Editor in AEM
description: Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8357caf2b0d396f6a1bd7b6160d6b48d8d6c026c
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---


# Aan de slag met de Universal Editor in AEM {#getting-started}

Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.

>[!TIP]
>
>Als u in een voorbeeld liever zou duiken, kunt u de [ Universele SteekproefApp van de Redacteur op GitHub herzien.](https://github.com/adobe/universal-editor-sample-editable-app)

Hoewel de Universal Editor inhoud uit elke bron kan bewerken, wordt in dit document een AEM-app als voorbeeld gebruikt. Dit document begeleidt u door deze stappen.

## De pagina instrumenteren {#instrument-page}

De Universal Editor heeft een JavaScript-bibliotheek nodig om de pagina in de editor te kunnen renderen en bewerken.

Bovendien vereist de Universele dienst van de Redacteur a [ eenvormige middelnaam (URN) ](https://en.wikipedia.org/wiki/Uniform_Resource_Name) om het correcte backendesysteem voor de inhoud in app te identificeren en te gebruiken die wordt uitgegeven. Daarom wordt een schema URN vereist om inhoud terug naar inhoudsmiddelen in kaart te brengen.

### Inclusief de Universal Editor CORS-bibliotheek {#cors-library}

Als u wilt dat de Universal Editor verbinding maakt met uw app, moet uw app de Universal Editor CORS-bibliotheek bevatten. Voeg het volgende script toe aan uw app.

```html
 <script src="https://universal-editor-service.adobe.io/cors.js" async></script>
```

### Verbindingen maken {#connections}

Verbindingen die in de app worden gebruikt, worden als `<meta>` -tags opgeslagen in de pagina&#39;s `<head>` .

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - Dit is een classificatie van de verbinding met twee opties.
   * `system` - Voor eindpunten van verbindingen
   * `config` - voor [ bepalend facultatieve configuratiemontages ](#configuration-settings)
* `<referenceName>` - Dit is een korte naam die opnieuw wordt gebruikt in het document om de verbinding te identificeren. Bijvoorbeeld: `aemconnection`
* `<protocol>` - Hiermee wordt aangegeven welke persistentie-insteekmodule van de Universal Editor Persistence Service moet worden gebruikt. Bijvoorbeeld: `aem`
* `<url>` - Dit is de URL naar het systeem waar de wijzigingen moeten worden voortgezet. Bijvoorbeeld: `http://localhost:4502`

De id `urn:adobe:aue:system` vertegenwoordigt de verbinding voor de Adobe Universal Editor.

`data-aue-resource` s zal het `urn` voorvoegsel gebruiken om het herkenningsteken te verkorten.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Dit is de benoemde referentie die wordt vermeld in de tag `<meta>` . Bijvoorbeeld: `aemconnection`
* `<resource>` - Dit is een aanwijzer naar de bron in het doelsysteem. Bijvoorbeeld een AEM inhoudspad zoals `/content/page/jcr:content`

>[!TIP]
>
>Zie het document [ Attributen en Types ](attributes-types.md) voor verdere details over de gegevensattributen en de types die de Universele Redacteur vereist.

### Voorbeeldverbinding {#example}

```html
<meta name="urn:adobe:aue:system:<referenceName>" content="<protocol>:<url>">

<html>
<head>
    <meta name="urn:adobe:aue:system:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:adobe:aue:system:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul data-aue-resource="urn:aemconnection:/content/example/list" data-aue-type="container">
            <li data-aue-resource="urn:aemconnection:/content/example/listitem" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">Jane Doe</p>
              <p data-aue-prop="title" data-aue-type="text">Journalist</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>

...

            <li data-aue-resource="urn:fcsconnection:/documents/mytext" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">John Smith</p>
              <p data-aue-resource="urn:aemconnection:/content/example/another-source" data-aue-prop="title" data-aue-type="text">Photographer</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

### Configuratie-instellingen {#configuration-settings}

U kunt het voorvoegsel `config` in uw verbinding URN gebruiken om dienst en uitbreidingseindpunten indien nodig te plaatsen.

Als u de Universal Editor-service niet wilt gebruiken, die wordt gehost op Adobe, maar uw eigen gehoste versie, kunt u dit instellen in een metatag. Om het standaardde diensteindpunt te beschrijven dat de Universele Redacteur verstrekt, plaats uw eigen de diensteindpunt:

* Metanaam - `urn:adobe:aue:config:service`
* Metainhoud - `content="https://adobe.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Als u alleen bepaalde extensies wilt inschakelen voor een pagina, kunt u dit instellen in een metatag. Als u extensies wilt ophalen, stelt u de eindpunten van de extensie in:

* Metanaam: `urn:adobe:aue:config:extensions`
* Meta-inhoud: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## U bent klaar om de Universal Editor te gebruiken {#youre-ready}

Uw app is nu van instrumenten voorzien om de Universal Editor te gebruiken.

Zie [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) om te leren hoe gemakkelijk en intuïtief het voor inhoudsauteurs is om inhoud tot stand te brengen gebruikend de Universele Redacteur.

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [ Universele Inleiding van de Redacteur ](introduction.md) - Leer hoe de Universele Redacteur het uitgeven om het even welk aspect van om het even welke inhoud in om het even welke implementatie toelaat zodat kunt u uitzonderlijke ervaringen leveren, inhoudssnelheid verhogen, en een ervaring van de allernieuwste ontwikkelaar verstrekken.
* [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) - Leer hoe gemakkelijk en intuïtief het voor inhoudsauteurs is om inhoud tot stand te brengen gebruikend de Universele Redacteur.
* [ het Publiceren Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/publishing.md) - leer hoe de Universele Redacteur inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen behandelen.
* [ Universele Architectuur van de Redacteur ](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [ Attributen en Types ](attributes-types.md) - leer over de gegevensattributen en de types die de Universele Redacteur vereist.
* [ Universele Authentificatie van de Redacteur ](authentication.md) - leer hoe de Universele Redacteur voor authentiek verklaart.

