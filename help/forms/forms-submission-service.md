---
Title: How to use forms submission service for submitting forms?
Description: Learn how to use forms submission service for submitting forms.
Keywords: Use form submission service, Submit form using form submission service
feature: Edge Delivery Services
Role: User, Developer
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 67416999d068af6350748d610e7c1c7b1d991bc4
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 0%

---

# Forms-verzendservice met Edge Delivery Services Forms

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail met uw GitHub organisatienaam en bewaarplaatsnaam van uw officieel adres aan <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a>. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>

Met de Forms-verzendservice kunt u gegevens uit de formulierverzendingen opslaan in elk spreadsheet, zoals OneDrive, SharePoint of Google Sheets, zodat u eenvoudig toegang hebt tot formuliergegevens en deze kunt beheren binnen het spreadsheetplatform van uw voorkeur.

![ de voorleggingsdienst van Forms ](/help/forms/assets/form-submission-service.png)

## Voordelen om de Forms-verzendservice te gebruiken

Een paar voordelen van het gebruik van de Forms-verzendservice met spreadsheets zijn:

* **Directe integratie**: U kunt vormen om gegevens aan een gespecificeerde spreadsheet direct voor te leggen, eliminerend de behoefte aan handgegevensoverdracht.
* **de structuur van Gegevens**: Wanneer vestiging de voorlegging, kunt u vormgebieden aan overeenkomstige spreadsheetkolommen voor georganiseerde gegevensopslag in kaart brengen.
* **controle van de Toegang**: U kunt hefboomwerking bestaande toestemmingen controleren wie tot voorgelegde vormgegevens, afhankelijk van de gekozen spreadsheetdienst toegang heeft en kan wijzigen.

## Voorwaarden

Hieronder staan de voorwaarden voor het gebruik van de Forms-verzendservice:

* Zorg ervoor dat uw AEM-project beschikt over het nieuwste adaptieve formulierblok.
* Zorg ervoor dat uw Git-opslagplaats aan de lijst van gewenste personen wordt toegevoegd om de Forms-verzendservice te gebruiken. Gelieve te [ mailto:aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) met uw Naam van de Organisatie GitHub en Naam van de Bewaarplaats om hen te hebben toegevoegd aan de lijst van gewenste personen voor het gebruiken van de dienst van de Verzending van Forms.

## Forms-verzendservice configureren

Maak een nieuw AEM-project dat is geconfigureerd met het Adaptive Forms Block. Verwijs naar het [ Begonnen Worden - het artikel van het Leerprogramma van de Ontwikkelaar ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial) om te leren hoe te om een nieuw project van AEM tot stand te brengen. Werk het `fstab.yaml` dossier in uw project bij. Vervang de bestaande verwijzing door het pad naar de map die u met de `forms@adobe.com` hebt gedeeld.

