---
title: Inhoud zoeken en indexeren
description: Meer informatie over Inhoud zoeken en indexeren in AEM as a Cloud Service.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
feature: Operations
role: Admin
source-git-commit: 65e67225a6a91d871218c12c4696dd281787cd58
workflow-type: tm+mt
source-wordcount: '2449'
ht-degree: 0%

---

# Inhoud zoeken en indexeren {#indexing}

## Wijzigingen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM as a Cloud Service, beweegt de Adobe zich van een AEM instantie-centric model aan een op dienst-gebaseerde mening met n-x AEM Containers, die door CI/CD pijpleidingen in de Manager van de Wolk wordt gedreven. In plaats van het vormen van en het handhaven van Indexen op enige AEM instanties, moet de configuratie van de Index vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie zijn duidelijk het beleid van CI/CD breken. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als niet nader aangegeven, getest en opnieuw geïndexeerd voordat deze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. De gebruikers hebben geen toegang tot de Manager van de Index van één enkele AEMInstantie om, indexeren te zuiveren te vormen of te handhaven. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.
1. De gebruikers veranderen geen Indexen op één enkel AEMInstantie noch moeten zij zich over consistentiecontroles of het opnieuw indexeren meer ongerust maken.
1. Over het algemeen worden indexwijzigingen doorgevoerd voordat naar de productie wordt gegaan om kwaliteitsgateways in de CBI/CD-leidingen van de Cloud Manager niet te omzeilen en geen invloed te hebben op KPI&#39;s van bedrijven in de productie.
1. Alle verwante metriek, met inbegrip van onderzoeksprestaties in productie, is beschikbaar voor klanten bij runtime om de holistische mening over de onderwerpen van Onderzoek en het Indexeren te verstrekken.
1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.
1. SRE&#39;s controleren de systeemgezondheid 24/7 en er wordt zo snel mogelijk actie ondernomen.
1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.
1. Op hoog niveau voor AEM as a Cloud Service, met de invoering van de [implementatiemodel](#index-management-using-rolling-deployments)Er zijn twee indexen: een voor de oude versie en een voor de nieuwe versie.
1. Klanten kunnen zien of de indexeertaak is voltooid op de pagina voor het bouwen van Cloud Manager en ontvangen een melding wanneer de nieuwe versie klaar is om verkeer te nemen.

Beperkingen:

* Indexbeheer op AEM as a Cloud Service wordt momenteel alleen ondersteund voor indexen van het type `lucene`.
* Alleen standaardanalysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.
* Intern, zouden andere indexen voor vragen kunnen worden gevormd en worden gebruikt. Bijvoorbeeld, vragen die tegen `damAssetLucene` De index zou, op Skyline, in feite tegen een versie van de Elasticsearch van deze index kunnen worden uitgevoerd. Dit verschil is doorgaans niet zichtbaar voor de toepassing en de gebruiker, maar voor bepaalde gereedschappen, zoals de `explain` een andere index rapporteren. Voor verschillen tussen Lucene-indexen en Elastic-indexen raadpleegt u [de Elastic documentation in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten hoeven en kunnen Elasticsearch-indexen niet rechtstreeks configureren.
* Zoeken op vergelijkbare vakvectoren (`useInSimilarity = true`) wordt niet ondersteund.

>[!TIP]
>
>Voor meer informatie over de indexering en de Vragen van het Eak, met inbegrip van een gedetailleerde beschrijving van geavanceerde onderzoek en het indexeren eigenschappen, zie [Documentatie voor Apache Oak](https://jackrabbit.apache.org/oak/docs/query/query.html).


## Hoe wordt het gebruikt {#how-to-use}

Indexdefinities kunnen als volgt in drie gevallen van primair gebruik worden ingedeeld:

1. **Toevoegen** een nieuwe aangepaste indexdefinitie.
2. **Bijwerken** een bestaande indexdefinitie door een nieuwe versie toe te voegen.
3. **Verwijderen** een indexdefinitie die niet meer nodig is.

Voor zowel de punten 1 als 2 hierboven moet u een indexdefinitie maken als onderdeel van uw aangepaste codebasis in het respectievelijke releaseprogramma voor Cloud Manager. Zie de klasse [Distribueren naar AEM as a Cloud Service](/help/implementing/deploying/overview.md) documentatie.

## Indexnamen {#index-names}

Een indexdefinitie kan in één van de volgende categorieën vallen:

1. De OOTB-index (Out-of-the-box). Bijvoorbeeld: `/oak:index/cqPageLucene-2` of `/oak:index/damAssetLucene-8`.

2. Aanpassing van een OOTB-index. Deze worden aangegeven door toevoegen `-custom-` gevolgd door een numerieke id van de oorspronkelijke indexnaam. Bijvoorbeeld: `/oak:index/damAssetLucene-8-custom-1`.

3. Volledig aangepaste index: het is mogelijk een geheel nieuwe geheel nieuwe index te maken. Hun naam moet een voorvoegsel hebben om naamconflicten te voorkomen. Bijvoorbeeld: `/oak:index/acme.product-1-custom-2`, waarbij het voorvoegsel `acme.`

>[!NOTE]
>
>Nieuwe indexen introduceren op de `dam:Asset` nodetype (in het bijzonder fulltext-indexen) wordt sterk afgeraden, omdat deze in conflict kunnen komen met OOTB-productkenmerken, wat kan leiden tot functionele en prestatieproblemen. In het algemeen voegt u aanvullende eigenschappen toe aan de huidige `damAssetLucene-*` indexversie is de meest geschikte manier om query&#39;s te indexeren op de `dam:Asset` nodetype (deze wijzigingen worden automatisch samengevoegd in een nieuwe productversie van de index als deze daarna wordt vrijgegeven). In geval van twijfel kunt u contact opnemen met de Adobe Support voor advies.

## De nieuwe indexdefinitie voorbereiden {#preparing-the-new-index-definition}

>[!NOTE]
>
>Als u bijvoorbeeld een index buiten het vak aanpast, `damAssetLucene-8`, kopieert u de meest recente out-of-box-indexdefinitie van een *Cloud Service* met behulp van CRX DE Package Manager (`/crx/packmgr/`). Naam wijzigen in `damAssetLucene-8-custom-1` (of hoger) en voeg uw aanpassingen toe in het XML-bestand. Dit zorgt ervoor dat de vereiste configuraties niet per ongeluk worden verwijderd. Bijvoorbeeld de `tika` knooppunt onder `/oak:index/damAssetLucene-8/tika` is vereist in de aangepaste index die wordt geïmplementeerd in een AEM Cloud Service-omgeving, maar niet in de lokale AEM SDK.

Maak voor aanpassingen van een OOTB-index een nieuw pakket met de feitelijke indexdefinitie die volgt op dit naamgevingspatroon:

`<indexName>-<productVersion>-custom-<customVersion>`

Voor een volledig aangepaste index bereidt u een nieuw indexdefinitiepakket voor dat de indexdefinitie bevat die volgt op dit naamgevingspatroon:

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Voor elk inhoudspakket met indexdefinities moeten de volgende eigenschappen worden ingesteld in het dialoogvenster `properties.xml` van het inhoudspakket. `properties.xml` wordt standaard gemaakt in een nieuw pakket en bevindt zich op `<package_name>/META-INF/vault/properties.xml`:
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## Aangepaste indexdefinities gebruiken {#deploying-custom-index-definitions}

Om de plaatsing van een aangepaste versie van de uit-van-doos index te illustreren `damAssetLucene-8`, zullen wij een stapsgewijze gids verstrekken. In dit voorbeeld wordt de naam gewijzigd in `damAssetLucene-8-custom-1`. Dan is het proces als volgt:

1. Maak een nieuwe map met de bijgewerkte indexnaam in het dialoogvenster `ui.apps` map:
   * Voorbeeld: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. Een configuratiebestand toevoegen `.content.xml` met de aangepaste configuraties in de gemaakte map. Hieronder ziet u een voorbeeld van een aanpassing: Bestandsnaam: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:jcr="http://www.jcp.org/jcr/1.0" xmlns:dam="http://www.day.com/dam/1.0" xmlns:nt="http://www.jcp.org/jcr/nt/1.0" xmlns:oak="http://jackrabbit.apache.org/oak/ns/1.0" xmlns:rep="internal"
       jcr:mixinTypes="[rep:AccessControllable]"
       jcr:primaryType="oak:QueryIndexDefinition"
       async="[async,nrt]"
       compatVersion="{Long}2"
       evaluatePathRestrictions="{Boolean}true"
       includedPaths="[/content/dam]"
       maxFieldLength="{Long}100000"
       type="lucene">
       <facets
           jcr:primaryType="nt:unstructured"
           secure="statistical"
           topChildren="100"/>
       <indexRules jcr:primaryType="nt:unstructured">
           <dam:Asset jcr:primaryType="nt:unstructured">
               <properties jcr:primaryType="nt:unstructured">
                   <cqTags
                       jcr:primaryType="nt:unstructured"
                       name="jcr:content/metadata/cq:tags"
                       nodeScopeIndex="{Boolean}true"
                       propertyIndex="{Boolean}true"
                       useInSpellcheck="{Boolean}true"
                       useInSuggest="{Boolean}true"/>
               </properties>
           </dam:Asset>
       </indexRules>
       <tika jcr:primaryType="nt:folder">
           <config.xml jcr:primaryType="nt:file"/>
       </tika>
   </jcr:root>
   ```

3. Voeg een item toe aan het FileVault-filter in `ui.apps/src/main/content/META-INF/vault/filter.xml`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. Voeg een configuratiebestand voor Apache Tika toe in: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml`:

   ```xml
   <properties>
       <detectors>
           <detector class="org.apache.tika.detect.TypeDetector"/>
       </detectors>
       <parsers>
           <parser class="org.apache.tika.parser.DefaultParser">
           <mime>text/plain</mime>
           </parser>
       </parsers>
       <service-loader initializableProblemHandler="ignore" dynamic="true"/>
   </properties>
   ```

5. Zorg ervoor dat uw configuratie voldoet aan de richtlijnen die zijn vermeld in het dialoogvenster [Projectconfiguratie](#project-configuration) sectie. Breng de nodige aanpassingen aan.

## Projectconfiguratie

We raden u aan versie >= te gebruiken `1.3.2` van het jasje `filevault-package-maven-plugin`. U kunt dit als volgt in uw project opnemen:

1. De versie op het hoogste niveau bijwerken `pom.xml`:

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
       ...
   </plugin>
   ```

2. Voeg het volgende toe aan het hoogste niveau `pom.xml`:

   ```xml
   <jackrabbit-packagetype>
       <options>   
           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
       </options>
   </jackrabbit-packagetype>
   ```

   Hier volgt een voorbeeld van het bovenste niveau van het project `pom.xml` dossier met de bovengenoemde configuraties omvatten:

   Bestandsnaam: `pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           ...
           <version>1.3.2</version>
           <configuration>
               ...
               <validatorsSettings>
                   <jackrabbit-packagetype>
                       <options>
                           <immutableRootNodeNames>apps,libs,oak:index</immutableRootNodeNames>
                       </options>
                   </jackrabbit-packagetype>
                   ...
               ...
   </plugin>
   ```

3. In `ui.apps/pom.xml` en `ui.apps.structure/pom.xml` het is noodzakelijk `allowIndexDefinitions` en `noIntermediateSaves` in de `filevault-package-maven-plugin`. Inschakelen `allowIndexDefinitions` staat voor aangepaste indexdefinities toe, terwijl `noIntermediateSaves` zorgt ervoor dat de configuraties automatisch worden toegevoegd.

   Bestandsnamen: `ui.apps/pom.xml` en `ui.apps.structure/pom.xml`

   ```xml
   <plugin>
       <groupId>org.apache.jackrabbit</groupId>
           <artifactId>filevault-package-maven-plugin</artifactId>
           <configuration>
               <allowIndexDefinitions>true</allowIndexDefinitions>
               <properties>
                   <cloudManagerTarget>none</cloudManagerTarget>
                   <noIntermediateSaves>true</noIntermediateSaves>
               </properties>
       ...
   </plugin>
   ```

4. Een filter toevoegen voor `/oak:index` in `ui.apps.structure/pom.xml`:

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

Nadat u de nieuwe indexdefinitie hebt toegevoegd, implementeert u de nieuwe toepassing met Cloud Manager. Deze implementatie start twee taken, die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. Vóór de omschakeling, ondergaan de onderliggende bewaarplaatsen opnieuw in overeenstemming met de bijgewerkte indexdefinities.

>[!TIP]
>
>Ga voor meer informatie over de vereiste pakketstructuur voor AEM as a Cloud Service naar [AEM projectstructuur](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexbeheer met behulp van rollende implementaties {#index-management-using-rolling-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het wijzigen van *definitie* van een index is snel, maar het toepassen van de wijziging (vaak &#39;&#39;een index samenstellen&#39;&#39; genoemd, of, voor bestaande indexen, &#39;&#39;opnieuw indexeren&#39;&#39;) vereist tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet gescand worden om de gegevens te indexeren.

### Wat zijn de Rolling Plaatsingen {#what-are-rolling-deployments}

Een rolplaatsing kan onderbreking verminderen. Het staat ook voor nul downtime verbeteringen toe en verstrekt snelle terugschroeven van prijzen. De oude versie van de toepassing wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd.

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

De volgende tabel bevat vijf indexdefinities: index `cqPageLucene` wordt gebruikt in beide versies terwijl index `damAssetLucene-custom-1` wordt alleen gebruikt in versie 2.

>[!NOTE]
>
>De `<indexName>-custom-<customerVersionNumber>` is nodig om AEM as a Cloud Service te markeren als vervanging voor een bestaande index.

| Index | Index buiten de box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eak:index/damAssetLucene | Ja | Ja | Nee |
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Nee | Ja |
| /oak:index/acme.product-custom-1 | Nee | Ja | Nee |
| /oak:index/acme.product-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Als u wilt voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen buiten het vak eindigen met `-custom-<number>`.

### Wijzigingen in indexen buiten de box {#changes-to-out-of-the-box-indexes}

Nadat de Adobe een uit-van-de-doos index zoals &quot;damAssetLucene&quot;of &quot;cqPageLucene&quot;verandert, een nieuwe index genoemd `damAssetLucene-2` of `cqPageLucene-2` wordt gemaakt. Of als de index al is aangepast, wordt de aangepaste indexdefinitie samengevoegd met de wijzigingen in de index buiten het vak, zoals hieronder wordt weergegeven. Het samenvoegen van wijzigingen gebeurt automatisch. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen.

| Index | Index buiten de box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

### Huidige beperkingen {#current-limitations}

Indexbeheer wordt alleen ondersteund voor typeindexen `lucene`, met `compatVersion` instellen op `2`. Intern, zouden andere indexen voor vragen, bijvoorbeeld, Elasticsearch indexen kunnen worden gevormd en worden gebruikt. Vragen die worden geschreven tegen de `damAssetLucene` index zou, op AEM as a Cloud Service, in feite tegen een Elasticsearch versie van deze index kunnen worden in werking gesteld. Dit verschil is onzichtbaar voor de gebruiker van de toepassing, maar bepaalde gereedschappen, zoals de `explain` deze functie rapporteert een andere index. Voor verschillen tussen indexen van Lucene en van de Elasticsearch, zie [de documentatie over de Elasticsearch in Apache Jackrabbit Oak](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten kunnen en hoeven Elasticsearch-indexen niet rechtstreeks te configureren.

Alleen ingebouwde analysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.

Voor de beste operationele prestaties, zouden de indexen niet bovenmatig groot moeten zijn. De totale grootte van alle indexen kan als richtlijn worden gebruikt. Als deze grootte na het toevoegen van aangepaste indexen met meer dan 100% toeneemt en de standaardindexen in een ontwikkelomgeving zijn aangepast, moeten de aangepaste indexdefinities worden aangepast. AEM as a Cloud Service kan de plaatsing van indexen verhinderen die de systeemstabiliteit en prestaties negatief zouden beïnvloeden.

### Een index toevoegen {#adding-an-index}

Een volledig aangepaste index toevoegen met de naam `/oak:index/acme.product-custom-1`, die in een nieuwe versie van de toepassing en later moet worden gebruikt, moet de index als volgt worden gevormd:

`acme.product-1-custom-1`

Deze configuratie werkt door een aangepaste id voor te bereiden op de indexnaam, gevolgd door een punt (**`.`**). De id moet uit 2 tot 5 tekens bestaan.

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

Soms wordt het nodig om een wijziging in een indexdefinitie ongedaan te maken. Dit kan gebeuren als er een onbedoelde fout optreedt of als de wijziging niet langer vereist is. Neem bijvoorbeeld de indexdefinitie `damAssetLucene-8-custom-3,` die per ongeluk is gecreëerd en al is ingezet. Daarom wilt u terugkeren naar de vorige indexdefinitie, `damAssetLucene-8-custom-2.` Hiervoor moet u een nieuwe index met de naam `damAssetLucene-8-custom-4` die de definitie van de vorige index omvat, `damAssetLucene-8-custom-2.`

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
