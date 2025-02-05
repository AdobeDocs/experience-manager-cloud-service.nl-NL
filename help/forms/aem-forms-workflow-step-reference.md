---
title: Welke workflowstappen zijn beschikbaar voor AEM Forms Cloud Service om een workflow te maken of voor BPM (Business Process Automation)?
description: Met Forms-gerichte workflows kunt u snel adaptieve, op Forms gebaseerde workflows maken. Met Adobe Sign kunt u documenten elektronisch ondertekenen, op formulieren gebaseerde bedrijfsprocessen maken, gegevens ophalen en verzenden naar meerdere gegevensbronnen en e-mailmeldingen verzenden
exl-id: e1403ba6-8158-4961-98a4-2954b2e32e0d
google-site-verification: A1dSvxshSAiaZvk0yHu7-S3hJBb1THj0CZ2Uh8N_ck4
keywords: Gebruik AEM werkstromen, gebruik taakstappen, zet om in stap PDF/A, produceer document van geregistreerde stap, gebruik werkschema's, de stap van het Document van het Ondertekenen, produceer gedrukte outputstap, produceer niet interactieve PDF output
feature: Adaptive Forms, Workflow
role: Admin, User
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '6730'
ht-degree: 0%

---


# Forms-centrische AEM Workflows gebruiken - Step Reference to automatisate business processes {#forms-centric-workflow-on-osgi-step-reference}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html) |
| AEM as a Cloud Service | Dit artikel |

