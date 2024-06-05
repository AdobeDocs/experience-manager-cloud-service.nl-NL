---
title: Projectinstelling
description: Leer hoe AEM projecten met Maven en de normen worden gebouwd u moet waarnemen wanneer het creëren van uw eigen project.
exl-id: 76af0171-8ed5-4fc7-b5d5-7da5a1a06fa8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1399'
ht-degree: 0%

---

# Projectinstelling {#project-setup}

Leer hoe AEM projecten met Maven en de normen worden gebouwd u moet waarnemen wanneer het creëren van uw eigen project.

## Details projectinstelling {#project-setup-details}

Voor een geslaagde ontwikkeling en implementatie met Cloud Manager moeten AEM projecten zich aan de volgende richtlijnen houden:

* De projecten moeten worden gebouwd gebruikend [Apache Maven.](https://maven.apache.org)
* Er moet een `pom.xml` in de hoofdmap van de it-opslagplaats. Dit `pom.xml` bestand kan verwijzen naar zoveel submodules (die op hun beurt weer andere submodules kunnen hebben, enzovoort) als dat nodig is.
* U kunt verwijzingen toevoegen naar extra gegevensopslagruimten voor vervormingen in uw `pom.xml` bestanden.
   * Toegang tot [met wachtwoord beveiligde gegevensbanken voor artefacten](#password-protected-maven-repositories) wordt gesteund wanneer gevormd. Toegang tot door het netwerk beveiligde gegevensbestanden voor artefacten wordt echter niet ondersteund.
* Implementeerbare inhoudspakketten worden gedetecteerd door te zoeken naar een inhoudspakket `.zip` bestanden, die zich in een map met de naam `target`.
   * Elk aantal submodules kan inhoudspakketten produceren.
* Inzetbare verzenders worden gedetecteerd door te scannen op `.zip` bestanden (ook opgenomen in de map genaamd `target`), die mappen met naam hebben `conf` en `conf.d`.
* Als er meer dan één inhoudspakket is, wordt de volgorde van pakketimplementaties niet gegarandeerd.
   * Als een specifieke orde nodig is, kunnen de gebiedsdelen van het inhoudspakket worden gebruikt om de orde te bepalen.
* Verpakkingen kunnen [overgeslagen](#skipping-content-packages) tijdens de implementatie.

## GeMaven profielen activeren in Cloud Manager {#activating-maven-profiles-in-cloud-manager}

In sommige beperkte gevallen moet u het constructieproces mogelijk enigszins variëren wanneer u werkt in Cloud Manager, in tegenstelling tot wanneer u werkt op ontwikkelaarswerkstations. In deze gevallen: [Geweven profielen](https://maven.apache.org/guides/introduction/introduction-to-profiles.html) kan worden gebruikt om te definiëren hoe de build in verschillende omgevingen moet verschillen, waaronder Cloud Manager.

Als u een Maven-profiel activeert in de ontwerpomgeving van Cloud Manager, moet u zoeken naar de `CM_BUILD` [omgevingsvariabele](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md). Op dezelfde manier moet een profiel dat alleen buiten de buildomgeving van Cloud Manager moet worden gebruikt, worden uitgevoerd door te zoeken naar de afwezigheid van deze variabele.

Als u bijvoorbeeld alleen een eenvoudig bericht wilt uitvoeren wanneer de build wordt uitgevoerd in Cloud Manager, doet u dit.

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
>Als u dit profiel op een werkstation voor ontwikkelaars wilt testen, kunt u het op de opdrachtregel inschakelen (met `-PcmBuild`) of in uw geïntegreerde ontwikkelomgeving (IDE).

En als u een eenvoudig bericht alleen wilt uitvoeren wanneer de build buiten Cloud Manager wordt uitgevoerd, doet u dit.

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

>[!NOTE]
>
>Artefacten van een met wachtwoord beveiligde Maven-opslagplaats moeten voorzichtig worden gebruikt omdat code die via dit mechanisme wordt geïmplementeerd, momenteel niet wordt uitgevoerd [code quality rules](/help/implementing/cloud-manager/custom-code-quality-rules.md) geïmplementeerd in de kwaliteitspoort van Cloud Manager. Daarom mag het alleen worden gebruikt in zeldzame gevallen en voor code die niet aan AEM is gekoppeld. Het wordt geadviseerd om de bronnen van Java en de volledige code van de projectbron samen met het binaire getal op te stellen.

Een met wachtwoord beveiligde Maven-opslagplaats gebruiken in Cloud Manager:

1. Geef het wachtwoord (en eventueel de gebruikersnaam) op als geheim [pijpleidingvariabele](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md).
1. Verwijs dan naar dat geheim binnen een dossier genoemd `.cloudmanager/maven/settings.xml` in de git-opslagplaats, die volgt op de [Maven Settings-bestand](https://maven.apache.org/settings.html) schema.

Wanneer het buildproces van Cloud Manager wordt gestart:

* De `<servers>` element in dit bestand wordt samengevoegd tot het standaardelement `settings.xml` bestand geleverd door Cloud Manager.
   * Server-id&#39;s die beginnen met `adobe` en `cloud-manager` worden als gereserveerd beschouwd. Gebruik deze niet op aangepaste servers.
   * Server-id&#39;s die niet overeenkomen met een van deze voorvoegsels of de standaard-id `central` wordt nooit weerspiegeld door Cloud Manager.
* Als dit bestand is geïnstalleerd, wordt vanuit een `<repository>` en/of `<pluginRepository>` element binnen de `pom.xml` bestand.
* Over het algemeen: `<repository>` en/of `<pluginRepository>` elementen zouden in een [Specifiek profiel voor Cloud Manager](#activating-maven-profiles-in-cloud-manager), hoewel dat niet strikt noodzakelijk is.

Als voorbeeld, laten we zeggen dat de bewaarplaats is bij `https://repository.myco.com/maven2`is de gebruikersnaam die Cloud Manager moet gebruiken: `cloudmanager`en het wachtwoord is `secretword`. Voer de volgende stappen uit.

1. Plaats het wachtwoord als geheim in de pijpleiding.

   ```text
   $ aio cloudmanager:set-pipeline-variables PIPELINEID --secret CUSTOM_MYCO_REPOSITORY_PASSWORD secretword`
   ```

1. Verwijs hier vanuit de `.cloudmanager/maven/settings.xml` bestand.

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

1. Verwijs ten slotte de server-id binnen de `pom.xml` bestand:

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

Het is een goede praktijk om de volledige projectbron samen met binair aan een Geweven bewaarplaats op te stellen. Hierdoor kan het exacte artefact opnieuw worden opgebouwd.

Om dit te doen, vorm maven-assemblage-stop in uw project.

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

In Cloud Manager kunnen builds een willekeurig aantal inhoudspakketten produceren. Om diverse redenen is het misschien gewenst om een inhoudspakket te maken, maar dit niet te implementeren. Een voorbeeld zou kunnen zijn wanneer het bouwen van inhoudspakketten die slechts voor het testen worden gebruikt of die door een andere stap in het bouwstijlproces worden herverpakt. Dit is een subpakket van een ander pakket.

Voor deze scenario&#39;s zoekt Cloud Manager naar een eigenschap met de naam `cloudManagerTarget` in de eigenschappen van samengestelde inhoudspakketten. Als deze eigenschap is ingesteld op `none`, wordt het pakket overgeslagen en niet geïmplementeerd.

Het mechanisme om dit bezit te plaatsen hangt van de manier af bouwt het inhoudspakket produceert. Met de `filevault-maven-plugin` u zou de stop als volgt vormen.

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

In veel gevallen, wordt de zelfde code opgesteld aan veelvoudige AEM milieu&#39;s. Waar mogelijk, zal de Manager van de Wolk vermijden herbouwend de codebasis wanneer het ontdekt dat het zelfde gat begaan wordt gebruikt in veelvoudige full-stack pijpleidinguitvoeringen.

Wanneer een uitvoering is begonnen, begaat de huidige HEAD voor de takpijpleiding wordt gehaald. De commit hash is zichtbaar in UI en via API. Wanneer de bouwstijlstap met succes voltooit, worden de resulterende artefacten opgeslagen gebaseerd op die knoeiboel begaan en kunnen in verdere pijpleidingsuitvoeringen opnieuw worden gebruikt.

Pakketten worden opnieuw gebruikt via pijpleidingen als ze zich in hetzelfde programma bevinden. Wanneer u pakketten zoekt die opnieuw kunnen worden gebruikt, negeert AEM vertakkingen en hergebruikt artefacten tussen vertakkingen.

Wanneer een hergebruik voorkomt, worden de bouw en de stappen van de codekwaliteit effectief vervangen met de resultaten van de originele uitvoering. Het logboekdossier voor de bouwstijlstap zal van de artefacten en de uitvoeringsinformatie een lijst maken die werd gebruikt om hen oorspronkelijk te bouwen.

Hieronder ziet u een voorbeeld van een dergelijke loguitvoer.

```shell
The following build artifacts were reused from the prior execution 4 of pipeline 1 which used commit f6ac5e6943ba8bce8804086241ba28bd94909aef:
build/aem-guides-wknd.all-2021.1216.1101633.0000884042.zip (content-package)
build/aem-guides-wknd.dispatcher.cloud-2021.1216.1101633.0000884042.zip (dispatcher-configuration)
```

Het logboek van de stap van de codekwaliteit zal gelijkaardige informatie bevatten.

### Voorbeelden {#example-reuse}

#### Voorbeeld 1 {#example-1}

Houd er rekening mee dat uw programma twee ontwikkelingspijplijnen heeft:

* Pijpleiding 1 op vertakking `foo`
* Pijpleiding 2 op vertakking `bar`

Beide vertakkingen zijn op zelfde verbind identiteitskaart

1. De lopende Pijpleiding 1 zal eerst de pakketten normaal bouwen.
1. Dan zal het lopen Pijpleiding 2 pakketten hergebruiken die door Pijpleiding 1 worden gecreeerd.

#### Voorbeeld 2 {#example-2}

Houd er rekening mee dat uw programma twee vertakkingen heeft:

* Branch `foo`
* Branch `bar`

Beide vertakkingen hebben zelfde verbind identiteitskaart

1. Een ontwikkelingspijplijn bouwt en voert uit `foo`.
1. Daarna bouwt en voert een productiepijpleiding uit `bar`.

In dit geval is het artefact van `foo` wordt opnieuw gebruikt voor de productiepijpleiding aangezien dezelfde &quot;commit hash&quot; is geïdentificeerd.

### Afmelden {#opting-out}

Indien gewenst, kan het hergebruikgedrag voor specifieke pijpleidingen door de pijpleidingsvariabele te plaatsen worden onbruikbaar gemaakt `CM_DISABLE_BUILD_REUSE` tot `true`. Als deze variabele wordt geplaatst, begaan hash nog wordt gehaald en de resulterende artefacten voor later gebruik worden opgeslagen, maar om het even welke eerder opgeslagen artefacten zullen niet opnieuw worden gebruikt. Overweeg het volgende scenario om dit gedrag te begrijpen.

1. Er wordt een nieuwe pijpleiding gemaakt.
1. De pijpleiding wordt uitgevoerd (uitvoering #1) en de huidige HEAD begaan is `becdddb`. De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De `CM_DISABLE_BUILD_REUSE` variable is set.
1. De pijpleiding wordt opnieuw uitgevoerd zonder code te veranderen. Hoewel er opgeslagen artefacten verbonden aan zijn `becdddb`, worden zij niet opnieuw gebruikt vanwege `CM_DISABLE_BUILD_REUSE` variabele.
1. De code wordt veranderd en de pijpleiding wordt uitgevoerd. De HEAD commit is nu `f6ac5e6`. De uitvoering is geslaagd en de resulterende artefacten worden opgeslagen.
1. De `CM_DISABLE_BUILD_REUSE` variabele wordt verwijderd.
1. De pijpleiding wordt re-uitgevoerd zonder de code te veranderen. Aangezien er opgeslagen artefacten verbonden aan zijn `f6ac5e6`, worden deze artefacten opnieuw gebruikt.

### Caveats {#caveats}

* Artefacten van de bouwstijl worden niet opnieuw gebruikt over verschillende programma&#39;s, ongeacht als de commit knoeiboel identiek is.
* De kunstmatigheden van de bouwstijl worden opnieuw gebruikt binnen het zelfde programma zelfs als de tak en/of de pijpleiding verschillend is.
* [Beproefde versieafhandeling](/help/implementing/cloud-manager/managing-code/project-version-handling.md) vervangt de projectversie alleen in productiepijpleidingen. Daarom als het zelfde begaat op zowel een ontwikkelt uitvoering en een uitvoering van de productiepijplijn en de ontwikkelings opstellen pijpleiding eerst wordt gebruikt, worden de versies opgesteld aan stadium en productie zonder wordt veranderd. In dit geval wordt echter nog steeds een tag gemaakt.
* Als de terugwinning van de opgeslagen artefacten niet succesvol is, wordt de bouwstijlstap in werking gesteld alsof geen artefacten waren opgeslagen.
* Andere pijpleidingvariabelen dan `CM_DISABLE_BUILD_REUSE` worden niet in overweging genomen wanneer Cloud Manager besluit eerder gemaakte constructieartefacten opnieuw te gebruiken.
