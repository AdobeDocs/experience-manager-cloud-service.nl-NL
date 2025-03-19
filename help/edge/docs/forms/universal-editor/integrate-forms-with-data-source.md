---
title: Hoe te om het Model van de Gegevens van de Vorm (FDM) voor een vorm in Universele Redacteur te integreren?
description: Leer formulieren te maken op basis van een formuliergegevensmodel (FDM). Voorbeeldgegevens voor gegevensmodelobjecten in de FDM genereren en bewerken.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
hide: true
hidefromtoc: true
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: 381aad580762fe957e1dc1d5824e4d35098f1ca4
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 0%

---

# Formulieren integreren met formuliergegevensmodel in de universele editor

Door formulieren te integreren met een formuliergegevensmodel (FDM) in de Universal Editor kunt u verschillende bronnen van backendgegevens gebruiken om een formuliergegevensmodel (FDM) te maken. U kunt het formuliergegevensmodel (FDM) gebruiken als een schema in verschillende formulierworkflows. Vorm de gegevensbronnen en creeer een Model van de Gegevens van de Vorm (FDM) dat op de voorwerpen en de diensten van het gegevensmodel beschikbaar in gegevensbronnen wordt gebaseerd.

## Overwegingen

* De prefill-service voor formulieren in de Universal Editor wordt momenteel niet ondersteund.

## Vereisten

Voordat u het formulier configureert met het formuliergegevensmodel in de Universal Editor, moet u de volgende stappen uitvoeren:

* [ vorm Gegevens Source ](/help/forms/configure-data-sources.md): Opstelling de gegevensbron om uw vorm aan achterste gegevens te verbinden.
* [ creeer het Model van de Gegevens van de Vorm (FDM) ](/help/forms/create-form-data-models.md): Bouw een gegevensmodel gebruikend gegevensvoorwerpen en de diensten van de gevormde gegevensbron.
* [ vormt de ModelVoorwerpen en de Diensten van Gegevens ](/help/forms/work-with-form-data-model.md): Wijs de voorwerpen en de diensten van het gegevensmodel in kaart om vlotte gegevensstroom tussen de vorm en de gegevensbron te verzekeren.

## Forms maken met formuliergegevensmodel in Universal Editor

