---
title: De spreadsheet voorbereiden voor het accepteren van gegevens
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve Forms Block Fields!
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 0%

---

# Google-bladen of Microsoft Excel-bestanden instellen om gegevens te accepteren


Eenmaal [Het formulier maken en een voorbeeld bekijken](/help/edge/docs/forms/create-forms.md), is het tijd om de overeenkomstige spreadsheet toe te laten beginnen gegevens te ontvangen. U kunt de spreadsheet handmatig inschakelen voor het accepteren van gegevens of Admin API&#39;s gebruiken om een spreadsheet in te schakelen voor het accepteren van gegevens.

![Ontwerpecosysteem op basis van documenten](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->


## De spreadsheet handmatig inschakelen voor het accepteren van gegevens

De spreadsheet inschakelen om gegevens te accepteren

1. Open het werkblad met het formulier en voeg een nieuw blad toe, onder een andere naam `incoming`.

   >[!WARNING]
   >
   > Als de `incoming` blad is niet aanwezig, AEM verzendt geen gegevens naar het werkblad.

1. Voeg op dit blad een tabel in met de naam &quot;take_form&quot;. Selecteer het aantal kolommen dat nodig is om overeen te komen met de namen van de formuliervelden. Ga vervolgens op de werkbalk naar Invoegen > Tabel en klik op OK.

1. Wijzig de naam van de tabel in &quot;take_form&quot;. Als u in Microsoft Excel de naam van de tabel wilt wijzigen, selecteert u de tabel en klikt u op Tabelontwerp.

1. Voeg vervolgens de namen van de formuliervelden toe als de tabelkoppen. Om ervoor te zorgen dat de velden exact hetzelfde zijn, kunt u deze kopiëren en plakken vanaf het standaardblad.  Selecteer en kopieer de formulier-id&#39;s onder de kolom Naam op het blad &#39;shared-default&#39;, behalve het verzendveld.

1. Selecteer Plakken speciaal > Rijen omzetten in kolommen op het blad &#39;inkomend&#39; om de veld-id&#39;s als kolomkoppen op dit nieuwe blad te kopiëren. Alleen velden behouden waarvan de gegevens andere gegevens moeten vastleggen, kunnen worden genegeerd.

   Elke waarde in het dialoogvenster `Name` kolom van de `shared-default` blad, met uitzondering van de verzendknop, kan dienen als koptekst in het dialoogvenster `incoming` blad. Neem bijvoorbeeld de volgende afbeelding die kopteksten illustreert voor een formulier &quot;contact-us&quot;:

   ![Velden voor een formulier met contactgegevens](/help/edge/assets/contact-us-form-excel-sheet-fields.png)



1. Gebruik de extensie AEM Sidekick om een voorbeeld van de formulierupdates weer te geven. Uw blad is nu klaar om inkomende formulierverzendingen te accepteren.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u het `incoming` blad voor het eerst.


Nadat de veldnamen aan de `incoming` blad, kan uw formulier opmerkingen accepteren. U kunt een voorbeeld van het formulier bekijken en gegevens naar het blad verzenden.

Zodra het blad is ingesteld om gegevens te ontvangen, kunt u [Een voorbeeld van het formulier weergeven met Adaptief Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) of [aanvragen voor POST gebruiken](#use-admin-apis-to-send-data-to-your-sheet) om gegevens naar het blad te verzenden.

>[!WARNING]
>
>  De &quot;gedeelde-standaard&quot;bladen moeten nooit om het even welke persoonlijk identificeerbare informatie of gevoelige gegevens bevatten die u niet aan openbaar toegankelijk bent.

### Admin API&#39;s gebruiken om een spreadsheet in te schakelen voor het accepteren van gegevens

U kunt ook een verzoek van de POST naar het formulier verzenden, zodat het gegevens kan accepteren en headers voor de `incoming` blad. Na ontvangst van het verzoek van de POST analyseert de dienst het lichaam van verzoek en produceert autonoom de essentiële kopballen en bladen nodig voor gegevensopname.

Admin APIs gebruiken om een spreadsheet toe te laten om gegevens goed te keuren:


1. Open het werkboek dat u hebt gecreeerd en verander de naam van het standaardblad in `incoming`.

   >[!WARNING]
   >
   > Als de `incoming` Het blad bestaat niet, AEM verzendt geen gegevens naar dit werkboek.

1. Geef een voorvertoning van het blad weer in het zijpaneel.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u het `incoming` blad voor het eerst.

1. Verzend het verzoek van de POST om de aangewezen kopballen in te produceren `incoming` en voegt de `shared-default` bladen naar het spreadsheet, als dit nog niet het geval is.

   Als u wilt weten hoe u de aanvraag van de POST voor het instellen van uw werkblad opmaakt, raadpleegt u de [Admin API-documentatie](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). U kunt het onderstaande voorbeeld bekijken:

   **Verzoek**

   ```JSON
   POST 'https://admin.hlx.page/form/{owner}/{repo}/{branch}/contact-us.json' \
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


   **Antwoord**

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

   U kunt gereedschappen zoals curl of Postman gebruiken om dit verzoek voor POSTEN uit te voeren, zoals hieronder wordt getoond:

   ```JSON
   curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

   Het bovenstaande verzoek om POST bevat voorbeeldgegevens, waaronder zowel formuliervelden als de bijbehorende samplewaarden. Deze gegevens worden door de beheerservice gebruikt om het formulier in te stellen.

   Uw formulier is nu ingeschakeld voor het accepteren van gegevens. U ziet ook de volgende wijzigingen in uw spreadsheet:

## Automatische wijzigingen in blad als dit is ingeschakeld voor het accepteren van gegevens.

Wanneer het werkblad is ingesteld op het ontvangen van gegevens, ziet u de volgende wijzigingen in het werkblad:

Er wordt een blad met de naam &quot;Slack&quot; toegevoegd aan uw Excel-werkboek of Google-werkblad. In dit blad, kunt u automatische berichten voor een aangewezen kanaal van de Slack vormen wanneer de nieuwe gegevens in uw spreadsheet worden opgenomen. Momenteel steunt AEM berichten uitsluitend aan de organisatie van de Slack van de Techniek van de AEM en de organisatie van de Steun van de Onderneming van de Adobe.

1. Als u meldingen voor Slacks wilt instellen, voert u &#39;teamId&#39; van de werkruimte van de Slack en &#39;kanaalnaam&#39; of &#39;ID&#39; in. U kunt ook de slack-bot (met de foutopsporingsopdracht) vragen naar &quot;teamId&quot; en &quot;channel ID&quot;. Het verdient de voorkeur de kanaalid te gebruiken in plaats van de kanaalnaam, omdat deze de kanaalnamen behoudt.

   >[!NOTE]
   >
   > Oudere formulieren hadden niet de kolom &quot;teamId&quot;. &quot;teamId&quot; is opgenomen in de kanaalkolom, gescheiden door &quot;#&quot; of &quot;/&quot;.

1. Voer een gewenste titel in en typ onder velden de namen van de velden die u wilt weergeven in het bericht Slack. Elke kop moet worden gescheiden door een komma (bijvoorbeeld naam, e-mail).

   >[!WARNING]
   >
   >  De &quot;gedeelde-standaard&quot;bladen moeten nooit om het even welke persoonlijk identificeerbare informatie of gevoelige gegevens bevatten die u niet aan openbaar toegankelijk bent.


## Gegevens naar uw werkblad verzenden {#send-data-to-your-sheet}

Nadat het blad is ingesteld om gegevens te ontvangen, kunt u [Een voorbeeld van het formulier weergeven met Adaptief Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) of [Admin API&#39;s gebruiken](#use-admin-apis-to-send-data-to-your-sheet) om gegevens naar het blad te verzenden.

### Admin API&#39;s gebruiken om gegevens naar uw werkblad te verzenden

U kunt verzoeken om POST rechtstreeks naar het formulier verzenden met hlx.page, hlx.live of uw productiedomein, om gegevens te verzenden.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> De URL mag niet de extensie .json hebben. U moet het blad publiceren om de verrichtingen van de POST te laten functioneren `.live` of op het productiegebied.

#### De formuliergegevens opmaken

Er zijn een paar verschillende manieren waarop u de formuliergegevens in de hoofdtekst van de POST kunt opmaken. U kunt het volgende gebruiken:

* array van `name:value` paren:

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

  Bijvoorbeeld

  ```JSON
  curl -s -i -X POST 'https://main--portal--wkndforms.hlx.page/contact-us' \
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



* een object met `key:value` paren:

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

  Bijvoorbeeld:

  ```JSON
  curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

* URL gecodeerd (`x-www-form-urlencoded`) lichaam (met `content-type` header ingesteld op `application/x-www-form-urlencoded`)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  Bijvoorbeeld:

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

Vervolgens kunt u [het bedankje aanpassen](/help/edge/docs/forms/thank-you-page-form.md).

## Zie ook

{{see-more-forms-eds}}
