---
title: Hoe kan de FDM-service (Form Data Model) van Adaptive Forms worden aangeroepen met behulp van API's?
description: Verklaart invokeWebServices API die u kunt gebruiken om Webdiensten aan te halen die in WSDL van binnen een Adaptief gebied van de Vorm worden geschreven.
uuid: 40561086-e69d-4e6a-9543-1eb2f54cd836
topic-tags: develop
discoiquuid: aa3e50f1-8f5a-489d-a42e-a928e437ab79
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---


# API om de FDM-service (Form Data Model) aan te roepen vanuit Adaptive Forms {#api-to-invoke-form-data-model-service-from-adaptive-forms}

## Overzicht {#overview}

[!DNL AEM Forms] Hiermee kunnen auteurs van formulieren de invulervaring van formulieren verder vereenvoudigen en verbeteren door services aan te roepen die in een formuliergegevensmodel (FDM) zijn geconfigureerd vanuit een adaptief formulierveld. Als u een gegevensmodelservice wilt aanroepen, kunt u een regel maken in de visuele editor of een JavaScript opgeven met de `guidelib.dataIntegrationUtils.executeOperation` API in de code-editor van de [regeleditor](rule-editor.md).

Dit document is vooral bedoeld voor het schrijven van een JavaScript met het `guidelib.dataIntegrationUtils.executeOperation` API om de service aan te roepen.

## De API gebruiken {#using-the-api}

De `guidelib.dataIntegrationUtils.executeOperation` API roept een service aan vanuit een adaptief formulierveld. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs)
```

De structuur van de `guidelib.dataIntegrationUtils.executeOperation` API specificeert details over de de dienstverrichting. De syntaxis van de structuur ziet er als volgt uit.

```javascript
var operationInfo = {
formDataModelId,
operationTitle,
operationName
};
var inputs = {
inputField1,
inputFieldN
};
var outputs = {
outputField1,
outputFieldN
}
```

De API-structuur geeft de volgende details over de servicebewerking op.

<table>
 <tbody>
  <tr>
   <th>Parameter</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td><code>operationInfo</code></td>
   <td>Structuur voor het opgeven van de id van het formuliergegevensmodel, de bewerkingstitel en de naam van de bewerking</td>
  </tr>
  <tr>
   <td><code>formDataModelId</code></td>
   <td>Geeft het opslagpad aan naar het formuliergegevensmodel (FDM) met de naam ervan</td>
  </tr>
  <tr>
   <td><code>operationName</code></td>
   <td>Specificeert de naam van de uit te voeren de dienstverrichting</td>
  </tr>
  <tr>
   <td><code>inputs</code></td>
   <td>Hiermee worden een of meer formulierobjecten toegewezen aan de invoerargumenten voor de servicebewerking</td>
  </tr>
  <tr>
   <td><code>Outputs</code></td>
   <td>Hiermee wijst u een of meer formulierobjecten toe aan uitvoerwaarden van de servicebewerking om formuliervelden te vullen<br /> </td>
  </tr>
  <tr>
   <td><code>success</code></td>
   <td>Retourneert waarden die zijn gebaseerd op de invoerargumenten voor de servicebewerking. Het is een optionele parameter die als callback functie wordt gebruikt.<br /> </td>
  </tr>
  <tr>
   <td><code>failure</code></td>
   <td>Toont een foutenmelding als de succesvolle callback functie er niet in slaagt om de outputwaarden te tonen die op de inputargumenten worden gebaseerd. Het is een optionele parameter die als callback functie wordt gebruikt.<br /> </td>
  </tr>
 </tbody>
</table>

## Voorbeeldscript om een service aan te roepen {#sample-script-to-invoke-a-service}

In het volgende voorbeeldscript wordt het `guidelib.dataIntegrationUtils.executeOperation` API om de `getAccountById` de dienstverrichting die in `employeeAccount` formuliergegevensmodel (FDM).

De `getAccountById` de bewerking neemt de waarde in de `employeeID` formulierveld als invoer voor de `empId` argument en retourneert werknemersnaam, accountnummer en rekeningsaldo voor de corresponderende werknemer. De uitvoerwaarden worden ingevuld in de opgegeven formuliervelden. De waarde in `name` argument is ingevuld in het dialoogvenster `fullName` formulierelement en -waarde voor `accountNumber` argument in `account` formulierelement.

```javascript
var operationInfo = {
"formDataModelId": "/content/dam/formsanddocuments-fdm/employeeAccount",
"operationName": "getAccountDetails"
};
var inputs = {
"empid" : employeeID
};
var outputs = {
"name" : fullName,
"accountNumber" : account,
"balance" : balance
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
```

## API gebruiken met callback-functie {#using-the-api-callback}

U kunt ook de service Formuliergegevensmodel inschakelen met de `guidelib.dataIntegrationUtils.executeOperation` API met een callback-functie. De API-syntaxis ziet er als volgt uit:

```javascript
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, callbackFunction)
```

De callback functie kan `success` en `failure` callback-functies.

### Sampletcript van de steekproef met succes en mislukkingscallback functies {#callback-function-success-failure}

In het volgende voorbeeldscript wordt het `guidelib.dataIntegrationUtils.executeOperation` API om de `GETOrder` de dienstverrichting die in `employeeOrder` formuliergegevensmodel (FDM).

De `GETOrder` de bewerking neemt de waarde in de `Order ID` formulierveld als invoer voor de `orderId` argument en retourneert de waarde voor het aantal bestellingen in het dialoogvenster `success` callback-functie.  Als de `success` callback-functie retourneert niet de hoeveelheid van de volgorde, de `failure` callback-functie geeft de `Error occured` bericht.

>[!NOTE]
>
> Als u het `success` callback-functie, worden de uitvoerwaarden niet ingevuld in de opgegeven formuliervelden.

```javascript
var operationInfo = {
    "formDataModelId": "/content/dam/formsanddocuments-fdm/employeeOrder",
    "operationTitle": "GETOrder",
    "operationName": "GETOrder"
};
var inputs = {
    "orderId" : Order ID
};
var outputs = {};
var success = function (wsdlOutput, textStatus, jqXHR) {
order_quantity.value = JSON.parse(wsdlOutput).quantity;
 };
var failure = function(){
alert('Error occured');
};
guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, success, failure);
```
