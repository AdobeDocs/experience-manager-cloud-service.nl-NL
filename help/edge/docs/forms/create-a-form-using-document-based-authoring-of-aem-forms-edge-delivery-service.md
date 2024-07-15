---
title: Een formulier maken met op documenten gebaseerde ontwerpen voor AEM Forms Edge Delivery Service
description: Creëer snelle perfecte formulieren! ⚡ AEM Forms Edge Delivery + documentgebaseerde authoring = ultrahoge snelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---


# Een formulier maken met op documenten gebaseerde ontwerpen voor AEM Forms Edge Delivery Service

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. In AEM Forms Edge Delivery kunt u op documenten gebaseerde ontwerpen maken met behulp van vertrouwde gereedschappen, zoals Word of Google Docs. Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google-bladbestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft Sharepoint kunt gebruiken om ingediende gegevens gemakkelijk te verwerken of een bestaande bedrijfsworkflow te starten.

Deze gids begeleidt u door:

* Prepping your spreadsheet: Learn how to set an Excel or Google Sheets file for data collection and add form fields to it.
* Gegevens naar uw werkblad verzenden: leer hoe u gegevens naar uw werkblad kunt verzenden aan de hand van verzoeken van POSTEN.
* Het formulier publiceren: Integreer uw formulier op uw AEM Sites-pagina of publiceer het als een zelfstandige pagina.

Of je nu een beginner of een pro bent, deze gids geeft je de mogelijkheid om prachtige, functionele vormen te bouwen waar gebruikers van houden. Laten we efficiënte formulierontwerpen ontgrendelen - duik nu in!

## Voordat u begint

`WIP`

## De spreadsheet voorbereiden voor het ontvangen van gegevens

1. Maak een Microsoft Excel-werkboek of Google-werkblad onder uw AEM Edge Delivery-projectmap op Microsoft OneDrive of Google Drive. In dit document wordt een Google-werkblad met de naam `contact-us.xlsx` gebruikt, dat zich bevindt in de hoofdmap van een Adobe Experience Manager-project (AEM).

1. Zorg ervoor dat de AEM gebruiker (bijvoorbeeld helix@adobe.com) die voor uw project is geconfigureerd, bewerkingsmachtigingen voor het werkblad heeft.

1. Open het werkboek dat u hebt gecreeerd en verander de naam van het standaardblad in &quot;inkomend&quot;.

   >[!NOTE]
   >
   > Als het &quot;inkomende&quot;blad niet bestaat, zal AEM geen gegevens naar dit werkboek verzenden.

1. Geef een voorvertoning van het blad weer in het zijpaneel.

   >[!NOTE]
   >
   >Zelfs als u al eerder een voorvertoning van het blad hebt weergegeven, moet u dit opnieuw bekijken nadat u voor het eerst het &#39;binnenkomende&#39; blad hebt gemaakt.

1. Bereid het blad door kopballen toe te voegen die de gegevens aanpassen u in zet. In het volgende voorbeeld worden velden voor een formulier &quot;contact-us&quot; weergegeven:

   ![ Gebieden voor een contact-usvorm ](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   U kunt dit handmatig doen of door een aanvraag van een POST in te dienen op de formulierroute in de AEM Admin-service. De admindienst zal de gegevens in het lichaam van de POST onderzoeken en zal de aangewezen kopballen, lijsten, en bladen produceren nodig om gegevens effectief in te voeren en de optimaal van de vormdienst te maken.

   Om te begrijpen hoe te om het verzoek van de POST voor vestiging uw blad te formatteren, verwijs naar de [ Admin API documentatie ](https://www.hlx.live/docs/admin.html#tag/form). Kijk ook naar het onderstaande voorbeeld:

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
   
   {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country","PreferredContactMethod","SubscribeToNewsletter"]}%
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

Terwijl de dienst Admin adviseerde om uw blad te vormen, als u verkiest om de kopballen manueel tot stand te brengen, verwijs naar het document genoemd [ Handmatige Opstelling van het Blad van Forms ](https://www.hlx.live/docs/manual-forms-sheet-setup).

Op het voorleggen van het verzoek van de POST aan de admin dienst, zult u de volgende veranderingen in uw werkboek waarnemen:

* Er wordt een nieuw blad met de naam &quot;shared-default&quot; toegevoegd aan uw Excel-werkboek of Google-werkblad. De gegevens in het &quot;gedeelde-gebrek&quot;blad worden teruggewonnen wanneer het maken van een verzoek van de GET aan het blad. Dit blad fungeert als een optimale locatie voor het gebruik van spreadsheetformules om de binnenkomende gegevens samen te vatten, waardoor het geschikt is voor consumptie in andere contexten.

  In geen geval mag het &quot;standaard-gedeelde&quot; blad persoonlijke identificeerbare informatie of gevoelige gegevens bevatten die u niet gemakkelijk kunt gebruiken om openbaar toegankelijk te zijn.

* Er wordt een blad met de naam &quot;slack&quot; toegevoegd aan uw Excel-werkboek of Google-werkblad. In dit blad, kunt u automatische berichten voor een aangewezen kanaal van de Slack vormen wanneer de nieuwe gegevens in uw spreadsheet worden opgenomen. Momenteel steunt AEM berichten uitsluitend aan de organisatie van de Slack van de Techniek van de AEM en de organisatie van de Steun van de Onderneming van de Adobe.

   1. Als u meldingen voor Slacks wilt instellen, voert u &quot;teamId&quot; van de werkruimte van de Slack en de &quot;kanaalnaam&quot; of &quot;ID&quot; in. U kunt ook de slack-bot (met de foutopsporingsopdracht) vragen naar &quot;teamId&quot; en &quot;channel ID&quot;. Het verdient de voorkeur de kanaalid te gebruiken in plaats van de kanaalnaam, omdat deze de kanaalnamen behoudt.

      >[!NOTE]
      >
      > Oudere formulieren hadden niet de kolom &quot;teamId&quot;. &quot;teamId&quot; is opgenomen in de kanaalkolom, gescheiden door &quot;#&quot; of &quot;/&quot;.

   1. Voer een gewenste titel in en typ onder velden de namen van de velden die u wilt weergeven in het bericht Slack. Elke kop moet worden gescheiden door een komma (bijvoorbeeld naam, e-mail).

Het blad is nu ingesteld op het ontvangen van gegevens en u kunt aanvragen voor POSTEN rechtstreeks naar het bestand verzenden met hlx.page, hlx.live of uw productiedomein.


## Gegevens naar uw werkblad verzenden {#send-data-to-your-sheet}

Nadat het blad wordt geplaatst om gegevens te ontvangen, kunt u verzoeken van de POST rechtstreeks naar het verzenden gebruikend hlx.page, hlx.live, of uw productiedomein, om gegevens te verzenden.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> De URL mag niet de extensie .json hebben. U moet het blad voor de verrichtingen van de POST publiceren om op .live of op het productiedomein te functioneren.

### Gegevens voor EDS Forms opmaken

Er zijn een aantal verschillende manieren waarop u de formuliergegevens in de hoofdtekst van de POST kunt opmaken.

* Array van naam:waardeparen:

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
              { "name": "message", "value": "I have some questions about your products." },
              { "name": "phone", "value": "123-456-7890" },
              { "name": "company", "value": "Example Inc." },
              { "name": "country", "value": "United States" },
              { "name": "preferred_contact_method", "value": "Email" },
              { "name": "newsletter_subscribe", "value": true }
              ]
          }'
  
* Object met sleutel:waardeparen

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

* `x-www-form-urlencoded` body (`content-type` header must be set to `application/x-www-form-urlencoded` )
&#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



