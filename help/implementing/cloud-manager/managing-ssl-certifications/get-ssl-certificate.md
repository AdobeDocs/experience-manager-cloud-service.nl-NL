---
title: Een SSL-certificaat ophalen - SSL-certificaten beheren
description: Een SSL-certificaat ophalen - SSL-certificaten beheren
translation-type: tm+mt
source-git-commit: e27e5302802e68dce2a5713626950896bb35420a
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# SSL-certificaat {#getting-an-ssl-certificate} ophalen

Bedrijven gebruiken SSL-certificaten om hun websites te beveiligen en hun klanten in staat te stellen er vertrouwen in te stellen. Voor het gebruik van het SSL-protocol vereist een webserver het gebruik van een SSL-certificaat. Cloud Manager biedt geen SSL-certificaten of persoonlijke sleutels. Deze moeten worden verkregen van certificeringsinstanties.

Wanneer een entiteit een certificaat aanvraagt van een certificeringsinstantie (CA), voltooit de CA een verificatieproces. Dit kan zich van het verifiëren van domeinnaamcontrole tot het verzamelen van de documenten van de bedrijfregistratie en abonneeovereenkomsten uitstrekken.

Zodra de informatie van een entiteit is geverifieerd, zal de CA hun openbare sleutel ondertekenen gebruikend de privé sleutel van CA. Omdat alle belangrijke certificeringsinstanties basiscertificaten hebben in webbrowsers, wordt het certificaat van de entiteit gekoppeld via een vertrouwensketen *en wordt het certificaat door de webbrowser herkend als een vertrouwd certificaat.*

