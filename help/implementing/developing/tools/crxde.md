---
title: CRXDE Lite gebruiken
description: CRXDE Lite maakt deel uit van de AEM quickstart en is beschikbaar voor u om toegang te krijgen tot en wijzigingen aan te brengen in de opslagruimte in uw lokale ontwikkelomgevingen in de browser.
exl-id: 1581a7e5-6f84-4a45-8e8f-c83692ea077a
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
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
1. Open de URL `https://<host>:<port>/crx/de` in uw browser.
1. Ga uw **gebruikersbenaming** en **wachtwoord** in.
1. Klik **OK**.

De gebruikersinterface van CRXDE Lite wordt als volgt weergegeven in uw browser:

![ de interface van CRXDE Lite ](assets/crxde-lite.png)

>[!TIP]
>
>U kunt CRXDE Lite ook openen via het menu AEM. Van het belangrijkste menu uitgezocht **Hulpmiddelen** > **Algemeen** > **CRXDE Lite**.

## Overzicht van de gebruikersinterface {#overview-of-the-user-interface}

CRXDE Lite-gebruikersinterface bevat veel onderdelen en functies.

### Bovenste schakelbalk {#top-switcher-bar}

De hoogste bar van de Schakelaar laat u snel tussen CRXDE Lite en [ de Manager van het Pakket ](package-manager.md) schakelen.

### Knooppuntwidget {#node-path-widget}

De widget Pad knooppunt geeft het pad naar het momenteel geselecteerde knooppunt weer.

U kunt het ook gebruiken om naar een knoop te springen door de weg in te gaan door het hand in te gaan of het van elders te kleven en binnengaan te drukken.

Het biedt ook ondersteuning voor het zoeken naar knooppunten met een specifieke knooppuntnaam. Voer de naam in van het knooppunt dat u wilt zoeken en wacht (of selecteer het zoekpictogram aan de rechterkant). Als een bepaald knooppunt of bepaalde knooppunten in het verkennervenster wordt geladen, wordt de lijst weergegeven en kunt u het pad selecteren en op Enter drukken om naar het knooppunt te navigeren. Het werkt alleen voor de knooppunten die momenteel in de CRXDE-clienttoepassing in de browser zijn geladen. Als u de volledige bewaarplaats wilt zoeken, gebruik **Hulpmiddelen** -&amp;gt: **Vraag**.

### Explorer-venster {#explorer-pane}

Het **Pane van de Ontdekkingsreiziger** toont een boom van alle knopen in de bewaarplaats.

Klik een knoop om zijn eigenschappen op het **Eigenschappen** lusje te tonen. Nadat u op een knooppunt hebt geklikt, kunt u een handeling op de werkbalk selecteren. Klik nogmaals op het knooppunt om de naam ervan te wijzigen.

Met het structuurnavigatiefilter (het binoculars-pictogram) kunt u de knooppunten in de opslagplaats filteren waarvoor de naam de invoertekst bevat. Het is alleen van toepassing op knooppunten die lokaal zijn geladen.

### Venster bewerken {#edit-pane}

**geeft Pane** uit laat u de inhoud van het momenteel-geselecteerde dossier in de bewaarplaats bekijken. Elk geopend bestand wordt in het deelvenster weergegeven als een eigen tabblad.

Het **lusje van het Huis** &lbrace;laat u inhoud en/of documentatie en toegangsontwikkelaardocumentatie en Adobe steun zoeken.

Dubbelklik een dossier in de **Ruit van de Ontdekkingsreiziger** om zijn inhoud in **te tonen geef Pane** uit. U kunt het dan wijzigen en de veranderingen bewaren.

Zodra een dossier in **wordt uitgegeven geef Pane** uit, zijn de volgende hulpmiddelen beschikbaar op de toolbar:

* **toon in boom** - toont het dossier in de opbergingstructuur.
* **Onderzoek/vervang** - voert een onderzoek uit of vervangt.

Dubbelklik de statuslijn van **uitgeeft Pane** opent **ga naar lijn** dialoog zodat kunt u een specifiek lijnaantal ingaan.

### Tabblad Eigenschappen {#properties-tab}

Het **Lusje van Eigenschappen** toont de eigenschappen van de knoop die u hebt geselecteerd. U kunt nieuwe eigenschappen toevoegen of bestaande eigenschappen verwijderen.

### Tabblad Toegangsbeheer {#access-control-tab}

Het **Lusje van het Toegangsbeheer** toont toestemmingen die op de huidige weg, de bewaarplaats, of het hoofd worden gebaseerd.

De machtigingen zijn onderverdeeld in de volgende categorieën.

* **Toepasselijk Beleid van het Toegangsbeheer** - het beleid dat op de huidige selectie kan worden toegepast
* **Lokaal Beleid van het Toegangsbeheer** - het huidige beleid dat plaatselijk op de huidige selectie wordt toegepast
* **Effectief Beleid van het Toegangsbeheer** - het huidige beleid dat voor de huidige selectie wordt toegepast, die plaatselijk zou kunnen worden geplaatst of van ouderknopen worden geërft

