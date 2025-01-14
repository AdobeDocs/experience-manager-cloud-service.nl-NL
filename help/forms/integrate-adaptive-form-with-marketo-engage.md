---
Title: How to integrate Marketo Engage with AEM Forms using Form wizard?
Description: Learn how to integrate your Marketo Engage instance with AEM Forms using form wizard.
Keywords: How to connect a Marketo instance with form? , Connect a form to Marketo, Integrate a form with Marketo Engage, Integrate an Adaptive Form with a Marketo instance.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 1fcba628-ffd8-416a-a8b5-76b35d4aabd4
source-git-commit: e46c5afac945620cc44e9064956848acecc786bf
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 0%

---

# Nieuw formulier configureren voor integratie met Marketo Engage

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-4.png)

Na het creëren van de configuratie van de wolkendienst om Marketo Engage met AEM Forms te integreren, kunt u een Aangepast Vorm vormen om met [ Adobe Marketo Engage ](https://experienceleague.adobe.com/en/docs/marketo/using/home) te integreren.

U kunt een Marketo Engage verbinden met een adaptief formulier met de wizard Formulier. Hiermee vereenvoudigt u het configuratieproces door u door elke stap te begeleiden. Het omvat het selecteren van sjablonen, stijlen en gegevensvelden en het instellen van gegevenstoewijzing om te controleren of uw formulier klaar is om te communiceren met het Marketo Engage nadat het is gemaakt. Met de wizard Formulier kunt u het Adaptief formulier ook zodanig configureren dat gegevens bij verzending rechtstreeks naar Adobe Marketo Engage worden verzonden.

## Overwegingen bij het configureren van de gegevensbron van het Marketo Engage voor formulieren

Tijdens het configureren van de gegevensbron van Marketo&#39;s Engage voor formulieren wordt rekening gehouden met het volgende:

* Het is niet mogelijk om Edge Delivery Services Forms met Marketo Engage te verbinden.

## Vereiste om Marketo Engage te verbinden met formulieren

Vereiste om Marketo Engage te verbinden met formulieren:

* Creeer de [ configuratie van de wolkendienst om Marketo Engage met vormen ](/help/forms/integrate-form-to-marketo-engage.md) te integreren.

## Hoe te om nieuw Aangepast Vorm te vormen om met Marketo Engage te integreren?

>[!VIDEO](https://video.tv.adobe.com/v/3442867/marketo-aem-marketo-engage-engage-aem-forms)

Voer de volgende stappen uit om een nieuw adaptief formulier te configureren voor integratie met Marketo Engage:

1. Selecteer **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

   ![ Uitgezochte Forms en Documenten ](/help/forms/assets/select-forms.png)

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Adaptive Forms]** . De wizard Formulier maken wordt geopend.

   ![ Uitgezochte AF ](/help/forms/assets/select-create-forms.png)

1. Selecteer op het tabblad **[!UICONTROL Source]** een sjabloon

   ![ Uitgezochte Malplaatjes ](/help/forms/assets/select-template.png)

1. Selecteer het thema in het **[!UICONTROL Style]** .

   ![ Uitgezochte Thema ](/help/forms/assets/select-form-theme.png)


1. In het **[!UICONTROL Data]** lusje, selecteer een gegevensmodel als **Marketo Engage**.

1. Selecteer **[!UICONTROL Cloud Configuration]** van de drop-down lijst die in de juiste ruit van het scherm verschijnt.
Standaard worden alle velden in de gekoppelde configuratie weergegeven. De wizard biedt u het gemak om via selectievakjes te kiezen welke velden moeten worden opgenomen in het adaptieve formulier.

   ![ Uitgezochte Gegevensmodel ](/help/forms/assets/select-marketo-data.png)

1. Selecteer op het tabblad **[!UICONTROL Submission]** de optie Verzenden als **[!UICONTROL Submit to Marketo]** .

   Wanneer u het gegevensmodel als **Marketo Engage** selecteert, dan verzend actie zoals **voorlegt aan Marketo** wordt auto-geselecteerd. U kunt een andere verzendactie selecteren op het tabblad **[!UICONTROL Submission]** . Op het tabblad **[!UICONTROL Submission]** worden alle beschikbare verzendhandelingen weergegeven.

   ![ voorleggen aan Marketo treedt ](/help/forms/assets/select-marketo-engage.png) in werking

1. Selecteer **[!UICONTROL Create]**. Geef een titel, naam en locatie op om het adaptieve formulier op te slaan.

   ![ creeer Vorm ](/help/forms/assets/create-marketo-form.png)

1. Selecteer **[!UICONTROL Create]** .

Het adaptieve formulier is nu geconfigureerd voor verbinding met een Marketo Engage-instantie. U kunt ook de eigenschappen van het adaptieve formulier bewerken om de bijbehorende configuratie te wijzigen.

## Veelgestelde vragen (FAQ&#39;s)

**Q: Kan u verzendactie voor vormen veranderen die om met het schema van het Marketo Engage worden gevormd te verbinden?**
**A:** Door gebrek, **voorleggen aan Marketo** actie wordt geselecteerd wanneer een vorm wordt gevormd om met het schema van het Marketo Engage te verbinden. U kunt de verzendactie voor de formulieren echter wijzigen als dat nodig is.


**Q: Wat gebeurt wanneer u de schakelaar van de vorm verandert?**\
**A:** als u de schakelaar van de vorm verandert, worden de bestaande banden ongeldig.

**Q: Wat zijn de drie verrichtingen beschikbaar in de Invoke Dienst van de Redacteur van de Regel voor vormen die met Marketo Engage worden geïntegreerd?**\
**A:** de drie uit-van-de-doos verrichtingen beschikbaar in **roepen de Dienst** voor vormen die met Marketo Engage worden geïntegreerd zijn:
* Lead synchroniseren
* Lead ophalen op id
* Regelafstand op filtertype ophalen

## Volgende stap

U kunt een AanpassingsVorm met de [ bibliotheek van Munchkin ](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) ook verbinden om het aantal bezoeken, klikken, en vormvoorlegging te volgen.

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}