U kunt [ de Dienst van de Verzending van Forms manueel vormen ](#configuring-the-forms-submission-service-manually) of [ vormen de Dienst van de Verzending van Forms gebruikend API ](#configuring-the-forms-submission-service-using-api).

### De Forms-verzendservice handmatig configureren

![ Werkschema voor de dienst van de vormenvoorlegging ](/help/forms/assets/forms-submission-service-workflow.png)

#### &#x200B;1. Een formulier maken met behulp van een formulierdefinitie

Maak een formulier met Google Sheets of Microsoft Excel. Leren hoe te om een vorm tot stand te brengen gebruikend een vormdefinitie in Microsoft Excel of de Bladen van Google, [ klik hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms).

In de onderstaande schermafbeelding wordt de formulierdefinitie weergegeven die wordt gebruikt om het formulier te maken:

![ de Definitie van de Vorm ](/help/forms/assets/form-submission-definition.png)

>[!IMPORTANT]
>
>**het blad waar de vorm wordt authored heeft beperkingen op wat het kan worden genoemd. Alleen `helix-default` en `shared-aem` kunnen als bladnamen worden gebruikt.**

#### &#x200B;2. Schakel het werkblad in om gegevens te accepteren.

Nadat u het formulier hebt gemaakt en een voorbeeld hebt bekeken, schakelt u het bijbehorende werkblad in om gegevens te ontvangen. voeg een nieuw blad toe als `incoming` . U kunt [ manueel toelaten spreadsheet om gegevens ](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/submit-forms#manually-enable-the-spreadsheet-to-accept-data) goed te keuren.

![ Binnenkomend blad ](/help/forms/assets/form-submission-incoming-sheet.png)

>[!WARNING]
>
> Als het `incoming` sheet niet bestaat, zou AEM geen gegevens naar dit werkboek verzenden.

#### &#x200B;3. Deel het werkblad en genereer een koppeling.

Voer de volgende stappen uit om het werkblad te delen met de `forms@adobe.com` -account en een koppeling te genereren:

1. In Excel of de Bladen van Google, klik de **knoop van het Aandeel** op de hoogste juiste hoek.
1. Voeg de `forms@adobe.com` -account toe en
Klik het oogpictogram, uitgezocht **geef** toegang uit, en klik **verzend**.

   ![ Aankomend blad van het Aandeel ](/help/forms/assets/form-submission-share-incoming.png)

1. Om de spreadsheetverbinding te kopiëren, klik de **knoop van het Aandeel** op de hoogste juiste hoek en selecteer **Verbinding van het Exemplaar**.

   ![ verbinding van het Exemplaar van inkomend blad ](/help/forms/assets/form-submission-copy-link.png)

#### &#x200B;4. Koppel het werkblad aan de formulierdefinitie

Voer de volgende stappen uit om de Forms-verzendservice te configureren met de Google Sheets of Microsoft Excel:

1. Open het werkblad met de formulierdefinitie.
1. In de rij die aan het **beantwoordt leg** gebied voor, kleef de gekopieerde spreadsheetverbinding in de **3&rbrace; kolom van de Actie &lbrace;.**

   ![ Verbinding een spreadsheet ](/help/forms/assets/form-submission-sheet-linking.png)

1. De voorproef en publiceert het blad gebruikend [ AEM Sidekick ](https://www.aem.live/docs/sidekick) met de bijgewerkte dienst van de Verzending van de Vorm.

>[!NOTE]
>
> U kunt naar [ spreadsheet ](/help/forms/assets/spreadsheet.xlsx) verwijzen om de dienst van de Verzending van Forms te gebruiken.

### De Forms-verzendservice configureren met behulp van API

U kunt a **POST** verzoek aan de vorm ook verzenden om het `incoming` blad met gegevens bij te werken.

>[!NOTE]
>
> * Als het `incoming` sheet niet bestaat, zou AEM geen gegevens naar dit werkboek verzenden.
> * Deel het `incoming` -werkblad met de Adobe Experience Manager `forms@adobe.com` en geef de bewerkingstoegang.
> * Bekijk een voorvertoning van het `incoming` -werkblad en publiceer het in het zijpaneel.

Om te begrijpen hoe te om het POST- verzoek voor vestiging uw blad te formatteren, verwijs naar de [ API documentatie ](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/). U kunt het onderstaande voorbeeld bekijken:

U kunt gereedschappen zoals curl of Postman gebruiken om dit POST-verzoek uit te voeren, zoals hieronder wordt getoond.

* **Gebruikend Postman**:

Verzend bijvoorbeeld de onderstaande aanvraag in Postman nadat u deze hebt vervangen:
* `{id}` met uw formulier-id
* `site or repository` met uw GitHub-opslagplaats of sitenaam
* `organization` met uw GitHub-gebruikersnaam

  ```json
  POST 'https://forms.adobe.com/adobe/forms/af/submit/{id}' \
  --header 'Content-Type: application/json' \
  --header 'x-adobe-routing: tier=live,bucket=main--[site/repository]--[organization]' \
  --data '{
      "data": {
          "startDate": "2025-01-10",
          "endDate": "2025-01-25",
          "destination": "Australia",
          "class": "First Class",
          "budget": "2000",
          "amount": "1000000",
          "name": "Mary",
          "age": "35",
          "subscribe": null,
          "email": "mary@gmail.com"
              }
          }'
  ```

Het klikken **verzendt** knoop in Postman keert een `201 Created` reactie terug, en de `incoming` bladupdates met de voorgelegde gegevens.

![ postmanscherm ](/help/forms/assets/postman-api.png)

* **Gebruikend bevel van de Kromme**:

Voer bijvoorbeeld de onderstaande opdracht uit in terminal- of opdrachtprompt na het vervangen:
* `{id}` met uw formulier-id
* `site or repository` met uw GitHub-opslagplaats of sitenaam
* `organization` met uw GitHub-gebruikersnaam


>[!BEGINTABS]

>[!TAB  voor macOS ]

     &quot;json 
     krullen - X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/ {id}&quot; \ 
     &#x200B;- kopbal &quot;Content-Type: application/json&quot; \ 
     &#x200B;- kopbal &quot;x-adobe-routing: tier=live, bucket=main—[plaats/bewaarplaats]&quot; \ 
     &#x200B;- gegevens &quot;
     &quot;data&quot;: 
     &quot;startDate&quot;: &quot;20 25-01-10&quot;, 
     &quot;endDate&quot;: &quot;2025-01-25&quot;, 
     &quot;bestemming&quot;: &quot;Australië&quot;, 
     &quot;klasse&quot;: &quot;First Class&quot;, 
     &quot;budget&quot;: &quot;2000&quot;, 
     &quot;bedrag&quot;: &quot;100 0000&quot;, 
     &quot;naam&quot;: &quot;Joe&quot;, 
     &quot;leeftijd&quot;: &quot;35&quot;, 
     &quot;onderteken&quot;: ongeldig, 
     &quot;e-mail&quot;: &quot;mary@gmail.com&quot;
     
     &quot;
    
    &quot;

>[!TAB  voor OS van Vensters ]

     &quot;json 
    
     krullen - X POST &quot;https://forms.adobe.com/adobe/forms/af/submit/ {id}&quot;&quot;
     &#x200B;- kopbal &quot;Content-Type: application/json&quot; ^
     &#x200B;- kopbal &quot;x-adobe-routing: tier=live, bucket=main—[site/gegevensopslagplaats]&quot;&quot;
     &#x200B;- gegevens &quot;&lbrace;\&quot;data\&quot;: {\&quot;startDate\&quot;: \&quot;202 5-01-10\&quot;, \&quot;endDate\&quot;: \&quot;2025-01-25\&quot;, \&quot;destination\&quot;: \&quot;Australia\&quot;, \&quot;class\&quot;: \&quot;First Class\&quot;, \&quot;budget\&quot;: \&quot;2000\&quot;, \&quot;bedrag\&quot;: \&quot;1000 000\&quot;, \&quot;name\&quot;: \&quot;Joe\&quot;, \&quot;age\&quot;: \&quot;35\&quot;, \&quot;subscribe\&quot;: null, \&quot;email\&quot;: \&quot;mary@gmail.com\&quot;}&quot;
    
    &quot;

>[!ENDTABS]

Met de bovenstaande POST-aanvraag wordt het `incoming` -blad bijgewerkt met het volgende antwoord:

```json
    < HTTP/1.1 201 Created
    < Connection: keep-alive
    < Content-Length: 0
    < X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
    < X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
    < Accept-Ranges: bytes
    < Date: Fri, 10 Jan 2025 13:06:10 GMT
    < Via: 1.1 varnish
    < Access-Control-Allow-Origin: *
    < X-Served-By: cache-del21750-DEL
    < X-Cache: MISS
    < X-Cache-Hits: 0
    < X-Timer: S1736514370.704084,VS0,VE1234
```

In het onderstaande scherm wordt de schermafbeelding weergegeven van het `incoming` -blad dat is bijgewerkt door de gegevens die via de API worden verzonden:

![ bijgewerkt blad ](/help/forms/assets/updated-sheet.png)

## Zie ook

{{see-more-forms-eds}}