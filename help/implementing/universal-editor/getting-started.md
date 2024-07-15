---
title: Aan de slag met de Universal Editor in AEM
description: Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 395cb7b2e37c7358baa7ae07329f42bd5a560cb1
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---


# Aan de slag met de Universal Editor in AEM {#getting-started}

Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.

>[!TIP]
>
>Als u in een voorbeeld liever zou duiken, kunt u de [ Universele SteekproefApp van de Redacteur op GitHub herzien.](https://github.com/adobe/universal-editor-sample-editable-app)

## Stappen aan boord {#onboarding}

Hoewel de Universal Editor inhoud uit elke bron kan bewerken, wordt in dit document een AEM-app als voorbeeld gebruikt.

Er zijn verschillende stappen om uw AEM-app aan te melden en van instrumenten te voorzien voor gebruik van de Universal Editor.

1. [Neem de kernbibliotheek van de Universal Editor op.](#core-library)
1. [Voeg de noodzakelijke configuratie OSGi toe.](#osgi-configurations)
1. [Instrueer de pagina.](#instrument-page)

Dit document begeleidt u door deze stappen.

## Inclusief de Universal Editor Core-bibliotheek {#core-library}

Voordat uw app van instrumenten kan worden voorzien voor gebruik met de Universal Editor, moet deze de volgende afhankelijkheid bevatten.

```javascript
@adobe/universal-editor-cors
```

Om de instrumentatie te activeren, moet de volgende import worden toegevoegd aan de `index.js` .

```javascript
import "@adobe/universal-editor-cors";
```

### Alternatief voor toepassingen die niet reageren {#alternative}

Als u geen React app implementeert en/of rendering op de server vereist, kunt u het volgende opnemen in de hoofdtekst van het document.

```html
<script src="https://universal-editor-service.experiencecloud.live/corslib/LATEST" async></script>
```

De recentste versie wordt altijd geadviseerd, maar de vorige versies van de dienst kunnen in het geval van het breken van veranderingen worden van verwijzingen voorzien.

* `https://universal-editor-service.experiencecloud.live/corslib/LATEST` - De nieuwste UE CORS lib
* `https://universal-editor-service.experiencecloud.live/corslib/2/LATEST` - De nieuwste UE CORS lib onder versie 2.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1/LATEST` - De nieuwste UE CORS lib onder versie 2.1.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1.1` - De exacte UE CORS lib versie 2.1.1

## Voeg de noodzakelijke configuraties OSGi toe {#osgi-configurations}

Als u AEM inhoud wilt kunnen bewerken met uw app met de Universal Editor, moeten de instellingen voor CORS en cookie binnen AEM zijn uitgevoerd.

De volgende [ configuraties OSGi moeten op de AEM auteursinstantie worden geplaatst.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None` in `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* X-FRAME-OPTIONS verwijderen: SAMEORIGIN-koptekst in `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

Het inlogtoken cookie moet als een extern domein naar AEM worden verzonden. Daarom moet het cookie van dezelfde site expliciet worden ingesteld op `None` .

Deze eigenschap moet worden ingesteld in de `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` OSGi-configuratie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Opties: SAMEORIGIN voorkomt dat AEM pagina&#39;s binnen een iframe worden weergegeven. Als u de koptekst verwijdert, kunnen de pagina&#39;s worden geladen.

Deze eigenschap moet worden ingesteld in de `org.apache.sling.engine.impl.SlingMainServlet` OSGi-configuratie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## De pagina instrumenteren {#instrument-page}

De Universele dienst van de Redacteur vereist a [ eenvormige middelnaam (URN) ](https://en.wikipedia.org/wiki/Uniform_Resource_Name) om het correcte backendesysteem voor de inhoud in app te identificeren en te gebruiken die wordt uitgegeven. Daarom wordt een schema URN vereist om inhoud terug naar inhoudsmiddelen in kaart te brengen.

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

