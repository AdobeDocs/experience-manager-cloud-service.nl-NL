---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.5.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.5.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.5.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.5.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.5.0 is 7 mei 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* Er zijn zes aanvullende regels voor codekwaliteit toegevoegd om klanten te helpen potentiële problemen te identificeren wanneer ze een migratie naar Cloud Service plannen.
* Er is een nieuwe metrische *Compatibiliteit met Cloud Servicen* toegevoegd om het aantal compatibiliteitsgerelateerde problemen samen te vatten.
* De omgevingen die niet konden worden gemaakt, worden nu ongeveer 24 uur na het maken automatisch verwijderd, tenzij ze al zijn verwijderd.
* De prestaties van de pagina van de Activiteit en de Uitvoeren van de Pijpleiding API zijn verbeterd.
* Het logbestand met codekwaliteit bevat nu volledige stacksporen voor uitzonderingen.

### Opgeloste problemen {#bug-fixes}

* Er is een misleidende kaart weergegeven op de overzichtspagina terwijl de productiepijpleiding actief was.
* De code *DontImplementOrExtendProviderTypesPomCheck* kwaliteitsregel kan soms een Null-aanwijzeruitzondering veroorzaken.
* Bepaalde documentatiekoppelingen van de overzichtspagina werken niet correct.
* Het dialoogvenster Omgeving maken is niet correct weergegeven in Safari.
* Bepaalde kaarten op de overzichtspagina gaven de entiteitsnamen niet correct weer.
* In sommige gevallen, zou het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.
