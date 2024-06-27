---
title: AEM as a Cloud Service-ontwikkelingsrichtsnoeren
description: Leer richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM op gebouwen en AEM in AMS.
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 0%

---

# AEM as a Cloud Service-ontwikkelingsrichtsnoeren {#aem-as-a-cloud-service-development-guidelines}

>[!CONTEXTUALHELP]
>id="development_guidelines"
>title="AEM as a Cloud Service-ontwikkelingsrichtsnoeren"
>abstract="Leer richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM op gebouwen en AEM in AMS."
>additional-url="https://video.tv.adobe.com/v/330555/" text="Demo van pakketstructuur"

Dit document bevat richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM in gebouwen en AEM in AMS.

## Code moet clustervriendelijk zijn {#cluster-aware}

Code die in AEM as a Cloud Service wordt uitgevoerd, moet zich ervan bewust zijn dat deze altijd in een cluster wordt uitgevoerd. Dit betekent dat er altijd meer dan één instantie actief is. De code moet veerkrachtig zijn, vooral omdat een instantie op om het even welk ogenblik zou kunnen worden tegengehouden.

Tijdens de update van AEM as a Cloud Service zijn er exemplaren met oude en nieuwe code die parallel lopen. Daarom moet oude code niet breken met inhoud die door nieuwe code wordt gecreeerd en de nieuwe code moet oude inhoud kunnen behandelen.

Als de primaire code in de cluster moet worden geïdentificeerd, kan de API voor detectie van Apache Sling worden gebruikt om deze te detecteren.

## Staat in geheugen {#state-in-memory}

De staat moet niet in geheugen worden bewaard maar in bewaarplaats voortgeduurd. Anders kan deze status verloren gaan als een instantie wordt gestopt.

## Status van het bestandssysteem {#state-on-the-filesystem}

Gebruik het bestandssysteem van de instantie niet in AEM as a Cloud Service. De schijf is ephemraal en wordt verwijderd wanneer instanties worden gerecycled. Beperkt gebruik van het bestandssysteem voor tijdelijke opslag in verband met de verwerking van afzonderlijke aanvragen is mogelijk, maar mag niet worden misbruikt voor grote bestanden. Dit is omdat het een negatieve invloed op het hulpmiddelgebruiksquotum kan hebben en op schijfbeperkingen in werking kan stellen.

Als voorbeeld waar het gebruik van het bestandssysteem niet wordt ondersteund, moet de Publish-laag ervoor zorgen dat alle gegevens die moeten worden geduurd, worden verzonden naar een externe service voor opslag op langere termijn.

## Waarneming {#observation}

Net als bij alles wat asynchroon gebeurt, zoals bij observatiegebeurtenissen, kan niet worden gegarandeerd dat het lokaal wordt uitgevoerd en moet het daarom met zorg worden gebruikt. Dit geldt zowel voor JCR-gebeurtenissen als voor Sling-brongebeurtenissen. Op het moment dat een wijziging plaatsvindt, kan de instantie worden verwijderd en worden vervangen door een andere instantie. Andere instanties in de topologie die op dat ogenblik actief zijn kunnen op die gebeurtenis reageren. In dit geval zal dit echter geen lokale gebeurtenis zijn en is er misschien zelfs geen actieve leider in het geval van een doorlopende verkiezing van de leider op het moment dat het evenement wordt uitgegeven.

## Achtergrondtaken en langdurige taken {#background-tasks-and-long-running-jobs}

Code die als achtergrondtaken wordt uitgevoerd, moet ervan uitgaan dat de instantie waarin deze wordt uitgevoerd, op elk gewenst moment kan worden ingedrukt. Daarom moet de code veerkrachtig zijn, en het allerbelangrijkste herbruikbaar. Dat betekent dat als de code opnieuw wordt uitgevoerd, deze niet opnieuw van het begin moet beginnen, maar eerder dicht bij het punt waar de code is gebleven. Hoewel dit geen nieuwe eis voor dit soort code is, is het in AEM as a Cloud Service waarschijnlijker dat een instantie zal verdwijnen.

