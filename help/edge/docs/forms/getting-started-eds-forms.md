---
title: Aan de slag met Forms op AEM Edge Delivery Services
description: Leer hoe u hoogwaardige formulieren maakt en levert op Adobe Experience Manager Edge Delivery Services, met de nadruk op de Universal Editor-ontwerpaanpak.
feature: Edge Delivery Services
exl-id: ecea1e05-d36b-4d63-af9d-c69dafd2f94f
role: Admin, Architect, Developer
source-git-commit: ccfb85da187e828b5f7e8b1a8bae3f483209368d
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 0%

---


# Aan de slag met Forms op AEM Edge Delivery Services

<!--<span class="preview"> This is a pre-release feature available through our <a href="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=nl-NL#new-features">pre-release channel</a>. </span>-->

Met Adobe Experience Manager (AEM) Edge Delivery Services (EDS) kunt u vanaf de rand genieten van supersnelle, zeer schaalbare webbeleving. Deze gids verklaart **hoe te om vormen voor die ervaringen** te bouwen en te publiceren—met een duidelijke aanbevelingshiërarchie:

1. **Universele Redacteur (UE) - Beste keus voor de meeste teams**
2. **document-Gebaseerde Authoring (Docs/Sheets) - Uitstekend voor snelle, eenvoudige vormen**
3. **Document Authoring (DA) - Gebruik om formulieren in te sluiten in pagina&#39;s die met DA zijn geschreven**

Tegen het einde kunt u de juiste ontwerpmethode kiezen, de verzendopties begrijpen en de volgende stappen volgen in de richting van formulieren die klaar zijn voor productie.



## Een ontwerpmethode kiezen

| Team en vereisten | Aanbevolen methode | Waarom |
|--------------------|--------------------|-----|
| Marketers/Ontwerpers hebben visuele controle, voorwaardelijke logica of AEM-integratie nodig | **Universele Redacteur** | Slepen en neerzetten, geavanceerde regels, verzenden naar publicatie in FSS of AEM |
| Inhoudsauteurs die al werken in Word / Google Docs / Sheets; eenvoudige gegevensvastlegging naar spreadsheet/email | **op document-Gebaseerde Authoring** | Vertrouwde gereedschappen, snelste pad voor basisformulieren |
| De pagina&#39;s van de website die in **Document Authoring (DA)** worden gebouwd | **bedt** een UE of op Doc-Gebaseerde vorm in de pagina van DA in | DA bouwt zelf geen formulieren |


## Detail ontwerpmethoden

### Universele editor

De Universele Redacteur is een visueel, belemmering-en-dalingsauteursinstrument voor marketers en ontwerpers die snelheid met onderneming-rang macht combineert:

- WYSIWYG-bewerkingen in realtime en voorvertoningen van apparaten.
- Geavanceerde regels en validatie-UI—geen code vereist.
- Directe integratie met AEM-elementen, -workflows en -formuliergegevensmodel (FDM).
- Naadloze overdracht aan ontwikkelaars voor aangepaste componenten in vanilla JS/CSS.
- De flexibele voorleggingsdoelstellingen: begin eenvoudig met de **Dienst van de Verzending van Forms (FSS)** of schakelaar aan **AEM publiceer acties** aangezien uw behoeften groeien.

> **Aanbeveling**: Begin elk nieuw vormproject met Universele Redacteur tenzij uw team 100 % document-centric is en de vorm zeer fundamenteel is.


### Authoring op basis van documenten (documenten/bladen)

Authoring op basis van documenten is het meest geschikt voor het maken van eenvoudige, complexe formulieren met behulp van vertrouwde gereedschappen, zoals Microsoft Word, Google Docs of Google Sheets. Deze methode is ideaal voor inhoudsteams die een snelle en eenvoudige manier nodig hebben om formulieren te maken.

- Formuliervelden definiëren in een tabel (Docs) of als rijen (Sheets).
- Ondersteunt basisveldvalidatie en Google reCAPTCHA voor spambeveiliging.
- Formulierverzendingen worden uitsluitend via de Forms-verzendservice verzonden.
- Onmiddellijk publiceren-om het even welke veranderingen die in het brondocument worden aangebracht worden onmiddellijk weerspiegeld op de plaats zonder een plaatsingspijpleiding te vereisen.


### Forms insluiten in Document Authoring (DA)

Document Authoring (DA) is ontworpen voor het maken van gestructureerde pagina-inhoud en ondersteunt het maken van native formulieren niet. Ga als volgt te werk als u een formulier wilt toevoegen aan een pagina die met DA is geschreven:

1. Creeer de vorm gebruikend de **Universele Redacteur** (geadviseerd) of op document-Gebaseerde Authoring.
2. Publiceer het formulier om een unieke URL te genereren (bijvoorbeeld `/forms/contact-us` ).
3. In uw pagina van DA, neem een **in bed het blok van de Vorm** in en specificeer de gepubliceerde vorm URL.

<!-- 
## Feature Comparison

| Capability | Universal Editor | Document-Based | Document Authoring |
|------------|-----------------|----------------|--------------------|
| Visual drag-and-drop | ✅ | – | – |
| Advanced rules editor | ✅ | Limited | – |
| Attachments | ✅ | EA | – |
| reCAPTCHA Enterprise | ✅ | ✅ | Depends on embed |
| Submit to spreadsheet/email | ✅ (FSS) | ✅ (FSS) | Via embed |
| Submit to AEM workflows/FDM | ✅ | – | Via UE embed |
| Custom components (JS/CSS) | ✅ | ✅ | Via embed |
| Localization via Sites | ✅ | Manual | Via embed |

-->

## Volgende stappen

1. **Begin met Universele Redacteur:** zie de [ Universele Redacteur begonnen gids ](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md) beginnen creërende vormen te beginnen.
2. **vormVerzending:** selecteer en opstelling uw aangewezen voorleggingsmethode. Verwijs naar [ de Dienst van de Verzending van Forms ](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md) of AEM publiceer acties voor configuratieinstructies.
3. **pas Beste praktijken toe:** Overzicht [ beste praktijken van het vormontwerp ](/help/edge/docs/forms/universal-editor/best-practices-eds-forms.md) om toegankelijkheid en prestaties te verzekeren.
4. **Gebruik op document-Gebaseerde Authoring:** om vormen met Microsoft Excel of de Bladen van Google tot stand te brengen, volg het [ op document-Gebaseerde Authoring leerprogramma ](/help/edge/docs/forms/tutorial.md).
5. **bedt Forms in Document Authoring in:** als u pagina&#39;s in Document Authoring bouwt, raadpleeg het [ DA leerprogramma ](https://www.aem.live/developer/da-tutorial) voor instructies over het inbedden van gepubliceerde vormen.

> **u bent nu klaar om uw eerste krachtige vorm met AEM Edge Delivery Services tot stand te brengen.**