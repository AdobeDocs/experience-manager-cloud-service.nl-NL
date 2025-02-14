---
title: Handelingen verzenden
description: Configureer Verzendhandelingen voor adaptief formulier.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: beee9be7-8215-496b-9fb9-61fba000a055
source-git-commit: da2f673319dd5cec764408b4517698a9d39031bb
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---

# Handeling Adaptief verzenden van formulier

Met een handeling Verzenden geeft u de bestemming op voor de gegevens die via een adaptief formulier worden verzameld. Het verzendingsproces begint wanneer de gebruiker op de knop **[!UICONTROL Submit]** op het formulier klikt. AEM Forms biedt twee soorten verzendacties die hieronder worden beschreven. U kunt aangepaste verzendacties maken en gebruiken om aan uw specifieke behoeften te voldoen. De verzendacties buiten de box zijn:

<!--To define a Submit Action for an Adaptive Form, you use the Properties dialog of the **Adaptive Form block** in the **Editor**-->

* [Verzenden naar REST-eindpunt](#rest-endpoint-submission-ue)
* [E-mail verzenden](#email-submission-ue)


### Verzenden naar REST-eindpunt {#rest-endpoint-submission-ue}

Verzenden naar REST Endpoint-actie wordt gebruikt om de verzonden formuliergegevens naar een opgegeven REST-eindpunt te verzenden. Het eindpunt kan tot of een interne server behoren waar de vorm wordt ontvangen of tot een externe server door een relatieve weg of een absolute weg te gebruiken. Als u gegevens wilt verzenden naar de AEM-server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM-server. Bijvoorbeeld `/content/forms/af/SampleForm.html` . Gebruik het absolute pad om gegevens naar een andere server te verzenden.

<!--Configuring the Submit Action to REST Endpoint for Adaptive Forms offers several benefits such as:  
* It facilitates seamless integration of form data with external systems and services via RESTful APIs.  
* Offers flexibility in managing data submissions from Adaptive Forms, accommodating dynamic and complex data structures.  
* Allows dynamic mapping of form fields to parameters within the REST endpoint URL, enabling adaptable and customizable data submissions.
-->



Om een REST eindpunt te vormen:

1. Open het adaptieve formulier in **[!UICONTROL Editor]** .
1. Selecteer **[!UICONTROL Adaptive Form Block]** .
1. Klik de eigenschappen ![ eigenschappen ](/help/forms/assets/Smock_Properties_18_N.svg) pictogram.
1. Selecteer de **[!UICONTROL Submit to a REST endpoint]** in de vervolgkeuzelijst **[!UICONTROL Submit Action]** .
1. Geef de URL van het REST-eindpunt op.
1. U kunt **POST verzoek** ook toelaten en URL verstrekken om het verzoek te posten.

![ laat postverzoek voor adaptieve vormen ](/help/forms/assets/enable-post-request-ue.png) toe

>[!NOTE]
>
> * Als u gegevens naar een interne server wilt posten, geeft u het pad van de bron op. De gegevens worden naar het pad van de bron gepost. Bijvoorbeeld `/content/restEndPoint` . Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.
> * Geef een URL op om gegevens naar een externe server te posten. De opmaak van de URL is `https://host:port/path_to_rest_end_point` . Zorg ervoor dat u de weg vormt om het POST- verzoek anoniem te behandelen.

### E-mail verzenden {#email-submission-ue}

Met Actie voor verzenden van e-mail kunt u een e-mail verzenden naar een of meer ontvangers nadat het formulier is verzonden. Met de configuratie E-mail verzenden kunt u een e-mail maken waarin formuliergegevens in een vooraf gedefinieerde indeling kunnen worden opgenomen. Neem bijvoorbeeld de volgende sjabloon waar de naam van de klant, het verzendadres, de naam van de staat en de postcode worden opgehaald uit de verzonden formuliergegevens. [ Leer meer over E-mailMalplaatjes in Aanpassings Forms ](/help/forms/html-email-templates-in-adaptive-forms.md). De volgende voordelen hebben het configureren van een adaptief formulier met de actie E-mail verzenden:

1. Hiermee kunt u snel communiceren terwijl formuliergegevens rechtstreeks naar aangewezen e-mailontvangers worden verzonden.
1. Het helpt de workflow te stroomlijnen door formulierverzendingen rechtstreeks te integreren in e-mailmeldingen.
1. Het helpt organisaties de e-mailinhoud aanpassen, zodat het geschikt wordt gemaakt voor specifieke communicatiebehoeften.

![ de Aanpassings eigenschappen van de Vorm in Universele Redacteur ](/help/forms/assets/submit-actions-ue.png)


Een verzendactie configureren als een e-mail voor het verzenden van het formulier:

1. Open uw AanpassingsVorm in **Redacteur**.
1. Selecteer de **[!UICONTROL Adaptive Form Block]** .
1. Klik de eigenschappen ![ eigenschappen ](/help/forms/assets/Smock_Properties_18_N.svg) pictogram.
1. Selecteer de optie **[!UICONTROL Send email]** in de vervolgkeuzelijst **[!UICONTROL Submit Action]** .
1. Nadat u de optie E-mail verzenden hebt geselecteerd, kunt u de volgende eigenschappen configureren, zoals in de onderstaande afbeelding wordt getoond.

<table>
  <thead>
    <tr>
      <th>Afbeelding</th>
      <th>Eigenschap</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
    <tr>
    <td rowspan="7"><img src="/help/forms/assets/email-config-ue.png" alt="E-mailconfiguratie"></td> 
    <td><b>Van</td>
    <td>Geef het e-mailadres van de afzender op.</td>
    </tr>
    <tr>
      <td><b>Naar</td>
      <td>Geef de primaire ontvangers van het e-mailbericht op en u kunt meerdere e-mailadressen toevoegen, gescheiden door komma's.</td>
    </tr>
    <tr>
      <td><b>CC</td>
      <td>Geef de ontvangers op die een koolstofkopie (CC) van het e-mailbericht moeten ontvangen.</td>
    </tr>
    <tr>
      <td><b>BCC</td>
      <td>Geef de ontvangers op die een BCC (blind carbon copy) van de e-mail moeten ontvangen.</td>
    </tr>
    <tr>
      <td><b>Onderwerp</td>
      <td>Geef de onderwerpregel van de e-mail op.</td>
    </tr>
    <tr>
      <td><b>Externe sjabloon gebruiken</td>
      <td>Hiermee kunt u een externe e-mailsjabloon gebruiken om de e-mailinhoud op te maken. Geef de URL of het pad naar de externe sjabloon op om een vooraf ontworpen e-mailsjabloon die in uw AEM Assets-map wordt gehost, te integreren.</td>
    </tr>
    <tr>
      <td><b>Bijlage opnemen</td>
      <td>Hiermee geeft u aan of de verzonden formuliergegevens een bijlage moeten bevatten die via het formulier in de e-mail is verzonden. Ondersteunde indelingen voor bijlagen zijn PDF, XML en JSON.</td>
    </tr>
  </tbody>
</table>






<!--
        
        * **From**: The email address of the sender.
        * **To**: Specify the primary recipients of the email, multiple email addresses can be added, separated by commas.
        * **CC**: Specify the recipients who should receive a carbon copy (CC) of the email.
        * **BCC**: Specify the recipients who should receive a blind carbon copy (BCC) of the email.
        * **Subject**: Specify the subject line of the email.
        * **Use External Template**: Enables the use of an external email template for formatting the email content. Provide the URL or path to the External template path to integrate a pre-designed email template hosted in your AEM Assets folder.
        * **Include Attachment**: Specifies whether the submitted form data should include an attachment submitted through the form in the email.

    {width=50%,height=50%}![Enable post request for adaptive forms](/help/forms/assets/email-config-ue.png)

-->

## Een aangepast bedankbericht weergeven bij het verzenden van een adaptief formulier {#submit-action-message-ue}

Met de optie Verzenden kunt u een bericht Actie verzenden configureren bij het verzenden van een adaptief formulier. Zo configureert u een bericht Actie verzenden voor het formulier:

1. Open uw AanpassingsVorm in **Redacteur**.
1. Selecteer de **[!UICONTROL Adaptive Form Block]** .
1. Klik de eigenschappen ![ eigenschappen ](/help/forms/assets/Smock_Properties_18_N.svg) pictogram.
1. Bij klikken ziet u de volgende optie:
   * **[!UICONTROL On Submit]**: Bij Verzenden kunt u een bericht aanpassen dat wordt weergegeven wanneer een formulier wordt verzonden. Standaard wordt een aangepast bericht &quot;Bedankt voor het verzenden van het formulier&quot; weergegeven aan de gebruiker wanneer een formulier is verzonden.
U kunt ook het Dank u bericht op vormvoorlegging aanpassen, door de optie aan **[!UICONTROL Show message]** te selecteren, en uw bericht toe te voegen/uit te geven in de Rich Text **Redacteur**.


## Zie ook

{{see-more-forms-eds}}
