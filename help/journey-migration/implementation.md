---
title: Implementatiefase
description: Zorg ervoor dat uw code en inhoud klaar zijn voor de migratie naar de cloud
exl-id: d124f9a5-a754-4ed0-a839-f2968c7c8faa
feature: Migration
role: Admin
source-git-commit: 913b1beceb974243f0aa7486ddd195998d5e9439
workflow-type: tm+mt
source-wordcount: '2288'
ht-degree: 8%

---

# Implementatiefase {#implementation-phase}

In de implementatiefase van de reis, zult u de hulpmiddelen onderzoeken waardoor u uw code en inhoud klaar kunt maken om over naar AEM as a Cloud Service te worden verplaatst.

## Het verhaal tot nu toe {#story-so-far}

In de vorige delen van de reis, bent u gegaan door [&#x200B; die met de veranderingen in AEM as a Cloud Service &#x200B;](/help/journey-migration/getting-started.md) vertrouwd worden, en bepaald als uw plaatsing klaar is om aan de wolk met de [&#x200B; gereedheidsfase &#x200B;](/help/journey-migration/readiness.md) worden bewogen.

Dit artikel gaat verder met advies over het gebruik van de Adobe die u kunt bieden om ervoor te zorgen dat uw code en inhoud klaar zijn om naar de cloud te worden verplaatst.

## Doelstelling {#objective}

Dit document beoogt:

* Introduceer u aan Cloud Manager, AEM voortdurend integratie en leveringskader dat wordt gebruikt om code aan AEM as a Cloud Service op te stellen
* Krijg u aan snelheid met het hulpmiddel van de inhoudoverdracht
* Beschrijf de hulpmiddelen van het coderefactoring u moet gebruiken zodat kunt u uw code voor AEM as a Cloud Service moderniseren

## Cloud Manager gebruiken {#using-cloud-manager}

Voordat u begint, moet u zich vertrouwd maken met Cloud Manager omdat dit het enige mechanisme is voor het implementeren van code naar AEM as a Cloud Service.

Met Cloud Manager kunnen organisaties AEM in de cloud helemaal zelf beheren. Cloud Manager biedt een kader voor doorlopende integratie en levering (CI/CD) waarmee IT-teams en implementatiepartners sneller hun updates en wijzigingen kunnen doorvoeren, zonder verlies in prestaties of veiligheid.

U kunt vertrouwd raken met het gebruik van Cloud Manager door de onderstaande bronnen te raadplegen:

* [&#x200B; Onboarding Reis &#x200B;](/help/journey-onboarding/overview.md) om zelfhulpmiddelen over onboarding voor Experience Manager as a Cloud Service te begrijpen.

* [Git integreren met Adobe Cloud Manager](/help/implementing/cloud-manager/managing-code/integrating-with-git.md) biedt informatie over het gebruik van een Single Git-repository voor het implementeren van code.

* [Adobe Experience as a Cloud Service-configuratie](/help/security/ims-support.md#aem-configuration) biedt informatie over het beheer van producten en gebruikerstoegang in Admin Console.

## Met de Adobe Tools kunt u uw inhoud en codewolk gereed maken {#use-tools-to-make-code-and-content-cloud-ready}

De exacte stappen van de overgang naar de Cloud Service zijn afhankelijk van de systemen die u hebt aangeschaft en de levenscycluspraktijken van de softwareontwikkeling die u volgt.

In de volgende afbeelding ziet u de belangrijkste stappen in de fase die het omzetten van uw code en inhoud voor gebruik met AEM as a Cloud Service omvat:

![&#x200B; stappen van de Omzetting &#x200B;](/help/journey-migration/assets/exec-image1.png)

We gaan de gereedschappen die u nodig hebt, in detail beschrijven, zodat u dit kunt bereiken in de onderstaande hoofdstukken.

## Inhoud migreren {#content-migration}

Als u inhoud van de huidige AEM naar de instantie van de Cloud Service wilt migreren, kunt u het gereedschap Inhoud overbrengen van de Adobe gebruiken.

Hiermee geeft u precies aan welke subset van content moet worden overgedragen van uw AEM-broninstantie naar uw AEM Cloud Service-instantie.

De Migratie van de inhoud is een multi-step proces dat planning, het volgen, en samenwerking tussen verschillende teams vereist.

Voor een volledig detail op hoe het hulpmiddel werkt en hoe de Adobe adviseert dat u het gebruikt, zie de [&#x200B; documentatie van het Hulpmiddel van de Overdracht van de Inhoud &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/overview-content-transfer-tool.md).

## Code Refactoring {#code-refactor}

### Instellen voor ontwikkeling {#set-up-for-development}

Het is tijd om de bestaande eigenschappen te beginnen reactoring om met Cloud Servicen compatibel te zijn.

Eerst, bekijk de documentatie detailleert het basistooling, en begin het refactoring van uw code:


* Tijdens planning, is het een goed idee om een lijst van gebieden te hebben die moeten worden bewaakt om met AEM as a Cloud Service compatibel te zijn. U kunt [&#x200B; Richtlijnen van de Ontwikkeling &#x200B;](/help/implementing/developing/introduction/development-guidelines.md) voor meer details over herzien en code voor Cloud Service optimaliseren.
* Lees omhoog op hoe te [&#x200B; te leiden Configuraties &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/configurations.html?lang=nl-NL#what-is-a-configuration) in AEM as a Cloud Service.
* Leer hoe te opstelling een Lokale Milieu van de Ontwikkeling door [&#x200B; SDK van AEM as a Cloud Service te downloaden &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=nl-NL)
* Tot slot vertrouwd maken met [&#x200B; AEM as a Cloud Service Java API &#x200B;](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/index.html).

Ook kunt u het volgende doen:

* Bekijk deze video om te zien hoe u de SDK van Dispatcher lokaal kunt installeren:

  >[!VIDEO](https://video.tv.adobe.com/v/30601)

* Bekijk deze video om te begrijpen hoe u de SDK van Dispatcher kunt configureren:

  >[!VIDEO](https://video.tv.adobe.com/v/30602)

### Een wijziging in de inspringing {#a-change-in-mindset}

Voor het ontwikkelen en uitvoeren van code in AEM as a Cloud Service is een mentaliteitswijziging vereist. Code moet robuust en veerkrachtig zijn, vooral omdat een instantie op elk moment kan worden gestopt. Code in Cloud Service moet &#39;beseffen&#39; dat deze altijd in een cluster wordt uitgevoerd. Dit betekent dat er altijd meer dan één instantie actief is.

Bepaalde veranderingen worden vereist om AEM Maven projecten wolkencompatibel te zijn. AEM as a Cloud Service vereist een scheiding van *inhoud* en *code* in verschillende pakketten voor plaatsing in AEM:

* `/apps` en `/libs` worden beschouwd als onveranderlijke gebieden van AEM, omdat ze niet kunnen worden gewijzigd nadat AEM gestart is (dat wil zeggen tijdens runtime). Dit omvat het maken, bijwerken of verwijderen van bewerkingen. Elke poging om een onveranderbaar gebied tijdens runtime te wijzigen, zal mislukken.

* Alle andere elementen in de opslagplaats (bijvoorbeeld `/content` , `/conf` , `/var` , `/home` , `/etc` , `/oak:index` , `/system` , `/tmp` ) zijn veranderbare gebieden, wat betekent dat ze tijdens runtime kunnen worden gewijzigd.

U kunt meer leren door de [&#x200B; Aanbevolen documentatie van de Structuur van het Pakket &#x200B;](/help/implementing/developing/introduction/aem-project-content-package-structure.md#recommended-package-structure) te raadplegen.


### Hulpprogramma&#39;s voor cloudmigratie {#cloud-migration-tools}

De Adobe verstrekt verscheidene hulpmiddelen helpen sommige van uw code refactoring taken versnellen. Als u deze gereedschappen en de problemen die ze oplossen begrijpt, wordt de migratie minder complex en sneller.

* [&#x200B; Migratie van het Werkschema van Activa &#x200B;](/help/journey-migration/moving-to-aem-assets/asset-workflow-migration-tool.md), een hulpmiddel dat wordt gebruikt om de werkschema&#39;s van de activaverwerking automatisch te migreren
* [&#x200B; de Convertor van Dispatcher &#x200B;](/help/journey-migration/refactoring-tools/dispatcher-transformation-utility-tools.md), een hulpmiddel dat uw bestaande configuraties van Dispatcher in een formaat omzet dat voor AEM as a Cloud Service klaar is.
* [&#x200B; Modernizer van de Bewaarplaats &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/repo-modernizer.html?lang=nl-NL), een hulpmiddel dat een AEM Multimode project als input neemt en het in AEM as a Cloud Service één omzet
* [&#x200B; Omzetter van de Index &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/moving/refactoring-tools/index-converter.html?lang=nl-NL), een hulpmiddel dat indexen in een vorm compatibel met AEM as a Cloud Service omzet
* [&#x200B; Moderniseringshulpmiddelen &#x200B;](/help/journey-migration/refactoring-tools/aem-modernization-tools.md), een reeks nut die kan worden gebruikt om erfenis AEM eigenschappen in de moderne en gesteunde mogelijkheden van AEM as a Cloud Service om te zetten.

Zodra u opstelling het lokale ontwikkelmilieu hebt, wordt vertrouwd met AEM as a Cloud Service SDK door de [&#x200B; documentatie &#x200B;](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) te raadplegen.

### Een code bevriezen plannen {#schedule-a-code-freeze}

Om uw aan de gang zijnde codeontwikkeling op uw actieve AEM samen met de code refactoring taken als deel van uw overgangsreis te beheren, adviseert de Adobe dat u een periode van de codeschrift plant tot u voltooit het herstructureren van uw Geweven project om met AEM as a Cloud Service compatibel te zijn.

Zodra de projectherstructurering wordt gedaan, kunt u nieuwe codeontwikkeling hervatten die op deze nieuwe structuur wordt gebaseerd. Dit vermindert Cloud Manager pijpleidingsmislukkingen tijdens codeplaatsing en het testen.

>[!NOTE]
>De taken Inhoudsoverdracht en Codereflector hoeven niet opeenvolgend te worden uitgevoerd. Deze taken kunnen onafhankelijk van elkaar worden uitgevoerd. De juiste projectstructuur is echter vereist om ervoor te zorgen dat de content correct wordt weergegeven in uw Cloud Service-omgeving.

## Beste praktijken voor de Plaatsing van de Code en het Testen {#best-practices}

De Cloud Manager-pijpleiding ondersteunt de uitvoering van tests die worden uitgevoerd tegen de werkgebiedomgeving.

Volg de aanbevolen procedures in de onderstaande documenten met betrekking tot het testen van de codekwaliteit:

* [&#x200B; het Testen van de Kwaliteit van de Code &#x200B;](/help/implementing/cloud-manager/code-quality-testing.md), een document dat het proces beschrijft om testmanuscripten te schrijven en het concept geadviseerde dekking van minstens 50% verklaart.
* [&#x200B; Begrijpend de Regels van de Kwaliteit van de Code van de Douane &#x200B;](/help/implementing/cloud-manager/custom-code-quality-rules.md) die de regels van de douanecode probeert te beschrijven die door Cloud Manager worden uitgevoerd die op beste praktijken van AEM Techniek worden gecreeerd.

## Voorbereiden op Go-Live {#preparing-for-go-live}

Wanneer u het bronsysteem op migratie voorbereidt, zijn er taken op systeem- en AEM-beheerdersniveau nodig. U kunt beginnen door te verifiëren dat de inhoudsbewaarplaats in een goed onderhouden staat is door de [&#x200B; revisie schoonmaakbeurt &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/revision-cleanup.html?lang=nl-NL) en de [&#x200B; status van de de huisvuilinzameling &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/administering/operations/data-store-garbage-collection.html?lang=nl-NL) taak van de gegevensopslag te controleren. Als u AEM versie 6.3 uitvoert (aangezien het Hulpmiddel van de Overdracht van de Inhoud vanaf versie 6.3 compatibel is), adviseert men om off-line compensatie uit te voeren, die door de inzameling van het huisvuil van de Opslag van Gegevens wordt gevolgd.

[&#x200B; de consistentiecontrole van Gegevens &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/consistency-check.html?lang=nl-NL) wordt geadviseerd over alle AEM versies om ervoor te zorgen dat de inhoudsbewaarplaats in een goede staat om migratieactiviteiten in werking te stellen.

De toegang van het de beheerderniveau van het systeem wordt vereist om [&#x200B; AZCopy &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/handling-large-content-repositories.md) te installeren en te vormen

U wordt ook aangeraden ongebruikte Assets, Pagina&#39;s, AEM Projecten, Gebruikers en Groepen te controleren om tijd te besparen bij de migratie. Zie de [&#128279;](#repository-health) sectie van de Gezondheid van de Bewaarplaats van de Inhoud .

### Gezondheid opslagplaats voor inhoud {#repository-health}

Zodra de toegang tot de kloon van de a [&#x200B; productie &#x200B;](#proof-of-migration) wordt gevestigd te werk gaat om de gezondheid van de bewaarplaats te controleren. Zoals vermeld in de vorige sectie, is het doel de opslagplaats op de bron schoon te maken en te comprimeren alvorens de migratie te beginnen. Deze stap bespaart mogelijk veel tijd anders aan het oplossen van problemenkwesties zodra de migratie begint.

| Item handeling | Key Takeaways |
|---------|----------|
| Gebruikers, groepen en machtigingen | U moet het volume van gebruikers, groepen, en ingewikkeldheid rond lidmaatschappen begrijpen. Zoek naar mogelijkheden om ongebruikte gebruikers, groepen in de bron vóór migratie op te schonen. |
| Onvolledige verwerking van middelen | Probeer de verwerking van elementen in het bronsysteem te voltooien voordat u de migratie start om mogelijke problemen in AEM as a Cloud Service na de migratie te voorkomen. |
| Inhoudsstatus | U wordt aangeraden te zoeken naar onjuiste inhoud en deze leeg te maken voordat u de migratie start. Zoek bijvoorbeeld naar elementen of pagina&#39;s die geen oorspronkelijke uitvoeringen hebben of die vastzitten in de verwerking van de workflow. Zie ook [&#x200B; Gezondheid van Activa &#x200B;](#asset-health). |

## Gegevens verzamelen {#gathering-data}

>[!NOTE]
> De [&#x200B; de migratiestrategie van de Inhoud en chronologie &#x200B;](#content-strategy-and-timeline) sectie meer details hoe te om de verzamelde gegevens te extrapoleren en een migratieplan tot stand te brengen.

Het verzamelen van gegevens kan u helpen de migratieactiviteiten en bijbehorende taken plannen. De extractie- en innametijden zijn bijzonder handig omdat de gegevenspunten kunnen worden gekoppeld aan een specifieke grootte van de migratieset. Deze gegevenspunten kunnen als zodanig worden geëxtrapoleerd om een plan op te stellen:

* Totale hoeveelheid tijd die voor [&#x200B; extractie &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md) wordt genomen
* Totale hoeveelheid tijd die voor [&#x200B; wordt genomen inname &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md)
* Totale hoeveelheid tijd die voor bovenop-up [&#x200B; extractie &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/extracting-content.md#top-up-extraction-process) wordt genomen
* Totale hoeveelheid tijd die voor bovenop [&#x200B; wordt genomen inname &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process)


<!-- Alexandru: hiding this for now

One more important datapoint is the amount of time it takes to complete the [user mapping](/help/journey-migration/content-transfer-tool/user-mapping-tool/overview-user-mapping-tool.md), if this is coupled with the content migration. You can take this data point into consideration for more realistic estimates, because it is added to the overall extraction timeline and it may not be required to run it during top-ups.

-->

Deze gegevenspunten kunnen u [&#x200B; ook helpen KPI &#x200B;](/help/journey-migration/readiness.md#establish-kpis) vestigen en andere migratie verwante taken.

### Migratieplan {#migration-plan}

Gebaseerd op de gegevenspunten u (zie hierboven) verzamelde, kunt u een migratieplan tot stand brengen dat in een macroprojectplan kan worden geïntegreerd. Met deze stap kunnen alle belangrijke belanghebbenden de migratieactiviteiten visualiseren en plannen.

De volgende tabel illustreert een typisch migratieplan:

| Migratie-herhaling | Begindatum | Geschatte einddatum | Afhankelijkheden | Geschatte duur (in dagen) | Aanvullende details/actiepunten |
|---|---|---|---|---|---|
| PRDCLONE-AUTHOR-INITIAL-USRMAP-CSSTAGE-AUTHOR |   |   |   |   |   |
| PRDCLONE-PUBLISH-TOPUP-CSSTAGE-AUTHOR |   |   |   |   |   |

Zoals u in de lijst kunt zien hierboven, is het nuttig om een specifiek noemend formaat te volgen om de migratieherhalingen te identificeren, bijvoorbeeld: **PRDCLONE** voor het bron AEM milieu, **AUTHOR/PUBLISH** voor het milieu van AEM as a Cloud Service, **CSSTAGE-AUTHOR** voor de instantie van AEM as a Cloud Service, etc.

Enkele belangrijke details die van invloed zijn op uw migratieplan:

**Het totale Aantal vereiste Extracties**

* Auteur- en Publish-extracties in specifieke omgevingen worden beschouwd als twee parallelle extracties, aangezien ze onafhankelijk van elkaar zijn.
* Aantal top-up extracties gebaseerd op de groei van de opslagplaats in specifieke tijdsperiodes.

**Totaal Aantal vereiste Ingesties**

* Het is belangrijk om dit punt in het plan te vangen, aangezien een gehaalde reeks in veelvoudige milieu&#39;s van de Cloud Service kan worden opgenomen.
* Aantal top-up ingestions.
* Inhoud migreren van de Source-auteur naar de Cloud Service Author-instantie en van de Source Publish naar Cloud Service Publish is de beste manier om te voorkomen dat alle Author-inhoud wordt opgenomen in de Cloud Service Publish.

### Migratiebeheer {#migration-tracker}

U kunt de migratiecontracker gebruiken om de tijden voor zowel de aanvankelijke als top-up looppas neer te noteren. Met deze gegevenspunten kunt u vóór de laatste top-up realistische vereisten voor het bevriezen van inhoud formuleren.

De tracker helpt u ook om:

* Eventuele afwijkingen van de planner identificeren die aanpassingen in de plan- of go-live tijdlijnen vereisen
* Verstrek een realistische status die in alle noodzakelijke mededelingen kan worden gebruikt
* Plan voor initiële of toekomstige aanvullende migratie

De volgende tabel illustreert een functionele migratiecontracker:

| Source (Environment / Instance / URL) | Doel (omgeving / instantie / URL) | Naam migratieset, type (bij openen of boven) | Grootte migratieset (MB) | Gebruikerstoewijzing (Ja/Nee) | Duur van extractie (begin, eind, genomen tijd) | Ingestieduur (begin, einde, tijd genomen) | Problemen/resoluties/details |
|---|---|---|---|---|---|---|---|
|   |   |   |   |   |   |   |   |

## Strategie en tijdlijn voor migratie van inhoud {#content-strategyand-timeline}

In de volgende sectie worden de belangrijke stappen en bijbehorende taken weergegeven die kunnen worden gebruikt om een strategie en tijdlijn voor inhoudsmigratie te formuleren.

![&#x200B; Stappen om een migratiestrategie te formuleren &#x200B;](/help/journey-migration/assets/content-migration2.png)

### Inrichting {#fitment}

* Voer revisie schoonmaak uit, de inzameling van de gegevensopslag en de controles van de gegevensconsistentie. Zie ook [&#x200B; Voorbereidend voor gaan-Levend &#x200B;](#preparing-for-go-live)
* [&#x200B; Verzamel statistieken &#x200B;](#gathering-data) over de AEM bronbewaarplaats:
   * Grootte van segmentarchief
   * Grootte van indexarchief
   * Aantal pagina&#39;s
   * Aantal activa
   * Aantal gebruikers en groepen
* Controleer of de volgende functies zijn ingeschakeld op de AEM-bron (ook vereist in AEM as a Cloud Service):
   * Slimme tags toepassen
   * Zoeken op gelijkenis
   * Zoeken naar tekst in woord- en PDF-documenten
* Verzamel het rapport van de Analysator van Beste praktijken [&#128279;](/help/journey-migration/best-practices-analyzer/overview-best-practices-analyzer.md)
* De invoer in [&#x200B; Cloud Acceleration Manager &#x200B;](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md)
   * Bekijk de aanbeveling voor zelfanalyse om ervoor te zorgen dat AEM as a Cloud Service de opslagvereisten kan verwerken.
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
* Voer minstens één volledige en [&#x200B; top-up &#x200B;](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md#top-up-ingestion-process) migratie uit, van de productiekloon in het niet productiemilieu van AEM as a Cloud Service
* Los mogelijke problemen op zoals:
   * Schijfruimte op de AEM
   * Connectiviteit tussen de AEM en AEM as a Cloud Service
   * Om het even welke [&#x200B; opname verwante beperkingen &#x200B;](go-live.md#known-limitations).
* Registreer de tijd voor [&#x200B; extractie en opname &#x200B;](#gathering-data) wordt genomen die:
   * Weet hoeveel inhoud per week wordt toegevoegd
   * Extrapoleer de tijden die van de proef van migratie worden gemeten om a [&#x200B; migratieplan &#x200B;](#migration-plan) tot stand te brengen.

## Volgende functies {#what-is-next}

Nadat u volledig hebt begrepen hoe te om te beoordelen of is uw AEM installatie klaar om aan de wolk worden bewogen, aangezien wij leren hoe te om de hulpmiddelen te gebruiken nodig om het klaar te maken, is het tijd om zich op de [&#x200B; gaan-levende fase &#x200B;](/help/journey-migration/go-live.md) te bewegen.
