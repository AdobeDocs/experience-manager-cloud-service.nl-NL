---
title: AEM projectstructuur
description: Leer hoe u pakketstructuren definieert voor implementatie op Adobe Experience Manager Cloud Service.
exl-id: 38f05723-5dad-417f-81ed-78a09880512a
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2859'
ht-degree: 3%

---

# AEM projectstructuur

>[!TIP]
>
>U vertrouwd maken met de basisbeginselen [Gebruik van Project Archetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)en de [Insteekmodule FileVault Content Maven](/help/implementing/developing/tools/maven-plugin.md) aangezien dit artikel op deze lessen en concepten voortbouwt.

In dit artikel worden de wijzigingen beschreven die nodig zijn om projecten van Adobe Experience Manager Maven as a Cloud Service AEM te maken door ervoor te zorgen dat ze de opsplitsing van muteerbare en onveranderlijke inhoud respecteren. Ook, worden de gebiedsdelen gevestigd om niet-strijdige, deterministische plaatsingen tot stand te brengen, en zij worden verpakt in een plaatsbare structuur.

AEM toepassingsimplementaties moeten bestaan uit één AEM. Dit pakket moet op zijn beurt subpakketten bevatten die alles bevatten wat door de toepassing wordt vereist om te functioneren, met inbegrip van code, configuratie, en om het even welke ondersteunende basislijninhoud.

AEM vereist een scheiding van **content** en **code**, wat betekent dat er één inhoudspakket is **kan** implementeren voor **beide** `/apps` en runtime-schrijfbare gebieden (bijvoorbeeld `/content`, `/conf`, `/home`of iets anders `/apps`) van de gegevensopslagruimte. In plaats daarvan moet de applicatie code en content scheiden in afzonderlijke pakketten voor implementatie in AEM.

De pakketstructuur die in dit document wordt beschreven, is compatibel met **zowel** lokale ontwikkelingsimplementaties als AEM Cloud Service-implementaties.

