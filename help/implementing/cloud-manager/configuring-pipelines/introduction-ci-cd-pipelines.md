---
title: CI/CD-pijpleidingen
description: Leer meer over de CI/CD-pijpleidingen van Cloud Manager en hoe deze kunnen worden gebruikt om uw code efficiënt te implementeren.
index: true
exl-id: 40d6778f-65e0-4612-bbe3-ece02905709b
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 0%

---


# Cloud Manager CI/CD Pipelines {#intro-cicd}

Leer meer over de CI/CD-pijpleidingen van Cloud Manager en hoe deze kunnen worden gebruikt om uw code efficiënt te implementeren.

## Inleiding {#introduction}

Een CI/CD pijpleiding in de Manager van de Wolk is een mechanisme om code van een bronbewaarplaats te bouwen en het in een milieu op te stellen. Een pijpleiding kan door een gebeurtenis, zoals een trekkrachtverzoek van een broncodebewaarplaats (d.w.z. een codeverandering), of op een regelmatige planning worden teweeggebracht om een versiecadence aan te passen.

Om een pijpleiding te vormen, moet u:

* Bepaal de trekker die de pijpleiding zal beginnen.
* Definieer de parameters die de productieimplementatie bepalen.
* Configureer de testparameters voor prestaties.

Cloud Manager biedt twee soorten pijpleidingen:

