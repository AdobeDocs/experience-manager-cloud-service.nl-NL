---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: d72f02f76f9be61ef4c3eefd790ff8abbb23a3d8
workflow-type: tm+mt
source-wordcount: '1812'
ht-degree: 1%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Cloud Readiness Analyzer (CRA):

* Het CRA-rapport wordt samengesteld met behulp van de uitvoer van de [Patroondetector](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html)van de Adobe Experience Manager (AEM). De versie van Patroondetector die door CRA wordt gebruikt, is opgenomen in het installatiepakket van CRA.

* De CRA kan alleen worden uitgevoerd door de `admin` gebruiker of een gebruiker in de `Administrators` groep.

* CRA wordt ondersteund op AEM-instanties met versie 6.1 en hoger.

* CRA kan op om het even welke milieu lopen, maar het verkiest om het op een milieu van het *Stadium* te laten lopen.

   >[!NOTE]
   >Om een impact op bedrijfskritieke instanties te vermijden, wordt aanbevolen om CRA uit te voeren op een *opvoeromgeving* die zo dicht mogelijk bij de productieomgeving ligt op het gebied van aanpassingen, configuraties, inhoud en gebruikerstoepassingen. Het kan ook worden uitgevoerd op een kloon van de *Auteur* -omgeving van de productie.

* Het genereren van het CRA-rapport kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot enkele uren. De vereiste tijd is in hoge mate afhankelijk van de grootte en aard van de inhoud van de AEM-opslagplaats, de AEM-versie en andere factoren.

* Wegens de significante tijd die wordt vereist om het rapport te produceren, worden de resultaten gehouden in een geheim voorgeheugen en zijn beschikbaar voor het verdere bekijken en het downloaden tot het geheime voorgeheugen verloopt of het rapport uitdrukkelijk wordt verfrist.

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer kan als zip- dossier van het Portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer van het Portaal van de Distributie van de Software *hangend*.

## De Cloud Readiness Analyzer uitvoeren {#running-tool}

Ga als volgt te werk om Cloud Readiness Analyzer uit te voeren:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Nadat u op **Cloud Readiness Analyzer** hebt geklikt, wordt het rapport gegenereerd en na enkele minuten is het samenvattingsrapport beschikbaar voor uw AEM-instantie.

   >[!NOTE]
   >U moet naar beneden schuiven om het volledige rapport te kunnen bekijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

### AEM 6.3 en hoger {#aem-older-version}

Voor AEM 6.3 en hoger is de primaire manier om Cloud Readiness Analyzer uit te voeren:

1. In de gebruikersinterface van de Adobe Experience Manager navigeert u naar Gereedschappen -> **Bewerkingen** -> **Cloud Readiness Analyzer**.

   >[!NOTE]
   >Het CRA zal een achtergrondproces beginnen om het rapport te produceren zodra het hulpmiddel wordt geopend. Het toont een aanwijzing dat de rapportgeneratie in proces is tot het rapport klaar is. U kunt het browsertabblad sluiten en later terugkeren om het rapport te bekijken wanneer het is voltooid.

Zodra het CRA- rapport is geproduceerd en getoond, hebt u de optie om het rapport in een komma-gescheiden formaat (CSV) te downloaden door de knoop **CSV** in de hogere juiste hoek van de hulpmiddelpagina te klikken.

U kunt CRA dwingen om zijn geheime voorgeheugen te ontruimen en het rapport opnieuw te produceren door de &quot;Refresh knoop van het Rapport&quot;in de hogere linkerhoek te klikken.

### AEM 6.2 en 6.1 {#aem-specific-versions}

De gebruikersinterface van CRA is beperkt in AEM 6.2 aan een verbinding die het CSV- rapport produceert en downloadt. Voor AEM 6.1 is de gebruikersinterface niet functioneel en kan alleen de HTTP-interface worden gebruikt.

In alle versies kan de opgenomen Patroondetector onafhankelijk worden uitgevoerd.

## CRA-overzichtsrapport {#cra-summary-report}

Wanneer CRA in het gebruikersinterface van AEM in werking wordt gesteld, wordt het rapport getoond als resultaten in het hulpmiddelvenster. De vorm van het rapport is:

* Overzicht van rapport: Informatie over het verslag zelf, ook wanneer het is opgesteld.
* Systeemoverzicht: Informatie over het AEM-systeem waarop het CRA is uitgevoerd.
* Categorieën zoeken: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie behandelt. Elk gedeelte bevat het volgende: Naam van categorie, subtypen, aantal en belang zoeken, overzicht, koppeling naar categoriedocumentatie en individuele zoekinformatie.

Aan elke bevinding wordt een belangrijk niveau toegewezen om een ruwe prioriteit voor actie aan te geven. De gebruikte hoeveelheden zijn als volgt:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt ter informatie verstrekt. |
| ADVISORY | Deze bevinding is mogelijk een upgradeprobleem. Verdere onderzoeken worden aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| KRITIEK | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functieverlies of prestatieverlies te voorkomen. |

## CRA CSV-rapport {#crs-csv-report}

Wanneer op de knop &quot;CSV&quot; wordt gedrukt, wordt de CSV-indeling van het CRA-rapport opgebouwd uit de resultaatcache en geretourneerd aan uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `results.csv`. Als de cache is verlopen, wordt het rapport opnieuw gegenereerd voordat het CSV-bestand wordt gemaakt en gedownload.

Voer de onderstaande stappen uit om een CSV-indeling van het samenvattingsrapport van uw AEM-instantie te genereren:

1. 
   1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

1. Zodra het rapport beschikbaar is, klik op **CSV** om het volledige samenvattingsrapport in komma-gescheiden waarden (CSV) formaat, zoals aangetoond in hieronder figuur te downloaden.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)

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

