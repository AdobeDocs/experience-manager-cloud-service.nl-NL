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
>Als u liever naar een voorbeeld wilt duiken, kunt u de opdracht [Universal Editor Sample App op GitHub.](https://github.com/adobe/universal-editor-sample-editable-app)

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

Om de instrumentatie te activeren, moet de volgende invoer aan uw worden toegevoegd `index.js`.

```javascript
import "@adobe/universal-editor-cors";
```

### Alternatief voor toepassingen die niet reageren {#alternative}

Als u geen React app implementeert en/of rendering op de server vereist, kunt u het volgende opnemen in de hoofdtekst van het document.

```html
<script src="https://universal-editor-service.experiencecloud.live/corslib/LATEST" async></script>
```

De recentste versie wordt altijd geadviseerd, maar de vorige versies van de dienst kunnen in het geval van het breken van veranderingen worden van verwijzingen voorzien.

* `https://universal-editor-service.experiencecloud.live/corslib/LATEST` - De nieuwste EU CORS lib
* `https://universal-editor-service.experiencecloud.live/corslib/2/LATEST` - De nieuwste UE CORS lib onder versie 2.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1/LATEST` - De nieuwste UE CORS lib onder versie 2.1.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1.1`- De exacte UE CORS lib versie 2.1.1

## Voeg de noodzakelijke configuraties OSGi toe {#osgi-configurations}

Als u AEM inhoud wilt kunnen bewerken met uw app met de Universal Editor, moeten de instellingen voor CORS en cookie binnen AEM zijn uitgevoerd.

Het volgende [OSGi configuraties moeten op de AEM auteursinstantie worden geplaatst.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None` in `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* X-FRAME-OPTIONS verwijderen: SAMEORIGIN-koptekst in `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

Het inlogtoken cookie moet als een extern domein naar AEM worden verzonden. Daarom moet het zelfde-plaats koekje uitdrukkelijk plaatsen aan `None`.

Deze eigenschap moet worden ingesteld in het dialoogvenster `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` OSGi-configuratie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Opties: SAMEORIGIN voorkomt dat AEM pagina&#39;s binnen een iframe worden weergegeven. Als u de koptekst verwijdert, kunnen de pagina&#39;s worden geladen.

Deze eigenschap moet worden ingesteld in het dialoogvenster `org.apache.sling.engine.impl.SlingMainServlet` OSGi-configuratie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## De pagina instrumenteren {#instrument-page}

Voor de Universal Editor-service is een [Naam van uniforme bron (URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name) om het juiste back-endsysteem te identificeren en te gebruiken voor de inhoud in de app die wordt bewerkt. Daarom wordt een schema URN vereist om inhoud terug naar inhoudsmiddelen in kaart te brengen.

### Verbindingen maken {#connections}

Verbindingen die in de app worden gebruikt, worden opgeslagen als `<meta>` -tags in de pagina&#39;s `<head>`.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` - Dit is een classificatie van het verband met twee opties.
   * `system` - Voor eindpunten van verbindingen
   * `config` - Voor [optionele configuratie-instellingen definiëren](#configuration-settings)
* `<referenceName>` - Dit is een korte naam die opnieuw wordt gebruikt in het document om de verbinding te identificeren. Bijv. `aemconnection`
* `<protocol>` - Hiermee wordt aangegeven welke persistentie-insteekmodule van de Universal Editor Persistence Service moet worden gebruikt. Bijv. `aem`
* `<url>` - Dit is de URL naar het systeem waar de wijzigingen zullen worden voortgezet. Bijv. `http://localhost:4502`

De id `urn:adobe:aue:system` vertegenwoordigt de verbinding voor de Adobe Universele Redacteur.

`data-aue-resource`s gebruikt de `urn` om de id te verkorten.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Dit is de benoemde referentie die wordt vermeld in het dialoogvenster `<meta>` -tag. Bijv. `aemconnection`
* `<resource>` - Dit is een aanwijzer naar de bron in het doelsysteem. Bijvoorbeeld een AEM inhoudspad, zoals `/content/page/jcr:content`

>[!TIP]
>
>Zie het document [Kenmerken en typen](attributes-types.md) voor meer informatie over de gegevenskenmerken en -typen die de Universal Editor nodig heeft.

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

U kunt de `config` in uw verbinding-URL om service- en extensieeindpunten indien nodig in te stellen.

Als u de Universal Editor-service niet wilt gebruiken, die wordt gehost op Adobe, maar uw eigen gehoste versie, kunt u dit instellen in een metatag. Om het standaardde diensteindpunt te beschrijven dat de Universele Redacteur verstrekt, plaats uw eigen de diensteindpunt:

* Metanaam - `urn:adobe:aue:config:service`
* Metainhoud - `content="https://adobe.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Als u alleen bepaalde extensies wilt inschakelen voor een pagina, kunt u dit instellen in een metatag. Als u extensies wilt ophalen, stelt u de eindpunten van de extensie in:

* Naam van meta: `urn:adobe:aue:config:extensions`
* Metainhoud: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (voorbeeld)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## U bent klaar om de Universal Editor te gebruiken {#youre-ready}

Uw app is nu van instrumenten voorzien om de Universal Editor te gebruiken.

Zie [Inhoud ontwerpen met de Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) om te leren hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken, zodat u uitzonderlijke ervaringen kunt opdoen, de snelheid van de inhoud kunt verhogen en een geavanceerde ontwikkelaarservaring kunt bieden.
* [Inhoud ontwerpen met de Universal Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Inhoud publiceren met de Universal Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) - Leer hoe de Universal Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.

