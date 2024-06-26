---
title: Zoeken in Assets API
description: Leer hoe u de zoek-Assets API gebruikt.
role: User
source-git-commit: 540aa876ba7ea54b7ef4324634f6c5e220ad19d3
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Zoeken in Assets API {#search-assets-api}

Alles [goedgekeurde activa](approve-assets.md) beschikbaar in de gegevensopslagplaats van de Experience Manager kan worden gezocht en dan aan geïntegreerde stroomafwaartse toepassingen worden geleverd gebruikend een Levering URL.

Het zoeken naar de juiste goedgekeurde middelen van de opslagplaats van de Experience Manager is de eerste stap naar het leveren van middelen met behulp van de leverings-URL. Het antwoord op het zoekverzoek bestaat uit een array van JSON-documenten die overeenkomen met de elementen die aan de zoekcriteria voldoen. Elk JSON-document wordt geïdentificeerd met behulp van een `id` veld, dat wordt gebruikt om de aanvraag voor levering van het element samen te stellen.

![Overzicht van het directe binaire upload protocol](assets/search-assets-api-overview.png)

U kunt eigenschappen definiëren in de aanvraag Zoeken in Assets API om de volgende mogelijkheden in te schakelen:

* **Volledige tekst zoeken**: Gebruik de `match` query om de tekst te definiëren waarnaar moet worden gezocht.  U kunt ook operatoren gebruiken in het dialoogvenster `match` vraag om de resultaten te filtreren.

* **Filters toepassen**: Gebruik de `term` vraag aan filters de resultaten verder door te bepalen `key` en een of meerdere waarden. `key` geeft het veld aan waarvan de waarde moet worden vergeleken en `value` staat voor wat er moet worden vergeleken met. U kunt ook de opdracht `range` query om een bereik voor een veld te definiëren met de eigenschappen Groter dan (gt), Groter dan of gelijk aan (gte), Minder dan (lt) en Kleiner dan of gelijk aan (lte).

* **Resultaten sorteren**: Gebruik de `OrderBy` eigenschap om zoekresultaten te sorteren op basis van een of meerdere velden. U kunt de resultaten in oplopende of aflopende volgorde sorteren.

* **Paginering**: Gebruik de `limit` en `cursor` eigenschappen voor het definiëren van eigenschappen voor paginering in een API-zoekopdracht. `limit` eigenschap definieert de maximale items die in een API-reactie kunnen worden opgehaald. `cursor` eigenschap vergemakkelijkt het ophalen van het beginpunt voor de volgende set elementen die zijn gedefinieerd in het dialoogvenster `limit` eigenschap. Als u bijvoorbeeld `50` als limiet in de API-aanvraag kunt u de `cursor` eigenschap om de volgende 50 items te starten en op te halen met de volgende API-aanvraag.

## API-eindpunt van zoekmiddelen {#search-assets-api-endpoint}

Het eindpunt in een API-aanvraag voor zoekmiddelen moet de volgende indeling hebben:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Het leveringsdomein is gelijkaardig in structuur aan het domein van de de auteur van de Experience Manager. Het enige verschil is het vervangen van de term `author` with `delivery`.

`pXXXX` verwijst naar de programma-id

`eYYYY` verwijst naar de milieu-id

## API-aanvraagmethode voor zoekmiddelen {#search-assets-api-request-method}

POST

## Zoeken in Assets API-header {#search-assets-api-header}

U moet de volgende gegevens opgeven wanneer u een header definieert in de API voor zoekmiddelen:

```java
headers: {
      'Content-Type': 'application/json',
      'X-Adobe-Accept-Experimental': '1',
      Authorization: 'Bearer <YOUR_JWT_HERE>',
      'X-Api-Key': 'YOUR_API_KEY_HERE'
    },
```

Om de zoek-API aan te roepen, is een IMS-token vereist voor het definiëren van de functie `Authorization` details. De token IMS wordt opgehaald van een technische account. Zie [Credentials van AEM as a Cloud Service ophalen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) om een nieuwe technische rekening op te stellen. Zie [Het toegangstoken genereren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) om de IMS-token te genereren en deze op de juiste wijze te gebruiken in de aanvraagheader van de API voor zoekmiddelen.

Als u aanvraagvoorbeelden, responsvoorbeelden en responscodes wilt weergeven, raadpleegt u [Zoeken in Assets API](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).

