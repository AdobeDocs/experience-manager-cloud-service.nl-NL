---
title: Een SSL-certificaat ophalen - SSL-certificaten beheren
description: Een SSL-certificaat ophalen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: fecbd0b4d5cfd8aa970c235c79158bea44403c09
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 0%

---


# SSL-certificaat {#getting-an-ssl-certificate} ophalen

Bedrijven gebruiken SSL-certificaten om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Voor het gebruik van het SSL-protocol vereist een webserver het gebruik van een SSL-certificaat. Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze moeten worden verkregen van certificeringsinstanties.

Wanneer een entiteit een certificaat aanvraagt bij een certificeringsinstantie, voltooit de certificeringsinstantie een verificatieproces. Dit kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken. Zodra de informatie van een entiteit is geverifieerd, zal de CA hun openbare sleutel ondertekenen gebruikend de privé sleutel van CA. Omdat alle belangrijke certificeringsinstanties basiscertificaten hebben in webbrowsers, wordt het certificaat van de entiteit gekoppeld via een vertrouwensketen *en wordt het certificaat door de webbrowser herkend als een vertrouwd certificaat.*

>[!NOTE]
>AEM als Cloud Service accepteert alleen OV-(Organisatie-validatie) of EV-(Uitgebreide validatie) certificaten. DV-(domeinvalidatie) of zelfondertekende certificaten worden niet geaccepteerd. OV- en EV-certificaten bieden gebruikers extra door CA gevalideerde informatie die ze kunnen gebruiken om te bepalen of de eigenaar van een website, de afzender van een e-mail of de digitale handtekening van uitvoerbare code of PDF-documenten betrouwbaar is. DV-certificaten zijn algemeen en goedkoop. Ze staan echter geen eigendomsverificatie toe.

