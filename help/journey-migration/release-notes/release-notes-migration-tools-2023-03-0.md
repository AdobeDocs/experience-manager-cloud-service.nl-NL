---
title: Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.03.0
description: Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.03.0
feature: Release Information
exl-id: cdc57cca-e10a-4b0d-b803-910ccc9350a6
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 1%

---

# Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.03.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2023.03.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.40 is 3 maart 2023.

### Wat is er nieuw? {#what-is-new-bpa}

* BPA kan nu conflicterende knooppunten detecteren en rapporteren - knooppunten met dezelfde `jcr:uuid` . Dergelijke bevindingen worden als kritiek gemarkeerd omdat dit kan leiden tot fouten bij het opnemen van inhoud wanneer inhoud naar AEM as a Cloud Service wordt verplaatst.
* BPA kan nu het gebruik van gebeurtenislisteners detecteren en rapporteren. Aanbevolen wordt om dit type gebeurtenishandgrepen te heroriënteren naar slingertaken bij de overgang naar AEM as a Cloud Service.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde valse positieven op `grouprendercondition`. Dit is opgelost.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.16 is 8 maart 2023.

### Wat is er nieuw? {#what-is-new-ctt}

* Toewijzing van gebruikers is gestroomlijnd en geïntegreerd in de extractiestap voor inhoud. Er is geen installatie nodig en door de standaardgebruikerstoewijzing wordt automatisch uitgevoerd wanneer de gebruiker inhoud afhaalt. De gebruiker heeft de optie om gebruikerstoewijzing indien nodig uit te schakelen. Leer meer [ hier.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/user-mapping-and-migration.html#user-mapping-detail)
* De precopystap die [ AzCopy ](https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-v10) gebruikt is geïntegreerd met het Hulpmiddel van de Overdracht van de Inhoud om inhoudextracties beduidend te versnellen. De precopy wordt automatisch gevormd en geïnstalleerd wanneer deze versie van CTT wordt geïnstalleerd. Wanneer de extractie wordt gestart, wordt de migratie standaard automatisch uitgevoerd voor migratiesets die groter zijn dan 200 GB. De gebruiker heeft de optie om het onbruikbaar te maken indien nodig. Leer meer [ hier.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/handling-large-content-repositories.html)
* CTT kan nu op de servers van Vensters worden gebruikt.

### Opgeloste problemen {#bug-fixes-ctt}

* Meerdere correcties om de weerbaarheid van extractie van inhoud te verbeteren.
