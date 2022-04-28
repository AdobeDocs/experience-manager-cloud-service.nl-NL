---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.4.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.4.0
feature: Release Information
source-git-commit: 87e3291b4a72c24fc6cf8df488df305f1a078ea5
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.4.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.4.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.28 is 22 april 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het gebruik van niet-ondersteunde API&#39;s van Asset Manager te detecteren en hierover verslag uit te brengen. Er zijn vier API&#39;s die niet meer worden ondersteund in AEM as a Cloud Service. Klanten moeten ervoor zorgen dat ze deze API&#39;s niet meer gebruiken en moeten de nieuwe methode voor het uploaden van middelen gebruiken.

* Mogelijkheid om het gebruik van sjablonen voor inhoudsfragmenten te detecteren. Sjablonen voor inhoudsfragmenten worden niet meer ondersteund voor het maken van nieuwe inhoudsfragmenten op AEM as a Cloud Service. Klanten moeten contentfragmentmodellen maken om sjablonen voor inhoudsfragmenten te vervangen.

* Mogelijkheid om activa met meer dan 100 afstammingen onder het metadatknooppunt van het actief in de repository te detecteren. Het wordt aanbevolen om metagegevensknooppunten te verwijderen die niet nodig zijn om de prestaties te verbeteren wanneer mappen met dergelijke elementen worden geladen.

* Mogelijkheid om het gebruikte type gegevensopslag te detecteren en te rapporteren.

* Patroon bijgewerkt voor AEM formulierportal.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde bevindingen voor kerncomponenten in plaats van alleen op klantcomponenten te rapporteren. Dit is opgelost.