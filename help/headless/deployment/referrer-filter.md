---
title: Configuratie van filter Referrer met AEM zonder kop
description: Met het filter Adobe Experience Manager Referrer kunt u toegang krijgen van andere hosts. Een configuratie OSGi voor de Filter van de Referateur is nodig om toegang tot het eindpunt van GraphQL voor headless toepassingen toe te laten.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Refererfilter {#referrer-filter}

Met het filter Adobe Experience Manager Referrer kunt u toegang krijgen van andere hosts.

Een configuratie OSGi voor de Filter van de Referateur is nodig om toegang tot het eindpunt van GraphQL voor hoofdloze toepassingen over de POST van HTTP toe te laten. Wanneer het gebruiken van AEM Zwaarteloze Vraag die tot AEM over de GET van HTTP toegang hebben, is een configuratie van de Filter van de Referateur niet nodig.

>[!WARNING]
> AEM de Filter van de Referateur is geen OSGi- configuratiemechanisme, die betekent slechts één configuratie actief op de AEM dienst tegelijkertijd is. Voeg waar mogelijk geen aangepaste filterconfiguraties van Referrer toe, aangezien dit AEM native configuraties overschrijft en de productfunctionaliteit kan onderbreken.

Dit wordt gedaan door een aangewezen configuratie OSGi voor de Filter toe te voegen Referrer die:

* geeft de hostnaam van een vertrouwde website op; ofwel `allow.hosts` ofwel `allow.hosts.regexp` ,
* verleent toegang voor deze gastheernaam.

De bestandsnaam moet `org.apache.sling.security.impl.ReferrerFilter.cfg.json` zijn.

Als u bijvoorbeeld toegang wilt verlenen voor aanvragen bij de Referenter `my.domain` , kunt u:

```xml
{
    "allow.empty": false,
    "allow.hosts": [
      "my.domain"
    ],
    "allow.hosts.regexp": [
      ""
    ],
    "filter.methods": [
      "POST",
      "PUT",
      "DELETE",
      "COPY",
      "MOVE"
    ],
    "exclude.agents.regexp": [
      ""
    ]
}
```

>[!CAUTION]
>
>De klant blijft verantwoordelijk voor:
>
>* alleen toegang verlenen tot vertrouwde domeinen
>* ervoor zorgen geen gevoelige informatie wordt blootgesteld
>* Gebruik geen vervangingswaarde [ * ] syntaxis; dit zal zowel voor authentiek verklaarde toegang tot het eindpunt van GraphQL onbruikbaar maken als het aan de volledige wereld blootstellen.

>[!CAUTION]
>
>Alle schema&#39;s van GraphQL [ ](#schema-generation) (die uit de Modellen van het Fragment van de Inhoud worden afgeleid die **** zijn toegelaten) zijn leesbaar door het eindpunt van GraphQL.
>
>Dit betekent dat u ervoor moet zorgen dat er geen gevoelige gegevens beschikbaar zijn, omdat deze op deze manier kunnen worden uitgelekt; dit omvat bijvoorbeeld informatie die als veldnamen in de modeldefinitie aanwezig kan zijn.
