---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 10%

---

# CDN in AEM as a Cloud Service {#cdn}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties."

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

AEM-geleide CDN voldoet aan de prestaties en de veiligheidsvereisten van de meeste klant. Voor de publicatielaag kunnen klanten optioneel naar de laag verwijzen vanuit hun eigen CDN, die ze moeten beheren. Dit scenario wordt toegestaan op een geval-voor-geval basis, gebaseerd op het voldoen van bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun leverancier CDN heeft die moeilijk is te verlaten.

<!-- ERROR: NEITHER URL IS FOUND (HTTP ERROR 404) Also, see the following videos [Cloud 5 AEM CDN Part 1](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part1.html) and [Cloud 5 AEM CDN Part 2](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-5/cloud5-aem-cdn-part2.html) for additional information about CDN in AEM as a Cloud Service. -->

## CDN met AEM beheer  {#aem-managed-cdn}

Volg de onderstaande secties om de zelfbedieningsinterface van Cloud Manager te gebruiken voor het voorbereiden van de levering van inhoud met behulp van AEM kant-en-klare CDN:

1. [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beperking van het verkeer**

Door gebrek, voor een AEM-beheerde opstelling CDN, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. U kunt verkeer tot de publicatieservice voor een bepaalde milieu beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) door als gebruikersinterface van de Manager van de Wolk.

Zie [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) voor meer informatie.

>[!CAUTION]
>
>Slechts worden de verzoeken van toegestane IPs gediend door AEM beheerde CDN. Als u uw eigen CDN aan AEM-beheerde CDN richt, dan zorg ervoor IPs van uw CDN in de lijst van gewenste personen inbegrepen is.

