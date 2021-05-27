---
title: Release-aantekeningen voor 2021.4.0-release van [!DNL Adobe Experience Manager] als Cloud Service.
description: Release-aantekeningen voor 2021.4.0-release van [!DNL Adobe Experience Manager] als Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: aeee895e4a4b959125d08091619988d0ffa09ace
workflow-type: tm+mt
source-wordcount: '1475'
ht-degree: 0%

---


# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] als een Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] als Cloud Service weergegeven.

>[!NOTE]
>Vanuit deze locatie kunt u navigeren om notities van eerdere versies weer te geven. bijvoorbeeld voor die in 2020, 2021 enzovoort.

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

* [!DNL Experience Manager] één elementdownload niet archiveert op de plaats waar het oorspronkelijke bestand is gedownload. Deze verbetering maakt snellere downloads mogelijk.

* Wanneer een element wordt gedownload via de optie voor het delen van koppelingen, kunt u nu kiezen of u de uitvoeringen wilt downloaden of niet. Eerder werden alle elementuitvoeringen gedownload.

* Beheerders kunnen [!DNL Experience Manager] zodanig configureren dat de bron van elementen wordt verwijderd nadat ze een pakket met elementen hebben gemaakt. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Wanneer het uitvoeren van een gezondheidscontrole om activa in bulk in te voeren, verstrekt de Experience Manager nu meer informatieredenen voor mislukkingen. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Bij het importeren van elementen met het gereedschap voor bulkimport hebben beheerders nu de optie om de bronbestanden te verwijderen nadat het importeren is voltooid. Zie [bulkopname van elementen](/help/assets/add-assets.md#asset-bulk-ingestor).

* Wanneer het uitgeven van een meta-gegevensschema, staat een nieuw gebied van de selecteur van de wortelweg beheerders toe om de selectie snel en gemakkelijk te maken, daardoor verminderend de configuratietijd.

* Metagegevens van vele elementen kunnen bulksgewijs worden geïmporteerd met behulp van een CSV-bestand en kunnen worden geëxporteerd naar een CSV-bestand. De standaarddatumnotatie is nu `yyyy-MM-dd'T'HH:mm:ss.SSSXXX`. Gebruikers kunnen een andere indeling gebruiken door de kolomkop bij te werken. Voeg bijvoorbeeld `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` toe als kolomkop in het CSV-bestand in plaats van het woord `Date`.

* Wanneer u elementen bladert in de kolomweergave, geeft een visuele indicator de goedgekeurde of geweigerde status van elk element weer.

* Bij het bladeren door elementen in de kolomweergave wordt een visuele indicator weergegeven voor verlopen elementen.

### Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* Wanneer u probeert meerdere elementen of mappen te verplaatsen, wordt een fout in de console gemeld en wordt de verplaatsingsbewerking niet voltooid. Verplaatsen mislukt als de titel niet kan worden bijgewerkt. (CQ-432/2008)

* Een metagegevensveld kan op basis van een regel worden verborgen, zodat metagegevens niet verplicht zijn wanneer aan een vooraf gedefinieerde voorwaarde wordt voldaan. Dergelijke verborgen metagegevensvelden worden echter als vereiste velden weergegeven. (CQ-4321285)

* Bulk-metagegevens kunnen niet worden geïmporteerd omdat de datumnotatie onjuist is. (CQ-4319/014)

* Wanneer op de pagina Eigenschappen een selectie wordt gemaakt om metagegevens bij te werken, reageert de interface langzaam wanneer het schema veel opties bevat. (CQ-4318538)

* Tijdens het bijwerken en opslaan van de metagegevenswaarde in een tekstveld met één regel, worden de waarden in het vervolgkeuzemenu verwijderd, zelfs als de bewerkingen zijn uitgeschakeld in het vervolgkeuzemenu. (CQ-4317077)

* U kunt ellips gebruiken als een aantekening om elementen te bekijken. Wanneer een kleine ellips wordt gebruikt, overlapt de ellips met het aantal van de annotatie in de drukversie. (CQ-4316792)

## [!DNL Adobe Experience Manager Forms] als  [!DNL Cloud Service] {#forms}

### Nieuw in [!DNL Forms] {#what-is-new-forms}

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

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM beschreven als Cloud Service 2021.4.0.

### Releasedatum {#release-date-cm-april}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.4.0 is 8 april 2021.
De volgende release is gepland voor 6 mei 2021.

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

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.12 is 12 april 2021.

### Opgeloste problemen {#bug-fixes-bpa-april}

* Er zijn dubbele rijen aangetroffen in het BPA-rapport. Dit is opgelost.
* BPA UI op AEM versie 6.4.2 werpt een fout JS die de Generate knoop van het Rapport onbruikbaar maakte. Dit is opgelost

