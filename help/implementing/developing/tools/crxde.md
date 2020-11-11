---
title: CRXDE Lite gebruiken
description: CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser.
translation-type: tm+mt
source-git-commit: c40d668cb6dcf5c3e2d09504b547457306a99c85
workflow-type: tm+mt
source-wordcount: '1705'
ht-degree: 0%

---


# CRXDE Lite gebruiken {#using-crxde-lite}

CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser. Met CRXDE Lite kunt u bestanden, mappen, knooppunten en eigenschappen bewerken. De gehele opslagplaats is voor u toegankelijk in deze gebruiksvriendelijke interface.

>[!NOTE]
>
>CRXDE Lite is alleen beschikbaar in uw lokale ontwikkelomgevingen. Het is niet beschikbaar in AEM als Cloud Service.

## Aan de slag met CRXDE Lite {#getting-started-with-crxde-lite}

Aan de slag met CRXDE Lite:

1. Start uw lokale AEM ontwikkeling snel.
1. Open de URL in uw browser `https://<host>:<port>/crx/de`.
1. Voer uw **gebruikersnaam** en **wachtwoord** in.
1. Click **OK**.

De gebruikersinterface van CRXDE Lite ziet er als volgt uit in uw browser:

![De interface CRXDE Lite](assets/crxde-lite.png)

U kunt nu CRXDE Lite gebruiken om uw toepassing te ontwikkelen.

>[!TIP]
>
>U kunt CRXDE Lite ook openen via het menu AEM. Selecteer in het hoofdmenu **Gereedschappen** -> **Algemeen** -> **CRXDE Lite**.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

De gebruikersinterface van CRXDE Lite bevat veel onderdelen en functies.

### Bovenste schakelbalk {#top-switcher-bar}

De hoogste Bar van de Schakelaar staat u toe om tussen CRXDE Lite, de Manager van het Pakket, en het Aandeel van het Pakket snel te schakelen.

### Knooppuntwidget {#node-path-widget}

De widget Pad knooppunt geeft het pad naar het momenteel geselecteerde knooppunt weer.

U kunt het ook gebruiken om naar een knoop te springen door de weg in te gaan door het hand in te gaan of het van elders te kleven en binnengaan te drukken.

Het biedt ook ondersteuning voor het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of selecteer het zoekpictogram aan de rechterkant). Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die momenteel in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de hele repository wilt doorzoeken, gebruikt u **Tools** -&amp;gt: **Query**.

### Venster Explorer {#explorer-pane}

In het deelvenster **** Verkenner wordt een structuur weergegeven van alle knooppunten in de opslagplaats.

Klik op een knooppunt om de eigenschappen ervan weer te geven op het tabblad **Eigenschappen** . Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.

Met het structuurnavigatiefilter (het binoculars-pictogram) kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is alleen van toepassing op knooppunten die lokaal zijn geladen.

### Venster bewerken {#edit-pane}

In het deelvenster **** Bewerken kunt u de inhoud van het geselecteerde bestand weergeven in de opslagplaats. Elk geopend bestand wordt in het deelvenster weergegeven als een eigen tabblad.

Op het tabblad **Home** kunt u zoeken in inhoud en/of documentatie en toegang krijgen tot documentatie van ontwikkelaars en ondersteuning voor Adobe.

Dubbelklik op een bestand in het deelvenster **Verkenner** om de inhoud ervan weer te geven in het deelvenster **Bewerken**. U kunt het dan wijzigen en de veranderingen bewaren.

Als een bestand eenmaal is bewerkt in het deelvenster **Bewerken**, zijn de volgende gereedschappen beschikbaar op de werkbalk:

* **Tonen in boomstructuur** - Geeft het bestand weer in de boomstructuur van de gegevensopslagruimte.
* **Zoeken/vervangen** - Hiermee wordt een zoekopdracht of vervangactie uitgevoerd.

Dubbelklik op de statusregel van het deelvenster **** Bewerken om het dialoogvenster **Ga naar regel** te openen, zodat u een specifiek regelnummer kunt invoeren.

### Tabblad Eigenschappen {#properties-tab}

Op het tabblad **Eigenschappen** worden de eigenschappen weergegeven van het knooppunt dat u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen verwijderen.

### Tabblad Toegangsbeheer {#access-control-tab}

Op het tabblad **Toegangsbeheer** worden bevoegdheden weergegeven op basis van het huidige pad, de huidige opslagplaats of het huidige hoofd.

