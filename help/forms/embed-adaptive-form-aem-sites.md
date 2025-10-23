---
title: Hoe kan ik een adaptief formulier toevoegen aan een AEM Sites-pagina?
description: Sluit Adaptieve Forms naadloos in op een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost.
feature: Adaptive Forms
role: Admin, User, Developer
Keywords: Forms AEM Sites, Embed Form to a Sites page, Adaptive Forms AEM Sites, Embed Adaptive Forms to AEM Page, Embed Forms in an AEM Sites page
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 958c166585ac7eeb667d73744403558b2dc5ce94
workflow-type: tm+mt
source-wordcount: '3105'
ht-degree: 0%

---

# Een adaptief formulier insluiten op een AEM-sitepagina {#embed-an-adaptive-form-to-aem-sites-page}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-aem-sites.html) |
| AEM as a Cloud Service | Dit artikel |


## Overzicht {#overview}

Met AEM Forms kunnen formulierontwikkelaars de Adaptieve Forms naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren. Zo kunnen gebruikers formulieren eenvoudig invullen en verzenden zonder de pagina waarop ze staan te verlaten. Deze integratie biedt een handige manier om Adaptieve Forms die ze al hebben gemaakt, opnieuw te gebruiken.

Met de AEM Page Editor kunt u snel meerdere formulieren insluiten op uw AEM Sites-pagina&#39;s. Met de AEM Page Editor kunnen auteurs van inhoud naadloze ervaringen maken met het vastleggen van gegevens op een sitepagina. Hierbij worden adaptieve Forms-componenten gebruikt, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

AEM Forms biedt **[!UICONTROL Adaptive Form Container]** - en **[!UICONTROL Adaptive Forms – Embed(v2)]** -componenten. U kunt **[!UICONTROL Adaptive Forms – Embed(v2)]** gebruiken om een bestaand adaptief formulier toe te voegen of een formulier te maken met de Adaptive Forms Editor, terwijl **[!UICONTROL Adaptive Form Container]** nieuwe formulieren maakt in een Experience-fragment of AEM Sites-pagina.

![ een voorbeeld van een AanpassingsVorm in een pagina van AEM Sites ](/help/forms/assets/adaptive-form-in-sites-page.png)

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). 

## Why embed an Adaptive Form in AEM Sites page or AEM Experience Fragment? 

Using **[!UICONTROL Adaptive Forms – Embed(v2)]** in AEM Page Editor lets you create seamless data capture experiences within a Sites page using the power of Adaptive Forms components including dynamic behavior, validations, data integration, generate document of record and business process automation. It also lets you use various features of AEM Sites pages like, versioning, targeting, translation, and multi-site manager, enhancing the overall form creation and management experience. Let's explore some of these features:

* **Versioning:** AEM Sites pages offer [robust versioning capabilities](/help/sites-cloud/authoring/sites-console/page-versions.md), allowing you to track and manage different versions of your forms. This enables you to make changes and enhancements to forms while maintaining the ability to roll back to previous versions if needed. Versioning ensures a controlled and organized approach to form development and evolution.
* **Targeting (Integration with Adobe Target):** With AEM Sites pages targeting capabilities, you can also [personalize the form experience for different audiences](/help/sites-cloud/integrating/integrating-adobe-target.md). By using user segments and targeting criteria, you can tailor the form's content, design, or behavior to specific groups of users. This enables you to provide a personalized and relevant form experience, increasing engagement and conversion rates.
* **Translation:** AEM Sites [seamless integration with translation services](/help/sites-cloud/administering/translation/overview.md), allowing you to translate forms into multiple languages easily. This feature simplifies the localization process, ensuring that your forms are accessible to a global audience. You can manage translations efficiently within AEM translation projects, reducing time and effort required for multilingual form support. See considerations section for more information on translation.  
* **Multi-site Management and Live Copy:** AEM Sites provide robust [Multi-site Management and Live Copy capabilities](/help/sites-cloud/administering/msm/overview.md), enabling you to create and manage multiple websites within a single environment. This feature now lets you reuse forms across different sites, ensuring consistency and reducing duplication efforts. With centralized control and management, you can efficiently maintain and update forms across multiple websites.
* **Themes:** AEM Sites pages provide a framework for designing and maintaining consistent visual styles across multiple web pages. These define colors, fonts, style sheets, and other visual elements that contribute to the overall look and feel of the website. [You can use the themes designed for an AEM Sites page for an Adaptive Form, saving time and effort](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes). 
* **Tagging:** AEM Sites pages allow you to [assign tags or labels to a page, an asset, or other content](/help/implementing/developing/introduction/tagging-framework.md). Tags are keywords or metadata labels that provide a way to categorize and organize content based on specific criteria. You can assign one or more tags to pages, assets, or any other content items within AEM to improve search and categorize the assets. 
* **Locking and Unlocking content:** AEM Sites allow users to [control access and modifications to pages](/help/sites-cloud/authoring/page-editor/edit-content.md) within the AEM Sites environment. When a page is locked, it means that it is protected from unauthorized changes or edits by other users. Only the user who has locked the content or a designated administrator can unlock it to allow modifications. 

