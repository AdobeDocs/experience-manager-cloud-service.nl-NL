---
title: Hoe kunt u inline stijlen toepassen op adaptieve formuliercomponenten?
description: Leer aangepaste stijlen toe te passen op een adaptief formulier, kunt u ook inline CSS-eigenschappen toepassen op afzonderlijke componenten van een adaptief formulier.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: ab84a96d0e206395063442457a61f274ad9bed23
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Inline opmaak van adaptieve formuliercomponenten {#inline-styling-of-adaptive-form-components}

>[!NOTE]
>
> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

U kunt de algemene verschijning en de stijl van een Aangepaste Vorm bepalen door stijlen te specificeren gebruikend [ themaredacteur ](themes.md). Bovendien kunt u inline CSS-stijlen toepassen op afzonderlijke componenten van Adaptief formulier en de wijzigingen direct bekijken. Inline stijlen overschrijven de opmaak die in het thema is opgenomen.

## Inline CSS-eigenschappen toepassen {#apply-inline-css-properties}

Inline stijlen toevoegen aan een component:

1. Open het formulier in de formulierbuilder en wijzig de modus in opmaakmodus. Om de wijze aan het stileren wijze, op de paginagoolbar te veranderen, selecteer ![ canvas-drop-down ](assets/Smock_ChevronDown.svg) > **[!UICONTROL Style]**.
1. Selecteer een component in de pagina, en selecteer uitgeven knoop ![ uitgeven-knoop ](assets/edit.svg). Stijleigenschappen worden geopend in de zijbalk.

   U kunt ook componenten selecteren in de boomstructuur van de formulierhiërarchie in het zijpaneel. De boomstructuur in de formulierhiërarchie is beschikbaar als formulierobjecten op de zijbalk.

   In de modus [!UICONTROL Style] kunt u componenten zien die onder Formulierobjecten worden weergegeven. In de lijst Formulierobjecten in het zijpaneel worden echter componenten zoals velden en deelvensters vermeld. Velden en deelvensters zijn algemene componenten die componenten kunnen bevatten, zoals tekstvak en keuzerondjes.

   Wanneer u een component selecteert in het zijpaneel, ziet u alle vermelde subcomponenten en de eigenschappen van de geselecteerde component. U kunt een specifieke subcomponent selecteren en deze opmaken.

1. Klik op een tabblad in de zijbalk om CSS-eigenschappen op te geven. U kunt eigenschappen opgeven, zoals:

   * [!UICONTROL Dimensions & Position] (Weergave-instelling, opvulling, hoogte, breedte, marge, positie, z-index, zwevend, wissen, overloop)
   * [!UICONTROL Text] (Lettertypefamilie, dikte, kleur, grootte, lijnhoogte en uitlijning)
   * [!UICONTROL Background] (Afbeelding en verloop, achtergrondkleur)
   * [!UICONTROL Border] (Breedte, stijl, kleur, straal)
   * [!UICONTROL Effects] (Schaduw, dekking)
   * [!UICONTROL Advanced] (Hiermee kunt u aangepaste CSS voor de component schrijven)

1. Op dezelfde manier kunt u stijlen toepassen op andere delen van een component, zoals [!UICONTROL Widget] , [!UICONTROL Caption] en [!UICONTROL Help] .
1. Selecteer **[!UICONTROL Done]** om de wijzigingen te bevestigen of **[!UICONTROL Cancel]** om de wijzigingen te negeren.

## Voorbeeld: inline stijlen voor een veldcomponent {#example-inline-styles-for-a-field-component}

In de volgende afbeeldingen wordt een tekstveld weergegeven voor- en nadat er inline stijlen op zijn toegepast.

![ de vakje van de Tekst component alvorens het gealigneerde stileren wordt toegepast ](assets/no-style.png)

Component van tekstvak voordat inline-stijleigenschappen worden toegepast

Let op de wijziging in de stijl van het tekstvak zoals wordt getoond in de volgende afbeelding na het toepassen van de volgende CSS-eigenschappen.

<table>
 <tbody>
  <tr>
   <td><p>Kiezer</p> </td>
   <td><p>CSS-eigenschap</p> </td>
   <td><p>Waarde</p> </td>
   <td><p>Effect</p> </td>
  </tr>
  <tr>
   <td><p>Veld</p> </td>
   <td><p>border</p> </td>
   <td><p>Randbreedte =2 px</p> <p>Randstijl=Effen</p> <p>Randkleur=#1111</p> </td>
   <td><p>Hiermee maakt u een zwarte 2-px brede rand rond het veld</p> </td>
  </tr>
  <tr>
   <td><p>Tekstvak</p> </td>
   <td><p>background-color</p> </td>
   <td><p>#6495ED</p> </td>
   <td><p>Hiermee wijzigt u de achtergrondkleur in CornflowerBlue (#6495ED)</p> <p>Opmerking: u kunt een kleurnaam of hexadecimale code opgeven in het waardeveld.</p> </td>
  </tr>
  <tr>
   <td><p>Label</p> </td>
   <td><p>Afmetingen en positie &gt; breedte</p> </td>
   <td><p>100 px</p> </td>
   <td><p>Hiermee stelt u de breedte in op 100 px voor het label</p> </td>
  </tr>
  <tr>
   <td>Help-pictogram Veld</td>
   <td>Tekst &gt; Tekstkleur</td>
   <td>#2ECC40</td>
   <td>Hiermee wijzigt u de kleur van het Help-pictogram.</td>
  </tr>
  <tr>
   <td><p>Lange beschrijving</p> </td>
   <td><p>text-align</p> </td>
   <td><p>midden</p> </td>
   <td><p>Lijnt de lange beschrijving voor het centreren uit</p> </td>
  </tr>
 </tbody>
</table>

![ het vakje van de Tekst stijl na het gealigneerde stileren wordt toegepast ](assets/applied-style.png)

Component van tekstvak na toepassen van inline-stijleigenschappen

Na de bovenstaande stappen kunt u andere componenten selecteren en opmaken, zoals deelvensters, verzendknoppen en keuzerondjes.

>[!NOTE]
>
>De stijleigenschappen variëren op basis van de component die u selecteert.

## Stijlen kopiëren en plakken {#copy-paste-styles}

U kunt ook een stijl van de ene component naar een andere component in een adaptief formulier kopiëren en plakken. Op de **[!UICONTROL Style]** wijze, selecteer de component en selecteer het pictogram van het Exemplaar ![ Exemplaar ](assets/property-copy-icon.svg).

Selecteer de andere component van het zelfde type en selecteer het pictogram van het Deeg ![ Exemplaar ](assets/Smock_Paste_18_N.svg) om de gekopieerde stijl te kleven. U kunt het Duidelijke pictogram van de Stijl ook selecteren ![ Exemplaar ](assets/clear-style-icon.svg) om de toegepaste stijl te ontruimen.

## Stijlen instellen voor verschillende statussen van een component {#set-styles-for-states}

U kunt stijlen instellen voor verschillende toestanden van een componenttype. De verschillende statussen zijn: [!UICONTROL Focus], [!UICONTROL Disabled], [!UICONTROL Hover], [!UICONTROL Error], [!UICONTROL Success] en [!UICONTROL Mandatory] .

Stijl definiëren voor een status van een component:

1. Op de **[!UICONTROL Style]** wijze, selecteer de component en selecteer het Edit pictogram ![ uitgeven ](assets/Smock_Edit_18_N.svg).

1. Selecteer de status voor de component met de vervolgkeuzelijst **[!UICONTROL State]** .

   ![ Uitgezochte staat ](assets/select-state.png)

1. Bepaal het stileren voor de geselecteerde staat van de component en selecteer ![ sparen ](assets/save_icon.svg) om de eigenschappen te bewaren.

U kunt ook de status van succes en fout simuleren. Selecteer het pictogram Uitvouwen om de opties **[!UICONTROL Simulate Success]** en **[!UICONTROL Simulate Error]** weer te geven.

![ Simuleer staten ](assets/simulate-states.png)


## Zie ook {#see-also}

{{see-also}}


<!--

>[!MORELIKETHIS]
>
>* [Use themes in Adaptive Form Core Components ](/help/forms/using-themes-in-core-components.md)

-->