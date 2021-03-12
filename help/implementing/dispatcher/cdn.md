---
title: CDN in AEM as a Cloud Service
description: CDN in AEM als Cloud Service
translation-type: tm+mt
source-git-commit: c71117de502b1ee756e06e756a643c987113ea45
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 7%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

De AEM beheerde CDN zal aan de prestaties en de veiligheidsvereisten van de meeste klant voldoen. Voor publiceer rij, kunnen de klanten naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten.

## Beheerde CDN AEM {#aem-managed-cdn}

Volg de onderstaande secties om de zelfbediening UI van de Manager van de Wolk te gebruiken om voor de levering van inhoud voor te bereiden door AEM uit-van-de-doos CDN te gebruiken:

1. [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beperking van het verkeer**

Door gebrek, voor een AEM beheerde opstelling CDN, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. Als u verkeer aan de publicatieservice voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) kunt u dit op een zelfbedienings manier via de UI van de Manager van de Wolk doen.

Raadpleeg [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) voor meer informatie.

>[!CAUTION]
>
>Slechts zullen de verzoeken van toegestane IPs door beheerde CDN van AEM worden gediend. Als u uw eigen CDN aan AEM beheerde CDN richt, dan zorg ervoor IPs van uw CDN in de lijst van gewenste personen inbegrepen is.

## Klant CDN verwijst naar AEM beheerde CDN {#point-to-point-CDN}

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het beheren en het richten aan AEM beheerde CDN, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM als Cloud Service te werken - zie de configuratieinstructies hieronder.
* De klant moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host`-header in met de domeinnaam.
1. Plaats de kopbal van de Gastheer met het oorsprongdomein, dat de ingang van AEM CDN is. De waarde moet van Adobe komen.
1. Verzend de kopbal SNI naar de oorsprong. Zoals de kopbal van de Gastheer, moet de kopbal SNI het oorsprongdomein zijn.
1. Stel de `X-Edge-Key` of `X-AEM-Edge-Key` in (als uw CDN X-Edge-*) bijsnijdt, wat nodig is om het verkeer naar de AEM servers correct te leiden. De waarde moet van Adobe komen. Gelieve te informeren Adobe als u directe toegang tot de ingang van Adobe CDN (moet worden geblokkeerd wanneer `X-Edge-Key` niet aanwezig is) wilt.

Alvorens levend verkeer goed te keuren, zou u met Adobe klantensteun moeten bevestigen dat het eind-aan-eind verkeer dat correct verplettert functioneert.

>[!NOTE]
>
>De klanten die hun eigen CDN beheren zouden de integriteit van de kopballen moeten verzekeren die door naar AEM CDN worden verzonden. Het wordt bijvoorbeeld aanbevolen dat klanten alle `X-Forwarded-*` headers wissen en deze op bekende en gecontroleerde waarden instellen. `X-Forwarded-For` moet bijvoorbeeld het IP-adres van de client bevatten, terwijl `X-Forwarded-Host` de host van de site moet bevatten.

Er is potentieel een kleine prestatieshit toe te schrijven aan de extra hop, hoewel de hop van klant CDN aan AEM beheerde CDN waarschijnlijk efficiënt zal zijn.

Houd er rekening mee dat deze CDN-configuratie van de klant wordt ondersteund voor de publicatielijst, maar niet vóór de auteurslaag.

## Geolocatiekoppen {#geo-headers}

De AEM beheerde CDN voegt kopballen aan elk verzoek met toe:

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

Deze informatie kan nuttig zijn in gevallen zoals omleiding naar een andere URL op basis van de oorsprong (land) van het verzoek. Gebruik de header Variëren voor het in cache plaatsen van reacties die afhankelijk zijn van geo-informatie. Omleiding naar een specifieke landingspagina moet bijvoorbeeld altijd `Vary: x-aem-client-country` bevatten. Indien nodig, kunt u `Cache-Control: private` gebruiken om caching te verhinderen. Zie ook [Caching](/help/implementing/dispatcher/caching.md#html-text).
