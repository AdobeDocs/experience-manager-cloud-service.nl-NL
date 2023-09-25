---
title: Ontwikkeling van lokale AEM met de Universal Editor
description: Leer hoe de Universele Redacteur het uitgeven op lokale AEM instanties voor ontwikkelingsdoeleinden steunt.
source-git-commit: bf09c31baf209f5315e35f47c0d79c2b4365d3d3
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 0%

---


# Ontwikkeling van lokale AEM met de Universal Editor {#local-dev-ue}

Leer hoe de Universele Redacteur het uitgeven op lokale AEM instanties voor ontwikkelingsdoeleinden steunt.

In dit document wordt uitgelegd hoe u AEM uitvoert in HTTPS naast een lokale kopie van de Universal Editor-service, zodat u zich lokaal kunt ontwikkelen op AEM met de Universal Editor.

## AEM instellen voor uitvoering op HTTPS {#aem-https}

Binnen een buitenframe dat is beveiligd met HTTPS kan een onbeveiligd HTTP-frame niet worden geladen. De Universal Editor Service wordt uitgevoerd op HTTPS en daarom moet AEM of een andere externe pagina ook worden uitgevoerd op HTTPS.

Hiervoor moet u AEM instellen voor uitvoering op HTTPS. Voor ontwikkelingsdoeleinden kunt u zelfondertekend certificaat gebruiken.

Zie dit document voor informatie over het instellen AEM uitvoeren op HTTPS, inclusief een zelfondertekend certificaat dat u kunt gebruiken.

## De Universal Editor-service installeren {#install-ue-service}

De Universal Editor-service bindt de Universal Editor en het back-endsysteem. Omdat de officiële Universal Editor Service wereldwijd wordt gehost, moet uw lokale AEM-instantie worden blootgesteld aan internet. Om dit te voorkomen, kunt u een lokale kopie van de Universal Editor Service uitvoeren.

[NodeJS versie 16](https://nodejs.org/en/download/releases) is vereist om een lokale kopie van de Universal Editor Service uit te voeren

De Universal Editor Service wordt rechtstreeks door AEM Engineering gedistribueerd. gelieve uw ingenieurcontact in het VIP programma voor een lokaal exemplaar te bereiken.

De techniek zal u van een `universal-editor-service.cjs` bestand. Sla dit op in uw lokale ontwikkelomgeving.

## Een certificaat maken om de Universal Editor-service met HTTPS uit te voeren {#ue-https}

Voor de Universal Editor Service is ook een certificaat vereist dat op HTTPS in uw ontwikkelomgeving wordt uitgevoerd.

Voer de volgende opdracht uit.

```text
$ openssl req -newkey rsa:2048 -nodes -keyout key.pem -x509 -days 365 -out certificate.pem
```

De opdracht genereert een `key.pem` en `certificate.pem` bestand. Sla deze bestanden op in hetzelfde pad als de `universal-editor-service.cjs` bestand.

## De configuratie van de Universal Editor-service instellen {#setting-up-service}

Een aantal omgevingsvariabelen moet in NodeJS worden ingesteld om de Universal Editor Service lokaal uit te voeren.

Op hetzelfde pad als uw `universal-editor-service.cjs`, `key.pem` en `certificate.pem` bestanden, een `.env` bestand met de volgende inhoud.

```text
EXPRESS_PORT=8000
EXPRESS_PRIVATE_KEY=./key.pem
EXPRESS_CERT=./certificate.pem
NODE_TLS_REJECT_UNAUTHORIZED=0
```

De variabele heeft de volgende betekenis:

* `EXPRESS_PORT`: Definieert op welke poort de Universal Editor Service luistert
* `EXPRESS_PRIVATE`: verwijst naar uw [eerder gemaakte persoonlijke sleutel,](#ue-https) `key.pem`
* `EXPRESS_CERT`: verwijst naar uw [eerder gemaakt certificaat,](#ue-https) `certificate.pem`
* `NODE_TLS_REJECT_UNAUTHORIZED=0`: Accepteert zelfondertekende certificaten

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

```
<meta name="urn:adobe:aem:editor:endpoint" content="https://localhost:8000">
```

Zodra reeks, zou u elke vraag van de inhoudsupdate moeten zien gaan naar `https://localhost:8000` in plaats van de standaard Universal Editor-service.

>[!TIP]
>
>Raadpleeg het document voor meer informatie over hoe pagina&#39;s van instrumenten worden voorzien om de Global Universal Editor Service te gebruiken [Aan de slag met de Universal Editor in AEM](/help/implementing/universal-editor/getting-started.md#instrument-page)

## Een pagina bewerken met de lokale universele editor {#editing}

Met de [Universal Editor Service wordt lokaal uitgevoerd](#running-ue) en uw [inhoudspagina waarop instrumenten zijn aangebracht om de lokale service te gebruiken;](#using-loca-ue) u kunt nu de editor starten.

1. Browser openen voor `https://localhost:8000/`.
1. Stuur de browser om te accepteren [uw zelfondertekende certificaat.](#ue-https)
1. Zodra het zelfondertekende certificaat wordt vertrouwd, kunt u de pagina bewerken met uw lokale Universal Editor-service.
