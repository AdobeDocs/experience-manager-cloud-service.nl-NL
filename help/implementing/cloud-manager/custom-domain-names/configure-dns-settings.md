---
title: DNS-instellingen configureren
description: Leer hoe te om DNS montages voor uw namen van het douanedomein te vormen uw plaats toelaat om bezoekers te dienen.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes [ wordt geverifieerd en opgesteld, ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) u bereid bent om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan alvorens te leven.

## Wat zijn DNS-instellingen? {#dns-settings}

Een `CNAME` - of A-record leidt, zodra deze is ingericht, al het internetverkeer voor het domein naar de locatie waar het naartoe wijst. Als die plaats niet provisioned is om het verkeer te dienen, is er een stroomonderbreking. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en u klaar bent om live te gaan.

Als u deze instellingen wilt configureren, moet u bepalen of een `CNAME` - of apex-record moet zijn geconfigureerd om uw aangepaste domeinnaam te laten verwijzen naar de Cloud Manager-domeinnaam. De volgende secties van dit document zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

## Vereisten {#requirements}

U moet aan deze vereisten voldoen alvorens uw DNS verslagen te vormen.

* U moet uw domeinhost of -registrar identificeren als u dit nog niet weet.
* U moet de DNS verslagen voor het domein van uw organisatie kunnen uitgeven, of de aangewezen persoon kunnen contacteren die kan.
* U moet reeds uw gevormde naam van het douanedomein zoals die in het document [ wordt beschreven Controlerend de Status van de Naam van het Domein hebben geverifieerd.](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md)

## CNAME-record {#cname-record}

Een canonieke naam of CNAME-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein, zoals `www.example.com` , toe te wijzen aan het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw domeinregistrar en maak een `CNAME` -record om de aangepaste domeinnaam naar het doel te verwijzen, zoals in de volgende tabel.

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX-record {#apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals `example.com` . Een ex-domein wordt geconfigureerd met een `A` , `ALIAS` of `ANAME` -record via uw DNS-provider. Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg de volgende `A` verslagen aan DNS montages van uw domein als uw domeinleverancier toe.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## Volgende stappen {#next-steps}

Zodra u uw DNS verslagen voor uw naam van het douanedomein hebt gevormd, zult u die montages in Cloud Manager moeten verifiëren. Ga aan het document [ te werk controlerend DNS Status van het Verslag ](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) om uw naam van het douanedomein te voltooien.
