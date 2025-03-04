---
title: Aan de slag met Edge Delivery Services for AEM Forms in de Universal Editor - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met een nieuw Adobe Experience Manager Forms-project (AEM). Over tien tot twintig minuten hebt u uw eigen Edge Delivery Services Forms gemaakt in de Universal Editor.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 24a23d98-1819-4d6b-b823-3f1ccb66dbd8
source-git-commit: 964fd32a7dbcb97190d40cb42100d0d66e69a0c4
workflow-type: tm+mt
source-wordcount: '1841'
ht-degree: 0%

---


# Aan de slag met Edge Delivery Services for AEM Forms met Universal Editor (WYSIWYG)

<span class="preview"> Deze functie is beschikbaar via het programma voor vroege toegang. Om toegang te verzoeken, verzend een e-mail van uw officieel adres naar <a href="mailto:aem-forms-ea@adobe.com"> aem-forms-ea@adobe.com </a> met uw GitHub organisatienaam en bewaarplaatsnaam. Bijvoorbeeld, als de bewaarplaats URL https://github.com/adobe/abc is, is de organisatienaam adobe en de bewaarplaatsnaam abc.</span>


In het huidige digitale tijdperk zijn gebruikersvriendelijke formulieren essentieel voor alle organisaties. Edge Delivery Services Forms wordt gemaakt met de Universal Editor, die WYSIWYG-mogelijkheden (what-you-see-is-what-you-get) biedt. Het biedt een moderne, intuïtieve interface voor efficiënt ontwerpen van formulieren.

