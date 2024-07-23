---
title: Opmerkingen bij de release voor Cloud Manager 2024.7.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2024.7.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 12e19fe771c0b70ec471949944141f4d6858cbfd
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager 2024.7.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release voor Cloud Manager versie 2024.7.0 in AEM as a Cloud Service gepubliceerd.

>[!NOTE]
>
>Zie [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2024.7.0 in AEM as a Cloud Service is 18 juli 2024. De volgende release is gepland voor 8 augustus 2024.

## Wat is er nieuw? {#what-is-new}

* De [ productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline) en [ niet-productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline) trekker **op de Veranderingen van het Git** om de pijpleiding op te starten begaat is nu beschikbaar voor [ privé bewaarplaatsen.](/help/implementing/cloud-manager/managing-code/private-repositories.md)
   * Dit zal gefaseerd worden uitgevoerd en medio augustus voltooid zijn.
* Wanneer het toevoegen van een [ Adobe-geleid DV certificaat, ](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) u één enkel certificaat kunt nu toevoegen dat veelvoudige domeinen in plaats van het creëren van een certificaat voor elk domein behandelt.
* De oplossingen die geen [ extra hebben publiceren gebieden ](/help/operations/additional-publish-regions.md) kunnen nu aan een programma worden toegevoegd zolang het programma minstens een oplossing van Plaatsen of van Forms op het van toepassing is.
* De oplossingen die geen [ 99.99% SLA ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#sla) hebben kunnen nu aan een programma worden toegevoegd zolang het programma minstens een oplossing van Plaatsen of van Forms op het van toepassing is.
* Het [ Dashboard van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-dashboard.md) is op een aantal manieren verbeterd.
   * Audits worden nu uitgevoerd tegen `.com` eindpunten via CDN, waarbij de vorige `.net` -benadering wordt vervangen.
      * Deze verandering simuleert echte gebruikerservaring nauwkeuriger en helpt u meer geïnformeerde besluiten over het beheren en optimaliseren van uw website nemen.
   * Er zijn meerdere verbeteringen aangebracht in de gebruikersinterface van de Experience Audit, waaronder:
      * Er is een trendweergave van prestaties, aanbevolen procedures, SEO en toegankelijkheid toegevoegd.
      * De koppeling voor het RAW-rapport in Lighthouse is nu intuïtiever zichtbaar, rechtstreeks in het deelvenster met details voor momentopnamen scannen.
      * De sectie met aanbevelingen voor Lighthouse is uitgebreid.
   * De PWA-waarde is verwijderd in overeenstemming met Lightroom-versie 12.0.0, waardoor deze waarde is verwijderd.
* [ Het AEM Archetype van het Project ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) is bijgewerkt aan [ versie 49.](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49)

## Programma voor vroegtijdige adoptie {#early-adoption}

Een kans om een aantal van de komende eigenschappen te testen, maakt deel uit van het programma van de Adobe voor vroegtijdige goedkeuring.

### Ondersteuning voor Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites in licentie hebt gegeven, [ kunt u nu aan boord van uw plaats met Edge Delivery Services direct in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery-services.md) gaan en het gebruiken van een geleide, zelfbediening ervaring gaan.

Dit maakt een verenigde ervaring voor al uw AEM eigenschappen mogelijk, die consistentie met alle kritieke werkschema&#39;s met inbegrip van het beheer van domeinnamen, SSL certificaatbeheer, en afbeeldingen CDN verzekeren.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `aemcs-cmedgedelsvs-program-adopter@adobe.com` via het e-mailadres dat bij uw Adobe ID hoort.

### DV-certificaten (Domain Validated)

Cloud Manager staat nu u toe [ zelfbediening produceert en beheert domein bevestigde (DV) SSL certificaten.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Dit biedt u de snelste, eenvoudigste en voordeligste oplossing om een veilige website voor uw onlinebedrijf te maken.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `Grp-aemcs-dv-dert-adopter@adobe.com` via het e-mailadres dat bij uw Adobe ID hoort.

### Experience Audit Dashboard {#experience-audit-dashboard}

[ het dashboard van de Controle van de Ervaring van Cloud Manager ](/help/implementing/cloud-manager/experience-audit-dashboard.md) omvat een trended mening van uw scores van paginaprestaties samen met inzichten en aanbevelingen om u te helpen hen verbeteren. De Experience Audit is opgenomen als een stap in de Cloud Manager-productiepijplijn.

Het dashboard gebruikt Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar, of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Om aan de slag te gaan, stuurt u een e-mail naar `aem-lighthouse-pilot@adobe.com` vanuit de e-mail die aan uw Adobe ID is gekoppeld.
