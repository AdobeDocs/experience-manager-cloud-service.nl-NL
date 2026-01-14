---
title: Nota's van de versie voor 2021.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: ab584923-5f06-4b54-941b-e00bc1158b81
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=nl-NL) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2021.10.0) is 4 november 2021.
De volgende release (2021.11.0) is op 2 december 2021.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; video van het Overzicht van de Versie van 0&rbrace; Oktober 2021 &lbrace;voor een samenvatting van de toegevoegde eigenschappen.](https://video.tv.adobe.com/v/338253)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in [!DNL Sites] {#sites-features}

* Inhoudsfragmentmodellen worden nu automatisch ingesteld op de status Alleen-lezen als ze eenmaal zijn gepubliceerd. Zo voorkomt u dat live API-query&#39;s per ongeluk worden afgebroken als een bewerkt model opnieuw wordt gepubliceerd. Gebruikers krijgen een waarschuwing te zien wanneer ze proberen een gepubliceerd model te bewerken. Bewerken is mogelijk bij het accepteren van de waarschuwing.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] biedt nu ondersteuning voor het automatisch genereren van teksttranscripties vanaf de ondersteunde audio- en video-elementen via een ingebouwde connector naar [!DNL Azure Media Services] . De [&#x200B; gesteunde dossiertypes &#x200B;](/help/assets/file-format-support.md#audio-video-transcription-formats) worden automatisch getranscripeerd en de tekst wordt opgeslagen in formaat WebVTT. De WebVTT-bijschriften worden gebruikt voor effectievere zoekacties, ondertiteling of vertaling. Bovendien verbetert de functie de toegankelijkheid, de ontdekkingsmogelijkheden en de lokalisatie van de middelen.

### Nieuwe functie in het [!DNL Assets] prereleasekanaal {#assets-prerelease-features}

* [!DNL Dynamic Media] Smart Crop and Swatch van afbeeldingen wordt nu aangedreven door de nieuwste AI-services, die verbeterde uitsnijdingen en stalen genereren. Er is ook een verbetering gestart om verschillende uitsnijdinhoud te genereren, voor dezelfde hoogte-breedteverhouding maar voor verschillende resoluties. Bovendien blijven eventuele handmatige bewerkingen behouden bij het opwerken als de breedte en hoogte in het afbeeldingsprofiel niet worden gewijzigd.

* Slimme tags worden automatisch toegepast op de elementen met behulp van asset-microservices in plaats van Smart Content Services. Het onderliggende model wordt bijgewerkt om de coderingsresultaten te verbeteren en afwijking te verminderen. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics voor Aanpassings Forms**: U kunt gedrag van zowel het programma geopende als niet het programma geopende (Anoniem) aan als Adobe Analytics voor Aangepaste Forms nu vangen en volgen om gebruikersinzichten te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms-oct-2021}

* **externaliseer de gegevens van het Werkschema van AEM voor veilige verwerking**: U kunt de gegevens van de Werkschema&#39;s van AEM in-proces (de gegevens van de Variabelen van het Werkschema van AEM) opslaan die Gevoelige Persoonlijke Gegevens (SPD) elementen in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in de gegevensopslagruimte van AEM en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Beta-functies van [!DNL Forms]  {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [&#x200B; Communicatie APIs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) hulp u een malplaatje en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* De invoegtoepassing CIF ondersteunt de nieuwste Commerce v2.4.3 met nieuwe GraphQL API&#39;s en schema&#39;s

* Auteurs kunnen koppelingen naar product- en cataloguspagina&#39;s in tekstvelden toevoegen met de RTE (RTE). Er is een CIF-pictogram toegevoegd aan de RTE-werkbalk waarmee de kiezers snel het product of de categorie kunnen zoeken en selecteren zonder de context te verlaten.

* Bestaande pop-up winkelwagentje en afhandeling zijn vervangen door speciale AEM-winkelwagentje en afhandelingspagina&#39;s. De componenten op deze pagina&#39;s worden samengesteld met behulp van uitbreidbare Peregrine-onderdelen van Adobe Commerce

* Met de Commerce-backend kunnen verkopers bepaalde productcataloguscategorieën in de navigatie verbergen. De CIF Navigation Core Component respecteert de Commentaar configuratie &quot;omvat in menu&quot;om categorieën in navigatie te tonen/te verbergen

* AEM Storefront Venia retourneert de HTTP 404-fout als de categorie of productpagina niet wordt gevonden

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.10.0 beschreven.

### Releasedatum {#release-date-cm-nov}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 9 december 2021.

### Wat is er nieuw? {#what-is-new-cm-nov}

