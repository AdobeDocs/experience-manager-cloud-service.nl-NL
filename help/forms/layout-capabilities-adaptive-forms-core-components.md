---
title: Wat zijn de lay-outmogelijkheden van Adaptive Forms gebaseerd op kerncomponenten?
description: De lay-out en vormgeving van Adaptief Forms op verschillende apparaten worden bepaald door de lay-outinstellingen. Begrijp de verschillende lay-outs en hoe te om hen toe te passen.
feature: Adaptive Forms, Core Components
keywords: Indeling van adaptief formulier op basis van kerncomponenten, verschillende indelingen voor formulieren, dynamische formulierindelingen AEM, AEM Cloud Service-formulierindelingen, formulierindelingstypen in AEM kerncomponenten, adaptieve formulierindelingen
role: User, Developer, Admin
exl-id: dcc01d84-0d39-4fa8-ac47-71a9aba91b1e
source-git-commit: 7cb963794ca0d7a12d8007564c9fd6e49b53d5c4
workflow-type: tm+mt
source-wordcount: '2091'
ht-degree: 0%

---

# Lay-outmogelijkheden van adaptieve Forms op basis van kerncomponenten


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html) |
| AEM as a Cloud Service (Foundation Components) | [ klik hier ](/help/forms/layout-capabilities-adaptive-forms.md) |
| AEM as a Cloud Service (Core Components) | Dit artikel |

Adaptive Forms biedt eersteklas componenten om de formulieren effectief in te delen en te ontwerpen. De indeling bepaalt hoe componenten in een formulier worden weergegeven. Adaptieve Forms biedt ondersteuning voor verschillende lay-outs: deelvenster, wizard, accordeon, tabs op horizontale/bovenste tabbladen en tabbladen op links/verticale tabbladen.

<!-- ![Types of Layout](/help/forms/assets/generic-layout-hero-image.png){align="center"}-->

## Voorwaarde

Voordat u de verschillende mogelijkheden van een lay-out gaat verkennen, moet u ervoor zorgen dat de kerncomponenten zijn ingeschakeld voor uw omgeving. Voor gedetailleerde instructies op hoe te om kerncomponenten voor uw milieu toe te laten, [ klik hier ](/help/forms/enable-adaptive-forms-core-components.md).

## Aangepaste Forms-lay-outtypen

Adaptief formulier op basis van kerncomponenten ondersteunt de volgende typen indelingen:
* **lay-out van het Comité**
* **lay-out van de Tovenaar**
* **Verticale lay-out**
* **Horizontale lay-out**
* **de lay-out van de Accordeon**

>[!BEGINTABS]

>[!TAB  Lay-out van het Comité ]

De indeling van deelvensters is handig om verwante velden zo te ordenen dat u gemakkelijker kunt navigeren en de bijbehorende inhoud kunt vinden. In de indeling van het deelvenster worden formuliercomponenten in afzonderlijke secties of deelvensters gerangschikt in een adaptief formulier.

![ Lay-out van het Comité ](/help/forms/assets/panel-layout.png)

Layout deelvenster

U kunt de [ paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel) gebruiken om de paneellay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om diverse eigenschappen van de paneelcomponent te vormen, verwijs naar het [ artikel van de paneelcomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/panel).

>[!TAB  Lay-out van de Tovenaar ]

De indeling van de wizard helpt een complex formulier te vereenvoudigen door het op te splitsen in afzonderlijke stappen. Elke stap vertegenwoordigt een verschillend deel van het proces, en de gebruikers navigeren opeenvolgend door de stappen, vaak met **Volgende** en **Vorige** knopen. U kunt de indeling van de wizard gebruiken om een formulier te maken dat uit meerdere secties of stappen bestaat.

![ Lay-out van de Tovenaar ](/help/forms/assets/wizard-layout-compare.gif)

Wizard Layout

U kunt de [ tovenaar component ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard) gebruiken om de tovenaarslay toe te voegen in een vorm. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de tovenaarscomponent te vormen, verwijs naar het [ artikel van de tovenaarscomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/wizard).

