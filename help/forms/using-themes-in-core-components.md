---
title: Hoe kunnen we thema's maken en gebruiken in Adaptive Forms?
description: U kunt thema's gebruiken om een adaptief formulier op te maken en een visuele identiteit te geven met behulp van kerncomponenten. U kunt een thema delen voor elk gewenst aantal Adaptive Forms.
feature: Adaptive Forms, Core Components
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: 159407dfaa5d17caddca2953a5732f0e91eb474c
workflow-type: tm+mt
source-wordcount: '2708'
ht-degree: 0%

---

# Thema&#39;s in adaptieve Forms {#themes-for-af-using-core-components}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Dit artikel |

U kunt thema&#39;s maken en toepassen om een adaptief formulier op te maken. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Een thema wordt onafhankelijk beheerd zonder verwijzing naar een adaptief formulier en kan opnieuw worden gebruikt in meerdere Adaptieve Forms.

## Beschikbare thema&#39;s

Forms as Cloud Service biedt de onderstaande thema&#39;s voor op Core Components gebaseerde Adaptive Forms:

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

## Werken met de structuur van de thema&#39;s

Een thema is een pakket dat het CSS-bestand, JavaScript-bestanden en bronnen (zoals pictogrammen) omvat die de stijl van uw Adaptieve Forms definiëren. Het thema Adaptief formulier volgt op een specifieke organisatie, die bestaat uit de volgende onderdelen:

* `src/theme.scss`: Deze map bevat het CSS-bestand dat een grote invloed heeft op het hele thema. Het fungeert als een gecentraliseerde locatie voor het definiëren en beheren van de opmaak en het gedrag van uw thema. Door dit bestand te bewerken, kunt u wijzigingen aanbrengen die overal in het thema worden toegepast. Zo kunt u de vormgeving en functionaliteit van zowel de adaptieve Forms- als AEM Sites-pagina&#39;s wijzigen.

* `src/site`: Deze map bevat CSS-bestanden die worden toegepast op de gehele pagina van AEM site. Deze bestanden bestaan uit code en stijlen die van invloed zijn op de algemene functionaliteit en lay-out van de pagina van de AEM. Alle wijzigingen die u hier aanbrengt, worden doorgevoerd op alle pagina&#39;s van uw site. [Wanneer moet u het gebruiken?]

* `src/components`: De CSS-bestanden in deze map zijn ontworpen voor afzonderlijke AEM kerncomponenten. Elke specifieke map voor een component bevat een `.scss` bestand dat die component in een adaptief formulier opmaakt. Het bestand /src/components/accordion/_accordion.scss bevat bijvoorbeeld stijlgegevens voor de component Adaptive Forms Accordion.

  ![op een adaptief formulier gebaseerde themastructuur](/help/forms/assets/theme_structure.png)

* `src/resources`: Deze map bevat statische bestanden, zoals pictogrammen, logo&#39;s en lettertypen. Deze bronnen worden gebruikt om de visuele elementen en het algehele ontwerp van uw thema te verbeteren.

## Een thema maken

Forms as Cloud Service biedt de onderstaande thema&#39;s voor Core Components based Adaptive Forms.

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

