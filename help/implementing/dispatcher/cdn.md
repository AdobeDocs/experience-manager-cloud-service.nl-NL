---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
feature: Dispatcher
exl-id: a3f66d99-1b9a-4f74-90e5-2cad50dc345a
source-git-commit: cc9e305d96f1de55a8c3fa450aa41142bb0adfd1
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 8%

---

# CDN in AEM as a Cloud Service {#cdn}


>[!CONTEXTUALHELP]
>id="aemcloud_golive_cdn"
>title="CDN in AEM as a Cloud Service"
>abstract="AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties."

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het belangrijkste doel is het verminderen van latentie door content te leveren die in de cache kan worden opgeslagen en die komt van de CDN-knooppunten aan de rand van de omgeving, dicht in de buurt van de browser. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

De AEM beheerde CDN zal aan de prestaties en de veiligheidsvereisten van de meeste klant voldoen. Voor publiceer rij, kunnen de klanten naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten.

## AEM beheerde CDN  {#aem-managed-cdn}

Volg de onderstaande secties om de zelfbediening UI van de Manager van de Wolk te gebruiken om voor de levering van inhoud voor te bereiden door AEM uit-van-de-doos CDN te gebruiken:

1. [SSL-certificaten beheren](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
1. [Aangepaste domeinnamen beheren](/help/implementing/cloud-manager/custom-domain-names/introduction.md)

**Beperking van het verkeer**

Door gebrek, voor een AEM beheerde opstelling CDN, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. Als u verkeer aan de publicatieservice voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) kunt u dit op een zelfbedienings manier via de UI van de Manager van de Wolk doen.

Zie [IP-Lijsten van gewenste personen beheren](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) voor meer informatie.

>[!CAUTION]
>
>Slechts zullen de verzoeken van toegestane IPs door beheerde CDN van AEM worden gediend. Als u uw eigen CDN aan AEM beheerde CDN richt, dan zorg ervoor IPs van uw CDN in de lijst van gewenste personen inbegrepen is.

## CDN van de klant wijst naar AEM Beheerde CDN {#point-to-point-CDN}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_byocdn"
>title="CDN van de klant wijst naar AEM Beheerde CDN"
>abstract="AEM als Cloud Service biedt klanten een optie om zijn bestaande CDN te gebruiken. Voor publiceer rij, kunnen de klanten naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten."

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het beheren en het richten aan AEM beheerde CDN, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM as a Cloud Service te werken - zie de hieronder vermelde configuratieinstructies.
* De klant moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Wijs de CDN toe aan de ingang van de Adobe CDN als zijn oorsprongdomein. Bijvoorbeeld, `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. SNI moet ook aan de ingang van Adobe CDN worden geplaatst
1. Stel de Hostkop in op het oorspronkelijke domein. Bijvoorbeeld: `Host:publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.
1. Stel de `X-Forwarded-Host` header met de domeinnaam zodat AEM de hostheader kan bepalen. Bijvoorbeeld: `X-Forwarded-Host:example.com`.
1. Set `X-AEM-Edge-Key`. De waarde moet van Adobe komen.
   * Dit is nodig zodat de Adobe CDN de bron van de verzoeken kan bevestigen en het `X-Forwarded-*` kopteksten naar de AEM toepassing. Bijvoorbeeld:`X-Forwarded-For` wordt gebruikt om cliëntIP te bepalen. Zo, wordt het de verantwoordelijkheid van de vertrouwde op bezoeker (d.w.z. klant-beheerde CDN) om de juistheid van te verzekeren `X-Forwarded-*` kopteksten (zie onderstaande opmerking).
   * De toegang tot de ingangen van Adobe CDN kan optioneel worden geblokkeerd wanneer een `X-AEM-Edge-Key` is niet aanwezig. Gelieve te informeren Adobe als u directe toegang tot de ingangen van Adobe CDN (moet worden geblokkeerd) nodig hebt.

Alvorens levend verkeer goed te keuren, zou u met Adobe klantensteun moeten bevestigen dat het eind-aan-eind verkeer dat correct verplettert functioneert.

Nadat u de `X-AEM-Edge-Key`, kunt u testen dat het verzoek correct als volgt wordt verpletterd:

`https://publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com -H 'X-Forwarded-Host: example.com' -H 'X-AEM-Edge-Key: <PROVIDED_EDGE_KEY>'`

Wanneer u uw eigen CDN gebruikt, hoeft u de domeinen en certificaten niet te installeren in Cloud Manager. Het verpletteren in Adobe CDN zal gebruikend het standaarddomein worden gedaan `publish-p<PROGRAM_ID>-e<ENV-ID>.adobeaemcloud.com`.

>[!NOTE]
>
>De klanten die hun eigen CDN beheren zouden de integriteit van de kopballen moeten verzekeren die door naar AEM CDN worden verzonden. Het wordt bijvoorbeeld aanbevolen dat klanten alles wissen `X-Forwarded-*` kopballen en plaatsen hen aan bekende en gecontroleerde waarden. Bijvoorbeeld: `X-Forwarded-For` zou het IP van de cliënt adres moeten bevatten, terwijl `X-Forwarded-Host` moet de host van de site bevatten.

>[!NOTE]
>
>Sandbox programmamilieu&#39;s steunen geen klant-Geleverde CDN.

Er is potentieel een kleine prestatieshit toe te schrijven aan de extra hop, hoewel de hop van klant CDN aan AEM beheerde CDN waarschijnlijk efficiënt zal zijn.

Houd er rekening mee dat deze CDN-configuratie van de klant wordt ondersteund voor de publicatielijst, maar niet vóór de auteurslaag.

## Geolocatie-headers {#geo-headers}

De AEM beheerde CDN voegt kopballen aan elk verzoek met toe:

* landcode: `x-aem-client-country`
* continentale code: `x-aem-client-continent`

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
