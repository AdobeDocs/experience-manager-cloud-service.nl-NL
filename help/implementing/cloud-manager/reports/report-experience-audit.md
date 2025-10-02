---
title: Experience Audit Dashboard
description: Ontdek hoe de Controle van de Ervaring uw plaatsingsproces bevestigt, die ervoor zorgt dat de veranderingen basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO voldoen. Het verstrekt een duidelijke en informatieve dashboardinterface om deze metriek te volgen.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5f9d53958076b77cd333a042003c83853594db87
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 0%

---


# Experience Audit-dashboard {#experience-audit-dashboard}

<!-- Engineer architect over this feature was Bogdan Anton; scrum master Alexandru Nica -->

Ontdek hoe de Controle van de Ervaring uw plaatsingsproces bevestigt, die ervoor zorgt dat de veranderingen basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO (de Optimalisering van de Motor van het Onderzoek) voldoen. Het verstrekt een duidelijke en informatieve dashboardinterface om deze metriek te volgen.

## Overzicht {#overview}

De Controle van de ervaring bevestigt het plaatsingsproces en de hulp zorgt ervoor dat de veranderingen worden opgesteld:

1. Voldoet aan basislijnstandaarden voor prestaties, toegankelijkheid, aanbevolen procedures en SEO.
1. Breng geen regressies aan.

De controle van de ervaring in Cloud Manager zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Deze insight is waardevol om te bepalen of er een regressie is die met de huidige plaatsing werd geïntroduceerd.

