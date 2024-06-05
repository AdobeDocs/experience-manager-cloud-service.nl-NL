---
title: Implementatiefase
description: Zorg ervoor dat uw code en inhoud klaar zijn voor de migratie naar de cloud
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
feature: Migration
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '2282'
ht-degree: 8%

---

# Implementatiefase {#implementation-phase}

In de implementatiefase van de reis, zult u de hulpmiddelen onderzoeken waardoor u uw code en inhoud klaar kunt maken om over aan AEM as a Cloud Service worden bewogen.

## Het verhaal tot nu toe {#story-so-far}

In de vorige delen van de reis ben je doorgegaan [kennis krijgen van de veranderingen in AEM as a Cloud Service](/help/journey-migration/getting-started.md)en bepaalt of uw implementatie klaar is om met de [gereedheidsfase](/help/journey-migration/readiness.md).

Dit artikel gaat verder met advies over het gebruik van de Adobe die u kunt bieden om ervoor te zorgen dat uw code en inhoud klaar zijn om naar de cloud te worden verplaatst.

## Doelstelling {#objective}

Dit document beoogt:

* Introduceer u tot de Manager van de Wolk, AEM ononderbroken integratie en leveringskader dat wordt gebruikt om code aan AEM as a Cloud Service op te stellen
* Krijg u aan snelheid met het hulpmiddel van de inhoudoverdracht
* Beschrijf de hulpmiddelen van het coderefactoring u moet gebruiken zodat kunt u uw code voor AEM as a Cloud Service moderniseren

## Cloud Manager gebruiken {#using-cloud-manager}

Voordat u begint, moet u zich vertrouwd maken met Cloud Manager, aangezien dit het enige mechanisme is voor het implementeren van code AEM as a Cloud Service.

Met Cloud Manager kunnen organisaties AEM in de cloud helemaal zelf beheren. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid.

U kunt vertrouwd raken met het gebruik van Cloud Manager door de onderstaande bronnen te raadplegen:

* [Onboarding Journaal](/help/journey-onboarding/overview.md) om zelf-hulpmiddelen over aan boord te nemen voor as a Cloud Service Experience Manager te begrijpen.

* [Git integreren met Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) biedt informatie over het gebruik van een Single Git-repository voor het implementeren van code.

