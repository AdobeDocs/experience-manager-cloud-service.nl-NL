---
title: Analysator van best practices gebruiken
description: Analysator van best practices gebruiken
translation-type: tm+mt
source-git-commit: ca6ee9c820c67b68c7498f2b0bad8c650b00562e
workflow-type: tm+mt
source-wordcount: '2207'
ht-degree: 47%

---


# Analysator van best practices gebruiken {#using-best-practices-analyzer}

## Belangrijke overwegingen voor het Gebruiken van Analyzer van Beste praktijken {#imp-considerations}

Volg de sectie hieronder om de belangrijke overwegingen voor het runnen van de Analysator van Beste praktijken (BPA) te begrijpen:

* The BPA report is built using the output of the Adobe Experience Manager (AEM) [Pattern Detector](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html). De versie van de Detector van het Patroon die door BPA wordt gebruikt is inbegrepen in het BPA installatiepakket.

* BPA may only be run by the **admin** user or a user in the **administrators** group.

* BPA wordt ondersteund op AEM instanties met versie 6.1 en hoger.

   >[!NOTE]
   > Please see [Installing on AEM 6.1](#installing-on-aem61) for special requirements for installing BPA on AEM 6.1.

* BPA can run on any environment, but it is preferred to have it run on a *Stage* environment.

   >[!NOTE]
   >In order to avoid an impact on business critical instances, it is recommended that you run BPA on an *Author* environment that is as close as possible to the *Production* environment in the areas of customizations, configurations, content and user applications. CRA kan ook worden uitgevoerd op een kloon van de *auteur* laag van de productieomgeving.

* Het genereren van de inhoud van het BPA-rapport kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot enkele uren. De benodigde tijd is in hoge mate afhankelijk van de grootte en aard van de AEM-repository-content, de AEM-versie en andere factoren.

* Vanwege de tijd die nodig is om de rapportcontent te produceren, gebeurt dit in een achtergrondproces, waarbij de data in cache worden opgeslagen. Het bekijken en downloaden van het rapport gaat relatief snel, omdat hierbij de content in het cachegeheugen wordt opgehaald, totdat het geheugen verloopt of het rapport uitdrukkelijk wordt vernieuwd. Tijdens de generatie van de rapportcontent kunt u uw browsertabblad sluiten en later terugkeren om het rapport te bekijken zodra de content in het cachegeheugen beschikbaar is.

## Beschikbaarheid {#availability}

De Analysator van Beste praktijken kan als zip dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download the Best Practices Analyzer from the [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portal.

## Het Rapport van de Analysator van Beste praktijken bekijken {#viewing-report}

### Adobe Experience Manager 6.3.0 en hoger {#aem-later-versions}

Volg deze sectie om te leren hoe te om het rapport van de Analysator van Beste praktijken te bekijken:

1. Select Adobe Experience Manager and navigate to tools -> **Operations** -> **Best Practices Analyzer**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic1.png)

1. Klik op Rapport **** genereren om de Analysator voor aanbevolen werkwijzen uit te voeren.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic2.png)

1. Terwijl BPA het rapport produceert, kunt u de vooruitgang zien die door het hulpmiddel op het scherm wordt gemaakt. Hier wordt het aantal geanalyseerde items weergegeven en ook het aantal gevonden bevindingen.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic3.png)


1. Zodra het BPA- rapport wordt geproduceerd, toont het een samenvatting en het aantal bevindingen in een tabelvorm die door het type van bevinding en het belangrijkheidsniveau wordt georganiseerd. Voor meer informatie over een bepaalde bevinding kunt u op het nummer klikken dat overeenkomt met het type bevinding in de tabel.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic4.png)

   De bovenstaande actie schuift automatisch naar de locatie van die bevinding in het rapport.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic5.png)

1. You have the option of downloading the report in a comma-separated values (CSV) format by clicking on **CSV**, as shown in the figure below.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic6.png)

   >[!NOTE]
   >You may force the BPA to clear its cache and regenerate the report by clicking **Refresh Report**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic7.png)

   >[!NOTE]
   >Tijdens het genereren van het rapport wordt de voortgang weergegeven in procenten dat is voltooid, zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/BPA_pic8.png)


### Adobe Experience Manager 6.2 en 6.1 {#aem-specific-versions}

Het hulpmiddel van de Analysator van Beste praktijken is beperkt in Adobe Experience Manager 6.2 aan een verbinding die het CSV- rapport produceert en downloadt.

De tool werkt niet voor Adobe Experience Manager 6.1 en kan alleen via de HTTP-interface worden gebruikt.

>[!NOTE]
>In alle versies kan de opgenomen Pattern Detector-functie onafhankelijk worden uitgevoerd.

## Het rapport met de analyse van best practices interpreteren {#cra-report}

Wanneer het hulpmiddel van de Analysator van Beste praktijken in de AEM instantie in werking wordt gesteld, wordt het rapport getoond als resultaten in het hulpmiddelvenster.

Het rapport is als volgt ingedeeld:

