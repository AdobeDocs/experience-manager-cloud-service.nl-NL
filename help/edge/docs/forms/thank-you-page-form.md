---
title: Een aangepast bedankbericht weergeven na het verzenden van het formulier
description: Leer hoe u pagina's voor bedankt en omleiding voor Forms Block configureert om de gebruikerservaring te optimaliseren en gebruikersreizen te stroomlijnen.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Architect, Developer
source-git-commit: 4356fcc73a9c33a11365b1eb3f2ebee5c9de24f0
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 0%

---

# Een aangepast bedankbericht weergeven na het verzenden van het formulier

Nadat een gebruiker een formulier heeft verzonden, is het van cruciaal belang dat u een probleemloze ervaring opdoet via een bedankbericht. Het bevestigt niet alleen een succesvolle indiening, maar vergroot ook de tevredenheid van de gebruikers en begeleidt hen verder op hun reis.

* **Dank u bericht**: Een dank u bericht is een hoeksteen van gebruikerservaring, die geruststelling aanbiedt en belangrijke informatie overbrengt terwijl het versterken van merkidentiteit. Het dient als directe erkenning van de actie van de gebruiker, die een gevoel van voltooiing en tevredenheid bevordert.

* **opnieuw richten**: Een omleiding speelt een centrale rol in het sturen van gebruikers naar relevante bestemmingen, het optimaliseren van overeenkomst, en uiteindelijk het verhogen van omzettingspercentages. Door gebruikers naadloos naar de volgende stap op hun reis te leiden, zorgt een omleiding voor een vloeiende navigatie. U kunt bijvoorbeeld de gebruiker omleiden naar de pagina met betalingen nadat u de eerste gegevens hebt verzameld.

Het standaardgedrag van Adaptive Forms Block is om het volgende bedankbericht bij verzending weer te geven. Het bericht wordt boven aan het formulier weergegeven wanneer het formulier is verzonden.

![ gebrek dank u bericht ](/help/edge/assets/thank-you-message.png)

U hebt echter de flexibiliteit om deze ervaring af te stemmen op uw specifieke behoeften. U kunt onder andere de volgende opties kiezen:

* Een aangepast bedankbericht weergeven na het verzenden van het formulier
* Gebruikers doorsturen naar een andere pagina na verzending voor verdere actie

>[!NOTE]
>
> U kunt naar het volgende [ onderzoeksspreadsheet ](/help/edge/docs/forms/assets/enquiry.xlsx) verwijzen om te passen dankt u bericht volgens uw vereisten.

## Een aangepast bedankbericht configureren

Als u een gepersonaliseerd bedankbericht wilt weergeven wanneer het formulier is verzonden, kunt u het werkblad zo configureren dat het wordt weergegeven.

