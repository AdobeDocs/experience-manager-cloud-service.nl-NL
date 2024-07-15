---
title: AEM Forms as a Cloud Service release notes
description: Meer informatie over nieuwe functies, bètareleases, pre-releasegegevens en meer voor AEM Forms as a Cloud Service.
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: 8ed477ec0c54bb0913562b9581e699c0bdc973ec
workflow-type: tm+mt
source-wordcount: '2003'
ht-degree: 1%

---


# [!DNL Experience Manager Forms] Opmerking bij as a Cloud Service release {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service ontvangt voortdurend verbeteringen. Bezoek deze pagina regelmatig om op de hoogte te blijven van de meest recente ontwikkelingen. Op deze pagina vindt u informatie over:

- Nieuwe functies
- Verbeteringen
- Functies vóór de release
- Beta-functies
- Bugfixes
- Afgekeurde functionaliteit
- Speciale instructies
- Geplande wijzigingen

>[!NOTE]
>
>Voor versienota&#39;s van alle andere de versiecomponenten van AEM as a Cloud Service, zie [ Huidige Nota&#39;s van de Versie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## 2021 10,0 {#sep-2021-10-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

- **Analytics voor Aanpassings Forms**: U kunt gedrag van zowel het programma geopende als niet het programma geopende (Anoniem) registreren nu vangen en volgen via Adobe Analytics voor Aanpassings Forms om gebruikersinzichten te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms-oct-2021}

- **externaliseer AEM gegevens van het Werkschema voor veilige verwerking**: U kunt in-proces AEM gegevens van de Werkschema&#39;s (AEM gegevens van de Variabelen van het Werkschema) opslaan die Gevoelige Persoonlijke Gegevens (SPD) elementen in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in AEM opslagplaats en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Beta-functies van [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [ Communicatie APIs ](aem-forms-cloud-service-communications.md) hulp u een malplaatje en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   - Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## 2021,9,0 {#sep-2021-09-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-sep-2021}

- **de rollen van Adobe Sign van het Gebruik in een Aangepaste Vorm**: Adobe Sign voor zaken en ondernemingsde dienstniveaus hebben de optie om de rollen voor de ontvangers van de Overeenkomst, voorbij enkel de Ondertekenaar, uit te breiden om hun werkschemavereisten beter aan te passen. U kunt [ elke ontvanger van overeenkomst nu toelaten om hun rol in een Aangepaste Vorm ](working-with-adobe-sign.md#addsignerstoanadaptiveform) te vormen, met Ondertekenaar die de standaardrol is.

- **Analytics voor Aanpassings Forms**: U kunt nu vangen en [ gebruikersgedrag als Adobe Analytics ](integrate-aem-forms-with-adobe-analytics.md) voor Aanpassings Forms volgen om gebruikersinzichten te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

- **verbindt gemakkelijk AEM Forms met de Dynamica en Salesforce van Microsoft**: De dienst verstrekt uit de configuratie van de doosgegevensbron en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, makend het [ sneller en gemakkelijker voor ontwikkelaars om de Dynamiek en Salesforce van Microsoft als gegevensbronnen voor een adaptieve vorm ](configure-msdynamics-salesforce.md) te vormen.

- **e-Onderteken een adaptieve vorm gebruikend DocuSign:** [ u kunt DocuSign gebruiken om een adaptieve vorm ](integrate-docusign-adaptive-forms.md) elektronisch te ondertekenen. De service biedt een aangepaste verzendactie om DocuSign te gebruiken met een adaptief formulier.

### Beta-functies van [!DNL Forms] {#sep-what-is-new-forms-prerelease}

- **Verenigde Schakelaar van de Opslag:** Gebruik Verenigde Schakelaar van de Opslag om in-procesgegevens in klant-beheerde bewaarplaatsen uit te voeren. Bijvoorbeeld, kunt u in-proces AEM de gegevens van Werkstromen (AEM gegevens van de Variabelen van het Werkschema) opslaan die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.
  <!--* Enable Forms Portal's save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [ Communicatie APIs ](aem-forms-cloud-service-communications.md) hulp u XDP malplaatjes en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   - Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Beperkingen {#limitations}

- Adobe Analytics kan de afmetingen van formulieren alleen bijhouden voor geverifieerde gebruikers.

<!--

### New features available in [!DNL Forms] prerelease channel {#prerelease-features-forms-sep-2021}

* **Forms Portal:**  In a typical forms-centric portal deployment scenario, forms development and portal development are two disjoint activities. While Form Designers design and store forms in a repository, Web Developers create a web application to list forms and handle submission of forms. Forms are copied over to the web tier as there is no communication between the forms repository and the web application.

  Such scenarios often result in management issues and production delays. For example, if there is a newer version of a form available in the repository, you need to replace the form on the web tier, modify the web application, and redeploy the form on the public site. Redeploying the web application might cause some server downtime. Typically, the server downtime is a planned activity and therefore the changes cannot be pushed to the public site instantaneously.

  AEM Forms provides portal components that reduce management overheads and production delays. The components equip Web Developers to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM). The form portal components allow you to add the following functionality:

  * List forms in customized layouts. Out of the box, List view and Card view are provided.

  * List published adaptive forms on an AEM Sites page.

  * Enable searching of forms based on a various criteria, such as form properties, metadata, and tags.

  * Lists drafts and submissions related to Adaptive Form created by user.

  -->

