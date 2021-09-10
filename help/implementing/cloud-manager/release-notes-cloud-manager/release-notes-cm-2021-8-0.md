---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.8.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2021.8.0
feature: Release Information
source-git-commit: 11910316836b33e886aeba84f89d1b2eebfe7de2
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2021.8.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2021.8.0.

>[!NOTE]
>Om de huidige Nota&#39;s van de Versie voor Adobe Experience Manager als Cloud Service te zien, klik [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2021.8.0 is 12 augustus 2021.

### Wat is er nieuw? {#what-is-new}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar worden gesteld.
Zie [SLA Rapportering](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) om meer te leren.

* Het type en de strengheid van de IndexType en `IndexDamAssetLucene` kwaliteitsregels zijn veranderd. Dit zijn nu beide bugs van Blocker *serverity*.

* De nieuwe de kwaliteitsregels van de indexkwaliteit van de eikel zijn geïntroduceerd om asynchrone en tika configuraties te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de interface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes}

* Update Available status should not be displayed when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met zeer lange namen.

* Af en toe, wanneer een pijpleiding tweemaal om één of andere reden wordt teweeggebracht, resulteert het in één van de uitvoeringen die met *geen status van de pijpleidingsuitvoering kan bijwerken* fout.
