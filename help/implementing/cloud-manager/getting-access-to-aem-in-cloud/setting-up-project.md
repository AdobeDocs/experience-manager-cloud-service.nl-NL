---
title: Projectinstelling
description: Leer hoe AEM Projecten met Maven en de normen worden gebouwd u moet waarnemen wanneer het creëren van uw eigen project.
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 88b4864da30fbf201dbd5bde1ac17d3be977648f
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# Projectinstelling {#project-setup}

Leer hoe AEM Projecten met Maven en de normen worden gebouwd u moet waarnemen wanneer het creëren van uw eigen project.

## Details projectinstelling {#project-setup-details}

Om met Cloud Manager succesvol te bouwen en op te stellen, moeten AEM Projecten aan de volgende richtlijnen voldoen:

* De projecten moeten worden gebouwd gebruikend [ Apache Maven ](https://maven.apache.org).
* Er moet een `pom.xml` -bestand aanwezig zijn in de hoofdmap van de it-opslagplaats. Dit bestand van `pom.xml` kan verwijzen naar zoveel submodules (die op hun beurt weer andere submodules kunnen hebben, enzovoort) als dat nodig is.
* U kunt verwijzingen naar extra bewaarplaatsen van het Artefact toevoegen Maven in uw `pom.xml` dossiers. De toegang tot [ wachtwoord-beschermde artefactrepositories ](#password-protected-maven-repositories) wordt gesteund wanneer gevormd. Toegang tot door het netwerk beveiligde gegevensbestanden voor artefacten wordt echter niet ondersteund.
* Implementeerbare inhoudspakketten worden ontdekt door te zoeken naar `.zip` -bestanden voor inhoudspakketten, die zich in een map met de naam `target` bevinden. Elk aantal submodules kan inhoudspakketten produceren.
* Inzetbare Dispatcher-artefacten worden gevonden door te zoeken naar `.zip` -bestanden (ook in de map met de naam `target` ) met mappen met de naam `conf` en `conf.d` .
* Als er meer dan één inhoudspakket is, wordt de volgorde van pakketimplementaties niet gegarandeerd. Als een specifieke orde nodig is, kunnen de gebiedsdelen van het inhoudspakket worden gebruikt om de orde te bepalen.
* De pakketten kunnen [ worden overgeslagen ](#skipping-content-packages) tijdens plaatsing.

## Geweven profielen activeren in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In sommige beperkte gevallen kan het zijn dat u het constructieproces iets moet variëren wanneer u in Cloud Manager werkt, in tegenstelling tot wanneer u op ontwikkelaarswerkstations werkt. Voor deze gevallen, [ Gemaakt profielen ](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) kunnen worden gebruikt om te bepalen hoe de bouwstijl in verschillende milieu&#39;s, met inbegrip van Cloud Manager verschillend zou moeten zijn.

De activering van een Geweven profiel binnen Cloud Manager bouwt milieu zou moeten worden gedaan door `CM_BUILD` [ milieuvariabele ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) te zoeken. Evenzo moet een profiel dat alleen buiten de Cloud Manager-ontwikkelomgeving moet worden gebruikt, worden uitgevoerd door te zoeken naar de afwezigheid van deze variabele.

Als u bijvoorbeeld een eenvoudig bericht wilt uitvoeren wanneer de build in Cloud Manager wordt uitgevoerd, doet u het volgende:

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
>Als u dit profiel wilt testen op een werkstation voor ontwikkelaars, kunt u het in de opdrachtregel (met `-PcmBuild` ) of in de geïntegreerde ontwikkelomgeving (IDE) inschakelen.

En als u een eenvoudig bericht wilde uitvoeren slechts wanneer de bouwstijl buiten Cloud Manager in werking wordt gesteld, zou u het volgende doen:

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

## Een met wachtwoord beveiligde Maven-opslagplaats gebruiken in Cloud Manager {#password-protected-maven-repositories}

>[!NOTE]
>
>Stel artefacten van wachtwoord-beschermde Gegeven bewaarplaatsen voorzichtig op, aangezien Cloud Manager deze code niet met zijn [ regels van de codekwaliteit ](/help/implementing/cloud-manager/custom-code-quality-rules.md) evalueert. Deze methode moet worden gereserveerd voor zeldzame situaties en alleen worden toegepast op code die geen verband houdt met AEM. De Adobe adviseert het omvatten van zowel de bronnen van Java als de volledige projectbroncode samen met binair getal. Dit zorgt voor meer transparantie en onderhoudsgemak tijdens het gehele implementatieproces.

**om een wachtwoord-beschermde Gegeven bewaarplaats binnen Cloud Manager te gebruiken:**

1. Specificeer het wachtwoord (en naar keuze, de gebruikersbenaming) als geheime [ pijpleidingsvariabele ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md).
1. Dan verwijzing dat geheim binnen een dossier genoemd `.cloudmanager/maven/settings.xml` in de git bewaarplaats, die het [ Gemaakte schema van het Dossier van Montages ](https://maven.apache.org/settings.html) volgt.

Wanneer het Cloud Manager-constructieproces start:

* Het element `<servers>` in dit bestand wordt samengevoegd in het standaardbestand van `settings.xml` dat door Cloud Manager wordt geleverd.
   * Server-id&#39;s die beginnen met `adobe` en `cloud-manager` worden als gereserveerd beschouwd. Gebruik deze niet op aangepaste servers.
   * Cloud Manager spiegelt alleen de server-id&#39;s die overeenkomen met specifieke voorvoegsels of de standaard-id `central` . Alle andere server-id&#39;s worden niet gespiegeld.
* Als dit bestand is geïnstalleerd, wordt vanuit een element `<repository>` en/of `<pluginRepository>` in het bestand `pom.xml` naar de server-id verwezen.
* Over het algemeen, zijn deze `<repository>` en `<pluginRepository>` elementen inbegrepen binnen a [ Cloud Manager-Specifieke profiel ](#activating-maven-profiles-in-cloud-manager), hoewel hun opneming niet strikt vereist is.

Stel bijvoorbeeld dat de repository zich op `https://repository.myco.com/maven2` bevindt, dat de gebruikersnaam die Cloud Manager moet gebruiken `cloudmanager` is en dat het wachtwoord `secretword` is. Voer de volgende stappen uit:

1. Plaats het wachtwoord als geheim in de pijpleiding.

   ```text
   $ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`
   ```

1. Verwijs naar dit geheim van het `.cloudmanager/maven/settings.xml` dossier in het volgende:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <settings xmlns="https://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="https://maven.apache.org/SETTINGS/1.0.0 https://maven.apache.org/xsd/settings-1.0.0.xsd">
       <servers>
           <server>
               <id>myco-repository</id>
               <username>cloudmanager</username>
              <password>${env.CUSTOM_MYCO_REPOSITORY_PASSWORD}</password>
           </server>
       </servers>
   </settings>
   ```

1. Verwijs ten slotte de server-id in het `pom.xml` -bestand:

   ```xml
   <profiles>
       <profile>
           <id>cmBuild</id>
           <activation>
                   <property>
                       <name>env.CM_BUILD</name>
                   </property>
           </activation>
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
       </profile>
   </profiles>
   ```

### Bronnen implementeren {#deploying-sources}

Het is een goede praktijk om de bronnen van Java samen met binair aan een Geweven bewaarplaats op te stellen.

Om dit te doen, vorm maven-bron-stop in uw project.

```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-source-plugin</artifactId>
             <executions>
                 <execution>
                     <id>attach-sources</id>
                     <goals>
                         <goal>jar-no-fork</goal>
                     </goals>
                 </execution>
             </executions>
         </plugin>
```

### Projectbronnen implementeren {#deploying-project-sources}

Het is een goede praktijk om de volledige projectbron samen met binair aan een Geweven bewaarplaats op te stellen. Zo kan het exacte artefact opnieuw opbouwen.

Vorm maven-assemblage-stop in uw project op de volgende manier:

```xml
         <plugin>
             <groupId>org.apache.maven.plugins</groupId>
             <artifactId>maven-assembly-plugin</artifactId>
             <executions>
                 <execution>
                     <id>project-assembly</id>
                     <phase>package</phase>
                     <goals>
                         <goal>single</goal>
                     </goals>
                     <configuration>
                         <descriptorRefs>
                             <descriptorRef>project</descriptorRef>
                         </descriptorRefs>
                     </configuration>
                 </execution>
             </executions>
         </plugin>
```

## Inhoudspakketten worden overgeslagen {#skipping-content-packages}

In Cloud Manager kunnen builds een willekeurig aantal inhoudspakketten produceren. Om diverse redenen is het misschien gewenst om een inhoudspakket te maken, maar dit niet te implementeren. Een voorbeeld doet zich voor wanneer inhoudspakketten alleen voor testdoeleinden worden gebouwd of wanneer een andere stap in het constructieproces deze opnieuw verpakt. Dit is een subpakket van een ander pakket.

Cloud Manager zoekt naar een eigenschap met de naam `cloudManagerTarget` in de eigenschappen van samengestelde inhoudspakketten om deze scenario&#39;s te kunnen gebruiken. Als deze eigenschap is ingesteld op `none` , wordt het pakket overgeslagen en niet geïmplementeerd.

Het mechanisme om dit bezit te plaatsen hangt van de manier af bouwt het inhoudspakket produceert. Met de `filevault-maven-plugin` configureert u bijvoorbeeld de insteekmodule als volgt.

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

De `content-package-maven-plugin` heeft een vergelijkbare configuratie.

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

## Artefacthergebruik maken {#build-artifact-reuse}

In veel gevallen, wordt de zelfde code opgesteld aan veelvoudige AEM milieu&#39;s. Waar mogelijk, vermijdt Cloud Manager het herbouwen van de codebasis wanneer het ontdekt dat het zelfde gat begaan wordt gebruikt in veelvoudige full-stack pijpleidinguitvoeringen.

Wanneer een uitvoering is begonnen, begaat de huidige HEAD voor de takpijpleiding wordt gehaald. De commit hash is zichtbaar in UI en via API. Wanneer de bouwstijlstap met succes voltooit, worden de resulterende artefacten opgeslagen gebaseerd op die knoeiboel begaan en kunnen in verdere pijpleidingsuitvoeringen opnieuw worden gebruikt.

Pakketten worden opnieuw gebruikt via pijpleidingen als ze zich in hetzelfde programma bevinden. Wanneer u pakketten zoekt die opnieuw kunnen worden gebruikt, negeert AEM vertakkingen en hergebruikt artefacten tussen vertakkingen.

Wanneer een hergebruik voorkomt, worden de bouw en de stappen van de codekwaliteit effectief vervangen met de resultaten van de originele uitvoering. Het logboekdossier voor de bouwstijlstap maakt een lijst van de artefacten en de uitvoeringsinformatie die werd gebruikt om hen oorspronkelijk te bouwen.

Hieronder ziet u een voorbeeld van een dergelijke loguitvoer.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Het logboek van de stap van de codekwaliteit bevat gelijkaardige informatie.

### Voorbeelden {#example-reuse}

#### Voorbeeld 1 {#example-1}

Houd er rekening mee dat uw programma twee ontwikkelingspijplijnen heeft:

* Pijpleiding 1 op vertakking `foo`
* Pijpleiding 2 op vertakking `bar`

Beide vertakkingen zijn op zelfde verbind identiteitskaart

1. Als u Pipeline 1 uitvoert, worden de pakketten normaal gebouwd.
1. Dan, gebruikt het lopen Pijpleiding 2 de pakketten opnieuw die door Pijpleiding 1 worden gecreeerd.

#### Voorbeeld 2 {#example-2}

Houd er rekening mee dat uw programma twee vertakkingen heeft:

* Branch `foo`
* Branch `bar`

Beide vertakkingen hebben zelfde verbind identiteitskaart

1. Een ontwikkelingspijplijn bouwt en voert `foo` uit.
1. Vervolgens wordt een productiepijplijn gebouwd en uitgevoerd `bar` .

In dit geval wordt het artefact van `foo` opnieuw gebruikt voor de productiepijplijn aangezien dezelfde commit hash werd geïdentificeerd.

### Afmelden {#opting-out}

Indien gewenst, kan het hergebruikgedrag voor specifieke pijpleidingen worden onbruikbaar gemaakt door de pijpleidingsvariabele `CM_DISABLE_BUILD_REUSE` aan `true` te plaatsen. Als deze variabele wordt geplaatst, haalt het systeem de geënquêteerde knoeiboel uit en slaat de resulterende artefacten voor later gebruik op maar hergebruikt eerder opgeslagen artefacten. Overweeg het volgende scenario om dit gedrag te begrijpen:

1. Er wordt een nieuwe pijpleiding gemaakt.
1. De pijpleiding wordt uitgevoerd (uitvoering #1) en de huidige HEAD begaan is `becdddb`. De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De variabele `CM_DISABLE_BUILD_REUSE` wordt ingesteld.
1. De pijpleiding wordt opnieuw uitgevoerd zonder code te veranderen. Hoewel er opgeslagen artefacten aan `becdddb` worden geassocieerd, worden zij niet opnieuw gebruikt toe te schrijven aan de `CM_DISABLE_BUILD_REUSE` variabele.
1. De code wordt veranderd en de pijpleiding wordt uitgevoerd. De HEAD commit is nu `f6ac5e6` . De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De variabele `CM_DISABLE_BUILD_REUSE` wordt verwijderd.
1. De pijpleiding wordt re-uitgevoerd zonder de code te veranderen. Aangezien er opgeslagen artefacten verbonden aan `f6ac5e6` zijn, worden die artefacten opnieuw gebruikt.

### Caveats {#caveats}

* Artefacten van de bouwstijl worden niet opnieuw gebruikt over verschillende programma&#39;s, ongeacht als de commit knoeiboel identiek is.
* De kunstmatigheden van de bouwstijl worden opnieuw gebruikt binnen het zelfde programma zelfs als de tak en/of de pijpleiding verschillend is.
* [ Gemaakt versie behandelend ](/help/implementing/cloud-manager/managing-code/project-version-handling.md) vervangt de projectversie slechts in productiepijpleidingen.
Als het zelfde begaat voor zowel een ontwikkelings opstellen als productiepijpleiding, en de ontwikkeling stelt looppas eerst in, worden de versies opgesteld aan stadium en de productie onveranderd. In dit geval wordt echter nog steeds een tag gemaakt.
* Als de terugwinning van de opgeslagen artefacten niet succesvol is, wordt de bouwstijlstap in werking gesteld alsof geen artefacten werden opgeslagen.
* Andere pijplijnvariabelen dan `CM_DISABLE_BUILD_REUSE` worden niet in aanmerking genomen wanneer Cloud Manager besluit eerder gemaakte constructieartefacten opnieuw te gebruiken.
