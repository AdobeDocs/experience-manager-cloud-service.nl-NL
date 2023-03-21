---
title: Implementeren naar AEM as a Cloud Service
description: Implementeren naar AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: 4eb7b1a32f0e266f12f67fdd2d12935698eeac95
workflow-type: tm+mt
source-wordcount: '3509'
ht-degree: 0%

---

# Implementeren naar AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Inleiding {#introduction}

De grondbeginselen van codeontwikkeling zijn in AEM as a Cloud Service vergelijkbaar met de oplossingen AEM On Premise en Managed Services. Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe AEM as a Cloud Service omgevingen. Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit is nu het enige mechanisme voor het opstellen van code aan AEM as a Cloud Service ontwikkelings, stadium, en productiemilieu&#39;s. Voor snelle functiebevestiging en het zuiveren voorafgaand aan het opstellen van die bovengenoemde milieu&#39;s, kan de code van een lokale milieu aan een worden gesynchroniseerd [Snelle ontwikkelomgeving](/help/implementing/developing/introduction/rapid-development-environments.md).

De bijwerking van de [AEM](/help/implementing/deploying/aem-version-updates.md) is altijd een afzonderlijke implementatiegebeurtenis van &#39;push&#39; [aangepaste code](#customer-releases). Op een andere manier bekeken, zouden de versies van de douanecode tegen de AEM versie moeten worden getest die op productie is aangezien dat is wat het bovenop zal worden opgesteld. AEM versies worden bijgewerkt die daarna plaatsvinden. Deze worden regelmatig en automatisch toegepast. Ze zijn bedoeld om achterwaarts compatibel te zijn met de reeds geïmplementeerde klantcode.

