---
title: CDN in AEM as a Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: b6ae5cab872a3cca4eb41259f6c242b1fbeb98bb
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 5%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

De AEM beheerde CDN zal aan de prestaties en de veiligheidsvereisten van de meeste klant voldoen. Voor publiceer rij, kunnen de klanten naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten.

## Beheerde CDN AEM {#aem-managed-cdn}

Volg de onderstaande secties om de zelfbediening UI van de Manager van de Wolk te gebruiken om op inhoudslevering voor te bereiden door uit-van-de-doos CDN van Adobe te gebruiken:

1. [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beperking van het verkeer**

Door gebrek, voor een Adobe Beheerde CDN opstelling, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. Als u verkeer aan de publicatieservice voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) kunt u dit op een zelfbedienings manier via de UI van de Manager van de Wolk doen.

Raadpleeg [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) voor meer informatie.

>[!CAUTION]
>
>Slechts zullen de verzoeken van toegestane IPs door beheerde CDN van AEM worden gediend. Als u uw eigen CDN aan AEM beheerde CDN richt dan zorg ervoor IPs van uw CDN in de lijst van gewenste personen inbegrepen is.

## Klant CDN verwijst naar AEM beheerde CDN {#point-to-point-CDN}

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het beheren en het richten aan Adobe beheerde CDN, op voorwaarde dat wordt voldaan aan het volgende:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM als Cloud Service te werken - zie de configuratieinstructies hieronder.
* De klant moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host`-header in met de domeinnaam.
1. Plaats de kopbal van de Gastheer domein, dat de ingang van Adobe CDN is. De waarde moet van Adobe komen.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Stel de `X-Edge-Key` in, die nodig is om het verkeer correct naar de AEM servers te leiden. De waarde moet van Adobe komen.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer dat van begin tot eind correct functioneert.

Er is een kleine prestatiesklap toe te schrijven aan de extra hop, hoewel de hop klant CDN aan een beheerde Adobe CDN waarschijnlijk efficiënt zal zijn.

Merk op dat deze klantCDN configuratie voor publiceert rij, maar niet vóór de auteursrij wordt gesteund.

## Geolocatiekoppen {#geo-headers}

De Adobe beheerde CDN zal kopballen aan elk verzoek met toevoegen:

* landcode: `x-aem-client-country`
* continentale code: `x-aem-client-continent`

De waarden voor de landcodes zijn de Alpha-2-codes die [hier](https://en.wikipedia.org/wiki/ISO_3166-1) worden beschreven.

De waarden voor de continentale codes zijn:

* AF Afrika
* AN Antarctica
* AS Azië
* EU-Europa
* NA Noord-Amerika
* OC Oceanië
* SA Zuid-Amerika

Deze informatie kan nuttig zijn in gevallen zoals omleiding naar een andere URL op basis van de oorsprong (land) van het verzoek. In dit specifieke geval mag de omleiding echter niet in de cache worden opgeslagen, aangezien deze varieert. Indien nodig, kunt u `Cache-Control: private` gebruiken om caching te verhinderen. Zie ook [Caching](/help/implementing/dispatcher/caching.md#html-text).
