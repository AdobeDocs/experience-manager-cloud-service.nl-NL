---
title: Aan de slag met AEM Forms-Edge Delivery Services - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met een nieuw Adobe Experience Manager Forms-project (AEM). Binnen tien tot twintig minuten hebt u uw eigen formulieren gemaakt.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 2b64cc8d2afb7d6064d1f60ba023448171862236
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 0%

---


# Aan de slag - Zelfstudie voor ontwikkelaars

In het huidige digitale tijdperk is het van essentieel belang gebruikersvriendelijke formulieren te maken voor elke organisatie. Met AEM Forms Edge Delivery Services (EDS) kunt u formulieren maken met vertrouwde gereedschappen, zoals Google Docs en Microsoft Office.

Deze formulieren verzenden gegevens rechtstreeks naar een Microsoft Excel- of Google Sheets-bestand, zodat u levendige ecosystemen en robuuste API&#39;s van Google Sheets, Microsoft Excel en Microsoft Sharepoint kunt gebruiken om ingediende gegevens eenvoudig te verwerken of een bestaande zakelijke workflow te starten.

AEM Forms biedt een blok, Adaptief formulierblok genaamd, waarmee u eenvoudig formulieren kunt maken voor het vastleggen en opslaan van vastgelegde gegevens.

Deze zelfstudie van AEM Forms begeleidt u bij het maken, voorvertonen en publiceren van uw eigen aangepaste formulier met een nieuw Adobe Experience Manager (AEM) Forms-project. U leert ook Adaptive Forms Block aan een bestaand AEM-project toevoegen.

