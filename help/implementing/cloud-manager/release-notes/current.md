---
title: Opmerkingen bij de release Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2024.6.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
role: Admin
source-git-commit: 958d8fb3526bafeb5a3be9828bddfa3330c05fec
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2024.6.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2024.6.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2024.6.0 in AEM as a Cloud Service is 6 juni 2024. De volgende release is gepland voor 11 juli 2024.

## Wat is er nieuw? {#what-is-new}

* U kunt nu [gebruik uw eigen GitHub-repositories](/help/implementing/cloud-manager/managing-code/private-repositories.md) als bronnen voor zowel volledig-stapelpijpleidingen als frontpijpleidingen.
   * Bovendien kunt u uit bewaarplaatsen GitHub met voordeel halen [git-submodules;](/help/implementing/cloud-manager/managing-code/git-submodules.md) voorzien u van verbeterde controle over de auto-geproduceerde pijpleidingen die voor de bevestiging van het trekkingsverzoek worden gebruikt en het toestaan van u om gedrag voor cruciale metriek tijdens de fase van het codescannen te bepalen.
   * [U kunt ook](/help/implementing/cloud-manager/managing-code/github-check-config.md) om de rapportgeschiedenis op GitHub te bewaren, noem de pijpleiding, en plaats pijpleidingsvariabelen om uw behoeften aan te passen.
* [Self-service inhoud herstellen](/help/operations/restore.md) biedt back-upherstel gedurende maximaal zeven dagen en functies:
   * Point-in-time back-upherstel voor de voorgaande 24 uur
   * Herstel van vaste tijd tot zeven dagen
* [Nieuwe OakPal-regels](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-ui-content-package) zijn toegevoegd aan de kwaliteitscontrole van Cloud Manager Code.
   * Elke nieuwe regel die vanaf juni 2024 wordt toegevoegd, is een onverbrekelijke verandering.
   * U wordt aangespoord deze problemen zo snel mogelijk aan te pakken, aangezien deze nieuwe regels ertoe zullen leiden dat pijpleidingen mislukken vanaf de release Cloud Manager August 2024.

## Programma voor vroegtijdige adoptie {#early-adoption}

Een kans om een aantal van de komende eigenschappen te testen, maakt deel uit van het programma van de Adobe voor vroegtijdige goedkeuring.

### Ondersteuning voor Edge Delivery Services in Cloud Manager {#edge-delivery-services}

Als u Edge Delivery Services met licentie hebt als onderdeel van Adobe Experience Manager Sites, [u kunt nu rechtstreeks in Cloud Manager aan boord van uw site gaan met Edge Delivery Services](/help/implementing/cloud-manager/edge-delivery-services.md) en woon met behulp van een geleide, zelfbediening ervaring.

Dit maakt een verenigde ervaring voor al uw AEM eigenschappen mogelijk, die consistentie met alle kritieke werkschema&#39;s met inbegrip van het beheer van domeinnamen, SSL certificaatbeheer, en afbeeldingen CDN verzekeren.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-cmedgedelsvs-program-adopter@adobe.com` van het e-mailadres dat aan uw Adobe ID is gekoppeld.

### DV-certificaten (Domain Validated)

Met Cloud Manager kunt u nu [De zelfbediening produceert en beheert domein bevestigde (DV) SSL certificaten.](/help/implementing/cloud-manager/managing-ssl-certifications/domain-validated-certificates.md) Dit biedt u de snelste, eenvoudigste en voordeligste oplossing om een veilige website voor uw online bedrijf te maken.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `Grp-aemcs-dv-dert-adopter@adobe.com` van het e-mailadres dat aan uw Adobe ID is gekoppeld.

<!-- RICK: REMOVED THIS SECTION AS PER EMAIL REQUEST TO DL-AEM-DOCS FROM SHWETA DUA, WEDNESDAY, JUNE 12, 2024 ### Client-Side Collection via Real Use Monitoring (RUM) {#rum}

You can leverage the [Real Use Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) to enable client-side collection for AEM as a Cloud Service.

Real Use Monitoring (RUM) Data Service offers a more precise reflection of user interactions, ensuring a reliable measure of website engagement. It is a great opportunity to gain advanced insights into your page performance. This is beneficial for customers who use either Adobe-managed CDN or non-Adobe managed CDN. For customers using a non-Adobe managed CDN, automated traffic reporting can now be enabled for them, thus removing the need to share any traffic report with Adobe.

If you are interested in testing this new feature and sharing your feedback, please send an email to `aemcs-rum-adopter@adobe.com` from the email address associated with your Adobe ID. Please include the domain name for production, stage, and dev environments in your email.  Availability of the early adopter program of this feature is limited. -->

### Experience Audit Dashboard {#experience-audit-dashboard}

[Cloud Manager Experience Audit-dashboard](/help/implementing/cloud-manager/experience-audit-dashboard.md) bevat een trendweergave van de prestatiesscores van uw pagina, samen met inzichten en aanbevelingen om u te helpen deze te verbeteren. Experience Audit is opgenomen als een stap in de productiepijplijn van Cloud Manager.

Het dashboard gebruikt Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar, of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Om aan de slag te gaan, stuurt u een e-mail naar `aem-lighthouse-pilot@adobe.com` van uw e-mail die aan uw Adobe ID is gekoppeld.
