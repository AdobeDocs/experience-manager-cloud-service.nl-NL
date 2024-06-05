---
title: Opmerkingen bij de release 2021.11.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.11.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 86f8ddd1-af51-4874-9111-0935b5a162c1
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1058'
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

De releasedatum van [!DNL Adobe Experience Manager] als [!DNL Cloud Service] huidige release (2021.11.0) is 16 december 2021.
De volgende release (2022.1.0) vindt plaats op 3 februari 2022.

## Video vrijgeven {#release-video}

Kijk eens naar de [Overzicht release december 2021](https://video.tv.adobe.com/v/339278) video voor een overzicht van de functies die zijn toegevoegd in de release van 2021.11.0 (november 2021).

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#assets-features}

* Dynamic Media Image Smart Crop and Swatch wordt nu aangedreven door de nieuwste Sensei-services, die verbeterde gewassen en stalen genereert. Er is ook een verbetering gestart om verschillende uitsnijdinhoud te genereren, voor dezelfde hoogte-breedteverhouding maar voor verschillende resoluties. Bovendien blijven eventuele handmatige bewerkingen behouden bij het opwerken als de breedte en hoogte in het afbeeldingsprofiel niet worden gewijzigd.

### Nieuwe functies in het dialoogvenster [!DNL Assets] prerelease-kanaal {#assets-prerelease-features}

* [!DNL Dynamic Media] - U kunt nu AEM Dynamic Media-interface gebruiken om Algemene instellingen en Publicatie-instellingen te configureren in plaats van de Dynamic Media Classic-bureaubladtoepassing te doorlopen.

* [!DNL Dynamic Media] ondersteunt nu opname, voorvertoning, afspelen en publiceren voor MXF-video&#39;s. Annotatie en verbluffende video voor MXF-video&#39;s worden nog niet ondersteund.

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt nu de opdracht [bewerkingen bijwerken, verwijderen, hernoemen en verplaatsen](/help/assets/use-assets-across-connected-assets-instances.md) op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* **Externe AEM workflowgegevens voor veilige verwerking**: U kunt in-process AEM Workflows gegevens (AEM gegevens van de Variabelen van het Werkschema) opslaan die de gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in AEM opslagplaats en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) Hiermee kunt u een sjabloon en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   * Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

* **Aangepaste lettertypen voor document van record- en PDF-documenten die zijn gemaakt met communicatie-API&#39;s**: U kunt nu met een merk goedgekeurde lettertypen gebruiken in PDF-documenten die zijn gegenereerd met communicatie-API&#39;s en die aan uw organisatorische vereisten voldoen.

* **Forms Portal**: U kunt [Forms Portal](/help/forms/configure-forms-portal.md) om gepubliceerde adaptieve formulieren op een AEM Sites-pagina weer te geven. Hiermee kan een sitebezoeker alle beschikbare formulieren detecteren. Bovendien kan de bezoeker de portal Formulieren gebruiken om een concept van een adaptief formulier op te slaan en te openen en de versie van de PDF van een ingediend adaptief formulier te bekijken.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Uitgebreide myAccount-componenten die zijn gebaseerd op uitbreidbare Peregrine-componenten van Commerce

![Uitgebreide myAccount-componenten](/help/assets/CIF/extended-myAccount-components.png)

* Auteurs kunnen ad-hoc Commerce Product Recommendations tot stand brengen gebruikend extra advisetypes

* Ondersteuning voor cadeaukaarten in AEM Storefront

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.11.0 beschreven.

### Releasedatum {#release-date-cm-nov}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 9 december 2021.

### Wat is er nieuw? {#what-is-new-cm-nov}

* De gebruikers kunnen nieuwe pijpleidingen van het Eind van de Voorzijde nu gebruiken om vooreind code op een versnelde manier uitsluitend op te stellen. Zie [Cloud Manager frontend Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) voor meer informatie.

  >[!IMPORTANT]
  >U moet AEM versie hebben `2021.10.5933.20211012T154732Z` of hoger voor het gebruik van nieuwe Front End-pijpleidingen.

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

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 1 december 2021.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om de gebruikte versie van ACS-gemeenschappelijk te detecteren en te rapporteren.
* Mogelijkheid om het aantal gebruikers en subgroepen in een groep op te sporen en te rapporteren.
* Mogelijkheid om waarden van knoopeigenschappen in MongoDB te detecteren en te rapporteren die groter zijn dan 16 MB.

### Opgeloste problemen {#bug-fixes-bpa}

* Detection of Foundation components was verfijnd om valse negatieven te verminderen.
* Voor AEM Forms-klanten geldt dat BPA-berichten `EMAIL_PDF_SUBMIT_ACTION` niet beschikbaar zijn op AEM as a Cloud Service is opgelost.