* [Adobe Experience as a Cloud Service-configuratie](/help/security/ims-support.md#aem-configuration) biedt informatie over het beheer van producten en gebruikerstoegang in Admin Console.

## Met de Adobe Tools kunt u uw inhoud en codewolk gereed maken {#use-tools-to-make-code-and-content-cloud-ready}

De exacte stappen van de overgang naar de Cloud Service zijn afhankelijk van de systemen die u hebt aangeschaft en de levenscycluspraktijken van de softwareontwikkeling die u volgt.

Het volgende cijfer toont de belangrijkste stappen betrokken in de fase die uw code en inhoud voor gebruik met AEM as a Cloud Service impliceert omzetten:

![afbeelding](/help/journey-migration/assets/exec-image1.png)

We gaan de gereedschappen die u nodig hebt, in detail beschrijven, zodat u dit kunt bereiken in de onderstaande hoofdstukken.

## Inhoud migreren {#content-migration}

Als u inhoud van de huidige AEM naar de instantie van de Cloud Service wilt migreren, kunt u het gereedschap Inhoud overbrengen van de Adobe gebruiken.

Hiermee geeft u precies aan welke subset van content moet worden overgedragen van uw AEM-broninstantie naar uw AEM Cloud Service-instantie.

De Migratie van de inhoud is een multi-step proces dat planning, het volgen, en samenwerking tussen verschillende teams vereist.

Zie voor meer informatie over de werking van het gereedschap en de manier waarop de Adobe u aanraadt het te gebruiken de [Documentatie van het gereedschap Inhoud overbrengen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Code Refactoring {#code-refactor}

### Instellen voor ontwikkeling {#set-up-for-development}

Het is tijd om de bestaande eigenschappen te beginnen reactoring om met Cloud Servicen compatibel te zijn.

Eerst, bekijk de documentatie detailleert het basistooling, en begin het refactoring van uw code:


* Tijdens planning, is het een goed idee om een lijst van gebieden te hebben die moeten worden bewaakt om met AEM as a Cloud Service compatibel te zijn. U kunt revisie [Richtlijnen voor ontwikkeling](/help/implementing/developing/introduction/development-guidelines.md) voor meer informatie over hoe te om code voor Cloud Service te beproeven en te optimaliseren.
* Lees meer over hoe u [Configuraties beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html#what-is-a-configuration) in AEM as a Cloud Service.
* Leer hoe u een lokale ontwikkelomgeving kunt instellen door de [AS A CLOUD SERVICE SDK AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html)
* Tot slot moet u zich vertrouwd maken met de [as a Cloud Service Java API AEM](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

Ook kunt u het volgende doen:

* Bekijk deze video om te begrijpen hoe u de Dispatcher SDK lokaal kunt installeren:

  >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Bekijk deze video om te begrijpen hoe u Dispatcher SDK kunt configureren:

  >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Een wijziging in de inspringing {#a-change-in-mindset}

Voor het ontwikkelen en uitvoeren van code in AEM as a Cloud Service is een mentaliteitswijziging vereist. Code moet robuust en veerkrachtig zijn, vooral omdat een instantie op elk moment kan worden gestopt. Code in Cloud Service moet &#39;beseffen&#39; dat deze altijd in een cluster wordt uitgevoerd. Dit betekent dat er altijd meer dan één instantie actief is.

Bepaalde veranderingen worden vereist om AEM Maven projecten wolkencompatibel te zijn. AEM as a Cloud Service vereist een scheiding van *content* en *code* in afzonderlijke pakketten voor implementatie in AEM:

* `/apps` en `/libs` worden beschouwd als onveranderlijke AEM, omdat deze niet kunnen worden gewijzigd nadat AEM is gestart (dat wil zeggen bij uitvoering). Dit omvat het maken, bijwerken of verwijderen van bewerkingen. Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

* Alle andere gegevens in de opslagplaats, (bijvoorbeeld `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp`) zijn alle veranderbare gebieden, wat betekent dat deze tijdens runtime kunnen worden gewijzigd.

U kunt meer leren door de [Aanbevolen pakketstructuur](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) documentatie.


### Hulpprogramma&#39;s voor cloudmigratie {#cloud-migration-tools}

De Adobe verstrekt verscheidene hulpmiddelen helpen sommige van uw code refactoring taken versnellen. Als u deze gereedschappen en de problemen die ze oplossen begrijpt, wordt de migratie minder complex en sneller.

* [Workflowmigratie van middelen](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), een hulpmiddel dat wordt gebruikt om werkstromen voor de verwerking van bedrijfsmiddelen automatisch te migreren
* [Dispatcher Converter](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), een hulpmiddel dat uw bestaande configuraties van de Verzender in een formaat omzet dat klaar voor AEM as a Cloud Service is.
* [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html), een hulpmiddel dat een AEM Multimode project als input neemt en het in AEM as a Cloud Service omzet
* [Indexconversie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html), een gereedschap waarmee indexen worden omgezet in een formulier dat compatibel is met AEM as a Cloud Service
* [Moderniseringsinstrumenten](/help/journey-migration/refactoring-tools/aem-modernization-tools.md), een reeks hulpprogramma&#39;s die kunnen worden gebruikt om bestaande AEM te converteren naar de moderne en ondersteunde mogelijkheden van AEM as a Cloud Service.

Als u de lokale ontwikkelomgeving hebt ingesteld, kunt u de AEM as a Cloud Service SDK leren kennen door de [documentatie](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md).

### Een code bevriezen plannen {#schedule-a-code-freeze}

Om uw aan de gang zijnde codeontwikkeling op uw actieve AEM samen met de code te beheren refactoring taken als deel van uw overgangsreis, adviseert de Adobe dat u een periode van de codeschrift plant tot u voltooit het herstructureren van uw Geweven project om met AEM as a Cloud Service compatibel te zijn.

Zodra de projectherstructurering wordt gedaan, kunt u nieuwe codeontwikkeling hervatten die op deze nieuwe structuur wordt gebaseerd. Hierdoor worden fouten in de pijplijnen van Cloud Manager tijdens het implementeren en testen van code verminderd.

>[!NOTE]
>De taken Inhoudsoverdracht en Codereflector hoeven niet opeenvolgend te worden uitgevoerd. Deze taken kunnen onafhankelijk van elkaar worden uitgevoerd. De juiste projectstructuur is echter vereist om ervoor te zorgen dat de content correct wordt weergegeven in uw Cloud Service-omgeving.

## Beste praktijken voor de Plaatsing van de Code en het Testen {#best-practices}

De pijplijn van de Manager van de Wolk steunt uitvoering van tests die tegen het werkgebiedmilieu lopen.

Volg de aanbevolen procedures in de onderstaande documenten met betrekking tot het testen van de codekwaliteit:

* [Testen van de codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md), een document waarin het schrijven van testscripts wordt beschreven en waarin het concept van aanbevolen dekking van ten minste 50% wordt toegelicht.
* [Aangepaste regels voor codekwaliteit](/help/implementing/cloud-manager/custom-code-quality-rules.md) waarmee wordt beoogd de kwaliteitsregels voor aangepaste code te beschrijven die worden uitgevoerd door Cloud Manager en die zijn gemaakt op basis van de beste werkwijzen van AEM Engineering.

## Voorbereiden op Go-Live {#preparing-for-go-live}

Wanneer u het bronsysteem op migratie voorbereidt, zijn er taken op systeem- en AEM-beheerdersniveau nodig. U kunt beginnen door te controleren of de inhoud in de gegevensopslagruimte goed wordt onderhouden door de [revisie opruimen](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html) en de [opschonen van opslaggegevens](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html) taakstatus. Als u AEM versie 6.3 uitvoert (aangezien het Hulpmiddel van de Overdracht van de Inhoud vanaf versie 6.3 compatibel is), adviseert men om off-line compensatie uit te voeren, die door de inzameling van het huisvuil van de Opslag van Gegevens wordt gevolgd.

[Controle van gegevensconsistentie](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html) wordt aanbevolen voor alle AEM versies om ervoor te zorgen dat de opslagplaats voor inhoud in goede staat is om migratieactiviteiten te initiëren.

Toegang op beheerdersniveau is vereist voor installatie en configuratie [AZCopy](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md)

U wordt ook aangeraden ongebruikte middelen, pagina&#39;s, AEM projecten, gebruikers en groepen te controleren om tijd te besparen bij de migratie. Zie de [Gezondheid opslagplaats voor inhoud](#repository-health) sectie.

### Gezondheid opslagplaats voor inhoud {#repository-health}

Eenmaal toegang tot [productiekloon](#proof-of-migration) wordt ingesteld om de gezondheid van de gegevensopslagplaats te controleren. Zoals vermeld in de vorige sectie, is het doel de opslagplaats op de bron schoon te maken en te comprimeren alvorens de migratie te beginnen. Deze stap bespaart mogelijk veel tijd anders aan het oplossen van problemenkwesties zodra de migratie begint.

| Item handeling | Key Takeaways |
|---------|----------|
| Gebruikers, groepen en machtigingen | U moet het volume van gebruikers, groepen, en ingewikkeldheid rond lidmaatschappen begrijpen. Zoek naar mogelijkheden om ongebruikte gebruikers, groepen in de bron vóór migratie op te schonen. |
| Onvolledige verwerking van middelen | Probeer de verwerking van elementen in het bronsysteem te voltooien voordat u de migratie start om mogelijke problemen bij AEM as a Cloud Service post migratie te voorkomen. |
| Inhoudsstatus | U wordt aangeraden te zoeken naar onjuiste inhoud en deze leeg te maken voordat u de migratie start. Zoek bijvoorbeeld naar elementen of pagina&#39;s die geen oorspronkelijke uitvoeringen hebben of die vastzitten in de verwerking van de workflow. Zie ook [Systeemgezondheid](#asset-health). |

## Gegevens verzamelen {#gathering-data}

>[!NOTE]
> De [Strategie en tijdlijn voor migratie van inhoud](#content-strategy-and-timeline) in deze sectie wordt nader beschreven hoe u de verzamelde gegevens kunt extrapoleren en een migratieplan kunt maken.

Het verzamelen van gegevens kan u helpen de migratieactiviteiten en bijbehorende taken plannen. De extractie- en innametijden zijn bijzonder handig omdat de gegevenspunten kunnen worden gekoppeld aan een specifieke grootte van de migratieset. Deze gegevenspunten kunnen als zodanig worden geëxtrapoleerd om een plan op te stellen:

* Totale hoeveelheid tijd die is besteed voor [extractie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md)
* Totale hoeveelheid tijd die is besteed voor [ingestie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Totale hoeveelheid tijd die voor de aanvulling is vereist [extractie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process)
* Totale hoeveelheid tijd die voor de aanvulling is vereist [ingestie](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)


<!-- Alexandru: hiding this for now

One more important datapoint is the amount of time it takes to complete the [user mapping](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), if this is coupled with the content migration. You can take this data point into consideration for more realistic estimates, because it is added to the overall extraction timeline and it may not be required to run it during top-ups.

-->

Deze gegevenspunten kunnen u ook helpen [KPI&#39;s instellen](/help/journey-migration/readiness.md#establish-kpis) en andere migratietaken.

### Migratieplan {#migration-plan}

Gebaseerd op de gegevenspunten u (zie hierboven) verzamelde, kunt u een migratieplan tot stand brengen dat in een macroprojectplan kan worden geïntegreerd. Met deze stap kunnen alle belangrijke belanghebbenden de migratieactiviteiten visualiseren en plannen.

De volgende tabel illustreert een typisch migratieplan:

| Migratie-herhaling | Begindatum | Geschatte einddatum | Afhankelijkheden | Geschatte duur (in dagen) | Aanvullende details/actiepunten |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |   |   |   |   |   |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |   |   |   |   |   |

Zoals u in de bovenstaande tabel kunt zien, is het nuttig om een specifieke naamgevingsindeling te gebruiken om de migratieherhalingen te identificeren, bijvoorbeeld: **PRDCLONE** voor de AEM van de bron, **AUTEUR/PUBLICEREN** voor de AEM as a Cloud Service omgeving, **CSSTAGE-AUTEUR** voor de AEM as a Cloud Service instantie enzovoort.

Enkele belangrijke details die van invloed zijn op uw migratieplan:

**Het totale aantal vereiste extracties**

* Auteur- en publicatie-extracties in specifieke omgevingen worden beschouwd als twee parallelle extracties, omdat ze onafhankelijk van elkaar zijn.
* Aantal top-up extracties gebaseerd op de groei van de opslagplaats in specifieke tijdsperiodes.

**Totaal aantal vereiste verteringsproblemen**

* Het is belangrijk om dit punt in het plan te vangen, aangezien een gehaalde reeks in veelvoudige milieu&#39;s van de Cloud Service kan worden opgenomen.
* Aantal top-up ingestions.
* Het migreren van inhoud van de BronAuteur aan de instantie van de de dienstauteur van de Wolk en van Bron publiceren aan Cloud Service publiceert is de beste praktijken om te vermijden het opnemen van alle inhoud van de Auteur in de Cloud Service publiceren.

### Migratiebeheer {#migration-tracker}

U kunt de migratiecontracker gebruiken om de tijden voor zowel de aanvankelijke als top-up looppas neer te noteren. Met deze gegevenspunten kunt u vóór de laatste top-up realistische vereisten voor het bevriezen van inhoud formuleren.

De tracker helpt u ook om:

* Eventuele afwijkingen van de planner identificeren die aanpassingen in de plan- of go-live tijdlijnen vereisen
* Verstrek een realistische status die in alle noodzakelijke mededelingen kan worden gebruikt
* Plan voor initiële of toekomstige aanvullende migratie

De volgende tabel illustreert een functionele migratiecontracker:

| Bron (Omgeving / Instantie / URL) | Doel (omgeving / instantie / URL) | Naam migratieset, type (bij openen of boven) | Grootte migratieset (MB) | Gebruikerstoewijzing (Ja/Nee) | Duur van extractie (begin, eind, genomen tijd) | Ingestieduur (begin, einde, tijd genomen) | Problemen/resoluties/details |
|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |

## Strategie en tijdlijn voor migratie van inhoud {#content-strategyand-timeline}

In de volgende sectie worden de belangrijke stappen en bijbehorende taken weergegeven die kunnen worden gebruikt om een strategie en tijdlijn voor inhoudsmigratie te formuleren.

![afbeelding](/help/journey-migration/assets/content-migration2.png)

### Inrichting {#fitment}

* Voer revisie schoonmaak uit, de inzameling van de gegevensopslag en de controles van de gegevensconsistentie. Zie ook [Voorbereiden op Go-Live](#preparing-for-go-live)
* [Statistieken verzamelen](#gathering-data) over de AEM bronopslagplaats:
   * Grootte van segmentarchief
   * Grootte van indexarchief
   * Aantal pagina&#39;s
   * Aantal activa
   * Aantal gebruikers en groepen
* Controleer of de volgende functies zijn ingeschakeld op de AEM-bron (ook vereist in AEM as a Cloud Service):
   * Slimme tags toepassen
   * Zoeken op gelijkenis
   * Zoeken naar tekst in woord- en PDF-documenten
* Verzamel de Analysator van Beste praktijken [verslag](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* Importeren in het dialoogvenster [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * Herzie de zelf-analyseaanbeveling om ervoor te zorgen dat AEM as a Cloud Service de opslagvereisten kan behandelen.
* Maak een ondersteuningsticket voor de Adobe voor eventuele verduidelijkingen voordat u doorgaat met het migratieplan.

### Bewijs van migratie {#proof-of-migration}

* Vraag een productiekloon aan die:
   * Is in de zelfde netwerkstreek
   * Productie-inhoud leveren zoals gebruikers en groepen
   * Clones auteur en publish - één knoop elk in het geval van een cluster of publiceer landbouwbedrijf
* Kies een subset van de inhoud die wordt gemigreerd, zodat:
   * Het is een mix van alle beschikbare inhoudstypen
   * Bevat alle gebruikers en groepen
* Bevat 25% van de inhoud of maximaal 1 TB aan inhoud, afhankelijk van welke waarde het minst is.
* ten minste één volledig uitvoeren en [top-up](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) migratie, van de productiekloon naar de AEM as a Cloud Service niet-productieomgeving
* Los mogelijke problemen op zoals:
   * Schijfruimte op de AEM
   * Connectiviteit tussen AEM bron en AEM as a Cloud Service
   * Alle [beperkingen met betrekking tot inname](go-live.md#known-limitations).
* Neem de tijd op die u nodig hebt [extractie en inname](#gathering-data):
   * Weet hoeveel inhoud per week wordt toegevoegd
   * Extrapoleer de tijden die van het bewijs van migratie worden gemeten om tot een [migratieplan](#migration-plan).

## Volgende functies {#what-is-next}

Nadat u volledig hebt begrepen hoe te om te beoordelen of uw AEM installatie klaar is om aan de wolk te worden bewogen, aangezien wij leren hoe te om de hulpmiddelen te gebruiken nodig om het klaar te maken, is het tijd om zich op aan te zetten [introductiefase](/help/journey-migration/go-live.md).
