---
title: Opmerkingen bij de release AEM as a Cloud Service 2024.09 voor migratiehulpprogramma's
description: Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2024.09.0
feature: Release Information
exl-id: 52709511-eab2-47a7-8bea-1b707cd568a1
role: Admin
source-git-commit: 0c16f264826a46907afc33c91a021e7696f5b7a8
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 3%

---

# Release-aantekeningen voor migratiehulpmiddelen in AEM as a Cloud Service Release 2024.09.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2024.09.0.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor het gereedschap Inhoud overbrengen v3.0.20 is 28 augustus 2024.

### Wat is er nieuw? {#what-is-new-ctt}

* Gebruikers worden niet meer opgenomen in deze release en daarom is de optionele functie voor het toewijzen van gebruikers verwijderd.
* Er is een OSGI config-optie toegevoegd om de migratie van hoofden tijdens extractie en opname uit te schakelen of in te schakelen (de standaardinstelling is om deze optie in te schakelen)

### Bugfixes {#bug-fixes-ctt}

* CTT werd verbeterd om een fout te verhinderen terwijl het unprotect van een geheime sleutel in azcopy config
* CTT handelt nu netjes eventuele fouten af tijdens het kopiëren van AzCopy-logbestanden in de validatiefase
* Logboekmap van azcopy wijzigen die is gemaakt tijdens het extractieproces

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.52 is 4 september 2024

### Wat is er nieuw? {#what-is-new-bpa}

* Er is een nieuw patroon geïntroduceerd voor het detecteren van op JCR gebaseerde gebeurtenissen in AEM

### Bugfixes {#bug-fixes-bpa}

* Correctie van fout-positieven
* Verbeterde robuustheid om omgeleide reactie van verzender te behandelen
* Correctie van niet-rapportage van NCC-bevinding voor alle talen onder /apps/wcm/core/resources/languages/
* Hiermee wordt een controle toegevoegd om te detecteren of een eigenschap van een knooppunt geen waarden heeft

