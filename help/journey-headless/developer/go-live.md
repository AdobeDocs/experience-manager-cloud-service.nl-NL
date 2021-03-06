---
title: Hoe u met uw headless toepassing kunt gaan werken
description: In dit deel van de AEM Headless Developer Journey leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
source-git-commit: 270eb35023e34eed2cd17674372794c6c2cc7757
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 0%

---

# Hoe u met uw headless toepassing kunt gaan werken {#go-live}

In dit deel van het [AEM Headless Developer Journey](overview.md)leert u hoe u live een toepassing zonder kop kunt implementeren door uw lokale code in Git in te voeren en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM zonder kop: [Alles bij elkaar plaatsen - uw app en uw inhoud in AEM headless](put-it-all-together.md) u leerde hoe te om de AEM ontwikkelingshulpmiddelen te gebruiken om alle facetten van uw project samen te brengen.

Dit artikel bouwt verder op die grondbeginselen zodat u begrijpt hoe u uw eigen AEM headless project kunt voorbereiden om te leven.

## Doelstelling {#objective}

Met dit document krijgt u inzicht in de publicatiepijplijn zonder kop en in de prestatieaspecten die u moet kennen voordat u live gaat met uw toepassing.

* De toepassing beveiligen en schalen voordat deze wordt gestart
* Prestaties bewaken en problemen met foutopsporing opsporen

<!-- Alexandru: this is a bit redundant, to review again later

## Prepare your AEM Headless Application for Go-Live {#prepare-your-aem-headless-application-for-golive}

-->
Volg de onderstaande aanbevolen procedures om uw AEM toepassing zonder koppen klaar te maken voor gebruik.

## Beveilig en schaal uw toepassing zonder koppen voordat u de toepassing start {#secure-and-scale-before-launch}

1. Configureren [Verificatie op basis van token](/help/headless/security/authentication.md) met uw GraphQL-verzoeken
1. Configureren [Caching](/help/implementing/dispatcher/caching.md).

## Modelstructuur versus GraphQL-uitvoer {#structure-vs-output}

* Maak geen query&#39;s die meer dan 15 kB van JSON uitvoeren (gecomprimeerd gzip). Lange JSON-bestanden zijn bronintensief, zodat de clienttoepassing kan parseren.
* Vermijd meer dan vijf geneste niveaus van fragmenthi??rarchie??n. Met extra niveaus kunnen auteurs van inhoud de gevolgen van hun wijzigingen moeilijk in overweging nemen.
* Gebruik multiobject query&#39;s in plaats van query&#39;s met afhankelijkheidshi??rarchie??n binnen de modellen te modelleren. Hierdoor is meer flexibiliteit op lange termijn mogelijk om JSON-uitvoer te herstructureren zonder dat er veel wijzigingen in de inhoud moeten worden aangebracht.

## CDN-hoogte-breedteverhouding in cache maximaliseren {#maximize-cdn}

* Gebruik geen directe vragen GraphQL, tenzij u levende inhoud van de oppervlakte verzoekt.
   * Gebruik waar mogelijk doorlopende query&#39;s.
   * Verstrek CDN TTL boven 600 seconden zodat CDN hen in het voorgeheugen onderbrengt.
   * AEM kan het effect van een modelwijziging op bestaande query&#39;s berekenen.
* Splits JSON- dossiers/GraphQL vragen tussen laag en hoge tarief van de inhoudsverandering om cli??ntverkeer aan CDN te verminderen en hogere TTL toe te wijzen. Dit minimaliseert CDN die JSON met de oorsprongserver opnieuw bevestigt.
* Als u de inhoud van de CDN actief ongeldig wilt maken, gebruikt u Zacht wissen. Hierdoor kan de CDN de inhoud opnieuw downloaden zonder dat een cache-fout optreedt.

## Verbeter de tijd om inhoud zonder kop te downloaden {#improve-download-time}

* Zorg ervoor dat HTTP-clients HTTP/2 gebruiken.
* Zorg ervoor dat HTTP-clients de headeraanvraag voor gzip accepteren.
* Minimaliseer het aantal domeinen dat wordt gebruikt om JSON te hosten en referenced artefacten.
* Hefboomwerking `Last-modified-since` om bronnen te vernieuwen.
* Gebruiken `_reference` uitvoer in JSON-bestand om te beginnen met het downloaden van elementen zonder dat volledige JSON-bestanden hoeven te worden geparseerd.

## Distribueren naar productie {#deploy-to-production}