Om de problemen tot een minimum te beperken, moeten zo mogelijk langdurige banen worden vermeden, en deze moeten ten minste herbruikbaar zijn. Voor het uitvoeren van dergelijke banen gebruikt u Sling Jobs, die minstens eenmaal een garantie hebben en die daarom zo snel mogelijk opnieuw zal worden uitgevoerd als ze worden onderbroken. Maar ze zouden waarschijnlijk niet opnieuw van het begin moeten beginnen. Voor het plannen van dergelijke taken kunt u het beste de opdracht [Verkooptaken](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) planner als dit opnieuw verzekert minstens eenmaal uitvoering.

Gebruik de Sling Commons Planner niet voor het plannen aangezien de uitvoering niet kan worden gewaarborgd. Het is nog waarschijnlijker dat het gepland is.

Op dezelfde manier, met alles dat asynchroon gebeurt, zoals handelend op observatiegebeurtenissen, (het zijn gebeurtenissen JCR of Sling resource), kan niet worden gewaarborgd om worden uitgevoerd en daarom moet met voorzichtigheid worden gebruikt. Dit geldt al voor AEM implementaties in het heden.

## Uitgaande HTTP-verbindingen {#outgoing-http-connections}

Het wordt sterk aanbevolen dat uitgaande HTTP-verbindingen redelijke time-outs voor verbinding en lezen instellen. De voorgestelde waarden zijn 1 seconde voor de time-out van de verbinding en 5 seconden voor de time-out bij lezen. De nauwkeurige aantallen moeten worden bepaald gebaseerd op de prestaties van het backend systeem die deze verzoeken behandelen.

Voor code die deze time-outs niet toepast, AEM instanties die op AEM as a Cloud Service worden uitgevoerd, zorgen voor een algemene time-out. Deze onderbrekingswaarden zijn 10 seconden voor verbind vraag en 60 seconden voor gelezen vraag naar verbindingen.

