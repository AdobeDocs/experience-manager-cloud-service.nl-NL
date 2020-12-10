---
title: DNS-recordstatus controleren
description: DNS-recordstatus controleren
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# DNS-recordstatus {#check-dns-record-status} controleren

U kunt bepalen of uw domeinnaam correct aan uw AEM als website van de Cloud Service door het pictogram van de Status voor het DNS verslag van de lijst op de Milieu&#39;s van de pagina van de Montages van het Domein te klikken oplost.

Cloud Manager zal automatisch een DNS raadpleging teweegbrengen wanneer uw Naam van het Domein van de Douane eerst met succes wordt geverifieerd en wordt opgesteld. Voor verdere pogingen, moet u actief **oplossen opnieuw** pictogram naast de status selecteren.

Cloud Manager voert een DNS-zoekopdracht voor uw domeinnaam uit en geeft een van de volgende statusberichten weer:

* **DNS status not**
detectedDNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld. Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost**
Incorrect opThis wijst erop dat of DNS archiefconfiguratie nog niet heeft opgelost/over gewezen of onjuist is. Een vertegenwoordiger van de Adobe wordt automatisch op de hoogte gesteld.

   >[!NOTE]
   >U moet of `CNAME` of `A-record` door de overeenkomstige instructies te volgen vormen. Zie DNS-instellingen configureren voor meer informatie. Wanneer klaar, moet u **oplossen opnieuw** pictogram naast de status selecteren.

* **DNS-resolutie In**
ProgressResolution wordt uitgevoerd. Deze status wordt meestal weergegeven nadat u het pictogram &quot;Opnieuw oplossen&quot; naast de status hebt geselecteerd.

* **DNS lost**
correct op Uw DNS montages worden behoorlijk gevormd. Uw site is bestemd voor bezoekers.