>[!NOTE]
>
>Om toegangsbeheerinformatie te kunnen zien, moet de gebruiker het programma opent aan CRXDE Lite rechten hebben om ACL ingangen te lezen.

### Tabblad Replicatie {#replication-tab}

Het **Lusje van de Replicatie** toont de replicatiestatus van huidige knoop. U kunt het huidige knooppunt repliceren en herhalen.

### Tabblad Console {#console-tab}

Het **Lusje van de Console** toont logboekberichten. U kunt het logboekniveau vormen, de console ontruimen, bij de geselecteerde rolpositie vastzetten en het tonen van berichten toelaten/onbruikbaar maken.

### Tabblad Informatie maken {#build-info-tab}

Het **lusje van Info van de Bouwstijl** toont informatie wanneer een bundel wordt gebouwd.

### Knop Vernieuwen {#refresh-button}

De **verfrist Knoop** verfrist de huidige selectie. Wijzigingen van andere gebruikers worden bijgewerkt in uw weergave van de opslagplaats. Wijzigingen die u hebt aangebracht, blijven ongewijzigd.

### Alle knoppen opslaan {#save-all-button}

**sparen Al Knoop** bewaart alle veranderingen u hebt aangebracht. Tot u verkiest om te bewaren, zijn de veranderingen tijdelijk, en verloren wanneer u de console weggaat.

* **terugkeren** - verwerpt alle veranderingen die u op de geselecteerde knoop sinds laatste sparen actie hebt aangebracht, dan herlaadt de huidige staat van de bewaarplaats voor de geselecteerde knoop
* **terugkeert allen** - verwerpt alle veranderingen die u door de volledige bewaarplaats sinds laatste sparen actie hebt aangebracht, dan herlaadt de huidige staat van de bewaarplaats

### Knop Maken {#create-button}

**creeer Knoop** is een drop-down menu om het volgende onder de geselecteerde knoop tot stand te brengen:

* Node - een knoop met een willekeurig knooptype
* File - an `nt:file` node and its nt:resource subnode
* Map - een knooppunt `nt:folder`

### Knop Verwijderen {#delete-button}

De **Knoop van de Schrapping** schrapt de geselecteerde knoop.

### Knop kopiëren {#copy-button}

De **Knoop van het Exemplaar** kopieert de geselecteerde knoop.

## Knop Plakken {#paste-button}

De **Knoop van het Deeg** kleeft de gekopieerde knoop onder de geselecteerde knoop.

### Knop Verplaatsen {#move-button}

De **Knoop van de Beweging** beweegt de geselecteerde knoop aan de knoop die door de dialoog wordt geplaatst.

### Naam wijzigen {#rename-button}

**noem Knoop anders** anders noemt de geselecteerde knoop.

### Mixins {#mixins-button}

De **Knoop van Mixins** laat u mixintypes aan het knooptype toevoegen. De mixintypen worden meestal gebruikt om geavanceerde functies toe te voegen.

### Gereedschappen {#tools-button}

De **Knoop van Hulpmiddelen** is een drop-down menu met de volgende beschikbare hulpmiddelen:

* **Config van de Server** - om tot de Console van de Felix (ook beschikbaar bij `https://<host>:<port>/system/console/configMgr`) toegang te hebben
* **Vraag** - om de bewaarplaats te vragen
* **Bevoegdheden** - om voorrechten te bekijken en toe te voegen
* **Controle van de Toegang van de Test** - om de toestemming voor bepaalde weg en/of hoofd te testen
* **Type van Knoop van de Uitvoer** - om knooptypes in het systeem als aantekening uit te voeren CND
* **het Type van Knoop van de Invoer** - om knooptypes in te voeren gebruikend aantekening CND.

### Aanmeldingswidget {#login-widget}

De **Login Widget** toont momenteel het programma geopende gebruiker.

Klik op deze knop om u aan te melden of opnieuw aan te melden als een andere gebruiker. `@crx.default` geeft aan dat u zich in de standaardwerkruimte (en alleen in de standaardwerkruimte) in de opslagplaats bevindt.

De **optie van de Voorkeur** kan worden gebruikt om uw taal te plaatsen UI en de hete sleutels voor diverse acties zoals sparen, onderzoek te bekijken, nota, etc. tot stand te brengen.

## Een map maken {#creating-a-folder}

Een map met CRXDE Lite maken:

1. Open CRXDE Lite in uw browser.
1. In de ruit van de Navigatie, klik de omslag met de rechtermuisknop aan waaronder u de nieuwe omslag wilt tot stand brengen, creeert de uitgezochte **...**, dan **leidt tot Omslag...**.

