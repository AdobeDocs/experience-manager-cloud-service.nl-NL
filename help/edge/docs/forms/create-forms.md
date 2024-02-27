---
title: Aan de slag met de AEM Forms Edge Delivery Service
description: Creëer snelle perfecte formulieren! ⚡ AEM Forms Edge Delivery doc-based authoring = ultrahoge snelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 78d40574e6fea8dde22414e43fd77215b9e7d2a1
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 0%

---


# Een formulier maken op AEM Forms Edge Delivery Service

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met AEM Forms Edge Delivery&#39;s kunt u formulieren maken met vertrouwde gereedschappen, zoals Word of Google Docs.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft Sharepoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

AEM Forms Edge Delivery biedt een formulierblok waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt het formulierblok opnemen in uw AEM EDS-project om een formulier te maken. Laten we beginnen:


## Vereisten

Controleer voordat u begint of u de volgende stappen hebt uitgevoerd:

* Stel Edge Delivery Service (EDS) Github-project in met AEM boilerplate en kloon de corresponderende Github-opslagplaats op uw lokale computer. Zie [zelfstudie ontwikkelaar](https://www.aem.live/developer/tutorial) voor meer informatie. In dit document wordt de lokale map van het EDS-project (Edge Delivery Service) `[EDS Project repository]` .
* Klonen met [Forms Block-opslagplaats](https://github.com/adobe/afb) op uw lokale computer. Het bevat de code die het formulier op een EDS-webpagina moet weergeven. In dit document wordt de lokale map van de Forms Block-opslagplaats aangeduid als `[Forms Block repository]`.
* Zorg ervoor dat u toegang hebt tot Google Sheets of Microsoft SharePoint. Als u Microsoft SharePoint wilt instellen als inhoudsbron, raadpleegt u [Hoe te om SharePoint te gebruiken](https://www.aem.live/docs/setup-customer-sharepoint)



## Een formulier maken

+++ Stap 1: Voeg het blok van de Vorm aan uw project van de Dienst van de Levering van de Rand (EDS) toe.

De `Form block` bevat de mogelijkheid om een formulier aan een EDS-site toe te voegen. Het blok is niet inbegrepen in een project dat gebruikend AEM boilerplate wordt gecreeerd. Om het blok van de Vorm aan uw project van de Dienst van de Levering van de Rand op te nemen:

1. Ga naar de `[Forms Block repository]/blocks` op uw lokale computer en kopieer de `form` map.

1. Ga naar de `[EDS Project repository]/blocks/` op uw lokale computer en plak de `form` map.

1. Inchecken `form` omslag en onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub.

   Het blok van de Vorm wordt toegevoegd aan uw EDS projectbewaarplaats op GitHub. Zorg ervoor dat de bouw GitHub niet ontbreekt:

   * Als er een fout optreedt &quot;Kan pad naar module &quot;&#39;../../scripts/lib-franklin.js&#39;&#39; niet omzetten, opent u het dialoogvenster `[EDS Project]/blocks/forms/form.js` bestand. Vervang in de importinstructie de opdracht `lib-franklin.js` met de `aem.js` bestand.

   * Als u fouten met de koppeling tegenkomt, kunt u deze vrij negeren. Als u de controles wilt omzeilen, opent u het dialoogvenster `[EDS Project]\package.json` bestand en werk het &quot;lint&quot;-script bij `"lint": "npm run lint:js && npm run lint:css"` tot `"lint": "echo 'skipping linting for now'"`. Sparen het dossier en begaat het aan uw project GitHub.

U kunt nu een formulier maken en dit toevoegen aan uw site.

+++

+++ Stap 2: Een formulier ontwerpen met Microsoft Excel of Google Sheet.

In plaats van complexe processen kunt u eenvoudig een formulier maken met behulp van een spreadsheet. U begint door de rijen en kolomkoppen toe te voegen aan een spreadsheet, waar elke rij een formulierveld definieert en elke kolomkop de eigenschappen van de overeenkomstige formuliervelden definieert.

In het volgende werkblad definiëren rijen bijvoorbeeld de velden voor een `contact us` formulier- en kolomkoppen definiëren de eigenschappen van de corresponderende velden.

![contact opnemen met ons spreadsheet](/help/edge/assets/contact-us-form-spreadsheet.png)

Een formulier maken:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Drive.

1. Maak een Microsoft Excel-werkboek of Google-werkblad onder de projectmap AEM Edge Delivery. Maak bijvoorbeeld een werkblad met de naam `contact-us` op AEM Edge Delivery-projectdirectory op Google Drive.

1. Controleer of het blad wordt gedeeld met AEM gebruiker (bijvoorbeeld `helix@adobe.com`) [geconfigureerd voor uw project](https://www.aem.live/docs/setup-customer-sharepoint) en de gebruiker heeft bewerkingsmachtigingen voor de pagina.

1. Open het werkblad dat u hebt gemaakt en wijzig de naam van het standaardwerkblad in &#39;shared-default&#39;.

   ![naam standaardblad wijzigen in &#39;shared-default&#39;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Als u de velden van het formulier wilt toevoegen, voegt u de rijen en kolomkoppen toe aan de `shared-default` blad, waarbij elke rij een formulierveld definieert en elke kolomkop de [eigenschappen](/help/edge/docs/forms/eds-form-field-properties)) van de desbetreffende formuliervelden.

   Als u snel wilt beginnen, kunt u de inhoud van het dialoogvenster [contact opnemen met ons spreadsheet](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link) naar uw spreadsheet.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)

1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven en het te publiceren.

   ![AEM Sidekick gebruiken om een voorvertoning van het blad weer te geven en het blad te publiceren](/help/edge/assets/preview-form.png)

   Bij voorvertonen en publiceren opent de browser nieuwe tabbladen waarin de inhoud van het blad in JSON-indeling wordt weergegeven. Let op de live URL omdat dit nodig is voor weergave van het formulier op een later tijdstip.

   De opmaak van de URL is:

   ```JSON
   https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   
   For example, https://main--portal--wkndforms.hlx.live/contact-us.json
   ```

+++

+++ Stap 3: Geef een voorbeeld van het formulier weer met de pagina Edge Delivery Service (EDS).


Tot nu toe hebt u het formulierblok aan uw EDS-project toegevoegd en de structuur van het formulier voorbereid. Nu een voorbeeld van het formulier weergeven:

1. Ga naar uw Microsoft SharePoint- of Google Drive-account en open uw AEM Edge Delivery-projectdirectory.

1. Open een documentbestand om het formulier in te sluiten. Open bijvoorbeeld het indexbestand. U kunt ook een nieuw documentbestand maken.

1. Navigeer naar de gewenste locatie in het document waar u het formulier wilt toevoegen.

1. Voeg een blok met de naam &#39;Formulier&#39; toe aan het bestand, vergelijkbaar met het blok hieronder.

   ![](/help/edge/assets/form-block-in-sites-page-example.png)

   Neem in de tweede rij de URL op die u in de vorige sectie als hyperlink hebt opgenomen. Gebruik de URL van de voorvertoning (.page URL) voor ontwikkelings- of testdoeleinden of de URL van de publicatie (.live) voor productiedoeleinden.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL een hyperlink heeft en niet wordt weergegeven als onbewerkte tekst.


1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om de pagina voor te vertonen. Het formulier wordt nu weergegeven op de pagina.

   Hier ziet u bijvoorbeeld het formulier dat is gebaseerd op de [contact opnemen met ons spreadsheet](https://docs.google.com/spreadsheets/d/12jvYjo1a3GOV30IqPY6_7YaCQtUmzWpFhoiOHDcjB28/edit?usp=drive_link):


   ![Een voorbeeld-EDS-formulier](/help/edge/assets/eds-form.png)

   Vul nu het formulier in en klik op de knop Verzenden. Er treedt een fout op, die lijkt op het volgende, omdat het werkblad nog niet is ingesteld op het accepteren van de gegevens.

   ![fout bij het verzenden van formulier](/help/edge/assets/form-error.png)

+++


## Volgende stap

[Werkblad voorbereiden](/help/edge/docs/forms/submit-forms.md) om gegevens te accepteren bij het verzenden van het formulier.



## Meer weergeven

* [Eigenschappen van formulierveld](/help/edge/docs/forms/eds-form-field-properties)
* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-eds-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)
