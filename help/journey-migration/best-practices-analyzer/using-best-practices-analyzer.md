---
title: Analysator van best practices gebruiken
description: Leer hoe u de Analysator voor aanbevolen werkwijzen gebruikt om de gereedheid voor upgrades te begrijpen.
exl-id: e8498e17-f55a-4600-87d7-60584d947897
feature: Migration
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2796'
ht-degree: 30%

---

# Analysator van best practices gebruiken {#using-best-practices-analyzer}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_using"
>title="De Analysator van Beste praktijken gebruiken"
>abstract="Bekijk de documentatie voor het gebruik van de Analysator voor best practices (voorheen Cloud Readiness Analyzer) en het gegenereerde rapport. Het Rapport van de Analysator van Beste praktijken wordt gebruikt om een inzicht op hoog niveau van algemene verbeteringsbereidheid te bereiken."
>additional-url="https://my.adobeconnect.com/pqgrfezoxghs?proto=true" text="[Webinar] Introductie van tools om de reis naar Adobe Experience Manager as a Cloud Service te versnellen"

## Belangrijke overwegingen voor het Gebruiken van Analyzer van Beste praktijken {#imp-considerations}

Volg de sectie hieronder om de belangrijke overwegingen voor het runnen van de Analysator van Beste praktijken (BPA) te begrijpen:

