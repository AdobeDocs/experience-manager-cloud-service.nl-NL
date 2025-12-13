---
title: Hoe wordt AEM Forms gebruikt voor bedrijfsprocesautomatisering (BPM)?
seo-title: Rapidly build Adaptive Forms-based processes, automate document services operations, and use Adobe Sign with AEM workflows
description: Gebruik AEM Forms Workflow om bedrijfsprocesworkflows te automatiseren en snel samen te stellen. Bijvoorbeeld, revisie en goedkeuring, PDF Generation, Adobe Sign workflows.
uuid: 797ba0f7-a378-45ac-9f82-fa9a952027be
topic-tags: publish, document_services
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f0fec4a9-b214-4931-bf09-5898b082481e
source-git-commit: 8f39bffd07e3b4e88bfa200fec51572e952ac837
workflow-type: tm+mt
source-wordcount: '2464'
ht-degree: 0%

---

# Forms-centric workflow op OSGi {#forms-centric-workflow-on-osgi}

![&#x200B; Hero Beeld &#x200B;](do-not-localize/header.png)

Ondernemingen verzamelen gegevens uit honderden en duizenden formulieren, verschillende back-endsystemen en online of offline gegevensbronnen. Zij hebben ook een dynamische reeks gebruikers om besluiten over de gegevens te nemen, die herhalende herbeoordeling en goedkeuringsprocessen impliceren.

Samen met overzicht en goedkeuringswerkschema&#39;s voor intern en extern publiek, hebben de grote organisaties en de ondernemingen herhalende taken. Een PDF-document wordt bijvoorbeeld geconverteerd naar een andere indeling. Wanneer manueel gedaan, nemen deze taken veel tijd en middelen op. Ondernemingen hebben ook wettelijke vereisten om een document digitaal te ondertekenen en formuliergegevens te archiveren voor later gebruik in vooraf gedefinieerde indelingen.

## Inleiding tot Forms-centric workflow op OSGi {#introduction-to-forms-centric-workflow-on-osgi}

U kunt AEM Workflows gebruiken om snel adaptieve Forms-workflows te maken. Deze workflows kunnen worden gebruikt voor revisie en goedkeuringen, bedrijfsprocesstromen, het starten van documentservices, integratie met de ondertekeningsworkflow van Adobe Sign en vergelijkbare bewerkingen. Bijvoorbeeld: verwerking van creditcardtoepassingen, workflows voor goedkeuring door werknemers, een formulier opslaan als een PDF-document. Bovendien kunnen deze workflows binnen een organisatie of via een netwerkfirewall worden gebruikt.

Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi, zonder het moeten het volledige vermogen van het Beheer van het Proces op de stapel van JEE installeren. Voor de ontwikkeling en het beheer van workflows worden de bekende AEM Workflow- en AEM Inbox-mogelijkheden gebruikt. De werkstromen vormen de basis van het automatiseren van echte bedrijfsprocessen die veelvoudige softwaresystemen, netwerken, afdelingen, en zelfs organisaties omspannen.

Zodra deze zijn ingesteld, kunnen deze workflows handmatig worden geactiveerd om een gedefinieerd proces te voltooien of via programmacode worden uitgevoerd wanneer gebruikers een formulier verzenden <!-- or [correspondence management](cm-overview.md) letter--> . <!-- With this enhanced AEM Workflow capabilities, [!DNL AEM Forms] offers two distinct, yet similar, capabilities. As part of your deployment strategy, you need to decide which one works for you. See a [comparison](capabilities-osgi-jee-workflows.md) of the Forms-centric AEM Workflows on OSGi and Process Management on JEE. Moreover, for the deployment topology see, [Architecture and deployment topologies for [!DNL AEM Forms]]((aem-forms-architecture-deployment.md). -->

Forms-centric werkschema op OSGi breidt [&#x200B; AEM Inbox &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/inbox.html#authoring) uit en verstrekt extra componenten (stappen) voor de redacteur van het Werkschema van AEM om steun voor [!DNL AEM Forms]-centric werkschema&#39;s toe te voegen. <!-- The extended AEM Inbox has functionalities similar to [[!DNL AEM Forms] Workspace](introduction-html-workspace.md). Along with managing human-centric workflows (Approval, Review, and so on), you can use AEM workflows to automate [document services](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem)-related operations (for example, Generate PDF) and electronically signing (Adobe Sign) documents. -->

Alle [!DNL AEM Forms] workflowstappen ondersteunen het gebruik van variabelen. Met variabelen kunnen workflowstappen metagegevens tijdens runtime bevatten en doorgeven. U kunt verschillende typen variabelen maken om verschillende typen gegevens op te slaan. U kunt ook variabele verzamelingen (arrays) maken om meerdere instanties van verwante, met hetzelfde type getypte gegevens op te slaan. Typisch, gebruikt u een variabele of een inzameling van variabelen wanneer u een besluit moet nemen dat op de waarde wordt gebaseerd die het houdt of informatie opslaat die u later in een proces nodig hebt. Voor meer informatie bij het gebruiken van variabelen in deze Forms-centric werkschemacomponenten (stappen), zie [&#x200B; Forms-centric werkschema op OSGi - de Verwijzing van de Stap &#x200B;](aem-forms-workflow-step-reference.md). Voor informatie bij het creëren van en het beheren van variabelen, zie [&#x200B; Variabelen in de werkschema&#39;s van AEM &#x200B;](variable-in-aem-workflows.md).

Het volgende diagram toont de procedure van begin tot eind om, een Forms-centric werkschema op OSGi tot stand te brengen in werking te stellen en te controleren.

![&#x200B; inleiding-aan-naam-vormen-werkschema &#x200B;](assets/introduction-to-aem-forms-workflow.jpg)

## Toepassings- en gebruiksgevallen

### Verzekeringen

## Biedt AEM Forms ondersteuning voor workflows voor verzekeringsgoedkeuring?

Ja. AEM Forms biedt ondersteuning voor workflowgebaseerde revisies en goedkeuringen, waardoor revisoren, beheerdersgoedkeuring en herwerklussen als onderdeel van verzekeringsprocessen kunnen worden ingeschakeld.

## Ondersteunt AEM Forms processen voor het controleren van verzekeringsmakelaars?

Ja. De workflows van AEM Forms kunnen worden gevormd om makelaarscontrolepatronen te steunen, die scheiding van taken tussen gegevensingang en goedkeuringsrollen verzekeren.

## Kan AEM Forms de status van verzekeringsclaims of -aanvragen volgen?

Ja. Met AEM Forms-workflows kunnen verzekeraars de status van het verzenden en verwerken van formulieren bijhouden in verschillende stadia van het bedrijfsproces.

## Biedt AEM Forms ondersteuning voor het overnemen van workflows?

Ja, met workflows en integratie. AEM Forms ondersteunt workflowgestuurde processen en backendintegratie die toepassingsgegevens in verzekerings- en beslissingssystemen laten stromen.

## Ondersteunt AEM Forms audittrails voor verzekeringsprocessen?

Ja. AEM Forms ondersteunt controleerbaarheid via workflowgeschiedenis, toegangscontroles en systeemlogboeken, die verzekeraars helpen te voldoen aan interne en externe auditbehoeften.

## Voordat u begint {#before-you-start}

* Een werkschema is een vertegenwoordiging van een echt bedrijfsproces. Houd uw real-world bedrijfsproces en lijst van de deelnemers van het bedrijfsproces klaar. Houd ook de gegevens (Adaptive Forms, PDF Documents en meer) bij de hand voordat u een workflow gaat maken.
* Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en Help de voortgang van de workflow te melden. Verdeel uw bedrijfsproces in logische stadia.
* U kunt de taakstap van AEM Workflows configureren om e-mailmeldingen naar de gebruikers of toewijzen te verzenden. Zo, [&#x200B; laat e-mailberichten &#x200B;](#configure-email-service) toe.
* Een workflow kan ook gebruikmaken van Adobe-handtekeningen voor digitale handtekeningen. Als u van plan bent om het Teken van Adobe in een werkschema te gebruiken, vormt [&#x200B; het Teken van Adobe voor  [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) alvorens het in een werkschema te gebruiken.

## Een workflowmodel maken {#create-a-workflow-model}

Een workflowmodel bestaat uit logica en stroom van een bedrijfsproces. Het bestaat uit een reeks stappen. Deze stappen zijn AEM-componenten. U kunt workflowstappen uitbreiden met parameters en scripts om desgewenst meer functionaliteit en controle te bieden. [!DNL AEM Forms] biedt naast de AEM-stappen uit het vak een aantal stappen. Voor een gedetailleerde lijst van AEM en [!DNL AEM Forms] stappen, zie [&#x200B; Verwijzing van de Stap van de Werkstroom van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-step-ref.html#extending-aem) en [&#x200B; Forms-centric werkschema op OSGi - de Verwijzing van de Stap &#x200B;](aem-forms-workflow.md).

AEM biedt een intuïtieve gebruikersinterface voor het maken van een workflowmodel met behulp van de meegeleverde workflowstappen. Voor geleidelijke instructies om een werkschemamodel tot stand te brengen, zie [&#x200B; Creërend de Modellen van het Werkschema &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/workflows/overview.html#workflows). In het volgende voorbeeld worden stapsgewijze instructies gegeven voor het maken van een workflowmodel voor een goedkeurings- en revisiewerkstroom:

>[!NOTE]
>
>Als u een workflowmodel wilt maken of bewerken, moet u lid zijn van de groep met workfloweditors.

### Een model maken voor een goedkeurings- en revisiewerkstroom {#create-a-model-for-an-approval-and-review-workflow}

Goedkeuring- en revisiewerkstroom is bedoeld voor de taken waarvoor menselijke tussenkomst vereist is om beslissingen te nemen. In het volgende voorbeeld wordt een workflowmodel gemaakt voor een hypotheekleningaanvraag die moet worden ingevuld door een bankagent voor het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde toepassing met Adobe-handtekening verzonden naar de aanvrager voor elektronische handtekeningen.

Het voorbeeld is beschikbaar als een hieronder bijgevoegd pakket. Importeer en installeer het voorbeeld met pakketbeheer. U kunt ook de volgende stappen uitvoeren om handmatig het workflowmodel voor de toepassing te maken:

In het voorbeeld wordt een workflowmodel gemaakt voor een hypotheektoepassing die moet worden ingevuld door een bankagent op het hoofdkantoor. Nadat de aanvraag is ingevuld, wordt deze ter goedkeuring verzonden. Later wordt de goedgekeurde toepassing voor elektronische handtekeningen naar de klant verzonden met Adobe Sign. U kunt het voorbeeld importeren en installeren met pakketbeheer.

[Bestand ophalen](assets/example-mortgage-loan-application.zip)

1. Open de console Workflowmodellen. De standaard-URL is `https://[server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Selecteer **creeer**, dan **creeer Model**. Het dialoogvenster Workflowmodel toevoegen wordt weergegeven.
1. Ga de **Titel** en **Naam** (facultatief) in. Bijvoorbeeld een hypotheekaanvraag. Selecteer **Gereed**.
1. Selecteer het gecreeerde werkschemamodel en selecteer **uitgeven**. Nu kunt u workflowstappen toevoegen om bedrijfslogica te maken. Wanneer u voor het eerst een workflowmodel maakt, bevat dit:

   * De stappen: Start en Einde stroom. Deze stappen vertegenwoordigen het begin en het einde van de workflow. Deze stappen zijn vereist en kunnen niet worden bewerkt of verwijderd.
   * Een stap van de voorbeelddeelnemer genoemd Stap 1. Deze stap wordt gevormd om een het werkpunt aan de admin gebruiker toe te wijzen. Verwijder deze stap.

1. E-mailmeldingen inschakelen. U kunt een op Forms gerichte workflow op OSGi configureren om e-mailmeldingen naar de gebruikers of gebruikers te sturen. Voer de volgende configuraties uit om e-mailmeldingen in te schakelen:

   1. Ga naar AEM Configuration Manager op `https://[server]:[port]/system/console/configMgr` .
   1. Open de **[!UICONTROL Day CQ Mail Service]** -configuratie. Geef een waarde op voor de velden **[!UICONTROL SMTP server host name]** , **[!UICONTROL SMTP server port]** en **[!UICONTROL "From" address]** . Klik op **[!UICONTROL Save]**.
   1. Open de **[!UICONTROL Day CQ Link Externalizer]** -configuratie. Geef in het veld **[!UICONTROL Domains]** het werkelijke hostnaam/IP-adres en poortnummer op voor lokale instanties, auteurs en publicatieinstanties. Klik op **[!UICONTROL Save]**.

1. Workflowfasen maken. Een werkstroom kan uit meerdere fasen bestaan. Deze fasen worden weergegeven in het AEM Inbox en de voortgang van de workflow rapporteren.

   Om een stadium te bepalen, selecteer het ![&#x200B; info-circle &#x200B;](assets/info-circle.png) pictogram om de eigenschappen van het werkschemamodel te openen, open het **lusje van Staven**, voeg stadia voor het werkschemamodel toe, en selecteer **sparen &amp; dicht**. Voor het voorbeeld van de hypotheektoepassing kunt u fasen maken: aanvraag voor een lening, status van de leningaanvraag, te ondertekenen documenten en ondertekend leningdocument.

1. De belemmering-en-daling **wijst de stappen van de Taak** browser aan het werkschemamodel toe. Maak van het de eerste stap van het model.

   De taakcomponent toewijzen wijst de taak, die door workflow wordt gemaakt, toe aan een gebruiker of groep. Naast het toewijzen van de taak kunt u de component gebruiken om een adaptief formulier of een niet-interactieve PDF voor de taak op te geven. Het adaptieve formulier is vereist voor het accepteren van invoer van gebruikers en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie zijn.

   U kunt de stap ook gebruiken om het gedrag van de taak te controleren. Als u bijvoorbeeld een automatisch document met records maakt, wijst u de taak toe aan een bepaalde gebruiker of groep, het pad van de verzonden gegevens, het pad van de gegevens die vooraf moeten worden ingevuld en de standaardhandelingen. Voor gedetailleerde informatie over de opties van de taakstap toewijzen, zie [&#x200B; Forms-centric werkschema op OSGi - het document van de Verwijzing van de Stap &#x200B;](aem-forms-workflow.md).

   ![&#x200B; werkschema-redacteur &#x200B;](assets/workflow-editor.png)

   Configureer voor het voorbeeld van de hypotheektoepassing de taakstap voor toewijzen om een alleen-lezen adaptief formulier te gebruiken en PDF-document weer te geven zodra de taak is voltooid. Selecteer ook voor gebruikersgroep die de aanvraag voor een lening mag goedkeuren. Op het **lusje van Acties**, maak **&#x200B;**&#x200B;optie voor voorleggen onbruikbaar. Creeer een **actiontaken** variabele van het gegevenstype van het Koord en specificeer de variabele als **Variabele van de Route**. Bijvoorbeeld actionTake. Voeg ook de routes Goedkeuren en Afwijzen toe. De routes worden getoond als afzonderlijke acties (knopen) in AEM Inbox. De werkstroom selecteert een vertakking op basis van de actie (knoop) een gebruiker tikt.

   U kunt het voorbeeldpakket importeren, dat u kunt downloaden vanaf het begin van de sectie, voor de volledige set waarden van alle velden van de taakstap toewijzen die is geconfigureerd, bijvoorbeeld hypotheektoepassing.

1. Sleep de component OR Splitsen van de stapbrowser naar het workflowmodel. Met de indeling OR wordt een splitsing in de workflow gemaakt, waarna slechts één vertakking actief is. Met deze stap kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren. U voegt workflowstappen naar wens toe aan elke vertakking.

   U kunt het verpletteren van uitdrukking voor een tak bepalen gebruikend een regeldefinitie, manuscript ECMA, of een extern manuscript.

   Gebruik de uitdrukkingsredacteur om het verpletteren van uitdrukkingen voor Tak 1 en Tak 2 tot stand te brengen. Deze verpletterende uitdrukkingen helpen een tak kiezen die op de gebruikersactie in AEM Inbox wordt gebaseerd.

   **Verpletterend uitdrukking voor Tak 1**

   Wanneer een gebruiker **tikt goedkeuren** in AEM Inbox, Tak 1 wordt geactiveerd.

   ![&#x200B; OF Gesplitst voorbeeld &#x200B;](assets/orsplit_branch1_active_new.png)

   **Verpletterend uitdrukking voor Tak 2**

   Wanneer een gebruiker **Afwijzen** in AEM Inbox tikt, wordt Tak 2 geactiveerd.

   ![&#x200B; OF Gesplitst voorbeeld &#x200B;](assets/orsplit_branch2_active_new.png)

   Voor informatie bij het creëren van het verpletteren van uitdrukkingen die variabelen gebruiken, zie [&#x200B; Variabelen in  [!DNL AEM Forms]  werkschema&#39;s &#x200B;](variable-in-aem-workflows.md).

1. Voeg andere workflowstappen toe om de bedrijfslogica te bouwen.

   Voeg voor het hypotheekvoorbeeld een Document van Record genereren toe, wijzen twee taakstappen toe en een stap van het ondertekeningsdocument naar vertakking 1 van het model, zoals in de onderstaande afbeelding wordt weergegeven. Één wijst taakstap toe moet **tonen en verzenden om ondertekende leningsdocumenten aan de aanvrager** te zijn en een andere taakcomponent toewijzen is **om ondertekende documenten** te tonen. Voeg ook een taakcomponent toe aan vertakking 2. Deze wordt geactiveerd wanneer een gebruiker op Afwijzen tikt in AEM Inbox.

   Voor de volledige set waarden van alle velden van de taakstappen toewijzen, importeert u de stap Document of Record en de stap Document ondertekenen die bijvoorbeeld is geconfigureerd voor hypotheektoepassing. Importeer het voorbeeldpakket, dat beschikbaar is om te worden gedownload vanaf het begin van deze sectie.

   Het workflowmodel is gereed. U kunt de workflow op verschillende manieren starten. Voor details, zie [&#x200B; Lancering een Forms-centric werkschema op OSGi &#x200B;](#launch).

   ![&#x200B; werkschema-redacteur-hypotheek &#x200B;](assets/workflow-editor-mortgage.png)

## Een Forms-centric Workflow-toepassing maken {#create-a-forms-centric-workflow-application}

De toepassing is het adaptieve formulier dat aan de workflow is gekoppeld. Wanneer een toepassing via Inbox wordt verzonden, wordt de bijbehorende workflow gestart. Als u een Forms-workflow als toepassing beschikbaar wilt maken in AEM Inbox en [!DNL AEM Forms] App, gaat u als volgt te werk om een workflowtoepassing te maken:

>[!NOTE]
>
>U moet lid van de fd-beheerder groep zijn om werkschematoepassingen te kunnen tot stand brengen en beheren.

1. Op uw de auteursinstantie van AEM, ga ![&#x200B; hulpmiddelen-1 &#x200B;](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Manage Workflow Application]** en tikken **[!UICONTROL Create]**.
1. In het Create venster van de Toepassing van het Werkschema, verstrek input voor de volgende gebieden, en tikt **&#x200B;**&#x200B;creëren. Er wordt een nieuwe toepassing gemaakt en deze wordt weergegeven in het scherm Workflowtoepassingen.

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Beschrijving</td>
  </tr>
  <tr>
   <td>Titel</td>
   <td>De titel is zichtbaar in AEM Inbox en helpt gebruikers een toepassing te kiezen. Houd het beschrijvend. Bijvoorbeeld, sparen de Toepassing van de Rekening die.<br /> opent </td>
  </tr>
  <tr>
   <td>Naam </td>
   <td>Geef de naam van de toepassing op. Alle andere tekens dan alfabeten, getallen, koppeltekens en onderstrepingstekens worden vervangen door afbreekstreepjes. </td>
  </tr>
  <tr>
   <td>Beschrijving</td>
   <td>De beschrijving is zichtbaar in AEM Inbox. Geef in de beschrijvingsvelden gedetailleerde informatie over de toepassing. Bijvoorbeeld, Doel van de toepassing.<br /> </td>
  </tr>
  <tr>
   <td>Adaptief formulier</td>
   <td><p>Geef het pad van een adaptief formulier op. Wanneer een gebruiker een toepassing start, wordt het opgegeven adaptieve formulier weergegeven.</p> <p><strong> Nota </strong>: De toepassingen van het werkschema steunen geen vormen en documenten van PDF die langer zijn dan één pagina of vereisen scrolling op Apple iPad. Wanneer een toepassing wordt geopend op Apple iPad en het adaptieve formulier of het PDF-document langer is dan een pagina, gaan de formuliervelden en inhoud van de tweede pagina verloren.</p> </td>
  </tr>
  <tr>
   <td>Toegangsgroep</td>
   <td><p>Selecteer een groep. De toepassing is in AEM Inbox alleen zichtbaar voor de leden van de geselecteerde groep. Met de optie voor toegangsgroepen maakt u alle groepen van de [!DNL workflow-users] -groep beschikbaar voor selectie. </p> <br /> </td>
  </tr>
  <tr>
   <td>Prefill-service</td>
   <td>Selecteer de a <a href="prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank"> prefill dienst </a> voor de Aangepaste Vorm.<br /> </td>
  </tr>
  <tr>
   <td>Workflowmodel</td>
   <td>Selecteer het model van het a <a href="aem-forms-workflow.md#create-a-workflow-model"> werkschema </a> voor de toepassing. Een workflowmodel bestaat uit logica en stroom van het bedrijfsproces. </td>
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

* [Een toepassing verzenden vanuit AEM Inbox](#inbox)
* [Het voorleggen van een toepassing van  [!DNL AEM Forms]  App](#afa)

* [Een adaptief formulier verzenden](#af)
* [Gecontroleerde map gebruiken](#watched)

* [Een interactieve communicatie of een brief indienen](#letter)

### Een toepassing verzenden vanuit AEM Inbox {#inbox}

De workflowtoepassing die u hebt gemaakt, is beschikbaar als een toepassing in Inbox. Gebruikers die lid zijn van een [!DNL workflow-users] -groep, kunnen de toepassing die de bijbehorende workflow activeert, invullen en verzenden.

<!-- ### Submitting an application from [!DNL AEM Forms] App {#afa}

The [!DNL AEM Forms] app syncs with an [!DNL AEM Forms] server and lets you change the form data, tasks, workflow applications, and saved information (drafts/templates) in your account. For more information, see [[!DNL AEM Forms] app]((aem-forms-app.md) and related articles.-->

### Een adaptief formulier verzenden {#af}

U kunt de verzendhandelingen van een adaptief formulier zo configureren dat een workflow wordt gestart bij het verzenden van het adaptieve formulier. De adaptieve Forms verstrekt **aanhalen een Werkschema van AEM** Actie voorleggen om een werkschema op voorlegging van een Aangepast Vorm te beginnen. Voor gedetailleerde informatie over Submit Actie, zie [&#x200B; Vormend de Submit Actie &#x200B;](configuring-submit-actions.md). Als u een adaptief formulier wilt verzenden via de app [!DNL AEM Forms] , schakelt u Synchroniseren met [!DNL AEM Forms] -toepassing in de eigenschappen van het adaptieve formulier in.

<!-- You can configure an Adaptive Form to sync, submit, and trigger a workflow from [!DNL AEM Forms] app. For details, see [working with a form]((working-with-form.md). -->

<!-- ### Using a watched folder {#watched}

An administrator (a member of fd-administrators group) can configure a network folder to run a pre-configured workflow when a user places a file (such as a PDF file) in the folder. After the workflow completes, it can save the result file to a specified output folder. Such a folder is known as [Watched Folder](watched-folder-in-aem-forms.md). Perform the following procedure to configure a watched folder to launch a workflow:

1. On your AEM author instance, go to ![tools-1](assets/tools-1.png) > **[!UICONTROL Forms]** > **[!UICONTROL Configure Watched Folder]**. A list of already configured watched folders is displayed.
1. Select **[!UICONTROL New]**. A list of fields is displayed. Specify a value for the following fields to configure a Watched Folder for a workflow:

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

1. Select **Advanced**. Specify a value for the following field and taps **Create**. The Watched Folder is configured to launch a workflow. Now, whenever a file is placed in the input directory of the Watched Folder, the specified workflow is triggered.

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
1. Open the **[!UICONTROL Day CQ Mail Service]** configuration. Specify a value for the **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]**, and **[!UICONTROL "From" address]** fields. Click **[!UICONTROL Save]**.
1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual hostname/IP address and port number for local, author, and publish instances. Click **[!UICONTROL Save]**. -->

### Workflowinstanties wissen {#purge-workflow-instances}

Door het minimaliseren van het aantal workflowexemplaren worden de prestaties van de workflow-engine verbeterd, zodat u regelmatig voltooide of actieve workflowexemplaren uit de repository kunt verwijderen. Voor gedetailleerde informatie zie, [&#x200B; Regelmatige het Schrappen van de Instanties van het Werkschema &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/operations/maintenance.html) het zuiveren van werkschemainstanties
