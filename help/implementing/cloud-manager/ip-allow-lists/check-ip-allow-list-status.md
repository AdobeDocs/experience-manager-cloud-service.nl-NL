---
title: Status van IP-Lijst van gewenste personen controleren
description: Status van IP-Lijst van gewenste personen controleren
exl-id: 5ddea04f-3720-4663-90a8-9399019bfcbe
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Status van IP-Lijst van gewenste personen controleren {#check-allow-list-status}

Follow the steps below to determine the status of updates to your IP Allow List:

1. Klik op het statuspictogram voor de IP-Lijst van gewenste personen in de tabel **Omgevingen** scherm en selecteren **IP-Lijsten van gewenste personen** pagina.

1. Cloud Manager will display one of the following statuses, as mentioned in the section below.

## Status van een IP Lijst van gewenste personen {#status}

Hier volgen de definities van status die in een IP-Lijst van gewenste personen worden weergegeven:

* **Toegepast**: IP de Lijst van gewenste personen wordt met succes toegepast op milieu&#39;s.  De omgevingen en service zijn zichtbaar zoals in de onderstaande afbeelding wordt getoond.

* **Bijwerken**: Er wordt een update van de IP-Lijst van gewenste personen uitgevoerd die een of meer van toepassing zijn of ongedaan maken. Elke toepassing toepassen en ongedaan maken wordt vermeld samen met Niet gestart/Bezig/Voltooid of Niet uitgevoerd.

* **Failed**: One or more apply or unapply process in an Update failed. Each Apply and Unapply will be  listed along with Complete or Failed.
   * De status is mislukt, zelfs als een toepassing wordt toegepast of ongedaan wordt gemaakt in de update.
   * De status blijft Mislukt totdat alle fouten zijn gewist. De gebruiker moet het pictogram Opnieuw proberen naast de status selecteren om de fout te ontruimen.
   * De gebruiker zal geen IP Lijst van gewenste personen kunnen bijwerken of schrappen terwijl de status Ontbroken is.

* **Verwijderen**: Aanvraag verwijderen is bezig. Dit betekent dat alle services niet van toepassing zijn. Each Unapply will be  listed along with Not Started/In Progress/Complete or Failed.
Zodra de verrichting van de Schrapping wordt voltooid, zal de IP Lijst van gewenste personen:
   * Niet meer in de IP lijst van de Lijst van gewenste personen verschijnen.
   * Niet meer toepassen op services in het programma in Cloud Manager.

* **Verwijderen is mislukt**: Een of meer verwijderingsprocessen in een verwijderbewerking zijn mislukt. Elke Unapply zal samen met Volledige of Ontbroken worden vermeld.

   * The status will be Delete Failed, even if one unapply fails.
   * De status blijft Verwijderen mislukt totdat alle fouten zijn gewist. Gebruiker moet Verwijderen selecteren in het menu **...** helemaal rechts van de rij in de tabel om eventuele fouten te wissen.
   * User will not be Allow to Update IP Allow List while the status is Failed.

## Pre-existing CDN Configurations for IP Allow Lists {#pre-existing-cdn}

Customers with environments that includes pre-existing CDN configurations for IP Allow Lists, SSL Certificates or Custom Domain Names will see the following message in the the **IP Allow List** and the **Environment** details page. Het bericht dat op UI wordt getoond zal verdwijnen zodra de klant alle reeds bestaande omgevingsconfiguraties via UI volledig heeft gemigreerd en het kan 1-2 werkdagen voor het bericht vergen om te verdwijnen.

>[!NOTE]
>Om de reeds bestaande configuraties te kunnen zien en beheren moeten zij via UI worden toegevoegd. Refer to [Adding an IP Allow List](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) for more details.

![](/help/implementing/cloud-manager/assets/ip-allow-list-message1.png)

![](/help/implementing/cloud-manager/assets/ip-allow-list-message2.png)
