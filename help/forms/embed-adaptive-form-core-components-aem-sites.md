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

* **creeer een Aangepast Vorm gebruikend de Aangepaste component van de Container van Forms**: De [ AanpassingsContainer van de Vorm ](#af-container-component) component laat u digitale inschrijvingservaringen bouwen door de Aangepaste componenten van Forms direct binnen de redacteur van AEM Sites te gebruiken. Deze integratie biedt een naadloze ervaring voor AEM Sites-auteurs die formulieren op hun AEM Sites-pagina&#39;s willen maken en beheren.

* **voeg een bestaande Aangepaste Vorm** toe: [ Aangepaste Forms - bed (v2) in ](#embed-existing-af) component laat u gemakkelijk een reeds bestaande Aangepaste Vorm in een pagina binnen AEM Sites toevoegen. Deze functie verbetert het aanpassingsvermogen en de herbruikbaarheid van Adaptive Forms. Deze integratie biedt klanten een handige manier om Adaptive Forms die ze al hebben gemaakt opnieuw te gebruiken.

* **Aangepaste Tovenaar van Forms van het Gebruik om een vorm** tot stand te brengen: Gebruik [ Aangepaste Forms - bed (v2) in ](#embed-new-af) component om een AanpassingsVorm van binnen de redacteur van AEM Sites tot stand te brengen gebruikend de tovenaar van de Aanmaak van de Vorm. Het formulier wordt opgeslagen als een externe entiteit. U kunt dit formulier ook hergebruiken in andere sitepagina&#39;s en op zichzelf staande formulieren.

* **voeg veelvoudige Aangepaste Forms in een pagina van AEM Sites** toe: Om veelvoudige Aanpassings Forms in een pagina van AEM Sites toe te voegen, gebruik de de containercomponenten van AEM Forms - [ Aangepaste Forms - bed (v2) ](#embed-new-af) en [ Aangepaste Container van de Vorm ](#af-container-component) in. Als u meer dan één adaptief formulier als div-element wilt toevoegen aan een AEM Sites-pagina, kunt u de component Adaptief formuliercontainer gebruiken.

U kunt de Redacteur van de Regel gebruiken om het dynamische gedrag van de Adaptieve componenten van de Vorm toe te voegen of te controleren. U kunt bijvoorbeeld een component verbergen of weergeven. De Rule Editor is niet beschikbaar voor niet-adaptieve formuliercomponenten. Gebruik dus uw zorgvuldigheid bij het gebruik van niet-adaptieve formuliercomponenten in de AEM Forms Container-component.

## Een adaptief formulier maken met de adaptieve Forms Container-component {#af-container-component}

Met de component [!UICONTROL Adaptive Form Container] kunt u digitale inschrijvingen maken met behulp van Adaptieve Forms-componenten in de AEM Sites-editor. U kunt een adaptief formulier maken door de formuliercomponenten te slepen en neer te zetten.

### Vereisten {#prerequisites-af-container}

+++ Schakel **[!UICONTROL Adaptive Forms Container]** in.

Voer de volgende stappen uit om [!UICONTROL Adaptive Forms Container] -component in sjabloonbeleid in te schakelen:

1. Ga naar [!UICONTROL Page Information] > [!UICONTROL Edit Template]
1. Klik [!UICONTROL Policy] en selecteer **[!UICONTROL Adaptive Forms Container]** checkbox onder **[AEM de Naam van het Project van Archetype ] - Aangepaste Vorm**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

+++ Inclusief Adaptieve Forms-clientbibliotheken naar AEM Sites-pagina

Als u Aangepaste Forms-componenten op een AEM Sites-pagina wilt gebruiken, neemt u de Client libraries Customheaderlibs en Customfooterlibs op naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository and Deployment-pijplijn.

1. Open uw [ Archetype van AEM Forms of het gekloonde project van de Bewaarplaats van de it ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een tekstredacteur. Bijvoorbeeld, de Code van Visual Studio.
1. Navigeer naar `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml` .
1. Kopieer de waarde van `sling:resourceSuperType` . De waarde is bijvoorbeeld `core/wcm/components/page/v3/page` .

   ![ sling middel ](/help/forms/assets/slingresource.png)

1. Maak een vergelijkbare structuur op dezelfde locatie `ui.apps/src/main/content/jcr_root/apps` als `core/wcm/components/page/v3/page` .

   ![ bekledingsstructuur ](/help/forms/assets/overlaystructure.png)

1. Voeg `customheaderlibs.html` - en `customfooterlibs.html` -bestanden toe.

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

   De customfooterlibs.html wordt gebruikt voor JavaScript en customheaderlibs.html voor css.

1. [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) in werking om de veranderingen op te stellen.

+++

### Een adaptief formulier maken met de adaptieve Forms Container-component {#create-af-using-af-container}


Een adaptief formulier maken met de component [!UICONTROL Adaptive Forms Container] :

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms Container]** vanuit het deelvenster Componentbrowser naar de pagina.
1. Maak een adaptief formulier met de Adaptief Forms-componenten.
1. Sla de instellingen op.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Uw formulier is klaar. Wanneer u de AEM Sites-pagina publiceert, worden automatisch het adaptieve formulier en de bijbehorende middelen waarnaar wordt verwezen, gepubliceerd.

#### Eigenschappen van adaptieve formuliercontainers configureren {#configure-additional-settings-container}

U kunt de geavanceerde instellingen van de component [!UICONTROL Adaptive Form Container] aanpassen. Bijvoorbeeld:

* U kunt de Prefill-service zodanig configureren dat een adaptief formulier met vooraf ingevulde waarden op de pagina van een site wordt geladen.
* U kunt de instellingen van het gegevensmodel zo configureren dat het adaptieve formulier wordt gekoppeld aan een gegevensbron.
* U kunt de verzendacties configureren om de gegevens op Microsoft® OneDrive, Microsoft® OneDrive of andere gegevensbronnen te verzenden wanneer een formulier wordt verzonden. U kunt ook een aangepaste verzendactie maken en selecteren voor uw Adaptieve Forms.

Om de eigenschappen voor de **[!UICONTROL Adaptive Forms Container]** component te plaatsen, klik ![ settings_icon ](/help/forms/assets/Smock_Wrench_18_N.svg) op de actiebar. Het dialoogvenster **[!UICONTROL Edit Adaptive Forms Container]** wordt geopend.

![ geef Dialoog ](/help/forms/assets/adaptiveformcontainer-editdialog.png) uit

In het dialoogvenster [!UICONTROL Edit Adaptive Forms Container] kunt u het volgende opgeven.
* **BasisLusje**
   * **vooraf ingevulde Dienst**: U kunt de prefill dienst gebruiken om gebieden van een Aangepast Vorm te vullen gebruikend bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. Voor informatie over de prefill dienst, zie [ Prefill de Aangepaste gebieden van de Vorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/prepopulate-adaptive-form-fields.html#configuring-prefill-service-using-configuration-manager)
   * **de bibliotheekcategorie van de Cliënt**: Specificeer de [ functies van JavaScript ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#custom-functions) die in uitdrukkingen worden gebruikt en door Adaptief Forms worden gesteund.
* **Model van Gegevens**: Een Model van Gegevens laat u entiteiten en de diensten van verschillende gegevensbronnen aan een AanpassingsVorm integreren. Kies **[!UICONTROL Form Data Model]** als het adaptieve formulier dat u maakt, bestaat uit het ophalen en schrijven van gegevens van en naar meerdere gegevensbron.
   * **het gegevensmodel van de Vorm**: Een Model van de Gegevens van de Vorm (FDM) laat een Aangepast Vorm met ongelijksoortige gegevensbronnen communiceren. Voor informatie, bij het vormen van een gegevensbron, zie [ gegevensbronnen ](/help/forms/configure-data-sources.md) vormen.
   * **Schema**: Het schema vertegenwoordigt de structuur waarin het gegeven wordt geproduceerd of door het achterste deelsysteem in uw organisatie verbruikt. U kunt [ het schema aan een AanpassingsVorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/adaptive-form-json-schema-form-model.html) associëren en zijn elementen gebruiken om dynamische inhoud aan een AanpassingsVorm toe te voegen.

     >[!NOTE]
     >
     > Nadat u het formuliergegevensmodel (FDM) hebt geconfigureerd, kunt u het bijbehorende formuliermodel niet meer wijzigen. Het is echter mogelijk het schema te wijzigen dat is gekoppeld aan het formuliergegevensmodel (FDM).

* **het Lusje van de Verzending**

   * **richt aan URL** opnieuw
      * **Redirect URL/Weg**: Specificeert URL of weg waaraan een Aangepast Vorm na de voorlegging opnieuw wordt gericht.

      * **legt Actie** voor: Een verzendactie wordt teweeggebracht wanneer een gebruiker de Submit knoop op een AanpassingsVorm klikt. U kunt [ vormen voorlegt actie op AanpassingsVorm ](/help/forms/configuring-submit-actions.md). Adaptieve formulieren bieden de volgende verzendacties uit het vak:
         * Verzenden naar REST-eindpunt
         * E-mail verzenden
         * Verzenden met gebruik van FDM (Form Data Model)
         * Een AEM-workflow aanroepen
         * Verzenden naar SharePoint
         * Verzenden naar OneDrive
         * Verzenden naar Azure Blob Storage

  U kunt [ ook uitbreiden het gebrek verzendt Acties ](custom-submit-action-form.md) om uw eigen douane tot stand te brengen verzendt Actie.

* **toon Bericht**
   * **Inhoud van het Bericht**: Schrijf een bericht gebruikend de rijke tekstredacteur om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.

## Een adaptief formulier insluiten  {#aem-container-component}

Met **[!UICONTROL Adaptive Forms - Embed (V2)]** kunt u een nieuw adaptief formulier insluiten of een bestaand adaptief formulier insluiten op de pagina van de site. Met de component [!UICONTROL Adaptive Forms - Embed(v2)] kunt u:

* [Een bestaand adaptief formulier toevoegen](#embed-new-af)

* [Een nieuw adaptief formulier maken en toevoegen](#embed-existing-af)

### Vereisten {#prerequisites}

+++ Laat **Aangepaste Forms toe - bed** component in.

Voer de volgende stappen uit om [!UICONTROL Adaptive Forms - Embed(v2)] -component in sjabloonbeleid in te schakelen:

1. Ga naar [!UICONTROL Page Information] > [!UICONTROL Edit Template]

1. Klik op [!UICONTROL Policy] en selecteer het selectievakje **[!UICONTROL Adaptive Form - Embed (v2)]** onder de groep **[!UICONTROL [AEM Archetype Project Name] - Forms]** .
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419369?quality=12&learn=on)

+++

+++ Inclusief Adaptieve Forms-clientbibliotheken naar AEM Sites-pagina

Wanneer de **[!UICONTROL When form covers entire width of a page]** optie in **[!UICONTROL Form Containers]** wordt geselecteerd vormt dialoogdoos en **Aangepaste Forms gebruikend kerncomponenten** wordt gebruikt, is het noodzakelijk om de clientlibs op de overeenkomstige pagina van de Plaats te omvatten.

![ Bedekking Gif ](/help/forms/assets/overlaycorecomponent.gif)

Als u Adaptieve Forms-componenten wilt gebruiken in een AEM Sites-pagina, neemt u de `Customheaderlibs` - en `Customfooterlibs` -clientbibliotheken op naar de AEM Sites-pagina met behulp van de AEM Archetype/Git Repository and Deployment-pijplijn.

1. Open uw [ Archetype van AEM Forms of het gekloonde project van de Bewaarplaats van de it ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) in een tekstredacteur. Bijvoorbeeld, de Code van Visual Studio.
1. Navigeer naar `ui.apps/src/main/content/jcr_root/apps/corecomponents/components/page/.content.xml` .
1. Kopieer de waarde van `sling:resourceSuperType` . De waarde is bijvoorbeeld `core/wcm/components/page/v3/page` .

   ![ sling middel ](/help/forms/assets/slingresource.png)

1. Maak een vergelijkbare structuur op dezelfde locatie `ui.apps/src/main/content/jcr_root/apps` als `core/wcm/components/page/v3/page` .

   ![ bekledingsstructuur ](/help/forms/assets/overlaystructure.png)

1. Voeg `customheaderlibs.html` - en `customfooterlibs.html` -bestanden toe.

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

   `customfooterlibs.html` wordt gebruikt voor JavaScript en `customheaderlibs.html` voor CSS.

1. [ stel de pijpleiding ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/site-creation/enable-front-end-pipeline.html) in werking om de veranderingen op te stellen.

+++

### Een bestaand adaptief formulier toevoegen aan de AEM Sites-pagina {#embed-existing-af}

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component [!UICONTROL Adaptive Forms - Embed] vanuit het deelvenster Componentbrowser naar de pagina.
1. Selecteer de [!UICONTROL Adaptive Forms - Embed] component in de plaatspagina en selecteer ![ settings_icon ](/help/forms/assets/Smock_Wrench_18_N.svg) op de actiebar. Het dialoogvenster **[!UICONTROL Edit Adaptive Forms - Embed]** wordt geopend.
1. Blader naar het adaptieve formulier dat u wilt insluiten in het [!UICONTROL Asset Path] en selecteer dit.
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419368?quality=12&learn=on)



### Nieuwe pagina Adaptief formulier maken en toevoegen aan AEM Sites {#embed-new-af}

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component [!UICONTROL Adaptive Forms - Embed(v2)] vanuit het deelvenster Componentbrowser naar de pagina.
1. Klik **plus** pictogram en u wordt opnieuw gericht aan de tovenaar van de vormverwezenlijking.

   ![ Aangepaste Forms - bed Component ](/help/forms/assets/aemformcontainer.png) in

1. Maak een nieuw adaptief formulier via de wizard [!UICONTROL Form Creation] .
1. Het [!UICONTROL Asset Path] bevat al het pad van een gemaakt adaptief formulier
1. Sla de instellingen op. Het adaptieve formulier is nu ingesloten in de pagina.

>[!VIDEO](https://video.tv.adobe.com/v/3419366/adaptive-form-aem-forms?quality=12&learn=on)

#### Adaptief formulier configureren - eigenschappen voor insluiten (v2) {#configure-adaptive-form-embed}

U kunt de geavanceerde instellingen van de component [!UICONTROL Adaptive Form - Embed(v2)] aanpassen. In het dialoogvenster [!UICONTROL Edit Adaptive Forms - Embed(v2)] kunt u het volgende opgeven.

* **Weg van Activa**: doorblader en selecteer de Aangepaste Vorm om in te bedden. Deze wordt automatisch ingevuld als u deze uit de Assets-browser hebt verwijderd.
* **de Verzending van Post**: Selecteer de actie om op vormvoorlegging teweeg te brengen. U kunt ervoor kiezen om een bedankbericht of een pagina voor bedankt weer te geven.
   * **toon Dank u Bericht**: Schrijf een bericht gebruikend de rijke tekstredacteur om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar als u een bedankbericht wilt weergeven.
   * **toon Dank u Pagina**: doorblader en selecteer de pagina om op vormvoorlegging te tonen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
   * **Redirect om u pagina** te danken: Laat de optie toe om de pagina te vervangen die de ingebedde Aangepaste Vorm met dank u pagina bevat. Anders vervangt de pagina Hartelijk dank u het Adaptieve formulier in de component [!UICONTROL Adaptive Forms - Embed] zonder de onderliggende sites op de pagina te vernieuwen. Deze optie is alleen beschikbaar wanneer u een pagina voor bedankt weergeeft.
* **Taal van de Pagina van het Gebruik**: Gebruik lokaal van de pagina van AEM Sites in plaats van scène van AanpassingsVorm.
* **plaats Focus op Vorm**: Uitgezocht om de nadruk op het eerste gebied van de Aangepaste Vorm te plaatsen.
* **de Vorm behandelt volledige breedte van het kader**: Als gecontroleerd, wordt iframe niet gebruikt om de vorm terug te geven.
* **Hoogte**: Specificeer de hoogte van de container. Laat deze leeg om de grootte van de container automatisch te wijzigen.
* **CSS de bibliotheek van de Cliënt**: Specificeer weg aan een CSS cliëntbibliotheek.

### Publish heeft Adaptive Forms toegevoegd met Adaptive Form - Embed(v2)-component  {#publish-embedded-adaptive-form}

Overweeg de volgende scenario&#39;s voor het publiceren van toegevoegde Adaptieve Forms met behulp van de component **[!UICONTROL Adaptive Form - Embed(v2)]** :

* Wanneer u een AEM Sites-pagina voor het eerst publiceert, worden de formulieren die aan de sitepagina zijn toegevoegd, automatisch gepubliceerd.
* Wanneer u een adaptief formulier wijzigt dat u toevoegt aan een reeds gepubliceerde sitepagina, moet u de bijbehorende Adaptief Forms handmatig publiceren.
* Wanneer u een pagina Sites en de overeenkomstige Adaptieve Forms wijzigt, publiceert u de pagina Sites en alle Adaptieve Forms die aan de pagina Sites is toegevoegd opnieuw.

### Toegevoegde adaptieve Forms wijzigen met adaptieve vorm - Insluiten (v2) component  {#modifying-embedded-adaptive-form}

Voer een van de volgende handelingen uit om een configuratie of eigenschap van een adaptief formulier te wijzigen:

* Open het oorspronkelijke formulier in een adaptief formulier in de desbetreffende editor en wijzig deze.
* Selecteer het adaptieve formulier in de bewerkingsmodus van de sitepagina en selecteer vervolgens **[!UICONTROL Edit in a new window]** . Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus die u kunt wijzigen.

## Lay-out wijzigen van een adaptief formulier dat is toegevoegd aan een AEM Sites-pagina {#change-layout-af-aem-sites-page}

In de pagina van AEM Sites, laat de [ wijze van de Lay-out ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/authoring/features/responsive-layout.html?#defining-layouts-layout-mode) u toe om een Aangepast Vorm resize dat wordt gecreeerd of aan een pagina van AEM Sites toegevoegd.

![ AF-lay-out-steun ](/help/forms/assets/afsite-layoutsupport.gif)

AEM sitepagina bevat een verwijzing naar het adaptieve formulier. Wanneer u een pagina van AEM Sites vertaalt, vertaalt het automatisch een AanpassingsVorm en zijn bijbehorende referenced activa gebruikend de [ vertaalprojecten ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/reusing-content/translation/managing-projects.html?lang=en#adding-pages-assets-to-a-translation-job) in andere talen.

## Aanbevolen procedures {#best-practices}

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de Forms Portal.

>[!MORELIKETHIS]
>
>* [ bed adaptieve vorm in die op kerncomponenten aan een externe Web-pagina wordt gebaseerd ](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
>* [ bed adaptieve vorm in externe Web-pagina ](/help/forms/embed-adaptive-form-external-web-page.md) in