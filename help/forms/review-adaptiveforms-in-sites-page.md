---
title: Hoe een adaptief formulier ter controle verzenden? Hoe kunt u revisies beheren voor een bepaald adaptief formulier?
description: Revisie is een mechanisme waarmee revisoren verschillende taken voor adaptieve formulieren kunnen uitvoeren met de stap Taak toewijzen.
feature: Adaptive Forms
hide: true
hidefromtoc: true
role: User
source-git-commit: 937bd4653e454beea3111cfc7ef7b4bbc1ace193
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---


# Revisies maken en beheren voor een adaptief formulier {#review-step-forms-aem-sites-page}

Gebruikend [ wijs stap ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/create-form-centric-workflows/aem-forms-workflow-step-reference.html#assign-task-step) van het AEM werkschema toe, herziet de recensent de voorgelegde vorm en voert actie op het uit. Voer de volgende stappen uit om het verzonden formulier te bekijken met de taakstap Toewijzen:

1. [Een AEM maken](#create-an-aem-workflow)
1. [De verzendactie van de container van het adaptieve formulier configureren](#configure-submit-action)
1. [ voorlegt een Aangepast vorm na overzicht ](#submit-af-after-review)

## Een AEM maken {#create-an-aem-workflow}

1. Open de auteurinstantie in geef wijze uit.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** > **[!UICONTROL Create]** > **[!UICONTROL Create Model]**
1. Specificeer de Titel van werkschema en voeg **[toe taakstap]** toewijst
1. Selecteer ![ settings_icon ](assets/settings_icon.png) op de actiebar. Het dialoogvenster **[!UICONTROL Assign Task]** wordt geopend.
1. Open [!UICONTROL Form and Document] en open [!UICONTROL Pre-populated] drop-down en specificeer:

   * Invoergegevensbestand selecteren met
   * Invoerbijlagen selecteren met

   ![ stap van het Overzicht ](/help/forms/assets/assigntask-review1.gif)

1. Open **[!UICONTROL Assignee]** en open [!UICONTROL Pre-populated] drop-down en specificeer **[!UICONTROL Assign  options]**:

   ![ stap van het Overzicht ](/help/forms/assets/review-assignstep.png)

1. Klik op **[!UICONTROL Done]** om de wijzigingen op te slaan.

## Verzendhandeling configureren {#configure-submit-action}

Configureer nu de handeling Verzenden van een component Adaptive Form Container op de pagina van de site:

1. Ga naar de pagina van de Site.
1. Selecteer ![ settings_icon ](assets/settings_icon.png) van een Adaptieve container van de Vorm. Het dialoogvenster **[!UICONTROL Adaptive Form Container]** wordt geopend.
1. Open het **[!UICONTROL Submission]** lusje en specificeer **[!UICONTROL Submit Action]** om [ te roepen een AEM werkschema ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html?lang=en#invoke-an-aem-workflow)

1. Klik [ Gedaan ] om de montages te bewaren.

![ voorlegging tab-reviewstep ](/help/forms/assets/submissiontab-reviewstep.gif)

## Een adaptief formulier verzenden na revisie {#submit-af-after-review}

Het ingediende adaptieve formulier beoordelen en bevestigen:

1. Ga naar [!UICONTROL Tools] > [!UICONTROL Workflow] > [!UICONTROL Instances]
1. In Inbox, kunt u zien dat een geval wordt gecreeerd.
1. Selecteer de instantie en klik op [!UICONTROL Open] .
1. U ziet nu het verzonden formulier.

De controleur voert verschillende handelingen uit als:

* **voorleggen**: De recensent voltooit de vorm en legt het voor verdere verwerking voor.
* **sparen**: De recensent bewaart de vorm in zijn huidige staat zonder het voor te leggen.
* **Terugstellen**: De recensent ontruimt om het even welke veranderingen die aan de vorm worden aangebracht en herstelt het aan zijn originele staat.
* **Afgevaardigde**: De recensent draagt eigendom van de vorm aan een andere persoon voor verdere actie of overzicht over.