>[!TAB  Verticale Lay-out van Lusjes ]

De lay-out van verticale tabbladen wordt ook wel tabbladen in de linkerlay-out genoemd. Met de verticale tabs-indeling ordent u deelvensters of secties langs de linkerzijde van een formulier. Dit is een algemene indeling voor formulieren waarbij deelvensters/secties verticaal worden gestapeld om gemakkelijk te kunnen lezen en navigeren.

![ Verticale Lay-out ](/help/forms/assets/vertical-tab.gif)

Lay-out verticale tabs

U kunt de [ verticale component van lusjes ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs) gebruiken om de verticale lusjelay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de verticale component van lusjes te vormen, verwijs naar het [ verticale artikel van de luscomponent van lusjes ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs).


>[!TAB  Horizontale Lay-out van Lusjes ]

De lay-out Horizontale tabbladen wordt ook wel Tabs in de bovenste lay-out genoemd. Met de lay-out Horizontale tabbladen rangschikt u deelvensters of secties naast elkaar in een rij. In deze indeling worden de formuliersecties lineair weergegeven over de breedte van het formulier of deelvenster.


![ Horizontale Lay-out ](/help/forms/assets/horizontal-layout.gif)

Lay-out horizontale tabs

U kunt de [ horizontale component van lusjes ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs) gebruiken om de horizontale lusjelay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de horizontale component van lusjes te vormen, verwijs naar het [ horizontale artikel van de lussencomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/horizontal-tabs).


>[!TAB  Lay-out van de Accordeon ]

De accordeonindeling geeft de inhoud in inklapbare secties of deelvensters weer in een adaptief formulier. Wanneer een sectie wordt uitgevouwen, geeft deze de inhoud binnen weer, terwijl andere secties worden samengevouwen. Deze indeling is ideaal voor het weergeven van grote hoeveelheden gegevens in een compacte vorm.

![ Lay-out van de Accordeon ](/help/forms/assets/accordion-layout-compare.gif)

Accordeonlay-out

