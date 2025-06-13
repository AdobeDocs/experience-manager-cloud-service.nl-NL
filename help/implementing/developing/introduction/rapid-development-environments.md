---
title: Snelle ontwikkelomgevingen
description: Leer hoe u Rapid Development Environment kunt gebruiken voor snelle ontwikkelherhalingen in een cloudomgeving.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 5db419e674ceb3c861f53a19e7b852c89ebd3702
workflow-type: tm+mt
source-wordcount: '5391'
ht-degree: 0%

---

# Snelle ontwikkelomgevingen {#rapid-development-environments}

Om veranderingen op te stellen, vereisen de huidige milieu&#39;s van de Ontwikkeling van de Wolk het gebruik van een proces dat uitgebreide codeveiligheid en kwaliteitsregels gebruikt genoemd een pijpleiding CI/CD. Voor situaties waar snelle en iteratieve veranderingen nodig zijn, heeft Adobe Rapid Development Environment (RDE&#39;s voor korte tijd) geïntroduceerd.

RDEs laat ontwikkelaars snel veranderingen opstellen en herzien, die de hoeveelheid tijd minimaliseren nodig om eigenschappen te testen die om in een lokale ontwikkelomgeving worden bewezen te werken.

Zodra de veranderingen in RDE zijn getest, kunnen zij aan een regelmatige milieu van de Ontwikkeling van de Wolk door de pijpleiding van Cloud Manager worden opgesteld.

