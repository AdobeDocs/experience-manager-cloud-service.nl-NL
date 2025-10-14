---
title: De spreadsheet voorbereiden voor het accepteren van gegevens
description: Krachtige formulieren sneller maken met spreadsheets en Adaptieve Forms Block Fields!
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Google-bladen of Microsoft Excel-bestanden instellen om gegevens te accepteren


Zodra u [&#x200B; hebt gecreeerd en de vorm &#x200B;](/help/edge/docs/forms/create-forms.md) previewde, is het tijd om het overeenkomstige spreadsheet toe te laten beginnen gegevens te ontvangen. U kunt

- [&#x200B; laat manueel spreadsheet toe om gegevens &#x200B;](#manually-enable-the-spreadsheet-to-accept-data) goed te keuren
- [Admin API&#39;s gebruiken om een spreadsheet in te schakelen voor het accepteren van gegevens](#use-admin-apis-to-enable-a-spreadsheet-to-accept-data)

![&#x200B; op document-gebaseerde het Authoring ecosysteem &#x200B;](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)


<!--

>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

## De spreadsheet handmatig inschakelen voor het accepteren van gegevens

De spreadsheet inschakelen om gegevens te accepteren

1. Open het werkblad met het formulier en voeg een nieuw blad toe, onder een andere naam `incoming` . Bijvoorbeeld, het [&#x200B; vraag &#x200B;](/help/edge/assets/enquiry.xlsx) van het werkboek van Microsoft Excel.

   >[!WARNING]
   >
   > Als het `incoming` sheet niet aanwezig is, verzendt AEM geen gegevens naar het spreadsheet.

1. Voeg op dit blad een tabel in met de naam &quot;take_form&quot;. Selecteer het aantal kolommen dat nodig is om overeen te komen met de namen van de formuliervelden. Ga vervolgens op de werkbalk naar Invoegen > Tabel en klik op OK.

1. Wijzig de naam van de tabel in &quot;take_form&quot;. Als u in Microsoft Excel de naam van de tabel wilt wijzigen, selecteert u de tabel en klikt u op Tabelontwerp.

1. Voeg vervolgens de namen van de formuliervelden toe als de tabelkoppen. Om ervoor te zorgen dat de velden exact hetzelfde zijn, kunt u deze kopiëren en plakken vanaf het &quot;shared-name&quot; blad.  Selecteer en kopieer de formulier-id&#39;s die onder de kolom &quot;Naam&quot; staan, behalve het veld Verzenden.

1. Selecteer Plakken speciaal > Rijen omzetten in kolommen op het blad &#39;inkomend&#39; om de veld-id&#39;s als kolomkoppen op dit nieuwe blad te kopiëren. Alleen velden behouden waarvan de gegevens andere gegevens moeten vastleggen, kunnen worden genegeerd.

   Elke waarde in de kolom `Name` van het `shared-aem` -blad, met uitzondering van de verzendknop, kan fungeren als koptekst in het `incoming` -blad. Neem bijvoorbeeld de volgende afbeelding die kopteksten illustreert voor een &quot;vraag&quot;-formulier:

   ![&#x200B; Gebieden voor een contact-usvorm &#x200B;](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Gebruik de [&#x200B; uitbreiding van AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) aan voorproef de vormupdates. Uw blad is nu klaar om inkomende formulierverzendingen te accepteren.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u het `incoming` -blad voor het eerst hebt gemaakt.


Nadat de veldnamen aan het `incoming` -werkblad zijn toegevoegd, kan het formulier opmerkingen accepteren. U kunt een voorbeeld van het formulier bekijken en gegevens naar het blad verzenden.

Zodra het blad opstelling is om gegevens te ontvangen, kunt u [&#x200B; voorproef de vorm &#x200B;](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> beginnen gegevens naar het blad te verzenden.

>[!WARNING]
>
>  De bladen &quot;shared-name&quot; mogen nooit persoonlijke identificeerbare informatie of gevoelige gegevens bevatten die u niet prettig vindt om openbaar toegankelijk te zijn.


## Admin API&#39;s gebruiken om een spreadsheet in te schakelen voor het accepteren van gegevens

U kunt ook een POST-aanvraag naar het formulier verzenden, zodat deze gegevens kan accepteren en kopteksten voor het `incoming` -blad kan configureren. Na ontvangst van het POST-verzoek analyseert de service de inhoud van het verzoek en genereert de service autonoom de essentiële koppen en bladen die nodig zijn voor het invoeren van gegevens.

Admin APIs gebruiken om een spreadsheet toe te laten om gegevens goed te keuren:


1. Open het werkboek dat u hebt gecreeerd en verander de naam van het standaardblad in `incoming`.

   >[!WARNING]
   >
   > Als het `incoming` sheet niet bestaat, zal AEM geen gegevens naar dit werkboek verzenden.

1. Geef een voorvertoning van het blad weer in het zijpaneel.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u het `incoming` -blad voor het eerst hebt gemaakt.

1. Verzend de POST-aanvraag om de juiste kopteksten op het `incoming` -blad te genereren en voeg de `shared-default` -bladen toe aan uw spreadsheet, als dit nog niet het geval is.

   Om te begrijpen hoe te om het POST- verzoek voor vestiging uw blad te formatteren, verwijs naar de [&#x200B; Admin API documentatie &#x200B;](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). U kunt het onderstaande voorbeeld bekijken:

   **Verzoek**

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


   **Reactie**

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

   U kunt gereedschappen zoals curl of Postman gebruiken om dit POST-verzoek uit te voeren, zoals hieronder wordt getoond:

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

   Het bovenstaande POST-verzoek bevat voorbeeldgegevens, waaronder zowel formuliervelden als de bijbehorende samplewaarden. Deze gegevens worden door de beheerservice gebruikt om het formulier in te stellen.

   Uw formulier is nu ingeschakeld voor het accepteren van gegevens. U ziet ook de volgende wijzigingen in uw spreadsheet:

## Automatische wijzigingen in blad als deze zijn ingeschakeld voor het accepteren van gegevens.

Wanneer het werkblad is ingesteld op het ontvangen van gegevens, ziet u de volgende wijzigingen in het werkblad:

Er wordt een blad met de naam &quot;Slack&quot; toegevoegd aan uw Excel-werkboek of Google-werkblad. In dit blad kunt u automatische meldingen voor een bepaald Slack-kanaal configureren wanneer nieuwe gegevens in uw spreadsheet worden opgenomen. Momenteel ondersteunt AEM uitsluitend meldingen aan de AEM Engineering Slack-organisatie en de Adobe Enterprise Support-organisatie.

1. Als u Slack-berichten wilt instellen, voert u &#39;teamId&#39; van de Slack-werkruimte en de &#39;kanaalnaam&#39; of &#39;ID&#39; in. U kunt ook de slack-bot (met de foutopsporingsopdracht) vragen naar &quot;teamId&quot; en &quot;channel ID&quot;. Het verdient de voorkeur de kanaalid te gebruiken in plaats van de kanaalnaam, omdat deze de kanaalnamen behoudt.

   >[!NOTE]
   >
   > Oudere formulieren hadden niet de kolom &quot;teamId&quot;. &quot;teamId&quot; is opgenomen in de kanaalkolom, gescheiden door &quot;#&quot; of &quot;/&quot;.

1. Voer een gewenste titel in en typ onder velden de namen van de velden die u wilt weergeven in het Slack-bericht. Elke kop moet worden gescheiden door een komma (bijvoorbeeld naam, e-mail).

   >[!WARNING]
   >
   >  De &quot;gedeelde-standaard&quot;bladen moeten nooit om het even welke persoonlijk identificeerbare informatie of gevoelige gegevens bevatten die u niet aan openbaar toegankelijk bent.



Daarna, kunt u [&#x200B; aanpassen dankt u bericht &#x200B;](/help/edge/docs/forms/thank-you-page-form.md).

