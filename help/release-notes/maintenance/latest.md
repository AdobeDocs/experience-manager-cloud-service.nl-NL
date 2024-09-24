---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: ca9b5965dbfade36763e2432601559c9abcd2d41
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 17689 {#release-17689}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 17689 samengevat, die op 10 september 2024 openbaar werd gemaakt. De vorige onderhoudsrelease was release 17569.

De activering van de 2024.9.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-17689}

* ASSETS-41404: Wijzigingen voor ondersteuning van DRM-verbeteringen.
* ASSETS-41621: Actualiseerde async Asset Copy-taak.
* ASSETS-32166: Bijgewerkte async Asset Move Job.
* ASSETS-41429: ondersteuning voor voorinstellingen voor afbeeldingen in DM OpenAPI.
* ASSETS-38968: Verbeterde weergave van verwijzingen naar inhoudsfragmenten.
* ASSETS-41787, ASSETS-41183: Improvements for Assets Bulk Operations Framework.
* GRANITE-52917: Optimalisaties om de installatietijden van het pakket voor het kopiëren van inhoud te verbeteren.
* SCRNS-3980: Detect Grijs scherm op spelers die opeenvolgingen zonder gepland middel hebben.

### Opgeloste problemen {#fixed-issues-17689}

* ASSETS-40875: Onbedoelde NPE geregistreerd door AssetDeleteHandler.
* ASSETS-42422: Vermijd het activeren van een asynchrone taak voor het verplaatsen van één element.
* ASSETS-41234: Verenigde Shell - Globale nav zou niet kunnen werken als geopend wanneer de onderzoeksbar open is.
* ASSETS-42256: Verenigde Shell - Tag/Badge die op milieu wijzen werkt slechts periodiek.
* ASSETS-41271: Voorkom dat Assets tijdens verplaatsingsbewerkingen opnieuw wordt gepubliceerd.
* ASSETS-38894: Limit Retries by processing watchdog.
* ASSETS-40815: Voorvertoning van PDF-uitvoering gebruiken voor het weergeven van PPT-bestand in de gebruikersinterface voor delen van koppeling.
* ASSETS-37123: Kan voorvertoning van element niet laden in het dialoogvenster Delen van koppeling.
* CQ-4358156: update-backs met tag die worden verwijderd.
* SCRNS-4495: Vaste knoop van het Deeg functioneert niet behoorlijk voor verschillende gebruikersgroepen.
* SCRNS-4512: Verwijder componenten met betrekking tot apparaat uit schermen AEMaaCS.
* SCRNS-4466: Op het Dashboard van het Kanaal, verberg - meningsmanifest, produceer off-line inhoud, werk manifestgeheime voorgeheugen bij, vertoningspaneel.
* SCRNS-4513: Voeg kolomkopballen voor de pagina van onderzoeksresultaten in lijstmening toe.

### Bekende problemen {#known-issues-17689}

* FORMS-14340: fout in het concretiseren van FormsAndDocumentOmniSearchHandler en CloudStorageSubmitActionInserter. Dit zijn ongevaarlijke loginstructies.
* FORMS-15818: Component descriptor-item &quot;OSGI-INF/com.adobe.aemfd.docmanager.impl.*.xml&quot; niet gevonden instructies in serverlogboeken. Dit zijn ongevaarlijke loginstructies.
* SITES-23662: Gebruiker die een publicatie activeert, kan niet uit JCR-loginstructies in serverlogboeken worden geëxtraheerd. Dit is voor een eigenschap onder ontwikkeling die intermitterende en ongevaarlijke &quot;kan geen geldige gebruiker - identiteitskaart in de partij van gebeurtenissen vinden OSGI&quot;fouten in het logboek zou kunnen veroorzaken.

### Kennisgeving wijzigen {#change-notice-17689}

* Vanaf september 2024 zal AEM as a Cloud Service de serialisatie van Resolvers van Middel via het Sling ModelExporter kader onbruikbaar maken. Zie [ de documentatie ](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md) voor meer details.

### Verouderde functies en API&#39;s {#deprecated-17689}

We zijn bezig met het bijwerken van `com.day.cq.wcm.api` en met de huidige release hebben we een aantal methoden en klassen gemarkeerd als `@Deprecated` . Deze zullen in toekomstige versies worden verwijderd, dus gelieve te overwegen aan hun voorgestelde alternatieven over te schakelen als u om het even welk van hen gebruikt.

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-17689}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 4 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-17689}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 68,0 | [ Oak API 1.68.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.68.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.24-1.4.0 | {de Specificatie van de Taal van het Malplaatje 0} HTML ](https://github.com/adobe/htl-spec)[ |
| AEM-kerncomponenten | 2.26.0. | [ AEM de Componenten van de Kern WCM ](https://github.com/adobe/aem-core-wcm-components) |
