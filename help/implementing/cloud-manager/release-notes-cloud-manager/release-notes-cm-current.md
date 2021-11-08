---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.11.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.11.0
feature: Release Information
exl-id: null
source-git-commit: e8ceeb0eb4fb26553683ced74a2e20628fc2952e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.11.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.11.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.11.0 is 4 november 2021.
De volgende release is gepland voor 9 december 2021.

### Wat is er nieuw? {#what-is-new}

* Gebruikers kunnen nu nieuwe Front End-pijpleidingen gebruiken om front-end code op een versnelde manier uitsluitend te implementeren. Zie [Cloud Manager frontend Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) voor meer informatie.

   >[!IMPORTANT]
   >U moet AEM versie hebben `2021.10.5933.20211012T154732Z` om nieuwe Front End-pijpleidingen te benutten.

* De duur van de pijpleiding van de Kwaliteit van de code wordt beduidend verminderd door de codeanalyse op een efficiëntere manier uit te voeren zonder de behoefte om een volledig AEM beeld te bouwen. Deze verandering zal geleidelijk plaatsvinden in de weken na de release.

* De Vastleggingsidentiteitskaart van het Git zal nu in de details van de pijpleidingsuitvoering worden getoond die het gemakkelijker maken om de code te volgen die werd gebouwd.

* Het programma wordt nu gemaakt via openbaar toegankelijke API.

* Environment Creation is nu beschikbaar via openbare API.

* De `x-request-id` responsheader is nu zichtbaar in de API-afspeelruimte op [www.adobe.io](https://www.adobe.io/). Deze kopbal is nuttig wanneer het voorleggen van de kwesties van de klantenzorg voor het oplossen van problemen.

* Als gebruiker zie ik een pijplijnkaart met nulpijpleidingen die mij de juiste begeleiding biedt.

* Een nieuwe pagina van de Activiteit is nu beschikbaar waar de activiteiten zoals pijpleiding en codeuitvoering samen met hun bijbehorende details kunnen worden bekeken. In de loop der tijd zullen de activiteiten die op deze pagina worden vermeld, in het toepassingsgebied worden uitgebreid, samen met de verstrekte gegevens.

* Er is nu een nieuwe pagina met pijplijnen beschikbaar met een statuspop-up, zodat u de samenvatting van de details eenvoudig kunt bekijken. De uitvoeringen van de pijpleiding kunnen samen met hun bijbehorende details worden bekeken.

* De Edit Pijpleiding API steunt nu het veranderen van het milieu dat in de plaatsingsfasen wordt gebruikt.

* Voor grote pakketten is een optimalisatie in het OakPal-scanproces geïntroduceerd.

* Het CSV-bestand voor kwaliteitsafgifte bevat nu de tijdstempel voor elke kwaliteitsuitgave.

### Opgeloste problemen {#bug-fixes}

* Bepaalde unorthodox bouwt configuraties resulteerde in onnodige dossiers die in het geheime voorgeheugen van Maven van de pijpleiding worden opgeslagen die in vreemde netwerk I/O resulteerde toen het beginnen en het tegenhouden van de bouwstijlcontainer.

* De PATCH API van de pijpleiding ontbreekt als de plaatsingsfase niet bestaat.

* De `ClientlibProxyResourceCheck` de kwaliteitsregel leverde fout-positieve problemen op wanneer er clientbibliotheken waren met algemene basispaden.

* Foutbericht wanneer het maximale aantal opslagplaatsen is bereikt, geeft geen reden voor de fout aan.

* In zeldzame gevallen faalden de pijpleidingen vanwege een onjuiste herbehandeling van bepaalde responscodes.

