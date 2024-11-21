---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
source-git-commit: 681c194f997ab66f93beedad4eea273614e6797d
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---


# Gegevensbron van Marketo Engage configureren voor bestaande adaptieve Forms

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-2.png)

Nadat u de cloudserviceconfiguratie hebt gemaakt om Marketo Engage te integreren met bestaande AEM Forms, kunt u de gegevensbron voor formulieren configureren.

Door gegevensintegratie te configureren, kunnen gebruikers verbinding maken met verschillende gegevensbronnen of schema&#39;s. Het integreren met de gegevensbron van het Marketo Engage en het gebruiken van het over verschillende vormen vergemakkelijkt verrichtingen op die gegevens. Om de gesteunde uit-van-de-doos gegevensbronnen voor een Aanpassings Vorm te onderzoeken, verwijs naar [ vormen Gegevensbronnen ](/help/forms/configure-data-sources.md) artikel.

## Overwegingen bij het configureren van de gegevensbron van het Marketo Engage voor formulieren

Tijdens het configureren van de gegevensbron van Marketo&#39;s Engage voor formulieren wordt rekening gehouden met het volgende:

* Het is niet mogelijk om Edge Delivery Services Forms met Marketo Engage te verbinden.

## Vereiste voor gebruik van Marketo Engage-gegevensbron voor formulieren

Vereiste om Marketo Engage gegevensbron met vormen te gebruiken:

* Creeer de [ configuratie van de wolkendienst om Marketo Engage met vormen ](/help/forms/integrate-form-to-marketo-engage.md) te integreren.

## Hoe te om bestaande Aangepaste Vorm voor de gegevensbron van het Marketo Engage te vormen?

Voer de volgende stappen uit om een adaptief formulier te configureren met de gegevensbron van het Marketo Engage:
1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.

1. Open het adaptieve formulier voor bewerking.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Guide Container]** .
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend om de gegevensbron te configureren.
1. Open het **[!UICONTROL Data Model]** lusje en selecteer een vormmodel als **Schakelaar**.
1. Selecteer de **[!UICONTROL Connector]** in de vervolgkeuzelijst.

1. Nadat u **[!UICONTROL Connector]** hebt geselecteerd, kunt u de cloudconfiguratie selecteren.

   ![ Uitgezochte Verbinding van Marketo ](/help/forms/assets/select-marketo-connector.png)

   Op basis van de geselecteerde configuratie van het Marketo Engage worden de formulierelementen weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van de **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen slepen en neerzetten om het adaptieve formulier te maken.

   ![ Source van Gegevens van Marketo ](/help/forms/assets/marketo-engage-data-source.png)

1. Klik op **[!UICONTROL Done]**.

U kunt ook de eigenschappen van het adaptieve formulier bewerken om de bijbehorende configuratie te wijzigen.

Het adaptieve formulier is nu geconfigureerd met de gegevensbron van de aangesloten Marketo Engage-instantie. Configureer het nu om gegevens naar Adobe Marketo Engage te verzenden.

## Veelgestelde vragen (FAQ&#39;s)

**Q: Wat gebeurt wanneer u de schakelaar van de vorm verandert?**\
**A:** als u de schakelaar van de vorm verandert, worden de bestaande banden ongeldig.

**Q: Wat zijn de drie verrichtingen beschikbaar in de Invoke Dienst van de Redacteur van de Regel voor vormen die met Marketo Engage worden geïntegreerd?**\
**A:** de drie uit-van-de-doos verrichtingen beschikbaar in **roepen de Dienst** voor vormen die met Marketo Engage worden geïntegreerd zijn:
* Lead synchroniseren
* Lead ophalen op id
* Regelafstand op filtertype ophalen

## Volgende stap

Nu, hebt u de gegevensbron van het Marketo Engage voor Adaptief Forms gevormd. Daarna, kunt u een Aangepaste Vorm vormen [ om gegevens naar Marketo Engage ](/help/forms/submit-adaptive-form-to-marketo-engage.md) te verzenden.

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}


