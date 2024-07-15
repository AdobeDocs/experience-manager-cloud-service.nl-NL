---
title: Go-Live
description: Leer hoe u de migratie uitvoert als de code en de inhoud klaar zijn voor de cloud
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1239'
ht-degree: 0%

---

# Go-Live {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Go-Live-voorbereiding"
>abstract="Om ervoor te zorgen dat AEM as a Cloud Service probleemloos en succesvol kan gaan werken, moet u plannen voor het bevriezen van code en inhoud, testversies, aanvulling van inhoud, prestatietests, beveiligingstests en meer."

In dit gedeelte van de reis leert u hoe u de migratie kunt plannen en uitvoeren zodra zowel de code als de inhoud gereed zijn om naar AEM as a Cloud Service te worden verplaatst. Bovendien leert u wat de beste praktijken en bekende beperkingen zijn wanneer u de migratie uitvoert.

## Het verhaal tot nu toe {#story-so-far}

In de vorige fasen van de reis:

* U leerde hoe te beginnen met de beweging aan AEM as a Cloud Service in [ worden Begonnen ](/help/journey-migration/getting-started.md) pagina.
* Vastgesteld als uw plaatsing klaar is om aan de wolk te worden bewogen door de [ fase van de Gereedheid ](/help/journey-migration/readiness.md) te lezen
* Vertrouwd zelf met de hulpmiddelen en het proces waardoor u uw code en inhoudswolk met de [ fase van de Implementatie ](/help/journey-migration/implementation.md) kunt maken.

## Doelstelling {#objective}

Dit document helpt u te begrijpen hoe u de migratie naar AEM as a Cloud Service kunt uitvoeren zodra u bekend bent met de vorige stappen van de reis. U leert hoe u de initiële migratie van uw productie kunt uitvoeren en de beste werkwijzen die u kunt volgen bij het migreren naar AEM as a Cloud Service.

## Oorspronkelijke productiemigratie {#initial-migration}

