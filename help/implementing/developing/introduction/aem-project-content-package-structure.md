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
>Verken me met basis [&#x200B; AEM het Gebruik van het Archetype van het Project &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL), en [&#x200B; Geweven Insteekmodule van de Inhoud FileVault &#x200B;](/help/implementing/developing/tools/maven-plugin.md) aangezien dit artikel op deze lessen en concepten voortbouwt.

In dit artikel worden de wijzigingen beschreven die nodig zijn om Adobe Experience Manager Maven-projecten compatibel te maken met AEM as a Cloud Service, door ervoor te zorgen dat ze de opsplitsing van muteerbare en onveranderlijke inhoud respecteren. Ook, worden de gebiedsdelen gevestigd om niet-strijdige, deterministische plaatsingen tot stand te brengen, en zij worden verpakt in een plaatsbare structuur.

AEM toepassingsimplementaties moeten bestaan uit één AEM. Dit pakket moet op zijn beurt subpakketten bevatten die alles bevatten wat door de toepassing wordt vereist om te functioneren, met inbegrip van code, configuratie, en om het even welke ondersteunende basislijninhoud.

AEM vereist een scheiding van **inhoud** en **code**, wat één enkel inhoudspakket **betekent kan niet** aan **zowel** opstellen `/apps` en runtime-schrijfbare gebieden (bijvoorbeeld, `/content`, `/conf`, `/home`, of om het even wat niet `/apps`) van de bewaarplaats. In plaats daarvan moet de applicatie code en content scheiden in afzonderlijke pakketten voor implementatie in AEM.

De pakketstructuur die in dit document wordt beschreven, is compatibel met **zowel** lokale ontwikkelingsimplementaties als AEM Cloud Service-implementaties.

>[!TIP]
>
>De configuraties die in dit document worden geschetst worden verstrekt door [&#x200B; AEM Project Maven Archetype 24 of later &#x200B;](https://github.com/adobe/aem-project-archetype/releases).

## Mutable versus Immuable Areas of the Repository {#mutable-vs-immutable}

`/apps` en `/libs` gebieden van AEM worden beschouwd als **onveranderlijk** omdat zij niet kunnen worden veranderd (creeer, update, schrapping) na AEM begin (namelijk bij runtime). Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, mislukt.

Al het andere in de bewaarplaats, `/content`, `/conf`, `/var`, `/etc`, `/oak:index`, `/system`, `/tmp`, etc., zijn alle **veranderbare** gebieden, betekenend zij kunnen bij runtime worden veranderd.

>[!WARNING]
>
>Net als in vorige versies van AEM, moet `/libs` niet worden gewijzigd. Alleen AEM productcode kan worden geïmplementeerd in `/libs` .

### Oak-indexen {#oak-indexes}

Oak-indexen (`/oak:index`) worden beheerd door het AEM as a Cloud Service-implementatieproces. De reden hiervoor is dat de Cloud Manager moet wachten totdat een nieuwe index wordt geïmplementeerd en volledig opnieuw is geordend voordat wordt overgeschakeld naar de nieuwe codeafbeelding.

Daarom, hoewel de indexen van Oak bij runtime veranderbaar zijn, moeten zij als code worden opgesteld zodat zij kunnen worden geïnstalleerd alvorens om het even welke veranderlijke pakketten worden geïnstalleerd. Daarom `/oak:index` de configuraties maken deel uit van het Pakket van de Code en geen deel van het Pakket van de Inhoud [&#x200B; zoals hieronder beschreven &#x200B;](#recommended-package-structure).

>[!TIP]
>
>Voor meer details over het indexeren in AEM as a Cloud Service, zie [&#x200B; Inhoud Onderzoek en het Indexeren &#x200B;](/help/operations/indexing.md).

## Aanbevolen pakketstructuur {#recommended-package-structure}

![&#x200B; de Structuur van het Pakket van het Project van de Experience Manager &#x200B;](assets/content-package-organization.png)

Dit diagram verstrekt een overzicht van de geadviseerde projectstructuur en pakketplaatsingsartefacten.

De aanbevolen implementatiestructuur voor toepassingen is als volgt:

### Codepakketten / OSGi-pakketten

+ Het Jar-bestand van de bundel OSGi wordt gegenereerd en rechtstreeks ingesloten in het hele project.

+ Het `ui.apps` -pakket bevat alle code die moet worden geïmplementeerd en wordt alleen geïmplementeerd op `/apps` . Veelvoorkomende elementen van het `ui.apps` -pakket zijn onder andere:
   + [&#x200B; de definities van de Component en HTML &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=nl-NL) manuscripten
      + `/apps/my-app/components`
   + JavaScript en CSS (via [&#x200B; Bibliotheken van de Cliënt &#x200B;](/help/implementing/developing/introduction/clientlibs.md))
      + `/apps/my-app/clientlibs`
   + [&#x200B; Bedekkingen &#x200B;](/help/implementing/developing/introduction/overlays.md) van `/libs`
      + `/apps/cq` , `/apps/dam/` , enzovoort.
   + Contextbewuste configuraties voor alternatieven
      + `/apps/settings`
   + ACLs (toestemmingen)
      + Alle `rep:policy` voor paden onder `/apps`
   + [&#x200B; vooraf gecompileerde gebundelde manuscripten &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/precompiled-bundled-scripts.html?lang=nl-NL)

>[!NOTE]
>
>Dezelfde code moet in alle omgevingen worden geïmplementeerd. Deze code garandeert een zeker betrouwbaarheidsniveau dat validaties in de werkgebiedomgeving ook in productie zijn. Voor meer informatie, zie de sectie op [&#x200B; Runmodes &#x200B;](/help/implementing/deploying/overview.md#runmodes).


### Inhoud-pakketten

+ Het `ui.content` -pakket bevat alle inhoud en configuratie. Het inhoudspakket bevat alle knoopdefinities die niet in de pakketten `ui.apps` of `ui.config` staan, of met andere woorden, alles wat niet in `/apps` of `/oak:index` staat. Veelvoorkomende elementen van het `ui.content` -pakket zijn onder andere:
   + Contextbewuste configuraties
      + `/conf`
   + Vereiste, complexe inhoudsstructuren (dat wil zeggen: de opbouw van inhoud die voortbouwt op en zich uitbreidt tot voorbij de basislijninhoudsstructuren die zijn gedefinieerd in Repo Init.)
      + `/content` , `/content/dam` , enzovoort.
   + Regelgevende taggende taxonomieën
      + `/content/cq:tags`
   + Verouderde knooppunten enz. (idealiter migreren deze knooppunten naar locaties buiten/enz.)
      + `/etc`

### Containerpakketten

+ Het `all` -pakket is een containerpakket dat ALLEEN implementeerbare artefacten, het OSGI-bundel Jar-bestand, `ui.apps` - `ui.config` - en `ui.content` -pakketten als insluitingen bevat. Het `all` pakket moet **geen inhoud of code** van zijn hebben, maar eerder al plaatsing aan de bewaarplaats aan zijn subpackages of OSGi bundel Jar dossiers delegeren.

  De pakketten zijn nu inbegrepen gebruikend het Geweven [&#x200B; Pakket FileVault Geproduceerde configuratie van de stop &#x200B;](#embeddeds), eerder dan de `<subPackages>` configuratie.

  Voor complexe implementaties van Experience Managers kan het wenselijk zijn om meerdere `ui.apps` -, `ui.config` - en `ui.content` -projecten/pakketten te maken die specifieke sites of huurders in AEM vertegenwoordigen. Als deze aanpak wordt toegepast, moet u ervoor zorgen dat de splitsing tussen muteerbare en onveranderlijke inhoud wordt gerespecteerd en dat de vereiste inhoudspakketten en OSGi-bundel Jar-bestanden worden ingesloten als subpakketten in het `all` containerinhoudspakket.

  Bijvoorbeeld, zou een complexe het pakketstructuur van de plaatsingsinhoud als dit kunnen kijken:

   + Met het inhoudspakket `all` worden de volgende pakketten ingesloten om een unieke implementatieartefact te maken
      + `common.ui.apps` stelt code op die door **wordt vereist zowel** plaats A als plaats B
      + `site-a.core` OSGi-bundel Jar vereist voor site A
      + `site-a.ui.apps` implementeert code die door site A wordt vereist
      + `site-a.ui.config` implementeert OSGi-configuraties die vereist zijn voor Site A
      + `site-a.ui.content` implementeert de inhoud en configuratie die vereist zijn voor site A
      + `site-b.core` OSGi-bundel Jar vereist voor site B
      + `site-b.ui.apps` implementeert code die vereist is voor site B
      + `site-b.ui.config` implementeert OSGi-configuraties die vereist zijn voor site B
      + `site-b.ui.content` implementeert de inhoud en configuratie die vereist zijn voor site B

+ Het `ui.config` pakket bevat alle [&#x200B; configuraties OSGi &#x200B;](/help/implementing/deploying/configuring-osgi.md):
   + Beschouw als code en behoort tot OSGi-bundels, maar bevat geen standaardinhoudsknooppunten. Het is dus gemarkeerd als een containerpakket
   + De omslag van de organisatie die loopwijze-specifieke definities OSGi config bevat
      + `/apps/my-app/osgiconfig`
   + Gemeenschappelijke OSGi configuratiemap die standaardOSGi configuraties bevat die op alle doelAEM as a Cloud Service plaatsingsdoelstellingen van toepassing zijn
      + `/apps/my-app/osgiconfig/config`
   + Voer wijze-specifieke OSGi configuratiemappen in werking die standaardOSGi configuraties bevatten die op alle doelAEM as a Cloud Service plaatsingsdoelstellingen van toepassing zijn
      + `/apps/my-app/osgiconfig/config.<author|publish>.<dev|stage|prod>`
   + Repo Init OSGi-configuratiescripts
      + [&#x200B; Reparatie &#x200B;](#repo-init) is de geadviseerde manier om (mutable) inhoud op te stellen die logisch gezien deel van de AEM toepassing uitmaakt. De OSGi-configuraties van Repo-poging moeten in de juiste `config.<runmode>` -map staan, zoals hierboven is beschreven. Deze configuraties moeten worden gebruikt om:
         + Basislijninhoudsstructuren
         + Gebruikers
         + Servicegebruikers
         + Groepen
         + ACLs (toestemmingen)

### Extra toepassingspakketten{#extra-application-packages}

Als andere AEM Projecten - die zelf uit hun eigen code en inhoudspakketten bestaan - door de AEM plaatsing worden gebruikt, zouden hun containerpakketten in het pakket van het project `all` moeten worden ingebed.

Bijvoorbeeld, zou een AEM project dat twee verkoper AEM toepassingen omvat als kunnen kijken:

+ Met het inhoudspakket `all` worden de volgende pakketten ingesloten om een unieke implementatieartefact te maken
   + `core` OSGi-bundel Jar vereist door de AEM toepassing
   + `ui.apps` implementeert code die is vereist door de AEM toepassing
   + `ui.config` implementeert OSGi-configuraties die vereist zijn door de AEM toepassing
   + `ui.content` implementeert de inhoud en configuratie die vereist zijn voor de AEM toepassing
   + `vendor-x.all` implementeert alle vereiste gegevens (code en inhoud) van de X-toepassing van de leverancier
   + `vendor-y.all` implementeert alles (code en inhoud) dat is vereist door de Y-toepassing van de leverancier

## Pakkettypen {#package-types}

Pakketten moeten worden gemarkeerd met het opgegeven pakkettype. De types van pakket helpen het doel en de plaatsing van een pakket verduidelijken.

+ Containerpakketten moeten hun `packageType` instellen op `container` . Containerpakketten mogen geen normale knooppunten bevatten. Alleen OSGi-bundels, -configuraties en -subpakketten zijn toegestaan. De containers in AEM as a Cloud Service worden niet toegestaan om [&#x200B; te gebruiken installeren haken &#x200B;](https://jackrabbit.apache.org/filevault/installhooks.html).
+ Codepakketten (onveranderlijk) moeten hun `packageType` instellen op `application` .
+ Inhoud (veranderbaar) pakketten moeten hun `packageType` instellen op `content` .


Voor meer informatie zie [&#x200B; Apache Jackrabbit FileVault - Pakket Maven de documentatie van de Insteekmodule &#x200B;](https://jackrabbit.apache.org/filevault-package-maven-plugin/package-mojo.html#packageType), [&#x200B; de Types van Pakket van het Pakket Apache Jackrabbit &#x200B;](https://jackrabbit.apache.org/filevault/packagetypes.html), en het [&#x200B; FileVault Maven configuratiefragment &#x200B;](#marking-packages-for-deployment-by-adoube-cloud-manager) hieronder.

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-package-types) hieronder sectie voor een volledig fragment.

## Pakketten markeren voor implementatie door Adobe Cloud Manager {#marking-packages-for-deployment-by-adoube-cloud-manager}

Standaard worden alle door de Maven-build geproduceerde pakketten door Adobe Cloud Manager geoogst. Nochtans, omdat het container (`all`) pakket het unieke plaatsingsartefact is dat alle code en inhoudspakketten bevat, moet u **verzekeren slechts** het container (`all`) pakket wordt opgesteld. Om dit te garanderen moeten andere pakketten die de Maven-build genereert, zijn gemarkeerd met de configuratie voor de FileVault Content Package Maven-invoegtoepassing van `<properties><cloudManagerTarget>none</cloudManageTarget></properties>`.

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#pom-xml-snippets) hieronder sectie voor een volledig fragment.

## Reparatie-item{#repo-init}

Repo Init verstrekt instructies, of manuscripten, die structuren JCR, die zich van gemeenschappelijke knoopstructuren zoals omslagbomen, aan gebruikers, de dienstgebruiker, groepen, en ACL definitie uitstrekken bepalen.

De belangrijkste voordelen van Repo Init zijn zij impliciete toestemmingen hebben om alle acties uit te voeren die door hun manuscripten worden bepaald. En, worden dergelijke manuscripten aangehaald vroeg in de plaatsingslevenscyclus die ervoor zorgt dat alle vereiste structuren JCR tegen de tijdcode bestaan in werking wordt gesteld.

Hoewel de manuscripten van de Inzet van de Repo in het `ui.config` project als manuscripten leven, kunnen en moeten zij worden gebruikt om de volgende veranderbare structuren te bepalen:

+ Basislijninhoudsstructuren
+ Servicegebruikers
+ Gebruikers
+ Groepen
+ ACLs

Scripts voor herhalingsindelingen worden opgeslagen als `scripts` -items van `RepositoryInitializer` OSGi-fabrieksconfiguraties. Als dusdanig, kunnen zij impliciet door looppaswijze worden gericht, die voor verschillen tussen AEM Auteur en AEM de manuscripten van de Repo van de Diensten van Publish, of zelfs tussen milieu&#39;s (Dev, Stadium, en Prod) toestaat.

Repo Init OSGi vormt best geschreven in het [`.config` OSGi configuratieformaat &#x200B;](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-config-1) aangezien zij multi-lines steunen, die een uitzondering op de beste praktijken is om [`.cfg.json` te gebruiken om configuraties te bepalen OSGi &#x200B;](https://sling.apache.org/documentation/bundles/configuration-installer-factory.html#configuration-files-cfgjson-1).

Wanneer het bepalen van Gebruikers, en Groepen, slechts worden de groepen beschouwd als deel van de toepassing, en integraal aan zijn functie. U definieert bij uitvoering nog steeds Organisatiegebruikers en -groepen in AEM. Als een aangepaste workflow bijvoorbeeld werk toewijst aan een benoemde groep, definieert u die groep als repo-item in de AEM toepassing. Nochtans, als de Groepering slechts organisatorisch, zoals &quot;Team van Wendy&quot;en &quot;Team van Sean&quot;is, worden deze groepen het best bepaald en geleid bij runtime in AEM.

>[!TIP]
>
>De manuscripten van het Begin van de herhaling *moeten* op het gealigneerde `scripts` gebied worden bepaald, of de `references` configuratie werkt niet.

De volledige woordenlijst voor de manuscripten van het Begin van de Repo is beschikbaar op [&#x200B; Apache Sling de documentatie van het Begin van de Repo &#x200B;](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language).

>[!TIP]
>
>Zie de [&#x200B; sectie van de Fragmenten van de Intrek van de Repo &#x200B;](#snippet-repo-init) hieronder voor een volledig fragment.

## Structuurpakket opslagplaats {#repository-structure-package}

Codepakketten vereisen dat de configuratie van de FileVault Maven-plug-in wordt geconfigureerd om te verwijzen naar een `<repositoryStructurePackage>` die de juistheid van structurele afhankelijkheden afdwingt (om ervoor te zorgen dat een codepakket niet boven een ander codepakket wordt geïnstalleerd). U kunt [&#x200B; uw eigen de structuurpakket van de bewaarplaats voor uw project &#x200B;](repository-structure-package.md) tot stand brengen.

**slechts vereist** voor de pakketten van de Code, betekenend om het even welk Pakket duidelijk met `<packageType>application</packageType>`.

Leren hoe te om een pakket van de gegevensopslagstructuur voor uw toepassing tot stand te brengen, zie [&#x200B; een Pakket van de Structuur van de Opslag ontwikkelen &#x200B;](repository-structure-package.md).

De pakketten van de inhoud (`<packageType>content</packageType>`) **vereisen niet** dit pakket van de bewaarplaatsstructuur.

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-repository-structure-package) hieronder sectie voor een volledig fragment.

## Subpakketten insluiten in het Containerpakket{#embeddeds}

Inhoud- of codepakketten worden in een speciale map &quot;side-car&quot; geplaatst en kunnen worden geïnstalleerd op AEM auteur, AEM publicatie of beide via de configuratie `<embeddeds>` van de FileVault Maven-plug-in. Gebruik de `<subPackages>` -configuratie niet.

Veelvoorkomende gebruiksgevallen zijn:

+ ACLs/toestemmingen die tussen AEM auteursgebruikers en AEM publicatiegebruikers verschillen
+ Configuraties die alleen worden gebruikt ter ondersteuning van activiteiten van AEM auteur
+ Code zoals integratie met back-office systemen, die alleen vereist is voor AEM auteur

![&#x200B; Inbeddend Pakketten &#x200B;](assets/embeddeds.png)

Als u AEM auteur als doel wilt instellen, AEM publiceert of beide, wordt het pakket ingesloten in het `all` -containerpakket in een speciale maplocatie, in de volgende indeling:

`/apps/<app-name>-packages/(content|application|container)/install(.author|.publish)?`

Deze mapstructuur indelen:

+ De omslag op het eerste niveau **moet** `/apps` zijn.
+ De map op het tweede niveau vertegenwoordigt de toepassing waarvan `-packages` is hersteld naar de mapnaam. Vaak is er slechts één map op het tweede niveau waarin alle subpakketten zijn ingesloten. Elk aantal mappen op het tweede niveau kan echter zo worden gemaakt dat dit de logische structuur van de toepassing het best weerspiegelt:
   + `/apps/my-app-packages`
   + `/apps/my-other-app-packages`
   + `/apps/vendor-packages`

  >[!WARNING]
  >
  >Standaard krijgen ingesloten mappen in subpakketten een naam met het achtervoegsel `-packages` . Dit het noemen zorgt ervoor dat de plaatsingscode en de inhoudspakketten **&#x200B;**&#x200B;niet de doelomslagen van om het even welk subpackage `/apps/<app-name>/...` worden opgesteld die in destructief en cyclisch installatiegedrag resulteren.

+ De map op het derde niveau moet ofwel
  `application` , `content` of `container`
   + De map `application` bevat codepakketten
   + De map `content` bevat inhoudspakketten
   + De `container` omslag houdt om het even welke [&#x200B; extra toepassingspakketten &#x200B;](#extra-application-packages) die door de AEM toepassing zouden kunnen worden omvat.
Deze omslagnaam beantwoordt aan de [&#x200B; pakkettypes &#x200B;](#package-types) van de pakketten die het bevat.
+ De map op het vierde niveau bevat de subpakketten en moet een van de volgende zijn:
   + `install` zodat installeert u op **zowel** AEM auteur en AEM publiceren
   + `install.author` zodat installeert u **slechts** op AEM auteur
   + `install.publish` zodat installeert u **slechts** op AEM publiceren
Alleen `install.author` en `install.publish` zijn ondersteunde doelen. Andere uitvoermodi **worden niet** ondersteund.

Een implementatie die AEM auteur bevat en specifieke pakketten publiceert, kan er bijvoorbeeld als volgt uitzien:

+ `all` Containerpakket sluit de volgende pakketten in om een uniek implementatieartefact te maken
   + `ui.apps` die is ingesloten in `/apps/my-app-packages/application/install` , implementeert code naar AEM auteur en AEM publiceren
   + `ui.apps.author` die is ingesloten in `/apps/my-app-packages/application/install.author` , implementeert code alleen naar AEM auteur
   + `ui.content` die is ingesloten in `/apps/my-app-packages/content/install` , implementeert inhoud en configuratie AEM auteur en AEM publiceren
   + `ui.content.publish` ingesloten in `/apps/my-app-packages/content/install.publish` implementeert inhoud en configuratie alleen om te AEM publiceren

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-embeddeds) hieronder sectie voor een volledig fragment.

### Filterdefinitie van containerpakket {#container-package-filter-definition}

Wegens het inbedden van de code en inhoudsubpakketten in het containerpakket, moeten de ingebedde doelwegen aan het containerproject `filter.xml` worden toegevoegd. Dit zorgt ervoor dat de ingesloten pakketten bij het maken in het containerpakket worden opgenomen.

Voeg gewoon de `<filter root="/apps/<my-app>-packages"/>` -items toe voor mappen op het tweede niveau die subpakketten bevatten die u wilt implementeren.

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-container-package-filters) hieronder sectie voor een volledig fragment.

## Pakketten van derden insluiten {#embedding-3rd-party-packages}

Alle pakketten moeten via de [&#x200B; openbare Geweven bewaarplaats van het Artefact van de Adobe &#x200B;](https://repo1.maven.org/maven2/com/adobe/) of een toegankelijk openbaar, van verwijzingen voorzien derdeGeproduceerde artefactbewaarplaats beschikbaar zijn.

Als de derdepakketten in **openbare Maven artefactbewaarplaats van de Adobe** zijn, is geen verdere configuratie nodig voor Adobe Cloud Manager om de artefacten op te lossen.

Als de derdepakketten in a **openbare derde Geleide artefactbewaarplaats** zijn, moet deze bewaarplaats in het project `pom.xml` en ingebed na de hierboven geschetste methode [&#128279;](#embeddeds) worden geregistreerd.

De toepassing/de schakelaars van de derde zouden moeten worden ingebed gebruikend zijn `all` pakket als container in de container van uw project (`all`) pakket.

Toevoegend Geweven gebiedsdelen volgen standaard Geweven praktijken, en het inbedden van derdeartefacten (code en inhoudspakketten) worden hierboven geschetst [&#128279;](#embedding-3rd-party-packages).

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-3rd-party-maven-repositories) hieronder sectie voor een volledig fragment.

## Afhankelijkheden van pakketten tussen de `ui.apps` en `ui.content` Pakketten {#package-dependencies}

Om een correcte installatie van de pakketten te verzekeren, wordt het geadviseerd interpackage gebiedsdelen worden gevestigd.

De algemene regel is pakketten die veranderbare inhoud (`ui.content`) bevatten zou van de onveranderlijke code (`ui.apps`) moeten afhangen die het teruggeven en het gebruik van de veranderlijke inhoud steunt.

Een opmerkelijke uitzondering op deze algemene regel is als het onveranderlijke codepakket (`ui.apps` of een ander), __slechts__ OSGi bundels bevat. Zo ja, dan zou geen AEM pakket een afhankelijkheid van het moeten verklaren. De reden is omdat de onveranderlijke codepakketten die __slechts__ OSGi bundels bevatten, niet met AEM [&#x200B; Manager van het Pakket &#x200B;](/help/implementing/developing/tools/package-manager.md) worden geregistreerd. Daarom heeft om het even welk AEM pakket dat van het afhangt een ontevreden gebiedsdeel en niet om te installeren.

>[!TIP]
>
>Zie de [&#x200B; POMXML Fragmenten &#x200B;](#xml-package-dependencies) hieronder sectie voor een volledig fragment.

De gemeenschappelijke patronen voor de gebiedsdelen van het inhoudspakket zijn:

### Eenvoudige implementatiepakketafhankelijkheden {#simple-deployment-package-dependencies}

Met het eenvoudige hoofdlettergebruik wordt het `ui.content` veranderbare inhoudspakket zo ingesteld dat het afhankelijk is van het `ui.apps` -pakket voor onveranderlijke code.

+ `all` heeft geen afhankelijkheden
   + `ui.apps` heeft geen afhankelijkheden
   + `ui.content` is afhankelijk van `ui.apps`

### Complexe implementatiepakketafhankelijkheden {#complex-deploxment-package-dependencies}

De complexe plaatsingen breiden zich op het eenvoudige geval uit, en plaatsen gebiedsdelen tussen de overeenkomstige veranderlijke inhoud en de onveranderlijke codepakketten. Zoals vereist, kunnen de gebiedsdelen ook tussen onveranderlijke codepakketten worden gevestigd.

+ `all` heeft geen afhankelijkheden
   + `common.ui.apps.common` heeft geen afhankelijkheden
   + `site-a.ui.apps` is afhankelijk van `common.ui.apps`
   + `site-a.ui.content` is afhankelijk van `site-a.ui.apps`
   + `site-b.ui.apps` is afhankelijk van `common.ui.apps`
   + `site-b.ui.content` is afhankelijk van `site-b.ui.apps`

## Lokale ontwikkeling en implementatie {#local-development-and-deployment}

De projectstructuren en organisatie die in dit artikel worden geschetst zijn **volledig - compatibele** lokale ontwikkeling AEM instanties.

## XML-fragmenten voor POM {#pom-xml-snippets}

Hier volgt een overzicht van `pom.xml` -configuratiefragmenten die kunnen worden toegevoegd aan Maven-projecten om deze uit te lijnen op de bovenstaande aanbevelingen.

### Pakkettypen {#xml-package-types}

De pakketten van de code en van de inhoud, die als subpakketten worden opgesteld, moeten een pakkettype van **toepassing** of **inhoud** verklaren, afhankelijk van wat zij bevatten.

#### Containerpakkettypen {#container-package-types}

Het container `all/pom.xml` project **verklaart niet** a `<packageType>`.

#### Code (Immuable) pakkettypen {#immutable-package-types}

Codepakketten moeten hun `packageType` instellen op `application` .

In de `ui.apps/pom.xml` -instructies declareert de `<packageType>application</packageType>` build-configuratieinstructies van de plug-in `filevault-package-maven-plugin` het pakkettype.

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

Inhoudspakketten moeten hun `packageType` instellen op `content` .

In de `ui.content/pom.xml` , verklaart de `<packageType>content</packageType>` bouwstijlconfiguratierichtlijn van de `filevault-package-maven-plugin` plugin verklaring zijn pakkettype.

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

### Pakketten markeren voor Adobe Cloud Manager-implementatie {#cloud-manager-target}

In elk project dat een pakket genereert, **behalve** voor het containerproject (`all`), voegt u `<cloudManagerTarget>none</cloudManagerTarget>` aan de `<properties>`-configuratie van de declaratie van de invoegtoepassing `filevault-package-maven-plugin` toe om ervoor te zorgen dat deze **niet** door Adobe Cloud Manager worden geïmplementeerd. Het containerpakket (`all`) moet het enkelvoudige pakket zijn dat via Cloud Manager wordt geïmplementeerd en dat op zijn beurt alle vereiste code- en inhoudspakketten insluit.

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

Scripts voor Repo Init die de scripts voor Repo Init bevatten, zijn via de eigenschap `scripts` gedefinieerd in de `RepositoryInitializer` OSGi-fabrieksconfiguratie. Omdat deze manuscripten binnen configuraties OSGi worden bepaald, kunnen zij gemakkelijk bereikbaar zijn door wijze in werking te stellen gebruikend de gebruikelijke `../config.<runmode>` omslagsemantiek.

Aangezien scripts doorgaans een declaratie van meerdere regels zijn, is het eenvoudiger om ze in het `.config` -bestand te definiëren dan in de op JSON gebaseerde `.cfg.json` -indeling.

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

Het `scripts` bezit OSGi bevat richtlijnen zoals die door de [&#x200B; Reparatie van de Schaal van Apache &#x200B;](https://sling.apache.org/documentation/bundles/repository-initialization.html#the-repoinit-repository-initialization-language) worden bepaald.

### Structuurpakket opslagplaats {#xml-repository-structure-package}

Voeg in de `ui.apps/pom.xml` en elke andere `pom.xml` die een codepakket declareert ( `<packageType>application</packageType>` ) de volgende configuratie van het opslagstructuurpakket toe aan de FileVault Maven-plug-in. U kunt [&#x200B; uw eigen de structuurpakket van de bewaarplaats voor uw project &#x200B;](repository-structure-package.md) tot stand brengen.

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

Voeg in de `all/pom.xml` de volgende `<embeddeds>` -instructies toe aan de declaratie van de `filevault-package-maven-plugin` -invoegtoepassing. Herinner me, **gebruikt** niet de `<subPackages>` configuratie. De reden hiervoor is dat de subpakketten niet in `/apps/my-app-packages/<application|content|container>/install(.author|.publish)?` , maar in `/etc/packages` worden opgenomen.

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

In `all` project `filter.xml` (`all/src/main/content/jcr_root/META-INF/vault/definition/filter.xml`), **omvat** om het even welke `-packages` omslagen die subpakketten bevatten om op te stellen:

```xml
<filter root="/apps/my-app-packages"/>
```

Als er meerdere `/apps/*-packages` worden gebruikt in de ingesloten doelen, moeten ze allemaal hier worden opgesomd.

### Geplaatste opslagplaatsen van derden {#xml-3rd-party-maven-repositories}

>[!WARNING]
>
>Als u meer Maven-opslagruimten toevoegt, kunnen de gefabriceerde buildtijden langer duren omdat extra Maven-opslagruimten op afhankelijkheden worden gecontroleerd.

Voeg in de `pom.xml` -instructies van het reactorproject de benodigde instructies van derden voor openbare opslag Maven toe. De volledige `<repository>` -configuratie moet beschikbaar zijn bij de externe opslagprovider.

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

### Afhankelijkheden van pakketten tussen de `ui.apps` en `ui.content` Pakketten {#xml-package-dependencies}

Voeg in de `ui.content/pom.xml` de volgende `<dependencies>` -instructies toe aan de declaratie van de `filevault-package-maven-plugin` -invoegtoepassing.

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

Voeg in `all/pom.xml` de plug-in `maven-clean-plugin` toe die de doelmap wist voordat een Maven-build werd gemaakt.

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
+ [&#x200B; Geproduceerde Plug-in van het Pakket van de Inhoud FileVault &#x200B;](https://jackrabbit.apache.org/filevault-package-maven-plugin/)
