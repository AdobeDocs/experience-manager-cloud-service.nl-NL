---
title: Voeg aangepaste fouthandlers toe in Adaptive Forms for AEM Adaptive Forms
description: AEM Forms verstrekt out-of-the-box succes en foutenmanagers voor een vorm gebruikend het REST eindpunt dat wordt gevormd om de externe dienst aan te halen. U kunt een standaardfouthandler en een aangepaste fouthandler toevoegen aan een AEM adaptief formulier.
keywords: Voeg een manager van de douanefout toe, voeg een standaardfoutenmanager toe, voeg een foutenmanager in vorm toe, gebruik de toepassing roept dienst van de redacteur om een douanefoutenmanager toe te voegen, regel redacteur te vormen om een manager van de douanefout toe te voegen, douanefoutafhandeling toe gebruikend regelredacteur
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Foundation Components
exl-id: 198a26a9-d6bb-457d-aab8-0a5d15177c48
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '2347'
ht-degree: 0%

---

# Aangepaste fouthandlers toevoegen in AEM adaptieve Forms {#error-handlers-in-adaptive-form}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Het biedt ook functie om functies van fouthandlers aan te passen. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een externe dienst gebruikend APIs wordt aangehaald, worden de gegevens overgebracht naar de server voor bevestiging, die een antwoord op de cliënt met informatie over het succes of de foutengebeurtenis voor de voorlegging terugkeert. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren. Met een fouthandler kunt u fouten of validatieproblemen die zijn opgetreden, beheren en weergeven.

![fout handler-workflow voor meer informatie over het toevoegen van een aangepaste fouthandler in formulieren](/help/forms/assets/error-handler-workflow.png)

De adaptieve Vorm bevestigt de input die u op gebieden verstrekt die op vooraf ingestelde bevestigingscriteria en controles op diverse fouten wordt gebaseerd door het REST eindpunt wordt gevormd om de externe dienst aan te halen. U kunt de validatiecriteria instellen op basis van de gegevensbron die u gebruikt met het adaptieve formulier. Als u bijvoorbeeld RESTful-webservices gebruikt als gegevensbron, kunt u de validatiecriteria definiëren in een Swagger-definitiebestand.

Als de invoerwaarden aan de validatiecriteria voldoen, worden de waarden naar de andere gegevensbron verzonden, geeft het adaptieve formulier een foutbericht weer met behulp van een fouthandler. Net als bij deze aanpak worden adaptieve Forms geïntegreerd met aangepaste fouthandlers voor het uitvoeren van gegevensvalidaties. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten weergegeven op veldniveau in het adaptieve formulier. Dit gebeurt wanneer het foutbericht van de validatie dat door de server wordt geretourneerd, de standaardberichtindeling heeft.


## Gebruikt fouthandlers {#uses-of-error-handler}

Fouthandlers worden voor verschillende doeleinden gebruikt. Enkele toepassingen van de functies van de foutenmanager zijn hieronder vermeld:
* **Validatie uitvoeren**: De foutafhandeling begint met het valideren van gebruikersinvoer op basis van vooraf gedefinieerde regels of criteria. Wanneer gebruikers een adaptief formulier invullen, valideert de fouthandler de invoer om ervoor te zorgen dat deze voldoet aan de vereiste indeling, lengte of andere beperkingen.

* **Feedback in real time geven**: Wanneer een fout wordt gedetecteerd, geeft de fouthandler direct feedback aan de gebruiker, zoals inline foutberichten onder de bijbehorende formuliervelden. Met deze feedback kunnen gebruikers fouten opsporen en corrigeren zonder het formulier te hoeven verzenden en op een reactie te moeten wachten.


* **Foutberichten weergeven**: Wanneer bij het verzenden van een adaptief formulier een validatiefout optreedt, geeft de fouthandler een geschikt foutbericht weer. De foutberichten moeten duidelijk, beknopt en nauwkeurig zijn en de specifieke velden moeten benadrukken die aandacht behoeven.

* **Hiermee wordt het onjuiste veld gemarkeerd**: Om de aandacht van de gebruiker op de specifieke onjuiste gebieden te trekken, benadrukt de foutenmanager of onderscheidt visueel de overeenkomstige gebieden. Dit wordt uitgevoerd door de achtergrondkleur te wijzigen, een pictogram of rand toe te voegen of door andere visuele aanwijzingen die gebruikers helpen de fouten snel te vinden en aan te pakken.


## Opmaak van reactie fout/fout {#failure-response-format}

