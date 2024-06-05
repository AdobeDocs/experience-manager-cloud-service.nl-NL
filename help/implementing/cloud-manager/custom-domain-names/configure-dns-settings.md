---
title: DNS-instellingen configureren
description: Leer hoe te om DNS montages voor uw namen van het douanedomein te vormen.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes wordt geverifieerd en opgesteld, bent u bereid om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan alvorens te leven.

## Wat zijn DNS-instellingen? {#dns-settings}

A `CNAME` of Een record: wanneer provisioned is, wordt al het internetverkeer voor het domein doorgestuurd naar de locatie waar het naartoe wijst. Als die plaats niet provisioned is om het verkeer te dienen, is er een stroomonderbreking. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en u klaar bent om live te gaan.

Om deze montages te vormen, moet u bepalen als `CNAME` of Apex-record moet zo zijn geconfigureerd dat uw aangepaste domeinnaam naar de domeinnaam van Cloud Manager wordt verwezen. De volgende secties zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

>[!NOTE]
>
>U of het aangewezen individu in uw organisatie moet login of uw DNS leverancier (het bedrijf van wie u het domein) kocht kunnen contacteren en updates in uw DNS montages maken.

## CNAME-record {#cname-record}

Een canonieke naam of CNAME-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein toe te wijzen, zoals `www.example.com` naar het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw domeinregistrar en maak een `CNAME` registreert om uw naam van het douanedomein aan het doel zoals in de volgende lijst te richten.

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX-record {#apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals `example.com`. Een apex domein wordt gevormd met een `A` , `ALIAS` , of `ANAME` neemt door uw DNS leverancier op. Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg het volgende toe `A` records naar de DNS-instellingen van uw domein via uw domeinprovider.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
