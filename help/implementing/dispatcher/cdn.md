---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
translation-type: tm+mt
source-git-commit: dd32e9357bfbd8a9b23db1167cecc4e713cccd99
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 5%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM als Cloud Service wordt verzonden met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

AEM beheerde CDN zal aan de prestaties en veiligheidsvereisten van de meeste klant voldoen. De klanten kunnen naar keuze aan het van hun eigen CDN richten, die zij zullen moeten beheren. Dit wordt per geval toegestaan, op basis van het voldoen aan bepaalde voorwaarden waaronder, maar niet beperkt tot, de klant die een oudere integratie met zijn CDN-leverancier heeft die moeilijk kan worden verlaten.

## Door AEM beheerde CDN  {#aem-managed-cdn}

Voer de volgende handelingen uit om de levering van inhoud voor te bereiden met CDN van Adobe buiten de doos:

1. Geef het ondertekende SSL-certificaat en de geheime sleutel aan Adobe door een koppeling te delen naar een beveiligd formulier met deze gegevens. Coördineer deze taak met de klantenondersteuning.
   **Opmerking:** Aem als Cloud Service ondersteunt geen domein-gevalideerde (DV) certificaten.
1. Klantenondersteuning informeren:
   * welk aangepast domein moet worden gekoppeld aan een bepaalde omgeving, zoals gedefinieerd door de programma-id en de omgeving-id. Aangepaste domeinen aan de zijde van de auteur worden niet ondersteund.
   * als om het even welk IP toegestaan is nodig om verkeer tot een bepaalde milieu te beperken.
1. Coördineer met klantensteun over timing van de noodzakelijke veranderingen in de DNS verslagen. De instructies zijn verschillend op basis van of een apex-record nodig is:
   * als een apex-record niet nodig is, moeten klanten het CNAME DNS-record zo instellen dat deze zijn FQDN aanwijst op `cdn.adobeaemcloud.com`.
   * als een apex-record nodig is, maakt u een A-record die verwijst naar de volgende IP&#39;s: 151.101.3.10, 15.101.67.10, 15.10.131.10, 15.10.195.10. Klanten hebben een apex-record nodig als de gewenste FQDN overeenkomt met de DNS-zone. Dit kan worden getest door het Unix gravingsbevel te gebruiken om te zien of past de waarde SOA van de output het domein aan. De opdracht `dig anything.dev.adobeaemcloud.com` retourneert bijvoorbeeld een SOA (Start of Authority, d.w.z. de zone) van `dev.adobeaemcloud.com` zodat het geen APEX-record is, terwijl een SOA wordt `dig dev.adobeaemcloud.com` `dev.adobeaemcloud.com` geretourneerd, zodat het een apex-record is.
1. U wordt op de hoogte gesteld wanneer de SSL-certificaten verlopen, zodat u de nieuwe SSL-certificaten opnieuw kunt verzenden.

**Beperking van het verkeer**

Standaard kan voor een CDN-installatie onder beheer van Adobe, al het openbaar verkeer zijn weg maken naar de publicatieservice, voor zowel productie- als niet-productie (ontwikkeling en stadium)-omgevingen. Als u verkeer aan de publicatiedienst voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) zou u met klantensteun moeten werken om deze beperkingen te vormen.

## CDN van klant wijst naar door AEM beheerde CDN {#point-to-point-CDN}

Als een klant zijn bestaande CDN moet gebruiken, kunnen zij het leiden en het richten aan beheerde CDN van Adobe, op voorwaarde dat het volgende wordt voldaan:

* De klant moet een bestaande CDN hebben die bezwaarlijk zou zijn om te vervangen.
* De klant moet het beheren.
* De klant moet CDN kunnen vormen om met AEM als Cloud Service te werken - zie de configuratieinstructies hieronder.
* De klant moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
* De klant moet een laadtest uitvoeren en met succes doorstaan alvorens naar productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Stel de Hostkop in met het oorspronkelijke domein. Dit is de invoer van de CDN van Adobe. De waarde moet afkomstig zijn van Adobe.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key`, die nodig is om verkeer aan de servers van AEM correct te leiden. De waarde moet afkomstig zijn van Adobe.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer van begin tot eind het verpletteren correct functioneert.

Merk op dat er potentieel een kleine prestatieshit toe te schrijven aan de extra hop is, hoewel de hop van klant CDN aan beheerde CDN van Adobe waarschijnlijk efficiënt zal zijn.
