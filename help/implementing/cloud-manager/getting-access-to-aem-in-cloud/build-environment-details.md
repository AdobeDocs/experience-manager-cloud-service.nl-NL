---
title: Build-omgeving
description: Leer meer over de buildomgeving van Cloud Manager en hoe deze uw code bouwt en test.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
source-git-commit: c138f0be15550df85a2ec23b6b551ccba07996c8
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---

# Build-omgeving {#build-environment}

Leer meer over de buildomgeving van Cloud Manager en hoe deze uw code bouwt en test.

## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 18.04.
* Apache Maven 3.6.0 is geïnstalleerd.
* De geïnstalleerde Java-versies zijn Oracle JDK 8u202 en Oracle JDK 11.0.2.
* Standaard worden de `JAVA_HOME` omgevingsvariabele is ingesteld op `/usr/lib/jvm/jdk1.8.0_202`  die Oracle JDK 8u202 bevat. Zie [JDK-versie van alternatieve uitvoering](#alternate-maven-jdk-version) voor meer informatie.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn.

   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`

* Andere pakketten kunnen worden geïnstalleerd tijdens het samenstellen zoals beschreven in de sectie [Extra systeempakketten installeren.](#installing-additional-system-packages)
* Elke bouw wordt gedaan op een ongerepte milieu; de bouwstijlcontainer houdt geen staat tussen uitvoeringen.
* Maven wordt altijd uitgevoerd met de volgende drie opdrachten.

* `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
* `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
* `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven is geconfigureerd op systeemniveau met een `settings.xml` bestand, dat automatisch de openbare gegevensopslagruimte Adobe bevat met een profiel genaamd `adobe-public`. (Zie [Adobe Public Maven Repository](https://repo1.maven.org/) voor meer informatie ).

>[!NOTE]
>
>Hoewel in Cloud Manager geen specifieke versie van het dialoogvenster `jacoco-maven-plugin`moet de gebruikte versie ten minste `0.7.5.201505241946`.

### Een specifieke Java-versie gebruiken {#using-java-support}

Standaard worden projecten gemaakt door het buildproces van Cloud Manager met Oracle 8 JDK. Klanten die een alternatieve JDK willen gebruiken, hebben twee opties.

* [Geweven toolketens gebruiken.](#maven-toolchains)
* [Selecteer een alternatieve JDK-versie voor het hele uitgevoerde Maven-proces.](#alternate-maven-jdk-version)

#### Maven Toolketins {#maven-toolchains}

De [Insteekmodule Maven Toolketins](https://maven.apache.org/plugins/maven-toolchains-plugin/) Hiermee kunnen projecten een specifieke JDK (of toolchain) selecteren die moet worden gebruikt in de context van Maven-plug-ins die geschikt zijn voor toolketens. Dit wordt gedaan in het project `pom.xml` door een leverancier- en versiewaarde op te geven.

```xml
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

Hierdoor wordt voor alle plug-ins met behoud van gereedschappen het Oracle JDK, versie 11, gebruikt.

Wanneer u deze methode gebruikt, wordt Maven zelf nog steeds uitgevoerd met de standaard-JDK (Oracle 8) en de `JAVA_HOME`  omgevingsvariabele wordt niet gewijzigd. Daarom werkt het controleren of afdwingen van de Java-versie via plug-ins zoals de Apache Maven Enforcer Plugin niet en mogen dergelijke plug-ins niet worden gebruikt.

De momenteel beschikbare leverancier/versiecombinaties zijn:

| Leverancier | Versie |
|---|---|
| `oracle` | `1.8` |
| `oracle` | `1.11` |
| `oracle` | `11` |
| `sun` | `1.8` |
| `sun` | `1.11` |
| `sun` | `11` |

>[!NOTE]
>
>Vanaf april 2022 is Oracle JDK de standaard-JDK voor de ontwikkeling en werking van AEM toepassingen. Het buildproces van Cloud Manager wordt automatisch overgeschakeld op het gebruik van Oracle JDK, zelfs als er expliciet een andere optie is geselecteerd in de Maven-toolchain. Raadpleeg de opmerkingen bij de release van april nadat deze voor meer informatie zijn gepubliceerd.

#### JDK-versie van alternatieve uitvoering {#alternate-maven-jdk-version}

Het is ook mogelijk om Java 8 of Java 11 als JDK voor de volledige Geweven uitvoering te selecteren. In tegenstelling tot de opties van toolketins, verandert dit JDK die voor alle stop-ins wordt gebruikt tenzij de toolketenconfiguratie ook wordt geplaatst waarin de toolkettenconfiguratie nog voor toolketens-bewuste Maven plugins wordt toegepast. Hierdoor wordt de Java-versie gecontroleerd en afgedwongen met de [Insteekmodule Apache Maven Enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/) werkt.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de door de pijpleiding gebruikte vertakking van de git-opslagplaats. Dit bestand kan de inhoud 11 of 8 hebben. Eventuele andere waarden worden genegeerd. Indien 11 wordt gespecificeerd, wordt Oracle 11 gebruikt en `JAVA_HOME` omgevingsvariabele is ingesteld op `/usr/lib/jvm/jdk-11.0.2`. Indien 8 gespecificeerd is, wordt Oracle 8 gebruikt en de `JAVA_HOME` omgevingsvariabele is ingesteld op `/usr/lib/jvm/jdk1.8.0_202`.

## Omgevingsvariabelen {#environment-variables}

### Standaardomgevingsvariabelen {#standard-environ-variables}

U kunt het noodzakelijk vinden om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als JavaScript-miniaturen tijdens het bouwen bijvoorbeeld worden gemaakt met een tool als gulp, is het mogelijk dat u een ander miniatuurniveau wilt gebruiken bij het bouwen voor een ontwikkelomgeving in plaats van voor het maken van ophaling en productie.

Ter ondersteuning hiervan voegt Cloud Manager deze standaardomgevingsvariabelen voor elke uitvoering toe aan de container voor de build.

| Naam variabele | Definitie |
|---|---|
| `CM_BUILD` | Altijd instellen op `true` |
| `BRANCH` | De gevormde tak voor de uitvoering |
| `CM_PIPELINE_ID` | De numerieke identificatie van de pijpleiding |
| `CM_PIPELINE_NAME` | De pijpleidingsnaam |
| `CM_PROGRAM_ID` | De numerieke programma-id |
| `CM_PROGRAM_NAME` | De naam van het programma |
| `ARTIFACTS_VERSION` | Voor een stadium of productiepijplijn, de synthetische versie die door Cloud Manager wordt geproduceerd |
| `CM_AEM_PRODUCT_VERSION` | De releaseversie |

### Pipetvariabelen {#pipeline-variables}

Uw bouwstijlproces kan van specifieke configuratievariabelen afhangen die om in de git bewaarplaats ongepast zouden zijn te plaatsen of u kunt hen tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak.

Met Cloud Manager kunnen deze variabelen per pijpleiding worden geconfigureerd via de Cloud Manager API of Cloud Manager CLI. Variabelen kunnen worden opgeslagen als onbewerkte tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele die vervolgens van binnen de `pom.xml` of andere build-scripts.

Dit CLI bevel plaatst een variabele.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Deze opdracht geeft een overzicht van variabelen.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Namen van variabelen moeten voldoen aan de volgende conventies.

* Variabelen mogen alleen alfanumerieke tekens en het onderstrepingsteken (`_`).
* De namen moeten allemaal hoofdletters zijn.
* Er is een grens van 200 variabelen per pijpleiding.
* Elke naam moet uit minder dan 100 tekens bestaan.
* Elk `string` waarde van variabele moet minder dan 2048 tekens zijn.
* Elk `secretString` waarde van tekstvariabele moet minder dan 500 tekens zijn.

Indien gebruikt in een Maven `pom.xml` , is het doorgaans handig om deze variabelen toe te wijzen aan Maven-eigenschappen met een vergelijkbare syntaxis.

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

Voor sommige builds moeten extra systeempakketten worden geïnstalleerd om volledig te kunnen functioneren. Een build kan bijvoorbeeld een Python- of Ruby-script aanroepen en moet een geschikte taalinterpreter hebben geïnstalleerd. Dit kan door te roepen [`exec-maven-plugin`](https://www.mojohaus.org/exec-maven-plugin/) in uw `pom.xml` om APT aan te roepen. Deze uitvoering moet doorgaans worden opgenomen in een specifiek Maven-profiel voor Cloud Manager. In dit voorbeeld wordt Python geïnstalleerd.

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

Dezelfde techniek kan worden gebruikt om taalspecifieke pakketten te installeren, bijvoorbeeld met behulp van `gem` voor RubyGems of `pip` voor Python Packages.

>[!NOTE]
>
>Als u een systeempakket op deze manier installeert, wordt dit niet geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.
