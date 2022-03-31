---
title: Een TXT-record toevoegen
description: Leer hoe u TXT-record toevoegt om een aangepaste domeinnaam toe te voegen in Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 491e710223c5878bfa81c4b0a57d18ec0ec29479
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 1%

---

# Een TXT-record toevoegen {#adding-txt}

Een DNS TXT-record geeft toestemming voor het hosten van een domein in een CDN-service. U moet een DNS TXT- verslag in de streek tot stand brengen die de Manager van de Wolk machtigt om de Dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze koppeling staat volledig onder uw controle en machtigt Cloud Manager om inhoud van de service aan een domein te leveren. Deze vergunning kan worden verleend en ingetrokken. De TXT-record is specifiek voor het domein en de omgeving van Cloud Manager.

U moet aan deze vereisten voldoen voordat u een TXT-record toevoegt.

* U moet de capaciteit hebben om de DNS verslagen voor het domein van uw organisatie te wijzigen, of de aangewezen persoon te contacteren die kan.
* U moet uw domeinhost of -registrar identificeren als u dit nog niet weet.

Wanneer u domeinverificatie start, geeft Cloud Manager u de naam en de TXT-waarde die u voor de verificatie wilt gebruiken. Voeg een TXT-record toe aan de DNS-server van uw domein met de opgegeven naam en waarde.

1. Meld u aan bij uw domeinhost en zoek de DNS-recordsectie.
1. Toevoegen `_aemverification.[yourdomainname]` als de **Naam** en voeg de TXT-waarde precies zo toe als deze wordt weergegeven.

Raadpleeg de voorbeelden in deze tabel.

| Domein | Naam | TXT-waarde |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Wanneer u klaar bent, kunt u het resultaat verifiëren door het volgende bevel in werking te stellen

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
>Er zijn een aantal [DNS-opzoekgereedschappen](https://www.ultratools.com/tools/dnsLookup) beschikbaar. Google DoH kan worden gebruikt om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.
