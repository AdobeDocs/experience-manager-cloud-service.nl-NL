---
title: Vorm RTE om toegankelijke Web-pagina's en plaatsen tot stand te brengen.
description: Leer Rich Text Editor te configureren om toegankelijke sites te maken in [!DNL Adobe Experience Manager].
contentOwner: AG
exl-id: 54050fc9-0348-4033-8e2b-b3897588cb62
source-git-commit: e9c1ec6807f86ab00f89ef292a89a0c8efdf802b
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 1%

---

# RTE configureren om toegankelijke sites te maken {#configure-rte-accessible-sites}

[!DNL Adobe Experience Manager] biedt ondersteuning voor standaardtoegankelijkheidsfuncties, zoals alternatieve tekst voor afbeeldingen, en extra functies die kunnen worden gebruikt bij het maken van inhoud. Inhoudsauteurs gebruiken deze functies met componenten die de RTE (RTE) gebruiken. Tot de functies behoren het toevoegen van alternatieve tekst, structuurinformatie via koppen en alinea-elementen, enzovoort.

Voor een begrip van typische configuraties van RTE, zie [RTE configureren](rich-text-editor.md) en [vormen stop-ins RTE voor specifieke functionaliteit](configure-rich-text-editor-plug-ins.md).

Gebruik de configuratie van stop-ins van RTE om de op toegankelijkheid betrekking hebbende eigenschappen te vormen en aan te passen. Gebruik bijvoorbeeld `paraformat` om extra semantische elementen op blokniveau toe te voegen, met inbegrip van het uitbreiden van het aantal kopniveaus die buiten het basisniveau worden gesteund `H1`, `H2` en `H3` standaard opgegeven. Het bewerken van tekst met opmaak is mogelijk met behulp van vele componenten uit de ontwerpgebruikersinterface. De algemeen gebruikte componenten zijn tekst, beeld, download, etc.

De functionaliteit van RTE kan in vele componenten ter beschikking worden gesteld. De primaire component is `Text` component.

Voor de `Text` component in [!DNL Experience Manager]In de volgende schermafbeelding wordt de RTF-editor weergegeven met een reeks ingeschakelde plug-ins, waaronder `paraformat`:

![RTE-tekstcomponent in de modus Volledig scherm](assets/rte-toolbar-full-screen-mode.png)

## De functies voor insteekmodules configureren {#configuring-the-plugin-features}

Voor instructies om RTE te vormen, zie [vormen de Rich Text Editor](rich-text-editor.md) pagina. Het artikel heeft betrekking op:

* [Plug-ins en bijbehorende functies](rich-text-editor.md#aboutplugins)
* [Configuratielocaties](rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Een insteekmodule activeren en de eigenschap features configureren](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Andere functies van de RTE configureren](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

Als u een aantal of alle functies voor een plug-in wilt activeren, configureert u de plug-in in het daarvoor bestemde `rtePlugins` subtak in CRXDE Lite.

![CRXDE Lite die een voorbeeld van rtePlugin toont](assets/example-rteplugin-crxde-lite.png)

### Voorbeeld om alineaopmaak op te geven die beschikbaar is in het veld RTE-selectie {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Er worden nieuwe semantische blokformaten beschikbaar gesteld voor selectie.

1. Afhankelijk van uw RTE, bepaal en navigeer aan [configuratielocatie](rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Het veld Alinea&#39;s selecteren inschakelen](rich-text-editor.md) door [de insteekmodule activeren](rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geef de indelingen op die beschikbaar moeten zijn in het veld Alinea&#39;s selecteren](rich-text-editor.md).
1. De paragraafformaten zijn dan beschikbaar aan de inhoudauteur van de selectiegebieden in RTE.

Met structuurelementen beschikbaar in de RTE via de opties voor alineaopmaak [!DNL Experience Manager] biedt een goede basis voor de ontwikkeling van toegankelijke inhoud. Inhoudsauteurs kunnen de RTE niet gebruiken om de tekengrootte of kleuren of andere verwante kenmerken op te maken, waardoor inlineopmaak niet mogelijk is. In plaats daarvan kunnen de auteurs de juiste structuurelementen selecteren, zoals koppen, en algemene stijlen gebruiken die u hebt gekozen bij de optie Stijlen, om een zuivere opmaak en grotere opties te garanderen voor gebruikers die met hun eigen stijlbladen en correct gestructureerde inhoud bladeren.

## De functie Bron bewerken gebruiken {#use-of-the-source-edit-feature}

In sommige gevallen, zullen de inhoudsauteurs het noodzakelijk vinden om de HTML broncode te onderzoeken en aan te passen die gebruikend RTE wordt gecreeerd. Bijvoorbeeld, kan een stuk van inhoud die binnen RTE wordt gecreeerd meer prijsverhoging vereisen om naleving WCAG 2.0 te verzekeren. Dit kan worden gedaan met de [bronbewerking](rich-text-editor.md#aboutplugins) optie van de RTE. U kunt de [`sourceedit` op de `misctools` insteekmodule](rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Gebruik de `sourceedit` zorgvuldig worden uitgevoerd. Bij typefouten en niet-ondersteunde functies kunnen problemen optreden.

<!--
TBD ENGREVIEW: Is this only applicable to Classic UI? 

## Adding Support for further HTML Elements and Attributes {#adding-support-for-additional-html-elements-and-attributes}

To further extend the accessibility features of [!DNL Experience Manager], it is possible to extend the existing components based on the RTE (such as the `Text` and `Table` components) with extra elements and attributes.

The following procedure illustrates how to extend the `Table` component with a `Caption` element that provides information about a data table to assistive technology users:

### Example: Add a caption to a table properties dialog {#example-adding-the-caption-to-the-table-properties-dialog}

In the constructor of the `TablePropertiesDialog`, add an extra text input field that is used for editing the caption. Set the `itemId` to `caption` (the DOM attribute???s name) to automatically handle its content.

In a `Table`, set the attribute to the DOM element or or remove it from the DOM element. The dialog in the `config` object passed the value. Set or remove the DOM attributes using the corresponding `CQ.form.rte.Common` methods (`com` is a shortcut for `CQ.form.rte.Common`). Using `CQ.form.rte.Common` methods avoids common pitfalls with browser implementations.

>[!NOTE]
>
>This procedure is only suitable for the classic UI.

### Step-by-step instructions {#step-by-step-instructions}

1. Start CRXDE Lite. For example: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`. Create intermediate folders if those do not exist.

1. Copy `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` to `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js` file to edit.

1. In the `constructor` method, before the mention of `var dialogRef = this;`, add the following code:

   ```javascript
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Open `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js` file.

1. Add the following code at the end of the `transferConfigToTable` method:

   ```javascript
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. To save your changes, click **[!UICONTROL Save All]**.

## Best practices and limitations {#best-practices-limitations-tips}

* A plain text field is not the only type of input allowed for the value of the caption element. You can use any ExtJS widget, that provides the caption???s value through its `getValue()` method.
* To add editing capabilities for more elements and attributes, ensure that:

  * The `itemId` property for each corresponding field is set to the name of the appropriate DOM attribute (`TablePropertiesDialog`).
  * The attribute is set and/or removed on the DOM element explicitly (`Table`).
-->

>[!MORELIKETHIS]
>
>* [Een snelle gids voor WCAG-standaarden](/help/compliance/accessibility/quick-guide-wcag.md)
>* [Toegankelijke inhoud maken in Experience Manager](/help/sites-cloud/authoring/fundamentals/accessible-content.md)