De machtigingen zijn onderverdeeld in de volgende categorieën.

* **Toepasselijk toegangsbeheerbeleid** - Het beleid dat op de huidige selectie kan worden toegepast
* **Lokaal beleid** voor toegangsbeheer - Het huidige beleid dat lokaal wordt toegepast op de huidige selectie
* **Effectief beleid** voor toegangsbeheer - Het huidige beleid dat wordt toegepast op de huidige selectie, die lokaal kan worden ingesteld of kan worden overgeërfd van bovenliggende knooppunten

>[!NOTE]
Om toegangsbeheerinformatie te kunnen zien, moet de gebruiker het programma opent aan CRXDE Lite rechten hebben om ACL ingangen te lezen.

### Tabblad Replicatie {#replication-tab}

Het lusje **van de** Replicatie toont de replicatiestatus van huidige knoop. U kunt het huidige knooppunt repliceren en herhalen.

###  Tabblad Console {#console-tab}

Op het tabblad **Console** worden logboekberichten weergegeven. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie vastzetten en het tonen van berichten toelaten/onbruikbaar maken.

### Tabblad Informatie maken {#build-info-tab}

Het tabblad **** Build Info geeft informatie weer wanneer een bundel wordt gemaakt.

### Knop Vernieuwen {#refresh-button}

Met de knop **** Vernieuwen wordt de huidige selectie vernieuwd. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.

### Alle knoppen opslaan {#save-all-button}

Met de knop **Alles** opslaan slaat u alle aangebrachte wijzigingen op. Tot u verkiest om te bewaren, zijn de veranderingen tijdelijk, en zullen verloren gaan wanneer u de console weggaat.

* **Vorige versie** - Hiermee worden alle wijzigingen genegeerd die u hebt aangebracht in het geselecteerde knooppunt sinds de laatste opslaghandeling en wordt vervolgens de huidige status van de opslagplaats voor het geselecteerde knooppunt opnieuw geladen
* **Alles** terugdraaien - Alle wijzigingen die u hebt aangebracht in de gehele opslagplaats sinds de laatste opslaghandeling, worden verwijderd en vervolgens de huidige status van de opslagplaats opnieuw geladen

### Knop Maken {#create-button}

De knop **Maken** is een vervolgkeuzelijst voor het maken van het volgende onder het geselecteerde knooppunt:

* Knooppunt - een knoop met een willekeurig knooppunttype
* File - an `nt:file` node and its nt:resource subnode
* Map - een `nt:folder` knooppunt

### Delete Button {#delete-button}

Met de knop **** Verwijderen verwijdert u het geselecteerde knooppunt.

### Knop Kopiëren {#copy-button}

Met de knop **Kopiëren** kopieert u het geselecteerde knooppunt.

## Knop Plakken {#paste-button}

Met de knop **** Plakken plakt u het gekopieerde knooppunt onder het geselecteerde knooppunt.

### Knop Verplaatsen {#move-button}

Met de knop **Verplaatsen** wordt het geselecteerde knooppunt verplaatst naar het knooppunt dat via het dialoogvenster is ingesteld.

### Naam wijzigen {#rename-button}

Met de knop **Naam wijzigen** wijzigt u de naam van het geselecteerde knooppunt.

### Mixins {#mixins-button}

Met de knop **Mixins** kunt u mixingtypen toevoegen aan het knooppunttype. De mixintypen worden meestal gebruikt om geavanceerde functies toe te voegen.

### Opties {#tools-button}

De knop **Gereedschappen** is een vervolgkeuzemenu met de volgende gereedschappen:

* **Serverconfiguratie** - voor toegang tot de Felix-console (ook beschikbaar op `https://<host>:<port>/system/console/configMgr`)
* **Vraag** - om de gegevensopslagplaats te vragen
* **Bevoegdheden** - om rechten weer te geven en toe te voegen
* **Toegangsbeheer** testen - om de toestemming voor bepaalde paden en/of hoofdletters te testen
* **Nodetype** exporteren - knooppunttypen in het systeem exporteren als CND-notatie
* **Node Type** van de invoer - om knooptypes in te voeren gebruikend aantekening CND.

### Aanmeldingswidget {#login-widget}

In de **aanmeldwidget** wordt de momenteel aangemelde gebruiker weergegeven.

