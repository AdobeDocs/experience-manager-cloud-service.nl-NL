---
title: Structuurpakket projectopslagplaats AEM
description: Gemaakte projecten op Adobe Experience Manager as a Cloud Service vereisen een definitie van subpakket van de Structuur van de Bewaarplaats met als enig doel de wortels van de bewaarplaats van JCR te bepalen waarin de Codepakketten van het project in subpakketten van de Code van het project opstellen.
exl-id: dec08410-d109-493d-bf9d-90e5556d18f0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 520ab0229b4f00a1de981209bf26059b0d00c3da
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Structuurpakket projectopslagplaats AEM

Gemaakte projecten voor Adobe Experience Manager as a Cloud Service vereisen een definitie van het subpakket van de opslagplaats met als enig doel het bepalen van de wortels van de bewaarplaats JCR waarin de code van het project subpackages opstelt. Deze methode zorgt ervoor dat de installatie van pakketten in as a Cloud Service Experience Manager automatisch door JCR middelgebiedsdelen wordt bevolen. Ontbrekende afhankelijkheden kunnen leiden tot scenario&#39;s waarbij substructuren worden geïnstalleerd vóór hun bovenliggende structuren en daarom onverwacht worden verwijderd, waardoor de implementatie wordt verbroken.

Als uw codepakket in een plaats opstelt **niet gedekt** door het codepakket moeten eventuele bronnen van voorouders (JCR-bronnen die dichter bij de JCR-basis liggen) worden opgesomd in het structuurpakket van de repository. Dit proces is noodzakelijk om deze gebiedsdelen te vestigen.

![Structuurpakket opslagplaats](./assets/repository-structure-packages.png)

In het structuurpakket van de repository wordt de verwachte, algemene status van `/apps` welke de pakketvalidator gebruikt om te bepalen welke gebieden &quot;veilig zijn tegen potentiële conflicten&quot; als standaardwortels hebben.

De meest gangbare paden die in het opslagstructuurpakket moeten worden opgenomen, zijn:

+ `/apps` Dit is een systeemknooppunt
+ `/apps/cq/...`, `/apps/dam/...`, `/apps/wcm/...`, en `/apps/sling/...` die algemene overlays bieden voor `/libs`.
+ `/apps/settings` Dit is het gedeelde context-bewuste pad van de configuratiepunt

Dit subpakket **heeft geen** alle inhoud en die uitsluitend bestaat uit een `pom.xml` de filterwortels definiëren.

## Het Repository Structure Package maken

Maak een leeg Maven-subproject als u een pakket gegevensopslagstructuur voor uw Maven-project wilt maken, met het volgende `pom.xml`, die de projectmeta-gegevens bijwerken om met uw ouder Maven project in overeenstemming te brengen.

Werk de `<filters>` om alle pad naar de JCR-opslagplaats op te nemen, zodat uw codepakketten worden geïmplementeerd.

