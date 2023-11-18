---
title: Hoe beheer ik formulieren, toepassingen en taken in het AEM Inbox?
description: Met AEM Inbox kunt u op Forms gerichte workflows starten door toepassingen in te dienen en taken te beheren.
uuid: c6c0d8ea-743f-4852-99d1-69fd50a0994e
contentOwner: vishgupt
topic-tags: document_services, publish
discoiquuid: dd11fd83-3df1-4727-8340-8c5426812823
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '1130'
ht-degree: 0%

---


# Forms-toepassingen en -taken beheren in AEM Postvak In{#manage-forms-applications-and-tasks-in-aem-inbox}

Een van de vele manieren om een Forms-centric workflow te starten of activeren is via toepassingen in AEM Inbox. U moet een workflowtoepassing maken om een Forms Workflow als toepassing beschikbaar te maken in Inbox. Ga voor meer informatie over workflowtoepassingen en andere manieren om Forms-workflows te starten naar [Een Forms-centric workflow starten op OSGi](aem-forms-workflow.md#launch).

Daarnaast consolideert AEM Inbox meldingen en taken van verschillende AEM, waaronder Forms-workflows. Wanneer een Forms Workflow die een Assign taakstap bevat wordt teweeggebracht, is de bijbehorende toepassing vermeld als taak in Inbox van de ontvanger. Als de toegewezen persoon een groep is, wordt de taak in het Postvak In van alle groepsleden weergegeven totdat een persoon de taak aanvraagt of delegeert.

De gebruikersinterface van Inbox verstrekt lijst en kalendermeningen om taken te bekijken. U kunt ook de weergave-instellingen configureren. U kunt taken filteren op basis van verschillende parameters. Zie voor meer informatie over weergave en filters [Uw Postvak IN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html#inbox-in-the-header).

Samenvattend kunt u met Inbox een toepassing maken en toegewezen taken beheren.

>[!NOTE]
>
>U moet lid zijn van de [!DNL workflow-users] groep die AEM Postvak IN moet kunnen gebruiken.

## Toepassing maken {#create-application}

1. Ga naar AEM Postvak IN op https://&#39;[server]:[poort]&#39;/aem/inbox.
1. Tik in de gebruikersinterface van het Postvak IN op **[!UICONTROL Create > Application]**. De pagina Selecteer toepassing wordt weergegeven.
1. Selecteer een toepassing en klik op **[!UICONTROL Create]**. Het adaptieve formulier dat aan de toepassing is gekoppeld, wordt geopend. Vul de gegevens in het adaptieve formulier in en tik op **[!UICONTROL Submit]**. De bijbehorende workflow wordt gestart en er wordt een taak gemaakt in het Postvak In van de ontvanger.

## Taken beheren {#manage-tasks}

Als een Forms-workflowtrigger wordt geactiveerd en u bent een toegewezen persoon of onderdeel van de groep waaraan u bent toegewezen, wordt een taak weergegeven in uw Postvak In. U kunt taakdetails bekijken en beschikbare acties op de taak van binnen Inbox uitvoeren.

### Vorderingen of gedelegeerde taken {#claim-or-delegate-tasks}

De taken die aan een groep worden toegewezen verschijnen in Inbox van alle groepsleden. Om het even welk groepslid kan die taak beweren of het aan een ander groepslid delegeren. Daartoe:

1. Tik om de miniatuur van de taak te selecteren. Opties voor het openen of delegeren van de taak worden bovenaan weergegeven.

   ![selecteren-taak](assets/select-task.png)

1. Voer een van de volgende handelingen uit:

   * Tik op **[!UICONTROL Delegate]**. Het dialoogvenster Item delegeren wordt geopend. Selecteer een gebruiker, voeg desgewenst een opmerking toe en tik op **[!UICONTROL OK]**.

   ![gedelegeerde](assets/delegate.png)

   * Tik op **[!UICONTROL Open]**. Het dialoogvenster Toewijzen aan zelf wordt geopend. Tikken **[!UICONTROL Proceed]** om de taak op te eisen. De geclaimde taak wordt met u weergegeven als de toegewezen persoon in uw Postvak IN.

   ![vordering](assets/claim.png)

### Details weergeven en handelingen uitvoeren voor taken {#view-details-and-perform-actions-on-tasks}

Wanneer u een taak opent, kunt u taakdetails bekijken en beschikbare acties uitvoeren. De acties beschikbaar voor een taak worden bepaald in de Assign taakstap van de bijbehorende Forms Workflow.

1. Tik om de miniatuur van de taak te selecteren. Opties voor het openen of delegeren van de geselecteerde taak worden bovenaan weergegeven.
1. Selecteren **Openen** om taakdetails en beschikbare acties te bekijken. De gedetailleerde taakweergave wordt geopend. In deze weergave kunt u taakdetails weergeven en op een taak reageren.

   >[!NOTE]
   >
   >Als een taak aan een groep wordt toegewezen, moet u beweren het in gedetailleerde mening kan openen.

![taakdetails](assets/task-details.png)

De gedetailleerde taakmening omvat de volgende secties:

* Taakdetails
* Formulier
* Workflowdetails
* Werkbalk Handelingen

#### Taakdetails {#task-details}

In de sectie Taakdetails wordt informatie over de taak weergegeven. De weergegeven informatie is afhankelijk van de configuratie-instellingen van de [Taakstap toewijzen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem) in de workflow. In het bovenstaande voorbeeld worden de beschrijving, de status, de begindatum en de workflow weergegeven die voor de taak worden gebruikt. U kunt ook een bestand aan de taak koppelen.

#### Formulier {#form}

Op het tabblad Formulier in het hoofdinhoudsgebied worden het verzonden formulier en eventuele bijlagen op veldniveau weergegeven.

#### Workflowdetails {#workflow-details}

Het tabblad Workflowdetails bovenaan geeft de voortgang van de taak in verschillende fasen van de workflow weer. Het toont voltooide, huidige, en hangende stadia voor de taak. De fasen van een workflow worden gedefinieerd in het dialoogvenster [Taakstap toewijzen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem) van de bijbehorende workflow.

Bovendien geeft het tabblad de taakgeschiedenis weer voor elk voltooid werkgebied in de workflow. U kunt tikken **[!UICONTROL View Details]** voor een voltooide fase om details over die fase te kennen. Er worden opmerkingen, formulier- en taakbijlagen, status, begin- en einddatums enzovoort over de taak weergegeven.

![workflowdetails](assets/workflow-details.png)

#### Werkbalk Handelingen {#actions-toolbar}

Op de werkbalk Handelingen staan alle beschikbare opties voor de taak. Terwijl sparen, het Terugstellen, en de Delegatie standaardacties zijn, worden andere beschikbare acties gevormd in [Taakstap toewijzen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem). In het bovenstaande voorbeeld worden Goedkeuren en Afwijzen geconfigureerd in de workflow.

Als u de taak uitvoert, gaat deze verder in de workflow.

### Voltooide taken weergeven {#view-completed-tasks}

AEM In Postvak In worden alleen actieve taken weergegeven. Voltooide taken worden niet in de lijst weergegeven. U kunt echter Inbox-filters gebruiken om taken te filteren op basis van verschillende parameters, zoals taaktype, status, begin- en einddatum. Voltooide taken weergeven:

1. Tik in AEM Postvak IN ![aan de zijkant schakelen1](assets/toggle-side-panel1.png) om de filterkiezer te openen.
1. Tikken **[!UICONTROL Task Status]** accordeon en selecteer **[!UICONTROL Complete]**. Alle voltooide taken worden weergegeven.

   ![filter](assets/filter.png)

1. Tik om een taak te selecteren en klik op **[!UICONTROL Open]**.

De taak wordt geopend om het document of het adaptieve formulier weer te geven dat aan de taak is gekoppeld. Voor Adaptief formulier wordt het alleen-lezen adaptief formulier of het PDF-document van het formulier weergegeven, zoals dit is geconfigureerd op het tabblad Formulier/Document van het dialoogvenster [Workflowstap Toewijzen](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem).

In de sectie met taakdetails wordt informatie weergegeven zoals de ondernomen actie, taakstatus, begindatum en einddatum.

![voltooide taak](assets/completed-task.png)

De **[!UICONTROL Workflow Details]** wordt elke stap van de workflow weergegeven. Tikken **[!UICONTROL View details]** voor een stap voor gedetailleerde informatie.

![voltooid-taak-werkschema](assets/completed-task-workflow.png)

## Problemen oplossen {#troubleshooting-workflows}

### Kan geen items weergeven die gerelateerd zijn aan AEM workflow in AEM Postvak In {#unable-to-see-aem-worklow-items}

Een eigenaar van een workflowmodel kan geen items weergeven die gerelateerd zijn aan AEM workflow in AEM Postvak IN. Om het probleem op te lossen, voegt u de onderstaande indexen toe aan uw AEM opslagplaats en maakt u de index opnieuw.

1. Gebruik een van de volgende methoden om indexen toe te voegen:

   * De volgende knooppunten maken in CRX DE op `/oak:index/workflowDataLucene/indexRules/granite:InboxItem/properties` met de respectieve eigenschappen zoals gespecificeerd in de volgende tabel:

     | Knooppunt | Eigenschap | Type |
     |---|---|---|
     | sharedWith | sharedWith | TEKENREEKS |
     | vergrendeld | vergrendeld | BOOLEAN |
     | geretourneerd | geretourneerd | BOOLEAN |
     | allowInboxSharing | allowInboxSharing | BOOLEAN |
     | allowExplicitSharing | allowExplicitSharing | BOOLEAN |


   * Implementeer de indices via een AEM. U kunt een [AEM Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=en) project om een implementeerbaar AEM pakket te maken. Gebruik de volgende steekproefcode om indexen aan een project van het type van AEM toe te voegen Archetype:

   ```Java
      .property("sharedWith", "sharedWith").type(TYPENAME_STRING).propertyIndex()
      .property("locked", "locked").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("returned", "returned").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowInboxSharing", "allowInboxSharing").type(TYPENAME_BOOLEAN).propertyIndex()
      .property("allowExplicitSharing", "allowExplicitSharing").type(TYPENAME_BOOLEAN).propertyIndex()
   ```

1. [Een index voor eigenschappen maken en instellen op true](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/queries-and-indexing.html?lang=en#the-property-index).

1. Na het configureren van indices in CRX DE of het implementeren via een pakket, [de gegevensopslagplaats opnieuw indexeren](https://helpx.adobe.com/in/experience-manager/kb/HowToCheckLuceneIndex.html#Completelyrebuildtheindex).

