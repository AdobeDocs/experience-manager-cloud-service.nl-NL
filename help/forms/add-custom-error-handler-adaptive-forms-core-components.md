---
title: Een aangepaste fouthandler toevoegen in Adaptive Forms op basis van Core Components for AEM Adaptive Forms
description: AEM Forms verstrekt out-of-the-box succes en foutenmanagers voor een vorm gebruikend het REST eindpunt dat wordt gevormd om de externe dienst aan te halen. U kunt een standaardfouthandler en een aangepaste fouthandler toevoegen aan een AEM Adaptive Form.
keywords: Voeg een manager van de douanefout toe, voeg een standaardfoutenmanager toe, voeg een foutenmanager in vorm toe, gebruik de toepassing roept dienst van de redacteur om een douanefoutenmanager toe te voegen, regel redacteur te vormen om een manager van de douanefout toe te voegen, douanefoutafhandeling toe gebruikend regelredacteur
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 4496c4cc-a5d7-4f34-91f9-13eded77b362
role: User, Developer
source-git-commit: 8d43f28e62a865b6b990678544e0d9589f17722a
workflow-type: tm+mt
source-wordcount: '2307'
ht-degree: 0%

---

# Fouthandlers voor adaptief formulier op basis van kerncomponenten {#error-handlers-in-adaptive-form}


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dit artikel |
| AEM 6.5 | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/add-custom-error-handler-adaptive-forms-core-components.html?lang=nl-NL) |

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Het biedt ook functie om functies van fouthandlers aan te passen. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant informeren dat de dienst neer is. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een externe dienst gebruikend APIs wordt aangehaald, worden de gegevens overgebracht naar de server voor bevestiging, die een antwoord op de cliënt met informatie over het succes of de foutengebeurtenis voor de voorlegging terugkeert. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren. Met een fouthandler kunt u fouten of validatieproblemen die zijn opgetreden, beheren en weergeven.

![&#x200B; werkschema van de foutenmanager om te begrijpen hoe te om de manager van de douanefout in vormen toe te voegen &#x200B;](/help/forms/assets/error-handler-workflow.png)

De adaptieve Vorm bevestigt de input die u op gebieden verstrekt die op vooraf ingestelde bevestigingscriteria en controles op diverse fouten wordt gebaseerd door het REST eindpunt wordt gevormd om de externe dienst aan te halen. U kunt de validatiecriteria instellen op basis van de gegevensbron die u gebruikt met het adaptieve formulier. Als u bijvoorbeeld RESTful-webservices gebruikt als gegevensbron, kunt u de validatiecriteria definiëren in een Swagger-definitiebestand.

Als de invoerwaarden aan de validatiecriteria voldoen, worden de waarden naar de andere gegevensbron verzonden, geeft het adaptieve formulier een foutbericht weer met behulp van een fouthandler. Net als bij deze aanpak worden adaptieve Forms geïntegreerd met aangepaste fouthandlers voor het uitvoeren van gegevensvalidaties. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten weergegeven op veldniveau in het adaptieve formulier. Dit gebeurt wanneer het foutbericht van de validatie dat door de server wordt geretourneerd, de standaardberichtindeling heeft.


## Gebruikt fouthandlers {#uses-of-error-handler}

Fouthandlers worden voor verschillende doeleinden gebruikt. Enkele toepassingen van de functies van de foutenmanager zijn hieronder vermeld:

* **voer bevestiging** uit: De fout behandeling begint met het bevestigen van gebruikersinput tegen vooraf bepaalde regels of criteria. Wanneer gebruikers een adaptief formulier invullen, valideert de fouthandler de invoer om ervoor te zorgen dat deze voldoet aan de vereiste indeling, lengte of andere beperkingen.

* **verstrekt in real time terugkoppelt**: Wanneer om het even welke fout wordt ontdekt, geeft de foutenmanager onmiddellijk aan de gebruiker terug, zoals gealigneerde foutenmeldingen onder de overeenkomstige vormgebieden. Met deze feedback kunnen gebruikers fouten opsporen en corrigeren zonder het formulier te hoeven verzenden en op een reactie te moeten wachten.


* **de foutenmeldingen van de Vertoning**: Wanneer een Aangepaste voorlegging van de Vorm om het even welke bevestigingsfout ontmoet, toont de foutenmanager een aangewezen foutenmelding. De foutberichten moeten duidelijk, beknopt en nauwkeurig zijn en de specifieke velden moeten benadrukken die aandacht behoeven.

* **benadrukt het onjuiste gebied**: Om de aandacht van de gebruiker op de specifieke onjuiste gebieden te trekken, benadrukt de foutenmanager of onderscheidt visueel de overeenkomstige gebieden. Dit wordt uitgevoerd door de achtergrondkleur te wijzigen, een pictogram of rand toe te voegen of door andere visuele aanwijzingen die gebruikers helpen de fouten snel te vinden en aan te pakken.


## Opmaak van reactie fout/fout {#failure-response-format}

In een adaptief formulier worden de fouten in een veld weergegeven als de foutberichten voor servervalidatie de volgende standaardindeling hebben.
De onderstaande code illustreert de bestaande structuur van de mislukkingsreactie:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
    }
