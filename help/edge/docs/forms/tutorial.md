---
title: Aan de slag met AEM Forms-Edge Delivery Services - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met een nieuw Adobe Experience Manager Forms-project (AEM). Binnen tien tot twintig minuten hebt u uw eigen formulieren gemaakt.
feature: Edge Delivery Services
exl-id: bb7e93ee-0575-44e1-9c5e-023284c19490
source-git-commit: ff8d04878da521b55121c9460a9d4b159ec617a4
workflow-type: tm+mt
source-wordcount: '1848'
ht-degree: 0%

---

# Aan de slag - Zelfstudie voor ontwikkelaars

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met AEM Forms Edge Delivery Services (EDS) kunt u formulieren maken met vertrouwde gereedschappen, zoals Google Docs en Microsoft Office.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft SharePoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

AEM Forms biedt een blok, Adaptive Forms Block genaamd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens. U kunt [een nieuw AEM-project maken dat vooraf is geconfigureerd met Adaptive Forms Block](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) of [het Adaptive Forms Block toevoegen aan een bestaand AEM-project](#add-adaptive-forms-block-to-your-existing-aem-project).

Deze zelfstudie van AEM Forms begeleidt u bij het maken, voorvertonen en publiceren van uw eigen aangepaste formulier met een nieuw Adobe Experience Manager (AEM) Forms-project.

## Vereisten

* U hebt een rekening GitHub, en begrijpt de grondbeginselen van het Git.
* Je hebt een Google- of Microsoft SharePoint-account.
* U begrijpt de grondbeginselen van HTML, CSS en JavaScript.
* Node/npm is geïnstalleerd voor lokale ontwikkeling.

**Koppen omhoog!** Deze zelfstudie gebruikt macOS, Chrome en Visual Studio Code. Terwijl de stappen voor andere montages kunnen worden aangepast, zouden de screenshots en specifieke elementen UI op uw gekozen werkend systeem, browser, en coderedacteur kunnen verschillen.


## Een nieuw AEM-project maken dat vooraf is geconfigureerd met Adaptive Forms Block

Met de AEM Forms Boilerplate-sjabloon kunt u snel aan de slag met een AEM project dat vooraf is geconfigureerd met het Adaptive Forms Block. Het is de snelste en eenvoudigste manier om AEM best practices te volgen en meteen uw formulieren samen te stellen.

### Aan de slag met de AEM Forms boilerplate-opslagsjabloon

1. Creeer een bewaarplaats GitHub voor uw AEM Project. Opslagplaats maken:
   1. Ga naar [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![AEM Forms Boilerplate](/help/edge/assets/aem-forms-boilerplate.png)
   1. Klik op de knop **Deze sjabloon gebruiken** en selecteert u de **Een nieuwe opslagplaats maken** -optie. Het scherm van de nieuwe repository wordt geopend.

      ![Nieuwe opslagplaats maken met AEM Forms Boilerplate](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   1. Selecteer in het scherm Nieuwe opslagplaats maken de optie **eigenaar** en geeft **Naam opslagplaats** . Adobe beveelt aan dat de opslagplaats wordt ingesteld op **Openbaar**. Selecteer dus de **publiek** en klik op **Opslagplaats maken**.

   ![De opslagplaats instellen op openbaar](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installeer de AEM Code Sync GitHub App in uw dataopslag. Installeren:
   1. Ga naar [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Selecteer in het scherm Install AEM Code Sync het **Alleen opslagplaatsen selecteren** en selecteert u de nieuwe opslagplaats. Klik op Opslaan.

   ![De opslagplaats instellen op openbaar](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

   >[!NOTE]
   >
   >
   > Als u de Onderneming van GitHub met IP het filtreren gebruikt, kunt u volgende IP aan de lijst van gewenste personen toevoegen: 3.227.118.73

   Gefeliciteerd! Er wordt een nieuwe website uitgevoerd op `https://<branch>--<repo>--<owner>.hlx.page/`.

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.

   Als de naam van de vertakking bijvoorbeeld `main`, opslagplaats `wefinance`en de eigenaar `wkndforms`, wordt de website op [https://main—wefinance—wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/).



### Uw eigen inhoudsbron koppelen

Uw nieuwe GitHub-opslagplaats wijst naar [voorbeeldinhoud opgeslagen in een Google Drive-map](https://drive.google.com/drive/folders/1bvjfi6TqpYA7DvbX6kKc-m7FgHuJ4RUQ). Deze inhoud met het kenmerk Alleen-lezen biedt een fantastisch beginpunt voor uw formulieren. U kunt het bestand gratis kopiëren naar uw eigen Google Drive en het aanpassen aan uw wensen.

![Voorbeeldinhoud op Google Drive](/help/edge/assets/folder-with-sample-content.png)

Om de steekproefinhoud aan uw eigen inhoudsomslag te kopiëren en uw bewaarplaats GitHub aan uw eigen inhoudsomslag te richten:

1. Maak een nieuwe map die specifiek voor uw AEM inhoud is bestemd in Google Drive of Microsoft SharePoint. In dit document wordt een map gebruikt die op Microsoft SharePoint is gemaakt.

1. Deel de map met de Adobe Experience Manager-gebruiker (helix@adobe.com).

   ![Gebruik de optie Toegang beheren om een map te delen met AEM gebruiker - SharePoint](/help/edge/assets/share-folder-with-aem-user.png)

   ![Gebruik de optie Toegang beheren om een map te delen met AEM gebruiker - Google Drive](/help/edge/assets/share-google-drive-folder.png)


   Zorg ervoor dat u bewerkingsrechten voor de map hebt opgegeven aan de Adobe Experience Manager-gebruiker.

   ![Map delen met AEM gebruiker, bewerkingsrechten bieden-SharePoint](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

   ![Map delen met AEM gebruiker, bewerkingsrechten bieden - Google Drive](/help/edge/assets/add-aem-user-google-folder.png)

1. De [voorbeeldinhoud opgeslagen in de map Google Drive](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_) naar uw map. Kopiëren:

   1. Download de bestanden samen of download afzonderlijke bestanden.

      ![Voorbeeldinhoud downloaden](/help/edge/assets/download-sample-content.png)

      De `nav` en `footer` de dossiers bepalen de basislay-out van uw pagina&#39;s en veranderen zelden door een project. Ze hebben ook een specifieke structuur die afwijkt van de meeste andere inhoudsbestanden. Door deze bestanden te bekijken, krijgt u een idee hoe inhoud in AEM Projecten wordt georganiseerd.


   1. Upload deze bestanden naar de map Microsoft SharePoint of Google Drive.

      ![Voorbeeldinhoud op Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Zorg ervoor dat u de  `enquiry` pagina van de voorbeeldinhoud naar uw map op Google Drive of Microsoft SharePoint. Deze bevat een structuur voor een voorbeeldformulier.

1. Nu u uw opstelling van de inhoudsomslag hebt, is het tijd om het met uw project op GitHub te verbinden die u eerder gebruikend AEM Forms Boilerplate creeerde. Verbinding maken:

   1. Ga naar de bewaarplaats GitHub die u eerder gebruikend AEM Forms Boilerplate creeerde.
   1. Open de `fstab.yaml` voor bewerken.
   1. Vervang de bestaande verwijzing door het pad naar de map die u met de AEM gebruiker hebt gedeeld (helix@adobe.com).

      ![Voorbeeldinhoud op Google Drive](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Als u de Microsoft SharePoint gebruikt, gebruikt het mappad de volgende notatie:

      ```HTML
      https://<tenant>.SharePoint.com/sites/<sp-site>/Shared%20Documents/<folder-name>
      ```

      Bijvoorbeeld:

      ```HTML
      https://adobe.SharePoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Ga voor meer informatie over het beheren van bestanden met Microsoft SharePoint naar [Adobe SharePoint gebruiken](https://www.aem.live/docs/setup-customer-sharepoint).


   1. De bijgewerkte `fsatb.yaml` als u de referentie hebt bijgewerkt en alles er goed uitziet. Als u om het even welke bouwstijlkwesties ontmoet, zie [Het oplossen van problemen GitHub bouwt kwesties](#troubleshooting-github-build-issues).



      ![Bijgewerkt bestand fsatab.yaml vastleggen](/help/edge/assets/commit-updated-fstab-yaml.png)

      Hiermee verbindt u de inhoudsmap met uw website. Na het bijwerken van de verwijzing kunnen fouten met &quot;404 Niet gevonden&quot; aanvankelijk optreden. Dit komt omdat er nog geen voorvertoning van uw inhoud is weergegeven. In de volgende sectie wordt uitgelegd hoe u begint met het ontwerpen en voorvertonen van uw inhoud.



### Inhoud voorvertonen en publiceren

Nadat u de laatste stap hebt uitgevoerd, is de nieuwe inhoudsbron niet leeg, maar is deze pas zichtbaar op uw website als deze wordt gepromoot naar de voorvertoning of de live stadia. Op dit moment kan dit 404 fouten veroorzaken.

Niet-gepubliceerde inhoud voorvertonen:

1. De chroom-extensie met de naam [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![AEM Sidekick installeren](/help/edge/assets/install-aem-sidekick.png)

   Nadat u de extensie hebt geïnstalleerd op Chrome, vergeet dan niet de extensie vast te zetten, zodat u deze gemakkelijker kunt vinden.

   ![Pin AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Als u de Sidekick Chrome-extensie wilt instellen, gaat u naar de eerder gedeelde map Google Drive of Microsoft SharePoint, klikt u met de rechtermuisknop op het extensiepictogram op de browserwerkbalk en selecteert u `Add this project`.

   ![AEM Sidekick - Een project toevoegen](/help/edge/assets/aem-sidekick-add-a-project.png)

   Wanneer de extensie is geïnstalleerd en uw project is toegevoegd, kunt u een voorvertoning van uw inhoud weergeven en deze publiceren vanaf uw Google Drive.

1. Selecteer alle documenten in de map Microsoft SharePoint of Google Drive. U kunt meerdere documenten kiezen door de Ctrl-toets (Windows/Linux) of de Cmd-toets (Mac) ingedrukt te houden terwijl u klikt.

   ![Alle bestanden selecteren](/help/edge/assets/select-all-files.png)

1. Klik op het AEM Sidekick-pictogram op de uitbreidingsbalk van Chrome. Er verschijnt een werkbalk op het scherm. U kunt uw inhoud voorvertonen of publiceren.

   Als u over hebt gekopieerd `index`, `nav`, `footer` en `enquiry` Dit zijn allemaal afzonderlijke documenten met een eigen voorvertoning en publicatiecyclus. Zorg er dus voor dat u een voorvertoning weergeeft (en publiceert) van al deze bestanden.

   Nadat u de bestanden hebt voorvertoond, worden de documenten weergegeven op de tabbladen van de nieuwe browser. Ga naar de volgende URL om een voorbeeld van het voorbeeldformulier te bekijken:


   ```HTML
   https://<branch>--<repository>--<owner>.hlx.live
   ```

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndforms&#39; en gebruikt u de &#39;main&#39;-vertakking, is de URL:

   [https://main—wefinance—wkndforms.hlx.page](https://main--wefinance--wkndforms.hlx.page).

### Een formulier maken

De voorbeeldinhoud bestaat uit een blad &quot;vraag&quot; dat fungeert als sjabloon voor het formulier &quot;vraag&quot;. Elke rij van het blad vertegenwoordigt een [formulierveld](/help/edge/docs/forms/form-components.md#available-components)en de kolomkoppen definiëren de [veldeigenschappen](/help/edge/docs/forms/form-components.md#available-components). Met dit voorbeeldformulier begint u met het samenstellen van uw formulier.

![Invorderingsformulier](/help/edge/docs/forms/assets/enquiry-form-microsoft-sharepoint.png)

Laten we beginnen met het bijwerken van een veldlabel. Open het blad &#39;Vraag&#39; voor bewerking, wijzig het label van de verzendknop in `Let's Chat` en gebruik AEM Sidekick om het bestand voor te vertonen en te publiceren.

![Invorderingsformulier](/help/edge/assets/enquiry-form-preview-publish.png)

Wanneer u een voorvertoning van het bestand weergeeft of het bestand publiceert, wordt een JSON-versie van het bestand op een nieuw tabblad weergegeven. Kopieer de voorvertoning (.hlx.page) of de publicatie (.hlx.live) URL van het bestand.

![JSON van het spreadsheet van het formulier](/help/edge/assets//preview-and-publish-enquiry-form.png)

Open de `enquiry` en vervangt u de URL in het formulierblok door de URL van het bestand die u in de vorige stap hebt gekopieerd. Controleer of de URL een hyperlink is.

![Bezig met opvragen van bestand met de URL .json van spreadsheet](/help/edge/assets/enquiry-doc-to-embed-form.png)

Gebruik AEM Sidekick om een voorvertoning van het enquêtedocument weer te geven en dit te publiceren.

![Bezig met opvragen van bestand met de URL .json van spreadsheet](/help/edge/assets/preview-and-publish-enquiry-document.png)


Ga naar de volgende URL om een voorbeeld van het bijgewerkte onderzoeksformulier te bekijken:


```HTML
    https://<branch>--<repository>--<owner>.hlx.page/enquiry
       
```

Het label van de verzendknop wordt bijgewerkt naar `Let's Chat`.

![Invorderingsformulier](/help/edge/assets/updated-form.png)

Ga voor meer informatie over het maken en publiceren van een nieuw formulier naar de [een formulier maken](/help/edge/docs/forms/create-forms.md) hulplijn.

### Beginnen met het ontwikkelen van stijlen en functionaliteit


Zo kunt u snel aan de slag met een lokale AEM-ontwikkelomgeving:

1. Installeer AEM CLI: AEM CLI vereenvoudigt ontwikkelingstaken. Laten we het wereldwijd installeren met npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Kloon uw project GitHub: Kloon uw projectbewaarplaats van GitHub gebruikend het volgende bevel, die vervangt <owner> met de eigenaar van de opslagplaats en <repo> met de naam van de opslagplaats:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. Start uw lokale omgeving: navigeer naar uw projectmap en vul uw lokale AEM met één opdracht in:

   ```
   cd <repo>
   aem up
   ```

Het Adaptive Forms-blok `blocks/form` De map is uw afspeelplaats voor het opmaken en coderen van uw formulieren! Alle `.css` of `.js` in deze map en u ziet de wijzigingen direct in uw browser.

Klaar om uw creatie te presenteren? Gebruik Git om uw wijzigingen vast te leggen en door te drukken. Hiermee werkt u de voorvertoning- en productieomgevingen bij die toegankelijk zijn via deze URL&#39;s (vervang plaatsaanduidingen door uw projectdetails):

Voorvertoning: `https://<branch>--<repo>--<owner>.hlx.page/`
Productie: `https://<branch>--<repo>--<owner>.hlx.live/`

Gefeliciteerd! U hebt uw lokale ontwikkelomgeving ingesteld en uw wijzigingen geïmplementeerd.



## Aangepast Forms-blok toevoegen aan uw bestaande AEM-project


>[!VIDEO](https://video.tv.adobe.com/v/3427789)

Als u een bestaand AEM project hebt, kunt u het Adaptive Forms Block integreren in uw huidige project om aan de slag te gaan met het maken van formulieren.

>[!NOTE]
>
>
> Deze stap is van toepassing op projecten die zijn gebouwd met de [AEM Boilerplate](https://github.com/adobe/aem-boilerplate). Als u uw AEM project gebruikend creeerde [AEM Forms Boilerplate](https://github.com/adobe-rnd/aem-boilerplate-forms)kunt u deze stap overslaan.

Om te integreren:

1. Clone the Adaptive Forms Block repository: [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms) naar uw computer.

1. Zoek in de gedownloade map de `blocks/form` map. Deze map kopiëren. Navigeer nu naar de lokale AEM van uw project `blocks` en plak de gekopieerde formuliermap hier.

1. Leg deze veranderingen in uw AEM project op GitHub vast en duw.


Dat is het! Het Adaptive Forms Block maakt nu deel uit van uw AEM project. U kunt beginnen met het maken en toevoegen van formulieren aan uw AEM.


## Het oplossen van problemen GitHub bouwt kwesties

Verzeker een vlotte GitHub bouwt proces door potentiële kwesties te richten:

* **Fout in pad van module oplossen:**
Als u de fout &quot;Kan pad naar module &quot;&#39;../../scripts/lib-franklin.js&#39;&#39; niet omzetten, navigeert u naar de [EDS-project]/blocks/forms/form.js. Werk de importinstructie bij door het bestand lib-franklin.js te vervangen door het bestand aem.js.

* **Fouten bij het koppelen van handgrepen:**
Als u tegenkomt met regelfouten, kunt u deze omzeilen. Open de [EDS-project]/package.json en wijzig het &quot;lint&quot;manuscript van `"lint": "npm run lint:js && npm run lint:css"` tot `"lint": "echo 'skipping linting for now'"`. Sparen het dossier en begaat de veranderingen in uw project GitHub.


## Zie ook

{{see-more-forms-eds}}
