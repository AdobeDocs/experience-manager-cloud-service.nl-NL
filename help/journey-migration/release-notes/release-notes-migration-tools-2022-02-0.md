---
title: Opmerkingen bij de release AEM as a Cloud Service 2022.2.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2022.2.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: b1cd871d-c71e-4902-a97e-2c859f6a4da4
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 1%

---

# Opmerkingen bij de release AEM as a Cloud Service 2022.2.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2022.2.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.24 is 1 februari 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het aantal elementen met en zonder slimme tags te detecteren en hierover te rapporteren.
* Mogelijkheid om de gebruikte versie van de Core Component te detecteren en hierover verslag uit te brengen.
* Mogelijkheid om het type bronlaag (Auteur of Publish) waar BPA werd uitgevoerd op te sporen en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA-logica voor grootteaanpassing is sneller en efficiënter gemaakt.
* In sommige scenario&#39;s, verhoogde BPA niet de geanalyseerde telling toen het in werking werd gesteld. Dit is opgelost.

## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.8.6 is 3 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Inhoudsvalidatie - Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Als u deze functie wilt gebruiken, schakelt u deze in in de `System Console` AEM van de bronomgeving. Zie [ Bevaliderende Inhoudsoverdrachten - Begonnen het Worden ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=nl-NL#getting-started) voor meer details.

### Opgeloste problemen {#bug-fixes-ctt}

* Sommige gebruikers zijn niet toegewezen omdat de toewijzing van de gebruiker hoofdlettergevoelig was. Dit is opgelost. Gebruikerstoewijzing is niet langer hoofdlettergevoelig.
