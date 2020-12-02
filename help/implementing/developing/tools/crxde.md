---
title: CRXDE Lite gebruiken
description: CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 0%

---


# CRXDE Lite {#using-crxde-lite} gebruiken

CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser. Met CRXDE Lite kunt u bestanden, mappen, knooppunten en eigenschappen bewerken. De gehele opslagplaats is voor u toegankelijk in deze gebruiksvriendelijke interface.

>[!NOTE]
>
>CRXDE Lite is alleen beschikbaar in uw lokale ontwikkelomgevingen. Het is niet beschikbaar in AEM als Cloud Service.

## Aan de slag met CRXDE Lite {#getting-started-with-crxde-lite}

Aan de slag met CRXDE Lite:

1. Start uw lokale AEM ontwikkeling snel.
1. Open de URL `https://<host>:<port>/crx/de` in uw browser.
1. Voer uw **gebruikersnaam** en **wachtwoord** in.
1. Klik **OK**.

De gebruikersinterface van CRXDE Lite ziet er als volgt uit in uw browser:

![De interface CRXDE Lite](assets/crxde-lite.png)

U kunt nu CRXDE Lite gebruiken om uw toepassing te ontwikkelen.

>[!TIP]
>
>U kunt CRXDE Lite ook openen via het menu AEM. Selecteer **Gereedschappen** -> **Algemeen** -> **CRXDE Lite**.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

De gebruikersinterface van CRXDE Lite bevat veel onderdelen en functies.

### Bovenste schakelbalk {#top-switcher-bar}

De hoogste Bar van de Schakelaar staat u toe om tussen CRXDE Lite, de Manager van het Pakket, en het Aandeel van het Pakket snel te schakelen.

### Knooppuntwidget {#node-path-widget}

De widget Pad knooppunt geeft het pad naar het momenteel geselecteerde knooppunt weer.

U kunt het ook gebruiken om naar een knoop te springen door de weg in te gaan door het hand in te gaan of het van elders te kleven en binnengaan te drukken.

Het biedt ook ondersteuning voor het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of selecteer het zoekpictogram aan de rechterkant). Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die momenteel in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de hele opslagplaats wilt doorzoeken, gebruikt u **Tools** -&amp;gt: **Query**.

### Deelvenster Verkenner {#explorer-pane}

In het **Explorer-venster** wordt een boomstructuur weergegeven van alle knooppunten in de opslagplaats.

Klik een knoop om zijn eigenschappen op **Eigenschappen** tabel te tonen. Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.

Met het structuurnavigatiefilter (het binoculars-pictogram) kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is alleen van toepassing op knooppunten die lokaal zijn geladen.

### Deelvenster {#edit-pane} bewerken

Met het venster **Bewerken kunt u de inhoud van het geselecteerde bestand weergeven in de opslagplaats.** Elk geopend bestand wordt in het deelvenster weergegeven als een eigen tabblad.

Met het tabblad **Home** kunt u zoeken in inhoud en/of documentatie en toegang krijgen tot de documentatie van ontwikkelaars en ondersteuning voor Adobe.

Dubbelklik op een bestand in het **Verkenner-venster** om de inhoud ervan weer te geven in het **Venster bewerken**. U kunt het dan wijzigen en de veranderingen bewaren.

Nadat een bestand is bewerkt in het venster **Bewerken**, zijn de volgende gereedschappen beschikbaar op de werkbalk:

* **Tonen in boomstructuur**  - Geeft het bestand weer in de boomstructuur van de gegevensopslagruimte.
* **Zoeken/vervangen** : hiermee wordt een zoekopdracht of een vervangactie uitgevoerd.

Dubbelklik op de statusregel van **Venster bewerken** opent het dialoogvenster **Ga naar regel** zodat u een specifiek regelnummer kunt invoeren.

### Tabblad Eigenschappen {#properties-tab}

Het **lusje van Eigenschappen** toont de eigenschappen van de knoop die u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen verwijderen.

### Tabblad Toegangsbeheer {#access-control-tab}

Het **Toegangsbeheer Tab** toont toestemmingen die op de huidige weg, de bewaarplaats, of het hoofd worden gebaseerd.

De machtigingen zijn onderverdeeld in de volgende categorieën.

