---
title: CRXDE Lite gebruiken
description: CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser.
exl-id: 1581a7e5-6f84-4a45-8e8f-c83692ea077a
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1678'
ht-degree: 0%

---

# CRXDE Lite gebruiken {#using-crxde-lite}

CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser. Met CRXDE Lite kunt u bestanden, mappen, knooppunten en eigenschappen bewerken. De gehele opslagplaats is voor u toegankelijk in deze gebruiksvriendelijke interface.

>[!NOTE]
>
>CRXDE Lite is alleen beschikbaar in uw lokale ontwikkelomgevingen. Het is niet beschikbaar in AEM as a Cloud Service.

## Aan de slag met CRXDE Lite {#getting-started-with-crxde-lite}

Aan de slag met CRXDE Lite:

1. Start uw lokale AEM-ontwikkeling snel.
1. Open de URL in uw browser `https://<host>:<port>/crx/de`.
1. Voer uw **gebruikersnaam** en **password**.
1. Klikken **OK**.

De gebruikersinterface van CRXDE Lite wordt als volgt weergegeven in uw browser:

![De interface CRXDE Lite](assets/crxde-lite.png)

>[!TIP]
>
>U kunt CRXDE Lite ook openen via het menu AEM. Selecteer in het hoofdmenu **Gereedschappen** > **Algemeen** > **CRXDE Lite**.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

De gebruikersinterface van CRXDE Lite bevat veel onderdelen en functies.

### Bovenste schakelbalk {#top-switcher-bar}

De hoogste Bar van de Schakelaar laat u snel tussen CRXDE Lite en schakelen [Package Manager.](package-manager.md)

### Knooppuntwidget {#node-path-widget}

De widget Pad knooppunt geeft het pad naar het momenteel geselecteerde knooppunt weer.

U kunt het ook gebruiken om naar een knoop te springen door de weg in te gaan door het hand in te gaan of het van elders te kleven en binnengaan te drukken.

Het biedt ook ondersteuning voor het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of selecteer het zoekpictogram aan de rechterkant). Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die momenteel in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de hele repository wilt doorzoeken, gebruikt u **Gereedschappen** ->: **Query**.

### Explorer-venster {#explorer-pane}

De **Explorer-venster** geeft een structuur weer van alle knooppunten in de opslagplaats.

Klik op een knooppunt om de eigenschappen ervan weer te geven in het dialoogvenster **Eigenschappen** tab. Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.

Met het structuurnavigatiefilter (het binoculars-pictogram) kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is alleen van toepassing op knooppunten die lokaal zijn geladen.

### Venster bewerken {#edit-pane}

De **Venster bewerken** Hiermee kunt u de inhoud van het geselecteerde bestand in de opslagplaats bekijken. Elk geopend bestand wordt in het deelvenster weergegeven als een eigen tabblad.

De **Home** kunt u zoeken in inhoud en/of documentatie en toegang krijgen tot de documentatie en ondersteuning van Adoben van ontwikkelaars.

Dubbelklik op een bestand in het dialoogvenster **Explorer-venster** om de inhoud ervan in de **Venster bewerken**. U kunt het dan wijzigen en de veranderingen bewaren.

Als een bestand eenmaal is bewerkt in de **Venster bewerken** zijn de volgende gereedschappen beschikbaar op de werkbalk:

* **Tonen in boomstructuur** - Geeft het bestand weer in de boomstructuur van de opslagplaats.
* **Zoeken/vervangen** - Voert een zoekopdracht of vervangactie uit.

Dubbelklik op de statusregel van het dialoogvenster **Venster bewerken** opent de **Ga naar regel** zodat u een specifiek regelnummer kunt invoeren.

### Tabblad Eigenschappen {#properties-tab}

De **Tabblad Eigenschappen** Hiermee geeft u de eigenschappen weer van het knooppunt dat u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen verwijderen.

### Tabblad Toegangsbeheer {#access-control-tab}

De **Tabblad Toegangsbeheer** geeft rechten weer op basis van het huidige pad, de huidige opslagplaats of het huidige hoofd.

De machtigingen zijn onderverdeeld in de volgende categorieën.

