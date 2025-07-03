---
title: Cache voor componenten en GraphQL wissen
description: Leer hoe u de Clear-Cache-functie in AEM CIF inschakelt en verifieert.
feature: Commerce Integration Framework
role: Admin
exl-id: f89c07c7-631f-41a4-b5b9-0f629ffc36f0
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Cache voor componenten en GraphQL wissen {#clear-cache}

Dit document bevat een uitgebreide handleiding voor het inschakelen en verifiëren van de functie voor het wissen van cache in AEM CIF.

>[!NOTE]
>
> Dit is een experimentele functie.

## Cache-functie wissen inschakelen in CIF-configuratie {#enable-clear-cache}

De functie clear-cache wordt standaard uitgeschakeld in de CIF-configuratie. Om het toe te laten, moet u het volgende aan uw overeenkomstige projecten toevoegen:

* Laat servlet `/bin/cif/invalidate-cache` toe die u helpt de duidelijk-geheime voorgeheugen API met hun overeenkomstige verzoeken teweegbrengen door de `com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json` configuratie in uw project toe te voegen zoals [ hier ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config.author/com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json) getoond.
  >[!NOTE]
  >
  > De configuratie moet slechts voor de auteursinstanties worden toegelaten.

* Laat de luisteraar toe om geheim voorgeheugen van elke instantie van AEM (te ontruimen publiceer en auteur) door de `com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json` configuratie in uw project toe te voegen zoals [ hier ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json) getoond.
   * Configuratie moet zijn ingeschakeld voor zowel auteur- als publicatieinstanties.
   * De Dispatcher-cache inschakelen (optioneel): u kunt de cacheinstelling voor de dispatcher wissen inschakelen door de eigenschap `enableDispatcherCacheInvalidation` in te stellen op true in de bovenstaande configuratie. Dit verstrekt functionaliteit om het geheime voorgeheugen van de verzender te ontruimen.
     >[!NOTE]
     >
     > Dit werkt alleen met publicatie-instanties.

   * Zorg er ook voor dat u het overeenkomende patroon opgeeft dat bij het product, de categorie en de CMS-pagina past, en dat u deze aan het bovenstaande configuratiebestand toevoegt om het uit de verzendcache te verwijderen.

* Als u de prestaties van SQL-query&#39;s wilt verbeteren om de bijbehorende pagina te zoeken die betrekking heeft op product en categorie, voegt u de corresponderende index toe aan uw project (aanbevolen). Voor meer informatie, zie [ cifCacheInvalidationSupport ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.apps/src/main/content/jcr_root/_oak_index/cifCacheInvalidationSupport/.content.xml).

## Cache-functie wissen verifiëren {#verify-clear-cache}

Om te controleren of alles correct is ingesteld:

* Trigger overeenkomstige servlet aan de Instantie AEM van de Auteur, bijvoorbeeld [ http://localhost:4502/bin/cif/invalidate-cache ](http://localhost:4502/bin/cif/invalidate-cache) en u zou een reactie van 200 HTTP moeten krijgen.
* Controleer of er een knooppunt is gemaakt onder het volgende pad in auteurinstanties: `/var/cif/cacheinvalidation` . De knooppuntnaam volgt dit patroon: `cmd_{{timestamp}}`.
* Verifieer dat de zelfde knoop in elke publicatieinstantie is gecreeerd.

Nu, om te controleren of de geheime voorgeheugens behoorlijk worden ontruimd:
1. Navigeer naar de corresponderende PLP- en PDP-pagina&#39;s.
2. Werk een product of categorienaam in de handels motor bij. De wijzigingen worden niet direct doorgevoerd in AEM op basis van cacheconfiguraties.
3. Trigger de servlet API zoals hier getoond:

   ```
   curl --location '{Author AEM Instance Url}/bin/cif/invalidate-cache' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: ••••••' \ // Mandatory
   --header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
   --data '{
       "productSkus": ["Sku1", "Sku2"], // Optional: Pass the corresponding sku which got updated.
       "categoryUids":["CategoryUid"], // Optional : Pass the corresponding category-uid which got updated.
       "storePath": "/content/venia/us/en", // Mandatory : Needs to be given to know for which site we are removing the clear cache.
   }'
   ```
Als alles goed gaat, worden de nieuwe veranderingen in elk geval weerspiegeld. Als de wijzigingen niet zichtbaar zijn op het publicatieexemplaar, probeert u de relevante PLP- en PDP-pagina&#39;s te openen in een browservenster van het type private/incognito.

>[!NOTE]
>
> Publiceer instanties kunnen veelvoudige niveau van geheim voorgeheugenlagen hebben. Deze functie is alleen verantwoordelijk voor het wissen van de cache van het interne geheugen en de verzender van AEM.

## Cache-validatie-API wissen {#clear-cache-api}

Dit is API die u moet teweegbrengen wanneer u geheim voorgeheugen van handel verwante gegevens van AEM wilde ontruimen.

Type aanvraag: `POST`

### Kopteksten

| Parameter | Waarde | Vereist/verplicht | Opmerking |
|------------------------------|-------------------|---|---|
| `Content-Type` | `application/json` | Vereist |  |
| `Authorization` | Overeenkomende gebruikersgegevens van auteur (Auth Type: Basic Auth) | Vereist | Voeg de bijbehorende gebruikersnaam en het bijbehorende wachtwoord toe. |


### Payload

In de volgende tabel worden bestaande kenmerken weergegeven die de functie uit het vak geeft. Deze `InvalidateType` -eigenschappen moeten worden gegeven in combinatie met een verplicht kenmerk (zoals `storePath` ).

| `invalidateType` | Waarde | Type (Array/String/Boolean) | Worden hiermee de cachegeheugen van de verzender gewist? | Opmerking |
|------------------------------|-------------------|---|---|---|
| `productSkus` | De sku van het product - die uit het geheime voorgeheugen moet worden ongeldig gemaakt. | Array | Ja | Wis het geheime voorgeheugen van intern geheugen gebruikend het volgende patroon:<br>```"\"sku\":\\s*\""```<br> Dispatcher <br><ul><li>Wis het PDP paginacache van overeenkomstige SKUs</li><li>Cache van de overeenkomstige categoriepagina wissen waarin deze bestaat (gebaseerd op de grafische reactie van de handel)</li><li>Cache wissen op basis van de volgende query:</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content, '{storePath}')<br>AND ( (content.[product] IN ('sku1','sku2') AND content.[productType] = 'combinedSku')<br> OR (content.[selection] IN ('sku1','sku2') AND content.[selectionType] IN ('combinedSku', 'sku')))``` |
| `categoryUids` | De uid van de categorie - die ongeldig moet worden gemaakt uit de cache. | Array | Ja | Wis het geheime voorgeheugen van intern geheugen gebruikend het volgende patroon:<br>```"\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\""```<br> Dispatcher <br><ul><li>Cache van categoriepagina&#39;s wissen voor corresponderende gegevens (inclusief de pagina met onderliggende categorieën)</li><li>Alle PDP-pagina&#39;s met de corresponderende categorieën wissen</li><li>Cache wissen op basis van de volgende query:</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content,'{storePath}')<br>AND ((content.[categoryId] in ('category1','category2')<br>AND content.[categoryIdType] in ('uid'))<br>OR (content.[category] in ('category1','category2') AND content.[categoryType] in ('uid')))``` |
| `regexPatterns` | Als u de GraphQL-responsgegevens op basis van het regex-patroon moet wissen, gebruikt u dit. | Array | Nee | |
| `cacheNames` | Deze waarden zijn gedefinieerd in de corresponderende CIF GraphQL client configuration factory >> Corresponding StorePath GraphQL configuration >> GraphQL cache configuration | Array | Nee | |
| `invalidateAll` | Waar of onwaar | Boolean | Ja | |

Deze lijst toont het verplichte bezit dat in elke API vraag moet worden overgegaan:

| Eigenschap | Waarde | Type (Array/String/Boolean) | Worden hiermee de cachegeheugen van de verzender gewist? | Opmerking |
|------------------------------|-------------------|---|---|---|
| `storePath` | Overeenkomende waarde van het sitepad vanaf waar de cache moet worden verwijderd (Voorbeeld: `/content/venia/us/en` als referentie met een venia-project). | String | Ja | Dit moet worden gegeven met de combinatie van `invalidateType.` |

### Voorbeeld-API-aanvraag

```
curl --location 'https://author-p10603-e145552-cmstg.adobeaemcloud.com/bin/cif/invalidate-cache' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
--data '{
"productSkus": ["VP01", "VT10"], // This will clear cache for the corresponding pages related with mentioned skus.
"categoryUids":["Mjk="], // This will clear cache for the corresponding pages related with mentioned categories.
"regexPatterns":["\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\"(Mjk=)\"", "\"sku\":\\s*\"(VP02|VP03)\""],
"cacheNames": ["venia/components/commerce/product"], // If this been added then it will clear respective caches for the corresponding storepath
"storePath": "/content/venia/us/en"
}'
```

## Uitbreidbaarheid {#clear-cache-extensibility}

Deze functie biedt niet alleen de kernfunctionaliteit, maar ook uitbreidbaarheid, zodat ontwikkelaars deze verder kunnen ontwikkelen en aanpassen als dat nodig is.

### Het bestaande kenmerk uitbreiden {#existing-attribute}

In gevallen waar het geheime voorgeheugen moet worden ontruimd die momenteel niet door de bestaande op attributen-gebaseerde functionaliteit (zoals `categoryUids`) worden behandeld, kunt u naar [ verwijzen dit verwijzingsdossier ](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/ExtendedCategoryUidInvalidation.java) om nieuwe patronen toe te voegen en extra `invalidatePaths` te bepalen die van het geheime voorgeheugen voorbij wat de huidige implementatiehandvatten zouden moeten worden ontruimd.

### Nieuw aangepast kenmerk toevoegen {#new-custom-attribute}

Als, bijvoorbeeld, u niet de bestaande attributen voor het ontruimen van het geheime voorgeheugen wilt gebruiken, dan hebt u de flexibiliteit om uw eigen attribuut tot stand te brengen en zijn overeenkomstige functionaliteit te bepalen.

* Als u slechts geheim voorgeheugen van het interne geheugen van AEM (de grafische reactie) moet ontruimen, dan moet u [ deze verwijzing ](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomInvalidation.java) volgen.
* Als u geheim voorgeheugen van het interne geheugen en het verzenders geheime voorgeheugen moet ontruimen, dan moet u [ deze verwijzing ](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomDispatcherInvalidation.java) volgen.
  >[!NOTE]
  >
  > U kunt de interne lege cache negeren door `null` voor de methode `getPatterns()` te retourneren.
