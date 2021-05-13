---
title: Inhoud zoeken en indexeren
description: Inhoud zoeken en indexeren
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 16afabcd80f9014684a5d3428a65d8b2c41c69c8
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 2%

---

# Inhoud zoeken en indexeren {#indexing}

## Wijzigingen in AEM als Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM als Cloud Service, beweegt Adobe zich van een AEM instantie-centric model aan een op dienst-gebaseerde mening met n-x AEM Containers, die door pijpleidingen CI/CD in de Manager van de Wolk wordt gedreven. In plaats van het vormen van en het handhaven van Indexen op enige AEM instanties, moet de configuratie van de Index vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie zijn duidelijk het beleid van CI/CD breken. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als niet nader aangegeven, getest en opnieuw geïndexeerd voordat deze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. De gebruikers zullen geen toegang tot de Manager van de Index van één enkele AEMInstantie hebben om het indexeren te zuiveren, te vormen of te handhaven. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.

1. De gebruikers zullen geen Indexen op één enkel AEMInstantie veranderen noch zullen zij zich over consistentiecontroles of het opnieuw indexeren meer moeten ongerust maken.

1. Over het algemeen worden indexwijzigingen doorgevoerd voordat naar de productie wordt gegaan om kwaliteitsgateways in de CBI/CD-leidingen van de Cloud Manager niet te omzeilen en geen invloed te hebben op de KPI&#39;s van de Business.

1. Alle verwante metriek met inbegrip van onderzoeksprestaties in productie zal voor klanten bij runtime beschikbaar zijn om de holistische mening over de onderwerpen van Onderzoek en het Indexeren te verstrekken.

1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.

1. SRE&#39;s bewaken de systeemgezondheid 24/7 en zullen zo nodig en zo vroeg mogelijk actie ondernemen.

1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.

