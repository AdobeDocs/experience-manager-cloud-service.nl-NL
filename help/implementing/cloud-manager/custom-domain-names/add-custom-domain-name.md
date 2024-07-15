---
title: Een aangepaste domeinnaam toevoegen
description: Leer hoe u een aangepaste domeinnaam kunt toevoegen met Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 0%

---


# Een aangepaste domeinnaam toevoegen {#adding-cdn}

U kunt een aangepaste domeinnaam vanuit twee locaties in Cloud Manager toevoegen:

* [Via de pagina Domeininstellingen](#adding-cdn-settings)
* [Van de pagina Milieu&#39;s](#adding-cdn-environments)

>[!NOTE]
>
>Een gebruiker moet de **BedrijfsEigenaar** of **rol hebben van de Manager van de Plaatsing** om een naam van het douanedomein in Cloud Manager toe te voegen, en u moet snelst CDN gebruiken.

## Een aangepaste domeinnaam toevoegen vanaf de pagina Domeininstellingen {#adding-cdn-settings}

Wanneer u een aangepaste domeinnaam toevoegt, wordt het domein gediend met het meest specifieke, geldige certificaat. Als meerdere certificaten hetzelfde domein hebben, wordt de meest recente bijgewerkte versie gekozen. Adobe raadt u aan certificaten zodanig te beheren dat er geen overlappende domeinen zijn.

Volg deze stappen om een naam van het douanedomein van de **pagina van de Montages van het Domein** toe te voegen. Deze stappen zijn gebaseerd op Snelheid. Als u een verschillende CDN gebruikt, moet u uw domein met CDN vormen u om hebt gekozen te gebruiken.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Navigeer aan het uitgezochte **lusje van de Montages van het Domein** in het linkernavigatievenster.

   ![ het venster van de Montages van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klik **voeg de knoop van het Domein** bij top-right toe om **te openen voeg de dialoog van de Naam van het Domein** toe.

   ![ voeg de dialoog van het Domein toe ](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Ga de naam van het douanedomein op het **gebied van de Naam van het 0} Domein in.**

   >[!NOTE]
   >
   >Neem geen `http://`, `https://` of spaties op wanneer u een domein betreedt.

1. Selecteer het **Milieu** de waarvan dienst met de domeinnaam wordt geassocieerd.

1. Selecteer of de **Publish** of **Voorproef** dienst.

1. Selecteer het **SSL van het Domein Certificaat** verbonden aan de domeinnaam van drop-down en selecteer **ga** verder.

1. **voegt de dialoogdoos van de Naam van het Domein** toe verschijnt en zal u aan het proces van de domeinnaamcontrole nemen. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen. Klik **creëren**.

   ![ de naamcontrole van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt vermeld door status **Verified en Geïmporteerd**.

Zie [ Controlerend de Status van de Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) om meer over diverse statussen te leren en hoe te om potentiële kwesties te richten.

>[!TIP]
>
>Herzie het volgende artikel over de behoefte [ een CNAME of een Verslag volgende ](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) toevoegen om verdubbelende inspanning te vermijden wanneer het toevoegen van DNS-verslagen aan uw douane-domein. De ingang TXT en CNAME of een Verslag kunnen gelijktijdig op de regerende DNS Server worden geplaatst.

>[!TIP]
>
>Zie [ Toevoegend een Verslag TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) om meer over verslagen te leren TXT.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Zie [ Controlerend de Status van de Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.

## Een aangepaste domeinnaam toevoegen vanaf de pagina Omgevingen {#adding-cdn-environments}

Volg deze stappen om een naam van het douanedomein van de **pagina van Milieu&#39;s** toe te voegen.

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. Navigeer aan **het Detail van Milieu** pagina voor het milieu van belang.

   ![ die domeinnaam op de pagina van de Details van het Milieu ingaan ](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de **lijst van de Namen van het Domein** om de naam van het douanedomein voor te leggen.

   1. Voer de aangepaste domeinnaam in.
   1. Selecteer het SSL-certificaat dat aan deze naam is gekoppeld in de vervolgkeuzelijst.
   1. Klik **+ toevoegen**.

   ![ voeg de Naam van het Domein van de Douane toe ](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Controleer de waarden die in **worden geselecteerd voegt de dialoogdoos van de Naam van het Domein** toe en klik **verdergaan**.

   ![ Venster van de Naam van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Neem geen `http://`, `https://` of spaties op wanneer u in de domeinnaam invoert.

1. **voegt de dialoogdoos van de Naam van het Domein** toe verschijnt en zal u aan het proces van de domeinnaamcontrole nemen. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen. Klik **creëren**.

   ![ de naamcontrole van het Domein ](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt vermeld door status **Verified en Geïmporteerd**.

Zie [ Controlerend de Status van de Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) om meer over diverse statussen te leren en hoe te om potentiële kwesties te richten.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Zie [ Controlerend de Status van de Naam van het Domein van de Douane ](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.

>[!TIP]
>
>Zie [ Toevoegend een Verslag TXT ](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) om meer over verslagen te leren TXT.
