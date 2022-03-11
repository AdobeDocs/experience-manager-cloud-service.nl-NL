---
title: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.12.0
description: Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.12.0
feature: Release Information
exl-id: 4155e1c0-cd40-4cbc-9d6c-b106d68a2db5
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 2%

---

# Opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service versie 2021.12.0 {#release-notes}

Deze pagina schetst de opmerkingen bij de release voor migratiehulpmiddelen in AEM as a Cloud Service 2021.12.0.

>[!NOTE]
>Klik op [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## Analysator van best practices {#bpa-release}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.22 is 1 december 2021.

### Wat is er nieuw? {#what-is-new-bpa}

* Mogelijkheid om de gebruikte versie van ACS-gemeenschappelijk te detecteren en te rapporteren.
* Mogelijkheid om het aantal gebruikers en subgroepen in een groep op te sporen en te rapporteren.
* Mogelijkheid om waarden van knoopeigenschappen in MongoDB te detecteren en te rapporteren die groter zijn dan 16 MB.

### Opgeloste problemen {#bug-fixes-bpa}

* Detection of Foundation components was verfijnd om valse negatieven te verminderen.
* Voor AEM Forms-klanten geldt dat BPA-berichten `EMAIL_PDF_SUBMIT_ACTION` niet beschikbaar zijn op AEM as a Cloud Service is opgelost.


## De tool Content Transfer {#ctt-release}

### Releasedatum {#release-date-ctt}

De releasedatum voor Content Transfer Tool v1.7.10 is 8 december 2021.

### Wat is er nieuw? {#what-is-new-ctt}

* In-/uitschakelen van aan de invoerfase in het gereedschap Inhoud overbrengen om gebruikers in staat te stellen [voorkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) tijdens inname. Voor een optimale inname moet de voorkopie tijdens inname worden uitgeschakeld voor kleine migratiesets of als er sinds de laatste inname slechts een paar blobs zijn toegevoegd.
* Gebruikerstoewijzing bijgewerkt om de verbeterde gebruikersbeheer-API te gebruiken waarmee 2000 gebruikers tegelijk kunnen worden opgehaald, hetgeen de prestaties aanzienlijk verbetert.
