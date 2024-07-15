---
title: CI/CD-pijpleidingen
description: Leer meer over Cloud Manager CI/CD pijpleidingen en hoe zij kunnen worden gebruikt om uw code efficiënt op te stellen.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1418'
ht-degree: 0%

---


# Cloud Manager CI/CD Pipelines {#intro-cicd}

Leer meer over Cloud Manager CI/CD pijpleidingen en hoe zij kunnen worden gebruikt om uw code efficiënt op te stellen.

## Inleiding {#introduction}

Een CI/CD pijpleiding in Cloud Manager is een mechanisme om code van een bronbewaarplaats te bouwen en het in een milieu op te stellen. Een pijpleiding kan door een gebeurtenis, zoals een trekkrachtverzoek van een broncodebewaarplaats (namelijk een codeverandering), of op een regelmatige planning worden teweeggebracht om een versiecadence aan te passen.

Om een pijpleiding te vormen, moet u:

* Bepaal de trekker die de pijpleiding zal beginnen.
* Definieer de parameters die de productieimplementatie bepalen.
* Configureer de testparameters voor prestaties.

Cloud Manager biedt twee soorten pijpleidingen:

* [Productiepijpleidingen](#prod-pipeline)
* [Niet-productiepijpleidingen](#non-prod-pipeline)

![ Types van pijpleidingen ](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Productiepijpleidingen {#prod-pipeline}

Een productiepijpleiding is een doelgerichte pijpleiding die een reeks georkestreerde stappen omvat om broncode voor productiegebruik op te stellen. De stappen omvatten eerste het bouwen, het verpakken, het testen, het bevestigen, en het opstellen in alle het opvoeren milieu&#39;s. Daarom kan een productiepijpleiding slechts worden toegevoegd zodra een reeks productie en het opvoeren milieu&#39;s wordt gecreeerd.

>[!TIP]
>
>Zie [ Vormend een Pijpleiding van de Productie ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) voor meer details.

## Niet-productiepijpleiding {#non-prod-pipeline}

Een niet-productiepijpleiding dient hoofdzakelijk om codescannen in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

>[!TIP]
>
>Zie [ Vormend een niet-Productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) voor meer details.

## Codebronnen {#code-sources}

Naast productie en niet-productie kunnen pijpleidingen worden gedifferentieerd naar het type code dat zij invoeren.

* **[Volledige Pijpleidingen van de Stapel](#full-stack-pipeline)** - stelt gelijktijdig achterste en front-end codebouwstijlen op die één of meerdere AEM servertoepassingen samen met configuraties HTTPD/Dispatcher bevatten
* **[Pijpleidingen Config](#config-deployment-pipeline)** - vorm en stel de regels van de verkeersfilter, met inbegrip van de regels van WAF, binnen notulen op
* **[voorste-Eind Pijpleidingen](#front-end)** - stel front-end code op bouwt die één of meerdere cliënt-zij toepassingen UI bevatten
* **[de Lijnen van het Web Config Pipelines](#web-tier-config-pipelines)** - stelt configuraties HTTPD/Dispatcher op

Deze worden later in dit document uitgebreid beschreven.

### KCI-CD-pijpleidingen in Cloud Manager {#understand-pipelines}

De volgende tabel geeft een overzicht van de in Cloud Manager beschikbare pijpleidingen en het gebruik ervan.

| Type pijpleiding | Implementatie- of codekwaliteit | Source-code | Doel | Notities |
|--- |--- |--- |---|---|
| Productie of niet-productie | Implementatie | Volledig stapel | Implementeert tegelijkertijd back-end- en front-end code samen met de configuraties HTTPD/Dispatcher | Wanneer front-end code met AEM servercode moet worden opgesteld.<br> wanneer front-end pijpleidingen of Web-rij config pijpleidingen nog niet zijn goedgekeurd. |
| Productie of niet-productie | Implementatie | Voorkant | Implementeert front-end code-build die een of meer client-side UI-toepassingen bevat | Steunt veelvoudige, gezamenlijke front-end pijpleidingen <br> veel sneller dan volledig-stapelplaatsingen |
| Productie of niet-productie | Implementatie | Config. web | HTML/Dispatcher-configuraties implementeren | Binnen enkele minuten implementeren |
| Productie of niet-productie | Implementatie | Config | Plaatst verkeer het filtreren regels | Binnen enkele minuten implementeren |
| Niet-productie | Codekwaliteit | Volledig stapel | Hiermee wordt de codekwaliteit zonder implementatie gescand op een full-stack code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Voorkant | Hiermee wordt de codekwaliteit zonder implementatie gescand op de front-end code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Config. web | Hiermee wordt de codekwaliteit zonder implementatie gescand op de configuraties van de verzender | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Config | Plaatst verkeer het filtreren regels |  |

In het volgende diagram worden Cloud Manager-pijpleidingconfiguraties geïllustreerd met traditionele, single front-end opslagsystemen of onafhankelijke front-end opslagsystemen.

![ de pijpleidingsconfiguraties van Cloud Manager ](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Full-Stack Pipelines {#full-stack-pipeline}

De volledig-stapel pijpleidingen voeren achterste-eindcode, front-end code, en de configuraties van de Webrij op om runtime allen tezelfdertijd te AEM.

* Back-endcode - Onveranderbare inhoud zoals Java-code, OSGi-configuraties, opnieuw aanwijzen en muteerbare inhoud
* Front-end Code - Application UI-bronnen zoals JavaScript, CSS, lettertypen
* Configuratie van de Rij van het Web - configuraties HTTPD/Dispatcher

De full-stack pijpleiding vertegenwoordigt een &#39;uber&#39; pijpleiding, die alles in één keer doet, terwijl het geven van gebruikers de opties om hun front-end code of configuraties van Dispatcher via de front-end pijpleiding en de Web-rij config pijpleidingen exclusief op te stellen.

De volledig-stapel pijpleidingen verpakken front-end code (JavaScript/CSS) als [ AEM cliëntbibliotheken ](/help/implementing/developing/introduction/clientlibs.md).

De volledig-stapel pijpleidingen kunnen configuraties van de Webrij opstellen als de a [ config pijpleiding van de Webrij ](#web-tier-config-pipelines) niet wordt gevormd.

De volgende beperkingen zijn van toepassing.

* Een gebruiker moet met de **rol van de Manager van de Plaatsing worden geregistreerd 0} om pijpleidingen te vormen of in werking te stellen.**
* Op elk ogenblik, kan er slechts één volledig-stapelpijpleiding per milieu zijn.

Bovendien ben zich bewust van hoe de volledig-stapelpijpleiding zich gedraagt als u verkiest om a [ Web rij config pijpleiding te introduceren.](#web-tier-config-pipelines)

* De volledig-stapelpijpleiding voor een milieu zal de configuratie van Dispatcher negeren als de overeenkomstige Web rij config pijpleiding bestaat.
* Als de overeenkomstige web rij config pijpleiding voor het milieu niet bestaat, kan de gebruiker de volledig-stapelpijpleiding vormen omvat of negeert de configuratie van Dispatcher.

De volledig-stapel pijpleidingen kunnen de pijpleidingen of plaatsing van de codekwaliteit zijn.

### Het vormen volledig-Stapel Pijpleidingen {#configure-full-stack}

Leren hoe te om volledig-stapelpijpleidingen te vormen, zie de volgende documenten:

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#full-stack-code)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code)

## Config Pipelines {#config-deployment-pipeline}

Met een config pijpleiding kunt u de regels van de verkeersfilter, met inbegrip van de regels van WAF, binnen notulen vormen en opstellen.

Zie [ Regels van de Filter van het Verkeer met inbegrip van de Regels van WAF ](/help/security/traffic-filter-rules-including-waf.md) leren hoe te om de configuraties in uw bewaarplaats te beheren zodat worden zij behoorlijk opgesteld.

### Config Pipelines configureren {#configure-config-deployment}

Leren hoe te om config pijpleidingen te vormen, zie de volgende documenten:

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)

## Pijpleidingen aan de voorzijde {#front-end}

Voorste code is elke code die als statische bestanden wordt gebruikt. Het is verschillend van code UI die door AEM wordt gediend en kan plaatsthema&#39;s, klant-bepaalde SPA, SPA, en andere oplossingen omvatten.

De front-end pijpleidingen helpen uw teams uw ontwerp en ontwikkelingsproces stroomlijnen door versnelde plaatsing van front-end code asynchroon van achterste-eindontwikkeling toe te laten. Deze speciale pijpleiding stelt JavaScript en CSS aan de AEM distributielaag als thema op, resulterend in een nieuwe themaversie die van pagina&#39;s door AEM kan worden van verwijzingen voorzien.

>[!NOTE]
>
>Een gebruiker met de **rol van de Manager van de Plaatsing 0} kan veelvoudige front-end pijpleidingen tot stand brengen en in werking stellen gelijktijdig.**
>
>Er is echter een maximum van 300 pijpleidingen per programma (voor alle soorten).

Voorste pijpleidingen kunnen pijpleidingen van codekwaliteit zijn of uitzetpijpleidingen.

### Alvorens u Voorste-Eind Pijpleidingen vormt {#before-start}

Alvorens u front-end pijpleidingen vormt, herzie de [ AEM Snelle Reis van de Aanmaak van de Plaats ](/help/journey-sites/quick-site/overview.md) voor een gids van begin tot eind door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Aanmaak van de Plaats. Deze reis zal u helpen uw front-end ontwikkeling stroomlijnen en u toestaan om uw plaats snel aan te passen zonder achterste-AEM kennis.

### Vorm een Voorste-Eind Pijpleiding {#configure-front-end}

Leren hoe te om front-end pijpleidingen te vormen, zie het volgende:

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Sites ontwikkelen met behulp van de voorste pijplijn {#developing-with-front-end-pipeline}

Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.

Zie [ het Ontwikkelen Plaatsen met de Voorste-Eind Pijpleiding ](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) voor hoe dit proces samen met sommige overwegingen werkt om zich bewust te zijn van om het volledige potentieel uit dit proces te krijgen.

## Webservicepijpleidingen {#web-tier-config-pipelines}

De configuratiepijpleidingen van het Web laten exclusieve plaatsing van configuratie HTTPD/Dispatcher aan AEM runtime toe door het van andere codeveranderingen te ontkoppelen. Het is een gestroomlijnde pijpleiding die gebruikers verstrekt die de configuratieveranderingen van de verzender slechts willen opstellen, een versnelde manier om dit in slechts een paar minuten te doen.

>[!TIP]
>
>Met de configuratiepijpleidingen van de Webrij, kunt u tussen het opslaan van uw Webconfig in de zelfde bronplaats kiezen zoals voor de volledige stapelpijpleiding of in een verschillende plaats, afhankelijk van welke structuur beter uw project aanpast.

De volgende beperkingen zijn van toepassing.

* U moet AEM versie `2021.12.6151.20211217T120950Z` of nieuwer zijn om config-pijpleidingen op het web te gebruiken.
* U moet [ kiezen binnen aan de flexibele wijze van de dispatcherhulpmiddelen ](/help/implementing/dispatcher/disp-overview.md#validation-debug) om web-rij config pijpleidingen te gebruiken.
* Een gebruiker moet met de **rol van de Manager van de Plaatsing worden geregistreerd 0} om pijpleidingen te vormen of in werking te stellen.**
* Op elk ogenblik, kan er slechts één Web rij config pijpleiding per milieu zijn.
* De gebruiker kan geen Web rij config pijpleiding vormen wanneer zijn overeenkomstige volledig-stapelpijpleiding loopt.
* De structuur van de Webrij moet aan de flexibele wijzestructuur, zoals die in het document [ wordt bepaald Dispatcher in de Wolk ](/help/implementing/dispatcher/disp-overview.md#validation-debug) naleven.

Bovendien ben zich bewust van hoe de [ volledige stapelpijpleiding ](#full-stack-pipeline) zich gedraagt wanneer het introduceren van een pijpleiding van de Webrij.

* Als een Web rij config pijpleiding niet voor een milieu is gevormd, kan de gebruiker een selectie maken terwijl het vormen van zijn overeenkomstige volledig-stapelpijpleiding om de configuratie van Dispatcher tijdens uitvoering en plaatsing te omvatten of te negeren.
* Zodra een Web rij config pijpleiding voor een milieu is gevormd, zal zijn overeenkomstige volledig-stapelpijpleiding (als één bestaat) de dispatcherconfiguratie tijdens uitvoering en plaatsing negeren.
* Nadat een configuratiepijplijn van de Webrij wordt geschrapt, wordt zijn overeenkomstige full-stack pijpleiding teruggesteld om de configuraties van Dispatcher tijdens zijn uitvoering op te stellen.

De configuratiepijpleidingen van het Web kunnen van het type code kwaliteit of plaatsing zijn.

### Het vormen Pijpleidingen van de Rij van het Web {#configure-web-tier}

Raadpleeg de volgende documenten voor informatie over het configureren van pijpleidingen voor het web:

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#targeted-deployment)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#targeted-deployment)

## Video Overzicht van de Types van Pijpleiding {#video}

Voor een snel overzicht van pijpleidingstypes, bekijk deze korte video.

>[!VIDEO](https://video.tv.adobe.com/v/342363)
