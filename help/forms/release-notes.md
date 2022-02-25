---
title: '"[!DNL AEM Forms] as a Cloud Service opmerkingen bij de release"'
description: '"[!DNL AEM Forms] as a Cloud Service opmerkingen bij de release"'
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: bc4da79735ffa99f8c66240bfbfd7fcd69d8bc13
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 2%

---


# [!DNL Experience Manager Forms] as a Cloud Service releaseopmerking {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service ontvangt voortdurend verbeteringen. Bezoek deze pagina regelmatig om op de hoogte te blijven van de meest recente ontwikkelingen. Op deze pagina vindt u informatie over:

- Nieuwe functies
- Verbeteringen
- Functies vóór de release
- Bètafuncties
- Bugfixes
- Afgekeurde functionaliteit
- Speciale instructies
- Geplande wijzigingen

>[!NOTE]
>
>Voor versienota&#39;s van alle andere AEM as a Cloud Service versiecomponenten, zie [Opmerkingen bij de huidige release](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html).

## 2021 10,0 {#sep-2021-10-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-oct-2021}

- **Analyses voor Adaptive Forms**: U kunt nu gedrag vastleggen en bijhouden van zowel aangemelde als niet-aangemelde (anonieme) gebruikers via Adobe Analytics for Adaptive Forms om inzichten van eindgebruikers te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms-oct-2021}

- **Externe AEM workflowgegevens voor veilige verwerking**: U kunt AEM werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) opslaan die de gevoelige elementen van Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats voor veilige verwerking bevatten. De gegevenselementen en workflowvariabelen worden niet opgeslagen in AEM opslagplaats en worden op verzoek opgehaald van een door de klant beheerde opslagplaats tijdens de verwerking van de Workflow.

### Bètafuncties van [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](aem-forms-cloud-service-communications.md) Hiermee kunt u een sjabloon en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus en in batchmodus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   - Genereer documenten door sjabloonbestanden (PDF en XDP) te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

## 2021,9,0 {#sep-2021-09-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-sep-2021}

- **Adobe Sign-rollen gebruiken in een adaptief formulier**: Adobe Sign for business and enterprise service levels hebben de mogelijkheid om de rollen voor overeenkomstontvangers uit te breiden, tot buiten alleen de ondertekenaar, zodat ze beter kunnen voldoen aan hun workflowvereisten. U kunt nu [elke ontvanger van de overeenkomst in staat stellen zijn rol in een adaptief formulier te configureren](working-with-adobe-sign.md#addsignerstoanadaptiveform), waarbij Ondertekenaar de standaardrol is.

- **Analyses voor Adaptive Forms**: U kunt nu vastleggen en [eindgebruikersgedrag volgen via Adobe Analytics](integrate-aem-forms-with-adobe-analytics.md) voor Adaptive Forms om inzichten van eindgebruikers te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

- **Verbind AEM Forms eenvoudig met Microsoft Dynamics en Salesforce**: De dienst verstrekt uit de doos gegevensbronconfiguratie en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, makend het [ontwikkelaars kunnen Microsoft Dynamics en Salesforce sneller en eenvoudiger configureren als gegevensbronnen voor een adaptief formulier](configure-msdynamics-salesforce.md).

- **Een adaptief formulier elektronisch ondertekenen met DocuSign:** [U kunt DocuSign gebruiken om een adaptief formulier elektronisch te ondertekenen](integrate-docusign-adaptive-forms.md). De service biedt een aangepaste verzendactie om DocuSign te gebruiken met een adaptief formulier.

### Bètafuncties van [!DNL Forms] {#sep-what-is-new-forms-prerelease}

- **Unified Storage-connector:** Gebruik Unified Storage Connector om procesgegevens in door de klant beheerde opslagruimten extern te maken. Bijvoorbeeld, kunt u in-proces AEM de gegevens van Werkstromen (AEM gegevens van de Variabelen van het Werkschema) opslaan die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](aem-forms-cloud-service-communications.md) Hiermee kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
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

  * Lists drafts and submissions related to Adaptive Form created by end user.

  -->

## 2021,8,0 {#aug-2021-08-0}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- AEM Archetype-project voor Forms as a Cloud Service omvat nu [modellen met formuliergegevens voor Microsoft Dynamics en Salesforce](setup-local-development-environment.md).

- **Op acroform gebaseerd document of record**: as a Cloud Service AEM Forms-ondersteuning gebruiken [Adobe Acrobat Form PDF (Acroform PDF)](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) als een sjabloon voor Document of Record naast XFA-formuliersjabloon.

- **Microsoft Azure Data Store-connector**: U kunt nu [Formuliergegevensmodel verbinden met Microsoft Azure Storage](configure-azure-storage.md). Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

### Beta-functie van [!DNL Forms] {#aug-what-is-new-forms-prerelease}

