---
title: AEM-projectstructuur
description: Leer hoe u pakketstructuren definieert voor implementatie op Adobe Experience Manager Cloud Service.
translation-type: tm+mt
source-git-commit: f9a6dbec25b8154fda8069ff213aaaaa1d443ca1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# AEM-projectstructuur

>[!TIP]
>
>Zorg dat u uzelf vertrouwd bent met de standaard [AEM Project Archetype use](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html) en de [FileVault Content Maven Plug-in](/help/implementing/developing/tools/maven-plugin.md), aangezien dit artikel voortbouwt op deze lessen en concepten.

Dit artikel beschrijft de veranderingen die aan Adobe Experience Manager Maven projecten worden vereist om als Cloud Service compatibel te worden AEM door ervoor te zorgen dat zij de splitsing van veranderbare en onveranderlijke inhoud eerbiedigen, gebiedsdelen worden gevestigd om niet-strijdige, deterministische plaatsingen tot stand te brengen en dat zij in een plaatsingsable structuur worden verpakt.

AEM toepassingsimplementaties moeten bestaan uit één AEM. Dit pakket dient op zijn beurt subpakketten te bevatten die alles omvatten wat door de toepassing wordt vereist om te functioneren, met inbegrip van code, configuratie en om het even welke ondersteunende basislijninhoud.

