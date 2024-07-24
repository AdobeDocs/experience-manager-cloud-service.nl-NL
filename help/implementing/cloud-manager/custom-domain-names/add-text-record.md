---
title: Een TXT-record toevoegen
description: Leer hoe u TXT-record toevoegt om te controleren of u eigenaar bent van een aangepast domein voor gebruik met Cloud Manager.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---


# Een TXT-record toevoegen {#adding-txt}

Leer hoe u TXT-record toevoegt om te controleren of u eigenaar bent van een aangepast domein voor gebruik met Cloud Manager.

## Wat is een TXT-record? {#what-is}

Een tekstrecord (ook wel een TXT-record genoemd) is een type resourcerecord in het Domain Name System (DNS). Het verstrekt de capaciteit om willekeurige tekst met een gastheernaam, zoals mens-leesbare informatie over hostname zoals server of netwerkinformatie te associëren.

Cloud Manager gebruikt een specifieke TXT-record om een domein te autoriseren dat in een CDN-service wordt gehost. U moet een DNS TXT- verslag in de streek tot stand brengen die Cloud Manager machtigt om de dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze vereniging is volledig onder uw controle en machtigt Cloud Manager om inhoud van de dienst aan een domein te dienen. Deze vergunning kan worden verleend en ingetrokken. De TXT-record is specifiek voor het domein en de Cloud Manager-omgeving.

## Vereisten {#requirements}

U moet aan deze vereisten voldoen voordat u een TXT-record toevoegt.

* U moet uw domeinhost of -registrar identificeren als u dit nog niet weet.
* U moet de DNS verslagen voor het domein van uw organisatie kunnen uitgeven, of de aangewezen persoon kunnen contacteren die kan.
* U moet een naam van het douanedomein zoals die in het document [ wordt beschreven eerst toevoegen een Naam van het Domein van de Douane.](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

## Een TXT-record toevoegen voor verificatie {#verification}

Er wordt een TXT-record toegevoegd als onderdeel van de verificatie van een aangepaste domeinnaam die in Cloud Manager moet worden gebruikt.

1. U moet een naam van het douanedomein zoals die in het document [ wordt beschreven eerst toevoegen een Naam van het Domein van de Douane.](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)

1. Wanneer op het **lusje van de Verificatie** van **voeg de dialoog van de Naam van het Domein** toe, toont Cloud Manager de naam en TXT waarde om voor controle te gebruiken. Deze waarde kopiëren.

   ![ de naamcontrole van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

1. Login aan uw domeingastheer en vind de DNS verslagensectie.

1. Voeg `_aemverification.[yourdomainname]` als **Naam** van de waarde toe en voeg precies de waarde TXT toe aangezien het in **verschijnt voeg de dialoog van de Naam van het Domein** toe.

   * Zie de [ voorbeelden in de volgende sectie.](#examples)

1. Sla de TXT-record op uw domeinhost op.

## Voorbeelden van TXT-records {#examples}

| Domein | Naam | TXT-waarde |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Dit is specifiek voor het domein en het milieu. Bijvoorbeeld:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

## TXT-record verifiëren {#verify}

Als u klaar bent, kunt u het resultaat controleren met de volgende opdracht.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Het verwachte resultaat zou de TXT-waarde moeten tonen die op het **lusje van de Verificatie** van **wordt verstrekt voegt de dialoog van de Naam van het Domein** van Cloud Manager UI toe.

Als uw domein bijvoorbeeld `example.com` is, voert u het volgende uit:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Er zijn verscheidene [ DNS opzoekhulpmiddelen ](https://www.ultratools.com/tools/dnsLookup) beschikbaar. Google DoH kan worden gebruikt om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Zie [ Controlerend de Status van de Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.

## Volgende stappen {#next-steps}

Nu u uw ingang van de TXT creeerde, kunt u uw status van de domeinnaam verifiëren. Ga aan het document [ Controleren de Status van de Naam van het Domein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) te werk om vestiging uw naam van het douanedomein voort te zetten.

>[!TIP]
>
>De ingang TXT en CNAME of een Verslag kunnen gelijktijdig op de regerende DNS Server worden geplaatst, waarbij tijd wordt bespaard.
>
>Als u dit wenst te doen, herzie eerst het volledige proces van vestiging een naam van het douanedomein zoals die in het document [ wordt gedetailleerd Inleiding aan de Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/introduction.md) die speciale nota nemen van het document [ help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) en werk uw DNS montages dienovereenkomstig bij.