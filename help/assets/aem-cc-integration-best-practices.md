---
title: Aanbevolen werkwijzen om te integreren met [!DNL Adobe Creative Cloud]
description: De beste praktijken integreren een plaatsing van de Experience Manager met Adobe Creative Cloud om werkschema's van de activaoverdracht te stroomlijnen en maximumefficiency te bereiken.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b1586cd9d6b3e9da115bff802d840a72d1207e4a
workflow-type: tm+mt
source-wordcount: '3296'
ht-degree: 18%

---


# Aanbevolen werkwijzen voor AEM- en Creative Cloud-integratie {#aem-and-creative-cloud-integration-best-practices}

Adobe Experience Manager (AEM) Assets is een DAM-oplossing (Digital Asset Management) die met Adobe Creative Cloud kan worden geïntegreerd om DAM-gebruikers te helpen met creatieve teams samen te werken en de samenwerking bij het maken van inhoud te stroomlijnen.

Adobe Creative Cloud biedt creatieve teams een ecosysteem van oplossingen en services om ze te helpen digitale middelen te maken. Het omvat desktop- en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en markten zoals Adobe Stock.

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>Delen van mappen AEM naar Creative Cloud is nu afgekeurd en wordt hieronder niet meer behandeld. Adobe raadt nieuwere mogelijkheden aan, zoals Adobe Asset Link of AEM desktop app, om creatieve gebruikers toegang te bieden tot de middelen die in AEM worden beheerd.

## De behoefte van de samenwerking van creatieven, verkopers, en gebruikers DAM {#collaboration-need-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktop vereenvoudigen | Toegang tot bedrijfsmiddelen van een DAM (AEM Assets) stroomlijnen voor creatieve professionals, of meer in het algemeen gebruikers op desktopcomputers die werken in toepassingen voor het maken van native bedrijfsmiddelen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in AEM te detecteren, te gebruiken (openen), te bewerken en op te slaan, en om nieuwe bestanden te uploaden. | Win- of Mac-bureaublad; Creative Cloud-apps |
| Middelen van Adobe Stock van hoge kwaliteit en gebruiksklaar maken | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | AEM Assets; Adobe Stock Marketplace metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | Merkportal, Commentaar voor delen van bedrijfsmiddelen |

