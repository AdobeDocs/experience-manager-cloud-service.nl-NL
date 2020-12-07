---
title: 'DNS-instellingen configureren '
description: DNS-instellingen configureren
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes wordt geverifieerd en opgesteld, bent u bereid om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan vóór Go-live.

>[!NOTE]
>U of het aangewezen individu in uw organisatie moet login of uw DNS leverancier (het bedrijf kunnen contacteren van wie u het domein van) kocht en updates in uw DNS montages maken.

Hiervoor moet u bepalen of u uw DNS-instellingen moet configureren naar een `CNAME`- of Apex-record die uw aangepaste domeinnaam verwijst naar de domeinnaam van Cloud Manager. Een `CNAME` of een verslag, zodra provisioned zal al Internet verkeer voor het domein leiden aan waar het richt. Als die plaats niet provisioned is om het verkeer te dienen, zal er een stroomonderbreking zijn. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en de klant klaar is voor Go-Live.

## CNAME-record {#cname-record}

De volgende secties zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

Een Canonical Name- of `CNAME`-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein, zoals `www.example.com`, toe te wijzen aan het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw Domeinregister en maak een CNAME-record om de aangepaste domeinnaam naar het doel te verwijzen, zoals hieronder wordt weergegeven:

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## APEX-record {#apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals example.com. Een apex domein wordt gevormd met `A`, `ALIAS`, of `ANAME` verslag door uw DNS leverancier. De Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg alle volgende A verslagen aan DNS van uw Domein montages via uw domeinleverancier toe:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
