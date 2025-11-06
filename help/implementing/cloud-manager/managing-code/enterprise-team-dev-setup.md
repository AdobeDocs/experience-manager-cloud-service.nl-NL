---
title: Teaminstallatie voor bedrijfsontwikkeling
description: Leer hoe u uw ontwikkelingsteam voor bedrijven kunt instellen en schalen en hoe AEM as a Cloud Service uw ontwikkelingsproces kan ondersteunen.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 0%

---

# Setup van het Enterprise Development Team voor AEM as a Cloud Service {#enterprise-setup}

Leer hoe u uw ontwikkelingsteam voor ondernemingen kunt instellen en schalen en hoe AEM (Adobe Experience Manager) as a Cloud Service uw ontwikkelingsproces kan ondersteunen.

## Inleiding {#introduction}

Om klanten met de montages van de ondernemingsontwikkeling te steunen, integreert AEM as a Cloud Service volledig met Cloud Manager en zijn doel-gebouwde, [ geadviseerde pijpleidingen CI/CD ](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md). Deze pijpleidingen en de diensten worden gebouwd gebaseerd op beste praktijken, die grondig [ het testen en de hoogste codekwaliteit ](/help/implementing/cloud-manager/code-quality-testing.md) verzekeren.

## Cloud Manager-ondersteuning in de ontwikkeling van een Enterprise-team {#cloud-manager}

Om snel aan boord te kunnen gaan, biedt Cloud Manager alles wat nodig is om meteen aan de slag te gaan met het ontwikkelen van digitale ervaringen, waaronder een Git-opslagplaats voor aanpassingen, die vervolgens worden gebouwd, geverifieerd en geïmplementeerd door Cloud Manager.

Met Cloud Manager kunnen ontwikkelingsteams vaak werken aan het doorvoeren van wijzigingen zonder afhankelijk te zijn van Adobe-personeel.

Er zijn drie typen omgevingen beschikbaar in Cloud Manager.

* Ontwikkeling
* Werkgebied
* Productie

De code kan aan ontwikkelmilieu&#39;s worden opgesteld gebruikend een niet productiepijplijn. Voor het opvoeren en productiemilieu&#39;s, die altijd samen gaan en zo bevestiging vóór productieplaatsing als beste praktijken verzekeren, gebruikt een productiepijpleiding [ kwaliteitsspoorten ](/help/implementing/cloud-manager/custom-code-quality-rules.md) om de toepassingscode en de configuratieveranderingen te bevestigen.

De productiepijpleiding stelt de code en de configuratie aan het opvoeren milieu eerst op, test de toepassing, en stelt definitief aan productie op.

Een Cloud Service SDK die altijd wordt bijgewerkt met de nieuwste AEM as a Cloud Service-verbeteringen maakt lokale ontwikkeling mogelijk die rechtstreeks gebruikmaakt van de lokale hardware van de ontwikkelaar. Deze aanpak maakt een snelle ontwikkeling met zeer lage omlooptijden mogelijk. Op die manier kunnen ontwikkelaars in hun vertrouwde lokale omgeving blijven en kiezen uit een groot aantal verschillende ontwikkelingsprogramma&#39;s, en overstappen op ontwikkelomgevingen of productie wanneer ze dat nodig achten.

Cloud Manager ondersteunt flexibele instellingen voor meerdere teams die kunnen worden aangepast aan de behoeften van een onderneming. Om stabiele plaatsingen over veelvoudige teams te verzekeren, bevestigt de gepositioneerde pijpleiding Cloud Manager en test de code van alle teams samen. Deze benadering helpt situaties te voorkomen waarin de veranderingen van één team de productie voor alle teams beïnvloeden.

## Voorbeeld van een echte wereld {#real-world-example}

Elke onderneming heeft verschillende vereisten met inbegrip van verschillende teamopstelling, processen, en ontwikkelingswerkstromen. De hieronder beschreven setup wordt door Adobe gebruikt voor verschillende projecten die ervaring bieden boven op AEM as a Cloud Service.

