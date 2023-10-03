---
title: Hoe kunt u revisies van Adaptive Forms maken en beheren die zijn ingesloten of gemaakt op de pagina Sites?
description: Revisie is een mechanisme waarmee revisoren verschillende taken voor adaptieve formulieren kunnen uitvoeren met de stap Taak toewijzen.
feature: Adaptive Forms
hide: true
hidefromtoc: true
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# Revisies maken en beheren voor een adaptief formulier {#review-step-forms-aem-sites-page}

Met de [Stap toewijzen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step) van de AEM werkstroom bekijkt de controleur het verzonden formulier en voert er actie op uit. Voer de volgende stappen uit om het verzonden formulier te bekijken met de taakstap Toewijzen:

1. [Een AEM maken](#create-an-aem-workflow)
1. [De verzendactie van de container van het adaptieve formulier configureren](#configure-submit-action)
1. [Een adaptief formulier verzenden na revisie](#submit-af-after-review)

## Een AEM maken {#create-an-aem-workflow}

1. Open de auteurinstantie in geef wijze uit.
1. Ga naar **[!UICONTROL Tools]** >  **[!UICONTROL Workflow]** >  **[!UICONTROL Models]** > **[!UICONTROL Create]** > **[!UICONTROL Create Model]**
1. Geef de titel van de workflow op en voeg de **[Taak toewijzen]** stap
1. Tikken ![settings_icon](assets/settings_icon.png) op de actiebalk. De **[!UICONTROL Assign Task]** wordt geopend.
1. Openen [!UICONTROL Form and Document] tab en open [!UICONTROL Pre-populated] vervolgkeuzelijst en geef op:

   * Invoergegevensbestand selecteren met
   * Invoerbijlagen selecteren met

   ![Revisiestap](/help/forms/assets/assigntask-review1.gif)

1. Openen **[!UICONTROL Assignee]** tab en open [!UICONTROL Pre-populated] vervolgkeuzelijst en specificeer **[!UICONTROL Assign  options]**:

   ![Revisiestap](/help/forms/assets/review-assignstep.png)

1. Klikken **[!UICONTROL Done]** om de wijzigingen op te slaan

## Verzendhandeling configureren {#configure-submit-action}

Configureer nu de handeling Verzenden van een component Adaptive Form Container op de pagina van de site:

1. Ga naar de pagina van de Site.
1. Tikken ![settings_icon](assets/settings_icon.png) van een container van een adaptief formulier. De **[!UICONTROL Adaptive Form Container]** wordt geopend.
1. Open de **[!UICONTROL Submission]** en geeft **[!UICONTROL Submit Action]** tot [Een AEM-workflow aanroepen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow)

1. Klikken [Gereed] om de instellingen op te slaan.

![indiening tabblad reviewstep](/help/forms/assets/submissiontab-reviewstep.gif)

## Een adaptief formulier verzenden na revisie {#submit-af-after-review}

Het ingediende adaptieve formulier beoordelen en bevestigen:

1. Ga naar [!UICONTROL Tools] >  [!UICONTROL Workflow] >  [!UICONTROL Instances]
1. In Inbox, kunt u zien dat een geval wordt gecreeerd.
1. Selecteer de instantie en klik op [!UICONTROL Open].
1. U ziet nu het verzonden formulier.

De controleur voert verschillende handelingen uit als:

* **Verzenden**: De controleur vult het formulier in en verzendt het voor verdere verwerking.
* **Opslaan**: De controleur slaat het formulier in de huidige staat op zonder het te verzenden.
* **Herstellen**: De controleur wist alle wijzigingen die in het formulier zijn aangebracht en herstelt het formulier in de oorspronkelijke staat.
* **Delegeren**: De controleur draagt de eigendom van het formulier over aan een andere persoon voor verdere actie of controle.
