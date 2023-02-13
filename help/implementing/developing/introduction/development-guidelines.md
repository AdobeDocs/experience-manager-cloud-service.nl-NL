---
title: Ontwikkelingsrichtlijnen voor AEM as a Cloud Service
description: Leer richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM in gebouwen en AEM in AMS.
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
source-git-commit: 01087aa2ec621d6bebd4d62edbc320df8122f71d
workflow-type: tm+mt
source-wordcount: '2591'
ht-degree: 1%

---

# Ontwikkelingsrichtlijnen voor AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

>[!CONTEXTUALHELP]
>id="development_guidelines"
>title="Ontwikkelingsrichtlijnen voor AEM as a Cloud Service"
>abstract="Leer richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM in gebouwen en AEM in AMS."
>additional-url="https://video.tv.adobe.com/v/330555/" text="Demo van pakketstructuur"

Dit document bevat richtsnoeren voor de ontwikkeling van AEM as a Cloud Service en belangrijke manieren waarop het verschilt van AEM in gebouwen en AEM in AMS.

## Code moet clustervriendelijk zijn {#cluster-aware}

De code die in AEM as a Cloud Service loopt moet zich ervan bewust zijn dat het altijd in een cluster loopt. Dit betekent dat er altijd meer dan één instantie actief is. De code moet veerkrachtig zijn, vooral omdat een instantie op om het even welk ogenblik zou kunnen worden tegengehouden.

Tijdens de update van AEM as a Cloud Service, zullen er instanties zijn met oude en nieuwe code die parallel lopen. Daarom moet oude code niet breken met inhoud die door nieuwe code wordt gecreeerd en de nieuwe code moet oude inhoud kunnen behandelen.

Als de primaire code in de cluster moet worden geïdentificeerd, kan de API voor detectie van Apache Sling worden gebruikt om deze te detecteren.

## Staat in geheugen {#state-in-memory}

De staat moet niet in geheugen worden bewaard maar in bewaarplaats voortbestaan. Anders kan deze status verloren gaan als een instantie wordt gestopt.

## Status van het bestandssysteem {#state-on-the-filesystem}

Het bestandssysteem van de instantie mag niet worden gebruikt in AEM as a Cloud Service. De schijf is ephenaal en wordt verwijderd wanneer instanties worden gerecycled. Beperkt gebruik van het bestandssysteem voor tijdelijke opslag in verband met de verwerking van afzonderlijke aanvragen is mogelijk, maar mag niet worden misbruikt voor grote bestanden. Dit is omdat het een negatieve invloed op het hulpmiddelgebruiksquotum kan hebben en op schijfbeperkingen in werking kan stellen.

Als voorbeeld waar het gebruik van het dossiersysteem niet wordt gesteund, zou de Publish rij ervoor moeten zorgen dat om het even welke gegevens die moeten worden voortgeduurd naar een externe dienst voor opslag op langere termijn wordt verscheept.

## Waarneming {#observation}

Net als bij alles wat asynchroon gebeurt, zoals bij observatiegebeurtenissen, kan niet worden gegarandeerd dat het lokaal wordt uitgevoerd en moet het daarom met zorg worden gebruikt. Dit geldt zowel voor JCR-gebeurtenissen als voor Sling-brongebeurtenissen. Op het moment dat een wijziging plaatsvindt, kan de instantie worden verwijderd en worden vervangen door een andere instantie. Andere instanties in de topologie die op dat ogenblik actief zijn zullen op die gebeurtenis kunnen reageren. In dit geval zal dit echter geen lokale gebeurtenis zijn en is er misschien zelfs geen actieve leider in het geval van een doorlopende verkiezing van de leider op het moment dat het evenement wordt uitgegeven.

## Achtergrondtaken en langdurige taken {#background-tasks-and-long-running-jobs}

