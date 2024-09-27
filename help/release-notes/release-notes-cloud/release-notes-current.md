---
title: De huidige Nota's van de Versie voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Huidige versienota's voor  [!DNL Adobe Experience Manager]  as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 2d5fa0b15456ad9838fa236a2b5c79d41a9af7fe
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates over de versienota&#39;s van de Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit van de Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.9.0) is 26 september 2024. De volgende release met functies (2024.10.0) is gepland voor 31 oktober 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!--  ## Release Video {#release-video}

Have a look at the September 2024 Release Overview video for a summary of the features added in the 2024.9.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

#### Vertaalbeheer {#translation-management}

AEM vertaalworkflows en API-acties activeren nu gebeurtenissen om inzicht te krijgen in wijzigingen in de status van vertaaltaken. Gebruikers kunnen zich op deze gebeurtenissen abonneren via de Adobe Developer Console. Zie [ hier ](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/translation/) voor meer informatie over AEM Vertaalbeheer API.

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door AEM nieuwe eigenschap, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.


## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functie voor vroege toegang in Dynamic Media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. Deze bijschriften helpen te voldoen aan toegankelijkheidsvereisten en verbeteren de videobetrokkenheid van gebruikers die op tekst gebaseerde videoondersteuning gebruiken of verkiezen.

