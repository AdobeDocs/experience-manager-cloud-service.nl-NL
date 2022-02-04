---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.2.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.2.0
feature: Release Information
source-git-commit: 8876702f1a172282fd1ff46387ade2a45e187fed
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 2%

---


# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2022.2.0 {#release-notes}

Deze pagina schetst de Nota&#39;s van de Versie voor de Hulpmiddelen van de Migratie in AEM as a Cloud Service 2022.2.0.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.24 is 1 februari 2022.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om het aantal elementen met en zonder slimme tags te detecteren en hierover te rapporteren.
* Mogelijkheid om de gebruikte versie van de Core Component te detecteren en hierover verslag uit te brengen.
* Mogelijkheid om het type bronlaag (Auteur of Publiceren) waar BPA is uitgevoerd, op te sporen en te rapporteren.

### Opgeloste problemen {#bug-fixes-bpa}

* BPA-logica voor grootteaanpassing is sneller en efficiënter gemaakt.
* In sommige scenario&#39;s, verhoogde BPA niet de geanalyseerde telling toen het in werking werd gesteld. Dit is opgelost.

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.8.6 is 3 februari 2022.

### Wat is er nieuw? {#what-is-new-ctt}

* Inhoudsvalidatie - Gebruikers kunnen betrouwbaar bepalen of alle inhoud die met het gereedschap Inhoud overbrengen is uitgepakt, is opgenomen in de doelinstantie. Als u deze functie wilt gebruiken, moet u deze inschakelen in het dialoogvenster `System Console` van de bron AEM omgeving. Zie [Inhoudsoverdrachten valideren - Aan de slag](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/validating-content-transfers.html?lang=en#getting-started) voor meer informatie .

### Opgeloste problemen {#bug-fixes-ctt}

* Sommige gebruikers zijn niet toegewezen omdat de toewijzing van de gebruiker hoofdlettergevoelig was. Dit is opgelost. Toewijzing van gebruikers is niet langer hoofdlettergevoelig.

