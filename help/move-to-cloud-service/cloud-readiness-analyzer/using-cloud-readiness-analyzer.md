---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: a0e58c626f94b778017f700426e960428b657806
workflow-type: tm+mt
source-wordcount: '1871'
ht-degree: 89%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Bekijk de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen voor het uitvoeren van CRA (Cloud Readiness Analyzer):

* Het CRA-rapport wordt samengesteld met de uitvoer van de [Pattern Detector](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html)-functie van Adobe Experience Manager (AEM). De versie van Pattern Detector die door CRA wordt gebruikt, is opgenomen in het installatiepakket van CRA.

* CRA may only be run by the **admin** user or a user in the **administrators** group.

* CRA wordt ondersteund op AEM-instanties met versie 6.1 en hoger.

   >[!NOTE]
   > Zie [Installeren op AEM 6.1](#installing-on-aem61) voor speciale vereisten voor de installatie van CRA op AEM 6.1.

* CRA kan in elke omgeving worden uitgevoerd, maar de voorkeur gaat uit naar de *Stage*-omgeving.

   >[!NOTE]
   >Om de impact op bedrijfskritieke instanties zo beperkt mogelijk te houden, raden we aan dat u CRA uitvoert op een *auteur* omgeving die zoveel mogelijk overeenkomt met de *productieomgeving* op het gebied van aanpassingen, configuraties, content en gebruikersapplicaties. CRA kan ook worden uitgevoerd op een kloon van de *auteur* laag van de productieomgeving.

* Het maken van een CRA-rapport kan flink wat tijd in beslag nemen, van enkele minuten tot een paar uur. De benodigde tijd is in hoge mate afhankelijk van de grootte en aard van de AEM-repository-content, de AEM-versie en andere factoren.

* Vanwege de tijd die nodig is om de rapportinhoud te produceren, gebeurt dit in een achtergrondproces, waarbij de data in cache worden opgeslagen. Het bekijken en downloaden van het rapport gaat relatief snel, omdat hierbij de inhoud in het cachegeheugen wordt opgehaald, totdat het geheugen verloopt of het rapport uitdrukkelijk wordt vernieuwd. Tijdens de generatie van de rapportinhoud kunt u uw browsertabblad sluiten en later terugkeren om het rapport te bekijken zodra de inhoud in het cachegeheugen beschikbaar is.

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer kan als zip- dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer van de [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)-portal.

## Het Cloud Readiness Analyzer-rapport weergeven {#viewing-report}

### Adobe Experience Manager 6.3.0 en hoger {#aem-later-versions}

In deze sectie wordt beschreven hoe u het Cloud Readiness Analyzer-rapport bekijkt:

1. Selecteer Adobe Experience Manager en navigeer naar Tools -> **Operations** -> **Cloud Readiness Analyzer**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Zodra u op **Cloud Readiness Analyzer** klikt, wordt het rapport aangemaakt en vervolgens weergegeven.

   >[!NOTE]
   >U moet naar beneden schuiven om het volledige rapport te kunnen bekijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. Zodra het CRA- rapport is geproduceerd en wordt weergegeven, kunt u het rapport desgewenst in een CSV-indeling (door komma&#39;s gescheiden) downloaden. Klik hiervoor op **CSV**, zoals in de onderstaand afbeelding.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >Klik op **Refresh Report** om CRA te forceren het cachegeheugen te wissen en het rapport opnieuw te produceren.

### Adobe Experience Manager 6.2 en 6.1 {#aem-specific-versions}

De Cloud Readiness Analyzer-tool in Adobe Experience Manager 6.2 is beperkt tot een koppeling waarmee het CSV-rapport wordt gegenereerd en gedownload.

De tool werkt niet voor Adobe Experience Manager 6.1 en kan alleen via de HTTP-interface worden gebruikt.

>[!NOTE]
>In alle versies kan de opgenomen Pattern Detector-functie onafhankelijk worden uitgevoerd.

## Het Cloud Readiness Analyzer-rapport interpreteren {#cra-report}

Wanneer de Cloud Readiness Analyzer-tool wordt uitgevoerd in de AEM-instantie, worden de rapportresultaten weergegeven in het toolvenster.

Het rapport is als volgt ingedeeld:

* **Overzicht van rapport**: Informatie over het rapport zelf. het overzicht biedt de volgende gegevens:
   * **Tijd van rapport**: Tijdstip waarop de rapportinhoud is gegenereerd en voor het eerst beschikbaar gesteld.
   * **Vervaltijd**: Tijdstip waarop de cache-inhoud verloopt.
   * **Tijdsperiode voor genereren**: De benodigde tijd om de rapportinhoud te genereren.
   * **Aantal bevindingen**: Het totale aantal bevindingen in het rapport.
* **Systeemoverzicht**: Informatie over het AEM-systeem waarop CRA is uitgevoerd.
* **Categorieën voor bevindingen**: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie worden behandeld. Elke sectie bevat de volgende items: categorienaam, subtypen, aantal en belang, samenvatting, koppeling naar categoriedocumentatie en individuele informatie over de bevindingen.

Aan elke bevinding wordt een belangniveau toegewezen als ruwe prioriteit voor de benodigde actie.

Bekijk de onderstaande tabel om inzicht te krijgen in de belangniveaus:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt alleen ter informatie verstrekt. |
| ADVISORY | Deze bevinding vormt mogelijk een upgradeprobleem. Vervolgonderzoek wordt aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| CRITICAL | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functie- of prestatieverlies te voorkomen. |


## Het Cloud Readiness Analyzer CSV-rapport interpreteren {#cra-csv-report}

Wanneer u op de optie **CSV** van uw AEM-instantie klikt, wordt de CSV-indeling van het Cloud Readiness Analyzer-rapport gemaakt op basis van de inhoudcache en geretourneerd naar uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `results.csv`.

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

CRA biedt een HTTP-interface die kan worden gebruikt als alternatief voor de gebruikersinterface binnen AEM. Deze interface ondersteunt zowel HEAD- als GET-opdrachten. Met de HTTP-interface kunt u het CRA-rapport produceren en in drie indelingen retourneren: JSON, CSV en in door tabs gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` de hostnaam en, indien nodig, de poort is van de server is waarop CRA is geïnstalleerd:
* `http://<host>/apps/readiness-analyzer/analysis/result.json` voor de JSON-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` voor de CSV-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` voor de TSV-indeling

### Een HTTP-verzoek uitvoeren {#executing-http-request}

De HTTP-interface kan op een aantal manieren worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregeltool gebruiken, zoals `curl` of `wget`, of elk type HTTP-clientapplicatie. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u de naam en wachtwoord van een beheerder-gebruiker opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### Headers en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>`: De levensduur van de cache in seconden. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Geeft aan dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

De volgende handige HTTP-queryparameters zijn beschikbaar wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (getal, optioneel): Geeft de levensduur van de cache op in seconden. Dit getal moet 0 of hoger zijn. De standaardlevensduur is 86.400 seconden. Dit betekent dat een nieuwe cache, zonder deze parameter of overeenkomstige header, 24 uur lang kan worden gebruikt om verzoeken te &#39;bedienen&#39; voordat het rapport opnieuw moet worden geproduceerd. Door gebruik van `max-age=0` wordt de cache gewist en het rapport opnieuw gegenereerd. Onmiddellijk na dit verzoek wordt de versheidslevensduur teruggezet naar de vorige waarde die niet gelijk is aan nul.
* `respond-async` (Booleaans, optioneel): Geeft aan of de respons asynchroon moet worden aangeboden. Als u `respond-async=true` gebruikt wanneer de cache verouderd is, retourneert de server een respons van `202 Accepted, processing cache`. In dit geval wordt er niet gewacht op het opnieuw gegenereerde rapport of de vernieuwde cache. Als de cache vernieuwd is, heeft deze parameter geen effect. De standaardwaarde is `false`. Dit houdt in dat de server synchroon reageert als deze parameter of de overeenkomstige header niet worden toegepast. Dit kan erg lang duren en een aanpassing van de maximale responstijd voor de HTTP-client vereisen.

Wanneer zowel de HTTP-header en de overeenkomstige queryparameter aanwezig zijn, heeft de queryparameter prioriteit.

De volgende opdracht vormt een eenvoudige manier om de productie van het rapport via de HTTP-interface te starten:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Zodra een verzoek is ingediend, hoeft de client niet actief te zijn voor het produceren van het rapport. Het rapport kan worden gemaakt doordat één client een HTTP GET-verzoek indient. Nadat het rapport is gemaakt, kan het vanuit de cache worden bekeken door een andere client of in de CSV-tool in de gebruikersinterface binnen AEM.

### Respons {#http-responses}

De volgende responswaarden zijn mogelijk:

* `200 OK`: De respons bevat bevindingen van de Pattern Detector die zijn gegenereerd tijdens de vernieuwingslevensduur van de cache.
* `202 Accepted, processing cache`: Geboden bij asynchrone respons om aan te geven dat de cache verouderd is en dat er een vernieuwingsbewerking wordt uitgevoerd.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met het verzoek. Een bericht in de indeling voor probleemdetails (zie [RFC 7807](https://tools.ietf.org/html/rfc7807)) voor meer informatie.
* `401 Unauthorized`: Het verzoek is niet ingewilligd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in de indeling voor probleemdetails biedt meer informatie.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere respons en dit verzoek niet tijdig kan uitvoeren. Dit gebeurt alleen bij synchrone verzoeken. Een bericht in de indeling voor probleemdetails biedt meer informatie.

## Beheerdersgegevens

### Levensduur van cache aanpassen {#cache-adjustment}

Standaard is de levensduur van de CRA-cache 24 uur. Deze standaardwaarde is geschikt voor de meeste toepassingen van CRA. De gebruiker beschikt namelijk ook over de optie om een rapport te vernieuwen en de cache te regenereren, zowel in de AEM-instantie als in de HTTP-interface. Als het erg lang duurt om een rapport te maken in de AEM-instantie, kunt u de levensduur van de cache aanpassen om de regeneratie van het rapport te minimaliseren.

De waarde voor de levensduur is opgeslagen als de eigenschap `maxCacheAge` op de volgende repository-node:
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan de levensduur aanpassen met CRX/DE Lite.

### Installeren op AEM 6.1 {#installing-on-aem61}

CRA gebruikt een gebruikersrekening van de systeemdienst genoemd `repository-reader-service` om de Detector van het Patroon uit te voeren. Deze account is beschikbaar op AEM 6.2 en hoger. In AEM 6.1 moet dit account worden aangemaakt *voordat* een CRA kan worden geïnstalleerd door de volgende stappen uit te voeren:

1. Volg de instructies bij het [Creëren van een nieuwe de dienstgebruiker](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) om een gebruiker tot stand te brengen. Stel de gebruikersnaam in op `repository-reader-service` en laat het tijdelijke pad leeg en klik op het groene vinkje.

2. Volg de instructies bij het [Leiden Gebruikers en Groepen](https://docs.adobe.com/content/help/en/experience-manager-65/administering/security/security.html#managing-users-and-groups), specifiek de instructies voor het Toevoegen van Gebruikers aan een Groep om de `repository-reader-service` gebruiker aan de `administrators` groep toe te voegen.

3. Installeer het CRA-pakket via Package Manager op uw AEM-broninstantie. (Dit zal de noodzakelijke configuratiewijziging aan de configuratie ServiceUserMapper voor de gebruiker van de `repository-reader-service` systeemdienst toevoegen.)
