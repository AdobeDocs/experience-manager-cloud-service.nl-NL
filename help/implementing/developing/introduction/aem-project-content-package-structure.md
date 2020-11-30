---
title: AEM-projectstructuur
description: Leer hoe u pakketstructuren definieert voor implementatie op Adobe Experience Manager Cloud Service.
translation-type: tm+mt
source-git-commit: 1a282bdaca02f47d7936222da8522e74831a4572
workflow-type: tm+mt
source-wordcount: '2828'
ht-degree: 13%

---


# AEM-projectstructuur

>[!TIP]
>
>U kunt uzelf vertrouwd maken met het standaardgebruik [van](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/archetype/overview.html)AEM Project Archetype en de [FileVault Content Maven-plug-in](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/vlt-mavenplugin.html) , aangezien dit artikel voortbouwt op deze lessen en concepten.

Dit artikel beschrijft de veranderingen die aan Adobe Experience Manager Maven projecten worden vereist om als Cloud Service compatibel te worden AEM door ervoor te zorgen dat zij de splitsing van veranderbare en onveranderlijke inhoud eerbiedigen, gebiedsdelen worden gevestigd om niet-strijdige, deterministische plaatsingen tot stand te brengen en dat zij in een plaatsingsable structuur worden verpakt.

AEM toepassingsimplementaties moeten bestaan uit één AEM. Dit pakket dient op zijn beurt subpakketten te bevatten die alles omvatten wat door de toepassing wordt vereist om te functioneren, met inbegrip van code, configuratie en om het even welke ondersteunende basislijninhoud.

