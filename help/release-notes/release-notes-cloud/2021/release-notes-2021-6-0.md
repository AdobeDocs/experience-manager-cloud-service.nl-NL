---
title: Nota's van de versie voor 2021.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Nota's van de versie voor 2021.6.0 versie van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service beschreven.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [&#x200B; Recente Updates van de Documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor details van documentatieupdates niet direct met een versie verwant.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.6.0 is 28 juni 2021.
De volgende release (2021.7.0) vindt plaats op 29 juli 2021.

## Video vrijgeven {#release-video}

Heb een blik bij de [&#x200B; Juni 2021 video van het Overzicht van de Versie &#x200B;](https://video.tv.adobe.com/v/334296) voor een samenvatting van de toegevoegde eigenschappen.

## XML Documentation voor AEM als cloudservice {#xml-documentation}

### Wat is er nieuw? {#what-is-new-xml-documentation}

* XML Documentation for AEM as a Cloud Service is nu GA.
* Hierdoor kunnen bestaande klanten van AEM Cloud Service XML Documentation-addon aanschaffen voor het importeren, maken, beheren en leveren van technische inhoud op meerdere kanalen, waaronder AEM-sites

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.6.0 en 2021.5.0 beschreven.

### Releasedatum {#release-date-june-cm}

De Releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.6.0 is 10 juni 2021.
De volgende release is gepland voor 15 juli 2021.

### Wat is er nieuw? {#what-is-new-junecm}

* De Voorproefdienst zal op rolbasis aan alle Programma&#39;s worden opgesteld. Klanten worden in-product op de hoogte gebracht wanneer hun Programma voor de Dienst van de Voorproef wordt toegelaten. Zie [&#x200B; Toegang hebbend tot de Dienst van de Voorproef &#x200B;](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) voor meer details.

* Geweven Gedeelten die tijdens de bouwstijlstap worden gedownload zullen nu in het voorgeheugen ondergebracht tussen pijpleidinguitvoeringen worden. Deze functie wordt de komende weken ingeschakeld voor klanten.

* De naam van het programma kan nu worden bewerkt in het dialoogvenster Programma bewerken.

* De standaardnaam van de vertakking die tijdens zowel het maken van een project als in de standaard-push-opdracht via de werkstromen voor het beheren van de it wordt gebruikt, is gewijzigd in `main` .

* De ervaring met het bewerken van programma&#39;s in de gebruikersinterface is vernieuwd.

* De kwaliteitsregel `ImmutableMutableMixCheck` is bijgewerkt om `/oak:index` -knooppunten te classificeren als zijnde onveranderlijk.

* De kwaliteitsregels `CQBP-84` en `CQBP-84--dependencies` zijn samengevoegd tot één regel. Als onderdeel van deze consolidatie, identificeert het aftasten van gebiedsdelen nauwkeuriger kwesties in derdegebiedsdelen die aan runtime van AEM worden opgesteld.

* Om verwarring te voorkomen zijn de segmentrijen AEM publiceren en Dispatcher publiceren op de pagina Environment Details geconsolideerd.

  ![&#x200B; de milieu&#39;s van Dispatcher &#x200B;](/help/implementing/cloud-manager/release-notes/assets/aem-dispatcher.png)

* Er is een nieuwe code kwaliteitsregel toegevoegd om de structuur van `damAssetLucene` indexen te valideren. Zie {de Indexen van Oak van het Activa van 10} Douane DAM [&#x200B; voor meer details.](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check)

* De pagina met omgevingsdetails geeft nu meerdere domeinnamen weer voor de services Publiceren en Voorvertonen (al naargelang van toepassing). Zie [&#x200B; Details van het Milieu &#x200B;](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) aan meer details.

### Opgeloste problemen {#bug-fixes-junecm}

* JCR-knooppuntdefinities die een nieuwe regel bevatten nadat de naam van het hoofdelement niet correct is geparseerd.

* De API voor opslagplaatsen weergeven filtert geen verwijderde opslagplaatsen.

* Er is een onjuist foutbericht weergegeven wanneer een ongeldige waarde voor de planningsstap is opgegeven.

* Soms, kan de gebruiker een groene *actieve* status naast een IP Lijst van gewenste personen zien zelfs wanneer die configuratie niet werd opgesteld.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in de onmogelijkheid kunnen resulteren om de productiepijplijn tot stand te brengen of uit te geven.

* Sommige programma het uitgeven opeenvolgingen konden in het **Overzicht** pagina resulteren die een misleidend bericht tonen om programma opstelling opnieuw uit te voeren.

## [!DNL Experience Manager Assets] als een [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#ga-features-assets}

* Met de functie voor automatisering van inhoud kan [!DNL Experience Manager Assets] de API&#39;s van [!DNL Adobe Creative Cloud] gebruiken om de productie van elementen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor de functionaliteit is geen code vereist en de functie werkt vanuit de DAM.
* [!DNL Adobe Asset Link] v3.0 voor [!DNL Adobe Photoshop] , [!DNL Adobe Illustrator] en [!DNL Adobe InDesign] en [!DNL Adobe Asset Link] v2.0 voor [!DNL Adobe XD] wordt vrijgegeven. Het voorziet in:

   * Ondersteuning voor [!DNL Assets Essentials] .
   * Mogelijkheid om automatisch verbinding te maken met [!DNL Experience Manager] als a [!DNL Cloud Service] of [!DNL Assets Essentials] .

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### Nieuwe functies die beschikbaar zijn in het [!DNL Assets] prereleasekanaal {#beta-features-assets}

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.
* De downloadfunctionaliteit van Linkshare gebruikt asynchrone downloads die de downloadsnelheid verhogen.
* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.
* [!DNL Experience Manager Assets] sluit de PDF Viewer van [!DNL Adobe Document Cloud] in om een voorvertoning van de ondersteunde documenten weer te geven. Met deze functie kunnen gebruikers PDF en andere bestanden met meerdere pagina&#39;s voorvertonen zonder dat er een complexe verwerking nodig is. Dit verbetert de eigenschappariteit met [!DNL Experience Manager] 6.5.

### Buizen gecorrigeerd in [!DNL Assets] {#bugs-fixed-assets}

* Wanneer u een eigenaar toevoegt aan een submap, voegt [!DNL Assets] ook dezelfde gebruiker toe als een eigenaar van de bovenliggende map. (CQ-4323737)
* Als een gebruiker bij het toevoegen van elementen aan verzamelingen een filter toepast op de zoekopdracht Verzamelingen, kan de gebruiker de Verzamelingen niet weergeven in de lijstweergave. (CQ-4323181)
* Wanneer u naar bestanden en mappen zoekt en de gebruiker een filter toepast en [!UICONTROL Files & Folders] selecteert, worden alleen de bestanden weergegeven, maar niet de map. (CQ-4319543)

## [!DNL Experience Manager Sites] als een [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#ga-features-sites}

* Publiceren naar voorvertoningsniveau wordt nu weergegeven als paginastatus in de gebruikersinterface voor Sitebeheer
* Publiceren op Voorvertoning van niveau surfact nu de URL van de voorvertoning aan het einde van de handeling en doorgaan met de URL in pagina-eigenschappen voor latere referentie

## [!DNL Experience Manager Forms] als een [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* Aangepaste kolommen filteren in AEM Inbox toegevoegd.
* Mogelijkheid toegevoegd om de themaeditor en stijllaag van een aangepaste formuliereditor te gebruiken voor het opmaken van de component captcha.
* Verbeterde snelheid en nauwkeurigheid voor het automatisch detecteren van logische secties in de bron-PDF forms en het converteren van deze secties naar overeenkomstige adaptieve formulierdeelvensters.
* Toegevoegde verplaatsingsactie om een PDF- of XDP-bestand van de ene map naar de andere te verplaatsen.

### Beta-functie van [!DNL Forms]  {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Met communicatie-API&#39;s kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF&#39;s genereren op basis van een XFA-formulier, PDF en Adobe Acrobat-formulier (AcroForm).

* **Variabele die Extern van Gegevens**: U kunt gegevens van de variabelen van het Werkschema van AEM op een extern opslagsysteem bewaren door uw organisatie wordt beheerd.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Buizen gecorrigeerd in [!DNL Forms] {#forms-bugs-fixed}

* Wanneer een veld wordt gevalideerd voordat gegevens via FDM (Form Data Model) naar de service Backend worden verzonden, slagen validaties erin, maar wordt postvalidatie niet aangeroepen door de service Form Data Model.
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Dit is een bekend probleem in Apple iOS. [&#x200B; FB9117687 &#x200B;](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] als een [!DNL Cloud Service] {#screens}

In deze sectie worden de opmerkingen bij de release voor AEM Screens as a Cloud Service beschreven.

### Releasedatum {#release-date-june-screens}

De Releasedatum voor AEM Screens as a Cloud Service is 24 juni 2021.

### Wat is er nieuw? {#what-is-new-screens-june}

>[!NOTE]
>Zie {de 1} Gids van as a Cloud Service van 0&rbrace; AEM Screens voor stichtingskennis die voor met succes wordt vereist het installeren, het vormen, en het runnen van Screens as a Cloud Service en verbinding uit aan gedetailleerde concepten technische documentatie.[&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html)

* Bulk Device Registration Management betekent dat het provisioning van enorme hoeveelheden spelerapparaten sneller en efficiënter verloopt.

* Verbeterde zoek- en filteropties voor de inventarisweergaven Apparaat, Weergave en Kanaal.

* Momentopname van apparaatgezondheid bespaart tijd door een kritieke status in één oogopslag te bieden.

* De pagina met objectdetails bevat een overzicht van de meest relevante informatie voor elk object in uw project.

## CIF-invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Nieuwe CIF-product- en categoriereferentiegegevenstypen voor Content Fragments (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* Nieuwe Commerce Content Fragment Core-component
* Full-text handelzoekopdracht ondersteund in AEM-achtergrond
* Commerce Core Components biedt ondersteuning voor Adobe Commerce AI Recs-gegevensverzameling
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.4 is 28 juni 2021.

### Wat is er nieuw? {#what-is-new-ctt-latest}

* Steun voor een facultatieve [&#x200B; pre-exemplaar &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) stap die aan gebruik met CTT wordt toegevoegd. De pre-kopiestap kan worden gebruikt om de extractie- en insluitingsfasen van de activiteit van de inhoudsoverdracht aanzienlijk te versnellen wanneer de bron-AEM-instantie is geconfigureerd voor het gebruik van een gegevensopslag van Amazon S3 of Azure Blob Storage.

* Guardrail toegevoegd aan CTT om te voorkomen dat gebruikers een opname stoppen en mogelijk gegevens beschadigen zodra deze het kritieke punt tijdens de innamefase heeft bereikt.

* De logboeken van de uitwinning maakten beschrijvender om met het oplossen van problemen te helpen.

* Meer beschrijvende statusberichten voor opname toegevoegd in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-ctt-latest}

* Terwijl een opname op de instantie Auteur stopt, overschrijft de interface een eerder voltooide opname op de instantie Publish naar `STOPPED` van `FINISHED` . Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.16 is 30 juni 2021.

### Wat is er nieuw? {#what-is-new-bpa-latest}

* Mogelijkheid om ontbrekende onderliggende knooppunten in mappen onder `/content/dam` te detecteren en hierover te rapporteren.

* Mogelijkheid om de gebruikte versie van Best Practices Analyzer te detecteren en hierover verslag uit te brengen.

### Opgeloste problemen {#bug-fixes-bpa-latest}

* Logboekfout met betrekking tot niet-ondersteunde Repository Structure (URS) hersteld.
