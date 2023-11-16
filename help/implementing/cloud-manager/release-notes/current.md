---
title: Opmerkingen bij de release Cloud Manager 2023.11.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.11.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 4e2ea040ec14515525424b42f524601d34786cb8
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.11.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.11.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.11.0 in AEM as a Cloud Service is 14 november 2023. De volgende release is gepland voor 7 december 2023.

## Wat is er nieuw? {#what-is-new}

* Web Application Firewall-DDOS protection (WAF-DDOS) is nu beschikbaar voor aankoop als deel van uw AEM as a Cloud Service rechten en [kan op een zelfbediening manier worden gevormd.](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md)
* Gespecialiseerd [configuratieleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) zijn nu beschikbaar om de regels van de verkeersfilter, met inbegrip van de regels van WAF, binnen notulen te vormen en op te stellen.
* [Bij het kopiëren van inhoud](/help/implementing/developing/tools/content-copy.md) van een hogere omgeving tot een ontwikkelomgeving wordt nu een boodschap weergegeven waarin u wordt aangeraden grote inhoudssets te kopiëren omdat ontwikkelomgevingen beperkt zijn in de capaciteit.
* [De pagina met details over de uitvoering van de pijpleiding](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) zullen nu alle stappen in een pijpleidingsuitvoering tonen met degenen die nog niet grayed zijn begonnen.
* Op beide **[Activiteit](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity)** en **[Pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#pipelines)** pagina&#39;s, is een samenvatting van de pijpleidingsuitvoering nu beschikbaar wanneer het klikken op een pijpleiding met een lopende status.
* Een nieuwe **Duur** is toegevoegd aan de [pagina met details over pijplijn](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details) dit omvat de gemiddelde duur van de pijpleidingstap op basis van de historische trend voor dat programma.
* Op de [pagina voor de uitvoering van pijpleidingen,](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#activity-window) de voltooide stappen geven nu de duur weer.
* Uitvoeringen die [constructieartefacten opnieuw gebruiken](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#build-artifact-reuse) De koppeling naar de uitvoering die deze artefacten aanvankelijk heeft gemaakt, wordt nu weergegeven.
* De optie om te selecteren **Belangrijke metrische fouten** kan nu worden geconfigureerd voor [pijpleidingen van codekwaliteit](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) ook.


## Programma voor vroegtijdige adoptie {#early-adoption}

Maak deel uit van ons programma voor vroegtijdige goedkeuring en heb de kans om een aantal van de komende kenmerken te testen.

### Breng uw eigen GitHub {#byo-github}

Als u GitHub gebruikt om uw bewaarplaatsen te beheren, [u kunt code binnen uw bewaarplaatsen van GitHub door de Manager van de Wolk nu bevestigen.](/help/implementing/cloud-manager/managing-code/byo-github.md) Door deze integratie is het niet nodig de code consistent te synchroniseren met de opslagplaats van de Adobe en kunt u terugtrekkingsverzoeken verifiëren voordat u ze samenvoegt in de hoofdvertakkingen.

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `Grp-CloudManager_BYOG@adobe.com` van uw e-mailadres dat aan uw Adobe ID is gekoppeld.

### Aangepaste machtigingen {#custom-permissions}

[Aangepaste machtigingen voor Cloud Manager](/help/implementing/cloud-manager/custom-permissions.md) Hiermee kunt u nieuwe aangepaste machtigingsprofielen maken met configureerbare machtigingen om de toegang tot programma&#39;s, pijpleidingen en omgevingen voor gebruikers van Cloud Manager te beperken.

Als u interesse hebt in het testen van deze nieuwe functie en het delen van uw feedback, kunt u een e-mail sturen `Grp-CloudManager-custom-permissions@adobe.com` van uw e-mailadres dat aan uw Adobe ID is gekoppeld.

### Self-Service inhoud herstellen {#content-restore}

[Een nieuwe functie voor het terugzetten van selfservice-inhoud](/help/operations/restore.md) biedt nu back-upherstel voor maximaal zeven dagen en is beschikbaar voor vroege gebruikers voor evaluatiedoeleinden met:

* Point-in-time back-upherstel voor de voorgaande 24 uur
* Herstel van vaste tijd tot zeven dagen

Als je deze nieuwe functie wilt testen en je feedback wilt delen, stuur dan een e-mail naar `aemcs-restorefrombackup-adopter@adobe.com` van uw e-mail die aan uw Adobe ID is gekoppeld. Opmerking:

* Het programma voor vroege adoptie is beperkt tot ontwikkelomgevingen.
* De beschikbaarheid van het programma voor vroege adoptie van deze functie is beperkt.
* Deze functie is bedoeld om per ongeluk verwijderde inhoud te herstellen en is niet bedoeld voor noodherstel.

### Experience Audit Dashboard {#experience-audit-dashboard}

[Cloud Manager Experience Audit-dashboard](/help/implementing/cloud-manager/experience-audit-dashboard.md) bevat een trendweergave van de prestatiesscores van uw pagina, samen met inzichten en aanbevelingen om u te helpen deze te verbeteren. Experience Audit is opgenomen als een stap in de productiepijplijn van Cloud Manager.

Het dashboard maakt gebruik van Google Lighthouse, een opensource, geautomatiseerd programma voor het verbeteren van de kwaliteit van uw webapps. U kunt het tegen om het even welke Web-pagina in werking stellen, openbaar of het vereisen van authentificatie. Er zijn audits voor prestaties, toegankelijkheid, progressieve webapps, SEO en meer.

Geïnteresseerd in het testen van het nieuwe dashboard? Stuur een e-mail naar `aem-lighthouse-pilot@adobe.com` via je e-mail die aan je Adobe ID is gekoppeld. We kunnen je aan de slag.

## Bekende problemen {#known-issues}

Er is een bekende bug die voorkomt [configuratieleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md##config-deployment-pipeline) van overschakelen op productie.

Als de **Pauzeren vóór implementatie naar productie** optie wordt vereist voor een config pijpleiding, is het volgende gesuggereerde tijdelijke oplossing tot de insect wordt opgelost.

1. Voer de pijplijn uit.
1. Test de code in de testomgeving.
1. Wanneer het opstellen en de goedkeuring beschikbaar wordt, klik op **Afwijzen**.
1. Bewerk de pijplijn om de **Pauzeren vóór implementatie naar productie** -optie.
1. Voer de pijplijn opnieuw uit. Het zal opnieuw lopen op het opvoeren toen op productie.
