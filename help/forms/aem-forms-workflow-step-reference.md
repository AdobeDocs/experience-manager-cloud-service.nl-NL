---
title: 'Hoe kan ik een workflow toewijzen aan andere gebruikers, e-mail verzenden en Adobe Sign gebruiken in een workflow? '
description: Met Forms-gerichte workflows kunt u snel adaptieve, op Forms gebaseerde workflows maken. Met Adobe Sign kunt u documenten elektronisch ondertekenen, op formulieren gebaseerde bedrijfsprocessen maken, gegevens ophalen en verzenden naar meerdere gegevensbronnen en e-mailmeldingen verzenden
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
source-git-commit: 895290aa0080e159549cd2de70f0e710c4a0ee34
workflow-type: tm+mt
source-wordcount: '4939'
ht-degree: 0%

---

# Forms-centric AEM Workflows - Step Reference {#forms-centric-workflow-on-osgi-step-reference}

U gebruikt workflowmodellen om een bedrijfslogica om te zetten in een geautomatiseerd, zich herhalend proces. Met behulp van een model kunt u een reeks stappen definiëren en uitvoeren. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt. U kunt [omvat diverse AEM stappen van het Werkschema in een model om bedrijfslogica te bereiken](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem).

## Forms-centric stappen {#forms-workflow-steps}

Forms-centric workflowstappen voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel een op Adaptive Forms gebaseerde Forms-gerichte workflow bouwen op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne processen en bedrijfsprocessen binnen de firewall. U kunt ook stappen van de Forms Workflow gebruiken om:

* Maak bedrijfsprocessen, workflows na verzending en back-endworkflows om inschrijvingsprocessen te beheren.

* Taken maken en toewijzen aan een gebruiker of groep.

* Gebruiken [!DNL Adobe Sign] in een AEM Workflow om een document voor ondertekening te verzenden.

* Genereer een document van Record op aanvraag of bij het verzenden van het formulier.

* Verbind een werkschemamodel met diverse gegevensbronnen om gegevens gemakkelijk te bewaren en terug te winnen.

* Gebruik de stap E-mail om meldingen en andere bijlagen te verzenden wanneer een actie is voltooid en wanneer een workflow is gestart of voltooid.

>[!NOTE]
>
>Als het workflowmodel is gemarkeerd voor externe opslag, kunt u voor alle Forms-workflowstappen alleen de optie voor het opslaan of ophalen van gegevensbestanden en bijlagen selecteren.


## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen maakt een tijdelijk item en wijst dit toe aan een gebruiker of groep. Naast het toewijzen van de taak geeft de component ook het adaptieve formulier of de niet-interactieve PDF voor de taak op. Het adaptieve formulier is vereist voor het accepteren van invoer van gebruikers en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie bestemd zijn.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch Document van Verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **[!UICONTROL Title]**: Titel van de taak. De titel wordt weergegeven in AEM Postvak IN.
* **[!UICONTROL Description]**: Uitleg van de bewerkingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **[!UICONTROL Thumbnail Path]**: Pad van de taakminiatuur. Als er geen pad is opgegeven, wordt voor een standaardminiatuur van een adaptief formulier en voor Document of Record een standaardpictogram weergegeven.
* **[!UICONTROL Workflow Stage]**: Een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Selecteren > Pagina > Pagina-eigenschappen > Staven).
* **[!UICONTROL Priority]**: De geselecteerde prioriteit wordt getoond in AEM Inbox. De beschikbare opties zijn Hoog, Normaal en Laag. De standaardwaarde is Normaal.
* **[!UICONTROL Due Date]**: Geef het aantal dagen of uren op waarna de taak achterstallig is. Als u **[!UICONTROL Off]** En dan is de taak nooit achterstallig. U kunt ook een time-outhandler opgeven om specifieke taken uit te voeren nadat de taak is uitgevoerd.

* **[!UICONTROL Days]**: Het aantal dagen voordat de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker is toegewezen. Als een taak niet volledig is en het aantal dagen overschrijdt specificeert op het gebied van Dagen, dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de vervaldatum.
* **[!UICONTROL Hours]**: Het aantal uren voordat de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren overschrijdt specificeert op het gebied van Uren, dan, als geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **[!UICONTROL Time-out after Due Date]**: Selecteer deze optie om het selectieveld Tijdlijnafhandeling in te schakelen.
* **[!UICONTROL Timeout Handler]**: Selecteer het script dat moet worden uitgevoerd wanneer de taakstap voor toewijzen de gewenste datum overschrijdt. Scripts geplaatst in de CRX-opslagplaats op [apps]/fd/dashboard/scripts/timeoutHandler zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt.
* **[!UICONTROL Highlight the action and comment from the last task in Task Details]**: Selecteer deze optie om de laatste actie weer te geven die is uitgevoerd en de opmerking die is ontvangen in de sectie met taakdetails van een taak.
* **[!UICONTROL Type]**: Kies het type document dat moet worden ingevuld wanneer de workflow wordt gestart. U kunt een adaptief formulier kiezen, een alleen-lezen adaptief formulier, een niet-interactief PDF-document. <!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->
* **[!UICONTROL Use Adaptive Form]**: Geef de methode op waarmee u het invoeradaptieve formulier wilt vinden. Deze optie is beschikbaar als u Adaptief formulier of Alleen-lezen adaptief formulier in de vervolgkeuzelijst Type selecteert. U kunt het Adaptief formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is in een absoluut pad of dat beschikbaar is in een pad in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven.\
   U kunt meerdere Adaptive Forms aan een workflow koppelen. Hierdoor kunt u bij uitvoering een adaptief formulier opgeven met de beschikbare invoermethoden.

<!-- 
* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  -->

