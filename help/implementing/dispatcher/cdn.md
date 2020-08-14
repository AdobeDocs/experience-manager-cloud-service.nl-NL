---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
translation-type: tm+mt
source-git-commit: 38b69b96011b7920adaf7f6cca0edff10f387b41
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 4%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

De AEM beheerde CDN zal aan de prestaties en de veiligheidsvereisten van de meeste klant voldoen. Voor publiceer rij, kunnen de klanten naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten.

## AEM beheerde CDN  {#aem-managed-cdn}

Volg deze om inhoudslevering voor te bereiden door Adobe uit-van-de-doos CDN te gebruiken:

1. Geef het ondertekende SSL-certificaat en de geheime sleutel op voor Adobe door een koppeling te delen naar een beveiligd formulier met deze gegevens. Coördineer deze taak met de klantenondersteuning.
   **Opmerking:** Aem als Cloud Service ondersteunt geen domein-gevalideerde (DV) certificaten.
1. Klantenondersteuning informeren:
   * welk aangepast domein moet worden gekoppeld aan een bepaalde omgeving, zoals gedefinieerd door de programma-id en de omgeving-id. Aangepaste domeinen aan de zijde van de auteur worden niet ondersteund.
   * als om het even welke IP toevoegend op lijst van gewenste personen nodig is om verkeer tot een bepaalde milieu te beperken.
1. Coördineer met klantensteun over timing van de noodzakelijke veranderingen in de DNS verslagen. De instructies zijn verschillend op basis van of een apex-record nodig is:
   * als een apex-record niet nodig is, moeten klanten het CNAME DNS-record zo instellen dat deze zijn FQDN aanwijst op `cdn.adobeaemcloud.com`.
   * als een apex-record nodig is, maakt u een A-record die verwijst naar de volgende IP&#39;s: 151.101.3.10, 15.101.67.10, 15.10.131.10, 15.10.195.10. Klanten hebben een apex-record nodig als de gewenste FQDN overeenkomt met de DNS-zone. Dit kan worden getest door het Unix gravingsbevel te gebruiken om te zien of past de waarde SOA van de output het domein aan. De opdracht `dig anything.dev.adobeaemcloud.com` retourneert bijvoorbeeld een SOA (Start of Authority, d.w.z. de zone) van `dev.adobeaemcloud.com` zodat het geen APEX-record is, terwijl een SOA wordt `dig dev.adobeaemcloud.com` `dev.adobeaemcloud.com` geretourneerd, zodat het een apex-record is.
1. U wordt op de hoogte gesteld wanneer de SSL-certificaten verlopen, zodat u de nieuwe SSL-certificaten opnieuw kunt verzenden.

**Beperking van het verkeer**

Door gebrek, voor een Adobe Beheerde CDN opstelling, kan al openbaar verkeer zijn weg aan de publicatiedienst, voor zowel productie als niet productie (ontwikkeling en stadium) milieu&#39;s maken. Als u verkeer aan de publicatiedienst voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) zou u met klantensteun moeten werken om deze beperkingen te vormen.

## CDN van de klant wijst naar AEM Beheerde CDN {#point-to-point-CDN}

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het beheren en het richten aan Adobe beheerde CDN, op voorwaarde dat wordt voldaan aan het volgende:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM als Cloud Service te werken - zie de configuratieinstructies hieronder.
* De klant moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Plaats de kopbal van de Gastheer domein, dat de ingang van Adobe CDN is. De waarde moet van Adobe komen.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key`, die nodig is om verkeer aan de servers van de AEM correct te leiden. De waarde moet van Adobe komen.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer dat van begin tot eind correct functioneert.

Er is een kleine prestatiesklap toe te schrijven aan de extra hop, hoewel de hop klant CDN aan een beheerde Adobe CDN waarschijnlijk efficiënt zal zijn.

Merk op dat deze klantCDN configuratie voor publiceert rij, maar niet vóór de auteursrij wordt gesteund.
