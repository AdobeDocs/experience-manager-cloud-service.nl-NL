---
title: Hoe maakt u een aangepaste verzendactie voor een adaptief formulier?
description: Leer hoe te om een douane te creëren legt Actie voor een Aangepast Forms voor om voorlegging en procesgegevens uit te stellen alvorens het aan een rusteindpunt voor te leggen, sparen aan een gegevensopslag, en andere douanefuncties uit te voeren.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 77131cc2-9cb1-4a00-bbc4-65b1a66e76f5
source-git-commit: 82a3016149645701abe829ad89c493f480956267
workflow-type: tm+mt
source-wordcount: '1700'
ht-degree: 0%

---

# Een aangepaste verzendactie maken voor Adaptieve Forms {#writing-custom-submit-action-for-adaptive-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/customize-aem-forms/custom-submit-action-form.html?lang=nl-NL) |
| AEM as a Cloud Service (Core Components) | [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/custom-submit-action-for-adaptive-forms-based-on-core-components) |
| AEM as a Cloud Service (Foundation Components) | Dit artikel |

Een adaptief formulier biedt meerdere OTB-acties (Verzenden buiten de box). In een handeling Verzenden worden de details opgegeven van de handelingen die moeten worden uitgevoerd op de gegevens die via het adaptieve formulier zijn verzameld. Bijvoorbeeld, verzendend gegevens over een e-mail.

U kunt een douane creëren legt Actie voor om functionaliteit toe te voegen niet inbegrepen in [ uit-van-de-doos Acties ](configuring-submit-actions.md) of niet gesteund via één enkele OTB legt Actie voor. Bijvoorbeeld het verzenden van gegevens naar een werkstroom, het opslaan van de gegevens in een gegevensopslag, het verzenden van e-mailbericht naar de persoon die het formulier verzendt, en het verzenden van een e-mail naar de persoon die verantwoordelijk is voor de verwerking van het ingediende formulier voor goedkeuringen en afwijzingen via één verzendhandeling.

## XML-gegevensindeling {#xml-data-format}

De XML-gegevens worden naar de servlet verzonden met behulp van de aanvraagparameter **`jcr:data`** . Verzendhandelingen hebben toegang tot de parameter om de gegevens te verwerken. In de volgende code wordt de indeling van de XML-gegevens beschreven. De velden die aan het formuliermodel zijn gebonden, worden weergegeven in de sectie **`afBoundData`** . De niet verbindende gebieden verschijnen in de `afUnoundData` sectie. <!--For more information about the format of the `data.xml` file, see [Introduction to prepopulating Adaptive Form fields](prepopulate-adaptive-form-fields.md).-->

```xml
<?xml ?>
<afData>
<afUnboundData>
<data>
<field1>value</field2>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
</data>
</afUnboundData>
<afBoundData>
<!-- xml corresponding to the Form Model /XML Schema -->
</afBoundData>
</afData>
```

### Actievelden {#action-fields}

Een Submit Actie kan verborgen inputgebieden (gebruikend de HTML [ input ](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input) markering) aan teruggegeven vormHTML toevoegen. Deze verborgen velden kunnen waarden bevatten die nodig zijn tijdens de verwerking van formulierverzendingen. Bij het verzenden van het formulier worden deze veldwaarden teruggeplaatst als aanvraagparameters die de verzendactie kan gebruiken tijdens de verwerking van het formulier. De invoervelden worden actievelden genoemd.

Met een handeling Verzenden die ook de tijd vastlegt die nodig is om een formulier in te vullen, kunt u bijvoorbeeld de verborgen invoervelden `startTime` en `endTime` toevoegen.

Een script kan de waarden van de velden `startTime` en `endTime` opgeven wanneer het formulier wordt gerenderd en vóór het verzenden van het formulier. Met het script Handeling verzenden `post.jsp` hebt u vervolgens toegang tot deze velden met behulp van aanvraagparameters en kunt u de totale tijd berekenen die nodig is om het formulier in te vullen.

### Bestandsbijlagen {#file-attachments}

Verzendhandelingen kunnen ook de bestandsbijlagen gebruiken die u uploadt met de component Bestandsbijlage. Verzend de manuscripten van de Actie kunnen tot deze dossiers toegang hebben gebruikend de van de schuine streep [ RequestParameter API ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). De [ isFormField ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) methode van de API hulp identificeert zich of de verzoekparameter een dossier of een vormgebied is. U kunt de parameters van het Verzoek in een Submit Actie herhalen om de parameters van de Bijlage van het Dossier te identificeren.

