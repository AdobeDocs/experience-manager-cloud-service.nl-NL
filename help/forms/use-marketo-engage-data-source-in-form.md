---
Title: How to configure Marketo Engage data for Adaptive Forms?
Description: Learn how to use Marketo Engage schema in Adaptive Forms.
Keywords: Use Marketo Engage data source in Adaptive Forms, How to connect a Marketo instance data source with form? , Connect a form to Marketo.
Feature: Adaptive Forms, Form Data Model
Role: User, Developer
exl-id: 4656ec65-f1ad-4e97-8d93-25933cdc7f7b
source-git-commit: dabf8029577c5fb6bb5eebdbf10d77f3d4d95a5d
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 0%

---

# Marketo Engage-gegevensbron configureren voor bestaande Adaptive Forms

<span class="preview"> De functie is beschikbaar in het programma voor vroege adoptie. U kunt vanaf uw officiële e-mailadres naar aem-forms-ea@adobe.com schrijven om deel te nemen aan het programma voor vroege adoptie en toegang tot de functie te vragen. </span>

![Workflow](/help/forms/assets/workflow-marketo-2.png)

Nadat u de configuratie van de cloudservice hebt gemaakt om Marketo Engage te integreren met de bestaande AEM Forms, kunt u de gegevensbron voor formulieren configureren.

Door gegevensintegratie te configureren, kunnen gebruikers verbinding maken met verschillende gegevensbronnen of schema&#39;s. Door te integreren met de Marketo Engage-gegevensbron en deze in verschillende formulieren te gebruiken, kunt u bewerkingen op die gegevens uitvoeren. Om de gesteunde uit-van-de-doos gegevensbronnen voor een Aanpassings Vorm te onderzoeken, verwijs naar [ vormen Gegevensbronnen ](/help/forms/configure-data-sources.md) artikel.

## Overwegingen bij het configureren van de Marketo Engage-gegevensbron voor formulieren

Denk aan het configureren van Marketo Engage-gegevensbron voor formulieren:

* Het is niet mogelijk om Edge Delivery Services Forms met Marketo Engage te verbinden.

## Vereiste om Marketo Engage-gegevensbron voor formulieren te gebruiken

Vereiste om Marketo Engage-gegevensbron met formulieren te gebruiken:

* Creeer de [ configuratie van de wolkendienst om Marketo Engage met vormen ](/help/forms/integrate-form-to-marketo-engage.md) te integreren.

## Hoe te om bestaand Aangepast Vorm voor de gegevensbron van Marketo Engage te vormen?

>[!VIDEO](https://video.tv.adobe.com/v/3442871/marketo-aem-forms-aem-marketo-engage)

<span> Deze video is alleen van toepassing op Core Components. Voor de Componenten van de UE/Foundation, gelieve naar het artikel te verwijzen.</span>

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Voer de volgende stappen uit om een adaptief formulier te configureren op basis van Foundation Components met de Marketo Engage-gegevensbron:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.
1. Open de Adaptieve Vorm voor het uitgeven en navigeer aan **[!UICONTROL Data Model]** sectie van de Adaptieve eigenschappen van de Container van de Vorm en selecteer een vormmodel als **Schakelaar**.
1. Selecteer de **[!UICONTROL Connector]** in de vervolgkeuzelijst.
1. Nadat u **[!UICONTROL Connector]** hebt geselecteerd, kunt u de cloudconfiguratie selecteren.

   ![ Uitgezochte Verbinding van Marketo ](/help/forms/assets/select-marketo-connector-af1.png){width=50%, height=50%}

   Op basis van de geselecteerde Marketo Engage-configuratie worden de formulierelementen weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van de **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen slepen en neerzetten om het adaptieve formulier te maken.

   ![ Source van Gegevens van Marketo ](/help/forms/assets/marketo-engage-data-source-af1.png){width=50%, height=50%}

1. Klik op **[!UICONTROL Done]**.

U kunt ook de eigenschappen van het adaptieve formulier bewerken om de bijbehorende configuratie te wijzigen.

Het adaptieve formulier is nu geconfigureerd met de gegevensbron van het aangesloten Marketo Engage-exemplaar. Configureer het nu om gegevens naar Adobe Marketo Engage te verzenden.

>[!TAB  Component van de Kern ]

Voer de volgende stappen uit om een adaptief formulier te configureren op basis van Core Components met de Marketo Engage-gegevensbron:

1. Meld u aan bij de [!DNL Experience Manager Forms] Author-instantie.

1. Open het adaptieve formulier voor bewerking.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Guide Container]** .
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend om de gegevensbron te configureren.
1. Open het **[!UICONTROL Data Model]** lusje en selecteer een vormmodel als **Schakelaar**.
1. Selecteer de **[!UICONTROL Connector]** in de vervolgkeuzelijst.