CRA verstrekt een interface van HTTP die als alternatief voor het gebruikersinterface AEM kan worden gebruikt. De interface steunt zowel HEAD als GET bevelen. Het kan worden gebruikt om het rapport van CRA te produceren en het in één van drie formaten terug te keren: JSON, CSV en door tabs gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` de hostnaam en poort, indien nodig, van de server is waarop de CRA is geïnstalleerd:
* `http://<host>/apps/readiness-analyzer/analysis/result.json` voor JSON-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.csv` voor CSV-indeling
* `http://<host>/apps/readiness-analyzer/analysis/result.tsv` voor TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-http-request}

De HTTP-interface kan in verschillende methoden worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregelprogramma gebruiken, zoals `curl` of `wget` elke HTTP-clienttoepassing. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u een beheergebruikersnaam en -wachtwoord opgeven als onderdeel van de opmerking. Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.csv' > result.csv`

### Kopteksten en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>`: Geef de levensduur van de cache-versheid op in seconden. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Geeft aan dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)

De volgende HTTP-queryparameters zijn beschikbaar als handig wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (nummer, optioneel): Geef de levensduur van de cache-versheid op in seconden. Dit getal moet 0 of hoger zijn. Het standaard versheidsleven is 86400 seconden, betekenend dat zonder deze parameter of de overeenkomstige kopbal een vers geheime voorgeheugen zal worden gebruikt om verzoeken voor 24 uren te dienen alvorens het rapport moet worden opnieuw geproduceerd. Het gebruiken `max-age=0` zal het geheime voorgeheugen dwingen om worden ontruimd en zal een regeneratie van het rapport in werking stellen. Onmiddellijk na dit verzoek wordt de versheidslevensduur teruggezet naar de vorige waarde die niet gelijk is aan nul.
* `respond-async` (Booleaans, optioneel): Geef op of de reactie asynchroon moet worden opgegeven. Het gebruiken `respond-async=true` wanneer het geheime voorgeheugen stale zal veroorzaken de server om een reactie van terug te keren `202 Accepted, processing cache` zonder het wachten op het te produceren rapport en het geheime voorgeheugen om worden verfrist. Als de cache vers is, heeft deze parameter geen effect. De standaardwaarde is `false`, dat wil zeggen dat zonder deze parameter of de corresponderende header de server synchroon zal reageren. Dit kan een aanzienlijke hoeveelheid tijd vereisen en een aanpassing van de maximale responstijd voor de HTTP-client vereisen.

Wanneer zowel een HTTP- kopbal als overeenkomstige vraagparameter aanwezig zijn, zal de vraagparameter belangrijkheid nemen.

Een eenvoudige manier om de generatie van het rapport via de interface van HTTP in werking te stellen is met het volgende bevel:
`curl -u admin:admin 'http://localhost:4502/apps/readiness-analyzer/analysis/result.json?max-age=0&respond-async=true'`

Zodra een verzoek is ingediend, te hoeven de cliënt niet actief voor het te produceren rapport te blijven. De rapportgeneratie zou met één cliënt kunnen in werking worden gesteld gebruikend HTTP KRIJGT verzoek en, zodra het rapport is geproduceerd, bekeken van het geheime voorgeheugen in een andere cliënt of het hulpmiddel CSV in het AEM gebruikersinterface.

### Reacties (#http-responses)

De volgende responswaarden zijn mogelijk:

* `200 OK`: De reactie bevat bevindingen van de Patroondetector die zijn gegenereerd binnen de versheidslevensduur van de cache.
* `202 Accepted, processing cache`: Opgegeven voor asynchrone reacties om aan te geven dat de cache leeg was en dat er een vernieuwingsbewerking wordt uitgevoerd.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met de aanvraag. Een bericht in het formaat van de Details van het Probleem (zie [RFC 7807](https://tools.ietf.org/html/rfc7807)) verstrekt meer details.
* `401 Unauthorized`: Het verzoek is niet ingewilligd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in het formaat van de Details van het Probleem verstrekt meer details.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere reactie en dit verzoek niet tijdig kan uitvoeren. Dit is slechts als voorkomen wanneer de synchrone verzoeken worden gemaakt. Een bericht in het formaat van de Details van het Probleem verstrekt meer details.

## Aanpassing van levensduur cache {#cache-adjustment}

De standaard CRA geheim voorgeheugenlevensduur is 24 uren. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de gebruikersinterface als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk voor de meeste toepassingen van CRA aangewezen zijn. Als de tijd van de rapportgeneratie voor uw instantie AEM bijzonder lang is, kunt u het geheim voorgeheugenleven willen aanpassen om de regeneratie van het rapport te minimaliseren.

De waarde van het geheim voorgeheugenleven wordt opgeslagen als `maxCacheAge` bezit op de volgende gegevensopslagplaats knoop:
`/apps/readiness-analyzer/content/CloudReadinessReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan het geheim voorgeheugenleven aanpassen gebruikend de interface CRX/DE Lite aan AEM.

## Het rapport bekijken in AEM 6.1 Instanties {#aem-instances-report}

Voer de onderstaande stappen uit om het CSV-rapport voor Adobe Experience Manager (AEM) 6.1 te downloaden:

1.Navigeer aan **Adobe Experience Manager Web ConsoleConfiguration** gebruikend `https://serveraddress:serverport/system/console/configMgr`.

1. Selecteer het tabblad **Status** en zoek in de vervolgkeuzelijst naar **Patroondetector** , zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-4.png)

1. U kunt het samenvattingsrapport downloaden in een ZIP-map of in JSON-indeling.


