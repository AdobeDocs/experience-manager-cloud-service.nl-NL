---
title: Hoe voegt u voetnoot aan een adaptief formulier toe?
description: Gebruik Rich Text Editor (RTE) voor voetnoten in een adaptieve vorm.
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Voetnootcomponent {#footnotecomponent}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/creating-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

**[!UICONTROL Footnote]** Dit is het extra beetje informatie of nota&#39;s die aan het eind van de pagina verschijnen. [!UICONTROL Footnote] bestaat uit de notities die in de tekst worden aangegeven met getallen als superscript.

Voetnoten worden opeenvolgend genummerd in de volgorde waarin ze op de pagina worden weergegeven. Elke voetnoot heeft een uniek nummer als superscript dat overeenkomt met het nummer dat onder aan de pagina is geplaatst. Naast het nummer wordt de aanvullende informatie weergegeven als een voetnootbeschrijving.

![Beschrijving van voetnoot](/help/forms/assets/footnote_description.png)


## Gebruik van voetnoot {#usesoffootnotes}

* Hiermee kunt u citaten aanbieden.
* Verstrekt extra informatie die de normale stroom van de belangrijkste informatie kan onderbreken.
* Biedt ronde informatie of copyrightmachtigingen.

In Adaptive Forms: [!UICONTROL footnote] wordt gebruikt om informatie weer te geven over het invullen of gebruiken van het formulier. Ga voor informatie over het maken van een adaptieve Forms naar [Een adaptief formulier maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## Voetnoot in Adaptive Forms {#using-footnote-adaptiveforms}

Voer de volgende stappen uit om voetnoot toe te voegen in Adaptive Forms:
1. Een adaptief formulier openen in **Bewerken** -modus.
1. Sleep vanuit de componentbrowser de **[!UICONTROL Text]** naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Text]** component die u hebt toegevoegd en geselecteerd ![cmppr](assets/configure-icon.svg) om de eigenschappen te bewerken.

   ![Voetnoot in Adaptive Forms](/help/forms/assets/footnote_rte.png)

1. Selecteer de tekst waaraan u een voetnootbeschrijving wilt toevoegen en klik op  ![ster](/help/forms/assets/asterisk.svg) om de **[!UICONTROL Footnote]** component.

1. Klikken ![controleren](/help/forms/assets/save_icon.svg) de wijzigingen en stijlen opslaan.

   >[!NOTE]
   >
   >* Voetnoten worden automatisch genummerd en worden weergegeven op een manier die ze maken op het adaptieve formulier.
   >* Als er dubbele voetnoten zijn, is de nummering voor alle dubbele voetnoten gelijk.

1. Sleep vanuit de componentbrowser de **[!UICONTROL Footnote Placeholder]** naar het adaptieve formulier.
   >[!NOTE]
   >
   >* In de publicatie-instantie worden voetnoten weergegeven op de positie waar **[!UICONTROL Footnote Placeholder]** wordt op het adaptieve formulier geplaatst.
   >* Wanneer u tussen verschillende deelvensters navigeert, worden alleen zichtbare voetnoten weergegeven in de **[!UICONTROL Footnote Placeholder]** die aanwezig zijn in het genavigeerde deelvenster.

1. Sla de eigenschappen op.

Tijdens de runtime wordt het getal in de tekst weergegeven als een superscript en wordt de bijbehorende beschrijving weergegeven in het dialoogvenster **[!UICONTROL Footnote]** component op de positie waar [!UICONTROL Footnote Placeholder] wordt op het adaptieve formulier geplaatst. U kunt rechtstreeks naar de voetnootbeschrijving navigeren door op het bijbehorende nummer op het tabblad [!UICONTROL Footnote].


## Zie ook {#see-also}

{{see-also}}