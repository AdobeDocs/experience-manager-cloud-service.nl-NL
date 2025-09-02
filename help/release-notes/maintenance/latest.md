---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 33468de99a3e77539f4bdc9435324c9f52a45d9f
workflow-type: tm+mt
source-wordcount: '350'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 22171 {#22171}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 22171 samengevat, die op 2 september 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd in release 21994 gepubliceerd.

De activering van de 2025.9.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Nieuwe functies  {#new-features-22171}

* ASSETS-53136: ondersteuning voor Vanity ID in Dynamic Media met OpenAPI.

### Verbeteringen {#enhancements-22171}

Geen.

### Opgeloste problemen {#fixed-issues-22171}

* ASSETS-52510: detectie van dubbele bestandsnamen mislukt voor bestandsnamen die Unicode bevatten `U+202F` .
* ASSETS-53489: het schrappen van de omslag van de UI van de Mening van Assets keurt niet alle bevatte activa goed.
* ASSETS-54821: Periodieke &quot;serverfout&quot; in Asset Link.
* ASSETS-55024: verbroken afbeelding in AEM Assets &quot;Download by Email&quot;-sjabloon.
* ASSETS-55325: statische URL&#39;s van dynamische media laten bestandsextensie weg nadat de naam van het element is gewijzigd.
* ASSETS-55334: Het dialoogvenster Delen van koppeling knippert kort en verdwijnt of verschijnt nooit.
* ASSETS-55382: opnieuw opgestarte taken voor async-elementen maken een dubbele doelmap.
* ASSETS-55472: Publicatieoptie &quot;Alleen al gepubliceerde pagina&#39;s opnemen&quot; wordt genegeerd.
* SITES-31600: Contexthub js fout die verpersoonlijking breken.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-22171}

Geen.

### Verouderde functies en API&#39;s {#deprecated-22171}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-22171}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 7 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-22171}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 84,0 | [ Oak API 1.84.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.84/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [ Apache Httpd 2.4.65 ](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [ Ondersteunde versies Node.js ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
