---
title: Inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service
description: 'Inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service. '
translation-type: tm+mt
source-git-commit: 23349f3350631f61f80b54b69104e5a19841272f
workflow-type: tm+mt
source-wordcount: '1679'
ht-degree: 100%

---


# Een inleiding tot de architectuur van Adobe Experience Manager as a Cloud Service {#an-introduction-to-the-architecture-adobe-experience-manager-as-a-cloud-service}

Adobe Experience Manager (AEM) as a Cloud Service heeft geleid tot wijzigingen in de architectuur.

## Schalen {#scaling}

AEM as a Cloud Service heeft nu:

* Een dynamische architectuur met een variabel aantal AEM-installatiekopieën.

![Dynamische architectuur](assets/concepts-01.png "Dynamische architectuur")

Deze architectuur:

* Wordt geschaald op basis van het *werkelijke* verkeer en de *werkelijke* activiteit.

* Bevat afzonderlijke instanties die alleen worden uitgevoerd wanneer dat nodig is.

* Gebruikt modulaire applicaties.

* Heeft een authoringcluster als standaard; dit voorkomt uitvaltijd voor onderhoudstaken.

Hierdoor is automatische schaling mogelijk voor variërende gebruikspatronen:

![Automatisch schalen voor variërende gebruikspatronen](assets/concepts-02.png "Automatisch schalen voor variërende gebruikspatronen")

Om dit te bereiken worden alle instanties van AEM as a Cloud Service gelijk gecreëerd, elk met dezelfde standaard formaateigenschappen in termen van het aantal nodes, toegewezen geheugen en toegewezen berekeningscapaciteit.

AEM as a Cloud Service is gebaseerd op het gebruik van een orkestratie-engine die:

* Voortdurend de status van de service controleert.

* Elk van de service-instanties dynamisch schaalt volgens de werkelijke behoeften, zowel omhoog als omlaag.

Dit:

* Geldt voor het aantal nodes, de hoeveelheid geheugen en de toegewezen CPU-capaciteit per node.

* Zorgt ervoor dat AEM as a Cloud Service zich kan aanpassen aan uw veranderende verkeerspatronen.

De schaling van instanties per tenant van de service kan automatisch of handmatig worden uitgevoerd, op beide assen:

* Verticaal: toegewezen geheugen en CPU-capaciteit kunnen worden vergroot of verkleind voor een vast aantal nodes.

* Horizontaal: het aantal nodes voor een bepaalde service kan worden verhoogd of verlaagd.

## Omgevingen {#environments}

