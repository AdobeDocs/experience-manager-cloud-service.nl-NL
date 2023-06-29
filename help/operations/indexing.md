---
title: Inhoud zoeken en indexeren
description: Inhoud zoeken en indexeren
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2427'
ht-degree: 0%

---

# Inhoud zoeken en indexeren {#indexing}

## Wijzigingen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM as a Cloud Service, beweegt Adobe zich weg van een AEM instantie-centric model aan een op dienst-gebaseerde mening met n-x AEM Containers, die door CI/CD pijpleidingen in de Manager van de Wolk wordt gedreven. In plaats van het vormen van en het handhaven van Indexen op enige AEM instanties, moet de configuratie van de Index vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie zijn duidelijk het beleid van CI/CD breken. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als niet nader aangegeven, getest en opnieuw geïndexeerd voordat deze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. De gebruikers hebben geen toegang tot de Manager van de Index van één enkele AEMInstantie om, indexeren te zuiveren te vormen of te handhaven. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.
1. De gebruikers veranderen geen Indexen op één enkel AEMInstantie noch moeten zij zich over consistentiecontroles of het opnieuw indexeren meer ongerust maken.
1. Over het algemeen worden indexwijzigingen doorgevoerd voordat naar de productie wordt gegaan om kwaliteitsgateways in de CBI/CD-leidingen van de Cloud Manager niet te omzeilen en geen invloed te hebben op KPI&#39;s van bedrijven in de productie.
1. Alle verwante metriek, met inbegrip van onderzoeksprestaties in productie, is beschikbaar voor klanten bij runtime om de holistische mening over de onderwerpen van Onderzoek en het Indexeren te verstrekken.
1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.
1. SRE&#39;s controleren de systeemgezondheid 24/7 en er wordt zo snel mogelijk actie ondernomen.
1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.
1. Op hoog niveau voor AEM as a Cloud Service, met de invoering van de [rolmodel](#index-management-using-rolling-deployments), bestaan er twee indexen: één voor de oude versie en één voor de nieuwe versie.
1. Klanten kunnen zien of de indexeertaak is voltooid op de pagina voor het bouwen van Cloud Manager en ontvangen een melding wanneer de nieuwe versie klaar is om verkeer te nemen.

Beperkingen:

* Indexbeheer op AEM as a Cloud Service wordt momenteel alleen ondersteund voor indexen van het type `lucene`.
* Alleen standaardanalysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.
* Intern, zouden andere indexen voor vragen kunnen worden gevormd en worden gebruikt. Bijvoorbeeld, vragen die tegen `damAssetLucene` De index zou, op Skyline, in feite tegen een versie van Elasticsearch van deze index kunnen worden uitgevoerd. Dit verschil is doorgaans niet zichtbaar voor de toepassing en de gebruiker, maar voor bepaalde gereedschappen, zoals de `explain` een andere index rapporteren. Voor verschillen tussen Lucene-indexen en Elastic-indexen raadpleegt u [de Elastic documentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten hoeven en kunnen Elasticsearch-indexen niet rechtstreeks configureren.

## Het gebruik {#how-to-use}

Het definiëren van indexen kan uit deze drie gebruiksgevallen bestaan:

1. Een definitie van de klantindex toevoegen.
1. Een bestaande indexdefinitie bijwerken. Deze update betekent in feite dat een nieuwe versie van een bestaande indexdefinitie wordt toegevoegd.
1. Verwijderen van een bestaande index die overbodig of verouderd is.

Voor zowel de punten 1 als 2 hierboven moet u een indexdefinitie maken als onderdeel van uw aangepaste codebasis in het respectievelijke releaseprogramma voor Cloud Manager. Zie voor meer informatie [Distribueren naar AEM as a Cloud Service documentatie](/help/implementing/deploying/overview.md).

## Indexnamen {#index-names}

Een indexdefinitie kan zijn:

1. Een index die buiten het vak valt. Eén voorbeeld is `/oak:index/cqPageLucene-2`.
1. Een aanpassing van een index die buiten het vak valt. Dergelijke aanpassingen worden bepaald door de klant. Eén voorbeeld is `/oak:index/cqPageLucene-2-custom-1`.
1. Een volledig aangepaste index. Eén voorbeeld is `/oak:index/acme.product-1-custom-2`. Om naamgevingsbotsingen te voorkomen, vereist Adobe dat volledig aangepaste indexen een voorvoegsel hebben, bijvoorbeeld `acme.`

Merk op dat zowel de aanpassing van een uit-van-de-doos index, als volledig douansindexen, moet bevatten `-custom-`. Alleen volledig aangepaste indexen moeten beginnen met een voorvoegsel.

## De nieuwe indexdefinitie voorbereiden {#preparing-the-new-index-definition}

>[!NOTE]
>
>Als u een index buiten het vak aanpast, bijvoorbeeld `damAssetLucene-6`, kopieert u de meest recente out-of-box-indexdefinitie van een *Cloud Service* met behulp van CRX DE Package Manager (`/crx/packmgr/`). Wijzig vervolgens de naam van de configuratie, bijvoorbeeld `damAssetLucene-6-custom-1`en voeg uw aanpassingen bovenaan toe. Dit proces zorgt ervoor dat de vereiste configuraties niet per ongeluk worden verwijderd. De `tika` knooppunt onder `/oak:index/damAssetLucene-6/tika` is vereist in de aangepaste index van de cloudservice. Deze komt niet voor in de SDK van de cloud.

Bereid een pakket van de indexdefinitie voor dat de daadwerkelijke indexdefinitie bevat, die dit noemende patroon volgt:

`<indexName>[-<productVersion>]-custom-<customVersion>`

En dan moeten we onder `ui.apps/src/main/content/jcr_root`. Alle aangepaste en aangepaste indexdefinities moeten worden opgeslagen onder `/oak:index`.

Het filter voor het pakket moet zo worden ingesteld dat bestaande indexen (out-of-the-box) behouden blijven. In het bestand `ui.apps/src/main/content/META-INF/vault/filter.xml`, moet elke aangepaste (of aangepaste) index worden vermeld, bijvoorbeeld `<filter root="/oak:index/damAssetLucene-6-custom-1"/>`. Als de indexversie later wordt gewijzigd, moet het filter worden aangepast.

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Voor elk inhoudspakket met indexdefinities moet de volgende eigenschap zijn ingesteld in het eigenschappenbestand van het inhoudspakket, op `/META-INF/vault/properties.xml`:
>
>`noIntermediateSaves=true`

## Indexdefinities implementeren {#deploying-index-definitions}

Indexdefinities zijn gemarkeerd als aangepast en versieingesteld:

* De indexdefinitie zelf (bijvoorbeeld `/oak:index/ntBaseLucene-custom-1`)

Als u een aangepaste of aangepaste index wilt implementeren, wordt de indexdefinitie (`/oak:index/definitionname`) moet worden geleverd door `ui.apps` via Git en het implementatieproces van Cloud Manager. In het filter FileVault bijvoorbeeld: `ui.apps/src/main/content/META-INF/vault/filter.xml`elke aangepaste en aangepaste index afzonderlijk vermelden, bijvoorbeeld `<filter root="/oak:index/damAssetLucene-7-custom-1"/>`. De aangepaste/aangepaste indexdefinitie zelf wordt opgeslagen in het bestand `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-7-custom-1/.content.xml`, als volgt:

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

Afhankelijk van welke versie van de Insteekmodule van het Pakket wordt gebruikt Van het Bestandsindeling van het Pakket van het Jasrabbit wordt Maven, wordt wat meer configuratie in het project vereist. Bij gebruik van de insteekmodule Jackrabbit FileVult Maven Package **1.1.6.** of hoger, dan het bestand `pom.xml` moet de volgende sectie in insteekconfiguratie voor bevatten `filevault-package-maven-plugin`, in `configuration/validatorsSettings` (net voor `jackrabbit-nodetypes`):

```xml
<jackrabbit-packagetype>
    <options>
        <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
    </options>
</jackrabbit-packagetype>
```

In dit geval geldt ook het `vault-validation` versie moet worden bijgewerkt naar een nieuwere versie:

```xml
<dependency>
    <groupId>org.apache.jackrabbit.vault</groupId>
    <artifactId>vault-validation</artifactId>
    <version>3.5.6</version>
</dependency>
```

Dan, binnen `ui.apps.structure/pom.xml` en `ui.apps/pom.xml`, de configuratie van de `filevault-package-maven-plugin` moeten `allowIndexDefinitions` en `noIntermediateSaves` ingeschakeld. De optie `noIntermediateSaves` zorgt ervoor dat de indexconfiguraties automatisch worden toegevoegd.

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

In `ui.apps.structure/pom.xml`de `filters` voor deze plug-in moet als volgt een hoofdmap van het filter bevatten:

```xml
<filter><root>/oak:index</root></filter>
```

Nadat de nieuwe indexdefinitie is toegevoegd, wordt de nieuwe toepassing geïmplementeerd via Cloud Manager. Bij de implementatie worden twee taken gestart die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. De onderliggende repository&#39;s worden opnieuw gedefiniëerd met de nieuwe indexdefinities, voordat de switch-ondernemingen worden geplaatst.

### OPMERKING

Als u de volgende fout in de validatie van het bestandssysteem opmerkt <br>
`[ERROR] ValidationViolation: "jackrabbit-nodetypes: Mandatory child node missing: jcr:content [nt:base] inside node with types [nt:file]"` <br>
Vervolgens kunt u een van de volgende stappen volgen om het probleem op te lossen - <br>

1. Download het bestand naar versie 1.0.4 en voeg het volgende toe aan de pom op hoofdniveau:

```xml
<allowIndexDefinitions>true</allowIndexDefinitions>
```

Hieronder ziet u waar u de bovenstaande configuratie in de pom wilt plaatsen.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    <configuration>
        <properties>
        ...
        </properties>
        ...
        <allowIndexDefinitions>true</allowIndexDefinitions>
        <repositoryStructurePackages>
        ...
        </repositoryStructurePackages>
        <dependencies>
        ...
        </dependencies>
    </configuration>
</plugin>
```

1. Geen typevalidatie uitschakelen. Stel de volgende eigenschap in de sectie jackrabbit-nodetypes van de configuratie van de insteekmodule filevault in:

```xml
<isDisabled>true</isDisabled>
```

Hieronder ziet u waar u de bovenstaande configuratie in de pom wilt plaatsen.

```xml
<plugin>
    <groupId>org.apache.jackrabbit</groupId>
    <artifactId>filevault-package-maven-plugin</artifactId>
    ...
    <configuration>
    ...
        <validatorsSettings>
        ...
            <jackrabbit-nodetypes>
                <isDisabled>true</isDisabled>
            </jackrabbit-nodetypes>
        </validatorsSettings>
    </configuration>
</plugin>
```

>[!TIP]
>
>Zie het document voor meer informatie over de vereiste pakketstructuur voor AEM as a Cloud Service [AEM projectstructuur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexbeheer met behulp van rollende implementaties {#index-management-using-rolling-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het wijzigen van *definitie* van een index is snel, maar het toepassen van de wijziging (vaak &#39;&#39;een index samenstellen&#39;&#39; genoemd, of, voor bestaande indexen, &#39;&#39;opnieuw indexeren&#39;&#39;) vereist tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet gescand worden om de gegevens te indexeren.

### Wat zijn de Rolling Plaatsingen {#what-are-rolling-deployments}

Een rolplaatsing kan onderbreking verminderen. Het staat ook voor nul downtime verbeteringen toe en verstrekt snelle terugdraaiversies. De oude versie van de toepassing wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd.

### Alleen-lezen en Gebieden lezen/schrijven {#read-only-and-read-write-areas}

Bepaalde delen van de opslagplaats (alleen-lezen onderdelen van de opslagplaats) kunnen verschillend zijn in de oude en de nieuwe versie van de toepassing. De gebieden met het kenmerk Alleen-lezen van de gegevensopslagruimte zijn doorgaans `/app` en `/libs`. In het volgende voorbeeld wordt cursief gebruikt voor het markeren van alleen-lezen gebieden, terwijl vet wordt gebruikt voor lezen-schrijven gebieden.

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

### Indexbeheer zonder doorlopende implementaties {#index-management-without-rolling-deployments}

Tijdens de ontwikkeling, of wanneer het gebruiken van installaties op-gebouw, kunnen de indexen worden toegevoegd, worden verwijderd, of bij runtime worden veranderd. Indexen worden gebruikt wanneer ze beschikbaar zijn. Als een index nog niet in de oude versie van de toepassing wordt gebruikt, dan wordt de index typisch gebouwd tijdens een geplande onderbreking. Hetzelfde geldt wanneer u een index verwijdert of een bestaande index wijzigt. Wanneer u een index verwijdert, is deze niet meer beschikbaar wanneer u de index verwijdert.

### Indexbeheer met doorlopende implementaties {#index-management-with-rolling-deployments}

Met het rollen plaatsingen, is er geen onderbreking. Gedurende een update worden zowel de oude versie (bijvoorbeeld versie 1) van de toepassing als de nieuwe versie (versie 2) tegelijkertijd uitgevoerd op dezelfde opslagplaats. Als voor versie 1 een bepaalde index beschikbaar moet zijn, mag deze index niet worden verwijderd in versie 2. De index moet later worden verwijderd, bijvoorbeeld in versie 3, waarna gegarandeerd is dat versie 1 van de toepassing niet meer wordt uitgevoerd. Ook, zouden de toepassingen zodanig moeten worden geschreven dat versie 1 goed werkt, zelfs als versie 2 loopt, en als de indexen van versie 2 beschikbaar zijn.

Nadat de upgrade naar de nieuwe versie is voltooid, kunnen oude indexen door het systeem worden opgeschoond. De oude indexen blijven misschien nog een tijdje, om terugdraaiversies te versnellen (als een terugdraaiing nodig zou moeten zijn).

In de volgende tabel staan vijf indexdefinities: index `cqPageLucene` wordt gebruikt in beide versies terwijl index `damAssetLucene-custom-1` wordt alleen gebruikt in versie 2.

>[!NOTE]
>
>De `<indexName>-custom-<customerVersionNumber>` is nodig om AEM as a Cloud Service te markeren als vervanging voor een bestaande index.

| Index | Index van out-of-the-box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eak:index/damAssetLucene | Ja | Ja | Nee |
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Nee | Ja |
| /oak:index/acme.product-custom-1 | Nee | Ja | Nee |
| /oak:index/acme.product-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Als u wilt voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen buiten het vak eindigen met `-custom-<number>`.

### Wijzigingen in indexen buiten de box {#changes-to-out-of-the-box-indexes}

Nadat Adobe een out-of-the-box index zoals &quot;damAssetLucene&quot; of &quot;cqPageLucene&quot; verandert, een nieuwe index genoemd `damAssetLucene-2` of `cqPageLucene-2` wordt gemaakt. Of als de index al is aangepast, wordt de aangepaste indexdefinitie samengevoegd met de wijzigingen in de index buiten het vak, zoals hieronder wordt weergegeven. Wijzigingen worden automatisch samengevoegd. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen.

| Index | Index van out-of-the-box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

### Huidige beperkingen {#current-limitations}

Indexbeheer wordt alleen ondersteund voor indexen van het type `lucene`, met `compatVersion` instellen op `2`. Intern, zouden andere indexen voor vragen, bijvoorbeeld Elasticsearch indexen kunnen worden gevormd en worden gebruikt. Vragen die worden geschreven tegen de `damAssetLucene` De index kan, op AEM as a Cloud Service, in feite tegen een versie van Elasticsearch van deze index worden uitgevoerd. Dit verschil is onzichtbaar voor de eindgebruiker van de toepassing, maar bepaalde gereedschappen, zoals de `explain` deze functie rapporteert een andere index. Voor verschillen tussen indexen Lucene en Elasticsearch raadpleegt u [de Elasticsearch-documentatie in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten kunnen en hoeven Elasticsearch indexen niet direct te vormen.

Alleen ingebouwde analysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.

Voor de beste operationele prestaties, zouden de indexen niet bovenmatig groot moeten zijn. De totale grootte van alle indexen kan als richtlijn worden gebruikt. Als deze grootte na het toevoegen van aangepaste indexen met meer dan 100% toeneemt en de standaardindexen in een ontwikkelomgeving zijn aangepast, moeten de aangepaste indexdefinities worden aangepast. AEM as a Cloud Service kan de plaatsing van indexen verhinderen die de systeemstabiliteit en prestaties negatief zouden beïnvloeden.

### Een index toevoegen {#adding-an-index}

Een volledig aangepaste index toevoegen met de naam `/oak:index/acme.product-custom-1`, die in een nieuwe versie van de toepassing en later moet worden gebruikt, moet de index als volgt worden gevormd:

`acme.product-1-custom-1`

Deze configuratie werkt door een aangepaste id voor te bereiden op de indexnaam, gevolgd door een punt (**`.`**). De id moet minimaal 2 en maximaal 5 tekens lang zijn.

Zoals hierboven, zorgt deze configuratie ervoor dat de index slechts door de nieuwe versie van de toepassing wordt gebruikt.

### Index wijzigen {#changing-an-index}

Wanneer een bestaande index wordt gewijzigd, moet een nieuwe index met de gewijzigde indexdefinitie worden toegevoegd. Neem bijvoorbeeld de bestaande index `/oak:index/acme.product-custom-1` is gewijzigd. De oude index is opgeslagen onder `/oak:index/acme.product-custom-1`en de nieuwe index wordt opgeslagen onder `/oak:index/acme.product-custom-2`.

De oude versie van de toepassing gebruikt de volgende configuratie:

`/oak:index/acme.product-custom-1`

De nieuwe versie van de toepassing gebruikt de volgende (veranderde) configuratie:

`/oak:index/acme.product-custom-2`

>[!NOTE]
>
>Indexdefinities op AEM as a Cloud Service komen mogelijk niet volledig overeen met de indexdefinities op een lokale ontwikkelingsinstantie. De ontwikkelingsinstantie heeft geen configuratie Tika, terwijl de instanties van AEM as a Cloud Service één hebben. Als u een index met een configuratie van de Tika aanpast, behoud de configuratie van de Tika.

### Een wijziging ongedaan maken {#undoing-a-change}

Soms moet een wijziging in een indexdefinitie worden teruggedraaid. De reden hiervoor zou kunnen zijn dat er een wijziging is gemaakt of dat er niet langer een wijziging nodig is. De indexdefinitie `damAssetLucene-8-custom-3` is bij vergissing gemaakt en is al geïmplementeerd. Hierdoor kunt u terugkeren naar de vorige indexdefinitie `damAssetLucene-8-custom-2`. Hiervoor voegt u een index met de naam `damAssetLucene-8-custom-4` die de definitie van de vorige index bevat, `damAssetLucene-8-custom-2`.

### Een index verwijderen {#removing-an-index}

Het volgende is alleen van toepassing op aangepaste indexen. Productindexen kunnen niet worden verwijderd omdat ze door AEM worden gebruikt.

Als een index in een recentere versie van de toepassing wordt verwijderd, kunt u een lege index (een lege index bepalen die nooit wordt gebruikt, en geen gegevens bevat), met een nieuwe naam. In dit voorbeeld kunt u het een naam geven `/oak:index/acme.product-custom-3`. Deze naam vervangt de index `/oak:index/acme.product-custom-2`. Na `/oak:index/acme.product-custom-2` wordt verwijderd door het systeem, de lege index `/oak:index/acme.product-custom-3` kan vervolgens worden verwijderd. Een voorbeeld van een dergelijke lege index is:

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

Apache Jackrabbit Oak maakt flexibele indexconfiguraties mogelijk om zoekopdrachten efficiënt af te handelen. Indexen zijn vooral belangrijk voor grotere opslagplaatsen. Zorg ervoor dat alle vragen door een aangewezen index worden gesteund. De vragen zonder een geschikte index kunnen duizenden knopen lezen, die dan als waarschuwing worden geregistreerd.

Zie [dit document](query-and-indexing-best-practices.md) voor informatie over hoe vragen en indexen kunnen worden geoptimaliseerd.
