---
title: Opmerkingen bij de release Cloud Manager 2023.4.0 in Adobe Experience Manager as a Cloud Service
description: Dit zijn de opmerkingen bij de release voor Cloud Manager 2023.4.0 in AEM as a Cloud Service.
feature: Release Information
exl-id: 9c73d7ab-c2c2-4803-a07b-e9054220c6b2
source-git-commit: be39b09b609cccff916db462af9a84149d23a698
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 1%

---


# Opmerkingen bij de release Cloud Manager 2023.4.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

Op deze pagina worden de opmerkingen bij de release 2023.4.0 van Cloud Manager in AEM as a Cloud Service gedocumenteerd.

>[!NOTE]
>
>Zie [deze pagina](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de actuele releaseopmerkingen voor Adobe Experience Manager as a Cloud Service.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager versie 2023.4.0 in AEM as a Cloud Service is 13 april 2023. De volgende release is gepland voor 11 mei 2023.

## Wat is er nieuw? {#what-is-new}

* [Het AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) is bijgewerkt naar versie 41.

## Opgeloste problemen {#bug-fixes}

* Wanneer een [certificaat](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) verloopt, [domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) en [IP-lijsten van gewenste personen](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) gekoppeld aan het certificaat wordt niet meer verwijderd uit de CDN.  In dergelijke gevallen, zal de plaats bereikbaar blijven.
* De gebruikersinterface van Cloud Manager biedt meer zichtbare voorafgaande waarschuwingen dat de [SSL-certificaat](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md) bijna verlopen.
* Er is een zeldzame situatie vastgesteld waarin klanten geen nieuwe omgeving konden creëren of een omgeving konden verwijderen.
