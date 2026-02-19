---
title: Contextafhankelijke experimenten in AEM as a Cloud Service
description: Leer hoe u de plug-in voor experimenten kunt gebruiken om experimentele mogelijkheden aan uw site toe te voegen.
feature: Administering
role: Admin
badgeSaas: label="AEM Sites" type="Positive" tooltip="van toepassing op AEM Sites)."
exl-id: 420f8d5e-27f9-4081-b174-b2d7752779f7
source-git-commit: ef20e6df5e19596ea742e6ac267b1f37b7517cfa
workflow-type: tm+mt
source-wordcount: '1805'
ht-degree: 0%

---

# Contextafhankelijke experimenten in AEM as a Cloud Service {#contextual-experimentation}

>[!NOTE]
>Momenteel is de functie voor contextuele experimenten alleen beschikbaar via het bètaprogramma. Neem contact op met de ondersteuning van Adobe of met uw accountmanager voor toegang tot het bètaprogramma.

Experimentatie is het testen van het ontwerp, de functionaliteit en de code van uw site om de prestaties te verbeteren en uw site efficiënter en gestroomlijnder te maken. Dit wordt bereikt door de inhoud of functionaliteit te wijzigen, de resultaten te vergelijken met een eerdere versie en de verbeteringen te kiezen die meetbare effecten hebben.

Als dit op de juiste wijze gebeurt, is het een krachtig patroon om conversies, betrokkenheid en bezoekerservaring te verbeteren. Over het algemeen zijn er een paar kwesties die moeten worden vermeden wanneer men de praktijk wil toepassen:

* **Te weinig**: de meeste bedrijven experimenteren niet genoeg, en wanneer zij, experimenteren zij met te weinig verkeer om betekenisvolle resultaten te krijgen.
* **Te langzaam**: vele experimentatiekaders vertragen de plaats zo veel dat de potentiële nieuwe omzettingen niet voor het verloren verkeer en de stuitingen wegens langzame teruggeven kunnen compenseren.
* **Te complex**: als het teveel tijd aan opstelling een nieuw experiment vergt, dan minder experimenten zullen worden in werking gesteld.

Voor plaatsen die op Adobe Experience Manager lopen, is er &quot;uit de doos&quot;**experimenterende stop** die ontwikkelaars toestaat om een experimenteringsvermogen aan hun plaatsen toe te voegen. Drie dingen maken deze benadering anders dan andere experimentatiekaders:

* Het is eenvoudig tests in te stellen met de gereedschappen waarmee uw auteurs al vertrouwd zijn en er is geen afzonderlijke aanmelding nodig.
* Het is diep geïntegreerd in het leveringssysteem van AEM, vertraagt niet uw plaats en veerkrachtig aan veranderingen in code en inhoud.
* Het staat het testen van eenvoudige inhoudveranderingen evenals experimenten toe die ontwerp, functionaliteit, en code behandelen.

## Voordat u begint {#before-start}

