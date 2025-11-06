---
title: Inleiding tot CI/CD-pijpleidingen
description: Leer meer over Cloud Manager CI/CD pijpleidingen en hoe zij kunnen worden gebruikt om uw code efficiënt op te stellen.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1546'
ht-degree: 0%

---


# Cloud Manager CI/CD Pipelines {#intro-cicd}

Leer meer over Cloud Manager CI/CD (Continuous Integration/Continuous Delivery) pijpleidingen en hoe zij kunnen worden gebruikt om uw code efficiënt op te stellen.

## Inleiding tot CI/CD-pijpleidingen {#introduction}

Een CI/CD pijpleiding in Cloud Manager is een mechanisme om code van een bronbewaarplaats te bouwen en het in een milieu op te stellen. Een gebeurtenis activeert een pijpleiding, zoals een trekkrachtverzoek van een broncodebewaarplaats zoals Git (namelijk een codeverandering). Of het kan worden geactiveerd volgens een regulier schema om overeen te komen met een releasecadence.

Om een pijpleiding te vormen, moet u het volgende doen:

* Bepaal de trekker die de pijpleiding begint.
* Definieer de parameters die de productieplaatsing controleren.
* Configureer de testparameters voor prestaties.

Cloud Manager biedt twee soorten pijpleidingen:

