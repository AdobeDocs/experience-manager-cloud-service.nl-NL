---
title: Aan de slag met Edge Delivery Services voor AEM Forms in de Universal Editor - Zelfstudie voor ontwikkelaars
description: Deze zelfstudie helpt u om aan de slag te gaan met een nieuw Adobe Experience Manager Forms-project (AEM). Over tien tot twintig minuten hebt u uw eigen Edge Delivery Services Forms gemaakt in de Universal Editor.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '1618'
ht-degree: 0%

---


# Aan de slag met Edge Delivery Services voor AEM Forms met de Universal Editor (WYSIWYG)

In het huidige digitale tijdperk zijn gebruikersvriendelijke formulieren essentieel voor alle organisaties. Edge Delivery Services Forms worden gemaakt met de Universal Editor, die WYSIWYG-mogelijkheden (what-you-see-is-what-you-get) biedt. Het biedt een moderne, intuïtieve interface voor efficiënt ontwerpen van formulieren.

AEM Forms biedt een blok, het Adaptive Forms Block, waarmee u eenvoudig Forms-Edge Delivery Services kunt maken voor het vastleggen en opslaan van gegevens. U kunt [ een nieuw AEMProject tot stand brengen dat met het AanpassingsBlok van Forms ](#create-a-new-aem-project-pre-configured-with-adaptive-forms-block) wordt gevormd of [ voegt het Aangepaste Blok van Forms aan een bestaand AEM Project ](#add-adaptive-forms-block-to-your-existing-aem-project) toe.

Deze zelfstudie begeleidt u bij het maken, voorvertonen en publiceren van uw eigen formulier met een nieuw of bestaand Adobe Experience Manager Site-project met behulp van de WYSIWYG-authoring van Universal Editor.


## Vereisten

* U hebt een rekening GitHub, en begrijpt de grondbeginselen van het Git.
* Je hebt een Google- of Microsoft SharePoint-account.
* U begrijpt de basisbeginselen van HTML, CSS en JavaScript.
* Node/npm is geïnstalleerd voor lokale ontwikkeling.

## Een nieuw AEM-project maken dat vooraf is geconfigureerd met Adaptive Forms Block

Met de AEM Forms Boilerplate-sjabloon kunt u snel aan de slag met een AEM project dat vooraf is geconfigureerd met het Adaptive Forms Block. Dit is de snelste en eenvoudigste manier om AEM best practices te volgen en meteen uw formulieren samen te stellen.

### Aan de slag met de AEM Forms boilerplate-opslagsjabloon

1. Creeer een bewaarplaats GitHub voor uw AEM Project. Opslagplaats maken:
   1. Ga naar [ https://github.com/adobe-rnd/aem-boilerplate-forms ](https://github.com/adobe-rnd/aem-boilerplate-forms).

      ![ AEM Forms Boilerplate ](/help/edge/docs/forms/assets/eds-form-boilerplate.png)
   1. Klik het **Gebruik deze malplaatje** optie en selecteer **creeer een nieuwe bewaarplaats** optie.

      ![ creeer nieuwe bewaarplaats gebruikend AEM Forms Boilerplate ](/help/edge/docs/forms/assets/use-eds-form-template.png)

      **creeer een nieuwe bewaarplaats** scherm opent.

   1. Op **creeer een nieuwe bewaarplaats** scherm, selecteer de **eigenaar**, en specificeer **Naam van de Bewaarplaats**. De Adobe adviseert om de bewaarplaats aan **Openbaar** te plaatsen. Zo, selecteer de **openbare** optie, en klik **creeer Bewaarplaats**.

      ![ plaats de bewaarplaats aan openbaar ](/help/edge/docs/forms/assets/name-eds-repo.png)

1. Installeer de AEM Code Sync GitHub App in uw dataopslag. Installeren:
   1. Ga naar [ https://github.com/apps/aem-code-sync/installations/new ](https://github.com/apps/aem-code-sync/installations/new).
   1. Op **installeer AEM het scherm van de Synchronisatie van de Code**, selecteer **slechts de optie van Bewaarplaatsen** en selecteer uw pas gecreëerde bewaarplaats. Klik **sparen**.

   ![ plaats de bewaarplaats aan openbaar ](/help/edge/docs/forms/assets/aem-code-sync-up.png)

1. Verbind nu de bewaarplaats GitHub u gebruikend AEM Forms Boilerplate aan uw AEM het auteursmilieu van het Project creeerde. Verbinding maken:

   1. Ga naar de bewaarplaats GitHub die u eerder gebruikend AEM Forms Boilerplate creeerde.
   1. Open het {**dossier 0} fstab.yaml voor het uitgeven.**

      ![ open fstab.yaml- dossier ](/help/edge/docs/forms/assets/open-fstab.png)

   1. Bewerk het {**dossier 0} fstab.yaml om het koppelingspunt van uw project bij te werken.** Vervang de URL door de URL van de AEM as a Cloud Service-ontwerpinstantie.
      `https://<aem-author>/bin/franklin.delivery/<owner>/<repository>/main`

      ![ geef fstab.yaml- dossier uit ](/help/edge/docs/forms/assets/edit-fstab-file.png)

   1. Leg het bijgewerkte {**dossier 0} fstab.yaml vast, zodra u de verwijzing hebt bijgewerkt en alles ziet er goed uit.**

      ![ begaat de veranderingen ](/help/edge/docs/forms/assets/commit-fstab-changes.png)

      Als u om het even welke bouwstijlkwesties ontmoet, zie [ het oplossen van problemen GitHub bouwt kwesties ](#troubleshooting-github-build-issues).

### Nieuw AEM maken

Nu u een project GitHub hebt, kunt u te werk gaan om een nieuw AEM Project bij de het auteursinstantie van AEM as a Cloud Service tot stand te brengen en te publiceren.
1. Een nieuw AEM-project maken:

   1. Login aan de auteursinstantie van AEM as a Cloud Service en selecteert **Plaatsen**.

      ![ uitgezochte plaatsen ](/help/edge/assets/select-sites.png)

   1. Klik **creëren** > **Plaats van malplaatje**.

      ![ creeer-plaatsen ](/help/edge/docs/forms/assets/create-sites.png)

   1. Selecteer het malplaatje van de Plaats van Edge Delivery Services en klik **daarna**.

      ![ selecteren-plaats-malplaatje ](/help/edge/docs/forms/assets/select-site-template.png)

      >[!NOTE]
      >
      > * Als het malplaatje van de Plaats van Edge Delivery Services niet beschikbaar op uw auteursinstantie is, klik de knoop van de Invoer om het malplaatje te uploaden.
      > * U kunt de malplaatjes van de Plaats van Edge Delivery Services van [ GitHub ](https://github.com/adobe-rnd/aem-boilerplate-xwalk/releases) downloaden.

   1. Voer de volgende gegevens in om een nieuw AEM project te maken:
      * **titel van de Plaats** - voeg een beschrijvende titel voor de plaats toe.
      * **titel van de Plaats** - gebruik `site-name` dat u in de vorige stap bepaalde.
      * **GitHub URL** - gebruik URL van het project GitHub u in de vorige stap creeerde.

      ![ creeer AEM Plaats ](/help/edge/docs/forms/assets/create-aem-site.png)

   1. **creeer de dialoog van de Plaats** verschijnt, klik **Oke**.

      ![ klik o.k. ](/help/edge/docs/forms/assets/click-ok-aem-site.png)

      Binnen een paar minuten wordt uw nieuwe AEM Project gemaakt.

   1. Navigeer aan uw onlangs-gecreeerd AEM project in de console van Plaatsen en klik **uitgeven**.
In dit geval wordt de pagina `index.html` gebruikt ter illustratie.

      ![ geef AEM Plaats uit ](/help/edge/docs/forms/assets/edit-site.png)

      Het AEM Project wordt in de Universal Editor geopend op een nieuw tabblad, zodat u in WYSIWYG kunt ontwerpen. U kunt nu uw AEM Project bewerken.

      ![ Plaats opent in Universele Redacteur ](/help/edge/docs/forms/assets/site-in-universal-editor.png)

1. Publish uw gemaakte AEM Project

   Publiceer het AEM nadat u klaar bent met het bewerken. Publiceren:

   1. Voor de console van Plaatsen, selecteer alle pagina&#39;s van het Project van de AEM en klik **Snelle Publish**.

      ![ publiceer AEM Sites Project ](/help/edge/docs/forms/assets/publish-sites.png)

   1. Het **Snelle de bevestigingsdialoog van Publish** verschijnt, klik **Publish** om het het publiceren proces te beginnen.

      ![ Snelle de bevestigingsdialoog van Publish ](/help/edge/docs/forms/assets/quick-publish.png)

      U kunt uw AEM projectpagina&#39;s ook rechtstreeks vanuit de gebruikersinterface van de Universal Editor publiceren.

      ![ Snelle de bevestigingsdialoog van Publish ](/help/edge/docs/forms/assets/qui.png)

   Gefeliciteerd! Er wordt een nieuwe website uitgevoerd op `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/` .

   * `<branch>` verwijst naar de vertakking van uw bewaarplaats GitHub.
   * `<repository>` geeft uw GitHub-opslagplaats aan.
   * `<owner>` verwijst naar gebruikersbenaming van uw rekening GitHub die gastheren uw bewaarplaats GitHub.
   * `<site-name>` verwijst naar de naam van de door u gemaakte site.

   Als de naam van de vertakking bijvoorbeeld `main` is, de opslagplaats `edsforms` is, de eigenaar `wkndforms` is en `site-name` is `eds-forms` , wordt de website uitgevoerd op `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   >[!NOTE]
   >
   > * Als u de pagina `index.html` van het AEM Project wilt weergeven, gebruikt u de URL: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`
   > * Als u andere pagina&#39;s dan de `index page` van het AEM Project wilt weergeven, gebruikt u de URL: `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/<site-page-name>`

Nu, kunt u beginnen [ creërend en toevoegend vormen aan uw AEM Project ](#add-edge-delivery-services-forms-to-aem-project).

## Aangepast Forms-blok toevoegen aan uw bestaande AEM-project

Als u een bestaand AEM project hebt, kunt u het Adaptive Forms Block integreren in uw huidige project om aan de slag te gaan met het maken van formulieren.

>[!NOTE]
>
>
> Deze stap is op projecten van toepassing die met [ worden gebouwd AEM Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-xwalk). Als u uw AEM project gebruikend [ AEM Forms Boilerplate ](https://github.com/adobe-rnd/aem-boilerplate-forms) creeerde, kunt u deze stap overslaan.

Om te integreren:

1. Kloon de Adaptieve bewaarplaats van GitHub van het Blok van Forms: [ https://github.com/adobe-rnd/aem-boilerplate-forms ](https://github.com/adobe-rnd/aem-boilerplate-forms) aan uw computer.
1. Zoek in de gedownloade map naar de map `blocks/form` en kopieer deze map.
1. Kloon uw AEM bewaarplaats van GitHub van het Project aan uw computer.
1. Navigeer nu naar de map `blocks` in uw lokale AEM Projectopslagplaats en plak de gekopieerde formuliermap daar.
1. Leg deze veranderingen in uw AEM bewaarplaats van het Project op GitHub vast en duw.

Dat is het! Het Adaptive Forms Block maakt nu deel uit van uw AEM Project. U kunt [ beginnen en vormen aan uw AEMProject ](#add-edge-delivery-services-forms-to-aem-site-project) toe te voegen.

## AEM Forms autoriseren met WYSIWYG

U kunt uw AEM Project openen in de Universele Redacteur voor het auteursrecht van WYSIWYG, waar u het project kunt uitgeven en de Adaptieve sectie van de Vorm toevoegen om Edge Delivery Services te omvatten vormen op AEM pagina&#39;s van het Project.

1. Voeg de sectie Adaptief formulier toe aan de AEM projectpagina. Toevoegen:
   1. Navigeer aan uw AEM Project in de console van Plaatsen en klik **uitgeven**. De pagina AEM Project wordt geopend in de Universal Editor en kan worden bewerkt.
In dit geval wordt de pagina `index.html` gebruikt ter illustratie.
   1. Open de Inhoudsstructuur en navigeer naar de locatie waar u de sectie Aangepast formulier wilt toevoegen.
   1. Klik op het pictogram **[!UICONTROL Add]** en selecteer de component **[!UICONTROL Adaptive Form]** in de lijst met componenten.

   ![ inhoudsboom ](/help/edge/docs/forms/assets/add-adaptive-form-block.png)

   De sectie Adaptief formulier wordt toegevoegd op de opgegeven locatie. U kunt nu formuliercomponenten toevoegen aan de AEM projectpagina.

1. Voeg formuliercomponenten toe aan de toegevoegde sectie Adaptief formulier. Formuliercomponenten toevoegen:
   1. Navigeer naar de toegevoegde sectie Adaptief formulier in de Inhoudsstructuur.

      ![ adaptief toegevoegd vormblok ](/help/edge/docs/forms/assets/adative-form-block.png)


   1. Klik het **[!UICONTROL Add]** pictogram en voeg de gewenste componenten van de **Adaptieve lijst van Componenten van de Vorm** toe.

      ![ voeg component ](/help/edge/docs/forms/assets/add-component.png) toe

      U kunt ook de vereiste Adaptieve Forms-componenten slepen en neerzetten, aangezien de Universal Editor een intuïtieve functie voor slepen en neerzetten biedt.

   1. Selecteer de toegevoegde component Adaptief formulier om de eigenschappen van de component bij te werken met **[!UICONTROL Properties]** .

      ![ open eigenschappen ](/help/edge/docs/forms/assets/component-properties.png)

      In de onderstaande schermafbeelding wordt het formulier weergegeven dat in het AEM Project is gemaakt en dat gebruikmaakt van WYSIWYG-authoring:

      ![ toegevoegde vorm ](/help/edge/docs/forms/assets/added-form-aem-sites.png)

   >[!NOTE]
   >
   > Het is belangrijk om uw AEM pagina van het Project opnieuw te publiceren nadat het aanbrengen van veranderingen; anders, zijn de updates niet zichtbaar in browser.

1. Publiceer de AEM projectpagina opnieuw.

   1. Klik **Publish** om de AEM pagina van het Project na het toevoegen van de vorm opnieuw te publiceren.

      ![ publiceer vorm ](/help/edge/docs/forms/assets/publish-form.png)

   1. Het **de bevestigingsdialoog van Publish** verschijnt op het scherm, klik **Publish** beginnen te publiceren.

      ![ publiceer form1 ](/help/edge/docs/forms/assets/publish-form1.png)

      Zodra u de **knoop van Publish** klikt, verschijnt het `Publish started successfully` bericht.

      ![ publiceer form2 ](/help/edge/docs/forms/assets/publish-form2.png)

   U kunt nu de AEM pagina Project met de toegevoegde Edge Delivery ServicesVorm bij volgende URL bekijken:
   `https://<branch>--<repo>--<owner>.aem.page/content/<site-name>/`.

   Als de naam van de vertakking bijvoorbeeld `main` is, de opslagplaats `edsforms` is, de eigenaar `wkndforms` is en de naam van de site `eds-forms` is, is de URL:
   `https://main--edsforms--wkndforms.aem.page/content/eds-forms/`

   ![ indexpagina ](/help/edge/docs/forms/assets/publish-index-page.png)

U kunt de Edge Delivery Services Forms opmaken door `.css` en `.js` dossiers in het AanpassingsBlok van Forms en [ vestiging een lokale AEM ontwikkelomgeving ](#set-up-local-aem-development-environment) uit te geven om de veranderingen in uw browser onmiddellijk te bekijken.

## Lokale AEM ontwikkelomgeving instellen

U kunt een lokale AEM ontwikkelomgeving instellen voor het lokaal ontwikkelen van aangepaste stijlen en componenten. Aan de slag met een lokale AEM ontwikkelomgeving:

1. **installeer AEM CLI**: AEM CLI vereenvoudigt ontwikkelingstaken. Laten we het wereldwijd installeren met npm:

   ```Bash
       npm install -g @adobe/aem-cli
   ```

1. **Kloon uw project GitHub**: Kloon uw AEM bewaarplaats van het Project van GitHub gebruikend het volgende bevel, die vervangt <owner> met de eigenaar van de opslagplaats en <repo> met de naam van de opslagplaats:

   ```
   git clone https://github.com/<owner>/<repo>
   ```

1. **Begin Uw Lokaal Milieu**: Navigeer aan uw projectfolder en begin uw lokale AEM instantie met één enkel bevel:

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

<!-- * **Resolve Module Path Error:**
    If you encounter the error "Unable to resolve path to module "'../../scripts/lib-franklin.js'", navigate to the [EDS Project]/blocks/forms/form.js file. Update the import statement by replacing the lib-franklin.js file with the aem.js file. -->
