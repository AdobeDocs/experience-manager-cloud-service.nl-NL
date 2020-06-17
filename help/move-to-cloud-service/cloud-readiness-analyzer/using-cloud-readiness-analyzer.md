---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: 1d5023e49288cfa922f8fff8264b857ac66ec97a
workflow-type: tm+mt
source-wordcount: '1708'
ht-degree: 1%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen voor het uitvoeren van de Cloud Readiness Analyzer (CRA):

* Het CRA-rapport wordt samengesteld met behulp van de uitvoer van de [Patroondetector](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html)van de Adobe Experience Manager (AEM). De versie van Patroondetector die door CRA wordt gebruikt, is opgenomen in het installatiepakket van CRA.

* CRA kan slechts door de **admin** gebruiker of een gebruiker in de groep van **Beheerders** worden in werking gesteld.

* CRA wordt ondersteund op AEM-instanties met versie 6.1 en hoger.

* CRA kan op om het even welke milieu lopen, maar het verkiest om het op een milieu van het *Stadium* te laten lopen.

   >[!NOTE]
   >Om een effect op bedrijfskritieke instanties te vermijden, wordt u aangeraden om CRA uit te voeren op een *Auteur* -omgeving die zo dicht mogelijk bij de *Productieomgeving* ligt op het gebied van aanpassingen, configuraties, inhoud en gebruikerstoepassingen. Het kan ook worden uitgevoerd op een kloon van de *Auteur* -omgeving van de productie.

* Het genereren van CRA-rapportinhoud kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot een paar uur. De vereiste tijd is in hoge mate afhankelijk van de grootte en aard van de inhoud van de AEM-opslagplaats, de AEM-versie en andere factoren.

* Wegens de significante tijd die kan worden vereist om de rapportinhoud te produceren, worden zij geproduceerd door een achtergrondproces en in een geheim voorgeheugen gehouden. Het bekijken van en het downloaden van het rapport zou vrij snel moeten zijn omdat het het inhoudsgeheime voorgeheugen tot het verloopt of het rapport uitdrukkelijk wordt verfrist. Tijdens de generatie van rapportinhoud kunt u uw browser lusje sluiten en in een recentere tijd terugkeren om het rapport te bekijken zodra zijn inhoud in het geheime voorgeheugen beschikbaar is.

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer kan als zip- dossier van het Portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer van het portaal van de Distributie van de Software.

## Het Rapport van de Cloud Readiness Analyzer weergeven {#viewing-report}

### Adobe Experience Manager 6.3.0 en hoger {#aem-later-versions}

Ga als volgt te werk om het rapport Cloud Readiness Analyzer te bekijken:

1. Selecteer Adobe Experience Manager en navigeer naar gereedschappen -> **Bewerkingen** -> **Cloud Readiness Analyzer**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Nadat u op **Cloud Readiness Analyzer** hebt geklikt, genereert het programma het rapport en geeft het weer wanneer het beschikbaar is.

   >[!NOTE]
   >U moet naar beneden schuiven om het volledige rapport te kunnen bekijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-1.png)

1. Zodra het CRA- rapport wordt geproduceerd en getoond, hebt u de optie om het rapport in een komma-gescheiden waarden (CSV) formaat te downloaden door op **CSV** te klikken, zoals aangetoond in het hieronder cijfer.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-tool-2.png)

   >[!NOTE]
   >U kunt CRA dwingen om zijn geheime voorgeheugen te ontruimen en het rapport opnieuw te produceren door te klikken **verfrist Rapport**.

### Adobe Experience Managers 6.2 en 6.1 {#aem-specific-versions}

Het hulpprogramma Cloud Readiness Analyzer is in Adobe Experience Manager 6.2 beperkt tot een koppeling waarmee het CSV-rapport wordt gegenereerd en gedownload.

Voor Adobe Experience Manager 6.1 is het gereedschap niet functioneel en kan alleen de HTTP-interface worden gebruikt.

