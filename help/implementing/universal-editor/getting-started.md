---
title: Aan de slag met de Universal Editor in AEM
description: Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
source-git-commit: a933073346e6b7c3b4256269f5796a64a6dfbfa8
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 0%

---

# Aan de slag met de Universal Editor in AEM {#getting-started}

Leer hoe u toegang krijgt tot de Universal Editor en hoe u uw eerste AEM-app van instrumenten kunt voorzien om deze te gebruiken.

>[!TIP]
>
>Als u liever naar een voorbeeld wilt duiken, kunt u de opdracht [Universal Editor Sample App op GitHub.](https://github.com/adobe/universal-editor-sample-editable-app)

## Stappen aan boord {#onboarding}

Hoewel de Universal Editor inhoud uit elke bron kan bewerken, wordt in dit document een AEM-app als voorbeeld gebruikt.

Er zijn een aantal stappen om uw AEM-app in te schrijven en van instrumenten te voorzien voor gebruik van de Universal Editor.

1. [Toegang aanvragen tot de Universal Editor.](#request-access)
1. [Neem de kernbibliotheek van de Universal Editor op.](#core-library)
1. [Voeg de noodzakelijke configuratie OSGi toe.](#osgi-configurations)
1. [Instrueer de pagina.](#instrument-page)

Dit document begeleidt u door deze stappen.

## Toegang tot de universele editor aanvragen {#request-access}

U moet eerst om toegang tot de Universele Redacteur verzoeken. Ga naar [https://experience.adobe.com/#/aem/editor,](https://experience.adobe.com/#/aem/editor) aanmelden en valideren als u toegang hebt tot de Universal Editor.

Als u geen toegang hebt, kunt u een aanvraag indienen via een formulier dat is gekoppeld op dezelfde pagina.

![Toegang aanvragen tot de Universal Editor](assets/request-access.png)

Klikken **Toegang aanvragen** en vul het formulier in volgens de instructies voor het aanvragen van toegang. Een Adobe-vertegenwoordiger zal uw verzoek beoordelen en contact opnemen om uw kwestie van het gebruik te bespreken.

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

Als u geen React app implementeert en/of rendering op de server vereist, kunt u ook het volgende opnemen in de hoofdtekst van het document.

```html
<script src="https://cdn.jsdelivr.net/gh/adobe/universal-editor-cors/dist/universal-editor-embedded.js" async></script>
```

## Voeg de noodzakelijke configuraties OSGi toe {#osgi-configurations}

Als u AEM inhoud met uw app wilt bewerken met de Universal Editor, moeten de instellingen voor CORS en cookie binnen AEM zijn uitgevoerd.

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

X-frame-opties: SAMEORIGIN voorkomt dat AEM pagina&#39;s binnen een iframe worden weergegeven. Als u de koptekst verwijdert, kunnen de pagina&#39;s worden geladen.

Deze eigenschap moet worden ingesteld in het dialoogvenster `org.apache.sling.engine.impl.SlingMainServlet` OSGi-configuratie.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## De pagina instrumenteren {#instrument-page}

De Universal Editor-service vereist een [Naam van uniforme bron (URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name) om het juiste back-endsysteem te identificeren en te gebruiken voor de inhoud in de app die wordt bewerkt. Daarom wordt een schema URN vereist om inhoud terug naar inhoudsmiddelen in kaart te brengen.

De instrumentatiekenmerken die aan de pagina worden toegevoegd, bestaan voornamelijk uit: [HTML Microdata](https://developer.mozilla.org/en-US/docs/Web/HTML/Microdata) een industriestandaard die ook kan worden gebruikt om HTML semantischer te maken, HTML-documenten indexeerbaar te maken, enz.

### Verbindingen maken {#connections}

Verbindingen die in de app worden gebruikt, worden opgeslagen als `<meta>` -tags in de pagina&#39;s `<head>`.

```html
<meta name="urn:adobe:aem:editor:<referenceName>" content="<protocol>:<url>">
```

* `<referenceName>` - Dit is een korte naam die opnieuw wordt gebruikt in het document om de verbinding te identificeren. Bijv. `aemconnection`
* `<protocol>` - Hiermee wordt aangegeven welke persistentie-insteekmodule van de Universal Editor Persistence Service moet worden gebruikt. Bijv. `aem`
* `<url>` - Dit is de URL naar het systeem waar de wijzigingen zullen worden voortgezet. Bijv. `http://localhost:4502`

De korte id `auecon` staat voor Adobe Universal Editor Connection.

`itemid`s gebruikt de `urn` om de id te verkorten.

```html
itemid="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Dit is de benoemde referentie die wordt vermeld in het dialoogvenster `<meta>` tag. Bijv. `aemconnection`
* `<resource>` - Dit is een aanwijzer naar de bron in het doelsysteem. Bijvoorbeeld een AEM inhoudspad, zoals `/content/page/jcr:content`

>[!TIP]
>
>Zie het document [Kenmerken en typen](attributes-types.md) voor meer informatie over de gegevenskenmerken en -typen die de Universal Editor nodig heeft.

### Voorbeeldverbinding {#example}

```html
<html>
<head>
    <meta name="urn:auecon:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:auecon:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul itemscope itemid="urn:aemconnection:/content/example/list" itemtype="container">
            <li itemscope itemid="urn:aemconnection/content/example/listitem" itemtype="component">
              <p itemprop="name" itemtype="text">Jane Doe</p>
              <p itemprop="title" itemtype="text">Journalist</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
 
...
 
            <li itemscope itemid="urn:fcsconnection:/documents/mytext" itemtype="component">
              <p itemprop="name" itemtype="text">John Smith</p>
              <p itemid="urn:aemconnection/content/example/another-source" itemprop="title" itemtype="text">Photographer</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

## U bent klaar om de Universele Redacteur te gebruiken {#youre-ready}

Uw app is nu van instrumenten voorzien om de Universal Editor te gebruiken.

Raadpleeg het document [Inhoud ontwerpen met de Universal Editor](authoring.md) om te leren hoe gemakkelijk en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.

## Aanvullende bronnen {#additional-resources}

Zie deze documenten voor meer informatie over de Universal Editor.

* [Introductie van Universal Editor](introduction.md) - Leer hoe u met de Universal Editor elk aspect van elke inhoud in een implementatie kunt bewerken om buitengewone ervaringen te bieden, de snelheid van de inhoud te verhogen en een geavanceerde ontwikkelaarservaring te bieden.
* [Inhoud ontwerpen met de Universal Editor](authoring.md) - Leer hoe eenvoudig en intuïtief het is voor inhoudsauteurs om inhoud te maken met de Universal Editor.
* [Inhoud publiceren met de Universal Editor](publishing.md) - Leer hoe de Universal Visual Editor inhoud publiceert en hoe uw apps de gepubliceerde inhoud kunnen verwerken.
* [Architectuur van Universal Editor](architecture.md) - Leer over de architectuur van de Universele Redacteur en hoe de gegevens tussen zijn diensten en lagen stromen.
* [Kenmerken en typen](attributes-types.md) - Meer informatie over de gegevenskenmerken en typen die de Universal Editor nodig heeft.
* [Universal Editor-verificatie](authentication.md) - Leer hoe de Universal Editor wordt geverifieerd.
