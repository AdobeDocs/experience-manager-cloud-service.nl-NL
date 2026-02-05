---
title: Aan de slag met de Universal Editor in AEM
description: Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Developer
source-git-commit: f73316b16b0fb90e225b954ba614008d734b8918
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---


# Aan de slag met de Universal Editor in AEM {#getting-started}

Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.

>[!TIP]
>
>Als u in een voorbeeld zou verkiezen te duiken, kunt u de [ Universele SteekproefApp van de Redacteur op GitHub ](https://github.com/adobe/universal-editor-sample-editable-app) herzien.

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

De id `urn:adobe:aue:system` vertegenwoordigt de verbinding voor de universele Adobe-editor.

`data-aue-resource` s zal het `urn` voorvoegsel gebruiken om het herkenningsteken te verkorten.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Dit is de benoemde referentie die wordt vermeld in de tag `<meta>` . Bijvoorbeeld: `aemconnection`
* `<resource>` - Dit is een aanwijzer naar de bron in het doelsysteem. Bijvoorbeeld een AEM-inhoudspad, zoals `/content/page/jcr:content`

>[!TIP]
>
>Zie het document [ Attributen en Types ](attributes-types.md) voor verdere details over de gegevensattributen en de types die de Universele Redacteur vereist.

### Voorbeeldverbinding {#example}

```html
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

Als u de Universal Editor-service, die door Adobe wordt gehost, maar uw eigen gehoste versie niet wilt gebruiken, kunt u dit instellen in een metatag. Om het standaardde diensteindpunt te beschrijven dat de Universele Redacteur verstrekt, plaats uw eigen de diensteindpunt:

* Meta-naam - `urn:adobe:aue:config:service`
* Meta-inhoud - `content="https://adobe.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Als u alleen bepaalde extensies wilt inschakelen voor een pagina, kunt u dit instellen in een metatag. Als u extensies wilt ophalen, stelt u de eindpunten van de extensie in:

* Meta-naam: `urn:adobe:aue:config:extensions`
* Meta-inhoud: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## Bepaal waarvoor inhoudswegen of `sling:resourceType` s de Universele Redacteur zullen worden geopend en hoe. (Optioneel) {#content-paths}

Als u een bestaand project van AEM gebruikend [ de paginaredacteur ](/help/sites-cloud/authoring/page-editor/introduction.md) hebt, wanneer de inhoudsauteurs pagina&#39;s uitgeven, worden de pagina&#39;s automatisch geopend met de paginaredacteur. U kunt definiëren welke editor AEM moet openen op basis van de inhoudspaden of de `sling:resourceType` en hoe deze moet worden geopend. Hierdoor verloopt de bewerking naadloos voor de auteurs, ongeacht de editor die vereist is voor de geselecteerde inhoud.

1. Open de Manager van de Configuratie.

   `http://<host>:<port>/system/console/configMgr`

1. Bepaal de plaats **`Universal Editor URL Service`** in de lijst en klik **geef de configuratiewaarden** uit.

1. Bepaal waarvoor inhoudswegen of `sling:resourceType` s de Universele Redacteur zullen worden geopend.

   * Geef in het veld **`mappings`** de paden op waarvoor de universele editor is geopend.
   * Geef in het veld **`resourcetypes`** een lijst met bronnen op die rechtstreeks door de Universal Editor worden geopend.

1. Bepaal hoe de redacteur zou moeten worden geopend.

   * Schakel de optie **`aemdomain`** in om de editor te openen onder uw AEM-domein, zoals `https://author-pXX-eYYY.adobeaemcloud.com...` , anders wordt deze geopend onder `https://experience.adobe.com...` .
   * Controleer de **`editorreleasepreview`** optie om de Universele Redacteur in het [ voorproefmilieu automatisch te openen, ](/help/release-notes/universal-editor/preview.md) anders zal het in het huidige versiemilieu openen.

1. Klik **sparen**.

1. Controleer uw [ externalizer configuratie ](/help/implementing/developing/tools/externalizer.md) en zorg bij een minimum u de lokale, auteur, en publiceer milieu&#39;s hebt die zoals in het volgende voorbeeld worden geplaatst.

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

Zodra deze configuratiestappen volledig zijn, zal AEM de Universele Redacteur voor pagina&#39;s in de volgende orde openen.

1. AEM controleert de toewijzingen onder `Universal Editor Opening Mapping` en als de inhoud zich onder de aldaar gedefinieerde paden bevindt, wordt de Universal Editor geopend.
1. Voor inhoud niet onder wegen die in `Universal Editor Opening Mapping` worden bepaald, controleert AEM als `resourceType` van de inhoud die in **worden bepaald het Verdelen :resourceTypes aanpast die door Universele Redacteur** zullen worden geopend en als de inhoud één van die types aanpast, wordt de Universele Redacteur voor het bij `${author}${path}.html` geopend.
1. Anders opent AEM de Pagina-editor.

De volgende variabelen zijn beschikbaar om uw afbeeldingen op het **Universele het Openen van de Redacteur 1} gebied van de Afbeelding te bepalen.**

