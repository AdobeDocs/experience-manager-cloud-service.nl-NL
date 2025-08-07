---
title: Hoe kunt u revisies in formulieren maken en beheren?
description: Met het revisiemechanisme kunt u revisoren toevoegen en revisoren toestaan opmerkingen toe te voegen aan een formulier.
topic-tags: forms-manager
feature: Adaptive Forms, Foundation Components
exl-id: 378049f8-bf21-4595-819d-ba5fba7023c0
role: User, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# Revisies maken en beheren op formulieren{#creating-and-managing-reviews-to-forms}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor auteur Adaptive Forms die gebruik maakt van stichtingscomponenten. </span>


| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/create-reviews-forms.html?lang=nl-NL) |
| AEM as a Cloud Service | Dit artikel |

## Controleren {#review}

Een revisie is een mechanisme waarmee een of meer revisoren opmerkingen op formulieren kunnen plaatsen.

## Een revisie instellen {#setting-up-a-review}

1. Navigeer naar de browser met formulieren en selecteer een formulier dat u wilt bekijken.
1. Als de Vorm geen overzicht lopend heeft, verschijnt het a **Overzicht van het Begin** ![ aem6forms_review_chat_comment ](assets/aem6forms_review_chat_comment.png) pictogram in de bar van de Actie. Klik het **Overzicht van het Begin** ![ aem6forms_review_chat_comment ](assets/aem6forms_review_chat_comment.png) pictogram.
1. Voer de volgende gegevens in:

   * **Titel**: Verplicht, kan alfanumerieke karakters, koppelteken, en onderstrepingsteken bevatten.
   * **Beschrijving**: Facultatieve, beschrijving van het doel/de inhoud voor overzicht.
   * **Deadline**: Facultatief, de datum waarop de overzicht beëindigt. Als de deadline is verstreken, wordt de taak weergegeven als &#39;Achterstallig&#39;.
   * **Naam van de Recensent**: Een minimum van één is verplicht. Gebruik combodoos om recensenten toe te voegen, typend een naamlijst van alle passende namen; selecteer een naam en klik **toevoegen**. Op de volgende sectie van het **lusje van Revisoren** toont de namen van alle recensenten.

1. Klik het **Begin** om een overzicht te beginnen.

   >[!NOTE]
   >
   >* Beheerders hebben toegang tot alle groepen die aan de formuliergebruikers zijn gekoppeld.
   >* De gebruikersgroep van de dienst is niet beschikbaar aan selectie voor overzicht.

### Handelingen die worden uitgevoerd wanneer een revisie wordt ingesteld {#actions-that-occur-when-a-review-is-set-up}

In deze sectie wordt beschreven wat er gebeurt wanneer een revisie wordt gemaakt of ingesteld.

1. Er wordt een nieuwe revisietaak gemaakt en toegewezen aan de geselecteerde revisor.
1. Aan alle revisoren wordt een controletaak toegewezen. De taak wordt weergegeven in de sectie Meldingen. Een revisor kan op een melding klikken of naar het Postvak In gaan om de taak te bekijken. Een revisor kan op deze knop klikken om de revisietaak te openen, het formulier weer te geven en opmerkingen toe te voegen.

   ![ Waarschuwing van het Bericht van de Recensent ](assets/review-notification-img.png)

   Waarschuwing revisormelding

1. Het opmerkingenvak is beschikbaar voor de revisoren van het formulier. Anderen kunnen de opmerkingen wel lezen, maar niet hun eigen opmerkingen toevoegen.

## Een revisie beheren {#managing-a-review}

>[!NOTE]
>
>* Alleen lopende revisies kunnen worden gewijzigd.
>* Volledige revisies kunnen niet worden gewijzigd.

1. Navigeer naar het tabblad Formulieren en selecteer een formulier.

1. Als een vorm een overzicht lopend heeft en u initiator van het overzicht bent, a **leidt het pictogram van het Overzicht** ![ aem6forms_review_chat_comment ](assets/aem6forms_review_chat_comment.png) in de actiebar. Alleen de aanvrager van de revisie kan de revisie beheren (Bijwerken/beëindigen).

   Klik **leiden het Overzicht** ![ aem6forms_review_chat_comment ](assets/aem6forms_review_chat_comment.png) pictogram.

   Voor andere gebruikers dan de aanvrager is het pictogram Revisie beheren uitgeschakeld.

1. Nu krijgt u een scherm dat informatie toont:

   * **naam van het Overzicht**: Kan niet worden uitgegeven.

   * **beschrijving van het Overzicht**: Beschikbaar voor het uitgeven.

   * **deadline van het Overzicht**: Beschikbaar voor het uitgeven. U kunt de deadline wijzigen in elke datum en tijd na de huidige datum en tijd.

   * **Recensenten**: Beschikbaar voor het uitgeven. U kunt revisoren toevoegen of verwijderen. Als een taak te laat is, kunt u revisoren pas toevoegen nadat de deadline is verlengd na de huidige datum.

1. Om de revisie te beëindigen, klik **Eind**.

### Handelingen die worden uitgevoerd wanneer een revisie wordt gewijzigd {#actions-that-occur-when-a-review-is-modified}

Deze sectie beschrijft wat op **Update/Eind van het Overzicht** gebeurt:

1. Als de revisiebeschrijving wordt gewijzigd, worden de bijbehorende taak van de revisoren en de aanvrager bijgewerkt.
1. Als de deadline van de revisie wordt gewijzigd, wordt de bijbehorende taak voor de revisoren bijgewerkt met de nieuwe datum.

1. Als een revisor wordt verwijderd:

   ![ Verwijderend een recensent ](assets/removeduser.png)

   Een revisor verwijderen

   1. Als onvolledig, wordt de toegewezen taak geëindigd.
   1. De revisor kan geen opmerkingen meer toevoegen aan het formulier.

1. Als een controleur wordt toegevoegd:

   ![ Toevoegend een recensent ](assets/addedreviewer.png)

   Een revisor toevoegen

   1. Er wordt een revisietaak gemaakt en toegewezen aan de nieuwe revisor.
   1. De zojuist toegevoegde controleur kan opmerkingen over het formulier toevoegen.

1. Wanneer een revisie wordt beëindigd:

   1. **Recensenten**: Voor elke recensent, wordt de onvolledige taak met betrekking tot het overzicht geëindigd. De taak wordt niet meer weergegeven als &#39;In behandeling&#39; in de sectie Meldingen van de controleur.
   1. **Initiator**: De taak die aan de initiatiefnemer van het Overzicht wordt toegewezen is duidelijk volledig. De taak wordt verwijderd uit de sectie Melding van de revisieaanvrager.
   1. **allen**: De revisie verschijnt in de Vorige sectie van Revisies. Er kunnen geen verdere opmerkingen worden toegevoegd.

   ![ volledige overzicht ](assets/review-complete-imgg.png)