* **Overzicht van rapport**: Informatie over het rapport zelf. het overzicht biedt de volgende gegevens:
   * **Tijd van rapport**: Tijdstip waarop de rapportcontent is gegenereerd en voor het eerst beschikbaar gesteld.
   * **Vervaltijd**: Tijdstip waarop de cachecontent verloopt.
   * **Tijdsperiode voor genereren**: De benodigde tijd om de rapportcontent te genereren.
   * **Aantal bevindingen**: Het totale aantal bevindingen in het rapport.
* **Systeemoverzicht**: Informatie over het AEM systeem waarop BPA werd uitgevoerd.
* **Categorieën voor bevindingen**: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie worden behandeld. Elke sectie bevat de volgende items: categorienaam, subtypen, aantal en belang, samenvatting, koppeling naar categoriedocumentatie en individuele informatie over de bevindingen.

Aan elke bevinding wordt een belangniveau toegewezen als ruwe prioriteit voor de benodigde actie.

>[!NOTE]
>Zie Categorieën [patroondetector voor meer informatie over elke zoekcategorie](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html).

Bekijk de onderstaande tabel om inzicht te krijgen in de belangniveaus:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt alleen ter informatie verstrekt. |
| ADVISORY | Deze bevinding vormt mogelijk een upgradeprobleem. Vervolgonderzoek wordt aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| CRITICAL | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functie- of prestatieverlies te voorkomen. |


## Het CSV-rapport van de Analysator van best practices interpreteren {#cra-csv-report}

When you click the **CSV** option from your AEM instance, the CSV format of the Best Practices Analyzer report is built from the content cache and returned to your browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `results.csv`.

Als het cachegeheugen is verlopen, wordt het rapport opnieuw gegenereerd voordat het CSV-bestand wordt gemaakt en gedownload.

De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de Pattern Detector-uitvoer. Deze informatie is gesorteerd en ingedeeld op categorietype, subtype en belang. De indeling is geschikt voor weergave en bewerking in een applicatie zoals Microsoft Excel. De bedoeling is om alle bevindingen toegankelijk te maken in een herhaalbare indeling, zodat rapporten in de loop der tijd kunnen worden vergeleken om de vooruitgang te meten.

Het CSV-indelingsrapport bevat de volgende kolommen:

* **code**: De categoriecode
* **type**: De categorienaam
* **subtype**: Het subtype van de categorie
* **importance**: Het belang van de bevinding
* **identifier**: De primaire id van de bevinding
* **other**: Aanvullende informatie over de bevinding
* **message**: Het bericht dat voor de bevinding wordt verstrekt
* **moreInfo**: Een koppeling voor toegang tot online hulp over de categorie
* **context**: Een JSON-tekenreeks voor het zoeken naar data

De waarde &quot;\N&quot; in een kolom voor een individuele bevinding geeft aan dat er geen data zijn opgegeven.

## HTTP-interface {#http-interface}

BPA verstrekt een interface van HTTP die als alternatief aan zijn gebruikersinterface binnen AEM kan worden gebruikt. Deze interface ondersteunt zowel HEAD- als GET-opdrachten. Het kan worden gebruikt om het BPA- rapport te produceren en het in één van drie formaten terug te keren: JSON, CSV en door tabs gescheiden waarden (TSV).

The following URLs are available for HTTP access, where `<host>` is the hostname, and port if necessary, of the server on which the BPA is installed:
* `http://<host>/apps/best-practices-analyzer/analysis/report.json` voor de JSON-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.csv` voor de CSV-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.tsv` voor de TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-http-request}

De HTTP-interface kan op een aantal manieren worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregeltool gebruiken, zoals `curl` of `wget`, of elk type HTTP-clientapplicatie. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u de naam en wachtwoord van een beheerder-gebruiker opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

### Headers en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>`: Geeft de levensduur van de cachevervaging in seconden aan. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Geeft op dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal`: Geeft aan dat de server een minimale reactie moet retourneren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

