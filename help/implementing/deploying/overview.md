---
title: Implementeren naar AEM as a Cloud Service
description: 'Implementeren naar AEM as a Cloud Service '
translation-type: tm+mt
source-git-commit: 10e12a8b15e6ea51e8b022deefaefed52780d48a
workflow-type: tm+mt
source-wordcount: '3512'
ht-degree: 1%

---


# Implementeren naar AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Inleiding {#introduction}

De grondbeginselen van codeontwikkeling zijn gelijkaardig in AEM als de Dienst van de Wolk in vergelijking met de oplossingen van AEM op Premise en Beheerde Diensten. Ontwikkelaars schrijven code en testen deze lokaal, waarna AEM als een Cloud Service-omgeving op afstand wordt geplaatst. Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor beheerde services, is vereist. Dit is nu het enige mechanisme voor het implementeren van code naar AEM als een Cloud Service-omgeving.

De update van de AEM-versie is altijd een afzonderlijke implementatiegebeurtenis en geen aangepaste code die u wilt doorvoeren. Op een andere manier bekeken, zouden de versies van de douanecode tegen de versie moeten worden getest AEM die op productie is aangezien dat is wat het bovenop van zal worden opgesteld. AEM versie updates die daarna gebeuren, die in vergelijking met de Beheerde Diensten vandaag vaak zullen voorkomen, worden automatisch toegepast. Ze zijn bedoeld om achterwaarts compatibel te zijn met de reeds geïmplementeerde klantcode.

De volgende video biedt een overzicht op hoog niveau over hoe u code als Cloud Service naar AEM kunt implementeren:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

In de rest van dit document wordt beschreven hoe ontwikkelaars hun praktijken moeten aanpassen, zodat ze zowel met AEM werken als met de Version-updates van een Cloud Service als met de updates van de klant.

>[!NOTE]
>Aanbevolen wordt dat klanten met bestaande codesystemen de in de [AEM-documentatie](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html)beschreven herstructurering van de opslagplaats doorlopen.


## AEM-versie-updates {#version-updates}

Het is belangrijk om te begrijpen dat AEM regelmatig, potentieel zo vaak als eenmaal per dag zal worden bijgewerkt, en zich op insectenmoeilijke situaties en prestatiesverhogingen zal concentreren. De update wordt op transparante wijze uitgevoerd en er wordt geen downtime veroorzaakt. De update is bedoeld om achterwaarts compatibel te zijn. Dit betekent dat u geen aangepaste code hoeft te wijzigen. In feite, zijn de updates AEM onafhankelijke gebeurtenissen van de plaatsingen van de klantencode. De AEM-update wordt geïmplementeerd boven op de laatste succesvolle code-push, die impliceert dat eventuele wijzigingen die zijn doorgevoerd sinds de laatste push naar de productie, niet worden geïmplementeerd.

>[!NOTE]
>
> Als de douanecode aan het opvoeren werd geduwd en dan door u werd verworpen, zal de volgende update AEM die veranderingen verwijderen om de git markering van de laatste succesvolle klantenversie aan productie te weerspiegelen.

Op een regelmatige frequentie, zal een eigenschapversie plaatsvinden, die zich op eigenschaptoevoegingen en verhogingen concentreert die wezenlijk de gebruikerservaring in vergelijking met de dagelijkse versies zullen beïnvloeden. Een eigenschapversie wordt teweeggebracht niet door de plaatsing van een grote veranderingsreeks, maar eerder door het omdraaien van een versiesknevel, activerende code die zich in de loop van dagen of weken door de dagelijkse updates heeft verzameld.

Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles mislukken tijdens een AEM als update van de Cloud Service, zal de release niet doorgaan voor die omgeving en zal Adobe onderzoeken waarom de update dit onverwachte gedrag heeft veroorzaakt.

### Composite Node Store {#composite-node-store}

Zoals hierboven vermeld, zullen updates in de meeste gevallen nul onderbreking, onder meer voor de auteur, die een cluster van knopen is. Rolling updates zijn mogelijk vanwege de functie &quot;Samengesteld knooppunt opslaan&quot; in Eak. Met deze functie kan AEM meerdere opslagplaatsen tegelijk gebruiken. In een voortschrijdende plaatsing, bevat de nieuwe Groene versie AEM zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke bewaarplaats), verschillend van de oudere Blauwe versie AEM, hoewel allebei verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare bewaarplaats die gebieden zoals `/content`, `/conf`, `/etc` en anderen bevat. Omdat blauw en Groen hun eigen versies van hebben, kunnen zij allebei actief tijdens de het rollen update zijn, allebei die verkeer nemen tot het blauw volledig door groen wordt vervangen. `/libs`

