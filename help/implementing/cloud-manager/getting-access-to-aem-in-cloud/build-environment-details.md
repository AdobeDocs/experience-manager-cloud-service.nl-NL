---
title: Build Environment of Cloud Manager
description: Meer informatie over de Cloud Manager-ontwikkelomgeving en hoe deze uw code bouwt en test.
exl-id: a4e19c59-ef2c-4683-a1be-3ec6c0d2f435
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ee01e5a2b805330f47af7ff563ca1ac90036f0bf
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 0%

---


# Build-omgeving {#build-environment}

Meer informatie over de Cloud Manager-ontwikkelomgeving en hoe deze uw code bouwt en test.

## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu.

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 22.04.
* Apache Maven 3.9.4 is geïnstalleerd.
   * De Adobe adviseert gebruikers [ hun Geweven bewaarplaatsen bij te werken om HTTPS in plaats van HTTP ](#https-maven) te gebruiken.
<!-- OLD Removed 1/16/25 * The Java versions installed are Oracle JDK 11.0.22 and Oracle JDK 8u401. -->
* De geïnstalleerde versies van Java zijn Oracle JDK 11.0.22, Oracle JDK 17.0.10, en Oracle JDK 21.0.4.

<!-- OLD Removed 1/16/25 * **IMPORTANT:** By default, the JAVA_HOME environment variable is set to `/usr/lib/jvm/jdk1.8.0_401`, which contains Oracle JDK 8u401. This default should be overridden for AEM Cloud Projects to use JDK 11. See the Setting the Maven JDK Version section for more details. -->
* **BELANGRIJK:** Door gebrek, wordt de `JAVA_HOME` milieuvariabele geplaatst aan `/usr/lib/jvm/jdk1.8.0_401`, die Oracle JDK 8u401 bevat. ***Dit gebrek zou voor AEM Projecten van de Wolk moeten worden met voeten getreden om JDK 21 (aangewezen), 17, of 11*** te gebruiken. Zie [ Plaatsend de Geweven sectie van de Versie JDK ](#alternate-maven-jdk-version) voor meer details.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn.
   * `bzip2`
   * `unzip`
   * `libpng`
   * `imagemagick`
   * `graphicsmagick`
* Andere pakketten kunnen bij bouwstijltijd zoals die in de sectie [ wordt beschreven worden geïnstalleerd die de Extra Pakketten van het Systeem ](#installing-additional-system-packages) installeert.
* Elke bouwstijl loopt in een schone milieu, met de bouwstijlcontainer die geen staat tussen uitvoeringen behoudt.
* Maven wordt altijd uitgevoerd met de volgende drie opdrachten.
   * `mvn --batch-mode org.apache.maven.plugins:maven-dependency-plugin:3.1.2:resolve-plugins`
   * `mvn --batch-mode org.apache.maven.plugins:maven-clean-plugin:3.1.0:clean -Dmaven.clean.failOnError=false`
   * `mvn --batch-mode org.jacoco:jacoco-maven-plugin:prepare-agent package`
* Maven wordt op systeemniveau geconfigureerd met een `settings.xml` -bestand dat automatisch de openbare gegevensopslagruimte voor Adoben bevat met een profiel met de naam `adobe-public` . (Zie ](https://repo1.maven.org/) voor meer details van de Adobe Openbare Maven Bewaarplaats [.)

>[!NOTE]
>
>Hoewel Cloud Manager geen specifieke versie van de `jacoco-maven-plugin` definieert, moet de gebruikte versie ten minste `0.7.5.201505241946` zijn.

## Door HTTPS aangebrachte opslagruimten {#https-maven}

Cloud Manager [ versie 2023.10.0 ](/help/implementing/cloud-manager/release-notes/2023/2023-10-0.md) begon een het rollen update aan het bouwstijlmilieu (die met versie 2023.12.0) voltooide, die een update aan Geweven 3.8.8 omvatte. Een belangrijke wijziging die werd aangebracht in Maven 3.8.1 was een verbetering van de beveiliging die bedoeld was om potentiële kwetsbaarheden te beperken. Specifiek, maven maakt nu alle onveilige `http://*` spiegels door gebrek onbruikbaar, zoals die in de [ Gemaakt versienota&#39;s ](https://maven.apache.org/docs/3.8.1/release-notes.html#cve-2021-26291) worden geschetst.

Als gevolg van deze beveiligingsuitbreiding kunnen sommige gebruikers problemen ondervinden tijdens de constructiestap, met name wanneer ze artefacten downloaden van Geweven opslagplaatsen die onveilige HTTP-verbindingen gebruiken.

Om ervoor te zorgen dat de bijgewerkte versie probleemloos wordt uitgevoerd, raadt Adobe gebruikers aan hun Geweven opslagplaatsen bij te werken om HTTPS in plaats van HTTP te gebruiken. Deze aanpassing sluit aan op de groeiende verschuiving van de industrie naar veilige communicatieprotocollen en helpt een veilig en betrouwbaar bouwproces in stand te houden.

<!-- OLD below Removed 1/16/25

### Use a specific Java version

The Cloud Manager build process uses the Oracle 8 JDK to build projects by default, but AEM Cloud Service customers should set the Maven execution JDK version to 11. -->

<!-- OLD below Removed 1/16/25

#### Set the Maven JDK version

Adobe recommends that you set the JDK version for the entire Maven execution to `11` in a `.cloudmanager/java-version file`.

To do so, create a file named `.cloudmanager/java-version` in the git repository branch used by the pipeline. Edit the file so that it contains only the text, `11`. While Cloud Manager also accepts a value of `8`, this version is no longer supported for AEM Cloud Service projects. Any other value is ignored. When `11` is specified, Oracle 11 is used and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-11.0.22`. -->

### Een specifieke Java-versie gebruiken {#using-java-support}

In het Cloud Manager-ontwikkelproces wordt standaard gebruikgemaakt van Oracle 8 JDK om projecten te maken, maar AEM Cloud Service-klanten moeten de JDK-versie van Maven voor uitvoering instellen op 21 (voorkeur), 17 of 11.

#### De Maven JDK-versie instellen {#alternate-maven-jdk-version}

Adobe raadt u aan de JDK-versie van Maven-uitvoering in te stellen op `21` of `17` in een `.cloudmanager/java-version` -bestand.

Hiertoe maakt u een bestand met de naam `.cloudmanager/java-version` in de vertakking Git-opslagruimte die door de pijplijn wordt gebruikt. Bewerk het bestand zodat het alleen de tekst `21` of `17` bevat. Hoewel Cloud Manager ook de waarde `8` accepteert, wordt deze versie niet meer ondersteund voor AEM Cloud Service-projecten. Eventuele andere waarden worden genegeerd. Als `21` of `17` is opgegeven, wordt Oracle Java 21 of Oracle Java 17 gebruikt. <!-- Removed this last part as per Brian's feedback on Slack. ...and the `JAVA_HOME` environment variable is set to `/usr/lib/jvm/jdk-21` or `/usr/lib/jvm/jdk-17`. -->


#### Vereisten voor migratie naar gebouwen met Java 21 of Java 17 {#prereq-for-building}

Als u wilt migreren naar gebouwen met Java 21 of Java 17, moet u eerst upgraden naar de nieuwste SonarQube-versie. Voor details, zie de [ Nota&#39;s van de Versie voor Cloud Manager 2025.1.0 ](/help/implementing/cloud-manager/release-notes/current.md#what-is-new).

Wanneer u uw toepassing naar een nieuwe Java-versie (build) en een nieuwe runtimeversie migreert, moet u deze grondig testen in ontwikkelings- en werkgebiedomgevingen voordat u de toepassing implementeert naar productie.

##### Enkele vertaalfuncties {#translation-features}

De volgende functies werken mogelijk niet correct wanneer u werkt met Java 21 of Java 17 en Adobe verwacht deze functies begin 2025 te kunnen oplossen:

* `XLIFF` (XML Localization Interchange File Format) mislukt bij gebruik van Human Translation.
* `I18n` (Internationalisatie) behandelt de taallandinstellingen Hebreeuws (`he`), Indonesisch (`in`) en Jiddisch (`yi`) niet correct als gevolg van wijzigingen in de constructor Locale in nieuwere Java-versies.

#### Runtime-vereisten {#runtime-requirements}

De Java 21-runtime wordt gebruikt voor builds met Java 21 en Java 17 en wordt geleidelijk ook toegepast op Java 11-builds (zie de opmerking hieronder). Om de compatibiliteit te garanderen, zijn de volgende aanpassingen vereist.

Bibliotheekupdates kunnen altijd worden toegepast, omdat ze compatibel blijven met oudere Java-versies.

* **Minimale versie van `org.objectweb.asm`:**
Werk het gebruik van `org.objectweb.asm` naar versie 9.5 of hoger bij om ondersteuning voor nieuwere JVM-runtimes te garanderen.

* **Minimale versie van `org.apache.groovy`:**
Werk het gebruik van `org.apache.groovy` naar versie 4.0.22 of hoger bij om ondersteuning voor nieuwere JVM-runtimes te garanderen.

  Deze bundel kan indirect worden omvat door dergebiedsdelen zoals de AEM Groovy Console toe te voegen.

* **geef een runtime parameter uit:**
Wanneer AEM lokaal wordt uitgevoerd met Java 21, mislukken de beginscripts ( `crx-quickstart/bin/start` of `crx-quickstart/bin/start.bat` ) vanwege de parameter `MaxPermSize` . Als remedie verwijdert u `-XX:MaxPermSize=256M` uit het script of definieert u de omgevingsvariabele `CQ_JVM_OPTS` en stelt u deze in op `-Xmx1024m -Djava.awt.headless=true` .

  De Adobe is van plan dit probleem in een toekomstige release op te lossen.

>[!IMPORTANT]
>
>Wanneer `.cloudmanager/java-version` is ingesteld op `21` of `17` , wordt de Java 21-runtime geïmplementeerd. De Java 21-runtime wordt vanaf donderdag 13 februari 2025 gepland voor geleidelijke implementatie in alle omgevingen (niet alleen die omgevingen waarvan de code is gemaakt met Java 11). De rollout begint met sandboxen en ontwikkelomgevingen en wordt vervolgens in april 2025 in alle productieomgevingen geïmplementeerd. De klanten die Java 21 runtime *willen goedkeuren* kunnen Adobe in [ aemcs-java-adopter@adobe.com ](mailto:aemcs-java-adopter@adobe.com) contacteren.


#### Vereisten voor de buildtijd {#build-time-reqs}

De volgende aanpassingen zijn vereist om het project te kunnen bouwen met Java 21 en Java 17. Ze kunnen al worden bijgewerkt voordat u Java 21 en Java 17 uitvoert, omdat ze compatibel zijn met oudere Java-versies.

* **Minimale versie van `bnd-maven-plugin`:**
Werk het gebruik van `bnd-maven-plugin` naar versie 6.4.0 bij om ondersteuning voor nieuwere JVM-runtimes te garanderen.

  Versies 7 of hoger zijn niet compatibel met Java 11 of lager. Een upgrade naar die versie wordt daarom afgeraden.

* **Minimale versie van `aemanalyser-maven-plugin`:**
Werk het gebruik van `aemanalyser-maven-plugin` naar versie 1.6.6 of hoger bij om ondersteuning voor nieuwere JVM-runtimes te garanderen.

* **Minimale versie van `maven-bundle-plugin`:**
Werk het gebruik van `maven-bundle-plugin` naar versie 5.1.5 of hoger bij om ondersteuning voor nieuwere JVM-runtimes te garanderen.

  Versie 6 of hoger is niet compatibel met Java 11 of lager. Een upgrade naar die versie wordt daarom niet aanbevolen.

* **de gebiedsdelen van de Update in `maven-scr-plugin`:**
`maven-scr-plugin` is niet rechtstreeks compatibel met Java 21 of Java 17. U kunt echter wel descriptorbestanden genereren door de ASM-afhankelijkheidsversie bij te werken in de plug-inconfiguratie, zoals in het volgende voorbeeld wordt getoond:

```XML
<project>
  ...
  <build>
    ...
    <plugins>
      ...
      <plugin>
        <groupId>org.apache.felix</groupId>
        <artifactId>maven-scr-plugin</artifactId>
        <version>1.26.4</version>
        <executions>
          <execution>
            <id>generate-scr-scrdescriptor</id>
            <goals>
              <goal>scr</goal>
            </goals>
          </execution>
        </executions>
        <dependencies>
          <dependency>
            <groupId>org.ow2.asm</groupId>
            <artifactId>asm-analysis</artifactId>
            <version>9.7.1</version>
            <scope>compile</scope>
          </dependency>
        </dependencies>
      </plugin>
      ...
    </plugins>
    ...
  </build>
  ...
</project>
```

## Omgevingsvariabelen - standaard {#environment-variables}

U kunt het noodzakelijk vinden om het bouwstijlproces te variëren dat op informatie over het programma of de pijpleiding wordt gebaseerd.

Als JavaScript bijvoorbeeld tijdens het maken van een product als gulp miniaturen maakt, hebben verschillende miniatuurniveaus de voorkeur voor verschillende omgevingen. Een ontwikkelingsbuild zou een lichtere minificatie kunnen gebruiken in vergelijking met ophaling en productie.

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

## Omgevingsvariabelen - pijpleiding {#pipeline-variables}

Uw bouwstijlproces zou specifieke configuratievariabelen kunnen vereisen die niet in de bewaarplaats van het Git zouden moeten worden opgeslagen. Bovendien, kunt u deze variabelen tussen pijpleidingsuitvoeringen moeten aanpassen gebruikend de zelfde tak.

Zie ook [ vormen de Variabelen van de Pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) voor meer informatie.

## Extra systeempakketten installeren {#installing-additional-system-packages}

Sommige bouwstijlen vereisen extra systeempakketten om volledig te functioneren. Een build kan bijvoorbeeld een Python- of Ruby-script aanroepen en moet een geschikte taalinterpreter hebben geïnstalleerd. Dit installatieproces kan worden beheerd door [`exec-maven-plugin` ](https://www.mojohaus.org/exec-maven-plugin/) in uw `pom.xml` te roepen om APT aan te roepen. Deze uitvoering moet doorgaans worden opgenomen in een Cloud Manager-specifiek Maven-profiel. In dit voorbeeld wordt Python geïnstalleerd.

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
