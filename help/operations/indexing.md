---
title: Inhoud zoeken en indexeren
description: Inhoud zoeken en indexeren
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: ac7e4f7d7b771c392d8f67bd0751dfeede970a5f
workflow-type: tm+mt
source-wordcount: '2246'
ht-degree: 1%

---

# Inhoud zoeken en indexeren {#indexing}

## Wijzigingen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM as a Cloud Service, beweegt Adobe zich weg van een AEM instantie-centric model aan een op dienst-gebaseerde mening met n-x AEM Containers, die door CI/CD pijpleidingen in de Manager van de Wolk wordt gedreven. In plaats van het vormen van en het handhaven van Indexen op enige AEM instanties, moet de configuratie van de Index vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie zijn duidelijk het beleid van CI/CD breken. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als niet nader aangegeven, getest en opnieuw geïndexeerd voordat deze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. De gebruikers zullen geen toegang tot de Manager van de Index van één enkele AEMInstantie hebben om het indexeren te zuiveren, te vormen of te handhaven. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.

1. De gebruikers zullen geen Indexen op één enkel AEMInstantie veranderen noch zullen zij zich over consistentiecontroles of het opnieuw indexeren meer moeten ongerust maken.

1. Over het algemeen worden indexwijzigingen doorgevoerd voordat naar de productie wordt gegaan om kwaliteitsgateways in de CBI/CD-leidingen van de Cloud Manager niet te omzeilen en geen invloed te hebben op de KPI&#39;s van de Business.

1. Alle verwante metriek met inbegrip van onderzoeksprestaties in productie zal voor klanten bij runtime beschikbaar zijn om de holistische mening over de onderwerpen van Onderzoek en het Indexeren te verstrekken.

1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.

1. SRE&#39;s bewaken de systeemgezondheid 24/7 en zullen zo nodig en zo vroeg mogelijk actie ondernemen.

1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.