## Klantenreleases {#customer-releases}

### Codering op basis van de juiste AEM-versie {#coding-against-the-right-aem-version}

Voor eerdere AEM-oplossingen is de meest recente AEM-versie niet vaak gewijzigd (ongeveer jaarlijks met driemaandelijkse servicepakketten) en klanten zouden de productie-instanties op hun eigen tijd bijwerken naar de nieuwste snelstartversie, waarbij naar de API Jar wordt verwezen. AEM als toepassingen van de Cloud-service worden echter vaker automatisch bijgewerkt naar de nieuwste versie van AEM, zodat aangepaste code voor interne releases tegen die nieuwere AEM-interfaces moet worden gemaakt.

Net als bij bestaande AEM-versies buiten de cloud, wordt een lokale, offline ontwikkeling op basis van een specifieke QuickStart ondersteund en wordt verwacht dat deze in de meeste gevallen het juiste middel is om fouten op te sporen.

>[!NOTE]
>Er zijn subtiele operationele verschillen tussen de werking van de toepassing op een lokale computer en die van Adobe Cloud. Deze architecturale verschillen moeten tijdens de lokale ontwikkeling worden gerespecteerd en kunnen bij de implementatie op de cloudinfrastructuur tot een ander gedrag leiden. Vanwege deze verschillen is het belangrijk om de uitgebreide tests uit te voeren op ontwikkelings- en werkgebiedomgevingen voordat nieuwe aangepaste code in productie wordt geïmplementeerd.

Als u aangepaste code voor een interne release wilt ontwikkelen, moet de relevante versie van de [AEM als SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) voor de cloudservice worden gedownload en geïnstalleerd. Zie [deze pagina](/help/implementing/dispatcher/overview.md)voor meer informatie over het gebruik van de AEM als programma&#39;s voor de verzending van cloudservices.

## Inhoudspakketten implementeren via Cloud Manager en Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementaties via Cloud Manager {#deployments-via-cloud-manager}

