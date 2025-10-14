---
title: DNS-recordstatus controleren
description: Leer hoe te bepalen of uw DNS montages behoorlijk gebruikend Cloud Manager worden opgelost.
exl-id: 76ca1584-e21d-4e3a-a08a-82b2779167cf
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# DNS-recordstatus controleren {#check-dns-record-status}

Leer hoe te bepalen of uw DNS montages behoorlijk gebruikend Cloud Manager worden opgelost.

## Status van DNS-records {#status}

Een naam van het douanedomein kan geen levend verkeer dienen tot DNS correct oplost. In Cloud Manager kunt u bepalen of uw domeinnaam correct wordt omgezet in uw AEM as a Cloud Service-website.

## Vereisten {#requirements}

Voldoe aan deze vereisten voordat u de status van een DNS-record controleert met Cloud Manager.

U moet reeds de DNS montages voor uw naam van het douanedomein zoals die in [&#x200B; wordt beschreven een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) hebben gevormd.

## DNS-recordstatus controleren {#how-to}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan het **scherm van Milieu&#39;s** van de **pagina van het Overzicht**.

1. Klik **Montages van het Domein** in het linkerzijmenu.

1. Klik het **pictogram van de Status** voor de domeinnaam.

Cloud Manager voert een DNS raadpleging voor uw domeinnaam uit en toont het [&#x200B; huidige status &#x200B;](#statuses).

Cloud Manager activeert automatisch een DNS-zoekopdracht wanneer uw aangepaste domeinnaam voor het eerst is geverifieerd en geïmplementeerd. Voor verdere pogingen, moet u actief selecteren **opnieuw oplossen** pictogram naast de status.

## DNS-statussen in Cloud Manager {#statuses}

Een aangepast domein kan een van de volgende statussen in Cloud Manager hebben.

| Status | Beschrijving |
| --- | --- |
| DNS-status niet gedetecteerd | DNS status wordt niet ontdekt tot uw naam van het douanedomein met succes wordt geverifieerd en opgesteld. Deze status wordt ook waargenomen wanneer uw naam van het douanedomein in het proces van schrapping is. |
| DNS wordt onjuist omgezet | Deze status geeft aan dat de DNS-recordconfiguratie niet is opgelost of onjuist is. Zie [&#x200B; een naam van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) toevoegen om meer te leren.<br> wanneer klaar, moet u het **opnieuw oplossen** pictogram naast de status selecteren. |
| DNS-resolutie wordt uitgevoerd | De resolutie is in uitvoering. Deze status wordt typisch gezien nadat u **selecteert los opnieuw** pictogram naast de status op. |
| DNS lost correct op | Uw DNS-instellingen zijn correct geconfigureerd. Uw site is bestemd voor bezoekers. |

## Volgende stappen {#next-steps}

U hebt met succes uw douanedomein voor gebruik met Cloud Manager gevormd. Zie het document [&#x200B; de namen van het douanedomein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md) voor details op hoe te om uw namen van het douanedomein te beheren gebruikend Cloud Manager.