* De gebruikers kunnen nieuwe pijpleidingen van het Eind van de Voorzijde nu gebruiken om vooreind code op een versnelde manier uitsluitend op te stellen. Zie [&#x200B; Cloud Manager Voorste Pijpleidingen van het Eind &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) om meer te leren.

  >[!IMPORTANT]
  >U moet op AEM versie `2021.10.5933.20211012T154732Z` zijn om nieuwe Front End pijpleidingen te gebruiken.

* De duur van de pijpleiding van de Kwaliteit van de code wordt beduidend verminderd door de codeanalyse op een efficiëntere manier uit te voeren zonder de behoefte om een volledig beeld van AEM te bouwen. Deze verandering zal geleidelijk plaatsvinden in de weken na de release.

* De Vastleggingsidentiteitskaart van het Git zal nu in de details van de pijpleidingsuitvoering worden getoond die het gemakkelijker maken om de code te volgen die werd gebouwd.

* Het programma wordt nu gemaakt via openbaar toegankelijke API.

* Environment Creation is nu beschikbaar via openbare API.

* De `x-request-id` antwoordkopbal is nu zichtbaar in API Playground op [&#x200B; www.adobe.io &#x200B;](https://www.adobe.io/). Deze kopbal is nuttig wanneer het voorleggen van de kwesties van de klantenzorg voor het oplossen van problemen.

* Als gebruiker zie ik een pijplijnkaart met nulpijpleidingen die mij van de juiste begeleiding voorziet.

* Een nieuwe pagina van de Activiteit is nu beschikbaar waar de activiteiten zoals pijpleiding en codeuitvoering samen met hun bijbehorende details kunnen worden bekeken. In de loop der tijd zullen de activiteiten die op deze pagina worden vermeld, in het toepassingsgebied worden uitgebreid, samen met de verstrekte gegevens.

* Er is nu een nieuwe pagina met pijplijnen beschikbaar met een statuspop-up, zodat u de samenvatting van de details eenvoudig kunt bekijken. De uitvoeringen van de pijpleiding kunnen samen met hun bijbehorende details worden bekeken.

* De Edit Pijpleiding API steunt nu het veranderen van het milieu dat in de plaatsingsfasen wordt gebruikt.

* Voor grote pakketten is een optimalisatie in het OakPal-scanproces geïntroduceerd.

* Het CSV-bestand voor kwaliteitsafgifte bevat nu de tijdstempel voor elke kwaliteitsuitgave.

### Opgeloste problemen {#bug-fixes-nov}

* Bepaalde unorthodox bouwt configuraties resulteerde in onnodige dossiers die in het geheime voorgeheugen van Maven van de pijpleiding worden opgeslagen die in vreemde netwerk I/O resulteerde toen het beginnen en het tegenhouden van de bouwstijlcontainer.

* De PATCH API van de pijpleiding ontbreekt als de plaatsingsfase niet bestaat.

* De kwaliteitsregel `ClientlibProxyResourceCheck` gaf false positieve problemen wanneer er clientbibliotheken waren met algemene basispaden.

* Foutbericht wanneer het maximale aantal opslagplaatsen is bereikt, geeft geen reden voor de fout aan.

* In zeldzame gevallen faalden de pijpleidingen vanwege een onjuiste herbehandeling van bepaalde responscodes.


## Releasedatum {#release-date-cm-oct}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.10.0 is 14 oktober 2021.

### Wat is er nieuw? {#what-is-new-cm-oct}

* In voorbereiding op sommige aanstaande veranderingen, zullen de bestaande plaatsingspijpleidingen nu van verwijzingen worden voorzien en geëtiketteerd in het gebruikersinterface als **Volledige 1&rbrace; pijpleidingen van de Stapel &lbrace;.**

* De kaart van de pijpleiding is verfrist om één enkel, geïntegreerd gezicht te tonen dat zowel productie als niet productiepijpleidingen toont, en de gebruiker kan Looppas/pauze direct selecteren/hervat van het actiemenu verbonden aan elke pijpleiding.

* Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via UI nu schrappen.

* De ervaring met toevoegen en bewerken van pijpleidingen is vernieuwd en gebruikt nu vertrouwde, moderne modellen.

* De gebruikers van Cloud Manager kunnen nu voorleggen terugkoppelt direct van het gebruikersinterface via de **Terugkoppeling** knoop op bovenkant recht van de het landen pagina.

* SLA Graphs kunnen nu worden gedownload vanuit de Cloud Manager-gebruikersinterface.

* De kwaliteit van de code en de niet-productiepijpleiding zullen nu een efficiënter oppervlakkig klonen proces tijdens de bouwstijlstap gebruiken, die tot een snellere bouwtijd voor klanten met bijzonder grote git bewaarplaatsen leidt.

* Voeg IP de tovenaar van de Lijst van gewenste personen nu toe zal de gebruiker informeren als maximum toegestaan aantal IP Lijsten van gewenste personen is bereikt.

* De Cloud Manager API-documentatie bevat nu een interactieve afspeelruimte waarmee aangemelde gebruikers vanuit hun browser kunnen experimenteren met de API. Zie [&#x200B; de Playground van Cloud Manager API &#x200B;](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) voor meer details.

* De knopinfo op de programmakaart is beschrijfbaarder als een selectieoptie onder &#39;Navigeren naar&#39; is uitgeschakeld. Het toont nu &quot;een productiemilieu bestaat niet.&quot;

### Opgeloste problemen {#bug-fixes-cm-oct}

* In zeldzame situaties, wanneer een personeel van Adobe de omgeving van een klant zou herstellen, werd het herstel als volledig beschouwd alvorens het milieu volledig operationeel was.

* Bepaalde interne verzoeken die tijdens het creëren van het milieu werden gedaan, werden niet opnieuw beproefd.

* Als de implementatie is mislukt na de verificatie van de domeinnaam, is het foutbericht gecorrigeerd en is de klant gevraagd contact op te nemen met zijn Adobe-vertegenwoordiger.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.20 is 5 oktober 2021.

### Wat is er nieuw? {#what-is-new}

* Mogelijkheid om de lengte van knoopnamen te detecteren en te rapporteren.

* Mogelijkheid om de totale indexgrootte op te sporen en te rapporteren.

* Mogelijkheid om elementen te detecteren en te rapporteren waarvoor de oorspronkelijke uitvoering ontbreekt.
