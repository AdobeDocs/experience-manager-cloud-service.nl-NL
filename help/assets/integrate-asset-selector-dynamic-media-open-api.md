---
title: De Selecteur van activa voor  [!DNL Adobe Experience Manager]  als a  [!DNL Cloud Service]
description: Integreer de selecteur van Activa met diverse Adobe, niet-Adobe, en derdetoepassingen.
role: Admin, User
exl-id: b01097f3-982f-4b2d-85e5-92efabe7094d
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '902'
ht-degree: 0%

---

# Integratie voor Dynamic Media met OpenAPI-mogelijkheden {#integrate-asset-selector-dynamic-media-open-apis}

| [ Beste praktijken van het Onderzoek ](/help/assets/search-best-practices.md) | [ Beste praktijken van Meta-gegevens ](/help/assets/metadata-best-practices.md) | [ Content Hub ](/help/assets/product-overview.md) | [ Dynamic Media met mogelijkheden OpenAPI ](/help/assets/dynamic-media-open-apis-overview.md) | [ de ontwikkelaarsdocumentatie van AEM Assets ](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Met Asset Selector kunt u de verschillende toepassingen voor Adobe integreren, zodat deze naadloos kunnen samenwerken.


## Vereisten {#prereqs-polaris}

Gebruik de volgende voorwaarden als u Asset Selector integreert met Dynamic Media met OpenAPI-mogelijkheden:

* [Communicatiemethoden](/help/assets/overview-asset-selector.md#prereqs)
* Voor toegang tot Dynamic Media met OpenAPI-mogelijkheden hebt u licenties nodig voor:
   * Assets repository (bijvoorbeeld Experience Manager Assets as a Cloud Service).
   * AEM Dynamic Media.
* Slechts [ goedgekeurde activa ](/help/assets/approve-assets.md) zijn beschikbaar voor gebruik die merkconsistentie verzekeren.

## Integratie voor Dynamic Media met OpenAPI-mogelijkheden {#adobe-app-integration-polaris}

De integratie van Asset Selector met het Dynamic Media OpenAPI-proces omvat verschillende stappen, zoals het maken van een aangepaste dynamische media-URL of het kiezen van de URL voor dynamische media, enz.

### Asset Selector voor Dynamic Media integreren met OpenAPI-mogelijkheden {#integrate-dynamic-media}

De eigenschappen `rootPath` en `path` mogen geen deel uitmaken van de Dynamic Media met OpenAPI-mogelijkheden. In plaats daarvan kunt u de eigenschap `aemTierType` configureren. Hier volgt de syntaxis van de configuratie:

```
aemTierType:[1: "delivery"]
```

Met deze configuratie kunt u alle goedgekeurde elementen weergeven zonder mappen of als een platte structuur. Voor meer informatie, navigeer aan `aemTierType` bezit onder [ de eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md).


### Een URL voor dynamische levering maken op basis van goedgekeurde elementen {#create-dynamic-media-url}

Nadat u Asset Selector hebt ingesteld, wordt een objectschema gebruikt om een URL voor dynamische levering te maken van de geselecteerde elementen.
Bijvoorbeeld een schema van één object van een array met objecten die wordt ontvangen bij de selectie van een element:

```
{
"dc:format": "image/jpeg",
"repo:assetId": "urn:aaid:aem:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
"repo:name": "image-7.jpg",
"repo:repositoryId": "delivery-pxxxx-exxxxxx.adobe.com",
...
}
```

Alle geselecteerde elementen worden gedragen door de functie `handleSelection` die als een JSON-object fungeert. Bijvoorbeeld `JsonObj` . De dynamische leverings-URL wordt gemaakt door de onderstaande dragers te combineren:

| Object | JSON |
|---|---|
| Host | `assetJsonObj["repo:repositoryId"]` |
| API-hoofdmap | `/adobe/dynamicmedia/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"].split(".").slice(0,-1).join(".")` |
| format | `.jpg` |

#### API-specificatie voor levering van goedgekeurde middelen {#approved-assets-delivery-api-specification}

URL-indeling:
`https://<delivery-api-host>/adobe/dynamicmedia/deliver/<asset-id>/<seo-name>.<format>?<image-modification-query-parameters>`

Wanneer

* Host is `https://delivery-pxxxxx-exxxxxx.adobe.com`
* API-hoofdmap is `"/adobe/dynamicmedia/deliver"`
* `<asset-id>` is element-id
* `<seo-name>` is de naam van een element
* `<format>` is de uitvoerindeling
* `<image modification query parameters>` als ondersteuning door de API-specificatie voor levering van goedgekeurde middelen

#### API voor levering van goedgekeurde middelen {#approved-assets-delivery-api}

De dynamische leverings-URL heeft de volgende syntaxis:
`https://<delivery-api-host>/adobe/assets/deliver/<asset-id>/<seo-name>` , waarbij:

* Host is `https://delivery-pxxxxx-exxxxxx.adobe.com`
* API-hoofdmap voor originele uitvoering is `"/adobe/assets/deliver"`
* `<asset-id>` is element-id
* `<seo-name>` is naam van de activa die al dan niet een uitbreiding kunnen hebben

### Gereed om dynamische URL voor levering te kiezen {#ready-to-pick-dynamic-delivery-url}

Alle geselecteerde elementen worden gedragen door de functie `handleSelection` die als een JSON-object fungeert. Bijvoorbeeld `JsonObj` . De dynamische leverings-URL wordt gemaakt door de onderstaande dragers te combineren:

| Object | JSON |
|---|---|
| Host | `assetJsonObj["repo:repositoryId"]` |
| API-hoofdmap | `/adobe/assets/deliver` |
| asset-id | `assetJsonObj["repo:assetId"]` |
| seo-name | `assetJsonObj["repo:name"]` |

Hieronder ziet u de twee manieren waarop u het JSON-object kunt doorlopen:

![ Dynamische levering url ](assets/dynamic-delivery-url.png)

* **Duimnagel:** de duimnagels kunnen beelden zijn en de activa zijn PDF, video, beelden, etc. Hoewel u de hoogte- en breedtekenmerken van de miniatuur van een element kunt gebruiken als de dynamische uitvoering van het element.
De volgende set uitvoeringen kan worden gebruikt voor de elementen van het type PDF:
Als er eenmaal een PDF is geselecteerd in sidekick, wordt in de selectiecontext de onderstaande informatie weergegeven. Hieronder ziet u de manier waarop u het JSON-object kunt doorlopen:

  <!--![Thumbnail dynamic delivery url](image-1.png)-->

  U kunt naar `selection[0].....selection[4]` verwijzen voor de array van vertoningskoppelingen uit de bovenstaande schermafbeelding. De belangrijkste eigenschappen van een van de miniatuuruitvoeringen zijn bijvoorbeeld:

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/as/algorithm design.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

In het bovenstaande scherm moet de bezorgings-URL van de oorspronkelijke uitvoering worden opgenomen in de doelervaring als PDF vereist is en niet de bijbehorende miniatuur. Bijvoorbeeld: `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:8560f3a1-d9cf-429d-a8b8-d81084a42d41/original/as/algorithm design.pdf?accept-experimental=1`

* **Video:** u videospeler URL voor de videotypeactiva kunt gebruiken die ingebedde iFrame gebruiken. U kunt de volgende arrayuitvoeringen gebruiken in de doelervaring:
  <!--![Video dynamic delivery url](image.png)-->

  ```
  { 
      "height": 319, 
      "width": 319, 
      "href": "https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/as/asDragDrop.2.jpg?accept-experimental=1&width=319&height=319&preferwebp=true", 
      "type": "image/webp" 
  } 
  ```

  U kunt naar `selection[0].....selection[4]` verwijzen voor de array van vertoningskoppelingen uit de bovenstaande schermafbeelding. De belangrijkste eigenschappen van een van de miniatuuruitvoeringen zijn bijvoorbeeld:

  Het codefragment in de bovenstaande schermafbeelding is een voorbeeld van een video-element. De array met uitvoeringen bevat koppelingen. `selection[5]` in het fragment is het voorbeeld van een afbeeldingsminiatuur die kan worden gebruikt als tijdelijke aanduiding voor een videominiatuur in de doelervaring. De `selection[5]` in de array van uitvoeringen is voor de videospeler. Dit dient een HTML en kan worden ingesteld als `src` van het iframe. De functie ondersteunt adaptieve bitsnelheidstreaming, dat wil zeggen, voor het web geoptimaliseerde levering van de video.

  In het bovenstaande voorbeeld is de URL van de videospeler `https://delivery-pxxxxx-exxxxx-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2fdef732-a452-45a8-b58b-09df1a5173cd/play?accept-experimental=1`

### Aangepaste filters configureren {#configure-custom-filters-dynamic-media-open-api}

Met Asset Selector for Dynamic Media met OpenAPI-mogelijkheden kunt u aangepaste eigenschappen en de daarop gebaseerde filters configureren. De eigenschap `filterSchema` wordt gebruikt om dergelijke eigenschappen te configureren. De aanpassing kan worden weergegeven als `metadata.<metadata bucket>.<property name>.` waartegen de filters kunnen worden geconfigureerd, waarbij:

* `metadata` is de informatie van een element
* `embedded` de statische parameter is die voor configuratie wordt gebruikt, en
* `<propertyname>` is de filternaam die u configureert

Voor de configuratie worden eigenschappen die op `jcr:content/metadata/` niveau worden bepaald blootgesteld als `metadata.<metadata bucket>.<property name>.` voor de filters die u wilt vormen.

In Asset Selector for Dynamic Media met OpenAPI-mogelijkheden wordt bijvoorbeeld een eigenschap op `asset jcr:content/metadata/client_name:market` omgezet in `metadata.embedded.client_name:market` voor filterconfiguratie.

Voor het ophalen van de naam moet een eenmalige activiteit worden uitgevoerd. Maak een onderzoek API vraag naar de activa en krijg de bezitsnaam (de emmer, hoofdzakelijk).

### Gebruikersinterface voor Asset Selector voor Dynamic Media met OpenAPI-mogelijkheden {#interface-dynamic-media-open-api}

Na integratie met de Micro-Frontend Asset Selector van de Adobe, kunt u de activa slechts structuur van alle goedgekeurde activa zien beschikbaar in de opslagplaats van activa van de Experience Manager.

![ Dynamic Media met OpenAPI mogelijkheden UI ](assets/polaris-ui.png)

* **A**: [ verberg/toon paneel ](#hide-show-panel)
* **B**: [ Assets ](#repository)
* **C**: [ Sorterend ](#sorting)
* **D**: [ Filters ](#filters)
* **E**: [ bar van het Onderzoek ](#search-bar)
* **F**: [ Sorterend in het stijgen of dalende orde ](#sorting)
* **G**: Cancel Selectie
* **H**: Selecteer enige of veelvoudige activa

>[!MORELIKETHIS]
>
>* [ integreer de Selector van Activa met diverse toepassingen ](/help/assets/integrate-asset-selector.md)
>* [ Eigenschappen van de Selecteur van Activa ](/help/assets/asset-selector-properties.md)
>* [ de aanpassingen van de Selecteur van Activa ](/help/assets/asset-selector-customization.md)
