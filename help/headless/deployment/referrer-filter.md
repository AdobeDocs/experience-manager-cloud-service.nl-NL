---
title: Configuratie van filter Referrer met AEM zonder kop
description: Met het filter Adobe Experience Manager Referrer kunt u toegang krijgen van andere hosts. Een configuratie OSGi voor de Filter van de Referateur is nodig om toegang tot het eindpunt van GraphQL voor headless toepassingen toe te laten.
feature: Headless, GraphQL API
exl-id: e2e3d2dc-b839-4811-b5d1-38ed8ec2cc87
solution: Experience Manager
role: Admin, Developer
source-git-commit: 3096436f8057833419249d51cb6c15e6c28e9e13
workflow-type: tm+mt
source-wordcount: '322'
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

## Voorbeeldconfiguratie {#example-configuration}

Als u bijvoorbeeld toegang wilt verlenen voor aanvragen bij de Referenter `my.domain` , kunt u:

>[!CAUTION]
>
>Dit is een eenvoudig voorbeeld dat de standaardconfiguratie kan overschrijven. U moet ervoor zorgen dat productupdates altijd op om het even welke aanpassingen worden toegepast.

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

## Gegevensbeveiliging {#data-security}

>[!CAUTION]
>
>Het blijft uw verantwoordelijkheid om de volgende punten volledig aan te pakken.

Om ervoor te zorgen dat uw gegevens veilig blijven, moet u ervoor zorgen dat:

* de toegang wordt **slechts** verleend aan vertrouwde op domeinen

* de vervanging [`*`] syntaxis in **niet** gebruikte; dit maakt allebei voor authentiek verklaarde toegang tot het eindpunt van GraphQL onbruikbaar, en stelt het ook aan de volledige wereld bloot

* De gevoelige informatie wordt **nooit** blootgesteld; noch direct, noch onrechtstreeks:

   * Bijvoorbeeld, zijn alle [&#x200B; schema&#39;s van GraphQL &#x200B;](/help/headless/graphql-api/content-fragments.md#schema-generation):

      * afgeleid uit de Modellen van het Fragment van de Inhoud die **&#x200B;**&#x200B;zijn toegelaten

     **en**

      * zijn leesbaar door het eindpunt van GraphQL

     Dit betekent dat informatie die in de modeldefinitie als veldnamen voorkomt, beschikbaar kan komen.

U moet ervoor zorgen dat er op geen enkele wijze gevoelige gegevens beschikbaar zijn, dus dergelijke details moeten zorgvuldig in overweging worden genomen.
