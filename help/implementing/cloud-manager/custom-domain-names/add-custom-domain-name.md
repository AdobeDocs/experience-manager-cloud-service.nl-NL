---
title: Een aangepaste domeinnaam toevoegen
description: Een aangepaste domeinnaam toevoegen
translation-type: tm+mt
source-git-commit: 27e96d66d93f2fa0e67e607c75f37efda17a13b7
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 0%

---


# Een aangepaste domeinnaam {#adding-cdn} toevoegen

Een gebruiker moet een Business Owner of Deployment Manager zijn om een aangepaste domeinnaam in Cloud Manager te kunnen toevoegen.

## Belangrijke overwegingen {#important-considerations}

* Voordat u een aangepaste domeinnaam kunt toevoegen, moet u een geldig SSL-certificaat met de aangepaste domeinnaam op uw programma installeren. Raadpleeg [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie.

* Er kan slechts één domeinnaam tegelijk worden toegevoegd. Gebruikers kunnen echter jokertekens toevoegen, bijvoorbeeld `*.wknd.com` als een domeinnaam, en dat zou betekenen dat meerdere subdomeinen met één TXT-record kunnen worden gehost.

* Elke Cloud Manager-omgeving kan maximaal 100 aangepaste domeinen per omgeving hosten.

* Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.

## Een aangepaste domeinnaam toevoegen vanaf de pagina met domeininstellingen {#adding-cdn-settings}

Voer de onderstaande stappen uit om een aangepaste domeinnaam toe te voegen van de pagina Domeininstellingen:

1. Navigeer naar **Environment**-scherm vanaf de pagina **Overzicht**.

1. Klik op **Domeininstellingen** in het linkernavigatiemenu.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klik op **Add Domain** knoop om **Add de dialoogdoos van de Naam van het Domein** te openen.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create2.png)

1. Voer de aangepaste domeinnaam in **Domeinnaam** in.

   >[!NOTE]
   >Neem `http://`, `https://` of spaties niet op wanneer u in uw domein gaat.

1. Selecteer de **Omgeving** waarvan de publicatieservice wordt gekoppeld aan de domeinnaam.

1. Selecteer **Domein SSL Certificaat** van drop-down en selecteer **Doorgaan**.

1. **Het** dialoogvenster Domeinnaam toevoegen wordt weergegeven. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Raadpleeg [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie.
Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen.

1. Klik op **Create**.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en Gedistribueerd**.
Navigeer naar [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over verschillende statussen en hoe u deze kunt adresseren.

   >[!NOTE]
   >DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.

## Een aangepaste domeinnaam uit de pagina Omgevingen toevoegen {#adding-cdn-environments}

1. Navigeer naar de pagina Environment Detail voor de omgeving van belang.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de invoervelden boven aan de tabel Domeinnamen om de aangepaste domeinnaam te verzenden en selecteer het SSL-certificaat in de vervolgkeuzelijst. Klik op **+ toevoegen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Controleer de velden in het dialoogvenster **Domeinnaam toevoegen** en klik op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >Neem `http://`, `https://`, of geen ruimten op wanneer het ingaan in uw domein.

1. De Verificatie van de Naam van het domein voor uw het schermvertoningen van het Milieu.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Raadpleeg [Domeinverificatie](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen.

1. Klik op **Create**.

1. Voor de implementatie van Aangepaste domeinnamen is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en Gedistribueerd**.

Op dit punt is uw aangepaste domeinnaam klaar om te worden getest en is een `CNAME` om ernaar te wijzen. Raadpleeg [Status domeinnaam](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over verschillende statussen en hoe u deze kunt adresseren.

>[!NOTE]
>DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.
