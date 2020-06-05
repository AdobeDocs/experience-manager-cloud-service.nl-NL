---
title: Opmerkingen bij de release Adobe Experience Manager als Cloud Service voor 2020.5.0
description: Opmerkingen bij de release Experience Manager voor 2020.5.0
translation-type: tm+mt
source-git-commit: 06a56b0ca8000a41fe4e492206459b1525aae59d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Opmerkingen bij de release van AEM als Cloud Service 2020.5.0 {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor Experience Manager weergegeven als Cloud Service 2020.5.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als cloudservice 2020.5.0 is 7 mei 2020.

## Nieuw in AEM-sites {#aem-sites}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor AEM-sites in AEM als Cloud Service Release 2020.5.0.

* Gedetailleerde taakgegevens zijn nu beschikbaar nadat grote pagina&#39;s zijn verwerkt en als asynchrone taken zijn verplaatst.
* Wanneer u een paginastructuur kopieert/plakt, kunt u nu kiezen tussen alleen het plakken van de basispagina of ook van de subpagina&#39;s van de structuur.
* AEM Experience Fragments die naar de werkruimten van het Doel van Adobe worden uitgevoerd verschijnen nu als unieke aanbiedingstypes en aanbiedingen bronnen in Doel.
* MSM - het gebruiken van *publiceer* trekker rolt nu met succes verwijderingsgebeurtenissen voor componenten in levende exemplaarbron uit, namelijk het schrappen van componenten in een levende kopie die in levende exemplaarbron werden geschrapt.
* MSM - de levende exemplaarcomponenten worden nu anders genoemd aan *_msm_moving* na de zelfde componentenuitrol van levende exemplaarbron.


## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie om te weten te komen wat nieuw is en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.5.0.

### What&#39;s New {#what-is-new}

* Er zijn zes aanvullende regels voor codekwaliteit toegevoegd om klanten te helpen potentiële problemen te identificeren bij het plannen van een migratie naar Cloud Service.
* Er is een nieuwe metrische *Cloud Service Compatibility* toegevoegd om het aantal compatibiliteitsgerelateerde problemen samen te vatten.
* De omgevingen die niet konden worden gemaakt, worden nu ongeveer 24 uur na het maken automatisch verwijderd, tenzij ze al zijn verwijderd.
* De prestaties van de pagina van de Activiteit en de Uitvoeren van de Pijpleiding API zijn verbeterd.
* Het logbestand met codekwaliteit bevat nu volledige stacksporen voor uitzonderingen.

### Bug Fixes  {#bug-fixes}

* Er is een misleidende kaart weergegeven op de overzichtspagina terwijl de productiepijpleiding actief was.
* De *regel van de codekwaliteit van DontImplementOrExtendProviderTypesPomCheck* kan soms een Uitzondering van de Wijzer van de Null veroorzaken.
* Bepaalde documentatiekoppelingen van de overzichtspagina werken niet correct.
* Het dialoogvenster Omgeving maken is niet correct weergegeven in Safari.
* Bepaalde kaarten op de overzichtspagina gaven de entiteitsnamen niet correct weer.
* In sommige gevallen, zou het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.


