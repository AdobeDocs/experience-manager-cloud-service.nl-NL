---
title: Hoe kunt u een Adaptive Form Core Components toevoegen aan of maken op de AEM Sites-pagina?
description: Gebruik Adaptief Form Core-componenten op een AEM Sites-pagina om een formulier in te vullen en te verzenden zonder de AEM Sites-pagina's te verlaten.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '1952'
ht-degree: 0%

---

# Een adaptief formulier maken of toevoegen met de AEM Sites Editor {#add-an-adaptive-form-to-aem-sites-page}

U kunt Adaptief Forms naadloos ontwerpen of insluiten in een AEM Sites-pagina zodat uw gebruikers een formulier kunnen invullen en verzenden zonder de sitepagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen van de webpagina blijven en tegelijkertijd met het formulier communiceren.

U kunt een van de volgende methoden kiezen om een adaptief formulier te maken of toe te voegen aan een AEM Sites-pagina:

* **Een adaptief formulier maken met de adaptieve Forms Container-component**: De [Aangepaste formuliercontainer](#af-container-component) kunt u digitale inschrijvingen maken door Adaptieve Forms-componenten rechtstreeks in de AEM Sites-editor te gebruiken. Deze integratie biedt een naadloze ervaring voor AEM Sites-auteurs die formulieren op hun AEM Sites-pagina&#39;s willen maken en beheren.

* **Een bestaand adaptief formulier toevoegen**: De [Adaptieve Forms - Embed(v2)](#embed-existing-af) kunt u eenvoudig een reeds bestaand adaptief formulier toevoegen aan een pagina in AEM Sites. Deze functie verbetert het aanpassingsvermogen en de herbruikbaarheid van Adaptive Forms. Deze integratie biedt klanten een handige manier om Adaptive Forms die ze al hebben gemaakt opnieuw te gebruiken.

* **De wizard Adaptieve Forms gebruiken om een formulier te maken**: Gebruik de [Adaptieve Forms - Embed(v2)](#embed-new-af) een adaptief formulier maken vanuit de AEM Sites-editor met de wizard Formulier maken. Het formulier wordt opgeslagen als een externe entiteit. U kunt dit formulier ook hergebruiken in andere sitepagina&#39;s en op zichzelf staande formulieren.

* **Meerdere adaptieve Forms&#39;s toevoegen aan een AEM Sites-pagina**: Gebruik de AEM Forms-containercomponenten om meerdere Adaptive Forms-componenten aan een AEM Sites-pagina toe te voegen - [Adaptieve Forms - Embed(v2)](#embed-new-af) en [Aangepaste formuliercontainer](#af-container-component). Als u meer dan één adaptief formulier als div-element wilt toevoegen aan een AEM Sites-pagina, kunt u de component Adaptief formuliercontainer gebruiken.

U kunt de Redacteur van de Regel gebruiken om het dynamische gedrag van de Adaptieve componenten van de Vorm toe te voegen of te controleren. U kunt bijvoorbeeld een component verbergen of weergeven. De Rule Editor is niet beschikbaar voor niet-adaptieve formuliercomponenten. Gebruik dus uw zorgvuldigheid bij het gebruik van niet-adaptieve formuliercomponenten in de AEM Forms Container-component.

## Een adaptief formulier maken met de adaptieve Forms Container-component {#af-container-component}

De [!UICONTROL Adaptive Form Container] maakt het mogelijk om digitale inschrijvingen te maken met behulp van Adaptive Forms-componenten in de AEM Sites-editor. U kunt een adaptief formulier maken door de formuliercomponenten te slepen en neer te zetten.

### Vereisten {#prerequisites-af-container}

+++ Inschakelen **[!UICONTROL Adaptive Forms Container]** component.

Inschakelen [!UICONTROL Adaptive Forms Container] in het sjabloonbeleid voert u de volgende stappen uit:

1. Ga naar de [!UICONTROL Page Information] > [!UICONTROL Edit Template]
1. Klik op de knop [!UICONTROL Policy] en selecteert u de **[!UICONTROL Adaptive Forms Container]**  selectievakje onder **[Projectnaam AEM] - Adaptief formulier**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Inclusief Adaptieve Forms-clientbibliotheken naar AEM Sites-pagina

Als u Aangepaste Forms-componenten op een AEM Sites-pagina wilt gebruiken, neemt u de Client libraries Customheaderlibs en Customfooterlibs op naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository and Deployment-pijplijn.

1. Open uw [AEM Forms Archetype of Cloned Git Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een teksteditor. Bijvoorbeeld, de Code van Visual Studio.
1. Navigeren naar `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. De waarde kopiëren van `sling:resourceSuperType`. De waarde is bijvoorbeeld `core/wcm/components/page/v3/page`.

   ![slingerbron](/help/forms/assets/slingresource.png)

1. Een vergelijkbare structuur maken op de locatie `ui.apps/src/main/content/jcr_root/apps` gelijk aan `core/wcm/components/page/v3/page`.

   ![bedekkingsstructuur](/help/forms/assets/overlaystructure.png)

1. Toevoegen `customheaderlibs.html` en `customfooterlibs.html` bestanden.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly> 
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly> 
   ```

   Het bestand customfooterlibs.html wordt gebruikt voor JavaScript en de aangepaste headerlibs.html voor de css.

1. [De pijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) om de wijzigingen te implementeren.

+++

### Een adaptief formulier maken met de adaptieve Forms Container-component {#create-af-using-af-container}


Een adaptief formulier maken met [!UICONTROL Adaptive Forms Container] component:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep vanuit het deelvenster Componentbrowser de **[!UICONTROL Adaptive Forms Container]** op de pagina.
1. Maak een adaptief formulier met de Adaptief Forms-componenten.
1. Sla de instellingen op.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Uw formulier is klaar. Wanneer u de AEM Sites-pagina publiceert, worden automatisch het adaptieve formulier en de bijbehorende middelen waarnaar wordt verwezen, gepubliceerd.

#### Eigenschappen van adaptieve formuliercontainers configureren {#configure-additional-settings-container}

U kunt de geavanceerde instellingen van het dialoogvenster [!UICONTROL Adaptive Form Container] component. Bijvoorbeeld:

* U kunt de Prefill-service zodanig configureren dat een adaptief formulier met vooraf ingevulde waarden op de pagina van een site wordt geladen.
* U kunt de instellingen van het gegevensmodel zo configureren dat het adaptieve formulier wordt gekoppeld aan een gegevensbron.
* U kunt de verzendacties configureren om de gegevens op Microsoft® OneDrive, Microsoft® OneDrive of andere gegevensbronnen te verzenden wanneer een formulier wordt verzonden. U kunt ook een aangepaste verzendactie maken en selecteren voor uw Adaptieve Forms.

De eigenschappen instellen voor de **[!UICONTROL Adaptive Forms Container]** component, klik ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) op de actiebalk. De **[!UICONTROL Edit Adaptive Forms Container]** wordt geopend.

![Dialoogvenster Bewerken](/help/forms/assets/adaptiveformcontainer-editdialog.png)

In de [!UICONTROL Edit Adaptive Forms Container] kunt u het volgende opgeven.
* **Tabblad Standaard**
   * **Prefill-service**: U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. Voor informatie over de Prefill-service raadpleegt u [Aangepaste formuliervelden vooraf invullen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)
   * **Categorie clientbibliotheek**: Geef de [JavaScript-functies](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions) die worden gebruikt in expressies en worden ondersteund door Adaptive Forms.
* **Gegevensmodel**: Met een gegevensmodel kunt u entiteiten en services integreren van verschillende gegevensbronnen tot een adaptief formulier. Kies **[!UICONTROL Form Data Model]** Als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.
   * **Formuliergegevensmodel**: Met een formuliergegevensmodel (FDM) kan een adaptief formulier communiceren met verschillende gegevensbronnen. Voor informatie, bij het vormen van een gegevensbron, zie [Gegevensbronnen configureren](/help/forms/configure-data-sources.md).
   * **Schema**: Het schema vertegenwoordigt de structuur waarin de gegevens door het achterste deelsysteem in uw organisatie worden geproduceerd of worden verbruikt. U kunt [het schema aan een adaptief formulier koppelen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html) en gebruikt de elementen ervan om dynamische inhoud toe te voegen aan een adaptief formulier.

     >[!NOTE]
     >
     > Nadat u het formuliergegevensmodel (FDM) hebt geconfigureerd, kunt u het bijbehorende formuliermodel niet meer wijzigen. Het is echter mogelijk het schema te wijzigen dat is gekoppeld aan het formuliergegevensmodel (FDM).

* **Tabblad Verzending**

   * **Omleiden naar URL**
      * **URL/pad omleiden**: Hiermee geeft u de URL of het pad op waarnaar een adaptief formulier na de verzending wordt omgeleid.

      * **Handeling verzenden**: Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt [De verzendactie configureren op adaptief formulier](/help/forms/configuring-submit-actions.md). Adaptieve formulieren bieden de volgende verzendacties uit het vak:
         * Verzenden naar REST-eindpunt
         * E-mail verzenden
         * Verzenden met gebruik van FDM (Form Data Model)
         * Een AEM-workflow aanroepen
         * Verzenden naar SharePoint
         * Verzenden naar OneDrive
         * Verzenden naar Azure Blob Storage

  U kunt [De standaardverzendhandelingen uitbreiden](custom-submit-action-form.md) om uw eigen aangepaste verzendhandeling te maken.

* **Bericht tonen**
   * **Berichtinhoud**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.

## Een adaptief formulier insluiten  {#aem-container-component}

Gebruiken **[!UICONTROL Adaptive Forms - Embed (V2)]** kunt u een nieuw adaptief formulier insluiten of een bestaand adaptief formulier insluiten op de pagina van de site. De [!UICONTROL Adaptive Forms - Embed(v2)] kunt u:

* [Een bestaand adaptief formulier toevoegen](#embed-new-af)

* [Een nieuw adaptief formulier maken en toevoegen](#embed-existing-af)

### Vereisten {#prerequisites}

+++ De optie **Adaptieve Forms - Insluiten** component.

Inschakelen [!UICONTROL Adaptive Forms - Embed(v2)] in het sjabloonbeleid voert u de volgende stappen uit:

1. Ga naar de [!UICONTROL Page Information] > [!UICONTROL Edit Template]

1. Klik op de knop [!UICONTROL Policy] en selecteert u de **[!UICONTROL Adaptive Form - Embed (v2)]** selectievakje onder **[!UICONTROL [AEM Archetype Project Name] - Forms]** groep .
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Inclusief Adaptieve Forms-clientbibliotheken naar AEM Sites-pagina

Wanneer de **[!UICONTROL When form covers entire width of a page]** is geselecteerd in het dialoogvenster **[!UICONTROL Form Containers]** configureren, dialoogvenster en **Adaptieve Forms met behulp van kerncomponenten** worden gebruikt, is het noodzakelijk om de clientlibs op te nemen op de corresponderende pagina van de Site.

![GIF-bedekking](/help/forms/assets/overlaycorecomponent.gif)

Als u Adaptieve Forms-componenten wilt gebruiken op een AEM Sites-pagina, neemt u de opdracht `Customheaderlibs` en `Customfooterlibs` clientbibliotheken naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository en distributiepijplijn.

1. Open uw [AEM Forms Archetype of Cloned Git Repository](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een teksteditor. Bijvoorbeeld, de Code van Visual Studio.
1. Navigeren naar `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml`.
1. De waarde kopiëren van `sling:resourceSuperType`. De waarde is bijvoorbeeld `core/wcm/components/page/v3/page`.

   ![slingerbron](/help/forms/assets/slingresource.png)

1. Een vergelijkbare structuur maken op de locatie `ui.apps/src/main/content/jcr_root/apps` gelijk aan `core/wcm/components/page/v3/page`.

   ![bedekkingsstructuur](/help/forms/assets/overlaystructure.png)

1. Toevoegen `customheaderlibs.html` en `customfooterlibs.html` bestanden.

   ```
   //Customheaderlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
       data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
       <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
   </sly>
   
   //customfooterlibs.html
   <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html"
     data-sly-use.form="com.adobe.cq.forms.core.components.models.aemform.AEMForm">
     <sly data-sly-test="${form.formVersion=='2.1' && !wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
   </sly>
   ```

   De `customfooterlibs.html` wordt gebruikt voor JavaScript en `customheaderlibs.html` voor de CSS.

1. [De pijplijn uitvoeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) om de wijzigingen te implementeren.

+++

### Een bestaand adaptief formulier toevoegen aan de AEM Sites-pagina {#embed-existing-af}

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep vanuit het deelvenster Componentbrowser de [!UICONTROL Adaptive Forms - Embed] op de pagina.
1. Selecteer de [!UICONTROL Adaptive Forms - Embed] in de sitepagina en selecteert u ![settings_icon](/help/forms/assets/Smock_Wrench_18_N.svg) op de actiebalk. De **[!UICONTROL Edit Adaptive Forms - Embed]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het dialoogvenster [!UICONTROL Asset Path].
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### Nieuwe pagina Adaptief formulier maken en toevoegen aan AEM Sites {#embed-new-af}

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep vanuit het deelvenster Componentbrowser de [!UICONTROL Adaptive Forms - Embed(v2)] op de pagina.
1. Klik op de knop **Plus** en wordt u omgeleid naar de wizard Formulier maken.

   ![Adaptieve Forms - component insluiten](/help/forms/assets/aemformcontainer.png)

1. Een nieuw adaptief formulier maken met de opdracht [!UICONTROL Form Creation] wizard.
1. De [!UICONTROL Asset Path] bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### Adaptief formulier configureren - eigenschappen voor insluiten (v2) {#configure-adaptive-form-embed}

U kunt de geavanceerde instellingen van het dialoogvenster [!UICONTROL Adaptive Form - Embed(v2)] component. In de [!UICONTROL Edit Adaptive Forms - Embed(v2)] kunt u het volgende opgeven.

* **Middelpad**: Blader naar het adaptieve formulier dat u wilt insluiten en selecteer dit. Deze wordt automatisch ingevuld als u deze uit de middelenbrowser hebt verwijderd.
* **Verzending na verzending** : Selecteer de actie die moet worden geactiveerd bij het verzenden van het formulier. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.
   * **Bericht met dank weergeven**: Schrijf een bericht met de teksteditor Rich die moet worden weergegeven bij het verzenden van formulieren. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
   * **Dankpagina tonen**: Blader en selecteer de pagina die u wilt weergeven bij het verzenden van het formulier. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Doorverwijzen naar pagina voor bedankt**: Schakel deze optie in om de pagina met het ingesloten adaptieve formulier te vervangen door de pagina Hartelijk dank. Anders vervangt de pagina Bedankt het Adaptief formulier in het dialoogvenster [!UICONTROL Adaptive Forms - Embed] zonder onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
* **Paginataal gebruiken**: Gebruik de landinstelling van de AEM Sites-pagina in plaats van Adaptief formulier.
* **Focus op formulier instellen**: Selecteer deze optie om de focus in te stellen op het eerste veld van het adaptieve formulier.
* **Het formulier bedekt de volledige breedte van het kader**: Indien ingeschakeld, wordt iframe niet gebruikt om het formulier te genereren.
* **Hoogte**: Geef de hoogte van de container op. Laat deze leeg om de grootte van de container automatisch te wijzigen.
* **CSS-clientbibliotheek**: Geef het pad op naar een CSS-clientbibliotheek.

### Toegevoegde adaptieve Forms publiceren met behulp van adaptief formulier - Embed(v2)-component  {#publish-embedded-adaptive-form}

Overweeg de volgende scenario&#39;s voor het publiceren van toegevoegde Adaptieve Forms die de **[!UICONTROL Adaptive Form - Embed(v2)]** component:

* Wanneer u een AEM Sites-pagina voor het eerst publiceert, worden de formulieren die aan de sitepagina zijn toegevoegd, automatisch gepubliceerd.
* Wanneer u een adaptief formulier wijzigt dat u toevoegt aan een reeds gepubliceerde sitepagina, moet u de bijbehorende Adaptief Forms handmatig publiceren.
* Wanneer u een pagina Sites en de overeenkomstige Adaptieve Forms wijzigt, publiceert u de pagina Sites en alle Adaptieve Forms die aan de pagina Sites is toegevoegd opnieuw.

### Toegevoegde adaptieve Forms wijzigen met adaptieve vorm - Insluiten (v2) component  {#modifying-embedded-adaptive-form}

Voer een van de volgende handelingen uit om een configuratie of eigenschap van een adaptief formulier te wijzigen:

* Open het oorspronkelijke formulier in een adaptief formulier in de desbetreffende editor en wijzig deze.
* Selecteer het adaptieve formulier in de bewerkingsmodus van de sitepagina en selecteer vervolgens **[!UICONTROL Edit in a new window]**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

## Lay-out wijzigen van een adaptief formulier dat is toegevoegd aan een AEM Sites-pagina {#change-layout-af-aem-sites-page}

Op de AEM Sites-pagina [Lay-outmodus](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode) Hiermee kunt u het formaat wijzigen van een adaptief formulier dat is gemaakt of toegevoegd aan een AEM Sites-pagina.

![AF-layout-support](/help/forms/assets/afsite-layoutsupport.gif)

AEM sitepagina bevat een verwijzing naar het adaptieve formulier. Wanneer u een AEM Sites-pagina vertaalt, worden automatisch een adaptief formulier en de bijbehorende middelen waarnaar wordt verwezen, omgezet met de [vertaalprojecten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job) in andere talen.

## Aanbevolen procedures {#best-practices}

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de Forms Portal.

>[!MORELIKETHIS]
>
>* [Aangepast formulier insluiten op basis van kerncomponenten op een externe webpagina](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
>* [Aangepast formulier insluiten in externe webpagina](/help/forms/embed-adaptive-form-external-web-page.md)