* **[Een nieuw AEM-project maken dat vooraf is uitgerust met een adaptief Forms-blok](#create-a-new-eds-project-pre-equipped-with-adaptive-forms-block)**
* **[Aangepast Forms-blok toevoegen aan een bestaand AEM-project](#add-adaptive-forms-block-to-an-existing-eds-project)**



## Vereisten

* U hebt een rekening GitHub, en begrijpt de grondbeginselen van het Git.
* Je hebt een Google- of Microsoft SharePoint-account.
* U begrijpt de grondbeginselen van HTML, CSS en JavaScript.
* Node/npm is geïnstalleerd voor lokale ontwikkeling.

**Koppen omhoog!** Deze zelfstudie gebruikt macOS, Chrome en Visual Studio Code. Terwijl de stappen voor andere montages kunnen worden aangepast, zouden de screenshots en specifieke elementen UI op uw gekozen werkend systeem, browser, en coderedacteur kunnen verschillen.


## Een nieuw AEM-project maken dat vooraf is uitgerust met een adaptief Forms-blok

Met de AEM Forms Boilerplate-sjabloon kunt u snel aan de slag met een AEM project dat vooraf is geconfigureerd met het Adaptive Form Block. Het is de snelste en eenvoudigste manier om AEM best practices te volgen en meteen uw formulieren samen te stellen.

### Aan de slag met de AEM Forms boilerplate-opslagsjabloon

1. Meld u aan bij uw Github-account.
1. Ga naar [https://github.com/adobe-rnd/aem-boilerplate-forms](https://github.com/adobe-rnd/aem-boilerplate-forms).

   ![AEM Forms Boilerplate](/help/edge/assets/aem-forms-boilerplate.png)
1. Klikken **Deze sjabloon gebruiken** en selecteert u de **Een nieuwe opslagplaats maken** en selecteert u waar u deze gegevensopslagruimte wilt maken.
   ![Nieuwe opslagplaats maken met AEM Forms Boilerplate](/help/edge/assets/create-new-repository-using-aem-forms-boilerplate.png)

   Adobe beveelt aan dat de gegevensopslagruimte wordt ingesteld op openbaar. Selecteer in het scherm Een nieuwe opslagplaats maken de optie **publiek** -optie.

   ![De opslagplaats instellen op openbaar](/help/edge/assets/create-a-new-repo-keep-it-public.png)


1. Installeer de AEM Code Sync GitHub App in uw dataopslag. Installeren:
   1. Ga naar [https://github.com/apps/aem-code-sync/installations/new](https://github.com/apps/aem-code-sync/installations/new).
   1. Selecteer in het scherm Install AEM Code Sync het **Alleen opslagplaatsen selecteren** en selecteert u de nieuwe opslagplaats. Klik op Opslaan.

   ![De opslagplaats instellen op openbaar](/help/edge/assets/install-aem-code-sync-app-for-your-repo.png)

       >[!OPMERKING]
       >
       >
       > Als u de Onderneming van Github met IP het filtreren gebruikt, kunt u volgende IP aan de lijst van gewenste personen toevoegen: 3.227.118.73
   
   Gefeliciteerd! Er wordt een nieuwe website uitgevoerd op `https://<branch>--<repo>--<owner>.hlx.page/`. In het bovenstaande voorbeeld is dat [https://main—wefinance—wkndforms.hlx.page/](https://main--wefinance--wkndforms.hlx.page/).

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.


### Uw eigen inhoudsbron koppelen met Google Drive

Uw geforceerde opslagplaats van Boilerplate van GitHub wijst aan wat [voorbeeldinhoud opgeslagen in een Google Drive-map](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_). Deze inhoud met het kenmerk Alleen-lezen biedt een fantastisch beginpunt voor uw formulieren. U kunt het bestand gratis kopiëren naar uw eigen Google Drive en het aanpassen aan uw wensen.

![Voorbeeldinhoud op Google Drive](/help/edge/assets/folder-with-sample-content.png)

Als u uw eigen inhoud wilt koppelen,

1. Maak een nieuwe map die specifiek voor uw AEM inhoud is bestemd in Google Drive of Microsoft SharePoint. In dit document wordt een map gebruikt die op Microsoft SharePoint is gemaakt.

1. Deel de map met de Adobe Experience Manager-gebruiker (helix@adobe.com).

   ![De optie Toegang beheren gebruiken om een map te delen met AEM gebruiker](/help/edge/assets/share-folder-with-aem-user.png)

   Zorg ervoor dat u bewerkingsrechten voor de map hebt opgegeven aan de Adobe Experience Manager-gebruiker.

   ![Map delen met AEM gebruiker, bewerkingsrechten opgeven](/help/edge/assets/share-folder-with-aem-user-provide-editing-access.png)

1. De [voorbeeldinhoud opgeslagen in de map Google Drive](https://drive.google.com/drive/folders/17LSiMZC77N8tCJRW45TnHHGcG8V3SLG_) naar uw map. Kopiëren:

   1. Download de bestanden samen of download afzonderlijke bestanden.

      ![Voorbeeldinhoud downloaden](/help/edge/assets/download-sample-content.png)

      De `index`, `nav`, en `footer` de dossiers bepalen de basislay-out van uw pagina&#39;s en veranderen zelden door een project. Ze hebben ook een specifieke structuur die afwijkt van de meeste andere inhoudsbestanden. Door deze bestanden te bekijken, krijgt u een idee hoe inhoud in AEM projecten wordt georganiseerd.


   1. Upload deze bestanden naar de map Microsoft SharePoint of Google Drive.

      ![Voorbeeldinhoud op Google Drive](/help/edge/assets/upload-sample-files-to-your-content-folder.png)

      Zorg ervoor dat u de  `enquiry` pagina van de voorbeeldinhoud naar uw map op Google Drive of Microsoft SharePoint. Deze bevat een structuur voor een voorbeeldformulier.

1. Nu u uw opstelling van de inhoudsomslag hebt, is het tijd om het met uw project op GitHub te verbinden die u eerder gebruikend AEM Forms Boilerplate creeerde. Verbinding maken:

   1. Meld u aan bij uw Github-account.
   1. Ga naar de bewaarplaats GitHub die u eerder gebruikend AEM Forms Boilerplate creeerde.
   1. Open de `fstab.yaml` voor bewerken.
   1. Vervang de bestaande verwijzing door het pad naar de map die u met de AEM gebruiker hebt gedeeld (helix@adobe.com).

      ![Voorbeeldinhoud op Google Drive](/help/edge/assets/replace-path-in-fstab-yaml-with-your-content-folder.png)


      Als u de Microsoft SharePoint gebruikt, gebruikt het mappad de volgende notatie:

      ```HTML
      https://<tenant>.sharepoint.com/sites/  <sp-site>/Shared%20Documents/<folder-name>
      ```

      Bijvoorbeeld:

      ```HTML
      https://adobe.sharepoint.com/sites/wkndforms/Shared%20Documents/wefinance
      ```

      Raadpleeg voor meer informatie over het beheren van bestanden met Microsoft SharePoint de [Hoe te om Adobe SharePoint te gebruiken](https://www.aem.live/docs/setup-customer-sharepoint).



   1. Leg het bijgewerkte bestand &#39;fsatb.yaml&#39; vast nadat u de verwijzing hebt bijgewerkt en alles er goed uitziet. Hiermee slaat u uw werk op en verbindt u uw inhoudsmap met uw website.

      ![Bijgewerkt bestand fsatab.yaml vastleggen](/help/edge/assets/commit-updated-fstab-yaml.png)


      >[!NOTE]
      >
      >
      >Na het bijwerken van de verwijzing kunnen fouten met &quot;404 Niet gevonden&quot; aanvankelijk optreden. Dit komt omdat er nog geen voorvertoning van uw inhoud is weergegeven. In de volgende sectie wordt uitgelegd hoe u begint met het ontwerpen en voorvertonen van uw inhoud.



### Inhoud voorvertonen en publiceren

Nadat u de laatste stap hebt uitgevoerd, is de nieuwe inhoudsbron niet leeg, maar is deze pas zichtbaar op uw website als deze wordt gepromoot naar de voorvertoning of de live stadia. Op dit moment kan dit 404 fouten veroorzaken.

Niet-gepubliceerde inhoud voorvertonen:

1. De chroom-extensie met de naam [AEM Sidekick](https://chrome.google.com/webstore/detail/helix-sidekick-beta/ccfggkjabjahcjoljmgmklhpaccedipo).

   ![AEM Sidekick installeren](/help/edge/assets/install-aem-sidekick.png)

   Nadat u de extensie hebt geïnstalleerd op Chrome, vergeet dan niet de extensie vast te zetten, zodat u deze gemakkelijker kunt vinden.

   ![Pin AEM Sidekick](/help/edge/assets/pin-aem-sidekick.png)

1. Als u de Sidekick Chrome-extensie wilt instellen, gaat u naar de eerder gedeelde map Google Drive of Microsoft SharePoint en klikt u met de rechtermuisknop op het extensiepictogram op de browserwerkbalk en selecteert u `Add this project`.

   ![AEM Sidekick - Een project toevoegen](/help/edge/assets/aem-sidekick-add-a-project.png)

   Zodra de extensie is geïnstalleerd en uw project is toegevoegd, kunt u een voorvertoning van uw inhoud weergeven en deze publiceren vanaf uw Google Drive.

1. Selecteer alle documenten in de map Microsoft SharePoint of Google Drive. U kunt meerdere documenten kiezen door de Ctrl-toets (Windows/Linux) of de Cmd-toets (Mac) ingedrukt te houden terwijl u klikt.

   ![Alle bestanden selecteren](/help/edge/assets/select-all-files.png)

1. Klik op het AEM Sidekick-pictogram dat op de uitbreidingsbalk van Chrome is vastgezet. Er verschijnt een werkbalk op het scherm. U kunt uw inhoud voorvertonen of publiceren.

   Als u over hebt gekopieerd `index`, `nav`, `footer` en `enquiry` Dit zijn allemaal afzonderlijke documenten met een eigen voorvertoning en publicatiecyclus. Zorg er dus voor dat u een voorvertoning weergeeft (en publiceert) van al deze bestanden.

   Nadat u de bestanden hebt voorvertoond, worden de documenten weergegeven op de tabbladen van de nieuwe browser. Ga naar de volgende URL om een voorbeeld van het voorbeeldformulier te bekijken:


   ```JSON
       https://<branch>--<repository>--<owner>.hlx.live/<form-path>/<form-file-name>.json
   ```

   * `<branch>` Verwijst naar de tak van uw bewaarplaats GitHub.
   * `<repository>` duidt uw bewaarplaats GitHub aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.


   `https://<branch>--<repo>--<owner>.hlx.page/enquiry` URL.

   Als de gegevensopslagruimte van uw project bijvoorbeeld &#39;wefinance&#39; heet, bevindt deze zich onder de eigenaar van de account &#39;wkndforms&#39; en gebruikt u de &#39;main&#39;-vertakking, is de URL:



   [https://main—wefinance—wkndforms.hlx.page/inquiry](https://main--wefinance--wkndforms.hlx.page/enquiry).


### Beginnen met het ontwikkelen van stijlen en functionaliteit


Zo kunt u snel aan de slag met een lokale AEM-ontwikkelomgeving:

1. Installeer AEM CLI: AEM CLI vereenvoudigt ontwikkelingstaken. Laten we het wereldwijd installeren met npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. Kloon uw project van Github: Kloon uw projectbewaarplaats van GitHub gebruikend het volgende bevel, die vervangt <owner> met de eigenaar van de opslagplaats en <repo> met de naam van de opslagplaats:

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

Als u een bestaand AEM project hebt, kunt u het Adaptief formulierblok integreren in uw huidige project om aan de slag te gaan met het maken van formulieren. Om te integreren:

1. Kloont de Adaptief opslagplaats voor formulierblokken: https://github.com/adobe-rnd/aem-boilerplate-forms naar uw computer.

1. Zoek in de gedownloade map de `blocks/form` map. Deze map kopiëren. Navigeer nu naar de lokale AEM van uw project `blocks` en plak de gekopieerde formuliermap hier.

1. Leg deze veranderingen in uw AEM project op GitHub vast en duw.


Dat is het! Het Adaptive Forms Block maakt nu deel uit van uw AEM project. U kunt beginnen met het maken en toevoegen van formulieren aan uw AEM.


### Het oplossen van problemen GitHub bouwt kwesties

Verzeker een vlotte GitHub bouwt proces door potentiële kwesties te richten:

* **Fout in pad van module oplossen:**
Als u de fout &quot;Kan pad naar module &quot;&#39;../../scripts/lib-franklin.js&#39;&#39; niet omzetten, navigeert u naar de [EDS-project]/blocks/forms/form.js. Werk de importinstructie bij door het bestand lib-franklin.js te vervangen door het bestand aem.js.

* **Fouten bij het koppelen van handgrepen:**
Als u tegenkomt met regelfouten, kunt u deze omzeilen. Open de [EDS-project]/package.json en wijzig het script &quot;lint&quot; van &quot;lint&quot;: &quot;npm run lint:js &amp;&amp; npm run lint:css&quot; naar &quot;lint&quot;: &quot;echo &#39;skipping linting for now&#39;. Sparen het dossier en begaat de veranderingen in uw project GitHub.





