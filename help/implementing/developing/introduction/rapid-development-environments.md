---
title: Snelle ontwikkelomgevingen
description: Leer hoe u Rapid Development Environment kunt gebruiken voor snelle ontwikkelherhalingen in een cloud-omgeving.
exl-id: 1e9824f2-d28a-46de-b7b3-9fe2789d9c68
source-git-commit: 4a5b7c671a149d61c60fc86f93a41d52fb4b5468
workflow-type: tm+mt
source-wordcount: '4294'
ht-degree: 0%

---

# Snelle ontwikkelomgevingen {#rapid-development-environments}

Om veranderingen op te stellen, vereisen de huidige milieu&#39;s van de Ontwikkeling van de Wolk het gebruik van een proces dat uitgebreide codeveiligheid en kwaliteitsregels gebruikt genoemd een pijpleiding CI/CD. Voor situaties waar snelle en iteratieve veranderingen nodig zijn, heeft de Adobe de Milieu&#39;s van de Snelle Ontwikkeling (RDEs voor kort) ingevoerd.

RDEs staat ontwikkelaars toe om veranderingen snel op te stellen en te herzien, die de hoeveelheid tijd minimaliseren nodig om eigenschappen te testen die aan een lokale ontwikkelomgeving blijken te werken.

Zodra de veranderingen in RDE zijn getest, kunnen zij aan een regelmatige milieu van de Ontwikkeling van de Wolk door de pijpleiding van de Manager van de Wolk worden opgesteld.

