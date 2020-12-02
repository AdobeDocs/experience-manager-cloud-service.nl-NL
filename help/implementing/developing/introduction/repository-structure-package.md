---
title: 'AEM-projectrepositorystructuurpakket  '
description: Adobe Experience Manager als Cloud Service Maven-projecten vereist een definitie van subpakket voor de structuur van de opslagplaats met als enig doel de wortels van de JCR-opslagplaats te bepalen waarin de subpakketten voor de code van het project worden geïmplementeerd.
translation-type: tm+mt
source-git-commit: a6820eab30f2b318d62d2504cb17c12081a320a3
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 9%

---


# AEM-projectrepositorystructuurpakket

Voor geMaven projecten voor Adobe Experience Manager als Cloud Service is een subpakketdefinitie van de structuur van de repository nodig die uitsluitend tot doel heeft de wortels van de JCR-opslagplaats te bepalen waarin de codecopakketten van het project worden geïmplementeerd. Dit verzekert de installatie van pakketten in Experience Manager als Cloud Service automatisch door JCR middelgebiedsdelen wordt bevolen. Ontbrekende afhankelijkheden kunnen leiden tot scenario&#39;s waarbij substructuren worden geïnstalleerd vóór hun bovenliggende structuren en daarom onverwacht worden verwijderd, waardoor de implementatie wordt verbroken.

Als uw codepakket wordt geïmplementeerd op een locatie die **niet door het codepakket wordt gedekt**, dan moeten bovenliggende resources (JCR-resources die zich dichter bij de JCR-root bevinden) in het pakket van de dataopslagstructuur worden opgesomd om deze afhankelijkheden tot stand te brengen.

![Structuurpakket opslagplaats](./assets/repository-structure-packages.png)

Het opslagstructuurpakket definieert de verwachte, algemene status van `/apps` die door de pakketvalidator wordt gebruikt om te bepalen welke gebieden &quot;veilig zijn tegen potentiële conflicten&quot;, aangezien ze de standaardachtergrond zijn.

De meest gangbare paden die in het opslagstructuurpakket moeten worden opgenomen zijn:

+ `/apps` Dit is een systeemknooppunt
+ `/apps/cq/...`,  `/apps/dam/...`,  `/apps/wcm/...`en  `/apps/sling/...` die algemene overlays voor  `/libs`.
+ `/apps/settings` Dit is het gedeelde context-bewuste pad van de configuratiegrootte

Dit subpakket **bevat geen**-inhoud en bestaat uitsluitend uit een `pom.xml` dat de filterwortels definieert.

## Het Repository Structure Package maken

Als u een pakket opslagplaats wilt maken voor uw Maven-project, maakt u een nieuw leeg Maven-subproject met de volgende `pom.xml`, waarbij u de metagegevens van het project bijwerkt conform uw bovenliggende Maven-project.

Werk `<filters>` bij om alle weg van de opslagplaats JCR te omvatten uw codepakketten opstellen in.

Zorg ervoor om dit nieuwe Maven subproject aan de ouderprojecten `<modules>` lijst toe te voegen.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
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
                    <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
                <configuration>
                    <properties>
                        <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                        <cloudManagerTarget>none</cloudManagerTarget>
                    </properties>
                    <filters>

                        <!-- /apps root -->
                        <filter><root>/apps</root></filter>

                        <!--
                        Examples of complex roots


                        Overlays of /libs typically require defining the overlayed structure, at each level here.

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

Als u het structuurpakket van de opslagplaats wilt gebruiken, kunt u dit raadplegen via alle codepakketten (de subpakketten die worden geïmplementeerd op `/apps`) Geweven projecten via het bestandsVault-inhoudspakket Maven plug-ins `<repositoryStructurePackage>`-configuratie.

In `ui.apps/pom.xml` en elk ander codepakket `pom.xml`s voegt u een verwijzing naar de configuratie van het opslagplaatsstructuurpakket (#repository-structure-package) van het project toe aan het FileVault-pakket Maven-plug-in.

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

## Gebruiksscenario voor meerdere code

Een minder gangbare, en complexere gebruikscase biedt ondersteuning voor de implementatie van meerdere codepakketten die in dezelfde gebieden van de JCR-opslagplaats worden geïnstalleerd.

Bijvoorbeeld:

+ Codepakket A wordt geïmplementeerd in `/apps/a`
+ Codepakket B wordt geïmplementeerd in `/apps/a/b`

Als er geen afhankelijkheid op pakketniveau wordt vastgesteld van codepakket B op codepakket A, kan codepakket B eerst worden geïmplementeerd in `/apps/a`, gevolgd door codepakket B, dat wordt geïmplementeerd in `/apps/a`, waardoor de eerder geïnstalleerde `/apps/a/b` wordt verwijderd.

In dit geval:

+ Codepakket A moet een `<repositoryStructurePackage>` definiëren op het opslagplaatsstructuurpakket van het project (dat een filter moet hebben voor `/apps`).
+ Codepakket B moet een `<repositoryStructurePackage>` definiëren op codepakket A, omdat codepakket B wordt geïmplementeerd in een ruimte die wordt gedeeld door codepakket A.

## Fouten en fouten opsporen

Als de opslagplaatsstructuurpakketten niet correct zijn ingesteld, wordt bij Maven een fout gerapporteerd:

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

Dit wijst op het het breken codepakket geen `<repositoryStructurePackage>` heeft die `/apps/some/path` in zijn filterlijst opsomt.

## Aanvullende bronnen

+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
