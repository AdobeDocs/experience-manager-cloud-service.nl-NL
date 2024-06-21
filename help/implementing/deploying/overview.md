---
title: Distribueren naar AEM as a Cloud Service
description: Leer over de grondbeginselen en beste praktijken van plaatsing aan AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
role: Admin
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '3429'
ht-degree: 0%

---

# Distribueren naar AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Inleiding {#introduction}

De grondbeginselen van codeontwikkeling zijn in AEM as a Cloud Service vergelijkbaar met de oplossingen AEM On Premise en Managed Services. Ontwikkelaars schrijven code en testen deze lokaal, wat vervolgens wordt doorgegeven aan externe omgevingen op AEM as a Cloud Service. Cloud Manager, een optioneel hulpprogramma voor het leveren van inhoud voor Managed Services, is vereist. Dit leveringshulpmiddel is nu het enige mechanisme voor het opstellen van code aan AEM as a Cloud Service ontwikkelings, stadium, en productiemilieu&#39;s. Voor snelle functiebevestiging en het zuiveren alvorens die eerder genoemde milieu&#39;s op te stellen, kan de code van een lokale milieu aan een worden gesynchroniseerd [Snelle ontwikkelomgeving](/help/implementing/developing/introduction/rapid-development-environments.md).

De bijwerking van de [AEM](/help/implementing/deploying/aem-version-updates.md) is altijd een afzonderlijke implementatiegebeurtenis van &#39;push&#39; [aangepaste code](#customer-releases). Op een andere manier bekeken, zouden de versies van de douanecode tegen de AEM versie moeten worden getest die op productie is omdat dat is wat het op de bovenkant wordt opgesteld. AEM versies die daarna plaatsvinden, die regelmatig voorkomen en automatisch worden toegepast. Ze zijn bedoeld om achterwaarts compatibel te zijn met de reeds geïmplementeerde klantcode.