>[!TIP]
>
>De configuraties die in dit document worden beschreven, worden geleverd door [AEM Project Maven Archetype 24 of hoger](https://github.com/adobe/aem-project-archetype/releases).

## Mutable versus Immuable Areas of the Repository {#mutable-vs-immutable}

De `/apps` en `/libs` AEM **onaantastbaar** omdat deze niet kunnen worden gewijzigd (maken, bijwerken, verwijderen) nadat AEM is gestart (dus bij uitvoering). Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, mislukt.

Alle andere gegevens in de opslagplaats, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, enzovoort, zijn allemaal **muteerbaar** gebieden, wat betekent dat deze tijdens runtime kunnen worden gewijzigd.

>[!WARNING]
>
>Zoals in vorige versies van AEM, `/libs` mogen niet worden gewijzigd. Alleen AEM productcode kan worden geïmplementeerd op `/libs`.

### eiken indexen {#oak-indexes}

Eik-indexen (`/oak:index`) worden beheerd door het AEM as a Cloud Service implementatieproces. De reden hiervoor is dat de Cloud Manager moet wachten tot een nieuwe index is geïmplementeerd en volledig opnieuw is gedexeerd voordat wordt overgeschakeld naar de nieuwe codeafbeelding.

Daarom, hoewel de indexen van de eiken in runtime veranderbaar zijn, moeten zij als code worden opgesteld zodat zij kunnen worden geïnstalleerd alvorens om het even welke veranderlijke pakketten worden geïnstalleerd. Daarom `/oak:index` configuraties maken deel uit van het codepakket en maken geen deel uit van het inhoudspakket [zoals hieronder beschreven](#recommended-package-structure).

>[!TIP]
>
>Voor meer details over het indexeren in AEM as a Cloud Service, zie [Inhoud zoeken en indexeren](/help/operations/indexing.md).

## Aanbevolen pakketstructuur {#recommended-package-structure}

![Experience Manager projectpakketstructuur](assets/content-package-organization.png)

Dit diagram verstrekt een overzicht van de geadviseerde projectstructuur en pakketplaatsingsartefacten.

De aanbevolen implementatiestructuur voor toepassingen is als volgt:

### Codepakketten / OSGi-pakketten

+ Het Jar-bestand van de bundel OSGi wordt gegenereerd en rechtstreeks ingesloten in het hele project.

+ De `ui.apps` pakket bevat alle code die moet worden geïmplementeerd en alleen wordt geïmplementeerd op `/apps`. Gemeenschappelijke elementen van de `ui.apps` pakket omvat , maar is niet beperkt tot :
   + [Componentdefinities en HTML](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) scripts
      + `/apps/my-app/components`
   + JavaScript en CSS (via [Clientbibliotheken](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [Bedekkingen](/help/implementing/developing/introduction/overlays.md) van `/libs`
      + `/apps/cq`, `/apps/dam/`, enzovoort.
   + Contextbewuste configuraties voor alternatieven
      + `/apps/settings`
   + ACLs (toestemmingen)
      + Alle `rep:policy` voor elk pad onder `/apps`
   + [Vooraf gecompileerde gebundelde scripts](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/precompiled-bundled-scripts.html)

>[!NOTE]
>
>Dezelfde code moet in alle omgevingen worden geïmplementeerd. Deze code garandeert een zeker betrouwbaarheidsniveau dat validaties in de werkgebiedomgeving ook in productie zijn. Zie de sectie over [Runmodi](/help/implementing/deploying/overview.md#runmodes).


### Inhoud-pakketten

+ De `ui.content` bevat alle inhoud en configuratie. Het inhoudspakket bevat alle knoopdefinities die niet in het dialoogvenster `ui.apps` of `ui.config` pakketten, met andere woorden alles wat zich niet in `/apps` of `/oak:index`. Gemeenschappelijke elementen van de `ui.content` pakket omvat , maar is niet beperkt tot :
   + Contextbewuste configuraties
      + `/conf`
   + Vereiste, complexe inhoudsstructuren (dat wil zeggen: de opbouw van inhoud die voortbouwt op en zich uitbreidt tot voorbij de basislijninhoudsstructuren die zijn gedefinieerd in Repo Init.)
      + `/content`, `/content/dam`, enzovoort.
   + Regelgevende taggende taxonomieën
      + `/content/cq:tags`
   + Verouderde knooppunten enz. (idealiter migreren deze knooppunten naar locaties buiten/enz.)
      + `/etc`

### Containerpakketten

+ De `all` pakket is een containerpakket dat ALLEEN inzetbare artefacten, het SGI-bundelJar-bestand, bevat. `ui.apps`, `ui.config`, en `ui.content` pakketten als insluitingen. De `all` pakket mag niet **enige inhoud of code** van zijn eigen, maar delegeer eerder al plaatsing aan de bewaarplaats aan zijn subpackages of OSGi bundel Jar dossiers.

  De pakketten zijn nu inbegrepen gebruikend Maven [Ingesloten configuratie van FileVault-pakket met Maven-plug-in](#embeddeds), in plaats van de `<subPackages>` configuratie.

  Voor complexe plaatsingen van de Experience Manager, kan het wenselijk zijn om veelvoudige te creëren `ui.apps`, `ui.config`, en `ui.content` projecten/pakketten die specifieke sites of huurders in AEM vertegenwoordigen. Als deze aanpak wordt toegepast, moet u ervoor zorgen dat de splitsing tussen muteerbare en onveranderlijke inhoud wordt gerespecteerd en moeten de vereiste inhoudspakketten en de OSGi-bundel Jar-bestanden als subpakketten worden ingesloten in de `all` containerinhoudspakket.

  Bijvoorbeeld, zou een complexe het pakketstructuur van de plaatsingsinhoud als dit kunnen kijken:

   + `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
      + `common.ui.apps` implementeert code die vereist is door **beide** site A en site B
      + `site-a.core` OSGi-bundel Jar vereist voor site A
      + `site-a.ui.apps` implementeert code die door site A wordt vereist
      + `site-a.ui.config` stelt configuraties OSGi op die door Plaats A worden vereist
      + `site-a.ui.content` stelt inhoud en configuratie op die door plaats A worden vereist
      + `site-b.core` OSGi-bundel Jar vereist voor site B
      + `site-b.ui.apps` implementeert code die vereist is voor site B
      + `site-b.ui.config` stelt configuraties OSGi op die door plaats B worden vereist
      + `site-b.ui.content` stelt inhoud en configuratie op die door plaats B worden vereist

+ De `ui.config` pakket bevat alle [OSGi-configuraties](/help/implementing/deploying/configuring-osgi.md):
   + Beschouw als code en behoort tot OSGi-bundels, maar bevat geen standaardinhoudsknooppunten. Het is dus gemarkeerd als een containerpakket
   + De omslag van de organisatie die loopwijze-specifieke definities OSGi config bevat
      + `/apps/my-app/osgiconfig`
   + Gemeenschappelijke OSGi configuratiemap die standaardOSGi configuraties bevat die op al doel AEM as a Cloud Service plaatsingsdoelstellingen van toepassing zijn
      + `/apps/my-app/osgiconfig/config`
   + De wijze-specifieke OSGi configuratiemappen van de looppas die standaardOSGi configuraties bevatten die op al doel AEM as a Cloud Service plaatsingsdoelstellingen van toepassing zijn
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi-configuratiescripts
      + [Reparatie-item](#repo-init) is de geadviseerde manier om (veranderbare) inhoud op te stellen die logisch gezien deel van de AEM toepassing uitmaakt. De OSGi-configuraties van de Repo-installatie moeten op de juiste plaats zijn `config.<runmode>` map als hierboven beschreven, en wordt gebruikt voor het definiëren van:
         + Basislijninhoudsstructuren
         + Gebruikers
         + Servicegebruikers
         + Groepen
         + ACLs (toestemmingen)

### Extra toepassingspakketten{#extra-application-packages}

Als andere AEM Projecten - die zelf uit hun eigen code en inhoudspakketten bestaan - door de AEM plaatsing worden gebruikt, zouden hun containerpakketten in het project moeten worden ingebed `all` pakket.

Bijvoorbeeld, zou een AEM project dat twee verkoper AEM toepassingen omvat als kunnen kijken:

+ `all` met het inhoudspakket worden de volgende pakketten ingesloten om een unieke implementatie-artefact te maken
   + `core` OSGi bundle Jar vereist door de AEM toepassing
   + `ui.apps` implementeert code die vereist is voor de AEM toepassing
   + `ui.config` stelt configuraties OSGi op die door de AEM toepassing worden vereist
   + `ui.content` stelt inhoud en configuratie op die door de AEM toepassing worden vereist
   + `vendor-x.all` implementeert alles (code en inhoud) dat vereist is door de X-toepassing van de leverancier
   + `vendor-y.all` stelt alles (code en inhoud) op die door de verkoperY toepassing wordt vereist

## Pakkettypen {#package-types}

Pakketten moeten worden gemarkeerd met het opgegeven pakkettype. De types van pakket helpen het doel en de plaatsing van een pakket verduidelijken.

+ Containerpakketten moeten hun `packageType` tot `container`. Containerpakketten mogen geen normale knooppunten bevatten. Alleen OSGi-bundels, -configuraties en -subpakketten zijn toegestaan. Containers in AEM as a Cloud Service mogen niet worden gebruikt [installatiekoppels](https://jackrabbit.apache.org/filevault/installhooks.html).
+ Codepakketten (onveranderbaar) moeten hun `packageType` tot `application`.
+ In inhoudspakketten moeten de inhoud (mutable) `packageType` tot `content`.


Zie voor meer informatie [Apache Jackrabbit FileVault - PakketMaven Plugin-documentatie](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType), [Apache Jackrabbit-pakkettypen](https://jackrabbit.apache.org/filevault/packagetypes.html)en de [FileVault Maven-configuratiefragment](#marking-packages-for-deployment-by-adoube-cloud-manager) hieronder.

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-package-types) hieronder voor een volledig fragment.

## Pakketten markeren voor implementatie door Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Adobe Cloud Manager verzamelt standaard alle pakketten die door de Maven-build zijn gemaakt. Maar omdat de container (`all`) is het unieke implementatieartefact dat alle code- en inhoudspakketten bevat. **alleen** de container (`all`) wordt geïmplementeerd. Om dit te garanderen moeten andere pakketten die de Maven-build genereert, zijn gemarkeerd met de configuratie voor de FileVault Content Package Maven-invoegtoepassing van `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#pom-xml-snippets) hieronder voor een volledig fragment.

## Reparatie-item{#repo-init}

Repo Init verstrekt instructies, of manuscripten, die structuren JCR, die zich van gemeenschappelijke knoopstructuren zoals omslagbomen, aan gebruikers, de dienstgebruiker, groepen, en ACL definitie uitstrekken bepalen.

De belangrijkste voordelen van Repo Init zijn zij impliciete toestemmingen hebben om alle acties uit te voeren die door hun manuscripten worden bepaald. En, worden dergelijke manuscripten aangehaald vroeg in de plaatsingslevenscyclus die ervoor zorgt dat alle vereiste structuren JCR tegen de tijdcode bestaan in werking wordt gesteld.

Terwijl de manuscripten van het Begin van de Repo zelf in `ui.config` Als scripts gebruiken, kunnen en moeten ze worden gebruikt om de volgende veranderbare structuren te definiëren:

+ Basislijninhoudsstructuren
+ Servicegebruikers
+ Gebruikers
+ Groepen
+ ACLs

Scripts voor herhalen van indelingen worden opgeslagen als `scripts` vermeldingen van `RepositoryInitializer` OSGi-fabrieksconfiguraties. Als dusdanig, kunnen zij impliciet door looppaswijze worden gericht, die voor verschillen tussen AEM Auteur en AEM de manuscripten van de Repo van de Diensten van de Publicatie, of zelfs tussen milieu&#39;s (Dev, Stadium, en Prod) toestaat.

Reparatie-Init OSGi-configuraties worden het beste geschreven in het dialoogvenster [`.config` OSGi-configuratie](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) aangezien zij multilines steunen, die een uitzondering op de beste praktijken van het gebruiken is [`.cfg.json` om OSGi configuraties te bepalen](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

Wanneer het bepalen van Gebruikers, en Groepen, slechts worden de groepen beschouwd als deel van de toepassing, en integraal aan zijn functie. U definieert bij uitvoering nog steeds Organisatiegebruikers en -groepen in AEM. Als een aangepaste workflow bijvoorbeeld werk toewijst aan een benoemde groep, definieert u die groep als repo-item in de AEM toepassing. Nochtans, als de Groepering slechts organisatorisch, zoals &quot;Team van Wendy&quot;en &quot;Team van Sean&quot;is, worden deze groepen het best bepaald en geleid bij runtime in AEM.

>[!TIP]
>
>Scripts voor herhalen *moet* worden gedefinieerd in de inline `scripts` of de `references` configuratie werkt niet.

De volledige woordenlijst voor scripts van Repo Init is beschikbaar op het tabblad [Apache Sling Repo Init-documentatie](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>Zie de [Fragmenten herhalen](#snippet-repo-init) hieronder voor een volledig fragment.

## Structuurpakket opslagplaats {#repository-structure-package}

Codepakketten vereisen dat de configuratie van de FileVault Maven-plug-in wordt geconfigureerd voor verwijzing naar een `<repositoryStructurePackage>` die de juistheid van structurele gebiedsdelen afdwingt (om ervoor te zorgen dat één codepakket niet over een andere installeert). U kunt [zelf een opslagstructuurpakket voor uw project maken](repository-structure-package.md).

**Alleen vereist** voor codepakketten: pakketten gemarkeerd met `<packageType>application</packageType>`.

Ga voor meer informatie over het maken van een opslagplaatsstructuurpakket voor uw toepassing naar [Een structuurpakket voor opslagplaats ontwikkelen](repository-structure-package.md).

Inhoudspakketten (`<packageType>content</packageType>`) **niet** vereist dit &#39;repository structure Package&#39;.

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-repository-structure-package) hieronder voor een volledig fragment.

## Subpakketten insluiten in het Containerpakket{#embeddeds}

Inhoud- of codepakketten worden in een speciale map &quot;side-car&quot; geplaatst en kunnen worden geïnstalleerd op AEM auteur, AEM publicatie of beide met de FileVault Maven-plug-in `<embeddeds>` configuratie. Gebruik de `<subPackages>` configuratie.

Veelvoorkomende gebruiksgevallen zijn:

+ ACLs/toestemmingen die tussen AEM auteursgebruikers en AEM publicatiegebruikers verschillen
+ Configuraties die alleen worden gebruikt ter ondersteuning van activiteiten van AEM auteur
+ Code zoals integratie met back-office systemen, die alleen vereist is voor AEM auteur

![Pakketten insluiten](assets/embeddeds.png)

Als u AEM auteur als doel wilt instellen, AEM publiceert of beide, wordt het pakket ingesloten in het `all` containerpakket in een speciale map-locatie, in de volgende indeling:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

Deze mapstructuur indelen:

+ De map op het eerste niveau **moet** `/apps`.
+ De map op het tweede niveau vertegenwoordigt de toepassing met `-packages` gepost-fixed aan de omslagnaam. Vaak is er slechts één map op het tweede niveau waarin alle subpakketten zijn ingesloten. Elk aantal mappen op het tweede niveau kan echter zo worden gemaakt dat dit de logische structuur van de toepassing het best weerspiegelt:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

  >[!WARNING]
  >
  >Volgens de conventie krijgen ingesloten subpakketten een naam met het achtervoegsel van `-packages`. Deze naam zorgt ervoor dat de plaatsingscode en de inhoudspakketten zijn **niet** de doelmappen van een willekeurig subpakket implementeren `/apps/<app-name>/...`  wat resulteert in destructief en cyclisch installatiemgedrag.

+ De map op het derde niveau moet ofwel
  `application`, `content` of `container`
   + De `application` map bevat codepakketten
   + De `content` map bevat inhoudspakketten
   + De `container` map bevat alle [extra toepassingspakketten](#extra-application-packages) die door de AEM toepassing kunnen worden opgenomen.
Deze mapnaam komt overeen met de naam [pakkettypen](#package-types) van de verpakkingen die het bevat.
+ De map op het vierde niveau bevat de subpakketten en moet een van de volgende zijn:
   + `install` dus u installeert op **beide** AEM auteur en AEM publiceren
   + `install.author` zodat u installeert **alleen** over AEM auteur
   + `install.publish` zodat u installeert **alleen** Alleen op AEM publiceren `install.author` en `install.publish` worden ondersteund. Andere uitvoermodi **worden niet** ondersteund.

Een implementatie die AEM auteur bevat en specifieke pakketten publiceert, kan er bijvoorbeeld als volgt uitzien:

+ `all` Containerpakket sluit de volgende pakketten in om een enkelvoudig implementatieartefact te maken
   + `ui.apps` ingesloten in `/apps/my-app-packages/application/install` implementeert code naar zowel AEM auteur als AEM publiceren
   + `ui.apps.author` ingesloten in `/apps/my-app-packages/application/install.author` implementeert code alleen naar AEM auteur
   + `ui.content` ingesloten in `/apps/my-app-packages/content/install` stelt inhoud en configuratie aan zowel AEM auteur als AEM publiceren op
   + `ui.content.publish` ingesloten in `/apps/my-app-packages/content/install.publish` implementeert inhoud en configuratie alleen om te AEM publiceren

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-embeddeds) hieronder voor een volledig fragment.

### Filterdefinitie van containerpakket {#container-package-filter-definition}

Door het insluiten van de code en inhoudsubpakketten in het containerpakket, moeten de ingebedde doelwegen aan het containerproject worden toegevoegd `filter.xml`. Dit zorgt ervoor dat de ingesloten pakketten bij het maken in het containerpakket worden opgenomen.

Voeg eenvoudig de `<filter root="/apps/<my-app>-packages"/>` vermeldingen voor mappen op het tweede niveau die subpakketten bevatten die moeten worden geïmplementeerd.

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-container-package-filters) hieronder voor een volledig fragment.

## Pakketten van derden insluiten {#embedding-3rd-party-packages}

Alle pakketten moeten beschikbaar zijn via de [Adobe openbare gegevensopslagplaats voor artefacten](https://repo1.maven.org/maven2/com/adobe/) of een toegankelijke openbare gegevensopslagruimte met verwijzing naar derde partijen.

Als de pakketten van derden zich bevinden in **Adobe openbare gegevensopslagplaats voor artefacten**, is er geen verdere configuratie nodig voor Adobe Cloud Manager om de artefacten op te lossen.

Als de pakketten van derden zich in een **openbare gegevensopslagruimte van derden voor Geweven artefact**, moet deze opslagplaats in het project worden geregistreerd `pom.xml` en ingesloten volgens de methode [hierboven geschetst](#embeddeds).

De toepassing/de schakelaars van de derde zouden moeten worden ingebed gebruikend zijn `all` pakket als container in de container van uw project (`all`).

Het toevoegen van Geweven gebiedsdelen volgt standaard Geweven praktijken, en het inbedden van derdeartefacten (code en inhoudspakketten) zijn [hierboven geschetst](#embedding-3rd-party-packages).

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-3rd-party-maven-repositories) hieronder voor een volledig fragment.

## Pakketafhankelijke onderdelen tussen de `ui.apps` van `ui.content` Pakketten {#package-dependencies}

Om een correcte installatie van de pakketten te verzekeren, wordt het geadviseerd interpackage gebiedsdelen worden gevestigd.

De algemene regel is dat pakketten met een veranderbaar gehalte (`ui.content`) moet afhankelijk zijn van de onveranderlijke code (`ui.apps`) die het renderen en gebruiken van de veranderbare inhoud ondersteunt.

Een opmerkelijke uitzondering op deze algemene regel is wanneer het onveranderlijke codepakket (`ui.apps` of andere), __alleen__ bevat OSGi-bundels. Zo ja, dan zou geen AEM pakket een afhankelijkheid van het moeten verklaren. De reden hiervoor is dat onveranderlijke codepakketten __alleen__ bevatten OSGi-bundels, zijn niet geregistreerd bij AEM [Pakketbeheer](/help/implementing/developing/tools/package-manager.md). Daarom heeft om het even welk AEM pakket dat van het afhangt een ontevreden gebiedsdeel en niet om te installeren.

>[!TIP]
>
>Zie de [XML-fragmenten voor POM](#xml-package-dependencies) hieronder voor een volledig fragment.

De gemeenschappelijke patronen voor de gebiedsdelen van het inhoudspakket zijn:

### Eenvoudige implementatiepakketafhankelijkheden {#simple-deployment-package-dependencies}

Met de eenvoudige optie stelt u de `ui.content` veranderbaar inhoudspakket om van `ui.apps` onveranderlijk codepakket.

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

De in dit artikel geschetste projectstructuren en -organisatie zijn **volledig compatibel** lokale ontwikkeling AEM instanties.

## XML-fragmenten voor POM {#pom-xml-snippets}

Het volgende wordt gemaakt `pom.xml` configuratiefragmenten die aan Geweven projecten kunnen worden toegevoegd om aan de bovengenoemde aanbevelingen te richten.

### Pakkettypen {#xml-package-types}

Code- en inhoudspakketten die als subpakketten worden geïmplementeerd, moeten een pakkettype declareren van **toepassing** of **content**, afhankelijk van wat ze bevatten.

#### Containerpakkettypen {#container-package-types}

De container `all/pom.xml` project **niet** verklaren `<packageType>`.

#### Code (Immuable) pakkettypen {#immutable-package-types}

Codepakketten moeten hun `packageType` tot `application`.

In de `ui.apps/pom.xml`de `<packageType>application</packageType>` stelt configuratierichtlijnen van de `filevault-package-maven-plugin` de insteekmoduledeclaratie declareert het pakkettype.

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

Inhoudspakketten moeten hun `packageType` tot `content`.

In de `ui.content/pom.xml`de `<packageType>content</packageType>` bouwstijlrichtlijn van `filevault-package-maven-plugin` de insteekmoduledeclaratie declareert het pakkettype.

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

In elk project dat een pakket genereert, **behalve** voor het containerproject (`all`), voegt u `<cloudManagerTarget>none</cloudManagerTarget>` aan de `<properties>`-configuratie van de declaratie van de invoegtoepassing `filevault-package-maven-plugin` toe om ervoor te zorgen dat deze **niet** door Adobe Cloud Manager worden geïmplementeerd. De container (`all`) moet het unieke pakket zijn dat via Cloud Manager wordt geïmplementeerd en dat op zijn beurt alle vereiste code en inhoudspakketten insluit.

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

Scripts voor Repo Init die de scripts voor Repo Init bevatten, worden gedefinieerd in het dialoogvenster `RepositoryInitializer` OSGi-fabrieksconfiguratie via de `scripts` eigenschap. Omdat deze manuscripten binnen configuraties OSGi worden bepaald, kunnen zij gemakkelijk bereikbaar door looppaswijze gebruikend het gebruikelijke zijn `../config.<runmode>` mapsemantiek.

Aangezien scripts doorgaans een declaratie van meerdere regels zijn, is het eenvoudiger om deze te definiëren in het dialoogvenster `.config` bestand, dan op JSON gebaseerd `.cfg.json` gebruiken.

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

De `scripts` OSGi-eigenschap bevat instructies zoals gedefinieerd door de [Repo Init-taal van Apache Sling](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

### Structuurpakket opslagplaats {#xml-repository-structure-package}

In de `ui.apps/pom.xml` en andere `pom.xml` dat een codepakket declareert (`<packageType>application</packageType>`), voegt u de volgende configuratie voor het structuurpakket van de repository toe aan de FileVault Maven-plug-in. U kunt [zelf een opslagstructuurpakket voor uw project maken](repository-structure-package.md).

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

In de `all/pom.xml`voegt u het volgende toe `<embeddeds>` aan de `filevault-package-maven-plugin` insteekdeclaratie. Onthoud, **niet** gebruiken `<subPackages>` configuratie. De reden hiervoor is dat de subpakketten in `/etc/packages` eerder dan `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?`.

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

In de `all` project `filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), **include** alle `-packages` mappen met subpakketten die moeten worden geïmplementeerd:

```xml
<filter root="/apps/my-app-packages"/>
```

Indien meerdere `/apps/*-packages` worden gebruikt in de ingesloten doelen, dan moeten ze allemaal hier worden opgesomd.

### Geplaatste opslagplaatsen van derden {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>Als u meer Maven-opslagruimten toevoegt, kunnen de gefabriceerde buildtijden langer duren omdat extra Maven-opslagruimten op afhankelijkheden worden gecontroleerd.

In het reactorproject `pom.xml`voegt u de benodigde instructies voor openbare gegevensopslagruimte van derden toe. De volledige `<repository>` De configuratie moet beschikbaar zijn bij de externe opslagprovider.

```xml
<repositories>
  ...
  <repository>
      <id>3rd-party-repository</id>
      <name>Public Third-Party Repository</name>
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

### Pakketafhankelijke onderdelen tussen de `ui.apps` van `ui.content` Pakketten {#xml-package-dependencies}

In de `ui.content/pom.xml`voegt u het volgende toe `<dependencies>` aan de `filevault-package-maven-plugin` insteekdeclaratie.

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

In de `all/pom.xml`, voegt u de `maven-clean-plugin` insteekmodule waarmee de doelmap wordt gewist voordat een Maven-build wordt gemaakt.

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
+ [Maven-plug-in voor het pakket met bestandsVault-inhoud](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
