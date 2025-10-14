---
title: Hoe u met uw headless toepassing kunt gaan werken
description: In dit deel van de AEM Headless Developer Journey leert u hoe u een toepassing zonder kop kunt implementeren door uw lokale code in Git te nemen en deze naar Cloud Manager Git voor de CI/CD-pijplijn te verplaatsen.
exl-id: 81616e31-764b-44b0-94a6-3ae24ce56bf6
solution: Experience Manager
feature: Headless, Content Fragments,GraphQL API
role: Admin, Architect, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 0%

---

# Hoe u met uw headless toepassing kunt gaan werken {#go-live}

In dit deel van de [&#x200B; AEM Dagloze Reis van de Ontwikkelaar &#x200B;](overview.md), leer hoe te om een toepassing zonder kop op te stellen levend door uw lokale code in Git te nemen en het te bewegen naar Cloud Manager Git voor de pijpleiding CI/CD.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de AEM hoofdloze reis, [&#x200B; hoe te om het allen samen te zetten - Uw App en Uw Inhoud in AEM Zetel &#x200B;](put-it-all-together.md) leerde u hoe te om de AEM ontwikkelingshulpmiddelen te gebruiken om alle facetten van uw project samen te zetten.

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

1. Vorm [&#x200B; Symbolische Gebaseerde Authentificatie &#x200B;](/help/headless/security/authentication.md) met uw verzoeken van GraphQL
1. Vorm [&#x200B; Caching &#x200B;](/help/implementing/dispatcher/caching.md).

## Modelstructuur versus GraphQL-uitvoer {#structure-vs-output}

* Maak geen query&#39;s die meer dan 15 kB van JSON uitvoeren (gecomprimeerd gzip). Lange JSON-bestanden zijn bronintensief, zodat de clienttoepassing kan parseren.
* Vermijd meer dan vijf geneste niveaus van fragmenthiërarchieën. Met extra niveaus kunnen auteurs van inhoud de gevolgen van hun wijzigingen moeilijk in overweging nemen.
* Gebruik multiobject query&#39;s in plaats van query&#39;s met afhankelijkheidshiërarchieën binnen de modellen te modelleren. Hierdoor is meer flexibiliteit op lange termijn mogelijk om JSON-uitvoer te herstructureren zonder dat u veel inhoudswijzigingen hoeft aan te brengen.

## CDN-hoogte-breedteverhouding in cache maximaliseren {#maximize-cdn}

* Gebruik geen directe GraphQL-query&#39;s, tenzij u live-inhoud vanaf het oppervlak aanvraagt.
   * Gebruik waar mogelijk doorlopende query&#39;s.
   * Verstrek CDN TTL boven 600 seconden zodat CDN hen in het voorgeheugen onderbrengt.
   * AEM kan het effect van een modelwijziging op bestaande query&#39;s berekenen.
* Splits JSON-bestanden/GraphQL-query&#39;s tussen lage en hoge wijzigingssnelheid voor inhoud, zodat u het clientverkeer naar CDN kunt verminderen en een hogere TTL kunt toewijzen. Dit minimaliseert CDN die JSON met de oorsprongserver opnieuw bevestigt.
* Als u de inhoud van de CDN actief ongeldig wilt maken, gebruikt u Zacht wissen. Hierdoor kan de CDN de inhoud opnieuw downloaden zonder dat een cache-fout optreedt.

## Verbeter de tijd om inhoud zonder kop te downloaden {#improve-download-time}

* Zorg ervoor dat HTTP-clients HTTP/2 gebruiken.
* Zorg ervoor dat HTTP-clients de headeraanvraag voor gzip accepteren.
* Minimaliseer het aantal domeinen dat wordt gebruikt om JSON te hosten en referenced artefacten.
* Vernieuw bronnen met `Last-modified-since` .
* Gebruik `_reference` -uitvoer in JSON-bestand om elementen te downloaden zonder dat u volledige JSON-bestanden hoeft te parseren.

## Distribueren naar productie {#deploy-to-production}

Zodra u ervoor zorgt dat alles is getest en behoorlijk werkt, bent u bereid om uw codeupdates aan a [&#x200B; gecentraliseerde bewaarplaats van de it in Cloud Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/setup-cloud-manager-git-integration.html?lang=nl-NL) te duwen.

Nadat de updates aan Cloud Manager zijn geupload, kunnen zij aan AEM as a Cloud Service worden opgesteld gebruikend [&#x200B; Cloud Manager CI/CD pijpleiding &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=nl-NL).

U kunt beginnen uw code op te stellen door de pijpleiding van Cloud Manager te gebruiken CI/CD, die uitgebreid onder [&#x200B; het Opstellen van de Pakketten van de Inhoud als Manager van Cloud Manager en van het Pakket &#x200B;](/help/implementing/deploying/overview.md) wordt behandeld.

## Prestatiebewaking {#performance-monitoring}

Voor gebruikers die de beste ervaring hebben wanneer ze de toepassing zonder AEM gebruiken, is het belangrijk dat u de belangrijkste prestatiewaarden in de gaten houdt, zoals hieronder wordt beschreven:

* Voorvertoning- en productieversies van de app valideren
* Verifieer AEM statuspagina&#39;s voor huidige de status van de de dienstbeschikbaarheid
* Toegang tot prestatierapporten
   * Leveringsprestaties
      * CDN (Fastly) prestaties - controleaantal vraag, geheim voorgeheugentarief, foutentarieven en ladingsverkeer
      * De servers van de oorsprong - aantal vraag, foutentarieven, lading CPU, ladingsverkeer
   * Auteursprestaties
      * Aantal gebruikers, aanvragen en laden controleren
* Toepassings- en ruimtespecifieke prestatierapporten openen
   * Als de server is geactiveerd, controleert u of de algemene meetwaarden groen/oranje/rood zijn en identificeert u vervolgens specifieke toepassingsproblemen
   * Open dezelfde rapporten die hierboven zijn gefilterd naar app of space (bijvoorbeeld Photoshop-bureaublad, paywall)
   * Logbestand-API&#39;s van Splunk gebruiken voor toegang tot service- en toepassingsprestaties
   * Neem contact op met de Klantenondersteuning als er andere problemen zijn.

## Problemen oplossen {#troubleshooting}

### Foutopsporing {#debugging}

Volg deze beste praktijken als algemene benadering van het zuiveren:

* Functionaliteit en prestaties valideren met de voorvertoningsversie van de toepassing
* Functionaliteit en prestaties valideren met de productieversie van de toepassing
* Valideren met de JSON-voorvertoning van de Content Fragment Editor
* Inspect de JSON in de clienttoepassing om te controleren of er problemen zijn met de clienttoepassing of levering
* Inspect de JSON met GraphQL om te controleren of er problemen zijn met inhoud in de cache of AEM

### Een probleem aanmelden met ondersteuning {#logging-a-bug-with-support}

Om een insect met Steun efficiënt te registreren voor het geval dat u verdere hulp nodig hebt, doe het volgende:

* Indien nodig screenshots van het probleem nemen
* Een manier documenteren om het probleem te reproduceren
* Documenteer de inhoud waarmee de uitgave wordt gereproduceerd
* Logboek een kwestie door het portaal van de Steun van de AEM met de aangewezen prioriteit

## De reis eindigt - of wel? {#journey-ends}

Gefeliciteerd! U hebt de AEM Headless Developer Journey voltooid! U zou nu een inzicht moeten hebben in:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM eindeloze functies.
* Hoe te om Hoofdloze project te organiseren en te AEM.
* Hoe te om koploze inhoud in AEM te creëren.
* Hoe te om koploze inhoud in AEM terug te winnen en bij te werken.
* Hoe te om met een AEM Zwaardeloos project te leven.
* Wat moet u doen na de go-live.

U hebt uw eerste AEM Headless-project al gestart of u hebt nu alle kennis die u nodig hebt om dit te doen. Geweldig werk!

### Toepassingen met één pagina verkennen {#explore-spa}

De koploze winkels in AEM hoeven hier echter niet te stoppen. U zou zich in het [&#x200B; Begonnen deel van de reis &#x200B;](getting-started.md#integration-levels) kunnen herinneren wij kort bespraken hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar ook hybride modellen kunnen steunen die de voordelen van allebei combineren.

Als dit soort flexibiliteit iets is u voor uw project nodig hebt, ga op het facultatieve, extra deel van de reis verder, [&#x200B; hoe te om Enige Toepassingen van de Pagina (SPA) met AEM &#x200B;](create-spa.md) tot stand te brengen.

## Aanvullende bronnen {#additional-resources}

* [Inleiding tot AEM als een CMS zonder kop](/help/headless/introduction.md)
* [&#x200B; AEM het Portaal van de Ontwikkelaar &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
* [&#x200B; Tutorials voor Zwaartepunt in AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL)
* [Een overzicht van de implementatie op AEM as a Cloud Service](/help/implementing/deploying/overview.md)
* [&#x200B; Gebruik Cloud Manager om Uw Code &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/deploying-code.html?lang=nl-NL) op te stellen
* [&#x200B; integreer de Bewaarplaats van het Git van Cloud Manager met een Externe Bewaarplaats van het Git en stel een Project aan AEM as a Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/devops/deploy-code.html?lang=nl-NL) op
