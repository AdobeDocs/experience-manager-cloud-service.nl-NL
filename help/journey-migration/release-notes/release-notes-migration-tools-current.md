---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2023.03.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2022.03.0
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
source-git-commit: 5815dacd2806cc7886aa0c7c5c9fd329306b3e1b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 1%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2023.03.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.03.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.40 is 3 maart 2023.

### Wat is er nieuw? {#what-is-new-bpa}

* BPA kan nu conflicterende knooppunten detecteren en rapporteren - knooppunten met hetzelfde `jcr:uuid`. Dergelijke bevindingen worden gemarkeerd als kritiek omdat dit kan leiden tot fouten bij het opnemen van inhoud wanneer inhoud wordt verplaatst naar AEM as a Cloud Service.
* BPA kan nu het gebruik van gebeurtenislisteners detecteren en rapporteren. Aanbevolen wordt dit type gebeurtenishandgrepen te herordenen met slingerende taken wanneer wordt overgeschakeld naar AEM as a Cloud Service.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde valse positieven op `grouprendercondition`. Dit is opgelost.