---
title: Logboekregistratie
description: Leer hoe te om globale parameters voor de centrale registrerendienst, specifieke montages voor de individuele diensten te vormen of hoe te om gegevensregistreren te verzoeken.
translation-type: tm+mt
source-git-commit: ae04553b17fcb7b9660f709565faed791a0c930e

---


# Logboekregistratie{#logging}

AEM als Cloud Service is een platform waarop klanten aangepaste code kunnen opnemen om unieke ervaringen voor hun klanten te creëren. Met dit in mening, is het registreren een kritieke functie om douanecode op wolkenmilieu&#39;s en meer in het bijzonder voor lokale dev milieu&#39;s te zuiveren.


<!-- ## Global Logging {#global-logging}

[Apache Sling Logging Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based) is used to configure the root logger. This defines the global settings for logging in AEM as a Cloud Service:

* the logging level
* the location of the central log file
* the number of versions to be kept
* version rotation; either maximum size or a time interval
* the format to be used when writing the log messages
-->

## AEM als logbestand voor cloudservice {#aem-as-a-cloud-service-logging}

AEM als Cloud Service biedt u de mogelijkheid om:

* globale parameters voor de centrale houtkapdienst
* verzoeken om registratie van gegevens; een gespecialiseerde registrerenconfiguratie voor verzoekinformatie
* specifieke instellingen voor de afzonderlijke diensten

Voor lokale ontwikkeling worden logbestandvermeldingen naar lokale bestanden in de `/crx-quickstart/logs` map geschreven.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten.

