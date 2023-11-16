---
title: Opmerkingen bij de release 2021.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.10.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: ab584923-5f06-4b54-941b-e00bc1158b81
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van vorige versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.10.0) is 4 november 2021.
De volgende release (2021.11.0) is op 2 december 2021.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release oktober 2021](https://video.tv.adobe.com/v/338253) video voor een overzicht van de toegevoegde functies.

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functie in [!DNL Sites] {#sites-features}

* Inhoudsfragmentmodellen worden nu automatisch ingesteld op de status Alleen-lezen als ze eenmaal zijn gepubliceerd. Zo voorkomt u dat live API-query&#39;s per ongeluk worden afgebroken als een bewerkt model opnieuw wordt gepubliceerd. Gebruikers krijgen een waarschuwing te zien wanneer ze proberen een gepubliceerd model te bewerken. Bewerken is mogelijk bij het accepteren van de waarschuwing.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] ondersteunt nu automatisch genereren van teksttranscripties van de ondersteunde audio- en video-elementen via een ingebouwde connector naar [!DNL Azure Media Services]. De [ondersteunde bestandstypen](/help/assets/file-format-support.md#audio-video-transcription-formats) worden automatisch getranscripeerd en de tekst wordt opgeslagen in formaat WebVTT. De WebVTT-bijschriften worden gebruikt voor effectievere zoekacties, ondertiteling of vertaling. Bovendien verbetert de functie de toegankelijkheid, de ontdekkingsmogelijkheden en de lokalisatie van de middelen.

### Nieuwe functie in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

* [!DNL Dynamic Media] Smart Crop and Swatch van afbeeldingen wordt nu aangedreven door de nieuwste Sensei-services, die verbeterde gewassen en stalen genereert. Er is ook een verbetering gestart om verschillende uitsnijdinhoud te genereren, voor dezelfde hoogte-breedteverhouding maar voor verschillende resoluties. Bovendien blijven eventuele handmatige bewerkingen behouden bij het opwerken als de breedte en hoogte in het afbeeldingsprofiel niet worden gewijzigd.

* Slimme tags worden automatisch toegepast op de elementen met behulp van asset-microservices in plaats van Smart Content Services. Het onderliggende model wordt bijgewerkt om de coderingsresultaten te verbeteren en afwijking te verminderen. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analyses voor Adaptive Forms**: U kunt nu gedrag vastleggen en bijhouden van zowel aangemelde als niet-aangemelde (anonieme) inhoud via Adobe Analytics for Adaptive Forms om inzichten van eindgebruikers te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms-oct-2021}

* **Externe AEM workflowgegevens voor veilige verwerking**: U kunt in-process AEM Workflows gegevens (AEM gegevens van de Variabelen van het Werkschema) opslaan die de gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in AEM opslagplaats en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Bètafuncties van [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u een sjabloon en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* De CIF add-on biedt ondersteuning voor de nieuwste Commerce v2.4.3 met nieuwe GraphQL API&#39;s en schema&#39;s

* Auteurs kunnen koppelingen naar product- en cataloguspagina&#39;s in tekstvelden toevoegen met de RTE (RTE). Er is een CIF pictogram toegevoegd aan de RTE-werkbalk waarmee de kiezers snel het product of de categorie kunnen zoeken en selecteren zonder de context te verlaten.

* Bestaande pop-up winkelwagentje en kassa zijn vervangen door speciale AEM winkelwagentje en afhandelingspagina&#39;s. De componenten op deze pagina&#39;s worden samengesteld met behulp van uitbreidbare Peregrine-onderdelen van Adobe Commerce

* Handelaars kunnen bepaalde categorieën van de productcatalogus in de navigatie verbergen gebruikend de achtergrond van de Handel. De CIF component van de Kern van de Navigatie eerbiedigt de handel achterste configuratie &quot;omvat in menu&quot;om categorieën in navigatie te tonen/te verbergen

* AEM Storefront Venia retourneert de HTTP 404-fout als de categorie of productpagina niet wordt gevonden

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.10.0 beschreven.

### Releasedatum {#release-date-cm-nov}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 9 december 2021.

### Wat is er nieuw? {#what-is-new-cm-nov}

* De gebruikers kunnen nieuwe pijpleidingen van het Eind van de Voorzijde nu gebruiken om vooreind code op een versnelde manier uitsluitend op te stellen. Zie [Cloud Manager frontend Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) voor meer informatie.

  >[!IMPORTANT]
  >U moet AEM versie hebben `2021.10.5933.20211012T154732Z` om nieuwe frontale pijpleidingen te gebruiken.

* De duur van de pijpleiding van de Kwaliteit van de code wordt beduidend verminderd door de codeanalyse op een efficiëntere manier uit te voeren zonder de behoefte om een volledig AEM beeld te bouwen. Deze verandering zal geleidelijk plaatsvinden in de weken na de release.

* De Vastleggingsidentiteitskaart van het Git zal nu in de details van de pijpleidingsuitvoering worden getoond die het gemakkelijker maken om de code te volgen die werd gebouwd.

* Het programma wordt nu gemaakt via openbaar toegankelijke API.

* Environment Creation is nu beschikbaar via openbare API.

* De `x-request-id` responsheader is nu zichtbaar in de API-afspeelruimte op [www.adobe.io](https://www.adobe.io/). Deze kopbal is nuttig wanneer het voorleggen van de kwesties van de klantenzorg voor het oplossen van problemen.

* Als gebruiker zie ik een pijplijnkaart met nulpijpleidingen die mij van de juiste begeleiding voorziet.

* Een nieuwe pagina van de Activiteit is nu beschikbaar waar de activiteiten zoals pijpleiding en codeuitvoering samen met hun bijbehorende details kunnen worden bekeken. In de loop der tijd zullen de activiteiten die op deze pagina worden vermeld, in het toepassingsgebied worden uitgebreid, samen met de verstrekte gegevens.

* Er is nu een nieuwe pagina met pijplijnen beschikbaar met een statuspop-up, zodat u de samenvatting van de details eenvoudig kunt bekijken. De uitvoeringen van de pijpleiding kunnen samen met hun bijbehorende details worden bekeken.

* De Edit Pijpleiding API steunt nu het veranderen van het milieu dat in de plaatsingsfasen wordt gebruikt.

* Voor grote pakketten is een optimalisatie in het OakPal-scanproces geïntroduceerd.

* Het CSV-bestand voor kwaliteitsafgifte bevat nu de tijdstempel voor elke kwaliteitsuitgave.

### Opgeloste problemen {#bug-fixes-nov}

* Bepaalde unorthodox bouwt configuraties resulteerde in onnodige dossiers die in het geheime voorgeheugen van Maven van de pijpleiding worden opgeslagen die in vreemde netwerk I/O resulteerde toen het beginnen en het tegenhouden van de bouwstijlcontainer.

* De PATCH API van de pijpleiding ontbreekt als de plaatsingsfase niet bestaat.

* De `ClientlibProxyResourceCheck` de kwaliteitsregel leverde fout-positieve problemen op wanneer er clientbibliotheken waren met algemene basispaden.

* Foutbericht wanneer het maximale aantal opslagplaatsen is bereikt, geeft geen reden voor de fout aan.

* In zeldzame gevallen faalden de pijpleidingen vanwege een onjuiste herbehandeling van bepaalde responscodes.


## Releasedatum {#release-date-cm-oct}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.10.0 is 14 oktober 2021.

### Wat is er nieuw? {#what-is-new-cm-oct}

* Ter voorbereiding op enkele aanstaande wijzigingen wordt nu in de gebruikersinterface verwezen naar en geëtiketteerd als bestaande implementatiepijplijnen **Volledige stapel** pijpleidingen.

* De kaart van de pijpleiding is verfrist om één enkel, geïntegreerd gezicht te tonen dat zowel productie als niet productiepijpleidingen toont, en de gebruiker kan Looppas/pauze direct selecteren/hervat van het actiemenu verbonden aan elke pijpleiding.

* Een gebruiker in de rol van de Manager van de Plaatsing kan de pijpleiding van de Productie op een zelfbediening manier via UI nu schrappen.

* De ervaring met toevoegen en bewerken van pijpleidingen is vernieuwd en gebruikt nu vertrouwde, moderne modellen.

* Gebruikers van Cloud Manager kunnen nu rechtstreeks vanuit de gebruikersinterface feedback verzenden via de **Feedback** op de rechterbovenhoek van de landingspagina.

* De jaarlijkse SLA-grafieken kunnen nu worden gedownload vanuit de gebruikersinterface van Cloud Manager.

* De kwaliteit van de code en de niet-productiepijpleiding zullen nu een efficiënter oppervlakkig klonen proces tijdens de bouwstijlstap gebruiken, die tot een snellere bouwtijd voor klanten met bijzonder grote git bewaarplaatsen leidt.

* Voeg IP de tovenaar van de Lijst van gewenste personen nu toe zal de gebruiker informeren als maximum toegestaan aantal IP Lijsten van gewenste personen is bereikt.

* De documentatie van de API voor Cloud Manager bevat nu een interactieve speelruimte waarmee aangemelde gebruikers vanuit hun browser kunnen experimenteren met de API. Zie [Afspelen van Cloud Manager-API](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) voor meer informatie .

* De knopinfo op de programmakaart is beschrijfbaarder als een selectieoptie onder &#39;Navigeren naar&#39; is uitgeschakeld. Het toont nu &quot;een productiemilieu bestaat niet.&quot;

### Opgeloste problemen {#bug-fixes-cm-oct}

* In zeldzame situaties, wanneer een personeel van de Adobe het milieu van een klant zou herstellen, werd het herstel als volledig beschouwd alvorens het milieu volledig operationeel was.

* Bepaalde interne verzoeken die tijdens het creëren van het milieu werden gedaan, werden niet opnieuw beproefd.

* Als de plaatsing mislukte fout na de controle van de domeinnaam voorkomt, is het foutenbericht verbeterd om de klant te verzoeken om hun Adobe te contacteren vertegenwoordiger.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.20 is 5 oktober 2021.

### Wat is er nieuw? {#what-is-new}

* Mogelijkheid om de lengte van knoopnamen te detecteren en te rapporteren.

* Mogelijkheid om de totale indexgrootte op te sporen en te rapporteren.

* Mogelijkheid om elementen te detecteren en te rapporteren waarvoor de oorspronkelijke uitvoering ontbreekt.
