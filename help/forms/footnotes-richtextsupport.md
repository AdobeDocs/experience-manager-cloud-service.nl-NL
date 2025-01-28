---
title: Hoe voegt u voetnoot aan een adaptief formulier toe?
description: Gebruik Rich Text Editor (RTE) voor voetnoten in een adaptieve vorm.
feature: Adaptive Forms, Foundation Components
exl-id: f04dae84-daab-42f8-876f-02fe426f62be
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Voetnootcomponent {#footnotecomponent}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

**[!UICONTROL Footnote]** is het extra beetje informatie of nota&#39;s die aan het eind van de pagina verschijnen. [!UICONTROL Footnote] bestaat uit de notities die in de tekst worden aangegeven met getallen als superscript.

Voetnoten worden opeenvolgend genummerd in de volgorde waarin ze op de pagina worden weergegeven. Elke voetnoot heeft een uniek nummer als superscript dat overeenkomt met het nummer dat onder aan de pagina is geplaatst. Naast het nummer wordt de aanvullende informatie weergegeven als een voetnootbeschrijving.

![ Beschrijving van voetnoten ](/help/forms/assets/footnote_description.png)


## Gebruik van voetnoot {#usesoffootnotes}

* Hiermee kunt u citaten aanbieden.
* Verstrekt extra informatie die de normale stroom van de belangrijkste informatie kan onderbreken.
* Biedt ronde informatie of copyrightmachtigingen.

In Adaptive Forms wordt [!UICONTROL footnote] gebruikt om informatie weer te geven over het invullen of gebruiken van het formulier. Voor informatie over hoe te om een Aanpassings Forms tot stand te brengen, zie [ Creërend een AanpassingsVorm ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-an-adaptive-form/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html).

## Voetnoot in Adaptive Forms {#using-footnote-adaptiveforms}

Voer de volgende stappen uit om voetnoot toe te voegen in Adaptive Forms:
1. Open een Adaptieve Vorm in **geeft** wijze uit.
1. Sleep de component **[!UICONTROL Text]** vanuit de componentbrowser naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Text]** component die u toevoegde en ![ cmp ](assets/configure-icon.svg) selecteert om zijn eigenschappen uit te geven.

   ![ Voetnoot in Aanpassings Forms ](/help/forms/assets/footnote_rte.png)

1. Selecteer de tekst waarvoor u een voetnootbeschrijving wilt toevoegen en ![ ster ](/help/forms/assets/asterisk.svg) knoop klikken om de **[!UICONTROL Footnote]** component te stileren.

1. Klik ![ controle ](/help/forms/assets/save_icon.svg) om de veranderingen en de stijlen te bewaren.

   >[!NOTE]
   >
   >* Voetnoten worden automatisch genummerd en worden weergegeven op een manier die ze maken op het adaptieve formulier.
   >* Als er dubbele voetnoten zijn, is de nummering voor alle dubbele voetnoten gelijk.

1. Sleep de component **[!UICONTROL Footnote Placeholder]** vanuit de componentbrowser naar het adaptieve formulier.
   >[!NOTE]
   >
   >* In de publicatie-instantie worden voetnoten weergegeven op de positie waar de component **[!UICONTROL Footnote Placeholder]** op het adaptieve formulier wordt geplaatst.
   >* Wanneer u tussen verschillende deelvensters navigeert, verschijnen in de **[!UICONTROL Footnote Placeholder]** alleen zichtbare voetnoten die aanwezig zijn in het deelvenster met navigatie.

1. Sla de eigenschappen op.

Tijdens de runtime wordt het getal in de tekst weergegeven als een superscript en wordt de bijbehorende beschrijving weergegeven in de component **[!UICONTROL Footnote]** op de positie waar [!UICONTROL Footnote Placeholder] op het adaptieve formulier is geplaatst. U kunt rechtstreeks naar de voetnootbeschrijving navigeren door op het bijbehorende nummer in de [!UICONTROL Footnote] te klikken.


## Zie ook {#see-also}

{{see-also}}