>[!NOTE]
> Krijg in contact met de ontwikkelaars van RDE op Adobe [ kanaal van de Opsporing ](https://discord.com/channels/1131492224371277874/1245304281184079872). Voel vrij om het even welke vragen te stellen of terugkoppelen betreffende onderwerpen RDE.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


U kunt extra video&#39;s zien die [ tonen hoe te om het ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup), [ te plaatsen hoe te om het ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use) te gebruiken, en de [ cyclus van het ontwikkelingsleven ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle) gebruikend RDE.

## Inleiding {#introduction}

RDEs kan voor code, inhoud, en Apache of Dispatcher configuraties worden gebruikt. In tegenstelling tot gewone Cloud Development-omgevingen kunnen ontwikkelaars lokale opdrachtregelprogramma&#39;s gebruiken om code die lokaal is gemaakt te synchroniseren met een RDE.

Elk programma wordt voorzien van RDE. Als er Sandbox-accounts zijn, worden deze na een paar uur niet meer gebruikt.

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare Adobe Experience Manager (AEM)-versie. Een RDE-reset, die kan worden uitgevoerd met Cloud Manager, fietst de RDE en stelt deze in op de meest recente beschikbare AEM-versie.

Typisch, wordt RDE gebruikt door één enkele ontwikkelaar in een bepaald tijd, voor het testen van en het zuiveren van een specifieke eigenschap. Wanneer de ontwikkelingszitting wordt gedaan, kan RDE in een standaardstaat voor het volgende gebruik worden teruggesteld.

Aanvullende RDE&#39;s kunnen in licentie worden gegeven voor productieprogramma&#39;s (niet-sandbox).

## RDE inschakelen in een programma {#enabling-rde-in-a-program}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik het programma waaraan u RDE wilt toevoegen om zijn details te tonen.

   * RDEs kan aan zowel [ zandbakprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) als [ productieprogramma&#39;s ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md) worden toegevoegd.

1. Van de **pagina van het Overzicht van het Programma**, op de **&#x200B;**&#x200B;kaart van Milieu&#39;s, klik **voegt Milieu** toe.

   ![ kaart van Milieu&#39;s ](/help/implementing/cloud-manager/assets/no-environments.png)

   * **voegt de optie van het Milieu** toe is ook beschikbaar op **Milieu** tabel.

     ![ Milieu&#39;s tabel ](/help/implementing/cloud-manager/assets/environments-tab.png)

   * **voeg Milieu** optie toe kan wegens gebrek aan toestemmingen of afhankelijk van de vergunning gegeven middelen worden onbruikbaar gemaakt.

1. In **voeg milieu** dialoogdoos toe, doe het volgende:

   * Selecteer **Snelle Ontwikkeling** onder de **Uitgezochte milieu type** rubriek.
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes achter het omgevingstype weergegeven.
   * Verstrek a **Naam** voor het milieu.
   * Verstrek een facultatieve **Beschrijving** voor het milieu.
   * Selecteer het Gebied van de a **Wolk**.

   ![ voeg milieudialoog ](/help/implementing/cloud-manager/assets/add-environment-wizard.png) toe

1. Klik **sparen** om het gespecificeerde milieu toe te voegen.

Het **scherm van het Overzicht** toont nu uw nieuw milieu in de **&#x200B;**&#x200B;kaart van Milieu&#39;s.

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare AEM-versie. Een RDE-reset, die ook kan worden uitgevoerd met Cloud Manager, fietst de RDE en stelt deze in op de laatst beschikbare AEM-versie.

Voor meer informatie over het gebruiken van Cloud Manager om milieu&#39;s tot stand te brengen, wie toegang tot hen heeft, en douanedomeinen toe te wijzen, zie [ Programma&#39;s en de Types van Programma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) in de documentatie van Cloud Manager.

## De RDE-opdrachtregelprogramma&#39;s installeren {#installing-the-rde-command-line-tools}

Nadat u een RDE voor uw programma gebruikend Cloud Manager hebt toegevoegd, kunt u met het in wisselwerking staan door de bevel-lijn hulpmiddelen te plaatsen zoals die in de volgende stappen worden beschreven:

>[!IMPORTANT]
>
>Zorg ervoor u versie 20 van [ geïnstalleerde Knoop en NPM ](https://nodejs.org/en/download/) voor CLI van Adobe I/O (AIO) en verwante steekmodules hebt om behoorlijk te werken.


1. Installeer de hulpmiddelen AIO CLI volgens deze [ procedure ](https://developer.adobe.com/app-builder/docs/guides/runtime_guides/tools/cli-install).
1. Installeer de AIO CLI-tools AEM RDE-insteekmodule:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Meld u aan met de Adobe I/O-client (AIO).

   ```
   aio login
   ```

   De login informatie (teken) wordt opgeslagen in de globale luchtvaartconfiguratie en steunt daarom slechts één login en organisatie. Voor het geval u veelvoudige RDEs wilt gebruiken die verschillende logins of organisaties vereisen, volg het hieronder voorbeeld introducerend contexten.

   <details><summary>Volg dit voorbeeld aan opstelling een lokale context voor één van uw logins van de RDE</summary>
   Voer de volgende stappen uit om de aanmeldingsgegevens lokaal op te slaan in een &grave;.aio'-bestand in de huidige map binnen een specifieke context. Een context is ook een slimme manier aan opstelling een milieu CI/CD of een manuscript.  Gebruik ten minste AIR versie 10.3.1 om van deze functie gebruik te maken. Werk deze bij met behulp van 'npm install -g @adobe/aio-cli'.

   Nu, creeer een context genoemd m `ycontext` die u als standaardcontext plaatst gebruikend de authlug alvorens het login bevel te roepen.

   ```
   aio config set --json -l "ims.contexts.mycontext" "{ cli.bare-output: false }"
   aio auth ctx -s mycontext
   aio login --no-open
   ```

   >[!NOTE]
   > De login bevel met de `--no-open` optie output een URL in de terminal in plaats van het openen van uw standaardbrowser. U kunt het met een **incognito** venster van uw browser kopiëren en openen. Hierdoor blijft de huidige sessie in het hoofdbrowservenster ongewijzigd, zodat u zich kunt aanmelden met de specifieke account en organisatie die voor uw taak zijn vereist.

   Met de eerste opdracht maakt u een nieuwe aanmeldingscontextconfiguratie met de naam `mycontext` in het lokale `.aio` -configuratiebestand (het bestand wordt indien nodig gemaakt). Met de tweede opdracht stelt u de context `mycontext` in als de &quot;huidige&quot; context, dat wil zeggen de standaardinstelling.

   Met deze configuratie op zijn plaats, slaat het login bevel automatisch de login tokens in de context `mycontext` op, en houdt zo het lokaal.

   U kunt meerdere contexten beheren door lokale configuraties in meerdere mappen te bewaren. Alternatief, is het ook mogelijk om veelvoudige context binnen één enkel configuratiedossier te plaatsen, en tussen hen te schakelen door de &quot;huidige&quot;context te veranderen.
   </details>

1. Configureer de RDE-plug-in om uw organisatie, programma en omgeving te gebruiken. De opstellingsbevel hieronder verstrekt interactief de gebruiker van een lijst van programma&#39;s in hun organisatie, en toont RDE milieu&#39;s in dat programma om van te kiezen.

   ```
   aio aem:rde:setup
   ```

   U kunt de installatiestap overslaan als u een gescripte omgeving gebruikt. In dat geval, omvat direct de organisatie, het programma, en milieuwaarden in elk bevel. [ zie hieronder bevelen RDE voor meer informatie ](#rde-cli-commands).

### Interactieve setup {#installing-the-rde-command-line-tools-interactive}

Het opstellingsbevel vraagt of zou de verstrekte configuratie plaatselijk of globaal moeten worden opgeslagen.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

Kies `no` naar

* sla de organisatie, het programma en het milieu globaal in uw configuratie van de lucht op.
* werken met slechts één RDE.

Kies `yes` om het volgende te doen:

* Sla de organisatie, het programma en de omgeving lokaal op in de huidige map, in een `.aio` -bestand. Deze aanpak is handig als u het bestand wilt toewijzen aan versiebeheer, zodat anderen die de Git-opslagplaats klonen deze kunnen gebruiken.
* Kan met vele RDEs werken, zodat het schakelen naar een andere folder die configuratie in plaats daarvan gebruikt.
* Gebruik de configuratie in een programmatic context zoals een manuscript, dat het kan van verwijzingen voorzien.


Zodra de lokale of globale configuratie wordt geselecteerd, probeert het opstellingsbevel om uw organisatie identiteitskaart van uw huidige login te lezen en dan de programma&#39;s van de organisatie te lezen. Als de organisatie niet kan worden gevonden, kunt u het manueel samen met sommige begeleiding ingaan.

```
Selected only organization: XYXYXYXYXYXYXYXXYY
retrieving programs of your organization ...
```

Nadat de programma&#39;s zijn opgehaald, kan de gebruiker een keuze maken in de lijst en filteren. Als het programma is geselecteerd, wordt een lijst met RDE-omgevingen weergegeven waaruit u kunt kiezen. Als er slechts één programma, of slechts één beschikbare milieu van RDE, of allebei is, wordt het automatisch geselecteerd.

Voer de volgende handelingen uit om de huidige omgevingscontext weer te geven:

```aio aem rde setup --show```

De opdracht reageert op een resultaat dat lijkt op het volgende:

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

### Handmatige installatieprocedure in een niet-interactieve omgeving {#manual-setup}

In omgevingen waar geen enkele gebruiker interactief de instellingsopdracht kan uitvoeren (zoals CI/CD of scripts), is handmatige configuratie vereist. U kunt de parameters voor organisatie, programma en omgeving instellen met de onderstaande stappen.


<details>
  <summary>Vouw uit om details te zoeken over het handmatig configureren</summary>

1. Configureer uw organisatie-id en vervang de alfanumerieke tekenreeks door uw eigen organisatie-id.

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   * Uw eigen organisatieidentiteitskaart kan omhoog worden gezocht gebruikend de methode die onder [ wordt gedocumenteerd Mening uw organisatieidentiteitskaart ](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configureer vervolgens uw programma-id:

   `aio config:set cloudmanager_programid 12345`

1. Dan, vorm milieu identiteitskaart dat RDE aan in bijlage zal zijn:

   `aio config:set cloudmanager_environmentid 123456`

1. Nadat u klaar bent met het configureren van de insteekmodule, meldt u zich aan door

   `aio login`

   Deze stappen vereisen u om een lid van de Cloud Manager **Ontwikkelaar te zijn - het Profiel van het Product van Cloud Service**. Zie [ de Leden van het Team aan de Profielen van het Product van Cloud Manager toewijzen - wijs het Profiel van het Product van de Ontwikkelaar ](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer details toe.

Voor meer informatie en demonstratie, bekijk het videoleerprogramma [ hoe te opstelling RDE (06:24) ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup).
</details>

## RDE gebruiken tijdens het ontwikkelen van een nieuwe functie {#using-rde-while-developing-a-new-feature}

Adobe raadt de volgende workflow aan voor het ontwikkelen van een nieuwe functie:

* Wanneer een tussentijdse mijlpaal wordt bereikt en met succes plaatselijk met AEM as a Cloud Service SDK wordt bevestigd, verbind de code aan een de eigenschaptak van de it. De vertakking mag nog geen deel uitmaken van de hoofdlijn, hoewel vastlegging aan de it optioneel is. Wat een &quot;tussenliggende mijlpaal&quot; is, varieert op basis van teamgewoonten. Voorbeelden zijn enkele nieuwe coderegels, een halve werkdag of het voltooien van een subfunctie.

* Herstel RDE als het door een andere eigenschap is gebruikt en u wilt [ het aan een standaardstaat ](#reset-rde) terugstellen. <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). --> het Terugstellen neemt een paar notulen en al bestaande inhoud en code wordt geschrapt. U kunt het RDE statusbevel gebruiken om RDE klaar te bevestigen. De RDE komt terug met de meest recente versie van de AEM versie.

  >[!IMPORTANT]
  >
  >Als uw testende en productiemilieu&#39;s geen automatische updates van de release van AEM ontvangen en achter de recentste versie zijn, kan RDE een verschillende versie van AEM in werking stellen. Dientengevolge, zou het codegedrag in RDE niet kunnen aanpassen hoe het in het opvoeren en productie functioneert. In dat geval, is het belangrijk om grondig het testen van de code op het opvoeren uit te voeren alvorens het aan productie op te stellen.


* Gebruikend RDE bevel-lijn interface, synchroniseer lokale code aan RDE. U kunt verschillende bestandstypen installeren, waaronder de volgende:

   * Inhoudspakketten
   * Specifieke pakketten
   * OSGi-configuratiebestanden
   * Inhoudbestanden
   * ZIP-bestanden met Apache/Dispatcher-configuraties

  Het is ook mogelijk te verwijzen naar een extern inhoudspakket. Zie [ RDE bevel-Lijn Hulpmiddelen ](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands) voor meer informatie. U kunt het statusbevel gebruiken om te bevestigen dat de plaatsing succesvol was. Gebruik optioneel Package Manager om inhoudspakketten te installeren.

* Test de code in RDE. Auteur- en publicatie-URL&#39;s zijn beschikbaar in Cloud Manager.

* Als de code zich niet zoals verwacht gedraagt, gebruik standaard het zuiveren technieken om het probleem te begrijpen en de aangewezen veranderingen aan te brengen. Zonder de codewijzigingen aan Git toe te wijzen (aangezien zij niet) zijn bevestigd, gebruik lokale CLI om de code aan RDE te synchroniseren. Herhaal dit totdat het probleem is opgelost.

* Zodra de code zich zoals verwacht gedraagt, wijs de code aan de git eigenschaptak toe.

* De code die aan RDE wordt gesynchroniseerd gebruikt geen pijpleiding van Cloud Manager zodat zou u nu een Cloud Manager non-production pijpleiding moeten gebruiken om de de eigenschaptak van de Git aan de milieu van de Ontwikkeling van de Wolk op te stellen. Dit proces bevestigt dat de code de de kwaliteitstoegangspoorten van Cloud Manager overgaat en laat u zeker zijn de code later met succes gebruikend de de productiepijplijn van Cloud Manager wordt opgesteld.

* Herhaal bovenstaande stappen voor elke tussenliggende mijlpaal totdat alle code voor de functie gereed is en goed wordt uitgevoerd op zowel de RDE als de Cloud Development-omgeving.

* Implementeer de code via de Cloud Manager-productiepijplijn naar de productie.

## RDE gebruiken om een bestaande eigenschap te zuiveren {#use-rde-to-debug-an-existing-feature}

Het werkschema is gelijkaardig aan het ontwikkelen van een nieuwe eigenschap. Het verschil is dat de code die aan RDE wordt gesynchroniseerd het etiket van de Git van weerspiegelt wat aan het milieu werd geduwd waar de kwestie voorkwam. Deze workflow zorgt voor consistentie bij het onderzoeken of weergeven van het probleem. Bovendien kan het nuttig zijn om inhoud op te stellen die de stroomopwaartse milieu aanpast. Deze aanpak kan worden bereikt door inhoudspakketten te exporteren en te importeren.

## Meerdere ontwikkelaars die samenwerken op dezelfde RDE {#multiple-developers-collaborating-on-the-same-rde}

RDE steunt één enkel project tegelijkertijd. Aangezien de code van een lokale ontwikkelomgeving aan het milieu RDE wordt gesynchroniseerd, is het het meest natuurlijk voor één ontwikkelaar om het op een bepaald ogenblik op zich te gebruiken.

Met zorgvuldige coördinatie is het echter mogelijk dat meerdere ontwikkelaars een specifieke functie valideren of fouten in een specifiek probleem opsporen. De sleutel is dat elke ontwikkelaar hun lokale projecten synchroon houdt zodat de codeveranderingen die door een bepaalde ontwikkelaar worden aangebracht door de andere ontwikkelaars worden geabsorbeerd. Anders zou één ontwikkelaar per ongeluk de code van de ander kunnen overschrijven. De aanbevolen strategie is dat elke ontwikkelaar zijn of haar wijzigingen doorvoert in een gedeelde Git-vertakking voordat hij of zij synchroniseert met de RDE, zodat de andere ontwikkelaars de wijzigingen doorvoeren voordat ze hun eigen wijzigingen doorvoeren.

## Opdrachten voor RDE-opdrachtregelprogramma&#39;s {#rde-cli-commands}

### Help/algemene informatie {#help}

* Voor een lijst met opdrachten typt u:

  `aio aem:rde`

* Voor gedetailleerde hulp voor een bevel, type:

  `aio aem rde <command> --help`

### Globale vlaggen {#global-flags}

* Voor een minder uitgebreide uitvoer gebruikt u de stille markering:

  `aio aem rde <command> --quiet`

  Deze markering verwijdert bepaalde elementen, zoals spinners en voortgangsbalken, en beperkt de noodzaak van gebruikersinvoer.

* Voor JSON in plaats van de output van het consolelogboek, gebruik de json vlag:

  `aio aem rde <command> --json`

  Deze vlag keert geldige JSON terwijl het onderdrukken van om het even welke consoleoutput terug. Zie de JSON-voorbeelden verderop.

* Om te vermijden vormend de de verbindingsinformatie van RDE gebruikend het opstellingsbevel, of om het even welke verwezenlijking van de AIR config, gebruik de drie vlaggen voor organisatie, programma en milieu:

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  Hiervoor moet een ```aio login``` worden uitgevoerd.

### Distribueren naar RDE {#deploying-to-rde}

Deze sectie verklaart hoe te om RDE CLI te gebruiken om, diverse middelen op te stellen te installeren of bij te werken. Deze bronnen zijn onder andere:

* Inhoudspakketten
* OSGi-configuraties
* Bundels
* Inhoudbestanden
* Apache- of Dispatcher-configuraties

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

Artefacten worden standaard ingezet op zowel auteur- als publicatieniveaus, maar de markering `-s` kan worden gebruikt om een specifieke laag als doel in te stellen.

Om het even welk pakket van AEM kan worden opgesteld, zoals pakketten met code, inhoud, of a [ containerpakket ](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (ook genoemd het &quot;alle&quot;pakket).

>[!IMPORTANT]
>
>De bovenstaande content-package installatie implementeert de Dispatcher configuratie voor het WKND project niet. Implementeer deze afzonderlijk volgens de stappen &quot;Apache/Dispatcher Configuration implementeren&quot;.

#### Een OSGI-configuratie implementeren {#deploy-OSGI-config}

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

#### Een inhoudsbestand implementeren {#deploy-content-file}

Als u een inhoudsbestand wilt implementeren, gebruikt u:

`aio aem:rde:install world.txt -p /apps/hello.txt`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

#### Een Apache/Dispatcher-configuratie implementeren {#deploy-apache-config}

Voor dit type configuratie moet de volledige mapstructuur de vorm hebben van een ZIP-bestand.

Vanuit de module `dispatcher` van een AEM-project kunt u de Dispatcher-configuratie comprimeren door de onderstaande gemaskeerde opdracht uit te voeren:

`mvn clean package`

Of u gebruikt de opdracht onder zip vanuit de map `src` van de module `dispatcher` :

`zip -y -r dispatcher.zip .`

Dan stel de configuratie door dit bevel op:

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>Het bovenstaande bevel veronderstelt u de [ configuraties van Dispatcher van het 1&rbrace; project van WKND &lbrace;. ](https://github.com/adobe/aem-guides-wknd) Vervang `X.X.X` door het corresponderende WKND-projectversienummer of uw projectspecifieke versienummer wanneer u de Dispatcher-configuratie van uw project implementeert.

>[!NOTE]
>
>RDE ondersteunt de Dispatcher-configuratie &quot;Flexible Mode&quot;, maar niet de Dispatcher-configuratie &quot;Legacy Mode&quot;. Zie {de documentatie van 0} Dispatcher [&#128279;](/help/implementing/dispatcher/disp-overview.md#validation-debug) voor informatie over de twee wijzen.  U kunt de documentatie ook raadplegen over [ migrerend aan Flexibele wijze ](/help/implementing/dispatcher/validation-debug.md#migrating), als u dit niet reeds hebt gedaan.

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

#### Distribueer configuratie met betrekking tot configuratiemogelijkheden voor config-pijpleidingen (configuraties yaml) {#deploy-config-pipeline}

De milieu-specifieke configuraties (één of meerdere yaml dossiers) die in het artikel [ worden beschreven Gebruikend Pijpleidingen Config ](/help/operations/config-pipeline.md) kunnen als volgt worden opgesteld:

`aio aem:rde:install -t env-config ./my-config-folder`
Waar `my-config-folder` de bovenliggende map is die uw onderliggende configuraties bevat.

U kunt ook een ZIP-bestand met de mapstructuur config installeren:

`aio aem:rde:install -t env-config config.zip`

De envTypes-array van het afbeeldingsbestand bevat de waarde `rde` , zoals in het onderstaande voorbeeld:

```
kind: "CDN"
version: "1"
metadata:
  envTypes: ["rde"]
```

### Voorste code implementeren op basis van sitethema&#39;s en sitesjablonen {#deploying-themes-to-rde}

RDEs steunt front-end code die met [ plaatsthema&#39;s ](/help/sites-cloud/administering/site-creation/site-themes.md) en [ plaatsmalplaatjes ](/help/sites-cloud/administering/site-creation/site-templates.md) wordt gebouwd. In plaats van het gebruiken van Cloud Manager [ voorste-Eind Pijpleiding ](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) als andere milieutypes, stelt RDEs voorste pakketten gebruikend een bevel-lijn richtlijn op.

Zoals gebruikelijk, bouw uw front-end pakket gebruikend npm:

`npm run build`

Er wordt een `dist/` -map gegenereerd, zodat uw front-end pakketmap een `package.json` bestand en `dist` -map bevat:

```
ls ./path-to-frontend-pkg-folder/
...
dist
package.json
```

Nu, bent u bereid om het front-end pakket aan RDE op te stellen door aan de front-end pakketomslag op de volgende manier te richten:

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
>
> * `dist` -map, voor de npm-map voor uitvoerpakketten.
> * `package.json` bestand, voor het Npm-afhankelijkheidspakket

>[!TIP]
>
>Als u RDE vóór April 2023 creeerde en `UNEXPECTED_API_ERROR` ontmoet wanneer het gebruiken van de front-end eigenschap voor het eerst, kan het aan een verouderde opstelling zijn. Verwijder de omgeving en maak een nieuwe omgeving om dit probleem op te lossen.

### Controleer de status van de RDE {#checking-rde-status}

U kunt RDE CLI gebruiken om te controleren of het milieu klaar is om aan worden opgesteld, aangezien welke plaatsingen door middel van het elektrische toestel van RDE zijn gemaakt.

Voer het volgende uit:

`aio aem:rde:status`

Retourneert met het volgende:

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

U kunt CLI het gebruiken om configuraties en bundels te schrappen die u eerder aan RDE opstelde. Gebruik de opdracht `status` voor een lijst met items die kunnen worden verwijderd. Deze lijst bevat de instructie `bsn` for bundles en `pid` voor configuraties waarnaar moet worden verwezen in de opdracht delete.

Bijvoorbeeld, als `com.adobe.granite.demo.MyServlet.cfg.json` is geïnstalleerd, is `bsn` enkel `com.adobe.granite.demo.MyServlet`, zonder het {**achtervoegsel 3} cfg.json.**

Verwijderen van inhoudspakketten of inhoudsbestanden wordt niet ondersteund. Om hen te verwijderen, stel RDE terug, die het aan een standaardstaat terugkeert.

Zie het onderstaande voorbeeld voor meer informatie:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Voor meer informatie en demonstratie, zie het videoleerprogramma [ hoe te om de bevelen van RDE (10:01) te gebruiken ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use).


## Implementeren naar een RDE van externe Git-providers {#deploy-to-rde}

>[!NOTE]
>
>Deze functie is beschikbaar via het Beta-programma. Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ CloudManager_BYOG@adobe.com ](mailto:cloudmanager_byog@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Zorg ervoor dat u ook het Git-platform opgeeft dat u wilt gebruiken en dat u zich in een opslagstructuur van een privéserver, een openbare opslagruimte of een bedrijfsopslagruimte bevindt.

Cloud Manager steunt het opstellen van code aan RDE direct van externe leveranciers van het Git wanneer het gebruiken van [ uw eigen configuratie van het Git (BYOG) ](/help/implementing/cloud-manager/managing-code/external-repositories.md) brengt.

Voor het implementeren van RDE&#39;s vanuit een externe Git-opslagplaats is het volgende vereist:

* Het gebruik van een externe Git-opslagplaats die is geïntegreerd met Cloud Manager (BYOG-instelling).
* Uw project moet een of meer RDE-omgevingen hebben ingericht.
* Als u `github.com` gebruikt, moet u de bijgewerkte app installatie van GitHub herzien en goedkeuren om de vereiste nieuwe toestemmingen te verlenen.

**Nota&#39;s van het Gebruik**

* Implementatie naar RDE wordt momenteel alleen ondersteund voor AEM-inhoud en Dispatcher-pakketten.
* De implementatie van andere pakkettypen (bijvoorbeeld volledige AEM-toepassingspakketten) wordt nog niet ondersteund.
* Momenteel wordt het opnieuw instellen van een RDE-omgeving met behulp van een opmerking niet ondersteund. In plaats daarvan, moet u het bestaande AIO CLI terugstellenbevel gebruiken, zoals [ hier wordt beschreven ](/help/implementing/developing/introduction/rapid-development-environments.md#reset-the-rde-command-line).

**hoe het** werkt

1. **bericht van de kwaliteitsbevestiging van de Code.**

   Wanneer een trekkingsverzoek (PR) een pijpleiding van de codekwaliteit teweegbrengt, wijzen de bevestigingsresultaten erop of de plaatsing aan een milieu van RDE kan te werk gaan.

   Hoe het op Onderneming GitHub kijkt:
   ![ de kwaliteitsbevestiging van de Code bericht op Onderneming GitHub ](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Hoe het er uitziet op GitLab:
   ![ bericht van de kwaliteitsbevestiging van de Code op GitLab ](/help/implementing/developing/introduction/assets/rde-gitlab-code-quality-validation-message.png)

   Hoe het er op Bitbucket uitziet:
   ![ bericht van de kwaliteitsbevestiging van de Code op Bitbucket ](/help/implementing/developing/introduction/assets/rde-bitbucket-code-quality-validation-message.png)

1. **de plaatsing die van de trekker een commentaar gebruikt.**

   Als u de implementatie wilt starten, voegt u een opmerking toe aan de PR in de volgende indeling: `deploy on rde-environment-<envName>`

   ![ plaatsing van de Trekker gebruikend een commentaar ](/help/implementing/developing/introduction/assets/rde-trigger-deployment-using-comment.png)

   `<envName>` moet de naam van een bestaande milieu van RDE aanpassen. Als de naam niet wordt gevonden, wordt een opmerking geretourneerd die aangeeft dat de omgeving ongeldig is.

   Als de milieustatus niet klaar is, krijgt u de volgende opmerking:

   ![ Milieu niet klaar om op te stellen ](/help/implementing/developing/introduction/assets/rde-environment-not-ready.png)

1. **controle van het Milieu en artefactplaatsing.**

   Als de RDE klaar is, post Cloud Manager een nieuwe controle aan PR.

   Hoe het op Onderneming GitHub kijkt:

   ![ Status van het milieu op GitHub ](/help/implementing/developing/introduction/assets/rde-github-environment-status-is-ready.png)

   Hoe het er uitziet op GitLab:

   ![ Status van het milieu op GitLab ](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-1.png)

   Hoe het er op Bitbucket uitziet:

   ![ Status van het milieu op Bitbucket ](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-1.png)

1. **Succesvol plaatsingsbericht.**

   Wanneer de implementatie is voltooid, wordt in Cloud Manager een succesbericht geplaatst met een overzicht van de artefacten die in de doelomgeving zijn geïmplementeerd.

   Hoe het op Onderneming GitHub kijkt:

   ![ status van de Plaatsing van het milieu op GitHub ](/help/implementing/developing/introduction/assets/rde-github-environment-deployed-artifacts.png)

   Hoe het er uitziet op GitLab:

   ![ status van de Plaatsing van milieu op GitLab ](/help/implementing/developing/introduction/assets/rde-gitlab-deployment-2.png)

   Hoe het er op Bitbucket uitziet:

   ![ status van de Plaatsing van milieu op Bitbucket ](/help/implementing/developing/introduction/assets/rde-bitbucket-deployment-2.png)




## Logboeken {#rde-logging}

Gelijkaardig aan andere milieutypes, kunnen de logboekniveaus worden geplaatst door configuraties te wijzigen OSGi, hoewel zoals hierboven beschreven, het plaatsingsmodel voor RDEs een bevellijn eerder dan een plaatsing van Cloud Manager impliceert. Controleer de [ registrerendocumentatie ](/help/implementing/developing/introduction/logging.md) voor meer informatie over hoe te om, logboeken te bekijken te downloaden en te interpreteren.

RDE CLI heeft ook zijn eigen logboekbevel dat wordt gebruikt om snel te vormen welke klassen en pakketten worden geregistreerd, en op welk logboekniveau. Deze configuraties kunnen als letterlijk worden beschouwd, aangezien zij niet de eigenschappen OSGI in versiecontrole wijzigen. Deze functie is gericht op het in real time stammen van logboeken in plaats van het omhoog kijken van logboeken van het verre verleden.

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

Functies zijn onder andere:

* logboekniveaus declareren op een pakket- of klassenniveau
* het aanpassen van het formaat van de logboekoutput
* die tot vier huidige logboekconfiguraties opmaken, elk in zijn eigen terminal
* markeren, specifieke logbestanden

Merk op dat de logboeken in geheugen op RDE worden opgeslagen en deze logboeken worden gerecycled en zo worden verworpen als zij niet worden gesleept of als het netwerk te langzaam is.


## De RDE opnieuw instellen {#reset-rde}

Als u de RDE opnieuw instelt, verwijdert u alle aangepaste code, configuraties en inhoud van zowel de auteur- als de publicatieversie. Het opnieuw instellen van de RDE is nuttig wanneer u klaar bent met het testen van één functie en de omgeving wilt terugzetten naar de standaardtoestand voordat u een andere test.

Met een reset wordt de RDE ingesteld op de meest recente beschikbare AEM-versie.

U kunt RDE terugstellen gebruikend of [ Cloud Manager ](#reset-the-rde-cloud-manager) of de [ bevellijn ](#reset-the-rde-command-line). Het opnieuw instellen duurt een paar minuten en alle bestaande inhoud en code wordt verwijderd uit de RDE.

>[!NOTE]
>
>Controleer of u de Cloud Manager Developer-rol hebt toegewezen voordat u de functie reset gebruikt. Anders mislukt de herstelactie met een fout.

### RDE herstellen met behulp van opdrachtregel {#reset-the-rde-command-line}

U kunt RDE terugstellen en het terugkeren aan een standaardstaat door het volgende in werking te stellen:

`aio aem:rde:reset`

Dit proces neemt meestal een paar minuten in beslag en rapporteert ```Environment reset.``` wanneer dit is gelukt of ```Failed to reset the environment.``` over fouten. Zie het onderstaande hoofdstuk over ```--json``` uitvoer voor een gestructureerde uitvoer.

Gebruik het [ statusbevel ](#checking-rde-status) om te controleren wanneer het milieu opnieuw klaar is.

### De RDE in Cloud Manager opnieuw instellen {#reset-the-rde-cloud-manager}

U kunt Cloud Manager gebruiken om uw RDE opnieuw in te stellen door de volgende stappen te volgen:

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Klik het programma waarvoor u RDE wilt terugstellen.

1. Van de **pagina van het Overzicht**, klik het **milieu&#39;s** lusje bij de bovenkant van het scherm.

   ![ Milieu&#39;s tabel ](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * Alternatief, klik **tonen Al** knoop op de **&#x200B;**&#x200B;kaart van Milieu&#39;s &lbrace;om rechtstreeks aan het **Milieu** lusje te springen.

     ![ toon alle optie ](/help/implementing/cloud-manager/assets/environment-showall.png)

1. Het **venster van Milieu&#39;s** opent en maakt een lijst van alle milieu&#39;s voor het programma.

   ![ het milieu tabel ](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Klik de elliptische knoop van RDE die u wilt terugstellen, en dan selecteren **Terugstellen**.

   ![ het omgevingsdetails van de Mening ](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Bevestig dat u RDE wilt terugstellen door **Terugstellen** in de dialoog te klikken.

   ![ bevestigt terugstellen ](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager bevestigt door middel van een bannermelding dat het herstelproces is gestart.

   ![ Bannerbericht van het Terugstellen ](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Nadat de RDE-reset is gestart, duurt het meestal enkele minuten om de omgeving te voltooien en terug te zetten naar de standaardtoestand. U kunt de terugstellingstatus op elk ogenblik in de **kolom van de Status** van de **kaart of het venster van Milieu&#39;s** bekijken.

![ RDE terugstellingstatus ](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

U kunt RDE ook terugstellen gebruikend de elliptische knoop direct van de **1&rbrace; kaart van Milieu&#39;s &lbrace;op de** Overzicht **pagina.**

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

#### Wacht tot de bewerking is voltooid, reset is voltooid {#wait-success}

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```

#### Wachten op voltooiing, opnieuw instellen mislukt {#wait-failed}

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
  <summary>Uitbreiden om voorbeelden van opnieuw opstarten weer te geven</summary>

```$ aio aem rde restart --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "restarted"
}
```

</details>

## Modus Uitvoeren {#runmodes}

RDE-specifieke configuratie OSGI kan worden toegepast door achtervoegsels op de omslagnaam te gebruiken, zoals in de voorbeelden hieronder:

* `config.rde`
* `config.author.rde`
* `config.publish.rde`

Zie de [ documentatie van de looppaswijze ](/help/implementing/deploying/overview.md#runmodes) voor algemene informatie over looppaswijzen.

>[!NOTE]
>
>De configuratie van RDE OSGI is uniek in die zin dat het de waarden van om het even welke eigenschappen overerft OSGI die door de `dev` loopgebiedwijze van de bundel worden verklaard.

RDE&#39;s verschillen van andere omgevingen in die zin dat inhoud kan worden geïnstalleerd in een `install.rde` -map (of `install.author.rde` of `install.publish.rde` ) onder `/apps` . Hierdoor kunt u inhoud toewijzen aan Git en deze leveren aan de RDE met behulp van opdrachtregelprogramma&#39;s.

## Vullen met inhoud {#populating-content}

Wanneer een RDE wordt teruggesteld, wordt al inhoud verwijderd en zo zo, zo moet de expliciete actie worden genomen om inhoud toe te voegen. Als beste praktijken, overweeg het assembleren van een reeks inhoud die als testinhoud voor het bevestigen van of het zuiveren eigenschappen in RDE moet worden gebruikt. Er zijn verscheidene mogelijke strategieën om RDE met die inhoud te bevolken:

1. Synchroniseer het inhoudspakket uitdrukkelijk aan RDE gebruikend bevel-lijn het gebruiken

1. Plaats en wijs de steekproefinhoud in git binnen een `install.rde` omslag onder `/apps` toe en synchroniseer dan het overkoepelende inhoudspakket aan RDE gebruikend het bevel-lijn hulpmiddel.

1. Gebruik het [ hulpmiddel van het inhoudsexemplaar ](/help/implementing/developing/tools/content-copy.md) om een bepaalde inhoud te kopiëren die van prod, stadium, of ontwikkelt milieu&#39;s, of van een andere RDE wordt geplaatst.

1. Pakketbeheer gebruiken

U kunt maximaal 1 GB gebruiken bij het synchroniseren van inhoudspakketten.


## Hoe verschillen RDE&#39;s van cloudontwikkelomgevingen? {#how-are-rds-different-from-cloud-development-environments}

Terwijl RDE in vele opzichten gelijkaardig aan een milieu van de Ontwikkeling van de Wolk is, zijn er sommige kleine architecturale verschillen om voor snelle synchronisatie van code toe te staan. Het mechanisme om code aan RDE te krijgen is verschillend — voor RDEs, één syncs code van een lokale ontwikkelomgeving, terwijl voor de milieu&#39;s van de Ontwikkeling van de Wolk, één code door Cloud Manager opstelt.

Om deze redenen, adviseert men dat na het bevestigen van code op een milieu RDE, u de code aan een milieu van de Ontwikkeling van de Wolk gebruikend de niet productiepijplijn opstelt. Tot slot test de code alvorens met de productiepijpleiding op te stellen.

Houd ook rekening met het volgende:

* RDE&#39;s bevatten geen voorvertoningsniveau
* RDEs steunt momenteel niet het prereleasekanaal.


## Hoeveel RDEs heb ik nodig? {#how-many-rds-do-i-need}

Een RDE is beschikbaar voor elke gelicentieerde oplossing en Adobe biedt ook extra RDEs aan, die voor Productie (niet-zandbak) programma&#39;s kunnen worden vergunning gegeven.

Het aantal vereiste RDEs hangt van de samenstelling en de processen van een organisatie af. Het meest flexibele model is waar een organisatie een specifieke RDE voor elk van hun ontwikkelaars van de Dienst van de Wolk AEM koopt. In dit model, kan elke ontwikkelaar hun code op RDE testen zonder met andere teamleden te coördineren op of een milieu RDE beschikbaar is.

Aan de andere kant kan een team met slechts één RDE op interne coördinatie vertrouwen om te bepalen welke ontwikkelaar het milieu op een bepaald tijdstip gebruikt. Deze aanpak werkt goed wanneer een ontwikkelaar een mijlpaal bereikt met functies en zijn werk moet valideren in een cloud-omgeving met de flexibiliteit om snel wijzigingen aan te brengen.

Een ingebouwd model is een model waarbij een organisatie verschillende RDE&#39;s koopt, zodat er een grotere kans is dat een ongebruikte RDE beschikbaar is. Eén strategie zou kunnen bestaan uit het toewijzen van een RDE per rumteam of belangrijke functie. Interne processen kunnen worden gebruikt om het gebruik van de omgevingen te coördineren.

## Hoe anders is een AEM Forms Cloud Service RDE dan andere omgevingen? {#how-are-forms-rds-different-from-cloud-development-environments}

Forms-ontwikkelaars kunnen AEM Forms Cloud Service Rapid Development Environment gebruiken om snel adaptieve Forms, workflows en aanpassingen te ontwikkelen, zoals het aanpassen van kerncomponenten, integratie met systemen van derden en meer. De AEM Forms Cloud Service Rapid Development Environment (RDE) biedt geen ondersteuning voor communicatie-API&#39;s. Het biedt ook geen ondersteuning voor functies en mogelijkheden die Documenten van Record vereisen, zoals het genereren van een Document of Record bij het verzenden van een adaptief formulier. De hieronder vermelde AEM Forms-functies zijn niet beschikbaar in een Rapid Development Environment (RDE):

* Een recorddocument configureren voor een adaptief formulier
* Een document met records genereren bij het indienen van een adaptief formulier of met een workflowstap
* Document verzenden als bijlage bij Record met de handeling Verzenden via e-mail of met de stap E-mail in een workflow
* Adobe-aanmelding gebruiken in een adaptief formulier of in een workflowstap
* Communicatie-API&#39;s

>[!NOTE]
>
> Er is geen verschil tussen de interface van Rapid Development Environment (RDE) en andere Cloud Service-omgevingen voor Forms. Alle aan het document van Verslag verwante opties, zoals het selecteren van een document van verslagmalplaatje voor een Aangepast Vorm, blijven in UI verschijnen. Deze omgevingen hebben geen communicatie-API&#39;s en documentmogelijkheden om dergelijke opties te testen. Als u dus een optie kiest waarvoor communicatie-API&#39;s of de functie Document of Record vereist is, voert het systeem de actie niet uit. In plaats daarvan wordt een foutbericht weergegeven.

## RDE-zelfstudie

Om over RDE in AEM as a Cloud Service te leren, zie het videoleerprogramma dat [ toont hoe te opstelling, hoe te om het te gebruiken, en de cyclus van het ontwikkelingsleven (01:25) ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/developing/rde/overview).

## Problemen oplossen {#troubleshooting}

### Los RDE (#rde-troublehooting) problemen op

#### De nieuwste AEM-versie verkrijgen voor een bestaande RDE {#get-latest-aem-version}

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare Adobe Experience Manager (AEM)-versie. Een [ teruggestelde RDE ](#reset-rde), die kan worden uitgevoerd gebruikend Cloud Manager of het `aio aem:rde:reset` bevel, cycli RDE en plaats het aan de recentste beschikbare versie van AEM.

### AIR RDE-plug-in oplossen {#aio-rde-plugin-troubleshooting}

#### Fouten met betrekking tot ontoereikende machtigingen {#insufficient-permissions}

Om de insteekmodule van RDE te gebruiken, vereist het u om een lid van de Cloud Manager **Ontwikkelaar - het Profiel van het Product van Cloud Service** te zijn. Zie [ de Leden van het Team aan de Profielen van het Product van Cloud Manager toewijzen - wijs het Profiel van het Product van de Ontwikkelaar ](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer details toe.

Alternatief, kunt u bevestigen dat u deze ontwikkelaarrol hebt als u login aan de ontwikkelaarsconsole door het volgende bevel in werking te stellen:

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>Als u de `Warning: cloudmanager:* is not a aio command.` fout ziet, moet u [ aio-cli-stop-cloudmanager ](https://github.com/adobe/aio-cli-plugin-cloudmanager) installeren door het volgende bevel in werking te stellen:
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

Controleer of de aanmelding is voltooid door het volgende uit te voeren:

`aio cloudmanager:list-programs`

Dit proces maakt een lijst van alle programma&#39;s onder uw gevormde organisatie en bevestigt dat u de correcte toegewezen rol hebt.

#### Vervangen context gebruiken `aio-cli-plugin-cloudmanager` {#aio-rde-plugin-troubleshooting-deprecatedcontext}

Vanwege de geschiedenis van de `aio-cli-plugin-aem-rde` is de contextnaam `aio-cli-plugin-cloudmanager` al enige tijd gebruikt. De insteekmodule RDE gebruikt nu de IMS-methode voor het beheer van contextinformatie, zodat u de context globaal of lokaal kunt opslaan. U kunt een standaardcontext ook vormen om automatisch op alle vraag toe te passen AIO. De standaard gevormde context wordt plaatselijk opgeslagen en laat de ontwikkelaars toe om individuele contexten en hun informatie binnen een omslag te volgen en te gebruiken. Voor verdere details, lees [ het voorbeeld aan opstelling hierboven een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools).

Ontwikkelaars die zowel de plug-ins `aio-cli-plugin-cloudmanager` als de `aio-cli-plugin-aem-rde` gebruiken en alle informatie in dezelfde context willen houden, moeten nu opties kiezen:

##### Context blijven gebruiken `aio-cli-plugin-cloudmanager`

De context kan nog steeds worden gebruikt. In de RDE-plug-in wordt een afleidingswaarschuwing weergegeven. Deze waarschuwing kan worden weggelaten in de modus ```--quiet``` . Recentere versies van de RDE-insteekmodule bieden niet langer de mogelijkheid om de context `aio-cli-plugin-cloudmanager` te lezen. Als u dit wilt blijven gebruiken, configureert u gewoon de standaardcontext op `aio-cli-plugin-cloudmanager` . Zie [ het voorbeeld aan opstelling een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) hierboven.

##### Gebruik een andere contextnaam ook voor de Cloud Manager-plug-in

De Cloud Manager-plug-ins bieden een parameter voor het definiëren van de context die moet worden gebruikt. De standaard IMS-contextconfiguratie wordt nog niet ondersteund. Om dit te doen, vorm de insteekmodule RDE gebruikend [ het voorbeeld aan opstelling een lokale context ](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools) en vertelt de insteekmodule van Cloud Manager om `myContext` als ```--imsContextName=myContext``` in elke vraag aan het te gebruiken.
