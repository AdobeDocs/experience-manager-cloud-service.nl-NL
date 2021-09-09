---
title: Het gebruiken van de Verzameling van Middel in Adobe Experience Manager als Cloud Service
description: De het Verdelen Samenvoeging van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen
exl-id: 5b6e5cb5-4c6c-4246-ba67-6b9f752867f5
source-git-commit: ac760e782f80ee82a9b0604ef64721405fc44ee4
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 1%

---

# De Sling Resource Merger in AEM as a Cloud Service gebruiken {#using-the-sling-resource-merger-in-aem}

## Doel {#purpose}

Sling Resource Merger verleent de diensten om tot middelen toegang te hebben en samen te voegen. Het verstrekt afdiff (differentiërende) mechanismen voor allebei:

* **[Bedekkingen](/help/implementing/developing/introduction/overlays.md)** van bronnen die gebruikmaken van de  [zoekpaden](/help/implementing/developing/introduction/overlays.md#search-paths).

* **Overschrijving** van componentendialogen voor touch-enabled UI (`cq:dialog`), gebruikend de hiërarchie van het middeltype (door het bezit  `sling:resourceSuperType`).

Met de Verschuivende Fusie van het Middel, worden de bedekking/met voeten getreden middelen en/of de eigenschappen samengevoegd met de originele middelen/eigenschappen:

* De inhoud van de aangepaste definitie heeft een hogere prioriteit dan die van het origineel (d.w.z. het *overlays* of *overschrijft* het).

* Indien nodig geven [eigenschappen](#properties) die in de aanpassing zijn gedefinieerd, aan hoe inhoud die uit het origineel is samengevoegd, moet worden gebruikt.

>[!CAUTION]
>
>De Sling Resource Merger en verwante methodes kunnen slechts met aanraking-toegelaten UI worden gebruikt (die enige UI voor AEM als Cloud Service beschikbaar is).

### Doelen voor AEM {#goals-for-aem}

De doelstellingen voor het gebruiken van de Verschuivende Fusie van het Middel in AEM zijn:

* zorgen ervoor dat aanpassingen niet worden aangebracht in `/libs`.
* vermindert de structuur die van `/libs` wordt herhaald.

   Wanneer het gebruiken van de Verzameling van het Middel wordt het niet geadviseerd om de volledige structuur van `/libs` te kopiëren aangezien dit in teveel informatie zou resulteren die in de aanpassing (gewoonlijk `/apps`) wordt gehouden. Het dupliceren van informatie vergroot onnodig de kans op problemen wanneer het systeem op om het even welke manier wordt verbeterd.

>[!CAUTION]
>
>U ***must*** verandert niets in `/libs` weg.
>
>Dit komt doordat de inhoud van `/libs` kan worden overschreven wanneer upgrades op uw instantie worden toegepast.
>
>* Bedekkingen zijn afhankelijk van [zoekpaden](/help/implementing/developing/introduction/overlays.md#search-paths).
>
>* Overschrijvingen zijn niet afhankelijk van de zoekpaden, maar maken de verbinding met de eigenschap `sling:resourceSuperType`.

>
>Overschrijvingen worden echter vaak gedefinieerd onder `/apps`, aangezien de beste praktijken in AEM als Cloud Service aanpassingen onder `/apps` moeten bepalen; Dit komt omdat u niets onder `/libs` moet veranderen.

### Eigenschappen {#properties}

De resourcefusie biedt de volgende eigenschappen:

* `sling:hideProperties` (  `String` of  `String[]`)

   Geeft de eigenschap op, of een lijst met eigenschappen, die moet worden verborgen.

   Alle jokertekens worden verborgen.`*`

* `sling:hideResource` ( `Boolean`)

   Geeft aan of de bronnen volledig verborgen moeten zijn, inclusief de onderliggende elementen.

* `sling:hideChildren` (  `String` of  `String[]`)

   Bevat het onderliggende knooppunt of de lijst met onderliggende knooppunten die moet worden verborgen. De eigenschappen van het knooppunt blijven behouden.

   Alle jokertekens worden verborgen.`*`

* `sling:orderBefore` (  `String`)

   Bevat de naam van de sibling knoop die de huidige knoop voor van zou moeten worden geplaatst.

Deze eigenschappen beïnvloeden hoe de overeenkomstige/originele middelen/eigenschappen (van `/libs`) door de bekleding/de opheffing (vaak in `/apps`) worden gebruikt.

### De structuur maken {#creating-the-structure}

Als u een bedekking wilt maken of overschrijven, moet u het oorspronkelijke knooppunt opnieuw maken, met de equivalente structuur, onder het doel (gewoonlijk `/apps`). Bijvoorbeeld:

* Bedekking

   * De definitie van het navigatie-item voor de Sites-console, zoals weergegeven in de spoorstaaf, is gedefinieerd op:

      `/libs/cq/core/content/nav/sites/jcr:title`

   * Als u dit wilt bedekken, maakt u het volgende knooppunt:

      `/apps/cq/core/content/nav/sites`

      Werk vervolgens de eigenschap `jcr:title` naar wens bij.

* Negeren

   * De definitie van het aanraakdialoogvenster voor de tekstconsole is als volgt:

      `/libs/foundation/components/text/cq:dialog`

   * Als u dit wilt overschrijven, maakt u het volgende knooppunt, bijvoorbeeld:

      `/apps/the-project/components/text/cq:dialog`

Als u een van deze opties wilt maken, hoeft u alleen de skeletstructuur opnieuw te maken. Om de recreatie van de structuur te vereenvoudigen kunnen alle intermediaire knopen van type `nt:unstructured` zijn (zij moeten niet het originele knooptype weerspiegelen; bijvoorbeeld in `/libs`).

In het bovenstaande overlayvoorbeeld zijn dus de volgende knooppunten nodig:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Bij gebruik van de samenvoeging van het Verspreide Middel (d.w.z. wanneer het behandelen van de norm, aanraking-toegelaten UI) wordt het niet geadviseerd om de volledige structuur van `/libs` te kopiëren aangezien het in teveel informatie zou resulteren die in `/apps` wordt gehouden. Dit kan problemen veroorzaken wanneer het systeem op om het even welke manier wordt bevorderd.

### Gevallen gebruiken {#use-cases}

Deze, samen met standaardfunctionaliteit, laten u toe:

* **Een eigenschap toevoegen**

   De eigenschap bestaat niet in de `/libs`-definitie, maar is vereist in de `/apps`-bedekking/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak de nieuwe eigenschap op dit knooppunt &quot;

* **Een eigenschap opnieuw definiëren (geen automatisch gemaakte eigenschappen)**

   De eigenschap wordt gedefinieerd in `/libs`, maar er is een nieuwe waarde vereist in de `/apps`-bedekking/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. De overeenkomende eigenschap op dit knooppunt maken (onder / `apps`)

      * Het bezit zal een prioriteit hebben die op de het Verspreiden configuratie van de Resolver van het Middel wordt gebaseerd.
      * Het wijzigen van het type eigenschap wordt ondersteund.

         Als u een bezitstype gebruikt verschillend aan die in `/libs` wordt gebruikt, dan zal het bezitstype u bepaalt worden gebruikt.
   >[!NOTE]
   >
   >Het wijzigen van het type eigenschap wordt ondersteund.

* **Een automatisch gemaakte eigenschap opnieuw definiëren**

   Door gebrek, auto-gecreeerde eigenschappen (zoals `jcr:primaryType`) zijn niet onderworpen aan een bedekking/opheffing om ervoor te zorgen dat het knooptype momenteel onder `/libs` wordt geëerbiedigd. Als u een bedekking/overschrijving wilt toepassen, moet u het knooppunt opnieuw maken in `/apps`, moet u de eigenschap expliciet verbergen en opnieuw definiëren:

   1. Maak het corresponderende knooppunt onder `/apps` met de gewenste `jcr:primaryType`
   1. Maak de eigenschap `sling:hideProperties` op dat knooppunt, met de waarde ingesteld op die van de eigenschap auto-created; bijvoorbeeld `jcr:primaryType`

      Deze eigenschap, gedefinieerd onder `/apps`, krijgt nu prioriteit boven de eigenschap gedefinieerd onder `/libs`

* **Een knooppunt en de onderliggende knooppunten opnieuw definiëren**

   De knoop en zijn kinderen worden bepaald in `/libs`, maar een nieuwe configuratie wordt vereist in `/apps` bedekking/opheffing.

   1. Combineer de handelingen van:

      1. Onderliggende items van een knooppunt verbergen (de eigenschappen van het knooppunt behouden)
      1. Eigenschappen opnieuw definiëren

* **Een eigenschap verbergen**

   De eigenschap wordt gedefinieerd in `/libs`, maar is niet vereist in de `/apps`-overlay/>.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak een eigenschap `sling:hideProperties` van het type `String` of `String[]`. Met deze optie geeft u de eigenschappen op die moeten worden verborgen of genegeerd. Jokertekens kunnen ook worden gebruikt. Bijvoorbeeld:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Een knooppunt en de onderliggende knooppunten verbergen**

   Het knooppunt en de onderliggende knooppunten worden gedefinieerd in `/libs`, maar zijn niet vereist in de `/apps`-overlay/>.

   1. Het corresponderende knooppunt maken onder /apps
   1. Een eigenschap `sling:hideResource` maken

      * type: `Boolean`
      * value: `true`

* **Onderliggende items van een knooppunt verbergen (terwijl de eigenschappen van het knooppunt behouden blijven)**

   De knoop, zijn eigenschappen en zijn kinderen worden bepaald in `/libs`. Het knooppunt en zijn eigenschappen zijn vereist in de `/apps`-bedekking/overschrijving, maar sommige of alle onderliggende knooppunten zijn niet vereist in de `/apps`-bedekking/overschrijving.

   1. Maak het corresponderende knooppunt onder `/apps`
   1. Maak de eigenschap `sling:hideChildren`:

      * type: `String[]`
      * waarde: een lijst met onderliggende knooppunten (zoals gedefinieerd in `/libs`) die moeten worden verborgen of genegeerd

      Jokerteken&amp;ast; kan worden gebruikt om alle onderliggende knooppunten te verbergen/te negeren.


* **Knooppunten opnieuw ordenen**

   Het knooppunt en de bijbehorende knooppunten worden gedefinieerd in `/libs`. Er is een nieuwe positie vereist, zodat het knooppunt opnieuw wordt gemaakt in de `/apps`-bedekking/overschrijving, waarbij de nieuwe positie wordt gedefinieerd ten opzichte van het desbetreffende knooppunt op hetzelfde niveau in `/libs`.

   * Gebruik de eigenschap `sling:orderBefore`:

      1. Maak het corresponderende knooppunt onder `/apps`
      1. Maak de eigenschap `sling:orderBefore`:

         This specifies the node (as in `/libs`) that the current node should be positioned before:

         * type: `String`
         * waarde: `<before-SiblingName>`

### Het aanroepen van de Verschuivende Fusie van het Middel van uw code {#invoking-the-sling-resource-merger-from-your-code}

De samenvoeging van het Verspreide Middel omvat twee leveranciers van douanemiddel - voor bekledingen en een andere voor met voeten treedt. Elk van deze kan binnen uw code worden aangehaald door een koppelingspunt te gebruiken:

>[!NOTE]
>
>Wanneer het toegang tot van uw middel wordt het geadviseerd om het aangewezen koppelingspunt te gebruiken.
>
>Dit zorgt ervoor dat de Verschuivende Fusie van het Middel wordt aangehaald en de volledig samengevoegde middelen teruggekeerd (verminderend de structuur die van `/libs` moet worden herhaald).

* Bedekking:

   * doel: bronnen samenvoegen op basis van zoekpad
   * koppelpunt: `/mnt/overlay`
   * usage: `mount point + relative path`
   * voorbeeld:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Overschrijven:

   * doel: samenvoegbronnen op basis van hun supertype
   * koppelpunt: `/mnt/overide`
   * gebruik: `mount point + absolute path`
   * voorbeeld:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

