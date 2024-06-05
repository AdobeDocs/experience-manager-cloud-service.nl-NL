---
title: Experience Audit Dashboard
description: Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO door een duidelijke, informatieve dashboardinterface voldoen.
exl-id: 6d33c3c5-258c-4c9c-90c2-d566eaeb14c0
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1958'
ht-degree: 0%

---


# Experience Audit Dashboard {#experience-audit-dashboard}

Leer hoe de Controle van de Ervaring uw plaatsingsproces valideert en helpt ervoor te zorgen dat de ingevoerde veranderingen aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, en SEO door een duidelijke, informatieve dashboardinterface voldoen.

>[!NOTE]
>
>Deze functie is alleen beschikbaar voor [het programma voor vroegtijdige adoptie .](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)
>
>Raadpleeg het document voor meer informatie over de bestaande functie Experience Audit voor AEM as a Cloud Service [Ervaring controleren testen](/help/implementing/cloud-manager/experience-audit-testing.md)

## Overzicht {#overview}

De Controle van de ervaring bevestigt het plaatsingsproces en de hulp zorgt ervoor dat de ingevoerde veranderingen:

1. Voldoe aan basislijnnormen voor prestaties, toegankelijkheid, beste praktijken, SEO (de Optimalisering van de Motor van het Onderzoek), en PWA (de Progressieve App van het Web).

1. Breng geen regressies aan.

De controle van de ervaring in de Manager van de Wolk zorgt ervoor dat de ervaring van de gebruiker op de plaats van de hoogste normen is.

De controleresultaten zijn informatief en staan de plaatsingsmanager toe om de scores en de verandering tussen de huidige en vorige scores te zien. Dit inzicht is waardevol om te bepalen als er een regressie is die met de huidige plaatsing werd geïntroduceerd.

De controle van de ervaring wordt aangedreven door [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/), een opensource-programma uit Google, en is ingeschakeld in alle productiepijpleidingen van Cloud Manager.

## Beschikbaarheid {#availability}

Experience Audit is beschikbaar voor Cloud Manager:

* Sites, productiepijpleidingen, standaard
* De volledige pijpleidingen van de ontwikkeling, facultatief
* Ontwikkeling front-end pijpleidingen, optioneel

