---
title: Cloud Manager - Veelgestelde vragen over Cloud Services
seo-title: Cloud Manager FAQs
description: Raadpleeg Cloud Manager for Cloud Services Veelgestelde vragen voor tips voor het oplossen van problemen
seo-description: Follow this page to get answers on Cloud Manager - Cloud Services FAQs
exl-id: eed148a3-4a40-4dce-bc72-c7210e8fd550
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1137'
ht-degree: 0%

---

# Veelgestelde vragen over Cloud Manager {#cloud-manager-faqs}

In het volgende gedeelte worden antwoorden gegeven op veelgestelde vragen over Cloud Manager for Cloud Services.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11-cloud-manager}

AEM de build van Cloud Manager mislukt tijdens een poging om te schakelen van Java 8 naar 11. Het probleem kan vele oorzaken hebben en de meest voorkomende zijn hieronder gedocumenteerd:

* Voeg de plug-in Gemaakt-toolketens toe met de juiste instellingen voor Java 11, zoals wordt beschreven [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started).  Zie bijvoorbeeld de [code van wknwdb-voorbeeldproject](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Als u hieronder de fout tegenkomt, moet u het gebruik van `maven-scr-plugin` en zet alle OSGi-annotaties om in OSGi R6-annotaties. Zie voor instructies [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/).

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Voor het samenstellen van Cloud Manager mislukt de gemaakte insteekmodule voor afdwingbare bestanden met een fout `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Dit is een bekend probleem vanwege het gebruik van een andere Java-versie voor het uitvoeren van de gedeelde opdracht in plaats van het compileren van code. Op dit moment weglaten `requireJavaVersion` van uw gefabriceerde afdwingbare plug-inconfiguraties.

## Onze implementatie is vastgelopen omdat de kwaliteitscontrole voor de code is mislukt. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Alle kwaliteitsfouten in de code, behalve *Beveiligingsbeoordeling* zijn niet-kritieke metriek, zodat kunnen zij worden omzeild door de punten in resultatenUI uit te breiden.

Een gebruiker met [Implementatiebeheer, projectmanager of bedrijfseigenaar](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) de rol kan de kwesties met voeten treden, waarin de pijpleiding te werk gaat of zij de kwesties kunnen goedkeuren, waarbij de pijpleiding met een mislukking stopt.  Zie [Drievoudige Gates terwijl het runnen van een Pijpleiding](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) voor meer informatie .


## Kunnen wij SNAPSHOT in de versie van het Maven project gebruiken? Hoe werkt het versioning van pakketten en bundeljar-bestanden voor werkgebied- en productieimplementaties? {#snapshot-version}

Raadpleeg de volgende scenario&#39;s voor meer informatie over het versieren van pakketten en bundeljar-bestanden voor werkgebied- en productieimplementaties:

1. Voor ontwikkelaarsplaatsingen, de tak van de it `pom.xml` bestanden moeten bevatten `-SNAPSHOT` aan het einde van de `<version>` waarde. Dit staat verdere plaatsing toe waar de versie niet verandert om nog geïnstalleerd te worden. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

1. In de implementatie van werkgebied en productie wordt een automatische versie gegenereerd zoals wordt gedocumenteerd [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Stel voor aangepaste versies in werkgebied- en productieimplementaties een correcte versie van drie onderdelen in, zoals `1.0.0`. Verhoog de versie telkens als u een andere moet doen opstelt aan productie.

1. Cloud Manager voegt automatisch zijn versie toe aan Stage en Production builds en maakt zelfs een Git-vertakking. Er is geen speciale configuratie vereist. Als stap 3 hierboven wordt overgeslagen, zou de plaatsing nog goed werken en een versie automatisch worden geplaatst.

1. Er zijn geen problemen als u de versie bij laat `-SNAPSHOT` voor Stage en Production builds of implementaties. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in Git. Indien nodig kunt u later naar dit label verwijzen.

1. Als u één of andere experimentele code op het milieu van de Ontwikkeling wilt uitproberen, kunt u een nieuwe tak van de Git tot stand brengen en de pijpleiding plaatsen om die verschillende tak te gebruiken. Dit is nuttig wanneer de plaatsingen beginnen te ontbreken en u met oudere versies van de code zou willen testen om te zien wanneer het brak.

   Met de opdracht Git hieronder maakt u een externe vertakking met de naam *testbank1* tegen een specifieke, reeds bestaande verbintenis `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Deze speciale vertakking kan worden gebruikt in Cloud Manager zonder andere vertakkingen te beïnvloeden:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Zie de [Git-documentatie](https://git-scm.com/book/en/v2/Git-Internals-Git-References) voor meer informatie .

   Als u de testtak later wilt schrappen, dan gebruik het schrappingsbevel:

   `git push origin --delete testbranch1`

## Maven-build mislukt in Cloud Manager, maar wordt lokaal zonder fouten gemaakt. Hoe kan ik fouten opsporen? {#maven-build-fail}

Zie [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer informatie .

## Wat moet u doen als de implementatie van Cloud Manager mislukt tijdens de implementatie in AEM as a Cloud Service omgeving? {#cloud-manager-deployment-cloud-service}

De gemeenschappelijkste reden voor plaatsingen om te ontbreken is wegens ontoereikende toestemmingen voor *sling-distribution-importer* gebruiker.
Raadpleeg het onderstaande voorbeeld voor meer informatie over een probleem, oorzaak en oplossing:

**Probleem**
Tijdens een implementatie van Cloud Manager in AEM as a Cloud Service omgevingen mislukt de implementatiestap en worden fouten als hieronder waargenomen.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Oorzaak**

De gebruiker van sling-distributie-importer heeft extra toestemmingen per de inhoudspaden nodig die in het pakket ui.content worden bepaald.  Dit betekent gewoonlijk wij toestemmingen voor zowel /conf als /var moeten toevoegen.

**Oplossing**
De oplossing hiervoor is het toevoegen van een [Configuratie RepositoryInitializer OSGi](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying) manuscript aan uw apps plaatsingspakket om ACLs voor de sling-distributie-importergebruiker toe te voegen.
In de bovenstaande voorbeeldfout bevat het pakket myapp-base.ui.content-*.zip inhoud onder `/conf` en `/var/workflow`. Opdat de plaatsing niet zou ontbreken, zouden wij toestemmingen voor sling-distributie-importeur onder die wegen moeten toevoegen.
Hier is een voorbeeld [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) van één dergelijke configuratie OSGi die extra toestemmingen voor de sling-distributie-importeur gebruiker toevoegt.  Deze configuratie voegt toestemmingen onder /var toe.  Dit XML-bestand hieronder [1] moet worden toegevoegd aan het toepassingspakket onder `/apps/myapp/config` (waarbij myapp de map is waarin uw toepassingscode is opgeslagen).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Als de *sling-distribution-importer* is niet de oorzaak, dan stelt zou kunnen ontbreken toe te schrijven aan een slechte configuratie OSGi die een uit de doosdienst breekt. Controleer de logboeken tijdens plaatsing om te zien of zijn er om het even welke duidelijke fouten.

1. De implementatie kan mislukken als gevolg van een slechte verzender of apache configuraties. Test uw Apache-configuraties en Dispatcher-configuraties lokaal met de Docker-afbeelding in de SDK. Zie [Dispatcher in de cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery) over hoe u de Dispatcher Docker-container instelt voor eenvoudige lokale tests.

1. De implementatie zou kunnen mislukken vanwege een andere fout tijdens de replicatie van de inhoudspakketten (sling distribution) van auteur om instanties te publiceren.

   Raadpleeg de onderstaande stappen om dit te simuleren bij een lokale installatie:

   * Een instantie Auteur en Publiceren installeren (met de nieuwste AEM SDK-jars)
   * Aanmelden bij de instantie Auteur
   * Ga naar **Gereedschappen** -> **Implementatie** -> **Distributie**
   * Distribueer de inhoudspakketten die deel uitmaken van de codebasis en controleer of de wachtrij wordt geblokkeerd door een fout

## Kan een variabele niet instellen via via een AIR-cloudmanager ingestelde pijpleidingvariabelen. Hoe te om deze kwesties te zuiveren? {#set-variable}

Als u een `403` fout wanneer het proberen om pijpleidingsvariabelen via bevelen te maken of te plaatsen gelijkend op hieronder, dan moet u als a worden toegevoegd *Implementatiebeheer* De productrol van Cloud Manager in de Admin Console.\
Zie [API-machtigingen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) voor meer informatie .

Verwante opdrachten en fouten:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fout*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fout*: `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fout*: `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
