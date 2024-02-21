---
title: Aan de slag met de AEM Forms Edge Delivery Service
description: Creëer snelle perfecte formulieren! ⚡ AEM Forms Edge Delivery doc-based authoring = ultrahoge snelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f37a99cd5cbfb745cb591e3be2a46a5f52139cb2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Een formulier maken op AEM Forms Edge Delivery Service

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met AEM Forms Edge Delivery&#39;s kunt u formulieren maken met vertrouwde gereedschappen, zoals Word of Google Docs.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft Sharepoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

## Vereisten

* Je hebt een Github-account.
* U hebt toegang tot Google Sheets of Microsoft SharePoint.
* U begrijpt de grondbeginselen van Git, HTML, CSS en JavaScript.
* U hebt Node en NPM geïnstalleerd voor lokale ontwikkeling.

## Voordat u begint

* Opstelling en kloon uw project van de Dienst van de Levering van de Rand (EDS). Zie [zelfstudie ontwikkelaar](https://www.aem.live/developer/tutorial) voor meer informatie.
* Klonen met [Forms Block-opslagplaats](https://github.com/adobe/afb). Het bevat het formulierblok dat nodig is om het formulier te genereren.

![Aan de slag met Edge Delivery Forms](/help/edge/assets/getting-started-with-eds-forms.png)

## Voeg het blok van de Vorm aan uw project van de Dienst van de Levering van de Rand (EDS) toe {#add-forms-block-to-an-eds-project}

AEM Forms Edge Delivery bevat een formulierblok waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. Om het blok van de Vorm aan uw project van de Dienst van de Levering van de Rand op te nemen:

1. Navigeer naar de projectmap Edge Delivery Service (EDS) in uw lokale ontwikkelomgeving.


   ```Shell
   cd [EDS Project folder]
   ```

1. Een map maken met de naam `form` onder de EDS-projectdirectory. Bijvoorbeeld, onder de folder voor het EDS- project genoemd `Portal`, maakt u een map met de naam `form`.

   ```Shell
   mkdir form
   ```


1. Voeg de [Forms Block](https://github.com/adobe/afb/tree/main/blocks/form) bestanden naar de map &#39;form&#39;.

   ```shell
   cp -R <source:path of the form block> <destination: path of the form folder created in the previous step>
   
   For example
   
   cp -R Documents/afb/blocks/form Documents/portal/blocks/
   ```

1. Check-in de &quot;vorm&quot;omslag en onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub.

   ```Shell
   git add .
   git commit -m "Added form block"
   git push origin
   ```

   U kunt nu een EDS-formulier genereren.

   >[!NOTE]
   >
   > * Als uw trekkrachtverzoek/project bouwt ontbreekt en u een fout met betrekking tot het invoeren ontmoet `franklin-lib.js` bestand, werk de importinstructie bij om naar de `aem.js` in plaats van het `franklin-lib.js` bestand.
   > * Als u fouten met de koppeling tegenkomt, kunt u deze vrij negeren. Als u de koppelingscontroles wilt omzeilen, navigeert u naar het bestand package.json en werkt u het script &quot;lint&quot; bij vanuit `"lint": "npm run lint:js && npm run lint:css"` tot `"lint": "echo 'skipping linting for now'"`. Wijs vervolgens de wijzigingen toe aan het bestand package.json.

## Een formulier maken met Microsoft Excel of Google Sheet {#create-a-form-for-an-eds-project}

Websiteontwikkelaars toestaan formulieren te maken en te kiezen welke informatie van websitebezoekers kan worden verzameld. In plaats van complexe processen kunnen auteurs eenvoudig een formulier instellen met behulp van een spreadsheet. Ze moeten de juiste kolomkoppen toevoegen en vervolgens een formulierblok gebruiken om het zonder problemen op de website weer te geven. Een formulier maken:

1. Maak overal onder uw AEM Edge Delivery-projectdirectory op Microsoft SharePoint of Google Drive een Microsoft Excel-werkboek of Google-werkblad.

1. Zorg ervoor dat de AEM gebruiker (bijvoorbeeld `helix@adobe.com`) die voor uw project is geconfigureerd, beschikt over bewerkingsmachtigingen voor het werkblad.

1. Open het werkboek dat u hebt gecreeerd en verander de naam van het standaardblad in &quot;gedeeld-gebrek&quot;.

   ![naam standaardblad wijzigen in &#39;shared-default&#39;](/help/edge/assets/rename-sheet-to-helix-default.png)

1. Kopieer de inhoud van het dialoogvenster [contact opnemen met ons spreadsheet](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) naar uw eigen spreadsheet.

   ![contact opnemen met ons spreadsheet](/help/edge/assets/contact-us-form-spreadsheet.png)

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven en het te publiceren.

   Bij voorvertonen en publiceren opent de browser nieuwe tabbladen waarin de inhoud van het blad in JSON-indeling wordt weergegeven. Let op de live URL omdat dit nodig is voor weergave van het formulier op een later tijdstip.

   De opmaak van de URL is:

   ```shell
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

## Geef een voorbeeld van het formulier weer met de pagina Edge Delivery Service (EDS) {#add-a-form-to-your-eds-page}

Tot nu toe hebt u het formulierblok voor uw EDS-project ingeschakeld en de structuur van het formulier voorbereid. Nu kunt u het formulier opnemen op uw EDS-pagina en het weergeven:

1. Ga naar uw AEM Edge Delivery-projectdirectory op Microsoft SharePoint of Google Drive.

1. Als u het formulier aan een pagina wilt toevoegen, opent u het bijbehorende documentbestand. Open bijvoorbeeld het indexbestand.

1. Navigeer naar de gewenste locatie in het document waar u het formulier wilt toevoegen.

1. Voeg een blok met de naam &#39;Formulier&#39; toe aan het bestand, vergelijkbaar met het blok hieronder.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Neem in de tweede rij de URL op die u in de vorige sectie hebt genoteerd, als hyperlink.

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van de pagina weer te geven en deze te publiceren. Het formulier wordt gegenereerd.

   Hier ziet u bijvoorbeeld het formulier dat is gebaseerd op de [contact opnemen met ons spreadsheet](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![contact met ons opnemen (EDS-formulier)](/help/edge/assets/eds-form.png)

   Het formulierblok geeft het formulier weer, maar het is nog niet klaar om de gegevens te accepteren. Als u op de knop Verzenden klikt, wordt een fout weergegeven die lijkt op het volgende:

   ![fout bij het verzenden van formulier](/help/edge/assets/form-error.png)

   [Uw blad voorbereiden op het accepteren van gegevens](/help/edge/docs/forms/submit-forms.md). U kunt de gegevens naar de werkbladen verzenden en deze voorbereiden op het accepteren van gegevens.


## Meer weergeven

* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-eds-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)