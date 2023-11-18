---
title: Aanbevolen procedures voor integratie met [!DNL Adobe Creative Cloud]
description: De beste praktijken integreren een plaatsing van de Experience Manager met Adobe Creative Cloud om werkschema's van de activaoverdracht te stroomlijnen en maximumefficiency te bereiken.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration,Adobe Asset Link,Desktop App
role: Architect,User,Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '3489'
ht-degree: 13%

---

# Aanbevolen werkwijzen voor Adobe Experience Manager- en Creative Cloud-integratie {#aem-and-creative-cloud-integration-best-practices}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Adobe Experience Manager Assets is een DAM-oplossing (Digital Asset Management) die met Adobe Creative Cloud kan worden geïntegreerd om DAM-gebruikers te helpen samen te werken met creatieve teams en de samenwerking bij het maken van inhoud te stroomlijnen.

Adobe Creative Cloud biedt creatieve teams een ecosysteem van oplossingen en services om ze te helpen digitale middelen te maken. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en marketinglocaties zoals Adobe Stock.

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>Het delen van mappen naar Creatives Cloud is nu afgekeurd en wordt hieronder niet meer besproken. Adobe raadt nieuwere mogelijkheden aan, zoals Adobe Asset Link of Experience Manager desktop app, om creatieve gebruikers toegang te bieden tot de middelen die in Experience Manager worden beheerd.

## De behoefte van de samenwerking van creatieven, verkopers, en gebruikers DAM {#collaboration-need-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktopcomputers vereenvoudigen | Toegang tot middelen van een DAM stroomlijnen ([!DNL Assets]) voor creatieve professionals, of meer in het algemeen, gebruikers op desktopcomputers die werken in toepassingen voor het maken van native elementen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in de Experience Manager te detecteren, te gebruiken (openen), te bewerken en op te slaan en nieuwe bestanden te uploaden. | Windows- of Mac-bureaublad; Creative Cloud-apps |
| Voorzie van hoogwaardige, gebruiksklare middelen van [!DNL Adobe Stock] | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creatieve professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve gereedschappen. | [!DNL Assets]; [!DNL Adobe Stock] Marketplace; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| Vooraf gedefinieerde variaties van geüploade elementen automatisch genereren | Verwerk automatisch elementen met behulp van de unieke media handling en transformatietechnologie van de Adobe voor vooraf gedefinieerde handelingen. Creeer douanelogica om uw eigen acties te bepalen gebruikend APIs en activa microservices. | [!DNL Assets] gebruikersinterface |

