---
title: Opmerkingen bij de release Cloud Manager 2023.8.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.8.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: 99772a1a3faa454a9b07dd92c9e7622ddb37ce2d
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 0%

---


# Opmerkingen bij de release Cloud Manager 2023.8.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.8.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.8.0 in AEM as a Cloud Service is 10 augustus 2023. De volgende release is gepland voor 7 september 2023.

## Wat is er nieuw? {#what-is-new}

* Wanneer u inhoud configureert die is ingesteld op [inhoud kopiëren,](/help/implementing/developing/tools/content-copy.md) [contextbewuste configuraties](/help/implementing/developing/introduction/configurations.md) zijn nu toegestaan in inhoudssets in de gebruikersinterface.
* Er zijn verbeteringen aangebracht om de begrijpelijkheid en het omgaan met foutberichten in de gebruikersinterface van Cloud Manager te verbeteren.

## Programma voor vroegtijdige adoptie {#early-adoption}

Maak deel uit van ons programma voor vroegtijdige goedkeuring en heb de kans om een aantal van de komende kenmerken te testen.

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

## Opgeloste problemen {#bug-fixes}

* De **Omgevingen** wordt nu gesloten na het activeren van de **[Inhoud kopiëren](/help/implementing/developing/tools/content-copy.md)** modal.
* [Een wederuitvoering van de pijpleiding](/help/implementing/cloud-manager/deploy-code.md#reexecute-deployment) is niet meer toegestaan als de vorige uitvoering geen `commitId` reeks op de bouwstijlstaat.
* Een begrijpelijker bericht wordt nu getoond voor zeldzame fouten wanneer een gebruiker op een pijpleiding in klikt **Activiteit** of **Pijpleiding** schermen.
* De `contentSetName` de waarde ontbreekt niet meer in logbestanden en wordt nu in de invoer opgegeven wanneer een [inhoudskopie](/help/implementing/developing/tools/content-copy.md) -bewerking.
* Het is in bepaalde zeldzame omstandigheden niet langer mogelijk om twee executies te starten vanaf dezelfde pijpleiding die tot een &quot;vastgelopen&quot; staat leiden.
* Wanneer een certificaat verloopt, worden de domeinnamen en IP allow-lists verbonden aan het certificaat niet meer verwijderd uit CDN.
   * In dergelijke gevallen, zal de plaats bereikbaar blijven.
   * [De interface van Cloud Manager](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) geeft meer zichtbare voorafgaande waarschuwingen dat het SSL-certificaat op het punt staat te verlopen.
* Een probleem met AEM het verliezen van toegang tot te publiceren eindpunt werd bevestigd in situaties wanneer de Plaatsen als oplossing aan een activa-slechts programma worden toegevoegd.
