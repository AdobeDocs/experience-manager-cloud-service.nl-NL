---
title: Forms-centric workflow op OSGi
seo-title: Rapidly build Adaptive Forms-based processes, automate document services operations, and use Adobe Sign with AEM workflows
description: Gebruiken [!DNL AEM Forms] Workflow voor het automatisch en snel samenstellen van revisie en goedkeuringen, voor het starten van documentservices
seo-description: Use [!DNL AEM Forms] Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Adobe Sign signature workflow, and more.
uuid: 797ba0f7-a378-45ac-9f82-fa9a952027be
topic-tags: publish, document_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 73e63493-e821-443f-b50d-10797360f5d1
docset: aem65
source-git-commit: 5ad33f0173afd68d8868b088ff5e20fc9f58ad5a
workflow-type: tm+mt
source-wordcount: '2336'
ht-degree: 0%

---


# Forms-centric workflow op OSGi{#forms-centric-workflow-on-osgi}

![Hoofdafbeelding](do-not-localize/header.png)

Ondernemingen verzamelen gegevens uit honderden en duizenden formulieren, verschillende back-endsystemen en online of offline gegevensbronnen. Zij hebben ook een dynamische reeks gebruikers om besluiten over de gegevens te nemen, die herhalende herbeoordeling en goedkeuringsprocessen impliceren.

Samen met overzicht en goedkeuringswerkschema&#39;s voor intern en extern publiek, hebben de grote organisaties en de ondernemingen herhalende taken. Bijvoorbeeld het omzetten van een PDF-document in een andere indeling. Wanneer manueel gedaan, nemen deze taken veel tijd en middelen op. Ondernemingen hebben ook wettelijke vereisten om een document digitaal te ondertekenen en formuliergegevens te archiveren voor later gebruik in vooraf gedefinieerde indelingen.

## Inleiding tot Forms-centric workflow op OSGi {#introduction-to-forms-centric-workflow-on-osgi}

U kunt AEM Workflows gebruiken om snel adaptieve Forms-workflows te maken. Deze workflows kunnen worden gebruikt voor revisie en goedkeuringen, bedrijfsprocesstromen, het starten van documentservices, integratie met de Adobe Sign-handtekeningworkflow en vergelijkbare bewerkingen. Bijvoorbeeld de verwerking van creditcardtoepassingen, de werkstromen van het werknemersverlaten goedkeurings, die een vorm als document van de PDF bewaren. Bovendien kunnen deze workflows binnen een organisatie of via een netwerkfirewall worden gebruikt.

Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Voor de ontwikkeling en het beheer van workflows wordt gebruikgemaakt van de vertrouwde AEM en AEM Inbox-mogelijkheden. De werkstromen vormen de basis van het automatiseren van echte bedrijfsprocessen die veelvoudige softwaresystemen, netwerken, afdelingen, en zelfs organisaties omspannen.

