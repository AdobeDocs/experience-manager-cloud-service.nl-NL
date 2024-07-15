---
title: Opmerkingen bij de release van Adobe Experience Manager as a Cloud Service voor 2020.5.0
description: "[!DNL Adobe Experience Manager] as a Cloud Service opmerkingen bij de release voor 2020.5.0."
exl-id: 8570d2c3-6d55-4914-94b2-f5d162e0c285
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Opmerkingen bij de release voor AEM as a Cloud Service 2020.5.0 {#release-notes}

Deze pagina beschrijft de algemene opmerkingen bij de release voor Experience Manager as a Cloud Service 2020.5.0.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Experience Manager] as a Cloud Service 2020.5.0 is 7 mei 2020.

## Nieuwe functies in AEM Sites {#aem-sites}

Volg deze sectie voor meer informatie over wat nieuw is en de updates voor AEM Sites in AEM as a Cloud Service Release 2020.5.0.

* Gedetailleerde taakgegevens zijn nu beschikbaar nadat grote pagina&#39;s zijn verwerkt en als asynchrone taken zijn verplaatst.
* Wanneer u een paginastructuur kopieert/plakt, kunt u nu kiezen tussen alleen het plakken van de basispagina of ook van de subpagina&#39;s van de structuur.
* AEM Experience Fragments geëxporteerd naar Adobe Target-werkruimten worden nu weergegeven als unieke aanbiedingstypen en bieden bronnen aan in Target.
* MSM - gebruikend *publiceer* trekker nu met succes rolt uit schrappingsgebeurtenissen voor componenten in levende exemplaarbron, namelijk het schrappen van componenten in een levend exemplaar die in levende exemplaarbron werden geschrapt.
* MSM - de levende exemplaarcomponenten worden nu anders genoemd aan *_msm_moving* na de zelfde componentenuitrol van levende exemplaarbron.


## Nieuwe functies in Cloud Manager {#cloud-manager}

Volg deze sectie voor meer informatie over wat nieuw is en de updates voor Cloud Manager in AEM as a Cloud Service Release 2020.5.0.

### Wat is er nieuw? {#what-is-new}

* Er zijn zes aanvullende regels voor codekwaliteit toegevoegd om klanten te helpen potentiële problemen te identificeren wanneer ze een migratie naar Cloud Service plannen.
* Een nieuwe metrische *Verenigbaarheid van de Cloud Service* is toegevoegd om het aantal op verenigbaarheid betrekking hebbende kwesties samen te vatten.
* De omgevingen die niet konden worden gemaakt, worden nu ongeveer 24 uur na het maken automatisch verwijderd, tenzij ze al zijn verwijderd.
* De prestaties van de pagina van de Activiteit en de Uitvoeren van de Pijpleiding API zijn verbeterd.
* Het logbestand met codekwaliteit bevat nu volledige stacksporen voor uitzonderingen.

### Opgeloste problemen  {#bug-fixes}

* Er is een misleidende kaart weergegeven op de overzichtspagina terwijl de productiepijpleiding actief was.
* *DontImplementOrExtendProviderTypesPomCheck* de kwaliteitsregel van de codekwaliteit kon soms een Volledige Uitzondering van de Aanwijzer veroorzaken.
* Bepaalde documentatiekoppelingen van de overzichtspagina werken niet correct.
* Het dialoogvenster Omgeving maken is niet correct weergegeven in Safari.
* Bepaalde kaarten op de overzichtspagina gaven de entiteitsnamen niet correct weer.
* In sommige gevallen, zou het Beeld van de Bouwstijl er niet in slagen om klantenpakketten met succes te downloaden.
