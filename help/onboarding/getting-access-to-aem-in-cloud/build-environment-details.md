---
title: Omgevingsdetails samenstellen
description: Omgevingsdetails samenstellen - Cloud Services
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: 00bea8b6a32bab358dae6a8c30aa807cf4586d84
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---

# Inzicht in de omgeving van de build {#understanding-build-environment}

## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu. Deze omgeving heeft de volgende kenmerken:

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 18.04.
* Apache Maven 3.6.0 is geïnstalleerd.
* De geïnstalleerde Java-versies zijn Oracle JDK 8u202 en 11.0.2.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * grafiesmagick

* Andere pakketten kunnen worden geïnstalleerd tijdens het samenstellen zoals beschreven [hieronder](#installing-additional-system-packages).
* Elke bouw wordt gedaan op een ongerepte milieu; de bouwstijlcontainer houdt geen staat tussen uitvoeringen.
* Maven wordt altijd uitgevoerd met de volgende drie opdrachten:

   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent packageco-maven-plugin:prepare-agent package`
* Maven wordt op systeemniveau geconfigureerd met een settings.xml-bestand dat automatisch de openbare Adobe **Artifact**-opslagplaats bevat met een profiel met de naam `adobe-public`. (Zie [Adobe Public Maven Repository](https://repo.adobe.com/) voor meer informatie).

>[!NOTE]
>Hoewel Cloud Manager geen specifieke versie van `jacoco-maven-plugin` definieert, moet de gebruikte versie ten minste `0.7.5.201505241946` zijn.

### Java 11-ondersteuning gebruiken {#using-java-support}

Cloud Manager ondersteunt nu het maken van klantprojecten met zowel Java 8 als Java 11. Standaard worden projecten gemaakt met behulp van Java 8.

Klanten die Java 11 in hun projecten willen gebruiken kunnen dit doen gebruikend [Apache Maven Toolchains Plugin](https://maven.apache.org/plugins/maven-toolchains-plugin/).

Hiervoor voegt u in het bestand pom.xml een `<plugin>`-item toe dat er als volgt uitziet:

```
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-toolchains-plugin</artifactId>
    <version>1.1</version>
    <executions>
        <execution>
            <goals>
                <goal>toolchain</goal>
            </goals>
        </execution>
    </executions>
    <configuration>
        <toolchains>
            <jdk>
                <version>11</version>
                <vendor>oracle</vendor>
           </jdk>
        </toolchains>
    </configuration>
</plugin>
```

>[!NOTE]
>Ondersteunde leverancierswaarden zijn `oracle` en `sun`en de ondersteunde versiewaarden zijn `1.8`, `1.11` en `11`.

>[!NOTE]
>De bouwstijl van het project van de Manager van de Wolk gebruikt nog Java 8 om Geweven aan te halen, daarom het controleren van of het handhaven van de versie van Java die in de toolchain stop - binnen door plugins zoals [Apache Maven Inforcer Plugin](https://maven.apache.org/enforcer/maven-enforcer-plugin/) wordt gevormd niet werkt en dergelijke plugins moeten niet worden gebruikt.

## Omgevingsvariabelen {#environment-variables}

### Standaardomgevingsvariabelen {#standard-environ-variables}

In sommige gevallen, vinden de klanten het noodzakelijk om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als bijvoorbeeld JavaScript-miniaturen tijdens de build worden geminimaliseerd via een tool als gulp, kan het nodig zijn een ander miniatuurniveau te gebruiken bij het bouwen voor een ontwikkelomgeving in plaats van voor het bouwen voor het werkgebied en de productie.

Ter ondersteuning hiervan voegt Cloud Manager deze standaardomgevingsvariabelen voor elke uitvoering toe aan de container voor de build.

| **Naam variabele** | **Definitie** |
|---|---|
| CM_BUILD | Altijd ingesteld op &quot;true&quot; |
| BRANCH | De gevormde tak voor de uitvoering |
| CM_PIPELINE_ID | De numerieke identificatie van de pijpleiding |
| CM_PIPELINE_NAME | De pijpleidingsnaam |
| CM_PROGRAM_ID | De numerieke programma-id |
| CM_PROGRAM_NAME | De naam van het programma |
| ARTIFACTS_VERSION | Voor een stadium of productiepijplijn, de synthetische versie die door Cloud Manager wordt geproduceerd |
| CM_AEM_PRODUCT_VERSION | De releasenaam |

### Pipetvariabelen {#pipeline-variables}

In sommige gevallen, kan het bouwstijlproces van een klant van specifieke configuratievariabelen afhangen die om in de bewaarplaats van het Git ongepast zouden zijn te plaatsen of tussen pijpleidingsuitvoeringen moeten variëren gebruikend de zelfde tak.

Met Cloud Manager kunnen deze variabelen per pijpleiding worden geconfigureerd via de Cloud Manager API of Cloud Manager CLI. Variabelen kunnen worden opgeslagen als onbewerkte tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele waarnaar vervolgens kan worden verwezen vanuit het `pom.xml`-bestand of andere constructiescripts.

Om een variabele te plaatsen die CLI gebruiken, stel een bevel als in werking:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Huidige variabelen kunnen worden weergegeven:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Namen van variabelen mogen alleen alfanumerieke tekens en onderstrepingstekens (_) bevatten. Volgens de conventie moeten de namen allemaal hoofdletters zijn. Er is een grens van 200 variabelen per pijpleiding, moet elke naam minder dan 100 karakters zijn en elke waarde moet minder dan 2048 karakters in het geval van koordtypevariabelen en 500 karakters in het geval van geheimString typevariabelen zijn.

Bij gebruik in een `Maven pom.xml`-bestand is het doorgaans handig om deze variabelen toe te wijzen aan Ge-maven-eigenschappen met behulp van een soortgelijke syntaxis:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```

## Extra systeempakketten installeren {#installing-additional-system-packages}

Voor sommige builds moeten extra systeempakketten worden geïnstalleerd om volledig te kunnen functioneren. Een build kan bijvoorbeeld een Python- of ruby-script aanroepen en moet daarom een geschikte taalinterpreter hebben geïnstalleerd. Dit kan worden gedaan door [exec-maven-plugin](https://www.mojohaus.org/exec-maven-plugin/) te roepen om APT aan te halen. Deze uitvoering moet doorgaans worden opgenomen in een specifiek Maven-profiel voor Cloud Manager. Zo kunt u bijvoorbeeld python installeren:

```xml
        <profile>
            <id>install-python</id>
            <activation>
                <property>
                        <name>env.CM_BUILD</name>
                </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <groupId>org.codehaus.mojo</groupId>
                        <artifactId>exec-maven-plugin</artifactId>
                        <version>1.6.0</version>
                        <executions>
                            <execution>
                                <id>apt-get-update</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>update</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                            <execution>
                                <id>install-python</id>
                                <phase>validate</phase>
                                <goals>
                                    <goal>exec</goal>
                                </goals>
                                <configuration>
                                    <executable>apt-get</executable>
                                    <arguments>
                                        <argument>install</argument>
                                        <argument>-y</argument>
                                        <argument>--no-install-recommends</argument>
                                        <argument>python</argument>
                                    </arguments>
                                </configuration>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

Deze zelfde techniek kan worden gebruikt om taalspecifieke pakketten te installeren, d.w.z. gebruikend `gem` voor RubyGems of `pip` voor Python Pakketten.

>[!NOTE]
>Als u een systeempakket op deze manier installeert, wordt dit **niet** geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.
