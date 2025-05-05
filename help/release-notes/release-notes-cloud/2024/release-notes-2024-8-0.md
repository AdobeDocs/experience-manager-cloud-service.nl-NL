---
title: Nota's van de versie voor 2024.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.8.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: dd1d4b8f-8331-4e97-a754-37e720974db6
source-git-commit: 4b8086920bc3e3b9c5ed2a74934645fbc69acf71
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# 2024.8.0 Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

The following section outlines the feature release notes for the 2024.8.0 version of [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.8.0) is 29 augustus 2024. De volgende release met functies (2024.9.0) is gepland voor 26 september 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van augustus 2024 voor een overzicht van de functies die in de release van 2024.8.0 zijn toegevoegd:

>[!VIDEO](https://video.tv.adobe.com/v/3433381?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

**Authoring van AEM voor Edge Delivery Services**

De bestaande functionaliteit van de Overerving van Plaatsen [&#128279;](/help/sites-cloud/authoring/universal-editor/inheritance.md) wordt nu gesteund met inbegrip van:

* [AEM Launches](/help/sites-cloud/authoring/launches/overview.md)
* [ MSM ](/help/sites-cloud/administering/msm/overview.md) op het paginaniveau

Bovendien worden de volgende functies voor paginabeheer nu ondersteund:

* [ de Markeringen van AEM ](/help/sites-cloud/authoring/sites-console/tags.md) kunnen als a [ taxonomie ](/help/edge/wysiwyg-authoring/taxonomy.md) aan Edge Delivery Services worden uitgevoerd.
* [ Malplaatjes ](/help/sites-cloud/authoring/universal-editor/templates.md) voor Edge Delivery Services komen binnenkort!

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.


## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**bijgewerkte Generatie van het Beeld van Adobe Firefly**

Assets as a Cloud Service gebruikt nu de nieuwste widget van Firefly waarmee u afbeeldingen in verschillende stijlen kunt genereren met Adobe Firefly. Door zijn stijl, samenstelling, dimensies, en meer te bepalen, gebruikend de ingebouwde redacteur van Firefly, kunt u de activa snel tot stand brengen en opslaan u direct binnen de bewaarplaats van AEM Assets voor onmiddellijk gebruik nodig hebt.

![ Adobe Firefly beeldgeneratie ](/help/assets/assets/bugatti-type-57.png)

**PSB- dossiersteun**

Assets as a Cloud Service ondersteunt nu grote documenten (PSB-bestanden) van Photoshop naast de bestaande PSD-bestandsondersteuning.

### Nieuwe verbeteringen in Content Hub {#content-hub-new-enhancements}

* Betere verwerking van lange bestandsnamen, eenvoudige uitbreiding van de volledige naam via knopinfo.
* Verbeterde miniaturen voor een betere verhouding tussen de inhoud en een groter inhoudsgebied.
* Aangepaste miniatuurervaring vanuit AEM ondersteund met inhoudshub.
* Verbeteringen in het zoeken naar kleuren.
* Improvements in configurations save experience.
* Improved info page of collections to reflect creator name.


## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### New Pre-release features in AEM Forms {#forms-new-prerelease-features}

#### Auto-save a draft for Core Components based Adaptive Forms

Gebruikers kunnen nu profiteren van een functie voor automatisch opslaan, waarmee een gedeeltelijk ingevuld formulier automatisch als concept wordt opgeslagen. Ze kunnen later terugkeren om de vulling op hetzelfde of een ander apparaat te voltooien. Met deze functie worden de conversiesnelheden voor organisaties verhoogd door het aantal gebruikers dat het formulier verlaat te verminderen, aangezien gebruikers niet vanaf het begin hoeven te beginnen met het invullen van het formulier.


### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties en om de ontwikkeling ervan vorm te geven.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### AEM Forms AI Assistant

Generative AI voor Adaptive Forms biedt een heel nieuw niveau van kracht en maakt het ontwikkelen van formulieren eenvoudiger. Hierdoor kunt u sneller dan ooit betere formulieren maken.

![ Generatieve AI Medewerker, Aangepaste Forms ](/help/forms/assets/generative-ai-assistant.png)

De beschikbare Generative AI-mogelijkheden zijn:

* **AI Medewerker voor de Vragen van het Product**: Krijg onmiddellijke antwoorden op uw vorm-verwante vragen van AEM. De AI-assistent fungeert als uw eigen persoonlijke kennisbasis en biedt direct binnen het platform inzichtelijke begeleiding en aanbevelingen.

* **Aangepaste Generatie van de Vorm**: Creëer gemakkelijk volledige vormen met Generatieve Herinneringen AI. Onze generatieve AI genereert automatisch gebruikersvriendelijke formulieren die keuzemogelijkheden verkleinen en de ervaring aanpassen.

* **Panel Generation for Forms**: Generate form sections tailored to specific data collection needs. U kunt bijvoorbeeld secties genereren voor het verzamelen van betalingsgegevens, voorkeuren van klanten of reisgegevens.

* **Veranderend de Lay-outs van de Vorm**: Experimenteer met verschillende lay-outs en ontwerpen gebruikend Generatieve Herinneringen AI. Probeer verschillende indelingen, zoals de wizard of de tabsgewijze weergave, uit om te zien wat het beste bij uw formulier past. Gebruik Generative AI-herinneringen om uw formulieren te optimaliseren voor een mobiel reactievermogen en visueel aantrekkelijke formulieren te maken waar gebruikers van houden.

* **vormt Verzenden Actie**: De Generatieve herinneringen van AI van het gebruik om een voorleggingsactie voor uw vorm moeiteloos te vormen. Maak een keuze uit een bibliotheek met vooraf gebouwde verzendacties of uit een lijst met aangepaste verzendacties die zijn gemaakt en geïmplementeerd door uw eigen ontwikkelingsteam.

>[!IMPORTANT]
>
> If you are interested in joining the Early Access Program for any innovation, simply send an email from your official address to [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) with the list of capabilities you are interested in.


## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Inhoudsgerelateerde programma&#39;s voor vroege adoptie {#foundation-early-adopter}

E-mail **<aemcs-cdn-config-adopter@adobe.com>** waarin wordt aangegeven in welke van de onderstaande programma&#39;s voor vroege adoptie u geïnteresseerd bent.

#### Basisverificatie bij de CDN (programma voor vroege adopters) {#basicauth-cdn}

Bescherm bepaalde inhoudsbronnen door een standaarddialoogvenster weer te geven waarin een gebruikersnaam en wachtwoord zijn vereist. Deze eigenschap richt hoofdzakelijk lichte kwesties van het authentificatiegebruik, zoals bedrijfsbelanghebbenden die inhoud herzien, eerder dan het dienen als een uitvoerige oplossing voor de rechten van de eindgebruikertoegang. De lijst van gebruikersbenaming en wachtwoorden in beheerd door een configuratiedossier in git dat via de Pijpleiding van de Configuratie, met een verwijzing naar geheim-type de milieuvariabelen van Cloud Manager wordt opgesteld. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Server-Side Redirects (Early-adopter-programma) {#server-side-redirects-early-adopter}

Vorm 301/302 server-zij richt in broncontrole, en stel aan CDN op. [ leer meer ](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Merk op dat er verscheidene andere eigenschappen reeds beschikbaar met betrekking tot [ CDN configuratie ](/help/implementing/dispatcher/cdn-configuring-traffic.md) zijn, met inbegrip van verzoek en reactietransformaties, en verpletterend verkeer aan off-AEM plaatsen.

#### Zakelijke gebruikers kunnen omleidingen buiten Git declareren (vroege adopter-programma) {#apache-rewritemaps-early-adopter}

Net als AEM 6.5 voert Apache/dispatcher opnieuw schrijfkaarten in die op een specifieke locatie in de publicatieopslagplaats zijn geplaatst, en laadt ze, zonder dat een pijpleiding op een webniveau hoeft te worden uitgevoerd. Deze benadering laat bedrijfsgebruikers redirects verklaren gebruikend een spreadsheet of een UI, zoals ACS Commons Redirect de Manager van de Kaart of een douanetoepassing. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) for Loading Dynamic Content (Early Introducter Program) {#esi-early-adopter}

Adobe beheerde CDN steunt nu [ de Zijde van Edge omvat (ESI) ](/help/implementing/dispatcher/edge-side-includes.md), een prijsverhogingstaal voor de dynamische assemblage van de Webinhoud van het randniveau. Door ESI fragmenten op te nemen, kunt u de algemene pagina van HTML bij CDN met hogere TTLs in het voorgeheugen plaatsen, terwijl het halen van uit oorsprong die kleinere secties die hogere toegangsupdates (lagere TTLs) vereisen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

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