AEM vereist een scheiding van **content** en **code**, wat betekent dat één enkel contentpakket **niet kan** worden geïmplementeerd op **zowel** `/apps` als tijdens runtime beschrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home` of iets anders dan `/apps`) van de opslagplaats. In plaats daarvan moet de applicatie code en content scheiden in afzonderlijke pakketten voor implementatie in AEM.

De pakketstructuur die in dit document wordt beschreven, is compatibel met **zowel** lokale ontwikkelingsimplementaties als AEM Cloud Service-implementaties.

>[!TIP]
>
>De configuraties die in dit document worden geschetst, worden geleverd door [AEM Project Maven Archetype 24 of later](https://github.com/adobe/aem-project-archetype/releases).

## Mutable versus Immuable Areas of the Repository {#mutable-vs-immutable}

`/apps` en `/libs`**worden beschouwd als onveranderbare gebieden van AEM omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dat wil zeggen tijdens runtime).** Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

Alle overige gegevens in de opslagplaats, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, enz. zijn alle **mutable** gebieden, wat betekent zij kunnen bij runtime worden veranderd.

>[!WARNING]
>
>Zoals in vorige versies van AEM, `/libs` zou niet moeten worden gewijzigd. Alleen AEM productcode kan worden geïmplementeerd op `/libs`.

### Oak-indexen {#oak-indexes}

De indexen van de eiken (`/oak:index`) worden specifiek beheerd door de AEM als proces van de Cloud Service plaatsing. De reden hiervoor is dat de Cloud Manager moet wachten totdat een nieuwe index wordt geïmplementeerd en volledig opnieuw wordt geïndexeerd voordat naar de nieuwe codeafbeelding wordt overgeschakeld.

Daarom, hoewel de indexen van de eiken in runtime veranderbaar zijn, moeten zij als code worden opgesteld zodat zij kunnen worden geïnstalleerd alvorens om het even welke veranderlijke pakketten worden geïnstalleerd. Daarom maken `/oak:index` configuraties deel uit van het Pakket van de Code en geen deel van het Pakket van de Inhoud [zoals hieronder beschreven ](#recommended-package-structure).

>[!TIP]
>
>Zie het document [Zoeken naar en indexeren van inhoud](/help/operations/indexing.md) voor meer informatie over indexering in AEM als Cloud Service.

## Aanbevolen pakketstructuur {#recommended-package-structure}

![Experience Manager projectpakketstructuur](assets/content-package-organization.png)

Dit diagram verstrekt een overzicht van de geadviseerde projectstructuur en pakketplaatsingsartefacten.

De aanbevolen implementatiestructuur voor toepassingen is als volgt:

### Codepakketten / OSGi-bundels

+ Het Jar-bestand van de bundel OSGi wordt gegenereerd en rechtstreeks ingesloten in het hele project.

+ Het `ui.apps`-pakket bevat alle code die moet worden geïmplementeerd en wordt alleen geïmplementeerd op `/apps`. Veelvoorkomende elementen van het `ui.apps`-pakket zijn onder meer:
   + [Componentdefinities en ](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) HTML-scripts
      + `/apps/my-app/components`
   + JavaScript en CSS (via [Clientbibliotheken](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [](/help/implementing/developing/introduction/overlays.md) Bedekkingen van  `/libs`
      + `/apps/cq`,  `/apps/dam/`enz.
   + Contextbewuste configuraties voor alternatieven
      + `/apps/settings`
   + ACLs (toestemmingen)
      + Elke `rep:policy` voor een pad onder `/apps`

+ Het `ui.config`-pakket bevat alle [OSGi-configuraties](/help/implementing/deploying/configuring-osgi.md):
   + De omslag van de organisatie die loopwijze specifieke definities OSGi config bevat
      + `/apps/my-app/osgiconfig`
   + Gemeenschappelijke OSGi configuratiemap die standaardOSGi configuraties bevat die op al doel AEM als doelstellingen van de Cloud Service plaatsing van toepassing zijn
      + `/apps/my-app/osgiconfig/config`
   + De wijze-specifieke OSGi configuratiemappen van de looppas die standaardOSGi configuraties bevat die op alle AEM als doelstellingen van de Cloud Service plaatsing van toepassing zijn
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi-configuratiescripts
      + [Repo ](#repo-init) Initis de geadviseerde manier om (mutable) inhoud op te stellen die logisch gezien deel van de AEM toepassing uitmaakt. De configuraties van OSGi van het Punt van de Repo zouden in de aangewezen `config.<runmode>` omslag moeten worden geplaatst zoals hierboven geschetst, en worden gebruikt om te bepalen:
         + Structuren voor basislijninhoud
         + Gebruikers
         + Servicegebruikers
         + Groepen
         + ACLs (toestemmingen)


### Inhoudspakketten

+ Het `ui.content`-pakket bevat alle inhoud en configuratie. Het inhoudspakket bevat alle knoopdefinities die niet in de pakketten `ui.apps` of `ui.config` of in andere woorden, niets in `/apps` of `/oak:index` staan. Veelvoorkomende elementen van het `ui.content`-pakket zijn onder meer:
   + Contextbewuste configuraties
      + `/conf`
   + Vereiste, complexe inhoudsstructuren (d.w.z. De bouwstijl van de inhoud die voortbouwt op en zich voorbij de de inhoudsstructuren van de Basislijn uitbreidt die in Repo worden bepaald.)
      + `/content`,  `/content/dam`enz.
   + Regelgevende taggende taxonomieën
      + `/content/cq:tags`
   + Verouderde knooppunten, enz. (idealiter migreren deze naar locaties die niet- of etc. zijn)
      + `/etc`

### Containerpakketten

+ Het `all`-pakket is een containerpakket dat ALLEEN implementeerbare artefacten, het OSGI-bundel Jar-bestand, `ui.apps`-, `ui.config`- en `ui.content`-pakketten als insluitingen bevat. Het `all`-pakket mag geen **inhoud of code** van zichzelf hebben, maar moet alle implementatie naar de opslagplaats delegeren aan zijn subpakketten of OSGi-bundelJar-bestanden.

   Pakketten worden nu opgenomen met de ingesloten configuratie](#embeddeds) van de Maven [FileVault-pakket Maven-plug-in in plaats van de `<subPackages>`-configuratie.

   Voor complexe implementaties van Experience Managers kan het wenselijk zijn meerdere `ui.apps`-, `ui.config`- en `ui.content`-projecten/pakketten te maken die specifieke sites of huurders in AEM vertegenwoordigen. Als dit wordt gedaan, zorg ervoor de scheiding tussen veranderlijke en onveranderlijke inhoud wordt geëerbiedigd, en de vereiste inhoudspakketten en de bundel OSGi Jar dossiers worden ingebed als subpakketten in `all` containerinhoudspakket.

   Bijvoorbeeld, zou een complexe het pakketstructuur van de plaatsingsinhoud als dit kunnen kijken:

   + `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
      + `common.ui.apps` code implementeert die vereist is door  **** zowel site A als site B
      + `site-a.core` OSGi-bundel Jar vereist voor site A
      + `site-a.ui.apps` implementeert code die door site A wordt vereist
      + `site-a.ui.config` stelt configuraties OSGi op die door Plaats A worden vereist
      + `site-a.ui.content` stelt inhoud en configuratie op die door plaats A worden vereist
      + `site-b.core` OSGi-bundel Jar vereist voor site B
      + `site-b.ui.apps` implementeert code die vereist is voor site B
      + `site-b.ui.config` stelt configuraties OSGi op die door plaats B worden vereist
      + `site-b.ui.content` stelt inhoud en configuratie op die door plaats B worden vereist

