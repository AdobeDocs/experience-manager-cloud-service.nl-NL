---
title: Een aangepaste domeinnaam toevoegen
description: Een aangepaste domeinnaam toevoegen
translation-type: tm+mt
source-git-commit: 9d5f7d633ac8dfaadf315e85666479c87a0afa04
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---


# Een aangepaste domeinnaam {#adding-cdn} toevoegen

Een gebruiker moet een Business Owner of Deployment Manager zijn om een aangepaste domeinnaam in Cloud Manager te kunnen toevoegen.

## Belangrijke overwegingen {#important-considerations}

* Voordat u een aangepaste domeinnaam kunt toevoegen, moet u een geldig SSL-certificaat met de aangepaste domeinnaam op uw programma installeren. Raadpleeg [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie.

* Er kan slechts één domeinnaam tegelijk worden toegevoegd. Gebruikers kunnen echter jokertekens toevoegen, bijvoorbeeld `*.wknd.com` als een domeinnaam, en dat zou betekenen dat meerdere subdomeinen met één TXT-record kunnen worden gehost.

* Elke Cloud Manager-omgeving kan maximaal 100 aangepaste domeinen per omgeving hosten. Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.

## Een aangepaste domeinnaam toevoegen vanaf de pagina met domeininstellingen {#adding-cdn-settings}

Voer de onderstaande stappen uit om een aangepaste domeinnaam toe te voegen van de pagina Domeininstellingen:

1. Navigeer naar de pagina Domeininstellingen van de **pagina Omgevingen**

1. Selecteer **Aangepaste domeinnaam toevoegen** om de wizard Aangepaste domeinnaam toevoegen te starten.

1. Voer de aangepaste domeinnaam in.

   >[!NOTE]
   >Neem `http://`, `https://` of spaties niet op wanneer u in uw domein gaat.

1. Selecteer het milieu waarvan de Publish dienst met de domeinnaam zal worden geassocieerd.

1. Selecteer het SSL-certificaat in de keuzelijst en selecteer Doorgaan.

1. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Raadpleeg [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie.
Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen.

1. Selecteer Doorgaan.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en Gedistribueerd**.
1. Navigeer naar Status aangepaste domeinnaam controleren voor meer informatie over verschillende statussen en over het adres ervan.

   >[!NOTE]
   >DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.

## Een aangepaste domeinnaam uit de pagina Omgevingen toevoegen {#adding-cdn-environments}

1. Navigeer naar de pagina Omgevingsdetails voor de omgeving die u wilt gebruiken.
1. Gebruik de invoervelden boven aan de tabel Domeinnamen om de aangepaste domeinnaam SSL-certificaat in te dienen. Selecteer vervolgens Toevoegen.
1. Hiermee wordt de wizard Aangepaste domeinnaam toevoegen gestart, waarbij de naam van de omgeving vooraf is ingevuld.
1. Voer de aangepaste domeinnaam in. Opmerking: Neem `http://`, `https://`, of geen ruimten op wanneer het ingaan in uw domein. Selecteer Doorgaan.
1. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Raadpleeg [Domeinverificatie](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen.

1. Selecteer Doorgaan.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en Gedistribueerd**.

Op dit punt is uw aangepaste domeinnaam klaar om te worden getest en is een `CNAME` om ernaar te wijzen. Verwijs naar de Status van de Naam van het Domein om meer over diverse statussen en te leren hoe te om te richten.

>[!NOTE]
>DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.
