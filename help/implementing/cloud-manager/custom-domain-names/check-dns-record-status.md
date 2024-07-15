---
title: DNS-recordstatus controleren
description: Leer hoe te om te bepalen of uw DNS montages behoorlijk door Cloud Manager te gebruiken oplossen.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# DNS-recordstatus controleren {#check-dns-record-status}

In Cloud Manager kunt u bepalen of uw domeinnaam correct wordt omgezet in uw AEM as a Cloud Service-website.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkernavigatievenster.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Cloud Manager voert een DNS raadpleging voor uw domeinnaam uit en toont één van de volgende statusberichten.

* **DNS status niet ontdekt** - DNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld.

   * Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost verkeerd** op - dit wijst erop dat of de DNS archiefconfiguratie niet heeft opgelost of onjuist is.

   * Zie [ Vormend DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) om meer te leren.
   * Wanneer klaar, moet u **selecteren opnieuw oplost** pictogram naast de status.

* **DNS Bezig Resolutie** - de resolutie is lopend.

   * Deze status wordt typisch gezien nadat u **selecteert los opnieuw** pictogram naast de status op.

* **DNS lost Correct** op - Uw DNS montages worden behoorlijk gevormd.

   * Uw site is bestemd voor bezoekers.

Cloud Manager activeert automatisch een DNS-zoekopdracht wanneer uw aangepaste domeinnaam voor het eerst is geverifieerd en geïmplementeerd. Voor verdere pogingen, moet u actief selecteren **opnieuw oplossen** pictogram naast de status.
