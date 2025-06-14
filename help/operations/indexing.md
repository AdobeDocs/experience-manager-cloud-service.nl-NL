---
title: Inhoud zoeken en indexeren
description: Meer informatie over zoeken en indexeren van inhoud in AEM as a Cloud Service.
exl-id: 4fe5375c-1c84-44e7-9f78-1ac18fc6ea6b
feature: Operations
role: Admin
source-git-commit: 8d881caf5181e9c3cdc6dcb69f0deabc2d5eeed8
workflow-type: tm+mt
source-wordcount: '2918'
ht-degree: 0%

---

# Inhoud zoeken en indexeren {#indexing}

## Wijzigingen in AEM as a Cloud Service {#changes-in-aem-as-a-cloud-service}

Met AEM as a Cloud Service beweegt Adobe zich van een instantie-centric model van AEM naar een op dienst-gebaseerde mening met n-x AEM Containers, die door CI/CD pijpleidingen in Cloud Manager wordt aangedreven. In plaats van het vormen en het handhaven van indexen op enige instanties van AEM, moet de indexconfiguratie vóór een plaatsing worden gespecificeerd. De veranderingen van de configuratie in productie breken CI/CD beleid. Hetzelfde geldt voor indexwijzigingen, aangezien dit van invloed kan zijn op de stabiliteit en de prestaties van het systeem als deze niet worden opgegeven, getest en opnieuw worden gedestilleerd voordat ze in productie worden genomen.

Hieronder volgt een lijst met de belangrijkste wijzigingen ten opzichte van AEM 6.5 en eerdere versies:

