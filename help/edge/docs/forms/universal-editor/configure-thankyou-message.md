---
title: Hoe te om een Redirect Pagina of Dank u bericht te vormen?
description: Leer hoe gebruikers een bedankt-uw-bericht kunnen worden getoond of aan een webpagina kunnen worden opnieuw gericht die de vormauteurs kunnen vormen terwijl het creëren van het formulier.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 87650caea6eb907093f0f327f1dbc19641098e4a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# Omleiding configureren of Bericht van bedankt

In formulieren die zijn gemaakt met de Universal Editor kunnen formulierauteurs configureren wat er gebeurt nadat een gebruiker een formulier heeft verzonden. U kunt een bedankbericht weergeven of de gebruiker omleiden naar een specifieke webpagina via het tabblad Verzending in de extensie Formuliereigenschappen bewerken.

U kunt het Thankyou-bericht of Rediect URLs voor vormen vormen vormen die in de Universele Redacteur worden gecreeerd gebruikend het **Verzending** lusje van de **3&rbrace; uitbreiding van de Eigenschappen van de Vorm van AEM.**

## Vereisten

U kunt de verzendactie voor vormen vormen vormen die in de Universele Redacteur worden gecreeerd gebruikend het **lusje van de Verzending** van **uitgeven de uitbreiding van de Eigenschappen van de Vorm**.

![ de eigenschappen van de Vorm pictogram ](/help/forms/assets/ue-form-properties-icon.png)

![ Universele Eigenschappen van de Vorm van de Redacteur ](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
> * Als u niet het **pictogram van de Eigenschappen van de Vorm** in uw Universele interface van de Redacteur ziet, laat **toe geef de 3&rbrace; uitbreiding van de Eigenschappen van de Vorm &lbrace;in Extension Manager uit.**
> * Verwijs naar het [ artikel van de Hoogtepunten van de Eigenschap van 0&rbrace; Extension Manager om te leren hoe te om uitbreidingen in of onbruikbaar te maken in de Universele Redacteur.](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)

## Hoe te om Redirect te vormen of Dank u Bericht?

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht weergeven.

U kunt als volgt de omleidingspagina of het bedankbericht configureren:

1. Open het adaptieve formulier voor bewerking.
2. Open de inhoudsstructuur en selecteer de **[!UICONTROL Guide Container]** .
3. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
4. Open de tab **[!UICONTROL Submission]** . De opties om een omleidingspagina of een bericht te vormen worden getoond:

   ![ de dialoog van de Verzending van de Contaner van de Gids om een omleidingspagina of een bericht te vormen ](/help/forms/assets/adaptive-forms-core-components-redirect-page-or-thank-you-message.png)

**vorm Redirect URLs**

* Als u een omleidings-URL wilt configureren, selecteert u bij Verzenden de optie **[!UICONTROL Redirect to URL option]** en geeft u een absoluut adres, een omleidings-URL of een relatief pad van een AEM Sites-pagina op.

![ redirect ](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**vorm Thanku bericht**

* Als u een aangepast bericht of een bedankbericht wilt configureren, selecteert u de optie **[!UICONTROL Show Message]** en geeft u een bericht op in het vak Berichtinhoud. Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

![ bedankt ](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

Formulierauteurs kunnen een pagina configureren voor elk formulier, waarnaar de formuliergebruikers worden omgeleid na het verzenden van een formulier.
