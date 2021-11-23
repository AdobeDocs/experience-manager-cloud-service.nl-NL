---
title: Een TXT-record toevoegen
description: Een aangepaste domeinnaam toevoegen
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 1427873fcc825a7321c96cbcb41f7839b6e78056
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Een TXT-record toevoegen {#adding-txt}

Een DNS TXT-record machtigt een domein om in een CDN-service te worden gehost. De klant moet een DNS TXT- verslag in de streek tot stand brengen die de Manager van de Wolk machtigt om de Dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze koppeling staat volledig onder de controle van de klant en machtigt Cloud Manager sterk om inhoud van de service aan een domein te leveren. Deze vergunning kan worden verleend en ingetrokken.

U kunt de onderstaande stappen volgen voordat u een TXT-record maakt:

* Heb de capaciteit om de DNS verslagen voor het domein van uw organisatie te wijzigen, of de aangewezen persoon te contacteren die kan.
* Identificeer uw domeingastheer of registrar als u het nog niet kent.

Wanneer u domeinverificatie start, geeft Cloud Manager u de naam en de TXT-waarde die u voor de verificatie wilt gebruiken. Voeg een TXT- verslag aan DNS van uw domein server toe gebruikend de gespecificeerde Naam en de Waarde.

1. Login aan uw Gastheer van het Domein en bezoek de DNS archiefsectie.
1. Toevoegen `_aemverification.[yourdomainname]` als de naam en voeg de TXT-waarde precies zo toe als deze wordt weergegeven.
Raadpleeg de voorbeelden in de onderstaande tabel.

| Domein | Naam | TXT-waarde |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. `Ex:adobe-aem-verification=example.com/[program]/[env]/..` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. `Ex:adobe-aem-verification=www.example.com/[program]/[env]/..` |

Wanneer u klaar bent, kunt u het resultaat verifiëren door te lopen: `dig _aemverification.[yourdomainname] -t txt`.
Het verwachte resultaat moet de TXT-waarde weergeven die is opgegeven in de gebruikersinterface van Cloud Manager.

Als uw domein bijvoorbeeld `example.com`en vervolgens uitvoeren: `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Er zijn ook verschillende [DNS-opzoekgereedschappen](https://www.ultratools.com/tools/dnsLookup), kan Google DoH worden gebruikt om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.