1. Nadat u **[!UICONTROL Connector]** hebt geselecteerd, kunt u de cloudconfiguratie selecteren.

   ![ Uitgezochte Verbinding van Marketo ](/help/forms/assets/select-marketo-connector.png){width=50%, height=50%}

   Op basis van de geselecteerde Marketo Engage-configuratie worden de formulierelementen weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van de **[!UICONTROL Content Browser]** in de zijbalk. U kunt deze elementen slepen en neerzetten om het adaptieve formulier te maken.

   ![ Source van Gegevens van Marketo ](/help/forms/assets/marketo-engage-data-source.png){width=50%, height=50%}

1. Klik op **[!UICONTROL Done]**.

U kunt ook de eigenschappen van het adaptieve formulier bewerken om de bijbehorende configuratie te wijzigen.

Het adaptieve formulier is nu geconfigureerd met de gegevensbron van het aangesloten Marketo Engage-exemplaar. Configureer het nu om gegevens naar Adobe Marketo Engage te verzenden.

>[!TAB  Universele Redacteur ]

Voer de volgende stappen uit om een adaptief formulier te configureren dat in de Universal Editor is geschreven met de Marketo Engage-gegevensbron:

1. Open de eigenschappen van het formulier voor bewerking.
1. Selecteer de **[!UICONTROL Form Model]** .
1. Selecteer **Schakelaar** van **[!UICONTROL Form Model]**.
1. Nadat u **[!UICONTROL Connector]** hebt geselecteerd, kunt u de cloudconfiguratie selecteren.

   ![ Uitgezochte Verbinding van Marketo ](/help/forms/assets/select-marketo-connector-ue.png)

1. Klik op **[!UICONTROL Save & Close]**.

Op basis van de geselecteerde Marketo Engage-configuratie worden de formulierelementen weergegeven op het tabblad **[!UICONTROL Datasource]** van de Inhoudsbrowser in het deelvenster Eigenschappen. U kunt deze elementen slepen en neerzetten om het adaptieve formulier te maken.

![ Source van Gegevens van Marketo ](/help/forms/assets/marketo-engage-data-source-ue.png)

Het formulier is nu geconfigureerd met de gegevensbron van het aangesloten Marketo Engage-exemplaar. Configureer het nu om gegevens naar Adobe Marketo Engage te verzenden.

>[!ENDTABS]

## Veelgestelde vragen (FAQ&#39;s)

**Q: Wat gebeurt wanneer u de schakelaar van de vorm verandert?**\
**A:** als u de schakelaar van de vorm verandert, worden de bestaande banden ongeldig.

**Q: Wat zijn de drie verrichtingen beschikbaar in de Invoke Dienst van de Redacteur van de Regel voor vormen die met Marketo Engage worden geïntegreerd?**\
**A:** de drie uit-van-de-doos verrichtingen beschikbaar in **roepen de Dienst** voor vormen die met Marketo Engage worden geïntegreerd zijn:
* Lead synchroniseren
* Lead ophalen op id
* Regelafstand op filtertype ophalen

## Volgende stap

Nu hebt u de Marketo Engage-gegevensbron geconfigureerd voor Adaptive Forms. Daarna, kunt u [ een Aangepast Vorm vormen om gegevens naar Marketo Engage ](/help/forms/submit-adaptive-form-to-marketo-engage.md) te verzenden.

## Verwante artikelen

{{af-submit-action}}

## Zie ook

{{marketo-engage-see-also}}
