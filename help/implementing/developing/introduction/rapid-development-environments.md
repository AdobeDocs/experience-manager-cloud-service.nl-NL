---
title: Snelle ontwikkelomgevingen
description: Leer hoe u Rapid Development Environment kunt gebruiken voor snelle ontwikkelherhalingen in een cloud-omgeving.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 24c34daebf7d45d9262181890310eb196c58a7db
workflow-type: tm+mt
source-wordcount: '4990'
ht-degree: 0%

---

# Snelle ontwikkelomgevingen {#rapid-development-environments}

Om veranderingen op te stellen, vereisen de huidige milieu&#39;s van de Ontwikkeling van de Wolk het gebruik van een proces dat uitgebreide codeveiligheid en kwaliteitsregels gebruikt genoemd een pijpleiding CI/CD. Voor situaties waar snelle en iteratieve veranderingen nodig zijn, heeft de Adobe de Milieu&#39;s van de Snelle Ontwikkeling (RDEs voor kort) ingevoerd.

RDEs staat ontwikkelaars toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren nodig om eigenschappen te testen die aan een lokale ontwikkelomgeving blijken te werken.

Zodra de veranderingen in RDE zijn getest, kunnen zij aan een regelmatige milieu van de Ontwikkeling van de Wolk door de pijpleiding van Cloud Manager worden opgesteld.

