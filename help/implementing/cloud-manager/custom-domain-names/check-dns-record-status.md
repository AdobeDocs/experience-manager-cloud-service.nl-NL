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

Cloud Manager zal automatisch een DNS raadpleging teweegbrengen wanneer uw Naam van het Domein van de Douane eerst met succes wordt geverifieerd en wordt opgesteld. Voor verdere pogingen, moet u actief **oplossen opnieuw** pictogram naast de status selecteren.

Cloud Manager voert een DNS-zoekopdracht voor uw domeinnaam uit en geeft een van de volgende statusberichten weer:

* **DNS status not**
detectedDNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld. Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost**
Incorrect opThis wijst erop dat of DNS archiefconfiguratie nog niet heeft opgelost/over gewezen of onjuist is.

   >[!NOTE]
   >U moet of `CNAME` of `A-record` door de overeenkomstige instructies te volgen vormen. Zie DNS-instellingen configureren voor meer informatie. Wanneer klaar, moet u **oplossen opnieuw** pictogram naast de status selecteren.

* **DNS-resolutie In**
ProgressResolution wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw oplossen&quot; naast de status hebt geselecteerd.

* **DNS lost**
correct op Uw DNS montages worden behoorlijk gevormd. Uw site is bestemd voor bezoekers.
