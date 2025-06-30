---
title: Beste werkwijzen om met  [!DNL Adobe Creative Cloud] te integreren
description: De beste praktijken integreren een plaatsing van Experience Manager met Adobe Creative Cloud om de werkschema's van de activaoverdracht te stroomlijnen en maximumefficiency te bereiken.
contentOwner: AG
mini-toc-levels: 1
feature: Collaboration, Adobe Asset Link, Desktop App
role: User, Architect, Admin
exl-id: cbed0d62-5148-45eb-b6a0-9fd164060fdc
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '3438'
ht-degree: 12%

---

# Aanbevolen werkwijzen voor integratie met Adobe Experience Manager en Creative Cloud {#aem-and-creative-cloud-integration-best-practices}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html?lang=en) |
| AEM as a Cloud Service | Dit artikel |

Adobe Experience Manager Assets is een DAM-oplossing (Digital Asset Management) die met Adobe Creative Cloud kan worden geïntegreerd om DAM-gebruikers te helpen samen te werken met creatieve teams en de samenwerking bij het maken van inhoud te stroomlijnen.

Adobe Creative Cloud biedt creatieve teams een ecosysteem van oplossingen en services om ze te helpen digitale middelen te maken. Hieronder vallen desktoptoepassingen en mobiele toepassingen, cloudservices zoals opslag met desktopsynchronisatie of webervaring, en marketinglocaties zoals Adobe Stock.

Lees verder om te weten welke integraties u kunt kiezen tussen desktop en DAM op bedrijfsniveau op basis van uw gebruiksscenario en wat de bijbehorende beste werkwijzen zijn voor de verbindingsworkflows.

>[!NOTE]
>
>Delen van mappen tussen Experience Manager en Creative Cloud is nu afgekeurd en wordt hieronder niet meer besproken. Adobe adviseert nieuwere mogelijkheden zoals Adobe Asset Link of Experience Manager desktop app om creatieve gebruikers toegang te geven tot de middelen die in Experience Manager worden beheerd.

## Collaboration heeft behoefte aan creatieven, marketers en DAM-gebruikers {#collaboration-need-of-creatives-marketers-and-dam-users}

| Vereisten | Hoofdletters gebruiken | Betrokken oppervlakken |
|---|---|---|
| Ervaring voor creatieve producten op desktopcomputers vereenvoudigen | Toegang tot middelen van een DAM ([!DNL Assets]) stroomlijnen voor creatieve professionals, of meer in het algemeen gebruikers op desktopcomputers die werken in toepassingen voor het maken van native elementen. Ze hebben een eenvoudige en eenvoudige manier nodig om wijzigingen in Experience Manager te detecteren, te gebruiken (openen), te bewerken en op te slaan en nieuwe bestanden te uploaden. | Win- of Mac-bureaublad; Creative Cloud-apps |
| Middelen van hoge kwaliteit en gebruiksklaar bieden vanuit [!DNL Adobe Stock] | Marketers helpen het proces voor het maken van inhoud te versnellen door hulp te bieden bij het aanschaffen en detecteren van bedrijfsmiddelen. Creative-professionals gebruiken de goedgekeurde middelen direct vanuit hun creatieve tools. | [!DNL Assets]; [!DNL Adobe Stock] Marketplace; metagegevensvelden |
| Elementen distribueren en delen door organisaties | De interne afdelingen/de lokale takken en de externe partners, de distributeurs, en de agentschappen gebruiken de goedgekeurde activa die door de ouderorganisatie worden gedeeld. De organisatie wil de gemaakte middelen veilig en naadloos delen voor breder hergebruik. | [!DNL Brand Portal], [!DNL Asset Share Commons] |
| Vooraf gedefinieerde variaties van geüploade elementen automatisch genereren | Verwerk automatisch elementen met behulp van Adobe-technologie voor het verwerken en transformeren van unieke media voor vooraf gedefinieerde handelingen. Creeer douanelogica om uw eigen acties te bepalen gebruikend APIs en activa microservices. | [!DNL Assets] gebruikersinterface |

## Adobe biedt ondersteuning voor de behoefte aan samenwerking {#adobe-offerings-to-support-the-collaboration-need}

