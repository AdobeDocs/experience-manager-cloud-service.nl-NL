---
title: Hartelijk dank voor de pagina configureren of formulier omleiden na verzending
description: Leer hoe u pagina's voor bedankt en omleiding voor Forms Block configureert om de gebruikerservaring te optimaliseren en gebruikersreizen te stroomlijnen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: d6b1048c44022da47a9d7443f564a2ff9d1802cf
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---


# De pagina Bedankt of het formulier omleiden na verzending weergeven

Nadat een gebruiker een formulier heeft verzonden, is het van cruciaal belang dat u een naadloze ervaring hebt dankzij een pagina voor bedankt of een omleiding. Deze elementen bevestigen niet alleen een geslaagde indiening, maar verhogen ook de tevredenheid van de gebruikers en begeleiden hen verder op hun reis.

* **Dankbriefje**: Een pagina met dank is een hoeksteen van de gebruikerservaring, die geruststelling biedt en belangrijke informatie overbrengt en tegelijkertijd de merkidentiteit versterkt. Het dient als directe erkenning van de actie van de gebruiker, die een gevoel van voltooiing en tevredenheid bevordert.

* **Omleiden**: Een omleiding speelt een centrale rol bij het sturen van gebruikers naar relevante bestemmingen, het optimaliseren van betrokkenheid en het uiteindelijk verhogen van de omrekeningskoersen. Door gebruikers naadloos naar de volgende stap op hun reis te leiden, zorgt een omleiding voor een vloeiende navigatie. Bijvoorbeeld, het opnieuw richten van gebruiker aan betalingspagina na het verzamelen van aanvankelijke details.

In het blok Adaptive Forms is het standaardgedrag dat u een pagina voor bedankt weergeeft. U hebt echter de flexibiliteit om deze ervaring af te stemmen op uw specifieke behoeften. U kunt onder andere de volgende opties kiezen:

* [De pagina en het bericht voor bedankt configureren zodat deze aansluiten op uw merk en communicatiedoelstellingen](#configuring-the-thank-you-page-and-message)
* [Na verzending gebruikers omleiden naar een andere pagina voor verdere actie](#redirect-users-to-another-page-post-submission)

## De pagina en het bericht voor bedankt configureren

Het standaardgedrag van het blok Adaptive Forms is om de pagina &quot;danku&quot; bij verzending weer te geven. Voer de volgende stappen uit om de pagina &quot;thanku&quot; voor uw Adaptive Forms-blok te configureren:

1. Open uw AEM Edge Delivery-projectmap op Microsoft SharePoint of Google Workspace.
1. Maak een Microsoft Word- of Google Docs-bestand met de naam &quot;thankyou&quot; in de projectmap.
1. Voeg uw dank toe aan het bestand &quot;dankuwel&quot;. </br>

   ![Voorbeeld van een pagina voor bedankt](/help/edge/assets/sample-thankyou-page.png)

1. Gebruik AEM Sidekick om een voorvertoning van het &quot;thankyou&quot;-bestand te bekijken en dit te publiceren.

In het blok Adaptive Forms wordt de pagina &quot;Dankuwel&quot; weergegeven bij het verzenden van het formulier.

## Gebruikers omleiden naar een andere pagina na verzending

Standaard leidt het blok Adaptive Forms de gebruikers om naar de pagina &quot;thanku&quot;. Als u gebruikers wilt omleiden naar een andere pagina dan de standaardpagina &quot;Thanku&quot;, hebt u twee opties:

* [De pagina &quot;Dankuwel&quot; vervangen door een andere pagina](#replace-the-existing-thankyou-page)
* [Omleiding van website gebruiken voor paginaomleiding &quot;thankyou&quot;](#use-website-redirects-for-thankyou-page-redirection)

### De pagina &quot;Thankyou&quot; vervangen

1. Open &quot;[EDS-project]/blocks/form/form.js&quot;.
1. Wijzig de `thankyou` pagina in de volgende regel naar keuze:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'thankyou';
   ```

   Bijvoorbeeld:

   ```JavaScript
   window.location.href = form.dataset?.redirect || 'payment';
   ```

   >[!NOTE]
   >
   > Zorg ervoor dat er een pagina met dezelfde naam aanwezig is in uw Edge Delivery Service-projectmap op de Microsoft SharePoint- of Google Workspace. Als de pagina niet bestaat, gaat u verder en publiceert u deze.

1. Ga aan controle in de bijgewerkte omslag &#39;form.js&#39; en zijn onderliggende dossiers aan uw project van de Dienst van de Levering van de Rand op GitHub te werk. Deze update zorgt ervoor dat het formulier nu naar de opgegeven bijgewerkte pagina wordt omgeleid.

1. Zorg ervoor dat de pagina in uw EDS-projectmap bestaat en publiceer deze.


### Omleiding van website gebruiken voor paginaomleiding &quot;thankyou&quot;

Het omleiden van een gebruiker naar een andere pagina na het verzenden van het formulier kan de gebruikerservaring verbeteren door relevante informatie op te geven, acties te bevestigen en gebruikers naar de gewenste resultaten te leiden. Bijvoorbeeld:

* nadat een gebruiker een inkoopformulier heeft ingevuld, wordt hij of zij omgeleid naar een betalingspagina om de transactie veilig te voltooien.
* wanneer een registratieformulier voor een gebeurtenis of webinar wordt verzonden, worden gebruikers omgeleid naar een bevestigingspagina met gebeurtenisdetails, zoals datum, tijd en locatie.

Als u de pagina &quot;bedankt&quot; wilt omleiden naar een andere pagina, gebruikt u de [omleidingen van website](https://www.aem.live/docs/redirects) spreadsheet.


## Meer weergeven

* [Formuliercomponenten](/help/edge/docs/forms/form-components.md)
* [Eigenschappen van formulierveld](/help/edge/docs/forms/eds-form-field-properties)
* [Een formulier maken en een voorbeeld ervan bekijken](/help/edge/docs/forms/create-forms.md)
* [Formulier verzenden van gegevens inschakelen](/help/edge/docs/forms/submit-forms.md)
* [Een formulier publiceren naar sitepagina](/help/edge/docs/forms/publish-eds-forms.md)
* [Validaties toevoegen aan formuliervelden](/help/edge/docs/forms/validate-forms.md)
* [Thema&#39;s en vormstijl wijzigen](/help/edge/docs/forms/style-theme-forms.md)
