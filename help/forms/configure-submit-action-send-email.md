---
Title: How to send an email on submission of an Adaptive Form?
Description: Explore the process to set up email notifications when submitting an Adaptive Form.
keywords: hoe u een e-mail verzendt voor een formulier, een handeling voor e-mail verzenden, een adaptief formulier per e-mail, een formulierverzending per e-mail, een verzendgids
feature: Adaptive Forms, Core Components
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
title: "Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?"
role: User, Developer
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 1%

---

# De handeling E-mail verzenden voor een adaptief formulier configureren

De **[!UICONTROL Send Email]** Met Actie verzenden kunt u een e-mail naar een of meer ontvangers verzenden wanneer het formulier met succes is verzonden. Met deze handeling Verzenden kunt u een e-mail maken die formuliergegevens in een vooraf gedefinieerde indeling kan bevatten. Neem bijvoorbeeld de volgende sjabloon waar de naam van de klant, het verzendadres, de naam van de staat en de postcode worden opgehaald uit de ingediende formuliergegevens:


    &quot;
    Hallo ${customer_Name},
    
    Het volgende is ingesteld als je standaard verzendadres:
    ${customer_Name},
    ${customer_Shipping_Address},
    ${customer_State},
    ${customer_ZIPCode}
    
    met betrekking tot
    WKND
    
    &quot;


## Voordelen

De volgende voordelen hebben het configureren van een adaptief formulier met de actie E-mail verzenden:

* Hiermee kunt u snel communiceren terwijl formuliergegevens rechtstreeks naar bepaalde e-mailontvangers worden verzonden.
* Het helpt de workflow te stroomlijnen door formulierverzendingen rechtstreeks te integreren in e-mailmeldingen.
* Het helpt organisaties de e-mailinhoud aanpassen, zodat het geschikt wordt gemaakt voor specifieke communicatiebehoeften.

## Handeling voor verzenden van e-mail configureren {#steps-to-configure-send-email-submit-action}

De handeling verzenden configureren:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de knop  **[!UICONTROL Submission]** tab.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Send email]**.

   ![Actieconfiguratie van Send Email](/help/forms/assets/send-email-action-configuration.gif)
1. Geef de e-mailid van de afzender op in het dialoogvenster **[!UICONTROL From]** textbox.
1. Voeg de e-mailid van de ontvanger toe in het dialoogvenster **[!UICONTROL To]** textbox. U kunt meerdere ontvangers toevoegen door op de knop **[!UICONTROL Add]** knop.
1. [Optioneel] Voeg de ontvanger voor CC en BCC toe door te klikken op **[!UICONTROL Add]** knop.
1. Geef een onderwerpregel op in het dialoogvenster **[!UICONTROL Subject]** textbox.
1. Voeg een e-mailsjabloon toe om de verzendactie voor verzending van e-mail te configureren.
   * U kunt het pad naar de externe e-mailsjabloon die in uw AEM is opgeslagen, opgeven met de opdracht **[!UICONTROL External Template Path]** -optie.
   * U kunt ook een aangepaste e-mailsjabloon toevoegen voor het verzenden van het formulier in het dialoogvenster **[!UICONTROL Email Template]** textbox.
1. [Optioneel] De **[!UICONTROL Send Email]** Met Actie verzenden kunt u bijlagen en een [Document of Record (DoR)](generate-document-of-record-core-components.md) met het e-mailbericht.
1. Klik op **[!UICONTROL Done]**.

## Aanbevolen procedures {#best-practices}

* Het wordt aanbevolen de e-mailinhoud duidelijk en beknopt te houden. Gebruikers dienen inzicht te hebben in het doel van de e-mail en in de acties die ze moeten ondernemen.
* Het wordt aanbevolen dat alle formuliervelden unieke elementnamen hebben, zelfs als ze op verschillende deelvensters in een adaptief formulier zijn geplaatst.
* Bij gebruik van AEM as a Cloud Service is codering vereist voor uitgaande e-mail. Standaard is de functie voor uitgaande e-mail uitgeschakeld. Als u het wilt activeren, verzendt u een ondersteuningsticket naar [verzoek om toegang](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).


## Verwante artikelen

{{af-submit-action}}
