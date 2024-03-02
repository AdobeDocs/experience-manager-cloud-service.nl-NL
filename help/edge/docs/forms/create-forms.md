---
title: Aan de slag met de AEM Forms Edge Delivery Service. Maak een formulier.
description: Creëer snelle perfecte formulieren! ⚡ AEM Forms Edge Delivery doc-based authoring = ultrahoge snelheid en SEO-vriendelijke formulieren voor gelukkige gebruikers en zoekmachines.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: d0c4f2f880ef7c11b11144502d30430336ac682e
workflow-type: tm+mt
source-wordcount: '1150'
ht-degree: 0%

---


# Een formulier maken met Adaptief formulierblok

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met AEM Forms Edge Delivery&#39;s kunt u formulieren maken met vertrouwde gereedschappen, zoals Word of Google Docs.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft Sharepoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

![Op documenten gebaseerd ontwerpecosysteem](/help/edge/assets/document-based-authoring-workflow-create-form.png)

AEM Forms Edge Delivery biedt een blok, ook wel Adaptief formulierblok genoemd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt het Adaptief formulierblok opnemen in uw AEM EDS-project om een formulier te maken. Laten we beginnen:


## Vereisten

Controleer voordat u begint of u de volgende stappen hebt uitgevoerd:

* De Dienst van de Levering van de Rand van de opstelling (EDS) GitHub project gebruikend AEM boilerplate en kloon de overeenkomstige bewaarplaats GitHub op uw lokale machine. Zie [zelfstudie ontwikkelaar](https://www.aem.live/developer/tutorial) voor meer informatie. In dit document wordt de lokale map van het EDS-project (Edge Delivery Service) `[EDS Project repository]` .
* Zorg ervoor dat u toegang hebt tot Google Sheets of Microsoft SharePoint. Als u Microsoft SharePoint wilt instellen als inhoudsbron, raadpleegt u [Hoe te om SharePoint te gebruiken](https://www.aem.live/docs/setup-customer-sharepoint)



## Een formulier maken

+++ Stap 1: Voeg het Adaptive Form Block toe aan uw Edge Delivery Service-project (EDS).

Met Adaptief kunnen gebruikers formulieren maken voor een Edge Delivery Service-site. Nochtans, is dit blok niet inbegrepen in het gebrek AEM boilerplate (die wordt gebruikt om een project van de Dienst van de Levering van de Rand tot stand te brengen). Het adaptieve formulierblok naadloos integreren in uw Edge Delivery Service-project:

1. **Klonen in de Adaptive Form Block-opslagplaats**: Kloon de [Adaptief opslagplaats voor formulierblokken](https://github.com/adobe/afb) op uw lokale computer. Het bevat de code die het formulier op een EDS-webpagina moet weergeven. In dit document wordt de lokale map van de Forms Block-opslagplaats aangeduid als `[Adaptive Form Block repository]`.
1. **Zoek de adaptieve opslagplaats voor formulierblokken:** Toegang krijgen tot de [Adaptief opslagplaats voor formulierblokken]/blokmap op uw lokale computer en kopieer de `form` map.
1. **Plak het Adaptief formulierblok in uw EDS-project:**
Ga naar de [EDS-projectopslagplaats]/bloks/ map op uw lokale computer en plak de formuliermap.
1. **Wijzigingen in GitHub vastleggen:** Controle in de vormomslag en zijn onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub.

Na het voltooien van deze stappen, wordt het Adaptieve Blok van de Vorm met succes toegevoegd aan uw het projectbewaarplaats van de Dienst van de Levering van Randen (EDS) op GitHub. U kunt nu formulieren maken en toevoegen aan een pagina EDS-sites.


**Het oplossen van problemen GitHub bouwt kwesties**

Verzeker een vlotte GitHub bouwt proces door potentiële kwesties te richten:

* **Fout in pad van module oplossen:**
Als u de fout &quot;Kan pad naar module &quot;&#39;../../scripts/lib-franklin.js&#39;&#39; niet omzetten, navigeert u naar de [EDS-project]/blocks/forms/form.js. Werk de importinstructie bij door het bestand lib-franklin.js te vervangen door het bestand aem.js.

* **Fouten bij het koppelen van handgrepen:**
Als u tegenkomt met regelfouten, kunt u deze omzeilen. Open de [EDS-project]/package.json en wijzig het script &quot;lint&quot; van &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot; naar &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;. Sparen het dossier en begaat de veranderingen in uw project GitHub.



+++

+++ Stap 2: Een formulier ontwerpen met Microsoft Excel of Google Sheet.

In plaats van door complexe processen te navigeren, kunt u zonder problemen een formulier maken met behulp van een spreadsheet. U begint door de rijen en kolomkoppen toe te voegen aan een spreadsheet, waar elke rij een formulierveld vertegenwoordigt, terwijl elke kolomkop de eigenschappen van het overeenkomstige veld definieert.

Neem bijvoorbeeld het volgende spreadsheet waar rijen omtrekvelden voor een `enquiry` de eigenschappen van formulier- en kolomkoppen worden gedefinieerd:

![Opzoekblad](/help/edge/assets/enquiry-form-spreadsheet.png)

Ga als volgt te werk om het formulier te maken:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Drive.

1. Maak een Microsoft Excel-werkboek of Google-werkblad in de projectmap voor AEM Edge Delivery. Maak bijvoorbeeld een werkblad met de naam `enquiry` op AEM Edge Delivery-projectdirectory op Google Drive.

1. Zorg ervoor dat het blad wordt gedeeld met de juiste AEM (bijvoorbeeld `helix@adobe.com`) [volgens de configuraties die zijn opgegeven voor uw project](https://www.aem.live/docs/setup-customer-sharepoint). Hiermee geeft u de gebruiker bewerkingsmachtigingen voor het blad.

1. Open het gemaakte werkblad en wijzig de naam van het standaardwerkblad in &#39;shared-default&#39;.

   ![naam standaardblad wijzigen in &#39;shared-default&#39;](/help/edge/assets/rename-sheet-to-shared-default.png)

1. Als u formuliervelden wilt toevoegen, voegt u rijen en kolomkoppen in het &#39;standaard-gedeelde&#39; blad in. Elke rij moet een [formulierveld](/help/edge/docs/forms/form-components.md), met kolomkoppen die het corresponderende veld definiëren [eigenschappen](/help/edge/docs/forms/eds-form-field-properties).

   Voor een snel begin kunt u de inhoud van het dialoogvenster [Opzoekblad](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0) in uw spreadsheet. Sla het werkblad op nadat u de inhoud hebt gekopieerd.

   >[!VIDEO](https://video.tv.adobe.com/v/3427468?quality=12&learn=on)


1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het blad weer te geven.

   ![AEM Sidekick gebruiken om een voorvertoning van het blad weer te geven](/help/edge/assets/preview-form.png)

   Als u een voorbeeld bekijkt, wordt de inhoud van het blad op de tabbladen van de nieuwe browser in JSON-indeling weergegeven. Zorg ervoor dat u de voorbeeld-URL vastlegt, zoals dit is vereist voor het weergeven van het formulier in de volgende sectie. De URL-indeling is als volgt:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form>.json
   ```

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Bijvoorbeeld, als de bewaarplaats van uw project &quot;portaal&quot;wordt genoemd, is het gevestigd onder de rekening &quot;wkndforms&quot;, en u gebruikt de &quot;belangrijkste&quot;tak, kijkt URL als het volgende:

   `https://main--portal--wkndforms.hlx.page/enquiry.json`


+++

+++ Stap 3: Geef een voorbeeld van het formulier weer met de pagina Edge Delivery Service (EDS).


Tot nu toe hebt u het Adaptief formulierblok toegevoegd aan uw EDS-project en de structuur van het formulier voorbereid. Nu een voorbeeld van het formulier weergeven:

1. **Toegang tot uw projectmap:** Open uw Microsoft SharePoint- of Google Drive-account en navigeer naar uw AEM Edge Delivery-projectdirectory.

1. **Het formulier insluiten in een document:** Open een documentbestand (bijvoorbeeld een indexbestand) om het formulier in te sluiten. U kunt ook een nieuw document maken.

1. **Navigeer naar de gewenste locatie:** Ga naar de gewenste locatie in het document waar u het formulier wilt toevoegen.

1. **Voeg het adaptieve formulierblok toe:** Voeg een blok met de naam &#39;Form&#39; in het bestand in, zoals hieronder wordt geïllustreerd:

   | Formulier |
   |---|
   | [https://main—portal—wkndforms.hlx.live/inquiry.json](https://main--portal--wkndforms.hlx.live/enquiry.json) |

   Dit blok fungeert als tijdelijke aanduiding voor het ingesloten formulier. Voeg in de tweede rij van het blok de voorbeeld-URL van uw `<form>.json` bestand als hyperlink.

   >[!IMPORTANT]
   >
   >
   > Zorg ervoor dat de URL is opgemaakt als een hyperlink en niet wordt weergegeven als onbewerkte tekst.


1. Gebruiken [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content) om een voorvertoning van het document weer te geven. Het formulier wordt nu weergegeven op de pagina. Hier ziet u bijvoorbeeld het formulier dat is gebaseerd op de [spreadsheet vragen](https://docs.google.com/spreadsheets/d/196lukD028RDK_evBelkOonPxC7w0l_IiJ-Yx3DvMfNk/edit#gid=0):


   [![Een voorbeeld-EDS-formulier](/help/edge/assets/eds-form.png)](https://main--portal--wkndforms.hlx.live/)

   Vul nu het formulier in en klik op de knop Verzenden. Er treedt een fout op, die lijkt op het volgende, omdat het werkblad nog niet is ingesteld op het accepteren van de gegevens.

   ![fout bij het verzenden van formulier](/help/edge/assets/form-error.png)

+++


## Volgende stap

[Werkblad voorbereiden](/help/edge/docs/forms/submit-forms.md) om gegevens te accepteren bij het verzenden van het formulier.



## Meer weergeven

* [Formuliercomponenten](/help/edge/docs/forms/form-components.md)
* [Eigenschappen van formulierveld](/help/edge/docs/forms/eds-form-field-properties)
* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-eds-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)
