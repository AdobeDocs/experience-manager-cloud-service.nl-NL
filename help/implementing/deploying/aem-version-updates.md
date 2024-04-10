---
title: Versie-updates AEM
description: Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 72fc611e006f80fdda672f08b0b795432f5899e2
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---


# Versie-updates AEM {#aem-version-updates}

Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.

## CI/CD {#ci-cd}

AEM as a Cloud Service gebruik ononderbroken integratie en ononderbroken levering (CI/CD) om ervoor te zorgen dat uw projecten op de huidigste AEM versie zijn. Met dit proces worden uw productie-, staging- en ontwikkelingsinstanties naadloos bijgewerkt, zonder dat dit uw gebruikers verstoort.

>[!NOTE]
> Aangezien ontwikkelingsinstanties al automatisch worden bijgewerkt, zijn de handmatige updates voor ontwikkelingsinstanties mogelijk niet beschikbaar voor _sommige_ van uw programma&#39;s. Deze functie wordt overgebracht naar automatische updates.

Voordat uw exemplaren automatisch worden bijgewerkt, wordt 3-5 dagen van tevoren een nieuwe AEM-onderhoudrelease gepubliceerd. Tijdens deze periode kan uw ontwikkelingsexemplaar automatisch worden bijgewerkt of in het geval dat deze beschikbaar is, kunt u dit optioneel doen [activeer de update voor uw ontwikkelingsinstanties](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). De updates van de versie worden automatisch toegepast op uw ontwikkelomgevingen eerst. Als de update succesvol is, gaat het updateproces naar uw werkgebied en productieinstanties. De ontwikkelings- en staging-instanties fungeren als een geautomatiseerde kwaliteitspoort, waar uw op maat geschreven tests worden uitgevoerd voordat de update wordt toegepast op uw productieomgeving.

### NIMU (Non-Intrusive Maintenance Updates) {#nimu}

Niet-opdringerige onderhoudsupdates zijn automatische updates die worden toegepast zonder de klantenpijpleidingen erbij te betrekken.
Door NIMU, kan de klant de pijpleiding op elk ogenblik gebruiken, zelfs als een AEM versieupdate gepland of lopend is en de Updates van het Onderhoud zullen niet meer in de de pijpleidingsgeschiedenis van de Klant verschijnen, makend het gemakkelijker om de geschiedenis van codeplaatsingen te volgen.

#### Activiteiten bijwerken

De huidige AEM kan nog steeds voor elke omgeving worden gecontroleerd, zoals voorheen, via het deelvenster Omgevingen van de gebruikersinterface van Cloud Manager. De zelfde kwaliteitsspoorten die in de pijpleiding worden gebruikt worden door de Updates van het Onderhoud van het Non-Intrusive, met inbegrip van de klant geschreven tests.
Er wordt een melding naar de interface van Cloud Manager verzonden wanneer een update voor niet-opdringerig onderhoud wordt toegepast op de omgevingen van uw programma. U kunt instellen dat deze ook naar uw e-mail wordt verzonden.

>[!NOTE]
>
> Opmerking: in 2024 zullen de updates voor niet-indringend onderhoud geleidelijk aan voor alle klanten worden ingeschakeld.


## Type updates {#update-types}

Er zijn twee typen AEM versie-updates:

* [**AEM Onderhoudsupdates**](/help/release-notes/maintenance/latest.md)

   * Ze zijn vooral bedoeld voor onderhoudsdoeleinden, inclusief de nieuwste oplossingen voor problemen en beveiligingsupdates.
   * Het heeft minimale gevolgen, omdat de wijzigingen regelmatig worden toegepast.

