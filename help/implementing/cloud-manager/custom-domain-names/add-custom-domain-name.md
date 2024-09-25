---
title: Een aangepaste domeinnaam toevoegen
description: Leer hoe u een aangepaste domeinnaam kunt toevoegen met behulp van Domeininstellingen in Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b9fb178760b74cb0e101506b6a9ff5ae30c18490
workflow-type: tm+mt
source-wordcount: '1509'
ht-degree: 0%

---


# Een aangepaste domeinnaam toevoegen {#adding-cdn}

Leer hoe te om een naam van het douanedomein toe te voegen gebruikend **Montages van het Domein** in Cloud Manager.

## Vereisten {#requirements}

Voldoe aan deze vereisten voordat u een aangepaste domeinnaam in Cloud Manager toevoegt.

* U moet een domeinSSL certificaat voor het domein hebben toegevoegd u alvorens een naam van het douanedomein toe te voegen zoals die in het document [ wordt beschreven een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegt.
* U moet de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** hebben om een naam van het douanedomein in Cloud Manager toe te voegen.
* Gebruik de sneltoets of een andere CDN (Content Delivery Network).

>[!IMPORTANT]
>
>Zelfs als u een niet-Adobe CDN gebruikt, moet u nog uw domein aan Cloud Manager toevoegen.

## Waar kunt u aangepaste domeinnamen toevoegen {#where-to-add-cdn}

U kunt een aangepaste domeinnaam op de volgende twee locaties in Cloud Manager toevoegen:

* [Pagina met domeininstellingen](#adding-cdn-settings)
* [De pagina Omgevingen](#adding-cdn-environments)

Wanneer u een aangepaste domeinnaam toevoegt, wordt het domein gediend met het meest specifieke, geldige certificaat. Als meerdere certificaten hetzelfde domein hebben, wordt de meest recente bijgewerkte versie gekozen. Adobe raadt u aan certificaten zodanig te beheren dat er geen overlappende domeinen zijn.

De stappen voor beide methoden die in dit document worden beschreven, zijn gebaseerd op Snelheid. Als u een verschillende CDN (het Netwerk van de Levering van de Inhoud) gebruikte, vorm uw domein met CDN u om hebt gekozen te gebruiken.

## Een aangepaste domeinnaam toevoegen {#adding-cdn-settings}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In het zijmenu, onder **Diensten**, uitgezochte ![ pictogram van Montages ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **Montages van het Domein**.

   ![ het venster van de Montages van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Vlak de hoger-juiste hoek van de **pagina van de Montages van het Domein**, klik **voegt Domein** toe.

1. In **voeg domein** dialoogdoos toe, op het **gebied van de Naam van het Domein**, ga de naam van het douanedomein in u gebruikt.
Neem geen `http://`, `https://` of spaties op wanneer u een domein betreedt.

1. Klik **creëren**.

1. In **verifieer de dialoogdoos van het Domein**, in **welk certificaattype u op het gebruiken van dit domein van plan bent?** selecteert u een van de volgende opties in de vervolgkeuzelijst:

   | Certificaattype, optie | Beschrijving |
   | --- | --- |
   | Door Adobe beheerd certificaat | Selecteer dit certificaattype als u een DV-certificaat (Domain Validation) wilt gebruiken. Deze optie is ideaal voor de meeste gevallen, die basisdomeinbevestiging verstrekken. Adobe beheert en vernieuwt het certificaat automatisch. |
   | Door de klant beheerd certificaat | Selecteer dit certificaattype als u een EV/OV-certificaat wilt gebruiken. Deze optie biedt uitgebreide beveiliging met EV (Extended Validation) of OV (Organization Validation). Gebruik deze optie als u strengere controles, hogere vertrouwensniveaus of aangepaste controle over de certificaten nodig hebt. |

1. In **verifieer domein** dialoogdoos, die op het certificaattype wordt gebaseerd u selecteerde, doe één van het volgende:

   | Als u het certificaattype hebt geselecteerd | Beschrijving |
   | --- | ---  |
   | Door Adobe beheerd certificaat | Voltooi de [ Adobe beheerde certificaatstappen ](#adobe-managed-cert-steps) alvorens aan de volgende stap verder te gaan. |
   | Door de klant beheerd certificaat | Voltooi de [ Klant beheerde certificaatstappen ](#customer-managed-cert-steps) alvorens aan de volgende stap verder te gaan. |

1. Klik **verifieer**.

1. U bent nu klaar om [ een SSL certificaat ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toe te voegen.

   >[!NOTE]
   >
   >Als u een klant-geleid SSL certificaat en een klant-geleide leverancier CDN gebruikt, kunt u overslaan toevoegend een SSL certificaat en direct gaan [ een configuratie CDN ](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md) toevoegen wanneer klaar.


### Door Adobe beheerde certificaatstappen {#adobe-managed-cert-steps}

Als u het certificaattype *beheerde Adobe* selecteerde, voltooi de volgende stappen in **verifieer domein** dialoogdoos.

![ Adobe beheerde certificaatstappen ](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Om het domein in gebruik te verifiëren, moet u een NAAM toevoegen en verifiëren.

Een `CNAME` of een verslag, zodra provisioned, leidt al verkeer van Internet voor het domein aan waar het richt. Als die plaats niet provisioned is om het verkeer te dienen, is er een stroomonderbreking. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en u klaar bent om live te gaan.

Als u deze instellingen wilt configureren, moet u bepalen of een `CNAME` - of apex-record moet zijn geconfigureerd om uw aangepaste domeinnaam te laten verwijzen naar de Cloud Manager-domeinnaam. De volgende secties van dit document kunnen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

>[!NOTE]
>
>Voor Adobe-geleide CDNs, wanneer het gebruiken van (de Bevestiging van het Domein) certificaten DV, slechts plaatsen met de bevestiging van ACME worden toegelaten.

#### Vereisten {#adobe-managed-cert-dv-requirements}

Voldoe deze vereisten alvorens uw DNS verslagen te vormen.

* Identificeer uw domeingastheer of registrar als u het nog niet kent.
* U kunt de DNS-records voor het domein van uw organisatie bewerken of contact opnemen met de juiste persoon die dat kan.
* U moet reeds uw gevormde naam van het douanedomein zoals die in het document [ wordt beschreven Controlerend de Status van de Naam van het Domein ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) hebben geverifieerd.

#### CNAME-record {#adobe-managed-cert-cname-record}

Een canonieke naam of CNAME-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein, zoals `www.example.com` , toe te wijzen aan het domein dat de inhoud van dat subdomein host.

Meld u aan bij het DNS-servicebureau en maak een `CNAME` -record om de aangepaste domeinnaam naar het doel te verwijzen, bijvoorbeeld in de volgende tabel.

| CNAME | Aangepast hoofdmappunt voor doel |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

#### APEX-record {#adobe-managed-cert-apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals `example.com` . Een ex-domein wordt geconfigureerd met een `A` -, `ALIAS` - of `ANAME` -record via uw DNS-provider. Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg de volgende `A` verslagen aan DNS montages van uw domein als uw domeinleverancier toe.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`


### Door de klant beheerde certificaatstappen {#customer-managed-cert-steps}

Als u het certificaattype *Klant beheerde certificaat* selecteerde, voltooi de volgende stappen in **verifieer domein** dialoogdoos.

![ Klant beheerde certificaatstappen ](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

Om het domein in gebruik te verifiëren, moet u een TXT-record toevoegen en verifiëren.

Een tekstrecord (ook wel een TXT-record genoemd) is een type resourcerecord in het Domain Name System (DNS). Hiermee kunt u willekeurige tekst aan een hostnaam koppelen. Deze tekst kan leesbare gegevens zoals server- of netwerkgegevens bevatten.

Cloud Manager gebruikt een specifieke TXT-record om een domein te autoriseren dat in een CDN-service wordt gehost. Creeer een DNS TXT- verslag in de streek die Cloud Manager machtigt om de dienst CDN met het douanedomein op te stellen en het te associëren met de backenddienst. Deze vereniging is volledig onder uw controle en machtigt Cloud Manager om inhoud van de dienst aan een domein te dienen. Deze vergunning kan worden verleend en ingetrokken. De TXT-record is specifiek voor het domein en de Cloud Manager-omgeving.

#### Vereisten {#customer-managed-cert-requirements}

Voldoe aan deze vereisten voordat u een TXT-record toevoegt.

* Identificeer uw domeingastheer of registrar als u het nog niet kent.
* U kunt de DNS-records voor het domein van uw organisatie bewerken of contact opnemen met de juiste persoon die dat kan.
* Voeg eerst een aangepaste domeinnaam toe, zoals eerder in dit artikel wordt beschreven.

#### Een TXT-record toevoegen ter verificatie {#customer-managed-cert-verification}

1. In **verifieer domein** dialoogdoos, toont Cloud Manager de naam en TXT waarde voor controle te gebruiken. Deze waarde kopiëren.

1. Login aan uw DNS dienstverlener en vind de DNS archiefsectie.

1. Voeg `aemverification.[yourdomainname]` als **Naam** van de waarde toe en voeg precies de waarde TXT toe aangezien het op het **gebied van de Naam van het Domein** verschijnt.

   **de verslagvoorbeelden van TXT**

   | Domein | Naam | TXT-waarde |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Deze waarde is specifiek voor het domein en de omgeving. Bijvoorbeeld:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Kopieer de volledige waarde die wordt weergegeven in de gebruikersinterface van Cloud Manager. Deze waarde is specifiek voor het domein en de omgeving. Bijvoorbeeld:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Sla de TXT-record op uw domeinhost op.

#### TXT-record verifiëren {#customer-managed-cert-verify}

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
>Er zijn verscheidene [ DNS opzoekhulpmiddelen ](https://www.ultratools.com/tools/dnsLookup) beschikbaar. U kunt Google DoH gebruiken om TXT-recorditems op te zoeken en vast te stellen of de TXT-record ontbreekt of onjuist is.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij, die in de lijst van de Montages van het Domein kan worden gezien. Zie [ de status van de naam van het douanedomein van de Controle ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.

<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->

>[!TIP]
>
>De ingang TXT en CNAME of een Verslag kunnen gelijktijdig op de regerende DNS server worden geplaatst, waarbij tijd wordt bespaard.
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


## Een aangepaste domeinnaam toevoegen op de pagina Environment {#adding-cdn-environments}

<!-- I DON'T SEE THIS ABILITY ANYMORE IN THE UI -->

De stappen om een naam van het douanedomein van de **pagina van Milieu&#39;s** toe te voegen zijn het zelfde als wanneer [ toevoegend een naam van het douanedomein van de pagina van de Montages van het Domein ](#adding-cdn-settings), maar het ingangspunt verschilt. Volg deze stappen om een naam van het douanedomein van de **pagina van Milieu&#39;s** toe te voegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan de **detailpagina van het Detail van Milieu** voor het milieu van belang.

   ![ die domeinnaam op de pagina van de Details van het Milieu ingaan ](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de **lijst van de Namen van het Domein** om de naam van het douanedomein voor te leggen.

   1. Voer de aangepaste domeinnaam in.
   1. Selecteer het SSL-certificaat dat aan deze naam is gekoppeld in de vervolgkeuzelijst.
   1. Klik ![ toevoegen pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **** toevoegen.

   ![ voeg een naam van het douanedomein toe ](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. **voegt domeinnaam** dialoogdoos toe opent aan de **Naam van het Domein** tabel. Ga zoals u voor [ verder toevoegend een naam van het douanedomein van de pagina van de Montages van het Domein ](#adding-cdn-settings).