## 2021,8,0 {#aug-2021-08-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- AEM project Archetype voor Forms as a Cloud Service omvat [ modellen van vormgegevens voor de Dynamiek van Microsoft en Salesforce ](setup-local-development-environment.md).

- **op acroform-Gebaseerd Document van Verslag**: De as a Cloud Service steunen van AEM Forms die [ de Vorm van Adobe Acrobat PDF (Acroform PDF) gebruiken ](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) als malplaatje voor Document van Verslag naast op XFA-Gebaseerd vormmalplaatje.

- **Microsoft Azure schakelaar van de gegevensopslag**: U kunt [ het Model van de Gegevens van de Vorm aan Microsoft Azure Opslag ](configure-azure-storage.md) nu verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

### Beta-functie van [!DNL Forms] {#aug-what-is-new-forms-prerelease}

- **Verenigde Schakelaar van de Opslag:** Gebruik Verenigde Schakelaar van de Opslag om in-procesgegevens in klant-beheerde bewaarplaatsen uit te voeren. U kunt bijvoorbeeld

   - Schakel de functie Opslaan en hervatten van Forms Portal in en sla adaptieve formulierconcepten op in een gegevensopslagruimte onder beheer van de klant.
   - Sla AEM werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) op die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [ Communicatie APIs ](aem-forms-cloud-service-communications.md) hulp u XDP malplaatjes en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   - Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#prerelease-features-forms-aug-2021}

