---
title: Versie-updates AEM
description: Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---


# Versie-updates AEM {#aem-version-updates}

Leer hoe Adobe Experience Manager (AEM) as a Cloud Service ononderbroken integratie en levering (CI/CD) gebruikt om uw projecten op de recentste versie te houden.

## CI/CD {#ci-cd}

AEM as a Cloud Service maakt gebruik van continue integratie en doorlopende levering (CI/CD) om ervoor te zorgen dat uw projecten de meest actuele AEM versie hebben. Met dit proces worden uw productie-, staging- en ontwikkelingsinstanties naadloos bijgewerkt, zonder dat dit uw gebruikers verstoort.

>[!NOTE]
> Aangezien de ontwikkelingsinstanties reeds automatisch worden bijgewerkt, zouden de handupdates voor ontwikkelingsinstanties niet aan _kunnen beschikbaar zijn wat_ van uw programma&#39;s. Deze functie wordt overgebracht naar automatische updates.

Voordat uw exemplaren automatisch worden bijgewerkt, wordt 3-5 dagen van tevoren een nieuwe AEM-onderhoudrelease gepubliceerd. Tijdens deze periode, zou uw ontwikkelingsinstantie automatisch kunnen worden bijgewerkt of in het geval dat het beschikbaar is kunt u naar keuze [ de update voor uw ontwikkelingsinstanties ](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment) teweegbrengen. De updates van de versie worden automatisch toegepast op uw ontwikkelomgevingen eerst. Als de update succesvol is, gaat het updateproces naar uw werkgebied en productieinstanties. De ontwikkelings- en staging-instanties fungeren als een geautomatiseerde kwaliteitspoort, waar uw op maat geschreven tests worden uitgevoerd voordat de update wordt toegepast op uw productieomgeving.

### NIMU (Non-Intrusive Maintenance Updates) {#nimu}

Niet-opdringerige onderhoudsupdates zijn automatische updates die worden toegepast zonder de klantenpijpleidingen erbij te betrekken.
Door NIMU, kan de klant de pijpleiding op elk ogenblik gebruiken, zelfs als een AEM versieupdate gepland of lopend is en de Updates van het Onderhoud zullen niet meer in de de pijpleidingsgeschiedenis van de Klant verschijnen, makend het gemakkelijker om de geschiedenis van codeplaatsingen te volgen.

#### Activiteiten bijwerken

