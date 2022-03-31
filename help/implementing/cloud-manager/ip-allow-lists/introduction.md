---
title: Inleiding aan IP Lijsten van gewenste personen
description: Leer hoe IP de lijsten van gewenste personen kunnen beperken waarvan de adressen gebruikers tot uw AEM as a Cloud Service domeinen kunnen toegang hebben.
exl-id: 352fae8e-d116-40b0-ba54-d7f001f076e8
source-git-commit: 8d1680fa8dbaaefa297cf8c6698097b3c7acc48d
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Inleiding aan IP Lijsten van gewenste personen {#introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_ipallowlist"
>title="IP-Lijsten van gewenste personen beheren"
>abstract="AEM als cloudservice is toegankelijk via internet en wordt beveiligd door gebruikersverificatie en autorisatie. IP van de Manager van de wolk kunnen de lijsten van gewenste personen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Gebruikers van Cloud Manager met de juiste machtigingen kunnen lijsten van gewenste personen met vertrouwde IP-adressen maken waarmee de gebruikers van de site toegang hebben tot hun AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Een IP-Lijst van gewenste personen toevoegen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/ip-allow-lists/view-update-ip-allow-list.html" text="Een IP-Lijst van gewenste personen weergeven en bijwerken"

AEM als cloudservice is toegankelijk via internet en wordt beveiligd door gebruikersverificatie en autorisatie. IP van de Manager van de wolk kunnen de lijsten van gewenste personen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Gebruikers van Cloud Manager met de juiste machtigingen kunnen lijsten van gewenste personen met vertrouwde IP-adressen maken waarmee de gebruikers van de site toegang hebben tot hun AEM.

IP de lijsten van gewenste personen kunnen eenmaal worden toegevoegd en worden toegepast/unapplied veelvoudige tijden als eenheid of entiteit aan een auteur en/of uitgeversdienst in een milieu.

## Beperkingen {#limitations}

Er zijn een aantal beperkingen aan IP staat lijsten toe om in mening te houden.

* Een maximum van 50 IP lijsten van gewenste personen kan in uw programma worden toegevoegd
* Een maximum van 50 IP/CIDR adressen kan aan elke IP lijst van gewenste personen worden toegevoegd.
* Namen van IP-lijsten van gewenste personen worden ondersteund in Cloud Manager voor auteur en/of publicatieservice in een omgeving.
