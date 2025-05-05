---
title: Een transactie opnemen voor aangepaste implementaties
description: Gebruik de API TransactionRecorder om handelingen op te nemen die niet automatisch als transacties worden beschouwd
feature: Adaptive Forms, Foundation Components
exl-id: cb584f78-30af-4a58-be99-843352e8249c
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 2%

---

# Een transactie opnemen voor aangepaste implementaties {#record-a-transaction-for-custom-implementations}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/forms/transaction-reports/transaction-reports-osgi/record-transaction-custom-implementation) |
| AEM as a Cloud Service | Dit artikel |

Gebruik de TransactieRecorder API om acties te registreren die niet automatisch als transacties worden rekenschap gegeven.

U kunt aangepaste code gebruiken om een PDF-formulier te verzenden. U kunt ook een formulier verzenden met aangepaste methoden in plaats van verzendmethoden te gebruiken die bij AEM Forms worden geleverd. Alle eerder genoemde acties en aangepaste implementaties van AEM Forms API&#39;s worden niet als transacties beschouwd. AEM Forms verstrekt API, [ TransactionRecorder ](https://javadoc.io/doc/com.adobe.aem/aem-forms-sdk-api/latest/com/adobe/aem/transaction/core/ITransactionRecorder.html), om dergelijke acties zoals transacties te registreren.

Om een transactie te registreren, schrijf het [ standaard sling servlet ](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/store-and-retrieve-af-with-2fa/create-servlet.html?lang=nl-NL) en vraag servlet van een cliënt om een transactie te registreren. U kunt servlet roepen gebruikend AJAX of een andere standaardmethode.

## Voorbeeld van servercode {#sample-server-sided-code}

U kunt de onderstaande voorbeeldcode gebruiken om de TransactionRecorder-API uit te voeren vanuit een Java™-klasse met behulp van een aangepaste OSGi-bundel.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;

doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## Voorbeeld van code aan clientzijde {#sample-client-side-code}

U kunt de hieronder steekproefcode gebruiken om servlet te roepen die `TransactionRecorder` API heeft.

```javascript
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1,
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## Verwante artikelen {#related-articles}

* [Transactierapporten Billable API&#39;s](/help/forms/transaction-reports-billable-apis.md)