Zie de [Configuratiesectie](#configuration) voor meer informatie over hoe te om de controle voor de facultatieve milieu&#39;s te vormen.

Audits worden uitgevoerd als onderdeel van de pijpleiding. Audits kunnen ook [op aanvraag worden uitgevoerd](#on-demand) buiten de pijpleidingen.

## Configuratie {#configuration}

De Experience Audit is standaard beschikbaar voor productiepijpleidingen. Het kan naar keuze voor ontwikkeling volledig-stapel en front-end pijpleidingen worden toegelaten. In alle gevallen, moet u bepalen welke inhoudswegen tijdens pijpleidingsuitvoering worden geëvalueerd.

1. Afhankelijk van het type van pijpleiding u wenst te vormen, volg de richtingen aan:

   * Een nieuwe toevoegen [productiepijpleiding,](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) als u de wegen wilt bepalen die door de controle moeten worden geëvalueerd.
   * Een nieuwe toevoegen [niet-productiepijpleiding,](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) als u wenst om de controle op een front-end of ontwikkelings volledig-stapelpijpleiding toe te laten.
   * Of u kunt [een bestaande pijpleiding bewerken;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) en werkt de bestaande opties bij.

1. Als u toevoegt of een niet productiepijplijn uitgeeft waarvoor u de Controle van de Ervaring wilt gebruiken, moet u selecteren **Experience Audit** Selectievakje op de **Broncode** tab.

   ![Ervaring controleren inschakelen](assets/experience-audit-enable.jpg)

   * Dit is alleen nodig voor niet-productiepijpleidingen.
   * De **Experience Audit** wordt weergegeven wanneer het selectievakje is ingeschakeld.

1. Voor zowel productie als niet productie pijpleidingen, bepaalt u de wegen die in de Controle van de Ervaring op moeten worden omvat **Experience Audit** tab.

   * Pagina-paden moeten beginnen met `/` en zijn relatief ten opzichte van uw site.
   * Als uw site bijvoorbeeld `wknd.site` en zou graag `https://wknd.site/us/en/about-us.html` Voer in de Experience Audit het pad in `/us/en/about-us.html`.

   ![Een pad definiëren voor de Experience Audit](assets/experience-audit-add-page.png)

1. Tik of klik op **Pagina toevoegen** en het pad wordt automatisch ingevuld met het adres van de omgeving en toegevoegd aan de padlijst.

   ![Pad naar tabel opslaan](assets/experience-audit-page-added.png)

1. U kunt paden naar wens toevoegen door de vorige twee stappen te herhalen.

   * U kunt maximaal 25 paden toevoegen.
   * Als u geen paden definieert, wordt de homepage van de site standaard opgenomen in de Experience Audit.

1. Klikken **Opslaan** om uw pijpleiding te redden.

## Resultaten controle ervaring {#results}

De resultaten van de Experience Audit worden weergegeven in de **Werkgebied testen** fase van de productiepijpleiding via de [pagina voor de uitvoering van de productiepijplijn.](/help/implementing/cloud-manager/deploy-code.md)

![Dashboard in pijplijn](assets/experience-audit-dashboard.jpg)

De Experience Audit biedt de mediane Google Lighthouse scores voor de [geconfigureerde pagina&#39;s](#configuration) en het verschil in score met de vorige scan.

Uit deze overzichtsweergave in het dialoogvenster **Werkgebiedtests** de fase van de pijpleiding, hebt u twee opties:

* **[Langzaamste pagina&#39;s weergeven](#view-slowest-pages)**
* **[Volledig rapport weergeven](#view-full-report)**

Naast de samenvatting die in de details van een pijpleidingslooppas wordt voorgesteld, kunt u tot de volledige resultaten van de controle ook direct toegang hebben door **Rapporten** tabblad van het dashboard voor Cloud Manager voor toegang [het volledige verslag](#view-full-report) rechtstreeks.

>[!TIP]
>
>In de volgende secties wordt beschreven hoe u de resultaten van de Experience Audit kunt bekijken.
>
>* Zie de sectie voor meer informatie over de manier waarop de controle werkt [De Gegevens van de Evaluatie van de Controle van de ervaring.](#details)
>* Als u wilt weten hoe u een ervaringscontrole op aanvraag kunt uitvoeren, raadpleegt u de sectie [Controleverslagen op aanvraag.](#on-demand)
>* Als u problemen ondervindt met de controle, raadpleegt u de sectie [De controle van de ervaring ontmoet kwesties.](#issues)
>* Zie de sectie voor algemene prestatietips [Algemene prestatietips.](#performance-tips)

### Langzame pagina&#39;s weergeven {#view-slowest-pages}

Tikken of klikken **Langzaamste pagina&#39;s weergeven** opent de **Langzaam 5 pagina&#39;s** wordt weergegeven met de vijf pagina&#39;s die u het slechtst presteert [geconfigureerd voor controle.](#configuration)

![Langzaamste vijf](assets/experience-audit-slowest-five.jpg)

De scores zijn onderverdeeld op **Prestaties**, **Toegankelijkheid**, **Aanbevolen procedures**, en **SEO** samen met de afwijking van elke meeteenheid ten opzichte van de laatste controle.

Standaard wordt het dialoogvenster geopend met de scores voor mobiele apparaten. U kunt dit wijzigen in desktopscores met de opdracht **Apparaten** bovenaan in het dialoogvenster schakelen.

Het dialoogvenster is bedoeld voor een snel overzicht. Tik of klik op **Volledig rapport weergeven**.

### Volledig rapport weergeven {#view-full-report}

U kunt het volledige rapport van de Controle van de Ervaring bekijken door:

* Tikken of klikken **Volledig rapport weergeven** in de **[Langzaam 5 pagina&#39;s](#view-slowest-pages)** in.
* Tikken of klikken **Volledig rapport weergeven** wanneer u de [uitvoering van een pijpleiding.](#results)
* Tikken of klikken op de knop **Rapporten** in Cloud Manager.

De **Rapporten** tabblad van Cloud Manager wordt geopend, met daarin de **Ervaring audit**.

![Ervaringsauditverslagen](assets/experience-audit-reports.png)

Het verslag is opgesplitst in twee gebieden:

* **[Paginascore - trend](#trend)**
* **[De resultaten van de controle van de ervaring](#results)**

#### Paginascore - trend {#trend}

Standaard wordt de geselecteerde weergave **Paginascore - trend** is **mediaanscores** voor de **Laatste 6 maanden**.

Gebruik de **Selecteren** en **Weergave** drop-down bij de bovenkant en de bodem van de grafiekknop om pagina-specifieke details en verschillende tijdkaders, respectievelijk te selecteren. Tik of klik op de knop **trend bijwerken** knoop bij de bovenkant van de grafiek om de selecties toe te passen en de grafiek te verfrissen.

Wanneer u de muis over het diagram beweegt, wordt knopinfo weergegeven met de waarden voor de categorieën van Google Lighthouse op bepaalde tijdpunten.

![Details van trend](assets/experience-audit-trend-details.png)

Als u op een bepaald moment op het diagram tikt of op het diagram klikt, wordt een pop-up geopend met details van de scan. Tik of klik op de knop **auditscan met open ervaring** om de resultaten van die scan in de **[De resultaten van de controle van de ervaring](#scan-results)** sectie.

![Andere scan selecteren](assets/experience-audit-open-scan.png)

#### Resultaten van controle door ervaring {#scan-results}

De **De resultaten van de controle van de ervaring** in deze sectie worden aanbevelingen gedaan voor het verbeteren van de score en voor het weergeven van details over alle gescande pagina&#39;s. Het bestaat uit twee delen:

* **[Recommendations](#recommendations)**
* **[Gescande pagina&#39;s](#scanned-pages)**

##### Recommendations {#recommendations}

De **Recommendations** in dit gedeelte wordt een geaggregeerde set inzichten weergegeven. Door gebrek, aanbevelingen voor **prestaties** worden weergegeven. Gebruik de vervolgkeuzelijst naast de knop **Recommendations** om naar een andere categorie te gaan.

![Recommendations](assets/experience-audit-recommendations.png)

Tik op het chevron of klik op een aanbeveling om details ervan weer te geven.

![Aanbevelingen](assets/experience-audit-recommendation-details.png)

Indien beschikbaar, bevatten de uitgebreide aanbevelingen details ook het percentage van het effect van de aanbevelingen, helpen nadruk op de meest impactful veranderingen.

Tik of klik op de knop **pagina&#39;s weergeven** in de weergave Details de pagina&#39;s bekijken waarop de aanbeveling van toepassing is.

![Pagina&#39;s voor de details van de aanbeveling](assets/experience-audit-details-pages.png)

##### Gescande pagina&#39;s {#scanned-pages}

De **Gescande pagina&#39;s** in deze sectie worden de detailscores voor alle gescande pagina&#39;s weergegeven. U kunt de **Vorige** en **Volgende** knoppen om door de resultaten te bladeren en te bepalen hoeveel de weergave moet pagineren.

![Gescande pagina&#39;s](assets/experience-audit-scanned-pages.png)

Als u op de koppeling van een bepaalde pagina tikt of erop klikt, wordt het dialoogvenster **Selecteren** filter van de [**Paginascore - trend** sectie](#trend) en toont de **Scores en aanbevelingen** voor de geselecteerde pagina.

![Paginaresultaten](assets/experience-audit-page-results.png)

De **Raw-rapporten** geeft u scores voor elke controle van de pagina. Tik of klik op de knop **Downloaden** om een JSON-bestand met de onbewerkte gegevens op te halen.

![Raw-rapport](assets/experience-audit-raw-reports.png)

Hiermee wordt een nieuw tabblad in uw browser geopend, waarin naar `https://googlechrome.github.io/lighthouse/viewer/` met een ondertekende URL van het rapport JSON (Raw JavaScript Object Notation) voor de geselecteerde pagina, die automatisch wordt geopend voor uw gedetailleerde inspectie

![Raw-rapport weergeven](assets/experience-audit-view-raw-report.png)

## Controleverslagen op aanvraag {#on-demand}

Naast het worden in werking gesteld tijdens pijpleidingsuitvoering, kunnen de rapporten van de Controle van de Ervaring ook op bestelling worden geproduceerd. Dit is een goede oplossing om uw pagina&#39;s snel af te tasten, zonder het moeten een pijpleiding in werking stellen.

Navigeer naar de  **Rapporten** om het volledige auditrapport te bekijken en dan tikken of klikken op **Scan uitvoeren** knop.

![Scannen op aanvraag](assets/experience-audit-on-demand.png)

Scans op aanvraag activeren een Experience Audit voor de nieuwste 25 [geconfigureerde pagina&#39;s](#configuration) en wordt meestal binnen een paar minuten voltooid.

Na voltooiing wordt het scorediagram automatisch bijgewerkt en kunt u de resultaten precies zo controleren als bij een scan van de uitvoering van een pijpleiding.

U kunt het scores-diagram filteren op basis van het triggertype met de opdracht **Trigger** kiezer.

![Trigger, filter](assets/experience-audit-on-demand-trigger.png)

>[!NOTE]
>
>Een scan op aanvraag kan alleen worden gestart als de omgeving niet wordt verwijderd en er geen andere scans in behandeling zijn op dezelfde omgeving.

## Problemen met de controle van de ervaring {#issues}

Indien [pagina&#39;s die u hebt geconfigureerd](#configuration) die niet konden worden gecontroleerd, blijkt uit de ervaringscontrole dat dit het geval is.

De pijpleiding toont een uitbreidbare foutensectie om de relatieve wegen URL te bekijken het niet kon toegang hebben.

![Problemen ondervonden door Experience Audit](assets/experience-audit-issues.jpg)

Als u het volledige rapport weergeeft, worden de details weergegeven in het dialoogvenster **[De resultaten van de controle van de ervaring](#results)** sectie.

![Volledige rapportkwesties](assets/experience-audit-issues-reports.jpeg)

De pagina&#39;s zijn mogelijk niet beschikbaar omdat:

* De configuratie blokkeert toegang.
* De pagina bestaat niet.
* De pagina wordt omgeleid waarvoor een andere verificatie dan basis vereist is.
* Er is een interne fout opgetreden.
* enz.

>[!TIP]
>
>[De onbewerkte rapporten openen](#scanned-pages) voor een pagina kunt u aangeven waarom de pagina niet kon worden gecontroleerd.

## Algemene prestatietips {#performance-tips}

Twee van de meest voorkomende problemen die eenvoudig te verhelpen zijn, hebben betrekking op Cumulatieve layoutverschuivingen (CLS) en de grootste inhoudelijke verf (LCP).

Deze kunnen worden verbeterd door:

* Laad de afbeeldingen niet lui boven de vouw (de inhoud is zichtbaar in de browser zonder dat u omlaag hoeft te schuiven).
* Correcte prioritering van de manier waarop bronnen worden geladen (bijvoorbeeld door de afbeeldingen onder de voud asynchroon te laden nadat het document is geladen).
* JavaScript- en CSS-bestanden die worden gebruikt om inhoud boven de vouw weer te geven (indien nodig), vooraf instellen.
* De verticale ruimte behouden door een hoogte-breedteverhouding toe te wijzen aan containers die langzaam worden geladen of later worden gerenderd.
* Afbeeldingen converteren naar WebP-indeling om de grootte ervan te beperken.
* Gebruiken `<picture>` en afbeelding `srcset` met verschillende afbeeldingsgrootten voor verschillende viewportgrootten (en zorgen dat de grootte werkt).

## Evaluatiegegevens controle van ervaring {#details}

De volgende details bieden aanvullende informatie over hoe de Experience Audit uw site evalueert. Ze zijn niet nodig voor algemeen gebruik van de functie en worden hier gegeven voor de volledigheid.

* Hoewel de [gevormde de de de paginaden van de Controle van de Ervaring](#configuration) tonen `.com` het domein van de uitgever, de controle scant de oorsprong (`.net`), om ervoor te zorgen dat tijdens de ontwikkeling geïntroduceerde problemen worden gedetecteerd.
   * De `.com` gebruikt een CDN en levert betere scores op of bevat resultaten in cache.
* Bij de productie van volledige-stapelpijpleidingen wordt de testomgeving gescand.
   * Om ervoor te zorgen dat de audit relevante details verschaft tijdens de controle, moet de inhoud van de testomgeving zo dicht mogelijk bij de productieomgeving liggen.
* De pagina&#39;s die worden weergegeven in het dialoogvenster **Selecteren** vervolgkeuzelijst [**Paginascore - trend** sectie](#trend) Dit zijn alle bekende pagina&#39;s die in het verleden zijn gescand door de Experience Audit.
* [Een aanbeveling](#recommendations) kan een potentiële winst en een verschil met vorige aftasten hebben.
   * De Controle van de ervaring schat de potentiële winst door het ruwe rapport voor elke pagina te verwerken en correlerend de verspilde bytes of milliseconden met een inzicht dat een gewogen effect op de prestatiesscore heeft.
   * De controle verschaft deze informatie (en de betrokken pagina&#39;s) om te helpen beslissen welke aanbeveling moet worden gevolgd.
   * Zie voor meer informatie de [Sectie Algemene prestatietips](#performance-tips)
* Aangezien een frontend pijpleiding aan een bestaand milieu (of er veelvoudige frontend pijpleidingen die zich richten op het zelfde milieu) zou kunnen opstellen, en de aftastenresultaten worden samengevoegd op een milieuniveau, worden de scores, de tendensen, en de aanbevelingen getoond in het zelfde geselecteerde milieu, ongeacht de pijpleidingsuitvoering die de aftasten teweegbracht.