De experimentatiestop - binnen wordt gebruikt binnen de context van [&#x200B; Edge Delivery Services &#x200B;](/help/edge/overview.md) zodat zult u een rekening van Github, een inhoudsbewaarplaats zoals de Aandrijving van SharePoint of van Google, en ook zult u [&#x200B; AEM Sidekick &#x200B;](https://www.aem.live/docs/sidekick) nodig hebben. Zie ook [&#x200B; Begonnen het Worden - de Universele pagina van het Leerprogramma van de Ontwikkelaar van de Redacteur &#x200B;](https://www.aem.live/developer/tutorial) en [&#x200B; Begonnen het worden - Leerprogramma van de Ontwikkelaar &#x200B;](https://www.aem.live/developer/tutorial).

Nadat u alles opstelling hebt, **gelieve op deze video** te letten titelde [&#x200B; Onmiddellijke experimentatie &#x200B;](https://business.adobe.com/products/experience-manager/sites/testing-optimization.html) voor een korte demonstratie op hoe het experimenteren plug-in werkt.

## Veelgebruikte termen {#frequently-used-terms}

Voordat u de rest van de handleiding volgt voor het instellen van uw eerste experiment, zijn er een aantal veelgebruikte termen die u bekend moeten maken:

* **Controle**: de ervaring voorafgaand aan het runnen van het experiment. Alle experimenten proberen een verbetering ten opzichte van de controleervaring te testen en aan te tonen.
* **Challenger**: een ervaring die van de controleervaring verschillend is en &quot;getest&quot;tegen het of naast het is.
* **Varianten**: de controle en de toerist zijn alle varianten van een experiment.
* **Statistische Belangrijkheid**: Evaluerend als uw uitdager echt beter dan de controle is. Door de statistische significantie te berekenen kunt u veel geluk uitsluiten en u concentreren op de resultaten die een echt effect hebben.

## Experimentele varianten en algemene workflow {#experiment-variants-workflow}

Over het algemeen gebruikt u bij het instellen van een experiment een reeds bestaande pagina als de controlepagina. Vervolgens maakt u een pagina voor ondervragers die de controlepagina voor sommige bezoekers vervangt. Op de pagina Challenger kunt u verschillende dingen testen, zoals inhoudvarianten, verschillende paginalay-outs, call-to-action (CTA) enzovoort. U kunt deze experimentele varianten configureren door metagegevensparameters toe te voegen aan de controlepagina (zie hieronder).

De [&#x200B; Operationele dienst van Telemetrie &#x200B;](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) verzamelt dan gegevens, bijvoorbeeld, het aantal bezoekers in de controlepagina tegenover de uitdagerpagina. Vervolgens gebruikt u deze gegevens om de noodzakelijke verbeteringen voor uw site te kiezen. Zolang u binnen de gevestigde ontwerptaal van uw website blijft en de bestaande blokfunctionaliteit gebruikt, zou u een proefvariant moeten kunnen opzetten en het naar productie binnen een paar minuten verzenden.

>[!NOTE]
>Houd er rekening mee dat de insteekmodule geen gegevens van de eindgebruiker gebruikt die tot hun identificatie kunnen leiden, noch deze gegevens blijft gebruiken. Geen eindgebruiker opt-in noch koekjestoestemming wordt vereist wanneer het gebruiken van de standaardconfiguratie die de [&#x200B; Operationele dienst van Telemetrie in AEM as a Cloud Service &#x200B;](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) gebruikt.

### Id van experiment {#experiment-identifier}

Voordat u begint, moet elk experiment een eigen id hebben voor tracerings- en analysedoeleinden. Een goed uitgangspunt is om een goede, unieke id te vinden voor uw experiment. Dit is de &#39;experimentele id&#39;. Experimenten worden vaak lineair genummerd of gecorreleerd aan hun uitgevers-id in een uitgiftecontrole- of beheersysteem. Experimentele id&#39;s gebruiken vaak een voorvoegsel voor het project, bijvoorbeeld: `OPT-0134` , `EXP0004` of `CCX0076` .

### Maak uw pagina voor hartenpagina&#39;s {#create-challenger-page}

Volgens de conventie verdient het aanbeveling een map te maken met een kleine-letterexperiment-id in uw `/experiments/ folder` (bijvoorbeeld /experiments/ccx0076/). Alle pagina&#39;s voor de varianten van de uitdager bevinden zich in deze map. U maakt deze map in uw lokale opslagruimte, bijvoorbeeld Sharepoint of Goggle Drive.

De map met experimenten moet er ongeveer als volgt uitzien:

![&#x200B; experimenten-omslag &#x200B;](/help/sites-cloud/administering/assets/experiments-folder.png)

Zodra de omslag wordt gecreeerd, zet een exemplaar van uw controlepagina in die omslag, en pas de veranderingen op de pagina toe die u als deel van uw proefvariant (zie video hierboven) zou willen testen. Laten we bijvoorbeeld aannemen dat we op de website de volgende pagina hebben waarop we een experiment willen uitvoeren:

![&#x200B; controle-pagina &#x200B;](/help/sites-cloud/administering/assets/control-page.png)

Uw exemplaar van de uitdager die in de `experiments/<experiment-id>` omslag wordt geplaatst zou als volgt kunnen kijken:

![&#x200B; challenger-page &#x200B;](/help/sites-cloud/administering/assets/challenger-page.png)

Geef een voorvertoning weer van de pagina met de uitdager en publiceer deze met de assistent en wanneer u klaar bent met het ontwerpen van de pagina met de uitdager. De URL van de gepubliceerde uitdager wordt gebruikt in de volgende sectie - het configureren van het experiment.

### Het experiment configureren {#configure-experiment}

Zodra de pagina&#39;s van de uitdager klaar zijn om te gaan, moet u naar de controlepagina teruggaan en meta-gegevens toevoegen erop wijzend dat de pagina(s) nu deel van de test uitmaken.

Er zijn twee meta-gegevensrijen die voor een proefvariant moeten worden toegevoegd.

* **Experiment**: die uw experimenteeridentiteitskaart bevatten

* **Experimentele Varianten**: die URLs voor alle uitdagers van deze pagina bevatten, door lijnonderbrekingen wordt gescheiden als u meer dan één uitdager hebt.

Zie het onderstaande voorbeeld:

![&#x200B; meta-gegevens-pagina &#x200B;](/help/sites-cloud/administering/assets/metadata-page.png)

Voor elk experiment, wordt het verkeer verdeeld over alle varianten (controle en uitdagers) en automatisch geplaatst aan een gelijke verdeling. Als je één toerist hebt, zal er automatisch een 50/50-verdeling zijn tussen controle en de toerist. Als u twee uitdagers hebt, zult u automatisch een derde van het verkeer zien dat aan controle wordt toegewezen en elke uitdager etc.

U kunt de verkeersverdeling met voeten treden door de meta-gegevens te vormen. Voor meer informatie over hoe u de meta-gegevens kunt aanpassen die in uw experimenten worden gebruikt, zie de volgende [&#x200B; pagina &#x200B;](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

### Experimentele varianten voorvertonen en in een werkgebied plaatsen {#preview-stage-experiment}

Zodra u klaar bent om een voorvertoning van uw experiment te bekijken en deze te testen, klikt u op Voorvertoning in de zijtrap linksboven. Wanneer u een voorvertoning weergeeft van een pagina waarop een experiment wordt uitgevoerd, wordt de overlay voor experimenten weergegeven in de `.aem.page` -voorvertoningsomgeving. Met de overlay voor experimenten kunt u schakelen tussen de verschillende experimenten en kunt u ook verkeersgegevens ophalen.

<!--- ![experimentation-overlay](/help/sites-cloud/administering/assets/experimentation-overlay.png)

By using the experimentation overlay, authors can get quick insights on the performance of experiments being run on the production site. These insights are helpful in making a decision about the duration of the experiment, but also about which variant is best suited for production.-->

De gegevensinzameling om de doeltreffendheid van elke variant te meten is gebaseerd op de [&#x200B; Operationele dienst van Telemetrie in AEM as a Cloud Service &#x200B;](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md).

### Uw experimentele variant naar productie verzenden {#production-experiment}

Selecteer de testpagina&#39;s en klik op Publiceren in de zijschop om zowel het besturingselement als de variant(en) live te zetten.

### Voorbeelden van hoofdletters/kleine letters gebruiken {#use-case-examples}

Hieronder staan verschillende voorbeelden van praktijkvoorbeelden voor experimentele varianten. In het algemeen zal de basisworkflow vergelijkbaar zijn met de bovenstaande, met bijzondere wijzigingen voor elk geval (zoals het aantal pagina&#39;s met een hoofdtelefoon of wijzigingen in metagegevens).

#### Experimenteer op volledige pagina {#full-page}

U gebruikt een volledig paginaexperiment om te testen tussen twee varianten van dezelfde pagina. Dit is een volledige pagina variant van een a/b-test waarbij u een besturingselement en een pagina voor de uitdager hebt. U vervangt de volledige inhoud van de &quot;originele&quot;controlepagina in de uitdagende variant met een verschillend type van inhoud. Houd in mening dat door gebrek het klantenverkeer gelijk (50/50) wordt verdeeld, maar u kunt douanesplitsen tot stand brengen als u houdt van.

<!--The metadata on the control page should look like this:

METADATA SETUP

#### Sections of the page Experiment {#sections-of-the-page}

This is experiment is similar to the full page one presented above but now the a/b test will contain changes to a section of the page instead of the whole content. For example, you can modify and test a carousel element, the call to action element and so on. As such, you will have a control and a challenger page, with the challenger page containing the modified elements. The metadata on the control page should look like this:

METADATA SETUP

#### Multi-path Experiment {#multi-path}

By leveraging the experimentation plug-in, you can set up a/b tests on several pages of your website at once. For example, on all product pages, photo galleries, all blog posts and so on.

The configuration logic is the same as above - you will create a control page and one or more challenger variants of that page. What changes in the multi-page use-case, is the following:

• You will create multiple control pages each with one or more variants.
• The control pages must have the same experiment ID in metadata field.

For example: We have 5 different production pages for which we need to set up an a/b test. We create 5 control pages (as detailed in the chapters above) and 5 (or more) challenger variants.

We then create an experiment ID, let’s say `prod-exp` and add this ID in the experiment metadata field for each control page. This basically means that all pages with the same ID are now “grouped”. We then assign the challenger variants for each control page, taking care to sequence them properly in case we have more than one variant for each control.

The metadata on the control page should look like this:

METADATA SETUP

#### Code-level experiments {#code-level}

Note that the examples above assume you have different content variants to serve, but if you want to run a pure code-based a/b test, this is achievable via:

Metadata

Experiment    Hero Test
Experiment Variants    2

This will create just two variants, without touching the content, and you'll be able to target those based on the `experiment-hero-test` and `variant-control/variant-challenger-1/variant-challenger-`2 CSS classes that will be set on the `<body>` element.

#### Browser based audience experiment {#browser-based}

You can create browser based experiments, where you deliver separate challenger pages depending on the browser used. You can, for example, serve a different challenger page to a Firefox user as opposed to a Chrome user. This is achieved by leveraging the audience parameter.

Once you configure the experiment, the target audience will be evaluated based on the context of the browser (client side) and limited to the browser APIs available. As such, you do not need to use server side third-party systems or customer profile data for your experiment.

Before you start authoring this experiment variant, the audience parameter needs to be defined in the project codebase. For more details, see ee the following [page](https://github.com/adobe/aem-experience-decisioning/wiki/Experiments#authoring).

Once the audiences have been defined you are ready to author the experiment. As stated previously, let’s say you want to create a Firefox versus Chrome experiment where you will serve different pages depending on the browser.

You need two different challenger pages, so set up the experiment as follows:

1.Duplicate the Control page by right-clicking and copying it to the experiment folder. You need to copies, one for Firefox and one for Chrome.
2.Rename the copies. Give them specific names like “page-for-firefox”.
3.Change the content of the pages depending on what you need to serve on Firefox versus Chrome.
4.Change the metadata as explained in the section below.
5.Click Preview from the side-kick in the upper left side, to preview the changes.

The most important part when authoring this experiment is to change the metadata in the control page. Let’s say you defined the browser audiences in the codebase as: Audience: Firefox and Audience: Chrome. You need to edit the control page and add these audiences and point to the appropriate challenge page you set up previously. It should look similar to this:

Metadata
Title Control Page
Description This is the control page.
Experiment ExpBrowser
Experiment Variants `https://{ref}--{repo}--{org}.hlx.page/my-page-for-firefox https://{ref}--{repo}--{org}.hlx.page/my-page-for-chrome`
Audience: Firefox `https://{ref}--{repo}--{org}.hlx.page/page-for-firefox`
Audience: Chrome `https://{ref}--{repo}--{org}.hlx.page/page-for-chrome`

After this configuration, the users will be triaged based on the browser they connect with and the appropriate challenger page will be served.

Please keep in mind that the names above are only for illustration purposes. You can define the Audiences parameter and the challenger pages according to your needs, for example: Audience (Firefox) or Audience Firefox.-->

## Andere overwegingen {#other-considerations}

Hieronder ziet u verschillende andere aspecten die u in overweging moet nemen wanneer u contextexperimenten gebruikt.

### Conversie {#conversion}

Experimenten zijn ingesteld om de conversie aan te pakken (hiermee worden klikbare elementen op de pagina bijgehouden). Alle experimenten moeten worden gedefinieerd voor:

* Type experiment
* Welke ervaring heeft het experiment in de weg?
* Hoeveel varianten bevat het experiment?
* Wat is de samenstelling van elke variant

### Zorg ervoor dat de experimentele varianten niet zijn geïndexeerd {#experiment-not-indexed}

Bij het uitvoeren van experimenten is het meestal aan te raden om de varianten van de sitemap uit te sluiten en ervoor te zorgen dat ze niet door zoekmachines worden geïndexeerd. De reden hiervoor is dat de variantpagina kan worden beschouwd als dubbele inhoud en SEO negatief kan beïnvloeden.

U kunt dit op een van de volgende twee manieren doen:

* Als u alle experimenten centraliseert in een specifieke map, bijvoorbeeld `/experiments` : zorg ervoor dat het `metadata.xlsx` -werkblad een rij bevat met `/experiments/**` als pad en een robots-kolom met de waarden `noindex` , `nofollow` .
* Als u de controle over het experiment en varianten met de reguliere inhoud behoudt: voeg een robots-item toe in de paginametagegevens voor elke variant, met de waarde `noindex`, `nofollow` .

## Ontwikkelaars en technische informatiebronnen {#dev-resources}

Adobe Experience Manager gebruikt [ Operationele Telemetrie ] (/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md

) om bewerkingsgegevens te verzamelen die strikt noodzakelijk zijn voor het opsporen en verhelpen van functionele en prestatieproblemen op Adobe Experience Manager-sites. De operationele gegevens van Telemetrie kunnen worden gebruikt om prestatieskwesties te diagnostiseren. Met de operationele telemetrie blijft de privacy van bezoekers behouden door middel van steekproeven (slechts een klein deel van alle paginaweergaven wordt gecontroleerd).

### Privacy {#privacy-experimentation}

[&#x200B; de Operationele dienst van Telemetrie in AEM as a Cloud Service &#x200B;](/help/sites-cloud/administering/operational-telemetry-for-aem-as-a-cloud-service.md) wordt ontworpen om bezoekersprivacy te bewaren en gegevensinzameling te minimaliseren. Als bezoeker betekent dit dat Adobe niet zal proberen persoonlijke gegevens over jou te verzamelen of informatie die je kunt volgen. Als plaatsexploitant, herzie hieronder verzamelde gegevenspunten om te begrijpen als zij toestemming vereisen.
AEM Operational Telemetry gebruikt geen clientstatus of -id, zoals cookies of `localStorage` , `sessionStorage` of dergelijke, om gebruiksmaatstaven te verzamelen. Gegevens worden transparant verzonden via een `Navigator.sendBeacon` -aanroep, niet via pixels of vergelijkbare technieken. Er is geen &quot;vingerafdrukken&quot; van apparaten of personen via hun IP-adres, de tekenreeks Gebruikersagent of andere gegevens voor het vastleggen van gesamplede gegevens.

Het is niet toegestaan persoonsgegevens toe te voegen aan de operationele telemetriegegevensverzameling en operationele telemetriegegevens mogen niet worden gebruikt voor gebruiksgevallen die verder gaan dan strikt noodzakelijk.

### Veelgestelde vragen {#faq}

Hieronder vindt u een lijst met veelgestelde vragen:

Q: Kan ik de splitsingsverhouding tussen de varianten van mijn experiment aanpassen, bijvoorbeeld 10% voor controle en 90% voor de uitdager?

Ja, kan de gespleten verhouding via [&#x200B; meta-gegevens &#x200B;](#configure-experiment) worden gevormd.

V: Kan ik experimenteren op zowel tekst als afbeeldingen?

Ja, de variant kan een volledig verschillende pagina zijn, zodat kunt u lay-outveranderingen zelfs testen.
