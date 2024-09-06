---
title: DNS-recordstatus controleren
description: Leer hoe te om te bepalen of uw DNS montages behoorlijk door Cloud Manager te gebruiken oplossen.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---


# DNS-recordstatus controleren {#check-dns-record-status}

Leer hoe te om te bepalen of uw DNS montages behoorlijk door Cloud Manager te gebruiken oplossen.

## Status van DNS-records {#status}

Een naam van het douanedomein kan geen levend verkeer dienen tot DNS correct oplost. In Cloud Manager kunt u bepalen of uw domeinnaam correct wordt omgezet in uw AEM as a Cloud Service-website.

## Vereisten {#requirements}

U moet aan deze vereisten voldoen voordat u een DNS-recordstatus kunt controleren met Cloud Manager.

* U moet reeds de DNS montages voor uw naam van het douanedomein zoals die in het document [ wordt beschreven Vormend DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) gevormd hebben.

## DNS-recordstatus controleren {#how-to}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkernavigatievenster.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Cloud Manager voert een DNS raadpleging voor uw domeinnaam uit en toont het [ huidige status ](#statuses).

Cloud Manager activeert automatisch een DNS-zoekopdracht wanneer uw aangepaste domeinnaam voor het eerst is geverifieerd en geïmplementeerd. Voor verdere pogingen, moet u actief selecteren **opnieuw oplossen** pictogram naast de status.

## DNS-statussen in Cloud Manager {#statuses}

Een aangepast domein kan een van de volgende statussen in Cloud Manager hebben.

* **DNS status niet ontdekt** - DNS status zal niet worden ontdekt tot uw naam van het douanedomein met succes is geverifieerd en opgesteld.

   * Deze status wordt ook waargenomen wanneer uw naam van het douanedomein in het proces van schrapping is.

* **DNS lost verkeerd** op - dit wijst erop dat of de DNS archiefconfiguratie niet heeft opgelost of onjuist is.

   * Zie [ Vormend DNS Montages ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) om meer te leren.
   * Wanneer klaar, moet u **selecteren opnieuw oplost** pictogram naast de status.

* **DNS Bezig Resolutie** - de resolutie is lopend.

   * Deze status wordt typisch gezien nadat u **selecteert los opnieuw** pictogram naast de status op.

* **DNS lost Correct** op - Uw DNS montages worden behoorlijk gevormd.

   * Uw site is bestemd voor bezoekers.

## Volgende stappen {#next-steps}

Gefeliciteerd! U hebt met succes uw douanedomein voor gebruik met Cloud Manager gevormd. Gelieve te zien het document [ het Leiden Namen van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) voor details op hoe te om uw namen van het douanedomein te beheren gebruikend Cloud Manager.