In de rest van dit document wordt beschreven hoe ontwikkelaars hun werkwijzen moeten aanpassen zodat ze zowel met de AEM van de Versie van de as a Cloud Service als met de updates van de klant werken.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Klantenreleases {#customer-releases}

### Codering op basis van de juiste AEM versie {#coding-against-the-right-aem-version}

Voor vorige AEM oplossingen, veranderde de huidigste AEM versie niet vaak (ruwweg jaarlijks met driemaandelijkse de dienstpakken) en de klanten zouden de productieinstanties aan de recentste snelstartversie op hun eigen tijd bijwerken, verwijzend naar API Jar. Toepassingen op AEM as a Cloud Service worden echter vaker automatisch bijgewerkt naar de nieuwste versie van AEM, zodat aangepaste code voor interne releases moet worden gebaseerd op de nieuwste AEM versie.

Net als bij bestaande niet-cloud AEM versies, wordt een lokale, offline ontwikkeling ondersteund op basis van een specifieke QuickStart en wordt verwacht dat deze ontwikkeling het meest geschikte middel is voor foutopsporing.

>[!NOTE]
>Er zijn subtiele operationele verschillen tussen de werking van de toepassing op een lokale computer en die van de Adobe Cloud. Deze architecturale verschillen moeten tijdens de lokale ontwikkeling worden gerespecteerd en kunnen bij de implementatie op de cloudinfrastructuur tot een ander gedrag leiden. Vanwege deze verschillen is het belangrijk om de uitgebreide tests uit te voeren op ontwikkelings- en werkgebiedomgevingen voordat nieuwe aangepaste code in productie wordt geïmplementeerd.

Als u aangepaste code voor een interne release wilt ontwikkelen, moet u de relevante versie van de [AS A CLOUD SERVICE SDK AEM](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) moet worden gedownload en geïnstalleerd. Voor meer informatie over het gebruiken van de AEM as a Cloud Service Hulpmiddelen van de Verzender, zie [deze pagina](/help/implementing/dispatcher/disp-overview.md).

De volgende video verstrekt een overzicht op hoog niveau over hoe te om code op te stellen om as a Cloud Service te AEM:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Inhoudspakketten implementeren via Cloud Manager en Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementaties via Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Klanten implementeren aangepaste code in cloudomgevingen via Cloud Manager. Cloud Manager transformeert lokaal geassembleerde inhoudspakketten naar een artefact dat voldoet aan het Sling Feature Model, dat is hoe een toepassing op AEM as a Cloud Service wordt beschreven wanneer deze wordt uitgevoerd in een cloudomgeving. Als gevolg hiervan worden de verpakkingen in [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) In cloudomgevingen bevat de naam &quot;cp2fm&quot; en zijn alle metagegevens verwijderd uit de getransformeerde pakketten. Er kan geen interactie met deze toepassingen plaatsvinden, wat betekent dat ze niet kunnen worden gedownload, gerepliceerd of geopend. Gedetailleerde documentatie over de converter kan worden weergegeven [hier gevonden](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhoudspakketten die zijn geschreven voor toepassingen op AEM as a Cloud Service, moeten een duidelijke scheiding hebben tussen onveranderbare en meerbare inhoud en Cloud Manager installeert alleen de inhoud die kan worden gemuild, en voert ook een bericht uit zoals hieronder:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

De rest van deze sectie beschrijft de samenstelling en implicaties van onveranderbare en veranderbare pakketten.

### Onveranderbare inhoudspakketten {#immutabe-content-packages}

Alle inhoud en code die in de onveranderlijke gegevensopslagplaats voortkomen, moeten in git worden gecontroleerd en door de Manager van de Wolk worden opgesteld. Met andere woorden, in tegenstelling tot huidige AEM oplossingen, wordt de code nooit direct opgesteld aan een lopende AEM instantie. Deze workflow zorgt ervoor dat de code die voor een bepaalde release in een Cloud-omgeving wordt uitgevoerd, identiek is, waardoor het risico van onbedoelde codevariatie tijdens de productie wordt uitgesloten. Als voorbeeld, zou de configuratie OSGI aan broncontrole eerder dan beheerd bij runtime door middel van de de configuratiemanager van de AEM Webconsole moeten worden geëngageerd.

Aangezien de toepassingsveranderingen toe te schrijven aan het plaatsingspatroon door een schakelaar worden toegelaten, kunnen zij niet van veranderingen in de veranderbare bewaarplaats behalve de dienstgebruikers, hun ACLs, nodetypes, en de veranderingen van de indexdefinitie afhangen.

Voor klanten met bestaande codebases is het van essentieel belang dat de in AEM documentatie beschreven herstructureringsoefening in de opslagplaats wordt doorlopen om ervoor te zorgen dat inhoud die voorheen onder de /etc. viel, naar de juiste locatie wordt verplaatst.

Voor deze codepakketten gelden bijvoorbeeld enkele aanvullende beperkingen: [installatiekoppels](https://jackrabbit.apache.org/filevault/installhooks.html) worden niet ondersteund.

## OSGI-configuratie {#osgi-configuration}

Zoals hierboven vermeld, zou de configuratie OSGI aan broncontrole eerder dan door de Webconsole moeten worden geëngageerd. Te dien einde zijn onder meer de volgende technieken van toepassing:

* De noodzakelijke wijzigingen aanbrengen in de lokale AEM van de ontwikkelaar met de configuratiemanager van de AEM webconsole en de resultaten vervolgens exporteren naar het AEM-project op het lokale bestandssysteem
* Creërend manueel de configuratie OSGI in het AEM project op het lokale dossiersysteem, het van verwijzingen voorzien van de configuratiemanager van de AEM console voor de bezitsnamen.

Lees meer over de configuratie van OSGI op [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Mabelinhoud {#mutable-content}

Soms is het handig om inhoudswijzigingen voor te bereiden in bronbeheer, zodat dit kan worden geïmplementeerd door Cloud Manager wanneer een omgeving is bijgewerkt. Het kan bijvoorbeeld redelijk zijn om bepaalde basismapstructuren uit te breiden. Of, regelup veranderingen in editable malplaatjes om beleidscomponenten toe te laten die door de toepassingsplaatsing werden bijgewerkt.

Er zijn twee strategieën om de inhoud te beschrijven die door Cloud Manager aan de veranderbare bewaarplaats, veranderbare inhoudspakketten wordt opgesteld en `repoinit` instructies.

### Tabelinhoudspakketten {#mutable-content-packages}

De inhoud zoals de hiërarchieën van de omslagweg, de dienstgebruikers, en toegangscontroles (ACLs) worden typisch toegewijd in een bepaald archetype-Gebaseerd AEM project. De technieken omvatten het uitvoeren van AEM of het schrijven direct als XML. Tijdens het ontwikkelings- en implementatieproces verpakt Cloud Manager het resulterende veranderbare inhoudspakket. De veranderlijke inhoud wordt geïnstalleerd bij drie verschillende tijden tijdens de opstellen fase in de pijpleiding:

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
   * Scripts (pakketten kunnen installatiekoppen activeren in verschillende stadia van het installatieproces van de pakketinstallatie. Zie [Jackrabbit filevault-documentatie](https://jackrabbit.apache.org/filevault/installhooks.html) over het installeren van haken. AEM CS gebruikt momenteel FileVault versie 3.4.0, die installatiekoppen beperkt tot beheerders, systeemgebruikers, en lid van de beheerdersgroep).

Het is mogelijk de installatie van veranderbare inhoud te beperken tot auteur of te publiceren door pakketten in een install.auteur of install.publish omslag in te bedden `/apps`. Herstructurering om deze scheiding te weerspiegelen vond plaats in AEM 6.5 en nadere bijzonderheden over de aanbevolen projectherstructurering zijn te vinden in de [AEM 6.5-documentatie.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

>[!NOTE]
>Inhoudspakketten worden geïmplementeerd op alle omgevingstypen (dev, stage, prod). Het is niet mogelijk de implementatie te beperken tot een specifieke omgeving. Deze beperking is van toepassing om ervoor te zorgen dat een testrun van geautomatiseerde uitvoering mogelijk is. Voor inhoud die specifiek is voor een omgeving is handmatige installatie vereist via [Pakketbeheer](/help/implementing/developing/tools/package-manager.md).

Er is ook geen mechanisme om wijzigingen in het veranderbare inhoudspakket terug te draaien nadat deze zijn toegepast. Als klanten een probleem ontdekken, kunnen zij verkiezen om het in hun volgende codeversie of als laatste redmiddel te bevestigen, het volledige systeem aan een punt in tijd vóór de plaatsing herstellen.

Alle meegeleverde pakketten van derden moeten worden gevalideerd als zijnde AEM as a Cloud Service compatibel, anders leidt de opname ervan tot een implementatiefout.

Zoals hierboven vermeld, dienen klanten met bestaande codebacons te voldoen aan de herstructureringsexercitie van de repository die nodig is voor de wijzigingen in de 6.5 repository die worden beschreven in de [AEM 6.5-documentatie.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html)

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

* `Repoinit` leidt tot middelen bij opstarten zodat de logica het bestaan van die middelen voor vanzelfsprekend kan nemen. In de veranderlijke benadering van het inhoudspakket, worden de middelen gecreeerd na opstarten, zodat de toepassingscode die op hen baseert kan ontbreken.
* `Repoinit` is een relatief veilige instructieset aangezien u uitdrukkelijk de te nemen actie controleert. Bovendien zijn de enige ondersteunde bewerkingen additief, behalve enkele beveiligingsgerelateerde gevallen die verwijdering van Gebruikers, Gebruikers en Groepen toestaan. Een verwijdering van iets in de methode voor het muteerbare inhoudspakket is daarentegen expliciet. Wanneer u een filter definieert, wordt alle aanwezige elementen die door een filter worden gedekt, verwijderd. Toch moet voorzichtigheid worden betracht, aangezien er scenario&#39;s zijn waarin de aanwezigheid van nieuwe inhoud het gedrag van de toepassing kan veranderen.
* `Repoinit` voert snelle en atomische bewerkingen uit. De uitvoerbare inhoudspakketten in tegenstelling tot kunnen sterk afhankelijk van prestaties van de structuren die door een filter worden behandeld. Zelfs als u één knooppunt bijwerkt, kan een momentopname van een grote boomstructuur worden gemaakt.
* Het is mogelijk om te valideren `repoinit` verklaringen over een lokaal dev milieu bij runtime omdat zij in werking worden gesteld wanneer de configuratie OSGi wordt geregistreerd.
* `Repoinit` instructies zijn atomisch en expliciet en worden overgeslagen als de status al overeenkomt.

Wanneer de toepassing wordt geïmplementeerd in Cloud Manager, worden deze instructies onafhankelijk van de installatie van inhoudspakketten uitgevoerd.

Om te creëren `repoinit` de verklaringen, volgen de hieronder procedure:

1. OSGi-configuratie toevoegen voor fabriek-PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in een configuratiemap van het project. Gebruik als een beschrijvende naam voor de configuratie **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Toevoegen `repoinit` verklaringen aan het manuscripteigenschap van config. De syntaxis en opties worden beschreven in [Verkoopdocumentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html). Er moet een bovenliggende map expliciet worden gemaakt voordat de onderliggende mappen worden gemaakt. Bijvoorbeeld een expliciete creatie van `/content` voor `/content/myfolder`, vóór `/content/myfolder/mysubfolder`. Voor ACLs die op laag-vlakke structuren worden geplaatst, wordt het geadviseerd om hen op een hoger niveau te plaatsen en met a te werken `rep:glob` beperking. Bijvoorbeeld: `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Valideren in de lokale ontwikkelomgeving bij uitvoering.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Voor ACLs die voor knopen onder wordt bepaald `/apps` of `/libs` de `repoinit`, wordt de uitvoering gestart in een lege opslagplaats. De pakketten worden geïnstalleerd nadat `repoinit` instructies kunnen dus niet vertrouwen op iets dat in de pakketten is gedefinieerd , maar moeten de voorwaarden definiëren , zoals de bovenliggende structuren eronder .

>[!TIP]
>
>Voor ACLs, zou de verwezenlijking van diepe structuren omslachtig kunnen zijn. Daarom is het redelijker om ACL op een hoger niveau te bepalen en te beperken waar het verondersteld wordt om als `rep:glob` beperking.

Meer informatie over `repoinit` kunt u vinden in het dialoogvenster [Verkoopdocumentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one offs&quot; voor Mutable Content Packages {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Pakketbeheer - Meerdere inhoudspakketten migreren"
>abstract="Verken het gebruik van Package Manager voor gebruik waarbij een inhoudspakket moet worden geïnstalleerd als &#39;one off&#39;. De installatie omvat het invoeren van specifieke inhoud van productie aan het opvoeren om een productieprobleem te zuiveren, het overbrengen van klein inhoudspakket van het milieu op-gebouw aan AEM milieu&#39;s van de Wolk, en meer."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html" text="Inhoud overbrengen"

Er zijn gebruiksgevallen waarin een inhoudspakket als &quot;één uit&quot; moet worden geïnstalleerd. Bijvoorbeeld, het invoeren van specifieke inhoud van productie aan het opvoeren om een productiekwestie te zuiveren. Voor deze scenario&#39;s [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) kan in milieu&#39;s op AEM as a Cloud Service worden gebruikt.

Aangezien Package Manager een runtimeconcept is, is het niet mogelijk om inhoud of code in de onveranderlijke bewaarplaats te installeren, zodat zouden deze inhoudspakketten slechts uit veranderbare inhoud (hoofdzakelijk) moeten bestaan `/content` of `/conf`). Als het inhoudspakket inhoud bevat die gemengd is (zowel muteerbare als onveranderlijke inhoud), wordt alleen de veranderbare inhoud geïnstalleerd.

>[!IMPORTANT]
>
>De gebruikersinterface van Package Manager kan een **ongedefinieerd** foutbericht als een pakket langer duurt dan tien minuten om te installeren.
>
>Deze tijd is niet het gevolg van een fout met de installatie, maar van een time-out die de Cloud Service heeft voor alle aanvragen.
>
>Probeer de installatie niet opnieuw als er een dergelijke fout optreedt. De installatie verloopt op de juiste wijze op de achtergrond. Als u de installatie opnieuw start, kunnen er conflicten optreden tijdens meerdere importprocessen tegelijk.

Alle inhoudspakketten die via Cloud Manager worden geïnstalleerd (zowel veranderbaar als onveranderbaar) worden in de gebruikersinterface van AEM Package Manager bevroren weergegeven. Deze pakketten kunnen niet opnieuw worden geïnstalleerd, opnieuw worden samengesteld of zelfs worden gedownload en worden weergegeven met een **&quot;cp2fm&quot;** achtervoegsel dat aangeeft dat de installatie ervan is beheerd door Cloud Manager.

### Inclusief pakketten van derden {#including-third-party}

Het is gebruikelijk voor klanten om vooraf gebouwde pakketten van derdebronnen zoals softwareverkopers zoals de vertaalpartners van de Adobe te omvatten. De aanbeveling is om deze pakketten in een verre bewaarplaats te ontvangen en hen in verwijzing in `pom.xml`. Deze methode is mogelijk voor openbare gegevensbanken en ook voor persoonlijke gegevensbanken met wachtwoordbeveiliging, zoals beschreven in [met wachtwoord beveiligde gegevensopslagruimten](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

Als het opslaan van het pakket in een externe opslagplaats niet mogelijk is, kunnen klanten in een lokale, op bestandssysteem gebaseerde Maven-opslagplaats plaatsen, die als onderdeel van het project aan SCM is toegewezen. Er wordt naar verwezen door wat er van afhangt. De gegevensopslagruimte wordt gedeclareerd in de projectpom, zoals hieronder wordt geïllustreerd:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle meegeleverde pakketten van derden moeten zich houden aan AEM as a Cloud Service coderings- en verpakkingsrichtlijnen die in dit artikel worden beschreven, anders leidt de opname ervan tot een implementatiefout.

Het volgende Gemaakt `POM.xml` het fragment toont hoe de derdepakketten in het &quot;Container&quot;pakket van het project kunnen worden ingebed, typisch genoemd **&#39;all&#39;** door **filevault-package-maven-plugin** Maven plug-inconfiguratie.

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

Als AEM updates, worden de klantenversies opgesteld gebruikend een het rollen plaatsingsstrategie om de onderbreking van de auteurcluster in de juiste omstandigheden te elimineren. De algemene volgorde van gebeurtenissen wordt hieronder beschreven, waarbij knooppunten met zowel de oude als de nieuwe versie van de klantcode dezelfde versie van AEM code uitvoeren.

* De knopen met de oude versie zijn actief en een versiekandidaat voor de nieuwe versie wordt gebouwd en beschikbaar gesteld.
* Als er nieuwe of bijgewerkte indexdefinities zijn, worden de overeenkomstige indexen verwerkt. Knooppunten met de oude versie gebruiken altijd de oude indexen, terwijl knooppunten met de nieuwe versie altijd de nieuwe indexen gebruiken.
* De knopen met de nieuwe versieopstarten, terwijl de oude versies nog verkeer dienen.
* Knooppunten met de oude versie worden uitgevoerd en blijven werken terwijl knooppunten met de nieuwe versie door middel van gezondheidscontroles op gereedheid worden gecontroleerd.
* De knopen met de nieuwe versie die klaar zijn, goedkeuren verkeer, en vervangen de knopen door de oude versie, die worden gebracht.
* In tijd, worden de knopen met de oude versie vervangen door knopen met de nieuwe versie tot slechts knopen met nieuwe versies overblijven, waarbij de plaatsing wordt voltooid.
* Alle nieuwe of gewijzigde veranderbare inhoud wordt vervolgens geïmplementeerd.

## Indexen {#indexes}

Nieuwe of gewijzigde indexen veroorzaken een extra indexerende of herindexerende stap alvorens de nieuwe versie verkeer kan nemen. Details over indexbeheer in AEM as a Cloud Service vindt u in [dit artikel](/help/operations/indexing.md). U kunt de indexeringsstatus van bouwstijlpagina&#39;s controleren in Cloud Manager, en een bericht ontvangen wanneer de nieuwe versie klaar is om verkeer te nemen.

>[!NOTE]
>
>De tijd nodig voor een het rollen plaatsing varieert afhankelijk van de grootte van de index. De reden is dat de nieuwe versie geen verkeer kan goedkeuren tot de nieuwe index wordt geproduceerd.

Op dit moment werkt AEM as a Cloud Service niet met hulpmiddelen voor indexbeheer, zoals ACS-opdrachten, voor het gereedschap eikenindex.

## Replicatie {#replication}

Het publicatiemechanisme is achterwaarts compatibel met het [Java™ API&#39;s voor replicatie AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html).

Voor het ontwikkelen en testen van replicatie met de cloud gereed AEM QuickStart, moeten de klassieke replicatiemogelijkheden worden gebruikt met een Auteur/Publish-installatie. Als het ingangspunt voor de gebruikersinterface van AEM auteur is verwijderd voor de cloud, gaan gebruikers naar `http://localhost:4502/etc/replication` voor configuratie.

## Achterwaarts Compatibele Code voor het Draaien Plaatsingen {#backwards-compatible-code-for-rolling-deployments}

Zoals hierboven beschreven, impliceert AEM de het rollen plaatsingsstrategie van as a Cloud Service dat zowel de oude als nieuwe versies tezelfdertijd kunnen werken. Wees daarom voorzichtig met codewijzigingen die niet achterwaarts compatibel zijn met de oude AEM versie die nog steeds wordt uitgevoerd.

Bovendien moet de oude versie worden getest op compatibiliteit met eventuele nieuwe, door de nieuwe versie toegepaste structuren voor veranderbare inhoud als er sprake is van terugdraaiing, omdat gemuteerde inhoud niet wordt verwijderd.

### De Gebruikers van de dienst en ACL Veranderingen {#service-users-and-acl-changes}

Het veranderen van de dienstgebruikers, of ACLs die tot inhoud of code toegang hebben, kon tot fouten in de oudere AEM versies leiden resulterend in toegang tot die inhoud of code met verouderde de dienstgebruikers. Om dit gedrag aan te pakken, wordt aanbevolen wijzigingen door ten minste twee releases te laten doorlopen, waarbij de eerste release als een koppeling fungeert voordat deze wordt opgeschoond in de volgende release.

### Indexwijzigingen {#index-changes}

Als er wijzigingen in indexen worden aangebracht, is het belangrijk dat de nieuwe versie de indexen blijft gebruiken totdat deze worden beëindigd, terwijl de oude versie een eigen aangepaste set indexen gebruikt. De ontwikkelaar moet de beschreven technieken voor indexbeheer volgen [in dit artikel](/help/operations/indexing.md).

### Conservatieve codering voor terugdraaiversies {#conservative-coding-for-rollbacks}

Als een mislukking na de plaatsing wordt gemeld of ontdekt, is het mogelijk dat het terugschroeven van prijzen aan de oude versie wordt vereist. Zorg ervoor dat de nieuwe code compatibel is met eventuele nieuwe structuren die door die nieuwe versie worden gemaakt, aangezien de nieuwe structuren (alle veranderbare inhoud) niet worden teruggedraaid. Als de oude code niet compatibel is, moeten fixes worden toegepast in verdere versies van de klant.

## Rapid Development Environment (RDE) {#rde}

[Snelle ontwikkelomgevingen](/help/implementing/developing/introduction/rapid-development-environments.md) (of RDEs voor kort) staat ontwikkelaars toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren noodzakelijk om eigenschappen te testen die reeds aan een lokale ontwikkelomgeving worden bewezen te werken.

In tegenstelling tot gewone ontwikkelomgevingen, die code als pijplijn van de Manager van de Wolk opstellen, gebruiken de ontwikkelaars bevel-lijn hulpmiddelen om code van een lokale ontwikkelomgeving aan RDE te synchroniseren. Nadat de wijzigingen met succes zijn getest in een RDE, implementeert u deze in een gewone Cloud Development-omgeving via de Cloud Manager-pijplijn, waardoor de code door de juiste kwaliteitskates wordt geleid.

## Modi uitvoeren {#runmodes}

In bestaande AEM oplossingen hebben klanten de mogelijkheid instanties uit te voeren met willekeurige uitvoeringsmodi en om OSGI-configuratie toe te passen of om OSGI-bundels op die specifieke instanties te installeren. De uitvoermodi die gewoonlijk worden gedefinieerd, omvatten de *service* (auteur en publicatie) en het milieu (rood, dev, podium, pod).

AEM as a Cloud Service is daarentegen meer mening over welke uitvoeringsmodi beschikbaar zijn en hoe de OSGI-bundels en de OSGI-configuratie aan hen kunnen worden toegewezen:

* De de configuratieloopwijzen van OSGI moeten RDE, ontwikkeling, stadium, productie voor het milieu of auteur, publiceren voor de dienst van verwijzingen voorzien. Een combinatie van `<service>.<environment_type>` wordt ondersteund, terwijl deze omgevingen in deze specifieke volgorde moeten worden gebruikt (bijvoorbeeld `author.dev` of `publish.prod`). Er moet rechtstreeks vanuit de code naar de OSGI-tokens worden verwezen in plaats van de `getRunModes` , die niet langer de `environment_type` bij uitvoering. Zie voor meer informatie [Het vormen OSGi voor AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* De de bundelloopwijzen van OSGI zijn beperkt tot de dienst (auteur, publiceer). OSGI-bundels per run-modus moeten in het inhoudspakket worden geïnstalleerd onder een van beide `install.author` of `install.publish`.

AEM as a Cloud Service staat het gebruik van uitvoeringsmodi niet toe om inhoud voor specifieke milieu&#39;s of de diensten te installeren. Als een ontwikkelomgeving moet worden voorzien van gegevens of HTML die zich niet in de het opvoeren of productie milieu&#39;s bevinden, kan de Manager van het Pakket worden gebruikt.

De ondersteunde configuraties in de uitvoeringsmodus zijn:

* **config** (*De standaardwaarde is van toepassing op alle AEM services*)
* **config.author** (*Is van toepassing op alle AEM Auteur-service*)
* **config.signer.dev** (*Is van toepassing op AEM Dev Author-service*)
* **config.signer.rde** (*Is van toepassing op AEM RDE-auteurservice*)
* **config.maker.stage** (*Is van toepassing op AEM Staging Author-service*)
* **config.maker.prod** (*Van toepassing op AEM dienst Productieauteur*)
* **config.publish** (*Is van toepassing op AEM Publish-service*)
* **config.publish.dev** (*Is van toepassing op AEM Dev Publish-service*)
* **config.publish.rde** (*Is van toepassing op AEM RDE Publish-service*)
* **config.publish.stage** (*Is van toepassing op AEM Staging Publish-service*)
* **config.publish.prod** (*Van toepassing op AEM Production Publish-service*)
* **config.dev** (*Van toepassing op AEM Dev-services*)
* **config.rde** (*Van toepassing op RDE-diensten*)
* **config.stage** (*Van toepassing op AEM-halveringsdiensten*)
* **config.prod** (*Van toepassing op AEM Productiediensten*)

De configuratie OSGI die de meest passende looppaswijzen heeft wordt gebruikt.

Bij lokale ontwikkeling, een looppas wijzestartparameter `-r`, wordt gebruikt om de configuratie van de looppas wijzeOSGI te specificeren.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Configuratie van onderhoudstaken in bronbeheer {#maintenance-tasks-configuration-in-source-control}

De configuraties van de Taak van het onderhoud moeten in broncontrole worden voortgeduurd omdat **Opties > Bewerkingen** scherm is niet beschikbaar in Cloud-omgevingen. Dit voordeel zorgt ervoor dat veranderingen opzettelijk worden voortgeduurd eerder dan reactief worden toegepast en worden vergeten. Zie [Onderhoudstaken, artikel](/help/operations/maintenance.md) voor aanvullende informatie.