```


Waarbij:

* `errorCausedBy` beschrijft de reden voor mislukking.
* In `errors` wordt de expressie vermeld van de velden waarvoor de validatiecriteria zijn mislukt, samen met het foutbericht voor validatie.
* `originCode` -veld toegevoegd door AEM en bevat de http-statuscode die door de externe service wordt geretourneerd.
* `originMessage` -veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

Met de verbeteringen in eigenschappen en verdere updates in de versies van AEM Forms, veranderde de bestaande structuur van de mislukkingsreactie in nieuw formaat dat op RFC7807 wordt gebaseerd, die achterwaarts compatibel met de bestaande structuur van de mislukkingsreactie is:

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<qualified fieldname of the field whose data sent is invalid>",
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
> * Zorg ervoor dat de structuur van de foutenreactie of **fieldName** of **dataRef** omvat.
> * Zorg ervoor dat de **&#x200B;**&#x200B;kopbal ContentType **toepassing/problem+json** is.

Waarbij:

* `type (required)` geeft het type fout aan. Dit kan een van de volgende waarden zijn:
   * `SERVER_SIDE_VALIDATION` geeft een fout aan vanwege validatie aan de serverzijde.
   * `FORM_SUBMISSION` geeft een fout aan tijdens het verzenden van het formulier
   * `SERVICE_INVOCATION` geeft een fout aan tijdens het aanroepen van een service van derden.
   * `FAILURE` geeft een algemene fout aan.
   * `VALIDATION_ERROR` geeft een fout aan vanwege een validatiefout.

* `title (optional)` geeft een titel of korte beschrijving van de fout.
* `detail (optional)` geeft indien nodig aanvullende informatie over de fout.
* `instance (optional)` staat voor een instantie of id die aan de fout is gekoppeld en helpt bij het bijhouden of identificeren van de specifieke instantie of id van de fout.
* `validationErrors (required)` bevat informatie over validatiefouten. Het bevat de volgende velden:
   * `fieldname` geeft de gekwalificeerde veldnaam weer van de velden waarvoor de validatiecriteria zijn mislukt.
   * `dataRef` vertegenwoordigt het JSON-pad of XPath van de velden waarvoor de validatie is mislukt.
   * `details` bevat het foutbericht voor validatie met het onjuiste veld.
* `originCode (optional)` -veld toegevoegd door AEM en bevat de http-statuscode geretourneerd door de externe service
* `originMessage (optional)` -veld toegevoegd door AEM en bevat de onbewerkte foutgegevens die door de externe service worden geretourneerd.

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
              "fieldName": "$form.PetId",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```

+++


