---
title: Inleiding aan IP Lijsten van gewenste personen
description: Leer hoe IP de Lijsten van gewenste personen kunnen beperken waarvan de adressen gebruikers tot domeinen in AEM as a Cloud Service kunnen toegang hebben.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f4c6331491bb08e81964476ad58065c1ee022967
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---


# Inleiding aan IP Lijsten van gewenste personen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP-Lijsten van gewenste personen beheren"
>abstract="AEM as a Cloud Service is via internet toegankelijk en wordt beveiligd door gebruikersverificatie en autorisatie. De Lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Cloud Manager-gebruikers met de juiste machtigingen kunnen lijsten van gewenste personen maken van vertrouwde IP-adressen waar de gebruikers van hun site toegang tot hun AEM kunnen krijgen."
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists" text="Een IP-Lijst van gewenste personen toevoegen"
>additional-url="https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists" text="Een IP-Lijst van gewenste personen weergeven en bijwerken"

AEM als cloudservice is standaard toegankelijk via internet. Terwijl de veiligheid door gebruikersauthentificatie en vergunning wordt behandeld, IP staat-lijst toe om toegang tot slechts vertrouwde op IP adressen te beperken.

De Lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts dergelijke vertrouwde op IP adressen te beperken en te controleren. De gebruikers van Cloud Manager met aangewezen toestemmingen kunnen [ IP Lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) van vertrouwde op IP adressen tot stand brengen waarvan de gebruikers van hun plaats tot hun AEM kunnen toegang hebben.

Na het toevoegen, [ IP kunnen de Lijsten van gewenste personen worden toegepast of ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) veelvoudige tijden als eenheid of entiteit aan de auteursdienst, of een uitgeversdienst, of allebei, in een milieu ongedaan worden gemaakt.

>[!NOTE]
>
>Als geen IP Lijst van gewenste personen wordt toegepast, door gebrek worden alle IP adressen toegestaan. Wanneer een IP Lijst van gewenste personen wordt toegepast, worden geen IP adressen toegestaan behalve adressen op de IP Lijst van gewenste personen.

## Beperkingen {#limitations}

Er zijn verscheidene beperkingen aan IP Lijsten van gewenste personen om in mening te houden.

* U kunt maximaal 50 IP-Lijsten van gewenste personen toevoegen aan uw programma.
* Een maximum van 50 IP/CIDR adressen kan aan elke IP Lijst van gewenste personen worden toegevoegd.
* IP de namen van de Lijst van gewenste personen worden gesteund in Cloud Manager voor de auteursdienst, of de publicatieservice, of allebei, in een milieu.
