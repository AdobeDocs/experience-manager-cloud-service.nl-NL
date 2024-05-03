---
title: Hoe kunnen wij variabelen aan AEM stappen van het Werkschema toevoegen?
description: Leer om een variabele tot stand te brengen, een waarde voor de variabele te plaatsen en het te gebruiken in [!DNL AEM Forms] Workflowstappen.
exl-id: d9139ea9-2f86-476c-8767-b36766790f2c
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '1916'
ht-degree: 0%

---

# Variabelen in Forms-centric AEM Workflows {#variables-in-aem-forms-workflows}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/variable-in-aem-workflows.html) |
| AEM as a Cloud Service | Dit artikel |

Een variabele in een workflowmodel is een manier om een waarde op te slaan op basis van het gegevenstype. U kunt de naam van de variabele in om het even welke werkschemastap gebruiken om de waarde terug te winnen die in de variabele wordt opgeslagen. U kunt veranderlijke namen ook gebruiken om uitdrukkingen te bepalen voor het nemen van verpletterende besluiten.

In AEM workflowmodellen kunt u:

* [Een variabele maken](variable-in-aem-workflows.md#create-a-variable) van een gegevenstype dat op het informatietype wordt gebaseerd dat u in het wilt opslaan.
* [Een waarde voor de variabele instellen](variable-in-aem-workflows.md#set-a-variable) met de workflowstap Variabele instellen.
* [De variabele gebruiken](variable-in-aem-workflows.md#use-a-variable) in totaal [!DNL AEM Forms] De stappen van het werkschema om de opgeslagen waarde en in OF Splitsen en gaan stappen terug om een verpletterende uitdrukking te bepalen.

De volgende video laat zien hoe u variabelen kunt maken, instellen en gebruiken in AEM workflowmodellen:

>[!VIDEO](assets/variables_introduction_1_1.mp4)

Variabelen zijn een uitbreiding van de bestaande [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface. U kunt [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) in ECMAScript gebruiken voor toegang tot metagegevens die zijn opgeslagen met variabelen.

## Een variabele maken {#create-a-variable}

U maakt variabelen aan de hand van de sectie Variabelen die beschikbaar is in de assistent van het workflowmodel. AEM workflowvariabelen ondersteunen de volgende gegevenstypen:

* **Primitieve gegevenstypen**: Long, Double, Boolean, Date en String
* **Complexe gegevenstypen**: [Document](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aemfd/docmanager/Document.html), [XML](https://docs.oracle.com/javase/8/docs/api/org/w3c/dom/Document.html), [JSON](https://static.javadoc.io/com.google.code.gson/gson/2.3/com/google/gson/JsonObject.html)en Formuliergegevensmodel.

>[!NOTE]
>
>Workflows ondersteunen alleen de ISO8601-indeling voor variabelen van het type Date.

Gebruik het gegevenstype ArrayList om variabele verzamelingen te maken. U kunt een variabele ArrayList maken voor alle primitieve en complexe gegevenstypen. Maak bijvoorbeeld een variabele ArrayList en selecteer String als subtype om meerdere tekenreekswaarden op te slaan met de variabele.

Een variabele maken:

1. Navigeer in een AEM naar Gereedschappen ![Hammerpictogram](assets/hammer-icon.svg) > Workflow > Modellen.
1. Selecteren **[!UICONTROL Create]** en geeft u de titel en een optionele naam voor het workflowmodel op. Selecteer het model en selecteer **[!UICONTROL Edit]**.
1. Selecteer het pictogram Variabelen dat beschikbaar is in de assistent van het workflowmodel en selecteer **[!UICONTROL Add Variable]**.

   ![Variabele toevoegen](assets/variables_add_variable_new.png)

1. Geef in het dialoogvenster Variabele toevoegen de naam op en selecteer het type variabele.
1. Selecteer het gegevenstype in het menu **[!UICONTROL Type]** vervolgkeuzelijst en geef de volgende waarden op:

   * Primitieve gegevenstype - Geef een optionele standaardwaarde voor de variabele op.
   * JSON of XML - Geef een optioneel JSON- of XML-schemapad op. Het systeem valideert het schemapad terwijl het in kaart brengen van en het opslaan van eigenschappen beschikbaar in dit schema aan een andere variabele.
   * Formuliergegevensmodel (FDM) - Geef een formuliergegevensmodelpad op.
   * ArrayList - Geef een subtype op voor de verzameling.

1. Geef een optionele beschrijving voor de variabele op en selecteer ![done_icon](assets/Smock_Checkmark_18_N.svg) om de wijzigingen op te slaan De variabele wordt weergegeven in de lijst die beschikbaar is in het linkerdeelvenster.

Houd rekening met de volgende werkwijzen wanneer u variabelen maakt:

* Maak zoveel variabelen als een workflow nodig heeft. Om databasemiddelen te besparen, moet u echter het minimale aantal vereiste variabelen gebruiken en moet u variabelen waar mogelijk opnieuw gebruiken.
* Variabelen zijn hoofdlettergevoelig. Zorg ervoor dat u in uw werkstroom naar variabelen verwijst met hetzelfde hoofdlettergebruik.
* Gebruik geen speciale tekens in de naam van een variabele

## Een variabele instellen {#set-a-variable}

Met de stap Variabele instellen kunt u de waarde van een variabele instellen en de volgorde definiëren waarin de waarden worden ingesteld. De variabele wordt ingesteld in de volgorde waarin de variabele-toewijzingen worden vermeld in de stap met de variabele-set.

Wijzigingen in waarden van variabelen zijn alleen van invloed op de instantie van het proces waarin de wijziging plaatsvindt. Wanneer bijvoorbeeld een werkstroom wordt gestart en variabele gegevens worden gewijzigd, hebben de wijzigingen alleen invloed op dat exemplaar van de werkstroom. De wijzigingen zijn niet van invloed op andere versies van de workflow die eerder zijn gestart of later zijn gestart.

Afhankelijk van het gegevenstype van de variabele kunt u de volgende opties gebruiken om de waarde van een variabele in te stellen:

* **Letterlijk:** Gebruik deze optie als u precies weet welke waarde u moet opgeven. U kunt de optie ook gebruiken om een JSON op te geven in de vorm van een tekenreeks.

* **Uitdrukking:** Gebruik de optie wanneer de te gebruiken waarde wordt berekend op basis van een expressie. De expressie wordt gemaakt in de beschikbare expressie-editor.

* **JSON-puntnotatie:** Gebruik de optie om een waarde van een JSON of FDM typevariabele terug te winnen.
* **XPATH:** Gebruik de optie om een waarde van een variabele van het type van XML terug te winnen.

* **Ten opzichte van lading:** Gebruik de optie wanneer de waarde die u wilt opslaan in een variabele, beschikbaar is op een pad dat relatief is ten opzichte van de laadbewerking.

* **Absoluut pad:** Gebruik de optie wanneer de waarde die u wilt opslaan in de variabele beschikbaar is in een absoluut pad.

U kunt ook specifieke elementen van een variabele van het type JSON of XML bijwerken met JSON-puntnotatie of XPATH-notatie.

### Toewijzing tussen variabelen toevoegen {#add-mapping-between-variables}

Toewijzing tussen variabelen toevoegen:

1. Selecteer op de pagina voor workflowbewerking het pictogram Stappen dat beschikbaar is in de assistent van het workflowmodel.
1. Sleep de **[!UICONTROL Set Variable]** stap naar de werkstroomeditor, selecteer de stap en selecteer ![configure_icon](assets/Smock_Wrench_18_N.svg) (Configureren).
1. Selecteer in het dialoogvenster Variabele instellen de optie **[!UICONTROL Mapping]** > **[!UICONTROL Add Mapping]**.
1. In de **Kaartvariabele** selecteert u de variabele die u wilt opslaan, selecteert u de toewijzingsmodus en geeft u een waarde op die u in de variabele wilt opslaan. De toewijzingsmodi variëren op basis van het type variabele.
1. Wijs meer variabelen toe om een betekenisvolle expressie te maken. Selecteren ![done_icon](assets/Smock_Checkmark_18_N.svg) om de wijzigingen op te slaan

### Voorbeeld 1: Vraag een XML-variabele naar een waarde voor een tekenreeksvariabele {#example-query-an-xml-variable-to-set-value-for-a-string-variable}

Selecteer een variabele van het type van XML om een dossier van XML op te slaan. Vraag de variabele van XML om de waarde voor een koordvariabele voor het bezit te plaatsen beschikbaar in het dossier van XML. Gebruiken **XPATH opgeven voor de XML-variabele** veld om de eigenschap te definiëren die in de tekenreeksvariabele moet worden opgeslagen.

Selecteer in dit voorbeeld een **formatiegegevens** XML-variabele om de **cc-app.xml** bestand. Vraag de **formatiegegevens** variabele die de waarde voor de **e-mailadres** tekenreeksvariabele die de waarde voor de **emailAddress** eigenschap beschikbaar in de **cc-app.xml** bestand.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/set_variable_example1.mp4 "Waarde van een variabele instellen")

### Voorbeeld 2: een expressie gebruiken om waarde op te slaan op basis van andere variabelen {#example2}

Gebruik een expressie om de som van de variabelen te berekenen en sla het resultaat op in een variabele.

In dit voorbeeld gebruikt u de expressie-editor om een expressie te definiëren die de som van **assetkosten** en **saldi** variabelen en sla het resultaat op in **totalvalue** variabele.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_expression.mp4)

## Expressieeditor gebruiken {#use-expression-editor}

U gebruikt ook expressies om de waarde van een variabele in de runtime te berekenen. Variabelen bieden een expressie-editor om expressies te definiëren.

Met de expressie-editor kunt u:

* Stel de waarde van variabelen in met behulp van andere workflowvariabelen, getallen of wiskundige expressies.
* Werkstroomvariabelen, tekenreeksen, getallen of expressies gebruiken in een wiskundige expressie
* Voeg voorwaarden toe om waarden van variabelen in te stellen.
* Operatoren toevoegen tussen voorwaarden.

![Expressieeditor](assets/variables_expression_editor_new.png)

Het is gebaseerd op de Adaptive Forms-regeleditor met de volgende wijzigingen. Regeleditor in variabelen:

* Biedt geen ondersteuning voor functies.
* Biedt geen interface voor het weergeven van een overzicht van regels
* Heeft geen code-editor.
* Hiermee wordt het in- en uitschakelen van de waarde van een object niet ondersteund.
* Hiermee wordt eigenschap instellen van een object niet ondersteund.
* Biedt geen ondersteuning voor het oproepen van een webservice.

Zie voor meer informatie [Adaptieve Forms-regeleditor](rule-editor.md).

## Een variabele gebruiken {#use-a-variable}

U kunt variabelen gebruiken om input en output terug te winnen of het resultaat van een stap te bewaren. De werkstroomeditor bevat twee typen workflowstappen:

* Workflowstappen met ondersteuning voor variabelen
* Workflowstappen zonder ondersteuning voor variabelen

### Workflowstappen met ondersteuning voor variabelen {#workflow-steps-with-support-for-variables}

De stap Ga naar OF Splitsen en alle [!DNL AEM Forms] Workflowstappen ondersteunen variabelen.

#### OF stap Splitsen {#or-split-step}

Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor OF de Gesplitste stap, zie [OF stap Splitsen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem#or-split).

In dit voorbeeld, alvorens de verpletterende uitdrukking te bepalen, gebruik [voorbeeld 2](variable-in-aem-workflows.md#example2) om de waarde voor de **totalvalue** variabele. Tak 1 is actief als de waarde van **totalvalue** variabele is groter dan 50000. Op dezelfde manier kunt u een regel bepalen om Tak 2 actief te maken als de waarde van **totalvalue** variabele is minder dan 50000.

>[!VIDEO](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/using/variables_orsplit_example.mp4)

Op dezelfde manier selecteer een externe manuscriptweg of specificeer het manuscript ECMA voor het verpletteren van uitdrukkingen om de actieve tak te evalueren. Selecteren **[!UICONTROL Rename Branch]** een alternatieve naam voor de vertakking opgeven.

<!-- For more examples, see [Create a workflow model](aem-forms-workflow.md#create-a-workflow-model). -->

#### Ga naar stap {#go-to-step}

De **Ga naar stap** laat u de volgende stap in het uit te voeren werkschemamodel specificeren, afhankelijk van het resultaat van een verpletterende uitdrukking.

Gelijkaardig aan OF de Gesplitste stap, kunt u het verpletteren van uitdrukking voor stap bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

U kunt variabelen gebruiken om de verpletterende uitdrukking te bepalen gebruikend de uitdrukkingsredacteur. Voor meer informatie bij het gebruiken van het verpletteren van uitdrukkingen voor de stap Ga, zie [Ga naar stap](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem#goto-step).

![Ga naar regel](assets/variables_goto_rule1_new.png)

In dit voorbeeld wordt in de stap Ga naar de toepassing Creditcard controleren opgegeven als de volgende stap als de waarde voor de **genomen maatregelen** variable is gelijk aan **Meer informatie nodig**.

Voor meer voorbeelden bij het gebruiken van regeldefinitie in de stap Ga naar, zie [Een lus For simuleren](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem#simulateforloop).

#### Forms-centric workflowstappen {#forms-workflow-centric-workflow-steps}

Alles [!DNL AEM Forms] Workflowstappen ondersteunen variabelen. Zie voor meer informatie [Forms-centric workflow op OSGi](aem-forms-workflow-step-reference.md).

### Workflowstappen zonder ondersteuning voor variabelen {#workflow-steps-without-support-for-variables}

U kunt [MetaDataMap](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface voor toegang tot variabelen in workflowstappen die geen variabelen ondersteunen.

#### De waarde van de variabele ophalen {#retrieve-the-variable-value}

Gebruik de volgende API&#39;s in het ECMA-script om waarden voor bestaande variabelen op te halen op basis van het gegevenstype:

| Gegevenstype variabele | API |
|---|---|
| Primitief (lang, dubbel, Boolean, datum en tekenreeks) | workItem.getWorkflowData().getMetaDataMap().get(variableName, type) |
| Document | Packages.com.adobe.aemfd.docmanager.Document = workItem.getWorkflowData().getMetaDataMap().get(&quot;docVar&quot;, Packages.com.adobe.aemfd.docmanager.Document.class); |
| XML | Packages.org.w3c.dom.Document xmlObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.org.w3c.dom.Document.class); |
| Formuliergegevensmodel (FDM) | Packages.com.adobe.name.dermis.api.FormDataModelInstance fdmObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.adobe.aem.dermis.api.FormDataModelInstance.class); |
| JSON | Packages.com.google.get.JsonObject jsonObject = workItem.getWorkflowData().getMetaDataMap().get(variableName, Packages.com.google.gson.JsonObject.class); |


**Voorbeeld**

Hiermee wordt de waarde van het gegevenstype String opgehaald met de volgende API:

```javascript
workItem.getWorkflowData().getMetaDataMap().get(accname, Packages.java.lang.String)
```

#### De waarde van de variabele bijwerken {#update-the-variable-value}

Gebruik de volgende API in het ECMA-script om de waarde van een variabele bij te werken:

```javascript
workItem.getWorkflowData().getMetaDataMap().put(variableName, value)
```

**Voorbeeld**

```javascript
workItem.getWorkflowData().getMetaDataMap().put(salary, 50000)
```

Hiermee werkt u de waarde voor de **salaris** variabel tot 50000.

### Variabelen instellen om workflows aan te roepen {#apiinvokeworkflow}

U kunt een API gebruiken om variabelen in te stellen en deze door te geven om workflowinstanties aan te roepen.

[workflowSession.startWorkflow](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/workflow/WorkflowSession.html#startWorkflow-com.adobe.granite.workflow.model.WorkflowModel-com.adobe.granite.workflow.exec.WorkflowData-java.util.Map-) gebruikt model, wfData, en metaData als argumenten. Gebruik MetaDataMap om de waarde voor de variabele in te stellen.

In deze API **variableName** variable is ingesteld op **value** met metaData.put(variableName, value);

```javascript
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*Assume that you already have a workflowSession and modelId along with the payloadType and payload*/
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
metaData.put(variableName, value); //Create a variable "variableName" in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

**Voorbeeld**

Initialiseer de **doc** documentobject naar een pad (&quot;a/b/c&quot;) en stel de waarde van de **docVar** variabele naar het pad dat is opgeslagen in het documentobject.

```javascript
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.WorkflowData;
import com.adobe.granite.workflow.model.WorkflowModel;
import com.adobe.granite.workflow.metadata.MetaDataMap;
import com.adobe.aemfd.docmanager.Document;

/*This example assumes that you already have a workflowSession and modelId along with the payloadType and payload */
WorkflowData wfData = workflowSession.newWorkflowData(payloadType, payload);
MetaDataMap metaData = wfData.getMetaDataMap();
Document doc = new Document("/a/b/c");// initialize a document object
metaData.put("docVar",doc); //Assuming that you have created a variable "docVar" of type Document in your workflow model
WorkflowModel model = workflowSession.getModel(modelId);
workflowSession.startWorkflow(model, wfData, metaData);
```

## Een variabele bewerken {#edit-a-variable}

1. Selecteer op de pagina voor de bewerkingsworkflow het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Selecteer de ![bewerken](assets/edit.svg) (Bewerken) naast de naam van de variabele die u wilt bewerken.
1. Bewerk de variabelegegevens en selecteer ![done_icon](assets/Smock_Checkmark_18_N.svg) om de wijzigingen op te slaan U kunt de **[!UICONTROL Name]** en **[!UICONTROL Type]** velden voor een variabele.

## Een variabele verwijderen {#delete-a-variable}

Voordat u de variabele verwijdert, verwijdert u alle referenties van de variabele uit de workflow. Zorg ervoor dat de variabele niet in de workflow wordt gebruikt.

Een variabele verwijderen:

1. Selecteer op de pagina voor de bewerkingsworkflow het pictogram Variabelen in de assistent van het workflowmodel. In het gedeelte Variabelen in het linkerdeelvenster worden alle bestaande variabelen weergegeven.
1. Selecteer het pictogram Verwijderen naast de naam van de variabele die u wilt verwijderen.
1. Selecteren ![done_icon](assets/Smock_Checkmark_18_N.svg) om de variabele te bevestigen en te schrappen.

## Verwijzingen {#references}

Meer voorbeelden over het gebruik van variabelen in [!DNL AEM Forms] Workflowstappen, zie [Variabelen in AEM werkstromen](https://helpx.adobe.com/experience-manager/kt/forms/using/authoring_variables_in_aem_forms-workflow1.html).
