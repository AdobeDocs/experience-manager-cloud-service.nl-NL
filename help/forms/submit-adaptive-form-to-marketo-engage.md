---
Title: How to configure submit action to Marketo Engage for forms?
Description: Learn how to configure the submit action of Adaptive Form to send data to Marketo Engage.
Keywords: Submit data to Marketo engage, Configure submit action as Submit to Marketo Engage
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# De handeling Verzenden naar Marketo Engage configureren voor bestaande formulieren

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-3.png)

De adaptieve redacteur van Forms verstrekt **voorleggen aan Marketo Engage** actie om de Adaptieve gegevens van Forms naar Adobe Marketo Engage voor verwerking te verzenden. U kunt een bestaande Aangepaste Vorm vormen om gegevens aan [ Adobe Marketo Engage ](https://experienceleague.adobe.com/en/docs/marketo/using/home) op voorlegging voor te leggen.

Er zijn verschillende verzendacties beschikbaar die niet in de verpakking staan en waarmee formulierverzendingen kunnen worden verwerkt. U kunt meer over deze opties leren in het [ AanpassingsVorm voorlegt Artikel van de Actie ](/help/forms/configure-submit-actions-core-components.md).

## Overwegingen bij het configureren van verzendactie naar Marketo Engage voor formulier

* Zorg ervoor dat het adaptieve formulier is geconfigureerd met de gegevensbron van het Marketo Engage om gegevens naar het Marketo Engage te verzenden bij het verzenden van het formulier. Nochtans, kunt u de verzendactie aan alternatieven veranderen, bijvoorbeeld, **voorleggen aan OneDrive** of **voorleggen aan SharePoint**, zelfs als de vorm met het schema van de Marketo Engage gegevens wordt gevormd.

## Vereiste om de verzendhandeling voor een bestaand formulier te configureren naar Marketo Engage

Vereiste om de verzendhandeling naar Marketo Engage te configureren:

* Vorm de [ gegevensbron van het Marketo Engage voor Aangepaste Vorm ](/help/forms/use-marketo-engage-data-source-in-form.md) en verbind de vormelementen met de gebieden van het Marketo Engage.

## Hoe te vormen verzend actie aan Marketo Engage voor bestaande vormen?

U kunt de verzendactie van een adaptief formulier configureren om gegevens naar Adobe Marketo Engage te verzenden. Voer de volgende stappen uit om de verzendactie naar Marketo Engage te configureren:

1. Open het adaptieve formulier voor bewerking.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Guide Container]** .
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer om verzendactie te configureren wordt geopend.
1. Open het **[!UICONTROL Submission]** lusje en selecteer voorlegt actie aangezien **aan Marketo Engage** voorlegt.
1. Klik op **[!UICONTROL Done]**.

![ Marketo legt Actie ](/help/forms/assets/marketo-engage-submit-action.png) {width=50% voor, height=50%}


Na het vormen van voorlegt actie voor de Aangepaste Vorm zoals **voorleggen aan Marketo Engage**, kunt u gegevens naar Adobe Marketo Engage voor verwerking verzenden. De gegevens kunnen worden gebruikt voor het analyseren en optimaliseren van marketingcampagnes, het automatiseren van follow-up-e-mails en het activeren van workflows op basis van formulierverzendingen.

## Veelgestelde vraag (FAQ)

**Q: Kan u verzendactie voor vormen veranderen die om met het schema van het Marketo Engage worden gevormd te verbinden?**
**A:** Door gebrek, **voorleggen aan Marketo** actie wordt geselecteerd wanneer een vorm wordt gevormd om met het schema van het Marketo Engage te verbinden. U kunt de verzendactie voor de formulieren echter wijzigen als dat nodig is.

## Volgende stap

U kunt een AanpassingsVorm met de [ bibliotheek van Munchkin ](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/setup/munchkin) ook verbinden om het aantal bezoeken, klikken, en vormvoorlegging te volgen.

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}