>[!NOTE]
> Krijg in contact met de ontwikkelaars van RDE op ons [ kanaal van de Opsporing ](https://discord.com/channels/1131492224371277874/1245304281184079872). Voel vrij om het even welke vragen te stellen of terugkoppelen betreffende onderwerpen RDE.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


U kunt extra video&#39;s zien die [ tonen hoe te om het ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html), [ te plaatsen hoe te om het ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html) te gebruiken, en de [ cyclus van het ontwikkelingsleven ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle.html) gebruikend RDE.

## Inleiding {#introduction}

RDEs kan voor code, inhoud, en Apache of Dispatcher configuraties worden gebruikt. In tegenstelling tot gewone Cloud Development-omgevingen kunnen ontwikkelaars lokale opdrachtregelprogramma&#39;s gebruiken om code die lokaal is gemaakt te synchroniseren met een RDE.

Elk programma wordt voorzien van RDE. Als er Sandbox-accounts zijn, worden deze na een paar uur niet meer gebruikt.

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare Adobe Experience Manager-versie (AEM). Een RDE-reset, die kan worden uitgevoerd met Cloud Manager, fietst de RDE en stelt deze in op de laatst beschikbare AEM versie.

Typisch, zou RDE door één enkele ontwikkelaar in een bepaalde tijd, voor het testen en het zuiveren van een specifieke eigenschap worden gebruikt. Wanneer de ontwikkelingszitting wordt gedaan, kan RDE in een standaardstaat voor het volgende gebruik worden teruggesteld.

Aanvullende RDE&#39;s kunnen in licentie worden gegeven voor productieprogramma&#39;s (niet-sandbox).

## RDE inschakelen in een programma {#enabling-rde-in-a-program}

Voer de volgende stappen uit, zodat u Cloud Manager kunt gebruiken om een RDE voor uw programma te maken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik het programma waaraan u RDE wilt toevoegen om zijn details te tonen.

   * RDEs kan aan zowel [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) als [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) worden toegevoegd.

1. Van de **pagina van het Overzicht van het 0} Programma, klik** voeg Milieu **op de** kaart van Milieu **toe om een milieu toe te voegen.**

   ![ kaart van Milieu&#39;s ](/help/implementing/cloud-manager/assets/no-environments.png)

   * **voegt de optie van het Milieu** toe is ook beschikbaar op **Milieu** tabel.

     ![ Milieu&#39;s tabel ](/help/implementing/cloud-manager/assets/environments-tab.png)

   * **voeg Milieu** optie toe kan wegens gebrek aan toestemmingen of afhankelijk van de vergunning gegeven middelen worden onbruikbaar gemaakt.

1. In **voeg milieu** dialoog toe die verschijnt:

   * Selecteer **Snelle Ontwikkeling** onder de **Uitgezochte milieu type** rubriek.
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes achter het omgevingstype weergegeven.
   * Verstrek a **Naam** voor het milieu.
   * Verstrek een facultatieve **Beschrijving** voor het milieu.
   * Selecteer het Gebied van de a **Wolk**.

   ![ voeg milieudialoog ](/help/implementing/cloud-manager/assets/add-environment-wizard.png) toe

1. Klik **sparen** om het gespecificeerde milieu toe te voegen.

Het **scherm van het Overzicht** toont nu uw nieuw milieu in de **** kaart van Milieu&#39;s.

Bij het maken worden RDE&#39;s ingesteld op de meest recente beschikbare AEM. Een RDE-reset, die ook kan worden uitgevoerd met Cloud Manager, fietst de RDE en stelt deze in op de laatst beschikbare AEM versie.

Voor meer informatie over het gebruiken van Cloud Manager om milieu&#39;s tot stand te brengen, wie toegang tot hen heeft, en douanedomeinen toe te wijzen, zie [ de documentatie van Cloud Manager ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

## De RDE Command-Lijn hulpmiddelen installeren {#installing-the-rde-command-line-tools}

Nadat u een RDE voor uw programma gebruikend Cloud Manager hebt toegevoegd, kunt u met het in wisselwerking staan door de bevel-lijn hulpmiddelen te plaatsen zoals die in de volgende stappen worden beschreven:

>[!IMPORTANT]
>
>Zorg ervoor u versie 20 van [ geïnstalleerde Knoop en NPM ](https://nodejs.org/en/download/) voor Adobe I/O CLI en verwante steekmodules hebt om behoorlijk te werken.


1. Installeer de Adobe I/O CLI hulpmiddelen volgens deze [ procedure ](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installeer de Adobe I/O CLI-gereedschappen AEM RDE-insteekmodule:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Meld u aan met de AIR-client.

   ```
   aio login
   ```

   De login informatie (teken) wordt opgeslagen in de globale luchtvaartconfiguratie en steunt daarom slechts één login en organisatie. Voor het geval u veelvoudige RDEs wilt gebruiken die verschillende logins of organisaties vereisen, volg hieronder voorbeeld introducerend contexten.

   <details><summary>Volg dit voorbeeld om een lokale context voor één van uw logins van de RDE te plaatsen</summary>
   Voer de volgende stappen uit om de aanmeldingsgegevens lokaal op te slaan in een .aio-bestand in de huidige map binnen een specifieke context. Een context is ook een slimme manier om een milieu CI/CD of een manuscript te plaatsen.  Gebruik ten minste AIR versie 10.3.1 om van deze functie gebruik te maken. Deze bijwerken met behulp van 'npm install -g @adobe/aio-cli'

   Laten we een context met de naam &#39;mycontext&#39; maken die we vervolgens instellen als de standaardcontext met de automatische insteekmodule voordat we de aanmeldingsopdracht aanroepen.

   ```
   aio config set --json -l "ims.contexts.mycontext" "{ cli.bare-output: false }"
   aio auth ctx -s mycontext
   aio login --no-open
   ```

   >[!NOTE]
   > De login bevel met de `--no-open` optie zal een URL in de terminal in plaats van het openen van uw standaardbrowser uitvoeren. Als dat kunt u het met een **incognito** venster van uw browser kopiëren en openen. Op deze manier blijft de sessie die momenteel is aangemeld in het normale browservenster ongewijzigd en kunt u ervoor zorgen dat u de specifieke aanmelding en organisatie gebruikt die nodig zijn voor uw context.

   Met de eerste opdracht maakt u een nieuwe aanmeldingscontextconfiguratie met de naam `mycontext` in het lokale `.aio` -configuratiebestand (het bestand wordt indien nodig gemaakt). Met de tweede opdracht stelt u de context `mycontext` in als de &quot;huidige&quot; context, d.w.z. de standaardcontext.

   Met deze configuratie op zijn plaats, slaat het login bevel automatisch de login tokens in de context `mycontext` op, en houdt zo het lokaal.

   U kunt meerdere contexten beheren door lokale configuraties in meerdere mappen te bewaren. Alternatief, is het ook mogelijk om veelvoudige context binnen één enkel configuratiedossier te plaatsen, en tussen hen te schakelen door de &quot;huidige&quot;context te veranderen.
   </details>

1. Configureer de RDE-plug-in om uw organisatie, programma en omgeving te gebruiken. De opstellingsbevel hieronder zal interactief de gebruiker van een lijst van programma&#39;s in hun organisatie voorzien, en zal milieu&#39;s RDE in dat programma tonen om van te kiezen.

   ```
   aio aem:rde:setup
   ```

   De opstellingsstap kan worden overgeslagen als de bedoeling een scripted milieu is te gebruiken, in welk geval de organisatie, het programma en de milieuwaarden in elk bevel kunnen worden omvat. [ zie hieronder bevelen voor meer informatie ](#rde-cli-commands).

### De interactieve installatie {#installing-the-rde-command-line-tools-interactive}

Het opstellingsbevel zal vragen of zou de verstrekte configuratie plaatselijk of globaal moeten worden opgeslagen.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

Kies `no` naar
* sla de organisatie, het programma en het milieu globaal in uw configuratie van de lucht op.
* werken met slechts één RDE.

Kies `yes` naar
* sla de organisatie, het programma en de omgeving lokaal op in de huidige map, in een `.aio` -bestand. Dit is handig als u het bestand wilt toewijzen aan versiebeheer, zodat andere gebruikers het kunnen gebruiken door de it-opslagplaats te klonen.
* het werk met vele RDEs, zodat het schakelen naar een andere folder die configuratie in plaats daarvan zal gebruiken.
* gebruik de configuratie in een programmatic context zoals een manuscript, dat het kan van verwijzingen voorzien.


Zodra de lokale of globale configuratie wordt geselecteerd, zal het opstellingsbevel proberen om uw organisatie identiteitskaart van uw huidige login te lezen en dan de programma&#39;s van de organisatie te lezen. Als de organisatie niet kan worden gevonden, kunt u het manueel samen met sommige begeleiding ingaan.

```
Selected only organization: XYXYXYXYXYXYXYXXYY
retrieving programs of your organization ...
```

Nadat de programma&#39;s zijn opgehaald, kan de gebruiker een keuze maken in de lijst en filteren.
Wanneer het programma is geselecteerd, wordt een lijst met RDE-omgevingen weergegeven waaruit u kunt kiezen.
Als er slechts één programma en/of RDE-omgeving beschikbaar is, wordt deze automatisch geselecteerd.

Om de huidige omgevingscontext te zien, voert u uit:

```aio aem rde setup --show```

De opdracht reageert op een resultaat dat lijkt op:

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

### Handmatige installatieprocedure in een niet-interactieve omgeving {#manual-setup}

Voor omgevingen waar geen enkele gebruiker de hierboven beschreven opstellingsopdracht interactief kan uitvoeren (zoals CI/CD of scripts), kunnen de drie parameters voor organisatie, programma en omgeving handmatig worden geconfigureerd volgens de volgende stappen.


<details>
  <summary>Vouw uit om details te zoeken over het handmatig configureren</summary>

1. Configureer uw organisatie-id en vervang de alfanumerieke tekenreeks door uw eigen organisatie-id.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   * Uw eigen organisatieidentiteitskaart kan omhoog worden gezocht gebruikend de methode die onder [ wordt gedocumenteerd Mening uw organisatieidentiteitskaart ](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configureer vervolgens uw programma-id:

   `aio config:set cloudmanager_programid 12345`

1. Dan, vorm milieu identiteitskaart dat RDE aan in bijlage zal zijn:

   `aio config:set cloudmanager_environmentid 123456`

1. Nadat u klaar bent met het configureren van de insteekmodule, meldt u zich aan door

   `aio login`

   Deze stappen vereisen u om een lid van de Ontwikkelaar van Cloud Manager **te zijn - Cloud Service** Profiel van het Product. Zie [ de Leden van het Team aan de Profielen van het Product van Cloud Manager toewijzen - wijs het Profiel van het Product van de Ontwikkelaar ](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer details toe.

Voor meer informatie en demonstratie, bekijk het videoleerprogramma [ hoe te opstelling RDE (06:24) ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html).
</details>

## RDE gebruiken terwijl het Ontwikkelen van een Nieuwe Eigenschap {#using-rde-while-developing-a-new-feature}

Adobe raadt de volgende workflow aan voor het ontwikkelen van een nieuwe functie:

* Wanneer een tussentijdse mijlpaal wordt bereikt en met succes plaatselijk met AEM as a Cloud Service SDK wordt bevestigd, verbind de code aan een de eigenschaptak van de it. De vertakking mag nog geen deel uitmaken van de hoofdlijn, hoewel vastlegging aan de it optioneel is. Wat een &quot;tussenliggende mijlpaal&quot; is, varieert op basis van teamgewoonten. Voorbeelden zijn enkele nieuwe coderegels, een halve werkdag of het voltooien van een subfunctie.

* Herstel RDE als het door een andere eigenschap is gebruikt en u wilt [ het aan een standaardstaat ](#reset-rde) terugstellen. <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). --> het Terugstellen neemt een paar notulen en al bestaande inhoud en code wordt geschrapt. U kunt het RDE statusbevel gebruiken om RDE klaar te bevestigen. De RDE komt terug met de meest recente versie van de AEM.

  >[!IMPORTANT]
  >
  > Als uw het opvoeren en productiemilieu&#39;s geen automatische AEM versie-updates ontvangen en achter de meest recente AEM versieversie zijn, kan de code die op RDE loopt niet aanpassen hoe de code op het opvoeren en productie functioneert. In dat geval, is het vooral belangrijk om grondig het testen van de code op het opvoeren uit te voeren alvorens het aan productie op te stellen.


* Gebruikend RDE bevel-lijn interface, synchroniseer lokale code aan RDE. U kunt onder andere een inhoudspakket, een specifieke bundel, een configuratiebestand voor SDAB, een inhoudsbestand en een ZIP-bestand van een Apache/Dispatcher-configuratie installeren. Het is ook mogelijk te verwijzen naar een extern inhoudspakket. Zie [ RDE bevel-Lijn Hulpmiddelen ](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands) voor meer informatie. U kunt het statusbevel gebruiken om te bevestigen dat de plaatsing succesvol was. Gebruik optioneel Package Manager om inhoudspakketten te installeren.

* Test de code in RDE. Auteur- en Publish-URL&#39;s zijn beschikbaar in Cloud Manager.

* Als de code zich niet zoals verwacht gedraagt, gebruik standaard het zuiveren technieken om het probleem te begrijpen en de aangewezen veranderingen aan te brengen. Zonder de codewijzigingen toe te wijzen aan git (aangezien zij niet) zijn bevestigd, gebruik lokale CLI om de code aan RDE te synchroniseren. Herhaal dit totdat het probleem is opgelost.

* Zodra de code zich zoals verwacht gedraagt, wijs de code aan de git eigenschaptak toe.

* De code die aan RDE wordt gesynchroniseerd gebruikt geen pijpleiding van Cloud Manager zodat zou u nu een Cloud Manager non-production pijpleiding moeten gebruiken om de de eigenschaptak van de it aan de milieu van de Ontwikkeling van de Wolk op te stellen. Dit bevestigt dat de code de de kwaliteitsgates van Cloud Manager overgaat en u erop kunt vertrouwen de code later met succes gebruikend de de productiepijplijn van Cloud Manager wordt opgesteld.

* Herhaal bovenstaande stappen voor elke tussenliggende mijlpaal totdat alle code voor de functie gereed is en goed wordt uitgevoerd op zowel de RDE als de Cloud Development-omgeving.

* Implementeer de code via de Cloud Manager-productiepijplijn naar de productie.

## RDE gebruiken om een Bestaande Eigenschap te zuiveren {#use-rde-to-debug-an-existing-feature}

Het werkschema is gelijkaardig aan het ontwikkelen van een nieuwe eigenschap. Het verschil is dat de code die wordt gesynchroniseerd met RDE het git-label zou weerspiegelen van wat er naar de omgeving werd geduwd waar het probleem is gevonden. Bovendien kan het nuttig zijn om inhoud op te stellen die de stroomopwaartse milieu aanpast. Dit kan worden bereikt door inhoudspakketten te exporteren en te importeren.

## Meerdere ontwikkelaars die samenwerken op dezelfde RDE {#multiple-developers-collaborating-on-the-same-rde}

RDE steunt één enkel project tegelijkertijd. Aangezien de code van een lokale ontwikkelomgeving aan het milieu RDE wordt gesynchroniseerd, is het het meest natuurlijk voor één ontwikkelaar om het op een bepaald ogenblik op zich te gebruiken.

Met zorgvuldige coördinatie is het echter mogelijk dat meerdere ontwikkelaars een specifieke functie valideren of fouten in een specifiek probleem opsporen. De sleutel is dat elke ontwikkelaar hun lokale projecten synchroon houdt zodat de codeveranderingen door een bepaalde ontwikkelaar worden aangebracht door de andere ontwikkelaars worden geabsorbeerd, anders zou één ontwikkelaar onbedoeld de code van andere kunnen overschrijven. De geadviseerde strategie is voor elke ontwikkelaar om hun veranderingen in een gedeelde git tak alvorens aan RDE te synchroniseren, zodat de andere ontwikkelaars de veranderingen trekken alvorens hun eigen veranderingen te maken.

## Opdrachten voor RDE-opdrachtregelprogramma&#39;s {#rde-cli-commands}

### Help/algemene informatie {#help}

* Voor een lijst met opdrachten typt u:

  `aio aem:rde`

* Voor gedetailleerde hulp voor een bevel, type:

  `aio aem rde <command> --help`

### Globale vlaggen {#global-flags}

* Voor een minder uitgebreide uitvoer gebruikt u de stille markering:

  `aio aem rde <command> --quiet`

  Hierdoor worden bepaalde elementen, zoals spinners en voortgangsbalken, verwijderd en wordt de gebruikersinvoer beperkt.

* Voor JSON in plaats van de output van het consolelogboek, gebruik de json vlag:

  `aio aem rde <command> --json`

  Dit keert geldige JSON terwijl het onderdrukken van om het even welke consoleoutput terug. Zie de JSON-voorbeelden verderop.

* Om te vermijden vormend de de verbindingsinformatie van RDE gebruikend het opstellingsbevel, of om het even welke verwezenlijking van de AIR config, gebruik de drie vlaggen voor organisatie, programma en milieu:

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  Hiervoor moet nog steeds een ```aio login``` worden uitgevoerd.

### Distribueren naar RDE {#deploying-to-rde}

Deze sectie beschrijft het gebruiken van RDE CLI voor het opstellen van, het installeren van, of het bijwerken van bundels, configuraties OSGI, inhoudspakketten, individuele inhoudsdossiers, en configuraties Apache of Dispatcher.

Het algemene gebruikspatroon is `aio aem:rde:install <artifact>` .

Hieronder vindt u enkele voorbeelden:

#### Een inhoudspakket implementeren {#deploy-content-package}

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

De reactie voor een succesvolle plaatsing lijkt op het volgende:

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

U kunt desgewenst naar een externe opslagplaats verwijzen:

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Artefacten worden standaard geïmplementeerd op zowel auteur- als publicatieniveaus, maar de markering &#39;-s&#39; kan worden gebruikt om een specifieke laag als doel in te stellen.

Om het even welk AEM pakket kan worden opgesteld, zoals pakketten met code, inhoud, of a [ containerpakket ](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (ook genoemd het &quot;alle&quot;pakket).

>[!IMPORTANT]
>
>De Dispatcher-configuratie voor het WKND-project wordt niet geïmplementeerd via de bovenstaande installatie van het inhoudspakket. Implementeer deze afzonderlijk volgens de stappen &quot;Apache/Dispatcher Configuration implementeren&quot;.

#### Het opstellen van een Configuratie OSGI {#deploy-OSGI-config}

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

#### Een bundel implementeren {#deploy-bundle}

Om een bundel op te stellen, gebruik:

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

#### Inhoudsbestanden gebruiken {#deploy-content-file}

Als u een inhoudsbestand wilt implementeren, gebruikt u:

`aio aem:rde:install world.txt -p /apps/hello.txt`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

#### Een Apache/Dispatcher-configuratie implementeren {#deploy-apache-config}

Voor dit type configuratie moet de volledige mapstructuur de vorm hebben van een ZIP-bestand.

In de module `dispatcher` van een AEM project kunt u de Dispatcher-configuratie comprimeren door de onderstaande toegewezen opdracht uit te voeren:

`mvn clean package`

Of u gebruikt de opdracht onder zip vanuit de map `src` van de module `dispatcher` :

`zip -y -r dispatcher.zip .`

Dan stel de configuratie door dit bevel op:

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>Het bovenstaande bevel veronderstelt u de [ configuraties van Dispatcher van het 1} project van WKND {. ](https://github.com/adobe/aem-guides-wknd) Vervang `X.X.X` door het corresponderende WKND-projectversienummer of uw projectspecifieke versienummer wanneer u de Dispatcher-configuratie van uw project implementeert.

>[!NOTE]
>
>RDE ondersteunt de Dispatcher-configuratie &quot;Flexible Mode&quot;, maar niet de Dispatcher-configuratie &quot;Legacy mode&quot;. Zie {de documentatie van 0} Dispatcher ](/help/implementing/dispatcher/disp-overview.md#validation-debug) voor informatie over de twee wijzen. [ U kunt de documentatie ook raadplegen over [ migrerend aan Flexibele wijze ](/help/implementing/dispatcher/validation-debug.md#migrating), als u dit niet reeds hebt gedaan.

Een succesvolle plaatsing produceert een reactie die op het volgende lijkt:

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

De code die aan RDE wordt opgesteld ondergaat geen pijpleiding van Cloud Manager en zijn bijbehorende kwaliteitspoorten. De code doorloopt echter wel een analyse, die de fouten rapporteert, zoals in het onderstaande codevoorbeeld wordt geïllustreerd:

```
$ aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar
...
#19: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D74FR1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
Logs:
The analyser found the following errors for author :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
The analyser found the following errors for publish :
[requirements-capabilities] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Artifact com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8 requires [org.apache.felix.gogo.jline/1.1.8] org.apache.felix.gogo; filter:="(&(org.apache.felix.gogo=command.implementation)(version>=1.0.0)(!(version>=2.0.0)))"; effective:=active in start level 20 but no artifact is providing a matching capability in this start level.
[api-regions-exportsimports] com.adobe.aem.temp:org.apache.felix.gogo.jline:1.1.8: Bundle org.apache.felix.gogo.jline:1.1.8 is importing package(s) [org.jline.builtins, org.jline.utils, org.apache.felix.service.command, org.apache.felix.service.threadio, org.jline.terminal, org.jline.reader, org.apache.felix.gogo.runtime, org.jline.reader.impl] in start level 20 but no bundle is exporting these for that start level.
```

Het bovenstaande codevoorbeeld illustreert het gedrag als een bundel niet oplost. In dat geval wordt het &quot;gefaseerd&quot; en wordt het alleen geïnstalleerd als aan de vereisten ervan (ontbrekende invoer, in dit geval) wordt voldaan door de installatie van andere code.

#### Het opstellen van de verwante configuratie van de Pijpleiding Config (yaml vormt) {#deploy-config-pipeline}

De milieu-specifieke configuraties (één of meerdere yaml dossiers) die in het artikel [ worden beschreven Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md) kunnen als volgt worden opgesteld:

`aio aem:rde:install -t env-config ./my-config-folder`
waarbij my-config-folder de ouderomslag is die uw yaml configuraties bevat.

U kunt ook een ZIP-bestand met de mapstructuur config installeren:

`aio aem:rde:install -t env-config config.zip`

Merk op dat de serie envTypes van het yaml dossier de waarde *zou moeten omvatten*, zoals in het hieronder voorbeeld:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["rde"]
```

### Voorste code implementeren op basis van sitethema&#39;s en sitesjablonen {#deploying-themes-to-rde}

RDEs steunt front-end code die op [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebaseerd. Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn om voorste pakketten op te stellen, eerder dan de voorste-EindPijpleiding van Cloud Manager [ ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) die voor andere milieutypes wordt gebruikt.

Zoals gebruikelijk, bouw uw front-end pakket gebruikend npm:

`npm run build`

Er moet een `dist/` -map worden gegenereerd, dus uw front-end pakketmap moet een `package.json` bestand en `dist` -map bevatten:

```
ls ./path-to-frontend-pkg-folder/
...
dist
package.json
```
Nu bent u bereid om het front-end pakket aan RDE op te stellen door aan de front-end pakketomslag te richten:

```
aio aem:rde:install -t frontend ./path-to-frontend-pkg-folder/
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

U kunt ook het bestand `package.json` en de map `dist` comprimeren en dat ZIP-bestand implementeren:

`zip -r frontend-pkg.zip ./path-to-frontend-pkg-folder/dist ./path-to-frontend-pkg-folder/package.json`

```
aio aem:rde:install -t frontend frontend-pkg.zip
...
#1: deploy completed for frontend frontend-pipeline.zip on author,publish - done by ... at 2024-01-18T15:33:22.898Z
Logs:
> Deployed artifact wknd-1.0.0-1705592008-26e7ec1a
> with workspace hash 692021864642a20d6d298044a927d66c0d9cf2adf42d4cca0c800a378ac3f8d3
```

>[!NOTE]
>
>De naamgeving van de bestanden in het front-end pakket moet voldoen aan de volgende naamgevingsconventies:
> * map &quot;dist&quot;, voor de npm-bouwuitvoerpakketmap
> * bestand &quot;package.json&quot;, voor het pakket voor npm-afhankelijkheden

>[!TIP]
>
> Als u RDE vóór April 2023 creeerde en de fout &quot;UNEXPECTED_API_ERROR&quot;ervaren wanneer het proberen van de frontend eigenschap voor het eerst, gelieve te proberen om uw milieu te schrappen en het opnieuw tot stand te brengen.

### De status van de RDE controleren {#checking-rde-status}

U kunt RDE CLI gebruiken om te controleren of het milieu klaar is om aan worden opgesteld, aangezien welke plaatsingen door middel van het elektrische toestel van RDE zijn gemaakt.

Uitvoeren:

`aio aem:rde:status`

Retourneert het volgende:

```
Info for cm-p12345-e987654
Environment: Ready
- Bundles Author:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Bundles Publish:
 com.adobe.granite.sample.demo-1.0.0.SNAPSHOT
- Configurations Author:
 com.adobe.granite.demo.MyServlet
- Configurations Publish:
 com.adobe.granite.demo.MyServlet
```

Als het bevel een nota over instanties terugkeert die opstellen, kunt u nog gaan en de volgende update uitvoeren, maar uw laatste zou nog niet op de instantie zichtbaar kunnen zijn.

### Implementatiegeschiedenis tonen {#show-deployment-history}

U kunt de geschiedenis van plaatsingen controleren die aan RDE door te lopen worden gemaakt:

`aio aem:rde:history`

Deze geeft een antwoord in de vorm van:

`#1: deploy completed for content-package aem-guides-wknd.all-2.1.0.zip on author,publish - done by 029039A55D4DE16A0A494025@AdobeID at 2022-09-12T14:41:55.393Z`

### Verwijderen uit RDE {#deleting-from-rde}

U kunt configuraties en bundels schrappen die eerder aan RDE door middel van CLI hulpmiddelen zijn opgesteld. Gebruik de opdracht `status` voor een lijst met items die kunnen worden verwijderd, waaronder `bsn` for bundles en `pid` voor configuraties waarnaar wordt verwezen in de opdracht delete.

Bijvoorbeeld, als `com.adobe.granite.demo.MyServlet.cfg.json` is geïnstalleerd, is `bsn` enkel `com.adobe.granite.demo.MyServlet`, zonder het {**achtervoegsel 3} cfg.json.**

Verwijderen van inhoudspakketten of inhoudsbestanden wordt niet ondersteund. Om hen te verwijderen, zou RDE moeten worden teruggesteld, die het aan een standaardstaat terugkeert.

Zie het onderstaande voorbeeld voor meer informatie:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Voor meer informatie en demonstratie, zie het videoleerprogramma [ hoe te om de bevelen van RDE (10:01) te gebruiken ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html).

## Logboeken {#rde-logging}

Gelijkaardig aan andere milieutypes, kunnen de logboekniveaus worden geplaatst door configuraties te wijzigen OSGi, hoewel zoals hierboven beschreven, het plaatsingsmodel voor RDEs een bevellijn eerder dan een plaatsing van Cloud Manager impliceert. Controleer de [ registrerendocumentatie ](/help/implementing/developing/introduction/logging.md) voor meer informatie over hoe te om, logboeken te bekijken te downloaden en te interpreteren.

RDE CLI heeft ook zijn eigen logboekbevel dat kan worden gebruikt om snel te vormen welke klassen en pakketten zouden moeten worden geregistreerd, en op welk logboekniveau. Deze configuraties kunnen als letterlijk worden beschouwd, aangezien zij niet de eigenschappen OSGI in versiecontrole wijzigen. Deze functie is gericht op het in real time stammen van logboeken in plaats van het omhoog kijken van logboeken van het verre verleden.

In het volgende voorbeeld wordt getoond hoe u de auteurslaag kunt staart, met één pakket dat is ingesteld op een logniveau voor foutopsporing en twee pakketten (gescheiden door spaties) die zijn ingesteld op een niveau voor foutopsporing voor info. Output die een **auth** pakket omvat wordt benadrukt.

`aio aem:rde:logs --target=author --debug=org.apache.sling --info=org.apache.sling.commons.threads.impl org.apache.sling.jcr.resource.internal.helper.jcr -H .auth.`

>[!TIP]
>
>Als de fout `RDECLI:UNEXPECTED_API_ERROR` wordt weergegeven bij het afspelen met de logboekopdrachten voor de auteurservice, moet u de omgeving opnieuw instellen en het opnieuw proberen. Deze fout treedt op als uw laatste herstelbewerking voor eind mei 2024 is uitgevoerd.
>
>```
>aio aem:rde:reset
>```

Zie `aio aem:rde:logs --help` voor de volledige reeks opties voor de opdrachtregel.

Functies:

* logboekniveaus declareren op een pakket- of klassenniveau
* het aanpassen van het formaat van de logboekoutput
* die tot vier huidige logboekconfiguraties opmaken, elk in zijn eigen terminal
* markeren, specifieke logbestanden

Merk op dat de logboeken in geheugen op RDE worden opgeslagen en deze logboeken worden gerecycled en zo worden verworpen als zij niet worden gesleept of als het netwerk te langzaam is.


## Herstellen {#reset-rde}

Als u de RDE opnieuw instelt, verwijdert u alle aangepaste code, configuraties en inhoud van zowel de auteur- als de publicatieversie. Dit terugstellen is bijvoorbeeld nuttig, als RDE is gebruikt om een specifieke eigenschap te testen en u het aan een standaardstaat wilt terugstellen zodat kunt u een verschillende eigenschap testen.

Met een reset wordt de RDE ingesteld op de laatst beschikbare AEM versie.

Het terugstellen kan als [ Cloud Manager ](#reset-the-rde-cloud-manager) of als [ bevellijn ](#reset-the-rde-command-line) worden gedaan. Het opnieuw instellen duurt een paar minuten en alle bestaande inhoud en code wordt verwijderd uit de RDE.

>[ NOTA!]
>
>U moet de Cloud Manager Developer-rol krijgen toegewezen om de functie reset te kunnen gebruiken. Als dat niet het geval is, leidt een herstelactie tot een fout.

### RDE via opdrachtregel opnieuw instellen {#reset-the-rde-command-line}

U kunt RDE terugstellen en het terugkeren aan een standaardstaat door in werking te stellen:

`aio aem:rde:reset`

Dit duurt meestal een paar minuten en ```Environment reset.``` wordt gerapporteerd wanneer dit is gelukt of ```Failed to reset the environment.``` wanneer er fouten zijn opgetreden. Zie het onderstaande hoofdstuk over ```--json``` uitvoer voor een gestructureerde uitvoer.

Gebruik het [ statusbevel ](#checking-rde-status) om te controleren wanneer het milieu opnieuw klaar is.

### De RDE in Cloud Manager opnieuw instellen {#reset-the-rde-cloud-manager}

U kunt Cloud Manager gebruiken om uw RDE opnieuw in te stellen door de volgende stappen te volgen:

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik het programma waarvoor u RDE wilt terugstellen.

1. Van de **pagina van het Overzicht**, klik het **milieu&#39;s** lusje bij de bovenkant van het scherm.

   ![ Milieu&#39;s tabel ](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Alternatief, klik **tonen Al** knoop op de **** kaart van Milieu&#39;s {om rechtstreeks aan het **Milieu** lusje te springen.

     ![ toon alle optie ](/help/implementing/cloud-manager/assets/environment-showall.png)

1. Het **venster van Milieu&#39;s** opent en maakt een lijst van alle milieu&#39;s voor het programma.

   ![ het milieu tabel ](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Klik de elliptische knoop van RDE die u wilt terugstellen, en dan selecteren **Terugstellen**.

   ![ het omgevingsdetails van de Mening ](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Bevestig dat u RDE wilt terugstellen door **Terugstellen** in de dialoog te klikken.

   ![ bevestigt terugstellen ](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager bevestigt door middel van een bannermelding dat het herstelproces is gestart.

   ![ Bannerbericht van het Terugstellen ](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Nadat het RDE-herstelproces is gestart, duurt het meestal een paar minuten om de omgeving te voltooien en terug te zetten naar de standaardtoestand. De status van het terugstellingsproces kan op elk ogenblik in de **kolom van de Status** van de **** kaart van Milieu&#39;s {of in het **milieu&#39;s** venster worden bekeken.

![ RDE terugstellingstatus ](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

U kunt RDE ook terugstellen gebruikend de elliptische knoop direct van de **1} kaart van Milieu&#39;s {op de** Overzicht **pagina.**

![ RDE van het Terugstellen van de kaart van Milieu ](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Voor meer informatie over hoe te om Cloud Manager te gebruiken om uw milieu&#39;s te beheren, zie [ de documentatie van Cloud Manager ](/help/implementing/cloud-manager/manage-environments.md).

## Opdrachten die JSON-uitvoer ondersteunen {#json-commands}

De meeste opdrachten ondersteunen de algemene markering ```--json``` , die de uitvoer van de console onderdrukt en geldige items retourneert die in scripts moeten worden verwerkt. Hieronder vindt u enkele ondersteunde opdrachten, met voorbeelden van de json-uitvoer.

### Status {#status}

<details>
  <summary>Uitbreiden om statusvoorbeelden weer te geven</summary>

#### Een schone RDE {#clean-rde}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Modification in progress | Deployment in progress | Upload in progress | Ready (instances are currently deploying) | Ready",
  "author": {
    "osgiBundles": [],
    "osgiConfigs": []
  },
  "publish": {
    "osgiBundles": [],
    "osgiConfigs": []
  }
}
```

#### Een RDE met sommige geïnstalleerde bundels {#rde-installed-bundles}

```$ aio aem rde status --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "author": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  },
  "publish": {
    "osgiBundles": [
      {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "updateId": "80",
        "service": "author",
        "type": "osgi-bundle",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        }
      }
    ],
    "osgiConfigs": [
      {
        "id": "publish_osgi-config_com.adobe.granite.demo.MyServlet",
        "updateId": "80",
        "service": "publish",
        "type": "osgi-config",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "configPid": "com.adobe.granite.demo.MyServlet"
        }
      }
    ]
  }
}
```

</details>

### Installeren {#install}

<details>
  <summary>Uitbreiden om voorbeelden van Installeren te bekijken</summary>

```$ aio aem rde install ~/Downloads/hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "4",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:30:44.578Z",
        "processed": "2024-05-21T12:31:07.886468Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Verwijderen {#delete}

<details>
  <summary>Uitbreiden om voorbeelden van verwijderen weer te geven</summary>

```$ aio aem rde delete com.adobe.granite.hotdev.demo-1.0.0.SNAPSHOT --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "items": [
    {
      "updateId": "84",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:16.889Z",
        "processed": "2024-05-21T11:49:18.188420Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    },
    {
      "updateId": "85",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T11:49:23.857Z",
        "processed": "2024-05-21T11:49:25.237930Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "83"
      },
      "hash": "636f6d2e",
      "logs": [
        "No logs available for this update."
      ]
    }
  ]
}
```

</details>

### Historie {#history}

<details>
  <summary>Uitbreiden om historievoorbeelden weer te geven</summary>

```$ aio aem rde history --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "Ready",
  "items": [
    {
      "updateId": "112",
      "info": "delete publish_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:07.934Z",
        "processed": "2024-05-21T12:53:09.118766Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "publish_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "publish",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "111",
      "info": "delete author_osgi-bundle_com.adobe.granite.hotdev.demo",
      "action": "delete",
      "metadata": {},
      "services": [
        "author"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:53:00.824Z",
        "processed": "2024-05-21T12:53:02.101560Z"
      },
      "user": "userId",
      "type": "osgi-bundle",
      "deletedArtifact": {
        "id": "author_osgi-bundle_com.adobe.granite.hotdev.demo",
        "metadata": {
          "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip",
          "bundleSymbolicName": "com.adobe.granite.hotdev.demo",
          "bundleName": "HotDev Bundle",
          "bundleVersion": "1.0.0.SNAPSHOT"
        },
        "service": "author",
        "type": "osgi-bundle",
        "updateId": "110"
      },
      "hash": "636f6d2e"
    },
    {
      "updateId": "110",
      "info": "deploy",
      "action": "deploy",
      "metadata": {
        "name": "hotdev.demo.ui.apps.all-1.0.0-SNAPSHOT.zip"
      },
      "services": [
        "author",
        "publish"
      ],
      "status": "completed",
      "timestamps": {
        "received": "2024-05-21T12:52:12.123Z",
        "processed": "2024-05-21T12:52:31.026147Z"
      },
      "user": "userId",
      "type": "content-package",
      "hash": "2ad73507"
    }
  ]
}
```

</details>

### Herstellen {#reset}

<details>
  <summary>Uitbreiden om voorbeelden opnieuw instellen weer te geven</summary>

#### Vuur en vergeten, geen wachttijd {#fire-no-wait}

```$ aio aem rde reset --no-wait --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "resetting"
}
```

#### Wachten op voltooien, opnieuw instellen geslaagd {#wait-success}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```

#### Wachten op voltooien, opnieuw instellen mislukt {#wait-failed}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset_failed"
}
```

</details>

### Opnieuw starten {#restart}

<details>
  <summary>Uitbreiden om voorbeelden van Opnieuw starten weer te geven</summary>

```$ aio aem rde restart --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "restarted"
}
```

</details>

## Modi uitvoeren {#runmodes}

RDE-specifieke configuratie OSGI kan worden toegepast door achtervoegsels op de omslagnaam te gebruiken, zoals in de voorbeelden hieronder:

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Zie de [ documentatie van de looppaswijze ](/help/implementing/deploying/overview.md#runmodes) voor algemene informatie over looppaswijzen.

>[!NOTE]
>
>De configuratie van RDE OSGI is uniek in die zin dat het de waarden van om het even welke eigenschappen overerft OSGI die door de `dev` loopgebiedwijze van de bundel worden verklaard.

RDE&#39;s verschillen van andere omgevingen omdat inhoud kan worden geïnstalleerd in de map install.load (of install.auteur.rde of install.publish.rde) onder /apps. Dit laat u inhoud aan git begaan en het leveren aan RDE gebruikend het bevel-lijn hulpmiddel.

## vullen met inhoud {#populating-content}

Wanneer een RDE wordt teruggesteld, wordt al inhoud verwijderd en zo zo, zo moet de expliciete actie worden genomen om inhoud toe te voegen. Als beste praktijken, overweeg het assembleren van een reeks inhoud die als testinhoud voor het bevestigen van of het zuiveren eigenschappen in RDE moet worden gebruikt. Er zijn verscheidene mogelijke strategieën om RDE met die inhoud te bevolken:

1. Synchroniseer het inhoudspakket uitdrukkelijk aan RDE gebruikend bevel-lijn het gebruiken

1. Plaats en wijs de steekproefinhoud in git binnen een install.rde omslag onder /apps toe en synchroniseer dan het overkoepelende inhoudspakket aan RDE gebruikend het bevel-lijn hulpmiddel.

1. Gebruik het [ hulpmiddel van het inhoudsexemplaar ](/help/implementing/developing/tools/content-copy.md) om een bepaalde inhoud te kopiëren die van prod, stadium, of ontwikkelt milieu&#39;s, of van een andere RDE wordt geplaatst.

1. Pakketbeheer gebruiken

U kunt maximaal 1 GB gebruiken bij het synchroniseren van inhoudspakketten.


## Hoe verschillen RDE&#39;s van Cloud Development Environment? {#how-are-rds-different-from-cloud-development-environments}

Terwijl RDE in vele opzichten gelijkaardig aan een Milieu van de Ontwikkeling van de Wolk is, zijn er sommige kleine architecturale verschillen om voor snelle synchronisatie van code toe te staan. Het mechanisme om code aan RDE te krijgen is verschillend — voor RDEs, één syncs code van een lokale ontwikkelomgeving, terwijl voor de Milieu van de Ontwikkeling van de Wolk, één code door Cloud Manager opstelt.

Om deze redenen, adviseert men dat na het bevestigen van code op een milieu RDE, u de code aan een Milieu van de Ontwikkeling van de Wolk zou moeten opstellen gebruikend de niet productiepijplijn. Tot slot test de code alvorens met de productiepijpleiding op te stellen.

Houd ook rekening met het volgende:

* RDE&#39;s bevatten geen voorvertoningsniveau
* RDEs steunt momenteel niet het prereleasekanaal.


## Hoeveel RDEs heb ik nodig? {#how-many-rds-do-i-need}

RDE is beschikbaar voor elke vergunning gegeven oplossing en de Adobe biedt ook extra RDEs aan, die voor Productie (niet zandbak) programma&#39;s kan worden vergunning gegeven.

Het aantal vereiste RDEs hangt van de samenstelling en de processen van een organisatie af. Het meest flexibele model is waar een organisatie een specifieke RDE voor elk van hun ontwikkelaars van AEM Cloud Service koopt. In dit model, kan elke ontwikkelaar hun code op RDE testen zonder met andere teamleden rond te coördineren of een milieu RDE beschikbaar is.

Aan de andere kant kan een team met één RDE interne processen gebruiken om te coördineren welke ontwikkelaars de omgeving op een bepaald moment kunnen gebruiken. Dit kan mogelijk altijd zijn wanneer een ontwikkelaar een mijlpaal voor tussentijdse functies heeft bereikt en klaar is om te valideren in een Cloud-omgeving waar hij snel de benodigde wijzigingen kan aanbrengen.

Een ingebouwd model is een model waarbij een organisatie verschillende RDE&#39;s koopt, zodat er een grotere kans is dat een ongebruikte RDE beschikbaar is. Eén strategie zou kunnen bestaan uit het toewijzen van een RDE per rumteam of belangrijke functie. Interne processen kunnen worden gebruikt om het gebruik van de omgevingen te coördineren.

## Hoe verschilt een AEM Forms Cloud Service Rapid Development Environment (RDE) van andere omgevingen? {#how-are-forms-rds-different-from-cloud-development-environments}

Forms-ontwikkelaars kunnen AEM Forms Cloud Service Rapid Development Environment gebruiken om snel Adaptive Forms, Workflows en aanpassingen te ontwikkelen, zoals het aanpassen van kerncomponenten, integratie met systemen van derden en meer. De AEM Forms Cloud Service Rapid Development Environment (RDE) biedt geen ondersteuning voor communicatie-API&#39;s. Het biedt ook geen ondersteuning voor functies en mogelijkheden die Documenten van Record vereisen, zoals het genereren van een Document of Record bij het verzenden van een adaptief formulier. De hieronder vermelde AEM Forms-functies zijn niet beschikbaar in een Rapid Development Environment (RDE):

* Een recorddocument configureren voor een adaptief formulier
* Een document met records genereren bij het indienen van een adaptief formulier of met een workflowstap
* Document verzenden als bijlage bij Record met de handeling Verzenden via e-mail of met de stap E-mail in een workflow
* Adobe Sign gebruiken in een adaptief formulier of in een workflowstap
* Communicatie-API&#39;s

>[!NOTE]
>
> Er is geen verschil tussen de interface van Rapid Development Environment (RDE) en andere Cloud Service omgevingen voor Forms. Alle aan het document van Verslag verwante opties, zoals het selecteren van een document van verslagmalplaatje voor een adaptief vorm, blijven in UI verschijnen. Deze omgevingen hebben geen communicatie-API&#39;s en documentmogelijkheden om dergelijke opties te testen. Als u dus een optie kiest waarvoor communicatie-API&#39;s of de functie Document of Record vereist is, wordt geen actie uitgevoerd en wordt een foutbericht weergegeven.

## RDE-zelfstudie

Om over RDE in AEM as a Cloud Service te leren, zie het videoleerprogramma dat [ toont hoe te opstelling, hoe te om het te gebruiken, en de cyclus van het ontwikkelingsleven (01:25) ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/overview.html).

# Problemen oplossen {#troubleshooting}

## RDE-problemen oplossen (#rde-troublehooting)

### Hoe te om de recentste AEM versie voor bestaande RDE te verkrijgen {#get-latest-aem-version}

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare Adobe Experience Manager-versie (AEM). Een [ teruggestelde RDE, ](#reset-rde) die kan worden uitgevoerd gebruikend Cloud Manager of het `aio aem:rde:reset` bevel, cycli RDE en plaats het aan de onlangs-beschikbare AEM versie.

## Problemen met de insteekmodule AIR RDE oplossen {#aio-rde-plugin-troubleshooting}

### Fouten met betrekking tot ontoereikende machtigingen {#insufficient-permissions}

Om de stop van RDE te gebruiken, vereist het u om een lid van de Ontwikkelaar van Cloud Manager **te zijn - Cloud Service** Profiel van het Product. Zie [ de Leden van het Team aan de Profielen van het Product van Cloud Manager toewijzen - wijs het Profiel van het Product van de Ontwikkelaar ](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer details toe.

Alternatief, kunt u bevestigen dat u deze ontwikkelaarrol hebt als u login aan de ontwikkelaarsconsole kunt door dit bevel in werking te stellen:

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>Als u de `Warning: cloudmanager:* is not a aio command.` fout ziet, moet u [ aio-cli-stop-cloudmanager ](https://github.com/adobe/aio-cli-plugin-cloudmanager) installeren door het hieronder bevel in werking te stellen:
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

Controleren of de aanmelding is voltooid door uitvoering

`aio cloudmanager:list-programs`

Dit zou van alle programma&#39;s onder uw gevormde organisatie moeten een lijst maken en bevestigen dat u de correcte toegewezen rol hebt.

### Afgekeurde context &#39;aio-cli-plugin-cloudmanager&#39; gebruiken {#aio-rde-plugin-troubleshooting-deprecatedcontext}

Vanwege de geschiedenis van de &#39;aio-cli-plugin-aem-rde&#39; werd de contextnaam &#39;aio-cli-plugin-cloudmanager&#39; al een tijd gebruikt. De rode plug-in gebruikt nu de IMS-manier om te gaan met contextinformatie, wat betekent dat er opties zijn om contextinformatie globaal of lokaal op te slaan en dat alle AIR-aanroepen standaard worden uitgevoerd als u dat wilt. De standaard gevormde context wordt plaatselijk opgeslagen en laat de ontwikkelaars toe om individuele contexten en hun informatie binnen een omslag te volgen en te gebruiken. Voor verdere details, lees [ het voorbeeld aan opstelling hierboven een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools).

Ontwikkelaars die beide plug-ins gebruiken, de air-cli-plugin-cloudmanager en de air-cli-plugin-aem-mode gebruiken en alle informatie in dezelfde context willen houden, moeten nu opties hebben:

#### Context &#39;air-cli-plugin-cloudmanager&#39; blijven gebruiken

De context kan nog steeds worden gebruikt. In de RDE-plug-in wordt een afleidingswaarschuwing weergegeven. Deze waarschuwing kan worden weggelaten in de modus ```--quiet``` . Recentere versies van de RDE-plug-in bieden geen fallback om de context &#39;aio-cli-plugin-cloudmanager&#39; meer te lezen. Om nog gebruik van het te maken, vorm eenvoudig de standaardcontext aan &#39;air-cli-stop-cloudmanager&#39;, zie [ het voorbeeld aan opstelling een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) hierboven.

#### Gebruik een andere contextnaam ook voor de plug-in voor cloud Manager

De insteekmodules van de cloud Manager bieden een parameter om een context te definiëren die moet worden gebruikt. De standaard IMS-contextconfiguratie wordt nog niet ondersteund. Om dit te doen, vorm de insteekmodule RDE gebruikend [ het voorbeeld om een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) te opstelling en vertelt de insteekmodule van de wolkenmanager om &quot;myContext&quot;als ```--imsContextName=myContext``` in elke vraag aan het te gebruiken.
