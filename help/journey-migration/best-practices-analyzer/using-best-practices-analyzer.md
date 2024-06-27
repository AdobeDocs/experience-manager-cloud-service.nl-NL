---
title: Analysator van best practices gebruiken
description: Leer hoe u de Analysator voor aanbevolen werkwijzen gebruikt om de gereedheid voor upgrades te begrijpen.
exl-id: e8498e17-f55a-4600-87d7-60584d947897
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2686'
ht-degree: 31%

---

# Analysator van best practices gebruiken {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="De Analysator van Beste praktijken gebruiken"
>abstract="Bekijk de documentatie voor het gebruik van de Analysator voor best practices (voorheen Cloud Readiness Analyzer) en het gegenereerde rapport. Het Rapport van de Analysator van Beste praktijken wordt gebruikt om een inzicht op hoog niveau van algemene verbeteringsbereidheid te bereiken."
>additional-url="https://my.adobeconnect.com/pqgrfezoxghs?proto=true" text="[Webinar] Introductie van tools om de reis naar Adobe Experience Manager as a Cloud Service te versnellen"

## Belangrijke overwegingen voor het Gebruiken van Analyzer van Beste praktijken {#imp-considerations}

Volg de sectie hieronder om de belangrijke overwegingen voor het runnen van de Analysator van Beste praktijken (BPA) te begrijpen:

* Het BPA-rapport wordt samengesteld met de uitvoer van de Adobe Experience Manager (AEM) [Patroondetector](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html). De versie van de Detector van het Patroon die door BPA wordt gebruikt is inbegrepen in het BPA installatiepakket.

* BPA mag alleen door de **admin** of een gebruiker in de **beheerders** groep.

* BPA wordt ondersteund op AEM instanties met versie 6.1 en hoger.

  >[!NOTE]
  >Zie [Installeren op AEM 6.1](#installing-on-aem61) voor speciale voorschriften voor de installatie van BPA op AEM 6.1.

* BPA kan op om het even welk milieu lopen, maar het wordt verkiest om het te hebben op een lopen *Werkgebied* milieu.

  >[!NOTE]
  >Om een effect op bedrijfskritieke instanties te vermijden, wordt u aangeraden BPA op een *Auteur* milieu dat zo dicht mogelijk bij de *Productie* omgeving op het gebied van aanpassingen, configuraties, inhoud en gebruikerstoepassingen. CRA kan ook worden uitgevoerd op een kloon van de *auteur* laag van de productieomgeving.

* Het genereren van de inhoud van het BPA-rapport kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot een paar uur. De benodigde tijd is in hoge mate afhankelijk van de grootte en aard van de AEM-repository-content, de AEM-versie en andere factoren.

* Vanwege de tijd die nodig is om de rapportcontent te produceren, gebeurt dit in een achtergrondproces, waarbij de data in cache worden opgeslagen. Het bekijken en downloaden van het rapport gaat relatief snel, omdat hierbij de content in het cachegeheugen wordt opgehaald, totdat het geheugen verloopt of het rapport uitdrukkelijk wordt vernieuwd. Tijdens de generatie van de rapportcontent kunt u uw browsertabblad sluiten en later terugkeren om het rapport te bekijken zodra de content in het cachegeheugen beschikbaar is.

## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_download"
>title="Download de Analyzer van Beste praktijken"
>abstract="De Analysator van Beste praktijken kan als zip dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager)."

De Analysator van Beste praktijken kan als zip dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket installeren via [Pakketbeheer](/help/implementing/developing/tools/package-manager.md) op uw bron-Adobe Experience Manager (AEM)-exemplaar.

>[!NOTE]
>Download de Best Practices Analyzer van de [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) portaal.

## Connectiviteit Source-omgeving {#source-environment-connectivity}

De bron AEM instantie kan achter een firewall lopen waar het slechts bepaalde gastheren kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u het BPA-gegenereerde rapport automatisch naar Cloud Acceleration Manager wilt uploaden, moeten de volgende eindpunten toegankelijk zijn vanaf de instantie die AEM uitvoert:

* De Azure-opslagservice: `casstorageprod.blob.core.windows.net`


## Het Rapport van de Analysator van Beste praktijken bekijken {#viewing-report}

### Adobe Experience Manager 6.3.0 en hoger {#aem-later-versions}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa_upload_setup"
>title="Upload het rapport Best Practices Analyzer automatisch naar CAM"
>abstract="Geef de uploadsleutel voor BPA op om het gegenereerde BPA-rapport automatisch te uploaden naar Cloud Acceleration Manager (CAM)."

Volg deze sectie om te leren hoe te om het rapport van de Analysator van Beste praktijken te bekijken:

1. Selecteer Adobe Experience Manager en navigeer naar gereedschappen > **Bewerkingen** > **Analysator van best practices**.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_pic1.png)