Klik op deze knop om u aan te melden of opnieuw aan te melden als een andere gebruiker. Het `@crx.default` geeft aan dat u zich in de standaardwerkruimte (en alleen) in de opslagplaats bevindt.

Met de optie **Voorkeuren** kunt u de taal van de gebruikersinterface instellen en de sneltoetsen weergeven en aanpassen voor verschillende handelingen, zoals opslaan, zoeken, notities maken, enzovoort.

## Een map maken {#creating-a-folder}

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. Klik in het navigatievenster met de rechtermuisknop op de map waaronder u de nieuwe map wilt maken, selecteer **Maken ...** en **Map maken..**.

1. Voer de **mapnaam** in en klik op **OK**.

1. Klik op Alles **** opslaan om de wijzigingen op de server op te slaan.

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het [**deelvenster** Exploderer met de rechtermuisknop op het knooppunt waar u het nieuwe knooppunt wilt maken, selecteer](#explorer-pane) Maken **en** Node **** maken.
1. Voer de **naam** in en selecteer het **type**.
1. Click **OK**.
1. Klik op de knop [**Alles**](#save-all-button) opslaan om de wijzigingen op de server op te slaan.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

>[!NOTE]
De meeste bewerkingen, waaronder Node **maken**, houden alle wijzigingen in het geheugen bij en slaan deze alleen op in de opslagplaats wanneer ze worden opgeslagen (met de knop [**Alles opslaan**](#save-all-button)). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
De validatie met betrekking tot het al dan niet toestaan van het nieuwe knooppunt door het knooppunttype van het bovenliggende knooppunt wordt ook uitgevoerd door de gegevensopslagruimte wanneer wijzigingen worden opgeslagen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, moet u controleren of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured` knooppunt maken als onderliggend knooppunt van een `nt:folder` knooppunt).

## Een eigenschap maken {#creating-a-property}

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer in het deelvenster [**Exploderer** het knooppunt waar u de nieuwe eigenschap wilt toevoegen](#explorer-pane) .
1. Voer op het tabblad [**Eigenschappen**](#properties-tab) in het onderste venster de **naam**, het **type** en de **waarde** in.
1. Click **Add**.
1. Klik op de knop [**Alles**](#save-all-button) opslaan om de wijzigingen op de server op te slaan.

## Een bestand maken {#creating-a-file}

Een nieuw bestand maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Klik in het deelvenster [**Exploderer** met de rechtermuisknop op de component waar u het bestand wilt maken,](#explorer-pane) selecteer **Maken** en **Bestand** maken.
1. Voer de **bestandsnaam** en de extensie in.
1. Click **OK**.
1. Het nieuwe bestand wordt geopend als een tabblad in het deelvenster [**Bewerken**.](#edit-pane)
1. Bewerk het bestand.
1. Klik op de knop [**Alles**](#save-all-button) opslaan om de wijzigingen op te slaan.

## Nodetypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite kunt u knooppunttypedefinities importeren en/of exporteren in [compacte naamruimte- en knooppunttypedefinitie (CND)-notatie](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van een knooptype exporteren in CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteer **Gereedschappen** en **Exporteer knooppunttype**.
1. De definitie wordt in de CND-notatie weergegeven op een nieuw tabblad in uw browser.
1. Sla de gegevens indien nodig op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteer **Gereedschappen** en **Importeer knooppunttype**.
1. Er wordt een nieuw tabblad geopend in het deelvenster [**Bewerken**](#edit-pane) met het label **Importknooppunttype**.
1. Voer de CND-notatie voor de definitie in het tekstvak op het tabblad Type **knooppunt** importeren in.
1. Schakel Update **** toestaan in als u een bestaande definitie bijwerkt.
1. Klik op **Importeren**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand weergeven `error.log` dat zich op het bestandssysteem bevindt `<aem-install-dir>/crx-quickstart/logs` en dit filteren met het gewenste logniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. Selecteer [**Serverlogbestanden**](#console-tab) in het vervolgkeuzemenu rechts van het tabblad **Console** onder in het venster.
1. Klik op het pictogram **Stoppen** om de berichten weer te geven.

U kunt:

* Pas de logparameters in de Felix-console aan door op het pictogram **Logging Configurations** te klikken.
* Wis de berichten door het **Duidelijke pictogram van de Console** te klikken.
* Plaats het bericht in de huidige selectie door op het pictogram **Pin Console** te klikken.
* Schakel de weergave van berichten in of uit door op het pictogram **Stoppen** te klikken.
