---
title: Experience Audit Dashboard
description: Ontdek hoe de Controle van de Ervaring uw plaatsingsproces bevestigt, die ervoor zorgt dat de veranderingen basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen. Het verstrekt een duidelijke en informatieve dashboardinterface om deze metriek te volgen.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 72868ab808ebbd99c5e81805e7669083c5c754fb
workflow-type: tm+mt
source-wordcount: '1927'
ht-degree: 0%

---


# Experience Audit-dashboard {#experience-audit-dashboard}

Ontdek hoe de Controle van de Ervaring uw plaatsingsproces bevestigt, die ervoor zorgt dat de veranderingen basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen. Het verstrekt een duidelijke en informatieve dashboardinterface om deze metriek te volgen.

>[!NOTE]
>
>Deze eigenschap is slechts beschikbaar aan [ het vroege adoptieprogramma ](/help/implementing/cloud-manager/release-notes/current.md#early-adoption).
>
>Voor details op de bestaande eigenschap van de Controle van de Ervaring voor AEM as a Cloud Service, zie [ het Testen van de Controle van de Ervaring ](/help/implementing/cloud-manager/experience-audit-testing.md).

## Overzicht {#overview}

De Controle van de ervaring bevestigt het plaatsingsproces en de hulp zorgt ervoor dat de veranderingen worden opgesteld:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Breng geen regressies aan.

De controle van de ervaring in Cloud Manager zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing werd geïntroduceerd.

De Controle van de ervaring wordt aangedreven door [ Lighthouse van Google ](https://developer.chrome.com/docs/lighthouse/overview/), een open bronhulpmiddel van Google, en in alle de productiepijpleidingen van Cloud Manager toegelaten.

## Beschikbaarheid {#availability}

Er is een Experience Audit beschikbaar voor Cloud Manager:

* (Standaard) Sites-productiepijpleidingen
* (Optioneel) Ontwikkeling van pijpleidingen in volle stapel
* (Facultatief) Ontwikkeling van voorpijpleidingen

Zie de [ sectie van de Configuratie ](#configuration) voor meer informatie over hoe te om de controle voor de facultatieve milieu&#39;s te vormen.

Audits worden uitgevoerd als onderdeel van de pijpleiding. De controles kunnen ook [ in werking worden gesteld op bestelling ](#on-demand) buiten pijpleidingen.

## Configuratie {#configuration}

De Experience Audit is standaard beschikbaar voor productiepijpleidingen. Het kan naar keuze voor ontwikkeling van volledig-stapel en front-end pijpleidingen worden toegelaten. In alle gevallen, moet u bepalen welke inhoudswegen tijdens pijpleidingsuitvoering worden geëvalueerd.

1. Afhankelijk van het type van pijpleiding u wenst te vormen, volg de richtingen aan:

   * Voeg een nieuwe [ productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) toe om de wegen te bepalen u de controle wilt evalueren.
   * Voeg een nieuwe [ niet-productiepijplijn toe, ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) als u wenst om de controle op een front-end of ontwikkelings volledig-stapelpijpleiding toe te laten.
   * Of u kunt [ een bestaande pijpleiding uitgeven, ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) en de bestaande opties bijwerken.

1. Om de Controle van de Ervaring te gebruiken wanneer het toevoegen van of het uitgeven van een niet productiepijplijn, selecteer het **checkbox van de Controle van de Ervaring 0}.** U kunt deze optie op het **Code van Source** lusje vinden.

   ![ toelatend de Controle van de Ervaring ](assets/experience-audit-enable.jpg)

   * Alleen nodig voor niet-productiepijpleidingen.
   * Het **lusje van de Controle van de Ervaring** verschijnt wanneer checkbox wordt geselecteerd.

1. Voor zowel productie als niet productiepijpleidingen, bepaalt u de wegen die in de Controle van de Ervaring op de **Controle van de Ervaring** tabel moeten worden omvat.

   * Pagina-paden moeten beginnen met `/` en zijn relatief ten opzichte van uw site.
   * Als uw site bijvoorbeeld `wknd.site` is en u `https://wknd.site/us/en/about-us.html` wilt opnemen in de Experience Audit, voert u het pad in `/us/en/about-us.html` .

   ![ die een weg voor de Controle van de Ervaring bepalen ](assets/experience-audit-add-page.png)

1. Klik **toevoegen de Pagina** en de weg is auto-voltooid met het adres van uw milieu en aan de lijst van wegen toegevoegd.

   ![ het Opslaan weg aan de lijst ](assets/experience-audit-page-added.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klik **sparen**.

## Resultaten van controle door ervaring {#results}

De resultaten van de Controle van de Ervaring worden voorgesteld in de **testende fase van het Stadium** van de productiepijpleiding via de [ pagina van de de uitvoeringspijplijn van de productiepijplijn ](/help/implementing/cloud-manager/deploy-code.md).

![ Dashboard in de pijpleiding ](assets/experience-audit-dashboard.jpg)

De Controle van de ervaring verstrekt de mediane Emissiescore van Google voor de [ gevormde pagina&#39;s ](#configuration) en het verschil in score aan het vorige aftasten.

Van deze summiere mening in de **het Testen van het Stadium** fase van de pijpleiding, hebt u twee opties:

* **[Mening de langzaamste pagina&#39;s](#view-slowest-pages)**
* **[Mening het volledige rapport](#view-full-report)**

U kunt tot de volledige controleresultaten toegang hebben door het **lusje van Rapporten** in het dashboard van Cloud Manager te klikken. Naast de samenvatting die in de details van de pijpleidingslooppas wordt getoond, kunt u [ het volledige rapport ](#view-full-report) direct bekijken.

>[!TIP]
>
>In de volgende secties wordt beschreven hoe u de resultaten van de Experience Audit kunt bekijken.
>
>* Om meer details op te leren hoe de controlewerken, zie {de Details van de Evaluatie van de Controle van 0} Ervaring ](#details).[
>* Om te weten hoe te om een Controle van de Ervaring op bestelling in werking te stellen, zie [ Rapporten van de Controle op bestelling ](#on-demand).
>* Als u kwesties met de controle ervaart, zie [ de Uitdagingen van de Controle van de Ervaring ](#issues).
>* Voor algemene prestatiesuiteinden, zie [ Algemene Tips van Prestaties ](#performance-tips).

### De langzaamste pagina&#39;s weergeven {#view-slowest-pages}

Klik **de langzaamste pagina&#39;s van de Mening** om de **Langzaamste 5 pagina&#39;s** dialoogdoos te openen. De vijf laagste-presterende pagina&#39;s die u [ aan controle ](#configuration) wordt gevormd worden getoond.

![ langzaamst vijf ](assets/experience-audit-slowest-five.png)

Cloud Manager onderbreekt de scores door **Prestaties**, **Toegankelijkheid**, **Beste praktijken**, en **SEO**, die de afwijking van elke metrisch van de vorige controle tonen.

Standaard wordt het dialoogvenster geopend met de scores voor mobiele apparaten. U kunt Desktopscores zien gebruikend **Apparaten** knevel dichtbij de bovenkant van de dialoogdoos.

Het dialoogvenster geeft u een snel overzicht. Voor volledige details, klik **Volledige rapport van de Mening**.

### Het volledige rapport weergeven {#view-full-report}

U kunt het volledige Rapport van de Controle van de Ervaring bekijken door het volgende te doen:

* Klik **`View full report`** in de **[Langst 5 pagina&#39;s](#view-slowest-pages)** dialoog.
* Klik **`View full report`** wanneer het bekijken van de [ uitvoering van een pijpleiding ](#results).
* Klik het **lusje van Rapporten** in Cloud Manager.

Het **lusje van Rapporten** van Cloud Manager wordt geopend, tonend de **Controle van de Ervaring**.

![ de rapporten van de Controle van de Ervaring ](assets/experience-audit-reports.png)

Het verslag is opgesplitst in twee gebieden:

* **[de scores van de Pagina — trend](#trend)**
* **[het aftasten van de Controle van de Ervaring resultaten](#results)**

#### Paginascore — trend {#trend}

Door gebrek, is de geselecteerde mening voor **de scores van de Pagina — trend** **mediaanscores** voor **Laatste 6 maanden**.

Gebruik **Uitgezochte** en **drop-down van de Mening** bij de bovenkant en de bodem van de grafiekknop om pagina-specifieke details en verschillende tijdkaders, respectievelijk te selecteren. Klik **updatetrend** bij de bovenkant van de grafiek om de selecties toe te passen en de grafiek te verfrissen.

Wanneer u de muis over het diagram beweegt, wordt knopinfo weergegeven met de waarden voor de categorieën van Google Lighthouse op bepaalde tijdpunten.

![ Details van de Tendens ](assets/experience-audit-trend-details.png)

Als u op een bepaald tijdstip op het diagram klikt, wordt een pop-up geopend met details van die scan. Klik het **open aftasten van de ervaringscontrole** om te laden dat aftasten resultaten in de **[aftasten van de Controle van de Ervaring](#scan-results)** sectie.

![ Uitgezochte verschillende aftasten ](assets/experience-audit-open-scan.png)

#### Resultaten van de controle van de ervaring {#scan-results}

De **de aftastenresultaten van de Controle van de Ervaring** sectie geeft aanbevelingen op hoe te om uw score en details van alle gescande pagina&#39;s te verbeteren. Het bestaat uit twee delen:

* **[Recommendations](#recommendations)**
* **[Gescande pagina&#39;s](#scanned-pages)**

##### Recommendations {#recommendations}

De **Recommendations** sectie toont een gezamenlijke reeks inzichten. Door gebrek, worden de aanbevelingen voor **prestaties** getoond. Gebruik drop-down naast de **Recommendations** rubriek om in een andere categorie te veranderen.

![ Recommendations ](assets/experience-audit-recommendations.png)

Klik op het chevron voor een aanbeveling om details over het pictogram weer te geven.

![ details van de Aanbeveling ](assets/experience-audit-recommendations-details.png)

Indien beschikbaar, bevatten de uitgebreide aanbevelingen details ook het percentage van het effect van de aanbevelingen, helpen nadruk op de meest impactful veranderingen.

Klik de **verbinding van meningspagina&#39;s** in de detailsmening om de pagina&#39;s te zien waarop de aanbeveling van toepassing is.

![ Pagina&#39;s voor de aanbevelingsdetails ](assets/experience-audit-details-pages.png)

##### Gescande pagina&#39;s {#scanned-pages}

De **Gescande pagina&#39;s** sectie geeft details van scores op alle gescande pagina&#39;s. Gebruik **Vorige** en **Volgende** knopen aan pagina door de resultaten en kies op hoeveel de vertoning zou moeten pagineren.

![ Gescande pagina&#39;s ](assets/experience-audit-scanned-pages.png)

Klik de verbinding van een bepaalde pagina werkt de **Uitgezochte** filter van de [**scores van de Pagina bij — trendmatige** sectie ](#trend) en toont het **Scores &amp; aanbevelingen** lusje voor de geselecteerde pagina.

![ de resultaten van de Pagina ](assets/experience-audit-page-results.png)

Het **Ruwe rapporten** lusje geeft u scores voor elke controle van de pagina. Klik de rapportdatum in de **kolom van het Rapport van de Lighthouse** om een JSON- dossier van de ruwe gegevens terug te winnen.

![ Onbewerkt rapport ](assets/experience-audit-raw-reports.png)

Er wordt een nieuw tabblad in uw browser geopend, waarin u naar `https://googlechrome.github.io/lighthouse/viewer/` wordt geleid. Er wordt automatisch een ondertekende URL geladen met het Raw JSON-rapport voor Lighthouse voor de geselecteerde pagina, zodat u gedetailleerde inspecties kunt uitvoeren.

![ bekijkend onbewerkt rapport ](assets/experience-audit-view-raw-report.png)

## Controleverslagen op aanvraag {#on-demand}

Naast het worden in werking gesteld tijdens pijpleidingsuitvoering, kunnen de rapporten van de Controle van de Ervaring ook op bestelling worden geproduceerd. Deze optie is een goede oplossing om uw pagina&#39;s snel te scannen, zonder dat u een pijplijn hoeft uit te voeren.

Om een aftasten op bestelling in werking te stellen, navigeer aan het **lusje van Rapporten** om het volledige controlerapport te zien en dan de **aftasten** knoop te klikken.

![ Scannen op bestelling ](assets/experience-audit-on-demand.png)

De **aftasten van de Looppas** knoop wordt niet beschikbaar en met een klokpictogram wanneer een aftasten op bestelling reeds loopt.

![ Scannen op bestelling ](assets/experience-audit-on-demand-running.png)

De aftasten op bestelling brengen een Controle van de Ervaring voor de recentste 25 [ gevormde pagina&#39;s ](#configuration) teweeg en beëindigen typisch in een paar notulen.

Op voltooiing, wordt de scores grafiek automatisch bijgewerkt, en u kunt de resultaten precies zoals voor een aftasten van de pijpleidingsuitvoering inspecteren.

U kunt het scoregrafiek filtreren dat op het trekkertype door de **selecteur te gebruiken 0} Trigger {wordt gebaseerd.**

![ de filter van de Trekker ](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Een scan op aanvraag kan alleen worden gestart als de omgeving niet wordt verwijderd en er geen andere scans in behandeling zijn op dezelfde omgeving.

## Problemen met de controle van de ervaring {#issues}

Als [ pagina&#39;s u ](#configuration) vormde om worden gecontroleerd niet beschikbaar waren of er andere fouten in de controle waren, weerspiegelt de Controle van de Ervaring dit feit.

De pijpleiding toont een uitbreidbare foutensectie om de relatieve wegen URL te bekijken het niet kon toegang hebben.

![ Kwesties die door de Controle van de Ervaring worden ontmoet ](assets/experience-audit-issues.jpg)

Als het bekijken van het volledige rapport, worden de details getoond in de **[Scanresultaten van de Controle van de Ervaring](#results)** sectie, die ook uitzetbaar is.

![ Volledige rapportkwesties ](assets/experience-audit-issues-report.png)

De pagina&#39;s zijn mogelijk niet beschikbaar omdat:

* De configuratie blokkeert toegang.
* De pagina bestaat niet.
* De pagina wordt omgeleid waarvoor een andere verificatie dan basis vereist is.
* Er is een interne fout opgetreden.
* enz.

>[!TIP]
>
>[ die tot de ruwe rapporten ](#scanned-pages) voor een pagina toegang hebben kan details op verstrekken waarom de pagina niet kon worden gecontroleerd.

## Algemene prestatietips {#performance-tips}

Twee van de meest voorkomende problemen die eenvoudig te verhelpen zijn, hebben betrekking op Cumulatieve layoutverschuivingen (CLS) en de grootste inhoudelijke verf (LCP).

U kunt deze gebieden verbeteren door het volgende te doen:

* Het laden van de afbeeldingen boven de vouw is niet lui. Dit is de inhoud die in de browser zichtbaar is zonder dat u omlaag hoeft te schuiven.
* Correcte prioritering van de manier waarop bronnen worden geladen (bijvoorbeeld door de afbeeldingen asynchroon onder de voud te laden nadat het document is geladen).
* JavaScript- en CSS-bestanden die worden gebruikt om inhoud boven de vouw weer te geven (indien nodig).
* De verticale ruimte behouden door een hoogte-breedteverhouding toe te wijzen aan containers die langzaam worden geladen of later worden gerenderd.
* Afbeeldingen converteren naar WebP-indeling om de grootte ervan te beperken.
* Het gebruik van `<picture>` en de afbeelding `srcset` met verschillende afbeeldingsgrootten voor verschillende viewportgrootten (en om ervoor te zorgen dat het formaat werkt).

## Evaluatiegegevens controle van ervaring {#details}

De volgende details bieden aanvullende informatie over hoe de Experience Audit uw site evalueert. Ze zijn niet nodig voor algemeen gebruik van de functie en worden hier gegeven voor de volledigheid.

* De controle scant het oorsprongs (`.com`) domein van de [ gevormde de de paginawegen van de Controle van de Ervaring ](#configuration) van de uitgever om echte gebruikerservaringen te simuleren, die u helpen betere besluiten nemen over het beheren van en het optimaliseren van uw websites.
* Bij de productie van volledige-stapelpijpleidingen wordt de testomgeving gescand. Om ervoor te zorgen dat de controle relevante details tijdens de controle verstrekt, moet de inhoud van de testomgeving zo dicht mogelijk bij de productieomgeving liggen.
* De pagina&#39;s die in **worden getoond Uitgezochte** drop-down in de [**scores van de Pagina — trendmatige** sectie ](#trend) zijn alle bekende pagina&#39;s die de Controle van de Ervaring in het verleden wordt gescand.
* [ de aanbeveling van A ](#recommendations) kan een potentiële winst en een verschil van het vorige aftasten hebben.
* De controle van de ervaring schat potentiële verbeteringen door het ruwe rapport voor elke pagina te verwerken. Het correleert verspilde bytes of milliseconden met inzichten, die een gewogen effect op de prestatiesscore toewijzen. De controle verschaft deze informatie, en de betrokken pagina&#39;s, om te helpen beslissen welke aanbeveling moet worden gevolgd.
Zie de [ Algemene sectie van de Uiteinden van Prestaties ](#performance-tips) voor meer details.
* Een front-end pijpleiding kan aan een bestaand milieu opstellen, en de veelvoudige front-end pijpleidingen kunnen het zelfde milieu richten. Omdat de scanresultaten worden samengevoegd op het niveau van de omgeving, zijn de scores, trends en aanbevelingen consistent. Deze resultaten worden weergegeven in de geselecteerde omgeving, ongeacht welke pijpleiding de scan heeft geactiveerd.
