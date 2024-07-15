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

Gemaakte projecten voor Adobe Experience Manager as a Cloud Service vereisen een definitie van het subpakket van de opslagplaats met als enig doel het bepalen van de wortels van de bewaarplaats JCR waarin de code van het project subpackages opstelt. Deze methode verzekert de installatie van pakketten in Experience Manager as a Cloud Service automatisch door JCR middelgebiedsdelen wordt bevolen. Ontbrekende afhankelijkheden kunnen leiden tot scenario&#39;s waarbij substructuren worden geïnstalleerd vóór hun bovenliggende structuren en daarom onverwacht worden verwijderd, waardoor de implementatie wordt verbroken.

Als uw codepakket in een plaats **opstelt niet die** door het codepakket wordt behandeld, dan moeten om het even welke vooroudermiddelen (middelen JCR dichter bij de wortel JCR) in het pakket van de opslagplaatsstructuur worden opgesomd. Dit proces is noodzakelijk om deze gebiedsdelen te vestigen.

![ Pakket van de Structuur van de Bewaarplaats ](./assets/repository-structure-packages.png)

Het opslagplaatsstructuurpakket definieert de verwachte, algemene status van `/apps` die door de pakketvalidator wordt gebruikt om te bepalen welke gebieden &#39;veilig zijn tegen potentiële conflicten&#39;, aangezien ze de standaardwortels hebben.

De meest gangbare paden die in het opslagstructuurpakket moeten worden opgenomen, zijn:

+ `/apps` dat een systeemknooppunt is
+ `/apps/cq/...` , `/apps/dam/...` , `/apps/wcm/...` en `/apps/sling/...` die algemene overlays voor `/libs` bieden.
+ `/apps/settings` Dit is het gedeelde pad naar de configuratieproot

Dit subpackage **heeft** geen inhoud en bestaat uitsluitend uit a `pom.xml` die de filterwortels bepalen.

## Het Repository Structure Package maken

Als u een pakket opslagplaats wilt maken voor uw Maven-project, maakt u een leeg Maven-subproject met de volgende `pom.xml` , waarbij u de metagegevens van het project bijwerkt conform uw bovenliggende Maven-project.

Werk `<filters>` bij om alle JCR-opslagpaden op te nemen die aan de basis liggen van uw codepakketten waarin u implementeert.

Zorg ervoor dat u dit nieuwe Maven-subproject toevoegt aan de lijst met bovenliggende projecten `<modules>` .

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

Als u het structuurpakket van de repository wilt gebruiken, kunt u ernaar verwijzen via alle codepakketten (de subpakketten die worden geïmplementeerd naar `/apps`) Gemaakt projecten via de configuratie van het FileVault-inhoudspakket Maven plug-ins `<repositoryStructurePackage>` .

In `ui.apps/pom.xml`, en om het even welk ander codepakket `pom.xml` s, voeg een verwijzing naar het de structuurpakket van de opslagplaats van het project (#repository-structure-package) configuratie aan het pakket FileVault Maven stop-in toe.

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

Als er geen afhankelijkheid op pakketniveau wordt vastgesteld van codepakket B op codepakket A, kan codepakket B eerst worden geïmplementeerd in `/apps/a` . Als deze wordt gevolgd door codepakket A, dat wordt geïmplementeerd in `/apps/a` , is het resultaat een verwijdering van de eerder geïnstalleerde `/apps/a/b` .

In dit geval:

+ Codepakket A moet een `<repositoryStructurePackage>` definiëren voor het opslagplaatsstructuurpakket van het project (dat een filter moet hebben voor `/apps` ).
+ Codepakket B moet een `<repositoryStructurePackage>` definiëren voor codepakket A, omdat codepakket B wordt geïmplementeerd in een ruimte die wordt gedeeld door codepakket A.

## Fouten en fouten opsporen

Als de opslagplaatsstructuurpakketten niet correct zijn ingesteld, wordt bij Maven een fout gemeld:

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

Deze fout geeft aan dat het pakket voor het afbreken van code geen `<repositoryStructurePackage>` bevat met `/apps/some/path` in de filterlijst.

## Aanvullende bronnen

+ [ Geproduceerde Plug-in van het Pakket van de Inhoud FileVault ](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
