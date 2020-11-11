---
title: Insteekmodule Adobe-inhoudspakket
description: Gebruik de Content Package Maven plug-in om AEM toepassingen te implementeren
translation-type: tm+mt
source-git-commit: 2cdbbe9b8f6608cbdd299889be515d421e3d9ad3
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 5%

---


# Insteekmodule Adobe-inhoudspakket {#adobe-content-package-maven-plugin}

Met de plug-in Adobe Content Package Maven kunt u taken voor pakketimplementatie en -beheer integreren in uw Maven-projecten.

De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door het Pakket van de Inhoud van de Adobe Geproduceerde stop en laat de automatisering van taken toe normaal die gebruikend AEM Manager van het Pakket worden uitgevoerd:

* Nieuwe pakketten maken van bestanden in het bestandssysteem.
* Installeer en verwijder pakketten op AEM.
* Bouw pakketten die reeds op AEM worden bepaald.
* Verkrijg een lijst van pakketten die op AEM geïnstalleerd zijn.
* Een pakket uit AEM verwijderen.

In dit document wordt beschreven hoe u deze taken beheert met de Maven. Het is echter ook belangrijk te begrijpen [hoe AEM projecten en hun pakketten gestructureerd zijn.](#aem-project-structure)

>[!NOTE]
>
>Het maken van pakketten is nu eigendom van de [Apache Jackrabbit FileVault Package Maven-plug-in](https://jackrabbit.apache.org/filevault-package-maven-plugin/). De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door de Adobe Content Package Maven stop hier beschreven.

## Pakketten en de AEM projectstructuur {#aem-project-structure}

AEM 6.5 houdt zich aan de meest recente beste praktijken voor pakketbeheer en projectstructuur, zoals geïmplementeerd door het meest recente AEM Project Archetype voor zowel de implementaties op locatie als in AMS.

>[!TIP]
>
>Voor meer details, zie het [AEM artikel van de Structuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) van het Project in de AEM als documentatie van de Cloud Service evenals de documentatie van de Archetype [van het](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) AEM Project. Beide worden volledig ondersteund voor AEM 6.5.

## De insteekmodule voor het inhoudspakket verkrijgen {#obtaining-the-content-package-maven-plugin}

De plug-in is beschikbaar in de [hoofdopslagruimte van Maven Central.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

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

Als u Maven wilt inschakelen om de insteekmodule te downloaden, gebruikt u het profiel dat is opgegeven in de sectie [Insteekmodule](#obtaining-the-content-package-maven-plugin) voor inhoudspakket verkrijgen op deze pagina.

## Doelstellingen van de plug-in Inhoudspakket {#goals-of-the-content-package-maven-plugin}

De doelstellingen en doelparameters die de insteekmodule van het Pakket van de Inhoud verstrekt worden beschreven in de secties die volgen. De parameters die in de Gemeenschappelijke sectie van Parameters worden beschreven kunnen voor de meeste doelstellingen worden gebruikt. De parameters die op één doel van toepassing zijn worden beschreven in de sectie voor dat doel.

### Plug-voorvoegsel {#plugin-prefix}

Het voorvoegsel van de plug-in is `content-package`. Gebruik dit voorvoegsel om een doel uit te voeren vanaf de opdrachtregel, zoals in het volgende voorbeeld:

```shell
mvn content-package:build
```

### Parametervoorvoegsel {#parameter-prefix}

Tenzij anders aangegeven, gebruiken de doelstellingen en parameters van de plug-in het `vault` voorvoegsel, zoals in het volgende voorbeeld:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxy {#proxies}

De doelstellingen die volmachten voor AEM gebruiken de eerste geldige volmachtsconfiguratie die in de GeMaven montages wordt gevonden. Als geen volmachtsconfiguratie wordt gevonden, wordt geen volmacht gebruikt. Zie de `useProxy` parameter in de sectie [Algemene parameters](#common-parameters) .

### Algemene parameters {#common-parameters}

De parameters in de volgende lijst zijn gemeenschappelijk voor alle doelstellingen behalve wanneer vermeld in de kolom van **Doelen** .

| Naam | Type | Vereist | Standaardwaarde | Beschrijving | Doelen |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nee | `false` | Een waarde van `true` oorzaken de bouwstijl om te ontbreken wanneer een fout voorkomt. Bij een waarde van `false` wordt de fout genegeerd. | Alle doelstellingen behalve `package` |
| `name` | `String` | `build`: Ja, `install`: Nee, `rm`: Ja | `build`: Geen standaardwaarde, `install`: De waarde van het `artifactId` eigendom van het Maven-project | De naam van het pakket waarop moet worden gehandeld | Alle doelstellingen behalve `ls` |
| `password` | `String` | Ja | `admin` | Het wachtwoord voor verificatie met AEM | Alle doelstellingen behalve `package` |
| `serverId` | `String` | Nee | De server-id waarvan de gebruikersnaam en het wachtwoord voor verificatie moeten worden opgehaald | Alle doelstellingen behalve `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | De URL van de HTTP-service-API van het AEM pakketbeheer | Alle doelstellingen behalve `package` |
| `timeout` | `int` | Nee | `5` | De verbindingstijd voor communicatie met de pakketbeheerservice, in seconden | Alle doelstellingen behalve `package` |
| `useProxy` | `boolean` | Nee | `true` | Een waarde van `true` oorzaken Maven om de eerste actieve volmachtsconfiguratie te gebruiken die in orde wordt gevonden volmachtsverzoeken aan de Manager van het Pakket. | Alle doelstellingen behalve `package` |
| `userId` | `String` | Ja | `admin` | De gebruikersnaam die moet worden geverifieerd met AEM | Alle doelstellingen behalve `package` |
| `verbose` | `boolean` | Nee | `false` | Schakelt uitgebreide logboekregistratie in of uit | Alle doelstellingen behalve `package` |

### build {#build}

Bouwt een inhoudspakket dat reeds op een AEM instantie wordt bepaald.

>[!NOTE]
>
>Dit doel hoeft niet binnen een Maven-project te worden uitgevoerd.

#### Parameters {#parameters}

Alle parameters voor het bouwstijldoel worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

### installeren {#install}

Hiermee installeert u een pakket in de opslagplaats. Voor de verwezenlijking van dit doel is geen Maven-project vereist. Het doel is gebonden aan de `install` fase van de Maven-levenscyclus.

#### Parameters {#parameters-1}

Naast de volgende parameters, zie de beschrijvingen in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|---|
| `artifact` | `String` | Nee | De waarde van het `artifactId` eigendom van het Maven-project | Een tekenreeks van het formulier `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nee | Geen | De id van het artefact dat moet worden geïnstalleerd |
| `groupId` | `String` | Nee | Geen | De `groupId` te installeren artefact |
| `install` | `boolean` | Nee | `true` | Hiermee wordt bepaald of het pakket automatisch moet worden uitgepakt wanneer het wordt geüpload |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nee | De waarde van de `localRepository` systeemvariabele | De lokale Maven opslagplaats die niet kan worden gevormd gebruikend de plugin configuratie aangezien het systeembezit altijd wordt gebruikt |
| `packageFile` | `java.io.File` | Nee | Het primaire artefact dat voor het Maven project wordt bepaald | De naam van het te installeren pakketbestand |
| `packaging` | `String` | Nee | `zip` | Het type verpakking van het te installeren artefact |
| `pomRemoteRepositories` | `java.util.List` | Ja | De waarde van het `remoteArtifactRepositories` bezit dat voor het Maven project wordt bepaald | Deze waarde kan niet worden gevormd gebruikend de pluginconfiguratie en moet in het project worden gespecificeerd. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Het project waarvoor de insteekmodule is geconfigureerd | Het Maven-project dat impliciet is omdat het project de plug-inconfiguratie bevat |
| `repositoryId` (POM), `repoID` (opdrachtregel) | `String` | Nee | `temp` | De id van de opslagplaats waarvan het artefact wordt opgehaald |
| `repositoryUrl` (POM), `repoURL` (opdrachtregel) | `String` | Nee | Geen | De URL van de opslagplaats waarvan het artefact wordt opgehaald |
| version | Tekenreeks | Nee | Geen | De versie van het artefact dat moet worden geïnstalleerd |

### ls {#ls}

Maakt een lijst van de pakketten die aan de Manager van het Pakket worden opgesteld.

#### Parameters {#parameters-2}

Alle parameters van het doel ls worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

### rm {#rm}

Hiermee wordt een pakket verwijderd uit Pakketbeheer.

#### Parameters {#parameters-3}

Alle parameters van het rm doel worden beschreven in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

### verwijderen {#uninstall}

Hiermee wordt een pakket verwijderd. Het pakket blijft op de server staan in de toestand Niet-geïnstalleerd.

#### Parameters {#parameters-4}

Alle parameters van het verwijderingsdoel worden beschreven in de sectie [Algemene parameters](#common-parameters) .

### package {#package}

Maakt een inhoudspakket. De standaardconfiguratie van het pakketdoel bevat de inhoud van de map waarin gecompileerde bestanden worden opgeslagen. De uitvoering van het pakketdoel vereist dat de compilatiefase is voltooid. Het pakketdoel is gebonden aan de pakketfase van de Maven-levenscyclus.

#### Parameters {#parameters-5}

Naast de volgende parameters, zie de beschrijving van de `name` parameter in de [Gemeenschappelijke sectie van Parameters](#common-parameters) .

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Nee | Geen | De archiefconfiguratie die moet worden gebruikt |
| `builtContentDirectory` | `java.io.File` | Ja | De waarde van de uitvoerdirectory van de Maven-build | De map met de inhoud die in het pakket moet worden opgenomen |
| `dependencies` | `java.util.List` | Nee | Geen |  |
| `embeddedTarget` | `java.lang.String` | Nee | Geen |  |
| `embeddeds` | `java.util.List` | Nee | Geen |  |
| `failOnMissingEmbed` | `boolean` | Ja | `false` | Een waarde van `true` veroorzaakt de bouwstijl om te ontbreken wanneer een ingebed artefact niet in de projectgebiedsdelen wordt gevonden. Een waarde van `false` zorgt ervoor dat de build dergelijke fouten negeert. |
| `filterSource` | `java.io.File` | Nee | Geen | Deze parameter definieert een bestand dat de bron van het werkruimtefilter aangeeft. De filters die in de configuratie worden opgegeven en via inbedden of subpakketten worden geïnjecteerd, worden samengevoegd met de bestandsinhoud. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Nee | Geen | Deze parameter bevat filterelementen die de pakketinhoud definiëren. Wanneer deze worden uitgevoerd, worden de filters in het `filter.xml` bestand opgenomen. Zie de onderstaande sectie [Filters](#using-filters) gebruiken. |
| `finalName` | `java.lang.String` | Ja | De `finalName` definitie in het Maven-project (bouwfase) | De naam van het gegenereerde pakket-ZIP-bestand, zonder de `.zip` bestandsextensie |
| `group` | `java.lang.String` | Ja | De `groupID` definitie in het Maven-project | Het `groupId` gegenereerde inhoudspakket dat deel uitmaakt van het doelinstallatiepad voor het inhoudspakket |
| `outputDirectory` | `java.io.File` | Ja | De bouwstijlfolder die in het Gemaakt project wordt bepaald | De lokale map waar het inhoudspakket is opgeslagen |
| `prefix` | `java.lang.String` | Nee | Geen |  |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Geen | Het Maven-project |
| `properties` | `java.util.Map` | Nee | Geen | Deze parameters definiëren aanvullende eigenschappen die u in het `properties.xml` bestand kunt instellen. Deze eigenschappen kunnen de volgende vooraf gedefinieerde eigenschappen niet overschrijven: `group` (gebruiksparameter `group` in te stellen), `name` (gebruiksparameter `name` in te stellen), `version` (gebruiksparameter `version` in te stellen), `description` (vanuit de projectbeschrijving ingesteld), `groupId` (`groupId` van de Maven-projectdescriptor), `artifactId` (`artifactId` `dependencies` `dependencies` `createdBy` `user.name` `created` `requiresRoot` `requiresRoot` `packagePath` van de Maven-projectparameter), (gebruik de parameter om in te stellen), (de waarde van de systeemdescriptor), (de huidige systeemtijd, het gebruik van de parameter), automatisch); van de groep en de pakketnaam) |
| `requiresRoot` | `boolean` | Ja | false | Definieert of het pakket root vereist. Dit wordt de `requiresRoot` eigenschap van het `properties.xml` bestand. |
| `subPackages` | `java.util.List` | Nee | Geen |  |
| `version` | `java.lang.String` | Ja | De versie die is gedefinieerd in het Maven-project | De versie van het inhoudspakket |
| `workDirectory` | `java.io.File` | Ja | De folder die in het Maven project (bouwstijlfase wordt bepaald) | De map met de inhoud die in het pakket moet worden opgenomen |

#### Filters gebruiken {#using-filters}

Gebruik het element filters om de pakketinhoud te definiëren. De filters worden toegevoegd aan het `workspaceFilter` element in het `META-INF/vault/filter.xml` bestand van het pakket.

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

Het `mode` element bepaalt hoe de inhoud de bewaarplaats wordt beïnvloed wanneer het pakket wordt ingevoerd. De volgende waarden kunnen worden gebruikt:

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

## Een miniatuurafbeelding of eigenschappenbestand opnemen in het pakket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Vervang de standaardpakketconfiguratiebestanden om de pakketeigenschappen aan te passen. Neem bijvoorbeeld een miniatuurafbeelding om het pakket te onderscheiden in Pakketbeheer en Delen van pakket.

U kunt de bronbestanden overal in uw bestandssysteem vinden. Definieer in het POM-bestand build-bronnen om de bronbestanden naar de map te kopiëren `target/vault-work/META-INF` voor opname in het pakket.

Met de volgende POM-code voegt u de bestanden in de `META-INF` map van de projectbron toe aan het pakket:

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

Met de volgende POM-code wordt alleen een miniatuurafbeelding aan het pakket toegevoegd. De miniatuurafbeelding moet een naam hebben `thumbnail.png`en zich in de `META-INF/vault/definition` map van het pakket bevinden. In dit voorbeeld bevindt het bronbestand zich in de `/src/main/content/META-INF/vault/definition` map van het project:

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

## Het gebruiken van het AEM Archetype van het Project om AEM Projecten te produceren {#using-archetypes}

De nieuwste AEM Project Archetype implementeert de pakketstructuur met best practices voor zowel de implementatie op locatie als in AMS en wordt aanbevolen voor alle AEM projecten.

>[!TIP]
>
>Voor meer details, zie het [AEM artikel van de Structuur](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) van het Project in de AEM als documentatie van de Cloud Service evenals de documentatie van de Archetype [van het](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) AEM Project. Beide worden volledig ondersteund voor AEM 6.5.