## Adobe-aanbod ter ondersteuning van de samenwerkingsbehoefte {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe-aanbieding | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers ontdekken elementen van AEM, openen en gebruiken deze, bewerken en uploaden wijzigingen in AEM en uploaden nieuwe bestanden naar AEM zonder Creative Cloud-apps te verlaten. | [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator en InDesign |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in AEM en het uploaden van nieuwe bestanden naar AEM vanuit de desktopomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=en) | Desktop-app AEM op Windows- en Mac-bureaublad |
| Marketers en zakelijke gebruikers detecteren, voorvertonen, licentiëren en opslaan, en beheren de Adobe Stock-middelen vanuit AEM. Gelicentieerde en opgeslagen middelen bieden geselecteerde Adobe Stock-metagegevens voor beter beheer. | [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md) | AEM webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. Alternatieve oplossingen zoals [AEM Assets Brand Portal](https://helpx.adobe.com/nl/experience-manager/brand-portal/user-guide.html), oplossingen die kunnen worden gebouwd op basis van componenten van [Asset Share Commons](https://adobe-marketing-cloud.github.io/asset-share-commons/), [Link Share](share-assets.md), met behulp van de [AEM Assets-interface](/help/assets/manage-digital-assets.md) moeten worden gecontroleerd op basis van een specifieke vereiste.

![Creative Cloud-verbindingen voor AEM: Bepalen welke mogelijkheid moet worden gebruikt](assets/creative-connections-aem.png)

Bepalen welke mogelijkheden moeten worden gebruikt

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

| Hoofdletters gebruiken | Adobe-itemkoppeling | Bureaubladapp AEM | Opmerkingen of alternatieve methoden |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Detecteren - door AEM mappen bladeren | Ja | Webinterface AEM en bureaubladacties | Als u op het gedeelde netwerk bladert, schakelt u de miniaturen uit om te voorkomen dat binaire bestanden met elementen worden gedownload. |
| Detecteren - toegang AEM verzamelingen | Ja | Webinterface AEM en bureaubladacties |  |
| Detecteren - middelen zoeken van AEM | Ja | Webinterface AEM en bureaubladacties |  |
| Gebruiken - element openen | Ja | Ja, voor elke app | [Openen vanuit ](/help/assets/manage-digital-assets.md#previewing-assets) webinterface of vanuit Finder |
| Gebruiken - element van AEM in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | AEM bureaubladtoepassing biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [Bij uitchecken in ](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) AAL wordt het middel standaard opgeslagen op de Creative Cloud Storage-account van de gebruiker (gesynchroniseerd door de Creative Cloud-app). |
| Bewerken - Bezig met werk buiten AEM | Ja - Asset beschikbaar in de Creative Cloud-opslagaccount van de gebruiker gesynchroniseerd met desktop. | Ja |  |
| Bewerken - wijzigingen uploaden | Ja - [Inchecken van handeling](https://helpx.adobe.com/enterprise/using/manage-assets-using-adobe-asset-link.html) met optionele opmerking | Ja |  |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [Uploaden via webinterface](/help/assets/manage-digital-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [Uploaden via webinterface](/help/assets/manage-digital-assets.md#uploading-assets); Aangepaste scripts of gereedschappen |
| Diverse - gebruiker en aanmelding | Creative Cloud-gebruiker die zich heeft aangemeld bij Creative Cloud-bureaublad wordt herkend (SSO) | AEM gebruiker/aanmelding | Gebruikers van beide oplossingen tellen mee voor de AEM gebruikersquota. |
| Diverse - netwerk en toegang | Vereist toegang van de Desktop van de gebruiker aan AEM plaatsing over netwerk | Vereist toegang van de Desktop van de gebruiker aan AEM plaatsing over netwerk | Adobe Asset Link deelt de omgeving van de netwerkproxy niet. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Om het gebruik van middelen te steunen, zouden andere oplossingen moeten worden overwogen:

* [AEM Assets Brand ](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) Portalfor a configureerbare, SaaS-invoegtoepassing voor AEM Assets voor het publiceren van middelen.

* De oplossingen van de douane worden gecreeerd gebaseerd op [Commons van het Aandeel van activa](https://adobe-marketing-cloud.github.io/asset-share-commons/) codebasis.
* AEM [link share](/help/assets/share-assets.md) om elementen ad hoc te delen met behulp van koppelingen.
* [AEM Assets-](/help/assets/manage-digital-assets.md) webinterface met gebieden voor externe partijen die zijn beveiligd door AEM Access Control-instelling en met noodzakelijke aanpassingen in de IT-/netwerkconfiguratie, zodat deze externe gebruikers toegang hebben tot AEM.

## Belangrijke concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst met algemene termen {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **Creatieve assets:** Assets die klaar zijn om te worden gedeeld met een groter team, of die zijn geselecteerd/goedgekeurd door het creatieve team om te delen met marketing- of LOB-teams.

* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitieve asset:** Een asset die alle goedkeuringen/metadatatagging heeft doorlopen en klaar is om door het grotere team te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.

* **Kleine update/wijziging van assets:** Een snelle en kleine wijziging in een digitale asset. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke update/wijziging van assets:** Een verandering in een digitale asset die aanzienlijk werk vereist, en soms over een langere periode moet worden uitgevoerd. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is dit gelijk aan AEM Experience Manager-assets, tenzij anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie kan een DAM-gebruiker een marketing- of niet-marketinggebruiker zijn, bijvoorbeeld een LOB-gebruiker (Line-of-Business), bibliothecaris, verkoopmedewerker, enz. zijn.

### Overwegingen bij het gebruik van AEM- en Creative Cloud-integratie {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Dit is een korte samenvatting van beste praktijken voor AEM &amp; de Integratie van de Creative Cloud. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **Voor creatieve gebruikers die in Photoshop, InDesign of Illustrator werken:** Adobe Asset Link biedt de beste gebruikerservaring, zoals een schone verwerking van het werk in uitvoering op assets die zijn uitgecheckt bij AEM
* **Voor het vereenvoudigen van de toegang tot assets van de desktop voor een generieke bestandsindeling of applicatie:** Gebruik een AEM-desktopapp
* **Begrijpen waarom en wanneer assets in DAM moeten worden opgeslagen:** Updates die ter beschikking moeten worden gesteld aan een groter team in uw organisatie
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere applicaties geen taken in uitvoering uit in een toegewezen/gedeelde map, tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot Adobe Stock-middelen van AEM Assets {#access-to-adobe-stock-assets-from-aem-assets}

[AEM en Adobe Stock-](/help/assets/aem-assets-adobe-stock.md) integratie bieden AEM gebruikers de mogelijkheid om middelen van Adobe Stock naar AEM te zoeken, voor te vertonen, te licentiëren en op te slaan. Bij gelicentieerde en opgeslagen Adobe Stock-elementen zijn de metagegevens van de Stock geselecteerd. Deze kunnen worden gebruikt om met extra filters naar deze elementen te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer de activa van de voorraad van Adobe aan AEM worden bewaard, worden zij een regelmatige AEM Assets, met binair opgeslagen aan AEM bewaarplaats. Sommige metagegevens die betrekking hebben op Adobe Stock, worden voor het element in AEM opgeslagen, anders ziet het innameproces er hetzelfde uit als voor elk ander bestand. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het middel dat naar AEM wordt opgeslagen, is een kopie en geen koppeling naar Adobe Stock.

**Werken met elementen die van Adobe Stock zijn opgeslagen in AEM in Creative Cloud**. Deze integratie is onafhankelijk van Adobe Asset Link, maar Adobe Asset Link herkent deze elementen die op die manier uit Stock zijn opgeslagen en geeft aanvullende metagegevens en voorraadpictogrammen voor deze elementen weer in de UI voor de uitbreiding van de Adobe Asset Link in Photoshop, Illustrator of InDesign. De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale AEM zijn wanneer ze worden opgeslagen naar AEM.
Creatieve gebruikers die werken in Creative Cloud-apps met de extensie Adobe Asset Link kunnen niet alleen toegang krijgen tot middelen met een licentie van Adobe Stock naar AEM, maar kunnen ook het deelvenster Creative Cloud-bibliotheken gebruiken om Adobe Stock-middelen te zoeken, voor te vertonen en in licentie te geven.
Activa van Adobe Stock die in licentie zijn gegeven en in AEM zijn opgeslagen, worden beschikbaar voor de bredere teams die toegang hebben tot de implementatie van AEM Assets, terwijl creatieve licenties voor activa van Adobe Stock via het deelvenster Bibliotheken van Creative Cloud ze standaard alleen beschikbaar maken op hun Creative Cloud-account.

## Informatie over het opslaan van elementen in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, dat partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor om activa slechts op te slaan die voor de stroomafwaartse marketing/LOB processen relevant zijn (het publiceren aan kanalen zoals Webkanaal via AEM Sites of andere kanalen die door Adobe Experience Cloud - Marketing Cloud, Advertising Cloud, en gemeten door Analytics Cloud worden gediend, die aan gebruikers/partners, etc. verstrekken). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een hoge kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen worden opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creatieve teams (en organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Activa die nog moeten worden afgerond of die moeten worden getest
* Middelen die niet de cyclus van het creatieve/interne teamoverzicht doorstaan
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Activa die een bepaalde looptijd hebben bereikt en die klaar worden geacht om te worden gedeeld
* Elementen die vooraf zijn geselecteerd door het creatieve team
* Specifieke asset-indelingen die kunnen worden gebruikt of aangevraagd door marketing, afhankelijk van een specifiek contract of een specifieke overeenkomst (bijvoorbeeld JPG-bestanden die zijn geconverteerd van RAW-bestanden, TIFF-bestanden/afbeeldingen van PSD-originelen)

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

AEM Assets ondersteunt twee soorten gebruikers op basis van hun toegang tot de AEM Assets-implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

Doorgaans hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot het DAM-exemplaar, inclusief AEM aanmelding. AEM en netwerkinfrastructuur kunnen worden opgezet om directe toegang tot externe partijen toe te staan - gewoonlijk vertrouwde organisaties zoals agentschappen die voor een cliënt werken - om toegang tot AEM over netwerk, bijvoorbeeld, via de lijst van gewenste personen van VPN of IP te hebben.

In dergelijke gevallen biedt de app Adobe Asset Link of AEM desktop eenvoudige toegang tot definitieve/goedgekeurde middelen en kunt u creatieve middelen opslaan in DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot het DAM-exemplaar hebben mogelijk toegang tot goedgekeurde activa nodig of willen hun nieuwe ontwerpen toevoegen aan het DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Gebruik [AEM Assets Brand Portal](https://helpx.adobe.com/experience-manager/brand-portal/user-guide.html) voor het veilig distribueren van middelen aan externe partners
* Gebruik een aangepaste implementatie van een distributie- en sourcingportal op basis van [Commons voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Het Toegangsbeheer van het gebruik opstelling in AEM en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP toegestaan lijst) om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven. Zij kunnen AEM Web UI gebruiken om activa te krijgen en nieuwe inhoud te uploaden in uw DAM.

#### Werk bezig met middelen van AEM {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, is het raadzaam belangrijke updates van elementen uit te voeren, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen worden geüpload naar AEM. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

Adobe Asset Link biedt een goede ondersteuning voor dit gebruiksgeval:

* Wanneer gebruikers in Photoshop, InDesign of Illustrator van plan zijn een bestand te bewerken, voeren ze een uitcheckbewerking uit op het opgegeven element
* Het middel wordt op de achtergrond gedownload, in gebruikersCreative Cloud-account geplaatst die door Creative Cloud desktop app op schijf wordt gesynchroniseerd, en de markering voor uitchecken wordt in AEM op het middel geschakeld om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het element zich in de Creative Cloud-account bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale mobiele Creative Cloud-app) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere Creative Cloud-gebruikers.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar Creative Cloud-toepassing, met een optionele opmerking. De overeenkomstige activa in AEM zijn versioned en bijgewerkt aan met het nieuwe binaire getal. AEM gebruikers zoals Marketers of LOB-gebruikers hebben via de tijdlijngebruikersinterface van AEM middelen toegang tot belangrijke wijzigingen in de activa of mijlpalen.

AEM bureaubladtoepassing biedt een netwerkshare voor elementen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar AEM. Met zo een configuratie, zou het frequente sparen tijdens de werk-in-lopende fase allen in AEM en versioned worden geupload, die tot veel netwerkverkeer en potentiële scalability uitdagingen leiden - om onnodige versies in AEM te noemen.

Hier kunt u het beste een optie in AEM bureaubladtoepassing gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in elementen handmatig te uploaden naar AEM, waarbij de actie voor uploadwijzigingen wordt gebruikt in de statusinterface van de app voor middelen.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

Deze beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto) als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Als u grote/hiërarchische mappen bulksgewijs wilt uploaden, gebruikt u AEM bureaubladtoepassing die [functionaliteit voor het uploaden van mappen](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html#bulkupload) biedt. U kunt ook hiërarchische mapstructuren uploaden. Elementen worden op de achtergrond geüpload en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de AEM Assets-webinterface.
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf desktop {#managing-digital-assets-directly-from-desktop} beheren

Als u Delen van netwerkbestanden gebruikt om digitale elementen te beheren, kan het gebruik van de netwerkshare die is toegewezen door AEM bureaubladtoepassing, worden beschouwd als een handige vervanging. Wanneer de overgang van netwerkdossieraandelen, AEM Webinterface een rijke reeks mogelijkheden van het Beheer van Digitale Middelen verstrekt die veel verder gaan dan wat op een netwerkaandeel (onderzoek, inzamelingen, meta-gegevens, samenwerking, voorproeven, etc.) mogelijk is, en AEM Desktopapp verstrekt een handige verbinding om de server-kantDAM bewaarplaats met het werk op Desktop aan te sluiten.

Vermijd het gebruik van AEM bureaubladtoepassing voor het rechtstreeks beheren van middelen in het netwerkaandeel van AEM Assets. Vermijd bijvoorbeeld het gebruik van AEM bureaubladtoepassing voor het verplaatsen/kopiëren van meerdere bestanden. Gebruik in plaats daarvan de AEM Assets-webinterface om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de AEM Assets-functie voor het uploaden van mappen.

<!-- 
#### Asset migration {#asset-migration}

To plan and execute asset migrations from existing system to a new system or migration of large volume of assets stored on servers, see the [Migration Guide](/help/assets/assets-migration-guide.md). AEM desktop app and AEM to Creative Cloud integrations do not support such migrations. Due to the large volumes of assets to be ingested, and additional requirements around metadata mapping, transformation, and ingestion, migrations should be handled using different tools and approaches.
-->