1. Ga de omslag **Naam** in en klik **O.K.**.

1. Klik **sparen allen** om de veranderingen op de server te bewaren.

## Een knooppunt maken {#creating-a-node}

Een knooppunt maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In het [**Pane Exploderer**](#explorer-pane), klik de knoop met de rechtermuisknop aan waar u de nieuwe knoop wilt tot stand brengen, **creeer**, dan **creeer Knoop**.
1. Ga de **Naam** in en selecteer het **Type**.
1. Klik **OK**.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen op de server te bewaren.

U kunt het knooppunt nu aan uw behoeften aanpassen door eigenschappen te wijzigen of nieuwe knooppunten te maken.

>[!NOTE]
>
>De meeste uitgeven verrichtingen, met inbegrip van **leiden Knoop**, houdt alle veranderingen in geheugen, en slaat hen slechts op in de bewaarplaats op (het gebruiken van [**sparen Alle Knoop**](#save-all-button)). Sommige bewerkingen, zoals verplaatsen, worden echter automatisch voortgezet.
>
>De validatie met betrekking tot of het gemaakte knooppunt wordt toegestaan door het knooppunttype van het bovenliggende knooppunt, wordt ook uitgevoerd door de gegevensopslagruimte wanneer wijzigingen worden opgeslagen. Als u een foutbericht ontvangt tijdens het opslaan van een knooppunt, controleert u of de inhoudsstructuur geldig is (u kunt bijvoorbeeld geen `nt:unstructured` -knooppunt maken als onderliggend knooppunt van `nt:folder` -knooppunt).

## Een eigenschap maken {#creating-a-property}

Een eigenschap maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In het [**Deelvenster Exploderer**](#explorer-pane), selecteer de knoop waar u het nieuwe bezit wilt toevoegen.
1. In het [**Lusje van Eigenschappen**](#properties-tab) in de bodemruit, ga de **Naam** in, het **Type**, en de **Waarde**.
1. Klik **toevoegen**.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen op de server te bewaren.

## Een bestand maken {#creating-a-file}

Een bestand maken met CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. In het [**Pane Exploderer**](#explorer-pane), klik de component met de rechtermuisknop aan waar u het dossier wilt tot stand brengen, **creeer**, dan **creeer Dossier**.
1. Ga het dossier **Naam** met inbegrip van zijn uitbreiding in.
1. Klik **OK**.
1. Het nieuwe dossier opent als lusje in [**uitgeeft Pane**](#edit-pane).
1. Bewerk het bestand.
1. Klik [**sparen Al Knoop**](#save-all-button) om de veranderingen te bewaren.

## Nodetypen exporteren en importeren {#exporting-and-importing-node-types}

Met CRXDE Lite kunt u knooptype definities in [ Compacte Namespace en van het Type van Knoop (CND) notatie invoeren en/of uitvoeren ](https://jackrabbit.apache.org/jcr/node-type-notation.html).

Een definitie van een knooptype exporteren in CRXDE Lite:

1. Open CRXDE Lite in uw browser.
1. Selecteer het vereiste knooppunt.
1. Selecteer **Hulpmiddelen** toen **het Type van Knoop van de Uitvoer**.
1. De definitie wordt weergegeven in CND-notatie op een nieuw tabblad in uw browser.
1. Sla indien nodig de gegevens op.

Een definitie van het knooppunttype importeren:

1. Open CRXDE Lite in uw browser.
1. Selecteer **Hulpmiddelen** toen **het Type van Knoop van de Invoer**.
1. Een nieuw lusje opent in [**uitgeeft Pane**](#edit-pane) geëtiketteerd **het Type van Knoop van de Invoer**.
1. Ga de aantekening CND voor de definitie in het tekstvakje van het **Type van Knoop van de Invoer** tabel in.
1. Controle **staat Update** toe als u een bestaande definitie bijwerkt.
1. Klik **Invoer**.

## Logboekregistratie {#logging}

Met CRXDE Lite kunt u het bestand `error.log` weergeven dat zich in het bestandssysteem op `<aem-install-dir>/crx-quickstart/logs` bevindt en dit filteren met het juiste logniveau. Ga als volgt te werk:

1. Open CRXDE Lite in uw browser.
1. In het drop-down menu op het recht van het [**Lusje van de Console**](#console-tab) bij de bodem van het venster, uitgezochte **Logboeken van de Server**.
1. Klik het **pictogram van het Einde** om de berichten te tonen.

U kunt:

* Pas de logboekparameters in de Console van de Felix aan door het **Logging van Configuraties** pictogram te klikken.
* Wis de berichten door het **Duidelijke pictogram van de Console** te klikken.
* Zet het bericht bij de huidige selectie vast door het **pictogram van de Console van het Punt** te klikken.
* Laat of maak het tonen van berichten onbruikbaar door het **pictogram van het Einde** te klikken.