Code die als achtergrondtaken wordt uitgevoerd, moet ervan uitgaan dat de instantie waarin deze wordt uitgevoerd, op elk gewenst moment kan worden ingedrukt. Daarom moet de code veerkrachtig zijn, en het allerbelangrijkste herbruikbaar. Dat betekent dat als de code opnieuw wordt uitgevoerd, deze niet opnieuw van het begin moet beginnen, maar eerder dicht bij het punt waar de code is gebleven. Hoewel dit geen nieuw vereiste voor dit soort code is, is het in AEM as a Cloud Service waarschijnlijker dat een instantie zal verdwijnen.

Om de problemen tot een minimum te beperken, moeten zo mogelijk langdurige banen worden vermeden, en die moeten ten minste herbruikbaar zijn. Voor het uitvoeren van dergelijke banen gebruikt u Sling Jobs, die minstens eenmaal een garantie hebben en die daarom zo snel mogelijk opnieuw zal worden uitgevoerd als ze worden onderbroken. Maar ze zouden waarschijnlijk niet opnieuw van het begin moeten beginnen. Voor het plannen van dergelijke taken kunt u het beste de opdracht [Verkooptaken](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) planner als dit opnieuw verzekert minstens eenmaal uitvoering.

De Sling Commons Planner zou niet voor het plannen moeten worden gebruikt aangezien de uitvoering niet kan worden gewaarborgd. Het is nog waarschijnlijker dat het zal worden gepland.

Op dezelfde manier, met alles dat asynchroon gebeurt, zoals handelend op observatiegebeurtenissen, (het zijn gebeurtenissen JCR of Sling resource), kan niet gegarandeerd worden uitgevoerd en daarom met voorzichtigheid worden gebruikt. Dit geldt al voor AEM implementaties in het heden.

## Uitgaande HTTP-verbindingen {#outgoing-http-connections}

Het wordt sterk geadviseerd dat om het even welke uitgaande verbindingen van HTTP redelijk plaatsen verbind en lees onderbrekingen; De voorgestelde waarden zijn 1 seconde voor de verbindingsperiode en 5 seconden voor read timeout. De nauwkeurige aantallen moeten worden bepaald gebaseerd op de prestaties van het backend systeem die deze verzoeken behandelen.

Voor code die deze time-outs niet toepast, AEM instanties die op AEM as a Cloud Service worden uitgevoerd een algemene time-out afdwingen. Deze onderbrekingswaarden zijn 10 seconden voor verbind vraag en 60 seconden voor gelezen vraag naar verbindingen.

