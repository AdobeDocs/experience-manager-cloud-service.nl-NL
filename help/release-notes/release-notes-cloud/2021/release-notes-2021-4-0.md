---
title: Nota's van de versie voor 2021.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.4.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 775332b5-24ce-430e-97a2-6eeb80877c64
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1545'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Adobe Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>Hier kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [ Recente Updates van de Documentatie ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.4.0 is 6 mei 2021.
De volgende release (2021.5.0) vindt plaats op 27 mei 2021.

## AEM as a Cloud Service Foundation{#aem-as-a-cloud-service-foundation}

### Nieuwe functies {#what-is-new-foundation}

* [ het werkschema van de Boom van de Inhoud van Publish ](/help/operations/replication.md#publish-content-tree-workflow) - een nieuw werkschemamodel en een stap verstrekt verhoogde prestaties wanneer het publiceren van diepe hiërarchieën van inhoud.

## [!DNL Adobe Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#what-is-new-sites}

* GraphQL Endpoints - het is nu mogelijk om de AEM GraphQL API voor afzonderlijke AEM Sites-configuraties in te schakelen en aangepaste GraphQL-eindpunten voor die configuraties te maken met een nieuwe GraphQL Console-interface. Met de gebruikersinterface kunt u ook GraphQL-eindpunten beheren.

* Inhoudsmodellen, verbeterd gegevenstype Datum&amp;tijd - het is nu mogelijk het datum&amp;tijdtype te configureren om alleen datum-, alleen tijd- of datum- en tijdgegevens voor de auteur toe te staan.

* Inhoudsmodellen, uitgebreid gegevenstype Codes - het is nu mogelijk het gegevenstype Codes te configureren om het schrijven van enkele of meerdere tags toe te staan.

* Inhoudsmodellen, nieuw gegevenstype Tijdelijke aanduiding voor tabblad - het nieuwe gegevenstype Tijdelijke aanduiding voor tabblad maakt het mogelijk gegevenstypen te groeperen in secties die worden gerenderd onder tabbladen in de inhoudsfragmenteditor.

### Opgeloste problemen in [!DNL Sites] {#bug-fixes-sites}

* Inhoudsfragmenten: het verplaatsen van inhoudsfragmenten of -mappen werkt nu geneste verwijzingen in het fragment bij (CQ-4320815)

* GraphQL - Aanhoudende vragen ondersteunen nu door de gebruiker gedefinieerde eindpunten die specifiek zijn voor AEM Sites-configuraties (CQ-4315928)

## [!DNL Adobe Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#what-is-new-assets}

* [!DNL Experience Manager] archiveert geen enkele elementdownloads waar het oorspronkelijke bestand is gedownload. Deze verbetering maakt snellere downloads mogelijk.

* Wanneer een element wordt gedownload via de optie voor het delen van koppelingen, kunt u de uitvoeringen nu downloaden of niet downloaden. Eerder werden alle elementuitvoeringen gedownload.

* Beheerders kunnen [!DNL Experience Manager] zo configureren dat de bron van elementen wordt verwijderd nadat ze elementen in bulk hebben opgenomen. Zie [ bulkactiva opnemen ](/help/assets/add-assets.md#asset-bulk-ingestor).

* Wanneer het uitvoeren van een gezondheidscontrole om activa in bulk in te voeren, verstrekt de Experience Manager nu meer informatieredenen voor mislukkingen. Zie [ bulkactiva opnemen ](/help/assets/add-assets.md#asset-bulk-ingestor).

* Bij het importeren van elementen met het gereedschap voor bulkimport hebben beheerders nu de optie om de bronbestanden te verwijderen nadat het importeren is voltooid. Zie [ bulkactiva opnemen ](/help/assets/add-assets.md#asset-bulk-ingestor).

* Wanneer het uitgeven van een meta-gegevensschema, staat een nieuw gebied van de selecteur van de wortelweg beheerders toe om de selectie snel en gemakkelijk te maken, daardoor verminderend de configuratietijd.

* Bij het bewerken van een metagegevensschema wordt een gegevenstype toegevoegd dat een tekstgebied met vrije vorm biedt in de metagegevenseditor. Gebruikers kunnen dit tekstgebied gebruiken om vrije tekst in te voeren als metagegevens van een element. Zie [ redacteur van het meta-gegevensschema ](/help/assets/metadata-schemas.md).

* Metagegevens van vele elementen kunnen in bulk worden geïmporteerd met behulp van een CSV-bestand en kunnen worden geëxporteerd naar een CSV-bestand. De standaarddatumnotatie is nu `yyyy-MM-dd'T'HH:mm:ss.SSSXXX` . Gebruikers kunnen een andere indeling gebruiken door de kolomkop bij te werken. Voeg bijvoorbeeld `Date: DateFormat: yyyy-MM-dd'T'HH:mm:ssXXX` toe als kolomkop in het CSV-bestand in plaats van het woord `Date` .

* Wanneer u elementen bladert in de kolomweergave, geeft een visuele indicator de goedgekeurde of geweigerde status van elk element weer.

* Bij het bladeren door elementen in de kolomweergave wordt een visuele indicator weergegeven voor verlopen elementen.

### Opgeloste problemen in [!DNL Assets] {#bug-fixes-assets}

* Wanneer u probeert meerdere elementen of mappen te verplaatsen, wordt een fout in de console gemeld en wordt de verplaatsingsbewerking niet voltooid. Verplaatsen mislukt als de titel niet kan worden bijgewerkt. (CQ-432/2008)

* Een metagegevensveld kan op basis van een regel worden verborgen, zodat metagegevens niet verplicht zijn wanneer aan een vooraf gedefinieerde voorwaarde wordt voldaan. Dergelijke verborgen metagegevensvelden worden echter als vereiste velden weergegeven. (CQ-4321285)

* Bulk-metagegevens kunnen niet worden geïmporteerd omdat de datumnotatie onjuist is. (CQ-4319/014)

* Wanneer op de pagina Eigenschappen een selectie wordt gemaakt om metagegevens bij te werken, reageert de interface langzaam wanneer het schema veel opties bevat. (CQ-4318538)

* Tijdens het bijwerken en opslaan van de metagegevenswaarde in een tekstveld met één regel worden de waarden in het vervolgkeuzemenu verwijderd, zelfs als de bewerkingen zijn uitgeschakeld in het vervolgkeuzemenu. (CQ-4317077)

* U kunt ellips gebruiken als een aantekening om elementen te bekijken. Wanneer een kleine ellips wordt gebruikt, overlapt de ellips met het aantal van de annotatie in de drukversie. (CQ-4316792)

* De optie Snel publiceren wordt niet weergegeven wanneer een element in de zoekresultaten wordt geselecteerd nadat ernaar is gezocht. (CQ-4317748)

## [!DNL Adobe Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Identiteitsauthentificatiemethode van identiteitskaart van de Overheid van het Gebruik in Adobe Sign toegelaten Aangepaste Forms**

  Met behulp van geavanceerde computerleeralgoritmen kunnen bedrijven over de hele wereld dankzij het Adobe Sign-proces voor overheidsidentiteitskaart een kwalitatief hoogstaande verificatie van de identiteit van hun ontvanger krijgen. Nu kunt u de methode voor identiteitsverificatie van overheidsidentiteiten gebruiken in met Adobe Sign ingeschakelde Adaptive Forms.

  Identiteitskaart van de overheid is een methode van de identiteitsauthentificatie van de premie die de ontvanger opdraagt [ het beeld van een door de overheid uitgegeven identiteitsdocument (rijbewijs, nationale identiteitskaart, paspoort) ](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html) te uploaden, en dan dat document te evalueren om het authentiek te verzekeren.

* **Steun om in-vorm het ondertekenen ervaring voor asynchrone adaptieve vormverzendingen te gebruiken**

  U kunt de ondertekeningservaring in formulieren nu gebruiken voor asynchrone, adaptieve verzending van formulieren. U kunt ook een adaptief formulier insluiten in een [!DNL Experience Manager Sites] -pagina en de ondertekeningservaring in formulieren gebruiken voor het verzenden van aangepaste formulieren.

* **Steun om een variabele te gebruiken om een gehechtheid te specificeren terwijl het prepopuleren van een AanpassingsVorm voor een Assign stap van de Taak**

  Terwijl u een adaptief formulier vooraf invult voor een toewijzingsstap, kunt u nu een variabele van het documenttype gebruiken om een invoerbijlage te selecteren voor het adaptieve formulier.

* **Steun om de letterlijke optie te gebruiken om waarde voor een JSON type variabele** te plaatsen

  U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

* **de lokale ontwikkelomgeving van het Gebruik om Document van Verslag tot stand te brengen (DoR)**

  U kunt een XDP als Document van het malplaatje van het Verslag op de instanties van de Cloud Service en as a Cloud Service SDK van AEM Forms (Lokale ontwikkelomgeving) gebruiken. Eerder was de ondersteuning beperkt tot alleen Cloud Servicen.

### Opgeloste problemen in [!DNL Forms] {#bug-fixes-forms}

* Wanneer een Adaptief formulier dat is geconfigureerd om Document of Record niet te genereren, wordt verzonden naar een AEM Workflow die is geconfigureerd om Document of Record te genereren, wordt geen foutbericht weergegeven en kan de taak niet worden verzonden.

### Overige updates {#misc-2021-04-0-forms}

* De service genereert nu live miniaturen voor XDP-, Dynamic PDF- en Schema-bestanden, zodat inhoud gemakkelijker herkend kan worden.
* Voeg de mogelijkheid toe om een PDF-bestand naar een map te verplaatsen die in de gebruikersinterface van AEM Forms is geplaatst.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Nieuwe functies {#what-is-new-commerce}

* Steun voor categorie UID - dit ontgrendelt derde handelsintegraties voor systemen die Koorden voor categorie ids gebruiken

* AEM extensie voor PWA Studio incl. voorbeeld-integratie

* Nieuwe CIF kerncomponent voor navigatie die de WCM-kerncomponent voor navigatie uitbreidt

* Visuele indicator voor gefaseerde catalogusgegevens in AEM storefront

* Het eindpunt van Commerce is nu configureerbaar via de gebruikersinterface van Cloud Manager

### Opgeloste problemen {#bug-fixes-commerce}

* Het veld Hoofdcategorie is niet weergegeven op het tabblad Handel in de pagina-eigenschappen van categoriepagina&#39;s

## Cloud Manager {#cloud-manager}

In dit gedeelte worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.4.0 beschreven.

### Releasedatum {#release-date-cm-april}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.4.0 is 8 april 2021.
De volgende release is gepland voor 6 mei 2021.

### Wat is er nieuw? {#what-is-new-april}

* UI werkt aan de Add en Edit de werkschema&#39;s van het Programma om het intuïtiever te maken.

* Een gebruiker met vereiste toestemmingen kan het commerciële eindpunt via UI nu voorleggen.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie `2021.03.5104.20210328T185548Z` of hoger.

* De **beheert knoop van het Git** wordt getoond op de kaart van Pijpleidingen zelfs wanneer geen pijpleidingen zijn gevormd.

* De versie van het AEM projectarchetype dat door Cloud Manager wordt gebruikt is bijgewerkt aan versie 27.

* Projecten in de Adobe I/O Developer Console die door Cloud Manager zijn gemaakt, kunnen niet langer onbedoeld worden bewerkt of verwijderd.

* Wanneer een gebruiker een nieuwe omgeving toevoegt, krijgt de gebruiker te horen dat een omgeving na het maken ervan niet naar een ander gebied kan worden verplaatst.

* De variabelen van het milieu kunnen nu aan de specifieke dienst, of auteur of publiceren worden onderworpen. Vereist AEM versie 2021.03.5104.20210328T185548Z of hoger.

* Het foutbericht bij het starten van een pijpleiding wanneer een omgeving werd verwijderd, is verduidelijkt.

* OSGi-bundels die door Eclipse-projecten worden geleverd, zijn nu uitgesloten van regel `CQBP-84--dependencies` .

### Opgeloste problemen {#bug-fixes-cm-april}

* Wanneer u de pagina Experience audit van een pijplijn bewerkt, zal een invoerpad dat begint met een schuine streep `( / )` er niet langer toe leiden dat de stap vastloopt in de status In behandeling.

* Wanneer een nieuwe productiepijplijn wordt gecreeerd, als geen de opheffing van de inhoudscontrole door de gebruiker wordt toegevoegd, werd de standaardhomepage niet gecontroleerd.

* Problemen voor `CloudServiceIncompatibleWorkflowProcess` hadden een onjuiste ernst in het CSV-bestand dat kan worden gedownload.

* De `Runmode` -controle gaf false positieven op knooppunten die geen map zijn.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.12 is 12 april 2021.

### Opgeloste problemen {#bug-fixes-bpa-april}

* Er zijn dubbele rijen aangetroffen in het BPA-rapport. Dit is opgelost.
* BPA UI op AEM versie 6.4.2 werpt een fout JS die de Generate knoop van het Rapport onbruikbaar maakte. Dit is opgelost
