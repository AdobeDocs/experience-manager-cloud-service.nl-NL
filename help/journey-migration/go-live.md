---
title: Go-Live
description: Leer hoe u de migratie uitvoert als de code en de inhoud klaar zijn voor de cloud
exl-id: 10ec0b04-6836-4e26-9d4c-306cf743224e
source-git-commit: ecf4c06fd290d250c14386b3135250633b26c910
workflow-type: tm+mt
source-wordcount: '1721'
ht-degree: 0%

---

# Go-Live {#go-live}

>[!CONTEXTUALHELP]
>id="aemcloud_golive_prep"
>title="Go-Live-voorbereiding"
>abstract="Om ervoor te zorgen dat AEM as a Cloud Service probleemloos en succesvol kan gaan werken, moet u plannen voor het bevriezen van code en inhoud, testversies, aanvullingen op inhoud, prestatietests, beveiligingstests en meer."

In dit deel van de reis, leert u hoe te om de migratie te plannen en uit te voeren zodra zowel de code als de inhoud klaar zijn om over aan AEM as a Cloud Service te worden bewogen. Bovendien leert u wat de beste praktijken en bekende beperkingen zijn wanneer u de migratie uitvoert.

## Het verhaal tot nu toe {#story-so-far}

In de vorige fasen van de reis:

* U hebt geleerd hoe u aan de slag kunt met de stap naar AEM as a Cloud Service in het dialoogvenster [Aan de slag](/help/journey-migration/getting-started.md) pagina.
* Vastgesteld of uw implementatie gereed is om naar de cloud te worden verplaatst door het lezen van de [Gereedheidsfase](/help/journey-migration/readiness.md)
* U bent vertrouwd met de gereedschappen en het proces waarmee u uw code en inhoud in de cloud kunt plaatsen [Implementatiefase](/help/journey-migration/implementation.md).

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe te om de migratie uit te voeren aan AEM as a Cloud Service zodra u met de vorige stappen van de reis vertrouwd bent. U leert hoe u de initiële migratie van productie uitvoert en de beste werkwijzen die u kunt volgen wanneer u naar AEM as a Cloud Service migreert.

## Oorspronkelijke productiemigratie {#initial-migration}