>[!NOTE]
>
>Zie [Implementeren - Runmodi](/help/implementing/deploying/overview.md#runmodes) voor meer informatie

AEM as a Cloud Service wordt beschikbaar gesteld als afzonderlijke instanties waarbij elke instantie een volledige AEM-omgeving vertegenwoordigt. Er zijn vier typen omgevingen beschikbaar met AEM as a Cloud Service:

* **Productieomgeving**: is de host voor de applicaties van alle zakelijke gebruikers.

* **Faseomgeving**: wordt altijd gekoppeld aan één productieomgeving in een 1-op-1-relatie. De faseomgeving wordt gebruikt voor verschillende prestatie- en kwaliteitstesten voordat wijzigingen in de applicatie worden doorgevoerd in de productieomgeving.

* **Ontwikkelomgeving**: hier kunnen ontwikkelaars AEM-applicaties implementeren onder dezelfde runtimevoorwaarden als de fase- en productieomgeving.

* **Demonstratieomgeving**: kan worden gebruikt voor evaluatie, demonstratie, prototypering en opleiding.

De ontwikkelings- en demonstratieomgeving worden vaak *niet-productieomgevingen* genoemd.

## Programma&#39;s {#programs}

Elk nieuw AEM-project is altijd gebonden aan precies één specifieke codebase, waar u zowel de configuratie als de aangepaste code voor uw project kunt opslaan. Deze informatie wordt opgeslagen in een code-repository die via de gebruikelijke Git-clients toegankelijk is. De repository is voor u beschikbaar wanneer nieuwe programma&#39;s worden gemaakt.

Een AEM-programma is de container die het volgende bevat:

|  Programma-element |  Getal |
|--- |--- |
| Code-repository (Git) |  1 |
| Basisinstallatiekopie (Sites of Assets) |  1 |
| Fase- en productieomgevingset (1:1) | 0 of 1 |
| Niet-productieomgevingen (ontwikkeling of demonstratie) | 0 tot en met N |
| Pijplijn voor elke omgeving | 0 of 1 |

Er zijn aanvankelijk twee typen programma&#39;s beschikbaar voor AEM as a Cloud Service:

* AEM Cloud Sites Service

* AEM Cloud Assets Service

Beide bieden toegang tot een aantal functies en functionaliteiten. De authoringlaag bevat alle Sites- en Assets-functionaliteit voor alle programma&#39;s, maar de Assets-programma&#39;s hebben standaard geen publicatielaag.

## Runtimearchitectuur {#runtime-architecture}

Deze nieuwe architectuur bestaat uit verschillende hoofdonderdelen:

<!--- needs reworking -->

![AEM as a Cloud Service - Runtimearchitectuur](assets/concepts-03.png "AEM as a Cloud Service - Runtimearchitectuur")

* Voor AEM Sites as a Cloud Service:

   * Het concept van een authoringlaag en een publicatielaag voor elke omgeving (op een hoog niveau) blijft bestaan.

   * De authoringlaag bestaat uit twee of meer nodes binnen één authoringcluster. De schaal wordt automatisch aangepast, afhankelijk van de authoringactiviteit.

      * Auteurs/makers van content melden zich aan bij de AEM-authoringlaag om content te maken, te bewerken en te beheren.

      * Aanmelding bij de authoringlaag wordt beheerd door de Adobe Identity Management Services (IMS).

      * Integratie en de verwerking van Assets maken gebruik van een specifieke Assets Compute Service.
   * De publicatielaag bestaat uit twee of meer nodes binnen één publicatiefarm: ze kunnen onafhankelijk van elkaar werken. Elke node bestaat uit een AEM-uitgever en een webserver die is uitgerust met de AEM Dispatcher-module. De schaal wordt automatisch aan het siteverkeer aangepast.

      * Eindgebruikers of sitebezoekers bezoeken de website via de AEM Publish Service.


* Voor AEM Assets as a Cloud Service:

   * De architectuur omvat uitsluitend een authoringomgeving.

* Zowel vanuit de authoringlaag als de publicatielaag wordt contant van/naar een content-repository gelezen en bewaard.

   * In de publicatielaag wordt de content van de persistentielaag alleen gelezen.

   * In de authoringlaag wordt content van en naar de persistentielaag gelezen en geschreven.

   * De opslag van blobs wordt gedeeld tussen de publicatie- en de authoringlaag; bestanden worden niet *verplaatst*.

   * Wanneer content vanuit de authoringlaag wordt goedgekeurd, is dit een aanwijzing dat deze kan worden geactiveerd, en daarom wordt de content naar de persistentielaag in de publicatielaag verplaatst. Dit gebeurt via de Replication Service, een middleware-pijplijn. Deze pijplijn ontvangt de nieuwe content, waarbij de afzonderlijke publicatieservicenodes die geabonneerd zijn op de content, naar de pijplijn worden verplaatst.

      >[!NOTE]
      >
      >Zie [Replicatie](/help/operations/replication.md) voor meer details.

   * Ontwikkelaars en beheerders beheren de applicatie AEM as a Cloud Service met behulp van een CI/CD-service (Continuous Integration/Continuous Delivery), die beschikbaar wordt gesteld via de [Cloud Manager](/help/overview/what-is-new-and-different.md#cloud-manager)). Dit omvat code- en configuratie-implementaties die gebruikmaken van de CCI/CD-pijplijn van de Cloud Manager. Alles wat te maken heeft met bewaking, onderhoud en probleemoplossing (bijvoorbeeld logbestanden), wordt aan klanten binnen Cloud Manager beschikbaar gesteld.

   * Toegang tot de authoring- en publicatielijsten vindt altijd plaats via een load balancer. Deze wordt altijd bijgewerkt met de actieve nodes in elke laag.

   * Voor de publicatielaag is ook een CDN (Continuous Delivery Network) beschikbaar als eerste ingangspunt.

* Voor demonstratie-instanties van AEM as a Cloud Service wordt de architectuur vereenvoudigd tot één authoringnode. Daarom bevat de installatie niet alle kenmerken van de omgevingen voor standaardontwikkeling, fase of productie. Dit betekent ook dat er enige uitvaltijd kan zijn en dat er geen ondersteuning is voor back-up-/herstelbewerkingen.

## Implementatiearchitectuur {#deployment-architecture}

Cloud Manager beheert alle updates van de instanties van AEM as a Cloud Service. Het programma is verplicht aangezien het de enige manier is om de klantapplicatie te bouwen, te testen en te implementeren, zowel naar de authoring- als de publicatielaag. Deze updates kunnen worden geactiveerd door Adobe wanneer een nieuwe versie van de AEM Cloud Service gereed is, of door de klant wanneer een nieuwe versie van hun applicatie gereed is.

Technisch gezien wordt dit geïmplementeerd volgens het concept van een implementatiepijplijn, die aan elke omgeving binnen een programma is gekoppeld. Wanneer een Cloud Manager-pijplijn wordt uitgevoerd, maakt deze een nieuwe versie van de klantapplicatie, zowel voor de authoring- als voor de publicatielaag. Dit wordt bereikt door de nieuwste klantpakketten te combineren met de nieuwste Adobe-basisinstallatiekopie. Wanneer de nieuwe installatiekopieën zijn gemaakt en met succes getest, zorgt Cloud Manager voor een volledige automatisering van de cutover naar de nieuwste versie van de installatiekopie door alle servicenodes bij te werken met een doorlopend updatepatroon. Hierdoor is er geen uitvaltijd voor de authoring- of de publicatieservice.

<!--- needs reworking -->

![AEM as a Cloud Service - Implementatiearchitectuur](assets/concepts-04.png "AEM as a Cloud Service - Implementatiearchitectuur")

## Contentdistributie {#content-distribution}

Adobe Experience Manager as a Cloud Service heeft de manier veranderd waarop content wordt gepubliceerd. Met AEM as a Cloud Service wordt het replicatiekader van eerdere versies van AEM niet meer gebruikt om pagina&#39;s te publiceren (wijzigingen van de authoringinstantie verplaatsen naar publicatie-instanties).

AEM as a Cloud Service gebruikt nu de functie [Sling Content Distribution](https://sling.apache.org/documentation/bundles/content-distribution.html) om de juiste content te verplaatsen. Hierbij wordt een pijplijnservice gebruikt die wordt uitgevoerd op Adobe I/O, die buiten de AEM-runtime valt.

De installatie wordt automatisch uitgevoerd, inclusief automatische zelfconfiguratie wanneer publicatienodes tijdens runtime worden toegevoegd, verwijderd of gerecycled.

Eén verzoek tot publicatie of ongedaan maken van publicatie kan meerdere bronnen bevatten, maar retourneert slechts één status voor alle bronnen. De publicatie zal voor alle bronnen in de AEM Publish Service slagen of voor allemaal mislukken. Daardoor zijn de bronnen binnen de AEM Publish Service nooit in een inconsistente toestand.

**Architectuurdiagram voor contentdistributie op hoog niveau**

![Architectuurdiagram voor contentdistributie op hoog niveau](assets/architecture-diagram.png "Architectuurdiagram voor contentdistributie op hoog niveau")

## Belangrijke ontwikkelingen {#key-evolutions}

De nieuwe architectuur voor AEM as a Cloud Service introduceert een paar fundamentele wijzigingen en vernieuwingen vergeleken bij de vorige generaties:

* Alle bestanden (blobs) worden rechtstreeks geüpload en aangeboden vanuit een gegevensopslag in de cloud. De bijbehorende bitstroom gaat nooit door de JVM van de AEM Author- en Publish-services. Hierdoor kunnen de nodes van de Author- en Publish-services van AEM kleiner zijn en beter voldoen aan de verwachting van snelle automatische schaling. Voor bedrijfsleiders leidt dit tot een snellere ervaring bij het uploaden en downloaden van afbeeldingen, video, enzovoort.

* Alle bewerkingen die bestaan uit het publiceren van content, bevatten nu een pijplijn die een abonnementspatroon volgt. Gepubliceerde content wordt verplaatst naar diverse wachtrijen in de pijplijn, waarop alle nodes van de publicatieservice zijn geabonneerd. Daarom hoeft de authoringlaag niets te weten over het aantal nodes in de publicatieservice; hierdoor kan de publicatielaag snel automatisch worden geschaald.

* Het concept van een Golden Master werd geïntroduceerd om de levenscyclus van de publicatienodes te automatiseren. De Golden Master is een gespecialiseerde publicatienode waartoe geen enkele eindgebruiker toegang heeft, en waaruit alle nodes van de publicatieservice worden gecreëerd. Onderhoudsbewerkingen zoals compressie worden uitgevoerd op de content-repository die is gekoppeld aan de Golden Master. De publicatienodes worden dagelijks gerecycled en vergen geen routineonderhoud; vroeger was voor dergelijke onderhoud uitvaltijd nodig, vooral voor de authoringinstantie.

* De architectuur scheidt de applicatiecontent volledig van de applicatiecode en de configuratie. Alle code en configuraties zijn praktisch onveranderlijk en ingebouwd in de basisinstallatiekopie die wordt gebruikt om de diverse nodes van de authoring- en publicatieservices te maken. Daardoor is absoluut gegarandeerd dat alle nodes identiek zijn, en kunnen veranderingen in de code en configuratie uitsluitend globaal worden aangebracht door een Cloud Manager-pijplijn uit te voeren.
