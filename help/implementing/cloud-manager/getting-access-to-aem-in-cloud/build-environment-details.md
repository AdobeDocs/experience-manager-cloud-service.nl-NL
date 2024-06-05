---
title: Build-omgeving
description: Leer meer over de buildomgeving van Cloud Manager en hoe deze uw code bouwt en test.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---


# Build-omgeving {#build-environment}

Leer meer over de buildomgeving van Cloud Manager en hoe deze uw code bouwt en test.

## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 22.04.
* Apache Maven 3.9.4 is geïnstalleerd.
   * Adobe raadt gebruikers aan [hun Maven repositories bijwerken om HTTPS in plaats van HTTP te gebruiken.](#https-maven)
* De geïnstalleerde Java-versies zijn Oracle JDK 11.0.22 en Oracle JDK 8u401.
* **BELANGRIJK**: Standaard worden de `JAVA_HOME` omgevingsvariabele is ingesteld op `/usr/lib/jvm/jdk1.8.0_401` die Oracle JDK 8u401 bevat. *_Deze standaardwaarde moet worden overschreven als AEM Cloud projects JDK 11 moet gebruiken_*. Zie de [De Maven JDK-versie instellen](#alternate-maven-jdk-version) voor meer informatie.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere pakketten kunnen worden geïnstalleerd tijdens het samenstellen zoals beschreven in de sectie [Extra systeempakketten installeren.](#installing-additional-system-packages)
* Elke build wordt uitgevoerd in een ongerepte omgeving; de constructiecontainer bewaart geen status tussen executies.
* Maven wordt altijd uitgevoerd met de volgende drie opdrachten.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven is geconfigureerd op systeemniveau met een `settings.xml` bestand, dat automatisch de openbare gegevensopslagruimte voor Adoben bevat met een profiel genaamd `adobe-public`. (Zie [Adobe openbaar gemaakte opslagplaats](https://repo1.maven.org/) voor meer informatie ).

>[!NOTE]
>
>Hoewel in Cloud Manager geen specifieke versie van het dialoogvenster `jacoco-maven-plugin`moet de gebruikte versie ten minste `0.7.5.201505241946`.

## Via HTTPS gemaakte opslagplaatsen {#https-maven}

Cloud Manager [release 2023.10.0](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) begon een het rollen update aan het bouwstijlmilieu (die met versie 2023.12.0) voltooide, die een update aan Maven 3.8.8 omvatte. Een belangrijke wijziging die werd aangebracht in Maven 3.8.1 was een verbetering van de beveiliging die bedoeld was om potentiële kwetsbaarheden te beperken. Met name Maven schakelt nu alles onveilig uit `http://*` spiegels standaard, zoals wordt beschreven in het dialoogvenster [Opmerkingen bij de release Maven.](http://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291)

Als gevolg van deze beveiligingsuitbreiding kunnen sommige gebruikers problemen ondervinden tijdens de constructiestap, met name wanneer ze artefacten downloaden van Geweven opslagplaatsen die onveilige HTTP-verbindingen gebruiken.

Om ervoor te zorgen dat de bijgewerkte versie probleemloos wordt uitgevoerd, raadt Adobe gebruikers aan hun Geweven opslagplaatsen bij te werken om HTTPS in plaats van HTTP te gebruiken. Deze aanpassing sluit aan op de groeiende verschuiving van de industrie naar veilige communicatieprotocollen en helpt een veilig en betrouwbaar bouwproces in stand te houden.

### Een specifieke Java-versie gebruiken {#using-java-support}

Standaard worden projecten gemaakt door het buildproces van Cloud Manager met behulp van Oracle 8 JDK, maar klanten van AEM Cloud Service wordt ten zeerste aangeraden de JDK-versie die wordt gebruikt om Maven uit te voeren in te stellen op `11`.

#### De Maven JDK-versie instellen {#alternate-maven-jdk-version}

Het wordt aanbevolen de JDK-versie voor de gehele uitgevoerde Maven in te stellen op `11` in een `.cloudmanager/java-version` bestand.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de door de pijpleiding gebruikte vertakking van de git-opslagplaats. Bewerk het bestand zodat het alleen de tekst bevat. `11`. Cloud Manager accepteert ook de waarde van `8`, wordt deze versie niet meer ondersteund voor AEM Cloud Service-projecten. Eventuele andere waarden worden genegeerd. Wanneer `11` wordt gespecificeerd, wordt Oracle 11 gebruikt en `JAVA_HOME` omgevingsvariabele is ingesteld op `/usr/lib/jvm/jdk-11.0.22`.

## Omgevingsvariabelen {#environment-variables}

### Standaardomgevingsvariabelen {#standard-environ-variables}

U kunt het noodzakelijk vinden om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als JavaScript-miniaturen tijdens het bouwen bijvoorbeeld worden gemaakt met een tool als gulp, is het mogelijk dat u een ander miniatuurniveau wilt gebruiken bij het bouwen voor een ontwikkelomgeving in plaats van voor het maken van ophaling en productie.

Ter ondersteuning hiervan voegt Cloud Manager deze standaardomgevingsvariabelen voor elke uitvoering toe aan de container voor de build.

| Naam variabele | Definitie |
|---|---|
| `CM_BUILD` | Altijd instellen op `true` |
| `BRANCH` | De gevormde tak voor de uitvoering |
| `CM_PIPELINE_ID` | De numerieke identificatie van de pijplijn |
| `CM_PIPELINE_NAME` | De pijpleidingsnaam |
| `CM_PROGRAM_ID` | De numerieke programma-id |
| `CM_PROGRAM_NAME` | De programmenaam |
| `ARTIFACTS_VERSION` | Voor een stadium of productiepijplijn, de synthetische versie die door Cloud Manager wordt geproduceerd |
| `CM_AEM_PRODUCT_VERSION` | De releaseversie |

### Pipetvariabelen {#pipeline-variables}

Uw bouwstijlproces kan van specifieke configuratievariabelen afhangen die om in de git bewaarplaats ongepast zouden zijn te plaatsen of u kunt hen tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak.

Zie het document [Het vormen Variabelen van de Pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) voor meer informatie

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

Deze zelfde techniek kan worden gebruikt om taal-specifieke pakketten te installeren, bijvoorbeeld `gem` voor RubyGems of `pip` voor Python Packages.

>[!NOTE]
>
>Als u een systeempakket op deze manier installeert, wordt dit niet geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.

>[!TIP]
>
>Voor meer informatie over de omgeving van de front-end build raadpleegt u [Sites ontwikkelen met behulp van de voorste pijplijn](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