De Adobe Creative Cloud-toepassingen, zoals Adobe Photoshop of Adobe Illustrator, bevatten bijvoorbeeld inhoudsbronnen, zoals zelfstudies, voorbeelden en hulplijnen die beschikbaar zijn voor eindgebruikers. Clienttoepassingen verbruiken inhoud van AEM as a Cloud Service zonder kop. Ze maken API-aanroepen naar de AEM Cloud-publicatielaag om gestructureerde inhoud op te halen als JSON-streams. Bovendien, wordt het [ Netwerk van de Levering van de Inhoud (CDN) in AEM as a Cloud Service ](/help/implementing/dispatcher/cdn.md#content-delivery) gebruikt om zowel gestructureerde als ongestructureerde inhoud met optimale prestaties te dienen.

De teams die aan dit project bijdragen volgen het volgende proces.

Elk team gebruikt zijn eigen ontwikkelworkflow en heeft een aparte Git-opslagplaats. Voor instapprojecten wordt een extra gedeelde Git-opslagplaats gebruikt. Deze Git-opslagplaats bevat de basisstructuur van de Cloud Manager Git-opslagplaats, inclusief de gedeelde Dispatcher-configuratie.

Voor het instappen van een nieuw project moet in het projectbestand Maven van de reactor een lijst worden opgenomen in de hoofdmap van de gedeelde Git-opslagplaats. Voor Dispatcher-configuratie wordt een nieuw configuratiebestand gemaakt in het Dispatcher-project. De hoofdconfiguratie van Dispatcher omvat dan dit dossier. Elk team is verantwoordelijk voor zijn eigen Dispatcher-configuratiebestand. Wijzigingen in de gedeelde Git-opslagplaats zijn zeldzaam en zijn gewoonlijk alleen vereist wanneer een nieuw project wordt gestart. Het belangrijkste werk wordt gedaan door elk projectteam binnen hun eigen bewaarplaats van het Git.

![ diagram van het Werkschema ](/help/implementing/cloud-manager/assets/team-setup1.png)

De bewaarplaats van het Git voor elk wordt opstelling gebruikend het [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/overview) en volgt derhalve de beste praktijken voor vestiging de Projecten van AEM. De enige uitzondering hierop is de Dispatcher-configuratie, die wordt uitgevoerd in de gedeelde Git-opslagplaats, zoals hierboven beschreven.

Elk team gebruikt een vereenvoudigde Git-workflow met twee vertakkingen + N, volgens het Git-flowmodel:

* Een stabiele releasetak bevat de productiecode.

* Een ontwikkelingstak bevat de recentste ontwikkeling.

* Voor elke functie wordt een nieuwe vertakking gemaakt.

De ontwikkeling wordt gedaan in een eigenschaptak. Wanneer de eigenschap rijpt, wordt het samengevoegd in de ontwikkelingstak. Voltooide en gevalideerde functies worden gekozen uit de ontwikkelingstak en samengevoegd in de stabiele vertakking.

Alle wijzigingen worden doorgevoerd via PR&#39;s (verzoeken om uitwissen). Kwaliteitskoppels valideren automatisch elke PR. Sonar wordt gebruikt voor kwaliteitscontrole van de code en er wordt een reeks testreeksen uitgevoerd om ervoor te zorgen dat de nieuwe code geen regressie introduceert.

De installatie in de Cloud Manager Git-opslagplaats heeft twee vertakkingen.

* Een stabiele releasetak bevat de productiecode van alle teams.
* Een ontwikkelingstak bevat de ontwikkelingscode van alle teams.

Elke duw aan de bewaarplaats van het Git van een team in of de ontwikkeling of de stabiele tak teweegbrengt de actie van a [ GitHub ](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code).

Alle projecten volgen de zelfde opstelling voor de stabiele tak. Een duw naar de stabiele tak van een project wordt automatisch geduwd aan de stabiele tak in de bewaarplaats van de Git van Cloud Manager. Een duw naar de stabiele tak brengt de productiepijpleiding in Cloud Manager in werking. Elke duw door om het even welk team in een stabiele tak brengt de productiepijpleiding teweeg. De productieplaatsing wordt bijgewerkt als alle kwaliteitspoorten overgaan.

![ Push diagram ](/help/implementing/cloud-manager/assets/team-setup2.png)

Penselen naar de ontwikkelingsvertakking worden anders verwerkt. Een duw aan een ontwikkelaartak in de bewaarplaats van de it van een team teweegbrengt ook een actie GitHub teweeg. Deze actie duwt automatisch de code in de ontwikkelingstak in de bewaarplaats van het Git van Cloud Manager. Deze code-push activeert echter niet automatisch de niet-productiepijplijn. Een aanroep van de Cloud Manager API activeert deze.

Het runnen van de productiepijpleiding omvat het controleren van de code van alle teams via de verstrekte kwaliteitsspoortaten. Nadat de code aan stadium wordt opgesteld, worden de tests en de controles in werking gesteld zodat werkt alles zoals verwacht. Wanneer alle poorten worden doorgegeven, worden de wijzigingen doorgevoerd in de productie zonder onderbreking of downtime.

Voor lokale ontwikkeling, wordt [ SDK voor AEM as a Cloud Service ](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) gebruikt. Met de SDK kunnen een lokale auteur, publicatie en Dispatcher worden ingesteld. Deze workflow maakt offline ontwikkeling en snelle doorlooptijden mogelijk. Soms wordt alleen de auteursomgeving gebruikt voor ontwikkeling, maar als u snel Dispatcher- en publicatieomgevingen instelt, kunt u alles lokaal testen voordat u naar de Git-opslagplaats gaat.

De leden van elk team controleren gewoonlijk de code van de gedeelde Git voor hun eigen projectcode. Andere projecten hoeven niet te worden gecontroleerd omdat de projecten onafhankelijk zijn.

![ Lokale controle en SDK ](/help/implementing/cloud-manager/assets/team-setup3.png)

Deze real-world opstelling kan als blauwdruk worden gebruikt en dan aan de behoeften van een onderneming worden aangepast. Met het flexibele vertakkings- en samenvoegingsconcept van Git kunt u de hierboven vermelde workflows variëren en aanpassen aan de behoeften van elk team. AEM as a Cloud Service steunt al deze variaties zonder de kernwaarde van de gedenkwaardige Cloud Manager-pijpleiding op te offeren.

>[!TIP]
>
>Zie [ het Werk met de Veelvoudige Opslagplaatsen van de Plaats van de it van Source ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/multiple-git-repos#managing-code) om meer over deze opstelling te leren.

### Overwegingen bij de installatie van meerdere teams {#considerations}

Met de Cloud Manager Git-opslagplaats en de productiepijpleiding gaat de volledige productiecode altijd door alle kwaliteitskates, waarbij deze als één uitzettingseenheid wordt behandeld. Op deze manier is het productiesysteem altijd zonder onderbreking of onderbreking.

Zonder een dergelijk systeem, omdat elk team afzonderlijk kan implementeren, bestaat daarentegen het risico dat een update van één team kan leiden tot problemen met productiestabiliteit. Daarnaast is coördinatie en geplande uitvaltijd nodig om updates uit te voeren. Met een toenemend aantal teams wordt de coördinatie-inspanning veel complexer en snel onbeheersbaar.

Als er een probleem wordt vastgesteld in de kwaliteitskates, heeft dit geen invloed op de productie en kan het probleem worden opgespoord en verholpen zonder dat er personeel van Adobe nodig is om in te stappen. Zonder Cloud Service en zonder altijd de volledige implementatie te testen, kunnen gedeeltelijke implementaties uitvallen veroorzaken waarvoor een verzoek tot terugdraaien of zelfs een volledige terugzetbewerking van een back-up is vereist. Gedeeltelijke tests kunnen ook aanleiding geven tot aanvullende problemen die later moeten worden opgelost, en waarvoor nogmaals coördinatie en ondersteuning van het personeel van Adobe vereist is.

>[!TIP]
>
>Voor elke instelling met meerdere teams is het van cruciaal belang dat er een governancemodel en een reeks standaarden worden gedefinieerd die alle teams moeten volgen. De vorige blauwdruk voor een multi-teamopstelling staat het schrapen over een groter aantal teams toe, die u als uitgangspunt kunt gebruiken.
