---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.10.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2021.10.0
feature: Release Information
exl-id: null
source-git-commit: c7cee58a465887b15994a963448fcba8d546673a
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 2%

---


# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.10.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2021.10.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.6.0 is 4 oktober 2021.

### Wat is er nieuw? {#what-is-new-ctt-oct}

* Verbeterd gereedschap voor het toewijzen van gebruikers met een vereenvoudigde gebruikerservaring, inclusief de volgende functies die hieronder worden vermeld. Raadpleeg voor meer informatie [Gebruikerstoewijzing gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Verbinding met de gebruikersbeheerAPI testen voordat de gebruikerstoewijzing wordt uitgevoerd
   * Fouten op een fraaie manier overslaan en doorgaan met de gebruikerstoewijzingsactiviteit
   * Toewijzing van gebruiker mislukt niet meer als **Toegangstoken** verloopt na 24 uur. Toewijzing van gebruikers kan opnieuw worden uitgevoerd vanaf het punt waarop het laatst is gestopt.

* Om de robuustheid van het hulpmiddel van de Overdracht van de Inhoud te verhogen, kan de inhoud aan of instantie Auteur of Publish tegelijkertijd worden opgenomen. Zie [Aan de slag met het gereedschap Inhoud overbrengen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) voor meer informatie .

* Wanneer versies worden opgenomen, wordt het pad `/var/audit` wordt automatisch opgenomen om auditgebeurtenissen te migreren.


## Cloud Acceleration Manager {#cam-release}

### Releasedatum {#release-date-cam}

De releasedatum voor Cloud Acceleration Manager is 25 oktober 2021.

### Wat is er nieuw? {#what-is-new-cam}

Cloud Acceleration Manager biedt gebruikers nu de mogelijkheid om historische BPA-rapporten weer te geven in een Trendline-rapport. Met dit rapport kunnen gebruikers de voortgang die ze maken bekijken in een eenvoudige grafische weergave. Zie [Trendline weergeven gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#trendline-view-cam) voor meer informatie .

### Releasedatum {#release-date-october-cam}

De releasedatum voor Cloud Acceleration Manager is 4 oktober 2021.

### Nieuwe functies {#what-is-new-cam-oct}

Met Cloud Acceleration Manager kunnen gebruikers de BPA-rapporten nu bekijken in een afdrukbaar voorbeeld, zodat ze eenvoudig kunnen afdrukken of afdrukken naar PDF, zodat ze gemakkelijk kunnen worden gedeeld. Zie Stap 6 en 7 in [De kaart van de Analyse van Beste praktijken gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa-latest}

De releasedatum voor de analyse van best practices v2.1.20 is 5 oktober 2021.

### Wat is er nieuw? {#what-is-new-bpa-oct}

* Mogelijkheid om de lengte van knoopnamen te detecteren en te rapporteren.

* Mogelijkheid om de totale indexgrootte op te sporen en te rapporteren.

* Mogelijkheid om elementen te detecteren en te rapporteren waarvoor de oorspronkelijke uitvoering ontbreekt.