Voer de onderstaande stappen uit om een aangepast bedankbericht voor uw Adaptive Forms Block te configureren:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.
1. Voeg een aangepast bedankbericht toe in de kolom `value` voor het veldtype `submit` in de spreadsheet.

   ![ Aangepast Thanku bericht ](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Voeg bijvoorbeeld het bericht `Submission Successful!` in de kolom `value` toe voor het veldtype `submit` .

1. Voorproef en publiceer het blad gebruikend [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![ Aangepast Thanku bericht ](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Gebruikers omleiden naar een andere pagina na verzending

Het omleiden van een gebruiker naar een andere pagina na het verzenden van het formulier kan de gebruikerservaring verbeteren door relevante informatie op te geven, acties te bevestigen en gebruikers naar de gewenste resultaten te leiden. Bijvoorbeeld:

* nadat een gebruiker een inkoopformulier heeft ingevuld, wordt hij of zij omgeleid naar een betalingspagina om de transactie veilig te voltooien.
* wanneer een registratieformulier voor een gebeurtenis of webinar wordt verzonden, worden gebruikers omgeleid naar een bevestigingspagina met gebeurtenisdetails, zoals datum, tijd en locatie.

Voer de volgende stappen uit om gebruikers om te leiden naar een andere pagina:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.
1. Plak de URL in de kolom `value` voor het veldtype `submit` in het spreadsheet om de gebruiker om te leiden wanneer het formulier is verzonden.
Om de pagina aan een verschillende pagina om te leiden, gebruik [ de Documentatie van Edge Delivery ](https://www.aem.live/docs/) pagina URL.

   ![ Thankyou redirect URL ](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Voorproef en publiceer het blad gebruikend [ AEM Sidekick ](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![ Redirect het bericht van Thanku ](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

U kunt ook een nieuw documentbestand maken en de voorbeeld-URL toevoegen in de kolom `value` voor het veldtype `submit` .

Nadat een gebruiker een formulier heeft verzonden, is het belangrijk dat u een duidelijke bedankboodschap ontvangt. Het bevestigt dat de verzending is gelukt en verbetert de tevredenheid van de gebruiker.

## Zie ook

{{see-more-forms-eds}}

<!--
## Configuring a custom thank you message

The default behavior of Adaptive Forms Block is to display the following thank you message on submission. The message is displayed on the top of the form. 

![default thank you message](/help/edge/assets/thank-you-message.png)


Follow the below steps to configure a custom thank you message for your Adaptive Forms Block:

1. Access your AEM Project on your local machine or GitHub repository.

2. Navigate to [AEM Project Folder]\blocks\form\submit.js file for editing.

3. Locate the following code 

    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Thanks for your submission';

    ```

4. Replace the default message with your custom message. For example, 


    ```JavaScript

        thankYouMessage.innerHTML = payload?.body?.thankYouMessage || 'Your submission has been received and noted.';

    ```


1. Save the file. Commit the updated file to your GitHub Repository. Now, when you submit a form, the custom thank you message is displayed. For example,

![Custom thank you message](/help/edge/assets/custom-thank-you-message.png)

* **Thank you message**: A thank you message is a cornerstone of user experience, offering reassurance and conveying important information while reinforcing brand identity. It serves as a direct acknowledgment of the user's action, fostering a sense of completion and satisfaction.

* **Redirect**: A redirect plays a pivotal role in steering users towards relevant destinations, optimizing engagement, and ultimately boosting conversion rates. By seamlessly guiding users to the next step in their journey, a redirect ensures a smooth navigation experience. For example, redirecting user to payments page after collecting initial details. 

In the Adaptive Forms Block, the default behavior is to display a thank you message. However, you have the flexibility to tailor this experience to meet your specific needs. Options include:

* [Configuring a custom thank you message to align with your brand and communication goals](#configuring-the-thank-you-page-and-message) 
* [Redirecting users to another page post-submission for further action](#redirect-users-to-another-page-post-submission)

## Redirect users to another page post-submission

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 





1. Access your AEM Edge Delivery project folder on Microsoft SharePoint or Google Workspace.
1. Create a Microsoft Word or Google Docs file named "thankyou" within your project directory.
1. Add your thank you message to the "thankyou" file. </br>
   
    ![Example thank you page](/help/edge/assets/sample-thankyou-page.png) 

1. Use AEM Sidekick to preview and publish the "thankyou" file.

 Your Adaptive Forms Block displays the "thankyou" page on form submission. 

## Redirect users to another page post-submission

By default, the Adaptive Forms Block redirects the users to the "thankyou" page. To redirect users to a page other than the default "thankyou" page, you have two options: 

* [Replace the "thankyou" page with a different page](#replace-the-existing-thankyou-page) 
* [Use website redirects for "thankyou" page redirection](#use-website-redirects-for-thankyou-page-redirection) 

### Replace the "thankyou" page

1. Open the "[EDS Project]/blocks/form/form.js" file for editing.
1. Change the `thankyou` page in the following line to page of your choice:

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'thankyou';

    ```

    For example,

    ```JavaScript

    window.location.href = form.dataset?.redirect || 'payment';
        
    ```
    
    >[!NOTE]
    >
    > Ensure that a page with the same name exists in your Edge Delivery Services project folder on either Microsoft SharePoint or Google Workspace. If the page does not exist, proceed to create and publish it.  

1. Proceed to check in the updated 'form.js' folder and its underlying files to your Edge Delivery Services project on GitHub. This update ensures that the form now redirects to the updated page as specified.

1. Ensure that the page exists in your EDS project folder and publish it.


### Use website redirects for "thankyou" page redirection

Redirecting a user to another page after form submission can enhance user experience by providing relevant information, confirming actions, and guiding users towards desired outcomes. For example, 

* after a user completes a purchase form, they are redirected to a payment page to complete the transaction securely. 
* upon submitting a registration form for an event or webinar, users are redirected to a confirmation page displaying event details, such as date, time, and location.

To redirect the "thankyou" page to a different page, use the [website redirects](https://www.aem.live/docs/redirects) spreadsheet. 



## See also

{{see-more-forms-eds}}