* **Toepasselijk toegangsbeheerbeleid** - Het beleid dat op de huidige selectie kan worden toegepast
* **Lokaal beleid voor toegangsbeheer** - Het huidige beleid dat lokaal wordt toegepast op de huidige selectie
* **Effectief beleid voor toegangscontrole** - Het huidige beleid dat wordt toegepast voor de huidige selectie, die lokaal kan worden ingesteld of kan worden overgeërfd van bovenliggende knooppunten

>[!NOTE]
>
Om toegangsbeheerinformatie te kunnen zien, moet de gebruiker het programma opent aan CRXDE Lite rechten hebben om ACL ingangen te lezen.

### Tabblad Replicatie {#replication-tab}

De **Tabblad Replicatie** Toont de replicatiestatus van huidige knoop. U kunt het huidige knooppunt repliceren en herhalen.

### Tabblad Console {#console-tab}

De **Tabblad Console** geeft logberichten weer. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie vastzetten en het tonen van berichten toelaten/onbruikbaar maken.

### Tabblad Informatie maken {#build-info-tab}

De **Tabblad Informatie maken** geeft informatie weer wanneer een bundel wordt gemaakt.

### Knop Vernieuwen {#refresh-button}

De **Knop Vernieuwen** Hiermee vernieuwt u de huidige selectie. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.

### Alle knoppen opslaan {#save-all-button}

De **Alle knoppen opslaan** Hiermee slaat u alle aangebrachte wijzigingen op. Tot u verkiest om te bewaren, zijn de veranderingen tijdelijk, en verloren wanneer u de console weggaat.

* **Vorige versie** - Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in het geselecteerde knooppunt sinds de laatste opslaghandeling en wordt vervolgens de huidige status van de opslagplaats voor het geselecteerde knooppunt opnieuw geladen
* **Alles terugkeren** - Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in de gehele opslagplaats sinds de laatste opslaghandeling, en wordt vervolgens de huidige status van de opslagplaats opnieuw geladen

### Knop Maken {#create-button}

De **Knop Maken** is een drop-down menu om het volgende onder de geselecteerde knoop tot stand te brengen:

* Node - een knoop met een willekeurig knooptype
* Bestand - een `nt:file` node en its nt:resource subnode
* Map - een `nt:folder` node

### Knop Verwijderen {#delete-button}

De **Knop Verwijderen** Hiermee verwijdert u het geselecteerde knooppunt.

### Knop kopiëren {#copy-button}

De **Knop kopiëren** Kopieert het geselecteerde knooppunt.

## Knop Plakken {#paste-button}

De **Knop Plakken** plakt het gekopieerde knooppunt onder het geselecteerde knooppunt.

### Knop Verplaatsen {#move-button}

De **Knop Verplaatsen** Hiermee wordt het geselecteerde knooppunt verplaatst naar het knooppunt dat via het dialoogvenster is ingesteld.

### Naam wijzigen {#rename-button}

De **Knop Naam wijzigen** wijzigt de naam van het geselecteerde knooppunt.

### Mixins {#mixins-button}

De **Mixins, knop** Hiermee kunt u gemengde typen toevoegen aan het knooppunttype. De mixintypen worden meestal gebruikt om geavanceerde functies toe te voegen.

### Gereedschappen {#tools-button}

De **Gereedschapknop** is een vervolgkeuzemenu met de volgende gereedschappen beschikbaar:

* **Serverconfiguratie** - toegang tot de Felix-console (ook beschikbaar op `https://<host>:<port>/system/console/configMgr`)
* **Query** - de gegevensopslagplaats opvragen
* **Rechten** - om rechten weer te geven en toe te voegen
* **Toegangsbeheer testen** - om de toestemming voor bepaalde paden en/of aangever te testen
* **Notitietype exporteren** - knooppunttypen in het systeem exporteren als CND-notatie
* **Notitietype importeren** - om knooppunttypes in te voeren gebruikend aantekening CND.

### Aanmeldingswidget {#login-widget}

De **Aanmeldingswidget** geeft de momenteel aangemelde gebruiker weer.

Klik op deze knop om u aan te melden of opnieuw aan te melden als een andere gebruiker. De `@crx.default` geeft aan dat u zich in de standaardwerkruimte (en alleen) in de repository bevindt.

De **Voorkeuren** U kunt deze optie gebruiken om de taal van de gebruikersinterface in te stellen en de sneltoetsen voor verschillende handelingen, zoals opslaan, zoeken, notities maken enzovoort, weer te geven en aan te passen.

