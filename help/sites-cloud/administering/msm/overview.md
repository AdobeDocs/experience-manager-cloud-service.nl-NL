---
title: Inhoud opnieuw gebruiken - Beheer van meerdere sites en Live kopiëren
description: Maak kennis met de introductie van het hergebruik van inhoud met AEM krachtige functies Live Copy en Multi Site Manager.
feature: Multi Site Manager
role: Admin
exl-id: 22b4041f-1df9-4189-8a09-cbc0c89fbf2e
source-git-commit: 0a4f9edba00e65439a306024c604e6935c8bac47
workflow-type: tm+mt
source-wordcount: '2721'
ht-degree: 0%

---

# Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren {#multi-site-manager-and-live-copy}

Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken. MSM gebruikt hiervoor de Live Copy-functionaliteit.

* Met MSM kunt u:
   * Inhoud eenmaal maken en vervolgens
   * Deze inhoud opnieuw gebruiken in andere gebieden (via [Actieve kopieën](#live-copies)) van dezelfde of andere sites.
* MSM onderhoudt dan de levende verhoudingen tussen uw broninhoud en zijn Levende Kopieën zodat:
   * Wanneer u de broninhoud wijzigt, worden de bron en Live kopieën gesynchroniseerd.
   * U kunt alleen de inhoud van de actieve kopieën aanpassen door de live relatie voor afzonderlijke subpagina&#39;s en/of componenten te verbreken.

Deze pagina biedt een overzicht van het hergebruiken van inhoud met MSM. Op de volgende pagina&#39;s worden verwante kwesties uitgebreid besproken.

* [Actieve kopieën maken en synchroniseren](creating-live-copies.md)
* [Console voor live kopiëren](live-copy-overview.md)
* [Synchronisatie van actieve kopie configureren](live-copy-sync-config.md)
* [Conflicten MSM-rollout](rollout-conflicts.md)
* [Aanbevolen MSM-procedures](best-practices.md)

>[!NOTE]
>
>MSM kan ook voor Activa, met inbegrip van Inhoudsfragmenten worden gebruikt. Zie [Inhoudsfragmenten opnieuw gebruiken met MSM voor elementen](/help/assets/reuse-assets-using-msm.md) (alleen beschikbaar via de middelenconsole).

## Mogelijke scenario&#39;s {#possible-scenarios}

Er zijn vele gebruiksgevallen voor MSM en Levende Exemplaren. Enkele scenario&#39;s zijn:

* **Multinationals - wereldwijd tot lokaal bedrijf**

  Een typisch gebruiksgeval dat MSM steunt is inhoud in verscheidene multinationale plaatsen van het zelfde-Taal opnieuw te gebruiken. Hierdoor kan de kerninhoud opnieuw worden gebruikt en kunnen nationale variaties worden toegestaan.

  Bijvoorbeeld de Engelse sectie van het [WKND-lesbestand](/help/implementing/developing/introduction/develop-wknd-tutorial.md) is opgericht voor klanten in de VS. De meeste inhoud op deze site kan ook worden gebruikt voor andere WKND-sites die geschikt zijn voor Engelstalige klanten van verschillende landen en culturen. De kerninhoud blijft voor alle sites hetzelfde, terwijl regionale aanpassingen kunnen worden aangebracht.

  De volgende structuur kan voor plaatsen voor de Verenigde Staten en Canada worden gebruikt. Let op: `language-masters` de knoop handhaaft het hoofdexemplaar van niet alleen Engels maar andere taalinhoud. Deze inhoud kan worden gebruikt als basis voor aanvullende regionale taalinhoud naast het Engels.

  ```xml
  /content
      |- wknd
          |- language-masters
              |- en
              |- es
              |- fr
          |- us
              |- en
              |- es
          |- ca
              |- en
              |- fr
  ```

  >[!NOTE]
  >
  >MSM vertaalt de inhoud niet. Het wordt gebruikt om de vereiste structuur tot stand te brengen en de inhoud op te stellen.
  >
  >
  >Zie [Inhoud vertalen voor meertalige sites](/help/sites-cloud/administering/translation/overview.md) voor een dergelijk voorbeeld.

* **Nationaal — Hoofdkantoor van regionale afdelingen**

  Een onderneming met een netwerk van dealers zou ook aparte websites willen voor haar afzonderlijke dealers, die elk een variant zijn van de hoofdsite die door het hoofdkantoor wordt aangeboden. Dit kan het geval zijn voor één enkele onderneming met meerdere regionale kantoren, of voor een nationaal franchisesysteem dat bestaat uit een centrale franchisegever en meerdere lokale franchisehouders.

  Het hoofdkantoor kan de kerninformatie verstrekken, terwijl de regionale entiteiten lokale informatie kunnen toevoegen, zoals contactgegevens, openingstijden en evenementen.

  ```xml
  /content
      |- head-office-berlin
      |- branch-hamburg
      |- branch-stuttgart
      |- branch-munich
      |- branch-frankfurt
  ```

* **Meerdere versies**

  MSM kan versies van een specifieke subtak tot stand brengen. Een subsite voor ondersteuning kan bijvoorbeeld details bevatten over de verschillende versies van een specifiek product, waarbij de basisinformatie constant blijft en alleen de bijgewerkte functies moeten worden gewijzigd:

  ```xml
  /content
      |- game-support
          |- polybius
              |- v5.0
              |- v4.0
              |- v3.0
              |- v2.0
              |- v1.0
  ```

  >[!TIP]
  >
  >In een dergelijk geval gaat het om de vraag of er een eenvoudige kopie moet worden gemaakt of dat er gebruik moet worden gemaakt van Actieve kopieën, wat een evenwicht is tussen:
  >
  >* Hoeveel van de kerninhoud moet worden bijgewerkt in meerdere versies.
  >
  >Tegen:
  >
  >* Hoeveel van de afzonderlijke kopieën moeten worden aangepast.

## MSM van UI {#msm-from-the-ui}

MSM is direct toegankelijk in UI gebruikend diverse opties van de aangewezen console.

* **Site maken** (**Sites**)

   * Met MSM kunt u meerdere websites beheren die gemeenschappelijke inhoud delen. Websites worden bijvoorbeeld vaak aangeboden voor een internationaal publiek, zodat de meeste inhoud in alle landen hetzelfde is, met een subset van de inhoud die specifiek is voor het afzonderlijke land. Met MSM kunt u [Actieve kopieën maken die automatisch een of meer sites bijwerken op basis van uw bronsite](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dit helpt u ook om een gemeenschappelijke basisstructuur af te dwingen, de gemeenschappelijke inhoud over de veelvoudige plaatsen te gebruiken, een gemeenschappelijke blik te handhaven en zich te concentreren inspanningen op het beheren van de inhoud die eigenlijk tussen de plaatsen verschilt. Een site maken op deze manier:
      * Vereist een vooraf bepaalde blauwdrukconfiguratie om de bron te specificeren.
      * Hiermee maakt u een live kopie van de (vooraf gedefinieerde) bron.
      * Biedt de gebruiker de **Uitrol** knop.

* **Live kopie maken** (**Sites**)

   * Met MSM kunt u [Maak een ad-hoc (eenmalige) live kopie van een afzonderlijke pagina of subvertakking van een website.](creating-live-copies.md#creating-a-live-copy-of-a-page) Bijvoorbeeld, het dupliceren van een subtak om informatie over een nieuwe/bijgewerkte versie van een product te verstrekken. Op deze manier een actieve kopie maken:
      * Hiermee maakt u een ad-hoc live kopie (geen configuratie voor blauwdrukken vereist).
      * Kan worden gebruikt om (direct) een actieve kopie van elke pagina of vertakking te maken.
      * Vereisten **Synchroniseren** (geen **Uitrol** ).

* **Eigenschappen weergeven** (**Sites**)

   * Deze optie helpt u, indien van toepassing [Live kopie controleren](creating-live-copies.md#monitoring-your-live-copy) door informatie te verstrekken over de **Live kopie** of **Blauwdruk**.

* **Verwijzingen** (**Sites**)

   * De [Verwijzingen](/help/sites-cloud/authoring/basic-handling.md#references) spoor verstrekt informatie **Actieve kopieën** en toegang tot passende maatregelen.

* **Overzicht van live kopiëren** (**Sites**)

   * Met deze console kunt u [bekijk en beheer uw blauwdruk en de bijbehorende Actieve exemplaren.](live-copy-overview.md)

* **Blauwdrukken** (**Gereedschappen** - **Sites**)

   * Met deze console kunt u [maak en beheer uw blauwdrukconfiguraties.](creating-live-copies.md#creating-a-blueprint-configuration)

>[!NOTE]
>
>MSM kan worden gebruikt met zowel pagina&#39;s als [Ervaar fragmenten](/help/sites-cloud/authoring/fragments/experience-fragments.md) aangezien deze fragmenten onderdeel zijn van een ervaring (pagina).

>[!NOTE]
>
>De aspecten van de functionaliteit MSM worden gebruikt in verscheidene andere AEM eigenschappen zoals Lanceringen. In deze gevallen wordt de live kopie beheerd door die functie.

### Gebruikte termen {#terms-used}

Als inleiding, verstrekt de volgende lijst een overzicht van de belangrijkste termen die met MSM worden gebruikt. Deze worden in de volgende secties en pagina&#39;s nader beschreven.

| Term | Definitie | Meer details |
|---|---|---|
| Bron | De originele pagina&#39;s die als basis voor Actieve exemplaren worden gebruikt | Gelijk aan blauwdrukken en/of blauwdrukken |
| Live kopie | De kopie (van de bron), onderhouden door synchronisatiehandelingen zoals gedefinieerd door de rollout-configuraties |  |
| Configuratie van live kopiëren | Definitie van de configuratiedetails voor een Live Copy |  |
| Live relatie | Effectieve definitie van de overerving voor een bepaalde bron, namelijk de verbinding(en) tussen de bron en actieve kopieën | Hiermee zorgt u ervoor dat wijzigingen in de bron kunnen worden gesynchroniseerd met Live Copy |
| Blauwdruk | Gelijk aan bron | Kan worden gedefinieerd door een configuratie van een blauwdruk |
| Blauwdrukconfiguratie | Vooraf gedefinieerde configuratie die een bronpad opgeeft | Wanneer in een blauwdrukconfiguratie naar een blauwdrukpagina wordt verwezen, wordt de opdracht Uitrollen beschikbaar |
| Hoofdstuk | De gedeelten van de blauwdruk die moeten worden opgenomen in de actieve kopie | Dit zijn doorgaans subpagina&#39;s van de hoofdmap |
| Synchronisatie | De generische term voor de synchronisatie van inhoud tussen de bron en Live kopieën (door beide **Uitrol** en **Synchroniseren** opties) |  |
| Uitrol | Synchroniseert van bron naar Live kopie | Kan worden geactiveerd door een auteur (op een blauwdrukpagina) of door een systeemgebeurtenis (zoals gedefinieerd door de rollout-configuratie) |
| Rolloutconfiguratie | Regels die bepalen welke eigenschappen worden gesynchroniseerd, hoe en wanneer |  |
| Synchroniseren | Een handmatig verzoek om synchronisatie, uitgevoerd vanaf de Live Copy-pagina&#39;s |  |
| Overerving | Een pagina/component van Actieve kopie overerft de inhoud van de bronpagina/component wanneer de synchronisatie plaatsvindt |  |
| Onderbreken | Hiermee wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina tijdelijk verwijderd |  |
| Loskoppelen | Hiermee wordt de live relatie tussen een Live kopie en de bijbehorende blauwdrukpagina permanent verwijderd |  |
| Herstellen | Een pagina van Live kopie opnieuw instellen om alle annuleringen van overerving te verwijderen en de pagina terug te brengen naar dezelfde status als de bronpagina | Herstellen is van invloed op wijzigingen die u hebt aangebracht in pagina-eigenschappen, het alineasysteem en de componenten. |
| Ondiep | Een actieve kopie van één pagina |  |
| Diep | Een actieve kopie van een pagina, samen met de onderliggende pagina&#39;s ervan |  |

>[!TIP]
>
>Zie [Het beheer van meerdere sites uitbreiden](/help/implementing/developing/extending/msm.md#overview-of-the-java-api) voor de objectnamen.

## Actieve kopieën {#live-copies}

Een live MSM-kopie is een kopie van specifieke site-inhoud waarvoor een live relatie met de oorspronkelijke bron behouden blijft:

* Live kopie neemt de inhoud van de bron over.
* De synchronisatie voert de daadwerkelijke overdracht van inhoud uit wanneer de veranderingen in de bron worden aangebracht.
* Een actieve kopie kan worden beschouwd als:
   * Ondiep: één pagina
   * Diep: de pagina, samen met de onderliggende pagina&#39;s
* De regels van de synchronisatie, genoemd rollout configuraties, bepalen welke eigenschappen worden gesynchroniseerd en wanneer de synchronisatie voorkomt.

In het vorige voorbeeld: `/content/wknd/language-masters/en` is de algemene hoofdsite in het Engels. Als u de inhoud van deze site opnieuw wilt gebruiken, worden live MSM-kopieën gemaakt:

* De onderstaande inhoud `/content/wknd/language-masters/en` is de bron.
* De onderstaande inhoud `/content/wknd/language-masters/en` wordt gekopieerd onder de `/content/wknd/us/en/` en `/content/wknd/ca/en` knooppunten. Dit zijn de actieve kopieën.
* Auteurs wijzigen onderstaande pagina&#39;s `/content/wknd/language-masters/en`.
* Wanneer teweeggebracht, synchroniseert MSM deze veranderingen in Levende Exemplaren.

### Actieve kopieën - Compositie {#live-copies-composition}

>[!NOTE]
>
>De diagrammen en beschrijvingen in deze sectie vertegenwoordigen momentopnamen van potentiële Levende Exemplaren. Ze zijn niet volledig, maar bieden een overzicht om specifieke kenmerken te benadrukken.

Wanneer u voor het eerst een live kopie maakt, worden de geselecteerde bronpagina&#39;s 1:1 weerspiegeld in de live kopie. Hierna kunnen ook nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) rechtstreeks in Live Copy worden gemaakt. Het is daarom nuttig om op de hoogte te zijn van deze variaties en van de invloed die deze hebben op de synchronisatie. Mogelijke composities zijn:

* [Live kopiëren met pagina&#39;s die niet live zijn gekopieerd](#live-copy-with-non-live-copy-pages)
* [Geneste actieve kopieën](#nested-live-copies)

De basisvorm van Live Copy heeft:

* Live Copy-pagina&#39;s die de geselecteerde bronpagina&#39;s op een 1:1-basis weerspiegelen.
* Eén configuratiedefinitie.
* Een live relatie gedefinieerd voor elke resource:
   * Koppel de Live Copy-bron aan de bijbehorende blauwdruk/bron.
   * Wordt gebruikt bij het realiseren van overerving en rollout.

Wijzigingen kunnen [gesynchroniseerd](creating-live-copies.md#synchronizing-your-live-copy) volgens de eisen.

![Samenstellingsoverzicht van live kopiëren](../assets/live-copy-composition.png)

#### Live kopiëren met pagina&#39;s die niet live worden gekopieerd {#live-copy-with-non-live-copy-pages}

Wanneer u een live kopie maakt in AEM, kunt u de vertakking Live kopie zien en door de vertakking Live kopie navigeren en de normale AEM gebruiken in de vertakking Live kopie. Dit betekent dat u (of een proces) nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) kunt maken in Live Copy. Bijvoorbeeld een product voor een bepaald gebied of land.

* Dergelijke bronnen hebben geen live relatie met de bron-/blauwdrukpagina&#39;s en zijn niet gesynchroniseerd.
* De scenario&#39;s kunnen voorkomen dat MSM als speciale gevallen behandelt. Wanneer u (of een proces) bijvoorbeeld een pagina maakt met dezelfde positie en naam in de vertakkingen van de bron/blauwdruk en Live kopie. Zie voor dergelijke situaties [Conflicten MSM-rollout](rollout-conflicts.md) voor meer informatie .

![Live kopiëren met niet-live kopiëren pagina&#39;s](../assets/live-copy-with-non-live-copy-pages.png)

#### Geneste actieve kopieën {#nested-live-copies}

Wanneer u (of een proces) een [nieuwe pagina in een bestaande live kopie](#live-copy-with-non-live-copy-pages) Deze nieuwe pagina kan ook worden ingesteld als een live kopie van een andere blauwdruk. Dit wordt een geneste live kopie genoemd. In geneste live kopieën wordt het gedrag van de tweede of binnenste live kopie op de volgende manieren beïnvloed door de eerste of buitenste live kopie:

* Een uitgebreide rollout die wordt geactiveerd voor Live Copy op hoofdniveau, kan worden doorgevoerd in de geneste Live Copy.
* Alle koppelingen tussen de bronnen worden herschreven in Live kopieën.

Koppelingen die bijvoorbeeld van de tweede naar de eerste blauwdruk wijzen, worden herschreven als koppelingen die van de geneste/tweede live kopie naar de eerste live kopie wijzen.

![Geneste actieve kopieën](../assets/live-copy-nested.png)

>[!NOTE]
>
>Als u een pagina verplaatst of de naam ervan wijzigt in de vertakking Live kopie, wordt deze behandeld als een geneste Live kopie zodat AEM de relaties kan bijhouden.

#### Gestapelde actieve kopieën {#stacked-live-copies}

Een actieve kopie wordt een gestapelde live kopie genoemd wanneer deze wordt gemaakt als het onderliggende element van een ondiepe Live kopie. Het gedraagt zich op dezelfde manier als [geneste live kopie](#nested-live-copies).

### Bron-, blauwdruk- en blauwdrukconfiguraties {#source-blueprints-and-blueprint-configurations}

Elke pagina of elke vertakking met pagina&#39;s kan worden gebruikt als bron van een Live kopie. Nochtans, MSM laat u ook een blauwdrukconfiguratie bepalen die een bronweg specificeert. De voordelen van het gebruik van een blauwdrukconfiguratie zijn dat zij:

* Laat de auteur het **Uitrol** op een blauwdruk. Dit wil zeggen dat er expliciet wijzigingen moeten worden aangebracht in Live kopieën die van deze blauwdruk overerven.
* Laat de auteur gebruiken **Site maken**. Op deze manier kan de gebruiker eenvoudig talen selecteren en de structuur van Live Copy configureren.
* Definieer een standaardconfiguratie voor rollout voor actieve kopieën die een relatie hebben met de blauwdruk.

De bron voor een live kopie kan gewone pagina&#39;s zijn of pagina&#39;s die door een blauwdrukconfiguratie worden omringd. Beide zijn geldige gebruiksgevallen.

De bron vormt de blauwdruk voor Live kopie. De blauwdruk wordt gedefinieerd wanneer u:

* [Een blauwdrukconfiguratie maken](creating-live-copies.md#creating-a-blueprint-configuration) - De configuratie definieert vooraf de pagina&#39;s die moeten worden gebruikt om de Live kopie te maken.
* [Een actieve kopie van een pagina maken](creating-live-copies.md#creating-a-live-copy-of-a-page) - De pagina&#39;s die worden gebruikt voor het maken van Live Copy (de bronpagina&#39;s) zijn de pagina&#39;s met de blauwdruk. Naar de bronpagina kan door een blauwdrukconfiguratie al dan niet worden verwezen.

### Uitvoeren en synchroniseren {#rollout-and-synchronize}

Een rollout is de centrale actie MSM die Levende Kopieën met hun bronnen synchroniseert. U kunt rollouts handmatig uitvoeren of automatisch uitvoeren.

* A [rollout-configuratie](#rollout-configurations) kunnen worden gedefinieerd zodat specifieke [gebeurtenissen](live-copy-sync-config.md#rollout-triggers) kan ertoe leiden dat een rollout automatisch voorkomt.
* Wanneer u een pagina met een blauwdruk maakt, kunt u de opdracht **[Uitrol](creating-live-copies.md#rolling-out-a-blueprint)** om wijzigingen door te voeren in Live Copy.
   * De **Uitrol** is beschikbaar op een pagina van de blauwdruk die door een blauwdrukconfiguratie van verwijzingen wordt voorzien.

  ![Uitrol](../assets/live-copy-rollout.png)

* Wanneer u een pagina voor Live kopie maakt, kunt u de opdracht **[Synchroniseren](creating-live-copies.md#synchronizing-a-live-copy)** gebruiken om wijzigingen van de bron naar Live kopie over te brengen.
   * De **Synchroniseren** Deze opdracht is altijd beschikbaar op de pagina Live kopiëren, ongeacht of de bron-/blauwdrukpagina is ingesloten door een blauwdrukconfiguratie.

  ![Synchroniseren](../assets/live-copy-synchronize.png)

### Uitrolconfiguraties {#rollout-configurations}

Een rollout-configuratie bepaalt wanneer en hoe een Live Copy wordt gesynchroniseerd met de broninhoud. Een rollout-configuratie bestaat uit een trigger en een of meer synchronisatiehandelingen:

* **Trigger** - Een trigger is een gebeurtenis die ervoor zorgt dat de synchronisatie van een live actie plaatsvindt, zoals de activering van een bronpagina. MSM bepaalt de trekkers die u kunt gebruiken.
* **Synchronisatiehandelingen** - Er worden synchronisatiehandelingen uitgevoerd op de Live kopie om deze te synchroniseren met de bron. Voorbeelden van handelingen zijn het kopiëren van inhoud, het bestellen van onderliggende knooppunten en het activeren van de pagina Live kopie. MSM biedt diverse synchronisatiehandelingen.

>[!NOTE]
>
>U kunt aangepaste handelingen voor uw instantie maken met de Java API.

De configuraties van de rollout kunnen worden opnieuw gebruikt, zodat meer dan één Levend Exemplaar de zelfde rollout configuratie kan gebruiken. Meerdere [rollout-configuraties](live-copy-sync-config.md#installed-rollout-configurations) zijn opgenomen in een standaardinstallatie.

### Conflicten bij rollout {#rollout-conflicts}

Rollouts kunnen ingewikkeld worden, vooral wanneer auteurs inhoud in zowel de bron als Live kopie bewerken. Het is dus handig om te weten hoe AEM omgaat met [conflicten die kunnen optreden tijdens rollout.](rollout-conflicts.md)

### Overerving en synchronisatie opschorten en annuleren {#suspending-and-cancelling-inheritance-and-synchronization}

Elke pagina en component in een live kopie is via een live relatie gekoppeld aan de bronpagina en -component ervan. De live relatie configureert de synchronisatie van Live Copy-inhoud van de bron.

U kunt **Onderbreken** de overerving van Live kopie voor een pagina van Live kopie, zodat u pagina-eigenschappen en -componenten kunt wijzigen. Wanneer u overerving onderbreekt, worden de pagina-eigenschappen en -componenten niet meer gesynchroniseerd met de bron.

Wanneer auteurs een afzonderlijke pagina bewerken, kunnen ze **Overerving annuleren** voor een component. Wanneer de overerving wordt geannuleerd, wordt de live relatie onderbroken en vindt de synchronisatie niet plaats voor die component. Het annuleren van overerving en synchronisatie is handig wanneer subsecties van de inhoud moeten worden aangepast.

### Een actieve kopie ontkoppelen {#detaching-a-live-copy}

U kunt [Een actieve kopie loskoppelen](creating-live-copies.md#detaching-a-live-copy) van zijn blauwdruk om alle verbindingen te verwijderen.

>[!CAUTION]
>
>De handeling Loskoppelen is permanent en niet-omkeerbaar.

Met de handeling Loskoppelen wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina permanent verwijderd. Alle MSM-relevante eigenschappen worden verwijderd uit Live Copy en de Live Copy-pagina&#39;s worden een zelfstandige kopie.

>[!TIP]
>
>Zie [Een actieve kopie ontkoppelen](creating-live-copies.md#detaching-a-live-copy) voor volledige informatie, met inbegrip van de gevolgen voor subpagina&#39;s en bovenliggende pagina&#39;s.

## Standaardstappen voor het gebruik van MSM {#standard-steps-for-using-msm}

De volgende stappen beschrijven de standaardprocedure voor het gebruiken van MSM om inhoud opnieuw te gebruiken en veranderingen in Levende Exemplaren te synchroniseren.

1. De inhoud van de bronsite ontwikkelen.
1. Bepaal de rollout configuratie aan gebruik.

   1. MSM [installeert verscheidene rollout configuraties](live-copy-sync-config.md#installed-rollout-configurations) die aan verschillende gebruiksgevallen kunnen voldoen.
   1. U kunt desgewenst [een rollout-configuratie maken](live-copy-sync-config.md#creating-a-rollout-configuration) indien nodig.

1. Bepaal waar u wilt [Geef de rollout-configuraties op die u wilt gebruiken](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) en configureren naar wens.
1. Indien nodig [een blauwdrukconfiguratie maken](creating-live-copies.md#creating-a-blueprint-configuration) waarmee de broninhoud van de actieve kopie wordt geïdentificeerd.
1. [Maak een actieve kopie.](creating-live-copies.md#creating-a-live-copy)
1. Breng de gewenste wijzigingen aan in de broninhoud. U dient het normale proces voor het beoordelen en goedkeuren van inhoud dat uw organisatie heeft ingesteld, te gebruiken.
1. [Uitrollen](creating-live-copies.md#rolling-out-a-blueprint) de blauwdruk, of [Live kopie synchroniseren](creating-live-copies.md#synchronizing-a-live-copy) met de wijzigingen.

## MSM aanpassen {#customizing-msm}

MSM verstrekt hulpmiddelen zodat uw implementatie aan de uitzonderlijke ingewikkeldheid kan aanpassen die wanneer het delen van inhoud kan bestaan.

* **Aangepaste implementatieconfiguraties** - [Een rollout-configuratie maken](live-copy-sync-config.md#creating-a-rollout-configuration) als de geïnstalleerde implementatieconfiguraties niet aan uw vereisten voldoen. U kunt elke beschikbare uitrolltrigger- en synchronisatiehandeling gebruiken.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## Aanbevolen procedures {#best-practices}

De [Aanbevolen MSM-procedures](best-practices.md) Deze pagina bevat belangrijke informatie over uw implementatie.