## CDN van de klant wijst aan AEM-Beheerde CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="CDN van de klant wijst naar AEM Beheerde CDN"
>abstract="AEM als Cloud Service biedt klanten een optie om zijn bestaande CDN te gebruiken. Voor de publicatielaag kunnen klanten optioneel naar de laag verwijzen vanuit hun eigen CDN, die ze moeten beheren. Dit scenario wordt toegestaan op een geval-voor-geval basis, gebaseerd op het voldoen van bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun leverancier CDN heeft die moeilijk is te verlaten."

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het leiden en het richten aan AEM-beheerde CDN, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM as a Cloud Service te werken - zie de hieronder vermelde configuratieinstructies.
* De klant moet ingenieurs CDN hebben die op vraag in geval-gerelateerde kwesties zijn.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Wijs uw CDN aan de ingang van Adobe CDN als zijn oorsprongdomein. Bijvoorbeeld, `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Stel SNI in op de invoer van de Adobe CDN.
1. Stel de Hostkop in op het oorspronkelijke domein. Bijvoorbeeld: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Stel de `X-Forwarded-Host` header met de domeinnaam zodat AEM de hostheader kan bepalen. Bijvoorbeeld: `X-Forwarded-Host:example.com`.
1. Set `X-AEM-Edge-Key`. De waarde moet van Adobe komen.

   * Nodig zodat Adobe CDN de bron van de verzoeken kan bevestigen en overgaan `X-Forwarded-*` kopteksten naar de AEM toepassing. Bijvoorbeeld:`X-Forwarded-For` wordt gebruikt om cliëntIP te bepalen. Zo, wordt het de verantwoordelijkheid van de vertrouwde op bezoeker (namelijk klant-beheerde CDN) om de juistheid van te verzekeren `X-Forwarded-*` kopteksten (zie onderstaande opmerking).
   * De toegang tot de ingangen van Adobe CDN kan optioneel worden geblokkeerd wanneer een `X-AEM-Edge-Key` is niet aanwezig. Informeer Adobe als u directe toegang tot de ingangen van Adobe CDN nodig hebt (te blokkeren).

Zie de [Voorbeeld van CDN-leveranciersconfiguraties](#sample-configurations) sectie voor configuratievoorbeelden van belangrijke verkopers CDN.

Alvorens levend verkeer goed te keuren, zou u met Adobe klantensteun moeten bevestigen dat het eind-aan-eind verkeer dat correct verplettert functioneert.

Nadat u de `X-AEM-Edge-Key`, kunt u testen dat het verzoek correct als volgt wordt verpletterd.

In Linux®:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H "X-Forwarded-Host: example.com" -H "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

In Windows:

```
curl https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com --header "X-Forwarded-Host: example.com" --header "X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>"
```

>[!NOTE]
>
>Wanneer u uw eigen CDN gebruikt, hoeft u geen domeinen en certificaten te installeren in Cloud Manager. Het verpletteren in Adobe CDN wordt gedaan door het standaarddomein te gebruiken `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com` die in het verzoek moeten worden ingediend `Host` header. Het verzoek overschrijven `Host` header met een aangepaste domeinnaam kan ertoe leiden dat de aanvraag onjuist wordt gerouteerd door de Adobe CDN.


>[!NOTE]
>
>De klanten die hun eigen CDN beheren zouden de integriteit van de kopballen moeten verzekeren die door naar AEM CDN worden verzonden. Het wordt bijvoorbeeld aanbevolen dat klanten alles wissen `X-Forwarded-*` kopballen en plaatsen hen aan bekende en gecontroleerde waarden. Bijvoorbeeld: `X-Forwarded-For` zou het IP van de cliënt adres moeten bevatten, terwijl `X-Forwarded-Host` moet de host van de site bevatten.

>[!NOTE]
>
>Sandbox programmamilieu&#39;s steunen geen klant-Geleverde CDN.

De extra hop tussen klant CDN en AEM CDN is slechts nodig als er een geheim voorgeheugenmisser is. Door de strategieën van de geheim voorgeheugenoptimalisering te gebruiken die in dit artikel worden beschreven, zou de toevoeging van een klant CDN slechts verwaarloosbare latentie moeten introduceren.

Deze CDN-configuratie van de klant wordt ondersteund voor de publicatielaag, maar niet vóór de auteurslaag.

### Voorbeeld van CDN-leveranciersconfiguraties {#sample-configurations}

Hieronder worden verschillende configuratievoorbeelden van verschillende toonaangevende CDN-leveranciers weergegeven.

**Akamai**

![Akamai1](assets/akamai1.png "Akamai")
![Akamai2](assets/akamai2.png "Akamai")

**Amazon CloudFront**

![CloudFront1](assets/cloudfront1.png "Amazon CloudFront")
![CloudFront2](assets/cloudfront2.png "Amazon CloudFront")

**Cloudflare**

![Cloudflare1](assets/cloudflare1.png "Cloudflare")
![Cloudflare2](assets/cloudflare2.png "Cloudflare")

## Geolocatie-headers {#geo-headers}

De AEM-beheerde CDN voegt kopballen aan elk verzoek met toe:

* landcode: `x-aem-client-country`
* continentale code: `x-aem-client-continent`

>[!NOTE]
>
>Als er een klant-geleide CDN is, wijzen deze kopballen op de plaats van de klantenCDN volmachtsserver eerder dan de daadwerkelijke cliënt. Daarom voor klant-beheerde CDN, zouden de geolocatiekopballen door klanten CDN moeten worden beheerd.

De waarden voor de landcodes zijn de beschreven alpha-2-codes [hier](https://en.wikipedia.org/wiki/ISO_3166-1).

De waarden voor de continentale codes zijn:

* AF Afrika
* AN Antarctica
* AS Azië
* EU-Europa
* NA Noord-Amerika
* OC Oceanië
* SA Zuid-Amerika

Deze informatie kan nuttig zijn in gevallen zoals omleiding naar een andere URL op basis van de oorsprong (land) van het verzoek. Gebruik de header Variëren voor het in cache plaatsen van reacties die afhankelijk zijn van geo-informatie. Omleiding naar een specifieke landingspagina moet bijvoorbeeld altijd het volgende bevatten: `Vary: x-aem-client-country`. Indien nodig kunt u `Cache-Control: private` om caching te voorkomen. Zie ook [Caching](/help/implementing/dispatcher/caching.md#html-text).
