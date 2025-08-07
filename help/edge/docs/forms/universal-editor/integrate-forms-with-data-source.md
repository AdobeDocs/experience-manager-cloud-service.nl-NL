---
title: Hoe te om het Model van de Gegevens van de Vorm (FDM) voor een vorm in Universele Redacteur te integreren?
description: Leer formulieren te maken op basis van een formuliergegevensmodel (FDM). Voorbeeldgegevens voor gegevensmodelobjecten in de FDM genereren en bewerken.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---


# Forms integreren met FDM (Form Data Model)

Sluit uw formulieren met FDM aan op back-endgegevensbronnen om werkstromen voor gegevensbinding, -validatie en -verzending in te schakelen.

## Vereisten

Voer de volgende stappen uit voordat u FDM integreert met uw formulieren:

1. **[vorm Gegevens Source](/help/forms/configure-data-sources.md)**: Opstelling achterste verbindingen
2. **[creeer het Model van de Gegevens van de Vorm](/help/forms/create-form-data-models.md)**: Bepaal gegevensstructuur en de diensten
3. **[vorm de Modelvoorwerpen van Gegevens](/help/forms/work-with-form-data-model.md)**: De gegevensverhoudingen van de kaart

## Overwegingen

Als u niet het **pictogram van Gegevensbronnen** in uw Universele interface van de Redacteur ziet of **Bind het bezit van de Verwijzing** in het juiste bezitspaneel, laat de **bron** uitbreiding van de Gegevensbron in **Extension Manager** toe.

![ Schermafbeelding van de Universele interface die van de Redacteur Extension Manager beschikbare uitbreidingen met inbegrip van de uitbreiding van Gegevensbronnen toont die voor vormintegratie ](/help/edge/docs/forms/universal-editor/assets/extension-manager.png) kan worden toegelaten

Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren om uitbreidingen in de Universele Redacteur toe te laten en onbruikbaar te maken.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Uw formuliertype kiezen

De Universal Editor ondersteunt twee methoden voor het maken van formulieren:

| Verhouding | Op schema gebaseerd formulier | Niet-Schema-gebaseerd Vorm |
|--------|-------------------|----------------------|
| **Complexiteit van de Opstelling** | Eenvoudig (automatische binding) | Handmatig (veld-voor-veld binding) |
| **Geval van het Gebruik** | Nieuwe formulieren met gedefinieerde gegevensstructuur | Bestaande formulieren of flexibele vereisten |
| **Gegevens Source** | Vereist tijdens maken | Kan later worden toegevoegd |
| **Binding** | Automatische veldbinding | Handmatige binding per veld |

![ Types van Vorm in Universele Redacteur ](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## Op schema gebaseerd formulier

Op schema gebaseerde formulieren configureren automatisch gegevensbronnen en binden formuliervelden aan gegevens. Deze aanpak is ideaal voor nieuwe formulieren met duidelijk gedefinieerde gegevensstructuren.

### Schema-gebaseerd formulier maken

1. **Toegang Forms Console**
   - Meld u aan bij uw [!DNL Experience Manager Forms] Author-instantie
   - Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**

2. **Van het Begin Vorm**
   - Selecteren **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]**
   - Een Edge Delivery Services-sjabloon kiezen
   - Klik **[!UICONTROL Create]** indien ingeschakeld

   ![ malplaatje van Edge Delivery Services ](/help/edge/assets/create-eds-forms.png)

