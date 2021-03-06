---
title: Configuratie van filter Referrer met AEM zonder kop
description: Met het filter Adobe Experience Manager Referrer kunt u toegang krijgen van hosts van derden. Een configuratie OSGi voor de Filter van de Referateur is nodig om toegang tot het eindpunt GraphQL voor headless toepassingen toe te laten.
feature: GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---

# Refererfilter {#referrer-filter}

Met het filter Adobe Experience Manager Referrer kunt u toegang krijgen van hosts van derden. Een configuratie OSGi voor de Filter van de Referateur is nodig om toegang tot het eindpunt GraphQL voor headless toepassingen toe te laten.

Dit wordt gedaan door een aangewezen configuratie OSGi voor de Filter toe te voegen Referrer die:

* geeft een hostnaam voor een vertrouwde website aan; ofwel `allow.hosts` of `allow.hosts.regexp`,
* verleent toegang voor deze gastheernaam.

De naam van het bestand moet `org.apache.sling.security.impl.ReferrerFilter.cfg.json`.

Bijvoorbeeld om toegang voor verzoeken met de Referiteur te verlenen `my.domain` u kunt:

```xml
{
    "allow.empty":false,
    "allow.hosts":[
      "my.domain"
    ],
    "allow.hosts.regexp":[
      ""
    ],
    "filter.methods":[
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp":[
      ""
    ]
}
```

>[!CAUTION]
>
>Het blijft de verantwoordelijkheid van de klant om:
>
>* alleen toegang verlenen tot vertrouwde domeinen
>* ervoor zorgen geen gevoelige informatie wordt blootgesteld
>* geen jokerteken gebruiken [*] syntaxis; dit zal allebei voor authentiek verklaarde toegang tot het eindpunt van GraphQL onbruikbaar maken en zal het aan de volledige wereld ook blootstellen.


>[!CAUTION]
>
>Alle GraphQL [schema&#39;s](#schema-generation) (afgeleid van Content Fragment Models die **Ingeschakeld**) zijn leesbaar door het eindpunt GraphQL.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, aangezien deze op deze manier kunnen worden gelekt; Dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.