* **Toepasselijk toegangsbeheerbeleid**  - Het beleid dat op de huidige selectie kan worden toegepast
* **Lokaal beleid**  voor toegangsbeheer: het huidige beleid dat lokaal wordt toegepast op de huidige selectie
* **Effectief beleid**  voor toegangsbeheer: het huidige beleid dat wordt toegepast op de huidige selectie, die lokaal kan worden ingesteld of kan worden overgeërfd van bovenliggende knooppunten

>[!NOTE]
Om toegangsbeheerinformatie te kunnen zien, moet de gebruiker het programma opent aan CRXDE Lite rechten hebben om ACL ingangen te lezen.

### Tabblad Replicatie {#replication-tab}

Het **lusje van de Replicatie** toont de replicatiestatus van huidige knoop. U kunt het huidige knooppunt repliceren en herhalen.

###  Tabblad Console {#console-tab}

Op het tabblad **Console** worden logboekberichten weergegeven. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie vastzetten en het tonen van berichten toelaten/onbruikbaar maken.

### Tabblad Informatie maken {#build-info-tab}

Het **tabblad Build Info** geeft informatie weer wanneer een bundel wordt gebouwd.

### Knop {#refresh-button} vernieuwen

Met de knop **Vernieuwen** wordt de huidige selectie vernieuwd. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.

### Alle knoppen opslaan {#save-all-button}

Met de **Alle knoppen opslaan** slaat u alle aangebrachte wijzigingen op. Tot u verkiest om te bewaren, zijn de veranderingen tijdelijk, en zullen verloren gaan wanneer u de console weggaat.

* **Vorige versie**  - Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in het geselecteerde knooppunt sinds de laatste opslaghandeling en wordt vervolgens de huidige status van de opslagruimte voor het geselecteerde knooppunt opnieuw geladen
* **Alles**  terugdraaien - Alle wijzigingen die u hebt aangebracht in de gehele opslagplaats sinds de laatste opslaghandeling worden genegeerd en vervolgens wordt de huidige status van de opslagplaats opnieuw geladen

### Knop {#create-button} maken

De **Create Button** is een vervolgkeuzemenu om onder het geselecteerde knooppunt het volgende te maken:

* Knooppunt - een knoop met een willekeurig knooppunttype
* File - an `nt:file` node and its nt:resource subnode
* Map - een `nt:folder`-knooppunt

### Knop {#delete-button} verwijderen

Met de **knop Verwijderen** verwijdert u het geselecteerde knooppunt.

### Knop {#copy-button} kopiëren

Met de **Knop Kopiëren** kopieert u het geselecteerde knooppunt.

## Knop Plakken {#paste-button}

Met de **Knop Plakken** plakt u het gekopieerde knooppunt onder het geselecteerde knooppunt.

### Knop Verplaatsen {#move-button}

Met de **knop Verplaatsen** wordt het geselecteerde knooppunt verplaatst naar het knooppunt dat via het dialoogvenster is ingesteld.

### Naam wijzigen {#rename-button}

De naam van het geselecteerde knooppunt wordt gewijzigd door **Naam van knop wijzigen**.

### Mixins {#mixins-button}

Met de **Mixins Button** kunt u mixintypen toevoegen aan het knooppunttype. De mixintypen worden meestal gebruikt om geavanceerde functies toe te voegen.

### Opties {#tools-button}

De **knop Gereedschappen** is een vervolgkeuzemenu met de volgende gereedschappen:

* **Serverconfiguratie**  - voor toegang tot de Felix-console (ook beschikbaar op  `https://<host>:<port>/system/console/configMgr`)
* **Vraag** - om een query op de gegevensopslagruimte
* **Bevoegdheden**  - om rechten weer te geven en toe te voegen
* **Toegangsbeheer**  testen - om de toestemming voor bepaalde weg en/of hoofd te testen
* **Node Type**  van de Uitvoer - om knooptypes in het systeem als aantekening CND uit te voeren
* **Type**  knooppunt importeren - voor het importeren van knooppunttypen met behulp van CND-notatie.

### Aanmeldingswidget {#login-widget}

Met de **Aanmeldingswidget** wordt de momenteel aangemelde gebruiker weergegeven.