In de rest van dit document wordt beschreven hoe ontwikkelaars hun werkwijzen moeten aanpassen zodat zij zowel met de AEM van de Versie van de as a Cloud Service als met de updates van de klant werken.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Klantenreleases {#customer-releases}

### Codering op basis van de juiste AEM versie {#coding-against-the-right-aem-version}

Voor vorige AEM oplossingen, veranderde de huidigste AEM versie niet vaak (ruwweg jaarlijks met driemaandelijkse de dienstpakken) en de klanten zouden de productieinstanties aan de recentste snelstartversie op hun eigen tijd bijwerken, verwijzend naar API Jar. Nochtans, AEM as a Cloud Service toepassingen automatisch aan de recentste versie van AEM worden bijgewerkt vaker, zodat zou de douanecode voor interne versies tegen de recentste AEM versie moeten worden gebouwd.

Net als bij bestaande niet-cloud AEM versies, wordt een lokale, offline ontwikkeling op basis van een specifieke snelstart ondersteund en wordt verwacht dat deze in de meeste gevallen het juiste middel is om foutopsporing uit te voeren.

>[!NOTE]
>Er zijn subtiele operationele verschillen tussen de werking van de toepassing op een lokale computer en die van de Adobe Cloud. Deze architecturale verschillen moeten tijdens de lokale ontwikkeling worden gerespecteerd en kunnen bij de implementatie op de cloudinfrastructuur tot een ander gedrag leiden. Vanwege deze verschillen is het belangrijk om de uitgebreide tests uit te voeren op ontwikkelings- en werkgebiedomgevingen voordat nieuwe aangepaste code in productie wordt geïmplementeerd.

Voor het ontwikkelen van aangepaste code voor een interne release wordt de relevante versie van de [as a Cloud Service SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) moet worden gedownload en geïnstalleerd. Voor meer informatie over het gebruiken van de AEM as a Cloud Service Hulpmiddelen van de Verzender, zie [deze pagina](/help/implementing/dispatcher/disp-overview.md).

De volgende video biedt een overzicht op hoog niveau over hoe u code kunt implementeren om as a Cloud Service te AEM:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Inhoudspakketten implementeren via Cloud Manager en Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementaties via Cloud Manager {#deployments-via-cloud-manager}

Klanten implementeren aangepaste code in cloudomgevingen via Cloud Manager. Cloud Manager transformeert lokaal geassembleerde inhoudspakketten naar een artefact dat voldoet aan het Sling Feature Model (Sling Feature Model). Zo wordt een AEM as a Cloud Service toepassing beschreven wanneer deze wordt uitgevoerd in een cloudomgeving. Als gevolg hiervan worden de verpakkingen in [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) In cloudomgevingen bevat de naam &quot;cp2fm&quot; en zijn alle metagegevens verwijderd uit de getransformeerde pakketten. Er kan geen interactie met deze toepassingen plaatsvinden, wat betekent dat ze niet kunnen worden gedownload, gerepliceerd of geopend. Gedetailleerde documentatie over de converter kan [hier gevonden](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhoudspakketten die voor AEM as a Cloud Service toepassingen zijn geschreven, moeten een duidelijke scheiding hebben tussen onveranderbare en veranderbare inhoud. Cloud Manager installeert alleen de veranderbare inhoud en voert ook een bericht uit zoals:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

In de rest van deze sectie worden de samenstelling en de gevolgen van onveranderbare en veranderbare pakketten beschreven.

### Onveranderbare inhoudspakketten {#immutabe-content-packages}

Alle inhoud en code die in de onveranderlijke gegevensopslagplaats voortkomen, moeten in git worden gecontroleerd en door de Manager van de Wolk worden opgesteld. Met andere woorden, in tegenstelling tot huidige AEM oplossingen, wordt de code nooit direct opgesteld aan een lopende AEM instantie. Dit zorgt ervoor dat de code die voor een bepaalde release in een Cloud-omgeving wordt uitgevoerd, identiek is, waardoor het risico van onbedoelde codevariatie bij de productie wordt uitgesloten. Als voorbeeld, zou de configuratie OSGI aan broncontrole eerder dan beheerd bij runtime via de de configuratiemanager van de AEM Webconsole moeten worden geëngageerd.

Aangezien de toepassingsveranderingen toe te schrijven aan het blauw-Groene plaatsingspatroon door een schakelaar worden toegelaten, kunnen zij niet van veranderingen in de veranderbare bewaarplaats met uitzondering van de dienstgebruikers, hun ACLs, nodetypes en de veranderingen van de indexdefinitie afhangen.

Voor klanten met bestaande codebases is het van essentieel belang dat de in AEM documentatie beschreven herstructureringsoefening in de opslagplaats wordt doorlopen om ervoor te zorgen dat inhoud die voorheen onder de /etc. viel, naar de juiste locatie wordt verplaatst.

Voor deze codepakketten gelden enkele aanvullende beperkingen, bijvoorbeeld [installatiekoppels](https://jackrabbit.apache.org/filevault/installhooks.html) worden niet ondersteund.

## OSGI-configuratie {#osgi-configuration}

Zoals hierboven vermeld, zou de configuratie OSGI aan broncontrole eerder dan door de Webconsole moeten worden geëngageerd. Te dien einde zijn onder meer de volgende technieken van toepassing:

* De noodzakelijke wijzigingen aanbrengen in de lokale AEM van de ontwikkelaar met de configuratiemanager van de AEM webconsole en de resultaten vervolgens exporteren naar het AEM-project op het lokale bestandssysteem
* Creërend manueel de configuratie OSGI in het AEM project op het lokale dossiersysteem, het van verwijzingen voorzien van de configuratiemanager van de AEM console voor de bezitsnamen.

Lees meer over de configuratie van OSGI op [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Mabelinhoud {#mutable-content}

In sommige gevallen is het handig om wijzigingen in de inhoud voor te bereiden in bronbeheer, zodat dit kan worden geïmplementeerd door Cloud Manager wanneer een omgeving is bijgewerkt. Het kan bijvoorbeeld redelijk zijn om bepaalde basismapstructuren of regelwijzigingen in bewerkbare sjablonen toe te staan om beleid in te schakelen voor componenten die door de implementatie van de toepassing zijn bijgewerkt.

Er zijn twee strategieën om de inhoud te beschrijven die door Cloud Manager aan de veranderlijke bewaarplaats, veranderbare inhoudspakketten zal worden opgesteld en verklaringen opnieuw richt.

### Mabelinhoudspakketten {#mutable-content-packages}

De inhoud zoals de hiërarchieën van de omslagweg, de dienstgebruikers, en toegangscontroles (ACLs) worden typisch toegewijd in een bepaald archetype-Gebaseerd AEM project. De technieken omvatten het uitvoeren van AEM of het schrijven direct als XML. Tijdens het ontwikkelings- en implementatieproces verpakt Cloud Manager het resulterende veranderbare inhoudspakket. De veranderlijke inhoud wordt geïnstalleerd bij 3 verschillende tijden tijdens de opstellen fase in de pijpleiding:

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
   * Scripts (pakketten kunnen installatiekoppen activeren in verschillende stadia van het installatieproces van de pakketinstallatie. Zie de [Jackrabbit filevault-documentatie](https://jackrabbit.apache.org/filevault/installhooks.html) over het installeren van haken. Merk op dat AEM CS momenteel FileVault versie 3.4.0 gebruikt, die installatiekoppen aan admin gebruikers, systeemgebruikers, en lid van de beheerdersgroep beperkt).

Het is mogelijk de installatie van veranderbare inhoud te beperken tot auteur of te publiceren door pakketten in een install.auteur of install.publish omslag in te bedden onder `/apps`. Herstructurering om deze scheiding te weerspiegelen vond plaats in AEM 6.5 en nadere bijzonderheden over de aanbevolen projectherstructurering zijn te vinden in de [AEM 6.5-documentatie.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

>[!NOTE]
>Inhoudspakketten worden geïmplementeerd op alle omgevingstypen (dev, stage, prod). Het is niet mogelijk de implementatie te beperken tot een specifieke omgeving. Deze beperking is van toepassing om ervoor te zorgen dat een testrun van geautomatiseerde uitvoering mogelijk is. Inhoud die specifiek is voor een omgeving, moet handmatig worden geïnstalleerd via [Pakketbeheer.](/help/implementing/developing/tools/package-manager.md)

Ook, is er geen mechanisme om de veranderlijke veranderingen van het inhoudspakket terug te draaien nadat zij zijn toegepast. Als klanten een probleem ontdekken, kunnen zij verkiezen om het in hun volgende codeversie of als laatste redmiddel te bevestigen, het volledige systeem aan een punt in tijd vóór de plaatsing herstellen.

Alle meegeleverde pakketten van derden moeten worden gevalideerd als zijnde compatibel met AEM as a Cloud Service service, anders leidt de opname ervan tot een implementatiefout.

Zoals hierboven vermeld, moeten klanten met bestaande codebacons zich houden aan de herstructureringsoperatie in de repository die nodig is door de wijzigingen in de 6.5 repository die in de [AEM 6.5-documentatie.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

## Opnieuw plaatsen {#repoinit}

In de volgende gevallen verdient het de voorkeur de methode voor het handmatig coderen van expliciete inhoud te kiezen `repoinit` verklaringen in OSGI-fabrieksconfiguraties:

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

* Herpoinit leidt tot middelen bij opstarten zodat de logica het bestaan van die middelen voor vanzelfsprekend kan nemen. In de veranderlijke benadering van het inhoudspakket, worden de middelen gecreeerd na opstarten, zodat de toepassingscode die op hen baseert kan ontbreken.
* Opnieuw aanwijzen is een relatief veilige instructieset aangezien u uitdrukkelijk de te nemen actie controleert. Bovendien zijn de enige ondersteunde bewerkingen additief, met uitzondering van een paar beveiligingsgerelateerde gevallen die verwijdering van Gebruikers, Gebruikers en Groepen toestaan. Daarentegen is het expliciet schrappen van iets in de aanpak van het veranderbare inhoudspakket; als u een filter definieert, wordt alles wat aanwezig is en door een filter wordt bedekt, verwijderd. Toch moet voorzichtigheid worden betracht, aangezien er scenario&#39;s zijn waarin de aanwezigheid van nieuwe inhoud het gedrag van de toepassing kan veranderen.
* Repoinit voert snelle en atomische bewerkingen uit. De uitvoerbare inhoudspakketten in tegenstelling tot kunnen sterk afhankelijk van prestaties van de structuren die door een filter worden behandeld. Zelfs als u één knooppunt bijwerkt, kan een momentopname van een grote boomstructuur worden gemaakt.
* Het is mogelijk om opnieuw richt verklaringen op een lokaal dev milieu bij runtime te bevestigen aangezien zij zullen worden uitgevoerd wanneer de configuratie OSGi wordt geregistreerd.
* Herpointe-instructies zijn atomisch en expliciet en worden overgeslagen als de status al overeenkomt.

Wanneer de toepassing wordt geïmplementeerd in Cloud Manager, worden deze instructies onafhankelijk van de installatie van inhoudspakketten uitgevoerd.

Volg de onderstaande procedure voor het maken van instructies voor opnieuw plaatsen:

1. OSGi-configuratie toevoegen voor fabriek-PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in een configuratiemap van het project. U kunt als volgt een beschrijvende naam voor de configuratie gebruiken **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Voeg opnieuw richt verklaringen aan het manuscripteigenschap van config toe. De syntaxis en opties worden beschreven in [Verkoopdocumentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html). Let op: er moet een bovenliggende map expliciet worden gemaakt voordat de onderliggende mappen worden gemaakt. Bijvoorbeeld een expliciete creatie van `/content` voor `/content/myfolder`, vóór `/content/myfolder/mysubfolder`. Voor ACLs die op lage niveaustructuren worden geplaatst wordt het geadviseerd om die op een hoger niveau te plaatsen en met een `rep:glob` beperking.  Bijvoorbeeld `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Valideren in de lokale ontwikkelomgeving bij uitvoering.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Voor ACLs die voor knopen onder wordt bepaald `/apps` of `/libs` de uitvoering van het herpunt begint in een lege opslagplaats. De pakketten worden geïnstalleerd nadat het opnieuw richt zodat kunnen de verklaringen niet op om het even wat baseren die in de pakketten wordt bepaald maar moeten de voorwaarden zoals de ouderstructuren onder bepalen.

>[!TIP]
>
>Voor ACLs zou de verwezenlijking van diepe structuren omslachtig kunnen zijn, daarom redelijker is om ACL op een hoger niveau te bepalen en te beperken waar het via een rep:glob beperking zou moeten handelen.

Meer informatie over het opnieuw aanwijzen vindt u in het gedeelte [Verkoopdocumentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one offs&quot; voor Mutable Content Packages {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Pakketbeheer - Meerdere inhoudspakketten migreren"
>abstract="Gebruik van pakketbeheer verkennen voor gebruik waarbij een inhoudspakket moet worden geïnstalleerd als &#39;één uit&#39;, dat het importeren van specifieke inhoud van productie naar staging omvat om een productieprobleem op te lossen, het overbrengen van kleine inhoudspakketten van on-premise omgeving naar AEM Cloud-omgevingen en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en#cloud-migration" text="De tool Content Transfer"

Er zijn gebruiksgevallen waarin een inhoudspakket als &quot;één uit&quot; moet worden geïnstalleerd. Bijvoorbeeld het invoeren van specifieke inhoud van productie aan het opvoeren om een productiekwestie te zuiveren. Voor deze scenario&#39;s [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) kan worden gebruikt in AEM as a Cloud Service omgevingen.

Aangezien Package Manager een runtimeconcept is, is het niet mogelijk om inhoud of code in de onveranderlijke bewaarplaats te installeren, zodat zouden deze inhoudspakketten slechts uit veranderbare inhoud (hoofdzakelijk) moeten bestaan `/content` of `/conf`). Als het inhoudspakket inhoud bevat die gemengd is (zowel muteerbare als onveranderlijke inhoud), wordt alleen de veranderbare inhoud geïnstalleerd.

>[!IMPORTANT]
>
>De interface van Package Manager kan een **ongedefinieerd** foutbericht als een pakket langer dan 10 minuten duurt om te installeren.
>
>Dit is niet het gevolg van een fout tijdens de installatie, maar van een time-out die de Cloud Service heeft voor alle aanvragen.
>
>Probeer de installatie niet opnieuw als er een dergelijke fout optreedt. De installatie verloopt op de juiste wijze op de achtergrond. Als u de installatie opnieuw start, kunnen er conflicten optreden tijdens meerdere importprocessen tegelijk.

Eventuele inhoudspakketten die via Cloud Manager zijn geïnstalleerd (zowel veranderbaar als onveranderbaar) worden in de gebruikersinterface van AEM Package Manager bevroren weergegeven. Deze pakketten kunnen niet opnieuw worden geïnstalleerd, opnieuw worden samengesteld of zelfs worden gedownload en worden weergegeven met een **&quot;cp2fm&quot;** achtervoegsel dat aangeeft dat de installatie ervan is beheerd door Cloud Manager.

### Inclusief pakketten van derden {#including-third-party}

Het is gemeenschappelijk voor klanten om pre-gebouwde pakketten van derdebronnen zoals softwareverkopers zoals Adobe vertaalpartners te omvatten. De aanbeveling is om deze pakketten in een verre bewaarplaats te ontvangen en hen in verwijzing in `pom.xml`. Dit is mogelijk voor openbare gegevensbanken en ook voor persoonlijke gegevensbanken met wachtwoordbeveiliging, zoals beschreven in [met wachtwoord beveiligde gegevensopslagruimten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

Als het opslaan van het pakket in een externe opslagplaats niet mogelijk is, kunnen klanten in een lokale, op bestandssysteem gebaseerde Maven opslagplaats plaatsen, die aan SCM als deel van het project wordt geëngageerd en door wat van het hangt van het van verwijzingen voorzien. De gegevensopslagruimte zou in de projectpom worden gedeclareerd, zoals hieronder wordt geïllustreerd:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle meegeleverde pakketten van derden moeten voldoen aan de AEM richtlijnen voor codering en verpakking van de as a Cloud Service service die in dit artikel worden beschreven. Als dit niet gebeurt, treedt een implementatiefout op.

Het volgende Gemaakt `POM.xml` codefragment toont hoe pakketten van derden kunnen worden ingesloten in het pakket &#39;Container&#39; van het project, meestal genaamd **&#39;all&#39;** via de **filevault-package-maven-plugin** Maven plug-inconfiguratie.

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

Als AEM updates, worden de klantenversies opgesteld gebruikend een het rollen plaatsingsstrategie om de onderbreking van de auteurcluster in de juiste omstandigheden te elimineren. De algemene volgorde van gebeurtenissen is zoals hieronder beschreven, waarbij **Blauw** is de oude versie van de klantcode en **Groen** is de nieuwe versie. Met zowel Blauw als Groen wordt dezelfde versie van AEM code uitgevoerd.

* De blauwe versie is actief en er is een releasekandidaat voor Groen gemaakt en beschikbaar
* Als er nieuwe of bijgewerkte indexdefinities zijn, worden de overeenkomstige indexen verwerkt. Merk op dat de blauwe plaatsing altijd de oude indexen zal gebruiken, terwijl groen altijd de nieuwe indexen zal gebruiken.
* Groen begint terwijl blauw nog steeds werkt
* Blauw wordt uitgevoerd en gebruikt terwijl Groen via gezondheidscontroles op gereedheid wordt gecontroleerd
* Groene knopen die klaar verkeer goedkeuren en Blauwe knopen vervangen, die worden onderdrukt
* In de loop der tijd worden blauwe knooppunten vervangen door groene knooppunten totdat alleen de groene knooppunten overblijven, zodat de implementatie wordt voltooid
* Nieuwe of gewijzigde inhoud die kan worden gemuteerd, wordt geïmplementeerd

## Indexen {#indexes}

De nieuwe of gewijzigde indexen zullen een extra indexerende of re-indexerende stap veroorzaken alvorens de nieuwe (Groene) versie verkeer kan nemen. Details over indexbeheer in AEM as a Cloud Service vindt u in [dit artikel](/help/operations/indexing.md). U kunt de status van de indexeertaak controleren op de bouwstijlpagina van Cloud Manager en ontvangt een melding wanneer de nieuwe versie klaar is om verkeer te nemen.

>[!NOTE]
>
>De tijd nodig voor een het rollen plaatsing zal afhankelijk van de grootte van de index variëren, aangezien de Groene versie geen verkeer kan goedkeuren tot de nieuwe index is geproduceerd.

Op dit moment werkt AEM as a Cloud Service niet met hulpmiddelen voor indexbeheer, zoals ACS-opdrachten, voor het gereedschap eikenindex.

## Replicatie {#replication}

Het publicatiemechanisme is achterwaarts compatibel met het [Java API&#39;s voor replicatie AEM](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Voor het ontwikkelen en testen van replicatie met de cloud gereed AEM QuickStart, moeten de klassieke replicatiemogelijkheden worden gebruikt met een Auteur/Publish-instelling. Als het UI-ingangspunt op AEM Author is verwijderd voor de cloud, gaan gebruikers naar `http://localhost:4502/etc/replication` voor configuratie.

## Achterwaarts Compatibele Code voor het Draaien Plaatsingen {#backwards-compatible-code-for-rolling-deployments}

Zoals hierboven beschreven, impliceert AEM de het rollen plaatsingsstrategie van as a Cloud Service dat zowel de oude als nieuwe versies tezelfdertijd kunnen werken. Wees daarom voorzichtig met codewijzigingen die niet achterwaarts compatibel zijn met de oude AEM versie die nog steeds wordt uitgevoerd.

Bovendien moet de oude versie worden getest op compatibiliteit met eventuele nieuwe muteerbare inhoudsstructuren die door de nieuwe versie worden toegepast in geval van terugdraaiing, aangezien muteerbare inhoud niet wordt verwijderd.

### De Gebruikers van de dienst en ACL Veranderingen {#service-users-and-acl-changes}

Het veranderen van de dienstgebruikers of ACLs nodig om tot inhoud of code toegang te hebben kon tot fouten in de oudere AEM versies leiden resulterend in toegang tot die inhoud of code met verouderde de dienstgebruikers. Om dit te verhelpen, is het raadzaam om wijzigingen door minstens 2 versies te laten spreiden, waarbij de eerste release als een brug fungeert voordat de release wordt opgeschoond.

### Indexwijzigingen {#index-changes}

Als er wijzigingen in indexen worden aangebracht, is het belangrijk dat de blauw-versie de indexen blijft gebruiken totdat deze worden beëindigd, terwijl de groene versie een eigen aangepaste set indexen gebruikt. De ontwikkelaar moet de beschreven technieken voor indexbeheer volgen [in dit artikel](/help/operations/indexing.md).

### Conservatieve codering voor terugdraaiversies {#conservative-coding-for-rollbacks}

Als een mislukking na de plaatsing wordt gemeld of ontdekt, is het mogelijk dat een terugschroeven van prijzen aan de Blauwe versie zal worden vereist. Het zou verstandig zijn om ervoor te zorgen dat de blauwe code compatibel is met nieuwe structuren die door de groene versie worden gecreëerd, aangezien de nieuwe structuren (muteerbare inhoud) niet worden teruggedraaid. Als de oude code niet compatibel is, moeten fixes worden toegepast in volgende versies van de klant.

## Rapid Development Environment (RDE) {#rde}

[Snelle ontwikkelomgevingen](/help/implementing/developing/introduction/rapid-development-environments.md) (of RDEs voor kort) staat ontwikkelaars toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren nodig om eigenschappen te testen die reeds aan een lokale ontwikkelomgeving worden bewezen te werken.

In tegenstelling tot gewone ontwikkelomgevingen, die code via de pijplijn van de Manager van de Wolk opstellen, gebruiken de ontwikkelaars bevellijnhulpmiddelen om code van een lokale ontwikkelomgeving aan RDE te synchroniseren. Zodra de veranderingen met succes in een RDE zijn getest, zouden zij aan een regelmatige milieu van de Ontwikkeling van de Wolk door de pijpleiding van de Manager van de Wolk moeten worden opgesteld, die de code door de aangewezen kwaliteitsspoorten zal zetten.

## Modi uitvoeren {#runmodes}

In bestaande AEM oplossingen hebben klanten de mogelijkheid instanties uit te voeren met willekeurige uitvoeringsmodi en om OSGI-configuratie toe te passen of om OSGI-bundels op die specifieke instanties te installeren. De uitvoermodi die gewoonlijk worden gedefinieerd, omvatten de *service* (auteur en publicatie) en het milieu (rood, dev, podium, pod).

AEM as a Cloud Service is daarentegen meer mening over welke uitvoeringsmodi beschikbaar zijn en hoe OSGI-bundels en OSGI-configuratie aan hen kunnen worden toegewezen:

* De de configuratieloopwijzen van OSGI moeten RDE, dev, stadium, prod voor het milieu of auteur, publiceren voor de dienst van verwijzingen voorzien. Een combinatie van `<service>.<environment_type>` wordt gesteund terwijl deze in deze specifieke orde moeten worden gebruikt (bijvoorbeeld `author.dev` of `publish.prod`). Er moet rechtstreeks vanuit de code naar de OSGI-tokens worden verwezen in plaats van de `getRunModes` , die niet langer de `environment_type` bij uitvoering. Zie voor meer informatie [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* De de bundelloopwijzen van OSGI zijn beperkt tot de dienst (auteur, publiceer). OSGI-bundels per run-modus moeten in het inhoudspakket worden geïnstalleerd onder een van beide `install.author` of `install.publish`.

AEM as a Cloud Service staat het gebruik van uitvoeringsmodi niet toe om inhoud voor specifieke milieu&#39;s of de diensten te installeren. Als een ontwikkelomgeving moet worden voorzien van gegevens of HTML die zich niet in de testomgeving of productieomgeving bevinden, kan de pakketbeheerder worden gebruikt.

De ondersteunde runmode configuraties zijn:

* **config** (*De standaardwaarde is van toepassing op alle AEM services*)
* **config.author** (*Is van toepassing op alle AEM Auteur-service*)
* **config.signer.dev** (*Is van toepassing op AEM Dev Author-service*)
* **config.signer.rde** (*Is van toepassing op AEM RDE-auteurservice*)
* **config.maker.stage** (*Is van toepassing op AEM Staging Author-service*)
* **config.maker.prod** (*Van toepassing op AEM dienst Productieauteur*)
* **config.publish** (*Is van toepassing op de AEM-publicatieservice*)
* **config.publish.dev** (*Is van toepassing op AEM Dev Publish-service*)
* **config.publish.rde** (*Is van toepassing op AEM RDE-publicatieservice*)
* **config.publish.stage** (*Is van toepassing op AEM service Staging publiceren*)
* **config.publish.prod** (*Van toepassing op AEM publicatieservice Productie*)
* **config.dev** (*Van toepassing op AEM Dev-services*)
* **config.rde** (*Van toepassing op RDE-diensten*)
* **config.stage** (*Van toepassing op AEM-halveringsdiensten*)
* **config.prod** (*Van toepassing op AEM Productiediensten*)

De configuratie OSGI die de meest passende runmodes heeft wordt gebruikt.

Bij lokale ontwikkeling, een runtime startparameter `-r`, wordt gebruikt om de configuratie op te geven van de runmode OSGI.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuratie van onderhoudstaken in bronbeheer {#maintenance-tasks-configuration-in-source-control}

De configuraties van de Taak van het onderhoud moeten in broncontrole worden voortgeduurd aangezien **Gereedschappen > Bewerkingen** -scherm niet meer beschikbaar zijn in Cloud-omgevingen. Dit heeft het voordeel dat we ervoor zorgen dat veranderingen met opzet worden doorgevoerd in plaats van reactief te worden toegepast en misschien vergeten worden. Verwijs naar de [Onderhoudstaken, artikel](/help/operations/maintenance.md) voor aanvullende informatie.
