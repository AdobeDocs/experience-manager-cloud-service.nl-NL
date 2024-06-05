---
title: Teaminstallatie voor bedrijfsontwikkeling
description: Leer hoe u uw ontwikkelingsteam voor bedrijven kunt instellen en schalen en hoe AEM as a Cloud Service uw ontwikkelingsproces kan ondersteunen.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '1423'
ht-degree: 0%

---

# Enterprise Development Team Setup voor AEM as a Cloud Service {#enterprise-setup}

Leer hoe u uw ontwikkelingsteam voor bedrijven kunt instellen en schalen en hoe AEM as a Cloud Service uw ontwikkelingsproces kan ondersteunen.

## Inleiding {#introduction}

Om klanten met bedrijfsontwikkelingsmontages te steunen, AEM as a Cloud Service volledig met de Manager van de Wolk en zijn doelgericht-gebouwd integreren, [geopinioneerde CI/CD-pijpleidingen](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md). Deze pijpleidingen en diensten zijn gebaseerd op de beste praktijken en zorgen voor een degelijke [testen en de hoogste codekwaliteit](/help/implementing/cloud-manager/code-quality-testing.md).

## De Steun van de Manager van de wolk in de Opstelling van de Ontwikkeling van het Team van de Onderneming {#cloud-manager}

Om snel aan boord te kunnen gaan, biedt Cloud Manager alles wat nodig is om meteen aan de slag te gaan met het ontwikkelen van digitale ervaringen, waaronder een git-opslagplaats voor aanpassingen die vervolgens worden gebouwd, geverifieerd en geïmplementeerd door Cloud Manager.

Met behulp van Cloud Manager kunnen ontwikkelingsteams regelmatig wijzigingen doorvoeren zonder afhankelijk te zijn van het personeel van de Adobe.

Er zijn drie typen omgevingen beschikbaar in Cloud Manager.

* Ontwikkeling
* Werkgebied
* Productie

De code kan aan ontwikkelmilieu&#39;s worden opgesteld gebruikend een niet productiepijplijn. Voor staging- en productieomgevingen, die altijd samenwerken en dus validering garanderen voordat de productie wordt geïmplementeerd als beste praktijken, gebruikt een productiepijpleiding [kwaliteitscentra](/help/implementing/cloud-manager/custom-code-quality-rules.md) om de toepassingscode en de configuratieveranderingen te bevestigen.

De productiepijpleiding stelt de code en de configuratie aan het opvoeren milieu eerst op, test de toepassing, en stelt definitief aan productie op.

Een Cloud Service-SDK die altijd wordt bijgewerkt met de nieuwste AEM as a Cloud Service verbeteringen maakt lokale ontwikkeling mogelijk die rechtstreeks gebruikmaakt van de lokale hardware van de ontwikkelaar. Dit maakt een snelle ontwikkeling mogelijk met zeer lage omlooptijden. Op die manier kunnen ontwikkelaars in hun vertrouwde lokale omgeving blijven en kiezen uit een groot aantal verschillende ontwikkelingsprogramma&#39;s, en overstappen op ontwikkelomgevingen of productie wanneer ze dat nodig achten.

Cloud Manager ondersteunt flexibele instellingen voor meerdere teams die kunnen worden aangepast aan de behoeften van een onderneming. Om stabiele plaatsingen met veelvoudige teams te verzekeren terwijl het vermijden van situaties waar één team productie voor alle teams beïnvloedt, bevestigt en test de geadviseerde pijpleiding van de Manager van de Wolk altijd de code van alle teams samen.

## Voorbeeld van een echte wereld {#real-world-example}

Elke onderneming heeft verschillende vereisten met inbegrip van verschillende teamopstelling, processen, en ontwikkelingswerkstromen. De hieronder beschreven opstelling wordt gebruikt door Adobe voor verscheidene projecten die ervaringen bovenop AEM as a Cloud Service leveren.

