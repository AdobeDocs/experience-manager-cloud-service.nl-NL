---
title: Nota's van de versie voor 2021.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 86f8ddd1-af51-4874-9111-0935b5a162c1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1058'
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

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release (2021.11.0) is 16 december 2021.
De volgende release (2022.1.0) vindt plaats op 3 februari 2022.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; December 2021 het Overzicht van de Versie &#x200B;](https://video.tv.adobe.com/v/339278) video voor een samenvatting van de eigenschappen die in de 2021.11.0 (November 2021) versie worden toegevoegd.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Dynamic Media Image Smart Crop and Swatch wordt nu aangedreven door de nieuwste Sensei-services, die verbeterde gewassen en stalen genereert. Er is ook een verbetering gestart om verschillende uitsnijdinhoud te genereren, voor dezelfde hoogte-breedteverhouding maar voor verschillende resoluties. Bovendien blijven eventuele handmatige bewerkingen behouden bij het opwerken als de breedte en hoogte in het afbeeldingsprofiel niet worden gewijzigd.

### Nieuwe functies in het [!DNL Assets] pre-releasekanaal {#assets-prerelease-features}

* [!DNL Dynamic Media] - U kunt nu AEM Dynamic Media-interface gebruiken om Algemene instellingen en Publish Setup te configureren in plaats van de Dynamic Media Classic-bureaubladtoepassing te doorlopen.

* [!DNL Dynamic Media] ondersteunt nu opname, voorvertoning, afspelen en publiceren voor MXF-video&#39;s. Annotatie en verbluffende video voor MXF-video&#39;s worden nog niet ondersteund.

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de [&#x200B; update nu uitvoeren, schrappen, hernoemen, en bewegingsverrichtingen &#x200B;](/help/assets/use-assets-across-connected-assets-instances.md) op de verre activa DAM of de omslagen anders. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **externaliseer AEM gegevens van het Werkschema voor veilige verwerking**: U kunt in-proces AEM gegevens van de Werkschema&#39;s (AEM gegevens van de Variabelen van het Werkschema) opslaan die Gevoelige Persoonlijke Gegevens (SPD) elementen in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in AEM opslagplaats en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [&#x200B; Communicatie APIs &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html?lang=nl-NL) hulp u een malplaatje en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

* **de doopvonten van de Douane voor Document van Verslag en PDF documenten die met Mededelingen APIs** worden gecreeerd: U kunt merk goedgekeurde doopvonten in de documenten van PDF nu gebruiken die Communicatie APIs worden geproduceerd om op uw organisatorische vereisten te richten.

* **Forms Portal**: U kunt [&#x200B; Portaal van Forms &#x200B;](/help/forms/configure-forms-portal.md) gebruiken om van uw gepubliceerde adaptieve vormen op een pagina van AEM Sites een lijst te maken. Hiermee kan een sitebezoeker alle beschikbare formulieren detecteren. Bovendien kan de bezoeker de portal Formulieren gebruiken om een concept van een adaptief formulier op te slaan en te openen en de versie van de PDF van een ingediend adaptief formulier te bekijken.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Uitgebreide myAccount-componenten die zijn gebaseerd op uitbreidbare Peregrine-componenten van Commerce

![&#x200B; Uitgebreide myAccount componenten &#x200B;](/help/assets/CIF/extended-myAccount-components.png)

* Auteurs kunnen ad-hoc Commerce Product Recommendations tot stand brengen gebruikend extra advisetypes

* Ondersteuning voor cadeaukaarten in AEM Storefront

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.11.0 beschreven.

### Releasedatum {#release-date-cm-nov}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 9 december 2021.

### Wat is er nieuw? {#what-is-new-cm-nov}

* De gebruikers kunnen nieuwe pijpleidingen van het Eind van de Voorzijde nu gebruiken om vooreind code op een versnelde manier uitsluitend op te stellen. Zie [&#x200B; Cloud Manager Voorste Pijpleidingen van het Eind &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) om meer te leren.

  >[!IMPORTANT]
  >U moet AEM versie `2021.10.5933.20211012T154732Z` of hoger zijn om nieuwe Front End-pijpleidingen te kunnen gebruiken.

* De duur van de pijpleiding van de Kwaliteit van de code wordt beduidend verminderd door de codeanalyse op een efficiëntere manier uit te voeren zonder de behoefte om een volledig AEM beeld te bouwen. Deze verandering zal geleidelijk plaatsvinden in de weken na de release.

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

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 1 december 2021.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om de gebruikte versie van ACS-gemeenschappelijk te detecteren en te rapporteren.
* Mogelijkheid om het aantal gebruikers en subgroepen in een groep op te sporen en te rapporteren.
* Mogelijkheid om waarden van knoopeigenschappen in MongoDB te detecteren en te rapporteren die groter zijn dan 16 MB.

### Opgeloste problemen {#bug-fixes-bpa}

* Detection of Foundation components was verfijnd om valse negatieven te verminderen.
* Voor AEM Forms-klanten is het BPA-bericht dat `EMAIL_PDF_SUBMIT_ACTION` niet beschikbaar is op AEM as a Cloud Service opgelost.
