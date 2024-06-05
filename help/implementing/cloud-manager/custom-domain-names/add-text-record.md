---
title: Een TXT-record toevoegen
description: Leer hoe u TXT-record toevoegt om een aangepaste domeinnaam toe te voegen in Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# Een TXT-record toevoegen {#adding-txt}

Een DNS TXT-record geeft toestemming voor het hosten van een domein in een CDN-service. U moet een DNS TXT- verslag in de streek tot stand brengen die de Manager van de Wolk machtigt om de Dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze koppeling staat volledig onder uw controle en machtigt Cloud Manager om inhoud van de service aan een domein te leveren. Deze vergunning kan worden verleend en ingetrokken. De TXT-record is specifiek voor het domein en de omgeving van Cloud Manager.

U moet aan deze vereisten voldoen voordat u een TXT-record toevoegt.

* U moet de DNS verslagen voor het domein van uw organisatie kunnen uitgeven, of de aangewezen persoon kunnen contacteren die kan.
* U moet uw domeinhost of -registrar identificeren als u dit nog niet weet.

Wanneer u domeinverificatie start, geeft Cloud Manager u de naam en de TXT-waarde die u voor de verificatie wilt gebruiken. Voeg een TXT-record toe aan de DNS-server van uw domein met de opgegeven naam en waarde.

1. Meld u aan bij uw domeinhost en zoek de DNS-recordsectie.
1. Toevoegen `_aemverification.[yourdomainname]` als de **Naam** en voeg de TXT-waarde precies zo toe als deze wordt weergegeven.

Zie de voorbeelden in deze tabel.

| Domein | Naam | TXT-waarde |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Als u klaar bent, kunt u het resultaat controleren met de volgende opdracht

```shell
dig _aemverification.[yourdomainname] -t txt
```

Het verwachte resultaat moet de TXT-waarde weergeven die is opgegeven in de gebruikersinterface van Cloud Manager.

Als uw domein bijvoorbeeld `example.com`en vervolgens uitvoeren:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Er zijn verschillende [DNS-opzoekgereedschappen](https://www.ultratools.com/tools/dnsLookup) beschikbaar. Google DoH kan worden gebruikt om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.