Voordat u de migratie van de productie kunt uitvoeren, volgt u de stappen voor de implementatie en het bewijs van migratie die in het dialoogvenster [Strategie en tijdlijn voor migratie van inhoud](/help/journey-migration/implementation.md##strategy-timeline) van de [Implementatiefase](/help/journey-migration/implementation.md).

* De migratie vanuit de productie starten op basis van de ervaring die u hebt opgedaan tijdens de migratie van het AEM as a Cloud Service stadium die op klonen is uitgevoerd:
   * Auteur
   * Publiceren en publiceren

* Valideer de inhoud die in zowel de AEM as a Cloud Service auteur als publicatielagen wordt opgenomen.
* Geef het ontwerpteam van de inhoud de opdracht om te voorkomen dat inhoud op zowel de bron als de bestemming wordt verplaatst totdat de opname is voltooid
* Nieuwe inhoud kan worden toegevoegd, bewerkt of verwijderd, maar u kunt het verplaatsen voorkomen. Dit geldt zowel voor de bron als voor de bestemming.
* Neem de [tijd genomen](/help/journey-migration/implementation.md#gathering-data) voor volledige extractie en inname een schatting te hebben van de toekomstige aanvullende migratietermijnen.
* Een [migratieplanner](/help/journey-migration/implementation.md#migration-plan) voor zowel auteur als publicatie.

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

* Migreren van auteur naar auteur en publiceren naar publicatie
* Vraag om een productiekloon die kan worden gebruikt om:
   * Statistieken over opslagplaatsen vastleggen
   * Bewijs van migratieactiviteiten
   * Het migratieplan voorbereiden
   * Vereisten voor het bevriezen van inhoud identificeren
   * Identificeer om het even welke stijgende behoeften op Productie wanneer het doen van de migratie van productie

**Tips en trucs voor het gereedschap Inhoud overbrengen**

Zorg ervoor dat wanneer u live gaat, u de migratie van inhoud uitvoert op productie in plaats van op een kloon. Een goede aanpak is het gebruik van [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) voor de initiële migratie en vervolgens regelmatig (zelfs dagelijks) aanvullende extracties uitvoeren om kleinere stukjes te extraheren en om langdurige belasting op de AEM te voorkomen.

Wanneer u de productiemigratie uitvoert, moet u het gereedschap Inhoud overbrengen niet vanuit een kloon uitvoeren omdat:

* Als een klant tijdens aanvullende migraties versies van inhoud moet migreren, worden de versies niet gemigreerd wanneer de klant het gereedschap Inhoud overbrengen van een kloon uitvoert. Zelfs als de kloon regelmatig van live auteur wordt ontspannen, telkens als een kloon wordt gecreeerd, worden de controlepunten die door het Hulpmiddel van de Overdracht van de Inhoud worden gebruikt om de delta&#39;s te berekenen teruggesteld.
* Aangezien een kloon niet als geheel kan worden verfrist, moet het ACL pakket van de Vraag worden gebruikt om de inhoud te verpakken en te installeren die van productie aan kloon wordt toegevoegd of wordt uitgegeven. Het probleem met deze aanpak is dat verwijderde inhoud op de broninstantie nooit naar de kloon wordt gebracht, tenzij deze handmatig wordt verwijderd uit zowel de bron als de kloon. Hierdoor wordt de mogelijkheid geïntroduceerd dat de verwijderde inhoud op de productie niet wordt verwijderd op de kloon en AEM as a Cloud Service.

**De belasting van de AEM optimaliseren tijdens het migreren van de inhoud**

Vergeet niet dat de belasting op de AEM tijdens de extractiefase groter is. Let op het volgende:

* Het gereedschap Inhoud overbrengen is een extern Java-proces dat een JVM-heap van 4 GB gebruikt
* De niet-AzCopy versie downloadt binaire getallen, slaat hen op een tijdelijke ruimte op de bron AEM auteur, verbruikt schijf I/O, dan uploadt in de Azure container die netwerkbandbreedte verbruikt
* [AzCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) brengt direct van de blob opslag aan de Azure container over die schijf I/O en netwerkbandbreedte bewaart. De versie AzCopy gebruikt nog de schijf en de netwerkbandbreedte om de gegevens uit de segmentopslag in de Azure-container te halen en te uploaden
* Het proces van het Hulpmiddel van de Overdracht van de Inhoud is lichter op de systeembronnen tijdens de innamefase, aangezien het slechts stromen ingeslikt logboeken en er niet veel lading op de broninstantie voor schijf I/O of netwerkbandbreedte betrokken is.

## Bekende beperkingen {#known-limitations}

Houd er rekening mee dat de volledige inname mislukt als een van de volgende beperkingen wordt aangetroffen als onderdeel van de uitgenomen migratieset:

* Een JCR-knooppunt met een naam van meer dan 150 tekens
* Een JCR-knooppunt dat groter is dan 16 MB
* Elke gebruiker/groep met `rep:AuthorizableID` die al aanwezig zijn op AEM as a Cloud Service
* Als een middel dat wordt geëxtraheerd en ingepakt, naar een ander pad wordt verplaatst op de bron of de bestemming vóór de volgende herhaling van de migratie.

## Systeemgezondheid {#asset-health}

Vergeleken met de sectie boven de ingestie **niet** mislukt vanwege de volgende problemen met activa. Het wordt echter ten zeerste aanbevolen om in deze scenario&#39;s de juiste stappen te ondernemen:

* Elk element met de oorspronkelijke uitvoering ontbreekt
* Een map waarin een map ontbreekt `jcr:content` knooppunt.

Beide items worden geïdentificeerd en gerapporteerd in de [Best Practice Analyzer](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md) verslag.

## Live checklist {#Go-Live-Checklist}

Controleer deze lijst met activiteiten om ervoor te zorgen dat de migratie soepel en succesvol verloopt.

* Voer een end-to-end productiepijplijn uit met functionele en UI-tests om een **altijd huidig** AEM productervaring. Zie de volgende bronnen.
   * [Versie-updates AEM](/help/implementing/deploying/aem-version-updates.md)
   * [Aangepaste functionele tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing)
   * [UI-tests](/help/implementing/cloud-manager/ui-testing.md)
* Inhoud migreren naar productie en ervoor zorgen dat een relevante subset beschikbaar is voor testdoeleinden.
   * De beste praktijken van DevOps voor AEM impliceren dat de code zich omhoog van ontwikkeling aan het productiemilieu beweegt terwijl de inhoud zich van productiemilieu&#39;s beweegt.
* Plan een code- en inhoudstijdsperiode.
   * Zie ook de sectie [Tijdlijnen voor code en inhoud vastzetten voor migratie](#code-content-freeze)
* Voer de laatste top-up van de inhoud uit.
* Valideer de configuraties van de verzender.
   * Gebruik een lokale verzender-validator waarmee de verzender lokaal kan worden geconfigureerd, gevalideerd en gesimuleerd
      * [Stel de lokale verzendprogramma&#39;s in.](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html#prerequisites)
   * Herzie zorgvuldig de virtuele gastheerconfiguratie.
      * De eenvoudigste (en standaard) oplossing moet `ServerAlias *` in uw virtuele hostbestand in het dialoogvenster `/dispatcher/src/conf.d/available_vhostsfolder`.
         * Hierdoor kunnen de hostaliassen die door productfunctionele tests, cachevalidatie van de verzender en klonen worden gebruikt, functioneren.
      * Als `ServerAlias *` niet aanvaardbaar is, ten minste: `ServerAlias` ingangen moeten naast uw douanedomeinen worden toegestaan:
         * `localhost`
         * `*.local`
         * `publish*.adobeaemcloud.net`
         * `publish*.adobeaemcloud.com`
* Vorm CDN, SSL en DNS.
   * Als u uw eigen CDN gebruikt, ga een steunkaartje in om aangewezen het verpletteren te vormen.
      * Zie de sectie [CDN van de klant wijst naar AEM Beheerde CDN](/help/implementing/dispatcher/cdn.md#point-to-point-cdn) in de CDN-documentatie voor meer informatie.
      * Vorm SSL en DNS volgens de documentatie van uw verkoper CDN.
   * Als u geen extra CDN gebruikt, beheer SSL en DNS volgens de volgende documentatie:
      * SSL-certificaten beheren
         * [Inleiding tot het beheren van SSL-certificaten](/help/implementing/cloud-manager/managing-ssl-certifications/introduction.md)
         * [SSL-certificaat beheren](/help/implementing/cloud-manager/managing-ssl-certifications/managing-certificates.md)
      * Aangepaste domeinnamen (DNS) beheren
         * Om ervoor te zorgen dat de DNS cutover geen onverwachte problemen zal introduceren, is het best om een testsubdomain tot stand te brengen om uw productieinstantie aan te sluiten alvorens u gaat-leven en een ronde van het testen van UAT doet. Dus als uw domein example.com is, kunt u een subdomein maken test.example.com en dit toepassen op productie. Tijdens het testen van de UAT van het domein zult u dingen zoals juiste verbindingsredirection, caching, en verzender configuraties willen zoeken.
         * [Inleiding tot aangepaste domeinnamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md)
         * [Een aangepaste domeinnaam toevoegen](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md)
         * [Aangepaste domeinnaam beheren](/help/implementing/cloud-manager/custom-domain-names/managing-custom-domain-names.md)
   * Herinner me om TTL te bevestigen die voor uw DNS verslag wordt geplaatst.
      * TTL is de hoeveelheid tijd een DNS verslag in een geheim voorgeheugen alvorens de server om een update te vragen blijft.
      * Als u zeer hoge TTL hebt, zullen de updates aan uw DNS verslag langer duren om zich te verspreiden.
* Voer prestatie- en beveiligingstests uit die voldoen aan uw zakelijke vereisten en doelstellingen.
   * Test de werkgebiedomgeving.  Het is even groot als de productie.
   * Ontwikkelomgevingen hebben niet dezelfde grootte als stadium en productie.
* Besnoeiing over en zorg ervoor dat daadwerkelijke go-live zonder enige nieuwe plaatsing of inhoudsupdate wordt uitgevoerd.
* Maak profielen voor gebruikersmeldingen van Admin Consoles. Zie [Meldingsprofielen](/help/journey-onboarding/notification-profiles.md)

U kunt altijd naar de lijst verwijzen als u uw taken opnieuw moet kalibreren tijdens het uitvoeren van de migratie.

## Volgende functies {#what-is-next}

Als u begrijpt hoe u de migratie naar AEM as a Cloud Service kunt uitvoeren, kunt u de knop [Nav. live](/help/journey-migration/post-go-live.md) pagina om de instantie vloeiend te laten werken.
