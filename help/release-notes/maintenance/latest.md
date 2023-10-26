---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: aa9629c3e48ca0bf4654351462a94777af9ed651
workflow-type: tm+mt
source-wordcount: '606'
ht-degree: 0%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 14029 {#release-14029}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 14029 samengevat, die op 25 oktober 2023 openbaar werd gemaakt. Deze onderhoudrelease is een update van eerdere onderhoudrelease 13804.

2023.11.0 Activering van functies biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-14029}

* ASSETS-2851: Verbeter scalability van Mijn Verbinding deelt UI
* ASSETS-28566: Add dam:metadataForm Lucene index
* ASSETS-29281: RAPI bijwerken voor het verzenden van v2-downloadgebeurtenissen

### Opgeloste problemen {#fixed-issues-14029}

* ASSETS-25199: beeldkerncomponent heeft geen juiste slimme gewassen
* ASSETS-26142: Unified-shell.js customEnvLabel niet ingesteld of geactiveerd als de detectieaanvraag mislukt of wordt onderbroken
* ACTIVA-26416: Relatieve datumvoorspelling wordt altijd gedefinieerd als &quot;1 dag(en) geleden&quot; in zoekformulier
* ASSETS-27321: wissen, groepscache bij wijzigingen in teamlidmaatschap
* ASSETS-27591: Corrigatie van oude org.json
* ASSETS-28439: Smart tags Lijst van gewezen personen NPE wanneer global lijst van gewezen personen niet is geconfigureerd
* ASSETS-28612: BlockedTagResolver fix in &quot;repository-api&quot;
* ASSETS-28634: Omnzoekveld in Adobe stock krijgt geen automatisch toegevoegde elementgegevens
* ASSETS-28727: De lijst Configuratie van het Profiel van de verwerking toont niet de gespecificeerde douanehoogte en breedtewaarden
* ASSETS-29056: Transcoderingsuitvoeringen toevoegen AEM standaard verwerkingsprofiel
* ASSETS-29105: Restrictieprovider ontbreekt in SecurityProviderRegistration requiredServicePids in RDE-functiemodel
* ASSETS-29106: View on Adobe stock werpt error on Unified Shell enabled AEM
* ASSETS-29115: wijzig de configuratie-eigenschap voor Restriction Provider-paden
* ASSETS-29208: fouten bij het uploaden van middelen die worden veroorzaakt door verzoeken die naar een auteurspod worden verzonden voordat service CompleteUploadAssetServlet is geregistreerd
* ASSETS-29297: Probleem tijdens het maken van Opslaan, zoekopdracht met uitgecheckte filteroptie
* ASSETS-29363: Metagegevensprofiel past geen standaardwaarden voor IPTC toe
* ASSETS-29404: Link Share report Hitting query limit
* ASSETS-29431: oude functiemarkeringen verwijderen
* ASSETS-29443: Unified Shell Hero blijft zichtbaar en kan worden geklikt wanneer de koptekstmodus van Granite Shell verandert in &quot;selectie&quot;
* ASSETS-29476: scene7DAMService.getS7FileReference(asset) Api call retourneert de verwachte waarde niet.
* ASSETS-29515: Middelen / Nodes met &quot;jcr:lastModifiedBy&quot;: &quot;workflow-process-service&quot; wordt weergegeven als &quot;externe gebruiker&quot; in de lijstweergave
* ASSETS-29579: gebruikers die geen beheerder zijn, kunnen geen Image Set maken
* ASSETS-29631: Use dam:rollen for secure delivery/search
* ASSETS-29689: dc:rollen (en de nieuwe bezitsdam:rollen) zouden van AEM kant moeten worden gefiltreerd
* ACTIVA-29738: Beperking van het uploaden van activa mislukt met NullPointerException
* ASSETS-29779: kleine activa kunnen niet naar webp worden verwerkt omdat ze zich niet in blob-opslag bevinden
* ASSETS-29892: het exporteren van metagegevens mislukt in een map met een groot aantal elementen
* ASSETS-2996: &quot;External User&quot; as modifier (Externe gebruiker) bij het tijdelijk uploaden van middelen alleen op PROD-instantie
* ASSETS-30167: HTML voor adobe_dam:regeleinden na het uploaden van een element
* ASSETS-30276: Share Link UI: cannot share from assetdetails
* ACTIVA-30434: Gebeurtenis na voltooiing van de verwerking van activa niet naar Pipeline verzonden
* ASSETS-30519: voeg RAPI toe aan REDMetricsServletFilter
* CQ-4354413: QueryBuilder: query&#39;s met vierkante haken worden onjuist vertaald naar xpath
* CQ-4354834: Kan geen opmerking toevoegen in Postvak IN-taak
* CQ-4354836: Kan geen workflow starten of taak maken vanuit projectenconsole
* CQ-4354867: verwijzing ToggleCondition verwijst naar een niet-bestaand veld in InstanceActionServlet
* CQ-4354895: AEM vertaalkit: 12 oktober
* GRANITE-45560: Gemeenschappelijke schemavertegenwoordiging in de Event-envelop
* GRANITE-47267: Update to Apache Felix HTTP Jetty 4.2.18
* GRANITE-47599: De invoer van inhoud mislukt sinds de upgrade van 13323 (JCRVLT-721)
* GRANITE-47873: Bijwerken naar Apache Felix Webconsole 4.9.6

### Bekende problemen {#known-issues-14029}

* CQ-4354836: Kan geen workflow starten of taak maken vanuit projectenconsole.
* CQ-4354834: Gebruikers kunnen geen opmerkingen toevoegen in een Postvak IN-taak.

### Ingesloten technologieën {#embedded-tech-14029}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,56-T20230927085643-189caed | [API 1.56.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.4 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