### Extra toepassingspakketten{#extra-application-packages}

Als andere AEM projecten, die zelf uit hun eigen code en inhoudspakketten bestaan, door de AEM plaatsing worden gebruikt, zouden hun containerpakketten in het `all` pakket van het project moeten worden ingebed.

Bijvoorbeeld, zou een AEM project dat 2 verkoper AEM toepassingen omvat als kunnen kijken:

+ `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
   + `core` OSGi bundle Jar vereist door de AEM toepassing
   + `ui.apps` implementeert code die vereist is voor de AEM toepassing
   + `ui.config` stelt configuraties OSGi op die door de AEM toepassing worden vereist
   + `ui.content` stelt inhoud en configuratie op die door de AEM toepassing worden vereist
   + `vendor-x.all` implementeert alles (code en inhoud) dat vereist is door de X-toepassing van de leverancier
   + `vendor-y.all` stelt alles (code en inhoud) op die door de verkoperY toepassing wordt vereist

## Pakkettypen {#package-types}

Pakketten moeten worden gemarkeerd met het opgegeven pakkettype.

+ Containerpakketten moeten hun `packageType` instellen op `container`. Containerpakketten mogen geen OSGi-bundels, OSGi-configuraties direct bevatten en mogen geen [installatiekoppels](http://jackrabbit.apache.org/filevault/installhooks.html) gebruiken.
+ Codepakketten (onveranderlijk) moeten hun `packageType` aan `application` plaatsen.
+ Inhoudspakketten (veranderbare pakketten) moeten hun `packageType` op `content` plaatsen.


Zie [Apache Jackrabbit FileVault - Package Maven Plugin documentation](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType) en het [FileVault Maven configuratiesfragment](#marking-packages-for-deployment-by-adoube-cloud-manager) hieronder voor meer informatie.

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-package-types) hieronder voor een volledig fragment.

## Pakketten markeren voor implementatie door Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Standaard worden alle pakketten die door de Maven-build worden gemaakt door Adobe Cloud Manager verzameld. Aangezien het containerpakket (`all`) het unieke implementatieartefact is dat alle code- en contentpakketten bevat, moeten we er echter voor zorgen dat **alleen** het containerpakket (`all`) wordt geïmplementeerd. Om dit te garanderen moeten andere pakketten die de Maven-build genereert, zijn gemarkeerd met de configuratie voor de FileVault Content Package Maven-invoegtoepassing van `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#pom-xml-snippets) hieronder voor een volledig fragment.

## Repo-inkt{#repo-init}

Repo Init verstrekt instructies, of manuscripten, die structuren JCR, die zich van gemeenschappelijke knoopstructuren zoals omslagbomen, aan gebruikers, de dienstgebruiker, groepen en ACL definitie bepalen.

De belangrijkste voordelen van Repo Init zijn zij impliciete toestemmingen hebben om alle acties uit te voeren die door hun manuscripten worden bepaald, en worden aangehaald vroeg in de plaatsingslevenscyclus die alle vereiste structuren JCR verzekeren tegen de tijdcode wordt uitgevoerd.

Terwijl de manuscripten van het Begin van de Repo in het `ui.config` project als manuscripten leven, kunnen en moeten zij worden gebruikt om de volgende veranderbare structuren te bepalen:

