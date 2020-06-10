---
title: CDN in AEM as a Cloud Service
description: CDN in AEM as a Cloud Service
translation-type: tm+mt
source-git-commit: 9d99a7513a3a912b37ceff327e58a962cc17c627
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 4%

---


# CDN in AEM as a Cloud Service {#cdn}

AEM als Cloud Service wordt geleverd met een ingebouwde CDN. Het is vooral de bedoeling de latentie te verminderen door cachebare inhoud van de CDN-knooppunten aan de rand, bij de browser, te leveren. Het systeem wordt volledig beheerd en geconfigureerd voor optimale prestaties van AEM-applicaties.

In totaal biedt AEM twee opties:

1. AEM Beheerde CDN - AEM&#39;s &#39;out-of-box&#39; CDN. Het is een strak geïntegreerde optie en vereist geen zware klanteninvestering in het steunen van de integratie CDN met AEM.
1. Door de klant beheerde CDN verwijst naar een door AEM beheerde CDN. De klant wijst zijn eigen CDN aan een CDN die buiten de box van AEM valt. De klant zal nog hun eigen CDN moeten beheren, maar de investering in de integratie met AEM is gematigd.

De eerste optie zou aan de meeste van de klantenprestaties en veiligheidsvereisten moeten voldoen. Bovendien vereist het minimale klanteninspanning.

De tweede mogelijkheid wordt per geval toegestaan. Het besluit is gebaseerd op het voldoen aan bepaalde voorwaarden met inbegrip van, maar niet beperkt tot, de klant die een erfenisintegratie met hun CDN verkoper heeft die moeilijk is te verlaten.

Hieronder ziet u een beslissingsmatrix waarmee de twee opties worden vergeleken. Meer gedetailleerde informatie vindt u in de volgende secties.

| Details | Door AEM beheerde CDN | Door de klant beheerde CDN verwijst naar AEM CDN |
|---|---|---|
| **Klantenservice** | Geen, het is volledig geïntegreerd. U hoeft alleen CNAME naar door AEM beheerde CDN te wijzen. | Matige klanteninvestering. De klant moet zijn eigen CDN beheren. |
| **Voorwaarden** | Geen | Bestaande CDN die te vervangen is. moet een geslaagde belastingstest aantonen voordat hij in leven wordt gehouden. |
| **CDN-expertise** | Geen | Vereist minstens één middel van de deeltijdtechniek met gedetailleerde kennis CDN die CDN van de klant kan vormen. |
| **Beveiliging** | Beheerd door Adobe. | Beheerd door Adobe (en optioneel door de klant op hun eigen CDN). |
| **Prestaties** | Geoptimaliseerd door Adobe. | Zal van sommige mogelijkheden van AEM CDN profiteren, maar potentieel een kleine prestatiesklap toe te schrijven aan de extra hop. **Opmerking**: Hops from customer CDN to Adobe&#39;s out of the box CDN likely to be effective.) |
| **Caching** | Ondersteunt cachekoppen die worden toegepast op de dispatcher. | Ondersteunt cachekoppen die worden toegepast op de dispatcher. |
| **Compressiemogelijkheden voor afbeeldingen en video** | Kan werken met dynamische media van Adobe. | Kan werken met Adobe Dynamic Media of CDN-afbeelding/video-oplossing die door klanten wordt beheerd. |

## Door AEM beheerde CDN  {#aem-managed-cdn}

Voer de volgende handelingen uit om de levering van inhoud voor te bereiden met CDN van Adobe buiten de doos:

1. U geeft het ondertekende SSL-certificaat en de geheime sleutel aan Adobe door een koppeling te delen naar een beveiligd formulier met deze gegevens. Coördineer deze taak met de klantenondersteuning.
   **Opmerking:** Aem als de Dienst van de Wolk steunt geen domein Gevalideerde (DV) certificaten.
1. U moet de klantenondersteuning op de hoogte stellen:
   * welk aangepast domein moet worden gekoppeld aan een bepaalde omgeving, zoals gedefinieerd door de programma-id en de omgeving-id. Aangepaste domeinen aan de zijde van de auteur worden niet ondersteund.
   * als om het even welk IP fluitend nodig is om verkeer tot een bepaald milieu te beperken.
1. U zou met klantensteun over timing van de noodzakelijke veranderingen in de DNS verslagen moeten coördineren. De instructies zijn verschillend op basis van of een apex-record nodig is:
   * als een apex-record niet nodig is, moeten klanten het CNAME DNS-record zo instellen dat deze zijn FQDN aanwijst op `cdn.adobeaemcloud.com`.
   * als een apex-record nodig is, maakt u een A-record die verwijst naar de volgende IP&#39;s: 151.101.3.10, 15.101.67.10, 15.10.131.10, 15.10.195.10. Klanten hebben een apex-record nodig als de gewenste FQDN overeenkomt met de DNS-zone. Dit kan worden getest door het Unix gravingsbevel te gebruiken om te zien of past de waarde SOA van de output het domein aan. De opdracht `dig anything.dev.adobeaemcloud.com` retourneert bijvoorbeeld een SOA (Start of Authority, d.w.z. de zone) van `dev.adobeaemcloud.com` zodat het geen APEX-record is, terwijl een SOA wordt `dig dev.adobeaemcloud.com` `dev.adobeaemcloud.com` geretourneerd, zodat het een apex-record is.
1. U wordt op de hoogte gesteld wanneer de SSL-certificaten verlopen, zodat u de nieuwe SSL-certificaten opnieuw kunt verzenden.

**Beperking van het verkeer**

Standaard kan voor een CDN-installatie onder beheer van Adobe, al het openbaar verkeer zijn weg maken naar de publicatieservice, voor zowel productie- als niet-productie (ontwikkeling en stadium)-omgevingen. Als u verkeer aan de publicatiedienst voor een bepaald milieu wilt beperken (bijvoorbeeld, beperkt het opvoeren door een waaier van IP adressen) zou u met klantensteun moeten werken om deze beperkingen te vormen.

## CDN van klant wijst naar door AEM beheerde CDN {#point-to-point-CDN}

Gesteund als u uw bestaande CDN wilt gebruiken, maar kan niet aan de vereisten van een Door Klant beheerde CDN voldoen. In dit geval beheert u uw eigen CDN, maar wijst u naar de beheerde CDN van Adobe.

Houd er rekening mee dat:

1. U moet een bestaande CDN hebben.
1. Je moet het beheren.
1. U moet CDN kunnen vormen om met Aem als Dienst van de Wolk te werken - zie de configuratieinstructies hieronder.
1. U moet ingenieurs CDN hebben die op vraag zijn in geval de verwante kwesties zich voordoen.
1. U moet een ladingstest uitvoeren en met succes overgaan alvorens aan productie te gaan.

Configuratieinstructies:

1. Stel de `X-Forwarded-Host` koptekst in met de domeinnaam.
1. Stel de Hostkop in met het oorspronkelijke domein. Dit is de invoer van de CDN van Adobe. De waarde moet afkomstig zijn van Adobe.
1. Verzend de kopbal SNI naar de oorsprong. Net als de Hostkop moet de sni-header het oorspronkelijke domein zijn.
1. Plaats `X-Edge-Key`, die nodig is om verkeer aan de servers van AEM correct te leiden. De waarde moet afkomstig zijn van Adobe.

Voorafgaand aan het goedkeuren van levend verkeer, zou u met de klantensteun van Adobe moeten bevestigen dat het verkeer van begin tot eind het verpletteren correct functioneert.