AEM vereist een scheiding van **content** en **code**, wat betekent dat één enkel contentpakket **niet kan** worden geïmplementeerd op **zowel** `/apps` als tijdens runtime beschrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home` of iets anders dan `/apps`) van de opslagplaats. In plaats daarvan moet de applicatie code en content scheiden in afzonderlijke pakketten voor implementatie in AEM.

De pakketstructuur die in dit document wordt beschreven, is compatibel met **zowel** lokale ontwikkelingsimplementaties als AEM Cloud Service-implementaties.

>[!TIP]
>
>De configuraties die in dit document worden beschreven, worden geleverd door [AEM Project Maven Archetype 24 of hoger](https://github.com/adobe/aem-project-archetype/releases).

## Mutable versus Immuable Areas of the Repository {#mutable-vs-immutable}

`/apps` en `/libs`**worden beschouwd als onveranderbare gebieden van AEM omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dat wil zeggen tijdens runtime).** Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

Everything else in the repository, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc. are all **mutable** areas, meaning they can be changed at runtime.

>[!WARNING]
>
>Zoals in vorige versies van AEM, `/libs` zou niet moeten worden gewijzigd. Alleen AEM productcode kan worden geïmplementeerd op `/libs`.

### eiken indexen {#oak-indexes}

De indexen van de eiken (`/oak:index`) worden specifiek beheerd door de AEM als proces van de Cloud Service plaatsing. De reden hiervoor is dat de Cloud Manager moet wachten totdat een nieuwe index wordt geïmplementeerd en volledig opnieuw wordt geïndexeerd voordat naar de nieuwe codeafbeelding wordt overgeschakeld.

Daarom, hoewel de indexen van de eiken in runtime veranderbaar zijn, moeten zij als code worden opgesteld zodat zij kunnen worden geïnstalleerd alvorens om het even welke veranderlijke pakketten worden geïnstalleerd. Daarom maken `/oak:index` configuraties deel uit van het codepakket en geen deel uit van het inhoudspakket [zoals hieronder](#recommended-package-structure)beschreven.

>[!TIP]
>
>Meer informatie over indexering in AEM als Cloud Service vindt u in [Inhoud van document zoeken en indexeren](/help/operations/indexing.md).

## Aanbevolen pakketstructuur {#recommended-package-structure}

![Experience Manager projectpakketstructuur](assets/content-package-organization.png)

Dit diagram verstrekt een overzicht van de geadviseerde projectstructuur en pakketplaatsingsartefacten.

De aanbevolen implementatiestructuur voor toepassingen is als volgt:

### Codepakketten / OSGi-bundels

+ Het Jar-bestand van de bundel OSGi wordt gegenereerd en rechtstreeks ingesloten in het hele project.

+ Het `ui.apps` pakket bevat alle code die moet worden opgesteld en slechts aan `/apps`. Gemeenschappelijke elementen van het `ui.apps` pakket zijn onder meer:
   + [Componentdefinities en HTML](https://docs.adobe.com/content/help/en/experience-manager-htl/using/overview.html) -scripts
      + `/apps/my-app/components`
   + JavaScript en CSS (via [clientbibliotheken](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [Bedekkingen](/help/implementing/developing/introduction/overlays.md) van `/libs`
      + `/apps/cq`, `/apps/dam/`enz.
   + Contextbewuste configuraties voor alternatieven
      + `/apps/settings`
   + ACLs (toestemmingen)
      + Willekeurig pad `rep:policy` onder `/apps`

+ Het `ui.config` pakket, bevat alle [configuraties](/help/implementing/deploying/configuring-osgi.md)OSGi:
   + De omslag van de organisatie die loopwijze specifieke definities OSGi config bevat
      + `/apps/my-app/osgiconfig`
   + Gemeenschappelijke OSGi configuratiemap die standaardOSGi configuraties bevat die op al doel AEM als doelstellingen van de Cloud Service plaatsing van toepassing zijn
      + `/apps/my-app/osgiconfig/config`
   + De wijze-specifieke OSGi configuratiemappen van de looppas die standaardOSGi configuraties bevat die op alle AEM als doelstellingen van de Cloud Service plaatsing van toepassing zijn
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi-configuratiescripts
      + [Repo Init](#repo-init) is de aanbevolen manier om (muteerbare) inhoud te implementeren die logisch deel uitmaakt van de AEM toepassing. De configuraties van OSGi van het Punt van de Repo zouden in de aangewezen `config.<runmode>` omslag moeten worden geplaatst zoals hierboven geschetst, en zouden moeten worden gebruikt om te bepalen:
         + Structuren voor basislijninhoud
         + Gebruikers
         + Servicegebruikers
         + Groepen
         + ACLs (toestemmingen)

### Inhoudspakketten

+ Het `ui.content` pakket bevat alle inhoud en configuratie. Het inhoudspakket bevat alle knoopdefinities die niet in de `ui.apps` pakketten of `ui.config` pakketten staan, of met andere woorden niets in `/apps` of `/oak:index`. Gemeenschappelijke elementen van het `ui.content` pakket zijn onder meer:
   + Contextbewuste configuraties
      + `/conf`
   + Vereiste, complexe inhoudsstructuren (d.w.z. De bouwstijl van de inhoud die voortbouwt op en zich voorbij de de inhoudsstructuren van de Basislijn uitbreidt die in Repo worden bepaald.)
      + `/content`, `/content/dam`enz.
   + Regelgevende taggende taxonomieën
      + `/content/cq:tags`
   + Verouderde knooppunten, enz. (idealiter migreren deze naar locaties die niet- of etc. zijn)
      + `/etc`

### Containerpakketten

+ Het `all` pakket is een containerpakket dat ALLEEN inzetbare artefacten, het SGI-bundel Jar-bestand `ui.apps`en `ui.config` `ui.content` pakketten als insluitingen bevat. The `all` package must not have **any content or code** of its own, but rather delegate all deployment to the repository to its sub-packages or OSGi bundle Jar files.

   Pakketten worden nu opgenomen met de insluitconfiguratie [van de Maven](#embeddeds)FileVault-plug-in voor Maven-bestanden in plaats van met de `<subPackages>` configuratie.

   Voor complexe plaatsingen van de Experience Manager, kan het wenselijk zijn om veelvoudige `ui.apps`, `ui.config` en `ui.content` projecten/pakketten tot stand te brengen die specifieke plaatsen of huurders in AEM vertegenwoordigen. Als dit wordt gedaan, zorg ervoor de scheiding tussen veranderlijke en onveranderlijke inhoud wordt geëerbiedigd, en de vereiste inhoudspakketten en de bundel OSGi Jar dossiers worden ingebed als subpakketten in het pakket van de `all` containerinhoud.

   Bijvoorbeeld, zou een complexe het pakketstructuur van de plaatsingsinhoud als dit kunnen kijken:

   + `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
      + `common.ui.apps` implementeert code die vereist is voor **zowel** site A als site B
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

