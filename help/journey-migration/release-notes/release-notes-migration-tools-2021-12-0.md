---
title: Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma's
description: Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma's
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 1%

---

# Opmerkingen bij de release AEM as a Cloud Service 2021.12.0 voor migratiehulpprogramma&#39;s {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>Om de huidige Nota&#39;s van de Versie voor Adobe Experience Manager as a Cloud Service te zien, klik [ hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

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

* Wissel dat aan de innamefase in het Hulpmiddel van de Overdracht van de Inhoud wordt toegevoegd om gebruikers toe te staan om [ pre-exemplaar ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) tijdens opname onbruikbaar te maken. Voor een optimale inname moet de voorkopie tijdens inname worden uitgeschakeld voor kleine migratiesets of als er sinds de laatste inname slechts een paar blobs zijn toegevoegd.
* Gebruikerstoewijzing bijgewerkt om de verbeterde gebruikersbeheer-API te gebruiken waarmee 2000 gebruikers tegelijk kunnen worden opgehaald, hetgeen de prestaties aanzienlijk verbetert.
