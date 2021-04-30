---
title: Hoe u met uw headless toepassing kunt gaan werken
description: In dit deel van de AEM Headless Developer Journey leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.
hide: true
hidefromtoc: true
index: false
exl-id: f79b5ada-8f59-4706-9f90-bc63301b2b7d
translation-type: tm+mt
source-git-commit: dc4f1e916620127ebf068fdcc6359041b49891cf
workflow-type: tm+mt
source-wordcount: '1039'
ht-degree: 0%

---

# Hoe te met Uw Hoofdloze Toepassing {#go-live} leven

>[!CAUTION]
>
>WERK IN VOORTGANG - De opstelling van dit document is aan de gang en mag niet worden opgevat als volledig of definitief en mag niet worden gebruikt voor productiedoeleinden.

In dit deel van [AEM Headless Developer Journey,](overview.md) leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM headless reis, [Hoe te om het allen samen te zetten - Uw App en Uw Inhoud in AEM Koploze](put-it-all-together.md) leerde u hoe te om uw eigen AEM headless project voor te bereiden om levend te gaan en u zou nu moeten:

* Begrijp de vereisten om live te gaan.

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe te om uw AEM Project zonder hoofd levend te brengen.

## Doel {#objective}

Met dit document krijgt u inzicht in de publicatiepijplijn zonder kop en in de prestatieaspecten die u moet kennen voordat u live gaat met uw toepassing.

* Inhoudsreplicatie en basiskennis van AEM inhoud in cache
* Configureer de vereiste gereedschappen om live te gaan voor uw toepassing zonder kop
* De toepassing beveiligen en schalen voordat deze wordt gestart
* Prestaties bewaken en problemen met foutopsporing opsporen

## Basisbeginselen van inhoudsreplicatie en -caching {#content-replication-and-caching}

Een volledige AEM omgeving bestaat uit een Auteur, Publish en Dispatcher.

* **De** service Auteur biedt interne gebruikers de mogelijkheid inhoud te maken, te beheren en voor te vertonen.

* **De** service Publiceren wordt beschouwd als de &quot;live&quot;-omgeving en is doorgaans de omgeving waarmee eindgebruikers werken. Inhoud wordt na bewerking en goedkeuring in de service Auteur gedistribueerd naar de service Publiceren.

* **De** Dispatcher is een statische webserver die is aangevuld met de AEM dispatcher-module. Webpagina&#39;s die door de instantie publish worden gemaakt, worden in het cachegeheugen opgeslagen om de prestaties te verbeteren.

Het meest gebruikelijke implementatiepatroon met toepassingen zonder kop is dat de productieversie van de toepassing verbinding maakt met een AEM-publicatieservice.

## Vereisten en configuratie {#requirements-and-configuration}

