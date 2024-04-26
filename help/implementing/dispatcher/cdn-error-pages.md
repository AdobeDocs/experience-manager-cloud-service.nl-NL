---
title: CDN-foutpagina's configureren
description: Leer hoe u de standaardfoutpagina kunt overschrijven door statische bestanden te hosten in zelfgehoste opslag zoals Amazon S3 of Azure Blob Storage, en ernaar te verwijzen in een configuratiebestand dat wordt geïmplementeerd met de configuratiepijplijn van Cloud Manager.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
source-git-commit: 8489b40f45e6cbeb98288969bc9f6bd42815e2a6
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# CDN-foutpagina&#39;s configureren {#cdn-error-pages}

In het onwaarschijnlijke geval dat [CDN met beheerde Adobe](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) kan niet de AEM oorsprong bereiken, CDN door gebrek dient een unbranded, generische foutenpagina die erop wijst dat de server niet kan worden bereikt. U kunt de standaardfoutenpagina met voeten treden door statische dossiers in zelf-ontvangen opslag zoals Amazon S3 of Azure Blob Storage te ontvangen, en van verwijzingen te voorzien in een configuratiedossier dat door het gebruiken van wordt opgesteld [Cloud Manager Configuration Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline).

## Instellen {#setup}

Voordat u de standaardfoutpagina kunt overschrijven, moet u het volgende doen:

* Maak eerst deze map en bestandsstructuur in de map op hoofdniveau van het Git-project:

```
config/
     cdn.yaml
```

* Ten tweede, de `cdn.yaml` Het configuratiebestand moet metagegevens en verwijzingen naar foutpagina&#39;s bevatten, zoals hieronder wordt beschreven.

### Configuratie {#configuration}

De foutpagina wordt geïmplementeerd als een toepassing van één pagina (SPA) en verwijst naar een handvol eigenschappen, zoals in het onderstaande voorbeeld wordt getoond.  De statische bestanden waarnaar wordt verwezen door de URL&#39;s, moeten door u worden gehost op een service die toegankelijk is voor internet, zoals Amazon S3 of Azure Blob Storage.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```

| Naam | Toegestane eigenschappen | Betekenis |
|-----------|--------------------------|-------------|
| **spa** | titel | Titel voor de foutpagina. |
|     | icoUrl | URL naar een pictogrambestand. |
|     | cssUrl | URL naar een CSS-bestand. |
|     | jsUrl | URL naar een JavaScript-bestand. |

### Monster van gegenereerde HTML {#sample-generated-html}

De code van HTML die door CDN wordt geproduceerd en aan de cliënt zoals browser wordt gediend zal (maar niet identiek aan) het volgende fragment lijken:

```
<!DOCTYPE html>
<html lang="en">
    <head>
        ...
        <title>the error page</title>
        <link rel="icon" href="https://www.example.com/error.ico">
        <link rel="stylesheet" href="https://www.example.com/error.css">
    </head>
    <body>
        ...
        <div id="root" status="403"></div>
        <script src="https://www.example.com/error.js"> </script>
    </body>
</html>
```

### Testen {#testing}

Voor testdoeleinden, roep het specifieke eindpunt met de gesteunde foutencode, bijvoorbeeld:

```
curl "https://publish-pXXXXX-eXXXXXX.adobeaemcloud.com/cdnstatus?code=403"
```

De volgende codes worden ondersteund: 403, 404, 406, 500 en 503.

Op deze manier activeert u rechtstreeks de fouthandler van de CDN om de synthetische reactie op een bepaalde foutcode te testen.
