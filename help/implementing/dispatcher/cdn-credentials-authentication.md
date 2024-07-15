---
title: CDN-referenties en -verificatie configureren
description: Leer hoe te om geloofsbrieven en authentificatie te vormen CDN door regels in een configuratiedossier te verklaren dat dan door de Pijpleiding van de Configuratie van Cloud Manager wordt opgesteld te gebruiken.
feature: Dispatcher
exl-id: a5a18c41-17bf-4683-9a10-f0387762889b
role: Admin
source-git-commit: 73d0a4a73a3e97a91b2276c86d3ed1324de8c361
workflow-type: tm+mt
source-wordcount: '1400'
ht-degree: 0%

---

# CDN-referenties en -verificatie configureren {#cdn-credentials-authentication}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. E-mail `aemcs-cdn-config-adopter@adobe.com` om deel te nemen aan het programma voor vroegtijdige adoptie.

Adobe-verstrekte CDN heeft verscheidene eigenschappen en de diensten, waarvan sommige op geloofsbrieven en authentificatie baseren om een aangewezen niveau van ondernemingsveiligheid te verzekeren. Door regels in een configuratiedossier te verklaren dat door [ wordt opgesteld de Pijpleiding van de Configuratie van Cloud Manager te gebruiken ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline), kunnen de klanten, op een zelfbediening manier, het volgende vormen:

* De HTTP- kopbalwaarde die door de Adobe CDN wordt gebruikt om verzoeken te bevestigen die van een klant-beheerde CDN komen.
* Het API-token dat wordt gebruikt om bronnen in de CDN-cache leeg te maken.
* Een lijst met combinaties van gebruikersnaam en wachtwoord waarmee toegang kan worden verkregen tot beperkte inhoud door het verzenden van een Basic Authentication-formulier.