1. Op een hoog niveau voor AEM als Cloud Service, met de introductie van het [Blauw-Groen plaatsingsmodel](#index-management-using-blue-green-deployments) zullen twee reeksen indexen bestaan: één set voor de oude versie (blauw) en één set voor de nieuwe versie (groen).

1. Klanten kunnen zien of de indexeertaak is voltooid op de pagina voor het samenstellen van de cloud Manager en ontvangen een melding wanneer de nieuwe versie gereed is voor verkeer.

1. Beperkingen: momenteel, wordt het indexbeheer op AEM als Cloud Service slechts gesteund voor indexen van type lucene.

## Het gebruik {#how-to-use}

Het definiëren van indexen kan uit deze drie gebruiksgevallen bestaan:

1. Een nieuwe klantindexdefinitie toevoegen
1. Een bestaande indexdefinitie bijwerken. Dit betekent in feite dat een nieuwe versie van een bestaande indexdefinitie moet worden toegevoegd
1. Verwijderen van een bestaande index die overbodig of verouderd is.

Voor zowel de punten 1 als 2 hierboven moet u een nieuwe indexdefinitie maken als onderdeel van uw aangepaste codebasis in het respectievelijke releaseprogramma voor Cloud Manager. Voor meer informatie, zie [het Opstellen aan AEM als documentatie van de Cloud Service](/help/implementing/deploying/overview.md).

### De nieuwe indexdefinitie {#preparing-the-new-index-definition} voorbereiden

>[!NOTE]
>
>Als u een uitpunt van de vakindex aanpast, bijvoorbeeld `damAssetLucene-6`, kopieert u de meest recente uit de definitie van de kaderindex van een *Cloud Service-omgeving* en voegt u uw aanpassingen bovenaan toe, zodat de vereiste configuraties niet per ongeluk worden verwijderd. Het knooppunt `tika` onder `/oak:index/damAssetLucene-6/tika` is bijvoorbeeld een vereist knooppunt en moet ook deel uitmaken van uw aangepaste index en het bestaat niet in de Cloud SDK.

U moet een nieuw indexdefinitiepakket voorbereiden dat de daadwerkelijke indexdefinitie bevat, die dit noemingspatroon volgt:

`<indexName>[-<productVersion>]-custom-<customVersion>`

die dan onder `ui.apps/src/main/content/jcr_root` moeten gaan. Subhoofdmappen worden op dit moment niet ondersteund.

Het pakket uit het bovenstaande voorbeeld is opgebouwd als `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`.

>[!NOTE]
>
>Voor elk inhoudspakket met indexdefinities moet de volgende eigenschap zijn ingesteld in het eigenschappenbestand van het inhoudspakket, dat zich bevindt op `/META-INF/vault/properties.xml`:
>
>`noIntermediateSaves=true`

### Indexdefinities {#deploying-index-definitions} implementeren

>[!NOTE]
>
>Er is een bekend probleem met de Versie **1.1.0** van de Plug-in `<packageType>application</packageType>`Pakket met hemrabbit FileVult, waarmee u `oak:index` niet kunt toevoegen aan modules van . Om dit te omzeilen, gelieve versie **1.0.4** te gebruiken.

Indexdefinities zijn nu gemarkeerd als aangepast en versieingesteld:

* De indexdefinitie zelf (bijvoorbeeld `/oak:index/ntBaseLucene-custom-1`)

Om een index te kunnen implementeren, moet de indexdefinitie (`/oak:index/definitionname`) daarom via Git en het implementatieproces van Cloud Manager worden geleverd.`ui.apps`

Nadat de nieuwe indexdefinitie is toegevoegd, moet de nieuwe toepassing worden geïmplementeerd via Cloud Manager. Na de implementatie worden twee taken gestart, die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. De onderliggende repository&#39;s worden opnieuw gedestilleerd met de nieuwe indexdefinities, voordat de Blauw-Groen omschakeling plaatsvindt.

>[!TIP]
>
>Zie het document [Projectstructuur AEM voor meer informatie over de vereiste pakketstructuur voor AEM als Cloud Service.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## Indexbeheer met Blauw-groene implementaties {#index-management-using-blue-green-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het wijzigen van de *definitie* van een index is snel, maar het toepassen van de wijziging (vaak &quot;een index bouwen&quot; genoemd, of, voor bestaande indexen, &quot;opnieuw indexeren&quot;) vereist tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet worden gescand om de gegevens te indexeren.

### Wat is een blauw-groene implementatie {#what-is-blue-green-deployment}

Met blauw-groene implementatie kunt u downtime verminderen. Het staat ook voor nul downtime verbeteringen toe en verstrekt snelle terugdraaiversies. De oude versie van de toepassing (blauw) wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd (groen).

### Alleen-lezen en lezen-schrijven gebieden {#read-only-and-read-write-areas}

Bepaalde delen van de opslagplaats (alleen-lezen onderdelen van de opslagplaats) kunnen verschillend zijn in de oude (blauwe) en de nieuwe (groene) versie van de toepassing. De gebieden met het kenmerk Alleen-lezen van de gegevensopslagruimte zijn doorgaans &quot;`/app`&quot; en &quot;`/libs`&quot;. In het volgende voorbeeld wordt cursief gebruikt voor het markeren van alleen-lezen gebieden, terwijl vet wordt gebruikt voor lezen-schrijven gebieden.

* **/**
* */apps (alleen-lezen)*
* **/content**
* */libs (alleen-lezen)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

De lees-schrijf gebieden van de bewaarplaats worden gedeeld tussen alle versies van de toepassing, terwijl voor elke versie van de toepassing, er een specifieke reeks van `/apps` en `/libs` is.

### Indexbeheer zonder blauw-groene implementatie {#index-management-without-blue-green-deployment}

Tijdens de ontwikkeling, of wanneer het gebruiken op gebouwinstallaties, kunnen indexen worden toegevoegd, worden verwijderd, of bij runtime worden veranderd. Indexen worden gebruikt zodra ze beschikbaar zijn. Als een index nog niet in de oude versie van de toepassing moet worden gebruikt, dan wordt de index typisch gebouwd tijdens een geplande onderbreking. Hetzelfde geldt wanneer u een index verwijdert of een bestaande index wijzigt. Wanneer u een index verwijdert, wordt deze niet meer beschikbaar zodra deze wordt verwijderd.

### Indexbeheer met blauw-groene implementatie {#index-management-with-blue-green-deployment}

Met blauwgroene implementaties is er geen downtime. Voor indexbeheer is het echter vereist dat indexen alleen door bepaalde versies van de toepassing worden gebruikt. Als u bijvoorbeeld een index toevoegt in versie 2 van de toepassing, wilt u deze nog niet gebruiken in versie 1 van de toepassing. Het omgekeerde is het geval wanneer een index wordt verwijderd: een in versie 2 verwijderde index is nog steeds nodig in versie 1. Als u een indexdefinitie wijzigt, willen we dat de oude versie van de index alleen wordt gebruikt voor versie 1 en dat de nieuwe versie van de index alleen wordt gebruikt voor versie 2.

In de volgende tabel staan vijf indexdefinities: index `cqPageLucene` wordt in beide versies gebruikt terwijl index `damAssetLucene-custom-1` alleen in versie 2 wordt gebruikt.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` is nodig voor AEM als Cloud Service om dit te markeren als een vervanging voor een bestaande index.

| Index | Index van out-of-the-box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eak:index/damAssetLucene | Ja | Ja | Nee |
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Nee | Ja |
| /oak:index/acme.product-custom-1 | Nee | Ja | Nee |
| /oak:index/acme.product-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Om te voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen van het vak eindigen met `-custom-<number>`.

### Wijzigingen in indexen {#changes-to-out-of-the-box-indexes}

Zodra Adobe een uit-van-de-doos index zoals &quot;damAssetLucene&quot;of &quot;cqPageLucene&quot;verandert, wordt een nieuwe index genoemd `damAssetLucene-2` of `cqPageLucene-2` gecreeerd, of, als de index reeds werd aangepast, wordt de aangepaste indexdefinitie samengevoegd met de veranderingen in de uit-van-de-doos index, zoals hieronder getoond. Wijzigingen worden automatisch samengevoegd. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen.

| Index | Index van out-of-the-box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

### Huidige beperkingen {#current-limitations}

Indexbeheer wordt momenteel alleen ondersteund voor indexen van het type `lucene`.

### Een index {#adding-an-index} toevoegen

Als u een index met de naam `/oak:index/acme.product-custom-1` wilt toevoegen die in een nieuwe versie van de toepassing en later moet worden gebruikt, moet de index als volgt worden geconfigureerd:

`acme.product-1-custom-1`

Dit werkt door een douane herkenningsteken aan de indexnaam vooraf in te stellen, die door een punt (**`.`**) wordt gevolgd. De id moet minimaal 2 en maximaal 5 tekens lang zijn.

Zoals hierboven, verzekert dit dat de index slechts door de nieuwe versie van de toepassing wordt gebruikt.

### Een index wijzigen {#changing-an-index}

Wanneer een bestaande index wordt gewijzigd, moet een nieuwe index met de gewijzigde indexdefinitie worden toegevoegd. Stel dat de bestaande index `/oak:index/acme.product-custom-1` is gewijzigd. De oude index wordt opgeslagen onder `/oak:index/acme.product-custom-1`, en de nieuwe index wordt opgeslagen onder `/oak:index/acme.product-custom-2`.

De oude versie van de toepassing gebruikt de volgende configuratie:

`/oak:index/acme.product-custom-1`

De nieuwe versie van de toepassing gebruikt de volgende (veranderde) configuratie:

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Indexdefinities van AEM als Cloud Service komen mogelijk niet volledig overeen met de indexdefinities van een lokale ontwikkelingsinstantie. De ontwikkelingsinstantie heeft geen configuratie Tika, terwijl AEM aangezien de instanties van de Cloud Service één hebben. Als u een index met een configuratie van de Tika aanpast, gelieve de configuratie van de Tika te behouden.

### Een wijziging {#undoing-a-change} ongedaan maken

Soms moet een wijziging in een indexdefinitie worden teruggedraaid. De reden hiervoor zou kunnen zijn dat er een wijziging is gemaakt of dat er niet langer een wijziging nodig is. De indexdefinitie `damAssetLucene-8-custom-3` is bijvoorbeeld per ongeluk gemaakt en is al geïmplementeerd. Hierdoor kunt u terugkeren naar de vorige indexdefinitie `damAssetLucene-8-custom-2`. Om dat te doen, moet u een nieuwe index toevoegen genoemd `damAssetLucene-8-custom-4` die de definitie van de vorige index, `damAssetLucene-8-custom-2` bevat.

### Een index {#removing-an-index} verwijderen

Het volgende is alleen van toepassing op aangepaste indexen. Productindexen kunnen niet worden verwijderd omdat ze door AEM worden gebruikt.

Als een index in een recentere versie van de toepassing moet worden verwijderd, kunt u een lege index (een lege index bepalen die nooit wordt gebruikt, en geen gegevens bevat), met een nieuwe naam. In dit voorbeeld kunt u het `/oak:index/acme.product-custom-3` een naam geven. Hiermee wordt de index `/oak:index/acme.product-custom-2` vervangen. Nadat `/oak:index/acme.product-custom-2` door het systeem is verwijderd, kan de lege index `/oak:index/acme.product-custom-3` ook worden verwijderd. Een voorbeeld van een dergelijke lege index is:

```xml
<acme.product-custom-3
        jcr:primaryType="oak:QueryIndexDefinition"
        async="async"
        compatVersion="2"
        includedPaths="/dummy"
        queryPaths="/dummy"
        type="lucene">
        <indexRules jcr:primaryType="nt:unstructured">
            <rep:root jcr:primaryType="nt:unstructured">
                <properties jcr:primaryType="nt:unstructured">
                    <dummy
                        jcr:primaryType="nt:unstructured"
                        name="dummy"
                        propertyIndex="{Boolean}true"/>
                </properties>
            </rep:root>
        </indexRules>
    </acme.product-custom-3>
```

Als het niet meer nodig is om een uit-van-de-doos index te hebben, dan moet u de uit-van-de-doos indexdefinitie kopiëren. Als u bijvoorbeeld `damAssetLucene-8-custom-3` al hebt geïmplementeerd, maar de aanpassingen niet meer nodig hebt en wilt terugschakelen naar de standaardindex `damAssetLucene-8`, moet u een index `damAssetLucene-8-custom-4` toevoegen die de indexdefinitie van `damAssetLucene-8` bevat.

### Indexbeschikbaarheid en fouttolerantie {#index-availability-and-fault-tolerance}

Het wordt aanbevolen dubbele indexen te maken voor functies die belangrijk zijn (rekening houdend met de bovenstaande naamgevingsconventie voor indexen), zodat er in het geval van indexbeschadiging of een dergelijke onvoorziene gebeurtenis een fallback-index beschikbaar is om te reageren op query&#39;s.
