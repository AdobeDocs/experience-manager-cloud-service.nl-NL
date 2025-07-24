---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3686697c85273ccc13e80b8d7f4ad1ff3c79845d
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 21706 {#21706}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 21706 samengevat, die op 24 juli 2025 openbaar werd gemaakt. De vorige onderhoudrelease was release 21570.

>[!NOTE]
>
>Release 21644 is privé gemaakt en vervangen door release 21706.

De activering van de 2025.7.0-functie biedt de volledige functionaliteit die is ingesteld voor deze onderhoudsrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-21706}

* ASSETS-39377: Verbeter de verwerking van 429s van externe opslag in Assets Bulk Importer.
* ASSETS-46026: configureerbare maximale diepte voor het exporteren van metagegevens.
* ASSETS-49172: Dynamic Media Template-elementen moeten metagegevens uit map overnemen.
* ASSETS-50209: Ondersteuning voor substring in DM Templates.
* ASSETS-52326: AEM Assets-configuratiepagina voor het instellen van de voorkeuren voor de titelweergave voor Assets.
* ASSETS-52805: voeg CSV-uitvoer-/downloadondersteuning toe voor de Bulk Operation Job.
* ASSETS-52873: voeg een nieuwe configuratie in de omslageigenschappen toe om AI verwerking voor die omslag onbruikbaar te maken.
* ASSETS-53535: betere prestaties bij het uploaden van YouTube-video.
* ASSETS-53612: Besturingselement voor hybride zoekopdrachten in Assets Omnissearch.
* GRANITE-60183: Update commons-fileupload gebiedsdeel aan 1.6.0.
* GRANITE-60287: Werk QS aan Jackrabbit 2.22.1 bij.
* SITES-30452: Content API met ASO - Title &amp; Description Suggestions.
* SITES-31677: Aangepaste werkruimte ondersteunt AEM Content fragment dat wordt geëxporteerd naar Doel.
* SKYOPS-112741: verwijder de `com.adobe.granite.product.support` -bundel uit de AEM-CS SDK.

### Opgeloste problemen {#fixed-issues-21706}

* ASSETS-12882: Problemen met de uitlijning van de gebruikersinterface nadat viewervoorinstellingen zijn geopend.
* ASSETS-48958: Probleem met het wijzigen van de Published Status in Sites local AEM.
* ASSETS-50856: `dam:processingAttempts` wordt niet opnieuw ingesteld bij completeUpload.
* ASSETS-51604: Het Rapport CSV van het Aandeel van de verbinding Ontbrekende &quot;Gedeeld met&quot;Gegevens.
* ASSETS-51783: Fallback aan DM config onder `/conf/global` als geen config gebruikend onderzoeksvraag wordt gevonden.
* ASSETS-51857: Posten in de tabel van activa die niet opnieuw kunnen worden geordend.
* ASSETS-52169: Nieuwe BAT-computeruitvoering wordt ten onrechte opgenomen in het downloaden van bedrijfsmiddelen.
* ASSETS-52229: Ontbrekende Postvak meldingen voor Asset Reports in AEM as a Cloud Service.
* ASSETS-52399: Version bump in com.day.cq.dam.api kan de klantcode onderbreken.
* ASSETS-52780: Element kan voor voorvertoning worden gemarkeerd, zelfs zonder dat dit ingeschakeld is.
* ASSETS-52866: Gigreerde DM-video&#39;s blijven in verwerkingsstatus onder map met DM Sync uitgeschakeld.
* ASSETS-53237: de dropdown van het Profiel van de Kleur in Beeld vooraf ingestelde redacteur.
* ASSETS-53240: Asset Report - Het schijfgebruik mislukt bij het ophalen van de grootte van de asset-uitvoering via Dynamic Media.
* ASSETS-53446: Periodieke YouTube auth token vernieuwt fouten vanwege NPE.
* ASSETS-53827: ACL bevestigingsblokken sparen Gemengde Reeksen van Media.
* ASSETS-5403: Dynamicmedia-clientlibs die worden gebruikt op een publicatie-instantie, moeten `allowProxy=true` hebben.
* ASSETS-54261: Metagegevens importeren lekt verbindingen en wordt geblokkeerd als het bestand niet kan worden gedownload.
* CQ-4359863: Het onderzoek van markeringen gebroken naar sleutelwoorden uit orde in de Redacteur van het Fragment van de Inhoud/de redacteur van Activa.
* CQ-4359958: Zorg dat openapi-ondersteuning compatibel is met AEM 6.5.22.0 en hoger.
* CQ-4360256: Neem het pad van de servlet-context op in het aanvraagpad voor HTTP-aanvragen die worden afgehandeld via de `/adobe` servlet-context.
* CQ-4360317: Methode toevoegen voor het instellen van de header Zonnedatum bij het maken van reacties.
* GRANITE-60311: AEM SDK Quickstart - NPE op &quot;OSGi Installer Configuration Printer&quot;.
* GS-15285: gebruikers worden weergegeven als gedeactiveerd.

### Bekende problemen {#known-issues-21706}

Geen.

### Verouderde functies en API&#39;s {#deprecated-21706}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-21706}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 4 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-21706}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 80,0 | [ Oak API 1.80.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.80/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,63 | [ Apache Httpd 2.4.63 ](https://github.com/apache/httpd/blob/2.4.63/CHANGES) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
