---
title: Ontwikkelingsrichtlijnen voor AEM as a Cloud Service
description: Ontwikkelingsrichtlijnen voor AEM as a Cloud Service
exl-id: 94cfdafb-5795-4e6a-8fd6-f36517b27364
source-git-commit: c9ebeefa2a8707cbbf43df15cf90c10aadbba45f
workflow-type: tm+mt
source-wordcount: '2059'
ht-degree: 2%

---

# Ontwikkelingsrichtlijnen voor AEM as a Cloud Service {#aem-as-a-cloud-service-development-guidelines}

De code die in AEM as a Cloud Service loopt moet zich ervan bewust zijn dat het altijd in een cluster loopt. Dit betekent dat er altijd meer dan één instantie actief is. De code moet veerkrachtig zijn, vooral omdat een instantie op om het even welk ogenblik zou kunnen worden tegengehouden.

Tijdens de update van AEM as a Cloud Service, zullen er instanties zijn met oude en nieuwe code die parallel lopen. Daarom moet oude code niet breken met inhoud die door nieuwe code wordt gecreeerd en de nieuwe code moet oude inhoud kunnen behandelen.
<!--

>[!NOTE]
> All of the best practices mentioned here hold true for on-premise deployments of AEM, if not stated otherwise. An instance can always stop due to various reasons. However, with Skyline it is more likely to happen therefore an instance stopping is the rule not an exception.

-->

Als de primaire code in de cluster moet worden geïdentificeerd, kan de API voor detectie van Apache Sling worden gebruikt om deze te detecteren.

## Staat in geheugen {#state-in-memory}

De staat moet niet in geheugen worden bewaard maar in bewaarplaats voortbestaan. Anders kan deze status verloren gaan als een instantie wordt gestopt.

## Status van het bestandssysteem {#state-on-the-filesystem}

Het bestandssysteem van de instantie mag niet worden gebruikt in AEM as a Cloud Service. De schijf is ephenaal en wordt verwijderd wanneer instanties worden gerecycled. Beperkt gebruik van het bestandssysteem voor tijdelijke opslag in verband met de verwerking van afzonderlijke aanvragen is mogelijk, maar mag niet worden misbruikt voor grote bestanden. Dit is omdat het een negatieve invloed op het hulpmiddelgebruiksquotum kan hebben en op schijfbeperkingen in werking kan stellen.

Als voorbeeld waar het gebruik van het dossiersysteem niet wordt gesteund, zou de Publish rij ervoor moeten zorgen dat om het even welke gegevens die moeten worden voortgeduurd naar een externe dienst voor opslag op langere termijn wordt verscheept.

## Waarneming {#observation}

Net als bij alles wat asynchroon gebeurt, zoals bij observatiegebeurtenissen, kan niet worden gegarandeerd dat het lokaal wordt uitgevoerd en moet het daarom met zorg worden gebruikt. Dit geldt zowel voor JCR-gebeurtenissen als voor Sling-brongebeurtenissen. Op het moment dat een wijziging plaatsvindt, kan de instantie worden verwijderd en worden vervangen door een andere instantie. Andere instanties in de topologie die op dat ogenblik actief zijn zullen op die gebeurtenis kunnen reageren. In dit geval zal dit echter geen lokale gebeurtenis zijn en is er misschien zelfs geen actieve leider in het geval van een doorlopende verkiezing van de leider op het moment dat het evenement wordt uitgegeven.

## Achtergrondtaken en langdurige taken {#background-tasks-and-long-running-jobs}

Code die als achtergrondtaken wordt uitgevoerd, moet ervan uitgaan dat de instantie waarin deze wordt uitgevoerd, op elk gewenst moment kan worden ingedrukt. Daarom moet de code veerkrachtig zijn en het meest invoer herbruikbaar. Dat betekent dat als de code opnieuw wordt uitgevoerd, deze niet opnieuw van het begin moet beginnen, maar eerder dicht bij het punt waar de code is gebleven. Hoewel dit geen nieuw vereiste voor dit soort code is, is het in AEM as a Cloud Service waarschijnlijker dat een instantie zal verdwijnen.