In de Universele Redacteur, kunt u tot stand brengen:
* [ op schema-Gebaseerde vorm ](#schema-based-form): Een op schema-Gebaseerde vorm gebruikt een gegevensbron die tijdens vormverwezenlijking in het **wordt gevormd Gegevens** lusje, dat automatisch gegevens bindt aan vormgebieden.
* [ niet op schema-Gebaseerde vorm ](#non-schema-based-form): Een niet op schema-Gebaseerde vorm vereist u om een gegevensbron manueel toe te voegen en elk gebied van de inhoudsboom te binden.

![ Types van Vorm in Universele Redacteur ](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

Deze methoden bieden u de flexibiliteit om gegevensmodellen te verbinden met formulieren die op uw behoeften zijn gebaseerd.

### Op schema gebaseerd formulier

Wanneer u een op een schema gebaseerd formulier maakt, wordt het automatisch geconfigureerd met een gegevensbron en worden de formuliervelden al gekoppeld aan de gegevens via gegevensbindingen. Voer de volgende stappen uit om een op een schema gebaseerd formulier te maken met de wizard Formulier maken:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.
2. Voer uw referenties in op de Experience Manager-aanmeldingspagina. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
3. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard wordt geopend. In het **Source** lusje, selecteer een malplaatje:

   ![ malplaatje van Edge Delivery Services ](/help/edge/assets/create-eds-forms.png)

   Wanneer u een op Edge Delivery Services gebaseerde sjabloon selecteert, wordt de knop **[!UICONTROL Create]** ingeschakeld. U kunt naar de tabbladen **[!UICONTROL Data Source]** of **[!UICONTROL Submission]** gaan om een gegevensbron te selecteren of een handeling te verzenden.

4. In het **lusje van Gegevens**, kunt u één van de volgende gegevensmodellen selecteren:

   * **Model van de Gegevens van de Vorm (FDM)**: Integreer de voorwerpen en de diensten van het gegevensmodel van gegevensbronnen in uw vorm. Kies FDM (Form Data Model) als in uw formulier gegevens uit meerdere bronnen moeten worden gelezen en geschreven.

   * **JSON Schema**: Integreer uw vorm met een achterste deelsysteem door een schema te associëren JSON dat de gegevensstructuur bepaalt. Hiermee kunt u dynamische inhoud toevoegen met behulp van de schema-elementen.

     Selecteer bijvoorbeeld het gemaakte formuliergegevensmodel met de naam Dierenformuliergegevensmodel.

     ![ Uitgezochte Model van de Gegevens van de Vorm ](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)


     Standaard worden alle velden van het bijbehorende JSON-schema of het formuliergegevensmodel (FDM) automatisch geselecteerd en geconverteerd naar de overeenkomstige formuliercomponenten, waardoor het ontwerpproces wordt vereenvoudigd. Met de wizard kunt u ook selectief kiezen welke velden u in het formulier wilt opnemen met selectievakjes.

5. Klik **[!UICONTROL Create]** en de **creeer 2} tovenaar van de Vorm {verschijnt.**
6. Specificeer de **Naam** en **Titel**.
7. Specificeer **GitHub URL**. Als uw GitHub-opslagplaats bijvoorbeeld de naam `edsforms` heeft, bevindt deze zich onder de account `wkndforms` , is de URL:
   `https://github.com/wkndforms/edsforms`
8. Klik op **[!UICONTROL Create]**.

   ![ creeer schema-gebaseerde vorm ](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

   Zodra u op **[!UICONTROL Create]** klikt, wordt het formulier in de Universal Editor geopend voor ontwerpen.

   ![ auteur de vorm ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

   Het formulier wordt gemaakt met behulp van de gegevenselementen van de bijbehorende gegevensbron, waarbij de formuliervelden vooraf ingestelde gegevensbinding hebben.

   ![ Automatische Gegevens die ](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png) binden

   U kunt nu toevoegen en [ vormen voorlegt actie ](/help/edge/docs/forms/universal-editor/submit-action.md) voor uw vorm.

### Niet-Schema-gebaseerd Vorm

Wanneer u een formulier maakt dat niet op een schema is gebaseerd, wordt er geen gegevensbron geconfigureerd. U kunt de formuliereigenschappen later bewerken om een gegevensbron toe te voegen en handmatig gegevensbindingen voor uw formuliervelden te configureren. Voer de volgende stappen uit om de formuliereigenschappen te bewerken en een gegevensbron toe te voegen:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.
1. Voer uw referenties in op de Experience Manager-aanmeldingspagina. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer het formulier waaraan u de gegevensbron wilt toevoegen en klik op **[!UICONTROL Properties]** .
   ![ Open vormeigenschappen ](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

   De formuliereigenschappen worden geopend.
1. Klik om het **Model van de Vorm** lusje, en van **Uitgezocht van** drop-down menu te openen. U kunt een van de volgende opties selecteren:

   * **Model van de Gegevens van de Vorm (FDM)**: Creeer de vorm gebruikend een model van vormgegevens.
   * **Verbinding**: Creeer de vorm gebruikend de gegevensbron van Adobe Marketo.
   * **Schema**: Creeer de vorm gebruikend een schema JSON dat aan AEM Forms wordt geupload.
   * **niets**: Creeer de vorm van kras zonder enig vormmodel te gebruiken.

     Selecteer bijvoorbeeld FDM (Form Data Model)

     ![ Uitgezochte het modellusje van het Vorm ](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

1. Selecteer het gemaakte formuliergegevensmodel (FDM) in de vervolgkeuzelijst. Selecteer bijvoorbeeld het gemaakte formuliergegevensmodel met de naam Dierenformuliergegevensmodel in de vervolgkeuzelijst.

   ![ Uitgezochte FDM ](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

   Als u het formuliergegevensmodel (FDM) selecteert, verschijnt er een waarschuwingsvenster. Klik **O.K.** om de dialoog te sluiten.

   ![ Tovenaar van het Model van de Vorm ](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

1. Klik op **[!UICONTROL Save & Close]**.
1. Open het formulier om het te bewerken. Het formulier wordt geopend in de Universal Editor voor ontwerpen.

   ![ niet op schema-Gebaseerde vorm creatie ](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

   De vormelementen huidig in het bijbehorende Model van de Gegevens van de Vorm (FDM) worden getoond in het **[!UICONTROL Datasource]** lusje van **[!UICONTROL Content Browser]** in het **Comité van Eigenschappen**.

   ![ Gegevens van de Vorm Source ](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

1. Selecteer de gegevenselementen op het tabblad **[!UICONTROL Datasource]** en klik op **[!UICONTROL Add]** .

   ![ voegt gegevenselementen ](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png) toe

   U kunt deze elementen ook slepen en neerzetten om het adaptieve formulier te maken. Wanneer u op **[!UICONTROL Add]** klikt, worden de geselecteerde elementen op het tabblad **[!UICONTROL Datasource]** aan het formulier toegevoegd en wordt een vinkje vóór de toegevoegde elementen weergegeven.

   ![ bouwt vorm ](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

   U moet gegevens manueel toevoegen die aan een vormelement binden door het in de **Bind eigenschappen van de Verwijzing** van het vormelement te specificeren.
Bijvoorbeeld, voeg een gegevensbindende verwijzing naar het **vakje van de Naam van het Huisdier** toe dat reeds in de vorm aanwezig is:

   ![ voeg manueel gegevens het dineren voor een vormgebied ](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png) toe

   U kunt nu toevoegen en [ vormen voorlegt actie ](/help/edge/docs/forms/universal-editor/submit-action.md) voor uw vorm.

## Zie ook

{{universal-editor-see-also}}
