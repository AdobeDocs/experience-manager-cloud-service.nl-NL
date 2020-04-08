---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
translation-type: tm+mt
source-git-commit: 114bc678fc1c6e3570d6d2a29bc034feb68aa56d

---


# Logboekregistratie{#logging}

AEM als Cloud Service biedt u de mogelijkheid om:

* globale parameters voor de centrale houtkapdienst
* verzoeken om registratie van gegevens; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke diensten; bijvoorbeeld een afzonderlijk logbestand en een indeling voor de logberichten

Voor lokale ontwikkeling worden logbestandvermeldingen naar lokale bestanden in de `/crx-quickstart/logs` map geschreven.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten.

>[!NOTE]
>
>Aanmelden bij AEM als cloudservice is gebaseerd op verkoopprincipes. Zie Logboekregistratie [](https://sling.apache.org/site/logging.html) voor meer informatie.

## Globale logboekregistratie {#global-logging}

[Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) wordt gebruikt om het hoofdlogger te configureren. Dit definieert de algemene instellingen voor het aanmelden bij AEM als cloudservice:

* het registratieniveau
* de locatie van het centrale logbestand
* het aantal versies dat moet worden bewaard
* versierotatie; of maximumgrootte of een tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten

## Loggers en schrijvers voor de Individuele Diensten {#loggers-and-writers-for-individual-services}

Naast de globale registrerenmontages, staat AEM als Dienst van de Wolk u toe om specifieke montages voor een individuele dienst te vormen:

* het specifieke registratieniveau
* de locatie van het individuele logbestand
* het aantal versies dat moet worden bewaard
* versierotatie; of maximumgrootte of tijdinterval
* de indeling die moet worden gebruikt bij het schrijven van de logberichten
* de registreermachine (de dienst OSGi die de logboekberichten levert)

Dit staat u toe om logboekberichten voor één enkele dienst in een afzonderlijk dossier te kanaliseren. Dit kan met name nuttig zijn tijdens de ontwikkeling of het testen; bijvoorbeeld, wanneer u een verhoogd logboekniveau voor de specifieke dienst nodig hebt.

AEM als Cloud Service gebruikt het volgende om logberichten naar bestand te schrijven:

1. Een **dienst** OSGi (registreerder) schrijft een logboekbericht.
1. Een **Logging Logger** neemt dit bericht en formatteert het volgens uw specificatie.
1. Een **Logging Schrijver** schrijft al deze berichten aan het fysieke dossier dat u hebt bepaald.

Deze elementen zijn gekoppeld aan de volgende parameters voor de desbetreffende elementen:

* **Logger (Logging Logger)**

   Definieer de service(s) die de berichten genereren.

* **Logbestand (Logging Logger)**

   Bepaal het fysieke dossier voor het opslaan van de logboekberichten.

   Dit wordt gebruikt om een Logging Logger met een het Registreren Schrijver te verbinden. De waarde moet aan de zelfde parameter in de Logging configuratie van de Schrijver identiek zijn om de verbinding te maken.

* **Logbestand (logboekschrijver)**

   Definieer het fysieke bestand waarnaar de logberichten worden geschreven.

   Dit moet gelijk zijn aan dezelfde parameter in de configuratie van Logging Writer, anders wordt de overeenkomst niet gemaakt. Als er geen gelijke is dan zal een impliciete Schrijver met standaardconfiguratie (dagelijkse logboekomwenteling) worden gecreeerd.

### Standaardloggers en -schrijvers {#standard-loggers-and-writers}

Bepaalde Loggers en schrijvers zijn als cloudservice-installatie opgenomen in een standaard-AEM.

Het eerste is een speciaal geval aangezien het zowel de `request.log` als `access.log` dossiers controleert:

* De logboekregistratie:

   * Apache Sling Aanpasbaar Data Logger Aanvraag

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Schrijf berichten over aanvraaginhoud aan `request.log`.

* Koppelingen naar:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Schrijft de berichten naar of `request.log` of `access.log`.

Deze kunnen indien nodig worden aangepast, hoewel de standaardconfiguratie geschikt is voor de meeste installaties.

De andere paren volgen de standaardconfiguratie:

* De logboekregistratie:

   * Logboekconfiguratie Apache Sling Logging

      (org.apache.sling.commons.log.LogManager.factory.config)

   * Schrijft `Information` berichten naar `logs/error.log`.

* Koppelingen naar de schrijver:

   * Configuratie van auteur van Apache Sling Logging

      (org.apache.sling.commons.log.LogManager.factory.writer)

* De logboekregistratie:

   * Apache Sling Logging Logger Configuration(org.apache.sling.commons.log.LogManager.factory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Schrijft `Warning` berichten aan `../logs/error.log` voor de dienst `org.apache.pdfbox`.

* Koppelt niet aan een specifieke schrijver, zodat er een impliciete schrijver met standaardconfiguratie (dagelijkse logrotatie) wordt gemaakt en gebruikt.

## Logniveau instellen {#setting-the-log-level}

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
> Om de hieronder vermelde configuratieveranderingen uit te voeren, moet u hen op een lokale ontwikkelomgeving tot stand brengen en dan hen duwen aan een AEM als instantie van de Dienst van de Wolk. Zie [Distribueren naar AEM als Cloud Service](/help/implementing/deploying/overview.md)voor meer informatie over hoe u dit kunt doen.

### Het FOUTOPSPORINGSlogniveau activeren {#activating-the-debug-log-level}

>[!WARNING]
>
> Door het deBUG-logniveau wereldwijd te activeren, wordt een grote hoeveelheid informatie gegenereerd die moeilijk te doorzoeken is. Het wordt geadviseerd u het slechts voor de diensten toelaat die het zuiveren vereisen. Voor meer informatie, zie [Loggers en Schrijvers voor de Individuele Diensten](logging.md#loggers-and-writers-for-individual-services).

Het standaardlogboekniveau is INFO, dat wil zeggen, worden de DEBUG- berichten niet geregistreerd.
Als u het niveau van het FOUTOPSPORINGSlogbestand wilt activeren, stelt u de optie

``` /libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level ```

eigenschap voor foutopsporing. Verlaat het logboek bij het DEBUG logboekniveau niet langer dan nodig, aangezien het veel logboeken produceert.
Een lijn in zuivert dossier begint gewoonlijk met DEBUG, en verstrekt dan het logboekniveau, de installeractie en het logboekbericht. Bijvoorbeeld:

``` DEBUG 3 WebApp Panel: WebApp successfully deployed ```

De logniveaus zijn als volgt:

| 0 | Fatale fout | De handeling is mislukt en het installatieprogramma kan niet doorgaan. |
|---|---|---|
| 1 | Fout | De handeling is mislukt. De installatie gaat door, maar een deel van CRX is niet correct geïnstalleerd en werkt niet. |
| 2 | Waarschuwing | De actie is geslaagd maar heeft problemen ondervonden. CRX werkt mogelijk niet correct. |
| 3 | Informatie | De actie is geslaagd. |

### Uw eigen registreerapparaten en schrijvers maken {#creating-your-own-loggers-and-writers}

U kunt uw eigen registreerapparaat/schrijfpaar definiëren:

1. Maak een nieuwe instantie van de configuratie- [Apache Sling Logging Logger](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based)van de Fabriek.

   1. Geef het logbestand op.
   1. Geef de logboekregistratie op.
   1. Configureer de overige parameters naar wens.

1. Maak een nieuw exemplaar van de Configuratie [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

   1. Geef het logbestand op. Dit moet overeenkomen met het logbestand dat is opgegeven voor de gebruiker.
   1. Configureer de overige parameters naar wens.

### Een aangepast logbestand maken {#create-a-custom-log-file}

>[!NOTE]
>
>Wanneer u met Adobe Experience Manager werkt, zijn er verschillende methoden om de configuratie-instellingen voor dergelijke services te beheren.

In bepaalde omstandigheden wilt u mogelijk een aangepast logbestand met een ander logniveau maken. U kunt dit in de repository doen door:

1. Als het nog niet bestaat, creeer een nieuwe configuratiemap ( `sling:Folder`) voor uw project `/apps/<*project-name*>/config`.
1. Onder `/apps/<*project-name*>/config`, creeer een knoop voor de nieuwe Configuratie van de Logboekregistrator van Apache Sling:

   * Naam: `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (aangezien dit een Logger is)

      Waar `<*identifier*>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten).

      Bijvoorbeeld: `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * Type: `sling:OsgiConfig`
   >[!NOTE]
   >
   >Hoewel het geen technische eis is, is het raadzaam `<*identifier*>` uniek te maken.

1. Stel de volgende eigenschappen in voor dit knooppunt:

   * Naam: `org.apache.sling.commons.log.file`

      Type: String

      Waarde: het logbestand specificeren; bijvoorbeeld: `logs/myLogFile.log`

   * Naam: `org.apache.sling.commons.log.names`

      Type: String[] (String + Multi)

      Waarde: specificeert de diensten OSGi waarvoor de Logger berichten moet registreren; bijvoorbeeld:

      * `org.apache.sling`
      * `org.apache.felix`
      * `com.day`
   * Naam: `org.apache.sling.commons.log.level`

      Type: String

      Waarde: het vereiste logniveau specificeren ( `debug`, `info`, `warn` of `error`); bijvoorbeeld `debug`

   * Configureer de overige parameters naar wens:

      * Naam: `org.apache.sling.commons.log.pattern`

         Type: `String`

         Waarde: het patroon van het logbericht specificeren, indien nodig; bijvoorbeeld:

         `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`
   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` ondersteunt maximaal zes argumenten.

   >{0} The timestamp of type `java.util.Date`
   >
   >{1} the log marker{2} the name of the current thread{3} the name of the logger{4} the log level{5} the log message

   >Als de logboekvraag een `Throwable` stapelspoor omvat wordt toegevoegd aan het bericht.

   >[!CAUTION]
   org.apache.sling.commons.log.names moet een waarde hebben.

   >[!NOTE]
   Logschrijfpaden zijn relatief ten opzichte van de `crx-quickstart` locatie.
   Daarom wordt een logbestand opgegeven als:
   `logs/thelog.log`

   >schrijft naar:
   `` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log&quot;.
   En een logbestand dat is opgegeven als:
   `../logs/thelog.log`

   >schrijft naar een map:
   ` <*cq-installation-dir*>/logs/`
&quot;(d.w.z. naast ` `&lt;*cq-installation-dir*>/`crx-quickstart/`)

1. Deze stap is alleen nodig wanneer een nieuwe schrijver is vereist (dat wil zeggen met een andere configuratie dan de standaardschrijver).

   >[!CAUTION]
   Een nieuwe configuratie van de schrijver van het Registreren wordt slechts vereist wanneer het bestaande gebrek niet geschikt is.

   >Als geen expliciete Schrijver wordt gevormd zal het systeem automatisch een impliciete Schrijver produceren die op het gebrek wordt gebaseerd.

   Onder `/apps/<*project-name*>/config`, creeer een knoop voor de nieuwe `Apache Sling Logging Writer` Configuratie:

   * Naam: `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (aangezien dit een schrijver is)

      Net als bij Logger, `<*identifier*>` wordt vervangen door vrije tekst die u (moet) ingaan om de instantie te identificeren (u kunt deze informatie niet weglaten). Bijvoorbeeld: `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

   * Type: `sling:OsgiConfig`
   >[!NOTE]
   Hoewel het geen technische eis is, is het raadzaam `<*identifier*>` uniek te maken.

   Stel de volgende eigenschappen in voor dit knooppunt:

   * Naam: `org.apache.sling.commons.log.file`

      Type: `String`

      Waarde: geeft het logbestand op, zodat het overeenkomt met het bestand dat is opgegeven in het logbestand;

      voor dit voorbeeld, `../logs/myLogFile.log`.

   * Configureer de overige parameters naar wens:

      * Naam: `org.apache.sling.commons.log.file.number`

         Type: `Long`

         Waarde: het aantal logbestanden opgeven dat u wilt behouden; bijvoorbeeld: `5`

      * Naam: `org.apache.sling.commons.log.file.size`

         Type: `String`

         Waarde: specificeren zoals vereist om de omwenteling van het dossier door grootte/datum te controleren; bijvoorbeeld: `'.'yyyy-MM-dd`
   >[!NOTE]
   `org.apache.sling.commons.log.file.size` Hiermee bepaalt u de rotatie van het logbestand door een van de volgende instellingen in te stellen:
   * een maximale bestandsgrootte
   * een datum-/tijdschema
   om aan te geven wanneer een nieuw bestand wordt gemaakt (en de naam van het bestaande bestand wordt gewijzigd volgens het naampatroon).
   * Een formaatlimiet kan met een getal worden opgegeven. Als er geen grootteindicator is opgegeven, wordt deze gebruikt als het aantal bytes. U kunt ook een van de grootteindicatoren toevoegen - `KB`, `MB`of `GB` (hoofdlettergebruik wordt genegeerd).
   * U kunt een tijd-/datumschema opgeven als een `java.util.SimpleDateFormat` patroon. Hiermee wordt de periode gedefinieerd waarna het bestand wordt geroteerd. ook het achtervoegsel dat aan het geroteerde dossier (voor identificatie) wordt toegevoegd.
   De standaardwaarde is &#39;.&#39;jjjj-MM-dd (voor dagelijkse logrotatie).
   Bijvoorbeeld, om middernacht van 20 Januari 2010 (of wanneer het eerste logboekbericht na dit voorkomt om precies te zijn), zal ../logs/error.log worden anders genoemd aan ../logs/error.log.2010-01-20. Logboekregistratie voor 21 januari wordt uitgevoerd naar (een nieuw en leeg) ../logs/error.log totdat de logbestanden bij de volgende wijziging van de dag worden doorgehaald.
       | `&#39;.&#39;yyyy-MM&quot;|Roteren aan het begin van elke maand|
    |—|—|
    | `&#39;.&#39;yyyy-ww&quot;|Rotatie op de eerste dag van elke week (afhankelijk van de landinstelling). |
       | `&#39;.&#39;yyyy-MM-dd&quot;|Dagelijks om middernacht. |
       | `&#39;.&#39;yyyy-MM-dd-a&quot;|Roteren om middernacht en om middag van elke dag. |
       | `&#39;.&#39;yyyy-MM-dd-HH&quot;|Roteren boven aan elk uur. |
       | `&#39;.&#39;yyyy-MM-dd-HH-mm&quot;|Roteren aan het begin van elke minuut. |
 Opmerking     
     : Wanneer u een tijd/datum opgeeft:
       1. U moet letterlijke tekst met enkele aanhalingstekens (&#39; &#39;) &quot;escape&quot;-tekens gebruiken;
   Dit     is om te voorkomen dat bepaalde tekens worden geïnterpreteerd als patroonletters.
       1. Gebruik alleen tekens die zijn toegestaan voor een geldige bestandsnaam op een willekeurige plaats in de optie.
   

1. Lees het nieuwe logbestand met het gekozen gereedschap.

   Het logbestand dat in dit voorbeeld wordt gemaakt, wordt `../crx-quickstart/logs/myLogFile.log`weergegeven.

De Felix-console biedt ook informatie over de ondersteuning voor het verkooplogboek op `../system/console/slinglog`; bijvoorbeeld `https://localhost:4502/system/console/slinglog`.draf