De Adobe Creative Cloud-toepassingen, zoals Adobe Photoshop of Adobe Illustrator, bevatten bijvoorbeeld inhoudsbronnen, zoals zelfstudies, voorbeelden en hulplijnen die beschikbaar zijn voor eindgebruikers. Deze inhoud wordt door de clienttoepassingen verbruikt met behulp van AEM as a Cloud Service zonder kop, door API-aanroepen uit te voeren naar de AEM Cloud-publicatielaag om de gestructureerde inhoud op te halen als JSON-streams en door de [CDN (Content Delivery Network) in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) om zowel gestructureerde als ongestructureerde inhoud met optimale prestaties te dienen.

De teams die aan dit project bijdragen volgen het volgende proces.

Elk team gebruikt zijn eigen ontwikkelingswerkstroom en heeft een afzonderlijke git bewaarplaats. Een extra gedeelde git-opslagplaats wordt gebruikt voor instapprojecten. Deze git-opslagplaats bevat de basisstructuur van de git-opslagplaats van Cloud Manager, inclusief de configuratie van de gedeelde verzender.

Als u een nieuw project aan boord wilt nemen, moet u dit in het projectbestand Maven van de reactor opnemen in de hoofdmap van de gedeelde git-opslagplaats. Voor de configuratie van de verzender wordt een nieuw configuratiedossier gecreeerd binnen het verzender project. Dit bestand wordt vervolgens opgenomen door de configuratie van de hoofddispatcher. Elk team is verantwoordelijk voor zijn eigen de configuratiedossier van de verzender. Wijzigingen in de gedeelde git-opslagplaats zijn zeldzaam en zijn gewoonlijk alleen vereist wanneer een nieuw project wordt gestart. Het belangrijkste werk wordt gedaan door elk projectteam binnen hun eigen git bewaarplaats.

![Workflowdiagram](/help/implementing/cloud-manager/assets/team-setup1.png)

De git-opslagplaats voor elk systeem wordt ingesteld met behulp van [Projectarchetype AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) en volgt derhalve de beste praktijken voor het opzetten van AEM projecten. De enige uitzondering is de configuratie van de verzender die wordt uitgevoerd in de gedeelde git-opslagplaats, zoals hierboven beschreven.

Elk team gebruikt een vereenvoudigde git werkstroom met twee + N takken, die het model van de git stroom volgen:

* Een stabiele releasetak bevat de productiecode.

* Een ontwikkelingstak bevat de recentste ontwikkeling.

* Voor elke functie wordt een nieuwe vertakking gemaakt.

De ontwikkeling wordt gedaan in een eigenschaptak. Wanneer de eigenschap rijpt wordt het samengevoegd in de ontwikkelingstak. Voltooide en gevalideerde functies worden gekozen uit de ontwikkelingstak en samengevoegd in de stabiele vertakking.