* Het BPA- rapport wordt gebouwd gebruikend de output van de Detector van het Patroon van Adobe Experience Manager (AEM) [&#x200B; &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html). De versie van de Detector van het Patroon die door BPA wordt gebruikt is inbegrepen in het BPA installatiepakket.

* BPA kan slechts door de **admin** gebruiker of een gebruiker in de **beheerders** groep worden in werking gesteld.

* BPA wordt ondersteund op AEM-instanties met versie 6.1 en hoger.

  >[!NOTE]
  >Zie [&#x200B; Installerend op AEM 6.1 &#x200B;](#installing-on-aem61) voor speciale vereisten voor het installeren van BPA op AEM 6.1.

* BPA kan op om het even welk milieu in werking stellen, maar het heeft de voorkeur om het op het milieu van het a *Stadium* te hebben.

  >[!NOTE]
  >Om een effect op bedrijfskritieke instanties te vermijden, adviseert men dat u BPA op een *milieu van het Stadium* in werking stelt dat zo dicht mogelijk aan het *milieu van de Productie* op de gebieden van aanpassingen, configuraties, inhoud en gebruikerstoepassingen is. CRA kan ook worden uitgevoerd op een kloon van de *auteur* laag van de productieomgeving.

* Het genereren van de inhoud van het BPA-rapport kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot een paar uur. De benodigde tijd is in hoge mate afhankelijk van de grootte en aard van de AEM-repository-content, de AEM-versie en andere factoren.

* Vanwege de tijd die nodig is om de rapportcontent te produceren, gebeurt dit in een achtergrondproces, waarbij de data in cache worden opgeslagen. Het bekijken en downloaden van het rapport gaat relatief snel, omdat hierbij de content in het cachegeheugen wordt opgehaald, totdat het geheugen verloopt of het rapport uitdrukkelijk wordt vernieuwd. Tijdens de generatie van de rapportcontent kunt u uw browsertabblad sluiten en later terugkeren om het rapport te bekijken zodra de content in het cachegeheugen beschikbaar is.

## Beschikbaarheid {#availability}

>[!CONTEXTUALHELP]
>id="aemcloud_bpa_download"
>title="Download de Analyzer van Beste praktijken"
>abstract="De Analysator van Beste praktijken kan als zip dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager)."

De Analysator van Beste praktijken kan als zip dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via [&#x200B; Manager van het Pakket &#x200B;](/help/implementing/developing/tools/package-manager.md) op uw bronAdobe Experience Manager (AEM) instantie installeren.

>[!NOTE]
>Download de Analysator van Beste praktijken van het [&#x200B; portaal van de Distributie van de Software &#x200B;](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html).

## Connectiviteit Source-omgeving {#source-environment-connectivity}

De AEM-broninstantie wordt mogelijk achter een firewall uitgevoerd, waarbij deze alleen bepaalde hosts kan bereiken die aan een Lijst van gewenste personen zijn toegevoegd. Als u het BPA-gegenereerde rapport automatisch naar Cloud Acceleration Manager wilt uploaden, moeten de volgende eindpunten toegankelijk zijn vanaf de instantie waarop AEM wordt uitgevoerd:

* De Azure-opslagservice: `casstorageprod.blob.core.windows.net`


## Het Rapport van de Analysator van Beste praktijken bekijken {#viewing-report}

### Adobe Experience Manager 6.3.0 en hoger {#aem-later-versions}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_bpa_upload_setup"
>title="Upload het rapport Best Practices Analyzer automatisch naar CAM"
>abstract="Geef de uploadsleutel voor BPA op om het gegenereerde BPA-rapport automatisch te uploaden naar Cloud Acceleration Manager (CAM)."

Volg deze sectie om te leren hoe te om het rapport van de Analysator van Beste praktijken te bekijken:

1. Selecteer Adobe Experience Manager en navigeer aan hulpmiddelen > **Verrichtingen** > **Analysator van Beste praktijken**.

   ![&#x200B; Analyzer van Beste praktijken &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_pic1.png)

1. Klik **produceren Rapport** om de Analysator van Beste praktijken uit te voeren.

   ![&#x200B; produceer Rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_pic2.png)

>[!NOTE]
> Vanaf BPA versie 2.1.54 is een nieuwe functie geïntroduceerd om de Lighthouse Score te verkrijgen.


1. Na het klikken **produceer Rapport**, zal een pop-up het verzoeken van de Openbare Plaats URL van AEM voor de Score van de Lichter verschijnen. De gebruiker moet een geldige URL invoeren in het opgegeven veld.

   ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/bpa_popup_url.png)

   1. Als de URL geldig is, wordt een succesbericht weergegeven.

      ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/valid_url.png)

   1. Als de URL ongeldig is, wordt een foutbericht weergegeven.

      ![afbeelding](/help/journey-migration/best-practices-analyzer/assets/invalid_url.png)

1. Verstrek BPA upload sleutel om het geproduceerde BPA- rapport aan [&#x200B; Cloud Acceleration Manager (CAM) &#x200B;](/help/journey-migration/cloud-acceleration-manager/introduction/benefits-cam.md) automatisch te uploaden. Om uploadt sleutel te krijgen, navigeer aan de [&#x200B; Analyse van Beste praktijken in CAM &#x200B;](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis)

   ![&#x200B; plaats BPA uploadt Sleutel &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key.png)

>[!NOTE]
>U hebt de optie om automatisch over te slaan uploadt aan CAM door **te selecteren overslaat rapport auto uploadt aan CAM**. Als u verkiest om over te slaan, zult u het BPA- rapport als komma-gescheiden waardedossier manueel moeten downloaden en dan het dossier in CAM uploaden. Het wordt aanbevolen de optie Upload key te gebruiken omdat deze de bewerking stroomlijnt.

>[!IMPORTANT]
>Wanneer het manueel uploaden aan CAM, zijn de rapportgrootte beperkt tot ongeveer 200MB. Voor grotere rapporten moet u de automatische upload gebruiken.

1. **produceer** knoop actief wordt wanneer een geldige sleutel wordt verstrekt. Klik op **produceren** om rapportgeneratie in werking te stellen.

   ![&#x200B; produceer Rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_upload_key1.png)

1. Terwijl BPA het rapport produceert, kunt u de vooruitgang zien die door het hulpmiddel op het scherm wordt gemaakt. De voortgang wordt weergegeven in procenten dat is voltooid. Ook wordt het aantal geanalyseerde items weergegeven en wordt het aantal gevonden bevindingen weergegeven.

   ![&#x200B; Genererend Rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_generate_upload.png)

>[!NOTE]
>De tijdstempel van de BPA-upload met sleutelvervaldatum wordt in de rechterbovenhoek weergegeven. U zou BPA moeten vernieuwen uploadt sleutel wanneer het bijna zijn vervaldatum is. Om de sleutel te vernieuwen, kunt u op **klikken vernieuwt** om aan CAM te navigeren om de sleutel te vernieuwen.

1. Nadat het BPA-rapport is gegenereerd, worden een samenvatting en het aantal bevindingen weergegeven in een tabelvorm die is ingedeeld op basis van het type bevinding en het belangrijkste niveau. Voor meer informatie over een bepaalde bevinding kunt u op het nummer klikken dat overeenkomt met het type bevinding in de tabel.

   ![&#x200B; Overzicht van het Rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)

1. U hebt de optie om het rapport in een komma-gescheiden waarden (CSV) formaat te downloaden door op **Uitvoer naar CSV** te klikken. U hebt ook de optie om het rapport in CAM te bekijken door op **te klikken gaat naar CAM**. Dit zal u aan de [&#x200B; pagina van de Analyse van Beste praktijken &#x200B;](/help/journey-migration/cloud-acceleration-manager/using-cam/cam-readiness-phase.md#best-practices-analysis) in CAM nemen.

U kunt BPA dwingen om zijn geheime voorgeheugen te ontruimen en het rapport opnieuw te produceren door **te klikken verfrist Rapport**.

![&#x200B; verfrist rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_report_upload.png)

1. Als het geheime voorgeheugen verloopt, hebt u de optie om het laatste geproduceerde rapport in CAM te bekijken door op **te klikken Mening het laatste geproduceerde rapport in CAM** of een nieuwe rapportgeneratie in werking te stellen door op **te klikken produceert Nieuw Rapport**.

![&#x200B; Geen rapport &#x200B;](/help/journey-migration/best-practices-analyzer/assets/BPA_regeneratereport.png)


#### Het gebruiken van Filters in het Rapport van de Analysator van Beste praktijken {#bpa-filters}

Om bevindingen met betrekking tot [&#x200B; ACS Commons &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/) uit te filtreren, volg de stappen hieronder:

1. Klik op het linkerspoorpictogram aan de linkerkant van de pagina. Dit zal de **filter van de Bevelen ACS** tonen. Klik de **filter van Bevelen ACS** om interactieve checkbox zoals aangetoond in het hieronder beeld te tonen.

   ![&#x200B; ACS Commons Filter &#x200B;](/help/journey-migration/best-practices-analyzer/assets/report_filter_1.png)

   >[!NOTE]
   >Het linkerspoorpictogram zal verschijnen slechts als BPA het gebruik van ACSCommons ontdekt.

1. Schakel het selectievakje uit om alle bevindingen met betrekking tot ACS-opdrachten uit te filteren. U zou a **Gefilterde het Vinden Aantal** op het rapport zoals aangetoond in het beeld hieronder moeten zien. Het filter wordt ook toegepast op het rapport wanneer het in een komma-gescheiden-waarde (CSV) formaat wordt uitgevoerd.

   ![&#x200B; Gefilterde het Vinden Telling &#x200B;](/help/journey-migration/best-practices-analyzer/assets/report_filter_2.png)

   >[!NOTE]
   >De bevindingen van de ACS-Gemeenschappelijke Gemeenschap moeten niet worden genegeerd. Zie [&#x200B; documentatie &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/pages/compatibility.html#aem-as-a-cloud-service-feature-incompatibility) om verenigbaarheid met AEM as a Cloud Service te bepalen.

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
>abstract="Er zijn twee opties om BPA- rapportoutput te bekijken: UI en CSV. Wanneer het hulpmiddel van de Analysator van Beste praktijken in de instantie van AEM in werking wordt gesteld, wordt het rapport UI getoond als resultaten in het hulpmiddelvenster. De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de uitvoer van de patroondetector, gesorteerd en ingedeeld op categorietype, subtype en belangrijkheidsniveau."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html#analysis-report" text="Rapport Analyse van beste praktijken"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html" text="De categorieën van het Rapport van de Analyse van Beste praktijken begrijpen"

Wanneer het hulpmiddel van de Analysator van Beste praktijken in de instantie van AEM in werking wordt gesteld, wordt het rapport getoond als resultaten in het hulpmiddelvenster.

Het rapport is als volgt ingedeeld:

* **Overzicht van rapport**: Informatie over het rapport zelf. het overzicht biedt de volgende gegevens:
   * **Tijd van rapport**: Tijdstip waarop de rapportcontent is gegenereerd en voor het eerst beschikbaar gesteld.
   * **Vervaltijd**: Tijdstip waarop de cachecontent verloopt.
   * **Tijdsperiode voor genereren**: De benodigde tijd om de rapportcontent te genereren.
   * **Aantal bevindingen**: Het totale aantal bevindingen in het rapport.
* **Overzicht van het Systeem**: Informatie over het systeem van AEM waarop BPA in werking werd gesteld.
* **Categorieën voor bevindingen**: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie worden behandeld. Elke sectie bevat de volgende items: categorienaam, subtypen, aantal en belang, samenvatting, koppeling naar categoriedocumentatie en individuele informatie over de bevindingen.

Aan elke bevinding wordt een belangniveau toegewezen als ruwe prioriteit voor de benodigde actie.

>[!NOTE]
>Meer over elke het Vinden Categorie leren, zie {de Categorieën van de Detector van 0} Patroon [.](https://experienceleague.adobe.com/docs/experience-manager-pattern-detection/table-of-contents/aso.html)

Bekijk de onderstaande tabel om inzicht te krijgen in de belangniveaus:

| Belang | Beschrijving |
|--- |--- |
| INFO | Deze bevinding wordt alleen ter informatie verstrekt. |
| ADVISORY | Deze bevinding vormt mogelijk een upgradeprobleem. Vervolgonderzoek wordt aanbevolen. |
| MAJOR | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
| CRITICAL | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functie- of prestatieverlies te voorkomen. |

## Het CSV-rapport van de Analysator van best practices interpreteren {#cra-csv-report}

Wanneer u de **CSV** optie van uw instantie van AEM klikt, wordt het formaat CSV van het rapport van de Analysator van Beste praktijken gebouwd van het inhoudsgeheime voorgeheugen en teruggekeerd aan uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `results.csv` .

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

BPA verstrekt een interface van HTTP die als alternatief voor zijn gebruikersinterface binnen AEM kan worden gebruikt. Deze interface ondersteunt zowel HEAD- als GET-opdrachten. Het kan worden gebruikt om het BPA- rapport te produceren en het in één van drie formaten terug te keren: JSON, CSV, en lusje-gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` de hostnaam en poort is, indien nodig, van de server waarop de BPA is geïnstalleerd:

* `http://<host>/apps/best-practices-analyzer/analysis/report.json` voor de JSON-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.csv` voor de CSV-indeling
* `http://<host>/apps/best-practices-analyzer/analysis/report.tsv` voor de TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-http-request}

De HTTP-interface kan op een aantal manieren worden gebruikt.

Een eenvoudige manier is om een browsertabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregelprogramma gebruiken, zoals `curl` of `wget` , en elke HTTP-clienttoepassing. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u de naam en wachtwoord van een beheerder-gebruiker opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.csv' > report.csv`.

### Kopteksten en parameters {#http-headers-and-parameters}

De volgende HTTP-headers worden door deze interface gebruikt:

* `Cache-Control: max-age=<seconds>` - Geeft de levensduur van de cache-versheid op in seconden. (Zie [RFC 7234](https://tools.ietf.org/html/rfc7234#section-5.2.2.8).)
* `Prefer: respond-async` - Geeft op dat de server asynchroon moet reageren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.1).)
* `Prefer: return=minimal` - Geeft op dat de server een minimale reactie moet retourneren. (Zie [RFC 7240](https://tools.ietf.org/html/rfc7240#section-4.2).)

De volgende handige HTTP-queryparameters zijn beschikbaar wanneer HTTP-headers niet gemakkelijk kunnen worden gebruikt:

* `max-age` (getal, optioneel): geeft de levensduur van de cache-versheid op in seconden. Dit getal moet 0 of hoger zijn. De standaard versheidslevensduur is 86400 seconden. Zonder deze parameter of de overeenkomstige kopbal, wordt een vers geheime voorgeheugen gebruikt om verzoeken voor 24 uren te dienen, waarbij het geheime voorgeheugen moet worden opnieuw geproduceerd. Het gebruiken van `max-age=0` zal dwingen het geheime voorgeheugen wordt ontruimd en zal een regeneratie van het rapport in werking stellen, gebruikend het vorige niet-nul freshness leven voor het onlangs geproduceerde geheime voorgeheugen.
* `respond-async` (Boolean, optioneel): geeft op dat de reactie asynchroon moet worden opgegeven. Als u `respond-async=true` gebruikt wanneer de cache leeg is, retourneert de server een reactie van `202 Accepted` zonder te wachten tot de cache is vernieuwd en tot het rapport is gegenereerd. Als de cache vernieuwd is, heeft deze parameter geen effect. De standaardwaarde is `false` . Zonder deze parameter of de overeenkomstige kopbal zal de server synchroon antwoorden, die een significante hoeveelheid tijd kan vereisen en een aanpassing van de maximumreactietijd voor de cliënt van HTTP vereisen.
* `may-refresh-cache` (Booleaans, optioneel): Geeft aan dat de server de cache kan vernieuwen als reactie op een aanvraag als de huidige cache leeg, leeg of verouderd is of binnenkort zal zijn. Als `may-refresh-cache=true` is, of als dit niet is opgegeven, kan de server een achtergrondtaak starten die de Patroondetector oproept en de cache vernieuwt. Als `may-refresh-cache=false` dan zal de server geen verfrissingstaak in werking stellen die anders zou gedaan zijn als het geheime voorgeheugen leeg of verouderd is, in welk geval het rapport leeg is. Deze parameter heeft geen invloed op vernieuwingstaken die al in uitvoering zijn.
* `return-minimal` (Booleaans, optioneel): geeft aan dat de reactie van de server alleen de status mag bevatten die de voortgangsindicatie en cachestatus in de JSON-indeling bevat. Als `return-minimal=true` , is de hoofdtekst van de reactie beperkt tot het statusobject. Als `return-minimal=false` is opgegeven of als deze niet is opgegeven, wordt een volledige reactie gegeven.
* `log-findings` (Boolean, optioneel): geeft aan dat de server de inhoud van de cache moet vastleggen wanneer deze voor het eerst wordt gemaakt of vernieuwd. Elke bevinding via de cache wordt geregistreerd als een JSON-tekenreeks. Deze logboekregistratie vindt alleen plaats als `log-findings=true` en de aanvraag een nieuwe cache genereren.

Wanneer zowel de HTTP-header en de overeenkomstige queryparameter aanwezig zijn, heeft de queryparameter prioriteit.

De volgende opdracht vormt een eenvoudige manier om de productie van het rapport via de HTTP-interface te starten:
`curl -u admin:admin 'http://localhost:4502/apps/best-practices-analyzer/analysis/report.json?max-age=0&respond-async=true'`.

Zodra een aanvraag is ingediend, hoeft de client niet actief te zijn voor het produceren van het rapport. De rapportgeneratie zou met één cliënt kunnen in werking worden gesteld gebruikend een HTTP GET- verzoek en, zodra het rapport is geproduceerd, bekeken van het geheime voorgeheugen met een andere cliënt of met het hulpmiddel BPA in het gebruikersinterface van AEM.

### Reacties {#http-responses}

De volgende responswaarden zijn mogelijk:

* `200 OK`: geeft aan dat de reactie bevindingen van de patroondetector bevat die zijn gegenereerd binnen de frissheidsperiode van de cache.
* `202 Accepted`: wordt gebruikt om aan te geven dat de cache leeg is. Als `respond-async=true` en `may-refresh-cache=true` dit antwoord aangeeft dat een vernieuwingstaak wordt uitgevoerd. Als `may-refresh-cache=false` deze reactie alleen maar aangeeft dat de cache leeg is.
* `400 Bad Request`: Geeft aan dat er een fout is opgetreden met de aanvraag. Een bericht in het formaat van de Details van het Probleem (zie [&#x200B; RFC 7807 &#x200B;](https://tools.ietf.org/html/rfc7807)) verstrekt meer details.
* `401 Unauthorized`: geeft aan dat de aanvraag niet is geautoriseerd.
* `500 Internal Server Error`: Geeft aan dat er een interne serverfout is opgetreden. Een bericht in de indeling voor probleemdetails biedt meer informatie.
* `503 Service Unavailable`: Geeft aan dat de server bezig is met een andere respons en deze aanvraag niet tijdig kan uitvoeren. Dit gebeurt alleen bij synchrone aanvragen. Een bericht in de indeling voor probleemdetails biedt meer informatie.

## Beheerdersinformatie

### Aanpassing van levensduur cache {#cache-adjustment}

De standaardlevensduur van de BPA-cache is 24 uur. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de instantie van AEM als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk aangewezen voor de meeste toepassingen van BPA zijn. Als de tijd van de rapportgeneratie voor uw instantie van AEM bijzonder lang is, kunt u het geheim voorgeheugenleven willen aanpassen om de regeneratie van het rapport te minimaliseren.

De langetermijnwaarde is opgeslagen als de eigenschap `maxCacheAge` op de volgende repository-node:
`/apps/best-practices-analyzer/content/BestPracticesReport/jcr:content`

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan de levensduur aanpassen met CRX/DE Lite.

### Installeren op AEM 6.1 {#installing-on-aem61}

BPA gebruikt een gebruikersaccount voor systeemservices met de naam `repository-reader-service` om de Patroondetector uit te voeren. Dit account is beschikbaar op AEM 6.2 en hoger. Op AEM 6.1, moet deze rekening *voorafgaand aan* installatie van BPA worden gecreeerd door de volgende stappen te nemen:

1. Volg de instructies bij het [Nieuwe servicegebruiker maken](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-service-users.html#creating-a-new-service-user) om een gebruiker te maken. Stel de UserID in op `repository-reader-service` en laat het tussenpad leeg en klik op het groene vinkje.

2. Volg de instructies bij [Gebruikers en groepen beheren](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security.html#managing-users-and-groups), met name de instructies voor het toevoegen van gebruikers aan een groep om de `repository-reader-service`-gebruiker aan de groep `administrators` toe te voegen.

3. Installeer het BPA-pakket via Package Manager op uw AEM-bronexemplaar. (Dit zal de noodzakelijke configuratiewijziging toevoegen aan de ServiceUserMapper-configuratie voor de gebruiker van de `repository-reader-service`-systeemservicegebruiker.)
