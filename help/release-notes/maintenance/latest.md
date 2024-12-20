---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8a798e1f1b7234f91682b6e5ef7072e024df022
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 18751 {#18751}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 18751 samengevat, die op 11 december 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 18598.

De activering van de 2025.1.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-18751}

* SKYOPS-88509: Java 21-ondersteuning voor de AEM SDK.

### Opgeloste problemen {#fixed-issues-18751}

* ASSETS-42802: De knop Terug op MFE werkt niet altijd en toont een extra dialoogvenster.
* ASSETS-44148: De vaste gebeurtenis NODE_MOVED in AEM kan NPE veroorzaken.
* ASSETS-44418: Fixed Correct env wordt niet geconfigureerd op skyline.
* ASSETS-44821: Fixed Update event filter to include form-url-encoded data for upload events.
* CNTBF-298: Kopie van vaste inhoud mislukt bij UUID-conflicten.
* CNTBF-331: [ inhoud-exemplaar-bundel ] versie 2.0.14.
* FORMS-16572: Verwijder mislukkingen van workflowtests voor de build van java 21 SDK.
* GRANITE-36205: Automated update for internal eak release in QS.
* GRANITE-53704: Sling Discovery on Repository Service opnieuw evalueren.
* GRANITE-54300: Werk Oak bij naar de meest recente openbare release (1.70.0).
* GRANITE-54416: Werk FileVault bij naar versie 3.8.2.
* GRANITE-54462: Vorm SubscriberAgents om hc.tags van &quot;systemready&quot;te gebruiken.
* GRANITE-54542: Werk de gemeenschappelijke afhankelijkheid van io aan 2.17.0.
* GRANITE-54658: Voeg delayFactor en partij-grootte OSGi vormen voor fullGC in QS toe.
* GRANITE-54696: Breid de invoerwaaier voor Jackrabbit API uit.
* GRANITE-54803: maak ClusterAtExchange in AEM onbruikbaar wanneer imsauth actief is.
* GRANITE-55095: Update Oak to latest public release (1.72.0).
* HULPLIJNEN-2006: De staat van het document duidelijk zoals Gedaan keert terug naar Ontwerp alvorens een nieuwe versie op te slaan, resulterend in de Gedaan staat niet voortduurt in om het even welke documentversies.
* GUIDEN-21840: In de Eigen uitvoer van PDF, ontbreken de hoofdstuktitels van TOC, leidend tot een onjuiste hiërarchie.
* GUIDEN-1958: Het uitgeven en dan het opslaan van een basislijn op een chronologie van de wolkenopstelling na 1 minuut als de basislijn groot aantal onderwerpen of kaarten heeft.
* GUIDEN-1973: De vertaling van de kaart die basislijn gebruikt wordt langzaam en uiteindelijk ontbreekt om de lijst van alle bijbehorende onderwerpen en kaartdossiers te laden.
* SITES-26798: De auto-Bevordering van de lancering werkt niet de Status van de Bevordering (de Datum van de Bevordering) bij.
* SITES-27137: Verwijder het Verschuiven gemeenschappelijke metrieafhankelijkheid van de kern MSM.
* SKYOPS-75446: Vaste AEM retourneert soms 404 of pagina&#39;s met ontbrekende inhoud.
* SKYOPS-76366: Geen Jetty Threadpool metrics in AEM release 15977 en hoger.
* SKYOPS-82371: java.io.IOException: classFile.delete() failed.
* SKYOPS-83369: AEM implementaties kunnen niet worden gestart als de uitvoering van de transformatietaak geen bundels genereert.
* SKYOPS-83910: Opgeloste problemen met gelijktijdige uitvoering gevonden in SKYOPS-82371.
* SKYOPS-84821: Plaats de het Sling Hoofdserver sling.includes.checkcontent type configuratie aan waar.
* SKYOPS-85798: Vaste transformatietaak genereert lege indexdefinities.
* SKYOPS-86251: Upgrade naar AEM Analyser core 1.5.6 en schakel de productpakketimportanalysator in de transformatietaak in.
* SKYOPS-86710: verwijder de mislukkingen van de Minfy-test voor de bouw van java 21 sdk.
* SKYOPS-86745: Update aan Sling ResourceResolver 1.12.2.
* SKYOPS-89616: Opgelost kan geen technisch account maken in Adobe Developer Console.
* SKYOPS-89691: Fixed Incorrect artifact id die voor de waarschuwingen van ASM wordt gebruikt.
* SKYOPS-89699: Ontbrekende waarschuwingen voor oude Groovy-versies ingesloten in de &#39;orbinson&#39;-smaak van de Groovy Console.
* SKYOPS-88664: Log en bescherm tegen een geval wanneer het gedownloade kaartdossier lijn overschrijdt 1024 grens.
* SKYOPS-89734: Geef de verzender beeld 2.0.235 van de versie op.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en de kwesties die in Experience Manager Guides worden bevestigd, bekijk de [ versie roadmap van Experience Manager Guides ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-18751}

Geen.

### Verouderde functies en API&#39;s {#deprecated-18751}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-18751}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 3 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-18751}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 72,0 | [ Oak API 1.72.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.72.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
