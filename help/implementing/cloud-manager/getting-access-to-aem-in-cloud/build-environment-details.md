---
title: Build-omgeving
description: Meer informatie over de Cloud Manager-ontwikkelomgeving en hoe deze uw code bouwt en test.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 500e1b78fb9688601848fc17f312fc23be83bcb0
workflow-type: tm+mt
source-wordcount: '786'
ht-degree: 0%

---


# Build-omgeving {#build-environment}

Meer informatie over de Cloud Manager-ontwikkelomgeving en hoe deze uw code bouwt en test.

## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 22.04.
* Apache Maven 3.9.4 is geïnstalleerd.
   * De Adobe adviseert gebruikers [ hun Geweven bewaarplaatsen bij te werken om HTTPS in plaats van HTTP ](#https-maven) te gebruiken.
* De geïnstalleerde Java-versies zijn Oracle JDK 11.0.22 en Oracle JDK 8u401.
* **BELANGRIJK**: Door gebrek, wordt de `JAVA_HOME` milieuvariabele geplaatst aan `/usr/lib/jvm/jdk1.8.0_401` die Oracle JDK 8u401 bevat. *_Dit gebrek zou voor AEM Projecten van de Wolk moeten worden met voeten getreden om JDK 11_* te gebruiken. Zie [ Plaatsend de Geweven sectie van de Versie JDK ](#alternate-maven-jdk-version) voor meer details.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere pakketten kunnen bij bouwstijltijd zoals die in de sectie [ wordt beschreven worden geïnstalleerd die de Extra Pakketten van het Systeem ](#installing-additional-system-packages) installeert.
* Elke build wordt uitgevoerd in een ongerepte omgeving; de constructiecontainer bewaart geen status tussen executies.
* Maven wordt altijd uitgevoerd met de volgende drie opdrachten.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wordt op systeemniveau geconfigureerd met een `settings.xml` -bestand dat automatisch de openbare gegevensopslagruimte voor Adoben bevat met een profiel met de naam `adobe-public` . (Zie ](https://repo1.maven.org/) voor meer details van de Adobe Openbare Maven Bewaarplaats [.)

>[!NOTE]
>
>Hoewel Cloud Manager geen specifieke versie van de `jacoco-maven-plugin` definieert, moet de gebruikte versie ten minste `0.7.5.201505241946` zijn.

## Via HTTPS gemaakte opslagplaatsen {#https-maven}

Cloud Manager [ versie 2023.10.0 ](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) begon een het rollen update aan het bouwstijlmilieu (die met versie 2023.12.0) voltooide, die een update aan Geweven 3.8.8 omvatte. Een belangrijke wijziging die werd aangebracht in Maven 3.8.1 was een verbetering van de beveiliging die bedoeld was om potentiële kwetsbaarheden te beperken. Specifiek, maven maakt nu alle onveilige `http://*` spiegels door gebrek onbruikbaar, zoals die in de [ Gemaakt versienota&#39;s ](http://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) worden geschetst.

Als gevolg van deze beveiligingsuitbreiding kunnen sommige gebruikers problemen ondervinden tijdens de constructiestap, met name wanneer ze artefacten downloaden van Geweven opslagplaatsen die onveilige HTTP-verbindingen gebruiken.

Om ervoor te zorgen dat de bijgewerkte versie probleemloos wordt uitgevoerd, raadt Adobe gebruikers aan hun Geweven opslagplaatsen bij te werken om HTTPS in plaats van HTTP te gebruiken. Deze aanpassing sluit aan op de groeiende verschuiving van de industrie naar veilige communicatieprotocollen en helpt een veilig en betrouwbaar bouwproces in stand te houden.

### Een specifieke Java-versie gebruiken {#using-java-support}

Standaard worden projecten gemaakt door het Cloud Manager-constructieproces met Oracle 8 JDK, maar AEM Cloud Service-klanten wordt sterk aangeraden de JDK-versie die wordt gebruikt om Maven uit te voeren in te stellen op `11` .

#### De Maven JDK-versie instellen {#alternate-maven-jdk-version}

U wordt aangeraden de JDK-versie voor de gehele uitgevoerde Maven in te stellen op `11` in een `.cloudmanager/java-version` -bestand.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de vertakking van de it-opslagruimte die door de pijplijn wordt gebruikt. Bewerk het bestand zodat het alleen de tekst bevat, `11` . Hoewel Cloud Manager ook de waarde `8` accepteert, wordt deze versie niet meer ondersteund voor AEM Cloud Service-projecten. Eventuele andere waarden worden genegeerd. Wanneer `11` wordt opgegeven, wordt Oracle 11 gebruikt en wordt de omgevingsvariabele `JAVA_HOME` ingesteld op `/usr/lib/jvm/jdk-11.0.22` .

## Omgevingsvariabelen {#environment-variables}

### Standaardomgevingsvariabelen {#standard-environ-variables}

U kunt het noodzakelijk vinden om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als bijvoorbeeld JavaScript-minificatie tijdens de bouw wordt uitgevoerd met behulp van een instrument als gulp, kan het nodig zijn een ander miniatuurniveau te gebruiken bij het bouwen voor een ontwikkelomgeving in plaats van voor het opvoeren en produceren.

Om dit te steunen, voegt Cloud Manager deze standaardmilieuvariabelen aan de bouwstijlcontainer voor elke uitvoering toe.

| Naam variabele | Definitie |
|---|---|
| `CM_BUILD` | Altijd ingesteld op `true` |
| `BRANCH` | De gevormde tak voor de uitvoering |
| `CM_PIPELINE_ID` | De numerieke identificatie van de pijplijn |
| `CM_PIPELINE_NAME` | De pijpleidingsnaam |
| `CM_PROGRAM_ID` | De numerieke programma-id |
| `CM_PROGRAM_NAME` | De programmenaam |
| `ARTIFACTS_VERSION` | Voor een stadium of een productiepijpleiding, de synthetische versie die door Cloud Manager wordt gegenereerd |
| `CM_AEM_PRODUCT_VERSION` | De releaseversie |

### Pipetvariabelen {#pipeline-variables}

Uw bouwstijlproces kan van specifieke configuratievariabelen afhangen die om in de git bewaarplaats ongepast zouden zijn te plaatsen of u kunt hen tussen pijpleidinguitvoeringen moeten variëren gebruikend de zelfde tak.

Zie ook [ de Variabelen van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) voor meer informatie vormen

## Extra systeempakketten installeren {#installing-additional-system-packages}

Voor sommige builds moeten extra systeempakketten worden geïnstalleerd om volledig te kunnen functioneren. Een build kan bijvoorbeeld een Python- of Ruby-script aanroepen en moet een geschikte taalinterpreter hebben geïnstalleerd. Dit kan worden gedaan door [`exec-maven-plugin` ](https://www.mojohaus.org/exec-maven-plugin/) in uw `pom.xml` te roepen om APT aan te halen. Deze uitvoering moet doorgaans worden opgenomen in een Cloud Manager-specifiek Maven-profiel. In dit voorbeeld wordt Python geïnstalleerd.

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

Dezelfde techniek kan worden gebruikt om taalspecifieke pakketten te installeren, bijvoorbeeld met `gem` voor RubyGems of `pip` voor Python Packages.

>[!NOTE]
>
>Als u een systeempakket op deze manier installeert, wordt dit niet geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.

>[!TIP]
>
>Voor details over het front-end bouwt milieu, zie [ het Ontwikkelen Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
