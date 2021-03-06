---
title: Een AEM-connector verzenden
description: Een AEM-connector verzenden
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: cf3273af030a8352044dcf4f88539121249b73e7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 11%

---

Een AEM-connector verzenden
===========================

Hieronder vindt u nuttige informatie over het verzenden van AEM-connectors. U dient deze informatie te lezen in combinatie met artikelen over het [implementeren](implement.md) en [onderhouden](maintain.md) van connectors.

AEM connectors worden vermeld op het tabblad [Adobe Exchange](https://partners.adobe.com/exchangeprogram/experiencecloud).

In eerdere AEM oplossingen [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) werd gebruikt om schakelaars op diverse AEM instanties te installeren. Met AEM as a Cloud Service connectors worden echter geïmplementeerd tijdens het CI-/CD-proces in Cloud Manager. Opdat de schakelaars worden opgesteld, moeten de schakelaars in pom.xml van het bepaalde project van verwijzingen worden voorzien.

Er zijn verschillende opties voor het opnemen van pakketten in een project:

1. Openbare opslagplaats van de partner - een partner zou het inhoudspakket in een openbaar toegankelijke beheerde opslagplaats ontvangen
1. Opslagplaats met wachtwoordbeveiliging voor partners - een partner zou het inhoudspakket hosten in een met wachtwoord beveiligde gegevensopslagruimte. Zie [met wachtwoord beveiligde gegevensopslagruimten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories) voor instructies.
1. Gebundelde vervorming - in dit geval is het aansluitingspakket lokaal opgenomen in het door de klant gemaakte project.

Ongeacht waar zij worden ontvangen, moeten de pakketten als gebiedsdelen in pom.xml worden van verwijzingen voorzien, zoals die door de verkoper worden verstrekt.

```xml
<!-- UberJAR Dependency to be added to the project's Reactor pom.xml -->
<dependency>
  <groupId>com.partnername</groupId>
  <artifactId>my-artifact</artifactId>
  <version>V123</version> <!-- use the latest! -->
  <scope>provided</scope>
  <classifier>my_classifier</classifier>
</dependency>
```

Als de ISV-partner de aansluiting host op een voor internet toegankelijke (zoals Cloud Manager toegankelijk) opslagplaats, moet de ISV de configuratie van de opslagplaats bieden waar de pom.xml kan worden geplaatst, zodat de (hierboven) vermelde connectorafhankelijkheden kunnen worden opgelost tijdens het maken (zowel lokaal als door Cloud Manager).

```xml
<repository>
    <id>the-repository</id>
    <name>The Repository Where the Connector is Hosted</name>
    <url>https://repo.partnername.com/repositories/aem_connector_repo</url>
    <releases>
        <enabled>true</enabled>
        <updatePolicy>never</updatePolicy>
    </releases>
    <snapshots>
        <enabled>false</enabled>
    </snapshots>
</repository>
```

Als de ISV-partner ervoor kiest de Connector als downloadbare bestanden te distribueren, moet de ISV instructies geven over hoe de bestanden kunnen worden geïmplementeerd in een opslagplaats voor lokale bestandssystemen die moet worden ingecheckt in Git als onderdeel van het AEM-project, zodat de Cloud Manager deze afhankelijkheden kan oplossen.