AEM Forms biedt een blok, het Adaptive Forms Block, waarmee u eenvoudig Edge Delivery Services Forms kunt maken om gegevens vast te leggen en op te slaan. U kunt [ een nieuw Project van AEM tot stand brengen dat met het AanpassingsBlok van Forms ](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) wordt gevormd of [ het Aangepaste Blok van Forms aan een bestaand Project van AEM ](#add-adaptive-forms-block-to-your-existing-aem-project) toevoegt.

![ Github het Werkschema van de Bewaarplaats ](/help/edge/assets/repo-workflow.png)

Deze zelfstudie begeleidt u bij het maken, voorvertonen en publiceren van uw eigen formulier met een nieuw of bestaand Adobe Experience Manager Site-project met behulp van de WYSIWYG-authoring van Universal Editor.


## Vereisten

* U hebt een rekening GitHub, en begrijpt de grondbeginselen van het Git.
* U begrijpt de basisbeginselen van HTML, CSS en JavaScript.
* Node/npm is geïnstalleerd voor lokale ontwikkeling.

## Een nieuw AEM-project maken dat vooraf is geconfigureerd met Adaptive Forms Block

Met de AEM Forms Boilerplate-sjabloon kunt u snel aan de slag met een AEM-project dat vooraf is geconfigureerd met het Adaptive Forms Block. Dit is de snelste en eenvoudigste manier om de beste praktijken van AEM te volgen en meteen uw formulieren samen te stellen.

### Aan de slag met de AEM Forms boilerplate-opslagsjabloon

1. Creeer een bewaarplaats GitHub voor uw Project van AEM. Opslagplaats maken:
   1. Ga naar [ https://github.com/adobe-rnd/aem-boilerplate-forms ](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![ AEM Forms Boilerplate ](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Klik het **Gebruik deze malplaatje** optie en selecteer **creeer een nieuwe bewaarplaats** optie.

      ![ creeer nieuwe bewaarplaats gebruikend AEM Forms Boilerplate ](/help/edge/docs/forms/assets/use-eds-form-template.png)

      **creeer een nieuwe bewaarplaats** scherm opent.

   1. Op **creeer een nieuwe bewaarplaats** scherm, selecteer de **eigenaar**, en specificeer **Naam van de Bewaarplaats**. Adobe adviseert om de bewaarplaats aan **Openbaar** te plaatsen. Zo, selecteer de **openbare** optie, en klik **creeer Bewaarplaats**.

      ![ plaats de bewaarplaats aan openbaar ](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installeer de AEM Code Sync GitHub App in uw repository. Installeren:
   1. Ga naar [ https://github.com/apps/aem-code-sync/installations/new ](https://github.com/apps/aem-code-sync/installations/new).
   1. Op **installeer het scherm van de Synchronisatie van de Code van AEM**, selecteer **slechts de optie van Bewaarplaatsen** en selecteer uw pas gecreëerde bewaarplaats. Klik **sparen**.

   ![ plaats de bewaarplaats aan openbaar ](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Koppel nu de GitHub-opslagplaats die u met AEM Forms Boilerplate hebt gemaakt aan uw AEM Project-ontwerpomgeving. Verbinding maken:

   1. Ga naar de bewaarplaats GitHub die u eerder gebruikend AEM Forms Boilerplate creeerde.
   1. Open het {**dossier 0} fstab.yaml voor het uitgeven.**

      ![ open fstab.yaml- dossier ](/help/edge/docs/forms/assets/open-fstab.png)

   1. Bewerk het {**dossier 0} fstab.yaml om het koppelingspunt van uw project bij te werken.** Vervang de URL door de URL van de AEM as a Cloud Service-ontwerpinstantie.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![ geef fstab.yaml- dossier uit ](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Leg het bijgewerkte {**dossier 0} fstab.yaml vast, zodra u de verwijzing hebt bijgewerkt en alles ziet er goed uit.**

      ![ begaat de veranderingen ](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Als u om het even welke bouwstijlkwesties ontmoet, zie [ het oplossen van problemen GitHub bouwt kwesties ](#troubleshooting-github-build-issues).

### Een nieuw AEM-project maken

Nu u een project GitHub hebt, kunt u te werk gaan om een nieuw Project van AEM bij de het auteursinstantie van AEM as a Cloud Service tot stand te brengen en te publiceren.
1. Een nieuw AEM-project maken:

   1. Login aan de auteursinstantie van AEM as a Cloud Service en selecteert **Plaatsen**.

      ![ uitgezochte plaatsen ](/help/edge/assets/select-sites.png)

   1. Klik **creëren** > **Plaats van malplaatje**.

      ![ creeer-plaatsen ](/help/edge/docs/forms/assets/create-sites.png)

   1. Selecteer het malplaatje van de Plaats van Edge Delivery Services en klik **daarna**.

      ![ selecteren-plaats-malplaatje ](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Als de Edge Delivery Services Site-sjabloon niet beschikbaar is in uw ontwerpexemplaar, klikt u op de knop Importeren om de sjabloon te uploaden.
      > * U kunt de malplaatjes van de Plaats van Edge Delivery Services van [ GitHub ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases) downloaden.

   1. Voer de volgende gegevens in om een nieuw AEM-project te maken:
      * **titel van de Plaats** - voeg een beschrijvende titel voor de plaats toe.
      * **titel van de Plaats** - gebruik `site-name` dat u in de vorige stap bepaalde.
      * **GitHub URL** - gebruik URL van het project GitHub u in de vorige stap creeerde.

      ![ creeer AEM Plaats ](/help/edge/docs/forms/assets/create-aem-site.png)

   1. **creeer de dialoog van de Plaats** verschijnt, klik **Oke**.

      ![ klik o.k. ](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      Binnen een paar minuten wordt je nieuwe AEM Project gemaakt.

   1. Navigeer aan uw onlangs-gecreeerd project van AEM in de console van Plaatsen en klik **uitgeven**.
In dit geval wordt de pagina `index.html` gebruikt ter illustratie.

      ![ geef de Plaats van AEM uit ](/help/edge/docs/forms/assets/edit-site.png)

      Het AEM-project wordt op een nieuw tabblad in de Universal Editor geopend, zodat u WYSIWYG kunt ontwerpen. U kunt nu uw AEM-project bewerken.

      ![ Plaats opent in Universele Redacteur ](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Uw gemaakte AEM-project publiceren

   Publiceer het AEM-project als u klaar bent met het bewerken. Publiceren:

   1. Voor de console van Plaatsen, selecteer alle pagina&#39;s van het Project van AEM en klik **Snel publiceren**.

      ![ publiceer AEM Sites Project ](/help/edge/docs/forms/assets/publish-sites.png)

   1. Het **Snelle publiceer** bevestigingsdialoog verschijnt, **publiceert** om het het publiceren proces te beginnen.

      ![ Snelle publiceer bevestigingsdialoog ](/help/edge/docs/forms/assets/quick-publish.png)

      U kunt uw AEM-projectpagina&#39;s ook rechtstreeks vanuit de gebruikersinterface van de Universal Editor publiceren.

      ![ Snelle publiceer bevestigingsdialoog ](/help/edge/docs/forms/assets/qui.png)

   Gefeliciteerd! Er wordt een nieuwe website uitgevoerd op `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/` .

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.
   * `<site-name>` verwijst naar de naam van de door u gemaakte site.

   Als de naam van de vertakking bijvoorbeeld `main` is, de opslagplaats `edsforms` is, de eigenaar `wkndforms` is en `site-name` is `eds-forms` , wordt de website uitgevoerd op `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   >[!NOTE]
   >
   > * Als u de pagina `index.html` van het AEM-project wilt weergeven, gebruikt u de URL: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * Als u andere pagina&#39;s dan de `index page` van het AEM-project wilt weergeven, gebruikt u de URL: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

Nu, kunt u beginnen [ creërend en toevoegend vormen aan uw Project van AEM ](#add-edge-delivery-services-forms-to-aem-project).

## Aangepast Forms-blok toevoegen aan uw bestaande AEM-project

Als u een bestaand AEM-project hebt, kunt u het Adaptive Forms Block integreren in uw huidige project om aan de slag te gaan met het maken van formulieren.

>[!NOTE]
>
>
> Deze stap is op projecten van toepassing die met [ worden gebouwd AEM Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-xwalk). Als u uw Project van AEM gebruikend het [ Boilerplate van AEM Forms ](https://github.com/adobe-rnd/aem-boilerplate-forms) creeerde, kunt u deze stap overslaan.

Integreren:
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
   1. Navigeer aan het `../scripts/editor-support.js` dossier in uw Project van AEM en werk het met de veranderingen van het {[ redacteur-support.js- dossier in AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms/blob/main/scripts/editor-support.js#L105-L106) bij
1. **update ESLint configuratiedossier**
   1. Navigeer naar het `../.eslintignore` -bestand in uw AEM-project en voeg de volgende coderegel toe om fouten met betrekking tot de regelengine voor formulierblokken te voorkomen:

      ```
          blocks/form/rules/formula/*
          blocks/form/rules/model/*
      ```

1. Leg deze wijzigingen vast en duw deze naar uw AEM Project-opslagplaats op GitHub.

Dat is het! Het Adaptive Forms Block maakt nu deel uit van uw AEM-project. U kunt [ beginnen tot stand te brengen en vormen toe te voegen aan uw Project van AEM ](#add-edge-delivery-services-forms-to-aem-site-project).

## AEM Forms autoriseren met WYSIWYG

U kunt uw AEM-project openen in de Universal Editor voor WYSIWYG-ontwerpen. Hierin kunt u het project bewerken en de sectie Adaptief formulier toevoegen om Edge Delivery Services-formulieren op AEM Project-pagina&#39;s toe te voegen.

1. Voeg de sectie Adaptief formulier toe aan uw AEM-projectpagina. Toevoegen:
   1. Navigeer aan uw project van AEM in de console van Plaatsen, selecteer de plaatspagina u wilt uitgeven, en klik **uitgeven**. De AEM-projectpagina wordt geopend in de Universal Editor en kan worden bewerkt.
In dit geval wordt de pagina `index.html` gebruikt ter illustratie.
   1. Open de Inhoudsstructuur en navigeer naar een sectie waar u de sectie Aangepast formulier wilt toevoegen.
   1. Klik op het pictogram **[!UICONTROL Add]** en selecteer de component **[!UICONTROL Adaptive Form]** in de lijst met componenten.

   ![ inhoudsboom ](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   De sectie Adaptief formulier wordt toegevoegd. U kunt nu formuliercomponenten toevoegen aan de AEM-projectpagina.

1. Voeg formuliercomponenten toe aan de toegevoegde sectie Adaptief formulier. Formuliercomponenten toevoegen:
   1. Navigeer naar de toegevoegde sectie Adaptief formulier in de Inhoudsstructuur.

      ![ adaptief toegevoegd vormblok ](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Klik het **[!UICONTROL Add]** pictogram en voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.

      ![ voeg component ](/help/edge/docs/forms/assets/add-component.png) toe

      U kunt ook de vereiste Adaptieve Forms-componenten slepen en neerzetten, aangezien de Universal Editor een intuïtieve functie voor slepen en neerzetten biedt.

   1. Selecteer de toegevoegde component Adaptief formulier om de eigenschappen van de component bij te werken met **[!UICONTROL Properties]** .

      ![ open eigenschappen ](/help/edge/docs/forms/assets/component-properties.png)

   1. Bekijk een voorbeeld van het formulier.
In de onderstaande schermafbeelding wordt het formulier weergegeven dat in het AEM Project is gemaakt en dat gebruikmaakt van WYSIWYG-authoring:

      ![ toegevoegde vorm ](/help/edge/docs/forms/assets/added-form-aem-sites.png)

      Als de gebruiker tevreden is met de voorvertoning, kan hij doorgaan met het publiceren van de pagina.

      >[!NOTE]
      >
      > Het is belangrijk dat u de AEM Project-pagina opnieuw publiceert nadat u wijzigingen hebt aangebracht. Als dit niet het geval is, zijn de updates niet zichtbaar in de browser.

1. Publiceer de AEM-projectpagina opnieuw.

   1. Klik **publiceren** om de pagina van het Project van AEM na het toevoegen van de vorm opnieuw te publiceren.

      ![ publiceer vorm ](/help/edge/docs/forms/assets/publish-form.png)

   1. De **publiceer** bevestigingsdialoog verschijnt op het scherm, **publiceert** om te beginnen publiceren.

      ![ publiceer form1 ](/help/edge/docs/forms/assets/publish-form1.png)

      Zodra u **klikt publiceer** knoop, verschijnt het `Publish started successfully` bericht.

      ![ publiceer form2 ](/help/edge/docs/forms/assets/publish-form2.png)

   U kunt nu de AEM-projectpagina met het toegevoegde Edge Delivery Services-formulier bekijken op de volgende URL:
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Als de naam van de vertakking bijvoorbeeld `main` is, de opslagplaats `edsforms` is, de eigenaar `wkndforms` is en de naam van de site `eds-forms` is, is de URL:
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![ indexpagina ](/help/edge/docs/forms/assets/publish-index-page.png)

U kunt Edge Delivery Services Forms opmaken door de `.css` en `.js` dossiers in het AanpassingsBlok van Forms en [ vestiging een lokale ontwikkelomgeving van AEM ](#set-up-local-aem-development-environment) uit te geven om de veranderingen in uw browser onmiddellijk te bekijken.

>[!NOTE]
>
> U kunt [ auteur een standalone vorm in Universele Redacteur ook en het publiceren aan Edge Delivery Services ](/help/edge/docs/forms/universal-editor/create-forms.md).

## Lokale AEM-ontwikkelomgeving instellen

U kunt een lokale AEM-ontwikkelomgeving instellen voor het lokaal ontwikkelen van aangepaste stijlen en componenten. Aan de slag met een lokale AEM-ontwikkelomgeving:

1. **installeer CLI van AEM**: AEM CLI vereenvoudigt ontwikkelingstaken. Laten we het wereldwijd installeren met npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **Kloon uw project GitHub**: Kloon uw plaats van het Project van AEM van GitHub gebruikend het volgende bevel, die vervangt <owner> met de eigenaar van de opslagplaats en <repo> met de naam van de opslagplaats:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Begin Uw Lokaal Milieu**: Navigeer aan uw projectfolder en begin uw lokale instantie van AEM met één enkel bevel:

   ```
   cd <repo>
   aem up
   ```

U kunt lokale wijzigingen aanbrengen in de map Adaptive Forms Block `blocks/form` voor de opmaak en codering van uw formulieren. Bewerk de `.css` - of `.js` -bestanden in deze map en u ziet dat de wijzigingen direct in uw browser worden doorgevoerd.

Nadat u de wijzigingen hebt aangebracht, gebruikt u de opdrachten van Git om deze vast te leggen en door te drukken. Hiermee werkt u de voorvertoning- en productieomgevingen bij, die toegankelijk zijn via de volgende URL&#39;s (vervang plaatsaanduidingen door uw projectdetails):

Voorvertoning: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>`

Productie: `https://<branch>--<repo>--<owner>.aem.live/content/<site-name>`


## Het oplossen van problemen GitHub bouwt kwesties

Verzeker een vlotte GitHub bouwt proces door potentiële kwesties te richten:

* **handvat het Leiden Fouten:**
Als u tegenkomt met regelfouten, kunt u deze omzeilen. Open het ] /package.json dossier van het Project van 0} EDS {en wijzig het &quot;plusteken&quot;manuscript van `"lint": "npm run lint:js && npm run lint:css"` aan `"lint": "echo 'skipping linting for now'"`. [ Sparen het dossier en begaat de veranderingen in uw project GitHub.

* **los de Fout van de Weg van de Module op:**
Als u de fout &quot;Onbekwaam ontmoet om weg aan module &quot;&quot;../../scripts/lib-franklin.js&quot;op te lossen, navigeer aan het [ EDS Project ] /blocks/forms/form.js- dossier. Werk de importinstructie bij door het bestand lib-franklin.js te vervangen door het bestand aem.js.

## Zie ook

{{universal-editor-see-also}}
