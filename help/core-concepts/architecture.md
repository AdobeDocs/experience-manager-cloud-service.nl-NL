---
title: Inleiding tot de architectuur van Adobe Experience Manager als Cloud Service
description: 'Maak kennis met de architectuur van Adobe Experience Manager als cloudservice. '
translation-type: tm+mt
source-git-commit: 5a846d34ee094e7d2f7fc71dbeef65f3fa58e86c

---


# Een inleiding tot de architectuur van Adobe Experience Manager als Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

Adobe Experience Manager (AEM) als Cloud Service heeft geleid tot wijzigingen in de architectuur.

## Schalen {#scaling}

AEM als Cloud Service heeft nu:

* Een dynamische architectuur met een variabel aantal AEM-afbeeldingen.

![Dynamische](assets/concepts-01.png "architectuurDynamische architectuur")

Deze architectuur:

* Wordt geschaald op basis van het *werkelijke* verkeer en de *werkelijke* activiteit.

* Bevat afzonderlijke instanties die alleen worden uitgevoerd wanneer dat nodig is.

* Gebruikt modulaire toepassingen.

* Heeft een auteurcluster als gebrek; dit voorkomt downtime voor onderhoudstaken.

Hierdoor wordt automatische schaling ingeschakeld voor verschillende gebruikspatronen:

![Automatisch schalen voor verschillende gebruikspatronenAutomatisch](assets/concepts-02.png "schalen voor verschillende gebruikspatronen")

Om dit te bereiken, worden alle instanties van AEM als Dienst van de Wolk gecreeerd gelijk, elk met de zelfde standaard rangschikkende eigenschappen in termen van het aantal knopen, toegewezen geheugen en toegewezen gegevensverwerkingscapaciteit.

AEM als cloudservice is gebaseerd op het gebruik van een orchestratie-engine die:

* De status van de service wordt voortdurend gecontroleerd.

* elk van de dienstinstanties dynamisch schalen volgens de werkelijke behoeften; zowel omhoog als omlaag, naar gelang van het geval.

Dit:

* Is van toepassing op het aantal knopen, de hoeveelheid geheugen en de toegewezen capaciteit van cpu op elke knoop.

* Staat AEM als Dienst van de Wolk toe om uw verkeerspatronen aan te passen aangezien zij veranderen.

De schrapping van per-huurderinstanties van de dienst kan automatisch of manueel, op de twee assen zijn:

* Verticaal: toegewezen geheugen en CPU-capaciteit kunnen worden vergroot of verkleind voor een vast aantal knooppunten.

* Horizontaal: het aantal knooppunten voor een bepaalde dienst kan worden verhoogd of verlaagd.

## Omgevingen {#environments}

