---
title: Hoe te om AEM Aangepast Vorm met Microsoft&amp te verbinden;reg; Lijst van SharePoint?
description: Een adaptief formulier verbinden met Microsoft&reg; SharePoint-lijst. Leer hoe u de Microsoft&reg; SharePoint-lijst configureert en een Form Data Model (FDM) maakt met behulp van de configuratie. Bovendien leert u hoe te om FDM met uw Aangepast Vorm te integreren.
role: User, Developer
keywords: Sluit AEM adaptief formulier aan op de Microsoft SharePoint-lijst, sluit adaptief formulier aan op de Microsoft SharePoint-lijst, integreer AEM adaptief formulier met de SharePoint SharePoint-lijst, integreer Adaptief formulier met de-lijst, verzend gegevens van een adaptief formulier naar de-lijst, verzend AEM workflow naar de-lijst.
hide: true
hidefromToC: true
source-git-commit: 81951a9507ec3420cbadb258209bdc8e2b5e2942
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst

<span class="preview"> Dit is een pre-versieeigenschap en toegankelijk door ons [ pre-vrijgavekanaal ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html#new-features). </span>

**Microsoft® SharePoint**: Microsoft® SharePoint laat samenwerking toe door dynamische en efficiënte teamplaatsen voor alle teams, afdelingen, en afdelingen te verstrekken. Het wordt gebruikt om, informatie van om het even welk apparaat op te slaan te organiseren, te delen en toegang tot informatie van om het even welk Webbrowser, bijvoorbeeld, Microsoft® Edge, Internet Explorer, Chrome, of Firefox. De twee belangrijkste componenten van **Microsoft® SharePoint** zijn:

* **de Bibliotheek van het Document van Microsoft® SharePoint®**: De Bibliotheek van het Document van Microsoft® SharePoint toont een lijst van dossiers en omslagen samen met hun zeer belangrijke informatie, zoals de laatste gewijzigde datum en de eigenaar van een dossier. Met deze functie kunt u eenvoudig bestanden ordenen en navigeren.
Voor instructies op hoe te om de Bibliotheek van het Document van a **Microsoft® SharePoint** met een Aangepaste Vorm te integreren, zie [ AanpassingsVorm voorlegt het artikel van de Actie ](/help/forms/configuring-submit-actions.md#submit-to-sharepoint).

* **Microsoft® SharePoint Lijst**: De Lijst van Microsoft® SharePoint is een inzameling van gegevens. U kunt kolommen toevoegen voor verschillende typen gegevens en weergaven maken om gegevens effectief weer te geven. U kunt de lijsten gemakkelijk groeperen, filteren, sorteren, en formatteren.

>[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

## Vereisten om een adaptief formulier aan te sluiten op de Microsoft® SharePoint-lijst {#prerequisites}

Voer de volgende stappen uit voordat u een adaptief formulier koppelt aan de Microsoft® SharePoint List:

1. [Microsoft configureren](/help/forms/configure-data-sources.md#configure-microsoft-sharepoint-list)
1. [Een formuliergegevensmodel (FDM) maken met Microsoft](/help/forms/create-form-data-models.md)
1. [Vorm het Model van de Gegevens van de Vorm (FDM) om gegevens terug te winnen en te verzenden](/help/forms/work-with-form-data-model.md#configure-services)
1. [Een adaptief formulier maken](/help/forms/creating-adaptive-form-core-components.md)

Nu kunt u:

* [Connect Microsoft](#connect-an-adaptive-form-to-microsoft-sharepoint-list-connect-af-sharepoint-list)
* [Connect Microsoft](#connect-sharepoint-list-workflow)

## Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

Om de Lijst van Microsoft® SharePoint aan uw Aangepaste Vorm [ te integreren vormt een Aangepast Vorm om een Model van de Gegevens van de Vorm (FDM) te gebruiken ](/help/forms/creating-adaptive-form-core-components.md#configure-a-schema-or-form-data-model-for-an-adaptive-formconfigure-schema-or-data-model-for-form)

Nadat u een adaptief formulier hebt geconfigureerd voor het gebruik van een FDM (Form Data Model), kunt u:

* [Verzendactie configureren met een FDM (Form Data Model)](/help/forms/configuring-submit-actions.md#submit-using-form-data-model)
* [Vorm de Redacteur van de Regel om een Model van de Gegevens van de Vorm (FDM) aan te halen](/help/forms/rule-editor.md#invoke-form-data-model-service-invoke)

## Microsoft® SharePoint List verbinden met een AEM workflow {#connect-sharepoint-list-workflow}

Microsoft® SharePoint List integreren in een AEM workflow:

1. [ creeer een werkschema om een model van Gegevens van de Vorm (FDM) aan te halen ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html)

   <!--
    To create a workflow with the editor:
    1.  Go to your **AEM Forms Author** instance > **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]**.
    1.  Click **[!UICONTROL Create]** > **[!UICONTROL Create Model]**. The Add Workflow Model dialog appears. 
    1. Specify **[!UICONTROL Title]** and **[!UICONTROL Name (optional)]**.
    1. Click **[!UICONTROL Done]**. The new model is listed in the Workflow Models console.
    1. Select your new workflow, then use **[!UICONTROL Edit]** to open it for configuration.
    1. Add **[!UICONTROL Invoke Form Data Model Service]** step to your workflow.
    1. Confirm the changes with Sync (editor toolbar) to generate the runtime model.
    -->

1. [Vorm voorleggen actie om een AEMWerkschema aan te halen](/help/forms/configuring-submit-actions.md#invoke-an-aem-workflow)


Leer hoe te [ gebruik AEM Werkschema ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/workflow/use-workflow.html) om, inhoud in een AanpassingsVorm samen te werken te beheren en te verwerken.

## Aanbevolen procedures {#best-practices}

<!-- * For storing data in a tabular format or implementing data permissions, it is advisable to use Microsoft&reg; SharePoint List rather than Microsoft&reg; SharePoint Document Library. -->
* In Microsoft® SharePoint List worden de volgende kolomtypen niet ondersteund:
   * afbeeldingskolom
   * metagegevenskolom
   * persoonlijke kolom
   * kolom externe gegevens

## Zie ook {#see-also}

* [Een adaptief formulier op basis van een kerncomponent maken](/help/forms/creating-adaptive-form-core-components.md)
* [Gegevensbronnen configureren](/help/forms/configuring-submit-actions.md)
* [Formuliergegevensmodel maken (FDM)](/help/forms/create-form-data-models.md)
* [Forms-centrische AEM Workflows gebruiken - Step Reference to automatisate business processes](/help/forms/aem-forms-workflow-step-reference.md)
* [Een aangepaste verzendactie maken voor Adaptieve Forms](/help/forms/custom-submit-action-form.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Een adaptief formulier insluiten op een AEM Sites-pagina](/help/forms/embed-adaptive-form-aem-sites.md)
* [Thema&#39;s maken, gebruiken en aanpassen in een adaptief formulier](/help/forms/using-themes-in-core-components.md)







