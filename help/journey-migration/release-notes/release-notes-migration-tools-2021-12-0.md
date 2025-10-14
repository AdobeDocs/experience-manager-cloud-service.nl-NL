---
title: Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
role: Admin
source-git-commit: 6719e0bcaa175081faa8ddf6803314bc478099d7
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---

# Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>
>Zie [&#x200B; Huidige Nota&#39;s van de Versie voor Adobe Experience Manager as a Cloud Service &#x200B;](/help/release-notes/release-notes-cloud/release-notes-current.md) voor de recentste versienota&#39;s.

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.2 is 1 december 2021.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om de gebruikte versie van ACS-gemeenschappelijk te detecteren en te rapporteren.
* Mogelijkheid om het aantal gebruikers en subgroepen in een groep op te sporen en te rapporteren.
* Mogelijkheid om waarden van knoopeigenschappen in MongoDB te detecteren en te rapporteren die groter zijn dan 16 MB.

### Opgeloste problemen {#bug-fixes-bpa}

* Detection of Foundation components was verfijnd om valse negatieven te verminderen.
* Voor AEM Forms-klanten is het BPA-bericht dat `EMAIL_PDF_SUBMIT_ACTION` niet beschikbaar is op AEM as a Cloud Service opgelost.


## Inhoud overbrengen {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.7.10 is 8 december 2021.

### Wat is er nieuw? {#what-is-new-ctt}

* Wissel dat aan de innamefase in het Hulpmiddel van de Overdracht van de Inhoud wordt toegevoegd om gebruikers toe te staan om [&#x200B; pre-exemplaar &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=nl-NL) tijdens opname onbruikbaar te maken. Voor een optimale inname moet de voorkopie tijdens inname worden uitgeschakeld voor kleine migratiesets of als er sinds de laatste inname slechts een paar blobs zijn toegevoegd.
* Gebruikerstoewijzing bijgewerkt om de verbeterde gebruikersbeheer-API te gebruiken waarmee 2000 gebruikers tegelijk kunnen worden opgehaald, hetgeen de prestaties aanzienlijk verbetert.