Alvorens u de productiemigratie kunt uitvoeren, volg de installatie en het bewijs van migratiestappen die in de [ worden geschetst de migratiestrategie van de Inhoud en chronologie ](/help/journey-migration/implementation.md##strategy-timeline) sectie van de [ fase van de Implementatie ](/help/journey-migration/implementation.md).

* De migratie vanuit productie starten op basis van de ervaring die u hebt opgedaan tijdens de AEM as a Cloud Service-migratie tijdens het uitvoeren van klonen:
   * Auteur
   * Publish-Publish

* Valideer de inhoud die in de AEM as a Cloud Service-auteur en -publicatielagen wordt opgenomen.
* Geef het ontwerpteam van de inhoud de opdracht om te voorkomen dat inhoud op zowel de bron als de bestemming wordt verplaatst totdat de opname is voltooid
* Nieuwe inhoud kan worden toegevoegd, bewerkt of verwijderd, maar u kunt het verplaatsen voorkomen. Dit geldt zowel voor de bron als voor de bestemming.
* Registreer de [ tijd die ](/help/journey-migration/implementation.md#gathering-data) voor volledige extractie en opname wordt genomen om een schatting voor toekomstige top-up migratiechronologie te hebben.
* Creeer a [ migratieplanner ](/help/journey-migration/implementation.md#migration-plan) voor zowel auteur als publiceert.

## Incrementele top-ups {#top-up}

Na de eerste migratie uit productie moet u incrementele verhogingen uitvoeren om ervoor te zorgen dat uw inhoud up-to-date wordt gebracht op de cloudinstantie. Daarom wordt u aangeraden de volgende aanbevolen procedures te volgen:

* Gegevens verzamelen over de hoeveelheid inhoud. Bijvoorbeeld: per week, twee weken of een maand.
* Zorg ervoor dat u de aanvullingen zodanig plant dat u meer dan 48 uur aan extractie en inname van inhoud voorkomt. Dit wordt aanbevolen, zodat de extra inhoud binnen een weekendtijdkader past.
* Plan het aantal vereiste topups en gebruik deze schattingen om rond de Go-Live-datum te plannen.

## Identificeer Code en de Inhoud stijgt Tijdlijnen voor de Migratie {#code-content-freeze}

Zoals eerder vermeld, moet u een periode voor het bevriezen van code en inhoud plannen. Gebruik de volgende vragen om u te helpen de periode van bevriezing te plannen:

* Hoe lang moet ik de creatie van content bevriezen?
* Voor hoe lang zou ik mijn leveringsteam moeten vragen om op te houden toevoegend nieuwe eigenschappen?

Als u de eerste vraag wilt beantwoorden, moet u rekening houden met de tijd die nodig is om proefversies uit te voeren in omgevingen waar geen productie plaatsvindt. Om de tweede vraag te beantwoorden, hebt u nauwe samenwerking tussen het team nodig dat nieuwe eigenschappen toevoegt en het team dat de code opnieuw in beweging brengt. Het doel is ervoor te zorgen alle code die aan de bestaande plaatsing wordt toegevoegd, wordt getest en, aan de tak van de wolkendiensten wordt opgesteld. In het algemeen betekent dit dat de hoeveelheid code die vastloopt, lager is.

Bovendien moet u plannen dat de inhoud wordt vastgezet wanneer de laatste aanvulling op de inhoud gepland is.

## Aanbevolen procedures {#best-practices}

Houd bij het plannen of uitvoeren van de migratie rekening met de volgende richtlijnen:

* Migreren van auteur naar auteur en Publish naar Publish
* Vraag om een productiekloon die kan worden gebruikt om:
   * Statistieken over opslagplaatsen vastleggen
   * Bewijs van migratieactiviteiten
   * Het migratieplan voorbereiden
   * Vereisten voor het bevriezen van inhoud identificeren
   * Identificeer om het even welke stijgende behoeften op Productie wanneer het doen van de migratie van productie

**Beste praktijken van het Hulpmiddel van de Overdracht van de Inhoud**

Zorg ervoor dat wanneer u live gaat, u de migratie van inhoud uitvoert op productie in plaats van op een kloon. Een goede benadering is [ AZCopy ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) voor de aanvankelijke migratie te gebruiken en dan bovenop extracties vaak (zelfs dagelijks) in werking te stellen om kleinere brokken te halen en om het even welke lading op lange termijn op de AEM te vermijden.

Wanneer u de productiemigratie uitvoert, moet u het gereedschap Inhoud overbrengen niet vanuit een kloon uitvoeren omdat:

* Als een klant tijdens aanvullende migraties versies van inhoud moet migreren, worden de versies niet gemigreerd wanneer de klant het gereedschap Inhoud overbrengen van een kloon uitvoert. Zelfs als de kloon regelmatig van live auteur wordt ontspannen, telkens als een kloon wordt gecreeerd, worden de controlepunten die door het Hulpmiddel van de Overdracht van de Inhoud worden gebruikt om de delta&#39;s te berekenen teruggesteld.
* Aangezien een kloon niet als geheel kan worden verfrist, moet het ACL pakket van de Vraag worden gebruikt om de inhoud te verpakken en te installeren die van productie aan kloon wordt toegevoegd of wordt uitgegeven. Het probleem met deze aanpak is dat verwijderde inhoud op de broninstantie nooit naar de kloon wordt gebracht, tenzij deze handmatig wordt verwijderd uit zowel de bron als de kloon. Hierdoor wordt de mogelijkheid geïntroduceerd dat de verwijderde inhoud op de productie niet wordt verwijderd op de kloon en AEM as a Cloud Service.

**Optimizing de lading op uw AEM bron terwijl het uitvoeren van de inhoudsmigratie**

Vergeet niet dat de belasting op de AEM tijdens de extractiefase groter is. Let op het volgende:

* Het gereedschap Inhoud overbrengen is een extern Java-proces dat een JVM-heap van 4 GB gebruikt
* De niet-AzCopy versie downloadt binaire getallen, slaat hen op een tijdelijke ruimte op de bron AEM auteur, verbruikt schijf I/O, dan uploadt in de Azure container die netwerkbandbreedte verbruikt
* [ AzCopy ](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) brengt direct van de blob opslag aan de Azure container over die schijf I/O en netwerkbandbreedte bespaart. De versie AzCopy gebruikt nog de schijf en de netwerkbandbreedte om de gegevens uit de segmentopslag in de Azure-container te halen en te uploaden
* Het proces van het Hulpmiddel van de Overdracht van de Inhoud is lichter op de systeembronnen tijdens de innamefase, aangezien het slechts stromen ingeslikt logboeken en er niet veel lading op de broninstantie voor schijf I/O of netwerkbandbreedte betrokken is.

## Bekende beperkingen {#known-limitations}

Houd er rekening mee dat de volledige inname mislukt als een van de volgende beperkingen wordt aangetroffen als onderdeel van de uitgenomen migratieset:

* Een JCR-knooppunt met een naam van meer dan 150 tekens
* Een JCR-knooppunt dat groter is dan 16 MB
* Elke gebruiker/groep met `rep:AuthorizableID` die wordt ingevoerd en al aanwezig is op AEM as a Cloud Service
* Als een middel dat wordt geëxtraheerd en ingepakt, naar een ander pad wordt verplaatst op de bron of de bestemming vóór de volgende herhaling van de migratie.

## Systeemgezondheid {#asset-health}

Vergeleken met de sectie boven het innemen **niet** om de volgende activazorgen ontbreekt. Het wordt echter ten zeerste aanbevolen om in deze scenario&#39;s de juiste stappen te ondernemen:

* Elk element met de oorspronkelijke uitvoering ontbreekt
* Een map waarin een knooppunt `jcr:content` ontbreekt.

Beide bovengenoemde punten worden geïdentificeerd en in het [ rapport van de Analysator van de Beste praktijk ](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) gemeld.

## Live checklist {#Go-Live-Checklist}

Voor meer informatie, raadpleeg de [ Go-Live Checklist ](/help/journey-onboarding/go-live-checklist.md) documentatie.

## Volgende functies {#what-is-next}

Zodra u begrijpt hoe te om de migratie aan AEM as a Cloud Service uit te voeren, kunt u [ Post-gaan-Levende ](/help/journey-migration/post-go-live.md) pagina controleren om uw instantie te houden die regelmatig loopt.
