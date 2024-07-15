---
title: Opmerkingen bij de release voor Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2024.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 6ca376bda8055d62e35e13053ff21f861c12b292
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release voor Cloud Manager versie 2024.6.0 in AEM as a Cloud Service gepubliceerd.

>[!NOTE]
>
>Zie [ deze pagina ](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager release 2024.6.0 in AEM as a Cloud Service is 6 juni 2024. De volgende release is gepland voor 18 juli 2024.

## Wat is er nieuw? {#what-is-new}

* U kunt [ uw eigen bewaarplaatsen GitHub ](/help/implementing/cloud-manager/managing-code/private-repositories.md) nu gebruiken als bronnen voor zowel volledig-stapel als frontend pijpleidingen.
   * Bovendien, kunt u uit bewaarplaatsen GitHub met [ git submodules voordeel halen, ](/help/implementing/cloud-manager/managing-code/git-submodules.md) die u van verbeterde controle over de auto-geproduceerde pijpleidingen voorzien die voor de bevestiging van het trekkingsverzoek worden gebruikt en die u toestaan om gedrag voor cruciale metriek tijdens de fase van het codescanningsprogramma te bepalen.
   * [ u hebt ook de keus ](/help/implementing/cloud-manager/managing-code/github-check-config.md) om de rapportgeschiedenis op GitHub te bewaren, de pijpleiding te noemen, en pijpleidingsvariabelen te plaatsen om uw behoeften aan te passen.
* [ Zelfinhoud herstelt ](/help/operations/restore.md) reserverestauratie voor maximaal zeven dagen en eigenschappen:
   * Point-in-time back-upherstel voor de voorgaande 24 uur
   * Herstel van vaste tijd tot zeven dagen
* [ de Nieuwe regels OakPal ](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package) werden toegevoegd aan het aftasten van de Kwaliteit van de Code van Cloud Manager.
   * Elke nieuwe regel die vanaf juni 2024 wordt toegevoegd, is een onverbrekelijke verandering.
   * U wordt aangespoord deze problemen zo snel mogelijk aan te pakken, aangezien deze nieuwe regels ertoe zullen leiden dat pijpleidingen vanaf de release van Cloud Manager augustus 2024 mislukken.

## Programma voor vroegtijdige adoptie {#early-adoption}

Een kans om een aantal van de komende eigenschappen te testen, maakt deel uit van het programma van de Adobe voor vroegtijdige goedkeuring.

### Ondersteuning voor Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Als u Edge Delivery Services als deel van Adobe Experience Manager Sites in licentie hebt gegeven, [ kunt u nu aan boord van uw plaats met Edge Delivery Services direct in Cloud Manager ](/help/implementing/cloud-manager/edge-delivery-services.md) gaan en het gebruiken van een geleide, zelfbediening ervaring gaan.

Dit maakt een verenigde ervaring voor al uw AEM eigenschappen mogelijk, die consistentie met alle kritieke werkschema&#39;s met inbegrip van het beheer van domeinnamen, SSL certificaatbeheer, en afbeeldingen CDN verzekeren.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `aemcs-cmedgedelsvs-program-adopter@adobe.com` via het e-mailadres dat bij uw Adobe ID hoort.

### DV-certificaten (Domain Validated)

Cloud Manager staat nu u toe [ zelfbediening produceert en beheert domein bevestigde (DV) SSL certificaten.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Dit biedt u de snelste, eenvoudigste en voordeligste oplossing om een veilige website voor uw onlinebedrijf te maken.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `Grp-aemcs-dv-dert-adopter@adobe.com` via het e-mailadres dat bij uw Adobe ID hoort.

<!-- RICK: REMOVED THIS SECTION AS PER EMAIL REQUEST TO DL-AEM-DOCS FROM SHWETA DUA, WEDNESDAY, JUNE 12, 2024 ### Client-Side Collection via Real Use Monitoring (RUM) {#rum}

You can leverage the [Real Use Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) to enable client-side collection for AEM as a Cloud Service.

Real Use Monitoring (RUM) Data Service offers a more precise reflection of user interactions, ensuring a reliable measure of website engagement. It is a great opportunity to gain advanced insights into your page performance. This is beneficial for customers who use either Adobe-managed CDN or non-Adobe managed CDN. For customers using a non-Adobe managed CDN, automated traffic reporting can now be enabled for them, thus removing the need to share any traffic report with Adobe.

If you are interested in testing this new feature and sharing your feedback, please send an email to `aemcs-rum-adopter@adobe.com` from the email address associated with your Adobe ID. Please include the domain name for production, stage, and dev environments in your email.  Availability of the early adopter program of this feature is limited.-->

### Experience Audit Dashboard {#experience-audit-dashboard}

[ het dashboard van de Controle van de Ervaring van Cloud Manager ](/help/implementing/cloud-manager/experience-audit-dashboard.md) omvat een trended mening van uw scores van paginaprestaties samen met inzichten en aanbevelingen om u te helpen hen verbeteren. De Experience Audit is opgenomen als een stap in de Cloud Manager-productiepijplijn.

Het dashboard gebruikt Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar, of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Om aan de slag te gaan, stuurt u een e-mail naar `aem-lighthouse-pilot@adobe.com` vanuit de e-mail die aan uw Adobe ID is gekoppeld.