Om de problemen tot een minimum te beperken, moeten zo mogelijk langdurige banen worden vermeden, en die moeten ten minste herbruikbaar zijn. Voor het uitvoeren van dergelijke banen gebruikt u Sling Jobs, die minstens eenmaal een garantie hebben en die daarom zo snel mogelijk opnieuw zal worden uitgevoerd als ze worden onderbroken. Maar ze zouden waarschijnlijk niet opnieuw van het begin moeten beginnen. Voor het plannen van dergelijke banen, is het best om [Sling Jobs](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#jobs-guarantee-of-processing) planner als dit opnieuw minstens eens uitvoering te gebruiken.

De Sling Commons Planner zou niet voor het plannen moeten worden gebruikt aangezien de uitvoering niet kan worden gewaarborgd. Het is nog waarschijnlijker dat het zal worden gepland.

Op dezelfde manier, met alles dat asynchroon gebeurt, zoals handelend op observatiegebeurtenissen, (het zijn gebeurtenissen JCR of Sling resource), kan niet gegarandeerd worden uitgevoerd en daarom met voorzichtigheid worden gebruikt. Dit geldt al voor AEM implementaties in het heden.

## Uitgaande HTTP-verbindingen {#outgoing-http-connections}

Het wordt sterk geadviseerd dat om het even welke uitgaande verbindingen van HTTP redelijk plaatsen verbind en lees onderbrekingen. Voor code die deze time-outs niet toepast, AEM instanties die op AEM as a Cloud Service worden uitgevoerd een algemene time-out afdwingen. Deze onderbrekingswaarden zijn 10 seconden voor verbind vraag en 60 seconden voor gelezen vraag naar verbindingen die door de volgende populaire bibliotheken van Java worden gebruikt:

Adobe raadt het gebruik aan van de meegeleverde [Apache HttpComponents Client 4.x library](https://hc.apache.org/httpcomponents-client-ga/) voor het maken van HTTP-verbindingen.

Alternatieven waarvan bekend is dat ze werken, maar waarvoor de afhankelijkheid zelf nodig kan zijn, zijn:

* [java.net.](https://docs.oracle.com/javase/7/docs/api/java/net/URL.html) URLand/or  [java.net.URLConnection](https://docs.oracle.com/javase/7/docs/api/java/net/URLConnection.html) (Provided by AEM)
* [Apache Commons HttpClient 3.x](https://hc.apache.org/httpclient-3.x/)  (niet aanbevolen omdat deze verouderd is en vervangen wordt door versie 4.x)
* [OK Http](https://square.github.io/okhttp/)  (niet opgegeven door AEM)

## Geen Klassieke UI-aanpassingen {#no-classic-ui-customizations}

AEM as a Cloud Service ondersteunt alleen de Touch UI voor klantcode van derden. Klassieke UI is niet beschikbaar voor aanpassing.

## Native binaire getallen vermijden {#avoid-native-binaries}

Code kan geen binaire bestanden downloaden tijdens runtime en deze niet wijzigen. Het is bijvoorbeeld niet mogelijk om `jar`- of `tar`-bestanden uit te pakken.

## Geen streamingbinders via AEM as a Cloud Service {#no-streaming-binaries}

De binaire getallen zouden door CDN moeten worden betreden, die binaire getallen buiten de kern AEM diensten zal dienen.

Gebruik bijvoorbeeld `asset.getOriginal().getStream()` niet, waardoor het downloaden van een binair getal op de vaste schijf van de AEM service wordt geactiveerd.

## Geen reverse Replication-agents {#no-reverse-replication-agents}

De omgekeerde replicatie van Publiceren aan Auteur wordt niet gesteund in AEM as a Cloud Service. Als een dergelijke strategie nodig is, kunt u een externe persistentieopslag gebruiken die onder het landbouwbedrijf van Publish instanties en potentieel de cluster van de Auteur wordt gedeeld.

## De voorwaartse Medewerkers van de Replicatie zouden kunnen moeten worden gesteund {#forward-replication-agents}

Inhoud wordt van Auteur naar Publiceren gerepliceerd via een submechanisme. Aangepaste replicatiemiddelen worden niet ondersteund.

## Controle en foutopsporing {#monitoring-and-debugging}

### Logboeken {#logs}

Voor lokale ontwikkeling worden logbestandvermeldingen geschreven naar lokale bestanden in de map `/crx-quickstart/logs`.

In cloudomgevingen kunnen ontwikkelaars logbestanden downloaden via Cloud Manager of een opdrachtregelprogramma gebruiken om de logbestanden vast te zetten. <!-- See the [Cloud Manager documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) for more details. Note that custom logs are not supported and so all logs should be output to the error log. -->

**Logniveau instellen**

Om de logboekniveaus voor de milieu&#39;s van de Wolk te veranderen, zou de het Registreren van de Sling configuratie OSGI moeten worden gewijzigd, gevolgd door een volledige herplaatsing. Aangezien dit niet onmiddellijk is, ben voorzichtig om uitgebreide logboeken op productiemilieu&#39;s toe te laten die veel verkeer ontvangen. In de toekomst is het mogelijk dat er mechanismen zijn om het logniveau sneller te wijzigen.

>[!NOTE]
>
>Om de hieronder vermelde configuratieveranderingen uit te voeren, moet u hen op een lokale ontwikkelomgeving tot stand brengen en dan hen duwen aan een AEM as a Cloud Service instantie. Voor meer informatie over hoe te om dit te doen, zie [Het opstellen aan AEM as a Cloud Service](/help/implementing/deploying/overview.md).

**Het FOUTOPSPORINGSlogniveau activeren**

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

### Thread Dumps {#thread-dumps}

Thread dumps op Cloud-omgevingen worden voortdurend verzameld, maar kunnen op dit moment niet op een zelfserverende manier worden gedownload. Ondertussen, gelieve te contacteren AEM steun als de draaddumps voor het zuiveren van een kwestie nodig zijn, specificerend het nauwkeurige tijdvenster.

## CRX/DE Lite en de Console van de Ontwikkelaar {#crxde-lite-and-developer-console}

### Lokale ontwikkeling {#local-development}

Voor lokale ontwikkeling, hebben de Ontwikkelaars volledige toegang tot CRXDE Lite (`/crx/de`) en de AEMConsole van het Web (`/system/console`).

Bij lokale ontwikkeling (met behulp van de SDK) kunnen `/apps` en `/libs` rechtstreeks worden geschreven, wat anders is dan in cloudomgevingen waar deze mappen op hoofdniveau onveranderlijk zijn.

### as a Cloud Service ontwikkelingsinstrumenten AEM {#aem-as-a-cloud-service-development-tools}

Klanten hebben toegang tot de CRXDE-lijst in de ontwikkelomgeving van de auteur, maar niet in het stadium of de productie. De onveranderlijke bewaarplaats (`/libs`, `/apps`) kan niet aan bij runtime worden geschreven zodat het proberen dit in fouten resulteert.

In de Developer Console for dev, stage, and production environment is een set tools beschikbaar voor foutopsporing AEM as a Cloud Service ontwikkelaarsomgevingen. De URL kan worden bepaald door de URL van de service Auteur of Publiceren als volgt aan te passen:

`https://dev-console/-<namespace>.<cluster>.dev.adobeaemcloud.com`

Als kortere weg, kan het volgende CLI bevel van de Manager van de Wolk worden gebruikt om de ontwikkelaarsconsole te lanceren die op een milieuparameter wordt gebaseerd die hieronder wordt beschreven:

`aio cloudmanager:open-developer-console <ENVIRONMENTID> --programId <PROGRAMID>`

Zie [deze pagina](/help/release-notes/home.md) voor meer informatie.

Ontwikkelaars kunnen statusinformatie genereren en diverse bronnen oplossen.

Zoals hieronder wordt geïllustreerd, omvat de beschikbare statusinformatie de staat van bundels, componenten, configuraties OSGI, eikenindexen, diensten OSGI, en het Sling banen.

![Dev Console 1](/help/implementing/developing/introduction/assets/devconsole1.png)

Zoals hieronder geïllustreerd, kunnen de ontwikkelaars pakketgebiedsdelen en servlets oplossen:

![Dev Console 2](/help/implementing/developing/introduction/assets/devconsole2.png)

![Dev Console 3](/help/implementing/developing/introduction/assets/devconsole3.png)

Ook nuttig voor het zuiveren, heeft de console van de Ontwikkelaar een verbinding aan het Uitleg hulpmiddel van de Vraag:

![Dev Console 4](/help/implementing/developing/introduction/assets/devconsole4.png)

Voor productieprogramma&#39;s wordt de toegang tot de Developer Console gedefinieerd door &quot;Cloud Manager - Developer Role&quot; in de Admin Console, terwijl voor sandboxprogramma&#39;s de Developer Console beschikbaar is voor elke gebruiker met een productprofiel dat hem toegang geeft tot AEM as a Cloud Service. Voor alle programma&#39;s is &quot;Cloud Manager - rol ontwikkelaar&quot; nodig voor statusdumps en moeten gebruikers ook worden gedefinieerd in het productprofiel van AEM gebruikers of AEM beheerders voor zowel auteur- als publicatieservices om statusstortgegevens van beide services te bekijken. Zie [Documentatie van Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/requirements/setting-up-users-and-roles.html) voor meer informatie over het instellen van gebruikersmachtigingen.

### AEM Staging- en productieservice {#aem-staging-and-production-service}

Klanten hebben geen toegang tot ontwikkelaarstools voor testomgevingen en productieomgevingen.

### Prestatiebewaking {#performance-monitoring}

Adobe bewaakt de prestaties van de toepassing en neemt maatregelen om verslechtering te verhelpen. Op dit moment kunnen maatgegevens van toepassingen niet worden nageleefd.

## E-mail verzenden {#sending-email}

AEM as a Cloud Service vereist dat uitgaande post wordt gecodeerd. In de onderstaande secties wordt beschreven hoe u e-mail kunt aanvragen, configureren en verzenden.

>[!NOTE]
>
>De dienst van de Post kan met steun worden gevormd OAuth2. Voor meer informatie, zie [Steun OAuth2 voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

### Uitgaande e-mail inschakelen {#enabling-outbound-email}

Standaard zijn de poorten die worden gebruikt voor verzending uitgeschakeld. Om het te activeren, vorm [geavanceerde voorzien van een netwerk](/help/security/configuring-advanced-networking.md), ervoor zorgend om voor elk nodig milieu de haven van `PUT /program/<program_id>/environment/<environment_id>/advancedNetworking` het eindpunt door:sturen regels te plaatsen zodat het verkeer door haven 465 (indien gesteund door de postserver) of haven 587 (als de postserver het vereist en ook TLS op die haven) afdwingt.

Het wordt aanbevolen geavanceerde netwerken te configureren met een `kind`-parameter ingesteld op `flexiblePortEgress`, omdat Adobe de prestaties van flexibel poortegress-verkeer kan optimaliseren. Als een uniek uitgangIP adres noodzakelijk is, kies een `kind` parameter van `dedicatedEgressIp`. Als u reeds VPN voor andere redenen hebt gevormd, kunt u het unieke IP adres gebruiken dat door die geavanceerde voorzien van een netwerkvariatie eveneens wordt verstrekt.

U moet e-mail via een e-mailserver verzenden in plaats van rechtstreeks naar e-mailclients. Anders kunnen de e-mailberichten geblokkeerd zijn.

### E-mails verzenden {#sending-emails}

De [Day CQ Mail Service OSGI-service](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service) moet worden gebruikt en e-mails moeten worden verzonden naar de mailserver die in het supportverzoek is aangegeven, en niet rechtstreeks naar ontvangers.

AEM as a Cloud Service vereist dat de post door haven 465 wordt verzonden. Als een mailserver poort 465 niet ondersteunt, kan poort 587 worden gebruikt, mits de optie TLS is ingeschakeld.

### Configuratie {#email-configuration}

E-mails in AEM moeten worden verzonden met de OSGi-service ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html#configuring-the-mail-service) van de [Day CQ-mailservice.

Zie [AEM 6.5 documentatie](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/notification.html) voor meer informatie over het configureren van e-mailinstellingen. Voor AEM as a Cloud Service, moeten de volgende aanpassingen aan de `com.day.cq.mailer.DefaultMailService OSGI` dienst worden aangebracht:

Indien haven 465 is aangevraagd:

* `smtp.port` instellen op `465`
* `smtp.ssl` instellen op `true`

Als poort 587 is aangevraagd (alleen toegestaan als de mailserver poort 465 niet ondersteunt):

* `smtp.port` instellen op `587`
* `smtp.ssl` instellen op `false`

De eigenschap `smtp.starttls` wordt automatisch door AEM as a Cloud Service bij uitvoering op een geschikte waarde ingesteld. Als `smtp.tls` is ingesteld op true, wordt `smtp.startls` dus genegeerd. Wanneer `smtp.ssl` op false is ingesteld, wordt `smtp.starttls` op true ingesteld. Dit is ongeacht de `smtp.starttls` waarden die in uw configuratie worden geplaatst OSGI.

De dienst van de Post kan naar keuze met steun worden gevormd OAuth2. Voor meer informatie, zie [Steun OAuth2 voor de Dienst van de Post](/help/security/oauth2-support-for-mail-service.md).

## [!DNL Assets] ontwikkelingsrichtsnoeren en gebruiksgevallen {#use-cases-assets}

Zie [Verwijzingen voor ontwikkelaars voor Elementen](/help/assets/developer-reference-material-apis.md#assets-cloud-service-apis) voor informatie over de gevallen, aanbevelingen en referentiematerialen voor ontwikkelaars die zijn as a Cloud Service.
