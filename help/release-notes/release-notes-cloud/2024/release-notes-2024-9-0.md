---
title: Nota's van de versie voor 2024.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.9.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 75ecd154-112a-4468-9962-de50bb1f4cd0
source-git-commit: 1481983bde41bda51e725930bae492aa599b6c93
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.9.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.9.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.9.0) is 26 september 2024. De volgende release met functies (2024.10.0) is gepland voor 31 oktober 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van september 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.9.0:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

#### Vertaalbeheer {#translation-management}

AEM-workflows voor vertaling en API-acties activeren nu gebeurtenissen om insight informatie te verschaffen over wijzigingen in de status van vertaaltaken. Gebruikers kunnen zich op deze gebeurtenissen abonneren via de Adobe Developer Console. Zie [ hier ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/) voor meer informatie over AEM Vertaalbeheer API.

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.


## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functie voor vroege toegang in dynamische media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. These captions help meet accessibility requirements and improve video engagement for audiences who rely on or prefer text-based video support.

To get early access to AI-generated captions support on your Dynamic Media account, [create and submit an Adobe Customer Support case](/help/assets/dynamic-media/video.md##enable-dash).

### Nieuwe functies in Asset Selector {#asset-selector-new-features}

Asset Selector biedt nu ondersteuning voor het bladeren in verzamelingen naar het gewenste element.
![ de selecteursinzamelingen van Activa ](/help/assets/assets/collections-rail-modal-view.png)

### Nieuwe functies in Content Hub {#content-hub-new-features}

Administrators can now control if they need expired assets to be visible on Content Hub. If the expired assets are made visible, they can also define if users can download them.

![Expired assets on Content Hub](/help/assets/assets/view-download-expired-assets.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### New Pre-release features in AEM Forms {#forms-new-prerelease-features}

#### Auto-save a draft for Core Components based Adaptive Forms

Gebruikers kunnen nu profiteren van een functie voor automatisch opslaan, waarmee een gedeeltelijk ingevuld formulier automatisch als concept wordt opgeslagen. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.


### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### AEM Forms AI Assistant

Generative AI voor Adaptive Forms biedt een heel nieuw niveau van kracht en maakt het ontwikkelen van formulieren eenvoudiger. It allows you to build better forms faster than ever before.

![ Generatieve AI Medewerker, Aangepaste Forms ](/help/forms/assets/generative-ai-assistant.png)

De beschikbare Generative AI-mogelijkheden zijn:

* **AI Medewerker voor de Vragen van het Product**: Krijg onmiddellijke antwoorden op uw vorm-verwante vragen van AEM. De AI-assistent fungeert als uw eigen persoonlijke kennisbasis en biedt direct binnen het platform inzichtelijke begeleiding en aanbevelingen.

* **Adaptive Form Generation**: Effortlessly create full-fledged forms with generative AI prompts. Adobe&#39;s generative AI automatically generates user-friendly forms that reduce drop-offs and personalize the experience.

* **Panel Generation for Forms**: Generate form sections tailored to specific data collection needs. U kunt bijvoorbeeld secties genereren voor het verzamelen van betalingsgegevens, voorkeuren van klanten of reisgegevens.

* **Changing Form Layouts**: Experiment with different layouts and designs using generative AI prompts. Probeer verschillende indelingen, zoals de wizard of de tabsgewijze weergave, uit om te zien wat het beste bij uw formulier past. Use generative AI prompts to optimize your forms for mobile responsiveness and create visually engaging forms that users love.

* **vormt Voorlegt Actie**: De generatieve herinneringen van AI van het gebruik om een voorlegt actie voor uw vorm te vormen. Maak een keuze uit een bibliotheek met vooraf gebouwde verzendacties of aangepaste verzendacties die zijn gemaakt en geïmplementeerd door uw ontwikkelingsteam.

>[!IMPORTANT]
>
> Wil je deelnemen aan het programma voor vroege toegang voor Forms-innovatie? Verzend een e-mail van uw officieel adres naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) met de lijst van mogelijkheden die u in geinteresseerd bent.

## CIF-invoegtoepassing {#cloud-services-cif}

### Verbeteringen {#improvements-fixes-cif}

* Categoriebeperking aanpasbaar maken.

### Bugfixes {#bug-fixes-cif}

* Commerce-velden zijn niet correct geïntegreerd met de Assets Metadata Schema-editor.
* Probleem met multifield Carrouselproducten voor slepen en neerzetten.
* Probleem met multiveld van categorie Carrousel voor slepen en neerzetten.
* Als u eenmaal klikt, werkt dit niet voor de menu&#39;s in de pagina-informatie op de pagina met categorieën en producteditor.
* Het bestelnummer is niet zichtbaar op de pagina voor bevestiging van de bestelling.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Edge Side Includes (ESI) voor het laden van dynamische inhoud {#esi}

Adobe beheerde CDN steunt nu [ de Zijde van Edge omvat (ESI) ](/help/implementing/dispatcher/edge-side-includes.md), een prijsverhogingstaal voor de dynamische assemblage van de Webinhoud van het randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. Dit onderdeel wordt geleidelijk ingevoerd.

### Basisverificatie bij de CDN {#basicauth-cdn}

Bescherm bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarin een gebruikersnaam en wachtwoord zijn vereist. Deze eigenschap richt hoofdzakelijk lichte kwesties van het authentificatiegebruik, zoals bedrijfsbelanghebbenden die inhoud herzien, eerder dan het dienen als een uitvoerige oplossing voor de rechten van de eindgebruikertoegang. De lijst van gebruikersbenaming en wachtwoorden wordt beheerd door een configuratiedossier in Git dat via Pijpleiding Config, met een verwijzing naar geheim-type de milieuvariabelen van Cloud Manager wordt opgesteld. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### Server-kant omleidingen {#server-side-redirects}

Declareer [ browser richt ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors) in een Git van het configuratiedossier opnieuw die aan en geëvalueerd bij CDN worden opgesteld. Dit kan handig zijn voor scenario&#39;s zoals het verwijderen van pagina&#39;s, gewijzigde sitestructuur en SEO-optimalisatie.

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit een vernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe welcomes feedback, which you can email to **<aemcs-new-devconsole-ui-beta@adobe.com>**.

![OSGi Bundles Screen in AEM Developer Console](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### Business Users Can Declare Redirects Outside of Git (Early Adopter Program) {#apache-rewritemaps-early-adopter}

Net als in AEM 6.5 worden door Apache/dispatcher opnieuw toegewezen die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en worden deze kaarten geladen zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Deze benadering laat bedrijfsgebruikers redirects verklaren gebruikend een spreadsheet of een UI, zoals ACS Commons Redirect de Manager van de Kaart of een douanetoepassing. U kunt deelnemen aan het programma voor vroege adoptie door een e-mail te verzenden **<aemcs-cdn-config-adopter@adobe.com>** .

### Config Pipeline voor RDEs (Vroege Programma van de Aannemer) {#config-pipeline-rdes-early-adopter}

De [ Pijpleiding Config ](/help/operations/config-pipeline.md) wordt gebruikt om uw dossierconfiguraties, met inbegrip van CDN opties (de regels van de verkeersfilter, verzoek/reactietransformaties, etc.) op te stellen. U kunt deelnemen aan het programma voor vroege adoptie door **<aemcs-cdn-config-adopter@adobe.com>** te e-mailen om dezelfde configuraties te implementeren in RDE&#39;s (Rapid Development Environment), die een CLI gebruiken.

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
