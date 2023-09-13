---
title: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de huidige onderhoudrelease [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 8a1ed1e44db0154854af73a96339d8e416afd3b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 2%

---

# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In de volgende sectie worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van as a Cloud Service Experience Manager beschreven.

## Release 13420 {#release-13420}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 13420 samengevat, die op 12 september 2023 openbaar werd gemaakt. Deze onderhoudrelease vervangt release 13323.

2023.9.0 Activering van de functie biedt de volledige functie die is ingesteld voor deze onderhoudsrelease. Zie de [Experience Manager geeft Routekaart vrij](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html) voor meer informatie .

### Verbeteringen {#enhancements-13420}

- ASSETS-19544: Activa die het laatst door eigendom zijn gewijzigd, zijn nu ingesteld op de gebruiker die de verwerking aanvraagt.

### Opgeloste problemen {#fixed-issues-13420}

- ASSETS-27628: Onjuiste &#39;kanalen&#39;-node die wordt gemaakt tijdens het aanpassen van het middelenzoekvenster
- ASSETS-27539: uploadbeperkingen reguliere expressie matching.
- ASSETS-26530: Unified Shell haalt gebruikers niet terug naar de oorspronkelijke pagina.
- ASSETS-22719: haken in de naam Onderbrekingspunt slim uitsnijden breken de functie Slim uitsnijden bewerken.
- ASSETS-27726: linkshare.html zou niet door Google moeten worden geïndexeerd.
- ASSETS-27791: Validatie van het metagegevensschema vindt alleen plaats voor het eerste veld.
- ASSETS-25544: Vaste knop voor CDN-cache-ongeldigmaking.
- ASSETS-26575: afkapping met vaste naam bij het maken van afbeeldingssets.
- ASSETS-26705: Oplossing voor onnodige verwerking van niet-DM-mapelementen en inhoudsfragmenten.
- ASSETS-25740: Vaste schermlezers vertellen de naam en de rol voor de besturingselementen Bewerken/Uitsnijden niet op de pagina &#39;Slimme uitsnijdingen bewerken&#39; met de pijltoetsen omlaag.
- CQ-4354266: Kan items in postvak niet openen.
- CQ-4354347: Bijgewerkte AEM vertalingen.
- DISP-1009: Gebruiker-Agent als niet eerste kopbal maakt x-Door:sturen-Gastheer in orde.
- Verschillende oplossingen voor toegankelijkheid en beveiliging.

### Bekende problemen {#known-issues-13420}

Geen.

### Ingesloten technologieën {#embedded-tech-13420}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM AK | 1,54-T20230817132355-3800a65 | [API 1.54.0 voor ongewenste API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Versie 2.27.2 | [API voor Apache Sling API 2.27.2](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Versie 1.4.20-1.4.0 | [HTML Sjabloontaalspecificaties](https://github.com/adobe/htl-spec) |
| AEM-kerncomponenten | Versie 2.23.2 | [AEM WCM Core-componenten](https://github.com/adobe/aem-core-wcm-components) |