In een adaptief formulier worden de fouten in een veld weergegeven als de foutberichten voor servervalidatie de volgende standaardindeling hebben.
De onderstaande code illustreert de bestaande structuur van de mislukkingsreactie:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


Waarbij:

* `errorCausedBy` beschrijft de reden voor mislukking.
* `errors` vermeld de SOM-expressie van de velden waarvoor de validatiecriteria niet zijn nageleefd, samen met het foutbericht voor de validatie.
* `originCode` veld toegevoegd door AEM en bevat de http-statuscode geretourneerd door de externe service.
* `originMessage` veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

Met de verbeteringen in eigenschappen en verdere updates in de versies van AEM Forms, veranderde de bestaande structuur van de mislukkingsreactie in nieuw formaat dat op RFC7807 wordt gebaseerd, die achterwaarts compatibel met de bestaande structuur van de mislukkingsreactie is:

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<SOM expression of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code>, (optional - in case of SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - in case of SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * Zorg ervoor dat de structuur van de foutreactie het volgende bevat: **fieldName** of **dataRef**.
> * Zorg ervoor dat de **ContentType** header is **application/problem+json**.

Waarbij:
* `type (required)` geeft het type fout aan. Dit kan een van de volgende waarden zijn:
   * `SERVER_SIDE_VALIDATION` Hiermee wordt een fout aangegeven als gevolg van validatie aan de serverzijde.
   * `FORM_SUBMISSION` Hiermee wordt een fout aangegeven tijdens het verzenden van het formulier
   * `SERVICE_INVOCATION` Hiermee wordt een fout aangegeven tijdens een aanroep van een externe service.
   * `FAILURE` geeft een algemene fout aan.
   * `VALIDATION_ERROR` Hiermee wordt een fout aangegeven als gevolg van een validatiefout.

* `title (optional)` bevat een titel of korte beschrijving van de fout.
* `detail (optional)` indien nodig aanvullende details over de fout geven.
* `instance (optional)` vertegenwoordigt een instantie of een herkenningsteken verbonden aan de mislukking en helpt in het volgen van of het identificeren van het specifieke voorkomen van de mislukking.
* `validationErrors (required)` bevat informatie over validatiefouten. Het bevat de volgende velden:
   * `fieldname` Hiermee wordt de SOM-expressie vermeld van de velden waarvoor de validatiecriteria zijn mislukt.
   * `dataRef` vertegenwoordigt het JSON-pad of XPath van de velden waarvoor de validatie is mislukt.
   * `details` bevat het foutbericht met het onjuiste veld.
* `originCode (optional)` veld toegevoegd door AEM en bevat de http-statuscode geretourneerd door de externe service
* `originMessage (optional)` veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

### Sample-indeling voor foutreactie {#sample-error-response-format}

Enkele opties om de foutreacties weer te geven zijn:

+++  Gebaseerd op de eigenschap Adaptive Form fieldName


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "guide[0].guide1[0].guideRootPanel[0].textbox1686647736683[0]",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```

  U kunt de SOM-expressie van elk veld in een adaptief formulier weergeven door op het veld te tikken en de **[!UICONTROL View SOM Expression]**.

  ![Som-expressie van een adaptief formulierveld voor weergave van foutreacties in aangepaste fouthandler](/help/forms/assets/custom-error-handler-somexpression.png)

+++


+++ Gebaseerd op de eigenschap Adaptive Form dataRef

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "/Pet/id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

  ![Gegevensverwijzing van een adaptief formulierveld voor weergave van foutreacties in aangepaste fouthandler](/help/forms/assets/custom-errorhandler-dataref.png)

U kunt de waarde van dataRef bekijken in **[!UICONTROL Properties]** venster van een formuliercomponent.

+++


## Fouthandler toevoegen met gebruik van de Regel-editor {#add-error-handler-using-rule-editor}

Met de [Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) , definieert u de validatiecriteria op basis van de gegevensbron die u gebruikt met het adaptieve formulier. Als u RESTful-webservices als gegevensbron gebruikt, kunt u de validatiecriteria definiëren in een bestand met definities van de Swagger. Door de functies van de foutenmanager en de Redacteur van de Regel in Aangepast Forms te gebruiken, kunt u fout behandeling effectief beheren en aanpassen. U bepaalt de voorwaarden gebruikend de Redacteur van de Regel en vormt de gewenste acties die moeten worden uitgevoerd wanneer de regel wordt teweeggebracht. Met Aangepast formulier worden de invoer die u invoert in velden gevalideerd op basis van vooraf ingestelde validatiecriteria. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten in een adaptief formulier weergegeven op veldniveau.

>[!NOTE]
>
> * Om foutenmanagers met de Invoke van de Redacteur van de Regel de dienstactie te gebruiken, vorm Aangepast Forms met een model van vormgegevens (FDM).
> * Er wordt een standaardfouthandler geboden voor het weergeven van foutberichten op velden als de foutreactie in het standaardschema staat. U kunt de standaardfoutenmanager van de functie van de douaneformmanager ook roepen.

Gebruikend de Redacteur van de Regel, kunt u:
* [Standaardfouthandlerfunctie toevoegen](#add-default-errror-handler)
* [Aangepaste fouthandlerfunctie toevoegen](#add-custom-errror-handler)


### Standaardfouthandlerfunctie toevoegen {#add-default-errror-handler}

Een standaardfouthandler wordt ondersteund voor het weergeven van foutberichten in velden als de foutreactie in het standaardschema of bij een validatiefout op de server staat.
Als u wilt weten hoe u een standaardfouthandler gebruikt met de functie [Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) handeling, neem een voorbeeld van een eenvoudig adaptief formulier met twee velden. **Huisdier-id** en **Naam huisdier** en gebruik een standaardfouthandler bij de **Huisdier-id** gebied om diverse fouten te controleren die door het REST eindpunt zijn teruggekeerd dat wordt gevormd om een externe dienst, bijvoorbeeld aan te halen, `200 - OK`,`404 - Not Found`, `400 - Bad Request`. Om een standaardfoutenmanager toe te voegen gebruikend de Actie van de Dienst van de Redacteur van de Regel Invoke, voer de volgende stappen uit:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formulieronderdeel en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteren **[!UICONTROL Create]**.
1. Een voorwaarde maken in het dialoogvenster **Wanneer** van de regel. Bijvoorbeeld: **Wanneer[Naam van veld Dierenid]** is gewijzigd. Selecteren wordt gewijzigd in het menu **Frame selecteren** vervolgkeuzelijst.
1. In de **Vervolgens** sectie, selecteert u **[!UICONTROL Invoke Service]** van de **Handeling selecteren** vervolgkeuzelijst.
1. Selecteer een **Post-service** en de overeenkomstige gegevensbindingen van de **Invoer** sectie. Bijvoorbeeld om te bevestigen **Huisdier-id** selecteert u een **Post-service** als **GET /pet/{petId}** en selecteert u **Huisdier-id** in de **Invoer** sectie.
1. Selecteer de gegevensbindingen in het menu **Uitvoer** sectie. Selecteren **Naam huisdier** in de **Uitvoer** sectie.
1. Selecteren **[!UICONTROL Default Error Handler]** van de **Fouthandler** sectie.
1. Klik op **[!UICONTROL Done]**.

![een standaardfouthandler toevoegen voor veldvalidatiecontroles in een formulier](/help/forms/assets/default-error-handler.png)

Als resultaat van deze regel worden de waarden waarvoor u invoert **Huisdier-id** controleert validatie voor **Naam huisdier** het gebruiken van externe dienst die door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![Geef het standaardfoutbericht weer wanneer u een standaardfouthandler in een formulier toevoegt voor de verwerking van foutreacties](/help/forms/assets/default-error-message.png)

### Aangepaste fouthandlerfunctie toevoegen {#add-custom-errror-handler}

U kunt een aangepaste fouthandlerfunctie toevoegen om een aantal van de volgende handelingen uit te voeren:

* foutreacties verwerken die niet-standaard of standaardfoutreacties gebruiken. Het is belangrijk om op te merken dat deze niet-standaardfoutreacties niet voldoen aan de [standaardschema van foutreacties](#failure-response-format).
* verzendt analytische gebeurtenissen naar alle analytische platforms. Bijvoorbeeld Adobe Analytics.
* modaal dialoogvenster weergeven met foutberichten.

Naast de vermelde acties, kunnen de managers van de douanefout worden gebruikt om aangepaste functies uit te voeren die aan specifieke gebruikersvereisten voldoen.

De manager van de douanefout is een functie (de Bibliotheek van de Cliënt) die wordt ontworpen om aan fouten te antwoorden die door de externe dienst zijn teruggekeerd en een aangepaste reactie aan eind te leveren - gebruikers. Elke clientbibliotheek met annotatie `@errorHandler` wordt beschouwd als een aangepaste fouthandlerfunctie. Deze aantekening helpt de functie van de foutenmanager te identificeren die in `.js` bestand.
Als u wilt weten hoe u een aangepaste fouthandler maakt en gebruikt met de functie [De Invoke-service van de Rule Editor](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) handeling, laten we een voorbeeld nemen van Adaptief formulier met twee velden. **Huisdier-id** en **Naam huisdier** en gebruik een aangepaste fouthandler bij het **Huisdier-id** gebied om diverse fouten te controleren die door het REST eindpunt zijn teruggekeerd dat wordt gevormd om een externe dienst, bijvoorbeeld aan te halen, `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

Voer de volgende stappen uit om een aangepaste fouthandler toe te voegen en te gebruiken in een adaptief formulier:
1. [Een aangepaste fouthandler maken](#create-custom-error-message)
1. [Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen](#use-custom-error-handler)

#### 1. Een aangepaste fouthandler maken {#create-custom-error-message}

Voer de volgende stappen uit om een aangepaste foutfunctie te maken:

1. [Clone your AEM Forms as a Cloud Service Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git).
1. Een map maken onder de `[AEM Forms as a Cloud Service repository folder]/apps/` map. Maak bijvoorbeeld een map met de naam `experience-league`
1. Navigeren naar `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` en een `ClientLibraryFolder` als `clientlibs`.
1. Een map maken met de naam `js`.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` map.
1. Voeg bijvoorbeeld een JavaScript-bestand toe. `function.js`. Het bestand bevat de code voor aangepaste fouthandler.
Voeg de volgende code aan het dossier van JavaScript toe om de reactie en kopballen te tonen, die van het de diensteindpunt van REST, in de browser console worden ontvangen.

   ```javascript
       /**
       * Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers);
           console.log("Custom Error Handler processing end...");
       }
   ```

   Om de standaardfoutenmanager van uw manager van de douanefout te roepen, wordt de volgende lijn van de steekproefcode gebruikt:
   `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `

   >[!NOTE]
   >
   > In de `.content.xml` bestand toevoegen `allowProxy` en `categories` eigenschappen.
   >
   > * `allowProxy = [Boolean]true`
   > * `categories= customfunctionsdemo`
   >In dit geval bijvoorbeeld: [custom-errorhandler-name] wordt verstrekt zoals `customfunctionsdemo`.

1. Sla de `function.js` bestand.
1. Ga naar de `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` map.
1. Een tekstbestand toevoegen als `js.txt`. Het bestand bevat:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla de `js.txt` bestand.\
   De gemaakte mapstructuur ziet er als volgt uit:

   ![Map-structuur voor clientbibliotheek gemaakt](/help/forms/assets/customclientlibrary_folderstructure.png)

   >[!NOTE]
   >
   > Klik voor meer informatie over het maken van aangepaste functies op [aangepaste functies in de Editor voor regels](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#write-rules).

1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding error handling files"
       git push
   ```

1. [Voer de pijplijn uit.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline)

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de manager van de douanefout beschikbaar in uw Adaptieve redacteur van de Regel van de Vorm. Nu, begrijpen hoe te om een manager van de douanefout te vormen en te gebruiken gebruikend de Invoke van de Redacteur van de Regel dienst in AEM Forms.

#### 2. Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen {#use-custom-error-handler}

Voordat u de aangepaste fouthandler implementeert in een adaptief formulier, moet u ervoor zorgen dat de naam van de clientbibliotheek in het dialoogvenster **[!UICONTROL Client Library Category]** wordt uitgelijnd met de naam die is opgegeven in de optie Categorieën van het dialoogvenster `.content.xml` bestand.

![De naam van de clientbibliotheek toevoegen in de configuratie van de adaptieve formuliercontainer](/help/forms/assets/client-library-category-name.png)

In dit geval wordt de naam van de clientbibliotheek opgegeven zoals `customfunctionsdemo` in de `.content.xml` bestand.

Als u een aangepaste fouthandler wilt gebruiken met de **[!UICONTROL Rule Editor's Invoke Service]** handeling:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formulieronderdeel en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteren **[!UICONTROL Create]**.
1. Een voorwaarde maken in het dialoogvenster **Wanneer** van de regel. Bijvoorbeeld wanneer **[Naam van veld Dierenid]** is gewijzigd, selecteert u **is gewijzigd** van de **Frame selecteren** vervolgkeuzelijst.
1. In de **Vervolgens** sectie, selecteert u **[!UICONTROL Invoke Service]** van de **Handeling selecteren** vervolgkeuzelijst.
1. Selecteer een **Post-service** en de overeenkomstige gegevensbindingen van de **Invoer** sectie. Bijvoorbeeld om te bevestigen **Huisdier-id** selecteert u een **Post-service** als **GET /pet/{petId}** en selecteert u **Huisdier-id** in de **Invoer** sectie.
1. Selecteer de gegevensbindingen in het menu **Uitvoer** sectie. Selecteer bijvoorbeeld **Naam huisdier** in de **Uitvoer** sectie.
1. Selecteren **[!UICONTROL Custom Error Handler]** van de **[!UICONTROL Error Handler]** sectie.
1. Klik op **[!UICONTROL Done]**.

![Aangepaste fouthandler toevoegen aan een formulier voor het verwerken van reacties op fouten](/help/forms/assets/custom-error-handler.png)

Als resultaat van deze regel worden de waarden waarvoor u invoert **Huisdier-id** controleert validatie voor **Naam huisdier** het gebruiken van externe dienst die door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![Voeg een aangepaste fouthandler toe aan een formulier voor het verwerken van reacties op fouten](/help/forms/assets/custom-error-handler-message.png)

Open de browser console en controleer de reactie en de kopbal, die van het de diensteindpunt van REST, voor het bericht van de bevestigingsfout worden ontvangen.


De aangepaste fouthandlerfunctie is verantwoordelijk voor het uitvoeren van aanvullende acties, zoals het weergeven van een modaal dialoogvenster of het verzenden van een analysegebeurtenis, op basis van de foutreactie. Een aangepaste fouthandlerfunctie biedt de flexibiliteit om foutafhandeling af te stemmen op de specifieke gebruikersvereisten.

<!-- 

## Configure Adaptive Form submission to add custom handlers {#configure-adaptive-form-submission}

If the server validation error message does not display in the standard format, you can enable asynchronous submission and add a custom error handler on Adaptive Form submission to convert the message into a standard format.

### Configure asynchronous Adaptive Form submission {#configure-asynchronous-adaptive-form-submission}

Before adding custom handler, you must configure the adaptive form for asynchronous submission. Execute the following steps:

1. In adaptive form authoring mode, select the Form Container object and select ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Select **[!UICONTROL Revalidate on server]** to validate the input field values on server before submission.
1. Select the Submit Action:

    * Select **[!UICONTROL Submit using Form Data Model (FDM)]** and select the appropriate data model, if you are using RESTful web service based [form data model (FDM)](work-with-form-data-model.md) as the data source.
    * Select **[!UICONTROL Submit to REST Service endpoint]** and specify the **[!UICONTROL Redirect URL/Path]**, if you are using RESTful web services as the data source.

    ![adaptive form submission properties](assets/af_submission_properties.png)

1. Select ![Save](assets/save_icon.png) to save the properties.

### Add custom error handler on Adaptive Form submission {#add-custom-error-handler-af-submission}

AEM Forms provides out-of-the-box success and error handlers for form submissions. Handlers are client-side functions that execute based on the server response. When an Adaptive Form is submitted, the data is transmitted to the server for validation, which returns a response to the client with information about the success or error event for the submission. The information is passed as parameters to the relevant handler to execute the function.

Execute the following steps to add custom error handler on Adaptive Form submission:

1. Open an Adaptive Form in authoring mode, select any form object, and select  to open the rule editor.
1. Select **[!UICONTROL Form]** in the Form Objects tree and select **[!UICONTROL Create]**.
1. Select **[!UICONTROL Error in Submission]** from the Event drop-down list.
1. Write a rule to convert custom error structure to the standard error structure and select **[!UICONTROL Done]** to save the rule.

The following is a sample code to convert a custom error structure to the standard error structure:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys (errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

The `var som_map` lists the SOM expression of the Adaptive Form fields that you want to transform into the standard format. You can view the SOM expression of any field in an adaptive form by tapping the field and selecting **[!UICONTROL View SOM Expression]**.

Using this custom error handler, the adaptive form converts the fields listed in `var som_map` to standard error message format. As a result, the validation error messages display at field-level in the adaptive form.

 -->


## Zie ook {#see-also}

{{see-also}}
* [Aangepaste fouthandlers maken en gebruiken in Adaptive Forms (Core Components)](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)

<!--

>[!MORELIKETHIS]
>
>* [Create style or themes for your forms](/help/forms/using-themes-in-core-components.md)
>* [Create or add an Adaptive Form to AEM Sites page](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

-->