>[!NOTE]
>In alle versies kan de opgenomen Patroondetector onafhankelijk worden uitgevoerd.

## Het Rapport Cloud Readiness Analyzer interpreteren {#cra-report}

Wanneer het hulpprogramma Cloud Readiness Analyzer wordt uitgevoerd in de AEM-instantie, wordt het rapport als resultaten weergegeven in het gereedschapsvenster.

De vorm van het rapport is:

* **Overzicht** van rapport: Informatie over het rapport zelf, die de volgende informatie bevat:
   * **Rapporttijd**: Wanneer de rapportinhoud is gegenereerd en voor het eerst beschikbaar is gesteld.
   * **Vervaltijd**: Wanneer het geheime voorgeheugen van de rapportinhoud zal verlopen.
   * **Generatietijd**: De tijd die door het proces van de het genereren van de rapportinhoud wordt doorgebracht.
   * **Aantal** zoeken: Het totale aantal bevindingen in het verslag.
* **Systeemoverzicht**: Informatie over het AEM-systeem waarop het CRA is uitgevoerd.
* **Categorieën** zoeken: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie behandelt. Elk gedeelte bevat het volgende: Naam van categorie, subtypen, aantal en belang zoeken, overzicht, koppeling naar categoriedocumentatie en individuele zoekinformatie.

Aan elke bevinding wordt een belangrijk niveau toegewezen om een ruwe prioriteit voor actie aan te geven.

Volg de onderstaande tabel om inzicht te krijgen in de belangrijkste niveaus:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt ter informatie verstrekt. |
| ADVISORY | Deze bevinding is mogelijk een upgradeprobleem. Verdere onderzoeken worden aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| KRITIEK | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functieverlies of prestatieverlies te voorkomen. |


## Het CSV-rapport van de Cloud Readiness Analyzer interpreteren {#cra-csv-report}

Wanneer u op de optie **CSV** van uw AEM-instantie klikt, wordt de CSV-indeling van het rapport van de Cloud Readiness Analyzer gemaakt vanuit de inhoudcache en geretourneerd naar uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `results.csv`.

Als de cache is verlopen, wordt het rapport opnieuw gegenereerd voordat het CSV-bestand wordt gemaakt en gedownload.

De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de uitvoer van de patroondetector, gesorteerd en ingedeeld op categorietype, subtype en belangrijkheidsniveau. De indeling is geschikt voor weergave en bewerking in een toepassing zoals Microsoft Excel. Het is bedoeld om alle vindingsinformatie in een herhaalbaar formaat te verstrekken dat wanneer het vergelijken van rapporten in tijd kan nuttig zijn om vooruitgang te meten.

De kolommen van het CSV-indelingsrapport zijn:

* **code**: de categoriecode
* **type**: de categorienaam
* **subtype**: het subtype categorie
* **belang**: het belangrijkste niveau
* **id**: de primaire identificator van de bevinding
* **andere**: aanvullende informatie over de bevinding
* **bericht**: het bericht voor de bevinding
* **meerInfo**: een link die kan worden gebruikt om online hulp over de categorie te openen
* **context**: een JSON-reeks voor het zoeken van gegevens

De waarde &quot;\N&quot; in een kolom voor een individuele bevinding geeft aan dat er geen gegevens zijn opgegeven.

## HTTP-interface {#http-interface}

CRA verstrekt een interface van HTTP die als alternatief voor zijn gebruikersinterface binnen AEM kan worden gebruikt. De interface steunt zowel HEAD als GET bevelen. Het kan worden gebruikt om het rapport van CRA te produceren en het in één van drie formaten terug te keren: JSON, CSV en door tabs gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` de hostnaam en poort, indien nodig, van de server is waarop de CRA is geïnstalleerd:
* `http://<host>/apps/readiness-analyzer/analysis/result.json` voor JSON-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` voor CSV-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` voor TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-http-request}