+++ Gebaseerd op de eigenschap Aangepaste formulierbindingsverwijzing

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
      {
          "type": "VALIDATION_ERROR",
          "validationErrors": [
          {
              "fieldName": "",
              "dataRef": "$.Pet.id",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
              ]
              }
      ]}
  ```

U kunt de waarde van dataRef weergeven in het **[!UICONTROL Properties]** -venster van een formuliercomponent.

+++

## Vereisten om foutenmanager toe te voegen gebruikend de Invoke dienst van de Redacteur van de Regel {#before-you-start-to-add-error-handler}

Alvorens u een foutenmanager gebruikend de Invoke dienst van de Redacteur van de Regel toevoegt:

* Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

* Leer hoe te om [&#x200B; douanefuncties &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=nl-NL#write-rules) tot stand te brengen.


## Fouthandler toevoegen met gebruik van de Regel-editor {#add-error-handler-using-rule-editor}

Gebruikend de [&#x200B; actie van de Dienst van de Redacteur van de Regel van 0&rbrace; Invoke, bepaalt u de bevestigingscriteria die op de gegevensbron worden gebaseerd die u met de Aangepaste Vorm gebruikt. &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=nl-NL#invoke) Als u RESTful-webservices als gegevensbron gebruikt, kunt u de validatiecriteria definiëren in een bestand met definities van de Swagger. Door de functies van de foutenmanager en de Redacteur van de Regel in Aangepast Forms te gebruiken, kunt u fout behandeling effectief beheren en aanpassen. U bepaalt de voorwaarden gebruikend de Redacteur van de Regel en vormt de gewenste acties die moeten worden uitgevoerd wanneer de regel wordt teweeggebracht. Met Aangepast formulier worden de invoer die u invoert in velden gevalideerd op basis van vooraf ingestelde validatiecriteria. Als de invoerwaarden niet voldoen aan de validatiecriteria, worden de foutberichten in een adaptief formulier weergegeven op veldniveau.

>[!NOTE]
>
> * Om foutenmanagers met de Invoke van de Redacteur van de Regel de dienstactie te gebruiken, vorm Aangepast Forms met een model van vormgegevens (FDM).
> * Er wordt een standaardfouthandler geboden voor het weergeven van foutberichten op velden als de foutreactie in het standaardschema staat. U kunt de standaardfoutenmanager van de functie van de douaneformmanager ook roepen.

Gebruikend de Redacteur van de Regel, kunt u:

* [Standaardfouthandlerfunctie toevoegen](#add-default-errror-handler)
* [Aangepaste fouthandlerfunctie toevoegen](#add-custom-errror-handler)


### Standaardfouthandlerfunctie toevoegen {#add-default-errror-handler}

Een standaardfouthandler wordt ondersteund voor het weergeven van foutberichten in velden als de foutreactie in het standaardschema of bij een validatiefout op de server staat.
Om te begrijpen hoe te om een standaardfoutenmanager te gebruiken die de [&#x200B; actie van de Dienst van de Regel van 0&rbrace; aanhaalt van de Regel {, een voorbeeld van een eenvoudige AanpassingsVorm met twee gebieden, &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=nl-NL#invoke) Huididentiteitskaart **en** Naam van Huisdier **gebruikt en een standaardfoutenmanager bij het** Huisdieridentiteitskaart **gebied gebruiken om diverse fouten te controleren die door het REST eindpunt worden gevormd om een externe dienst aan te halen, bijvoorbeeld, 8},**, `200 - OK`. `404 - Not Found` `400 - Bad Request` Om een standaardfoutenmanager toe te voegen gebruikend de Actie van de Dienst van de Redacteur van de Regel Invoke, voer de volgende stappen uit:

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formuliercomponent en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteer **[!UICONTROL Create]** .
1. Creeer een voorwaarde in **wanneer** sectie van de regel. Bijvoorbeeld, **wanneer [ Naam van het gebied van identiteitskaart van het Huisdier]** wordt veranderd. Uitgezocht wordt veranderd van de **Uitgezochte Staat** drop-down lijst.
1. In **toen** sectie, selecteer **[!UICONTROL Invoke Service]** van **Uitgezochte de drop-down lijst van de Actie**.
1. Selecteer de dienst van het a **Post** en zijn overeenkomstige gegevensbindingen van de **3&rbrace; sectie van de Input &lbrace;.** Bijvoorbeeld, om **identiteitskaart van het Huisdier** te bevestigen, selecteer de dienst van het a **Post** als **GET /pet/{petId}** en selecteer **Huididentiteitskaart** in de **sectie van de Invoer**.
1. Selecteer de gegevensbindingen van de **sectie van de Output**. Selecteer **Naam van Huisdier** in de **sectie van de Output**.
1. Selecteer **[!UICONTROL Default Error Handler]** van de **Handler van de Fout** sectie.
1. Klik op **[!UICONTROL Done]**.

![&#x200B; voeg een standaardfoutenmanager voor de controles van de gebiedsbevestiging in een vorm toe &#x200B;](/help/forms/assets/default-error-handler.png)

Als resultaat van deze regel, de waarden u voor **identiteitskaart van het Huisdier** controles bevestiging voor **Naam van het Huisdier** gebruikend externe die dienst door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![&#x200B; toon het standaardfoutenbericht wanneer u een standaardfoutenmanager in een vorm toevoegt om foutenreacties te behandelen &#x200B;](/help/forms/assets/default-error-message.png)

### Aangepaste fouthandlerfunctie toevoegen {#add-custom-errror-handler}

U kunt een aangepaste fouthandlerfunctie toevoegen om een aantal van de volgende handelingen uit te voeren:

* foutreacties verwerken die niet-standaard of standaardfoutreacties gebruiken. Het is belangrijk om op te merken dat deze niet-standaardfoutenreacties niet aan het [&#x200B; standaardschema van foutenreacties &#x200B;](#failure-response-format) voldoen.
* verzendt analytische gebeurtenissen naar alle analytische platforms. Bijvoorbeeld Adobe Analytics.
* modaal dialoogvenster weergeven met foutberichten.

Naast de vermelde acties, kunnen de managers van de douanefout worden gebruikt om aangepaste functies uit te voeren die aan specifieke gebruikersvereisten voldoen.

De manager van de douanefout is een functie (de Bibliotheek van de Cliënt) die wordt ontworpen om aan fouten te antwoorden die door de externe dienst zijn teruggekeerd en een aangepaste reactie aan eind te leveren - gebruikers. Elke clientbibliotheek met annotatie `@errorHandler` wordt beschouwd als een aangepaste fouthandlerfunctie. Deze aantekening helpt de functie van de foutenmanager te identificeren die in het `.js` dossier wordt gespecificeerd.
Om te begrijpen hoe te om een manager van de douanefout tot stand te brengen en te gebruiken die de [&#x200B; Invoke dienst van de Redacteur van de Regel gebruikt &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=nl-NL#invoke) actie, neem een voorbeeld van AanpassingsVorm met twee gebieden, **Huididentiteitskaart** en **Naam van Huisdier** en gebruik een manager van de douanefout bij het **Huisdier ID** gebied om diverse fouten te controleren die door het eindpunt van REST wordt teruggegeven dat wordt gevormd om een externe dienst aan te halen; voorbeeld, `200 - OK`, `404 - Not Found`, `400 - Bad Request`.

Voer de volgende stappen uit om een aangepaste fouthandler toe te voegen en te gebruiken in een adaptief formulier:

1. [&#x200B; creeer een manager van de douanefout &#x200B;](#create-custom-error-message)
1. [Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen](#use-custom-error-handler)

#### &#x200B;1. Een aangepaste fouthandler maken {#create-custom-error-message}

Voer de volgende stappen uit om een aangepaste foutfunctie te maken:

Voer de volgende stappen uit om een aangepaste foutfunctie te maken:

1. [&#x200B; kloon uw Bewaarplaats van AEM Forms as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#accessing-git).
1. Maak een map onder de map `[AEM Forms as a Cloud Service repository folder]/apps/` . Maak bijvoorbeeld een map met de naam `experience-league`
1. Navigeer naar `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` en maak een `ClientLibraryFolder` as `clientlibs` .
1. Maak een map met de naam `js` .
1. Navigeer naar de map `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` .
1. Voeg een JavaScript-bestand toe, bijvoorbeeld `function.js` . Het bestand bevat de code voor aangepaste fouthandler.
Voeg de volgende code aan het dossier van JavaScript toe om de reactie en kopballen te tonen, die van het de diensteindpunt van REST, in de browser console worden ontvangen.

   ```javascript
       /** 
       Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers, globals)
   {
       console.log("Custom Error Handler processing start...");
       console.log("response:"+JSON.stringify(response));
       console.log("headers:"+JSON.stringify(headers));
       alert("CustomErrorHandler - Enter valid PetId.")
       console.log("Custom Error Handler processing end...");
       return true; // true - call default error handler, false - don't call default error handler.
   }
   ```

   In de bovenstaande code roept `return true` automatisch de standaardfouthandler aan. Neem `return false` op om te voorkomen dat de standaardfouthandler standaard wordt aangeroepen.

   >[!NOTE]
   >
   > Voeg `.content.xml` toe in het bestand `categories = [custom-errorhandler-name]` . Bijvoorbeeld, in dit geval, [ douane-errorhandler-name ] wordt verstrekt als `customfunctionsdemoV2`.


1. Sla het `function.js` -bestand op.
1. Navigeer naar de map `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` .
1. Voeg een tekstbestand toe als `js.txt` . Het bestand bevat:

   ```javascript
       #base=js
       functions.js
   ```

1. Sla het `js.txt` -bestand op.\
   De gemaakte mapstructuur ziet er als volgt uit:

   ![&#x200B; creeerde de Omslagstructuur van de Bibliotheek van de Cliënt &#x200B;](/help/forms/assets/customclientlibrary_folderstructure.png)

   >[!NOTE]
   >
   > Meer over leren hoe te om douanefuncties tot stand te brengen, klik [&#x200B; douanefuncties in de Redacteur van de Regel &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=nl-NL#write-rules).


1. U kunt de wijzigingen in de opslagplaats toevoegen, vastleggen en doorvoeren met behulp van de onderstaande opdrachten:

   ```javascript
       git add .
       git commit -a -m "Adding error handling files"
       git push
   ```

1. [&#x200B; stel de pijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=nl-NL#setup-pipeline) in werking.

Zodra de pijpleiding met succes wordt uitgevoerd, wordt de manager van de douanefout beschikbaar in uw Adaptieve redacteur van de Regel van de Vorm. Nu, begrijpen hoe te om een manager van de douanefout te vormen en te gebruiken gebruikend de Invoke van de Redacteur van de Regel dienst in AEM Forms.

#### &#x200B;2. Gebruik de Redacteur van de Regel om de manager van de douanefout te vormen {#use-custom-error-handler}

Voordat u de aangepaste fouthandler implementeert in een adaptief formulier, moet u ervoor zorgen dat de naam van de clientbibliotheek in de **[!UICONTROL Client Library Category]** wordt uitgelijnd met de naam die is opgegeven in de optie Categorieën van het `.content.xml` -bestand.

![&#x200B; Toevoegend de naam van de cliëntbibliotheek in de Adaptieve configuratie van de Container van de Vorm &#x200B;](/help/forms/assets/client-library-category-name-core-component.png)

Een aangepaste fouthandler gebruiken met de handeling **[!UICONTROL Rule Editor's Invoke Service]** :

1. Open een adaptief formulier in de ontwerpmodus, selecteer een formuliercomponent en selecteer **[!UICONTROL Rule Editor]** om de regeleditor te openen.
1. Selecteer **[!UICONTROL Create]** .
1. Creeer een voorwaarde in **wanneer** sectie van de regel. Bijvoorbeeld, wanneer **[Naam van het gebied van identiteitskaart van het Huisdier]** wordt veranderd, wordt de uitgezochte **veranderd** van de **Uitgezochte Staat** drop-down lijst.
1. In **toen** sectie, selecteer **[!UICONTROL Invoke Service]** van **Uitgezochte de drop-down lijst van de Actie**.
1. Selecteer de dienst van het a **Post** en zijn overeenkomstige gegevensbindingen van de **3&rbrace; sectie van de Input &lbrace;.** Bijvoorbeeld, om **identiteitskaart van het Huisdier** te bevestigen, selecteer de dienst van het a **Post** als **GET /pet/{petId}** en selecteer **Huididentiteitskaart** in de **sectie van de Invoer**.
1. Selecteer de gegevensbindingen van de **sectie van de Output**. Bijvoorbeeld, Uitgezochte **Naam van Huisdier** in de **sectie van de Output**.
1. Selecteer **[!UICONTROL Custom Error Handler]** in de sectie **[!UICONTROL Error Handler]** .
1. Klik op **[!UICONTROL Done]**.

![&#x200B; voeg douanefoutenmanager in een vorm toe om foutenreacties &#x200B;](/help/forms/assets/custom-error-handler.png) te behandelen


Als resultaat van deze regel, de waarden u voor **identiteitskaart van het Huisdier** controles bevestiging voor **Naam van het Huisdier** gebruikend externe die dienst door het eindpunt van REST wordt aangehaald. Als de validatiecriteria op basis van de gegevensbron mislukken, worden de foutberichten weergegeven op veldniveau.

![&#x200B; voeg een manager van de douanefout in een vorm toe om foutenreacties te behandelen &#x200B;](/help/forms/assets/custom-error-handler-message-core-component.png)

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

    * Select **[!UICONTROL Submit using Form Data Model]** and select the appropriate data model, if you are using RESTful web service based [form data model](work-with-form-data-model.md) as the data source.
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
            Object.keys(errorData).forEach(function(key) {
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

## Aanvullende informatie {#additional-information}

* [Een op zichzelf staand adaptief formulier voor kerncomponenten maken](/help/forms/creating-adaptive-form-core-components.md)
* [Stijlen of thema&#39;s maken voor uw formulieren](/help/forms/using-themes-in-core-components.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

## Zie ook {#see-also}

{{see-also}}

