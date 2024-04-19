---
title: Pagina-eigenschappen bewerken
description: Leer hoe u de eigenschappen definieert die vereist zijn voor het beheer van een pagina in AEM.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '2268'
ht-degree: 2%

---

# Pagina-eigenschappen bewerken {#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is op de juiste wijze beschikbaar.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

* **Titel en tags**

   * **Titel** - De titel van de pagina wordt op verschillende plaatsen weergegeven. Bijvoorbeeld de **Websites** en de **Sites** kaart-/lijstweergaven.
      * Dit is een verplicht veld.
   * **Tags** - Hier kunt u codes aan de pagina toevoegen of eruit verwijderen door de lijst in het selectievak bij te werken.
      * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
      * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.
         * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
         * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
      * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
      * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
      * Zie voor meer informatie over tags [Tags gebruiken](/help/sites-cloud/authoring/features/tags.md).
   * **Verbergen in navigatie** - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site.

* **Branding**

  Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Voor deze functionaliteit is het gebruik van de component Pagina vanaf versie 2.14.0 of hoger van het dialoogvenster [Core Components.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **Brand Slug**

      * **Negeren** - Schakel dit selectievakje in om de merkwitruimte op deze pagina te definiëren.
         * De waarde wordt overgeërfd door onderliggende pagina&#39;s, tenzij deze ook hun **Negeren** ingestelde waarden.
      * **Waarde overschrijven** - De tekst van de merkmarkering die aan de paginatitel moet worden toegevoegd.
         * De waarde wordt toegevoegd aan de paginatitel na een pipe-teken, zoals &quot;Cycling Tuscany&quot; | Altijd klaar voor de WKND&quot;

* **HTML-id**

   * **ID** - HTML-id die moet worden toegepast op de component.

* **Meer titels en beschrijving**

   * **Paginatitel** - Een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Indien leeg, **Titel** wordt gebruikt.
   * **Navigatietitel** - U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Indien leeg, **Titel** wordt gebruikt.
   * **Ondertitel** - Een ondertitel voor gebruik op de pagina.
   * **Beschrijving** - Uw beschrijving van de pagina, het doel of andere details die u wilt toevoegen.

* **Aan/Uit-tijd**

  >[!NOTE]
  >
  > Zie [Aan- en uittijden - Configuratie activeren](/help/operations/replication.md#on-and-off-times-trigger-configuration) voor details van hoe te om de verwante automatische replicatie te vormen.

  >[!NOTE]
  >Als een van de **Op tijd** of **Uit-tijd** is in het verleden, en de automatische replicatie wordt gevormd, dan wordt de relevante actie onmiddellijk teweeggebracht.

   * **Op tijd** - De datum en het tijdstip waarop de gepubliceerde pagina zichtbaar wordt gemaakt (weergegeven) in de publicatieomgeving. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

      * Indien al [gepubliceerd (handmatig)](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) deze pagina wordt slapend (verborgen) gehouden totdat deze op het opgegeven tijdstip wordt weergegeven.
      * Als niet gepubliceerd, en gevormd voor auto-replicatie, wordt de pagina automatisch gepubliceerd, dan teruggegeven, op de gespecificeerde tijd.
      * Als niet gepubliceerd, en niet gevormd voor auto-replicatie, wordt de pagina niet automatisch gepubliceerd, zodat wordt 404 gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.

   * **Uit-tijd** - Vergelijkbaar met en vaak gebruikt in combinatie met **Op tijd** Hiermee bepaalt u de tijd waarop de gepubliceerde pagina wordt verborgen in de publicatieomgeving.

   * Deze velden behouden (**Op tijd** en **Uit-tijd**) is leeg voor pagina&#39;s die u direct wilt publiceren en die beschikbaar zijn in de publicatieomgeving totdat ze zijn gedeactiveerd (het normale scenario).

* **Vanity URL**

   * Hiermee kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of meer expressieve URL kunt gebruiken.
   * Als bijvoorbeeld de URL voor Vanity is ingesteld op `welcome` naar de pagina die wordt aangeduid door het pad `/v1.0/startpage` voor de website `http://example.com`vervolgens `http://example.com/welcome` zou de vanzelf-URL zijn van `http://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >Vanity-URL&#39;s:
  >
  >* Dit moet uniek zijn, dus zorg ervoor dat de waarde niet al door een andere pagina wordt gebruikt.
  >* Geen ondersteuning voor regex-patronen.
  >* Deze mag niet op een bestaande pagina worden ingesteld.

   * **Toevoegen** - Selecteer deze optie om een veld weer te geven waarin een vanity-URL voor de pagina wordt gedefinieerd.
      * Selecteer nogmaals om meerdere items toe te voegen.
      * Selecteer de **Verwijderen** pictogram om de vanity URL te verwijderen.
   * **Redirect Vanity URL** - Geeft aan of de pagina de vanity-URL moet gebruiken.

### Geavanceerd {#advanced}

* **Instellingen**

   * **Taal** - De paginataal
   * **Taalbasis** - Moet worden gecontroleerd als de pagina de basis van een taalkopie is
   * **Omleiden** - Geeft de pagina aan waarnaar deze pagina automatisch moet worden omgeleid met een HTML `302 Found` status.
      * **Permanent omleiden** - Als deze optie is ingeschakeld, wordt de pagina omgeleid naar het doelpad dat samen met een HTML wordt geleverd `301 Moved Permanently` status.
   * **Ontwerp** - Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site
   * **Alias** - Hiermee wordt een alias opgegeven die met deze pagina moet worden gebruikt
      * Als u bijvoorbeeld een alias definieert van `private` voor de pagina `/content/wknd/us/en/magazine/members-only`, kan deze pagina ook worden geopend via `/content/wknd/us/en/magazine/private`
      * Het creëren van een aliasreeksen `sling:alias` eigenschap op het paginaknooppunt, die alleen invloed heeft op de bron, niet op het pad naar de opslagplaats.
      * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [Publicatieopties](/help/sites-cloud/authoring/fundamentals/publishing-pages.md) in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.
      * Zie [Gelokaliseerde paginanamen onder SEO- en URL-beheertips](/help/overview/seo-and-url-management.md#localized-page-names).

* **Configuratie**

   * **Overgenomen van &lt;path>** - overerving in-/uitschakelen; schakelt beschikbaarheid van **Cloud Configuration** voor selectie

   * **Cloud Configuration** - Het pad naar de geselecteerde configuratie

* **Sjablooninstellingen**

   * **Toegestane sjablonen** - [Hiermee definieert u de lijst met beschikbare sjablonen](/help/sites-cloud/authoring/features/templates.md#enabling-and-allowing-a-template-template-author) binnen dit subbijkantoor

* **Verificatievereiste**

   * **Inschakelen** - Gebruik van verificatie toestaan om toegang te krijgen tot de pagina

     >[!NOTE]
     >
     >Gesloten gebruikersgroepen voor de pagina worden gedefinieerd op de **[Machtigingen](#permissions)** tab.

   * **Aanmeldingspagina** - De pagina die moet worden gebruikt voor aanmelding

* **Exporteren**

   * **Configuratie exporteren** - Geeft een exportconfiguratie op

* **SEO**

   * **Canonical Url** - kan worden gebruikt om de canonieke URL van de pagina te overschrijven; als deze leeg wordt gelaten, is de URL van de pagina de canonieke URL

   * **Robots-tags** - selecteer de robots-tags om het gedrag van zoekprogrammacrawlers te bepalen.

     >[!NOTE]
     >
     >Sommige opties veroorzaken een conflict met elkaar. In geval van een conflict krijgt de meer permissieve optie voorrang.

   * **Sitemap genereren** - als deze optie is geselecteerd, wordt een sitemap.xml gegenereerd voor deze pagina en de onderliggende elementen ervan

### Afbeeldingen {#images}

* **Aanbevolen afbeelding**

  Selecteer en configureer de afbeelding die u wilt weergeven. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

   * **Afbeelding**

     U kunt **Selecteren** een middel, of doorblader voor een dossier om te uploaden, dan **Bewerken**, of **Wissen**.

   * **Alternatieve tekst** - een tekst die wordt gebruikt om de betekenis en/of functie van de afbeelding weer te geven, bijvoorbeeld voor schermlezers.

   * **Overnemen - Uit het DAM-activum overgenomen waarde** - als deze optie wordt ingeschakeld, wordt de alternatieve tekst gevuld met de waarde van de optie `dc:description`metagegevens in DAM

* **Miniatuur**

  De paginaminiatuur configureren

   * **Voorvertoning genereren** - Een voorbeeld van de pagina genereren om als miniatuur te gebruiken
   * **Afbeelding uploaden** - Upload een afbeelding die u als miniatuur wilt gebruiken
   * **Afbeelding selecteren** - Selecteer een bestaand element dat u als miniatuur wilt gebruiken
   * **Vorige versie** - Deze optie wordt beschikbaar nadat u een wijziging in de miniatuur hebt aangebracht. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Cloud Servicen {#cloud-services}

* **Configuraties van Cloud Servicen** - Eigenschappen definiëren voor cloudservices

### Personalisatie {#personalization}

* **ContextHub-configuraties**

   * **Overgenomen van &lt;path>** - overerving in-/uitschakelen; schakelt beschikbaarheid van **ContextHub Pathn** en **Segmentpad** voor selectie

   * **ContextHub-pad** - De [ContextHub-configuratie](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Segmentpad** - De [Segmentpad](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **Doelconfiguratie**

   * **Merk** - Definieert een [Merk om een werkingsgebied voor het richten te specificeren](/help/sites-cloud/authoring/personalization/targeted-content.md).

  >[!NOTE]
  >Deze optie vereist dat de gebruikersaccount zich in de `Target Administrators`groep.

### Machtigingen {#permissions}

* **Machtigingen**

   * **Machtigingen toevoegen**
   * **Gesloten gebruikersgroep bewerken**
   * De weergave **Effectieve machtigingen**

### Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren. Blauwdrukken dienen als basis voor actieve kopieën en maken deel uit van [Beheer van meerdere sites](/help/sites-cloud/administering/msm/overview.md).

* **Huidige actieve kopieën** - Hiermee geeft u pagina&#39;s weer waarop deze blauwdrukpagina is gebaseerd (dat wil zeggen, Live kopieën van deze pagina zijn)

* **Rollout Configs** - Controleert de omstandigheden waaronder de wijzigingen aan Levende Exemplaar worden verspreid

### Live kopie {#live-copy}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die zijn geconfigureerd als live kopieën. Net als bij Blauwdrukken maken actieve kopieën deel uit van [Beheer van meerdere sites](/help/sites-cloud/administering/msm/overview.md).

* **Synchroniseren** - Actieve kopie synchroniseren met vervagen, lokale wijzigingen behouden
* **Herstellen** - Actieve kopie opnieuw instellen op de status Vervagen, lokale wijzigingen verwijderen
* **Onderbreken** - Live kopie van verdere rollout-wijzigingen onderbreken
* **Loskoppelen** - Actieve kopie loskoppelen van vervaging

* **Bron**

   * Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

* **Status**

   * Hiermee geeft u de huidige status van Live kopie van de pagina weer

* **Configuratie**

   * **Overerving van Actieve kopie** - Als deze optie is ingeschakeld, is de Live Copy-configuratie effectief voor alle onderliggende toepassingen
   * **Inherit Rollout Configs from Parent** - Als deze optie is ingeschakeld, wordt de rollout-configuratie overgenomen van het bovenliggende item van de pagina
   * **Uitrolconfiguratie kiezen** - Definieert de omstandigheden waaronder wijzigingen worden doorgegeven via het blauwdrukken en alleen beschikbaar zijn wanneer **Inherit Rollout Configs from Parent** is niet geselecteerd

### Voorvertoning {#preview}

Wanneer een omgeving van de Voorproef wordt toegelaten, ziet u het volgende:

* Voorbeeld-URL - de URL die wordt gebruikt voor toegang tot de inhoud in de voorvertoningsomgeving

### Progressieve webtoepassing {#progressive-web-app}

Dankzij een eenvoudige configuratie kan een auteur van inhoud nu functies (PWA) voor progressieve webtoepassingen inschakelen voor ervaringen die zijn gemaakt in AEM Sites.

>[!NOTE]
>
>Zie [Progressieve webtoepassingsfuncties inschakelen](/help/sites-cloud/authoring/features/enable-pwa.md).

* **Installeerbare ervaring configureren**

   * **PWA inschakelen** - de functie in-/uitschakelen; gebruikers kunnen de site als een PWA installeren
   * **StartupURL** - de voorkeursopstarthURL
   * **Weergavemodus** - hoe de browser moet worden verborgen of op een andere manier aan de gebruiker moet worden getoond op het lokale apparaat
   * **Schermoriëntatie** - hoe de PWA de oriëntatie van het apparaat zal verwerken
   * **Themakleur** - de kleur van de toepassing die van invloed is op de manier waarop het besturingssysteem van de lokale gebruiker de native UI-werkbalk en navigatiebesturingselementen weergeeft.
   * **Achtergrondkleur** - de achtergrondkleur van de app, die wordt weergegeven terwijl de app wordt geladen
   * **Pictogram** - het pictogram dat de toepassing op het apparaat van de gebruiker vertegenwoordigt

* **Cachebeheer (geavanceerd)**

   * **Caching strategie en frequentie van inhoudvernieuwing** - definieert het cachemodel voor uw PWA
   * **Bestanden die in cache moeten worden geplaatst voor offline gebruik**
      * **Bestanden vooraf in cache plaatsen (technische voorvertoning)** - bestanden die worden gehost op AEM worden opgeslagen in de lokale browsercache wanneer de serviceworker wordt geïnstalleerd en voordat deze wordt gebruikt
      * **Client-side bibliotheken** - clientbibliotheken die in cache moeten worden geplaatst voor offline ervaring
      * **Padinsluitingen** - de netwerkverzoeken voor de bepaalde wegen worden onderschept en de caching inhoud is teruggekeerd in overeenstemming met de gevormde Caching strategie en de frequentie van inhoud verfrissen zich
      * **Paduitsluitingen** - deze bestanden worden nooit in de cache geplaatst, ongeacht de instellingen onder Bestanden vooraf in cache plaatsen en Pad-insluiting

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

* Van de **Sites** console:
   * [Een nieuwe pagina maken](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-page) (een subset van de eigenschappen)
   * Klikken of tikken **Eigenschappen**
      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)
* Vanuit de pagina-editor:
   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Klikken of tikken **Eigenschappen** om de pagina-eigenschappen te definiëren:

1. Met de **Sites** navigeer naar de locatie van de pagina waarvan u de eigenschappen wilt weergeven en bewerken.
1. Selecteer de **Eigenschappen** optie voor de vereiste pagina met behulp van:
   * [Snelle acties](/help/sites-cloud/authoring/getting-started/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/getting-started/basic-handling.md#selecting-resources)
   * De pagina-eigenschappen worden weergegeven met de juiste tabbladen.
1. Bekijk of bewerk de eigenschappen naar wens.
1. Gebruik vervolgens **Opslaan** om uw updates op te slaan, gevolgd door **Sluiten** om naar de console terug te keren.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer u een pagina bewerkt, kunt u **Pagina-informatie** om de pagina-eigenschappen te definiëren:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.
1. Selecteer de **Pagina-informatie** pictogram om het selectiemenu te openen:
1. Selecteren **Eigenschappen openen** en er wordt een dialoogvenster geopend waarin u de eigenschappen kunt bewerken, gesorteerd op het juiste tabblad. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:
   * **Annuleren**
   * **Opslaan en sluiten**
1. Gebruik de **Opslaan en sluiten** om de wijzigingen op te slaan.

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Vanuit de **Sites**-console kunt u meerdere pagina&#39;s selecteren en vervolgens **Eigenschappen weergeven** gebruiken om de pagina-eigenschappen te bekijken en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer u door de **Sites** console
* Na gebruik van **Zoeken** om een set pagina&#39;s te zoeken

Nadat u de pagina&#39;s hebt geselecteerd en vervolgens op de knop **Eigenschappen, optie**, worden de eigenschappen voor bulkgoederen weergegeven:

![Pagina-eigenschappen voor bulkbewerking](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy
   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u:

* **Weergave**

   * Een lijst met de betrokken pagina&#39;s
      * U kunt desgewenst selecteren of deselecteren
      * Tabs
         * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.
   * Een subset van eigenschappen
      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.
   * Algemene eigenschappen met een gemeenschappelijke waarde
      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Als het veld meerdere waarden heeft (bijvoorbeeld tags), worden waarden alleen weergegeven als *alles* vaak voorkomen. Als slechts enkele van de algemene voorbeelden worden weergegeven, worden deze alleen weergegeven tijdens het bewerken.
      * Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **Bewerken**

   * U kunt de waarden in de beschikbare velden bijwerken.
      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed**.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.
   * Velden die veel voorkomen, maar die verschillende waarden op de verschillende pagina&#39;s hebben, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>`.
