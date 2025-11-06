---
title: IP-Lijsten van gewenste personen toevoegen
description: Leer hoe u uw eigen IP-Lijsten van gewenste personen toevoegt met Cloud Manager.
exl-id: 769be71f-5c11-4f98-8906-7a5667a25aee
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# Een IP-Lijst van gewenste personen toevoegen {#add-ip-allow-list}

Leer hoe u uw eigen IP-Lijst van gewenste personen toevoegt met Cloud Manager.

Een gebruiker in de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** kan deze stappen volgen om een IP Lijst van gewenste personen toe te voegen.

{{add-cm-allowlist-frontend-pipeline}}
{{ip-allow-lists-ue}}

**om een IP Lijst van gewenste personen toe te voegen:**

1. Logboek in Cloud Manager bij [&#x200B; experience.adobe.com &#x200B;](https://experience.adobe.com/experiencemanager/).

1. Klik in het linkermenu op Cloud Manager en selecteer de gewenste organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. Van de **pagina van het Overzicht van het Programma**, die het linkerzijmenu gebruikt (u kunt ![&#x200B; het menupictogram van de Show &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) in de upper-left hoek moeten klikken om het menu te zien), klik ![&#x200B; het pictogram van de Lijst van de Taak &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_TaskList_18_N.svg) **IP Lijsten van gewenste personen**.

   ![&#x200B; IP de optie van Lijsten van gewenste personen in het linkerzijmenu &#x200B;](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create.png)

1. Vlak de hoger-juiste hoek van de IP pagina van Lijsten van gewenste personen, klik **toevoegen IP Lijst van gewenste personen**.

   ![&#x200B; Add IP de dialoogdoos van de Lijst van gewenste personen &#x200B;](/help/implementing/cloud-manager/assets/ip-allow-list/ip-allow-list-create02.png)

1. In **voeg IP de dialoogdoos van de Lijst van gewenste personen** toe, op het **IP de naam van de Lijst van gewenste personen** gebied, ga een naam in die u wilt gebruiken om de IP Lijst van gewenste personen van verwijzingen te voorzien. Deze naam is alleen ter informatie. Zorg ervoor dat dit beschrijvend genoeg is om u te helpen de lijst te identificeren.

1. Op het **IP adres/CIDR** gebied, ga tot 50 IP adressen of blokken CIDR in. U kunt deze op een van de volgende manieren toevoegen:

   * Een voor een: Typ een adres en druk op `Enter` . Herhaal dit voor elk extra adres.
   * Meerdere tegelijk: typadressen gescheiden door komma&#39;s (,) of tabs, drukt vervolgens op `Enter` zodat elk adres afzonderlijk wordt herkend.

1. Nadat u het laatste IP-adres of CIDR-blok hebt ingevoerd, drukt u op `Enter` om de invoer te bevestigen. De ingang wordt erkend slechts nadat u `Enter` drukt, en **sparen** knoop wordt actief.

1. Klik **sparen**.

Na het bewaren, verschijnt de pas gecreëerde IP Lijst van gewenste personen als rij in de lijst in de **IP Lijsten van gewenste personen** pagina.