Adobe raadt het gebruik van de meegeleverde [Apache HttpComponents Client 4.x-bibliotheek](https://hc.apache.org/httpcomponents-client-ga/) voor het maken van HTTP-verbindingen.

Alternatieven waarvan bekend is dat ze werken, maar waarvoor de afhankelijkheid zelf nodig kan zijn, zijn:

* [java.net.URL](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URL.html) en/of [java.net.URLConnection](https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/net/URLConnection.html) (Door AEM verstrekt)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/) (niet aanbevolen omdat het verouderd is en wordt vervangen door versie 4.x)
* [OK Http](https://square.github.io/okhttp/) (Niet verstrekt door AEM)

Naast het verstrekken van onderbrekingen ook zou een juiste behandeling van dergelijke onderbrekingen evenals onverwachte HTTP- statuscodes moeten worden uitgevoerd.

## Geen Klassieke UI-aanpassingen {#no-classic-ui-customizations}

AEM as a Cloud Service ondersteunt alleen de Touch UI voor klantcode van derden. Klassieke UI is niet beschikbaar voor aanpassing.

## Native binaire getallen vermijden {#avoid-native-binaries}

Code kan geen binaire bestanden downloaden tijdens runtime en deze niet wijzigen. Het kan bijvoorbeeld niet uitpakken `jar` of `tar` bestanden.

## Geen streamingbinders via AEM as a Cloud Service {#no-streaming-binaries}

De binaire getallen zouden door CDN moeten worden betreden, die binaire getallen buiten de kern AEM diensten zal dienen.

Niet gebruiken `asset.getOriginal().getStream()`, die het downloaden van binair binair getal op de van de dienst van de AEM in werking stelt.

## Geen reverse Replication-agents {#no-reverse-replication-agents}

De omgekeerde replicatie van Publiceren aan Auteur wordt niet gesteund in AEM as a Cloud Service. Als een dergelijke strategie nodig is, kunt u een externe persistentieopslag gebruiken die onder het landbouwbedrijf van Publish instanties en potentieel de cluster van de Auteur wordt gedeeld.

## De voorwaartse Medewerkers van de Replicatie zouden kunnen moeten worden gesteund {#forward-replication-agents}

Inhoud wordt van Auteur naar Publiceren gerepliceerd via een submechanisme. Aangepaste replicatiemiddelen worden niet ondersteund.

## Controle en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

Voor lokale ontwikkeling worden logbestandvermeldingen geschreven naar lokale bestanden in het dialoogvenster `/crx-quickstart/logs` map.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Logniveau instellen**

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
>Om de hieronder vermelde configuratieveranderingen uit te voeren, moet u hen op een lokale ontwikkelomgeving tot stand brengen en dan hen duwen aan een AEM as a Cloud Service instantie. Ga voor meer informatie over hoe u dit kunt doen naar [Distribueren naar AEM as a Cloud Service](/help/implementing/deploying/overview.md).

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

| Milieu | OSGi-configuratielocatie per uitvoeringsmodus | `org.apache.sling.commons.log.level` eigenschapswaarde | | - | - | - | | Ontwikkeling | /apps/example/config/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | DEBUG | | Fase | /apps/example/config.stage/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | WAARSCHUWING | | Productie | /apps/example/config.prod/org.apache.sling.commons.log.LogManager.factory.config~example.cfg.json | FOUT |

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

Thread dumps op Cloud-omgevingen worden voortdurend verzameld, maar kunnen op dit moment niet op een zelfserverende manier worden gedownload. Ondertussen, gelieve te contacteren AEM steun als de draaddumps voor het zuiveren van een kwestie nodig zijn, specificerend het nauwkeurige tijdvenster.

## CRX/DE Lite en de Console van de Ontwikkelaar {#crxde-lite-and-developer-console}

### Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling hebben ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de AEM webconsole (`/system/console`).

Merk op dat bij lokale ontwikkeling (met behulp van de SDK), `/apps` en `/libs` U kunt rechtstreeks naar deze map schrijven. Dit is anders dan in een cloud-omgeving waar deze mappen op hoofdniveau onveranderlijk zijn.

### as a Cloud Service ontwikkelingsinstrumenten AEM {#aem-as-a-cloud-service-development-tools}

Klanten hebben toegang tot de CRXDE-lijst in de ontwikkelomgeving van de auteur, maar niet in het stadium of de productie. De onveranderlijke gegevensopslagruimte (`/libs`, `/apps`) kan niet worden geschreven naar bij uitvoering. Als u dit probeert, treedt er een fout op.

In plaats daarvan kan de Repository Browser worden gestart vanuit de Developer Console, waarmee een alleen-lezen weergave in de opslagplaats wordt geboden voor alle omgevingen op auteur-, publicatie- en voorvertoningslagen. Meer informatie over de Repository Browser [hier](/help/implementing/developing/tools/repository-browser.md).

Een reeks hulpmiddelen voor het zuiveren AEM as a Cloud Service ontwikkelaarmilieu&#39;s zijn beschikbaar in de Console van de Ontwikkelaar voor RDE, dev, stadium, en productiemilieu&#39;s. De URL kan worden bepaald door de URL van de service Auteur of Publiceren als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als kortere weg, kan het volgende CLI bevel van de Manager van de Wolk worden gebruikt om de ontwikkelaarsconsole te lanceren die op een milieuparameter wordt gebaseerd die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [deze pagina](/help/release-notes/home.md) voor meer informatie .

Ontwikkelaars kunnen statusinformatie genereren en diverse bronnen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eikenindexen, diensten OSGI, en het Sling banen.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Zoals hieronder geïllustreerd, kunnen de ontwikkelaars pakketgebiedsdelen en servlets oplossen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Ook nuttig voor het zuiveren, heeft de console van de Ontwikkelaar een verbinding aan het Uitleg hulpmiddel van de Vraag:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

Voor productieprogramma&#39;s wordt de toegang tot de Developer Console gedefinieerd door &quot;Cloud Manager - Developer Role&quot; in de Admin Console, terwijl voor sandboxprogramma&#39;s de Developer Console beschikbaar is voor elke gebruiker met een productprofiel dat hem toegang geeft tot AEM as a Cloud Service. Voor alle programma&#39;s is &quot;Cloud Manager - Developer Role&quot; vereist voor statusdumps en moeten de browser van de opslagplaats en gebruikers ook worden gedefinieerd in het productprofiel van AEM gebruikers of AEM beheerders voor zowel auteur- als publicatieservices om gegevens van beide services te kunnen bekijken. Voor meer informatie over het instellen van gebruikersmachtigingen raadpleegt u [Documentatie voor Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html).

### Prestatiebewaking {#performance-monitoring}

Adobe bewaakt de prestaties van de toepassing en neemt maatregelen om verslechtering te verhelpen. Op dit moment kunnen maatgegevens van toepassingen niet worden nageleefd.

## E-mail verzenden {#sending-email}

In de onderstaande secties wordt beschreven hoe u e-mail kunt aanvragen, configureren en verzenden.

>[!NOTE]
>
>De dienst van de Post kan met steun worden gevormd OAuth2. Zie voor meer informatie [OAuth2 Steun voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

### Uitgaande e-mail inschakelen {#enabling-outbound-email}

Standaard zijn poorten die worden gebruikt om e-mail te verzenden, uitgeschakeld. Om een haven te activeren, vorm [geavanceerde netwerken](/help/security/configuring-advanced-networking.md), waarbij u ervoor zorgt dat voor elke benodigde omgeving de `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` De haven die van het eindpunt regels door:sturen, die de voorgenomen haven (bijvoorbeeld, 465 of 587) aan een volmachtshaven in kaart brengt.

Het wordt geadviseerd om geavanceerd voorzien van een netwerk met te vormen `kind` parameter ingesteld op `flexiblePortEgress` aangezien Adobe de prestaties van flexibel havenuitgang verkeer kan optimaliseren. Als een uniek uitgangIP adres noodzakelijk is, kies een `kind` parameter van `dedicatedEgressIp`. Als u reeds VPN voor andere redenen hebt gevormd, kunt u het unieke IP adres gebruiken dat door die geavanceerde voorzien van een netwerkvariatie eveneens wordt verstrekt.

U moet e-mail via een e-mailserver verzenden in plaats van rechtstreeks naar e-mailclients. Anders kunnen de e-mailberichten geblokkeerd zijn.

### E-mails verzenden {#sending-emails}

De [Day CQ Mail Service OSGI-service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service) moeten worden gebruikt en e-mails moeten worden verzonden naar de mailserver die in het supportverzoek wordt vermeld, en niet rechtstreeks naar ontvangers.

### Configuratie {#email-configuration}

E-mails in AEM moeten worden verzonden via de [Day CQ Mail Service OSGi-service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service).

Zie de [AEM 6.5-documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html) voor meer informatie over het configureren van e-mailinstellingen. Voor AEM as a Cloud Service, noteer de volgende noodzakelijke aanpassingen aan `com.day.cq.mailer.DefaultMailService OSGI` service:

* De SMTP servergastheernaam zou aan $ moeten worden geplaatst[env:AEM_PROXY_HOST;default=proxy.tunnel]
* De SMTP serverhaven zou aan de waarde van de originele volmachtshaven moeten worden geplaatst die in de portForwards parameter wordt geplaatst in de API vraag wordt gebruikt wanneer het vormen van omhoog geavanceerd voorzien van een netwerk. Bijvoorbeeld, 30465 (eerder dan 465)

De SMTP serverhaven zou als `portDest` waarde die is ingesteld in de parameter portForwards die wordt gebruikt in de API-aanroep bij het configureren van geavanceerde netwerken en de `portOrig` De waarde moet een betekenisvolle waarde zijn die binnen het vereiste bereik van 30000 - 30999 ligt. Bijvoorbeeld, als de SMTP serverhaven 465 is, zou haven 30465 als moeten worden gebruikt `portOrig` waarde.

In dit geval en het veronderstellen van SSL moet worden toegelaten, in de configuratie van **Day CQ Mail Service OSGI** service:

* Set `smtp.port` tot `30465`
* Set `smtp.ssl` tot `true`

Alternatief, als de bestemmingshaven 587 is, `portOrig` de waarde 30587 moet worden gebruikt. En ervan uitgaande dat SSL moet worden uitgeschakeld, de configuratie van de Day CQ Mail Service OSGI-service:

* Set `smtp.port` tot `30587`
* Set `smtp.ssl` tot `false`

De `smtp.starttls` eigenschap wordt automatisch door AEM as a Cloud Service bij uitvoering ingesteld op een geschikte waarde. Als `smtp.ssl` is ingesteld op true, `smtp.startls` wordt genegeerd. Indien `smtp.ssl` is ingesteld op false, `smtp.starttls` is ingesteld op true. Dit is ongeacht `smtp.starttls` waarden die zijn ingesteld in uw OSGI-configuratie.


De dienst van de Post kan naar keuze met steun worden gevormd OAuth2. Zie voor meer informatie [OAuth2 Steun voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

### Verouderde e-mailconfiguratie {#legacy-email-configuration}

Vóór de release van 2021.9.0 werd e-mail geconfigureerd via een verzoek om klantenondersteuning. De volgende noodzakelijke aanpassingen in de `com.day.cq.mailer.DefaultMailService OSGI` service:

AEM as a Cloud Service vereist dat de post door haven 465 wordt verzonden. Als een mailserver poort 465 niet ondersteunt, kan poort 587 worden gebruikt, mits de optie TLS is ingeschakeld.

Indien haven 465 is aangevraagd:

* set `smtp.port` tot `465`
* set `smtp.ssl` tot `true`

en indien om poort 587 is verzocht:

* set `smtp.port` tot `587`
* set `smtp.ssl` tot `false`

De `smtp.starttls` eigenschap wordt automatisch door AEM as a Cloud Service bij uitvoering ingesteld op een geschikte waarde. Als `smtp.ssl` is ingesteld op true, `smtp.startls` wordt genegeerd. Indien `smtp.ssl` is ingesteld op false, `smtp.starttls` is ingesteld op true. Dit is ongeacht `smtp.starttls` waarden die zijn ingesteld in uw OSGI-configuratie.

De SMTP servergastheer zou aan dat van uw postserver moeten worden geplaatst.

## Vermijd grote multi-value eigenschappen {#avoid-large-mvps}

De opslagplaats van de Eak-inhoud die AEM as a Cloud Service steunt is niet bedoeld om met een bovenmatig aantal multi-value eigenschappen (MVPs) te worden gebruikt. MVP&#39;s zijn lager dan 1000 en daarom is het handig deze regel te handhaven. De werkelijke prestaties zijn echter afhankelijk van vele factoren.

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

Raadpleeg voor meer informatie over de gevallen, aanbevelingen en referentiematerialen voor as a Cloud Service middelen van het ontwikkelingstoepassingsprogramma de [Referenties voor ontwikkelaars voor Middelen.](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis)
