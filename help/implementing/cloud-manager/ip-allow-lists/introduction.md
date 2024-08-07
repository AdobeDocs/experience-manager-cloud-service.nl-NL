---
title: Inleiding aan IP Lijsten van gewenste personen
description: Leer hoe IP de lijsten van gewenste personen kunnen beperken waarvan de adressen gebruikers tot domeinen op AEM as a Cloud Service kunnen toegang hebben.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# Inleiding aan IP Lijsten van gewenste personen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP-lijsten van gewenste personen beheren"
>abstract="AEM als cloudservice is toegankelijk via internet en wordt beveiligd door verificatie en autorisatie van gebruikers. De lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Cloud Manager-gebruikers met de juiste machtigingen kunnen lijsten van gewenste personen maken van vertrouwde IP-adressen waar de gebruikers van hun site toegang tot hun AEM kunnen krijgen."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Een IP-Lijst van gewenste personen toevoegen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html" text="Een IP-Lijst van gewenste personen weergeven en bijwerken"

AEM als cloudservice is standaard toegankelijk via internet. Terwijl de veiligheid door gebruikersauthentificatie en vergunning wordt behandeld, IP staat-lijst toe om toegang tot slechts vertrouwde op IP adressen te beperken.

De lijsten van gewenste personen van Cloud Manager IP kunnen worden gebruikt om toegang tot slechts dergelijke vertrouwde op IP adressen te beperken en te controleren. De gebruikers van Cloud Manager met aangewezen toestemmingen kunnen [ lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) van vertrouwde op IP adressen tot stand brengen waarvan de gebruikers van hun plaats tot hun AEM kunnen toegang hebben.

Na het toevoegen, [ IP kunnen de lijsten van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) veelvoudige tijden als eenheid of entiteit aan een auteur en/of uitgeversdienst in een milieu worden toegepast/worden niet toegepast.

>[!NOTE]
>
>Als geen IP lijst van gewenste personen wordt toegepast, door gebrek worden alle IP adressen toegestaan. Wanneer een IP lijst van gewenste personen wordt toegepast, worden geen IP adressen toegestaan behalve adressen op de IP lijst van gewenste personen.

## Beperkingen {#limitations}

Er zijn verscheidene beperkingen aan IP lijsten van gewenste personen om in mening te houden.

* Een maximum van 50 IP lijsten van gewenste personen kan in uw programma worden toegevoegd
* Een maximum van 50 IP/CIDR adressen kan aan elke IP lijst van gewenste personen worden toegevoegd.
* IP de namen van lijsten van gewenste personen worden gesteund in Cloud Manager voor auteur, of de publicatieservice, of allebei, in een milieu.
