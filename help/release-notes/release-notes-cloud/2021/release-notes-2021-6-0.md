---
title: Opmerkingen bij de release 2021.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
description: Opmerkingen bij de release 2021.6.0 van [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

In de volgende sectie worden de algemene opmerkingen bij de release voor de huidige (meest recente) versie van [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Van hieruit kunt u navigeren om notities van eerdere versies vrij te geven, bijvoorbeeld voor de versies in 2020, 2021 enzovoort.

>[!NOTE]
>
>Zie [Recente documentatieupdates](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html) voor meer informatie over documentatie-updates die niet rechtstreeks verband houden met een release.

## Releasedatum {#release-date}

De releasedatum voor [!DNL Adobe Experience Manager] as a Cloud Service 2021.6.0 is 28 juni 2021.
De volgende release (2021.7.0) vindt plaats op 29 juli 2021.

## Video vrijgeven {#release-video}

Kijk eens naar de [Juni 2021 Overzicht van de Versie](https://video.tv.adobe.com/v/334296) video voor een overzicht van de toegevoegde functies.

## XML Documentation for AEM as a cloud Service {#xml-documentation}

### Wat is er nieuw? {#what-is-new-xml-documentation}

* XML Documentation for AEM as a Cloud Service is nu GA.
* Hierdoor kunnen bestaande AEM Cloud Service-klanten XML Documentation-addon aanschaffen voor het importeren, maken, beheren en leveren van technische inhoud op meerdere kanalen, waaronder AEM sites

## Cloud Manager {#cloud-manager}

In deze sectie worden de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2021.6.0 en 2021.5.0 beschreven.

### Releasedatum {#release-date-june-cm}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2021.6.0 is 10 juni 2021.
De volgende release is gepland voor 15 juli 2021.

### Wat is er nieuw? {#what-is-new-junecm}

* De Voorproefdienst zal op rolbasis aan alle Programma&#39;s worden opgesteld. Klanten worden in-product op de hoogte gebracht wanneer hun Programma voor de Dienst van de Voorproef wordt toegelaten. Zie [Voorvertoningsservice openen](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) voor meer informatie .

* Geweven Gedeelten die tijdens de bouwstijlstap worden gedownload zullen nu in het voorgeheugen ondergebracht tussen pijpleidinguitvoeringen worden. Deze functie wordt de komende weken ingeschakeld voor klanten.

* De naam van het programma kan nu worden bewerkt in het dialoogvenster Programma bewerken.

* De standaardvertakkingsnaam die tijdens zowel de projectverwezenlijking als in het gebrek wordt gebruikt duw bevel via beheert de werkschema&#39;s van de it is veranderd in `main`.

* De ervaring met het bewerken van programma&#39;s in de gebruikersinterface is vernieuwd.

* De kwaliteitsregel `ImmutableMutableMixCheck` is bijgewerkt om te classificeren `/oak:index` knooppunten als onveranderlijk.

* De kwaliteitsregels `CQBP-84` en `CQBP-84--dependencies` zijn in één regel geconsolideerd. Als onderdeel van deze consolidatie, identificeert het aftasten van gebiedsdelen nauwkeuriger kwesties in derdegebiedsdelen die aan AEM runtime worden opgesteld.

* Om verwarring te voorkomen, zijn de segmentrijen van de AEM Publish en Publish Dispatcher op de pagina van de Details van het Milieu geconsolideerd.

  ![Verzendomgevingen](/help/implementing/cloud-manager/release-notes/assets/aem-dispatcher.png)

* Er is een nieuwe regel voor de kwaliteit van de code toegevoegd om de structuur van `damAssetLucene` indexen. Zie [Aangepaste DAM-indexen voor luyleen](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) voor meer informatie .

* De pagina met omgevingsdetails geeft nu meerdere domeinnamen weer voor de services Publiceren en Voorvertonen (al naargelang van toepassing). Zie [Omgevingsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) voor meer informatie.

### Opgeloste problemen {#bug-fixes-junecm}

* JCR-knooppuntdefinities die een nieuwe regel bevatten nadat de naam van het hoofdelement niet correct is geparseerd.

* De API voor opslagplaatsen weergeven filtert geen verwijderde opslagplaatsen.

* Er is een onjuist foutbericht weergegeven wanneer een ongeldige waarde voor de planningsstap is opgegeven.

* De gebruiker kan soms een groen zien *actief* status naast een IP Lijst van gewenste personen zelfs toen die configuratie niet werd opgesteld.

* Sommige programma&#39;s die opeenvolgingen uitgeven zouden in de onmogelijkheid kunnen resulteren om de productiepijplijn tot stand te brengen of uit te geven.

* Sommige bewerkingsreeksen van programma&#39;s kunnen resulteren in de **Overzicht** pagina met een misleidend bericht om de programma-instelling opnieuw uit te voeren.

## [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#assets}

### Nieuwe functies in [!DNL Assets] {#ga-features-assets}

* Met de functionaliteit voor automatisering van inhoud kunt u [!DNL Experience Manager Assets] gebruiken [!DNL Adobe Creative Cloud] API&#39;s om de productie van bedrijfsmiddelen op schaal te automatiseren. Het verbetert de snelheid van de inhoud door de benodigde tijd en herhalingen aanzienlijk te verminderen om variaties van hetzelfde element te maken. Voor de functionaliteit is geen code vereist en de functie werkt vanuit de DAM.
* [!DNL Adobe Asset Link] v3.0 voor [!DNL Adobe Photoshop], [!DNL Adobe Illustrator], en [!DNL Adobe InDesign] en [!DNL Adobe Asset Link] v2.0 voor [!DNL Adobe XD] wordt vrijgegeven. Het voorziet in:

   * Ondersteuning voor [!DNL Assets Essentials].
   * Mogelijkheid om automatisch te verbinden met [!DNL Experience Manager] als [!DNL Cloud Service] of [!DNL Assets Essentials].

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### Nieuwe functies beschikbaar in het dialoogvenster [!DNL Assets] prerelease-kanaal {#beta-features-assets}

* De weergave-instellingen worden verbeterd zodat gebruikers een standaardweergave en een standaardsorteerparameter kunnen kiezen.
* De downloadfunctionaliteit van Linkshare gebruikt asynchrone downloads die de downloadsnelheid verhogen.
* Gebruikers kunnen de mappen zoeken en filteren op basis van voorspelden van eigenschappen.
* [!DNL Experience Manager Assets] sluit de PDF Viewer in, aangedreven door [!DNL Adobe Document Cloud] om een voorvertoning van de ondersteunde documenten weer te geven. Met deze functie kunnen gebruikers PDF- en andere bestanden met meerdere pagina&#39;s voorvertonen zonder dat er sprake is van complexe verwerking. Hierdoor wordt de pariteit van de functie verbeterd met [!DNL Experience Manager] 6.5

### Buizen vastgesteld in [!DNL Assets] {#bugs-fixed-assets}

* Wanneer u een eigenaar toevoegt aan een submap, [!DNL Assets] voegt ook dezelfde gebruiker toe als een eigenaar van de bovenliggende map. (CQ-4323737)
* Als een gebruiker bij het toevoegen van elementen aan verzamelingen een filter toepast op de zoekopdracht Verzamelingen, kan de gebruiker de Verzamelingen niet weergeven in de lijstweergave. (CQ-4323181)
* Als de gebruiker bij het zoeken naar bestanden en mappen een filter toepast en [!UICONTROL Files & Folders], alleen de bestanden worden weergegeven, maar niet de map. (CQ-4319543)

## [!DNL Experience Manager Sites] als [!DNL Cloud Service] {#sites}

### Nieuwe functies in [!DNL Sites] {#ga-features-sites}

* Publiceren naar voorvertoningsniveau wordt nu weergegeven als paginastatus in de gebruikersinterface voor Sitebeheer
* Publiceren op Voorvertoning van niveau surfact nu de URL van de voorvertoning aan het einde van de handeling en doorgaan met de URL in pagina-eigenschappen voor latere referentie

## [!DNL Experience Manager Forms] als [!DNL Cloud Service] {#forms}

### Nieuwe functies in [!DNL Forms] {#what-is-new-forms}

* Toegevoegde mogelijkheid om aangepaste kolommen in AEM Inbox te filteren.
* Mogelijkheid toegevoegd om de themaeditor en stijllaag van een aangepaste formuliereditor te gebruiken voor het opmaken van de component captcha.
* Verbeterde snelheid en nauwkeurigheid voor het automatisch detecteren van logische secties in de PDF forms van de bron en het converteren van deze secties naar overeenkomstige adaptieve formulierdeelvensters.
* Toegevoegde verplaatsingsactie om een PDF- of XDP-bestand van de ene map naar de andere te verplaatsen.

### Beta-functie van [!DNL Forms] {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Met communicatie-API&#39;s kunt u XDP-sjablonen en XML-gegevens combineren om afdrukdocumenten in verschillende indelingen te genereren. Met de service kunt u documenten in synchrone modus genereren. Met de API&#39;s kunt u toepassingen maken waarmee u:
   * Definitieve formulierdocumenten genereren door sjabloonbestanden te vullen met XML-gegevens.
   * Uitvoerformulieren genereren in verschillende indelingen, waaronder niet-interactieve PDF-afdrukstromen.
   * Afdruk-PDF genereren op basis van een XFA-formulier PDF en een Adobe Acrobat-formulier (AcroForm).

* **Variabele-gegevensexternalizer**: U kunt gegevens van AEM workflowvariabelen opslaan op een extern opslagsysteem dat wordt beheerd door uw organisatie.

U kunt schrijven naar [!DNL formscsbeta@adobe.com] om u aan te melden voor het bètaprogramma.

### Buizen vastgesteld in [!DNL Forms] {#forms-bugs-fixed}

* Wanneer een veld wordt gevalideerd voordat gegevens via FDM (Form Data Model) naar de service Backend worden verzonden, slagen validaties erin, maar wordt postvalidatie niet aangeroepen door de service Form Data Model.
* Wanneer u een formulier verzendt met een standaard HTML-uploadveld van een Apple iOS-apparaat, wordt soms de inhoud van het bestand niet verzonden en wordt aan de andere kant een bestand van 0 byte ontvangen. Dit is een bekend probleem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] als [!DNL Cloud Service] {#screens}

In deze sectie worden de opmerkingen bij de release voor AEM Screens as a Cloud Service beschreven.

### Releasedatum {#release-date-june-screens}

De releasedatum voor AEM Screens as a Cloud Service is 24 juni 2021.

### Wat is er nieuw? {#what-is-new-screens-june}

>[!NOTE]
>Zie [AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html) Handleiding voor basiskennis die vereist is voor het correct installeren, configureren en uitvoeren van rasters as a Cloud Service en koppeling naar gedetailleerde technische documentatie.

* Bulk Device Registration Management betekent dat het provisioning van enorme hoeveelheden spelerapparaten sneller en efficiënter verloopt.

* Verbeterde zoek- en filteropties voor de inventarisweergaven Apparaat, Weergave en Kanaal.

* Momentopname van apparaatgezondheid bespaart tijd door een kritieke status in één oogopslag te bieden.

* De pagina met objectdetails bevat een overzicht van de meest relevante informatie voor elk object in uw project.

## CIF invoegtoepassing {#cloud-services-cif}

### Nieuwe functies {#what-is-new-cif}

* Nieuwe CIF product- en categoriereferentietypen voor inhoudsfragmenten (incl. product/categoriekiezer (ondersteuning voor gebruikersinterface)
* Nieuwe Commerce Content Fragment Core-component
* Full-text zoekopdracht ondersteund in AEM achterkant
* Commerce Core Components ondersteunt Adobe Commerce Sensei Recs gegevensverzameling
* Verbeterde SEO-vriendelijke URL&#39;s voor categoriepagina&#39;s
* Ondersteuning voor aangepaste HTTP-headers per site/config

## Inhoud overbrengen {#content-transfer-tool}

### Releasedatum {#release-date-ctt-latest}

De releasedatum voor Content Transfer Tool v1.5.4 is 28 juni 2021.

### Wat is er nieuw? {#what-is-new-ctt-latest}

* Ondersteuning voor een optionele [voorkopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html) toegevoegd aan gebruik met CTT. De pre-exemplaarstap kan worden gebruikt om de extractie en inname fasen van de activiteit van de inhoudoverdracht beduidend te versnellen wanneer de bron AEM instantie wordt gevormd om een gegevensbestand van de Opslag van Amazon S3 of van Azure Blob te gebruiken.

* Guardrail toegevoegd aan CTT om te voorkomen dat gebruikers een opname stoppen en mogelijk gegevens beschadigen zodra deze het kritieke punt tijdens de innamefase heeft bereikt.

* De logboeken van de uitwinning maakten beschrijvender om met het oplossen van problemen te helpen.

* Meer beschrijvende statusberichten voor opname toegevoegd in de gebruikersinterface.

### Opgeloste problemen {#bug-fixes-ctt-latest}

* Terwijl het tegenhouden van een opname op de instantie van de Auteur, overlapte UI een eerder gebeëindigde opname op de Publish instantie aan `STOPPED` van `FINISHED`. Dit is opgelost.

## Analysator van best practices {#best-practices-analyzer}

### Releasedatum {#release-date-bpa}

De releasedatum voor de analyse van best practices v2.1.16 is 30 juni 2021.

### Wat is er nieuw? {#what-is-new-bpa-latest}

* Mogelijkheid om ontbrekende onderliggende knooppunten te detecteren en te rapporteren in mappen onder `/content/dam`.

* Mogelijkheid om de gebruikte versie van Best Practices Analyzer te detecteren en hierover verslag uit te brengen.

### Opgeloste problemen {#bug-fixes-bpa-latest}

* Logboekfout met betrekking tot niet-ondersteunde Repository Structure (URS) hersteld.
