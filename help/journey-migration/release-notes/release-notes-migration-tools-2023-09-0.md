---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2023.09.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2022.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
source-git-commit: c89ca7320d8f31d2545cadf98f39e577337b8918
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 3%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service release 2023.09.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.09.0.

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v3.0.0 is 7 september 2023.

### Wat is er nieuw? {#what-is-new-ctt}

Het gereedschap Inhoud overbrengen is aanzienlijk verbeterd en biedt de volgende voordelen:
* Minder overdrachtstijd bij het migreren van een subset van een opslagplaats voor inhoud door AzCopy te gebruiken om alleen de vereiste blob-id&#39;s te kopiëren in plaats van alle blob-id&#39;s te kopiëren
* Snellere differentiële inhoudverhogingen gebruikend eiken-verbetering
* Verbeterde robuustheid door het indexeringsproces te scheiden van het innameproces van de inhoud. Als de indexering mislukt, hoeft de inhoud niet opnieuw te worden ingevoerd. Alleen indexering wordt automatisch opnieuw gestart en bespaart aanzienlijke tijd en moeite
