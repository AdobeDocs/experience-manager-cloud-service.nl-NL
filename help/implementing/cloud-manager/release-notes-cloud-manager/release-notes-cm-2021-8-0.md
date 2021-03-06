---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.8.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.8.0
feature: Release Information
exl-id: cf1d5c4f-404a-4ced-90f2-273c710adc0f
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2021.8.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.8.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.8.0 is 12 augustus 2021.

### Wat is er nieuw? {#what-is-new}

* Klanten van Cloud Servicen kunnen nu SLA-rapporten (Service Level Agreement) weergeven in Cloud Manager. Dit zal de komende maanden geleidelijk beschikbaar worden gesteld.
Zie [SLA-rapportage](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/sla-reporting.html) voor meer informatie.

* Het type en de ernst van het IndexType en `IndexDamAssetLucene` de kwaliteitsvoorschriften zijn gewijzigd . Dit zijn nu beide bugs van Blocker *seriteit*.

* De nieuwe de kwaliteitsregels van de indexkwaliteit van de eikel zijn geïntroduceerd om asynchrone en tika configuraties te behandelen.

* Verhoog de maximale SSL-certs per programma tot 50.

* Self-service mogelijkheid om gebruikers in staat te stellen meerdere opslagruimten te maken en te beheren via de interface van Cloud Manager.

* SonarQube leest onnodig de gegevens uit de Git-geschiedenis. Op grote codebasis, zou dit tot een onnodige bouwstijlprestaties kunnen leiden.

* Er is nu een API beschikbaar om het Geweven gebiedsdeelheidsgeheime voorgeheugen per pijpleiding ongeldig te maken.

* De versie van het AEM Project Archetype dat wordt gebruikt door Cloud Manager is bijgewerkt naar versie 29.

### Opgeloste problemen {#bug-fixes}

* Update Available status should not be displayed when the latest release is less than the current release.

* De eerste instapweigering mislukte voor nieuwe organisaties met zeer lange namen.

* Af en toe, wanneer een pijpleiding tweemaal om één of andere reden in werking wordt gesteld, resulteert het in één van de terechtstellingen die nalaten *kan uitvoerstatus van pijpleiding niet bijwerken* fout.
