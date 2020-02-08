---
title: Afstemmen van elementprestaties
description: Belangrijke aandachtsgebieden rond AEM-configuratie, wijzigingen in hardware, software en netwerkcomponenten om knelpunten te verwijderen en de prestaties van AEM Assets te optimaliseren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Afstemmen van elementprestaties{#assets-performance-tuning-guide}

Een installatie van Adobe Experience Manager (AEM) Assets bevat een aantal hardware-, software- en netwerkcomponenten. Afhankelijk van uw plaatsingsscenario, kunt u specifieke configuratieveranderingen in hardware, software, en netwerkcomponenten vereisen om prestatiesknelpunten te verwijderen.

Bovendien zorgt het identificeren en volgen van bepaalde richtlijnen voor hardware- en softwareoptimalisatie voor een solide basis waarmee uw implementatie van AEM-middelen kan voldoen aan de verwachtingen op het gebied van prestaties, schaalbaarheid en betrouwbaarheid.

De slechte prestaties in AEM Assets kunnen gebruikerservaring rond interactieve prestaties, activa verwerking, downloadsnelheid, en andere gebieden beïnvloeden.

In feite, is de prestatiesoptimalisering een fundamentele taak die u uitvoert alvorens u doelmetriek voor om het even welk project vestigt.

Hier zijn bepaalde belangrijke aandachtsgebieden waaromheen u prestatieproblemen ontdekt en verhelpt voordat deze van invloed zijn op gebruikers.

## Platform {#platform}

Hoewel AEM op een aantal platforms wordt ondersteund, heeft Adobe de grootste ondersteuning voor native gereedschappen op Linux en Windows gevonden. Dit levert optimale prestaties en vereenvoudigt de implementatie. In het ideale geval moet u een 64-bits besturingssysteem implementeren om te voldoen aan de hoge geheugenvereisten van een AEM Assets-implementatie. Net als bij elke AEM-implementatie moet u TarMK waar mogelijk implementeren. Hoewel TarMK niet voorbij één enkele auteurinstantie kan schrapen, wordt het gevonden om beter te presteren dan MongoMK. U kunt TarMK-offloadinstanties toevoegen om de verwerkingskracht van de workflow voor de implementatie van AEM-middelen te verhogen.

### Temp-map {#temp-folder}

Om de uploadtijden van middelen te verbeteren, gebruik krachtige opslag voor de folder van de Temp van Java. In Linux en Windows kan een RAM-station of SSD worden gebruikt. In cloudomgevingen kan een vergelijkbaar type snelle opslag worden gebruikt. In Amazon EC2 kan bijvoorbeeld een [&quot;ephaleral drive&quot;](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/InstanceStorage.html) -station worden gebruikt voor de map temp.

Ervan uitgaande dat de server over voldoende geheugen beschikt, configureert u een RAM-station. Voer in Linux de volgende opdrachten uit om een 8 GB RAM-station te maken:

```
mkfs -q /dev/ram1 800000
 mkdir -p /mnt/aem-tmp
 mount /dev/ram1 /mnt/aem-tmp
 df -H | grep aem-tmp
```

In Windows OS moet u een stuurprogramma van een andere fabrikant gebruiken om een RAM-station te maken of gewoon krachtige opslagruimte zoals SSD gebruiken.

Zodra het volume van de hoge prestatietemp klaar is, dan plaats de parameter JVM -Djava.io.tmpdir. U kunt bijvoorbeeld de JVM-parameter hieronder toevoegen aan de CQ_JVM_OPTS-variabele in het bin/start-script van AEM:

`-Djava.io.tmpdir=/mnt/aem-tmp`

## Java-configuratie {#java-configuration}

### Java-versie {#java-version}

Omdat Oracle de release van updates voor Java 7 sinds april 2015 heeft stopgezet, raadt Adobe aan AEM Assets te implementeren op Java 8. In sommige gevallen heeft het een verbeterde prestatie aangetoond.

### JVM-parameters {#jvm-parameters}

U moet de volgende JVM-parameters instellen:

* `-XX:+UseConcMarkSweepGC`
* `-Doak.queryLimitInMemory`=500000
* `-Doak.queryLimitReads`=100000
* `-Dupdate.limit`=250000
* `-Doak.fastQuerySize`=true

## Gegevensopslag en geheugenconfiguratie {#data-store-and-memory-configuration}

### Configuratie bestandsgegevensopslag {#file-data-store-configuration}

Het wordt aanbevolen de gegevensopslag te scheiden van de segmentopslag voor alle gebruikers van AEM Assets. Bovendien kan het vormen van de `maxCachedBinarySize` en `cacheSizeInMB` parameters helpen prestaties maximaliseren. Stel dit in `maxCachedBinarySize` op de kleinste bestandsgrootte die in de cache kan worden opgeslagen. Geef de grootte op van de cache in het geheugen die moet worden gebruikt voor de datastore binnen `cacheSizeInMB`. Adobe raadt u aan deze waarde in te stellen tussen 2 en 10 procent van de totale heapgrootte. Het testen van de belasting/prestaties kan echter helpen de ideale instelling te bepalen.

### De maximale grootte van de cache voor gebufferde afbeeldingen configureren {#configure-the-maximum-size-of-the-buffered-image-cache}

Wanneer u grote hoeveelheden middelen uploadt naar Adobe Experience Manager, kunt u de geconfigureerde maximale grootte van de cache voor gebufferde afbeeldingen verkleinen om onverwachte pieken in het geheugengebruik mogelijk te maken en te voorkomen dat JVM uitvalt met OutOfMemoryErrors. Bekijk een voorbeeld van een systeem met een maximale heap (- `Xmx`param) van 5 GB, een Oak BlobCache ingesteld op 1 GB en een documentcache ingesteld op 2 GB. In dit geval neemt de gebufferde cache maximaal 1,25 GB en geheugen in beslag, waardoor er slechts 0,75 GB geheugen overblijft voor onverwachte pieken.

Vorm de als buffer opgetreden voor geheim voorgeheugengrootte in de Console van het Web OSGi. Stel de eigenschap in `https://host:port/system/console/configMgr/com.day.cq.dam.core.impl.cache.CQBufferedImageCache``cq.dam.image.cache.max.memory` bytes in. 1073741824 is bijvoorbeeld 1 GB (1024 x 1024 x 1024 = 1 GB).

Van AEM 6.1 SP1, als u een `sling:osgiConfig` knoop voor het vormen van dit bezit gebruikt, zorg ervoor om het gegevenstype aan Lang te plaatsen. Zie [CQBufferedImageCache gebruikt heap tijdens het uploaden](https://helpx.adobe.com/experience-manager/kb/cqbufferedimagecache-consumes-heap-during-asset-uploads.html)van bedrijfsmiddelen voor meer informatie.

### Gedeelde gegevensopslag {#shared-data-stores}

Het uitvoeren van S3 of de Gedeelde Datastore van het Dossier kan helpen om schijfruimte te besparen en netwerkproductie in grootschalige implementaties te verhogen.

### S3-gegevensopslag {#s-data-store}

Met de volgende S3 Data Store-configuratie ( `org.apache.jackrabbit.oak.plugins.blob.datastore.S3DataStore.cfg`) kon Adobe 12,8 TB binaire grote objecten (BLOB&#39;s) uitpakken uit een bestaande bestandsgegevensopslag naar een S3-gegevensopslag op een klantsite:

```
accessKey=<snip>
 secretKey=<snip>
 s3Bucket=<snip>
 s3Region=us-standard
 s3EndPoint=<a href="https://s3.amazonaws.com/">s3.amazonaws.com</a>
 connectionTimeout=120000
 socketTimeout=120000
 maxConnections=80
 writeThreads=60
 concurrentUploadsThreads=30
 asyncUploadLimit=30
 maxErrorRetry=1000
 path=/opt/author/crx-quickstart/repository/datastore
 s3RenameKeys=false
 s3Encryption=SSE_S3
 proactiveCaching=true
 uploadRetries=1000
 migrateFailuresCount=400
```

## Netwerkoptimalisatie {#network-optimization}

Adobe raadt u aan HTTPS in te schakelen omdat veel bedrijven firewalls hebben die HTTP-verkeer sluizen, wat het uploaden van bestanden negatief beïnvloedt en bestanden beschadigt. Bij grote bestanden uploaden dient u ervoor te zorgen dat gebruikers een bekabelde verbinding met het netwerk hebben omdat een WiFi-netwerk snel verzadigd raakt. Om netwerkprestaties te beoordelen door netwerktopologie te analyseren, zie de Overwegingen van het Netwerk van [Activa](/help/assets/assets-network-considerations.md).

Primair, hangt uw strategie van de netwerkoptimalisering van de hoeveelheid beschikbare bandbreedte en de lading op uw instantie AEM af. De gemeenschappelijke configuratieopties, met inbegrip van firewalls of volmachten kunnen helpen netwerkprestaties verbeteren. Hier volgen enkele belangrijke punten:

* Afhankelijk van uw instantietype (klein, gematigd, groot), zorg ervoor dat u voldoende netwerkbandbreedte voor uw instantie AEM hebt. De juiste bandbreedtetoewijzing is vooral belangrijk als AEM op AWS wordt ontvangen.
* Als uw AEM-instantie wordt gehost op AWS, kunt u profiteren van een veelzijdig schalingsbeleid. De instantie vergroten als gebruikers een hoge belasting verwachten. Downsize het voor matige/lage lading.
* HTTPS: De meeste gebruikers hebben firewalls die het verkeer van HTTP snuffelen, wat het uploaden van dossiers of zelfs corrupte dossiers tijdens het uploaden negatief kan beïnvloeden.
* Grote bestanden uploaden: Zorg ervoor dat gebruikers een bekabelde verbinding met het netwerk hebben (WiFi-verbindingen verzadigen snel).

## Workflows {#workflows}

### Tijdelijke workflows {#transient-workflows}

Stel waar mogelijk de DAM Update Asset-workflow in op Transient. De instelling verlaagt aanzienlijk de overheadkosten die nodig zijn voor het verwerken van workflows, omdat workflows in dit geval niet door de normale tracking- en archiveringsprocessen hoeven te gaan.

>[!NOTE]
>
>Standaard is de DAM Update Asset-workflow ingesteld op Transient in AEM 6.3. In dit geval kunt u de volgende procedure overslaan.

1. Navigeer naar */miscadmin* in de AEM-instantie die moet worden geconfigureerd (d.w.z. [https://localhost:4502/miscadmin)](https://localhost:4502/miscadmin)).
1. Vouw in de navigatiestructuur **Gereedschappen** > **Workflow** > **Modellen** > **dam** uit.
1. Dubbelklik op **DAM Update Asset**.
1. Ga in het zwevende gereedschapvenster naar het tabblad **Pagina** en klik vervolgens op **Pagina-eigenschappen...**
1. Selecteer **Transient Workflow** en klik op **OK**.

   >[!NOTE]
   >
   >Bepaalde functies ondersteunen geen tijdelijke workflows. Configureer geen tijdelijke workflows als deze functies vereist zijn voor de implementatie van AEM-middelen.

   Als er geen tijdelijke workflows kunnen worden gebruikt, voert u de workflow regelmatig uit om gearchiveerde DAM Update Asset-workflows te verwijderen om ervoor te zorgen dat de systeemprestaties niet afnemen.

   Normaal gesproken dient u wekelijks penseelworkflows uit te voeren. Nochtans, in middel-intensieve scenario&#39;s, zoals tijdens brede activaopname, kunt u het vaker in werking stellen.

   Om werkschemazuivering te vormen, voeg een nieuwe configuratie van de Woorden van het Werkschema van Adobe Granite door de console OSGi toe. Vervolgens configureert en plant u de workflow als onderdeel van het wekelijkse onderhoudsvenster.

   Als het leegmaken te lang duurt, is het wel even. Daarom dient u ervoor te zorgen dat uw reinigingstaken zijn voltooid om situaties te voorkomen waarin het leegmaken van werkstromen mislukt vanwege het grote aantal werkstromen.

   Bijvoorbeeld, na het runnen van talrijke niet-transient werkschema&#39;s (die tot de knopen van de werkschemainstantie leidt), kunt u het Werkschema van [ACS AEM Commons Remover](https://adobe-consulting-services.github.io/acs-aem-commons/features/workflow-remover.html) op een ad hoc basis in werking stellen. Het verwijdert overbodige, voltooide workflowexemplaren direct in plaats van te wachten tot de Adobe Granite Workflow Purge-planner wordt uitgevoerd.

### Maximumaantal parallelle banen {#maximum-parallel-jobs}

Standaard voert AEM een maximumaantal parallelle taken uit dat gelijk is aan het aantal processors op de server. Het probleem met deze instelling is dat tijdens perioden van zware belasting alle processors worden gebruikt door DAM Update Asset-workflows, waardoor de reactiesnelheid van de gebruikersinterface wordt vertraagd en wordt voorkomen dat AEM andere processen uitvoert die de prestaties en stabiliteit van de server waarborgen. U kunt deze waarde als een goede praktijk instellen op de helft van de processors die beschikbaar zijn op de server door de volgende stappen uit te voeren:

1. Ga naar [https://localhost:4502/system/console/slingevent](https://localhost:4702/system/console/slingevent)op AEM-auteur.
1. Klik op Bewerken in elke werkstroomwachtrij die relevant is voor uw implementatie, bijvoorbeeld de Granite Transient Workflow Queue.
1. Wijzig de waarde van Maximale parallelle taken en klik op Opslaan.

Het instellen van een wachtrij op de helft van de beschikbare processors is een werkbare oplossing om mee te beginnen. Het kan echter zijn dat u dit aantal moet verhogen of verlagen om een maximale doorvoer te bereiken en dat aantal aan te passen aan de omgeving. Er zijn afzonderlijke rijen voor tijdelijke en niet-tijdelijke werkstromen evenals andere processen, zoals externe werkschema&#39;s. Als meerdere wachtrijen die zijn ingesteld op 50% van de processors tegelijkertijd actief zijn, kan het systeem snel overbelast raken. De rijen die zwaar worden gebruikt variëren zeer over gebruikersimplementaties. Daarom kunt u hen voor maximumefficiency moeten zorgvuldig vormen zonder serverstabiliteit te offeren.

### DAM Update Asset Configuration {#dam-update-asset-configuration}

De DAM Update Asset-workflow bevat een volledige reeks stappen die zijn geconfigureerd voor taken, zoals het genereren van Scene7 PTIFF en de integratie van InDesign Server. Het is echter mogelijk dat de meeste gebruikers niet meerdere van deze stappen nodig hebben. Adobe raadt u aan een aangepaste kopie van het workflowmodel voor DAM Update Asset te maken en overbodige stappen te verwijderen. In dit geval werkt u de draagraketten voor DAM Update Asset bij en wijst u deze naar het nieuwe model.

>[!NOTE]
>
>Als u de DAM Update Asset-workflow intensief uitvoert, kan de bestandsdatatastore aanzienlijk groter worden. De resultaten van een door Adobe uitgevoerd experiment hebben aangetoond dat de grootte van de datastore met ongeveer 400 GB kan toenemen als binnen 8 uur ongeveer 5500 workflows worden uitgevoerd.
>
>Het is een tijdelijke verhoging, en datastore wordt hersteld aan zijn originele grootte nadat u de taak van de datastore huisvuilinzameling in werking stelt.
>
>Typisch, loopt de de inzamelingstaak van de datastore wekelijks samen met andere geplande onderhoudstaken.
>
>Als u een beperkte schijfruimte hebt en de werkschema&#39;s van de Activa van de Update van DAM intensief in werking stelt, overweeg de taak van de huisvuilinzameling vaker te plannen.

#### Genereren van uitvoering bij uitvoering {#runtime-rendition-generation}

Klanten gebruiken afbeeldingen van verschillende grootten en indelingen op hun website of voor distributie aan zakelijke partners. Omdat elke uitvoering de afdruk van het middel in de opslagplaats vergroot, raadt Adobe u aan deze functie zorgvuldig te gebruiken. Om de hoeveelheid bronnen te verminderen die nodig is om afbeeldingen te verwerken en op te slaan, kunt u deze afbeeldingen tijdens runtime genereren in plaats van als uitvoeringen tijdens het opnemen.

Vele klanten van Plaatsen voeren een beeldservlet uit die resizes en teelten beelden op het ogenblik zij worden gevraagd, wat extra lading aan de publicatieinstantie oplegt. Maar zolang deze afbeeldingen in het cachegeheugen kunnen worden opgeslagen, kan de uitdaging worden beperkt.

Een alternatieve benadering is Scene7-technologie te gebruiken om beeldmanipulatie volledig uit te schakelen. Bovendien kunt u Brand Portal implementeren dat niet alleen taken voor het genereren van vertoningen overneemt van de AEM-infrastructuur, maar ook de volledige publicatielaag.

### XMP-schrijfback {#xmp-writeback}

XMP-schrijfback werkt het oorspronkelijke element bij wanneer metagegevens worden gewijzigd in AEM. Dit resulteert in het volgende:

* Het element zelf wordt gewijzigd
* Er wordt een versie van het element gemaakt
* DAM Update-element wordt uitgevoerd op het element

De vermelde resultaten verbruiken aanzienlijke middelen. Daarom raadt Adobe aan om de functie voor het terugdraaien [van XMP uit te](https://helpx.adobe.com/experience-manager/kb/disable-xmp-writeback.html)schakelen als dit niet verplicht is.

Het invoeren van een grote hoeveelheid meta-gegevens kan in middel-intensieve kringactiviteit resulteren XMP als de loopwerkstroomvlag wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

## Replicatie {#replication}

Als u elementen wilt repliceren naar een groot aantal publicatie-instanties, bijvoorbeeld in een Sites-implementatie, raadt Adobe u aan kettingreplicatie te gebruiken. In dit geval dupliceert de auteurinstantie naar één enkel publicatiegeval dat beurtelings aan andere publicatieinstanties herhaalt, die de auteursinstantie vrijmaken.

### Kettingreplicatie configureren {#configure-chain-replication}

1. Bepaal op welke publicatie-instantie u de replicaties wilt koppelen
1. Op die publicatieinstantie voeg replicatieagenten toe die aan andere publicatieinstanties richten
1. Schakel op elk van die replicatieagents &quot;Bij ontvangst&quot; in op het tabblad &quot;Triggers&quot;

>[!NOTE]
>
>Adobe raadt automatische activering van elementen niet aan. Indien nodig raadt Adobe u echter aan dit als de laatste stap in een workflow te doen, meestal DAM Update Asset.

## Indexen zoeken {#search-indexes}

Zorg ervoor u de recentste de dienstpakken en op prestaties betrekking hebbende hotfixes uitvoert aangezien zij vaak updates aan systeemindexen omvatten. Zie Tips voor [afstemmen van prestaties| 6.x](https://helpx.adobe.com/experience-manager/kb/performance-tuning-tips.html) voor bepaalde indexoptimalisaties die kunnen worden toegepast, afhankelijk van uw versie van AEM.

<!--
Create custom indexes for queries that you run often. For details, see [methodology for analyzing slow queries](https://aemfaq.blogspot.com/2014/08/oak-query-log-file-analyzer-tool.html) and [crafting custom indexes](/help/sites-deploying/queries-and-indexing.md). For additional insights around query and index best practices, see [Best Practices for Queries and Indexing](/help/sites-deploying/best-practices-for-queries-and-indexing.md).
-->

### Lucene-indexconfiguraties {#lucene-index-configurations}

Sommige optimalisaties kunnen worden uitgevoerd op de indexconfiguraties van de eikel die de prestaties van AEM-elementen kunnen helpen verbeteren:

Indexconfiguraties bijwerken om de herindexatietijd te verbeteren:

1. CRXDe /crx/de/index.jsp openen en aanmelden als beheerder
1. Bladeren naar /ak:index/lucene
1. Voeg een String[] -eigenschap met de naam &quot;excludePaths&quot; toe met de waarden &quot;/var&quot;, &quot;/etc/workflow/instances&quot; en &quot;/etc/replication&quot;
1. Blader naar /oak:index/damAssetLucene
1. Voeg een String[] -eigenschap met de naam &quot;includedPaths&quot; toe met één waarde &quot;/content/dam&quot;
1. Opslaan

(Alleen AEM6.1 en 6.2) Werk de index ntBaseLucene bij om de prestaties van het verwijderen en verplaatsen van elementen te verbeteren:

1. Bladeren naar */einde:index/ntBaseLucene/indexRules/nt:base/properties*
1. Voeg twee nt:niet-gestructureerde knopen &quot;slingResource&quot;en &quot;damResolvedPath&quot;onder */eak:index/ntBaseLucene/indexRules/nt:base/properties toe*
1. Stel de eigenschappen hieronder op de knooppunten in (waarbij ordered en propertyIndex-eigenschappen van het type *Boolean*zijn):
slingResourcename=&quot;sling:resource&quot;ordered=falsepropertyIndex= truetype=&quot;String&quot;damResolvedPathname=&quot;dam:resolvedPath&quot;ordered=falsepropertyIndex=truetype=&quot;String&quot;

1. Stel in het knooppunt /oak:index/ntBaseLucene de eigenschap *reindex=true in*
1. Klik op Alles opslaan
1. Controleer error.log om te zien wanneer het indexeren wordt voltooid:
Indexering voltooid voor indexen: [/ak:index/ntBaseLucene]
1. U kunt ook zien dat het indexeren door de /oak:index/ntBaseLucene knoop in CRXDe te verfrissen wordt voltooid aangezien het herindexbezit aan vals zou terugkeren
1. Nadat het indexeren is voltooid, gaat u terug naar CRXDe en stelt u de eigenschap &quot;type&quot; in op uitgeschakeld voor deze twee indexen

   * */oak:index/slingResource*
   * */oak:index/damResolvedPath*

1. Klik op Alles opslaan

<!--
Disable Lucene Text Extraction:

If your users don't need to be able to search the contents of assets, for example, searching the text contained in PDF documents, then you can improve index performance by disabling this feature.

1. Go to the AEM package manager /crx/packmgr/index.jsp
1. Upload and install the package below

[Get File](assets/disable_indexingbinarytextextraction-10.zip)
-->

### Totaal raden {#guess-total}

Wanneer het creëren van vragen die grote resultaatreeksen produceren, gebruik de `guessTotal` parameter om zwaar geheugengebruik te vermijden wanneer u hen in werking stelt.

## Bekende problemen {#known-issues}

### Grote bestanden {#large-files}

Er zijn twee belangrijke bekende problemen met betrekking tot grote bestanden in AEM. Wanneer de dossiers grootten groter dan 2 GB bereiken, kan de koude reserve synchronisatie in een uit-van-geheugensituatie lopen. In sommige gevallen wordt de stand-bysynchronisatie niet uitgevoerd. In andere gevallen loopt de primaire instantie vast. Dit scenario is van toepassing op elk bestand in AEM dat groter is dan 2 GB, inclusief inhoudspakketten.

Op dezelfde manier kan het enige tijd duren voordat het bestand, wanneer bestanden een grootte van 2 GB hebben wanneer een gedeelde S3-datastore wordt gebruikt, volledig doorloopt van de cache naar het bestandssysteem. Dientengevolge, wanneer het gebruiken van binair-minder replicatie, is het mogelijk dat de binaire gegevens niet kunnen zijn voortgeduurd alvorens de replicatie voltooit. Deze situatie kan tot problemen leiden, vooral als de beschikbaarheid van gegevens belangrijk is.

## Prestaties testen {#performance-testing}

Stel voor elke AEM-implementatie een systeem voor het testen van de prestaties in dat knelpunten snel kan opsporen en oplossen. Hier volgen enkele belangrijke aandachtsgebieden.

### Netwerktests {#network-testing}

Voor alle kwesties van netwerkprestaties van de klant, voer de volgende taken uit:

* De netwerkprestaties van de test van binnen het klantennetwerk
* Test de netwerkprestaties vanuit het Adobe-netwerk. Voor klanten van AMS, werk met uw CSE om van binnen het netwerk van Adobe te testen.
* De netwerkprestaties van de test van een ander toegangspunt
* Door een hulpmiddel van de netwerkbenchmark te gebruiken
* Testen tegen de verzender

### AEM-instantietests {#aem-instance-testing}

Om latentie te minimaliseren en hoge productie door efficiënt gebruik van cpu en ladingdeling te bereiken, controleer de prestaties van uw AEM instantie regelmatig. Met name:

* Laadtests uitvoeren op de AEM-instantie
* Uploadprestaties en reactiesnelheid van de gebruikersinterface bewaken

## Controlelijst voor prestaties van AEM-middelen en impact van taken voor middelenbeheer {#checklist}

* HTTPS toestaan om rond om het even welke collectieve het verkeerssniffers van HTTP te krijgen
* Een bekabelde verbinding gebruiken voor het uploaden van zware middelen
* Implementeer in Java 8.
* Optimale JVM-parameters instellen
* Een FileSystem DataStore of een S3 DataStore configureren
* Tijdelijke workflows inschakelen
* Stem de workflowwachtrijen voor graniet af om gelijktijdige taken te beperken
* Vorm ImageMagick om middelverbruik te beperken
* Overbodige stappen verwijderen uit de DAM Update Asset-workflow
* Workflow en versiebeheer configureren
* Optimaliseer indexen met de recentste de dienstpakken en hotfixes. Raadpleeg de Technische Ondersteuning van Adobe voor eventuele extra indexoptimalisaties die beschikbaar zijn.
* Gebruik radenTotal om queryprestaties te optimaliseren.
* Als u AEM configureert om bestandstypen van de inhoud van de bestanden te detecteren (door CQ DAM Mime Type Service **[!UICONTROL op]** dag in te schakelen in de **[!UICONTROL AEM-webconsole]**), kunt u veel bestanden bulksgewijs uploaden tijdens niet-piekuren omdat dit veel bronnen vergt.

