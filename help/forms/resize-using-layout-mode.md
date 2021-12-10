---
title: Hoe gebruikt u de lay-outmodus om het formaat van componenten voor Adaptief Forms te wijzigen?
description: Bepaal de positie van componenten gebruikend het ontvankelijke net beschikbaar op de wijze van de Lay-out. Leer hoe u de modus Indeling kunt openen, de grootte van componenten kunt wijzigen, deelvensters kunt vergroten of verkleinen, lay-out met meerdere kolommen voor een deelvenster kunt definiëren, het nieuwe responsieve raster kunt inschakelen voor oude responsieve layouts en de modus Indeling kunt uitschakelen voor formulieren met een oude responsieve indeling.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: 53896a8e-4568-460b-bca7-994baea0c8eb
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# Gebruik de modus Lay-out om het formaat van componenten te wijzigen {#use-layout-mode-to-resize-components}

Met de ontwerpinterface voor Adaptief formulier kunt u het formaat van componenten wijzigen in de modus Indeling. Sleep blauwe stippen binnen kolommen om de begin- en eindpunten te definiëren voor de positioneringscomponenten. De blauwe stippen worden weergegeven nadat u op de component in het responsieve raster hebt getikt. Het responsieve raster bestaat uit 12 gelijke kolommen. Met de witte en blauwe kleurschaduw in alternatieve kolommen wordt de ene kolom onderscheiden van de andere.

U kunt de modus Lay-out gebruiken om het formaat van componenten te wijzigen voor alle apparaattypen, zoals bureaublad, tablet, telefoon en andere kleinere apparaten. De tablet leidt automatisch de lay-outconfiguratie van de Desktopversie af en de kleinere apparaten leiden lay-outconfiguratie van telefoon af. Nochtans, kunt u de automatisch afgeleide configuraties met voeten treden om een verschillende configuratie voor elk apparatentype te bepalen.

## Modus Toegang tot layout {#access-layout-mode}

Selecteren **[!UICONTROL Layout]** in de vervolgkeuzelijst die boven aan de ontwerpinterface voor adaptieve formulieren wordt weergegeven naast de knop **[!UICONTROL Preview]** optie. Het formulier wordt weergegeven in de modus Indeling.

1. Aanmelden bij de [!DNL Adobe Experience Manager] instantie van auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Een nieuwe of bestaande [Adaptief formulier](creating-adaptive-form.md).
1. Selecteren **[!UICONTROL Layout]** in de vervolgkeuzelijst die boven aan het dialoogvenster **[!UICONTROL Preview]** optie. Het formulier wordt weergegeven in de modus Indeling.

   ![Lay-outmodus](assets/layout_mode_ic_new.png)

## Formaat van componenten wijzigen {#resize-components}

1. Tik in de modus Lay-out op de component om de grootte te wijzigen. De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.
1. Sleep de blauwe stippen om de positie van de component in het responsieve raster te definiëren.

   ![Vergroten/verkleinen met de modus Lay-out](assets/layout_mode_resize_new_updated1.png)

   De werkbalk die wordt weergegeven nadat u op componenten hebt getikt, bestaat uit de volgende opties:

   * **[!UICONTROL Parent]**: Selecteer het bovenliggende element van een component.
   * **[!UICONTROL Revert breakpoint layout]**: Alle wijzigingen in de grootte ongedaan maken en de standaardlay-out toepassen op de component.
   * **[!UICONTROL Float to new line]**: Verplaats de component naar de volgende regel als er meerdere componenten binnen dezelfde regel zijn.

   U kunt ook de opdracht **[!UICONTROL Revert breakpoint layout]** ( ![Onderbrekingspunt herstellen](assets/reverttopreviouslypublishedversion.png)) op deelvensterniveau om alle wijzigingen in de grootte ongedaan te maken.

   >[!NOTE]
   >
   >U kunt de grootte van tabelkolommen, werkbalkknop, en doelgebiedcomponenten niet wijzigen in de modus Indeling. Gebruik de modus Stijl om het formaat van deze componenten te wijzigen.

### Voorbeeld {#example}

**Doel:** U wilt een tabelcomponent en een afbeeldingscomponent invoegen en deze parallel aan elkaar plaatsen in een adaptief formulier.

1. De tabel- en afbeeldingscomponenten invoegen met [!UICONTROL Edit] in het adaptieve formulier. De component image wordt weergegeven na de tabelcomponent.
1. Overschakelen op [!UICONTROL Layout] en tikt u op de [!UICONTROL Table] component. De blauwe stippen om het formaat van de componentweergave te wijzigen in kolom 1 en 12.
1. Sleep de blauwe stip in kolom 12 naar kolom 6 van het responsieve raster.

   ![Het eindpunt van de tabel definiëren](assets/layout_mode_end_point_table_new.png)

1. Selecteer op dezelfde manier de [!UICONTROL Image] en sleep de blauwe stip in kolom 1 naar kolom 7 van het responsieve raster. De tabel- en afbeeldingscomponenten worden parallel met elkaar weergegeven.

   ![Tabel en afbeelding parallel in de modus Lay-out](assets/table_image_parallel_new.png)

   U kunt de component Image selecteren en tikken op de knop **[!UICONTROL Float to new line]** beschikbaar op de werkbalk om de component Afbeelding naar de volgende regel te verplaatsen.

