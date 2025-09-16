---
title: Hoe kunt u thema's maken en gebruiken in Adaptive Forms?
description: Met thema's kunt u een adaptief formulier vormgeven en een visuele identiteit geven met behulp van Core Components. U kunt een thema delen voor elk gewenst aantal Adaptive Forms.
keywords: thema's voor formulierbuilders, adaptieve formulieren opmaken, kerncomponenten, formulierontwerper, opmaken, adaptief formulier, thema's aanpassen, formulierthema's maken
feature: Adaptive Forms, Core Components
role: User, Developer
exl-id: 11c52b66-dbb1-4c47-a94d-322950cbdac1
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '2760'
ht-degree: 0%

---

# Thema&#39;s gebruiken om de stijl van op Core Components gebaseerde Adaptive Forms te bepalen{#themes-for-af-using-core-components}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-core-components/create-or-customize-themes-for-adaptive-forms-core-components.html) |
| AEM as a Cloud Service | Dit artikel |

U kunt thema&#39;s maken en toepassen om een adaptief formulier op te maken. Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten. Een thema wordt onafhankelijk beheerd zonder verwijzing naar een adaptief formulier en kan opnieuw worden gebruikt in meerdere Adaptieve Forms.

In dit artikel begrijpen we hoe we aangepaste ontwerpen kunnen maken voor op Core Component gebaseerde Adaptive Forms met gebruik van thema&#39;s.

## Beschikbare thema&#39;s voor de opmaak van kerncomponenten

Forms as Cloud Service biedt de volgende thema&#39;s voor op Core Components gebaseerde Adaptive Forms:

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)

## Werken met de structuur van de thema&#39;s

Een thema is een pakket met opmaakcomponenten zoals CSS-bestanden, JavaScript-bestanden en bronnen (zoals pictogrammen) die de stijl van uw Adaptieve Forms definiëren. Het thema Adaptief formulier volgt op een specifieke organisatie, die bestaat uit de volgende onderdelen:

* `src/theme.scss`: Deze map bevat het CSS-bestand dat een grote invloed heeft op het hele thema. Het fungeert als een gecentraliseerde locatie voor het definiëren en beheren van de opmaak en het gedrag van uw thema. Door dit bestand te bewerken, kunt u wijzigingen aanbrengen die overal in het thema worden toegepast. Zo kunt u de vormgeving en functionaliteit van zowel de adaptieve Forms- als AEM Sites-pagina&#39;s wijzigen.

* `src/site`: Deze map bevat CSS-bestanden die worden toegepast op de hele pagina van de AEM-site. Deze bestanden bestaan uit code en stijlen die de algemene functionaliteit en lay-out van de pagina van uw AEM-site beïnvloeden. Alle wijzigingen die u hier aanbrengt, worden doorgevoerd op alle pagina&#39;s van uw site. [ wanneer om het te gebruiken?]

* `src/components`: De CSS-bestanden in deze map zijn ontworpen voor afzonderlijke AEM-kerncomponenten. Elke toegewijde map voor een component bevat een `.scss` -bestand waarmee die component in een adaptief formulier wordt geformatteerd. Het bestand /src/components/accordion/_accordion.scss bevat bijvoorbeeld stijlgegevens voor de component Adaptive Forms Accordion.

  ![ adaptieve vorm gebaseerde themastructuur ](/help/forms/assets/theme_structure.png)

* `src/resources`: deze map bevat statische bestanden, zoals pictogrammen, logo&#39;s en lettertypen. Deze bronnen worden gebruikt om de visuele elementen en het algehele ontwerp van uw thema te verbeteren.

## Een thema maken

Forms as Cloud Service biedt de onderstaande Adaptive Form styling-thema&#39;s voor op Core Components gebaseerde Adaptive Forms.

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)