1. Klikken **Rapport genereren** om de Analysator van Beste praktijken uit te voeren.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_pic2.png)

1. Geef de BPA-upload-sleutel op om het gegenereerde BPA-rapport automatisch te uploaden naar [Cloud Acceleration Manager (CAM)](/help/journey-migration/cloud-acceleration-manager/introduction/benefits-cam.md). Navigeer naar de knop [Analyse van beste praktijken in CAM](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key.png)

>[!NOTE]
>U kunt automatisch uploaden naar CAM overslaan door **Rapport automatisch uploaden naar CAM overslaan**. Als u verkiest om over te slaan, zult u het BPA- rapport als komma-gescheiden waardedossier manueel moeten downloaden en dan het dossier in CAM uploaden. Het wordt aanbevolen de optie Upload key te gebruiken omdat deze de bewerking stroomlijnt.

1. De **Genereren** wordt geactiveerd wanneer een geldige toets wordt opgegeven. Klikken op **Genereren** om rapportgeneratie in werking te stellen.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key1.png)


1. Terwijl BPA het rapport produceert, kunt u de vooruitgang zien die door het hulpmiddel op het scherm wordt gemaakt. De voortgang wordt weergegeven in procenten dat is voltooid. Ook wordt het aantal geanalyseerde items weergegeven en wordt het aantal gevonden bevindingen weergegeven.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_generate_upload.png)

>[!NOTE]
>De tijdstempel van de BPA-upload met sleutelvervaldatum wordt in de rechterbovenhoek weergegeven. U zou BPA moeten vernieuwen uploadt sleutel wanneer het bijna zijn vervaldatum is. Als u de toets wilt vernieuwen, klikt u op **Vernieuwen** om naar CAM te navigeren om de sleutel te vernieuwen.

1. Nadat het BPA-rapport is gegenereerd, worden een samenvatting en het aantal bevindingen weergegeven in een tabelvorm die is ingedeeld op basis van het type bevinding en het belangrijkste niveau. Voor meer informatie over een bepaalde bevinding kunt u op het nummer klikken dat overeenkomt met het type bevinding in de tabel.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)