## Een map maken {#creating-a-folder}

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waaronder u de nieuwe map wilt maken en selecteer **Maken...** vervolgens **Map maken...**.

1. Voer de map in **Naam** en klik op **OK**.

1. Klikken **Alles opslaan** om de wijzigingen op de server op te slaan.

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de [**Deelvenster Exploderer**,](#explorer-pane) Klik met de rechtermuisknop op het knooppunt waar u het nieuwe knooppunt wilt maken, selecteer **Maken** vervolgens **Knooppunt maken**.
1. Voer de **Naam** en selecteert u de **Type**.
1. Klikken **OK**.
1. Klik op de knop [**Alle knoppen opslaan**](#save-all-button) om de wijzigingen op de server op te slaan.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

>[!NOTE]
>
De meeste bewerkingen, inclusief **Knooppunt maken**, houdt alle wijzigingen in het geheugen bij en slaat deze alleen op in de opslagplaats bij het opslaan (met de [**Alle knoppen opslaan**](#save-all-button)). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
>
De validatie met betrekking tot of het gemaakte knooppunt wordt toegestaan door het knooppunttype van het bovenliggende knooppunt, wordt ook uitgevoerd door de gegevensopslagruimte wanneer wijzigingen worden opgeslagen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, controleert u of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured` knooppunt als onderliggend element van `nt:folder` knooppunt).

## Een eigenschap maken {#creating-a-property}

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de [**Deelvenster Exploderer**,](#explorer-pane) Selecteer het knooppunt waaraan u de nieuwe eigenschap wilt toevoegen.
1. In de [**Tabblad Eigenschappen**](#properties-tab) Voer in het onderste venster het **Naam** de **Type** en de **Waarde**.
1. Klikken **Toevoegen**.
1. Klik op de knop [**Alle knoppen opslaan**](#save-all-button) om de wijzigingen op de server op te slaan.

## Een bestand maken {#creating-a-file}

Een bestand maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In de [**Deelvenster Exploderer**,](#explorer-pane) Klik met de rechtermuisknop op de component waar u het bestand wilt maken, selecteer **Maken** vervolgens **Bestand maken**.
1. Voer het bestand in **Naam** , met inbegrip van de verlenging ervan.
1. Klikken **OK**.
1. Het nieuwe bestand wordt geopend als een tabblad in het dialoogvenster [**Venster bewerken**.](#edit-pane)
1. Bewerk het bestand.
1. Klik op de knop [**Alle knoppen opslaan**](#save-all-button) om de wijzigingen op te slaan

## Nodetypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite kunt u knooppunttypedefinities importeren en/of exporteren in [Compacte naamruimte en knooppuntdefinitie (CND)](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van een knooptype exporteren in CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteren **Gereedschappen** dan **Notitietype exporteren**.
1. De definitie wordt weergegeven in CND-notatie op een nieuw tabblad in uw browser.
1. Sla indien nodig de gegevens op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteren **Gereedschappen** dan **Notitietype importeren**.
1. Er wordt een nieuw tabblad geopend in het dialoogvenster [**Venster bewerken**](#edit-pane) gelabeld **Notitietype importeren**.
1. Voer de CND-notatie voor de definitie in het tekstvak van het dialoogvenster **Notitietype importeren** tab.
1. Controleren **Update toestaan** als u een bestaande definitie bijwerkt.
1. Klikken **Importeren**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand weergeven `error.log` die zich in het bestandssysteem bevindt op `<aem-install-dir>/crx-quickstart/logs` en filtreer het met het aangewezen logboekniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. In het vervolgkeuzemenu rechts van het dialoogvenster [**Tabblad Console**](#console-tab) onder aan het venster selecteert u **Serverlogboeken**.
1. Klik op de knop **Stoppen** om de berichten weer te geven.

U kunt:

* Pas de logboekparameters in de Console van het Felix aan door te klikken **Logboekconfiguraties** pictogram.
* De berichten wissen door op de knop **Console wissen** pictogram.
* Plaats het bericht op de huidige selectie door op de knop **Puntconsole** pictogram.
* De weergave van berichten in- of uitschakelen door op de knop **Stoppen** pictogram.
