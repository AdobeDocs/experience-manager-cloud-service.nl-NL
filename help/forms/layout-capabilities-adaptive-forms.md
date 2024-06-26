---
title: Wat zijn de lay-outmogelijkheden van Adaptive Forms?
description: De lay-out en vormgeving van Adaptief Forms op verschillende apparaten worden bepaald door de lay-outinstellingen. Begrijp de verschillende lay-outs en hoe te om hen toe te passen.
feature: Adaptive Forms, Foundation Components
exl-id: e30c6ff9-692b-4415-8f14-b4ef616b2d12
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 0%

---

# Lay-outmogelijkheden van adaptieve Forms {#layout-capabilities-of-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/layout-capabilities-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |

[!DNL Adobe Experience Manager] Hiermee kunt u gebruiksvriendelijke adaptieve Forms maken die eindgebruikers een dynamische ervaring biedt. De formulierindeling bepaalt hoe items of componenten in een adaptieve vorm worden weergegeven.

<!-- ## Prerequisite knowledge {#prerequisite-knowledge}

Before learning about the different layout capabilities of Adaptive Forms, read [Introduction to authoring forms](introduction-forms-authoring.md) to know more about Adaptive Forms. -->

## Typen lay-outs {#types-of-layouts}

Een adaptief formulier biedt u de volgende typen indelingen:

**[!UICONTROL Panel Layout]** Bepaalt hoe items of componenten in een deelvenster op een apparaat worden weergegeven.

**[!UICONTROL Mobile Layout]** Hiermee regelt u de navigatie van een formulier op een mobiel apparaat. Als de apparaatbreedte 768 pixels of meer is, wordt de lay-out beschouwd als een mobiele lay-out en geoptimaliseerd voor een mobiel apparaat.

**[!UICONTROL Toolbar Layout]** Hiermee bepaalt u de plaatsing van de knoppen Handeling op de werkbalk of de werkbalk van het deelvenster in een formulier.

Al deze paneellay-outs worden bepaald bij `/libs/fd/af/layouts` locatie.

Als u de indeling van een adaptief formulier wilt wijzigen, gebruikt u de ontwerpmodus in [!DNL Experience Manager].

## [!UICONTROL Panel layout] {#panel-layout}

Een auteur van een formulier kan een indeling koppelen aan elk deelvenster van een adaptief formulier, inclusief het hoofdvenster.

De schermindelingen van het deelvenster zijn beschikbaar op `/libs/fd/af/layouts/panel` locatie. Selecteer het deelvenster en selecteer ![cmppr1](assets/configure-icon.svg) om de deelvenstereigenschappen weer te geven.

![Lijst met deelvensterindelingen voor het hoofdvenster van een adaptief formulier](assets/layouts.png)

### [!UICONTROL Responsive - everything on one page without navigation] {#responsive-everything-on-one-page-without-navigation-br}

Met deze deelvensterlay-out maakt u een responsieve lay-out die zich aanpast aan de schermgrootte van uw apparaat zonder dat u hiervoor speciale navigatie nodig hebt.

Met deze layout kunt u meerdere plaatsen **[!UICONTROL Panel Adaptive Form]** in het deelvenster een voor een.

![Een formulier met een responsieve indeling zoals wordt weergegeven op een klein scherm](assets/responsive-layout.png)

### [!UICONTROL Wizard] {#wizard}

Met deze deelvensterindeling kunt u navigatie met instructies in een formulier bieden. Gebruik deze indeling bijvoorbeeld wanneer u verplichte gegevens in een formulier wilt vastleggen en gebruikers stapsgewijs wilt begeleiden.

Gebruik de **[!UICONTROL Panel Adaptive Form]** voor stapsgewijze navigatie binnen een deelvenster. Als u deze lay-out gebruikt, gaat een gebruiker pas naar de volgende stap nadat de huidige stap is voltooid

```javascript
window.guideBridge.validate([], this.panel.navigationContext.currentItem.somExpression)
```

![Een formulier met wizardindeling](assets/wizard-layout2.png)

### [!UICONTROL Accordion] {#layout-for-accordion-design}

Met deze lay-out kunt u de **[!UICONTROL Panel Adaptive Form]** in een deelvenster met accordeonstijlnavigatie. Met deze indeling kunt u ook herhaalbare deelvensters maken. Met herhalende deelvensters kunt u, indien nodig, deelvensters dynamisch toevoegen of verwijderen. U kunt het minimum en het maximum aantal keren bepalen dat een paneel herhaalt. De titel van het deelvenster kan ook dynamisch worden bepaald op basis van de informatie in de deelvensteritems.

De summiere uitdrukking kan worden gebruikt om de waarden te tonen die door de gebruiker in de titel van het geminimaliseerde paneel worden verstrekt.

![Herhaalbare deelvensters met de accordeonlay-out in Adaptive Forms](assets/accordion-layout.png)

