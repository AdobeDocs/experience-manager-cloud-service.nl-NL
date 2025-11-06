---
title: Insteekmodule Adobe Content Package Maven
description: Gebruik de insteekmodule Content Package Maven om AEM-toepassingen te implementeren
exl-id: d631d6df-7507-4752-862b-9094af9759a0
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1235'
ht-degree: 0%

---

# Insteekmodule Adobe Content Package Maven {#adobe-content-package-maven-plugin}

Met de insteekmodule Adobe Content Package Maven kunt u taken voor pakketimplementatie en -beheer integreren in uw Maven-projecten.

De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door het Pakket Maven van de Inhoud van Adobe stop en laat de automatisering van taken toe normaal uitgevoerd gebruikend de Manager van het Pakket van AEM [ ](/help/implementing/developing/tools/package-manager.md)

* Nieuwe pakketten maken van bestanden in het bestandssysteem.
* Installeer en verwijder pakketten op AEM.
* Pakketten maken die al op AEM zijn gedefinieerd.
* Vraag een lijst met pakketten aan die op AEM zijn geïnstalleerd.
* Verwijder een pakket uit AEM.

In dit document wordt beschreven hoe u deze taken beheert met de Maven. Nochtans is het ook belangrijk om [ te begrijpen hoe de projecten van AEM en hun pakketten gestructureerd ](#aem-project-structure) zijn.

>[!NOTE]
>
>Gebruik altijd de nieuwste versies van deze plug-ins.

>[!NOTE]
>
>De verwezenlijking van het pakket **** wordt nu bezeten door het [ Pakket Maven van het Pakket Apache Jackrabbit FileVault Pakket ](https://jackrabbit.apache.org/filevault-package-maven-plugin/).
>
>Dit artikel beschrijft de **plaatsing** van de geconstrueerde pakketten aan AEM zoals die door het Pakket Maven van de Inhoud van Adobe wordt uitgevoerd.

## Pakketten en de AEM-projectstructuur {#aem-project-structure}

AEM as a Cloud Service houdt zich aan de nieuwste best practices voor pakketbeheer en projectstructuur, zoals geïmplementeerd door de nieuwste AEM Project Archetype.

>[!TIP]
>
>Zie het [ artikel van de Structuur van het Project van 0} AEM in de documentatie van AEM as a Cloud Service en de ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) documentatie van de Archetype van het Project van AEM [. ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) Beide zijn volledig ondersteund voor AEM 6.5.

## De insteekmodule voor het inhoudspakket verkrijgen {#obtaining-the-content-package-maven-plugin}

De stop is beschikbaar bij [ Gemaakt Centrale Bewaarplaats ](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public).

## Doelstellingen en parameters van insteekmodule voor inhoudspakket

Als u de insteekmodule Inhoudspakket met Maven wilt gebruiken, voegt u het volgende insteekmodule toe in het element build van het POM-bestand:

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>1.0.4</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Om Maven toe te laten om de stop te downloaden, gebruik het profiel dat in [ wordt verstrekt het Verkrijgen van de sectie van de Insteekmodule van het Pakket van de Inhoud ](#obtaining-the-content-package-maven-plugin) op deze pagina wordt verstrekt.

## Doelstellingen van de plug-in Inhoudspakket {#goals-of-the-content-package-maven-plugin}

De doelstellingen en doelparameters die de insteekmodule van het Pakket van de Inhoud verstrekt worden beschreven in de secties die volgen. De parameters die in de Gemeenschappelijke sectie van Parameters worden beschreven kunnen voor de meeste doelstellingen worden gebruikt. De parameters die op één doel van toepassing zijn worden beschreven in de sectie voor dat doel.

### Plug-voorvoegsel {#plugin-prefix}

Het voorvoegsel van de plug-in is `content-package` . Gebruik dit voorvoegsel om een doel uit te voeren vanaf de opdrachtregel, zoals in het volgende voorbeeld:

```shell
mvn content-package:build
```

### Parametervoorvoegsel {#parameter-prefix}

Tenzij anders vermeld, gebruiken de doelstellingen en parameters van de plug-in het voorvoegsel `vault` , zoals in het volgende voorbeeld:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxy {#proxies}

De doelstellingen die volmachten voor AEM gebruiken gebruiken gebruiken de eerste geldige volmachtsconfiguratie die in de GeMaven montages wordt gevonden. Als geen volmachtsconfiguratie wordt gevonden, wordt geen volmacht gebruikt. Zie de `useProxy` parameter in de [ Gemeenschappelijke Parameters ](#common-parameters) sectie.

### Algemene parameters {#common-parameters}

De parameters in de volgende lijst zijn gemeenschappelijk aan alle doelstellingen behalve wanneer genoteerd in de **1} kolom van Doelen {.**

| Naam | Type | Vereist | Standaardwaarde | Beschrijving | Doelen |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nee | `false` | De waarde `true` zorgt ervoor dat de build mislukt wanneer een fout optreedt. Bij de waarde `false` wordt de fout genegeerd. | Alle doelen behalve `package` |
| `name` | `String` | `build`: Ja, `install`: Nee, `rm`: Ja | `build`: Geen standaardwaarde, `install`: de waarde van de eigenschap `artifactId` van het Maven-project | De naam van het pakket waarop moet worden gehandeld | Alle doelen behalve `ls` |
| `password` | `String` | Ja | `admin` | Het wachtwoord voor verificatie met AEM | Alle doelen behalve `package` |
| `serverId` | `String` | Nee | De server-id waarvan de gebruikersnaam en het wachtwoord voor verificatie moeten worden opgehaald | Alle doelen behalve `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | De URL van de HTTP-service-API van het AEM-pakketbeheer | Alle doelen behalve `package` |
| `timeout` | `int` | Nee | `5` | De verbindingstijd voor communicatie met de pakketbeheerservice, in seconden | Alle doelen behalve `package` |
| `useProxy` | `boolean` | Nee | `true` | Een waarde van `true` veroorzaakt Maven om de eerste actieve volmachtsconfiguratie te gebruiken die aan volmachtsverzoeken aan de Manager van het Pakket wordt gevonden. | Alle doelen behalve `package` |
| `userId` | `String` | Ja | `admin` | De gebruikersnaam die moet worden geverifieerd met AEM | Alle doelen behalve `package` |
| `verbose` | `boolean` | Nee | `false` | Schakelt uitgebreide logboekregistratie in of uit | Alle doelen behalve `package` |

### build {#build}

Bouwt een inhoudspakket dat reeds op een instantie van AEM wordt bepaald.

>[!NOTE]
>
>Dit doel hoeft niet binnen een Maven-project te worden uitgevoerd.

#### Parameters {#parameters}

Alle parameters voor het bouwstijldoel worden beschreven in de [ Gemeenschappelijke sectie van Parameters ](#common-parameters).

### installeren {#install}

Hiermee installeert u een pakket in de opslagplaats. Voor de verwezenlijking van dit doel is geen Maven-project vereist. Het doel is gebonden aan de `install` -fase van de Maven-levenscyclus.

#### Parameters {#parameters-1}

Naast de volgende parameters, zie de beschrijvingen in de [ Gemeenschappelijke sectie van Parameters ](#common-parameters).

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `artifact` | `String` | Nee | De waarde van de eigenschap `artifactId` van het Maven-project | Een tekenreeks van het formulier `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nee | Geen | De id van het te installeren artefact |
| `groupId` | `String` | Nee | Geen | De `groupId` van het te installeren artefact |
| `install` | `boolean` | Nee | `true` | Hiermee wordt bepaald of het pakket automatisch moet worden uitgepakt wanneer het wordt geüpload |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nee | De waarde van de systeemvariabele `localRepository` | De lokale Maven opslagplaats die niet kan worden gevormd gebruikend de plugin configuratie aangezien het systeembezit altijd wordt gebruikt |
| `packageFile` | `java.io.File` | Nee | Het primaire artefact dat voor het Maven project wordt bepaald | De naam van het te installeren pakketbestand |
| `packaging` | `String` | Nee | `zip` | Het type verpakking van het te installeren artefact |
| `pomRemoteRepositories` | `java.util.List` | Ja | De waarde van de eigenschap `remoteArtifactRepositories` die is gedefinieerd voor het Maven-project | Deze waarde kan niet worden gevormd gebruikend de pluginconfiguratie en moet in het project worden gespecificeerd. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Het project waarvoor de insteekmodule is geconfigureerd | Het Maven-project dat impliciet is omdat het project de plug-inconfiguratie bevat |
| `repositoryId` (POM), `repoID` (opdrachtregel) | `String` | Nee | `temp` | De id van de opslagplaats waarvan het artefact wordt opgehaald |
| `repositoryUrl` (POM), `repoURL` (opdrachtregel) | `String` | Nee | Geen | De URL van de opslagplaats waarvan het artefact wordt opgehaald |
| versie | String | Nee | Geen | De versie van het artefact dat moet worden geïnstalleerd |

### ls {#ls}

Maakt een lijst van de pakketten die aan [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md) worden opgesteld.

#### Parameters {#parameters-2}

Alle parameters van het doel ls worden beschreven in de [ Gemeenschappelijke sectie van Parameters ](#common-parameters).

### rm {#rm}

Verwijdert een pakket uit [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md).

#### Parameters {#parameters-3}

Alle parameters van het rm doel worden beschreven in de [ Gemeenschappelijke sectie van Parameters ](#common-parameters).

### verwijderen {#uninstall}

Hiermee wordt een pakket verwijderd. Het pakket blijft op de server staan in de toestand Niet-geïnstalleerd.

#### Parameters {#parameters-4}

Alle parameters van uninstall doel worden beschreven in de [ Gemeenschappelijke sectie van Parameters ](#common-parameters).


### help {#help}

#### Parameters {#parameters-6}

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `detail` | `boolean` | Nee | `false` | Bepaalt of om alle settable eigenschappen voor elk doel te tonen |
| `goal` | `String` | Nee | Geen | Deze parameters bepalen de naam van het doel waarvoor om hulp te tonen. Als geen waarde wordt gespecificeerd, wordt de hulp voor alle doelstellingen getoond. |
| `indentSize` | `int` | Nee | `2` | Het aantal spaties dat moet worden gebruikt voor de inspringing van elk niveau (moet positief zijn als dit is gedefinieerd) |
| `lineLength` | `int` | Nee | `80` | De maximumlengte van een weergaveregel (moet positief zijn als deze is gedefinieerd) |

## Een miniatuurafbeelding of eigenschappenbestand opnemen in het pakket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Vervang de standaardpakketconfiguratiebestanden om de pakketeigenschappen aan te passen. Bijvoorbeeld, omvat een duimnagelbeeld om het pakket in [ Manager van het Pakket ](/help/implementing/developing/tools/package-manager.md) te onderscheiden.

U kunt de bronbestanden overal in uw bestandssysteem vinden. Definieer in het POM-bestand build-bronnen om de bronbestanden naar de `target/vault-work/META-INF` te kopiëren voor opname in het pakket.

Met de volgende POM-code voegt u de bestanden in de map `META-INF` van de projectbron toe aan het pakket:

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail and so on) -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF</directory>
            <targetPath>../vault-work/META-INF</targetPath>
        </resource>
    </resources>
</build>
```

Met de volgende POM-code wordt alleen een miniatuurafbeelding aan het pakket toegevoegd. De miniatuurafbeelding moet de naam `thumbnail.png` hebben en zich in de map `META-INF/vault/definition` van het pakket bevinden. In dit voorbeeld bevindt het bronbestand zich in de map `/src/main/content/META-INF/vault/definition` van het project:

```xml
<build>
    <resources>
        <!-- thumbnail only -->
        <resource>
            <directory>${basedir}/src/main/content/META-INF/vault/definition</directory>
            <targetPath>../vault-work/META-INF/vault/definition</targetPath>
        </resource>
    </resources>
</build>
```

## AEM Project Archetype gebruiken om AEM-projecten te genereren {#using-archetypes}

De nieuwste AEM Project Archetype implementeert de best-practice-pakketstructuur voor zowel de implementatie op locatie als de implementatie van AMS en wordt aanbevolen voor alle AEM-projecten.

>[!TIP]
>
>Zie het [ artikel van de Structuur van het Project van 0} AEM in de documentatie van AEM as a Cloud Service en de ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) documentatie van de Archetype van het Project van AEM [. ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) Beide zijn volledig ondersteund voor AEM 6.5.
