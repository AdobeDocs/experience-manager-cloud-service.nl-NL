---
title: Zoeken in Assets API
description: Leer hoe u de zoek-Assets API gebruikt.
role: User
exl-id: 0c52e793-4c33-4230-b4f2-27296dd9e4b3
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Zoeken in Assets API {#search-assets-api}

Alle [ goedgekeurde activa ](approve-assets.md) beschikbaar in de activa van Experience Manager bewaarplaats kan worden gezocht en dan aan geïntegreerde stroomafwaartse toepassingen worden geleverd gebruikend een Levering URL.

Het zoeken naar de juiste goedgekeurde middelen van de Experience Manager-opslagplaats is de eerste stap naar het leveren van middelen via de bezorgings-URL. Het antwoord op het zoekverzoek bestaat uit een array van JSON-documenten die overeenkomen met de elementen die aan de zoekcriteria voldoen. Elk JSON-document wordt geïdentificeerd met behulp van een `id` -veld, dat wordt gebruikt om de aanvraag voor het leveren van elementen samen te stellen.

![ Overzicht van direct binair upload protocol ](assets/search-assets-api-overview.png)

U kunt eigenschappen definiëren in de aanvraag Zoeken in Assets API om de volgende mogelijkheden in te schakelen:

* **full-text onderzoek**: Gebruik de `match` vraag om de tekst te bepalen aan onderzoek.  U kunt operatoren binnen de query van `match` ook gebruiken om de resultaten te filteren.

* **pas filters** toe: Gebruik de `term` vraag aan filters de resultaten verder door a `key` en één of veelvoudige waarden te bepalen. `key` geeft het veld aan waarvan de waarde moet worden aangepast en `value` geeft aan met welke waarde moet worden vergeleken. Op dezelfde manier kunt u de query `range` gebruiken om een bereik voor een veld te definiëren met de eigenschappen Groter dan (gt), Groter-dan of Gelijk-aan (gte), Kleiner-dan (lt) en Kleiner-dan of gelijk-aan (lte).

* **de resultaten van de Soort**: Gebruik het `OrderBy` bezit aan soortonderzoeksresultaten die op één of veelvoudige gebieden worden gebaseerd. U kunt de resultaten in oplopende of aflopende volgorde sorteren.

* **Paginering**: Gebruik `limit` en `cursor` eigenschappen om pagineringseigenschappen binnen een Onderzoek API verzoek te bepalen. De eigenschap `limit` definieert het maximum aantal items dat in een API-reactie moet worden opgehaald. De eigenschap `cursor` kan het beginpunt voor de volgende set elementen ophalen die in de eigenschap `limit` zijn gedefinieerd. Als u bijvoorbeeld `50` definieert als de limiet in de API-aanvraag, kunt u de eigenschap `cursor` gebruiken om de volgende 50 items te starten en op te halen met de volgende API-aanvraag.

## API-eindpunt van zoekmiddelen {#search-assets-api-endpoint}

Het eindpunt in een API-aanvraag voor zoekmiddelen moet de volgende indeling hebben:
`https://delivery-pXXXX-eYYYY.adobeaemcloud.com/adobe/assets/search`

Het leveringsdomein is qua structuur vergelijkbaar met het domein van de Experience Manager-auteuromgeving. Het enige verschil is het vervangen van de term `author` door `delivery` .

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

Om de zoek-API aan te roepen, is een IMS-token vereist om in de `Authorization` -details te definiëren. De token IMS wordt opgehaald van een technische account. Zie [ Vetsen de Referenties van AEM as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#fetch-the-aem-as-a-cloud-service-credentials) om een nieuwe technische rekening tot stand te brengen. Zie [ Genererend het toegangstoken ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/generating-access-tokens-for-server-side-apis.html?lang=en#generating-the-access-token) om het teken IMS te produceren en het te gebruiken geschikt in de activaAPI van het Onderzoek verzoekkopbal.

Om verzoeksteekproeven, reactiemonsters, en reactiecodes te bekijken, zie [ Onderzoek Assets API ](https://adobe-aem-assets-delivery-experimental.redoc.ly/#operation/search).
