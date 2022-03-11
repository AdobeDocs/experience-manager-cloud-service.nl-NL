---
title: DNS-recordstatus controleren
description: DNS-recordstatus controleren
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
source-git-commit: d37193833d784f3f470780b8f28e53b473fd4e10
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# DNS-recordstatus controleren {#check-dns-record-status}

U kunt bepalen of uw domeinnaam correct aan uw AEM as a Cloud Service website door het pictogram van de Status voor het DNS verslag van de lijst op de Milieu&#39;s van de pagina van de Montages van het Domein te klikken wordt opgelost.

Cloud Manager zal automatisch een DNS raadpleging teweegbrengen wanneer uw Naam van het Domein van de Douane eerst met succes wordt geverifieerd en wordt opgesteld. Voor volgende pogingen moet u actief de optie **opnieuw oplossen** naast de status.

Cloud Manager voert een DNS-zoekopdracht voor uw domeinnaam uit en geeft een van de volgende statusberichten weer:

* **DNS-status niet gedetecteerd**
DNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld. Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost onjuist op**
Dit wijst erop dat één van beide DNS archiefconfiguratie niet heeft opgelost/op nog gewezen of onjuist is.

   >[!NOTE]
   >U moet één van beide vormen `CNAME` of `A-record` door de desbetreffende instructies te volgen. Zie DNS-instellingen configureren voor meer informatie. Wanneer u klaar bent, moet u de optie **opnieuw oplossen** naast de status.

* **DNS-resolutie in uitvoering**
De resolutie is in uitvoering. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw oplossen&quot; naast de status hebt geselecteerd.

* **DNS lost correct op**
Uw DNS-instellingen zijn correct geconfigureerd. Uw site is bestemd voor bezoekers.
