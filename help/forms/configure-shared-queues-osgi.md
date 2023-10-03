---
title: Hoe te om gedeelde rijen te vormen?
description: Leer hoe u gedeelde wachtrijen kunt gebruiken voor op Forms gerichte workflows op [!DNL AEM Forms] over OSGi.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 1%

---


# Deel en verzoek toegang tot Inbox punten van een gebruiker {#share-and-request-access}

Een wachtrij is een lijst met items in AEM Postvak IN van een gebruiker. Dit kunnen punten zijn die aan een gebruiker of punten worden toegewezen aan de groep wordt gedeeld een gebruiker is een lid van. U hebt toegang tot uw Postvak IN om het Postvak IN-item weer te geven en actie te ondernemen. Deel bijvoorbeeld een item met een andere gebruiker.

U kunt uw Postvak IN-items ook met een andere gebruiker delen. Zodra een andere gebruiker toegang heeft tot uw Inbox-items, kan de gebruiker een claim indienen en de juiste actie ondernemen voor gedeelde items. Op dezelfde manier kunt u andere gebruikers om toegang tot Inbox-items verzoeken.

## Voorwaarden {#pre-requisites}

De het programma geopende gebruiker moet een lid van zijn [!DNL `workflow-users`] groep. De gebruiker kan punten delen of om toegang tot punten slechts van de gebruikers verzoeken de het programma geopende gebruiker heeft gelezen toestemmingen op of slechts van de gebruikers die openbare profiel hebben toegelaten.

## Eén of alle items van uw Postvak IN delen met een andere gebruiker

Met AEM Postvak IN kunt u een enkele of alle items in uw postvak IN delen met een andere gebruiker.

### Alle postvakitems delen

Voer de volgende stappen uit om alle items in een Postvak IN te delen met een andere gebruiker:

1. Meld u aan bij uw AEM. Tik op de knop ![Inbox](assets/bell.svg) pictogram en tik **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Tik op de knop ![Kiezer weergeven](assets/viewlist.svg) of ![Kiezer weergeven](assets/calendar.svg) pictogram naast **[!UICONTROL Create]** knop en tik **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Open de **[!UICONTROL Share]** in het dialoogvenster Instellingen.
1. Voer de naam van een gebruiker in het dialoogvenster **[!UICONTROL Grant access of your Inbox items]** tekstvak en tikken **[!UICONTROL Grant]**. Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot je objecten worden weergegeven onder de **Gebruikersnaam** sectie.
1. Tik op **[!UICONTROL Save]**.

>[!NOTE]
>
>(Alleen voor workflowitems die op Forms zijn gericht) Schakel de optie **[Toestaan dat de ontvanger deelt via Postvak IN](aem-forms-workflow-step-reference.md)** van de **Taak toewijzen** in de workflow. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

### Afzonderlijke items delen

Voer de volgende stappen uit om een Inbox-item met een andere gebruiker te delen:

1. Meld u aan bij uw AEM. Tik op de knop ![Inbox](assets/bell.svg) pictogram en tik **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer een item en tik op **[!UICONTROL Share]**. Er wordt een dialoogvenster weergegeven.
1. Typ de naam van een gebruiker in het tekstvak Gebruikers toevoegen om dit item te delen en tik op **[!UICONTROL Add]**. Herhaal deze stap om meer gebruikers toe te voegen. Alle gebruikers met toegang tot je objecten worden weergegeven onder de **[!UICONTROL Username]** sectie.
1. Tik op **[!UICONTROL Save]**.


>[!NOTE]
>
>(Alleen voor workflowitems die op Forms zijn gericht) Schakel de optie **[Toestaan dat de ontvanger expliciet in Postvak IN deelt](aem-forms-workflow-step-reference.md)** van de **Taak toewijzen** in de workflow. Alleen items waarvoor de bovenstaande optie is ingeschakeld, worden weergegeven aan andere gebruikers.

## Toegang aanvragen tot postvakken {#request-access}

U kunt toegang tot de items in het Postvak IN van een andere gebruiker aanvragen. Zodra de toegang wordt verleend, kunt u bekijken, eisen, en aangewezen acties op gedeelde punten nemen. Voer de volgende stappen uit om toegang tot Inbox-items van een andere gebruiker aan te vragen:

1. Meld u aan bij uw AEM. Tik op de knop ![Kiezer weergeven](assets/bell.svg) pictogram en tik **[!UICONTROL View All]**.
1. Tik op de knop ![Kiezer weergeven](assets/viewlist.svg) of ![Kiezer weergeven](assets/calendar.svg) pictogram naast **[!UICONTROL Create]** knop en tik **[!UICONTROL Settings]**. Het dialoogvenster Instellingen wordt weergegeven.
1. Voer de naam van een gebruiker in het dialoogvenster **[!UICONTROL Request access to Inbox items of the user]** tekstvak en tikken **[!UICONTROL Request]**. Een verzoek wordt verzonden naar de gebruiker en de status van het verzoek wordt getoond tegen de naam van de gebruiker. Herhaal deze stap om meer gebruikers toe te voegen.
1. Tik op **[!UICONTROL Save]**. Het verzoek wordt verzonden als Inbox punt aan de gebruikers. De gebruiker kan het item selecteren en op Goedkeuren of Afwijzen tikken om de toegang te verlenen of af te wijzen.


## Items claimen die door andere gebruikers worden gedeeld {#claim-items}

U kunt pas aan een gedeeld item beginnen te werken nadat u dit hebt opgeëist. Hiermee voorkomt u dat meerdere gebruikers aan één item werken. Voer de volgende stappen uit om een object te claimen:

1. Meld u aan bij uw AEM. Tik op het Postvak IN ![Inbox](assets/bell.svg) pictogram en tik **[!UICONTROL View All]**.
1. Tik op de knop ![Alleen inhoud](assets/railleft.svg) om de filterkiezer te openen.
1. Tik op de knop **[!UICONTROL Select Assignee]** vervolgkeuzelijst om gebruikers weer te geven en te selecteren die hun Postvak IN-items met u hebben gedeeld.
1. Selecteer een item en tik op **[!UICONTROL Claim]**. Het item wordt toegevoegd aan je Postvak IN.

## Opgevraagde items vrijgeven {#release-items}

U kunt alleen aan een gedeeld item werken nadat u dit hebt opgeëist. Andere gebruikers kunnen een door u geclaimd object niet zien of bewerken. Als u niet aan een punt kunt blijven werken, kunt u het terug naar de pool vrijgeven.   Nadat je het object hebt uitgebracht, kunnen anderen een claim indienen en aan het object werken:

Voer de volgende stappen uit om een item vrij te geven:

1. Meld u aan bij uw AEM. Tik op het Postvak IN ![Inbox](assets/bell.svg) pictogram en tik **[!UICONTROL View All]**. Er wordt een lijst met je postvak-items weergegeven.
1. Selecteer het item dat u wilt loslaten en tikken **[!UICONTROL UnClaim]**. Het item wordt weer aan de pool toegevoegd. Anderen kunnen nu een claim indienen op het object.

## Beperkingen {#limitations}

* Het delen van items met een groep wordt niet ondersteund.
* Het delen van projecttaken wordt niet ondersteund.