De HTTP-interface kan in verschillende methoden worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregelprogramma gebruiken, zoals `curl` of `wget` elke HTTP-clienttoepassing. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u een beheergebruikersnaam en -wachtwoord opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`.

### Kopteksten en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>`: Geef de levensduur van de cache-versheid op in seconden. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Geeft aan dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

De volgende HTTP-queryparameters zijn beschikbaar als handig wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (nummer, optioneel): Geef de levensduur van de cache-versheid op in seconden. Dit getal moet 0 of hoger zijn. Het standaard versheidsleven is 86400 seconden, betekenend dat zonder deze parameter of de overeenkomstige kopbal een vers geheime voorgeheugen zal worden gebruikt om verzoeken voor 24 uren te dienen alvorens het rapport moet worden opnieuw geproduceerd. Het gebruiken `max-age=0` zal het geheime voorgeheugen dwingen om worden ontruimd en zal een regeneratie van het rapport in werking stellen. Onmiddellijk na dit verzoek wordt de versheidslevensduur teruggezet naar de vorige waarde die niet gelijk is aan nul.
* `respond-async` (Booleaans, optioneel): Geef op of de reactie asynchroon moet worden opgegeven. Het gebruiken `respond-async=true` wanneer het geheime voorgeheugen stale zal veroorzaken de server om een reactie van terug te keren `202 Accepted, processing cache` zonder het wachten op het te produceren rapport en het geheime voorgeheugen om worden verfrist. Als de cache vers is, heeft deze parameter geen effect. De standaardwaarde is `false`, dat wil zeggen dat zonder deze parameter of de corresponderende header de server synchroon zal reageren. Dit kan een aanzienlijke hoeveelheid tijd vereisen en een aanpassing van de maximale responstijd voor de HTTP-client vereisen.

Wanneer zowel een HTTP- kopbal als overeenkomstige vraagparameter aanwezig zijn, zal de vraagparameter belangrijkheid nemen.

Een eenvoudige manier om de generatie van het rapport via de interface van HTTP in werking te stellen is met het volgende bevel:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`.

Zodra een verzoek is ingediend, te hoeven de cliënt niet actief voor het te produceren rapport te blijven. De rapportgeneratie zou met één cliënt kunnen in werking worden gesteld gebruikend HTTP KRIJGT verzoek en, zodra het rapport is geproduceerd, bekeken van het geheime voorgeheugen in een andere cliënt of het hulpmiddel CSV in het gebruikersinterface binnen AEM.

### Reacties {#http-responses}

De volgende responswaarden zijn mogelijk:

* `200 OK`: De reactie bevat bevindingen van de Patroondetector die zijn gegenereerd binnen de versheidslevensduur van de cache.
* `202 Accepted, processing cache`: Opgegeven voor asynchrone reacties om aan te geven dat de cache leeg was en dat er een vernieuwingsbewerking wordt uitgevoerd.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met de aanvraag. Een bericht in het formaat van de Details van het Probleem (zie [RFC 7807](https://tools.ietf.org/html/rfc7807)) voor meer details.
* `401 Unauthorized`: Het verzoek is niet ingewilligd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in het formaat van de Details van het Probleem verstrekt meer details.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere reactie en dit verzoek niet tijdig kan uitvoeren. Dit zal alleen gebeuren wanneer synchrone verzoeken worden gedaan. Een bericht in het formaat van de Details van het Probleem verstrekt meer details.

## Aanpassing van levensduur cache {#cache-adjustment}

De standaard CRA geheim voorgeheugenlevensduur is 24 uren. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de instantie AEM als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk voor de meeste toepassingen van CRA aangewezen zijn. Als de tijd van de rapportgeneratie voor uw instantie AEM bijzonder lang is, kunt u het geheim voorgeheugenleven willen aanpassen om de regeneratie van het rapport te minimaliseren.

De waarde van het geheim voorgeheugenleven wordt opgeslagen als `maxCacheAge` bezit op de volgende gegevensopslagplaats knoop:
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan het geheim voorgeheugenleven aanpassen gebruikend CRX/DE Lite.





