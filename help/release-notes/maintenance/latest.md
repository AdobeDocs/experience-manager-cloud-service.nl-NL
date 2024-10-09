---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ea7e027b5247b64e78da1d14e4e602f39a37e4bd
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 18099 {#release-18099}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 18099 samengevat, die op 9 oktober 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 17964.

De activering van de 2024.10.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-18099}

* ASSETS-43015: Update to latest auth.ims bundle.
* ASSETS-41684: Update src/main/features/docker/ethos/base-ims-oauth.json.
* ASSETS-38322: Het toelaten van de gebeurtenis van het HTTP- verzoek voor AEM.
* ASSETS-41684: Voeg OOB OSGI-configuraties toe om FI te definiëren voor groepstoewijzing voor Assets, Foundation, Sites en Forms.
* ASSETS-41448: Update auth.ims bundle om FI aan groepstoewijzingen te steunen.
* CQ-4356633: Extra tekens toevoegen in de knopinfo Alleen inhoud.
* SITES-23584: De componenttests van de stichting ontbreken op Java 17.
* HULPLIJNEN-19069: Voeg hulplijnenPeerLinkIndex toe voor naamhulplijnen.
* GRANITE-54300: Werk Oak bij naar de meest recente openbare release (1.70.0).
* GRANITE-54274: Accept Firefly IMS client.
* GRANITE-36205: Werk de interne versie van de eikversie bij naar de recentste versie.
* GRANITE-45298: Een laag bevoorrechte gebruiker kan RCE krijgen door een kwaadwillige vorm zonder JS maar op de manier van XSS te creëren.
* GRANITE-54266: Production SDK mist Search Suggestor-service.
* GRANITE-50948 - Integreer de dataopslagdienst in AEM Voeg alternatieve dataopslagdienst voor lokale ontwikkeling toe.
* GRANITE-53966: Gebruik afzonderlijke draadpool voor inhoud-distributie.
* GRANITE-53514: Treeactivation 1.0.26.
* GRANITE-54054: Omgevingsvariabele voor com.adobe.granite.repository.impl.SystemUserValidation warnOnly.
* GRANITE-50948: Integreer de dataopslagservice in AEM Support for repository service.
* GRANITE-52454: ondersteunende helper 0.1.2 toevoegen.
* GRANITE-53514: Treeactivation 1.0.26.
* GRANITE-54038: Voeg de Enterprise IMS-client van het Creative Cloud toe aan de AEM IMS-client-lijst van gewenste personen.
* GRANITE-36205: Werk de interne versie van de eikversie bij naar de recentste versie.
* GRANITE-53485: Support Service Principal authentication for replication Azure Blob Storage.
* GRANITE-54006: update Jackson to 2.17.2.
* GRANITE-53287: Bezig met bijwerken van testversie voor integratie met beveiligingsrechten.
* GRANITE-53914: Platformtestfouten met Java 17 bijgewerkte moduleversie.
* GRANITE-53870: Maak een intern mechanisme om de maximale JVM-versiecontrole voor de snelstart over te slaan.
* GRANITE-52454: Verbetering van de ondersteuning Helper GRANITE-52454 voor upgradeondersteuning voor gebruik van de nieuwste release voor AEMaaCS.
* SKYOPS-85335: Update org.apache.sling.jcr.repoinit naar 1.1.52.
* SKYOPS-85336: Update Sling Commons Threads to 3.3.0.
* SKYOPS-76378: Verbeter draad-veiligheid van de registratie/deregistratie van ResourceBundle in i18n.
* SKYOPS-84951: Gegenereerde code voor het genereren van de controlesom van de inhoud van het bestand is onjuist.
* SKYOPS-82383: Stel het &quot;helm-waarden&quot;omzet-fusie-analyseresultaat in de beschrijver van de beveluitvoering bloot.
* SKYOPS-86329: het bijwerken van versies van platformtestmodules voor java 21 sdk steun.
* SKYOPS-69768: SlingModels deserialize ResourceResolvers niet.
* SKYOPS-84810: sla uitvoering &quot;40-initialize-publish.sh&quot;bij opstarten voor RDE over.
* SKYOPS-79285: Update Sling XSS aan 2.4.2

### Opgeloste problemen {#fixed-issues-18099}

* CNTBF-298: verwijder jcr:uid uit CC-geëxporteerde pakketten.
* SKYOPS-83910: Los problemen met gelijktijdige uitvoering op die in SKYOPS-82371 zijn aangetroffen.
* GRANITE-52876: Bijwerken naar com.adobe.granite.ui.content 0.8.1448.
* GRANITE-53088: Regressie ingevoerd bij de vaststelling van SITES-1992.
* GUIDEN-14445: De inheemse generatie van PDF ontbreekt met een fout met betrekking tot het krijgen van gebiedsdelen voor Node.js.
* HULPLIJNEN-16961: De titel met `<conref>` lost niet in Baseline en de Vertaaldashboards van de Redacteur van het Web op.
* HULPLIJNEN-17283: Wanneer het selecteren van de **meta-gegevens van het Gebruik die in de topicmeta** optie worden toegevoegd, worden de meta-gegevenseigenschappen niet verspreid in de documenteigenschappen van de inheemse output van PDF.
* HULPLIJNEN-17793: De referenced PDF wordt niet geactiveerd van het **BulkPublish Dashboard** tijdens de Bulkactivering van gepubliceerde inhoud.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en de kwesties van Gidsen die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-18099}

* FORMS - 15818: Component descriptor-item `OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml` niet gevonden instructies in serverlogboeken. Dit zijn ongevaarlijke loginstructies.

### Verouderde functies en API&#39;s {#deprecated-18099}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

Hieronder volgt een overzicht van onlangs vervangen functies of functies die verouderd zijn.

#### JavaScript Use API {#javascript-use-api}

[ het Gebruik API van JavaScript ](https://github.com/adobe/htl-spec/blob/master/SPECIFICATION.md#42-javascript-use-api) wordt officieel verouderd toe te schrijven aan uitdagingen hebben de gebruikers het zuiveren en het handhaven van code die hefboomwerkingen API, evenals prestatiesbeperkingen in vergelijking met het alternatief van Java.

U zou overgang aan [ het Gebruik API van Java moeten overschakelen, ](https://experienceleague.adobe.com/en/docs/experience-manager-htl/content/java-use-api) dat betere prestaties, gemakkelijkere zuivering, en grotere steun op lange termijn aanbiedt.

#### com.day.cq.wcm.api {#com-day-cq-wcm-api}

Houd er rekening mee dat de Adobe bezig is met het bijwerken van `com.day.cq.wcm.api` . Sommige methoden en klassen zijn in de huidige release gemarkeerd als `@Deprecated` . Deze worden in toekomstige versies verwijderd. Overstappen op de voorgestelde alternatieven.

#### org.apache.jackrabbit.oak.plugins.blob {#org.apache.jackrabbit.oak.plugins.blob}

* GRANITE-54165: Deprecate org.apache.jackrabbit.oak.plugins.blob in public API.

### Beveiligingsproblemen {#security-18099}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt twee geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-18099}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 70,0 | [ Oak API 1.70.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.70.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2 27,0 | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
