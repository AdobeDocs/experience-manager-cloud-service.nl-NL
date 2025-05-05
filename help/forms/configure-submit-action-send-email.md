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

Met de handeling **[!UICONTROL Send Email]** Verzenden kunt u een e-mail verzenden naar een of meer ontvangers nadat het formulier is verzonden. Met deze handeling Verzenden kunt u een e-mail maken die formuliergegevens in een vooraf gedefinieerde indeling kan bevatten. Neem bijvoorbeeld de volgende sjabloon waar de naam van de klant, het verzendadres, de naam van de staat en de postcode worden opgehaald uit de ingediende formuliergegevens:


    &quot;
     Hi $ {customer_Name}, 
    
     het volgende wordt geplaatst als uw standaard verschepend adres:
     $ {customer_Name}, 
     $ {customer_Shipping_Address}, 
     $ {customer_State}, 
     $ {customer_ZIPCode} 
    
     Regards, 
     WKND 
    
    &quot;


## Voordelen

De volgende voordelen hebben het configureren van een adaptief formulier met de actie E-mail verzenden:

* Hiermee kunt u snel communiceren terwijl formuliergegevens rechtstreeks naar bepaalde e-mailontvangers worden verzonden.
* Het helpt de workflow te stroomlijnen door formulierverzendingen rechtstreeks te integreren in e-mailmeldingen.
* Het helpt organisaties de e-mailinhoud aanpassen, zodat het geschikt wordt gemaakt voor specifieke communicatiebehoeften.

## Handeling voor verzenden van e-mail configureren {#steps-to-configure-send-email-submit-action}

De handeling verzenden configureren:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de tab **[!UICONTROL Submission]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Send email]**.

   ![ configuratie van de Actie van Send E-mail ](/help/forms/assets/send-email-action-configuration.gif)
1. Geef de e-mailid van de afzender op in het tekstvak **[!UICONTROL From]** .
1. Voeg de e-mailid van de ontvanger toe in het tekstvak **[!UICONTROL To]** . U kunt meerdere ontvangers toevoegen door op de knop **[!UICONTROL Add]** te klikken.
1. [ Facultatieve ] voeg de ontvanger voor CC en BCC toe door de **[!UICONTROL Add]** knoop te klikken.
1. Geef een onderwerpregel op in het tekstvak **[!UICONTROL Subject]** .
1. Voeg een e-mailsjabloon toe om de verzendactie voor verzending van e-mail te configureren.
   * Met de optie **[!UICONTROL External Template Path]** kunt u het pad naar de externe e-mailsjabloon opgeven die in uw AEM is opgeslagen.
   * U kunt ook een aangepaste e-mailsjabloon toevoegen voor het verzenden van het formulier in het tekstvak **[!UICONTROL Email Template]** .
1. [ Facultatieve ] **[!UICONTROL Send Email]** legt Actie voor verstrekt de optie om gehechtheid en a [ Document van Verslag (DoR) ](generate-document-of-record-core-components.md) met e-mail te omvatten.
1. Klik op **[!UICONTROL Done]**.

## Aanbevolen procedures {#best-practices}

* Het wordt aanbevolen de e-mailinhoud duidelijk en beknopt te houden. Gebruikers dienen inzicht te hebben in het doel van de e-mail en in de acties die ze moeten ondernemen.
* Het wordt aanbevolen dat alle formuliervelden unieke elementnamen hebben, zelfs als ze op verschillende deelvensters in een adaptief formulier zijn geplaatst.
* Bij gebruik van AEM as a Cloud Service is codering vereist voor uitgaande e-mail. Standaard is de functie voor uitgaande e-mail uitgeschakeld. Om het te activeren, leg een steunkaartje voor aan [ verzoektoegang ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=nl-NL#sending-email).


## Verwante artikelen

{{af-submit-action}}