+ Structuren voor basislijninhoud
+ Servicegebruikers
+ Gebruikers
+ Groepen
+ ACLs

De manuscripten van de Inzet van de Repo worden opgeslagen als `scripts` ingangen van `RepositoryInitializer` OSGi fabrieksconfiguraties, en kunnen daarom impliciet door looppas worden gericht, die voor verschillen tussen de manuscripten van de Inzet van de Auteur AEM en van de Publicatie van de Diensten van de Publicatie AEM, of zelfs tussen milieu&#39;s (Dev, Stadium en Prod) toestaan.

Repo Init OSGi configureert is het best geschreven in [`.config` OSGi configuratieformaat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) aangezien zij multi-lines steunen, die een uitzondering op de beste praktijken is om [`.cfg.json` te gebruiken om configuraties te bepalen OSGi](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

Merk op dat wanneer het bepalen van Gebruikers, en Groepen, slechts groepen als deel van de toepassing worden beschouwd, en integraal aan zijn functie zou hier moeten worden bepaald. De gebruikers en de Groepen van de organisatie zouden nog bij runtime in AEM moeten worden bepaald; Bijvoorbeeld, als een douanewerkschema werk aan een genoemde Groep toewijst, zou die Groep binnen via RepoInit in de AEM toepassing moeten worden bepaald, echter als de Groepering slechts organisatorisch is, zoals &quot;Team van Wendy&quot;en &quot;Team van Sean&quot;, zijn deze het best bepaald, en beheerd bij runtime in AEM.

>[!TIP]
>
>Scripts voor herhalingsinvoer *must* moeten worden gedefinieerd in het veld inline `scripts` en de configuratie `references` werkt niet.

De volledige woordenlijst voor scripts van Repo Init is beschikbaar in de [documentatie van het Start van Apache Sling Repo Init](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>Zie de sectie [Fragmenten voor herhaling van invoer](#snippet-repo-init) hieronder voor een volledig fragment.

## Structuurpakket opslagplaats {#repository-structure-package}

Codepakketten vereisen dat de configuratie van de FileVault Maven-plug-in wordt geconfigureerd om te verwijzen naar een `<repositoryStructurePackage>` die de juistheid van structurele afhankelijkheden afdwingt (om ervoor te zorgen dat één codepakket niet boven een ander wordt geïnstalleerd). U kunt [uw eigen opslagstructuurpakket maken voor uw project](repository-structure-package.md).

Dit is **alleen vereist** voor codepakketten. (Dit zijn pakketten die zijn gemarkeerd met `<packageType>application</packageType>`.)

Zie [Een structuurpakket voor opslagplaats ontwikkelen](repository-structure-package.md) voor meer informatie over het maken van een pakket voor opslagplaats voor uw toepassing.

Voor inhoudspakketten (`<packageType>content</packageType>`) **do not** is dit pakket met opslagplaatsstructuurvereisten vereist.

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-repository-structure-package) hieronder voor een volledig fragment.

## Subpakketten insluiten in het containerpakket{#embeddeds}

Inhoud- of codepakketten worden in een speciale map &quot;side-car&quot; geplaatst en kunnen worden gebruikt voor installatie op AEM auteur, AEM publicatie of beide, met behulp van de `<embeddeds>`-configuratie van de FileVault Maven-plug-in. Merk op dat `<subPackages>` configuratie niet zou moeten worden gebruikt.

Veelvoorkomende gebruiksgevallen zijn:

+ ACLs/toestemmingen die tussen AEM auteursgebruikers en AEM publicatiegebruikers verschillen
+ Configuraties die alleen worden gebruikt ter ondersteuning van activiteiten van AEM auteur
+ Code zoals integratie met back-office systemen, die alleen vereist is voor AEM auteur

![Pakketten insluiten](assets/embeddeds.png)

Als u AEM auteur als doel wilt instellen, AEM publiceren of beide, wordt het pakket ingesloten in het containerpakket `all` in een speciale map-locatie, in de volgende indeling:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

Deze mappenstructuur omlaag splitsen:

+ De map op het eerste niveau **moet** `/apps` zijn.
+ De map op het tweede niveau vertegenwoordigt de toepassing waarvan `-packages` is hersteld naar de mapnaam. Vaak is er slechts één map op het tweede niveau waarin alle subpakketten zijn ingesloten. Elk aantal mappen op het tweede niveau kan echter zo worden gemaakt dat dit de logische structuur van de toepassing het best weerspiegelt:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

   >[!WARNING]
   >
   >Op basis van conventies krijgen ingesloten mappen in subpakketten een naam met het achtervoegsel `-packages`. Dit zorgt ervoor dat de code- en contentpakketten van de implementatie **niet** worden geïmplementeerd op de doelmappen van een subpakket `/apps/<app-name>/...`, hetgeen resulteert in destructief en cyclisch installatiegedrag.

+ De map op het derde niveau moet ofwel
   `application`,  `content` of  `container`
   + De map `application` bevat codepakketten
   + De map `content` bevat inhoudspakketten
   + In de map `container` staan [extra toepassingspakketten](#extra-application-packages) die mogelijk door de AEM toepassing worden opgenomen.
Deze mapnaam komt overeen met de [pakkettypen](#package-types) van de pakketten die erin staan.
+ De map op het vierde niveau bevat de subpakketten en moet een van de volgende zijn:
   + `install` om te installeren op **zowel** de AEM-auteur als de AEM-publicatie
   + `install.author` om **alleen** te installeren op de AEM-auteur
   + `install.publish` om  **** alleen op AEM te installeren Opmerking: alleen  `install.author` en  `install.publish` ondersteunde doelen. Andere uitvoermodi **worden niet** ondersteund.

Een implementatie die AEM auteur bevat en specifieke pakketten publiceert, kan er bijvoorbeeld als volgt uitzien:

+ `all` Containerpakket sluit de volgende pakketten in om een enkelvoudig implementatieartefact te maken
   + `ui.apps` ingebed in  `/apps/my-app-packages/application/install` stelt code aan zowel auteur als AEM publiceren op
   + `ui.apps.author` ingebed in  `/apps/my-app-packages/application/install.author` stelt code aan slechts AEM auteur op
   + `ui.content` ingebed in  `/apps/my-app-packages/content/install` stelt inhoud en configuratie aan zowel AEM auteur als AEM publiceren op
   + `ui.content.publish` ingesloten in  `/apps/my-app-packages/content/install.publish` implementeert inhoud en configuratie alleen AEM publiceren

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-embeddeds) hieronder voor een volledig fragment.

### Filterdefinitie van containerpakket {#container-package-filter-definition}

Wegens het inbedden van de code en inhoudsubpakketten in het containerpakket, moeten de ingebedde doelwegen aan `filter.xml` van het containerproject worden toegevoegd om ervoor te zorgen de ingebedde pakketten in het containerpakket worden omvat wanneer gebouwd.

Voeg eenvoudig de `<filter root="/apps/<my-app>-packages"/>` ingangen voor om het even welke tweede niveauomslagen toe die subpakketten bevatten om op te stellen.

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-container-package-filters) hieronder voor een volledig fragment.

## Pakketten van derden insluiten {#embedding-3rd-party-packages}

Alle pakketten moeten beschikbaar zijn via de openbaar gemaakte gegevensopslagruimte voor artefacten](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) of via een toegankelijke openbare gegevensopslagruimte van derden waarnaar verwezen kan worden.[

Als de pakketten van derden zich in de **openbare Maven-artefactopslagplaats van Adobe** bevinden, is geen verdere configuratie nodig wanneer Adobe Cloud Manager de artefacten oplost.

Als de pakketten van derden zich in een **openbare Maven-artefactopslagplaats van derden** bevinden, moet deze opslagplaats worden geregistreerd in de `pom.xml` van het project en worden ingesloten volgens de [hierboven beschreven](#embeddeds) methode.

Toepassingen/connectors van derden moeten worden ingesloten met het `all`-pakket als een container in het containerpakket van uw project (`all`).

Als u Geweven afhankelijkheden toevoegt, volgt u de standaard Geweven werkwijzen en wordt het insluiten van artefacten van derden (code en inhoudspakketten) [hierboven geschetst](#embedding-3rd-party-packages).

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-3rd-party-maven-repositories) hieronder voor een volledig fragment.

## Afhankelijkheden tussen `ui.apps` van `ui.content` pakketten {#package-dependencies} verpakken

Om een correcte installatie van de pakketten te waarborgen, wordt aanbevolen om afhankelijkheden tussen pakketten tot stand te brengen.

De algemene regel is pakketten die veranderbare inhoud (`ui.content`) bevatten zouden van de onveranderlijke code (`ui.apps`) moeten afhangen die het teruggeven en het gebruik van de veranderlijke inhoud steunt.

Een opmerkelijke uitzondering op deze algemene regel is als het onveranderlijke codepakket (`ui.apps` of om het even welk ander), __only__ OSGi bundels bevat. Zo ja, dan zou geen AEM pakket een afhankelijkheid van het moeten verklaren. Dit is omdat de onveranderlijke codepakketten __only__ die bundels OSGi bevatten niet met AEM Manager van het Pakket worden geregistreerd, en daarom zal om het even welk AEM pakket afhankelijk van het een ontevreden gebiedsdeel hebben en niet om te installeren.

>[!TIP]
>
>Zie de sectie [POM XML-fragmenten](#xml-package-dependencies) hieronder voor een volledig fragment.

De gemeenschappelijke patronen voor tevreden pakketgebiedsdelen zijn:

### Eenvoudige implementatiepakketafhankelijke {#simple-deployment-package-dependencies}

Met de eenvoudige optie wordt het veranderbare inhoudspakket `ui.content` ingesteld op basis van het onveranderlijke codepakket `ui.apps`.

+ `all` heeft geen afhankelijkheden
   + `ui.apps` heeft geen afhankelijkheden
   + `ui.content` afhankelijk van  `ui.apps`

### Complexe implementatiepakketafhankelijkheden {#complex-deploxment-package-dependencies}

De complexe plaatsingen breiden zich op het eenvoudige geval uit, en plaatsen gebiedsdelen tussen de overeenkomstige veranderlijke inhoud en de onveranderlijke codepakketten. Zoals vereist, kunnen de gebiedsdelen ook tussen onveranderlijke codepakketten worden gevestigd.

+ `all` heeft geen afhankelijkheden
   + `common.ui.apps.common` heeft geen afhankelijkheden
   + `site-a.ui.apps` afhankelijk van  `common.ui.apps`
   + `site-a.ui.content` afhankelijk van  `site-a.ui.apps`
   + `site-b.ui.apps` afhankelijk van  `common.ui.apps`
   + `site-b.ui.content` afhankelijk van  `site-b.ui.apps`

## Lokale ontwikkeling en implementatie {#local-development-and-deployment}

De projectstructuren en -organisatie die in dit artikel worden beschreven, zijn **volledig compatibel** lokale AEM.

## XML-fragmenten voor POM {#pom-xml-snippets}

Het volgende is Gemaakt `pom.xml` configuratievluiven die aan Geweven projecten kunnen worden toegevoegd om aan de bovengenoemde aanbevelingen te richten.

### Pakkettypen {#xml-package-types}

Code- en contentpakketten die als subpakketten worden geïmplementeerd, moeten het pakkettype **applicatie** of **content** declareren, afhankelijk van wat ze bevatten.

#### Containerpakkettypen {#container-package-types}

Het project `all/pom.xml` van de container **declareert geen** a `<packageType>`.

#### Code (Immuable) pakkettypes {#immutable-package-types}

Codepakketten moeten hun `packageType` op `application` plaatsen.

In `ui.apps/pom.xml`, `<packageType>application</packageType>` bouwt configuratierichtlijnen van `filevault-package-maven-plugin` plugin verklaring verklaart zijn pakkettype.

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
        <name>my-app.ui.apps</name>
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

Inhoudspakketten moeten hun `packageType` instellen op `content`.

In `ui.content/pom.xml`, verklaart `<packageType>content</packageType>` de richtlijn van de bouwstijlconfiguratie van `filevault-package-maven-plugin` plugin verklaring zijn pakkettype.

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
        <name>my-app.ui.content</name>
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

In elk project dat een pakket genereert, **behalve** voor het containerproject (`all`), voegt u `<cloudManagerTarget>none</cloudManagerTarget>` aan de `<properties>`-configuratie van de declaratie van de invoegtoepassing `filevault-package-maven-plugin` toe om ervoor te zorgen dat deze **niet** door Adobe Cloud Manager worden geïmplementeerd. Het containerpakket (`all`) moet het enkelvoudige pakket zijn dat wordt geïmplementeerd via Cloud Manager, dat op zijn beurt alle vereiste code en inhoudspakketten insluit.

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

### Repo-inkt{#snippet-repo-init}

De manuscripten van de Inzet van de Repo die de manuscripten bevatten van de Inzet van de Repo worden bepaald in `RepositoryInitializer` OSGi fabrieksconfiguratie via het `scripts` bezit. Merk op dat aangezien deze manuscripten binnen configuraties OSGi worden bepaald, zij gemakkelijk kunnen worden scoped door wijze in werking stellen gebruikend de gebruikelijke `../config.<runmode>` omslagsemantiek.

Aangezien scripts doorgaans een declaratie van meerdere regels zijn, is het eenvoudiger om ze in het `.config`-bestand te definiëren dan de op JSON gebaseerde `.cfg.json`-indeling.

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

De eigenschap `scripts` OSGi bevat instructies zoals gedefinieerd door de Repo Init language](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language) van [Apache Sling&#39;s.

### Structuurpakket opslagplaats {#xml-repository-structure-package}

Voeg in `ui.apps/pom.xml` en elke andere `pom.xml` die een codepakket (`<packageType>application</packageType>`) declareert, de volgende configuratie van het opslagstructuurpakket toe aan de FileVault Maven-plug-in. U kunt [uw eigen opslagstructuurpakket maken voor uw project](repository-structure-package.md).

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

Voeg in de `all/pom.xml` de volgende `<embeddeds>` aanwijzingen toe aan de `filevault-package-maven-plugin` plug-indeclaratie. **gebruik niet** de `<subPackages>` configuratie, aangezien dit de subpakketten in `/etc/packages` eerder dan `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?` zal omvatten.

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

          <!-- OSGi Bundle Jar file that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.core</artifactId>
              <type>jar</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

          <!-- Code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.apps</artifactId>
              <type>zip</type>
              <target>/apps/my-app-packages/application/install</target>
          </embedded>

           <!-- OSGi configuration code package that deploys to BOTH AEM Author and AEM Publish -->
          <embedded>
              <groupId>${project.groupId}</groupId>
              <artifactId>my-app.ui.config</artifactId>
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

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
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
>
>Als u meer Maven-opslagruimten toevoegt, kunnen de gefabriceerde buildtijden langer duren omdat extra Maven-opslagruimten op afhankelijkheden worden gecontroleerd.

Voeg in de `pom.xml` van het reactorproject de noodzakelijke richtlijnen toe van de derde partij van de openbare Maven bewaarplaats. De volledige `<repository>` configuratie zou bij de leverancier van de derdebewaarplaats beschikbaar moeten zijn.

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

### Afhankelijkheden tussen `ui.apps` van `ui.content` pakketten {#xml-package-dependencies} verpakken

Voeg in de `ui.content/pom.xml` de volgende `<dependencies>` aanwijzingen toe aan de `filevault-package-maven-plugin` plug-indeclaratie.

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

### De doelmap van het containerproject {#xml-clean-container-package} reinigen

Voeg in `all/pom.xml` de `maven-clean-plugin` plug-in toe waarmee de doelmap wordt gewist voordat een Maven-versie wordt gemaakt.

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

+ [Pakketten beheren met Maven](/help/implementing/developing/tools/maven-plugin.md)
+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](http://jackrabbit.apache.org/filevault-package-maven-plugin/)
