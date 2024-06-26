---
title: Hoe kunt u inline stijlen toepassen op adaptieve formuliercomponenten?
description: Leer aangepaste stijlen toe te passen op een adaptief formulier, kunt u ook inline CSS-eigenschappen toepassen op afzonderlijke componenten van een adaptief formulier.
feature: Adaptive Forms, Foundation Components
role: User, Developer
level: Intermediate
exl-id: 25adabfb-ff19-4cb2-aef5-0a8086d2e552
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---

# Inline opmaak van adaptieve formuliercomponenten {#inline-styling-of-adaptive-form-components}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/inline-style-adaptive-forms.html) |
| AEM as a Cloud Service | Dit artikel |

U kunt de algemene weergave en stijl van een adaptief formulier definiëren door stijlen op te geven met [themaeditor](themes.md). Bovendien kunt u inline CSS-stijlen toepassen op afzonderlijke componenten van Adaptief formulier en de wijzigingen direct bekijken. Inline stijlen overschrijven de opmaak die in het thema is opgenomen.

## Inline CSS-eigenschappen toepassen {#apply-inline-css-properties}

Inline stijlen toevoegen aan een component:

1. Open het formulier in de formuliereditor en wijzig de modus in opmaakmodus. Als u de modus wilt wijzigen in de opmaakmodus, selecteert u op de pagina-werkbalk de optie ![canvas-drop-down](assets/Smock_ChevronDown.svg) > **[!UICONTROL Style]**.
1. Selecteer een component op de pagina en selecteer de knop Bewerken ![bewerken, knop](assets/edit.svg). Stijleigenschappen worden geopend in de zijbalk.

   U kunt ook componenten selecteren in de boomstructuur van de formulierhiërarchie in het zijpaneel. De boomstructuur in de formulierhiërarchie is beschikbaar als formulierobjecten op de zijbalk.

   In de [!UICONTROL Style] in de modus, kunt u de componenten onder Formulierobjecten zien. In de lijst Formulierobjecten in het zijpaneel worden echter componenten zoals velden en deelvensters vermeld. Velden en deelvensters zijn algemene componenten die componenten kunnen bevatten, zoals tekstvak en keuzerondjes.

   Wanneer u een component selecteert in het zijpaneel, ziet u alle vermelde subcomponenten en de eigenschappen van de geselecteerde component. U kunt een specifieke subcomponent selecteren en deze opmaken.

1. Klik op een tabblad in de zijbalk om CSS-eigenschappen op te geven. U kunt eigenschappen opgeven, zoals:

   * [!UICONTROL Dimensions & Position] (Weergave-instelling, opvulling, hoogte, breedte, marge, positie, z-index, zwevend, wissen, overloop)
   * [!UICONTROL Text] (Lettertypefamilie, dikte, kleur, grootte, lijnhoogte en uitlijning)
   * [!UICONTROL Background] (Afbeelding en verloop, achtergrondkleur)
   * [!UICONTROL Border] (Breedte, stijl, kleur, straal)
   * [!UICONTROL Effects] (Schaduw, dekking)
   * [!UICONTROL Advanced] (Hiermee kunt u aangepaste CSS voor de component schrijven)

1. Op dezelfde manier kunt u stijlen toepassen op andere delen van een component, zoals [!UICONTROL Widget], [!UICONTROL Caption], en [!UICONTROL Help].
1. Selecteren **[!UICONTROL Done]** om de wijzigingen te bevestigen of **[!UICONTROL Cancel]** om de wijzigingen te verwijderen.

## Voorbeeld: inline stijlen voor een veldcomponent {#example-inline-styles-for-a-field-component}

In de volgende afbeeldingen wordt een tekstveld weergegeven voor- en nadat er inline stijlen op zijn toegepast.

![Component van tekstvak voordat inline-opmaak wordt toegepast](assets/no-style.png)

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
   <td><p>Dimensionen en positie &gt; breedte</p> </td>
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

![Stijl van tekstvak nadat inline-opmaak is toegepast](assets/applied-style.png)

Component van tekstvak na toepassen van inline-stijleigenschappen

Na de bovenstaande stappen kunt u andere componenten selecteren en opmaken, zoals deelvensters, verzendknoppen en keuzerondjes.

>[!NOTE]
>
>De stijleigenschappen variëren op basis van de component die u selecteert.

## Stijlen kopiëren en plakken {#copy-paste-styles}

U kunt ook een stijl van de ene component naar een andere component in een adaptief formulier kopiëren en plakken. In de **[!UICONTROL Style]** Selecteer de component en selecteer het pictogram Kopiëren ![Kopiëren](assets/property-copy-icon.svg).

Selecteer de andere component van hetzelfde type en selecteer het pictogram Plakken ![Kopiëren](assets/Smock_Paste_18_N.svg) om de gekopieerde stijl te plakken. U kunt ook het pictogram Stijl wissen selecteren ![Kopiëren](assets/clear-style-icon.svg) om de toegepaste stijl te wissen.

## Stijlen instellen voor verschillende statussen van een component {#set-styles-for-states}

U kunt stijlen instellen voor verschillende toestanden van een componenttype. De verschillende staten omvatten: [!UICONTROL Focus], [!UICONTROL Disabled], [!UICONTROL Hover], [!UICONTROL Error], [!UICONTROL Success], en [!UICONTROL Mandatory].

Stijl definiëren voor een status van een component:

1. In de **[!UICONTROL Style]** Selecteer de component en selecteer het pictogram Bewerken ![Bewerken](assets/Smock_Edit_18_N.svg).

1. Selecteer de status voor de component met de opdracht **[!UICONTROL State]** vervolgkeuzelijst.

   ![Status selecteren](assets/select-state.png)

1. Definieer de opmaak voor de geselecteerde status van de component en selecteer ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.

U kunt ook de status van succes en fout simuleren. Selecteer het pictogram Uitvouwen om het dialoogvenster **[!UICONTROL Simulate Success]** en **[!UICONTROL Simulate Error]** opties.

![Frames simuleren](assets/simulate-states.png)


## Zie ook {#see-also}

{{see-also}}


<!--

>[!MORELIKETHIS]
>
>* [Use themes in Adaptive Form Core Components ](/help/forms/using-themes-in-core-components.md)

-->