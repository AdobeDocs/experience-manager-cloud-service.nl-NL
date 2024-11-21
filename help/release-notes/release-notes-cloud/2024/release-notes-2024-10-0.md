---
title: Nota's van de versie voor 2024.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
source-git-commit: 941d544a983ac4ad9b82c82edf3b68c964267e9c
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.10.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij de [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates over de versienota&#39;s van de Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit van de Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.10.0) is 31 oktober 2024. De volgende functieversie (2024.11.0) is gepland voor 21 november 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

<!-- ## Release Video {#release-video}

Have a look at the October 2024 Release Overview video for a summary of the features added in the 2024.10.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

**Modernized de Gebeurtenissen van de Pagina**

De volgende AEM Sites-paginagebeurtenissen zijn nu beschikbaar als extern verbruikbare gebeurtenissen die zijn gebaseerd op het AEM as a Cloud Service Event Platform. De gebeurtenissen kunnen via Adobe I/O worden verwerkt om met externe processen in wisselwerking te staan.
* Pagina gepubliceerd
* Pagina niet gepubliceerd
* Pagina verwijderd

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door AEM nieuwe eigenschap, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met het accountteam van uw Adobe voor advies in het programma.

**AEM REST OpenAPI voor levering van inhoudsfragmenten**

[ AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud ](/help/headless/aem-rest-openapi-content-fragment-delivery.md), is nu beschikbaar voor AEM as a Cloud Service.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functie voor vroege toegang in Dynamic Media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. Deze bijschriften helpen te voldoen aan toegankelijkheidsvereisten en verbeteren de videobetrokkenheid van gebruikers die op tekst gebaseerde videoondersteuning gebruiken of verkiezen.

Om vroege toegang tot AI-Gegenereerde titelsteun op uw rekening van Dynamic Media te krijgen, [ creeer en voorlegt een geval van de Steun van de Klant van de Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**Geplande Rapporten**

De rapporten kunnen nu automatisch in de Mening van Assets op een terugkerend programma of op een toekomstige datum worden geproduceerd, die de inspanning vermindert om gegeven-gedreven inzichten te ontdekken.

![ Geplande Rapporten- ](/help/assets/assets/scheduled-reports-tab.png)

### Nieuwe functies in Content Hub {#content-hub-new-features}

**Digitaal beheer van Rechten voor vergunning gegeven activa**

Organisaties kunnen nu de naleving van de licentievoorwaarden verhogen en het risico minimaliseren dat ze middelen delen met licentievoorwaarden door DRM te gebruiken voor gelicentieerde middelen voor gebruikers van Content Hub, waardoor gebruikers de licentievoorwaarden moeten controleren en accepteren voordat ze gelicentieerde activa kunnen downloaden. Voor meer informatie, zie [ Gelicentieerde activa op Content Hub ](/help/assets/manage-licensed-assets-on-content-hub.md) beheren.

![ download-veelvoudige-vergunning ](/help/assets/assets/download-multiple-license.png)

**de meta-gegevensconfiguratie van de kaart van Activa**

Met Content Hub kunt u nu maximaal zes velden configureren voor de belangrijkste metagegevensvelden die u op de Asset Card moet weergeven. Voor meer informatie, zie de sectie van de Kaart van Activa in [ vormen Content Hub ](/help/assets/configure-content-hub-ui-options.md#asset-card).

![ zeer belangrijke meta-gegevens op de Kaart van Activa ](/help/assets/assets/asset-card-key-metadata.png)

**vorm het zicht en de download van verlopen activa**

Beheerders kunnen nu bepalen of verlopen elementen zichtbaar moeten zijn op Content Hub. Als de verlopen elementen zichtbaar worden gemaakt, kunnen ze ook definiëren of gebruikers ze kunnen downloaden. Voor meer informatie, zie de Verlopen sectie van Assets in [ vormen Content Hub ](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub).

![ Verlopen activa op Content Hub ](/help/assets/assets/expired-assets-content-hub.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functie in AEM Forms {#forms-new-features}

* [ verbeter de Ervaring van de Gebruiker met de Knopen van de Navigatie in Comité Lay-outs ](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button): U kunt navigatieknopen aan uw paneellay-outs, zoals Horizontale Lusjes, Verticale Lusjes, Accordeons, of Tovenaar nu toevoegen. Met deze knoppen vergroot u de gebruikerservaring door de overgangen tussen deelvensters te vereenvoudigen en de focus op het geselecteerde deelvenster te richten.

<!--* **Specify Display Styles for Document of Record (DoR) Components**: In an XFA file, you can now specify the display styles for Document of Record components. These styles can later be applied to the corresponding components in Adaptive Forms Editor.-->

### Nieuwe functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

* [ auto-sparen een ontwerp voor de Componenten van de Kern baseerde Adaptieve Forms ](/help/forms/save-core-component-based-form-as-draft.md): De gebruikers kunnen nu van een auto-sparen eigenschap profiteren die een gedeeltelijk voltooide vorm als ontwerp automatisch opslaat. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.

* [ het werkingsgebied van Adobe Sign van de Update gemakkelijk ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms): U kunt het werkingsgebied van een configuratie van Adobe Sign direct van de pagina van de Configuraties van de AEMWolk wijzigen, makend het sneller en gemakkelijker om bestaande configuraties bij te werken.

* [ Asynchrone functiesteun voor Adaptieve Forms ](/help/forms/using-async-funct-in-rule-editor.md): Wanneer uw Aanpassings Vorm asynchrone verrichtingen, zoals het wachten op externe processen of gegevensherwinning vereist, kunt u deze verrichtingen met douanefuncties uitvoeren en hen vormen in de Redacteur van de Regel.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie {de documentatie van het Programma van de Vroege Toegang van AEM Forms ](/help/forms/early-access-ea-features.md).[

#### AEM Forms AI Assistant

[ Generatieve AI voor Aanpassings Forms ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features#aem-forms-ai-assistant-gen-ai) brengt een geheel nieuw niveau van macht en gemak aan uw processen van de vormontwikkeling. Hierdoor kunt u sneller dan ooit betere formulieren maken.

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

### Bugfixes {#bug-fixes-cif}

* Vaste UI-tests om correct te werken met Core CIF-componenten.
* Correctie van het probleem waarbij de categorie-URL-indeling niet werkte zoals verwacht in de cloud-instantie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Configuratie om formulierverzendingen te beheren {#configuration-submissions}

AEM heeft een nieuwe configuratie geïntroduceerd: `com.adobe.granite.ui.components.FormRestrict` om formulierverzendingen voor Coral of Foundation op specifieke locaties te beheren. Deze configuratie bestaat uit twee velden:

1. **voegt Toegestane Wegen** toe: Specificeert de wegen waar de vormacties worden toegelaten.
1. **Beperk Gedrag**: Bepaalt het gedrag voor beperkte wegen (wegen niet inbegrepen in de lijst van gewenste personen). U kunt kiezen uit twee opties:
   * **Popup** (gebrek): Toont een popup bericht.
   * **verhinderen**:Blokken van voorlegging.

>[!NOTE]
>
>Deze configuratie wordt niet ondersteund voor alle koraal- of stichtingsformulieren onder `/apps` , `/libs` , `/mnt/overlay` en `/mnt/override` .

### Self-Serve Log Forwarding met de Geavanceerde Optie van het Voorzien van een netwerk {#log-forwarding}

Terwijl AEM (met inbegrip van Apache/Dispatcher) en CDN logboeken van Cloud Manager kunnen worden gedownload, vinden vele organisaties het nuttig om die logboeken aan een aangewezen registrerenbestemming te stromen. AEM steunt nu [ logboek het door:sturen ](/help/implementing/developing/introduction/log-forwarding.md) aan de Opslag van Azure Blob, Datadog, HTTPS, Elasticsearch (en OpenSearch), en Splunk. AEM logboeken kunnen naar keuze over geavanceerde voorzien van een netwerkconfiguraties, zoals het gebruiken van een specifiek IP adres door:sturen.

Deze eigenschap wordt gevormd door gebruikers op een zelfbediende manier, en gebruikend de [ Pijpleiding Config ](/help/operations/config-pipeline.md) opgesteld.

### URL-omleidingen zonder pijplijn voor zakelijke gebruikers {#pipeline-free-redirects}

Omleidingen aan de browserzijde zijn handig wanneer een webpagina is omlaag of verplaatst of wanneer er andere scenario&#39;s zijn toegepast. Met [ lijn-vrije URL richt ](/help/implementing/dispatcher/pipeline-free-url-redirects.md) opnieuw, kunt u een Apache kaartdossier in AEM plaatsen publiceert plaats, waar het automatisch wordt geladen — geen behoefte om het dossier aan broncontrole vast te leggen of een pijpleiding van Cloud Manager in werking te stellen.

De opties voor het publiceren van het herschrijven dossier omvatten het uploaden van het als activa, het gebruiken van de Bevelen ACS herschrijft de Manager van de Kaart, of het in wisselwerking staan met een douanegebruikersinterface.

### Config Pipeline voor RDEs {#config-pipeline-rdes}

De milieu&#39;s van de Snelle Ontwikkeling zijn een krachtig hulpmiddel om code en configuratie in een milieu van de Wolk snel op te stellen en te testen. RDEs steunt nu [ het synchroniseren van configuratie YAML-dossiers ](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline), met inbegrip van CDN montages zoals de regels van de verkeersfilter en verzoek/reactietransformaties, evenals logboek het door:sturen en andere configuratieopties. [ zie de volledige lijst ](/help/operations/config-pipeline.md) van gesteunde configuratieopties voor meer details.

### Nieuwe productprofielen {#new-product-profiles}

Wanneer een nieuwe AEM wordt gecreeerd, verschijnen de Profielen van het Product automatisch in Adobe Admin Console, toelatend beheerders om toegang tot vergunning gegeven oplossingen en eigenschappen toe te wijzen.

Nieuwe omgevingen bevatten nu een bijgewerkte set productprofielen, waardoor deze compatibel zijn met toekomstige functies, waaronder het genereren van API-referenties in de Adobe Developer Console. Bestaande omgevingen kunnen hun productprofielen in een toekomstige release bijwerken. [ leer meer ](/help/onboarding/aem-cs-team-product-profiles.md).

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit gevernieuwde [ AEM Developer Console ](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe is verheugd over feedback, die u via e-mail kunt verzenden naar **<aemcs-new-devconsole-ui-beta@adobe.com>** .

![ het Scherm van Bundles OSGi in AEM Developer Console ](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [ hier ](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-0-release/whats-new-2024-10-0) vinden.

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
