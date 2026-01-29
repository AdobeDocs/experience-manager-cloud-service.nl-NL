---
title: Hoe voegt u voetnoot aan een adaptief formulier toe?
description: Gebruik Rich Text Editor (RTE) voor voetnoten in een adaptieve vorm.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
role: User, Developer
source-git-commit: a7265b4f8df34efc09076c03d1433f9aae542e76
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 0%

---

# Voetnootcomponent {#footnotecomponent}

Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/creating-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

**[!UICONTROL Footnote]** is het extra beetje informatie of nota&#39;s die aan het eind van de pagina verschijnen. [!UICONTROL Footnote] bestaat uit de notities die in de tekst worden aangegeven met getallen als superscript.

Voetnoten worden opeenvolgend genummerd in de volgorde waarin ze op de pagina worden weergegeven. Elke voetnoot heeft een uniek nummer als superscript dat overeenkomt met het nummer dat onder aan de pagina is geplaatst. Naast het nummer wordt de aanvullende informatie weergegeven als een voetnootbeschrijving.

![&#x200B; Beschrijving van voetnoten &#x200B;](/help/forms/assets/footnote_description.png)


## Gebruik van voetnoot {#usesoffootnotes}

* Hiermee kunt u citaten aanbieden.
* Verstrekt extra informatie die de normale stroom van de belangrijkste informatie kan onderbreken.
* Biedt ronde informatie of copyrightmachtigingen.

In Adaptive Forms wordt [!UICONTROL footnote] gebruikt om informatie weer te geven over het invullen of gebruiken van het formulier. Voor informatie over hoe te om een Aanpassings Forms tot stand te brengen, zie [&#x200B; Creërend een AanpassingsVorm &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## Voetnoot in Adaptive Forms {#using-footnote-adaptiveforms}

Voer de volgende stappen uit om voetnoot toe te voegen in Adaptive Forms:

1. Open een Adaptieve Vorm in **geeft** wijze uit.
1. Sleep de component **[!UICONTROL Text]** vanuit de componentbrowser naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Text]** component die u toevoegde en ![&#x200B; cmp &#x200B;](assets/configure-icon.svg) selecteert om zijn eigenschappen uit te geven.

   ![&#x200B; Voetnoot in Aanpassings Forms &#x200B;](/help/forms/assets/footnote_rte.png)

1. Selecteer de tekst waarvoor u een voetnootbeschrijving wilt toevoegen en ![&#x200B; ster &#x200B;](/help/forms/assets/asterisk.svg) knoop klikken om de **[!UICONTROL Footnote]** component te stileren.

1. Klik ![&#x200B; controle &#x200B;](/help/forms/assets/save_icon.svg) om de veranderingen en de stijlen te bewaren.

   >[!NOTE]
   >
   >* Voetnoten worden automatisch genummerd en worden weergegeven op een manier die ze maken op het adaptieve formulier.
   >* Als er dubbele voetnoten zijn, is de nummering voor alle dubbele voetnoten gelijk.

1. Sleep de component **[!UICONTROL Footnote Placeholder]** vanuit de componentbrowser naar het adaptieve formulier.

1. Sla de eigenschappen op.

Tijdens de runtime wordt het getal in de tekst weergegeven als een superscript en wordt de bijbehorende beschrijving weergegeven in de component **[!UICONTROL Footnote]** op de positie waar [!UICONTROL Footnote Placeholder] op het adaptieve formulier is geplaatst. U kunt rechtstreeks naar de voetnootbeschrijving navigeren door op het bijbehorende nummer in de [!UICONTROL Footnote] te klikken.

## Plaatsaanduidingsgedrag voor voetnoten in Adaptief Forms

* In de publicatie-instantie worden voetnoten weergegeven op de positie waar de component **[!UICONTROL Footnote Placeholder]** op het adaptieve formulier wordt geplaatst.
* Voetnoten ondersteunen regeleinden, zodat formulierauteurs inhoud op meerdere regels in de component **[!UICONTROL Footnote Placeholder]** kunnen opmaken.
* Voetnoten blijven te allen tijde zichtbaar in de **[!UICONTROL Footnote Placeholder]** , onafhankelijk van de zichtbaarheid van de gekoppelde deelvensters.


## Zie ook {#see-also}

{{see-also}}