Klanten implementeren aangepaste code in cloudomgevingen via Cloud Manager. Cloud Manager transformeert lokaal geassembleerde inhoudspakketten naar een artefact dat voldoet aan het Sling Feature Model (Sling Feature Model). Zo wordt een AEM als Cloud Service-toepassing beschreven wanneer deze wordt uitgevoerd in een cloudomgeving. Als u de pakketten in Package Manager bekijkt in Cloud-omgevingen, bevat de naam dus &quot;cp2fm&quot; en zijn alle metagegevens verwijderd uit de getransformeerde pakketten. Er kan geen interactie met deze toepassingen plaatsvinden, wat betekent dat ze niet kunnen worden gedownload, gerepliceerd of geopend. U vindt hier [](https://github.com/apache/sling-org-apache-sling-feature-cpconverter)gedetailleerde documentatie over de converter.

Inhoudspakketten die voor AEM als toepassingen van de Cloud Service worden geschreven, moeten een duidelijke scheiding tussen onveranderbare en veranderbare inhoud hebben en Cloud Manager zal dit afdwingen door de build niet uit te voeren, zoals:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

In de rest van deze sectie worden de samenstelling en de gevolgen van onveranderbare en veranderbare pakketten beschreven.

### Onveranderbare inhoudspakketten {#immutabe-content-packages}

Alle inhoud en code die in de onveranderlijke gegevensopslagplaats voortkomen, moeten in git worden gecontroleerd en door de Manager van de Wolk worden opgesteld. Met andere woorden, in tegenstelling tot de huidige AEM-oplossingen, wordt code nooit rechtstreeks geïmplementeerd op een actieve AEM-instantie. Dit zorgt ervoor dat de code die voor een bepaalde release in een Cloud-omgeving wordt uitgevoerd, identiek is, waardoor het risico van onbedoelde codevariatie bij de productie wordt uitgesloten. Als voorbeeld, zou de configuratie OSGI aan broncontrole eerder dan beheerd bij runtime via de configuratiemanager van de AEM Webconsole moeten worden geëngageerd.

Aangezien de toepassingsveranderingen toe te schrijven aan het blauw-Groene plaatsingspatroon door een schakelaar worden toegelaten, kunnen zij niet van veranderingen in de veranderbare bewaarplaats met uitzondering van de dienstgebruikers, hun ACLs, nodetypes en de veranderingen van de indexdefinitie afhangen.

Voor klanten met bestaande codebases is het van essentieel belang om de herstructureringsoefening in de opslagplaats te doorlopen die in de documentatie van AEM wordt beschreven om ervoor te zorgen dat inhoud die voorheen onder /etc. viel, naar de juiste plaats wordt verplaatst.

## OSGI-configuratie {#osgi-configuration}

Zoals hierboven vermeld, zou de configuratie OSGI aan broncontrole eerder dan door de Webconsole moeten worden geëngageerd. Te dien einde zijn onder meer de volgende technieken van toepassing:

* De noodzakelijke wijzigingen aanbrengen in de lokale AEM-omgeving van de ontwikkelaar met de configuratiemanager van de AEM-webconsole en de resultaten vervolgens exporteren naar het AEM-project op het lokale bestandssysteem
* Creërend manueel de configuratie OSGI in het AEM- project op het lokale dossiersysteem, het van verwijzingen voorzien van de configuratiemanager van de console AEM voor de bezitsnamen.

Lees meer over configuratie OSGI bij het [Vormen OSGi voor AEM als de Dienst](/help/implementing/deploying/configuring-osgi.md)van de Wolk.

## Mabelinhoud {#mutable-content}

In sommige gevallen is het handig om wijzigingen in de inhoud voor te bereiden in bronbeheer, zodat dit kan worden geïmplementeerd door Cloud Manager wanneer een omgeving is bijgewerkt. Het kan bijvoorbeeld redelijk zijn om bepaalde basismapstructuren of regelwijzigingen in bewerkbare sjablonen toe te staan om beleid in te schakelen voor componenten die door de implementatie van de toepassing zijn bijgewerkt.

Er zijn twee strategieën om de inhoud te beschrijven die door Cloud Manager aan de veranderlijke bewaarplaats, veranderbare inhoudspakketten zal worden opgesteld en verklaringen opnieuw richt.

### Mabelinhoudspakketten {#mutable-content-packages}

Inhoud zoals de hiërarchieën van de omslagweg, de dienstgebruikers, en toegangscontroles (ACLs) worden typisch toegewijd in een bepaald archetype-Gebaseerd AEM- project. Tot de technieken behoren exporteren vanuit AEM of rechtstreeks schrijven als XML. Tijdens het ontwikkelings- en implementatieproces verpakt Cloud Manager het resulterende veranderbare inhoudspakket. De veranderlijke inhoud wordt geïnstalleerd bij 3 verschillende tijden tijdens de opstellen fase in de pijpleiding:

Voor het opstarten van een nieuwe versie van de toepassing:

* indexdefinities (toevoegen, wijzigen, verwijderen)

Tijdens het opstarten van een nieuwe versie van de toepassing, maar vóór de omschakeling:

* Servicegebruikers (toevoegen)
* ACLs van de Gebruiker van de dienst (toevoegen)
* knooppunttypen (toevoegen)

Na de overgang naar de nieuwe versie van de toepassing:

* Alle andere inhoud die kan worden gedefinieerd via een jackrabbit-vault. Bijvoorbeeld:
   * Mappen (toevoegen, wijzigen, verwijderen)
   * Bewerkbare sjablonen (toevoegen, wijzigen, verwijderen)
   * Contextbewuste configuratie (alles onder `/conf`) (toevoegen, wijzigen, verwijderen)
   * Scripts (pakketten kunnen installatiehaken activeren in verschillende stadia van het installatieproces van een pakket

Het is mogelijk om installatie van veranderlijke inhoud tot auteur te beperken of te publiceren door pakketten in te bedden installeer.auteur of installeer.publish omslag onder `/apps`. Nadere bijzonderheden zijn te vinden in de [AEM-documentatie](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/restructuring/repository-restructuring.html) over de aanbevolen projectherstructurering.

>[!NOTE]
>Inhoudspakketten worden geïmplementeerd op alle omgevingstypen (dev, stage, prod). Het is niet mogelijk de implementatie te beperken tot een specifieke omgeving. Deze beperking is van toepassing om ervoor te zorgen dat een testrun van geautomatiseerde uitvoering mogelijk is. Voor inhoud die specifiek is voor een omgeving is handmatige installatie via Package Manager vereist.

Ook, is er geen mechanisme om de veranderlijke veranderingen van het inhoudspakket terug te draaien nadat zij zijn toegepast. Als klanten een probleem ontdekken, kunnen zij verkiezen om het in hun volgende codeversie of als laatste redmiddel te bevestigen, het volledige systeem aan een punt in tijd vóór de plaatsing herstellen.

Alle meegeleverde pakketten van derden moeten worden gevalideerd als zijnde compatibel met AEM als cloudservice, anders leidt de opname ervan tot een implementatiefout.

Zoals hierboven vermeld, moeten klanten met bestaande codebacken zich houden aan de herstructureringsexercitie van de repository die in de [AEM documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html)wordt beschreven.

## Opnieuw plaatsen {#repoinit}

In de volgende gevallen verdient het de voorkeur de hand te houden aan het coderen van expliciete `repoinit` instructies voor het maken van inhoud in OSGI-fabrieksconfiguraties:

* Servicegebruikers maken/verwijderen/uitschakelen
* Groepen maken/verwijderen
* Gebruikers maken/verwijderen
* Voeg ACLs toe
   > [!NOTE]
   >De definitie van ACLs vereist dat de knoopstructuren reeds aanwezig zijn. Het is dus mogelijk dat u padinstructies moet maken.
* Pad toevoegen (bijvoorbeeld voor basismapstructuren)
* CND&#39;s toevoegen (geen typedefinities)

Het is aan te raden deze gevallen van wijziging van inhoud opnieuw te plaatsen om de volgende voordelen te bieden:

* Herpoinit leidt tot middelen bij opstarten zodat de logica het bestaan van die middelen voor vanzelfsprekend kan nemen. In de veranderlijke benadering van het inhoudspakket, worden de middelen gecreeerd na opstarten, zodat de toepassingscode die op hen baseert kan ontbreken.
* Opnieuw aanwijzen is een relatief veilige instructieset aangezien u uitdrukkelijk de te nemen actie controleert. Bovendien zijn de enige ondersteunde bewerkingen additief, met uitzondering van een paar beveiligingsgerelateerde gevallen die verwijdering van Gebruikers, Gebruikers en Groepen toestaan. Daarentegen is het expliciet schrappen van iets in de aanpak van het veranderbare inhoudspakket;  als u een filter definieert, wordt alles wat aanwezig is en door een filter wordt bedekt, verwijderd. Toch moet voorzichtigheid worden betracht, aangezien er scenario&#39;s zijn waarin de aanwezigheid van nieuwe inhoud het gedrag van de toepassing kan veranderen.
* Repoinit voert snelle en atomische bewerkingen uit. De veranderlijke inhoudspakketten in contrast kunnen hoogst afhankelijk van prestaties van de structuren die door een filter worden behandeld. Zelfs als u één knooppunt bijwerkt, kan een momentopname van een grote boomstructuur worden gemaakt.
* Het is mogelijk om opnieuw richt verklaringen op een lokaal dev milieu bij runtime te bevestigen aangezien zij zullen worden uitgevoerd wanneer de configuratie OSGi wordt geregistreerd.
* Herpointe-instructies zijn atomisch en expliciet en worden overgeslagen als de status al overeenkomt.

Wanneer de toepassing wordt geïmplementeerd in Cloud Manager, worden deze instructies onafhankelijk van de installatie van inhoudspakketten uitgevoerd.

Volg de onderstaande procedure voor het maken van instructies voor opnieuw plaatsen:

1. Voeg configuratie OSGi voor PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in een configuratiemap van het project toe
1. Voeg opnieuw richt verklaringen aan het manuscripteigenschap van config toe. De syntaxis en de opties worden beschreven in de documentatie [van het](https://sling.apache.org/documentation/bundles/repository-initialization.html)Sling. Let op: er moet een bovenliggende map expliciet worden gemaakt voordat de onderliggende mappen worden gemaakt. Bijvoorbeeld, een expliciete verwezenlijking van `/content` vóór `/content/myfolder`, vóór `/content/myfolder/mysubfolder`. Voor ACLs die op lage niveaustructuren worden geplaatst wordt het geadviseerd om die op een hoger niveau te plaatsen en met een `rep:glob` beperking te werken.  Bijvoorbeeld `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Valideren in de lokale ontwikkelomgeving bij uitvoering.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Voor ACLs die voor knopen wordt bepaald onderaan `/apps` of zal `/libs` de herpuntuitvoering op een lege bewaarplaats beginnen. De pakketten worden geïnstalleerd nadat het opnieuw richt zodat kunnen de verklaringen niet op om het even wat baseren die in de pakketten wordt bepaald maar moeten de voorwaarden zoals de ouderstructuren onder bepalen.

>[!TIP]
>
>Voor ACLs zou de verwezenlijking van diepe structuren omslachtig kunnen zijn, daarom redelijker is om ACL op een hoger niveau te bepalen en te beperken waar het via een rep:glob beperking zou moeten handelen.

Meer informatie over het opnieuw aanwijzen vindt u in de [verkoopdocumentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one offs&quot; voor Mutable Content Packages {#package-manager-oneoffs-for-mutable-content-packages}

Er zijn gebruiksgevallen waarin een inhoudspakket als &quot;één uit&quot; moet worden geïnstalleerd. Bijvoorbeeld het invoeren van specifieke inhoud van productie aan het opvoeren om een productiekwestie te zuiveren. Voor deze scenario&#39;s, kan de Manager van het Pakket in AEM als milieu&#39;s van de Dienst van de Wolk worden gebruikt.

Aangezien Package Manager een runtimeconcept is, is het niet mogelijk om inhoud of code in de onveranderlijke opslagplaats te installeren, zodat zouden deze inhoudspakketten slechts uit veranderbare inhoud (hoofdzakelijk `/content` of `/conf`) moeten bestaan. Als het inhoudspakket inhoud bevat die gemengd is (zowel muteerbare als onveranderlijke inhoud), wordt alleen de veranderbare inhoud geïnstalleerd.

Eventuele inhoudspakketten die via Cloud Manager zijn geïnstalleerd (zowel veranderbaar als onveranderbaar) worden in bevroren toestand weergegeven in de gebruikersinterface van AEM Package Manager. Deze pakketten kunnen niet opnieuw worden geïnstalleerd, opnieuw worden samengesteld of zelfs worden gedownload en worden weergegeven met het achtervoegsel **&quot;cp2fm&quot;** , waarmee wordt aangegeven dat de installatie ervan is beheerd door Cloud Manager.

### Inclusief pakketten van derden {#including-third-party}

Het is gebruikelijk dat klanten vooraf gebouwde pakketten van bronnen van derden opnemen, zoals softwareleveranciers zoals de vertaalpartners van Adobe. De aanbeveling is om deze pakketten in een verre bewaarplaats te ontvangen en hen in `pom.xml`te verwijzen. Dit is alleen mogelijk voor openbare gegevensbanken.

Als het opslaan van het pakket in een externe opslagplaats niet mogelijk is, kunnen klanten in een lokale, op bestandssysteem gebaseerde Maven opslagplaats plaatsen, die aan SCM als deel van het project wordt geëngageerd en door wat van het hangt van het van verwijzingen voorzien. De opslagplaats zou worden gedeclareerd in de onderstaande projectpomp:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle meegeleverde pakketten van derden moeten aan de AEM-code en verpakkingsrichtlijnen van de cloudservice worden gekoppeld, zoals in dit artikel wordt beschreven. Als dit niet gebeurt, treedt een implementatiefout op.

Het volgende Maven POM XML-fragment toont hoe pakketten van derden in het &quot;Container&quot;-pakket van het project kunnen worden ingesloten, doorgaans **&#39;all&#39;** genoemd, via de configuratie voor de Maven-invoegtoepassing **filevault-package-maven-plugin**.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <subPackages>
           
          <!-- Include the application's ui.apps and ui.content packages -->
          ...
 
          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <!-- Set the version for all dependencies, including 3rd party packages, in the project's Reactor POM -->
          <subPackage>
              <groupId>com.adobe.cq</groupId>
              <artifactId>core.wcm.components.all</artifactId>
              <filter>true</filter>
          </subPackage>
 
 
          <subPackage>
              <groupId>com.3rdparty.groupId</groupId>
              <artifactId>core.3rdparty.artifactId</artifactId>
              <filter>true</filter>
          </subPackage>
      <subPackages>
  </configuration>
</plugin>
...
```

## Hoe de Rolling Inzet werkt {#how-rolling-deployments-work}

Net als de updates van AEM, worden de klantenversies opgesteld gebruikend een het rollen plaatsingsstrategie om auteurcluster onderbreking in de juiste omstandigheden te elimineren. De algemene volgorde van gebeurtenissen wordt hieronder beschreven. **Blauw** is de oude versie van de klantcode en **Groen** is de nieuwe versie. Met zowel Blauw als Groen wordt dezelfde versie van de AEM-code uitgevoerd.

* De blauwe versie is actief en er is een releasekandidaat voor Groen gemaakt en beschikbaar
* Als er nieuwe of bijgewerkte indexdefinities zijn, worden de overeenkomstige indexen verwerkt. Merk op dat de blauwe plaatsing altijd de oude indexen zal gebruiken, terwijl groen altijd de nieuwe indexen zal gebruiken.
* Groen begint terwijl blauw nog steeds werkt
* Blauw wordt uitgevoerd en gebruikt terwijl Groen via gezondheidscontroles op gereedheid wordt gecontroleerd
* Groene knopen die klaar verkeer goedkeuren en Blauwe knopen vervangen, die worden onderdrukt
* In de loop der tijd worden blauwe knooppunten vervangen door groene knooppunten totdat alleen de groene knooppunten overblijven, zodat de implementatie wordt voltooid
* Nieuwe of gewijzigde inhoud die kan worden gemuteerd, wordt geïmplementeerd

## Indexen {#indexes}

De nieuwe of gewijzigde indexen zullen een extra indexerende of re-indexerende stap veroorzaken alvorens de nieuwe (Groene) versie verkeer kan nemen. De details over indexbeheer in Skyline kunnen in [dit artikel](/help/operations/indexing.md)worden gevonden. U kunt de status van de indexeertaak controleren op de bouwstijlpagina van Cloud Manager en ontvangt een melding wanneer de nieuwe versie klaar is om verkeer te nemen.

>[!NOTE]
>
>De tijd nodig voor een het rollen plaatsing zal afhankelijk van de grootte van de index variëren, aangezien de Groene versie geen verkeer kan goedkeuren tot de nieuwe index is geproduceerd.

Op dit ogenblik, werkt de Veldlijn niet met indexbeheerhulpmiddelen zoals ACS de Commons verzekeren het hulpmiddel van de Index van het Eik.

## Replicatie {#replication}

Het publicatiemechanisme is achterwaarts compatibel met de Java API&#39;s voor [AEM Replication](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Voor het ontwikkelen en testen van replicatie met AEM QuickStart, klaar voor de cloud, moeten de klassieke replicatiemogelijkheden worden gebruikt met een Auteur/Publish opstelling. Als het UI-ingangspunt op AEM Author is verwijderd voor de cloud, gaan gebruikers naar `http://localhost:4502/etc/replication` de configuratie.

## Achterwaarts Compatibele Code voor het Draaien Plaatsingen {#backwards-compatible-code-for-rolling-deployments}

Zoals hierboven beschreven, impliceert AEM als de het rollen plaatsingsstrategie van de Dienst van de Wolk dat zowel de oude als nieuwe versies tezelfdertijd kunnen werken. Wees daarom voorzichtig met codewijzigingen die niet achterwaarts compatibel zijn met de oude AEM-versie die nog steeds wordt uitgevoerd.

Bovendien moet de oude versie worden getest op compatibiliteit met eventuele nieuwe muteerbare inhoudsstructuren die door de nieuwe versie worden toegepast in geval van terugdraaiing, aangezien muteerbare inhoud niet wordt verwijderd.

### De Gebruikers van de dienst en ACL Veranderingen {#service-users-and-acl-changes}

Het veranderen van de dienstgebruikers of ACLs nodig om tot inhoud of code toegang te hebben kon tot fouten in de oudere versies leiden AEM resulterend in toegang tot die inhoud of code met verouderde de dienstgebruikers. Om dit te verhelpen, is het raadzaam om wijzigingen door minstens 2 versies te laten spreiden, waarbij de eerste release als een brug fungeert voordat de release wordt opgeschoond.

### Indexwijzigingen {#index-changes}

Als er wijzigingen in indexen worden aangebracht, is het belangrijk dat de blauw-versie de indexen blijft gebruiken totdat deze worden beëindigd, terwijl de groene versie een eigen aangepaste set indexen gebruikt. De ontwikkelaar moet de [in dit artikel](/help/operations/indexing.md)beschreven technieken voor indexbeheer volgen.

### Conservatieve codering voor terugdraaiversies {#conservative-coding-for-rollbacks}

Als een mislukking na de plaatsing wordt gemeld of ontdekt, is het mogelijk dat een terugschroeven van prijzen aan de Blauwe versie zal worden vereist. Het zou verstandig zijn om ervoor te zorgen dat de blauwe code compatibel is met nieuwe structuren die door de groene versie worden gecreëerd, aangezien de nieuwe structuren (muteerbare inhoud) niet worden teruggedraaid. Als de oude code niet compatibel is, moeten fixes worden toegepast in volgende versies van de klant.

## Runmodi {#runmodes}

In bestaande AEM oplossingen, hebben de klanten de optie om instanties met willekeurige looppaswijzen in werking te stellen en de configuratie toe te passen OSGI of bundels te installeren OSGI op die specifieke instanties. De wijze van de looppas die typisch worden bepaald omvat de *dienst* (auteur en publiceer) en het milieu (dev, stadium, prod).

AEM als Cloud Service daarentegen is meer overtuigd over welke uitvoeringsmodi beschikbaar zijn en hoe OSGI-bundels en OSGI-configuratie aan hen kunnen worden toegewezen:

* De de configuratieloopwijzen van OSGI moeten dev, stadium, prod voor het milieu of auteur, publiceren voor de dienst van verwijzingen voorzien. Er `<service>.<environment_type>` wordt een combinatie van beide ondersteund, terwijl deze in deze volgorde moeten worden gebruikt (bijvoorbeeld `author.dev` of `publish.prod`). Er moet rechtstreeks vanuit de code naar de OSGI-tokens worden verwezen in plaats van de `getRunModes` methode, die de tokens niet meer `environment_type` bij uitvoering bevat. Voor meer informatie, zie het [Vormen OSGi voor AEM als de Dienst](/help/implementing/deploying/configuring-osgi.md)van de Wolk.
* De de bundelloopwijzen van OSGI zijn beperkt tot de dienst (auteur, publiceer). OSGI-bundels per run-modus moeten in het inhoudspakket worden geïnstalleerd onder `install/author` of `install/publish`.

Net als de bestaande AEM-oplossingen is er geen manier om runmodi te gebruiken om alleen inhoud voor specifieke omgevingen of services te installeren. Als u een ontwikkelomgeving wilt laten doorlopen met gegevens of HTML-code die zich niet in het werkgebied of de productie bevindt, kan de pakketmanager worden gebruikt.

De ondersteunde runmode configuraties zijn:

* **config** (*het gebrek, is op alle Diensten* van AEM van toepassing)
* **config.author** (*van toepassing op alle dienst* van de Auteur AEM)
* **config.author.dev** (van *toepassing op de dienst* van de Auteur van AEM Dev)
* **config.author.stage** (*van toepassing op de AEM Staging Author-service*)
* **config.author.prod** (van *toepassing op de dienst* van de Auteur van de Productie AEM)
* **config.publish** (van *toepassing op de publicatieservice* AEM)
* **config.publish.dev** (van *toepassing op de publicatieservice* van AEM Dev)
* **config.publish.stage** (*van toepassing op de publicatieservice* voor AEM-paginering)
* **config.publish.prod** (van *toepassing op de publicatieservice* van de Productie van AEM)
* **config.dev** (*Is van toepassing op de diensten van AEM Dev)
* **config.stage** (*Van toepassing op de Staging van AEM de diensten)
* **config.prod** (*Is van toepassing op de Diensten van de Productie AEM)

De configuratie OSGI die de meest passende runmodes heeft wordt gebruikt.

Wanneer het ontwikkelen plaatselijk, kan een loopmode startparameter worden overgegaan om te dicteren welke loopmode configuratie OSGI zal worden gebruikt.

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuratie van onderhoudstaken in bronbeheer {#maintenance-tasks-configuration-in-source-control}

De configuraties van de onderhoudstaak moeten in broncontrole worden voortgezet aangezien het scherm van **Hulpmiddelen > Verrichtingen** niet meer in de milieu&#39;s van de Wolk beschikbaar zal zijn. Dit heeft het voordeel dat we ervoor zorgen dat veranderingen met opzet worden doorgevoerd in plaats van reactief te worden toegepast en misschien vergeten worden. Raadpleeg het artikel [](/help/operations/maintenance.md) Onderhoudstaken voor aanvullende informatie.
