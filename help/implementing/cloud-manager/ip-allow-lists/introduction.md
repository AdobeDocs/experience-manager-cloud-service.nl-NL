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
>abstract="AEM als cloudservice is toegankelijk via internet en wordt beveiligd door verificatie en autorisatie van gebruikers. De IP van de Manager van de wolk lijsten van gewenste personen kunnen worden gebruikt om toegang tot slechts vertrouwde op IP adressen te beperken en te controleren. Gebruikers van Cloud Manager met de juiste machtigingen kunnen lijsten van gewenste personen maken met vertrouwde IP-adressen waarmee de gebruikers van de site toegang hebben tot hun AEM."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/add-ip-allow-lists.html" text="Een IP-Lijst van gewenste personen toevoegen"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/ip-allow-lists/managing-ip-allow-lists.html" text="Een IP-Lijst van gewenste personen weergeven en bijwerken"

AEM als cloudservice is standaard toegankelijk via internet. Terwijl de veiligheid door gebruikersauthentificatie en vergunning wordt behandeld, IP staat-lijst toe om toegang tot slechts vertrouwde op IP adressen te beperken.

De IP van de Manager van de wolk lijsten van gewenste personen kunnen worden gebruikt om toegang tot slechts dergelijke vertrouwde op IP adressen te beperken en te controleren. Gebruikers van Cloud Manager met de juiste machtigingen kunnen [lijsten van gewenste personen maken](/help/implementing/cloud-manager/ip-allow-lists/add-ip-allow-lists.md) van vertrouwde IP-adressen waar de gebruikers van hun site toegang tot hun AEM kunnen krijgen.

Na toevoegen, [IP de lijsten van gewenste personen kunnen worden toegepast/unapplied](/help/implementing/cloud-manager/ip-allow-lists/apply-allow-list.md) meerdere keren als eenheid of entiteit aan een auteur en/of uitgeversdienst in een milieu.

>[!NOTE]
>
>Als geen IP lijst van gewenste personen wordt toegepast, door gebrek worden alle IP adressen toegestaan. Wanneer een IP lijst van gewenste personen wordt toegepast, worden geen IP adressen toegestaan behalve adressen op de IP lijst van gewenste personen.

## Beperkingen {#limitations}

Er zijn verscheidene beperkingen aan IP lijsten van gewenste personen om in mening te houden.

* Een maximum van 50 IP lijsten van gewenste personen kan in uw programma worden toegevoegd
* Een maximum van 50 IP/CIDR adressen kan aan elke IP lijst van gewenste personen worden toegevoegd.
* Namen van IP-lijsten van gewenste personen worden ondersteund in Cloud Manager voor auteur, of publicatieservice, of beide, in een omgeving.
