---
title: Distribueren naar AEM as a Cloud Service
description: Meer informatie over de basisbeginselen en de beste werkwijzen van implementatie naar AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
role: Admin
source-git-commit: d6c5c70e8b6565a20866d392900aef219d3fd09d
workflow-type: tm+mt
source-wordcount: '3440'
ht-degree: 0%

---

# Distribueren naar AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Inleiding {#introduction}

De grondbeginselen van codeontwikkeling zijn in AEM as a Cloud Service vergelijkbaar met de oplossingen AEM On Premise en Managed Services. Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe omgevingen op AEM as a Cloud Service. Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit leveringshulpmiddel is nu het enige mechanisme voor het opstellen van code aan AEM as a Cloud Service dev, stadium, en productiemilieu&#39;s. Voor snelle eigenschapbevestiging en het zuiveren alvorens die eerder vermelde milieu&#39;s op te stellen, kan de code van een lokaal milieu aan a [ Snelle Milieu van de Ontwikkeling ](/help/implementing/developing/introduction/rapid-development-environments.md) worden gesynchroniseerd.

De update van de [ versie van AEM ](/help/implementing/deploying/aem-version-updates.md) is altijd een afzonderlijke plaatsingsgebeurtenis van het duwen van [ douanecode ](#customer-releases). Op een andere manier bekeken, zouden de versies van de douanecode tegen de versie van AEM moeten worden getest die op productie is omdat dat is wat het bovenop wordt opgesteld. AEM-versies die later worden bijgewerkt (vaak en automatisch worden toegepast), moeten compatibel zijn met de reeds geïmplementeerde klantcode.

In de rest van dit document wordt beschreven hoe ontwikkelaars hun praktijken moeten aanpassen zodat ze zowel met de updates van de AEM as a Cloud Service-versie als met de updates van de klant werken.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Klantenreleases {#customer-releases}

### Codering tegen de juiste AEM-versie {#coding-against-the-right-aem-version}

Voor eerdere AEM-oplossingen is de meest recente AEM-versie niet vaak gewijzigd (ongeveer jaarlijks met driemaandelijkse servicepakketten) en klanten zouden de productie-instanties op hun eigen tijd bijwerken naar de recentste snelstartversie, waarbij naar de API Jar wordt verwezen. Toepassingen op AEM as a Cloud Service worden echter vaker automatisch bijgewerkt naar de nieuwste versie van AEM, zodat aangepaste code voor interne releases moet worden gebaseerd op de nieuwste versie van AEM.

Net als bij bestaande niet-cloud AEM-versies, wordt een lokale, offline ontwikkeling ondersteund op basis van een specifieke QuickStart. Deze ontwikkeling is naar verwachting het meest geschikte instrument voor foutopsporing.

>[!NOTE]
>Er zijn subtiele operationele verschillen tussen de werking van de toepassing op een lokale computer en die van de Adobe Cloud. Deze architecturale verschillen moeten tijdens de lokale ontwikkeling worden gerespecteerd en kunnen bij de implementatie op de cloudinfrastructuur tot een ander gedrag leiden. Vanwege deze verschillen is het belangrijk om de uitgebreide tests uit te voeren op ontwikkelings- en werkgebiedomgevingen voordat nieuwe aangepaste code in productie wordt geïmplementeerd.

Om douanecode voor een interne versie te ontwikkelen, zou de relevante versie van [ AEM as a Cloud Service SDK ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) moeten worden gedownload en worden geïnstalleerd. Voor extra informatie over het gebruiken van de Hulpmiddelen van AEM as a Cloud Service Dispatcher, zie [ Dispatcher in de Wolk ](/help/implementing/dispatcher/disp-overview.md).

De volgende video biedt een overzicht op hoog niveau over hoe u code kunt implementeren in AEM as a Cloud Service:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Inhoudspakketten implementeren via Cloud Manager en Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Inzet via Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Klanten implementeren aangepaste code in cloudomgevingen via Cloud Manager. Cloud Manager transformeert lokaal geassembleerde inhoudspakketten naar een artefact dat voldoet aan het Sling Feature Model, dat is hoe een toepassing op AEM as a Cloud Service wordt beschreven wanneer deze in een cloudomgeving wordt uitgevoerd. Dientengevolge, wanneer het bekijken van de pakketten in [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md) op de milieu&#39;s van de Wolk, omvat de naam &quot;cp2fm&quot;en de getransformeerde pakketten hebben alle meta-gegevens verwijderd. Er kan geen interactie met deze toepassingen plaatsvinden, wat betekent dat ze niet kunnen worden gedownload, gerepliceerd of geopend. Zie [&#128279;](https://github.com/apache/sling-org-apache-sling-feature-cpconverter) voor gedetailleerde documentatie over de converter.
sling-org-apache-sling-feature-cpconverter op GitHub .

Inhoudspakketten die voor toepassingen op AEM as a Cloud Service zijn geschreven, moeten een duidelijke scheiding hebben tussen onveranderbare en muteerbare inhoud en Cloud Manager installeert alleen de veranderbare inhoud en voert ook een bericht uit zoals:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

De rest van deze sectie beschrijft de samenstelling en implicaties van onveranderbare en veranderbare pakketten.

### Onveranderbare inhoudspakketten {#immutabe-content-packages}

Alle inhoud en code die in de onveranderlijke gegevensopslagplaats voortkomen moeten in git worden gecontroleerd en door Cloud Manager worden opgesteld. Met andere woorden, in tegenstelling tot de huidige AEM-oplossingen, wordt code nooit rechtstreeks geïmplementeerd op een actieve AEM-instantie. Deze workflow zorgt ervoor dat de code die voor een bepaalde release in een Cloud-omgeving wordt uitgevoerd, identiek is, waardoor het risico van onbedoelde codevariatie tijdens de productie wordt uitgesloten. Als voorbeeld, zou de configuratie OSGI aan broncontrole eerder dan beheerd bij runtime door middel van de configuratiemanager van de Webconsole van AEM moeten worden geëngageerd.

Aangezien de toepassingsveranderingen toe te schrijven aan het plaatsingspatroon door een schakelaar worden toegelaten, kunnen zij niet van veranderingen in de veranderbare bewaarplaats behalve de dienstgebruikers, hun ACLs, nodetypes, en de veranderingen van de indexdefinitie afhangen.

Voor klanten met bestaande codebases is het van essentieel belang dat de in AEM-documentatie beschreven herstructureringsoefening in de repository wordt doorlopen om ervoor te zorgen dat inhoud die voorheen onder de /etc. viel, naar de juiste locatie wordt verplaatst.

Sommige extra beperkingen zijn van toepassing voor deze codepakketten, bijvoorbeeld, [ installeert haken ](https://jackrabbit.apache.org/filevault/installhooks.html) niet worden gesteund.

## OSGI-configuratie {#osgi-configuration}

Zoals hierboven vermeld, zou de configuratie OSGI aan broncontrole eerder dan door de Webconsole moeten worden geëngageerd. Te dien einde zijn onder meer de volgende technieken van toepassing:

* De benodigde wijzigingen aanbrengen in de lokale AEM-omgeving van de ontwikkelaar met de configuratiemanager van de AEM-webconsole en de resultaten vervolgens exporteren naar het AEM-project op het lokale bestandssysteem
* Creërend manueel de configuratie OSGI in het project van AEM op het lokale dossiersysteem, het van verwijzingen voorzien van de configuratiemanager van de console van AEM voor de bezitsnamen.

Lees meer over configuratie OSGI bij [ het Vormen OSGi voor AEM as a Cloud Service ](/help/implementing/deploying/configuring-osgi.md).

## Mabelinhoud {#mutable-content}

Soms, zou het nuttig kunnen zijn om inhoudsveranderingen in broncontrole voor te bereiden zodat kan het door Cloud Manager worden opgesteld wanneer een milieu werd bijgewerkt. Het kan bijvoorbeeld redelijk zijn om bepaalde basismapstructuren uit te breiden. Of, regelup veranderingen in editable malplaatjes om beleidscomponenten toe te laten die door de toepassingsplaatsing werden bijgewerkt.

Er zijn twee strategieën om de inhoud te beschrijven die door Cloud Manager wordt geïmplementeerd in de gemuteerde opslagplaats, pakketten met gemuteerde inhoud en `repoinit` -instructies.

### Tabelinhoudspakketten {#mutable-content-packages}

Inhoud zoals de hiërarchieën van de omslagweg, de dienstgebruikers, en toegangscontroles (ACLs) worden typisch toegewijd in een bepaald archetype-Gebaseerd AEM project. Tot de technieken behoren exporteren vanuit AEM of rechtstreeks schrijven als XML. Tijdens het ontwikkelings- en implementatieproces verpakt Cloud Manager het resulterende veranderbare inhoudspakket. De veranderlijke inhoud wordt geïnstalleerd bij drie verschillende tijden tijdens de opstellen fase in de pijpleiding:

Voor het opstarten van een nieuwe versie van de toepassing:

* indexdefinities (toevoegen, wijzigen, verwijderen)

Tijdens het opstarten van een nieuwe versie van de toepassing, maar vóór de omschakeling:

* Servicegebruikers (toevoegen)
* ACLs van de Gebruiker van de dienst (toevoegen)
* knooppunttypen (toevoegen)

Na de overgang naar de nieuwe versie van de toepassing:

* Alle andere inhoud die kan worden gedefinieerd door middel van een Jackrabbit-vault. Bijvoorbeeld:
   * Mappen (toevoegen, wijzigen, verwijderen)
   * Bewerkbare sjablonen (toevoegen, wijzigen, verwijderen)
   * Contextbewuste configuratie (alles onder `/conf`) (toevoegen, wijzigen, verwijderen)
   * Scripts (pakketten kunnen installatiekoppen activeren in verschillende stadia van het installatieproces van de pakketinstallatie. Zie [ het filevault documentatie van het Jasrabbit ](https://jackrabbit.apache.org/filevault/installhooks.html) over installeert haken. AEM CS gebruikt momenteel FileVault versie 3.4.0, die installatiekoppen beperkt tot beheergebruikers, systeemgebruikers en leden van de beheerdersgroep).

U kunt de installatie van veranderbare inhoud beperken tot auteur of publiceren door pakketten in te sluiten in de map install.auteur of install.publish onder `/apps` . De herstructurering om deze scheiding te weerspiegelen werd gedaan in AEM 6.5 en de details over geadviseerde projectherstructurering kunnen in [ AEM 6.5 documentatie ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html) worden gevonden.

>[!NOTE]
>Inhoudspakketten worden geïmplementeerd op alle omgevingstypen (dev, stage, prod). Het is niet mogelijk de implementatie te beperken tot een specifieke omgeving. Deze beperking is van toepassing om ervoor te zorgen dat een testrun van geautomatiseerde uitvoering mogelijk is. De inhoud die voor een milieu specifiek is vereist handinstallatie als [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md).

Er is ook geen mechanisme om wijzigingen in het veranderbare inhoudspakket terug te draaien nadat deze zijn toegepast. Als klanten een probleem ontdekken, kunnen zij verkiezen om het in hun volgende codeversie of als laatste redmiddel te bevestigen, het volledige systeem aan een punt in tijd vóór de plaatsing herstellen.

Alle meegeleverde pakketten van derden moeten als compatibel met AEM as a Cloud Service worden gevalideerd, anders leidt de opname ervan tot een implementatiefout.

Zoals hierboven vermeld, zouden de klanten met bestaande codebases aan de opbergordeherstructureringsoefening moeten in overeenstemming zijn nodig door de veranderingen van de 6.5 bewaarplaats die in [ AEM 6.5 documentatie ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html) worden beschreven.

## Opnieuw plaatsen {#repoinit}

In de volgende gevallen verdient het de voorkeur de handmatige codering van expliciete instructies `repoinit` voor het maken van inhoud in de OSGI-fabrieksconfiguraties te gebruiken:

* Servicegebruikers maken/verwijderen/uitschakelen
* Groepen maken/verwijderen
* Gebruikers maken/verwijderen
* Voeg ACLs toe

  >[!NOTE]
  >
  >De definitie van ACLs vereist dat de knoopstructuren reeds aanwezig zijn. Het is dus mogelijk dat u padinstructies moet maken.

* Pad toevoegen (bijvoorbeeld voor basismapstructuren)
* CND&#39;s toevoegen (geen typedefinities)

Het is aan te raden deze gevallen van wijziging van inhoud opnieuw te plaatsen om de volgende voordelen te bieden:

* `Repoinit` maakt bij het opstarten bronnen, zodat logica het bestaan van deze bronnen vanzelfsprekend kan maken. In de veranderlijke benadering van het inhoudspakket, worden de middelen gecreeerd na opstarten, zodat de toepassingscode die op hen baseert kan ontbreken.
* `Repoinit` is een relatief veilige instructieset omdat u expliciet bepaalt welke actie moet worden uitgevoerd. Bovendien zijn de enige ondersteunde bewerkingen additief, behalve enkele beveiligingsgerelateerde gevallen die verwijdering van Gebruikers, Gebruikers en Groepen toestaan. Een verwijdering van iets in de methode voor het muteerbare inhoudspakket is daarentegen expliciet. Wanneer u een filter definieert, wordt alle aanwezige elementen die door een filter worden gedekt, verwijderd. Toch moet voorzichtigheid worden betracht, aangezien er scenario&#39;s zijn waarin de aanwezigheid van nieuwe inhoud het gedrag van de toepassing kan veranderen.
* `Repoinit` voert snelle en atomische bewerkingen uit. De uitvoerbare inhoudspakketten in tegenstelling tot kunnen sterk afhankelijk van prestaties van de structuren die door een filter worden behandeld. Zelfs als u één knooppunt bijwerkt, kan een momentopname van een grote boomstructuur worden gemaakt.
* Het is mogelijk om `repoinit` verklaringen op een lokaal dev milieu bij runtime te bevestigen omdat zij in werking worden gesteld wanneer de configuratie OSGi wordt geregistreerd.
* `Repoinit` -instructies zijn atomisch en expliciet en worden overgeslagen als de status al overeenkomt.

Wanneer Cloud Manager de toepassing implementeert, worden deze instructies onafhankelijk van de installatie van inhoudspakketten uitgevoerd.

Volg de onderstaande procedure om `repoinit` -instructies te maken:

1. Voeg configuratie OSGi voor fabriek PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in een configuratiemap van het project toe. Gebruik een beschrijvende naam voor de configuratie als **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Voeg `repoinit` verklaringen aan het manuscripteigenschap van config toe. De syntaxis en de opties worden gedocumenteerd in [ het Verdelen documentatie ](https://sling.apache.org/documentation/bundles/repository-initialization.html). Er moet een bovenliggende map expliciet worden gemaakt voordat de onderliggende mappen worden gemaakt. Bijvoorbeeld, een expliciete verwezenlijking van `/content` before `/content/myfolder`, before `/content/myfolder/mysubfolder`. Voor ACLs die op laag-vlakke structuren worden geplaatst, wordt het geadviseerd om hen op een hoger niveau te plaatsen en met een `rep:glob` beperking te werken. Bijvoorbeeld `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))` .
1. Valideren in de lokale ontwikkelomgeving bij uitvoering.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Voor ACLs die voor knopen onder `/apps` of `/libs` wordt bepaald `repoinit`, begint de uitvoering op een lege bewaarplaats. De pakketten worden geïnstalleerd na `repoinit` , zodat instructies niet kunnen vertrouwen op iets dat in de pakketten is gedefinieerd, maar de voorwaarden moeten definiëren, zoals de bovenliggende structuren eronder.

>[!TIP]
>
>Voor ACLs, zou de verwezenlijking van diepe structuren omslachtig kunnen zijn. Daarom is het redelijker om ACL op een hoger niveau te bepalen en te beperken waar het verondersteld is om als `rep:glob` beperking te handelen.

Meer detail over `repoinit` kan in de [ het Verdelen documentatie ](https://sling.apache.org/documentation/bundles/repository-initialization.html) worden gevonden

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one offs&quot; voor Mutable Content Packages {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Pakketbeheer - Meerdere inhoudspakketten migreren"
>abstract="Verken het gebruik van Package Manager voor gebruik waarbij een inhoudspakket moet worden geïnstalleerd als &#39;one off&#39;. De installatie omvat het importeren van specifieke inhoud van de productie naar het opbouwen om een productieprobleem op te lossen, het overbrengen van een pakket met kleine inhoud van een on-premise omgeving naar AEM Cloud-omgevingen en nog veel meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html" text="Inhoud overbrengen"

Er zijn gebruiksgevallen waarin een inhoudspakket als &quot;één uit&quot; moet worden geïnstalleerd. Bijvoorbeeld, het invoeren van specifieke inhoud van productie aan het opvoeren om een productiekwestie te zuiveren. Voor deze scenario&#39;s, [ de Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md) kan in milieu&#39;s op AEM as a Cloud Service worden gebruikt.

Aangezien Package Manager een runtimeconcept is, is het niet mogelijk om inhoud of code in de onveranderlijke opslagplaats te installeren, zodat zouden deze inhoudspakketten slechts uit veranderbare inhoud (hoofdzakelijk `/content` of `/conf`) moeten bestaan. Als het inhoudspakket inhoud bevat die gemengd is (zowel muteerbare als onveranderlijke inhoud), wordt alleen de veranderbare inhoud geïnstalleerd.

>[!IMPORTANT]
>
>Het gebruikersinterface van de Manager van het Pakket zou een **niet gedefiniëerd** foutenmelding kunnen terugkeren als een pakket langer dan tien minuten om duurt te installeren.
>
>Deze keer is niet het gevolg van een fout tijdens de installatie, maar van een time-out die Cloud Service heeft voor alle aanvragen.
>
>Probeer de installatie niet opnieuw als er een dergelijke fout optreedt. De installatie verloopt op de juiste wijze op de achtergrond. Als u de installatie opnieuw start, kunnen er conflicten optreden tijdens meerdere importprocessen tegelijk.

Alle inhoudspakketten die in Cloud Manager (zowel mutabel als onveranderbaar) zijn geïnstalleerd, worden in de gebruikersinterface van AEM Package Manager bevroren weergegeven. Deze pakketten kunnen niet opnieuw worden geïnstalleerd, worden herbouwd, of zelfs worden gedownload, en zijn vermeld met a **&quot;cp2fm&quot;** achtervoegsel, erop wijzend dat hun installatie door Cloud Manager werd beheerd.

### Inclusief pakketten van derden {#including-third-party}

Het is gebruikelijk dat klanten vooraf gebouwde pakketten van bronnen van derden, zoals softwareleveranciers zoals Adobe-vertaalpartners, opnemen. Het wordt aanbevolen deze pakketten te hosten in een externe opslagruimte en ernaar te verwijzen in de `pom.xml` . Deze methode is mogelijk voor openbare bewaarplaatsen en ook voor privé bewaarplaatsen met wachtwoordbescherming, zoals die in [ wordt beschreven wachtwoord beschermde gemandateerde bewaarplaatsen ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

Als het opslaan van het pakket in een externe opslagplaats niet mogelijk is, kunnen klanten in een lokale, op bestandssysteem gebaseerde Maven-opslagplaats plaatsen, die als onderdeel van het project aan SCM is toegewezen. Er wordt naar verwezen door wat er van afhangt. De gegevensopslagruimte wordt gedeclareerd in de projectpom, zoals hieronder wordt geïllustreerd:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle meegeleverde pakketten van derden moeten voldoen aan de AEM as a Cloud Service-coderings- en verpakkingsrichtlijnen die in dit artikel worden beschreven, anders leidt de opname ervan tot een implementatiefout.

Het volgende Geweven `POM.xml` fragment toont hoe de derdepakketten in het &quot;Container&quot;pakket van het project kunnen worden ingebed, typisch genoemd **&quot;all&quot;**, als **filevault-package-maven-stop - in** Gemaakt insteekconfiguratie.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          ...

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

## Hoe de Rolling Inzet werkt {#how-rolling-deployments-work}

Net als bij AEM-updates worden klantreleases geïmplementeerd met behulp van een implementatiestrategie om clusterdowntime van de auteur onder de juiste omstandigheden te voorkomen. De algemene volgorde van gebeurtenissen wordt hieronder beschreven, waarbij knooppunten met zowel de oude als de nieuwe versie van de klantcode dezelfde versie van de AEM-code uitvoeren.

* De knopen met de oude versie zijn actief en een versiekandidaat voor de nieuwe versie wordt gebouwd en beschikbaar gesteld.
* Als er nieuwe of bijgewerkte indexdefinities zijn, worden de overeenkomstige indexen verwerkt. Knooppunten met de oude versie gebruiken altijd de oude indexen, terwijl knooppunten met de nieuwe versie altijd de nieuwe indexen gebruiken.
* De knopen met de nieuwe versieopstarten, terwijl de oude versies nog verkeer dienen.
* Knooppunten met de oude versie worden uitgevoerd en blijven werken terwijl knooppunten met de nieuwe versie door middel van gezondheidscontroles op gereedheid worden gecontroleerd.
* De knopen met de nieuwe versie die klaar zijn, goedkeuren verkeer, en vervangen de knopen door de oude versie, die worden gebracht.
* In tijd, worden de knopen met de oude versie vervangen door knopen met de nieuwe versie tot slechts knopen met nieuwe versies overblijven, waarbij de plaatsing wordt voltooid.
* Alle nieuwe of gewijzigde veranderbare inhoud wordt vervolgens geïmplementeerd.

## Indexen {#indexes}

Nieuwe of gewijzigde indexen veroorzaken een extra indexerende of herindexerende stap alvorens de nieuwe versie verkeer kan nemen. De details over indexbeheer in AEM as a Cloud Service kunnen onder [ Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md) worden gevonden. U kunt de indexerende status van bouwstijlpagina&#39;s op Cloud Manager controleren, en een bericht ontvangen wanneer de nieuwe versie klaar is om verkeer te nemen.

>[!NOTE]
>
>De tijd nodig voor een het rollen plaatsing varieert afhankelijk van de grootte van de index. De reden is dat de nieuwe versie geen verkeer kan goedkeuren tot de nieuwe index wordt geproduceerd.

AEM as a Cloud Service werkt momenteel niet met indexbeheerprogramma&#39;s zoals ACS Commons zorgen voor Oak Index.

## Replicatie {#replication}

Het publicatiemechanisme is achterwaarts compatibel met [ de Replicatie Java™ APIs van AEM ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html).

Voor het ontwikkelen en testen van replicatie met de AEM QuickStart die klaar is voor de cloud, moeten de klassieke replicatiemogelijkheden worden gebruikt met een Author/Publish-instelling. Als het ingangspunt voor de gebruikersinterface van AEM Author voor de wolk wordt verwijderd, gaan de gebruikers naar `http://localhost:4502/etc/replication` voor configuratie.

## Achterwaarts Compatibele Code voor het Draaien Plaatsingen {#backwards-compatible-code-for-rolling-deployments}

Zoals hierboven beschreven, impliceert de het rollen van AEM as a Cloud Service plaatsingsstrategie dat zowel de oude als nieuwe versies tezelfdertijd kunnen werken. Wees daarom voorzichtig met wijzigingen in de code die niet achterwaarts compatibel zijn met de oude AEM-versie die nog wordt uitgevoerd.

Bovendien moet de oude versie worden getest op compatibiliteit met eventuele nieuwe, door de nieuwe versie toegepaste structuren voor veranderbare inhoud als er sprake is van terugdraaiing, omdat gemuteerde inhoud niet wordt verwijderd.

### De Gebruikers van de dienst en ACL Veranderingen {#service-users-and-acl-changes}

Het veranderen van de dienstgebruikers, of ACLs die tot inhoud of code toegang hebben, kon tot fouten in de oudere versies van AEM leiden resulterend in toegang tot die inhoud of code met verouderde de dienstgebruikers. Om dit gedrag aan te pakken, wordt aanbevolen wijzigingen door ten minste twee releases te laten doorlopen, waarbij de eerste release als een koppeling fungeert voordat deze wordt opgeschoond in de volgende release.

### Indexwijzigingen {#index-changes}

Als er wijzigingen in indexen worden aangebracht, is het belangrijk dat de oude versie de indexen blijft gebruiken totdat deze worden beëindigd, terwijl de nieuwe versie een eigen aangepaste set indexen gebruikt. De ontwikkelaar zou de technieken moeten volgen van het indexbeheer die onder [ Inhoud Onderzoek en het Indexeren ](/help/operations/indexing.md) worden beschreven.

### Conservatieve codering voor terugdraaiversies {#conservative-coding-for-rollbacks}

Als een mislukking na de plaatsing wordt gemeld of ontdekt, is het mogelijk dat het terugschroeven van prijzen aan de oude versie wordt vereist. Zorg ervoor dat de nieuwe code compatibel is met eventuele nieuwe structuren die door die nieuwe versie worden gemaakt, aangezien de nieuwe structuren (alle veranderbare inhoud) niet worden teruggedraaid. Als de oude code niet compatibel is, moeten fixes worden toegepast in verdere versies van de klant.

## Rapid Development Environment (RDE) {#rde}

[ Snelle Milieu&#39;s van de Ontwikkeling ](/help/implementing/developing/introduction/rapid-development-environments.md) (of RDEs voor kort) staan ontwikkelaars toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren noodzakelijk om eigenschappen te testen die reeds om aan een lokaal ontwikkelingsmilieu worden bewezen te werken.

In tegenstelling tot gewone dev milieu&#39;s, die code als pijpleiding van Cloud Manager opstellen, gebruiken de ontwikkelaars bevel-lijn hulpmiddelen om code van een lokale ontwikkelomgeving aan RDE te synchroniseren. Nadat de veranderingen met succes in RDE worden getest, stel hen aan een regelmatige milieu van de Ontwikkeling van de Wolk door de pijpleiding van Cloud Manager op, die de code door de aangewezen kwaliteitspoorten zet.

## Modi uitvoeren {#runmodes}

In bestaande AEM-oplossingen kunnen klanten instanties uitvoeren met willekeurige uitvoeringsmodi en OSGI-configuratie toepassen of OSGI-bundels installeren op die specifieke instanties. De wijzen van de looppas die typisch worden bepaald omvatten de *dienst* (auteur en publiceer) en het milieu (rde, dev, stadium, prod).

AEM as a Cloud Service daarentegen is meer overtuigd over welke uitvoeringsmodi beschikbaar zijn en hoe de OSGI-bundels en de OSGI-configuratie aan hen kunnen worden toegewezen:

* De de configuratieloopwijzen van OSGI moeten RDE, ontwikkeling, stadium, productie voor het milieu of auteur, publiceren voor de dienst van verwijzingen voorzien. Een combinatie van `<service>.<environment_type>` wordt ondersteund, terwijl deze omgevingen in deze specifieke volgorde moeten worden gebruikt (bijvoorbeeld `author.dev` of `publish.prod` ). Er moet rechtstreeks vanuit code naar de OSGI-tokens worden verwezen in plaats van de methode `getRunModes` , die niet langer de `environment_type` bij uitvoering bevat. Voor meer informatie, zie [ Vormend OSGi voor AEM as a Cloud Service ](/help/implementing/deploying/configuring-osgi.md).
* De de bundelloopwijzen van OSGI zijn beperkt tot de dienst (auteur, publiceer). OSGI-bundels per-run-modus moeten worden geïnstalleerd in het inhoudspakket onder `install.author` of `install.publish` .

AEM as a Cloud Service staat het gebruik van uitvoeringsmodi niet toe om inhoud voor specifieke omgevingen of services te installeren. Als een ontwikkelomgeving moet worden voorzien van gegevens of HTML die zich niet in de opvoeromgeving of productieomgeving bevindt, kan Package Manager worden gebruikt.

De ondersteunde configuraties in de uitvoeringsmodus zijn:

* **config** (*het gebrek, is op alle diensten van AEM* van toepassing)
* **config.signer** (*is op alle dienst van de Auteur van AEM* van toepassing)
* **config.author.dev** (*is op de dienst van de Auteur van AEM Dev* van toepassing)
* **config.author.rde** (*is op de dienst van de Auteur van AEM RDE* van toepassing)
* **config.author.stage** (*is op de dienst van de Auteur van het Staging van AEM van toepassing*)
* **config.author.prod** (*is op de dienst van de Auteur van de Productie van AEM van toepassing*)
* **config.publish** (*is op de publicatiedienst van AEM van toepassing*)
* **config.publish.dev** (*is op de Dev van AEM van toepassing publiceer dienst*)
* **config.publish.rde** (*van toepassing is op AEM RDE publicatiedienst*)
* **config.publish.stage** (*is op de Staging van AEM van toepassing publicatiedienst*)
* **config.publish.prod** (*is op de dienst van de Publicatie van de Productie van AEM van toepassing*)
* **config.dev** (*is op de diensten van AEM Dev* van toepassing)
* **config.rde** (*is op de diensten van RDE* van toepassing)
* **config.stage** (*is op de Staging van AEM de diensten* van toepassing)
* **config.prod** (*is op de diensten van de Productie van AEM* van toepassing)

De configuratie OSGI die de meest passende looppaswijzen heeft wordt gebruikt.

Wanneer plaatselijk het ontwikkelen, wordt een looppas wijzestartparameter, `-r`, gebruikt om de loopwijzeConfiguratie te specificeren OSGI.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuratie van onderhoudstaken in Source Control {#maintenance-tasks-configuration-in-source-control}

De configuraties van de Taak van het onderhoud moeten in broncontrole worden voortgeduurd omdat het **Hulpmiddelen > het scherm van Verrichtingen** niet beschikbaar in de milieu&#39;s van de Wolk is. Dit voordeel zorgt ervoor dat veranderingen opzettelijk worden voortgeduurd eerder dan reactief worden toegepast en worden vergeten. Zie [ Taken van het Onderhoud in AEM as a Cloud Service ](/help/operations/maintenance.md) voor extra informatie.
