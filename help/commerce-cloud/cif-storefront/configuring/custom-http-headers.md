---
title: Aangepaste HTTP-headers
description: Leer hoe te om de kopballen van douaneHTTP te vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden.
exl-id: 2cef5d4b-45f6-4d72-a24b-67ca53d9057d
feature: Commerce Integration Framework
role: Admin
index: false
source-git-commit: 80bd8da1531e009509e29e2433a7cbc8dfe58e60
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Aangepaste HTTP-headers {#custom-http-headers}

Leer hoe te om de kopballen van douaneHTTP te vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden.

## Overzicht {#overview}

Om meer controle over hun achterkant te krijgen, kunnen de auteurs de kopballen van douaneHTTP vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden. Veelvoorkomende gebruiks-gevallen omvatten multi-store montages waarin u de kopballen van HTTP kunt gebruiken om de reactie van de handel achterste-eind te controleren.

>[!NOTE]
>
>Ontwikkelaars kunnen aangepaste HTTP-headers altijd configureren met de GraphQL-clientconfiguratie.
>

## Configuratie {#configuration}

Om de kopballen van douaneHTTP te vormen, moet men hen eerst bepalen. De kopballen van douaneHTTP moeten eerst worden bepaald door hen aan de `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` de dienstconfiguratie toe te voegen gebruikend een OSGi config.

U kunt de waarden van de kopballen van HTTP in de pagina van de Configuratie van Cloud Service voor uw project vormen:

1. Ga naar de Cloud Service-configuratiepagina in Tools > Cloud Services > CIF Configuration
1. Een bestaande configuratie openen of maken
1. Ga naar het tabblad &quot;Geavanceerd&quot; en zoek het multiveld &quot;Aangepaste HTTP-headers&quot;. U kunt de eerder gedefinieerde kopteksten selecteren en er waarden aan toewijzen.

De componenten die de bovenstaande cloudserviceconfiguratie gebruiken, verzenden deze HTTP-headers met elke GraphQL-aanvraag.

## Beperkingen {#restrictions}

Terwijl de dienst voor om het even welke kopbalnamen om toestaat worden bepaald, met inbegrip van de standaarddegenen, zullen zij niet voor het vormen beschikbaar zijn. Met andere woorden, u kunt de standaard HTTP-headers niet overschrijven met deze functie. Een lijst van beperkte kopbalnamen kan onder [&#x200B; worden gevonden mdn Webdocumenten - de kopballen van HTTP.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) Daarnaast zijn er nog twee headers die niet kunnen worden gebruikt:

* &quot;Winkel&quot; - wordt door CIF gebruikt om de Adobe Commerce-winkel te identificeren
* &quot;Voorvertoning-versie&quot; - wordt gebruikt door CIF om gefaseerde producten op te halen
