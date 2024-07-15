---
title: Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.09.0
description: Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.09.0
feature: Release Information
exl-id: 484a60d4-a439-43d6-a23e-4a3b45ef4160
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 1%

---

# Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2023.09.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2023.09.0.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v3.0.0 is 7 september 2023.

### Wat is er nieuw? {#what-is-new-ctt}

Het gereedschap Inhoud overbrengen is verbeterd en biedt nu de volgende voordelen:

* Minder overdrachtstijd bij het migreren van een subset van een opslagplaats voor inhoud door AzCopy te gebruiken om alleen de vereiste blob-id te kopiëren in plaats van alle blob-id&#39;s te kopiëren.
* Snellere differentiële inhoudsaanvullingen met Oak-upgrade.
* Verbeterde robuustheid door het indexeringsproces te scheiden van het innameproces van de inhoud. Als indexering mislukt, hoeft u de inhoud niet opnieuw in te voeren. Alleen indexering wordt automatisch opnieuw gestart, zodat u veel tijd en moeite bespaart.