Elk van deze, met inbegrip van de configuratiesyntaxis, wordt beschreven in zijn eigen sectie hieronder. De [ Gemeenschappelijke sectie van de Opstelling ](#common-setup) illustreert de opstelling gemeenschappelijk aan zowel, als plaatsing. Tot slot is er een sectie op hoe te [ te roteren sleutels ](#rotating-secrets), die als goede veiligheidspraktijk wordt beschouwd.

## Door de klant beheerde CDN HTTP-headerwaarde {#CDN-HTTP-value}

Zoals die in [ CDN in AEM as a Cloud Service ](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) pagina wordt beschreven, kunnen de klanten verkiezen om verkeer door hun eigen CDN te leiden, die als Klant CDN (ook genoemd ook BYOCDN) wordt bedoeld.

Als deel van de opstelling, moeten CDN van de Adobe en CDN van de Klant over een waarde van de `X-AEM-Edge-Key` Kopbal van HTTP akkoord gaan. Deze waarde wordt geplaatst op elk verzoek, bij Klant CDN, alvorens het aan Adobe CDN wordt verpletterd, die dan bevestigt dat de waarde zoals verwacht is, zodat kan het andere kopballen van HTTP vertrouwen, met inbegrip van die die helpen het verzoek aan de aangewezen AEM oorsprong leiden.

De waarde `X-AEM-Edge-Key` wordt gedeclareerd met de onderstaande syntaxis, waarbij de werkelijke waarde(n) wordt vermeld door de eigenschappen edgeKey1 en edgeKey2. Zie de [ Gemeenschappelijke sectie van de Opstelling ](#common-setup) leren hoe te om de configuratie op te stellen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
      - name: edge-auth
        type: edge
        edgeKey1: ${{CDN_EDGEKEY_052824}}
        edgeKey2: ${{CDN_EDGEKEY_041425}}
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

De syntaxis voor de waarde `X-AEM-Edge-Key` bevat:

* Type, versie en metagegevens.
* Gegevensknooppunt dat een onderliggend knooppunt `experimental_authentication` bevat (het experimentele voorvoegsel wordt verwijderd wanneer de functie wordt losgelaten).
* Onder `experimental_authentication` staan één `authenticators` node en één `rules` node, die beide arrays zijn.
* Authenticatoren: hiermee kunt u een type token of referentie declareren. Dit is in dit geval een Edge-sleutel. Het bevat de volgende eigenschappen:
   * name - a descriptive string.
   * type - moet `edge` zijn.
   * edgeKey1 - de waarde van *x-AEM-Edge-Zeer belangrijk*, die een geheim teken moet verwijzen, dat niet in git zou moeten worden opgeslagen, maar eerder als a [ Veranderlijke van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) van type geheim verklaard. Selecteer Alle voor het veld Toegepaste service. Men adviseert dat de waarde (bijvoorbeeld, `${{CDN_EDGEKEY_052824}}`) op de dag wijst het werd toegevoegd.
   * edgeKey2 - die voor de omwenteling van geheimen wordt gebruikt, die in [ wordt beschreven het roteren geheimen sectie ](#rotating-secrets) hieronder. Definieer het op dezelfde manier als edgeKey1. Minstens een van `edgeKey1` en `edgeKey2` moet worden gedeclareerd.
<!--   * OnFailure - defines the action, either `log` or `block`, when a request doesn't match either `edgeKey1` or `edgeKey2`. For `log`, request processing will continue, while `block` will serve a 403 error. The `log` value is useful when testing a new token on a live site since you can first confirm that the CDN is correctly accepting the new token before changing to `block` mode; it also reduces the chance of lost connectivity between the customer CDN and the Adobe CDN, as a result of an incorrect configuration. -->
* Regels: hiermee kunt u aangeven welke van de authenticatoren moeten worden gebruikt en of dit voor de publicatie- en/of voorvertoningslaag is.  Het omvat:
   * name - a descriptive string.
   * wanneer - een voorwaarde die bepaalt wanneer de regel, volgens de syntaxis in het [ artikel van de Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md) zou moeten worden geëvalueerd. Typisch, zal het een vergelijking van de huidige rij (bijvoorbeeld, publiceren) omvatten zodat wordt al levend verkeer bevestigd zoals verpletterend door klant CDN.
   * action - must specify &quot;authenticate&quot;, with the intended authenticator referenced.

>[!NOTE]
>De sleutel van Edge moet als a [ veranderlijke van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) variabele van type `secret` (met *allen* die voor Toegepaste Dienst worden geselecteerd) worden gevormd, alvorens de configuratie die het van verwijzingen voorziet wordt opgesteld.

## API-token wissen {#purge-API-token}

De klanten kunnen [ het CDN geheime voorgeheugen ](/help/implementing/dispatcher/cdn-cache-purge.md) zuiveren door een verklaard Stem API teken te gebruiken. Het token wordt gedeclareerd met de onderstaande syntaxis.  Zie de [ Gemeenschappelijke sectie van de Opstelling ](#common-setup) leren hoe te om het op te stellen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
       - name: purge-auth
         type: purge
         purgeKey1: ${{CDN_PURGEKEY_031224}}
         purgeKey2: ${{CDN_PURGEKEY_021225}}
    rules:
       - name: purge-auth-rule
         when: { reqProperty: tier, equals: "publish" }
         action:
           type: authenticate
           authenticator: purge-auth
```

De syntaxis bevat:

* type, versie en metagegevens.
* gegevensknooppunt dat een onderliggend knooppunt `experimental_authentication` bevat (het experimentele voorvoegsel wordt verwijderd wanneer de functie wordt losgelaten).
* Onder `experimental_authentication` staan één `authenticators` node en één `rules` node, die beide arrays zijn.
* Authenticatoren: hiermee kunt u een type token of referentie declareren. Dit is in dit geval een purge key. Het bevat de volgende eigenschappen:
   * name - a descriptive string.
   * type - moet leeg zijn .
   * purgeKey1 - zijn waarde moet een geheim teken van verwijzingen voorzien, dat niet in git zou moeten worden opgeslagen, maar eerder gedeclareerd als [ de Variabelen van het Milieu van Cloud Manager ](/help/implementing/cloud-manager/environment-variables.md) van type `secret`.
   * Selecteer Alle voor het veld Toegepaste service. Het wordt aanbevolen dat de waarde (bijvoorbeeld `${{CDN_PURGEKEY_031224}}` ) de dag weergeeft waarop deze is toegevoegd.
   * purgeKey2 - die voor omwenteling van geheimen wordt gebruikt, die in de [ het roteren geheime sectie ](#rotating-secrets) hieronder wordt beschreven. Minstens een van `purgeKey1` en `purgeKey2` moet worden gedeclareerd.
* Regels: hiermee kunt u aangeven welke van de authenticatoren moeten worden gebruikt en of dit voor de publicatie- en/of voorvertoningslaag is.  Het omvat:
   * name - a descriptive string
   * wanneer - een voorwaarde die bepaalt wanneer de regel, volgens de syntaxis in het [ artikel van de Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md) zou moeten worden geëvalueerd. Doorgaans bevat dit een vergelijking van de huidige laag (bijvoorbeeld publiceren).
   * action - must specify &quot;authenticate&quot;, with the intended authenticator referenced.

>[!NOTE]
>De sleutel van Edge moet als veranderlijke ](/help/implementing/cloud-manager/environment-variables.md) van het Milieu van a [ Cloud Manager {van type `secret` worden gevormd, alvorens de configuratie die het van verwijzingen voorziet wordt opgesteld.

## Basisverificatie {#basic-auth}

Protect bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarvoor een gebruikersnaam en wachtwoord vereist zijn. Deze functie is vooral bedoeld voor eenvoudige gevallen van verificatiegebruik, zoals het beoordelen van inhoud door belanghebbenden uit het bedrijfsleven, in plaats van als een volledige oplossing voor toegangsrechten voor eindgebruikers.

De eindgebruiker zal een basisauthandboek als het volgende ervaren:

![ basis-dialoog ](/help/implementing/dispatcher/assets/basic-auth-dialog.png)


De syntaxis wordt gedeclareerd zoals hieronder beschreven. Zie de [ Gemeenschappelijke sectie van de Opstelling ](#common-setup) hieronder voor informatie over hoe te om het op te stellen.

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["dev"]
data:
  experimental_authentication:
    authenticators:
       - name: my-basic-authenticator
         type: basic
         credentials:
           - user: johndoe
             password: ${{JOHN_DOE_PASSWORD}}
           - user: janedoe
             password: ${{JANE_DOE_PASSWORD}}
    rules:
       - name: basic-auth-rule
         when: { reqProperty: path, like: "/summercampaign" }
         action:
           type: authenticate
           authenticator: my-basic-authenticator
```

De syntaxis bevat:

* type, versie en metagegevens.
* een gegevensknooppunt dat een `experimental_authentication` -knooppunt bevat (het experimentele voorvoegsel wordt verwijderd wanneer de functie wordt losgelaten).
* Onder `experimental_authentication` staan één `authenticators` node en één `rules` node, die beide arrays zijn.
* Authenticators: in dit scenario verklaart basisauthenticator, die de volgende structuur heeft:
   * name - a descriptive string
   * type - must be `basic`
   * een array met referenties, die elk de volgende naam/waarde-paren bevatten en die eindgebruikers kunnen invoeren in het standaarddialoogvenster voor de verificatie:
      * gebruiker - de naam van de gebruiker
      * wachtwoord - zijn waarde moet een geheim teken van verwijzingen voorzien, dat niet in git zou moeten worden opgeslagen, maar eerder als de Variabelen van het Milieu van Cloud Manager van type geheim (met **allen** geselecteerd als de dienstgebied) gedeclareerd
* Regels: laat u verklaren welke authentificators zouden moeten worden gebruikt, en welke middelen zouden moeten worden beschermd. Elke regel bevat:
   * name - a descriptive string
   * wanneer - een voorwaarde die bepaalt wanneer de regel, volgens de syntaxis in het [ artikel van de Regels van de Filter van het Verkeer ](/help/security/traffic-filter-rules-including-waf.md) zou moeten worden geëvalueerd. Doorgaans bevat dit een vergelijking van de publicatielaag of specifieke paden.
   * action - moet &quot;voor authentiek verklaren&quot;specificeren, met de voorgenomen authentificator referenced, die basisauth voor dit scenario is

>[!NOTE]
>De sleutel van Edge moet als veranderlijke ](/help/implementing/cloud-manager/environment-variables.md) van het Milieu van a [ Cloud Manager {van type `secret` worden gevormd, alvorens de configuratie die het van verwijzingen voorziet wordt opgesteld.

## Algemene instelling {#common-setup}

Alle authenticatoren zijn als volgt ingesteld:

* Maak eerst de volgende map- en bestandsstructuur in de map op hoofdniveau van het Git-project:

```
config/
     cdn.yaml
```

* Ten tweede moet het configuratiebestand van `cdn.yaml` de knooppunten bevatten die in de onderstaande voorbeelden worden beschreven. De eigenschap `kind` moet worden ingesteld op `CDN` en de versie moet worden ingesteld op de schemaversie, die momenteel `1` is. Het metagegevensknooppunt heeft een eigenschap &quot;envTypes&quot;, die aangeeft op welke omgevingstypen (dev, stage, prod) deze configuratie wordt geëvalueerd.

* Tot slot creeer een gerichte plaatsing config pijpleiding in Cloud Manager. Zie [ vormend productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en [ vormend niet-productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Let op:

* RDEs steunt momenteel niet de configuratiepijplijn.
* Met `yq` kunt u de YAML-opmaak van uw configuratiebestand lokaal valideren (bijvoorbeeld `yq cdn.yaml` ).

## Geheimen roteren {#rotating-secrets}

Het is een goede veiligheidspraktijk om af en toe geloofsbrieven te veranderen. Dit kan worden verwezenlijkt zoals hieronder wordt geïllustreerd, gebruikend het voorbeeld van een randsleutel, hoewel de zelfde strategie voor purge sleutels wordt gebruikt.

* Aanvankelijk is alleen `edgeKey1` gedefinieerd, in dit geval wordt `${{CDN_EDGEKEY_052824}}` genoemd. Dit wordt aanbevolen voor de datum waarop het is gemaakt.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* Wanneer het tijd is om de sleutel te roteren, creeer een nieuw geheim van Cloud Manager, bijvoorbeeld `${{CDN_EDGEKEY_041425}}`.
* Verwijs er in de configuratie naar vanuit `edgeKey2` en implementeer deze.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Als u zeker weet dat de oude Edge-toets niet meer wordt gebruikt, verwijdert u deze door `edgeKey1` uit de configuratie te verwijderen.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Verwijder de oude geheime verwijzing (`${{CDN_EDGEKEY_052824}}`) uit Cloud Manager en implementeer deze.
* Wanneer u gereed bent voor de volgende rotatie, volgt u dezelfde procedure, maar deze keer voegt u `edgeKey1` toe aan de configuratie en verwijst u naar een nieuw Cloud Manager-omgevingsgeheim met de naam `${{CDN_EDGEKEY_031426}}` .

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
