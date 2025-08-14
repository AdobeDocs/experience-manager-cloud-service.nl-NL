---
title: Nota's van de versie voor 2024.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.11.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 3fd6482e-66f0-48ee-983c-4cb6b7742dcd
source-git-commit: bb149cd43158bfd1ceb43b04cc536c8c8291f968
workflow-type: tm+mt
source-wordcount: '1810'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.11.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.11.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.11.0) is 21 november 2024. De volgende release met functies (2025.1.0) is gepland voor 30 januari 2025.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Heb een blik bij de Video van het Overzicht van de Versie van november 2024 voor een samenvatting van de eigenschappen die in de versie 2024.11.0 worden toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

**[!DNL Edge Delivery Services]Paginasjablonen met Universal Editor-ontwerp**

U kunt elke Edge Delivery-pagina snel veranderen in een paginasjabloon. Hierdoor kunt u een nieuwe pagina met een vooraf gedefinieerde structuur en inhoud starten in plaats van een lege pagina. [ las meer ](/help/sites-cloud/authoring/universal-editor/templates.md).

**[!DNL Edge Delivery Services]CSV-importmodule voor publicatie via een AEM-instantie**

Beheer uw Edge Delivery-spreadsheetgegevens (bijvoorbeeld omleidingen) efficiënt in uw favoriete spreadsheetprogramma en upload deze naar AEM via de nieuwe CSV-importmodule. [ las meer ](https://www.aem.live/docs/authoring-tabular-data).

### Prerelease-mogelijkheden in AEM Sites

Verbeterd [ het Fragment van de Inhoud die met unieke op identiteitskaart-Gebaseerde verwijzingen ](/help/headless/graphql-api/uuid-reference-upgrade.md) van verwijzingen verwijzen, die stabiele verbindingen verzekeren die geldig blijven zelfs wanneer de activa of de fragmenten worden bewogen, die de behoefte aan updates elimineren of opnieuw publiceren. Huidige beperking: paginaverwijzingen worden nog niet ondersteund met unieke id&#39;s. Als er in inhoudsfragmenten wordt verwezen naar pagina&#39;s, mag deze mogelijkheid niet worden gebruikt.

### Programma voor vroege adoptie {#sites-early-adopter}

**AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud**

[ AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud ](/help/headless/aem-content-fragment-delivery-with-openapi.md), is nu beschikbaar voor AEM as a Cloud Service.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functies voor vroege toegang in dynamische media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. Deze bijschriften helpen te voldoen aan toegankelijkheidsvereisten en verbeteren de videobetrokkenheid van gebruikers die op tekst gebaseerde videoondersteuning gebruiken of verkiezen.

Om vroege toegang tot AI-Gegenereerde titelsteun op uw Dynamische rekening van Media te krijgen, [ creeer en voorlegt een geval van de Steun van de Klant van Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

**Dynamisch rapport van de Levering van Media**

Krijg leveringsinzichten voor activa die met Dynamische Media worden geleverd, met de telling van de levering op activaniveau, verwijzende informatie, activaweg in AEM Assets en unieke activa ID. Er kunnen rapporten worden gegenereerd voor alle elementen die via Dynamic Media voor AEM Assets-opslagplaats worden geleverd of voor een specifieke maphiërarchie in AEM Assets. Met behulp van inzichten kunt u het rendement van de geleverde middelen meten, de kanaalprestaties meten en weloverwogen taken voor middelenbeheer voor middelen uitvoeren.

Om vroege toegang tot het Dynamische Rapport van de Levering van Media op uw Dynamische rekening van Media te krijgen, [ creeer en voorlegt een geval van de Steun van de Klant van Adobe ](https://helpx.adobe.com/nl/enterprise/using/support-for-experience-cloud.html).

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**Dynamisch paneel van Media**

In de Assets-weergave hebt u nu toegang tot Dynamic Media en Dynamic Media met OpenAPI-uitvoeringen vanuit een apart deelvenster dat u ter beschikking wordt gesteld. U kunt ervoor kiezen de leverings-URL te kopiëren of de uitvoeringen te downloaden op basis van het element- en weergavetype. Voor meer informatie, zie [ Dynamische vertoningen van Media ](/help/assets/renditions.md#dynamic-media-renditions) en [ Dynamische Media met OpenAPI mogelijkheden vertoningen ](/help/assets/renditions.md#dm-with-openapi-renditions).

![ dynamische vertoningen ](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in AEM Forms {#forms-new-features}

* **[het werkingsgebied van het Ondertekenen van Adobe van de Update gemakkelijk](/help/forms/adobe-sign-integration-adaptive-forms.md)**: U kunt het werkingsgebied van een configuratie van het Ondertekenen van Adobe direct van de pagina van de Configuraties van de Wolk van AEM wijzigen, makend het sneller en gemakkelijker om bestaande configuraties bij te werken.

* **[Asynchrone functiesteun voor Adaptieve Forms](/help/forms/using-async-funct-in-rule-editor.md)**: Wanneer uw Aanpassings Vorm asynchrone verrichtingen, zoals het wachten op externe processen of gegevensherwinning vereist, kunt u deze verrichtingen met douanefuncties uitvoeren en hen vormen in de Redacteur van de Regel.

### Functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

* **beheer Publicatie**: U kunt het Manage werkschema van de Publicatie gebruiken om formulieren over milieu&#39;s, typisch van de auteursinstantie aan te publiceren en voorproef instantie(s) te publiceren of unpublish. Gebruikers kunnen de publicatie van inhoud op een gestroomlijnde manier publiceren, ongedaan maken of plannen.

* **[auto-sparen een ontwerp voor de Componenten van de Kern baseerde Adaptieve Forms](/help/forms/save-core-component-based-form-as-draft.md)**: De gebruikers kunnen nu van een auto-sparen eigenschap profiteren die een gedeeltelijk voltooide vorm als ontwerp automatisch opslaat. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.

* **[de redacteursverhogingen van de Regel](/help/forms/invoke-service-enhancements-rule-editor.md)**: Voor Aanpassings Forms die op de Componenten van de Kern wordt gebaseerd, kunt u dropdown opties nu bevolken gebruikend de output van de Invoke Dienst, reeks herhaalbare panelen gebruikend de output van de InvokeDienst, en gebruik de outputparameter van de InvokeDienst om andere gebieden te bevestigen.

* **[verbeter de Ervaring van de Gebruiker met de Knopen van de Navigatie in Comité Lay-outs](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: U kunt navigatieknopen aan uw paneellay-outs, zoals Horizontale Lusjes, Verticale Lusjes, Accordeons, of Tovenaar nu toevoegen. Met deze knoppen vergroot u de gebruikerservaring door de overgangen tussen deelvensters te vereenvoudigen en de focus op het geselecteerde deelvenster te richten.


### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)

#### Integrations

* **[integreer Aanpassings Forms met Adobe Marketo Engage](/help/forms/integrate-form-to-marketo-engage.md)**: AEM Forms as a Cloud Service omvat nu een makkelijk te gebruiken optie om Aanpassings Forms met Adobe Marketo Engage te verbinden. Dankzij deze integratie kunt u Adaptive Forms rechtstreeks maken met behulp van Marketo Engage lead capture en verwante aangepaste objecten. U kunt nu formuliervelden vooraf invullen met gegevens van Marketo Engage en gegevens terugsturen om workflows zoals slimme campagnes en e-mailautomatisering te automatiseren. U kunt ook een adaptief formulier verbinden met de Munchkin-bibliotheek om het aantal bezoeken, klikken en verzonden formulieren bij te houden.

#### Adaptieve Forms en HTML5 Forms

* **[creeer Aangepast Forms dat op bestaand malplaatje XFA](/help/forms/create-adaptive-form-using-xfa-templates.md)** wordt gebaseerd: U kunt tot de Component-Gebaseerde Aangepaste Forms van de Kern nu leiden gebruikend XFA vormmalplaatjes (*.XDP dossiers). Dankzij deze mogelijkheid kunnen AEM Forms On-Premise klanten met bestaande investeringen in XFA-technologie AEM Forms as a Cloud Service aannemen.

* **HTML5 Forms (op XFA-Gebaseerde Vormen van het Web)**: Nu, kunnen de klanten die van AEM Forms op locatie XFA technologie gebruiken moeiteloos overgang naar AEM Forms as a Cloud Service terwijl het bewaren van hun bestaande gebruikerservaring met HTML5 Forms (op XFA-Gebaseerde Vormen van het Web). Met deze functie wordt de weergave van XFA-formuliersjablonen in HTML5-indeling mogelijk, waardoor formulieren toegankelijk worden gemaakt voor apparaten die geen XFA-gebaseerde PDF forms ondersteunen.

  ![ HTML Forms (op XFA-Gebaseerde Vormen van het Web) ](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[Base64 de Gecodeerde Steun van het Koord voor de Bijlage van het Dossier ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)**: De component van de Bijlage van het Dossier in Aanpassende Forms die op de Componenten van de Kern wordt gebaseerd omvat nu een optie om dossiers in bijlage als Base64-Gecodeerde koorden voor te leggen.

#### Interactieve communicatie- en communicatie-API&#39;s

* **Interactieve Communicatie Redacteur**: De Interactieve Communicatie Redacteur is een gebruikersvriendelijk, grafisch Communicatie ontwerphulpmiddel dat de verwezenlijking van gepersonaliseerde, gegeven-gedreven correspondentie vereenvoudigt en in om het even welke moderne browser loopt. Het steunt naadloze gegevensintegratie, ingewikkelde logische definitie, en rijke media integratie, die professioneel en volgzaam document, Communicatie, en malplaatjegeneratie voor diverse bedrijfsbehoeften verzekeren.

  ![ Interactieve Communicatie Redacteur ](/help/forms/assets/ic-editor.png)


* **[de Verbeteringen van de Naleving PDF/A](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)**: U kunt Communicatie APIs nu gebruiken om de documenten van PDF in formaten PDF/A (1a, 2a, 3a) voor archiveringsdoeleinden om te zetten terwijl het verzekeren van toegankelijkheid en het controleren van naleving van deze normen.


* **[handtekening API (Document Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)**: Een nieuwe RESTful API in Communicatie APIs laat gemakkelijk beheer van de handtekeningen van PDF toe. Deze ondersteunt bewerkingen zoals:
   * Handtekening wissen: verwijdert een handtekening uit een opgegeven veld.
   * Handtekeningveld verwijderen: hiermee wordt een opgegeven handtekeningveld verwijderd.

<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## Automated Forms Conversion Service

* **[zet PDF forms in de Componenten van de Kern om Gebaseerde Aangepaste Forms ](https://experienceleague.adobe.com/nl/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)**: U kunt de Geautomatiseerde Dienst van de Omzetting van Vormen nu gebruiken om PDF forms, AcroForms, of op XFA-Gebaseerde vormen in de Componenten van de Kern Aangepaste Forms om te zetten.

>[!IMPORTANT]
>
> Wil je deelnemen aan het programma voor vroege toegang voor Forms-innovatie? Verzend een e-mail van uw officieel adres naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) met de lijst van mogelijkheden die u in geinteresseerd bent.## CIF Add-on {#cloud-services-cif}

## CIF-invoegtoepassing {#cif}

### Bugfixes {#bug-fixes-cif}

* Correctie van UI-tests voor correct werken met Core CIF-componenten.
* Correctie van het probleem waarbij de categorie-URL-indeling niet werkte zoals verwacht in de cloud-instantie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Verbeterde boomstructuurreplicatieprestaties (en veroudering van de workflow voor de publicatiestructuur) {#tree-replication-performance}

[ de Stap van het Werkschema van de Activering van de Boom ](/help/operations/replication.md#tree-activation) is een nieuwe stap van het werkschemamodel die voor het herhalen van diepe inhoudshiërarchieën wordt geadviseerd. Nota, staat het onafhankelijke replicaties (b.v. door snel te publiceren of publicatie te beheren) toe om parallel aan de lopende boom replicatiewerkschema te werk te gaan. Dit is vooral nuttig als u wat tijd-gevoelige inhoud moet publiceren terwijl een bulkreplicatie nog bezig is. De Stap van de Replicatie van de boom vervangt de Publish Werkstroom van de Inhoudsboom en zijn verwante Stap van het Werkschema, die nu verouderd zijn.

### API&#39;s op basis van OpenAPI&#39;s - Vroege adopter-programma {#open-apis-earlyadopter}

Ontwikkelaars kunnen AEM als Cloud Service-functies diep integreren in hun eigen toepassingen en tools. Nieuwe AEM as a Cloud Service API&#39;s volgen de OpenAPI-specificatie, met als doel consistent, goed gedocumenteerd en gebruikersvriendelijk te zijn. De geloofsbrieven voor eindpunten die authentificatie vereisen zullen worden geproduceerd door de projecten van Adobe Developer Console te creëren.

Leer meer over [ OpenAPI-Gebaseerde AEM APIs ](/help/implementing/developing/open-api-based-apis.md) en probeer uit een [ leerprogramma van begin tot eind ](https://experienceleague.adobe.com/nl/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) die configuratie en gebruik illustreren.

Concreet zijn de API-eindpunten die hieronder worden vermeld, beschikbaar als onderdeel van een programma voor vroege adoptie. Als geinteresseerd, e-mail [ aem-apis@adobe.com ](mailto:aem-apis@adobe.com) beschrijvend hoe u van hen van plan bent gebruik te maken.
* [ de Fragmenten APIs van de Inhoud van Plaatsen ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)
* [ Assets APIs ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* API&#39;s voor sites en Assets-mappen
* [ Communicatie APIs van Forms ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge Computing - Verzoek om feedback! {#edge-computing-feedback}

Edge Computing brengt gegevensverwerking dichter bij de browser, wat voordelen heeft, zoals minder latentie. Als input in de roadmap, zouden wij graag horen als u deze technologie nuttig voor de projecten van de Publicatie van AEM en van Edge Delivery Services en zou vinden waarvoor u het gebruikt. E-mail [ aemcs-edgecompute-feedback@adobe.com ](mailto:aemcs-edgecompute-feedback@adobe.com) met vragen en commentaren!

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit een vernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe verwelkomt terugkoppelen, die u aan [ aemcs-new-devconsole-ui-beta@adobe.com ](mailto:aemcs-new-devconsole-ui-beta@adobe.com) kunt e-mailen

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [ hier ](https://experienceleague.adobe.com/nl/docs/release-notes/experience-cloud/current) vinden.
