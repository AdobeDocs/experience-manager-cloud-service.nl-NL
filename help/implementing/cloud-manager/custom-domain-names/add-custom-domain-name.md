---
title: Een aangepaste domeinnaam toevoegen
description: Leer hoe u een aangepaste domeinnaam kunt toevoegen met Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
source-git-commit: 21496a52fbe3caa08c606ddaeb85481a9d416b3d
workflow-type: tm+mt
source-wordcount: '577'
ht-degree: 0%

---

# Een aangepaste domeinnaam toevoegen {#adding-cdn}

U kunt een aangepaste domeinnaam toevoegen vanuit twee locaties in Cloud Manager:

* [Via de pagina Domeininstellingen](#adding-cdn-settings)
* [Van de pagina Milieu&#39;s](#adding-cdn-environments)

>[!NOTE]
>
>Een gebruiker moet beschikken over de **Zakelijke eigenaar** of **Implementatiebeheer** rol om een aangepaste domeinnaam toe te voegen in Cloud Manager

## Een aangepaste domeinnaam toevoegen vanaf de pagina Domeininstellingen {#adding-cdn-settings}

Ga als volgt te werk om een aangepaste domeinnaam toe te voegen vanuit de **Domeininstellingen** pagina.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Ga naar de **Omgevingen** van het scherm **Overzicht** pagina.

1. Klikken op **Domeininstellingen** in het linkernavigatievenster.

   ![Het venster Domeininstellingen](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Klik op de knop **Domein toevoegen** om de **Domeinnaam toevoegen** .

   ![Domein toevoegen, dialoogvenster](/help/implementing/cloud-manager/assets/cdn/add-cdn1.png)

1. Voer de aangepaste domeinnaam in het dialoogvenster **Domeinnaam** veld.

   >[!NOTE]
   >
   >Niet opnemen `http://`, `https://`of spaties bij het invoeren in uw domein.

1. Selecteer **Omgeving** waarvan de dienst met de domeinnaam zal worden geassocieerd.

1. Selecteer een van de **Publiceren** of **Voorvertoning** service.

1. Selecteer **Domain SSL-certificaat** gekoppeld aan de domeinnaam in de vervolgkeuzelijst en selecteert u **Doorgaan**.

1. De **Domeinnaam toevoegen** wordt weergegeven en gaat u naar het proces voor domeinnaamverificatie. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen. Klikken op **Maken**.

   ![Domeinnaamverificatie](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en geïmplementeerd**.

Het document raadplegen [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over de verschillende statussen en over de manier waarop mogelijke problemen kunnen worden aangepakt.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Het document raadplegen [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie .

>[!TIP]
>
>Zie [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie over TXT-records.

## Een aangepaste domeinnaam uit de pagina Omgevingen toevoegen {#adding-cdn-environments}

Ga als volgt te werk om een aangepaste domeinnaam toe te voegen vanuit de **Omgevingen** pagina.

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie en het juiste programma.

1. Navigeren naar **Omgevingsdetails** pagina voor de omgeving van belang.

   ![Domeinnaam invoeren op de pagina Environment Details](/help/implementing/cloud-manager/assets/cdn/cdn-create4.png)

1. Gebruik de **Domeinnamen** tabel om de aangepaste domeinnaam te verzenden.

   1. Voer de aangepaste domeinnaam in.
   1. Selecteer het SSL-certificaat dat aan deze naam is gekoppeld in de vervolgkeuzelijst.
   1. Klikken op **+Toevoegen**.

   ![Aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)

1. Controleer de waarden die zijn geselecteerd in het dialoogvenster **Domeinnaam toevoegen** en klik op **Doorgaan**.

   ![Venster Domeinnaam](/help/implementing/cloud-manager/assets/cdn/cdn-create5.png)

   >[!NOTE]
   >
   >Niet opnemen `http://`, `https://`of spaties bij het invoeren in de domeinnaam.

1. De **Domeinnaam toevoegen** wordt weergegeven en gaat u naar het proces voor domeinnaamverificatie. Volg de instructies die worden gegeven om domeineigendom voor uw milieu te bewijzen. Klikken op **Maken**.

   ![Domeinnaamverificatie](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

Voor CDN-implementatie is een geldig SSL-certificaat en een geslaagde TXT-verificatie vereist. Dit wordt aangegeven door status **Geverifieerd en geïmplementeerd**.

Het document raadplegen [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie over de verschillende statussen en over de manier waarop mogelijke problemen kunnen worden aangepakt.

>[!NOTE]
>
>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.
>
>Cloud Manager controleert het eigendom en werkt de status bij die in de tabel met domeininstellingen kan worden weergegeven. Het document raadplegen [Status aangepaste domeinnaam controleren](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer informatie .

>[!TIP]
>
>Zie [Een TXT-record toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-text-record.md) voor meer informatie over TXT-records.
