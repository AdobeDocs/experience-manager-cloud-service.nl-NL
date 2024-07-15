---
title: Pagina-eigenschappen bewerken
description: Leer hoe u de eigenschappen definieert die vereist zijn voor het beheer van een pagina in AEM.
exl-id: 27521a6d-c6e9-4f43-9ddf-9165b0316084
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2268'
ht-degree: 2%

---

# Pagina-eigenschappen bewerken {#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is op de juiste wijze beschikbaar.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

* **Titel &amp; Markeringen**

   * **Titel** - de titel van de pagina wordt getoond in diverse plaatsen. Bijvoorbeeld, de **het tablijst van Websites** en de **3} kaart/lijstmeningen van Plaatsen {.**
      * Dit is een verplicht veld.
   * **Markeringen** - hier kunt u markeringen toevoegen, of verwijderen uit de pagina door de lijst in de selectievak bij te werken.
      * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
      * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.
         * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
         * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
      * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
      * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
      * Voor meer informatie over markeringen, zie [ Gebruikend Markeringen ](/help/sites-cloud/authoring/sites-console/tags.md).
   * **Verbergen in Navigatie** - wijst erop of de pagina in de paginanavigatie van de resulterende plaats wordt getoond of verborgen.

* **Branding**

  Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Deze functionaliteit vereist gebruik van de Component van de Pagina van versie 2.14.0 of later van de [ Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **Merk Slug**

      * **met voeten treden** - Controle om de merkschuine streep op deze pagina te bepalen.
         * De waarde wordt geërft door om het even welke kindpagina&#39;s tenzij zij ook hun **vastgestelde waarden van de Overschrijving** hebben.
      * **waarde van de Overschrijving** - de tekst van de merkschuine streep die aan de paginatitel moet worden toegevoegd.
         * De waarde wordt toegevoegd aan de paginatitel na een pipe-teken, zoals &quot;Cycling Tuscany&quot; | Altijd klaar voor de WKND&quot;

* **identiteitskaart van de HTML**

   * **identiteitskaart** - identiteitskaart van HTML om op de component van toepassing te zijn.

* **Meer Titels en Beschrijving**

   * **Titel van de Pagina** - een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Als leeg, wordt de **Titel** gebruikt.
   * **Titel van de Navigatie** - U kunt een afzonderlijke titel voor gebruik in de navigatie (bijvoorbeeld, specificeren als u iets beknopter wilt). Als leeg, wordt de **Titel** gebruikt.
   * **Titel** - een ondertitel voor gebruik op de pagina.
   * **Beschrijving** - Uw beschrijving van de pagina, zijn doel, of een andere details u wilt toevoegen.

* **Aan/uit Tijd**

  >[!NOTE]
  >
  > Zie [ aan en van Tijden - de Configuratie van de Trekker ](/help/operations/replication.md#on-and-off-times-trigger-configuration) voor details van hoe te om de verwante automatische replicatie te vormen.

  >[!NOTE]
  >Als of **op Tijd** of **van Tijd** in het verleden is, en de automatische replicatie wordt gevormd, dan wordt de relevante actie onmiddellijk teweeggebracht.

   * **op Tijd** - de datum en de tijd waarop de gepubliceerde pagina zichtbaar (teruggegeven) op het publicatiemilieu wordt gemaakt. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

      * Als reeds [ gepubliceerd (manueel) ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) deze pagina wordt gehouden slapend (verborgen) tot het teruggeven in de gespecificeerde tijd.
      * Als niet gepubliceerd, en gevormd voor auto-replicatie, wordt de pagina automatisch gepubliceerd, dan teruggegeven, op de gespecificeerde tijd.
      * Als niet gepubliceerd, en niet gevormd voor auto-replicatie, wordt de pagina niet automatisch gepubliceerd, zodat wordt 404 gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.

   * **Van Tijd** - Gelijkaardig aan en vaak gebruikt in combinatie met **op Tijd**, bepaalt dit de tijd waarbij de gepubliceerde pagina op het publicatiemilieu wordt verborgen.

   * Verlaat deze gebieden (**op Tijd** en **van Tijd**) leeg voor pagina&#39;s u onmiddellijk wilt publiceren en beschikbaar op publiceer milieu hebben tot zij (het normale scenario) worden gedeactiveerd.

* **Vanity URL**

   * Hiermee kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of meer expressieve URL kunt gebruiken.
   * Als de URL vanity bijvoorbeeld is ingesteld op `welcome` op de pagina die wordt aangegeven door het pad `/v1.0/startpage` voor de website `http://example.com` , is `http://example.com/welcome` de URL van de vanity van `http://example.com/content/v1.0/startpage` .

  >[!CAUTION]
  >
  >Vanity-URL&#39;s:
  >
  >* Dit moet uniek zijn, dus zorg ervoor dat de waarde niet al door een andere pagina wordt gebruikt.
  >* Geen ondersteuning voor regex-patronen.
  >* Deze mag niet op een bestaande pagina worden ingesteld.

   * **voeg** toe - Uitgezocht om een gebied te tonen om een ijdelheid URL voor de pagina te bepalen.
      * Selecteer nogmaals om meerdere items toe te voegen.
      * Selecteer **verwijder** pictogram om ijdelheid URL te schrappen.
   * **Redirect Vanity URL** - wijst erop of u de pagina de ijdelheid URL wilt gebruiken.

### Geavanceerd {#advanced}

* **Montages**

   * **Taal** - de paginataal
   * **Wortel van de Taal** - moet worden gecontroleerd als de pagina de wortel van een taalexemplaar is
   * **opnieuw richt** - wijst op de pagina waaraan deze pagina automatisch met een HTML `302 Found` status zou moeten opnieuw richten.
      * **Permanent opnieuw richten** - wanneer gecontroleerd, richt de pagina aan de doelweg die samen met een HTML `301 Moved Permanently` status wordt verstrekt.
   * **Ontwerp** - wijst erop of de pagina in de paginanavigatie van de resulterende plaats wordt getoond of verborgen
   * **Alias** - specificeert een alias die met deze pagina moet worden gebruikt
      * Als u bijvoorbeeld een alias van `private` voor de pagina `/content/wknd/us/en/magazine/members-only` definieert, kunt u deze pagina ook openen via `/content/wknd/us/en/magazine/private`
      * Als u een alias maakt, wordt de eigenschap `sling:alias` op het paginaknooppunt ingesteld. Dit heeft alleen invloed op de bron, niet op het pad naar de opslagplaats.
      * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [ de opties van Publish ](/help/sites-cloud/authoring/sites-console/publishing-pages.md) in de redacteur zijn slechts beschikbaar voor pagina&#39;s die via hun daadwerkelijke wegen worden betreden.
      * Zie [ Gelokaliseerde paginanamen onder SEO en de Beste praktijken van het Beheer URL ](/help/overview/seo-and-url-management.md#localized-page-names).

* **Configuratie**

   * **Geërft van &lt;path>** - laat/maak overerving toe onbruikbaar; knevels beschikbaarheid van **de Configuratie van de Wolk** voor selectie

   * **Configuratie van de Wolk** - de weg aan de geselecteerde configuratie

* **Montages van het Malplaatje**

   * **Toegestane Malplaatjes** - [ bepaalt de lijst van malplaatjes die ](/help/sites-cloud/authoring/sites-console/templates.md#enabling-and-allowing-a-template-template-author) binnen deze subtak beschikbaar zijn

* **Vereiste van de Authentificatie**

   * **laat** toe - laat gebruik van authentificatie toe om tot de pagina toegang te hebben

     >[!NOTE]
     >
     >De gesloten gebruikersgroepen voor de pagina worden bepaald op de **[Toestemmingen](#permissions)** tabel.

   * **Login Pagina** - de pagina die voor login moet worden gebruikt

* **Uitvoer**

   * **de Configuratie van de Uitvoer** - specificeert een de uitvoerconfiguratie

* **SEO**

   * **Canonical Url** - kan worden gebruikt om canonical Url van de pagina te beschrijven; als verlaten leeg is is URL van de pagina zijn canonical Url

   * **Codes Robots** - selecteer de robots markeringen om het gedrag van de kruipende zoekmachine te controleren.

     >[!NOTE]
     >
     >Sommige opties veroorzaken een conflict met elkaar. In geval van een conflict krijgt de meer permissieve optie voorrang.

   * **produceer Sitemap** - wanneer geselecteerd, wordt sitemap.xml geproduceerd voor deze pagina, en zijn nakomelingen

### Afbeeldingen {#images}

* **Aanbevolen Beeld**

  Selecteer en configureer de afbeelding die u wilt weergeven. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

   * **Beeld**

     U kunt **een Activa kiezen**, of voor een dossier doorbladeren om te uploaden, dan **uitgeven**, of **Duidelijk**.

   * **Alternatieve Tekst** - een tekst die wordt gebruikt om de betekenis en/of functie van het beeld te vertegenwoordigen; bijvoorbeeld, voor gebruik door het schermlezers.

   * **erven - Waarde die van de activa DAM** wordt genomen - wanneer gecontroleerd zal dit de alternatieve tekst met de waarde van de `dc:description` meta-gegevens in DAM bevolken

* **Duimnagel**

  De paginaminiatuur configureren

   * **produceer Voorproef** - produceer een voorproef van de pagina om als duimnagel te gebruiken
   * **upload Beeld** - upload een beeld om als duimnagel te gebruiken
   * **Uitgezochte Beeld** - selecteer een bestaand Middel om als duimnagel te gebruiken
   * **terugkeren** - deze optie wordt beschikbaar nadat u een verandering in de duimnagel hebt aangebracht. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Cloud Servicen {#cloud-services}

* **Configuraties van de Cloud Service** - bepaal eigenschappen voor de clouddiensten

### Personalization {#personalization}

* **Configuraties ContextHub**

   * **Geërft van &lt;path>** - laat/maak overerving toe onbruikbaar; knevels beschikbaarheid van **Het Weg van ContextHub** en **Weg van Segmenten** voor selectie

   * **ContextHub Weg** - bepaal de [ configuratie ContextHub ](/help/sites-cloud/authoring/personalization/contexthub.md)
   * **Weg van Segmenten** - bepaal de [ weg van Segmenten ](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)

* **richtend Configuratie**

   * **Merk** - bepaalt a [ Merk om een werkingsgebied te specificeren voor het richten ](/help/sites-cloud/authoring/personalization/targeted-content.md).

  >[!NOTE]
  >Deze optie vereist de gebruikersrekening om in de `Target Administrators` groep te zijn.

### Machtigingen {#permissions}

* **Toestemmingen**

   * **voeg Toestemmingen** toe
   * **geeft Gesloten Groep van de Gebruiker uit**
   * Bekijk de **Effectieve Toestemmingen**

### Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren. De blauwdrukken dienen als basis voor Levende Kopieën, en maken deel uit van [ Multisite Beheer van de Plaats ](/help/sites-cloud/administering/msm/overview.md).

* **Huidige Levende Kopieën** - Lijsten pagina&#39;s die op (namelijk zijn Levende Kopieën van) deze blauwdrukpagina gebaseerd zijn

* **Rollout vormt** - controleert de omstandigheden waaronder de wijzigingen aan het Levende Exemplaar worden verspreid

### Live kopie {#live-copy}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die zijn geconfigureerd als live kopieën. Zoals met Vervagen, maken de Levende Kopieën deel uit van [ Beheer van de MultiPlaats ](/help/sites-cloud/administering/msm/overview.md).

* **synchroniseer** - synchroniseer Levende Exemplaar met Vervaging, die lokale wijzigingen houden
* **Teruggestelde** - het Levende Exemplaar van het Terugstellen aan staat van Vervaging, verwijderend lokale aanpassingen
* **Opschorting** - onderbreek Levend Exemplaar van verdere rollout wijzigingen
* **losmaken** - loskoppel Levend Exemplaar van Vervaging

* **Source**

   * Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

* **Status**

   * Hiermee geeft u de huidige status van Live kopie van de pagina weer

* **Configuratie**

   * **Levende Overerving van het Exemplaar** - als gecontroleerd, is de Levende configuratie van het Exemplaar efficiënt op alle kinderen
   * **erven de Vormen van de Output van de Ouder** - als gecontroleerd, wordt de rollout configuratie geërft van de ouder van de pagina
   * **kies Configuratie van de Uitvoer** - bepaalt de omstandigheden waaronder de wijzigingen van het Vervagen en slechts beschikbaar worden verspreid wanneer **Inherit de Vorm van de Uitvoer van Bovenliggend** niet wordt geselecteerd

### Voorvertoning {#preview}

Wanneer een omgeving van de Voorproef wordt toegelaten, ziet u het volgende:

* Voorbeeld-URL - de URL die wordt gebruikt voor toegang tot de inhoud in de voorvertoningsomgeving

### Progressieve webtoepassing {#progressive-web-app}

Dankzij een eenvoudige configuratie kan een auteur van inhoud nu functies (PWA) voor progressieve webtoepassingen inschakelen voor ervaringen die zijn gemaakt in AEM Sites.

>[!NOTE]
>
>Zie [ toelatend de Progressieve Eigenschappen van de App van het Web ](/help/sites-cloud/authoring/sites-console/enable-pwa.md).

* **vorm installeerbare ervaring**

   * **laat PWA** toe - laat/maak de eigenschap toe onbruikbaar; staat gebruikers toe om de plaats als PWA te installeren
   * **StartupURL** - de aangewezen opstartenURL
   * **Wijze van de Vertoning** - hoe browser zou moeten worden verborgen of anders aan de gebruiker op het lokale apparaat worden voorgesteld
   * **de richtlijn van het Scherm** - hoe PWA apparatenrichtingen zal behandelen
   * **kleur van het Thema** - de kleur van app die beïnvloedt hoe het werkende systeem van de lokale gebruiker de inheemse toolbar UI en navigatiecontroles toont
   * **Achtergrondkleur** - de achtergrondkleur van app, die wordt getoond aangezien app laadt
   * **Pictogram** - het pictogram dat app op het apparaat van de gebruiker vertegenwoordigt

* **(Geavanceerd) het beheer van het Geheime voorgeheugen**

   * **Caching strategie en frequentie van inhoud verfrissen zich** - bepaalt het caching model voor uw PWA
   * **Dossiers aan geheime voorgeheugen voor off-line gebruik**
      * **Dossier pre-caching (technische voorproef)** - de dossiers op AEM worden ontvangen worden bewaard aan het lokale browser geheime voorgeheugen wanneer de de dienstarbeider installeert en alvorens het wordt gebruikt
      * **Client-side Bibliotheken** - cliënt-zijbibliotheken om voor off-line ervaring in het voorgeheugen op te slaan
      * **de uitbreidingen van de Weg** - de netwerkverzoeken voor de bepaalde wegen worden onderschept en de caching inhoud is teruggekeerd in overeenstemming met de gevormde Caching strategie en de frequentie van inhoud verfrissen zich
      * **de uitsluitingen van de Weg** - deze dossiers zullen nooit in het voorgeheugen ondergebracht worden ongeacht de montages onder Dossier pre-caching en de opneming van de Weg

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

* Van de **console van Plaatsen**:
   * [ Creërend een nieuwe pagina ](/help/sites-cloud/authoring/sites-console/creating-pages.md#creating-a-new-page) (een ondergroep van de eigenschappen)
   * Het klikken of het tappen **Eigenschappen**
      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)
* Vanuit de pagina-editor:
   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Het klikken of het tappen **Eigenschappen** om de pagina eigenschappen te bepalen:

1. Gebruikend de **console van Plaatsen**, navigeer aan de plaats van de pagina waarvoor u eigenschappen bekijken en wilt uitgeven.
1. Selecteer de **optie van Eigenschappen** voor de vereiste pagina die of gebruikt:
   * [Snelle acties](/help/sites-cloud/authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-cloud/authoring/basic-handling.md#selecting-resources)
   * De pagina-eigenschappen worden weergegeven met de juiste tabbladen.
1. Bekijk of bewerk de eigenschappen naar wens.
1. Dan gebruik **sparen** om uw updates te bewaren die door **worden gevolgd dicht** om aan de console terug te keren.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer het uitgeven van een pagina kunt u **Informatie van de Pagina** gebruiken om de paginaeigenschappen te bepalen:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.
1. Selecteer het **pictogram van de Informatie van de Pagina** om het selectiemenu te openen:
1. Selecteer **Open Eigenschappen** en een dialoogdoos opent die u de eigenschappen laat uitgeven, die door het aangewezen lusje worden gesorteerd. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:
   * **annuleert**
   * **sparen &amp; Sluiten**
1. Gebruik **sparen &amp; sluit** knoop om de veranderingen te bewaren.

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Vanuit de **Sites**-console kunt u meerdere pagina&#39;s selecteren en vervolgens **Eigenschappen weergeven** gebruiken om de pagina-eigenschappen te bekijken en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer het doorbladeren van de **console van Plaatsen**
* Na het gebruiken van **Onderzoek** om van een reeks pagina&#39;s de plaats te bepalen

Na het selecteren van de pagina&#39;s en dan het klikken of het tikken van de **optie van Eigenschappen**, worden de bulkeigenschappen getoond:

![ Bulk het uitgeven paginaeigenschappen ](/help/sites-cloud/authoring/assets/page-properties-bulk-edit.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy
   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u:

* **Mening**

   * Een lijst met de betrokken pagina&#39;s
      * U kunt desgewenst selecteren of deselecteren
      * Tabs
         * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.
   * Een subset van eigenschappen
      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.
   * Algemene eigenschappen met een gemeenschappelijke waarde
      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Wanneer het gebied multi-waarde (bijvoorbeeld, Markeringen) is, zullen de waarden slechts worden getoond wanneer *allen* gemeenschappelijk zijn. Als slechts enkele van de algemene voorbeelden worden weergegeven, worden deze alleen weergegeven tijdens het bewerken.
      * Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **geeft** uit

   * U kunt de waarden in de beschikbare velden bijwerken.
      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed** selecteert.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.
   * Velden die veel voorkomen, maar die verschillende waarden hebben op de verschillende pagina&#39;s, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>` .