>[!NOTE]
>
>Aanmelden bij AEM als cloudservice is gebaseerd op verkoopprincipes. Zie Logboekregistratie [](https://sling.apache.org/site/logging.html) voor meer informatie.

## Java-aanmelding voor AEM als cloudservice {#aem-as-a-cloud-service-java-logging}

### Standaardloggers en -schrijvers {#standard-loggers-and-writers}

> [!IMPORTANT]
> Deze kunnen indien nodig worden aangepast, hoewel de standaardconfiguratie geschikt is voor de meeste installaties. Als u echter de standaardlogconfiguraties moet aanpassen, dient u ervoor te zorgen dat u deze alleen in `dev` omgevingen uitvoert.

Bepaalde Loggers en schrijvers zijn als cloudservice-installatie opgenomen in een standaard-AEM.

Het eerste geval is een speciaal geval aangezien het zowel de `request` als `access` logboeken controleert:

* De logboekregistratie:

   * Apache Sling Aanpasbaar Data Logger Aanvraag

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Schrijf berichten over aanvraaginhoud aan `request.log`.

* Koppelingen naar:

   * Apache Sling Request Logger

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Schrijft de berichten naar of `request.log` of `access.log`.

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

* Koppelt niet aan een specifieke schrijver, zodat er een impliciete schrijver met standaardconfiguratie wordt gemaakt en gebruikt.

**AEM als HTTP-aanvraagaanmelding voor cloudservice**

Alle toegangsverzoeken aan AEM WCM en de gegevensopslagplaats worden hier geregistreerd.

Voorbeeld-uitvoer:

**AEM als HTTP-aanvraag-/antwoordtoegangsregistratie voor cloudservice**

Elk toegangsverzoek wordt hier geregistreerd samen met de reactie.

Voorbeeld-uitvoer:

**Apache-webserver/Dispatcher Logging**

Dit is een logboek voor gebruikt voor het zuiveren van de kwesties van de Verzender. Zie [Fouten opsporen in uw Apache- en Dispatcher-configuratie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/)voor meer informatie.

<!-- Besides the three types of logs present on an AEM as a Cloud Service instance (`request`, `access` and `error` logs) there is another dispatcher/overview.html#debugging-apache-and-dispatcher-configuration.

leftover text from the last breakaway chunk (re dispatcher) -->

Wat beproefde praktijken gaan, adviseert u zich aan de configuraties die momenteel in AEM als Cloud Service Maven archetype bestaan. Met deze opties stelt u verschillende loginstellingen en niveaus in voor bepaalde omgevingstypen:

* voor `local dev` - en `dev` omgevingen stelt u het logger in op **DEBUG** -niveau op `error.log`
* voor `stage`, plaats de registreerder aan **WARN** niveau aan `error.log`
* Stel voor `prod`, registreerapparaat in op **ERROR** -niveau op de `error.log`

Hieronder vindt u voorbeelden voor elke configuratie:

* `dev` omgevingen:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="debug"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```


* `stage` omgevingen:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="warn"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

* `prod` omgevingen:

```
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
    org.apache.sling.commons.log.level="error"
    org.apache.sling.commons.log.names="[com.mycompany.myapp]" />
```

### Loggers en schrijvers voor de Individuele Diensten {#loggers-and-writers-for-individual-services}

Naast de globale registrerenmontages, staat AEM als Dienst van de Wolk u toe om specifieke montages voor een individuele dienst te vormen:

* het specifieke registratieniveau
* de registreermachine (de dienst OSGi die de logboekberichten levert)

Dit staat u toe om logboekberichten voor één enkele dienst in een afzonderlijk dossier te kanaliseren. Dit kan met name nuttig zijn tijdens de ontwikkeling of het testen; bijvoorbeeld, wanneer u een verhoogd logboekniveau voor de specifieke dienst nodig hebt.

AEM als Cloud Service gebruikt het volgende om logberichten naar bestand te schrijven:

1. Een **dienst** OSGi (registreerder) schrijft een logboekbericht.
1. Een **Logging Logger** neemt dit bericht en formatteert het volgens uw specificatie.
1. Een **Logging Schrijver** schrijft al deze berichten aan het fysieke dossier dat u hebt bepaald.

Deze elementen zijn gekoppeld aan de volgende parameters voor de desbetreffende elementen:

* **Logger (Logging Logger)**

   Definieer de service(s) die de berichten genereren.

<!-- * **Log File (Logging Logger)**

  Define the physical file for storing the log messages.

  This is used to link a Logging Logger with a Logging Writer. The value must be identical to the same parameter in the Logging Writer configuration for the connection to be made.

* **Log File (Logging Writer)**

  Define the physical file that the log messages will be written to.

  This must be identical to the same parameter in the Logging Writer configuration, or the match will not be made. If there is no match then an implicit Writer will be created with default configuration (daily log rotation).
-->

### Logniveau instellen {#setting-the-log-level}

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
> Om de hieronder vermelde configuratieveranderingen uit te voeren, moet u hen op een lokale ontwikkelomgeving tot stand brengen en dan hen duwen aan een AEM als instantie van de Dienst van de Wolk. Zie [Distribueren naar AEM als Cloud Service](/help/implementing/deploying/overview.md)voor meer informatie over hoe u dit kunt doen.

**Het FOUTOPSPORINGSlogniveau activeren**

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

   1. Geef de logboekregistratie op.

<!-- 1. Create a new instance of the Factory Configuration [Apache Sling Logging Writer Configuration](https://sling.apache.org/documentation/development/logging.html#user-configuration---osgi-based).

    1. Specify the Log File - this must match that specified for the Logger.
    1. Configure the other parameters as required. -->

### Logboekregistratie configureren {#configure-logging}

>[!NOTE]
>
>Wanneer u met Adobe Experience Manager werkt, zijn er verschillende methoden om de configuratie-instellingen voor dergelijke services te beheren.

In bepaalde omstandigheden kunt u een aangepast logboek met een verschillend logboekniveau willen tot stand brengen. U kunt dit in de repository doen door:

1. Als het nog niet bestaat, creeer een nieuwe configuratiemap ( `sling:Folder`) voor uw project `/apps/<*project-name*>/config`.
1. Onder `/apps/<*project-name*>/config`, creeer een knoop voor de nieuwe Configuratie van de Logboekregistrator van Apache Sling:

   * Naam: `org.apache.sling.commons.log.LogManager.factory.config-<*identifier*>` (aangezien dit een Logger is)

      Waar `<*identifier*>` wordt vervangen door vrije tekst die u (moet) invoeren om het exemplaar te identificeren (u kunt deze informatie niet weglaten).

      Bijvoorbeeld, `org.apache.sling.commons.log.LogManager.factory.config-MINE`

   * Type: `sling:OsgiConfig`
   >[!NOTE]
   >
   >Hoewel het geen technische eis is, is het raadzaam `<*identifier*>` uniek te maken.

<!-- 1. Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: String

      Value: specify the Log File; for example, `logs/myLogFile.log`

    * Name: `org.apache.sling.commons.log.names`

      Type: String[] (String + Multi)

      Value: specify the OSGi services for which the Logger is to log messages; for example, all of the following:

        * `org.apache.sling`
        * `org.apache.felix`
        * `com.day`

    * Name: `org.apache.sling.commons.log.level`

      Type: String

      Value: specify the log level required ( `debug`, `info`, `warn` or `error`); for example `debug`

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.pattern`

          Type: `String`

          Value: specify the pattern of the log message as required; for example,

          `{0,date,dd.MM.yyyy HH:mm:ss.SSS} *{4}* [{2}] {3} {5}`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.pattern` supports up to six arguments.

   >
   >
   >{0} The timestamp of type `java.util.Date`
   >{1} the log marker
   >{2} the name of the current thread
   >{3} the name of the logger
   >{4} the log level
   >{5} the log message

   >
   >
   >If the log call includes a `Throwable` the stacktrace is appended to the message.

   >[!CAUTION]
   >
   >org.apache.sling.commons.log.names must have a value.

   >[!NOTE]
   >
   >Log writer paths are relative to the `crx-quickstart` location.
   >
   >
   >Therefore, a log file specified as:
   >
   >
   >`logs/thelog.log`

   >
   >
   >writes to:
   >
   >
   >`` ` ` `<*cq-installation-dir*>/``crx-quickstart/logs/thelog.log`.
   >
   >
   >And a log file specified as:
   >
   >
   >`../logs/thelog.log`

   >
   >
   >writes to a directory:
   >
   >
   >` <*cq-installation-dir*>/logs/`
   >``(i.e. next to ` `<*cq-installation-dir*>/`crx-quickstart/`)
 -->

<!-- open question: see if we need to leave the above warning note in place, but adjust it so that it doesn't mention filenames -->

<!-- 1. This step is only necessary when a new Writer is required (i.e. with a configuration that is different to the default Writer).

   >[!CAUTION]
   >
   >A new Logging Writer Configuration is only required when the existing default is not suitable.

   >
   >
   >If no explicit Writer is configured the system will automatically generate an implicit Writer based on the default.

   Under `/apps/<*project-name*>/config`, create a node for the new `Apache Sling Logging Writer` Configuration:

    * Name: `org.apache.sling.commons.log.LogManager.factory.writer-<*identifier*>` (as this is a Writer)

      As with the Logger, `<*identifier*>` is replaced by free text that you (must) enter to identify the instance (you cannot omit this information). For example, `org.apache.sling.commons.log.LogManager.factory.writer-MINE`

    * Type: `sling:OsgiConfig`

   >[!NOTE]
   >
   >Although not a technical requirement, it is advisable to make `<*identifier*>` unique.

   Set the following properties on this node:

    * Name: `org.apache.sling.commons.log.file`

      Type: `String`

      Value: specify the Log File so that it matches the file specified in the Logger;

      for this example, `../logs/myLogFile.log`.

    * Configure the other parameters as required:

        * Name: `org.apache.sling.commons.log.file.number`

          Type: `Long`

          Value: specify the number of log files you want kept; for example, `5`

        * Name: `org.apache.sling.commons.log.file.size`

          Type: `String`

          Value: specify as required to control file rotation by size/date; for example, `'.'yyyy-MM-dd`

   >[!NOTE]
   >
   >`org.apache.sling.commons.log.file.size` controls the rotation of the log file by setting either:
   >
   >* a maximum file size
   >* a time/date schedule
   >
   >to indicate when a new file will be created (and the existing file renamed according to the name pattern).
   >
   >* A size limit can be specified with a number. If no size indicator is given, then this is taken as the number of bytes, or you can add one of the size indicators - `KB`, `MB`, or `GB` (case is ignored).
   >* A time/date schedule can be specified as a `java.util.SimpleDateFormat` pattern. This defines the time period after which the file will be rotated; also the suffix appended to the rotated file (for identification).
   >
   >The default is '.'yyyy-MM-dd (for daily log rotation).
   >
   >So for example, at midnight of January 20th 2010 (or when the first log message after this occurs to be precise), ../logs/error.log will be renamed to ../logs/error.log.2010-01-20. Logging for the 21st of January will be output to (a new and empty) ../logs/error.log until it is rolled over at the next change of day.
   >
   >      | `'.'yyyy-MM` |Rotation at the beginning of each month |
   >      |---|---|
   >      | `'.'yyyy-ww` |Rotation at the first day of each week (depends on the locale). |
   >      | `'.'yyyy-MM-dd` |Rotation at midnight each day. |
   >      | `'.'yyyy-MM-dd-a` |Rotation at midnight and midday of each day. |
   >      | `'.'yyyy-MM-dd-HH` |Rotation at the top of every hour. |
   >      | `'.'yyyy-MM-dd-HH-mm` |Rotation at the beginning of every minute. |
   >
   >      Note: When specifying a time/date:
   >      1. You should "escape" literal text within a pair of single quotes (' ');
   >      this is to avoid certain characters being interpreted as pattern letters.
   >      1. Only use characters allowed for a valid file name anywhere in the option.

1. Read your new log file with your chosen tool.

   The log file created by this example will be `../crx-quickstart/logs/myLogFile.log`. -->

De Felix-console biedt ook informatie over de ondersteuning voor het verkooplogboek op `../system/console/slinglog`; bijvoorbeeld `https://localhost:4502/system/console/slinglog`.draf

## Logbestanden openen en beheren {#manage-logs}

Raadpleeg de documentatie bij [Cloud Manager voor informatie over het openen en beheren van logbestanden](/help/implementing/cloud-manager/manage-logs.md).