1. Op hoog niveau voor AEM as a Cloud Service, met de invoering van de [Blauw-groen implementatiemodel](#index-management-using-blue-green-deployments) er zullen twee indexen bestaan : één set voor de oude versie (blauw) en één set voor de nieuwe versie (groen).

1. Klanten kunnen zien of de indexeertaak is voltooid op de pagina voor het samenstellen van de cloud Manager en ontvangen een melding wanneer de nieuwe versie gereed is voor verkeer.

1. Beperkingen:
* Indexbeheer op AEM as a Cloud Service wordt momenteel alleen ondersteund voor indexen van het type `lucene`.
* Alleen standaardanalysatoren worden ondersteund (dat wil zeggen die welke met het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.
* Intern, zouden andere indexen voor vragen kunnen worden gevormd en worden gebruikt. Bijvoorbeeld, vragen die tegen `damAssetLucene` De index zou, op Skyline, in feite tegen een versie van Elasticsearch van deze index kunnen worden uitgevoerd. Dit verschil is doorgaans niet zichtbaar voor de toepassing en de gebruiker, maar bepaalde gereedschappen, zoals de `explain` Deze functie rapporteert een andere index. Voor verschillen tussen Lucene-indexen en Elastic-indexen raadpleegt u [de Elastic documentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten hoeven en kunnen Elasticsearch-indexen niet rechtstreeks configureren.

## Het gebruik {#how-to-use}

Het definiëren van indexen kan uit deze drie gebruiksgevallen bestaan:

1. Het toevoegen van een nieuwe definitie van de klantenindex.
1. Een bestaande indexdefinitie bijwerken. In feite betekent dit dat een nieuwe versie van een bestaande indexdefinitie moet worden toegevoegd.
1. Verwijderen van een bestaande index die overbodig of verouderd is.

Voor zowel de punten 1 als 2 hierboven moet u een nieuwe indexdefinitie maken als onderdeel van uw aangepaste codebasis in het respectievelijke releaseprogramma voor Cloud Manager. Zie voor meer informatie de [Distribueren naar AEM as a Cloud Service documentatie](/help/implementing/deploying/overview.md).

## Indexnamen {#index-names}

Een indexdefinitie kan zijn:

1. Een index die buiten het vak valt. Eén voorbeeld is `/oak:index/cqPageLucene-2`.
1. Een aanpassing van een index die buiten het vak valt. Dergelijke aanpassingen worden bepaald door de klant. Eén voorbeeld is `/oak:index/cqPageLucene-2-custom-1`.
1. Een volledig aangepaste index. Eén voorbeeld is `/oak:index/acme.product-1-custom-2`. Om het noemen van botsingen te vermijden, vereisen wij dat de volledig douaneindexen een prefix hebben, bijvoorbeeld: `acme.`

Merk op dat zowel de aanpassing van een uit-van-de-doos index, als volledig douaneindexen, moet bevatten `-custom-`. Alleen volledig aangepaste indexen moeten beginnen met een voorvoegsel.

## De nieuwe indexdefinitie voorbereiden {#preparing-the-new-index-definition}

>[!NOTE]
>
>Als u een index buiten het vak aanpast, bijvoorbeeld `damAssetLucene-6`, kopieer de meest recente out-of-box-indexdefinitie van een *Cloud Service* met behulp van CRX DE Package Manager (`/crx/packmgr/`). Wijzig vervolgens de naam van de configuratie, bijvoorbeeld `damAssetLucene-6-custom-1`en voeg uw aanpassingen bovenaan toe. Dit zorgt ervoor dat de vereiste configuraties niet per ongeluk worden verwijderd. De `tika` knooppunt onder `/oak:index/damAssetLucene-6/tika` is vereist in de aangepaste index van de cloudservice. Het bestaat niet op de Cloud SDK.

U moet een nieuw indexdefinitiepakket voorbereiden dat de daadwerkelijke indexdefinitie bevat, die dit noemingspatroon volgt:

`<indexName>[-<productVersion>]-custom-<customVersion>`

die dan nog verder moeten `ui.apps/src/main/content/jcr_root`. Alle aangepaste en aangepaste indexdefinities moeten onder `/oak:index`.

Het filter voor het pakket moet zo worden ingesteld dat bestaande indexen (out-of-the-box) behouden blijven. In het bestand `ui.apps/src/main/content/META-INF/vault/filter.xml`moet elke aangepaste (of aangepaste) index worden vermeld, bijvoorbeeld `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. Als de indexversie later wordt gewijzigd, moet het filter worden aangepast.

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Voor elk inhoudspakket met indexdefinities moet de volgende eigenschap zijn ingesteld in het eigenschappenbestand van het inhoudspakket, dat zich bevindt op `/META-INF/vault/properties.xml`:
>
>`noIntermediateSaves=true`

## Indexdefinities implementeren {#deploying-index-definitions}

Indexdefinities zijn gemarkeerd als aangepast en versieingesteld:

* De indexdefinitie zelf (bijvoorbeeld `/oak:index/ntBaseLucene-custom-1`)

Als u een aangepaste of aangepaste index wilt implementeren, wordt de indexdefinitie (`/oak:index/definitionname`) moet worden geleverd via `ui.apps` via Git en het implementatieproces van Cloud Manager. In het filter FileVault bijvoorbeeld: `ui.apps/src/main/content/META-INF/vault/filter.xml`elke aangepaste en aangepaste index afzonderlijk vermelden, bijvoorbeeld `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. De aangepaste/aangepaste indexdefinitie zelf wordt vervolgens opgeslagen in het bestand `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`, als volgt:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:oak="https://jackrabbit.apache.org/oak/ns/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:rep="internal"
        jcr:primaryType="oak:QueryIndexDefinition"
        async="[async,nrt]"
        compatVersion="{Long}2"
        ...
        </indexRules>
        <tika jcr:primaryType="nt:unstructured">
            <config.xml jcr:primaryType="nt:file"/>
        </tika>
</jcr:root>
```

Het bovenstaande voorbeeld bevat een configuratie voor Apache Tika. Het Tika-configuratiebestand wordt opgeslagen onder `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/tika/config.xml`.

### Projectconfiguratie

Afhankelijk van welke versie van de Insteekmodule van het Pakket wordt gebruikt Van het Bestandsindeling van het Pakket van het Jasrabbit wordt Maven, wordt wat meer configuratie in het project vereist. Bij gebruik van de insteekmodule Jackrabbit FileVult Maven Package **1.1.6.** of hoger, dan het bestand `pom.xml` moet de volgende sectie in plug-inconfiguratie bevatten voor de `filevault-package-maven-plugin`, in `configuration/validatorsSettings` (net voor `jackrabbit-nodetypes`):

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

In dit geval geldt ook het `vault-validation` De versie moet worden bijgewerkt naar een nieuwere versie:

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

Dan, binnen `ui.apps.structure/pom.xml` en `ui.apps/pom.xml`, de configuratie van de `filevault-package-maven-plugin` moet `allowIndexDefinitions` alsmede `noIntermediateSaves` ingeschakeld. De optie `noIntermediateSaves` zorgt ervoor dat de indexconfiguraties automatisch worden toegevoegd.

```xml
<groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <properties>
            <cloudManagerTarget>none</cloudManagerTarget>
            <noIntermediateSaves>true</noIntermediateSaves>
        </properties>
    ...
```

In `ui.apps.structure/pom.xml`de `filters` voor deze insteekmodule moet als volgt een filterhoofdmap bevatten:

```xml
<filter><root>/oak:index</root></filter>
```

Nadat de nieuwe indexdefinitie is toegevoegd, moet de nieuwe toepassing worden geïmplementeerd via Cloud Manager. Na de implementatie worden twee taken gestart, die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. De onderliggende repository&#39;s worden opnieuw gedestilleerd met de nieuwe indexdefinities, voordat de Blauw-Groen omschakeling plaatsvindt.

>[!TIP]
>
>Zie het document voor meer informatie over de vereiste pakketstructuur voor AEM as a Cloud Service [AEM projectstructuur.](/help/implementing/developing/introduction/aem-project-content-package-structure.md)

## Indexbeheer met Blauw-groene implementaties {#index-management-using-blue-green-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het wijzigen van *definitie* van een index is snel, maar het toepassen van de wijziging (vaak &#39;&#39;een index samenstellen&#39;&#39; genoemd, of, voor bestaande indexen, &#39;&#39;opnieuw indexeren&#39;&#39;) vereist tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet worden gescand om de gegevens te indexeren.

### Wat is een blauw-groene implementatie {#what-is-blue-green-deployment}

Met blauw-groene implementatie kunt u downtime verminderen. Het staat ook voor nul downtime verbeteringen toe en verstrekt snelle terugdraaiversies. De oude versie van de toepassing (blauw) wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd (groen).

### Alleen-lezen en Gebieden lezen/schrijven {#read-only-and-read-write-areas}

Bepaalde delen van de opslagplaats (alleen-lezen onderdelen van de opslagplaats) kunnen verschillend zijn in de oude (blauwe) en de nieuwe (groene) versie van de toepassing. De gebieden met het kenmerk Alleen-lezen in de gegevensopslagruimte zijn doorgaans &quot;`/app`&quot; en &quot;`/libs`&quot;. In het volgende voorbeeld wordt cursief gebruikt voor het markeren van alleen-lezen gebieden, terwijl vet wordt gebruikt voor lezen-schrijven gebieden.

* **/**
* */apps (alleen-lezen)*
* **/content**
* */libs (alleen-lezen)*
* **/oak:index**
* **/oak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

De read-write gebieden van de bewaarplaats worden gedeeld tussen alle versies van de toepassing, terwijl voor elke versie van de toepassing, er een specifieke reeks is van `/apps` en `/libs`.

### Indexbeheer zonder blauw-groene implementatie {#index-management-without-blue-green-deployment}

Tijdens de ontwikkeling, of wanneer het gebruiken op gebouwinstallaties, kunnen indexen worden toegevoegd, worden verwijderd, of bij runtime worden veranderd. Indexen worden gebruikt zodra ze beschikbaar zijn. Als een index nog niet in de oude versie van de toepassing moet worden gebruikt, dan wordt de index typisch gebouwd tijdens een geplande onderbreking. Hetzelfde geldt wanneer u een index verwijdert of een bestaande index wijzigt. Wanneer u een index verwijdert, wordt deze niet meer beschikbaar zodra deze wordt verwijderd.

### Indexbeheer met blauw-groene implementatie {#index-management-with-blue-green-deployment}

Met blauwgroene implementaties is er geen downtime. Tijdens een upgrade worden gedurende enige tijd zowel de oude versie (bijvoorbeeld versie 1) van de toepassing als de nieuwe versie (versie 2) tegelijk uitgevoerd tegen dezelfde opslagplaats. Als voor versie 1 een bepaalde index beschikbaar moet zijn, mag deze index niet worden verwijderd in versie 2: de index moet later worden verwijderd, bijvoorbeeld in versie 3, waarna gegarandeerd is dat versie 1 van de toepassing niet meer wordt uitgevoerd. Ook, zouden de toepassingen zodanig moeten worden geschreven dat versie 1 goed werkt, zelfs als versie 2 loopt, en als de indexen van versie 2 beschikbaar zijn.

Nadat de upgrade naar de nieuwe versie is voltooid, kunnen oude indexen door het systeem worden opgeschoond. De oude indexen blijven misschien nog een tijdje, om terugdraaiversies te versnellen (als een terugdraaiing nodig zou moeten zijn).

In de volgende tabel staan vijf indexdefinities: index `cqPageLucene` wordt gebruikt in beide versies terwijl index `damAssetLucene-custom-1` wordt alleen gebruikt in versie 2.

>[!NOTE]
>
>`<indexName>-custom-<customerVersionNumber>` is nodig voor AEM as a Cloud Service om dit te markeren als een vervanging voor een bestaande index.

| Index | Index van out-of-the-box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eak:index/damAssetLucene | Ja | Ja | Nee |
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Nee | Ja |
| /oak:index/acme.product-custom-1 | Nee | Ja | Nee |
| /oak:index/acme.product-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Als u wilt voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen van het vak eindigen met `-custom-<number>`.

### Wijzigingen in indexen buiten de box {#changes-to-out-of-the-box-indexes}

Zodra Adobe een out-of-the-box index zoals &quot;damAssetLucene&quot; of &quot;cqPageLucene&quot; verandert, een nieuwe index genoemd `damAssetLucene-2` of `cqPageLucene-2` wordt gemaakt, of als de index al is aangepast, wordt de aangepaste indexdefinitie samengevoegd met de wijzigingen in de index voor de uitverkochte items, zoals hieronder wordt weergegeven. Wijzigingen worden automatisch samengevoegd. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen.

| Index | Index van out-of-the-box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

### Huidige beperkingen {#current-limitations}

Indexbeheer wordt momenteel alleen ondersteund voor indexen van het type `lucene`. Intern, zouden andere indexen voor vragen, bijvoorbeeld elastische indexen kunnen worden gevormd en worden gebruikt.

### Een index toevoegen {#adding-an-index}

Een volledig aangepaste index toevoegen met de naam `/oak:index/acme.product-custom-1` om in een nieuwe versie van de toepassing en later te worden gebruikt, moet de index als volgt worden gevormd:

`acme.product-1-custom-1`

Dit werkt door een aangepaste id vooraf op de indexnaam in te stellen, gevolgd door een punt (**`.`**). De id moet minimaal 2 en maximaal 5 tekens lang zijn.

Zoals hierboven, verzekert dit dat de index slechts door de nieuwe versie van de toepassing wordt gebruikt.

### Index wijzigen {#changing-an-index}

Wanneer een bestaande index wordt gewijzigd, moet een nieuwe index met de gewijzigde indexdefinitie worden toegevoegd. Neem bijvoorbeeld de bestaande index `/oak:index/acme.product-custom-1` is gewijzigd. De oude index is opgeslagen onder `/oak:index/acme.product-custom-1`en de nieuwe index wordt opgeslagen onder `/oak:index/acme.product-custom-2`.

De oude versie van de toepassing gebruikt de volgende configuratie:

`/oak:index/acme.product-custom-1`

De nieuwe versie van de toepassing gebruikt de volgende (veranderde) configuratie:

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Indexdefinities op AEM as a Cloud Service komen mogelijk niet volledig overeen met de indexdefinities op een lokale ontwikkelingsinstantie. De ontwikkelingsinstantie heeft geen configuratie Tika, terwijl AEM as a Cloud Service instanties één hebben. Als u een index met een configuratie van de Tika aanpast, gelieve de configuratie van de Tika te behouden.

### Een wijziging ongedaan maken {#undoing-a-change}

Soms moet een wijziging in een indexdefinitie worden teruggedraaid. De reden hiervoor zou kunnen zijn dat er een wijziging is gemaakt of dat er niet langer een wijziging nodig is. De indexdefinitie `damAssetLucene-8-custom-3` is bij vergissing gemaakt en is al geïmplementeerd. Hierdoor kunt u terugkeren naar de vorige indexdefinitie `damAssetLucene-8-custom-2`. Hiervoor moet u een nieuwe index toevoegen met de naam `damAssetLucene-8-custom-4` die de definitie van de vorige index bevat, `damAssetLucene-8-custom-2`.

### Een index verwijderen {#removing-an-index}

Het volgende is alleen van toepassing op aangepaste indexen. Productindexen kunnen niet worden verwijderd omdat ze door AEM worden gebruikt.

Als een index in een recentere versie van de toepassing moet worden verwijderd, kunt u een lege index (een lege index bepalen die nooit wordt gebruikt, en geen gegevens bevat), met een nieuwe naam. In dit voorbeeld kunt u het een naam geven `/oak:index/acme.product-custom-3`. Hiermee wordt de index vervangen `/oak:index/acme.product-custom-2`. Eenmaal `/oak:index/acme.product-custom-2` wordt verwijderd door het systeem, de lege index `/oak:index/acme.product-custom-3` kan vervolgens ook worden verwijderd. Een voorbeeld van een dergelijke lege index is:

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

Als het niet meer nodig is om een uit-van-de-doos index te hebben, dan moet u de uit-van-de-doos indexdefinitie kopiëren. Als u bijvoorbeeld al hebt geïmplementeerd `damAssetLucene-8-custom-3`, maar u hebt de aanpassingen niet meer nodig en u wilt terugschakelen naar de standaardinstelling `damAssetLucene-8` index, dan moet u een index toevoegen `damAssetLucene-8-custom-4` die de indexdefinitie van `damAssetLucene-8`.

## Optimalisatie van index en query {#index-query-optimizations}

Apache Jackrabbit Oak maakt flexibele indexconfiguraties mogelijk om zoekopdrachten efficiënt af te handelen. Indexen zijn vooral belangrijk voor grotere opslagplaatsen. Controleer of alle query&#39;s worden ondersteund door een geschikte index. De vragen zonder een geschikte index kunnen duizenden knopen lezen, die dan als waarschuwing wordt geregistreerd.

Zie [dit document](query-and-indexing-best-practices.md) voor informatie over hoe vragen en indexen kunnen worden geoptimaliseerd.