De volgende voorbeeldcode identificeert de bestandsbijlagen in de aanvraag. Daarna, leest het de gegevens in het dossier gebruikend [ krijg API ](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get()). Ten slotte wordt een object Document gemaakt met behulp van de gegevens en toegevoegd aan een lijst.

```java
RequestParameterMap requestParameterMap = slingRequest.getRequestParameterMap();
for (Map.Entry<String, RequestParameter[]> param : requestParameterMap.entrySet()) {
    RequestParameter rpm = param.getValue()[0];
    if(!rpm.isFormField()) {
        fileAttachments.add(new Document(rpm.get()));
    }
}
```

Als u bestanden bijvoegt bij het adaptieve formulier, valideert de server de bestandsbijlagen na het verzenden van het adaptieve formulier en wordt een foutbericht geretourneerd als:

* Bestandsbijlagen bevatten een bestandsnaam die begint met het teken (.) en die \ / : * ? bevat &quot; &lt; > | ; % $ tekens of bevat speciale bestandsnamen die zijn gereserveerd voor Windows-besturingssystemen, zoals `nul` , `prn` , `con` , `lpt` of `com` .

* De grootte van de bestandsbijlage is 0 bytes.

* Het formaat van de dossiergehechtheid wordt niet bepaald in de [ Ondersteunde sectie van de Types van Dossier ](https://helpx.adobe.com/nl/document-cloud/help/supported-file-formats-fill-sign.html#main-pars_text) terwijl het vormen van de component van de Bijlage van het Dossier in een Aangepaste Vorm.

### Pad doorsturen en URL omleiden {#forward-path-and-redirect-url}

Nadat de vereiste actie is uitgevoerd, stuurt de Submit servlet de aanvraag door naar het voorwaartse pad. Een handeling gebruikt de setForwardPath API om het voorwaartse pad in te stellen in de Guide Submit servlet.

Als de handeling geen voorwaarts pad biedt, leidt de verzendserver de browser om met de Redirect URL. De auteur configureert de omleidings-URL met behulp van de configuratie Bedankt voor de pagina in het dialoogvenster Formulier bewerken. U kunt de Redirect URL ook configureren via de Submit Action of de setRedirectUrl API in de Guide Submit servlet. U kunt de parameters van het Verzoek die naar Redirect URL worden verzonden ook vormen gebruikend setRedirectParameters API in de Gids Submit servlet.

>[!NOTE]
>
>Een auteur verstrekt Redirect URL (gebruikend de Dank u Configuratie van de Pagina). [ OOTB legt Acties ](configuring-submit-actions.md) voor gebruik Redirect URL om browser van het middel om te leiden dat de voorwaartse wegverwijzingen.
>
>U kunt een aangepaste handeling Verzenden schrijven die een aanvraag doorstuurt naar een bron of servlet. Adobe raadt aan dat het script dat de verwerking van bronnen voor het voorwaartse pad uitvoert, de aanvraag omleidt naar de Redirect URL wanneer de verwerking is voltooid.

## Handeling verzenden {#submit-action}

Een handeling Verzenden is een sling:map die het volgende bevat:

* **addfields.jsp**: Dit manuscript verstrekt de actievelden die aan het dossier van HTML tijdens vertoning worden toegevoegd. Gebruik dit script om verborgen invoerparameters toe te voegen die vereist zijn tijdens verzending in het script post.POST.jsp.
* **dialog.xml**: Dit manuscript is gelijkaardig aan de dialoog van de Component CQ. Het verstrekt configuratieinformatie die de auteur aanpast. De velden worden weergegeven op het tabblad Handelingen verzenden in het dialoogvenster Formulier bewerken Adaptief wanneer u Handeling verzenden selecteert.
* **post.POST.jsp**: Submit servlet roept dit manuscript met de gegevens die u en de extra gegevens in de vorige secties voorlegt. Elke vermelding van het uitvoeren van een handeling op deze pagina houdt in dat het script post.POST.jsp wordt uitgevoerd. Als u de handeling Verzenden wilt registreren bij de Adaptief Forms voor weergave in het dialoogvenster Formulier bewerken, voegt u de volgende eigenschappen toe aan de `sling:Folder` :

   * **guideComponentType** van typeKoord en waarde **fd/af/components/guidesubmittype**
   * **guideDataModel** van typeKoord dat het type van AanpassingsVorm specificeert waarvoor de Submit Actie van toepassing is. <!--**xfa** is supported for XFA-based Adaptive Forms while -->**xsd** wordt gesteund voor op XSD-Gebaseerde Aanpassings Forms. **basis** wordt gesteund voor Aanpassings Forms die geen XDP of XSD gebruiken. Voeg de overeenkomende tekenreeksen toe om de handeling weer te geven op meerdere typen Adaptief Forms. Scheid elke tekenreeks door een komma. Als u bijvoorbeeld een handeling zichtbaar wilt maken op <!--XFA- and --> XSD-gebaseerde Adaptieve Forms, geeft u de waarde op als <!--**xfa** and--> **xsd**.

   * **jcr:beschrijving** van typeKoord. De waarde van deze eigenschap wordt weergegeven in de lijst Handeling verzenden op het tabblad Handelingen verzenden van het dialoogvenster Formulier bewerken Adaptief. De OOTB-acties zijn aanwezig in de CRX-opslagplaats op de locatie **/libs/fd/af/components/guidesubmittype** .

   * **submitService** van typeKoord. Voor meer informatie, zie [ de Aangepaste voorlegging van de Vorm van het Programma voor douaneacties ](#schedule-adaptive-form-submission).

## Een aangepaste verzendhandeling maken {#creating-a-custom-submit-action}

>[!NOTE]
>
> Leren hoe te om een douane te creëren voorlegt actie voor de Componenten van de Kern, zie [ een douane verzend actie voor Aanpassings Forms (de Componenten van de Kern) ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/custom-submit-action-for-adaptive-forms-based-on-core-components).

Voer de volgende stappen uit om een aangepaste handeling Verzenden te maken die de gegevens opslaat in de CRX-opslagplaats en u vervolgens een e-mail stuurt. Het adaptieve formulier bevat de afgekeurde OOTB-code voor het verzenden van Action Store-inhoud die de gegevens opslaat in de CRX-opslagplaats. Bovendien verstrekt AEM a [ Post ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/mailer/package-summary.html) API die kan worden gebruikt om e-mail te verzenden. Voordat u de e-mail-API gebruikt, configureert u de Day CQ Mail-service via de systeemconsole. U kunt de actie Store Content (afgekeurd) opnieuw gebruiken om de gegevens in de opslagplaats op te slaan. De actie Store Content (afgekeurd) is beschikbaar op de locatie /libs/fd/af/components/guidesubmittype/store in de CRX-opslagplaats.

1. Meld u aan bij CRXDE Lite op de URL https://&lt;server>:&lt;port>/crx/de/index.jsp. Maak een knooppunt met de eigenschap sling:Folder en name store_and_mail in de map /apps/custom_submit_action. Maak de map custom_submit_action als deze nog niet bestaat.

   ![ Scherenshot die de verwezenlijking van een knoop met het bezit toont:Omslag ](assets/step1.png)

2. **verstrek de verplichte configuratiegebieden.**

   Voeg de configuratie toe die de winkelactie vereist. Kopieer **cq:dialoog** knoop van de actie van de Opslag van /libs/fd/af/components/guidesubmittype/store aan de actiemap bij /apps/custom_submit_action/store_and_email.

   ![ Schermafbeelding die het kopiëren van de dialoogknoop aan de actiemap tonen ](assets/step2.png)

3. **verstrek configuratiegebieden om de auteur voor e-mailconfiguratie te veroorzaken.**

   Het adaptieve formulier bevat ook een e-mailactie waarmee e-mailberichten naar gebruikers worden verzonden. Pas deze actie aan op basis van uw vereisten. Ga naar /libs/fd/af/components/guidesubmittype/email/dialog. Kopieer de knooppunten in het cq:dialog-knooppunt naar cq:dialog-knooppunt van uw verzendhandeling (/apps/custom_submit_action/store_and_email/dialog).

   ![ Aanpassen van de e-mailactie ](assets/step3.png)

4. **maak de actie beschikbaar in de Aangepaste Vorm geeft dialoog uit.**

   Voeg de volgende eigenschappen in de store_and_email knoop toe:

   * **guideComponentType** van type **Koord** en waarde **fd/af/components/guidesubmittype**

   * **guideDataModel** van type **Koord** en waarde **<!--xfa, -->xsd, basis**

   * **jcr:beschrijving** van type **Koord** en waarde **Slag en E-mailActie**

   * **submitService** van type **Koord** en waarde **opslag en E-mail**. Voor meer informatie, zie [ de Aangepaste voorlegging van de Vorm van het Programma voor douaneacties ](#schedule-adaptive-form-submission).

5. Open een adaptief formulier. Klik **uitgeven** knoop naast **Begin** om **te openen geef** dialoog van de Aangepaste container van de Vorm uit. De nieuwe actie wordt getoond in **legt Acties** Lusje voor. Het selecteren van de **Opslag en E-mailActie** toont de configuratie die in de dialoogdoos wordt toegevoegd.

   ![ voorlegt de configuratiedialoog van de Actie ](assets/store_and_email_submit_action_dialog.jpg)

6. **gebruik de actie om een taak te voltooien.**

   Voeg het script post.POST.jsp toe aan uw handeling. (/apps/custom_submit_action/store_and_mail/).

   Voer de actie OOTB Store uit (script post.POST.jsp). Gebruik [ FormsHelper.runAction ](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/foundation/forms/FormsHelper.html#runAction-java.lang.String-java.lang.String-org.apache.sling.api.resource.Resource-org.apache.sling.api.SlingHttpServletRequest-org.apache.sling.api.SlingHttpServletResponse-) (java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse) API die CQ verstrekt in je code om de actie Winkel uit te voeren. Voeg de volgende code in uw JSP dossier toe:

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   Om e-mail te verzenden, leest de code het e-mailadres van de ontvanger van de configuratie. Om de configuratiewaarde in het manuscript van de actie te halen, lees de eigenschappen van het huidige middel gebruikend de volgende code. Op dezelfde manier kunt u de andere configuratiedossiers lezen.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   Tot slot gebruikt u de CQ Mail-API om de e-mail te verzenden. Gebruik de [ klasse SimpleEmail ](https://commons.apache.org/proper/commons-email/commons-email2-javax/apidocs/org/apache/commons/mail2/javax/SimpleEmail.html) om het E-mailVoorwerp tot stand te brengen zoals hieronder afgebeeld:

   >[!NOTE]
   >
   >Zorg ervoor dat het JSP-bestand de naam post.POST.jsp heeft.

   ```java
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <%@page import="com.day.cq.wcm.foundation.forms.FormsHelper,
          org.apache.sling.api.resource.ResourceUtil,
          org.apache.sling.api.resource.ValueMap,
                   com.day.cq.mailer.MessageGatewayService,
     com.day.cq.mailer.MessageGateway,
     org.apache.commons.mail.Email,
                   org.apache.commons.mail.SimpleEmail" %>
   <%@taglib prefix="sling"
                   uri="https://sling.apache.org/taglibs/sling/1.0" %>
   <%@taglib prefix="cq"
                   uri="https://www.day.com/taglibs/cq/1.0"
   %>
   <cq:defineObjects/>
   <sling:defineObjects/>
   <%
           String storeContent =
                       "/libs/fd/af/components/guidesubmittype/store";
           FormsHelper.runAction(storeContent, "post", resource,
                                   slingRequest, slingResponse);
    ValueMap props = ResourceUtil.getValueMap(resource);
    Email email = new SimpleEmail();
    String[] mailTo = props.get("mailto", new String[0]);
    email.setFrom((String)props.get("from"));
           for (String toAddr : mailTo) {
               email.addTo(toAddr);
      }
    email.setMsg((String)props.get("template"));
    email.setSubject((String)props.get("subject"));
    MessageGatewayService messageGatewayService =
                       sling.getService(MessageGatewayService.class);
    MessageGateway messageGateway =
                   messageGatewayService.getGateway(SimpleEmail.class);
    messageGateway.send(email);
   %>
   ```

   Selecteer de handeling in het adaptieve formulier. De actie verzendt een e-mail en slaat de gegevens op.

## Use submitService property for custom Submit Actions {#submitservice-property}

Wanneer u de douane plaatst legt Actie voor, die het `submitService` bezit omvat, brengt de vorm [ FormSubmitActionService ](https://helpx.adobe.com/nl/experience-manager/6-5/forms/javadocs/com/adobe/aemds/guide/service/FormSubmitActionService.html) op voorlegging in werking. In `FormSubmitActionService` wordt de methode `getServiceName` gebruikt om de waarde voor de eigenschap `submitService` op te halen. Gebaseerd op de waarde van het `submitService` bezit, roept de dienst aangewezen voorlegt methode aan. Neem de `FormSubmitActionService` op in de aangepaste bundel die u uploadt naar de [!DNL AEM Forms] -server.

Voeg de eigenschap `submitService` van het type tekenreeks toe aan de `sling:Folder` van de aangepaste handeling Verzenden om [!DNL Adobe Sign] in te schakelen voor het adaptieve formulier. U kunt de optie **[!UICONTROL Enable Adobe Sign]** alleen selecteren in het gedeelte **[!UICONTROL Electronic Signature]** van de containereigenschappen van het adaptieve formulier nadat u de waarde hebt ingesteld voor de eigenschap `submitService` van de aangepaste verzendactie.

<!--As a result of setting an appropriate value for the `submitService` property and enabling [!DNL Adobe Sign], you can schedule the submission of an Adaptive Form to ensure that all configured signers have taken an action on the form. [!DNL Adobe Sign] Configuration Service keeps polling [!DNL Adobe Sign] server at regular intervals to verify the status of signatures. If all the signers complete signing the form, the Submit Action service is started and the form is submitted.-->


![ voorlegt de dienstbezit ](assets/submit-service-property.png)

<!-- You can't do comments within comments, so I changed comment tags to <start-comment> <end-comment> -->

<!--
## Workflow for a Submit Action {#workflow-for-a-submit-action}

The flowchart depicts the workflow for a Submit Action that is triggered when you click the **[!UICONTROL Submit]** button in an Adaptive Form. The files in the File Attachment component are uploaded to the server, and the form data is updated with the URLs of the uploaded files. Within the client, the data is stored in the JSON format. The client sends an Ajax request to an internal servlet that massages the data you specified and returns it in the XML format. The client collates this data with action fields. It submits the data to the final servlet (Guide Submit servlet) through a Form Submit Action. Then, the servlet forwards the control to the Submit Action. The Submit Action can forward the request to a different sling resource or redirect the browser to another URL.

![Flowchart depicting the workflow for Submit Action](assets/diagram1.png)

### XML data format {#xml-data-format}

The XML data is sent to the servlet using the **`jcr:data`** request parameter. Submit Actions can access the parameter to process the data. The following code describes the format of the XML data. The fields that are bound to the Form model appear in the **`afBoundData`** section. Unbound fields appear in the `afUnoundData`section. For more information about the format of the `data.xml` file, see [Introduction to prepopulating Adaptive Form fields](prepopulate-adaptive-form-fields.md).

```xml
<?xml ?>
<afData>
<afUnboundData>
<data>
<field1>value</field2>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
<repeatablePanel>
    <field2>value</field2>
</repeatablePanel>
</data>
</afUnboundData>
<afBoundData>
<start comment> xml corresponding to the Form Model /XML Schema <end comment>
<start comment> </afBoundData> <end comment>
</afData>
```

### Action fields {#action-fields}

A Submit Action can add hidden input fields (using the HTML [input](https://developer.mozilla.org/en/docs/Web/HTML/Element/Input) tag) to the rendered form HTML. These hidden fields can contain values that it needs while processing form submission. When submitting the form, these field values are posted back as request parameters that the Submit Action can use during submission handling. The input fields are called action fields.

For example, a Submit Action that also captures the time taken to fill a form can add the hidden input fields `startTime` and `endTime`.

A script can supply the values of the `startTime` and `endTime` fields when the form renders and before form submission, respectively. The Submit Action script `post.jsp` can then access these fields using request parameters and compute the total time required to fill the form.

### File attachments {#file-attachments}

Submit Actions can also use the file attachments you upload using the File Attachment component. Submit Action scripts can access these files using the sling [RequestParameter API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html). The [isFormField](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#isFormField()) method of the API helps identify whether the request parameter is a file or a form field. You can iterate over the Request parameters in a Submit Action to identify File Attachment parameters.

The following sample code identifies the file attachments in the request. Next, it reads the data into the file using the [Get API](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/request/RequestParameter.html#get()). Finally, it creates a Document object using the data and appends it to a list.

```java
RequestParameterMap requestParameterMap = slingRequest.getRequestParameterMap();
for (Map.Entry<String, RequestParameter[]> param : requestParameterMap.entrySet()) {
    RequestParameter rpm = param.getValue()[0];
    if(!rpm.isFormField()) {
        fileAttachments.add(new Document(rpm.get()));
    }
}
```

### Forward path and Redirect URL {#forward-path-and-redirect-url}

After performing the required action, the Submit servlet forwards the request to the forward path. An action uses the setForwardPath API to set the forward path in the Guide Submit servlet.

If the action does not provide a forward path, the Submit servlet redirects the browser using the Redirect URL. The author configures the Redirect URL using the Thank You Page configuration in the Adaptive Form Edit dialog. You can also configure the Redirect URL through the Submit Action or the setRedirectUrl API in the Guide Submit servlet. You can also configure the Request parameters sent to the Redirect URL using the setRedirectParameters API in the Guide Submit servlet.

>[!NOTE]
>
>An author provides the Redirect URL (using the Thank You Page Configuration). [OOTB Submit Actions](configuring-submit-actions.md) use the Redirect URL to redirect the browser from the resource that the forward path references.
>
>You can write a custom Submit Action that forwards a request to a resource or servlet. Adobe recommends that the script that performs resource handling for the forward path redirect the request to the Redirect URL when the processing completes.

## Submit Action {#submit-action}

A Submit Action is a sling:Folder that includes the following:

* **addfields.jsp**: This script provides the action fields that are added to the HTML file during rendition. Use this script to add hidden input parameters required during submission in the post.POST.jsp script.
* **dialog.xml**: This script is similar to the CQ Component dialog. It provides configuration information that the author customizes. The fields are displayed in the Submit Actions Tab in the Adaptive Form Edit dialog when you select the Submit Action.
* **post.POST.jsp**: The Submit servlet calls this script with the data that you submit and the additional data in the previous sections. Any mention of running an action in this page implies running the post.POST.jsp script. To register the Submit Action with the Adaptive Forms to display in the Adaptive Form Edit dialog, add these properties to the sling:Folder:

    * **guideComponentType** of type String and value **fd/af/components/guidesubmittype**
    * **guideDataModel** of type String that specifies the type of Adaptive Form for which the Submit Action is applicable. **xfa** is supported for XFA-based Adaptive Forms while **xsd** is supported for XSD-based Adaptive Forms. **basic** is supported for Adaptive Forms that do not use XDP or XSD. To display the action on multiple types of Adaptive Forms, add the corresponding strings. Separate each string by a comma. For example, to make an action visible on XFA- and XSD-based Adaptive Forms, specify the values **xfa** and **xsd** respectively.

    * **jcr:description** of type String. The value of this property is displayed in the Submit Action list in the Submit Actions Tab of the Adaptive Form Edit dialog. The OOTB actions are present in the CRX repository at the location **/libs/fd/af/components/guidesubmittype**.

## Creating a custom Submit Action {#creating-a-custom-submit-action}

Perform the following steps to create a custom Submit Action that saves the data in the CRX repository and then sends you an email. The Adaptive Form contains the OOTB Submit Action Store Content (deprecated) that saves the data in the CRX repository. In addition, CQ provides a [Mail](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/mailer/package-summary.html) API that can be used to send emails. Before using the Mail API, configure the Day CQ Mail service through the system console. You can reuse the Store Content (deprecated) action to store the data in the repository. The Store Content (deprecated) action is available at the location /libs/fd/af/components/guidesubmittype/store in the CRX repository.

1. Log in to CRXDE Lite at the URL https://&lt;server&gt;:&lt;port&gt;/crx/de/index.jsp. Create a node with the property sling:Folder and name store_and_mail in the /apps/custom_submit_action folder. Create the custom_submit_action folder if it does not exist already.

   ![Screenshot depicting the creation of a node with the property sling:Folder](assets/step1.png)

1. **Provide the mandatory configuration fields.**

   Add the configuration the Store action requires. Copy the **cq:dialog** node of the Store action from /libs/fd/af/components/guidesubmittype/store to the action folder at /apps/custom_submit_action/store_and_email.

   ![Screenshot showing the copying of the dialog node to the action folder](assets/step2.png)

1. **Provide configuration fields to prompt the author for email configuration.**

   The Adaptive Form also provides an Email action that sends emails to users. Customize this action based on your requirements. Navigate to /libs/fd/af/components/guidesubmittype/email/dialog. Copy the nodes within the cq:dialog node to cq:dialog node of your Submit Action (/apps/custom_submit_action/store_and_email/dialog).

   ![Customizing the email action](assets/step3.png)

1. **Make the action available in the Adaptive Form Edit dialog.**

   Add the following properties in the store_and_email node:

    * **guideComponentType** of type **String** and value **fd/af/components/guidesubmittype**

    * **guideDataModel** of type **String** and value **xfa, xsd, basic**

    * **jcr:description** of type **String** and value **Store and Email Action**

1. Open any Adaptive Form. Click the **Edit** button next to **Start** to open the **Edit** dialog of the Adaptive Form container. The new action is displayed in the **Submit Actions** Tab. Selecting the **Store and Email Action** displays the configuration added in the dialog node.

   ![Submit Action configuration dialog](assets/store_and_email_submit_action_dialog.jpg)

1. **Use the action to complete a task.**

   Add the post.POST.jsp script to your action. (/apps/custom_submit_action/store_and_mail/).

   Run the OOTB Store action (post.POST.jsp script). Use the [FormsHelper.runAction](https://www.adobe.io/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/foundation/forms/FormsHelper.html#runAction-java.lang.String-java.lang.String-org.apache.sling.api.resource.Resource-org.apache.sling.api.SlingHttpServletRequest-org.apache.sling.api.SlingHttpServletResponse-(java.lang.String, java.lang.String, org.apache.sling.api.resource.Resource, org.apache.sling.api.SlingHttpServletRequest, org.apache.sling.api.SlingHttpServletResponse)) API that CQ provides in your code to run the Store action. Add the following code in your JSP file:

   `FormsHelper.runAction("/libs/fd/af/components/guidesubmittype/store", "post", resource, slingRequest, slingResponse);`

   To send the email, the code reads the recipient's email address from the configuration. To fetch the configuration value in the action's script, read the properties of the current resource using the following code. Similarly you can read the other configuration files.

   `ValueMap properties = ResourceUtil.getValueMap(resource);`

   `String mailTo = properties.get("mailTo");`

   Finally, use the CQ Mail API to send the email. Use the [SimpleEmail](https://commons.apache.org/proper/commons-email/apidocs/org/apache/commons/mail/SimpleEmail.html) class to create the Email Object as depicted below:

   >[!NOTE]
   >
   >Ensure that the JSP file has the name post.POST.jsp.

   ```java
   <%@include file="/libs/fd/af/components/guidesglobal.jsp" %>
   <%@page import="com.day.cq.wcm.foundation.forms.FormsHelper,
          org.apache.sling.api.resource.ResourceUtil,
          org.apache.sling.api.resource.ValueMap,
                   com.day.cq.mailer.MessageGatewayService,
     com.day.cq.mailer.MessageGateway,
     org.apache.commons.mail.Email,
                   org.apache.commons.mail.SimpleEmail" %>
   <%@taglib prefix="sling"
                   uri="https://sling.apache.org/taglibs/sling/1.0" %>
   <%@taglib prefix="cq"
                   uri="https://www.day.com/taglibs/cq/1.0"
   %>
   <cq:defineObjects/>
   <sling:defineObjects/>
   <%
           String storeContent =
                       "/libs/fd/af/components/guidesubmittype/store";
           FormsHelper.runAction(storeContent, "post", resource,
                                   slingRequest, slingResponse);
    ValueMap props = ResourceUtil.getValueMap(resource);
    Email email = new SimpleEmail();
    String[] mailTo = props.get("mailto", new String[0]);
    email.setFrom((String)props.get("from"));
           for (String toAddr : mailTo) {
               email.addTo(toAddr);
      }
    email.setMsg((String)props.get("template"));
    email.setSubject((String)props.get("subject"));
    MessageGatewayService messageGatewayService =
                       sling.getService(MessageGatewayService.class);
    MessageGateway messageGateway =
                   messageGatewayService.getGateway(SimpleEmail.class);
    messageGateway.send(email);
   %>
   ```

   Select the action in the Adaptive Form. The action sends an email and stores the data. 

-->

>[!MORELIKETHIS]
>
>* [ vorm een Submit Actie voor een Aangepaste Vorm ](/help/forms/configure-submit-actions-core-components.md)