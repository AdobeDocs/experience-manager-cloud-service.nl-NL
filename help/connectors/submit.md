---
title: Een AEM-connector verzenden
description: Leer hoe u in Adobe Experience Manager (AEM) as a Cloud Service naar connectors kunt verwijzen en deze kunt implementeren.
exl-id: 9be1f00e-3666-411c-9001-c047e90b6ee5
source-git-commit: 78ead5f15c2613d9c3bed3025b43423a66805c59
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 2%

---

# Een AEM-connector verzenden

Hieronder vindt u nuttige informatie over het verzenden van Adobe Experience Manager (AEM) Connectors en deze informatie moet worden gelezen met artikelen over [uitvoeren](implement.md) en  [handhaven](maintain.md) connectors.

AEM connectors worden vermeld op het tabblad [Adobe Exchange](https://partners.adobe.com/technologyprogram/experiencecloud.html).

In eerdere AEM oplossingen [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) werd gebruikt om schakelaars op diverse AEM instanties te installeren. Met AEM as a Cloud Service connectors worden echter geïmplementeerd tijdens het CI-/CD-proces in Cloud Manager. Voor de schakelaars die moeten worden opgesteld, moeten de schakelaars in pom.xml van het bepaalde project van verwijzingen worden voorzien.

Er zijn verschillende opties voor het opnemen van pakketten in een project:

1. Openbare opslagplaats van de partner - een partner zou het inhoudspakket in een openbaar toegankelijke beheerde opslagplaats ontvangen
1. Opslagplaats met wachtwoordbeveiliging voor partners - een partner zou het inhoudspakket hosten in een met wachtwoord beveiligde gegevensopslagruimte. Zie [met wachtwoord beveiligde gegevensopslagruimten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/create-application-project/setting-up-project.html?lang=en#password-protected-maven-repositories) voor instructies.
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

Als de ISV-partner de aansluiting host op een gegevensopslagruimte die toegankelijk is voor internet (zoals Cloud Manager), moet de ISV de configuratie van de opslagplaats bieden waar de `pom.xml` kan worden geplaatst. De reden hiervoor is dat de verbindingsafhankelijkheden (boven) kunnen worden opgelost tijdens het samenstellen, zowel lokaal als via Cloud Manager.

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

Als de ISV partner verkiest om de Schakelaar als downloadbare dossiers te verdelen, dan zou ISV instructies moeten verstrekken. In de instructie moet worden beschreven hoe de bestanden kunnen worden geïmplementeerd in een opslagplaats voor lokale bestandssystemen die in Git moet worden ingecheckt als onderdeel van het AEM project. Zo zorgt u ervoor dat Cloud Manager deze afhankelijkheden kan oplossen.
