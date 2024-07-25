---
title: CDN-foutpagina's configureren
description: Leer hoe te om de standaardfoutenpagina met voeten te treden door statische dossiers in zelf-ontvangen opslag zoals Amazon S3 of Azure Blob Storage te ontvangen, en van verwijzingen te voorzien hen in een configuratiedossier dat gebruikend de configuratiepijplijn van Cloud Manager wordt opgesteld.
feature: Dispatcher
exl-id: 1ecc374c-b8ee-41f5-a565-5b36445d3c7c
role: Admin
source-git-commit: 3a10a0b8c89581d97af1a3c69f1236382aa85db0
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# CDN-foutpagina&#39;s configureren {#cdn-error-pages}

In de onwaarschijnlijke gebeurtenis dat [ Adobe-geleide CDN ](/help/implementing/dispatcher/cdn.md#aem-managed-cdn) niet de AEM oorsprong kan bereiken, dient CDN door gebrek een unbranded, generische foutenpagina die erop wijst dat de server niet kan worden bereikt. U kunt de standaardfoutenpagina met voeten treden door statische dossiers in zelf-ontvangen opslag zoals Amazon S3 of Azure BlobOpslag te ontvangen, en hen van verwijzingen te voorzien in een configuratiedossier dat door de Cloud Manager [ config pijpleiding te gebruiken wordt opgesteld.](/help/operations/config-pipeline.md#managing-in-cloud-manager)

## Instellen {#setup}

Voordat u de standaardfoutpagina kunt overschrijven, moet u het volgende doen:

1. Maak een bestand met de naam `cdn.yaml` of een vergelijkbaar bestand en verwijs naar de onderstaande syntaxissectie.

1. Plaats het dossier ergens onder een top niveauomslag genoemd *config* of gelijkaardig, zoals die in [ wordt beschreven config pijpleidingsartikel ](/help/operations/config-pipeline.md#folder-structure).

1. Creeer een configuratiepijpleiding in Cloud Manager, zoals die in het [ wordt beschreven config pijpleidingsartikel ](/help/operations/config-pipeline.md#managing-in-cloud-manager).

1. Implementeer de configuratie.

### Syntaxis {#syntax}

De foutpagina wordt geïmplementeerd als een toepassing van één pagina (SPA) en verwijst naar een handvol eigenschappen, zoals in het onderstaande voorbeeld wordt getoond.  De statische bestanden waarnaar wordt verwezen door de URL&#39;s, moeten door u worden gehost op een service die toegankelijk is voor internet, zoals Amazon S3 of Azure Blob Storage.

Voorbeeld van configuratie:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  errorPages:
    spa:
      title: the error page
      icoUrl: https://www.example.com/error.ico
      cssUrl: https://www.example.com/error.css
      jsUrl: https://www.example.com/error.js
```
Zie het [ config pijpleidingsartikel ](/help/operations/config-pipeline.md#common-syntax) voor een beschrijving van de eigenschappen boven de gegevensknoop. De waarde van het typebezit zou *CDN* moeten zijn en het `version` bezit zou aan *1* moeten worden geplaatst.


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