>[!NOTE]
>
> Zie [Implementeren - Runmodi voor meer informatie](/help/implementing/deploying/overview.md#runmodes)

AEM als Cloud Service wordt beschikbaar gesteld als afzonderlijke exemplaren waarbij elke instantie een volledige AEM-omgeving vertegenwoordigt. Er zijn vier typen omgevingen beschikbaar met AEM als cloudservice:

* **Productieomgeving**: gastheren de toepassingen voor de bedrijfsartsen.

* **Werkgebiedomgeving**: wordt altijd gekoppeld aan één productieomgeving in een 1:1-relatie. De werkgebiedomgeving wordt gebruikt voor verschillende prestatie- en kwaliteitstests voordat wijzigingen in de toepassing worden doorgevoerd in de productieomgeving.

* **Ontwikkelomgeving**: kunnen ontwikkelaars AEM-toepassingen implementeren onder dezelfde runtimevoorwaarden als de fase- en productieomgeving.

* **Demonstratieomgeving**: kan worden gebruikt voor evaluatie, demonstratie, prototype, en opleidingsdoeleinden.

De ontwikkelings- en demonstratieomgevingen worden vaak *niet-productieomgevingen* genoemd.

## Programma&#39;s {#programs}

Om het even welk nieuw project AEM is altijd gebonden aan precies één specifieke codebase, waar u zowel configuratie als douanecode voor uw project kunt opslaan. Deze informatie wordt opgeslagen in een codeopslagplaats, die via de gebruikelijke cliënten van Git toegankelijk is, die aan u bij de tijd beschikbaar wordt gesteld nieuwe programma&#39;s worden gecreeerd.

Een AEM-programma is de container die het volgende bevat:

|  Programmaelement |  Getal |
|--- |--- |
| Codeopslagplaats (Git) |  1 |
| Basislijnafbeelding (sites of elementen) |  1 |
| Werkgebied en productieomgeving ingesteld (1:1) | 0 of 1 |
| Niet-productieomgevingen (ontwikkeling of demonstratie) | 0 tot en met N |
| Pijpleiding voor elke omgeving | 0 of 1 |

Er zijn aanvankelijk twee typen programma&#39;s beschikbaar voor AEM als cloudservice:

* AEM Cloud Sites Service

* AEM Cloud Assets Service

Beide bieden toegang tot een aantal functies en functies. De auteurslaag zal alle Sites en Activa functionaliteit voor alle programma&#39;s bevatten, maar de programma&#39;s van Activa zullen geen publicatielaag door gebrek hebben.

## Runtime Architectuur {#runtime-architecture}

Deze nieuwe architectuur bestaat uit verschillende onderdelen:

<!--- needs reworking -->

![AEM als cloudservice - Runtime](assets/concepts-03.png "ArchitectuurAEM als cloudservice - Runtime Architectuur")

* Voor AEM-sites als cloudservice:

   * Het concept van een ontwerplaag en een publicatieniveau blijft bestaan voor elke omgeving (op een hoog niveau).

   * De auteurslaag wordt gemaakt van twee of meer knopen binnen één enkele auteurscluster. De schaal wordt automatisch aangepast, afhankelijk van de ontwerpactiviteit.

      * Auteurs/makers van inhoud melden zich aan bij de AEM-auteurslaag om inhoud te maken, te bewerken en te beheren.

      * Het aanmelden op de auteurslaag wordt beheerd door de Diensten van het Beheer van de Identiteit van Adobe (IMS).

      * De integratie en de verwerking van activa gebruiken een specifieke Dienst van het Rekeningmateriaal van Activa.
   * De publicatielaag bestaat uit twee of meer knopen binnen één enkel publiceer landbouwbedrijf: zij kunnen onafhankelijk van elkaar werken . Elk knooppunt bestaat uit een AEM-uitgever en een webserver die is uitgerust met de AEM Dispatcher-module. Het schalen automatisch met de behoeften van het plaatsverkeer.

      * Eindgebruikers of sitebezoekers bezoeken de website via de AEM-publicatieservice.


* Voor AEM-middelen als cloudservice:

   * De architectuur omvat slechts een auteursmilieu.

* Zowel de auteurslaag als publiceren rij lezen en blijven inhoud van/aan de Dienst van de Bewaarplaats van de Inhoud voortzetten.

   * De publicatielaag leest alleen inhoud van de persistentielaag.

   * De auteurslaag leest en schrijft inhoud van en aan de persistentielaag.

   * De opslag van lobs wordt gedeeld over publiceren en de auteursrij; bestanden worden niet *verplaatst*.

   * Wanneer inhoud wordt goedgekeurd van de auteurslaag, is dit een aanwijzing dat het kan worden geactiveerd, daarom aan de laag van de publicatielaag persistence worden geduwd. Dit gebeurt via de Replication Service, een middleware-pijplijn. Deze pijpleiding ontvangt de nieuwe inhoud, met individueel publiceert de dienstknopen die aan de inhoud intekenen die aan de pijpleiding wordt geduwd.

      >[!NOTE]
      >
      >For more details see [Replication](/help/operations/replication.md).

   * Ontwikkelaars en beheerders beheren de AEM als een Cloud Service-toepassing met behulp van een Continuous Integration/Continuous Delivery (CI/CD)-service, beschikbaar gesteld via de [Cloud Manager](/help/overview/what-is-new-and-different.md#cloud-manager)). Dit omvat code en configuratieplaatsingen die de CCI/CD pijpleiding van de Manager van de Wolk gebruiken. Alles wat betrekking heeft op bewaking, onderhoud en probleemoplossing (bijvoorbeeld logbestanden), wordt beschikbaar gesteld aan klanten in Cloud Manager.

   * Toegang tot de auteur- en publicatielijsten vindt altijd plaats via een taakverdelingsmechanisme. Dit is altijd bijgewerkt met de actieve knopen in elk van de rijen.

   * Voor publiceer rij, is de Ononderbroken Dienst van het Netwerk van de Levering (CDN) ook beschikbaar als eerste ingangspunt.

* Voor demonstratiegevallen van AEM als Cloud Service wordt de architectuur vereenvoudigd tot één auteurknooppunt. Daarom bevat het niet alle kenmerken van de standaardontwikkeling, het stadium of de productieomgeving. Dit betekent ook dat er enige downtime kan zijn en dat er geen ondersteuning is voor back-up-/herstelbewerkingen.

## Implementatiearchitectuur {#deployment-architecture}

Cloud Manager beheert alle updates van de AEM-instanties als een Cloud Service. Het is verplicht, aangezien de enige manier is om de klantentoepassing te bouwen, te testen en op te stellen, zowel aan de auteur als publicatielagen. Deze updates kunnen worden geactiveerd door Adobe, wanneer een nieuwe versie van de AEM Cloud Service gereed is, of door de klant wanneer een nieuwe versie van de toepassing gereed is.

Technisch gezien, wordt dit uitgevoerd wegens het concept van een plaatsingspijpleiding, die aan elke milieu binnen een programma wordt gekoppeld. Wanneer een pijplijn van de Manager van de Wolk loopt, leidt het tot een nieuwe versie van de klantentoepassing, zowel voor de auteur als publicatielagen. Dit wordt bereikt door de nieuwste klantpakketten te combineren met de nieuwste basisversie van Adobe. Wanneer de nieuwe afbeeldingen zijn gemaakt en met succes zijn getest, automatiseert Cloud Manager de cutover volledig naar de nieuwste versie van de afbeelding door alle serviceknoppen bij te werken met een rollend updatepatroon. Dit resulteert in geen onderbreking voor noch de auteur noch de publicatieservice.

<!--- needs reworking -->

![AEM als cloudservice - ImplementatiearchitectuurAEM als](assets/concepts-04.png "cloudservice - Implementatiearchitectuur")

## Inhoudsdistributie {#content-distribution}

Adobe Experience Manager als Cloud Service heeft de manier gewijzigd waarop het publiceren van inhoud werkt. Met AEM als Cloud Service wordt het replicatieframework van eerdere versies van AEM niet meer gebruikt om pagina&#39;s te publiceren (wijzig de wijzigingen van de auteur naar de publicatie-instanties).

AEM als cloudservice gebruikt nu de [verkoopfunctie voor inhoudsdistributie](https://sling.apache.org/documentation/bundles/content-distribution.html) om de juiste inhoud te verplaatsen. Dit gebruikt een pijpleidingsdienst die op Adobe I/O, die buiten runtime AEM wordt in werking gesteld is.

De installatie wordt automatisch uitgevoerd, inclusief automatische zelfconfiguratie wanneer publicatieknooppunten tijdens runtime worden toegevoegd, verwijderd of gerecycled.

Eén publicatie- of publicatieverzoek kan meerdere bronnen bevatten, maar retourneert één status die op alle bronnen is toegepast. het zal voor alle middelen in de publicatieservice van AEM slagen, of voor allen ontbreken. Dit zorgt ervoor dat de middelen binnen de AEM publicatieservice nooit in een inconsistente staat zullen zijn.

**Diagram van de Architectuur van de Distributie van de Inhoud op hoog niveau**

![DiagramHigh-level Content Distribution Architecture](assets/architecture-diagram.png "DiagramHigh-level Content Distribution Architecture Diagram")

## Belangrijkste ontwikkelingen {#key-evolutions}

De nieuwe architectuur voor AEM als Cloud Service introduceert enkele fundamentele wijzigingen en vernieuwingen in vergelijking met de vorige generaties:

* Alle bestanden (blobs) worden rechtstreeks geüpload en aangeboden in een gegevensopslag in de cloud. De bijbehorende bitstroom gaat nooit door de JVM van de AEM-auteur- en -publicatieservices. Hierdoor kunnen de knooppunten van de auteur- en publicatieservices van AEM kleiner van formaat zijn en beter compatibel zijn met de verwachting van snelle automatische schaling. Voor bedrijven leidt dit tot een snellere ervaring bij het uploaden en downloaden van afbeeldingen, video, enzovoort.

* Alle bewerkingen die bestaan uit het publiceren van inhoud, bestaan nu uit een pijplijn die volgt op een abonnementspatroon. De gepubliceerde inhoud wordt geduwd aan diverse rijen in de pijpleiding, waaraan alle knopen van de publicatiedienst intekenen. Dientengevolge, te hoeven de auteursrij zich niet bewust te zijn van het aantal knopen in de publicatiedienst; hierdoor kan de publicatielaag snel automatisch worden geschaald.

* Het concept van een gouden meester werd geïntroduceerd voor het automatiseren van de levenscyclus van de publicatieknopen. De gouden meester is een gespecialiseerde publiceerknoop, nooit betreden door om het even welke eind - gebruiker, en waarvan alle knopen van de publicatiedienst worden gecreeerd. Onderhoudsbewerkingen, zoals compactie, worden uitgevoerd op de opslagplaats voor inhoud die is gekoppeld aan de gouden master. De publicatieknooppunten worden dagelijks gerecycleerd en vereisen geen routineonderhoud; in het verleden was er enige onderbreking nodig , vooral voor de auteur .

* De architectuur scheidt volledig de toepassingsinhoud van de toepassingscode en configuratie. Alle code en configuratie zijn praktisch onveranderlijk en in het basislijnbeeld terug dat wordt gebruikt om de diverse knopen van de auteur tot stand te brengen en de publicatieservices te publiceren. Dientengevolge, is er een absolute garantie dat elke knoop identiek is, en de veranderingen in code en configuratie kunnen slechts globaal worden gemaakt door een pijpleiding van de Manager van de Wolk in werking te stellen.