Klik op deze knop om u aan te melden of opnieuw aan te melden als een andere gebruiker. De `@crx.default` staat voor de standaardwerkruimte (en alleen) in de repository.

De optie **Voorkeuren** kan worden gebruikt om de taal van de gebruikersinterface in te stellen en de sneltoetsen voor verschillende handelingen, zoals opslaan, zoeken, notitie maken, enz., weer te geven en aan te passen.

## Een map {#creating-a-folder} maken

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waaronder u de nieuwe map wilt maken en selecteer **Maken..**, dan **Map maken..**.

1. Voer de map **Naam** in en klik op **OK**.

1. Klik **Alles opslaan** om de wijzigingen op de server op te slaan.

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In [**Deelvenster Exploderer**, ](#explorer-pane) klikt u met de rechtermuisknop op het knooppunt waar u het nieuwe knooppunt wilt maken. Selecteer **Maken** en **Node maken**.
1. Voer de **Naam** in en selecteer **Type**.
1. Klik **OK**.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen op de server te bewaren.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

>[!NOTE]
De meeste bewerkingsbewerkingen, inclusief **Node maken**, houden alle wijzigingen in het geheugen en slaan deze alleen op in de opslagplaats wanneer ze worden opgeslagen (met de [**Alle knop opslaan**](#save-all-button)). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
De validatie met betrekking tot het al dan niet toestaan van het nieuwe knooppunt door het knooppunttype van het bovenliggende knooppunt wordt ook uitgevoerd door de gegevensopslagruimte wanneer wijzigingen worden opgeslagen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, moet u controleren of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured`-knooppunt maken als onderliggend knooppunt van `nt:folder`).

## Een eigenschap {#creating-a-property} maken

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In [**Deelvenster Exploderer**, ](#explorer-pane) selecteert de knoop waar u het nieuwe bezit wilt toevoegen.
1. Typ op het tabblad [**Eigenschappen**](#properties-tab) in het onderste venster de **Naam**, het **Type** en de **Waarde**.
1. Klik **Add**.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen op de server te bewaren.

## Een bestand {#creating-a-file} maken

Een nieuw bestand maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In [**Deelvenster Exploderer**, ](#explorer-pane) klikt u met de rechtermuisknop op de component waar u het bestand wilt maken. Selecteer **Maken** en **Bestand maken**.
1. Voer het bestand **Naam** in, inclusief de extensie ervan.
1. Klik **OK**.
1. Het nieuwe bestand wordt geopend als een tabblad in het [**Venster bewerken**.](#edit-pane)
1. Bewerk het bestand.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen te bewaren.

## Knooppunttypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite kunt u knooppunttypedefinities importeren en/of exporteren in de notatie [Compacte naamruimte en knooppuntdefinitie (CND)](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van een knooptype exporteren in CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteer **Gereedschappen** dan **Nodetype** exporteren.
1. De definitie wordt in de CND-notatie weergegeven op een nieuw tabblad in uw browser.
1. Sla de gegevens indien nodig op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteer **Gereedschappen** dan **Nodetype** importeren.
1. Er wordt een nieuw tabblad geopend in het [**Venster bewerken**](#edit-pane) met het label **Nodetype importeren**.
1. Voer de CND-notatie voor de definitie in het tekstvak in van het tabblad **Type knooppunt importeren**.
1. Schakel **Update** toestaan in als u een bestaande definitie bijwerkt.
1. Klik **Importeren**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand `error.log` weergeven dat zich op het bestandssysteem bevindt op `<aem-install-dir>/crx-quickstart/logs` en dit filteren met het juiste logniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. Selecteer **Serverlogbestanden** in het vervolgkeuzemenu rechts van het tabblad [**Console**](#console-tab) onder aan het venster.
1. Klik op het pictogram **Stoppen** om de berichten weer te geven.

U kunt:

* Pas de logboekparameters in de Console van Felix aan door het **Logging Configurations** pictogram te klikken.
* Wis de berichten door **Duidelijke Console** te klikken pictogram.
* Zet het bericht vast bij de huidige selectie door op het pictogram **Pin Console** te klikken.
* Schakel de weergave van berichten in of uit door op het pictogram **Stop** te klikken.