- **de rollen van Adobe Sign van het Gebruik in een Aangepaste Vorm**: Adobe Sign voor zaken en ondernemingsde dienstniveaus hebben de optie om de rollen voor de ontvangers van de Overeenkomst, voorbij enkel de Ondertekenaar, uit te breiden om hun werkschemavereisten beter aan te passen. U kunt [ elke ontvanger van overeenkomst nu toelaten om hun rol in een Aangepaste Vorm ](working-with-adobe-sign.md#addsignerstoanadaptiveform) te vormen, met Ondertekenaar die de standaardrol is.

- **Analytics voor Aanpassings Forms**: U kunt gebruikersgedrag nu vangen en volgen als Adobe Analytics voor Aanpassings Forms om gebruikersinzichten te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

- **verbindt gemakkelijk AEM Forms met de Dynamica en Salesforce van Microsoft**: De dienst verstrekt uit de configuratie van de doosgegevensbron en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, makend het [ sneller en gemakkelijker voor ontwikkelaars om de Dynamiek en Salesforce van Microsoft als gegevensbronnen voor een adaptieve vorm ](configure-msdynamics-salesforce.md) te vormen.

## 2021,7,0 {#july-2021-07-0}

### Nieuwe functies in [!DNL Forms] {#july-what-is-new-forms}

- U kunt de dienst van de Automatede form conversion nu gebruiken om [ PDF forms in het Frans, Duits, en Spaans taal ](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) in aanpassingsvormen om te zetten.
- Er is een apart deelvenster toegevoegd aan de sjablooneditor om fouten weer te geven die betrekking hebben op adaptieve formuliercomponenten. Hiermee kunt u alle adaptieve formulierfouten op één locatie consolideren en de resolutietijd verminderen.

### Nieuwe functies beschikbaar in [!DNL Forms] prereleasekanaal {#july-prerelease-features-forms}

- **op acroform-Gebaseerd Document van Verslag**: U kunt ook [ de Vorm van Adobe Acrobat PDF (Acroform PDF) ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als malplaatje voor Document van Verslag naast op XFA-Gebaseerd vormmalplaatje gebruiken.

- **Microsoft Azure schakelaar van de gegevensopslag**: U kunt [ het Model van de Gegevens van de Vorm aan Microsoft Azure Opslag ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html) nu verbinden. Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

- **Variabele die Extern van Gegevens**: U kunt gegevens van AEM variabelen van het Werkschema op een extern opslagsysteem bewaren door uw organisatie wordt geleid.

### Beta-functie van [!DNL Forms] {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [ Communicatie APIs ](aem-forms-cloud-service-communications.md) hulp u XDP malplaatjes en de gegevens van XML combineert om drukdocumenten in diverse formaten te produceren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   - Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

## 2021,6,0 {#july-2021-06-0}

### Nieuwe functies in [!DNL Forms] {#june-what-is-new-forms}

- Toegevoegde mogelijkheid om aangepaste kolommen in AEM Inbox te filteren.
- Mogelijkheid toegevoegd om de themaeditor en stijllaag van een aangepaste formuliereditor te gebruiken voor het opmaken van de component captcha.
- Verbeterde snelheid en nauwkeurigheid voor het automatisch detecteren van logische secties in de PDF forms van de bron en het converteren van deze secties naar overeenkomstige adaptieve formulierdeelvensters.
- Toegevoegde verplaatsingsactie om een PDF- of XDP-bestand van de ene map naar de andere te verplaatsen.

### Beta-functie van [!DNL Forms] {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: Met communicatie-API&#39;s kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:

   - Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF genereren op basis van een XFA-formulier PDF en een Adobe Acrobat-formulier (AcroForm).

- **Variabele die Extern van Gegevens**: U kunt gegevens van AEM variabelen van het Werkschema op een extern opslagsysteem bewaren door uw organisatie wordt geleid.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Buizen gecorrigeerd in [!DNL Forms] {#june-forms-bugs-fixed}

- Wanneer een veld wordt gevalideerd voordat gegevens via FDM (Form Data Model) naar de service Backend worden verzonden, slagen validaties erin, maar wordt postvalidatie niet aangeroepen door de service Form Data Model.
- Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Apple iOS 15.1 biedt een oplossing voor het probleem.

## 2021,5,0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#may-what-is-new-forms}

- **Contextafhankelijke hulp**: Toegevoegde contextafhankelijke hulp voor adaptieve vormenredacteur, malplaatjeredacteur, en themaredacteur om auteurs te helpen diverse eigenschappen van redacteurs beter begrijpen.
- **de berichten van de Fout in browser van Eigenschappen**: Toegevoegde foutenmeldingen voor elk bezit in Adaptieve browser van Eigenschappen van Forms. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

### De aanstaande bètafunctie van [!DNL Forms] {#may-what-is-new-forms-prerelease}

Uitvoer als cloudservice: de uitvoerservice helpt u bij het combineren van XDP-sjablonen en XML-gegevens om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone en asynchrone batchmodus. Met uitvoerservice kunt u toepassingen maken waarmee u:

- Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
- Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
- Afdruk-PDF genereren op basis van XFA-formulier-PDF.

U kunt schrijven naar formscsbeta@adobe.com om u aan te melden voor het bètaprogramma.

### Buizen gecorrigeerd in [!DNL Forms] {#may-forms-bugs-fixed}

- Wanneer u in een taakstap toewijzen van AEM Forms Workflows het standaardpictogram van de actieknoppen vervangt door een koraalpictogram, wordt de workflow beëindigd en wordt een uitzondering geregistreerd. De workflow wordt op de verwachte wijze uitgevoerd wanneer standaardpictogrammen worden gebruikt.
- Als u in de lay-outlaag het aantal kolommen wijzigt, de bewerkingslaag opent en enkele componenten in een deelvenster sleept, verschijnen er vierkante blauwe vakken in het inhoudsgebied van de adaptieve formuliereditor en reageert de editor niet meer.
- Foutbericht van een optie voor een regeleditor die betrekking heeft op het opgeven van een URL van een adaptief of extern element, is te lang en is niet gebruikersvriendelijk.

## 2021,4,0 {#april-2021-04-0}

### Nieuwe functies in [!DNL Forms] {#april-what-is-new-forms}

- **Identiteitsauthentificatiemethode van identiteitskaart van de Overheid van het Gebruik in Adobe Sign toegelaten Aangepaste Forms**

  Met behulp van geavanceerde computerleeralgoritmen kunnen bedrijven over de hele wereld dankzij het Adobe Sign-proces voor overheidsidentiteitskaart een kwalitatief hoogstaande verificatie van de identiteit van hun ontvanger krijgen. Nu kunt u de methode voor identiteitsverificatie van overheidsidentiteiten gebruiken in met Adobe Sign ingeschakelde Adaptive Forms.

  Identiteitskaart van de overheid is een methode van de identiteitsauthentificatie van de premie die de ontvanger opdraagt [ het beeld van een door de overheid uitgegeven identiteitsdocument (rijbewijs, nationale identiteitskaart, paspoort) ](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html) te uploaden, en dan dat document te evalueren om het authentiek te verzekeren.

- **Steun om in-vorm het ondertekenen ervaring voor asynchrone adaptieve vormverzendingen te gebruiken**

  U kunt de ondertekeningservaring in formulieren nu gebruiken voor asynchrone, adaptieve verzending van formulieren. U kunt ook een adaptief formulier insluiten in een [!DNL Experience Manager Sites] -pagina en de ondertekeningservaring in formulieren gebruiken voor het verzenden van aangepaste formulieren.

- **Steun om een variabele te gebruiken om een gehechtheid te specificeren terwijl het prepopuleren van een AanpassingsVorm voor een Assign stap van de Taak**

  Terwijl u een adaptief formulier vooraf invult voor een toewijzingsstap, kunt u nu een variabele van het documenttype gebruiken om een invoerbijlage te selecteren voor het adaptieve formulier.

- **Steun om de letterlijke optie te gebruiken om waarde voor een JSON type variabele** te plaatsen

  U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

- **de lokale ontwikkelomgeving van het Gebruik om Document van Verslag tot stand te brengen (DoR)**

  U kunt een XDP als Document van het malplaatje van het Verslag op de instanties van de Cloud Service en as a Cloud Service SDK van AEM Forms (Lokale ontwikkelomgeving) gebruiken. Eerder was de ondersteuning beperkt tot alleen Cloud Servicen.

### Opgeloste problemen in [!DNL Forms] {#april-bug-fixes-forms}

- Wanneer een Adaptief formulier dat is geconfigureerd om Document of Record niet te genereren, wordt verzonden naar een AEM Workflow die is geconfigureerd om Document of Record te genereren, wordt geen foutbericht weergegeven en kan de taak niet worden verzonden.
