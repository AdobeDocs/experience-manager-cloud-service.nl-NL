---
title: Uw eigen Universal Editor-service uitvoeren
description: Leer hoe u uw eigen Universal Editor-service kunt uitvoeren voor lokale ontwikkeling of als onderdeel van uw eigen infrastructuur.
exl-id: ba1bf015-7768-4129-8372-adfb86e5a120
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 0%

---


# Uw eigen Universal Editor-service uitvoeren {#local-ue-service}

Leer hoe u uw eigen Universal Editor-service kunt uitvoeren voor lokale ontwikkeling of als onderdeel van uw eigen infrastructuur.

## Overzicht {#overview}

De Universal Editor-service bindt de Universal Editor en het back-endsysteem. Als u zich lokaal voor de Universele Redacteur wilt kunnen ontwikkelen, moet u een lokaal exemplaar van de Universele Dienst van de Redacteur in werking stellen. Dit komt omdat:

* De officiële Universal Editor Service van Adobe wordt wereldwijd gehost en uw lokale AEM-instantie moet worden blootgesteld aan internet.
* Tijdens de ontwikkeling met een lokale AEM SDK, heeft de Universal Editor Service van Adobe geen toegang tot internet.
* Als uw AEM instantie IP beperkingen heeft en de Universele Dienst van de Redacteur van de Adobe niet in een bepaalde IP waaier is, kunt u het zelf ontvangen.

## Gevallen gebruiken {#use-cases}

Uw eigen exemplaar van de Universal Editor-service is handig als u het volgende wilt doen:

* Lokaal ontwikkelen op AEM voor gebruik met de Universele Redacteur.
* Voer uw eigen Universal Editor Service uit als onderdeel van uw eigen infrastructuur, onafhankelijk van de Universal Editor Service van Adobe.

Beide gebruiksgevallen worden ondersteund. In dit document wordt uitgelegd hoe u AEM uitvoert in HTTPS naast een lokale kopie van de Universal Editor-service.

Als u uw eigen Universal Editor-service wilt uitvoeren als onderdeel van uw eigen infrastructuur, voert u dezelfde stappen uit als in het lokale ontwikkelingsvoorbeeld.

## AEM instellen voor uitvoering op HTTPS {#aem-https}

Binnen een buitenframe dat is beveiligd met HTTPS, kan een onbeveiligd HTTP-frame niet worden geladen. De Universal Editor Service wordt uitgevoerd op HTTPS en daarom moet AEM of een andere externe pagina ook worden uitgevoerd op HTTPS.

Hiervoor moet u AEM instellen voor uitvoering op HTTPS. Voor ontwikkelingsdoeleinden kunt u zelfondertekend certificaat gebruiken.

[ zie dit document ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html) op hoe te opstelling AEM lopend op HTTPS met inbegrip van een zelf-ondertekend certificaat u kunt gebruiken.

## De Universal Editor-service installeren {#install-ue-service}

De Universele Dienst van de Redacteur is geen volledig exemplaar van de Universele Redacteur, maar slechts een ondergroep van zijn eigenschappen om ervoor te zorgen dat de vraag van uw lokale AEM milieu niet over Internet wordt verpletterd, maar van een bepaald eindpunt u controleert.

[ versie NodeJS 20 ](https://nodejs.org/en/download/releases) wordt vereist om een lokaal exemplaar van de Universele Dienst van de Redacteur in werking te stellen.

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
UES_PORT=8000
UES_PRIVATE_KEY=./key.pem
UES_CERT=./certificate.pem
UES_TLS_REJECT_UNAUTHORIZED=false
UES_CORS_PRIVATE_NETWORK=true
```

Dit zijn de minimumwaarden die vereist zijn voor lokale ontwikkeling in ons voorbeeld.

>[!NOTE]
>
>Als u versie 130+ van Chrome in werking stelt, moet u het verzenden van de kopballen van CORS voor [ privé netwerktoegang ](https://wicg.github.io/private-network-access/#private-network-request) toelaten gebruikend de `UES_CORS_PRIVATE_NETWORK` optie.


In de volgende tabel worden deze en aanvullende waarden beschreven.

| Waarde | Optioneel | Standaard | Beschrijving |
|---|---|---|---|
| `UES_PORT` | Ja | `8080` | Poort waarop de server wordt uitgevoerd |
| `UES_PRIVATE_KEY` | Ja | Geen | Pad naar de persoonlijke sleutel voor de HTTPS-server |
| `UES_CERT` | Ja | Geen | Pad naar het certificeringsbestand voor de HTTPS-server |
| `UES_TLS_REJECT_UNAUTHORIZED` | Ja | `true` | Niet-geautoriseerde TLS-verbindingen negeren |
| `UES_DISABLE_IMS_VALIDATION` | Ja | `false` | IMS-validatie uitschakelen |
| `UES_ENDPOINT_MAPPING` | Ja | Leeg | Toewijzing van de eindpunten voor intern herschrijft <br> Voorbeeld: `UES_ENDPOINT_MAPPING='[{"https://your-public-facing-author-domain.net": "http://10.0.0.1:4502"}]'`<br> Resultaat: De Universele Dienst van de Redacteur zal met `http://10.0.0.1:4502` in plaats van de verstrekte verbinding `https://your-public-facing-author-domain.net` verbinden |
| `UES_LOG_LEVEL` | Ja | `info` | Logniveau voor de server, mogelijke waarden zijn `silly`, `trace`, `debug`, `verbose`, `info`, `log`, `warn`, `error` en `fatal` |
| `UES_SPLUNK_HEC_URL` | Ja | Geen | HEC URL aan Splunk eindpunt |
| `UES_SPLUNK_TOKEN` | Ja | Geen | Splunk-token |
| `UES_SPLUNK_INDEX` | Ja | Geen | Index die moet worden gebruikt voor het schrijven van logbestanden naar |
| `UES_SPLUNK_SOURCE` | Ja | `universal-editor-service` | Naam van de bron in de splunklogboeken |
| `UES_CORS_PRIVATE_NETWORK` | Ja | `false` | Laat het verzenden van kopballen CORS toe om [ Privé netwerk ](https://wicg.github.io/private-network-access/#private-network-request) toe te staan. Vereist voor gebruikers van Chrome versie 130+ |

>[!NOTE]
>
>Voorafgaand aan de [ versie 2024.08.13 ](/help/release-notes/universal-editor/current.md) van de Universele Redacteur, werden de volgende variabelen vereist in het `.env` dossier. Deze waarden worden tot 1 oktober 2024 ondersteund voor achterwaartse compatibiliteit.
>
>`EXPRESS_PORT=8000`
>`EXPRESS_PRIVATE_KEY=./key.pem`
>`EXPRESS_CERT=./certificate.pem`
>`NODE_TLS_REJECT_UNAUTHORIZED=0`

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

Met de [ Universele dienst die van de Redacteur ](#running-ue) en uw [ inhoudspagina plaatselijk in werking stelt van instrumenten om de lokale dienst ](#using-loca-ue) te gebruiken, kunt u de redacteur nu beginnen.

1. Open uw browser naar `https://localhost:8000/ping` .
1. Verricht uw browser om [ uw zelf-ondertekend certificaat ](#ue-https) goed te keuren.
1. Zodra het zelfondertekende certificaat wordt vertrouwd, kunt u de pagina bewerken met uw lokale Universal Editor-service.

