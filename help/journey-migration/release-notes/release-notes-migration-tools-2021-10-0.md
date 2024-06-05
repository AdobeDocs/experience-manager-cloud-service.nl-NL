---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.10.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.11.0
feature: Release Information
exl-id: 6b1caa63-dcb0-4c48-ab2c-fd72617abf13
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 1%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.10.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Als u de huidige opmerkingen bij de release voor Adobe Experience Manager as a Cloud Service wilt weergeven, klikt u op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html).

## Cloud Acceleration Manager {#cam-release}

### Releasedatum {#release-date-cam}

De releasedatum voor Cloud Acceleration Manager is 25 oktober 2021.

### Wat is er nieuw? {#what-is-new-cam}

Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om historische BPA-rapporten weer te geven in een Trendline-rapport. Met dit rapport kunnen gebruikers de voortgang die ze maken bekijken in een eenvoudige grafische weergave. Zie [Trendline weergeven gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#trendline-view-cam) voor meer informatie .

### Releasedatum {#release-date-october-cam}

De releasedatum voor Cloud Acceleration Manager is 4 oktober 2021.

### Nieuwe functies {#what-is-new-cam-oct}

Met Cloud Acceleration Manager kunnen gebruikers de BPA-rapporten nu bekijken in een afdrukbaar voorbeeld, zodat ze eenvoudig kunnen afdrukken of afdrukken naar PDF, zodat ze gemakkelijk kunnen worden gedeeld. Zie Stap 6 en 7 in [De kaart van de Analyse van Beste praktijken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#best-practices-analysis).


## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.6.0 is 4 oktober 2021.

### Wat is er nieuw? {#what-is-new-ctt-oct}

* Verbeterd gereedschap voor het toewijzen van gebruikers met een vereenvoudigde gebruikerservaring, inclusief de volgende functies die hieronder worden vermeld. Zie voor meer informatie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html).
   * Verbinding met de gebruikersbeheerAPI testen voordat de gebruikerstoewijzing wordt uitgevoerd
   * Fouten op een fraaie manier overslaan en doorgaan met de gebruikerstoewijzingsactiviteit
   * Toewijzing van gebruiker mislukt niet meer als **Toegangstoken** verloopt na 24 uur. Toewijzing van gebruikers kan opnieuw worden uitgevoerd vanaf het punt waar de gebruikerstoewijzing het laatst is gestopt.

* Om de robuustheid van het hulpmiddel van de Overdracht van de Inhoud te verhogen, kan de inhoud aan of instantie Auteur of Publish tegelijkertijd worden opgenomen. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html) voor meer informatie .

* Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.20 is 5 oktober 2021.

### Wat is er nieuw? {#what-is-new-bpa-oct}

* Mogelijkheid om de lengte van knoopnamen te detecteren en te rapporteren.

* Mogelijkheid om de totale indexgrootte op te sporen en te rapporteren.

* Mogelijkheid om elementen te detecteren en te rapporteren waarvoor de oorspronkelijke uitvoering ontbreekt.