U gebruikt workflowmodellen. Met behulp van een model kunt u een reeks stappen definiëren en uitvoeren. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt. U kunt [ diverse AEM stappen van het Werkschema in een model omvatten om de bedrijfslogica ](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-workflows/workflows-models.html?lang=en#extending-aem) te bereiken.

## Forms-centric stappen {#forms-workflow-steps}

Forms-centric workflowstappen voeren AEM Forms-specifieke bewerkingen uit in een AEM workflow. Met deze stappen kunt u snel een op Adaptive Forms gebaseerde Forms-gerichte workflow bouwen op OSGi. Deze workflows kunnen worden gebruikt voor het ontwikkelen van basis revisie- en goedkeurings-workflows, interne processen en bedrijfsprocessen binnen de firewall. U kunt ook stappen van de Forms Workflow gebruiken om:

* Maak bedrijfsprocessen, workflows na verzending en back-endworkflows om inschrijvingsprocessen te beheren.

* Taken maken en toewijzen aan een gebruiker of groep.

* Gebruik [!DNL Adobe Sign] in een AEM Workflow om een document voor ondertekening te verzenden.

* Genereer een document van Record op aanvraag of bij het verzenden van het formulier.

* Verbind een werkschemamodel met diverse gegevensbronnen om gegevens gemakkelijk te bewaren en terug te winnen.

* Gebruik de stap E-mail om meldingen en andere bijlagen te verzenden wanneer een actie is voltooid en wanneer een workflow is gestart of voltooid.

>[!NOTE]
>
>Als het workflowmodel is gemarkeerd voor externe opslag, kunt u voor alle stappen in de Forms Workflow alleen de optie voor het opslaan of ophalen van gegevensbestanden en bijlagen selecteren.

## Taakstap toewijzen {#assign-task-step}

De taakstap toewijzen maakt een tijdelijk item en wijst dit toe aan een gebruiker of groep. Naast het toewijzen van de taak geeft de component ook het adaptieve formulier of de niet-interactieve PDF voor de taak op. Het adaptieve formulier is vereist voor het accepteren van invoer van gebruikers en niet-interactieve PDF of een alleen-lezen adaptief formulier wordt gebruikt voor workflows die alleen voor revisie bestemd zijn.

U kunt de component ook gebruiken om het gedrag van de taak te controleren. Bijvoorbeeld, creërend een automatisch Document van Verslag, toewijzend de taak aan een specifieke gebruiker of een groep, specificerend de weg van de voorgelegde gegevens, specificerend de weg van te vullen gegevens, en specificerend standaardacties. De stap Taak toewijzen heeft de volgende eigenschappen:

* **[!UICONTROL Title]**: titel van de taak. De titel wordt weergegeven in het AEM Inbox.
* **[!UICONTROL Description]**: uitleg van de bewerkingen die in de taak worden uitgevoerd. Deze informatie is nuttig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **[!UICONTROL Thumbnail Path]**: pad van de taakminiatuur. Als er geen pad is opgegeven, wordt voor een adaptief formulier een standaardminiatuur weergegeven en voor Document of Record, wordt een standaardpictogram weergegeven.
* **[!UICONTROL Workflow Stage]**: een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model (Sidekick > Pagina > Pagina-eigenschappen > Staven).
* **[!UICONTROL Priority]**: de geselecteerde prioriteit wordt weergegeven in het AEM Inbox. De beschikbare opties zijn Hoog, Medium en Laag. De standaardwaarde is Medium.
* **[!UICONTROL Due Date]**: geef het aantal dagen of uren op waarna de taak achterstallig is. Als u **[!UICONTROL Off]** selecteert, wordt de taak nooit achterstallig gemarkeerd. U kunt ook een time-outhandler opgeven om specifieke taken uit te voeren nadat de taak is uitgevoerd.

* **[!UICONTROL Days]**: Het aantal dagen voordat de taak moet worden voltooid. Het aantal dagen wordt geteld nadat de taak aan een gebruiker is toegewezen. Als een taak niet volledig is en het aantal dagen overschrijdt die in het gebied van Dagen worden gespecificeerd, dan als het wordt geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de correcte datum.
* **[!UICONTROL Hours]**: Het aantal uren voordat de taak moet worden voltooid. Het aantal uren wordt geteld nadat de taak aan een gebruiker wordt toegewezen. Als een taak niet volledig is en het aantal uren overschrijdt specificeert op het gebied van Uren, dan als het wordt geselecteerd, wordt een onderbrekingsmanager teweeggebracht na de verschuldigde uren.
* **[!UICONTROL Time-out after Due Date]**: Selecteer deze optie om het selectieveld Tijdlijnhandler in te schakelen.
* **[!UICONTROL Timeout Handler]**: selecteer het script dat moet worden uitgevoerd wanneer de taakstap toewijzen de juiste datum overschrijdt. De manuscripten die in CRX-bewaarplaats bij [ worden geplaatst apps ]/fd/dashboard/scripts/timeoutHandler zijn beschikbaar voor selectie. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt.
* **[!UICONTROL Highlight the action and comment from the last task in Task Details]**: Selecteer deze optie om de laatste actie weer te geven die is uitgevoerd en de opmerking die is ontvangen in het gedeelte met taakdetails van een taak.
* **[!UICONTROL Type]**: Kies het type document dat moet worden ingevuld wanneer de werkstroom wordt gestart. U kunt een adaptief formulier kiezen, een alleen-lezen adaptief formulier, een niet-interactief PDF-document.

<!-- , Interactive Communication Agent UI, or Interactive Communication Web Channel Document. -->


* **[!UICONTROL Use Adaptive Form]**: geef de methode op waarmee u het invoeradaptief formulier wilt zoeken. Deze optie is beschikbaar als u Adaptief formulier of Alleen-lezen adaptief formulier in de vervolgkeuzelijst Type selecteert. U kunt het Adaptief formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is in een absoluut pad of dat beschikbaar is in een pad in een variabele. U kunt een variabele van het type String gebruiken om het pad op te geven.\
  U kunt meerdere Adaptive Forms aan een workflow koppelen. Hierdoor kunt u bij uitvoering een adaptief formulier opgeven met de beschikbare invoermethoden.

<!-- 

* **[!UICONTROL Use Interactive Communication]**: Specify the method to locate the input interactive communication. You can use the interactive communication submitted to the workflow, available at an absolute path, or available at a path in a variable. You can use a variable of type String to specify the path. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 

> [!NOTE]
>
>You must have cm-agent-users and workflow-users group assignments to access Interactive Communications Agent UI in AEM inbox.  

-->

* **[!UICONTROL Adaptive Form Path]**: geef het pad op van het adaptieve formulier. U kunt het Adaptief formulier gebruiken dat naar de workflow wordt verzonden, beschikbaar via een absoluut pad, of het Adaptief formulier ophalen via een pad dat is opgeslagen in een variabele van het type tekenreeksgegevens.
* **[!UICONTROL Select input PDF using]**: geef het pad op van een niet-interactief PDF-document. Het veld is beschikbaar wanneer u een niet-interactief PDF-document kiest in het veld Type. U kunt de invoer-PDF selecteren met behulp van het pad dat relatief is ten opzichte van de payload, opgeslagen op een absoluut pad of met behulp van een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/PDF/credit-card.pdf. Het pad bestaat niet in crx-repository. Een beheerder maakt het pad voordat het wordt gebruikt. U hebt een Document of Record-optie ingeschakeld of op een formuliersjabloon gebaseerde Adaptieve Forms nodig om de optie PDF-pad te kunnen gebruiken.
* **[!UICONTROL For completed task, render the Adaptive Form as]**: wanneer een taak is gemarkeerd als voltooid, kunt u het adaptieve formulier weergeven als een alleen-lezen adaptief formulier of als een PDF-document. U hebt een Document of Record-optie ingeschakeld of op een formuliersjabloon gebaseerde Adaptieve Forms nodig om het Adaptief formulier weer te geven als Document of Record.
* **[!UICONTROL Pre-populated]**: De volgende velden hieronder dienen als invoer voor de taak:

   * **[!UICONTROL Select input data file using]**: pad van het invoergegevensbestand (.json, .xml, .doc of het formuliergegevensmodel (FDM)). U kunt het invoergegevensbestand terugwinnen gebruikend een weg die met betrekking tot de lading is of het dossier terugwinnen dat in een variabele van Document, XML, of gegevenstype JSON wordt opgeslagen. Het bestand bevat bijvoorbeeld de gegevens die via een AEM Inbox-toepassing voor het formulier zijn verzonden. Een voorbeeldweg is [ Payload_Directory ]/workflow/data.
   * **[!UICONTROL Select input attachments using]**: de op de locatie beschikbare bijlagen worden gekoppeld aan het formulier dat aan de taak is gekoppeld. Het pad kan relatief zijn ten opzichte van de lading of de bijlage ophalen die is opgeslagen in een variabele van een document. Een voorbeeldweg is [ Payload_Directory ] /attachments/. U kunt bijlagen opgeven die relatief zijn ten opzichte van de lading of een variabele van het documenttype (Array-lijst > Document) gebruiken om een invoerbijlage op te geven voor het adaptieve formulier.

  <!-- 
    
    * **[!UICONTROL Choose input JSON]**: Select an input JSON file using a path that is relative to payload or stored in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list.

    * **[!UICONTROL Choose a custom prefill service]**: Select the prefill service to retrieve the data and prefill the Interactive Communication Web channel document or the Agent UI.  
    
    * **[!UICONTROL Use the prefill service of the interactive communication selected above]**: Use this option to use the prefill service of the Interactive Communication defined in the Use Interactive Communication drop-down list. 
    
    -->

   * **[!UICONTROL Request Attribute Mapping]**: Gebruik de sectie van de Toewijzing van Attributen van het Verzoek om de [ naam en waarde van de verzoekattributen ](work-with-form-data-model.md#bindargument) te bepalen. Haal de details van de gegevensbron op die op de attributennaam en waarde wordt gebaseerd in het verzoek wordt gespecificeerd. U kunt een waarde van een aanvraagkenmerk definiëren met een letterlijke waarde of een variabele van het gegevenstype String.

  <!--  
     
     The prefill service and request attribute mapping options are available only if you select Interactive Communication Agent UI or Interactive Communication Web Channel Document from the Type drop-down list. 
     
     -->

* **[!UICONTROL Submitted information]**: De volgende velden hieronder fungeren als uitvoerlocaties voor de taak:

   * **[!UICONTROL Save output data file using]**: sla het gegevensbestand op (.json, .xml, .doc of het formuliergegevensmodel (FDM)). Het gegevensbestand bevat informatie die via het bijbehorende formulier is verzonden. U kunt het uitvoergegevensbestand opslaan met een pad dat relatief is ten opzichte van de lading of dit opslaan in een variabele van het gegevenstype Document, XML of JSON. Bijvoorbeeld, [ Payload_Directory ]/Workflow/data, waar het gegeven een dossier is.
   * **[!UICONTROL Save attachments using]**: sla de formulierbijlagen in een taak op. U kunt de bijlagen opslaan met een pad dat relatief is ten opzichte van de lading of deze opslaan in een arraylijst van het gegevenstype Document.
   * **[!UICONTROL Save Document of Record using]**: pad om een document van een recordbestand op te slaan. Bijvoorbeeld, [ Payload_Directory ] /DocumentofRecord/credit-card.pdf. U kunt het Document van Verslag bewaren gebruikend een weg die met betrekking tot de lading is of het opslaan in een variabele van het gegevenstype van het Document. Als u de optie **[!UICONTROL Relative to Payload]** selecteert, wordt het document of record niet gegenereerd als het padveld leeg blijft. Deze optie is alleen beschikbaar als u Adaptief formulier selecteert in de vervolgkeuzelijst Type.

  <!-- 
    
    * **[!UICONTROL Save Web Channel data using]**: Save the Web Channel data file using a path that is relative to the payload or store it in a variable of Document, JSON, or Form Data Model (FDM) data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. c
    * **[!UICONTROL Save PDF document using]**: Save the PDF document using a path that is relative to the payload or store it in a variable of Document data type. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list.
    <!-- * **[!UICONTROL Save layout template using]**: Save the layout template using a path that is relative to the payload or store it in a variable of Document data type. The [layout template](layout-design-details.md) refers to an XDP file that you create using Forms Designer. This option is available only if you select Interactive Communication Agent UI from the Type drop-down list. 
    
    -->

* **[!UICONTROL Assignee]** > **[!UICONTROL Assign options]** : geef de methode op die u aan een gebruiker wilt toewijzen. U kunt de taak dynamisch toewijzen aan een gebruiker of groep met behulp van het script Deelnemerkiezer of u kunt de taak toewijzen aan een specifieke AEM gebruiker of groep.
* **[!UICONTROL Participant Chooser]**: De optie is beschikbaar wanneer de optie **[!UICONTROL Dynamically to a user or group]** is geselecteerd in het veld Opties toewijzen. U kunt een ECMAScript of de dienst gebruiken om een gebruiker of een groep dynamisch te selecteren. Voor meer informatie, zie [ dynamisch een werkschema toewijzen aan de gebruikers ](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) en [ Creërend een stap van de Dynamische Deelnemer van de douane Adobe Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=en&amp;CID=RedirectAEMCommunityKautuk).

* **[!UICONTROL Participants]**: Het veld is beschikbaar wanneer de optie **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** is geselecteerd in het veld **[!UICONTROL Participant Chooser]** . In het veld kunt u gebruikers of groepen selecteren voor de optie RandomParticipantChooser.

* **[!UICONTROL Assignee]**: Het veld is beschikbaar wanneer **[!UICONTROL com.adobe.fd.workspace.step.service.VariableParticipantChooser]** is geselecteerd in het veld **[!UICONTROL Participant Chooser]** . In het veld kunt u een variabele van het gegevenstype String selecteren om de toewijzing te definiëren.

* **[!UICONTROL Arguments]**: Het veld is beschikbaar wanneer een ander script dan het script RandomParticipantChoose is geselecteerd in het veld Deelnemerkiezer. In het veld kunt u een lijst met door komma&#39;s gescheiden argumenten opgeven voor het script dat is geselecteerd in het veld Deelnemerkiezer.

* **[!UICONTROL User or Group]**: De taak wordt toegewezen aan een geselecteerde gebruiker of groep. De optie is beschikbaar wanneer **[!UICONTROL To a specific user or group option]** is geselecteerd in het veld **[!UICONTROL Assign options]** . In het veld worden alle gebruikers en groepen van de groep [!DNL workflow-users] weergegeven.\
  In het vervolgkeuzemenu **[!UICONTROL User or Group]** worden de gebruikers en groepen weergegeven waartoe de aangemelde gebruiker toegang heeft. De weergave van de gebruikersnaam is afhankelijk van of u toegangsmachtigingen hebt voor het knooppunt **[!UICONTROL users]** in de crx-opslagplaats voor die bepaalde gebruiker.

* **[!UICONTROL Send Notification Email]**: Selecteer deze optie om e-mailmeldingen naar de toegewezen persoon te verzenden. Deze meldingen worden verzonden wanneer een taak wordt toegewezen aan een gebruiker of een groep. Met de optie **[!UICONTROL Recipient Email Address]** kunt u opgeven hoe het e-mailadres moet worden opgehaald.

* **[!UICONTROL Recipient Email Address]**: U kunt een e-mailadres in een variabele opslaan, een letterlijk adres gebruiken om een permanent e-mailadres op te geven of het standaard e-mailadres van de ontvanger gebruiken, zoals opgegeven in het profiel van de ontvanger. U kunt het letterlijke of variabele gebruiken om het e-mailadres van een groep op te geven. De optie Variabele is handig bij het dynamisch ophalen en gebruiken van een e-mailadres. De optie **[!UICONTROL Use default email address of the assignee]** is slechts voor één toegewezen persoon. In dit geval wordt het e-mailadres gebruikt dat is opgeslagen in het gebruikersprofiel Toegewezen.

* **[!UICONTROL HTML Email Template]**: selecteer de e-mailsjabloon voor de e-mailmelding. Als u een sjabloon wilt bewerken, wijzigt u het bestand op /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt in de crx-repository.
* **[!UICONTROL Allow Delegation To]**: AEM Inbox biedt de aangemelde gebruiker een optie om de toegewezen workflow te delegeren aan een andere gebruiker. U kunt delegeren binnen dezelfde groep of aan de werkschemagebruiker van een andere groep. Als de taak aan één gebruiker wordt toegewezen en de optie **[!UICONTROL allow delegation to members of the assignee group]** wordt geselecteerd, dan is het niet mogelijk om de taak aan een andere gebruiker of groep te delegeren.
* **[!UICONTROL Share Settings]**: AEM Inbox biedt opties om een of alle taken in het Postvak IN te delen met een andere gebruiker:
   * Wanneer de optie **[!UICONTROL Allow assignee to share explicitly in inbox]** is geselecteerd, kan de gebruiker de taak in AEM Postvak In selecteren en deze met een andere AEM delen.
   * Wanneer de optie **[!UICONTROL Allow assignee to share via inbox sharing]** is geselecteerd en gebruikers hun Postvak IN-items delen of andere gebruikers toegang geven tot hun Postvak IN-items, worden alleen taken waarvoor de eerder vermelde optie is ingeschakeld, gedeeld met andere gebruikers.
   * Wanneer **[!UICONTROL Allow assignee to delegate using 'Out of Office' settings]** is geselecteerd. De ontvanger kan de optie toelaten om de taak aan andere gebruikers samen met andere uit opties van het Bureau te delegeren. Om het even welke nieuwe die taken aan de uit-van-bureaugebruiker worden toegewezen worden automatisch gedelegeerd (toegewezen) aan de gebruikers in uit-van-bureaumontages worden vermeld.

  Het staat andere gebruikers toe om toewijstaken te kiezen terwijl buiten het bureau is en niet aan toegewezen taken kan werken.

* **[!UICONTROL Actions]** > **[!UICONTROL Default Actions]**: De acties Verzenden, Opslaan en Herstellen zijn beschikbaar. Standaard zijn alle standaardhandelingen ingeschakeld.
* **[!UICONTROL Route Variable]**: naam van de routevariabele. De routevariabele vangt douaneacties die een gebruiker in AEM Inbox selecteert.
* **[!UICONTROL Routes]**: een taak kan zich vertakken naar verschillende routes. Wanneer geselecteerd in AEM Inbox, keert de route een waarde en de werkschematakken terug die op de geselecteerde route worden gebaseerd. U kunt routes in een variabele van serie van de gegevenstypes van het Koord opslaan of **[!UICONTROL Literal]** selecteren om routes manueel toe te voegen.

* **[!UICONTROL Route Title]**: geef de titel voor de route op. Deze wordt weergegeven in het AEM Inbox.
* **[!UICONTROL Coral Icon]**: geef een HTML-kenmerk van een koraalpictogram op. De Adobe CorelUI-bibliotheek biedt een uitgebreide set aanraakpictogrammen. U kunt een pictogram voor de route kiezen en gebruiken. Deze wordt samen met de titel weergegeven in het AEM Inbox. Als u de routes in een variabele opslaat, gebruiken de routes een standaard &quot;Tags&quot;koraalpictogram.
* **[!UICONTROL Allow assignee to add comment]**: Selecteer deze optie om opmerkingen voor de taak in te schakelen. Een toegewezen persoon kan de opmerkingen toevoegen vanuit het Postvak AEM op het moment dat de taak wordt verzonden.
* **[!UICONTROL Save comment in variable]**: sla de opmerking op in een variabele van het gegevenstype String. Deze optie wordt alleen weergegeven als u het selectievakje **[!UICONTROL Allow assignee to add comment]** inschakelt.

* **[!UICONTROL Allow assignee to add attachments to the task]**: selecteer deze optie om bijlagen in te schakelen voor de taak. Een toegewezen persoon kan de bijlagen toevoegen vanuit het AEM Postvak In op het moment dat de taak wordt verzonden. U kunt ook de maximale grootte **[!UICONTROL (Maximum File Size)]** van een bijlage beperken. De standaardgrootte is 2 MB.

* **[!UICONTROL Save output task attachments using]**: geef de locatie van de map met bijlagen op. U kunt uitvoertaakbijlagen opslaan met een pad dat is gebaseerd op de lading of in een variabele van een array met documentgegevenstypen. Deze optie wordt alleen weergegeven als u het selectievakje **[!UICONTROL Allow assignee to add attachments to the task]** inschakelt en **[!UICONTROL Adaptive Form]** , **[!UICONTROL Read-only Adaptive Form]** of **[!UICONTROL Non-interactive PDF document]** selecteert in de vervolgkeuzelijst **[!UICONTROL Type]** op het tabblad **[!UICONTROL Form/Document]** .

* **[!UICONTROL Use custom metadata]**: Selecteer deze optie om het veld voor aangepaste metagegevens in te schakelen. Aangepaste metagegevens worden gebruikt in e-mailsjablonen.
* **[!UICONTROL Custom Metadata]**: selecteer aangepaste metagegevens voor de e-mailsjablonen. De aangepaste metagegevens zijn beschikbaar in de crx-gegevensopslagruimte op apps/fd/dashboard/scripts/metadataScripts. Het opgegeven pad bestaat niet in de crx-gegevensopslagruimte. Een beheerder maakt het pad voordat het wordt gebruikt. U kunt ook een service gebruiken voor de aangepaste metagegevens. U kunt de interface van `WorkitemUserMetadataService` ook uitbreiden om douanemetagegevens te verstrekken.
* **[!UICONTROL Show Data from Previous Steps]**: Selecteer deze optie om ervoor te zorgen dat toewijzen vorige toewijzingen, reeds ondernomen actie op de taak, aan de taak toegevoegde opmerkingen en Document of Record van de voltooide taak kunnen weergeven, indien beschikbaar.
* **[!UICONTROL Show Data from Subsequent Steps]**: Selecteer deze optie om de huidige toegewezen persoon in staat te stellen de actie te bekijken die is uitgevoerd en de opmerkingen die aan de taak zijn toegevoegd door de volgende toegewezen personen. Het staat ook de huidige toegewezen persoon toe om een Document van Verslag van de voltooide taak te bekijken, als beschikbaar.
* **[!UICONTROL Visibility of data type]**: standaard kan een toegewezen persoon een document met records, toewijzingen, ondernomen actie en opmerkingen bekijken die door vorige en volgende toewijzingen zijn toegevoegd. Gebruik de zichtbaarheid van de optie Gegevenstype om het type gegevens te beperken dat zichtbaar is voor de ontvangers.

>[!NOTE]
>
>De opties om de Assign stap van de Taak als ontwerp te bewaren en de geschiedenis van de Assign stap van de Taak terug te winnen worden onbruikbaar gemaakt wanneer u een AEM werkschemamodel voor externe gegevensopslag vormt. In Postvak In is bovendien de optie om op te slaan uitgeschakeld.

## Omzetten in stap PDF/A {#convert-pdfa}

PDF/A is een archiefindeling voor langdurige bewaring van de inhoud van het document, door de lettertypen in te sluiten en de compressie van het bestand op te heffen. Een PDF/A-document is daarom doorgaans groter dan een standaard PDF-document. U kunt ***gebruiken zet in PDF/A*** stap in een AEMWerkschema om uw documenten van PDF in formaat om te zetten PDF/A.

De stap Omzetten in PDF/A heeft de volgende eigenschappen:

**[!UICONTROL Input Document]**: Het invoerdocument kan relatief zijn ten opzichte van de lading, een absoluut pad hebben, als een lading kunnen worden verstrekt of in een variabele van het gegevenstype Document worden opgeslagen.

**[!UICONTROL Conversion Options]**: Met deze eigenschap worden de instellingen opgegeven voor het converteren van PDF-documenten naar PDF/A-documenten. Onder dit tabblad zijn verschillende opties beschikbaar:
* **[!UICONTROL Compliance]** - Geeft de standaard aan waaraan het uitvoer-PDF/A-document moet voldoen. Het steunt verschillende normen van PDF zoals PDF/A-1b, PDF/A-2b, of PDF/A-3b.
* **[!UICONTROL Result Level]** - Geeft het resultaatniveau op als PassFail, Summary of Gedetailleerd voor de conversie-uitvoer.
* **[!UICONTROL Color Space]**: geeft de vooraf gedefinieerde kleurruimte op als S_RGB, COATED_FOGRA27, JAPAN_COLOR_COATED of SWOP, die kan worden gebruikt voor uitvoer van PDF/A-bestanden.
* **[!UICONTROL Optional Content]**: Toestaan dat specifieke grafische objecten en/of annotaties alleen zichtbaar zijn in uitvoer-PDF/A-document als aan een bepaalde set criteria wordt voldaan.

**[!UICONTROL Output Documents]** - Geeft de locatie op waar het uitvoerbestand moet worden opgeslagen. Het uitvoerbestand kan worden opgeslagen op een locatie die relatief is ten opzichte van de lading, de lading wordt overschreven, als de lading een bestand is of in een variabele van het gegevenstype Document.


## E-mailstap verzenden {#send-email-step}

Met de stap E-mail kunt u bijvoorbeeld een e-mail verzenden met een document of record, een koppeling naar een adaptief formulier <!-- , link of an interactive communication--> of een bijgevoegd PDF-document. Verzend E-mailstap steunt [ HTML e-mail ](https://en.wikipedia.org/wiki/HTML_email). HTML e-mailberichten reageren en passen zich aan de e-mailclient en schermgrootte van de ontvangers aan. Met een e-mailsjabloon voor HTML kunt u de vormgeving, het kleurenschema en het gedrag van de e-mail definiëren.

In de e-mailstap wordt de Day CQ Mail Service gebruikt om e-mailberichten te verzenden. Controleer voordat u de e-mailstap gebruikt of de e-mailservice is geconfigureerd. E-mailondersteuning biedt standaard alleen HTTP- en HTTP-protocollen. [ contacteer het steunteam ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=en#sending-email) om havens toe te laten om e-mail te verzenden en protocol SMTP voor uw milieu toe te laten. De beperking helpt de beveiliging van het platform te verbeteren.

De e-mailstap heeft de volgende eigenschappen:

**[!UICONTROL Title]**: titel van de stap helpt de stap in de werkstroomeditor te identificeren.

**[!UICONTROL Description]**: uitleg is handig voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

**[!UICONTROL Email Subject]**: Onderwerp kan worden opgehaald uit een werkstroommetagegevens die handmatig zijn opgegeven of worden opgehaald uit de waarde die in een variabele is opgeslagen. Selecteer een van de volgende opties:

* **[!UICONTROL Literal]** Geef handmatig een onderwerp op.
* **[!UICONTROL Retrieve from Workflow metadata]** - Haal het onderwerp op van een eigenschap metadata.
* **[!UICONTROL Variable]** - Haal het onderwerp op uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

**[!UICONTROL HTML Email Template]**: HTML sjabloon voor e-mail. U kunt variabelen in een e-mailsjabloon opgeven. De E-mailstap extraheert en geeft alle variabelen weer die in een sjabloon zijn opgenomen voor invoer.

**[!UICONTROL Email Template Metadata]**: de waarde van de sjabloonvariabelen voor e-mail kan een door de gebruiker opgegeven waarde zijn, het pad van een element op de auteur of de publicatieserver, afbeelding of eigenschap voor metagegevens van de workflow.

* **[!UICONTROL Literal]**: gebruik de optie wanneer u precies weet welke waarde moet worden opgegeven. Bijvoorbeeld, [ example@example.com ](mailto:example@example.com).

* **[!UICONTROL Workflow Metadata]**: gebruik de optie wanneer de te gebruiken waarde wordt opgeslagen in een eigenschap voor metagegevens van de workflow. Nadat u de optie hebt geselecteerd, typt u de naam van de eigenschap metadata in het lege tekstvak onder de optie Metagegevens werkstroom. Bijvoorbeeld emailAddress.

<!-- 

* **[!UICONTROL Asset URL]**: Use the option to embed a web link of an interactive communication to the email. After selecting the option, browse and choose the interactive communication to embed. The asset can reside on the author or the publish server. 

-->

* **[!UICONTROL Image]**: gebruik de optie om een afbeelding in te sluiten in de e-mail. Blader en kies de afbeelding nadat u de optie hebt geselecteerd. De beeldoptie is beschikbaar slechts voor de beeldmarkeringen (&lt;img src=&quot;&#42;&quot;/>) beschikbaar in het e-mailmalplaatje.

**[!UICONTROL Sender's / Recipient's Email Address]**: selecteer de optie **[!UICONTROL Literal]** om handmatig een e-mailadres op te geven of selecteer de optie **[!UICONTROL Retrieve from Workflow metadata]** om het e-mailadres op te halen uit een eigenschap voor metagegevens. U kunt ook een lijst met arrays met metagegevenseigenschappen opgeven voor de optie **[!UICONTROL Retrieve from Workflow metadata]** . Selecteer de optie **[!UICONTROL Variable]** om het e-mailadres op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String.

* **[!UICONTROL File Attachment]**: Het middel dat beschikbaar is op de opgegeven locatie, is als bijlage bij de e-mail gevoegd. Het pad van het element kan relatief zijn ten opzichte van de payload of het absolute pad. Een voorbeeldweg is [ Payload_Directory ] /attachments/.

Selecteer de optie **[!UICONTROL Variable]** om de bestandsbijlage op te halen die is opgeslagen in een variabele van het gegevenstype Document, XML of JSON.

**[!UICONTROL File Name]**: naam van het bestand met e-mailbijlagen. Met de E-mailstap wijzigt u de oorspronkelijke bestandsnaam van de bijlage in de opgegeven bestandsnaam. De naam kan handmatig worden opgegeven of opgehaald uit een eigenschap voor metagegevens van een workflow of een variabele. Gebruik de optie **[!UICONTROL Literal]** als u precies weet welke waarde u moet opgeven. Gebruik de optie **[!UICONTROL Variable]** om de bestandsnaam op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Gebruik de optie **[!UICONTROL Retrieve from a Workflow Metadata]** wanneer de te gebruiken waarde wordt opgeslagen in een eigenschap voor metagegevens van een workflow.

## Document met recordstap genereren {#generate-document-of-record-step}

Wanneer een formulier wordt ingevuld of verzonden, kunt u het formulier afdrukken of in documentindeling registreren. Deze record wordt een Document of Record (DoR) genoemd. Met de stap Document van record genereren kunt u een alleen-lezen of interactieve PDF versie van een adaptief formulier maken. De PDF-versie bevat informatie die in het formulier is ingevuld en de indeling van het adaptieve formulier.

De stap Document of Record heeft de volgende eigenschappen:

**[!UICONTROL Use Adaptive Form]**: geef de methode op waarmee u het invoeradaptief formulier wilt zoeken. U kunt het Adaptief formulier gebruiken dat naar de workflow wordt verzonden, dat beschikbaar is in een absoluut pad of dat beschikbaar is in een pad in een variabele. U kunt een variabele van het gegevenstype String gebruiken om het pad op te geven in het veld **[!UICONTROL Select variable to resolve]** .\
U kunt meerdere Adaptive Forms aan een workflow koppelen. Hierdoor kunt u bij uitvoering een adaptief formulier opgeven met de beschikbare invoermethoden.

**[!UICONTROL Adaptive Form Path]**: geef het pad op van het adaptieve formulier. Het veld is beschikbaar wanneer u de optie **[!UICONTROL Available at an absolute path]** in het veld **[!UICONTROL Use Adaptive Form]** selecteert.

**[!UICONTROL Select Input data using]**: pad van de invoergegevens voor het adaptieve formulier. U kunt de gegevens op een plaats met betrekking tot de lading houden, een absolute weg van de gegevens specificeren, of gegevens terugwinnen die in een variabele van document, JSON, of het gegevenstype van XML worden opgeslagen. De invoergegevens worden samengevoegd met het Adaptief formulier om een Document of Record te maken.

**[!UICONTROL Select Input attachment path using]**: pad van de bijlagen. Deze bijlagen worden opgenomen in het document of record. U kunt de bijlagen op een locatie relatief ten opzichte van de lading houden, een absoluut pad naar de bijlagen opgeven of bijlagen ophalen die zijn opgeslagen in een variabele van het gegevenstype Document.

Als u bijvoorbeeld het pad van een map opgeeft, worden alle bestanden die rechtstreeks in de map beschikbaar zijn, gekoppeld aan het document met records. Als er bestanden beschikbaar zijn in de mappen die rechtstreeks beschikbaar zijn in het opgegeven pad naar de bijlage, worden de bestanden als bijlagen opgenomen in Document of Record. Als er mappen in direct beschikbare mappen staan, worden deze overgeslagen.

**[!UICONTROL Save Generated Document of Record using below options]**: geef de locatie op waar u een document van een recordbestand wilt behouden. U kunt ervoor kiezen om de ladingmap te overschrijven, het document of record op een locatie in de ladingmap te plaatsen of het document of record op te slaan in een variabele van het gegevenstype Document.

**[!UICONTROL Locale]**: geef de taal op van het document of record. Selecteer **[!UICONTROL Literal]** om de landinstelling in een vervolgkeuzelijst te selecteren of selecteer **[!UICONTROL Variable]** om de landinstelling op te halen uit de waarde die is opgeslagen in een variabele van het gegevenstype String. Definieer de landinstellingscode terwijl u de waarde voor de landinstelling in een variabele opslaat. Bijvoorbeeld, specificeer **en_US** voor Engels en **fr_FR** voor Frans.

## DDX-stap aanroepen {#invokeddx}

XML (DDX) van de Beschrijving van het document is een verklarende prijsverhogingstaal de waarvan elementen bouwstenen van documenten vertegenwoordigen. Deze bouwstenen omvatten PDF- en XDP-documenten en andere elementen, zoals opmerkingen, bladwijzers en gestileerde tekst. DDX definieert een set bewerkingen die op een of meer invoerdocumenten kan worden toegepast om een of meer uitvoerdocumenten te genereren. Eén DDX kan worden gebruikt met een reeks brondocumenten. U kunt de ***aanhalen stap DDX*** in een AEM Werkschema gebruiken om diverse verrichtingen uit te voeren, zoals het assembleren van documenten, het Creëren van, en het wijzigen van Acrobat en XFA Forms, en anderen die in de [ documentatie van de Verwijzing DDX ](https://helpx.adobe.com/content/dam/help/en/experience-manager/forms-cloud-service/ddxRef.pdf) worden beschreven.

De aanroepende DDX-stap heeft de volgende eigenschappen:

**[!UICONTROL Input Documents]**: wordt gebruikt om eigenschappen van een invoerdocument in te stellen. Onder dit tabblad zijn verschillende opties beschikbaar:
* **[!UICONTROL Specify DDX Using]** - Geeft het invoerdocument op dat relatief is ten opzichte van de payload, een absoluut pad heeft, kan worden opgegeven als een payload of kan worden opgeslagen in een variabele van het gegevenstype Document.
* **[!UICONTROL Create Map from Payload]**: voeg alle documenten onder de ladingsomslag aan de Kaart van het Document van de Input voor aan te halen API in Assembler. De knooppuntnaam voor elk document wordt gebruikt als sleutel in de kaart.
* **[!UICONTROL Input Document's Map]**: de optie wordt gebruikt om meerdere items toe te voegen met de knop **[!UICONTROL ADD]** . Elk item vertegenwoordigt de sleutel van het document in de kaart en de bron van het document.

**[!UICONTROL Environment Options]**: deze optie wordt gebruikt om verwerkingsinstellingen in te stellen voor het aanroepen van de API. Onder dit tabblad zijn verschillende opties beschikbaar:
* **[!UICONTROL Validate Only]**: hiermee wordt de geldigheid van het invoer-DDX-document gecontroleerd.
* **[!UICONTROL Fail on Error]**: Booleaanse waarde die aangeeft of de API-service aanroepen mislukt, als er een fout is of niet. De standaardwaarde is False.
* **[!UICONTROL First Bates Number]** - Geeft het getal op dat automatisch wordt verhoogd. Dit zelf-stijgende aantal wordt automatisch getoond op elke opeenvolgende pagina.
* **[!UICONTROL Default Style]** - Stelt de standaardstijl voor het uitvoerbestand in.

>[!NOTE]
>
>Omgevingsopties blijven gesynchroniseerd met HTTP API&#39;s.

**[!UICONTROL Output Documents]** - Geeft de locatie op waar het uitvoerbestand moet worden opgeslagen. Onder dit tabblad zijn verschillende opties beschikbaar:
* **[!UICONTROL Save Output in Payload]**: slaat uitvoerdocumenten op onder de payload-map of overschrijft de payload, voor het geval dat de payload een bestand is.
* **[!UICONTROL Output Document's Map]** - Geeft de locatie op waar elk documentbestand expliciet moet worden opgeslagen door één item per document toe te voegen. Elk item vertegenwoordigt het document en de locatie waar het moet worden opgeslagen. Als er meerdere uitvoerdocumenten zijn, wordt deze optie gebruikt.

## FDM-service (Form Data Model) aanroepen {#invoke-form-data-model-service-step}

U kunt [[!DNL AEM Forms]  Integratie van Gegevens gebruiken ](data-integration.md) om te vormen en met ongelijksoortige gegevensbronnen te verbinden. Deze gegevensbronnen kunnen de Webdienst, de dienst van REST, de dienst van OData, en oplossing van CRM zijn. [!DNL AEM Forms] De Integratie van gegevens laat u een Model van de Gegevens van de Vorm (FDM) tot stand brengen dat de diverse diensten omvat om gegevensherwinning uit te voeren, toevoeging, het bijwerken verrichtingen op het gevormde gegevensbestand. U kunt **[!UICONTROL Invoke Data Model Service step]** gebruiken om een Model van de Gegevens van de Vorm (FDM) te selecteren en de diensten van FDM te gebruiken om, gegevens terug te winnen bij te werken of toe te voegen om gegevensbronnen te verdelen.

Om input voor gebieden van de stap te verklaren, worden de volgende gegevensbestandlijst en het dossier JSON gebruikt als voorbeeld:

**[!UICONTROL Sample CustomerDetails table]**

<table>
 <tbody> 
  <tr> 
   <td>Eigenschap</td> 
   <td>Waarde <br /> </td> 
  </tr> 
  <tr> 
   <td>FirstName <br /> </td> 
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
   <td>E-mailadres <br /> </td> 
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

De stap FDM (Invoke Form Data Model)-service bevat de onderstaande velden om FDM-bewerkingen (Form Data Model) te vergemakkelijken:

* **[!UICONTROL Title]**: titel van de stap. Hiermee kunt u de stappen in de werkstroomeditor identificeren.
* **[!UICONTROL Description]**: uitleg die nuttig is voor andere procesontwikkelaars wanneer u in een gedeelde ontwikkelomgeving werkt.

* **[!UICONTROL Form Data Model Path]**: blader en selecteer een Model van de Gegevens van het Vorm (FDM) aanwezig op de server.

* **[!UICONTROL Errors and Validations]**: met deze optie kunt u foutberichten vastleggen en validatieopties opgeven voor gegevens die zijn opgehaald en naar gegevensbronnen worden verzonden. Met deze veranderingen, kunt u gegevens verzekeren die tot de Invoke stap van de Dienst van de Gegevens van de Vorm van de Vorm (FDM) worden overgegaan voldoet aan de gegevensbeperkingen die door de gegevensbron worden bepaald. Voor meer details, zie [ Geautomatiseerde bevestiging van inputgegevens ](work-with-form-data-model.md#automated-validation-of-input-data)

* **[!UICONTROL Validation level]**: Er zijn drie validatiecategorieën: Standaard, Volledig en UIT:

   * Volledig - Alle beperkingen worden gevalideerd.
   * Eenvoudig: alleen vereiste en niet-uitvoerbare beperkingen
   * UIT: er vindt geen validatie plaats.

* **[!UICONTROL Terminate Workflow on Failure]**: Wanneer een beperking niet kan worden gevalideerd, wordt de workflow gestopt.

* **[!UICONTROL Store Error Code in Variable]**: U kunt een foutencode in a [ het type van Koord variabele ](variable-in-aem-workflows.md) opslaan.

* **[!UICONTROL Store Error Message in Variable]**: U kunt een foutenmelding in a [ typevariabele van het Type van Koord ](variable-in-aem-workflows.md) opslaan.

* **[!UICONTROL Store Error Details in Variable]**: U kunt een foutendetail in a [ opslaan JSON type variabele ](variable-in-aem-workflows.md).

* **[!UICONTROL Service]**: Lijst met services die door het geselecteerde formuliergegevensmodel (FDM) worden geboden.
* **[!UICONTROL Input for services]** > **[!UICONTROL Provide input data using literal, variable, or workflow metadata, and a JSON file]**: een service kan meerdere argumenten hebben. Selecteer de optie om de waarde van de de dienstargumenten van een werkschemabezit, een voorwerp JSON, een variabele te verkrijgen, of direct de waarde in het verstrekte tekstvakje in te gaan:

   * **[!UICONTROL Literal]**: gebruik de optie wanneer u precies weet welke waarde moet worden opgegeven. Bijvoorbeeld srose@we.info.
   * **[!UICONTROL Variable]**: gebruik de optie om de waarde op te halen die in een variabele is opgeslagen.
   * **[!UICONTROL Retrieve from Workflow Metadata]**: gebruik de optie wanneer de te gebruiken waarde wordt opgeslagen in een eigenschap voor metagegevens van de workflow. Bijvoorbeeld emailAddress.

   * **[!UICONTROL Relative to Payload]**: gebruik de optie om de bestandsbijlage op te halen die is opgeslagen op een pad dat relatief is ten opzichte van de laadbewerking. Selecteer de optie en geef de mapnaam op die de bestandsbijlage bevat of geef de naam van de bestandsbijlage op in het tekstvak.

     Als de map Relatief aan Payload in de CRX-opslagplaats bijvoorbeeld een bestandsbijlage bevat op de locatie `attachment\attachment-folder` , geeft u `attachment\attachment-folder` in het tekstvak op nadat u de optie **[!UICONTROL Relative to Payload]** hebt geselecteerd.

   * **[!UICONTROL JSON Dot Notation]**: gebruik de optie wanneer de te gebruiken waarde zich in een JSON-bestand bevindt. Bijvoorbeeld verzekering.customerDetails.emailAddress. De optie JSON-puntnotatie is alleen beschikbaar als invoervelden toewijzen van de JSON-invoeroptie is geselecteerd.
   * **[!UICONTROL Map input fields from input JSON]**: geef het pad op van een JSON-bestand om de invoerwaarde van bepaalde serviceargumenten op te halen uit het JSON-bestand. Het pad van het JSON-bestand kan relatief zijn ten opzichte van de payload, een absoluut pad, of u kunt een invoer-JSON-document selecteren met een variabele van het type JSON of Form Data Model (FDM).

* **[!UICONTROL Input for services]** > **[!UICONTROL Provide input data using variable or a JSON file]**: Selecteer de optie om waarden voor alle argumenten op te halen uit een JSON-bestand dat is opgeslagen op een absoluut pad, op een pad dat relatief is ten opzichte van de payload of in een variabele.
* **[!UICONTROL Select Input JSON document using]**: Het JSON-bestand met waarden voor alle serviceargumenten. Het pad van het JSON-bestand kan **[!UICONTROL relative to the payload]** of **[!UICONTROL absolute path]** zijn. U kunt het invoer-JSON-document ook ophalen met behulp van een variabele van het gegevenstype JSON of Form Data Model (FDM).

* **[!UICONTROL JSON Dot Notation]**: Laat het veld leeg om alle objecten van het opgegeven JSON-bestand te gebruiken als invoer voor serviceargumenten. Als u een specifiek JSON-object uit het opgegeven JSON-bestand wilt lezen als invoer voor serviceargumenten, geeft u puntnotatie voor het JSON-object op. Als u bijvoorbeeld een JSON-object hebt dat vergelijkbaar is met de JSON-object dat aan het begin van de sectie wordt vermeld, geeft u Insurance.customerDetails op om alle details van een klant als invoer voor de service op te geven.
* **[!UICONTROL Output of service]** > **[!UICONTROL Map and write output values to variable or metadata]**: selecteer de optie om de uitvoerwaarden op te slaan als eigenschappen van het metagegevensknooppunt voor workflowinstanties in de crx-gegevensopslagruimte. Specificeer de naam van het meta-gegevensbezit en selecteer het overeenkomstige attribuut van de de dienstoutput dat met het meta-gegevensbezit moet worden in kaart gebracht, bijvoorbeeld, phone_number dat door de outputdienst met het phone_number bezit van werkschemameta-gegevens is teruggekeerd. Op dezelfde manier kunt u de uitvoer opslaan in een variabele van het gegevenstype Long. Wanneer u een eigenschap voor de optie **[!UICONTROL Service output attribute to be mapped]** selecteert, worden alleen variabelen die gegevens van de geselecteerde eigenschap kunnen opslaan, gevuld voor de optie **[!UICONTROL Save the output to]** .

* **[!UICONTROL Output of service]** > **[!UICONTROL Save output to variable or a JSON file]**: selecteer de optie om de uitvoerwaarden in een JSON-bestand op te slaan met een absoluut pad, een pad dat relatief is ten opzichte van de laadtijd of een variabele.
* **[!UICONTROL Save Output JSON document using below options]**: sla het JSON-uitvoerbestand op. Het pad van het JSON-uitvoerbestand kan relatief zijn ten opzichte van de payload of een absoluut pad. U kunt het JSON-uitvoerbestand ook opslaan met een variabele van het gegevenstype JSON of Form Data Model (FDM).



## stap Document ondertekenen {#sign-document-step}

Met de stap Document ondertekenen kunt u [!DNL Adobe Sign] gebruiken om documenten te ondertekenen. Wanneer u de workflowstap van [!DNL Adobe Sign] gebruikt om een adaptief formulier te ondertekenen, kan het formulier tussen ontvangers worden doorgegeven of tegelijkertijd naar alle ontvangers worden verzonden, afhankelijk van de configuratie van de workflowstap. [!DNL Adobe Sign] Aangepaste Forms die is ingeschakeld, worden alleen naar Experience Manager Forms Server verzonden nadat alle ontvangers het ondertekeningsproces hebben voltooid.

Standaard controleert de [!DNL Adobe Sign] Scheduler-service (opiniepeilingen) de reacties van de ontvanger na elke 24 uur. U kunt [ het standaardinterval voor uw milieu ](adobe-sign-integration-adaptive-forms.md#for-aem-workflows-only-configure-dnl-adobe-acrobat-sign-scheduler-to-sync-the-signing-status-configure-adobe-sign-scheduler-to-sync-the-signing-status) veranderen.

De stap Document ondertekenen heeft de volgende eigenschappen:

* **[!UICONTROL Agreement Name]**: geef de titel van de overeenkomst op. De naam van de overeenkomst wordt onderdeel van het onderwerp en de hoofdtekst van de e-mail die naar de ondertekenaars wordt verzonden. U kunt de naam opslaan in een variabele van het gegevenstype String of **[!UICONTROL Literal]** selecteren om de naam handmatig toe te voegen.

* **[!UICONTROL Locale]**: geef de taal op voor de opties voor e-mail en verificatie. U kunt de landinstelling opslaan in een variabele van het gegevenstype String of **[!UICONTROL Literal]** selecteren om de landinstelling te kiezen in de lijst met beschikbare opties. U moet de landinstellingscode definiëren terwijl u de waarde voor de landinstelling in een variabele opslaat. Geef bijvoorbeeld **[!UICONTROL en_US]** op voor Engels en **[!UICONTROL fr_FR]** voor Frans.

* **[!UICONTROL Adobe Sign Cloud Configuration]**: kies een [!DNL Adobe Sign] cloudconfiguratie. Als u niet [!DNL Adobe Sign] voor [!DNL AEM Forms] hebt gevormd, zie [ Adobe Sign met  [!DNL AEM Forms]](adobe-sign-integration-adaptive-forms.md) integreren.

* **[!UICONTROL Select Document to be signed using]**: U kunt een document kiezen op een locatie die relatief is ten opzichte van de lading, de lading gebruiken als het document, een absoluut pad van het document opgeven of het document ophalen dat is opgeslagen in een variabele van het gegevenstype Document.
* **[!UICONTROL Days Until Deadline]**: Een document is gemarkeerd als vervallen (verstreken deadline) nadat de taak gedurende het opgegeven aantal dagen niet is geactiveerd in het veld **[!UICONTROL Days Until Deadline]** . Het aantal dagen wordt geteld nadat de documentatie aan een gebruiker is toegewezen voor ondertekening.
* **[!UICONTROL Reminder Email Frequency]**: U kunt een herinnering per e-mail verzenden met een dagelijkse of wekelijkse interval. De week wordt geteld vanaf de dag waarop de documentatie aan een gebruiker is toegewezen voor ondertekening.
* **[!UICONTROL Signature Process]**: u kunt ervoor kiezen een document in een opeenvolgende of parallelle volgorde te ondertekenen. Eén ondertekenaar ontvangt het document op volgorde voor ondertekening. Nadat de eerste ondertekenaar het ondertekenen van het document heeft voltooid, wordt het document verzonden naar de tweede ondertekenaar, enzovoort. Parallel hieraan kunnen meerdere ondertekenaars een document tegelijk ondertekenen.
* **[!UICONTROL Redirection URL]**: geef een URL voor omleiding op. Nadat het document is ondertekend, kunt u de ontvanger omleiden naar een URL. Gewoonlijk bevat deze URL een bedankbericht of verdere instructies.
* **[!UICONTROL Workflow Stage]**: een werkstroom kan uit meerdere fasen bestaan. Deze stadia worden getoond in AEM Inbox. U kunt deze fasen definiëren in de eigenschappen van het model ( **[!UICONTROL Sidekick]** > **[!UICONTROL Page]** > **[!UICONTROL Page Properties]** > **[!UICONTROL Stages]** ).
* **[!UICONTROL Select Recipients]**: geef de methode op waarmee u ontvangers voor het document kunt kiezen. U kunt de workflow dynamisch toewijzen aan een gebruiker of groep of gegevens van een ontvanger handmatig toevoegen. Wanneer u Handmatig selecteert in de vervolgkeuzelijst, voegt u de gewenste gegevens toe, zoals E-mail, Rol en Verificatiemethode.

  >[!NOTE]
  >
  >* In de sectie Rol kunt u de rol van ontvanger opgeven als ondertekenaar, fiatteur, accepteerder, gecertificeerde ontvanger, invuller van formulier en gedelegeerde.
  >* Als u Delegator in de optie van de Rol selecteert, kan de Delegator de ondertekeningstaak aan een andere ontvanger toewijzen.
  >* Als u een verificatiemethode voor [!DNL Adobe Sign] hebt geconfigureerd, selecteert u op basis van uw configuratie een verificatiemethode zoals verificatie via telefoon, verificatie op basis van sociale identiteit, verificatie op basis van kennis en verificatie op basis van identiteit van de overheid.

* **[!UICONTROL Script or service to select recipients]**: De optie is alleen beschikbaar als u de optie Dynamisch selecteert in het veld Ontvangers selecteren. U kunt een ECMAScript of een dienst specificeren om ondertekenaars en verificatieopties voor een document te kiezen.
* **[!UICONTROL Recipient Details]**: De optie is alleen beschikbaar als de optie Handmatig is geselecteerd in het veld Ontvangers selecteren. Geef een e-mailadres op en kies een optioneel verificatiemechanisme. Voordat u een verificatiemechanisme met twee stappen selecteert, moet u controleren of de bijbehorende verificatieoptie is ingeschakeld voor de geconfigureerde [!DNL Adobe Sign] -account. U kunt een variabele van het gegevenstype String gebruiken om waarden voor de velden E-mail, Landcode en Telefoonnummer te definiëren. De velden Landcode en Telefoonnummer worden alleen weergegeven als u Telefoonverificatie selecteert in de vervolgkeuzelijst in twee stappen.
* **[!UICONTROL Signed Document]**: u kunt de status van het ondertekende document opslaan in Variabele. Als u een elektronisch audittrail voor handtekeningen wilt toevoegen voor meer beveiliging en wettigheid aan uw ondertekende document, kunt u Auditrapport opnemen. U kunt het ondertekende document opslaan in de map Variabele of Payload.

  >[!NOTE]
  >
  > Het auditrapport wordt toegevoegd aan de laatste pagina van het ondertekende document.

<!--
## Document Services steps {#document-services-steps}

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
* **[!UICONTROL Indirect accessible printer]**: The printer that is installed on a print server is accessed from other computers. Technologies such as the common UNIX&reg; printing system (CUPS) and the Line Printer Daemon (LPD) protocol are available to connect to a network printer. To access an indirect accessible printer, specify the print server's IP or host name. Using this mechanism, you can send a document to an LPD URI when the network has an LPD running. The mechanism lets you route the document to any printer that is connected to the network that has an LPD running.
    -->

## Afgedrukte uitvoerstap genereren {#generatePrintedOutput}

De stap genereert een PCL-, PostScript-, ZPL-, IPL-, TPCL- of DPL-uitvoer op basis van een formulierontwerp en een gegevensbestand. Het gegevensbestand wordt samengevoegd met het formulierontwerp en voor afdrukken opgemaakt. De uitvoer die door deze stap wordt gegenereerd, kan rechtstreeks naar een printer worden verzonden of als bestand worden opgeslagen. U wordt aangeraden deze stap te gebruiken als u formulierontwerpen of gegevens uit een toepassing wilt gebruiken. Als uw formulierontwerpen zich op het netwerk, het lokale bestandssysteem of de HTTP-locatie bevinden, gebruikt u de bewerking generatePrintedOutput.

Uw toepassing vereist bijvoorbeeld dat u een formulierontwerp samenvoegt met een gegevensbestand. De gegevens bevatten honderden records. Bovendien moet de uitvoer worden verzonden naar een printer die ZPL ondersteunt. Het formulierontwerp en uw invoergegevens bevinden zich in een toepassing. Met de bewerking generatePrintedOutput kunt u elke record samenvoegen met een formulierontwerp en de uitvoer verzenden naar een printer die ZPL ondersteunt.

De stap Afgedrukte uitvoer genereren heeft de volgende eigenschappen:

**[!UICONTROL Input properties]**

* **[!UICONTROL Select template file using]**: geef het pad van het sjabloonbestand op. U kunt het sjabloonbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt. Bovendien kunt u de laadgegevens ook accepteren als het invoergegevensbestand.

* **[!UICONTROL Select data document using]**: geef het pad op van een invoergegevensbestand. U kunt het invoergegevensbestand selecteren met het pad dat relatief is ten opzichte van de lading, opgeslagen op een absoluut pad of met een variabele van het gegevenstype Document. Bijvoorbeeld, [ Payload_Directory ] /Workflow/data.xml. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

* **[!UICONTROL Printer Format]**: Een waarde in de afdrukindeling die de beschrijvingstaal van de pagina opgeeft die moet worden gebruikt om de uitvoerstroom te genereren wanneer geen XDC-bestand wordt geleverd. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:

   * **[!UICONTROL color PCL]**: gebruik de optie om een XDC-bestand voor PCL op te geven.
   * **[!UICONTROL Generic PostScript]**: gebruik de optie om een algemeen XDC-bestand voor PostScript op te geven.
   * **[!UICONTROL ZPL 300 DPI]**: gebruik ZPL 300 DPI. Zpl300.xdc wordt gebruikt.
   * **[!UICONTROL ZPL 600 DPI]**: gebruik ZPL 600 DPI. Het bestand zpl600.xdc wordt gebruikt.
   * **[!UICONTROL IPL 300 DPI]**: gebruik IPL 300 DPI. Het bestand ipl300.xdc wordt gebruikt.
   * **[!UICONTROL IPL 400 DPI]**: gebruik IPL 400 DPI. Het bestand ipl400.xdc wordt gebruikt.
   * **[!UICONTROL TPCL 600 DPI]**: gebruik TPCL 600 DPI. Het bestand tpcl600.xdc wordt gebruikt.
   * **[!UICONTROL PostScript Plain]**: gebruik de optie om een XDC-bestand met normale tekst op te geven voor PostScript.
   * **[!UICONTROL DPL300DPI]**: gebruik DPL 300 DPI. De dpl300.xdc wordt gebruikt.
   * **[!UICONTROL DPL400DPI]**: gebruik DPL 400 DPI. De dpl400.xdc wordt gebruikt.
   * **[!UICONTROL DPL600DPI]**: gebruik DPL 600 DPI. De dpl600.xdc wordt gebruikt.
   * **[!UICONTROL HP_PCL_5e]**: gebruik de optie om meerdere Canon-apparaten te ondersteunen.


**[!UICONTROL Output Properties]**

* **[!UICONTROL Save output document using]**: geef de locatie op waar u het uitvoerbestand wilt opslaan. U kunt het uitvoerbestand opslaan op een locatie die relatief is ten opzichte van de lading, in een variabele of u kunt een absolute locatie opgeven om het uitvoerbestand op te slaan. Als het pad niet bestaat in de crx-gegevensopslagruimte, kan een beheerder het pad maken voordat het wordt gebruikt.

**[!UICONTROL Advanced Properties]**

* **[!UICONTROL Select Content Root location using]**: De hoofdmap van de inhoud is een tekenreekswaarde die de URI, absolute verwijzing of locatie in de gegevensopslagruimte opgeeft voor het ophalen van relatieve elementen die door het formulierontwerp worden gebruikt. Als het formulierontwerp bijvoorbeeld relatief verwijst naar een afbeelding, zoals `../myImage.gif` , moet `myImage.gif` at `repository://` zijn. De standaardwaarde is `repository://` , dat naar het hoofdniveau van de repository verwijst.

  Wanneer u een element kiest uit uw toepassing, moet het pad van de URI van de inhoudsbasis de juiste structuur hebben. Als bijvoorbeeld een formulier wordt gekozen uit een toepassing met de naam SampleApp en wordt geplaatst op `SampleApp/1.0/forms/Test.xdp` , moet de URI van de inhoudswortel worden opgegeven als `repository://administrator@password/Applications/SampleApp/1.0/forms/` of `repository:/Applications/SampleApp/1.0/forms/` (als de instantie null is). Wanneer de URI voor de inhoudsbasis op deze manier wordt opgegeven, worden de paden van alle middelen waarnaar wordt verwezen in het formulier, omgezet met deze URI.

* **[!UICONTROL Select XCI file using]**: XCI-bestanden worden gebruikt om lettertypen en andere eigenschappen te beschrijven die worden gebruikt voor formulierontwerpelementen. U kunt een XCI-bestand relatief ten opzichte van de payload, op een absoluut pad houden of een variabele van het gegevenstype Document gebruiken.

* **[!UICONTROL Locale]** - Geeft de taal aan die wordt gebruikt voor het genereren van het PDF-document. Als u een letterlijke waarde opgeeft, selecteert u een taal in de lijst of selecteert u een van de volgende waarden:
   * **[!UICONTROL To use server default]** :
(Standaard) Gebruik de landinstelling die op de [!DNL AEM Forms] -server is geconfigureerd. De landinstelling wordt geconfigureerd met de beheerconsole. (Zie [ Hulp van Designer ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/using-designer.pdf).)

   * **[!UICONTROL To use custom value]** :
Typ de landinstellingscode in het letterlijke vak of selecteer een tekenreeksvariabele die de landinstellingscode bevat. Ga naar https://docs.oracle.com/javase/1.5.0/docs/guide/intl/locale.doc.html voor een volledige lijst met ondersteunde landinstellingscodes.

* **[!UICONTROL Copies]**: Een geheel getal dat het aantal kopieën opgeeft dat voor de uitvoer moet worden gegenereerd. De standaardwaarde is 1.

* **[!UICONTROL Duplex Printing]**: Een pagineringswaarde die aangeeft of dubbelzijdig of enkelzijdig afdrukken moet worden gebruikt. Deze waarde wordt gebruikt voor printers die PostScript en PCL ondersteunen. Als u een letterlijke waarde opgeeft, selecteert u een van de volgende waarden:
   * **[!UICONTROL Duplex Long Edge]**: dubbelzijdig afdrukken en afdrukken met paginering op lange randen.
   * **[!UICONTROL Duplex Short Edge]**: dubbelzijdig afdrukken en afdrukken gebruiken met paginering op korte zijde.
   * **[!UICONTROL Simplex]**: enkelzijdig afdrukken gebruiken.

## Niet-interactieve PDF-uitvoerstap genereren   {#generatePDFdocuments}

1. Sleep de workflow Niet-interactieve PDF-uitvoer genereren onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]** .

### Invoerdocumenten {#input-documents-3}

* **Dossier van het Malplaatje**: Specificeert de plaats van het malplaatje XDP. Het is een verplicht veld.

* **Document van Gegevens**: Specificeert de plaats van gegevens xml die met het malplaatje moeten worden samengevoegd.

### Uitvoerdocument {#output-document}

**Document van de Output**: Specificeert de naam van de geproduceerde vorm van de PDF.

### Aanvullende parameters {#additional-parameters-1}

* **Wortel van de Inhoud**: Specificeert de weg aan de omslag in de bewaarplaats waar de fragmenten of de beelden die in het inputXDP malplaatje worden gebruikt worden opgeslagen.
* **Landinstelling**: Specificeert de standaardscène voor de geproduceerde vorm van PDF.
* **Versie van Acrobat**: Specificeert de gerichte versie van Acrobat voor de geproduceerde vorm van PDF.
* **Gelineariseerde PDF**: Specificeert of om de geproduceerde PDF voor Web het bekijken te optimaliseren.
* **Tagged PDF**: Specificeert of om de geproduceerde PDF toegankelijk te maken.
* **XCI document**: Specificeert de weg aan het XCI dossier.

## Zie ook {#see-also}

* [Variabelen in Forms-centric AEM Workflows](/help/forms/variable-in-aem-workflows.md)
* [Vorm uit Bureau het plaatsen](/help/forms/configure-out-of-office-settings.md)

<!--

>[!MORELIKETHIS]
>
>* [Forms-centric workflow on OSGi](/help/forms/aem-forms-workflow.md)
>* [Use AEM translation workflow to localize Adaptive Forms and Document of Record](/help/forms/using-aem-translation-workflow-to-localize-adaptive-forms.md)

-->