### [!UICONTROL Tabbed layout - tabs appear on the left]{#tabbed-layout-tabs-appear-on-the-left}

Met deze lay-out kunt u de **[!UICONTROL Panel Adaptive Form]** in een deelvenster met tabnavigatie. De tabbladen worden links van de inhoud van het deelvenster geplaatst.

![In de lay-out Tabbed, verschijnen de lusjes op de linkerzijde](assets/tabs-on-left.png)

Tabs die links van een deelvenster worden weergegeven

### [!UICONTROL Tabbed layout - tabs appear on the top] {#tabbed-layout-tabs-appear-on-the-top}

Met deze lay-out kunt u de **[!UICONTROL Panel Adaptive Form]** Component in a panel with tab navigation. De tabbladen worden boven op de inhoud van het deelvenster geplaatst.

![Lay-out met tabs in Adaptive Forms met tabs bovenaan](assets/tabs-on-top.png)

## Mobiele lay-outs {#mobile-layouts}

Mobiele lay-outs maken gebruikersvriendelijke navigatie op mobiele apparaten met relatief kleinere schermen mogelijk. Mobiele lay-outs maken gebruik van tabbladen of wizards voor formuliernavigatie. Als u een mobiele indeling toepast, beschikt u over één indeling voor het hele formulier.

Deze indeling bepaalt de navigatie met behulp van een navigatiebalk en een navigatiemenu. De navigatiebalk toont **&lt;** en **>** pictogram om aan te geven **[!UICONTROL next]** en **[!UICONTROL previous]** navigatiestappen in het formulier.

De mobiele lay-outs zijn beschikbaar op `/libs/fd/af/layouts/mobile/` locatie. De volgende mobiele lay-outs zijn standaard beschikbaar in Adaptive Forms.

![Lijst met mobiele lay-outs in Adaptive Forms](assets/mobile-navigation.png)

Selecteer de **[!UICONTROL Add navigable items of responsive layout to mobile menu]** Hiermee geeft u de opties voor navigatie weer die beschikbaar zijn voor een deelvenster in de mobiele lay-out. De navigeerbare opties zijn alleen zichtbaar als u **[!UICONTROL Responsive]** lay-out voor een deelvenster.

Als u een mobiele indeling gebruikt, kunt u in het formuliermenu verschillende formulierdeelvensters openen door op ![aem6forms_form_menu](assets/rail-icon.svg) pictogram.

### [!UICONTROL Layout with panel titles in the form header] {#layout-with-panel-titles-in-the-form-header}

In deze indeling worden, zoals in de naam wordt gesuggereerd, deelvenstertitels weergegeven, samen met het navigatiemenu en de navigatiebalk. Deze indeling biedt ook de pictogrammen Volgende en Vorige voor navigatie.

![Mobiele lay-outs met titels van deelvensters in de formulierkoppen](assets/mobile-layout1.png)

### [!UICONTROL Layout without panel titles in the form header]{#layout-without-panel-titles-in-the-form-header}

In deze indeling worden, zoals in de naam wordt gesuggereerd, alleen het navigatiemenu en de navigatiebalk zonder venstertitels weergegeven. Deze indeling biedt ook de pictogrammen Volgende en Vorige voor navigatie.

![Mobiele lay-outs zonder titels in de formulierkoppen](assets/mobile-layout2.png)

## Zie ook {#see-also}

{{see-also}}


<!-- ## Toolbar layouts {#toolbar-layouts}

A Toolbar Layout controls positioning and display of any action buttons that you add to your Adaptive Forms. The layout can be added at a form level or at a panel level.

![A list of Toolbar Layouts in Adaptive Forms to control layout of buttons](assets/toolbar-layouts.png)

A list of Toolbar Layouts in Adaptive Forms

Toolbar layouts are available at `/libs/fd/af/layouts/toolbar` location. Adaptive Forms provide the following Toolbar Layouts, by default.

### [!UICONTROL Default layout for toolbar] {#default-layout-for-toolbar}

This layout is selected as the default layout when you add any action buttons in an Adaptive Form. Selecting this layout displays the same layout for both, desktop and mobile devices.

Also, you can add multiple toolbars containing action buttons configured with this layout. An action button is associated with a form control. You can configure the toolbars to be before or after a panel.

![Default view for toolbar](assets/toolbar_layout_default.png)

Default view for toolbar

### [!UICONTROL Mobile fixed layout for toolbar] {#mobile-fixed-layout-for-toolbar}

Select this layout to provide alternate layouts for desktop and mobile devices.

For the desktop layout, you can add Action buttons using some specific labels. Only one toolbar can be configured with this layout. If more than one toolbar is configured with this layout, there is an overlap for mobile devices and only one toolbar is visible. For example, you can have a toolbar at the bottom or the top of the form, or, after or before panels in the form.

For the Mobile layout, you can add action buttons using icons.

![Mobile fixed layout for toolbar](assets/toolbar_layout_mobile_fixed.png)

Mobile fixed layout for toolbar-->


