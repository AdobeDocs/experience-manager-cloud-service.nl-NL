---
title: DNS-recordstatus controleren
description: Leer hoe te om te bepalen of uw DNS montages behoorlijk door de Manager van de Wolk te gebruiken oplossen.
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

In Cloud Manager kunt u bepalen of uw domeinnaam correct wordt omgezet in uw AEM as a Cloud Service website.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Klikken **Domeininstellingen** in het linkernavigatievenster.

1. Klik op de knop **Status** pictogram voor de domeinnaam.

Cloud Manager voert een DNS raadpleging voor uw domeinnaam uit en toont één van de volgende statusberichten.

* **DNS-status niet gedetecteerd** - DNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld.

   * Deze status wordt ook waargenomen wanneer uw naam van het Domein van de Douane in het proces van schrapping is.

* **DNS lost onjuist op** - Dit wijst erop dat of de DNS archiefconfiguratie niet heeft opgelost of onjuist is.

   * Zie [DNS-instellingen configureren](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) voor meer informatie.
   * Wanneer u klaar bent, moet u de optie **Opnieuw oplossen** naast de status.

* **DNS-resolutie in uitvoering** - De resolutie is in behandeling.

   * Deze status wordt meestal weergegeven nadat u de optie **Opnieuw oplossen** naast de status.

* **DNS lost correct op** - Uw DNS-instellingen zijn correct geconfigureerd.

   * Uw site is bestemd voor bezoekers.

Cloud Manager activeert automatisch een DNS-zoekopdracht wanneer uw aangepaste domeinnaam voor het eerst is geverifieerd en geïmplementeerd. Voor volgende pogingen moet u actief de optie **Opnieuw oplossen** naast de status.