De huidige AEM kan nog steeds voor elke omgeving worden gecontroleerd, zoals eerder, met behulp van het deelvenster Cloud Manager UI-omgevingen. De zelfde kwaliteitsspoorten die in de pijpleiding worden gebruikt worden door de Updates van het Onderhoud van het Non-Intrusive, met inbegrip van de klant geschreven tests.
A [ het bericht van Cloud Manager UI ](/help/implementing/cloud-manager/notifications.md) zal worden verzonden wanneer een Niet-Intrusieve Update van het Onderhoud wordt toegepast op de milieu&#39;s van uw programma. U kunt instellen dat deze ook naar uw e-mail wordt verzonden.

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
> De belangrijkste data van de controle voor maandelijkse versies op de [ versies van de Experience Manager roadmap ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html#aem-as-cloud-service) en merken uw kalenders om zich voor te bereiden op de belangrijkste activiteiten om voor de versie klaar te worden.

## Update mislukt {#update-failure}

AEM updates doorlopen een intensieve en volledig geautomatiseerde productvalideringspijplijn met meerdere stappen, zodat de service voor alle systemen in productie niet wordt onderbroken. Gezondheidscontroles worden gebruikt om de gezondheid van de toepassing te controleren. Als deze controles tijdens een update van AEM as a Cloud Service ontbreken, gaat de versie niet te werk, en de Adobe onderzoekt waarom de update dit onverwachte gedrag veroorzaakte.

Wanneer u een nieuwe versie van douanecode op uw milieu opstelt, [ product en de functionele tests van de Douane ](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) spelen een cruciale rol. Zij zorgen ervoor dat de productiesystemen stabiel en functioneel blijven, zelfs nadat een wijziging is aangebracht. Deze tests worden ook toegepast in het updateproces van de Versie van de AEM.

Als de update naar de productieomgeving mislukt, draait Cloud Manager automatisch de testomgeving terug. Dit wordt automatisch gedaan om ervoor te zorgen dat nadat een update voltooit, zowel de het opvoeren als productiemilieu&#39;s op de zelfde AEM versie zijn.
En als een geautomatiseerde update van een ontwikkelomgeving mislukt, worden de faserings- en productieomgevingen niet bijgewerkt.

>[!NOTE]
>
>Als de douanecode aan het opvoeren en niet aan productie werd geduwd, verwijdert de volgende AEM update die veranderingen om op de git markering van de laatste succesvolle klantenversie aan productie te wijzen. Daarom moet de douanecode die slechts op het opvoeren beschikbaar was opnieuw worden opgesteld.

## Aanbevolen procedures {#best-practices}

* **Gebruik van het Milieu van het Stadium**
   * Gebruik een andere omgeving (geen werkgebied) voor lange QA/UAT-cycli.
   * Nadat het testen van de hygiëne in het werkgebied is voltooid, gaat u naar Verifiëren bij Productie.

* **de Pijpleiding van de Productie**
   * Pauze voordat u gaat implementeren naar productie.
   * Het annuleren van de pijpleiding na een Stadium stelt erop dat de code &quot;een wegbaan&quot;en geen geldige kandidaat voor Productie is, verwijs [ het Vormen van een Pijpleiding van de Productie ](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **niet-Productie Pijpleiding**
   * Vorm a [ niet-Productiepijpleiding ](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Versnelt leversnelheid/frequentie voor mislukte productiepijplijnen. Identificeer kwesties in niet-prod pijpleidingen door het Functionele Testen van het Product, het Aangepast Functioneren Testen, en het Testen van de UI van de Douane toe te laten.

* **Exemplaar van de Inhoud**
   * Het Exemplaar van de Inhoud van het gebruik ](/help/implementing/developing/tools/content-copy.md) om gelijkaardige inhoudssets aan een niet-prod milieu te bewegen.[

* **Geautomatiseerd Functioneel het Testen**
   * Neem de automatische test op in de pijplijn, zodat u kritieke functionaliteit kunt testen.
   * [ Functionele Testen van de Klant ](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) en [ Testen van UI van de Douane ](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blokkeren, als zij de AEM versie niet uit worden opgerold.

## Regressie {#regression}

Als u een probleem tegenkomt met betrekking tot regressie, dient u een ondersteuningsgeval in via de Admin Console. Als de kwestie een blokker is en de invloed ervan op de productie, moet een P1 worden opgeworpen. Geef alle gegevens op die nodig zijn om het regressieprobleem te reproduceren.

## Composite Node Store {#composite-node-store}

Meestal worden updates zonder downtime uitgevoerd, inclusief voor de ontwerpinstantie, die een cluster met knooppunten is. Het rollen updates zijn mogelijk toe te schrijven aan [ de samengestelde eigenschap van de knoopopslag in Oak ](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html).

Met deze functie kunnen AEM tegelijkertijd verwijzen naar meerdere opslagplaatsen. In a [ het rollen plaatsing ](/help/implementing/deploying/overview.md#how-rolling-deployments-work), bevat de nieuwe AEM versie zijn eigen `/libs` (de op TarMK gebaseerde onveranderlijke bewaarplaats). Deze gegevensopslagruimte verschilt van de oudere AEM, hoewel beide verwijzen naar een gezamenlijke, op DocumentMK gebaseerde, veranderbare gegevensopslagruimte die gebieden als `/content` , `/conf` , `/etc` en andere bevat.

Omdat zowel de oude als de nieuwe versie een eigen versie van `/libs` hebben, kunnen beide actief zijn tijdens de actieve update. En, kunnen beide verkeer nemen tot de oude volledig door nieuwe wordt vervangen.

## Aanvullende informatie {#further-information}

Voor meer informatie over verwante thema&#39;s:

* [Cloud Manager CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
* [Cloud Manager UI-melding](/help/implementing/cloud-manager/notifications.md)
* [de Architectuur van Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md)