- **Unified Storage-connector:** Gebruik Unified Storage Connector om procesgegevens in door de klant beheerde opslagruimten extern te maken. U kunt bijvoorbeeld

   - Schakel de functie Opslaan en hervatten van Forms Portal in en sla adaptieve formulierconcepten op in een gegevensopslagruimte onder klantbeheer.
   - Sla AEM werkstroomgegevens (AEM gegevens van de Variabelen van het Werkschema) op die Gevoelige Persoonlijke Gegevens (SPD) in een klant-beheerde bewaarplaats bevatten.

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](aem-forms-cloud-service-communications.md) Hiermee kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   - Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#prerelease-features-forms-aug-2021}

- **Adobe Sign-rollen gebruiken in een adaptief formulier**: Adobe Sign for business and enterprise service levels hebben de mogelijkheid om de rollen voor overeenkomstontvangers uit te breiden, tot buiten alleen de ondertekenaar, zodat ze beter kunnen voldoen aan hun workflowvereisten. U kunt nu [elke ontvanger van de overeenkomst in staat stellen zijn rol in een adaptief formulier te configureren](working-with-adobe-sign.md#addsignerstoanadaptiveform), waarbij Ondertekenaar de standaardrol is.

- **Analyses voor Adaptive Forms**: U kunt het gedrag van de eindgebruiker nu vastleggen en volgen via Adobe Analytics for Adaptive Forms om inzichten van de eindgebruiker te verzamelen. Het helpt geïnformeerde beslissingen te nemen op basis van gegevens om de gebruikerservaring te verbeteren.

- **Verbind AEM Forms eenvoudig met Microsoft Dynamics en Salesforce**: De dienst verstrekt uit de doos gegevensbronconfiguratie en gegevensmodellen voor de Dynamica en Salesforce van Microsoft, makend het [ontwikkelaars kunnen Microsoft Dynamics en Salesforce sneller en eenvoudiger configureren als gegevensbronnen voor een adaptief formulier](configure-msdynamics-salesforce.md).

## 2021,7,0 {#july-2021-07-0}

### Nieuwe functies in [!DNL Forms] {#july-what-is-new-forms}

- U kunt de dienst van de Automatede form conversion nu gebruiken aan [PDF forms converteren in het Frans, Duits en Spaans](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) aan adaptieve formulieren.
- Een apart deelvenster toegevoegd aan de sjablooneditor om fouten weer te geven die betrekking hebben op adaptieve formuliercomponenten. Hiermee kunt u alle adaptieve formulierfouten op één locatie consolideren en de resolutietijd verminderen.

### Nieuwe functies beschikbaar in [!DNL Forms] prerelease-kanaal {#july-prerelease-features-forms}

- **Op acroform gebaseerd document of record**: U kunt ook [Adobe Acrobat Form PDF gebruiken (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html) als een sjabloon voor Document of Record naast XFA-formuliersjabloon.

- **Microsoft Azure Data Store-connector**: U kunt nu [Formuliergegevensmodel verbinden met Microsoft Azure Storage](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). Hiermee kunt u adaptieve formuliergegevens ophalen en opslaan naar Microsoft Azure Storage als een BLOB.

- **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat door uw organisatie wordt beheerd.

### Beta-functie van [!DNL Forms] {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Communicatie-API&#39;s](aem-forms-cloud-service-communications.md) Hiermee kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:
   - Genereer documenten door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF-bestanden genereren op basis van een XFA-formulier met PDF en Adobe Acrobat-formulier.

## 2021,6,0 {#july-2021-06-0}

### Nieuwe functies in [!DNL Forms] {#june-what-is-new-forms}

- Toegevoegde mogelijkheid om aangepaste kolommen in AEM Inbox te filteren.
- Mogelijkheid toegevoegd om de themaeditor en stijllaag van een aangepaste formuliereditor te gebruiken voor het opmaken van de component captcha.
- Verbeterde snelheid en nauwkeurigheid voor het automatisch detecteren van logische secties in de bron-PDF forms en het converteren van deze secties naar overeenkomstige adaptieve formulierdeelvensters.
- Toegevoegde verplaatsingsactie om een PDF- of XDP-bestand van de ene map naar de andere te verplaatsen.

### Beta-functie van [!DNL Forms] {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: Via communicatie-API&#39;s kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone modus. Met de API&#39;s kunt u toepassingen maken waarmee u:

   - Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
   - Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   - Afdruk-PDF genereren op basis van een XFA-formulier PDF en een Adobe Acrobat-formulier (AcroForm).

- **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat door uw organisatie wordt beheerd.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Buizen vastgesteld in [!DNL Forms] {#june-forms-bugs-fixed}

- Wanneer een veld wordt gevalideerd voordat gegevens worden verzonden naar de service Back-end via het Form Data Model (FDM), slagen validaties erin, maar wordt postvalidatie niet aangeroepen door de service Form Data Model.
- Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Apple iOS 15.1 biedt een oplossing voor het probleem.

## 2021,5,0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#may-what-is-new-forms}

- **Contextafhankelijke Help**: Er is contextafhankelijke Help toegevoegd voor een aangepaste formuliereditor, sjablooneditor en themaeditor, zodat ontwerpers meer inzicht kunnen krijgen in verschillende functies van editors.
- **Foutberichten in de browser Eigenschappen**: Foutberichten toegevoegd voor elke eigenschap in de browser Adaptive Forms Properties. Met deze berichten kunt u de toegestane waarden voor een veld beter begrijpen.

### De aanstaande bètafunctie van [!DNL Forms] {#may-what-is-new-forms-prerelease}

Uitvoeren als cloudservice: Met de uitvoerservice kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met deze service kunt u documenten genereren in synchrone en asynchrone batchmodus. Met uitvoerservice kunt u toepassingen maken waarmee u:

- Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
- Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
- Afdruk-PDF genereren op basis van XFA-formulier-PDF.

U kunt schrijven naar formscsbeta@adobe.com om u aan te melden voor het bètaprogramma.

### Buizen vastgesteld in [!DNL Forms] {#may-forms-bugs-fixed}

- Wanneer u in een taakstap toewijzen van AEM Forms Workflows het standaardpictogram van de actieknoppen vervangt door een koraalpictogram, wordt de workflow beëindigd en wordt een uitzondering geregistreerd. De workflow wordt op de verwachte wijze uitgevoerd wanneer standaardpictogrammen worden gebruikt.
- Als u in de lay-outlaag het aantal kolommen wijzigt, de bewerkingslaag opent en enkele componenten in een deelvenster sleept, verschijnen er vierkante blauwe vakken in het inhoudsgebied van de adaptieve formuliereditor en reageert de editor niet meer.
- Foutbericht van een optie voor een regeleditor die betrekking heeft op het opgeven van een URL van een adaptief of extern element, is te lang en is niet gebruikersvriendelijk.

## 2021,4,0 {#april-2021-04-0}

### Nieuwe functies in [!DNL Forms] {#april-what-is-new-forms}

- **Gebruik de methode voor identiteitsverificatie van overheidsidentiteiten in met Adobe Sign ingeschakelde Adaptieve Forms**

   Met behulp van geavanceerde computerleeralgoritmen kunnen bedrijven over de hele wereld dankzij het Adobe Sign-proces voor overheidsidentiteitskaart een kwalitatief hoogstaande verificatie van de identiteit van hun ontvanger krijgen. Nu kunt u de methode voor identiteitsverificatie van overheidsidentiteiten gebruiken in met Adobe Sign ingeschakelde Adaptive Forms.

   De identiteitskaart van de overheid is een methode van de identiteitsauthentificatie van de premie die de ontvanger aan opdraagt [het beeld uploaden van een door de overheid afgegeven identiteitsdocument (rijbewijs, nationale identiteitskaart, paspoort)](https://helpx.adobe.com/in/sign/using/adobesign-authentication-government-id.html)en evalueert vervolgens dat document om te controleren of het authentiek is.

- **Ondersteuning voor het gebruik van ondertekeningservaring in formulieren voor asynchrone, adaptieve verzending van formulieren**

   U kunt de ondertekeningservaring in formulieren nu gebruiken voor asynchrone, adaptieve verzending van formulieren. U kunt ook een adaptief formulier insluiten in een [!DNL Experience Manager Sites] pagina en gebruik de ondertekeningservaring in formulieren voor het verzenden van aangepaste formulieren.

- **Ondersteuning voor het gebruik van een variabele om een bijlage op te geven terwijl een adaptief formulier vooraf wordt ingevuld voor een taakstap Toewijzen**

   Terwijl u een adaptief formulier vooraf invult voor een toewijzingsstap, kunt u nu een variabele van het documenttype gebruiken om een invoerbijlage te selecteren voor het adaptieve formulier.

- **Ondersteuning voor het gebruik van de letterlijke optie voor het instellen van de waarde voor een JSON-typevariabele**

   U kunt letterlijke optie gebruiken om waarde voor een JSON typevariabele in de vastgestelde veranderlijke stap van een AEM Werkstroom te plaatsen. Met de letterlijke optie kunt u een JSON opgeven in de vorm van een tekenreeks.

- **De lokale ontwikkelomgeving gebruiken om Document of Record (DoR) te maken**

   U kunt een XDP als Document van het malplaatje van het Verslag op de instanties van de Cloud Service en as a Cloud Service SDK van AEM Forms (Lokale ontwikkelomgeving) gebruiken. Eerder was de ondersteuning beperkt tot alleen Cloud Servicen.

### Bugfixes in [!DNL Forms] {#april-bug-fixes-forms}

- Wanneer een Adaptief formulier dat is geconfigureerd om Document of Record niet te genereren, wordt verzonden naar een AEM Workflow die is geconfigureerd om Document of Record te genereren, wordt geen foutbericht weergegeven en kan de taak niet worden verzonden.
