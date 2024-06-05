---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.5.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.5.0
feature: Release Information
exl-id: 1aa49e85-1914-44d9-bcf7-0a1b03926df0
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.5.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.5.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.30 is 1 juni 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het gebruik van aangepaste dialoogwidgets te detecteren en hierover verslag uit te brengen met gebruik van de widgets CoralUI en Klassieke dialoog. Het wordt aanbevolen aangepaste Klassieke Dialoogwidgets om te zetten van ExtJS in CoralUI. De widgets van het dialoogvenster Aangepast koraal moeten worden bijgewerkt naar CoralUI3.
* Mogelijkheid om het gebruik en de versie van Assets Share Commons te detecteren en te rapporteren. Commons 1.x voor het delen van bedrijfsmiddelen wordt niet ondersteund op AEM as a Cloud Service en moet worden bijgewerkt naar 2.x.
* Mogelijkheid om het aantal knooppunten van versies te detecteren en hierover te rapporteren.
* Capaciteit om op de agenten van de douanereplicatie of uit de agenten van de doosreplicatie te ontdekken en te rapporteren die zijn gewijzigd.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA rapporteerde NCC (Niet-compatibele wijzigingen), UMI (Probleem met configuratie van upgrades) en PCX (Complexiteit van pagina)-bevindingen die fout-positieven zijn. Deze zijn opgelost.
* BPA rapporteerde mislukkingen wanneer om het even welke lengte van de knoopnaam meer dan 150 bytes. Dit is gecorrigeerd om dergelijke mislukkingen slechts te ontdekken wanneer de knoop ouderweg gelijk of groter is dan 350 bytes.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v2.0.10 is 2 juni 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* De CTT (Content Transfer Tool) is ontwikkeld om met Cloud Acceleration Manager te werken en het gehele proces voor de overdracht van inhoud te stroomlijnen. CTT richt zich nu op het uitvoeren van inhoud-extracties. De service voor het opnemen van CTT-gegevens is nu geïntegreerd in Cloud Acceleration Manager. De voordelen die door deze ontwikkeling worden geboden zijn:
   * Zelfbediening om een migratieset één keer uit te pakken en tegelijkertijd in meerdere omgevingen in te voeren.
   * Verbeterde gebruikerservaring dankzij betere laadstatussen, instructies en foutafhandeling.
   * Logbestanden voor inname blijven bestaan en zijn altijd beschikbaar voor probleemoplossing.

## Cloud Acceleration Manager {#cam-release}

### Releasedatum {#release-date-cam}

De releasedatum voor Cloud Acceleration Manager is 2 juni 2022.

### Wat is er nieuw? {#what-is-new-cam}

* Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om inhoudoverdrachten te starten en te beheren om inhoud van een AEM (On-premise of Adobe Managed Services) van een klant te verplaatsen naar AEM as a Cloud Service als onderdeel van een migratieproject. Zie [Inhoudsoverdrachtkaart gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-implementation-phase.html#content-transfer) voor meer informatie .