De volgende handige HTTP-queryparameters zijn beschikbaar wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (nummer, optioneel): Geeft de levensduur van de cachevervaging in seconden aan. Dit getal moet 0 of hoger zijn. De standaard versheidslevensduur is 86400 seconden. Zonder deze parameter of de overeenkomstige kopbal zal een vers geheime voorgeheugen worden gebruikt om verzoeken gedurende 24 uren te dienen, waarbij het geheime voorgeheugen moet worden opnieuw geproduceerd. Het gebruiken `max-age=0` zal het geheime voorgeheugen dwingen om worden ontruimd en zal een regeneratie van het rapport in werking stellen, gebruikend het vorige niet-nul freshness leven voor het onlangs geproduceerde geheime voorgeheugen.
* `respond-async` (Booleaans, optioneel): Geeft op dat de reactie asynchroon moet worden opgegeven. Using `respond-async=true` when the cache is stale will cause the server to return a response of `202 Accepted` without waiting for the cache to be refreshed and for the report to be generated. Als de cache vernieuwd is, heeft deze parameter geen effect. The default value is `false`. Without this parameter or the corresponding header the server will respond synchronously, which may require a significant amount of time and require an adjustment to the maximum response time for the HTTP client.
* `may-refresh-cache` (Booleaans, optioneel): Geeft aan dat de server de cache kan vernieuwen als reactie op een aanvraag als de huidige cache leeg, leeg of bijna leeg is. Als `may-refresh-cache=true`, of als het niet wordt gespecificeerd, dan kan de server een achtergrondtaak in werking stellen die de Detector van het Patroon aanhaalt en het geheime voorgeheugen vernieuwt. Als `may-refresh-cache=false` dan zal de server geen verfrissingstaak in werking stellen die anders zou gedaan zijn als het geheime voorgeheugen leeg of verouderd is, in welk geval het rapport leeg zal zijn. Deze parameter heeft geen invloed op vernieuwingstaken die al in uitvoering zijn.
* `return-minimal` (Booleaans, optioneel): Geeft aan dat de reactie van de server alleen de status moet bevatten die de voortgangsindicatie en cachestatus in de JSON-indeling bevat. Als `return-minimal=true`, dan zal het reactievermogen tot het statusvoorwerp worden beperkt. Als `return-minimal=false`, of als het niet wordt gespecificeerd, zal een volledige reactie worden verstrekt.
* `log-findings` (Booleaans, optioneel): Specificeert dat de server de inhoud van het geheime voorgeheugen zou moeten registreren wanneer het eerst wordt gebouwd of verfrist. Elke bevinding in de cache wordt geregistreerd als een JSON-tekenreeks. Dit registreren zal slechts voorkomen als `log-findings=true` en het verzoek een nieuw geheime voorgeheugen produceert.

Wanneer zowel de HTTP-header en de overeenkomstige queryparameter aanwezig zijn, heeft de queryparameter prioriteit.

De volgende opdracht vormt een eenvoudige manier om de productie van het rapport via de HTTP-interface te starten:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Zodra een aanvraag is ingediend, hoeft de client niet actief te zijn voor het produceren van het rapport. De rapportgeneratie zou met één cliënt kunnen in werking worden gesteld gebruikend een verzoek van de GET van HTTP en, zodra het rapport is geproduceerd, bekeken van het geheime voorgeheugen met een andere cliënt of met het hulpmiddel BPA in het AEM gebruikersinterface.

### Respons {#http-responses}

De volgende responswaarden zijn mogelijk:

* `200 OK`: Geeft aan dat de reactie bevindingen van de Patroondetector bevat die zijn gegenereerd binnen de versheidslevensduur van de cache.
* `202 Accepted`: Wordt gebruikt om aan te geven dat de cache leeg is. Wanneer `respond-async=true` en `may-refresh-cache=true` deze reactie erop wijst dat verfrist taak lopend is. Wanneer `may-refresh-cache=false` deze reactie eenvoudig erop wijst dat het geheime voorgeheugen stabiel is.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met de aanvraag. A message in Problem Details format (see [RFC 7807](https://tools.ietf.org/html/rfc7807)) provides more details.
* `401 Unauthorized`: Geeft aan dat de aanvraag niet is geautoriseerd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in de indeling voor probleemdetails biedt meer informatie.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere respons en deze aanvraag niet tijdig kan uitvoeren. Dit gebeurt alleen bij synchrone aanvragen. Een bericht in de indeling voor probleemdetails biedt meer informatie.

## Beheerdersinformatie

### Levensduur van cache aanpassen {#cache-adjustment}

De standaardlevensduur van de BPA-cache is 24 uur. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de AEM instantie als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk voor de meeste toepassingen van BPA aangewezen zijn. Als het erg lang duurt om een rapport te maken in de AEM-instantie, kunt u de levensduur van de cache aanpassen om de regeneratie van het rapport te minimaliseren.

De langetermijnwaarde is opgeslagen als de eigenschap `maxCacheAge` op de volgende repository-node:
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan de levensduur aanpassen met CRX/DE Lite.

### Installeren op AEM 6.1 {#installing-on-aem61}

BPA utilizes a system service user account named `repository-reader-service` to execute the Pattern Detector. Dit account is beschikbaar op AEM 6.2 en hoger. On AEM 6.1, this account must be created *prior to* installation of BPA by taking the following steps:

1. Volg de instructies bij het [Nieuwe servicegebruiker maken](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) om een gebruiker te maken. Stel de UserID in op `repository-reader-service` en laat het tussenpad leeg en klik op het groene vinkje.

2. Volg de instructies bij [Gebruikers en groepen beheren](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security.html#managing-users-and-groups), met name de instructies voor het toevoegen van gebruikers aan een groep om de `repository-reader-service`-gebruiker aan de groep `administrators` toe te voegen.

3. Installeer het BPA-pakket via Package Manager op de bron-AEM. (Dit zal de noodzakelijke configuratiewijziging toevoegen aan de ServiceUserMapper-configuratie voor de gebruiker van de `repository-reader-service`-systeemservicegebruiker.)
