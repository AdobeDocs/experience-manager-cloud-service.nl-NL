---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 859af15f4038b28e6e1398e5168dc008d22985e9
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 1%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

>[!NOTE]
>
> De releases 20936 en 20783 zijn privé gemaakt.

## Release 20626 {#20626}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 20626 samengevat, die op 29 april 2025 openbaar werd gemaakt. De vorige onderhoudrelease werd uitgebracht in 20476.

De activering van de 2025.5.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

### Verbeteringen {#enhancements-20626}

* ASSETS-46413, ASSETS-46580: voeg een nieuwe revisiestatus &quot;Voorvertoning&quot; toe.
* ASSETS-49542: Uitbreiding van ondersteunde talen voor video- en audiotranscriptie en -translatie.
* ASSETS-48264: uitbreiding van ondersteuning voor PNG-kwaliteit voor uitvoeringen.

### Opgeloste problemen {#fixed-issues-20626}

* ASSETS-50387: Corrit de standaardminiatuur van inhoudsfragment voor gebruik in GenStudio.
* ASSETS-49006: video-eigenschappen weergeven als de gebruiker geen schrijfmachtigingen heeft.
* ASSETS-46757, ASSETS-46997: Verbeterde toegankelijkheid in de Smart crop editor.
* ASSETS-48018: Verbeter de functie voor het bijhouden van middelenverwijzingen in het Assets-publicatierapport.
* ASSETS-35846: Verbeter de consistentie van toegang tussen auteur en leveringsrij.
* ASSETS-48171: Verbeter consistentie van Dynamic Media Templating met Canvas.
* ASSETS-49813: Vervalmelding verbeteren.
* ASSETS-47768, ASSETS-49825, ASSETS-49008, ASSETS-48287: Verbeteren van het beheer en de zichtbaarheid in bulktransacties.
* ASSETS-50003, ASSETS-50004: Verbeter naamgeving en controle over de uitvoeringen die deel uitmaken van een download van middelen.
* ASSETS-47939: Verbetering van de organisatie van de antwoorden voor Content Hub.
* ASSETS-46738: Verbeter de prestaties voor zeer grote verzamelingen.
* ASSETS-50121: Verbeteren van de betrouwbaarheid van gebeurtenissen die gepubliceerd zijn op het gebied van bedrijfsmiddelen.
* ASSETS-48490: Verbeter de veerkracht van geautomatiseerde verwerking tijdens het opnemen van afbeeldingen.
* ASSETS-28106, ASSETS-49404: Verbeter robuustheid van het volledige tekstzoeken.
* ASSETS-50006, ASSETS-50423: Verbeter zoekprestaties en traversal prestaties in een grote map.
* ASSETS-46021: Verbetering van de videoweergave voor Safari- en mobiele browsers.
* ASSETS-49002: Verbeterde verwerking van het bewerken van dynamische mediasjablonen.
* ASSETS-48376: Diverse verbeteringen in de gebruikersinterface van Content Hub.
* ASSETS-48504, ASSETS-49378: Diverse verbeteringen aan het gedrag van de gebruikersinterface.
* ASSETS-49540: Verplaats Asset Relations OpenAPI uit de experimentele fase.
* ASSETS-40284: Werk documentatie bij over de integratie met Adobe Stock.
* ASSETS-49739: Acties voor de integratie van Figma van Asset Selector.

#### AEM Guides {#guides}

* HULPLIJNEN-21734: Nieuwe id&#39;s kunnen niet worden gegenereerd voor elementen wanneer dergelijke elementen via fragmenten worden toegevoegd of via sjablonen worden gemaakt, zelfs wanneer de optie Automatisch id genereren is ingeschakeld in XMLEditorConfig.
* GUIDEN-25969: Als het `scope=external` attribuut van externe verbindingen in een DITA onderwerp mist, ontbreekt het publiceren HTML5 zonder op de dossiers te wijzen waar dit attribuut in de foutenlogboeken mist, vooral wanneer de microservice wordt toegelaten.
* GUIDES-27288: Kan de eigenschappen van metagegevens niet doorgeven om bestemmingspagina&#39;s die zijn gegenereerd met behulp van nieuwe AEM Sites-publicaties toe te wijzen.

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [ versie van Experience Manager Guides roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-20626}

Geen.

### Verouderde functies en API&#39;s {#deprecated-20626}

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [ Vervangen en Verwijderde Eigenschappen en APIs ](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-20626}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 11 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-20626}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 78,0 | [ Oak API 1.78.0 ](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.78.0/index.html) |
| AEM SLING-API | 2,27,6 | [ Apache Sling API 2.27.6 API ](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.26-1.4.0 | [ Specificatie van de Taal van het Malplaatje van HTML ](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | 2 29,0 | [ AEM WCM de Componenten van de Kern ](https://github.com/adobe/aem-core-wcm-components) |