De Controle van de ervaring wordt aangedreven door [&#x200B; Lighthouse van Google &#x200B;](https://developer.chrome.com/docs/lighthouse/overview/), een open bronhulpmiddel van Google, en in alle de productiepijpleidingen van Cloud Manager toegelaten.

## Beschikbaarheid {#availability}

Er is een Experience Audit beschikbaar voor Cloud Manager:

* (Standaard) Sites-productiepijpleidingen.
* (Optioneel) Ontwikkeling van pijpleidingen met volledige stapelcapaciteit.
* (Optioneel) Ontwikkeling van voorpijpleidingen.

Zie de [&#x200B; sectie van de Configuratie &#x200B;](#configuration) voor meer informatie over hoe te om de controle voor de facultatieve milieu&#39;s te vormen.

Audits worden uitgevoerd als onderdeel van de pijpleiding. De controles kunnen ook [&#x200B; in werking worden gesteld op bestelling &#x200B;](#on-demand) buiten pijpleidingen.

## Configuratie {#configuration}

De Experience Audit is standaard beschikbaar voor productiepijpleidingen. Het kan naar keuze voor ontwikkeling van volledig-stapel en front-end pijpleidingen worden toegelaten. In alle gevallen, moet u bepalen welke inhoudswegen tijdens pijpleidingsuitvoering worden geëvalueerd.

1. Afhankelijk van het type van pijpleiding u wilt vormen, doe één van het volgende:

   * [&#x200B; voeg een productiepijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) toe om de wegen te bepalen u de controle wilt evalueren.
   * [&#x200B; voeg een niet productiepijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) toe, als u de controle op een front-end of ontwikkelings volledig-stapelpijpleiding wilt toelaten.
   * [&#x200B; geef een bestaande pijpleiding &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) uit, en werk de bestaande opties bij.

1. Om de Controle van de Ervaring te gebruiken wanneer het toevoegen van of het uitgeven van een niet productiepijplijn, selecteer het **checkbox van de Controle van de Ervaring 0&rbrace;.** U kunt deze optie op het **Code van Source** lusje vinden.

   ![&#x200B; toelatend de Controle van de Ervaring &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-enable.jpg)

   * Alleen nodig voor niet-productiepijpleidingen.
   * Het **lusje van de Controle van de Ervaring** verschijnt wanneer checkbox wordt geselecteerd.

1. Voor zowel productie als niet productiepijpleidingen, bepaalt u de wegen die in de Controle van de Ervaring op de **Controle van de Ervaring** tabel moeten worden omvat.

   * Pagina-paden moeten beginnen met `/` en zijn relatief ten opzichte van uw site.
   * Als uw site bijvoorbeeld `wknd.site` is en u `https://wknd.site/us/en/about-us.html` wilt opnemen in de Experience Audit, voert u het pad in `/us/en/about-us.html` .

   ![&#x200B; die een weg voor de Controle van de Ervaring bepalen &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-add-page.png)

1. Klik **toevoegen de Pagina** en de weg is auto-voltooid met het adres van uw milieu en aan de lijst van wegen toegevoegd.

   ![&#x200B; het Opslaan weg aan de lijst &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-page-added.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klik **sparen**.

## Resultaten van controle door ervaring {#results}

De resultaten van de Controle van de Ervaring worden voorgesteld in de **testende fase van het Stadium** van de productiepijplijn door de [&#x200B; pagina van de de uitvoeringspijplijn van de productiepijplijn &#x200B;](/help/implementing/cloud-manager/deploy-code.md).

![&#x200B; Dashboard in de pijpleiding &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-dashboard.png)

De Controle van de ervaring verstrekt de mediane Emissiescore van Google voor de [&#x200B; gevormde pagina&#39;s &#x200B;](#configuration) en het verschil in score aan het vorige aftasten.

Van deze summiere mening in de **het Testen van het Stadium** fase van de pijpleiding, hebt u twee opties:

* **[Mening de langzaamste pagina&#39;s](#view-slowest-pages)**
* **[Mening het volledige rapport](#view-full-report)**

U kunt tot de volledige controleresultaten toegang hebben door het **lusje van Rapporten** in het dashboard van Cloud Manager te klikken. Naast de samenvatting die in de details van de pijpleidingslooppas wordt getoond, kunt u [&#x200B; het volledige rapport &#x200B;](#view-full-report) direct bekijken.

>[!TIP]
>
>In de volgende secties wordt beschreven hoe u de resultaten van de Experience Audit kunt bekijken.
>
>* Om meer details op te leren hoe de controlewerken, zie {de Details van de Evaluatie van de Controle van 0} Ervaring [.](#details)
>* Om te weten hoe te om een Controle van de Ervaring op bestelling in werking te stellen, zie [&#x200B; Rapporten van de Controle op bestelling &#x200B;](#on-demand).
>* Als u kwesties met de controle ervaart, zie [&#x200B; de Uitdagingen van de Controle van de Ervaring &#x200B;](#issues).

### De langzaamste pagina&#39;s weergeven {#view-slowest-pages}

Klik **de langzaamste pagina&#39;s van de Mening** om de **Langzaamste 5 pagina&#39;s** dialoogdoos te openen. De vijf laagste-presterende pagina&#39;s die u [&#x200B; aan controle &#x200B;](#configuration) wordt gevormd worden getoond.

![&#x200B; langzaamst vijf &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-slowest-five.png)

Cloud Manager onderbreekt de scores door **Prestaties**, **Toegankelijkheid**, **Beste praktijken**, en **SEO**, die de afwijking van elke metrisch van de vorige controle tonen.

Standaard wordt het dialoogvenster geopend met de scores voor mobiele apparaten. U kunt Desktopscores zien gebruikend **Apparaten** knevel dichtbij de bovenkant van de dialoogdoos.

Het dialoogvenster geeft u een snel overzicht. Voor volledige details, klik **Volledige rapport van de Mening**.

### Het volledige rapport weergeven {#view-full-report}

U kunt het volledige Rapport van de Controle van de Ervaring bekijken door het volgende te doen:

* Klik **`View full report`** in de **[Langst 5 pagina&#39;s](#view-slowest-pages)** dialoog.
* Klik **`View full report`** wanneer het bekijken van de [&#x200B; uitvoering van een pijpleiding &#x200B;](#results).
* Klik het **lusje van Rapporten** in Cloud Manager.

Het **lusje van Rapporten** van Cloud Manager wordt geopend, tonend de **Controle van de Ervaring**.

![&#x200B; de rapporten van de Controle van de Ervaring &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-reports.png)

Het verslag is opgesplitst in twee gebieden:

* **[de scores van de Pagina — trend](#trend)**
* **[het aftasten van de Controle van de Ervaring resultaten](#results)**

#### Paginascore — trend {#trend}

Door gebrek, is de geselecteerde mening voor **scores van de Pagina — trend** **mediaanscores** voor **Vorig jaar**.

U kunt de trends voor specifieke categorieën Lighthouse weergeven door op de categorienaam in de legenda te klikken.

![&#x200B; Keuze Trend &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-selectable.png)

Gebruik drop-down **Uitgezochte** bij de bovenkant van de grafiek om pagina-specifieke details te selecteren, en de **Mening** en **Trekker** drop-down bij de bodem om verschillende tijdkaders en het trekkertype te kiezen, respectievelijk.

De **drop-down Mening** biedt de mogelijkheid om een vooraf ingesteld tijdkader, of een douaneinterval voor een specifiekere mening te selecteren.

![&#x200B; Mening van de Trend &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-view.png)

Wanneer u de muis over het diagram beweegt, wordt knopinfo weergegeven met de waarden voor de categorieën van Google Lighthouse op bepaalde tijdpunten.

![&#x200B; Details van de Tendens &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-trend-details.png)

Als u op een bepaald tijdstip op het diagram klikt, wordt een pop-up geopend met details van die scan. Klik het **open aftasten van de ervaringscontrole** om te laden dat aftasten resultaten in de **[aftasten van de Controle van de Ervaring](#scan-results)** sectie.

![&#x200B; Uitgezochte verschillende aftasten &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-open-scan.png)

#### Resultaten van de controle van de ervaring {#scan-results}

De **sectie van de het aftasten van de Controle van de Ervaring** geeft details van scores op alle afgescande pagina&#39;s. Gebruik **Vorige** en **Volgende** knopen aan pagina door de resultaten en kies op hoeveel de vertoning zou moeten pagineren.

![&#x200B; Gescande pagina&#39;s &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-scanned-pages.png)

Klik de verbinding van een bepaalde pagina werkt de filter **Uitgezochte** van de [**scores van de Pagina bij — trendmatige** sectie &#x200B;](#trend) en toont het **Ruwe rapporten** lusje dat u scores voor elke controle van de pagina geeft. Klik de rapportdatum in de **kolom van het Rapport van de Lighthouse** om een JSON- dossier van de ruwe gegevens terug te winnen.

![&#x200B; Onbewerkt rapport &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-raw-reports.png)

Een nieuw tabblad dat in uw browser wordt geopend, leidt u naar `https://googlechrome.github.io/lighthouse/viewer/` . Er wordt automatisch een ondertekende URL geladen met het Raw JSON-rapport voor Lighthouse voor de geselecteerde pagina, zodat u gedetailleerde inspecties kunt uitvoeren.

![&#x200B; bekijkend onbewerkt rapport &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-view-raw-report.png)

## Controleverslagen op aanvraag {#on-demand}

Naast het worden in werking gesteld tijdens pijpleidingsuitvoering, kunnen de rapporten van de Controle van de Ervaring ook op bestelling worden geproduceerd. Deze optie is een goede oplossing om uw pagina&#39;s snel te scannen, zonder dat u een pijplijn hoeft uit te voeren.

Om een aftasten op bestelling in werking te stellen, navigeer aan het **lusje van Rapporten** zodat u het volledige controlerapport kunt zien, en dan de **aftasten van de Looppas** knoop klikken.

![&#x200B; Scannen op bestelling &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand.png)

De **aftasten van de Looppas** knoop wordt niet beschikbaar en met een klokpictogram wanneer een aftasten op bestelling reeds loopt.

![&#x200B; Scannen op bestelling &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-running.png)

De aftasten op bestelling brengen een Controle van de Ervaring voor de recentste 25 [&#x200B; gevormde pagina&#39;s &#x200B;](#configuration) teweeg en beëindigen typisch in een paar notulen.

Op voltooiing, wordt de scores grafiek automatisch bijgewerkt, en u kunt de resultaten precies zoals voor een aftasten van de pijpleidingsuitvoering inspecteren.

U kunt het scoregrafiek filtreren dat op het trekkertype door de **selecteur te gebruiken 0&rbrace; Trigger &lbrace;wordt gebaseerd.**

![&#x200B; de filter van de Trekker &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Een scan op aanvraag kan alleen worden gestart als de omgeving niet wordt verwijderd en er geen andere scans in behandeling zijn op dezelfde omgeving.

## Problemen met de controle van de ervaring {#issues}

Als [&#x200B; pagina&#39;s u &#x200B;](#configuration) vormde om worden gecontroleerd niet beschikbaar waren of er andere fouten in de controle waren, weerspiegelt de Controle van de Ervaring dit feit.

De pijpleiding toont een uitbreidbare foutensectie om de relatieve wegen URL te bekijken het niet kon toegang hebben.

![&#x200B; Kwesties die door de Controle van de Ervaring worden ontmoet &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-issues.png)

Als het bekijken van het volledige rapport, worden de details getoond in de **[Scanresultaten van de Controle van de Ervaring](#results)** sectie, die ook uitzetbaar is.

![&#x200B; Volledige rapportkwesties &#x200B;](/help/implementing/cloud-manager/reports/assets/experience-audit-issues-report.png)

De pagina&#39;s zijn mogelijk niet beschikbaar omdat:

* De configuratie blokkeert toegang.
* De pagina bestaat niet.
* De pagina wordt omgeleid waarvoor een andere verificatie dan basis vereist is.
* Er is een interne fout opgetreden.

>[!TIP]
>
>[&#x200B; die tot de ruwe rapporten &#x200B;](#scan-results) voor een pagina toegang hebben kan details op verstrekken waarom de pagina niet kon worden gecontroleerd.

## Gegevens van de evaluatie van de ervaring {#details}

De volgende details bieden aanvullende informatie over hoe de Experience Audit uw site evalueert. Ze zijn niet nodig voor algemeen gebruik van de functie en worden hier gegeven voor de volledigheid.

* De controle scant het oorsprongs (`.com`) domein van de [&#x200B; gevormde de de paginawegen van de Controle van de Ervaring &#x200B;](#configuration) van de uitgever om echte gebruikerservaringen te simuleren, die u helpen betere besluiten nemen over het beheren van en het optimaliseren van uw websites.
* Bij de productie van volledige-stapelpijpleidingen wordt de testomgeving gescand. Om ervoor te zorgen dat de controle relevante details tijdens de controle verstrekt, moet de inhoud van de testomgeving zo dicht mogelijk bij de productieomgeving liggen.
* De pagina&#39;s die in drop-down **worden getoond Uitgezocht** in de [**scores van de Pagina — trendmatige** sectie &#x200B;](#trend) zijn alle bekende pagina&#39;s die de Controle van de Ervaring in het verleden wordt gescand.
