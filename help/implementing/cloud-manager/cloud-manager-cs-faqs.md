---
title: Cloud Manager - Veelgestelde vragen over Cloud Services
seo-title: Veelgestelde vragen over Cloud Manager
description: Raadpleeg Cloud Manager for Cloud Services Veelgestelde vragen voor tips voor het oplossen van problemen
seo-description: Volg deze pagina om antwoorden te krijgen op Cloud Manager - Veelgestelde vragen over Cloud Services
translation-type: tm+mt
source-git-commit: 75a5ff02e5f7c0e0e3ba42c8559851d3c98c3c8d
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 0%

---


# Veelgestelde vragen over wolkenbeheer {#cloud-manager-faqs}

In het volgende gedeelte worden antwoorden gegeven op veelgestelde vragen over Cloud Manager for Cloud Services.

## Is het mogelijk om Java 11 te gebruiken met Cloud Manager builds? {#java-11-cloud-manager}

AEM de build van Cloud Manager mislukt tijdens een poging om te schakelen van Java 8 naar 11. Het probleem kan vele oorzaken hebben en de meest voorkomende zijn hieronder gedocumenteerd:

* Voeg de plug-in maven-toolketins toe met de juiste instellingen voor Java 11, zoals [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/create-application-project/using-the-wizard.html?lang=en#getting-started) wordt beschreven.  Bijvoorbeeld, zie [wint steekproefprojectcode](https://github.com/adobe/aem-guides-wknd/commit/6cb5238cb6b932735dcf91b21b0d835ae3a7fe75).

* Als u hieronder de fout ontmoet dan moet u gebruik van `maven-scr-plugin` verwijderen en alle OSGi- annotaties in OSGi R6- annotaties omzetten. Zie [hier](https://cqdump.wordpress.com/2019/01/03/from-scr-annotations-to-osgi-annotations/) voor instructies.

   `[main] [ERROR] Failed to execute goal org.apache.felix:maven-scr-plugin:1.26.4:scr (generate-scr-scrdescriptor) on project helloworld.core: /build_root/build/testsite/src/main/java/com/adobe/HelloWorldServiceImpl.java : Unable to load compiled class: com.adobe.HelloWorldServiceImpl: com/adobe/HelloWorldServiceImpl has been compiled by a more recent version of the Java Runtime (class file version 55.0), this version of the Java Runtime only recognizes class file versions up to 52.0 -> [Help 1]`

* Voor het samenstellen van Cloud Manager mislukt de gemaakte plug-in voor afgedwongen naleving met fout `"[main] [WARNING] Rule 1: org.apache.maven.plugins.enforcer.RequireJavaVersion"`. Dit is een bekend probleem vanwege het gebruik van een andere Java-versie voor het uitvoeren van de gedeelde opdracht in plaats van het compileren van code. Laat op dit moment `requireJavaVersion` weg uit uw gefabriceerde-handhaving-stop- configuraties.

## Onze implementatie is vastgelopen omdat de kwaliteitscontrole voor de code is mislukt. Is er een manier om deze controle te omzeilen? {#deployment-stuck}

Alle fouten van de Kwaliteit van de Code behalve *de Classificatie van de Veiligheid* zijn niet-kritieke metriek, zodat kunnen zij worden omzeild door de punten in resultatenUI uit te breiden.

Een gebruiker met [De Manager van de Plaatsing, de Manager van het Project, of de rol Bedrijfs van de Eigenaar ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html?lang=en#requirements) kan de kwesties met voeten treden, in welk geval de pijpleiding te werk gaat of zij kunnen de kwesties goedkeuren, in welk geval de pijpleiding met een mislukking ophoudt.  Zie [Drievoudige poorten tijdens het uitvoeren van een pijplijn](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#how-to-use) voor meer informatie.


## Kunnen wij SNAPSHOT in de versie van het Maven project gebruiken? Hoe werkt het versioning van pakketten en bundeljar-bestanden voor werkgebied- en productieimplementaties? {#snapshot-version}

Raadpleeg de volgende scenario&#39;s voor meer informatie over het versieren van pakketten en bundeljar-bestanden voor werkgebied- en productieimplementaties:

1. Voor ontwikkelaarsimplementaties moeten de Git-vertakking `pom.xml`-bestanden `-SNAPSHOT` bevatten aan het einde van de waarde `<version>`. Dit staat verdere plaatsing toe waar de versie niet verandert om nog geïnstalleerd te worden. In ontwikkelaarsplaatsingen, wordt geen automatische versie toegevoegd of geproduceerd voor de beproefde bouwstijl.

1. In de plaatsing van het Stadium en van de Productie, wordt een automatische versie geproduceerd zoals gedocumenteerd [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/activating-maven-project.html?lang=en#managing-code).

1. Stel voor aangepaste versies in werkgebied- en productieimplementaties een correcte versie van drie onderdelen in, bijvoorbeeld `1.0.0`. Verhoog de versie telkens als u een andere moet doen opstelt aan productie.

1. Cloud Manager voegt automatisch zijn versie toe aan Stage en Production builds en maakt zelfs een Git-vertakking. Er is geen speciale configuratie vereist. Als stap 3 hierboven wordt overgeslagen, zou de plaatsing nog goed werken en een versie automatisch worden geplaatst.

1. Er zijn geen kwesties, als u de versie met `-SNAPSHOT` voor Stadium en Productie bouwt of plaatsingen verlaat. Cloud Manager stelt automatisch een correct versienummer in en maakt een tag voor u in Git. Indien nodig kunt u later naar dit label verwijzen.

1. Als u één of andere experimentele code op het milieu van de Ontwikkeling wilt uitproberen, kunt u een nieuwe tak van de Git tot stand brengen en de pijpleiding plaatsen om die verschillende tak te gebruiken. Dit is nuttig wanneer de plaatsingen beginnen te ontbreken en u met oudere versies van de code zou willen testen om te zien wanneer het brak.

   Met de opdracht Git hieronder maakt u een externe vertakking met de naam *testvertakking1* op basis van een specifieke, reeds bestaande koppeling `485548e4fbafbc83b11c3cb12b035c9d26b6532b`.  Deze speciale vertakking kan worden gebruikt in Cloud Manager zonder andere vertakkingen te beïnvloeden:

   `git push origin 485548e4fbafbc83b11c3cb12b035c9d26b6532b:refs/heads/testbranch1`

   Raadpleeg de [Git-documentatie](https://git-scm.com/book/en/v2/Git-Internals-Git-References) voor meer informatie.

   Als u de testtak later wilt schrappen, dan gebruik het schrappingsbevel:

   `git push origin --delete testbranch1`

## Maven-build mislukt in Cloud Manager, maar wordt lokaal zonder fouten gemaakt. Hoe kan ik fouten opsporen? {#maven-build-fail}

Zie [Git Resource](https://github.com/cqsupport/cloud-manager/blob/main/cm-build-step-fails.md) voor meer informatie.

## Wat moet u doen als de implementatie van Cloud Manager mislukt tijdens de implementatie in AEM als een Cloud Service-omgeving? {#cloud-manager-deployment-cloud-service}

De gemeenschappelijkste reden voor plaatsingen om te ontbreken is wegens ontoereikende toestemmingen voor *sling-distributie-importeur* gebruiker.
Raadpleeg het onderstaande voorbeeld voor meer informatie over een probleem, oorzaak en oplossing:

****
ProbleemTijdens een implementatie van Cloud Manager op AEM als een Cloud Service-omgeving mislukt de implementatiestap en worden fouten als hieronder waargenomen.

`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.jackrabbit.vault.fs.io.Importer Error while committing changes. Retrying import from checkpoint at /. Retries 4/10`
`[Queue Processor for Subscriber agent forwardPublisherSubscriber] org.apache.sling.distribution.journal.impl.subscriber DistributionSubscriber Error processing queue item`
`org.apache.sling.distribution.common.DistributionException: Error processing distribution package`
`dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 162/infinite.`
`Caused by: org.apache.sling.api.resource.PersistenceException: Unable to commit changes to session.`
`Caused by: javax.jcr.AccessDeniedException: OakAccess0000: Access denied [EventAdminAsyncThread #7] org.apache.sling.distribution.journal.impl.publisher.DistributionPublisher [null] Error processing distribution package` `dstrpck-1583514457813-c81e7751-2da6-4d00-9814-434187f08d32. Retry attempts 344/infinite. Message: Error trying to extract package at path /etc/packages/com.myapp/myapp-base.ui.content-5.1.0-SNAPSHOT.`

**Oorzaak**

De gebruiker van sling-distributie-importer heeft extra toestemmingen per de inhoudspaden nodig die in het pakket ui.content worden bepaald.  Dit betekent gewoonlijk wij toestemmingen voor zowel /conf als /var moeten toevoegen.

****
SolutionThe oplossing aan dit moet een  [RepositoryInitializer OSGi ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html?lang=en#deploying) configurationscript aan uw apps plaatsingspakket toevoegen om ACLs voor de sling-distributie-importergebruiker toe te voegen.
In de bovenstaande voorbeeldfout bevat het pakket myapp-base.ui.content-*.zip inhoud onder `/conf` en `/var/workflow`. Opdat de plaatsing niet zou ontbreken, zouden wij toestemmingen voor sling-distributie-importeur onder die wegen moeten toevoegen.
Hier is een voorbeeld [org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config](https://github.com/cqsupport/cloud-manager/blob/main/org.apache.sling.jcr.repoinit.RepositoryInitializer-distribution.config) van één dergelijke configuratie OSGi die extra toestemmingen voor de sling-distributie-importergebruiker toevoegt.  Deze configuratie voegt toestemmingen onder /var toe.  Dit XML-bestand onder [1] moet worden toegevoegd aan het toepassingspakket onder `/apps/myapp/config` (waarbij mijntoepassing de map is waarin uw toepassingscode is opgeslagen).
org.apache.sling.jcr.repoinit.RepositoryInitializer-DistributionService.config

1. Als *sling-distributie-importer* niet de oorzaak is, dan zou opstellen wegens een slechte configuratie OSGi kunnen ontbreken die een uit de doosdienst breekt. Controleer de logboeken tijdens plaatsing om te zien of zijn er om het even welke duidelijke fouten.

1. De implementatie kan mislukken als gevolg van een slechte verzender of apache configuraties. Test uw Apache-configuraties en Dispatcher-configuraties lokaal met de Docker-afbeelding in de SDK. Zie [Dispatcher in de cloud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/disp-overview.html?lang=en#content-delivery) voor informatie over het instellen van de Dispatcher Docker-container voor eenvoudige lokale tests.

1. De implementatie zou kunnen mislukken vanwege een andere fout tijdens de replicatie van de inhoudspakketten (sling distribution) van auteur om instanties te publiceren.

   Raadpleeg de onderstaande stappen om dit te simuleren bij een lokale installatie:

   * Een instantie Auteur en Publiceren installeren (met de nieuwste AEM SDK-jars)
   * Aanmelden bij de instantie Auteur
   * Ga naar **Extra** -> **Implementatie** -> **Distributie**
   * Distribueer de inhoudspakketten die deel uitmaken van de codebasis en controleer of de wachtrij wordt geblokkeerd door een fout

## Kan een variabele niet instellen via via een AIR-cloudmanager ingestelde pijpleidingvariabelen. Hoe te om deze kwesties te zuiveren? {#set-variable}

Als u een `403` fout wanneer het proberen om pijpleidingsvariabelen via bevelen te vermelden of te plaatsen gelijkend op hieronder, dan moet u als *Manager van de Plaatsing worden toegevoegd* het productrol van de Manager van de Wolk in de Admin Console.\
Zie [API-machtigingen](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html#!AdobeDocs/cloudmanager-api-docs/master/permissions.md) voor meer informatie.

Verwante opdrachten en fouten:

`$ aio cloudmanager:list-pipeline-variables 222`

*Fout*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-pipeline-variables 222 --variable TEST 1`

*Fout*:  `Cannot get variables: https://cloudmanager.adobe.io/api/program/111/pipeline/222/variables (403 Forbidden)`

`$ aio cloudmanager:set-environment-variables 1755 --variable TEST 1`

`setting variables... !`

*Fout*:  `Cannot set variables: https://cloudmanager.adobe.io/api/program/111/environment/222/variables (403 Forbidden)`
