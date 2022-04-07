---
title: Veelgestelde vragen over Cloud Manager
description: Zoek antwoorden op de meest gestelde vragen over Cloud Manager in AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 5f4bbedaa5c4630d6f955bb0986e8b32444d6aa3
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 0%

---


# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

Dit document bevat antwoorden op de meest gestelde vragen over Cloud Manager in AEM as a Cloud Service.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11-cloud-manager}

Ja. U moet de opdracht `maven-toolchains-plugin` met de juiste instellingen voor Java 11.

* Dit wordt gedocumenteerd [hier](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).
* Zie bijvoorbeeld de [projectcode van wknwdd-project](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mijn build mislukt met een fout over maven-scr-plugin na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#build-fails-maven-scr-plugin}

Het is mogelijk dat de build van uw AEM Cloud Manager mislukt wanneer u probeert de build over te schakelen van Java 8 naar 11. Als de volgende fout optreedt, moet u `maven-scr-plugin` en zet alle OSGi-annotaties om in OSGi R6-annotaties.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
```

Voor instructies over het verwijderen van deze plug-in raadpleegt u [hier.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/)

## Mijn build mislukt met een fout met betrekking tot RequireJavaVersion na het schakelen van Java 8 naar Java 11. Wat kan ik doen? {#build-fails-requirejavaversion}

Voor builds van Cloud Manager worden de `maven-enforcer-plugin` mislukt met deze fout.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

Dit is een bekend probleem vanwege het gebruik van een andere Java-versie voor het uitvoeren van de gedeelde opdracht in plaats van het compileren van code. Eenvoudig weglaten `requireJavaVersion` van uw `maven-enforcer-plugin` configuraties.

## De kwaliteitscontrole van de code is mislukt en onze implementatie is vastgelopen. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Ja. Alle mislukte controles van de codekwaliteit behalve de veiligheidsclassificatie zijn niet-kritieke metriek, zodat kunnen zij worden omzeild door de punten in resultatenUI uit te breiden.

Zie het document [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md) voor meer informatie .

## Kan ik SNAPSHOT voor de versie van het Maven project gebruiken? {#use-snapshot}

Ja. Voor ontwikkelaarsplaatsingen, de git tak `pom.xml` bestanden moeten bevatten `-SNAPSHOT` aan het einde van de `<version>` waarde.

Dit laat verdere plaatsing toe om nog worden geïnstalleerd wanneer de versie niet veranderde. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

U kunt de versie ook instellen op `-SNAPSHOT` voor stadium- en productiegebouwen of -implementaties. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in de it. Indien nodig kunt u later naar dit label verwijzen.

## Hoe werkt het pakket en de bundelversioning bij stadium en productielokalisaties? {#snapshot-version}

In werkgebied- en productieimplementaties wordt een automatische versie gegenereerd als [Hier gedocumenteerd.](/help/implementing/cloud-manager/managing-code/project-version-handling.md)

Voor aangepaste versioning in werkgebied- en productieimplementaties stelt u een correcte versie met drie delen in, zoals `1.0.0`. Verhoog de versie telkens wanneer u aan productie opstelt.

Cloud Manager voegt automatisch zijn versie aan stadium toe en de productie bouwt en leidt tot een git tak. Er is geen speciale configuratie vereist. Als u een bepaalde versie niet zoals eerder beschreven plaatst, zal de plaatsing nog slagen en een versie zal automatisch worden geplaatst.

## Mijn gefabriceerde build mislukt voor implementaties van Cloud Manager, maar het wordt lokaal zonder fouten gemaakt. Wat is er mis? {#maven-build-fail}

Zie [deze git-resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer informatie .

## Wat doe ik als een implementatie van Cloud Manager bij de implementatiestap in AEM as a Cloud Service mislukt? {#cloud-manager-deployment-cloud-service}

De gemeenschappelijkste reden voor een plaatsing om te ontbreken is wegens ontoereikende toestemmingen voor `sling-distribution-importer` gebruiker. In deze situatie mislukt de implementatiestap tijdens een implementatie van Cloud Manager en worden fouten zoals de volgende gegenereerd.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

De `sling-distribution-importer` gebruiker heeft extra machtigingen nodig voor de inhoudspaden die zijn gedefinieerd in het dialoogvenster `ui.content package`.  Dit betekent gewoonlijk u toestemmingen voor beide moet toevoegen `/conf` en `/var`.

De oplossing is om een [Configuratie RepositoryInitializer OSGi](/help/implementing/deploying/overview.md#repoint) manuscript aan uw apps plaatsingspakket om ACLs voor toe te voegen `sling-distribution-importer` gebruiker.

In de vorige voorbeeldfout wordt het pakket `myapp-base.ui.content-*.zip` bevat inhoud onder `/conf` en `/var/workflow`. Om de plaatsing te slagen, toestemmingen voor `sling-distribution-importer` onder deze paden is het noodzakelijk .

Hier is een voorbeeld [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) van één dergelijke configuratie OSGi die extra toestemmingen voor `sling-distribution-importer` gebruiker.  Deze configuratie voegt machtigingen toe onder `/var`.  Dit XML-bestand hieronder [1] moet worden toegevoegd aan het toepassingspakket onder `/apps/myapp/config` (waarbij myapp de map is waarin uw toepassingscode is opgeslagen).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

## Mijn plaatsing van de Manager van de Wolk ontbreekt bij de opstellen stap in AEM as a Cloud Service en ik reeds een configuratie RepositoryInitializer OSGi. Wat kan ik nog meer doen? {#build-failures}

Indien [het toevoegen van een configuratie RepositoryInitializer OSGi](##cloud-manager-deployment-cloud-service) heeft de fout niet opgelost, mogelijk is dit te wijten aan een van deze extra problemen.

* De plaatsing zou wegens een slechte configuratie kunnen ontbreken OSGi die een uit-van-de doosdienst breekt.
   * Controleer de logboeken tijdens plaatsing om te zien of zijn er om het even welke duidelijke fouten.

* De implementatie zou kunnen mislukken door slechte verzender of Apache configuraties.
   * Test uw Apache- en verzendersconfiguraties lokaal met de Docker-afbeelding in de SDK.
   * Zie [Dispatcher in de cloud](/help/implementing/dispatcher/disp-overview.md#content-delivery) over hoe u de Dispatcher Docker-container instelt voor eenvoudige lokale tests.

* De implementatie zou kunnen mislukken vanwege een andere fout tijdens de replicatie van de inhoudspakketten (de distributie van het Verdelen) van auteur om instanties te publiceren.
   * Ga als volgt te werk om het probleem op een lokale installatie te simuleren.
      1. Installeer een auteur en publiceer een instantie lokaal met de nieuwste AEM SDK-jars.
      1. Meld u aan bij de instantie van de auteur.
      1. Ga naar **Gereedschappen** -> **Implementatie** -> **Distributie**.
      1. Distribueer de inhoudspakketten die deel uitmaken van de codebasis en controleer of de rij met een fout wordt geblokkeerd.

## Ik kan geen variabele plaatsen gebruikend een bevel van de lucht. Wat kan ik doen? {#set-variable}

U kunt een `403` fout zoals het volgende wanneer het proberen van pijplijnvariabelen een lijst te maken of te plaatsen via `aio` opdrachten.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In dit geval moet de gebruiker die deze opdrachten uitvoert, worden toegevoegd aan de opdracht **Implementatiebeheer** rol in de Admin Console.

Zie [API-machtigingen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) voor meer informatie .