* [Productiepijpleidingen](#prod-pipeline)
* [Niet-productiepijpleidingen](#non-prod-pipeline)

![ Types van pijpleidingen ](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Productiepijpleidingen {#prod-pipeline}

Een productiepijpleiding is een doelgerichte pijpleiding die een reeks georkestreerde stappen omvat om broncode voor productiegebruik op te stellen. De stappen omvatten eerste het bouwen, het verpakken, het testen, het bevestigen, en het opstellen in alle het opvoeren milieu&#39;s. Daarom kan een productiepijpleiding slechts worden toegevoegd zodra een reeks productie en het opvoeren milieu&#39;s wordt gecreeerd.

>[!TIP]
>
>Zie [ een productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) vormen.

## Niet-productiepijpleidingen {#non-prod-pipeline}

Een niet-productiepijpleiding dient hoofdzakelijk om codescannen in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

>[!TIP]
>
>Zie [ een non-production pijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) vormen.

## Codebronnen {#code-sources}

De pijpleidingen kunnen ook verschillen door het type van code zij, naast productie en niet-productiemilieu&#39;s opstellen.

* **[Volledige stapelpijpleidingen](#full-stack-pipeline)** - stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere de servertoepassingen van AEM samen met configuraties HTTPD/Dispatcher bevatten.
* **[Config pijpleidingen](#config-deployment-pipeline)** - u kunt configuraties voor eigenschappen zoals logboek snel opstellen door:sturen en op zuivering betrekking hebbende onderhoudstaken. Het omvat ook diverse configuraties CDN (het Netwerk van de Levering van de Inhoud), zoals de regels van de verkeersfilter, met inbegrip van de regels van de Firewall van de Toepassing van het Web (WAF). Daarnaast kunt u verzoek- en responstransformaties, oorspronkelijke kiezers, omleidingen aan de clientzijde, foutpagina&#39;s, CDN-sleutels, opruimAPI-sleutels en basisverificatie beheren. Zie [ pijpleidingen van Configuratie van het Gebruik ](/help/operations/config-pipeline.md) voor details.
* **[voorste-eindpijpleidingen](#front-end)** - stel front-end code bouwt die één of meerdere cliënt-zijtoepassingen van het gebruikersinterface bevatten.
* **[de pijpleidingen van Config van de rij van het Web](#web-tier-config-pipelines)** - stelt configuraties HTTPD/Dispatcher op.

Deze pijpleidingstypes worden beschreven in detail later in dit document.

### I.C.-CD pijpleidingen in Cloud Manager begrijpen {#understand-pipelines}

De volgende tabel geeft een overzicht van de in Cloud Manager beschikbare pijpleidingen en het gebruik ervan.

| Type pijpleiding | Implementatie- of codekwaliteit | Source-code | Doel | Notities |
| --- | --- | --- | --- | ---|
| Productie of niet-productie | Implementatie | Volledig stapel | Implementeert tegelijkertijd back-end- en front-end code samen met de configuraties HTTPD/Dispatcher | Wordt gebruikt wanneer front-end code gelijktijdig met AEM-servercode moet worden geïmplementeerd. Gebruikt wanneer de pijpleidingen aan de voorzijde of de configuratieleidingen aan de voorzijde nog niet zijn goedgekeurd. |
| Productie of niet-productie | Implementatie | Voorkant | Implementeert front-end code-build die een of meer client-side UI-toepassingen bevat | Steunt veelvoudige, gezamenlijke front-end pijpleidingen <br> veel sneller dan volledig-stapel plaatsingen. |
| Productie of niet-productie | Implementatie | Webconfiguratie | HTML/Dispatcher-configuraties implementeren | Binnen enkele minuten implementeren |
| Productie of niet-productie | Implementatie | Config | Stelt [ configuratie voor een aantal eigenschappen ](/help/operations/config-pipeline.md) met betrekking tot CDN op, logboek het door:sturen, en zuivert onderhoudstaken | Binnen enkele minuten implementeren |
| Niet-productie | Codekwaliteit | Volledige stapel | Hiermee wordt de codekwaliteit zonder implementatie gescand op een full-stack code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Voorkant | Hiermee wordt de codekwaliteit zonder implementatie gescand op de front-end code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Webconfiguratie | Voert scans van de codekwaliteit op configuraties van Dispatcher zonder plaatsing in werking | Ondersteunt meerdere pijpleidingen |

In het volgende diagram worden Cloud Manager-pijpleidingconfiguraties geïllustreerd met traditionele, single front-end opslagsystemen of onafhankelijke front-end opslagsystemen.

![ de pijpleidingsconfiguraties van Cloud Manager ](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Pijpleidingen met volledige stapel {#full-stack-pipeline}

Met behulp van full-stack pijpleidingen kunt u back-end code, front-end code en weblaagconfiguraties tegelijk implementeren in de AEM-runtime.

* Back-endcode - Onveranderbare inhoud zoals Java-code, OSGi-configuraties, opnieuw aanwijzen en muteerbare inhoud
* Front-end Code - Application UI-bronnen zoals JavaScript, CSS, lettertypen
* Configuratie van de Rij van het Web - configuraties HTTPD/Dispatcher

De pijpleiding van de volledig-stapel vertegenwoordigt een &quot;uber&quot;pijpleiding. Het behandelt alles gelijktijdig, terwijl ook het toestaan van gebruikers om hun front-end code of configuraties van Dispatcher afzonderlijk op te stellen. Deze plaatsing is door de front-end pijpleiding en de Web-rij config pijpleidingen, respectievelijk.

De volledig-stapel pijpleidingen verpakken front-end code (JavaScript/CSS) als [ de cliëntbibliotheken van AEM ](/help/implementing/developing/introduction/clientlibs.md).

De volledig-stapel pijpleidingen kunnen configuraties van de Webrij opstellen als de a [ config pijpleiding van de Webrij ](#web-tier-config-pipelines) niet wordt gevormd.

De volgende beperkingen zijn van toepassing.

* Een gebruiker moet met de **rol van de Manager van de Plaatsing worden geregistreerd 0} om pijpleidingen te vormen of in werking te stellen.**
* Op elk ogenblik, kan er slechts één volledig-stapelpijpleiding per milieu zijn.

Bovendien ben zich bewust van hoe de volledig-stapelpijpleiding zich gedraagt als u verkiest om de configuratiepijplijn van de a [ Webrij ](#web-tier-config-pipelines) te introduceren.

* De volledig-stapelpijpleiding voor een milieu negeert de configuratie van Dispatcher als de overeenkomstige Web rij config pijpleiding bestaat.
* Als de overeenkomstige web rij config pijpleiding voor het milieu niet bestaat, kan de gebruiker de full-stack pijpleiding vormen om de configuratie van Dispatcher te omvatten of te negeren.

De volledig-stapel pijpleidingen kunnen de pijpleidingen of plaatsing van de codekwaliteit zijn.

### Alle-stapelpijpleidingen configureren {#configure-full-stack}

Zie [ een productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code) toevoegen.
Zie [ een niet productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code) toevoegen.

## Config-pijpleidingen {#config-deployment-pipeline}

Gebruikend een config pijpleiding, kunt u montages voor logboek opstellen door:sturen, zuivert-verwante onderhoudstaken, en diverse configuraties CDN, met inbegrip van de regels van de verkeersfilter (zoals de Firewall van de Toepassing van het Web van WAF). Daarnaast kunt u verzoek- en responstransformaties, oorspronkelijke kiezers, omleidingen aan de clientzijde, foutpagina&#39;s, door de klant beheerde CDN-sleutels, de API-sleutels en de basisverificatie beheren.

Zie [ het Gebruik config pijpleidingen van het Gebruik ](/help/operations/config-pipeline.md) voor een uitvoerige lijst van gesteunde eigenschappen en te leren hoe te om de configuraties in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.

>[!NOTE]
>
>Edge Delivery Configuration Pipelines hebben geen aparte ontwikkelings-, staging- en productieomgevingen. In AEM as a Cloud Service worden wijzigingen doorgevoerd in ontwikkelings-, fase- en productieniveaus. Een Edge Delivery Configuration Pipeline past daarentegen zijn configuratie rechtstreeks toe op alle Edge Delivery Sites-domeinen die in Cloud Manager zijn geregistreerd. Meer leren, zie [ een Pijpleiding van Edge Delivery ](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md) toevoegen.


### Configuratiepijplijnen configureren {#configure-config-deployment}

Zie [ een productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment) toevoegen.
Zie [ een niet productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment) toevoegen.

## Pijpleidingen aan de voorzijde {#front-end}

Voorste code is elke code die als statische bestanden wordt gebruikt. Het is gescheiden van code UI die door AEM wordt gediend en kan plaatsthema&#39;s, klant-bepaalde SPAs, SPAs, en andere oplossingen omvatten.

De front-end pijpleidingen helpen uw teams uw ontwerp en ontwikkelingsproces stroomlijnen door versnelde plaatsing van front-end code, asynchroon van achterste-eindontwikkeling toe te laten. Deze speciale pijpleiding stelt JavaScript en CSS aan de distributielaag van AEM als thema op, resulterend in een nieuwe themaversie, die van pagina&#39;s door AEM kan worden van verwijzingen voorzien.

>[!NOTE]
>
>Een gebruiker met de **rol van de Manager van de Plaatsing 0} kan veelvoudige front-end pijpleidingen tot stand brengen en in werking stellen gelijktijdig.**
>
>Er is echter een maximum van 300 pijpleidingen per programma (voor alle soorten).

Voorste pijpleidingen kunnen pijpleidingen van codekwaliteit zijn of uitzetpijpleidingen.

### Voordat u front-end pijpleidingen configureert {#before-start}

Alvorens u front-end pijpleidingen vormt, herzie de [ Reis van de Aanmaak van de Plaats van AEM Snelle ](/help/journey-sites/quick-site/overview.md) voor een gids van begin tot eind door het makkelijk te gebruiken hulpmiddel van de Aanmaak van de Plaats van AEM Snelle. Deze reis helpt u uw front-end ontwikkeling te stroomlijnen en laat u uw plaats snel aanpassen zonder achterste-end AEM kennis.

### Vorm een front-end pijpleiding {#configure-front-end}

Zie [ een productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline) toevoegen.
Zie [ een niet productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline) toevoegen.

### Sites ontwikkelen met de front-end pijplijn {#developing-with-front-end-pipeline}

Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.

Zie [ Ontwikkelen Plaatsen met de front-end pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) voor hoe dit proces samen met sommige overwegingen werkt om zich bewust te zijn van om het volledige potentieel uit dit proces te krijgen.

## Webconfiguratieleidingen {#web-tier-config-pipelines}

De configuratiepijpleidingen van het Web staan exclusieve plaatsing van configuratie HTTPD/Dispatcher aan runtime van AEM toe, die het van andere codeveranderingen loskoppelt. Het is een gestroomlijnde pijpleiding die gebruikers verstrekt die slechts de configuratieveranderingen van Dispatcher willen opstellen, een versnelde manier om dit in slechts een paar minuten te doen.

>[!TIP]
>
>De lijst van het Web config pijpleidingen laten u uw Webconfig in de zelfde of een verschillende bronplaats opslaan zoals de volledige stapelpijpleiding, afhankelijk van wat het beste uw projectstructuur aanpast.

De volgende beperkingen zijn van toepassing.

* Gebruik AEM-versie `2021.12.6151.20211217T120950Z` of hoger als u configuratieleidingen op internet wilt gebruiken.
* [ Opt binnen aan de flexibele wijze van de hulpmiddelen van Dispatcher ](/help/implementing/dispatcher/disp-overview.md#validation-debug) om web-rij config pijpleidingen te gebruiken.
* Een gebruiker moet met de **rol van de Manager van de Plaatsing worden geregistreerd 0} om pijpleidingen te vormen of in werking te stellen.**
* Op elk ogenblik, kan er slechts één Web rij config pijpleiding per milieu zijn.
* De gebruiker kan geen Web rij config pijpleiding vormen wanneer zijn overeenkomstige volledig-stapelpijpleiding loopt.
* De structuur van de Webrij moet aan de flexibele wijzestructuur, zoals die in het document [ wordt bepaald Dispatcher in de Wolk ](/help/implementing/dispatcher/disp-overview.md#validation-debug) naleven.

Bovendien ben zich bewust van hoe de [ volledige stapelpijpleiding ](#full-stack-pipeline) zich gedraagt wanneer het introduceren van een pijpleiding van de Webrij.

* Als een web rij config pijpleiding niet opstelling voor een milieu is, kan de gebruiker verkiezen om de configuratie van Dispatcher te omvatten of te negeren terwijl het vormen van de full-stack pijpleiding. Deze selectie wordt gemaakt tijdens uitvoering en implementatie.
* Zodra een Web rij config pijpleiding voor een milieu wordt gevormd, zijn overeenkomstige volledig-stapelpijpleiding (als één bestaat) negeert de configuratie van Dispatcher tijdens uitvoering en plaatsing.
* Nadat een configuratiepijplijn van de Webrij wordt geschrapt, wordt zijn overeenkomstige full-stack pijpleiding teruggesteld om de configuraties van Dispatcher tijdens zijn uitvoering op te stellen.

Webniveau config-pijpleidingen kunnen van het type `Code quality` of `Deployment` zijn.

### Weblaagpijpleidingen configureren {#configure-web-tier}

Zie [ een productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment) toevoegen.
Zie [ een niet productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment) toevoegen.

## Video-overzicht van pijpleidingtypen {#video}

Bekijk de volgende video (2 minuten, 26 seconden) voor een snel overzicht van pijpleidingtypen.

>[!VIDEO](https://video.tv.adobe.com/v/342363)
