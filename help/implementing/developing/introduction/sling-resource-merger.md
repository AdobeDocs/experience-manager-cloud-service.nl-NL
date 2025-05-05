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

# Het gebruiken van de Verzameling van Middel in AEM as a Cloud Service {#using-the-sling-resource-merger-in-aem}

## Doel {#purpose}

Sling Resource Merger verleent de diensten om tot middelen toegang te hebben en samen te voegen. Het verstrekt afdiff (differentiërende) mechanismen voor allebei:

* **[Bedekkingen](/help/implementing/developing/introduction/overlays.md)** van middelen die de [ onderzoekspaden ](/help/implementing/developing/introduction/overlays.md#search-paths) gebruiken.

* **treedt** van componentendialogen voor aanraking-toegelaten UI (`cq:dialog`) met voeten, gebruikend de hiërarchie van het middeltype (door middel van het bezit `sling:resourceSuperType`).

Met de Verschuivende Fusie van het Middel, worden de bedekking/met voeten getreden middelen en/of de eigenschappen samengevoegd met de originele middelen/eigenschappen:

* De inhoud van de aangepaste definitie heeft een hogere prioriteit dan die van origineel (namelijk het *bekledingen* of *met voeten treedt* het).

* Waar noodzakelijk, [ eigenschappen ](#properties) die in de aanpassing worden bepaald, wijzen erop hoe de inhoud die van origineel wordt samengevoegd moet worden gebruikt.

>[!CAUTION]
>
>De Sling Resource Merger en verwante methoden kunnen alleen worden gebruikt met de interface met aanraakbediening (de enige interface die beschikbaar is voor AEM as a Cloud Service).

### Doelen voor AEM {#goals-for-aem}

De doelstellingen voor het gebruiken van de Verschuivende Fusie van het Middel in AEM zijn:

* zorgt u ervoor dat er geen wijzigingen in de aanpassing worden aangebracht in `/libs` .
* reduceert de structuur die wordt gerepliceerd vanuit `/libs` .

  Wanneer u de samenvoeging van meerdere bronnen gebruikt, wordt het niet aangeraden de volledige structuur van `/libs` te kopiëren, omdat dit ertoe zou leiden dat er te veel informatie in de aanpassing wordt bewaard (gewoonlijk `/apps` ). Het dupliceren van informatie vergroot onnodig de kans op problemen wanneer het systeem op om het even welke manier wordt verbeterd.

>[!CAUTION]
>
>U ***moet*** niets in de `/libs` weg veranderen.
>
>De reden hiervoor is dat de inhoud van `/libs` kan worden overschreven wanneer upgrades op uw instantie worden toegepast.
>
>* De bekledingen zijn afhankelijk van [ onderzoekspaden ](/help/implementing/developing/introduction/overlays.md#search-paths).
>
>* Overschrijvingen zijn niet afhankelijk van de zoekpaden, maar maken de verbinding met de eigenschap `sling:resourceSuperType` .
>
>Overschrijvingen worden echter vaak gedefinieerd onder `/apps` , omdat het de beste manier in AEM as a Cloud Service is om aanpassingen onder `/apps` te definiëren. Dit komt omdat u niets onder `/libs` moet wijzigen.

### Eigenschappen {#properties}

De resourcefusie biedt de volgende eigenschappen:

* `sling:hideProperties` ( `String` of `String[]`)

  Geeft de eigenschap op, of een lijst met eigenschappen, die moet worden verborgen.

  Alle jokertekens worden verborgen. `*`

* `sling:hideResource` ( `Boolean`)

  Geeft aan of de bronnen volledig verborgen moeten zijn, inclusief de onderliggende elementen.

* `sling:hideChildren` ( `String` of `String[]`)

  Bevat het onderliggende knooppunt of de lijst met onderliggende knooppunten die moet worden verborgen. De eigenschappen van het knooppunt blijven behouden.

  Alle jokertekens worden verborgen. `*`

* `sling:orderBefore` ( `String`)

  Bevat de naam van de sibling knoop die de huidige knoop voor van zou moeten worden geplaatst.

Deze eigenschappen beïnvloeden hoe de corresponderende/oorspronkelijke resources/eigenschappen (van `/libs`) worden gebruikt door de overlay/overschrijving (vaak in `/apps` ).

### De structuur maken {#creating-the-structure}

Als u een overlay wilt maken of overschrijven, moet u het oorspronkelijke knooppunt opnieuw maken, met de equivalente structuur, onder het doel (gewoonlijk `/apps` ). Bijvoorbeeld:

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

Als u een van deze opties wilt maken, hoeft u alleen de skeletstructuur opnieuw te maken. Om de recreatie van de structuur te vereenvoudigen, kunnen alle intermediaire knooppunten van het type `nt:unstructured` zijn (ze hoeven niet het oorspronkelijke knooppunttype te weerspiegelen, bijvoorbeeld in `/libs` ).

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
>Wanneer u de samenvoeging van bronnen met meerdere aanraakfuncties (de standaardinterface) gebruikt, wordt het niet aangeraden de volledige structuur van `/libs` te kopiëren, omdat dit ertoe zou leiden dat er te veel informatie in `/apps` wordt opgeslagen. Dit kan problemen veroorzaken wanneer het systeem op om het even welke manier wordt bevorderd.

### Gevallen gebruiken {#use-cases}

Deze, samen met standaardfunctionaliteit, laten u toe:

* **voeg een bezit** toe

  De eigenschap bestaat niet in de definitie `/libs` , maar is vereist in de `/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. Maak de nieuwe eigenschap op dit knooppunt &quot;

* **herdefinieert een bezit (niet auto-gecreeerde eigenschappen)**

  De eigenschap wordt gedefinieerd in `/libs` , maar er is een nieuwe waarde vereist in de `/apps` overlay/override.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. De overeenkomende eigenschap op dit knooppunt maken (onder / `apps`)

      * Het bezit zal een prioriteit hebben die op de het Verspreiden configuratie van de Resolver van het Middel wordt gebaseerd.
      * Het wijzigen van het type eigenschap wordt ondersteund.

        Als u een ander type eigenschap gebruikt dan in `/libs` wordt gebruikt, wordt het type eigenschap dat u definieert gebruikt.

  >[!NOTE]
  >
  >Het wijzigen van het type eigenschap wordt ondersteund.

* **herdefinieert een auto-gecreeerde bezit**

  Standaard zijn automatisch gemaakte eigenschappen (zoals `jcr:primaryType` ) niet onderworpen aan een bedekking/overschrijving om ervoor te zorgen dat het knooppunttype dat momenteel onder `/libs` staat, wordt gerespecteerd. Als u een bedekking/overschrijving wilt toepassen, moet u het knooppunt opnieuw maken in `/apps` , moet u de eigenschap expliciet verbergen en opnieuw definiëren:

   1. Maak het corresponderende knooppunt onder `/apps` met het gewenste `jcr:primaryType`
   1. Maak de eigenschap `sling:hideProperties` op dat knooppunt, met de waarde ingesteld op die van de eigenschap auto-created, bijvoorbeeld `jcr:primaryType`

      Deze eigenschap, gedefinieerd onder `/apps` , krijgt nu voorrang op de eigenschap die is gedefinieerd onder `/libs` .

* **herdefinieert een knoop en zijn kinderen**

  Het knooppunt en de onderliggende knooppunten worden gedefinieerd in `/libs` , maar er is een nieuwe configuratie vereist in de `/apps` -overlay/overschrijving.

   1. Combineer de handelingen van:

      1. Onderliggende items van een knooppunt verbergen (de eigenschappen van het knooppunt behouden)
      1. Eigenschappen opnieuw definiëren

* **verberg een bezit**

  De eigenschap wordt gedefinieerd in `/libs` , maar is niet vereist in de `/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. Maak een eigenschap `sling:hideProperties` van het type `String` of `String[]` . Met deze optie geeft u de eigenschappen op die moeten worden verborgen of genegeerd. Jokertekens kunnen ook worden gebruikt. Bijvoorbeeld:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **verberg een knoop en zijn kinderen**

  Het knooppunt en de onderliggende knooppunten worden gedefinieerd in `/libs` , maar zijn niet vereist in de `/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken onder /apps
   1. Een eigenschap maken `sling:hideResource`

      * type: `Boolean`
      * value: `true`

* **de kinderen van de Huid van een knoop (terwijl het houden van de eigenschappen van de knoop)**

  Het knooppunt, de eigenschappen en onderliggende knooppunten worden gedefinieerd in `/libs` . Het knooppunt en de eigenschappen ervan zijn vereist in de `/apps` -overlay/overschrijving, maar sommige of alle onderliggende knooppunten zijn niet vereist in de `/apps` -overlay/overschrijving.

   1. Het corresponderende knooppunt maken onder `/apps`
   1. Maak de eigenschap `sling:hideChildren` :

      * type: `String[]`
      * waarde: een lijst met onderliggende knooppunten (zoals gedefinieerd in `/libs`) die moeten worden verborgen of genegeerd

      Jokerteken&ast; kan worden gebruikt om alle onderliggende knooppunten te verbergen/te negeren.

* **opnieuw ordenen knopen**

  Het knooppunt en de knooppunten op hetzelfde niveau worden gedefinieerd in `/libs` . Een nieuwe positie is vereist, zodat het knooppunt opnieuw wordt gemaakt in de `/apps` overlay/overschrijving, waarbij de nieuwe positie wordt gedefinieerd ten opzichte van het desbetreffende knooppunt op hetzelfde niveau in `/libs` .

   * Gebruik de eigenschap `sling:orderBefore` :

      1. Het corresponderende knooppunt maken onder `/apps`
      1. Maak de eigenschap `sling:orderBefore` :

         This specifies the node (as in `/libs`) that the current node should be positioned before:

         * type: `String`
         * value: `<before-SiblingName>`

### Het aanroepen van de Verschuivende Fusie van het Middel van uw code {#invoking-the-sling-resource-merger-from-your-code}

De samenvoeging van het Verspreide Middel omvat twee leveranciers van douanemiddel - voor bekledingen en een andere voor met voeten treedt. Elk van deze kan binnen uw code worden aangehaald door een koppelingspunt te gebruiken:

>[!NOTE]
>
>Wanneer het toegang tot van uw middel wordt het geadviseerd om het aangewezen koppelingspunt te gebruiken.
>
>Dit zorgt ervoor dat de Verschuivende Fusie van het Middel wordt aangehaald en het volledig samengevoegde middel teruggekeerd (verminderend de structuur die van `/libs` moet worden herhaald).

* Bedekking:

   * doel: voeg bronnen samen op basis van hun zoekpad
   * koppelpunt: `/mnt/overlay`
   * use: `mount point + relative path`
   * voorbeeld:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Overschrijven:

   * doel: voeg bronnen samen op basis van hun supertype
   * koppelpunt: `/mnt/overide`
   * use: `mount point + absolute path`
   * voorbeeld:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

