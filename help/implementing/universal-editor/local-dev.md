---
title: Ontwikkeling van lokale AEM met de Universal Editor
description: Leer hoe de Universele Redacteur het uitgeven op lokale AEM instanties voor ontwikkelingsdoeleinden steunt.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---


# Ontwikkeling van lokale AEM met de Universal Editor {#local-dev-ue}

Leer hoe de Universele Redacteur het uitgeven op lokale AEM instanties voor ontwikkelingsdoeleinden steunt.

## Overzicht {#overview}

De Universal Editor-service bindt de Universal Editor en het back-endsysteem. Als u zich lokaal voor de Universele Redacteur wilt kunnen ontwikkelen, moet u een lokaal exemplaar van de Universele Dienst van de Redacteur in werking stellen. Dit komt omdat:

* De officiële Universal Editor Service van Adobe wordt wereldwijd gehost en uw lokale AEM-instantie moet worden blootgesteld aan internet.
* Tijdens het ontwikkelen met een lokale AEM SDK is de Universal Editor Service van de Adobe niet toegankelijk via internet.
* Als uw AEM instantie IP beperkingen heeft en de Universele Dienst van de Redacteur van de Adobe niet in een bepaalde IP waaier is, kunt u het zelf ontvangen.

In dit document wordt uitgelegd hoe u AEM uitvoert in HTTPS naast een lokale kopie van de Universal Editor-service, zodat u zich lokaal kunt ontwikkelen op AEM voor gebruik met de Universal Editor.

## AEM instellen voor uitvoering op HTTPS {#aem-https}

Binnen een buitenframe dat is beveiligd met HTTPS kan een onbeveiligd HTTP-frame niet worden geladen. De Universal Editor Service wordt uitgevoerd op HTTPS en daarom moet AEM of een andere externe pagina ook worden uitgevoerd op HTTPS.

Hiervoor moet u AEM instellen voor uitvoering op HTTPS. Voor ontwikkelingsdoeleinden kunt u zelfondertekend certificaat gebruiken.

[ zie dit document ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html) op hoe te opstelling AEM lopend op HTTPS met inbegrip van een zelf-ondertekend certificaat u kunt gebruiken.

## De Universal Editor-service installeren {#install-ue-service}

De Universele Dienst van de Redacteur is geen volledig exemplaar van de Universele Redacteur, maar slechts een ondergroep van zijn eigenschappen om ervoor te zorgen dat de vraag van uw lokale AEM milieu niet over Internet wordt verpletterd, maar van een bepaald eindpunt u controleert.

[ versie 16 NodeJS ](https://nodejs.org/en/download/releases) wordt vereist om een lokaal exemplaar van de Universele Dienst van de Redacteur in werking te stellen.

De Universal Editor Service is beschikbaar via Software Distribution. Gelieve te zien de [ documentatie van de Distributie van de Software ](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html) voor details op hoe te om tot het toegang te hebben.

Sla het `universal-editor-service.cjs` -bestand op van Softwaredistributie naar uw lokale ontwikkelomgeving.

## Een certificaat maken om de Universal Editor-service met HTTPS uit te voeren {#ue-https}

Voor de Universal Editor Service is ook een certificaat vereist dat op HTTPS in uw ontwikkelomgeving wordt uitgevoerd.

Voer de volgende opdracht uit.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

De opdracht genereert een `key.pem` - en een `certificate.pem` -bestand. Sla deze bestanden op in hetzelfde pad als het `universal-editor-service.cjs` -bestand.

## De configuratie van de Universal Editor-service instellen {#setting-up-service}

Een aantal omgevingsvariabelen moet in NodeJS worden ingesteld om de Universal Editor Service lokaal uit te voeren.

Maak een `.env` -bestand met de volgende inhoud op hetzelfde pad als de `universal-editor-service.cjs` -, `key.pem` - en `certificate.pem` -bestanden.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

De variabele heeft de volgende betekenis:

* `EXPRESS_PORT`: definieert op welke poort de Universal Editor Service luistert
* `EXPRESS_PRIVATE`: Punten aan uw [ eerder-gecreeerde privé sleutel, ](#ue-https) `key.pem`
* `EXPRESS_CERT`: Punten aan uw [ eerder-gecreeerd certificaat, ](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: accepteert zelfondertekende certificaten

## De Universal Editor-service uitvoeren {#running-ue}

Voer de volgende opdracht uit om de Universal Editor Service te starten:

```text
$ node ./universal-editor-service.cjs
```

Het zou het volgende aan uw terminal moeten uitvoeren:

```text
Universal Editor Service listening on port 8000 as HTTPS Server
```

Zorg ervoor dat de service HTTPS Server start en niet HTTP Server.

## De lokale Universal Editor-service gebruiken in plaats van de algemene service {#using-local-ue}

De Universal Editor weet welke Universal Editor-service moet worden gebruikt om een pagina te bewerken op basis van de manier waarop de pagina van instrumenten is voorzien. Dit gebeurt aan de hand van metatags op de pagina die wordt geladen in de Universal Editor.

Als u een pagina wilt bewerken met uw lokale Universal Editor-service, moet u de volgende metatag instellen:

```html
<meta name="urn:adobe:aue:config:service" content="https://localhost:8000">
```

Als deze eenmaal is ingesteld, wordt elke aanroep van de inhoudsupdate weergegeven in plaats van naar `https://localhost:8000` de standaardservice van de universele editor.

>[!NOTE]
>
>Wanneer u probeert rechtstreeks toegang te krijgen tot `https://localhost:8000` , treedt er een `404` -fout op. Dit wordt verwacht.
>
>Gebruik `https://localhost:8000/corslib/LATEST` om de toegang tot uw lokale Universal Editor-service te testen. Zie de [ volgende sectie ](#editing) voor details.

>[!TIP]
>
>Voor meer details op hoe de pagina&#39;s van instrumenten worden voorzien om de Globale Universele Dienst van de Redacteur te gebruiken, zie het document [ Begonnen Worden met de Universele Redacteur in AEM ](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Een pagina bewerken met de lokale universele editor {#editing}

Met de [ Universele dienst die van de Redacteur ](#running-ue) en uw [ inhoudspagina plaatselijk in werking stelt van instrumenten om de lokale dienst te gebruiken, ](#using-loca-ue) kunt u de redacteur nu beginnen.

1. Open uw browser naar `https://localhost:8000/corslib/LATEST` .
1. Verricht uw browser om [ uw zelf-ondertekend certificaat goed te keuren.](#ue-https)
1. Zodra het zelfondertekende certificaat wordt vertrouwd, kunt u de pagina bewerken met uw lokale Universal Editor-service.

