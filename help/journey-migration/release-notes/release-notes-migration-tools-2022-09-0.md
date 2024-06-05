---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.9.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.9.0
feature: Release Information
exl-id: 581370ba-e3e8-487e-af83-a1eacbda2763
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 1%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.9.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.9.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.34 is 12 september 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* BPA kan nu ontdekken en rapporteren of de klant een configuratie van het douaneregistreerapparaat heeft toegevoegd. AEM as a Cloud Service ondersteunt geen aangepaste logbestanden. Alle logbestanden moeten naar `error.log`
* BPA kan nu over de verschillende binaire MIME types rapporteren die in de bewaarplaats van de klant aanwezig zijn en tellingen verbonden aan hen.

### Opgeloste problemen {#bug-fixes-bpa}

* De BPA UI had teruggevende kwesties toen het tonen van een groot aantal bevindingen onder één enkel patroon. Dit is opgelost.
* BPA rapporteerde sommige bevindingen onjuist als niet-compatibele wijzigingen met kritieke ernst. Dit is opgelost.
