---
title: 'DNS-instellingen configureren '
description: DNS-instellingen configureren
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 016954bc712a135886a6031deba05d92e7d5099c
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# DNS-instellingen configureren {#configure-dns}

Nadat uw naam van het douanedomein met succes wordt geverifieerd en opgesteld, bent u bereid om de DNS verslagen voor uw naam van het douanedomein met uw DNS leverancier bij te werken. Hierdoor kan uw site bezoekers bedienen. Deze activiteit wordt daarom typisch gedaan vóór Go-live.

>[!NOTE]
>U of het aangewezen individu in uw organisatie moet login of uw DNS leverancier (het bedrijf kunnen contacteren van wie u het domein van) kocht en updates in uw DNS montages maken.

Om dit te doen, moet u bepalen als u uw DNS montages aan a moet vormen `CNAME` of Apex-record die uw aangepaste domeinnaam verwijst naar de domeinnaam van Cloud Manager. A `CNAME` of Een record: wanneer provisioned is, wordt al het internetverkeer voor het domein doorgestuurd naar de locatie waar het naartoe wijst. Als die plaats niet provisioned is om het verkeer te dienen, zal er een stroomonderbreking zijn. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en de klant klaar is voor Go-Live.

De volgende stappen moeten worden uitgevoerd zoals aangegeven in onderstaande tabel:

| Stap |  | Verantwoordelijkheid | Meer informatie |
|--- |--- |--- |---|
| SSL-certificaat toevoegen | SSL-certificaat toevoegen | Klant | [Een SSL-certificaat toevoegen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) |
| Domeinverificatie | TXT-record toevoegen | Klant | [Een TXT-record toevoegen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-text-record.html?lang=en) |
| Status domeinverificatie controleren |  | Klant |  |
|  | Status: Domeinverificatie mislukt | Klant | [Status domeinnaam controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
|  | Status: Geverifieerd, implementatie mislukt | Adobe-contactpersoon | [Status domeinnaam controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
| DNS-records toevoegen die wijzen naar AEM as a Cloud Service door CNAME- of APEX-records toe te voegen | DNS-instellingen configureren | Klant | [DNS-instellingen configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/configure-dns-settings.html?lang=en) |
| DNS-recordstatus controleren |  | Klant | [DNS-recordstatus controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | Status: DNS-status niet gedetecteerd | Klant | [DNS-recordstatus controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | Status: DNS wordt onjuist omgezet | Klant |  |


## CNAME-record {#cname-record}

De volgende secties zullen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

Een canonieke naam of `CNAME` record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein toe te wijzen, zoals `www.example.com`  naar het domein dat de inhoud van dat subdomein host.

Meld u aan bij uw Domeinregister en maak een CNAME-record om de aangepaste domeinnaam naar het doel te verwijzen, zoals hieronder wordt weergegeven:

| CNAME | Aangepast domeinnaampunt voor doel |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## APEX-record {#apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals example.com. Een apex domein wordt gevormd met een `A` , `ALIAS` , of `ANAME` neemt door uw DNS leverancier op. De Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg alle volgende A verslagen aan DNS van uw Domein montages via uw domeinleverancier toe:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