Nadat de werkstromen zijn ingesteld, kunnen deze handmatig worden geactiveerd om een gedefinieerd proces te voltooien of via programmacode worden uitgevoerd wanneer gebruikers een formulier verzenden <!-- or [correspondence management](cm-overview.md) letter-->. <!-- With this enhanced AEM Workflow capabilities, [!DNL AEM Forms] offers two distinct, yet similar, capabilities. As part of your deployment strategy, you need to decide which one works for you. See a [comparison](capabilities-osgi-jee-workflows.md) of the Forms-centric AEM Workflows on OSGi and Process Management on JEE. Moreover, for the deployment topology see, [Architecture and deployment topologies for [!DNL AEM Forms]]((aem-forms-architecture-deployment.md). -->

Forms-gecentreerde workflow op OSGi breidt uit [AEM Inbox](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html#authoring) en biedt extra componenten (stappen) voor AEM Workfloweditor om ondersteuning toe te voegen voor [!DNL AEM Forms]-centric workflows. <!-- The extended AEM Inbox has functionalities similar to [[!DNL AEM Forms] Workspace](introduction-html-workspace.md). Along with managing human-centric workflows (Approval, Review, and so on), you can use AEM workflows to automate [document services](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem)-related operations (for example, Generate PDF) and electronically signing (Adobe Sign) documents. -->

Alles [!DNL AEM Forms] workflowstappen ondersteunen het gebruik van variabelen. Met variabelen kunnen workflowstappen metagegevens tijdens runtime bevatten en doorgeven. U kunt verschillende typen variabelen maken om verschillende typen gegevens op te slaan. U kunt ook variabele verzamelingen (arrays) maken om meerdere instanties van verwante, met hetzelfde type getypte gegevens op te slaan. Typisch, gebruikt u een variabele of een inzameling van variabelen wanneer u een besluit moet nemen dat op de waarde wordt gebaseerd die het houdt of informatie opslaat die u later in een proces nodig hebt. Zie voor meer informatie over het gebruik van variabelen in deze Forms-centric workflowcomponenten (stappen) [Forms-centric workflow voor OSGi - Step Reference](aem-forms-workflow-step-reference.md). Voor informatie over het maken en beheren van variabelen raadpleegt u [Variabelen in AEM werkstromen](variable-in-aem-workflows.md).

Het volgende diagram toont de procedure van begin tot eind om, een Forms-centric werkschema op OSGi tot stand te brengen in werking te stellen en te controleren.

![introductie-to-name-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Voordat u begint {#before-you-start}

* Een werkschema is een vertegenwoordiging van een echt bedrijfsproces. Houd uw real-world bedrijfsproces en lijst van de deelnemers van het bedrijfsproces klaar. Houd ook het onderpand (Adaptive Forms, PDF Documents en meer) gereed voordat u een workflow gaat maken.
* Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en Help de voortgang van de workflow te melden. Verdeel uw bedrijfsproces in logische stadia.
* U kunt de taakstap van AEM Workflows configureren om e-mailmeldingen te verzenden naar de gebruikers of de toewijzingen. Dus, [e-mailberichten inschakelen](#configure-email-service).
* Een workflow kan ook gebruikmaken van een Adobe voor digitale handtekeningen. Als u Adobe Sign in een workflow wilt gebruiken, [Adobe Sign configureren voor [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) voordat u het gebruikt in een workflow.

## Een workflowmodel maken {#create-a-workflow-model}

Een workflowmodel bestaat uit logica en stroom van een bedrijfsproces. Het bestaat uit een reeks stappen. Deze stappen zijn AEM componenten. U kunt workflowstappen uitbreiden met parameters en scripts om desgewenst meer functionaliteit en controle te bieden. [!DNL AEM Forms] biedt naast AEM stappen die beschikbaar zijn vanuit het vak een aantal stappen. Voor een gedetailleerde lijst van AEM en [!DNL AEM Forms] stappen, zie [AEM Workflowstapverwijzing](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem) en [Forms-centric workflow voor OSGi - Step Reference](aem-forms-workflow.md).

AEM biedt een intuïtieve gebruikersinterface voor het maken van een workflowmodel met behulp van de meegeleverde workflowstappen. Voor stapsgewijze instructies voor het maken van een workflowmodel raadpleegt u [Workflowmodellen maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/workflows/overview.html#workflows). In het volgende voorbeeld worden stapsgewijze instructies gegeven voor het maken van een workflowmodel voor een goedkeurings- en revisiewerkstroom:

>[!NOTE]
>
>Als u een workflowmodel wilt maken of bewerken, moet u lid zijn van de groep met workfloweditors.

### Een model maken voor een goedkeurings- en revisiewerkstroom {#create-a-model-for-an-approval-and-review-workflow}

Goedkeuring- en revisiewerkstroom is bedoeld voor de taken waarvoor menselijke tussenkomst vereist is om beslissingen te nemen. In het volgende voorbeeld wordt een workflowmodel gemaakt voor een hypotheekleningaanvraag die moet worden ingevuld door een bankagent voor het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde aanvraag met Adobe Sign naar de aanvrager van elektronische handtekeningen gezonden.

Het voorbeeld is beschikbaar als een hieronder bijgevoegd pakket. Importeer en installeer het voorbeeld met pakketbeheer. U kunt ook de volgende stappen uitvoeren om handmatig het workflowmodel voor de toepassing te maken:

In het voorbeeld wordt een workflowmodel gemaakt voor een hypotheektoepassing die moet worden ingevuld door een bankagent op het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde toepassing met Adobe Sign naar de klant verzonden voor elektronische handtekeningen. U kunt het voorbeeld importeren en installeren met pakketbeheer.

[Bestand ophalen](assets/example-mortgage-loan-application.zip)

1. Open de console Workflowmodellen. De standaard-URL is `https://[server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selecteren **Maken** vervolgens **Model maken**. Het dialoogvenster Workflowmodel toevoegen wordt weergegeven.
1. Voer de **Titel** en **Naam** (optioneel). Bijvoorbeeld een hypotheekaanvraag. Tikken **Gereed**.
1. Selecteer het nieuwe workflowmodel en tik op **Bewerken**. Nu kunt u workflowstappen toevoegen om bedrijfslogica te maken. Wanneer u voor het eerst een workflowmodel maakt, bevat dit:

   * De stappen: Start en Einde stroom. Deze stappen vertegenwoordigen het begin en het einde van de workflow. Deze stappen zijn vereist en kunnen niet worden bewerkt of verwijderd.
   * Een stap van de voorbeelddeelnemer genoemd Stap 1. Deze stap wordt gevormd om een het werkpunt aan de admin gebruiker toe te wijzen. Verwijder deze stap.

1. E-mailmeldingen inschakelen. U kunt een op Forms gerichte workflow op OSGi configureren om e-mailmeldingen naar de gebruikers of gebruikers te sturen. Voer de volgende configuraties uit om e-mailmeldingen in te schakelen:

   1. Ga naar AEM configuratiemanager op `https://[server]:[port]/system/console/configMgr`.
   1. Open de **[!UICONTROL Day CQ Mail Service]** configuratie. Geef een waarde op voor de **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port,]** en **[!UICONTROL "From" address]** velden. Klik op **[!UICONTROL Save]**.
   1. Open de **[!UICONTROL Day CQ Link Externalizer]** configuratie. In de **[!UICONTROL Domains]** Geef het daadwerkelijke hostname-/IP-adres en poortnummer op voor lokale instanties, auteurs- en publicatieinstanties. Klik op **[!UICONTROL Save]**.

1. Workflowfasen maken. Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en de voortgang van de workflow rapporteren.

   Tik op de knop ![info-circle](assets/info-circle.png) om eigenschappen van workflowmodellen te openen, opent u het dialoogvenster **Staven** tabblad, fasen voor het workflowmodel toevoegen en tikken **Opslaan en sluiten**. Voor het voorbeeld van de hypotheektoepassing kunt u fasen maken: aanvraag voor een lening, status van de leningaanvraag, te ondertekenen documenten en ondertekend leningdocument.

1. Sleep de **Taak toewijzen** stappen browser aan het werkschemamodel. Maak van het de eerste stap van het model.

   De taakcomponent toewijzen wijst de taak, die door workflow wordt gemaakt, toe aan een gebruiker of groep. Naast het toewijzen van de taak kunt u de component gebruiken om een adaptief formulier of een niet-interactieve PDF voor de taak op te geven. Het adaptieve formulier is vereist voor het accepteren van invoer van gebruikers en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie bestemd zijn.

   U kunt de stap ook gebruiken om het gedrag van de taak te controleren. Als u bijvoorbeeld een automatisch document met records maakt, wijst u de taak toe aan een bepaalde gebruiker of groep, het pad van de verzonden gegevens, het pad van de gegevens die vooraf moeten worden ingevuld en de standaardhandelingen. Voor gedetailleerde informatie over de opties van de taakstap van de toewijzing, zie [Forms-centric workflow voor OSGi - Step Reference](aem-forms-workflow.md) document.

   ![workflow-editor](assets/workflow-editor.png)

   Configureer voor het voorbeeld van de hypotheektoepassing de taakstap voor toewijzen om een alleen-lezen adaptief formulier te gebruiken en PDF Document weer te geven zodra de taak is voltooid. Selecteer ook voor gebruikersgroep die de aanvraag voor een lening mag goedkeuren. Op de **Handelingen** tabblad, schakelt u de **Verzenden** -optie. Een **actionTake** variabele van het gegevenstype String en geef de variabele op als de **Route Variable**. Bijvoorbeeld actionTake. Voeg ook de routes Goedkeuren en Afwijzen toe. De routes worden getoond als afzonderlijke acties (knopen) in AEM Inbox. De werkstroom selecteert een vertakking op basis van de actie (knoop) een gebruiker tikt.

   U kunt het voorbeeldpakket importeren, dat u kunt downloaden vanaf het begin van de sectie, voor de volledige set waarden van alle velden van de taakstap toewijzen die is geconfigureerd, bijvoorbeeld hypotheektoepassing.

1. Sleep de component OR Splitsen van de stapbrowser naar het workflowmodel. Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

   U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

   Gebruik de uitdrukkingsredacteur om het verpletteren van uitdrukkingen voor Tak 1 en Tak 2 tot stand te brengen. Deze verpletterende uitdrukkingen helpen een tak kiezen die op de gebruikersactie in AEM Inbox wordt gebaseerd.

   **Het verpletteren van uitdrukking voor Tak 1**

   Wanneer een gebruiker tikt **Goedkeuren** in AEM Inbox, wordt Tak 1 geactiveerd.

   ![OR Splitsen, voorbeeld](assets/orsplit_branch1_active_new.png)

   **Verpletterende uitdrukking voor Tak 2**

   Wanneer een gebruiker tikt **Afwijzen** in AEM Inbox, wordt Tak 2 geactiveerd.

   ![OR Splitsen, voorbeeld](assets/orsplit_branch2_active_new.png)

   Voor informatie bij het creëren van het verpletteren van uitdrukkingen die variabelen gebruiken, zie [Variabelen in [!DNL AEM Forms] workflows](variable-in-aem-workflows.md).

1. Voeg andere workflowstappen toe om de bedrijfslogica te bouwen.

   Voeg voor het hypotheekvoorbeeld een Document van Record genereren toe, wijzen twee taakstappen toe en een stap van het ondertekeningsdocument naar vertakking 1 van het model, zoals in de onderstaande afbeelding wordt weergegeven. Eén taakstap toewijzen is weergeven en verzenden **te ondertekenen leningsdocumenten aan de aanvrager** en een andere taakcomponent toewijzen is **om ondertekende documenten te tonen**. Voeg ook een taakcomponent toe aan vertakking 2. Deze wordt geactiveerd wanneer een gebruiker op Afwijzen in AEM Postvak IN tikt.

   Voor de volledige set waarden van alle velden van de taakstappen toewijzen, de stap Document of Record en de stap Document ondertekenen die zijn geconfigureerd voor bijvoorbeeld hypotheektoepassing, importeert u het voorbeeldpakket dat beschikbaar is voor downloaden in het begin van deze sectie.

   Het workflowmodel is gereed. U kunt de workflow op verschillende manieren starten. Zie voor meer informatie [Een Forms-centric workflow starten op OSGi](#launch).

   ![workflow-editor-hypotheek](assets/workflow-editor-mortgage.png)

## Een Forms-centric Workflow-toepassing maken {#create-a-forms-centric-workflow-application}

De toepassing is het adaptieve formulier dat aan de workflow is gekoppeld. Wanneer een toepassing via Inbox wordt verzonden, wordt de bijbehorende workflow gestart. Een Forms-workflow beschikbaar maken als een toepassing in AEM Inbox en [!DNL AEM Forms] Voer de volgende handelingen uit om een workflowtoepassing te maken:

>[!NOTE]
>
>U moet lid van de fd-beheerder groep zijn om werkschematoepassingen te kunnen tot stand brengen en beheren.

1. Ga naar de AEM ![gereedschappen-1](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Manage Workflow Application]** en kranen **[!UICONTROL Create]**.
1. Geef in het venster Workflowtoepassing maken invoer op voor de volgende velden en tikken **Maken**. Er wordt een nieuwe toepassing gemaakt en deze wordt weergegeven in het scherm Workflowtoepassingen.

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>De titel is zichtbaar in AEM Postvak IN en helpt gebruikers een toepassing te kiezen. Houd het beschrijvend. Bijvoorbeeld, sparen Account die Toepassing opent.<br /> </td>
  </tr>
  <tr>
   <td>Naam </td>
   <td>Geef de naam van de toepassing op. Alle andere tekens dan alfabeten, getallen, koppeltekens en onderstrepingstekens worden vervangen door afbreekstreepjes. </td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>De beschrijving is zichtbaar in AEM Postvak IN. Geef in de beschrijvingsvelden gedetailleerde informatie over de toepassing. Bijvoorbeeld Doel van de toepassing.<br /> </td>
  </tr>
  <tr>
   <td>Adaptief formulier</td>
   <td><p>Geef het pad van een adaptief formulier op. Wanneer een gebruiker een toepassing start, wordt het opgegeven adaptieve formulier weergegeven.</p> <p><strong>Opmerking</strong>: Workflowtoepassingen ondersteunen geen formulieren en PDF-documenten die langer zijn dan één pagina of die schuiven op Apple iPad vereisen. Wanneer een toepassing wordt geopend in Apple iPad en het adaptieve formulier of het PDF-document langer is dan een pagina, gaan de formuliervelden en inhoud van de tweede pagina verloren.</p> </td>
  </tr>
  <tr>
   <td>Toegangsgroep</td>
   <td><p>Selecteer een groep. De toepassing is alleen zichtbaar in AEM Postvak IN voor de leden van de geselecteerde groep. De optie van de toegangsgroep maakt alle groepen van [!DNL workflow-users] groep beschikbaar voor selectie. </p> <br /> </td>
  </tr>
  <tr>
   <td>Prefill-service</td>
   <td>Selecteer een <a href="prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">Prefill-service</a> voor het adaptieve formulier.<br /> </td>
  </tr>
  <tr>
   <td>Workflowmodel</td>
   <td>Selecteer een <a href="aem-forms-workflow.md#create-a-workflow-model">workflowmodel</a> voor de toepassing. Een workflowmodel bestaat uit logica en stroom van het bedrijfsproces. </td>
  </tr>
  <tr>
   <td>Pad gegevensbestand</td>
   <td>Geef het pad op van het gegevensbestand in de crx-gegevensopslagruimte. Het pad is relatief ten opzichte van de payload van het adaptieve formulier en bevat de naam van het gegevensbestand. Neem altijd de volledige naam van het bestand op, inclusief de extensie, indien van toepassing. Bijvoorbeeld [payload]/data.xml. </td>
  </tr>
  <tr>
   <td>Pad bijlage</td>
   <td>Geef het pad van de map voor bijlagen op in de crx-repository. Het pad naar de bijlage is relatief ten opzichte van de laadlocatie. Bijvoorbeeld [payload]/data.xml. </td>
  </tr>
  <tr>
   <td>Document van Recordpad</td>
   <td>Geef het pad op van het document of recordbestand in de crx-gegevensopslagruimte. Het pad is relatief ten opzichte van de payload-locatie van het adaptieve formulier. Neem altijd de volledige naam van het bestand op, inclusief de extensie, indien van toepassing. Bijvoorbeeld [payload]/DOR/creditcard.pdf.</td>
  </tr>
 </tbody>
</table>

## Een Forms-centric workflow starten op OSGi {#launch}

U kunt een Forms-centric workflow starten of activeren door:

* [Een toepassing verzenden vanuit AEM Postvak In](#inbox)
* [Een toepassing verzenden vanuit [!DNL AEM Forms] App](#afa)

* [Een adaptief formulier verzenden](#af)
* [Gecontroleerde map gebruiken](#watched)

* [Een interactieve communicatie of een brief indienen](#letter)

### Een toepassing verzenden vanuit AEM Postvak In {#inbox}

De workflowtoepassing die u hebt gemaakt, is beschikbaar als een toepassing in Inbox. Gebruikers die lid zijn van [!DNL workflow-users] de groep kan de toepassing die de bijbehorende workflow activeert, vullen en verzenden. Voor informatie over het gebruiken van AEM Inbox om toepassingen voor te leggen en taken te beheren, zie [Forms-toepassingen en -taken beheren in AEM Postvak In](manage-applications-inbox.md).

<!-- ### Submitting an application from [!DNL AEM Forms] App {#afa}

The [!DNL AEM Forms] app syncs with an [!DNL AEM Forms] server and lets you make changes to the form data, tasks, workflow applications, and saved information (drafts/templates) in your account. For more information, see [[!DNL AEM Forms] app]((aem-forms-app.md) and related articles.-->

### Een adaptief formulier verzenden {#af}

U kunt de verzendhandelingen van een adaptief formulier zo configureren dat een workflow wordt gestart bij het verzenden van het adaptieve formulier. Adaptive Forms biedt de **Een AEM-workflow aanroepen** Verzend Actie om een workflow te starten bij het verzenden van een adaptief formulier. Zie voor meer informatie over de handeling Verzenden [De handeling Verzenden configureren](configuring-submit-actions.md). Een adaptief formulier verzenden via het dialoogvenster [!DNL AEM Forms] app, synchroniseren inschakelen met [!DNL AEM Forms] App in de eigenschappen Adaptief formulier.

<!-- You can configure an Adaptive Form to sync, submit, and trigger a workflow from [!DNL AEM Forms] app. For details, see [working with a form]((working-with-form.md). -->

<!-- ### Using a watched folder {#watched}

An administrator (a member of fd-administrators group) can configure a network folder to run a pre-configured workflow when a user places a file (such as a PDF file) in the folder. After the workflow completes, it can save the result file to a specified output folder. Such a folder is known as [Watched Folder](watched-folder-in-aem-forms.md). Perform the following procedure to configure a watched folder to launch a workflow:

1. On your AEM author instance, go to ![tools-1](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Configure Watched Folder]**. A list of already configured watched folders is displayed.
1. Tap **[!UICONTROL New]**. A list of fields is displayed. Specify a value for the following fields to configure a Watched Folder for a workflow:

<table>
 <tbody>
  <tr>
   <td>Field</td>
   <td>Description</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Name</code></td>
   <td>Specify the name of the Watched Folder. This field support only alphanumeric.</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Path</code></td>
   <td>Specify the physical location of the Watched Folder. In a clustered environment, use a shared network folder that is accessible from AEM cluster node.</td>
  </tr>
  <tr>
   <td><span class="uicontrol">Process Files Using</code></td>
   <td>Select the <span class="uicontrol">Workflow </code>option. </td>
  </tr>
  <tr>
   <td><span class="uicontrol">Workflow Model</code></td>
   <td>Select a workflow model.<br /> </td>
  </tr>
  <tr>
   <td><span class="uicontrol">Output File Pattern</code></td>
   <td>Specify the directory structure for output files and directories. </a>.</td>
  </tr>
 </tbody>
</table>

1. Tap **Advanced**. Specify a value for the following field and taps **Create**. The Watched Folder is configured to launch a workflow. Now, whenever a file is placed in the input directory of the Watched Folder, the specified workflow is triggered.

   | Field |Description |
   |---|---|
   | Payload Mapper Filter |When you create a watched folder, it creates a folder structure in the crx-repository. The folder structure can serve as a payload to the workflow. You can write a script to map an AEM Workflow to accept inputs from the watched folder structure. An out of the box implementation is available and listed in the Payload Mapper Filter. If you do not have a custom implementation, select the default implementation. |

   The Advanced tab contains more fields. Most of these fields contain a default value. To learn about all the fields, see the [Create or Configure a watched folder]((admin-help/configuring-watched-folder-endpoints.md) article. -->

<!-- ### Submitting an interactive communication or a letter {#letter}

You can associate and execute a Forms-centric workflow on OSGi on submission of an interactive communication or a letter. In correspondence management workflows are used for post processing interactive communications and letters. For example, emailing, printing, faxing, or archiving final letters. For detailed steps, see [Post processing of interactive communications and letters](submit-letter-topostprocess.md).

## Additional Configurations {#additional-configurations}

### Configure email service {#configure-email-service}

You can use the Assign Task and Send Email steps of AEM Workflows to send an email. Perform the following steps to specify email servers and other configurations required to send email:

1. Go to AEM configuration manager at `https://[server]:[port]/system/console/configMgr`.
1. Open the **[!UICONTROL Day CQ Mail Service]** configuration. Specify a value for the **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port,]** and **[!UICONTROL "From" address]** fields. Click **[!UICONTROL Save]**.
1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual hostname/IP address and port number for local, author, and publish instances. Click **[!UICONTROL Save]**. -->

### Workflowinstanties wissen {#purge-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen. Zie voor meer informatie [Regelmatig leegmaken van workflowinstanties](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html) leegmaken van werkstroominstanties
