---
title: Adobe Experience Manager als de Nota's van de Versie van de Cloud Service voor 2020.5.0
description: Opmerkingen bij de release van Experience Manager voor 2020.5.0
translation-type: tm+mt
source-git-commit: 3dc0d1d77595f7b3e890fb4b390eef5bcf84ecd8
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# Opmerkingen bij de release voor AEM als Cloud Service 2020.5.0 {#release-notes}

Deze pagina schetst de algemene opmerkingen bij de release voor Experience Manager als Cloud Service 2020.5.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] als Cloud Service 2020.5.0 is 7 mei 2020.

## Nieuwe functies in AEM Sites {#aem-sites}

Volg deze sectie om te leren over wat nieuw en de updates voor AEM Sites in AEM als Versie van de Cloud Service 2020.5.0 is.

* Gedetailleerde taakgegevens zijn nu beschikbaar nadat grote pagina&#39;s zijn verwerkt en als asynchrone taken zijn verplaatst.
* Wanneer u een paginastructuur kopieert/plakt, kunt u nu kiezen tussen alleen het plakken van de basispagina of ook van de subpagina&#39;s van de structuur.
* AEM Experience Fragments geëxporteerd naar Adobe Target-werkruimten worden nu weergegeven als unieke aanbiedingstypen en bieden bronnen aan in Target.
* MSM - het gebruiken van *publiceer* trekker rolt nu met succes verwijderingsgebeurtenissen voor componenten in levende exemplaarbron uit, namelijk het schrappen van componenten in een levende kopie die in levende exemplaarbron werden geschrapt.
* MSM - de levende exemplaarcomponenten worden nu anders genoemd aan *_msm_moving* na de zelfde componentenuitrol van levende exemplaarbron.


## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over nieuwe functies en de updates voor Cloud Manager in AEM als Cloud Service Release 2020.5.0.

### What&#39;s New {#what-is-new}

* Er zijn zes aanvullende regels voor codekwaliteit toegevoegd om klanten te helpen potentiële problemen te identificeren wanneer ze een migratie naar Cloud Service plannen.
* Er is een nieuwe metrische *Cloud Service-compatibiliteit* toegevoegd om het aantal compatibiliteitsproblemen samen te vatten.
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