Zorg ervoor dit nieuwe Gemaakt subproject aan de ouderprojecten toevoegt `<modules>` lijst.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- ====================================================================== -->
    <!-- P A R E N T  P R O J E C T  D E S C R I P T I O N                      -->
    <!-- ====================================================================== -->
    <parent>
        <groupId>com.my-company</groupId>
        <artifactId>my-app</artifactId>
        <version>x.x.x</version>
        <relativePath>../pom.xml</relativePath>
    </parent>

    <!-- ====================================================================== -->
    <!-- P R O J E C T  D E S C R I P T I O N                                   -->
    <!-- ====================================================================== -->
    <artifactId>ui.apps.structure</artifactId>
    <packaging>content-package</packaging>
    <name>UI Apps Structure - Repository Structure Package for /apps</name>

    <description>
        Empty package that defines the structure of the Adobe Experience Manager repository the code packages in this project deploy into.
        Any roots in the code packages of this project should have their parent enumerated in the filters list below.
    </description>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.jackrabbit</groupId>
                <artifactId>filevault-package-maven-plugin</artifactId>
                <extensions>true</extensions>
                <properties>
                    <!-- Set Cloud Manager Target to none, else this package is deployed and remove all defined filter roots -->
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
                <configuration>
                    <properties>
                        <!-- Set Cloud Manager Target to none, else this package is deployed and remove all defined filter roots -->
                        <cloudManagerTarget>none</cloudManagerTarget>
                    </properties>
                    <filters>

                        <!-- /apps root -->
                        <filter><root>/apps</root></filter>

                        <!--
                        Examples of complex roots


                        Overlays of /libs typically require defining the overlay structure, at each level here.

                        For example, adding a new section to the main AEM Tools navigation, necessitates the following rules:

                        <filter><root>/apps/cq</root></filter>
                        <filter><root>/apps/cq/core</root></filter>
                        <filter><root>/apps/cq/core/content</root></filter>
                        <filter><root>/apps/cq/core/content/nav/</root></filter>
                        <filter><root>/apps/cq/core/content/nav/tools</root></filter>


                        Any /apps level Context-aware configurations need to enumerated here. 
                        
                        For example, providing email templates under `/apps/settings/notification-templates/com.day.cq.replication` necessitates the following rules:

                        <filter><root>/apps/settings</root></filter>
                        <filter><root>/apps/settings/notification-templates</root></filter>
                        <filter><root>/apps/settings/notification-templates/com.day.cq.replication</root></filter>
                        -->

                    </filters>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

## Verwijzen naar het Repository Structure Package

Als u het structuurpakket van de repository wilt gebruiken, moet u ernaar verwijzen via alle codepakketten (de subpakketten die worden geïmplementeerd op `/apps`) GeMaven projecten via het FileVault-inhoudspakket Maven plug-ins `<repositoryStructurePackage>` configuratie.

In de `ui.apps/pom.xml`en elk ander codepakket `pom.xml`s, voeg een verwijzing naar het de structuurpakket van de bewaarplaats van het project (#repository-structure-package) configuratie aan het pakket FileVault Maven stop-in toe.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
</build>
<dependencies>
    <!-- Add the dependency for the repository structure package so it resolves -->
    <dependency>
        <groupId>${project.groupId}</groupId>
        <artifactId>ui.apps.structure</artifactId>
        <version>${project.version}</version>
        <type>zip</type>
    </dependency>
    ...
</dependencies>
```

## Gebruiksscenario voor multi-code pakket

Een minder gangbare, en complexere gebruikscase biedt ondersteuning voor de implementatie van meerdere codepakketten die in dezelfde gebieden van de JCR-opslagplaats worden geïnstalleerd.

Bijvoorbeeld:

+ Codepakket A wordt geïmplementeerd in `/apps/a`
+ Codepakket B wordt geïmplementeerd in `/apps/a/b`

Als een op pakketniveau gebiedsdeel niet van codepakket B op codepakket A wordt gevestigd, kan het codepakket B eerst in `/apps/a`. Als het dan door codepakket A wordt gevolgd, dat in opstelt `/apps/a`, het resultaat is dat de eerder geïnstalleerde `/apps/a/b`.

In dit geval:

+ Codepakket A moet een `<repositoryStructurePackage>` over het pakket opslagplaats van het project (dat een filter moet hebben voor `/apps`).
+ Codepakket B moet een `<repositoryStructurePackage>` op codepakket A, omdat codepakket B wordt geïmplementeerd in een ruimte die wordt gedeeld door codepakket A.

## Fouten en fouten opsporen

Als de opslagplaatsstructuurpakketten niet correct zijn ingesteld, wordt bij Maven een fout gemeld:

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

Deze fout geeft aan dat het pakket voor het afbreken van code geen `<repositoryStructurePackage>` die lijsten `/apps/some/path` in de filterlijst.

## Aanvullende bronnen

+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