Alle wijzigingen worden doorgevoerd via pull-aanvragen (PR&#39;s). Elke PR wordt automatisch gevalideerd door kwaliteitspoorten. Sonar wordt gebruikt voor kwaliteitscontrole van de code en er wordt een reeks testreeksen uitgevoerd om ervoor te zorgen dat de nieuwe code geen regressie introduceert.

De installatie in de git-opslagplaats van Cloud Manager heeft twee vertakkingen.

* Een stabiele releasetak bevat de productiecode van alle teams.
* Een ontwikkelingstak bevat de ontwikkelingscode van alle teams.

Elke duw aan de gokbewaarplaats van een team in of de ontwikkeling of de stabiele tak teweegbrengt [GitHub, actie](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code).

Alle projecten volgen de zelfde opstelling voor de stabiele tak. Een duw naar de stabiele tak van een project wordt automatisch geduwd aan de stabiele tak in de gokbewaarplaats van de Manager van de Wolk. De productiepijplijn in de Manager van de Wolk wordt gevormd om door een duw aan de stabiele tak worden teweeggebracht. De productiepijpleiding wordt daarom uitgevoerd door elke duw van om het even welk team in een stabiele tak en de productieleiding wordt bijgewerkt als alle kwaliteitstoegangspoorten overgaan.

![Push-diagram](/help/implementing/cloud-manager/assets/team-setup2.png)

Penselen naar de ontwikkelingsvertakking worden anders verwerkt. Terwijl een duw aan een ontwikkelaarstak in de git bewaarplaats van een team een actie GitHub eveneens teweegbrengt en de code automatisch in de ontwikkelingstak in de git bewaarplaats van de Manager van de Wolk wordt geduwd, wordt de niet productiepijpleiding niet automatisch teweeggebracht door de codeduw. Dit wordt geactiveerd door een aanroep van de API van Cloud Manager.

Het runnen van de productiepijpleiding omvat het controleren van de code van alle teams via de verstrekte kwaliteitsspoortaten. Zodra de code aan stadium wordt opgesteld, worden de tests en de controles uitgevoerd om ervoor te zorgen alles zoals verwacht werkt. Wanneer alle poorten zijn doorgegeven, worden de wijzigingen zonder onderbreking of downtime omgezet in productie.

Voor lokale ontwikkeling [SDK voor AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) wordt gebruikt. Met de SDK kan een lokale auteur, publicateur en verzender worden ingesteld. Dit maakt offline ontwikkeling en snelle doorlooptijden mogelijk. Soms wordt alleen de auteursomgeving gebruikt voor ontwikkeling, maar als u snel een verzender- en publicatieomgeving instelt, kunt u alles lokaal testen voordat u naar de opslagplaats voor kompas gaat.

De leden van elk team controleren gewoonlijk de code van de gedeelde git voor hun eigen projectcode. Andere projecten hoeven niet te worden gecontroleerd omdat de projecten onafhankelijk zijn.

![Lokale uitchecken en SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Deze real-world opstelling kan als blauwdruk worden gebruikt en dan aan de behoeften van een onderneming worden aangepast. Het flexibele vertakkings- en samenvoegingsconcept van git maakt variaties mogelijk van de bovenstaande workflows, die zijn aangepast aan de behoeften van elk team. AEM as a Cloud Service ondersteunt al deze variaties zonder dat dit ten koste gaat van de kernwaarde van de geadviseerde Cloud Manager-pijplijn.

>[!TIP]
>
>Zie [Werken met Meerdere bronopslaglocaties voor Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html#managing-code) voor meer informatie over deze installatie.

### Overwegingen voor een Opstelling van het Meerdere Team {#considerations}

Met de git-opslagplaats van Cloud Manager en de productiepijplijn wordt de volledige productiecode altijd door alle kwaliteitspoorten geleid, waarbij deze als één implementatieeenheid wordt behandeld. Op deze manier is het productiesysteem altijd zonder onderbreking of onderbreking.

Zonder een dergelijk systeem is er daarentegen een risico dat een update van één team tot problemen met productiestabiliteit kan leiden, omdat elk team afzonderlijk kan implementeren. Daarnaast is coördinatie en geplande uitvaltijd nodig om updates uit te voeren. Met een toenemend aantal teams wordt de coördinatie-inspanning veel complexer en snel onbeheersbaar.

Als een probleem wordt ontdekt in de kwaliteitskates, wordt de productie niet beïnvloed, en het probleem kan worden ontdekt en worden bevestigd zonder het personeel van de Adobe dat wordt vereist om binnen te stappen. Zonder Cloud Service en zonder altijd de volledige plaatsing te testen, kunnen de gedeeltelijke plaatsingen stroomonderbrekingen veroorzaken die een verzoek vereisen om terug te draaien of zelfs volledig te herstellen van een steun. De gedeeltelijke tests kunnen ook leiden tot andere problemen die vervolgens moeten worden opgelost nadat het personeel van de Adobe opnieuw moet worden gecoördineerd en ondersteund.

>[!TIP]
>
>Voor elke opstelling van meerdere teams is het van cruciaal belang om een bestuursmodel en een reeks normen te definiëren die alle teams moeten volgen. De vorige blauwdruk voor een multi-teamopstelling staat het schrapen over een groter aantal teams toe, die u als uitgangspunt kunt gebruiken.
