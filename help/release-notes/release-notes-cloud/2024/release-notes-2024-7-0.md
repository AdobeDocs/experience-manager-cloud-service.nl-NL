---
title: Nota's van de versie voor 2024.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2024.7.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 6194df9d-8c3c-4c7f-be59-099b970a565a
source-git-commit: 47b6d7871201cd7dbc1db77620879e69bce4ad3a
workflow-type: tm+mt
source-wordcount: '1626'
ht-degree: 0%

---

# Opmerkingen bij de release 2024.7.0 voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de opmerkingen bij de functierelease voor de versie 2024.7.0 van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies, zoals 2022 of 2023, vrij te geven.
>
>Heb een blik bij [ Experience Manager geeft Roadmap ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) vrij om over de aanstaande eigenschapactivering voor [!DNL Experience Manager] as a Cloud Service te leren.

>[!NOTE]
>
>Om een maandelijks e-mailbericht over updates aan de versienota&#39;s van Experience Cloud te ontvangen, onderteken aan de [ Update van het Product van de Prioriteit Adobe ](https://www.adobe.com/subscription/priority-product-update.html).

## Releasedatum {#release-date}

De releasedatum van [!DNL Adobe Experience Manager] als een [!DNL Cloud Service] huidige release met functies (2024.7.0) is 25 juli 2024. De volgende release met functies (2024.8.0) is gepland voor 29 augustus 2024.

## Opmerkingen bij de onderhoudsrelease {#maintenance}

U kunt de recentste nota&#39;s van de onderhoudsversie [ hier ](/help/release-notes/maintenance/latest.md) vinden.

## Video vrijgeven {#release-video}

Bekijk de video Overzicht van de release van juli 2024 voor een overzicht van de functies die zijn toegevoegd in de release van 2024.7.0:

