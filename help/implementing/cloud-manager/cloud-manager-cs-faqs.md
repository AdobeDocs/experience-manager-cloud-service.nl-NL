---
title: Veelgestelde vragen over Cloud Manager
description: Zoek antwoorden op de meest gestelde vragen over Cloud Manager in AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 11ac22974524293ce3e4ceaa26e59fe75ea387e6
workflow-type: tm+mt
source-wordcount: '1045'
ht-degree: 0%

---


# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

Dit document bevat antwoorden op de meest gestelde vragen over Cloud Manager in AEM as a Cloud Service.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11-cloud-manager}

Het is mogelijk dat de build van uw AEM Cloud Manager mislukt wanneer u probeert de build over te schakelen van Java 8 naar 11. Het probleem kan vele oorzaken hebben en de gemeenschappelijkste zijn gedocumenteerd in deze sectie.

* Voeg de `maven-toolchains-plugin` met de juiste instellingen voor Java 11.
   * Dit wordt gedocumenteerd [hier](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started).
   * Zie bijvoorbeeld de [projectcode van wknwdd-project](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Als de volgende fout optreedt, moet u `maven-scr-plugin` en zet alle OSGi-annotaties om in OSGi R6-annotaties.
   * Zie voor instructies [hier.](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   ```text
   [main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]
   ```

* Voor builds van Cloud Manager worden de `maven-enforcer-plugin` mislukt met fout `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Dit is een bekend probleem vanwege het gebruik van een andere Java-versie voor het uitvoeren van de gedeelde opdracht in plaats van het compileren van code. Op dit moment weglaten `requireJavaVersion` van uw `maven-enforcer-plugin` configuraties.

## De kwaliteitscontrole van de code is mislukt en onze implementatie is vastgelopen. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Alle mislukte controles van de codekwaliteit behalve de veiligheidsclassificatie zijn niet-kritieke metriek, zodat kunnen zij worden omzeild door de punten in resultatenUI uit te breiden.

Een gebruiker in de [Deployment Manager, Program Manager of Business Owner](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md) de rol kan de kwesties met voeten treden, waarin de pijpleiding te werk gaat. Deze toepassingen kunnen de kwesties ook goedkeuren, waarbij de pijpleiding met een mislukking ophoudt.

Zie het document [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md) voor meer informatie .

## Kan ik SNAPSHOT voor de versie van het Maven project gebruiken? Hoe werkt het versioning van pakketten en bundeljar-bestanden voor werkgebied- en productieimplementaties? {#snapshot-version}

De volgende scenario&#39;s hebben betrekking op pakket en bundel jar dossierversioning voor stadium en productielokaties.

* Voor ontwikkelaarsplaatsingen, de git tak `pom.xml` bestanden moeten bevatten `-SNAPSHOT` aan het einde van de `<version>` waarde.
   * Dit laat verdere plaatsing toe om nog worden geïnstalleerd wanneer de versie niet veranderde. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

* In werkgebied- en productieimplementaties wordt een automatische versie gegenereerd als [Hier gedocumenteerd.](/help/implementing/cloud-manager/managing-code/project-version-handling.md)

* Voor aangepaste versioning in werkgebied- en productieimplementaties stelt u een correcte versie met drie delen in, zoals `1.0.0`. Verhoog de versie telkens wanneer u aan productie opstelt.

* Cloud Manager voegt automatisch zijn versie aan stadium toe en de productie bouwt en leidt tot een git tak. Er is geen speciale configuratie vereist. Als u een bepaalde versie niet zoals eerder beschreven plaatst, zal de plaatsing nog slagen en een versie zal automatisch worden geplaatst.

* U kunt de versie instellen op `-SNAPSHOT` voor het stadium en de productie bouwt of plaatsingen zonder kwestie. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in de it. Indien nodig kunt u later naar dit label verwijzen.

* Als u één of andere experimentele code in een ontwikkelomgeving wilt uitproberen, kunt u een nieuwe git tak tot stand brengen en de pijpleiding plaatsen om die tak te gebruiken.
   * Dit is nuttig wanneer de plaatsingen ontbreken en u met oudere versies van de code zou willen testen om te bepalen welke verandering de mislukking veroorzaakte.

   * De git-opdracht hieronder maakt een externe vertakking met de naam `testbranch1` op basis van de bestaande `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Deze vertakking kan worden gebruikt in Cloud Manager zonder andere vertakkingen te beïnvloeden.

   ```shell
   git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1
   ```

   * Zie de [git-documentatie](https://git-scm.com/book/en/v2/Git-Internals-Git-References) voor meer informatie .

   * Als u de testtak later wilt schrappen, dan gebruik het schrappingsbevel:

   ```shell
   git push origin --delete testbranch1
   ```

## Mijn gefabriceerde build mislukt voor implementaties van Cloud Manager, maar het wordt lokaal zonder fouten gemaakt. Wat is er mis? {#maven-build-fail}

Zie [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer informatie .

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

In dit geval worden de `sling-distribution-importer` gebruiker heeft extra machtigingen nodig voor de inhoudspaden die zijn gedefinieerd in het dialoogvenster `ui.content package`.  Dit betekent gewoonlijk u toestemmingen voor beide moet toevoegen `/conf` en `/var`.

De oplossing is om een [Configuratie RepositoryInitializer OSGi](/help/implementing/deploying/overview.md#repoint) manuscript aan uw apps plaatsingspakket om ACLs voor toe te voegen `sling-distribution-importer` gebruiker.

In de vorige voorbeeldfout wordt het pakket `myapp-base.ui.content-*.zip` bevat inhoud onder `/conf` en `/var/workflow`. Om de plaatsing te slagen, toestemmingen voor `sling-distribution-importer` onder deze paden is het noodzakelijk .

Hier is een voorbeeld [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) van één dergelijke configuratie OSGi die extra toestemmingen voor `sling-distribution-importer` gebruiker.  Deze configuratie voegt machtigingen toe onder `/var`.  Dit XML-bestand hieronder [1] moet worden toegevoegd aan het toepassingspakket onder `/apps/myapp/config` (waarbij myapp de map is waarin uw toepassingscode is opgeslagen).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

Als het toevoegen van een configuratie RepositoryInitializer OSGi de fout niet oploste, kan het aan één van deze extra kwesties te wijten zijn.

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
