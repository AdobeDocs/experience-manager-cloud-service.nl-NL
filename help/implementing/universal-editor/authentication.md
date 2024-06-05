---
title: Universal Editor-verificatie
description: Leer hoe de Universele Redacteur het Systeem van Identity Management van de Adobe (IMS) voor authentificatie gebruikt.
exl-id: fb86c510-3c41-4511-81b7-1bdf2f5e7dd3
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Universal Editor-verificatie {#authentication}

Leer hoe de Universal Editor wordt geverifieerd.

## Opties {#options}

De Universele Redacteur gebruikt de authentificatie van het Systeem van Identity Management van de Adobe (IMS), die via Verenigde Shell wordt verstrekt.

Alle toepassingen/externe pagina&#39;s zijn verantwoordelijk voor verificatie op vereiste back-endsystemen. De universele dienst van de Redacteur heeft deze authentificatie aan achterste systemen nodig om verrichtingen CRUD uit te voeren aangezien het een standalone dienst is.

## Standaardstroom {#standard-flow}

Dit is de oplossing voor AEM as a Cloud Service en AMS die IMS gebruiken om de Universele redacteur te gebruiken.

Om de Universele Redacteur te gebruiken, moet de gebruiker in Verenigde Shell worden geregistreerd die tegen IMS voor authentiek verklaart. Het opgegeven IMS-token wordt opgeslagen in de gebruikerssessiewinkel.

Wanneer een gebruiker een CRUD verrichting uitvoert, wordt een vraag verzonden naar de Universele dienst van de Redacteur met het IMS dragerteken in de kopbal van HTTP. De universele dienst van de Redacteur gebruikt dan het dragerteken om het verzoek tegen het AEM achtergrondsysteem voor authentiek te verklaren om verrichtingen in de naam van de gebruiker uit te voeren.

![Standaardverificatiestroom](assets/standard-flow.png)
