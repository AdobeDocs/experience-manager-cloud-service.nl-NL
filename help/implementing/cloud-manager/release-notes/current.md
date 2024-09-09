---
title: Opmerkingen bij de release voor Cloud Manager 2024.9.0 in Adobe Experience Manager as a Cloud Service
description: Meer informatie over de opmerkingen bij de release voor Cloud Manager 2024.9.0 in AEM as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: 610ae004b6da2f7fc0dae2baa613cb363fe9fb00
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2024.9.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release voor Cloud Manager versie 2024.9.0 in AEM as a Cloud Service gepubliceerd.

>[!NOTE]
>
>Zie de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager release 2024.9.0 in AEM as a Cloud Service is 5 september 2024. De volgende release is gepland voor 3 oktober 2024.

## Nieuwe functies {#what-is-new}

* **Dashboard van de Controle van de Ervaring:**

  De Adobe Cloud Manager [ verbeterde Dashboard van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md), aangedreven door de Lighthouse van Google, verstrekt inzicht in de kwaliteit en de prestaties van AEM Sites door kernWeb vitals, SEO, en toegankelijkheidsmetriek te evalueren. Het helpt gebruikers gebieden voor verbetering identificeren door activeerbare aanbevelingen aan te bieden, toelatend teams om gebruikerservaring, pagina ladingstijden, en plaatsnaleving te verbeteren. Dit dashboard vereenvoudigt de controle van kritieke plaatsmetriek en zorgt ervoor dat AEM toepassingen aan hoge prestaties en toegankelijkheidsnormen voldoen.

* **geproduceerde Adobe en beheerde certificaten van de Bevestiging van het Domein:**

  Met Cloud Manager, kunt u nu aan [ zelf-dienst Adobe produceren en beheerde (de Bevestiging van het Domein) SSL certificaten DV ](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) leiden. Deze mogelijkheid biedt u de snelste, eenvoudigste en voordeligste oplossing voor het maken van een veilige website voor uw onlineorganisatie of bedrijf. <!-- CMGR-52403 -->

  >[!NOTE]
  >
  >[ Content Hub ](/help/assets/product-overview.md) klanten zijn gepland om deze eigenschap in fasen als deel van een geleidelijke uitlooptraject te ontvangen.

* **Edge Delivery Services steun in Cloud Manager:**

  Als u een Edge Delivery Services vergunning als deel van AEM Sites hebt, [ kunt u nu aan boord uw plaats met Edge Delivery Services direct door Cloud Manager ](/help/implementing/cloud-manager/edge-delivery-services.md). Met deze functie beschikt u over een begeleide, zelfbediening voor Go Live-ervaring. Het verenigt ook essentiële werkschema&#39;s zoals het beheer van domeinnamen, SSL certificaten, en afbeeldingen CDN over al uw AEM eigenschappen, die consistentie en efficiency verzekeren. <!-- CMGR-49859 -->

  >[!NOTE]
  >
  >[ Content Hub ](/help/assets/product-overview.md) klanten zijn gepland om deze eigenschap in fasen als deel van een geleidelijke uitlooptraject te ontvangen.

* De klanten die bewaarplaatsen GitHub gebruiken hebben nu de capaciteit om de pijpleidingen van Config van de Rij van het Web tot stand te brengen en te gebruiken. <!--( KEEP IN? SP: YES CMGR-59046 and Slack https://cq-dev.slack.com/archives/C07LFP5BZ2L/p1725407057847379 ) -->

<!--
## Early adoption program {#early-adoption}

For a chance to test some upcoming features, be a part of Adobe's early adoption program. -->


## Bugfixes

* Paginering voor de tabel SSL-certificaten werkt nu zoals u had verwacht. <!-- (CMGR-60804 - [UI] Pagination doesn't work for ssl certificates) -->
* De verkeerde artefactversie werd bevorderd wanneer het gebruiken van **bevordert bouwstijl** knoop van een uitvoering. <!-- ( KEEP IN? SP: YES CMGR-59519 and Slack https://cq-dev.slack.com/archives/C07LFPN2R08/p1725408253474129 ) -->

<!-- * Slack message says next release? SP: REMOVE (Leave in for now) SSL Certificates table in Cloud Manager now enables pagination in the user experience. ( https://jira.corp.adobe.com/browse/CMGR-61041 and Slack https://cq-dev.slack.com/archives/C07LFRE9QJU/p1725408553760009 ) --<>
