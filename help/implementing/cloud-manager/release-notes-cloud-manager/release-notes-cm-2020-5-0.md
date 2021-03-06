---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.5.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.5.0
feature: Release Information
exl-id: 9f534858-d18f-4224-8b94-9583a05aed95
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.5.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2020.5.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2020.5.0 is 7 mei 2020.

## Wat is er nieuw? {#whats-new-cloud-manager}

* Er zijn zes aanvullende regels voor codekwaliteit toegevoegd om klanten te helpen potentiële problemen te identificeren wanneer ze een migratie naar Cloud Service plannen.
* Een nieuwe metrische waarde *Compatibiliteit met Cloud Service* is toegevoegd om een overzicht te geven van het aantal compatibiliteitsproblemen.
* De omgevingen die niet konden worden gemaakt, worden nu ongeveer 24 uur na het maken automatisch verwijderd, tenzij ze al zijn verwijderd.
* De prestaties van de pagina van de Activiteit en de Uitvoeren van de Pijpleiding API zijn verbeterd.
* Het logbestand met codekwaliteit bevat nu volledige stacksporen voor uitzonderingen.

### Opgeloste problemen  {#bug-fixes}

* Er is een misleidende kaart weergegeven op de overzichtspagina terwijl de productiepijpleiding actief was.
* De *DontImplementOrExtendProviderTypesPomCheck* De regel voor codekwaliteit kan soms een uitzondering met de aanwijzer Null veroorzaken.
* Bepaalde documentatiekoppelingen van de overzichtspagina werken niet correct.
* Het dialoogvenster Omgeving maken is niet correct weergegeven in Safari.
* Bepaalde kaarten op de overzichtspagina gaven de entiteitsnamen niet correct weer.
* In sommige gevallen, zou het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.
