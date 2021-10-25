---
title: Een aangepaste domeinnaam toevoegen
description: Een aangepaste domeinnaam toevoegen
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 98c137645351c86da8680a31b4929c588863a981
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---

# Een aangepaste domeinnaam toevoegen {#adding-cdn}

Een gebruiker moet een Business Owner of Deployment Manager zijn om een aangepaste domeinnaam in Cloud Manager te kunnen toevoegen.

De volgende stappen moeten worden uitgevoerd zoals aangegeven in onderstaande tabel:

| Stap |  | Verantwoordelijkheid | Meer informatie |
|--- |--- |--- |---|
| SLL-certificaat toevoegen | SLL-certificaat toevoegen | Klant | [Een SSL-certificaat toevoegen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate.html?lang=en) |
| Domeinverificatie | TXT-record toevoegen | Klant | [Een TXT-record toevoegen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/add-text-record.html?lang=en) |
| Status domeinverificatie controleren |  | Klant |  |
|  | Status: Domeinverificatie mislukt | Klant | [Status domeinnaam controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
|  | Status: Geverifieerd, implementatie mislukt | Adobe-contactpersoon | [Status domeinnaam controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-domain-name-status.html?lang=en) |
| DNS-records toevoegen die wijzen naar AEM as a Cloud Service door CNAME- of APEX-records toe te voegen | DNS-instellingen configureren | Klant | [DNS-instellingen configureren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/configure-dns-settings.html?lang=en) |
| DNS-recordstatus controleren |  | Klant | [DNS-recordstatus controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | Status: DNS-status niet gedetecteerd | Klant | [DNS-recordstatus controleren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/custom-domain-names/check-dns-record-status.html?lang=en) |
|  | Status: DNS wordt onjuist omgezet | Klant |  |


## Belangrijke overwegingen {#important-considerations}

* Voordat u een aangepaste domeinnaam kunt toevoegen, moet een geldig SSL-certificaat met de aangepaste domeinnaam zijn geïnstalleerd op uw programma. Zie [Een SSL-certificaat toevoegen](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) voor meer informatie.

* De namen van het domein kunnen niet aan milieu&#39;s worden toegevoegd terwijl er een huidige lopende pijpleiding verbonden aan die milieu&#39;s is.

* Er kan slechts één domeinnaam tegelijk worden toegevoegd. Aangepaste domeinen aan de zijde van de auteur worden niet ondersteund.

* AEM as a Cloud Service ondersteunt geen jokertekendomeinen.

* Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten.

* Dezelfde domeinnaam kan niet op meer dan één omgeving worden gebruikt.

## Een aangepaste domeinnaam toevoegen vanaf de pagina Domeininstellingen {#adding-cdn-settings}

Voer de onderstaande stappen uit om een aangepaste domeinnaam toe te voegen van de pagina Domeininstellingen:

1. Navigeren naar **Omgevingen** scherm van **Overzicht** pagina.

1. Klikken op **Domeininstellingen** in het navigatiemenu aan de linkerkant.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klikken op **Domein toevoegen** te openen knop **Domeinnaam toevoegen** in.

   ![](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Voer de aangepaste domeinnaam in **Domeinnaam**.

   >[!NOTE]
   >U dient geen `http://`, `https://`of spaties bij het invoeren in uw domein.

1. Selecteer **Omgeving** wiens publicatieservice wordt gekoppeld aan de domeinnaam.

1. Selecteer de service als **Publiceren** of **Voorvertoning**.

   >[!NOTE]
   >Aangepaste domeinnamen worden nu ondersteund in Cloud Manager for Sites-programma&#39;s voor zowel Services voor publiceren als voorvertonen. Elke Cloud Manager-omgeving kan maximaal 500 aangepaste domeinen per omgeving hosten. Raadpleeg voor meer informatie over Voorvertoningsservice [Voorvertoningsservice](/help/implementing/cloud-manager/manage-environments.md#preview-service).

1. Selecteer **Domain SSL-certificaat** in de vervolgkeuzelijst en selecteert u **Doorgaan**.

1. **Domeinnaam toevoegen** wordt weergegeven. Dit zal u aan de Verificatie van de Naam van het Domein voor uw scherm van het Milieu nemen. Zie [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie.

   Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen:

1. Klikken op **Maken**.
1. Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en geïmplementeerd**.
Navigeren naar [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over de verschillende statussen en over de manier waarop ze moeten omgaan.

   >[!NOTE]
   >DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.

## Een aangepaste domeinnaam uit de pagina Omgevingen toevoegen {#adding-cdn-environments}

1. Navigeer naar de pagina Environment Detail voor de omgeving van belang.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de invoervelden boven aan de tabel Domeinnamen om de aangepaste domeinnaam te verzenden en selecteer het SSL-certificaat in de vervolgkeuzelijst. Klikken op **+ Toevoegen**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Velden controleren vanuit de **Domeinnaam toevoegen** en klik op **Doorgaan**.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >Niet opnemen `http://`, `https://`of spaties bij het invoeren in uw domein.

1. De Verificatie van de Naam van het domein voor uw het schermvertoningen van het Milieu.

   ![](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

   Zie [Domeinverificatie](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen.

1. Klikken op **Maken**.

1. Voor de implementatie van Aangepaste domeinnamen is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en geïmplementeerd**.

Op dit punt is uw aangepaste domeinnaam gereed voor testen en een `CNAME` om ernaar te wijzen. Zie [Status van domeinnaam](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over de verschillende statussen en over de manier waarop ze moeten omgaan.

>[!NOTE]
>DNS het bewijs kan tot een paar uren aan erkenning, wegens DNS propagatievertragingen vergen. Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Raadpleeg Status domeinnaam controleren voor meer informatie.