U kunt [al deze thema&#39;s aanpassen om een nieuw thema te maken](#customize-a-theme-core-components).

![Workflow voor themaaanpassing](/help/forms/assets/workflow-of-customization-of-theme.png)

## Een thema aanpassen {#customize-a-theme-core-components}

Wanneer u een thema aanpast, wordt hiermee verwezen naar het wijzigen en aanpassen van de weergave van een thema. Wanneer u een thema aanpast, wijzigt u de ontwerpelementen, lay-out, kleuren, typografie en soms de onderliggende code. Hiermee kunt u een unieke en op maat gemaakte look voor uw website of toepassing maken met behoud van de basisstructuur en -functionaliteit die door het thema worden geboden.

### Vereisten {#prerequisites-to-customize}

* Verken uzelf met [een pijplijn instellen in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline) en het hebben van basiskennis van hoe te opstelling helpt een pijpleiding u efficiënt beheren en uw themaaanpassingen opstellen.
* Leer hoe u [een gebruiker configureren met de rol van contribuant](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html). Begrijpen hoe te om een gebruiker met de bijdragerrol te vormen laat u de noodzakelijke toestemmingen voor themaaanpassing verlenen.
* Installeer de nieuwste versie van [Apache Maven.](https://maven.apache.org/download.cgi) Apache Maven is een tool voor automatisering van build die veel wordt gebruikt voor Java™-projecten. De installatie van de recentste versie verzekert u de noodzakelijke gebiedsdelen voor themaaanpassing.
* Installeer een teksteditor zonder opmaak. Bijvoorbeeld Microsoft® Visual Studio Code. Het gebruiken van een gewone tekstredacteur zoals de Code van Microsoft® Visual Studio verstrekt een gebruikersvriendelijk milieu voor het uitgeven en het wijzigen van themadossiers.

### Uw omgeving instellen

* [Adaptieve Forms Core-componenten inschakelen](/help/forms/enable-adaptive-forms-core-components.md)  voor uw lokale ontwikkelings- en Cloud Service-omgeving.
* Configureren [front-end implementatiepijplijn](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) voor uw Cloud Service-omgeving. Alternatief, kunt u de pijpleiding vormen later, die u de flexibiliteit geven om aan het testen prioriteit te geven en het thema te verfijnen alvorens de plaatsingspijpleiding te vestigen.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Na het leren van de voorwaarden en het vormen van de ontwikkelomgeving, bent u bereid om te beginnen uw thema aan uw specifieke vereisten aanpassen.

### Een thema aanpassen {#steps-to-customize-a-theme-core-components}

Het aanpassen van een thema is een proces met meerdere stappen. Voer de stappen in de aangegeven volgorde uit om het thema aan te passen:

1. [Een thema klonen](#download-a-theme-core-components)
1. [Naam van thema instellen](#set-name-of-theme)
1. [Een thema aanpassen](#customize-the-theme)
1. [Een thema testen](#test-the-theme)
1. [Een thema implementeren](#deploy-the-theme)

De voorbeelden in het document zijn gebaseerd op de **Canvas** thema, maar het is belangrijk om op te merken dat u om het even welk thema kunt klonen en het aanpassen gebruikend de zelfde instructies. Deze instructies zijn van toepassing op elk thema, zodat u thema&#39;s kunt aanpassen aan uw specifieke behoeften.

#### 1. Een thema klonen {#download-a-theme-core-components}

Kies een van de volgende thema&#39;s om een thema voor op Core Components gebaseerde Adaptieve Forms te klonen:

* [Canvasthema](https://github.com/adobe/aem-forms-theme-canvas)
* [WKND-thema](https://github.com/adobe/aem-forms-theme-wknd)
* [EASEL-thema](https://github.com/adobe/aem-forms-theme-easel)

Voer de volgende instructies uit om een thema te klonen:

1. Open de opdrachtprompt of het terminalvenster in uw lokale ontwikkelomgeving.

1. Voer de `git clone` om een thema te klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Vervang de [Pad van Git Repository van het thema] met de werkelijke URL van de overeenkomstige Git Repository van het thema

   Als u bijvoorbeeld het thema Canvas wilt klonen, voert u de volgende opdracht uit:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Nadat de opdracht is uitgevoerd, beschikt u over een lokale kopie van het thema op uw computer in het dialoogvenster  `aem-forms-theme-canvas` map.


#### 2. Naam van thema instellen {#set-name-of-theme}

1. Open de themamap in een teksteditor zonder opmaak. Als u bijvoorbeeld het dialoogvenster `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio.

1. Ga naar de `aem-forms-theme-canvas` map.

1. Voer de volgende opdracht uit:

   ```
      code .
   ```

   ![De themamap openen in een teksteditor zonder opmaak](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   De omslag opent in de Code van Visual Studio.

1. Open de `package.json` bestand voor bewerking.

1. Stel de waarden in voor de `name` en `version` kenmerken.

   ![Wijziging van afbeelding van de naam van het canvasthema](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * Het kenmerk name wordt gebruikt om het thema op unieke wijze te identificeren en de opgegeven naam wordt weergegeven in het dialoogvenster **Stijl** tabblad van het **Wizard Formulier maken**.
   > * U kunt bijvoorbeeld een naam voor uw thema selecteren op basis van uw keuze `mytheme` of `customtheme`. In dit geval hebben we de naam echter opgegeven als `aem-forms-wknd-theme`.

1. Open de `package-lock.json` bestand voor bewerking.
1. Stel de waarden in voor de `name` en `version` kenmerken. Zorg ervoor dat de waarden voor de `name` en `version` kenmerken in de `Package-lock`.json-bestand komt overeen met de bestanden in het dialoogvenster `Package.json` bestand.

   ![Wijziging van afbeelding van de naam van het canvasthema](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (Optioneel) Open het dialoogvenster `ReadMe` bestand voor bewerken en bijwerken van de naam van het thema.

   ![Wijziging van afbeelding van de naam van het canvasthema](/help/forms/assets/changename_canvastheme-readme-file.png)

1. Sla de bestanden op en sluit ze.

**Overwegingen bij het instellen van de naam van het thema**

* Het is verplicht de `@aemforms` van de themanaam in `Package.json` en `Package-lock.json` bestand. In het geval dat u het bestand niet verwijdert `@aemforms` uit uw aangepaste themanaam, resulteert het in de mislukking van de frontend pijpleiding tijdens de themaplaatsing.
* Het wordt aanbevolen het thema bij te werken `version` in `Package.json` en `Package-lock.json` om wijzigingen en verbeteringen in de tijd voor uw thema nauwkeurig weer te geven.
* Voor de belangrijke informatie over het gebruik, de installatie-instructies en andere relevante details wordt aanbevolen de naam van het thema in het dialoogvenster `ReadMe` bestand.

#### 3. Een thema aanpassen {#customize-the-theme}

U kunt afzonderlijke componenten aanpassen of wijzigingen op themaniveau aanbrengen met algemene variabelen van een thema. Wijzigingen in algemene variabelen zijn van invloed op alle afzonderlijke componenten. U kunt bijvoorbeeld algemene variabelen gebruiken om de randkleur te wijzigen van alle componenten van een adaptief formulier en een heldere vulkleur om CTA (Call to action) in te stellen met behulp van knopcomponent:

* [Stijlen voor themaniveau instellen](#theme-customization-global-level)

* [Stijlen op componentniveau instellen](#component-based-customization)

##### Stijlen voor themaniveau instellen{#theme-customization-global-level}

De `variable.scss` Het bestand bevat de algemene themavariabelen. Door deze variabelen bij te werken, kunt u op themaniveau op stijl betrekking hebbende veranderingen aanbrengen. Voer de volgende stappen uit om stijlen op themaniveau toe te passen:

1. Open de `<your-theme-sources>/src/site/_variables.scss` bestand voor bewerking.
1. Wijzig de waarde van een willekeurige eigenschap. De standaardfoutkleur is bijvoorbeeld `red`. De foutkleur wijzigen van `red` tot `blue`wijzigt u de hexkleurcode van de `$errorvariable`. Bijvoorbeeld: `$error: #196ee5`.
1. Sla het bestand op en sluit het.

   ![Thema bewerken](/help/forms/assets/edit_theme.png)

U kunt ook de opdracht `variable.scss` bestand voor het instellen van lettertypefamilie en -type, thema- en lettertypekleuren, lettergrootte, themaspatiëring, foutpictogram, themarand en meer variabele die van invloed zijn op meerdere componenten van het adaptieve formulier.

##### Stijlen op componentniveau instellen {#component-based-customization}

U kunt ook het lettertype, de kleur, de grootte en andere CSS-eigenschappen wijzigen van een specifieke kerncomponent van Adaptief formulier. Bijvoorbeeld knop, selectievakje, container, voettekst en meer. U kunt een stijl op de knop of het selectievakje toepassen door het CSS-bestand van de specifieke component te bewerken en het uit te lijnen met de stijl van uw organisatie. Een stijl van een component aanpassen:

1. Het bestand openen `<your-theme-sources>/src/components/<component>/<component.scss>` voor bewerken. Als u bijvoorbeeld de lettertypekleur van de knopcomponent wilt wijzigen, opent u de knop `<your-theme-sources>/src/components/button/button.scss`, bestand.
1. Wijzig desgewenst de waarde van een object. Als u bijvoorbeeld de kleur van de knopcomponent wilt wijzigen wanneer u de muisaanwijzer verplaatst naar `green`wijzigt u de waarde van `color: $white` eigenschap in de `cmp-adaptiveform-button__widget:hover` klasse naar hexadecimale code `#12B453` of een andere vorm van `green`. De uiteindelijke code ziet er als volgt uit:

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Sla het bestand op en sluit het.

   ![CSS van tekstvak bewerken](/help/forms/assets/edit_color_textbox.png)

   >
   >
   > Wanneer een stijl zowel op thema als componentenniveau wordt bepaald, krijgt de stijl die op het componentenniveau wordt bepaald prioriteit.

#### 4. Test een aangepast thema {#test-the-theme}

Voer de volgende stappen uit om een voorvertoning van de wijzigingen in de lokale omgeving te bekijken en deze te testen en het thema aan te passen aan de vereisten voor verschillende AEM:

* 4,1 [Lokale omgeving configureren voor testen](#rename-env-file-theme-folder)
* 4,2 [Het thema testen in de lokale omgeving](#start-a-local-proxy-server)

##### 4.1. De lokale omgeving configureren voor testen {#rename-env-file-theme-folder}

1. Open de themamap in een teksteditor zonder opmaak. Open bijvoorbeeld de `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio.
1. De naam van de `env_template` bestand naar `.env` in de themamap en voeg de volgende parameters toe:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   De URL van het formulier is bijvoorbeeld `http://localhost:4502/editor.html/content/forms/af/contactusform.html`. De waarden van:

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Sla het bestand op.

   ![Structuur van canvasthema](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Het thema testen met behulp van de lokale omgeving {#start-a-local-proxy-server}

1. Navigeer naar de hoofdmap van de themamap. In dit geval is de naam van de themamap `aem-forms-theme-canvas`.
1. Open de opdrachtprompt of terminal.
1. Uitvoeren `npm install` om de gebiedsdelen te installeren.
1. Uitvoeren `npm run live` om een voorbeeld van het formulier weer te geven met het bijgewerkte thema in uw lokale browser.

   >[!NOTE]
   >
   > Als er een fout optreedt tijdens de uitvoering van de `npm run live` opdracht, voert de volgende opdrachten uit `npm run live` opdracht:
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

Dit is een hete implementatie. Dus wanneer u wijzigingen aanbrengt en de `_variables.scss` en `button.scss` bestanden selecteert de server automatisch de wijzigingen en geeft een voorvertoning weer van de meest recente uitvoer. De lijn `[Browsersync] File event [change]` Geeft aan dat de server de laatste wijzigingen heeft herkend en de wijzigingen in de lokale omgeving implementeert.

![Proxy browsersync](/help/forms/assets/browser_sync.png)

Nadat u de voorbeelden hebt gevolgd die zowel op themaniveau als op componentniveau voor themaaanpassingen worden geleverd, worden de foutberichten van een adaptief formulier gewijzigd in de `blue` kleur, terwijl de labelkleur voor de knopcomponent verandert in `green` bij het aanwijzen.

**Een voorbeeld weergeven van de stijl voor themaniveau**

![Voorbeeld: Foutkleur ingesteld op blauw](/help/forms/assets/theme-level-changes.png)

**Stijl op componentniveau voorvertonen**

![Voorbeeld: kleur aanwijzen ingesteld op groen](/help/forms/assets/button-customization.png)

###### Het thema testen voor formulieren die worden gehost in een Cloud Service-omgeving

U kunt ook het thema testen voor het adaptieve formulier dat wordt gehost op uw as a Cloud Service AEM Forms-exemplaar. Voer de volgende stappen uit om de lokale omgeving voor het testen van de thema&#39;s te configureren en in te stellen met de Adaptive Forms die wordt gehost op de cloudinstantie:

1. Open de themamap in een teksteditor zonder opmaak. Open bijvoorbeeld de `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio.
1. De naam van de `env_template` bestand naar `.env` en voeg de volgende parameters toe:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   De URL van het formulier in de cloud-omgeving is bijvoorbeeld `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html`. De waarden van:

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Sla het bestand op.
1. Maak een lokale gebruiker.

   >[!NOTE]
   >
   > Een lokale gebruiker maken:
   >
   > * Ga naar **[!UICONTROL AEM Home]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** .
   > * Zorg ervoor dat de gebruiker lid is van de `forms-users` groep.

1. Navigeer naar de hoofdmap van de themamap. In dit geval is de naam van de themamap `aem-forms-theme-canvas`.
1. Uitvoeren `npm run live` en u wordt omgeleid naar een lokale browser.
1. Klikken `SIGN IN LOCALLY (ADMIN TASKS ONLY)` en aanmelden met de lokale gebruikersgegevens.

U kunt een voorbeeld van het adaptieve formulier bekijken met de meest recente wijzigingen. Zodra, bent u tevreden met de wijzigingen die in een themamap worden gedaan, stel het thema aan uw milieu van AEM Cloud Service gebruikend de front-end pijpleiding op.

#### 5. Een thema gebruiken {#deploy-the-theme}

Om het thema aan uw milieu van de Cloud Service op te stellen gebruikend de front-end pijpleiding:

* 5,1 [Een opslagplaats voor thema maken](#create-a-new-theme-repo)
* 5,2 [De wijzigingen in de opslagplaats doorvoeren](#committing-the-changes)
* 5,3 [De frontend pijpleiding in werking stellen](#run-a-frontend-pipeline)

##### 5.1 Een opslagplaats voor thema maken{#create-a-new-theme-repo}

U hebt een opslagplaats nodig om het thema te implementeren. Aanmelden bij uw [AEM Cloud Manager-opslagplaats](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) en voeg nieuwe opslagplaats voor uw thema toe.

1. Nieuwe opslagplaats voor thema&#39;s maken door op de knop **[!UICONTROL Repositories]** > **[!UICONTROL Add Repository]**.

   ![nieuwe themarepo maken](/help/forms/assets/createrepo_canvastheme.png)


1. Geef de **Naam opslagplaats** in de **Opslagplaats toevoegen** in. De opgegeven naam is bijvoorbeeld `custom-canvas-theme-repo`.
1. Klik op **[!UICONTROL Save]**.

   ![Repo Canvasthema toevoegen](/help/forms/assets/addcanvasthemerepo.png)

1. Klikken **[!UICONTROL Copy Repository URL]** om de URL van de repository te kopiëren.

   ![URL van Canvasthema](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * U kunt één opslagplaats voor meerdere thema&#39;s gebruiken.
   > * Om verschillende thema&#39;s op te stellen, moet u afzonderlijke front-end pijpleidingen tot stand brengen.
   >* U kunt bijvoorbeeld dezelfde gegevensopslagruimte gebruiken als `custom-canvas-theme-repo`, voor Canvas-thema, WKND-thema en EASEL-thema. Als u de thema&#39;s echter wilt implementeren, moet u aparte front-end pijpleidingen maken. De toekomstige aanpassingen voor een specifiek thema worden opgesteld gebruikend de overeenkomstige front-end pijpleiding.

##### 5.2. Verhoog de wijzigingen in de gegevensopslagruimte {#committing-the-changes}

Breng nu de wijzigingen aan in de themaopslagplaats van uw AEM Forms-Cloud Service.

1. Navigeer naar de hoofdmap van de themamap.  In dit geval is de naam van de themamap `aem-forms-theme-canvas`.
1. Open de opdrachtprompt of terminal.
1. Voer de volgende opdracht in de vermelde volgorde uit:

   ```
   git remote add [alias-name-for-repository] [URL of repository]
   git add .
   git commit
   git push [name-for-createdrepository]
   ```

   Bijvoorbeeld:

   ```
   git remote add canvascloudthemerepo https://git.cloudmanager.adobe.com/stage-aemformsdev/customcanvastheme/
   git add .
   git commit
   git push canvascloudthemerepo 
   ```

   ![Toegestane wijzigingen](/help/forms/assets/cmd_git_push.png)



##### 5.3 Loop de frontend pijpleiding {#run-a-frontend-pipeline}

Het thema wordt opgesteld gebruikend [pijpleiding aan de voorzijde.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). Voer de volgende stappen uit om thema te implementeren:

1. Meld u aan bij de AEM Cloud Manager-opslagplaats.
1. Klikken **[!UICONTROL Add]** van de knop **[!UICONTROL Pipelines]** sectie.
1. Selecteren **[!UICONTROL Add Non-Production Pipeline]** of **[!UICONTROL Add Production Pipeline]** op basis van de omgeving van de Cloud Service. Hier kunt u bijvoorbeeld de **[!UICONTROL Add Production Pipeline]** is geselecteerd.
1. In de **[!UICONTROL Add Production Pipeline]** als onderdeel van de **[!UICONTROL Configuration]** stappen, specificeer naam voor uw pijpleiding. De naam van de pijplijn is bijvoorbeeld `customcanvastheme`.
1. Klik op **[!UICONTROL Continue]**.
1. Selecteer de **[!UICONTROL Targeted Deployment]** > de **[!UICONTROL Front-end code]** opties, in de **[!UICONTROL Source Code]** stappen.
1. Selecteer de **[!UICONTROL Repository]** en de **[!UICONTROL Git Branch]** waarden met de meest recente wijzigingen. Hier is bijvoorbeeld de naam van de geselecteerde opslagplaats `custom-canvas-theme-repo` en de Git-vertakking is `main`.
1. Selecteer de **[!UICONTROL Code Location]** als `/`, als de wijzigingen aanwezig zijn in de hoofdmap.
1. Klik op **[!UICONTROL Save]**.
   ![front-endpijpleiding maken](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Nadat de pijpleidingsopstelling volledig is, wordt de vraag-aan-actie kaart bijgewerkt.

1. Klik de gecreeerde pijpleiding met de rechtermuisknop aan.
1. Klikken **[!UICONTROL Run]** .

   ![run-a-pipleine](/help/forms/assets/canvas-theme-run-pipeline.png)

Zodra de bouwstijl volledig is, wordt het thema beschikbaar bij de auteursinstantie voor het gebruik. Het verschijnt onder de **[!UICONTROL Style]** in de wizard Adaptief formulier maken, terwijl u een adaptief formulier maakt.

![aangepast thema beschikbaar onder tabblad Stijl](/help/forms/assets/custom-theme-style-tab.png)

## Een thema toepassen op een adaptief formulier {#using-theme-in-adaptive-form}

De stappen voor het toepassen van een thema op een adaptief formulier zijn:

1. Meld u aan bij de AEM Forms-auteur.

1. Selecteren **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Klikken **Maken** > **Adaptieve Forms**. De wizard voor het maken van adaptief formulier wordt geopend.

1. Selecteer de sjabloon voor de kerncomponent in het dialoogvenster **Bron** tab.
1. Selecteer het thema in het dialoogvenster **Stijl** tab.
1. Klikken **Maken**.

De thema&#39;s Adaptief formulier worden gebruikt als onderdeel van een adaptieve formuliersjabloon om opmaak te definiëren terwijl u een adaptief formulier maakt.

## Aanbevolen procedures {#best-practices}

* **Elementen uit een ander thema verwijderen**

  Wanneer u een thema bewerkt, kunt u door elementen (zoals afbeeldingen) bladeren en elementen uit andere thema&#39;s toevoegen. U bewerkt bijvoorbeeld de achtergrond van een pagina. Wanneer u bijvoorbeeld **[!UICONTROL Page]** ![bewerken, knop](assets/edit-button.png)> **[!UICONTROL Background]** > **[!UICONTROL Add]** > **[!UICONTROL Image]** Er wordt dan een dialoogvenster weergegeven waarin u door afbeeldingen in andere thema&#39;s kunt bladeren en deze kunt toevoegen.

  U kunt problemen met uw huidige thema oplossen als een element wordt toegevoegd uit een ander thema en het andere thema wordt verplaatst of verwijderd. U wordt aangeraden te voorkomen dat u bladeren en elementen uit andere thema&#39;s toevoegt.

* **De lay-outbreedte van het containervenster wijzigen**

  Het wordt niet aanbevolen de lay-outbreedte van het containervenster te wijzigen. Wanneer u de breedte van een containerdeelvenster opgeeft, wordt het statisch en wordt het niet aangepast aan verschillende weergaven.

* **Formuliereditor of themaeditor gebruiken voor het werken met kop- en voettekst**

  Gebruik de themaeditor als u koptekst en voettekst wilt opmaken met opmaakopties zoals lettertypestijl, achtergrond en transparantie.
Gebruik de opties voor de formuliereditor als u informatie wilt opgeven, zoals een logoafbeelding, een bedrijfsnaam in de koptekst en copyrightinformatie in de voettekst.

## Veelgestelde vragen {#faq}

**V:** Welke aanpassing neemt prioriteit wanneer het maken van aanpassingen in een themamap op zowel het globale niveau als componentenniveau?

**Ans:** Wanneer aanpassingen op zowel het globale niveau als componentenniveau worden gemaakt, neemt de aanpassing op het componentenniveau prioriteit.

<!--

## See next

* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generate Document of Record for Adaptive Forms (Core Components](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Create an Adaptive Forms with Repeatable sections](/help/forms/create-forms-repeatable-sections.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)


>[!MORELIKETHIS]
>
>* [Enable Adaptive Forms Core Components on AEM Forms as a Cloud Service and local development environment](/help/forms/enable-adaptive-forms-core-components.md)

-->


## Zie ook {#see-also}

{{see-also}}
* [Formulierindeling instellen voor verschillende schermgrootten en apparaattypen](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Document met record genereren voor adaptieve Forms (kerncomponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Een adaptieve Forms maken met herhalende secties](/help/forms/create-forms-repeatable-sections.md)
* [Voorbeeldthemasjablonen en formuliergegevensmodellen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
* [Adaptieve Forms Core-componenten inschakelen in de as a Cloud Service en lokale ontwikkelomgeving van AEM Forms](/help/forms/enable-adaptive-forms-core-components.md)
