---
title: CI-CD-pijpleidingen
description: CI-CD-pijpleidingen
index: false
source-git-commit: 76cff84003576cf23eb1d23674ce6eaf082bbbb1
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---


# Cloud Manager CI-CD Pipelines {#intro-cicd}

## Inleiding {#introduction}

Een CI/CD pijpleiding in de Manager van de Wolk kan door één of andere soort gebeurtenis, zoals een trekkingsverzoek van een broncodebewaarplaats worden teweeggebracht, namelijk een codeverandering, of één of ander soort regelmatig programma om een versiecadence aan te passen.

>[!NOTE]
>Om uw pijpleiding te vormen, moet u:
>* bepaal de trekker die de pijpleiding zal beginnen
>* de parameters definiëren die de productie-implementatie beheersen
>* configureren van de testparameters voor de prestaties


In Cloud Manager zijn er twee soorten pijplijnen:

* [Productiepijpleiding](#prod-pipeline)
* [Niet-productiepijpleiding](#non-prod-pipeline)

## Productiepijpleiding {#prod-pipeline}

Een productiepijpleiding is een doelpijpleiding die een reeks georkestreerde stappen omvat om broncode helemaal in productie te nemen. De stappen omvatten eerst het bouwen, verpakken, testen, valideren en implementeren in alle Stage-omgeving. Een productiepijpleiding kan natuurlijk alleen worden toegevoegd als een productie- en werkgebiedomgeving is ingesteld.

Verwijs naar het Vormen van de Pijpleiding van de Productie voor meer details.


## Niet-productiepijpleiding {#non-prod-pipeline}

Een pijpleiding van de niet-Productie richt code-kwaliteit scans in werking te stellen of broncode in een ontwikkelomgeving op te stellen.

Raadpleeg de pijplijnen Niet-productie en Alleen kwaliteit van code voor meer informatie.

## CI-CD-pijpleidingen begrijpen in Cloud Manager {#understand-pipelines}

In de volgende tabel worden de pijpleidingen in Cloud Manager gecategoriseerd, samen met het gebruik ervan.

| Type pijpleiding | Implementatie- of codekwaliteit | Broncode | Wanneer gebruiken | Wanneer of waarom moet ik gebruiken? |
|--- |--- |--- |---|---|---|
| Productie of niet-productie | Implementatie | Voorkant | Voorste eindcode implementeren. Voorste eindcode is elke code die als statisch bestand wordt gebruikt. Het is verschillend van code UI die door AEM wordt gediend. Het omvat Sites Thema&#39;s, Door de klant gedefinieerde SPA, Firefly SPA en andere oplossingen. Moet AEM versie zijn. | Snelle implementatietijden.<br> De veelvoudige front-end pijpleidingen kunnen worden gevormd en gelijktijdig per milieu lopen. |
|  | Implementatie | Volledige stapel | De back-end-, front-end- en HTTPD/dispatcherconfiguratie tegelijk implementeren. Opmerking: Er gelden enkele beperkingen. | Wanneer de pijpleidingen van Config van het Voorste of van het Web nog niet zijn goedgekeurd. |
|  | Implementatie | Config. web | HTTPD/verzender-configuratie uitsluitend in een paar minuten implementeren.  Deze gestroomlijnde pijpleiding verstrekt gebruikers die wensen om de configuratieveranderingen van de verzender slechts op te stellen, een versnelde manier om dit te doen. Opmerking: Moet AEM versie zijn [versie] | Snelle implementatietijden. |



## Cloud Manager frontend Pipelines {#front-end}

De pijpleidingen van het Eind van de voorzijde helpen uw teams uw ontwerp en ontwikkelingsproces stroomlijnen, door versnelde front-end pijpleidingen voor het opstellen van front-end code toe te laten. Deze onderscheiden pijpleiding stelt JavaScript en CSS aan de AEM distributielaag als thema op, resulterend in een nieuwe themaversie die van pagina&#39;s van AEM runtime kan worden van verwijzingen voorzien. Voorste eindcode is elke code die als statisch bestand wordt gebruikt. Het is verschillend van code UI die door AEM wordt gediend. Het omvat Sites Thema&#39;s, Door de klant gedefinieerde SPA, Firefly SPA en andere oplossingen.

>[!NOTE]
>Een gebruiker die als rol van de Manager van de Plaatsing wordt aangemeld kan veelvoudige vooreind pijpleidingen tot stand brengen en in werking stellen gelijktijdig. Er is echter een maximum van 300 pijpleidingen per programma (voor alle soorten).

Er zijn twee soorten Voorste Pijpleidingen:

* Codekwaliteit aan voorzijde
* Front End-implementatie

## Volledige stapelpijplijnen {#full-stack-pipeline}

De volledige pijpleiding van de Stapel geeft de gebruiker de optie om achterste-eind, front-end en configuratie HTTPD/dispatcher tezelfdertijd op te stellen.  Er wordt code en inhoud naar de AEM-runtime geïmplementeerd, inclusief front-end code (JavaScript/CSS) die is verpakt als AEM clientbibliotheken. Het kan configuratie van de Webrij opstellen als een pijpleiding van de Rij van het Web niet wordt gevormd. Dit vertegenwoordigt de &quot;uber&quot;pijpleiding, terwijl het geven van gebruikers de opties om hun Voorste code van het Eind of de berichtconfiguratie via de Voorste pijpleiding van het Eind en de pijpleiding van Config van de Rij van het Web uitsluitend op te stellen.


De volgende beperkingen zijn van toepassing:

1. Een gebruiker moet als Manager van de Plaatsing worden het programma geopend om pijpleidingen te vormen of in werking te stellen.

1. Op elk ogenblik, kan er slechts één Volledige pijpleiding van de Stapel per milieu zijn.

1. De gebruiker kan de Volledige pijpleiding van de Stapel voor een milieu vormen om al dan niet de dispatcherconfiguratie te negeren, als de overeenkomstige pijpleiding Config van de Rij van het Web voor het milieu niet bestaat.

1. De Volledige pijpleiding van de Stapel voor een milieu zal de dispatcherconfiguratie negeren als de overeenkomstige pijpleiding Config van de Rij van het Web voor het milieu bestaat.

Er zijn twee soorten Volledige Pijpleidingen van de Stapel:

* Pipet van volledige stapelcodekwaliteit
* Volledige distributiepijpleiding van de Stapel