Adobe beveelt aan de verstrekte informatie te gebruiken [Apache HttpComponents Client 4.x-bibliotheek](https://hc.apache.org/httpcomponents-client-ga/) voor het maken van HTTP-verbindingen.

Alternatieven waarvan bekend is dat ze werken, maar waarvoor de afhankelijkheid zelf nodig kan zijn, zijn:

* [java.net.URL](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URL.html) en/of [java.net.URLConnection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URLConnection.html) (Door AEM verstrekt)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (niet aanbevolen omdat het verouderd is en wordt vervangen door versie 4.x)
* [OK Http](https://square.github.io/okhttp/) (Niet verstrekt door AEM)

Naast het verstrekken van onderbrekingen ook zou een juiste behandeling van dergelijke onderbrekingen en onverwachte HTTP- statuscodes moeten worden uitgevoerd.

## Aanvraagsnelheidslimieten afhandelen {#rate-limit-handling}

Wanneer het tarief van inkomende verzoeken aan AEM gezonde niveaus overschrijdt, AEM aan nieuwe verzoeken met de foutencode van HTTP 429 beantwoordt. Toepassingen die programmatische vraag aan AEM maken kunnen defensief coderen overwegen, die na een paar seconden met een exponentiële backoff strategie opnieuw proberen. Vóór medio augustus 2023 reageerde AEM op dezelfde voorwaarde met HTTP-foutcode 503.

## Geen Klassieke UI-aanpassingen {#no-classic-ui-customizations}

AEM as a Cloud Service ondersteunt alleen de Touch-gebruikersinterface voor klantcode van derden. Klassieke UI is niet beschikbaar voor aanpassing.

## Geen eigen binaire of native bibliotheken {#avoid-native-binaries}

Native binaire bestanden en bibliotheken mogen niet worden geïmplementeerd of geïnstalleerd in cloudomgevingen.

Bovendien mag de code niet proberen native binaire bestanden of native Java-extensies (bijvoorbeeld JNI) te downloaden tijdens runtime.

## Geen streamingbinaire getallen via AEM as a Cloud Service {#no-streaming-binaries}

De binaire getallen zouden door CDN moeten worden betreden, die binaire getallen buiten de kern AEM diensten zal dienen.

Gebruik bijvoorbeeld niet `asset.getOriginal().getStream()`, die het downloaden van binair binair getal op de van de dienst van de AEM in werking stelt.

## Geen reverse Replication-agents {#no-reverse-replication-agents}

Reverse Replication from Publish to Author wordt niet ondersteund in AEM as a Cloud Service. Als een dergelijke strategie nodig is, kunt u een externe persistentieopslag gebruiken die onder het landbouwbedrijf van de instanties van Publish en potentieel de cluster van de Auteur wordt gedeeld.

## De voorwaartse Medewerkers van de Replicatie zouden kunnen moeten worden gesteund {#forward-replication-agents}

Inhoud wordt via een submechanisme van Auteur naar Publish gerepliceerd. Aangepaste replicatiemiddelen worden niet ondersteund.

## Geen overbelastende ontwikkelomgevingen {#overloading-dev-envs}

Productieomgevingen zijn groter om een stabiele werking te garanderen, terwijl werkgebiedomgevingen als productieomgevingen worden geschaald om realistische tests onder productieomstandigheden te garanderen.

Dev-omgevingen en Rapid Dev-omgevingen dienen beperkt te blijven tot ontwikkeling, foutenanalyse en functionele tests en zijn niet ontworpen voor het verwerken van hoge werklasten of grote hoeveelheden inhoud.

Als voorbeeld, kan het veranderen van een indexdefinitie op een grote inhoudsbewaarplaats op een Dev milieu in het re-indexeren resulteren resulterend in teveel verwerking. Tests waarvoor aanzienlijke inhoud nodig is, moeten worden uitgevoerd in werkgebiedomgevingen.

## Controle en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

Voor lokale ontwikkeling worden logbestandvermeldingen geschreven naar lokale bestanden in het dialoogvenster `/crx-quickstart/logs` map.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden te staart. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Custom logs are not supported and so all logs should be output to the error log. -->

**Logniveau instellen**

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Omdat dit niet onmiddellijk is, ben voorzichtig over het toelaten van breedband logboeken op productiemilieu&#39;s die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
>Om de hieronder vermelde configuratieveranderingen uit te voeren, creeert u hen op een lokale ontwikkelomgeving en duw hen dan aan een instantie van AEM as a Cloud Service. Ga voor meer informatie over hoe u dit kunt doen naar [Distribueren naar AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Het FOUTOPSPORINGSlogniveau activeren**

Het standaardlogboekniveau is INFO, dat wil zeggen, worden de DEBUG- berichten niet geregistreerd. Als u het niveau van het DEBUG-logbestand wilt activeren, werkt u de volgende eigenschap bij naar de foutopsporingsmodus.

`/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level`

Stel bijvoorbeeld `/apps/<example>/config/org.apache.sling.commons.log.LogManager.factory.config~<example>.cfg.json` met de volgende waarde.

```json
{
   "org.apache.sling.commons.log.names": [
      "com.example"
   ],
   "org.apache.sling.commons.log.level": "DEBUG",
   "org.apache.sling.commons.log.file": "logs/error.log",
   "org.apache.sling.commons.log.additiv": "false"
}
```

Laat het logbestand op het niveau van het DEBUG-logbestand niet langer dan nodig is, omdat dit veel items genereert.

De discrete logboekniveaus kunnen voor de verschillende AEM milieu&#39;s worden geplaatst gebruikend runtime op wijze-gebaseerde configuratie OSGi die als het wenselijk is om altijd bij te registreren `DEBUG` tijdens de ontwikkeling. Bijvoorbeeld:

| Omgeving | OSGi-configuratielocatie per uitvoeringsmodus | `org.apache.sling.commons.log.level` eigenschapswaarde |
| - | - | - |
| Ontwikkeling | /apps/example/config/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | DEBUG |
| Werkgebied | /apps/example/config.stage/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | WAARSCHUWING |
| Productie | /apps/example/config.prod/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | FOUT |

Een lijn in zuivert dossier begint gewoonlijk met DEBUG, en verstrekt dan het logboekniveau, de installeractie en het logboekbericht. Bijvoorbeeld:

```text
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

De logniveaus zijn als volgt:

| 0 | Fatale fout | De handeling is mislukt en het installatieprogramma kan niet doorgaan. |
|---|---|---|
| 1 | Fout | De handeling is mislukt. De installatie gaat door, maar een deel van CRX is niet correct geïnstalleerd en werkt niet. |
| 2 | Waarschuwing | De actie is geslaagd maar heeft problemen ondervonden. CRX werkt mogelijk niet correct. |
| 3 | Informatie | De actie is geslaagd. |

### Thread Dumps {#thread-dumps}

Thread dumps op Cloud-omgevingen worden voortdurend verzameld, maar kunnen op dit moment niet op een zelfserverende manier worden gedownload. Ondertussen, AEM de steun van het contact als de draaddumps voor het zuiveren van een kwestie nodig zijn, die het nauwkeurige tijdvenster specificeren.

## CRX/DE Lite en AEM as a Cloud Service Developer Console {#crxde-lite-and-developer-console}

### Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling hebben ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de AEM webconsole (`/system/console`).

Bij lokale ontwikkeling (met de SDK) `/apps` en `/libs` U kunt rechtstreeks naar deze map schrijven. Dit is anders dan in een cloud-omgeving waar deze mappen op hoofdniveau onveranderlijk zijn.

### AEM as a Cloud Service-ontwikkelingstools {#aem-as-a-cloud-service-development-tools}

>[!NOTE]
>De AEM as a Cloud Service Developer Console mag niet verward worden met de gelijksoortige naam [*Adobe Developer Console*](https://developer.adobe.com/developer-console/).
>

Klanten hebben toegang tot de CRXDE-lijst in de ontwikkelomgeving van de auteur, maar niet in het stadium of de productie. De onveranderlijke gegevensopslagruimte (`/libs`, `/apps`) kan niet worden geschreven naar bij uitvoering. Als u dit probeert, treedt er een fout op.

In plaats daarvan kan de Repository Browser worden gestart vanuit de AEM as a Cloud Service Developer Console, waarmee een alleen-lezen weergave in de opslagplaats wordt geboden voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen. Meer informatie over de Repository Browser [hier](/help/implementing/developing/tools/repository-browser.md).

Er is een set tools beschikbaar voor foutopsporing in AEM as a Cloud Service-ontwikkelomgevingen in de AEM as a Cloud Service Developer Console for RDE-, Dev-, stage- en productieomgevingen. De URL kan worden bepaald door de URL van de Auteur of Publish-service als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als sneltoets kunt u de volgende Cloud Manager CLI-opdracht gebruiken om de AEM as a Cloud Service Developer Console te starten op basis van een omgevingsparameter die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [deze pagina](/help/release-notes/home.md) voor meer informatie .

Ontwikkelaars kunnen statusinformatie genereren en diverse bronnen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eikenindexen, diensten OSGI, en het Sling banen.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Zoals hieronder geïllustreerd, kunnen de ontwikkelaars pakketgebiedsdelen en servlets oplossen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Ook nuttig voor het zuiveren, heeft AEM as a Cloud Service Developer Console een verbinding aan het Uitleg hulpmiddel van de Vraag:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

Voor productieprogramma&#39;s wordt de toegang tot de AEM as a Cloud Service Developer Console gedefinieerd door de &quot;Cloud Manager - Developer Role&quot; in de Adobe Admin Console, terwijl voor sandboxprogramma&#39;s de AEM as a Cloud Service Developer Console beschikbaar is voor gebruikers met een productprofiel dat hen toegang geeft tot AEM as a Cloud Service. Voor alle programma&#39;s is &quot;Cloud Manager - Developer Role&quot; nodig voor statusdumps en moeten de browser van de opslagplaats en gebruikers ook worden gedefinieerd in het productprofiel van AEM gebruikers of AEM beheerders voor zowel auteur- als publicatieservices om gegevens van beide services te bekijken. Zie voor meer informatie over het instellen van gebruikersmachtigingen [Cloud Manager-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).

### Prestatiebewaking {#performance-monitoring}

De Adobe bewaakt de prestaties van de toepassing en neemt maatregelen om verslechtering te verhelpen. Op dit moment kan de metrieke toepassing niet worden nageleefd.

## E-mail verzenden {#sending-email}

In de onderstaande secties wordt beschreven hoe u e-mail kunt aanvragen, configureren en verzenden.

>[!NOTE]
>
>De dienst van de Post kan met steun worden gevormd OAuth2. Zie voor meer informatie [OAuth2 Steun voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

### Uitgaande e-mail inschakelen {#enabling-outbound-email}

Standaard zijn poorten die worden gebruikt om e-mail te verzenden, uitgeschakeld. Om een haven te activeren, vorm [geavanceerd netwerken](/help/security/configuring-advanced-networking.md), waarbij u ervoor zorgt dat voor elke benodigde omgeving de `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` De haven die van het eindpunt regels door:sturen, die de voorgenomen haven (bijvoorbeeld, 465 of 587) aan een volmachtshaven in kaart brengt.

Het wordt geadviseerd om geavanceerd voorzien van een netwerk met te vormen `kind` parameter ingesteld op `flexiblePortEgress` aangezien de Adobe prestaties van flexibel havenuitgang verkeer kan optimaliseren. Als een uniek uitgangIP adres noodzakelijk is, kies een `kind` parameter van `dedicatedEgressIp`. Als u reeds VPN voor andere redenen hebt gevormd, kunt u het unieke IP adres gebruiken dat door die geavanceerde voorzien van een netwerkvariatie eveneens wordt verstrekt.

U moet e-mail via een e-mailserver verzenden in plaats van rechtstreeks naar e-mailclients. Anders kunnen de e-mailberichten geblokkeerd zijn.

### E-mails verzenden {#sending-emails}

De [Day CQ Mail Service OSGI](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service) moeten worden gebruikt en e-mails moeten worden verzonden naar de mailserver die in het supportverzoek wordt vermeld, en niet rechtstreeks naar ontvangers.

### Configuratie {#email-configuration}

E-mails in AEM moeten worden verzonden via de [Day CQ Mail Service OSGi-service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service).

Zie de [AEM 6.5-documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html) voor meer informatie over het configureren van e-mailinstellingen. Neem voor AEM as a Cloud Service de volgende noodzakelijke aanpassingen op in de `com.day.cq.mailer.DefaultMailService OSGI` service:

* De SMTP servergastheernaam zou aan $ moeten worden geplaatst[env:AEM_PROXY_HOST;default=proxy.tunnel]
* De SMTP serverhaven zou aan de waarde van de originele volmachtshaven moeten worden geplaatst die in de portForwards parameter wordt geplaatst in de API vraag wordt gebruikt wanneer het vormen van omhoog geavanceerd voorzien van een netwerk. Bijvoorbeeld, 30465 (eerder dan 465)

De SMTP serverhaven zou als `portDest` waarde die is ingesteld in de parameter portForwards die wordt gebruikt in de API-aanroep bij het configureren van geavanceerde netwerken en de `portOrig` De waarde moet een betekenisvolle waarde zijn die binnen het vereiste bereik van 30000 - 30999 ligt. Bijvoorbeeld, als de SMTP serverhaven 465 is, zou haven 30465 als moeten worden gebruikt `portOrig` waarde.

In dit geval, en het veronderstellen van SSL moet worden toegelaten, in de configuratie van **Day CQ Mail Service OSGI** service:

* Set `smtp.port` tot `30465`
* Set `smtp.ssl` tot `true`

Alternatief, als de bestemmingshaven 587 is, `portOrig` de waarde 30587 moet worden gebruikt. En ervan uitgaande dat SSL moet worden uitgeschakeld, de configuratie van de Day CQ Mail Service OSGI-service:

* Set `smtp.port` tot `30587`
* Set `smtp.ssl` tot `false`

De `smtp.starttls` Deze eigenschap wordt door AEM as a Cloud Service tijdens runtime automatisch op een geschikte waarde ingesteld. Als `smtp.ssl` is ingesteld op true, `smtp.startls` wordt genegeerd. Indien `smtp.ssl` is ingesteld op false, `smtp.starttls` is ingesteld op true. Dit is ongeacht `smtp.starttls` waarden die zijn ingesteld in uw OSGI-configuratie.


De dienst van de Post kan naar keuze met steun worden gevormd OAuth2. Zie voor meer informatie [OAuth2 Steun voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

### Verouderde e-mailconfiguratie {#legacy-email-configuration}

Vóór de release van 2021.9.0 werd e-mail geconfigureerd via een verzoek om klantenondersteuning. De volgende noodzakelijke aanpassingen in de `com.day.cq.mailer.DefaultMailService OSGI` service:

AEM as a Cloud Service vereist dat post wordt verzonden via poort 465. Als een mailserver poort 465 niet ondersteunt, kan poort 587 worden gebruikt, mits de optie TLS is ingeschakeld.

Indien haven 465 is aangevraagd:

* set `smtp.port` tot `465`
* set `smtp.ssl` tot `true`

en indien om poort 587 is verzocht:

* set `smtp.port` tot `587`
* set `smtp.ssl` tot `false`

De `smtp.starttls` Deze eigenschap wordt door AEM as a Cloud Service tijdens runtime automatisch op een geschikte waarde ingesteld. Als `smtp.ssl` is ingesteld op true, `smtp.startls` wordt genegeerd. Indien `smtp.ssl` is ingesteld op false, `smtp.starttls` is ingesteld op true. Dit is ongeacht `smtp.starttls` waarden die zijn ingesteld in uw OSGI-configuratie.

De SMTP servergastheer zou aan dat van uw postserver moeten worden geplaatst.

## Vermijd grote multi-value eigenschappen {#avoid-large-mvps}

De Oak-inhoudsopslagplaats die ten grondslag ligt aan AEM as a Cloud Service, is niet bedoeld voor gebruik met een buitensporig aantal MVP&#39;s (multi-value properties). Een duimregel is MVPs onder 1000 te houden. De werkelijke prestaties zijn echter afhankelijk van vele factoren.

De waarschuwingen worden geregistreerd door gebrek na meer dan 1000. Ze zijn vergelijkbaar met het volgende.

```text
org.apache.jackrabbit.oak.jcr.session.NodeImpl Large multi valued property [/path/to/property] detected (1029 values). 
```

Grote MVP&#39;s kunnen leiden tot fouten omdat het MongoDB-document groter is dan 16 MB, wat resulteert in fouten die lijken op de volgende.

```text
Caused by: com.mongodb.MongoWriteException: Resulting document after update is larger than 16777216
```

Zie de [Apache Oak-documentatie](https://jackrabbit.apache.org/oak/docs/dos_and_donts.html#Large_Multi_Value_Property) voor meer informatie .

## [!DNL Assets] ontwikkelingsrichtsnoeren en gebruiksgevallen {#use-cases-assets}

Ga voor meer informatie over de gebruiksgevallen, aanbevelingen en referentiematerialen voor Assets as a Cloud Service naar [Referenties voor ontwikkelaars voor Assets](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis).
