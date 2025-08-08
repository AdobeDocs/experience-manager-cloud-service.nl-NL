---
description: Ontdek het proces voor het instellen van e-mailmeldingen bij het verzenden van een adaptief formulier.
keywords: hoe u een e-mail verzendt voor een formulier, een handeling voor e-mail verzenden, een adaptief formulier per e-mail, een formulierverzending per e-mail, een verzendgids
feature: Adaptive Forms, Core Components, Foundation Components, Edge Delivery Services
exl-id: 70386e57-345b-4edb-97f1-3fd52ea9ff4f
title: Hoe te om een Submit Actie voor een Aangepast Vorm te vormen?
role: User, Developer
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '796'
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

>[!BEGINTABS]

>[!TAB  Component van de Stichting ]

Een Send Email Submit Handeling voor de Component van de Stichting vormen:

1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Submit Action]** de optie **[!UICONTROL Send email]**.

   ![ configuratie van de Actie van Send E-mail ](/help/forms/assets/send-email-fc.png)

1. Geef de e-mailid van de afzender op in het tekstvak **[!UICONTROL From]** .
1. Voeg de e-mailid van de ontvanger toe in het tekstvak **[!UICONTROL To]** . U kunt meerdere ontvangers toevoegen door op de knop **[!UICONTROL Add]** te klikken.
1. [ Facultatieve ] voeg de ontvanger voor CC en BCC toe door de **[!UICONTROL Add]** knoop te klikken.
1. Geef een onderwerpregel op in het tekstvak **[!UICONTROL Subject]** .
1. Voeg een e-mailsjabloon toe om de verzendactie voor verzending van e-mail te configureren.
   * Met de optie **[!UICONTROL External Template Path]** kunt u het pad naar de externe e-mailsjabloon opgeven die is opgeslagen in uw AEM-elementen.
   * U kunt ook een aangepaste e-mailsjabloon toevoegen voor het verzenden van het formulier in het tekstvak **[!UICONTROL Email Template]** .
1. [ Facultatieve ] **[!UICONTROL Send Email]** legt Actie voor verstrekt de optie om gehechtheid en a [ Document van Verslag (DoR) ](generate-document-of-record-core-components.md) met e-mail te omvatten.
1. Klik op **[!UICONTROL Done]**.

>[!TAB  Component van de Kern ]

De handeling E-mail verzenden voor kerncomponent configureren:

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
   * Met de optie **[!UICONTROL External Template Path]** kunt u het pad naar de externe e-mailsjabloon opgeven die is opgeslagen in uw AEM-elementen.
   * U kunt ook een aangepaste e-mailsjabloon toevoegen voor het verzenden van het formulier in het tekstvak **[!UICONTROL Email Template]** .
1. [ Facultatieve ] **[!UICONTROL Send Email]** legt Actie voor verstrekt de optie om gehechtheid en a [ Document van Verslag (DoR) ](generate-document-of-record-core-components.md) met e-mail te omvatten.
1. Klik op **[!UICONTROL Done]**.

>[!TAB  Universele Redacteur ]

U kunt als volgt de handeling E-mail verzenden in de universele editor configureren:

1. Open het adaptieve formulier voor bewerking.
1. Klik **uitgeven de uitbreiding van de Eigenschappen van de Vorm** op de redacteur.
Het **de dialoogvakje van de Eigenschappen van de Vorm** verschijnt.

   >[!NOTE]
   >
   > * Als u niet **ziet geef de Eigenschappen van de Vorm** pictogram in uw Universele interface van de Redacteur uit, laat **toe geef de 3} uitbreiding van de Eigenschappen van de Vorm {in Extension Manager uit.**
   > * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0} Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)


1. Klik **Verzending** lusje en selecteer **[!UICONTROL Send email]** voorlegt actie.

   ![ verzend E-mail Universele Redacteur ](/help/forms/assets/send-email-ue.png)

1. Geef de e-mailid van de afzender op in het tekstvak **[!UICONTROL From]** .
1. Voeg de e-mailid van de ontvanger toe in het tekstvak **[!UICONTROL To]** . U kunt meerdere ontvangers toevoegen door op de knop **[!UICONTROL Add]** te klikken.
1. [ Facultatieve ] voeg de ontvanger voor CC en BCC toe door de **[!UICONTROL Add]** knoop te klikken.
1. Geef een onderwerpregel op in het tekstvak **[!UICONTROL Subject]** .
1. Voeg een e-mailsjabloon toe om de verzendactie voor verzending van e-mail te configureren.
   * Met de optie **[!UICONTROL External Template Path]** kunt u het pad naar de externe e-mailsjabloon opgeven die is opgeslagen in uw AEM-elementen.
   * U kunt ook een aangepaste e-mailsjabloon toevoegen voor het verzenden van het formulier in het tekstvak **[!UICONTROL Email Template]** .
1. [ Facultatieve ] **[!UICONTROL Send Email]** legt Actie voor verstrekt de optie om gehechtheid en a [ Document van Verslag (DoR) ](generate-document-of-record-core-components.md) met e-mail te omvatten.
1. Klik op **[!UICONTROL Save&Close]**.

>[!ENDTABS]

## Aanbevolen procedures {#best-practices}

* Het wordt aanbevolen de e-mailinhoud duidelijk en beknopt te houden. Gebruikers dienen inzicht te hebben in het doel van de e-mail en in de acties die ze moeten ondernemen.
* Het wordt aanbevolen dat alle formuliervelden unieke elementnamen hebben, zelfs als ze op verschillende deelvensters in een adaptief formulier zijn geplaatst.
* Bij gebruik van AEM as a Cloud Service is codering vereist voor uitgaande e-mail. Standaard is de functie voor uitgaande e-mail uitgeschakeld. Om het te activeren, leg een steunkaartje voor aan [ verzoektoegang ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email).

## Verwante artikelen

{{af-submit-action}}