* [**AEM Functie activeren**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Ze worden op een voorspelbaar maandelijks schema vrijgegeven.

>[!NOTE]
>
> Controleer de belangrijkste datums voor maandelijkse versies op de [Routekaart voor release van Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service) en markeer uw kalenders om u voor te bereiden op de belangrijkste activiteiten om klaar te zijn voor de release.

## Update mislukt {#update-failure}

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen, zodat de service voor alle systemen in productie niet wordt onderbroken. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een AEM as a Cloud Service update ontbreken, gaat de versie niet te werk, en de Adobe onderzoekt waarom de update dit onverwachte gedrag veroorzaakte.

Wanneer u een nieuwe versie van douanecode op uw milieu opstelt, [Product- en aangepaste functionele tests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) een cruciale rol spelen. Zij zorgen ervoor dat de productiesystemen stabiel en functioneel blijven, zelfs nadat een wijziging is aangebracht. Deze tests worden ook toegepast in het updateproces van de Versie van de AEM.

Als de update naar de productieomgeving mislukt, draait Cloud Manager automatisch de testomgeving terug. Dit wordt automatisch gedaan om ervoor te zorgen dat nadat een update voltooit, zowel de het opvoeren als productiemilieu&#39;s op de zelfde AEM versie zijn.
En als een geautomatiseerde update van een ontwikkelomgeving mislukt, worden de faserings- en productieomgevingen niet bijgewerkt.

>[!NOTE]
>
>Als de douanecode aan het opvoeren en niet aan productie werd geduwd, verwijdert de volgende AEM update die veranderingen om op de git markering van de laatste succesvolle klantenversie aan productie te wijzen. Daarom moet de douanecode die slechts op het opvoeren beschikbaar was opnieuw worden opgesteld.

## Aanbevolen procedures {#best-practices}

* **Gebruik van Stage-omgeving**
   * Gebruik een andere omgeving (geen werkgebied) voor lange QA/UAT-cycli.
   * Nadat het testen van de hygiëne in het werkgebied is voltooid, gaat u naar Verifiëren bij Productie.

* **Productiepijpleiding**
   * Pauze voordat u gaat implementeren naar productie.
   * Als de pijplijn wordt geannuleerd nadat een werkgebied is geïmplementeerd, geeft de code aan dat de code &quot;een wegbaan&quot; is en geen geldige kandidaat voor Productie. Raadpleeg [Een productiepijpleiding configureren](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **Niet-productiepijpleiding**
   * Een [Niet-productiepijpleiding](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Versnelt leversnelheid/frequentie voor mislukte productiepijplijnen. Identificeer kwesties in niet-prod pijpleidingen door het Functionele Testen van het Product, het Aangepast Functioneren Testen, en het Testen van de UI van de Douane toe te laten.

* **Inhoud kopiëren**
   * Gebruiken [Inhoud kopiëren](/help/implementing/developing/tools/content-copy.md) om vergelijkbare inhoudssets te verplaatsen naar een niet-prodomgeving.

* **Geautomatiseerde functionele tests**
   * Neem de automatische test op in de pijplijn, zodat u kritieke functionaliteit kunt testen.
   * [Functionele tests van de klant](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) en [Aangepaste UI-tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blokkeren als ze er niet in slagen de AEM uit te voeren.

## Regressie {#regression}

Als u een probleem tegenkomt met betrekking tot regressie, dient u een ondersteuningsgeval in via de Admin Console. Als de kwestie een blokker is en de invloed ervan op de productie, moet een P1 worden opgeworpen. Geef alle gegevens op die nodig zijn om het regressieprobleem te reproduceren.

## Composite Node Store {#composite-node-store}

Meestal worden updates zonder downtime uitgevoerd, inclusief voor de ontwerpinstantie, die een cluster met knooppunten is. Rolling-updates zijn mogelijk vanwege [de samengestelde eigenschap van de knoopopslag in Eak.](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In een [implementatie](/help/implementing/deploying/overview.md#how-rolling-deployments-work), bevat de nieuwe AEM een eigen versie `/libs` (de op TarMK gebaseerde onveranderlijke opslagplaats). Het is verschillend van de oudere AEM versie, hoewel allebei verwijzen naar een gedeelde op DocumentMK gebaseerde veranderbare bewaarplaats die gebieden zoals bevat `/content` , `/conf` , `/etc` en andere.

Omdat zowel de oude als de nieuwe versie hun eigen versies hebben `/libs`en kunnen beide actief zijn tijdens de actieve update. En, kunnen beide verkeer nemen tot de oude volledig door nieuwe wordt vervangen.
