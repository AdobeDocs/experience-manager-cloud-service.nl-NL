---
title: De spreadsheet voorbereiden voor het accepteren van gegevens
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve Forms Block Fields!
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: 086706a1b9ab211738ea2978b73e1681b04ddac2
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# Google-bladen of Microsoft Excel-bestanden instellen om gegevens te accepteren


Zodra u hebt [ gecreeerd en de vorm ](/help/edge/docs/forms/create-forms.md) previewde, is het tijd om het overeenkomstige spreadsheet toe te laten beginnen gegevens te ontvangen. U kunt de spreadsheet handmatig inschakelen voor het accepteren van gegevens of Admin API&#39;s gebruiken om een spreadsheet in te schakelen voor het accepteren van gegevens.

![ op document-gebaseerde het Authoring ecosysteem ](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->


## De spreadsheet handmatig inschakelen voor het accepteren van gegevens

De spreadsheet inschakelen om gegevens te accepteren

1. Open het werkblad met het formulier en voeg een nieuw blad toe, onder een andere naam `incoming` . Bijvoorbeeld, het [ vraag ](/help/edge/assets/enquiry.xlsx) van het werkboek van Microsoft Excel.

   >[!WARNING]
   >
   > Als het `incoming` sheet niet aanwezig is, verzendt AEM geen gegevens naar het spreadsheet.

2. Voeg op dit blad een tabel in met de naam &quot;take_form&quot;. Selecteer het aantal kolommen dat nodig is om overeen te komen met de namen van de formuliervelden. Ga vervolgens op de werkbalk naar Invoegen > Tabel en klik op OK.

3. Wijzig de naam van de tabel in &quot;take_form&quot;. Als u in Microsoft Excel de naam van de tabel wilt wijzigen, selecteert u de tabel en klikt u op Tabelontwerp.

4. Voeg vervolgens de namen van de formuliervelden toe als de tabelkoppen. Om ervoor te zorgen dat de velden exact hetzelfde zijn, kunt u deze kopiëren en plakken vanaf het standaardblad.  Selecteer en kopieer de formulier-id&#39;s onder de kolom Naam op het blad &#39;shared-default&#39;, behalve het verzendveld.

5. Selecteer Plakken speciaal > Rijen omzetten in kolommen op het blad &#39;inkomend&#39; om de veld-id&#39;s als kolomkoppen op dit nieuwe blad te kopiëren. Alleen velden behouden waarvan de gegevens andere gegevens moeten vastleggen, kunnen worden genegeerd.

   Elke waarde in de kolom `Name` van het `shared-default` -blad, met uitzondering van de verzendknop, kan fungeren als koptekst in het `incoming` -blad. Neem bijvoorbeeld de volgende afbeelding die kopteksten illustreert voor een &quot;vraag&quot;-formulier:

   ![ Gebieden voor een contact-usvorm ](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

6. Gebruik de [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) uitbreiding aan voorproef de vormupdates. Uw blad is nu klaar om inkomende formulierverzendingen te accepteren.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u het `incoming` -blad voor het eerst hebt gemaakt.


Nadat de veldnamen aan het `incoming` -werkblad zijn toegevoegd, kan het formulier opmerkingen accepteren. U kunt een voorbeeld van het formulier bekijken en gegevens naar het blad verzenden.

Zodra het blad opstelling is om gegevens te ontvangen, kunt u [ voorproef de vorm ](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> beginnen gegevens naar het blad te verzenden.

>[!WARNING]
>
>  De &quot;gedeelde-standaard&quot;bladen moeten nooit om het even welke persoonlijk identificeerbare informatie of gevoelige gegevens bevatten die u niet aan openbaar toegankelijk bent.

<!--
### Use Admin APIs to enable a spreadsheet to accept data

You can also send a POST request to the form to enable it to accept data and configure headers for the `incoming` sheet. Upon receiving the POST request, the service analyzes the body of request and autonomously generates the essential headers and sheets needed for data ingestion.

To use Admin APIs to enable a spreadsheet to accept data: 


1. Open the workbook that you have created and change the name of the default sheet to `incoming`. 

    >[!WARNING] 
    >
    > If the `incoming` sheet doesn't exist, AEM won't send any data to this workbook.

1. Preview the sheet in the sidekick.

    >[!NOTE] 
    >
    >Even if you have previewed the sheet before, you must preview it again after creating the `incoming` sheet for the first time.

1. Send the POST request to generate the appropriate headers in the `incoming` sheet, and add the `shared-default` sheets to your spread sheet, if it does not exist already.

    To understand how to format the POST request for setting up your sheet, refer to the [Admin API documentation](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). You can look at the example provided below: 

    **Request** 
    
    ```JSON

    POST 'https://admin.aem.page/form/{owner}/{repo}/{branch}/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "john@wknd.com",
            "Name": "John",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```


    **Response**

    ```JSON

    HTTP/2 200 
    content-type: application/json
    x-invocation-id: 1b3bd30a-8cfb-4f85-a662-4b1f7cf367c5
    cache-control: no-store, private, must-revalidate
    accept-ranges: bytes
    date: Sat, 10 Feb 2024 09:26:48 GMT
    via: 1.1 varnish
    x-served-by: cache-del21736-DEL
    x-cache: MISS
    x-cache-hits: 0
    x-timer: S1707557205.094883,VS0,VE3799
    strict-transport-security: max-age=31557600
    content-length: 138

    {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country",      "PreferredContactMethod","SubscribeToNewsletter"]}%

    ```

    You can use tools like curl or Postman to execute this POST request, as demonstrated below:

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
        --header 'Content-Type: application/json' \
        --data '{
            "data": {
                "Email": "john@wknd.com",
                "Name": "John",
                "Subject": "Regarding Product Inquiry",
                "Message": "I have some questions about your products.",
                "Phone": "123-456-7890",
                "Company": "Wknd Inc.",
                "Country": "United States",
                "PreferredContactMethod": "Email",
                "SubscribeToNewsletter": true
        }
    }'

    ```

    The above mentioned POST request provides sample data, including both form fields and their respective sample values. This data is used by the Admin service to set up the form.

    Your form is now enabled to accept data. You also observe the following changes in your spreadsheet: 

## Automatic changes to sheet once it is enabled to accept data. 

Once the sheet is set to recieve data, you observe the following changes in your spreadsheet: 

A sheet named "Slack" is added to your Excel Workbook or Google Sheet. In this sheet, you can configure automatic notifications for a designated Slack channel whenever new data is ingested into your spreadsheet. At present, AEM supports notifications exclusively to the AEM Engineering Slack organization and the Adobe Enterprise Support organization.

1. To set up Slack notifications enter the "teamId" of the Slack workspace and the "channel name" or "ID". You can also ask the slack-bot (with the debug command) for the "teamId" and the "channel ID". Using the "channel ID" instead of the "channel name" is preferable, as it survives channel renames.

    >[!NOTE] 
    >
    > Older forms didn't have the "teamId" column. The "teamId" was included in the channel column, separated by a "#" or "/".

1. Enter any title that you want and under fields enter the names of the fields you want to see in the Slack notification. Each heading should be separated by a comma (For example name, email).

    >[!WARNING] 
    >
    >  Never should the "shared-default" sheets contain any personally identifiable information or sensitive data that you are not comfortable with being publicly accessible.



<!--
## Send data to your sheet {#send-data-to-your-sheet}

After the sheet is set to receive data, you can [preview the form using Adaptive Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) or [use Admin APIs](#use-admin-apis-to-send-data-to-your-sheet) to start sending data to the sheet.

### Use Admin APIs to send data to your sheet

You can send POST requests directly to your form using aem.page, aem.live, or your production domain, to send data. 


```JSON

POST https://branch–repo–owner.aem.(page|live)/email-form
POST https://my-domain.com/email-form

```

>[!NOTE] 
>
> The URL should not have the .json extension. You must publish the sheet for POST operations to function on `.live` or on the production domain.

#### Formatting the form data

There are a few different ways that you can format the form data in the POST body. You can use: 

* array of `name:value` pairs: 
    
    ```JSON
    
    {
      "data": [
        { "name": "name", "value": "Clark Kent" },
        { "name": "email", "value": "superman@example.com" },
        { "name": "subject", "value": "Regarding Product Inquiry" },
        { "name": "message", "value": "I have some questions about your products." },
        { "name": "phone", "value": "123-456-7890" },
        { "name": "company", "value": "Example Inc." },
        { "name": "country", "value": "United States" },
        { "name": "preferred_contact_method", "value": "Email" },
        { "name": "newsletter_subscribe", "value": true }
      ]
    }

    ```

    For example

    ```JSON

    curl -s -i -X POST 'https://main--wefinance--wkndform.aem.page/contact-us' \
        --header 'Content-Type: application/json' \
        --data '{
        "data": [
            { "name": "name", "value": "Clark Kent" },
            { "name": "email", "value": "superman@example.com" },
            { "name": "subject", "value": "Regarding Product Inquiry" },
            { "name": "message", "value": "I have some questions about your        products." },
            { "name": "phone", "value": "123-456-7890" },
            { "name": "company", "value": "Example Inc." },
            { "name": "country", "value": "United States" },
            { "name": "preferred_contact_method", "value": "Email" },
            { "name": "newsletter_subscribe", "value": true }
        ]
    }'

    ```



* an object with `key:value` pairs:

    ```JSON

        {
          "data": {
            "name": "Jessica Jones",
            "email": "jj@example.com",
            "subject": "Regarding Product Inquiry",
            "message": "I have some questions about your products.",
            "phone": "123-456-7890",
            "company": "Example Inc.",
            "country": "United States",
            "preferred_contact_method": "Email",
            "newsletter_subscribe": true
          }
        }

    ```

    For example,

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "khushwant@wknd.com",
            "Name": "khushwant",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```

* URL encoded (`x-www-form-urlencoded`) body (with `content-type` header set to `application/x-www-form-urlencoded`)

    ```Shell

    'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'

    ```

    For example, if your project's repository is named "wefinance", it's located under the account owner "wkndform", and you're using the "main" branch.,

    ```Shell

    curl -s -i -X POST \
      -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
      https://main--wefinance--wkndform.aem.live/contact-us

    ```
-->

Daarna, kunt u [ aanpassen dankt u bericht ](/help/edge/docs/forms/thank-you-page-form.md).

## Zie ook

{{see-more-forms-eds}}
