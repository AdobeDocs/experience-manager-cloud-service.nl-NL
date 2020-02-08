---
title: Een AEM-connector indienen
description: Een AEM-connector indienen
translation-type: tm+mt
source-git-commit: 629de3a9f55d2e4c52ef91c9e0bb5d439aebe84f

---


Een AEM-connector indienen
===========================

Hieronder vindt u nuttige informatie over het verzenden van AEM-connectors. U dient deze informatie te lezen in combinatie met artikelen over het [implementeren](implement.md) en [onderhouden](maintain.md) van connectors.

AEM-connectors worden vermeld op de [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html).

In vorige AEM-oplossingen werd Package Manager gebruikt om connectors op verschillende AEM-instanties te installeren. Met AEM als Cloud Service worden connectors echter geïmplementeerd tijdens het CI-/CD-proces in Cloud Manager. Opdat de schakelaars worden opgesteld, moeten de schakelaars in pom.xml van het bepaalde project van verwijzingen worden voorzien.

Er zijn verschillende opties voor het opnemen van pakketten in een project:

1. Openbare opslagplaats van de partner - een partner zou het inhoudspakket in een openbaar toegankelijke beheerde opslagplaats ontvangen
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

Als de ISV-partner de aansluiting host op een voor internet toegankelijke gegevensopslagruimte (zoals Cloud Manager toegankelijk), moet de ISV de configuratie van de opslagplaats bieden waar de pom.xml kan worden geplaatst, zodat de (hierboven) vermelde connectorafhankelijkheden tijdens de build (zowel lokaal als door Cloud Manager) kunnen worden opgelost.

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

Als de ISV-partner ervoor kiest om de Connector als downloadbare bestanden te distribueren, moet de ISV instructies geven over hoe de bestanden kunnen worden geïmplementeerd in een opslagplaats voor lokale bestandssystemen die moet worden ingecheckt in Git als onderdeel van het AEM-project, zodat Cloud Manager deze afhankelijkheden kan oplossen.