1. Stel een [Lokale runtime](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#install-java) in met de [AEM als Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
2. Installeer de [WKND-voorbeeldinhoud](/help/implementing/developing/introduction/develop-wknd-tutorial.md) en de volgende GraphQL-eindpunten
3. Implementeer en configureer een [statische Node Server](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/production-deployment.html?lang=en#static-server).

## Beveilig en schaal uw toepassing zonder hoofd alvorens {#secure-and-scale-before-launch} te lanceren

1. [Op token gebaseerde verificatie](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) configureren
2. Beveiligde webhaken
3. Caching en schaalbaarheid configureren

## Distribueren naar productie {#deploy-to-production}

Zodra u al uw code en inhoud plaatselijk hebt getest, bent u nu bereid om een productielocatie met AEM te beginnen.

### Modelstructuur versus GraphQL-uitvoer {#structure-vs-output}

* Maak geen query&#39;s die meer dan 15 kB van JSON uitvoeren (gecomprimeerd gzip). Lange JSON-bestanden zijn bronintensief, zodat de clienttoepassing kan parseren.
* Vermijd meer dan vijf geneste niveaus van fragmenthiërarchieën. Met extra niveaus kunnen auteurs van inhoud de gevolgen van hun wijzigingen moeilijk in overweging nemen.
* Gebruik multiobject query&#39;s in plaats van query&#39;s met afhankelijkheidshiërarchieën binnen de modellen te modelleren. Hierdoor is meer flexibiliteit op lange termijn mogelijk om JSON-uitvoer te herstructureren zonder dat er veel wijzigingen in de inhoud moeten worden aangebracht.

### CDN-hoogte-breedteverhouding in cache maximaliseren {#maximize-cdn}

* Gebruik geen directe vragen GraphQL, tenzij u levende inhoud van de oppervlakte verzoekt.
   * Gebruik in plaats daarvan doorlopende query&#39;s.
   * Verstrek CDN TTL boven 600 seconden zodat CDN hen kan in het voorgeheugen onderbrengen.
   * AEM kan het effect van een modelwijziging op bestaande query&#39;s berekenen.
* Splits JSON- dossiers/GraphQL- vragen tussen laag en hoge tarief van de inhoudsverandering om cliëntverkeer aan CDN te verminderen en hogere TTL toe te wijzen. Dit minimaliseert CDN die JSON met de oorsprongserver opnieuw bevestigt.
* Als u de inhoud van de CDN actief ongeldig wilt maken, gebruikt u Zacht wissen. Hierdoor kan de CDN de inhoud opnieuw downloaden zonder dat een cache-fout optreedt.

### Tijd voor downloaden van inhoud zonder kop {#improve-download-time} verbeteren

* Zorg ervoor dat HTTP-clients HTTP/2 gebruiken.
* Zorg ervoor dat HTTP-clients de headeraanvraag voor gzip accepteren.
* Minimaliseer het aantal domeinen dat wordt gebruikt om JSON te hosten en referenced artefacten.
* Gebruik `Last-modified-since` om bronnen te vernieuwen.
* Gebruik `_reference` uitvoer in JSON-bestand om te beginnen met het downloaden van elementen zonder dat u volledige JSON-bestanden hoeft te parseren.

## Bewaking {#monitoring}

### Hoe te om Algemene Prestaties {#check-overall-performance} te controleren

* Voorvertoning- en productieversies van de app valideren
* Verifieer AEM statuspagina&#39;s voor huidige de status van de de dienstbeschikbaarheid
* Toegang tot prestatierapporten
   * Leveringsprestaties
      * Fastly (CDN) - controleaantal vraag, geheim voorgeheugentarief, foutentarieven, ladingsverkeer
      * De servers van de oorsprong - aantal vraag, foutentarieven, cpu laadt, loonladingsverkeer
   * Auteursprestaties
      * Aantal gebruikers, aanvragen en laden controleren
* Toepassings- en ruimtespecifieke prestatierapporten openen
   * Als de server is geactiveerd, controleert u of de algemene meetwaarden groen/oranje/rood zijn en identificeert u vervolgens specifieke toepassingsproblemen
   * Open dezelfde rapporten die hierboven zijn gefilterd naar app/space (zoals Photoshop-bureaublad, paywall, enz.)
   * Logbestand-API&#39;s van Splunk gebruiken om toegang te krijgen tot service- en toepassingsprestaties
   * Neem contact op met de Klantenondersteuning als er andere problemen zijn.

## Problemen oplossen {#troubleshooting}

### Foutopsporing {#debugging}

Om ervoor te zorgen dat uw toepassing goed functioneert voordat u de toepassing start, wordt u aangeraden deze stappen te volgen als een algemene benadering van foutopsporing:

* Functionaliteit en prestaties valideren met de voorvertoningsversie van de toepassing
* Functionaliteit en prestaties valideren met de productieversie van de toepassing
* Valideren met de JSON-voorvertoning van de Content Fragment Editor
* Inspect de JSON in de clienttoepassing om te controleren of er problemen zijn met de clienttoepassing of levering
* Inspect de JSON met GraphQL om te controleren of er problemen zijn met inhoud of AEM in cache.

### Een probleem aanmelden met ondersteuning {#logging-a-bug-with-support}

Volg de onderstaande stappen om een bug efficiënt te kunnen aanmelden bij Support voor het geval u verdere hulp nodig hebt:

* Maak, indien nodig, screenshots van het probleem
* Een manier documenteren om het probleem te reproduceren
* Documenteer de inhoud waarmee de uitgave wordt gereproduceerd
* Logboek een kwestie door het portaal van de Steun van de AEM met de aangewezen prioriteit

## Volgende {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Inhoudsreplicatie en basiskennis van AEM inhoud in cache begrijpen.
* Zorg dat u weet hoe u de vereiste gereedschappen configureert om live te gaan voor uw toepassing zonder kop.
* Zorg dat u weet hoe u de toepassing kunt beveiligen en schalen voordat u de toepassing start.
* Begrijp hoe te om Prestaties te controleren en te zuiveren Kwesties.

U moet uw AEM zonder kop voortzetten door het document [Post Launch](post-launch.md) te bekijken waar u leert hoe u uw headless ervaring kunt behouden.

## Aanvullende bronnen {#additional-resources}