* **[!UICONTROL Adaptive Form Path]**: Geef het pad van het adaptieve formulier op.<!--  or Interactive Communication.--> U kunt het adaptieve formulier gebruiken <!-- or interactive communication --> die naar de workflow wordt verzonden, beschikbaar via een absoluut pad, of het Adaptief formulier ophalen via een pad dat is opgeslagen in een variabele van het type tekenreeksgegevens.
* **[!UICONTROL Select input PDF using]**: Geef het pad op van een niet-interactief PDF-document. Het veld is beschikbaar wanneer u een niet-interactief PDF-document kiest in het veld Type. U kunt de invoer-PDF selecteren met behulp van het pad dat relatief is ten opzichte van de payload, opgeslagen op een absoluut pad of met behulp van een variabele van het gegevenstype Document. Bijvoorbeeld: [Payload_Directory]/Workflow/PDF/credit-card.pdf. Het pad bestaat niet in crx-repository. Een beheerder maakt het pad voordat het wordt gebruikt. U hebt een Document of Record-optie ingeschakeld of op een formuliersjabloon gebaseerde Adaptieve Forms nodig om de optie PDF-pad te kunnen gebruiken.
* **[!UICONTROL For completed task, render the Adaptive Form as]**: Als een taak is gemarkeerd als voltooid, kunt u het adaptieve formulier weergeven als een alleen-lezen adaptief formulier of als een PDF-document. U hebt een Document of Record-optie ingeschakeld of op een formuliersjabloon gebaseerde Adaptieve Forms nodig om het Adaptief formulier weer te geven als Document of Record.
* **[!UICONTROL Pre-populated]**: De volgende velden die hieronder worden vermeld, dienen als invoer voor de taak:

   * **[!UICONTROL Select input data file using]**: Pad van invoergegevensbestand (.json, .xml, .doc of formuliergegevensmodel). U kunt het invoergegevensbestand terugwinnen gebruikend een weg die met betrekking tot de lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Het bestand bevat bijvoorbeeld de gegevens die via een AEM Inbox-toepassing voor het formulier zijn verzonden. Een voorbeeldpad is [Payload_Directory]/workflow/gegevens.
   * **[!UICONTROL Select input attachments using]**: Bijlagen die op de locatie beschikbaar zijn, worden gekoppeld aan het formulier dat aan de taak is gekoppeld. Het pad kan relatief zijn ten opzichte van de lading of de bijlage ophalen die is opgeslagen in een variabele van een document. Een voorbeeldpad is [Payload_Directory]/bijlagen/. U kunt bijlagen opgeven die relatief zijn ten opzichte van de lading of een variabele van het documenttype (Array-lijst > Document) gebruiken om een invoerbijlage op te geven voor het adaptieve formulier.

   <!-- * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. -->
   * **[!UICONTROL Request Attribute Mapping]**: In het gedeelte Aanvraagkenmerktoewijzing kunt u het volgende definiëren: [naam en waarde van het aanvraagkenmerk](work-with-form-data-model.md#bindargument). Haal de details van de gegevensbron op die op de attributennaam en waarde wordt gebaseerd in het verzoek wordt gespecificeerd. U kunt een waarde van het verzoekattribuut bepalen gebruikend een letterlijke waarde of een variabele van het gegevenstype van het Koord.

   <!--  The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. -->

* **[!UICONTROL Submitted information]**: De volgende velden die hieronder worden vermeld, fungeren als uitvoerlocaties voor de taak:

   * **[!UICONTROL Save output data file using]**: Sla het gegevensbestand op (.json, .xml, .doc of het gegevensmodel van het formulier). Het gegevensbestand bevat informatie die via het bijbehorende formulier is verzonden. U kunt het uitvoergegevensbestand opslaan met een pad dat relatief is ten opzichte van de lading of dit opslaan in een variabele van het gegevenstype Document, XML of JSON. Bijvoorbeeld: [Payload_Directory]/Workflow/data, waarbij de gegevens een bestand zijn.
   * **[!UICONTROL Save attachments using]**: Sla de formulierbijlagen in een taak op. U kunt de bijlagen opslaan met een pad dat relatief is ten opzichte van de lading of deze opslaan in een arraylijst van het gegevenstype Document.
   * **[!UICONTROL Save Document of Record using]**: Pad om een document van een recordbestand op te slaan. Bijvoorbeeld: [Payload_Directory]/DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u **[!UICONTROL Relative to Payload]** wordt het document of record niet gegenereerd als het padveld leeg blijft. Deze optie is alleen beschikbaar als u Adaptief formulier selecteert in de vervolgkeuzelijst Type.

   <!-- * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. -->

* **[!UICONTROL Assignee]** > **[!UICONTROL Assign options]**: Geef de methode op waarmee de taak aan een gebruiker wordt toegewezen. U kunt de taak dynamisch toewijzen aan een gebruiker of groep met behulp van het script Deelnemerkiezer of u kunt de taak toewijzen aan een specifieke AEM gebruiker of groep.
* **[!UICONTROL Participant Chooser]**: De optie is beschikbaar wanneer de optie **[!UICONTROL Dynamically to a user or group]** is geselecteerd in het veld Opties toewijzen. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Zie voor meer informatie [Een workflow dynamisch toewijzen aan de gebruikers](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [Een aangepaste stap voor Adobe Experience Manager Dynamic Participant maken.](https://docs.adobe.com/content/help/en/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?CID=RedirectAEMCommunityKautuk)

* **[!UICONTROL Participants]**: Het veld is beschikbaar wanneer de **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** is geselecteerd in het dialoogvenster **[!UICONTROL Participant Chooser]** veld. In het veld kunt u gebruikers of groepen selecteren voor de optie RandomParticipantChooser.

* **[!UICONTROL Assignee]**: Het veld is beschikbaar wanneer de **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** is geselecteerd in het dialoogvenster **[!UICONTROL Participant Chooser]** veld. In het veld kunt u een variabele van het gegevenstype String selecteren om de toewijzing te definiëren.

* **[!UICONTROL Arguments]**: Het veld is beschikbaar wanneer een ander script dan het script RandomParticipantChoose is geselecteerd in het veld Deelnemerkiezer. In het veld kunt u een lijst met door komma&#39;s gescheiden argumenten opgeven voor het script dat is geselecteerd in het veld Deelnemerkiezer.

* **[!UICONTROL User or Group]**: De taak wordt toegewezen aan de geselecteerde gebruiker of groep. De optie is beschikbaar wanneer de optie **[!UICONTROL To a specific user or group option]** is geselecteerd in het dialoogvenster **[!UICONTROL Assign options]** veld. In het veld worden alle gebruikers en groepen van de [!DNL workflow-users] groep.\
   De **[!UICONTROL User or Group]** drop-down menu maakt een lijst van de gebruikers en de groepen die de het programma geopende gebruiker toegang heeft tot. De weergave van de gebruikersnaam is afhankelijk van het feit of u toegangsmachtigingen hebt voor de **[!UICONTROL users]** knooppunt in crx-repository voor die bepaalde gebruiker.

* **[!UICONTROL Send Notification Email]**: Selecteer deze optie als u e-mailberichten wilt verzenden naar de ontvanger. Deze meldingen worden verzonden wanneer een taak wordt toegewezen aan een gebruiker of een groep. U kunt de **[!UICONTROL Recipient Email Address]** om het mechanisme voor het ophalen van het e-mailadres op te geven.

* **[!UICONTROL Recipient Email Address]**: U kunt e-mailadres in een variabele opslaan, letterlijk een permanent e-mailadres opgeven of standaard e-mailadres gebruiken van de ontvanger die is opgegeven in het profiel van de ontvanger. U kunt de letterlijke waarde of een variabele gebruiken om het e-mailadres van een groep op te geven. De optie Variabele is handig bij het dynamisch ophalen en gebruiken van een e-mailadres. De **[!UICONTROL Use default email address of the assignee]** Deze optie geldt slechts voor één enkele ontvanger. In dit geval wordt het e-mailadres gebruikt dat is opgeslagen in het gebruikersprofiel van de toewijzing.

* **[!UICONTROL HTML Email Template]**: Selecteer een e-mailsjabloon voor het e-mailbericht. Als u een sjabloon wilt bewerken, wijzigt u het bestand op /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in de crx-repository.
* **[!UICONTROL Allow Delegation To]**: AEM Inbox verstrekt een optie aan de het programma geopende gebruiker om het toegewezen werkschema aan een andere gebruiker te delegeren. U kunt delegeren binnen dezelfde groep of aan de werkschemagebruiker van een andere groep. Als de taak aan één gebruiker wordt toegewezen en **[!UICONTROL allow delegation to members of the assignee group]** wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of een groep te delegeren.
* **[!UICONTROL Share Settings]**: AEM Inbox biedt opties om één of alle taken in het Postvak IN te delen met andere gebruikers:
   * Wanneer de **[!UICONTROL Allow assignee to share explicitly in inbox]** is geselecteerd, kan de gebruiker de taak in AEM Postvak In selecteren en deze delen met een andere AEM.
   * Wanneer de **[!UICONTROL Allow assignee to share via inbox sharing]** is geselecteerd en gebruikers hun Postvak IN-items delen of andere gebruikers toegang geven tot hun Postvak IN-items. Alleen taken waarvoor de optie is ingeschakeld, worden met andere gebruikers gedeeld.
   * Wanneer de **[!UICONTROL Allow assignee to delegate using 'Out of Office' settings]** is geselecteerd. De ontvanger kan de optie toelaten om de taak aan andere gebruikers samen met andere uit opties van het Bureau te delegeren. Om het even welke nieuwe die taken aan de uit-van-bureaugebruiker worden toegewezen worden automatisch gedelegeerd (toegewezen) aan de gebruikers in uit-van-bureaumontages worden vermeld.

   Het staat andere gebruikers toe om toewijstaken te kiezen terwijl buiten bureau is en niet aan toegewezen taken kan werken.

* **[!UICONTROL Actions]** > **[!UICONTROL Default Actions]**: De acties Verzenden, Opslaan en Herstellen zijn beschikbaar in het vak. Standaard zijn alle standaardhandelingen ingeschakeld.
* **[!UICONTROL Route Variable]**: Naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **[!UICONTROL Routes]**: Een taak kan zich aan verschillende routes vertakken. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt routes opslaan in een variabele van een gegevenstype String of **[!UICONTROL Literal]** om routes manueel toe te voegen.

* **[!UICONTROL Route Title]**: Specificeer de titel voor de route. Deze wordt weergegeven in AEM Postvak IN.
* **[!UICONTROL Coral Icon]**: Geef het HTML-kenmerk van een koraalpictogram op. De Adobe CorelUI-bibliotheek biedt een uitgebreide set aanraakpictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Deze wordt samen met de titel in AEM Inbox weergegeven. Als u de routes in een variabele opslaat, gebruiken de routes een standaard &quot;Tags&quot;koraalpictogram.
* **[!UICONTROL Allow assignee to add comment]**: Selecteer deze optie als u opmerkingen voor de taak wilt inschakelen. Een toegewezen persoon kan de opmerkingen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden.
* **[!UICONTROL Save comment in variable]**: Sla de opmerking op in een variabele van het gegevenstype String. Deze optie wordt alleen weergegeven als u **[!UICONTROL Allow assignee to add comment]** selectievakje.

* **[!UICONTROL Allow assignee to add attachments to the task]**: Selecteer deze optie om bijlagen in te schakelen voor de taak. Een toegewezen persoon kan de bijlagen toevoegen vanuit AEM Postvak In op het moment dat de taak wordt verzonden. U kunt ook de maximumgrootte beperken **[!UICONTROL (Maximum File Size)]** van een bijlage. De standaardgrootte is 2 MB.

* **[!UICONTROL Save output task attachments using]**: Geef de locatie van de map met bijlagen op. U kunt uitvoertaakbijlagen opslaan met een pad dat is gebaseerd op de laadbewerking of met een variabele van een array van documentgegevenstype. Deze optie wordt alleen weergegeven als u **[!UICONTROL Allow assignee to add attachments to the task]** Selectievakje en selecteer **[!UICONTROL Adaptive Form]**, **[!UICONTROL Read-only Adaptive Form]**, of **[!UICONTROL Non-interactive PDF document]** van de **[!UICONTROL Type]** vervolgkeuzelijst in het dialoogvenster **[!UICONTROL Form/Document]** tab.

* **[!UICONTROL Use custom metadata]**: Selecteer deze optie om het veld Aangepaste metagegevens in te schakelen. Aangepaste metagegevens worden gebruikt in e-mailsjablonen.
* **[!UICONTROL Custom Metadata]**: Selecteer aangepaste metagegevens voor de e-mailsjablonen. De aangepaste metagegevens zijn beschikbaar in de crx-gegevensopslagruimte op apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt. U kunt ook een service gebruiken voor de aangepaste metagegevens. U kunt ook het dialoogvenster `WorkitemUserMetadataService` interface voor aangepaste metagegevens.
* **[!UICONTROL Show Data from Previous Steps]**: Schakel deze optie in als u wilt dat toewijzen vorige toewijzingen, reeds ondernomen actie op de taak, aan de taak toegevoegde opmerkingen en Document of Record van de voltooide taak kunnen weergeven, indien beschikbaar.
* **[!UICONTROL Show Data from Subsequent Steps]**: Selecteer deze optie om de huidige toegewezen persoon in staat te stellen de actie te bekijken die is ondernomen en de opmerkingen die aan de taak zijn toegevoegd door de volgende toegewezen personen. Het staat ook de huidige toegewezen persoon toe om een Document van Verslag van de voltooide taak te bekijken, als beschikbaar.
* **[!UICONTROL Visibility of data type]**: Standaard kan een toegewezen persoon een document met records, toewijzingen, ondernomen actie en opmerkingen bekijken die door eerdere en volgende toewijzingen zijn toegevoegd. Gebruik de zichtbaarheid van de optie Gegevenstype om het type gegevens te beperken dat zichtbaar is voor de ontvangers.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen worden onbruikbaar gemaakt wanneer u een AEM werkschemamodel voor externe gegevensopslag vormt. In Postvak In is bovendien de optie voor opslaan uitgeschakeld.

## E-mailstap verzenden {#send-email-step}

Gebruik de stap E-mail om een e-mail te verzenden, bijvoorbeeld een e-mail met een Document of Record, koppeling van een adaptief formulier <!-- , link of an interactive communication-->of met een bijgevoegd PDF-document. E-mailstapondersteuning verzenden [HTML-e-mail](https://en.wikipedia.org/wiki/HTML_email). HTML e-mailberichten reageren en passen zich aan de e-mailclient en schermgrootte van de ontvangers aan. Met een e-mailsjabloon voor HTML kunt u de weergave, het kleurenschema en het gedrag van de e-mail definiëren.

In de e-mailstap wordt de Day CQ Mail Service gebruikt om e-mailberichten te verzenden. Controleer voordat u de e-mailstap gebruikt of de e-mailservice is geconfigureerd. E-mailondersteuning biedt standaard alleen HTTP- en HTTP-protocollen. [Contact opnemen met het ondersteuningsteam](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=en#sending-email) om havens voor het verzenden van e-mail toe te laten en SMTP protocol voor uw milieu toe te laten. De beperking helpt de beveiliging van het platform te verbeteren.

De e-mailstap heeft de volgende eigenschappen:

**[!UICONTROL Title]**: De titel van de stap helpt de stap in de werkstroomeditor te identificeren.

**[!UICONTROL Description]**: Uitleg is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**[!UICONTROL Email Subject]**: Onderwerp kan uit een werkschemameta-gegevens worden teruggewonnen, manueel worden gespecificeerd, of van de waarde worden teruggewonnen die in een variabele wordt opgeslagen. Selecteer een van de volgende opties:

* **[!UICONTROL Literal]** Geef een onderwerp handmatig op.
* **[!UICONTROL Retrieve from Workflow metadata]** - Haal het onderwerp op uit een eigenschap metadata.
* **[!UICONTROL Variable]** - Haal het onderwerp op uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

**[!UICONTROL HTML Email Template]**: HTML sjabloon voor e-mail. U kunt variabelen in een e-mailsjabloon opgeven. De E-mailstap extraheert en geeft alle variabelen weer die in een sjabloon zijn opgenomen voor invoer.

**[!UICONTROL Email Template Metadata]**: De waarde van de sjabloonvariabelen voor e-mail kan een door de gebruiker opgegeven waarde zijn, het pad van een element op de auteur of de publicatieserver, afbeelding of eigenschap voor metagegevens van de workflow.

* **[!UICONTROL Literal]**: Gebruik deze optie als u precies weet welke waarde u moet opgeven. Bijvoorbeeld: [example@example.com](mailto:example@example.com).

* **[!UICONTROL Workflow Metadata]**: Gebruik de optie wanneer de te gebruiken waarde in een werkschemabezit wordt opgeslagen. Nadat u de optie hebt geselecteerd, typt u de naam van de eigenschap metadata in het lege tekstvak onder de optie Metagegevens werkstroom. Bijvoorbeeld emailAddress.

<!-- * **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. -->
* **[!UICONTROL Image]**: Gebruik de optie om een afbeelding in te sluiten in de e-mail. Blader en kies de afbeelding nadat u de optie hebt geselecteerd. De afbeeldingsoptie is alleen beschikbaar voor de afbeeldingstags (&lt;img src=&quot;*&quot; />) die beschikbaar zijn in de e-mailsjabloon.

**[!UICONTROL Sender’s / Recipient's Email Address]**: Selecteer **[!UICONTROL Literal]** om handmatig een e-mailadres op te geven of selecteer de optie **[!UICONTROL Retrieve from Workflow metadata]** om het e-mailadres op te halen uit een eigenschap metadata. U kunt ook een lijst met arrays met metagegevenseigenschappen opgeven voor de **[!UICONTROL Retrieve from Workflow metadata]** optie. Selecteer **[!UICONTROL Variable]** om het e-mailadres op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

* **[!UICONTROL File Attachment]**: Het middel dat op de opgegeven locatie beschikbaar is, wordt als bijlage aan de e-mail toegevoegd. Het pad van het element kan relatief zijn ten opzichte van de payload of het absolute pad. Een voorbeeldpad is [Payload_Directory]/bijlagen/.

Selecteer **[!UICONTROL Variable]** om de bestandsbijlage op te halen die is opgeslagen in een variabele van het gegevenstype Document, XML of JSON.

**[!UICONTROL File Name]**: Naam van het bestand met e-mailbijlagen. Met de E-mailstap wijzigt u de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan handmatig worden opgegeven of opgehaald uit een eigenschap voor metagegevens van een workflow of een variabele. Gebruik de **[!UICONTROL Literal]** als u precies weet welke waarde u moet opgeven. Gebruik de **[!UICONTROL Variable]** om de bestandsnaam op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Gebruik de **[!UICONTROL Retrieve from a Workflow Metadata]** als de te gebruiken waarde wordt opgeslagen in een werkstroommetagegevenseigenschap.

## Document met recordstap genereren {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Deze record wordt een Document of Record (DoR) genoemd. Met de stap Document van record genereren kunt u een alleen-lezen of interactieve PDF versie van een adaptief formulier maken. De PDF-versie bevat informatie die in het formulier is ingevuld en de indeling van het adaptieve formulier.

De stap Document of Record heeft de volgende eigenschappen:

**[!UICONTROL Use Adaptive Form]**: Geef de methode op waarmee u het invoeradaptieve formulier wilt vinden. U kunt het Adaptief formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is in een absoluut pad of dat beschikbaar is in een pad in een variabele. U kunt een variabele van het gegevenstype String gebruiken om het pad op te geven in het dialoogvenster **[!UICONTROL Select variable to resolve]** veld.\
U kunt meerdere Adaptive Forms aan een workflow koppelen. Hierdoor kunt u bij uitvoering een adaptief formulier opgeven met de beschikbare invoermethoden.

**[!UICONTROL Adaptive Form Path]**: Geef het pad van het adaptieve formulier op. Het veld is beschikbaar wanneer u de optie **[!UICONTROL Available at an absolute path]** van de **[!UICONTROL Use Adaptive Form]** veld.

**[!UICONTROL Select Input data using]**: Pad van de invoergegevens voor het adaptieve formulier. U kunt de gegevens op een plaats met betrekking tot de lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het Adaptief formulier om een Document of Record te maken.

**[!UICONTROL Select Input attachment path using]**: Pad van de bijlagen. Deze bijlagen worden opgenomen in het document of record. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.

Als u bijvoorbeeld het pad van een map opgeeft, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, gekoppeld aan het document met records. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document of Record. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

**[!UICONTROL Save Generated Document of Record using below options]**: Geef de locatie op waar u een document van een recordbestand wilt bewaren. U kunt ervoor kiezen om de payload-map te overschrijven, Document of Record op een locatie in de payload-map te plaatsen of het Document of Record op te slaan in een variabele van het documentgegevenstype.

**[!UICONTROL Locale]**: Geef de taal van het document met records op. Selecteren **[!UICONTROL Literal]** om de landinstelling te selecteren in een vervolgkeuzelijst of selecteer **[!UICONTROL Variable]** om de landinstelling op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. U moet de landinstellingscode definiëren terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **nl_NL** voor het Engels en **fr_FR** voor Frans.

## De stap Service van het formuliergegevensmodel aanroepen {#invoke-form-data-model-service-step}

U kunt [[!DNL AEM Forms] Gegevensintegratie](data-integration.md) om te vormen en met ongelijksoortige gegevensbronnen te verbinden. Deze gegevensbronnen kunnen de Webdienst, de dienst van REST, de dienst van OData, en oplossing van CRM zijn. [!DNL AEM Forms] De Integratie van gegevens staat u toe om een Model van de Gegevens van de Vorm te creëren dat de diverse diensten omvat om gegevensherwinning uit te voeren, toevoeging, het bijwerken verrichtingen op het gevormde gegevensbestand. U kunt de **[!UICONTROL Invoke Data Model Service step]** om een Model van de Gegevens van de Vorm (FDM) te selecteren en de diensten van FDM te gebruiken om, gegevens terug te winnen bij te werken of toe te voegen aan ongelijksoortige gegevensbronnen.

Om input voor gebieden van de stap te verklaren, worden de volgende gegevensbestandlijst en het dossier JSON gebruikt als voorbeeld:

**[!UICONTROL Sample CustomerDetails table]**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Waarde<br /> </td> 
  </tr> 
  <tr> 
   <td>FirstName<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>LastName</td> 
   <td>Roze</td> 
  </tr> 
  <tr> 
   <td>Klant-id</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>E-mailadres<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**[!UICONTROL Sample JSON file]**

```json
  { 
    customer: { 
     firstName: "Sarah", 
     lastName:"Rose", 
     customerId: "1", 
     emailAddress:"srose@we.info" 
   }, 
    insurance: {
     customerId: "1", 
    policyType: "Premium,
    policyNumber: "Premium-521499",
    customerDetails: { 
     firstName: "Sarah",
     lastName: "Rose",
     customerId: "1",
     emailAddress: "srose@we.info" 
    }
   }
  }
```

Voor de stap Service van het formuliergegevensmodel aanroepen worden de onderstaande velden weergegeven om bewerkingen in het formuliergegevensmodel te vergemakkelijken:

* **[!UICONTROL Title]**: Titel van de stap. Het helpt de stap in de werkschemaredacteur identificeren.
* **[!UICONTROL Description]**: Uitleg nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **[!UICONTROL Form Data Model Path]**: Blader naar en selecteer een formuliergegevensmodel dat op de server aanwezig is.

* **[!UICONTROL Errors and Validations]**: Met deze optie kunt u foutberichten vastleggen en validatieopties opgeven voor gegevens die worden opgehaald en naar gegevensbronnen worden verzonden. Met deze veranderingen, kunt u gegevens verzekeren die tot de Invoke stap van de Dienst van het Gegevensmodel van de Vorm worden overgegaan voldoet aan de gegevensbeperkingen die door gegevensbron worden bepaald. Zie voor meer informatie [Geautomatiseerde validatie van invoergegevens](work-with-form-data-model.md#automated-validation-of-input-data)

* **[!UICONTROL Validation level]**: Er zijn drie validatiecategorieën: Standaard, Volledig en UIT:

   * Volledig: Alle beperkingen worden gevalideerd.
   * Eenvoudig: Alleen vereiste en nulbare beperkingen
   * UIT: Er vindt geen validatie plaats.

* **[!UICONTROL Terminate Workflow on Failure]**: Wanneer een beperking niet kan worden gevalideerd, wordt de workflow gestopt.

* **[!UICONTROL Store Error Code in Variable]**: U kunt een foutcode opslaan in een [Variabele van het type String](variable-in-aem-workflows.md).

* **[!UICONTROL Store Error Message in Variable]**: U kunt een foutbericht opslaan in een [Variabele van het type String](variable-in-aem-workflows.md).

* **[!UICONTROL Store Error Details in Variable]**: U kunt foutgegevens opslaan in een [Variabele van het type JSON](variable-in-aem-workflows.md).

* **[!UICONTROL Service]**: Lijst met services die worden geleverd door het geselecteerde formuliergegevensmodel.
* **[!UICONTROL Input for services]** > **[!UICONTROL Provide input data using literal, variable, or workflow metadata, and a JSON file]**: Een service kan meerdere argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten van een werkschemabezit, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **[!UICONTROL Literal]**: Gebruik deze optie als u precies weet welke waarde u moet opgeven. Bijvoorbeeld srose@we.info.
   * **[!UICONTROL Variable]**: Gebruik de optie om de waarde op te halen die in een variabele is opgeslagen.
   * **[!UICONTROL Retrieve from Workflow Metadata]**: Gebruik de optie wanneer de te gebruiken waarde in een werkschemabezit wordt opgeslagen. Bijvoorbeeld emailAddress.

   * **[!UICONTROL Relative to Payload]**: Gebruik de optie om de bestandsbijlage op te halen die is opgeslagen op een pad dat relatief is ten opzichte van de laadbewerking. Selecteer de optie en geef de mapnaam op die de bestandsbijlage bevat of geef de naam van de bestandsbijlage op in het tekstvak.

      Als de map Relatief aan Payload in de CRX-opslagplaats bijvoorbeeld een bestandsbijlage bevat in de `attachment\attachment-folder` locatie, opgeven `attachment\attachment-folder` in het tekstvak nadat u de **[!UICONTROL Relative to Payload]** optie.

   * **[!UICONTROL JSON Dot Notation]**: Gebruik deze optie als de te gebruiken waarde zich in een JSON-bestand bevindt. Bijvoorbeeld verzekering.customerDetails.emailAddress. De optie Puntnotatie JSON is alleen beschikbaar als de optie Invoervelden toewijzen van de invoeroptie JSON is geselecteerd.
   * **[!UICONTROL Map input fields from input JSON]**: Geef het pad van een JSON-bestand op om de invoerwaarde van bepaalde serviceargumenten op te halen uit het JSON-bestand. Het pad van het JSON-bestand kan relatief zijn ten opzichte van de payload, een absoluut pad of u kunt een invoer-JSON-document selecteren met een variabele van het type JSON- of Formuliergegevensmodel.

* **[!UICONTROL Input for services]** > **[!UICONTROL Provide input data using variable or a JSON file]**: Selecteer de optie om waarden voor alle argumenten op te halen uit een JSON-bestand dat is opgeslagen op een absoluut pad, een pad dat relatief is ten opzichte van de payload of een variabele.
* **[!UICONTROL Select Input JSON document using]**: Het JSON-bestand met waarden voor alle serviceargumenten. Het pad van het JSON-bestand kan **[!UICONTROL relative to the payload]** of **[!UICONTROL absolute path]**. U kunt het invoer-JSON-document ook ophalen met behulp van een variabele van het gegevenstype JSON of Form Data Model.

* **[!UICONTROL JSON Dot Notation]**: Laat het veld leeg als u alle objecten van het opgegeven JSON-bestand als invoer voor serviceargumenten wilt gebruiken. Als u een specifiek JSON-object uit het opgegeven JSON-bestand wilt lezen als invoer voor serviceargumenten, geeft u puntnotatie voor het JSON-object op. Als u bijvoorbeeld een JSON-object hebt dat vergelijkbaar is met de JSON-object dat aan het begin van de sectie wordt vermeld, geeft u Insurance.customerDetails op om alle details van een klant als invoer voor de service op te geven.
* **[!UICONTROL Output of service]** > **[!UICONTROL Map and write output values to variable or metadata]**: Selecteer de optie om de uitvoerwaarden op te slaan als eigenschappen van het metagegevensknooppunt voor workflowinstanties in de crx-repository. Specificeer de naam van het meta-gegevensbezit en selecteer het overeenkomstige attribuut van de de dienstoutput dat met meta-gegevensbezit moet worden in kaart gebracht, bijvoorbeeld, phone_number dat door de outputdienst met het phone_number bezit van werkschemameta-gegevens is teruggekeerd. Op dezelfde manier kunt u de uitvoer opslaan in een variabele van het gegevenstype Long. Wanneer u een eigenschap voor de **[!UICONTROL Service output attribute to be mapped]** optie, alleen variabelen die gegevens van de geselecteerde eigenschap kunnen opslaan, worden gevuld voor de **[!UICONTROL Save the output to]** optie.

* **[!UICONTROL Output of service]** > **[!UICONTROL Save output to variable or a JSON file]**: Selecteer de optie om de uitvoerwaarden in een JSON-bestand op te slaan met een absoluut pad, een pad dat relatief is ten opzichte van de laadtijd of een variabele.
* **[!UICONTROL Save Output JSON document using below options]**: Sla het JSON-uitvoerbestand op. Het pad van het JSON-uitvoerbestand kan relatief zijn ten opzichte van de payload of een absoluut pad. U kunt het JSON-uitvoerbestand ook opslaan met een variabele van het gegevenstype JSON of Form Data Model.

## stap Document ondertekenen {#sign-document-step}

Met de stap Document ondertekenen kunt u [!DNL Adobe Sign] om documenten te ondertekenen. Wanneer u [!DNL Adobe Sign] Workflowstap voor het ondertekenen van een adaptief formulier: het formulier kan door ondertekenaars worden doorgegeven of tegelijkertijd naar alle ondertekenaars worden verzonden, afhankelijk van de configuratie van de workflowstap. [!DNL Adobe Sign] Aangepaste adaptieve Forms worden alleen naar Experience Manager Forms Server verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid.

Standaard worden de [!DNL Adobe Sign] De diensten van de planner controleren (opiniepeilingen) ondertekeningsreactie na om de 24 uur. U kunt [het standaardinterval voor uw omgeving wijzigen](adobe-sign-integration-adaptive-forms.md##configure-adobe-sign-scheduler-to-sync-the-signing-status).

De stap Document ondertekenen heeft de volgende eigenschappen:

* **[!UICONTROL Agreement Name]**: Geef de titel van de overeenkomst op. De naam van de overeenkomst wordt onderdeel van het onderwerp en de hoofdtekst van de e-mail die naar de ondertekenaars wordt verzonden. U kunt de naam opslaan in een variabele van het gegevenstype String of **[!UICONTROL Literal]** om de naam handmatig toe te voegen.

* **[!UICONTROL Locale]**: Geef de taal op voor de opties voor e-mail en verificatie. U kunt de landinstelling opslaan in een variabele van het gegevenstype String of **[!UICONTROL Literal]** om de landinstelling te kiezen in de lijst met beschikbare opties. U moet de landinstellingscode definiëren terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **[!UICONTROL en_US]** voor het Engels en **[!UICONTROL fr_FR]** voor Frans.

* **[!UICONTROL Adobe Sign Cloud Configuration]**: Kies een [!DNL Adobe Sign] Cloudconfiguratie. Als u niet hebt geconfigureerd [!DNL Adobe Sign] for [!DNL AEM Forms], zie [Adobe Sign integreren met [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md).

* **[!UICONTROL Select Document to be signed using]**: U kunt een document kiezen op een locatie die relatief is ten opzichte van de lading, de lading als document gebruiken, een absoluut pad van het document opgeven of het document ophalen dat is opgeslagen in een variabele van het documentgegevenstype.
* **[!UICONTROL Days Until Deadline]**: Een document is gemarkeerd als opeisbaar (verstreken deadline) nadat de taak gedurende het opgegeven aantal dagen niet is geactiveerd in het dialoogvenster **[!UICONTROL Days Until Deadline]** veld. Het aantal dagen wordt geteld nadat het document is toegewezen aan een gebruiker voor ondertekening.
* **[!UICONTROL Reminder Email Frequency]**: U kunt een herinnering per dag of wekelijks e-mail verzenden. De week wordt geteld vanaf de dag waarop de documentatie aan een gebruiker is toegewezen voor ondertekening.
* **[!UICONTROL Signature Process]**: U kunt ervoor kiezen om een document in een opeenvolgende of parallelle volgorde te ondertekenen. Eén ondertekenaar ontvangt het document op volgorde voor ondertekening. Nadat de eerste ondertekenaar het ondertekenen van het document heeft voltooid, wordt het document verzonden naar de tweede ondertekenaar, enzovoort. Parallel hieraan kunnen meerdere ondertekenaars een document tegelijk ondertekenen.
* **[!UICONTROL Redirection URL]**: Geef een omleidings-URL op. Nadat het document is ondertekend, kunt u de ontvanger omleiden naar een URL. Gewoonlijk bevat deze URL een bedankbericht of verdere instructies.
* **[!UICONTROL Workflow Stage]**: Een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model ( **[!UICONTROL Sidekick]** > **[!UICONTROL Page]** > **[!UICONTROL Page Properties]** > **[!UICONTROL Stages]**).
* **[!UICONTROL Select Signers]**: Geef de methode op waarmee u ondertekenaars voor het document wilt kiezen. U kunt de workflow dynamisch toewijzen aan een gebruiker of groep of gegevens van een ondertekenaar handmatig toevoegen.
* **[!UICONTROL Script or service to select signers]**: De optie is alleen beschikbaar als de optie Dynamisch is geselecteerd in het veld Ondertekenaars selecteren. U kunt een ECMAScript of een dienst specificeren om ondertekenaars en verificatieopties voor een document te kiezen.
* **[!UICONTROL Signer Details]**: De optie is alleen beschikbaar als de optie Handmatig is geselecteerd in het veld Ondertekenaars selecteren. Geef een e-mailadres op en kies een optioneel verificatiemechanisme. Voordat u een verificatiemechanisme met twee stappen selecteert, moet u ervoor zorgen dat de bijbehorende verificatieoptie is ingeschakeld voor de geconfigureerde [!DNL Adobe Sign] account. U kunt een variabele van het gegevenstype String gebruiken om waarden voor de velden E-mail, Landcode en Telefoonnummer te definiëren. De velden Landcode en Telefoonnummer worden alleen weergegeven als u Telefoonverificatie selecteert in de vervolgkeuzelijst in twee stappen.

<!-- ## Document Services steps {#document-services-steps}

AEM Document services are a set of services for creating, assembling, and securing PDF Documents. [!DNL AEM Forms] provides a separate AEM Workflow step for each document service.

Similar to other [!DNL AEM Forms] workflow steps, such as Assign Task, Send Email, and Sign Document, you can use variables in all AEM Document services steps. For more information on creating and managing variables, see [Variables in AEM workflows](variable-in-aem-workflows.md).

### Apply Document Time Stamp step {#apply-document-time-stamp-step}

Add time stamp to a document. You provide document details such as input document path, input document name, location to store exported data. You may choose to overwrite existing payload file, choose a different file name to store data in a different file under payload folder, provide an absolute path to the data, or store data in a variable of Document data type.

### Convert to image step {#convert-to-image-step}

Converts a PDF document to list of images. Supported image formats are JPEG, JPEG2000, PNG, and TIFF. The following information applies to conversions to TIFF images:

* A multi-page TIFF file is generated.
* Some annotations are not included in TIFF images. Annotations that require Acrobat to generate their appearance are not included.

### Convert to PDF/A step {#convert-to-pdf-a-step}

Converts a PDF document to PDF/A format using the options provided. The PDF/A version of Portable Document Format (PDF) is specialized for archiving and long-term preservation of documents.

### Convert to PS step {#convert-to-ps-step}

Convert PDF documents to PostScript. When converting to PostScript, you can use the conversion operation to specify the source document and whether to convert to PostScript level 2 or 3. The PDF document you convert to a PostScript file must be non-interactive.

### Create PDF from specified type step {#create-pdf-from-specified-type-step}

Generate a PDF document from an input file. The input document can be relative to the payload, have an absolute path, can be payload itself, or stored in a variable of Document data type.

### Create PDF from URL/HTML/ZIP step {#create-pdf-from-url-html-zip-step}

Generates a PDF document from supplied URL, HTML, and ZIP file.

### Export Data step {#export-data-step}

Exports data from a PDF forms or XDP file. It requires you to enter the file path of Input Document and the Export Data Format. The options for Export Data Format are Auto, XDP and XmlData.

### Export PDF to specified type step {#export-pdf-to-specified-type-step}

Converts a PDF document to a selected format.

### Generate Non-Interactive PDF step {#generatenoninteractive}

Generate a Non-Interactive PDF. It provides various customization options.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Import Data step {#import-data-step}

Merges form data into a PDF form. You can import form data into a PDF form.

### Invoke DDX step {#invokeddx}

Executes the DDX file on the specified map of input documents and returns the manipulated PDF documents.

>[!NOTE]
>
>You can use variables to specify the DDX file for input documents. Store the DDX file in a variable of Document or XML data type.

### Optimize PDF step {#optimize-pdf-step}

Optimizes PDF files by reducing their size. The result of this conversion is PDF files that may be smaller than their original versions. This operation also converts PDF documents to the PDF version specified in the optimization parameters.

Optimization settings specify how files are optimized. Here are example settings:

* Target PDF version
* Discarding objects such as JavaScript actions and embedded page thumbnails
* Discarding user data such as comments and file attachments
* Discarding invalid or unused settings
* Compressing uncompressed data or using more efficient compression algorithms
* Removing embedded fonts
* Setting transparency values

### Render PDF Form step {#renderpdf}

Renders a form created in Form Designer (XDP) to a PDF form.

>[!NOTE]
>
>You can use variables to specify the template file for input documents. Store the path of the template file in a variable of String data type.

### Secure Document step {#secure-document-step}

Encrypt, Sign, and certify a document. [!DNL AEM Forms] supports both password based and certificate base encryption. You can also choose between various algorithms for signing documents. For example, SHA-256 and SH-512. You can also use the workflow step to reader extend PDF documents. The workflow step provides option to enable barcode decoding, digital signatures, import and export of PDF data, and other options.

### Send to Printer step {#send-to-printer-step}

Send a document directly to a printer. It supports the following printing access mechanisms:

* **[!UICONTROL Direct accessible printer]**: A printer that is installed on the same computer is called a direct accessible printer, and the computer is named printer host. This type of printer can be a local printer that is connected to the computer directly.
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX® printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server’s IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.

### Generate Printed Output Step {#generatePrintedOutput}

The step generates a PCL, PostScript, ZPL, IPL, TPCL, or DPL output given a form design and data file. The data file is merged with the form design and formatted for printing. The output generated by this step can be sent directly to a printer or saved as file. It is recommended that you use this step when you want to use form designs or data from an application. If your form designs or form designs are located on the network, local file system, or HTTP location, use the generatePrintedOutput operation operation.

For example, your application requires that you merge a form design with a data file. The data contains hundreds of records. In addition, it requires the output is sent to a printer that supports ZPL. The form design and your input data are located in an application. Use the generatePrintedOutput operation to merge each record with a form design and send the output to a printer that supports ZPL.

The Generate Printed Output step has the following properties:

**[!UICONTROL Input properties]**

* **[!UICONTROL Select template file using]**: Specify the path of the template file. You can select the template file using the path that is relative to the payload, saved at an absolute path, or using a variable of Document data type. For example, [Payload_Directory]/Workflow/data.xml. If the path does not exist in crx-repository, an administrator can create the path before using it. Moreover, you can also accept payload as the input data file.

* **[!UICONTROL Select data document using]**: Specify the path of a input data file. You can select the input data file using the path that is relative to the payload, saved at an absolute path, or using a variable of Document data type. For example, [Payload_Directory]/Workflow/data.xml. If the path does not exist in crx-repository, an administrator can create the path before using it.

* **[!UICONTROL Printer Format]**: A Print Format value that specifies the page description language to use, when an XDC file is not provided, to generate the output stream. If you provide a literal value, select one of these values:

  * **[!UICONTROL Custom PCL]**: Use the option to specify a custom XDC file for PCL.
  * **[!UICONTROL Custom PostScript]**: Use the option to specify a custom XDC file for PostScript.
  * **[!UICONTROL Custom ZPL]**: Use the option to specify a custom XDC file file for ZPL.
  * **[!UICONTROL Generic Color PCL (5c)]**: Use a generic color PCL (5c).
  * **[!UICONTROL Generic PostScript Level3]**: Use generic PostScript Level 3.
  * **[!UICONTROL ZPL 300 DPI]**: Use ZPL 300 DPI. The zpl300.xdc is used.
  * **[!UICONTROL ZPL 600 DPI]**: Use ZPL 600 DPI. The zpl600.xdc file is used.
  * **[!UICONTROL Custom IPL]**: Use the option to specify a custom XDC file for IPL.
  * **[!UICONTROL IPL 300 DPI]**: Use IPL 300 DPI. The ipl300.xdc is used.
  * **[!UICONTROL IPL 400 DPI]**: Use IPL 400 DPI. The ipl400.xdc file is used.
  * **[!UICONTROL Custom TPCL]**: Use the option to specify a custom XDC file for TPCL.
  * **[!UICONTROL TPCL 305 DPI]**: Use TPCL 300 DPI. The tpcl305.xdc file is used.
  * **[!UICONTROL PCL 600 DPI]**: Use TPCL 600 DPI. The tpcl600.xdc file is used.
  * **[!UICONTROL Custom DPL]**: Use the option to specify a custom XDC file DPL.
  * **[!UICONTROL DPL300DPI]**: Use DPL 300 DPI. The dpl300.xdc file is used.
  * **[!UICONTROL DPL406DPI]**: Use DPL 400 DPI. The dpl406.xdc is used.
  * **[!UICONTROL DPL600DPI]**: Use DPL 600 DPI. The dpl600.xdc is used.

**[!UICONTROL Output Properties]**

* **[!UICONTROL Save output document using]**: Specify the location to save the output file. You can save the output file at an location  which is relative to the payload, in a variable, or specify an absolute location to save the output file. If the path does not exist in crx-repository, an administrator can create the path before using it.

**[!UICONTROL Advanced Properties]**

* **[!UICONTROL Select Content Root location using]**: Content root is a string value that specifies the URI, absolute reference, or location in the repository to retrieve relative assets used by the form design. For example, if the form design references an image relatively, such as ../myImage.gif, myImage.gif must be located at repository://. The default value is repository://, which points to the root level of the repository.

  When you pick an asset from your application, the Content Root URI path must have the correct structure. For example, if a form is picked from an application named SampleApp, and is placed at SampleApp/1.0/forms/Test.xdp, the Content Root URI must be specified as repository://administrator@password/Applications/SampleApp/1.0/forms/, or repository:/Applications/SampleApp/1.0/forms/ (when authority is null). When the Content Root URI is specified this way, the paths of all of the referenced assets in the form will be resolved against this URI.

* **[!UICONTROL Select XCI file using]**: XCI files are used to describe fonts and other properties that are used for form design elements. You can keep an XCI file relative to the payload, at an absolute path, or using a variable of Document data type.

* **[!UICONTROL Locale]**: Specifies the language used for generating the PDF document. If you provide a literal value, select a language from the list or select one of these values:
  * **[!UICONTROL To use server default]**:
    (Default) Use the Locale setting configured on the [!DNL AEM Forms] Server. The Locale setting is configured using Administration Console. (See [Designer Help](http://www.adobe.com/go/learn_aemforms_designer_65).)

  * **[!UICONTROL To use custom value]**:
    Type the Locale code in the literal box or select a string variable containing the locale code. For a complete list of supported locale codes, see http://java.sun.com/j2se/1.5.0/docs/guide/intl/locale.doc.html.

* **[!UICONTROL Copies]**: An integer value that specifies the number of copies to generate for the output. The default value is 1.

* **[!UICONTROL Duplex Printing]**:  A Pagination value that specifies whether to use two-sided or single-sided printing. Printers that support PostScript and PCL use this value.If you provide a literal value, select one of these values:
    * **[!UICONTROL Duplex Long Edge]**: Use two-sided printing and print using long-edge pagination. 
    * **[!UICONTROL Duplex Short Edge]**: Use two-sided printing and print using short-edge pagination. 
    * **[!UICONTROL Simplex]**: Use single-sided printing.-->
