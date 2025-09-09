---
title: Inleiding tot bereikobjecten in aangepaste functies
description: Het formulier ondersteunt bereikobjecten in aangepaste functies die als laatste argument worden doorgegeven aan functies wanneer de regel wordt uitgevoerd.
keywords: bereikobjecten in aangepaste functies, algemene objecten en veldobjecten.
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 248c75a5-6335-41d2-aa0a-28a20a710f88
source-git-commit: e2bc958104bd9b75845ad2c213eec18d2560a3a4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Object Scope in aangepaste functies

In Adaptief Forms wordt een bereikobject als laatste argument doorgegeven aan functies wanneer een regel wordt uitgevoerd. Deze kan worden gebruikt om formulier-/veldeigenschappen te lezen en het formulier vanuit de functies te wijzigen. Het bereikobject bevat een alleen-lezen proxyobject voor het formulier, de getriggerde gebeurtenis en het doelveld. De eigenschappen van het formulier en het veld zijn toegankelijk via het object scope door `$` toe te voegen, bijvoorbeeld `scope.form.$id` en `scope.field.$id` .

## Formulierwijzigingfuncties met bereikobject

Object Scope heeft de volgende functies voor formulierwijziging:

| Functie | Syntaxis | Beschrijving | Codevoorbeeld |
|-----------------|--------|-------------|-------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Hiermee wordt een eigenschap op het doelveld ingesteld met de eigenschap `$payload` . | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) om het voorbeeld te bekijken. |
| **bevestigt** | `validate([any $element])` | Hiermee wordt validatie uitgevoerd op het doelveld. Hiermee wordt validatie uitgevoerd op het gehele formulier als er geen doel is opgegeven, en wordt een array met validatiefouten geretourneerd. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) om het voorbeeld te bekijken. |
| **teruggestelde** *(afgekeurd)* | `reset([any $element])` | Vervangen. Gebruik in plaats hiervan `dispatchEvent($target, 'reset')` . Hiermee herstelt u het doelveld of, als er geen doel is opgegeven, herstelt u het hele formulier. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) om het voorbeeld te bekijken. |
| **importData** | `importData(any $payload)` | Hiermee importeert u gegevens in het formulier, waarbij bestaande formuliergegevens worden vervangen. Als `qualifiedName` is opgegeven, worden alleen gegevens in dat containerveld geïmporteerd. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) om het voorbeeld te bekijken. |
| **exportData** | `exportData()` | Retourneert de gegevens van het formulier. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) om het voorbeeld te bekijken. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Triggert een verzonden formulier. U kunt opgeven wat u wilt verzenden via de parameter `$payload` en het inhoudstype instellen via de parameter `$contentType` . Gegevens worden standaard verzonden als `multipart/form-data` . Met de optionele parameter `$validateForm` wordt opgegeven of het formulier moet worden gevalideerd vóór verzending (standaard: true). Als de bewerking succesvol is, wordt `submitSuccess` geactiveerd; als de bewerking mislukt, wordt `submitError` geactiveerd. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) om het voorbeeld te bekijken. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Hiermee wordt de focus ingesteld op het doelveld, dat een deelvenster of formulierveld kan zijn. Als geen doel wordt verstrekt, wordt de nadruk geplaatst aan het gebied dat de regel teweegbracht. Met de optionele parameter `$focusOption` wordt opgegeven of het volgende of vorige item ten opzichte van het doel de focus moet krijgen. Ondersteunde waarden: `'nextItem'`, `'previousItem'` . Bij gebruik met een deelvenster blijft de navigatie beperkt tot dat deelvenster. Indien gebruikt met een veld, vindt navigatie plaats binnen het bovenliggende deelvenster van dat veld. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) om het voorbeeld te bekijken. |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Verzendt een gebeurtenis van het type `$eventName` op het element dat door `$target` wordt bepaald. Als er geen doel is opgegeven, wordt de gebeurtenis verzonden op het formulier. De optionele `$payload` is beschikbaar voor expressies die de gebeurtenis afhandelen. De optionele parameter `$dispatch` bestuurt het gedrag van de gebeurtenisdoorgave. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) om het voorbeeld te bekijken. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Hiermee markeert u het veld dat door `$fieldIdentifier` wordt aangegeven als ongeldig en geeft u `$validationMessage` weer. De optionele parameter `$option` geeft aan of `$fieldIdentifier` wordt geïnterpreteerd als `id` , `dataRef` of `qualifiedName` . De standaardwaarde is `{useId: true}` . Ondersteunde waarden: `{useId: true}`, `{useDataRef: true}`, `{useQualifiedName: true}` . | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) om het voorbeeld te bekijken. |

## Zie ook

{{see-also-rule-editor}}

