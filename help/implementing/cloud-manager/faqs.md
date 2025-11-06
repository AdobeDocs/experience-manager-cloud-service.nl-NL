---
title: Veelgestelde vragen over Cloud Manager
description: Vind antwoorden op de vaakst gestelde vragen over Cloud Manager in AEM as a Cloud Service.
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 0%

---


# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

In dit document worden antwoorden gegeven op de meest gestelde vragen over Cloud Manager in AEM as a Cloud Service.

## Is het mogelijk om Java™ 11 te gebruiken met Cloud Manager builds? {#java-11-cloud-manager}

Ja. Voeg de `maven-toolchains-plugin` toe met de juiste instellingen voor Java™ 11.

Het proces wordt gedocumenteerd - zie {de Tovenaar van de Aanmaak van het 0} Project [.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/using-the-wizard.md#getting-started)

Bijvoorbeeld, zie de [ lWKND projectcode van de projectsteekproef ](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

## Mijn build mislukt met een fout over maven-scr-plugin na het schakelen van Java™ 8 via Java™ 11. Wat kan ik doen? {#build-fails-maven-scr-plugin}

Uw AEM Cloud Manager-build kan mislukken wanneer u probeert de build over te schakelen van Java™ 8 tot en met 11. Als de volgende fout optreedt, moet u `maven-scr-plugin` verwijderen en alle OSGi-annotaties omzetten in OSGi R6-annotaties.

```text
[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 > [Help 1]
```

Voor instructies op hoe te om deze stop te verwijderen, zie [ Van SCR annotaties aan annotaties OSGI ](https://cqdump.joerghoh.de/2019/01/03/from-scr-annotations-to-osgi-annotations/).

## Mijn build mislukt met een fout met betrekking tot RequireJavaVersion na het schakelen van Java™ 8 naar Java™ 11. Wat kan ik doen? {#build-fails-requirejavaversion}

Voor Cloud Manager builds kan `maven-enforcer-plugin` mislukken met deze fout.

```text
"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion".
```

Deze fout is een bekend probleem omdat Cloud Manager een andere versie van Java™ gebruikt om de Maven-opdracht uit te voeren in plaats van code te compileren. Laat `requireJavaVersion` gewoon weg van uw `maven-enforcer-plugin` configuraties.

## De kwaliteitscontrole van de code is mislukt en de implementatie is vastgelopen. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Ja. Alle mislukte controles van de codekwaliteit behalve de veiligheidsclassificatie zijn niet-kritieke metriek. Dientengevolge, kunnen zij als deel van een plaatsingspijpleiding worden overgeslagen door de punten in resultatenUI uit te breiden.

Een gebruiker met de Manager van de Plaatsing van a [, de Manager van het Project, of de rol van BedrijfsEigenaar ](/help/onboarding/aem-cs-team-product-profiles.md#cloud-manager-product-profiles) kan de kwesties met voeten treden. In dat geval gaat de pijpleiding door of kunnen zij de kwesties aanvaarden, in welk geval de pijpleiding met een mislukking stopt.

Zie de documenten [ het Testen van de Kwaliteit van de Code ](/help/implementing/cloud-manager/code-quality-testing.md#three-tiered-gate) en [ het Vormen niet-Productiepijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#non-production-pipelines) voor meer details.

## Kan ik SNAPSHOT voor de versie van het Maven project gebruiken? {#use-snapshot}

Ja. Voor ontwikkelaarsimplementaties moeten de `pom.xml` bestanden van de grijsvertakking `-SNAPSHOT` aan het einde van de `<version>` -waarde bevatten.

Met deze waarde kan de volgende implementatie nog worden geïnstalleerd wanneer de versie niet is gewijzigd. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

U kunt de versie ook instellen op `-SNAPSHOT` voor stadium- en productiebuilds of -implementaties. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in de it. Indien nodig kunt u later naar dit label verwijzen.

Voor meer details over versie behandeling, zie [ Gemaakt Verwerking van de Versie van het Project ](/help/implementing/cloud-manager/managing-code/project-version-handling.md).

## Hoe werkt het pakket en de bundelversioning voor stadium en productieplaatsingen? {#snapshot-version}

In stadium en productieplaatsingen, wordt een automatische versie geproduceerd - zie [ Gemaakt de Behandeling van de Versie van het Project ](/help/implementing/cloud-manager/managing-code/project-version-handling.md).

Stel voor aangepaste versies in werkgebied- en productieimplementaties een geschikte versie met drie delen in, zoals `1.0.0` . Verhoog de versie telkens wanneer u aan productie opstelt.

Cloud Manager voegt automatisch zijn versie aan stadium toe en de productie bouwt en leidt tot een git tak. Er is geen speciale configuratie vereist. Als u een bepaalde versie niet zoals eerder beschreven plaatst, slaagt de plaatsing nog en een versie wordt automatisch geplaatst.

## Mijn gefabriceerde build mislukt voor Cloud Manager-implementaties, maar het wordt lokaal zonder fouten gemaakt. Wat is er mis? {#maven-build-fail}

Zie [ dit git middel ](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer details.

## Wat doe ik als een Cloud Manager-implementatie mislukt tijdens de implementatiestap in AEM as a Cloud Service? {#cloud-manager-deployment-cloud-service}

De meest voorkomende reden voor een mislukte implementatie is dat de `sling-distribution-importer` -gebruiker onvoldoende rechten heeft. In deze situatie, ontbreekt de plaatsingsstap tijdens een plaatsing van Cloud Manager en de fouten zoals het volgende worden geproduceerd.

```text
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10
[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item
org.apache.sling.distribution.common.DistributionException: Error processing distribution package
dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.
Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.
Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.
```

De gebruiker van `sling-distribution-importer` heeft extra machtigingen nodig voor de inhoudspaden die in `ui.content package` worden gedefinieerd. Deze regel houdt doorgaans in dat u machtigingen moet toevoegen voor zowel `/conf` als `/var` .

De oplossing moet a [ RepositoryInitializer OSGi configuratiescript ](/help/implementing/deploying/overview.md#repoint) aan uw apps plaatsingspakket toevoegen om ACLs voor de `sling-distribution-importer` gebruiker toe te voegen.

In de vorige voorbeeldfout bevat het pakket `myapp-base.ui.content-*.zip` inhoud onder `/conf` en `/var/workflow` . Voor een succesvolle implementatie zijn machtigingen voor de `sling-distribution-importer` onder deze paden vereist.

Hier is een voorbeeld van een [`org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config` ](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) configuratie OSGi die extra toestemmingen voor de `sling-distribution-importer` gebruiker toevoegt. De configuratie voegt machtigingen toe onder `/var` . Een dergelijke configuratie moet onder `/apps/myapp/config` aan het toepassingspakket worden toegevoegd (waarbij `myapp` de map is waarin uw toepassingscode is opgeslagen).

## Mijn plaatsing van Cloud Manager ontbreekt bij de opstellen stap in AEM as a Cloud Service en ik voegde reeds een configuratie RepositoryInitializer OSGi toe. Wat kan ik nog meer doen? {#build-failures}

Als [ toevoegend een configuratie RepositoryInitializer OSGi ](#cloud-manager-deployment-cloud-service) niet de fout oploste, kan het aan één van deze extra kwesties toe te schrijven zijn.

* De plaatsing zou wegens een slechte configuratie kunnen ontbreken OSGi die een uit-van-de-doosdienst breekt.
   * Controleer de logboeken tijdens plaatsing zodat kunt u zien of zijn er om het even welke duidelijke fouten.

* De implementatie kan mislukken als gevolg van slechte Dispatcher- of Apache-configuraties.
   * Test uw Apache- en Dispatcher-configuraties lokaal met de Docker-afbeelding in de SDK.
   * Zie [ Dispatcher in de Wolk ](/help/implementing/dispatcher/disp-overview.md#content-delivery) op hoe te opstelling de container van het Dok van Dispatcher voor gemakkelijke lokale het testen.

* De implementatie zou kunnen mislukken vanwege een andere fout tijdens de replicatie van de inhoudspakketten (de distributie van het Verdelen) van auteur om instanties te publiceren.
   * Voer de volgende stappen uit om het probleem op een lokale installatie te simuleren.
      1. Installeer een Author en een Publish instantie plaatselijk gebruikend de recentste Jars van AEM SDK.
      1. Meld u aan bij de instantie van de auteur.
      1. Ga naar **Hulpmiddelen** > **Plaatsing** > **Distributie**.
      1. Distribueer de inhoudspakketten die deel uitmaken van de codebasis en controleer of de rij met een fout wordt geblokkeerd.

## Ik kan geen variabele plaatsen gebruikend een bevel van de lucht. Wat kan ik doen? {#set-variable}

U ontvangt mogelijk een `403` -fout, zoals de volgende, wanneer u probeert pijpleidingvariabelen weer te geven of in te stellen via `aio` -opdrachten.

```shell
$ aio cloudmanager:list-pipeline-variables 222

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1

Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)

$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1

setting variables... !

Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)
```

In dit geval, moet de gebruiker die deze bevelen in werking stelt aan de **rol van de Manager van de Plaatsing** in Admin Console worden toegevoegd.

Zie [ API Toestemmingen ](https://developer.adobe.com/experience-cloud/cloud-manager/guides/getting-started/permissions/) voor meer details.