Om vroege toegang tot AI-Gegenereerde titelsteun op uw rekening van Dynamic Media te krijgen, [ creeer en voorlegt een geval van de Steun van de Klant van de Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nieuwe functies in Asset Selector {#asset-selector-new-features}

Asset Selector biedt nu ondersteuning voor het bladeren in verzamelingen naar het gewenste element.
![ de selecteursinzamelingen van Activa ](/help/assets/assets/collections-rail-modal-view.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

#### Een concept voor adaptieve Forms op basis van Core Components automatisch opslaan

Gebruikers kunnen nu profiteren van een functie voor automatisch opslaan, waarmee een gedeeltelijk ingevuld formulier automatisch als concept wordt opgeslagen. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.


### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms ](/help/forms/early-access-ea-features.md).[

#### AEM Forms AI Assistant

Generative AI voor Adaptive Forms biedt een heel nieuw niveau van kracht en maakt het ontwikkelen van formulieren eenvoudiger. Hierdoor kunt u sneller dan ooit betere formulieren maken.

![ Generatieve AI Medewerker, Aangepaste Forms ](/help/forms/assets/generative-ai-assistant.png)

De beschikbare Generative AI-mogelijkheden zijn:

* **AI Medewerker voor de Vragen van het Product**: Krijg onmiddellijke antwoorden op uw AEM vorm-verwante vragen. De AI-assistent fungeert als uw eigen persoonlijke kennisbasis en biedt direct binnen het platform inzichtelijke begeleiding en aanbevelingen.

* **Aangepaste Generatie van de Vorm**: Creëer gemakkelijk volledige vormen met generatieve herinneringen AI. De generatieve AI van de Adobe produceert automatisch gebruikersvriendelijke vormen die drop-outs verminderen en de ervaring personaliseren.

* **de Generatie van het Comité voor Forms**: produceer vormsecties die aan specifieke behoeften van de gegevensinzameling worden aangepast. U kunt bijvoorbeeld secties genereren voor het verzamelen van betalingsgegevens, voorkeuren van klanten of reisgegevens.

* **Veranderend de Lay-outs van de Vorm**: Experimenteer met verschillende lay-outs en ontwerpen gebruikend generatieve herinneringen AI. Probeer verschillende indelingen, zoals de wizard of de tabsgewijze weergave, uit om te zien wat het beste bij uw formulier past. Gebruik generatieve AI-aanwijzingen om uw formulieren te optimaliseren voor een mobiel reactievermogen en visueel aantrekkelijke formulieren te maken waar gebruikers van houden.

* **vormt Voorlegt Actie**: De generatieve herinneringen van AI van het gebruik om een voorlegt actie voor uw vorm te vormen. Maak een keuze uit een bibliotheek met vooraf gebouwde verzendacties of aangepaste verzendacties die zijn gemaakt en geïmplementeerd door uw ontwikkelingsteam.

>[!IMPORTANT]
>
> Wil je deelnemen aan het programma voor vroege toegang voor Forms-innovatie? Verzend een e-mail van uw officieel adres naar [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) met de lijst van mogelijkheden die u in geinteresseerd bent.

## CIF invoegtoepassing {#cloud-services-cif}

### Verbeteringen {#improvements-fixes-cif}

* Categoriebeperking aanpasbaar maken.

### Bugfixes {#bug-fixes-cif}

* Commerce-velden zijn niet correct geïntegreerd met de Assets Metadata Schema-editor.
* Probleem met multifield Carrouselproducten voor slepen en neerzetten.
* Probleem met multiveld van categorie Carrousel voor slepen en neerzetten.
* Klik niet op de menu&#39;s in de pagina Pagina-informatie op de pagina Categorie en producteditor.
* Volgnummer is niet zichtbaar op de pagina voor bevestiging van bestelling.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Edge Side Includes (ESI) voor het laden van dynamische inhoud {#esi}

De Adobe beheerde CDN steunt nu [ Kant van Edge omvat (ESI) ](/help/implementing/dispatcher/edge-side-includes.md), een prijsverhogingstaal voor de dynamische assemblage van de Webinhoud van het randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van de HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl vaker het halen van van oorsprong die kleinere secties die hogere tijdigheidsupdates (lagere TTLs) vereisen. Dit onderdeel wordt geleidelijk ingevoerd.

### Basisverificatie bij de CDN {#basicauth-cdn}

Protect bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarvoor een gebruikersnaam en wachtwoord vereist zijn. Deze eigenschap richt hoofdzakelijk lichte kwesties van het authentificatiegebruik, zoals bedrijfsbelanghebbenden die inhoud herzien, eerder dan het dienen als een uitvoerige oplossing voor de rechten van de eindgebruikertoegang. De lijst van gebruikersbenaming en wachtwoorden wordt beheerd door een configuratiedossier in git dat via Pijpleiding Config, met een verwijzing naar geheim-type de milieuvariabelen van Cloud Manager wordt opgesteld. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

### Omleiding op de client {#client-side-redirects}

Verklaar [ browser richt ](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) in een gebied van het configuratiedossier opnieuw dat aan wordt opgesteld en bij CDN geëvalueerd. Dit kan nuttig zijn voor scenario&#39;s zoals het schrappen van pagtes, veranderde plaatsstructuur, en optimalisering SEO.

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit gevernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe is verheugd over feedback, die u via e-mail kunt verzenden naar **<aemcs-new-devconsole-ui-beta@adobe.com>** .

![ het Scherm van Bundles OSGi in AEM Developer Console ](/help/implementing/developing/introduction/assets/osgi-bundles.png)

### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (vroege adopter-programma) {#apache-rewritemaps-early-adopter}

Net als bij AEM 6.5 worden door Apache/dispatcher ingegrepen opnieuw kaarten geschreven die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en worden deze geladen zonder dat een pijpleiding op de weblaag hoeft te worden uitgevoerd. Deze benadering laat bedrijfsgebruikers redirects verklaren gebruikend een spreadsheet of een UI, zoals ACS Commons Redirect de Manager van de Kaart of een douanetoepassing. U kunt deelnemen aan het programma voor vroege adoptie door een e-mail te verzenden **<aemcs-cdn-config-adopter@adobe.com>** .

### Config Pipeline voor RDEs (Vroege Programma van de Aannemer) {#config-pipeline-rdes-early-adopter}

De [ Pijpleiding Config ](/help/operations/config-pipeline.md) wordt gebruikt om uw dossierconfiguraties, met inbegrip van CDN opties (de regels van de verkeersfilter, verzoek/reactietransformaties, enz.) op te stellen. U kunt deelnemen aan het programma voor vroege adoptie door **<aemcs-cdn-config-adopter@adobe.com>** te e-mailen om dezelfde configuraties te implementeren in RDE&#39;s (Rapid Development Environment), die een CLI gebruiken.

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [ hier ](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [ hier ](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [ hier ](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [ hier ](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van het Experience Cloud [ hier ](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