>[!VIDEO](https://video.tv.adobe.com/v/3431707?quality=12)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functie in Experience Manager Sites {#new-feature-sites}

### Programma voor vroege adoptie {#sites-early-adopter}

**produceer Variaties**

Hefboomgaard GenAI door de nieuwe eigenschap van AEM, [ produceert variaties ](/help/generative-ai/generate-variations.md), nu toegankelijk in Cloud Service. Met het genereren van variaties kunt u inhoud genereren en schalen met behulp van generatieve AI. Neem contact op met uw Adobe-accountteam voor hulp in het programma.

**het doorbladeren van activa in de Console van het Fragment van de Inhoud**

Inhoudsauteurs kunnen nu door afbeeldingen en andere elementen bladeren, deze weergeven en deze activeren zonder dat ze de Content Fragment Console hoeven te verlaten.

![ het Bladeren van activa ](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Wilt u de functie proberen en feedback delen? Stuur een e-mail naar aemcs-headless-adopter@adobe.com vanuit uw officiële e-mailadres voor meer informatie over het programma voor vroege adoptie.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

**uploadt activa gebruikend de Selecteur van Activa**

Met Asset Selector kunnen auteurs van inhoud nu de definitieve elementen rechtstreeks vanuit de kiezer uploaden door te slepen of door te bladeren vanuit het lokale bestandssysteem. Met deze functionaliteit kunnen definitieve elementen vanuit de toepassing van uw keuze naar de DAM worden geüpload.

### Functie voor vroege toegang in dynamische media {#dm-early-access}

**AI-Gegenereerde videotitels**

Door AI gegenereerde videobijschriften in Adobe Dynamic Media gebruiken kunstmatige intelligentie om automatisch bijschriften te genereren voor video-inhoud. Deze functie is ontworpen om de toegankelijkheid te verbeteren en de gebruikerservaring te verbeteren door nauwkeurige, real-time bijschriften te bieden. De AI analyseert de audiotrack van de video om spraak te transcriperen en bijschriften te maken, die kunnen worden bewerkt voor nauwkeurigheid of aanpassing. Deze bijschriften helpen te voldoen aan toegankelijkheidsvereisten en verbeteren de videobetrokkenheid van gebruikers die op tekst gebaseerde videoondersteuning gebruiken of verkiezen.

Om vroege toegang tot AI-Gegenereerde titelsteun op uw Dynamische rekening van Media te krijgen, [ creeer en voorlegt een geval van de Steun van de Klant van Adobe ](/help/assets/dynamic-media/video.md##enable-dash).

### Nieuwe functies in de Assets-weergave {#assets-view-new-features}

**de geloofsbrieven van de Inhoud integratie**

Experience Manager Assets ondersteunt nu inhoudsreferenties voor ondersteunde afbeeldingsindelingen. Deze mogelijkheid biedt informatie over de relatie tussen het actief en de manier waarop het is gemaakt, inclusief of het is gewijzigd met behulp van GenAI.

![ geloofsbrieven van de Inhoud ](/help/assets/assets/content-credentials.png)

**Visuele voorproeven van omslaginhoud**

Experience Manager Assets geeft nu visuele voorvertoningen van de inhoud van de map weer op de miniatuur van de map wanneer u naar inhoud bladert of zoekt, waardoor de beschikbare middelen in de AEM Assets-opslagruimte beter kunnen worden ontdekt.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in AEM Forms {#forms-new-prerelease-features}

#### Verbeterde Visual Rule Editor voor op kerncomponenten gebaseerde adaptieve Forms

Aangepaste auteurs van formulieren kunnen herhaalbare formuliervelden en functies van de out-of-the-box visuele regeleditor gebruiken om complexe bedrijfslogica in formulieren te maken zonder dat ze aanpassingen of ondersteuning van het ontwikkelingsteam nodig hebben.

### Functies voor vroege toegang in AEM Forms {#forms-new-early-access-features}

Het AEM Forms Early Access-programma biedt u een unieke gelegenheid om exclusieve toegang te krijgen tot geavanceerde innovaties voordat iemand anders ze ontwikkelt. Het programma biedt toegang tot meerdere innovaties.

Deze release bevat een overzicht van de innovaties die in de huidige release worden geleverd. Voor de volledige lijst van innovaties beschikbaar onder het Vroege Programma van de Toegang, zie &lbrace;de documentatie van het Programma van de Vroege Toegang van AEM Forms [&#128279;](/help/forms/early-access-ea-features.md).

#### Aangepaste formulieren maken met Universal Editor

Hefboomwerking de Universele Redacteur van Adobe Experience Manager [&#128279;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) om adaptieve vormen tot stand te brengen gebruikend de belemmering-dalingsauteursrecht van WYSIWYG, voor zowel hoofd als krachtige inschrijvingservaringen, die via de Dienst van Edge Delivery worden geleverd.  Auteurs van adaptieve formulieren kunnen eenvoudig experimenten maken en starten voor variaties van de formulieren op de webpagina&#39;s. Hierdoor kunnen ze de best presterende ervaringen voor eindgebruikers bepalen.

>[!IMPORTANT]
>
> Als u in het aansluiten van bij het Vroege Programma van de Toegang van Adobe voor om het even welke vroege toegangsinnovatie geinteresseerd bent, verzend eenvoudig een e-mail van uw officieel adres aan [ aem-forms-ea@adobe.com ](mailto:aem-forms-ea@adobe.com) om toegang te verzoeken. U kunt toegang vragen tot alle of tot specifieke innovaties.

## [!DNL Experience Manager] als een [!DNL Cloud Service] Foundation {#foundation}

### Inhoud op de CDN wissen met een Self-Serve API-sleutel {#purge-cdn}

Het plaatsen van TTL gebruikend HTTP Cachebeheer kopbal is een efficiënte benadering om de prestaties van de inhoudslevering en inhoudsversheid in evenwicht te brengen. In scenario&#39;s waarin het van essentieel belang is om bijgewerkte inhoud direct te leveren, kan het echter nuttig zijn om de CDN-cache rechtstreeks te wissen.

[ Leer hoe ](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) om de configuratie van een purge API teken zelf-dienen gebruikend de de configuratiepijplijn van Cloud Manager, zodat kunt u [ zuiveren APIs ](/help/implementing/dispatcher/cdn-cache-purge.md), met om het even welk van deze variaties aanhalen:

* Eén URL
* Meerdere URL&#39;s die een tag gebruiken
* Volledige CDN-cache leegmaken

### Zelfstandige configuratie van X-AEM-Edge-Key voor CDN die door de klant wordt beheerd {#customermanaged-keys}

Eerder, was een steunkaartje nodig om X-AEM-Edge-Sleutel te produceren die voor configuratie van een klant-beheerde CDN wordt vereist. Dit werkschema is nu zelfbediening door de zeer belangrijke waarde in een configuratiedossier te verklaren dat gebruikend de Pijpleiding van de Configuratie wordt opgesteld, verwijderend om het even welke vertraging in het aan boord gaan van een nieuw milieu. [ leer meer ](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

### Waarschuwing verkeersfilterregels {#traffic-filter-rules-alerts}

De de filterregels van het verkeer, die de naar keuze licentiable regels van de Firewall van de Toepassing van het Web (WAF) omvatten, laat u vormen welk verkeer zou moeten worden geblokkeerd.

Nu, kunt u [ aan alarm ](/help/security/traffic-filter-rules-including-waf.md#traffic-filter-rules-alerts) intekenen wanneer uw regels van de verkeersfilter worden teweeggebracht. Met e-mailmeldingen van het Actions Center kunt u op de hoogte worden gehouden wanneer bepaalde verkeersvoorwaarden zich voordoen, zodat u de juiste maatregelen kunt nemen.

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

### Kennisgevingen van het Centrum voor activiteiten in verband met de gezondheid van de inhoud Vroege adopter-programma {#actions-center-notifications}

[ Centrum van Acties ](/help/operations/actions-center.md) verzendt e-mailberichten wanneer de belangrijke incidenten gebeuren, of als iets over uw code of configuratie wordt opgemerkt waar u proactieve actie zou moeten nemen. Adobe heeft nu verschillende nieuwe typen berichten geïntroduceerd die zijn gekoppeld aan de status van uw inhoud. Deze functie is beschikbaar via een programma voor vroege adoptie. Neem contact op met de klantenservice van Adobe om deel te nemen.

#### Pagina&#39;s bevatten veel knooppunten {#page-nodes}

Een groot aantal knooppunten kan de renderprestaties verlagen en de laadtijden van de pagina verminderen. Ontvang een pro-actieve melding via het Actions Center wanneer een groot aantal knooppunten op een pagina wordt gedetecteerd, zodat u de nodige stappen kunt ondernemen om het totale aantal knooppunten op een pagina te verminderen.

#### Groot aantal actieve workflowinstanties {#running-workflows}

De prestaties van de workflowengine worden beïnvloed wanneer er een groot aantal actieve workflows is in de ontwerpomgeving. U ontvangt een proactief bericht via het Actions Center wanneer een groot aantal actieve workflowinstanties wordt gedetecteerd. Met dit proces kunt u een opschoningstaak configureren om overbodige workflows te beëindigen.

#### Gebruikers die rechtstreeks aan aangepaste groepen zijn toegevoegd {#users-customgroups}

U ontvangt een proactief bericht via het Actions Center wanneer gebruikers rechtstreeks aan aangepaste groepen worden toegevoegd. Met dit proces kunt u de best practices van IMS volgen door gebruikers toe te voegen aan relevante IMS-groepen en deze IMS-groepen vervolgens op te nemen als leden van AEM-groepen.

#### Ontbrekende JCR-inhoud {#jcr-content}

Het Centrum van acties brengt u proactief op de hoogte wanneer het missen van inhoud JCR wordt ontdekt. Op deze manier kunt u de ontbrekende inhoud toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

#### Voltooide workflows niet gewist {#workflows}

Het Centrum van acties brengt proactief u op de hoogte wanneer voltooide werkschema&#39;s ouder dan 90 dagen niet zijn gezuiverd. Deze aanpak verbetert de prestaties van de workflowengine door het aantal workflowexemplaren te verminderen.

#### Ontbrekende verkoopbron {#sling-resource}

Het Centrum van acties brengt pro-actief u op de hoogte wanneer een ontbrekende het verdelen middel wordt ontdekt. Op deze manier kunt u de ontbrekende bron toevoegen en het mislukken van bepaalde AEM Assets-functies voorkomen.

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