+ Containerpakketten moeten hun `packageType` waarde instellen op `container`.
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

Terwijl de manuscripten van het Begin van de Repo in het `ui.config` project zelf als manuscripten leven, kunnen en moeten zij worden gebruikt om de volgende veranderbare structuren te bepalen:

+ Structuren voor basislijninhoud
+ Servicegebruikers
+ Gebruikers
+ Groepen
+ ACLs

De manuscripten van de Inzet van de Repo worden opgeslagen als `scripts` ingangen van `RepositoryInitializer` OSGi fabrieksconfiguraties, en kunnen daarom impliciet door looppas worden gericht wijze, die voor verschillen tussen de manuscripten van de Inzet van de Auteur AEM en van de Diensten van de Publicatie AEM, of zelfs tussen milieu&#39;s (Dev, Stadium en Prod) toestaat.

Repo Init OSGi vormt best geschreven in het [`.config` OSGi configuratieformaat](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) aangezien zij multi-lines steunen, die een uitzondering op de beste praktijken is om te gebruiken [`.cfg.json` om configuraties](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1)te bepalen OSGi.

Merk op dat wanneer het bepalen van Gebruikers, en Groepen, slechts groepen als deel van de toepassing worden beschouwd, en integraal aan zijn functie zou hier moeten worden bepaald. De gebruikers en de Groepen van de organisatie zouden nog bij runtime in AEM moeten worden bepaald; Bijvoorbeeld, als een douanewerkschema werk aan een genoemde Groep toewijst, zou die Groep binnen via RepoInit in de AEM toepassing moeten worden bepaald, echter als de Groepering slechts organisatorisch is, zoals &quot;Team van Wendy&quot;en &quot;Team van Sean&quot;, zijn deze het best bepaald, en beheerd bij runtime in AEM.

>[!TIP]
>
>Scripts voor herhalingsindelingen *moeten* in het inlineveld worden gedefinieerd en de `scripts` `references` configuratie werkt niet.

De volledige woordenlijst voor scripts van Repo Init is beschikbaar in de documentatie [van](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language)Apache Sling Repo Init.

>[!TIP]
>
>Zie de sectie [Repo Init Snippets](#snippet-repo-init) hieronder voor een volledig fragment.

## Structuurpakket opslagplaats {#repository-structure-package}

Codepakketten vereisen dat de configuratie van de FileVault Maven-plug-in wordt geconfigureerd om te verwijzen naar een `<repositoryStructurePackage>` methode die de juistheid van structurele afhankelijkheden afdwingt (om ervoor te zorgen dat een codepakket niet boven een ander codepakket wordt geïnstalleerd). U kunt uw eigen structuurpakket voor de gegevensopslagruimte [maken voor uw project](repository-structure-package.md).

Dit is **alleen vereist** voor codepakketten. (Dit zijn pakketten die zijn gemarkeerd met `<packageType>application</packageType>`.)

Zie Een structuurpakket voor opslagplaatsen [ontwikkelen voor meer informatie over het maken van een pakket](repository-structure-package.md)met opslagplaatsen voor uw toepassing.

Voor inhoudspakketten (`<packageType>content</packageType>`) is dit &#39;opslagplaatsstructuurpakket&#39; **niet** vereist.

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-repository-structure-package) voor POM hieronder voor een volledig fragment.

