---
title: Insteekmodule Adobe-inhoudspakket
description: Gebruik de Content Package Maven-plug-in om AEM toepassingen te implementeren
exl-id: d631d6df-7507-4752-862b-9094af9759a0
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 0%

---

# Insteekmodule Adobe-inhoudspakket {#adobe-content-package-maven-plugin}

Met de plug-in Adobe Content Package Maven kunt u taken voor pakketimplementatie en -beheer integreren in uw Maven-projecten.

De plaatsing van de geconstrueerde pakketten aan AEM wordt uitgevoerd door de Insteekmodule van het Pakket van de Inhoud van de Adobe Maven en laat de automatisering van taken toe normaal die gebruikend AEM worden uitgevoerd [Pakketbeheer:](/help/implementing/developing/tools/package-manager.md)

* Nieuwe pakketten maken van bestanden in het bestandssysteem.
* Installeer en verwijder pakketten op AEM.
* Bouw pakketten die reeds op AEM worden bepaald.
* Verkrijg een lijst van pakketten die op AEM geïnstalleerd zijn.
* Een pakket uit AEM verwijderen.

In dit document wordt beschreven hoe u deze taken beheert met de Maven. Het is echter ook van belang om te begrijpen [hoe AEM projecten en hun pakketten gestructureerd zijn .](#aem-project-structure)

>[!NOTE]
>
>Pakket **creatie** is nu eigendom van de [Apache Jackrabbit FileVault Package Maven plugin.](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
>
>* De `content-package-maven-plugin` ondersteunt geen pakket meer uit versie 1.0.2.
>* In dit artikel worden de **implementatie** van de geconstrueerde pakketten die moeten worden AEM, wordt uitgevoerd door de Adobe Content Package Maven plugin.

## Pakketten en de AEM projectstructuur {#aem-project-structure}

AEM as a Cloud Service houdt zich aan de recentste beste praktijken voor pakketbeheer en projectstructuur zoals uitgevoerd door het recentste Archetype van AEM Project.

>[!TIP]
>
>Zie de [AEM projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) artikel in de AEM as a Cloud Service documentatie en de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) documentatie. Beide worden volledig ondersteund voor AEM 6.5.

## De insteekmodule voor het inhoudspakket verkrijgen {#obtaining-the-content-package-maven-plugin}

De insteekmodule is beschikbaar via de [Centrale gegevensopslagruimte.](https://mvnrepository.com/artifact/com.day.jcr.vault/content-package-maven-plugin?repo=adobe-public)

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

Gebruik het profiel in het dialoogvenster [De insteekmodule voor het inhoudspakket verkrijgen](#obtaining-the-content-package-maven-plugin) op deze pagina.

## Doelstellingen van de plug-in Inhoudspakket {#goals-of-the-content-package-maven-plugin}

De doelstellingen en doelparameters die de insteekmodule van het Pakket van de Inhoud verstrekt worden beschreven in de secties die volgen. De parameters die in de Gemeenschappelijke sectie van Parameters worden beschreven kunnen voor de meeste doelstellingen worden gebruikt. De parameters die op één doel van toepassing zijn worden beschreven in de sectie voor dat doel.

### Plug-voorvoegsel {#plugin-prefix}

Het voorvoegsel van de plug-in is `content-package`. Gebruik dit voorvoegsel om een doel uit te voeren vanaf de opdrachtregel, zoals in het volgende voorbeeld:

```shell
mvn content-package:build
```

### Parametervoorvoegsel {#parameter-prefix}

Tenzij anders vermeld, gebruiken de doelstellingen en de parameters van de plug-in `vault` voorvoegsel, zoals in het volgende voorbeeld:

```shell
mvn content-package:install -Dvault.targetURL="https://192.168.1.100:4502/crx/packmgr/service.jsp"
```

### Proxy {#proxies}

De doelstellingen die volmachten voor AEM gebruiken de eerste geldige volmachtsconfiguratie die in de GeMaven montages wordt gevonden. Als geen volmachtsconfiguratie wordt gevonden, wordt geen volmacht gebruikt. Zie de `useProxy` in de [Algemene parameters](#common-parameters) sectie.

### Algemene parameters {#common-parameters}

De parameters in de volgende tabel zijn gemeenschappelijk voor alle doelstellingen, behalve wanneer ze in de **Doelen** kolom.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving | Doelen |
|---|---|---|---|---|---|
| `failOnError` | `boolean` | Nee | `false` | Een waarde van `true` veroorzaakt de bouwstijl om te ontbreken wanneer een fout voorkomt. Een waarde van `false` zorgt ervoor dat de build de fout negeert. | Alle doelstellingen behalve `package` |
| `name` | `String` | `build`: Ja, `install`: Nee, `rm`: Ja | `build`: Geen standaard, `install`: De waarde van de `artifactId` eigendom van het Maven-project | De naam van het pakket waarop moet worden gehandeld | Alle doelstellingen behalve `ls` |
| `password` | `String` | Ja | `admin` | Het wachtwoord voor verificatie met AEM | Alle doelstellingen behalve `package` |
| `serverId` | `String` | Nee | De server-id waarvan de gebruikersnaam en het wachtwoord voor verificatie moeten worden opgehaald | Alle doelstellingen behalve `package` |
| `targetURL` | `String` | Ja | `http://localhost:4502/crx/packmgr/service.jsp` | De URL van de HTTP-service-API van het AEM pakketbeheer | Alle doelstellingen behalve `package` |
| `timeout` | `int` | Nee | `5` | De verbindingstijd voor communicatie met de pakketbeheerservice, in seconden | Alle doelstellingen behalve `package` |
| `useProxy` | `boolean` | Nee | `true` | Een waarde van `true` oorzaken Maven om de eerste actieve volmachtsconfiguratie te gebruiken die aan volmachtsverzoeken aan de Manager van het Pakket wordt gevonden. | Alle doelstellingen behalve `package` |
| `userId` | `String` | Ja | `admin` | De gebruikersnaam die moet worden geverifieerd met AEM | Alle doelstellingen behalve `package` |
| `verbose` | `boolean` | Nee | `false` | Schakelt uitgebreide logboekregistratie in of uit | Alle doelstellingen behalve `package` |

### build {#build}

Bouwt een inhoudspakket dat reeds op een AEM instantie wordt bepaald.

>[!NOTE]
>
>Dit doel hoeft niet binnen een Maven-project te worden uitgevoerd.

#### Parameters {#parameters}

Alle parameters voor het bouwstijldoel worden beschreven in [Algemene parameters](#common-parameters) sectie.

### installeren {#install}

Hiermee installeert u een pakket in de opslagplaats. Voor de verwezenlijking van dit doel is geen Maven-project vereist. Het doel is gebonden aan de `install` fase van de levenscyclus van de Maven-build.

#### Parameters {#parameters-1}

Naast de volgende parameters, zie de beschrijvingen in [Algemene parameters](#common-parameters) sectie.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `artifact` | `String` | Nee | De waarde van `artifactId` eigendom van het Maven-project | Een tekenreeks van het formulier `groupId:artifactId:version[:packaging]` |
| `artifactId` | `String` | Nee | Geen | De id van het te installeren artefact |
| `groupId` | `String` | Nee | Geen | De `groupId` van het te installeren artefact |
| `install` | `boolean` | Nee | `true` | Hiermee wordt bepaald of het pakket automatisch moet worden uitgepakt wanneer het wordt geüpload |
| `localRepository` | `org.apache.maven.artifact.repository.ArtifactRepository` | Nee | De waarde van `localRepository` systeemvariabele | De lokale Maven opslagplaats die niet kan worden gevormd gebruikend de plugin configuratie aangezien het systeembezit altijd wordt gebruikt |
| `packageFile` | `java.io.File` | Nee | Het primaire artefact dat voor het Maven project wordt bepaald | De naam van het te installeren pakketbestand |
| `packaging` | `String` | Nee | `zip` | Het type verpakking van het te installeren artefact |
| `pomRemoteRepositories` | `java.util.List` | Ja | De waarde van `remoteArtifactRepositories` eigenschap die is gedefinieerd voor het Maven-project | Deze waarde kan niet worden gevormd gebruikend de pluginconfiguratie en moet in het project worden gespecificeerd. |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Het project waarvoor de insteekmodule is geconfigureerd | Het Maven-project dat impliciet is omdat het project de plug-inconfiguratie bevat |
| `repositoryId` (POM), `repoID` (opdrachtregel) | `String` | Nee | `temp` | De id van de opslagplaats waarvan het artefact wordt opgehaald |
| `repositoryUrl` (POM), `repoURL` (opdrachtregel) | `String` | Nee | Geen | De URL van de opslagplaats waarvan het artefact wordt opgehaald |
| versie | String | Nee | Geen | De versie van het artefact dat moet worden geïnstalleerd |

### ls {#ls}

Maakt een lijst van de pakketten die worden opgesteld aan [Pakketbeheer](/help/implementing/developing/tools/package-manager.md).

#### Parameters {#parameters-2}

Alle parameters van het doel ls worden beschreven in [Algemene parameters](#common-parameters) sectie.

### rm {#rm}

Een pakket verwijderen uit [Pakketbeheer](/help/implementing/developing/tools/package-manager.md).

#### Parameters {#parameters-3}

Alle parameters van het rm-doel worden beschreven in de [Algemene parameters](#common-parameters) sectie.

### verwijderen {#uninstall}

Hiermee wordt een pakket verwijderd. Het pakket blijft op de server staan in de toestand Niet-geïnstalleerd.

#### Parameters {#parameters-4}

Alle parameters van het doel voor verwijderen worden beschreven in het dialoogvenster [Algemene parameters](#common-parameters) sectie.

### package {#package}

Maakt een inhoudspakket. De standaardconfiguratie van het pakketdoel omvat de inhoud van de folder waar de gecompileerde dossiers worden bewaard. De uitvoering van het pakketdoel vereist dat de compilatiefase is voltooid. Het pakketdoel is gebonden aan de pakketfase van de Maven-levenscyclus.

#### Parameters {#parameters-5}

Naast de volgende parameters, zie de beschrijving van `name` in de [Algemene parameters](#common-parameters) sectie.

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `archive` | `org.apache.maven.archiver.MavenArchiveConfiguration` | Nee | Geen | De archiefconfiguratie die moet worden gebruikt |
| `builtContentDirectory` | `java.io.File` | Ja | De waarde van de uitvoerdirectory van de Maven-build | De map met de inhoud die in het pakket moet worden opgenomen |
| `dependencies` | `java.util.List` | Nee | Geen |  |
| `embeddedTarget` | `java.lang.String` | Nee | Geen |  |
| `embeddeds` | `java.util.List` | Nee | Geen |  |
| `failOnMissingEmbed` | `boolean` | Ja | `false` | Een waarde van `true` veroorzaakt de bouwstijl om te ontbreken wanneer een ingebed artefact niet in de projectgebiedsdelen wordt gevonden. Een waarde van `false` zorgt ervoor dat de build dergelijke fouten negeert. |
| `filterSource` | `java.io.File` | Nee | Geen | Deze parameter definieert een bestand dat de bron van het werkruimtefilter aangeeft. De filters die in de configuratie worden opgegeven en via inbedden of subpakketten worden geïnjecteerd, worden samengevoegd met de bestandsinhoud. |
| `filters` | `com.day.jcr.vault.maven.pack.impl.DefaultWorkspaceFilter` | Nee | Geen | Deze parameter bevat filterelementen die de pakketinhoud definiëren. Wanneer deze worden uitgevoerd, worden de filters opgenomen in de `filter.xml` bestand. Zie de [Filters gebruiken](#using-filters) hieronder. |
| `finalName` | `java.lang.String` | Ja | De `finalName` gedefinieerd in het Maven-project (bouwfase) | De naam van het gegenereerde ZIP-bestand voor het pakket, zonder het `.zip` bestandsextensie |
| `group` | `java.lang.String` | Ja | De `groupID` gedefinieerd in het Maven-project | De `groupId` van het gegenereerde inhoudspakket dat deel uitmaakt van het doelinstallatiepad voor het inhoudspakket |
| `outputDirectory` | `java.io.File` | Ja | De bouwstijlfolder die in het Gemaakt project wordt bepaald | De lokale map waar het inhoudspakket is opgeslagen |
| `prefix` | `java.lang.String` | Nee | Geen |  |
| `project` | `org.apache.maven.project.MavenProject` | Ja | Geen | Het Maven-project |
| `properties` | `java.util.Map` | Nee | Geen | Deze parameters definiëren aanvullende eigenschappen die u kunt instellen in het dialoogvenster `properties.xml` bestand. Deze eigenschappen kunnen de volgende vooraf gedefinieerde eigenschappen niet overschrijven: `group` (gebruik `group` in te stellen parameter), `name` (gebruik `name` in te stellen parameter), `version` (gebruik `version` in te stellen parameter), `description` (op basis van de projectbeschrijving), `groupId` (`groupId` van de Maven-projectdescriptor), `artifactId` (`artifactId` van de Maven-projectdescriptor), `dependencies` (gebruik `dependencies` in te stellen parameter), `createdBy` (de waarde van de `user.name` systeemeigenschap), `created` (de huidige systeemtijd), `requiresRoot` (gebruik `requiresRoot` in te stellen parameter), `packagePath` (wordt automatisch gegenereerd op basis van de groep en de pakketnaam) |
| `requiresRoot` | `boolean` | Ja | false | Definieert of het pakket root vereist. Wordt de `requiresRoot` eigendom van de `properties.xml` bestand. |
| `subPackages` | `java.util.List` | Nee | Geen |  |
| `version` | `java.lang.String` | Ja | De versie die is gedefinieerd in het Maven-project | De versie van het inhoudspakket |
| `workDirectory` | `java.io.File` | Ja | De folder die in het Maven project (bouwstijlfase wordt bepaald) | De map die de inhoud bevat die in het pakket moet worden opgenomen |

#### Filters gebruiken {#using-filters}

Gebruik het element filters om de pakketinhoud te definiëren. De filters worden toegevoegd aan de `workspaceFilter` in het `META-INF/vault/filter.xml` bestand van het pakket.

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

De `mode` element definieert hoe inhoud wordt beïnvloed door de repository wanneer het pakket wordt geïmporteerd. De volgende waarden kunnen worden gebruikt:

* **Samenvoegen:** Inhoud in het pakket die zich nog niet in de opslagplaats bevindt, wordt toegevoegd. De inhoud in zowel het pakket als de opslagplaats blijft ongewijzigd. Er wordt geen inhoud uit de opslagplaats verwijderd.
* **Vervangen:** Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket. Inhoud wordt verwijderd uit de opslagplaats wanneer deze niet bestaat in het pakket.
* **Bijwerken:** Inhoud in het pakket die zich niet in de opslagplaats bevindt, wordt toegevoegd aan de opslagplaats. Inhoud in de opslagplaats wordt vervangen door overeenkomende inhoud in het pakket.

Wanneer het filter geen `mode` -element, de standaardwaarde van `replace` wordt gebruikt.

### help {#help}

#### Parameters {#parameters-6}

| Naam | Type | Vereist | Standaardwaarde | Beschrijving |
|---|---|---|---|---|
| `detail` | `boolean` | Nee | `false` | Bepaalt of om alle settable eigenschappen voor elk doel te tonen |
| `goal` | `String` | Nee | Geen | Deze parameters bepalen de naam van het doel waarvoor om hulp te tonen. Als geen waarde wordt gespecificeerd, wordt de hulp voor alle doelstellingen getoond. |
| `indentSize` | `int` | Nee | `2` | Het aantal spaties dat moet worden gebruikt voor de inspringing van elk niveau (moet positief zijn als dit is gedefinieerd) |
| `lineLength` | `int` | Nee | `80` | De maximumlengte van een weergaveregel (moet positief zijn als deze is gedefinieerd) |

## Een miniatuurafbeelding of eigenschappenbestand opnemen in het pakket {#including-a-thumbnail-image-or-properties-file-in-the-package}

Vervang de standaardpakketconfiguratiebestanden om de pakketeigenschappen aan te passen. Neem bijvoorbeeld een miniatuurafbeelding om het pakket te onderscheiden in [Pakketbeheer](/help/implementing/developing/tools/package-manager.md).

U kunt de bronbestanden overal in uw bestandssysteem vinden. Definieer in het POM-bestand build-bronnen om de bronbestanden naar de `target/vault-work/META-INF` voor opname in het pakket.

De volgende POM-code voegt de bestanden toe aan de `META-INF` map van de projectbron naar het pakket:

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

Met de volgende POM-code wordt alleen een miniatuurafbeelding aan het pakket toegevoegd. De miniatuurafbeelding moet een naam hebben `thumbnail.png`en moet zich in de `META-INF/vault/definition` van het pakket. In dit voorbeeld bevindt het bronbestand zich in het dialoogvenster `/src/main/content/META-INF/vault/definition` map van het project:

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
>Zie de [AEM projectstructuur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) artikel in de AEM as a Cloud Service documentatie en de [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) documentatie. Beide worden volledig ondersteund voor AEM 6.5.
