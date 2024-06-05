---
title: Het gebruiken van de Verzameling van Middel in Adobe Experience Manager as a Cloud Service
description: De het Verdelen Samenvoeging van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen
exl-id: 5b6e5cb5-4c6c-4246-ba67-6b9f752867f5
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1158'
ht-degree: 0%

---

# Het gebruiken van de Verschuivende Fusie van het Middel in AEM as a Cloud Service {#using-the-sling-resource-merger-in-aem}

## Doel {#purpose}

Sling Resource Merger verleent de diensten om tot middelen toegang te hebben en samen te voegen. Het verstrekt afdiff (differentiërende) mechanismen voor allebei:

* **[Bedekkingen](/help/implementing/developing/introduction/overlays.md)** van middelen die [zoekpaden](/help/implementing/developing/introduction/overlays.md#search-paths).

* **Overschrijvingen** van componentdialoogvensters voor de interface met aanraakbediening (`cq:dialog`), met behulp van de hiërarchie van het middeltype (via de eigenschap `sling:resourceSuperType`).

Met de Verschuivende Fusie van het Middel, worden de bedekking/met voeten getreden middelen en/of de eigenschappen samengevoegd met de originele middelen/eigenschappen:

* De inhoud van de aangepaste definitie heeft een hogere prioriteit dan die van het origineel (dat wil zeggen *bedekkingen* of *overschrijvingen* het).

* Indien nodig [eigenschappen](#properties) Geef aan hoe inhoud die is samengevoegd met het origineel, moet worden gebruikt.

>[!CAUTION]
>
>De Sling Resource Merger en verwante methodes kunnen slechts met aanraking-toegelaten UI worden gebruikt (die enige UI beschikbaar voor AEM as a Cloud Service is).

### Doelen voor AEM {#goals-for-aem}

De doelstellingen voor het gebruiken van de Verschuivende Fusie van het Middel in AEM zijn:

* ervoor zorgen dat er geen wijzigingen in de aanpassing worden aangebracht in `/libs`.
* de structuur reduceren waarvan een replicatie wordt uitgevoerd `/libs`.

  Wanneer het gebruiken van de Verzameling van het Middel wordt het niet geadviseerd om de volledige structuur van te kopiëren `/libs` aangezien dit zou leiden tot te veel informatie in de aanpassing (gewoonlijk `/apps`). Het dupliceren van informatie vergroot onnodig de kans op problemen wanneer het systeem op om het even welke manier wordt verbeterd.

>[!CAUTION]
>
>U ***moet*** niets wijzigen in het dialoogvenster `/libs` pad.
>
>Dit komt omdat de inhoud van `/libs` kan worden overschreven wanneer upgrades op uw exemplaar worden toegepast.
>
>* Bedekkingen zijn afhankelijk van [zoekpaden](/help/implementing/developing/introduction/overlays.md#search-paths).
>
>* Overschrijvingen zijn niet afhankelijk van de zoekpaden, ze gebruiken de eigenschap `sling:resourceSuperType` om de verbinding te maken.
>
>Overschrijvingen worden echter vaak gedefinieerd onder `/apps`, aangezien de beste praktijken in AEM as a Cloud Service is aanpassingen te bepalen onder `/apps`; dit komt omdat je niets mag veranderen onder `/libs`.

### Eigenschappen {#properties}

De resourcefusie biedt de volgende eigenschappen:

* `sling:hideProperties` ( `String` of `String[]`)

  Geeft de eigenschap op, of een lijst met eigenschappen, die moet worden verborgen.

  Het jokerteken `*` verbergt alles.

* `sling:hideResource` ( `Boolean`)

  Geeft aan of de bronnen volledig verborgen moeten zijn, inclusief de onderliggende elementen.

* `sling:hideChildren` ( `String` of `String[]`)

  Bevat het onderliggende knooppunt of de lijst met onderliggende knooppunten die moet worden verborgen. De eigenschappen van het knooppunt blijven behouden.

  Het jokerteken `*` verbergt alles.

* `sling:orderBefore` ( `String`)

  Bevat de naam van de sibling knoop die de huidige knoop voor van zou moeten worden geplaatst.

Deze eigenschappen beïnvloeden hoe de overeenkomstige/originele middelen/eigenschappen (van `/libs`) worden gebruikt door de bedekking/overschrijving (vaak in `/apps`).

### De structuur maken {#creating-the-structure}

Als u een bedekking wilt maken of overschrijven, moet u het oorspronkelijke knooppunt opnieuw maken, met de equivalente structuur, onder de bestemming (gewoonlijk `/apps`). Bijvoorbeeld:

* Bedekking

   * De definitie van het navigatie-item voor de Sites-console, zoals weergegeven in de spoorstaaf, is gedefinieerd op:

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Als u dit wilt bedekken, maakt u het volgende knooppunt:

     `/apps/cq/core/content/nav/sites`

     Vervolgens werkt u de eigenschap bij `jcr:title` zoals vereist.

* Negeren

   * De definitie van het aanraakdialoogvenster voor de tekstconsole is als volgt:

     `/libs/foundation/components/text/cq:dialog`

   * Als u dit wilt overschrijven, maakt u het volgende knooppunt, bijvoorbeeld:

     `/apps/the-project/components/text/cq:dialog`

Als u een van deze opties wilt maken, hoeft u alleen de skeletstructuur opnieuw te maken. Om de recreatie van de structuur te vereenvoudigen kunnen alle intermediaire knopen van type zijn `nt:unstructured` (ze hoeven niet het oorspronkelijke knooppunttype te weerspiegelen, bijvoorbeeld in `/libs`).

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
>Wanneer u de samenvoeging van het Sling Resource (dat wil zeggen, wanneer u werkt met de standaard, interface met aanraakbediening) gebruikt, wordt het niet aanbevolen om de volledige structuur te kopiëren van `/libs` omdat het zou leiden tot te veel informatie in `/apps`. Dit kan problemen veroorzaken wanneer het systeem op om het even welke manier wordt bevorderd.

### Gevallen gebruiken {#use-cases}

Deze, samen met standaardfunctionaliteit, laten u toe:

* **Een eigenschap toevoegen**

  De eigenschap bestaat niet in het dialoogvenster `/libs` , maar is vereist in de `/apps` bedekking/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak de nieuwe eigenschap op dit knooppunt &quot;

* **Een eigenschap opnieuw definiëren (geen automatisch gemaakte eigenschappen)**

  De eigenschap wordt gedefinieerd in `/libs`, maar in de `/apps` bedekking/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Maak de overeenkomende eigenschap op dit knooppunt (onder / `apps`)

      * Het bezit zal een prioriteit hebben die op de het Verspreiden configuratie van de Resolver van het Middel wordt gebaseerd.
      * Het wijzigen van het type eigenschap wordt ondersteund.

        Als u een ander type eigenschap gebruikt dan het type dat wordt gebruikt in `/libs`Vervolgens wordt het door u gedefinieerde type eigenschap gebruikt.

  >[!NOTE]
  >
  >Het wijzigen van het type eigenschap wordt ondersteund.

* **Een automatisch gemaakte eigenschap opnieuw definiëren**

  Standaard worden automatisch gemaakte eigenschappen (zoals `jcr:primaryType`) niet onderworpen zijn aan een bedekking/overschrijving om ervoor te zorgen dat het knooptype dat momenteel onder `/libs` wordt nageleefd. Als u een bedekking/overschrijving wilt toepassen, moet u het knooppunt opnieuw maken in `/apps`, de eigenschap expliciet verbergen en opnieuw definiëren:

   1. Maak het corresponderende knooppunt onder `/apps` met het gewenste `jcr:primaryType`
   1. De eigenschap maken `sling:hideProperties` op dat knooppunt, met de waarde ingesteld op die van de eigenschap auto-created, bijvoorbeeld `jcr:primaryType`

      Deze eigenschap, gedefinieerd onder `/apps`, zal nu voorrang krijgen boven de in `/libs`

* **Een knooppunt en de onderliggende knooppunten opnieuw definiëren**

  De knoop en zijn kinderen worden bepaald in `/libs`, maar een nieuwe configuratie is vereist in de `/apps` bedekking/overschrijving.

   1. Combineer de handelingen van:

      1. Onderliggende items van een knooppunt verbergen (de eigenschappen van het knooppunt behouden)
      1. Eigenschappen opnieuw definiëren

* **Een eigenschap verbergen**

  De eigenschap wordt gedefinieerd in `/libs`, maar niet vereist in de `/apps` bedekking/overschrijving.

   1. Maak het corresponderende knooppunt binnen `/apps`
   1. Een eigenschap maken `sling:hideProperties` van het type `String` of `String[]`. Met deze optie geeft u de eigenschappen op die moeten worden verborgen of genegeerd. Jokertekens kunnen ook worden gebruikt. Bijvoorbeeld:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **Een knooppunt en de onderliggende knooppunten verbergen**

  De knoop en zijn kinderen worden bepaald in `/libs`, maar niet vereist in de `/apps` bedekking/overschrijving.

   1. Het corresponderende knooppunt maken onder /apps
   1. Een eigenschap maken `sling:hideResource`

      * type: `Boolean`
      * waarde: `true`

* **Onderliggende items van een knooppunt verbergen (terwijl de eigenschappen van het knooppunt behouden blijven)**

  De knoop, zijn eigenschappen en zijn kinderen worden bepaald in `/libs`. Het knooppunt en de eigenschappen ervan zijn vereist in het dialoogvenster `/apps` bedekken/overschrijven, maar sommige of alle onderliggende knooppunten zijn niet vereist in het dialoogvenster `/apps` bedekking/overschrijving.

   1. Maak het corresponderende knooppunt onder `/apps`
   1. De eigenschap maken `sling:hideChildren`:

      * type: `String[]`
      * waarde: een lijst met onderliggende knooppunten (zoals gedefinieerd in `/libs`) om te verbergen/negeren

      Jokerteken&amp;ast; kan worden gebruikt om alle onderliggende knooppunten te verbergen/te negeren.

* **Knooppunten opnieuw ordenen**

  De knoop en zijn siblings worden bepaald in `/libs`. Een nieuwe positie wordt vereist zodat wordt de knoop opnieuw gemaakt in `/apps` bedekking/overschrijving, waarbij de nieuwe positie wordt gedefinieerd ten opzichte van het juiste knooppunt op hetzelfde niveau in `/libs`.

   * Gebruik de `sling:orderBefore` eigenschap:

      1. Maak het corresponderende knooppunt onder `/apps`
      1. De eigenschap maken `sling:orderBefore`:

         Dit specificeert de knoop (zoals in `/libs`) dat het huidige knooppunt moet worden geplaatst voor:

         * type: `String`
         * waarde: `<before-SiblingName>`

### Het aanroepen van de Verschuivende Fusie van het Middel van uw code {#invoking-the-sling-resource-merger-from-your-code}

De samenvoeging van het Verspreide Middel omvat twee leveranciers van douanemiddel - voor bekledingen en een andere voor met voeten treedt. Elk van deze kan binnen uw code worden aangehaald door een koppelingspunt te gebruiken:

>[!NOTE]
>
>Wanneer het toegang tot van uw middel wordt het geadviseerd om het aangewezen koppelingspunt te gebruiken.
>
>Dit zorgt ervoor dat de Verschuivende Fusie van het Middel wordt aangehaald en volledig samengevoegde middel teruggekeerd (verminderend de structuur die van moet worden herhaald `/libs`).

* Bedekking:

   * doel: voeg bronnen samen op basis van hun zoekpad
   * koppelpunt: `/mnt/overlay`
   * gebruik: `mount point + relative path`
   * voorbeeld:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Overschrijven:

   * doel: voeg bronnen samen op basis van hun supertype
   * koppelpunt: `/mnt/overide`
   * gebruik: `mount point + absolute path`
   * voorbeeld:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

