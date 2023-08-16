---
title: Een adaptief formulier insluiten in AEM Sites-pagina
seo-title: How to add an Adaptive Form to an AEM Sites page?
description: Met de component Adaptive Forms - Embed kunt u Adaptive Forms insluiten in een AEM Sites-pagina, zodat u een formulier kunt invullen en verzenden zonder de AEM Sites-pagina's te verlaten.
feature: Adaptive Forms
Keywords: Forms AEM Sites, Embed Form to a Sites page, Adaptive Forms AEM Sites, Embed Adaptive Forms to AEM Page, Embed Forms in an AEM Sites page
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: bb2ee07f8750c15959ecdaa65f0932b05edfcd39
workflow-type: tm+mt
source-wordcount: '2947'
ht-degree: 0%

---

# Een adaptief formulier insluiten op een pagina met AEM sites {#embed-an-adaptive-form-to-aem-sites-page}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-aem-sites.html) |
| AEM as a Cloud Service | Dit artikel |


## Overzicht {#overview}

Met AEM Forms kunnen formulierontwikkelaars de Adaptieve Forms naadloos insluiten in een AEM Sites-pagina of een webpagina die buiten AEM wordt gehost. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren. Zo kunnen gebruikers formulieren eenvoudig invullen en verzenden zonder de pagina waarop ze staan te verlaten. Deze integratie biedt een handige manier om Adaptieve Forms die ze al hebben gemaakt, opnieuw te gebruiken.

Met AEM paginaeditor kunt u snel meerdere formulieren insluiten op uw AEM Sites-pagina&#39;s. Met AEM Pagina-editor kunnen auteurs van inhoud naadloze ervaringen maken met het vastleggen van gegevens op een sitepagina. Hierbij worden adaptieve Forms-componenten gebruikt, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

AEM Forms-provider **[!UICONTROL Adaptive Form Container]** en **[!UICONTROL Adaptive Forms – Embed(v2)]** componenten. U kunt **[!UICONTROL Adaptive Forms – Embed(v2)]** om een bestaand adaptief formulier toe te voegen of een formulier te maken met de Adaptive Forms Editor, terwijl **[!UICONTROL Adaptive Form Container]** om een nieuw formulier te maken binnen een Experience Fragment of AEM Sites-pagina.

![Een voorbeeld van een adaptief formulier in een AEM Sites-pagina](/help/forms/assets/adaptive-form-in-sites-page.png)

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). 

## Why embed an Adaptive Form in AEM Sites page or AEM Experience Fragment? 

Using **[!UICONTROL Adaptive Forms – Embed(v2)]** in AEM Page Editor lets you create seamless data capture experiences within a Sites page using the power of Adaptive Forms components including dynamic behavior, validations, data integration, generate document of record and business process automation. It also lets you use various features of AEM Sites pages like, versioning, targeting, translation, and multi-site manager, enhancing the overall form creation and management experience. Let's explore some of these features:

* **Versioning:** AEM Sites pages offer [robust versioning capabilities](/help/sites-cloud/authoring/features/page-versions.md), allowing you to track and manage different versions of your forms. This enables you to make changes and enhancements to forms while maintaining the ability to roll back to previous versions if needed. Versioning ensures a controlled and organized approach to form development and evolution.
* **Targeting (Integration with Adobe Target):** With AEM Sites pages targeting capabilities, you can also [personalize the form experience for different audiences](/help/sites-cloud/integrating/integration-adobe-target-ims.md). By leveraging user segments and targeting criteria, you can tailor the form's content, design, or behavior to specific groups of users. This enables you to provide a personalized and relevant form experience, increasing engagement and conversion rates.
* **Translation:** AEM Sites [seamless integration with translation services](/help/sites-cloud/administering/translation/overview.md), allowing you to translate forms into multiple languages easily. This feature simplifies the localization process, ensuring that your forms are accessible to a global audience. You can manage translations efficiently within AEM translation projects, reducing time and effort required for multilingual form support. See considerations section for more information on translation.  
* **Multi-site Management and Live Copy:** AEM Sites provide robust [Multi-site Management and Live Copy capabilities](/help/sites-cloud/administering/msm/overview.md), enabling you to create and manage multiple websites within a single environment. This feature now lets you reuse forms across different sites, ensuring consistency and reducing duplication efforts. With centralized control and management, you can efficiently maintain and update forms across multiple websites.
* **Themes:** AEM Sites pages provide a framework for designing and maintaining consistent visual styles across multiple web pages. These define colors, fonts, style sheets, and other visual elements that contribute to the overall look and feel of the website. [You can use the themes designed for an AEM Sites page for an Adaptive Form, saving time and effort](/help/sites-cloud/administering/site-creation/site-themes.md#using-site-themes-using-themes). 
* **Tagging:** AEM Sites pages allow you to [assign tags or labels to a page, an asset, or other content](/help/implementing/developing/introduction/tagging-framework.md). Tags are keywords or metadata labels that provide a way to categorize and organize content based on specific criteria. You can assign one or more tags to pages, assets, or any other content items within AEM to improve search and categorize the assets. 
* **Locking and Unlocking content:** AEM Sites allow users to [control access and modifications to pages](/help/sites-cloud/authoring/fundamentals/editing-content.md) within the AEM Sites environment. When a page is locked, it means that it is protected from unauthorized changes or edits by other users. Only the user who has locked the content or a designated administrator can unlock it to allow modifications. 

In addition, Adaptive Forms in AEM Page Editor use [Adaptive Forms Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#features). These Core Components provide a standard and easier methods to style and customize the components, identical to [AEM Sites WCM Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=en).

-->

## Hoe maakt of sluit u een adaptief formulier in op een AEM Sites-pagina of in AEM Experience Fragment? {#various-options-to-create-or-embed-an-adaptive-form-in-aem-sites-page-or-aem-experience-fragment}

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **[Een adaptief formulier maken met goedgekeurde sjablonen en dit insluiten op een AEM Sites-pagina](#embed-form-using-adaptive-form-wizzard-aem-sites):** U kunt vooraf goedgekeurde sjablonen gebruiken om snel een adaptieve Forms te maken en in te sluiten die voldoet aan de richtlijnen en ontwerpstandaarden van uw organisatie voor het brandmerken.

* **[Bestaande formulieren insluiten op een AEM Sites-pagina](#embed-an-adaptive-form-in-sites-editor):** U kunt formulieren die u al hebt gemaakt, eenvoudig integreren in uw websites, zodat bezoekers direct met hen kunnen communiceren.

* **[Een ingesloten adaptief formulier converteren naar Experience Fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment):** Converteer een ingesloten adaptief formulier dat aan een AEM Sites-pagina is toegevoegd naar een Experience-fragment en gebruik het formulier opnieuw op meerdere AEM Sites-pagina&#39;s.

* **[Een aangepast adaptief formulier maken en toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor-or-experience-fragment):** U kunt de **[!UICONTROL Adaptive Form Container]** om een geheel nieuw formulier te maken, dat speciaal aan uw vereisten en ontwerpvoorkeuren is aangepast.

* **[Een aangepast adaptief formulier maken en toevoegen aan een Experience Fragments](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md#create-an-adaptive-form-in-sites-editor):** U kunt het bereik van uw formulieren uitbreiden door ze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites.

* **Meerdere formulieren toevoegen aan een AEM Sites-pagina of Ervaar fragment:**  U kunt meerdere Adaptieve Forms-bestanden maken of toevoegen aan een AEM Sites-pagina om gebruikers meerdere keuzes te bieden op basis van hun voorkeuren en vereisten. Met AEM paginaeditor kunt u snel meerdere formulieren insluiten op uw AEM Sites-pagina&#39;s. U kunt de **[!UICONTROL Adaptive Form Container]** om Adaptief Forms meerdere keren toe te voegen aan een AEM Sites-pagina. U kunt de **[!UICONTROL Adaptive Forms - Embed]** meerdere keren op een AEM Sites-pagina opnemen, alleen als **[!UICONTROL Form covers entire width of the frame]** is geselecteerd. In het geval van **[!UICONTROL Form covers entire width of the frame]** is niet ingeschakeld, ondersteunt de AEM Sites-pagina slechts één adaptief formulier dat zonder iframe kan bestaan. Als u meer adaptieve Forms wilt toevoegen, gebruikt u de opdracht **[!UICONTROL Adaptive Forms - Embed]** component, selecteren **[!UICONTROL Form covers entire width of the frame]** -optie.

## Overwegingen bij het insluiten van een adaptief formulier in een AEM Sites-pagina of AEM Experience Fragment {#consideration}

* Wanneer u een formulier maakt of toevoegt met de opdracht **[!UICONTROL Adaptive Forms – Embed(v2)]** worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. **[!UICONTROL Adaptive Forms – Embed(v2)]** biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

* Wanneer u de opdracht **[!UICONTROL Adaptive Form Container]** om een formulier te maken, worden de formulieren via de vertaalstroom van AEM Sites vertaald en gelokaliseerd. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. **[!UICONTROL Adaptive Form Container]** Hiermee kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Vereisten voor het insluiten van een adaptief formulier in een AEM Sites-pagina of AEM Experience Fragment {#before-you-start-embedding-an-adaptive-form}

Voordat u begint met het insluiten van een nieuw adaptief formulier of een reeds bestaand adaptief formulier met **[!UICONTROL Adaptive Forms – Embed(v2)]**, enable **Adaptieve Forms Core-componenten** en toevoegen **Adaptieve Forms-clientbibliotheken** op je AEM Sites-pagina:

+++  Adaptieve Forms Core-componenten inschakelen voor uw AEM Cloud Service-omgeving

Zorg ervoor dat de [Adaptieve Forms Core-componenten zijn ingeschakeld voor uw as a Cloud Service AEM Forms-omgeving](enable-adaptive-forms-core-components.md).

+++

+++  Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina of Experience Fragment

Wanneer de **[!UICONTROL When form covers entire width of a page]** is geselecteerd in het dialoogvenster **[!UICONTROL Form Containers]** het dialoogvenster voor configureren en Adaptieve Forms met behulp van Core Components worden gebruikt, is het noodzakelijk dat de clientbibliotheken op de corresponderende sitepagina worden geplaatst.

![Als een formulier de volledige breedte van een pagina bedekt, is de optie geselecteerd en wordt een adaptief formulier met de kerncomponenten gebruikt](/help/forms/assets/overlaycorecomponent.gif)


Voeg de **CustomHederlibs** en **Aangepaste voetflabs** clientbibliotheken naar uw AEM Sites-pagina met de implementatiepijplijn. De clientbibliotheken toevoegen:

1. Toegang krijgen tot uw [AEM Cloud Service Git Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/managing-code/repositories.html).
1. Open de map AEM Cloud Service Git Repository in een planningsteksteditor. Bijvoorbeeld Microsoft® Visual Code.
1. Open de `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open de `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\page\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Open de `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open de `ui.apps\src\main\content\jcr_root\apps\[your-project]\components\xfpage\customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. [De implementatiepijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) om de cliëntbibliotheken aan uw AEM as a Cloud Service milieu op te stellen.

+++

+++ Inschakelen **[!UICONTROL Adaptive Forms – Embed(v2)]** voor uw AEM Sites-pagina of Experience Fragment

Inschakelen **[!UICONTROL Adaptive Forms – Embed(v2)]** in het sjabloonbeleid voert u de volgende stappen uit:

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op **[!UICONTROL Edit]**.
1. Open de sjabloon van de pagina Sites of Experience Fragment. Ga naar de **[!UICONTROL Page Information]** ![Pagina-informatie](/help/forms/assets/Smock_Properties_18_N.svg) > **[!UICONTROL Edit Template]**. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. Klik in de structuurweergave op de knop **[!UICONTROL Policy]** ![Beleid](/help/forms/assets/Smock_FeedManagement_18_N.svg) in de menubalk. In de **[!UICONTROL Allowed Components]** en selecteert u de **[!UICONTROL Adaptive Forms – Embed(v2)]**  selectievakje onder **[Projectnaam AEM] - Adaptief formulier**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

## Een adaptief formulier insluiten met de component Adaptief Forms - Embed(v2) {#embed-an-adaptive-form-in-sites-editor-or-experience-fragment}

Gebruik de **[!UICONTROL Adaptive Forms - Embed(v2)]** een adaptief formulier rechtstreeks in de AEM Sites-editor maken met de wizard Formulier maken. Het resulterende formulier wordt opgeslagen als een externe entiteit, zodat het opnieuw kan worden gebruikt in andere sitepagina&#39;s en op zichzelf staande formulieren. U kunt een geheel nieuw formulier insluiten, zodat u het kunt aanpassen aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een AEM Sites-pagina of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt direct schrijven naar een AEM Sites-pagina aanbevolen, terwijl Experience Fragments ideaal is voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

U kunt een nieuw formulier eenvoudig insluiten met **[!UICONTROL Adaptive Forms - Embed(v2)]**.  Stel dat u een nieuw contactformulier opneemt in een AEM Sites-pagina of AEM Experience Fragment. Alle updates of wijzigingen die in het contactformulier zijn aangebracht op de AEM Sites-pagina of het Experience-fragment, worden automatisch toegepast op alle pagina&#39;s waar het wordt geïmplementeerd. Dit vereenvoudigt het beheer van de formulieren van uw website, zodat de gebruiker probleemloos kan werken en het hele proces kan worden gestroomlijnd.

Gebruiken **[!UICONTROL Adaptive Forms - Embed(v2)]** kunt u:

* [Nieuw formulier insluiten met de wizard Adaptive Forms in AEM Sites Page](#embed-form-using-adaptive-form-wizzard-aem-sites)
* [Nieuw formulier insluiten met de wizard Adaptieve Forms in een ervaringsfragment](#embed-form-using-adaptive-form-wizzard-experience-fragment)
* [Een bestaand adaptief formulier insluiten in een AEM Sites-pagina](#embed-an-adaptive-form-in-sites-editor)
* [Een bestaand formulier insluiten in een ervaringsfragment](#embed-an-adaptive-form-in-experience-fragment)
* [Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Nieuw formulier insluiten met de wizard Adaptive Forms in AEM Sites Page {#embed-form-using-adaptive-form-wizzard-aem-sites}

De stappen voor het insluiten van een nieuw formulier op een AEM Sites-pagina zijn:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep vanuit het deelvenster Componentbrowser de **[!UICONTROL Adaptive Forms - Embed(v2)]** op de pagina.
1. Klik op de knop **Plus** en wordt u omgeleid naar de wizard Formulier maken.

   ![Adaptieve Forms - component insluiten](/help/forms/assets/aemformcontainer.png)

1. Een nieuw adaptief formulier maken met de opdracht **[!UICONTROL Form Creation]** wizard.
De **[!UICONTROL Asset Path]** bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

Vervolgens kunt u [De handeling Verzenden instellen](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingesloten adaptief formulier met de wizard Formulier maken.


### Nieuw formulier insluiten met de wizard Adaptieve Forms in een ervaringsfragment {#embed-form-using-adaptive-form-wizzard-experience-fragment}

De stappen voor het insluiten van een nieuw formulier in een ervaringsfragment zijn:

1. Open het fragment van de Ervaring in geef wijze uit.
1. Sleep vanuit het deelvenster Componentbrowser de **[!UICONTROL Adaptive Forms - Embed(v2)]** op de pagina.
1. Klik op de knop **Plus** en wordt u omgeleid naar de wizard Formulier maken.

   ![Adaptieve Forms - component insluiten](/help/forms/assets/aemformcontainer.png)

1. Een nieuw adaptief formulier maken met de opdracht **[!UICONTROL Form Creation]** wizard.
De **[!UICONTROL Asset Path]** bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in het ervaringsfragment.

Vervolgens kunt u [De handeling Verzenden instellen](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingesloten adaptief formulier met de wizard Formulier maken.

### Een bestaand adaptief formulier insluiten in een AEM Sites-pagina {#embed-an-adaptive-form-in-sites-editor}

Met de **[!UICONTROL Adaptive Forms - Embed(v2)]** kunt u een reeds bestaand adaptief formulier moeiteloos integreren in een pagina in AEM Sites. Met deze functie wordt het aanpassingsvermogen en de herbruikbaarheid van Adaptive Forms aanzienlijk verbeterd en kunnen klanten op een handige manier formulieren hergebruiken die ze al hebben gemaakt. Stel bijvoorbeeld dat u een contactformulier opneemt op een AEM Sites-pagina, zodat het formulier niet meerdere keren opnieuw hoeft te worden gemaakt.

Een bestaand adaptief formulier insluiten in een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de **[!UICONTROL Adaptive Forms - Embed(v2)]** van de Browser van de Component aan de pagina van Plaatsen.
1. Tik op de knop **[!UICONTROL Adaptive Forms - Embed]** component op de pagina Sites en tik op ![Eigenschappen van adaptieve formuliercontainers](/help/forms/assets/configure-icon.svg) op de actiebalk. De **[!UICONTROL Edit Adaptive Forms - Embed(v2)]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het dialoogvenster **[!UICONTROL Asset Path]**.
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)

Vervolgens kunt u [De handeling Verzenden instellen](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingesloten adaptief formulier met de wizard Formulier maken.

### Een bestaand adaptief formulier insluiten in een ervaringsfragment {#embed-an-adaptive-form-in-experience-fragment}

U kunt de toegankelijkheid van uw formulieren ook uitbreiden door deze in te sluiten in AEM Experience Fragment. Een adaptief formulier insluiten in een ervaringsfragment:

1. Open een Experience Fragment in de bewerkingsmodus.
1. Sleep de **[!UICONTROL Adaptive Forms - Embed(v2)]** van Componentbrowser naar Experience Fragment.
1. Tik op de knop **[!UICONTROL Adaptive Forms - Embed]** component in Experience Fragment en tik ![Eigenschappen van adaptieve formuliercontainers](/help/forms/assets/configure-icon.svg) op de actiebalk. De **[!UICONTROL Edit Adaptive Forms - Embed(v2)]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het dialoogvenster **[!UICONTROL Asset Path]**.
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in het ervaringsfragment.

Vervolgens kunt u [De handeling Verzenden instellen](/help/forms/configuring-submit-actions.md) en geavanceerde eigenschappen van een ingesloten adaptief formulier met de wizard Formulier maken.

### Een formulier in een AEM Sites-pagina converteren naar een Experience-fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

U kunt een bestaand adaptief formulier in een sitepagina-editor converteren naar een ervaringsfragment om het formulier te hergebruiken op meerdere pagina&#39;s of sites.

Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment:

1. Open de AEM Sites-pagina met het adaptieve formulier (in de Adaptive Forms Container-component) in de bewerkingsmodus.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** dat als host fungeert voor uw adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Selecteer in de menubalk de optie ![Omzetten in ervaringspictogram voor fragmentvariatie](/help/forms/assets/Smock_FilingCabinet_18_N.svg) Omzetten in het pictogram voor het ervaren van fragmentvariatie.

   ![Klik op het logo van de bestandsruimte om een adaptief formulier in AEM Sites om te zetten in een Experience-fragment](/help/forms/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Er wordt een dialoogvenster weergegeven waarin u de container Adaptief formulier kunt converteren naar een nieuw Erviteitsfragment of een bestaand Erviteitsfragment kunt toevoegen.

1. Op de **[!UICONTROL Convert to Experience Fragment]** In het dialoogvenster Variatie stelt u waarden in voor de volgende opties:

   * **Handeling:** Selecteer deze optie om een ervaringsfragment te maken of aan een bestaand ervaringsfragment toe te voegen.
   * **Bovenliggend pad:** Geef het pad van de map op waarin u het ervaringsfragment wilt plaatsen. De optie is alleen beschikbaar voor het maken van een nieuw ervaringsfragment.
   * **Template:** Geef het pad van de fragmentsjabloon voor ervaring op. Als u geen fragmentsjabloon voor ervaring hebt, [maken](/help/implementing/developing/extending/experience-fragments.md). De optie is alleen beschikbaar als u een adaptief formulier toevoegt aan een bestaand ervaringsfragment.
   * **Fragmenttitel:** Geef de titel van het ervaringsfragment op. De titel identificeert uniek een Fragment van de Ervaring.
   * **Fragmenttags:** Geef de tag van het ervaringsfragment op. De tag geeft een unieke categorie van een ervaringsfragment aan.

## Adaptieve eigenschappen voor insluiten van formulieren (v2) configureren

U kunt de geavanceerde instellingen van het dialoogvenster **[!UICONTROL Adaptive Form - Embed(v2)]** component. In de **[!UICONTROL Edit Adaptive Forms - Embed]** kunt u het volgende opgeven:

* **Middelpad**: Blader naar een adaptief formulier dat u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
* **Verzending na verzending** : Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.
   * **Bericht met dank weergeven**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
   * **Dankpagina tonen**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Doorverwijzen naar pagina voor bedankt**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vervangen door de pagina Hartelijk dank. Anders vervangt de pagina Bedankt het Adaptief formulier in het dialoogvenster **[!UICONTROL Adaptive Forms - Embed(v2)]** zonder onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Thankyou Message**: Korte bevestiging of bevestiging die op het scherm wordt weergegeven nadat een formulier is verzonden.
   * **Thankyou Page**: Blader en selecteer de pagina die u wilt weergeven nadat u een formulier hebt verzonden.

* **Paginataal gebruiken**: Gebruik de landinstelling van de AEM Sites-pagina in plaats van Adaptief formulier. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).
* **Focus op formulier instellen**: Selecteer deze optie om de focus in te stellen op het eerste veld van het adaptieve formulier. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).
* **Thema**: Selecteer een thema waarmee u opmaak definieert voor componenten van uw adaptieve formulier. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning. Deze optie is alleen van toepassing voor Adaptief formulier (Foundation).
* **Het formulier bedekt de volledige breedte van het kader**: Een inline-frame (iframe) is een HTML-element dat een adaptief formulier laadt naar een AEM Sites-pagina.

   * Als de **[!UICONTROL Form covers entire width of the frame]** Als deze optie is ingeschakeld, neemt een adaptief formulier de volledige breedte in van de container waarin het is geplaatst. In dit geval wordt geen iframe gebruikt om het formulier te genereren. De indeling en het ontwerp van een adaptief formulier worden aangepast om de volledige breedte van de container te omspannen, zodat de container reageert en kan worden aangepast aan verschillende schermgrootten. Met deze optie kunt u meerdere Adaptieve Forms insluiten in een AEM Sites-pagina.

     >[!NOTE]
     >
     > Selecteer **[!UICONTROL Form covers entire width of the frame]** selectievakje.

   * Als de **[!UICONTROL Form covers entire width of the frame]** selectievakje is niet ingeschakeld, een adaptief formulier beslaat niet de volledige breedte van de container. In plaats daarvan wordt een iframe gebruikt om het formulier te genereren, dat niet verder kan worden uitgebreid dan een bepaalde breedte. Deze aanpak is handig wanneer een adaptief formulier duidelijke grenzen heeft en moet bestaan naast andere AEM componenten in de container. Als deze optie niet is ingeschakeld, kan slechts één adaptieve Forms-pagina in AEM Sites zonder iframe worden ingesloten.

     >[!NOTE]
     >
     > AEM Sites-pagina ondersteunt slechts één adaptief formulier dat zonder iframe kan worden gebruikt. Als u meer adaptieve Forms wilt toevoegen, gebruikt u de opdracht **[!UICONTROL Adaptive Forms - Embed]** component, selecteren **[!UICONTROL Form covers entire width of the frame]** -optie.

* **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
* **CSS-clientbibliotheek**: Geef het pad op naar een CSS-clientbibliotheek.

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

1. To create and embed a new form, on the component toolbar, tap the **Create Form** icon. A window to create the form opens. 

1. Tap the embedded Adaptive Forms - Embed component in the sites page, and then tap ![settings_icon](assets/settings_icon.png) on the action bar. The **[!UICONTROL Edit Adaptive Forms - Embed]** dialog opens.
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

Overweeg de volgende scenario&#39;s voor het publiceren van een ingebedde Aangepaste Vorm in AEM plaatspagina:

* Als u de pagina met AEM sites voor het eerst publiceert en deze een ingesloten adaptief formulier bevat, publiceert u de pagina met sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier hebt gewijzigd in een gepubliceerde sitepagina, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de sitepagina en het ingesloten adaptieve formulier hebt gewijzigd, publiceert u de sitepagina en het ingesloten element opnieuw.

## Ingesloten adaptief formulier wijzigen  {#modifying-embedded-adaptive-form}

Voer een van de volgende handelingen uit om een configuratie of eigenschap van het ingesloten adaptieve formulier te wijzigen.

* Open het oorspronkelijke formulier in een adaptief formulier in de desbetreffende editor en wijzig deze.
* Tik in de bewerkingsmodus op het adaptieve formulier en tik vervolgens op **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

>[!NOTE]
>
>De wijzigingen die in het oorspronkelijke adaptieve formulier zijn aangebracht, worden automatisch doorgevoerd in het ingesloten formulier. Publiceer echter het adaptieve formulier of de pagina van de site om de wijzigingen in de gepubliceerde pagina weer te geven.

## Aanbevolen procedures {#best-practices}

Houd rekening met de volgende punten wanneer u Adaptive Forms insluit in AEM sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de Forms Portal.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.

## Zie ook {#see-also}

* [Zelfstandige adaptieve Forms op basis van Core Component maken](/help/forms/creating-adaptive-form-core-components.md)
* [Direct een adaptief formulier op basis van een kerncomponent maken op een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