3. **vorm het Model van Gegevens**
   - Ga naar het **lusje van Gegevens**
   - Selecteer **Model van de Gegevens van de Vorm (FDM)** voor veelvoudige gegevensbronnen of **JSON Schema** voor enig achterste systeem
   - Kies de door u gemaakte FDM (bijvoorbeeld Dierenformuliergegevensmodel)

   ![ Uitgezochte Model van de Gegevens van de Vorm ](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **Volledige Opstelling van de Vorm**
   - Ga **Naam** en **Titel** in
   - Specificeer **GitHub URL** (bijvoorbeeld, `https://github.com/wkndforms/edsforms`)
   - Klikken **[!UICONTROL Create]**

   ![ creeer schema-gebaseerde vorm ](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### Op schema gebaseerd formulier verifiëren

Het formulier wordt geopend in de Universal Editor met vooraf geconfigureerde gegevensbinding:

![ Schermafbeelding van de Universele Redacteur die een op schema-gebaseerde vorm met pre-bevolkte vormgebieden en Browser van de Inhoud toont beschikbare gegevensbronelementen ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![ Automatische Gegevens die ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png) binden

## Niet-Schema-gebaseerd Vorm

Niet-schemaformulieren vereisen handmatige configuratie van de gegevensbron en veldbinding. Deze aanpak biedt flexibiliteit voor bestaande formulieren of complexe vereisten.

### Niet-Schema-gebaseerd formulier maken

1. **de Eigenschappen van de Vorm van de Toegang**
   - Meld u aan bij uw [!DNL Experience Manager Forms] Author-instantie
   - Ga naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**
   - Selecteer het formulier en klik op **[!UICONTROL Properties]**

   ![ Open vormeigenschappen ](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **vorm Model**
   - Open het **Model van de Vorm** lusje
   - Selecteer **Model van de Gegevens van de Vorm (FDM)** van **Uitgezocht van** dropdown
   - Kies uw FDM in de lijst

   ![ Uitgezochte het modellusje van het Vorm ](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![ Uitgezochte FDM ](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **bevestigt Configuratie**
   - Klik **O.K.** in de waarschuwingsdialoog
   - Klikken **[!UICONTROL Save & Close]**

   ![ Tovenaar van het Model van de Vorm ](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### Gegevenselementen toevoegen

1. **Open Vorm voor het Uitgeven**
   - Het formulier wordt geopend in de Universal Editor

   ![ niet op schema-Gebaseerde vorm creatie ](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **Gegevens van de Toegang Source Elements**
   - Ga naar de tab **[!UICONTROL Datasource]** in het dialoogvenster **[!UICONTROL Content Browser]**
   - Beschikbare gegevenselementen van uw FDM weergeven

   ![ Gegevens van de Vorm Source ](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **voegt Elementen aan Vorm** toe
   - Selecteer gegevenselementen en klik op **[!UICONTROL Add]**
   - Of sleep elementen om uw formulier samen te stellen

   ![ voegt gegevenselementen ](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png) toe

   ![ Schermafbeelding die de Universele Redacteur met een niet-schemavorm toont die door gegevenselementen van het lusje van Source van Gegevens te slepen en te laten vallen in de vormstructuur ](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png) wordt gebouwd

### Handmatige gegevensbinding toevoegen

Voor bestaande vormgebieden, voeg gegevens toe die door het **binden bezit van de Verwijzing** binden:

1. **Open Eigenschappen van het Gebied**
   - Selecteer het formulierveld voor binding
   - Het deelvenster Eigenschappen openen

2. **vorm Bindverwijzing**
   - Ga naar het **Bind bezit van de Verwijzing**
   - Klik **doorbladeren** pictogram

   ![ voeg manueel gegevens het dineren voor een vormgebied ](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png) toe

3. **Uitgezochte het Element van Gegevens**
   - Kies van de gegevensbronboom in **Uitgezocht een Bind tovenaar van de Verwijzing**
   - Selecteer het gewenste gegevenselement en klik **Uitgezocht**

   ![ uitgezochte gegevens binden verwijzing ](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![ uitgezocht gegevenselement ](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **verifieer het Binden**
   - Het formulierveld is nu gekoppeld aan het gegevenselement
   - De band verschijnt in het **Bind bezit van de Verwijzing**

   ![ Automatische Gegevens die ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png) binden

## Integratie verifiëren

Na voltooiing van de integratie:

1. **de gegevensband van de Test**: Verifieer de vertoningscorrecte gegevens van vormgebieden
2. **bevestigt indieningen**: Zorg gegevensopslag aan gevormde bronnen
3. **de fout behandeling van de Controle**: Test met ongeldige gegevensscenario&#39;s

## Volgende stappen

Vorm [ voorlegt acties ](/help/edge/docs/forms/universal-editor/submit-action.md) om uw vormwerkschema te voltooien.
