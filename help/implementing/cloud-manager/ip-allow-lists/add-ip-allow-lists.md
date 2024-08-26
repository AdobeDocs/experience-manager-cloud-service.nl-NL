---
title: IP-Lijsten van gewenste personen toevoegen
description: Leer hoe u uw eigen IP-Lijsten van gewenste personen toevoegt met Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 1415d07235641262814e81362c806572bcf582ba
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# Een IP-Lijst van gewenste personen toevoegen {#add-ip-allow-list}

Leer hoe u uw eigen IP-Lijst van gewenste personen toevoegt met Cloud Manager.

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen om een IP Lijst van gewenste personen toe te voegen.

{{add-cm-allowlist-frontend-pipeline}}

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het Programma**, die het zijpaneel op de linkerkant gebruikt (u kunt het hamburgerpictogram in de upper-left hoek moeten klikken om het paneel te zien), klik **IP Lijsten van gewenste personen**.

   ![ IP de optie van Lijsten van gewenste personen in het zijpaneel ](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Vlak de hoger-juiste hoek van de IP pagina van Lijsten van gewenste personen, klik **toevoegen IP Lijst van gewenste personen**.

   ![ Add IP de dialoogdoos van de Lijst van gewenste personen ](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. In **voeg IP de dialoogdoos van de Lijst van gewenste personen** toe, op het **IP de naam van de Lijst van gewenste personen** gebied, ga een naam in die u wilt gebruiken om de IP Lijst van gewenste personen van verwijzingen te voorzien. Deze naam is alleen ter informatie. Zorg ervoor dat dit beschrijvend genoeg is om u te helpen de lijst te identificeren.

1. Op het **IP adres/CIDR** gebied, ga IP of IP CIDR blok in. Scheid meerdere blokken met een komma of een tab.

1. Klik **sparen**.

Na het bewaren, verschijnt de pas gecreëerde IP Lijst van gewenste personen als rij in de lijst in de **IP Lijsten van gewenste personen** pagina.

## De Cloud Manager IP-Lijst van gewenste personen toevoegen {#add-cm-allowlist}

De front-end pijpleiding vereist dat de volgende Lijst van gewenste personen van Cloud Manager IP vooraf wordt toegevoegd.

**Cloud Manager IP Lijst van gewenste personen**

`52.254.106.192/28,20.186.185.181,52.254.106.240/28,52.254.107.128/28,52.254.105.192/28,52.254.106.176/28,20.186.185.227,52.254.106.144/28,52.254.107.64/28,20.186.185.239,20.22.83.112,52.254.107.80/28,52.254.107.144/28,52.254.106.224/28,20.14.241.153,52.254.107.0/28,52.254.107.32/28,52.254.106.208/28,40.70.154.136/29,52.254.106.160/28,52.254.107.16/28,52.254.106.0/28,4.152.211.251`

Om verstoring van het runnen van de front-end pijpleiding te vermijden, zorg ervoor dat deze Lijst van gewenste personen van Cloud Manager IP wordt toegevoegd en dan toegepast op de dienst van de Auteur van het milieu *alvorens* u de pijpleiding toelaat.

**om de Lijst van gewenste personen van Cloud Manager toe te voegen IP:**

1. Logboek in Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het Programma**, die het zijpaneel op de linkerkant gebruikt (u kunt het hamburgerpictogram in de upper-left hoek moeten klikken om het paneel te zien), klik **IP Lijsten van gewenste personen**.

1. Vlak de hoger-juiste hoek van de IP pagina van Lijsten van gewenste personen, klik **toevoegen IP Lijst van gewenste personen**.

1. In **voeg IP de dialoogdoos van de Lijst van gewenste personen** toe, op het **IP de naam van de Lijst van gewenste personen** gebied, type *`Cloud Manager`*.

1. Kopieer het blok van de hierboven adressen van de Lijst van gewenste personen van Cloud Manager IP. Elk adres is reeds gescheiden door een komma.

1. In **voeg IP de dialoogdoos van de Lijst van gewenste personen** toe, kleef het blok in het **IP adres/CIDR** gebied.

1. Plaats de curseur enkel na de eerste komma in de adreslijst en druk **binnengaan**.

1. Klik **sparen**.

Nu, [ pas de Lijst van gewenste personen van Cloud Manager IP ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) op uw programmamilieu&#39;s toe.



