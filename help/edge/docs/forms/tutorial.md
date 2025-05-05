---
title: Aan de slag met Edge Delivery Services voor AEM Forms - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met een nieuw Adobe Experience Manager Forms-project (AEM). Over tien tot twintig minuten hebt u uw eigen formulieren gemaakt.
feature: Edge Delivery Services
exl-id: bb7e93ee-0575-44e1-9c5e-023284c19490
role: Admin, Architect, Developer
source-git-commit: e2259e542df5a12748705af901d073e4486292c4
workflow-type: tm+mt
source-wordcount: '1907'
ht-degree: 0%

---

# Aan de slag - Zelfstudie voor ontwikkelaars

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met Edge Delivery Services for AEM Forms kunt u formulieren maken met vertrouwde gereedschappen, zoals Google Docs en Microsoft Office.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

AEM Forms biedt een blok, Adaptive Forms Block genaamd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt [ tot een nieuw project van AEM leiden preconfigured met het AanpassingsBlok van Forms ](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) <!--or [add the Adaptive Forms Block to an existing AEM project](#add-adaptive-forms-block-to-your-existing-aem-project)-->.

Deze zelfstudie van AEM Forms begeleidt u bij het maken, voorvertonen en publiceren van uw eigen aangepaste formulier met een nieuw Adobe Experience Manager (AEM) Forms-project.

## Vereisten

* U hebt een rekening GitHub, en begrijpt de grondbeginselen van het Git.
* Je hebt een Google- of Microsoft SharePoint-account.
* U begrijpt de basisbeginselen van HTML, CSS en JavaScript.
* Node/npm is geïnstalleerd voor lokale ontwikkeling.

**Koppen omhoog!** In deze zelfstudie worden macOS, Chrome en Visual Studio Code gebruikt. Terwijl de stappen voor andere montages kunnen worden aangepast, zouden de screenshots en specifieke elementen UI op uw gekozen werkend systeem, browser, en coderedacteur kunnen verschillen.


## Een nieuw AEM-project maken dat vooraf is geconfigureerd met Adaptive Forms Block

Met de AEM Forms Boilerplate-sjabloon kunt u snel aan de slag met een AEM-project dat vooraf is geconfigureerd met het Adaptive Forms Block. Het is de snelste en eenvoudigste manier om de beste praktijken van AEM te volgen en meteen al uw formulieren samen te stellen.

### Aan de slag met de AEM Forms boilerplate-opslagsjabloon

1. Creeer een bewaarplaats GitHub voor uw Project van AEM. Opslagplaats maken:
   1. Ga naar [ https://github.com/adobe-rnd/aem-boilerplate-forms ](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![ AEM Forms Boilerplate ](/help/edge/assets/aem-forms-boilerplate.png)
   1. Klik het **Gebruik deze malplaatje** optie en selecteer **creeer een nieuwe bewaarplaats** optie. Het scherm van de nieuwe repository wordt geopend.

      ![ creeer nieuwe bewaarplaats gebruikend AEM Forms Boilerplate ](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. Voor creeer een nieuw bewaarplaatsscherm, selecteer de **eigenaar**, en specificeer **Naam van de Bewaarplaats**. Adobe adviseert dat de bewaarplaats aan **Openbaar** wordt geplaatst. Zo, selecteer de **openbare** optie, en klik **creeer Bewaarplaats**.

   ![ plaats de bewaarplaats aan openbaar ](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installeer de AEM Code Sync GitHub App in uw repository. Installeren:
   1. Ga naar [ https://github.com/apps/aem-code-sync/installations/new ](https://github.com/apps/aem-code-sync/installations/new).
   1. Voor het Install scherm van de Synchronisatie van de Code van AEM, selecteer **slechts de optie van Bewaarplaatsen** en selecteer uw pas gecreëerde bewaarplaats. Klik op Opslaan.

   ![ plaats de bewaarplaats aan openbaar ](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Als u de Onderneming van GitHub met IP het filtreren gebruikt, kunt u volgende IP aan de lijst van gewenste personen toevoegen: 3.227.118.73

   Gefeliciteerd! Er wordt een nieuwe website uitgevoerd op `https://<branch>--<repo>--<owner>.aem.page/` .

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Als de naam van de vertakking bijvoorbeeld `main` is, de opslagplaats `wefinance` is en de eigenaar `wkndforms` is, wordt de website uitgevoerd op `https://main--wefinance--wkndforms.aem.page`
&lt;!—(https://main—wefinance—wkndform.aem.page)—>

### Uw eigen inhoudsbron koppelen

<!--Your newly created GitHub repository points to [example content stored in a Google Drive folder](https://drive.google.com/drive/folders/1bvjfi6TqpYA7DvbX6kKc-m7FgHuJ4RUQ). This read-only content provides a great starting point for your forms. Feel free to copy it into your own Google Drive and customize it to fit your needs.

![Sample Content on Google Drive](/help/edge/assets/folder-with-sample-content.png)-->

Om de steekproefinhoud aan uw eigen inhoudsomslag te kopiëren en uw bewaarplaats GitHub aan uw eigen inhoudsomslag te richten:

1. Maak een nieuwe map die speciaal voor uw AEM-inhoud is bestemd in Google Drive of Microsoft SharePoint. In dit document wordt een map gebruikt die op Microsoft SharePoint is gemaakt.

1. Deel de map met de Adobe Experience Manager-gebruiker (forms@adobe.com).

   ![ het Gebruik beheert de optie van de Toegang om omslag met de Gebruiker van AEM te delen - SharePoint ](/help/edge/assets/share-folder-with-aem-user.png)

   ![ het Gebruik beheert de optie van de Toegang om omslag met AEM te delen Gebruiker - de Aandrijving van Google ](/help/edge/assets/share-google-drive-folder.png)


   Zorg ervoor dat u bewerkingsrechten voor de map hebt opgegeven aan de Adobe Experience Manager-gebruiker.

   ![ omslag van het Aandeel met de Gebruiker van AEM, verstrek het uitgeven rechten-SharePoint ](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png) {width=50%}

   ![ de omslag van het Aandeel met de Gebruiker van AEM, verstrekt het uitgeven rechten - de Aandrijving van Google ](/help/edge/assets/add-aem-user-google-folder.png) {width=50%}

1. Kopieer de [ voorbeeldinhoud ](/help/edge/assets/wefinance1.zip) aan uw omslag. Kopiëren:

   1. Pak de gedownloade map uit en kopieer de inhoud.

      ![ Inhoud van de Steekproef van de Download ](/help/edge/assets/download-sample-content.png)

      De bestanden `nav` en `footer` definiëren de basislay-out van uw pagina&#39;s en veranderen zelden in een project. Ze hebben ook een specifieke structuur die afwijkt van de meeste andere inhoudsbestanden. Door deze bestanden te bekijken, krijgt u een idee hoe de inhoud in AEM Projecten wordt georganiseerd.


   1. Upload deze bestanden naar de map Microsoft SharePoint of Google Drive.

      ![ Inhoud van de Steekproef op de Aandrijving van Google ](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Kopieer het `enquiry` -blad van de voorbeeldinhoud naar de map op Google Drive of Microsoft SharePoint. Deze bevat een structuur voor een voorbeeldformulier.

1. Nu u uw opstelling van de inhoudsomslag hebt, is het tijd om het met uw project op GitHub te verbinden die u eerder gebruikend AEM Forms Boilerplate creeerde. Verbinding maken:

   1. Ga naar de bewaarplaats GitHub die u eerder gebruikend AEM Forms Boilerplate creeerde.
   1. Open de `fstab.yaml` voor bewerking.
   1. Vervang de bestaande verwijzing door het pad naar de map die u met de AEM-gebruiker hebt gedeeld (forms@adobe.com).

      ![ Inhoud van de Steekproef op de Aandrijving van Google ](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Als u de Microsoft SharePoint gebruikt, gebruikt het mappad de volgende notatie:

      ```HTML
      https://<tenant>.SharePoint.com/sites/<sp-site>/Shared%20Documents/<folder-name>
      ```

      Bijvoorbeeld:

      ```HTML
      https://adobe.SharePoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Voor meer informatie bij het beheren van dossiers met Microsoft SharePoint, zie [ hoe te Adobe SharePoint ](https://www.aem.live/docs/setup-customer-sharepoint) gebruiken.


   1. Leg het bijgewerkte `fsatb.yaml` -bestand vast nadat u de verwijzing hebt bijgewerkt en alles er goed uitziet. Als u om het even welke bouwstijlkwesties ontmoet, zie [ het oplossen van problemen GitHub bouwt kwesties ](#troubleshooting-github-build-issues).

      ![ Leg bijgewerkt fsatab.yaml- dossier ](/help/edge/assets/commit-updated-fstab-yaml.png) vast

      Hiermee verbindt u de inhoudsmap met uw website. Na het bijwerken van de verwijzing kunnen fouten met &quot;404 Niet gevonden&quot; aanvankelijk optreden. Dit komt omdat er nog geen voorvertoning van uw inhoud is weergegeven. In de volgende sectie wordt uitgelegd hoe u begint met het ontwerpen en voorvertonen van uw inhoud.

### Inhoud voorvertonen en publiceren

Nadat u de laatste stap hebt uitgevoerd, is de nieuwe inhoudsbron niet leeg, maar is deze pas zichtbaar op uw website als deze wordt gepromoot naar de voorvertoning of de live stadia. Op dit moment kan dit 404 fouten veroorzaken.

Niet-gepubliceerde inhoud voorvertonen:

1. Installeer de uitbreiding van Chrome genoemd [ AEM Sidekick ](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![ installeer AEM Sidekick ](/help/edge/assets/install-aem-sidekick.png)

   Nadat u de extensie hebt geïnstalleerd op Chrome, vergeet dan niet de extensie vast te zetten, zodat u deze gemakkelijker kunt vinden.

   ![ Vastzetten AEM Sidekick ](/help/edge/assets/pin-aem-sidekick.png)

1. Als u de extensie Sidekick Chrome wilt instellen, gaat u naar de map Google Drive of Microsoft SharePoint die u eerder hebt gedeeld, klikt u met de rechtermuisknop op het extensiepictogram op de browserwerkbalk en selecteert u `Add this project` .

   ![ AEM Sidekick - voeg een project ](/help/edge/assets/aem-sidekick-add-a-project.png) toe

   Wanneer de extensie is geïnstalleerd en uw project is toegevoegd, kunt u een voorvertoning van uw inhoud weergeven en deze publiceren vanaf uw Google Drive.

1. Selecteer alle documenten in de map Microsoft SharePoint of Google Drive. U kunt meerdere documenten kiezen door de Ctrl-toets (Windows/Linux) of de Cmd-toets (Mac) ingedrukt te houden terwijl u klikt.

   ![ selecteer alle dossiers ](/help/edge/assets/select-all-files.png)

1. Klik op het AEM Sidekick-pictogram op de Chrome-uitbreidingsbalk. Er verschijnt een werkbalk op het scherm. U kunt uw inhoud voorvertonen of publiceren.

   Als u de bestanden `index` , `nav` , `footer` en `enquiry` hebt gekopieerd, zijn al deze documenten afzonderlijke documenten met hun eigen voorvertoning- en publicatiecycli. Zorg er dus voor dat u een voorvertoning weergeeft (en publiceert) van al deze documenten.

   Nadat u de bestanden hebt voorvertoond, worden de documenten weergegeven op de tabbladen van de nieuwe browser. Ga naar de volgende URL om een voorbeeld van het voorbeeldformulier te bekijken:


   ```HTML
   https://<branch>--<repository>--<owner>.aem.live
   ```

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.


   `https://<branch>--<repo>--<owner>.aem.page/enquiry` URL.

   Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndform&#39; en gebruikt u de &#39;main&#39;-vertakking en formuliernaam als `enquiry` , is de URL: `https://main--wefinance--wkndform.aem.live/enquiry` .
&lt;!—(https://main—wefinance—wkndform.aem.live/inquiry).—>

### Een formulier maken

De voorbeeldinhoud bestaat uit een blad &quot;vraag&quot; dat fungeert als sjabloon voor het formulier &quot;vraag&quot;. Elke rij van het blad vertegenwoordigt a [ vormgebied ](/help/edge/docs/forms/form-components.md#available-components), en de kolomkopballen bepalen de [ gebiedseigenschappen ](/help/edge/docs/forms/form-components.md#available-components). Met dit voorbeeldformulier begint u met het samenstellen van uw formulier.

![ Vorm van het Onderzoek ](/help/edge/docs/forms/assets/enquiry-form-microsoft-sharepoint.png)

Laten we beginnen met het bijwerken van een veldlabel. Open het blad &#39;Vraag&#39; om het te bewerken, wijzig het label van de verzendknop in `Let's Talk` en gebruik AEM Sidekick om het bestand voor te vertonen en te publiceren.

![ Vorm van het Onderzoek ](/help/edge/assets/enquiry-form-preview-publish.png)

Wanneer u een voorvertoning van het bestand weergeeft of het bestand publiceert, wordt een JSON-versie van het bestand op een nieuw tabblad weergegeven. Kopieer de voorvertoning (.name.page) of de publicatie (.aem.live) URL van het bestand.

![ JSON van de vormspreadsheet ](/help/edge/assets/preview-and-publish-enquiry-form.png)

Open het `enquiry` -bestand en vervang de URL in het formulierblok door de URL van het bestand dat u in de vorige stap hebt gekopieerd. Controleer of de URL een hyperlink is.

![ dossier van het Onderzoek met .json URL van URL van spreadsheet ](/help/edge/assets/enquiry-doc-to-embed-form.png)

Gebruik AEM Sidekick om een voorvertoning van het enquêtedocument weer te geven en dit te publiceren.

![ dossier van het Onderzoek met .json URL van URL van spreadsheet ](/help/edge/assets/preview-and-publish-enquiry-document.png)


Ga naar de volgende URL om een voorbeeld van het bijgewerkte onderzoeksformulier te bekijken:


```HTML
    https://<branch>--<repository>--<owner>.aem.page/enquiry
       
```

Het label van de verzendknop wordt bijgewerkt naar `Let's Talk` .

![ Vorm van het Onderzoek ](/help/edge/assets/updated-form.png)

&lt;!— (https://main—wefinance—wkndform.aem.live/inquiry)—>

URL: `https://main--wefinance--wkndform.aem.live/enquiry`
&lt;!— (https://main—wefinance—wkndform.aem.live/inquiry)—>


Voor gedetailleerde informatie over het creëren van en het publiceren van een nieuwe vorm, hoofd over aan [ creeert een vorm ](/help/edge/docs/forms/create-forms.md) gids.

### Beginnen met het ontwikkelen van stijlen en functionaliteit


Zo kunt u snel aan de slag met een lokale AEM-ontwikkelomgeving:

1. Installeer de AEM CLI: de AEM CLI vereenvoudigt ontwikkelingstaken. Laten we het wereldwijd installeren met npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Kloon uw project GitHub: Kloon uw projectbewaarplaats van GitHub gebruikend het volgende bevel, die vervangt &lt;owner> met de eigenaar van de opslagplaats en &lt;repo> met de naam van de opslagplaats:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Start uw lokale omgeving: navigeer naar uw projectmap en vul uw lokale AEM-instantie op met één opdracht:

   ```
   cd <repo>
   aem up
   ```

De map Adaptive Forms Block `blocks/form` is uw afspeelplaats voor opmaak en code voor uw formulieren! Bewerk `.css` - of `.js` -bestanden in deze map en u ziet de wijzigingen direct in uw browser.

Klaar om uw creatie te presenteren? Gebruik Git om uw wijzigingen vast te leggen en door te drukken. Hiermee werkt u de voorvertoning- en productieomgevingen bij die toegankelijk zijn via deze URL&#39;s (vervang plaatsaanduidingen door uw projectdetails):

Voorvertoning: `https://<branch>--<repo>--<owner>.aem.page/`
Productie: `https://<branch>--<repo>--<owner>.aem.live/`

Gefeliciteerd! U hebt uw lokale ontwikkelomgeving ingesteld en uw wijzigingen geïmplementeerd.

## Aangepast Forms-blok toevoegen aan uw bestaande AEM-project

<!--
>[!VIDEO](https://video.tv.adobe.com/v/3427789)-->

Als u een bestaand AEM-project hebt, kunt u het Adaptive Forms Block integreren in uw huidige project om aan de slag te gaan met het maken van formulieren.

>[!NOTE]
>
>
> Deze stap is op projecten van toepassing die met [ worden gebouwd AEM Boilerplate ](https://github.com/adobe/aem-boilerplate). Als u uw project van AEM gebruikend [ AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms) creeerde, kunt u deze stap overslaan.

Om te integreren:

1. **voegt vereiste dossiers en omslagen** toe
   1. Kopieer en kleef de volgende omslagen en de dossiers van [ AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms) in uw Project van AEM:

      * [ van het vormblok ](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/blocks/form) omslag
      * [ vorm-gemeenschappelijke ](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-common) omslag
      * [ vorm-componenten ](https://github.com/adobe-rnd/aem-boilerplate-forms/tree/main/models/form-components) omslag
      * [ vorm-redacteur-support.js ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.js) dossier
      * [ vorm-redacteur-support.css ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/form-editor-support.css) dossier

1. **de componentendefinities en modeldossiers van de Update**
   1. Navigeer naar het `../models/_component-definition.json` dossier in uw Project van AEM en werk het met de veranderingen van het [ _component-definition.json- dossier in de Boilerplate van AEM Forms ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-definition.json#L39-L48) bij.

   1. Navigeer naar het `../models/_component-models.json` dossier in uw Project van AEM en werk het met de veranderingen van het [ _component-models.json dossier in de Boilerplate van AEM Forms bij ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/models/_component-models.json#L24-L26)

1. **voeg de Redacteur van de Vorm in redacteursmanuscript** toe
   1. Navigeer aan het `../scripts/editor-support.js` dossier in uw Project van AEM en werk het met de veranderingen van het &lbrace;[ redacteur-support.js- dossier in AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js#L105-L106) bij
1. **update ESLint configuratiedossier**
   1. Navigeer naar het `../.eslintignore` -bestand in uw AEM-project en voeg de volgende coderegel toe om fouten met betrekking tot de regelengine voor formulierblokken te voorkomen:

      ```
          blocks/form/rules/formula/*
          blocks/form/rules/model/*
      ```

1. Leg deze wijzigingen vast en duw deze naar uw AEM Project-opslagplaats op GitHub.

Dat is het! Het Adaptive Forms Block maakt nu deel uit van uw AEM-project. U kunt formulieren maken en toevoegen aan uw AEM-pagina&#39;s.

## Het oplossen van problemen GitHub bouwt kwesties

Verzeker een vlotte GitHub bouwt proces door potentiële kwesties te richten:

* **los de Fout van de Weg van de Module op:**
Als u de fout &quot;Onbekwaam ontmoet om weg aan module &quot;&quot;../../scripts/lib-franklin.js&quot;op te lossen, navigeer aan het [ EDS Project ] /blocks/forms/form.js- dossier. Werk de importinstructie bij door het bestand lib-franklin.js te vervangen door het bestand aem.js.

* **handvat het Leiden Fouten:**
Als u tegenkomt met regelfouten, kunt u deze omzeilen. Open het &rbrack; /package.json dossier van het Project van 0&rbrace; EDS &lbrace;en wijzig het &quot;plusteken&quot;manuscript van `"lint": "npm run lint:js && npm run lint:css"` aan `"lint": "echo 'skipping linting for now'"`. &lbrack; Sparen het dossier en begaat de veranderingen in uw project GitHub.


## Zie ook

{{see-more-forms-eds}}
