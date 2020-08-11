---
title: Toepassingsproject AEM - Cloud Service
description: Toepassingsproject AEM - Cloud Service
translation-type: tm+mt
source-git-commit: 1dfc9cfaba4c7701ebca58346d6eec6b946dd517
workflow-type: tm+mt
source-wordcount: '1442'
ht-degree: 9%

---


# Een AEM-applicatieproject maken {#aem-application-project}

## Het gebruiken van Tovenaar om een Project van de AEMToepassing te creëren {#using-wizard-to-create-an-aem-application-project}

Om nieuwe klanten aan de slag te helpen, kan Cloud Manager nu een minimaal AEM project maken als startpunt. Dit proces is gebaseerd op het [**AEM Project Archetype **](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Voer de onderstaande stappen uit om een AEM toepassingsproject te maken in Cloud Manager:

1. Nadat u zich hebt aangemeld bij Cloud Manager en de basisconfiguratie van het programma is voltooid, wordt een speciale aanroep naar een actiekaart weergegeven op het scherm **Overzicht** als de opslagplaats leeg is.

   ![](assets/create-wizard1.png)

1. Klik op **Maken** om naar het scherm **Een vertakking en een project maken** te gaan.

   ![](assets/create-wizard2.png)

1. De tegel **Project in uitvoering** wordt weergegeven in het scherm *Program Overview* .

   ![](assets/create-wizard3.png)

1. Nadat het programma is gemaakt, wordt de tegel **Omgeving toevoegen** weergegeven op de pagina *Programmaoverzicht*.
   ![](assets/create-wizard4.png)

   Raadpleeg [Uw omgevingen](/help/implementing/cloud-manager/manage-environments.md) beheren voor meer informatie over het toevoegen of beheren van omgevingen.

## Uw project instellen {#setting-up-your-project}

### Details projectinstelling wijzigen {#modifying-project-setup-details}

Om te kunnen worden gebouwd en geïmplementeerd met Cloud Manager, moeten bestaande AEM projecten zich aan een aantal basisregels houden:

* Projecten moeten worden gebouwd met Apache Maven.
* Er moet een *pom.xml* -bestand aanwezig zijn in de hoofdmap van de Git-opslagplaats. Dit *pom.xml* -bestand kan verwijzen naar zoveel submodules (die op hun beurt weer andere submodules kunnen hebben, enzovoort) indien nodig.

* U kunt verwijzingen naar extra bewaarplaatsen van het Artefact toevoegen Maven in uw *pom.xml* - dossiers. Toegang tot met [wachtwoord beveiligde gegevensopslagruimten](#password-protected-maven-repositories) voor artefacten wordt ondersteund wanneer dit is geconfigureerd. Toegang tot door het netwerk beveiligde gegevensbestanden voor artefacten wordt echter niet ondersteund.
* Implementeerbare inhoudspakketten worden ontdekt door te zoeken naar *ZIP* -bestanden van inhoudspakketten die zich in een map met de naam *target* bevinden. Elk aantal submodules kan inhoudspakketten produceren.

* Implementeerbare Dispatcher-artefacten worden gedetecteerd door te zoeken naar *ZIP* -bestanden (opnieuw opgenomen in een map met de naam *target*) met mappen met de naam *conf* en *conf.d*.

* Als er meer dan één inhoudspakket is, wordt de volgorde van pakketimplementaties niet gegarandeerd. Als een specifieke orde nodig is, kunnen de gebiedsdelen van het inhoudspakket worden gebruikt om de orde te bepalen. Pakketten kunnen van plaatsing worden [overgeslagen](#skipping-content-packages) .


## Omgevingsdetails samenstellen {#build-environment-details}

Cloud Manager bouwt en test uw code gebruikend een gespecialiseerde bouwstijlmilieu. Deze omgeving heeft de volgende kenmerken:

* De ontwikkelomgeving is gebaseerd op Linux en is afgeleid van Ubuntu 18.04.
* Apache Maven 3.6.0 is geïnstalleerd.
* Er zijn enkele extra systeempakketten geïnstalleerd die nodig zijn:

   * bzip2
   * unzip
   * libpng
   * imagemagick
   * grafiesmagick

* Andere pakketten kunnen worden geïnstalleerd tijdens het samenstellen zoals [hieronder](#installing-additional-system-packages)wordt beschreven.
* Elke bouw wordt gedaan op een ongerepte milieu; de bouwstijlcontainer houdt geen staat tussen uitvoeringen.
* Maven wordt altijd uitgevoerd met de opdracht: *mvn —batch-mode clean org.jacoco:jacoco-maven-plugin:prepare-agent package*
* Maven wordt gevormd op systeemniveau met een settings.xml- dossier dat automatisch de openbare bewaarplaats van het **Artefact** van de Adobe omvat. (Zie [Adobe Public Maven Repository](https://repo.adobe.com/) voor meer informatie.)

>[!NOTE]
>Hoewel in Cloud Manager geen specifieke versie van de versie wordt gedefinieerd, moet de gebruikte versie minstens `jacoco-maven-plugin``0.7.5.201505241946`zijn.


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

Met Cloud Manager kunnen deze variabelen per pijpleiding worden geconfigureerd via de Cloud Manager API of Cloud Manager CLI. Variabelen kunnen worden opgeslagen als onbewerkte tekst of in rust worden versleuteld. In beide gevallen worden variabelen binnen de ontwikkelomgeving beschikbaar gemaakt als een omgevingsvariabele waarnaar vervolgens kan worden verwezen vanuit het `pom.xml` bestand of andere constructiescripts.

Om een variabele te plaatsen die CLI gebruiken, stel een bevel als in werking:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test`

Huidige variabelen kunnen worden weergegeven:

`$ aio cloudmanager:list-pipeline-variables PIPELINEID`

Namen van variabelen mogen alleen alfanumerieke tekens en onderstrepingstekens (_) bevatten. Volgens de conventie moeten de namen allemaal hoofdletters zijn. Er geldt een limiet van 200 variabelen per pijpleiding. Elke naam moet uit minder dan 100 tekens bestaan en elke waarde moet uit minder dan 2048 tekens bestaan.

Wanneer deze variabelen in een `Maven pom.xml` bestand worden gebruikt, is het doorgaans handig om deze variabelen aan de hand van een vergelijkbare syntaxis toe te wijzen aan de eigenschappen Maven:

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

## Ondersteuning voor met wachtwoord beveiligde gegevensopslagruimte {#password-protected-maven-repositories}

Als u een met een wachtwoord beveiligde gegevensopslagruimte vanuit Cloud Manager wilt gebruiken, geeft u het wachtwoord (en eventueel de gebruikersnaam) op als een geheime [Pipeline-variabele](#pipeline-variables) en verwijst u naar dat geheim in een bestand dat in de gegevensopslagruimte `.cloudmanager/maven/settings.xml` is genoemd. Dit bestand volgt het schema [Maven Settings File](https://maven.apache.org/settings.html) . Wanneer het buildproces van Cloud Manager wordt gestart, wordt het `<servers>` `settings.xml` element in dit bestand samengevoegd met het standaardbestand dat wordt geleverd door Cloud Manager. Server-id&#39;s die beginnen met `adobe` en `cloud-manager` worden beschouwd als gereserveerd en mogen niet worden gebruikt door aangepaste servers. Server-id&#39;s komen **niet** overeen met een van deze voorvoegsels, anders `central` wordt de standaard-id nooit weerspiegeld door Cloud Manager. Als dit bestand is geïnstalleerd, wordt er vanuit een `<repository>` en/of `<pluginRepository>` element in het `pom.xml` bestand naar de server-id verwezen. Over het algemeen worden deze `<repository>` en/of `<pluginRepository>` elementen opgenomen in een specifiek profiel [voor](#activating-maven-profiles-in-cloud-manager)Cloud Manager, hoewel dat niet strikt noodzakelijk is.

Stel bijvoorbeeld dat de gegevensopslagruimte zich bevindt op https://repository.myco.com/maven2, dat de gebruikersnaam is ingesteld op Cloud Manager `cloudmanager` en dat het wachtwoord is `secretword`.

Plaats eerst het wachtwoord als geheim op de pijpleiding:

`$ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`

Verwijs dit vervolgens vanuit het `.cloudmanager/maven/settings.xml` bestand:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
    <servers>
        <server>
            <id>myco-repository</id>
            <username>cloudmanager</username>
            <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
        </server>
    </servers>
</settings>
```

En ten slotte verwijs naar de server-id in het `pom.xml` bestand:

```xml
<profiles>
    <profile>
        <id>cmBuild</id>
        <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
        </activation>
        <build>
            <repositories>
                <repository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>myco-repository</id>
                    <name>MyCo Releases</name>
                    <url>https://repository.myco.com/maven2</url>
                    <snapshots>
                        <enabled>false</enabled>
                    </snapshots>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                </pluginRepository>
            </pluginRepositories>
        </build>
    </profile>
</profiles>
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
>Als u een systeempakket op deze manier installeert, wordt dit **niet** geïnstalleerd in de runtimeomgeving die voor het uitvoeren van Adobe Experience Manager wordt gebruikt. Als u een systeempakket nodig hebt dat op de AEM-omgeving is geïnstalleerd, neemt u contact op met uw Adobe-vertegenwoordiger.

## Inhoudspakketten worden overgeslagen {#skipping-content-packages}

In Cloud Manager kunnen builds een willekeurig aantal inhoudspakketten produceren.
Om diverse redenen kan het wenselijk zijn een inhoudspakket te maken, maar het niet te implementeren. Dit kan bijvoorbeeld handig zijn wanneer u inhoudspakketten maakt die alleen voor testen worden gebruikt of die door een andere stap in het constructieproces opnieuw worden verpakt, dat wil zeggen als een subpakket van een ander pakket.

Voor deze scenario&#39;s zoekt Cloud Manager naar een eigenschap met de naam ***cloudManagerTarget*** in de eigenschappen van samengestelde contentpakketten. Als deze eigenschap is ingesteld op Geen, zal het pakket worden overgeslagen en niet geïmplementeerd. Het mechanisme om deze eigenschap in te stellen hangt af van de manier waarop de build het contentpakket produceert. Met de invoegtoepassing filevault-maven-plugin kunt u de invoegtoepassing bijvoorbeeld als volgt configureren:

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