1. Gebruikers hebben geen toegang tot Indexbeheer van één AEM-instantie om fouten op te sporen, te configureren of indexering te onderhouden. Het wordt alleen gebruikt voor lokale ontwikkeling en on-prem-implementaties.
1. Gebruikers veranderen de indexen niet op één AEM-exemplaar en hoeven zich ook geen zorgen meer te maken over consistentiecontroles of opnieuw indexeren.
1. Over het algemeen worden indexwijzigingen aangevangen voordat naar de productie wordt gegaan om de kwaliteitsgateways in de Cloud Manager-CBI/Cd-pijpleidingen niet te omzeilen en geen invloed te hebben op de KPI&#39;s van de bedrijfsactiviteiten in de productie.
1. Alle verwante metriek, met inbegrip van onderzoeksprestaties in productie, zijn beschikbaar voor klanten bij runtime om de holistische mening over de onderwerpen van onderzoek en het indexeren te verstrekken.
1. Klanten kunnen waarschuwingen instellen op basis van hun behoeften.
1. SRE&#39;s controleren de systeemgezondheid 24/7 en er wordt zo snel mogelijk actie ondernomen.
1. Indexconfiguratie wordt gewijzigd via implementaties. Wijzigingen in indexdefinities worden net als andere wijzigingen in de inhoud geconfigureerd.
1. Op een hoog niveau op AEM as a Cloud Service, met de introductie van het [ het rollen plaatsingsmodel ](#index-management-using-rolling-deployments), bestaan twee reeksen indexen: voor de oude versie, en voor de nieuwe versie.
1. Klanten kunnen zien of de indexerende baan op Cloud Manager volledig is bouwt pagina en ontvangt een bericht wanneer de nieuwe versie klaar is om verkeer te nemen.

Beperkingen:

* Indexbeheer op AEM as a Cloud Service wordt momenteel alleen ondersteund voor indexen van het type `lucene` . Dit betekent dat alle indexaanpassingen van het type `lucene` moeten zijn. De eigenschap `async` mag slechts een van de volgende eigenschappen zijn: `[async]` , `[async,nrt]` of `[fulltext-async]` .
* Intern, zouden andere indexen voor vragen kunnen worden gevormd en worden gebruikt. Vragen die bijvoorbeeld op basis van de `damAssetLucene` -index worden geschreven, kunnen op AEM as a Cloud Service in feite worden uitgevoerd op basis van een Elasticsearch-versie van deze index. Dit verschil is niet zichtbaar voor de gebruiker. Bepaalde gereedschappen, zoals de functie `explain` , rapporteren echter een andere index. Voor verschillen tussen de indexen van Lucene en Elastische indexen, zie [ de Elastische documentatie in Apache Jackrabbit Oak ](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten hoeven en kunnen Elasticsearch-indexen niet rechtstreeks configureren.
* Alleen standaardanalysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.
* Zoeken op vergelijkbare eigenschapvectoren (`useInSimilarity = true`) wordt niet ondersteund.

>[!TIP]
>
>Voor meer details op Oak het indexeren en de vragen, met inbegrip van een gedetailleerde beschrijving van geavanceerde onderzoek en het indexeren eigenschappen, zie de [ documentatie van Apache Oak ](https://jackrabbit.apache.org/oak/docs/query/query.html).


## Hoe wordt het gebruikt {#how-to-use}

Indexdefinities kunnen als volgt in drie gevallen van primair gebruik worden ingedeeld:

1. **voeg** een nieuwe definitie van de douaneindex toe.
2. **werk** een bestaande indexdefinitie bij door een nieuwe versie toe te voegen.
3. **verwijder** een indexdefinitie die niet meer noodzakelijk is.

Voor zowel de punten 1 als 2 hierboven, moet u een indexdefinitie als deel van uw basis van douanecode in het respectieve de versieschema van Cloud Manager tot stand brengen. Voor meer informatie, zie [ het Opstellen aan AEM as a Cloud Service ](/help/implementing/deploying/overview.md) documentatie.

## Indexnamen {#index-names}

Een indexdefinitie kan in één van de volgende categorieën vallen:

1. De OOTB-index (Out-of-the-box). Dit zijn vooraf gedefinieerde indexen van AEM. Bijvoorbeeld: `/oak:index/cqPageLucene-2` of `/oak:index/damAssetLucene-8` .

2. Aanpassing van een OOTB-index. Als u een OOTB-index wilt aanpassen, voegt u `-custom-` toe, gevolgd door een getal. `/oak:index/damAssetLucene-8-custom-1` is bijvoorbeeld de aanpassing van de OOTB-index `/oak:index/damAssetLucene-8` . Een aanpassing is doorgaans een kopie van de OOTB-index, plus aanvullende eigenschappen die moeten worden geïndexeerd.

3. Volledig aangepaste index: u kunt een geheel nieuwe geheel nieuwe index maken. Deze indexen moeten ook eindigen met `-custom-` en een versienummer. U voorkomt naamconflicten door een voorvoegsel in de indexnaam te gebruiken. Bijvoorbeeld: `/oak:index/acme.product-1-custom-2` , waarbij `acme.` het voorvoegsel is.

>[!NOTE]
>
>Het introduceren van nieuwe indexen op het `dam:Asset` nodetype (in het bijzonder fulltext indexen) wordt sterk afgeraden, omdat deze een conflict kunnen veroorzaken met OOTB-productfuncties, wat tot functionele en prestatieproblemen kan leiden. In plaats daarvan kunt u query&#39;s het beste indexeren op het `dam:Asset` nodetype door de `damAssetLucene-*` -index aan te passen door de extra eigenschappen toe te voegen. Deze wijzigingen worden automatisch in volgende releases samengevoegd in een nieuwe productversie. Neem in geval van twijfel contact op met Adobe Support voor advies.

## De nieuwe indexdefinitie voorbereiden {#preparing-the-new-index-definition}

>[!NOTE]
>
>Wanneer het aanpassen van een uit-van-de-doos index, bijvoorbeeld, `damAssetLucene-8`, kopieer de recentste uit-van-de-doos indexdefinitie van het milieu van a *Cloud Service* gebruikend de Manager van het Pakket van CRX DE (`/crx/packmgr/`). Wijzig de naam in `damAssetLucene-8-custom-1` (of hoger) en voeg uw aanpassingen toe in het XML-bestand. Als de index in de cloud van het type `elasticsearch` is, zijn aanvullende wijzigingen nodig: wijzig de eigenschap `type` in `lucene` , wijzig de eigenschap `async` in `[async,nrt]` en wijzig de eigenschap `similarityTags` in `true` . Dit zorgt ervoor dat de vereiste configuraties niet per ongeluk worden verwijderd. Het knooppunt `tika` onder `/oak:index/damAssetLucene-8/tika` is bijvoorbeeld vereist in de aangepaste index die wordt geïmplementeerd in een AEM Cloud Service-omgeving, maar bestaat niet in de lokale AEM SDK.

Maak voor aanpassingen van een OOTB-index een nieuw pakket met de aangepaste of aangepaste indexdefinitie. De indexnaam moet het naamgevingspatroon volgen:

`<indexName>-<productVersion>-custom-<customVersion>`

Voor een volledig aangepaste index maakt u een nieuw indexdefinitiepakket dat de indexdefinitie bevat die volgt op dit naamgevingspatroon:

`<prefix>.<indexName>-<productVersion>-custom-<customVersion>`

Zoals vermeld in de limietsecties, moet de `type` van de aangepaste indexdefinitie altijd worden ingesteld op `lucene` , zelfs als de geëxtraheerde indexdefinitie met Package Manager van een ander type is (bijvoorbeeld `elasticsearch` ).
De eigenschap `async` moet ook worden gewijzigd als de definitie van de geëxtraheerde index is ingesteld op `elastic-async` . De eigenschap `async` moet op een van de volgende waarden worden ingesteld: `[async]` , `[async,nrt]` of `[fulltext-async]` voor de aangepaste indexdefinitie.

<!-- Alexandru: temporarily drafting this statement due to CQDOC-17701

The package from the above sample is built as `com.adobe.granite:new-index-content:zip:1.0.0-SNAPSHOT`. -->

>[!NOTE]
>
>Voor inhoudspakketten met indexdefinities moeten de volgende eigenschappen zijn ingesteld in het `properties.xml` -bestand van het inhoudspakket. `properties.xml` wordt standaard gemaakt in een nieuw pakket en bevindt zich op `<package_name>/META-INF/vault/properties.xml` :
>
> * `noIntermediateSaves=true`
>
> * `allowIndexDefinitions=true`

## Aangepaste indexdefinities gebruiken {#deploying-custom-index-definitions}

Om de plaatsing van een aangepaste versie van de uit-van-de-doos index `damAssetLucene-8` te illustreren, zullen wij een geleidelijke gids verstrekken. In dit voorbeeld wordt de naam gewijzigd in `damAssetLucene-8-custom-1` . Dan is het proces als volgt:

1. Maak een nieuwe map met de bijgewerkte indexnaam in de map `ui.apps` :
   * Voorbeeld: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/`

2. Voeg een configuratiebestand `.content.xml` toe met de aangepaste configuraties in de gemaakte map. Hieronder ziet u een voorbeeld van een aanpassing:
Bestandsnaam: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/.content.xml`

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

3. Voeg een item toe aan het FileVault-filter in `ui.apps/src/main/content/META-INF/vault/filter.xml` :

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       ...
       <filter root="/oak:index/damAssetLucene-8-custom-1"/> 
   </workspaceFilter>
   ```

4. Voeg een configuratiebestand voor Apache Tika toe in: `ui.apps/src/main/content/jcr_root/_oak_index/damAssetLucene-8-custom-1/tika/config.xml`

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

5. Zorg ervoor dat uw configuratie met de richtlijnen in de [ sectie van de Configuratie van het Project ](#project-configuration) wordt verstrekt in overeenstemming is. Breng de nodige aanpassingen aan.

## Projectconfiguratie

We raden u ten zeerste aan om versie >= `1.3.2` van het Jackrabbit `filevault-package-maven-plugin` te gebruiken. U kunt dit als volgt in uw project opnemen:

1. Werk de versie op het hoogste niveau bij `pom.xml` :

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

   Hier volgt een voorbeeld van het bestand op hoofdniveau van het project `pom.xml` met de bovenstaande configuraties:

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

3. In `ui.apps/pom.xml` en `ui.apps.structure/pom.xml` is het nodig om de opties `allowIndexDefinitions` en `noIntermediateSaves` in te schakelen in het dialoogvenster `filevault-package-maven-plugin` . Als u `allowIndexDefinitions` inschakelt, zijn aangepaste indexdefinities mogelijk, terwijl `noIntermediateSaves` ervoor zorgt dat de configuraties automatisch worden toegevoegd.

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

4. Voeg een filter voor `/oak:index` in `ui.apps.structure/pom.xml` toe:

   ```xml
   <filters>
       ...
       <filter><root>/oak:index</root></filter>
   </filters>
   ```

Implementeer de nieuwe toepassing met Cloud Manager nadat u de nieuwe indexdefinitie hebt toegevoegd. Deze implementatie start twee taken, die verantwoordelijk zijn voor het toevoegen (en indien nodig samenvoegen) van de indexdefinities aan respectievelijk MongoDB en Azure Segment Store voor auteur en publicatie. Vóór de omschakeling, ondergaan de onderliggende bewaarplaatsen opnieuw in overeenstemming met de bijgewerkte indexdefinities.

>[!TIP]
>
>Voor meer details over de vereiste pakketstructuur voor AEM as a Cloud Service, zie [ de Structuur van het Project van AEM ](/help/implementing/developing/introduction/aem-project-content-package-structure.md).

## Indexbeheer met behulp van rollende implementaties {#index-management-using-rolling-deployments}

### Wat is indexbeheer {#what-is-index-management}

Indexbeheer gaat over het toevoegen, verwijderen en wijzigen van indexen. Het veranderen van de *definitie* van een index is snel, maar het toepassen van de verandering (vaak genoemd &quot;bouwend een index&quot;, of, voor bestaande indexen, &quot;het opnieuw indexeren&quot;vereist tijd. Het is niet onmiddellijk: de gegevensopslagruimte moet gescand worden om de gegevens te indexeren.

### Wat zijn de Rolling Plaatsingen {#what-are-rolling-deployments}

Een het rollen plaatsing staat voor nul downtime verbeteringen toe, en verstrekt snelle terugdraaiversies. De oude versie van de toepassing wordt tegelijk met de nieuwe versie van de toepassing uitgevoerd.

### Alleen-lezen en Gebieden lezen/schrijven {#read-only-and-read-write-areas}

Bepaalde delen van de opslagplaats (alleen-lezen onderdelen van de opslagplaats) kunnen verschillend zijn in de oude en de nieuwe versie van de toepassing. De gebieden met het kenmerk Alleen-lezen van de gegevensopslagruimte zijn doorgaans `/app` en `/libs` . In het volgende voorbeeld wordt cursief gebruikt voor het markeren van alleen-lezen gebieden, terwijl vet wordt gebruikt voor lezen-schrijven gebieden.

* **/**
* */apps (alleen-lezen)*
* **/content**
* */libs (alleen-lezen)*
* **/eak:index**
* **/eak:index/acme.**
* **/jcr:system**
* **/system**
* **/var**

De lees-schrijfgebieden van de opslagplaats worden gedeeld tussen alle versies van de toepassing, terwijl er voor elke versie van de toepassing een specifieke set `/apps` en `/libs` is.

### Indexbeheer zonder doorlopende implementaties {#index-management-without-rolling-deployments}

Tijdens de ontwikkeling, of wanneer het gebruiken van installaties op-gebouw, kunnen de indexen worden toegevoegd, worden verwijderd, of bij runtime worden veranderd. Indexen worden gebruikt wanneer ze beschikbaar zijn. Als een index nog niet in de oude versie van de toepassing wordt gebruikt, dan wordt de index typisch gebouwd tijdens een geplande onderbreking. Hetzelfde geldt wanneer u een index verwijdert of een bestaande index wijzigt. Wanneer u een index verwijdert, is deze niet meer beschikbaar wanneer u de index verwijdert.

### Indexbeheer met doorlopende implementaties {#index-management-with-rolling-deployments}

Met het rollen plaatsingen, is er geen onderbreking. Gedurende een update worden zowel de oude versie (bijvoorbeeld versie 1) van de toepassing als de nieuwe versie (versie 2) tegelijkertijd uitgevoerd op dezelfde opslagplaats. Als voor versie 1 een bepaalde index beschikbaar moet zijn, mag deze index niet worden verwijderd in versie 2. De index moet later worden verwijderd, bijvoorbeeld in versie 3, waarna gegarandeerd is dat versie 1 van de toepassing niet meer wordt uitgevoerd. Ook, zouden de toepassingen zodanig moeten worden geschreven dat versie 1 goed werkt, zelfs als versie 2 loopt, en als de indexen van versie 2 beschikbaar zijn.

Nadat de upgrade naar de nieuwe versie is voltooid, kunnen oude indexen door het systeem worden opgeschoond. De oude indexen blijven doorgaans één week behouden om terugdraaiversies te versnellen (als een terugdraaiactie nodig is).

In de volgende tabel worden vijf indexdefinities weergegeven: index `cqPageLucene` wordt in beide versies gebruikt, terwijl index `damAssetLucene-custom-1` alleen in versie 2 wordt gebruikt.

>[!NOTE]
>
>AEM as a Cloud Service heeft `<indexName>-custom-<customerVersionNumber>` nodig om deze te markeren als vervanging voor een bestaande index.

| Index | Index buiten de box | Gebruiken in versie 1 | Gebruiken in versie 2 |
|---|---|---|---|
| /eikel:index/damAssetLucene-8 | Ja | Ja | Nee |
| /eak:index/damAssetLucene-8-custom-1 | Ja (aangepast) | Nee | Ja |
| /oak:index/acme.product-1-custom-1 | Nee | Ja | Nee |
| /oak:index/acme.product-1-custom-2 | Nee | Nee | Ja |
| /oak:index/cqPageLucene-2 | Ja | Ja | Ja |

Het versienummer wordt telkens verhoogd wanneer de index wordt gewijzigd. Als u wilt voorkomen dat aangepaste indexnamen botsen met indexnamen van het product zelf, moeten aangepaste indexen en wijzigingen in indexen die buiten het vak staan, eindigen met `-custom-<number>` .

### Wijzigingen in indexen buiten de box {#changes-to-out-of-the-box-indexes}

Nadat Adobe een index heeft gewijzigd die buiten het vak valt, zoals `damAssetLucene` of `cqPageLucene` , wordt een nieuwe index met de naam `damAssetLucene-2` of `cqPageLucene-2` gemaakt. Of als de index al is aangepast, wordt de aangepaste indexdefinitie samengevoegd met de wijzigingen in de index buiten het vak, zoals hieronder wordt weergegeven. Het samenvoegen van wijzigingen gebeurt automatisch. Dat betekent dat u niets hoeft te doen als een index buiten de doos verandert. Het is echter mogelijk de index later opnieuw aan te passen. In dit geval is het belangrijk om de nieuwste (samengevoegde) versie als basislijn te gebruiken.

| Index | Index buiten de box | Gebruiken in versie 2 | Gebruiken in versie 3 |
|---|---|---|---|
| /eak:index/damAssetLucene-1-custom-1 | Ja (aangepast) | Ja | Nee |
| /eak:index/damAssetLucene-2-custom-1 | Ja (automatisch samengevoegd van damAssetLucene-1-custom-1 en damAssetLucene-2) | Nee | Ja |
| /oak:index/cqPageLucene-1 | Ja | Ja | Nee |
| /oak:index/cqPageLucene-2 | Ja | Nee | Ja |

Het is belangrijk om te weten dat omgevingen zich in verschillende AEM-versies kunnen bevinden. De `dev` -omgeving staat bijvoorbeeld op de release `X+1` terwijl het werkgebied en de prod nog steeds op de release staan `X` en wachten op upgrade tot de `X+1` -omgeving wordt uitgebracht nadat de vereiste tests op `dev` zijn uitgevoerd. Als release `X+1` wordt geleverd met een nieuwere versie van een productindex die is aangepast en een nieuwe aanpassing van die index is vereist, wordt in de volgende tabel uitgelegd welke versies moeten worden ingesteld in omgevingen die zijn gebaseerd op de AEM-release:

| Omgeving (AEM-releaseversie) | Versie van productindex | Bestaande aangepaste indexversie | Nieuwe aangepaste indexversie |
|-----------------------------------|-----------------------|-------------------------------|----------------------------|
| Dev (X+1) | damAssetLucene-11 | damAssetLucene-11-custom-1 | damAssetLucene-11-custom-2 |
| Werkgebied (X) | damAssetLucene-10 | damAssetLucene-10-custom-1 | damAssetLucene-10-custom-2 |
| Prod (X) | damAssetLucene-10 | damAssetLucene-10-custom-1 | damAssetLucene-10-custom-2 |


### Huidige beperkingen {#current-limitations}

Indexbeheer wordt alleen ondersteund voor indexen van het type `lucene` met `compatVersion` ingesteld op `2` . Intern, zouden andere indexen voor vragen, bijvoorbeeld, indexen van Elasticsearch kunnen worden gevormd en worden gebruikt. Query&#39;s die zijn geschreven op basis van de `damAssetLucene` -index kunnen in AEM as a Cloud Service worden uitgevoerd op een Elasticsearch-versie van deze index. Dit verschil is onzichtbaar voor de gebruiker van de toepassing, maar bepaalde gereedschappen, zoals de functie `explain` , rapporteren een andere index. Voor verschillen tussen de indexen van Lucene en van Elasticsearch, zie [ de documentatie van Elasticsearch in Apache Jackrabbit Oak ](https://jackrabbit.apache.org/oak/docs/query/elastic.html). Klanten kunnen en hoeven Elasticsearch-indexen niet rechtstreeks te configureren.

Alleen ingebouwde analysatoren worden ondersteund (dat wil zeggen de analysatoren die bij het product worden geleverd). Aangepaste analysatoren worden niet ondersteund.

Het indexeren van de inhoud van `/oak:index` wordt momenteel niet ondersteund.

Voor de beste operationele prestaties, zouden de indexen niet bovenmatig groot moeten zijn. De totale grootte van alle indexen kan als richtlijn worden gebruikt. Als deze grootte na het toevoegen van aangepaste indexen met meer dan 100% toeneemt en de standaardindexen in een ontwikkelomgeving zijn aangepast, moeten de aangepaste indexdefinities worden aangepast. AEM as a Cloud Service kan de implementatie van indexen voorkomen of indexen verwijderen die de stabiliteit en prestaties van het systeem negatief beïnvloeden.

### Een index toevoegen {#adding-an-index}

Als u een volledig aangepaste index met de naam `/oak:index/acme.product-1-custom-1` wilt toevoegen die in een nieuwe versie van de toepassing en hoger wordt gebruikt, moet de index als volgt worden geconfigureerd:

`acme.product-1-custom-1`

Deze configuratie werkt door een douane herkenningsteken aan de indexnaam vooraf in te stellen, die door een punt (**`.`**) wordt gevolgd. De id moet uit 2 tot 5 tekens bestaan.

Zoals hierboven, zorgt deze configuratie ervoor dat de index slechts door de nieuwe versie van de toepassing wordt gebruikt.

### Index wijzigen {#changing-an-index}

Wanneer een bestaande index wordt gewijzigd, moet een nieuwe index met de gewijzigde indexdefinitie worden toegevoegd. Stel bijvoorbeeld dat de bestaande index `/oak:index/acme.product-1-custom-1` is gewijzigd. De oude index wordt opgeslagen onder `/oak:index/acme.product-1-custom-1` en de nieuwe index wordt opgeslagen onder `/oak:index/acme.product-1-custom-2` .

De oude versie van de toepassing gebruikt de volgende configuratie:

`/oak:index/acme.product-1-custom-1`

De nieuwe versie van de toepassing gebruikt de volgende (veranderde) configuratie:

`/oak:index/acme.product-1-custom-2`

>[!NOTE]
>
>Indexdefinities in AEM as a Cloud Service komen mogelijk niet volledig overeen met de indexdefinities in een lokale ontwikkelingsinstantie. Het ontwikkelingsexemplaar heeft geen configuratie Tika, terwijl de instanties van AEM as a Cloud Service één hebben. Als u een index met een configuratie van de Tika aanpast, behoud de configuratie van de Tika.

### Een wijziging ongedaan maken {#undoing-a-change}

Soms is het nodig om een wijziging in een indexdefinitie ongedaan te maken, bijvoorbeeld vanwege een fout of omdat de wijziging niet langer nodig is. Als de indexdefinitie `damAssetLucene-8-custom-3` bijvoorbeeld een fout bevat, kunt u terugkeren naar de vorige definitie, `damAssetLucene-8-custom-2` . Hiertoe maakt u een nieuwe index met de naam `damAssetLucene-8-custom-4` die een kopie is van de vorige index, `damAssetLucene-8-custom-2.`

### Een index verwijderen {#removing-an-index}

Het volgende is alleen van toepassing op aanpassingen van kant-en-klare indexen (OTB) en op volledig aangepaste indexen. De oorspronkelijke OOTB-indexen kunnen niet worden verwijderd, omdat ze door AEM worden gebruikt.

Om systeemintegriteit en stabiliteit te waarborgen, moeten indexdefinities worden behandeld als onveranderlijk zodra opgesteld. Als u een aangepaste index of aanpassing moet verwijderen, maakt u een nieuwe versie van die index met een definitie die het verwijderen effectief simuleert
(zie de onderstaande voorbeelden).

Zodra een nieuwe versie van een index wordt opgesteld, zal de oudere versie van de zelfde index niet meer door vragen worden gebruikt.
De oudere versie wordt niet onmiddellijk uit de omgeving verwijderd,
maar komt in aanmerking voor afvalophaling door een opruimingsmechanisme dat periodiek wordt uitgevoerd.
Na een respijtperiode die is ontworpen om herstel mogelijk te maken in geval van fouten
(momenteel 7 dagen tellen vanaf het tijdstip waarop de indexering is verwijderd, maar kan worden gewijzigd),
dit opruimingsmechanisme verwijdert de ongebruikte indexgegevens;
en schakelt u de oude versie van de index uit of verwijdert u deze uit de omgeving.

Hieronder worden de twee mogelijke gevallen beschreven: het verwijderen van aanpassingen van een OTB-index en het verwijderen van een volledig aangepaste index.

#### Het verwijderen van Aanpassingen van een uit-van-de-doos index

Volg de stappen in [ worden beschreven ongedaan maken een Verandering ](#undoing-a-change-undoing-a-change) gebruikend de definities van de index OTB als nieuwe versie die. Als u bijvoorbeeld `damAssetLucene-8-custom-3` al hebt geïmplementeerd, maar de aanpassingen niet meer nodig hebt en wilt terugschakelen naar de standaard `damAssetLucene-8` -index, moet u een index `damAssetLucene-8-custom-4` toevoegen die de indexdefinitie van `damAssetLucene-8` bevat.

#### Een volledig aangepaste index verwijderen

Volg de stappen die in [ worden beschreven Ongedaan maken een Verandering ](#undoing-a-change-undoing-a-change) gebruikend een dummyindex als nieuwe versie. Een dummyindex wordt nooit gebruikt voor query&#39;s en bevat geen gegevens. Het effect is dus hetzelfde als wanneer de index niet bestaat. In dit voorbeeld kunt u de naam `/oak:index/acme.product-1-custom-3` geven. Deze naam vervangt de index `/oak:index/acme.product-1-custom-2`. Een voorbeeld van een dergelijke dummy-index is:

```xml
<acme.product-1-custom-3
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
</acme.product-1-custom-3>
```

## Optimalisatie van index en query {#index-query-optimizations}

Met Apache Jackrabbit Oak kunnen flexibele indexconfiguraties zoekopdrachten efficiënt verwerken. Indexen zijn vooral belangrijk voor grotere opslagplaatsen. Zorg ervoor dat alle vragen door een aangewezen index worden gesteund. De vragen zonder een geschikte index kunnen duizenden knopen lezen, die dan als waarschuwing worden geregistreerd.

Zie [ dit document ](query-and-indexing-best-practices.md) voor informatie over hoe de vragen en de indexen kunnen worden geoptimaliseerd.