* `path`: Inhoudspad van de bron die moet worden geopend
* `localhost`: ExternalAlizer-item voor `localhost` zonder schema, bijvoorbeeld `localhost:4502`
* `author`: ExternalAlizer-item voor auteur zonder schema, bijvoorbeeld `localhost:4502`
* `publish`: ExternalAlizer-item voor publiceren zonder schema, bijvoorbeeld `localhost:4503`
* `preview`: ExternalAlizer-item voor voorvertoning zonder schema, bijvoorbeeld `localhost:4504`
* `env`: `prod`, `stage` `dev` op basis van de gedefinieerde uitvoeringsmodi voor Verschuiven
* `token`: Zoektoken vereist voor de `QueryTokenAuthenticationHandler`

### Voorbeeldtoewijzingen {#example-mappings}

* Open alle pagina&#39;s onder `/content/foo` op de AEM-auteur:

   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Dit leidt tot het openen van `https://localhost:4502/content/foo/x.html?login-token=<token>`

* Open alle pagina&#39;s onder `/content/bar` op een externe NextJS-server, waarbij alle variabelen als informatie worden opgegeven:

   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Dit leidt tot het openen van `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>`

## U bent klaar om de Universal Editor te gebruiken {#youre-ready}

Uw app is nu van instrumenten voorzien om de Universal Editor te gebruiken.

Zie [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) om te leren hoe gemakkelijk en intuïtief het voor inhoudsauteurs is om inhoud tot stand te brengen gebruikend de Universele Redacteur.

{{ue-headless-auth}}

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [ Universele Inleiding van de Redacteur ](introduction.md) - Leer hoe de Universele Redacteur het uitgeven om het even welk aspect van om het even welke inhoud in om het even welke implementatie toelaat zodat kunt u uitzonderlijke ervaringen leveren, inhoudssnelheid verhogen, en een ervaring van de allernieuwste ontwikkelaar verstrekken.
* [ Authoring Inhoud met de Universele Redacteur ](/help/sites-cloud/authoring/universal-editor/authoring.md) - Leer hoe gemakkelijk en intuïtief het voor inhoudsauteurs is om inhoud tot stand te brengen gebruikend de Universele Redacteur.
* [ het Publiceren Inhoud met de Universele Redacteur ](/help/implementing/universal-editor/publishing.md) - leer hoe de Universele Redacteur inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen behandelen.
* [ Universele Architectuur van de Redacteur ](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [ Attributen en Types ](attributes-types.md) - leer over de gegevensattributen en de types die de Universele Redacteur vereist.
* [ Universele Authentificatie van de Redacteur ](authentication.md) - leer hoe de Universele Redacteur voor authentiek verklaart.