In addition, Adaptive Forms in AEM Page Editor use [Adaptive Forms Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#features). These Core Components provide a standard and easier methods to style and customize the components, identical to [AEM Sites WCM Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).

-->

## Hoe maakt of sluit u een adaptief formulier in op een AEM Sites-pagina of in een AEM Experience-fragment? {#various-options-to-create-or-embed-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **[creeer een Aangepast Vorm gebruikend goedgekeurde malplaatjes en bedt het aan een pagina van AEM Sites ](#embed-form-using-adaptive-form-wizzard-aem-sites) in:** u kunt vooraf goedgekeurde malplaatjes gebruiken om Aangepast Forms snel tot stand te brengen en in te bedden die zich met de brandende richtlijnen van uw organisatie en ontwerpnormen richt.

* **[bed bestaande vormen aan een pagina van AEM Sites ](#embed-an-adaptive-form-in-sites-editor) in:** u kunt vormen gemakkelijk integreren die u reeds in uw websites hebt gecreeerd, toelatend bezoekers om met hen direct in wisselwerking te staan.

* **[zet een ingebedde AanpassingsVorm in het Fragment van de Ervaring ](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment) om:** zet een ingebedde AanpassingsVorm die aan een pagina van AEM Sites wordt toegevoegd in een Fragment van de Ervaring om de vorm over veelvoudige pagina&#39;s van AEM Sites opnieuw te gebruiken.

* **[creeer en voeg een douane Aangepaste Vorm aan een pagina van AEM Sites toe ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** u kunt de **[!UICONTROL Adaptive Form Container]** component gebruiken om een gloednieuwe vorm van kras te bouwen, die het specifiek aan uw vereisten en ontwerpvoorkeur aanpast.

* **[creeer en voeg een douane Aangepaste Vorm aan een Fragmenten van de Ervaring toe ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor):** u kunt het bereik van uw vormen uitbreiden door hen aan de Fragmenten van de Ervaring van AEM toe te voegen, die voor naadloos hergebruik over veelvoudige pagina&#39;s of plaatsen toestaan.

* **voeg veelvoudige vormen aan een de pagina of Fragment van de Ervaring van AEM Sites toe:** u kunt veelvoudige AanpassingsForms tot stand brengen of toevoegen aan een pagina van AEM Sites om veelvoudige keuzen aan gebruikers te verstrekken die op hun voorkeur en vereisten worden gebaseerd. Met de AEM Page Editor kunt u snel meerdere formulieren insluiten op uw AEM Sites-pagina&#39;s. U kunt de component **[!UICONTROL Adaptive Form Container]** meerdere keren gebruiken om Adaptieve Forms toe te voegen aan een AEM Sites-pagina. U kunt de component **[!UICONTROL Adaptive Forms - Embed]** meerdere keren gebruiken op een AEM Sites-pagina, alleen als de optie **[!UICONTROL Form covers entire width of the frame]** is geselecteerd. Als de optie **[!UICONTROL Form covers entire width of the frame]** niet is ingeschakeld, ondersteunt de AEM Sites-pagina slechts één adaptief formulier dat zonder iframe kan worden gebruikt. Als u meer Adaptieve Forms wilt toevoegen met de component **[!UICONTROL Adaptive Forms - Embed]** , selecteert u de optie **[!UICONTROL Form covers entire width of the frame]** .

## Overwegingen bij het insluiten van een adaptief formulier in een AEM Sites-pagina of AEM Experience Fragment {#consideration}

* Wanneer u een formulier maakt of toevoegt met de component **[!UICONTROL Adaptive Forms – Embed(v2)]** , worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. **[!UICONTROL Adaptive Forms – Embed(v2)]** biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

* Wanneer u **[!UICONTROL Adaptive Form Container]** gebruikt om een formulier te maken, worden de formulieren vertaald en gelokaliseerd via de AEM Sites-vertaalstroom. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. Met **[!UICONTROL Adaptive Form Container]** kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Vereisten voor het insluiten van een adaptief formulier in een AEM Sites-pagina of AEM Experience Fragment {#before-you-start-embedding-an-adaptive-form}

Alvorens u begint een nieuwe Aangepaste Vorm of een reeds bestaand Aangepast Vorm in te bedden gebruikend **[!UICONTROL Adaptive Forms – Embed(v2)]**, laat **Aangepaste Componenten van de Kern van Forms** toe en voeg **Aangepaste Bibliotheken van de Cliënt van Forms** aan uw pagina van AEM Sites toe:

### Adaptieve Forms Core-componenten inschakelen voor uw AEM Cloud Service-omgeving

Installeer de nieuwste versie om Adaptive Forms Core Components in te schakelen voor uw AEM Cloud Service-omgeving.

### Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina of Experience Fragment

Als de optie **[!UICONTROL When form covers entire width of a page]** is geselecteerd in het dialoogvenster **[!UICONTROL Form Containers]** configureren en als Adaptieve Forms met Core Components wordt gebruikt, moeten de clientbibliotheken op de bijbehorende sitepagina worden geplaatst.

![ wanneer de vorm de volledige breedte van een paginaoptie behandelt wordt geselecteerd en de adaptieve vorm met kerncomponenten wordt gebruikt ](/help/forms/assets/overlaycorecomponent.gif)

**Geval 1: Het gebruiken van Afzonderlijke Componenten van de Pagina van Plaatsen**

Voeg de **Klantenkopballen** en **Customfooterlibs** cliëntbibliotheken aan uw pagina van AEM Sites toe gebruikend de plaatsingspijpleiding. De clientbibliotheken toevoegen:

1. De toegang en kloon uw [ Bewaarplaats van de Bewaarplaats van het Bezit van de Bedieningsruimte van de Dienst van de Wolk van AEM ](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
2. Open de map AEM Cloud Service Git Repository in een abonnementsteksteditor. Bijvoorbeeld Microsoft® Visual Code.
3. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

4. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

5. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

6. Open het bestand `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

7. [ stel de plaatsingspijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) in werking om de cliëntbibliotheken aan uw milieu van AEM as a Cloud Service op te stellen.

>[!NOTE]
>
> Hardcode de clientbibliotheek van de aangepaste functie alleen wanneer dit voor alle formulieren is vereist. Voor bibliotheken die verschillen op basis van het formuliertype, voegt u deze toe via sjabloonpaginabeleid, zoals wordt uitgelegd in de volgende sectie.

**Geval 2: Gebruikend de Zelfde Component van de Pagina van Plaatsen**

Neem de runtimeclientbibliotheken of aangepaste functiebibliotheken op in het paginabeleid van de sjabloon die wordt gebruikt voor het maken van pagina&#39;s met formulieren.

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op **[!UICONTROL Edit]** .
2. Open de sjabloon van de pagina Sites of Experience Fragment. Om het malplaatje te openen, ga naar **[!UICONTROL Page Information]** ![ de Informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Edit Template]**. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
3. Ga naar de **[!UICONTROL Page Information]** ![ sectie van de Informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) van het malplaatje en selecteer de **[!UICONTROL Page Policy]** optie. Hierdoor worden de eigenschappen van de AEM Sites-sjabloon geopend, waarin u aangepaste functies of clientbibliotheken bij uitvoering kunt definiëren.
4. Klik op de knop **[!UICONTROL Add]** op het tabblad **[!UICONTROL Properties]** om nieuwe aangepaste functiebibliotheken of runtimebibliotheken toe te voegen.
5. Klik **[Gedaan]**.

>[!VIDEO](https://video.tv.adobe.com/v/3476178?quality=12&learn=on)

### Adaptieve Forms - Embed(v2) inschakelen voor uw AEM Sites-pagina of Experience Fragment

Voer de volgende stappen uit om **[!UICONTROL Adaptive Forms – Embed(v2)]** -component in sjabloonbeleid in te schakelen:

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op **[!UICONTROL Edit]** .
1. Open de sjabloon van de pagina Sites of Experience Fragment. Om het malplaatje te openen, ga naar **[!UICONTROL Page Information]** ![ de Informatie van de Pagina ](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Edit Template]**. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. In de mening van de Structuur, klik het **[!UICONTROL Policy]** ![ Beleid ](/help/forms/assets/Smock_FeedManagement_18_N.svg) pictogram in de menubar. In de **[!UICONTROL Allowed Components]** lijst en selecteer **[!UICONTROL Adaptive Forms – Embed(v2)]** checkbox onder de **[Naam van het Project van de Archetype van AEM ] - Aangepaste Vorm**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

## Een adaptief formulier insluiten met de component Adaptief Forms - Embed(v2) {#embed-an-adaptive-form-in-sites-editor-or-experience-fragment}

Met de component **[!UICONTROL Adaptive Forms - Embed(v2)]** kunt u rechtstreeks in de AEM Sites-editor een adaptief formulier maken met de wizard Formulier maken. Het resulterende formulier wordt opgeslagen als een externe entiteit, zodat het opnieuw kan worden gebruikt in andere sitepagina&#39;s en op zichzelf staande formulieren. U kunt een geheel nieuw formulier insluiten, zodat u het kunt aanpassen aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een AEM Sites-pagina of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt direct schrijven naar een AEM Sites-pagina aanbevolen, terwijl Experience Fragments ideaal is voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

U kunt een nieuw formulier eenvoudig insluiten met **[!UICONTROL Adaptive Forms - Embed(v2)]** .  Stel dat u een nieuw contactformulier opneemt in een AEM Sites-pagina of AEM Experience Fragment. Alle updates of wijzigingen die in het contactformulier zijn aangebracht op de AEM Sites-pagina of het Experience-fragment, worden automatisch toegepast op alle pagina&#39;s waar het wordt geïmplementeerd. Dit vereenvoudigt het beheer van de formulieren van uw website, zodat de gebruiker probleemloos kan werken en het hele proces kan worden gestroomlijnd.

Met **[!UICONTROL Adaptive Forms - Embed(v2)]** kunt u:

* [Nieuw formulier insluiten met de wizard Adaptive Forms in AEM Sites Page](#embed-form-using-adaptive-form-wizzard-aem-sites)
* [Nieuw formulier insluiten met de wizard Adaptieve Forms in een ervaringsfragment](#embed-form-using-adaptive-form-wizzard-experience-fragment)
* [Een bestaand adaptief formulier insluiten in een AEM Sites-pagina](#embed-an-adaptive-form-in-sites-editor)
* [Een bestaand formulier insluiten in een ervaringsfragment](#embed-an-adaptive-form-in-experience-fragment)
* [ zet een Aangepast Vorm in de pagina van AEM Sites in een Fragment van de Ervaring om ](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Nieuw formulier insluiten met de wizard Adaptive Forms in AEM Sites Page {#embed-form-using-adaptive-form-wizzard-aem-sites}

De stappen voor het insluiten van een nieuw formulier op een AEM Sites-pagina zijn:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms - Embed(v2)]** vanuit het deelvenster Componentbrowser naar de pagina.
1. Klik **plus** pictogram en u wordt opnieuw gericht aan de tovenaar van de vormverwezenlijking.

   ![ Aangepaste Forms - bed Component ](/help/forms/assets/aemformcontainer.png) in

1. Maak een nieuw adaptief formulier via de wizard **[!UICONTROL Form Creation]** .
Het **[!UICONTROL Asset Path]** bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

Daarna, kunt u [ plaatsen de Submit Actie ](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingebedde AanpassingsVorm gebruikend de tovenaar van de creatie van de Vorm.


### Nieuw formulier insluiten met de wizard Adaptieve Forms in een ervaringsfragment {#embed-form-using-adaptive-form-wizzard-experience-fragment}

De stappen voor het insluiten van een nieuw formulier in een ervaringsfragment zijn:

1. Open het fragment van de Ervaring in geef wijze uit.
1. Sleep de component **[!UICONTROL Adaptive Forms - Embed(v2)]** vanuit het deelvenster Componentbrowser naar de pagina.
1. Klik **plus** pictogram en u wordt opnieuw gericht aan de tovenaar van de vormverwezenlijking.

   ![ Aangepaste Forms - bed Component ](/help/forms/assets/aemformcontainer.png) in

1. Maak een nieuw adaptief formulier via de wizard **[!UICONTROL Form Creation]** .
Het **[!UICONTROL Asset Path]** bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in het ervaringsfragment.

Daarna, kunt u [ plaatsen de Submit Actie ](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingebedde AanpassingsVorm gebruikend de tovenaar van de creatie van de Vorm.

### Een bestaand adaptief formulier insluiten in een AEM Sites-pagina {#embed-an-adaptive-form-in-sites-editor}

Met de component **[!UICONTROL Adaptive Forms - Embed(v2)]** kunt u een reeds bestaand adaptief formulier moeiteloos integreren in een pagina in AEM Sites. Met deze functie wordt het aanpassingsvermogen en de herbruikbaarheid van Adaptive Forms aanzienlijk verbeterd en kunnen klanten op een handige manier formulieren hergebruiken die ze al hebben gemaakt. Stel bijvoorbeeld dat u een contactformulier opneemt op een AEM Sites-pagina, zodat het formulier niet meerdere keren opnieuw hoeft te worden gemaakt.

Een bestaand adaptief formulier insluiten in een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms - Embed(v2)]** van de Componentbrowser naar de pagina Sites.
1. Selecteer de **[!UICONTROL Adaptive Forms - Embed]** component in de pagina van Plaatsen en selecteer ![ de Adaptieve eigenschappen van de Container van de Vorm ](/help/forms/assets/configure-icon.svg) op de actiebar. Het dialoogvenster **[!UICONTROL Edit Adaptive Forms - Embed(v2)]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het **[!UICONTROL Asset Path]** en selecteer dit.
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

Daarna, kunt u [ plaatsen de Submit Actie ](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingebedde AanpassingsVorm gebruikend de tovenaar van de creatie van de Vorm.

### Een bestaand adaptief formulier insluiten in een ervaringsfragment {#embed-an-adaptive-form-in-experience-fragment}

U kunt de toegankelijkheid van uw formulieren ook uitbreiden door deze in te sluiten in AEM Experience Fragment. Een adaptief formulier insluiten in een ervaringsfragment:

1. Open een Experience Fragment in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms - Embed(v2)]** van de Componentbrowser naar het fragment van de Experience.
1. Selecteer de **[!UICONTROL Adaptive Forms - Embed]** component in het Fragment van de Ervaring en selecteer ![ de Adaptieve eigenschappen van de Container van de Vorm ](/help/forms/assets/configure-icon.svg) op de actiebar. Het dialoogvenster **[!UICONTROL Edit Adaptive Forms - Embed(v2)]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het **[!UICONTROL Asset Path]** en selecteer dit.
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in het ervaringsfragment.

Daarna, kunt u [ plaatsen de Submit Actie ](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingebedde AanpassingsVorm gebruikend de tovenaar van de creatie van de Vorm.

### Een formulier in een AEM Sites-pagina converteren naar een Experience-fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

U kunt een bestaand adaptief formulier in een sitepagina-editor converteren naar een ervaringsfragment om het formulier te hergebruiken op meerdere pagina&#39;s of sites.

Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment:

1. Open de AEM Sites-pagina met het adaptieve formulier (in de Adaptive Forms Container-component) in de bewerkingsmodus.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Voor de menubar, selecteer ![ Bekeerling om het pictogram van de fragmentvariatie ](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Omzetten in het de variatiepictogram van het Fragment van de Ervaring te ervaren.

   ![ klik het embleem van het dossierkabinet om een Aangepast Vorm in de pagina van AEM Sites in een Fragment van de Ervaring om te zetten ](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Er wordt een dialoogvenster weergegeven waarin u de container Adaptief formulier kunt converteren naar een nieuw Erviteitsfragment of een bestaand Erviteitsfragment kunt toevoegen.

1. Stel in het dialoogvenster **[!UICONTROL Convert to Experience Fragment]** Variatie waarden in voor de volgende opties:

   * **Actie:** Uitgezocht om een Fragment van de Ervaring tot stand te brengen of aan een bestaand Fragment van de Ervaring toe te voegen.
   * **de weg van de Ouder:** specificeer weg van de omslag om het Fragment van de Ervaring binnen te ontvangen. De optie is alleen beschikbaar voor het maken van een nieuw ervaringsfragment.
   * **Malplaatje:** specificeer weg van het malplaatje van het Fragment van de Ervaring. Als u geen malplaatje van het Fragment van de Ervaring hebt, [ creeer het ](/help/implementing/developing/extending/experience-fragments.md). De optie is alleen beschikbaar als u een adaptief formulier toevoegt aan een bestaand ervaringsfragment.
   * **titel van het Fragment:** specificeer titel van het Fragment van de Ervaring. De titel identificeert uniek een Fragment van de Ervaring.
   * **de markeringen van het Fragment:** specificeer markering van het Fragment van de Ervaring. De tag geeft een unieke categorie van een ervaringsfragment aan.

## Adaptieve eigenschappen voor insluiten van formulieren (v2) configureren

U kunt de geavanceerde instellingen van de component **[!UICONTROL Adaptive Form - Embed(v2)]** aanpassen. In het dialoogvenster **[!UICONTROL Edit Adaptive Forms - Embed]** kunt u het volgende opgeven:

* **Weg van Activa**: doorblader en selecteer een Aangepast Vorm om in te bedden. Deze wordt automatisch ingevuld als u deze uit de Assets-browser hebt verwijderd.
* **Post Verzending** : Selecteer de actie om op vormvoorlegging teweeg te brengen. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.
   * **toon Dank u Bericht**: Schrijf een bericht gebruikend de rijke tekstredacteur om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
   * **toon Dank u Pagina**: doorblader en selecteer de pagina om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Redirect om u pagina** te danken: Laat de optie toe om de pagina te vervangen die de ingebedde Aangepaste Vorm met dank u pagina bevat. Anders vervangt de pagina Hartelijk dank u het Adaptieve formulier in de component **[!UICONTROL Adaptive Forms - Embed(v2)]** zonder de onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Bericht van de Thanku**: Korte bevestiging of erkenning die op het scherm na met succes het voorleggen van een vorm wordt getoond.
   * **Pagina van de Bedankt**: doorblader en selecteer de pagina aan vertoning na met succes het voorleggen van een vorm.

* **Taal van de Pagina van het Gebruik**: Gebruik lokaal van de pagina van AEM Sites in plaats van scène van AanpassingsVorm. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).
* **plaats Focus op Vorm**: Uitgezocht om de nadruk op het eerste gebied van de Aangepaste Vorm te plaatsen. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).
* **Thema**: Selecteer een thema dat het stileren voor componenten van uw Aangepaste Vorm bepaalt. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).

  >[!NOTE]
  >
  > U kunt de **Taal van de Pagina van het Gebruik** gebruiken, **Vastgestelde Nadruk op Vorm** en **de opties van het Thema** slechts voor Aangepaste Vorm (Stichting).

* **de vorm behandelt volledige breedte van het kader**:
Een inline-frame (iframe) is een HTML-element dat een adaptief formulier laadt naar een AEM Sites-pagina.

   * Als het selectievakje **[!UICONTROL Form covers entire width of the frame]** is ingeschakeld, neemt een adaptief formulier de volledige breedte in van de container waarin het is geplaatst. In dit geval wordt geen iframe gebruikt om het formulier te genereren. De indeling en het ontwerp van een adaptief formulier worden aangepast om de volledige breedte van de container te omspannen, zodat de container reageert en kan worden aangepast aan verschillende schermgrootten. Met deze optie kunt u meerdere Adaptieve Forms insluiten in een AEM Sites-pagina.

     >[!NOTE]
     >
     > Als u meerdere formulieren wilt insluiten in een AEM Sites-pagina, schakelt u het selectievakje **[!UICONTROL Form covers entire width of the frame]** in.

   * Als het selectievakje **[!UICONTROL Form covers entire width of the frame]** niet is ingeschakeld, beslaat een adaptief formulier niet de volledige breedte van de container. In plaats daarvan wordt een iframe gebruikt om het formulier te genereren, dat niet verder kan worden uitgebreid dan een bepaalde breedte. Deze aanpak is handig wanneer een adaptief formulier duidelijke grenzen heeft en moet bestaan naast andere AEM-componenten in de container. Als deze optie niet is ingeschakeld, kan slechts één adaptieve Forms-pagina in AEM Sites zonder iframe worden ingesloten.

     >[!NOTE]
     >
     > AEM Sites-pagina ondersteunt slechts één adaptief formulier dat zonder iframe kan worden gebruikt. Als u meer Adaptieve Forms wilt toevoegen met de component **[!UICONTROL Adaptive Forms - Embed]** , selecteert u de optie **[!UICONTROL Form covers entire width of the frame]** .

* **Hoogte**: Specificeer de hoogte van de container. Laat deze leeg om de grootte van de container automatisch te wijzigen.
* **CSS de bibliotheek van de Cliënt**: Specificeer weg aan een CSS cliëntbibliotheek.

<!--
In AEM Sites page, you can add an Adaptive Form using:

* **Adaptive Forms - Embed component**
   Adaptive Forms - Embed component enables AEM Sites authors to include an existing Adaptive Form within an AEM Sites page, thereby enhancing the reusability of adaptive forms. Existing Adaptive Forms can be used standalone or embedded in the site page. This integration provides a convenient way for customers to reuse Adaptive Forms they have already created.

* **Asset browser**
  All the forms are available under Assets. You can drag-drop the form as an asset on your page.

## Prerequisites {#prerequisites}

 To embed an Adaptive Form in an AEM Sites page that uses an editable template, ensure that the AEM Form component is configured as an allowed component in the associated template. 

In case **Adaptive Forms - Embed component** is not visible in the **Component browser panel** of AEM sites page, perform the following steps as illustrated in the video.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

In case Sites page is using a static template, you need to configure it in the paragraph system of the site page. 

## Embedding an Adaptive Form {#af-component}

To embed an Adaptive Form using the **[!UICONTROL Adaptive Forms - Embed]** component:

1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the [!UICONTROL Adaptive Forms - Embed] component on the page. Alternatively, you can search for an Adaptive Form in the Assets browser and drag-drop it onto the Sites page. You can add a new Adaptive Form or embed an existing Adaptive Form. 

   >[!NOTE]
   >
   >Multiple Adaptive Forms - Embed components on a page are not supported.

1. To create and embed a new form, on the component toolbar, select the **Create Form** icon. A window to create the form opens. 

1. Select the embedded Adaptive Forms - Embed component in the sites page, and then select ![settings_icon](assets/settings_icon.png) on the action bar. The **[!UICONTROL Edit Adaptive Forms - Embed]** dialog opens.
1. In the Edit Adaptive Forms - Embed dialog, specify the following.

    **Asset Type:** Select the type of asset to embed. 
    * **Asset Path**: Browse and select the Adaptive Form to embed. It is auto-populated if you dropped it from the Assets browser.
    * **Post Submission** : Select the action to trigger on form submission. You can choose to show a thank you message or a thank you page.
        * Show

        * **Thank You Message**: Write a message using the rich text editor to show on form submission. This option is available only when you choose to show a thank you message.
        * **Thank You Page**: Browse and select the page to display on form submission. This option is available only when you choose to show a thank you page.
           * **Redirect to thank you page**: Enable the option to replace the page containing the embedded Adaptive Form with thank you page. Otherwise, the thank you page replaces the Adaptive Form in the [!UICONTROL Adaptive Forms - Embed] component, without refreshing underlying sites the page. This option is available only when you choose to show a thank you page.
    * **Use Page Language**: Use local of the AEM Sites page instead locale of Adaptive Form.
    * **Set Focus on Form**: Select to set the focus on the first field of the Adaptive Form.
    * **Theme**: Select a theme that defines styling for components of your Adaptive Form. Styling includes appearance properties such as font style, background color, dimensions, and alignment.
    * **Form covers entire width of the frame**: If checked, iframe is not used to render the form. 
    * **Height**: Specify the height of the container. Leave it blank to automatically resize the container.
    * **CSS Client library**: Specify path to a CSS client library.

1. Save the settings. The Adaptive Form  is now embedded in the page.


AEM site also lets you create an Adaptive Form on the fly using the Adaptive Forms - Embed component. Follow the steps to create an Adaptive Form using the **Adaptive Forms - Embed component** on AEM sites page:
1. Open the AEM sites page, in edit mode, in which you want to embed an Adaptive Form.
1. From the Component browser panel, drag-drop the Adaptive Forms - Embed component on the page.
1. Click the **Plus** icon and you are redirected to the form creation wizard.

    ![Adaptive Forms - Embed Component](/help/forms/assets/aemformcontainer.png)

1. You can now embed an Adaptive Form on AEM site pages using the [!UICONTROL AEM Forms Container Component].
-->

## Ingesloten adaptief formulier publiceren {#publishing-embedded-adaptive-form}

Neem de volgende scenario&#39;s in overweging voor het publiceren van een ingesloten adaptief formulier in AEM-sitepagina:

* Als u de AEM-sitepagina voor het eerst publiceert en een ingesloten adaptief formulier bevat, publiceert u de sitepagina en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier hebt gewijzigd in een gepubliceerde sitepagina, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier wijzigen  {#modifying-embedded-adaptive-form}

Voer een van de volgende handelingen uit om een configuratie of eigenschap van het ingesloten adaptieve formulier te wijzigen.

* Open het oorspronkelijke formulier in een adaptief formulier in de desbetreffende editor en wijzig deze.
* Selecteer het adaptieve formulier in de bewerkingsmodus van de sitepagina en selecteer vervolgens **[!UICONTROL Edit in a new window]** . Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen die in het oorspronkelijke adaptieve formulier zijn aangebracht, worden automatisch doorgevoerd in het ingesloten formulier. Publiceer echter het adaptieve formulier of de pagina van de site om de wijzigingen in de gepubliceerde pagina weer te geven.

## Aanbevolen procedures {#best-practices}

Houd rekening met de volgende punten wanneer u Adaptive Forms insluit op AEM-sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de Forms Portal.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.

## Zie ook {#see-also}

* [Zelfstandige adaptieve Forms op basis van Core Component maken](/help/forms/creating-adaptive-form-core-components.md)
* [Direct een adaptief formulier op basis van een kerncomponent maken op een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
