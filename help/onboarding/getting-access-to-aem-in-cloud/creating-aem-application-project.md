---
title: AEM Application Project - Cloud Service
description: AEM Application Project - Cloud Service
translation-type: tm+mt
source-git-commit: 57206e36725e28051b2468d47da726e318bd763b

---


# Een AEM-toepassingsproject maken {#aem-application-project}

## Wizard gebruiken om een AEM-toepassingsproject te maken {#using-wizard-to-create-an-aem-application-project}

Om nieuwe klanten aan de slag te helpen, kan Cloud Manager nu een minimaal AEM-project maken als startpunt. Dit proces is gebaseerd op het [**AEM Project Archetype **](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Voer de onderstaande stappen uit om een AEM-toepassingsproject te maken in Cloud Manager:

1. Nadat u zich hebt aangemeld bij Cloud Manager en de basisconfiguratie van het programma is voltooid, wordt een speciale aanroep naar een actiekaart weergegeven op het scherm **Overzicht** als de gegevensopslagruimte leeg is.

   ![](assets/create-wizard1.png)

1. Klik op **Maken** om naar het scherm **Een vertakking maken en Project** te navigeren.

   ![](assets/create-wizard2.png)

1. De tegel **Project in uitvoering** wordt weergegeven in het scherm *Program Overview* .

   ![](assets/create-wizard3.png)

1. Nadat het programma is gemaakt, wordt de tegel Omgeving **** toevoegen weergegeven op de pagina *Programmaoverzicht* .
   ![](assets/create-wizard4.png)

   Raadpleeg [Uw omgevingen](/help/implementing/cloud-manager/manage-environments.md) beheren voor meer informatie over het toevoegen of beheren van omgevingen.

## Uw project instellen {#setting-up-your-project}

### Details projectinstelling wijzigen {#modifying-project-setup-details}

Voor een correcte bouw en implementatie met Cloud Manager moeten bestaande AEM-projecten zich aan een aantal basisregels houden:

* Projecten moeten worden gebouwd met Apache Maven.
* Er moet een *pom.xml* -bestand aanwezig zijn in de hoofdmap van de Git-opslagplaats. Dit *pom.xml* -bestand kan verwijzen naar zoveel submodules (die op hun beurt weer andere submodules kunnen hebben, enzovoort) indien nodig.

* U kunt verwijzingen naar extra bewaarplaatsen van het Artefact toevoegen Maven in uw *pom.xml* - dossiers. De toegang tot met een wachtwoord beveiligde of door het netwerk beveiligde gegevensopslagruimten voor artefacten wordt echter niet ondersteund.
* Implementeerbare inhoudspakketten worden ontdekt door te zoeken naar *ZIP* -bestanden van inhoudspakketten die zich in een map met de naam *target* bevinden. Elk aantal submodules kan inhoudspakketten produceren.

* Implementeerbare Dispatcher-artefacten worden gedetecteerd door te zoeken naar *ZIP* -bestanden (opnieuw opgenomen in een map met de naam *target*) met mappen met de naam *conf* en *conf.d*.

* Als er meer dan één inhoudspakket is, wordt de volgorde van pakketimplementaties niet gegarandeerd. Als een specifieke orde nodig is, kunnen de gebiedsdelen van het inhoudspakket worden gebruikt om de orde te bepalen. Pakketten kunnen van plaatsing worden [overgeslagen](#skipping-content-packages) .


## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu. Deze omgeving heeft de volgende kenmerken:

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 18.04.
* Apache Maven 3.6.0 is geïnstalleerd.
* De geïnstalleerde Java-versie is Oracle JDK 8u202.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * grafiesmagick

* Andere pakketten kunnen worden geïnstalleerd tijdens het samenstellen zoals [hieronder](#installing-additional-system-packages)wordt beschreven.
* Elke bouw wordt gedaan op een ongerepte milieu; de bouwstijlcontainer houdt geen staat tussen uitvoeringen.
* Maven wordt altijd uitgevoerd met de opdracht: *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven wordt geconfigureerd op systeemniveau met een bestand settings.xml dat automatisch de openbare Adobe **Artefact** -opslagplaats omvat. (Raadpleeg de [Adobe Public Maven Repository](https://repo.adobe.com/) voor meer informatie.)


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


### Aangepaste omgevingsvariabelen {#custom-environ-variables}

In sommige gevallen kan het constructieproces van een klant afhangen van specifieke configuratievariabelen die niet geschikt zijn om in de opslagplaats voor it te plaatsen. Met Cloud Manager kunnen deze variabelen door een Adobe-vertegenwoordiger per klant worden geconfigureerd. Deze variabelen worden opgeslagen in een veilige opslagplaats en zijn slechts zichtbaar in de bouwstijlcontainer voor de specifieke klant. Klanten die deze functie willen gebruiken, moeten contact opnemen met hun Adobe-vertegenwoordiger om hun variabelen te configureren.

Zodra gevormd, zullen deze variabelen als omgevingsvariabelen beschikbaar zijn. Als u deze eigenschappen als Maven-eigenschappen wilt gebruiken, kunt u ernaar verwijzen in het bestand pom.xml, mogelijk binnen een profiel zoals hierboven beschreven:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <properties>
                  <my.custom.property>${env.MY_CUSTOM_PROPERTY}</my.custom.property>  
            </properties>
        </profile>
```

>[!NOTE]
>
>Namen van omgevingsvariabelen mogen alleen alfanumerieke tekens en onderstrepingstekens (_) bevatten. Volgens de conventie moeten de namen allemaal hoofdletters zijn.

## GeMaven profielen activeren in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In sommige beperkte gevallen moet u het constructieproces mogelijk enigszins variëren wanneer u het uitvoert in Cloud Manager, in tegenstelling tot wanneer het wordt uitgevoerd op ontwikkelaarswerkstations. In deze gevallen kunt u [Maven Profiles](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) gebruiken om te definiëren hoe de build in verschillende omgevingen moet verschillen, waaronder Cloud Manager.

De activering van een Geweven Profiel binnen de de bouwstijlmilieu van de Manager van de Wolk zou moeten worden gedaan door Cm_BUILD milieuvariabele te zoeken die hierboven wordt beschreven. Een profiel dat alleen buiten de buildomgeving van Cloud Manager mag worden gebruikt, moet daarentegen worden uitgevoerd door te zoeken naar de abnormaal werking van deze variabele.

Als u bijvoorbeeld alleen een eenvoudig bericht wilt uitvoeren wanneer de build wordt uitgevoerd in Cloud Manager, doet u het volgende:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                  <property>
                        <name>env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running inside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```

>[!NOTE]
>
>Om dit profiel op een ontwikkelaarwerkstation te testen, kunt u of het op de bevellijn (met `-PcmBuild`) of in uw Geïntegreerde Milieu van de Ontwikkeling (winde) toelaten.

En als u een eenvoudig bericht wilt uitvoeren slechts wanneer de bouwstijl buiten de Manager van de Wolk in werking wordt gesteld, zou u dit doen:

```xml
        <profile>
            <id>notCMBuild</id>
            <activation>
                  <property>
                        <name>!env.CM_BUILD</name>
                  </property>
            </activation>
            <build>
                <plugins>
                    <plugin>
                        <artifactId>maven-antrun-plugin</artifactId>
                        <version>1.8</version>
                        <executions>
                            <execution>
                                <phase>initialize</phase>
                                <configuration>
                                    <target>
                                        <echo>I'm running outside Cloud Manager!</echo>
                                    </target>
                                </configuration>
                                <goals>
                                    <goal>run</goal>
                                </goals>
                            </execution>
                        </executions>
                    </plugin>
                </plugins>
            </build>
        </profile>
```


## Extra systeempakketten installeren {#installing-additional-system-packages}

Voor sommige builds moeten extra systeempakketten worden geïnstalleerd om volledig te kunnen functioneren. Een build kan bijvoorbeeld een Python- of ruby-script aanroepen en moet daarom een geschikte taalinterpreter hebben geïnstalleerd. Dit kan worden gedaan door de [exec-maven-stop](https://www.mojohaus.org/exec-maven-plugin/) aan te roepen APT. Deze uitvoering moet doorgaans worden opgenomen in een specifiek Maven-profiel voor Cloud Manager. Zo kunt u bijvoorbeeld python installeren:

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

Dezelfde techniek kan worden gebruikt om taalspecifieke pakketten te installeren, d.w.z. `gem` voor RubyGems of `pip` voor Python Packages.

>[!NOTE]
>
>Als u een systeempakket op deze manier installeert, wordt dit **niet** geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Neem contact op met uw Adobe-vertegenwoordiger als u een systeempakket op de AEM-omgeving wilt installeren.

## Inhoudspakketten worden overgeslagen {#skipping-content-packages}

In Cloud Manager kunnen builds een willekeurig aantal inhoudspakketten produceren.
Om diverse redenen kan het wenselijk zijn een inhoudspakket te maken, maar het niet te implementeren. Dit kan bijvoorbeeld handig zijn wanneer u inhoudspakketten maakt die alleen voor testen worden gebruikt of die door een andere stap in het constructieproces opnieuw worden verpakt, dat wil zeggen als een subpakket van een ander pakket.

Voor deze scenario&#39;s zoekt Cloud Manager naar een eigenschap met de naam ***cloudManagerTarget*** in de eigenschappen van samengestelde inhoudspakketten. Als dit bezit aan niets wordt geplaatst, zal het pakket worden overgeslagen en niet opgesteld. Het mechanisme om dit bezit te plaatsen hangt van de manier af de bouwstijl het inhoudspakket produceert. Met de insteekmodule filevault kunt u de insteekmodule bijvoorbeeld als volgt configureren:

```xml
        <plugin>
            <groupId>org.apache.jackrabbit</groupId>
            <artifactId>filevault-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```

Met de insteekmodule voor het verpakken van inhoud is deze vergelijkbaar:

```xml
        <plugin>
            <groupId>com.day.jcr.vault</groupId>
            <artifactId>content-package-maven-plugin</artifactId>
            <extensions>true</extensions>
            <configuration>
                <properties>
                    <cloudManagerTarget>none</cloudManagerTarget>
                </properties>
        <!-- other configuration -->
            </configuration>
        </plugin>
```
