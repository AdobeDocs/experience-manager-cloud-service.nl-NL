---
title: Inleiding tot bereikobjecten in aangepaste functies
description: Het formulier ondersteunt bereikobjecten in aangepaste functies die als laatste argument worden doorgegeven aan functies wanneer de regel wordt uitgevoerd.
keywords: bereikobjecten in aangepaste functies, algemene objecten en veldobjecten.
feature: Adaptive Forms, Core Components
role: User, Developer
source-git-commit: af211649a4f22d06f4e8669335a8267ee948a408
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Object Scope in aangepaste functies

In Adaptief Forms wordt een bereikobject als laatste argument doorgegeven aan functies wanneer een regel wordt uitgevoerd. Deze kan worden gebruikt om formulier-/veldeigenschappen te lezen en het formulier vanuit de functies te wijzigen. Het bereikobject bevat een alleen-lezen proxyobject voor het formulier, de getriggerde gebeurtenis en het doelveld. De eigenschappen van het formulier en het veld zijn toegankelijk via het object scope door `$` toe te voegen, bijvoorbeeld `scope.form.$id` en `scope.field.$id` .

## Formulierwijzigingfuncties met bereikobject

Object Scope heeft de volgende functies voor formulierwijziging:

| Functie | Syntaxis | Beschrijving | Codevoorbeeld |
|-----------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------|
| **setProperty** | `setProperty(any $element, any $payload)` | Stelt een eigenschap van de `$element` in met de eigenschap `$payload` . | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#show-a-panel-using-the-setproperty-rule) om het voorbeeld te bekijken. |
| **bevestigt** | `validate([any $element])` | Hiermee wordt validatie uitgevoerd op `$element` . Als er geen element is opgegeven, wordt het gehele formulier gevalideerd. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#validate-the-field) om het voorbeeld te bekijken. |
| **teruggestelde** | `reset([any $element])` | Hiermee stelt u de `$element` opnieuw in. Als er geen element is opgegeven, wordt het gehele formulier opnieuw ingesteld. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#reset-a-panel) om het voorbeeld te bekijken. |
| **importData** | `importData(any $payload)` | Hiermee importeert u gegevens in het formulier, waarbij bestaande formuliergegevens worden vervangen. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#pre-fill-the-field-with-a-value-when-the-form-loads) om het voorbeeld te bekijken. |
| **exportData** | `exportData()` | Retourneert de gegevens van het formulier. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) om het voorbeeld te bekijken. |
| **submitForm** | `submitForm(any $data [, boolean $validate_form = true, string $submit_as = 'multipart/form-data'])` | Triggert een verzonden formulier. De parameter `$data` geeft aan wat er moet worden verzonden en `$submit_as` definieert het inhoudstype (standaard ingesteld op &#39;multipart/form-data&#39;). De optionele `$validate_form` bepaalt of het formulier moet worden gevalideerd (standaard: true). Als de bewerking succesvol is, wordt `submitSuccess` geactiveerd; als de bewerking mislukt, wordt `submitError` geactiveerd. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#submit-altered-data-to-the-server) om het voorbeeld te bekijken. |
| **setFocus** | `setFocus(any $element [, FocusOption $focusOption])` | Hiermee wordt de focus ingesteld op de `$element` , die een deelvenster of veld kan zijn. Als geen element wordt verstrekt, wordt de nadruk geplaatst aan het gebied dat de regel teweegbracht. De optionele parameter `$focusOption` (van het type Enum `FocusOption` ) geeft aan of de focus op het &#39;nextItem&#39; of &#39;previousItem&#39; moet worden gericht ten opzichte van `$element` . Als een deelvenster is opgegeven, blijft de navigatie beperkt tot dat deelvenster. Bij een veld gebeurt de navigatie in het bovenliggende deelvenster. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#set-focus-on-the-specific-field) om het voorbeeld te bekijken. |
| **dispatchEvent** | `dispatchEvent(any $element, string $eventName [, any $payload])` | Verzendt een gebeurtenis van het type `$eventName` op het element dat door `$element` wordt gespecificeerd. Als er geen element is opgegeven, wordt de gebeurtenis verzonden op het formulier. De optionele `$payload` wordt beschikbaar gesteld voor expressies die de gebeurtenis afhandelen. | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#add-or-delete-repeatable-panel-using-the-dispatchevent-property) om het voorbeeld te bekijken. |
| **markFieldAsInvalid** | `markFieldAsInvalid(string $fieldIdentifier, string $validationMessage [, any $option = {useId: true}])` | Hiermee markeert u het veld dat door `$fieldIdentifier` wordt aangegeven als ongeldig en stelt u het validatiebericht in op `$validationMessage` . De optionele parameter `$option` geeft aan of `$fieldIdentifier` wordt geïnterpreteerd als `id` , `name` of `dataRef` . De standaardwaarde is `{useId: true}` en ondersteunde waarden zijn `{useId: true}` , `{useDataRef: true}` en `{useQualifiedName: true}` . | [ klik hier ](/help/forms/custom-function-core-components-use-cases.md#to-display-a-custom-message-at-the-field-level-and-marking-the-field-as-invalid) om het voorbeeld te bekijken. |

## Zie ook

{{see-also-rule-editor}}