U kunt [ om het even welk van deze thema&#39;s aanpassen om nieuw thema ](#customize-a-theme-core-components) tot stand te brengen.

![ Werkschema van themaaanpassing ](/help/forms/assets/workflow-of-customization-of-theme.png)

## Een thema aanpassen {#customize-a-theme-core-components}

Wanneer u een thema aanpast, wordt hiermee verwezen naar het wijzigen, opmaken en aanpassen van de weergave van een thema. Wanneer u een thema aanpast, wijzigt u de ontwerpelementen, lay-out, kleuren, typografie en soms de onderliggende code. Hiermee kunt u een unieke en op maat gemaakte look voor uw website of toepassing maken met behoud van de basisstructuur en -functionaliteit die door het thema worden geboden.

### Vereisten {#prerequisites-to-customize}

* Verken zelf met [ vestiging een pijpleiding in Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#setup-pipeline) en het hebben van basiskennis van hoe te opstelling helpt u efficiënt uw themaaanpassingen beheren en opstellen.
* Leer hoe te [ een gebruiker met de bijdragerrol ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/assign-profiles-aem.html) vormen. Begrijpen hoe te om een gebruiker met de bijdragerrol te vormen laat u de noodzakelijke toestemmingen voor themaaanpassing verlenen.
* Installeer de recentste versie van [ Apache Maven ](https://maven.apache.org/download.cgi). Apache Maven is een tool voor automatisering van build die veel wordt gebruikt voor Java™-projecten. De installatie van de recentste versie verzekert u de noodzakelijke gebiedsdelen voor themaaanpassing.
* Installeer een teksteditor zonder opmaak. Bijvoorbeeld Microsoft® Visual Studio Code. Het gebruiken van een gewone tekstredacteur zoals de Code van Microsoft® Visual Studio verstrekt een gebruikersvriendelijk milieu voor het uitgeven en het wijzigen van themadossiers.

### Uw omgeving instellen

* Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.
* Vorm a [ front-end plaatsingspijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html) voor uw milieu van Cloud Service. Alternatief, kunt u de pijpleiding vormen later, die u de flexibiliteit geven om aan het testen prioriteit te geven en het thema te verfijnen alvorens de plaatsingspijpleiding te vestigen.

<!-- 
To deploy your themes to a Forms as a Cloud Service environment, first test theme on a local development environment to address any issues. Once the theme is tested, configure the front-end deployment pipeline, which is responsible for deploying the themes.

These themes are deployed to a Forms as a Cloud Service environment via the front-end pipeline. You can configure the pipeline later also, after testing the theme on a local development environment. 

-->

Na het leren van de vereisten en het vormen van de ontwikkelomgeving, bent u bereid om te beginnen uw thema aan te passen of te stileren volgens uw specifieke vereisten.

### Een thema aanpassen {#steps-to-customize-a-theme-core-components}

Het aanpassen van een thema is een proces met meerdere stappen. Voer de stappen in de aangegeven volgorde uit om het thema aan te passen:

1. [ Kloon een thema ](#download-a-theme-core-components)
1. [Naam van thema instellen](#set-name-of-theme)
1. [Een thema aanpassen](#customize-the-theme)
1. [Een thema testen](#test-the-theme)
1. [Een thema implementeren](#deploy-the-theme)

De voorbeelden die in het document worden verstrekt zijn gebaseerd op het **&#x200B;**&#x200B;thema van het Canvas, maar het is belangrijk om op te merken dat u om het even welk thema kunt klonen en het aanpassen gebruikend de zelfde instructies. Deze instructies zijn van toepassing op elk thema, zodat u thema&#39;s kunt aanpassen aan uw specifieke behoeften.

Laten we beginnen met een proces om een merkervaring te maken voor de Adaptieve Forms op basis van uw Core-component met gebruik van thema&#39;s.

#### &#x200B;1. Een thema klonen {#download-a-theme-core-components}

Kies een van de volgende thema&#39;s om een thema voor op Core Components gebaseerde Adaptieve Forms te klonen:

* [ het thema van Canvas ](https://github.com/adobe/aem-forms-theme-canvas)
* [ WKND thema ](https://github.com/adobe/aem-forms-theme-wknd)
* [ EASEL thema ](https://github.com/adobe/aem-forms-theme-easel)

Voer de volgende instructies uit om een thema te klonen:

1. Open de opdrachtprompt of het terminalvenster in uw lokale ontwikkelomgeving.

1. Voer de opdracht `git clone` uit om een thema te klonen.

   ```
      git clone [Path of Git Repository of the theme]
   ```

   Vervang het [ Weg van de Bewaarplaats van het Git van het thema ] met daadwerkelijke URL van de overeenkomstige Bewaarplaats van het Git van het thema

   Als u bijvoorbeeld het thema Canvas wilt klonen, voert u de volgende opdracht uit:

   ```
      git clone https://github.com/adobe/aem-forms-theme-canvas
   ```

   Nadat de opdracht is uitgevoerd, beschikt u over een lokale kopie van het thema op uw computer in de map `aem-forms-theme-canvas` .


#### &#x200B;2. Naam van thema instellen {#set-name-of-theme}

1. Open de themamap in uw winde. Bijvoorbeeld, om de `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio te openen.

1. Navigeer naar de map `aem-forms-theme-canvas` .

1. Voer de volgende opdracht uit:

   ```
      code .
   ```

   ![ open de themamap in een gewone tekstredacteur ](/help/forms/assets/aem-forms-theme-folder-in-vs-code.png)

   De omslag opent in de Code van Visual Studio.

1. Open het `package.json` -bestand om het te bewerken.

1. Stel de waarden in voor de kenmerken `name` en `version` .

   ![ de naamverandering van het Thema van het Canvas beeld ](/help/forms/assets/changename_canvastheme.png)

   >[!NOTE]
   >
   > * Het naamattribuut wordt gebruikt om het thema uniek te identificeren, en de gespecificeerde naam wordt getoond in het **lusje van de Stijl** van de **Tovenaar van de Aanmaak van de Vorm**.
   > * U kunt desgewenst een naam voor het thema selecteren, bijvoorbeeld `mytheme` of `customtheme` . In dit geval hebben we de naam echter opgegeven als `aem-forms-wknd-theme` .

1. Open het `package-lock.json` -bestand om het te bewerken.
1. Stel de waarden in voor de kenmerken `name` en `version` . Zorg ervoor dat de waarden voor de kenmerken `name` en `version` in het bestand `Package-lock` .json overeenkomen met die in het bestand `Package.json` .

   ![ de naamverandering van het Thema van het Canvas beeld ](/help/forms/assets/changename_canvastheme-package-lock.png)

1. (Optioneel) Open het `ReadMe` -bestand om het te bewerken en werk de naam van het thema bij.

   ![ de naamverandering van het Thema van het Canvas beeld ](/help/forms/assets/changename_canvastheme-readme-file.png)

1. Sla de bestanden op en sluit ze.

**Overwegingen terwijl het plaatsen van de naam van het thema**

* Het is verplicht om `@aemforms` te verwijderen uit de themanaam in `Package.json` bestand en `Package-lock.json` bestand. Als u `@aemforms` niet kunt verwijderen uit uw aangepaste themanaam, resulteert dit in de fout van de frontend-pijplijn tijdens de themaimplementatie.
* U wordt aangeraden het thema `version` in het `Package.json` -bestand en het `Package-lock.json` -bestand bij te werken om wijzigingen en verbeteringen in de tijd voor uw thema nauwkeurig weer te geven.
* Voor de belangrijke informatie over het gebruik, de installatie-instructies en andere relevante details wordt aangeraden de naam van het thema in het `ReadMe` -bestand bij te werken.

#### &#x200B;3. Een thema aanpassen {#customize-the-theme}

U kunt afzonderlijke componenten aanpassen of wijzigingen op themaniveau aanbrengen met algemene variabelen van een thema. Wijzigingen in algemene variabelen zijn van invloed op alle afzonderlijke componenten. Met algemene variabelen kunt u bijvoorbeeld de randkleur wijzigen van alle componenten van een adaptief formulier en een heldere vulkleur om CTA (Call to action) in te stellen met behulp van een knopcomponent:

* [Stijlen voor themaniveau instellen](#theme-customization-global-level)

* [Stijlen op componentniveau instellen](#component-based-customization)

##### Stijlen voor themaniveau instellen{#theme-customization-global-level}

Het bestand `variable.scss` bevat de algemene themavariabelen. Door deze variabelen bij te werken, kunt u op themaniveau op stijl betrekking hebbende veranderingen aanbrengen. Voer de volgende stappen uit om stijlen op themaniveau toe te passen:

1. Open het `<your-theme-sources>/src/site/_variables.scss` -bestand om het te bewerken.
1. Wijzig de waarde van een willekeurige eigenschap. De standaardfoutkleur is bijvoorbeeld `red` . Als u de foutkleur wilt wijzigen van `red` in `blue` , wijzigt u de hexadecimale kleurcode van de `$errorvariable` . Bijvoorbeeld `$error: #196ee5` .
1. Sla het bestand op en sluit het.

   ![ geef thema ](/help/forms/assets/edit_theme.png) uit

Op dezelfde manier kunt u het bestand `variable.scss` gebruiken om lettertypefamilie en -type, thema- en lettertypekleuren, lettergrootte, themaspatiëring, foutpictogram, themarand en meer variabele in te stellen die van invloed zijn op meerdere componenten van het adaptieve formulier.

##### Stijlen op componentniveau instellen {#component-based-customization}

U kunt ook het lettertype, de kleur, de grootte en andere CSS-eigenschappen wijzigen van een specifieke kerncomponent van Adaptief formulier. Bijvoorbeeld knop, selectievakje, container, voettekst en meer. U kunt een knop of selectievakje opmaken door het CSS-bestand van de specifieke component te bewerken en deze uit te lijnen met de stijl van uw organisatie. Een stijl van een component aanpassen:

1. Open het bestand `<your-theme-sources>/src/components/<component>/<component.scss>` voor bewerking. Als u bijvoorbeeld de lettertypekleur van de knopcomponent wilt wijzigen, opent u het bestand `<your-theme-sources>/src/components/button/button.scss` .
1. Wijzig desgewenst de waarde van een object. Als u bijvoorbeeld de kleur van de component Button bij de muisaanwijzer wilt wijzigen in `green` , wijzigt u de waarde van de eigenschap `color: $white` in de klasse `cmp-adaptiveform-button__widget:hover` in hexadecimale code `#12B453` of een andere tint van `green` . De uiteindelijke code ziet er als volgt uit:

   ```
   .cmp-adaptiveform-button__widget:hover {
   background: $dark-gray;
   color: #12B453;
   }
   ```

1. Sla het bestand op en sluit het.

   ![ geeft CSS TextBox uit ](/help/forms/assets/edit_color_textbox.png)

   >
   >
   > Wanneer een stijl zowel op het thema als componentenniveau wordt bepaald, krijgt de stijl die op het componentenniveau wordt bepaald voorrang.

#### &#x200B;4. Test een aangepast thema {#test-the-theme}

Voer de volgende stappen uit om een voorvertoning van de wijzigingen in de lokale omgeving weer te geven en deze te testen en het thema aan te passen aan de vereisten voor verschillende AEM-componenten:

* 4.1 [ vorm een lokaal milieu voor het testen ](#rename-env-file-theme-folder)
* 4.2 [ Test het thema gebruikend het lokale milieu ](#start-a-local-proxy-server)

##### 4.1. Een lokale omgeving configureren voor testen {#rename-env-file-theme-folder}

1. Open de themamap in uw winde. Bijvoorbeeld, open de `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio.
1. Wijzig de naam van het `env_template` -bestand in `.env` -bestand in de themamap en voeg de volgende parameters toe:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   De URL van het formulier is bijvoorbeeld `http://localhost:4502/editor.html/content/forms/af/contactusform.html` . De waarden van:

   * AEM_URL = `http://localhost:4502/`
   * AEM_ADAPTIVE_FORM = `contactusform`

1. Sla het bestand op.

   ![ Structuur van het Thema van Canvas ](/help/forms/assets/env-file-canvas-theme.png)

##### 4.2 Het thema testen met een lokale omgeving {#start-a-local-proxy-server}

1. Navigeer naar de hoofdmap van de themamap. In dit geval is de naam van de themamap `aem-forms-theme-canvas` .
1. Open de opdrachtprompt of terminal.
1. Voer `npm install` uit om de afhankelijkheden te installeren.
1. Voer `npm run live` uit om een voorbeeld van het formulier weer te geven met het bijgewerkte thema in uw lokale browser.

   >[!NOTE]
   >
   > Als een fout optreedt tijdens de uitvoering van de opdracht `npm run live` , voert u de volgende opdrachten uit vóór de opdracht `npm run live` :
   >
   > * `npm install parcel --save-dev`
   > * `npm i @parcel/transformer-sass`

Dit is een hete implementatie. Als u dus wijzigingen aanbrengt en de `_variables.scss` - en `button.scss` -bestanden opslaat, selecteert de server automatisch de wijzigingen en geeft een voorvertoning van de meest recente uitvoer weer. De regel `[Browsersync] File event [change]` geeft aan dat de server de laatste wijzigingen heeft herkend en de wijzigingen implementeert in de lokale omgeving.

![ Proxy browserSync ](/help/forms/assets/browser_sync.png)

Nadat u de voorbeelden hebt gevolgd voor het opmaken van een adaptief formulier (kerncomponenten) op themaniveau en componentniveau voor themaaanpassingen, worden de foutberichten van een adaptief formulier gewijzigd in de `blue` -kleur, terwijl de labelkleur van de knopcomponent bij aanwijzen verandert in `green` .

**Previewing de stijl van het themaniveau**

![ Voorbeeld: De kleur van de fout die aan blauw wordt geplaatst ](/help/forms/assets/theme-level-changes.png)

**Previewing de stijl van het componentenniveau**

![ Voorbeeld: De kleur van de omslag die aan groen ](/help/forms/assets/button-customization.png) wordt geplaatst

Als u een thema aanpast, kunt u het aangepaste ontwerp gebruiken om de op Core Component gebaseerde Adaptieve Forms te zoeken op basis van de organisatorische vereisten.

###### Het thema testen voor formulieren die worden gehost in een Cloud Service-omgeving

U kunt ook het thema testen voor het adaptieve formulier dat wordt gehost op uw AEM Forms as a Cloud Service-exemplaar. Voer de volgende stappen uit om de lokale omgeving voor het testen van de thema&#39;s te configureren en in te stellen met de Adaptive Forms die wordt gehost op de cloudinstantie:

1. Open de themamap in uw winde. Bijvoorbeeld, open de `aem-forms-theme-canvas` omslag in de redacteur van de Code van Visual Studio.
1. Wijzig de naam van het `env_template` -bestand in `.env` -bestand en voeg de volgende parameters toe:

   ```
   * **AEM url**
   AEM_URL=https://[author-instance] 
   
   * **AEM Adaptive form name**
   AEM_ADAPTIVE_FORM=Form_name
   
   * **AEM proxy port**
   AEM_PROXY_PORT=7000
   ```

   De URL van het formulier in de cloud-omgeving is bijvoorbeeld `https://author-XXXX.adobeaemcloud.com/editor.html/content/forms/af/contactusform.html` . De waarden van:

   * AEM_URL = `https://author-XXXX-cmstg.adobeaemcloud.com/`
   * AEM_ADAPTIVE_FORM = `contactusform`
1. Sla het bestand op.
1. Maak een lokale gebruiker.

   >[!NOTE]
   >
   > Een lokale gebruiker maken:
   >
   > * Ga naar **[!UICONTROL AEM Home]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** .
   > * Controleer of de gebruiker lid is van de groep `forms-users` .

1. Navigeer naar de hoofdmap van de themamap. In dit geval is de naam van de themamap `aem-forms-theme-canvas` .
1. Voer `npm run live` uit en u wordt omgeleid naar een lokale browser.
1. Klik op `SIGN IN LOCALLY (ADMIN TASKS ONLY)` en meld u aan met de lokale gebruikersgegevens.

U kunt een voorbeeld van het adaptieve formulier bekijken met de meest recente wijzigingen. Zodra, bent u tevreden met de wijzigingen die in een themamap worden gedaan, stel het thema aan uw milieu van de Dienst van de Wolk AEM gebruikend de front-end pijpleiding op.

#### &#x200B;5. Een thema gebruiken {#deploy-the-theme}

Om het thema aan uw milieu van Cloud Service op te stellen gebruikend de front-end pijpleiding:

* 5.1 [ creeer een bewaarplaats voor thema ](#create-a-new-theme-repo)
* 5.2 [ duw de veranderingen in de bewaarplaats ](#committing-the-changes)
* 5.3 [ stel de frontend pijpleiding ](#run-a-frontend-pipeline) in werking

##### 5.1 Een opslagplaats voor thema maken{#create-a-new-theme-repo}

U hebt een opslagplaats nodig om het thema te implementeren. Login aan uw [ bewaarplaats van AEM Cloud Manager ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html#accessing-git) en voeg nieuwe bewaarplaats voor uw thema toe.

1. Maak een nieuwe opslagplaats voor een thema door op **[!UICONTROL Repositories]** > **[!UICONTROL Add Repository]** te klikken.

   ![ creeer nieuwe themarepo ](/help/forms/assets/createrepo_canvastheme.png)


1. Specificeer de **Naam van de Bewaarplaats** in **voeg de dialoogdoos van de Bewaarplaats** toe. De opgegeven naam is bijvoorbeeld `custom-canvas-theme-repo` .
1. Klik op **[!UICONTROL Save]**.

   ![ voeg de Repo van het Thema van het Canvas ](/help/forms/assets/addcanvasthemerepo.png) toe

1. Klik op **[!UICONTROL Copy Repository URL]** om de URL van de gegevensopslagruimte te kopiëren.

   ![ het thema URL van het Canvas ](/help/forms/assets/copyurl_canvastheme.png)

   >[!NOTE]
   > 
   > * U kunt één opslagplaats voor meerdere thema&#39;s gebruiken.
   > * Om verschillende thema&#39;s op te stellen, moet u afzonderlijke front-end pijpleidingen tot stand brengen.
   >* U kunt bijvoorbeeld dezelfde gegevensopslagruimte gebruiken als `custom-canvas-theme-repo` voor Canvas-thema, WKND-thema en EASEL-thema. Als u de thema&#39;s echter wilt implementeren, moet u aparte front-end pijpleidingen maken. De toekomstige aanpassingen voor een specifiek thema worden opgesteld gebruikend de overeenkomstige front-end pijpleiding.

##### 5.2. Verhoog de wijzigingen in de gegevensopslagruimte {#committing-the-changes}

Breng nu de wijzigingen aan in de themaopslagplaats van uw AEM Forms Cloud Service.

1. Navigeer naar de hoofdmap van de themamap.  In dit geval is de naam van de themamap `aem-forms-theme-canvas` .
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

   ![ Gecommitteerde Veranderingen ](/help/forms/assets/cmd_git_push.png)



##### 5.3 Loop de frontend pijpleiding {#run-a-frontend-pipeline}

Het thema wordt opgesteld gebruikend de [ front-end pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/enable-frontend-pipeline-devops/create-frontend-pipeline.html). Voer de volgende stappen uit om thema te implementeren:

1. Meld u aan bij uw AEM Cloud Manager-opslagplaats.
1. Klik op de knop **[!UICONTROL Add]** in de sectie **[!UICONTROL Pipelines]** .
1. Selecteer **[!UICONTROL Add Non-Production Pipeline]** of **[!UICONTROL Add Production Pipeline]** in de Cloud Service-omgeving. Hier is bijvoorbeeld de optie **[!UICONTROL Add Production Pipeline]** geselecteerd.
1. Geef in het dialoogvenster **[!UICONTROL Add Production Pipeline]** de naam voor de pijplijn op als onderdeel van de stappen van **[!UICONTROL Configuration]** . De naam van de pijplijn is bijvoorbeeld `customcanvastheme` .
1. Klik op **[!UICONTROL Continue]**.
1. Selecteer de opties **[!UICONTROL Targeted Deployment]** > **[!UICONTROL Front-end code]** in
de **[!UICONTROL Source Code]** stappen.
1. Selecteer de waarden **[!UICONTROL Repository]** en **[!UICONTROL Git Branch]** die de meest recente wijzigingen hebben ondergaan. Hier is de geselecteerde naam van de opslagplaats bijvoorbeeld `custom-canvas-theme-repo` en is de Git-vertakking `main` .
1. Selecteer **[!UICONTROL Code Location]** als `/` als de wijzigingen aanwezig zijn in de hoofdmap.
1. Klik op **[!UICONTROL Save]**.
   ![ creeer front-endpipe ](/help/forms/assets/canvas-theme-frontendpipeline.gif)

   Nadat de pijplijnopstelling volledig is, wordt de kaart van call-to-action bijgewerkt.

1. Klik de gecreeerde pijpleiding met de rechtermuisknop aan.
1. Klik op **[!UICONTROL Run]** .

   ![ looppas-a-pipleine ](/help/forms/assets/canvas-theme-run-pipeline.png)

Zodra de bouwstijl volledig is, wordt het thema beschikbaar bij de auteursinstantie voor het gebruik. Deze wordt weergegeven onder het tabblad **[!UICONTROL Style]** in de wizard Adaptief formulier bij het maken van een adaptief formulier.

![ douanethema beschikbaar onder stijllusje ](/help/forms/assets/custom-theme-style-tab.png)

Het aangepaste thema helpt bij het maken van een merkervaring voor op Core Component gebaseerde Adaptive Forms.

## Een thema toepassen op een adaptief formulier {#using-theme-in-adaptive-form}

De stappen voor het toepassen van een thema op een adaptief formulier zijn:

1. Meld u aan bij de AEM Forms-auteur.

1. Selecteer **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.

1. Klik **creëren** > **Aanpassings Forms**. De wizard voor het maken van adaptief formulier wordt geopend.

1. Selecteer het malplaatje van de kerncomponent in het **Source** lusje.
1. Selecteer het thema in de **Stijl** tabel.
1. Klik **creëren**.

De thema&#39;s Adaptief formulier worden gebruikt als onderdeel van een adaptieve formuliersjabloon om opmaak te definiëren terwijl u een adaptief formulier maakt.

## Aanbevolen procedures {#best-practices}

* **vermijdend activa van een ander thema**

  Wanneer u een thema bewerkt, kunt u door elementen (zoals afbeeldingen) bladeren en elementen uit andere thema&#39;s toevoegen. U bewerkt bijvoorbeeld de achtergrond van een pagina. Bijvoorbeeld, wanneer u **[!UICONTROL Page]** ![ uitgeeft-knoop ](assets/edit-button.png) > **[!UICONTROL Background]** > **[!UICONTROL Add]** > **[!UICONTROL Image]** selecteert, ziet u een dialoog die u laat doorbladeren en beelden in ander thema toevoegen.

  U kunt problemen met uw huidige thema oplossen als een element wordt toegevoegd uit een ander thema en het andere thema wordt verplaatst of verwijderd. U wordt aangeraden te voorkomen dat u bladeren en elementen uit andere thema&#39;s toevoegt.

* **Veranderend de lay-outbreedte van het containerpaneel**

  Het wordt niet aanbevolen de lay-outbreedte van het containervenster te wijzigen. Wanneer u de breedte van een containerdeelvenster opgeeft, wordt het statisch en wordt het niet aangepast aan verschillende weergaven.

## Veelgestelde vragen {#faq}

**Q:** Welke aanpassing neemt prioriteit wanneer het maken van aanpassingen in een themamap op zowel het globale niveau als componentenniveau?

**Ans:** wanneer de aanpassingen op zowel het globale niveau als componentenniveau worden gemaakt, neemt de aanpassing op het componentenniveau prioriteit.

<!--

## See next

* [Set layout of forms for different screen sizes and device types](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Generate Document of Record for Adaptive Forms (Core Components](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Create an Adaptive Forms with Repeatable sections](/help/forms/create-forms-repeatable-sections.md)
* [Sample themes templates and form data models](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)

-->


## Zie ook {#see-also}

{{see-also}}

* [Formulierindeling instellen voor verschillende schermgrootten en apparaattypen](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
* [Document met record genereren voor adaptieve Forms (kerncomponenten)](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)
* [Een adaptieve Forms maken met herhalende secties](/help/forms/create-forms-repeatable-sections.md)
* [ de themasjablonen van de Steekproef en modellen van vormgegevens ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