## Subpakketten insluiten in het Containerpakket{#embeddeds}

Inhoud- of codepakketten worden in een speciale map &quot;side-car&quot; geplaatst en kunnen worden geïnstalleerd op AEM auteur, AEM publicatie of beide met behulp van de `<embeddeds>` configuratie van de FileVault Maven-plug-in. Merk op dat de `<subPackages>` configuratie niet zou moeten worden gebruikt.

Veelvoorkomende gebruiksgevallen zijn:

+ ACLs/toestemmingen die tussen AEM auteursgebruikers en AEM publicatiegebruikers verschillen
+ Configuraties die alleen worden gebruikt ter ondersteuning van activiteiten van AEM auteur
+ Code zoals integratie met back-office systemen, die alleen vereist is voor AEM auteur

![Pakketten insluiten](assets/embeddeds.png)

Als u AEM auteur als doel wilt instellen, AEM publiceren of beide, wordt het pakket ingesloten in het `all` containerpakket in een speciale map-locatie, in de volgende indeling:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

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
   `application`, `content` of `container`
   + De `application` map bevat codepakketten
   + De `content` map bevat inhoudspakketten
   + De `container` map bevat eventuele [extra toepassingspakketten](#extra-application-packages) die mogelijk door de AEM worden opgenomen.
Deze mapnaam komt overeen met de [pakkettypen](#package-types) van de pakketten die erin staan.
+ De map op het vierde niveau bevat de subpakketten en moet een van de volgende zijn:
   + `install` om te installeren op **zowel** de AEM-auteur als de AEM-publicatie
   + `install.author` om **alleen** te installeren op de AEM-auteur
   + `install.publish` om **alleen** te installeren op AEM publishOpmerking: alleen `install.author` en `install.publish` worden ondersteunde doelen gebruikt. Andere uitvoermodi **worden niet** ondersteund.

Een implementatie die AEM auteur bevat en specifieke pakketten publiceert, kan er bijvoorbeeld als volgt uitzien:

+ `all` Containerpakket sluit de volgende pakketten in om een enkelvoudig implementatieartefact te maken
   + `ui.apps` ingebed in `/apps/my-app-packages/application/install` stelt code aan zowel AEM auteur als AEM publiceren op
   + `ui.apps.author` ingebed in `/apps/my-app-packages/application/install.author` stelt code aan slechts AEM auteur op
   + `ui.content` ingebed in `/apps/my-app-packages/content/install` stelt inhoud en configuratie aan zowel AEM auteur als AEM publiceren op
   + `ui.content.publish` ingesloten in `/apps/my-app-packages/content/install.publish` implementeert inhoud en configuratie alleen om te AEM publiceren

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

Alle pakketten moeten beschikbaar zijn via de gegevensopslagruimte van [Adobe of via een openbare gegevensopslagplaats](https://repo.adobe.com/nexus/content/groups/public/com/adobe/) voor artefacten van derden.

Als de pakketten van derden zich in de **openbare Maven-artefactopslagplaats van Adobe** bevinden, is geen verdere configuratie nodig wanneer Adobe Cloud Manager de artefacten oplost.

Als de pakketten van derden zich in een **openbare Maven-artefactopslagplaats van derden** bevinden, moet deze opslagplaats worden geregistreerd in de `pom.xml` van het project en worden ingesloten volgens de [hierboven beschreven](#embeddeds) methode.

Toepassingen/connectors van derden moeten worden ingesloten met het bijbehorende `all` pakket als een container in het containerpakket (`all`) van uw project.

Het toevoegen van Geweven gebiedsdelen volgt standaard Geweven praktijken, en het inbedden van derdeartefacten (code en inhoudspakketten) worden [geschetst hierboven](#embedding-3rd-party-packages).

>[!TIP]
>
>Zie de [sectie XML-fragmenten](#xml-3rd-party-maven-repositories) voor POM hieronder voor een volledig fragment.

## Afhankelijkheden tussen pakketten `ui.apps` van `ui.content` pakketten {#package-dependencies}

Om een correcte installatie van de pakketten te waarborgen, wordt aanbevolen om afhankelijkheden tussen pakketten tot stand te brengen.

De algemene regel is pakketten met veranderbare inhoud (`ui.content`) die afhankelijk moeten zijn van de onveranderlijke code (`ui.apps`) die het teruggeven en het gebruik van de veranderlijke inhoud steunt.

Een opmerkelijke uitzondering op deze algemene regel is als het onveranderlijke codepakket (`ui.apps` of een ander), __slechts__ bundels OSGi bevat. Zo ja, dan zou geen AEM pakket een afhankelijkheid van het moeten verklaren. Dit is omdat de onveranderlijke codepakketten __slechts__ die OSGi- bundels bevatten niet bij AEM Manager van het Pakket worden geregistreerd, en daarom om het even welk AEM pakket afhankelijk van het een ontevreden gebiedsdeel zal hebben en zal niet installeren.

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
   + `common.ui.apps.common` heeft geen afhankelijkheden
   + `site-a.ui.apps` afhankelijk van `common.ui.apps`
   + `site-a.ui.content` afhankelijk van `site-a.ui.apps`
   + `site-b.ui.apps` afhankelijk van `common.ui.apps`
   + `site-b.ui.content` afhankelijk van `site-b.ui.apps`

## Lokale ontwikkeling en implementatie {#local-development-and-deployment}

De in dit artikel geschetste projectstructuren en -organisatie zijn **volledig verenigbaar** met de plaatselijke ontwikkeling AEM instanties.

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

In elk project dat een pakket genereert, **behalve** voor het containerproject (`all`), voegt u `<cloudManagerTarget>none</cloudManagerTarget>` aan de `<properties>`-configuratie van de declaratie van de invoegtoepassing `filevault-package-maven-plugin` toe om ervoor te zorgen dat deze **niet** door Adobe Cloud Manager worden geïmplementeerd. The container (`all`) package should be the singular package deployed via Cloud Manager, which in turn embeds all required code and content packages.

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

Scripts voor Repo Init die de scripts voor Repo Init bevatten, worden gedefinieerd in de `RepositoryInitializer` OSGi-fabrieksconfiguratie via de `scripts` eigenschap. Merk op dat aangezien deze manuscripten binnen configuraties OSGi worden bepaald, zij gemakkelijk kunnen zijn scoped door wijze gebruikend de gebruikelijke `../config.<runmode>` omslagsemantiek.

Aangezien scripts doorgaans een declaratie met meerdere regels zijn, is het gemakkelijker om ze in het `.config` bestand te definiëren dan in de op JSON gebaseerde `.cfg.json` indeling.

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

Voeg in de `ui.apps/pom.xml` en een andere `pom.xml` code die een codepakket (`<packageType>application</packageType>`) declareert, de volgende configuratie van het opslagplaatsstructuurpakket toe aan de FileVault Maven-plug-in. U kunt uw eigen structuurpakket voor de gegevensopslagruimte [maken voor uw project](repository-structure-package.md).

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

Voeg in de `all/pom.xml`sectie de volgende `<embeddeds>` instructies toe aan de `filevault-package-maven-plugin` insteekmoduledeclaratie. Herinner me, **gebruik niet** de `<subPackages>` configuratie, aangezien dit subpakketten in `/etc/packages` plaats van `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`zal omvatten.

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

Voeg in het reactorproject `pom.xml`de noodzakelijke richtlijnen van derden inzake openbare opslagplaats Maven toe. De volledige `<repository>` configuratie moet beschikbaar zijn bij de externe opslagprovider.

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