## Adobe biedt ondersteuning voor de behoefte aan samenwerking {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe aanbieden | Betrokken oppervlakken |
|---|---|---|
| Creatieve gebruikers ontdekken elementen van [!DNL Experience Manager], openen en gebruiken, wijzigingen bewerken en uploaden naar [!DNL Experience Manager]en uploadt u nieuwe bestanden naar [!DNL Experience Manager], zonder hun [!DNL Creative Cloud] app. | [Adobe-itemkoppeling](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator en InDesign. |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in [!DNL Experience Manager]en nieuwe bestanden uploaden naar [!DNL Experience Manager] in de desktopomgeving. Ze gebruiken een algemene integratie om elk elementtype in de native bureaubladtoepassing te openen, inclusief niet-Adobe toepassingen. | [[!DNL Experience Manager] bureaubladtoepassing](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Desktop-app Experience Manager op Win- en Mac-bureaublad |
| Marketers en zakelijke gebruikers detecteren, voorvertonen, licentiëren en opslaan, en beheren de Adobe Stock-middelen vanuit de Experience Manager. Gelicentieerde en opgeslagen middelen bieden geselecteerde Adobe Stock-metagegevens voor beter beheer. | [Integratie van Experience Manager en Adobe Stock](aem-assets-adobe-stock.md) | [!DNL Experience Manager] webinterface |
| De samenwerking tussen ontwerpers van digitale producten en marketers verbeteren. Laat ontwerpers de digitale elementen gebruiken in ontwerp- en draadframemodellen op het Adobe XD-canvas. | [[!DNL Adobe Asset Link] for [!DNL Adobe XD]](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| Marktdeelnemers kunnen automatisch variaties en derivaten maken op basis van geüploade elementen en vooraf gedefinieerde handelingen die met behulp van aanpassingen zijn gemaakt. Gebruik deze automatisering om de snelheid van de inhoud te verbeteren en handmatige inspanningen te verminderen. | [Inhoud automatiseren](/help/assets/cc-api-integration.md) | [!DNL Experience Manager Assets] webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. Alternatieve oplossingen, zoals [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), oplossingen die op [Commentaar voor het delen van bedrijfsmiddelen](https://opensource.adobe.com/asset-share-commons/) componenten, [Delen van koppeling](share-assets.md), gebruiken [Experience Manager Assets-webinterface](/help/assets/manage-digital-assets.md) moeten worden herzien op basis van specifieke eisen.

![Verbindingen van het Creative Cloud voor Experience Manager: Besluiten welke capaciteit om te gebruiken](assets/creative-connections-aem.png)

Bepalen welke mogelijkheden moeten worden gebruikt

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

| Hoofdletters gebruiken | Adobe-itemkoppeling | Experience Manager-bureaubladtoepassing | Opmerkingen of alternatieve methoden |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Detecteren - naar mappen bladeren | Ja | Experience Manager, webinterface en bureaubladacties | Als u op het gedeelde netwerk bladert, schakelt u de miniaturen uit om te voorkomen dat binaire bestanden met elementen worden gedownload. |
| Detecteren - toegangsverzamelingen | Ja | Experience Manager, webinterface en bureaubladacties |  |
| Detecteren - zoeken naar middelen | Ja | Experience Manager, webinterface en bureaubladacties |  |
| Gebruiken - element openen | Ja | Ja, voor elke app | [Openen vanuit webinterface](/help/assets/manage-digital-assets.md#previewing-assets) of van Finder |
| Gebruiken - element van Experience Manager in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | De desktop-app van de Experience Manager biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [Uitchecken in AAL](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) Hiermee slaat u het element standaard op in de Creative Cloud Storage-account van de gebruiker (gesynchroniseerd door Creative Cloud-app). |
| Bewerken - Bezig met werk buiten Experience Manager | Ja - Asset beschikbaar in de opslagaccount van het Creative Cloud van de gebruiker gesynchroniseerd met desktop. | Ja |  |
| Bewerken - wijzigingen uploaden | Ja - [Inchecken, actie](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) met optionele opmerking | Ja |  |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [Uploaden via webinterface](/help/assets/manage-digital-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [Uploaden via webinterface](/help/assets/manage-digital-assets.md#uploading-assets); Aangepaste scripts of gereedschappen |
| Diverse - gebruiker en aanmelding | Gebruikers van Creatives Cloud die zich hebben aangemeld bij de desktop-app van het Creative Cloud, worden herkend (SSO) | Experience Manager gebruiker/aanmelding | Gebruikers van beide oplossingen tellen mee voor de gebruikersquota van de Experience Manager. |
| Diverse - netwerk en toegang | Vereist toegang van de Desktop van de gebruiker aan de plaatsing van de Experience Manager over netwerk | Vereist toegang van de Desktop van de gebruiker aan de plaatsing van de Experience Manager over netwerk | De Verbinding van de Activa van de Adobe deelt geen milieu van de netwerkvolmacht. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Houd rekening met de volgende opties ter ondersteuning van het gebruik van gevallen voor distributie van bedrijfsmiddelen:

* [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor een configureerbare invoegtoepassing van Elementen om elementen te publiceren.

* Aangepaste oplossingen worden gemaakt op basis van [Commentaar voor het delen van bedrijfsmiddelen](https://opensource.adobe.com/asset-share-commons/) code base.
* Experience Manager [delen van koppeling](/help/assets/share-assets.md) om activa op bestelling te delen gebruikend verbindingen.
* [Elementen van de webinterface](/help/assets/manage-digital-assets.md) met gebieden voor externe partijen die door de opstelling van het Toegangsbeheer van de Experience Manager en met noodzakelijke aanpassingen van de IT/netwerkconfiguratie worden beveiligd, die deze externe gebruikers toegang tot Experience Manager geven.

## Belangrijkste concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **Creatieve assets:** Assets die klaar zijn om te worden gedeeld met een groter team, of die zijn geselecteerd/goedgekeurd door het creatieve team om te delen met marketing- of LOB-teams.

* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitieve asset:** Een asset die alle goedkeuringen/metadatatagging heeft doorlopen en klaar is om door het grotere team te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.

* **Kleine update/wijziging van assets:** Een snelle en kleine wijziging in een digitale asset. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke update/wijziging van assets:** Een verandering in een digitale asset die aanzienlijk werk vereist, en soms over een langere periode moet worden uitgevoerd. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is dit gelijk aan Experience Manager-assets, tenzij anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie kan een DAM-gebruiker een marketing- of niet-marketinggebruiker zijn, bijvoorbeeld een LOB-gebruiker (Line-of-Business), bibliothecaris, verkoopmedewerker, enz. zijn.

### Overwegingen bij het gebruik van Experience Manager- en Creative Cloud-integratie {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Dit is een korte samenvatting van beste praktijken voor Experience Manager en de Integratie van Creatives Cloud. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **Voor creatieve gebruikers die in Photoshop, InDesign, of Illustrator werken:** Adobe Asset Link biedt de beste gebruikerservaring, waaronder een schone verwerking van de onderhanden werk op middelen die van de Experience Manager zijn uitgecheckt
* **Voor het vereenvoudigen van de toegang tot middelen van de Desktop voor om het even welke generische dossierformaat of toepassing:** Experience Manager desktop app gebruiken
* **Begrijpen waarom en wanneer assets in DAM moeten worden opgeslagen:** Updates die ter beschikking moeten worden gesteld aan een groter team in uw organisatie
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere toepassingen geen actieve taken uit in toegewezen/gedeelde map tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot Adobe Stock-middelen van Experience Manager Assets {#access-to-adobe-stock-assets-from-aem-assets}

[Integratie van Experience Manager en Adobe Stock](/help/assets/aem-assets-adobe-stock.md) biedt gebruikers van Experience Managers de mogelijkheid om middelen van Adobe Stock naar Experience Manager te zoeken, voor te vertonen, in licentie te geven en op te slaan. Bij gelicentieerde en opgeslagen Adobe Stock-elementen zijn de metagegevens van de Stock geselecteerd. Deze kunnen worden gebruikt om met extra filters naar deze elementen te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer de activa van de voorraad van de Adobe aan Experience Manager worden bewaard, worden zij een regelmatige Experience Manager Assets, met binair opgeslagen aan de bewaarplaats van de Experience Manager. Sommige metagegevens die betrekking hebben op Adobe Stock, worden in de Experience Manager van het element opgeslagen. Als dit niet het geval is, ziet het innameproces er hetzelfde uit als bij andere bestanden. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het middel dat aan Experience Manager wordt opgeslagen is een exemplaar, niet een verbinding terug in Adobe Stock.

**Werken met middelen die van Adobe Stock zijn opgeslagen in Experience Manager in Creative Cloud**. Deze Adobe staat los van Asset Link, maar de Adobe Asset Link herkent deze elementen die op die manier uit Stock zijn opgeslagen en geeft aanvullende metagegevens en het voorraadpictogram voor deze elementen weer in de UI voor de uitbreiding van Asset Link in Photoshop, Illustrator of InDesign van de Adobe. De bestanden zijn beschikbaar voor bladeren, openen, enzovoort, omdat het normale Experience Managers zijn wanneer deze worden opgeslagen in de Experience Manager.
Creatieve gebruikers die werken in Creative Cloud-apps met de extensie Adobe Asset Link kunnen niet alleen toegang krijgen tot middelen met een licentie van Adobe Stock naar Experience Manager, maar kunnen ook het deelvenster Bibliotheken van Creatives Cloud gebruiken om Adobe Stock-elementen te zoeken, voor te vertonen en in licentie te geven.
Activa van Adobe Stock die in Experience Manager zijn gelicentieerd en zijn opgeslagen, komen beschikbaar voor de bredere teams die toegang hebben tot de implementatie van Experience Manager Assets, terwijl creatieve licenties voor middelen van Adobe Stock via het deelvenster Bibliotheken van Creatives Cloud deze middelen standaard alleen op hun Creative Cloud-account beschikbaar maken.

## Elementen opslaan in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, die partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor om activa slechts op te slaan die voor de stroomafwaartse marketing/LOB processen relevant zijn (het publiceren aan kanalen zoals Webkanaal via Experience Manager Sites of andere kanalen die door Adobe Experience Cloud - Marketing Cloud, Advertising Cloud, en gemeten door Analytics Cloud worden gediend, die aan gebruikers/partners, etc. verstrekken). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een grote kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen zijn opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creatieve teams (en organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Activa die nog moeten worden afgerond of die moeten worden getest
* Middelen die niet de cyclus van het creatieve/interne teamoverzicht doorstaan
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Activa die een bepaalde looptijd hebben bereikt en die klaar worden geacht om te worden gedeeld
* Elementen die vooraf zijn geselecteerd door het creatieve team
* Specifieke activaformaten die door marketing, afhankelijk van een specifiek contract of een overeenkomst (bijvoorbeeld JPG dossiers die van RAW dossiers, TIFF/beelden van PSD originelen worden omgezet worden gebruikt of worden gevraagd)

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

Experience Manager Assets ondersteunt twee soorten gebruikers op basis van hun toegang tot de Experience Manager Assets-implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creatieve gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

Doorgaans hebben interne creatieve teams of bureaus/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot het DAM-exemplaar, inclusief aanmelding bij de Experience Manager. Experience Manager- en netwerkinfrastructuren kunnen worden ingesteld om directe toegang tot externe partijen mogelijk te maken - doorgaans vertrouwde organisaties zoals clientbureaus - om toegang tot Experience Manager via een netwerk te hebben, bijvoorbeeld via VPN of IP-lijst van gewenste personen.

In dergelijke gevallen biedt de desktop-app Adobe Asset Link of Experience Manager eenvoudige toegang tot definitieve/goedgekeurde middelen en kunt u creatieve middelen opslaan naar DAM.

#### Creatieve gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot het DAM-exemplaar hebben mogelijk toegang tot goedgekeurde activa nodig of willen hun nieuwe ontwerpen toevoegen aan het DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Gebruiken [Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor het veilig verdelen van activa aan externe partners
* Gebruik een aangepaste implementatie van een distributie- en sourcingportal op basis van [Commentaar voor het delen van bedrijfsmiddelen](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Het Toegangsbeheer van het gebruik opstelling in Experience Manager en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP toegestaan lijst) om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven. Ze kunnen de Experience Manager-webinterface gebruiken om elementen op te halen en nieuwe inhoud te uploaden naar uw DAM.

#### Werk in uitvoering met middelen van Experience Manager {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt aangeraden belangrijke updates van elementen uit te voeren, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen naar de Experience Manager worden geüpload. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

De Verbinding van de Activa van de Adobe biedt een goede steun voor dit gebruiksgeval:

* Wanneer gebruikers in Photoshop, InDesign of Illustrator van plan zijn een bestand te bewerken, voeren ze een uitcheckbewerking uit op het opgegeven element
* Het element wordt op de achtergrond gedownload, in de gebruikersaccount van het Creative Cloud gesynchroniseerd op schijf per bureaublad-app en de uitcheckmarkering wordt in de Experience Manager op het middel geschakeld om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Omdat het element zich in de account Creative Cloud bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale mobiele app voor Creatives Cloud) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere gebruikers van het Creative Cloud.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar toepassing op het Creative Cloud, met een optionele opmerking. De overeenkomstige activa in Experience Manager zijn versioned en bijgewerkt aan met het nieuwe binaire getal. Gebruikers van Experience Managers, zoals Marketers of LOB-gebruikers, hebben via de tijdlijngebruikersinterface van Experience Managers toegang tot belangrijke wijzigingen in bedrijfsmiddelen of mijlpalen.

De desktop-app van de Experience Manager biedt een gedeelde netwerkbestanden voor bestanden die in de native app worden geopend. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar de Experience Manager. Met zulk een configuratie, zou het frequente sparen tijdens de werk-in-lopende fase allen in Experience Manager en versioned worden geupload, die tot een grote hoeveelheid netwerkverkeer en potentiële scalability uitdagingen - om onnodige versies in Experience Manager te noemen.

Hier kunt u het beste een optie in de bureaubladtoepassing van de Experience Manager gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in  handmatig te uploaden naar Experience Manager met behulp van de actie voor uploadwijzigingen in de statusinterface van de app voor middelen.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

Deze beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto) als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Als u grote/hiërarchische mappen bulksgewijs wilt uploaden, gebruikt u de bureaubladtoepassing van de Experience Manager die [map uploaden](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#bulk-upload-assets) functionaliteit. U kunt ook hiërarchische mapstructuren uploaden. Elementen worden op de achtergrond geüpload en zijn daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de Experience Manager Assets-webinterface.
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf het bureaublad beheren {#managing-digital-assets-directly-from-desktop}

Als u Delen van netwerkbestanden gebruikt om digitale elementen te beheren, kan het gebruik van de netwerkshare die is toegewezen door de desktop-app van de Experience Manager, worden beschouwd als een handige vervanging. Bij de overgang van netwerkbestanden biedt de webinterface van de Experience Manager een uitgebreide reeks mogelijkheden voor beheer van digitale bedrijfsmiddelen die veel verder gaan dan wat mogelijk is bij het delen van een netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen enzovoort) en de desktop-app van de Experience Manager biedt een handige koppeling om de DAM-opslagplaats aan de serverzijde te verbinden met het werk op een desktopcomputer.

Vermijd het gebruik van de bureaubladtoepassing van de Experience Manager voor het rechtstreeks beheren van middelen in het netwerkaandeel van Experience Manager Assets. Vermijd bijvoorbeeld het gebruik van de bureaubladtoepassing van de Experience Manager om meerdere bestanden te verplaatsen/kopiëren. Gebruik in plaats daarvan de Experience Manager Assets-webinterface om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de Experience Manager Assets-functie voor het uploaden van mappen.

**Zie ook**

* [Elementen vertalen](translate-assets.md)
* [HTTP-API voor assets](mac-api-assets.md)
* [Ondersteunde bestandsindelingen](file-format-support.md)
* [Assets doorzoeken](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Rapporten over assets](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Facetten doorzoeken](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
