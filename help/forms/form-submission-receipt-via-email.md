---
title: Hoe kan ik een ontvangstbevestiging voor formulierverzending via e-mail verzenden in AEM Forms?
description: Met AEM Forms kunt u de handeling Verzenden via e-mail configureren die een bevestiging naar een gebruiker stuurt bij het verzenden van het formulier.
uuid: c80b1ef4-8fe3-48e0-8fc6-3032dc022a38
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---


# Een bevestiging van het verzenden van een formulier verzenden via e-mail {#sending-a-form-submission-acknowledgement-via-email}

## Aangepaste verzending van formuliergegevens {#adaptive-form-data-submission}

Adaptive Forms biedt verschillende kant-en-klare [Handelingen verzenden](configuring-submit-actions.md) workflows voor het verzenden van de formuliergegevens naar verschillende eindpunten.

Bijvoorbeeld de **[!UICONTROL Send email]** Met Actie verzenden wordt een e-mail verzonden wanneer een adaptief formulier met succes is verzonden. Het kan ook worden geconfigureerd om de formuliergegevens en de PDF in de e-mail te verzenden.

In dit artikel worden de stappen beschreven waarmee de e-mailactie wordt ingeschakeld op een adaptief formulier en op verschillende configuraties ervan.

>[!NOTE]
>
>U kunt ook de opdracht **[!UICONTROL Send PDF via email]** om het ingevulde formulier per e-mail te verzenden als een PDF-bijlage. De configuratieopties die beschikbaar zijn voor deze actie zijn gelijk aan de opties die beschikbaar zijn voor de **[!UICONTROL Send email]** handeling. De PDF-actie via e-mail is alleen beschikbaar voor adaptieve Forms op basis van XFA

## E-mailactie verzenden {#email-action}

Met de handeling E-mail verzenden kan een auteur automatisch e-mail verzenden naar een of meer ontvangers wanneer een adaptief formulier is verzonden.

<!-- >>[!NOTE]
>
>To use the Send email action, you need to configure the AEM mail service as described in [Configuring the mail service](/help/sites-administering/notification.md#configuring-the-mail-service).

### Enabling Send email action on an Adaptive Form {#enabling-email-action-on-an-adaptive-form}

1. Open an Adaptive Form in **[!UICONTROL edit]** mode.

1. In the **[!UICONTROL Content]** tab, tap **[!UICONTROL Form Container]** and tap ![configure](assets/configure-icon.svg) to view the Adaptive Form properties.  

1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Send email]** from the **[!UICONTROL Submit Action]** drop-down list.  

   ![Submit Actions](assets/submission-actions.png)

1. Specify valid email IDs in the **[!UICONTROL To]**, **[!UICONTROL CC]**, and **[!UICONTROL BCC]** fields.

   Specify the subject and the body of the email in the **[!UICONTROL Subject]** and **[!UICONTROL Email Template]** fields, respectively.

   You can also specify variable placeholders in the fields, in which case, the values of the fields are processed when the form is successfully submitted by an end user. For more information, see [Using Adaptive Form field names to dynamically create email content](form-submission-receipt-via-email.md#p-using-adaptive-form-field-names-to-dynamically-create-email-content-p).

   Select **[!UICONTROL Include attachments]** if the form includes file attachments and you want to attach these files in the email.

   >[!NOTE]
   >
   >If you choose the **[!UICONTROL Send PDF via Email]** option, you must select the Include attachments option.

1. Click ![save](assets/save_icon.svg) to save the changes. -->

### Veldnamen van Adaptief formulier gebruiken om dynamisch e-mailinhoud te maken {#using-adaptive-form-field-names-to-dynamically-create-email-content}

De veldnamen in een adaptief formulier worden tijdelijke aanduidingen genoemd die worden vervangen door de waarde van dat veld nadat een gebruiker het formulier heeft verzonden.

In de **[!UICONTROL Send email]** gebruiken, kunt u plaatsaanduidingen gebruiken die worden verwerkt wanneer de handeling wordt uitgevoerd. Dit betekent dat de kopteksten van de e-mail (zoals **[!UICONTROL To]**, **[!UICONTROL CC]**, **[!UICONTROL BCC]**, **[!UICONTROL Subject]**) worden gegenereerd wanneer de gebruiker het formulier verzendt.

Als u een tijdelijke aanduiding wilt definiëren, geeft u `${<field name>}` in een veld na het selecteren **[!UICONTROL Send email]** als handeling verzenden.

Als het formulier bijvoorbeeld het **[!UICONTROL Email address]** veld, naam `email_addr`Voor het vastleggen van de e-mailadres van een gebruiker kunt u het volgende opgeven in het dialoogvenster **[!UICONTROL To]**, **[!UICONTROL CC]**, of **[!UICONTROL BCC]** velden.

`${email_addr}`

Wanneer een gebruiker het formulier verzendt, wordt een e-mailbericht verzonden naar de e-mailid die is ingevoerd in het dialoogvenster `email_addr` veld van het formulier.

>[!NOTE]
>
>U kunt de naam van een veld vinden in het dialoogvenster **[!UICONTROL Edit]** voor het veld.

U kunt ook plaatsaanduidingen voor variabelen gebruiken in het dialoogvenster **[!UICONTROL Subject]** en **[!UICONTROL Email Template]** velden.

Bijvoorbeeld:

`Hi ${first_name} ${last_name},`

`Your form has been received by our department. It usually takes ten business days to process the request.`

`Regards`

`Administrator`

>[!NOTE]
>
>Velden in herhaalbare deelvensters kunnen niet worden gebruikt als plaatsaanduidingen voor variabelen.

