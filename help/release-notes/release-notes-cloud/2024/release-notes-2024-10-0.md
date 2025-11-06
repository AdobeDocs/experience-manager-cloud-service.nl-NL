---
title: Nota's van de versie voor 2024.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.10.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 7a63f04f-10f0-4879-bd06-4182bb288a9b
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.10.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.10.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [&#x200B; Update van het Product van de Prioriteit Adobe &#x200B;](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.10.0) is 31 oktober 2024. De volgende functieversie (2024.11.0) is gepland voor 21 november 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [&#x200B; hier &#x200B;](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van oktober 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.10.0:

>[!VIDEO](https://video.tv.adobe.com/v/3440501?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

**Modernized de Gebeurtenissen van de Pagina**

De volgende AEM Sites-paginagebeurtenissen zijn nu beschikbaar als extern verbruikbare gebeurtenissen die zijn gebaseerd op het AEM as a Cloud Service Event Platform. De gebeurtenissen kunnen via Adobe I/O worden verwerkt voor interactie met externe processen.

* Pagina gepubliceerd
* Pagina niet gepubliceerd
* Pagina verwijderd

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [&#x200B; produceert variaties &#x200B;](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud**

[&#x200B; AEM REST OpenAPI voor de Levering van het Fragment van de Inhoud &#x200B;](/help/headless/aem-content-fragment-delivery-with-openapi.md), is nu beschikbaar voor AEM as a Cloud Service.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Functie voor vroege toegang in dynamische media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. Deze bijschriften helpen te voldoen aan toegankelijkheidsvereisten en verbeteren de videobetrokkenheid van gebruikers die op tekst gebaseerde videoondersteuning gebruiken of verkiezen.

Om vroege toegang tot AI-Gegenereerde titelsteun op uw Dynamische rekening van Media te krijgen, [&#x200B; creeer en voorlegt een geval van de Steun van de Klant van Adobe &#x200B;](/help/assets/dynamic-media/video.md##enable-dash).

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**Geplande Rapporten**

De rapporten kunnen nu automatisch in de Mening van Assets op een terugkerend programma of op een toekomstige datum worden geproduceerd, die de inspanning vermindert om gegeven-gedreven inzichten te ontdekken.

![&#x200B; Geplande Rapporten- &#x200B;](/help/assets/assets/scheduled-reports-tab.png)

### Nieuwe functies in Content Hub {#content-hub-new-features}

**Digitaal beheer van Rechten voor vergunning gegeven activa**

Organisaties kunnen nu de naleving van de licentievoorwaarden verhogen en het risico minimaliseren dat ze middelen delen met licentievoorwaarden door DRM te gebruiken voor gelicentieerde middelen voor gebruikers van Content Hub, waardoor gebruikers de licentievoorwaarden moeten controleren en accepteren voordat ze gelicentieerde activa kunnen downloaden. Voor meer informatie, zie [&#x200B; Gelicentieerde activa op Content Hub &#x200B;](/help/assets/manage-licensed-assets-on-content-hub.md) beheren.

![&#x200B; download-veelvoudige-vergunning &#x200B;](/help/assets/assets/download-multiple-license.png)

**de meta-gegevensconfiguratie van de kaart van Activa**

Met Content Hub kunt u nu maximaal zes velden configureren voor de belangrijkste metagegevensvelden die u op de Asset Card moet weergeven. Voor meer informatie, zie de sectie van de Kaart van Activa in [&#x200B; vormen Content Hub &#x200B;](/help/assets/configure-content-hub-ui-options.md#asset-card).

![&#x200B; zeer belangrijke meta-gegevens op de Kaart van Activa &#x200B;](/help/assets/assets/asset-card-key-metadata.png)

**vorm het zicht en de download van verlopen activa**

Beheerders kunnen nu bepalen of verlopen elementen zichtbaar moeten zijn op Content Hub. Als de verlopen elementen zichtbaar worden gemaakt, kunnen ze ook definiëren of gebruikers ze kunnen downloaden. Voor meer informatie, zie de Verlopen sectie van Assets in [&#x200B; vormen Content Hub &#x200B;](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub).

![&#x200B; Verlopen activa op Content Hub &#x200B;](/help/assets/assets/expired-assets-content-hub.png)

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functie in AEM Forms {#forms-new-features}

* [&#x200B; verbeter de Ervaring van de Gebruiker met de Knopen van de Navigatie in Comité Lay-outs &#x200B;](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button): U kunt navigatieknopen aan uw paneellay-outs, zoals Horizontale Lusjes, Verticale Lusjes, Accordeons, of Tovenaar nu toevoegen. Met deze knoppen vergroot u de gebruikerservaring door de overgangen tussen deelvensters te vereenvoudigen en de focus op het geselecteerde deelvenster te richten.

<!--* **Specify Display Styles for Document of Record (DoR) Components**: In an XFA file, you can now specify the display styles for Document of Record components. These styles can later be applied to the corresponding components in Adaptive Forms Editor.-->

### Nieuwe functies voor pre-release in AEM Forms {#forms-new-prerelease-features}

* [&#x200B; auto-sparen een ontwerp voor de Componenten van de Kern baseerde Adaptieve Forms &#x200B;](/help/forms/save-core-component-based-form-as-draft.md): De gebruikers kunnen nu van een auto-sparen eigenschap profiteren die een gedeeltelijk voltooide vorm als ontwerp automatisch opslaat. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversietarieven voor organisaties verbeterd doordat het aantal gebruikers dat het formulier afsluit, wordt verminderd, omdat gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.

* [&#x200B; het werkingsgebied van het Ondertekenen van Adobe van de Update gemakkelijk &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms): U kunt het werkingsgebied van een configuratie van het Ondertekenen van Adobe direct van de pagina van de Configuraties van de Wolk van AEM wijzigen, makend het sneller en gemakkelijker om bestaande configuraties bij te werken.

* [&#x200B; Asynchrone functiesteun voor Adaptieve Forms &#x200B;](/help/forms/using-async-funct-in-rule-editor.md): Wanneer uw Aanpassings Vorm asynchrone verrichtingen, zoals het wachten op externe processen of gegevensherwinning vereist, kunt u deze verrichtingen met douanefuncties uitvoeren en hen vormen in de Redacteur van de Regel.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [.](/help/forms/early-access-ea-features.md)

#### AEM Forms AI Assistant

[&#x200B; Generatieve AI voor Aanpassings Forms &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/forms-overview/early-access-ea-features#aem-forms-ai-assistant-gen-ai) brengt een geheel nieuw niveau van macht en gemak aan uw processen van de vormontwikkeling. Hierdoor kunt u sneller dan ooit betere formulieren maken.

![&#x200B; Generatieve AI Medewerker, Aangepaste Forms &#x200B;](/help/forms/assets/generative-ai-assistant.png)

De beschikbare Generative AI-mogelijkheden zijn:

* **AI Medewerker voor de Vragen van het Product**: Krijg onmiddellijke antwoorden op uw vorm-verwante vragen van AEM. De AI-assistent fungeert als uw eigen persoonlijke kennisbasis en biedt direct binnen het platform inzichtelijke begeleiding en aanbevelingen.

* **Aangepaste Generatie van de Vorm**: Creëer gemakkelijk volledige vormen met generatieve herinneringen AI. Adobe generatieve AI genereert automatisch gebruikersvriendelijke formulieren die drop-outs verkleinen en de ervaring aanpassen.

* **de Generatie van het Comité voor Forms**: produceer vormsecties die aan specifieke behoeften van de gegevensinzameling worden aangepast. U kunt bijvoorbeeld secties genereren voor het verzamelen van betalingsgegevens, voorkeuren van klanten of reisgegevens.

* **Veranderend de Lay-outs van de Vorm**: Experimenteer met verschillende lay-outs en ontwerpen gebruikend generatieve herinneringen AI. Probeer verschillende indelingen, zoals de wizard of de tabsgewijze weergave, uit om te zien wat het beste bij uw formulier past. Gebruik generatieve AI-aanwijzingen om uw formulieren te optimaliseren voor een mobiel reactievermogen en visueel aantrekkelijke formulieren te maken waar gebruikers van houden.

* **vormt Voorlegt Actie**: De generatieve herinneringen van AI van het gebruik om een voorlegt actie voor uw vorm te vormen. Maak een keuze uit een bibliotheek met vooraf gebouwde verzendacties of aangepaste verzendacties die zijn gemaakt en geïmplementeerd door uw ontwikkelingsteam.

>[!IMPORTANT]
>
> Wil je deelnemen aan het programma voor vroege toegang voor Forms-innovatie? Verzend een e-mail van uw officieel adres naar [&#x200B; aem-forms-ea@adobe.com &#x200B;](mailto:aem-forms-ea@adobe.com) met de lijst van mogelijkheden die u in geinteresseerd bent.

## CIF-invoegtoepassing {#cloud-services-cif}

### Bugfixes {#bug-fixes-cif}

* Correctie van UI-tests voor correct werken met Core CIF-componenten.
* Correctie van het probleem waarbij de categorie-URL-indeling niet werkte zoals verwacht in de cloud-instantie.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Configuratie om formulierverzendingen te beheren {#configuration-submissions}

AEM heeft een nieuwe configuratie geïntroduceerd: `com.adobe.granite.ui.components.FormRestrict` om formulierverzendingen voor Coral of Foundation op specifieke locaties te beheren. Deze configuratie bestaat uit twee velden:

1. **voegt Toegestane Wegen** toe: Specificeert de wegen waar de vormacties worden toegelaten.
1. **Beperk Gedrag**: Bepaalt het gedrag voor beperkte wegen (wegen niet inbegrepen in de lijst van gewenste personen). U kunt kiezen uit twee opties:
   * **Popup** (gebrek): Toont een popup bericht.
   * **verhindert**:Blocks vormvoorlegging.

>[!NOTE]
>
>Deze configuratie wordt niet ondersteund voor alle koraal- of stichtingsformulieren onder `/apps` , `/libs` , `/mnt/overlay` en `/mnt/override` .

### Self-Serve Log Forwarding met de Geavanceerde Optie van het Voorzien van een netwerk {#log-forwarding}

Hoewel AEM (inclusief Apache/Dispatcher)- en CDN-logbestanden vanuit Cloud Manager kunnen worden gedownload, vinden veel organisaties het nuttig die logbestanden te streamen naar een voorkeurslogbestemming. AEM steunt nu [&#x200B; logboek het door:sturen &#x200B;](/help/implementing/developing/introduction/log-forwarding.md) aan de Opslag van Azure Blob, Datadog, HTTPS, Elasticsearch (en OpenSearch), en Splunk. AEM-logboeken kunnen optioneel worden doorgestuurd via geavanceerde netwerkconfiguraties, zoals het gebruik van een toegewezen IP-adres.

Deze eigenschap wordt gevormd door gebruikers op een zelfbediende manier, en gebruikend de [&#x200B; Pijpleiding Config &#x200B;](/help/operations/config-pipeline.md) opgesteld.

### URL-omleidingen zonder pijplijn voor zakelijke gebruikers {#pipeline-free-redirects}

Omleidingen aan de browserzijde zijn handig wanneer een webpagina is omlaag of verplaatst of wanneer er andere scenario&#39;s zijn toegepast. Met [&#x200B; lijn-vrije URL richt &#x200B;](/help/implementing/dispatcher/pipeline-free-url-redirects.md) opnieuw, kunt u een Apache plaatsen herschrijft kaartdossier in AEM publiceren plaats, waar het automatisch wordt geladen — geen behoefte om het dossier aan broncontrole vast te leggen of een pijpleiding van Cloud Manager in werking te stellen.

De opties voor het publiceren van het herschrijven dossier omvatten het uploaden van het als activa, het gebruiken van de Bevelen ACS herschrijft de Manager van de Kaart, of het in wisselwerking staan met een douanegebruikersinterface.

### Config Pipeline voor RDEs {#config-pipeline-rdes}

De milieu&#39;s van de Snelle Ontwikkeling zijn een krachtig hulpmiddel om code en configuratie in een milieu van de Wolk snel op te stellen en te testen. RDEs steunt nu [&#x200B; het synchroniseren van configuratie YAML-dossiers &#x200B;](/help/implementing/developing/introduction/rapid-development-environments.md#deploy-config-pipeline), met inbegrip van CDN montages zoals de regels van de verkeersfilter en verzoek/reactietransformaties, evenals logboek het door:sturen en andere configuratieopties. [&#x200B; zie de volledige lijst &#x200B;](/help/operations/config-pipeline.md) van gesteunde configuratieopties voor meer details.

### Nieuwe productprofielen {#new-product-profiles}

Wanneer een nieuwe AEM-omgeving wordt gemaakt, worden productprofielen automatisch weergegeven in de Adobe Admin Console, zodat beheerders toegang kunnen toewijzen aan gelicentieerde oplossingen en functies.

Nieuwe omgevingen bevatten nu een bijgewerkte set productprofielen, waardoor deze compatibel zijn met toekomstige functies, waaronder het genereren van API-referenties in de Adobe Developer Console. Bestaande omgevingen kunnen hun productprofielen in een toekomstige release bijwerken. [&#x200B; leer meer &#x200B;](/help/onboarding/aem-cs-team-product-profiles.md).

### New AEM Developer Console (Public Beta) {#aem-developer-console-beta}

Probeer uit een vernieuwde [&#x200B; AEM Developer Console &#x200B;](/help/implementing/developing/introduction/aem-developer-console.md), die een meer interactieve ervaring voor het zuiveren van code in de milieu&#39;s van de Wolk aanbiedt.

Iedereen kan tot de openbare bèta toegang hebben door de *Nieuwe Beschikbare Console* knoop van de Console in huidige AEM Developer Console te klikken. Adobe verwelkomt feedback, die u via e-mail kunt verzenden naar **<aemcs-new-devconsole-ui-beta@adobe.com>** .

![&#x200B; het Scherm van Bundles OSGi in AEM Developer Console &#x200B;](/help/implementing/developing/introduction/assets/osgi-bundles.png)

## [!DNL Experience Manager] Hulplijnen {#guides}

U kunt een volledige lijst van nieuwe en verbeterde eigenschappen van de recentste versie van Adobe Experience Manager Guides [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap) vinden.

## Cloud Manager {#cloud-manager}

U kunt een volledige lijst van de maandelijkse versies van Cloud Manager [&#x200B; hier &#x200B;](/help/implementing/cloud-manager/release-notes/current.md) vinden.

## Migratiehulpmiddelen {#migration-tools}

U kunt een volledige lijst van de versies van Hulpmiddelen van de Migratie [&#x200B; hier &#x200B;](/help/journey-migration/release-notes/release-notes-migration-tools-current.md) vinden.

## Universele editor {#universal-editor}

U kunt een volledige lijst van Universele versies van de Redacteur [&#x200B; hier &#x200B;](/help/release-notes/universal-editor/current.md) vinden.

## Variaties genereren {#generate-variations}

U kunt een volledige lijst van Generate de versies van Variaties [&#x200B; hier &#x200B;](/help/generative-ai/release-notes-generate-variations.md) vinden.

## Opmerkingen bij de release van Experience Cloud {#experience-cloud}

U kunt informatie over versies van andere toepassingen van Experience Cloud [&#x200B; hier &#x200B;](https://experienceleague.adobe.com/en/docs/release-notes/experience-cloud/current) vinden.
