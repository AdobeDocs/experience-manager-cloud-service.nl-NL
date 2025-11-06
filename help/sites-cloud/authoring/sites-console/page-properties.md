---
title: Pagina-eigenschappen
description: Leer meer over de verschillende eigenschappen die een pagina kan hebben en hoe ze het gedrag van de pagina bepalen en hoe deze wordt beheerd.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
mini-toc-levels: 2
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---


# Pagina-eigenschappen {#page-properties}

Leer meer over de verschillende eigenschappen die een pagina kan hebben en hoe ze het gedrag van de pagina bepalen en hoe deze wordt beheerd.

>[!TIP]
>
>Voor details op hoe u de eigenschappen van een pagina kunt uitgeven en veranderen, te zien gelieve het document [ het Uitgeven Eigenschappen van de Pagina.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md)

## Overzicht en beschikbaarheid van eigenschappen {#overview}

Met pagina-eigenschappen kunt u vele aspecten van een pagina beheren, van de titel en branding van de pagina tot aan de machtigingen. De eigenschappen worden over verschillende tabbladen verdeeld, waarvan sommige afhankelijk van het type pagina kunnen worden verborgen. Zoals de meeste eigenschappen in AEM, [ pagina kunnen eigenschappen worden geërft.](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#inheritance)

>[!NOTE]
>
>In dit document worden alle mogelijke pagina-eigenschappen beschreven. Afhankelijk van het type pagina zijn niet alle eigenschappen beschikbaar.

## Tabblad Standaard {#basic}

### Titel en tags {#title-tags}

* **Titel** - bepaalt de titel van paginameta voor SEO doeleinden evenals de titel die in de paginacontent wordt getoond (tenzij met voeten getreden)

   * De titel van de pagina wordt getoond in diverse plaatsen in AEM UI met inbegrip van de **kaart/lijstmeningen van 0} Plaatsen {in de** Console van Plaatsen.[](/help/sites-cloud/authoring/sites-console/introduction.md)
   * Dit is een verplicht veld.

* **Markeringen** - bepaalt de markeringen van paginameta voor SEO doeleinden

   * U kunt codes toevoegen aan of verwijderen uit de pagina door de lijst in het selectievak bij te werken.
   * Gebruik de vervolgkeuzelijst om een bestaande tag te selecteren.
   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.

      * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
      * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.

   * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
   * Voor meer informatie over markeringen, zie [ Gebruikend Markering.](/help/sites-cloud/authoring/sites-console/tags.md)

* **Verbergen in Navigatie** - wijst erop of de pagina in de paginanavigatie van de resulterende plaats wordt getoond of verborgen

### Branding {#branding}

Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Deze functionaliteit vereist gebruik van de Component van de Pagina van versie 2.14.0 of later van de [ Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

* **Merk Slug**

   * **met voeten treden** - Controle om de merkschuine streep op deze pagina te bepalen.

      * De waarde wordt geërft door om het even welke kindpagina&#39;s tenzij zij ook hun **vastgestelde waarden van de Overschrijving** hebben.

   * **waarde van de Overschrijving** - de tekst van de merkschuine streep die aan de paginatitel moet worden toegevoegd.

      * De waarde wordt aan de paginatitel toegevoegd na een pipe-teken, zoals `Cycling Tuscany | Always ready for the WKND`

### HTML-id {#html-id}

* **identiteitskaart** - identiteitskaart van HTML om op de component van toepassing te zijn.

### Meer titels en beschrijving {#more-titles}

* **Titel van de Pagina** - een titel die op de pagina moet worden gebruikt

   * Dit wordt meestal gebruikt door titelcomponenten.
   * Als leeg, wordt de **Titel** gebruikt.

* **Titel van de Navigatie** - U kunt een afzonderlijke titel voor gebruik in de navigatie (bijvoorbeeld, specificeren als u iets beknopter wilt).

   * Als leeg, wordt de **Titel van de Pagina** gebruikt.

* **Ondertitel** - een ondertitel voor gebruik op de pagina
* **Beschrijving** - Uw beschrijving van de pagina, zijn doel, of een andere details u wilt toevoegen

### Aan/Uit-tijd {#on-off-time}

De aan/uit-tijd voor een pagina is een handige manier om inhoud die al is gepubliceerd, tijdelijk te verbergen. De inhoud blijft op de publicatie-instantie staan wanneer deze is uitgeschakeld. Als u een pagina uitschakelt, wordt de publicatie van de inhoud niet ongedaan gemaakt.

* **op Tijd** - de datum en de tijd waarop de gepubliceerde pagina zichtbaar (teruggegeven) op het publicatiemilieu wordt gemaakt. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

   * Als reeds [ gepubliceerd, ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) is deze pagina beschikbaar op publiceer instantie, maar gehouden slapend (verborgen) tot het teruggeven op de gespecificeerde tijd.
   * Als niet gepubliceerd en [ voor auto-replicatie wordt gevormd, ](/help/operations/replication.md#on-and-off-times-trigger-configuratio) wordt de pagina automatisch gepubliceerd, dan teruggegeven, op de gespecificeerde tijd.
   * Als niet gepubliceerd en niet gevormd voor auto-replicatie, wordt de pagina niet automatisch gepubliceerd, zodat wordt 404 gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.

* **Van Tijd** - Gelijkaardig aan en vaak gebruikt in combinatie met **op Tijd**, bepaalt dit de tijd waarbij de gepubliceerde pagina op het publicatiemilieu wordt verborgen.

Verlaat deze gebieden (**op Tijd** en **van Tijd**) leeg voor pagina&#39;s u wilt publiceren en beschikbaar hebben onmiddellijk en beschikbaar op publiceer milieu tot zij (het normale scenario) worden gedeactiveerd.

>[!NOTE]
>Als of **op Tijd** of **van Tijd** in het verleden is, en de automatische replicatie wordt gevormd, dan wordt de relevante actie onmiddellijk teweeggebracht.

>[!TIP]
>
>Aan/uit-tijden hebben uitsluitend betrekking op inhoud die al is gepubliceerd (handmatig of via automatische replicatie). Daarom hebben publicatieworkflows, zoals die voor het goedkeuren van inhoud, geen invloed op de publicatiestatus van de pagina als gevolg van aan-/uittijden en aan/uit-tijden. Daarom zijn aan/uit-tijden het meest geschikt voor het tijdelijk tonen/verbergen van inhoud die al is goedgekeurd en gepubliceerd.
>
>Als u wenst om nieuwe inhoud met alle bijbehorende werkschema&#39;s te publiceren of (unpublish inhoud) volledig te verwijderen uit uw plaats, overweeg [ het leiden van uw publicatie.](/help/sites-cloud/authoring/sites-console/publishing-pages.md#manage-publication)

### Vanity URL {#vanity-url}

Met deze eigenschap kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of meer expressieve URL kunt gebruiken. Als de URL vanity bijvoorbeeld is ingesteld op `welcome` op de pagina die wordt aangegeven door het pad `/v1.0/startpage` voor de website `http://example.com` , is `http://example.com/welcome` de URL van de vanity van `http://example.com/content/v1.0/startpage` .

>[!CAUTION]
>
>Vanity-URL&#39;s:
>
>* Moet uniek zijn.
>* Geen ondersteuning voor regex-patronen.
>* Deze mag niet op een bestaande pagina worden ingesteld.

* **voeg** toe - Uitgezocht om een gebied te tonen om een ijdelheid URL voor de pagina te bepalen.
   * Selecteer nogmaals om meerdere items toe te voegen.
   * Selecteer **verwijder** pictogram om ijdelheid URL te schrappen.
* **Redirect Vanity URL** - wijst erop of u de pagina de ijdelheid URL wilt gebruiken of aan daadwerkelijke URL van de pagina opnieuw richten

## Geavanceerd {#advanced}

### Instellingen {#settings}

* **Taal** - de paginataal
* **Wortel van de Taal** - moet worden gecontroleerd als de pagina de wortel van een taalexemplaar is
* **opnieuw richt** - wijst op de pagina waaraan deze pagina automatisch met een status van HTML `302 Found` zou moeten opnieuw richten
   * **Permanent opnieuw richten** - wanneer gecontroleerd, richt de pagina aan de doelweg die samen met een status van HTML `301 Moved Permanently` wordt verstrekt.
* **Ontwerp**
* **Alias** - specificeert een alias die met deze pagina moet worden gebruikt
   * Als u bijvoorbeeld een alias van `private` voor de pagina `/content/wknd/us/en/magazine/members-only` definieert, kunt u deze pagina ook openen via `/content/wknd/us/en/magazine/private`
   * Als u een alias maakt, wordt de eigenschap `sling:alias` op het paginaknooppunt ingesteld. Dit heeft alleen invloed op de bron, niet op het pad naar de opslagplaats.
   * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [ publiceer opties ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) in de redacteur zijn slechts beschikbaar voor pagina&#39;s die via hun daadwerkelijke wegen worden betreden.
   * Zie [ Gelokaliseerde paginanamen onder SEO en de Beste praktijken van het Beheer URL ](/help/overview/seo-and-url-management.md#localized-page-names) voor meer informatie.

### Configuratie {#configuration}

* **Geërft van &lt;path>** - laat/maak overerving van de **Configuratie van de Wolk** voor de pagina toe onbruikbaar
   * De beschikbaarheid van knevels van **Configuratie van de Wolk** voor het uitgeven

* **Configuratie van de Wolk** - de weg aan de geselecteerde configuratie

### Sjablooninstellingen {#template-settings}

* **Toegestane Malplaatjes** - [ bepaalt de lijst van malplaatjes die ](/help/sites-cloud/authoring/page-editor/templates.md#enabling-and-allowing-a-template-template-author) binnen deze subtak beschikbaar zijn
   * Elke waarde moet een absoluut pad naar een sjabloon zijn.
   * Gebruik `/.*` om alle sjablonen onder dit pad toe te staan.
* **Pagina van het Gebruik als Malplaatje** - [ creeer een nieuw malplaatje dat op de huidige pagina wordt gebaseerd.](/help/sites-cloud/authoring/universal-editor/templates.md)
   * Dit is alleen van toepassing op pagina&#39;s die zijn gemaakt voor gebruik met Edge Delivery Services van de Universal Editor.

### Verificatievereiste {#authentication}

* **laat** toe - laat gebruik van authentificatie toe om tot de pagina toegang te hebben

>[!NOTE]
>
>De gesloten gebruikersgroepen voor de pagina worden bepaald op de **[Toestemmingen](#permissions)** tabel.

* **Login Pagina** - de pagina die voor login moet worden gebruikt

### Exporteren {#export}

* **de Configuratie van de Uitvoer** - specificeert een de uitvoerconfiguratie

## SEO {#seo}

* **Canonical Url** - die wordt gebruikt om canonical URL van de pagina te beschrijven
   * Als de URL van de pagina leeg wordt gelaten, is deze de canonieke URL.

* **Codes Robots** - gebruik dropdown om de robots markeringen te selecteren om het gedrag van de kruipende zoekmachine te controleren
   * Sommige opties zijn in strijd met elkaar, in welk geval de meer permissieve optie voorrang krijgt.

* **produceer Sitemap** - wanneer geselecteerd, wordt a `sitemap.xml` geproduceerd voor deze pagina, en zijn nakomelingen.

## Afbeeldingen {#images}

### Aanbevolen afbeelding {#featured-image}

Deze sectie wordt gebruikt om het beeld te selecteren en te vormen om te omvatten. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

* **Beeld** - u kunt **** een activa kiezen, of voor een dossier doorbladeren om te uploaden, dan **uitgeven**, of **ontruimen** het geselecteerde beeld.
* **Alternatieve Tekst** - een tekst die wordt gebruikt om de betekenis en/of functie van het beeld te vertegenwoordigen, algemeen gebruikt door het schermlezers
* **erven - Waarde die van de activa DAM** wordt genomen - wanneer gecontroleerd, wordt de alternatieve tekst bevolkt met de waarde van de `dc:description` meta-gegevens in DAM.

### Miniatuur {#thumbnail}

In deze sectie wordt de miniatuur van de afbeelding voor de pagina geselecteerd en geconfigureerd. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

* **produceer Voorproef** - produceer een voorproef van de pagina om als duimnagel te gebruiken
* **upload Beeld** - upload een beeld om als duimnagel te gebruiken
* **Uitgezochte Beeld** - selecteer een bestaand element om als duimnagel te gebruiken
* **terugkeren** - deze optie wordt beschikbaar nadat u een verandering in de duimnagel hebt aangebracht. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

## Cloud Services {#cloud-services}

* **de Configuraties van Cloud Service** - bepaalt welke configuratie voor de wolkendiensten voor de pagina wordt gebruikt
* **die van** wordt overgeërfd - voor Levende Exemplaren en de Kopieën van de Taal, worden de wolkenconfiguraties door gebrek geërfd van de Vervaging.
   * Uitschakelen om overerving te overschrijven

## Personalization {#personalization}

### ContextHub-configuraties {#contexthub-config}

* **ContextHub Weg** - bepaal de [ configuratie ContextHub ](/help/sites-cloud/authoring/personalization/contexthub.md)
* **Weg van Segmenten** - bepaal de [ weg van Segmenten ](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

### Doelconfiguratie {#targeting-config}

* **Merk** - bepaalt a [ Merk om een werkingsgebied te specificeren voor het richten ](/help/sites-cloud/authoring/personalization/targeted-content.md)
   * Voor deze optie moet de gebruikersaccount deel uitmaken van de `Target Administrators` -groep.

## Machtigingen {#permissions}

Gebruik het **lusje van Toestemmingen** om te bepalen welke gebruikers, groepen, of [ gesloten gebruikersgroepen (CUGs) ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) tot de pagina kunnen toegang hebben en/of wijzigen.

* **voeg Toestemmingen** toe
* **geeft Gesloten Groep van de Gebruiker uit**
* Bekijk de **Effectieve Toestemmingen**

## Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren. De blauwdrukken dienen als basis voor Levende Kopieën, en maken deel uit van [ Multisite Beheer.](/help/sites-cloud/administering/msm/overview.md)

* **Uitdraaiing** - stel een uitrol van blauwdrukinhoud aan Levende Exemplaren in werking
* **Levend Overzicht van het Exemplaar** - Open een venster om de Levende de paginastructuur van het Exemplaar te doorbladeren
* **Huidige Levende Kopieën** - een lijst van pagina&#39;s die op (namelijk Levende Kopieën van) worden gebaseerd de geselecteerde blauwdrukpagina

## Live kopie {#live-copy}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die zijn geconfigureerd als live kopieën. Zoals met [ blauwdrukken, ](#blueprint) Levende Exemplaren deel van [ Multisite Beheer zijn.](/help/sites-cloud/administering/msm/overview.md)

* **synchroniseer** - synchroniseer Levend Exemplaar met blauwdruk, die lokale wijzigingen houden
* **Teruggestelde** - het Levende Exemplaar van het Terugstellen aan staat van blauwdruk, verwijderend lokale aanpassingen
* **Opschorting** - onderbreek Levend Exemplaar van verdere rollout wijzigingen
* **losmaken** - loskoppel Levend Exemplaar van blauwdruk

### Source {#source}

* Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

### Status {#status}

* Hiermee geeft u de huidige status van Live kopie van de pagina weer

### Configuratie {#live-copy-config}

* **Levende Overerving van het Exemplaar** - als gecontroleerd, is de Levende configuratie van het Exemplaar efficiënt op alle kinderen.
* **erven de Vorm van de Output van het Overerven van Bovenliggend** - als gecontroleerd, wordt de rollout configuratie geërft van de ouder van de pagina.
* **kies Configuratie van de Uitvoer** - bepaalt de omstandigheden waaronder de wijzigingen van het Vervagen en slechts beschikbaar worden verspreid wanneer **Inherit de Vorm van de Uitvoer van Bovenliggend** niet wordt geselecteerd
* **Lijst van uitgesloten wegen**

## Voorvertoning {#preview}

Wanneer het milieu van de a [ voorproef ](/help/sites-cloud/authoring/sites-console/previewing-content.md) wordt toegelaten, zijn de volgende details beschikbaar:

* **Voorproef URL** - URL die voor de toegang tot van de inhoud op het voorproefmilieu wordt gebruikt

## Progressieve webtoepassing {#progressive-web-app}

Een auteur van inhoud kan via een eenvoudige configuratie functies voor progressieve webapps (PWA) inschakelen voor ervaringen die zijn gemaakt in AEM Sites. Uw site kan zich dan gedragen als een native app door deze te installeren op het thuisscherm van het bezoekersapparaat en vervolgens offline beschikbaar te maken.

{{pwa-deprecation}}

### Installeerbare ervaring configureren {#config-pwa}

* **laat PWA** toe - wanneer toegelaten, kunnen de bezoekers van de pagina de plaats als PWA installeren.
* **Opstarten URL** - URL die zou moeten worden geladen wanneer de gebruiker Webapp lanceert
   * Als de URL relatief is, wordt de manifest-URL gebruikt als basis-URL om
   * Als deze URL leeg is, wordt de URL gebruikt van de pagina vanwaar de app is geïnstalleerd.
   * U wordt aangeraden een waarde in te stellen.
* **Wijze van de Vertoning** - hoe browser zou moeten worden verborgen of anders aan de gebruiker op het lokale apparaat worden voorgesteld
* **de richtlijn van het Scherm** - hoe PWA apparatenrichtingen zal behandelen
* **kleur van het Thema** - de kleur van app die beïnvloedt hoe het werkende systeem van de lokale gebruiker de inheemse toolbar UI en navigatiecontroles toont
* **Achtergrondkleur** - de achtergrondkleur van app, die wordt getoond aangezien app laadt
* **Pictogram** - het pictogram dat app op het apparaat van de gebruiker vertegenwoordigt wanneer PWA wordt geïnstalleerd

### Cachebeheer (geavanceerd) {#cache-management}

* **Caching strategie en frequentie van inhoud verfrissen zich** - bepaalt het caching model voor uw PWA.
* **Dossiers aan geheime voorgeheugen voor off-line gebruik**
   * **Dossier pre-caching (technische voorproef)** - de Dossiers op AEM worden ontvangen worden bewaard aan het lokale browser geheime voorgeheugen wanneer de de dienstarbeider installeert en alvorens het wordt gebruikt.
   * **Cliënt-zij Bibliotheken** - Cliënt-zijbibliotheken aan geheim voorgeheugen voor off-line ervaring
   * **de uitbreidingen van de Weg** - De verzoeken van het netwerk voor de bepaalde wegen worden onderschept en de caching inhoud is teruggekeerd in overeenstemming met de gevormde Caching strategie en de frequentie van inhoud verfrissen zich
   * **de uitsluitingen van de Weg** - Deze dossiers zullen nooit in het voorgeheugen ondergebracht worden ongeacht de montages onder Dossier pre-caching en de opneming van de Weg.

>[!NOTE]
>
>Zie [ toelatend de Progressieve Eigenschappen van de App van het Web ](/help/sites-cloud/authoring/sites-console/enable-pwa.md) voor meer details.

