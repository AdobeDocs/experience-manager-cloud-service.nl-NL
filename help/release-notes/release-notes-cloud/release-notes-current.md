---
title: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
description: Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6c1320d43b551247e63962dd52ada58d463fb92e
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als een Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>Vanaf hier kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De datum van de Versie voor [!DNL Adobe Experience Manager] als Cloud Service 2021.4.0 is 6 Mei, 2021.
De volgende release (2021.5.0) vindt plaats op 27 mei 2021.

## AEM als Stichting van de Cloud Service{#aem-as-a-cloud-service-foundation}

### Nieuwe functies {#what-is-new-foundation}

* [Workflow](/help/operations/replication.md#publish-content-tree-workflow)  van de inhoudsstructuur publiceren - Een nieuw workflowmodel en een nieuwe stap leveren betere prestaties bij het publiceren van diepe hiërarchieën met inhoud.

## [!DNL Adobe Experience Manager Sites] als  [!DNL Cloud Service] {#sites}

### Nieuw in [!DNL Sites] {#what-is-new-sites}

* Eindpunten GraphQL - het is nu mogelijk om AEM GraphQL API voor individuele configuraties van AEM Sites toe te laten en om de eindpunten van douaneGraphQL voor die configuraties tot stand te brengen door een nieuwe console te gebruiken GraphQL UI. UI staat ook het beheren van eindpunten GraphQL toe.

* Inhoudsmodellen, verbeterd gegevenstype Datum&amp;tijd - het is nu mogelijk het datum&amp;tijdtype te configureren om alleen datum-, alleen tijd- of datum- en tijdgegevens voor de auteur toe te staan.

* Inhoudsmodellen, uitgebreid gegevenstype Codes - het is nu mogelijk het gegevenstype Codes te configureren om het schrijven van enkele of meerdere tags toe te staan.

* Inhoudsmodellen, nieuw gegevenstype Tijdelijke aanduiding voor tabblad - het nieuwe gegevenstype Tijdelijke aanduiding voor tabblad maakt het mogelijk gegevenstypen te groeperen in secties die worden gerenderd onder tabbladen in de inhoudsfragmenteditor.

### Opgeloste problemen in [!DNL Sites] {#bug-fixes-sites}

* Inhoudsfragmenten: het verplaatsen van inhoudsfragmenten of -mappen werkt nu geneste verwijzingen in het fragment bij (CQ-4320815)

* GraphQL - voortgezette vragen steunen nu user-defined eindpunten die voor configuraties AEM Sites specifiek zijn (CQ-4315928)

## [!DNL Adobe Experience Manager Assets] als  [!DNL Cloud Service] {#assets}

### Nieuw in [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] één elementdownload niet archiveert op de plaats waar het oorspronkelijke bestand is gedownload. Deze verbetering maakt snellere downloads mogelijk. Zie [Elementen downloaden](/help/assets/download-assets-from-aem.md).

* Wanneer u een element downloadt via een koppelingsoptie, kunt u nu kiezen of u de uitvoeringen wilt downloaden of niet. Eerder werden alle elementuitvoeringen gedownload. Zie [downloadopties](/help/assets/download-assets-from-aem.md).

* Wanneer het uitvoeren van een gezondheidscontrole om activa in bulk in te voeren, verstrekt de Experience Manager nu meer informatieredenen voor mislukkingen. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Bij het importeren van elementen met het gereedschap voor bulkimport hebben beheerders nu de optie om de bronbestanden te verwijderen nadat het importeren is voltooid. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Als u een metagegevensschema bewerkt, kunnen beheerders de selectie snel en eenvoudig maken met een nieuw veld voor de padkiezer. Deze verbetering helpt de configuratietijd voor metagegevens te verminderen.

* Metagegevens van vele elementen kunnen bulksgewijs worden geïmporteerd met behulp van een CSV-bestand en kunnen worden geëxporteerd naar een CSV-bestand. De standaarddatumnotatie is nu `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Gebruikers kunnen een andere indeling gebruiken door de kolomkop bij te werken. Voeg bijvoorbeeld `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` toe als kolomkop in het CSV-bestand in plaats van het woord `Date`. Zie [Metagegevens importeren](/help/assets/metadata-import-export.md).

* Wanneer u elementen bladert in de kolomweergave, geeft een visuele indicator de goedgekeurde of geweigerde status van elk element weer.

* Bij het bladeren door elementen in de kolomweergave wordt een visuele indicator weergegeven voor verlopen elementen.

* Een gegevenstype van het tekstgebied wordt ter beschikking gesteld in [!DNL Assets] meta-gegevensredacteur. Met deze optie kunt u gebruikers metagegevens laten invoeren in een tekstveld in een vrije vorm.

### Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* Wanneer u probeert meerdere elementen of mappen te verplaatsen, wordt een fout in de console gemeld en wordt de verplaatsingsbewerking niet voltooid. Verplaatsen mislukt als de titel niet kan worden bijgewerkt. (CQ-432/2008)

* Een metagegevensveld kan op basis van een regel worden verborgen, zodat metagegevens niet verplicht zijn wanneer aan een vooraf gedefinieerde voorwaarde wordt voldaan. Dergelijke verborgen metagegevensvelden worden echter als vereiste velden weergegeven. (CQ-4321285)

* Bulk-metagegevens kunnen niet worden geïmporteerd omdat de datumnotatie onjuist is. (CQ-4319/014)

* Wanneer op de pagina Eigenschappen een selectie wordt gemaakt om metagegevens bij te werken, reageert de interface langzaam wanneer het schema veel opties bevat. (CQ-4318538)

* Tijdens het bijwerken en opslaan van de metagegevenswaarde in een tekstveld met één regel, worden de waarden in het vervolgkeuzemenu verwijderd, zelfs als de bewerkingen zijn uitgeschakeld in het vervolgkeuzemenu. (CQ-4317077)

* U kunt ellips gebruiken als een aantekening om elementen te bekijken. Wanneer een kleine ellips wordt gebruikt, overlapt de ellips met het aantal van de annotatie in de drukversie. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms}

Met [AEM Forms kunt u als Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/home.html) digitale formulieren maken, formulieren verbinden met bestaande gegevensbronnen, formulieren integreren met Adobe Sign om e-handtekeningen toe te voegen aan formulieren, Document of Record genereren (DoR) om verzonden formulieren als PDF-bestanden te archiveren. De service kan uw bestaande PDF forms ook converteren naar digitale formulieren. Naast de standaard AEM Forms-functies biedt de service verschillende mogelijkheden in de cloud, zoals automatisch schalen, geen downtime voor upgrades en ontwikkelomgeving in de cloud. Lees [dit blogbericht](https://blog.adobe.com/en/publish/2021/03/11/experience-manager-forms-as-a-cloud-service.html) voor meer informatie over de mogelijkheden en functies van AEM Forms als Cloud Service.

* **Gebruik de methode voor identiteitsverificatie van overheidsidentiteiten in met Adobe Sign ingeschakelde Adaptieve Forms**

   Met behulp van geavanceerde computerleeralgoritmen kunnen bedrijven over de hele wereld dankzij het Adobe Sign-proces voor overheidsidentiteitskaart een kwalitatief hoogstaande verificatie van de identiteit van hun ontvanger krijgen. Nu kunt u de methode voor identiteitsverificatie van overheidsidentiteiten gebruiken in met Adobe Sign ingeschakelde Adaptive Forms.

   De identiteitskaart van de overheid is een methode van de identiteitsauthentificatie van de premie die de ontvanger opdraagt om [het beeld van een door de overheid uitgegeven identiteitsdocument (rijbewijs, nationale identiteitskaart, paspoort) ](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html) te uploaden, en dan dat document te evalueren om het authentiek te verzekeren.

* **Ondersteuning voor het gebruik van ondertekeningservaring in formulieren voor asynchrone, adaptieve verzending van formulieren**

   U kunt de ondertekeningservaring in formulieren nu gebruiken voor asynchrone, adaptieve verzending van formulieren. U kunt ook een adaptief formulier insluiten in een [!DNL Experience Manager Sites]-pagina en de ondertekeningservaring in formulieren gebruiken voor het verzenden van aangepaste formulieren.

* **Ondersteuning voor het gebruik van een variabele om een bijlage op te geven terwijl een adaptief formulier vooraf wordt ingevuld voor een taakstap Toewijzen**

   Terwijl u een adaptief formulier vooraf invult voor een toewijzingsstap, kunt u nu een variabele van het documenttype gebruiken om een invoerbijlage te selecteren voor het adaptieve formulier.

* **Ondersteuning voor het gebruik van de letterlijke optie voor het instellen van de waarde voor een JSON-typevariabele**

   U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

* **De lokale ontwikkelomgeving gebruiken om Document of Record (DoR) te maken**

   U kunt een XDP als Document van het malplaatje van het Verslag op de instanties van de Cloud Service en AEM Forms als Cloud Service SDK (Lokale ontwikkelomgeving) gebruiken. Eerder was de ondersteuning beperkt tot alleen Cloud Servicen.

### Opgeloste problemen in [!DNL Forms] {#bug-fixes-forms}

* Wanneer een Adaptief formulier dat is geconfigureerd om Document of Record niet te genereren, wordt verzonden naar een AEM Workflow die is geconfigureerd om Document of Record te genereren, wordt geen foutbericht weergegeven en kan de taak niet worden verzonden.

### Overige updates {#misc-2021-04-0-forms}

* De service genereert nu live miniaturen voor XDP-, dynamische PDF- en Schema-bestanden, zodat inhoud gemakkelijker kan worden herkend.
* Voeg de mogelijkheid toe om een PDF-bestand te verplaatsen naar een map die in de gebruikersinterface van AEM Forms is geplaatst.

## Adobe Experience Manager Commerce als Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Ondersteuning voor categorie UID - Hierdoor wordt integratie van andere leveranciers mogelijk voor systemen die strings gebruiken voor categorie-id&#39;s

* AEM extensie voor PWA Studio incl. voorbeeldintegratie

* Nieuwe CIF-kerncomponent voor navigatie die de WCM-kerncomponent voor navigatie uitbreidt

* Visuele indicator voor gefaseerde catalogusgegevens in AEM storefront

* Het eindpunt van de handel kan nu worden geconfigureerd via de interface van Cloud Manager

### Opgeloste problemen {#bug-fixes-commerce}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s


## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.5.0 en 2021.4.0.

### Releasedatum {#release-date-cm-may}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.5.0 is 6 mei 2021.
De volgende release is gepland voor 3 juni 2021.

### Wat is er nieuw?{#what-is-new-may}

* De PackageOverlaps kwaliteitsregel ontdekt nu gevallen waar het zelfde pakket veelvoudige tijden, d.w.z. in veelvoudige ingebedde plaatsen, in de zelfde opgestelde pakketreeks werd opgesteld.

* Het eindpunt van de repository in de Public API bevat nu de Git URL.

* Het implementatielogboek dat door een gebruiker van Cloud Manager wordt gedownload, is begrijpelijker en bevat nu details over fouten en successcenario&#39;s.

* Intermitterende fouten die werden aangetroffen tijdens het doorvoeren van code naar Adobe-it, zijn nu opgelost.

* Invoegtoepassing voor handel kan nu worden toegepast op Sandbox-programma&#39;s tijdens de workflow van het bewerkingsprogramma.

* De ervaring met het bewerkingsprogramma is vernieuwd.

* De lijst van de Namen van het Domein in de pagina van Details van het Milieu zal tot 250 namen van Domein via paginering tonen.

* Het lusje van Oplossingen in Add Programma en geef de werkschema&#39;s van het Programma uit zal de oplossing tonen, zelfs als slechts één oplossing voor het Programma beschikbaar is.

* Het foutenbericht in het bouwstijlstaplogboek toen de bouwstijl geen opgestelde inhoudspakketten produceerde was onduidelijk.

### Opgeloste problemen {#bug-fixes-cm-may}

* Soms, kan de gebruiker een groene &quot;actieve&quot;status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* In plaats van &#39;verwijderde&#39; variabelen te verwijderen, markeert de API voor pijpleidingvariabelen deze alleen met status **DELETED**.

* Sommige kwaliteitskwesties van het type Code Smell hadden een onjuiste invloed op de beoordeling Betrouwbaarheid.

* Omdat jokertekendomeinen niet worden ondersteund, staat de gebruikersinterface de gebruiker niet toe een jokertekendomein in te dienen.

* Wanneer een pijpleidingsuitvoering tussen middernacht en 1am UTC werd begonnen, werd de artefactversie die door de Manager van de Wolk werd geproduceerd niet gewaarborgd om groter te zijn dan een versie die de vorige dag werd gecreeerd.

* Tijdens de opstelling van het programma Sandbox, zodra het project met steekproefcode met succes is gecreeerd, zal Manage Git als verbinding van de heldenkaart in de pagina van het Overzicht verschijnen.

### Releasedatum {#release-date-cm-april}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.4.0 is 8 april 2021.

### Wat is er nieuw?{#what-is-new-april}

* UI werkt aan de Add en Edit de werkschema&#39;s van het Programma om het intuïtiever te maken.

* Een gebruiker met vereiste toestemmingen kan het commerciële eindpunt via UI nu voorleggen.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie `2021.03.5104.20210328T185548Z` of hoger.

* De **Manage knoop van Git** wordt getoond op de kaart van Pijpleidingen zelfs wanneer geen pijpleidingen zijn gevormd.

* De versie van het AEM projectarchetype dat door de Manager van de Wolk wordt gebruikt is bijgewerkt aan versie 27.

* Projecten in de Adobe I/O Developer Console die door Cloud Manager zijn gemaakt, kunnen niet langer per ongeluk worden bewerkt of verwijderd.

* Wanneer een gebruiker een nieuwe omgeving toevoegt, wordt hem meegedeeld dat een nieuwe omgeving niet naar een andere regio kan worden verplaatst.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie 2021.03.5104.20210328T185548Z of hoger.

* Het foutbericht bij het starten van een pijpleiding wanneer een omgeving werd verwijderd, is verduidelijkt.

* OSGi-bundels die door Eclipse-projecten worden geleverd, zijn nu uitgesloten van regel `CQBP-84--dependencies`.

### Opgeloste problemen {#bug-fixes-cm-april}

* Wanneer het uitgeven van de de controlepagina van de Ervaring van een pijpleiding, zal een inputweg die met een schuine streep `( / )` begint niet meer resulteren in het plakken van de stap in wachtende status.

* Wanneer een nieuwe productiepijplijn wordt gecreeerd, als geen de opheffing van de inhoudscontrole door de gebruiker wordt toegevoegd, werd de standaardhomepage niet gecontroleerd.

* De kwesties voor `CloudServiceIncompatibleWorkflowProcess` hadden de onjuiste strengheid in het downloadbare dossier van de uitgave CSV.

* De `Runmode` controle produceerde valse positieven op niet omslagknopen.

## De tool Content Transfer {#content-transfer-tool}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.4.0 is 11 mei 2021.

### Wat is er nieuw?{#what-is-new-ctt-may}

* Met deze versie van het gereedschap Inhoud overbrengen maakt u tekstuitvoeringen voor elementen die naar de Cloud Service worden gemigreerd. Tekstuitvoeringen zijn vereist voor ondersteuning van het zoeken naar volledige tekst op ingesloten elementen.
* Het maximumaantal migratiesets van Content Transfer Tool dat een gebruiker kan maken, is verhoogd van 4 naar 10.

### Opgeloste problemen {#bug-fixes-ctt-may}

* De veelvoudige insectenmoeilijke situaties verwant met auto-verfrissen eigenschap in het Hulpmiddel van de Overdracht van de Inhoud UI.
* Het hulpmiddel van de Overdracht van de inhoud met `wipe=true` resulteerde in onjuiste tellerindex op het doel. Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.12 is 12 april 2021.

### Opgeloste problemen {#bug-fixes-bpa-april}

* Er zijn dubbele rijen aangetroffen in het BPA-rapport. Dit is opgelost.
* BPA UI op AEM versie 6.4.2 werpt een fout JS die de Generate knoop van het Rapport onbruikbaar maakte. Dit is opgelost

