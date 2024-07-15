---
title: Opmerkingen bij de release AEM as a Cloud Service 2023.07.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2023.07.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: 2f787321-f156-480d-bbe8-1a6d04f110c5
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 1%

---

# Opmerkingen bij de release AEM as a Cloud Service 2023.07.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2023.07.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.42 is 6 juli 2023.

### Wat is er nieuw? {#what-is-new-bpa}

* Er zijn meerdere best practices-patronen toegevoegd aan deze versie van de Best Practices Analyzer. Deze omvatten:
   * Configuratie van minimale onderhoudstaken identificeren
   * Langlopende/zware query&#39;s detecteren
   * Een groot aantal workflows voor auteurs detecteren in de status actief of geschaald
   * Configuratie van OSGI Apache-slingertaken detecteren
   * Aangepaste guave-caches detecteren

### Opgeloste problemen {#bug-fixes-bpa}

* BPA werd verbeterd om te voorkomen dat het genereren van rapporten met een hoog aantal bevindingen mislukte vanwege het genereren van rapporten vanwege onvoldoende geheugen.
* BPA is verbeterd op het detecteren van escape-tekens in paden om fouten met het opnemen van inhoud te voorkomen bij het migreren van inhoud naar AEM as a Cloud Service.
