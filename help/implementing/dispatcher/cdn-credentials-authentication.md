---
title: CDN-referenties en -verificatie configureren
description: Leer hoe te om geloofsbrieven en authentificatie te vormen CDN door regels in een configuratiedossier te verklaren dat dan door de Pijpleiding van de Configuratie van de Manager van de Wolk te gebruiken wordt opgesteld.
feature: Dispatcher
source-git-commit: ee993798739232da794dbf7ff0a643ca93effa7d
workflow-type: tm+mt
source-wordcount: '1143'
ht-degree: 0%

---

# CDN-referenties en -verificatie configureren {#cdn-credentials-authentication}

>[!NOTE]
>Deze functie is nog niet algemeen beschikbaar. Als u wilt deelnemen aan het programma voor vroegtijdige adoptie, kunt u een e-mail sturen `aemcs-cdn-config-adopter@adobe.com`.

Adobe-verstrekte CDN heeft verscheidene eigenschappen en de diensten, waarvan sommige op geloofsbrieven en authentificatie baseren om een aangewezen niveau van ondernemingsveiligheid te verzekeren. Door regels in een configuratiedossier te verklaren dat door te gebruiken wordt opgesteld [Cloud Manager Configuration Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#config-deployment-pipeline), kunnen de klanten, op een zelfbediening manier, het volgende vormen:

* De HTTP- kopbalwaarde die door de Adobe CDN wordt gebruikt om verzoeken te bevestigen die van een klant-beheerde CDN komen.
* Het API-token dat wordt gebruikt om bronnen in de CDN-cache leeg te maken.

Elk van deze, met inbegrip van de configuratiesyntaxis, wordt beschreven in zijn eigen sectie hieronder. De [Algemene instelling](#common-setup) de sectie illustreert de opstelling gemeenschappelijk voor zowel, als plaatsing. Tot slot is er een sectie over hoe te [roteren, toetsen](#rotating-secrets), wat als een goede veiligheidspraktijk wordt beschouwd.

## Door de klant beheerde CDN HTTP-headerwaarde {#CDN-HTTP-value}

Zoals beschreven in het [CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) pagina, kunnen de klanten verkiezen om verkeer door hun eigen CDN te leiden, die als CDN van de Klant (ook genoemd ook BYOCDN) wordt bedoeld.

Als deel van de opstelling, moeten de Adobe CDN en de Klant CDN over een waarde van overeenkomen `X-AEM-Edge-Key` HTTP-header. Deze waarde wordt geplaatst op elk verzoek, bij Klant CDN, alvorens het aan Adobe CDN wordt verpletterd, die dan bevestigt dat de waarde zoals verwacht is, zodat kan het andere kopballen van HTTP vertrouwen, met inbegrip van die die helpen het verzoek aan de aangewezen AEM oorsprong leiden.

De `X-AEM-Edge-Key` Deze waarde wordt gedeclareerd met de onderstaande syntaxis. Zie de [Algemene instelling](#common-setup) te leren hoe u het kunt implementeren.

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
        onFailure: log # optional, default: log, enum: log/block
    rules:
      - name: edge-auth-rule
        when: { reqProperty: tier, equals: "publish" }
        action:
          type: authenticate
          authenticator: edge-auth
```

De syntaxis voor de `X-AEM-Edge-Key` waarde omvat:

* Type, versie en metagegevens.
* Gegevensknooppunt dat een onderliggend item bevat `experimental_authentication` node (het experimentele voorvoegsel wordt verwijderd wanneer het kenmerk wordt losgelaten).
* Onder experimentele_authenticatie, met één authenticatorknoop en één regelknoop, allebei waarvan series zijn.
* Authenticatoren: hiermee kunt u een type token of referentie declareren. Dit is in dit geval een Edge-sleutel. Het bevat de volgende eigenschappen:
   * name - a descriptive string.
   * type - moet rand zijn.
   * edgeKey1 - de waarde ervan moet naar een geheim token verwijzen, dat niet in een it moet worden opgeslagen, maar als een [Omgevingsvariabele van Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) van het type geheim. Selecteer Alle voor het veld Toegepaste service. Het wordt aanbevolen de waarde (bijvoorbeeld`${{CDN_EDGEKEY_052824}}`) weerspiegelt de dag waarop deze is toegevoegd.
   * edgeKey2 - wordt gebruikt voor het roteren van geheimen, die in [roteren van geheimen](#rotating-secrets) hieronder. Ten minste één van `edgeKey1` en `edgeKey2` moeten worden aangegeven.
   * OnFailed - definieert de handeling, ofwel `log` of `block`, wanneer een aanvraag niet overeenkomt met `edgeKey1` of `edgeKey2`. Voor `log`, verzoek wordt verwerkt, terwijl `block` zal een fout van 403 dienen. De `log` Deze waarde is nuttig wanneer u een nieuwe token test op een live site, omdat u eerst kunt bevestigen dat de CDN het nieuwe token correct accepteert voordat u overschakelt op `block` wijze; het vermindert ook de kans op verloren connectiviteit tussen de klant CDN en de Adobe CDN, als resultaat van een onjuiste configuratie.
* Regels: hiermee kunt u aangeven welke van de authenticatoren moeten worden gebruikt en of dit voor de publicatie- en/of voorvertoningslaag is.  Het omvat:
   * name - a descriptive string.
   * Wanneer - een voorwaarde die bepaalt wanneer de regel, volgens de syntaxis in zou moeten worden geëvalueerd [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md) artikel. Typisch, zal het een vergelijking van de huidige rij (bijvoorbeeld, publiceren) omvatten zodat wordt al levend verkeer bevestigd zoals verpletterend door klant CDN.
   * action - must specify &quot;authenticate&quot;, with the intended authenticator referenced.

>[!NOTE]
>De sleutel van de Rand moet als a worden gevormd [Omgevingsvariabele van Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) variabele van het type `secret`, alvorens de configuratie die het van verwijzingen voorziet wordt opgesteld.

## API-token wissen {#purge-API-token}

Klanten kunnen de CDN-cache leegmaken met behulp van een gedeclareerd token voor de zuiverings-API. Het token wordt gedeclareerd met de onderstaande syntaxis.  Zie de [Algemene instelling](#common-setup) te leren hoe u het kunt implementeren.

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
* gegevensknooppunt dat een onderliggend item bevat `experimental_authentication` node (het experimentele voorvoegsel wordt verwijderd wanneer het kenmerk wordt losgelaten).
* Onder `experimental_authentication`, met één authenticator-knooppunt.
* Authenticatoren: hiermee kunt u een type token of referentie declareren. Dit is in dit geval een purge key. Het bevat de volgende eigenschappen:
   * name - a descriptive string.
   * type - moet leeg zijn .
   * purgeKey1 - de waarde ervan moet verwijzen naar een geheim token, dat niet opgeslagen mag worden in een it, maar gedeclareerd moet worden als [Omgevingsvariabelen van Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) van het type `secret`.
   * Selecteer Alle voor het veld Toegepaste service. Het wordt aanbevolen de waarde (bijvoorbeeld `${{CDN_PURGEKEY_031224}}`) weerspiegelt de dag waarop deze is toegevoegd.
   * purgeKey2 - gebruikt voor het roteren van geheimen, die in [roteren van geheimen](#rotating-secrets) hieronder. Ten minste één van `purgeKey1` en `purgeKey2` moeten worden aangegeven.
* Regels: hiermee kunt u aangeven welke van de authenticatoren moeten worden gebruikt en of dit voor de publicatie- en/of voorvertoningslaag is.  Het omvat:
   * name - a descriptive string
   * Wanneer - een voorwaarde die bepaalt wanneer de regel, volgens de syntaxis in zou moeten worden geëvalueerd [Regels voor verkeersfilters](/help/security/traffic-filter-rules-including-waf.md) artikel. Doorgaans bevat dit een vergelijking van de huidige laag (bijvoorbeeld publiceren).
   * action - must specify &quot;authenticate&quot;, with the intended authenticator referenced.

>[!NOTE]
>De sleutel van de Rand moet als a worden gevormd [Omgevingsvariabele van Cloud Manager](/help/implementing/cloud-manager/environment-variables.md) variabele van het type `secret`, alvorens de configuratie die het van verwijzingen voorziet wordt opgesteld.

## Algemene instelling {#common-setup}

Alle authenticatoren zijn als volgt ingesteld:

* Maak eerst de volgende map- en bestandsstructuur in de map op hoofdniveau van het Git-project:

```
config/
     cdn.yaml
```

* Ten tweede, de `cdn.yaml` Het configuratiebestand moet de knooppunten bevatten die in de onderstaande voorbeelden worden beschreven. De `kind` eigenschap moet worden ingesteld op `CDN` en de versie moet worden ingesteld op de schemaversie die momenteel is `1`. Het metagegevensknooppunt heeft een eigenschap &quot;envTypes&quot;, die aangeeft op welke omgevingstypen (dev, stage, prod) deze configuratie wordt geëvalueerd.

* Tot slot creeer een gerichte plaatsing config pijpleiding in de Manager van de Wolk. Zie [productiepijpleidingen configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) en [configureren van niet-productiepijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md).

Let op:

* RDEs steunt momenteel niet de configuratiepijplijn.
* U kunt `yq` om de opmaak van uw configuratiebestand lokaal te valideren (bijvoorbeeld `yq cdn.yaml`).

## Geheimen roteren {#rotating-secrets}

Het is een goede veiligheidspraktijk om af en toe geloofsbrieven te veranderen. Dit kan worden verwezenlijkt zoals hieronder wordt geïllustreerd, gebruikend het voorbeeld van een randsleutel, hoewel de zelfde strategie voor purge sleutels wordt gebruikt.

* Aanvankelijk alleen `edgeKey1` is gedefinieerd, in dit geval waarnaar wordt verwezen als `${{CDN_EDGEKEY_052824}}`, die als aanbevolen conventie de datum van oprichting weerspiegelt.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
```

* Wanneer het tijd is om de sleutel te roteren, creeer een nieuw geheim van de Manager van de Wolk, bijvoorbeeld `${{CDN_EDGEKEY_041425}}`.
* Verwijs in de configuratie het van `edgeKey2` en implementeren.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey1: ${{CDN_EDGEKEY_052824}}
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* Als u zeker weet dat de oude Edge-toets niet meer wordt gebruikt, verwijdert u deze door deze te verwijderen `edgeKey1` uit de configuratie.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
```

* De oude geheime verwijzing verwijderen (`${{CDN_EDGEKEY_052824}}`) van Cloud Manager en implementeren.
* Wanneer klaar voor de volgende omwenteling, volg de zelfde procedure echter dit keer zult u toevoegen `edgeKey1` naar de configuratie, waarbij wordt verwezen naar een nieuw Cloud Manager-omgevingsgeheim genaamd, bijvoorbeeld `${{CDN_EDGEKEY_031426}}`.

```
experimental_authentication:
  authenticators:
    - name: edge-auth
      type: edge
      edgeKey2: ${{CDN_EDGEKEY_041425}}
      edgeKey1: ${{CDN_EDGEKEY_031426}}
```