U kunt de [ accordeoncomponent ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) gebruiken om de accordeonlay-out in een vorm toe te voegen. Voor gedetailleerde instructies op hoe te om de diverse eigenschappen van de accordeoncomponent te vormen, verwijs naar het [&#128279;](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/accordion) artikel van de component 0&rbrace; accordeon &lbrace;.

>[!ENDTABS]

Leren hoe te om een lay-out op te nemen en vormcomponenten aan het toe te voegen, verwijs naar de sectie genoemd [ hoe te om een lay-out op te nemen en vormcomponenten aan het toe te voegen?](#how-to-insert-a-layout-and-add-form-components-to-it)

### Hoe kunt u de juiste indeling voor adaptief formulier kiezen?

Het is belangrijk dat u de juiste indeling voor Adaptief formulier selecteert om de gebruikerservaring en de functionaliteit van formulieren te optimaliseren. De tabel geeft u inzicht in de verschillende beschikbare lay-outopties en helpt u bij het selecteren van de meest geschikte lay-out op basis van uw specifieke behoeften en gebruiksgevallen:

| Functie | Layout deelvenster | Wizard Layout | Tabs op de lay-out Boven/Verticaal tabs | Tabs op de lay-out Linkertabs/Horizontale tabs | Accordeonlay-out |
|--------------------------|-----------------------------------------------------|----------------------------------------------------|-----------------------------------------------------|--------------------------------------------------------|--------|
| **Doel** | Hiermee groepeert u gerelateerde inhoud in afzonderlijke secties | Hiermee worden gebruikers door een proces of formulier met meerdere stappen geleid | Hiermee kunt u schakelen tussen secties/weergaven op dezelfde pagina | Vergelijkbaar met bovenste tabbladen, maar verticaal links gerangschikt | Inhoud indelen in inklapbare secties |
| **Structuur** | Afzonderlijke secties | Opeenvolgende stappen/pagina&#39;s | Horizontale tabbladen boven | Verticale tabbladen aan de linkerkant | Inklapbare deelvensters/secties |
| **Navigatie** | Klik op de kopteksten van het deelvenster om te navigeren | - Voorwaarts: &quot;Volgende&quot;knoop <br> - Achteruit: &quot;Achtergrond&quot;knoop <br> - Facultatieve het overslaan stappen | Klik op tabbladen om te schakelen tussen secties | Klik op tabbladen om te schakelen tussen secties | Klik op kopteksten om secties uit te vouwen/samen te vouwen |
| **Ervaring van 0&rbrace; Gebruiker** | Hiermee ordent u grote hoeveelheden inhoud op een beheerbare manier | Stapsgewijze begeleiding, waardoor de overweldigende | Duidelijk, toegankelijke omschakeling tussen meningen | Efficiënt gebruik van verticale ruimte, altijd zichtbare tabbladen | Compacte weergave met uitgevouwen/samengevouwen secties |
| **Geval van het Gebruik** | Complexe formulieren met gecategoriseerde secties | Installatieprocessen, complexe formulieren | Instellingen of inhoudscategorieën ordenen | Dashboards, complexe gegevensweergaven | Veelgestelde vragen, instellingenmenu&#39;s, gedetailleerde inhoudssecties |


## Hoe te om een lay-out op te nemen en vormcomponenten aan het toe te voegen?

In het onderstaande diagram worden de stappen weergegeven voor het invoegen van een indeling in een formulier en het toevoegen van formuliercomponenten aan het formulier:

![ Werkschema om een lay-out en vormcomponenten toe te voegen ](/help/forms/assets/workflow-to-add-component-to-a-layout.png)

Overweeg de **Vorm van het Verzoek van IT** in de [ AanpassingsForms sectie van de Lay-out van de Lay-out ](#adaptive-forms-layout-types) wordt getoond. Het formulier verzamelt informatie van werknemers die technische problemen ondervinden met betrekking tot hun netwerk of laptop. Het bevat drie deelvensters:

* **de Details van de Werknemer**: Het paneel verzamelt informatie over de werknemer en bevat drie textboxes geëtiketteerd Naam, E-mail identiteitskaart, en Afdeling.

* **Details van het Probleem**: Het paneel vangt details over de kwestie. Het omvat checkbox voor de probleemcategorie met drie opties: Netwerk, Computer, of andere. Het bevat ook twee tekstvakken met het label Opgeven en Opmerkingen.

* **Gehechtheid**: Het paneel staat gebruikers toe om ondersteunende documenten met betrekking tot het probleem te uploaden.

Laten we het stapsgewijze proces verkennen om een lay-out in te voegen en er componenten aan toe te voegen. In dit voorbeeld wordt een horizontale tabs-indeling ingevoegd in een formulier.

### 1. Een indelingscomponent invoegen in een formulier

1. Meld u aan bij uw [!DNL Experience Manager Forms] -instantie.
1. Selecteer in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Open een bestaand adaptief formulier in een bewerkingsmodus als dit al is gemaakt.

   ![ Open een AanpassingsVorm ](/help/forms/assets/insert-layout.png)

   Alternatief, kunt u [ nieuwe AanpassingsVorm ](/help/forms/creating-adaptive-form-core-components.md) ook creëren.

1. Zoek de sectie in de formuliereditor waarin u een indeling kunt toevoegen.

   ![ redacteur van de Vorm ](/help/forms/assets/form-editor.png)
1. Klik **toevoegen** pictogram. Het pictogram is een plusteken (+) waarmee u nieuwe componenten kunt toevoegen.

   ![ lay-out van het Tussenvoegsel ](/help/forms/assets/insert-layout-add-icon.png)

   Het klikken **voegt** pictogram toe toont een **Nieuwe de dialoogdoos van de Component van het Tussenvoegsel** die diverse componenten voor toevoeging toont.

   >[!NOTE]
   >
   > Alternatief, kunt u ook [ slepen en de lay-outcomponent ](#extra-bytes) laten vallen.

1. Blader door de beschikbare componenten in het dialoogvenster en selecteer de gewenste indeling in de lijst. In ons geval selecteert u de component Horizontale tabbladen om de horizontale tabs-lay-out in te voegen.

   ![ Uitgezochte horizontale lusjes ](/help/forms/assets/select-horizontal-tab.png)

   Wanneer u de component met horizontale tabbladen aan het formulier toevoegt, bestaat deze in eerste instantie uit twee lege deelvensters, standaard genaamd Item1 en Item2. U moet handmatig formuliercomponenten aan deze deelvensters toevoegen.

   ![ Horizontale lusjes ](/help/forms/assets/insert-tabs-on-top.png)

1. Open de eigenschappen van de component met horizontale tabbladen en geef de naam voor de component op.
In dit geval voegen we bijvoorbeeld de naam van de horizontale tabbladcomponent toe als aanvraagformulier voor IT.

   ![ voeg naam voor Horizontale lusjes toe ](/help/forms/assets/change-name-of-horizontal-tabs.png)

1. Klik **Gedaan**.

   ![ Horizontale lusjes ](/help/forms/assets/tabs-on-top-rename-component.png)

Nadat de indelingscomponent in het formulier is toegevoegd, wijzigt u het aantal deelvensters volgens de vereisten.

### 2. Voeg deelvensters toe aan de layout

Nieuw deelvenster toevoegen aan de component met horizontale tabbladen:

1. Open de horizontale eigenschappen van de lusjescomponent en klik de **Punten** tabel.

   ![ lusje van het Punt voor Horizontale lusjes ](/help/forms/assets/tabs-on-top-items-tab.png)

1. Klik **toevoegen** pictogram om nieuw paneel toe te voegen.

   ![ voeg nieuw paneel ](/help/forms/assets/tabs-on-top-add-panel.png) toe

   Wanneer u **klikt voeg** pictogram toe, verschijnt het **Nieuwe de dialoogvakje van de Component van het Tussenvoegsel**.

1. Selecteer de deelvenstercomponent.

   ![ voeg nieuw paneel ](/help/forms/assets/tabs-on-top-new-panel.png) toe

   Wanneer u de deelvenstercomponent selecteert, wordt het nieuwe deelvenster toegevoegd aan de horizontale lay-out.

   ![ voeg nieuw paneel ](/help/forms/assets/tabs-on-top-add-new-panel.png) toe

   Geef een naam op voor het nieuwe deelvenster, anders kunt u de eigenschappen van de component met horizontale tabbladen niet opslaan.

1. Geef de namen van de deelvensters op, zoals in de onderstaande afbeelding wordt getoond:

   ![ de namen van het Comité ](/help/forms/assets/tabs-on-tops-panel-name.png)

1. Klik **Gedaan**.

   Zodra u **Gedaan** klikt, verschijnen de drie panelen naast elkaar in een rij. De deelvensternamen worden als koppen voor elk deelvenster weergegeven en u kunt formuliercomponenten aan elk deelvenster toevoegen.

   ![ de namen van het Comité ](/help/forms/assets/tabs-on-top-initial-view.png)

   U kunt de eigenschappen van een deelvenstercomponent configureren. Het IT-aanvraagformulier bevat bijvoorbeeld geen titels van deelvensters. Hier volgen de stappen voor het configureren van eigenschappen van een deelvenstercomponent.

1. Open de eigenschappen van het eerste deelvenster.

   ![ Comité 1 Eigenschappen ](/help/forms/assets/tabs-on-tops-panel1-properties.png)

1. Selecteer **titel** checkbox van de Huid van **Basis** tabel.

   ![ Verberg titel ](/help/forms/assets/tabs-on-top-hide-panel.png)

1. Klik **Gedaan**.

Op dezelfde manier kunt u ook titels voor de andere twee deelvensters verbergen. Als u klaar bent, kunt u doorgaan met het toevoegen van formuliercomponenten aan elk deelvenster.

### 3. Voeg formuliercomponenten toe aan het deelvenster

<!-- You can employ one of the following method to add form components to the panel:
* [Add components to a layout's panel using the Add icon](#add-components-to-a-layouts-panel-using-the-add-icon)
* [Drag and drop components into a layout's panel](#drag-and-drop-components-into-a-layouts-panel) -->

1. Zoek de sectie in het deelvenster waarin u componenten kunt toevoegen.
1. Klik **toevoegen** pictogram. Het pictogram is een plusteken (+) waarmee u nieuwe componenten kunt toevoegen.
   ![ lay-out van het Tussenvoegsel ](/help/forms/assets/tabs-on-top-add-component.png)

   Het klikken **voegt** pictogram toe toont een **Nieuwe de dialoogdoos van de Component van het Tussenvoegsel** die diverse componenten voor toevoeging toont.

   ![ de Doos van de Dialoog van de Component van het Tussenvoegsel Nieuwe ](/help/forms/assets/insert-new-component.png)

1. Blader door de beschikbare componenten in het dialoogvenster dat wordt weergegeven en selecteer de gewenste component. Selecteer in ons geval de component Tekstvak.
1. Open de eigenschappen van de toegevoegde component en geef de naam ervan op. Hiermee kunt u de eigenschappen van de toegevoegde component Tekstvak bewerken en de naam ervan opgeven.
   ![ lay-out van het Tussenvoegsel ](/help/forms/assets/tabs-on-top-textbox-component.png)
1. Voeg op dezelfde manier nog twee tekstvakcomponenten toe en noem de componenten als e-mailadres en afdeling.\
   ![ Eerste Comité ](/help/forms/assets/tabs-on-tops-first-panel.png)

   Nu de componenten in het eerste deelvenster zijn toegevoegd, kunt u doorgaan met het toevoegen van de componenten aan het tweede deelvenster.

1. Om het paneel te schakelen, klik **Uitgezochte Comité** van de toolbar.

   ![ Deelvenster van de Schakelaar ](/help/forms/assets/tabs-on-top-select-panel.png)

   Wanneer u het **Uitgezochte Comité** klikt, verschijnt de lijst van de toegevoegde panelen in de Horizontale component van Lusjes.

   ![ Deelvenster van de Schakelaar ](/help/forms/assets/tabs-on-tops-panel2.png)

1. Selecteer **2 Comité** van de paneellijst en de meningsveranderingen van het eerste paneel aan het tweede paneel.

   ![ Tweede Comité ](/help/forms/assets/tabs-on-top-panel2-component.png)

1. Herhaal de stappen die van Stap 2 aan Stap 4 voor het toevoegen van de gewenste componenten in paneel 2 zoals aangetoond in het hieronder cijfer worden geschetst:

   ![ Tweede de componenten van het Comité ](/help/forms/assets/panel-2-components.png)

1. Schakelaar aan het **3 Comité** door de stappen te volgen die in Stap 6 en Stap 7 worden geschetst.

1. Herhaal de stappen die van Stap 2 tot Stap 4 worden beschreven voor het toevoegen van de gewenste component in paneel 3:

   ![ De componenten van het Derde Comité ](/help/forms/assets/panel-3-component.png)

1. Klik op **[!UICONTROL Preview]** in de rechterbovenhoek van de ontwerpomgeving.
   ![ Horizontale Lay-out ](/help/forms/assets/horizontal-layout.gif)

U kunt ook [ slepen-en-daling de componenten ](#extra-bytes) om de vormcomponenten aan elk paneel toe te voegen.


<!-- #### Drag and drop components into a layout's panel 

1. Locate the section within the panel that allows you to add components. 
2. Navigate to the left panel within your authoring environment and click **Components**.

    ![Component Panel](/help/forms/assets/add-new-component.png){width="200" align="center"}

    When you click the **Components** option, the list of the available components appears.   

    ![Component Panel](/help/forms/assets/add-new-component2.png){width="200" align="center"}

3. Browse the available components and select the Text Box component.

4. Drag the component by clicking and holding the selected component, then drag it over to the panel area to place it.

5. Drop the component into the panel by releasing the mouse. 

6. Open the properties of the added Text Box component and specify its name as Name.
    ![Insert layout](/help/forms/assets/tabs-on-top-textbox-component.png){width="200" align="center"}
7. Similarly, add two more Text Box components and name added the components as Email ID and Department.   
    ![First Panel](/help/forms/assets/tabs-on-tops-first-panel.png){width="200" align="center"}

    Now that the components in the first panel have been added, you can proceed with adding the components to the second panel. 

8. To switch the panel, click **Select Panel** from the toolbar. 

    ![Switch Panel](/help/forms/assets/tabs-on-top-select-panel.png){width="200" align="center"}

    When you click the **Select Panel**, the list of the added panels in the Horizontal Tabs component appears.

    ![Switch Panel](/help/forms/assets/tabs-on-tops-panel2.png){width="200" align="center"}

9. Select **2 Panel** from the panel list and the view changes from the first panel to the second panel.

    ![Second Panel](/help/forms/assets/tabs-on-top-panel2-component.png){width="200" align="center"}

10. Repeat the steps outlined from Step 2 to Step 6 for adding the desired components in panel 2 as shown in the below figure:   

     ![Second Panel components](/help/forms/assets/panel-2-components.png){width="200" align="center"}

11. Switch to the **3 Panel** by following the steps outlined in Step 8 and Step 9.

12. Repeat the steps outlined from Step 2 to Step 6 for adding the desired component in panel 3:

    ![Third Panel components](/help/forms/assets/panel-3-component.png){width="200" align="center"} 

    -->



U kunt vormcomponent van het paneel ook schrappen gebruikend het ![ pictogram van de Schrapping ](/help/forms/assets/Smock_Delete_18_N.svg).

![ Deleting a component ](/help/forms/assets/delete-component.png)

U kunt desgewenst ook de vereiste validaties voor de componenten toevoegen.

## Hoe te om een bestaande lay-out met een nieuwe lay-out te vervangen?

U kunt een indeling van een formulier vervangen door een nieuwe indeling. Hierbij moet u wijzigen hoe componenten worden gerangschikt en weergegeven in een formulier.

Voer de volgende stappen uit om de bestaande indeling van een formulier te vervangen:

1. Klik op het pictogram Vervangen op de werkbalk van de lay-outcomponent en het dialoogvenster **[!UICONTROL Replace Component]** wordt weergegeven.

   ![ vervangt Lay-out ](/help/forms/assets/replace-layout.png)

1. Selecteer de gewenste indeling in het dialoogvenster **[!UICONTROL Replace Component]** .

   ![ vervangt de dialoogdoos van de Component ](/help/forms/assets/replace-component.png)

   Nadat u de lay-out hebt geselecteerd, wordt de rangschikking van de componenten in de lay-out dienovereenkomstig gewijzigd. Selecteer bijvoorbeeld de component met verticale tabbladen in het dialoogvenster **[!UICONTROL Replace Component]** . De rangschikking van het deelvenster verandert in tabbladen aan de linkerkant:

   ![ Verticale Lay-out ](/help/forms/assets/vertical-tab.gif)

## Extra bytes

Voer de volgende stappen uit om componenten naar de formuliereditor te slepen:

1. Zoek de sectie waarin u componenten kunt toevoegen.
1. Navigeer aan het linkerpaneel binnen uw auteursmilieu en klik **Componenten**.

   ![ Deelvenster van de Component ](/help/forms/assets/add-new-component.png)

   Wanneer u de **optie van Componenten** klikt, verschijnt de lijst van de beschikbare componenten.

   ![ Deelvenster van de Component ](/help/forms/assets/add-new-component2.png)

1. Blader door de beschikbare componenten en selecteer de gewenste component.

1. Sleep de component door op de geselecteerde component te klikken en deze ingedrukt te houden en vervolgens over de component naar het deelvenstergebied te slepen.

1. Zet de component neer in het paneel door de muis vrij te geven.

## Volgende stappen

Als u bekend bent met de verschillende indelingsmogelijkheden voor een adaptief formulier op basis van kerncomponenten, kunt u verdergaan met de volgende stappen:

* [Uw eerste adaptieve formulier maken op basis van kerncomponenten](/help/forms/creating-adaptive-form-core-components.md)
* [Aangepaste formulierthema&#39;s maken en gebruiken](/help/forms/using-themes-in-core-components.md)



## Zie ook

{{see-also}}
