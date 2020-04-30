---
title: AEM-projectstructuur
description: Leer hoe u pakketstructuren definieert voor implementatie op Adobe Experience Manager Cloud Service.
translation-type: tm+mt
source-git-commit: 94182b95cb00923d3e055cb3c2e1d943db70c7a9

---


# AEM-projectstructuur

>[!TIP]
>
>Zorg dat u uzelf vertrouwd bent met het basisgebruik [van de](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM-projectarchitectuur en de [insteekmodule](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html) FileVault Content Maven, aangezien dit artikel voortbouwt op deze lessen en concepten.

In dit artikel worden de wijzigingen beschreven die nodig zijn om Adobe Experience Manager Maven-projecten compatibel te maken met AEM Cloud Service door ervoor te zorgen dat ze de splitsing van muteerbare en onveranderbare inhoud respecteren. de nodige afhankelijkheden worden gecreëerd om niet-conflicterende, deterministische implementaties te creëren; en dat zij in een inzetbare structuur worden verpakt.

Implementaties van AEM-toepassingen moeten uit één AEM-pakket bestaan. Dit pakket dient op zijn beurt subpakketten te bevatten die alles omvatten wat door de toepassing wordt vereist om te functioneren, met inbegrip van code, configuratie en om het even welke ondersteunende basislijninhoud.

AEM vereist een scheiding van **content** en **code**, wat betekent dat één enkel contentpakket **niet kan** worden geïmplementeerd op **zowel** `/apps` als tijdens runtime beschrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home` of iets anders dan `/apps`) van de opslagplaats. In plaats daarvan moet de applicatie code en content scheiden in afzonderlijke pakketten voor implementatie in AEM.

De pakketstructuur die in dit document wordt beschreven, is compatibel met **zowel** lokale ontwikkelingsimplementaties als AEM Cloud Service-implementaties.

>[!TIP]
>
>De configuraties die in dit document worden beschreven, worden geleverd door [AEM Project Maven Archetype 21 of hoger](https://github.com/adobe/aem-project-archetype/releases).

## Mutable versus Immuable Areas of the Repository {#mutable-vs-immutable}

`/apps` en `/libs` worden beschouwd als **onveranderbare** gebieden van AEM omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dat wil zeggen tijdens runtime). Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

Al het andere in de opslagplaats, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, enz. Dit zijn allemaal **veranderbare** gebieden, wat betekent dat deze tijdens runtime kunnen worden gewijzigd.

>[!WARNING]
>
> Zoals in vorige versies van AEM, `/libs` zou niet moeten worden gewijzigd. Alleen AEM-productcode kan worden geïmplementeerd op `/libs`.

## Aanbevolen pakketstructuur {#recommended-package-structure}

![Experience Manager Project Package Structure](assets/content-package-organization.png)

Dit diagram verstrekt een overzicht van de geadviseerde projectstructuur en pakketplaatsingsartefacten.

De aanbevolen implementatiestructuur voor toepassingen is als volgt:

+ Het `ui.apps` pakket, of het Pakket van de Code, bevat alle code die moet worden opgesteld en slechts aan `/apps`opstelt. Gemeenschappelijke elementen van het `ui.apps` pakket zijn onder meer:
   + OSGi-bundels
      + `/apps/my-app/install`
   + OSGi-configuraties
      + `/apps/my-app/config`
   + HTML-scripts
      + `/apps/my-app/components`
   + JavaScript en CSS (via clientbibliotheken)
      + `/apps/my-app/clientlibs`
   + Bedekkingen van /libs
      + `/apps/cq`, `/apps/dam/`enz.
   + Contextbewuste configuraties voor alternatieven
      + `/apps/settings`
   + ACLs (toestemmingen)
      + Willekeurig pad `rep:policy` onder `/apps`
   + Repo Init OSGi configuratierichtlijnen (en begeleidende manuscripten)
      + [Repo Init](#repo-init) is de aanbevolen manier om (muteerbare) inhoud te implementeren die logisch deel uitmaakt van de AEM-toepassing. Repo Init moet worden gebruikt om te definiëren:
         + Structuren voor basislijninhoud
            + `/conf/my-app`
            + `/content/my-app`
            + `/content/dam/my-app`
         + Gebruikers
         + Servicegebruikers
         + Groepen
         + ACLs (toestemmingen)
            + Willekeurig pad `rep:policy` (veranderbaar of onveranderbaar)
+ Het `ui.content` pakket, of het Pakket van de Inhoud, bevat al inhoud en configuratie. Het inhoudspakket bevat alles wat niet in het `ui.apps` pakket staat, met andere woorden niets in `/apps` of `/oak:index`. Gemeenschappelijke elementen van het `ui.content` pakket zijn onder meer:
   + Contextbewuste configuraties
      + `/conf`
   + Vereiste, complexe inhoudsstructuren (d.w.z. De bouwstijl van de inhoud die voortbouwt op en zich voorbij de de inhoudsstructuren uitbreidt van de Basislijn die in RepoInit worden bepaald.
      + `/content`, `/content/dam`enz.
   + Regelgevende taggende taxonomieën
      + `/content/cq:tags`
   + Etc oudere knooppunten
      + `/etc`
+ Het pakket `all` is een containerpakket dat ALLEEN de pakketten `ui.apps` en `ui.content` als ingesloten items bevat. Het pakket `all` mag geen **eigen content** hebben, maar moet alle implementaties op de opslagplaats delegeren naar zijn subpakketten.

   Pakketten worden nu opgenomen met de insluitconfiguratie [van de Maven](#embeddeds)FileVault-plug-in voor Maven-bestanden in plaats van met de `<subPackages>` configuratie.

   Voor complexe plaatsingen van de Manager van de Ervaring, kan het wenselijk zijn om veelvoudige `ui.apps` en `ui.content` projecten/pakketten tot stand te brengen die specifieke plaatsen of huurders in AEM vertegenwoordigen. Als dit gebeurt, moet u ervoor zorgen dat de splitsing tussen muteerbare en onveranderlijke inhoud wordt gerespecteerd en dat de vereiste inhoudspakketten als subpakketten worden toegevoegd in het inhoudspakket van de `all` container.

   Een complexe structuur voor het pakket met implementatieinhoud kan er bijvoorbeeld als volgt uitzien:

   + `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
      + `ui.apps.common` implementeert code die vereist is voor **zowel** site A als site B
      + `ui.apps.site-a` implementeert code die door site A wordt vereist
      + `ui.content.site-a` stelt inhoud en configuratie op die door plaats A worden vereist
      + `ui.apps.site-b` implementeert code die vereist is voor site B
      + `ui.content.site-b` stelt inhoud en configuratie op die door plaats B worden vereist

## Pakkettypen {#package-types}

Pakketten moeten worden gemarkeerd met het opgegeven pakkettype.

+ Containerpakketten mogen geen `packageType` set bevatten.
+ Codepakketten (onveranderlijk) moeten hun `packageType` aan `application`.
+ Inhoudspakketten (veranderbare pakketten) moeten hun `packageType` op `content`.

Zie [Apache Jackrabbit FileVault - Package Maven Plugin-documentatie](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) en het [FileVault Maven-configuratiefragment](#marking-packages-for-deployment-by-adoube-cloud-manager) hieronder voor meer informatie.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-package-types) voor POM hieronder voor een volledig fragment.

## Pakketten markeren voor implementatie door Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Standaard worden alle pakketten die door de Maven-build worden gemaakt door Adobe Cloud Manager verzameld. Aangezien het containerpakket (`all`) het unieke implementatieartefact is dat alle code- en contentpakketten bevat, moeten we er echter voor zorgen dat **alleen** het containerpakket (`all`) wordt geïmplementeerd. Om dit te garanderen moeten andere pakketten die de Maven-build genereert, zijn gemarkeerd met de configuratie voor de FileVault Content Package Maven-invoegtoepassing van `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#pom-xml-snippets) voor POM hieronder voor een volledig fragment.

## Reparatie-item{#repo-init}

Repo Init verstrekt instructies, of manuscripten, die structuren JCR, die zich van gemeenschappelijke knoopstructuren zoals omslagbomen, aan gebruikers, de dienstgebruiker, groepen en ACL definitie bepalen.

De belangrijkste voordelen van Repo Init zijn zij impliciete toestemmingen hebben om alle acties uit te voeren die door hun manuscripten worden bepaald, en worden aangehaald vroeg in de plaatsingslevenscyclus die alle vereiste structuren JCR verzekeren tegen de tijdcode wordt uitgevoerd.

Terwijl de manuscripten van het Begin van de Repo in het `ui.apps` project zelf als manuscripten leven, kunnen en moeten zij worden gebruikt om de volgende veranderbare structuren te bepalen:

+ Structuren voor basislijninhoud
   + Examples: `/content/my-app`, `/content/dam/my-app`, `/conf/my-app/settings`
+ Servicegebruikers
+ Gebruikers
+ Groepen
+ ACLs

Scripts voor herhalingsindelingen worden opgeslagen als `scripts` vermeldingen van `RepositoryInitializer` OSGi-fabrieksconfiguraties en kunnen dus impliciet worden geactiveerd door de runmode, waardoor er verschillen kunnen optreden tussen de scripts voor de repo-invoer van AEM-auteur en AEM-publicatieservices, of zelfs tussen Envs (Dev, Stage en Prod).

Merk op dat wanneer het bepalen van Gebruikers, en Groepen, slechts groepen als deel van de toepassing worden beschouwd, en integraal aan zijn functie zou hier moeten worden bepaald. Organisatiegebruikers en -groepen moeten nog steeds bij uitvoering in AEM worden gedefinieerd; Bijvoorbeeld, als een douanewerkschema werk aan een genoemde Groep toewijst, zou die Groep binnen via Repo Init in de toepassing AEM moeten worden bepaald, echter als de Groepering slechts organisatorisch, zoals &quot;Team van Wendy&quot;en &quot;Team van Sean&quot;is, worden deze het best bepaald, en bij runtime in AEM geleid.

>[!TIP]
>
>Scripts voor herhalingsindelingen *moeten* in het inlineveld worden gedefinieerd en de `scripts` `references` configuratie werkt niet.

De volledige woordenlijst voor scripts van Repo Init is beschikbaar in de documentatie [van](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)Apache Sling Repo Init.

>[!TIP]
>
>Zie de sectie [Repo Init Snippets](#snippet-repo-init) hieronder voor een volledig fragment.

## Structuurpakket opslagplaats {#repository-structure-package}

Codepakketten vereisen dat de configuratie van de FileVault Maven-plug-in wordt geconfigureerd om te verwijzen naar een `<repositoryStructurePackage>` methode die de juistheid van structurele afhankelijkheden afdwingt (om ervoor te zorgen dat een codepakket niet boven een ander codepakket wordt geïnstalleerd). U kunt uw eigen structuurpakket voor uw project [](repository-structure-package.md)maken.

Dit is **alleen vereist** voor codepakketten. (Dit zijn pakketten die zijn gemarkeerd met `<packageType>application</packageType>`.)

Zie Een structuurpakket voor opslagplaatsen [ontwikkelen voor meer informatie over het maken van een pakket](repository-structure-package.md)met opslagplaatsen voor uw toepassing.

Voor inhoudspakketten (`<packageType>content</packageType>`) is dit &#39;opslagplaatsstructuurpakket&#39; **niet** vereist.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-repository-structure-package) voor POM hieronder voor een volledig fragment.

## Subpakketten insluiten in het Containerpakket{#embeddeds}

Inhoud- of codepakketten worden in een speciale map &quot;side-car&quot; geplaatst en kunnen worden geïnstalleerd op AEM-auteur, AEM-publicatie of beide met behulp van de `<embeddeds>` configuratie van de FileVault Maven-plug-in. Merk op dat de `<subPackages>` configuratie niet zou moeten worden gebruikt.

Veelvoorkomende gebruiksgevallen zijn:

+ ACLs/toestemmingen die tussen AEM auteursgebruikers en AEM publiceren gebruikers verschillen
+ Configuraties die alleen worden gebruikt ter ondersteuning van activiteiten bij AEM-auteur
+ Code, zoals integratie met back-office systemen, die alleen vereist is voor AEM-auteur

![Pakketten insluiten](assets/embeddeds.png)

Als u de auteur van AEM, AEM-publicatie of beide als doel wilt instellen, wordt het pakket ingesloten in het `all` containerpakket in een speciale maplocatie, in de volgende indeling:

`/apps/<app-name>-packages/(content|application)/install(.author|.publish)?`

Deze mappenstructuur omlaag splitsen:

+ De map op het eerste niveau **moet een map zijn** `/apps`.
+ De map op het tweede niveau vertegenwoordigt de toepassing waarvan de mapnaam is `-packages` hersteld. Vaak is er slechts één map op het tweede niveau waarin alle subpakketten zijn ingesloten. Elk aantal mappen op het tweede niveau kan echter zo worden gemaakt dat dit de logische structuur van de toepassing het best weerspiegelt:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`
   >[!WARNING]
   >
   >Op basis van conventies krijgen ingesloten mappen in subpakketten een naam met het achtervoegsel `-packages`. Dit zorgt ervoor dat de code- en contentpakketten van de implementatie **niet** worden geïmplementeerd op de doelmappen van een subpakket `/apps/<app-name>/...`, hetgeen resulteert in destructief en cyclisch installatiegedrag.

+ De map op het derde niveau moet ofwel
   `application` or `content`
   + De `application` map bevat codepakketten
   + De `content` map bevat pakketten met goudinhoud. Deze mapnaam moet overeenkomen met de [pakkettypen](#package-types) van de pakketten die de map bevat.
+ De map op het vierde niveau bevat de subpakketten en moet een van de volgende zijn:
   + `install` om te installeren op **zowel** de AEM-auteur als de AEM-publicatie
   + `install.author` om **alleen** te installeren op de AEM-auteur
   + `install.publish` om **alleen** op AEM publishNote te installeren dat alleen `install.author` en `install.publish` ondersteunde doelen zijn. Andere uitvoermodi **worden niet** ondersteund.

Een implementatie die AEM-auteur bevat en specifieke pakketten publiceert, kan er bijvoorbeeld als volgt uitzien:

+ `all` Containerpakket sluit de volgende pakketten in om een enkelvoudig implementatieartefact te maken
   + `ui.apps` ingesloten in `/apps/my-app-packages/application/install` implementeert code naar zowel AEM-auteur als AEM-publicatie
   + `ui.apps.author` ingesloten in `/apps/my-app-packages/application/install.author` implementeert code alleen naar AEM-auteur
   + `ui.content` ingesloten in `/apps/my-app-packages/content/install` implementeert inhoud en configuratie naar zowel AEM-auteur als AEM-publicatie
   + `ui.content.publish` ingesloten in `/apps/my-app-packages/content/install.publish` implementeert inhoud en configuratie alleen voor publicatie door AEM

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-embeddeds) voor POM hieronder voor een volledig fragment.

### Filterdefinitie van containerpakket {#container-package-filter-definition}

Wegens het inbedden van de code en inhoudsubpakketten in het containerpakket, moeten de ingebedde doelwegen aan het containerproject worden toegevoegd `filter.xml` om ervoor te zorgen de ingebedde pakketten in het containerpakket inbegrepen zijn wanneer gebouwd.

Voeg eenvoudig de `<filter root="/apps/<my-app>-packages"/>` ingangen voor om het even welke tweede niveauomslagen toe die subpakketten bevatten om op te stellen.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-container-package-filters) voor POM hieronder voor een volledig fragment.

## Pakketten van derden insluiten {#embedding-3rd-party-packages}

Alle pakketten moeten beschikbaar zijn via de openbare gegevensopslagruimte [van Maven Artefact van](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) Adobe of via een toegankelijke openbare gegevensopslagruimte van derden waarnaar kan worden verwezen.

Als de pakketten van derden zich in de **openbare Maven-artefactopslagplaats van Adobe** bevinden, is geen verdere configuratie nodig wanneer Adobe Cloud Manager de artefacten oplost.

Als de pakketten van derden zich in een **openbare Maven-artefactopslagplaats van derden** bevinden, moet deze opslagplaats worden geregistreerd in de `pom.xml` van het project en worden ingesloten volgens de [hierboven beschreven](#embeddeds) methode. Als voor de applicatie/connector van derden zowel code- als contentpakketten zijn vereist, moet elk pakket zijn ingesloten in de juiste locaties in het containerpakket (`all`).

Het toevoegen van Geweven gebiedsdelen volgt standaard Geweven praktijken, en het inbedden van derdeartefacten (code en inhoudspakketten) worden [geschetst hierboven](#embedding-3rd-party-packages).

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-3rd-party-maven-repositories) voor POM hieronder voor een volledig fragment.

## Afhankelijkheden tussen pakketten `ui.apps` van `ui.content` pakketten {#package-dependencies}

Om een correcte installatie van de pakketten te waarborgen, wordt aanbevolen om afhankelijkheden tussen pakketten tot stand te brengen.

De algemene regel is dat pakketten met veranderbare inhoud (`ui.content`) afhankelijk moeten zijn van de onveranderlijke inhoud (`ui.apps`) die het renderen en het gebruik van de veranderbare inhoud ondersteunt.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-package-dependencies) voor POM hieronder voor een volledig fragment.

De gemeenschappelijke patronen voor tevreden pakketgebiedsdelen zijn:

### Eenvoudige implementatiepakketafhankelijkheden {#simple-deployment-package-dependencies}

Met het eenvoudige hoofdlettergebruik wordt het `ui.content` veranderbare inhoudspakket zo ingesteld dat het afhankelijk is van het `ui.apps` onveranderlijke codepakket.

+ `all` heeft geen afhankelijkheden
   + `ui.apps` heeft geen afhankelijkheden
   + `ui.content` afhankelijk van `ui.apps`

### Complexe implementatiepakketafhankelijkheden {#complex-deploxment-package-dependencies}

De complexe plaatsingen breiden zich op het eenvoudige geval uit, en plaatsen gebiedsdelen tussen de overeenkomstige veranderlijke inhoud en de onveranderlijke codepakketten. Zoals vereist, kunnen de gebiedsdelen ook tussen onveranderlijke codepakketten worden gevestigd.

+ `all` heeft geen afhankelijkheden
   + `ui.apps.common` heeft geen afhankelijkheden
   + `ui.apps.site-a` afhankelijk van `ui.apps.common`
   + `ui.content.site-a` afhankelijk van `ui.apps.site-a`
   + `ui.apps.site-b` afhankelijk van `ui.apps.common`
   + `ui.content.site-b` afhankelijk van `ui.apps.site-b`

## Lokale ontwikkeling en implementatie {#local-development-and-deployment}

De in dit artikel beschreven projectstructuren en -organisatie zijn **volledig compatibel** met AEM-instanties voor lokale ontwikkeling.

## XML-fragmenten voor POM {#pom-xml-snippets}

Het volgende is Gemaakt `pom.xml` configuratiefragmenten die aan Geweven projecten kunnen worden toegevoegd om aan de bovengenoemde aanbevelingen te richten.

### Pakkettypen {#xml-package-types}

Code- en contentpakketten die als subpakketten worden geïmplementeerd, moeten het pakkettype **applicatie** of **content** declareren, afhankelijk van wat ze bevatten.

#### Containerpakkettypen {#container-package-types}

Het containerproject `all/pom.xml` verklaart **geen** a `<packageType>`.

#### Code (Immuable) pakkettypen {#immutable-package-types}

Codepakketten moeten hun `packageType` instellen op `application`.

In de `ui.apps/pom.xml`, verklaart de richtlijnen van de `<packageType>application</packageType>` bouwstijlconfiguratie van de `filevault-package-maven-plugin` plugin zijn pakkettype.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>${my-app.ui.apps}</name>
        <packageType>application</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

#### Inhoud (Mutable) Pakkettypen {#mutable-package-types}

Inhoudspakketten moeten hun `packageType` waarde instellen op `content`.

In de `ui.content/pom.xml`, verklaart de richtlijn van de `<packageType>content</packageType>` bouwstijlconfiguratie van de `filevault-package-maven-plugin` plugin verklaring zijn pakkettype.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        <group>${project.groupId}</group>
        <name>${my-app.ui.content}</name>
        <packageType>content</packageType>
        <accessControlHandling>merge</accessControlHandling>
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Pakketten markeren voor implementatie van Adobe Cloud Manager {#cloud-manager-target}

In elk project dat een pakket genereert, **behalve** voor het containerproject (`all`), voegt u `<cloudManagerTarget>none</cloudManagerTarget>` aan de `<properties>`-configuratie van de declaratie van de invoegtoepassing `filevault-package-maven-plugin` toe om ervoor te zorgen dat deze **niet** door Adobe Cloud Manager worden geïmplementeerd. Het containerpakket (`all`) moet het enkelvoudige pakket zijn dat via Cloud Manager wordt geïmplementeerd en dat op zijn beurt alle vereiste code- en contentpakketten insluit.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <properties>
          <cloudManagerTarget>none</cloudManagerTarget>
        </properties>
      </configuration>
    </plugin>
    ...
```

### Reparatie-item{#snippet-repo-init}

Scripts voor Repo Init die de scripts voor Repo Init bevatten, worden gedefinieerd in de `RepositoryInitializer` OSGi-fabrieksconfiguratie via de `scripts` eigenschap. Merk op dat aangezien deze manuscripten binnen configuraties OSGi worden bepaald, zij gemakkelijk door runmode kunnen zijn gebruikend de gebruikelijke `../config.<runmode>` omslagsemantiek.

Aangezien scripts doorgaans een declaratie met meerdere regels zijn, is het eenvoudiger om ze in het `.config` bestand te definiëren dan in de `sling:OsgiConfig` indeling XML.

`/apps/my-app/config.author/org.apache.sling.jcr.repoinit.RepositoryInitializer-author.config`

```plain
scripts=["
    create service user my-data-reader-service

    set ACL on /var/my-data
        allow jcr:read for my-data-reader-service
    end

    create path (sling:Folder) /conf/my-app/settings
"]
```

Het `scripts` bezit OSGi bevat richtlijnen zoals die door de [Repo Init taal](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)van Apache Sling worden bepaald.

### Structuurpakket opslagplaats {#xml-repository-structure-package}

Voeg in de `ui.apps/pom.xml` en een andere `pom.xml` code die een codepakket (`<packageType>application</packageType>`) declareert, de volgende configuratie van het opslagplaatsstructuurpakket toe aan de FileVault Maven-plug-in. U kunt uw eigen structuurpakket voor uw project [](repository-structure-package.md)maken.

```xml
...
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.jackrabbit</groupId>
      <artifactId>filevault-package-maven-plugin</artifactId>
      <extensions>true</extensions>
      <configuration>
        ...
        <repositoryStructurePackages>
          <repositoryStructurePackage>
              <groupId>${project.groupId}</groupId>
              <artifactId>ui.apps.structure</artifactId>
              <version>${project.version}</version>
          </repositoryStructurePackage>
        </repositoryStructurePackages>
      </configuration>
    </plugin>
    ...
```

### Subpakketten insluiten in het Containerpakket {#xml-embeddeds}

Voeg in de `all/pom.xml`sectie de volgende `<embeddeds>` instructies toe aan de `filevault-package-maven-plugin` insteekmoduledeclaratie. Herinner me, **gebruik niet** de `<subPackages>` configuratie, aangezien dit subpakketten in `/etc/packages` plaats van `/apps/my-app-packages/<application|content>/install(.author|.publish)?`zal omvatten.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          <!-- Include the application's ui.apps and ui.content packages -->
          <!-- Ensure the artifactIds are correct -->

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys ONLY to AEM Author -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps.author</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install.author</target>
          </embedded>

          <!-- Content package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install</target>
          </embedded>

          <!-- Content package that deploys ONLY to AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.content.publish-only</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/content/install.publish</target>
          </embedded>

          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Code package's artifact is named `.content` -->
              <artifactId>core.wcm.components.content</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/application/install</target>
          </embedded>

          <embedded>
              <groupId>com.adobe.cq</groupId>
              <!-- Not to be confused; WCM Core Components' Content package's artifact is named `.conf` -->
              <artifactId>core.wcm.components.conf</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/content/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

### Filterdefinitie van containerpakket {#xml-container-package-filters}

In het `filter.xml` van het project `all` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), moeten alle `-packages` met subpakketten voor implementatie worden **opgenomen**:

```xml
<filter root="/apps/my-app-packages"/>
```

Als de veelvoudige `/apps/*-packages` in ingebedde doelstellingen worden gebruikt, dan moeten zij allen hier worden opgesomd.

### Bewaarplaatsen van derden {#xml-3rd-party-maven-repositories}

>[!WARNING]
> Als u meer Maven-repositories toevoegt, kunnen de gefabriceerde buildtijden langer duren omdat extra Maven-opslagplaatsen op afhankelijkheden worden gecontroleerd.

Voeg in het reactorproject de noodzakelijke richtlijnen van de derde partij inzake openbare opslagplaats Maven toe `pom.xml`. De volledige `<repository>` configuratie moet beschikbaar zijn bij de externe opslagprovider.

```xml
<repositories>
  ...
  <repository>
      <id>3rd-party-repository</id>
      <name>Public 3rd Party Repository</name>
      <url>https://repo.3rdparty.example.com/...</url>
      <releases>
          <enabled>true</enabled>
          <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
          <enabled>false</enabled>
      </snapshots>
  </repository>
  ...
</repositories>
```

### Afhankelijkheden tussen pakketten `ui.apps` van `ui.content` pakketten {#xml-package-dependencies}

Voeg in de `ui.content/pom.xml`sectie de volgende `<dependencies>` instructies toe aan de `filevault-package-maven-plugin` insteekmoduledeclaratie.

```xml
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <dependencies>
        <!-- Declare the content package dependency in the ui.content/pom.xml on the ui.apps project -->
        <dependency>
            <groupId${project.groupId}</groupId>
            <artifactId>my-app.ui.apps</artifactId>
            <version>${project.version}</version>
        </dependency>
      </dependencies>
    ...
  </configuration>
</plugin>
...
```

### De doelmap van het containerproject opschonen {#xml-clean-container-package}

Voeg in het `all/pom.xml` dialoogvenster de `maven-clean-plugin` plug-in toe waarmee de doelmap wordt gewist voordat een Maven-versie wordt gemaakt.

```xml
<plugins>
  ...
  <plugin>
    <artifactId>maven-clean-plugin</artifactId>
    <executions>
      <execution>
        <id>auto-clean</id>
        <!-- Run at the beginning of the build rather than the default, which is after the build is done -->
        <phase>initialize</phase>
        <goals>
          <goal>clean</goal>
        </goals>
      </execution>
    </executions>
  </plugin>
  ...
</plugins>
```

## Aanvullende bronnen {#additional-resources}

+ [Pakketten beheren met Maven](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html)
+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](http://jackrabbit.apache.org/filevault-package-maven-plugin/)