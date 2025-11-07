---
title: Inhoud opnieuw gebruiken - Beheer van meerdere sites en Live kopiëren
description: Ontdek een introductie over het hergebruik van inhoud met AEM-functies voor krachtige live kopieën en beheer van meerdere sites.
feature: Multi Site Manager
role: Admin
exl-id: 22b4041f-1df9-4189-8a09-cbc0c89fbf2e
solution: Experience Manager Sites
source-git-commit: 2e257634313d3097db770211fe635b348ffb36cf
workflow-type: tm+mt
source-wordcount: '2719'
ht-degree: 0%

---

# Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren {#multi-site-manager-and-live-copy}

Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken. MSM gebruikt hiervoor de Live Copy-functionaliteit.

* Met MSM kunt u:
   * Inhoud eenmaal maken en vervolgens
   * Hergebruik deze inhoud op andere gebieden (via [ Levende Exemplaren ](#live-copies)) van de zelfde of andere plaatsen.
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
>MSM kan ook voor Assets, met inbegrip van Inhoudsfragmenten worden gebruikt. Zie [ de Fragmenten van de Inhoud van het Hergebruik gebruikend MSM voor Assets ](/help/assets/reuse-assets-using-msm.md) (slechts beschikbaar door de console van Assets).

## Mogelijke scenario&#39;s {#possible-scenarios}

Er zijn vele gebruiksgevallen voor MSM en Levende Exemplaren. Enkele scenario&#39;s zijn:

* **Multinationals - Globaal aan Lokaal Bedrijf**

  Een typisch gebruiksgeval dat MSM steunt is inhoud in verscheidene multinationale plaatsen van het zelfde-Taal opnieuw te gebruiken. Hierdoor kan de kerninhoud opnieuw worden gebruikt en kunnen nationale variaties worden toegestaan.

  Bijvoorbeeld, wordt de Engelse sectie van de [ WKND tutorial steekproef ](/help/implementing/developing/introduction/develop-wknd-tutorial.md) gecreeerd voor klanten in de V.S. De meeste inhoud op deze site kan ook worden gebruikt voor andere WKND-sites die geschikt zijn voor Engelstalige klanten van verschillende landen en culturen. De kerninhoud blijft voor alle sites hetzelfde, terwijl regionale aanpassingen kunnen worden aangebracht.

  De volgende structuur kan voor plaatsen voor de Verenigde Staten en Canada worden gebruikt. Opmerking: het knooppunt `language-masters` behoudt de hoofdkopie van niet alleen de Engelse maar ook de andere taalinhoud. Deze inhoud kan worden gebruikt als basis voor aanvullende regionale taalinhoud naast het Engels.

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
  >Zie [ Vertaal Inhoud voor Meertalige Plaatsen ](/help/sites-cloud/administering/translation/overview.md) voor zulk een voorbeeld.

* **Nationaal - HoofdBureau aan Regionale Troepen**

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

* **Veelvoudige Versies**

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

* **creeer Plaats** (**Plaatsen**)

   * Met MSM kunt u meerdere websites beheren die gemeenschappelijke inhoud delen. Websites worden bijvoorbeeld vaak aangeboden voor een internationaal publiek, zodat de meeste inhoud in alle landen hetzelfde is, met een subset van de inhoud die specifiek is voor het afzonderlijke land. MSM laat u [ Levende Kopieën tot stand brengen die automatisch één of meerdere plaatsen bijwerken die op uw bronplaats ](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) worden gebaseerd. Dit helpt u ook om een gemeenschappelijke basisstructuur af te dwingen, de gemeenschappelijke inhoud over de veelvoudige plaatsen te gebruiken, een gemeenschappelijke blik te handhaven en zich te concentreren inspanningen op het beheren van de inhoud die eigenlijk tussen de plaatsen verschilt. Een site maken op deze manier:
      * Vereist een vooraf bepaalde blauwdrukconfiguratie om de bron te specificeren.
      * Hiermee maakt u een live kopie van de (vooraf gedefinieerde) bron.
      * Verstrekt de gebruiker van de **knoop van de Uitvoer**.

* **creeer Levend Exemplaar** (**Plaatsen**)

   * MSM laat u [ tot een ad hoc (eenmalig) Levend Exemplaar van een individuele pagina of subtak van een website ](creating-live-copies.md#creating-a-live-copy-of-a-page) leiden. Bijvoorbeeld, het dupliceren van een subtak om informatie over een nieuwe/bijgewerkte versie van een product te verstrekken. Op deze manier een actieve kopie maken:
      * Hiermee maakt u een ad-hoc live kopie (geen configuratie voor blauwdrukken vereist).
      * Kan worden gebruikt om (direct) een actieve kopie van elke pagina of vertakking te maken.
      * Vereist **Synchroniseer** (verstrekt niet de **knoop van de Uitvoer**).

* **Eigenschappen van de Mening** (**Plaatsen**)

   * Waar aangewezen, helpt deze optie u [ uw Levende Exemplaar ](creating-live-copies.md#monitoring-your-live-copy) controleren door informatie over het verwante **Levende Exemplaar** of **Vervaging** te verstrekken.

* **Verwijzingen** (**Plaatsen**)

   * Het [ spoor van Verwijzingen ](/help/sites-cloud/authoring/basic-handling.md#references) verstrekt informatie over **Levende Exemplaren** samen met toegang tot aangewezen acties.

* **Levend Overzicht van het Exemplaar** (**Plaatsen**)

   * Deze console laat u [ bekijken en uw blauwdruk en zijn Levende Exemplaren ](live-copy-overview.md) beheren.

* **Blauwdrukken** (**Hulpmiddelen** - **Plaatsen**)

   * Deze console laat u [ uw configuraties van de blauwdruk ](creating-live-copies.md#creating-a-blueprint-configuration) tot stand brengen en beheren.

>[!NOTE]
>
>MSM kan met zowel pagina&#39;s als [ de Fragmenten van de Ervaring ](/help/sites-cloud/authoring/fragments/experience-fragments.md) worden gebruikt aangezien deze fragmenten deel van een ervaring (pagina) uitmaken.

>[!NOTE]
>
>Aspecten van de functionaliteit MSM worden gebruikt in verscheidene andere eigenschappen van AEM zoals Lanceringen. In deze gevallen wordt de live kopie beheerd door die functie.

### Gebruikte termen {#terms-used}

Als inleiding, verstrekt de volgende lijst een overzicht van de belangrijkste termen die met MSM worden gebruikt. Deze worden in de volgende secties en pagina&#39;s nader beschreven.

| Term | Definitie | Meer details |
|---|---|---|
| Source | De originele pagina&#39;s die als basis voor Actieve exemplaren worden gebruikt | Gelijk aan blauwdrukken en/of blauwdrukken |
| Live kopie | De kopie (van de bron), onderhouden door synchronisatiehandelingen zoals gedefinieerd door de rollout-configuraties |  |
| Configuratie van live kopiëren | Definitie van de configuratiedetails voor een Live Copy |  |
| Live relatie | Effectieve definitie van de overerving voor een bepaalde bron, namelijk de verbinding(en) tussen de bron en actieve kopieën | Hiermee zorgt u ervoor dat wijzigingen in de bron kunnen worden gesynchroniseerd met Live Copy |
| Blauwdruk | Gelijk aan Source | Kan worden gedefinieerd door een configuratie van een blauwdruk |
| Blauwdrukconfiguratie | Vooraf gedefinieerde configuratie die een bronpad opgeeft | Wanneer in een blauwdrukconfiguratie naar een blauwdrukpagina wordt verwezen, wordt de opdracht Uitrollen beschikbaar |
| Hoofdstuk | De gedeelten van de blauwdruk die moeten worden opgenomen in de actieve kopie | Dit zijn doorgaans subpagina&#39;s van de hoofdmap |
| Synchronisatie | De generische termijn voor de synchronisatie van inhoud tussen de bron en Levende Exemplaren (door zowel **Uitvoer** als **synchroniseer** opties) |  |
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
>Zie [ Uitbreidend de Multi Manager van de Plaats ](/help/implementing/developing/extending/msm.md#overview-of-the-java-api) voor de objecten namen.

## Actieve kopieën {#live-copies}

Een live MSM-kopie is een kopie van specifieke site-inhoud waarvoor een live relatie met de oorspronkelijke bron behouden blijft:

* Live kopie neemt de inhoud van de bron over.
* De synchronisatie voert de daadwerkelijke overdracht van inhoud uit wanneer de veranderingen in de bron worden aangebracht.
* Een actieve kopie kan worden beschouwd als:
   * Ondiep: één pagina
   * Diep: de pagina, samen met de onderliggende pagina&#39;s
* De regels van de synchronisatie, genoemd rollout configuraties, bepalen welke eigenschappen worden gesynchroniseerd en wanneer de synchronisatie voorkomt.

In het vorige voorbeeld is `/content/wknd/language-masters/en` de algemene hoofdsite in het Engels. Als u de inhoud van deze site opnieuw wilt gebruiken, worden live MSM-kopieën gemaakt:

* De inhoud onder `/content/wknd/language-masters/en` is de bron.
* De inhoud onder `/content/wknd/language-masters/en` wordt gekopieerd onder de knooppunten `/content/wknd/us/en/` en `/content/wknd/ca/en` . Dit zijn de actieve kopieën.
* Auteurs wijzigen de pagina&#39;s onder `/content/wknd/language-masters/en` .
* Wanneer teweeggebracht, synchroniseert MSM deze veranderingen in Levende Exemplaren.

### Actieve kopieën - Compositie {#live-copies-composition}

>[!NOTE]
>
>De diagrammen en beschrijvingen in deze sectie vertegenwoordigen momentopnamen van potentiële Levende Exemplaren. Ze zijn niet volledig, maar bieden een overzicht om specifieke kenmerken te benadrukken.

Wanneer u eerst een Levende Exemplaar creeert, worden de geselecteerde bronpagina&#39;s weerspiegeld op een 1 :1 basis in Levende Exemplaar. Hierna kunnen ook nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) rechtstreeks in Live Copy worden gemaakt. Het is daarom nuttig om op de hoogte te zijn van deze variaties en van de invloed die deze hebben op de synchronisatie. Mogelijke composities zijn:

* [Live kopiëren met pagina&#39;s die niet live zijn gekopieerd](#live-copy-with-non-live-copy-pages)
* [Geneste actieve kopieën](#nested-live-copies)

De basisvorm van Live Copy heeft:

* De levende pagina&#39;s van het Exemplaar die op een 1 :1 basis op de geselecteerde bronpagina&#39;s wijzen.
* Eén configuratiedefinitie.
* Een live relatie gedefinieerd voor elke resource:
   * Koppel de Live Copy-bron aan de bijbehorende blauwdruk/bron.
   * Wordt gebruikt bij het realiseren van overerving en rollout.

De veranderingen kunnen [ worden gesynchroniseerd ](creating-live-copies.md#synchronizing-your-live-copy) volgens vereisten.

![ Levende de samenstellingsoverzicht van het Exemplaar ](../assets/live-copy-composition.png)

#### Live kopiëren met pagina&#39;s die niet live worden gekopieerd {#live-copy-with-non-live-copy-pages}

Wanneer u een live kopie maakt in AEM, kunt u de vertakking Live kopie zien en door de vertakking Live kopie navigeren en de normale AEM-functionaliteit gebruiken in de vertakking Live kopie. Dit betekent dat u (of een proces) nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) kunt maken in Live Copy. Bijvoorbeeld een product voor een bepaald gebied of land.

* Dergelijke bronnen hebben geen live relatie met de bron-/blauwdrukpagina&#39;s en zijn niet gesynchroniseerd.
* De scenario&#39;s kunnen voorkomen dat MSM als speciale gevallen behandelt. Wanneer u (of een proces) bijvoorbeeld een pagina maakt met dezelfde positie en naam in de vertakkingen van de bron/blauwdruk en Live kopie. Voor dergelijke situaties zie {de Conflicten van de Uitvoer MSM [ voor meer informatie.](rollout-conflicts.md)

![ Levend Exemplaar met niet-Levende pagina&#39;s van het Exemplaar ](../assets/live-copy-with-non-live-copy-pages.png)

#### Geneste actieve kopieën {#nested-live-copies}

Wanneer u (of een proces) a [ nieuwe pagina binnen een bestaand Levend Exemplaar ](#live-copy-with-non-live-copy-pages) creeert kan deze nieuwe pagina ook opstelling als Levend Exemplaar van een verschillende blauwdruk worden. Dit wordt een geneste live kopie genoemd. In geneste live kopieën wordt het gedrag van de tweede of binnenste live kopie op de volgende manieren beïnvloed door de eerste of buitenste live kopie:

* Een uitgebreide rollout die wordt geactiveerd voor Live Copy op hoofdniveau, kan worden doorgevoerd in de geneste Live Copy.
* Alle koppelingen tussen de bronnen worden herschreven in Live kopieën.

Koppelingen die bijvoorbeeld van de tweede naar de eerste blauwdruk wijzen, worden herschreven als koppelingen die van de geneste/tweede live kopie naar de eerste live kopie wijzen.

![ genestelde Levende Exemplaren ](../assets/live-copy-nested.png)

>[!NOTE]
>
>Als u een pagina verplaatst of de naam ervan wijzigt in de vertakking Live kopie, wordt deze behandeld als een geneste Live kopie, zodat AEM de relaties kan bijhouden.

#### Gestapelde actieve kopieën {#stacked-live-copies}

Een actieve kopie wordt een gestapelde live kopie genoemd wanneer deze wordt gemaakt als het onderliggende element van een ondiepe Live kopie. Het gedraagt zich op de zelfde manier zoals a [ genestelde Levende Exemplaar ](#nested-live-copies).

### Configuraties van Source, Blauwdrukken en Blauwdruk {#source-blueprints-and-blueprint-configurations}

Elke pagina of elke vertakking met pagina&#39;s kan worden gebruikt als bron van een Live kopie. Nochtans, MSM laat u ook een blauwdrukconfiguratie bepalen die een bronweg specificeert. De voordelen van het gebruik van een blauwdrukconfiguratie zijn dat zij:

* Sta de auteur toe om de **optie van de Uitvoer** op een blauwdruk te gebruiken. Dit wil zeggen dat er expliciet wijzigingen moeten worden aangebracht in Live kopieën die van deze blauwdruk overerven.
* Toestaan de auteur om **te gebruiken creeer Plaats**. Op deze manier kan de gebruiker eenvoudig talen selecteren en de structuur van Live Copy configureren.
* Definieer een standaardconfiguratie voor rollout voor actieve kopieën die een relatie hebben met de blauwdruk.

De bron voor een live kopie kan gewone pagina&#39;s zijn of pagina&#39;s die door een blauwdrukconfiguratie worden omringd. Beide zijn geldige gebruiksgevallen.

De bron vormt de blauwdruk voor Live kopie. De blauwdruk wordt gedefinieerd wanneer u:

* [ creeer een configuratie van de Vervaging ](creating-live-copies.md#creating-a-blueprint-configuration) - de configuratie bepaalt vooraf de pagina&#39;s die moeten worden gebruikt om Levend Exemplaar tot stand te brengen.
* [ creeer een Levend Exemplaar van een Pagina ](creating-live-copies.md#creating-a-live-copy-of-a-page) - de pagina&#39;s die worden gebruikt om Levend Exemplaar (de bronpagina&#39;s) tot stand te brengen zijn de blauwdrukpagina&#39;s. Naar de bronpagina kan door een blauwdrukconfiguratie al dan niet worden verwezen.

### Uitvoeren en synchroniseren {#rollout-and-synchronize}

Een rollout is de centrale actie MSM die Levende Kopieën met hun bronnen synchroniseert. U kunt rollouts handmatig uitvoeren of automatisch uitvoeren.

* A [ rollout configuratie ](#rollout-configurations) kan worden bepaald zodat de specifieke [ gebeurtenissen ](live-copy-sync-config.md#rollout-triggers) een rollout kunnen veroorzaken om automatisch voor te komen.
* Wanneer het ontwerpen van een blauwdrukpagina kunt u het **[bevel van de Uitvoer](creating-live-copies.md#rolling-out-a-blueprint)** gebruiken om veranderingen in het Levende Exemplaar te duwen.
   * Het **bevel van de Uitvoer** is beschikbaar op een blauwdruk pagina die door een blauwdrukconfiguratie van verwijzingen wordt voorzien.

  ![ Uitvoer ](../assets/live-copy-rollout.png)

* Wanneer het ontwerpen van een Levende pagina van het Exemplaar kunt u **[gebruiken synchroniseer](creating-live-copies.md#synchronizing-a-live-copy)** bevel om veranderingen van de bron aan het Levende Exemplaar te trekken.
   * Het **synchroniseer** bevel is altijd beschikbaar op de Levende pagina van het Exemplaar ongeacht of de bron/blauwdruk pagina door een blauwdrukconfiguratie wordt omvat.

  ![ synchroniseren ](../assets/live-copy-synchronize.png)

### Uitrolconfiguraties {#rollout-configurations}

Een rollout-configuratie bepaalt wanneer en hoe een Live Copy wordt gesynchroniseerd met de broninhoud. Een rollout-configuratie bestaat uit een trigger en een of meer synchronisatiehandelingen:

* **Trekker** - een trekker is een gebeurtenis die de levende actiesynchronisatie veroorzaakt om voor te komen, zoals de activering van een bronpagina. MSM bepaalt de trekkers die u kunt gebruiken.
* **de Acties van de Synchronisatie** - de acties van de Synchronisatie worden uitgevoerd op het Levende Exemplaar om het met de bron te synchroniseren. Voorbeelden van handelingen zijn het kopiëren van inhoud, het bestellen van onderliggende knooppunten en het activeren van de pagina Live kopie. MSM biedt diverse synchronisatiehandelingen.

>[!NOTE]
>
>U kunt aangepaste handelingen voor uw instantie maken met de Java API.

De configuraties van de rollout kunnen worden opnieuw gebruikt, zodat meer dan één Levend Exemplaar de zelfde rollout configuratie kan gebruiken. Verscheidene [ rollout configuraties ](live-copy-sync-config.md#installed-rollout-configurations) zijn inbegrepen in een standaardinstallatie.

### Conflicten bij rollout {#rollout-conflicts}

Rollouts kunnen ingewikkeld worden, vooral wanneer auteurs inhoud in zowel de bron als Live kopie bewerken. Zo is het nuttig om zich van bewust te zijn hoe AEM om het even welke [ conflicten behandelt die tijdens rollout ](rollout-conflicts.md) zouden kunnen voorkomen.

### Overerving en synchronisatie opschorten en annuleren {#suspending-and-cancelling-inheritance-and-synchronization}

Elke pagina en component in een live kopie is via een live relatie gekoppeld aan de bronpagina en -component ervan. De live relatie configureert de synchronisatie van Live Copy-inhoud van de bron.

U kunt **opschorten** de Levende overerving van het Exemplaar voor een Levende pagina van het Exemplaar zodat u paginaeigenschappen en componenten kunt veranderen. Wanneer u overerving onderbreekt, worden de pagina-eigenschappen en -componenten niet meer gesynchroniseerd met de bron.

Wanneer het uitgeven van een individuele pagina, kunnen de auteurs **Overerving** voor een component annuleren. Wanneer de overerving wordt geannuleerd, wordt de live relatie onderbroken en vindt de synchronisatie niet plaats voor die component. Het annuleren van overerving en synchronisatie is handig wanneer subsecties van de inhoud moeten worden aangepast.

### Een actieve kopie ontkoppelen {#detaching-a-live-copy}

U kunt ook [ een Levend Exemplaar ](creating-live-copies.md#detaching-a-live-copy) van zijn blauwdruk losmaken om alle verbindingen te verwijderen.

>[!CAUTION]
>
>De handeling Loskoppelen is permanent en niet-omkeerbaar.

Met de handeling Loskoppelen wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina permanent verwijderd. Alle MSM-relevante eigenschappen worden verwijderd uit Live Copy en de Live Copy-pagina&#39;s worden een zelfstandige kopie.

>[!TIP]
>
>Zie [ Ontstekend Levend Exemplaar ](creating-live-copies.md#detaching-a-live-copy) voor volledige details, met inbegrip van het verwante effect op sub- en ouderpagina&#39;s.

## Standaardstappen voor het gebruik van MSM {#standard-steps-for-using-msm}

De volgende stappen beschrijven de standaardprocedure voor het gebruiken van MSM om inhoud opnieuw te gebruiken en veranderingen in Levende Exemplaren te synchroniseren.

1. De inhoud van de bronsite ontwikkelen.
1. Bepaal de rollout configuratie aan gebruik.

   1. MSM [ installeert verscheidene rollout configuraties ](live-copy-sync-config.md#installed-rollout-configurations) die verscheidene gebruiksgevallen kunnen tevreden stellen.
   1. Naar keuze kunt u [ een rollout configuratie ](live-copy-sync-config.md#creating-a-rollout-configuration) tot stand brengen indien nodig.

1. Bepaal waar u [ moet specificeren de rollout configuraties om te gebruiken ](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) en zonodig te vormen.
1. Indien noodzakelijk, [ creeer een blauwdrukconfiguratie ](creating-live-copies.md#creating-a-blueprint-configuration) die de broninhoud van het Levende Exemplaar identificeert.
1. [ creeer een Levend Exemplaar ](creating-live-copies.md#creating-a-live-copy).
1. Breng de gewenste wijzigingen aan in de broninhoud. U dient het normale proces voor het beoordelen en goedkeuren van inhoud dat uw organisatie heeft ingesteld, te gebruiken.
1. [ Uitrol ](creating-live-copies.md#rolling-out-a-blueprint) de blauwdruk, of [ synchroniseer Levende Exemplaar ](creating-live-copies.md#synchronizing-a-live-copy) met de veranderingen.

## MSM aanpassen {#customizing-msm}

MSM verstrekt hulpmiddelen zodat uw implementatie aan de uitzonderlijke ingewikkeldheid kan aanpassen die wanneer het delen van inhoud kan bestaan.

* **de Configuraties van de Uitvoer van de Douane** - [ creeer een rollout configuratie ](live-copy-sync-config.md#creating-a-rollout-configuration) wanneer de geïnstalleerde configuraties van de uitrol niet aan uw vereisten voldoen. U kunt elke beschikbare uitrolltrigger- en synchronisatiehandeling gebruiken.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## Aanbevolen procedures {#best-practices}

De [ MSM Beste praktijken ](best-practices.md) pagina bevat belangrijke informatie betreffende uw implementatie.
