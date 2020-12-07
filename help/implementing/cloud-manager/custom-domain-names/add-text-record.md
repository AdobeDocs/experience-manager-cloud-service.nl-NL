---
title: Een TXT-record toevoegen
description: Een aangepaste domeinnaam toevoegen
translation-type: tm+mt
source-git-commit: 8d97bedc8c473c13e3378849741104b2c85492e2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Een TXT-record toevoegen {#adding-txt}

Een DNS TXT-record machtigt een domein om in een CDN-service te worden gehost. De klant moet een DNS TXT- verslag in de streek tot stand brengen die de Manager van de Wolk machtigt om de Dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze koppeling staat volledig onder de controle van de klant en machtigt Cloud Manager sterk om inhoud van de service aan een domein te leveren. Deze vergunning kan worden verleend en ingetrokken.

U kunt de onderstaande stappen volgen voordat u een TXT-record maakt:

* Heb de capaciteit om de DNS verslagen voor het domein van uw organisatie te wijzigen, of de aangewezen persoon te contacteren die kan.
* Identificeer uw domeingastheer of registrar als u het nog niet kent.

Wanneer u domeinverificatie start, geeft Cloud Manager u de naam en de TXT-waarde die u voor de verificatie wilt gebruiken. Voeg een TXT- verslag aan DNS van uw domein server toe gebruikend de gespecificeerde Naam en de Waarde.

1. Login aan uw Gastheer van het Domein en bezoek de DNS archiefsectie.
1. Voeg `_aemverification.[yourdomainname]` als Naam toe, en voeg de Waarde TXT precies toe aangezien het verschijnt.
Raadpleeg de voorbeelden in de onderstaande tabel.

| Domein | Naam | TXT-waarde |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Wordt weergegeven in de gebruikersinterface van Cloud Manager en is specifiek voor het domein en de omgeving van Cloud Manager |
| `test.example.com` | `_aemverification.test.example.com` | Wordt weergegeven in de gebruikersinterface van Cloud Manager en is specifiek voor het domein en de omgeving van Cloud Manager |

Wanneer u klaar bent, kunt u het resultaat verifiëren door te lopen: `dig _aemverification.[yourdomainname] -t txt`.
Het verwachte resultaat moet de TXT-waarde weergeven die is opgegeven in de gebruikersinterface van Cloud Manager.

Bijvoorbeeld, als uw domein `example.com` is, dan looppas: `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Er zijn ook verschillende [DNS opzoekgereedschappen](https://www.ultratools.com/tools/dnsLookup), Google DoH kan worden gebruikt om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.

