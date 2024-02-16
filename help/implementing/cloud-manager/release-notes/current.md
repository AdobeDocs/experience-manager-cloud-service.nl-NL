---
title: Opmerkingen bij de release Cloud Manager 2024.2.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2024.2.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4a41de9da557be562bb2ff5773c7954f76a9acc7
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2024.2.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2024.2.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2024.2.0 in AEM as a Cloud Service is 15 februari 2024. De volgende release is gepland voor 16 maart 2024.

## Wat is er nieuw? {#what-is-new}

* Cloud Manager ondersteunt nu zelfbediening voor [pijplijnvariabelen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) via de interface van Cloud Manager.
* [De voorvertoningsservice](/help/implementing/cloud-manager/manage-environments.md#access-preview-sevice) wordt nu ingeschakeld voor omgevingen die zijn gemaakt voordat de functie voor de voorvertoningsservice werd geïmplementeerd.
* [Aangepaste machtigingen voor Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) Hiermee kunt u aangepaste machtigingsprofielen maken met configureerbare machtigingen om de toegang tot programma&#39;s, pijpleidingen en omgevingen voor gebruikers van Cloud Manager te beperken.
   * Deze functie begon geleidelijk uit te rollen met de [Release december 2023](/help/implementing/cloud-manager/release-notes/2023/2023-12-0.md) en is op 20 februari 2024 voltooid.
* Voor alle nieuwe omgevingen [omgevingsproductprofiel](/help/onboarding/aem-cs-team-product-profiles.md) namen worden gebruikersvriendelijker op basis van een combinatie van profielbeschrijving, omgevingstype, nummer en programmanummer.
* [De ontwikkelomgeving](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) is bijgewerkt naar versie 3.9.4 en JDK-versies jdk-11.0.22 en jdk1.8.0_401.

## Programma voor vroegtijdige adoptie {#early-adoption}

Een kans om een aantal van de komende eigenschappen te testen, maakt deel uit van het programma van de Adobe voor vroegtijdige goedkeuring.

### Clientverzameling via Real User Monitoring (RUM) {#rum}

U kunt de [Real User Monitoring (RUM) Data Service](/help/implementing/cloud-manager/content-requests.md#cliendside-collection) om client-side verzameling voor AEM as a Cloud Service in te schakelen.

Real User Monitoring (RUM) Data Service biedt een nauwkeuriger weergave van gebruikersinteracties, waardoor een betrouwbare maatstaf voor de betrokkenheid van websites wordt geboden. Het is een geweldige kans om geavanceerde inzichten in uw paginaprestaties te krijgen. Dit is voordelig voor klanten die of Adobe-geleide CDN of niet-Adobe beheerde CDN gebruiken. Voor klanten die een niet-Adobe beheerde CDN gebruiken, kan het geautomatiseerde verkeer nu voor hen worden toegelaten, waarbij de behoefte wordt verwijderd om het even welk verkeersrapport met Adobe te delen.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-rum-adopter@adobe.com` van het e-mailadres dat aan uw Adobe ID is gekoppeld. Neem de domeinnaam voor productie-, werkgebied- en ontwikkelomgevingen op in uw e-mail.  De beschikbaarheid van het programma voor vroege adoptie van deze functie is beperkt.

### Breng uw eigen GitHub {#byo-github}

Als u GitHub gebruikt om uw bewaarplaatsen te beheren, [u kunt code binnen uw bewaarplaatsen van GitHub door de Manager van de Wolk nu bevestigen.](/help/implementing/cloud-manager/managing-code/byo-github.md) Door deze integratie is het niet nodig de code consistent te synchroniseren met de opslagplaats van de Adobe en kunt u terugtrekkingsverzoeken verifiëren voordat u ze samenvoegt in de hoofdvertakkingen. Deze eigenschap is exclusief aan openbare GitHub. De steun voor zelf-ontvangen GitHub is niet beschikbaar.

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `Grp-CloudManager_BYOG@adobe.com` van uw e-mailadres dat aan uw Adobe ID is gekoppeld.

### Self-Service inhoud herstellen {#content-restore}

[Een nieuwe functie voor het terugzetten van selfservice-inhoud](/help/operations/restore.md) biedt nu back-upherstel voor maximaal zeven dagen en is beschikbaar voor vroege gebruikers voor evaluatiedoeleinden met:

* Point-in-time back-upherstel voor de voorgaande 24 uur
* Herstel van vaste tijd tot zeven dagen

Als u deze nieuwe functie wilt testen en feedback wilt delen, stuurt u een e-mail naar `aemcs-restorefrombackup-adopter@adobe.com` van uw e-mail die aan uw Adobe ID is gekoppeld.

* Het programma voor vroege adoptie is beperkt tot ontwikkelomgevingen.
* De beschikbaarheid van het programma voor vroege adoptie van deze functie is beperkt.
* Deze functie is bedoeld om per ongeluk verwijderde inhoud te herstellen en is niet bedoeld voor noodherstel.

### Experience Audit Dashboard {#experience-audit-dashboard}

[Cloud Manager Experience Audit-dashboard](/help/implementing/cloud-manager/experience-audit-dashboard.md) bevat een trendweergave van de prestatiesscores van uw pagina, samen met inzichten en aanbevelingen om u te helpen deze te verbeteren. Experience Audit is opgenomen als een stap in de productiepijplijn van Cloud Manager.

Het dashboard gebruikt Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar, of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Om aan de slag te gaan, stuurt u een e-mail naar `aem-lighthouse-pilot@adobe.com` van uw e-mail die aan uw Adobe ID is gekoppeld.

## Opgeloste problemen {#bug-fixes}

* JDK van de bouwstijlcontainers is bijgewerkt aan een versie die oplost [8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