| Waardevoorstel voor de betreffende personen | Adobe-aanbieding | Betrokken oppervlakken |
|---|---|---|
| Creative-gebruikers detecteren elementen vanuit [!DNL Experience Manager] , openen en gebruiken deze, bewerken en uploaden wijzigingen in [!DNL Experience Manager] en uploaden nieuwe bestanden naar [!DNL Experience Manager] zonder hun [!DNL Creative Cloud] -app te verlaten. | [ de Verbinding van Activa van Adobe ](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html) | Photoshop, Illustrator en InDesign. |
| Zakelijke gebruikers vereenvoudigen het openen en gebruiken van middelen, het bewerken en uploaden van wijzigingen in [!DNL Experience Manager] en het uploaden van nieuwe bestanden naar [!DNL Experience Manager] vanuit de bureaubladomgeving. Ze gebruiken een algemene integratie om elk elementtype te openen in de native bureaubladtoepassing, inclusief niet-Adobe-toepassingen. | [[!DNL Experience Manager]  Desktop app ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html) | Experience Manager-bureaubladtoepassing op Win- en Mac-desktop |
| Marketers en zakelijke gebruikers detecteren, voorvertonen, licentiëren en opslaan, en beheren de Adobe Stock-middelen vanuit Experience Manager. Gelicentieerde en opgeslagen middelen bieden geselecteerde Adobe Stock-metagegevens voor beter beheer. | [ de integratie van Experience Manager en van Adobe Stock ](aem-assets-adobe-stock.md) | [!DNL Experience Manager] webinterface |
| De samenwerking tussen ontwerpers van digitale producten en marketers verbeteren. Laat ontwerpers de digitale elementen gebruiken in ontwerp- en draadframemodellen op het Adobe XD-canvas. | [[!DNL Adobe Asset Link]  voor  [!DNL Adobe XD] ](https://helpx.adobe.com/enterprise/using/adobe-asset-link-for-xd.html) | [!DNL Adobe XD] |
| Marktdeelnemers kunnen automatisch variaties en derivaten maken op basis van geüploade elementen en vooraf gedefinieerde handelingen die met behulp van aanpassingen zijn gemaakt. Gebruik deze automatisering om de snelheid van de inhoud te verbeteren en handmatige inspanningen te verminderen. | [ de automatisering van de Inhoud ](/help/assets/cc-api-integration.md) | [!DNL Experience Manager Assets] webinterface |

Dit artikel richt zich hoofdzakelijk op de eerste twee aspecten van de samenwerkingsbehoeften. Distributie en sourcing van assets op schaal wordt kort als gebruiksscenario genoemd. Overweeg Adobe Brand Portal of Asset Share Commons voor dergelijke oplossingen. De afwisselende oplossingen zoals [ Experience Manager Assets Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html), oplossingen die kunnen worden gebouwd gebaseerd op [ de Commons van het Aandeel van Activa ](https://opensource.adobe.com/asset-share-commons/) componenten, [ het Aandeel van de Verbinding ](share-assets.md), gebruikend [ het Web UI van Experience Manager Assets ](/help/assets/manage-digital-assets.md) zou moeten worden herzien gebaseerd op specifiek vereiste.

![ de verbindingen van Creative Cloud voor Experience Manager: Beslissend welk vermogen aan gebruik ](assets/creative-connections-aem.png)

Bepalen welke mogelijkheden moeten worden gebruikt

### Toewijzing van gebruiksgevallen en Adobe-oplossingen {#mapping-of-use-cases-and-adobe-solutions}

| Hoofdletters gebruiken | Adobe Asset Link | Experience Manager-bureaubladtoepassing | Opmerkingen of alternatieve methoden |
|----------------------------------------------------------|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Detecteren - naar mappen bladeren | Ja | Experience Manager Web UI + bureaubladacties | Als u op het gedeelde netwerk bladert, schakelt u de miniaturen uit om te voorkomen dat binaire bestanden met elementen worden gedownload. |
| Detecteren - toegangsverzamelingen | Ja | Experience Manager Web UI + bureaubladacties |  |
| Detecteren - zoeken naar middelen | Ja | Experience Manager Web UI + bureaubladacties |  |
| Gebruiken - element openen | Ja | Ja, voor elke app | [ Open van de interface van het Web ](/help/assets/manage-digital-assets.md#previewing-assets) of van Vinder |
| Gebruiken - Middelen uit Experience Manager in een document plaatsen | Ja - insluiten | Ja - koppelen of insluiten | De Experience Manager-bureaubladtoepassing biedt toegang tot elementen als bestanden op het lokale bestandssysteem. Deze koppelingen in de native apps worden weergegeven door lokale paden. |
| Bewerken - openen voor bewerking | Ja, uitchecken, actie | Ja - Handeling openen (in netwerkshare) | [ Controle-uit in AAL ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) bewaart de activa aan de creatieve rekening van de wolkenopslag van de gebruiker (die door Creative Cloud app wordt gesynchroniseerd) door gebrek. |
| Bewerken - Bezig met werk buiten Experience Manager | Ja - Asset beschikbaar in de Creative Cloud-opslagaccount van de gebruiker gesynchroniseerd met desktop. | Ja |  |
| Bewerken - wijzigingen uploaden | Ja - [ Controle-in actie ](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html) met facultatieve commentaar | Ja |  |
| Uploaden - één bestand | Ja - het actieve document wordt geüpload | Ja | [ uploadt via Webinterface ](/help/assets/manage-digital-assets.md#uploading-assets) |
| Uploaden - meerdere bestanden / hiërarchische mapstructuren | Nee | Ja | [ uploadt via Webinterface ](/help/assets/manage-digital-assets.md#uploading-assets); Het scripting van de Douane of hulpmiddel |
| Diverse - gebruiker en aanmelding | Creative Cloud-gebruiker die zich heeft aangemeld bij Creative Cloud-bureaubladtoepassing wordt herkend (SSO) | Experience Manager-gebruiker/aanmelding | Gebruikers van beide oplossingen tellen mee voor de Experience Manager-gebruikersquota. |
| Diverse - netwerk en toegang | Toegang van desktop tot Experience Manager via netwerk vereist | Toegang van desktop tot Experience Manager via netwerk vereist | Adobe Asset Link deelt geen omgeving voor netwerkproxy. |


<!-- Removing this row from table as migration guide is not yet final.
| Misc - Migrate large number of assets | No | No | [Migration Guide](/help/assets/assets-migration-guide.md) |
-->

Houd rekening met de volgende opties ter ondersteuning van het gebruik van gevallen voor distributie van bedrijfsmiddelen:

* [ Experience Manager Assets Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor een configureerbare toe:voegen-op aan Assets om activa te publiceren.

* De oplossingen van de douane worden gecreeerd gebaseerd op ](https://opensource.adobe.com/asset-share-commons/) de codebasis van het Aandeel van activa 0}.[
* Experience Manager [ verbindingsaandeel ](/help/assets/share-assets.md) om activa te delen op bestelling gebruikend verbindingen.
* [ het Webinterface van Assets ](/help/assets/manage-digital-assets.md) met gebieden voor externe partijen die door de opstelling van het Toegangsbeheer van Experience Manager en met noodzakelijke aanpassingen van IT/netwerkconfiguratie worden beveiligd, die deze externe gebruikers toegang tot Experience Manager geven.

## Belangrijkste concepten en gebruiksgevallen {#key-concepts-and-use-cases}

### Verklarende woordenlijst {#glossary-of-common-terms}

* **Werk in uitvoering of creatief werk in uitvoering (WIP):** Een fase in de levenscyclus van assets waarbij een asset meerdere wijzigingen ondergaat en doorgaans nog niet klaar is om te worden gedeeld met grotere teams.
* **Creatieve assets:** Assets die klaar zijn om te worden gedeeld met een groter team, of die zijn geselecteerd/goedgekeurd door het creatieve team om te delen met marketing- of LOB-teams.

* **Goedkeuring van assets:** Het goedkeuringsproces dat wordt uitgevoerd voor assets die reeds naar DAM zijn geüpload, en dat typisch merkgoedkeuringen, wettelijke goedkeuringen, enz. omvat.
* **Definitieve asset:** Een asset die alle goedkeuringen/metadatatagging heeft doorlopen en klaar is om door het grotere team te worden gebruikt. Een dergelijke asset wordt opgeslagen in DAM en beschikbaar gesteld aan alle (geïnteresseerde) gebruikers. Deze kan in marketingkanalen of door creatieve teams worden gebruikt om ontwerpen te maken.

* **Kleine update/wijziging van assets:** Een snelle en kleine wijziging in een digitale asset. Deze wordt vaak uitgevoerd als reactie op een retoucheerverzoek of een verzoek om kleine bewerkingen, een assetrevisie of goedkeuring (bijvoorbeeld om de positie te wijzigen, de tekstgrootte te wijzigen, de verzadiging/helderheid en kleur aan te passen, enz.).
* **Belangrijke update/wijziging van assets:** Een verandering in een digitale asset die aanzienlijk werk vereist, en soms over een langere periode moet worden uitgevoerd. Dit omvat doorgaans meerdere wijzigingen. De asset moet tijdens het bijwerken meerdere keren worden opgeslagen. De belangrijkste assetupdates leiden er doorgaans toe dat de asset een WIP-status krijgt.
* **DAM:** Beheer van digitale assets. In dit document is het synoniem met Experience Manager Assets, tenzij uitdrukkelijk anders vermeld.
* **Creatieve gebruiker:** Een creatieve professional die digitale assets maakt met Creative Cloud-apps en -services. In sommige gevallen is een creatieve gebruiker lid van een creatief team dat mogelijk Creative Cloud gebruikt, maar geen digitale assets maakt (zoals een creatieve directeur of een creatieve teammanager).
* **DAM-gebruiker:** Een typische gebruiker van een DAM-systeem. Afhankelijk van de organisatie, kan een gebruiker DAM een marketing of een niet-marketing gebruiker, bijvoorbeeld, een lijn-van-Bedrijfs (LOB) gebruiker, bibliothecaris, verkooppersoon, etc. zijn.

### Overwegingen bij het gebruik van de integratie van Experience Manager en Creative Cloud {#considerations-when-using-aem-and-creative-cloud-integration}

<!--incomplete and TBD: 

* DA2.0 best practices: See troubleshooting.md
* Stock integration: See ?
* AAL: See ?
* BP: See ?

-->

Dit is een korte samenvatting van beste praktijken voor de Integratie van Experience Manager en Creative Cloud. Lees de rest van dit document voor een gedetailleerd begrip hiervan.

* **voor creatieve gebruikers, die in Photoshop, InDesign, of Illustrator werken:** De Verbinding van de Activa van Adobe verstrekt de beste gebruikerservaring, met inbegrip van schone behandeling van het Werk in uitvoering op activa die uit Experience Manager worden gecontroleerd
* **voor het vereenvoudigen van toegang tot activa van Desktop voor om het even welk generisch dossierformaat of toepassing:** gebruik Experience Manager Desktop app
* **Begrijpen waarom en wanneer assets in DAM moeten worden opgeslagen:** Updates die ter beschikking moeten worden gesteld aan een groter team in uw organisatie
* **Houd rekening met het volume van de gedeelde assets:** Als u gebruikmaakt van assetdistributie, kunnen governance en beveiliging de belangrijkste aspecten zijn. Overweeg om tools te gebruiken die bedoeld zijn om governance en beveiliging op grote schaal toe te passen, zoals de Brand Portal.
* **De levenscyclus van assets begrijpen:** Begrijp hoe assets in uw organisatie worden verwerkt door verschillende teams
* **Correct en regelmatig opslaan van assets:** Adobe Asset Link doet dit voor u met PS, AI, ID. Voer voor andere toepassingen geen actieve taken uit in toegewezen/gedeelde map tenzij u alle wijzigingen in DAM nodig hebt

### Toegang tot Adobe Stock-middelen van Experience Manager Assets {#access-to-adobe-stock-assets-from-aem-assets}

[ de integratie van Experience Manager en van Adobe Stock ](/help/assets/aem-assets-adobe-stock.md) voorziet de gebruikers van Experience Manager van de capaciteit om, activa van Adobe Stock in Experience Manager te zoeken, voor te vertonen, vergunning te geven en te bewaren. Bij gelicentieerde en opgeslagen Adobe Stock-elementen zijn de metagegevens van de Stock geselecteerd. Deze kunnen worden gebruikt om met extra filters naar deze elementen te zoeken.

Een paar belangrijke punten over deze integratie:

* Wanneer middelen uit Adobe-voorraad worden opgeslagen naar Experience Manager, worden ze een gewone Experience Manager Assets, met binair opgeslagen naar de Experience Manager-opslagplaats. Sommige metagegevens die betrekking hebben op Adobe Stock, worden opgeslagen voor het element in Experience Manager. Als dit niet het geval is, ziet het innameproces er hetzelfde uit als voor andere bestanden. Als slimme tags bijvoorbeeld actief zijn, worden de tags bij het opslaan aan deze elementen toegevoegd.
* Het middel dat is opgeslagen naar Experience Manager is een kopie, geen koppeling naar Adobe Stock.

**Werkend met activa die van Adobe Stock in Experience Manager in Creative Cloud** worden bewaard. Deze integratie is onafhankelijk van Adobe Asset Link, maar Adobe Asset Link herkent deze middelen die op die manier uit Stock zijn opgeslagen en geeft aanvullende metagegevens en het pictogram Stock weer voor deze middelen in de Adobe Asset Link-extensie in Photoshop, Illustrator of InDesign. De bestanden zijn beschikbaar voor bladeren, openen enzovoort, omdat het normale Experience Manager-middelen zijn die worden opgeslagen in Experience Manager.
Creative-gebruikers die werken in Creative Cloud-apps met de Adobe Asset Link-extensie aanwezig, hebben naast toegang tot reeds in licentie gegeven middelen van Adobe Stock naar Experience Manager ook toegang tot het Creative Cloud Libraries-deelvenster om Adobe Stock-middelen te zoeken, voor te vertonen en in licentie te geven.
Assets uit Adobe Stock met een licentie en opgeslagen in Experience Manager wordt beschikbaar voor de bredere teams die toegang hebben tot de implementatie van Experience Manager Assets, terwijl creatieve licentiefaciliteiten uit Adobe Stock via het deelvenster Creative Cloud Libraries ze alleen standaard beschikbaar maken voor zichzelf in hun Creative Cloud-account.

## Elementen opslaan in een DAM {#about-storing-assets-in-a-dam}

Om een efficiënte werkstroom tussen creatieve en marketing/lijn-van-zaken (LOB) teams te ontwerpen en de beste steunmogelijkheden te kiezen, is het belangrijk om te begrijpen wanneer en waarom de activa in DAM worden opgeslagen.

### Waarom elementen zijn opgeslagen in DAM {#why-assets-are-stored-in-dam}

Door middelen in DAM op te slaan, zijn ze gemakkelijk toegankelijk en te vinden. Het zorgt ervoor dat de activa door talrijke gebruikers over de organisatie of het ecosysteem kunnen worden gebruikt, die partners, klanten, etc. omvat.

De meeste organisaties kiezen ervoor om activa slechts op te slaan die voor de stroomafwaartse marketing/LOB processen relevant zijn (het publiceren aan kanalen zoals Webkanaal via Experience Manager Sites of andere kanalen die door Adobe Experience Cloud - Marketing Cloud worden gediend, Advertising Cloud, en gemeten door Analytics Cloud, die aan gebruikers/partners, etc. verstrekken). Bovendien slaan organisaties activa op die aan een overzicht/goedkeuringsprocedure in DAM kunnen worden onderworpen. Op deze manier slaat DAM vooral activa op die een grote kans hebben om te worden gebruikt, en vermijdt het opslaan van niet-actieve activa.

De opslag van activa is ook onderworpen aan technische overwegingen en middelgebruik. DAM verleent de extra diensten rond opgeslagen activa, met inbegrip van het halen van meta-gegevens, het versioning, het produceren van voorproeven/het transcoderen, het beheren van verwijzingen, en het toevoegen van toegangsbeheerinformatie. Deze diensten verbruiken extra tijd en infrastructuurmiddelen.

Vaak is het niet wenselijk om alle elementen en updates op te slaan. Bijvoorbeeld, als de updates aan specifieke activa van slechte kwaliteit zijn en bovenmatige middelen verbruiken, kunnen de activa niet in DAM worden opgeslagen.

#### Wanneer elementen zijn opgeslagen in DAM {#when-assets-are-stored-in-dam}

Creative-teams (en -organisaties) zijn gewoonlijk niet geïnteresseerd in het opslaan van middelen in elke fase van de levenscyclus van de middelen. In de volgende gevallen worden bijvoorbeeld geen elementen opgeslagen:

* Assets dat nog moet worden afgerond of moet worden getest
* Assets die de beoordelingscyclus voor creatieve/interne teams niet doorstaat
* Vergeleken met de middelen in kwestie, heeft het team betere kandidaten om hun werk aan externe teams te vertegenwoordigen

Gewoonlijk worden de volgende klassenelementen opgeslagen in DAM:

* Assets dat een bepaalde looptijd heeft bereikt en klaar wordt geacht om te worden gedeeld
* Assets die vooraf is geselecteerd door het creatieve team
* Specifieke asset-indelingen die kunnen worden gebruikt of aangevraagd door marketing, afhankelijk van een specifiek contract of een specifieke overeenkomst (bijvoorbeeld JPG-bestanden die zijn geconverteerd van RAW-bestanden, TIFF-bestanden/afbeeldingen van PSD-originelen)

#### Wanneer updates van elementen worden opgeslagen in DAM {#when-updates-to-assets-are-stored-in-dam}

Normaliter moeten alleen updates van middelen die relevant zijn voor de bredere reeks DAM-gebruikers in DAM worden opgeslagen. Hiermee zorgt u ervoor dat gebruikers (marketing en soortgelijke functies) alleen relevante versies in de tijdlijn van de DAM-middelen zien.

Doorgaans zijn er wijzigingen die betrekking hebben op belangrijke mijlpalen in de levenscyclus van de middelen. Het eerste marketingklare middel of een officiële update op basis van een verzoek/revisie van het creatieve team moet bijvoorbeeld worden opgeslagen en gecontroleerd in DAM.

De update van het creatieve team voor revisie door het marketingteam na een verzoek om wijziging van het bestaande middel in DAM is een voorbeeld van een relevante update. Het zou in DAM voor verdere verwijzing of voor het terugkeren naar de vorige versie moeten worden opgeslagen en worden versioned.

Hieronder volgen voorbeelden van updates die doorgaans niet relevant zijn:

* Vroege versies van elementen die zijn geüpload voordat ze klaar zijn voor marketingcontrole
* Veelvoorkomende creatieve wijzigingen in het bedrijfsmiddel in de aan de gang zijnde fase voordat creatieve en marketingteams besluiten dat het middel klaar is

### Toegang van gebruikers tot DAM {#user-access-to-dam}

Experience Manager Assets ondersteunt twee soorten gebruikers op basis van hun toegang tot de Experience Manager Assets-implementatie. Doorgaans hebben gebruikers binnen het bedrijfsnetwerk (firewall) directe toegang tot DAM. Andere gebruikers buiten het ondernemingsnetwerk zouden geen directe toegang hebben. Het gebruikerstype bepaalt welke integraties vanuit technisch oogpunt kunnen worden gebruikt.

#### Creative-gebruikers met directe toegang tot DAM {#creative-users-with-direct-access-to-dam}

In het algemeen hebben interne creatieve teams of agentschappen/creatieve professionals die aan het interne netwerk zijn toegewezen, toegang tot het DAM-exemplaar, inclusief Experience Manager-aanmelding. Experience Manager en netwerkinfrastructuur kunnen worden ingesteld om directe toegang te verlenen tot externe partijen - doorgaans vertrouwde organisaties zoals organisaties die voor een klant werken - om toegang te hebben tot Experience Manager via een netwerk, bijvoorbeeld via VPN of IP-lijst van gewenste personen.

In dergelijke gevallen biedt de Adobe Asset Link- of Experience Manager-bureaubladtoepassing eenvoudig toegang tot definitieve/goedgekeurde middelen en kunt u creatieve middelen opslaan in DAM.

#### Creative-gebruikers zonder toegang tot DAM {#creative-users-without-access-to-dam}

Externe agentschappen en freelancers zonder directe toegang tot het DAM-exemplaar hebben mogelijk toegang tot goedgekeurde activa nodig of willen hun nieuwe ontwerpen toevoegen aan het DAM.

Gebruik de volgende strategieën om toegang te verlenen tot definitieve/goedgekeurde middelen:

* Gebruik de bureaubladtoepassing als Asset Link niet werkt.
* Het gebruik [ Experience Manager Assets Brand Portal ](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/home.html) voor het verdelen van activa veilig aan externe partners
* Gebruik een douanetoepassing van een distributie en het sourcen portaal die op [ wordt gebaseerd de Commons van het Aandeel van Activa ](https://adobe-marketing-cloud.github.io/asset-share-commons/)
* Het Toegangsbeheer van het gebruik opstelling in Experience Manager en noodzakelijke netwerkinfrastructuur (bijvoorbeeld, VPN en IP toegestaan lijst) om externe partijen toegang tot een specifiek gebied van inhoud in uw DAM te geven. Ze kunnen Experience Manager Web UI gebruiken om middelen op te halen en nieuwe inhoud te uploaden naar uw DAM.

#### Aan de slag met middelen van Experience Manager {#work-in-progress-on-assets-from-aem}

Zoals in dit document wordt besproken, wordt het aanbevolen belangrijke updates uit te voeren voor elementen, ook wel &#39;werk in uitvoering&#39; genoemd, zonder dat alle bewerkingen die in het lokale bestand zijn opgeslagen, als wijzigingen naar Experience Manager worden geüpload. Dit versnelt het werk van een Desktopgebruiker, beperkt gebruikte netwerkbandbreedte, en houdt de activa chronologie schoon en concentreert zich op gecontroleerde, belangrijke updates.

Adobe Asset Link biedt een goede ondersteuning voor dit gebruiksgeval:

* Wanneer gebruikers in Photoshop, InDesign of Illustrator van plan zijn een bestand te bewerken, voeren ze een uitcheckbewerking uit op het opgegeven element
* Het middel wordt op de achtergrond gedownload, in gebruikers wordt gezet Creative Cloud-account door Creative Cloud desktop app op schijf gesynchroniseerd en de markering voor uitchecken wordt in Experience Manager op het middel in- en uitgeschakeld om bewerkingsconflicten te minimaliseren
* Vanaf dat punt werkt de gebruiker in een bestand dat lokaal is opgeslagen op de gesynchroniseerde locatie. De gebruiker kan doorgaan met het werken en opslaan van noodzakelijke wijzigingen met elke vereiste frequentie
* Aangezien het element zich in de Creative Cloud-account bevindt, is het ook beschikbaar op andere apparaten die de gebruiker mogelijk heeft (kunnen bijvoorbeeld worden geopend of bewerkt in een speciale Creative Cloud mobile-app) en kan het voor samenwerkingsdoeleinden worden gedeeld met andere Creative Cloud-gebruikers.
* Wanneer de creatieve gebruiker klaar is met de wijzigingen, kan hij of zij een incheckbewerking op dat bestand uitvoeren in zijn of haar Creative Cloud-toepassing, met een optionele opmerking. Het corresponderende element in Experience Manager wordt versioned en bijgewerkt met het nieuwe binaire element. Experience Manager-gebruikers zoals Marketers of LOB-gebruikers hebben via de tijdlijngebruikersinterface van Experience Manager toegang tot belangrijke wijzigingen in activa of mijlpalen.

De Experience Manager-bureaubladtoepassing biedt een netwerkshare voor elementen die zijn geopend in de native app. Standaard worden alle lokaal uitgevoerde wijzigingen na een korte tijd automatisch geüpload naar Experience Manager. Met zo&#39;n configuratie, zouden de frequente besparingen tijdens de werk-in-lopende fase allen in Experience Manager en versioned worden geupload, die tot een grote hoeveelheid netwerkverkeer en potentiële scalability uitdagingen leiden - om het even welke onnodige versies in Experience Manager te noemen.

Hier kunt u het beste een optie in de Experience Manager-bureaubladtoepassing gebruiken om geautomatiseerde updates uit te schakelen en wijzigingen in middelen handmatig te uploaden naar Experience Manager met de actie voor uploadwijzigingen in de Asset Status UI van de app.

#### Bulkupload naar DAM {#bulk-upload-to-dam}

In sommige gevallen moet u wellicht een groter aantal bestanden tegelijkertijd uploaden naar DAM, bijvoorbeeld:

* Resultaten van foto&#39;s of grotere projecten uploaden
* Door creatieve bureaus geleverde activa uploaden
* Geselecteerde elementen uploaden vanaf een grotere set als de selectie buiten DAM is uitgevoerd

Deze beschrijving verwijst naar het operationeel uploaden van bestanden (bijvoorbeeld elke week of met elke foto), als een normaal onderdeel van de workflow van de desktopgebruiker. De migratie van grote activa wordt hier niet behandeld.

U kunt de volgende uploadmogelijkheden gebruiken:

* Om grote/hiërarchische omslagen in massa te uploaden, gebruik Experience Manager Desktop app die [ omslag verstrekt uploadt ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#bulk-upload-assets) functionaliteit. U kunt ook hiërarchische mapstructuren uploaden. Assets wordt op de achtergrond geüpload en is daarom niet gekoppeld aan een webbrowsersessie
* Als u enkele bestanden uit één map wilt uploaden, sleept u de bestanden rechtstreeks naar de webinterface of gebruikt u de optie Maken in de Experience Manager Assets-webinterface.
* Afhankelijk van uw bedrijfsvereisten kunt u ook aangepaste uploader gebruiken.

#### Digitale middelen rechtstreeks vanaf het bureaublad beheren {#managing-digital-assets-directly-from-desktop}

Als u Delen van netwerkbestanden gebruikt voor het beheer van digitale elementen, kan het gebruik van de netwerkshare die is toegewezen door de Experience Manager-bureaubladtoepassing worden beschouwd als een handige vervanging. Bij de overgang van netwerkbestanden biedt de Experience Manager-webinterface een uitgebreide reeks Digital Asset Management-mogelijkheden die veel verder gaan dan wat mogelijk is op een gedeeld netwerk (zoeken, verzamelingen, metagegevens, samenwerking, voorvertoningen enzovoort) en de Experience Manager-bureaubladtoepassing biedt een handige koppeling om de DAM-opslagplaats aan de serverzijde te verbinden met het werk op een desktopcomputer.

Vermijd het gebruik van de Experience Manager-bureaubladtoepassing voor het rechtstreeks beheren van middelen in het netwerkaandeel van Experience Manager Assets. Vermijd bijvoorbeeld het gebruik van de Experience Manager-bureaubladtoepassing voor het verplaatsen/kopiëren van meerdere bestanden. Gebruik in plaats daarvan de Experience Manager Assets-webinterface om mappen van Finder/Explorer naar het gedeelde netwerk te slepen of gebruik de Experience Manager Assets-functie voor het uploaden van mappen.

**zie ook**

* [Assets vertalen](translate-assets.md)
* [ASSETS HTTP API](mac-api-assets.md)
* [Door Assets ondersteunde bestandsindelingen](file-format-support.md)
* [Zoeken in middelen](search-assets.md)
* [Verbonden elementen](use-assets-across-connected-assets-instances.md)
* [Elementen rapporteren](asset-reports.md)
* [Metagegevensschema&#39;s](metadata-schemas.md)
* [Elementen downloaden](download-assets-from-aem.md)
* [Metagegevens beheren](manage-metadata.md)
* [Zoeken in facetten](search-facets.md)
* [Verzamelingen beheren](manage-collections.md)
* [Bulkmetagegevens importeren](metadata-import-export.md)
* [Assets publiceren naar AEM en Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)