## Deelvensters vergroten/verkleinen {#resize-panels-layout-mode}

Voer de volgende stappen uit als u het formaat van het hele deelvenster wilt wijzigen in plaats van de afzonderlijke componenten:

1. Tik op de componenten in het deelvenster waarvan u het formaat wilt wijzigen en selecteer ![Bovenliggend element selecteren](assets/select_parent_icon.svg)en selecteert u de eerste optie in de vervolgkeuzelijst als het deelvenster het directe bovenliggende element van de component is.

   De blauwe stippen worden weergegeven aan het begin en einde van het responsieve raster.

1. Sleep de blauwe stippen om de positie van het deelvenster in het responsieve raster te definiëren.
U kunt de stappen 1 en 2 herhalen en ![Bovenliggend element selecteren](assets/float_to_new_line_icon.svg) om het vergrote of verkleinde deelvenster naar de volgende regel te verplaatsen.

## Meerdere kolommen voor een deelvenster definiëren

Voer de volgende stappen uit om het aantal kolommen voor een deelvenster te definiëren:

1. In **[!UICONTROL Edit]** tikken op het deelvenster, selecteren ![Configureren](assets/configure-icon.svg)en selecteert u **[!UICONTROL Responsive - everything on the page without navigation]** van de **[!UICONTROL Panel Layout]** vervolgkeuzelijst.

1. Tikken ![Opslaan](assets/save_icon.svg) om de eigenschappen op te slaan.

1. In de **[!UICONTROL Layout]** , tikt u op een van de componenten in het deelvenster en selecteert u ![Bovenliggend element selecteren](assets/select_parent_icon.svg)en selecteert u het deelvenster.

1. Tikken ![meerdere kolommen](assets/multi-column.svg) en selecteert u het aantal kolommen in de vervolgkeuzelijst. Het aantal kolommen kan variëren van 1 tot en met 12. Het deelvenster wordt onderverdeeld in een lay-out met meerdere kolommen.

![meerdere kolommen in de lay-outmodus](assets/multi-column-layout.png)

## Het nieuwe responsieve raster inschakelen voor oude responsieve layouts {#enableresponsivegrid}

Het nieuwe responsieve raster inschakelen voor formulieren die u maakt met [!DNL Adobe Experience Manager] Forms 6.4 of lager om het formaat van componenten te wijzigen.

>[!NOTE]
>
>Als u overschakelt naar het nieuwe responsieve raster, worden de lay-outeigenschappen verwijderd die al zijn gedefinieerd voor componenten die in het formulier worden gebruikt.

Voer de volgende stappen uit om het nieuwe responsieve raster in te schakelen:

1. Selecteren **[!UICONTROL Layout]** in de vervolgkeuzelijst die boven aan het dialoogvenster **[!UICONTROL Preview]** optie. Er wordt een bevestiging weergegeven om de modus Lay-out in te schakelen.
1. Tikken **[!UICONTROL Yes]** de **[!UICONTROL Layout]** voor het formulier.

### Een oud fragment insluiten in een adaptief formulier met nieuwe responsieve indeling {#embed-an-old-fragment-in-an-adaptive-form-with-new-responsive-layout}

Met de nieuwe responsieve indeling voor adaptief formulier kunt u een adaptief formulierfragment met de oude responsieve indeling toevoegen aan het formulier. De nieuwe indeling verwijdert echter de lay-outeigenschappen die al zijn gedefinieerd voor componenten die in het fragment worden gebruikt. U kunt overschakelen naar de modus Lay-out om de eigenschappen voor de lay-out te definiëren van de componenten die in het fragment worden gebruikt.

### Een fragment met een nieuwe responsieve indeling insluiten in een oud adaptief formulier {#embed-a-fragment-with-new-responsive-layout-in-an-old-adaptive-form}

Als u een fragment met de nieuwe responsieve indeling insluit in een adaptief formulier met een oude responsieve indeling, wordt u gevraagd de modus Indeling in te schakelen voor het formulier en het fragment opnieuw in te sluiten.

Selecteer **[!UICONTROL Layout]** in de vervolgkeuzelijst die boven aan het dialoogvenster **[!UICONTROL Preview]** tikken **[!UICONTROL Yes]** ter bevestiging. Selecteren **[!UICONTROL Edit]** om het fragment opnieuw in te sluiten.

## Lay-outmodus uitschakelen voor formulieren met oude responsieve indeling {#disable-layout-mode-for-forms-with-old-responsive-layout}

U kunt de modus Indeling uitschakelen voor formulieren met een oude responsieve indeling door eigenschappen te bewerken voor de sjabloon die in het formulier wordt gebruikt.

Voer de volgende stappen uit om de modus Lay-out uit te schakelen:

1. Selecteren **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** en opent u de sjabloon die in het formulier wordt gebruikt **[!UICONTROL Edit]** in.
1. Selecteer de Formuliercontainer in het linkervenster en tik op **[!UICONTROL Policy.]**

   ![Lay-outmodus uitschakelen](assets/policy_disable_layout_mode.png)

1. Tik op de knop **[!UICONTROL Layout Settings]** en selecteert u **[!UICONTROL Disable Layout Mode]**.
1. Tikken ![Wijzigingen opslaan](assets/save_icon.svg) om de sjablooneigenschappen op te slaan.