Zodra u ervoor hebt gezorgd dat alles is getest en correct werkt, bent u klaar om uw code-updates naar een [gecentraliseerde Git-opslagplaats in Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html).

Nadat de updates zijn ge??pload naar Cloud Manager, kunnen ze worden ge??mplementeerd naar AEM as a Cloud Service via [De CI/CD-pijplijn van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html).

U kunt uw code gaan implementeren door gebruik te maken van de uitgebreide Cloud Manager CI/CD-pijplijn [hier](/help/implementing/deploying/overview.md).

## Prestatiebewaking {#performance-monitoring}

Voor gebruikers die de beste ervaring hebben wanneer ze de toepassing zonder AEM gebruiken, is het belangrijk dat u de belangrijkste prestatiewaarden in de gaten houdt, zoals hieronder wordt beschreven:

* Voorvertoning- en productieversies van de app valideren
* Verifieer AEM statuspagina&#39;s voor huidige de status van de de dienstbeschikbaarheid
* Toegang tot prestatierapporten
   * Leveringsprestaties
      * CDN (Fastly) prestaties - controleaantal vraag, geheim voorgeheugentarief, foutentarieven en ladingsverkeer
      * De servers van de oorsprong - aantal vraag, foutentarieven, cpu laadt, loonladingsverkeer
   * Auteursprestaties
      * Aantal gebruikers, aanvragen en laden controleren
* Toepassings- en ruimtespecifieke prestatierapporten openen
   * Als de server is geactiveerd, controleert u of de algemene meetwaarden groen/oranje/rood zijn en identificeert u vervolgens specifieke toepassingsproblemen
   * Open dezelfde rapporten die hierboven zijn gefilterd naar app of space (bijvoorbeeld Photoshop-bureaublad, paywall)
   * Logbestand-API&#39;s van Splunk gebruiken om toegang te krijgen tot service- en toepassingsprestaties
   * Neem contact op met de Klantenondersteuning als er andere problemen zijn.

## Problemen oplossen {#troubleshooting}

### Foutopsporing {#debugging}

Volg deze beste praktijken als algemene benadering van het zuiveren:

* Functionaliteit en prestaties valideren met de voorvertoningsversie van de toepassing
* Functionaliteit en prestaties valideren met de productieversie van de toepassing
* Valideren met de JSON-voorvertoning van de Content Fragment Editor
* Inspect de JSON in de clienttoepassing om te controleren of er problemen zijn met de clienttoepassing of levering
* Inspect de JSON met GraphQL om te controleren of er problemen zijn met inhoud of AEM in cache.

### Een probleem aanmelden met ondersteuning {#logging-a-bug-with-support}

Volg de onderstaande stappen om een bug effici??nt te kunnen aanmelden bij Support voor het geval u verdere hulp nodig hebt:

* Maak, indien nodig, screenshots van het probleem
* Een manier documenteren om het probleem te reproduceren
* Documenteer de inhoud waarmee de uitgave wordt gereproduceerd
* Logboek een kwestie door het portaal van de Steun van de AEM met de aangewezen prioriteit

## De reis eindigt - of wel? {#journey-ends}

Gefeliciteerd! U hebt de AEM Headless Developer Journey voltooid! U zou nu een inzicht moeten hebben in:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM functies zonder kop.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM tot stand te brengen.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.
* Wat moet u doen na de go-live.

U hebt uw eerste AEM Headless-project al gestart of u hebt nu alle kennis die u nodig hebt om dit te doen. Geweldig werk!

### Toepassingen met ????n pagina verkennen {#explore-spa}

De koploze winkels in AEM hoeven hier echter niet te stoppen. U herinnert zich misschien in het [Een deel van de reis aan de slag](getting-started.md#integration-levels) we hebben kort besproken hoe AEM niet alleen de levering zonder kop en traditionele full-stack modellen ondersteunt, maar ook hybride modellen die de voordelen van beide combineren.

Als dit soort flexibiliteit iets u voor uw project nodig hebt, ga aan het facultatieve, extra deel van de reis voort, [Uitleg over het maken van toepassingen voor ????n pagina (SPA) met AEM.](create-spa.md)

## Aanvullende bronnen {#additional-resources}

* [Een overzicht van het Opstellen aan AEM as a Cloud Service](/help/implementing/deploying/overview.md)
* [Cloud Manager gebruiken om uw code te implementeren](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html)
* [Integreer de opslagplaats voor de Intel Health Care Management Suite van Cloud Manager met een externe opslagplaats voor Git en implementeer een project om as a Cloud Service te AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html)