* [Productiepijpleidingen](#prod-pipeline)
* [Niet-productiepijpleidingen](#non-prod-pipeline)

![Typen pijpleidingen](/help/implementing/cloud-manager/assets/configure-pipeline/ci-cd-config1.png)

## Video-overzicht {#video}

Voor een snel overzicht van pijpleidingstypes, bekijk deze korte video.

>[!VIDEO](https://video.tv.adobe.com/v/342363)

## Productiepijpleidingen {#prod-pipeline}

Een productiepijpleiding is een doelgerichte pijpleiding die een reeks georkestreerde stappen omvat om broncode voor productiegebruik op te stellen. De stappen omvatten eerste het bouwen, het verpakken, het testen, het bevestigen, en het opstellen in alle het opvoeren milieu&#39;s. Daarom kan een productiepijpleiding slechts worden toegevoegd zodra een reeks productie en het opvoeren milieu&#39;s wordt gecreeerd.

>[!TIP]
>
>Het document raadplegen [Een productiepijpleiding configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) voor meer informatie .

## Niet-productiepijpleiding {#non-prod-pipeline}

Een niet-productiepijpleiding dient hoofdzakelijk om codescannen in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

>[!TIP]
>
>Het document raadplegen [Een niet-productiepijplijn configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) voor meer informatie .

## Codebronnen {#code-sources}

Naast productie en niet-productie kunnen pijpleidingen worden gedifferentieerd naar het type code dat zij invoeren.

* **[Volledige stapelpijplijnen](#full-stack-pipeline)** - Tegelijkertijd back-end- en front-end codebuilds implementeren die een of meer AEM servertoepassingen bevatten, samen met configuraties van HTTPD/Dispatcher
* **[Pijpleidingen aan de voorzijde](#front-end)** - Maak front-end codebouwwerken die één of meerdere cliënt-kant toepassingen UI bevatten
* **[Webservicepijpleidingen](#web-tier-config-pipelines)** - Implementeert HTTPD/Dispatcher-configuraties

Deze worden later in dit document uitgebreid beschreven.

### CI-CD-pijpleidingen begrijpen in Cloud Manager {#understand-pipelines}

In de volgende tabel vindt u een overzicht van alle pijpleidingen die beschikbaar zijn in Cloud Manager en het gebruik ervan.

| Type pijpleiding | Implementatie- of codekwaliteit | Broncode | Doel | Notities |
|--- |--- |--- |---|---|
| Productie of niet-productie | Implementatie | Volledige stapel | Plaatst gelijktijdig achter-eind en front-end code bouwt samen met configuraties HTTPD/Dispatcher | Wanneer front-end code met AEM servercode moet worden opgesteld.<br>Wanneer de pijpleidingen aan de voorzijde of de configuratieleidingen aan de Webzijde nog niet zijn goedgekeurd. |
| Productie of niet-productie | Implementatie | Voorkant | Implementeert front-end code-build die een of meer client-side UI-toepassingen bevat | Ondersteunt meerdere, gelijktijdige front-end pijpleidingen<br>Veel sneller dan implementaties op volledige stapel |
| Productie of niet-productie | Implementatie | Config. web | Implementeert HTTPD/Dispatcher-configuraties | Binnen enkele minuten implementeren |
| Niet-productie | Codekwaliteit | Volledige stapel | Hiermee wordt de codekwaliteit zonder implementatie gescand op een full-stack code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Voorkant | Hiermee wordt de codekwaliteit zonder implementatie gescand op de front-end code | Ondersteunt meerdere pijpleidingen |
| Niet-productie | Codekwaliteit | Config. web | Hiermee wordt de codekwaliteit zonder implementatie gescand op de configuraties van de verzender | Ondersteunt meerdere pijpleidingen |

Het volgende diagram illustreert de pijplijnconfiguraties van Cloud Manager met traditionele, single front-end repository, of onafhankelijke front-end dataopslaginstellingen.

![Poortconfiguraties van Cloud Manager](/help/implementing/cloud-manager/assets/configure-pipeline/cm-setup.png)

## Full-Stack Pipelines {#full-stack-pipeline}

De volledig-stapel pijpleidingen voeren achterste-eindcode, front-end code, en de configuraties van de Webrij op om runtime allen tezelfdertijd te AEM.

* Back-endcode - Onveranderbare inhoud zoals Java-code, OSGi-configuraties, opnieuw aanwijzen en muteerbare inhoud
* Voorwaardelijke code - UI-bronnen voor toepassingen zoals JavaScript, CSS, lettertypen
* Configuratie van de Rij van het Web - configuraties HTTPD/Dispatcher

De full-stack pijpleiding vertegenwoordigt een &#39;uber&#39; pijpleiding, die alles in één keer doet, terwijl het geven van gebruikers de opties om hun front-end code of configuraties van de Verzender via de front-end pijpleiding en de Web-rij config pijpleidingen exclusief op te stellen.

Poortvolle pijpleidingen verpakken front-end code (JavaScript/CSS) als [AEM clientbibliotheken.](/help/implementing/developing/introduction/clientlibs.md)

Bij volledige-stapelpijpleidingen kunnen configuraties in een weblaag worden geïmplementeerd als een [configuratiepijplijn voor webniveau](#web-tier-config-pipelines) is niet geconfigureerd.

De volgende beperkingen zijn van toepassing.

* Een gebruiker moet met het programma worden geregistreerd **Implementatiebeheer** rol om pijpleidingen te vormen of in werking te stellen.
* Op elk ogenblik, kan er slechts één volledig-stapelpijpleiding per milieu zijn.

Bovendien moet u zich bewust zijn van het gedrag van de pijplijn in de volledige stapel als u ervoor kiest om een [configuratiepijplijn voor webniveau.](#web-tier-config-pipelines)

* De volledig-stapelpijpleiding voor een milieu zal de configuratie van de Verzender negeren als de overeenkomstige Web rij config pijpleiding bestaat.
* Als de overeenkomstige web rij config pijpleiding voor het milieu niet bestaat, kan de gebruiker de volledig-stapelpijpleiding vormen omvatten of negeren de configuratie van de Ontvanger.

De volledig-stapelpijpleidingen kunnen de pijpleidingen of plaatsing van de codekwaliteit zijn.

## Pijpleidingen aan de voorzijde {#front-end}

Voorste-eindcode is om het even welke code die als statische dossiers wordt gediend. Het is verschillend van code UI die door AEM wordt gediend en kan plaatsthema&#39;s, klant-bepaalde SPA, SPA, en andere oplossingen omvatten.

De front-end pijpleidingen helpen uw teams uw ontwerp en ontwikkelingsproces stroomlijnen door versnelde plaatsing van front-end code asynchroon van achterste-eindontwikkeling toe te laten. Deze speciale pijpleiding stelt JavaScript en CSS aan de AEM distributielaag als thema op, resulterend in een nieuwe themaversie die van pagina&#39;s door AEM kan worden van verwijzingen voorzien.

>[!IMPORTANT]
>
>U moet AEM versie hebben `2021.10.5933.20211012T154732Z ` of hoger met AEM Sites ingeschakeld voor het gebruik van voorste-eindpijpleidingen.

>[!NOTE]
>
>Een gebruiker met de **Implementatiebeheer** De rol kan veelvoudige front-end pijpleidingen tot stand brengen en in werking stellen gelijktijdig.
>
>Er is echter een maximum van 300 pijpleidingen per programma (voor alle soorten).

Voorste pijpleidingen kunnen pijpleidingen van codekwaliteit zijn of uitzetpijpleidingen.

### Alvorens u Voorste-Eind Pijpleidingen vormt {#before-start}

Voordat u front-end pijpleidingen configureert, moet u de [Reis voor snel maken van site AEM](/help/journey-sites/quick-site/overview.md) voor een end-to-end gids door het makkelijk te gebruiken AEM Snelle hulpmiddel van de Plaats. Deze reis zal u helpen uw front-end ontwikkeling stroomlijnen en u toestaan om uw plaats snel aan te passen zonder achterste-AEM kennis.

### Vorm een Voorste-Eind Pijpleiding {#configure-front-end}

Raadpleeg de volgende documenten voor meer informatie over het configureren van front-end pijpleidingen.

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)

### Sites ontwikkelen met behulp van de voorste pijplijn {#developing-with-front-end-pipeline}

Met frontend pijpleidingen wordt meer onafhankelijkheid gegeven aan front-end ontwikkelaars en kan het ontwikkelingsproces worden versneld.

Raadpleeg het document [Sites ontwikkelen met behulp van de voorste pijplijn](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) hoe dit proces samen met enkele overwegingen werkt , moet u zich ervan bewust zijn dat dit proces alle mogelijkheden biedt .

### Het vormen volledig-Stapel Pijpleidingen {#configure-full-stack}

Raadpleeg de volgende documenten voor meer informatie over het configureren van pijpleidingen in volledige stapel.

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)


## Webservicepijpleidingen {#web-tier-config-pipelines}

De configuratiepijpleidingen van de rij van het Web laten exclusieve plaatsing van configuratie HTTPD/Dispatcher aan AEM runtime toe door het van andere codeveranderingen te ontkoppelen. Het is een gestroomlijnde pijpleiding die gebruikers verstrekt die wensen om de configuratieveranderingen van de verzender slechts op te stellen, een versnelde manier om dit in slechts een paar minuten te doen.

>[!TIP]
>
>Met de configuratiepijpleidingen van de Webrij, kunt u tussen het opslaan van uw Webconfig in de zelfde bronplaats kiezen zoals voor de volledige stapelpijpleiding of in een verschillende plaats, afhankelijk van welke structuur beter uw project aanpast.

De volgende beperkingen zijn van toepassing.

* U moet AEM versie hebben `2021.12.6151.20211217T120950Z` of nieuwer om web-tier config pijpleidingen te gebruiken.
* U moet [deelnemen aan de flexibele modus van de verzendingsprogramma&#39;s](/help/implementing/dispatcher/disp-overview.md#validation-debug) om web-tier config pijpleidingen te gebruiken.
* Een gebruiker moet met het programma worden geregistreerd **Implementatiebeheer** rol om pijpleidingen te vormen of in werking te stellen.
* Op elk ogenblik, kan er slechts één pijpleiding van de Webrij config per milieu zijn.
* De gebruiker kan geen configuratiepijplijn van de Webrij vormen wanneer zijn overeenkomstige volledig-stapelpijpleiding loopt.
* De structuur van de weblaag moet voldoen aan de structuur van de flexibele modus, zoals gedefinieerd in het document [Dispatcher in de cloud.](/help/implementing/dispatcher/disp-overview.md#validation-debug)

Houd er bovendien rekening mee dat de [volledige stapelpijplijn](#full-stack-pipeline) gedraagt zich wanneer het invoeren van een Web-rij pijpleiding.

* Als een Web rij config pijpleiding niet voor een milieu is gevormd, kan de gebruiker een selectie maken terwijl het vormen van zijn overeenkomstige volledig-stapelpijpleiding om de configuratie van de Verzender tijdens uitvoering en plaatsing te omvatten of te negeren.
* Zodra een Web rij config pijpleiding voor een milieu is gevormd, zal zijn overeenkomstige volledig-stapelpijpleiding (als één bestaat) de dispatcherconfiguratie tijdens uitvoering en plaatsing negeren.
* Nadat een configuratiepijplijn van de Webrij wordt geschrapt, wordt zijn overeenkomstige full-stack pijpleiding teruggesteld om de configuraties van de Ontvanger tijdens zijn uitvoering op te stellen.

De configuratiepijpleidingen van het Web kunnen van het type code kwaliteit of plaatsing zijn.

### Het vormen de Pijpleidingen van Config van de Rij Web {#configure-web-tier-config-pipelines}

Raadpleeg de volgende documenten voor meer informatie over het configureren van configuratieleidingen voor websites.

* [Een productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md#adding-production-pipeline)
* [Een niet-productiepijpleiding toevoegen](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#adding-non-production-pipeline)
