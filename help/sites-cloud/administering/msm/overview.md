---
title: Inhoud opnieuw gebruiken - Beheer van meerdere sites en Live kopiëren
description: Maak kennis met de introductie van het hergebruik van inhoud met AEM krachtige functies Live Copy en Multi Site Manager.
feature: Beheer van meerdere sites
role: Beheerder
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '2686'
ht-degree: 0%

---


# Inhoud opnieuw gebruiken: Beheer van meerdere sites en actieve kopie {#multi-site-manager-and-live-copy}

Met MSM (Multi Site Manager) kunt u dezelfde site-inhoud op meerdere locaties gebruiken. MSM gebruikt hiervoor de Live Copy-functionaliteit.

* Met MSM kunt u:
   * Inhoud eenmaal maken en vervolgens
   * Gebruik deze inhoud opnieuw in andere gebieden (via [Actieve kopieën](#live-copies)) van dezelfde of andere sites.
* MSM onderhoudt dan de levende verhoudingen tussen uw broninhoud en zijn Levende Kopieën zodat:
   * Wanneer u wijzigingen aanbrengt in de broninhoud, worden de bron en Actieve kopieën gesynchroniseerd.
   * U kunt alleen de inhoud van de actieve kopieën aanpassen door de live relatie voor afzonderlijke subpagina&#39;s en/of componenten te verbreken.

Deze pagina biedt een overzicht van het hergebruiken van inhoud met MSM. Op de volgende pagina&#39;s worden verwante kwesties uitgebreid besproken.

* [Actieve kopieën maken en synchroniseren](creating-live-copies.md)
* [Console voor live kopiëren](live-copy-overview.md)
* [Synchronisatie van actieve kopie configureren](live-copy-sync-config.md)
* [Conflicten MSM-rollout](rollout-conflicts.md)
* [Aanbevolen MSM-procedures](best-practices.md)

## Mogelijke scenario&#39;s {#possible-scenarios}

Er zijn vele gebruiksgevallen voor MSM en Levende Exemplaren. Enkele scenario&#39;s zijn:

* **Multinationals - wereldwijd tot lokaal bedrijf**

   Een typisch gebruiksgeval dat MSM steunt is inhoud in verscheidene multinationale plaatsen van het zelfde-Taal opnieuw te gebruiken. Hierdoor kan de kerninhoud opnieuw worden gebruikt en kunnen nationale variaties worden toegestaan.

   Het Engelse gedeelte van het voorbeeld [WKND-zelfstudie](/help/implementing/developing/introduction/develop-wknd-tutorial.md) is bijvoorbeeld gemaakt voor klanten in de VS. De meeste inhoud op deze site kan ook worden gebruikt voor andere WKND-sites die geschikt zijn voor Engelstalige klanten van verschillende landen en culturen. De kerninhoud blijft voor alle sites hetzelfde, terwijl regionale aanpassingen kunnen worden aangebracht.

   De volgende structuur kan voor plaatsen voor de Verenigde Staten en Canada worden gebruikt. Merk op hoe `language-masters` knoop het master exemplaar van niet alleen Engels maar andere taalinhoud handhaaft. Deze inhoud kan worden gebruikt als basis voor aanvullende regionale taalinhoud naast het Engels.

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

* **Site**  maken (**sites**)

   * Met MSM kunt u meerdere websites beheren die gemeenschappelijke inhoud delen. Websites worden bijvoorbeeld vaak aangeboden voor een internationaal publiek, zodat de meeste inhoud in alle landen hetzelfde is, met een subset van de inhoud die specifiek is voor het afzonderlijke land. Met MSM kunt u [Actieve kopieën maken die automatisch een of meer sites bijwerken op basis van uw bronsite](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration). Dit helpt u ook om een gemeenschappelijke basisstructuur af te dwingen, de gemeenschappelijke inhoud over de veelvoudige plaatsen te gebruiken, een gemeenschappelijke blik te handhaven en zich te concentreren inspanningen op het beheren van de inhoud die eigenlijk tussen de plaatsen verschilt. Een site maken op deze manier:
      * Vereist een vooraf bepaalde blauwdrukconfiguratie om de bron te specificeren.
      * Hiermee maakt u een live kopie van de (vooraf gedefinieerde) bron.
      * Biedt de gebruiker de knop **Uitvoeren**.

* **Live kopie**  maken (**sites**)

   * Met MSM kunt u [een ad-hoc (eenmalige) live kopie van een afzonderlijke pagina of subvertakking van een website maken.](creating-live-copies.md#creating-a-live-copy-of-a-page) Bijvoorbeeld, het dupliceren van een subtak om informatie over een nieuwe/bijgewerkte versie van een product te verstrekken. Op deze manier een actieve kopie maken:
      * Hiermee maakt u een ad-hoc live kopie (geen configuratie voor blauwdrukken vereist).
      * Kan worden gebruikt om (direct) een actieve kopie van elke pagina of vertakking te maken.
      * Vereist **Synchronize** (verstrekt niet **Rollout** knoop).

* **Eigenschappen**  weergeven (**sites**)

   * Deze optie helpt u, indien van toepassing, [uw Live kopie te controleren](creating-live-copies.md#monitoring-your-live-copy) door informatie op te geven over de betreffende **actieve kopie** of **blauwdruk**.

* **Verwijzingen** (**sites**)

   * De [References](/help/sites-cloud/authoring/getting-started/basic-handling.md#references) rail verstrekt informatie over **Actieve exemplaren** samen met toegang tot aangewezen acties.

* **Overzicht**  van live kopiëren (**sites**)

   * Met deze console kunt u uw blauwdruk en de bijbehorende actieve kopieën [weergeven en beheren.](live-copy-overview.md)

* **Blauwdrukken**  (**gereedschappen**  -  **Sites**)

   * Met deze console kunt u [uw blauwdrukconfiguraties maken en beheren.](creating-live-copies.md#creating-a-blueprint-configuration)

>[!NOTE]
>
>De aspecten van de functionaliteit MSM worden gebruikt in verscheidene andere AEM eigenschappen zoals Lanceringen. In deze gevallen wordt Live Copy beheerd door die functie.

### Gebruikte termen {#terms-used}

Als inleiding, verstrekt de volgende lijst een overzicht van de belangrijkste termen die met MSM worden gebruikt. Deze zullen in de volgende secties en pagina&#39;s in meer detail worden behandeld.

| Term | Definitie | Meer details |
|---|---|---|
| Bron | De originele pagina&#39;s die als basis voor Actieve exemplaren worden gebruikt | Gelijk aan blauwdrukken en/of vervagingspagina&#39;s |
| Live kopie | De kopie (van de bron), onderhouden door synchronisatiehandelingen zoals gedefinieerd door de rollout-configuraties |  |
| Configuratie van live kopiëren | Definitie van de configuratiedetails voor een Live Copy |  |
| Live relatie | Effectieve definitie van de overerving van een bepaalde bron, d.w.z. de verbinding(en) tussen de bron en actieve kopieën | Hiermee zorgt u ervoor dat wijzigingen in de bron kunnen worden gesynchroniseerd met Live Copy |
| Blauwdruk | Gelijk aan bron | Kan worden gedefinieerd door een configuratie van een blauwdruk |
| Blauwdrukconfiguratie | Vooraf gedefinieerde configuratie die een bronpad opgeeft | Wanneer in een blauwdrukconfiguratie naar een blauwdrukpagina wordt verwezen, wordt de opdracht Uitrollen beschikbaar |
| Hoofdstuk | De gedeelten van de blauwdruk die moeten worden opgenomen in de actieve kopie | Dit zijn doorgaans subpagina&#39;s van de hoofdmap |
| Synchronisatie | De generische termijn voor de synchronisatie van inhoud tussen de bron en Live kopieën (door zowel **Rollout** als **Synchronize** opties) |  |
| Uitrol | Synchroniseert van bron naar Live kopie | Kan worden geactiveerd door een auteur (op een blauwdrukpagina) of door een systeemgebeurtenis (zoals gedefinieerd door de rollout-configuratie) |
| Rolloutconfiguratie | Regels die bepalen welke eigenschappen worden gesynchroniseerd, hoe en wanneer |  |
| Synchroniseren | Een handmatig verzoek om synchronisatie, uitgevoerd vanaf de Live Copy-pagina&#39;s |  |
| Overerving | Een pagina/component van Actieve kopie overerft de inhoud van de bronpagina/component wanneer de synchronisatie plaatsvindt |  |
| Onderbreken | Hiermee wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina tijdelijk verwijderd |  |
| Loskoppelen | Hiermee wordt de live relatie tussen een Live kopie en de bijbehorende blauwdrukpagina permanent verwijderd |  |
| Herstellen | Een pagina van Live kopie opnieuw instellen om alle annuleringen van overerving te verwijderen en de pagina terug te brengen naar dezelfde status als de bronpagina | Herstellen is van invloed op wijzigingen die u hebt aangebracht in pagina-eigenschappen, het alineasysteem en de componenten. |
| Ondiep | Een actieve kopie van één pagina |  |
| Diep | Een actieve kopie van een pagina, samen met de onderliggende pagina&#39;s ervan |  |

<!--
>[!TIP]
>
>See [Overview of the Java API](/help/sites-developing/extending-msm.md#overview-of-the-java-api) for the object names.
-->

## Actieve kopieën {#live-copies}

Een live MSM-kopie is een kopie van specifieke site-inhoud waarvoor een live relatie met de oorspronkelijke bron behouden blijft:

* Live kopie neemt de inhoud van de bron over.
* De synchronisatie voert de daadwerkelijke overdracht van inhoud uit wanneer de veranderingen in de bron worden aangebracht.
* Een actieve kopie kan worden beschouwd als:
   * Ondiep: één pagina
   * Diep: de pagina, samen met de onderliggende pagina&#39;s ervan
* De regels van de synchronisatie, genoemd rollout configuraties, bepalen welke eigenschappen worden gesynchroniseerd en wanneer de synchronisatie voorkomt.

In het vorige voorbeeld is `/content/wknd/language-masters/en` de algemene master site in het Engels. Als u de inhoud van deze site opnieuw wilt gebruiken, worden live MSM-kopieën gemaakt:

* De inhoud onder `/content/wknd/language-masters/en` is de bron.
* De inhoud onder `/content/wknd/language-masters/en` wordt gekopieerd onder de `/content/wknd/us/en/` en `/content/wknd/ca/en` knopen. Dit zijn de actieve kopieën.
* Auteurs brengen wijzigingen aan op de pagina&#39;s onder `/content/wknd/language-masters/en`.
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

Wijzigingen kunnen [gesynchroniseerd](creating-live-copies.md#synchronizing-your-live-copy) zijn volgens de vereisten.

![Samenstellingsoverzicht van live kopiëren](../assets/live-copy-composition.png)

#### Live kopiëren met pagina&#39;s die niet live worden gekopieerd {#live-copy-with-non-live-copy-pages}

Wanneer u een live kopie maakt in AEM, kunt u de vertakking Live kopie zien en door de vertakking Live kopie navigeren en de normale AEM gebruiken in de vertakking Live kopie. Dit betekent dat u (of een proces) nieuwe bronnen (pagina&#39;s en/of alinea&#39;s) kunt maken in Live Copy. Bijvoorbeeld een product voor een bepaald gebied of land.

* Dergelijke bronnen hebben geen live relatie met de bron-/blauwdrukpagina&#39;s en zijn niet gesynchroniseerd.
* De scenario&#39;s kunnen voorkomen dat MSM als speciale gevallen behandelt. Wanneer u (of een proces) bijvoorbeeld een pagina maakt met dezelfde positie en naam in de vertakkingen bron/blauwdruk en Live kopie. Voor dergelijke situaties zie [Conflicten van de Uitvoer MSM](rollout-conflicts.md) voor meer informatie.

![Live kopie met niet-live kopiëren pagina&#39;s](../assets/live-copy-with-non-live-copy-pages.png)

#### Geneste actieve kopieën {#nested-live-copies}

Wanneer u (of een proces) een [nieuwe pagina binnen een bestaand Levend Exemplaar ](#live-copy-with-non-live-copy-pages) creeert kan deze nieuwe pagina ook als Levend Exemplaar van een verschillende blauwdruk worden geplaatst. Dit wordt een geneste live kopie genoemd. In geneste live kopieën wordt het gedrag van de tweede of binnenste live kopie op de volgende manieren beïnvloed door de eerste of buitenste live kopie:

* Een uitgebreide rollout die wordt geactiveerd voor Live Copy op hoofdniveau, kan worden doorgevoerd in de geneste Live Copy.
* Eventuele koppelingen tussen de bronnen worden in de Live kopieën herschreven.

Koppelingen die bijvoorbeeld van de tweede naar de eerste blauwdruk wijzen, worden herschreven als koppelingen die van de geneste/tweede live kopie naar de eerste live kopie wijzen.

![Geneste actieve kopieën](../assets/live-copy-nested.png)

>[!NOTE]
>
>Als u een pagina verplaatst of de naam van een pagina wijzigt in de vertakking Live kopie, wordt deze behandeld als een geneste Live kopie zodat AEM de relaties kan bijhouden.

#### Gestapelde actieve kopieën {#stacked-live-copies}

Een actieve kopie wordt een gestapelde live kopie genoemd wanneer deze wordt gemaakt als het onderliggende element van een ondiepe Live kopie. Het gedraagt zich op de zelfde manier zoals [genestelde Levende Exemplaar ](#nested-live-copies).

### Bronconfiguraties, blauwdrukken en blauwdrukken {#source-blueprints-and-blueprint-configurations}

Elke pagina of elke vertakking met pagina&#39;s kan worden gebruikt als bron van een Live kopie. Nochtans, staat MSM u ook toe om een blauwdrukconfiguratie te bepalen die een bronweg specificeert. De voordelen van het gebruik van een blauwdrukconfiguratie zijn:

* Laat de auteur de optie **Uitvoer** op een blauwdruk gebruiken. Dit wil zeggen dat er expliciet wijzigingen moeten worden aangebracht in Live kopieën die van deze blauwdruk overerven.
* Laat de auteur **Site maken/> gebruiken.** Op deze manier kan de gebruiker eenvoudig talen selecteren en de structuur van Live Copy configureren.
* Definieer een standaardconfiguratie voor rollout voor actieve kopieën die een relatie hebben met de blauwdruk.

De bron voor een live kopie kan gewone pagina&#39;s zijn of pagina&#39;s die door een blauwdrukconfiguratie worden omringd. Beide zijn geldige gebruiksgevallen.

De bron vormt de blauwdruk voor Live kopie. De blauwdruk wordt gedefinieerd wanneer u:

* [Maak een configuratie](creating-live-copies.md#creating-a-blueprint-configuration)  Vervagen. De configuratie definieert vooraf de pagina&#39;s die moeten worden gebruikt om de actieve kopie te maken.
* [Een actieve kopie van een pagina](creating-live-copies.md#creating-a-live-copy-of-a-page)  maken. De pagina&#39;s die worden gebruikt om de actieve kopie (de bronpagina&#39;s) te maken, zijn de pagina&#39;s met de blauwdruk. Naar de bronpagina kan door een blauwdrukconfiguratie al dan niet worden verwezen.

### Uitvoeren en synchroniseren {#rollout-and-synchronize}

Een rollout is de centrale actie MSM die Levende Kopieën met hun bronnen synchroniseert. U kunt rollouts handmatig uitvoeren of automatisch uitvoeren.

* Een [rollout configuratie](#rollout-configurations) kan worden bepaald zodat specifieke [gebeurtenissen](live-copy-sync-config.md#rollout-triggers) een rollout kan veroorzaken om automatisch voor te komen.
* Wanneer u een pagina met een blauwdruk maakt, kunt u de opdracht **[Uitvoer](creating-live-copies.md#rolling-out-a-blueprint)** gebruiken om wijzigingen door te voeren in Live kopie.
   * De opdracht **Rollout** is beschikbaar op een blauwdrukpagina waarnaar wordt verwezen door een blauwdrukconfiguratie.

   ![Uitrol](../assets/live-copy-rollout.png)

* Wanneer u een pagina van Live kopie ontwerpt, kunt u de opdracht **[Synchroniseren](creating-live-copies.md#synchronizing-a-live-copy)** gebruiken om wijzigingen van de bron naar de Live kopie over te brengen.
   * De opdracht **Synchroniseren** is altijd beschikbaar op de pagina Live kopie, ongeacht of de bron-/blauwdrukpagina door een blauwdrukconfiguratie is omsloten.

   ![Synchroniseren](../assets/live-copy-synchronize.png)

### Uitrolconfiguraties {#rollout-configurations}

Een rollout-configuratie bepaalt wanneer en hoe een Live Copy wordt gesynchroniseerd met de broninhoud. Een rollout-configuratie bestaat uit een trigger en een of meer synchronisatiehandelingen:

* **Trigger**  - Een trigger is een gebeurtenis die ervoor zorgt dat de synchronisatie van actieve handelingen plaatsvindt, zoals de activering van een bronpagina. MSM bepaalt de trekkers die u kunt gebruiken.
* **Synchronisatiehandelingen**  - Synchronisatiehandelingen worden uitgevoerd op de Live kopie om deze te synchroniseren met de bron. Voorbeelden van handelingen zijn het kopiëren van inhoud, het bestellen van onderliggende knooppunten en het activeren van de pagina Live kopie. MSM biedt een aantal synchronisatiehandelingen.

>[!NOTE]
>
>U kunt aangepaste handelingen voor uw instantie maken met de Java API.

De configuraties van de rollout kunnen worden opnieuw gebruikt, zodat meer dan één Levend Exemplaar de zelfde rollout configuratie kan gebruiken. Verschillende [implementatieconfiguraties](live-copy-sync-config.md#installed-rollout-configurations) zijn opgenomen in een standaardinstallatie.

### Uitrolconflicten {#rollout-conflicts}

Rollouts kunnen ingewikkeld worden, vooral wanneer auteurs inhoud in zowel de bron als Live kopie bewerken. Zo is het nuttig om zich van bewust te zijn hoe AEM om het even welke [conflicten behandelt die tijdens rollout zouden kunnen voorkomen.](rollout-conflicts.md)

### Overerving en synchronisatie opheffen en annuleren {#suspending-and-cancelling-inheritance-and-synchronization}

Elke pagina en component in een live kopie is via een live relatie gekoppeld aan de bronpagina en -component ervan. De live relatie configureert de synchronisatie van Live Copy-inhoud van de bron.

U kunt de overerving van Live kopie voor een pagina van Live kopie **opschorten**, zodat u pagina-eigenschappen en -componenten kunt wijzigen. Wanneer u overerving onderbreekt, worden de pagina-eigenschappen en -componenten niet meer gesynchroniseerd met de bron.

Tijdens het bewerken van een afzonderlijke pagina kunnen auteurs Overerving **Annuleren** voor een component. Wanneer de overerving wordt geannuleerd, wordt de live relatie onderbroken en vindt de synchronisatie niet plaats voor die component. Het annuleren van overerving en synchronisatie is handig wanneer subsecties van de inhoud moeten worden aangepast.

### Live kopie {#detaching-a-live-copy} ontkoppelen

U kunt ook [een Live kopie](creating-live-copies.md#detaching-a-live-copy) loskoppelen van de blauwdruk om alle verbindingen te verwijderen.

>[!CAUTION]
>
>De handeling Loskoppelen is permanent en niet-omkeerbaar.

Met de handeling Loskoppelen wordt de live relatie tussen een actieve kopie en de bijbehorende blauwdrukpagina permanent verwijderd. Alle MSM-relevante eigenschappen worden verwijderd uit Live Copy en de Live Copy-pagina&#39;s worden een zelfstandige kopie.

>[!TIP]
>
>Zie [Een actieve kopie loskoppelen](creating-live-copies.md#detaching-a-live-copy) voor volledige informatie, inclusief de gerelateerde impact op subpagina&#39;s en bovenliggende pagina&#39;s.

## Standaardstappen voor het gebruik van MSM {#standard-steps-for-using-msm}

De volgende stappen beschrijven de standaardprocedure voor het gebruiken van MSM om inhoud opnieuw te gebruiken en veranderingen in Levende Exemplaren te synchroniseren.

1. De inhoud van de bronsite ontwikkelen.
1. Bepaal de rollout configuratie aan gebruik.

   1. MSM [installeert verscheidene rollout configuraties](live-copy-sync-config.md#installed-rollout-configurations) die aan een aantal gebruiksgevallen kunnen voldoen.
   1. Naar keuze kunt u [een rollout configuratie](live-copy-sync-config.md#creating-a-rollout-configuration) indien nodig tot stand brengen.

1. Bepaal waar u [de rollout configuraties aan gebruik ](live-copy-sync-config.md#specifying-the-rollout-configurations-to-use) moet specificeren en zonodig vormen.
1. Indien nodig, [creeer een blauwdrukconfiguratie](creating-live-copies.md#creating-a-blueprint-configuration) die de broninhoud van Levend Exemplaar identificeert.
1. [Maak een actieve kopie.](creating-live-copies.md#creating-a-live-copy)
1. Breng de gewenste wijzigingen aan in de broninhoud. U dient het normale proces voor het beoordelen en goedkeuren van inhoud dat uw organisatie heeft ingesteld, te gebruiken.
1. [Schuif ](creating-live-copies.md#rolling-out-a-blueprint) de blauwdruk uit of  [synchroniseer de actieve ](creating-live-copies.md#synchronizing-a-live-copy) kopie met de wijzigingen.

## MSM {#customizing-msm} aanpassen

MSM verstrekt hulpmiddelen zodat uw implementatie aan de uitzonderlijke ingewikkeldheid kan aanpassen die wanneer het delen van inhoud kan bestaan.

* **Aangepaste implementatieconfiguraties** :  [maak een ](live-copy-sync-config.md#creating-a-rollout-configuration) implementatieconfiguratie wanneer de geïnstalleerde implementatieconfiguraties niet aan uw vereisten voldoen. U kunt elke beschikbare uitrolltrigger- en synchronisatiehandeling gebruiken.

<!--
* **Custom Synchronization Actions** - [Create a custom synchronization action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action) when the installed actions do not meet your specific application requirements. MSM provides a Java API for creating custom synchronization actions.
-->

## Best practices voor {#best-practices}

De [MSM beste praktijken](best-practices.md) pagina bevat belangrijke informatie betreffende uw implementatie.