1. U kunt het rapport downloaden in de indeling CSV (comma-separated values, door komma&#39;s van elkaar gescheiden waarden) door op **Exporteren naar CSV**. U kunt het rapport ook weergeven in CAM door op **Ga naar CAM**. Hiermee gaat u naar de [Analyse van best practices](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis) pagina in CAM.

U kunt BPA dwingen om zijn geheime voorgeheugen te ontruimen en het rapport opnieuw te produceren door te klikken **Rapport vernieuwen**.

![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)


1. Als het geheime voorgeheugen verloopt, hebt u de optie om het laatste geproduceerde rapport in CAM te bekijken door op te klikken **Bekijk het laatste geproduceerde rapport in CAM** of stel een nieuwe rapportgeneratie in door op **Nieuw rapport genereren**.

![afbeelding](/help/journey-migration/best-practices-analyzer/assets/BPA_regeneratereport.png)


#### Het gebruiken van Filters in het Rapport van de Analysator van Beste praktijken {#bpa-filters}

Bevindingen met betrekking tot [ACS-opdrachten](https://adobe-consulting-services.github.io/acs-aem-commons/)volgt u de onderstaande stappen:

1. Klik op het linkerspoorpictogram aan de linkerkant van de pagina. Hiermee wordt het dialoogvenster **ACS-opdrachtfilter**. Klik op de knop **ACS-opdrachtfilter** om het interactieve selectievakje weer te geven, zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/report_filter_1.png)

   >[!NOTE]
   >Het linkerspoorpictogram zal verschijnen slechts als BPA het gebruik van ACSCommons ontdekt.

1. Schakel het selectievakje uit om alle bevindingen met betrekking tot ACS-opdrachten uit te filteren. U dient een **Aantal gefilterde zoekopdrachten** in het rapport zoals weergegeven in onderstaande afbeelding. Het filter wordt ook toegepast op het rapport wanneer het in een komma-gescheiden-waarde (CSV) formaat wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/report_filter_2.png)

   >[!NOTE]
   >De bevindingen van de ACS-Gemeenschappelijke Gemeenschap moeten niet worden genegeerd. Zie [documentatie](https://adobe-consulting-services.github.io/acs-aem-commons/pages/compatibility.html#aem-as-a-cloud-service-feature-incompatibility) om de compatibiliteit met AEM as a Cloud Service te bepalen.

<!--
### Adobe Experience Manager 6.2 and 6.1 {#aem-specific-versions}
 
The Best Practices Analyzer tool is limited in Adobe Experience Manager 6.2 to a link that generates and downloads the CSV report.

For Adobe Experience Manager 6.1, the tool is not functional and only the HTTP interface may be used.

>[!NOTE]
>In all versions, the included Pattern Detector may run independently.
-->

## Het rapport met de analyse van best practices interpreteren {#cra-report}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_interpreting"
>title="Het rapport met de analyse van best practices interpreteren"
>abstract="Er zijn twee opties om BPA- rapportoutput te bekijken: UI en CSV. Wanneer het hulpmiddel van de Analysator van Beste praktijken in de AEM instantie in werking wordt gesteld, wordt het rapport UI getoond als resultaten in het hulpmiddelvenster. De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de uitvoer van de patroondetector, gesorteerd en ingedeeld op categorietype, subtype en belangrijkheidsniveau."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#analysis-report" text="Rapport Analyse van beste praktijken"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html" text="De categorieën van het Rapport van de Analyse van Beste praktijken begrijpen"

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
>Meer over elke het Vinden Categorie leren, zie [Categorieën patroondetector](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html).

Bekijk de onderstaande tabel om inzicht te krijgen in de belangniveaus:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt alleen ter informatie verstrekt. |
| ADVISORY | Deze bevinding vormt mogelijk een upgradeprobleem. Vervolgonderzoek wordt aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| CRITICAL | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functie- of prestatieverlies te voorkomen. |

## Het CSV-rapport van de Analysator van best practices interpreteren {#cra-csv-report}

Wanneer u op de knop **CSV** van uw AEM instantie, wordt het formaat CSV van het rapport van de Analysator van Beste praktijken gebouwd van het inhoudsgeheime voorgeheugen en teruggekeerd aan uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam: `results.csv`.

Als het geheime voorgeheugen is verlopen, dan wordt het rapport opnieuw geproduceerd alvorens het Csv- dossier wordt gebouwd en gedownload.

De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de Pattern Detector-uitvoer. Deze informatie is gesorteerd en ingedeeld op categorietype, subtype en belang. De indeling is geschikt voor weergave en bewerking in een applicatie zoals Microsoft Excel. Het is bedoeld om alle vindingsinformatie in een herhaalbare formaat te verstrekken dat wanneer het vergelijken van rapporten in tijd kan nuttig zijn om vooruitgang te meten.

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

BPA verstrekt een interface van HTTP die als alternatief aan zijn gebruikersinterface binnen AEM kan worden gebruikt. Deze interface ondersteunt zowel HEAD- als GET-opdrachten. Het kan worden gebruikt om het BPA- rapport te produceren en het in één van drie formaten terug te keren: JSON, CSV, en lusje-gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` is hostname, en haven indien nodig, van de server waarop BPA wordt geïnstalleerd:
* `http://<host>/apps/best-practices-analyzer/analysis/report.json` voor de JSON-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.csv` voor de CSV-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.tsv` voor de TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-http-request}

De HTTP-interface kan op een aantal manieren worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregelprogramma gebruiken, zoals `curl` of `wget` en elke HTTP-clienttoepassing. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u de naam en wachtwoord van een beheerder-gebruiker opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

### Kopteksten en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>`: Geeft de levensduur van de cache-versheid in seconden aan. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async`: Geeft op dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal`: Geeft aan dat de server een minimale reactie moet retourneren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

De volgende handige HTTP-queryparameters zijn beschikbaar wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (getal, optioneel): geeft de levensduur van de cacheverversheid op in seconden. Dit getal moet 0 of hoger zijn. De standaard versheidslevensduur is 86400 seconden. Zonder deze parameter of de overeenkomstige kopbal, wordt een vers geheime voorgeheugen gebruikt om verzoeken voor 24 uren te dienen, waarbij het geheime voorgeheugen moet worden opnieuw geproduceerd. Gebruiken `max-age=0` zal dwingen het geheime voorgeheugen wordt ontruimd en een regeneratie van het rapport in werking stellen, gebruikend het vorige niet-nul freshness leven voor het pas geproduceerde geheime voorgeheugen.
* `respond-async` (Booleaans, optioneel): geeft aan dat de reactie asynchroon moet worden opgegeven. Gebruiken `respond-async=true` wanneer de cache leeg is, retourneert de server een reactie van `202 Accepted` zonder te wachten op het geheime voorgeheugen om worden verfrist en op het rapport wordt geproduceerd. Als de cache vernieuwd is, heeft deze parameter geen effect. De standaardwaarde is `false`. Zonder deze parameter of de overeenkomstige kopbal zal de server synchroon antwoorden, die een significante hoeveelheid tijd kan vereisen en een aanpassing van de maximumreactietijd voor de cliënt van HTTP vereisen.
* `may-refresh-cache` (Booleaans, optioneel): Geeft aan dat de server de cache kan vernieuwen als reactie op een aanvraag als de huidige cache leeg, verouderd of binnenkort leeg is. Indien `may-refresh-cache=true`of als deze niet is opgegeven, kan de server een achtergrondtaak starten die de Patroondetector oproept en de cache vernieuwt. Indien `may-refresh-cache=false` dan zal de server geen verfrissingstaak in werking stellen die anders zou gedaan zijn als het geheime voorgeheugen leeg of verouderd is, in welk geval het rapport leeg is. Deze parameter heeft geen invloed op vernieuwingstaken die al in uitvoering zijn.
* `return-minimal` (Booleaans, optioneel): geeft aan dat de reactie van de server alleen de status moet bevatten die de voortgangsindicatie en cachestatus in de JSON-indeling bevat. Indien `return-minimal=true`dan is de responsinstantie beperkt tot het statusobject. Indien `return-minimal=false`, of als het niet wordt gespecificeerd, dan wordt een volledige reactie verstrekt.
* `log-findings` (Booleaans, optioneel): geeft aan dat de server de inhoud van de cache moet vastleggen wanneer deze voor het eerst wordt gemaakt of vernieuwd. Elke bevinding via de cache wordt geregistreerd als een JSON-tekenreeks. Dit registreren zal slechts voorkomen als `log-findings=true` en de aanvraag genereert een nieuwe cache.

Wanneer zowel de HTTP-header en de overeenkomstige queryparameter aanwezig zijn, heeft de queryparameter prioriteit.

De volgende opdracht vormt een eenvoudige manier om de productie van het rapport via de HTTP-interface te starten:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Zodra een aanvraag is ingediend, hoeft de client niet actief te zijn voor het produceren van het rapport. De rapportgeneratie zou met één cliënt kunnen in werking worden gesteld gebruikend een verzoek van de GET van HTTP en, zodra het rapport is geproduceerd, bekeken van het geheime voorgeheugen met een andere cliënt of met het hulpmiddel BPA in het AEM gebruikersinterface.

### Reacties {#http-responses}

De volgende responswaarden zijn mogelijk:

* `200 OK`: Geeft aan dat de reactie bevindingen van de Patroondetector bevat die zijn gegenereerd binnen de versheidslevensduur van de cache.
* `202 Accepted`: Wordt gebruikt om aan te geven dat de cache leeg is. Wanneer `respond-async=true` en `may-refresh-cache=true` deze reactie wijst erop dat een verfrissingstaak lopend is. Wanneer `may-refresh-cache=false` dit antwoord wijst eenvoudig erop dat het geheime voorgeheugen stabiel is.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met de aanvraag. Een bericht in de indeling Probleemdetails (zie [RFC 7807](https://tools.ietf.org/html/rfc7807)) bevat meer details.
* `401 Unauthorized`: Geeft aan dat de aanvraag niet is geautoriseerd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in de indeling voor probleemdetails biedt meer informatie.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere respons en deze aanvraag niet tijdig kan uitvoeren. Dit gebeurt alleen bij synchrone aanvragen. Een bericht in de indeling voor probleemdetails biedt meer informatie.

## Beheerdersinformatie

### Aanpassing van levensduur cache {#cache-adjustment}

De standaardlevensduur van de BPA-cache is 24 uur. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de AEM instantie als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk voor de meeste toepassingen van BPA aangewezen zijn. Als de tijd van de rapportgeneratie voor uw AEM instantie bijzonder lang is, kunt u het geheim voorgeheugenleven willen aanpassen om de regeneratie van het rapport te minimaliseren.

De langetermijnwaarde is opgeslagen als de eigenschap `maxCacheAge` op de volgende repository-node:
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan de levensduur aanpassen met CRX/DE Lite.

### Installeren op AEM 6.1 {#installing-on-aem61}

BPA gebruikt een genoemde rekening van de systeemdienstgebruiker `repository-reader-service` om de Patroondetector uit te voeren. Dit account is beschikbaar op AEM 6.2 en hoger. Op AEM 6.1 moet dit account worden aangemaakt *vóór* installatie van BPA door de volgende stappen te nemen:

1. Volg de instructies bij het [Nieuwe servicegebruiker maken](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) om een gebruiker te maken. Stel de UserID in op `repository-reader-service` en laat het tussenpad leeg en klik op het groene vinkje.

2. Volg de instructies bij [Gebruikers en groepen beheren](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#managing-users-and-groups), met name de instructies voor het toevoegen van gebruikers aan een groep om de `repository-reader-service`-gebruiker aan de groep `administrators` toe te voegen.

3. Installeer het BPA-pakket via Package Manager op de bron-AEM. (Dit zal de noodzakelijke configuratiewijziging toevoegen aan de ServiceUserMapper-configuratie voor de gebruiker van de `repository-reader-service`-systeemservicegebruiker.)
