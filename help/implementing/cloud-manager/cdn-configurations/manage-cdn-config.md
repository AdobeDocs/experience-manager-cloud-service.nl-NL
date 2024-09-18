---
title: CDN-configuraties beheren
description: Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken en bijwerken of verwijderen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 8e2fc0d4ee82e79d1a822a528b1a46acce3c192a
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---


# CDN-configuraties beheren {#manage-cdn-configurations}

Leer hoe u met Cloud Manager CDN-configuraties voor een Edge Delivery-site of een Cloud Manager-omgeving kunt bewerken en bijwerken of verwijderen.

## Een CDN-configuratie bewerken {#edit-cdn}

In Adobe Cloud Manager kunt u om verschillende redenen een CDN-configuratie bewerken, inclusief de milieulaag (Publish of Voorvertoning) en het SSL-certificaat.

* **de veranderingen van het Milieu**: Het aanpassen van de rijhulp past de montages CDN met het correcte milieu aan, hetzij voor levende productie (Publish) of het testen (Voorproef).
* **de verhogingen van de Veiligheid**: Het selecteren van een verschillend SSL certificaat kan noodzakelijk zijn wanneer het bijwerken van certificaten of het richten van naleving en veiligheidsbehoeften.
* **Optimaliserend prestaties**: Het uitgeven van de configuratie verzekert de correcte montages CDN voor het leveren van inhoud die op veranderende operationele behoeften wordt gebaseerd.

U kunt een configuratie bewerken zonder de bestaande configuratie volledig te verwijderen. Wijzigingen worden toegepast op de geselecteerde omgeving, bijvoorbeeld in de testfase of de productieomgeving, en kunnen van invloed zijn op de manier waarop inhoud wordt geleverd en beveiligd.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie uit te geven CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.
1. In het linkernavigatievenster, onder **Diensten**, klik **Configuraties CDN**.
1. In de **CDN Configuraties** lijst, klik de ellips aan het eind van een rij waarvan configuratie CDN u wilt uitgeven.

   ![ Uitgevend een configuratie CDN ](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Klik **uitgeven**.
1. In **geef CDN configuratie** dialoogdoos uit, plaats één of meerdere opties in de respectieve drop-down lijst.

   De opties die u in de dialoogdoos ziet kunnen afhankelijk van variëren als u Adobe-geleide CDN of een klant-beheerde CDN gebruikt.

1. Klik **Update**.

   Het statuut van uitgegeven CDN wordt bijgewerkt in de **CDN Configuratie** lijst om op de veranderingen te wijzen u aanbracht.

## Een CDN-configuratie verwijderen {#delete-cdn}

Wanneer u een Adobe-beheerde of klant-beheerde configuratie CDN in Adobe Cloud Manager schrapt, worden het verpletteren van het bijbehorende domein en SSL certificaatmontages verwijderd. Het domein gebruikt niet meer CDN voor verkeerslevering, en om het even welke veiligheid of prestatiesverhogingen die door CDN worden verstrekt wordt verloren. U kunt de dienstverstoring ervaren tot een nieuwe configuratie opstelling is, of het re-toevoegen van geschrapte CDN of het toevoegen van nieuwe.

Een gebruiker moet een lid van de **BedrijfsEigenaar** of **rol zijn van de Manager van de Plaatsing** om deze taak te voltooien.

**om een configuratie te schrappen CDN:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteert de aangewezen organisatie en het programma.

1. In het linkernavigatievenster, onder **Diensten**, klik **Configuraties CDN**.

1. Klik in de tabel CDN-configuraties op de ovaal aan het einde van een rij waarvan u de CDN wilt verwijderen.

   ![ het Schrappen van een configuratie CDN ](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. Klik **Schrapping**.
1. Klik **Schrapping** opnieuw om de verwijdering van CDN van de plaats te bevestigen.


