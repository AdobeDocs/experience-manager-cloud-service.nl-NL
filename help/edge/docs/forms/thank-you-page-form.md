---
title: Een aangepast bedankbericht weergeven na het verzenden van het formulier
description: Leer hoe u pagina's voor bedankt en omleiding voor Forms Block configureert om de gebruikerservaring te optimaliseren en gebruikersreizen te stroomlijnen.
feature: Edge Delivery Services
exl-id: e6c66b22-dc52-49e3-a920-059adb5be22f
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---

# Een aangepast bedankbericht weergeven na het verzenden van het formulier

Nadat een gebruiker een formulier heeft verzonden, is het van cruciaal belang dat u een probleemloze ervaring opdoet via een bedankbericht. Het bevestigt niet alleen een succesvolle indiening, maar vergroot ook de tevredenheid van de gebruikers en begeleidt hen verder op hun reis.

- **Dank u bericht**: Een dank u bericht is een hoeksteen van gebruikerservaring, die geruststelling aanbiedt en belangrijke informatie overbrengt terwijl het versterken van merkidentiteit. Het dient als directe erkenning van de actie van de gebruiker, die een gevoel van voltooiing en tevredenheid bevordert.

- **opnieuw richten**: Een omleiding speelt een centrale rol in het sturen van gebruikers naar relevante bestemmingen, het optimaliseren van overeenkomst, en uiteindelijk het verhogen van omzettingspercentages. Door gebruikers naadloos naar de volgende stap op hun reis te leiden, zorgt een omleiding voor een vloeiende navigatie. U kunt bijvoorbeeld de gebruiker omleiden naar de pagina met betalingen nadat u de eerste gegevens hebt verzameld.

Het standaardgedrag van Adaptive Forms Block is om het volgende bedankbericht bij verzending weer te geven. Het bericht wordt boven aan het formulier weergegeven wanneer het formulier is verzonden.

![&#x200B; gebrek dank u bericht &#x200B;](/help/edge/assets/thank-you-message.png)

U hebt echter de flexibiliteit om deze ervaring af te stemmen op uw specifieke behoeften. U kunt onder andere de volgende opties kiezen:

- Een aangepast bedankbericht weergeven na het verzenden van het formulier
- Gebruikers doorsturen naar een andere pagina na verzending voor verdere actie

>[!NOTE]
>
> U kunt naar het volgende [&#x200B; onderzoeksspreadsheet &#x200B;](/help/edge/docs/forms/assets/enquiry.xlsx) verwijzen om te passen dankt u bericht volgens uw vereisten.

## Een aangepast bedankbericht configureren

Als u een gepersonaliseerd bedankbericht wilt weergeven wanneer het formulier is verzonden, kunt u het werkblad zo configureren dat het wordt weergegeven.

Voer de onderstaande stappen uit om een aangepast bedankbericht voor uw Adaptive Forms Block te configureren:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.
1. Voeg een aangepast bedankbericht toe in de kolom `value` voor het veldtype `submit` in de spreadsheet.

   ![&#x200B; Aangepast Thanku bericht &#x200B;](/help/edge/docs/forms/assets/thankyou-custommessage.png)

   Voeg bijvoorbeeld het bericht `Submission Successful!` in de kolom `value` toe voor het veldtype `submit` .

1. Voorproef en publiceer het blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![&#x200B; Aangepast Thanku bericht &#x200B;](/help/edge/docs/forms/assets/customized-thank-you-message.png)

## Gebruikers omleiden naar een andere pagina na verzending

Het omleiden van een gebruiker naar een andere pagina na het verzenden van het formulier kan de gebruikerservaring verbeteren door relevante informatie op te geven, acties te bevestigen en gebruikers naar de gewenste resultaten te leiden. Bijvoorbeeld:

- nadat een gebruiker een inkoopformulier heeft ingevuld, wordt hij of zij omgeleid naar een betalingspagina om de transactie veilig te voltooien.
- wanneer een registratieformulier voor een gebeurtenis of webinar wordt verzonden, worden gebruikers omgeleid naar een bevestigingspagina met gebeurtenisdetails, zoals datum, tijd en locatie.

Voer de volgende stappen uit om gebruikers om te leiden naar een andere pagina:

1. Ga naar uw Edge Deliver-projectmap op Microsoft SharePoint of Google Workspace en open uw spreadsheet.
1. Plak de URL in de kolom `value` voor het veldtype `submit` in het spreadsheet om de gebruiker om te leiden wanneer het formulier is verzonden.
Om de pagina aan een verschillende pagina om te leiden, gebruik [&#x200B; de Documentatie van Edge Delivery &#x200B;](https://www.aem.live/docs/) pagina URL.

   ![&#x200B; Thankyou redirect URL &#x200B;](/help/edge/docs/forms/assets/thankyou-redirecturl.png)

1. Voorproef en publiceer het blad gebruikend [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/developer/tutorial#preview-and-publish-your-content).

   ![&#x200B; Redirect het bericht van Thanku &#x200B;](/help/edge/docs/forms/assets/thankyou-redirectpage.gif)

U kunt ook een nieuw documentbestand maken en de voorbeeld-URL toevoegen in de kolom `value` voor het veldtype `submit` .

Nadat een gebruiker een formulier heeft verzonden, is het belangrijk dat u een duidelijke bedankboodschap ontvangt. Het bevestigt dat de verzending is gelukt en verbetert de tevredenheid van de gebruiker.

