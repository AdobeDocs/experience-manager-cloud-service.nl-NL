---
title: Insteekmodule Adobe-inhoudspakket
description: Gebruik de Content Package Maven plug-in om AEM toepassingen te implementeren
exl-id: d631d6df-7507-4752-862b-9094af9759a0
source-git-commit: ac64ca485391d843c0ebefcf86e80b4015b72b2f
workflow-type: tm+mt
source-wordcount: '1847'
ht-degree: 4%

---

# Insteekmodule voor Adobe-inhoudspakket {#adobe-content-package-maven-plugin}

Met de plug-in Adobe Content Package Maven kunt u taken voor pakketimplementatie en -beheer integreren in uw Maven-projecten.

De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door het Pakket van de Inhoud van de Adobe Geproduceerde stop en laat de automatisering van taken toe normaal die gebruikend AEM Manager van het Pakket worden uitgevoerd:

* Nieuwe pakketten maken van bestanden in het bestandssysteem.
* Installeer en verwijder pakketten op AEM.
* Bouw pakketten die reeds op AEM worden bepaald.
* Verkrijg een lijst van pakketten die op AEM geïnstalleerd zijn.
* Een pakket uit AEM verwijderen.

In dit document wordt beschreven hoe u deze taken beheert met de Maven. Nochtans is het ook belangrijk om [te begrijpen hoe AEM projecten en hun pakketten gestructureerd zijn.](#aem-project-structure)

>[!NOTE]
>
>Het maken van pakketten is nu eigendom van de [Apache Jackrabbit FileVault-pakket Maven-plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/). De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door de Adobe Content Package Maven stop hier beschreven.

## Pakketten en de AEM projectstructuur {#aem-project-structure}

AEM als Cloud Service houdt zich aan de recentste beste praktijken voor pakketbeheer en projectstructuur zoals uitgevoerd door het recentste Project Archetype van AEM.

>[!TIP]
>
>Zie het artikel [AEM Projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in de AEM als documentatie voor Cloud Servicen en de documentatie [AEM Projectarchetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) voor meer informatie. Beide worden volledig ondersteund voor AEM 6.5.

## De insteekmodule {#obtaining-the-content-package-maven-plugin} voor het ophalen van het inhoudspakket

De insteekmodule is beschikbaar in de [Maven Central Repository.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

## Doelstellingen en parameters van insteekmodule voor inhoudspakket

Als u de insteekmodule Inhoudspakket met Maven wilt gebruiken, voegt u het volgende insteekmodule toe in het element build van het POM-bestand:

```xml
<plugin>
 <groupId>com.day.jcr.vault</groupId>
 <artifactId>content-package-maven-plugin</artifactId>
 <version>0.0.24</version>
 <configuration>
       <!-- parameters and values common to all goals, as required -->
 </configuration>
</plugin>
```

Als u wilt dat Maven de plug-in kan downloaden, gebruikt u het profiel in de sectie [Gemaakt inhoudspakket verkrijgen](#obtaining-the-content-package-maven-plugin) op deze pagina.

## Doelstellingen van de insteekmodule Inhoudspakket {#goals-of-the-content-package-maven-plugin}

De doelstellingen en doelparameters die de insteekmodule van het Pakket van de Inhoud verstrekt worden beschreven in de secties die volgen. De parameters die in de Gemeenschappelijke sectie van Parameters worden beschreven kunnen voor de meeste doelstellingen worden gebruikt. De parameters die op één doel van toepassing zijn worden beschreven in de sectie voor dat doel.

### Plug-voorvoegsel {#plugin-prefix}

Het voorvoegsel van de plug-in is `content-package`. Gebruik dit voorvoegsel om een doel uit te voeren vanaf de opdrachtregel, zoals in het volgende voorbeeld:

```shell
mvn content-package:build
```

### Parametervoorvoegsel {#parameter-prefix}

Tenzij anders aangegeven, gebruiken de doelstellingen en parameters van de plug-in het voorvoegsel `vault`, zoals in het volgende voorbeeld:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxy {#proxies}

De doelstellingen die volmachten voor AEM gebruiken de eerste geldige volmachtsconfiguratie die in de GeMaven montages wordt gevonden. Als geen volmachtsconfiguratie wordt gevonden, wordt geen volmacht gebruikt. Zie de parameter `useProxy` in de sectie [Algemene parameters](#common-parameters).

### Algemene parameters {#common-parameters}

De parameters in de volgende lijst zijn gemeenschappelijk voor alle doelstellingen behalve wanneer vermeld in **Doels** kolom.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving | Doelen |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nee | `false` | Een waarde van `true` veroorzaakt de bouwstijl om te ontbreken wanneer een fout voorkomt. Bij een waarde van `false` wordt de fout genegeerd. | Alle doelen behalve `package` |
| `name` | `String` | `build`: Ja,  `install`: Nee,  `rm`: Ja | `build`: Geen standaardwaarde,  `install`: De waarde van het  `artifactId` eigendom van het Maven-project | De naam van het pakket waarop moet worden gehandeld | Alle doelen behalve `ls` |
| `password` | `String` | Ja | `admin` | Het wachtwoord voor verificatie met AEM | Alle doelen behalve `package` |
| `serverId` | `String` | Nee | De server-id waarvan de gebruikersnaam en het wachtwoord voor verificatie moeten worden opgehaald | Alle doelen behalve `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | De URL van de HTTP-service-API van het AEM pakketbeheer | Alle doelen behalve `package` |
| `timeout` | `int` | Nee | `5` | De verbindingstijd voor communicatie met de pakketbeheerservice, in seconden | Alle doelen behalve `package` |
| `useProxy` | `boolean` | Nee | `true` | Een waarde van `true` veroorzaakt Maven om de eerste actieve volmachtsconfiguratie te gebruiken die in orde wordt gevonden volmachtsverzoeken aan de Manager van het Pakket. | Alle doelen behalve `package` |
| `userId` | `String` | Ja | `admin` | De gebruikersnaam die moet worden geverifieerd met AEM | Alle doelen behalve `package` |
| `verbose` | `boolean` | Nee | `false` | Schakelt uitgebreide logboekregistratie in of uit | Alle doelen behalve `package` |

### build {#build}

Bouwt een inhoudspakket dat reeds op een AEM instantie wordt bepaald.

>[!NOTE]
>
>Dit doel hoeft niet binnen een Maven-project te worden uitgevoerd.

#### Parameters {#parameters}

Alle parameters voor het bouwstijldoel worden beschreven in [Gemeenschappelijke Parameters](#common-parameters) sectie.

### installeren {#install}

Hiermee installeert u een pakket in de opslagplaats. Voor de verwezenlijking van dit doel is geen Maven-project vereist. Het doel is gebonden aan de `install` fase van de Maven-build levenscyclus.

#### Parameters {#parameters-1}

Naast de volgende parameters, zie de beschrijvingen in [Gemeenschappelijke Parameters](#common-parameters) sectie.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|---|
| `artifact` | `String` | Nee | De waarde van de `artifactId`-eigenschap van het Maven-project | Een tekenreeks van het formulier `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nee | Geen | De id van het artefact dat moet worden geïnstalleerd |
| `groupId` | `String` | Nee | Geen | De `groupId` van het te installeren artefact |
| `install` | `boolean` | Nee | `true` | Hiermee wordt bepaald of het pakket automatisch moet worden uitgepakt wanneer het wordt geüpload |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nee | De waarde van de systeemvariabele `localRepository` | De lokale Maven opslagplaats die niet kan worden gevormd gebruikend de plugin configuratie aangezien het systeembezit altijd wordt gebruikt |
| `packageFile` | `java.io.File` | Nee | Het primaire artefact dat voor het Maven project wordt bepaald | De naam van het te installeren pakketbestand |
| `packaging` | `String` | Nee | `zip` | Het type verpakking van het te installeren artefact |
| `pomRemoteRepositories` | `java.util.List` | Ja | De waarde van het `remoteArtifactRepositories` bezit dat voor het Gemaakt project wordt bepaald | Deze waarde kan niet worden gevormd gebruikend de pluginconfiguratie en moet in het project worden gespecificeerd. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Het project waarvoor de insteekmodule is geconfigureerd | Het Maven-project dat impliciet is omdat het project de plug-inconfiguratie bevat |
| `repositoryId` (POM),  `repoID` (opdrachtregel) | `String` | Nee | `temp` | De id van de opslagplaats waarvan het artefact wordt opgehaald |
| `repositoryUrl` (POM),  `repoURL` (opdrachtregel) | `String` | Nee | Geen | De URL van de opslagplaats waarvan het artefact wordt opgehaald |
| version | Tekenreeks | Nee | Geen | De versie van het artefact dat moet worden geïnstalleerd |

### ls {#ls}

Maakt een lijst van de pakketten die aan de Manager van het Pakket worden opgesteld.

#### Parameters {#parameters-2}

Alle parameters van het doel ls worden beschreven in [Gemeenschappelijke Parameters](#common-parameters) sectie.

### rm {#rm}

Hiermee wordt een pakket verwijderd uit Pakketbeheer.

#### Parameters {#parameters-3}

Alle parameters van het rm-doel worden beschreven in de sectie [Algemene parameters](#common-parameters).

### verwijderen {#uninstall}

Hiermee wordt een pakket verwijderd. Het pakket blijft op de server staan in de toestand Niet-geïnstalleerd.

#### Parameters {#parameters-4}

Alle parameters van het doel voor verwijderen worden beschreven in de sectie [Algemene parameters](#common-parameters).

### package {#package}

Maakt een inhoudspakket. De standaardconfiguratie van het pakketdoel bevat de inhoud van de map waarin gecompileerde bestanden worden opgeslagen. De uitvoering van het pakketdoel vereist dat de compilatiefase is voltooid. Het pakketdoel is gebonden aan de pakketfase van de Maven-levenscyclus.

#### Parameters {#parameters-5}

Naast de volgende parameters, zie de beschrijving van de `name` parameter in [Gemeenschappelijke Parameters](#common-parameters) sectie.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Nee | Geen | De archiefconfiguratie die moet worden gebruikt |
| `builtContentDirectory` | `java.io.File` | Ja | De waarde van de uitvoerdirectory van de Maven-build | De map met de inhoud die in het pakket moet worden opgenomen |
| `dependencies` | `java.util.List` | Nee | Geen |  |
| `embeddedTarget` | `java.lang.String` | Nee | Geen |  |
| `embeddeds` | `java.util.List` | Nee | Geen |  |
| `failOnMissingEmbed` | `boolean` | Ja | `false` | Een waarde van `true` veroorzaakt de bouwstijl om te ontbreken wanneer een ingebed artefact niet in de projectgebiedsdelen wordt gevonden. Een waarde van `false` veroorzaakt de bouwstijl om dergelijke fouten te negeren. |
| `filterSource` | `java.io.File` | Nee | Geen | Deze parameter definieert een bestand dat de bron van het werkruimtefilter aangeeft. De filters die in de configuratie worden opgegeven en via inbedden of subpakketten worden geïnjecteerd, worden samengevoegd met de bestandsinhoud. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Nee | Geen | Deze parameter bevat filterelementen die de pakketinhoud definiëren. Wanneer deze worden uitgevoerd, worden de filters opgenomen in het `filter.xml`-bestand. Zie de onderstaande sectie [Filters gebruiken](#using-filters). |
| `finalName` | `java.lang.String` | Ja | `finalName` bepaald in het Maven project (bouwstijlfase) | De naam van het gegenereerde pakket-ZIP-bestand, zonder de bestandsextensie `.zip` |
| `group` | `java.lang.String` | Ja | `groupID` gedefinieerd in het Maven-project | De `groupId` van het gegenereerde inhoudspakket dat deel uitmaakt van het doelinstallatiepad voor het inhoudspakket |
| `outputDirectory` | `java.io.File` | Ja | De bouwstijlfolder die in het Gemaakt project wordt bepaald | De lokale map waar het inhoudspakket is opgeslagen |
| `prefix` | `java.lang.String` | Nee | Geen |  |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Geen | Het Maven-project |
| `properties` | `java.util.Map` | Nee | Geen | Deze parameters definiëren aanvullende eigenschappen die u kunt instellen in het `properties.xml`-bestand. Deze eigenschappen kunnen de volgende vooraf gedefinieerde eigenschappen niet overschrijven: `group` (gebruik `group` parameter om in te stellen), `name` (gebruik `name` parameter om in te stellen), `version` (gebruik `version` parameter om in te stellen), `description` (reeks uit de projectbeschrijving), `groupId` (`groupId` van de Maven projectdescriptor), `artifactId` (`artifactId` Maven project descriptor), `dependencies` (gebruik `dependencies` parameter om in te stellen), `createdBy` (de waarde van de `user.name` systeemeigenschap), `created` (de huidige systeemtijd), `requiresRoot` (gebruik `requiresRoot` parameter om in te stellen), `packagePath` (wordt automatisch gegenereerd op basis van de naam van de groep en het pakket) |
| `requiresRoot` | `boolean` | Ja | false | Definieert of het pakket root vereist. Dit wordt de eigenschap `requiresRoot` van het `properties.xml`-bestand. |
| `subPackages` | `java.util.List` | Nee | Geen |  |
| `version` | `java.lang.String` | Ja | De versie die is gedefinieerd in het Maven-project | De versie van het inhoudspakket |
| `workDirectory` | `java.io.File` | Ja | De folder die in het Maven project (bouwstijlfase wordt bepaald) | De map met de inhoud die in het pakket moet worden opgenomen |

#### Filters {#using-filters} gebruiken

Gebruik het element filters om de pakketinhoud te definiëren. De filters worden toegevoegd aan het `workspaceFilter` element in het `META-INF/vault/filter.xml` dossier van het pakket.

In het volgende filtervoorbeeld wordt de XML-structuur getoond die moet worden gebruikt:

```xml
<filter>
   <root>/apps/myapp</root>
   <mode>merge</mode>
       <includes>
              <include>/apps/myapp/install/</include>
              <include>/apps/myapp/components</include>
       </includes>
       <excludes>
              <exclude>/apps/myapp/config/*</exclude>
       </excludes>
</filter>
```

##### Importmodus {#import-mode}

Het `mode`-element definieert hoe inhoud wordt beïnvloed door de opslagplaats wanneer het pakket wordt geïmporteerd. De volgende waarden kunnen worden gebruikt:

* **Samenvoegen:** Inhoud in het pakket die zich nog niet in de opslagplaats bevindt, wordt toegevoegd. De inhoud in zowel het pakket als de opslagplaats blijft ongewijzigd. Er wordt geen inhoud uit de opslagplaats verwijderd.
* **Vervangen:** Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket. Inhoud wordt verwijderd uit de opslagplaats wanneer deze niet bestaat in het pakket.
* **Bijwerken:** Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket. Bestaande inhoud wordt verwijderd uit de opslagplaats.

Wanneer het filter geen `mode` element bevat, wordt de standaardwaarde van `replace` gebruikt.

### help {#help}

#### Parameters {#parameters-6}

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `detail` | `boolean` | Nee | `false` | Bepaalt of om alle settable eigenschappen voor elk doel te tonen |
| `goal` | `String` | Nee | Geen | Deze parameters bepalen de naam van het doel waarvoor om hulp te tonen. Als geen waarde wordt gespecificeerd, wordt de hulp voor alle doelstellingen getoond. |
| `indentSize` | `int` | Nee | `2` | Het aantal spaties dat moet worden gebruikt voor de inspringing van elk niveau (moet positief zijn als dit is gedefinieerd) |
| `lineLength` | `int` | Nee | `80` | De maximumlengte van een weergaveregel (moet positief zijn als deze is gedefinieerd) |

## Een miniatuurafbeelding of eigenschapsbestand opnemen in het pakket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Vervang de standaardpakketconfiguratiebestanden om de pakketeigenschappen aan te passen. Neem bijvoorbeeld een miniatuurafbeelding om het pakket te onderscheiden in Pakketbeheer en Delen van pakket.

U kunt de bronbestanden overal in uw bestandssysteem vinden. Definieer in het POM-bestand build-resources om de bronbestanden naar `target/vault-work/META-INF` te kopiëren voor opname in het pakket.

De volgende POM-code voegt de bestanden in de map `META-INF` van de projectbron toe aan het pakket:

```xml
<build>
    <resources>
        <!-- vault META-INF resources (thumbnail etc.) -->
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

## Het gebruiken van het AEM Archetype van het Project om AEM Projecten {#using-archetypes} te produceren

De nieuwste AEM Project Archetype implementeert de pakketstructuur met best practices voor zowel de implementatie op locatie als in AMS en wordt aanbevolen voor alle AEM projecten.

>[!TIP]
>
>Zie het artikel [AEM Projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) in de AEM als documentatie voor Cloud Servicen en de documentatie [AEM Projectarchetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) voor meer informatie. Beide worden volledig ondersteund voor AEM 6.5.
