---
title: 'Structuurpakket voor AEM-projectopslagplaats  '
description: Voor Adobe Experience Manager als een met cloudservice gefinancierde projecten is een definitie vereist van het subpakket Structuur in opslagplaats met als enig doel de wortels van de JCR-opslagplaats te definiëren waarin de subpakketten Code van het project worden geïmplementeerd.
translation-type: tm+mt
source-git-commit: a6efcbb85949e65167ebab0e2a8dae06eaeaa07f

---


# Structuurpakket voor AEM-projectopslagplaats

Voor geMaven projecten voor Adobe Experience Manager als Cloud Service is een subpakketdefinitie vereist in de opslagplaats met als enig doel het definiëren van de wortels van de JCR-opslagplaats waarin de code-subpakketten van het project worden geïmplementeerd. Dit zorgt ervoor dat de installatie van pakketten in de Manager van de Ervaring als Dienst van de Wolk automatisch door JCR middelgebiedsdelen wordt bevolen. Ontbrekende afhankelijkheden kunnen leiden tot scenario&#39;s waarbij substructuren worden geïnstalleerd vóór hun bovenliggende structuren en daarom onverwacht worden verwijderd, waardoor de implementatie wordt verbroken.

Als uw codepakket wordt geïmplementeerd op een locatie die **niet door het codepakket wordt gedekt**, dan moeten bovenliggende resources (JCR-resources die zich dichter bij de JCR-root bevinden) in het pakket van de dataopslagstructuur worden opgesomd om deze afhankelijkheden tot stand te brengen.

![Structuurpakket opslagplaats](./assets/repository-structure-packages.png)

Het opslagstructuurpakket definieert de verwachte, algemene status `/apps` die door de pakketvalidator wordt gebruikt om te bepalen welke gebieden &quot;veilig zijn tegen potentiële conflicten&quot;, aangezien ze de standaardachtergrond zijn.

De meest gangbare paden die in het opslagstructuurpakket moeten worden opgenomen zijn:

+ `/apps` Dit is een systeemknooppunt
+ `/apps/cq/...`, `/apps/dam/...`, `/apps/wcm/...`, en `/apps/sling/...` die gemeenschappelijke overlays voor `/libs`.
+ `/apps/settings` Dit is het gedeelde context-bewuste pad van de configuratiegrootte

Deze subverpakking bevat **geen** inhoud en bestaat uitsluitend uit een `pom.xml` definitie van de filterwortels.

## Het Repository Structure Package maken

Om een pakket van de gegevensopslagstructuur voor u Maven project tot stand te brengen, creeer een nieuw leeg subproject Maven, met het volgende, bijwerkt de projectmeta-gegevens om met uw ouder Maven project in overeenstemming te zijn. `pom.xml`

Werk de code bij `<filters>` om alle pad naar de JCR-opslagplaats te gebruiken die aan de basis ligt van uw codepakketten waarin u implementeert.

Zorg ervoor om dit nieuwe Maven subproject aan de `<modules>` lijst van ouderprojecten toe te voegen.

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
    <artifactId>my-app.repository-structure</artifactId>
    <packaging>content-package</packaging>
    <name>My App - Adobe Experience Manager Repository Structure Package</name>

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
                <configuration>
                    <properties>
                        <!-- Set Cloud Manager Target to none, else this package will be deployed and remove all defined filter roots -->
                        <cloudManagerTarget>none</cloudManagerTarget>
                    </properties>
                    <filters>

                        <!-- /apps root -->
                        <filter><root>/apps</root></filter>

                        <!-- Common overlay roots -->
                        <filter><root>/apps/sling</root></filter>
                        <filter><root>/apps/cq</root></filter>
                        <filter><root>/apps/dam</root></filter>
                        <filter><root>/apps/wcm</root></filter>

                        <!-- Immutable context-aware configurations -->
                        <filter><root>/apps/settings</root></filter>

                    </filters>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

## Verwijzen naar het Repository Structure Package

Als u het structuurpakket van de repository wilt gebruiken, kunt u ernaar verwijzen via alle codepakketten (de subpakketten die worden geïmplementeerd naar `/apps`) GeMaven projecten via het FileVault-inhoudspakket Maven plug-ins `<repositoryStructurePackage>` configuratie.

Voeg in de `ui.apps/pom.xml`en eventuele andere codepakketten een verwijzing `pom.xml`toe naar de configuratie van het opslagruimtestructuurpakket (#repository-structure-package) van het project aan het FileVault-pakket Maven-plug-in.

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
              <artifactId>my-app.repository-structure</artifactId>
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
        <artifactId>my-app.repository-structure</artifactId>
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

Als een pakket-vlakke gebiedsdeel niet van codepakket B op codepakket A wordt gevestigd, kan codepakket B eerst in opstellen, `/apps/a`gevolgd door codepakket B, dat in opstelt `/apps/a`, resulterend in een verwijdering van eerder geïnstalleerd `/apps/a/b`.

In dit geval:

+ Codepakket A moet een definitie geven `<repositoryStructurePackage>` voor het pakket met de opslagplaats van het project (waarvoor een filter moet worden gebruikt `/apps`).
+ Het pakket van de code B zou een `<repositoryStructurePackage>` op codepakket A moeten bepalen, omdat het codepakket B in ruimte die door codepakket A wordt gedeeld opstelt.

## Fouten en fouten opsporen

Als de opslagplaatsstructuurpakketten niet correct zijn ingesteld, wordt bij Maven een fout gerapporteerd:

```
1 error(s) detected during dependency analysis.
Filter root's ancestor '/apps/some/path' is not covered by any of the specified dependencies.
```

Dit geeft aan dat het pakket voor afbrekende code geen code heeft `<repositoryStructurePackage>` die voorkomt `/apps/some/path` in de filterlijst.

## Aanvullende bronnen

+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