>[!NOTE]
> Neem contact op met RDE-ontwikkelaars op onze [Disorder channel](https://discord.com/channels/1131492224371277874/1245304281184079872). Voel vrij om het even welke vragen te stellen of terugkoppelen betreffende onderwerpen RDE.

>[!VIDEO](https://video.tv.adobe.com/v/3415582/?quality=12&learn=on)


U ziet aanvullende video&#39;s waarin u kunt demonstreren [instellen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html), [gebruiken](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html)en de [ontwikkelingscyclus](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/development-life-cycle.html) RDE gebruiken.

## Inleiding {#introduction}

RDEs kan voor code, inhoud, en Apache of Dispatcher configuraties worden gebruikt. In tegenstelling tot gewone Cloud Development-omgevingen kunnen ontwikkelaars lokale opdrachtregelprogramma&#39;s gebruiken om code die lokaal is gemaakt te synchroniseren met een RDE.

Elk programma wordt voorzien van RDE. Als er Sandbox-accounts zijn, worden deze na een paar uur niet meer gebruikt.

Bij het maken worden RDE&#39;s ingesteld op de laatst beschikbare Adobe Experience Manager-versie (AEM). Een RDE-reset, die kan worden uitgevoerd met gebruik van Cloud Manager, fietst de RDE en stelt deze in op de laatst beschikbare AEM versie.

Typisch, zou RDE door één enkele ontwikkelaar in een bepaalde tijd, voor het testen en het zuiveren van een specifieke eigenschap worden gebruikt. Wanneer de ontwikkelingszitting wordt gedaan, kan RDE in een standaardstaat voor het volgende gebruik worden teruggesteld.

Aanvullende RDE&#39;s kunnen in licentie worden gegeven voor productieprogramma&#39;s (niet-sandbox).

## RDE inschakelen in een programma {#enabling-rde-in-a-program}

Voer de volgende stappen uit, zodat u Cloud Manager kunt gebruiken om een RDE voor uw programma te maken.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik het programma waaraan u RDE wilt toevoegen om zijn details te tonen.

   * RDE&#39;s kunnen aan beide worden toegevoegd [sandboxprogramma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-sandbox-programs.md) en [productieprogramma&#39;s](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/introduction-production-programs.md).

1. Van de **Programmaoverzicht** pagina, klikt u **Omgeving toevoegen** op de **Omgevingen** -kaart om een omgeving toe te voegen.

   ![Milieukaart](/help/implementing/cloud-manager/assets/no-environments.png)

   * De **Omgeving toevoegen** deze optie is ook beschikbaar op de **Omgevingen** tab.

     ![Het tabblad Omgevingen](/help/implementing/cloud-manager/assets/environments-tab.png)

   * De **Omgeving toevoegen** Deze optie kan worden uitgeschakeld bij gebrek aan machtigingen of afhankelijk van de gelicentieerde bronnen.

1. In de **Omgeving toevoegen** dialoogvenster dat wordt weergegeven:

   * Selecteren **Snelle ontwikkeling** onder de **Omgevingstype selecteren** kop.
      * Het aantal beschikbare/gebruikte omgevingen wordt tussen haakjes achter het omgevingstype weergegeven.
   * Geef een **Naam** voor het milieu
   * Een optionele **Beschrijving** voor het milieu
   * Selecteer een **Cloud Region**.

   ![Omgevingsdialoogvenster toevoegen](/help/implementing/cloud-manager/assets/add-environment-wizard.png)

1. Klikken **Opslaan** om de opgegeven omgeving toe te voegen.

De **Overzicht** het scherm toont nu uw nieuwe milieu in **Omgevingen** kaart.

Bij het maken worden RDE&#39;s ingesteld op de meest recente beschikbare AEM. Een RDE-reset, die ook kan worden uitgevoerd met gebruik van Cloud Manager, fietst de RDE en stelt deze in op de laatst beschikbare AEM versie.

Ga voor meer informatie over het gebruik van Cloud Manager om omgevingen te maken, te beheren wie er toegang toe heeft en aangepaste domeinen toe te wijzen naar [de documentatie van Cloud Manager](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md).

## De RDE Command-Lijn hulpmiddelen installeren {#installing-the-rde-command-line-tools}

Nadat u een RDE voor uw programma hebt toegevoegd gebruikend de Manager van de Wolk, kunt u met het in wisselwerking staan door de bevel-lijn hulpmiddelen te plaatsen zoals die in de volgende stappen worden beschreven:

>[!IMPORTANT]
>
>Zorg ervoor dat u de nieuwste versie van [Knooppunt en NPM geïnstalleerd](https://nodejs.org/en/download/) voor Adobe I/O CLI en verwante plug-ins correct te laten werken.


1. Installeer de Adobe I/O CLI-gereedschappen volgens de procedure [hier](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installeer de Adobe I/O CLI-plug-in voor cloudbeheer en configureer deze zoals beschreven [hier](https://github.com/adobe/aio-cli-plugin-cloudmanager).
1. Installeer de Adobe I/O CLI hulpmiddelen AEM de stop van RDE door deze bevelen in werking te stellen:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Configureer de plug-in voor cloud Manager voor uw organisatie-id:

   `aio config:set cloudmanager_orgid 4E03EQC05D34GL1A0B49421C@AdobeOrg`

   en vervangt u de alfanumerieke tekenreeks door uw eigen organisatie-id, die u kunt opzoeken met de strategie [hier](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255).

1. Configureer vervolgens uw programma-id:

   `aio config:set cloudmanager_programid 12345`

1. Dan, vorm milieu identiteitskaart RDE zal worden vastgemaakt aan:

   `aio config:set cloudmanager_environmentid 123456`

1. Nadat u klaar bent met het configureren van de insteekmodule, meldt u zich aan door

   `aio login`

   De reactie op een geslaagde aanmelding zou op de hieronder weergegeven uitvoer moeten lijken, maar u kunt de weergegeven waarden negeren.

   ```
   ...
   You are currently in:
   1. Org: <no org selected>
   2. Project: <no project selected>
   3. Workspace: <no workspace selected>
   ```

   Voor deze stap moet u lid zijn van Cloud Manager **Ontwikkelaar - Cloud Service** Productprofiel. Zie [deze pagina](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer informatie .

   Alternatief, kunt u bevestigen dat u deze ontwikkelaarrol hebt als u login aan de ontwikkelaarsconsole kunt door dit bevel in werking te stellen:

   `aio cloudmanager:environment:open-developer-console`

   >[!TIP]
   >
   >Als u de `Warning: cloudmanager:list-programs is not a aio command.` fout, moet u installeren [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) door de onderstaande opdracht uit te voeren:
   >
   >```
   >aio plugins:install @adobe/aio-cli-plugin-cloudmanager
   >```

1. Controleren of de aanmelding is voltooid door uitvoering

   `aio cloudmanager:list-programs`

   Dit zou alle programma&#39;s onder uw gevormde organisatie moeten een lijst maken.


Bekijk de videozelfstudie voor meer informatie en demonstratie [RDE instellen (06:24)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-setup.html).

## De RDE Command-Lijn hulpmiddelen (met interactieve wijze) installeren {#installing-the-rde-command-line-tools-interactive}

>[!NOTE]
>
> Dit installatieproces is nog niet beschikbaar. Het zal het vorige proces ergens in juni vervangen.
> 

Nadat u een RDE voor uw programma hebt toegevoegd gebruikend de Manager van de Wolk, kunt u met het in wisselwerking staan door de bevel-lijn hulpmiddelen te plaatsen zoals die in de volgende stappen worden beschreven:

>[!IMPORTANT]
>
>Zorg ervoor dat u de nieuwste versie van [Knooppunt en NPM geïnstalleerd](https://nodejs.org/en/download/) voor Adobe I/O CLI en verwante plug-ins correct te laten werken.


1. Installeer de Adobe I/O CLI-gereedschappen volgens deze [procedure](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).
1. Installeer de Adobe I/O CLI-gereedschappen AEM RDE-insteekmodule:

   ```
   aio plugins:install @adobe/aio-cli-plugin-aem-rde
   aio plugins:update
   ```

1. Configureer de RDE-plug-in om uw organisatie, programma en omgeving te gebruiken. De opstellingsbevel hieronder zal interactief de gebruiker van een lijst van programma&#39;s in hun organisatie voorzien, en zal milieu&#39;s RDE in dat programma tonen om van te kiezen.

   ```
   aio login
   aio aem:rde:setup
   ```

   De opstellingsstap kan worden overgeslagen als de bedoeling een scripted milieu is te gebruiken, in welk geval de organisatie, het programma en de milieuwaarden in elk bevel kunnen worden omvat. [Zie onderstaande opdrachten voor meer informatie](#rde-cli-commands).

### De interactieve installatie

Het opstellingsbevel zal vragen of zou de verstrekte configuratie plaatselijk of globaal moeten worden opgeslagen.

```
Setup the CLI configuration necessary to use the RDE commands.
? Do you want to store the information you enter in this setup procedure locally? (y/N)
```

Kies `no` tot
* sla de organisatie, het programma en het milieu globaal in uw configuratie van de lucht op.
* werken met slechts één RDE.

Kies `yes` tot
* de organisatie, het programma en de omgeving lokaal opslaan in de huidige directory, in een `.aio` bestand. Dit is handig als u het bestand wilt toewijzen aan versiebeheer, zodat andere gebruikers het kunnen gebruiken door de it-opslagplaats te klonen.
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

Deze opdracht reageert op een resultaat dat lijkt op:

```Current configuration: cm-p1-e1: programName - environmentName (organization: ...@AdobeOrg)```

## RDE gebruiken terwijl het Ontwikkelen van een Nieuwe Eigenschap {#using-rde-while-developing-a-new-feature}

Adobe raadt de volgende workflow aan voor het ontwikkelen van een nieuwe functie:

* Wanneer een tussenliggende mijlpaal wordt bereikt en met succes plaatselijk met de AEM as a Cloud Service SDK wordt bevestigd, verbind de code aan een de eigenschaptak van de it. De vertakking mag nog geen deel uitmaken van de hoofdlijn, hoewel vastlegging aan de it optioneel is. Wat een &quot;tussenliggende mijlpaal&quot; is, varieert op basis van teamgewoonten. Voorbeelden zijn enkele nieuwe coderegels, een halve werkdag of het voltooien van een subfunctie.

* Herstel RDE als het door een andere eigenschap is gebruikt en u wilt [herstellen naar standaardstaat](#reset-rde). <!-- Alexandru: hiding for now, do not delete This can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). -->Herstellen duurt een paar minuten en alle bestaande inhoud en code wordt verwijderd. U kunt het RDE statusbevel gebruiken om RDE klaar te bevestigen. De RDE komt terug met de meest recente versie van de AEM.

  >[!IMPORTANT]
  >
  > Als uw het opvoeren en productiemilieu&#39;s geen automatische AEM versie-updates ontvangen en achter de meest recente AEM versieversie zijn, kan de code die op RDE loopt niet aanpassen hoe de code op het opvoeren en productie functioneert. In dat geval, is het vooral belangrijk om grondig het testen van de code op het opvoeren uit te voeren alvorens het aan productie op te stellen.


* Gebruikend RDE bevel-lijn interface, synchroniseer lokale code aan RDE. U kunt onder andere een inhoudspakket, een specifieke bundel, een configuratiebestand voor SDAB, een inhoudsbestand en een ZIP-bestand van een Apache/Dispatcher-configuratie installeren. Het is ook mogelijk te verwijzen naar een extern inhoudspakket. Zie [RDE-opdrachtregelprogramma&#39;s](/help/implementing/developing/introduction/rapid-development-environments.md#rde-cli-commands) voor meer informatie . U kunt het statusbevel gebruiken om te bevestigen dat de plaatsing succesvol was. Gebruik optioneel Package Manager om inhoudspakketten te installeren.

* Test de code in RDE. Auteur- en publicatie-URL&#39;s zijn beschikbaar in Cloud Manager.

* Als de code zich niet zoals verwacht gedraagt, gebruik standaard het zuiveren technieken om het probleem te begrijpen en de aangewezen veranderingen aan te brengen. Zonder de codewijzigingen toe te wijzen aan git (aangezien zij niet) zijn bevestigd, gebruik lokale CLI om de code aan RDE te synchroniseren. Herhaal dit totdat het probleem is opgelost.

* Zodra de code zich zoals verwacht gedraagt, wijs de code aan de git eigenschaptak toe.

* De code die aan RDE wordt gesynchroniseerd gebruikt geen pijpleiding van de Manager van de Wolk zodat zou u nu een niet productiepijplijn van de Manager van de Wolk moeten gebruiken om de de eigenschaptak van de it aan de milieu van de Ontwikkeling van de Wolk op te stellen. Hiermee wordt gecontroleerd of de code de kwaliteitspoort van Cloud Manager doorgeeft en of de code later correct wordt geïmplementeerd via de productiepijplijn van Cloud Manager.

* Herhaal bovenstaande stappen voor elke tussenliggende mijlpaal totdat alle code voor de functie gereed is en goed wordt uitgevoerd op zowel de RDE als de Cloud Development-omgeving.

* Implementeer de code naar productie via de productiepijplijn van Cloud Manager.

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

>[!NOTE]
>
> Deze globale markeringen zijn nog niet beschikbaar. Ze zullen ergens in juni worden ingevoerd.
> 

* Voor een minder uitgebreide uitvoer gebruikt u de stille markering:

  `aio aem rde <command> --quiet`

  Hierdoor worden bepaalde elementen, zoals spinners en voortgangsbalken, verwijderd en wordt de gebruikersinvoer beperkt.

* Voor JSON in plaats van de output van het consolelogboek, gebruik de json vlag:

  `aio aem rde <command> --json`

  Dit keert geldige JSON terwijl het onderdrukken van om het even welke consoleoutput terug. Zie de JSON-voorbeelden verderop.

* Om te vermijden vormend de de verbindingsinformatie van RDE gebruikend het opstellingsbevel, of om het even welke verwezenlijking van de AIR config, gebruik de drie vlaggen voor organisatie, programma en milieu:

  `aio aem rde <command> --organizationId=<value> --programId=<value> --environmentId=<value>`

  Dit vereist nog steeds ```aio login``` uit te voeren.

### Distribueren naar RDE {#deploying-to-rde}

Deze sectie beschrijft het gebruiken van RDE CLI voor het opstellen van, het installeren van, of het bijwerken van bundels, configuraties OSGI, inhoudspakketten, individuele inhoudsdossiers, en Apache of Dispatcher configuraties.

Het algemene gebruikspatroon is `aio aem:rde:install <artifact>`.

Hieronder vindt u enkele voorbeelden:

<u>Een inhoudspakket implementeren</u>

`aio aem:rde:install sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip`

De reactie voor een succesvolle plaatsing lijkt op het volgende:

```
...
#1: deploy completed for content-package sample.demo.ui.apps.all-1.0.0-SNAPSHOT.zip on author,publish - done by 9E072FC75D54FE1A2B49431C@AdobeID at 2022-09-13T11:32:06.229Z
```

U kunt desgewenst naar een externe opslagplaats verwijzen:

`aio aem:rde:install -t content-package "https://repo1.maven.org/maven2/com/adobe/aem/guides/aem-guides-wknd.all/2.1.0/aem-guides-wknd.all-2.1.0.zip"`

Artefacten worden standaard geïmplementeerd op zowel auteur- als publicatieniveaus, maar de markering &#39;-s&#39; kan worden gebruikt om een specifieke laag als doel in te stellen.

Elk AEM pakket kan worden geïmplementeerd, zoals pakketten met code, inhoud of een [containerpakket](/help/implementing/developing/introduction/aem-project-content-package-structure.md#container-packages) (ook wel het &quot;all&quot;-pakket genoemd).

>[!IMPORTANT]
>
>De configuratie van de Verzender voor het WKND- project wordt niet opgesteld als bovengenoemde inhoud-pakket installatie. Implementeer deze afzonderlijk volgens de stappen &quot;Apache/Dispatcher Configuration implementeren&quot;.

<u>Het opstellen van een Configuratie OSGI</u>

`aio aem:rde:install com.adobe.granite.demo.MyServlet.cfg.json`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
...
#2: deploy completed for osgi-config com.adobe.granite.demo.MyServlet.cfg.json on author,publish - done by 9E0725C05D54FE1A0B49431C@AdobeID at 2022-09-13T11:54:36.390Z
```

<u>Een bundel implementeren</u>

Om een bundel op te stellen, gebruik:

`aio aem:rde:install ~/.m2/repository/org/apache/felix/org.apache.felix.gogo.jline/1.1.8/org.apache.felix.gogo.jline-1.1.8.jar`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
...
#3: deploy staged for osgi-bundle org.apache.felix.gogo.jline-1.1.8.jar on author,publish - done by 9E0725C05D53BE1A0B49431C@AdobeID at 2022-09-14T07:54:28.882Z
```

<u>Inhoudsbestanden gebruiken</u>

Als u een inhoudsbestand wilt implementeren, gebruikt u:

`aio aem:rde:install world.txt -p /apps/hello.txt`

Waar de reactie voor een succesvolle plaatsing op het volgende lijkt:

```
..
#4: deploy completed for content-file world.txt on author,publish - done by 9E0729C05C54FE1A0B49431C@AdobeID at 2022-09-14T07:49:30.644Z
```

<u>Een Apache/Dispatcher-configuratie implementeren</u>

Voor dit type configuratie moet de volledige mapstructuur de vorm hebben van een ZIP-bestand.

Van de `dispatcher` van een AEM project, kunt u de configuratie van de Ontvanger door het hieronder Gemaakt bevel in werking te stellen zip:

`mvn clean package`

Of u gebruikt de opdracht onder zip vanuit het menu `src` map van de `dispatcher` module:

`zip -y -r dispatcher.zip .`

Dan stel de configuratie door dit bevel op:

`aio aem:rde:install target/aem-guides-wknd.dispatcher.cloud-X.X.X-SNAPSHOT.zip`

>[!TIP]
>
>Het bovenstaande bevel veronderstelt u opstelt [WKND](https://github.com/adobe/aem-guides-wknd) De Dispatcher-configuraties van het project. Zorg ervoor dat u de `X.X.X` met het overeenkomstige WKND aantal van de projectversie of uw project-specifiek versieaantal wanneer het opstellen van de configuratie van de Ontvanger van uw project.

>[!NOTE]
>
>RDE steunt de configuratie van de Verzender van de &quot;Flexibele wijze&quot;, maar niet de configuratie van de Verzender van de &quot;Verouderde wijze&quot;. Zie [Documentatie van Dispatcher](/help/implementing/dispatcher/disp-overview.md#validation-debug) voor informatie over de twee modi. U kunt ook de documentatie raadplegen over [migreren naar flexibele modus](/help/implementing/dispatcher/validation-debug.md#migrating), als u dat nog niet hebt gedaan.

Een succesvolle plaatsing produceert een reactie die op het volgende lijkt:

```
..
#5 deploy completed for dispatcher-config dispatcher.zip on author,publish - done by 9E0735C05T54FE1A0B49431C@AdobeID at 2022-10-03T10:26:31.286Z
Logs:
  Cloud manager validator 2.0.49
  2022/10/03 10:26:37 No issues found
  Syntax OK
```

De code die aan RDE wordt opgesteld ondergaat geen pijpleiding van de Manager van de Wolk en zijn bijbehorende kwaliteitsspoorten. De code doorloopt echter wel een analyse, die de fouten rapporteert, zoals in het onderstaande codevoorbeeld wordt geïllustreerd:

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

### Voorste code implementeren op basis van sitethema&#39;s en sitesjablonen {#deploying-themes-to-rde}

>[!NOTE]
>
> Deze functie is nog niet beschikbaar. Het zal ergens in juni worden ingevoerd.
>

RDEs steunt front-end code die op wordt gebaseerd [sitethema&#39;s](/help/sites-cloud/administering/site-creation/site-themes.md) en [sitesjablonen](/help/sites-cloud/administering/site-creation/site-templates.md). Met RDEs, wordt dit gedaan gebruikend een richtlijn van de bevellijn om voorste-eindpakketten, eerder dan de Manager van de Wolk op te stellen [Pijpleiding aan de voorzijde](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md) gebruikt voor andere omgevingstypen.

Zoals gebruikelijk, bouw uw front-end pakket gebruikend npm:

`npm run build`

Het moet een `dist/` map, zodat uw voorste pakketmap een `package.json` en `dist` map:

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

U kunt ook de `package.json` en `dist` map en implementeer dat ZIP-bestand:

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

U kunt configuraties en bundels schrappen die eerder aan RDE door middel van CLI hulpmiddelen zijn opgesteld. Gebruik de `status` gebruiken voor een lijst met handelingen die u wilt verwijderen, waaronder de opdracht `bsn` voor bundels `pid` voor vormen om in het schrappingsbevel van verwijzingen te voorzien.

Als `com.adobe.granite.demo.MyServlet.cfg.json` is geïnstalleerd, `bsn` is net `com.adobe.granite.demo.MyServlet`, zonder de **cfg.json** achtervoegsel.

Verwijderen van inhoudspakketten of inhoudsbestanden wordt niet ondersteund. Om hen te verwijderen, zou RDE moeten worden teruggesteld, die het aan een standaardstaat terugkeert.

Zie het onderstaande voorbeeld voor meer informatie:

```
aio aem:rde:delete com.adobe.granite.csrf.impl.CSRFFilter
#13: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on author - done by karl at 2022-09-12T22:01:01.955Z
#14: delete completed for osgi-config com.adobe.granite.csrf.impl.CSRFFilter on publish - done by karl at 2022-09-12T22:01:12.979Z
```

Raadpleeg de videozelfstudie voor meer informatie en demonstratie [RDE-opdrachten gebruiken (10:01)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/how-to-use.html).

## Logboeken {#rde-logging}

>[!NOTE]
>
> Deze functie is nog niet beschikbaar. Het zal ergens in juni worden ingevoerd.
> 

Gelijkaardig aan andere milieutypes, kunnen de logboekniveaus worden geplaatst door configuraties te wijzigen OSGi, hoewel zoals hierboven beschreven, het plaatsingsmodel voor RDEs een bevellijn eerder dan een plaatsing van de Manager van de Wolk impliceert. Controleer de [logboekdocumentatie](/help/implementing/developing/introduction/logging.md) voor meer informatie over het weergeven, downloaden en interpreteren van logbestanden.

RDE CLI heeft ook zijn eigen logboekbevel dat kan worden gebruikt om snel te vormen welke klassen en pakketten zouden moeten worden geregistreerd, en op welk logboekniveau. Deze configuraties kunnen als letterlijk worden beschouwd, aangezien zij niet de eigenschappen OSGI in versiecontrole wijzigen. Deze functie is gericht op het in real time stammen van logboeken in plaats van het omhoog kijken van logboeken van het verre verleden.

In het volgende voorbeeld wordt getoond hoe u de auteurslaag kunt staart, met één pakket dat is ingesteld op een logniveau voor foutopsporing en twee pakketten (gescheiden door spaties) die zijn ingesteld op een niveau voor foutopsporing voor info. Uitvoer die een **auth** pakket is gemarkeerd.

`aio aem:rde:logs --target=author --debug=org.apache.sling --info=org.apache.sling.commons.threads.impl org.apache.sling.jcr.resource.internal.helper.jcr -H .auth.`

Zie `aio aem:rde:logs --help` voor de volledige set opdrachtregelopties.

Functies:

* logboekniveaus declareren op een pakket- of klassenniveau
* het aanpassen van het formaat van de logboekoutput
* die tot vier huidige logboekconfiguraties opmaken, elk in zijn eigen terminal
* markeren, specifieke logbestanden

Merk op dat de logboeken in geheugen op RDE worden opgeslagen en deze logboeken worden gerecycled en zo worden verworpen als zij niet worden gesleept of als het netwerk te langzaam is.


## Herstellen {#reset-rde}

Als u de RDE opnieuw instelt, verwijdert u alle aangepaste code, configuraties en inhoud van zowel de auteur- als de publicatieversie. Dit terugstellen is bijvoorbeeld nuttig, als RDE is gebruikt om een specifieke eigenschap te testen en u het aan een standaardstaat wilt terugstellen zodat kunt u een verschillende eigenschap testen.

Met een reset wordt de RDE ingesteld op de laatst beschikbare AEM versie.

<!-- Alexandru: hiding for now, do not delete

Resetting can be done by way of [Cloud Manager](#reset-the-rde-cloud-manager) or by way of the [command line](#reset-the-rde-command-line). Resetting takes a few minutes and all existing content and code is deleted from the RDE.

>[NOTE!]
>
>You must be assigned the Cloud Manager Developer role to use the reset feature. If not, a reset action results in an error.

### Reset the RDE by way of Command Line {#reset-the-rde-command-line}

You can reset the RDE and return it to a default state by running:

`aio aem:rde:reset`

This usually takes a few minutes. Use the [status command](#checking-rde-status) to check when the environment is ready again.

### Reset the RDE in Cloud Manager {#reset-the-rde-cloud-manager} -->

U kunt Cloud Manager gebruiken om uw RDE opnieuw in te stellen door de volgende stappen te volgen:

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Klik het programma waarvoor u RDE wilt terugstellen.

1. Van de **Overzicht** pagina, klikt u op de **Omgevingen** aan de bovenkant van het scherm.

   ![Het tabblad Omgevingen](/help/implementing/cloud-manager/assets/environments-tab2.png)

   * U kunt ook op de knop **Alles tonen** op de knop **Omgevingen** kaart om rechtstreeks naar de **Omgevingen** tab.

     ![Alle opties tonen](/help/implementing/cloud-manager/assets/environment-showall.png)

1. De **Omgevingen** wordt geopend en worden alle omgevingen voor het programma weergegeven.

   ![Het tabblad omgevingen](/help/implementing/cloud-manager/assets/environments-tab-populated.png)

1. Klik de ellipsieknoop van RDE die u wilt terugstellen, en dan selecteren **Herstellen**.

   ![Omgevingsdetails weergeven](/help/implementing/cloud-manager/assets/rde-reset.png)

1. Bevestig dat u RDE wilt terugstellen door te klikken **Herstellen** in het dialoogvenster.

   ![Opnieuw instellen bevestigen](/help/implementing/cloud-manager/assets/rde-reset-confirm.png)

1. Cloud Manager bevestigt door middel van een bannermelding dat het herstelproces is gestart.

   ![Bannermelding opnieuw instellen](/help/implementing/cloud-manager/assets/rde-reset-banner.png)

Nadat het RDE-herstelproces is gestart, duurt het meestal een paar minuten om de omgeving te voltooien en terug te zetten naar de standaardtoestand. De status van het herstelproces kan op elk gewenst moment worden weergegeven in het dialoogvenster **Status** kolom van de **Omgevingen** of in de **Omgevingen** venster.

![Status RDE opnieuw instellen](/help/implementing/cloud-manager/assets/rde-reset-status-environments-card.png)

U kunt RDE ook opnieuw instellen gebruikend de ellipsknoop direct van **Omgevingen** kaart op **Overzicht** pagina.

![RDE herstellen van de kaart van Milieu](/help/implementing/cloud-manager/assets/rde-reset-environments-card.png)

Ga voor meer informatie over het gebruik van Cloud Manager om uw omgevingen te beheren naar [de documentatie van Cloud Manager](/help/implementing/cloud-manager/manage-environments.md).

## Opdrachten die JSON-uitvoer ondersteunen {#json-commands}

>[!NOTE]
>
> Deze opdrachten zijn nog niet beschikbaar. Ze zullen ergens in juni worden ingevoerd.
> 

De meeste opdrachten ondersteunen de globale ```--json``` markering die consoleoutput onderdrukt en geldige JSON terugkeert die in manuscripten moet worden verwerkt. Hieronder vindt u enkele ondersteunde opdrachten, met voorbeelden van de json-uitvoer.

### Status

<details>
  <summary>Uitbreiden om statusvoorbeelden weer te geven</summary>

#### Een schone RDE

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

#### Een RDE met sommige geïnstalleerde bundels

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

### Installeren

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

### Verwijderen

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

### Historie

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

### Herstellen

<details>
  <summary>Uitbreiden om voorbeelden opnieuw instellen weer te geven</summary>

#### Vuur en vergeten, geen wachttijd

```$ aio aem rde reset --no-wait --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "resetting"
}
```

#### Wacht op voltooiing

```$ aio aem rde reset --json```

```json
{
  "programId": "myProgram",
  "environmentId": "myEnv",
  "status": "reset"
}
```
</details>

### Opnieuw starten

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

Zie de [uitvoermodusdocumentatie](/help/implementing/deploying/overview.md#runmodes) voor algemene informatie over uitvoeringsmodi.

>[!NOTE]
>
>De configuratie van RDE OSGI is uniek in die zin dat het de waarden van om het even welke eigenschappen overerft OSGI die door de bundel worden verklaard `dev` uitvoeringsmodus.

RDE&#39;s verschillen van andere omgevingen omdat inhoud kan worden geïnstalleerd in de map install.load (of install.auteur.rde of install.publish.rde) onder /apps. Dit laat u inhoud aan git begaan en het leveren aan RDE gebruikend het bevel-lijn hulpmiddel.

## vullen met inhoud {#populating-content}

Wanneer een RDE wordt teruggesteld, wordt al inhoud verwijderd en zo zo, zo moet de expliciete actie worden genomen om inhoud toe te voegen. Als beste praktijken, overweeg het assembleren van een reeks inhoud die als testinhoud voor het bevestigen van of het zuiveren eigenschappen in RDE moet worden gebruikt. Er zijn verscheidene mogelijke strategieën om RDE met die inhoud te bevolken:

1. Synchroniseer het inhoudspakket uitdrukkelijk aan RDE gebruikend bevel-lijn het gebruiken

1. Plaats en wijs de steekproefinhoud in git binnen een install.rde omslag onder /apps toe en synchroniseer dan het overkoepelende inhoudspakket aan RDE gebruikend het bevel-lijn hulpmiddel.

1. Gebruik de [inhoudskopie](/help/implementing/developing/tools/content-copy.md) om een bepaalde inhoudenset van prod, stadium, of ontwikkelmilieu&#39;s, of van een andere RDE te kopiëren.

1. Pakketbeheer gebruiken

U kunt maximaal 1 GB gebruiken bij het synchroniseren van inhoudspakketten.


## Hoe verschillen RDE&#39;s van Cloud Development Environment? {#how-are-rds-different-from-cloud-development-environments}

Terwijl RDE in vele opzichten gelijkaardig aan een Milieu van de Ontwikkeling van de Wolk is, zijn er sommige kleine architecturale verschillen om voor snelle synchronisatie van code toe te staan. Het mechanisme om code aan RDE te krijgen is verschillend — voor RDEs, één synchroniseert code van een lokale ontwikkelomgeving, terwijl voor de Milieu&#39;s van de Ontwikkeling van de Wolk, één code als Manager van de Wolk opstelt.

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

Om over RDE in AEM as a Cloud Service te leren, zie de videozelfstudie die aantoont [hoe het op te zetten, hoe het te gebruiken, en de ontwikkelingscyclus (01:25)](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/developing/rde/overview.html).

# Problemen oplossen

## AIR RDE-plug-in {#aio-rde-plugin}

### fouten met ontoereikende machtigingen

Als u de RDE-plug-in wilt gebruiken, moet u lid zijn van Cloud Manager **Ontwikkelaar - Cloud Service** Productprofiel. Zie [deze pagina](/help/journey-onboarding/assign-profiles-cloud-manager.md#assign-developer) voor meer informatie .

Alternatief, kunt u bevestigen dat u deze ontwikkelaarrol hebt als u login aan de ontwikkelaarsconsole kunt door dit bevel in werking te stellen:

`aio cloudmanager:environment:open-developer-console`

>[!TIP]
>
>Als u de `Warning: cloudmanager:* is not a aio command.` fout, moet u installeren [aio-cli-plugin-cloudmanager](https://github.com/adobe/aio-cli-plugin-cloudmanager) door de onderstaande opdracht uit te voeren:
>
>```
>aio plugins:install @adobe/aio-cli-plugin-cloudmanager
>```

Controleren of de aanmelding is voltooid door uitvoering

`aio cloudmanager:list-programs`

Dit zou van alle programma&#39;s onder uw gevormde organisatie moeten een lijst maken en bevestigen dat u de correcte toegewezen rol hebt.
